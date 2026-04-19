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
| `BnuuySolutions/PSVR2Toolkit` | Partially studied | Vendor-enhancement layer over an official headset stack | High | High | Vendor update fragility, developer API usage, hook boundaries, and the practical limits of the non-commercial feature set |
| `DaniXmir/GlassVr` | Partially studied | Bridge non-VR glasses hardware into SteamVR via emulation | High | High | Headset/controller/tracker emulation boundaries, hand-tracking path |
| `clear-xr/clearxr-server` | Partially studied | Runtime-side service host that mixes UI shell, registration helpers, streaming orchestration, and an OpenXR API layer | High | High | Keep the next pass narrow: runtime registration, layer boundaries, and service ownership instead of the full streaming platform |
| `verncat/RayNeo-Air-3S-Pro-OpenVR` | Partially studied | SDK-first glasses bridge whose driver still trails behind the transport layer | Medium-High | Medium-High | Dedicated driver repo maturity, IMU-to-pose handling, and how far the OpenVR path moves beyond the current stub |
| `krazysh01/VirtualDesktop-OpenVR-Trackers` | Partially studied | Product direction suggests body-state-to-tracker bridging, but the current public snapshot looks much thinner than expected | Medium | Medium | Re-check only if the public repo grows a real data-ingress surface or visible tracker-role mapping logic |

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
| `hai-vr/h-view` | Partially studied | Overlay-first utility host with desktop parity, ImGui rendering, and broader OSCQuery or hardware-tooling scope | High | High | Inspect the non-overlay boundaries next: OSCQuery, hardware inventory, OCR, external-service integration, and true product scope |
| `MeroFune/GOpy` | Not studied deeply | Experimental integration helper that may add a new desktop-to-VR bridge angle | Medium | Low | Actual problem scope, packaging model, and whether it contributes reusable bridge patterns |

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
| `OpenDisplayXR/OpenDisplayXR-VDD` | Not studied deeply | Simulated OpenVR/OpenXR virtual hardware driver path | Medium | Medium | Wait for stronger source/docs, then compare with `virtual_display`, `Virtual-Display-Driver`, and `VRto3D` |

## Priority batch G: Wave 12 follow-up candidates

These were surfaced or only partially exhausted during the Wave 12 source pass.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `openvrmc/OpenVR-MotionCompensation` | Partially studied | Pose-rewrite driver with separate library and in-VR dashboard | High | High | Hook insertion points, calibration model, overlay/lib coordination, and comparison with OpenXR-side motion compensation |
| `puresoul/Barebone` | Partially studied | HMD-relative synthetic Vive controllers driven by XInput | High | Medium | Driver/helper-app split, offset persistence, and long-term maintainability of the repo cluster |

## Priority batch H: Wave 13 follow-up candidates

These were surfaced or only partially exhausted during the Wave 13 source pass.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `chnoblouch/aethervr` | Partially studied | Webcam-driven custom OpenXR runtime with a Python tracker and local TCP protocol | High | High | Banjo runtime internals, pose prediction, graphics-path limits, and practical QA use |
| `MasonSakai/VR-AI-Full-Body-Tracking` | Not studied deeply | Camera FBT path that still carries InputEmulator-era assumptions while aiming at a cleaner driver rewrite | Medium | Medium | Whether the rewrite lands, how much of the current repo is reusable, and how it compares with `Mediapipe-VR-Fullbody-Tracking` |

## Priority batch I: foundational retro-normalization follow-up candidates

These were clarified during the foundational `waves 1-7` normalization pass and
should remain visible as the next honest follow-ups from the older corpus.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `CrispyPin/ovr-utils` | Partially studied | Early utility-suite lineage whose GitHub mirror no longer contains the real implementation source | Low-Medium | Medium | Follow the current non-GitHub upstream, determine whether the live code still matters, and compare it with `ovr-utils-dashboard` plus `openvr_widgets` |

## Priority batch J: Wave 14 follow-up candidates

These were surfaced during the Wave 14 source pass, or clarified as the next
honest follow-ups from the tracker-ingress and OSC-export family.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `TheNexusAvenger/Enigma` | Not studied deeply | Consumer-side export of SteamVR tracker roles into a non-XR client with a companion plugin path | Medium | Medium | Clipboard and companion-plugin transport, tracker-role mapping, and whether the pattern generalizes beyond Roblox |
| `ThatGuyThimo/leapmotion-osc` | Not studied deeply | Finger-only OSC export that complements SteamVR hand-tracking stacks | Medium | Medium | Avatar parameter model, OSC send cadence, and whether it teaches anything beyond `VRCThumbParamsOSC` |

## Priority batch K: Waves 20-21 surfaced follow-up candidates

