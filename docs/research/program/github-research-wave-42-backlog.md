# GitHub Research Wave 42 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `XR-glasses virtual-display stacks`, `workspace shells`, and
  `spatial screen utilities`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for XR-glasses drivers, workspace shells, and special-display utilities
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a base driver, a workspace shell, a game-mode plugin wrapper, a Rust virtual-display stack, and head-tracked screen utilities
- `Done` Keep `Virtual-Display-Driver` as an already-tracked comparison node instead of replacing the more specialized glasses-oriented donors

## Work package B: Local source acquisition

- `Done` Confirm `XRLinuxDriver` in local cache
- `Done` Confirm `breezy-desktop` in local cache
- `Done` Confirm `decky-XRGaming` in local cache
- `Done` Confirm `virtual-display-rs` in local cache
- `Done` Confirm `viture_virtual_display` in local cache
- `Done` Confirm `desktop2stereo` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect backend hooks, feature flags, and device abstraction in `XRLinuxDriver`
- `Done` Inspect workspace-shell boundaries and Vulkan-mode split in `breezy-desktop`
- `Done` Inspect Decky and SteamOS wrapper behavior in `decky-XRGaming`
- `Done` Inspect named-pipe IPC and user-session service boundaries in `virtual-display-rs`
- `Done` Inspect Viture IMU and capture-to-screen flow in `viture_virtual_display`
- `Done` Inspect stereoscopic desktop transformation flow in `desktop2stereo`

## Work package D: Repository updates

- `Done` Add Wave 42 plan document
- `Done` Add Wave 42 backlog document
- `Done` Add Wave 42 synthesis document
- `Done` Update the project registry for XR-glasses display stacks and spatial-screen utilities
- `Done` Update overlap families for base drivers, workspace shells, and virtual-display service stacks
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes
- `Done` Update the methods catalog with glasses and virtual-display methods
- `Done` Update documentation indexes to include Wave 42

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `breezy-desktop` if a future pass needs a deeper comparison of its Linux desktop-environment integrations and gaming mode split
- `Next` Revisit `desktop2stereo` only if a future pass needs a narrower look at its AI depth pipeline and stereo-display assumptions
