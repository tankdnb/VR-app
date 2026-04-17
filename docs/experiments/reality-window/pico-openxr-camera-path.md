# PICO OpenXR Camera Path

- Date: `2026-04-09`
- Goal: clarify which official `PICO/OpenXR` path can actually satisfy the product requirement of showing real camera imagery inside our own window.

## What the official sources show

### 1. PICO now expects native OpenXR apps to use the Khronos Android loader

Official PICO messaging states that native OpenXR development supports the Khronos OpenXR Android Loader starting from OS `5.9.0`.

Source:

- [PICO Native OpenXR development supports OpenXR Android Loader](https://developer.picoxr.com/blog/muz6s63x/)

### 2. PICO officially supports OpenXR 1.1

PICO announced official `OpenXR 1.1` runtime compliance as of `2024-11-19`.

Source:

- [PICO officially supports the OpenXR 1.1 standard](https://developer.picoxr.com/blog/openxr-standard-1point1/)

### 3. The official native spec contains a raw camera extension

The current official native OpenXR spec payload includes `XR_PICO_camera_image`.

From the spec overview:

- it "enables applications to acquire image data from cameras on XR devices";
- it describes camera properties, capabilities, capture sessions, intrinsics, extrinsics, image acquisition, image data retrieval, and image release;
- it notes that Android runtimes may require `android.permission.CAMERA`.

### 4. The same spec also contains SecureMR, which is different

The current official native OpenXR spec payload also includes `XR_PICO_secure_mixed_reality`.

From the SecureMR overview:

- developers may find RGB cameras or depth data hard to access due to privacy concerns;
- the isolated SecureMR service executes the developer's algorithms;
- camera or sensor data are not returned to the calling application.

## Practical interpretation

For our product idea, the two official PICO paths are not interchangeable.

`XR_PICO_camera_image` is the path that could potentially give us real camera frames for:

- textured quads;
- our existing `Reality Window` model;
- explicit crop / tilt / opacity control in app space.

`XR_PICO_secure_mixed_reality` is useful for privacy-preserving MR, but it does not by itself satisfy:

- "get camera pixels back into our app";
- "pipe those pixels into our own overlay window";
- "treat the real-world image as a normal video source in our current architecture".

## What this means for implementation

The next official PICO feasibility gate is:

1. run an on-device OpenXR extension probe;
2. confirm whether the headset runtime advertises:
   - `XR_PICO_camera_image`
   - `XR_EXT_future`
   - `XR_PICO_secure_mixed_reality`
3. only if `XR_PICO_camera_image` is present, proceed to camera capture session implementation.

If the runtime exposes only `XR_PICO_secure_mixed_reality`, then the product likely needs one of these pivots:

- a SecureMR-driven architecture instead of raw-frame overlays;
- a compositor-layer passthrough model;
- a narrowed product scope that no longer depends on direct frame ownership.

## What the headset actually reported on-device

The repository now includes an Android probe that uses the official Khronos Android loader, successfully runs:

- `xrInitializeLoaderKHR`
- `xrEnumerateInstanceExtensionProperties`
- `xrCreateInstance`

On the tested `PICO 4 Pro` runtime, the result was:

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

This changes the engineering interpretation:

- the official loader path is valid;
- direct raw camera ownership is not the first visible capability on this runtime;
- the more promising next path is now passthrough and vendor MR extensions, not `XR_PICO_camera_image`.

In other words, `PICO` still looks promising for the product, but the likely implementation route has shifted from:

- `camera_image -> raw frame -> our window`

to something closer to:

- `passthrough / vendor MR extension -> evaluate whether it can be composited or scoped into a usable reality window`.

## Repo status

This repository now includes an on-device extension probe scaffold:

- [PicoOpenXrExtensionProbe](C:/Users/Username/Documents/VR.app/spikes/PicoOpenXrExtensionProbe/README.md)

That probe does not capture camera frames yet. It now answers two decisive questions:

- does the official Android loader path really work on-device?
- which actual extensions does the headset runtime advertise for camera/passthrough/MR?
