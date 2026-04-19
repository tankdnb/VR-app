# VR Projects Wave 37: Mixed-VR Controller Bridges, Driver-Side Input Emulation, and Hand-Tracking Adaptation

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `mixed-VR controller bridges`, `driver-side input emulation`, and
  `hand-tracking to controller adaptation`.

## Why this wave exists

`VR-apps-lab` already had strong tracker bridges and custom-device drivers, but
it still needed a clearer picture of `controller-side bridge design`:

- mixed-runtime paths that reuse foreign controllers inside SteamVR;
- generic IPC-driven drivers that can spawn synthetic trackers or controllers;
- hand-tracking repos that attempt full controller emulation instead of only
  finger or skeleton export.

This wave exists to make `controller-emulation architecture` clearer inside
`VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with mixed-VR controller, OpenHMD bridge, IPC driver, and
   hand-emulation queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `mm0zct/Oculus_Touch_Steam_Link` | Strong donor for mixed-runtime controller reuse, with controller-or-tracker behavior and explicit Oculus profile reuse |
| `ChristophHaag/SteamVR-OpenHMD` | Strong donor for a foreign hardware stack bridged into SteamVR through device-index config and vendor-specific profile choices |
| `kodowiec/Yet-Another-OpenVR-IPC-Driver` | Strongest new donor for a generic IPC bridge that can spawn and drive synthetic controllers or trackers |
| `bdub1011/Quest-Link-Hand-Tracking` | Useful product signal for gesture-configurable hand tracking mapped to SteamVR controller semantics, even though the public source is thin |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `mSparks43/PSVR-SteamVR-openHMD` | Useful PSVR-specific comparison node for Linux and OpenHMD work, but weaker than the mainline bridge donors in this wave |

## Deep-pass notes by project

## `mm0zct/Oculus_Touch_Steam_Link`

- GitHub:
  [mm0zct/Oculus_Touch_Steam_Link](https://github.com/mm0zct/Oculus_Touch_Steam_Link)
- What it is:
  a SteamVR driver that reuses Oculus Touch hardware in mixed-VR setups with
  other headsets and calibration tools.
- Why it matters:
  it remains one of the strongest donors in the repo for
  `mixed-runtime controller bridge with explicit profile and model reuse`.
- Interesting ideas:
  allow the same physical controller path to show up as either true controllers
  or tracker-like objects; reuse Oculus input profiles and render models
  instead of inventing new controller semantics; lean on external calibration
  tools instead of hiding mixed-space alignment inside the driver.
- Interesting implementation choices:
  `CustomHMD/OculusTouchLink.cpp` and
  `CustomHMD/TouchControllerDriver.h`
  make the `LibOVR session -> SteamVR tracked devices -> profile, render-model,
  skeleton, and haptic components` flow explicit. The `be_objects` toggle is
  especially useful because it shows how the same hardware can be framed as
  controllers or trackers.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  operational setup depends on several external tools, but that complexity is
  part of the real mixed-VR lesson.
- What to inspect next:
  keep it as a main donor whenever a future path needs
  `foreign controller hardware reused inside SteamVR`.

## `ChristophHaag/SteamVR-OpenHMD`

- GitHub:
  [ChristophHaag/SteamVR-OpenHMD](https://github.com/ChristophHaag/SteamVR-OpenHMD)
- What it is:
  an OpenHMD-backed SteamVR driver that maps foreign HMD and controller devices
  into OpenVR.
- Why it matters:
  it is the clearest donor in the repo for
  `hardware-stack bridge driven by config-level device-role selection`.
- Interesting ideas:
  choose which OpenHMD devices become display, HMD tracker, and controllers
  through a tiny config file; override vendor identity when SteamVR behavior
  depends on specific manufacturer strings; keep hardware selection outside the
  main driver codepath.
- Interesting implementation choices:
  `driver_openhmd.cpp` and
  `ohmd_config.h`
  make the `config file -> OpenHMD device indices -> SteamVR device activation`
  flow explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  older bridge with imperfect controller support, but still a strong donor for
  config-driven foreign-hardware mapping.
- What to inspect next:
  keep it visible whenever a future branch needs a
  `foreign runtime or hardware -> SteamVR driver` comparison.

## `kodowiec/Yet-Another-OpenVR-IPC-Driver`

- GitHub:
  [kodowiec/Yet-Another-OpenVR-IPC-Driver](https://github.com/kodowiec/Yet-Another-OpenVR-IPC-Driver)
- What it is:
  an OpenVR bridge driver that exposes a command-driven IPC surface for adding
  trackers or controllers and updating their state.
- Why it matters:
  it is the strongest new donor in the repo for
  `generic IPC command surface that spawns synthetic controllers and trackers`.
- Interesting ideas:
  keep the bridge contract command-oriented and text-based; let clients add
  devices dynamically; expose both controller-state commands and raw pose
  update commands; keep cross-platform transport support in a thin IPC library.
- Interesting implementation choices:
  `driver/driver_files/src/Driver/VRDriver.cpp`,
  `driver/driver_files/src/Driver/ControllerDevice.cpp`, and
  `driver/libraries/ipc/Ipc.cpp`
  make the `accept IPC command -> create device -> update inputs and pose`
  flow explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  still a learning-oriented bridge, but unusually clean as a donor because the
  command surface and synthetic-device semantics are easy to read.
- What to inspect next:
  treat it as the best current donor whenever a future `VR-apps-lab` tool needs
  `external process -> synthetic controller or tracker` integration.

## `bdub1011/Quest-Link-Hand-Tracking`

- GitHub:
  [bdub1011/Quest-Link-Hand-Tracking](https://github.com/bdub1011/Quest-Link-Hand-Tracking)
- What it is:
  a Quest hand-tracking project framed as full SteamVR controller emulation via
  Oculus Link.
- Why it matters:
  it is a useful product signal for
  `gesture-configurable hand tracking adapted into controller semantics`.
- Interesting ideas:
  keep gesture logic in a simple JSON config; expose controller semantics
  through a dedicated input profile; frame the tool as full controller
  emulation rather than raw hand export.
- Interesting implementation choices:
  `gesture_config/default_config.json` and
  `resources/input_profile.json`
  make the gesture-to-controller contract visible even though the public driver
  source itself is currently thin.
- Code donor value:
  low-medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  the main driver source in the current public snapshot is a placeholder-like
  preview, so the repo cannot honestly be promoted as a strong code donor yet.
- What to inspect next:
  revisit only if the public repo grows a real hand-tracking implementation
  beyond the current thin-source snapshot.

## Main takeaways from Wave 37

- `Controller bridge design` is now clearer as a distinct branch, not just a
  side effect of tracker-bridge work.
- The strongest split in this family is:
  - `mixed-runtime hardware reuse`
  - `foreign hardware mapped through config-selected device roles`
  - `generic IPC bridge that spawns synthetic devices`
  - `gesture-configurable hand tracking framed as controller emulation`
- The most reusable lesson is often the `adaptation contract`:
  - reuse existing vendor input profiles and render models where possible
  - keep device-role selection outside the hardcoded driver path
  - expose controllers through explicit IPC commands and device lifecycle
  - separate gesture config from SteamVR-facing controller semantics

## Reusable methods clarified by this wave

- `IPC command surface that spawns synthetic controllers and trackers`
- `Gesture-configurable hand-tracking bridge that emulates full controllers`

## Recommended next moves after this wave

1. Keep `Oculus_Touch_Steam_Link` as the main donor for
   `mixed-runtime controller reuse`.
2. Keep `SteamVR-OpenHMD` as the main donor for
   `config-selected foreign hardware bridged into SteamVR`.
3. Treat `Yet-Another-OpenVR-IPC-Driver` as the clearest donor for
   `external process -> synthetic controller or tracker`.
4. Keep `Quest-Link-Hand-Tracking` visible as a product signal, but retain an
   honest `Partially studied` status until the public implementation surface is
   stronger.
