# GitHub Research Wave 99 Backlog

- Date: `2026-04-27`
- Scope: next GitHub discovery wave focused on
  `VRChat world control gadgets`, `environmental systems`, and
  `specialized operator surfaces`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for creator-world control surfaces, day-night systems,
  depth-buffer helpers, and stage-lighting packages
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning render fixups, large operator
  panels, synced environment control, and keypad access surfaces

## Work package B: Local source acquisition

- `Done` Confirm `VUdon-DepthBufferToolkit` in local cache
- `Done` Confirm `VR-Stage-Lighting` in local cache
- `Done` Confirm `UdonSharpDayNightController` in local cache
- `Done` Confirm `VRChat_Keypad` in local cache
- `Done` Confirm `UdonKeypad` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect editor setup, build post-process, and runtime activators in
  `VUdon-DepthBufferToolkit`
- `Done` Inspect local operator panel, DMX grid reader, camera configurator,
  and patch-export tooling in `VR-Stage-Lighting`
- `Done` Inspect synced time and local override flow in
  `UdonSharpDayNightController`
- `Done` Inspect passcode, object-control, and callback routing in
  `VRChat_Keypad`
- `Done` Inspect single-component keypad and access-gating flow in
  `UdonKeypad`

## Work package D: Repository updates

- `Done` Add Wave 99 plan document
- `Done` Add Wave 99 backlog document
- `Done` Add Wave 99 synthesis document
- `Done` Update the project registry for world-control and operator-surface
  donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new render-fixup, operator-surface,
  environment, and keypad patterns
- `Done` Update documentation indexes to include Wave 99

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `VR-Stage-Lighting` if a future pass needs a deeper map of
  its DMX fixture model, shader families, or patch format ecosystem
- `Next` Compare `VRChat_Keypad` and `UdonKeypad` whenever future work needs a
  sharper choice between
  `multi-code routed keypad`
  and
  `compact drag-and-drop keypad`
