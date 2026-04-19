# VR Projects Wave 19: Vendor Mods, Repurposed Output Bridges, and Alternative Hardware Paths

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `vendor enhancement tooling`, `repurposed output bridges`, and
  `alternative hardware paths`.

## Why this wave exists

The repository already had strong coverage of:

- driver tutorials and synthetic device paths;
- tracker bridges and no-HMD development helpers;
- overlay hosts and runtime-side tools.

What still needed a clearer synthesis was the family where:

- official vendor stacks are `wrapped or augmented` instead of replaced;
- repurposed displays and glasses become `quasi-XR hardware`;
- public repos may be strategically interesting even when the visible source is
  thin.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with vendor-enhancement and hardware-bridge family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, overlap, and donor value;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `BnuuySolutions/PSVR2Toolkit` | Strongest current vendor-enhancement donor in the repo |
| `krazysh01/VirtualDesktop-OpenVR-Trackers` | Needed an honest re-check because earlier assumptions about donor value had to be validated against the current public snapshot |
| `verncat/RayNeo-Air-3S-Pro-OpenVR` | Useful bridge between a glasses SDK and a still-thin OpenVR driver path |
| `alatnet/OpenPSVR` | Important legacy full-driver path for repurposed headset hardware |

## Secondary candidate surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `OpenDisplayXR/OpenDisplayXR-VDD` | Strategically relevant idea, but the public GitHub state is still too sparse to classify as a real donor |

## Deep-pass notes by project

## `BnuuySolutions/PSVR2Toolkit`

