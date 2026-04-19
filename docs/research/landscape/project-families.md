# Project Families

- Date: `2026-04-19`
- Goal: reorganize the `VR-apps-lab` research corpus around logical overlap
  families instead of a long flat list of repositories.

## Why this file exists

At this point `VR-apps-lab` already contains:

- a large initial landscape pass;
- multiple follow-up research waves;
- several focused reuse-plan documents;
- deeper passes on under-documented repositories.

The next useful step is not more random expansion. It is `grouping`,
`deduplication by idea`, and understanding which clusters are already mature.

## Status legend

- `Already studied`
  covered well enough across one or more existing docs.
- `Partially studied`
  present in `VR-apps-lab`, but still deserving a dedicated deeper code-level pass.
- `Not studied deeply`
  either missing from the repo or only known through a quick mention.
- `Fork / variant only`
  valuable for comparison, but probably not worth a full standalone deep dive
  before the main upstream is understood.

## Family 1: OpenXR runtime switchers, inventories, and layer managers

This family is already converging into the future `OpenXR Doctor` direction.

| Project | Status | Notes |
|---|---|---|
| `KhronosGroup/OpenXR-Inventory` | Already studied | Structured capability matrix for runtime and middleware support |
| `rpavlik/xr-picker` | Already studied | Clean core/GUI split for runtime picking and manifest inspection |
| `elliotttate/OpenXR-Simulator` | Already studied | Headsetless runtime and runtime-registration reference |
| `mbucchia/OpenXR-Vk-D3D12` | Already studied | Graphics API adapter layer bridging Vulkan/OpenGL apps into D3D12-only runtime paths |
| `mbucchia/VirtualDesktop-OpenXR` | Already studied | Full runtime implementation reference with registration, settings watch, and precompositor paths |
| `fredemmott/OpenXR-API-Layers-GUI` | Already studied | Strongest layer diagnostics and enable/disable UX reference |
| `WaGi-Coding/OpenXR-Runtime-Switcher` | Already studied | Runtime switching reference with admin-aware UX |
| `UniStuttgart-VISUS/OpenXR-Runtime-Switcher` | Already studied | Alternate runtime switcher framing |
| `ytdlder/OpenXR-Switcher` | Already studied | Runtime and layer toggling overlap |
| `jonyrh/OXR_Switcher` | Already studied | Runtime manager UX variant with CLI angle |
| `shiena/OpenXRRuntimeSelector` | Already studied | Engine-side runtime selection helper built around runtime providers and registry enumeration |
| `1runeberg/OpenXRProvider` | Partially studied | Library plus sandbox wrapper around OpenXR core, render, and input bring-up |
| `mbucchia/OpenXR-Layer-Template` | Already studied | Bootstrap template for future layer work |
| `Jabbah/OpenXR-Layer-OBSMirror` | Already studied | Practical example of a layer built from a template |
| `maluoi/openxr-explorer` | Already studied | Strongest single reference for `OpenXR doctor/runtime inspector` |
| `Ybalrid/OpenXR-Runtime-Manager` | Not studied deeply | Additional runtime-manager variant for comparison |
| `pembem22/etvr-openxr-layer` | Not studied deeply | Niche OpenXR layer worth comparing with diagnostics/layer family |
| `clear-xr/clearxr-server` | Not studied deeply | Candidate runtime-side service node to inspect later |

### Consolidation note

This is one of the highest-overlap families in the whole repository. The main
output of this family for `VR-apps-lab` should be a single future product concept:

- `OpenXR Doctor`
- `runtime capability matrix`
- `runtime adapter and bring-up playbook`

## Family 2: SteamVR/OpenVR notification and remote-control overlays

This family centers on letting an external process drive overlay or
notification behavior.

| Project | Status | Notes |
|---|---|---|
| `BOLL7708/OpenVROverlayPipe` | Already studied | Best reference for `server-driven overlay creation` |
| `jeppevinkel/OpenVRNotificationPipe` | Already studied | Focused notification pipe reference |
| `WiiPlayer2/VnotifieR` | Partially studied | Same product family, useful as a comparison point |
| `BOLL7708/OpenVR2WS` | Already studied | Broader runtime I/O and settings bridge |
| `I5UCC/SteaMeeter` | Already studied | Dashboard bridge into an external audio/control system |
| `I5UCC/ParameterSaveStates` | Not studied deeply | Related automation/control-surface family node |
| `hai-vr/h-view` | Not studied deeply | Candidate remote/control utility worth a follow-up pass |
| `MeroFune/GOpy` | Not studied deeply | Additional control/integration utility candidate |

