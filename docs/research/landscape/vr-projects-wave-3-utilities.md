# VR Projects Wave 3: Utilities, Layers, Services

- Date: `2026-04-10`
- Goal: add another curated wave of VR-related repositories that were not yet
  documented in `VR.app`, with a focus on utilities, overlay/app-layer tools,
  managers, accessibility helpers, and service-style integrations.

## Executive summary

This wave is especially valuable because it adds five capability areas that were
not as strong in the previous research set:

1. `OpenXR layer management and runtime switching`
2. `Remote-control / IPC overlay services`
3. `Accessibility and comfort tools`
4. `Lighthouse automation and device-management utilities`
5. `Controller/input to external-system bridge patterns`

The strongest product and engineering ideas from this wave are:

- a first-class `OpenXR doctor + layer manager`
- a `VR notification / remote-control server`
- a `VR hotkey and automation bridge`
- accessibility overlays such as `live captions`
- `base-station and device power managers`
- highly focused single-purpose tools with very clear UX

## Category A: OpenXR layer management and runtime tools

### 1. `fredemmott/OpenXR-API-Layers-GUI`

- What it is:
  Windows GUI for detecting, inspecting, enabling, disabling, fixing, and
  re-ordering OpenXR API layers.
- Why it matters:
  this is one of the cleanest references for a serious `OpenXR layer manager`
  rather than a generic VR overlay.
- Interesting ideas:
  error detection for common API layer problems, actual layer ordering view,
  "fix common issues" UX, layer enable/disable/add/remove flow.
- Best reuse value:
  direct inspiration for a future `VR.app OpenXR Doctor / Layer Manager`.
- Caveat:
  mainly a desktop diagnostic/configuration tool, not an in-headset utility.
