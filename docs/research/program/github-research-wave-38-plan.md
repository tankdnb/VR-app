# GitHub Research Wave 38 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `SteamVR validation helpers`, `config patchers`, and
  `environment-hygiene micro-tools`.

## Why this wave exists

The repository already contained multiple SteamVR helpers, but it still lacked
one tighter comparative pass around the `small but high-leverage` end of the
family:

- CI-friendly validation tools for SteamVR metadata;
- one-shot patchers that safely repair one broken configuration area;
- lightweight desktop tools that disable or reconfigure SteamVR behavior before
  startup;
- background helpers that watch runtime output and keep a setting in sync.

This wave exists to make `environment hygiene micro-tools` clearer inside
`VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- SteamVR action-manifest validators and linters;
- focused JSON or settings patchers for SteamVR or Lighthouse files;
- startup helpers that change autolaunch or driver state outside SteamVR;
- runtime-side micro-tools that continuously rewrite one SteamVR setting.

## Frozen shortlist for code-level study

- `username223/SteamVR-ActionsManifestValidator`
- `Erimelowo/Lighthouse-Scale-Fix`
- `MuffinTastic/steamvr-exconfig`
- `Virus-vr/SteamVRAdaptiveBrightness`

## Secondary candidates surfaced in the same wave

- `username223/SteamVRNoHeadset`
- `shieldmeidunn/SteamVRNullFlipper`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for SteamVR validation tools, one-shot patchers, and startup
  hygiene helpers;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate a broader already-studied environment helper
  without a distinct micro-tool lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `small, focused workflow utilities`, not broader
  dashboards or overlays;
- allow both CLI and GUI helpers so the family stays comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where the target config or runtime artifact is read and rewritten;
- whether the repo is a validator, a one-shot patcher, a prelaunch toggler, or
  a continuously running helper;
- what the reusable lesson is for future `VR-apps-lab` workflow tools.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 38 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest comparison nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies focused
  validation and environment-helper methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `workflow micro-tools` stay distinct from broader overlay suites;
- the family clearly separates validation, patching, startup toggling, and
  feedback-daemon behavior;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 38 synthesis document exists with code-level findings;
4. the registry and families clearly represent validation and environment
   hygiene micro-tools;
5. workflow-helper methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
