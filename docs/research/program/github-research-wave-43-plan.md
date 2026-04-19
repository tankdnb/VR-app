# GitHub Research Wave 43 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `wearable haptics`, `tactile bridge sidecars`, and
  `avatar-driven feedback systems`.

## Why this wave exists

The repository already had trackers, expressive input, and some avatar-facing
automation tools, but one tactile branch was still under-modeled:

- sidecars that translate avatar or `OSC` events into wearable haptic systems;
- firmware and hardware stacks for DIY tactile wearables;
- bridge apps that connect VRChat or adjacent avatar consumers to external
  haptic devices.

This wave exists to make
`wearable haptics, tactile bridges, and avatar-driven feedback`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- VRChat-facing haptic bridges and `OSC`-driven wearable controllers;
- Unity-side avatar setup tooling for haptic wearables;
- firmware and hardware repos for DIY tactile systems;
- niche tactile bridges that connect avatar events to alternate devices or
  transports.

## Frozen shortlist for code-level study

- `OpenShock/ShockOSC`
- `bhaptics/VRChatOSC`
- `senseshift/senseshift-firmware`
- `senseshift/senseshift-hardware`
- `Z4urce/VRC-Haptic-Pancake`
- `lebaston100/vrc-patpatpat`
- `shadorki/vrc-owo-suit`
- `Python1320/vrcjoycon`

## Secondary candidates surfaced in the same wave

- `OpenShock/OpenShock`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VRChat haptics, tactile wearables, and avatar-driven
  feedback tools;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate one hardware-specific integration without
  adding a new bridge, solver, firmware-stack, or avatar-setup lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `wearable haptics and tactile bridges`, not generic
  controller rumble or game-side haptics alone;
- allow both software bridges and hardware-stack repos so the family stays
  comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how avatar or `OSC` events become wearable or actuator outputs;
- where bridge-app, editor-tooling, firmware, and hardware boundaries sit;
- whether the reusable lesson is routing, contact solving, avatar setup, or
  hardware platform structure.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 43 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies wearable
  haptics and tactile-bridge methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `wearable haptics and tactile bridges` stay distinct from generic input or
  body-tracking families;
- the family clearly separates software bridges, editor-side avatar setup,
  solver logic, and firmware or hardware platform donors;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 43 synthesis document exists with code-level findings;
4. the registry and families clearly represent wearable haptics and
   avatar-driven feedback systems;
5. wearable-haptics methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
