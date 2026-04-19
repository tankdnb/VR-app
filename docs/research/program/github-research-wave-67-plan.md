# GitHub Research Wave 67 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenVR tracking export`, `recording`, and `robotics bridge tooling`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage for tracker bridges, OSC tools, and
driver-side helpers than for the broader question of
`how SteamVR tracking gets exported, recorded, relayed, or consumed by robotics stacks`.

This wave exists to make several donor branches explicit:

- simple background pose collectors;
- `SteamVR -> ROS` or `ROS2` bridges;
- modular export services with multiple publishers;
- record or replay harnesses at the OpenVR layer;
- direct VR consumers of robotics topics.

## Search scope

Primary search directions for this wave:

- SteamVR or OpenVR tracking exporters;
- ROS, `ROS2`, `VRPN`, or WebSocket bridges around OpenVR tracking;
- tooling that records, replays, or visualizes OpenVR pose streams.

## Frozen shortlist for code-level study

- `Omnifinity/OpenVR-Tracking-Example`
- `sharif1093/openvr_ros`
- `personalrobotics/openvr_ros_bridge`
- `qeftser/openvr_ros2_tracker`
- `lebek/openvr-input-recorder`
- `RViMLab/vrviz`

## Secondary candidates surfaced in the same wave

- `zhouhs88/vrpn-openvr`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for OpenVR tracking exporters, ROS bridges, and pose-recorder
  tooling;
- compare results against `catalog/project-registry.md`;
- reject repos that are only narrow app integrations without a clearer export
  or bridge lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `tracking export and reuse`, not ordinary overlay
  tooling;
- allow research or robotics repos when they expose especially strong bridge
  boundaries.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how OpenVR tracking is collected and normalized;
- what publisher or transport layers exist;
- whether the repo supports recording, replay, or visualization;
- whether the repo is strongest as a direct donor, a product reference, or a
  comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 67 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  pluggable tracking export, recording, replay, and robotics-consumer patterns.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `tracking export` stays distinct from tracker drivers, OSC bridges, and
  avatar-facing control families;
- the family clearly separates `simple tracker exporter`, `ROS bridge`,
  `ROS2 bridge`, `record/replay harness`, and `VR robotics consumer` answers;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 67 synthesis document exists with code-level findings;
4. the registry and families clearly represent OpenVR tracking-export donor
   lines;
5. new export and recorder methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
