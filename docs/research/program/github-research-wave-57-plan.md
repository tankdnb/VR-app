# GitHub Research Wave 57 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `Linux overlay control shells`, `desktop-service panels`, and
  `interaction variants`.

## Why this wave exists

`VR-apps-lab` already had several Windows-heavy overlay references, but the
Linux-oriented branch still needed a cleaner donor map:

- overlays that behave like desktop-control shells rather than just texture
  mirrors;
- panels that coordinate audio devices, media services, or desktop utilities;
- interaction models where controller rays, screen capture, and keyboard
  helpers replace the usual dashboard assumptions;
- repos that explicitly preserve a `--novr` or desktop-only debug path.

This wave exists to make
`Linux overlay control shells, desktop-service panels, and interaction variants`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- Linux `OpenVR` overlay utilities and desktop-control panels;
- Qt or KDE overlay shells tied to desktop services;
- overlay apps with `X11` capture, controller-mouse interaction, or
  on-overlay keyboard logic;
- historical Linux overlay projects whose product framing is clearer than their
  polish level.

## Frozen shortlist for code-level study

- `galister/OVR4X11`
- `DrogonMar/SVRLinuxTools`
- `Dragon092/OpenVR_Audio_Manager`

## Secondary candidates surfaced in the same wave

- `CrispyPin/sinpin-vr`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for Linux desktop-service overlays, Qt overlay panels, and
  `X11`-oriented `OpenVR` tools;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate already-tracked desktop mirrors without a
  clearer Linux control-shell lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `desktop-service control` and `interaction model`,
  not on generic browser overlays;
- allow both polished tools and rough Linux-specific shells when they expose a
  distinct systems or interaction idea.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the repo handles Linux desktop capture, desktop services, or device
  enumeration;
- how interaction works when the overlay is more than a passive display;
- whether a non-VR debug path exists and how much that helps maintainability.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 57 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies Linux
  control-shell and controller-mouse overlay methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- Linux overlay shells stay distinct from ordinary cross-platform display
  surfaces;
- the family clearly separates `screen-control shell`, `desktop-service panel`,
  and `audio-routing overlay` lessons;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 57 synthesis document exists with code-level findings;
4. the registry and families clearly represent Linux overlay control-shell
   donors;
5. a Linux-focused overlay-shell method is added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
