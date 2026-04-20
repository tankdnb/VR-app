# GitHub Research Wave 87 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that map
  `transformed video viewers`, `volumetric or VR180 playback`, and
  `nonstandard 3D media viewing environments`.

## Why this wave exists

`VR-apps-lab` already had immersive playback coverage, but it still lacked a
cleaner answer to:

`what donor patterns appear when video is not shown on an ordinary sphere or flat screen, but transformed, volumetric, depth-expanded, or embedded inside a dome-style environment`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- nonstandard or transformed VR video viewers;
- volumetric, VR180, or layered-depth playback stacks;
- depth-to-3D viewing tools and experimental media viewers;
- dome or spatial-media viewing environments that ingest several live or local
  source types.

## Frozen shortlist for code-level study

- `dfaker/VR-reversal`
- `fbriggs/lifecast_public`
- `parkchamchi/DepthViewer`
- `prefrontalcortex/DomeTools`

## Secondary candidates surfaced in the same wave

No extra candidates were strong enough to widen this wave further without
turning it into a generic `all unusual media viewers` bucket.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for volumetric, VR180, depth-based, and transformed video
  viewers;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos that teach a reusable transform, playback, or ingest model
  rather than only a content demo.

### Step 2: Freeze the shortlist

- keep the wave centered on `nonstandard 3D playback substrates`;
- allow both viewer-style tools and richer environments when they expose a
  different media-ingest or display boundary.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the repo transforms ordinary or stereo media into new view geometry;
- where media ingestion, inference, mesh generation, or scene assembly live;
- whether the repo is strongest as a product reference, donor, or experimental
  viewing substrate;
- how much of the public value sits in transform math versus surrounding UX.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 87 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- experimental viewers are described honestly when they are broad research
  stacks rather than small donors;
- volumetric and depth-based viewers stay distinct from ordinary 360-player
  shells;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 87 synthesis document exists with code-level findings;
4. the registry and families represent transformed and nonstandard 3D viewers
   more clearly;
5. new methods are captured where this wave clarified volumetric, depth, or
   transform-based media patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
