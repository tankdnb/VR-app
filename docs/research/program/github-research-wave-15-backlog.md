# GitHub Research Wave 15 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `overlay-first utility hosts`,
  `HUD micro-overlays`, `web or scene overlay scaffolds`, and
  `engine-side overlay integration` that were not yet fully represented in
  `VR-apps-lab`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for overlay-first utility hosts and dashboard-focused shells
- `Done` Search GitHub for browser-backed, WinForms-backed, WPF-backed, and ImGui-backed overlay paths
- `Done` Search GitHub for Unity scene-overlay scaffolds and wrist or HUD micro-overlays
- `Done` Search GitHub for engine-side OpenXR overlay integration samples
- `Done` Deduplicate all results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record source-light and domain-specific secondary candidates for later follow-up

## Work package B: Local source acquisition

- `Done` Confirm `KainosSoftwareLtd/VRSceneOverlay` in local cache
- `Done` Confirm `artumino/SteamVR_HUDCenter` in local cache
- `Done` Confirm `LapisGit/LapisOverlay` in local cache
- `Done` Confirm `elvissteinjr/SteamVR-PrimaryDesktopOverlay` in local cache
- `Done` Confirm `Martin-Oehler/SteamVR-WebApps` in local cache
- `Done` Confirm `hai-vr/h-view` in local cache
- `Done` Confirm `LunarG/OpenXR-Overlays-UE4-Plugin` in local cache
- `Done` Confirm `Denwa/vive-wireless-info-overlay` in local cache
- `Done` Confirm `vrkit-platform/vrkit-platform` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect scene-overlay bootstrap and tracked helper scripts in `VRSceneOverlay`
- `Done` Inspect overlay lifecycle, notification API, and UI rasterization path in `SteamVR_HUDCenter`
- `Done` Inspect dashboard, watch, and media-sidecar split in `LapisOverlay`
- `Done` Inspect existing-overlay patch model and autolaunch flow in `SteamVR-PrimaryDesktopOverlay`
- `Done` Inspect browser-backed dashboard wrappers in `SteamVR-WebApps`
- `Done` Inspect ImGui overlay host, OpenVR management layer, and saved-data model in `h-view`
- `Done` Inspect minimal engine-side `XR_EXTX_overlay` integration in `OpenXR-Overlays-UE4-Plugin`
- `Done` Inspect `Denwa/vive-wireless-info-overlay` far enough to classify it as source-light and product-reference-first
- `Done` Inspect `vrkit-platform/vrkit-platform` far enough to classify it as a large domain-specific overlay platform that still needs a narrower future pass

## Work package D: Repository updates

- `Done` Add Wave 15 plan document
- `Done` Add Wave 15 backlog document
- `Done` Add Wave 15 synthesis document
- `Done` Add an `h-view` reuse plan because it surfaced as a strong overlay-host donor
- `Done` Update project registry with the newly promoted overlay repos
- `Done` Update overlap families with the new overlay-host and scaffold notes
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-up gaps
- `Done` Update methods catalog with Wave 15 overlay-host and overlay-patch patterns
- `Done` Update documentation navigation to include Wave 15 and the new reuse plan

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the main documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `SteamVR_HUDCenter`, `SteamVR-WebApps`, and `h-view` directly as one `desktop UI stack -> overlay texture and input bridge` design note
- `Next` Compare `LapisOverlay` and `h-view` as one `overlay-first host with dashboard plus secondary surface` product pattern
- `Next` Revisit `vrkit-platform/vrkit-platform` with a tighter scope around its plugin manifest, overlay component model, and OpenXR layer script
- `Next` Revisit `Denwa/vive-wireless-info-overlay` only if source code or a stronger implementation mirror appears
- `Next` Compare `SteamVR-PrimaryDesktopOverlay`, `DesktopPlus`, and `OpenVRDesktopDisplayPortal` as one `patch existing desktop surface vs render your own desktop surface` design study
- `Next` Revisit `h-view` beyond the overlay slice to inspect its OSCQuery, hardware inventory, OCR, and external-service boundaries
