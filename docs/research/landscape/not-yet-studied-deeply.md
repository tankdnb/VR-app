# Not Yet Studied Deeply

- Date: `2026-04-21`
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

- Use this file as the active deep-study and follow-up queue.
- The status values shown here are copied from `../catalog/project-registry.md`
  for queue context only.
- For a shorter `what matters now` view, start with `../current-focus.md`.

## Priority batch A

These are the strongest next candidates after the latest runtime, bridge, and
overlay-host waves.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
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

## Priority batch S: Waves 60-63 surfaced follow-up candidates

These were surfaced while deepening low-level overlay scaffolds,
managed-language starters, companion overlays, and specialized effect surfaces,
but they were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `Daniel-Webster/WT-OpenVR-Overlay` | Partially studied | Broad Unity overlay app whose local webservice and embedded overlay-framework lineage may still hide reusable pieces | Medium | Medium-High | Narrow the next pass to the reusable `OVRLay` boundary, local service consumption, and what is genuinely donor-worthy beyond the War Thunder-specific shell |
| `kurohuku7/zenn-overlay-tutorial` | Not studied deeply | Tutorial-first SteamVR overlay teaching path that may matter more as onboarding material than as a code donor | Low-Medium | Medium | Inspect only if a future pass needs stronger overlay tutorial references or Unity onboarding material |
| `Wulkop/VolumeVR` | Partially studied | Narrow `CEF`-based media or volume shell whose current public donor surface exposes bootstrapping more clearly than overlay behavior | Medium | Medium | Inspect whether deeper overlay logic lives in submodules or hidden paths, and compare the result against broader browser-runtime hosts |
| `emymin/EmyOverlay` | Not studied deeply | Thin specialized overlay node with too little current framing to promote, but still plausible as an effect-overlay comparison point | Low-Medium | Low-Medium | Check whether meaningful overlay logic exists beyond the current solution shell and whether it teaches anything distinct from the clearer effect-overlay donors |

## Priority batch T: Waves 80-83 surfaced follow-up candidates

These were surfaced while deepening VR audio helpers, immersive playback
systems, spatial-audio substrate, and creator-facing audio frameworks, but
they were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `BIVROST/360PlayerWindows` | Partially studied | Mature multi-headset media shell whose reusable value may extend beyond the current shell and headset split coverage | High | High | Inspect decoder, service-result, and per-backend playback layers more deeply if a future media-shell pass needs stronger desktop-plus-headset references |
| `videolan/vlc-unity` | Partially studied | Broad engine media framework where the strongest donor value may sit in packaging, backend abstraction, and immersive playback demos rather than one player prefab | High | High | Narrow the next pass to plugin packaging, demo scripts, and what parts of the LibVLC bridge are most reusable for VR utility work |
| `videolabs/libspatialaudio` | Partially studied | Unified spatial audio renderer spanning HOA, objects, speaker, and binaural output | High | Medium-High | Narrow the next pass to the actual `Renderer` implementation, object flow, and how much of the doc surface corresponds to direct donor code |
| `VoidXH/Cavern` | Partially studied | Broad immersive audio framework with Unity-like listener or source semantics plus filters and remapping | High | High | Revisit only if a future audio-substrate pass needs a fuller map of rendering, calibration, and Unity-side integration rather than current high-level architecture notes |
| `llealloo/audiolink` | Partially studied | Audio-reactive ecosystem where `_AudioTexture`, controller surfaces, and creator-side integrations may justify a dedicated donor pass | High | High | Inspect player APIs, mini-player flow, sync semantics, and shader or script integration boundaries more deeply |
| `JLChnToZ/VVMW` | Partially studied | Large modular creator-facing media frontend whose strongest reusable boundaries may sit between core, playlist, screen, and overlay subsystems | High | High | Narrow the next pass to core partials, frontend or queue boundaries, and which slices are genuinely donor-worthy beyond the full product shell |

