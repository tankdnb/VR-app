# VR Projects Wave 21: OpenXR Provider Stacks, Gaze Layers, and Runtime-Side Utility Platforms

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `OpenXR provider stacks`, `gaze API layers`, and
  `runtime-side utility platforms`.

## Why this wave exists

The repository already had strong coverage of:

- OpenXR runtime switchers, registries, and diagnostics tools;
- template-level API layers;
- runtime compatibility adapters and graphics interop helpers.

What still needed a more precise pass was the family where:

- a repo packages raw OpenXR bring-up as a `reusable provider stack`;
- an API layer adapts `foreign gaze or rendering expectations` into an OpenXR
  surface the app can consume;
- a broader utility platform is still worth tracking, but only through the
  specific layer, manifest, or plugin surfaces that are genuinely reusable.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with OpenXR provider and gaze-layer family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, overlap, and donor value;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `1runeberg/OpenXRProvider` | Clear library-plus-sandbox OpenXR bring-up stack |
| `mbucchia/Quad-Views-Foveated` | Strong rendering-adaptation API layer that exposes advanced OpenXR extension emulation |
| `mbucchia/OpenXR-Eye-Trackers` | Strongest multi-backend eye-gaze adaptation layer in the current repo |
| `clear-xr/clearxr-server` | Larger runtime-side platform whose layer/service split matters more than the whole product shell |
| `vrkit-platform/vrkit-platform` | Useful but scope-drifted platform signal with plugin-manifest and overlay configuration surfaces |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `BattleAxeVR/PSVR2_OpenXR_Eye_Tracking` | Relevant gaze-layer signal, but not needed once `OpenXR-Eye-Trackers` already covered the stronger multi-backend family representative |
| `LordOfDragons/openxr_oscclient` | Interesting OSC-to-OpenXR angle, but still better treated as a later comparison node than as a core donor in this pass |

## Deep-pass notes by project

## `1runeberg/OpenXRProvider`

