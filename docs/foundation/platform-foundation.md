# VR.app Platform Foundation

## Purpose

`VR.app` is a public knowledge repository and reusable foundation for VR
utility development, not a single one-off prototype.

The repository keeps the original `Reality Window` work, but now treats it as a
technical seed that produced:

- a working overlay runtime path;
- reusable camera and processing abstractions;
- a PICO/OpenXR probing workflow;
- a large body of architecture, product, and repository research.

## Core design principles

1. Preserve and structure knowledge, not only code.
2. Build reusable infrastructure before niche UX.
3. Keep runtime-specific integration isolated behind clear interfaces.
4. Favor practical utility tools that can ship on current hardware.
5. Preserve experiments and findings, even when a product hypothesis fails.
6. Design around overlays, diagnostics, and control surfaces first.

## Reusable capabilities already in repo

### Desktop OpenVR foundation

- overlay lifecycle management
- world-locked and hand-locked placement
- basic controller-driven interaction
- desktop-side diagnostics via `doctor`, `probe`, and `overlay`

### Shared core layer

- source/provider abstraction via `ICameraProvider`
- shared frame model and status reporting
- CPU-side frame processing pipeline
- JSON-backed settings model

### Android OpenXR spike infrastructure

- Android project structure for standalone headset testing
- OpenXR extension probing on PICO hardware
- a repeatable path for testing runtime capabilities before product investment

## What this repo should become

The repository is best suited to become:

- a durable knowledge base for VR utility development;
- a pattern library for overlays, bridges, diagnostics, and helpers;
- a working prototype foundation for future VR tools.

The most natural utility directions inside that frame are:

- wrist dashboards
- quick action panels
- desktop/reference windows in VR
- device metrics overlays
- tracking and calibration helpers
- external-camera and mixed-reality experiments
- developer diagnostics tools

## What this repo should not promise

Right now the repository should not promise:

- that it is one finished application;
- universal passthrough access across all headsets
- raw camera access from `Pico Connect`
- production-ready mixed reality
- vendor-independent headset camera support

These remain research areas, not shipped capabilities.

## Recommended architecture direction

Short term:

- `OpenVR companion overlay` architecture for useful SteamVR tools

Medium term:

- `OpenXR runtime/app-layer` experiments for headset-native utilities

Long term:

- selected runtime integrations or API-layer work where device support is real

## Product evaluation filter

Before starting a new utility in this repo, ask:

1. Does it reuse the current overlay/runtime foundation?
2. Can it work on real hardware without vendor-locked hidden APIs?
3. Is it useful even without passthrough?
4. Can it be validated in a small MVP?

If the answer is mostly yes, it is a good candidate for this repository.
