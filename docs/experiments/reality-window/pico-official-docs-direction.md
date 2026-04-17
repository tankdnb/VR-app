# PICO Official Docs Direction

- Date: `2026-04-09`
- Focus device: `PICO 4 Pro`
- Goal: decide whether the MVP should stay on `SteamVR/OpenVR` or pivot to an official `PICO` integration path.

## What the official PICO materials confirm

### 1. PICO has first-party development paths for MR and passthrough

The official documentation index exposes dedicated XR capability areas including:

- `Rendering`
- `Input & tracking`
- `Mixed reality`
- `Spatial audio`

Source:

- [PICO documentation index](https://developer.picoxr.com/document/)

### 2. PICO Unity docs include a dedicated passthrough page

There is an official Unity documentation page for passthrough:

- [Unity XR Platform SDK passthrough](https://developer.picoxr.com/document/unity/unity-xr-platform-passthrough)

This is a strong signal that the vendor-supported path for "show the real world in XR" is not an OpenVR tracked-camera trick, but a first-party XR/MR SDK path.

### 3. PICO native docs include a dedicated see-through camera page

The official native documentation payload contains a page with:

- title: `image`
- path: `en_seethroughcamere`
- nearby native API sections:
  - `render`
  - `feature`
  - `Sensor tracking`
  - `Vulkan`

The same payload also exposes keywords associated with that page that include references to:

- `image`
- `left eye`
- `right eye`

This is not yet a full body-text extraction, but it is a strong official indicator that PICO has a native API surface around see-through camera imagery.

Sources:

- [Native see-through camera page URL](https://developer.picoxr.com/document/native/en_seethroughcamere/)
- [Native render page URL](https://developer.picoxr.com/document/native/en_render/)
- [Native feature page URL](https://developer.picoxr.com/document/native/en_feature/)

### 4. PICO is explicitly moving its platform toward OpenXR

Official PICO materials state:

- PICO native OpenXR development supports the Khronos OpenXR Android Loader starting from OS `5.9.0`
- the runtime is officially `OpenXR 1.1` compliant as of `2024-11-19`
- current Unity and Unreal SDK messaging is centered around OpenXR

Sources:

- [PICO news / blog index](https://developer.picoxr.com/news)
- [PICO developer home](https://developer.picoxr.com/)

### 5. Official native spec now exposes two very different PICO paths

The official native OpenXR spec payload contains:

- `XR_PICO_camera_image`, which explicitly describes acquiring camera image data, intrinsics, extrinsics, capture sessions, and `android.permission.CAMERA`;
- `XR_PICO_secure_mixed_reality`, which explicitly says the calling app does not obtain camera or sensor data back, because the isolated SecureMR service keeps sensitive data inside the runtime boundary.

Practical consequence:

- `XR_PICO_camera_image` is the path that can potentially feed our overlay window with real frames;
- `XR_PICO_secure_mixed_reality` is useful for privacy-preserving MR workloads, but by itself does not satisfy our current product model of "show the camera image inside our own utility window".

## What this means for our MVP

## Recommended primary architecture

For a `PICO 4 Pro`-first MVP, the most promising implementation path is now:

1. `PICO official SDK / OpenXR / native Android path` for camera or passthrough access.
2. `SteamVR/OpenVR overlay` only as a fallback experiment or compatibility path.

Reason:

- our local `OpenVR tracked camera` probe already failed on a PICO runtime;
- official PICO materials clearly expose MR/passthrough/see-through documentation on their own stack;
- official platform messaging increasingly centers on `OpenXR`, not `OpenVR`.

## Practical implication for the codebase

The project should no longer treat `OpenVRTrackedCameraProvider` as the likely production provider for PICO.

Instead, the provider roadmap should become:

1. `PicoOfficialProvider` or `PicoOpenXrProvider`
2. `OpenVRTrackedCameraProvider` as a compatibility probe
3. `ExternalCameraProvider` / `TestPatternProvider` as fallbacks

## What is still unclear

These are the main unknowns that official page structure does not fully answer yet:

1. Does `PICO 4 Pro` expose the same MR / passthrough / see-through camera functionality as newer `PICO 4 Ultra` and `PICO OS 6` materials?
2. Does the official API return raw camera frames, or only enable compositor-level passthrough?
3. Are there permission, entitlement, or enterprise-only gates for camera image access?
4. Is the useful path a `Unity/OpenXR` app, a `native Android/OpenXR` app, or both?
5. Can a vendor-native MR layer coexist with the exact world-space utility window UX we want, or do we need to emulate it ourselves with textured quads?
6. Does the actual headset runtime advertise `XR_PICO_camera_image`, or only `XR_PICO_secure_mixed_reality`?

## Updated recommendation

### Keep

- current `OpenVR` probe utility
- current overlay scaffold
- current source abstraction

### Add next

- a new `PICO official SDK` investigation spike
- a `PicoOfficialProvider` interface stub
- a second executable spike that runs on-device instead of only through SteamVR on PC

### Do not assume anymore

- that `SteamVR/OpenVR tracked camera` is the right production path for `PICO 4 Pro`

## Suggested next spike

Build a minimal on-device `PICO` prototype that answers only four questions:

1. Does the headset runtime advertise `XR_PICO_camera_image`, `XR_EXT_future`, and `XR_PICO_secure_mixed_reality`?
2. If `XR_PICO_camera_image` exists, can we obtain raw camera imagery with permission and capture sessions?
3. Can we render that content onto a movable quad in world space?
4. Can we toggle it quickly enough for the `temporary peek` use case?

If the answer is yes, the app architecture should pivot from `SteamVR companion overlay` to `PICO-native/OpenXR MR utility`.

If the answer is no, we keep the current OpenVR prototype as a research branch and reconsider the product scope.
