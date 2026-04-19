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
| `ox-runtime/ox-sim-driver` | Already studied | Automation-friendly simulator runtime with shared core plus GUI and programmatic control paths |
| `davidrios/openxr-device-simulator` | Not studied deeply | Thin but relevant Rust runtime-simulator signal that still needs a clearer public pass |
| `mbucchia/OpenXR-Vk-D3D12` | Already studied | Graphics API adapter layer bridging Vulkan/OpenGL apps into D3D12-only runtime paths |
| `mbucchia/VirtualDesktop-OpenXR` | Already studied | Full runtime implementation reference with registration, settings watch, and precompositor paths |
| `fredemmott/OpenXR-API-Layers-GUI` | Already studied | Strongest layer diagnostics and enable/disable UX reference |
| `WaGi-Coding/OpenXR-Runtime-Switcher` | Already studied | Runtime switching reference with admin-aware UX |
| `UniStuttgart-VISUS/OpenXR-Runtime-Switcher` | Already studied | Alternate runtime switcher framing |
| `ytdlder/OpenXR-Switcher` | Already studied | Runtime and layer toggling overlap |
| `jonyrh/OXR_Switcher` | Already studied | Runtime manager UX variant with CLI angle |
| `shiena/OpenXRRuntimeSelector` | Already studied | Engine-side runtime selection helper built around runtime providers and registry enumeration |
| `1runeberg/OpenXRProvider` | Already studied | Library plus sandbox wrapper around OpenXR core, render, and input bring-up |
| `mbucchia/OpenXR-Layer-Template` | Already studied | Bootstrap template for future layer work |
| `Jabbah/OpenXR-Layer-OBSMirror` | Already studied | Practical example of a layer built from a template |
| `maluoi/openxr-explorer` | Already studied | Strongest single reference for `OpenXR doctor/runtime inspector` |
| `Ybalrid/OpenXR-Runtime-Manager` | Already studied | Small WPF runtime switcher built around registry reads plus well-known manifest probes |
| `PlutoVR/OpenXR-OverlayLayer-1` | Already studied | Remote overlay client plus API-layer experiment using shared-memory RPC |
| `pembem22/etvr-openxr-layer` | Already studied | Android-side implicit API layer that adapts OSC eye-tracking data into OpenXR gaze surfaces |
| `clear-xr/clearxr-server` | Already studied | Runtime-side platform split across desktop streamer, landing-space app, and action-rewriting OpenXR API layer |
| `vrkit-platform/vrkit-platform` | Partially studied | Electron or native-interop utility platform with strong plugin and overlay-manager slices, but still broad and scope-shifted |

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
| `WiiPlayer2/VnotifieR` | Already studied | Local HTTP notification server with config-driven overlay placement and fade behavior |
| `BOLL7708/OpenVR2WS` | Already studied | Broader runtime I/O and settings bridge |
| `I5UCC/SteaMeeter` | Already studied | Dashboard bridge into an external audio/control system |
| `I5UCC/ParameterSaveStates` | Not studied deeply | Related automation/control-surface family node |
| `hai-vr/h-view` | Already studied | Desktop-plus-overlay utility host with OSCQuery tooling, hardware views, and strong overlay-management slices |
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
| `zeroae/VRBattery` | Already studied | Tiny Qt battery widget rendered into an OpenVR dashboard surface |
| `Black4Blade/SteamVR-Devices-Battery-Status` | Already studied | Tiny battery micro-tool reference |
| `rhaamo/OpenVR-Display-Devices` | Already studied | Broader device inventory view |
| `copperpixel/steamvrbattery` | Already studied | Minimal CLI property-polling battery monitor |
| `Denwa/vive-wireless-info-overlay` | Not studied deeply | Source-light wireless-temperature micro-overlay whose product framing is stronger than its visible code donor value |
| `KaftanOS/SteamVR-Battery-Checker` | Already studied | Tiny one-shot Python battery inspector with almost no product baggage |
| `jangxx/openvr-battery-monitoring` | Already studied | Tray watcher that reacts to charging-state changes and can notify through desktop or OVRT channels |
| `mutr/openvr_battery_monitor` | Already studied | Background battery exporter that writes per-device telemetry to InfluxDB |

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
| `gpsnmeajp/VirtualMotionTracker` | Already studied | Mature OSC tracker platform with manager/driver split and skeletal input support |
| `John-Dean/OpenVR-Tracker-Websocket-Driver` | Already studied | Mainline WebSocket tracker-service driver with local HTTP test surface and pose echo |
| `surplex-io/OpenVR-Driver` | Fork / variant only | Near-clone of the John-Dean line that mainly adds tracker-role mapping |
| `ju1ce/Simple-OpenVR-Bridge-Driver` | Already studied | Named-pipe bridge-driver skeleton with explicit tracker lifecycle, timing sync, and pose readback helpers |
| `3NekoSystem/OpenVR-Tracker-Websocket-Driver` | Fork / variant only | Simpler JSON/WebSocket fork on `8082` that trims the broader local-service ambitions of the main WebSocket line |
| `v0xie/OpenVR-Tracker-Websocket-Driver` | Fork / variant only | Near-mirror of the John-Dean line with the same local web page, HTTPS helpers, and device-state echo surfaces |
| `krazysh01/VirtualDesktop-OpenVR-Trackers` | Partially studied | Tracker-bridge signal from an external ecosystem whose current public snapshot still looks thinner than expected |
| `SophiaH67/soph_wireless` | Already studied | UDP relay driver that re-registers tracker state from another SteamVR instance |
| `SophiaH67/soph_wireless_transmitter` | Already studied | Tiny paired sender utility that makes the relay packet contract explicit |
| `Greendayle/SteamVR_To_OSC` | Already studied | SteamVR to OSC bridge |
| `ZekkVRC/OpenVR2OSC` | Already studied | VRChat-oriented input bridge |
| `BarakChamo/OpenVR-OSC` | Already studied | Minimal OpenVR pose-to-OSC exporter built around `triad_openvr` and OSC bundles |
| `jangxx/steamvr-osc-control` | Already studied | Control bridge for SteamVR functions |
| `choyai/SteamVRTrackerUtility` | Already studied | Tiny serial-based identity helper for deterministic tracker binding workflows |
| `TriadSemi/triad_openvr` | Already studied | Strong Python wrapper for scripting, events, and device polling |
| `biosmanager/unity-openvr-tracking` | Already studied | Unity-side OpenVR adapter with no-HMD-friendly initialization and SteamVR tracker-role reuse |
| `JLChnToZ/axis-vrc-osc-bridge` | Already studied | Standalone vendor-tracker-to-VRChat OSC bridge that bypasses the SteamVR driver path |
| `I5UCC/VRCThumbParamsOSC` | Already studied | Configurable SteamVR/XInput-to-VRChat OSC exporter with OSCQuery and auto-launch support |
| `TheNexusAvenger/Enigma` | Not studied deeply | Consumer-side export of SteamVR tracker roles into a non-XR client with a companion plugin path |
| `ThatGuyThimo/leapmotion-osc` | Not studied deeply | Finger-only OSC egress utility adjacent to the hand-tracking and avatar-parameter bridge family |

