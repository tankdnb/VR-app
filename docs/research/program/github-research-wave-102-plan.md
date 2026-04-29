# GitHub Research Wave 102 Plan

- Date: `2026-04-30`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat avatar emulation`, `gesture preview`, `repair`, and
  `OSC-assisted posing`.

## Why this wave exists

`VR-apps-lab` needed stronger coverage of the space between
`avatar assets on disk`
and
`the creator actually seeing, testing, repairing, and posing the avatar`.

This wave exists to make the `avatar preview and manual intervention` branch
clearer.

## Search scope

Primary search directions for this wave:

- in-editor avatar emulators;
- gesture or expression preview tools;
- manual avatar repair and surgery suites;
- pose systems with OSC sidecars or external helpers.

## Frozen shortlist for code-level study

- `lyuma/Av3Emulator`
- `BlackStartx/VRC-Gesture-Manager`
- `JLChnToZ/avautils`
- `IlexisTheMadcat/LexisPosingSystem`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `Natsumi-sama/FACSvatar`
  looked more like a future expression and viseme track than a better donor for
  preview, repair, or pose workflow than the chosen shortlist;
- several tiny pose or gesture utilities surfaced, but the final shortlist
  already captured the stronger contrasts between emulation, gesture preview,
  manual repair, and OSC-sidecar posing.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for avatar emulator, gesture preview, fitting-room, and pose
  system queries;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where preview, repair, or sidecar flow is visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `avatar preview and manual intervention`
  rather than all avatar runtime features;
- allow one partially public product if its sidecar code still exposes a real
  reusable pattern.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the repo is mainly an emulator, a preview shell, a repair toolkit, or
  an external pose companion;
- where PlayableGraph, OSC, or repair logic actually lives;
- which product surfaces are public and which remain hidden behind closed
  assets.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 102 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- preview, repair, and posing are represented as distinct reusable branches;
- partially public products stay classified honestly;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 102 synthesis document exists with code-level findings;
4. the registry and families represent preview, repair, and pose donors more
   clearly;
5. new methods are captured where this wave clarified emulation, gesture, or
   OSC-sidecar patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
