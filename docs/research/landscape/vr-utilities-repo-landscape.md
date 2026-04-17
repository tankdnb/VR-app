# VR Utilities Repo Landscape

- Date: `2026-04-10`
- Goal: consolidate useful ideas and reusable code paths from public VR utility projects for future tools built on top of our existing repository.

## Executive summary

The repo list splits naturally into 5 buckets:

1. `OpenXR/OpenVR layers and compatibility`  
   Good for runtime interception, API translation, loader patterns, and compatibility shims.

2. `Overlays, desktop access, and dashboard UX`  
   Best reference bucket for practical VR utilities we can actually ship soon.

3. `Tracking, calibration, input remapping, and device virtualization`  
   Strong for power-user tools, mocap, mixed-device setups, and debugging.

4. `Performance and post-processing`  
   Useful when we need native rendering tricks, texture pipelines, shaders, and frame-time optimization.

5. `SDKs and official foundations`  
   Core reference for low-level integration and long-term maintainability.

The best short-term product direction from this landscape is:

- `OpenVR/OpenXR utility overlays`
- `desktop/reference windows`
- `wrist dashboard / quick panel`
- `metrics + device status tools`
- `space / tracking calibration helpers`

The best long-term architecture direction is:

- `OpenXR API layer` for runtime-level utilities;
- `OpenVR overlay companion app` for fast and compatible SteamVR utilities.

## Strongest reuse candidates

If we optimize for practical reuse instead of curiosity, the top donors are:

1. `DesktopPlus` for desktop/window overlay UX, profiles, interaction, and real-world product polish.
2. `DesktopXR` for `OpenXR API layer`-based desktop overlay ideas.
3. `OpenVR-AdvancedSettings` for dashboard UX, bindings, space tools, and utility breadth.
4. `OpenXR-Toolkit` for API-layer structure, companion tooling, and rendering feature organization.
5. `ALVR` for Android/OpenXR bootstrap, standalone headset client structure, and passthrough extension handling patterns.
6. `OpenVR-SpaceCalibrator` for cross-tracking-space alignment and calibration UX.
7. `OpenVR-InputEmulator` and active forks for virtual devices, remapping, and motion-compensation concepts.
8. `Rectus/openxr-steamvr-passthrough` for SteamVR camera/passthrough architecture and calibration/projection ideas.
9. `Valve openvr` and `Khronos OpenXR-SDK-Source` as the primary low-level references.
10. `OVRLay`, `openvr_widgets`, and `OVRTools` as compact overlay-focused references.

## Reuse rules

### Good code donors

These are the projects most likely to give directly reusable implementation ideas for utilities:

- `DesktopPlus`
- `OpenVR-AdvancedSettings`
- `OpenVR-SpaceCalibrator`
- `OpenVR-InputEmulator`
- `OVRLay`
- `openvr_widgets`
- `OpenXR-Toolkit`
- `ALVR`
- `Rectus/openxr-steamvr-passthrough`
- `ValveSoftware/openvr`
- `KhronosGroup/OpenXR-SDK-Source`

### Architecture references only

These are valuable mostly for design patterns, not for copy-paste integration:

- `vrperfkit`
- `openvr_fsr`
- `xrizer`
- `OpenComposite`
- `Revive`
- `DesktopXR`
- `tracking-toolkit`

### Treat carefully

These need extra caution because they are forks, older hacks, or narrowly scoped:

- `Erimelowo/OpenVR-InputEmulator-Fixed`
- `wirelessdreamer/OpenVR-InputEmulator`
- `Stavdel/OpenVR-SpaceCalibrator`
- `OpenVRDesktopDisplayPortal`
- `r57zone/OpenVR-OpenTrack`
- `WMR-Passthrough`

### License caution

For a future product, licensing matters.

- `MIT / BSD / Apache` style repos are easier for selective code reuse.
- `GPL` repos are still great references, but direct code reuse can affect distribution strategy.
- `DesktopXR` is explicitly distributed under a proprietary binary license even though it includes OpenXR SDK components.

## Repository notes

### 1. `mbucchia/OpenXR-Toolkit`

- What it is:
  `OpenXR API layer` that adds upscaling, sharpening, foveated rendering, controller/hand input helpers, image adjustments, and other runtime tweaks.
- Useful for us:
  best public reference for `OpenXR API layer + companion app + runtime feature toggles`.
- Best ideas to borrow:
  API-layer structure, menu/companion split, rendering feature modularization, config handling.
- Caveat:
  the latest release page explicitly says support is discontinued and the author does not recommend it for newer games due to compatibility issues.
