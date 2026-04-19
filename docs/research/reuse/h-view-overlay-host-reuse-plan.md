# h-view Overlay Host Reuse Plan

- Date: `2026-04-19`
- Source repository:
  [hai-vr/h-view](https://github.com/hai-vr/h-view)
- Goal: capture what `VR-apps-lab` can realistically learn from and apply from
  the `overlay-host` slice of `h-view`.

## Why this project matters

`h-view` is one of the strongest public references in the repo for a modern
`overlay-first utility host` that still keeps `desktop parity`.

It matters because it proves that one utility shell can combine:

- a desktop window;
- a SteamVR dashboard overlay;
- device and hardware inventory;
- OSCQuery-style control features;
- saved user preferences;
- alternate overlay input models such as eye tracking.

That is much closer to the long-term direction of `VR-apps-lab` than a
single-purpose overlay sample.

## Strongest things to borrow

### 1. One host, multiple surfaces

The biggest lesson is product-level:

- one app shell;
- one shared state model;
- more than one presentation surface.

Useful evidence from the repo:

- desktop mode is the default path;
- when SteamVR is available, the app can also create a dashboard overlay;
- the same host still owns settings, hardware state, and utility logic.

What to apply in `VR-apps-lab`:

- do not treat desktop and VR surfaces as separate products;
- keep one utility shell that can expose a desktop mode and one or more overlay
  modes;
- let the desktop surface remain useful for setup, diagnostics, and advanced
  configuration.

### 2. Immediate-mode UI rendered into an overlay

`HVImGuiOverlay.cs` is a strong donor because it shows how to:

- render a normal UI stack with `Veldrid`;
- pass a live texture pointer into OpenVR;
- keep overlay input separate from desktop-window input;
- only render the overlay contents when the overlay is actually visible.

What to apply in `VR-apps-lab`:

- maintain a clean `renderer -> overlay texture` boundary;
- treat overlay input as its own abstraction instead of mixing it directly into
  the UI layer;
- avoid over-rendering when a dashboard surface is hidden.

### 3. Dedicated overlay input snapshot

`HVImGuiOverlay.cs` uses `HOverlayInputSnapshot` as a translation layer between
OpenVR events and the UI runtime.

What to apply in `VR-apps-lab`:

- create one normalized overlay-input model;
- feed mouse move, button, and scroll into that model;
- keep UI code independent from raw OpenVR event structs.

This is the cleanest reusable engineering pattern in the repo's overlay slice.

### 4. Action-manifest-driven overlay management

`HVOpenVRManagement.cs` does not hard-code everything around controller polling.
Instead it loads a SteamVR action manifest and resolves action handles for
open, interact, and grab behaviors.

What to apply in `VR-apps-lab`:

- prefer action-based overlay management controls;
- keep overlay-open and interact actions explicit;
- avoid binding critical overlay behavior to fixed controller buttons.

### 5. Saved-data and backup model

`SavedData.cs` is a useful example of lightweight but honest persistence:

- one JSON config;
- one backup copy;
- strong defaults;
- one home for hardware preferences and theme values.

What to apply in `VR-apps-lab`:

- give future overlay hosts a small persistence layer with backup support;
- group hardware or UI preferences in one place;
- keep config recovery simple and visible.

### 6. Eye-tracking as overlay pointer

The eye-tracking path inside `HVImGuiOverlay.cs` is especially interesting:

- it computes overlay intersections from eye origin plus gaze;
- it treats gaze as another pointer source;
- it keeps that logic optional instead of making it the only input path.

What to apply in `VR-apps-lab`:

- think of gaze as `optional overlay pointer augmentation`, not a separate app;
- keep pointer-source abstractions open for mouse, controller, or gaze.

## What is most reusable for VR-apps-lab

The best direct donors are:

- `overlay host shell` pattern;
- `renderer texture -> OpenVR overlay` handoff;
- `overlay input snapshot` translation layer;
- `action manifest` management path;
- `JSON plus backup` persistence for overlay preferences.

## What should not be copied blindly

- the full app scope, because `h-view` includes much more than the overlay path;
- feature sprawl, because the repo mixes overlay hosting, OSCQuery, OCR,
  hardware views, and external-service ideas;
- disabled or still-evolving overlay movement logic as a ready-made placement
  system.

## Best next reuse direction

The strongest practical reuse direction for `VR-apps-lab` is:

1. one `overlay host shell` that can run both in desktop mode and in a VR
   dashboard mode;
2. one normalized overlay-input abstraction;
3. one saved-data layer for overlay placement and utility preferences;
4. optional advanced pointer modes later, including gaze.
