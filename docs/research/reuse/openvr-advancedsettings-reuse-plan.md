# OpenVR-AdvancedSettings Reuse Plan

- Date: `2026-04-10`
- Source repository:
  [OpenVR-Advanced-Settings/OpenVR-AdvancedSettings](https://github.com/OpenVR-Advanced-Settings/OpenVR-AdvancedSettings)
- Goal: capture what `VR.app` can realistically learn from and apply from
  `OpenVR-AdvancedSettings`.

## Why this project matters

`OpenVR-AdvancedSettings` is one of the strongest public references for a mature
`SteamVR utility suite`, not just a single overlay.

It matters because it proves that users value an in-VR control surface for:

- runtime tweaks
- playspace tools
- chaperone control
- bindings and hotkeys
- media and keyboard shortcuts
- audio controls
- statistics and device information
- small utility functions like alarms, markers, or battery overlays

From the repo README, the project explicitly positions itself as an overlay that
adds "advanced settings and useful utilities" to the OpenVR dashboard and makes
the same features available in a desktop window as well.

## Strongest things to borrow

### 1. Product shape: a utility suite, not one isolated tool

The biggest lesson is product-level:

- one runtime
- one overlay shell
- many small utilities inside it

This is exactly aligned with the direction `VR.app` has been moving toward.

Useful evidence from the upstream repo:

- the README feature list spans motion, audio, keyboard, media, statistics,
  chaperone, and SteamVR controls
- the UI is split into focused pages instead of one overloaded panel
- the same functionality is exposed in both VR and desktop contexts

## What is most reusable for VR.app

### 1. Tabbed utility architecture

The repo has dedicated tab controllers for major areas:

- `SteamVRTabController`
- `ChaperoneTabController`
- `MoveCenterTabController`
- `RotationTabController`
- `AudioTabController`
- `VideoTabController`
- `UtilitiesTabController`
- `StatisticsTabController`
- `SettingsTabController`

This is visible in:

- `.tmp/OpenVR-AdvancedSettings/src/tabcontrollers`

What to apply in `VR.app`:

- keep features modular by domain
- one controller per utility area
- one shared overlay shell that hosts multiple panels
- easy growth from one MVP utility into a suite

This is one of the clearest architecture patterns we should reuse.

### 2. Overlay plus desktop companion model

The README explicitly says all major features are available in VR and from a
desktop window.

What to apply in `VR.app`:

- do not force every workflow to happen only in-headset
- keep a desktop companion for diagnostics, setup, and advanced configuration
- expose the same core feature set through two surfaces when useful

This is especially relevant for:

- `OpenXR Doctor`
- runtime/layer diagnostics
- device inventory
- calibration setup
- accessibility configuration

### 3. Strong input/binding model

The project has one of the best public SteamVR input guides among utility apps.
Its binding system includes:

- action sets
- chords
- long hold / held / touch activation types
- haptics
- system actions that remain available
- keyboard shortcuts and key presses

Primary source:

- `.tmp/OpenVR-AdvancedSettings/docs/SteamVRInputGuide.md`
- `.tmp/OpenVR-AdvancedSettings/docs/keyboard_input_guide.md`

What to apply in `VR.app`:

- action-based bindings instead of hard-coded controller buttons
- chord support for global utility actions
- separate always-available system actions
- haptic feedback as first-class UX for utility tools
- keyboard/macro bridges as a real utility feature, not an afterthought

### 4. Typed settings architecture

This repo has especially useful internal documentation for a settings API that
moves away from ad-hoc string keys.

Primary sources:

- `.tmp/OpenVR-AdvancedSettings/docs/specs/Settings-API.md`
- `.tmp/OpenVR-AdvancedSettings/docs/specs/Settings-Object-API.md`

What is valuable:

- typed enum-backed settings
- grouped settings categories
- default values for every setting
- explicit save/load API
- separate object-persistence API for more complex profile-like objects

What to apply in `VR.app`:

- move beyond plain JSON bag-of-fields over time
- define typed categories for settings
- add structured object persistence for profiles, widgets, and layouts
- keep one global settings service instead of scattered direct storage calls

This is one of the most immediately reusable engineering ideas in the repo.

### 5. Shared controller registration into UI

The `OverlayController` registers multiple controllers into the QML layer as
singletons and then treats them as globally accessible utility modules.

Primary source:

- `.tmp/OpenVR-AdvancedSettings/src/overlaycontroller.cpp`

What to apply in `VR.app`:

- one shell/controller that owns runtime lifecycle
- domain-specific controllers registered into the UI layer
- keep UI declarative and feature logic in separate controllers

Even if we do not use Qt/QML long term, the separation pattern is very useful.

### 6. Utility micro-features as composable modules

`UtilitiesTabController` is a good reminder that small utilities still matter.
It includes things like:

- keyboard sends
- media keys
- battery overlays for tracked devices
- simple toggles

Primary source:

- `.tmp/OpenVR-AdvancedSettings/src/tabcontrollers/UtilitiesTabController.h`

What to apply in `VR.app`:

- battery widgets
- keyboard/macro actions
- media controls
- tiny focused wrist widgets
- feature flags for optional micro-tools

This strongly supports the "many small useful tools" direction for `VR.app`.

### 7. Statistics and health panels

`StatisticsTabController` tracks HMD movement, rotations, controller max speed,
and compositor frame stats such as presented/dropped/reprojected frames.

Primary source:

- `.tmp/OpenVR-AdvancedSettings/src/tabcontrollers/StatisticsTabController.h`

What to apply in `VR.app`:

- metrics overlay
- movement/session statistics
- controller-speed diagnostics
- session resettable counters

This is a strong reference for a future `VR.app metrics` feature set.

### 8. SteamVR system integration and per-app bindings

`SteamVRTabController` shows a mature utility interacting with:

- SteamVR settings
- camera toggles
- pairing flows
- custom bindings
- WebSocket/network-backed interactions
- app-specific binding application

Primary source:

- `.tmp/OpenVR-AdvancedSettings/src/tabcontrollers/SteamVRTabController.h`

What to apply in `VR.app`:

- per-app profiles
- pairing helpers
- runtime state toggles
- "device manager" and "runtime helper" modules

## Best product ideas to borrow

The strongest product-level ideas from `OpenVR-AdvancedSettings` are:

1. `Wrist dashboard` or utility root panel
2. `Play space tools`
3. `Chaperone / room tools`
4. `Keyboard and media bridge`
5. `Battery and device widgets`
6. `Metrics and health stats`
7. `Profiles and per-app behavior`

## What VR.app should not copy directly

### 1. The whole suite as one monolith

`OpenVR-AdvancedSettings` is powerful, but it is also broad.
For `VR.app`, it is better to preserve modularity and build smaller utilities
that share one foundation.

### 2. Direct GPL code reuse without a licensing decision

The upstream project is `GPL-3.0`.
That means:

- it is excellent as a reference
- direct code reuse requires deliberate licensing choices

For now, treat it primarily as:

- architecture reference
- UX reference
- product reference

### 3. Qt/QML specifics as mandatory architecture

The exact Qt/QML stack is not the point.
The reusable part is:

- shell + controllers
- typed settings
- dual VR/desktop surface model
- modular utility tabs

## Concrete VR.app applications

The most direct uses for `VR.app` are:

### Near-term

- `Wrist Dashboard`
- `Device Monitor Overlay`
- `Metrics Overlay`
- `Keyboard / Hotkey Bridge`

### Medium-term

- `Room Tools`
- `Per-app utility profiles`
- `Desktop companion for VR tool configuration`

### Long-term

- richer utility suite that still stays modular

## Bottom line

`OpenVR-AdvancedSettings` is one of the most important repositories in the
entire `VR.app` research base because it proves that:

- utility overlays can become a serious product
- one shared shell can host many tools
- desktop and VR surfaces should coexist
- typed settings and action-based bindings matter
- small micro-features add up to real user value

If `DesktopPlus` is the best reference for desktop windows in VR, then
`OpenVR-AdvancedSettings` is one of the best references for a broad
SteamVR utility platform.

