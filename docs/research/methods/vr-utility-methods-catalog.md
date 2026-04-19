# VR Utility Methods Catalog

- Date: `2026-04-19`
- Purpose: extract reusable implementation methods and product patterns from the
  tracked VR repositories, so `VR-apps-lab` can grow around proven approaches rather
  than only around named projects.

## How to use this file

Use this document when designing a new module or utility and ask:

1. which implementation method fits the problem?
2. which public repositories already demonstrate that method?
3. is the method better suited as:
   - overlay
   - API layer
   - background desktop utility
   - service/bridge
   - driver
   - creator tool

## Method 1: OpenVR companion overlay app

- What it is:
  a standalone desktop app that connects to `SteamVR/OpenVR` and renders one or
  more overlays in VR.
- Good for:
  quick utility panels, wrist dashboards, notes, clocks, metrics, reference
  windows, small control surfaces.
- Why it matters:
  this is the shortest path to a usable VR utility on current PCVR hardware.
- Strong references:
  `DesktopPlus`, `OpenVRDesktopDisplayPortal`, `openvr_widgets`,
  `OpenVR-AdvancedSettings`, `WhereIsForward`, `OpenVRDeviceBattery`,
  `openvr-metrics`, `VROverlay`, `SteamVR-Webkit`,
  `steamvr_overlay_vulkan`.
- Best fit for `VR-apps-lab`:
  near-term product work.

## Method 2: OpenXR API-layer utility

- What it is:
  a runtime-level layer that sits between the application and the OpenXR
  runtime.
- Good for:
  diagnostics, mirroring, motion compensation, image adjustment, experimental
  overlays, passthrough interception, runtime-level tooling.
- Why it matters:
  this is the cleanest path when utility behavior must exist below the app or
  across multiple apps.
- Strong references:
  `OpenXR-Toolkit`, `OpenXR-Layer-Template`, `OpenXR-Layer-OBSMirror`,
  `OpenXR-OverlayLayer`, `WMR-Passthrough`, `XRFrameTools`.
- Best fit for `VR-apps-lab`:
  medium-term and advanced tooling.

## Method 3: Wrist dashboard / controller-attached UI

- What it is:
  a utility surface attached to the controller or wrist, usually available on
  demand with quick interactions.
- Good for:
  quick actions, stats, battery levels, toggles, shortcuts, overlay controls.
- Why it matters:
  this is one of the most repeatable UX patterns across successful VR utilities.
- Strong references:
  `DesktopPortal`, `wlx-overlay-s`, `SteamVR_ClockOverlay_Public`,
  `OpenVR-AdvancedSettings`, `openvr_widgets`.
- Best fit for `VR-apps-lab`:
  first user-facing utility family.

## Method 4: Desktop-side companion utility

- What it is:
  a Windows or Linux helper app that complements VR usage without necessarily
  rendering in-headset UI.
- Good for:
  config editors, tray tools, runtime switching, battery watchers, install
  helpers, background diagnostics.
- Why it matters:
  many useful VR tools solve friction outside the headset, not only inside it.
- Strong references:
  `OpenXR-API-Layers-GUI`, `OpenXR-Runtime-Switcher` family,
  `steamvr-exconfig`, `OpenVRDeviceBattery`, `SteamVR-Toggle`, `dashfix`,
  `OculusKiller`, `WFOVFix`, `SteamVRAdaptiveBrightness`,
  `SteamVR-ActionsManifestValidator`, `Lighthouse-Scale-Fix`.
- Best fit for `VR-apps-lab`:
  setup utilities and companion workflows.

## Method 5: Micro-utility overlay

- What it is:
  a very small tool with one clear job and almost no platform baggage.
- Good for:
  clocks, forward arrows, cable-direction hints, battery hints, one-function
  overlays.
- Why it matters:
  these projects are often the cleanest examples of focused VR utility design.