## Priority batch U: Waves 84-87 surfaced follow-up candidates

These were surfaced while deepening browser panoramic players, engine-side
stereo panoramic viewers, creator-side synced video systems, and nonstandard
3D media viewers, but they were intentionally kept as honest follow-up nodes
instead of being over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `UNAmedia/ue5-stereo-panoramic-player-demo` | Partially studied | Public Unreal demo shell that exposes a strong `authoring surface plus programmable sphere` split even though the core plugin is external | Medium | High | Revisit only if a future pass needs the real plugin boundary, actor model, and asset flow rather than the public demo client |
| `koorimizuw/YamaPlayer` | Partially studied | Broad modular creator-facing video frontend with playlist, queue, handler, and integration surfaces | High | High | Narrow the next pass to controller partials, handler abstraction, module boundaries, and what is genuinely reusable beyond the full creator package |
| `fbriggs/lifecast_public` | Partially studied | Volumetric and VR180 playback substrate spanning WebXR player code and engine export targets | High | High | Narrow the next pass to media-format handling, volumetric playback core, and where the reusable web or engine boundaries actually sit |
| `parkchamchi/DepthViewer` | Partially studied | Depth-expanded 3D viewer that turns image or video input plus several inference backends into a navigable mesh surface | Medium-High | High | Revisit if `VR-apps-lab` needs a deeper `depth-to-3D media viewer` donor pass or clearer backend comparison |
| `prefrontalcortex/DomeTools` | Partially studied | Dome-style viewing environment where local media, `NDI`, and `Spout` ingest all feed one immersive shell | Medium | High | Revisit when a future pass needs deeper source-ingest flow, creator-viewer split, and dome-space interaction coverage |

## Priority batch V: Waves 88-91 surfaced follow-up candidates

These were surfaced while deepening VRChat creator-world authoring, runtime
infrastructure, camera/admin control, and utility-prefab families, but they
were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `Varneon/UdonEssentials` | Partially studied | Historical prefab-suite baseline that still matters for lineage even though the repo is deprecated | Medium | High | Compare the old bundle more directly against `VUdon` package decomposition and identify which legacy prefabs still deserve standalone follow-up |
| `Varneon/VUdon` | Partially studied | Ecosystem umbrella for packageized creator tools where the strongest donor value sits in the linked package repos | Medium | High | Inspect `QuickMenu`, `Menus`, `PlayerTracker`, and `Common` as individual package repos rather than treating the umbrella as the whole system |
| `VRLabs/Camera-System` | Partially studied | Avatar-driven OSC camera path system whose main architecture crosses an avatar package and an external companion executable | Medium | High | Narrow the next pass to companion protocol, path encoding model, and how the avatar-side constraints or contacts actually serialize the data |
| `SylanTroh/GMMenu` | Partially studied | Broad modular admin surface where watch camera, pings, permissions, teleports, and optional audio modes interact | High | High | Map the permission model, ping or alert flow, and optional `AudioManager` branch more directly instead of only the watch-camera slice |
| `Miner28/AvatarImageReader` | Partially studied | Unusual dynamic data carrier that encodes text through avatar imagery and runtime pedestal decoding | Medium | High | Re-check the editor encoder, multi-avatar queueing, and what parts still matter after the original string-loading era shifted |
| `Guribo/UdonLeaderBoard` | Not studied deeply | Possible scoreboard or ranking layer that may pair especially well with recycled-cell list infrastructure | Medium | Medium | Inspect whether it is mostly prefab sugar over `UdonRecyclingScrollRect` or whether it contributes a stronger data-model and sorting layer of its own |

## Priority batch W: Waves 92-95 surfaced follow-up candidates

These were surfaced while deepening VRChat world persistence, creator
diagnostics, embodied interaction, and creator utility-foundation families, but
they were intentionally kept as honest follow-up nodes instead of being
over-promoted immediately.

