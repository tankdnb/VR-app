# GitHub Research Wave 98 Backlog

- Date: `2026-04-27`
- Scope: next GitHub discovery wave focused on
  `Udon sync`, `event dispatch`, `runtime logging`, and
  `shared helper micro-frameworks`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for Udon event, networking, logging, and sync helper
  repositories
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning build-time event routing,
  parameterized networking, sync substrate, and runtime diagnostics

## Work package B: Local source acquisition

- `Done` Confirm `VUdon-Events` in local cache
- `Done` Confirm `UdonSharpNetworkingLib` in local cache
- `Done` Confirm `LightSync` in local cache
- `Done` Confirm `VUdon-Logger` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect build-time resolver and runtime dispatch flow in
  `VUdon-Events`
- `Done` Inspect compile patch, serializer, and RPC surface in
  `UdonSharpNetworkingLib`
- `Done` Inspect state model and setup helpers in `LightSync`
- `Done` Inspect logger abstraction and in-world console implementation in
  `VUdon-Logger`

## Work package D: Repository updates

- `Done` Add Wave 98 plan document
- `Done` Add Wave 98 backlog document
- `Done` Add Wave 98 synthesis document
- `Done` Update the project registry for runtime helper framework donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new dispatch, networking, and logging
  patterns
- `Done` Update documentation indexes to include Wave 98

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `LightSync` only if a future pass needs a broader
  `custom synced-object state-machine`
  lineage map, ideally together with `SmartObjectSync`
- `Next` Revisit `VUdon-Events` and `UdonSharpNetworkingLib` whenever future
  creator-runtime work needs a sharper split between
  `serialized event routing`
  and
  `parameterized network RPC`