### Consolidation note

This family is the clearest foundation for a future:

- `Tracker Bridge Service`
- `SteamVR/OSC bridge`
- `external sensor -> virtual tracker` platform
- `engine-side role reuse and direct consumer export`

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
| `CrispyPin/ovr-utils` | Partially studied | GitHub snapshot is now mostly a relocation stub, but the lineage still matters for the suite family |
| `mittorn/ovr-utils-dashboard` | Already studied | Godot overlay shell with settings-driven overlay instances and reusable add-ons |
| `artumino/SteamVR_HUDCenter` | Already studied | C# overlay helper and notification library with WinForms or WPF rasterization into VR |
| `LapisGit/LapisOverlay` | Already studied | In-progress overlay-first host with dashboard, wrist surface, and media sidecar split |
| `elvissteinjr/SteamVR-PrimaryDesktopOverlay` | Already studied | Micro-tool that patches SteamVR's existing desktop overlay instead of rendering a new one |
| `Nexz/turncountervr` | Not studied deeply | Rotation counter / cable-awareness overlay node |
| `Martin-Oehler/SteamVR-WebApps` | Already studied | Thin browser-backed dashboard wrappers built on top of `SteamVR-Webkit` |

### Consolidation note

This family should feed a future comparative UX document, not just more
individual project entries. The real overlap axes are:

- `desktop mirror`
- `window portal`
- `wrist/watch controls`
- `dashboard suite`
- `overlay patch micro-tool`
- `Linux vs Windows UX`
- `OpenVR overlay vs OpenXR layer`

## Family 7: Accessibility overlays and assistive HUDs

This family is now clearly large enough to be treated as a first-class product
direction.

