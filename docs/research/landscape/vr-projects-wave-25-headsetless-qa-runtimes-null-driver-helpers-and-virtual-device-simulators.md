# VR Projects Wave 25: Headsetless QA Runtimes, Null-Driver Helpers, and Virtual Device Simulators

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `headsetless QA runtimes`, `null-driver helpers`, and
  `virtual device simulators`.

## Why this wave exists

The repository already knew several `no-HMD` tricks and references, but the
family was still fragmented:

- some repos were only manual recipes;
- others were real drivers or runtimes;
- some were simulator platforms with proper external control surfaces;
- a few were only weak source signals that still mattered strategically.

This wave exists to make `headsetless development and fake-hardware QA` a clear
architecture family inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with no-HMD, simulator, virtual-driver, and fake-hardware
   family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `username223/SteamVRNoHeadset` | Best pure recipe reference for null-driver SteamVR workflows |
| `n1ckfg/ViveTrackerExample` | Practical tracker-without-HMD workflow node |
| `oleuzop/VirtualSteamVRDriver` | Clear virtual-HMD SteamVR driver donor |
| `elliotttate/OpenXR-Simulator` | Strong desktop-window OpenXR runtime simulator |
| `shieldmeidunn/SteamVRNullFlipper` | Useful config-swap micro-tool for toggling null-driver mode |
| `OpenDisplayXR/OpenDisplayXR-VDD` | Source-light but strategically relevant virtual hardware signal |
| `chnoblouch/aethervr` | Strong camera-driven custom runtime donor |
| `ox-runtime/ox-sim-driver` | Strongest automation-friendly simulator platform surfaced in this pass |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `davidrios/openxr-device-simulator` | Interesting Rust runtime simulator signal, but still too thin publicly to promote beyond a follow-up node |

## Deep-pass notes by project

## `username223/SteamVRNoHeadset`

