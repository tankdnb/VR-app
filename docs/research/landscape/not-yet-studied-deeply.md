# Not Yet Studied Deeply

- Date: `2026-04-19`
- Goal: keep a prioritized list of repositories that either:
  - are not yet represented in `VR-apps-lab`;
  - are only lightly covered;
  - or belong to a high-value overlap family that deserves a deeper code-level
    pass.

## How to use this file

For each project, track four things:

- `interesting idea`
- `code donor value`
- `product reference value`
- `what to inspect next`

This keeps the backlog aligned with the existing wave documents and makes it
easier to decide whether the next pass should focus on architecture, UX, or
implementation details.

## Priority batch A

These are the strongest next candidates.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `BnuuySolutions/PSVR2Toolkit` | Partially studied | Vendor-enhancement layer over an official headset stack | Medium | High | IPC layout, developer API surface, driver patch boundaries |
| `MuffinTastic/steamvr-exconfig` | Partially studied | Pre-launch SteamVR config utility with narrow focus | Medium | High | SteamVR settings model, disabled overlay/driver flow, restart assumptions |
| `John-Dean/OpenVR-Tracker-Websocket-Driver` | Partially studied | WebSocket-native tracker spawning and pose exchange | High | High | Message protocol, tracker lifecycle, read/write API, driver/service split |
| `surplex-io/OpenVR-Driver` | Partially studied | Alternative evolution of websocket tracker driver architecture | High | Medium | Delta versus upstream, protocol changes, maintainability improvements |
| `gpsnmeajp/VirtualMotionTracker` | Partially studied | External pose and skeletal input into virtual SteamVR trackers | High | High | Driver-manager boundary, OSC transport, skeletal input path |
| `LucidVR/opengloves-driver` | Partially studied | Hand-specific custom device integration with multiple transports | High | Medium | Serial/named-pipe/Bluetooth transport handling, device abstraction |
| `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay` | Partially studied | Overlay-first calibration UX for eye tracking | Medium | High | 9-point flow, calibration state machine, input/feedback UX |
| `DaniXmir/GlassVr` | Partially studied | Bridge non-VR glasses hardware into SteamVR via emulation | High | High | Headset/controller/tracker emulation boundaries, hand-tracking path |
| `krazysh01/VirtualDesktop-OpenVR-Trackers` | Partially studied | Turn body-state data from another ecosystem into trackers | High | Medium | Data format, tracker role mapping, assumptions about upstream source |
| `terminal29/Simple-OpenVR-Driver-Tutorial` | Partially studied | Clean learning path for driver architecture | High | Low | Minimal driver bootstrap, lifecycle, where real projects diverge |
| `jangxx/openvr-battery-monitoring` | Not studied deeply | Battery-specific overlay/monitor pattern | Medium | Medium | Notification model, sampling strategy, whether it logs or only displays |
| `BarakChamo/OpenVR-OSC` | Not studied deeply | OSC bridge family comparison node | Medium | Medium | Event model, pose/input scope, VRChat/general automation fit |
| `PlutoVR/OpenXR-OverlayLayer-1` | Not studied deeply | Another OpenXR overlay-layer experiment | High | Medium | Overlay-layer architecture, host/client split, runtime assumptions |

## Priority batch B: comparison variants and forks

These are worth keeping visible, but they should usually be studied after the
main upstream or main family representative is understood.

| Project | Why it matters | What to inspect next |
|---|---|---|
| `3NekoSystem/OpenVR-Tracker-Websocket-Driver` | Fork/variant in tracker-driver family | Compare protocol and maintenance differences from the main WebSocket driver line |
| `v0xie/OpenVR-Tracker-Websocket-Driver` | Fork/variant in tracker-driver family | Determine whether it adds meaningful tracker or control features |
| `mutr/openvr_battery_monitor` | Battery-monitor family comparison node | Check whether it focuses on overlay, tray, or logging behavior |
| `TrueOpenVR/SteamVR-TrueOpenVR` | Custom driver/device learning path | Identify whether it is a teaching repo, compatibility shim, or device emulator |

## Priority batch C: newly discovered GitHub wave candidates

