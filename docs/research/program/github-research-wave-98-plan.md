# GitHub Research Wave 98 Plan

- Date: `2026-04-27`
- Goal: run the next focused GitHub research wave for repositories that map
  `Udon sync`, `event dispatch`, `runtime logging`, and
  `shared helper micro-frameworks`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of creator mechanics and broader
utility foundations than of:

`the smaller runtime frameworks that make creator systems tolerable to wire together: event dispatch, parameterized networking, object sync substrate, and in-world diagnostics`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- Udon event and callback helpers;
- creator-world networking micro-frameworks;
- runtime logging or in-world console helpers;
- sync frameworks that reveal reusable state or ownership patterns.

## Frozen shortlist for code-level study

- `Varneon/VUdon-Events`
- `DeltaNeverUsed/UdonSharpNetworkingLib`
- `MMMaellon/LightSync`
- `Varneon/VUdon-Logger`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `kurone-kito/udonsharp-toybox`
  stayed outside this wave because the shortlist already had clearer event,
  networking, and runtime-diagnostics donors;
- `aiya000/VRChat-UdonSharpCommon`
  stayed outside this pass because the stronger value here was executable
  runtime framework patterns rather than broader common helpers.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for Udon events, networking, logging, and sync frameworks;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where editor hooks, runtime dispatch, or sync substrate are
  visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `runtime helper frameworks`
  rather than all creator utilities;
- allow one unstable or incomplete repo when its architecture still reveals a
  useful lineage lesson.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where editor-time or compile-time preprocessing happens;
- how runtime dispatch or routing is represented in serialized state;
- whether the repo is strong enough as a direct donor or mainly a lineage
  reference.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 98 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- compile-hook and build-time behavior is described honestly;
- unstable repos are treated honestly rather than promoted beyond the evidence;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 98 synthesis document exists with code-level findings;
4. the registry and families represent Udon runtime helper frameworks more
   clearly;
5. new methods are captured where this wave clarified reusable dispatch,
   networking, or logging patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
