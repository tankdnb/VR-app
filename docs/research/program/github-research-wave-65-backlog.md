# GitHub Research Wave 65 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `OpenXR language bindings`, `generator-backed wrappers`, and `SDK facades`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenXR bindings, wrapper generators, and language-level facades
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a Rust safe-plus-raw stack, a generated Python facade, a `.NET` binding generator, and a Zig build-integrated wrapper

## Work package B: Local source acquisition

- `Done` Confirm `openxrs` in local cache
- `Done` Confirm `pyopenxr` in local cache
- `Done` Confirm `OpenXR.NET` in local cache
- `Done` Confirm `openxr-zig` in local cache
- `Done` Confirm `openxr.py` and `rlOpenXR` as surfaced comparison nodes
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect the safe wrapper, raw `sys` layer, and loader-negotiation split in `openxrs`
- `Done` Inspect the generator flow, packaged loader handling, and optional Python API-layer helper in `pyopenxr`
- `Done` Inspect the registry-driven C# generator and proc-address fallback flow in `OpenXR.NET`
- `Done` Inspect the build-integrated codegen flow and generated Zig wrapper surface in `openxr-zig`
- `Done` Confirm that `openxr.py` and `rlOpenXR` remain more useful as comparison nodes than as mainline donors in this pass

## Work package D: Repository updates

- `Done` Add Wave 65 plan document
- `Done` Add Wave 65 backlog document
- `Done` Add Wave 65 synthesis document
- `Done` Update the project registry for OpenXR bindings and wrapper-generation donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with new binding-generation and API-facade methods
- `Done` Update documentation indexes to include Wave 65

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `openxrs` visible whenever a future branch needs a `safe + raw OpenXR stack` reference
- `Next` Keep `pyopenxr` visible whenever a future branch needs a `generated scripting facade` or Python-side API-layer helper
- `Next` Revisit `OpenXR.NET` whenever `VR-apps-lab` needs a stronger `.NET`-first OpenXR donor
- `Next` Revisit `openxr-zig` whenever a future branch needs `build-integrated code generation` rather than a pre-generated binding package
