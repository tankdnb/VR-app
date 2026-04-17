# VR Projects Wave 6: Driver Bridges, Vendor Tooling, and Hardware Utilities

- Date: `2026-04-11`
- Goal: document a new wave of VR-related repositories centered on:
  - `SteamVR/OpenVR driver tooling`
  - `virtual trackers and remote tracking bridges`
  - `vendor-specific enhancement layers`
  - `custom hardware integration`
  - `small desktop-side runtime helpers`

## Why this wave matters

Previous waves focused mostly on overlays, runtime switching, diagnostics,
desktop-in-VR, and utility UX.

This wave adds a different but very important layer of knowledge:

- how VR utilities can live as `drivers`
- how external systems can feed data into SteamVR/OpenVR
- how a desktop app can augment an official vendor stack
- how small hardware-specific tools become useful bridge products

It also strengthens the idea that `VR.app` should not think only in terms of
"overlay apps". There is also a whole product space in:

- driver-backed utilities
- tracker bridges
- vendor enhancement layers
- calibration utilities
- micro desktop helpers

## Projects covered in this wave

1. `BnuuySolutions/PSVR2Toolkit`
2. `MuffinTastic/steamvr-exconfig`
3. `zeroae/VRBattery`
4. `John-Dean/OpenVR-Tracker-Websocket-Driver`
5. `surplex-io/OpenVR-Driver`
6. `gpsnmeajp/VirtualMotionTracker`
7. `LucidVR/opengloves-driver`
8. `HoboVR-Labs/hobo_vr`
9. `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay`
10. `r57zone/OpenVR-ArduinoHMD`
11. `DaniXmir/GlassVr`
12. `krazysh01/VirtualDesktop-OpenVR-Trackers`
13. `terminal29/Simple-OpenVR-Driver-Tutorial`
14. `Copprhead/hotas-vr-controller`
15. `SophiaH67/soph_wireless`
16. `SophiaH67/soph_wireless_transmitter`
17. `mittorn/ovr-utils-dashboard`

## Category A: Vendor enhancement and desktop-side runtime helpers

### 1. `BnuuySolutions/PSVR2Toolkit`

- What it is:
  unofficial enhancement layer for the official `PlayStation VR2` PC driver/app.
- Why it matters:
  this is a great reference for `utility on top of a vendor stack` rather than
  replacing the stack entirely.
- Interesting ideas:
  eye tracking support, improved controller prediction, improved haptics,
  adaptive triggers, developer API, desktop app plus IPC plus driver-side
  components.
- Architecture clues from the repo:
  the tree contains separate `PSVR2Toolkit.App`, `PSVR2Toolkit.IPC`,
  `psvr2_openvr_driver_ex`, and `shared` projects, which strongly suggests a
  split `desktop app + IPC + driver patch layer` model.
- Best reuse value:
  vendor-specific enhancement patterns, IPC separation, and "augment the
  official runtime instead of replacing it" design.
- Caveat:
  very vendor-specific and contains explicit non-commercial language around some
  features, especially eye-tracking use.