- GitHub:
  [1runeberg/OpenXRProvider](https://github.com/1runeberg/OpenXRProvider)
- What it is:
  a reusable OpenXR wrapper library paired with a sandbox application.
- Why it matters:
  it is one of the clearest public references for `library plus sandbox
  learning harness` applied specifically to OpenXR bring-up.
- Interesting ideas:
  split the wrapper into core, render, and input layers; keep a runnable sample
  so abstraction does not hide runtime reality; organize input profiles by
  device family rather than keeping one monolithic input block.
- Interesting implementation choices:
  `OpenXRProvider.cpp` wires together `XRCore`, `XRRender`, and `XRInput`;
  the include tree splits input profiles into dedicated device-focused files;
  the sandbox app serves as a concrete proof that the wrapper stays practical.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  this is more of a bring-up and learning scaffold than a user-facing utility
  product.
- What to inspect next:
  extension-wrapper boundaries and how much of the render/input split remains
  reusable under more advanced OpenXR feature work.

## `mbucchia/Quad-Views-Foveated`

- GitHub:
  [mbucchia/Quad-Views-Foveated](https://github.com/mbucchia/Quad-Views-Foveated)
- What it is:
  an OpenXR API layer that adapts `quad views` and foveated-rendering behavior
  onto runtimes and applications that would not normally expose them together.
- Why it matters:
  it is the strongest current donor in the repo for `rendering adaptation API
  layer` design.
- Interesting ideas:
  advertise advanced extensions to the app while suppressing them from the
  underlying runtime; request eye-tracking surfaces implicitly when needed;
  apply per-runtime or per-game quirks through configuration rather than hard
  one-off branches only.
- Interesting implementation choices:
  `layer.cpp` explicitly advertises `XR_VARJO_quad_views` and related features,
  blocks the same extensions from the underlying runtime, loads config, and
  applies compatibility logic; the layer is very explicit about its
  `runtime-facing adaptation` role.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  current support is still bounded by `D3D11` and a specialized rendering
  domain.
- What to inspect next:
  how much of the compatibility and config logic could generalize into a future
  `advanced OpenXR doctor or layer toolkit`.

## `mbucchia/OpenXR-Eye-Trackers`

- GitHub:
  [mbucchia/OpenXR-Eye-Trackers](https://github.com/mbucchia/OpenXR-Eye-Trackers)
- What it is:
  an OpenXR API layer that adapts multiple foreign eye-tracking sources into a
  runtime-facing gaze surface.
- Why it matters:
  it is the clearest `multi-backend eye-tracker aggregator API layer` donor in
  the repository.
- Interesting ideas:
  support several hardware and transport backends under one layer; treat
  `VRChat OSC`, `Virtual Desktop`, `Steam Link`, `PSVR2Toolkit`, and simulated
  sources as interchangeable gaze providers behind one runtime-facing
  extension.
- Interesting implementation choices:
  the backend fan-in is explicit in files such as `omnicept.cpp`, `pimax.cpp`,
  `psvr2_toolkit.cpp`, `quest_pro.cpp`, `steam_link.cpp`,
  `virtual_desktop.cpp`, `vrchat_osc.cpp`, and `simulated.cpp`; the layer then
  normalizes those inputs into an OpenXR gaze surface.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  highly extension-specific; practical value depends on the stability of the
  foreign backends it consumes.
- What to inspect next:
  compare its backend adapters directly, especially `VRChat OSC` versus
  vendor-toolkit ingestion, to see which pattern generalizes best.

## `clear-xr/clearxr-server`

- GitHub:
  [clear-xr/clearxr-server](https://github.com/clear-xr/clearxr-server)
- What it is:
  a larger runtime-side platform whose public repo combines a desktop shell,
  an OpenXR app, and an OpenXR API layer.
- Why it matters:
  even though the overall scope is broad, the repo is still valuable as a
  `layer plus service-host split` reference.
- Interesting ideas:
  keep `clearxr-streamer`, `clearxr-space`, and `clearxr-layer` as separate
  responsibilities; pair session management and device orchestration with a
  smaller API-layer component that fixes or adapts runtime behavior.
- Interesting implementation choices:
  `clear-xr-layer.json` defines a dedicated layer manifest;
  `clearxr-layer/src/lib.rs` intercepts OpenXR action-state queries and injects
  controller touch/click behavior from an external channel; the overall repo
  makes the `platform shell vs layer slice` boundary visible.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the repo is too broad to promote wholesale as one clean donor; the research
  value is strongest when the scope stays tightly bounded to the layer and
  service ownership model.
- What to inspect next:
  registration flow, process ownership, and the exact boundary between
  controller-fix logic and the wider streaming or utility platform.

## `vrkit-platform/vrkit-platform`

- GitHub:
  [vrkit-platform/vrkit-platform](https://github.com/vrkit-platform/vrkit-platform)
- What it is:
  a platform repo whose current public snapshot exposes interesting plugin and
  overlay surfaces, but no longer reads like a clean general-purpose OpenXR
  utility platform.
- Why it matters:
  it is still a useful signal for `plugin-manifest and overlay-config platform
  design`, but it has to be labeled honestly.
- Interesting ideas:
  keep plugin metadata explicit; use a manifest-driven plugin system; define
  overlay configuration through a schema rather than only through app code.
- Interesting implementation choices:
  the strongest visible artifacts are
  `docs/Design/PluginSystem/PluginManifestExample.plugin-manifest.json` and
  `etc/schema/models/OverlayConfig.json`, which teach more than the repo's
  current top-level framing.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  current public scope has drifted; it should remain `Not studied deeply` until
  a narrower pass confirms a cleaner OpenXR utility core.
- What to inspect next:
  whether the public snapshot grows a clearer layer/runtime boundary or a
  plugin-host architecture that is less domain-specific.

## Main takeaways from Wave 21

- `Provider stack`, `sensor adaptation layer`, and `runtime-side host platform`
  are now separate sub-patterns instead of one vague OpenXR bucket.
- The strongest split inside the family is:
  - `wrapper plus sandbox OpenXR bring-up`
  - `rendering adaptation API layer`
  - `multi-backend gaze adaptation API layer`
  - `broad service host with a valuable layer slice`
  - `scope-drifted platform signal`
- Honest scope control matters: some repos are strong donors only when one
  narrow subsystem is isolated from the rest.

## Reusable methods clarified by this wave

- `Multi-backend eye-tracker aggregator API layer`
- sharper references for `library plus sandbox learning harness`
- sharper references for `protocol-adapter OpenXR layer for foreign sensor data`

## Recommended next moves after this wave

1. Promote `OpenXRProvider`, `Quad-Views-Foveated`, and `OpenXR-Eye-Trackers`
   as the strongest donors in this family.
2. Keep `clearxr-server` partially open because the layer/service split is more
   valuable than the whole platform shell.
3. Keep `vrkit-platform` visible but explicitly caution that the current public
   snapshot is scope-shifted.
4. Use future follow-up waves to compare gaze-layer backends and smaller
   OpenXR-side OSC experiments if that branch expands.
