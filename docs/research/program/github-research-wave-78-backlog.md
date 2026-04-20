# GitHub Research Wave 78 Backlog

- Date: `2026-04-20`
- Scope: next GitHub discovery wave focused on
  `OpenXR passthrough samples` and
  `engine-side extension integration references`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for engine-side OpenXR passthrough samples across Unreal, Godot, and Unity
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a UE plugin, a very small Godot sample, and a broader Unity example project

## Work package B: Local source acquisition

- `Done` Confirm `ue-openxr-passthrough` in local cache
- `Done` Confirm `godot_test_passthrough` in local cache
- `Done` Confirm `mr-openxr-unity-meta-passthrough-sample` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect module registration, optional extension negotiation, and layer insertion in `ue-openxr-passthrough`
- `Done` Inspect transparent viewport handling and OpenXR interface toggling in `godot_test_passthrough`
- `Done` Inspect runtime manager, diagnostics, and editor setup helpers in `mr-openxr-unity-meta-passthrough-sample`

## Work package D: Repository updates

- `Done` Add Wave 78 plan document
- `Done` Add Wave 78 backlog document
- `Done` Add Wave 78 synthesis document
- `Done` Update the project registry for engine-side passthrough references
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new engine-integration patterns
- `Done` Update documentation indexes to include Wave 78

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `ue-openxr-passthrough` visible as a strong `engine-native extension plugin` donor
- `Next` Keep `godot_test_passthrough` visible as a tiny `runtime toggle plus transparent viewport` reference
- `Next` Keep `mr-openxr-unity-meta-passthrough-sample` visible for future follow-up on `editor bootstrap plus runtime diagnostics`
