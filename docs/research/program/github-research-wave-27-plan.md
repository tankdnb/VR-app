# GitHub Research Wave 27 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `motion compensation`, `calibration overlays`, and
  `spatial alignment tools`.

## Why this wave exists

The repository already had several calibration references, but the family still
needed a clearer synthesis of its internal branches:

- `OpenVR` versus `OpenXR` motion compensation;
- one-shot versus continuous calibration;
- overlay-first calibration UX versus deeper driver-hook paths;
- spatial capture and reconstruction as an adjacent alignment tool.

This wave exists to make `alignment UX and pose rewriting` a stronger family in
`VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- OpenVR and OpenXR motion-compensation stacks;
- tracker-space calibration overlays and continuous-calibration variants;
- eye-tracking calibration overlays;
- room or pose capture tools that belong next to spatial alignment work rather
  than generic creator tooling.

## Frozen shortlist for code-level study

- `openvrmc/OpenVR-MotionCompensation`
- `BuzzteeBear/OpenXR-MotionCompensation`
- `pushrax/OpenVR-SpaceCalibrator`
- `Marshall-vak/OpenVR-SpaceCalibrator2`
- `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay`
- `alexander-clarke/openvr-room-mapping`

## Secondary candidates surfaced in the same wave

- `tobexeon/PSVR2EyeTrackingCalibration`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for motion compensation, calibration overlay, and room-mapping
  family queries;
- compare results against `catalog/project-registry.md`;
- reject thin forks unless they expose a materially different alignment or
  calibration model.

### Step 2: Freeze the shortlist

- keep the wave centered on `pose correction`, `calibration UX`, and
  `alignment-related capture`;
- allow adjacent spatial tools only when they help explain alignment workflows.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the main boundary is `driver hook`, `API layer`, `overlay UX`,
  `shared library`, or `capture pipeline`;
- how offsets, profiles, or calibration state are persisted and applied;
- whether the repo is a primary donor, a comparison extension, or a secondary
  follow-up node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 27 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies alignment,
  pose-rewrite, and spatial-capture methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `motion compensation`, `space calibration`, and `room capture` stay related
  but not collapsed into one vague bucket;
- overlay-first calibration tools remain distinguished from deeper driver or
  runtime hooks;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 27 synthesis document exists with code-level findings;
4. newly clarified calibration and alignment repos are promoted or reclassified
   in the registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