| Project | Current status in `VR-apps-lab` | Interesting idea | Code donor value | Product reference value | What to inspect next |
|---|---|---|---|---|---|
| `ChrisFeline/ToNSaveManager` | Partially studied | World-specific save companion that becomes interesting as a reusable `log parser + event bus + plugin host` even outside its original world | High | High | Narrow the next pass to DB model, JS plugin API, WebSocket event contract, and where the world-specific logic cleanly separates from the generic sidecar substrate |
| `DarthShader/Udon-MIDI-Web-Helper` | Partially studied | External helper that extends creator worlds through logs, HTTP, WebSocket, local storage, and MIDI return transport without client mods | High | High | Map the exact request framing, trust boundaries, local-storage model, and how much of the transport is reusable outside this specific helper |
| `GotoFinal/GotoUdon` | Partially studied | Broad editor-side Udon rehearsal stack whose strongest value may be the split between emulation, event injection, and multi-client test workflow | High | High | Inspect the client-launch automation, ownership or networking shims, and how much of the simulation core is reusable independently of the Unity editor chrome |
| `Janooba/immersive-interactions` | Partially studied | Package-shaped physical interaction toolkit where the strongest donor value may sit in collider rig generation, switch variants, and prefab decomposition | High | High | Split the next pass across buttons, switches, levers, and skeleton-generation helpers instead of treating the package as one surface |
| `Nestorboy/NUMovement` | Partially studied | Extensible movement framework that may hide several reusable sub-patterns under one broad controller package | High | High | Inspect the extension seams, debug helpers, moving-platform model, and which slices are best kept as framework substrate versus narrow movement donors |
| `kurotori4423/KurotoriUdonKart` | Partially studied | Broad creator vehicle rig whose most reusable value may be in seat-state, handle logic, and time-attack or race-side companions rather than the base kart loop alone | Medium-High | High | Map the seat, ranking, and state-side modules and compare the VR steering surface more directly against other embodied-control donors |
| `Guribo/UdonUtils` | Partially studied | Broad creator utility foundation where lifecycle, singleton identity, and execution-order validation are only the first layer of a larger subsystem tree | High | High | Peel off network-time, task, event, or helper subsystems and decide whether `UdonUtils` should become a multi-pass foundation donor rather than one registry node |

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

### 25. `Code-first overlay scaffolds and projection-overlay baselines`

- Main entries:
  `OpenGL-VROverlay`, `OpenVRWindowOverlay`, `openvr-overlay-test`,
  `openvr-overlay-bunny`
- Why it matters:
  the latest pass made it clear that `small honest overlay baselines` are a
  reusable family of their own rather than just implementation trivia.

### 26. `Managed-language overlay starters and Unity event-bridge scaffolds`

- Main entries:
  `uitoko-ovr`, `BasicOverlay`, `OpenVR-Overlay`, `WT-OpenVR-Overlay`
- Why it matters:
  this branch now spans reusable Unity templates, managed GPU-interoperable
  hosts, and broader app-specific scaffolds with clearer service boundaries.

### 27. `Desktop-adjacent companion overlays and phone or media control surfaces`

- Main entries:
  `OVR_SLDO`, `OVRPhoneBridge`, `ViveOverlayPaster`, `VolumeVR`
- Why it matters:
  the overlay corpus now clearly includes `companions for external workflows`,
  not just dashboards or full runtime hosts.

### 28. `Specialized effect overlays and visibility-shaping comfort surfaces`

- Main entries:
  `OpenMixerXR`, `SteamVRBlackBarOverlay`, `VR-Overlay-Half_Ring`,
  `OpenVR-Windows-Activation`
- Why it matters:
  the latest pass made it clear that `effect-first overlays` are a meaningful
  product family with reuse value for comfort, passthrough cutouts, and visual
  masking.

### 29. `OpenXR sample-app bring-up references and rendering baselines`

- Main entries:
  `OpenXRSamples`, `openxr-vulkan-example`, `wgpu-openxr-example`,
  `android_openxr_gles`, `openxr-simple-example`, `OpenXR-Samples`
