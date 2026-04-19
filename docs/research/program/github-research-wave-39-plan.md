# GitHub Research Wave 39 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `overlay host lineage`, `dashboard shells`, and
  `browser-backed overlay surfaces`.

## Why this wave exists

The repository already contained many overlay references, but it still lacked a
cleaner comparative pass on one unresolved branch:

- the historical `ovr-utils` lineage where the live code moved away from
  GitHub;
- Godot-based dashboard shells with reusable overlay instances;
- broader utility hosts that run as both desktop window and SteamVR overlay;
- browser-backed toolkits that expose a general overlay construction pattern
  rather than one product.

This wave exists to make `overlay host lineage and toolkit-level overlay
construction` clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- historical or relocated overlay utility suites;
- browser-backed overlay toolkits and dashboard wrappers;
- overlay-first utility hosts with desktop parity;
- Godot or engine-side shells that manage multiple overlays as one platform.

## Frozen shortlist for code-level study

- `CrispyPin/ovr-utils`
- `mittorn/ovr-utils-dashboard`
- `hai-vr/h-view`
- `BenWoodford/SteamVR-Webkit`

## Secondary candidates surfaced in the same wave

- `sh-akira/VROverlay`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for overlay utility suites, browser-backed toolkits, and
  broader dashboard shells;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate a simpler overlay sample without adding a
  host or toolkit lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `host and toolkit lineage`, not only finished
  end-user overlay products;
- allow both historical and modern repos so the family stays comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where overlay lifecycle and persistence live;
- whether the repo is a toolkit, a reusable suite shell, or a broader utility
  host;
- what still matters if the public GitHub snapshot is incomplete or moved.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 39 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest historical follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies overlay
  host and toolkit methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `overlay host lineage` stays distinct from simple overlay samples;
- the family clearly separates historical lineage nodes, reusable suite shells,
  modern utility hosts, and toolkit libraries;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 39 synthesis document exists with code-level findings;
4. the registry and families clearly represent overlay host lineage and
   toolkit-level overlay construction;
5. overlay-host methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
