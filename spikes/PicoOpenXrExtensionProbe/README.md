# PICO OpenXR Passthrough Probe

This spike has moved beyond simple extension enumeration.

Its current goal is to answer a more practical question for the project:

- can a local `OpenXR` app on `PICO 4 Pro` create an immersive session and initialize passthrough-related runtime objects;
- and does that still work when `Pico Connect` is active.

## What this probe now does

On launch, the app:

1. initializes the official Khronos Android OpenXR loader;
2. enumerates runtime extensions;
3. creates an `XrInstance`;
4. queries `XrSystemId` and `XrSystemProperties`;
5. reads `XR_FB_passthrough` system capabilities when available;
6. creates a minimal `EGL/OpenGL ES` context;
7. attempts to create an `XrSession`;
8. polls session state changes and tries `xrBeginSession`;
9. if `XR_FB_passthrough` is available, attempts:
   - `xrCreatePassthroughFB`
   - `xrPassthroughStartFB`
   - `xrCreatePassthroughLayerFB`
   - `xrPassthroughLayerResumeFB`
10. writes the report to:
   - `/sdcard/Android/data/com.vrapp.picoopenxrextensionprobe/files/pico_openxr_extension_probe.txt`
11. mirrors the same report to `logcat`;
12. shows the report directly on-screen.

## Why this matters

For the product, standalone headset passthrough is not enough.

The useful product must work while `Pico Connect` is streaming the PC-rendered VR scene.

So the important comparison is now:

- run once from normal headset `Home`;
- run once while `Pico Connect` is active.

If session creation and passthrough object creation succeed in `Home` mode but fail under `Pico Connect`, then coexistence with streaming is the blocker.

## Build prerequisites

This spike was successfully built in this workspace with:

- Android SDK at `C:\Users\Username\AppData\Local\Android\Sdk`
- JDK 17
- Android NDK `26.1.10909125`
- CMake `3.22.1`

## Build

From `C:\Users\Username\Documents\VR.app\spikes\PicoOpenXrExtensionProbe`:

```powershell
$env:JAVA_HOME='C:\Users\Username\.gradle\jdks\jetbrains_s_r_o_-17-amd64-windows.2'
$env:ANDROID_HOME='C:\Users\Username\AppData\Local\Android\Sdk'
$env:ANDROID_SDK_ROOT='C:\Users\Username\AppData\Local\Android\Sdk'
& 'C:\Users\Username\.gradle\wrapper\dists\gradle-9.3.1-bin\23ovyewtku6u96viwx3xl3oks\gradle-9.3.1\bin\gradle.bat' assembleDebug
```

## Install

```powershell
& 'C:\Users\Username\AppData\Local\Android\Sdk\platform-tools\adb.exe' install -r 'C:\Users\Username\Documents\VR.app\spikes\PicoOpenXrExtensionProbe\app\build\outputs\apk\debug\app-debug.apk'
```

## Test flow

### Test 1: Home mode

1. Exit `Pico Connect`.
2. Launch `PICO OpenXR Passthrough Probe` from the headset app list.
3. Wait until the status says the probe has finished.
4. Capture the on-screen report.

### Test 2: Pico Connect mode

1. Start `Pico Connect`.
2. While streaming mode is active, try to launch `PICO OpenXR Passthrough Probe`.
3. If it launches, wait for the report and capture it.
4. If it cannot be launched or immediately loses focus, note that behavior explicitly.

## What to compare

The most important lines are:

- `system_get_result`
- `fb_passthrough.supports_passthrough`
- `graphics_requirements_result`
- `session_create_result`
- `session_state_event`
- `session_begin_result`
- `fb_passthrough.create_result`
- `fb_passthrough.layer_create_result`
- `coexistence_verdict`

## Interpretation

- `session_create_result=XR_SUCCESS` and `fb_passthrough.create_result=XR_SUCCESS`
  The current launch mode accepts both the XR session and passthrough object creation path.

- `session_create_result=XR_SUCCESS` but `fb_passthrough.create_result!=XR_SUCCESS`
  The runtime is alive, but passthrough itself is restricted in that mode.

- `instance/system` work but `session_create_result` fails
  The runtime can be reached, but immersive coexistence is blocked in that mode.

- app cannot be launched while `Pico Connect` is active
  Multi-app coexistence is likely blocked before our OpenXR code even runs.

## Third-party headers

This spike vendors official Khronos OpenXR headers:

- `app/src/main/cpp/third_party/openxr/openxr.h`
- `app/src/main/cpp/third_party/openxr/openxr_platform_defines.h`

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