- Sources:
  [repo](https://github.com/BnuuySolutions/PSVR2Toolkit)

### 2. `MuffinTastic/steamvr-exconfig`

- What it is:
  tiny external configurator for SteamVR.
- Why it matters:
  strong example of a `small desktop utility` with clear value: quickly disable
  overlays/drivers/settings without walking through SteamVR UI.
- Interesting ideas:
  direct config editing, fast pre-launch or pre-restart workflow, tiny app
  footprint, pragmatic focus on saving setup time.
- Architecture clues from the repo:
  the codebase is a small WinForms app with classes like `SteamVRConfig`,
  `OpenVRPaths`, `VRAppSetting`, and `Config`.
- Best reuse value:
  direct inspiration for a future `VR.app quick config tool` and lightweight
  desktop companions.
- Caveat:
  very narrow scope, which is also its strength.
- Sources:
  [repo](https://github.com/MuffinTastic/steamvr-exconfig)

### 3. `zeroae/VRBattery`

- What it is:
  small SteamVR battery overlay.
- Why it matters:
  one of the cleanest examples of a single-purpose micro-utility.
- Interesting ideas:
  battery-only UX, minimal overlay scope, simple always-useful information.
- Architecture clues from the repo:
  Qt-based app with `batteryinfowidget` and `openvroverlaycontroller`, which is
  a very direct pattern for a tiny overlay + widget app.
- Best reuse value:
  battery widgets, micro-overlays, and proof that small utilities can be worth
  shipping on their own.
- Caveat:
  feature scope is intentionally tiny.
- Sources:
  [repo](https://github.com/zeroae/VRBattery)

## Category B: WebSocket, OSC, and remote tracker drivers

### 4. `John-Dean/OpenVR-Tracker-Websocket-Driver`

- What it is:
  OpenVR driver that hosts a local WebSocket server and allows spawning/updating
  trackers while also echoing active VR device poses.
- Why it matters:
  one of the strongest public references for `OpenVR driver as a local service`.
- Interesting ideas:
  tracker creation over JSON, device pose echo, simple browser-accessible HTTP
  page, WebSocket and local IPC-friendly architecture, multi-tracker updates in
  a single request.
- Best reuse value:
  `VR.app tracker service`, remote tracker injection, local automation bridge,
  WebSocket-based device services.
- Caveat:
  driver-level deployment complexity and no higher-level polished UX.
- Sources:
  [repo](https://github.com/John-Dean/OpenVR-Tracker-Websocket-Driver)

### 5. `surplex-io/OpenVR-Driver`

- What it is:
  another WebSocket-based OpenVR tracker driver, closely related in architecture
  to the driver above.
- Why it matters:
  useful as a second implementation of the same general pattern.
- Interesting ideas:
  confirms that `driver-backed WebSocket tracker servers` are not a one-off
  gimmick, but a repeatable utility architecture.
- Best reuse value:
  compare and validate design choices for tracker-bridge services.
- Caveat:
  conceptually overlaps heavily with the John-Dean project; best used as a
  comparison point.
- Sources:
  [repo](https://github.com/surplex-io/OpenVR-Driver)

### 6. `gpsnmeajp/VirtualMotionTracker`

- What it is:
  very mature virtual tracker driver for OpenVR that accepts pose over OSC and
  now also supports skeletal input.
- Why it matters:
  one of the strongest projects in the entire `virtual tracker` space.
- Interesting ideas:
  OSC pose input, glove-style skeletal input, separate `vmt_driver` and
  `vmt_manager`, sample code and API docs, manager app plus driver split,
  direct support for creating custom tracking devices from outside software.
- Architecture clues from the repo:
  separate `vmt_driver` and `vmt_manager` projects, OSC handling, and external
  control docs show a clear `driver + manager + API` pattern.
- Best reuse value:
  tracker bridge architecture, OSC integration, skeletal input pathways,
  separation of runtime service from management UI.
- Caveat:
  docs are partly Japanese and the project solves a more advanced domain than a
  casual utility overlay.
- Sources:
  [repo](https://github.com/gpsnmeajp/VirtualMotionTracker)
  [docs](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/)

### 7. `SophiaH67/soph_wireless`

- What it is:
  SteamVR driver that receives tracking data from another remote SteamVR
  instance over the network.
- Why it matters:
  strong reference for `distributed tracking` and remote tracker availability.
- Interesting ideas:
  remote SteamVR as a tracker source, UDP transport, registration of remote
  trackers into the local runtime, travel/remote setup use case.
- Best reuse value:
  remote tracking, distributed VR services, and "one machine exposes tracking to
  another" patterns.
- Caveat:
  focused on tracker forwarding, not a general framework.
- Sources:
  [repo](https://github.com/SophiaH67/soph_wireless)

### 8. `SophiaH67/soph_wireless_transmitter`

- What it is:
  companion sender for `soph_wireless`.
- Why it matters:
  useful because it makes the split architecture explicit: `receiver driver +
  external transmitter`.
- Interesting ideas:
  paired sender/receiver architecture, very small focused sidecar app.
- Best reuse value:
  reinforces the value of keeping external senders separate from driver code.
- Caveat:
  mostly meaningful together with the main driver.
- Sources:
  [repo](https://github.com/SophiaH67/soph_wireless_transmitter)

### 9. `krazysh01/VirtualDesktop-OpenVR-Trackers`

- What it is:
  OpenVR driver that uses Virtual Desktop body state data to create trackers.
- Why it matters:
  strong example of `ecosystem bridge`: data from one XR platform becomes
  trackers in another.
- Interesting ideas:
  body-state bridge, translation layer from an existing external ecosystem into
  SteamVR tracking objects, specialized but very practical interoperability.
- Best reuse value:
  future `VR.app` bridge modules that translate third-party state into VR device
  abstractions.
- Caveat:
  tightly coupled to the Virtual Desktop ecosystem.
- Sources:
  [repo](https://github.com/krazysh01/VirtualDesktop-OpenVR-Trackers)

## Category C: Custom hardware and alternative device plumbing

### 10. `LucidVR/opengloves-driver`

- What it is:
  SteamVR/OpenVR driver for VR gloves and DIY hand hardware.
- Why it matters:
  one of the strongest references for `custom input hardware -> SteamVR device`
  integration.
- Interesting ideas:
  force feedback, full finger tracking, splay support, individual joints,
  tracker/controller positioning and offsets, multiple communication methods,
  companion UI for calibration and settings.
- Architecture clues from the repo:
  separate `driver` and `server` directories plus documentation and a separate
  UI project in another repo.
- Best reuse value:
  custom device integration, hand-specific input plumbing, multi-transport
  communication, manager/driver split.
- Caveat:
  hand/glove-specific domain with a larger hardware expectation.
- Sources:
  [repo](https://github.com/LucidVR/opengloves-driver)

### 11. `HoboVR-Labs/hobo_vr`

- What it is:
  SteamVR driver prototyping toolkit with a flexible communication protocol and
  cross-language bindings.
- Why it matters:
  one of the best research foundations for building and testing custom SteamVR
  drivers.
- Interesting ideas:
  generic configurable devices, driver protocol abstracted behind an API,
  external "poser" processes that implement tracking or input systems, Python
  and C++ bindings, Linux support.
- Best reuse value:
  `VR.app` future driver experimentation, protocol design, and "driver plus
  external process" patterns.
- Caveat:
  more of a developer foundation than an end-user utility.
- Sources:
  [repo](https://github.com/HoboVR-Labs/hobo_vr)

### 12. `r57zone/OpenVR-ArduinoHMD`

- What it is:
  DIY OpenVR HMD driver using Arduino-based rotation tracking and a second
  display.
- Why it matters:
  useful reference for `minimal custom HMD path` and low-cost hardware
  experimentation.
- Interesting ideas:
  serial IMU pipeline, direct config-file control of optics and display
  parameters, hotkey-based recenter and movement adjustment, DIY display-driven
  HMD model.
- Best reuse value:
  hardware experiments, simple serial-device VR bridges, low-level headset path
  understanding.
- Caveat:
  niche DIY setup and older architecture.
- Sources:
  [repo](https://github.com/r57zone/OpenVR-ArduinoHMD)

### 13. `DaniXmir/GlassVr`

- What it is:
  OpenVR driver/tooling for using XR/AR glasses and other non-standard hardware
  in SteamVR.
- Why it matters:
  one of the most interesting `hardware bridge` projects in this list.
- Interesting ideas:
  headset emulation, controller emulation, tracker emulation, split position and
  rotation sources, static offsets, webcam-based hand tracking, controller
  remapping, experimental support for XR glasses as VR displays.
- Best reuse value:
  "non-VR hardware -> SteamVR" bridge patterns, device-emulation design,
  position/rotation composition ideas.
- Caveat:
  highly experimental and hardware-fragile.
- Sources:
  [repo](https://github.com/DaniXmir/GlassVr)

### 14. `Copprhead/hotas-vr-controller`

- What it is:
  OpenVR driver that repositions VR controllers so sim pilots can keep hands on
  HOTAS hardware while still interacting with cockpit controls.
- Why it matters:
  excellent example of a `domain-specific utility driver`.
- Interesting ideas:
  arm-mounted controller offsets, input substitution with finger mice,
  controller-transform manipulation as a product feature, cockpit workflow
  optimization.
- Best reuse value:
  simulator-specific tools, controller offset/calibration concepts, and "adapt
  VR input around a real-world tool" product thinking.
- Caveat:
  niche but very compelling use case.
- Sources:
  [repo](https://github.com/Copprhead/hotas-vr-controller)

## Category D: Driver tutorials, calibration, and dashboard suites

### 15. `terminal29/Simple-OpenVR-Driver-Tutorial`

- What it is:
  tutorial/sample repository for building common OpenVR driver components.
- Why it matters:
  arguably one of the most important educational repos for the whole
  SteamVR/OpenVR driver ecosystem.
- Interesting ideas:
  central driver setup, config loading, logging, example HMD/controllers/tracker
  devices, tracking references, custom render models, explicit SteamVR debugging
  guidance.
- Best reuse value:
  baseline architecture reference for any future driver-side work in `VR.app`.
- Caveat:
  tutorial foundation, not a product utility.
- Sources:
  [repo](https://github.com/terminal29/Simple-OpenVR-Driver-Tutorial)

### 16. `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay`

- What it is:
  eye-tracking calibration overlay for OpenVR/SteamVR.
- Why it matters:
  strong reference for `overlay-based calibration UX`.
- Interesting ideas:
  3D calibration flow in overlay form, eye-tracking calibration as a dedicated
  VR utility, separation of calibration UX from the underlying eye-tracking
  stack.
- Best reuse value:
  calibration-flow design for `VR.app`, especially where a visual guided wizard
  is needed in-VR.
- Caveat:
  README is very minimal, so this is more a direction signal than a fully
  documented code donor.
- Sources:
  [repo](https://github.com/RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay)

### 17. `mittorn/ovr-utils-dashboard`

- What it is:
  Godot-based cross-platform SteamVR overlay app aimed at having many useful
  tools available while in VR.
- Why it matters:
  useful alternate implementation of the `utility suite dashboard` idea, and it
  connects back to the already tracked `CrispyPin/ovr-utils` line.
- Interesting ideas:
  game-engine-based utility dashboards, cross-platform overlay app, many-tools
  framing instead of one narrow function.
- Best reuse value:
  dashboard-style utility suites and cross-platform UI experimentation.
- Caveat:
  appears closer to a variant/fork line than a wholly separate product family.
- Sources:
  [repo](https://github.com/mittorn/ovr-utils-dashboard)

## Strongest patterns from this wave

### 1. `Driver + manager` is a recurring winning architecture

This pattern shows up repeatedly:

- `VirtualMotionTracker`
- `PSVR2Toolkit`
- `OpenGloves`
- various lighthouse/device tools from earlier waves

This suggests that `VR.app` should not assume everything belongs in one process.
For harder utility domains, a good architecture is often:

- runtime driver/service
- management app
- shared protocol or IPC

### 2. `External system -> virtual VR device` is a huge design space

This wave strongly confirms that many useful utilities follow one pattern:

- external data source
- translation layer
- virtual device or tracker inside SteamVR/OpenVR

Examples:

- WebSocket tracker drivers
- OSC tracker drivers
- remote tracker forwarding
- Virtual Desktop body state bridge
- glasses/headset/controller emulation

This is one of the most fertile technical directions in the whole research set.

### 3. `Vendor enhancement layer` is a real product strategy

`PSVR2Toolkit` is especially important because it shows a path between:

- using the official runtime
- but still adding missing capabilities and improvements

That pattern may be reusable for other ecosystems too.

### 4. `Micro desktop tools` are still valuable

Even among all the complex driver systems, there is still strong evidence for:

- battery-only tools
- external config editors
- calibration-only overlays

So `VR.app` should continue to allow very small utilities to exist beside bigger
systems.

### 5. `Domain-specific hardware bridges` are unusually strong ideas

The most interesting products in this wave are often very specific:

- HOTAS cockpit adaptation
- XR glasses bridge
- Arduino HMD
- glove driver

That suggests `VR.app` could eventually host highly focused utility modules for
specific niches without needing them to be mass-market.

## Recommended additions to the VR.app backlog

This wave especially strengthens these directions:

1. `Tracker Bridge Service`
   WebSocket/OSC/UDP tracker injection and device mirroring.

2. `Device Manager + Companion`
   Separate runtime-facing service and user-facing configuration tool.

3. `Battery and Config Micro-Utilities`
   Very small tools with high practical value.

4. `Calibration Wizards`
   Guided overlay calibration flows for eye tracking, offsets, and device
   mapping.

5. `Hardware Bridge Research`
   XR glasses, DIY HMDs, glove input, cockpit-specific interaction.

6. `Vendor Enhancement Research`
   Utility layers that augment official vendor stacks instead of replacing them.

## Bottom line

This wave pushes `VR.app` closer to a full VR tooling ecosystem:

- overlays
- desktop helpers
- runtime services
- drivers
- external bridges
- calibration tools
- vendor enhancement layers

That broadens the platform in a useful way and makes the repository much more
valuable as a long-term utility foundation.