### Consolidation note

This family points toward a future `VR notification / overlay service bus`
instead of several unrelated mini-tools.

## Family 3: Lighthouse managers and room-state helpers

This is a large family with very high overlap in problem space and very low
need for flat duplication in the index.

| Project | Status | Notes |
|---|---|---|
| `kurotu/OVR-Lighthouse-Manager` | Already studied | One of the main Windows references |
| `DHCPCD9/go-steamvr-lighthouse-manager` | Already studied | Alternate UI/automation angle |
| `xi-ve/openvr-lighthouse-manager-linux` | Already studied | Linux port/reference |
| `nouser2013/lighthouse-v2-manager` | Already studied | Small scripting-oriented variant |
| `SeeUnsharp/LighthouseManager` | Already studied | Command-line and Windows BLE angle |
| `seader/LighthouseManagerPimax` | Already studied | Pimax-oriented variant |
| `FennecLabsLtd/LighthouseManager` | Already studied | Config backup/restore framing |
| `risa2000/lhctrl` | Already studied | Linux BLE micro-tool for v1 |
| `risa2000/lh2ctrl` | Already studied | Linux BLE micro-tool for v2 |
| `ugokutennp/watchman-pairing-assistant` | Already studied | GUI wrapper around pairing flows and `lighthouse_console` |

### Consolidation note

This family deserves a later comparative matrix, because the main axis is not
just platform but also:

- `power only`
- `BLE control`
- `room/config backup`
- `SteamVR automation`

## Family 4: Battery and device-monitor utilities

This family has a lot of logical duplication, but it is still useful because it
shows different product scales: tray app, overlay, notification tool, inventory
panel, and logging utility.

| Project | Status | Notes |
|---|---|---|
| `OVRTools/OpenVRDeviceBattery` | Already studied | Strong tray-app and background-helper reference |
| `zeroae/VRBattery` | Partially studied | Good battery-only overlay/product reference |
| `Black4Blade/SteamVR-Devices-Battery-Status` | Already studied | Tiny battery micro-tool reference |
| `rhaamo/OpenVR-Display-Devices` | Already studied | Broader device inventory view |
| `copperpixel/steamvrbattery` | Already studied | Minimal CLI property-polling battery monitor |
| `Denwa/vive-wireless-info-overlay` | Not studied deeply | Wireless-link and device-health overlay candidate |
| `KaftanOS/SteamVR-Battery-Checker` | Not studied deeply | Charging-state micro-tool worth comparison |
| `jangxx/openvr-battery-monitoring` | Not studied deeply | Likely useful for notifications/logging behavior |
| `mutr/openvr_battery_monitor` | Not studied deeply | Another narrow monitoring variant worth comparing |

### Consolidation note

This should become a single `Device Monitor` family inside `VR-apps-lab`, with
sub-modes like:

- wrist/device overlay
- tray/desktop watcher
- notification-only helper
- inventory/detail screen

## Family 5: Virtual tracker, OSC, WebSocket, and bridge tooling

This is one of the most strategically valuable families because it converts
external data into `SteamVR/OpenVR devices`, `pose streams`, or `OSC events`.

| Project | Status | Notes |
|---|---|---|
| `Timocop/PSMoveServiceEx-VMT` | Already studied | Core virtual-tracker reference |
| `gpsnmeajp/VirtualMotionTracker` | Partially studied | Likely central project in this family |
| `John-Dean/OpenVR-Tracker-Websocket-Driver` | Partially studied | Strong WebSocket-native tracker-driver reference |
| `surplex-io/OpenVR-Driver` | Partially studied | Alternative evolution of the same idea |
| `3NekoSystem/OpenVR-Tracker-Websocket-Driver` | Not studied deeply | Variant/fork comparison target |
| `v0xie/OpenVR-Tracker-Websocket-Driver` | Not studied deeply | Variant/fork comparison target |
| `krazysh01/VirtualDesktop-OpenVR-Trackers` | Partially studied | Body-state bridge from an external ecosystem |
| `Greendayle/SteamVR_To_OSC` | Already studied | SteamVR to OSC bridge |
| `ZekkVRC/OpenVR2OSC` | Already studied | VRChat-oriented input bridge |
| `BarakChamo/OpenVR-OSC` | Not studied deeply | Should be added for broader OSC comparison |
| `jangxx/steamvr-osc-control` | Already studied | Control bridge for SteamVR functions |
| `choyai/SteamVRTrackerUtility` | Not studied deeply | Tracker role/power helper worth comparison with tracker bridge family |
| `TriadSemi/triad_openvr` | Already studied | Strong Python wrapper for scripting, events, and device polling |
| `biosmanager/unity-openvr-tracking` | Not studied deeply | Unity-side tracking bridge/reference candidate |

