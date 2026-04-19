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
| `clear-xr/clearxr-server` | Partially studied | Runtime-side service host that mixes UI shell, registration helpers, streaming orchestration, and an OpenXR API layer | High | High | Keep the next pass narrow: runtime registration, layer boundaries, and service ownership instead of the full streaming platform |
| `hai-vr/h-view` | Partially studied | Overlay-first utility host with desktop parity, ImGui rendering, and broader OSCQuery or hardware-tooling scope | High | High | Inspect the non-overlay boundaries next: OSCQuery, hardware inventory, OCR, external-service integration, and true product scope |
| `puresoul/Barebone` | Partially studied | HMD-relative synthetic Vive controllers driven by XInput | High | Medium | Driver/helper-app split, offset persistence, and long-term maintainability of the repo cluster |
| `krazysh01/VirtualDesktop-OpenVR-Trackers` | Partially studied | Product direction suggests body-state-to-tracker bridging, but the current public snapshot looks much thinner than expected | Medium | Medium | Re-check only if the public repo grows a real data-ingress surface or visible tracker-role mapping logic |
| `BattleAxeVR/PSVR2_OpenXR_Eye_Tracking` | Not studied deeply | PSVR2-specific OpenXR eye-tracking path that may overlap with broader gaze-layer tooling | Medium | Medium | Compare its backend assumptions, extension surface, and donor value against `OpenXR-Eye-Trackers` and `PSVR2Toolkit` |

## Priority batch B: comparison variants and forks

These are worth keeping visible, but they should usually be studied after the
main upstream or main family representative is understood.

| Project | Why it matters | What to inspect next |
|---|---|---|
| `surplex-io/OpenVR-Driver` | Variant of the John-Dean WebSocket tracker-driver line | Revisit only if the fork diverges materially beyond tracker-role mapping or becomes the better-maintained branch |
| `3NekoSystem/OpenVR-Tracker-Websocket-Driver` | Simpler JSON/WebSocket fork in the tracker-driver family | Revisit only if the lighter `8082` branch becomes the better-maintained ingress baseline |
| `v0xie/OpenVR-Tracker-Websocket-Driver` | Near-mirror of the John-Dean WebSocket line with extra web-service surfaces | Revisit only if its HTTP/HTTPS side channels become a clearly reused product pattern |
| `TrueOpenVR/SteamVR-TrueOpenVR` | Sample-derived bridge driver that still depends on an external TrueOpenVR data surface | Revisit only if the public bridge contract or DLL-side standard becomes easier to map in source form |

## Priority batch C: newly discovered GitHub wave candidates

These were discovered in the latest GitHub source pass and added to the
registry, but not yet studied deeply enough to promote beyond `Not studied
deeply`.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `Nexz/turncountervr` | Not studied deeply | Rotation/cable-awareness overlay variant | Low | Medium | Counter logic, world-space placement, comfort framing |
| `vrkit-platform/vrkit-platform` | Not studied deeply | Domain-specific OpenXR overlay platform with plugin-manifest and monitor-surface signals | High | High | Narrow the pass to plugin manifests, overlay component model, and actual OpenXR layer or runtime boundaries |
| `Denwa/vive-wireless-info-overlay` | Not studied deeply | Device-specific thermal micro-overlay with very focused user value | Low | Medium | Revisit only if fuller source appears; the product framing is clearer than the current donor surface |
| `mbucchia/_ARCHIVE_OverXR` | Fork / variant only | Archive shell pointing to a once-promising overlay compatibility idea | Low | Medium | Whether useful code exists in releases, tags, or external mirrors |

## Priority batch D: Wave 9 follow-up candidates

These were discovered during the Wave 9 source pass, added to the registry, and
kept for the next deeper inspection round.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `I5UCC/ParameterSaveStates` | Not studied deeply | VRChat or control-surface state management that may complement remote-control overlays | Medium | Medium | State model, persistence approach, OSC or app-integration flow, overlap with `SteaMeeter` |
| `MeroFune/GOpy` | Not studied deeply | Experimental integration helper that may add a new desktop-to-VR bridge angle | Medium | Low | Actual problem scope, packaging model, and whether it contributes reusable bridge patterns |

## Priority batch E: Wave 11 follow-up candidates

These were surfaced or only partially exhausted during the Wave 11 source pass.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `OpenDisplayXR/OpenDisplayXR-VDD` | Not studied deeply | Simulated OpenVR/OpenXR virtual hardware driver path | Medium | Medium | Wait for stronger source/docs, then compare with `virtual_display`, `Virtual-Display-Driver`, and `VRto3D` |