- Why it matters:
  the latest pass made it clear that `OpenXR bring-up references` are a
  reusable donor family of their own, spanning one-file lower bounds,
  structured sample apps, desktop-to-XR migration paths, and shared-core sample
  suites.

### 30. `OpenXR language bindings and wrapper-generation systems`

- Main entries:
  `openxrs`, `pyopenxr`, `OpenXR.NET`, `openxr-zig`, `openxr.py`, `rlOpenXR`
- Why it matters:
  the repo now has a distinct donor branch for `how OpenXR gets wrapped`,
  including safe-plus-raw stacks, generated scripting facades, managed-language
  emitters, and build-integrated wrapper generation.

### 31. `OpenVR language bindings and runtime facades`

- Main entries:
  `rust-openvr`, `pyopenvr`, `openvr-go`, `node-openvr`, `OpenVR.NET`,
  `java openvr`
- Why it matters:
  the latest pass made it clear that `OpenVR access layers` are not just thin
  interop trivia; they are reusable donor families for typed wrappers,
  scripting surfaces, runtime bridges, and richer managed-language facades.

### 32. `OpenVR tracking export, record-replay, and robotics integration`

- Main entries:
  `OpenVR-Tracking-Example`, `openvr_ros`, `openvr_ros_bridge`,
  `openvr_ros2_tracker`, `openvr-input-recorder`, `vrviz`, `vrpn-openvr`
- Why it matters:
  tracking export is now clearly broader than `send poses somewhere`; it
  includes pluggable publishers, record-replay harnesses, and VR-native
  consumers for robotics topics.

### 33. `VMT adapters, OSC action compilers, and skeletal validation utilities`

- Main entries:
  `VirtualMotionTracker`, `SteamVR_To_OSC`, `OpenVR-OSC`, `VMC2VMT`,
  `SkeletonPoseTester`, `OVR-VRC-OSC-Bridge`
- Why it matters:
  this branch now separates `mature tracker host`, `thin OSC exporter`,
  `protocol adapter`, `skeletal validation node`, and `config-defined
  controller-state compiler` into one coherent product family.

### 34. `OpenXR platform shells, layer managers, and runtime inspection workbenches`

- Main entries:
  `vrkit-platform`, `clearxr-server`, `openxr-explorer`,
  `OpenXR-API-Layers-GUI`
- Why it matters:
  this family turns `OpenXR doctor` from a vague idea into a concrete cluster
  of runtime-side platforms, session-owning shells, shared GUI-plus-CLI
  inspectors, and repair-oriented layer managers.

### 35. `Mixed-VR controller bridges, hand emulation, and external-tracker interop`

- Main entries:
  `Oculus_Touch_Steam_Link`, `SteamVR-OpenHMD`,
  `Yet-Another-OpenVR-IPC-Driver`, `Quest-Link-Hand-Tracking`,
  `PSVR-SteamVR-openHMD`, `VirtualDesktop-OpenVR-Trackers`
- Why it matters:
  controller reuse is now broader than pose transport alone; it spans profile
  reuse, command-driven synthetic devices, declarative hand emulation, and
  hardware-specific OpenHMD variants.

### 36. `OpenVR driver learning paths, synthetic devices, and remote-input ingress`

- Main entries:
  `Simple-OpenVR-Driver-Tutorial`, `openvr-driver-example`, `Barebone`,
  `OpenVR-ArduinoHMD`, `RemoteVVR`, `OpenVR-Tracker-Driver-Example`
- Why it matters:
  this family exposes the smallest honest `driver baseline` path, from
  tutorial shells and narrow input examples to DIY HMDs, remote/file-fed
  ingress, and tracking-override harnesses.

### 37. `OpenVR overlay access layers, starter variants, and minimal shell experiments`

- Main entries:
  `ovr_overlay`, `OpenVROverlayTest`, `UniversalVROverlay`,
  `OpenVR.ALBRT.overlay`