### Consolidation note

This family is the clearest foundation for a future:

- `Tracker Bridge Service`
- `SteamVR/OSC bridge`
- `external sensor -> virtual tracker` platform

## Family 6: Desktop and overlay utility suites

This family overlaps heavily in product goal even when implementation differs
by runtime or operating system.

| Project | Status | Notes |
|---|---|---|
| `DesktopXR` | Already studied | OpenXR desktop-overlay product reference |
| `DesktopPlus` | Already studied | Strongest Windows/OpenVR product reference |
| `OpenVRDesktopDisplayPortal` | Already studied | Early but feature-rich overlay utility |
| `DesktopPortal` | Already studied | Utility-suite framing with watch controls |
| `UVROverlay` | Already studied | General-purpose overlay shell |
| `WlxOverlay` | Already studied | Linux-first overlay reference |
| `wlx-overlay-s` | Already studied | Modern lightweight Linux overlay reference |
| `wlx-overlay-x` | Already studied | Transitional OpenXR overlay path |
| `fnuidesktop-VR` | Already studied | Direct desktop interaction patterns |
| `wayvr` | Already studied | Low-overhead desktop/app-launching view |
| `rrkpp/SpotifyOverlay` | Already studied | Qt dashboard micro-utility rendered offscreen into OpenVR |
| `Hotrian/OpenVRTwitchChat` | Already studied | Twitch-specific chat overlay with threaded service layer and profile persistence |
| `CrispyPin/ovr-utils` | Partially studied | GitHub snapshot is stale and moved off-platform |
| `mittorn/ovr-utils-dashboard` | Partially studied | Useful dashboard-style variant |
| `artumino/SteamVR_HUDCenter` | Not studied deeply | Centered HUD micro-utility worth a later pass |
| `LapisGit/LapisOverlay` | Not studied deeply | Multi-purpose overlay shell in progress |
| `elvissteinjr/SteamVR-PrimaryDesktopOverlay` | Not studied deeply | Focused desktop-overlay sample from a strong maintainer |
| `Nexz/turncountervr` | Not studied deeply | Rotation counter / cable-awareness overlay node |

### Consolidation note

This family should feed a future comparative UX document, not just more
individual project entries. The real overlap axes are:

- `desktop mirror`
- `window portal`
- `wrist/watch controls`
- `dashboard suite`
- `Linux vs Windows UX`
- `OpenVR overlay vs OpenXR layer`

## Family 7: Accessibility overlays and assistive HUDs

This family is present in the repo, but not yet treated as a first-class
product direction.

| Project | Status | Notes |
|---|---|---|
| `Vinventive/live-captions-vr` | Already studied | Speech-to-text overlay reference |
| `MochiDoesVR/OpenVRCaptions` | Already studied | C#/SteamVR captions reference |
| `matzman666/OpenVR-MicrophoneControl` | Already studied | Dashboard mute/PTT overlay with OS audio integration |
| `Beyley/eepyxr` | Already studied | OpenXR overlay utility framed around comfort/sleep use |
| `rrazgriz/VRCMicOverlay` | Already studied | Minimal HMD-relative mic-state overlay with OSC/audio hooks |
| `I5UCC/VRCTextboxSTT` | Already studied | Local STT service with SteamVR overlay as one output surface |
| `OpenVROverlayPipe` / notification tools | Already studied | Assistive notification angle |
| `TurnSignal` | Already studied | Comfort/safety micro-utility |
| `SteamVR_ClockOverlay_Public` | Already studied | Minimal assistive wrist-clock pattern |

### Consolidation note

This is big enough to be treated as a product family:

- captions
- status hints
- assistive HUDs
- comfort and orientation helpers

## Family 8: Driver tutorials and custom-device plumbing

This family is less about end-user utilities and more about building the
knowledge needed for `device-side tooling`.

