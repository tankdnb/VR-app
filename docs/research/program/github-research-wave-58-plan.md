# GitHub Research Wave 58 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `micro-overlays`, `timed status surfaces`, and
  `plugin-fed informational display helpers`.

## Why this wave exists

`VR-apps-lab` already had broader overlay hosts and contextual micro-overlays,
but one smaller and very practical branch still needed a cleaner donor map:

- tiny overlays controlled through `HTTP`, `OSC`, or a similarly lightweight
  local interface;
- informational surfaces that can aggregate data from plugins or external
  scripts;
- timer and reminder overlays that escalate from passive display to stronger
  notification;
- raw note or writing overlays that reveal the lower bound of
  `stateful informational surface` design.

This wave exists to make
`micro-overlays, timed status surfaces, and plugin-fed informational display helpers`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- tiny SteamVR overlays with `HTTP`, `OSC`, or local API control;
- timer, reminder, or session HUD overlays;
- informational panels with provider or plugin inputs;
- rough notebook or slide overlays whose value lies in the state or data model.

## Frozen shortlist for code-level study

- `R-VUt/OVRBrightnessAPI`
- `CorvinRyder/VR-Slideshow-Overlay`
- `Podshot/VRSessionTimer`
- `Yukiiro-Nite/notebook-vr-overlay`

## Secondary candidates surfaced in the same wave

- no additional secondary candidates were strong enough to displace the frozen
  shortlist

## Execution model

### Step 1: Search and deduplicate

- search GitHub for small informational overlays, timer overlays, notebook
  overlays, and local API-driven overlay helpers;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate already-studied context overlays without a
  clearer `micro-control plane` or `provider model` lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `small surfaces with one strong value`;
- allow rough prototypes when they expose a useful lower-bound architecture for
  stateful overlay content.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the control plane is `HTTP`, `OSC`, a desktop GUI, or a plugin
  provider model;
- how the overlay surface updates and persists its small state;
- whether the repo is a product reference, a method donor, or both.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 58 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  micro-overlay control-plane, informational-provider, and timed-notification
  methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- micro-overlays stay distinct from broad dashboard shells;
- the family clearly separates `tiny API-driven overlays`,
  `plugin-fed informational surfaces`, `timer overlays`, and
  `rough note-taking prototypes`;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 58 synthesis document exists with code-level findings;
4. the registry and families clearly represent micro-overlays and timed status
   surfaces;
5. new micro-overlay and informational-surface methods are added where
   justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
