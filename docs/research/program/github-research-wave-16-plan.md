# GitHub Research Wave 16 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `device-monitor overlays`, `battery watchers`, `pose-inspection and export
  helpers`, and `SteamVR environment-side utilities`.

## Why this wave exists

After Wave 15 the repository had good coverage of:

- overlay hosts and scaffolds;
- tracker bridges and OSC exporters;
- runtime switchers and layer diagnostics;
- driver tutorials and accessibility helpers.

What was still thinner than it should be was the `small practical utility`
layer around day-to-day SteamVR usage:

- `battery watchers` that differ by alert model, persistence, and output
  surface;
- `device-health tools` that behave as tray apps, one-shot scripts, or metrics
  exporters rather than as classic overlays;
- `pose inspection and export helpers` that turn live SteamVR state into useful
  assets for creator workflows;
- `Linux-side SteamVR hygiene scripts` that live outside the headset but still
  solve real VR friction.

## Search scope

Primary search directions for this wave:

- SteamVR battery and charging-state utilities;
- device-inventory or pose-inspection micro-tools;
- creator-side pose export helpers;
- tray apps, notification tools, and metrics loggers;
- Linux-side SteamVR environment helpers with daemon behavior.

## Frozen shortlist for code-level study

- `jangxx/openvr-battery-monitoring`
- `mutr/openvr_battery_monitor`
- `KaftanOS/SteamVR-Battery-Checker`
- `MuffinTastic/openvr-device-positions`
- `DavidRisch/steamvr_utils`

## Secondary candidate discovered in the same wave

- `Denwa/vive-wireless-info-overlay`

## Execution model

### Step 1: Search and deduplicate

- search by `utility family` rather than by generic VR keywords;
- compare each candidate against `catalog/project-registry.md`;
- reject already-covered repos unless the previous note was too shallow or the
  repo represented a clearly different product shape.

### Step 2: Freeze the shortlist

- keep the wave bounded around `device monitoring`, `battery alerting`,
  `pose inspection/export`, and `environment-side helpers`;
- prefer repos that show a distinct output model such as `desktop
  notifications`, `metrics logging`, `CLI snapshots`, `overlay diagnostics`, or
  `daemonized environment switching`.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- README and product framing;
- whether it is a `tray app`, `background watcher`, `CLI tool`, `overlay`,
  `creator utility`, or `daemon`;
- how it reads SteamVR/OpenVR state;
- whether it reacts to `state transitions` or only reports current state;
- how it persists configuration and muted devices;
- whether it is mostly a `code donor`, a `product reference`, or a narrow
  comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 16 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens
  notification-driven monitor patterns, pose-export helpers, and
  environment-side daemon utilities.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- registry and family placement stay coherent;
- cross-family utilities such as `openvr-device-positions` land in the right
  place instead of being forced into the wrong bucket;
- source-light repos remain labeled honestly;
- `.research-sources/` stays ignored by git.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 16 synthesis document exists with code-level findings;
4. promoted repos are reflected in the registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