- GitHub:
  [username223/SteamVRNoHeadset](https://github.com/username223/SteamVRNoHeadset)
- What it is:
  a configuration recipe for running SteamVR without a headset.
- Why it matters:
  it is the cleanest reference in the repo for `manual null-driver workflow`.
- Interesting ideas:
  sometimes the right donor is not code but a minimal, repeatable config model;
  make the required `forcedDriver`, `requireHmd`, and multi-driver settings
  explicit.
- Interesting implementation choices:
  the repo's value is almost entirely in the documented SteamVR settings shape
  and usage sequence.
- Code donor value:
  low.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  not a software donor in the usual sense.
- What to inspect next:
  keep it mainly as a workflow reference and compare it with helper tools that
  automate the same configuration changes.

## `n1ckfg/ViveTrackerExample`

- GitHub:
  [n1ckfg/ViveTrackerExample](https://github.com/n1ckfg/ViveTrackerExample)
- What it is:
  a tracker-without-HMD workflow guide with a tiny Unity-side example.
- Why it matters:
  it is a useful reference for the practical `what users actually need to do`
  side of no-HMD workflows.
- Interesting ideas:
  do not treat tracker-only workflows as a purely theoretical config problem;
  include the operational steps, dongle assumptions, and practical bring-up
  guidance.
- Interesting implementation choices:
  the donor value is mostly in the workflow notes and tiny helper framing, not
  in deep driver code.
- Code donor value:
  low-medium.
- Product reference value:
  medium.
- Architecture reference value:
  low-medium.
- Caveats:
  mainly a workflow reference.
- What to inspect next:
  compare it with richer simulator and virtual-driver repos when designing a
  later `headsetless QA playbook`.

## `oleuzop/VirtualSteamVRDriver`

- GitHub:
  [oleuzop/VirtualSteamVRDriver](https://github.com/oleuzop/VirtualSteamVRDriver)
- What it is:
  a virtual HMD SteamVR driver for development without physical headset
  hardware.
- Why it matters:
  it is the strongest donor in this wave for
  `virtual HMD driver with configurable desktop controls`.
- Interesting ideas:
  use a fake HMD with desktop input; expose headset profiles; keep the virtual
  device small and focused on bring-up and testing.
- Interesting implementation choices:
  `src/hmd_device_driver.cpp`, `src/device_provider.cpp`,
  `src/Configuration.cpp`, and the default driver settings make the virtual HMD
  boundary very clear.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  this is a driver-centric path, not a runtime simulator.
- What to inspect next:
  compare it directly with OpenXR simulators to isolate where
  `driver-level fake hardware` is better than `runtime-level simulation`.

## `elliotttate/OpenXR-Simulator`

- GitHub:
  [elliotttate/OpenXR-Simulator](https://github.com/elliotttate/OpenXR-Simulator)
- What it is:
  a lightweight OpenXR runtime that simulates a headset and controllers in a
  desktop window.
- Why it matters:
  it is the clearest donor in the repo for `desktop simulator runtime`.
- Interesting ideas:
  support several graphics APIs; keep runtime registration explicit; drive input
  simulation with mouse and keyboard; present views in a normal desktop window.
- Interesting implementation choices:
  the repo makes runtime bring-up and lifecycle visible through
  `src/runtime.cpp`, UI support headers, and registration scripts such as
  `scripts/register-runtime.ps1`.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  still a simulator, not a real device-integration path.
- What to inspect next:
  compare its runtime shape with more automation-oriented simulators to see
  what should belong in a future `QA runtime`.

## `shieldmeidunn/SteamVRNullFlipper`

- GitHub:
  [shieldmeidunn/SteamVRNullFlipper](https://github.com/shieldmeidunn/SteamVRNullFlipper)
- What it is:
  a tiny utility that flips SteamVR into and out of a null-driver configuration
  with backup-aware config handling.
- Why it matters:
  it is a strong micro-donor for `config-swap helper` construction.
- Interesting ideas:
  do one thing only; keep a reversible settings change; treat null-driver mode
  as a repeatable development state instead of a one-time manual hack.
- Interesting implementation choices:
  `NullDriverFlipper.bat` is small, but it makes backup, swap, and restore
  behavior explicit enough to study.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  tiny and intentionally narrow.
- What to inspect next:
  compare it with broader config patchers such as `steamvr-exconfig` to isolate
  the minimum useful `mode flipper` pattern.

## `OpenDisplayXR/OpenDisplayXR-VDD`

- GitHub:
  [OpenDisplayXR/OpenDisplayXR-VDD](https://github.com/OpenDisplayXR/OpenDisplayXR-VDD)
- What it is:
  a strategically interesting but currently source-light virtual hardware path.
- Why it matters:
  it keeps the `simulated OpenVR/OpenXR hardware` idea visible even though the
  current public repo is thin.
- Interesting ideas:
  connect virtual-display and fake-hardware thinking; treat the display path as
  part of XR simulation, not only tracking or input.
- Interesting implementation choices:
  the current public snapshot is too sparse to support a stronger donor claim.
- Code donor value:
  low-medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  still source-light and under-documented.
- What to inspect next:
  revisit only if the visible source or docs grow enough to compare it fairly
  with `virtual_display`, `Virtual-Display-Driver`, and richer simulator repos.

## `chnoblouch/aethervr`

- GitHub:
  [chnoblouch/aethervr](https://github.com/chnoblouch/aethervr)
- What it is:
  a headsetless custom OpenXR runtime paired with a Python tracker process.
- Why it matters:
  it is the strongest donor in the repo for
  `camera-driven custom runtime with a separate tracker process`.
- Interesting ideas:
  split runtime and tracker responsibilities; use a local protocol boundary;
  treat webcam-driven QA and fake hardware as a full runtime experiment, not
  only a controller emulator.
- Interesting implementation choices:
  the repo exposes a clear split between the runtime tree and tracker-side code
  such as `tracker/runtime_connection.py` and other runtime registration and
  configuration helpers.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  ambitious prototype quality and custom runtime complexity are real.
- What to inspect next:
  compare it with `OpenXR-Simulator` and `ox-sim-driver` to separate
  `camera runtime`, `desktop simulator`, and `automation simulator` patterns.

## `ox-runtime/ox-sim-driver`

- GitHub:
  [ox-runtime/ox-sim-driver](https://github.com/ox-runtime/ox-sim-driver)
- What it is:
  a simulator stack for the `ox` OpenXR ecosystem with both GUI and
  programmatic control surfaces.
- Why it matters:
  it is the strongest donor surfaced in this pass for
  `automation-friendly simulator runtime`.
- Interesting ideas:
  expose a high-level C API; keep GUI and automation clients on the same core;
  support profile switching, device metadata, and typed input control.
- Interesting implementation choices:
  `include/ox_sim.h`, `src/driver.cpp`, `src/ox_sim.cpp`,
  `src/gui/gui_window.cpp`, and the example C++ or Python clients show a very
  deliberate `core simulator API + optional controllers` architecture.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  tied to the `ox` stack, so some product assumptions are ecosystem-specific.
- What to inspect next:
  compare it with other runtime simulators when designing a future
  `scriptable XR QA sandbox`.

## Main takeaways from Wave 25

- `Headsetless development` is now clearer as several distinct methods, not one
  generic trick.
- The strongest split inside the family is:
  - `manual null-driver recipe`
  - `config swap micro-tool`
  - `virtual HMD driver`
  - `desktop simulator runtime`
  - `camera-driven custom runtime`
  - `automation-friendly simulator platform`
- Tiny utilities still matter when they reduce friction around a recurring mode
  switch, as seen in `SteamVRNullFlipper`.

## Reusable methods clarified by this wave

- `Null-driver config swapper with backup-safe mode toggling`
- `Automation-friendly simulator runtime with shared core plus GUI or API controllers`
- `Virtual HMD driver for no-headset development and testing`

## Recommended next moves after this wave

1. Treat `headsetless QA` as a real architecture track across SteamVR and
   OpenXR, not just a setup footnote.
2. Use `VirtualSteamVRDriver` when the right abstraction is a fake OpenVR
   device.
3. Use `OpenXR-Simulator` when the right abstraction is a desktop runtime.
4. Use `ox-sim-driver` when automation, scripting, or external test control is
   a core requirement.
5. Keep `aethervr` visible as the strongest `camera runtime` comparison node in
   this family.