| Project | Status | Notes |
|---|---|---|
| `Vinventive/live-captions-vr` | Already studied | Speech-to-text overlay reference |
| `MochiDoesVR/OpenVRCaptions` | Already studied | C#/SteamVR captions reference |
| `ctobin1114/UniversalVR-CC` | Already studied | Browser-first closed-caption surface meant to be pulled into VR through another host |
| `gt0777/VRCLiveCaptionsMod` | Already studied | App-internal live-captions path built around a VRChat voice hook |
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
| `terminal29/Simple-OpenVR-Driver-Tutorial` | Already studied | Best current public learning-path repo for sample-like OpenVR driver structure |
| `ValveSoftware/openvr` tutorial/sample code | Already studied | Foundational reference |
| `ChristophHaag/SteamVR-OpenHMD` | Already studied | OpenHMD hardware bridge into SteamVR/OpenVR |
| `mm0zct/Oculus_Touch_Steam_Link` | Already studied | Mixed-VR controller, tracker, and sensor bridge driver |
| `kodowiec/Yet-Another-OpenVR-IPC-Driver` | Already studied | Named-pipe or Unix-socket bridge driver that spawns synthetic trackers and controllers from external commands |
| `bdub1011/Quest-Link-Hand-Tracking` | Partially studied | Gesture-configurable Quest hand-tracking to SteamVR controller-emulation path whose current public source is thin |
| `mSparks43/PSVR-SteamVR-openHMD` | Not studied deeply | PSVR-specific Linux/OpenHMD comparison node for the mixed-VR bridge family |
| `SlimeVR/SlimeVR-OpenVR-Driver` | Already studied | Modern tracker bridge driver with external service transport |
| `oleuzop/VirtualSteamVRDriver` | Already studied | Virtual HMD driver for no-headset development and testing |
| `finallyfunctional/openvr-driver-example` | Already studied | Beginner-friendly controller/input-emulation driver tutorial |
| `SecondReality/VirtualControllerDriver` | Already studied | Tiny synthetic controller driver for mixed-reality workflows |
| `oneup03/VRto3D` | Already studied | Productized stereo-display and AR-glasses driver that heavily reshapes SteamVR behavior |
| `ValveSoftware/driver_hydra` | Already studied | Official peripheral bridge driver with controller realignment and calibration monitor |
| `alatnet/OpenPSVR` | Already studied | Full PSVR HMD/display driver with monitor detection, power control, display component, and IMU-based tracking |
| `r57zone/OpenVR-driver-for-DIY` | Already studied | Keyboard-driven DIY null-HMD plus controller path built close to the stock sample |
| `gpsnmeajp/SegsVRControllerDriverSample` | Already studied | Controller-driver sample with a shared-memory helper client and JSON payloads |
| `puresoul/Barebone` | Partially studied | XInput-driven synthetic Vive controller path anchored relative to the HMD |
| `mmorselli/Joy2OpenVR` | Already studied | DirectInput-to-InputEmulator sidecar for unusual physical controllers |
| `mdovgialo/SteamVR-Glove` | Already studied | Arduino glove proof of concept piggybacking on existing Vive controller tracking |
| `openvrmc/OpenVR-MotionCompensation` | Already studied | Pose-rewrite driver with shared library and in-VR dashboard configuration |
| `OpenDisplayXR/OpenDisplayXR-VDD` | Not studied deeply | Sparse but relevant signal for a simulated OpenVR/OpenXR virtual hardware path |
| `verncat/RayNeo-Air-3S-Pro-OpenVR` | Already studied | SDK-first RayNeo glasses bridge whose transport and API layer now sit cleanly beside a dedicated driver repo |
| `verncat/RayNeo-Air-3S-Pro-OpenVR-Driver` | Already studied | Dedicated RayNeo OpenVR driver repo with bindings, prelauncher, and clearer device-provider split |
| `LucidVR/opengloves-driver` | Already studied | Hand-specific custom device path with driver, service, and overlay split |
| `LucidVR/lucidgloves` | Already studied | Matching firmware and hardware ecosystem for the same glove family |
| `r57zone/OpenVR-ArduinoHMD` | Partially studied | DIY HMD and config-driven setup |
| `DaniXmir/GlassVr` | Already studied | XR/AR glasses bridge with Python sidecar, headset/controller/tracker emulation, and hand-simulation path |
| `Copprhead/hotas-vr-controller` | Already studied | Domain-specific cockpit/device bridge with config-driven offsets and hook-based clicks |
| `TrueOpenVR/SteamVR-TrueOpenVR` | Partially studied | Sample-derived bridge that feeds SteamVR from an external TrueOpenVR DLL surface |
| `HoboVR-Labs/hobo_vr` | Already studied | Driver prototyping stack with an explicit external poser protocol and language bindings |
| `r57zone/Razer-Hydra-SteamVR-driver` | Already studied | Legacy peripheral bridge with helper monitor and controller-role mapping |

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
| `BnuuySolutions/PSVR2Toolkit` | Already studied | Vendor-driver wrapper with versioned IPC for gaze data and trigger-effect control |
| `BnuuySolutions/PSVR2Toolkit.VRCFT` | Already studied | Downstream consumer module that maps toolkit IPC into VRCFaceTracking semantics |
| `s-ilent/PSVR2ToolkitTriggerConfig` | Already studied | Focused desktop trigger-config utility layered over the toolkit IPC contract |
| `tabithamoon/ResonitePSVR2` | Already studied | Engine-specific eye-tracking bridge that consumes the toolkit IPC surface |
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
| `OSVR/SteamVR-OSVR` | Already studied | Foreign-framework compatibility driver that maps OSVR HMD and tracked-device surfaces into SteamVR |
| `terminal29/OSVR-SteamVR-Bridge` | Already studied | Smaller alias-mapping comparison node for the same OSVR-to-SteamVR bridge family |

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
| `RavenSystem/VRPerfKit_RSF` | Already studied | Practical `vrperfkit` continuation with dynamic modes, hidden radial mask control, and original-DLL chaining |
| `CamelCaseName/OpenVRPerfKit` | Already studied | Backend-expanded fork line that pushes the same family toward `D3D12` and bundled `FSR2` |
| `Granther/foveated-rendering` | Already studied | Dynamic focus-source experiment that currently leans on cursor-driven control more than mature gaze ingestion |
| `mbucchia/Quad-Views-Foveated` | Already studied | Important OpenXR rendering-adaptation layer for quad views and foveation compatibility |
| `mbucchia/OpenXR-Eye-Trackers` | Already studied | Multi-backend eye-gaze adaptation layer that normalizes several foreign sources into OpenXR gaze surfaces |
| `retroluxfilm/reshade-vrtoolkit` | Already studied | VR-first shader bundle for sharpening, color treatment, and other image adjustments |
| `zhukovv/upscale-injection` | Already studied | Generic D3D11 injection and upscaling donor for low-level hook mechanics |

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
| `alexander-clarke/openvr-room-mapping` | Already studied | Pose-plus-image capture pipeline that sits between environment reconstruction and alignment research |

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
| `MuffinTastic/openvr-device-positions` | Already studied | Creator-side pose inventory exporter with dashboard overlay and FBX output path |

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
| `BenWoodford/SteamVR-Webkit` | Already studied | Browser-backed overlay toolkit with JS interop and dual dashboard/in-game surfaces |
| `BenWoodford/OVROverlayManager` | Already studied | Tiny Unity helper that turns render textures and OpenVR events into reusable overlay projectors |
| `beniwtv/vr-streaming-overlay` | Already studied | Godot multi-overlay shell with widget/config split |
| `Nyabsi/steamvr_overlay_vulkan` | Already studied | Modern Vulkan/ImGui overlay template |
| `Hotrian/HeadlessOverlayToolkit` | Already studied | Hidden-window and background-host overlay pattern in Unity |
| `cnlohr/openvr_overlay_model` | Already studied | Experimental stereo-per-eye overlay technique for pseudo-3D content |
| `JoeLudwig/overlay_experiments` | Already studied | Historical browser-backed OpenVR dashboard experiments |
| `artumino/SteamVR_HUDCenter` | Already studied | Older but valuable C# overlay library with notification flow and desktop-UI-backed surfaces |
| `Martin-Oehler/SteamVR-WebApps` | Already studied | Web-app-driven overlay wrappers that demonstrate the thinnest `browser -> dashboard` shell |
| `LapisGit/LapisOverlay` | Already studied | Unity overlay host with dashboard, wrist-surface, and sidecar-fed media panel pattern |
| `KainosSoftwareLtd/VRSceneOverlay` | Already studied | Unity scene-overlay scaffold with tracked helpers and Leap-oriented augmentation |
| `hai-vr/h-view` | Already studied | Modern overlay-first utility host with ImGui rendering, desktop parity, and action-manifest-driven overlay management |
| `vrkit-platform/vrkit-platform` | Partially studied | OpenXR monitor/overlay platform with plugin-manager and native-interop signals that still deserves a narrower future pass |
| `LunarG/OpenXR-Overlays-UE4-Plugin` | Already studied | Tiny Unreal-side reference for injecting `XR_EXTX_overlay` session-create info |
| `mbucchia/_ARCHIVE_OverXR` | Fork / variant only | Current GitHub state is an archive shell with little code to inspect |

