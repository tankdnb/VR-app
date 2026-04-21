# Current Focus

- Date: `2026-04-21`
- Purpose: give a short `what matters now` view of `VR-apps-lab` without
  forcing a new session or visitor through the full wave archive.

## What this repository is doing now

`VR-apps-lab` is being maintained as a public:

- `knowledge repository`
- `pattern library`
- `working lab`

for VR utilities, overlays, diagnostics, tracking helpers, runtime tools, and
experimental XR integrations.

The repository is no longer trying to act like one hidden main application.

## Strongest active directions

These are the clearest current product and research lines:

1. `Overlay implementation references and overlay-first utility hosts`
   small and medium overlay surfaces remain one of the strongest donor areas in
   the whole repo, now including thinner access layers and starter variants.
2. `OpenXR runtime, capability-injection layers, diagnostics, and micro-layer utilities`
   the repository now has enough material to support both an `OpenXR doctor /
   runtime inspector` branch and smaller capability, passthrough, and
   operator-facing layer utilities.
3. `Tracker, OSC, and virtual-device tooling`
   `VMT`, OSC exporters, and synthetic-device hosts form a strong reusable
   implementation family.
4. `Mixed-VR bridge patterns`
   controller, hand-tracking, and hardware-interop bridges are now a clear
   comparison line of their own.
5. `OpenVR driver learning paths`
   the repo now contains a stronger baseline for future driver experiments than
   it did earlier.
6. `Accessibility, communication, and companion surfaces`
   small user-value-first tools remain an important public direction, not just
   a side branch.
7. `VR audio, immersive playback, projection-aware video systems, and creator-facing media tools`
   the repository now has a clearer branch for mic-state tools, media-player
   shells, panoramic video donors, nonstandard 3D viewers, spatial-audio
   substrate, and creator-side media frameworks.
8. `VRChat creator-world tooling, runtime substrate, persistence, diagnostics, and physical mechanics`
   the repository now has a much clearer branch for world-authoring helpers,
   creator runtime substrate, persistence and external-data bridges,
   diagnostics, event-camera systems, reusable utility surfaces, and embodied
   interaction donors.

## Most useful current docs

Use these first if you need fast recovery:

1. `../foundation/current-operating-context.md`
2. `program/new-session-quickstart.md`
3. `catalog/project-registry.md`
4. `landscape/project-families.md`
5. `landscape/not-yet-studied-deeply.md`
6. `methods/vr-utility-methods-catalog.md`

## Recent landmark waves

These are the most useful recent reference waves if you need current examples
instead of full history:

