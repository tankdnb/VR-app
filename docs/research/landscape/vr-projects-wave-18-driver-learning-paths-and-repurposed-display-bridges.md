# VR Projects Wave 18: Driver Learning Paths and Repurposed Display Bridges

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `driver learning paths`, `custom-device providers`, and
  `DIY or repurposed-display bridges`.

## Why this wave exists

The repository already had a meaningful set of driver-related repos, but the
learning story was still uneven:

- some repos taught the raw OpenVR driver shape well;
- some taught `device-provider architecture` better than API basics;
- some showed how to turn unconventional hardware into a useful SteamVR device
  even when the hardware target itself was niche.

This wave exists to make the `driver-side learning track` more coherent and
less dependent on scattered partial notes.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with driver tutorial and custom-device family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, overlap, and donor value;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `terminal29/Simple-OpenVR-Driver-Tutorial` | Best current public learning-path repo for sample-like OpenVR driver structure |
| `LucidVR/opengloves-driver` | Strong modular device-provider stack with multiple transports and a sidecar process |
| `TrueOpenVR/SteamVR-TrueOpenVR` | Good bridge-style example for sample-derived HMD and controller emulation tied to an external standard |
| `DaniXmir/GlassVr` | Repurposed AR-glasses bridge that mixes an OpenVR driver with a large Python sidecar |
| `r57zone/OpenVR-ArduinoHMD` | Clear DIY HMD path built around config-driven display setup and Arduino sensor input |

## Deep-pass notes by project

## `terminal29/Simple-OpenVR-Driver-Tutorial`