- Why it matters:
  this family now makes the `smallest honest overlay implementation layers`
  explicit, from focused access wrappers to dashboard starters and desktop
  shells over shared overlay backends.

### 38. `WayVR ecosystem add-ons, Linux dashboard extensions, and IPC-backed overlay surfaces`

- Main entries:
  `wayvr`, `wayvr-dashboard`, `wayvr-ipc`, `WayvrWalltaker`
- Why it matters:
  the latest pass made it clear that some Linux desktop-in-VR families are
  really `host ecosystems`, not single tools, with reusable splits across
  compositor core, protocol crate, dashboard client, and script extension.

### 39. `OpenVR capture, replay, and orchestration toolchains`

- Main entries:
  `vr-capture-replay`, `virtual-camera-offset`,
  `VRScout_Agent_Orchestration_Unity_Project`, `ViRe`
- Why it matters:
  this branch now separates `capture artifact`, `replay driver`,
  `post-capture alignment`, `closed-loop orchestration`, and
  `VR-native recording studio`
  into one coherent product family.

### 40. `OpenXR micro-layers for view shaping, streamout, debugging capture, and frame-time intervention`

- Main entries:
  `OpenXR-RecenterOverride`, `OpenXR-Layer-crop-fov`,
  `openxr_streamout_layer`, `openxr-renderdoc-layer`,
  `Smoothing-OpenXR-Layer`
- Why it matters:
  the latest pass made it clear that `OpenXR layer` is not only about generic
  templates or compatibility work; it now includes operator-facing micro-tools,
  stream bridges, developer-tool integration, and advanced frame intervention.

### 41. `OpenXR capability-injection layers, input remappers, and peripheral extension bridges`

- Main entries:
  `OpenXRHandTracking`, `openxr_remapping_layer`, `OpenXR_ApiLayer_Patstrap`
- Why it matters:
  the latest pass made it clear that some of the best OpenXR layers do not
  inspect or patch rendering at all; they add new capability surfaces or remap
  semantics before the app sees them.

### 42. `OpenXR helper stacks, layer toolchains, and runtime adaptation helpers`

- Main entries:
  `quark`, `rayxr`, `openxr-layer-scripts`, `OpenXR-CAS`
- Why it matters:
  this branch now spans authoring frameworks, tiny renderer-facing helpers,
  loader-hygiene micro-tools, and more productized runtime adaptation layers.

### 43. `OpenXR passthrough samples and engine-side extension integration references`

- Main entries:
  `ue-openxr-passthrough`, `godot_test_passthrough`,
  `mr-openxr-unity-meta-passthrough-sample`
- Why it matters:
  the latest pass made it clear that engine-facing OpenXR integration is a
  reusable family of its own, especially when a plugin or sample adds one
  runtime feature cleanly without dragging in a full vendor stack.

### 44. `Desktop-window overlay shells, Linux capture utilities, and launcher stubs`

- Main entries:
  `DesktopOverlayer`, `ovr-penguin`, `RobloxVRLauncher`
- Why it matters:
  this branch now captures a rougher but still useful part of the overlay
  landscape: native texture bridges, CLI-first capture hosts, and thin launcher
  product directions that should be tracked honestly.

### 45. `Microphone control, voice-input fan-out, and audio routing helpers`

- Main entries:
  `OpenVR-MicrophoneControl`, `VRCTextboxSTT`, `OpenVR_Audio_Manager`,
  `Virtual-Audio-Driver`
- Why it matters:
  this branch now makes `VR audio helpers` much more explicit, spanning
  mic-state dashboards, STT fan-out sidecars, endpoint-routing panels, and
  lower-layer virtual audio substrate.

### 46. `Immersive media playback and browser video shells`

- Main entries:
  `around-sound`, `360PlayerWindows`, `WebXR-video-player`, `vlc-unity`