- Strong references:
  `WhereIsForward`, `TurnSignal`, `SteamVR_ClockOverlay_Public`,
  `VRBattery`.
- Best fit for `VR-apps-lab`:
  fast MVPs and proof-of-value utilities.

## Method 6: Widget suite / utility shell

- What it is:
  one app hosts multiple small tools or panels under a shared runtime shell.
- Good for:
  dashboards, metrics, keyboards, window capture, toggles, status views.
- Why it matters:
  it reduces startup friction and encourages reuse of runtime scaffolding.
- Strong references:
  `openvr_widgets`, `OpenVR-AdvancedSettings`, `DesktopPortal`,
  `openvr-metrics`, `vr-streaming-overlay`.
- Best fit for `VR-apps-lab`:
  long-term suite architecture.

## Method 7: Runtime switcher and doctor tool

- What it is:
  a tool that inspects XR runtime state, layers, manifests, and runtime
  selection.
- Good for:
  diagnosing broken XR setups, switching runtimes, enabling/disabling layers,
  spotting stale manifests.
- Why it matters:
  this is a natural product category for advanced XR users and developers.
- Strong references:
  `OpenXR-API-Layers-GUI`, `OpenXR-Runtime-Switcher` family,
  `openxr-explorer`, `OpenXR-Inventory`, `xr-picker`,
  `OpenXR-Simulator`, `VirtualDesktop-OpenXR`.
- Best fit for `VR-apps-lab`:
  `OpenXR Doctor`.

## Method 8: Notification and remote-control service bus

- What it is:
  an external process or server drives VR overlay behavior through IPC,
  WebSocket, or JSON payloads.
- Good for:
  notifications, alerts, automation, integration with external apps, stream
  control, status messages.
- Why it matters:
  it turns VR utilities into a platform rather than a closed app.
- Strong references:
  `OpenVROverlayPipe`, `OpenVRNotificationPipe`, `OpenVR2WS`, `VnotifieR`.
- Best fit for `VR-apps-lab`:
  automation and integration layer.

## Method 9: Virtual tracker bridge

- What it is:
  external software or sensors are converted into virtual SteamVR/OpenVR
  trackers, poses, or skeletal data.
- Good for:
  mocap, body tracking, custom sensors, OSC-driven tracking, remote tracking,
  experimental input devices.
- Why it matters:
  this is one of the richest architectural spaces in the entire repo.
- Strong references:
  `VirtualMotionTracker`, `PSMoveServiceEx-VMT`,
  `OpenVR-Tracker-Websocket-Driver`, `Simple-OpenVR-Bridge-Driver`,
  `OpenVR-Driver`,
  `VirtualDesktop-OpenVR-Trackers`.
- Best fit for `VR-apps-lab`:
  tracker bridge platform and experimentation tools.

## Method 10: OSC and external automation bridge

- What it is:
  VR events or poses are exported to OSC, or OSC commands are imported into the
  VR stack.
- Good for:
  VRChat, home automation, stream control, cross-app triggers, integration with
  creative tools.
- Why it matters:
  OSC is a low-friction control plane for VR automation.
- Strong references:
  `SteamVR_To_OSC`, `OpenVR2OSC`, `steamvr-osc-control`, `OpenVR-OSC`,
  `VRCThumbParamsOSC`, `axis-vrc-osc-bridge`, `VRCOSC`, `VRC-OSC`.
- Best fit for `VR-apps-lab`:
  external integration modules.

## Method 11: Device monitor and battery watcher

- What it is:
  a utility that tracks connected devices, battery state, roles, or health.
- Good for:
  battery overlays, inventory views, tray monitors, device status dashboards,
  notifications.
- Why it matters:
  small but very practical user value.
- Strong references:
  `OpenVRDeviceBattery`, `VRBattery`, `OpenVR-Display-Devices`,
  `SteamVR-Devices-Battery-Status`, `steamvrbattery`.
- Best fit for `VR-apps-lab`:
  diagnostics and device health tools.

