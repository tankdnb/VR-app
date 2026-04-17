# PICO Connect Constraint

- Date: `2026-04-09`
- Target workflow: `PICO 4 Pro` used with `Pico Connect` for PC VR streaming.
- Hard product requirement: the "reality window" must work while the headset is actively receiving the PC-rendered scene through `Pico Connect`.

## Why this changes the engineering decision

An on-device MR or passthrough prototype is not enough by itself.

If passthrough only works from the headset home environment, but becomes unavailable or inaccessible once the user enters a `Pico Connect` streaming session, then the product does not satisfy the intended use case.

The real target is no longer just:

- "Can PICO show passthrough on-device?"

The real target is:

- "Can a user see a controlled passthrough window while a PC VR scene is being streamed through Pico Connect?"

## What is already confirmed

### Local validation on the current device

On the tested headset/runtime combination:

- headset class: `PICO 4 Pro`
- observed runtime environment during PC testing: `PICO 4S / pico` through `SteamVR/OpenVR`
- on-device OS family observed through `adb`: `PICO OS 5.12.0`

The repository already proved:

- `SteamVR/OpenVR` overlay rendering works on the headset during PC VR streaming;
- `SteamVR/OpenVR` tracked camera access does **not** work on this runtime;
- official on-device `OpenXR` initialization works when running locally on the headset;
- the on-device runtime advertises:
  - `XR_PICO_passthrough`
  - `XR_FB_passthrough`
  - `XR_BD_external_camera`
  - `XR_BD_mr_management`
- the on-device runtime does **not** advertise:
  - `XR_PICO_camera_image`
  - `XR_PICO_external_camera`
  - `XR_PICO_secure_mixed_reality`

## What official PICO materials suggest

Official PICO sources point in two important directions.

### 1. PICO is moving toward multi-application spatial computing

PICO's `2024-12-17` article "Advancing Open Standards for Spatial Computing: Multi-Application Support and Rendering Architectures" describes simultaneous mixed-reality multi-app scenarios as an important direction for spatial computing.

This is encouraging, because our product is fundamentally a utility layer coexisting with another immersive workload.

### 2. PICO explicitly markets simultaneous PICO Connect support for PICO 4 Ultra

On the current PICO developer `PICO 4 Ultra` page, PICO Developer Center is described as being "enhanced by PICO 4 Ultra's simultaneous PICO Connect support."

This matters because it is the clearest official sign that PICO is thinking about development and testing workflows where local spatial features coexist with `Pico Connect`.

## What is still unproven

For the tested `PICO 4 Pro / PICO OS 5.12.0` setup, we do **not** yet have official evidence that:

- an app-local passthrough layer can remain active during an active `Pico Connect` session;
- `XR_FB_passthrough` or `XR_PICO_passthrough` remain usable when the headset is acting as a streaming client;
- `Pico Connect` allows third-party app composition on top of the streamed VR scene on this device generation;
- `PICO 4 Pro` has the same "simultaneous Pico Connect support" that PICO explicitly advertises for `PICO 4 Ultra`.

## Practical consequence

This changes the roadmap.

The next technical spike should no longer be framed as:

- "Can we show passthrough on a standalone PICO app?"

It should now be framed as:

- "Can we activate passthrough or a scoped MR layer while `Pico Connect` streaming is active on `PICO 4 Pro`?"

## Recommended next spike

### Spike goal

Build a minimal on-device `OpenXR` test app that:

- creates an instance/session on the headset;
- attempts to enable `XR_FB_passthrough` and/or `XR_PICO_passthrough`;
- clearly reports success/failure on-screen;
- is tested in two conditions:
  - from normal headset home mode;
  - during an active `Pico Connect` PC streaming session.

### Pass criteria

At least one of these must be true during `Pico Connect`:

1. passthrough can be activated inside a local app while the streaming session is active;
2. the runtime exposes a composition path that lets a local MR layer coexist with streamed PC VR content;
3. `Pico Connect` itself exposes a documented or discoverable extension point for this kind of overlay.

### Failure criteria

If passthrough only works in headset home mode and is blocked or hidden once `Pico Connect` starts, then:

- the current `PICO 4 Pro + Pico Connect` product target is not feasible in the intended form;
- we would need either:
  - a different headset/runtime path;
  - a different streaming stack;
  - or a revised product scope.

## Decision update

Until proven otherwise, the product should now be treated as:

- `OpenVR overlay viability`: **proven**
- `raw camera path during SteamVR streaming`: **blocked**
- `on-device passthrough capability`: **promising**
- `passthrough during Pico Connect streaming`: **critical unvalidated blocker**
