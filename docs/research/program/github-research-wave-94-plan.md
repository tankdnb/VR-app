# GitHub Research Wave 94 Plan

- Date: `2026-04-21`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat embodied interaction`, `custom movement`, and
  `physical world-mechanics prefabs`.

## Why this wave exists

`VR-apps-lab` already had some good creator-world utility UI and platform
helpers, but it still lacked a stronger answer to:

`what the best donor repos look like when the value sits in physical buttons, grapples, movement controllers, interactable doors, or controller-driven vehicle rigs`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- physics-first buttons, switches, and handles for creator worlds;
- grapple or rope-style locomotion helpers;
- custom movement controllers and platform interaction systems;
- physical door and vehicle prefabs for creator worlds.

## Frozen shortlist for code-level study

- `Janooba/immersive-interactions`
- `squiddingme/UdonTether`
- `Nestorboy/NUMovement`
- `esnya/UdonDoor`
- `kurotori4423/KurotoriUdonKart`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- already tracked repos such as `UdonPlayerPlatformHook`
  stayed comparison anchors instead of widening the wave;
- thinner world-interaction prefabs like `ToggUltima`
  stayed outside this pass because the shortlist already had stronger physical
  interaction donors.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VRChat physical interaction, movement, grapple, and vehicle
  repos;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where runtime interaction boundaries are visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on `embodied interaction and world mechanics`, not on
  all creator-world prefabs;
- allow both narrow mechanics and broader controller frameworks when they show
  different implementation shapes.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how player hands, bones, or pickups enter the interaction system;
- whether state sync is manual, ownership-driven, or mostly local;
- how physical constraints, movement, or vehicle control are represented;
- what reusable mechanics methods belong in the methods catalog.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 94 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- narrow prefabs stay distinct from broader movement or vehicle frameworks;
- physically rich but broad repos are described honestly when follow-up is still
  warranted;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 94 synthesis document exists with code-level findings;
4. the registry and families represent physical creator-world mechanics more
   clearly;
5. new methods are captured where this wave clarified reusable mechanic or
   movement patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
