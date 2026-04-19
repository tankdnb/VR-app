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

These are the strongest next candidates after the latest runtime, bridge, and
overlay-host waves.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `vrkit-platform/vrkit-platform` | Partially studied | Domain-specific overlay/runtime platform with plugin-manager and native-interop signals, but still broad and scope-shifted | High | High | Keep the next pass narrow: plugin manifests, native overlay interop, and real OpenXR boundaries instead of the whole product shell |
| `puresoul/Barebone` | Partially studied | HMD-relative synthetic Vive controllers driven by XInput | High | Medium | Driver/helper-app split, offset persistence, and long-term maintainability of the repo cluster |
| `krazysh01/VirtualDesktop-OpenVR-Trackers` | Partially studied | Product direction suggests body-state-to-tracker bridging, but the current public snapshot looks much thinner than expected | Medium | Medium | Re-check only if the public repo grows a real data-ingress surface or visible tracker-role mapping logic |
| `Sharrnah/whispering` | Partially studied | Broad local speech platform where VR is one consumer among OSC, websocket, TTS, and plugin outputs | High | High | Narrow the next pass to plugin boundaries, overlay-facing surfaces, and which slices matter most for future VR utility work |

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
| `CrispyPin/ovr-utils` | Partially studied | Historical utility-suite lineage whose GitHub repo is now mostly a relocation stub | Low-Medium | Medium | Follow the current non-GitHub upstream only if a dedicated recovery pass is worthwhile, and compare the lineage with `ovr-utils-dashboard` plus `openvr_widgets` |

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

## Priority batch L: Waves 32-35 surfaced follow-up candidates

These were surfaced while deepening communication-sidecar, alternative-runtime,
tracked-device, and expressive-input families, but they were intentionally kept
as honest follow-up nodes instead of being over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `maximum-game-22/openxr-3d-display` | Not studied deeply | Monado-derived spatial-display runtime that may clarify what parts of the special-display branch are generic versus product-specific | Medium | Medium | Compare its runtime layering and display assumptions directly against `displayxr-runtime` |
| `Kartaverse/OpenDisplayXR` | Not studied deeply | Nonstandard-display project cluster that may expose additional runtime packaging and deployment patterns | Medium | Medium | Inspect the exact split between runtime code, resources, and surrounding platform assets |
| `fughilli/ViveTrackedDevice` | Partially studied | Documentation-first reverse-engineering donor whose main code still sits behind submodules | Medium | Medium | Revisit only when a deeper submodule-aware pass on Lighthouse device internals becomes worthwhile |
| `ebadier/ViveTrackers` | Not studied deeply | Unity-side consumer library for Vive tracker hardware that may clarify the `hardware consumer` side of tracker tooling | Medium | Medium | Inspect API surface, data model, and whether it teaches more than the existing tracker-helper nodes |
| `takana-v/quest_steamvr_fbt_tool` | Not studied deeply | Quest-derived body-state export path aimed at avatar-facing consumers | Medium | Medium | Compare export model and consumer assumptions with `Baballonia`, `VRCThumbParamsOSC`, and other avatar-facing bridges |

## Priority batch M: Waves 36-39 surfaced follow-up candidates

These were surfaced while deepening broader OpenXR utility platforms,
mixed-VR controller bridges, workflow micro-tools, and overlay-host lineage,
but they were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `bdub1011/Quest-Link-Hand-Tracking` | Partially studied | Gesture-configurable Quest hand tracking mapped to SteamVR controller semantics | Low-Medium | Medium-high | Revisit only if the public driver source grows beyond the current thin placeholder snapshot |
| `mSparks43/PSVR-SteamVR-openHMD` | Not studied deeply | PSVR-specific Linux/OpenHMD bridge variant that could clarify how far the mixed-VR bridge family extends outside the mainline donors | Medium | Medium | Inspect the exact PSVR adaptations, packaging model, and overlap with `SteamVR-OpenHMD` before promoting it further |

## Priority batch N: Waves 40-43 surfaced follow-up candidates

These were surfaced while deepening VRChat text sidecars, avatar-facing OSC
companions, XR-glasses stacks, and wearable-haptics families, but they were
intentionally kept as honest follow-up nodes instead of being over-promoted
immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `lenoobkinda/VRCOSCUtils` | Partially studied | Broader mixed helper repo that still adds a useful comparison angle around small VRChat-side automation tools | Medium | Medium | Revisit only if a future pass needs a sharper comparison between weakly-structured helper bundles and the clearer companion-framework donors |

