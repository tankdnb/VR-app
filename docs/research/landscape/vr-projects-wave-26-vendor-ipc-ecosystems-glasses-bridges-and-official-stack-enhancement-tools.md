# VR Projects Wave 26: Vendor IPC Ecosystems, Glasses Bridges, and Official-Stack Enhancement Tools

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `vendor IPC ecosystems`, `glasses bridges`, and
  `official-stack enhancement tools`.

## Why this wave exists

The repository already knew that `PSVR2Toolkit` mattered, but it still lacked a
full ecosystem picture:

- the IPC consumers were not cataloged cleanly;
- the repo still treated vendor enhancement too much like one toolkit bullet;
- glasses bridges were present, but their architectural differences were still
  blurry;
- downstream micro-tools were not yet integrated as reusable patterns.

This wave exists to turn `vendor enhancement and glasses bridge ecosystems`
into a clearer architecture track inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with PSVR2 enhancement, toolkit consumer, and glasses-bridge
   family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `BnuuySolutions/PSVR2Toolkit` | Strongest vendor-wrapper and local-IPC ecosystem donor in the current repo |
| `BnuuySolutions/PSVR2Toolkit.VRCFT` | Clear downstream consumer of that IPC surface |
| `s-ilent/PSVR2ToolkitTriggerConfig` | Focused config micro-tool over the same IPC contract |
| `tabithamoon/ResonitePSVR2` | Engine-specific feature bridge built on the toolkit IPC layer |
| `verncat/RayNeo-Air-3S-Pro-OpenVR` | SDK-first glasses bridge with public API surface |
| `verncat/RayNeo-Air-3S-Pro-OpenVR-Driver` | Dedicated driver continuation of that same glasses path |
| `DaniXmir/GlassVr` | Strong sidecar-plus-emulation bridge for XR/AR glasses and related role emulation |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `BnuuySolutions/PSVR2Toolkit-Lite` | Deprecated earlier line that is mainly useful as a historical variant |
| `tobexeon/PSVR2EyeTrackingCalibration` | Interesting calibration node, but tied to a custom PSVR2Toolkit fork rather than the main upstream |

## Deep-pass notes by project

## `BnuuySolutions/PSVR2Toolkit`

