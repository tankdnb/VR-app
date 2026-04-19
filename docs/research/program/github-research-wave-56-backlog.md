# GitHub Research Wave 56 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `browser-backed overlay runtimes`, `web-tech hosts`, and
  `UI runtime experiments`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for browser-backed overlay hosts, webview-driven overlay stacks, and `UI runtime -> OpenVR texture` experiments
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans native backend plus web runtime, offscreen browser mirroring, daemon-backed overlay hosts, and Compose-style UI experimentation

## Work package B: Local source acquisition

- `Done` Confirm `ovrsalt` in local cache
- `Done` Confirm `electron-openvr` in local cache
- `Done` Confirm `ovrly` in local cache
- `Done` Confirm `ComposeVR` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect backend, runtime, and frontend split in `ovrsalt`
- `Done` Inspect offscreen `BrowserWindow`, frame capture, and texture submit path in `electron-openvr`
- `Done` Inspect browser host, per-app daemon model, and in-page API bridge in `ovrly`
- `Done` Inspect `Compose`, `Skia`, `GLFW`, and `OpenVR` integration boundaries in `ComposeVR`

## Work package D: Repository updates

- `Done` Add Wave 56 plan document
- `Done` Add Wave 56 backlog document
- `Done` Add Wave 56 synthesis document
- `Done` Update the project registry for browser-backed overlay runtimes and web-tech hosts
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with browser-host and `UI runtime -> overlay texture` methods
- `Done` Update documentation indexes to include Wave 56

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `ovrsalt` visible whenever a future branch needs a clearer `native backend + web runtime + local IPC` donor
- `Next` Keep `ovrly` visible whenever a future branch needs `overlay host with per-app daemons` rather than one monolithic app
- `Next` Revisit `ComposeVR` only if a future branch needs a deeper `Kotlin or Compose overlay runtime` comparison
