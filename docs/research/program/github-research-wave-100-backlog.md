# GitHub Research Wave 100 Backlog

- Date: `2026-04-30`
- Scope: next GitHub discovery wave focused on
  `VRChat avatar setup`, `optimization`, and `Quest portability`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for avatar setup workbenches, Quest conversion helpers,
  optimizer packages, and scaling preprocessors
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning editor workbenches, mobile
  conversion, upload-time optimization, and DCC-side scaling

## Work package B: Local source acquisition

- `Done` Confirm `PumkinsAvatarTools` in local cache
- `Done` Confirm `VRCQuestTools` in local cache
- `Done` Confirm `d4rkAvatarOptimizer` in local cache
- `Done` Confirm `immersive_scaler` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect editor shell, prefs, copier infrastructure, and pose editor in
  `PumkinsAvatarTools`
- `Done` Inspect NDMF passes, validation automators, and setup windows in
  `VRCQuestTools`
- `Done` Inspect build-hook ordering, optimizer phases, shader analysis, and
  animator rewrite logic in `d4rkAvatarOptimizer`
- `Done` Inspect body-metric extraction, proportional alignment, and UI
  controls in `immersive_scaler`

## Work package D: Repository updates

- `Done` Add Wave 100 plan document
- `Done` Add Wave 100 backlog document
- `Done` Add Wave 100 synthesis document
- `Done` Update the project registry for avatar setup and optimization donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new setup, conversion, optimization,
  and scaling patterns
- `Done` Update documentation indexes to include Wave 100

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `VRCQuestTools` whenever a later pass needs a deeper map of
  its material registry, callback flow, or package-level Quest migration story
- `Next` Compare `d4rkAvatarOptimizer` with other upload-time optimizers if a
  later wave needs a sharper split between mesh-only cleanup and
  shader-aware plus animator-aware optimization
