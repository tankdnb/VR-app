# VR Projects Wave 4: Gap Fill From Utility List

- Date: `2026-04-10`
- Goal: close the gaps from an additional user-provided list of VR utility
  repositories by separating:
  - projects already covered in `VR.app`
  - projects newly added in this pass
  - the strongest new ideas that emerge from them

## Coverage status for the submitted list

The following projects were already covered in earlier `VR.app` research docs,
primarily in:

- `vr-projects-wave-3-utilities.md`
- `vr-projects-master-index.md`

Already covered:

1. `fredemmott/OpenXR-API-Layers-GUI`
2. `WaGi-Coding/OpenXR-Runtime-Switcher`
3. `UniStuttgart-VISUS/OpenXR-Runtime-Switcher`
4. `Jabbah/OpenXR-Layer-OBSMirror`
5. `CircuitLord/DesktopPortal`
6. `scudzey/UVROverlay`
7. `galister/WlxOverlay`
8. `matrixfurry/wlx-overlay-s`
9. `galister/wlx-overlay-x`
10. `Vinventive/live-captions-vr`
11. `BOLL7708/OpenVROverlayPipe`
12. `jeppevinkel/OpenVRNotificationPipe`
13. `BOLL7708/OpenVR2WS`
14. `Otter-Co/TurnSignal`
15. `pottedmeat7/OpenVR-WalkInPlace`
16. `naelstrof/VRPlayspaceMover`
17. `kurotu/OVR-Lighthouse-Manager`
18. `xi-ve/openvr-lighthouse-manager-linux`
19. `PhialsBasement/fnuidesktop-VR`
20. `Danealor/VRPassthrough`
21. `jangxx/LeapOVRPassthrough`
22. `Raphiiko/OyasumiVR`
23. `mdovgialo/steam-vr-wheel`
24. `Deryck2000/SteamVR_ClockOverlay_Public`

Newly added in this pass:

1. `ytdlder/OpenXR-Switcher`
2. `jonyrh/OXR_Switcher`
3. `rhaamo/OpenVR-Display-Devices`
4. `SeeUnsharp/LighthouseManager`
5. `seader/LighthouseManagerPimax`
6. `Marshall-vak/OpenVR-SpaceCalibrator2`

## Newly documented projects

### 1. `ytdlder/OpenXR-Switcher`

- What it is:
  Windows utility for switching OpenXR runtimes and toggling installed OpenXR
  API layers.
- Why it matters:
  this is stronger than a plain runtime switcher because it combines `runtime`
  and `layer` management in one tool.
- Interesting ideas:
  registry scan for installed runtimes and layers, stale JSON detection, quick
  layer enable/disable, custom rename support, CLI and GUI modes in one small
  app.
- Best reuse value:
  direct feature inspiration for a future `VR.app OpenXR Doctor`, especially the
  idea that runtime switching and layer toggling should live together.
- Caveat:
  requires admin rights and is `GPL-3.0`.