| Project | Status | Notes |
|---|---|---|
| `terminal29/Simple-OpenVR-Driver-Tutorial` | Partially studied | Important learning-path repo |
| `ValveSoftware/openvr` tutorial/sample code | Already studied | Foundational reference |
| `ChristophHaag/SteamVR-OpenHMD` | Already studied | OpenHMD hardware bridge into SteamVR/OpenVR |
| `mm0zct/Oculus_Touch_Steam_Link` | Already studied | Mixed-VR controller, tracker, and sensor bridge driver |
| `SlimeVR/SlimeVR-OpenVR-Driver` | Already studied | Modern tracker bridge driver with external service transport |
| `oleuzop/VirtualSteamVRDriver` | Already studied | Virtual HMD driver for no-headset development and testing |
| `finallyfunctional/openvr-driver-example` | Already studied | Beginner-friendly controller/input-emulation driver tutorial |
| `SecondReality/VirtualControllerDriver` | Already studied | Tiny synthetic controller driver for mixed-reality workflows |
| `oneup03/VRto3D` | Already studied | Productized stereo-display and AR-glasses driver that heavily reshapes SteamVR behavior |
| `ValveSoftware/driver_hydra` | Already studied | Official peripheral bridge driver with controller realignment and calibration monitor |
| `alatnet/OpenPSVR` | Partially studied | Full PSVR HMD/display driver with sensor fusion, display component, and watchdog split |
| `r57zone/OpenVR-driver-for-DIY` | Already studied | Keyboard-driven DIY null-HMD plus controller path built close to the stock sample |
| `gpsnmeajp/SegsVRControllerDriverSample` | Already studied | Controller-driver sample with a shared-memory helper client and JSON payloads |
| `puresoul/Barebone` | Partially studied | XInput-driven synthetic Vive controller path anchored relative to the HMD |
| `mmorselli/Joy2OpenVR` | Already studied | DirectInput-to-InputEmulator sidecar for unusual physical controllers |
| `mdovgialo/SteamVR-Glove` | Already studied | Arduino glove proof of concept piggybacking on existing Vive controller tracking |
| `openvrmc/OpenVR-MotionCompensation` | Partially studied | Pose-rewrite driver with shared library and in-VR dashboard configuration |
| `OpenDisplayXR/OpenDisplayXR-VDD` | Not studied deeply | Sparse but relevant signal for a simulated OpenVR/OpenXR virtual hardware path |
| `verncat/RayNeo-Air-3S-Pro-OpenVR` | Not studied deeply | Early AR-glasses/OpenVR bridge signal that currently looks more like SDK scaffolding |
| `LucidVR/opengloves-driver` | Partially studied | Hand-specific custom device path |
| `r57zone/OpenVR-ArduinoHMD` | Partially studied | DIY HMD and config-driven setup |
| `DaniXmir/GlassVr` | Partially studied | XR/AR glasses bridge and emulation |
| `Copprhead/hotas-vr-controller` | Partially studied | Domain-specific cockpit/device bridge |
| `TrueOpenVR/SteamVR-TrueOpenVR` | Not studied deeply | Candidate for a later driver pass |
| `HoboVR-Labs/hobo_vr` | Partially studied | Driver prototyping and external poser model |

### Consolidation note

This should eventually become a dedicated learning track in `VR-apps-lab`:

- `driver tutorial`
- `custom device plumbing`
- `synthetic controller and input-emulation sidecars`
- `pose rewriting and motion-manipulation drivers`
- `domain-specific hardware bridges`
- `virtual display and repurposed output drivers`

## Family 9: Vendor enhancement and mod layers

These projects are especially useful because they sit `on top of` official
vendor stacks instead of replacing them.

| Project | Status | Notes |
|---|---|---|
| `BnuuySolutions/PSVR2Toolkit` | Partially studied | Strongest current vendor-enhancement reference |
| `PSVR2-related forks/variants` | Not studied deeply | Worth mapping later if this branch expands |

### Consolidation note

This family supports a future `vendor enhancement` research direction:

- augment official stack
- keep vendor runtime intact
- expose extra features through utility-side APIs

## Family 10: Compatibility layers and runtime translation

These projects sit between incompatible or competing runtime ecosystems and are
valuable for understanding translation, emulation, and compatibility shims.

| Project | Status | Notes |
|---|---|---|
| `QuestCraftPlusPlus/OpenComposite` | Already studied | Main OpenVR-to-OpenXR compatibility reference |
| `Supreeeme/xrizer` | Already studied | Alternate OpenVR-on-OpenXR direction |
| `LibreVR/Revive` | Already studied | Compatibility layer between Oculus stack and OpenVR/OpenXR |
| `alvr-org/ALVR` | Already studied | Streaming stack, but also useful for runtime compatibility patterns |

