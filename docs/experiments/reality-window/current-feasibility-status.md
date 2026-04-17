# Current Feasibility Status

- Date: `2026-04-09`
- Environment: `Windows + .NET 8 + SteamVR/OpenVR runtime`
- Detected HMD during local probe: `PICO 4S`
- Detected OpenVR tracking system name: `pico`

## What was validated

- MVP scaffold builds successfully.
- `probe` command works.
- `test-pattern` source works and exports a frame.
- OpenVR runtime initializes on this machine.

## What is currently blocked on this machine

- `tracked-camera` probe reports that the HMD does not expose a camera through `SteamVR/OpenVR`.
- This means the exact product idea, in the form "read external HMD camera via OpenVR and show it as overlay", is not currently proven on this headset/runtime combination.

## Practical implication

Right now the application is technically capable of:

- creating the MVP runtime structure;
- probing for tracked camera support;
- rendering a raw OpenVR overlay;
- switching between world and hand anchor modes;
- using a fallback source for overlay pipeline testing.

But it is not yet able to show real camera passthrough on this detected `PICO 4S`, because the runtime does not expose that feed through the tracked camera API.

## Next decision point

To continue toward the real product, one of these needs to be true:

1. another target headset/runtime combination exposes tracked camera through OpenVR;
2. a non-OpenVR camera path is available for the target device;
3. the product scope changes from "real HMD camera feed" to another external source.

## Updated direction after reviewing official PICO documentation

Official PICO materials now make option `2` much more realistic than it first looked.

What is officially visible:

- PICO publishes dedicated documentation for `Mixed reality` and Unity `passthrough`.
- PICO native docs expose a dedicated `see-through camera` page path.
- Recent official platform messaging is centered around `OpenXR`, not `OpenVR`.

Practical consequence:

- `OpenVRTrackedCameraProvider` should remain a compatibility probe.
- The most promising production path for `PICO 4 Pro` is now a vendor-specific `PICO/OpenXR` integration.
- The next hard gate is not "does PICO have MR docs", but "does the on-device runtime actually advertise `XR_PICO_camera_image` plus `XR_EXT_future`".
- Official `SecureMR` is important, but it is not equivalent to raw camera access: it does not return camera or sensor data back to the app.

Reference:

- [PICO official docs direction](./pico-official-docs-direction.md)
- [PICO raw camera vs SecureMR notes](./pico-openxr-camera-path.md)

## New on-device result from official OpenXR loader probe

An on-device Android probe was then rebuilt around the official Khronos Android loader path and run directly on `PICO 4 Pro`.

What was validated:

- the bundled official `libopenxr_loader.so` initializes successfully on-device;
- `xrInitializeLoaderKHR` succeeds;
- `xrEnumerateInstanceExtensionProperties` succeeds;
- `xrCreateInstance` succeeds on the headset runtime.

What the runtime actually advertises:

- `XR_KHR_android_create_instance`: `true`
- `XR_KHR_loader_init_android`: `true`
- `XR_PICO_camera_image`: `false`
- `XR_EXT_future`: `false`
- `XR_PICO_secure_mixed_reality`: `false`
- `XR_PICO_external_camera`: `false`
- `XR_PICO_passthrough`: `true`
- `XR_FB_passthrough`: `true`
- `XR_BD_external_camera`: `true`
- `XR_BD_mr_management`: `true`

Practical consequence:

- the original raw-camera hypothesis for `PICO 4 Pro` is now weaker than before;
- the runtime does not advertise the expected `XR_PICO_camera_image` path;
- the next realistic path is no longer "raw camera frame ownership first";
- the next realistic path is now a vendor-extension probe around:
  - `XR_PICO_passthrough`
  - `XR_FB_passthrough`
  - `XR_BD_external_camera`
  - `XR_BD_mr_management`

That means the product may still be feasible on `PICO`, but the likely implementation model has shifted toward passthrough-layer or vendor-MR integration rather than direct raw camera acquisition.

## New critical product constraint: must work during Pico Connect streaming

The target use case has now been clarified further:

- the app is only valuable if it works while `Pico Connect` is actively streaming the PC-rendered VR scene to the headset;
- a passthrough or MR proof-of-concept that only works from the standalone headset home environment is not sufficient.

This changes the meaning of the next feasibility gate.

It is no longer enough to prove:

- `passthrough works on-device`

We now need to prove:

- `passthrough or an equivalent scoped reality layer still works while Pico Connect is active`

Important current status:

- official PICO materials explicitly mention `PICO 4 Ultra` having "simultaneous PICO Connect support";
- this is encouraging, but it is not the same as proof for the tested `PICO 4 Pro / PICO OS 5.12.0` setup;
- we do not yet have proof that `XR_FB_passthrough`, `XR_PICO_passthrough`, or `XR_BD_*` capabilities remain available during a live `Pico Connect` session.

Practical consequence:

- the next spike must test passthrough under two conditions:
  - headset home mode;
  - active `Pico Connect` streaming mode.

Reference:

- [PICO Connect constraint](./pico-connect-constraint.md)

## New baseline from the passthrough coexistence spike

The Android probe was upgraded again to attempt:

- `xrCreateInstance`
- `xrGetSystem`
- `xrGetOpenGLESGraphicsRequirementsKHR`
- `xrCreateSession`
- `xrCreatePassthroughFB`

On a local smoke run from the current headset environment, the new checkpoints showed:

- `system_get_result = XR_SUCCESS`
- `graphics_requirements_result = XR_SUCCESS`
- `xrCreateSession = XR_SUCCESS`
- execution then stalled when entering `xrCreatePassthroughFB`

Practical consequence:

- the current runtime is capable of getting much farther than simple extension enumeration;
- immersive session creation is not the first blocker;
- the first visible deep blocker is now passthrough object creation itself;
- this makes the next comparison very concrete:
  - if the same stall happens in headset `Home`, passthrough initialization itself is unstable or gated;
  - if it only happens differently under `Pico Connect`, streaming coexistence is adding another blocker layer.

Reference:

- [PICO Connect passthrough spike](./pico-connect-passthrough-spike.md)
