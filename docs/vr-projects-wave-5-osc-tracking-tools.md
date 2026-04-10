# VR Projects Wave 5: OSC, Marker Tracking, and Device Micro-Tools

- Date: `2026-04-10`
- Goal: add another niche-focused wave of VR projects that strengthen `VR.app`
  in three areas:
  - `OSC and external automation bridges`
  - `marker-based tracking and low-cost tracking utilities`
  - `small device/status helpers and room-setup tools`

## Coverage status for the submitted list

The following projects from the submitted list were already covered in earlier
`VR.app` docs:

- `fredemmott/OpenXR-API-Layers-GUI`
- `ytdlder/OpenXR-Switcher`
- `jonyrh/OXR_Switcher`
- `rhaamo/OpenVR-Display-Devices`
- `SeeUnsharp/LighthouseManager`

Mostly covered in:

- `vr-projects-wave-3-utilities.md`
- `vr-projects-wave-4-gap-fill.md`
- `vr-projects-master-index.md`

Newly documented in this pass:

1. `jangxx/UniversalTrackerMarkers`
2. `jangxx/steamvr-osc-control`
3. `Greendayle/SteamVR_To_OSC`
4. `ZekkVRC/OpenVR2OSC`
5. `MochiDoesVR/OpenVRCaptions`
6. `terminal29/VRUco`
7. `GoLez28/Aruco-TagTracking-VR`
8. `ju1ce/April-Tag-VR-FullBody-Tracker`
9. `FennecLabsLtd/LighthouseManager`
10. `risa2000/lhctrl`
11. `risa2000/lh2ctrl`
12. `Black4Blade/SteamVR-Devices-Battery-Status`

## Category A: Marker overlays and tracked-device visualization

### 1. `jangxx/UniversalTrackerMarkers`

- What it is:
  SteamVR utility that attaches image overlays to arbitrary tracked devices,
  including Lighthouses.
- Why it matters:
  one of the clearest references for `tracked-device markers as overlays`, which
  is a distinct product class from desktop windows or notifications.
- Interesting ideas:
  arbitrary PNG markers on tracked devices, tint/size/offset controls,
  proximity-based opacity, OSC hide/show support, serial-number overlays for
  device selection, automatic transform placement relative to another device.
- Best reuse value:
  visual debugging, navigation markers, calibration hints, and device-label
  overlays for `VR.app`.
- Caveat:
  narrow scope, but that is also its strength.
