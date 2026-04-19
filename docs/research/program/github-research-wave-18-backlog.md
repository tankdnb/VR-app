# GitHub Research Wave 18 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `driver learning paths`,
  `custom-device providers`, and `DIY or repurposed-display bridges`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenVR driver tutorials and sample-derived learning repos
- `Done` Search GitHub for modular custom-device providers and multi-transport driver stacks
- `Done` Search GitHub for DIY HMD and repurposed display bridges
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for the wave

## Work package B: Local source acquisition

- `Done` Confirm `terminal29/Simple-OpenVR-Driver-Tutorial` in local cache
- `Done` Confirm `LucidVR/opengloves-driver` in local cache
- `Done` Confirm `TrueOpenVR/SteamVR-TrueOpenVR` in local cache
- `Done` Confirm `DaniXmir/GlassVr` in local cache
- `Done` Confirm `r57zone/OpenVR-ArduinoHMD` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect the driver abstraction, settings path, and debugging guidance in `Simple-OpenVR-Driver-Tutorial`
- `Done` Inspect provider startup, transport configuration, and sidecar launch behavior in `opengloves-driver`
- `Done` Inspect the bridge-style single-file driver in `SteamVR-TrueOpenVR`
- `Done` Inspect the Python sidecar and OpenVR driver surfaces in `GlassVr`
- `Done` Inspect the config-driven DIY HMD path and sensor thread in `OpenVR-ArduinoHMD`

## Work package D: Repository updates

- `Done` Add Wave 18 plan document
- `Done` Add Wave 18 backlog document
- `Done` Add Wave 18 synthesis document
- `Done` Update the project registry for the newly promoted driver-learning repos
- `Done` Update overlap families for driver tutorials, custom-device providers, and repurposed-display bridges
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new driver-side and sidecar patterns
- `Done` Update documentation indexes to include Wave 18

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `Simple-OpenVR-Driver-Tutorial`, `openvr-driver-example`, and the stock `ValveSoftware/openvr` samples as one learning-track note
- `Next` Revisit `opengloves-driver` specifically around hand skeleton, force feedback, and controller-offset automation
- `Next` Revisit `GlassVr` with a tighter scope around its actual data-ingress contracts and tracking override logic
- `Next` Revisit `SteamVR-TrueOpenVR` only if the external `TrueOpenVR` standard or DLL surface becomes easier to map in public code