- `landscape/vr-projects-wave-64-openxr-sample-apps-rendering-baselines-and-bring-up-references.md`
- `landscape/vr-projects-wave-67-openvr-tracking-export-recording-and-robotics-bridge-tooling.md`
- `landscape/vr-projects-wave-68-vmt-adapters-osc-action-compilers-and-skeletal-validation-utilities.md`
- `landscape/vr-projects-wave-69-openxr-platform-shells-layer-managers-and-runtime-inspection-workbenches.md`
- `landscape/vr-projects-wave-70-mixed-vr-controller-bridges-hand-emulation-and-external-tracker-interop.md`
- `landscape/vr-projects-wave-71-openvr-driver-learning-paths-synthetic-devices-and-remote-input-ingress.md`
- `landscape/vr-projects-wave-72-openvr-overlay-access-layers-starter-variants-and-minimal-shell-experiments.md`
- `landscape/vr-projects-wave-73-wayvr-ecosystem-add-ons-linux-dashboard-extensions-and-ipc-backed-overlay-surfaces.md`
- `landscape/vr-projects-wave-74-openvr-capture-replay-and-orchestration-toolchains.md`
- `landscape/vr-projects-wave-75-openxr-micro-layers-for-view-shaping-streamout-debugging-capture-and-frame-time-intervention.md`
- `landscape/vr-projects-wave-76-openxr-capability-injection-layers-input-remappers-and-peripheral-extension-bridges.md`
- `landscape/vr-projects-wave-77-openxr-helper-stacks-layer-toolchains-and-runtime-adaptation-helpers.md`
- `landscape/vr-projects-wave-78-openxr-passthrough-samples-and-engine-side-extension-integration-references.md`
- `landscape/vr-projects-wave-79-desktop-window-overlay-shells-linux-capture-utilities-and-launcher-stubs.md`
- `landscape/vr-projects-wave-80-microphone-control-voice-input-pipelines-and-audio-routing-helpers.md`
- `landscape/vr-projects-wave-81-immersive-music-players-vr-media-playback-surfaces-and-browser-video-shells.md`
- `landscape/vr-projects-wave-82-spatial-audio-sdks-renderers-and-object-optimization-toolchains.md`
- `landscape/vr-projects-wave-83-creator-facing-audio-systems-synced-player-frameworks-and-world-side-voice-management.md`
- `landscape/vr-projects-wave-84-browser-panoramic-video-players-mobile-wrappers-and-projection-aware-web-playback.md`
- `landscape/vr-projects-wave-85-engine-side-stereo-panoramic-viewers-vendor-player-samples-and-layout-specific-video-surfaces.md`
- `landscape/vr-projects-wave-86-vrchat-synced-video-player-frameworks-queue-frontends-and-event-optimized-media-shells.md`
- `landscape/vr-projects-wave-87-transformed-volumetric-and-nonstandard-3d-video-viewers.md`
- `landscape/vr-projects-wave-88-vrchat-world-authoring-toolkits-optimization-helpers-and-prefab-ecosystems.md`
- `landscape/vr-projects-wave-89-vrchat-world-runtime-infrastructure-voice-networking-and-player-state-helpers.md`
- `landscape/vr-projects-wave-90-vrchat-camera-staging-and-admin-control-systems-for-world-events.md`
- `landscape/vr-projects-wave-91-vrchat-interaction-ui-and-information-surface-prefabs.md`
- `landscape/vr-projects-wave-92-vrchat-world-persistence-inventory-save-manager-companions-and-external-data-bridges.md`
- `landscape/vr-projects-wave-93-vrchat-creator-diagnostics-editor-inspection-profiling-and-static-analysis-helpers.md`
- `landscape/vr-projects-wave-94-vrchat-embodied-interaction-custom-movement-and-physical-world-mechanics.md`
- `landscape/vr-projects-wave-95-udon-data-structure-libraries-serialization-helpers-and-creator-utility-foundations.md`

## Strong donor clusters right now

If the goal is to extract high-value implementation patterns, these are some of
the strongest current clusters:

- `openxr-explorer`, `OpenXR-API-Layers-GUI`, `clearxr-server`,
  `vrkit-platform`
  for runtime inspection, layer-state repair, and desktop-plus-XR platform
  splits.
- `VirtualMotionTracker`, `VMC2VMT`, `OVR-VRC-OSC-Bridge`,
  `SteamVR_To_OSC`
  for tracker-host design, adapter layers, and controller-to-OSC compilers.
- `Yet-Another-OpenVR-IPC-Driver`, `Simple-OpenVR-Driver-Tutorial`,
  `OpenVR-Tracker-Driver-Example`, `OpenVR-ArduinoHMD`
  for synthetic-device ingress, driver learning, and test harnesses.
- `DesktopPlus`, `OpenKneeboard`, `h-view`, `SteamVR-WebApps`,
  `VRSceneOverlay`
  for overlay-first utility shells and in-headset workflow surfaces.
- `ovr_overlay`, `OpenVR.ALBRT.overlay`, `wayvr`, `wayvr-ipc`
  for overlay backplanes, Linux host ecosystems, and desktop-shell plus
  overlay-backend splits.
- `vr-capture-replay`, `VRScout_Agent_Orchestration_Unity_Project`, `ViRe`
  for record-replay harnesses, orchestration loops, and VR-native recording
  studios.
- `OpenXR-RecenterOverride`, `OpenXR-Layer-crop-fov`,
  `openxr-renderdoc-layer`, `openxr_streamout_layer`
  for operator-facing and developer-facing OpenXR micro-layers.
- `OpenXRHandTracking`, `openxr_remapping_layer`, `quark`, `OpenXR-CAS`,
  `ue-openxr-passthrough`
  for capability injection, layer authoring, runtime adaptation, and
  engine-side extension integration.