- GitHub:
  [BnuuySolutions/PSVR2Toolkit](https://github.com/BnuuySolutions/PSVR2Toolkit)
- What it is:
  a vendor-driver wrapper that augments the official PSVR2 stack and exposes a
  local developer-facing IPC layer.
- Why it matters:
  it is still the strongest donor in the repo for
  `vendor wrapper + proxy hooks + local IPC`.
- Interesting ideas:
  keep the official stack intact; hook selected driver surfaces; expose gaze and
  trigger functionality through a reusable IPC contract; treat enhancement as an
  ecosystem, not a monolith.
- Interesting implementation choices:
  `include/psvr2_toolkit_capi.h` exposes a public C API, the
  `PSVR2Toolkit.IPC` project defines the consumer contract, and the
  `psvr2_openvr_driver_ex` tree makes proxy, hook, loader, gaze, and
  trigger-management boundaries very explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  vendor updates and hook fragility are real constraints.
- What to inspect next:
  compare it with future vendor-specific OpenXR eye-tracking projects to see
  where `driver wrapper` should end and `OpenXR layer` should begin.

## `BnuuySolutions/PSVR2Toolkit.VRCFT`

- GitHub:
  [BnuuySolutions/PSVR2Toolkit.VRCFT](https://github.com/BnuuySolutions/PSVR2Toolkit.VRCFT)
- What it is:
  a VRCFaceTracking module built on top of the PSVR2Toolkit IPC contract.
- Why it matters:
  it is the clearest donor in the repo for
  `consumer-specific module over vendor IPC`.
- Interesting ideas:
  keep the toolkit generic and put consumer-specific mapping logic in a smaller
  downstream repo; smooth raw data before passing it to the host ecosystem.
- Interesting implementation choices:
  `IpcClient.cs`, `IpcProtocol.cs`, `Psvr2TrackingModule.cs`, and
  `LowPassFilter.cs` show a focused `consume toolkit -> adapt to target host`
  architecture.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  useful mainly as an ecosystem node, not as a standalone product direction.
- What to inspect next:
  compare it with other downstream consumers to decide what a reusable vendor
  SDK or IPC package should guarantee.

## `s-ilent/PSVR2ToolkitTriggerConfig`

- GitHub:
  [s-ilent/PSVR2ToolkitTriggerConfig](https://github.com/s-ilent/PSVR2ToolkitTriggerConfig)
- What it is:
  a focused trigger-configuration utility built on PSVR2Toolkit's IPC surface.
- Why it matters:
  it is the strongest donor in the repo for
  `config micro-tool over vendor IPC`.
- Interesting ideas:
  do one highly specific thing well; expose live parameter tweaking; persist
  presets to JSON instead of folding everything into the main toolkit.
- Interesting implementation choices:
  `IpcClient.cs`, `IpcProtocol.cs`, and `MainWindow.xaml.cs` make the
  `focused desktop config tool over toolkit IPC` pattern easy to study.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  very narrow scope, but that narrowness is part of its reuse value.
- What to inspect next:
  compare it with more general control surfaces when deciding whether a future
  vendor utility should stay tiny or fold into a larger shell.

## `tabithamoon/ResonitePSVR2`

- GitHub:
  [tabithamoon/ResonitePSVR2](https://github.com/tabithamoon/ResonitePSVR2)
- What it is:
  a Resonite mod that consumes PSVR2Toolkit data for eye tracking and related
  expression signals.
- Why it matters:
  it is a strong donor for `engine-specific feature bridge over vendor IPC`.
- Interesting ideas:
  keep the toolkit general; map the vendor-specific signal into the semantics of
  a specific target app or engine; expose only the host-relevant slice.
- Interesting implementation choices:
  `Drivers/EyeTrackingDriver.cs`, `ToolkitInterop/IpcClient.cs`,
  `ToolkitInterop/IpcProtocol.cs`, and `ResonitePSVR2Config.cs` show a focused
  mod-side integration boundary.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  target-engine specificity limits direct reuse.
- What to inspect next:
  use it mainly as an ecosystem reference for downstream consumer design, not
  as a generic utility donor.

## `verncat/RayNeo-Air-3S-Pro-OpenVR`

- GitHub:
  [verncat/RayNeo-Air-3S-Pro-OpenVR](https://github.com/verncat/RayNeo-Air-3S-Pro-OpenVR)
- What it is:
  an SDK-first bridge for RayNeo glasses that still includes an older OpenVR
  driver snapshot.
- Why it matters:
  it is the clearest donor in the repo for
  `SDK-first device bridge with optional or separated driver repo`.
- Interesting ideas:
  expose a public C API first; let the transport, IMU, and EDID surfaces live
  in an SDK layer; separate the dedicated driver when the hardware path grows.
- Interesting implementation choices:
  the repo exposes `include/rayneo_api.h`, `src/RayneoApi.cpp`, and an older
  `openvr_driver` tree, which makes the `SDK first, driver second` split very
  visible.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the old driver slice is no longer the whole story.
- What to inspect next:
  compare it with the separate driver repo to isolate what belongs in a public
  device SDK versus a runtime-specific bridge.

## `verncat/RayNeo-Air-3S-Pro-OpenVR-Driver`

- GitHub:
  [verncat/RayNeo-Air-3S-Pro-OpenVR-Driver](https://github.com/verncat/RayNeo-Air-3S-Pro-OpenVR-Driver)
- What it is:
  the dedicated OpenVR driver repo for the newer RayNeo glasses path.
- Why it matters:
  it completes the earlier RayNeo SDK note by giving the bridge a proper
  driver-side home.
- Interesting ideas:
  split driver evolution into a separate repo; expose input components and
  bindings; pair the driver with a small prelauncher helper.
- Interesting implementation choices:
  `src/device_provider.cpp`, `src/hmd_device_driver.cpp`,
  `resources/input/rayneo_hmd_profile.json`, and
  `src/tools/rayneo_prelauncher.cpp` make the driver surface much clearer than
  the older embedded stub.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  still tied to one device family.
- What to inspect next:
  compare it with other glasses bridges and repurposed-output drivers to see
  how much of the pattern generalizes.

## `DaniXmir/GlassVr`

- GitHub:
  [DaniXmir/GlassVr](https://github.com/DaniXmir/GlassVr)
- What it is:
  a sidecar-driven XR/AR glasses bridge that can emulate several SteamVR roles,
  including controllers and trackers.
- Why it matters:
  it is the strongest donor in the repo for
  `Python sidecar + multi-role emulation driver`.
- Interesting ideas:
  bridge glasses hardware into SteamVR; emulate headset, controller, and
  tracker roles; mix hand-tracking and offset logic into one sidecar-managed
  stack.
- Interesting implementation choices:
  `code-glassvrserver/main.py`, the shipped `glassvrdriver` assets, and the
  `HmdVr/samples/driver_sample` tree with `viture.cpp`, `hand_simulation.cpp`,
  and tracker-related sample code make the `server + emulation driver` split
  concrete.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broad emulation scope increases complexity and makes maintenance harder.
- What to inspect next:
  compare it with `RayNeo` to separate `SDK-first bridge` and
  `sidecar-driven emulation bridge` patterns.

## Main takeaways from Wave 26

- `Vendor enhancement` is now clearer as an ecosystem problem, not one repo.
- The strongest split inside the family is:
  - `vendor wrapper with local IPC`
  - `consumer-specific module over vendor IPC`
  - `focused config micro-tool over vendor IPC`
  - `SDK-first glasses bridge`
  - `sidecar-driven multi-role emulation bridge`
- Small downstream repos matter because they make the ecosystem boundary
  visible, not because they are standalone products.

## Reusable methods clarified by this wave

- `Vendor enhancement ecosystem built around local IPC and downstream consumers`
- `Consumer-specific module over vendor IPC`
- `Config micro-tool over vendor IPC`

## Recommended next moves after this wave

1. Treat `PSVR2Toolkit` as a full ecosystem donor, not just a single
   repository.
2. Use `PSVR2Toolkit.VRCFT`, `ResonitePSVR2`, and `PSVR2ToolkitTriggerConfig`
   as downstream-consumer references when designing any future local IPC or SDK
   surface.
3. Use `RayNeo-Air-3S-Pro-OpenVR` and its dedicated driver repo as the main
   `SDK-first bridge` comparison line.
4. Keep `GlassVr` visible as the strongest current
   `sidecar-driven device-emulation bridge` in the glasses family.