- GitHub:
  [terminal29/Simple-OpenVR-Driver-Tutorial](https://github.com/terminal29/Simple-OpenVR-Driver-Tutorial)
- What it is:
  a tutorial repo that walks through a central driver manager and multiple
  tracked device types.
- Why it matters:
  it is the cleanest public `learning path` repo in this family because it
  explicitly teaches device registration, settings, events, frame timing, and
  debugging setup.
- Interesting ideas:
  treat the driver as a central owner of devices and OpenVR events; keep device
  classes split into HMD, controller, tracker, and tracking reference types;
  teach Visual Studio debugging against `vrstartup` and `vrserver`.
- Interesting implementation choices:
  `IVRDriver.hpp` defines a driver abstraction around device lists, settings,
  input, properties, and logging;
  the tutorial reads settings through `VRSettings`, logs to `VRDriverLog`, and
  uses a simple frame loop to update devices and collect runtime events.
- Code donor value:
  high.
- Product reference value:
  low.
- Architecture reference value:
  high.
- Caveats:
  sample-like by design and not meant as an end-user product.
- What to inspect next:
  compare it directly with `openvr-driver-example` and Valve's stock samples as
  one onboarding path.

## `LucidVR/opengloves-driver`

- GitHub:
  [LucidVR/opengloves-driver](https://github.com/LucidVR/opengloves-driver)
- What it is:
  a SteamVR driver for gloves and DIY hardware with serial, Bluetooth, and
  named-pipe transport paths plus a companion overlay/UI ecosystem.
- Why it matters:
  it is one of the strongest examples of `modular custom-device provider with
  sidecar`.
- Interesting ideas:
  separate the SteamVR driver from device probing and user-facing tools; start
  internal and external services before attaching SteamVR devices; let the same
  driver support multiple transport modes and left/right hand configuration.
- Interesting implementation choices:
  `driver_factory.cpp` exposes a single `PhysicalDeviceProvider`;
  `physical_device_provider.cpp` launches background services and an overlay
  process, builds a structured server configuration from driver settings,
  starts a prober, and attaches left and right `KnuckleDeviceDriver` instances
  to discovered glove devices.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  large enough that hand skeleton, force feedback, and calibration deserve
  their own future pass.
- What to inspect next:
  focus later on skeletal input, offsets, and calibration automation rather
  than repeating the provider/bootstrap slice.

## `TrueOpenVR/SteamVR-TrueOpenVR`

- GitHub:
  [TrueOpenVR/SteamVR-TrueOpenVR](https://github.com/TrueOpenVR/SteamVR-TrueOpenVR)
- What it is:
  a bridge-style SteamVR driver that reads HMD and controller data from an
  external `TrueOpenVR` DLL surface and exposes config-driven HMD display
  behavior.
- Why it matters:
  it is a useful reference for `sample-derived driver plus foreign data bridge`
  rather than for polished driver architecture.
- Interesting ideas:
  keep most behavior in a single driver file; use config for distortion, FOV,
  stereo mode, window placement, and debug behavior; load an external bridge
  DLL for HMD and controller data instead of embedding the hardware logic.
- Interesting implementation choices:
  `driver_sample.cpp` declares function pointers such as `GetHMDData`,
  `GetControllersData`, `SetControllerData`, and `SetCentering`, then feeds
  that state into a sample-derived HMD and controller implementation with
  SteamVR property setup and display config.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  the real hardware or runtime logic sits behind an external standard or DLL,
  so the public repo is better as a bridge example than as a full donor.
- What to inspect next:
  only revisit if the public `TrueOpenVR` surface becomes easier to map in
  source form.

## `DaniXmir/GlassVr`

- GitHub:
  [DaniXmir/GlassVr](https://github.com/DaniXmir/GlassVr)
- What it is:
  an OpenVR driver plus a large Python sidecar for turning XR or AR glasses and
  other nonstandard hardware setups into SteamVR HMD, controller, tracker, or
  hand-tracking flows.
- Why it matters:
  it is one of the strongest `repurposed hardware bridge` references in the
  repo because it mixes display bridging, copied tracking, offsets, webcam hand
  tracking, and controller emulation in one stack.
- Interesting ideas:
  treat position and rotation as separable inputs; allow one device to donate
  pose to another with offsets; bridge to OpenGloves named pipes for hand
  tracking; keep a large desktop control surface for nontrivial setup and
  experimentation.
- Interesting implementation choices:
  `code-glassvrserver/main.py` is a very large PyQt sidecar that owns the UI,
  settings, MediaPipe and OpenCV ingestion, named-pipe access, and many
  bridging behaviors;
  the OpenVR side is still sample-derived, but the overall product value comes
  from the sidecar-plus-driver split and the willingness to mix multiple data
  sources.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  broad, experimental, and somewhat chaotic; the public value is in the
  patterns and product ambition more than in polished internals.
- What to inspect next:
  narrow a future pass to data-ingress contracts, tracking overrides, and the
  actual bridge surfaces between the Python sidecar and the driver.

## `r57zone/OpenVR-ArduinoHMD`

- GitHub:
  [r57zone/OpenVR-ArduinoHMD](https://github.com/r57zone/OpenVR-ArduinoHMD)
- What it is:
  a DIY HMD driver that combines an external display with Arduino-based
  rotation tracking.
- Why it matters:
  it is a clean `repurposed display + external sensor = synthetic HMD` example
  with straightforward configuration and setup guidance.
- Interesting ideas:
  use SteamVR settings as the main configuration surface; treat monitor
  placement and optical parameters as user-tunable values; expose centering and
  crouch controls; ship a tiny assistant utility around the core driver path.
- Interesting implementation choices:
  the README and settings model treat window position, render size, FOV, IPD,
  and lens distortion as first-class user inputs;
  the repo includes a driver sample tree plus a helper app and references to
  Arduino sensor protocols for yaw/pitch/roll or quaternion data.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  tied to a DIY hardware workflow and older sensor/firmware assumptions.
- What to inspect next:
  compare it with `OpenPSVR`, `VRto3D`, and `RayNeo-Air-3S-Pro-OpenVR` as one
  `repurposed display becomes HMD` family.

## Main takeaways from Wave 18

- `Driver-side research` is now clearer as a multi-branch learning track.
- The most useful split is:
  - `tutorial baseline`
  - `modular device provider with sidecar`
  - `bridge-style sample-derived driver`
  - `repurposed display plus external tracker`
- Hardware niche does not automatically make a repo weak if the architecture is
  reusable.

## Reusable methods clarified by this wave

- `Multi-transport custom-device provider with sidecar control surface`
- `Repurposed display plus sensor stack as synthetic HMD`

## Recommended next moves after this wave

1. Treat `Simple-OpenVR-Driver-Tutorial` as the primary onboarding reference in
   the driver-learning family.
2. Keep `opengloves-driver` visible as the strongest provider-plus-sidecar
   donor in the family.
3. Revisit `GlassVr` and `TrueOpenVR` only with tighter boundaries so the next
   pass stays architecture-focused.
