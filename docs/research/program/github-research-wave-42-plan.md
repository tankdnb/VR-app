# GitHub Research Wave 42 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `XR-glasses virtual-display stacks`, `workspace shells`, and
  `spatial screen utilities`.

## Why this wave exists

The repository already had generic virtual-display drivers and some glasses
projects, but one branch was still not clean enough:

- base driver stacks for XR glasses and special screens;
- workspace shells that sit on top of those drivers;
- per-user virtual-display drivers and screen utilities that bridge desktop or
  captured content into head-tracked surfaces.

This wave exists to make
`XR-glasses virtual-display stacks and spatial screen utilities`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- XR-glasses driver stacks and Linux workspace shells;
- SteamOS or game-mode wrappers around special-display stacks;
- virtual-display drivers with clean IPC or service boundaries;
- spatial screen and stereo-screen utilities for nontraditional display paths.

## Frozen shortlist for code-level study

- `wheaney/XRLinuxDriver`
- `wheaney/breezy-desktop`
- `wheaney/decky-XRGaming`
- `MolotovCherry/virtual-display-rs`
- `mgschwan/viture_virtual_display`
- `lc700x/desktop2stereo`

## Secondary candidates surfaced in the same wave

- `peacepenguin/Virtual-Display-Driver`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for XR-glasses drivers, spatial screen shells, and
  virtual-display utilities;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate a generic virtual display without adding a
  clearer glasses, workspace-shell, or head-tracked screen lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `special-display and spatial-screen workflows`, not
  generic desktop overlays alone;
- allow both low-level driver stacks and higher-level workspace shells so the
  family stays comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where driver, service, shell, or plugin boundaries live;
- whether the repo owns hardware access, workspace UX, or only a control layer;
- how captured or synthetic displays become spatial screens.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 42 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies glasses,
  virtual-display, and spatial-screen methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `XR-glasses and spatial screen tools` stay distinct from generic virtual
  displays or ordinary desktop-in-VR overlays;
- the family clearly separates driver stacks, workspace shells, user-session
  services, and head-tracked screen utilities;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 42 synthesis document exists with code-level findings;
4. the registry and families clearly represent XR-glasses virtual-display
   stacks and spatial-screen utilities;
5. glasses and virtual-display methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
