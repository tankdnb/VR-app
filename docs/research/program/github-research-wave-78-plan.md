# GitHub Research Wave 78 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenXR passthrough samples` and
  `engine-side extension integration references`.

## Why this wave exists

`VR-apps-lab` had accumulated OpenXR layers and runtime utilities, but it still
lacked a clearer map of the engine-facing repos that answer:

- how to inject vendor-specific passthrough extensions without taking on a full
  vendor SDK;
- how thin an engine passthrough sample can be while still being reusable;
- how editor-time setup, runtime toggles, and diagnostics split across engine
  plugins or samples.

This wave exists to make those references explicit.

## Search scope

Primary search directions for this wave:

- Unreal, Godot, and Unity passthrough samples on top of OpenXR;
- engine-side extension plugins that request optional passthrough extensions;
- narrow mixed-reality sample projects with reusable runtime setup helpers.

## Frozen shortlist for code-level study

- `AgileLens/ue-openxr-passthrough`
- `BastiaanOlij/godot_test_passthrough`
- `olir/mr-openxr-unity-meta-passthrough-sample`

## Secondary candidates surfaced in the same wave

These candidates overlapped with already-tracked repos or were better treated
as adjacent comparison nodes:

- `Rectus/openxr-steamvr-passthrough`
- `DesktopXR`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for OpenXR passthrough samples across major engines;
- compare results against `catalog/project-registry.md`;
- prefer repos that expose engine lifecycle hooks and reusable integration
  patterns rather than only showing one scene outcome.

### Step 2: Freeze the shortlist

- keep the wave centered on `engine-side extension integration`, not general MR
  app repositories;
- allow both very thin samples and slightly broader sample projects when they
  teach different setup boundaries.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where extensions are requested and resolved;
- how passthrough state is toggled or layered into the engine frame;
- whether the repo includes diagnostics, editor setup, or runtime scaffolding;
- whether the repo is strongest as a code donor, product reference, or
  integration baseline.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 78 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- engine plugin references stay distinct from runtime-side API layers;
- thin samples are described honestly;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 78 synthesis document exists with code-level findings;
4. the registry and families represent these engine-side passthrough donors
   more clearly;
5. new methods are captured where this wave clarified reusable patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
