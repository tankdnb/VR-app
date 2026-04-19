# GitHub Research Wave 59 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `embodied locomotion overlays`, `live tuning surfaces`, and
  `external-device control panels`.

## Why this wave exists

`VR-apps-lab` already had control overlays, simulator panels, and tactile
bridges, but another adjacent product branch still needed a cleaner donor map:

- overlays that directly influence locomotion, movement intent, or bodily
  interaction rather than just display information;
- desktop editors that mirror their state into a live VR tuning surface;
- device-control panels that coordinate remote APIs, persisted settings, and
  hand-specific interaction in-headset;
- lineage nodes where a newer overlay host clearly supersedes an older Unity or
  early-stack implementation.

This wave exists to make
`embodied locomotion overlays, live tuning surfaces, and external-device control panels`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- locomotion or control overlays tied to trackers, gaze, or motion devices;
- profile editors or tuning tools with a VR-facing surface;
- overlays that control external hardware or networked devices through local or
  remote APIs;
- lineage repos where an older implementation still helps clarify the product
  branch.

## Frozen shortlist for code-level study

- `hiinaspace/bikeheadvr`
- `MartyDude20/Omni-Tune`
- `OpenShock/OVR-Shock`
- `OpenShock/VROverlay`

## Secondary candidates surfaced in the same wave

- `NewChromantics/PopExposeXr`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for locomotion overlays, live tuning surfaces, and external
  device control overlays;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate already-studied haptics or control-shell
  donors without a clearer embodied-control lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `embodied control` and `live external-device
  interaction`, not on generic dashboards;
- allow older lineage repos when they clarify how a stronger current donor
  evolved.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the overlay affects locomotion, live tuning, or external-device control;
- how much state lives in desktop UI, overlay UI, config files, or remote APIs;
- whether the repo is strongest as a current donor, a product reference, or a
  lineage comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 59 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies embodied
  control, live tuning, and external-device overlay methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- embodied-control overlays stay distinct from ordinary status or media
  surfaces;
- the family clearly separates `locomotion overlay`, `desktop editor plus live
  VR tuning surface`, and `external-device control overlay`;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 59 synthesis document exists with code-level findings;
4. the registry and families clearly represent embodied-control and
   external-device overlay donors;
5. new embodied-control or device-panel methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
