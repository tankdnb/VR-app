# PICO Connect Passthrough Spike

- Date: `2026-04-09`
- Target headset: `PICO 4 Pro`
- Target OS observed earlier: `PICO OS 5.12.0`
- Critical product constraint: the reality window is only valuable if it coexists with `Pico Connect` PC streaming.

## What was prepared

The Android probe was upgraded from a simple extension inspector to a minimal runtime capability spike.

The new version now attempts:

- `xrCreateInstance`
- `xrGetSystem`
- `xrGetSystemProperties`
- `xrGetOpenGLESGraphicsRequirementsKHR`
- `xrCreateSession`
- session state polling
- `xrBeginSession`
- `xrCreatePassthroughFB`
- `xrPassthroughStartFB`
- `xrCreatePassthroughLayerFB`
- `xrPassthroughLayerResumeFB`

## Why this spike is the right next step

The repository has already proven:

- `OpenVR` overlays work on the headset during PC VR streaming;
- `OpenVR tracked camera` access does not work on the current `PICO` runtime;
- official on-device `OpenXR` loader initialization works;
- the runtime advertises `XR_FB_passthrough` and `XR_PICO_passthrough`.

The missing answer is no longer:

- "Does PICO have any passthrough capability at all?"

The missing answer is:

- "Does a local OpenXR passthrough path still work while Pico Connect is active?"

## Current test artifact

Latest built APK:

- Local build output: `spikes/PicoOpenXrExtensionProbe/app/build/outputs/apk/debug/app-debug.apk`

## Expected evaluation pattern

Run the same app in two situations:

1. normal headset home mode;
2. active `Pico Connect` streaming mode.

Then compare:

- whether the app can launch at all;
- whether `XrSession` creation succeeds;
- whether `XR_FB_passthrough` object creation succeeds.

## Current baseline before manual dual-mode testing

A local smoke run from the connected headset already produced one very important checkpoint sequence:

- `checkpoint.system_get_result=XR_SUCCESS`
- `checkpoint.graphics_requirements_result=XR_SUCCESS`
- `checkpoint.before_xrCreateSession`
- `checkpoint.after_xrCreateSession=XR_SUCCESS`
- `checkpoint.before_xrCreatePassthroughFB`

After that point, the probe did not reach a matching `after_xrCreatePassthroughFB` line within the quick smoke window.

This means:

- `OpenXR` instance and system creation are alive;
- `OpenGL ES` graphics requirements are available;
- `XrSession` creation works;
- the first observed deep stall is inside or below `xrCreatePassthroughFB`.

That is now the baseline to compare against when you run the same app manually in:

1. headset home mode;
2. active `Pico Connect` mode.

## Decision logic

- success in both modes:
  the `Pico Connect` coexistence hypothesis stays alive.

- success only in home mode:
  `Pico Connect` is the blocker, not basic OpenXR passthrough.

- failure in both modes:
  even standalone passthrough session creation is not yet good enough on this path.

