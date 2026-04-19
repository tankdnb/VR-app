# GitHub Research Wave 67 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `OpenVR tracking export`, `recording`, and `robotics bridge tooling`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenVR tracking exporters, ROS bridges, recorders, and robotics-bridge utilities
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a simple tracking collector, `ROS` and `ROS2` bridges, a pluggable export host, a record-replay harness, and a VR-side robotics consumer

## Work package B: Local source acquisition

- `Done` Confirm `OpenVR-Tracking-Example` in local cache
- `Done` Confirm `openvr_ros` in local cache
- `Done` Confirm `openvr_ros_bridge` in local cache
- `Done` Confirm `openvr_ros2_tracker` in local cache
- `Done` Confirm `openvr-input-recorder` in local cache
- `Done` Confirm `vrviz` in local cache
- `Done` Confirm `vrpn-openvr` as a surfaced comparison node
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect background tracking collection and action-manifest setup in `OpenVR-Tracking-Example`
- `Done` Inspect pose polling and `tf` rebroadcast flow in `openvr_ros`
- `Done` Inspect modular connections, publishers, and status UI in `openvr_ros_bridge`
- `Done` Inspect topic, frame, and visualization parameters in `openvr_ros2_tracker`
- `Done` Inspect protobuf-backed recording and replay flow in `openvr-input-recorder`
- `Done` Inspect native VR consumption of robotics topics in `vrviz`
- `Done` Confirm that `vrpn-openvr` remains a useful follow-up node rather than a mainline donor in this pass

## Work package D: Repository updates

- `Done` Add Wave 67 plan document
- `Done` Add Wave 67 backlog document
- `Done` Add Wave 67 synthesis document
- `Done` Update the project registry for tracking-export and robotics-bridge donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with new tracking-export, recorder, and robotics-consumer methods
- `Done` Update documentation indexes to include Wave 67

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `openvr_ros_bridge` visible whenever a future branch needs a `pluggable tracking-export service` donor
- `Next` Keep `openvr-input-recorder` visible whenever `VR-apps-lab` needs a stronger `record and replay at the runtime layer` reference
- `Next` Revisit `openvr_ros` and `openvr_ros2_tracker` whenever `VR-apps-lab` needs thinner bridge baselines than the broader export host
- `Next` Revisit `vrviz` whenever a future branch needs a stronger `VR-native robotics topic consumer` comparison
