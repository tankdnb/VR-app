# GitHub Research Wave 21 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `OpenXR provider stacks`,
  `gaze API layers`, and `runtime-side utility platforms`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenXR wrapper libraries with sandbox or sample executables
- `Done` Search GitHub for OpenXR eye-tracking and foveation API-layer projects
- `Done` Search GitHub for runtime-side service hosts and utility platforms with registration or plugin boundaries
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record `BattleAxeVR/PSVR2_OpenXR_Eye_Tracking` and `LordOfDragons/openxr_oscclient` as follow-up signals instead of over-expanding the wave

## Work package B: Local source acquisition

- `Done` Confirm `1runeberg/OpenXRProvider` in local cache
- `Done` Confirm `mbucchia/Quad-Views-Foveated` in local cache
- `Done` Confirm `mbucchia/OpenXR-Eye-Trackers` in local cache
- `Done` Confirm `clear-xr/clearxr-server` in local cache
- `Done` Confirm `vrkit-platform/vrkit-platform` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect wrapper, sandbox, and input-profile structure in `OpenXRProvider`
- `Done` Inspect extension adaptation and config gating in `Quad-Views-Foveated`
- `Done` Inspect backend fan-in and runtime-facing gaze adaptation in `OpenXR-Eye-Trackers`
- `Done` Inspect layer and service-host split in `clearxr-server`
- `Done` Inspect manifest, plugin, and overlay-surface signals in `vrkit-platform`

## Work package D: Repository updates

- `Done` Add Wave 21 plan document
- `Done` Add Wave 21 backlog document
- `Done` Add Wave 21 synthesis document
- `Done` Update the project registry for the newly clarified OpenXR provider and gaze-layer repos
- `Done` Update overlap families for OpenXR runtime and layer tooling
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new or sharpened OpenXR adaptation methods
- `Done` Update documentation indexes to include Wave 21

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `clear-xr/clearxr-server` with a tighter scope around layer ownership, controller-fix boundaries, and service orchestration
- `Next` Revisit `vrkit-platform/vrkit-platform` only if the public snapshot becomes less scope-shifted and reveals a clearer OpenXR utility core
- `Next` Compare `OpenXR-Eye-Trackers` and `Quad-Views-Foveated` as one `sensor adaptation layer vs rendering adaptation layer` story
- `Next` Inspect `BattleAxeVR/PSVR2_OpenXR_Eye_Tracking` and `LordOfDragons/openxr_oscclient` if the gaze-layer family expands further
