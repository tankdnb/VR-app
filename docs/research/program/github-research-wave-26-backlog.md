# GitHub Research Wave 26 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `vendor IPC ecosystems`,
  `glasses bridges`, and `official-stack enhancement tools`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for PSVR2 enhancement tooling and toolkit-adjacent modules
- `Done` Search GitHub for glasses-to-SteamVR bridge drivers and SDK-first bridge stacks
- `Done` Search GitHub for narrow downstream tools built on vendor IPC contracts
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Keep `PSVR2Toolkit-Lite` and `PSVR2EyeTrackingCalibration` as secondary nodes instead of widening the wave too far

## Work package B: Local source acquisition

- `Done` Confirm `PSVR2Toolkit` in local cache
- `Done` Confirm `PSVR2Toolkit.VRCFT` in local cache
- `Done` Confirm `PSVR2ToolkitTriggerConfig` in local cache
- `Done` Confirm `ResonitePSVR2` in local cache
- `Done` Confirm `RayNeo-Air-3S-Pro-OpenVR` in local cache
- `Done` Confirm `RayNeo-Air-3S-Pro-OpenVR-Driver` in local cache
- `Done` Confirm `GlassVr` in local cache
- `Done` Confirm the secondary comparison nodes in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect hook, proxy, and IPC boundaries in `PSVR2Toolkit`
- `Done` Inspect vendor-IPC consumer shape in `PSVR2Toolkit.VRCFT`
- `Done` Inspect focused trigger-configuration helper flow in `PSVR2ToolkitTriggerConfig`
- `Done` Inspect downstream engine-mod integration in `ResonitePSVR2`
- `Done` Inspect SDK-first bridge and old driver split in `RayNeo-Air-3S-Pro-OpenVR`
- `Done` Inspect the dedicated driver repo and input-profile work in `RayNeo-Air-3S-Pro-OpenVR-Driver`
- `Done` Inspect sidecar plus emulation-driver structure in `GlassVr`

## Work package D: Repository updates

- `Done` Add Wave 26 plan document
- `Done` Add Wave 26 backlog document
- `Done` Add Wave 26 synthesis document
- `Done` Update the project registry for the newly clarified vendor and glasses repos
- `Done` Update overlap families for vendor IPC ecosystems and glasses bridges
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new vendor-IPC and enhancement methods
- `Done` Update documentation indexes to include Wave 26

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `PSVR2EyeTrackingCalibration` together with broader PSVR2-specific OpenXR eye-tracking work if that branch becomes its own wave
- `Next` Keep `PSVR2Toolkit-Lite` as a variant node only unless it unexpectedly grows beyond its deprecated state
- `Next` Compare `PSVR2Toolkit`, `RayNeo-Air-3S-Pro-OpenVR`, and `GlassVr` directly as `vendor wrapper`, `SDK-first bridge`, and `sidecar-driven emulation bridge`
