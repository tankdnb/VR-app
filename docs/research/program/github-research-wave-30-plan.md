# GitHub Research Wave 30 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `spatial UI interaction frameworks`, `input stacks`, and
  `menu-enabling XR scaffolds`.

## Why this wave exists

The repository already had many single-purpose utilities and menu examples, but
it still needed a better framework-level comparison for the lower layers that
make those utilities usable:

- how ray, poke, and hand input are wired into UI systems;
- how palm menus are enabled or suppressed by gesture heuristics;
- how a toolkit turns `Unity UI` into `VR-usable UI` without each app
  reimplementing the same plumbing.

This wave exists to make `XR UI framework donors` a clearer branch inside
`VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- toolkit example repositories that include spatial keyboards, menus, and 3D UI
  interaction;
- hand-menu and spatial-panel scaffolds inside OpenXR or mixed-reality sample
  stacks;
- input modules and pointer systems that adapt ordinary UI event systems to VR.

## Frozen shortlist for code-level study

- `Unity-Technologies/XR-Interaction-Toolkit-Examples`
- `microsoft/MixedRealityToolkit-Unity`
- `ViveSoftware/ViveInputUtility-Unity`
- `Unity-Technologies/mr-example-meta-openxr`

## Secondary candidates surfaced in the same wave

- `MixedRealityToolkit/MixedRealityToolkit-Unity`
- `oculus-samples/Unity-FirstHand`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for XR interaction toolkit examples, mixed reality toolkit UI,
  3D input module, hand menu framework, and spatial panel samples;
- compare results against `catalog/project-registry.md`;
- reject repos that are too broad unless they expose especially reusable UI or
  interaction scaffolding.

### Step 2: Freeze the shortlist

- keep the wave centered on `framework-level UI plumbing`, not just one menu;
- allow broader toolkit repositories only when they teach repeatable input or
  menu-enablement patterns.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how hand, ray, poke, or gaze input reaches UI;
- how palm-up and gesture-driven menus are activated;
- whether keyboard, panel, and world-space UI systems are first-class citizens
  or only scene demos.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 30 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest successor or follow-up
  nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies UI-input
  stack methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `framework-level UI plumbing` stays distinct from small standalone menus;
- legacy and current toolkit lines are represented honestly;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 30 synthesis document exists with code-level findings;
4. the registry and families clearly represent XR UI input-stack donors;
5. framework-oriented methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
