# GitHub Research Wave 22 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories already
  present but still not represented deeply enough in `VR-apps-lab`, focusing on
  `vision tracking hosts`, `camera full-body bridges`, and
  `hand-input sidecar stacks`.

## Why this wave exists

Wave 13 made the `vision tracking` family much denser, but it deliberately left
several of the strongest repositories only `Partially studied`.

What still needed a dedicated repeat pass was:

- the `legacy app -> plugin host` migration story in the `K2VR` ecosystem;
- the difference between `driver-first`, `sidecar-first`, and
  `switchable backend` camera-tracking designs;
- the hand-specific branch where `foreign runtime tracking` or
  `cheap webcam tracking` becomes SteamVR input.

This wave exists to upgrade the family from `broadly mapped` to
`architecture-extracted`.

## Search scope

Primary search directions for this wave:

- revisit the strongest `Partially studied` entries from the vision and hand
  family;
- compare host platforms against thinner camera-driver shells;
- inspect repos whose real value lies in backend switching, plugin boundaries,
  or service endpoints rather than in raw tracking quality.

## Frozen shortlist for code-level study

- `KinectToVR/Amethyst`
- `KinectToVR/KinectToVR`
- `ju1ce/Mediapipe-VR-Fullbody-Tracking`
- `Wunder-Wulfe/NVIDIA-BodyTracking`
- `Nordskog/HandOfLesser`
- `NovaAshwolfDev/HandCameraDriver`

## Secondary candidates surfaced in the same wave

- `chnoblouch/aethervr`
- `MasonSakai/VR-AI-Full-Body-Tracking`

## Execution model

### Step 1: Search and deduplicate

- search only enough to confirm whether stronger family representatives or
  maintained forks appeared;
- deduplicate against the registry and prefer deepening existing nodes over
  expanding the wave with noise.

### Step 2: Freeze the shortlist

- keep the wave centered on `repeat deep pass`, not a broad new search;
- choose repos that expose a meaningful host, backend, transport, or service
  split.

### Step 3: Sync local source cache

- confirm shortlisted repositories in `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the main architecture is `plugin host`, `driver shell`,
  `camera sidecar`, or `switchable backend`;
- transport and settings boundaries;
- calibration, WebUI, overlay, or service endpoint design;
- what has matured enough to promote from `Partially studied`.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 22 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens reusable
  tracking-host and backend-switch methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- repeat deep-pass repos are promoted only when the source now justifies it;
- the family distinguishes `plugin host`, `driver shell`, and `CV backend`
  patterns clearly;
- `.research-sources/` stays ignored by git;
- navigation stays coherent across the new wave documents and the backlog.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 22 synthesis document exists with code-level findings;
4. partially studied repos are honestly promoted or kept partial in the
   registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
