# OpenXR SteamVR Passthrough Reuse Plan

- Date: `2026-04-10`
- Source repo: `Rectus/openxr-steamvr-passthrough`
- Repo URL: `https://github.com/Rectus/openxr-steamvr-passthrough`

## Short verdict

This is the closest public reference to the original product idea on the PC/SteamVR side.

It is useful as:

- an architecture reference;
- a donor of calibration and compositing ideas;
- a possible alternative base **if** the product is reframed as a `SteamVR OpenXR API layer`.

It is **not** a proof that the same thing will work with `Pico Connect` on `PICO 4 Pro`.

## What the repo clearly proves

The project explicitly states:

- it is an `OpenXR API layer for providing camera passthrough support to SteamVR`;
- SteamVR itself does not expose OpenXR passthrough, so the layer uses proprietary `OpenVR` camera feeds and projection data;
- it can also use a `USB camera`;
- it inserts itself between the `OpenXR` application and the SteamVR runtime and composites passthrough before frames are passed to the runtime.

This is very close to the original "window to reality in PC VR" direction, but the implementation model is different from our initial companion overlay app.

## Most useful parts for us

### 1. API-layer architecture

The strongest reusable idea is architectural:

- instead of building only an external SteamVR companion overlay,
- build an `OpenXR API layer` that modifies what OpenXR applications see and submit.

That is a better fit for real passthrough compositing than our current external overlay shell.

### 2. Camera-source abstraction

The repo supports:

- `OpenVR` HMD camera input;
- `USB camera` input.

This aligns well with our earlier provider abstraction idea.

The `USB camera` path is especially important because it gives us a fallback concept for headsets whose onboard camera is not exposed to SteamVR.

### 3. Calibration and projection ideas

The repository contains dedicated modules for:

- camera calibration;
- fisheye rectification;
- floor projection adjustment;
- stereo reconstruction depth.

Those are directly relevant if we ever revisit a camera-window product using:

- an external webcam mounted to the headset;
- a stereo camera rig;
- or another tracked camera source.

### 4. SteamVR dashboard menu pattern

The repo includes:

- a settings overlay in the SteamVR dashboard;
- runtime configuration of opacity, color parameters, overrides, and passthrough modes.

That is useful for our wrist/panel UX and for quick iteration on VR controls.

### 5. Blend-mode and depth-compositing ideas

The README and releases show support for:

- alpha blend;
- additive blend;
- chroma key masking;
- depth blending;
- partial `XR_FB_passthrough`;
- temporal filtering.

These ideas are relevant for any future visual utility layer or mixed-reality compositor work.

## What it does not solve for us

### 1. It does not bypass the `Pico Connect` blocker

The repo explicitly states:

- only the `SteamVR` runtime is supported;
- only HMD cameras that expose the feed to SteamVR are supported;
- if SteamVR `Room View` does not work, the HMD camera is not accessible.

That matches our own finding on `PICO 4 Pro / Pico Connect`: the headset camera path is the blocker.

### 2. It is not an external overlay companion app

Our current project already proved:

- external `OpenVR` overlays;
- hand/world anchoring;
- panel UX direction.

This repo solves a different layer of the stack:

- in-app compositing through an OpenXR API layer.

So this is not a drop-in merge with our current architecture.

### 3. It only helps OpenXR applications

The README explicitly says:

- `OpenVR applications are not supported`.

That means even on PC it is not a universal SteamVR passthrough solution.

## Best practical uses for our project

### Option A: Reference only

Use it as a donor for:

- calibration UX;
- compositing modes;
- filtering ideas;
- config model;
- dashboard integration ideas.

This is the lowest-risk use.

### Option B: Pivot to API-layer architecture

If we ever return to the original passthrough goal on PCVR, the more promising architecture is:

- `OpenXR API layer`

rather than:

- pure external overlay companion app.

That would make this repo a much more direct starting point.

### Option C: External camera variant

If onboard `PICO` cameras remain inaccessible during `Pico Connect`, the repo still suggests a possible workaround path:

- attach a `USB camera` or stereo camera to the headset;
- calibrate it;
- track it as a SteamVR device or rigid transform;
- render that feed as the "reality window".

This would not be true headset passthrough, but it could approximate the product idea.

## Recommendation

Use this repo as:

- the best reference for the original PC/SteamVR passthrough concept;
- not as proof that `Pico Connect` can expose the real headset camera;
- and not as a direct replacement for our current overlay utility architecture.

If we revisit passthrough later, the smartest move would be:

1. keep our overlay/panel UX work;
2. borrow concepts from this repo;
3. decide whether to pivot the rendering side to an `OpenXR API layer`;
4. seriously consider an external tracked camera fallback if onboard `PICO` camera access stays blocked.