### Consolidation note

This family should feed `VR-apps-lab` as a methods donor layer:

- overlay lifecycle references
- graphics-path references
- UI stack references
- host-scene and render-loop scaffolds
- overlay patch helpers
- engine-side overlay extension hooks

## Family 15: SteamVR environment helpers and runtime hygiene tools

These utilities improve the way SteamVR behaves around startup, dashboard
interaction, distortion, or overlay-heavy workflows.

| Project | Status | Notes |
|---|---|---|
| `MuffinTastic/steamvr-exconfig` | Already studied | Backup-safe config patcher for disabling autolaunch apps and always-active drivers before startup |
| `BnuuySolutions/OculusKiller` | Already studied | Vendor-shell replacement that redirects Oculus launch flow into SteamVR |
| `username223/SteamVRNoHeadset` | Already studied | Null-driver and no-HMD recipe for SteamVR workflows |
| `n1ckfg/ViveTrackerExample` | Already studied | Tracker-without-HMD workflow and tiny Unity helper |
| `craftyinsomniac/WFOVFix` | Already studied | Guided SteamVR settings patcher for wide-FOV headsets |
| `BnuuySolutions/SteamVRLinuxFixes` | Already studied | Vulkan-layer and compositor-fix utility for Linux SteamVR |
| `simonowen/dashfix` | Already studied | Dashboard-input fix via SDL hook injection |
| `W-Drew/SteamVR-Toggle` | Already studied | Tray utility that toggles SteamVR by renaming install path |
| `sencercoltu/steamvr-undistort` | Already studied | Lens distortion adjustment tool for custom optics |
| `elvissteinjr/SteamVR-VoidScene` | Already studied | Minimal scene app to lower baseline cost for overlay use |
| `shieldmeidunn/SteamVRNullFlipper` | Already studied | Tiny backup-aware helper for flipping SteamVR into null-driver mode |
| `Virus-vr/SteamVRAdaptiveBrightness` | Already studied | Mirror-texture feedback daemon that continuously rewrites SteamVR brightness |
| `username223/SteamVR-ActionsManifestValidator` | Already studied | CI-friendly manifest linter with explicit warning gates and duplicate-key rejection |
| `Erimelowo/Lighthouse-Scale-Fix` | Already studied | Backup-safe one-shot patcher for lighthouse scale configuration |
| `DavidRisch/steamvr_utils` | Already studied | Linux helper collection with a SteamVR lifecycle daemon, base-station power control, and audio switching |

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

