# VR Projects Wave 12: Synthetic Devices, Input Emulation, and DIY Driver Paths

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet in `VR-apps-lab`, focusing on synthetic devices,
  input-emulation sidecars, DIY/custom-hardware drivers, and
  motion-manipulation paths around `SteamVR/OpenVR`.

## Why this wave exists

The repository already had stronger coverage of:

- runtime adapters and OpenXR bring-up references;
- virtual-display and repurposed-output workflows;
- workflow micro-utilities and validation tools;
- classic overlay suites, tracker bridges, and several driver tutorials.

What was still missing was a denser layer of:

- `legacy and niche hardware bridge drivers`;
- `sample-derived custom-device paths` that stay smaller than a product stack;
- `input-emulation sidecars` that piggyback on existing tracked devices;
- `pose-rewrite` or `motion-compensation` drivers;
- low-cost `DIY controller/HMD` experiments that teach concrete SteamVR
  plumbing tricks.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with focused queries and topic streams;
2. deduplicate against the registry;
3. freeze a shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `ValveSoftware/driver_hydra` | Official peripheral-bridge driver sample with calibration-monitor flow |
| `alatnet/OpenPSVR` | Full legacy HMD/display driver path for PSVR hardware |
| `r57zone/OpenVR-driver-for-DIY` | Sample-derived DIY null-HMD and controller path |
| `gpsnmeajp/SegsVRControllerDriverSample` | Shared-memory controller-driver sample with external client |
| `puresoul/Barebone` | Gamepad-driven synthetic Vive controller emulation |
| `mmorselli/Joy2OpenVR` | DirectInput-to-InputEmulator sidecar for unusual physical controllers |
| `mdovgialo/SteamVR-Glove` | Arduino glove proof of concept built on top of an existing tracked controller |
| `openvrmc/OpenVR-MotionCompensation` | Pose-rewrite driver plus in-VR dashboard for simulator motion compensation |

## Secondary candidate surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `verncat/RayNeo-Air-3S-Pro-OpenVR` | The repository currently looks more like early SDK scaffolding than a clear OpenVR driver or bridge implementation, so it remains a useful signal but not yet a strong code donor |

## Deep-pass notes by project

## `ValveSoftware/driver_hydra`