- Sources:
  [repo](https://github.com/fredemmott/OpenXR-API-Layers-GUI)

### 2. `WaGi-Coding/OpenXR-Runtime-Switcher`

- What it is:
  Windows tool for switching the system default OpenXR runtime.
- Why it matters:
  practical reference for a focused system utility that solves one frustrating
  XR setup problem cleanly.
- Interesting ideas:
  presets for common runtimes, custom runtime entries, registry-based detection,
  explicit admin-elevation requirement, zero vendor app dependency for switching.
- Best reuse value:
  runtime-management features in a future `VR.app doctor` desktop companion.
- Caveat:
  only changes the system default runtime; app-specific runtime selection is a
  separate issue.
- Sources:
  [repo](https://github.com/WaGi-Coding/OpenXR-Runtime-Switcher)

### 3. `UniStuttgart-VISUS/OpenXR-Runtime-Switcher`

- What it is:
  another Windows runtime switcher focused on switching OpenXR runtimes without
  vendor software.
- Why it matters:
  useful second reference for the same problem, with a simpler,
  less ecosystem-tied framing.
- Interesting ideas:
  self-contained runtime switching utility, service/helper split, runtime
  switching as a small standalone Windows app.
- Best reuse value:
  validation that `runtime switcher` is worth treating as a separate utility
  module.
- Caveat:
  appears smaller and less battle-tested than some other XR utilities.
- Sources:
  [repo](https://github.com/UniStuttgart-VISUS/OpenXR-Runtime-Switcher)

### 4. `mbucchia/OpenXR-Layer-Template`

- What it is:
  template repository for building a basic OpenXR API layer.
- Why it matters:
  probably the strongest bootstrap for any future `VR.app` OpenXR-layer work on
  Windows.
- Interesting ideas:
  layer bootstrap flow, customization docs, example branches, script-assisted
  setup, clear dependency expectations.
- Best reuse value:
  future OpenXR-layer prototypes such as metrics, mirroring, diagnostics, or
  accessibility layers.
- Caveat:
  template only; product logic still has to be built from scratch.
- Sources:
  [repo](https://github.com/mbucchia/OpenXR-Layer-Template)

### 5. `Jabbah/OpenXR-Layer-OBSMirror`

- What it is:
  OpenXR API layer plus OBS plugin for mirroring what the user sees in VR to
  OBS.
- Why it matters:
  strong real-world example of a useful `OpenXR layer` built from a template and
  paired with desktop tooling.
- Interesting ideas:
  layer + plugin architecture, OBS integration, DX11-only focused scope,
  PowerShell install/uninstall scripts.
- Best reuse value:
  reference for capture/export/mirroring utilities and for how to ship an
  OpenXR layer with a companion tool.
- Caveat:
  focused on OBS and recording rather than in-VR utility UX.
- Sources:
  [repo](https://github.com/Jabbah/OpenXR-Layer-OBSMirror)

## Category B: Desktop overlays and window portals

### 6. `CircuitLord/DesktopPortal`

- What it is:
  SteamVR add-on and utility program for desktop windows, watch controls, music,
  FPS access, and an in-VR library replacement.
- Why it matters:
  very strong product reference for a polished `desktop utility suite` rather
  than a single overlay.
- Interesting ideas:
  window spawning into playspace, anchor/resize/curve/opacity actions, wrist
  watch controls, utility suite framing, app/library replacement inside VR.
- Best reuse value:
  `VR.app` wrist dashboard, desktop/reference windows, utility watch, and
  overlay profile system.
- Caveat:
  archived and `GPL-3.0`.
- Sources:
  [repo](https://github.com/CircuitLord/DesktopPortal)

### 7. `scudzey/UVROverlay`

- What it is:
  general-purpose OpenVR desktop/content overlay.
- Why it matters:
  useful mid-level reference between tiny demo overlays and large polished tools
  like `DesktopPlus`.
- Interesting ideas:
  generic overlay manager framing, multiple content types, DWM-backed window
  mirroring, spatial tracking caveats, simple "universal overlay" concept.
- Best reuse value:
  lightweight overlay manager patterns and content-provider abstraction.
- Caveat:
  older project and `GPL-3.0`; known limitations with window capture.
- Sources:
  [repo](https://github.com/scudzey/UVROverlay)

### 8. `galister/WlxOverlay`

- What it is:
  simple OpenVR overlay for Wayland and X11 desktops.
- Why it matters:
  useful Linux-first reference for desktop-in-VR, especially before the
  evolution into newer WlxOverlay variants.
- Interesting ideas:
  simple desktop overlay structure, Linux capture pipeline, low-complexity
  screen access.
- Best reuse value:
  Linux overlay architecture reference and historical context for the later
  `wlx-overlay-x` and `wlx-overlay-s`.
- Caveat:
  superseded by newer variants.
- Sources:
  [repo](https://github.com/galister/WlxOverlay)

### 9. `matrixfurry/wlx-overlay-s`

- What it is:
  lightweight OpenXR/OpenVR overlay for Wayland/X11 desktops, forked from
  `wayvr`, now with Vulkan and a strong "run alongside games" focus.
- Why it matters:
  one of the best modern references for desktop access with low overhead.
- Interesting ideas:
  OpenXR/OpenVR dual support, minimal but customizable UI, working-set concept,
  watch-based control surface, screen/keyboard overlays, autostart registration,
  pointer mode colors.
- Best reuse value:
  watch-style overlay control, low-overhead desktop UX, dual-runtime thinking.
- Caveat:
  Linux-first and `GPL-3.0`.
- Sources:
  [repo](https://github.com/matrixfurry/wlx-overlay-s)

### 10. `galister/wlx-overlay-x`

- What it is:
  Rust OpenXR overlay for Wayland desktops, later superseded by
  `WlxOverlay-S`.
- Why it matters:
  valuable as a simpler OpenXR-specific intermediate step.
- Interesting ideas:
  left-wrist watch control, grab-to-move/resize behavior, direct OpenXR overlay
  workflow, explicit note about why the next generation moved away from older
  rendering approaches.
- Best reuse value:
  OpenXR overlay UX references and Rust/OpenXR prototype patterns.
- Caveat:
  explicitly superseded by `WlxOverlay-S`.
- Sources:
  [repo](https://github.com/galister/wlx-overlay-x)

### 11. `PhialsBasement/fnuidesktop-VR`

- What it is:
  Linux/Wayland SteamVR overlay that mirrors the desktop with controller mouse
  input, scrolling, drag-to-move, and pinch-to-resize.
- Why it matters:
  great focused reference for direct-manipulation desktop windows in VR.
- Interesting ideas:
  PipeWire + XDG Desktop Portal capture, controller gestures mapped to desktop
  interaction, very explicit input model, split capture/display process layout.
- Best reuse value:
  controller interaction patterns for desktop windows and reference surfaces.
- Caveat:
  highly Linux/Wayland-specific.
- Sources:
  [repo](https://github.com/PhialsBasement/fnuidesktop-VR)

## Category C: Accessibility, comfort, and human-centered utilities

### 12. `Raphiiko/OyasumiVR`

- What it is:
  large suite of VR sleeping, comfort, automation, device control, and
  environment-management utilities with a SteamVR overlay.
- Why it matters:
  one of the strongest proofs that `VR utilities` can be a whole ecosystem, not
  just a single overlay.
- Interesting ideas:
  movement-based sleep detection, battery-based automations, SteamVR overlay
  control, base station management, GPU power automation, brightness/color
  temperature automation, render-resolution automation, chaperone automation,
  Home Assistant integration over MQTT.
- Best reuse value:
  automation engine ideas, device status UX, comfort tooling, and “overlay +
  desktop service + home automation bridge” architecture.
- Caveat:
  broad scope means it is more ecosystem reference than small code donor.
- Sources:
  [repo](https://github.com/Raphiiko/OyasumiVR)

### 13. `Vinventive/live-captions-vr`

- What it is:
  accessibility-focused SteamVR overlay for real-time speech transcription in
  3D space.
- Why it matters:
  strong example of an accessibility-first VR utility with a very clear social
  value.
- Interesting ideas:
  live captions in spatial UI, communication support for deaf/hard-of-hearing
  users, AI-assisted speech-to-text as overlay content instead of desktop
  mirroring.
- Best reuse value:
  caption overlays, assistive communication tools, text-in-space rendering.
- Caveat:
  transcription quality is inherently imperfect.
- Sources:
  [repo](https://github.com/Vinventive/live-captions-vr)

### 14. `jangxx/LeapOVRPassthrough`

- What it is:
  passthrough overlay using a Leap Motion mounted on an OpenVR headset.
- Why it matters:
  especially valuable not as camera tech, but as a UX pattern for
  hand-triggered passthrough overlays.
- Interesting ideas:
  hand-mounted passthrough window, gesture or hand-presence driven invocation,
  passthrough as a small utility surface instead of full-scene mode.
- Best reuse value:
  trigger metaphors for temporary overlays and context-sensitive tools.
- Caveat:
  depends on Leap/UltraLeap hardware assumptions and an older passthrough
  approach.
- Sources:
  [repo](https://github.com/jangxx/LeapOVRPassthrough)

## Category D: Passthrough and reality-window experiments

### 15. `Danealor/VRPassthrough`

- What it is:
  lightweight standalone OpenXR + DirectX 11 app for real-time stereo USB-camera
  passthrough to VR headsets.
- Why it matters:
  this is one of the closest practical references to the original
  `Reality Window` dream, but built around external cameras instead of hidden
  vendor headset cameras.
- Interesting ideas:
  direct camera-to-compositor pipeline, minimal-latency design, debug overlay,
  auto-reconnect, compute-shader conversion, strong architecture notes,
  engine-free approach.
- Best reuse value:
  external-camera provider path, stereo passthrough experiments, performance
  architecture, debug overlay concepts.
- Caveat:
  hardware-specific starting point and not a drop-in solution for onboard
  headset cameras.
- Sources:
  [repo](https://github.com/Danealor/VRPassthrough)

## Category E: Lighthouse and device power management

### 16. `kurotu/OVR-Lighthouse-Manager`

- What it is:
  Windows utility for managing SteamVR base station power with Bluetooth LE,
  especially for setups without Vive/Index HMDs.
- Why it matters:
  excellent example of a practical utility solving a common standalone-headset +
  Vive-tracker problem.
- Interesting ideas:
  base-station power automation tied to SteamVR start/end, standalone-headset
  compatibility, detailed device control via desktop UI.
- Best reuse value:
  device manager modules, Bluetooth-backed automation, PICO/Quest + tracker
  ecosystem support.
- Caveat:
  Windows-only and `GPL-3.0`.
- Sources:
  [repo](https://github.com/kurotu/OVR-Lighthouse-Manager)

### 17. `DHCPCD9/go-steamvr-lighthouse-manager`

- What it is:
  Go/Wails-based UI tool for controlling Base Station 2.0 power and channel.
- Why it matters:
  demonstrates the same problem space solved with a more modern desktop app
  stack and explicit automation.
- Interesting ideas:
  channel management, automated SteamVR session integration, cross-platform
  build intent, systray patterns.
- Best reuse value:
  device-manager UI patterns and desktop-service architecture.
- Caveat:
  currently focused on Base Station 2.0.
- Sources:
  [repo](https://github.com/DHCPCD9/go-steamvr-lighthouse-manager)

### 18. `xi-ve/openvr-lighthouse-manager-linux`

- What it is:
  Linux port of lighthouse management with GUI, CLI, and SteamVR addon mode.
- Why it matters:
  useful reference for making a device utility run both as a manual app and as
  an auto-launched SteamVR service.
- Interesting ideas:
  addon installation scripts, auto-start with SteamVR, GUI plus CLI split,
  manual and automatic operating modes.
- Best reuse value:
  future `VR.app` service-mode utilities, especially Linux-side helpers.
- Caveat:
  Linux-specific.
- Sources:
  [repo](https://github.com/xi-ve/openvr-lighthouse-manager-linux)

### 19. `nouser2013/lighthouse-v2-manager`

- What it is:
  Python utility for waking and sleeping Lighthouse V2 devices.
- Why it matters:
  tiny but strong reference for the minimal viable version of a base-station
  utility.
- Interesting ideas:
  stripped-down Bluetooth device-control workflow, small footprint, script-first
  utility design.
- Best reuse value:
  quick automation scripts and proof-of-concept device control.
- Caveat:
  less polished and less feature-rich than the larger managers.
- Sources:
  [repo](https://github.com/nouser2013/lighthouse-v2-manager)

## Category F: Overlay IPC, remote control, and notification services

### 20. `BOLL7708/OpenVROverlayPipe`

- What it is:
  WebSocket server for displaying image overlays and notifications in SteamVR.
- Why it matters:
  one of the strongest references for `overlay as a service` and remote-control
  architecture.
- Interesting ideas:
  JSON payloads for overlays, channels, anchor targets, placement/animation
  parameters, custom image notifications, browser-testable WebSocket interface.
- Best reuse value:
  `VR.app remote overlay server`, desktop companion apps, automation hooks, and
  multi-process control architecture.
- Caveat:
  `GPL-3.0`; focus is notifications and overlay payload dispatch more than full
  utility UX.
- Sources:
  [repo](https://github.com/BOLL7708/OpenVROverlayPipe)

### 21. `jeppevinkel/OpenVRNotificationPipe`

- What it is:
  WebSocket server for sending SteamVR or custom notifications by JSON payload.
- Why it matters:
  simpler notification-first version of the service-driven overlay concept.
- Interesting ideas:
  payload schema, transition/animation options, remote notifications from other
  applications, SteamVR-native plus custom notification blending.
- Best reuse value:
  notification subsystem design for `VR.app`.
- Caveat:
  focused scope and appears lightly adopted.
- Sources:
  [repo](https://github.com/jeppevinkel/OpenVRNotificationPipe)

### 22. `WiiPlayer2/VnotifieR`

- What it is:
  notification server and overlay for OpenVR.
- Why it matters:
  useful additional reference that validates the notification-server pattern.
- Interesting ideas:
  standalone notification service, OpenVR overlay integration, small-purpose
  utility packaging.
- Best reuse value:
  secondary reference for server-driven VR notifications.
- Caveat:
  older and smaller than some alternatives.
- Sources:
  [repo](https://github.com/WiiPlayer2/VnotifieR)

### 23. `BOLL7708/OpenVR2WS`

- What it is:
  WebSocket server that exposes SteamVR I/O as JSON.
- Why it matters:
  very important reference for turning SteamVR into an external-data service.
- Interesting ideas:
  JSON bridge for SteamVR state, settings access, I/O exposure to external apps,
  service architecture that lets non-VR tools react to VR runtime state.
- Best reuse value:
  `VR.app automation bridge`, external integrations, dashboards, device state
  mirroring.
- Caveat:
  data bridge rather than end-user polished utility.
- Sources:
  [repo](https://github.com/BOLL7708/OpenVR2WS)

## Category G: Small focused utilities with clear UX

### 24. `Otter-Co/TurnSignal`

- What it is:
  anti-cable-twisting management utility for SteamVR.
- Why it matters:
  one of the best examples of a tiny VR utility with a crystal-clear purpose.
- Interesting ideas:
  minimal overlay UX, one-job-only product focus, body-orientation utility
  design.
- Best reuse value:
  reminder that `VR.app` does not need every tool to be huge; simple utilities
  can still be valuable and polished.
- Caveat:
  narrow scope by design.
- Sources:
  [repo](https://github.com/Otter-Co/TurnSignal)

### 25. `Deryck2000/SteamVR_ClockOverlay_Public`

- What it is:
  tiny SteamVR digital clock overlay that follows the left wrist.
- Why it matters:
  a perfect micro-example of a `single-purpose wrist utility`.
- Interesting ideas:
  left-wrist anchored micro-overlay, "always glanceable" information design,
  tiny-product simplicity.
- Best reuse value:
  direct inspiration for a `VR.app wrist dashboard` and small modular wrist
  widgets.
- Caveat:
  very small scope and minimal codebase.
- Sources:
  [repo](https://github.com/Deryck2000/SteamVR_ClockOverlay_Public)

### 26. `BenWoodford/OVROverlayManager`

- What it is:
  tiny Unity helper for setting up OpenVR overlays.
- Why it matters:
  simple bootstrap reference for Unity-side overlay setup.
- Interesting ideas:
  render texture to overlay flow, canvas/camera setup, dashboard overlay
  bootstrap, minimal helper class set.
- Best reuse value:
  Unity prototype bootstrap when experimenting with quick VR UI tests.
- Caveat:
  small helper rather than a full utility framework.
- Sources:
  [repo](https://github.com/BenWoodford/OVROverlayManager)

## Category H: Input remapping, locomotion, and external control surfaces

### 27. `pottedmeat7/OpenVR-WalkInPlace`

- What it is:
  OpenVR client and driver that turns tracked movement patterns into locomotion.
- Why it matters:
  strong example of a VR utility that combines driver, overlay, profile system,
  data models, and gameplay-facing output.
- Interesting ideas:
  movement data-model recording, custom controller routing, profiles, tracked
  device selection, overlay-assisted calibration of locomotion patterns.
- Best reuse value:
  motion-analysis tooling, profile-driven behavior, “driver + overlay + UI”
  architecture.
- Caveat:
  domain-specific and `GPL-3.0`.
- Sources:
  [repo](https://github.com/pottedmeat7/OpenVR-WalkInPlace)

### 28. `mdovgialo/steam-vr-wheel`

- What it is:
  steering wheel, joystick, and gamepad emulation driven by SteamVR devices.
- Why it matters:
  great example of turning VR tracking/input into a specialized external
  controller.
- Interesting ideas:
  VR-to-vJoy bridge, mode-based external control surfaces, configurator plus
  runtime tools, practical input conversion.
- Best reuse value:
  controller-to-external-device bridges and specialized VR control panels.
- Caveat:
  older Python-based implementation and paused maintenance.
- Sources:
  [repo](https://github.com/mdovgialo/steam-vr-wheel)

## Category I: VRChat and OSC service ecosystems

### 29. `ShayBox/VRC-OSC`

- What it is:
  Rust plugin-based VRChat OSC toolkit with dynamically loaded plugins.
- Why it matters:
  strong example of a modular desktop utility ecosystem with plugin architecture
  and SteamVR integration.
- Interesting ideas:
  plugin loader design, small focused plugins, auto-start/stop via SteamVR
  overlay registration, media/chatbox/control integrations.
- Best reuse value:
  future plugin architecture for `VR.app`, especially for desktop-side services.
- Caveat:
  VRChat-centric rather than general VR tooling.
- Sources:
  [repo](https://github.com/ShayBox/VRC-OSC)

### 30. `VolcanicArts/VRCOSC`

- What it is:
  large modular VRChat OSC platform with node-style programming, routing,
  debugging, automation, and many integrations.
- Why it matters:
  it shows what a mature `desktop-side automation platform for VR` can become.
- Interesting ideas:
  node-based automation, toolkit/router/debugger fusion, SteamVR stats, haptic
  control, AFK detection, process management, extensible desktop utility
  platform.
- Best reuse value:
  inspiration for an eventual `VR.app automation hub` or plugin/graph system.
- Caveat:
  large scope and VRChat-specific center of gravity.
- Sources:
  [repo](https://github.com/VolcanicArts/VRCOSC)

## Strongest cross-project ideas from this wave

### 1. `OpenXR doctor` should be a real product line

This wave strongly reinforces a desktop-side XR configuration toolchain:

- `OpenXR-API-Layers-GUI`
- `OpenXR-Runtime-Switcher`
- `OpenXR-Layer-Template`
- `OpenXR-Layer-OBSMirror`

This is enough to justify a serious `VR.app OpenXR Doctor` direction with:

- runtime detection
- runtime switching
- API layer inspection
- layer ordering
- known-problem diagnosis

### 2. `Overlay as a service` is a very strong architecture

Projects like these point to a modular service model:

- `OpenVROverlayPipe`
- `OpenVRNotificationPipe`
- `OpenVR2WS`
- `VnotifieR`

This suggests a future `VR.app service bus` with:

- WebSocket/JSON control
- notifications
- remote overlay creation
- external automation integration

### 3. Accessibility and comfort tools are underrepresented and valuable

The strongest examples here are:

- `live-captions-vr`
- `OyasumiVR`
- `TurnSignal`

This points toward:

- captions
- posture/comfort reminders
- device/battery aware automations
- health or sleep mode helpers

### 4. Wrist utilities are a real product class

Multiple projects point to wrist-first UX:

- `WlxOverlay-S` watch
- `DesktopPortal` watch
- `SteamVR_ClockOverlay_Public`

This makes `Wrist Dashboard` one of the best next `VR.app` products.

### 5. Device management is worth treating as its own family

This wave adds a lot of proof for `VR device management`:

- lighthouse managers
- battery/state tools
- OSC/virtual tracker bridges
- runtime switchers

This is a broader and more practical direction than passthrough alone.

## Best additions to the VR.app backlog

Based on this wave, the best concrete additions are:

1. `OpenXR Doctor`
   Runtime switcher, layer inspector, layer ordering, problem detection.

2. `VR Notification Service`
   SteamVR notifications and simple remote overlays via WebSocket.

3. `Wrist Dashboard`
   Time, battery, quick actions, device control, shortcuts.

4. `Accessibility Overlay`
   Captions, large text, communication-focused panels.

5. `Device Manager`
   Base stations, tracker/device state, battery and power automation.

6. `Automation Bridge`
   WebSocket/OSC/MQTT style external integration for desktop tools and smart
   home style workflows.

7. `Reference / Utility Windows`
   Task-focused windows for notes, checklists, chat, timers, and simple
   desktop/reference content.

## Bottom line

This wave pushes `VR.app` in a strong direction:

- not just overlays
- not just passthrough experiments
- but a whole toolkit ecosystem of desktop companions, in-VR panels,
  diagnostics, device managers, automation bridges, and accessibility tools

That is a durable and realistic product foundation.