### Consolidation note

This family matters less as a direct product target and more as a source of:

- translation-layer architecture
- runtime compatibility patterns
- install and registration models

## Family 11: Performance, rendering, and post-process tooling

This family is about image processing, foveation, scaling, and rendering-side
instrumentation rather than overlays or device control.

| Project | Status | Notes |
|---|---|---|
| `fholger/vrperfkit` | Already studied | Main donor for D3D11 post-process patterns |
| `fholger/openvr_fsr` | Already studied | Earlier, smaller reference for the same lineage |
| `RavenSystem/VRPerfKit_RSF` | Partially studied | Practical fork/variant with extended features |
| `CamelCaseName/OpenVRPerfKit` | Partially studied | Additional evolution path in the same family |
| `Granther/foveated-rendering` | Partially studied | Eye-tracked/foveated experimentation branch |
| `mbucchia/Quad-Views-Foveated` | Partially studied | Important OpenXR eye-tracked/foveation reference |
| `mbucchia/OpenXR-Eye-Trackers` | Partially studied | Useful eye-gaze integration reference |
| `retroluxfilm/reshade-vrtoolkit` | Partially studied | Shader-pipeline and image-adjustment reference |
| `zhukovv/upscale-injection` | Partially studied | Generic D3D11 injection and upscaling reference |

### Consolidation note

This family should feed:

- GPU-side processing ideas
- future texture-path upgrades
- foveation and eye-tracking experimentation

## Family 12: Passthrough, reality layers, and camera experiments

This family is directly relevant to the original `Reality Window` concept, even
though not all projects are practical product donors for current target
hardware.

| Project | Status | Notes |
|---|---|---|
| `Rectus/openxr-steamvr-passthrough` | Already studied | Closest PC/SteamVR architectural analogue to the original idea |
| `zhangxuelei86/WMR-Passthrough` | Already studied | OpenXR API-layer plus camera-service pattern |
| `Danealor/VRPassthrough` | Already studied | Lightweight USB-camera passthrough utility path |
| `jangxx/LeapOVRPassthrough` | Already studied | Gesture-triggered passthrough UX reference |
| `alexander-clarke/openvr-room-mapping` | Not studied deeply | Possible room-scan and environment-capture comparison node |

### Consolidation note

This family is now best treated as:

- `research and experimentation`
- `external camera / scoped passthrough` inspiration

rather than a guaranteed production direction.

## Family 13: Creator tools, capture, metrics, and workflow utilities

These projects are more about recording, inspection, workflow support, and
creator-facing XR use than about simple end-user overlays.

| Project | Status | Notes |
|---|---|---|
| `OpenKneeboard/OpenKneeboard` | Already studied | Strong simulator and workflow-oriented overlay reference |
| `baffler/OBS-OpenVR-Input-Plugin` | Already studied | OpenVR mirror-texture capture into OBS through D3D11 shared resources |
| `ValveSoftware/virtual_display` | Already studied | `IVRVirtualDisplay` sample with out-of-process remote presentation transport |
| `BOLL7708/SuperScreenShotterVR` | Already studied | Screenshot utility combining viewfinder overlays, notifications, timers, and WebSocket automation |
| `iigomaru/Periodic-Immersive-SteamVR-Screenshots` | Already studied | Ultra-small timed screenshot micro-utility for startup-overlay workflows |
| `xrtlab/clovr` | Already studied | Session capture and research-tooling reference |
| `ethanporcaro/tracking-toolkit` | Already studied | Creator-facing OpenXR recording and Blender integration |
| `Nyabsi/openvr-metrics` | Already studied | Strong metrics + control overlay product reference |
| `fredemmott/XRFrameTools` | Already studied | OpenXR frame-loop metrics reference |
| `peacepenguin/Virtual-Display-Driver` | Already studied | Infrastructure for desktop and workflow scenarios |
| `ValveSoftware/OpenXR-Canonical-Pose-Tool` | Already studied | Runtime-vendor pose validation and canonical-pose comparison tool |

### Consolidation note

This family supports a separate `creator and diagnostics` branch inside
`VR-apps-lab`, not just consumer-facing overlays.

It also strengthens a smaller but useful sub-branch:

- screenshot workflow helpers
- creator micro-automation tools
- remote-triggered capture flows

## Family 14: Overlay implementation references and host scaffolds

