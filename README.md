# VR.app

`VR.app` is a foundation repository for building practical VR utilities,
overlays, diagnostics tools, and experimental runtime integrations.

The project started as a `Reality Window` MVP for showing camera-backed
real-world content inside VR. That original direction produced useful code,
research, and clear technical findings, even though the `Pico Connect +
onboard-camera passthrough` path did not prove viable for the target headset.

Instead of throwing that work away, this repository now serves as the shared
base for future VR tools.

## What this repository contains

- A working `OpenVR` companion overlay prototype in `C# / .NET 8`
- Reusable abstractions for camera sources and frame processing
- A `PICO/OpenXR` spike app used to probe passthrough and extension support
- Research notes on SteamVR, OpenXR, overlays, passthrough, performance, and
  VR utility products

## Current status

What is already proven:

- Desktop `OpenVR` overlays work on the target setup
- World-locked and hand-locked overlay behavior is viable
- A reusable frame-processing pipeline is in place
- `PICO` OpenXR runtime probing works on-device

What is not proven:

- `Pico Connect` access to the headset's onboard camera feed
- A production passthrough path that works during active PCVR streaming

Current product direction:

- Treat this repo as a base for `VR utility overlays`, `wrist dashboards`,
  `desktop/reference windows`, `metrics tools`, `tracking helpers`, and other
  VR power-user utilities

## Repository layout

```text
src/
  VRRealityWindow.Core/      shared models, providers, processing pipeline
  VRRealityWindow.OpenVr/    OpenVR runtime integration and overlay presenter
  VRRealityWindow.App/       desktop CLI app for doctor/probe/overlay

spikes/
  PicoOpenXrExtensionProbe/  Android OpenXR probe app for PICO runtime testing

docs/
  README.md                  docs index
  foundation/                stable platform and roadmap docs
  experiments/               feasibility notes and original passthrough track
  research/                  landscape, reuse plans, registry, and templates
```

## Desktop app commands

From the repository root:

```powershell
dotnet build .\VRRealityWindowMvp.sln
dotnet run --project .\src\VRRealityWindow.App -- doctor
dotnet run --project .\src\VRRealityWindow.App -- probe --source test-pattern
dotnet run --project .\src\VRRealityWindow.App -- overlay --source test-pattern
```

Useful variants:

```powershell
dotnet run --project .\src\VRRealityWindow.App -- doctor --target-headset pico-4-pro
dotnet run --project .\src\VRRealityWindow.App -- probe --source tracked-camera
dotnet run --project .\src\VRRealityWindow.App -- overlay --anchor left-hand
dotnet run --project .\src\VRRealityWindow.App -- overlay --duration-seconds 20
```

## Reusable building blocks

- `ICameraProvider` abstraction for interchangeable video sources
- `FrameProcessingPipeline` for CPU-side processing and future GPU upgrades
- `OpenVrOverlayPresenter` for world-space utility windows
- JSON settings and experiment configuration
- `PicoOpenXrExtensionProbe` for Android/OpenXR capability discovery

## Best next products from this foundation

- `VR Utility Overlay Suite`
- `Wrist Dashboard / quick actions panel`
- `Reference windows for work in VR`
- `VR diagnostics and device metrics`
- `Tracking / calibration helpers`
- `External-camera reality tools`

## Documentation map

Start here:

- `docs/README.md`
- `docs/foundation/platform-foundation.md`
- `docs/foundation/public-roadmap.md`
- `docs/research/README.md`
- `docs/research/landscape/project-families.md`
- `docs/research/catalog/project-registry.md`
- `docs/research/landscape/not-yet-studied-deeply.md`
- `docs/research/program/repository-restructuring-plan.md`
- `docs/research/program/restructuring-backlog.md`
- `docs/research/landscape/vr-projects-master-index.md`
- `docs/research/landscape/vr-projects-wave-3-utilities.md`
- `docs/research/landscape/vr-projects-wave-4-gap-fill.md`
- `docs/research/landscape/vr-projects-wave-5-osc-tracking-tools.md`
- `docs/research/landscape/vr-projects-wave-6-driver-bridges.md`
- `docs/research/landscape/vr-projects-wave-7-depth-pass.md`

Original Reality Window and passthrough research:

- `docs/experiments/reality-window/overlay-vr-mvp-spec.md`
- `docs/experiments/reality-window/current-feasibility-status.md`
- `docs/experiments/reality-window/pico-openxr-camera-path.md`
- `docs/experiments/reality-window/pico-connect-constraint.md`
- `docs/experiments/reality-window/pico-connect-passthrough-spike.md`

Landscape and reuse research:

- `docs/research/landscape/vr-utilities-repo-landscape.md`
- `docs/research/reuse/openxr-steamvr-passthrough-reuse-plan.md`
- `docs/research/reuse/alvr-reuse-plan.md`
- `docs/research/reuse/openvr-advancedsettings-reuse-plan.md`
- `docs/research/reuse/vrperfkit-reuse-plan.md`
- `docs/research/reuse/external-repos-reuse-plan.md`

## Notes on licensing

This repository is released under `MIT`, with third-party notices documented in
`THIRD_PARTY_NOTICES.md`. Vendored SDK files keep their original notices.
