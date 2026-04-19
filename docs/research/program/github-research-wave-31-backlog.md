# GitHub Research Wave 31 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `teleoperation workspaces`,
  `embodied control surfaces`, and `VR command menus for external systems`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for VR teleoperation, ROS reality, and robot-control interface projects
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that mixes rich teleoperation shells and thin controller-export frontends
- `Done` Keep comparison nodes that are more architectural or visualization-oriented as secondary follow-ups

## Work package B: Local source acquisition

- `Done` Confirm `unity_ros_teleoperation` in local cache
- `Done` Confirm `ros_reality` in local cache
- `Done` Confirm `UR10_Teleop` in local cache
- `Done` Confirm `ReachyTeleoperation` in local cache
- `Done` Confirm comparison metadata and follow-up status for `VR_Teleop_Interface` and `GHOST`
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect palm-menu control hub and connection-state surfaces in `unity_ros_teleoperation`
- `Done` Inspect semantic robot-command menu flow in `ros_reality`
- `Done` Inspect controller-pose export and reconnect logic in `UR10_Teleop`
- `Done` Inspect staged teleoperation scenes, side menus, and VR keyboard flow in `ReachyTeleoperation`

## Work package D: Repository updates

- `Done` Add Wave 31 plan document
- `Done` Add Wave 31 backlog document
- `Done` Add Wave 31 synthesis document
- `Done` Update the project registry for the new teleoperation and control-surface donors
- `Done` Update overlap families for embodied control surfaces and teleoperation workspaces
- `Done` Update `not-yet-studied-deeply.md` with the honest follow-up nodes
- `Done` Update the methods catalog with control-surface utility methods
- `Done` Update documentation indexes to include Wave 31

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `VR_Teleop_Interface` as a more architectural comparison node if a future wave needs stronger branch-level or system-level teleoperation synthesis
- `Next` Compare `unity_ros_teleoperation`, `ros_reality`, and `ReachyTeleoperation` directly as `palm-menu shell`, `semantic action menu`, and `staged teleoperation workspace` approaches