## Priority batch O: Waves 44-47 surfaced follow-up candidates

These were surfaced while deepening playspace tooling, redirected-walking
platforms, XR latency measurement stacks, and simulator-sidecar families, but
they were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `Knerten0815/VR_Dodge_Study` | Fork / variant only | Thesis-driven OpenRDW fork focused on dodging-informed reset research | Low-Medium | Medium | Revisit only if a future redirected-walking pass needs thesis-specific trial-data and sampling-interval changes rather than the main OpenRDW architecture |
| `Greendayle/VR-Motion-to-photon-latency-` | Partially studied | VRChat world plus smartphone slow-motion methodology for quick motion-to-photon checks | Low-Medium | High | Revisit if `VR-apps-lab` needs a more reproducible consumer-grade latency workflow or clearer asset breakdown beyond the Udon script and spreadsheet results |
| `giuseppdimaria/Unity-VRlines` | Partially studied | XR flight-sim prototype with modular aircraft physics and VR controller input mapping | Medium | Medium-high | Inspect the moved manuscript repo, scene architecture, and aircraft-control modules if a future pass needs richer embodied-control or simulator-shell references |

## Priority batch P: Waves 48-51 surfaced follow-up candidates

These were surfaced while deepening VRChat text workflows, OSC companion
frameworks, XR-glasses shells, and biometric or accessory-control families, but
they were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `MaurerKrisztian/vrc-tts-osc` | Not studied deeply | Narrow speech or TTS-to-chatbox path that could sharpen the `text workflow` comparison line without requiring a broader desktop shell | Medium | Medium | Inspect voice selection, message pacing, and whether it adds anything distinct beyond `VRCT`, `VRCTextboxSTT`, and other clearer text donors |
| `samyk/myo-osc` | Not studied deeply | Historical armband-to-OSC bridge that could add a useful `wearable input to avatar-facing signal` comparison node | Medium | Medium | Inspect whether it teaches more about wearable acquisition and gesture routing than the newer biometric and accessory-control donors |

## Priority batch Q: Waves 52-55 surfaced follow-up candidates

These were surfaced while deepening overlay scaffolds, media display shells,
Discord or note overlays, and specialized creator or companion surfaces, but
they were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `Marlamin/VROverlayTest` | Not studied deeply | Extra-thin D3D11/OpenVR overlay scratchpad that might matter if a future pass needs a smaller Windows baseline than `SampleVRO` | Medium | Low-Medium | Compare exact texture-upload path and event handling against `SampleVRO`, `OpenVROverlay_imgui`, and `csharp-openvr-overlay-imgui` |
| `beareogaming/BD-XSOverlay-notify` | Not studied deeply | Desktop plugin that pushes notifications into an existing overlay host over the official XSOverlay WebSocket contract | Medium | Medium | Inspect the exact WebSocket payload model and whether the `plugin -> host` split generalizes beyond Discord notifications |
| `iigomaru/MPVR` | Partially studied | Very rough `libmpv inside OpenVR overlay` proof of concept that may still matter as a lower-bound media embed comparison node | Medium | Medium | Revisit only if a future pass needs a cleaner comparison between full `vr-video-player-overlay` style shells and direct media-engine embedding |

## Priority batch R: Waves 56-59 surfaced follow-up candidates

These were surfaced while deepening browser-backed overlay runtimes, Linux
overlay shells, micro-overlays, and embodied-control surfaces, but they were
intentionally kept as honest follow-up nodes instead of being over-promoted
immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `CrispyPin/sinpin-vr` | Not studied deeply | Linux overlay project whose GitHub repo is now mostly a relocation stub | Low-Medium | Medium | Follow the moved upstream only if a future Linux overlay recovery pass becomes worthwhile |
| `Yukiiro-Nite/notebook-vr-overlay` | Partially studied | Rough note-surface overlay with explicit event plumbing but incomplete drawing or persistence flow | Medium | Medium | Revisit if a future pass needs deeper note persistence, drawing, or writing-state UX rather than just a lower-bound prototype |
| `OpenShock/VROverlay` | Partially studied | Older Unity lineage for a stronger current remote-device control overlay branch | Medium | Medium-High | Revisit only if a future lineage pass needs a tighter comparison against `OVR-Shock` |
| `NewChromantics/PopExposeXr` | Not studied deeply | Thin XR-state exposure concept that hints at a possible outward-facing bridge family | Medium | Medium | Inspect the networking contract and state-exposure model only if the public repo grows beyond its current sparse snapshot |

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
  `OVROverlayManager`, `LapisOverlay`, `h-view`, `VRSceneOverlay`,
  `godot-openvr-overlay`, `csharp-openvr-overlay-imgui`, `SampleVRO`,
  `ovrsalt`, `electron-openvr`, `ovrly`, `ComposeVR`
