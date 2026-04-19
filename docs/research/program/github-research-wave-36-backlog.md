# GitHub Research Wave 36 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `runtime-side service hosts`,
  `broader OpenXR utility platforms`, and `layer diagnostics and fixers`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenXR service hosts, layer-management tools, and broader runtime utility platforms
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans service hosts, plugin-shaped utility platforms, runtime explorers, and fix-oriented layer tools
- `Done` Keep the wave centered on OpenXR runtime tooling instead of diluting it with generic templates or samples

## Work package B: Local source acquisition

- `Done` Confirm `clearxr-server` in local cache
- `Done` Confirm `vrkit-platform` in local cache
- `Done` Confirm `openxr-explorer` in local cache
- `Done` Confirm `OpenXR-API-Layers-GUI` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect service-host, landing-space, and API-layer boundaries in `clearxr-server`
- `Done` Inspect Electron shell, plugin manager, and native overlay-manager boundaries in `vrkit-platform`
- `Done` Inspect runtime enumeration, manifest parsing, and GUI or CLI parity in `openxr-explorer`
- `Done` Inspect lint-rule, fix-object, and layer-store boundaries in `OpenXR-API-Layers-GUI`

## Work package D: Repository updates

- `Done` Add Wave 36 plan document
- `Done` Add Wave 36 backlog document
- `Done` Add Wave 36 synthesis document
- `Done` Update the project registry for the strengthened OpenXR runtime-platform donors
- `Done` Update overlap families for runtime service hosts and layer doctoring
- `Done` Update `not-yet-studied-deeply.md` with the honest remaining follow-up nodes
- `Done` Update the methods catalog with runtime-platform methods
- `Done` Update documentation indexes to include Wave 36

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `vrkit-platform` with a narrower future pass on plugin manifests, native overlay interop, and actual OpenXR integration boundaries
- `Next` Compare `clearxr-server`, `vrkit-platform`, `openxr-explorer`, and `OpenXR-API-Layers-GUI` directly as `service host`, `plugin platform`, `runtime explorer`, and `fixable layer doctor`