## Family 17: Calibration, motion compensation, and tracking alignment

These projects are unified by one practical problem: helping the user keep
different tracking spaces, poses, or sensors aligned enough to remain usable.

| Project | Status | Notes |
|---|---|---|
| `pushrax/OpenVR-SpaceCalibrator` | Already studied | Foundational mixed-space calibration reference |
| `Stavdel/OpenVR-SpaceCalibrator` | Already studied | Fork line preserved mainly for historical comparison |
| `Marshall-vak/OpenVR-SpaceCalibrator2` | Already studied | Continuous-calibration extension of the SpaceCalibrator idea |
| `BuzzteeBear/OpenXR-MotionCompensation` | Already studied | OpenXR-side motion compensation and calibration flow |
| `openvrmc/OpenVR-MotionCompensation` | Already studied | Driver-side pose rewrite plus dashboard configuration path |
| `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay` | Already studied | Minimal overlay-first 9-point eye-tracking calibration surface |
| `alexander-clarke/openvr-room-mapping` | Already studied | Spatial capture and reconstruction path that overlaps with alignment and room-space research |
| `tobexeon/PSVR2EyeTrackingCalibration` | Not studied deeply | Real-time PSVR2 eye-calibration client that currently depends on a custom toolkit fork |

### Consolidation note

This family matters because the best tracking helper is often not a new sensor
or a new driver, but a better `alignment UX`:

- guided point sequences
- overlay-first feedback
- persistent offsets
- continuous correction
- pose-rewrite layers and drivers
- capture-driven alignment artifacts

## Family 16: Vision-based tracking, hand-input bridges, and headsetless camera runtimes

This family covers repositories that use cameras, computer vision,
hand-tracking services, or foreign runtimes to generate SteamVR devices or
OpenXR substitute inputs without relying on classic lighthouse-tracked
controller stacks.