- Why it matters:
  this remains the clearest place to compare `scene-overlay scaffolds`,
  `desktop UI rasterization bridges`, `overlay-first hosts`,
  `engine-native projection overlays`, `browser-backed overlay runtimes`,
  and `micro-overlay patches` as distinct construction strategies.

### 3. `Runtime-side service hosts and broader OpenXR utility platforms`

- Main entries:
  `clearxr-server`, `vrkit-platform`, `openxr-explorer`,
  `OpenXR-API-Layers-GUI`
- Why it matters:
  Wave 36 clarified the family considerably, but the repo still needs a
  narrower follow-up on the broadest platform node, especially
  `vrkit-platform`, so the donor picture does not collapse back into a generic
  `runtime tools` bucket.

### 4. `Mixed-VR controller and tracker bridges`

- Main entries:
  `Oculus_Touch_Steam_Link`, `SteamVR-OpenHMD`,
  `Yet-Another-OpenVR-IPC-Driver`, `Quest-Link-Hand-Tracking`,
  `VirtualDesktop-OpenVR-Trackers`
- Why it matters:
  Wave 37 made the mainline donors much clearer, but the family still benefits
  from future comparison between strong bridges, thin hand-emulation repos, and
  hardware-specific variants.

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
  Wave 38 clarified the core donor patterns, and the remaining value now lies
  more in productization and comparison than in basic discovery.

### 10. `Historical utility-suite recovery`

- Main entries:
  `ovr-utils`, `ovr-utils-dashboard`, `openvr_widgets`
- Why it matters:
  Wave 39 made the lineage much clearer, but one partly unresolved branch still
  exists because the live `ovr-utils` code moved off GitHub and the public
  donor picture is still partly archival.

### 11. `VRChat text workflow refinements and TTS follow-up`

- Main entries:
  `vrcosc-magicchatbox`, `Chatbox`, `VRCT`, `TaSTT`, `KillFrenzyAvatarText`,
  `VRCOSCChatbox`
- Why it matters:
  the repo now has strong donors for `bounded text composition`,
  `mobile relay`, `translation shell`, `avatar text surfaces`, and
  `tiny senders`, so the remaining value is in sharper TTS follow-up and
  cleaner product comparison rather than basic discovery.

### 12. `Avatar-facing OSC companion frameworks and automation relays`

- Main entries:
  `OscGoesBrrr`, `VRCRouter`, `Quest2-VRC`, `vrc-oscquery-lib`,
  `vrchat-mcp-osc`, `OSCmooth`
- Why it matters:
  these repos now clarify desktop companions, discovery frameworks, relays, and
  smoothing layers; the next value lies in sharper comparison and productization
  rather than proving the family exists.

### 13. `XR glasses workspace shells and head-tracked screen tools`

- Main entries:
  `XRLinuxDriver`, `breezy-desktop`, `OpenVR-xrealAirGlassesHMD`,
  `virtual-display-rs`, `viture_virtual_display`, `desktop2stereo`,
  `PhoenixHeadTracker`
- Why it matters:
  special-display workflows now span platform shells, runtime-facing HMD paths,
  virtual-display services, screen-transformation tools, and non-XR tracking
  sidecars.

### 14. `Biometric, neurofeedback, and accessory-control bridges`

- Main entries:
  `PulsoidToOSC`, `iron-heart`, `vrc-osc-miband-hrm`, `vrc-osc-manager`,
  `OpenShock-ESP-Legacy`, `BrainFlowsIntoVRChat`
- Why it matters:
  the repo now has a distinct branch for measurements, biosignal trees,
  accessory plugins, and safety-aware embedded controllers, which is different
  from ordinary haptics bridges.

### 15. `Wearable haptics and avatar-driven feedback systems`

- Main entries:
  `ShockOSC`, `VRChatOSC`, `VRC-Haptic-Pancake`, `vrc-patpatpat`,
  `senseshift-firmware`
- Why it matters:
  tactile tooling now has clear layers around avatar authoring, bridge routing,
  solver logic, and firmware or hardware reference stacks.

### 16. `Playspace editors and room-boundary tooling`

- Main entries:
  `ChaperoneTweak`, `xr-chaperone`, `Guardian2Chaperone`,
  `Playspace-Mover`, `RotatoExpress`