## Method 12: Calibration wizard

- What it is:
  step-by-step guided alignment or calibration flow for tracking, eye tracking,
  motion compensation, or spatial registration.
- Good for:
  device alignment, eye tracking, mixed tracking spaces, reticle calibration,
  role assignment.
- Why it matters:
  calibration UX is often the difference between a clever tool and a usable
  tool.
- Strong references:
  `OpenVR-SpaceCalibrator`, `OpenXR-MotionCompensation`,
  `EyeTrackVR-OpenVR-Calibration-Overlay`,
  `OpenXR-Canonical-Pose-Tool`.
- Best fit for `VR-apps-lab`:
  tracking helpers and setup tools.

## Method 13: Vendor enhancement layer

- What it is:
  augment the official vendor stack rather than replacing it.
- Good for:
  unlocking extra features, developer APIs, prediction improvements, haptics
  upgrades, optional mod layers.
- Why it matters:
  useful when the official stack exists but leaves value on the table.
- Strong references:
  `PSVR2Toolkit`.
- Best fit for `VR-apps-lab`:
  future vendor-specific research branches.

## Method 14: Creator and research capture tool

- What it is:
  a utility focused on logging, capture, workflow, and content creation rather
  than only live overlay UX.
- Good for:
  session capture, pose logging, NLA recording, performance capture, workflow
  support.
- Why it matters:
  creator tools open a different product track than end-user overlays.
- Strong references:
  `clovr`, `tracking-toolkit`, `XRFrameTools`, `openvr-metrics`,
  `OpenKneeboard`, `OBS-OpenVR-Input-Plugin`, `Valve virtual_display`,
  `SuperScreenShotterVR`, `Periodic-Immersive-SteamVR-Screenshots`.
- Best fit for `VR-apps-lab`:
  diagnostics and creator tools branch.

## Method 15: Passthrough and scoped reality layer experiment

- What it is:
  insert or compose limited real-world imagery or passthrough data into VR.
- Good for:
  external camera windows, projection experiments, scoped passthrough, reality
  tool prototypes.
- Why it matters:
  still valuable as a research direction, even when vendor support is unstable.
- Strong references:
  `openxr-steamvr-passthrough`, `WMR-Passthrough`, `VRPassthrough`,
  `LeapOVRPassthrough`.
- Best fit for `VR-apps-lab`:
  experiments only unless hardware support is proven.

## Method 16: Runtime graphics adapter layer

- What it is:
  an API layer or runtime-side component that bridges incompatible graphics
  paths between the app and the active XR runtime.
- Good for:
  Vulkan-to-D3D runtime bridging, compatibility experiments, graphics
  interop, and runtime bring-up on awkward platform combinations.
- Why it matters:
  not every XR compatibility problem is solved by a runtime switcher; some
  need a true graphics adapter in the middle.
- Strong references:
  `OpenXR-Vk-D3D12`, `VirtualDesktop-OpenXR`, `OpenComposite`, `xrizer`.
- Best fit for `VR-apps-lab`:
  advanced compatibility and runtime research.

## Method 17: Library plus sandbox learning harness

- What it is:
  a reusable runtime wrapper paired with a small sandbox executable that proves
  the wrapper in practice.
- Good for:
  onboarding, engine bring-up, extension experimentation, and keeping complex
  runtime setup reusable without hiding it completely.
- Why it matters:
  this is one of the best ways to turn raw XR bring-up knowledge into a
  reusable development asset.
- Strong references:
  `OpenXRProvider`, `OpenXR-SDK-Source` samples, `Simple-OpenVR-Driver-Tutorial`.
- Best fit for `VR-apps-lab`:
  future sample apps and reusable experimental foundations.

## Method 18: Virtual display and remote presentation driver

- What it is:
  a driver or utility path that repurposes XR compositor output for another
  display, transport, or presentation flow rather than a standard HMD.