| Project | Status | Notes |
|---|---|---|
| `ultraleap/driver_ultraleap` | Already studied | Mature hardware-service to SteamVR hand-driver path with optional elbow trackers and a `DebugRequest` external-input hook |
| `Nordskog/HandOfLesser` | Already studied | Quest/OpenXR hand-tracking bridge into SteamVR and VRChat with structured packets plus named-pipe and UDP transport |
| `NovaAshwolfDev/HandCameraDriver` | Already studied | Archived webcam-hand-tracking WIP with a Python-sidecar plus custom SteamVR driver split |
| `KinectToVR/KinectToVR` | Already studied | Legacy multi-process Kinect and PSMove full-body stack with heavy calibration and tracker-orientation math |
| `KinectToVR/Amethyst` | Already studied | Plugin-based body-tracking host with device plugins and service-endpoint contracts |
| `ju1ce/Mediapipe-VR-Fullbody-Tracking` | Already studied | Single-camera body tracking with switchable SteamVR-driver and VRChat OSC backends plus Quest-friendly WebUI |
| `Wunder-Wulfe/NVIDIA-BodyTracking` | Already studied | GPU-assisted camera body-tracking driver with overlay-assisted alignment and dense tracker-role configuration |
| `chnoblouch/aethervr` | Already studied | Webcam-driven custom OpenXR runtime with a Python tracker connected over local TCP |
| `MasonSakai/VR-AI-Full-Body-Tracking` | Not studied deeply | Camera FBT comparison node still partly anchored in an InputEmulator-era transition |

### Consolidation note

This family shows that `vision-driven XR utility design` is now large enough to
split into several repeatable sub-branches:

- `service-backed hand drivers`
- `camera CV sidecars with SteamVR or OSC backends`
- `legacy tracker apps evolving into plugin platforms`
- `headsetless camera runtimes`

The strongest future product concepts suggested by this family are:

- `vision tracking sandbox`
- `driver/backend-agnostic tracking bridge`
- `headsetless camera QA runtime`

## Family 18: Text entry, tracked keyboards, and non-native input surfaces

This family covers the UI surfaces that let a VR utility collect text or short
commands without bouncing the user back to a desktop monitor.

| Project | Status | Notes |
|---|---|---|
| `campfireunion/VRKeys` | Already studied | Focused drum-style keyboard with validation-aware lifecycle, layout switching, and hand-attached mallets |
| `ultraleap/XR-Keyboard` | Already studied | Physical keyboard generator with prefab, manager, and keymap split |
| `oculus-samples/Unity-TrackedKeyboard` | Already studied | Tracked hardware keyboard sample with hand-proximity reveal and MR desk context |
| `Ayfel/MRTK-Keyboard` | Already studied | Semantic non-native keyboard with multiple layout modes and host-facing callbacks |
| `RTUITLab/Oculus-HandTracking-Keyboard` | Already studied | Lightweight fingertip-driven hand-tracking keyboard experiment |

### Consolidation note

This family matters because `text entry` is one of the fastest ways a VR tool
falls back to a desktop if the UX is not handled deliberately.

It suggests a separate donor branch inside `VR-apps-lab`:

- setup and configuration keyboards
- overlay-side text entry
- mixed-reality desk-aware typing
- semantic non-native keyboard components

## Family 19: Hand, palm, radial, and quick-access menus

This family covers the fast-launch and quick-selection surfaces that make VR
tools feel usable without a large persistent desktop metaphor.

| Project | Status | Notes |
|---|---|---|
| `NovaUI-Unity/XRHandMenuSample` | Already studied | Palm-up launcher that opens richer panels at a detached popup anchor |
| `Housz/VRMenuDesigner` | Already studied | Menu-archetype toolkit spanning default, radial, ring, and editor-side modifiers |
| `Oyshoboy/RadialMenuVR` | Already studied | Minimal radial-selection donor with hover scaling and auto-hide |
| `yusufalibrahim1994/UnityXR-Physicalized-Radial-Menu` | Already studied | Radial selection that resolves into real interactables in the hand |
| `auroreRakoto/XR-UI-Prototype` | Already studied | Small menu-list to contextual secondary-panel comparison node |

### Consolidation note

This family points toward a strong `quick-access shell` branch inside
`VR-apps-lab`:

- palm launchers
- radial selectors
- contextual detail panels
- menu archetypes that can be reused across utilities

## Family 20: Spatial UI interaction frameworks and input stacks

This family is less about one finished menu and more about the lower-level
plumbing that makes ordinary UI surfaces usable in XR.

