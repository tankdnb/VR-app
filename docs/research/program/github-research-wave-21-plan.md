# GitHub Research Wave 21 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenXR provider stacks`, `gaze API layers`, and
  `runtime-side utility platforms`.

## Why this wave exists

After Wave 20 the repository had a stronger rendering-mod family, but one
important OpenXR slice still needed consolidation:

- `library-plus-sandbox` bring-up stacks that turn raw OpenXR work into a
  reusable wrapper;
- `API layers` that adapt foreign sensor or gaze data into runtime-facing
  OpenXR surfaces;
- larger platforms where the interesting donor value lives in the
  layer/service split rather than in the entire app shell.

This wave exists to keep `OpenXR provider and gaze-layer tooling` represented
as a real product family instead of leaving it spread thinly across runtime
manager, overlay, and vendor-enhancement notes.

## Search scope

Primary search directions for this wave:

- OpenXR wrapper libraries with runnable sandbox apps;
- OpenXR API layers that expose eye tracking, foveation, or controller fixes;
- runtime-side utility platforms with service hosts, registration helpers, or
  plugin-manifest surfaces;
- adjacent follow-up signals where the public repo may be strategically useful
  even if it should stay only partially studied.

## Frozen shortlist for code-level study

- `1runeberg/OpenXRProvider`
- `mbucchia/Quad-Views-Foveated`
- `mbucchia/OpenXR-Eye-Trackers`
- `clear-xr/clearxr-server`
- `vrkit-platform/vrkit-platform`

## Secondary candidates surfaced in the same wave

- `BattleAxeVR/PSVR2_OpenXR_Eye_Tracking`
- `LordOfDragons/openxr_oscclient`

## Execution model

### Step 1: Search and deduplicate

- search GitHub by `OpenXR provider`, `OpenXR eye tracking`, `OpenXR layer`,
  and `runtime utility platform` family queries;
- compare candidates against `catalog/project-registry.md`;
- reject repos that only restate the same layer template without exposing a new
  adaptation pattern or utility split.

### Step 2: Freeze the shortlist

- keep the wave bounded around `provider stacks`, `gaze/foveation layers`, and
  `runtime-side host platforms`;
- treat broad multi-app ecosystems honestly and focus only on their most
  reusable boundaries.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the main donor value is a wrapper library, API layer, or service host;
- extension and capability surfaces it exposes or synthesizes;
- runtime registration, manifest, or layer boundaries;
- whether the current public snapshot is a strong donor, a scope-drifted
  platform, or only a follow-up signal.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 21 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens OpenXR
  layer-adaptation and provider-stack methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- OpenXR runtime and layer families stay coherent;
- broad platforms remain described by their current public scope, not by old
  assumptions;
- `.research-sources/` stays ignored by git;
- new wave links appear in the documentation indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 21 synthesis document exists with code-level findings;
4. newly clarified repos are promoted or kept partial in the registry and
   families with honest labels;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
