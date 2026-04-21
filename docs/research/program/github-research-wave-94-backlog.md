# GitHub Research Wave 94 Backlog

- Date: `2026-04-21`
- Scope: next GitHub discovery wave focused on
  `VRChat embodied interaction`, `custom movement`, and
  `physical world-mechanics prefabs`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for VRChat physical interaction, movement, grapple, and vehicle repositories
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning physics interaction surfaces, grapples, movement controllers, and vehicle rigs

## Work package B: Local source acquisition

- `Done` Confirm `immersive-interactions` in local cache
- `Done` Confirm `UdonTether` in local cache
- `Done` Confirm `NUMovement` in local cache
- `Done` Confirm `UdonDoor` in local cache
- `Done` Confirm `KurotoriUdonKart` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect player-bone collider generation and manual-sync control surfaces in `immersive-interactions`
- `Done` Inspect tether physics, detection, and rigidbody split in `UdonTether`
- `Done` Inspect abstract controller substrate and movement application flow in `NUMovement`
- `Done` Inspect hinge-angle and pickup-driven motion logic in `UdonDoor`
- `Done` Inspect kart seat, handle, throttle, and visual sync split in `KurotoriUdonKart`

## Work package D: Repository updates

- `Done` Add Wave 94 plan document
- `Done` Add Wave 94 backlog document
- `Done` Add Wave 94 synthesis document
- `Done` Update the project registry for creator-world mechanic donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new interaction and movement patterns
- `Done` Update documentation indexes to include Wave 94

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `immersive-interactions` when a future pass needs a broader map of lever, switch, and package-level interaction variants
- `Next` Revisit `NUMovement` through its collider helpers and derived-class extension examples
- `Next` Revisit `KurotoriUdonKart` if a future pass needs stronger vehicle-state, seat, and time-attack lineage coverage