## Priority batch F: Wave 13 follow-up candidates

These were surfaced or only partially exhausted during the Wave 13 source pass.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `MasonSakai/VR-AI-Full-Body-Tracking` | Not studied deeply | Camera FBT path that still carries InputEmulator-era assumptions while aiming at a cleaner driver rewrite | Medium | Medium | Whether the rewrite lands, how much of the current repo is reusable, and how it compares with `Mediapipe-VR-Fullbody-Tracking` |

## Priority batch G: foundational retro-normalization follow-up candidates

These were clarified during the foundational `waves 1-7` normalization pass and
should remain visible as the next honest follow-ups from the older corpus.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `CrispyPin/ovr-utils` | Partially studied | Early utility-suite lineage whose GitHub mirror no longer contains the real implementation source | Low-Medium | Medium | Follow the current non-GitHub upstream, determine whether the live code still matters, and compare it with `ovr-utils-dashboard` plus `openvr_widgets` |

## Priority batch H: Wave 14 follow-up candidates

These were surfaced during the Wave 14 source pass, or clarified as the next
honest follow-ups from the tracker-ingress and OSC-export family.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `TheNexusAvenger/Enigma` | Not studied deeply | Consumer-side export of SteamVR tracker roles into a non-XR client with a companion plugin path | Medium | Medium | Clipboard and companion-plugin transport, tracker-role mapping, and whether the pattern generalizes beyond Roblox |
| `ThatGuyThimo/leapmotion-osc` | Not studied deeply | Finger-only OSC export that complements SteamVR hand-tracking stacks | Medium | Medium | Avatar parameter model, OSC send cadence, and whether it teaches anything beyond `VRCThumbParamsOSC` |

## Priority batch I: Waves 20-21 surfaced follow-up candidates

These were surfaced while deepening the rendering-mod and OpenXR gaze-layer
families, but they were intentionally kept out of the core shortlist until the
stronger mainline donors were fully integrated.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `LordOfDragons/openxr_oscclient` | Not studied deeply | Thin OSC-to-OpenXR signal bridge hinting at a lighter runtime-side adaptation path | Medium | Medium | Inspect extension boundary, OSC transport model, and whether it complements or duplicates the broader OpenXR gaze-layer family |

## Priority batch J: Waves 24-27 surfaced follow-up candidates

These were surfaced while strengthening the accessibility, headsetless QA,
vendor IPC, and alignment families, but they were intentionally kept as honest
follow-up nodes instead of being over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `davidrios/openxr-device-simulator` | Not studied deeply | Rust-based runtime simulator that hints at a leaner fake-device path | Medium | Medium | Inspect the rest of the runtime surface, input model, and whether it grows into a stronger simulator comparison node |
| `tobexeon/PSVR2EyeTrackingCalibration` | Not studied deeply | Real-time PSVR2 eye-calibration client with no runtime restart requirement | Medium | Medium | Separate the reusable calibration UX from the custom-fork dependency and compare it with broader PSVR2 eye-tracking work |

## Priority batch K: Waves 28-31 surfaced follow-up candidates

These were surfaced while deepening VR keyboard, menu, framework, and
teleoperation families, but they were intentionally kept as honest follow-up
nodes instead of being over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | Not studied deeply | Current-generation continuation of the MRTK spatial-UI line, which may clarify how palm-menu, keyboard, and solver ideas evolved after the legacy repo | High | High | Inspect package split, successor UI primitives, and whether the modern line still exposes the same reusable menu and keyboard donors |
| `nakama-lab/VR_Teleop_Interface` | Not studied deeply | Teleoperation stack whose architectural decomposition may matter more than any single widget | Medium | Medium-high | Inspect non-main branches, scene structure, and transport boundaries to see whether it is a better system-design donor than a UI donor |
| `h2r/GHOST` | Not studied deeply | Visualization-rich teleoperation sidecar with point-cloud and gesture-control overlap | Medium | Medium-high | Inspect visualization pipeline, gesture boundary, and how tightly it couples to `ros_reality` |

## Family-level gaps that now deserve deeper passes

These are larger than a single repo and should guide the next research wave.

### 1. `Virtual tracker / OSC platform`

- Main entries:
  `VirtualMotionTracker`, `SteamVR_To_OSC`, `OpenVR2OSC`, `OpenVR-OSC`,
  `VRCThumbParamsOSC`, `axis-vrc-osc-bridge`