- Why it matters:
  this family now clearly spans room authoring, boundary import, live room
  transform control, and shared-space helper patterns.

### 17. `Redirected walking and locomotion adaptation toolkits`

- Main entries:
  `RDWT`, `OpenRDW`, `OpenRDW2`, `ArmSwinger`
- Why it matters:
  algorithm harnesses and comfort locomotion are now a distinct reusable
  family rather than just scattered movement experiments.

### 18. `XR latency measurement and replay-analysis tooling`

- Main entries:
  `motion-to-photon-measurement`, `VRLate`, `vrlatency`,
  `dreyevr_recording_analyzer`
- Why it matters:
  this family now spans lab-style measurement, consumer-grade checks, and
  parser or analyzer tooling for XR replay data.

### 19. `Simulation telemetry overlays and motion-cueing sidecars`

- Main entries:
  `TinyPedal`, `VPforce-TelemFFB`, `SpaceMonkey`, `SimFeedback-AC-Servo`,
  `DReyeVR`
- Why it matters:
  mature sim sidecars and research simulator stacks are now clear donor lines
  for future VR utility and helper-app design.

### 20. `Context-aware overlay surfaces and specialized display shells`

- Main entries:
  `SteamVR-Discord-Overlay`, `vr-notes-anywhere`, `SmudgeTimerOpenVR`,
  `VRBro-Overlay`, `ROVER`, `steamvr-overlay-vrbuddy`, `VRPoleOverlay`
- Why it matters:
  the latest waves made it clear that some of the best overlay donors are not
  desktop mirrors at all, but narrow contextual surfaces with their own local
  state, control panel, study schema, collaborator view, or room anchor.

### 21. `Browser-backed overlay runtimes and web-tech UI hosts`

- Main entries:
  `ovrsalt`, `electron-openvr`, `ovrly`, `ComposeVR`
- Why it matters:
  these repos now expose several distinct answers to `web or declarative UI as
  overlay runtime`, from tiny frame-capture bridges to daemon-backed browser
  hosts.

### 22. `Linux overlay control shells and desktop-service panels`

- Main entries:
  `OVR4X11`, `SVRLinuxTools`, `OpenVR_Audio_Manager`
- Why it matters:
  Linux overlay tooling now has enough donor surface to justify its own follow-
  up branch around service panels, controller-mouse interaction, and desktop
  fallback modes.

### 23. `Micro-overlays, timed status surfaces, and informational display helpers`

- Main entries:
  `OVRBrightnessAPI`, `VR-Slideshow-Overlay`, `VRSessionTimer`,
  `notebook-vr-overlay`
- Why it matters:
  the latest pass made it clear that `small overlay with one strong value` is a
  coherent donor family, not just a set of weak side projects.

### 24. `Embodied workflow overlays and external-device control panels`

- Main entries:
  `bikeheadvr`, `Omni-Tune`, `OVR-Shock`, `OpenShock/VROverlay`
- Why it matters:
  these repos show that some overlay families are really `control surfaces`
  over body motion, live tuning, or remote hardware rather than informational
  panels.

## Recommended next move

If `VR-apps-lab` continues this research, the next most valuable deep-pass order is:

1. `VirtualMotionTracker and broader OSC export family`
2. `Overlay implementation references and overlay-first hosts`
3. `Runtime-side service hosts and broader OpenXR utility platforms`
4. `Mixed-VR controller and tracker bridges`
5. `Low-level driver tutorial and custom-device plumbing`
6. `Vision-based hand and body tracking bridges`
7. `Virtual display and repurposed output workflows`
8. `PSVR2-specific OpenXR eye-tracking and calibration follow-up`
9. `Historical utility-suite recovery`
10. `Validation and workflow micro-utilities`
11. `Biometric, neurofeedback, and accessory-control bridges`
12. `VRChat text workflow refinements and TTS follow-up`
13. `Avatar-facing OSC companion frameworks and automation relays`
14. `XR glasses workspace shells and head-tracked screen tools`
15. `Wearable haptics and avatar-driven feedback systems`
16. `Playspace editors and room-boundary tooling`
17. `XR latency measurement and replay-analysis tooling`
18. `Simulation telemetry overlays and motion-cueing sidecars`
19. `Redirected walking and locomotion adaptation toolkits`
20. `Context-aware overlay surfaces and specialized display shells`
21. `Browser-backed overlay runtimes and web-tech UI hosts`
22. `Linux overlay control shells and desktop-service panels`
23. `Micro-overlays, timed status surfaces, and informational display helpers`
24. `Embodied workflow overlays and external-device control panels`