| Project | Status | Notes |
|---|---|---|
| `Unity-Technologies/XR-Interaction-Toolkit-Examples` | Already studied | Broad baseline for spatial keyboard, 2D UI, 3D UI, gaze, and toolkit-scale interaction samples |
| `microsoft/MixedRealityToolkit-Unity` | Already studied | Legacy but still strong solver-driven hand-menu and prefab-UI donor |
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | Not studied deeply | Current-generation MRTK continuation that deserves its own later pass |
| `ViveSoftware/ViveInputUtility-Unity` | Already studied | VR-aware 3D pointer and custom EventSystem input-module donor |
| `Unity-Technologies/mr-example-meta-openxr` | Already studied | Modern Meta/OpenXR sample stack for hand-menu, gesture, and spatial-panel flows |

### Consolidation note

This family matters because many future `VR-apps-lab` tools will not need a new
menu idea as much as they will need a clean `input and UI substrate`.

It strengthens a framework-donor layer around:

- UI EventSystem adaptation
- ray, poke, and hand-input routing
- palm and gesture gating
- toolkit-side keyboard and panel scaffolds

## Family 21: Teleoperation workspaces and embodied control surfaces

This family covers VR applications that behave like control rooms, operator
stations, or embodied dashboards for external systems.

| Project | Status | Notes |
|---|---|---|
| `leggedrobotics/unity_ros_teleoperation` | Already studied | Palm-menu teleoperation shell with ROS-state surfaces and subsystem toggles |
| `h2r/ros_reality` | Already studied | Semantic action-menu reference over a websocket bridge |
| `elpis-lab/UR10_Teleop` | Already studied | Thin controller-pose exporter to an external robot-control process |
| `pollen-robotics/ReachyTeleoperation` | Already studied | Strong staged teleoperation product with connection, mirror, and live-control rooms |
| `nakama-lab/VR_Teleop_Interface` | Not studied deeply | Architectural comparison node for broader teleoperation interface decomposition |
| `h2r/GHOST` | Not studied deeply | Adjacent visualization and gesture-control node worth later comparison |

### Consolidation note

This family matters because it shows a wider product branch than ordinary
utility overlays:

- VR control-room shells
- side-panel and palm-menu command surfaces
- staged setup-to-operation room flows
- thin VR frontends that hand control to an external process

## Family 22: Social overlays, communication sidecars, and companion surfaces

This family covers repositories where the core value is not a generic dashboard
but an ongoing social, speech, or communication workflow that can feed VR
through overlays, `OSC`, `WebSocket`, or desktop companion surfaces.

| Project | Status | Notes |
|---|---|---|
| `designeerlabs/discord-vr` | Already studied | Browser-automation sidecar that turns Discord voice presence into a prefab-driven OpenVR overlay |
| `kittynXR/VRCattoChatto` | Already studied | Desktop-native chat companion with Twitch plus OSC outputs and persisted broadcaster/auth state |
| `Wolf-G88/vrchat-proximity-app` | Already studied | Service-first proximity sidecar with OSC transport and optional SteamVR overlay controls |
| `Sharrnah/whispering` | Partially studied | Broad local speech platform whose VR value comes from OSC and websocket fan-out rather than a single overlay |
| `Hotrian/OpenVRTwitchChat` | Already studied | Twitch-chat overlay reference with a stronger in-headset presentation bias |
| `MeroFune/GOpy` | Not studied deeply | Smaller integration-helper comparison node that may still add another desktop-to-VR communication angle |
| `I5UCC/VRCTextboxSTT` | Already studied | Local speech-to-text helper where the SteamVR overlay is one output surface among others |
| `gt0777/VRCLiveCaptionsMod` | Already studied | App-internal speech surface comparison node from the accessibility and social boundary |
| `rrazgriz/VRCMicOverlay` | Already studied | Minimal status-overlay node for avatar-facing communication state |

### Consolidation note

This family matters because it shows that `communication tooling` is its own VR
utility branch, not just an accessibility afterthought:

- social-presence overlays
- desktop-native chat companions
- service-first speech utilities
- VRChat-facing sidecars with optional overlay control surfaces

## Family 23: Alternative OpenXR runtimes, special-display paths, and platform experiments

This family covers runtime implementations that target nontraditional hardware,
embedded platform contexts, or proof-of-concept runtime architectures rather
than ordinary HMD-first desktop setups.

