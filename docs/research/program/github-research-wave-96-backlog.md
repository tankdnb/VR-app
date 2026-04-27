# GitHub Research Wave 96 Backlog

- Date: `2026-04-27`
- Scope: next GitHub discovery wave focused on
  `VRChat creator starter baselines`, `test harnesses`, and
  `language-boundary experiments`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for VRChat templates, Udon test helpers, and unusual
  UdonSharp codegen experiments
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning official templates, historical
  template lineage, creator testing, and language-boundary code generation

## Work package B: Local source acquisition

- `Done` Confirm `template-world` in local cache
- `Done` Confirm `template-udonsharp` in local cache
- `Done` Confirm `udon-test` in local cache
- `Done` Confirm `wasm2usharp` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect editor bootstrap and package-restoration flow in
  `template-world`
- `Done` Inspect deprecated-template lineage in `template-udonsharp`
- `Done` Inspect assertion surface and equality handling in `udon-test`
- `Done` Inspect Wasm validation, IR, and UdonSharp code generation in
  `wasm2usharp`

## Work package D: Repository updates

- `Done` Add Wave 96 plan document
- `Done` Add Wave 96 backlog document
- `Done` Add Wave 96 synthesis document
- `Done` Update the project registry for creator starter, test, and codegen
  donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new bootstrap, testing, and codegen
  patterns
- `Done` Update documentation indexes to include Wave 96

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `template-world` if a future pass needs a stronger
  `official creator bootstrap lineage` map
- `Next` Keep `template-udonsharp` visible as a migration or historical-variant
  node rather than a mainline donor
- `Next` Revisit `wasm2usharp` whenever a future pass needs a stronger
  `non-C# to creator-world codegen`
  comparison line
