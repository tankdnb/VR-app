# GitHub Research Wave 31 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `teleoperation workspaces`, `embodied control surfaces`, and
  `VR command menus for external systems`.

## Why this wave exists

The repository already contained many utility overlays and input bridges, but
it still needed a clearer family around `VR as a control room`:

- palm menus and side panels that control remote systems;
- staged room flows for connection, mirror, and live control;
- thin VR frontends that send controller state to another process.

This wave exists to make `embodied control surfaces` a stronger product branch
inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- Unity and ROS teleoperation interfaces;
- VR robot-control menus and remote command panels;
- VR control frontends that export controller pose or button state to another
  process;
- teleoperation products with staged connection and live-control scenes.

## Frozen shortlist for code-level study

- `leggedrobotics/unity_ros_teleoperation`
- `h2r/ros_reality`
- `elpis-lab/UR10_Teleop`
- `pollen-robotics/ReachyTeleoperation`

## Secondary candidates surfaced in the same wave

- `nakama-lab/VR_Teleop_Interface`
- `h2r/GHOST`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VR teleoperation, ROS reality, robot VR interface, and VR
  robot control queries;
- compare results against `catalog/project-registry.md`;
- reject repos that do not materially expose a reusable UI, scene flow, or
  transport boundary.

### Step 2: Freeze the shortlist

- keep the wave centered on `VR control surfaces`, not robotics algorithms;
- allow both rich teleoperation shells and thin transport frontends so the
  family stays comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how menus, panels, or rooms organize the control workflow;
- how connection state and transport boundaries are exposed;
- whether the repo is a product shell, a semantic command menu, or a thin
  controller-data bridge.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 31 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies embodied
  control-surface methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `teleoperation workspaces` stay distinct from ordinary utility overlays;
- the family stays focused on UI, scene flow, and transport boundaries rather
  than robotics implementation details;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 31 synthesis document exists with code-level findings;
4. the registry and families clearly represent teleoperation and embodied
   control-surface donors;
5. control-surface methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