- `spatialaudio-unity`, `omnitone`, `libspatialaudio`, `Cavern`,
  `spatial-audio-clustering`
  for spatial-audio substrate, renderer abstractions, and object-budget-aware
  audio tooling.
- `AudioLink`, `USharpVideo`, `USharpVideoQueue`, `VVMW`, `AudioManager`
  for creator-facing audio infrastructure, synced media systems, and world
  voice-state control.
- `360WebPlayer`, `videojs-panorama`, `videojs-vr`, `Unity_Panorama180View`,
  `VideoTXL`, `VR-reversal`, `DomeTools`
  for projection-aware playback layers, creator-side video systems, and
  nonstandard 3D viewing environments.
- `VRWorldToolkit`, `UdonSharpOptimizer`, `VUdon`, `UdonEssentials`
  for creator-world authoring, package ecosystems, and pre-runtime workflow
  tooling.
- `UdonVoiceUtils`, `UNet`, `CyanPlayerObjectPool`, `VRChatCameraWorks`,
  `CameraSystem`, `GMMenu`, `U-Key`, `VRCMarker`, `UdonRecyclingScrollRect`
  for creator-world runtime substrate, staging systems, admin surfaces, and
  utility-prefab infrastructure.
- `NUSaveState`, `InventorySystem`, `ToNSaveManager`,
  `Udon-MIDI-Web-Helper`
  for creator-world persistence, companion save managers, and external-data
  bridge architecture.
- `GotoUdon`, `UdonExplorer`, `UdonSharpProfiler`,
  `UdonRabbit.Analyzer`
  for creator diagnostics, editor inspection, compiler instrumentation, and
  static guardrails.
- `immersive-interactions`, `UdonTether`, `NUMovement`, `UdonDoor`,
  `KurotoriUdonKart`
  for embodied interaction, locomotion mechanics, and physical world-control
  donors.
- `UdonUtils`, `udon-list`, `udon-dictionary`, `udon-json`,
  `UArrayCollections`, `VUdon-ArrayExtensions`
  for creator-world substrate, lifecycle foundations, and constrained
  data-structure design.

## Highest-value next follow-up passes

If a new research wave should start soon, these remain especially strong next
directions:

1. `Overlay implementation references and overlay-first hosts`
2. `OpenXR capability-injection, passthrough extension, and runtime-side intervention tooling`
3. `Vision-based hand and body tracking bridges`
4. `Virtual display and repurposed output workflows`
5. `OpenVR capture, replay, and orchestration toolchains`
6. `Historical utility-suite recovery`
7. `Browser panoramic video players and projection-aware web playback`
8. `Creator-side synced video player frameworks and queue frontends`
9. `Engine-side stereo panoramic viewers and vendor playback samples`
10. `Transformed, volumetric, and nonstandard 3D video viewers`
11. `Microphone control, voice-input, and audio routing helpers`
12. `Immersive media playback and browser video shells`
13. `Spatial audio SDKs, renderers, and audio-object optimization`
14. `Creator-facing audio systems and world voice management`
15. `VRChat world-authoring toolkits and optimization helpers`
16. `VRChat world runtime infrastructure and per-player state helpers`
17. `VRChat camera, staging, and admin-control systems`
18. `VRChat interaction prefabs and utility UI`
19. `VRChat world persistence, inventory, and external-data bridges`
20. `VRChat creator diagnostics, editor inspection, profiling, and static analysis`
21. `VRChat embodied interaction, custom movement, and physical world mechanics`
22. `Udon data-structure libraries, serialization helpers, and creator utility foundations`

## Current repository-maintenance priorities

Besides new research waves, the main repository-maintenance work now is:

- keep `project-registry.md` as the clear per-repository source of truth;
- keep `project-families.md` focused on synthesis instead of status ownership;
- keep `not-yet-studied-deeply.md` focused on active queueing;
- reduce archive pressure in front-door docs;
- preserve wave history without making every entry document chronological.

## If you need deeper history

For the full chronological archive, use:

- `program/README.md`
- `landscape/README.md`
- `landscape/vr-projects-master-index.md`
