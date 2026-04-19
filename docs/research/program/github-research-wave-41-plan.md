# GitHub Research Wave 41 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `avatar-facing OSC companions`, `routing sidecars`, and
  `consumer automation utilities`.

## Why this wave exists

The repository already had tracker bridges, OSC exporters, and some VRChat
utility tools, but one user-facing branch was still too blurred:

- routers that sit between VRChat and other desktop-side consumers;
- plugin hosts that turn headset or device telemetry into reusable `OSC`
  signals;
- sidecars that translate avatar parameters into consumer actions, audio tools,
  locks, or other external behaviors.

This wave exists to make
`avatar-facing OSC companions, routers, and consumer automation sidecars`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- VRChat-facing `OSC` routers and sidecar launchers;
- plugin-based telemetry hosts that expose device or headset state;
- small utilities that turn avatar parameters into desktop or hardware actions;
- `OSCQuery`-aware bridges and parameter persistence helpers.

## Frozen shortlist for code-level study

- `OscToys/OscGoesBrrr`
- `valuef/VRCRouter`
- `Sergey004/Quest2-VRC`
- `I5UCC/VRCMeeter`
- `I5UCC/VRCAvatarParameterSync`
- `ZenithVal/OSCLeash`
- `ZenithVal/OSCLock`

## Secondary candidates surfaced in the same wave

- `lenoobkinda/VRCOSCUtils`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VRChat OSC routers, automation tools, and avatar-facing
  sidecars;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate a thinner bridge without adding a new router,
  telemetry-host, or consumer-automation lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `avatar-facing companions and automation`, not only
  generic OSC export or tracker egress;
- allow both broad platforms and narrow single-purpose consumer bridges so the
  family stays comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where `OSC`, `OSCQuery`, and local IPC boundaries sit;
- whether the reusable lesson is routing, plugin hosting, consumer automation,
  or parameter persistence;
- how the tool treats avatar state, headset telemetry, and sidecar lifecycle.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 41 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies routing,
  plugin-host, and automation-sidecar methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `avatar-facing OSC companions` stay distinct from generic tracker exporters;
- the family clearly separates routers, plugin telemetry hosts, desktop-action
  bridges, and parameter persistence helpers;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 41 synthesis document exists with code-level findings;
4. the registry and families clearly represent avatar-facing OSC companions and
   consumer automation sidecars;
5. routing and automation-sidecar methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
