# GitHub Research Wave 77 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenXR helper stacks`, `layer toolchains`, and
  `runtime adaptation helpers`.

## Why this wave exists

`VR-apps-lab` already had strong coverage of OpenXR bindings, sample apps, and
platform shells, but it still lacked a cleaner map of the smaller helper
surfaces that sit between:

- full runtime platforms;
- layer templates;
- engine integrations;
- one-off graphics or tool bridges.

This wave exists to clarify that middle layer.

## Search scope

Primary search directions for this wave:

- OpenXR API-layer helper frameworks and authoring crates;
- tiny engine or renderer wrappers around OpenXR boilerplate;
- operator or developer micro-tools for inspecting or editing layer state;
- narrow runtime adaptation layers such as image-processing helpers.

## Frozen shortlist for code-level study

- `technobaboo/quark`
- `doraibu/rayxr`
- `fredemmott/openxr-layer-scripts`
- `elliotttate/OpenXR-CAS`

## Secondary candidates surfaced in the same wave

These candidates overlapped with already-tracked repos or were better kept for
later focused follow-up:

- `Ybalrid/OpenXR-API-Layer-Template`
- `openxr-explorer`
- `OpenXR-API-Layers-GUI`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for OpenXR layer frameworks, wrappers, and helper scripts;
- compare results against `catalog/project-registry.md`;
- prefer repos that expose a distinct `helper` boundary rather than another
  full runtime or sample app.

### Step 2: Freeze the shortlist

- keep the wave centered on `helper stacks and adaptation helpers`;
- allow a mix of toolchain repos, wrapper repos, and one strong runtime-side
  intervention repo when they teach different boundaries.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the repo helps author layers, host graphics, edit loader state, or
  adapt runtime output;
- how handle ownership, graphics setup, or config precedence are structured;
- whether the repo is strongest as a donor for tooling, wrapper shape, or
  runtime intervention.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 77 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- helper frameworks stay distinct from bindings and full runtime platforms;
- micro-tools are not understated just because they are small;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 77 synthesis document exists with code-level findings;
4. the registry and families represent these OpenXR helper donors more
   clearly;
5. new methods are captured where this wave clarified reusable patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
