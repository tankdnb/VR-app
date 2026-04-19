# VR Projects Wave 31: Teleoperation Workspaces and Embodied Control Surfaces

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `teleoperation workspaces`, `embodied control surfaces`, and
  `VR command menus for external systems`.

## Why this wave exists

Many repositories in `VR-apps-lab` already show overlays, utilities, and input
bridges, but they do not fully cover another valuable product direction:

- VR as a room for controlling other systems;
- menus and side panels as command surfaces for robotics or remote workflows;
- staged connection, preview, and live-control flows instead of one flat scene.

This wave exists to make `VR control-room and teleoperation UX` a stronger
family inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VR teleoperation, ROS VR interface, and robot-control UI
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `leggedrobotics/unity_ros_teleoperation` | Strongest donor for a palm-menu teleoperation shell with subsystem toggles and live status |
| `h2r/ros_reality` | Best small donor for semantic robot-command menus over a websocket bridge |
| `elpis-lab/UR10_Teleop` | Useful comparison donor for a very thin controller-state export frontend |
| `pollen-robotics/ReachyTeleoperation` | Strongest product-like donor for staged teleoperation rooms and side-panel management |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `nakama-lab/VR_Teleop_Interface` | Architecturally interesting, but the public mainline is better treated as a follow-up comparison node than a primary code donor from this pass |
| `h2r/GHOST` | Valuable adjacent visualization and gesture-control node, but stronger as a later comparison with `ros_reality` than as a primary entry in this wave |

## Deep-pass notes by project

## `leggedrobotics/unity_ros_teleoperation`

- GitHub:
  [leggedrobotics/unity_ros_teleoperation](https://github.com/leggedrobotics/unity_ros_teleoperation)
- What it is:
  a Unity and ROS teleoperation environment with palm-menu UI, subsystem
  toggles, and multiple viewer or stream surfaces.
- Why it matters:
  it is the strongest donor in the repo for
  `teleoperation shell with palm menu as control hub`.
- Interesting ideas:
  let a palm menu control multiple subsystems; show connection state directly in
  menu materials; treat the menu as an operations shell rather than a generic
  launcher.
- Interesting implementation choices:
  `Assets/Components/Menu/Scripts/MenuManager.cs` and the related menu prefabs
  make the submenu toggling and ROS-state visualization explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  tied to a robotics context, but the control-surface lessons generalize well.
- What to inspect next:
  compare it with overlay-first utility hosts to see how much of a future
  `operations dashboard in VR` should live on the hand versus in detached
  workspace panels.

## `h2r/ros_reality`

- GitHub:
  [h2r/ros_reality](https://github.com/h2r/ros_reality)
- What it is:
  an older VR robotics interface with menu demos and semantic command buttons.
- Why it matters:
  it is the clearest donor in the repo for
  `semantic action menu over a websocket bridge`.
- Interesting ideas:
  keep the VR layer simple; map button presses directly to high-level robot
  actions; treat teleoperation UI as a semantic command surface, not only a
  pose-stream pipe.
- Interesting implementation choices:
  `Assets/Scripts/EinMenuScript.cs` makes the `UI button -> websocket command`
  flow very visible.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  narrower and older than the more product-like teleoperation shells.
- What to inspect next:
  keep it as the best reference for small command-menu surfaces that control an
  external system through semantic messages.

## `elpis-lab/UR10_Teleop`

- GitHub:
  [elpis-lab/UR10_Teleop](https://github.com/elpis-lab/UR10_Teleop)
- What it is:
  a very thin Unity VR frontend that exports controller pose and button state
  to an external robotics process.
- Why it matters:
  it is the strongest donor in the repo for
  `thin VR control frontend with external process ownership`.
- Interesting ideas:
  keep the Unity side minimal; send transformed controller pose, buttons, and
  frame-timed updates over a socket; reconnect cleanly instead of assuming a
  one-shot transport.
- Interesting implementation choices:
  `VR-Teleop/Assets/Scripts/SendVRControllerData.cs` makes the
  `XR controller -> socket payload` loop explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  more of a transport donor than a broader menu donor.
- What to inspect next:
  keep it as the minimum useful reference whenever a future tool needs a thin
  `VR frontend -> external control process` boundary.

## `pollen-robotics/ReachyTeleoperation`

- GitHub:
  [pollen-robotics/ReachyTeleoperation](https://github.com/pollen-robotics/ReachyTeleoperation)
- What it is:
  a more product-like VR teleoperation stack with staged scenes for connection,
  mirror, and live control.
- Why it matters:
  it is the strongest donor in the repo for
  `staged teleoperation workspace with side panels and setup flow`.
- Interesting ideas:
  separate connection, preview, and control into distinct rooms; manage side
  menus as part of the teleoperation lifecycle; include a VR keyboard for
  configuration and IP entry instead of punting setup to desktop-only flows.
- Interesting implementation choices:
  `Assets/Scripts/Manager/TeleoperationManager.cs`,
  `Assets/Scripts/Miscellaneous/VRKeyboard.cs`, and the split scenes make the
  lifecycle and setup/control boundary easy to study.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  larger and more product-shaped than the rest of the family.
- What to inspect next:
  use it as the main reference whenever a future `VR-apps-lab` tool needs a
  `connection room -> operational room` progression.

## Main takeaways from Wave 31

- `Embodied control surfaces` are a real family, not a robotics-only anomaly.
- The strongest split in this family is:
  - `palm-menu teleoperation shell`
  - `semantic action menu`
  - `thin controller-data export frontend`
  - `staged teleoperation workspace`
- The most reusable lesson is often `workflow structure`, not robotics logic:
  - connection state
  - setup flow
  - control-room layout
  - separation between VR frontend and external process ownership

## Reusable methods clarified by this wave

- `Teleoperation workspace with palm-menu control hub and live connection-state surfaces`
- `Thin VR control frontend that streams controller state to an external robot or service process`

## Recommended next moves after this wave

1. Treat `unity_ros_teleoperation` and `ReachyTeleoperation` as the strongest
   donors for `VR control-room` design.
2. Keep `ros_reality` as the best small donor for semantic command-menu flows.
3. Use `UR10_Teleop` whenever a future prototype needs the thinnest possible
   `controller state exporter` pattern.