These were surfaced while deepening the rendering-mod and OpenXR gaze-layer
families, but they were intentionally kept out of the core shortlist until the
stronger mainline donors were fully integrated.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `shieldmeidunn/SteamVRNullFlipper` | Not studied deeply | Null-driver and window-routing helper that may help headsetless graphics testing | Medium | Low-Medium | Confirm the actual graphics-hook and null-driver boundary, and decide whether it belongs closer to rendering mods or no-HMD workflow tooling |
| `BattleAxeVR/PSVR2_OpenXR_Eye_Tracking` | Not studied deeply | PSVR2-specific OpenXR eye-tracking path that may overlap with broader gaze-layer tooling | Medium | Medium | Compare its backend assumptions, extension surface, and donor value against `OpenXR-Eye-Trackers` and `PSVR2Toolkit` |
| `LordOfDragons/openxr_oscclient` | Not studied deeply | Thin OSC-to-OpenXR signal bridge hinting at a lighter runtime-side adaptation path | Medium | Medium | Inspect extension boundary, OSC transport model, and whether it complements or duplicates the broader OpenXR gaze-layer family |

## Family-level gaps that now deserve deeper passes

These are larger than a single repo and should guide the next research wave.

### 1. `Vendor enhancement tooling`

- Main entry: `PSVR2Toolkit`
- Why it matters:
  shows how to augment an official VR stack without fully replacing it.

### 2. `Tracker-ingress drivers and external program endpoints`

- Main entries:
  `OpenVR-Tracker-Websocket-Driver`, `Simple-OpenVR-Bridge-Driver`
- Why it matters:
  strongest path toward a future `Tracker Bridge Service`, and now clearly a
  place where `named pipe`, `JSON/WebSocket`, and richer local web-service
  variants should be compared directly.

### 3. `Virtual tracker / OSC platform`

- Main entries:
  `VirtualMotionTracker`, `SteamVR_To_OSC`, `OpenVR2OSC`, `OpenVR-OSC`,
  `VRCThumbParamsOSC`, `axis-vrc-osc-bridge`
- Why it matters:
  turns many scattered utility ideas into one coherent architecture category,
  now spanning both `SteamVR-centric export` and `direct OSC consumer` flows.

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
  `VROverlay`, `SteamVR-Webkit`, `SteamVR_HUDCenter`, `SteamVR-WebApps`,
  `OVROverlayManager`, `LapisOverlay`, `h-view`, `VRSceneOverlay`
- Why it matters:
  this is now one of the clearest places where `VR-apps-lab` can compare
  `scene-overlay scaffolds`, `desktop UI rasterization bridges`,
  `overlay-first hosts`, and `micro-overlay patches` as distinct construction
  strategies instead of one flat overlay bucket.

### 7. `SteamVR environment helpers and runtime hygiene tools`

- Main entries:
  `dashfix`, `SteamVR-Toggle`, `steamvr-undistort`, `SteamVR-VoidScene`,
  `steamvr-exconfig`, `steamvr_utils`
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

### 13. `Vision-based hand and body tracking bridges`

- Main entries:
  `driver_ultraleap`, `HandOfLesser`, `Mediapipe-VR-Fullbody-Tracking`,
  `NVIDIA-BodyTracking`
- Why it matters:
  this is now a distinct architecture zone where cameras, vendor hand-tracking
  services, or foreign runtimes become SteamVR hands, trackers, or fallback
  body-input paths.

### 14. `Headsetless camera runtimes and fake-hardware QA`

- Main entries:
  `aethervr`, `OpenXR-Simulator`, `VirtualSteamVRDriver`, `SteamVRNoHeadset`
- Why it matters:
  this turns no-HMD workflow research into something stronger than null-driver
  recipes by adding real runtime substitution and fake-hardware bring-up paths.

### 15. `Engine-side role reuse and consumer-side export`

- Main entries:
  `unity-openvr-tracking`, `SteamVRTrackerUtility`, `VRCThumbParamsOSC`,
  `axis-vrc-osc-bridge`
- Why it matters:
  this family shows that a useful VR utility does not always end in a new
  driver or overlay; sometimes the real value is reusing SteamVR roles in a
  host app or exporting them straight to a consumer-facing protocol.

## Recommended next move

If `VR-apps-lab` continues this research, the next most valuable deep-pass order is:

1. `VirtualMotionTracker and broader OSC export family`
2. `PSVR2Toolkit / vendor enhancement path`
3. `Accessibility overlays`
4. `Low-level driver tutorial and custom-device plumbing`
5. `Overlay implementation references`
6. `SteamVR environment helpers`
7. `Headsetless and no-HMD development workflows`
8. `Mixed-VR controller and tracker bridges`
9. `Runtime adapters and graphics interop`
10. `Virtual display and repurposed output workflows`
11. `Validation and workflow micro-utilities`
12. `Vision-based hand and body tracking bridges`
13. `Headsetless camera runtimes and fake-hardware QA`
14. `Engine-side role reuse and consumer-side export`
