# GitHub Research Wave 38 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `SteamVR validation helpers`,
  `config patchers`, and `environment-hygiene micro-tools`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for SteamVR manifest validators, focused patchers, and startup hygiene helpers
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans CLI validation, one-shot JSON patching, prelaunch config toggling, and a continuous runtime feedback helper
- `Done` Keep `SteamVRNoHeadset` and `SteamVRNullFlipper` as comparison nodes instead of diluting the mainline shortlist

## Work package B: Local source acquisition

- `Done` Confirm `SteamVR-ActionsManifestValidator` in local cache
- `Done` Confirm `Lighthouse-Scale-Fix` in local cache
- `Done` Confirm `steamvr-exconfig` in local cache
- `Done` Confirm `SteamVRAdaptiveBrightness` in local cache
- `Done` Confirm comparison metadata for `SteamVRNoHeadset` and `SteamVRNullFlipper`
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect duplicate-key rejection and disableable warning gates in `SteamVR-ActionsManifestValidator`
- `Done` Inspect backup-safe one-shot JSON rewrite flow in `Lighthouse-Scale-Fix`
- `Done` Inspect external config loading, toggle lists, and save flow in `steamvr-exconfig`
- `Done` Inspect mirror-texture analysis and continuous `analogGain` rewrite flow in `SteamVRAdaptiveBrightness`

## Work package D: Repository updates

- `Done` Add Wave 38 plan document
- `Done` Add Wave 38 backlog document
- `Done` Add Wave 38 synthesis document
- `Done` Update the project registry for the stronger workflow micro-tool synthesis
- `Done` Update overlap families for validation and environment-hygiene tools
- `Done` Update `not-yet-studied-deeply.md` with the honest follow-up nodes
- `Done` Update the methods catalog with workflow-helper methods
- `Done` Update documentation indexes to include Wave 38

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `SteamVRNoHeadset` and `SteamVRNullFlipper` visible as the closest comparison nodes for null-driver mode flips and no-HMD workflows
- `Next` Compare `SteamVR-ActionsManifestValidator`, `Lighthouse-Scale-Fix`, `steamvr-exconfig`, and `SteamVRAdaptiveBrightness` directly as `linter`, `one-shot patcher`, `prelaunch toggler`, and `continuous runtime feedback helper`