- Good for:
  wireless transport, creator capture, 3D displays, AR glasses, simulated
  hardware, and special-purpose stereo output workflows.
- Why it matters:
  this opens a whole class of VR-adjacent tools that are not classic overlays
  and not classic runtime switchers either.
- Strong references:
  `ValveSoftware/virtual_display`, `VRto3D`, `Virtual-Display-Driver`,
  `OpenDisplayXR-VDD`.
- Best fit for `VR-apps-lab`:
  advanced workflow tooling and repurposed-output experiments.

## Method 19: Validation and config-patch micro-tool

- What it is:
  a very focused utility that validates one XR artifact or applies one safe
  configuration fix with backup and rollback behavior.
- Good for:
  manifest linting, SteamVR settings hygiene, one-off environment fixes,
  repair flows, and preflight checks.
- Why it matters:
  tiny helpers like these often solve real workflow pain faster than larger
  dashboard products.
- Strong references:
  `SteamVR-ActionsManifestValidator`, `Lighthouse-Scale-Fix`, `WFOVFix`,
  `steamvr-exconfig`.
- Best fit for `VR-apps-lab`:
  desktop-side helpers and future doctor/preflight tools.

## Method 16: Custom device plumbing and driver prototyping

- What it is:
  integrate new device classes or experimental hardware into the VR stack using
  OpenVR drivers, pose-rewrite layers, or input-emulation sidecars.
- Good for:
  gloves, glasses, Arduino HMDs, cockpit control bridges, distributed tracking,
  legacy peripheral recovery, synthetic controllers, and simulator-linked pose
  manipulation.
- Why it matters:
  it is the main path for hardware experimentation in PCVR.
- Strong references:
  `opengloves-driver`, `GlassVr`, `OpenVR-ArduinoHMD`,
  `hotas-vr-controller`, `hobo_vr`, `Simple-OpenVR-Driver-Tutorial`,
  `SteamVR-OpenHMD`, `Oculus_Touch_Steam_Link`,
  `SlimeVR-OpenVR-Driver`, `VirtualSteamVRDriver`, `driver_hydra`,
  `OpenPSVR`, `OpenVR-driver-for-DIY`, `SegsVRControllerDriverSample`,
  `Barebone`, `Joy2OpenVR`, `SteamVR-Glove`,
  `OpenVR-MotionCompensation`.
- Best fit for `VR-apps-lab`:
  advanced research and hardware bridge branch.

## Method 17: Web-rendered overlay surface

- What it is:
  render a web UI or browser surface into a VR overlay and treat the browser as
  the primary UI layer.
- Good for:
  rich dashboards, remote-control panels, streamer tools, HTML/CSS-based
  interfaces, plugin-friendly control surfaces.
- Why it matters:
  this can dramatically speed up UI iteration and lowers the cost of complex
  panel design.
- Strong references:
  `SteamVR-Webkit`, `overlay_experiments`.
- Best fit for `VR-apps-lab`:
  advanced dashboards and external-control surfaces.

## Method 18: SteamVR environment helper and runtime hygiene tool

- What it is:
  a narrow helper that improves the way SteamVR behaves around startup,
  dashboard input, compositor state, or overlay-heavy workflows.
- Good for:
  toggles, dashboard fixes, distortion tuning, headroom helpers, tray tools,
  pre-launch configuration.
- Why it matters:
  many valuable VR utilities are not overlays at all - they remove runtime
  friction around SteamVR.
- Strong references:
  `steamvr-exconfig`, `dashfix`, `SteamVR-Toggle`, `steamvr-undistort`,
  `SteamVR-VoidScene`, `OculusKiller`, `SteamVRNoHeadset`,
  `ViveTrackerExample`, `WFOVFix`, `SteamVRLinuxFixes`.
- Best fit for `VR-apps-lab`:
  desktop-side support tools and maintenance helpers.

## Method 19: Headless overlay host

