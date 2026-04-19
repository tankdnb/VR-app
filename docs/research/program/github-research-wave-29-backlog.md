# GitHub Research Wave 29 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `hand menus`,
  `palm menus`, `radial menus`, and `quick-access VR surfaces`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for hand-menu, palm-menu, radial-menu, ring-menu, and XR quick-access projects
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that mixes `utility menu`, `menu scaffold`, and `context-panel` donors
- `Done` Keep broader toolkit repos for a later framework-centered wave instead of collapsing everything into one menu bucket

## Work package B: Local source acquisition

- `Done` Confirm `XRHandMenuSample` in local cache
- `Done` Confirm `VRMenuDesigner` in local cache
- `Done` Confirm `RadialMenuVR` in local cache
- `Done` Confirm `UnityXR-Physicalized-Radial-Menu` in local cache
- `Done` Confirm `XR-UI-Prototype` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect palm-orientation gating, launcher flow, and popup panel behavior in `XRHandMenuSample`
- `Done` Inspect archetype generation, editor modifiers, and radial-to-ring transitions in `VRMenuDesigner`
- `Done` Inspect hover scaling, auto-hide, and proximity-based selection in `RadialMenuVR`
- `Done` Inspect thumbstick-opened radial flow and interactable handoff in `UnityXR-Physicalized-Radial-Menu`
- `Done` Inspect dynamic menu list generation and contextual secondary-panel flow in `XR-UI-Prototype`

## Work package D: Repository updates

- `Done` Add Wave 29 plan document
- `Done` Add Wave 29 backlog document
- `Done` Add Wave 29 synthesis document
- `Done` Update the project registry for the new menu and quick-access donors
- `Done` Update overlap families for palm, radial, and quick-access menus
- `Done` Update the methods catalog with menu-oriented utility methods
- `Done` Update documentation indexes to include Wave 29

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `XRHandMenuSample`, `VRMenuDesigner`, and `mr-example-meta-openxr` directly when a later wave needs stronger `palm menu versus framework hand menu` synthesis
- `Next` Revisit `UnityXR-Physicalized-Radial-Menu` whenever a future prototype wants menu items that resolve into real interactables rather than abstract commands
