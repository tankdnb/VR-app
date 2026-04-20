# GitHub Research Wave 76 Backlog

- Date: `2026-04-20`
- Scope: next GitHub discovery wave focused on
  `OpenXR capability-injection layers`, `input remappers`, and
  `peripheral extension bridges`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenXR capability-injection, hand-tracking, and remapping layers
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans an archived hand-tracking layer, an input-remapping layer, and a tiny Rust capability-layer skeleton

## Work package B: Local source acquisition

- `Done` Confirm `OpenXRHandTracking` in local cache
- `Done` Confirm `openxr_remapping_layer` in local cache
- `Done` Confirm `OpenXR_ApiLayer_Patstrap` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect archived extension-injection behavior and operator configuration in `OpenXRHandTracking`
- `Done` Inspect runtime detection, wrapper registries, and SuInput ownership in `openxr_remapping_layer`
- `Done` Inspect loader-negotiation baseline and forwarding skeleton in `OpenXR_ApiLayer_Patstrap`

## Work package D: Repository updates

- `Done` Add Wave 76 plan document
- `Done` Add Wave 76 backlog document
- `Done` Add Wave 76 synthesis document
- `Done` Update the project registry for OpenXR capability and remapping layers
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new OpenXR layer patterns
- `Done` Update documentation indexes to include Wave 76

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `OpenXRHandTracking` visible as a strong `capability-injection` product reference even though the public snapshot is source-thin
- `Next` Keep `openxr_remapping_layer` visible whenever `VR-apps-lab` needs an `input remapping OpenXR layer` donor
- `Next` Keep `OpenXR_ApiLayer_Patstrap` visible as a lower-bound `Rust API-layer skeleton` baseline