- What it is:
  an app whose real job is to keep one or more VR overlays alive while the
  desktop window stays hidden, minimized, or visually irrelevant.
- Good for:
  background overlay suites, tray-driven utilities, Unity-based dashboards
  without desktop clutter, status indicators that should feel always-on.
- Why it matters:
  many practical VR tools are valuable precisely because they do not behave
  like normal foreground desktop apps.
- Strong references:
  `HeadlessOverlayToolkit`, `SteaMeeter`, `VRCMicOverlay`.
- Best fit for `VR-apps-lab`:
  always-on utility hosts and background helper surfaces.

## Method 20: Runtime inventory and capability matrix

- What it is:
  a structured catalog of runtime, middleware, or client capabilities that can
  be parsed, compared, and rendered into human-readable reports or diagnostics.
- Good for:
  capability dashboards, compatibility reports, runtime-health tools, extension
  support matrices, and environment triage.
- Why it matters:
  prose notes alone do not scale once the repository starts comparing many XR
  runtimes, layers, and clients.
- Strong references:
  `OpenXR-Inventory`, `xr-picker`.
- Best fit for `VR-apps-lab`:
  capability intelligence behind `OpenXR Doctor` and related research tools.

## Method 21: Vendor shell replacement and runtime auto-redirect

- What it is:
  replace, intercept, or supervise a vendor launcher or dashboard process so it
  redirects into a different VR runtime or workflow.
- Good for:
  Oculus-to-SteamVR flows, startup cleanup, desktop runtime redirection, and
  narrow environment helpers.
- Why it matters:
  not every valuable VR tool lives inside the headset; some remove friction by
  fixing runtime launch behavior.
- Strong references:
  `OculusKiller`.
- Best fit for `VR-apps-lab`:
  advanced environment-helper and compatibility research.

## Method 22: Headsetless and null-driver development workflow

- What it is:
  run SteamVR or OpenXR tooling without a real headset through null drivers,
  virtual HMDs, or simulator runtimes.
- Good for:
  tool development, test harnesses, tracker-only workflows, manual QA without
  full hardware, and reproducible dev setups.
- Why it matters:
  this method lowers the barrier to developing VR utilities and diagnostics.
- Strong references:
  `SteamVRNoHeadset`, `ViveTrackerExample`, `VirtualSteamVRDriver`,
  `OpenXR-Simulator`, `unity-openvr-tracking`.
- Best fit for `VR-apps-lab`:
  developer tooling, research harnesses, and workflow docs.

## Method 23: OpenVR mirror-surface capture bridge

- What it is:
  acquire SteamVR/OpenVR mirror textures and route them into an external
  desktop application or capture pipeline.
- Good for:
  OBS plugins, creator tools, debugging, stream production, and research
  recording.
- Why it matters:
  capture bridges are a distinct class of VR utility that connects runtime
  output to non-VR tools.
- Strong references:
  `OBS-OpenVR-Input-Plugin`.
- Best fit for `VR-apps-lab`:
  creator workflows and runtime-inspection side tools.

## Method 24: Mixed tracking and controller bridge

- What it is:
  convert foreign runtime devices, external services, or non-native hardware
  into SteamVR/OpenVR controllers, trackers, sensors, or HMD-like devices.
- Good for:
  MixedVR setups, controller reuse, tracker bridging, external pose services,
  and hardware interoperability experiments.
- Why it matters:
  this is one of the richest paths for turning external ecosystems into usable
  VR devices.
- Strong references:
  `Oculus_Touch_Steam_Link`, `SteamVR-OpenHMD`,
  `SlimeVR-OpenVR-Driver`.
- Best fit for `VR-apps-lab`:
  tracker-bridge and driver-plumbing research.

## Method 25: Vision-tracking sidecar with switchable backend

- What it is:
  a camera or CV pipeline estimates pose or gestures in a sidecar process and
  can target more than one output backend such as a SteamVR driver, OSC, or a
  lightweight bridge protocol.