- Source:
  [repo](https://github.com/mbucchia/OpenXR-Toolkit)
  [releases](https://github.com/mbucchia/OpenXR-Toolkit/releases)

### 2. `fholger/vrperfkit`

- What it is:
  performance-oriented VR mod toolkit for `D3D11`, with `FSR`, `NIS`, `CAS`, and fixed foveated rendering.
- Useful for us:
  native post-processing helpers, shader pipeline ideas, texture path optimization.
- Best ideas to borrow:
  `D3D11` helper layer, post-process chain, timing/profiling hooks.
- Caveat:
  not a utility overlay framework; mostly rendering injection.
- Source:
  [repo](https://github.com/fholger/vrperfkit)

### 3. `fholger/openvr_fsr`

- What it is:
  older modified `openvr_api.dll` approach for `FSR/NIS` upscaling in `SteamVR` games.
- Useful for us:
  compact early reference for OpenVR-side interception and config evolution.
- Best ideas to borrow:
  lightweight hook structure, config simplicity, D3D11 upscaling path.
- Caveat:
  largely superseded by `vrperfkit`.
- Source:
  [repo](https://github.com/fholger/openvr_fsr)

### 4. `Supreeeme/xrizer`

- What it is:
  reimplementation of `OpenVR` on top of `OpenXR`, allowing OpenVR games to run without SteamVR.
- Useful for us:
  strong reference for `API translation` and `OpenVR -> OpenXR` compatibility logic.
- Best ideas to borrow:
  runtime redirection, shim architecture, testability mindset.
- Caveat:
  README calls it immature and points to OpenComposite as the more mature solution.
- Source:
  [repo](https://github.com/Supreeeme/xrizer)

### 5. `QuestCraftPlusPlus/OpenComposite`

- What it is:
  `OpenVR` implementation forwarding to an `OpenXR` runtime.
- Useful for us:
  compatibility runtime patterns, OpenVR interface emulation, config strategy.
- Best ideas to borrow:
  OpenVR compatibility shim concepts and config surface.
- Caveat:
  this fork is useful, but conceptually it belongs to the broader `OpenComposite/OpenOVR` family and is not itself a utility product.
- Source:
  [repo](https://github.com/QuestCraftPlusPlus/OpenComposite)

### 6. `alvr-org/ALVR`

- What it is:
  wireless PCVR streaming stack with server + standalone headset clients.
- Useful for us:
  Android/OpenXR client bootstrap, headset-side runtime handling, streaming architecture reference, vendor extension patterns.
- Best ideas to borrow:
  headset client architecture, Android packaging, OpenXR runtime integration, passthrough handling patterns.
- Caveat:
  not a utility overlay app base; too much streaming-specific infrastructure.
- Source:
  [repo](https://github.com/alvr-org/ALVR)
  [How ALVR works](https://github.com/alvr-org/ALVR/wiki/How-ALVR-works)

### 7. `glenimp617/DesktopXR`

- What it is:
  `OpenXR API layer` that renders a desktop overlay in VR using `DirectX 11/12`.
- Useful for us:
  one of the most relevant references for `OpenXR overlay utility` products.
- Best ideas to borrow:
  minimal desktop overlay layer concept, installer and registration model, OpenXR-first approach.
- Caveat:
  distributed as a binary under a proprietary license, so treat it as an architectural reference, not a code donor.
- Source:
  [repo](https://github.com/glenimp617/DesktopXR)

### 8. `elvissteinjr/DesktopPlus`

- What it is:
  advanced desktop/window access for `OpenVR`, with many overlays, profiles, browser overlays, keyboard, interaction, and performance monitoring.
- Useful for us:
  probably the best single reference for a polished `SteamVR utility overlay` product.
- Best ideas to borrow:
  overlay origin model, profile system, overlay actions, custom laser pointer, keyboard overlay, app-specific profiles, browser overlay concept.
- Caveat:
  GPL-licensed.
- Source:
  [repo](https://github.com/elvissteinjr/DesktopPlus)

### 9. `Hotrian/OpenVRDesktopDisplayPortal`

- What it is:
  older SteamVR utility that mirrors desktop windows into cross-game overlays.
- Useful for us:
  simple reference for window mirroring, crop, controller interaction, profiles, attachment modes.
- Best ideas to borrow:
  world/screen/controller attachment model and mirrored-window UX.
- Caveat:
  older project; development concluded and moved toward `OVRdrop`.
- Source:
  [repo](https://github.com/Hotrian/OpenVRDesktopDisplayPortal)

### 10. `Nyabsi/openvr-metrics`

- What it is:
  real-time VR profiling and monitoring utility with an in-VR overlay for frame
  timing, per-process metrics, resource usage, and device status.
- Useful for us:
  strong product reference for a `metrics overlay`.
- Best ideas to borrow:
  per-process metrics, FPS/frame timing, controller-mounted versus dashboard
  overlay split, resource visibility, device status, and in-overlay runtime
  controls.
- Caveat:
  uses a source-available but non-standard license (`Source First License
  1.1`), so treat it carefully as a donor.
- Source:
  [repo](https://github.com/Nyabsi/openvr-metrics)

### 11. `matzman666/OpenVR-InputEmulator`

- What it is:
  OpenVR driver that can create virtual controllers, emulate input, manipulate poses, remap buttons, and do motion compensation.
- Useful for us:
  massive reference for power-user utilities, virtual devices, remapping, and low-level pose/input tooling.
- Best ideas to borrow:
  shared-memory client/driver split, input remapping UX, virtual controller model, command-line automation.
- Caveat:
  hooks into driver internals and may break with SteamVR updates; GPL.
- Source:
  [repo](https://github.com/matzman666/OpenVR-InputEmulator)

### 12. `LibreVR/Revive`

- What it is:
  compatibility layer between Oculus SDK and `OpenVR/OpenXR`.
- Useful for us:
  excellent example of compatibility-layer design, dashboard integration, and injector/proxy architecture.
- Best ideas to borrow:
  runtime translation patterns, overlay/dashboard integration, install/update model.
- Caveat:
  much more about app compatibility than utility overlays.
- Source:
  [repo](https://github.com/LibreVR/Revive)
  [releases](https://github.com/LibreVR/Revive/releases)

### 13. `benotter/OVRLay`

- What it is:
  Unity-focused toolkit for building `OpenVR` overlays.
- Useful for us:
  compact and directly relevant reference if we ever prototype overlays in Unity.
- Best ideas to borrow:
  drag-and-drop overlay toolkit thinking, dashboard + in-game overlays, Unity UI interaction model.
- Caveat:
  older Unity-era toolkit.
- Source:
  [repo](https://github.com/benotter/OVRLay)

### 14. `OVRTools/WhereIsForward`

- What it is:
  small utility to help find the front/center of the VR space with an arrow.
- Useful for us:
  excellent example of a narrow, highly useful single-purpose VR utility.
- Best ideas to borrow:
  simple “one problem, one overlay” product thinking.
- Caveat:
  more product inspiration than low-level code donor in this pass.
- Source:
  [project page](https://ovrtools.dev/projects/whereisforward)
  [OVRTools](https://ovrtools.dev/)

### 15. `OVRTools/OpenVRDeviceBattery`

- What it is:
  taskbar app to monitor battery levels of `OpenVR` devices and show device info.
- Useful for us:
  small reference for polling device properties and presenting practical state outside VR.
- Best ideas to borrow:
  device info polling, simple UX, background utility architecture.
- Caveat:
  explicitly rough UX according to the README.
- Source:
  [repo](https://github.com/OVRTools/OpenVRDeviceBattery)

### 16. `ValveSoftware/openvr`

- What it is:
  official `OpenVR SDK`.
- Useful for us:
  primary source for application API, driver API, samples, and property/input definitions.
- Best ideas to borrow:
  everything low-level related to SteamVR/OpenVR should anchor here first.
- Caveat:
  SDK, not a product reference.
- Source:
  [repo](https://github.com/ValveSoftware/openvr)
  [wiki](https://github.com/ValveSoftware/openvr/wiki)

### 17. `ValveSoftware/steamvr_unity_plugin`

- What it is:
  Valve’s Unity plugin for `SteamVR`.
- Useful for us:
  good reference if we ever want rapid Unity-based tool prototyping.
- Best ideas to borrow:
  input models, controller models, interaction example structure.
- Caveat:
  mostly relevant for Unity apps, not native overlay apps.
- Source:
  [repo](https://github.com/ValveSoftware/steamvr_unity_plugin)

### 18. `ValveSoftware/unity-xr-plugin`

- What it is:
  OpenVR plugin for Unity’s XR API.
- Useful for us:
  useful when mapping Unity XR management to OpenVR loader/provider behavior.
- Best ideas to borrow:
  Unity XR plugin loading model and packaging.
- Caveat:
  older, specific to Unity XR API and OpenVR loader bridging.
- Source:
  [repo](https://github.com/ValveSoftware/unity-xr-plugin)

### 19. `OpenVR-Advanced-Settings/OpenVR-AdvancedSettings`

- What it is:
  dashboard overlay exposing advanced SteamVR settings and many utilities without leaving VR.
- Useful for us:
  one of the strongest references for a serious utility suite rather than a single app.
- Best ideas to borrow:
  bindings, space movement tools, chaperone controls, audio/media integration, stats, desktop companion parity.
- Caveat:
  broad and mature, but also GPL and somewhat “kitchen sink”.
- Source:
  [repo](https://github.com/OpenVR-Advanced-Settings/OpenVR-AdvancedSettings)

### 20. `pushrax/OpenVR-SpaceCalibrator`

- What it is:
  cross-tracking-system alignment tool with SteamVR dashboard calibration UX.
- Useful for us:
  best known reference for mixed tracking space calibration in SteamVR.
- Best ideas to borrow:
  calibration flow, device identification, profile storage, chaperone/bounds copying, driver + UI split.
- Caveat:
  drift still exists in some inside-out / wireless setups.
- Source:
  [repo](https://github.com/pushrax/OpenVR-SpaceCalibrator)
  [releases](https://github.com/pushrax/OpenVR-SpaceCalibrator/releases)

### 21. `Stavdel/OpenVR-SpaceCalibrator`

- What it is:
  Linux port of Space Calibrator with continuous calibration support.
- Useful for us:
  good reference for continuous drift correction and Linux-friendly mixed-tracking setups.
- Best ideas to borrow:
  continuous calibration concepts and mixed wireless/Lighthouse alignment behavior.
- Caveat:
  fork, narrower ecosystem, no published releases.
- Source:
  [repo](https://github.com/Stavdel/OpenVR-SpaceCalibrator)

### 22. `SDraw/openvr_widgets`

- What it is:
  set of simple SteamVR overlay widgets such as stats and keyboard widgets.
- Useful for us:
  very relevant reference for lightweight modular widgets instead of one giant utility app.
- Best ideas to borrow:
  widget model, controller-bound stats widget, keyboard widget, small focused overlay design.
- Caveat:
  older project, limited polish compared with modern utility suites.
- Source:
  [repo](https://github.com/SDraw/openvr_widgets)

### 23. `Rectus/openxr-steamvr-passthrough`

- What it is:
  `OpenXR API layer` that provides passthrough support to SteamVR by using OpenVR camera feeds or USB cameras and compositing them into submitted frames.
- Useful for us:
  closest public reference to the original “window to reality” idea on PCVR.
- Best ideas to borrow:
  API-layer architecture, camera provider abstraction, calibration/rectification, projection and compositing.
- Caveat:
  only works if the HMD camera is actually exposed to SteamVR; it does not solve our `Pico Connect` camera blocker by itself.
- Source:
  [repo](https://github.com/Rectus/openxr-steamvr-passthrough)
  [compatibility wiki mirror](https://github-wiki-see.page/m/Rectus/openxr-steamvr-passthrough/wiki/Compatibility)

### 24. `zhangxuelei86/WMR-Passthrough`

- What it is:
  current repo metadata could not be reliably fetched during this pass.
- Likely value:
  niche reference for unofficial `WMR` passthrough experiments.
- Recommendation:
  treat as research-only and re-verify directly before relying on it.
- Caveat:
  do not build roadmap assumptions around it without a fresh direct validation.

### 25. `r57zone/OpenVR-OpenTrack`

- What it is:
  OpenVR driver allowing head tracking from `OpenTrack`, including DIY/smartphone-based setups.
- Useful for us:
  strong reference for alternate tracking sources and low-cost prototyping.
- Best ideas to borrow:
  external tracker integration, config-driven HMD/driver setup, DIY tracking path.
- Caveat:
  niche use case, more hacky than productized.
- Source:
  [repo](https://github.com/r57zone/OpenVR-OpenTrack)

### 26. `ethanporcaro/tracking-toolkit`

- What it is:
  Blender add-on that views and records `OpenXR` devices for motion capture and scene integration.
- Useful for us:
  very good reference for turning runtime tracking data into creator-facing tools.
- Best ideas to borrow:
  OpenXR device discovery, recording workflow, reference/offset separation, creator tooling UX.
- Caveat:
  Blender/mocap focus rather than in-headset utility UX.
- Source:
  [repo](https://github.com/ethanporcaro/tracking-toolkit)

### 27. `Erimelowo/OpenVR-InputEmulator-Fixed`

- What it is:
  fork of InputEmulator aiming to stay compatible with newer SteamVR versions.
- Useful for us:
  practical evidence that the original concept remains useful enough to maintain through forks.
- Best ideas to borrow:
  updated compatibility work and modernized fix strategy if we explore virtual-device tools.
- Caveat:
  still inherits the fragility and GPL constraints of the original.
- Source:
  [repo](https://github.com/Erimelowo/OpenVR-InputEmulator-Fixed)

### 28. `wirelessdreamer/OpenVR-InputEmulator`

- What it is:
  fork of InputEmulator that adds step detection / WIP locomotion ideas.
- Useful for us:
  interesting reference for “walking in place” and overlay-assisted locomotion utilities.
- Best ideas to borrow:
  locomotion experimentation on top of virtual controller/input infrastructure.
- Caveat:
  more experimental than the original project.
- Source:
  [repo](https://github.com/wirelessdreamer/OpenVR-InputEmulator)

### 29. `CrispyPin/ovr-utils`

- What it is:
  cross-platform SteamVR overlay utility app built in Godot.
- Useful for us:
  attractive reference for lightweight, engine-based, cross-platform utility overlays.
- Best ideas to borrow:
  Godot-based overlay app structure, “many small tools in one overlay” concept.
- Caveat:
  source in this pass was gathered through a mirror page, not the GitHub UI directly.
- Source:
  [mirror page](https://git.crispypin.cc/CrispyPin/ovr-utils)

### 30. `KhronosGroup/OpenXR-SDK-Source`

- What it is:
  official source project for the `OpenXR` loader, validation layers, tests, and sample code.
- Useful for us:
  primary source for loader behavior, API layers, and `hello_xr` sample patterns.
- Best ideas to borrow:
  loader initialization, Android path, sample API-layer structure, conformance-minded implementation habits.
- Caveat:
  foundational repo, not a ready-made utility app.
- Source:
  [repo](https://github.com/KhronosGroup/OpenXR-SDK-Source)
  [registry overview](https://registry.khronos.org/OpenXR/)

## Product directions enabled by this landscape

### Direction A: `SteamVR Utility Overlay Suite`

Most directly supported by:

- `DesktopPlus`
- `OpenVR-AdvancedSettings`
- `openvr_widgets`
- `OVRLay`
- `OpenVRDeviceBattery`
- `WhereIsForward`
- `ovr-utils`

Potential feature set:

- wrist panel
- metrics/status widgets
- quick settings
- pinned notes/checklists
- battery/device status
- keyboard and desktop snippets

### Direction B: `OpenXR Desktop / Reference Layer`

Most directly supported by:

- `DesktopXR`
- `OpenXR-Toolkit`
- `OpenComposite`
- `xrizer`
- `OpenXR-SDK-Source`

Potential feature set:

- desktop/reference overlay for OpenXR apps
- low-friction configuration
- performance-aware rendering path
- runtime-compatible overlay layer behavior

### Direction C: `Tracking / Calibration Toolkit`

Most directly supported by:

- `OpenVR-SpaceCalibrator`
- `OpenVR-InputEmulator`
- `OpenVR-OpenTrack`
- `tracking-toolkit`

Potential feature set:

- tracker alignment
- mixed-device setup assistant
- role assignment / debugging
- mocap and recording bridge
- virtual device and remap lab

### Direction D: `VR Diagnostics & Metrics`

Most directly supported by:

- `openvr-metrics`
- `OpenVR-AdvancedSettings`
- `openvr_widgets`
- `OpenVRDeviceBattery`

Potential feature set:

- FPS/frame timing overlay
- dropped/reprojected frame counters
- CPU/GPU/VRAM status
- device battery, connection, tracking quality

### Direction E: `External Camera Reality Tools`

Most directly supported by:

- `Rectus/openxr-steamvr-passthrough`
- `OpenVR-SpaceCalibrator`
- `OpenVR-OpenTrack`

Potential feature set:

- external USB camera window
- tracked camera calibration
- desk/keyboard view tool
- sim cockpit utility window

This is the most realistic way to revisit the original reality-window idea if onboard `PICO` camera access stays blocked.

## Recommended next steps

### Best immediate product pivot

Build:

- `Wrist Dashboard + Utility Overlay Suite`

Why:

- maximum reuse of our current overlay/panel work;
- does not depend on vendor passthrough;
- fast to validate in `SteamVR` and `Pico Connect`.

### Best medium-term technical branch

Prototype:

- `OpenXR desktop/reference layer`

Why:

- gives us a runtime-level path for OpenXR-native utilities;
- aligns with `DesktopXR`, `OpenXR-Toolkit`, and `OpenXR-SDK-Source`.

### Best experimental branch

Prototype:

- `external camera reality window`

Why:

- salvages the original idea without depending on proprietary HMD passthrough access.