- Sources:
  [repo](https://github.com/jangxx/UniversalTrackerMarkers)

## Category B: SteamVR to OSC and external automation bridges

### 2. `jangxx/steamvr-osc-control`

- What it is:
  small utility that triggers SteamVR debug commands from incoming OSC packets.
- Why it matters:
  strong reference for `OSC -> SteamVR action` bridges and VRChat integration.
- Interesting ideas:
  config-driven OSC address mapping, bridge from VRChat actions to SteamVR
  developer/debug commands, lightweight command server instead of heavy overlay
  UI.
- Best reuse value:
  external automation bridge for `VR.app`, especially if we expose VR actions to
  OSC or other event buses.
- Caveat:
  focused on a small set of commands rather than a broad automation platform.
- Sources:
  [repo](https://github.com/jangxx/steamvr-osc-control)

### 3. `Greendayle/SteamVR_To_OSC`

- What it is:
  utility that redirects SteamVR controller input to OSC, largely for VRChat.
- Why it matters:
  a clean example of `VR input -> OSC output`.
- Interesting ideas:
  configurable parameter names via `config.json`, reusing SteamVR bindings as
  the input side while treating OSC as the output side, simple bridge design.
- Best reuse value:
  controller-to-automation bridges and app integration tooling in `VR.app`.
- Caveat:
  narrow scope and older UX.
- Sources:
  [repo](https://github.com/Greendayle/SteamVR_To_OSC)

### 4. `ZekkVRC/OpenVR2OSC`

- What it is:
  OSC application for VRChat that sets named parameters based on held controller
  buttons from SteamVR.
- Why it matters:
  reinforces the value of `button -> OSC parameter` mapping as a real utility
  pattern.
- Interesting ideas:
  explicit button-to-endpoint assignment, binding save flow, simple
  "while-held = true" semantics, lightweight companion app with direct user
  configuration.
- Best reuse value:
  button automation and event routing modules for `VR.app`.
- Caveat:
  VRChat-centered and more specific than a general bridge.
- Sources:
  [repo](https://github.com/ZekkVRC/OpenVR2OSC)

## Category C: Accessibility overlays

### 5. `MochiDoesVR/OpenVRCaptions`

- What it is:
  accessibility tool that uses `Vosk` speech-to-text and shows closed captions
  in a SteamVR overlay.
- Why it matters:
  this gives us a second accessibility-focused reference in addition to
  `live-captions-vr`, which strengthens the case that caption overlays are a
  legitimate VR utility category.
- Interesting ideas:
  speech-to-text as overlay content, captions as a dedicated assistive tool, C#
  overlay pipeline for accessibility instead of entertainment.
- Best reuse value:
  a future `VR.app accessibility overlay` family.
- Caveat:
  transcription accuracy and latency depend on the speech pipeline.
- Sources:
  [repo](https://github.com/MochiDoesVR/OpenVRCaptions)

## Category D: Marker-based tracking and low-cost tracking research

### 6. `terminal29/VRUco`

- What it is:
  SteamVR driver and standalone app that uses ArUco markers in the room for head
  tracking.
- Why it matters:
  very strong research reference for `camera + marker + driver` pipelines.
- Interesting ideas:
  room markers for headset tracking, standalone process + driver IPC split, use
  of commodity cameras like PS3 Eye, marker-map based head pose estimation.
- Best reuse value:
  tracking research and low-cost spatial tools.
- Caveat:
  the author explicitly says the current tracking is too jittery to recommend
  for real use.
- Sources:
  [repo](https://github.com/terminal29/VRUco)

### 7. `GoLez28/Aruco-TagTracking-VR`

- What it is:
  ArUco-based full-body tracking system for SteamVR.
- Why it matters:
  good example of `low-cost FBT using markers + cameras + VMT`.
- Interesting ideas:
  two-camera or multi-camera support, config-driven tracker definitions,
  smoothing controls, tag-based calibration flow, dependency on
  `VirtualMotionTracker` as the bridge into SteamVR.
- Best reuse value:
  tracker-bridge experiments, calibration UX, and data-driven tracking config
  design.
- Caveat:
  still presented as `WIP` and requires external setup effort.
- Sources:
  [repo](https://github.com/GoLez28/Aruco-TagTracking-VR)

### 8. `ju1ce/April-Tag-VR-FullBody-Tracker`

- What it is:
  open source full-body tracking system for VR using AprilTag markers.
- Why it matters:
  one of the strongest open references for `low-cost marker-based FBT` with a
  large user and contributor footprint.
- Interesting ideas:
  "phone + cardboard + printed markers" accessibility of the concept, full
  installer/build flow, wiki-driven setup, community support model, marker-based
  tracking positioned as a practical alternative to expensive hardware.
- Best reuse value:
  low-cost tracking research, community documentation patterns, and hardware
  accessibility ideas for `VR.app`.
- Caveat:
  much larger than a simple utility and primarily focused on full-body tracking.
- Sources:
  [repo](https://github.com/ju1ce/April-Tag-VR-FullBody-Tracker)

## Category E: Lighthouse setup and room-config helpers

### 9. `FennecLabsLtd/LighthouseManager`

- What it is:
  utility for saving and restoring Lighthouse and Chaperone configuration files.
- Why it matters:
  this is a different and very practical angle on Lighthouse tooling: not power
  control, but `room/setup deployment`.
- Interesting ideas:
  save/restore room configs to portable files, recommended use from USB/network
  storage, command-line automation, optional SteamVR restart on load.
- Best reuse value:
  backup/restore tools, room deployment helpers, and "carry your setup between
  PCs" style utilities.
- Caveat:
  focused only on configuration persistence, not ongoing device control.
- Sources:
  [repo](https://github.com/FennecLabsLtd/LighthouseManager)

### 10. `risa2000/lhctrl`

- What it is:
  Linux/Python utility for Valve Lighthouse v1 power management over Bluetooth
  LE.
- Why it matters:
  clean low-level reference for Lighthouse v1 BLE control and protocol notes.
- Interesting ideas:
  documented protocol behavior, command-line operations, explicit v1 master/slave
  behavior discussion, scriptable power-management workflow.
- Best reuse value:
  Linux-side device management and Bluetooth control research.
- Caveat:
  focused on v1 hardware and command-line use.
- Sources:
  [repo](https://github.com/risa2000/lhctrl)

### 11. `risa2000/lh2ctrl`

- What it is:
  Linux/Python utility for Valve Lighthouse v2 power management over Bluetooth
  LE.
- Why it matters:
  pairs well with `lhctrl` and provides a simple reference for v2-specific
  control differences.
- Interesting ideas:
  very small BLE command surface, simple write-to-characteristic power control,
  explicit notes on BT signal strength and hardware interference.
- Best reuse value:
  Linux-side v2 lighthouse automation and protocol understanding.
- Caveat:
  narrow scope and Linux-first.
- Sources:
  [repo](https://github.com/risa2000/lh2ctrl)

## Category F: Device status micro-tools

### 12. `Black4Blade/SteamVR-Devices-Battery-Status`

- What it is:
  small repository described as a utility for checking SteamVR device battery
  status.
- Why it matters:
  even though the repository currently looks rough and underdeveloped, it
  reinforces the idea that `battery status alone` is valuable enough to motivate
  standalone utilities.
- Interesting ideas:
  battery-only micro-tooling, extremely narrow focus, possibility of a tiny
  always-on companion app.
- Best reuse value:
  supports the case for modular battery widgets inside `VR.app`.
- Caveat:
  low confidence. The public repo page currently looks partially inconsistent,
  with sample content visible alongside the repo description. Treat it as a
  product signal more than a reliable code donor.
- Sources:
  [repo](https://github.com/Black4Blade/SteamVR-Devices-Battery-Status)

## Strongest ideas added by this wave

### 1. OSC deserves to be a first-class integration path

This wave strongly reinforces OSC as a useful interface layer:

- `steamvr-osc-control`
- `SteamVR_To_OSC`
- `OpenVR2OSC`

That suggests `VR.app` should eventually consider:

- `OSC in`
- `OSC out`
- controller/button mapping to external systems
- bridge modules for VRChat, automation, or custom workflows

### 2. Marker overlays are useful even without full tracking ambitions

`UniversalTrackerMarkers` shows that not every tracked-device tool needs to be a
driver or a calibration app. Some can simply be:

- labels
- warnings
- navigation markers
- device-identification aids

That is a strong product direction for small overlay utilities.

### 3. Marker-based tracking is a real experimentation branch

The ArUco/AprilTag projects together show a useful subdomain:

- cheap tracking alternatives
- driver + standalone pipeline design
- camera calibration workflows
- data-driven tracker definitions

This may not be the first `VR.app` product line, but it is a valuable research
branch.

### 4. Setup backup/restore is a separate utility class

`FennecLabsLtd/LighthouseManager` highlights a useful category beyond power
management:

- backup and restore
- transportable room setups
- setup deployment helpers

That can become part of a broader `VR.app room tools` family.

### 5. Battery tools can stay tiny

Not every useful VR utility needs to be a suite. Battery and status tools can
be:

- tiny overlays
- tray apps
- wrist widgets
- notification-only services

## Recommended updates to the VR.app backlog

This wave strengthens these candidate directions:

1. `OSC Bridge`
   SteamVR buttons and events mapped to OSC in both directions.

2. `Device Marker Overlay`
   Labels, arrows, tracked-device markers, serial/debug display.

3. `Accessibility Overlay`
   Closed captions and communication-oriented in-VR text.

4. `Room Tools`
   Lighthouse/chaperone backup and restore, setup deployment helpers.

5. `Battery Widgets`
   Wrist widgets, tray tools, device monitor panels.

6. `Tracking Research`
   Marker-based experiments, calibration helpers, virtual tracker bridges.

## Bottom line

This wave adds a more experimental but still very practical layer to the
repository:

- OSC integration
- marker overlays
- low-cost tracking experiments
- room setup tools
- battery micro-utilities

These are exactly the kinds of specialized utilities that fit the long-term
vision of `VR.app` as a platform for many focused VR tools instead of a single
app.
