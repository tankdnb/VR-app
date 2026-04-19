# VR-apps-lab

English | [Русский](README.ru.md)

`VR-apps-lab` is a public `knowledge repository`, `pattern library`, and `working
base` for building VR utilities, overlays, diagnostics tools, tracking helpers,
and experimental XR integrations.

This repo is no longer best described as one standalone VR app.

It started from a `Reality Window` prototype, but it has grown into something
more useful: a curated place where we collect studied repositories, reusable
methods, implementation patterns, prototype code, and research workflows for
future VR tools.

## What this repository is

`VR-apps-lab` combines three layers:

1. `Knowledge repository`
   - studied public VR-related repositories
   - extracted implementation methods
   - overlap families and research waves
   - backlog-driven discovery and deep-pass workflow
2. `Working foundation`
   - reusable `OpenVR` prototype code in `C# / .NET 8`
   - shared runtime and processing abstractions
   - spike apps and helper scripts
3. `Experiment archive`
   - passthrough and camera experiments
   - feasibility notes
   - dead ends that still produced useful engineering knowledge

## Who this repository is for

- VR developers looking for implementation references
- people building utilities, overlays, dashboards, and VR power-user tools
- researchers comparing public VR projects and extracting methods
- contributors who want to add new repositories in a structured way
- Russian-speaking users who need an additional entry point in Russian

## What this repository contains

- a canonical registry of tracked VR repositories
- reusable methods and product patterns for VR utility development
- landscape docs grouped by families and research waves
- a working `OpenVR` companion overlay prototype
- `PICO/OpenXR` spike apps and feasibility research
- helper scripts for repeatable GitHub research passes

## Current identity of the project

The most accurate way to describe `VR-apps-lab` today is:

- `knowledge repository for VR utility development`
- `curated research base for VR tools and overlays`
- `pattern library plus working prototypes`

What it should not promise:

- one finished end-user product
- universal passthrough support
- production-ready support for every runtime and headset

## Repository layout

```text
src/
  VRRealityWindow.Core/      shared models, providers, processing pipeline
  VRRealityWindow.OpenVr/    OpenVR runtime integration and overlay presenter
  VRRealityWindow.App/       desktop CLI app for doctor/probe/overlay

spikes/
  PicoOpenXrExtensionProbe/  Android OpenXR probe app for PICO runtime testing

scripts/
  research/                  local helper scripts for GitHub research waves

docs/
  README.md                  docs index
  README.ru.md               docs index in Russian
  foundation/                stable platform and roadmap docs
  experiments/               feasibility notes and original passthrough track
  research/                  landscape, reuse plans, registry, and templates
```

## Repository entry points

Start here:

- `AGENTS.md` for the repository operating instructions
- `README.ru.md` for the Russian-language overview
- `docs/README.md` for the English documentation index
- `docs/README.ru.md` for the Russian documentation index
- `docs/foundation/repository-positioning.md` for the public-facing repository
  identity
- `docs/foundation/current-operating-context.md` for the current handoff context
- `docs/research/program/new-session-quickstart.md` for a fresh-session reading
  path
- `docs/research/program/new-chat-prompt-block.md` for a ready-to-paste prompt
  when starting a new chat
- `docs/research/methods/vr-utility-methods-catalog.md` for reusable methods
- `docs/research/catalog/project-registry.md` for the canonical tracked-project
  list

## Working code and prototypes

The repository still includes real code and experiments.

The main code foundation currently includes:

- `OpenVR` overlay prototype code
- reusable camera/source abstractions
- frame-processing pipeline building blocks
- `PICO/OpenXR` probing experiments

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

## Best next outputs from this repository

- new VR utilities built on top of the existing foundation
- structured deep-pass research waves
- reusable methods for overlay, OpenXR layer, tracker bridge, and diagnostics
- contribution-ready public knowledge for other VR developers

## How changes are validated here

`VR-apps-lab` is not maintained like a single shipping app.

For `research` and `documentation` changes, the main quality checks are:

- repository structure stays coherent;
- links and navigation remain valid;
- registry, families, methods, and backlog stay aligned;
- the repository description stays honest about support boundaries.

For `prototype` or runnable `tool` changes, validation may also include build
checks, smoke tests, and runtime notes for the affected component.

## Documentation map

Start here:

- `README.ru.md`
- `docs/README.md`
- `docs/README.ru.md`
- `docs/foundation/repository-positioning.md`
- `docs/foundation/repository-positioning-backlog.md`
- `docs/foundation/platform-foundation.md`
- `docs/foundation/public-roadmap.md`
- `docs/research/README.md`
- `docs/research/methods/vr-utility-methods-catalog.md`
- `docs/research/landscape/project-families.md`
- `docs/research/catalog/project-registry.md`
- `docs/research/discovery/local-source-cache-workflow.md`
- `docs/research/discovery/intake-pipeline.md`
- `docs/research/discovery/watchlist.md`
- `docs/research/landscape/not-yet-studied-deeply.md`
- `docs/research/program/repository-restructuring-plan.md`
- `docs/research/program/restructuring-backlog.md`
- `docs/research/program/github-research-wave-8-plan.md`
- `docs/research/program/github-research-wave-8-backlog.md`
- `docs/research/program/github-research-wave-9-plan.md`
- `docs/research/program/github-research-wave-9-backlog.md`
- `docs/research/program/github-research-wave-10-plan.md`
- `docs/research/program/github-research-wave-10-backlog.md`
- `docs/research/program/github-research-wave-11-plan.md`
- `docs/research/program/github-research-wave-11-backlog.md`
- `docs/research/program/github-research-wave-12-plan.md`
- `docs/research/program/github-research-wave-12-backlog.md`
- `docs/research/landscape/vr-projects-master-index.md`
- `docs/research/landscape/vr-projects-wave-3-utilities.md`
- `docs/research/landscape/vr-projects-wave-4-gap-fill.md`
- `docs/research/landscape/vr-projects-wave-5-osc-tracking-tools.md`
- `docs/research/landscape/vr-projects-wave-6-driver-bridges.md`
- `docs/research/landscape/vr-projects-wave-7-depth-pass.md`
- `docs/research/landscape/vr-projects-wave-8-github-source-pass.md`
- `docs/research/landscape/vr-projects-wave-9-runtime-overlay-devtools.md`
- `docs/research/landscape/vr-projects-wave-10-runtime-bridge-and-headsetless-tools.md`
- `docs/research/landscape/vr-projects-wave-11-runtime-adapters-virtual-displays-and-validation.md`
- `docs/research/landscape/vr-projects-wave-12-synthetic-devices-input-emulation-and-diy-driver-paths.md`

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