- Good for:
  low-cost body tracking, webcam hand tracking, Quest-friendly calibration
  flows, and experiments where the tracking frontend should stay decoupled from
  the runtime output path.
- Why it matters:
  this method turns one fragile tracker experiment into a reusable pipeline with
  multiple delivery targets.
- Strong references:
  `Mediapipe-VR-Fullbody-Tracking`, `HandCameraDriver`,
  `NVIDIA-BodyTracking`.
- Best fit for `VR-apps-lab`:
  experimental tracking bridges and calibration-first prototypes.

## Method 26: Plugin-based tracking host with service endpoints

- What it is:
  a host application defines contracts for `device plugins` and `service
  endpoints`, then centralizes calibration, lifecycle, and settings UX while
  letting diverse sensors and output targets plug into the same shell.
- Good for:
  alternative tracking ecosystems, modular device support, mixed output targets,
  and long-lived desktop hosts that should survive beyond one sensor class.
- Why it matters:
  this is the cleanest architecture in the repo so far for turning a messy
  tracking ecosystem into a coherent product platform.
- Strong references:
  `KinectToVR/Amethyst`.
- Best fit for `VR-apps-lab`:
  long-term tracking lab architecture and reusable bridge hosts.

## Method 27: Headsetless camera runtime

- What it is:
  a custom OpenXR runtime pretends to be real XR hardware while a separate
  tracker process feeds it camera-derived head and hand input.
- Good for:
  no-HMD QA, education, accessibility experiments, runtime debugging, and
  fake-hardware bring-up without dedicated devices.
- Why it matters:
  this is qualitatively different from a null driver or simulator because it
  owns actual runtime registration, swapchain flow, and runtime-side input.
- Strong references:
  `aethervr`, `OpenXR-Simulator`, `VirtualSteamVRDriver`.
- Best fit for `VR-apps-lab`:
  research harnesses, headsetless workflow docs, and advanced runtime
  experimentation.

## Method 28: Overlay toolkit and prefab scaffolding

- What it is:
  a lightweight helper layer that wraps overlay creation, render-texture
  submission, and pointer/input translation into reusable scene components or
  plugin nodes rather than a full end-user utility product.
- Good for:
  rapid overlay prototyping, Unity or Godot experiments, internal labs, and
  reusable host scaffolding for future utility suites.
- Why it matters:
  this is the shortest path between `raw overlay API` and `finished overlay
  product`, and it keeps early UX experiments from turning into throwaway code.
- Strong references:
  `OVRLay`, `OVROverlayManager`, `openvr_widgets`, `ovr-utils-dashboard`.
- Best fit for `VR-apps-lab`:
  future overlay host abstractions and reusable prototype scaffolds.

## Method 29: Driver ingress endpoint for external tracker feeds

- What it is:
  an OpenVR driver exposes a transport endpoint such as a `named pipe` or local
  `WebSocket` so external programs can spawn, update, or query trackers without
  embedding the whole tracking stack inside the driver.
- Good for:
  CV sidecars, locomotion helpers, browser-based prototypes, mixed-language
  experiments, and custom sensors that should stay out-of-process.
- Why it matters:
  this is one of the cleanest ways to decouple `tracking producer` from
  `SteamVR driver lifecycle`.
- Strong references:
  `Simple-OpenVR-Bridge-Driver`, `OpenVR-Tracker-Websocket-Driver`,
  `3NekoSystem/OpenVR-Tracker-Websocket-Driver`,
  `SegsVRControllerDriverSample`.
- Best fit for `VR-apps-lab`:
  tracker bridge services and experimental sensor ingress.

## Method 30: Engine-side tracked-device adapter with SteamVR role reuse

- What it is:
  a game-engine package reads OpenVR device poses directly and reuses
  SteamVR tracker-role bindings or serial mappings inside scene objects,
  without needing the full end-user SteamVR app stack.
