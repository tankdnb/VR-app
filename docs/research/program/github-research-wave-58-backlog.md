# GitHub Research Wave 58 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `micro-overlays`, `timed status surfaces`, and
  `plugin-fed informational display helpers`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for small informational overlays, timer HUDs, notebook overlays, and local API-driven overlay helpers
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans tiny local control planes, plugin-fed information surfaces, timer escalation, and note-overlay lower bounds

## Work package B: Local source acquisition

- `Done` Confirm `OVRBrightnessAPI` in local cache
- `Done` Confirm `VR-Slideshow-Overlay` in local cache
- `Done` Confirm `VRSessionTimer` in local cache
- `Done` Confirm `notebook-vr-overlay` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect `HTTP` and `OSC` control surfaces plus overlay rendering path in `OVRBrightnessAPI`
- `Done` Inspect plugin model, output sinks, and overlay integration in `VR-Slideshow-Overlay`
- `Done` Inspect overlay widget, timer state, and notification loop in `VRSessionTimer`
- `Done` Inspect image-surface, event loop, and future writing hooks in `notebook-vr-overlay`

## Work package D: Repository updates

- `Done` Add Wave 58 plan document
- `Done` Add Wave 58 backlog document
- `Done` Add Wave 58 synthesis document
- `Done` Update the project registry for micro-overlays and timed status surfaces
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with micro-overlay and informational-surface methods
- `Done` Update documentation indexes to include Wave 58

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `OVRBrightnessAPI` visible whenever a future branch needs the smallest possible `overlay plus local control plane`
- `Next` Keep `VR-Slideshow-Overlay` visible whenever a future branch needs a `provider-fed informational surface` rather than a hardcoded HUD
- `Next` Revisit `notebook-vr-overlay` only if a future branch needs a deeper pass on note persistence, drawing, or writing-state UX
