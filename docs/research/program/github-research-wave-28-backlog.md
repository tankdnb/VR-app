# GitHub Research Wave 28 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `text entry`,
  `tracked keyboards`, and `non-native input surfaces`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for spatial, non-native, tracked, and hand-tracking keyboard projects
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that keeps `synthetic`, `tracked physical`, and `hand-driven` keyboards in the same comparison set
- `Done` Reject broader UI repos that do not materially teach keyboard-specific input patterns

## Work package B: Local source acquisition

- `Done` Confirm `VRKeys` in local cache
- `Done` Confirm `XR-Keyboard` in local cache
- `Done` Confirm `Unity-TrackedKeyboard` in local cache
- `Done` Confirm `MRTK-Keyboard` in local cache
- `Done` Confirm `Oculus-HandTracking-Keyboard` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect lifecycle, layout switching, validation surfaces, and hand attachment flow in `VRKeys`
- `Done` Inspect prefab generation, keymap, and runtime spawn logic in `XR-Keyboard`
- `Done` Inspect tracked-device management, visibility gating, and MR keyboard UX in `Unity-TrackedKeyboard`
- `Done` Inspect non-native keyboard events, placement model, and semantic layouts in `MRTK-Keyboard`
- `Done` Inspect fingertip-driven typing model and minimal hand-tracking keyboard flow in `Oculus-HandTracking-Keyboard`

## Work package D: Repository updates

- `Done` Add Wave 28 plan document
- `Done` Add Wave 28 backlog document
- `Done` Add Wave 28 synthesis document
- `Done` Update the project registry for the new keyboard and text-entry donors
- `Done` Update overlap families for keyboard and text-entry surfaces
- `Done` Update the methods catalog with keyboard-oriented utility methods
- `Done` Update documentation indexes to include Wave 28

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `VRKeys`, `XR-Keyboard`, and `MRTK-Keyboard` directly as `toolkit prefab`, `physical keyboard generator`, and `semantic non-native keyboard` approaches
- `Next` Revisit tracked physical keyboard flows only when a later wave needs deeper desk, passthrough, or mixed-reality input research