- GitHub:
  [ValveSoftware/driver_hydra](https://github.com/ValveSoftware/driver_hydra)
- What it is:
  an official SteamVR/OpenVR driver for the `Razer Hydra` using the
  `Sixense SDK`.
- Why it matters:
  it is one of the clearest public references for `legacy peripheral bridge
  drivers`, especially when they must coexist with another HMD driver.
- Interesting ideas:
  explicit multi-driver coexistence through `activateMultipleDrivers`; launch a
  dedicated `hydra_monitor` calibration utility; keep realignment and chorded
  system-button behavior inside the driver flow.
- Interesting implementation choices:
  `CServerDriver_Hydra` scans controllers on a background thread; each
  `CHydraHmdLatest` combines `ITrackedDeviceServerDriver` with
  `IVRControllerComponent`; the repo ships a dedicated monitor tool under
  `tools/` instead of hiding calibration inside the driver DLL only.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  tied to an old hardware stack and older OpenVR driver interfaces.
- What to inspect next:
  coordinate realignment flow, the monitor tool handoff, and how its older API
  shape compares with more modern sample drivers.

## `alatnet/OpenPSVR`

- GitHub:
  [alatnet/OpenPSVR](https://github.com/alatnet/OpenPSVR)
- What it is:
  an open-source `OpenVR` driver for `PlayStation VR` hardware.
- Why it matters:
  it adds a much more ambitious `full HMD/display driver` reference than the
  smaller tutorial and synthetic-device samples already in the repo.
- Interesting ideas:
  unify PSVR display, sensor, and future controller/camera ambitions inside one
  driver project; keep build, generate, clean, and deploy scripts self-contained;
  treat SteamVR driver packaging as a first-class part of the repo.
- Interesting implementation choices:
  `COpenPSVRDeviceDriver` implements both `ITrackedDeviceServerDriver` and
  `IVRDisplayComponent`; `CServerDriver_OpenPSVR` and
  `WatchdogDriver_OpenPSVR` split startup/runtime concerns; the source tree
  includes `Mahony`, `Madgwick`, and `BMI055` sensor-fusion code directly in the
  driver path.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  ambitious, older, and not fully exhausted by one pass, especially beyond the
  HMD path.
- What to inspect next:
  controller and camera ambitions, monitor detection quality, and installer
  versus manual deployment flow.

## `r57zone/OpenVR-driver-for-DIY`

- GitHub:
  [r57zone/OpenVR-driver-for-DIY](https://github.com/r57zone/OpenVR-driver-for-DIY)
- What it is:
  a keyboard-driven DIY `OpenVR/SteamVR` driver for moving a virtual HMD and
  controllers.
- Why it matters:
  it is a compact reference for `sample-derived no-hardware prototyping`, not a
  polished bridge product.
- Interesting ideas:
  manual keyboard control of HMD and controller transforms; keep the repo close
  to the OpenVR sample layout so the learning path stays obvious; support
  Windows and Linux builds for the same experiment.
- Interesting implementation choices:
  the structure stays very close to `driver_sample` with
  `CServerDriver_Sample`, one sample HMD, and two controller drivers; the repo
  mostly reshapes the sample through custom bindings, settings, and packaging
  rather than inventing a new architecture from scratch.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  heavily sample-derived and intentionally manual rather than sensor-driven.
- What to inspect next:
  whether it adds meaningful pose logic beyond the sample, or mainly acts as a
  pragmatic repackaging of the stock driver tutorial.

## `gpsnmeajp/SegsVRControllerDriverSample`

- GitHub:
  [gpsnmeajp/SegsVRControllerDriverSample](https://github.com/gpsnmeajp/SegsVRControllerDriverSample)
- What it is:
  an OpenVR controller-driver sample that also ships a small external client
  using `shared memory` and `JSON`.
- Why it matters:
  it adds a very useful `driver + external process` comparison node that is
  more explicit than most pure sample repos.
- Interesting ideas:
  keep the driver sample close to Valve's baseline but feed it from a helper
  client; use a small memory-mapped shared-memory wrapper instead of a more
  complex IPC stack; document a keyboard-driven sample client for quick testing.
- Interesting implementation choices:
  `driver_sample.cpp` keeps the controller-driver path readable; the client
  wraps `CreateFileMapping` and `MapViewOfFile` behind a `SharedMemory` helper;
  `picojson` is used to structure payloads across the sidecar boundary.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  older Visual Studio assumptions, hardcoded local include paths, and mostly
  Japanese comments make the repo rougher than the concept itself.
- What to inspect next:
  the actual JSON payload schema, synchronization rules, and whether the
  sidecar pattern generalizes into a more modern bridge service.

## `puresoul/Barebone`

- GitHub:
  [puresoul/Barebone](https://github.com/puresoul/Barebone)
- What it is:
  an OpenVR controller driver that emulates `Vive` controllers from an
  `XInput` gamepad and places them relative to the HMD.
- Why it matters:
  it is one of the strongest examples in the wave for `synthetic controller
  emulation` without dedicated hardware sensors.
- Interesting ideas:
  single-controller and dual-controller modes; HMD-relative controller offsets;
  gamepad-driven rotation, touchpad, trigger, grip, and system input; extra
  helper projects around device enumeration and Daydream experiments.
- Interesting implementation choices:
  `driver_barebone.cpp` combines gamepad polling with explicit quaternion math
  and `VRDriverInput` components; the repo is not just a driver DLL, but a small
  cluster of helper programs and experiments living next to the main driver.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  the author explicitly frames it as an early OpenVR project, so the quality is
  uneven and the repo carries more exploratory weight than polish.
- What to inspect next:
  how the helper utilities relate to the driver, whether offsets can be
  persisted cleanly, and how much of the repo is stable enough to reuse
  directly.

## `mmorselli/Joy2OpenVR`

- GitHub:
  [mmorselli/Joy2OpenVR](https://github.com/mmorselli/Joy2OpenVR)
- What it is:
  a desktop-side translator from `DirectInput` joystick events into
  `OpenVR-InputEmulator` commands.
- Why it matters:
  it sharpens the `input-emulation sidecar` pattern, where a niche controller
  does not become a full driver but still becomes usable in VR.
- Interesting ideas:
  map arbitrary joystick buttons and axes into two SteamVR controllers through
  a config file; emit controller commands by shelling into a bundled
  command-line helper; support unusual real-world devices such as the `Cabela
  TopShot Elite`.
- Interesting implementation choices:
  an `SFML` desktop app polls joystick state, applies config-driven deadzones
  and mappings, and forwards actions to `client_commandline.exe`; the tool keeps
  its mapping model in `config.ini` rather than forcing recompilation for each
  device.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  the tool depends on an old SteamVR build and the original
  `OpenVR-InputEmulator`, which heavily limits present-day drop-in reuse.
- What to inspect next:
  whether its mapping model can be re-targeted to maintained InputEmulator
  forks or to a future `VR-apps-lab` sidecar helper.

## `mdovgialo/SteamVR-Glove`

- GitHub:
  [mdovgialo/SteamVR-Glove](https://github.com/mdovgialo/SteamVR-Glove)
- What it is:
  a minimal VR glove proof of concept that uses an `Arduino Nano`, a tracked
  Vive controller for pose, and `OpenVR-InputEmulator` for button and axis
  injection.
- Why it matters:
  it is a clean example of a `hybrid sidecar` path: reuse existing tracking,
  then add custom physical input on top.
- Interesting ideas:
  avoid building a full tracking stack; strap the glove to a controller whose
  pose already exists; use a tiny serial protocol from the Arduino sketch to
  drive trigger, grip, and trackpad states.
- Interesting implementation choices:
  the console app opens a COM port, finds the target controller by serial
  number, and emits button/axis events through `vrinputemulator`; the repo keeps
  both the PC-side code and the Arduino sketch in one place.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  highly specific hardware assumptions, hardcoded serial settings, and legacy
  InputEmulator dependence keep it closer to proof of concept than reusable
  platform.
- What to inspect next:
  Arduino protocol details, extensibility beyond binary touch states, and
  whether the same pattern can serve other custom wearables.

## `openvrmc/OpenVR-MotionCompensation`

- GitHub:
  [openvrmc/OpenVR-MotionCompensation](https://github.com/openvrmc/OpenVR-MotionCompensation)
- What it is:
  an OpenVR driver that applies motion compensation to the HMD pose and ships
  an in-VR dashboard for configuration.
- Why it matters:
  it adds a very important `pose-rewrite driver` pattern to the repository,
  bridging custom-device plumbing with calibration and simulator tooling.
- Interesting ideas:
  intercept or rewrite pose updates before the runtime consumes them; expose
  settings through an in-VR dashboard instead of desktop config only; keep a
  shared library layer between the driver and client-facing surfaces.
- Interesting implementation choices:
  the repo is split into `driver_vrmotioncompensation`,
  `lib_vrmotioncompensation`, `client_overlay`, and `installer`; the exported
  driver entry point stays tiny while the deeper behavior is pushed into named
  driver classes and helper libraries.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  by its own README this is a hacky driver-side path that can break when Valve
  changes the driver API.
- What to inspect next:
  hook boundaries, calibration flow, overlay/library coordination, and how this
  differs from `OpenXR-MotionCompensation`.

## Cross-wave synthesis

Wave 12 made the `custom hardware and driver plumbing` branch of
`VR-apps-lab` much denser and more coherent:

- `Driver tutorials and custom-device plumbing`
  no longer stop at generic examples. The family now includes an official
  peripheral bridge (`driver_hydra`), a full legacy HMD path (`OpenPSVR`),
  a sample-derived DIY driver (`OpenVR-driver-for-DIY`), and a gamepad-driven
  synthetic controller path (`Barebone`).
- `Input-emulation sidecars`
  became clearer as a distinct sub-pattern through `Joy2OpenVR` and
  `SteamVR-Glove`, which both reuse existing tracked devices or legacy
  InputEmulator tooling instead of introducing a new full driver stack.
- `Pose manipulation and simulator-linked drivers`
  became more concrete through `OpenVR-MotionCompensation`, which shows a
  larger `driver + library + in-VR dashboard` split rather than a single DLL.

## Most reusable methods clarified by this wave

- `official or sample-derived peripheral bridge driver`
- `sample plus helper-client synthetic controller path`
- `input-emulation sidecar over an existing tracked device`
- `DIY hybrid device that reuses existing tracking`
- `pose-rewrite driver with library and overlay companions`

## Best follow-up work after this wave

1. deepen `OpenPSVR`, especially controller, camera, and installer boundaries;
2. deepen `OpenVR-MotionCompensation` around its hook points and
   overlay/library coordination model;
3. compare `Barebone`, `Joy2OpenVR`, `SteamVR-Glove`, and
   `OpenVR-InputEmulator` as one `synthetic device and input-emulation sidecar`
   family;
4. compare `driver_hydra`, `OpenPSVR`, `OpenVR-driver-for-DIY`,
   `OpenVR-ArduinoHMD`, and `RayNeo-Air-3S-Pro-OpenVR` as one `legacy and
   niche hardware bridge` family.
