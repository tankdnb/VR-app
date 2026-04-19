# GitHub Research Wave 25 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `headsetless QA runtimes`,
  `null-driver helpers`, and `virtual device simulators`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for SteamVR no-headset recipes and helper tools
- `Done` Search GitHub for virtual HMD and fake-device drivers
- `Done` Search GitHub for OpenXR runtime simulators and simulator-side control surfaces
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Keep `davidrios/openxr-device-simulator` as a thinner follow-up node instead of over-expanding the wave

## Work package B: Local source acquisition

- `Done` Confirm `SteamVRNoHeadset` in local cache
- `Done` Confirm `ViveTrackerExample` in local cache
- `Done` Confirm `VirtualSteamVRDriver` in local cache
- `Done` Confirm `OpenXR-Simulator` in local cache
- `Done` Confirm `SteamVRNullFlipper` in local cache
- `Done` Confirm `OpenDisplayXR-VDD` in local cache
- `Done` Confirm `aethervr` in local cache
- `Done` Confirm `ox-sim-driver` in local cache
- `Done` Confirm `openxr-device-simulator` in local cache as a comparison node
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect the null-driver recipe surface in `SteamVRNoHeadset`
- `Done` Inspect the tracker-without-HMD workflow framing in `ViveTrackerExample`
- `Done` Inspect virtual HMD driver structure and configuration in `VirtualSteamVRDriver`
- `Done` Inspect runtime bring-up, input simulation, and registration scripts in `OpenXR-Simulator`
- `Done` Inspect config-backup and mode-swap behavior in `SteamVRNullFlipper`
- `Done` Inspect the current visible source signal in `OpenDisplayXR-VDD`
- `Done` Inspect custom runtime plus Python-tracker split in `aethervr`
- `Done` Inspect GUI plus external-control simulator design in `ox-sim-driver`

## Work package D: Repository updates

- `Done` Add Wave 25 plan document
- `Done` Add Wave 25 backlog document
- `Done` Add Wave 25 synthesis document
- `Done` Update the project registry for newly clarified headsetless and simulator repos
- `Done` Update overlap families for OpenXR simulators, no-HMD helpers, and camera runtimes
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new headsetless-QA and simulator methods
- `Done` Update documentation indexes to include Wave 25

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `openxr-device-simulator` if its public docs and runtime surface grow beyond the current thin snapshot
- `Next` Revisit `OpenDisplayXR-VDD` only when there is stronger visible source or documentation to compare with the richer simulator and virtual-display donors
- `Next` Compare `OpenXR-Simulator`, `ox-sim-driver`, and `aethervr` directly as `desktop simulator runtime`, `automation-friendly simulator`, and `camera-driven custom runtime`