- GitHub:
  [BnuuySolutions/PSVR2Toolkit](https://github.com/BnuuySolutions/PSVR2Toolkit)
- What it is:
  an unofficial enhancement layer over Sony's official PS VR2 PC driver that
  adds extra capabilities such as eye tracking, improved haptics, and adaptive
  trigger control.
- Why it matters:
  it is the clearest `augment the official stack instead of replacing it`
  reference in the repo.
- Interesting ideas:
  rename and load the original vendor DLL; proxy the original `HmdDriverFactory`
  surface; hook internal HMD and USB paths; expose extra capabilities over
  versioned local IPC; keep a separate app and developer-facing API in the same
  ecosystem.
- Interesting implementation choices:
  `hmd_driver_loader.cpp` locates and loads the original
  `driver_playstation_vr2_orig.dll`;
  `ipc_server.cpp` runs a TCP IPC server with handshake, versioning, and gaze
  or trigger-related commands;
  the `psvr2_openvr_driver_ex` project contains hook and proxy layers around
  the vendor driver;
  the repo also ships a small WPF app and public headers for developers.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  tightly coupled to vendor updates, legal boundaries, and a non-commercial
  positioning.
- What to inspect next:
  revisit calibration limits, gaze stability, and the public API surface rather
  than repeating the loader/proxy slice.

## `krazysh01/VirtualDesktop-OpenVR-Trackers`

- GitHub:
  [krazysh01/VirtualDesktop-OpenVR-Trackers](https://github.com/krazysh01/VirtualDesktop-OpenVR-Trackers)
- What it is:
  currently a much thinner public repo than earlier expectations suggested.
- Why it matters:
  it is a useful reminder that the repo should describe the current public
  source honestly, not the implied product direction alone.
- Interesting ideas:
  the product direction still points at `external body-state -> SteamVR
  trackers`, but the current public snapshot looks heavily tutorial-derived and
  exposes only a very small visible custom implementation surface.
- Interesting implementation choices:
  the public tree still centers on `driver_files/src/Driver/*` sample-like
  classes;
  `VRDriver.cpp` and `TrackerDevice.cpp` look close to tutorial scaffolding,
  which makes the repo a weaker donor than its name alone suggests.
- Code donor value:
  low-medium.
- Product reference value:
  medium.
- Architecture reference value:
  low-medium.
- Caveats:
  the currently visible public code is too thin to treat as a strong mainline
  donor.
- What to inspect next:
  revisit only if the public repo grows a real data-ingress surface or a
  clearer tracker-role mapping implementation.

## `verncat/RayNeo-Air-3S-Pro-OpenVR`

- GitHub:
  [verncat/RayNeo-Air-3S-Pro-OpenVR](https://github.com/verncat/RayNeo-Air-3S-Pro-OpenVR)
- What it is:
  a lightweight cross-platform SDK for RayNeo glasses plus an optional OpenVR
  stub driver.
- Why it matters:
  it shows a practical intermediate pattern where `SDK maturity` is stronger
  than `driver maturity`, but both still belong in the same public repo.
- Interesting ideas:
  separate the transport and protocol SDK from the OpenVR driver; keep the
  driver optional; support Windows, Linux, and macOS at the SDK level; use
  EDID detection and IMU polling in the driver stub.
- Interesting implementation choices:
  `RayneoApi.cpp` owns libusb or HID transport, event queuing, command parsing,
  and IMU/device-info handling;
  `openvr_driver/src/device_provider.cpp` initializes the RayNeo SDK, switches
  the glasses into 3D mode, enables IMU streaming, and runs an event thread;
  `hmd_device_driver.cpp` derives display configuration from EDID and feeds
  IMU orientation into an HMD pose.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  the current OpenVR driver is still explicitly a stub and has moved toward a
  dedicated separate driver repo.
- What to inspect next:
  re-check the dedicated driver repo once the stub evolves into a fuller
  hardware bridge.

## `alatnet/OpenPSVR`

- GitHub:
  [alatnet/OpenPSVR](https://github.com/alatnet/OpenPSVR)
- What it is:
  a legacy but still valuable full SteamVR driver for the original PSVR headset
  with monitor detection, display setup, and IMU-based head tracking.
- Why it matters:
  it is one of the strongest older references for `repurposed headset hardware
  becomes a real OpenVR HMD driver`.
- Interesting ideas:
  own the full HMD lifecycle; query the hardware directly; find the display in
  Windows; power the headset on and off; run a sensor thread; expose a proper
  `IVRDisplayComponent`.
- Interesting implementation choices:
  `ServerDriver_OpenPSVR.cpp` opens the PSVR context and registers the HMD with
  SteamVR;
  `OpenPSVRDeviceDriver.cpp` reads PSVR device info, derives serial and display
  state, configures display and render settings, powers the headset on, starts
  sensor updates, and exposes pose data through an AHRS or integrator path.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  older toolchain assumptions and unfinished controller/camera ambitions make
  it a legacy donor rather than a polished current product.
- What to inspect next:
  inspect controller ambitions, installer flow, and calibration quality only if
  a later PSVR family pass becomes necessary.

## `OpenDisplayXR/OpenDisplayXR-VDD`

- GitHub:
  [OpenDisplayXR/OpenDisplayXR-VDD](https://github.com/OpenDisplayXR/OpenDisplayXR-VDD)
- What it is:
  currently a one-line public signal about a simulated OpenVR or OpenXR virtual
  hardware device driver.
- Why it matters:
  the product direction is relevant even though the public source is not yet.
- Code donor value:
  low.
- Product reference value:
  medium.
- Architecture reference value:
  low.
- Caveats:
  source-light.
- What to inspect next:
  only revisit once public code or technical detail exists.

## Main takeaways from Wave 19

- `Vendor enhancement` is now clearly separate from `repurposed hardware
  driver` work.
- The most useful split is:
  - `official-driver wrapper and hook layer`
  - `SDK-first hardware bridge with optional driver`
  - `legacy full driver for repurposed headset hardware`
  - `source-light strategic signal`
- Public source quality varies sharply in this family, so honest labeling is
  part of the research value.

## Reusable methods clarified by this wave

- `Vendor-driver wrapper with proxy hooks and local IPC`
- `SDK-first hardware bridge with optional runtime driver`

## Recommended next moves after this wave

1. Keep `PSVR2Toolkit` as the main vendor-enhancement donor but leave it
   partially open for deeper API and calibration study.
2. Promote `OpenPSVR` as a stronger historical donor for repurposed headset
   hardware.
3. Leave `OpenDisplayXR-VDD` and the current `VirtualDesktop-OpenVR-Trackers`
   snapshot labeled cautiously instead of inflating their donor value.