- Good for:
  Unity tools, no-HMD tracker workflows, previs, device visualization, and
  internal lab apps.
- Why it matters:
  it turns SteamVR device state into a reusable engine subsystem instead of a
  one-off integration script.
- Strong references:
  `unity-openvr-tracking`, `SteamVRTrackerUtility`, `ViveTrackerExample`.
- Best fit for `VR-apps-lab`:
  engine plugins, no-HMD development workflows, and internal research tools.

## Method 31: Direct tracker and controller state export to OSC consumers

- What it is:
  a desktop sidecar turns SteamVR state, tracker roles, controller actions, or
  vendor-specific body data into OSC messages for VRChat or other consumers,
  without requiring a new SteamVR driver.
- Good for:
  avatar parameters, Quest-friendly workflows, remote control surfaces, and
  thin consumer-facing bridges.
- Why it matters:
  sometimes the shortest and most honest utility path is
  `SteamVR or vendor SDK -> OSC consumer`, not `new driver`.
- Strong references:
  `OpenVR-OSC`, `VRCThumbParamsOSC`, `axis-vrc-osc-bridge`,
  `OpenVR2OSC`, `SteamVR_To_OSC`.
- Best fit for `VR-apps-lab`:
  direct consumer bridges, avatar utilities, and quick automation prototypes.

## Method 32: Existing UI stack to overlay texture bridge

- What it is:
  an overlay host reuses a mature UI stack such as `WinForms`, `WPF`, `CEF`,
  or `ImGui`, rasterizes it into a texture, and translates overlay input back
  into that UI runtime.
- Good for:
  dashboard apps, browser-backed utilities, desktop-parity tools, and
  productivity overlays that should not be rebuilt from scratch as VR-only UI.
- Why it matters:
  this is one of the shortest paths from `desktop-grade UI` to
  `usable VR overlay`, and it keeps the overlay layer focused on transport,
  lifecycle, and input translation.
- Strong references:
  `SteamVR_HUDCenter`, `SteamVR-WebApps`, `h-view`.
- Best fit for `VR-apps-lab`:
  future overlay shells, control surfaces, and diagnostics tools with desktop
  parity.

## Method 33: Overlay patch micro-tool over an existing runtime surface

- What it is:
  a tiny helper finds an overlay the runtime already owns and modifies its
  bounds, placement, or behavior instead of rendering a new overlay host.
- Good for:
  desktop-overlay crop tools, workflow patches, corrective helpers, and
  extremely narrow utilities that should stay small.
- Why it matters:
  sometimes the right VR utility is not `new overlay app`; it is
  `surgical patch over the overlay users already have`.
- Strong references:
  `SteamVR-PrimaryDesktopOverlay`.
- Best fit for `VR-apps-lab`:
  small corrective helpers and runtime-comfort micro-tools.

## Method 34: Scene-based overlay scaffold with tracked attachments

- What it is:
  a Unity or engine scene acts as the overlay body, while tracked-device
  helpers, sensors, or simple interactions drive scene content inside that
  overlay space.
- Good for:
  embodied HUDs, tracker-mounted scenes, experimental utility shells,
  sensor-enhanced overlays, and rapid spatial UI experiments.
- Why it matters:
  not every useful overlay should start as a flat desktop panel; some utility
  concepts are easier to prototype as a small scene with tracked attachments.
- Strong references:
  `VRSceneOverlay`, `VROverlay`, `OVROverlayManager`.
- Best fit for `VR-apps-lab`:
  experimental overlay concepts, scene-overlay labs, and tracker-aware utility
  prototypes.

## Recommended usage inside `VR-apps-lab`

When a new utility idea appears:

1. classify it first by `method`;
2. then map it to a `project family`;
3. then look up which repositories already demonstrate that method;
4. then decide whether `VR-apps-lab` should build it as:
   - overlay
   - desktop companion
   - service
   - API layer
   - driver
   - creator tool
