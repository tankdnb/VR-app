# GitHub Research Wave 17 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `OpenXR runtime managers`,
  `experimental API layers`, and `runtime-side service hosts`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for runtime-manager utilities and registry-based switchers
- `Done` Search GitHub for experimental OpenXR overlay-layer and API-layer repos
- `Done` Search GitHub for runtime-side service and registration hosts
- `Done` Deduplicate all results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record `vrkit-platform/vrkit-platform` as a follow-up node instead of forcing it into the core wave

## Work package B: Local source acquisition

- `Done` Confirm `PlutoVR/OpenXR-OverlayLayer-1` in local cache
- `Done` Confirm `Ybalrid/OpenXR-Runtime-Manager` in local cache
- `Done` Confirm `pembem22/etvr-openxr-layer` in local cache
- `Done` Confirm `clear-xr/clearxr-server` in local cache
- `Done` Confirm `vrkit-platform/vrkit-platform` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect the remote overlay client and API-layer split in `OpenXR-OverlayLayer-1`
- `Done` Inspect registry probing and well-known runtime discovery in `OpenXR-Runtime-Manager`
- `Done` Inspect negotiation entrypoints and OSC-backed eye-gaze injection in `etvr-openxr-layer`
- `Done` Inspect runtime registration helpers, Tauri host structure, and OpenXR layer boundaries in `clearxr-server`
- `Done` Inspect `vrkit-platform` far enough to keep it as a scope-mismatched follow-up node instead of a promoted mainline donor

## Work package D: Repository updates

- `Done` Add Wave 17 plan document
- `Done` Add Wave 17 backlog document
- `Done` Add Wave 17 synthesis document
- `Done` Update the project registry for the newly promoted runtime and layer repos
- `Done` Update overlap families for runtime managers, API layers, and runtime-side service hosts
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new runtime and API-layer methods
- `Done` Update documentation indexes to include Wave 17

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `PlutoVR/OpenXR-OverlayLayer-1` and `LunarG/OpenXR-OverlayLayer` directly as one `remote overlay session via API layer` lineage
- `Next` Compare `Ybalrid/OpenXR-Runtime-Manager`, `xr-picker`, and `openxr-explorer` as one `registry-plus-probe runtime switcher` family
- `Next` Revisit `clear-xr/clearxr-server` with a tighter scope around `clearxr-layer` and runtime registration only
- `Next` Revisit `vrkit-platform/vrkit-platform` only after confirming the current public snapshot again exposes meaningful OpenXR utility logic
