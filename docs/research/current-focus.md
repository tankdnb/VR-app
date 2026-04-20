# Current Focus

- Date: `2026-04-20`
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

## Highest-value next follow-up passes

If a new research wave should start soon, these remain especially strong next
directions:

1. `Overlay implementation references and overlay-first hosts`
2. `OpenXR capability-injection, passthrough extension, and runtime-side intervention tooling`
3. `Vision-based hand and body tracking bridges`
4. `Virtual display and repurposed output workflows`
5. `OpenVR capture, replay, and orchestration toolchains`
6. `Historical utility-suite recovery`

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