| Project | Status | Notes |
|---|---|---|
| `DisplayXR/displayxr-runtime` | Already studied | Clean layered runtime architecture for spatial displays and 3D monitors |
| `JoeyAnthony/XRGameBridge` | Already studied | Focused runtime wrapper for UEVR-style game flows on special displays |
| `warrenm/OpenXRKit` | Already studied | Embedded Apple-platform OpenXR runtime framework with platform-specific system implementations |
| `rinsuki/FruitXR` | Already studied | Local IPC and runtime-server proof-of-concept for macOS |
| `maximum-game-22/openxr-3d-display` | Not studied deeply | Monado-derived spatial-display comparison node |
| `Kartaverse/OpenDisplayXR` | Not studied deeply | Project cluster around OpenXR paths for nonstandard displays |
| `chnoblouch/aethervr` | Already studied | Webcam-driven custom OpenXR runtime that reinforces the broader nonstandard-runtime branch |

### Consolidation note

This family matters because it expands `runtime research` beyond switchers and
layers into `runtime ownership for nontraditional targets`:

- special-display runtimes
- embedded platform runtimes
- local IPC runtime experiments
- custom runtimes that are better understood as architecture donors than as products

## Family 24: Tracked-device geometry, CAD, and auxiliary tracker tooling

This family covers the point where tracked-device design becomes an explicit
engineering workflow rather than only a pose-ingestion problem.

| Project | Status | Notes |
|---|---|---|
| `fughilli/ViveTrackedDevice` | Partially studied | Documentation-first reverse-engineering donor for Lighthouse-tracked device internals |
| `TriadSemi/Fusion360_SteamVR_Json` | Already studied | CAD-authored path from construction geometry to SteamVR tracking JSON |
| `aughip/augmented-hip` | Already studied | Derived waist-tracker driver built from existing tracked body nodes |
| `m9cd0n9ld/IMU-VR-Full-Body-Tracker` | Already studied | Full-stack DIY tracker ecosystem spanning firmware, desktop tooling, and driver registration |
| `ebadier/ViveTrackers` | Not studied deeply | Unity-side consumer node for Vive tracker hardware data |
| `choyai/SteamVRTrackerUtility` | Already studied | Narrow tracker-identity and serial helper for deterministic role workflows |
| `jangxx/UniversalTrackerMarkers` | Already studied | Marker and identity helper that reinforces the auxiliary tracker-tooling side of the family |

### Consolidation note

This family matters because `tracked-device work` is not only about network
bridges:

- reverse-engineered device geometry
- CAD authoring for sensor definitions
- derived or synthetic role devices
- auxiliary tracker identity and hardware workflows

## Family 25: Expressive tracking, face and eye input, and avatar-facing bridges

This family covers the branches where the input is not only a body pose but a
more expressive face, eye, hand, or avatar-facing signal that must be adapted
into SteamVR, OpenXR, or avatar-consumer surfaces.

| Project | Status | Notes |
|---|---|---|
| `Project-Babble/Baballonia` | Already studied | Cross-platform expressive-tracking host with overlay-assisted calibration and modular capture sources |
| `jcorvinus/HandshakeVR` | Already studied | Hand-provider remapping layer that normalizes incompatible input models |
| `moshimeow/mercury_steamvr_driver` | Already studied | SteamVR hand-driver path built around an out-of-process tracking source |
| `BattleAxeVR/PSVR2_OpenXR_Eye_Tracking` | Already studied | Vendor-specific gaze source translated into standard OpenXR layer surfaces |
| `Nordskog/HandOfLesser` | Already studied | Quest or OpenXR hand-tracking bridge into SteamVR and avatar-facing consumers |
| `mbucchia/OpenXR-Eye-Trackers` | Already studied | OpenXR-side gaze and eye-tracking adaptation donor |
| `pembem22/etvr-openxr-layer` | Already studied | OSC eye-tracking to OpenXR gaze adaptation path |
| `ThatGuyThimo/leapmotion-osc` | Not studied deeply | Finger-only avatar-facing OSC output comparison node |
| `takana-v/quest_steamvr_fbt_tool` | Not studied deeply | Quest-derived body state and avatar-facing export follow-up node |

### Consolidation note

This family matters because it pulls together several adaptation layers that
would otherwise look unrelated:

- overlay-assisted expressive calibration
- hand-provider remapping
- driver plus subprocess expressive input
- vendor-specific gaze adaptation into standard XR surfaces
- avatar-facing exports built on top of those richer inputs

## Recommended synthesis path for `VR-apps-lab`

The next useful step is not another long unsorted list.

It is:

1. build product concepts around `families`, not repos;
2. prioritize deep dives where status is `Partially studied` or
   `Not studied deeply`;
3. keep forks/variants as comparison nodes instead of promoting each one to a
   full standalone research wave.