- Sources:
  [repo](https://github.com/ytdlder/OpenXR-Switcher)

### 2. `jonyrh/OXR_Switcher`

- What it is:
  GUI utility for switching active OpenXR runtime, with x32/x64 support and CLI.
- Why it matters:
  adds another useful UX reference for `runtime management` and explicitly
  handles multiple architecture views.
- Interesting ideas:
  architecture-aware runtime list, CLI plus GUI packaging, icon-based runtime
  recognition for a wide set of ecosystems including SteamVR, WMR, Vive, Varjo,
  Pimax, Virtual Desktop, and Monado.
- Best reuse value:
  good UX reference for making runtime tools legible to non-technical users.
- Caveat:
  small project and focused only on switching, not diagnostics.
- Sources:
  [repo](https://github.com/jonyrh/OXR_Switcher)

### 3. `rhaamo/OpenVR-Display-Devices`

- What it is:
  standalone window plus SteamVR overlay that lists connected OpenVR devices.
- Why it matters:
  one of the clearest references for a `device inventory overlay`.
- Interesting ideas:
  model/vendor/tracking-type display, serial number view, battery status,
  tracking state, low-battery notifications, charge-state notifications, support
  for both standalone desktop view and in-VR overlay.
- Best reuse value:
  direct inspiration for a `VR.app Device Monitor` and battery/tracking health
  overlay.
- Caveat:
  OpenVR-specific and partly geared toward power users.
- Sources:
  [repo](https://github.com/rhaamo/OpenVR-Display-Devices)

### 4. `SeeUnsharp/LighthouseManager`

- What it is:
  command-line tool to discover and manage SteamVR Lighthouse base stations, plus
  a worker service for automation.
- Why it matters:
  a strong minimal reference for `device management + background service`
  architecture.
- Interesting ideas:
  CLI discover/power workflow, worker service that watches `vrserver.exe`,
  configurable poll interval, Windows Service installation path, `appsettings`
  driven configuration.
- Best reuse value:
  future `VR.app` service-mode device management and auto-start automation.
- Caveat:
  command-line first and tightly scoped to base stations.
- Sources:
  [repo](https://github.com/SeeUnsharp/LighthouseManager)

### 5. `seader/LighthouseManagerPimax`

- What it is:
  Pimax-oriented variant of Lighthouse manager with service support.
- Why it matters:
  useful proof that `device management logic often needs runtime/vendor-specific
  process watchers`.
- Interesting ideas:
  monitoring `pi_server.exe` instead of generic SteamVR server, service-based
  automation, MSI installer packaging, `.NET 8`-based utility/service split.
- Best reuse value:
  reminder that `VR.app` device services should support pluggable runtime
  watchers rather than hardcoding only SteamVR.
- Caveat:
  narrower audience and vendor-specific focus.
- Sources:
  [repo](https://github.com/seader/LighthouseManagerPimax)

### 6. `Marshall-vak/OpenVR-SpaceCalibrator2`

- What it is:
  alternative Space Calibrator branch with support for continuous calibration.
- Why it matters:
  this is one of the most important additions in this gap-fill pass, because it
  extends calibration from one-off setup into an always-on mode.
- Interesting ideas:
  continuous calibration using a tracker mounted on the headset, playspace sync
  that keeps updating during use, explicit flow for switching from regular to
  continuous calibration.
- Best reuse value:
  strong product direction for `VR.app calibration helpers`, especially for
  mixed-tracking or long-session drift correction tools.
- Caveat:
  requires a tracker on the headset and remains a specialist tool.
- Sources:
  [repo](https://github.com/Marshall-vak/OpenVR-SpaceCalibrator2)

## Strongest new ideas from this gap-fill pass

### 1. Runtime switching and layer toggling belong in one product

The combination of:

- `OpenXR-API-Layers-GUI`
- `WaGi-Coding/OpenXR-Runtime-Switcher`
- `ytdlder/OpenXR-Switcher`
- `jonyrh/OXR_Switcher`

suggests that the best future `OpenXR Doctor` is not just a diagnostic screen,
but a unified tool that can:

- detect runtimes
- switch runtimes
- inspect layers
- toggle layers
- flag stale/broken manifest paths

### 2. Device inventory is its own valuable overlay class

`OpenVR-Display-Devices` shows that users benefit from a dedicated overlay that
answers:

- what devices are connected
- what their battery state is
- whether they are charging
- whether tracking is good
- what vendor/model each device really is

This strengthens the case for a `VR.app Device Monitor`.

### 3. Service-backed automation is a recurring pattern

`LighthouseManager` and `LighthouseManagerPimax` both point to the same useful
pattern:

- small CLI core
- background watcher/service
- runtime-process-aware automation

That pattern is reusable beyond base stations.

### 4. Continuous calibration is a much stronger story than one-shot setup

`OpenVR-SpaceCalibrator2` adds an important idea:

- calibration should not always be a one-time wizard
- there is real value in ongoing alignment maintenance during use

That makes calibration helpers more compelling as an ongoing utility family.

## Recommended updates to the VR.app backlog

These additions reinforce four especially strong directions:

1. `OpenXR Doctor`
   Add runtime switching, layer toggling, stale-manifest detection, x86/x64
   awareness.

2. `Device Monitor Overlay`
   Device inventory, battery, charge state, tracking state, notifications.

3. `Device Automation Service`
   Background watchers for base stations and other VR hardware.

4. `Calibration Tools`
   Include both one-shot calibration and continuous-calibration concepts.

## Bottom line

This pass did not just add more projects; it filled specific capability gaps:

- combined runtime + layer management
- device inventory overlays
- service-backed VR hardware automation
- continuous calibration

Those are all directly useful to `VR.app` and strengthen it as a platform for
practical VR tools.
