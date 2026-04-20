# GitHub Research Wave 77 Backlog

- Date: `2026-04-20`
- Scope: next GitHub discovery wave focused on
  `OpenXR helper stacks`, `layer toolchains`, and
  `runtime adaptation helpers`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenXR helper frameworks, micro-tools, and wrapper-style adaptation repos
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a layer-authoring framework, a tiny graphics wrapper, registry-edit scripts, and a post-process layer

## Work package B: Local source acquisition

- `Done` Confirm `quark` in local cache
- `Done` Confirm `rayxr` in local cache
- `Done` Confirm `openxr-layer-scripts` in local cache
- `Done` Confirm `OpenXR-CAS` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect macro-generated loader plumbing and handle registries in `quark`
- `Done` Inspect narrow graphics and session facade design in `rayxr`
- `Done` Inspect registry-state listing and edit flow in `openxr-layer-scripts`
- `Done` Inspect config precedence, live reload, and frame-end post-processing in `OpenXR-CAS`

## Work package D: Repository updates

- `Done` Add Wave 77 plan document
- `Done` Add Wave 77 backlog document
- `Done` Add Wave 77 synthesis document
- `Done` Update the project registry for OpenXR helper stacks and adaptation helpers
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new helper and toolchain patterns
- `Done` Update documentation indexes to include Wave 77

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `quark` visible as a strong `OpenXR API-layer authoring framework`
- `Next` Keep `rayxr` visible whenever `VR-apps-lab` needs a tiny `graphics-facing OpenXR facade`
- `Next` Keep `openxr-layer-scripts` visible as a Windows-specific `layer hygiene micro-tool`
- `Next` Keep `OpenXR-CAS` visible as a strong `runtime adaptation layer` donor
