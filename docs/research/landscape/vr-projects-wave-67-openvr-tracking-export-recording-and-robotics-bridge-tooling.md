# VR Projects Wave 67: OpenVR Tracking Export, Recording, and Robotics Bridge Tooling

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `OpenVR tracking export`, `recording`, and `robotics bridge tooling`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage for tracker bridges and avatar-side
export flows than for the broader question of
`how SteamVR tracking gets exported, recorded, replayed, or consumed in robotics stacks`.

This wave exists to make that family clearer:

- background tracking collectors;
- `SteamVR -> ROS` and `SteamVR -> ROS2` bridges;
- modular export services with swappable publisher backends;
- record or replay harnesses at the runtime layer;
- VR apps that consume robotics topics directly.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with OpenVR tracking, ROS bridge, recorder, replay, and
   robotics visualization queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Omnifinity/OpenVR-Tracking-Example` | Useful lower-bound donor for background SteamVR tracking collection |
| `sharif1093/openvr_ros` | Strong donor for a thin SteamVR-to-ROS pose bridge |
| `personalrobotics/openvr_ros_bridge` | Strong donor for a modular export host with multiple publishers and status UI |
| `qeftser/openvr_ros2_tracker` | Useful donor for a minimal `ROS2` OpenVR tracker bridge |
| `lebek/openvr-input-recorder` | Strong donor for runtime-level recording and replay of OpenVR device input and motion |
| `RViMLab/vrviz` | Strong donor for consuming robotics topics directly inside a native VR app |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `zhouhs88/vrpn-openvr` | Useful comparison node, but thinner than the shortlisted bridges and recorders in this pass |

## Deep-pass notes by project

## `Omnifinity/OpenVR-Tracking-Example`

- GitHub:
  [Omnifinity/OpenVR-Tracking-Example](https://github.com/Omnifinity/OpenVR-Tracking-Example)
- What it is:
  a small background OpenVR app that initializes tracking, loads an action
  manifest, and polls pose data in a simple loop.
- Why it matters:
  it is a useful lower-bound donor for
  `simple SteamVR tracking collector without broader bridge infrastructure`.
- Interesting ideas:
  keep background tracking logic narrow; make action-manifest paths explicit;
  use a simple runtime loop to show the minimal collector shape.
- Interesting implementation choices:
  `OpenVRTrackingExample.cpp`
  performs runtime initialization, action-handle lookup, and repeated polling
  inside a compact background procedure.
- Code donor value:
  medium.
- Product reference value:
  low-medium.
- Architecture reference value:
  medium.
- Caveats:
  intentionally small, but valuable as a lower bound.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `small tracking collector`
  reference.

## `sharif1093/openvr_ros`

- GitHub:
  [sharif1093/openvr_ros](https://github.com/sharif1093/openvr_ros)
- What it is:
  a thin bridge that polls SteamVR poses and publishes them into ROS topics and
  `tf`.
- Why it matters:
  it is the clearest donor in this wave for
  `simple SteamVR -> ROS pose bridge`.
- Interesting ideas:
  keep the pose publisher small; separate the steady poll loop from later
  `tf` rebroadcast logic; avoid burying the bridge inside a much larger host.
- Interesting implementation choices:
  `openvr_ros/src/track_publisher.cpp`
  owns the polling and ROS publication while
  `openvr_ros/script/tracked2tf.py`
  rebroadcasts frames into a more convenient `tf` topology.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  narrow by design, but strong precisely because the bridge boundary is so
  clear.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `small ROS bridge`
  rather than a broader service host.

## `personalrobotics/openvr_ros_bridge`

- GitHub:
  [personalrobotics/openvr_ros_bridge](https://github.com/personalrobotics/openvr_ros_bridge)
- What it is:
  a broader tracking-export service that can publish OpenVR tracking to
  multiple consumers such as ROS, WebSocket, and other sinks while also
  exposing status UI.
- Why it matters:
  it is the clearest donor in this wave for
  `pluggable tracking-export host with multiple publishers`.
- Interesting ideas:
  make the connection source swappable; separate publisher families; let status
  UI and visualizers stay first-class instead of treating them as debugging
  afterthoughts.
- Interesting implementation choices:
  scripts such as
  `scripts/main.t`,
  `scripts/publishers.t`,
  `scripts/ros_publishers.t`,
  `scripts/ws_publishers.t`, and
  `scripts/statusui.t`
  make the modularity explicit, while `node_relay` adds another consumer path.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broader and more research-facing than a small bridge, but that is exactly
  what makes it useful.
- What to inspect next:
  treat it as the main donor whenever a future branch needs
  `tracking export with pluggable transports`.

## `qeftser/openvr_ros2_tracker`

- GitHub:
  [qeftser/openvr_ros2_tracker](https://github.com/qeftser/openvr_ros2_tracker)
- What it is:
  a small `ROS2` node that publishes OpenVR tracker poses and optional
  visualization markers.
- Why it matters:
  it is a useful donor for
  `minimal OpenVR -> ROS2 tracker bridge`.
- Interesting ideas:
  keep configuration small and parameter-driven; expose visualization as a
  toggle; keep frame naming and publication rate explicit.
- Interesting implementation choices:
  `src/openvr_tracker_node.cpp`
  owns the core node logic, including parameters for topic, frame, poll delay,
  and visualization marker publication.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  narrower than the broader export host, but valuable as a thin `ROS2` donor.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `minimal ROS2 bridge`
  comparison.

## `lebek/openvr-input-recorder`

- GitHub:
  [lebek/openvr-input-recorder](https://github.com/lebek/openvr-input-recorder)
- What it is:
  a recorder and replay harness that serializes OpenVR device properties and
  timed motion or input samples.
- Why it matters:
  it is the clearest donor in this wave for
  `record and replay at the OpenVR layer`.
- Interesting ideas:
  record metadata and samples separately; use protobuf messages as the replay
  contract; treat replay as a first-class runtime use case rather than a debug
  side effect.
- Interesting implementation choices:
  `src/main.cc`
  owns record and replay flow while
  `messages/recording.proto`
  and
  `messages/ovr_device.proto`
  define the persistent contracts for device metadata and sample timelines.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  tied partly to `VRInputEmulator` for replay, but still unusually valuable as
  a harness donor.
- What to inspect next:
  keep it visible whenever a future branch needs
  `pose recording`, `replay`, or `deterministic input harness`
  references.

## `RViMLab/vrviz`

- GitHub:
  [RViMLab/vrviz](https://github.com/RViMLab/vrviz)
- What it is:
  a native VR application that consumes robotics topics directly, including
  point clouds, images, markers, transforms, and robot models.
- Why it matters:
  it is the clearest donor in this wave for
  `VR-native consumer of robotics topics rather than exporter only`.
- Interesting ideas:
  treat VR as a robotics visualization client; consume multiple topic families
  directly; combine world-space data with overlays or VR camera control.
- Interesting implementation choices:
  `vrviz/src/vrviz_gl.cpp`
  makes the render-side consumer model visible instead of hiding it behind a
  large framework abstraction.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broader research scope than a simple bridge, but important because it shows
  the other end of the pipeline.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `VR as robotics visualization client`
  donor.

## Main takeaways from Wave 67

- `OpenVR tracking export` splits more cleanly into:
  - `simple background tracker collector`
  - `thin ROS bridge`
  - `modular export host`
  - `minimal ROS2 bridge`
  - `record and replay harness`
  - `VR-native robotics topic consumer`
- The strongest lesson from this wave is that
  `tracking export`
  is not one pattern. Publisher modularity, replay, and downstream consumption
  are all separate donor branches.
- Another strong lesson is that `robotics bridge` work overlaps with future
  diagnostics, playback, and tool-harness ideas inside `VR-apps-lab`.

## Reusable methods clarified by this wave

- `OpenVR tracking-export bridge with pluggable publishers for ROS, WebSocket, file, or other consumers`
- `OpenVR pose recorder and replayer that serializes device metadata and motion timelines`
- `Native VR consumer for ROS or robotics topics with both world-space data and HMD-relative overlays`

## Recommended next moves after this wave

1. Treat `openvr_ros_bridge` as the clearest donor for
   `pluggable tracking-export service`.
2. Treat `openvr-input-recorder` as the strongest donor in this wave for
   `record and replay at the runtime layer`.
3. Keep `openvr_ros` and `openvr_ros2_tracker` visible whenever `VR-apps-lab`
   needs thinner bridge baselines than the modular export host.
4. Keep `vrviz` visible whenever a future branch needs a stronger
   `VR-native robotics consumer`
   comparison.