- Why it matters:
  immersive playback is now a clearer family of its own, spanning VR-native
  music experiences, desktop-plus-headset shells, browser-native video players,
  and engine-side media frameworks.

### 47. `Spatial audio SDKs, renderers, and audio-object optimization`

- Main entries:
  `spatialaudio-unity`, `libspatialaudio`, `omnitone`, `Cavern`,
  `spatial-audio-clustering`
- Why it matters:
  the repository now has a much stronger lower-layer audio branch covering
  engine spatializers, unified renderers, browser ambisonics, broad immersive
  audio frameworks, and object-budget optimization.

### 48. `Creator-facing audio systems and world voice management`

- Main entries:
  `audiolink`, `USharpVideo`, `USharpVideoQueue`, `VVMW`, `AudioManager`
- Why it matters:
  creator-side audio is now clearly broader than one player or one reactive
  prefab. It spans audio-reactive substrate, synced media cores, queue
  companions, modular media frontends, and world voice-state control.

### 49. `Browser panoramic video players and projection-aware web playback`

- Main entries:
  `360WebPlayer`, `videojs-panorama`, `videojs-vr`, `VR-Player`
- Why it matters:
  the latest pass made it clear that `immersive browser playback` is not one
  shell shape; it spans full playback frameworks, plugin upgrades over existing
  players, projection-enum control surfaces, and thin mobile wrappers.

### 50. `Engine-side stereo panoramic viewers and vendor playback samples`

- Main entries:
  `Unity_Panorama180View`, `VideoPlayer-UnityXR`,
  `ue5-stereo-panoramic-player-demo`
- Why it matters:
  engine-side playback now has a clearer donor branch of its own around
  projection-surface components, layout-specific sample matrices, and
  higher-level panoramic authoring shells.

### 51. `Creator-side synced video player frameworks and queue frontends`

- Main entries:
  `VideoTXL`, `UdonVideoplayer`, `YamaPlayer`
- Why it matters:
  the latest pass made it clear that `creator video system` is broader than one
  sync script; it spans manager splits, queue and playlist flow, backend
  abstraction, and extension-heavy frontends for events or shared spaces.

### 52. `Transformed, volumetric, and nonstandard 3D video viewers`

- Main entries:
  `VR-reversal`, `lifecast_public`, `DepthViewer`, `DomeTools`
- Why it matters:
  this branch now captures several unusual but reusable media directions:
  transform-driven viewers, volumetric and VR180 substrate, depth-expanded
  media viewers, and immersive dome environments with multi-source ingest.

### 53. `VRChat world-authoring toolkits, optimization helpers, and prefab ecosystems`

- Main entries:
  `VRWorldToolkit`, `UdonSharpOptimizer`, `UdonEssentials`, `VUdon`
- Why it matters:
  the latest pass made it clear that `creator-world tooling before runtime` is
  a reusable donor branch of its own, spanning build-request guardrails,
  compiler-pipeline intervention, legacy prefab suites, and ecosystem-shaped
  package constellations.

### 54. `VRChat world runtime infrastructure, voice, networking, and player-state helpers`

- Main entries:
  `UdonVoiceUtils`, `UNet`, `UdonPlayerPlatformHook`, `CyanPlayerObjectPool`
- Why it matters:
  this branch now shows that `creator-world runtime substrate` is broader than
  one sync script, spanning voice-state control, byte-array transport,
  moving-platform correction, and stable per-player object anchoring.

### 55. `VRChat camera, staging, and admin-control systems for world events`

- Main entries:
  `VRChatCameraWorks`, `CameraSystem`, `Camera-System`, `GMMenu`
- Why it matters:
  the latest pass made it clear that `creator camera tooling` splits into
  prefab staging rigs, world-side operator consoles, avatar-driven OSC camera
  paths, and broader admin surfaces with watch-camera modules.

### 56. `VRChat interaction, utility UI, and information-surface prefabs`

- Main entries:
  `U-Key`, `VRCMarker`, `AvatarImageReader`, `UdonRecyclingScrollRect`,
  `UdonLeaderBoard`
