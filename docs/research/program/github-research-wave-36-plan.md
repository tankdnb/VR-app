# GitHub Research Wave 36 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `runtime-side service hosts`, `broader OpenXR utility platforms`, and
  `layer diagnostics and fixers`.

## Why this wave exists

The repository already contained runtime switchers, layer templates, and
smaller diagnostic tools, but it still lacked a tighter comparative pass around
the `bigger platform-shaped` end of the OpenXR utility family:

- service hosts that split responsibilities across a desktop app, a landing
  space, and an API layer;
- overlay or monitor platforms that look more like product shells than one-off
  samples;
- layer-management tools that go beyond toggling and actually model
  `fixable runtime problems`.

This wave exists to make `runtime utility platforms and layer doctoring`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- OpenXR runtime-side service hosts;
- OpenXR layer managers and diagnostics UIs;
- broader overlay or monitor platforms that sit close to runtime tooling;
- repos that combine runtime inspection with packaging, configuration, or
  repair flows.

## Frozen shortlist for code-level study

- `clear-xr/clearxr-server`
- `vrkit-platform/vrkit-platform`
- `maluoi/openxr-explorer`
- `fredemmott/OpenXR-API-Layers-GUI`

## Secondary candidates surfaced in the same wave

- no separate secondary repo was strong enough to justify promotion beyond the
  frozen shortlist in this pass

## Execution model

### Step 1: Search and deduplicate

- search GitHub for OpenXR service hosts, layer-management tools, and broader
  utility platforms;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate the already-studied runtime-switcher family
  without a new platform or diagnostics lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `platform-shaped runtime tooling`, not on generic
  OpenXR templates alone;
- allow both developer tools and broader runtime-side product shells so the
  family stays comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where runtime registration, inspection, and repair logic lives;
- whether overlay, dashboard, or monitor UI is thin shell or real platform
  surface;
- whether the reusable lesson is `service host`, `plugin platform`,
  `runtime explorer`, or `layer linter/fixer`.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 36 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest remaining follow-ups;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies broader
  runtime-platform methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `runtime utility platforms` stay distinct from lighter switchers and
  templates;
- the family clearly separates platform shells, service hosts, explorers, and
  fix-oriented layer tools;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 36 synthesis document exists with code-level findings;
4. the registry and families clearly represent runtime service hosts and
   broader OpenXR utility platforms;
5. runtime-platform methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
