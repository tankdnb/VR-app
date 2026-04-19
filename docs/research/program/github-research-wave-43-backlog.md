# GitHub Research Wave 43 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `wearable haptics`, `tactile bridge sidecars`, and
  `avatar-driven feedback systems`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for VRChat haptics, tactile wearables, and avatar-driven feedback tools
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans desktop bridge apps, Unity-side avatar setup tooling, a DIY tactile firmware and hardware pair, and niche wearable integrations
- `Done` Keep `OpenShock/OpenShock` as a broader platform comparison node instead of replacing the more VR-facing bridge repo in this wave

## Work package B: Local source acquisition

- `Done` Confirm `ShockOSC` in local cache
- `Done` Confirm `VRChatOSC` in local cache
- `Done` Confirm `senseshift-firmware` in local cache
- `Done` Confirm `senseshift-hardware` in local cache
- `Done` Confirm `VRC-Haptic-Pancake` in local cache
- `Done` Confirm `vrc-patpatpat` in local cache
- `Done` Confirm `vrc-owo-suit` in local cache
- `Done` Confirm `vrcjoycon` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect grouped outputs, config surfaces, and `OSCQuery` flow in `ShockOSC`
- `Done` Inspect Unity editor setup and avatar injection tooling in `VRChatOSC`
- `Done` Inspect modular firmware structure in `senseshift-firmware`
- `Done` Inspect hardware-reference structure and fabrication assets in `senseshift-hardware`
- `Done` Inspect VRChat or Resonite bridge flow in `VRC-Haptic-Pancake`
- `Done` Inspect sparse-contact solving and haptic placement logic in `vrc-patpatpat`
- `Done` Inspect avatar contact and OWO-side control flow in `vrc-owo-suit`
- `Done` Inspect Joy-Con remap and rumble bridge behavior in `vrcjoycon`

## Work package D: Repository updates

- `Done` Add Wave 43 plan document
- `Done` Add Wave 43 backlog document
- `Done` Add Wave 43 synthesis document
- `Done` Update the project registry for wearable haptics and avatar-driven feedback systems
- `Done` Update overlap families for software bridges, firmware and hardware stacks, and solver-based haptic mapping
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes
- `Done` Update the methods catalog with wearable-haptics methods
- `Done` Update documentation indexes to include Wave 43

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `ShockOSC`, `VRC-Haptic-Pancake`, and `vrc-patpatpat` directly as `wearable router`, `bridge app`, and `contact-to-actuator solver`
- `Next` Treat the `senseshift` firmware and hardware pair as a future donor line whenever `VR-apps-lab` needs DIY tactile wearable references