- Why it matters:
  this branch now captures a broad but coherent family of creator-world
  interaction surfaces: access-control prefabs, annotation tools, dynamic data
  carriers, and lower-layer list or board infrastructure.

### 57. `VRChat world persistence, inventory, and external-data bridges`

- Main entries:
  `NUSaveState`, `ToNSaveManager`, `InventorySystem`,
  `Udon-MIDI-Web-Helper`
- Why it matters:
  this family now shows that `creator-world persistence` splits across pure
  in-world encoding, synced inventory ownership, world-specific save
  companions, and external helper bridges for data the platform does not expose
  directly.

### 58. `VRChat creator diagnostics, editor inspection, profiling, and static analysis`

- Main entries:
  `GotoUdon`, `UdonExplorer`, `UdonSharpProfiler`,
  `UdonRabbit.Analyzer`
- Why it matters:
  this family now makes `creator diagnostics` a concrete branch of its own,
  spanning simulation, inspection, compiler instrumentation, and analyzer-based
  guardrails.

### 59. `VRChat embodied interaction, custom movement, and physical world mechanics`

- Main entries:
  `immersive-interactions`, `UdonTether`, `NUMovement`, `UdonDoor`,
  `KurotoriUdonKart`
- Why it matters:
  this family now captures a strong creator-world mechanics branch where the
  key donor value sits in collider rigs, locomotion controllers, narrow
  physical prefabs, and vehicle-state splits rather than in generic UI.

### 60. `Udon data-structure libraries, serialization helpers, and creator utility foundations`

- Main entries:
  `UdonUtils`, `udon-list`, `udon-dictionary`, `udon-json`,
  `UArrayCollections`, `VUdon-ArrayExtensions`
- Why it matters:
  this family now makes `creator substrate` explicit, from lifecycle and
  execution-order foundations to historical collection emulation and modern
  array-first helper layers.

### 61. `VRChat creator starter baselines, test harnesses, and language-boundary experiments`

- Main entries:
  `template-world`, `template-udonsharp`, `udon-test`, `wasm2usharp`
- Why it matters:
  this family now makes the `very first creator-world layer` explicit, spanning
  official bootstrap lineage, in-world assertion helpers, and unusual
  alternative-language experiments that still target UdonSharp.

### 62. `Udon encoding, token, query, and structured-data micro-libraries`

- Main entries:
  `udon-encoding`, `udon-jwt`, `ULinq`, `UdonXMLParser`
- Why it matters:
  this family now captures a strong constrained-runtime micro-library branch:
  manual encoding fallback, frame-sliced cryptography, compile-time query DSL
  lowering, and structured-data parsing over `DataDictionary` or `DataList`.

### 63. `Udon sync, events, runtime logging, and shared helper micro-frameworks`

- Main entries:
  `VUdon-Events`, `UdonSharpNetworkingLib`, `LightSync`, `VUdon-Logger`
- Why it matters:
  this family now makes `creator runtime helper frameworks` much clearer,
  spanning serialized event routing, typed RPC surfaces, stateful sync lineage,
  and in-world diagnostics.

### 64. `VRChat world control gadgets, environmental systems, and specialized operator surfaces`

- Main entries:
  `VUdon-DepthBufferToolkit`, `VR-Stage-Lighting`,
  `UdonSharpDayNightController`, `VRChat_Keypad`, `UdonKeypad`
- Why it matters:
  this family now captures a coherent control-surface branch across narrow
  render fixups, shared environmental clocks, larger operator ecosystems, and
  reusable access-control gadgets.

### 65. `VRChat avatar setup, optimization, and Quest portability`

- Main entries:
  `PumkinsAvatarTools`, `VRCQuestTools`, `d4rkAvatarOptimizer`,
  `immersive_scaler`
- Why it matters:
  this family now makes the avatar bring-up pipeline explicit across editor
  workbenches, validator-driven mobile conversion, upload-time optimization,
  and DCC-side proportional scaling.