These were discovered in the latest GitHub source pass and added to the
registry, but not yet studied deeply enough to promote beyond `Not studied
deeply`.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `KainosSoftwareLtd/VRSceneOverlay` | Not studied deeply | Unity scene-overlay implementation sample | Medium | Medium | Overlay bootstrap, scene composition, Unity package layout |
| `artumino/SteamVR_HUDCenter` | Not studied deeply | HUD-centering micro-tool | Low | Medium | Transform logic and comfort UX |
| `LapisGit/LapisOverlay` | Not studied deeply | Multi-purpose overlay shell in progress | Medium | Medium | Panel model, settings, interaction approach |
| `elvissteinjr/SteamVR-PrimaryDesktopOverlay` | Not studied deeply | Focused primary-desktop crop overlay | Medium | Medium | Desktop crop logic, overlay bounds, startup model |
| `Nexz/turncountervr` | Not studied deeply | Rotation/cable-awareness overlay variant | Low | Medium | Counter logic, world-space placement, comfort framing |
| `vrkit-platform/vrkit-platform` | Not studied deeply | OpenXR monitor and overlay platform | High | High | Platform boundaries, monitor surfaces, runtime assumptions |
| `LunarG/OpenXR-Overlays-UE4-Plugin` | Not studied deeply | Engine-side route into OpenXR overlay support | Medium | Medium | Unreal integration boundary and extension assumptions |
| `KaftanOS/SteamVR-Battery-Checker` | Not studied deeply | Charging-state battery micro-helper | Low | Medium | Charging workflow, UX scale, whether it is tray or CLI driven |
| `DavidRisch/steamvr_utils` | Not studied deeply | Linux-side SteamVR helper collection | Medium | Medium | Which utilities are included and how they are packaged |
| `choyai/SteamVRTrackerUtility` | Not studied deeply | Tracker wake/role helper | Medium | Medium | Tracker management flow, role mapping, power handling |
| `mbucchia/_ARCHIVE_OverXR` | Fork / variant only | Archive shell pointing to a once-promising overlay compatibility idea | Low | Medium | Whether useful code exists in releases, tags, or external mirrors |

## Priority batch D: Wave 9 follow-up candidates

These were discovered during the Wave 9 source pass, added to the registry, and
kept for the next deeper inspection round.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `Ybalrid/OpenXR-Runtime-Manager` | Not studied deeply | Yet another runtime-manager implementation with a likely different UX and detection model | Medium | High | Runtime discovery logic, registry handling, layer-awareness, UX differences versus `xr-picker` and other switchers |
| `clear-xr/clearxr-server` | Not studied deeply | Runtime-side or service-side XR infrastructure that may broaden the runtime-intelligence family | Medium | Medium | Determine actual scope, runtime/service boundary, and whether it fits doctor/monitor tooling or a different family |
| `pembem22/etvr-openxr-layer` | Not studied deeply | Niche OpenXR layer candidate that may expose uncommon integration patterns | Medium | Medium | Layer bootstrap, extension assumptions, how it differs from generic OpenXR layer templates |
| `Martin-Oehler/SteamVR-WebApps` | Not studied deeply | Web-app-centric SteamVR overlay direction | Medium | Medium | Browser/runtime integration model, overlay-host architecture, security and maintenance tradeoffs |
| `I5UCC/ParameterSaveStates` | Not studied deeply | VRChat or control-surface state management that may complement remote-control overlays | Medium | Medium | State model, persistence approach, OSC or app-integration flow, overlap with `SteaMeeter` |
| `Denwa/vive-wireless-info-overlay` | Not studied deeply | Micro-overlay focused on wireless headset/link diagnostics | Low | Medium | Data source, polling cadence, narrow-device UX, whether it generalizes into device-health overlays |
| `hai-vr/h-view` | Not studied deeply | Specialized utility/control surface in the broader remote-control overlay family | Medium | Medium | Feature boundaries, external integration points, whether it is a dashboard or helper service |
| `MeroFune/GOpy` | Not studied deeply | Experimental integration helper that may add a new desktop-to-VR bridge angle | Medium | Low | Actual problem scope, packaging model, and whether it contributes reusable bridge patterns |
| `biosmanager/unity-openvr-tracking` | Not studied deeply | Unity-side helper for pulling OpenVR tracking into engine code | Medium | Medium | Tracking abstraction, device-role handling, and whether it belongs in the tracker-bridge learning path |
| `MuffinTastic/openvr-device-positions` | Not studied deeply | Narrow device-position inspection helper | Medium | Medium | Pose enumeration model, output surface, diagnostic usefulness, overlap with `triad_openvr` and device monitors |

## Priority batch E: Wave 10 follow-up candidates

These were discovered during the Wave 10 source pass, or identified as the
next comparison nodes after the new code-level study.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `alexander-clarke/openvr-room-mapping` | Not studied deeply | Spatial and room-mapping angle adjacent to passthrough and environment-capture research | Medium | Medium | Mapping method, output artifacts, whether it belongs closer to calibration, passthrough, or creator-tool families |

## Priority batch F: Wave 11 follow-up candidates

These were surfaced or only partially exhausted during the Wave 11 source pass.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `1runeberg/OpenXRProvider` | Partially studied | Library plus sandbox wrapper around raw OpenXR bring-up | High | Medium | Input profiles, extension wrappers, sandbox render loop, and where the wrapper surface stops abstracting raw OpenXR |
| `OpenDisplayXR/OpenDisplayXR-VDD` | Not studied deeply | Simulated OpenVR/OpenXR virtual hardware driver path | Medium | Medium | Wait for stronger source/docs, then compare with `virtual_display`, `Virtual-Display-Driver`, and `VRto3D` |

## Priority batch G: Wave 12 follow-up candidates