- Why it matters:
  this is still one of the strongest product directions in the whole repo, and
  it now spans both `SteamVR-centric export` and `direct OSC consumer` flows.

### 2. `Overlay implementation references and overlay-first hosts`

- Main entries:
  `VROverlay`, `SteamVR-Webkit`, `SteamVR_HUDCenter`, `SteamVR-WebApps`,
  `OVROverlayManager`, `LapisOverlay`, `h-view`, `VRSceneOverlay`
- Why it matters:
  this remains the clearest place to compare `scene-overlay scaffolds`,
  `desktop UI rasterization bridges`, `overlay-first hosts`, and
  `micro-overlay patches` as distinct construction strategies.

### 3. `Runtime-side service hosts and broader OpenXR utility platforms`

- Main entries:
  `clearxr-server`, `vrkit-platform`, `openxr-explorer`,
  `OpenXR-API-Layers-GUI`
- Why it matters:
  the repo now has many small OpenXR tools, but it still needs a stronger pass
  on the larger `runtime utility platform` end of that family.

### 4. `Mixed-VR controller and tracker bridges`

- Main entries:
  `Oculus_Touch_Steam_Link`, `SteamVR-OpenHMD`,
  `SlimeVR-OpenVR-Driver`, `VirtualDesktop-OpenVR-Trackers`
- Why it matters:
  this remains one of the richest zones for turning foreign runtimes, services,
  or hardware stacks into usable SteamVR devices.

### 5. `Low-level driver tutorial and custom-device plumbing`

- Main entries:
  `Simple-OpenVR-Driver-Tutorial`, `Barebone`, `OpenVR-ArduinoHMD`,
  `SteamVR-TrueOpenVR`
- Why it matters:
  the mainline donors are now strong enough that the remaining value is in
  thinner comparison nodes and more explicit learning-path synthesis.

### 6. `Virtual display and repurposed output workflows`

- Main entries:
  `virtual_display`, `VRto3D`, `Virtual-Display-Driver`,
  `OpenDisplayXR-VDD`
- Why it matters:
  this family keeps pointing toward glasses, creator, and simulated-hardware
  workflows that do not fit neatly into ordinary overlay buckets.

### 7. `Vision-based hand and body tracking bridges`

- Main entries:
  `driver_ultraleap`, `HandOfLesser`, `Mediapipe-VR-Fullbody-Tracking`,
  `NVIDIA-BodyTracking`, `VR-AI-Full-Body-Tracking`
- Why it matters:
  cameras, vendor hand-tracking services, and foreign runtimes are now a
  distinct architecture zone for producing SteamVR hands, trackers, or body
  inputs.

### 8. `PSVR2-specific OpenXR eye-tracking and calibration follow-up`

- Main entries:
  `PSVR2_OpenXR_Eye_Tracking`, `PSVR2EyeTrackingCalibration`,
  `PSVR2Toolkit`
- Why it matters:
  the broader vendor-enhancement family is now much stronger, which makes the
  remaining PSVR2-specific OpenXR and calibration nodes more valuable as a
  future focused comparison wave.

### 9. `Validation and workflow micro-utilities`

- Main entries:
  `SteamVR-ActionsManifestValidator`, `Lighthouse-Scale-Fix`,
  `SteamVRAdaptiveBrightness`, `steamvr-exconfig`, `WFOVFix`
- Why it matters:
  these small tools solve real setup pain with unusually good effort-to-value
  ratios and still deserve a cleaner synthesis pass.

### 10. `Historical utility-suite recovery`

- Main entries:
  `ovr-utils`, `ovr-utils-dashboard`, `openvr_widgets`
- Why it matters:
  the repository still has one partly unresolved branch where the live code
  moved off GitHub and the public donor picture needs cleanup.

## Recommended next move

If `VR-apps-lab` continues this research, the next most valuable deep-pass order is:

1. `VirtualMotionTracker and broader OSC export family`
2. `Overlay implementation references and overlay-first hosts`
3. `Runtime-side service hosts and broader OpenXR utility platforms`
4. `Mixed-VR controller and tracker bridges`
5. `Low-level driver tutorial and custom-device plumbing`
6. `Virtual display and repurposed output workflows`
7. `Vision-based hand and body tracking bridges`
8. `PSVR2-specific OpenXR eye-tracking and calibration follow-up`
9. `Validation and workflow micro-utilities`
10. `Historical utility-suite recovery`