### 66. `VRChat avatar composition, packaging, and install automation`

- Main entries:
  `modular-avatar`, `modular-avatar-as-code`, `vrc-get`,
  `Avatars-3.0-Manager`
- Why it matters:
  this family now captures a strong creator integration branch where
  composition substrate, package management, and install-safe helper shells all
  matter together.

### 67. `VRChat avatar emulation, gesture preview, repair, and OSC-assisted posing`

- Main entries:
  `Av3Emulator`, `VRC-Gesture-Manager`, `avautils`, `LexisPosingSystem`
- Why it matters:
  this family now makes `avatar rehearsal and intervention`
  explicit, spanning full emulators, preview harnesses, repair suites, and
  pose-session OSC companions.

### 68. `VRChat avatar text, speech, translation, and viseme sidecars`

- Main entries:
  `TTS-Voice-Wizard`, `kikitan-translator`, `HeadTTS`, `Billboard`
- Why it matters:
  this family now captures the avatar-facing speech stack more honestly across
  operator speech hubs, overlay-backed translation shells, viseme-aware engines,
  and avatar-visible speech surfaces.

## Recommended next move

If `VR-apps-lab` continues this research, the next most valuable deep-pass order is:

1. `Overlay implementation references and overlay-first hosts`
2. `OpenXR capability-injection, passthrough extension, and runtime-side intervention tooling`
3. `Vision-based hand and body tracking bridges`
4. `Virtual display and repurposed output workflows`
5. `OpenVR capture, replay, and orchestration toolchains`
6. `WayVR ecosystem and Linux overlay surfaces`
7. `PSVR2-specific OpenXR eye-tracking and calibration follow-up`
8. `Browser panoramic video players and projection-aware web playback`
9. `Creator-side synced video player frameworks and queue frontends`
10. `Engine-side stereo panoramic viewers and vendor playback samples`
11. `Transformed, volumetric, and nonstandard 3D video viewers`
12. `Historical utility-suite recovery`
13. `Validation and workflow micro-utilities`
14. `Biometric, neurofeedback, and accessory-control bridges`
15. `VRChat world-authoring toolkits and optimization helpers`
16. `VRChat world runtime infrastructure and per-player state helpers`
17. `VRChat camera, staging, and admin-control systems`
18. `VRChat interaction prefabs and utility UI`
19. `VRChat text workflow refinements and TTS follow-up`
20. `Avatar-facing OSC companion frameworks and automation relays`
21. `XR glasses workspace shells and head-tracked screen tools`
22. `Wearable haptics and avatar-driven feedback systems`
23. `Simulation telemetry overlays and motion-cueing sidecars`
24. `Microphone control, voice-input, and audio routing helpers`
25. `Immersive media playback and browser video shells`
26. `Spatial audio SDKs, renderers, and audio-object optimization`
27. `Creator-facing audio systems and world voice management`
28. `VRChat world persistence, inventory, and external-data bridges`
29. `VRChat creator diagnostics, editor inspection, profiling, and static analysis`
30. `VRChat embodied interaction, custom movement, and physical world mechanics`
31. `Udon data-structure libraries, serialization helpers, and creator utility foundations`
32. `VRChat creator starter baselines, test harnesses, and language-boundary experiments`
33. `Udon encoding, token, query, and structured-data micro-libraries`
34. `Udon sync, events, runtime logging, and shared helper micro-frameworks`
35. `VRChat world control gadgets, environmental systems, and specialized operator surfaces`
36. `VRChat avatar setup, optimization, and Quest portability`
37. `VRChat avatar composition, packaging, and install automation`
38. `VRChat avatar emulation, gesture preview, repair, and OSC-assisted posing`
39. `VRChat avatar text, speech, translation, and viseme sidecars`

For the longer-range family backlog beyond this shorter priority order, use the
`Family-level gaps` section below.