These were surfaced or only partially exhausted during the Wave 12 source pass.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `alatnet/OpenPSVR` | Partially studied | Full PSVR HMD/display driver with embedded sensor fusion and SteamVR packaging | High | High | Controller path, camera ambitions, installer/register flow, and calibration quality |
| `openvrmc/OpenVR-MotionCompensation` | Partially studied | Pose-rewrite driver with separate library and in-VR dashboard | High | High | Hook insertion points, calibration model, overlay/lib coordination, and comparison with OpenXR-side motion compensation |
| `puresoul/Barebone` | Partially studied | HMD-relative synthetic Vive controllers driven by XInput | High | Medium | Driver/helper-app split, offset persistence, and long-term maintainability of the repo cluster |
| `verncat/RayNeo-Air-3S-Pro-OpenVR` | Not studied deeply | Early AR-glasses/OpenVR bridge signal | Medium | Medium | Determine whether it grows into a true OpenVR driver path or stays as device SDK scaffolding |

## Family-level gaps that now deserve deeper passes

These are larger than a single repo and should guide the next research wave.

### 1. `Vendor enhancement tooling`

- Main entry: `PSVR2Toolkit`
- Why it matters:
  shows how to augment an official VR stack without fully replacing it.

### 2. `WebSocket-native tracker drivers`

- Main entries:
  `OpenVR-Tracker-Websocket-Driver`, `OpenVR-Driver`
- Why it matters:
  strongest path toward a future `Tracker Bridge Service`.

### 3. `Virtual tracker / OSC platform`

- Main entries:
  `VirtualMotionTracker`, `SteamVR_To_OSC`, `OpenVR2OSC`, `OpenVR-OSC`
- Why it matters:
  turns many scattered utility ideas into one coherent architecture category.

### 4. `Accessibility overlay family`

- Main entries:
  `OpenVRCaptions`, `live-captions-vr`, notification overlays
- Why it matters:
  already proven as a repeatable utility class, not a one-off experiment.

### 5. `Low-level driver learning path`

- Main entries:
  `Simple-OpenVR-Driver-Tutorial`, `opengloves-driver`, `GlassVr`,
  `OpenVR-ArduinoHMD`
- Why it matters:
  the repository has enough device-side references now to justify a dedicated
  learning track.

### 6. `Overlay implementation references and templates`

- Main entries:
  `VROverlay`, `SteamVR-Webkit`, `vr-streaming-overlay`,
  `steamvr_overlay_vulkan`, `VRSceneOverlay`
- Why it matters:
  this is where `VR-apps-lab` can learn concrete overlay construction techniques
  across Unity, Godot, C#, and modern native C++.

### 7. `SteamVR environment helpers and runtime hygiene tools`

- Main entries:
  `dashfix`, `SteamVR-Toggle`, `steamvr-undistort`, `SteamVR-VoidScene`,
  `steamvr-exconfig`
- Why it matters:
  these tools solve real VR pain points without being traditional overlays,
  which makes them especially useful for future `desktop companion` modules.

### 8. `Headsetless and no-HMD development workflows`

- Main entries:
  `SteamVRNoHeadset`, `ViveTrackerExample`, `VirtualSteamVRDriver`,
  `OpenXR-Simulator`
- Why it matters:
  this family turns scattered setup tricks into a real development and testing
  strategy for VR tooling without physical hardware.

### 9. `Mixed-VR controller and tracker bridges`

- Main entries:
  `Oculus_Touch_Steam_Link`, `SteamVR-OpenHMD`,
  `SlimeVR-OpenVR-Driver`
- Why it matters:
  this is one of the strongest architectural zones for turning foreign
  runtimes, services, or hardware stacks into usable SteamVR devices.

### 10. `Runtime adapters and graphics interop`

- Main entries:
  `OpenXR-Vk-D3D12`, `VirtualDesktop-OpenXR`, `OpenComposite`, `xrizer`
- Why it matters:
  these projects show how to bridge graphics and runtime expectations, not
  just how to switch runtimes or patch settings around them.

### 11. `Virtual display and repurposed output workflows`

- Main entries:
  `virtual_display`, `VRto3D`, `Virtual-Display-Driver`,
  `OpenDisplayXR-VDD`
- Why it matters:
  this family turns XR compositor output into creator, stereo-display, AR
  glasses, or simulated-hardware workflows.

### 12. `Validation and workflow micro-utilities`

- Main entries:
  `SteamVR-ActionsManifestValidator`, `Lighthouse-Scale-Fix`,
  `SteamVRAdaptiveBrightness`, `steamvr-exconfig`, `WFOVFix`
- Why it matters:
  these tiny tools solve real setup and workflow pain without needing to grow
  into full dashboard suites.

## Recommended next move

If `VR-apps-lab` continues this research, the next most valuable deep-pass order is:

1. `WebSocket tracker drivers`
2. `VirtualMotionTracker and OSC bridge family`
3. `PSVR2Toolkit / vendor enhancement path`
4. `Accessibility overlays`
5. `Low-level driver tutorial and custom-device plumbing`
6. `Overlay implementation references`
7. `SteamVR environment helpers`
8. `Headsetless and no-HMD development workflows`
9. `Mixed-VR controller and tracker bridges`
10. `Runtime adapters and graphics interop`
11. `Virtual display and repurposed output workflows`
12. `Validation and workflow micro-utilities`
