# GitHub Research Wave 86 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat synced video player frameworks`, `queue frontends`, and
  `event-optimized media shells`.

## Why this wave exists

`VR-apps-lab` already had creator-facing audio and synced media coverage, but
it still lacked a clearer answer to:

`what the strongest creator-side video donors look like when playback, sync, screen routing, playlists, and moderation split into reusable subsystems`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- VRChat video player frameworks with strong code surfaces;
- Udon synced players with backend abstraction or late-join handling;
- modular creator-facing video frontends with queue, history, or extension
  systems;
- repos where audio, screen, and playback managers are intentionally split.

## Frozen shortlist for code-level study

- `vrctxl/VideoTXL`
- `UdonVR/UdonVideoplayer`
- `koorimizuw/YamaPlayer`

## Secondary candidates surfaced in the same wave

These nodes remained comparison context instead of widening the wave:

- `MerlinVR/USharpVideo`
  already tracked as a stronger baseline for synced media-core ownership;
- `sam-ln/USharpVideoQueue`
  already tracked as a queue companion around an existing player;
- `JLChnToZ/VVMW`
  already tracked as a broader creator-facing media frontend.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VRChat and Udon video players, queue shells, and sync
  frontends;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos that expose reusable ownership, queue, sync, or manager
  boundaries clearly.

### Step 2: Freeze the shortlist

- keep the wave centered on `creator-side video system design`;
- allow both leaner Udon scripts and larger modular packages when they reveal
  different control surfaces cleanly.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where playback ownership, time sync, and late-join repair live;
- how playlists, queues, handlers, and permissions split from core playback;
- whether the repo is strongest as a donor, creator framework, or product
  reference;
- how audio and screen routing sit beside video-state ownership.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 86 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- creator-facing video systems stay distinct from the older audio-focused
  family;
- larger package repos are described honestly when they are broader than the
  current deep pass;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 86 synthesis document exists with code-level findings;
4. the registry and families represent creator-side video-system donors more
   clearly;
5. new methods are captured where this wave clarified sync, queue, or modular
   player-shell patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
