# GitHub Research Wave 66 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `OpenVR language bindings`, `managed wrappers`, and `scripting access layers`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenVR bindings, managed wrappers, and scripting access layers
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a Rust typed wrapper, a Python `ctypes` binding, a Go `cgo` bridge, a Node native addon, and a fuller `.NET` runtime facade

## Work package B: Local source acquisition

- `Done` Confirm `rust-openvr` in local cache
- `Done` Confirm `pyopenvr` in local cache
- `Done` Confirm `openvr-go` in local cache
- `Done` Confirm `node-openvr` in local cache
- `Done` Confirm `OpenVR.NET` in local cache
- `Done` Confirm `java openvr` and `openvrsimplexamples` as surfaced comparison nodes
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect context ownership, subsystem access, and examples in `rust-openvr`
- `Done` Inspect binding generation and sample-heavy scripting surfaces in `pyopenvr`
- `Done` Inspect the `cgo` interface-loading flow in `openvr-go`
- `Done` Inspect native-addon wrapping and JS-facing argument validation in `node-openvr`
- `Done` Inspect object-oriented runtime facade, manifest helpers, and draw-input-update split in `OpenVR.NET`
- `Done` Confirm that `java-graphics/openvr` and `matinas/openvrsimplexamples` remain more useful as comparison nodes than as mainline donors in this pass

## Work package D: Repository updates

- `Done` Add Wave 66 plan document
- `Done` Add Wave 66 backlog document
- `Done` Add Wave 66 synthesis document
- `Done` Update the project registry for OpenVR bindings and wrapper donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with new OpenVR wrapper and runtime-facade methods
- `Done` Update documentation indexes to include Wave 66

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `rust-openvr` visible whenever a future branch needs a `typed wrapper over OpenVR subsystems`
- `Next` Keep `pyopenvr` visible whenever `VR-apps-lab` needs a fast scripting-side OpenVR access layer
- `Next` Revisit `openvr-go` and `node-openvr` whenever a future branch needs a stronger `bridge to another runtime` comparison
- `Next` Revisit `OpenVR.NET` whenever `VR-apps-lab` needs a broader `.NET`-first runtime facade rather than a thin binding