These repos are especially useful for understanding `how to build` overlays,
not only how finished utility products behave.

| Project | Status | Notes |
|---|---|---|
| `sh-akira/VROverlay` | Already studied | Unity/OpenVR overlay sample with VR UI pointer plumbing |
| `BenWoodford/SteamVR-Webkit` | Already studied | Browser-backed overlay toolkit with JS interop |
| `beniwtv/vr-streaming-overlay` | Already studied | Godot multi-overlay shell with widget/config split |
| `Nyabsi/steamvr_overlay_vulkan` | Already studied | Modern Vulkan/ImGui overlay template |
| `Hotrian/HeadlessOverlayToolkit` | Already studied | Hidden-window and background-host overlay pattern in Unity |
| `cnlohr/openvr_overlay_model` | Already studied | Experimental stereo-per-eye overlay technique for pseudo-3D content |
| `JoeLudwig/overlay_experiments` | Already studied | Historical browser-backed OpenVR dashboard experiments |
| `Martin-Oehler/SteamVR-WebApps` | Not studied deeply | Web-app-driven overlay direction worth comparing later |
| `KainosSoftwareLtd/VRSceneOverlay` | Not studied deeply | Unity scene-overlay implementation reference |
| `vrkit-platform/vrkit-platform` | Not studied deeply | OpenXR monitor/overlay platform worth deeper inspection |
| `LunarG/OpenXR-Overlays-UE4-Plugin` | Not studied deeply | Engine-side overlay integration sample |
| `mbucchia/_ARCHIVE_OverXR` | Fork / variant only | Current GitHub state is an archive shell with little code to inspect |

### Consolidation note

This family should feed `VR-apps-lab` as a methods donor layer:

- overlay lifecycle references
- graphics-path references
- UI stack references
- host-scene and render-loop scaffolds

## Family 15: SteamVR environment helpers and runtime hygiene tools

These utilities improve the way SteamVR behaves around startup, dashboard
interaction, distortion, or overlay-heavy workflows.

| Project | Status | Notes |
|---|---|---|
| `MuffinTastic/steamvr-exconfig` | Partially studied | Pre-launch SteamVR config editor and cleanup helper |
| `BnuuySolutions/OculusKiller` | Already studied | Vendor-shell replacement that redirects Oculus launch flow into SteamVR |
| `username223/SteamVRNoHeadset` | Already studied | Null-driver and no-HMD recipe for SteamVR workflows |
| `n1ckfg/ViveTrackerExample` | Already studied | Tracker-without-HMD workflow and tiny Unity helper |
| `craftyinsomniac/WFOVFix` | Already studied | Guided SteamVR settings patcher for wide-FOV headsets |
| `BnuuySolutions/SteamVRLinuxFixes` | Already studied | Vulkan-layer and compositor-fix utility for Linux SteamVR |
| `simonowen/dashfix` | Already studied | Dashboard-input fix via SDL hook injection |
| `W-Drew/SteamVR-Toggle` | Already studied | Tray utility that toggles SteamVR by renaming install path |
| `sencercoltu/steamvr-undistort` | Already studied | Lens distortion adjustment tool for custom optics |
| `elvissteinjr/SteamVR-VoidScene` | Already studied | Minimal scene app to lower baseline cost for overlay use |
| `Virus-vr/SteamVRAdaptiveBrightness` | Already studied | Mirror-texture analysis helper that continuously rewrites SteamVR brightness |
| `username223/SteamVR-ActionsManifestValidator` | Already studied | CLI manifest validator for SteamVR input/action metadata |
| `Erimelowo/Lighthouse-Scale-Fix` | Already studied | Backup-safe one-shot patcher for lighthouse scale configuration |
| `DavidRisch/steamvr_utils` | Not studied deeply | Linux SteamVR helper collection worth future comparison |

### Consolidation note

This family points toward a separate `environment helper` track inside
`VR-apps-lab`, not just overlays:

- tray toggles
- dashboard fixes
- scene-host helpers
- compositor and distortion helpers
- headsetless/null-driver helpers
- vendor-shell redirects and focused config patchers
- validation and lint micro-tools
- backup-safe config patchers

## Recommended synthesis path for `VR-apps-lab`

The next useful step is not another long unsorted list.

It is:

1. build product concepts around `families`, not repos;
2. prioritize deep dives where status is `Partially studied` or
   `Not studied deeply`;
3. keep forks/variants as comparison nodes instead of promoting each one to a
   full standalone research wave.
