# VR Projects Wave 20: Performance Mods, Graphics Injection, and VR Sweet-Spot Shaders

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `performance mods`, `runtime-aware graphics injection`, and
  `VR sweet-spot shader bundles`.

## Why this wave exists

The repository already had strong coverage of:

- overlays, dashboards, and runtime diagnostics;
- OpenXR layers and runtime switchers;
- tracker bridges, device monitors, and driver-learning paths.

What still needed a more coherent pass was the family where:

- the utility boundary is a `proxy DLL` or `graphics hook`, not a visible app;
- performance and image quality are tuned through `config + shader chain`
  rather than a separate overlay shell;
- repos often share lineage, which makes `fork-quality assessment` part of the
  research value.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with rendering-mod and proxy-injection family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `RavenSystem/VRPerfKit_RSF` | Strong practical fork of the `vrperfkit` line with a visibly expanded config and compatibility surface |
| `CamelCaseName/OpenVRPerfKit` | Useful evolution branch that extends the same family into `D3D12` and bundled `FSR2` territory |
| `Granther/foveated-rendering` | Interesting public experiment around dynamic focus control rather than only static FFR |
| `retroluxfilm/reshade-vrtoolkit` | Cleanest VR-focused shader bundle in the wave |
| `zhukovv/upscale-injection` | Strong adjacent donor for low-level D3D11 proxy and hook mechanics |

## Secondary candidate surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `shieldmeidunn/SteamVRNullFlipper` | Useful headsetless testing signal, but more relevant as a future null-driver workflow follow-up than as a core rendering-mod donor |

## Deep-pass notes by project

## `RavenSystem/VRPerfKit_RSF`

- GitHub:
  [RavenSystem/VRPerfKit_RSF](https://github.com/RavenSystem/VRPerfKit_RSF)
- What it is:
  a practical continuation of the `vrperfkit` proxy-DLL line with more knobs
  around dynamic rendering behavior and compatibility.
- Why it matters:
  it is the clearest public donor in this wave for `runtime-aware DXGI proxy
  performance mod` design.
- Interesting ideas:
  keep `fixed` and `dynamic` rendering modes in the same config; chain the
  original `dxgi.dll` through `dxgi_ori.dll`; expose hidden radial mask control
  and target-FPS-oriented radius adaptation.
- Interesting implementation choices:
  the repo keeps explicit proxy entry points in `src/proxy/`; separates D3D11,
  OpenVR, and Oculus-related slices into dedicated trees; and exposes a broad
  `vrperfkit_RSF.yml` surface for hotkeys, dynamic FFR policy, radial mask
  behavior, and filter choice.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  still closely tied to a fork lineage and `D3D11` assumptions; the value is
  strongest as a donor, not as a new product direction by itself.
- What to inspect next:
  direct compare with `OpenVRPerfKit`, especially around backend growth and
  config compatibility.

## `CamelCaseName/OpenVRPerfKit`

- GitHub:
  [CamelCaseName/OpenVRPerfKit](https://github.com/CamelCaseName/OpenVRPerfKit)
- What it is:
  another extended `vrperfkit`-line repository that broadens backend coverage
  and bundles more modern upscaling pieces.
- Why it matters:
  it shows how the same proxy-mod family evolves when the goal becomes
  `more backends and more built-in scaling options`, not just more config
  toggles.
- Interesting ideas:
  keep the familiar drop-in proxy packaging while adding `D3D12` support and a
  bundled `ffx_fsr2` subtree; preserve a recognizable config surface so users
  can migrate from earlier `vrperfkit`-style tools.
- Interesting implementation choices:
  in addition to the expected proxy and D3D11 slices, the repo adds `src/d3d12`
  and packages `FSR2` dependencies directly; `OpenVRPerfKit.yml` keeps the
  family resemblance visible at the configuration layer.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  still a lineage fork rather than a clean greenfield design; family overlap is
  very high.
- What to inspect next:
  where the `D3D12` path meaningfully diverges from `VRPerfKit_RSF`, and which
  parts are true donor improvements instead of simply a broader packaging scope.

## `Granther/foveated-rendering`

- GitHub:
  [Granther/foveated-rendering](https://github.com/Granther/foveated-rendering)
- What it is:
  a public OpenXR-oriented foveated-rendering experiment that currently exposes
  more of a `dynamic focus-source prototype` than a finished eye-tracking tool.
- Why it matters:
  it shows an honest intermediate stage between static performance mods and a
  real eye-tracked path: `change the focus source first, then mature the rest`.
- Interesting ideas:
  use a cursor-driven focus estimate as a stand-in for future gaze data; keep
  the familiar proxy-mod lineage while exploring how dynamic focal control
  might work in practice.
- Interesting implementation choices:
  the repo contains a small Windows-side cursor app in `src/cursor/` that
  tracks and normalizes focus coordinates, while the rest of the source still
  resembles a `vrperfkit`-style D3D11 performance-mod path.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  the public repo is still closer to `cursor-simulated dynamic focus` than to a
  production-ready eye-tracking integration.
- What to inspect next:
  revisit only if the repo grows a true tracker ingestion path or clearer
  OpenXR gaze integration.

## `retroluxfilm/reshade-vrtoolkit`

- GitHub:
  [retroluxfilm/reshade-vrtoolkit](https://github.com/retroluxfilm/reshade-vrtoolkit)
- What it is:
  a VR-shaped ReShade shader pack that combines several useful visual treatments
  into one compact toolkit.
- Why it matters:
  it is the clearest public donor in this wave for a `single-pass VR sweet-spot
  shader bundle`.
- Interesting ideas:
  package sharpening, color correction, anti-aliasing, center-mask treatment,
  and related adjustments as one VR-first shader surface instead of a generic
  chain of unrelated game shaders.
- Interesting implementation choices:
  the main value is concentrated in `Shaders/VRToolkit.fx`, which keeps several
  image-treatment controls unified in one effect file and therefore teaches
  more about packaging and user-facing control surface than about runtime
  hooking.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  this is a shader-bundle donor, not a runtime-registration or driver-level
  utility.
- What to inspect next:
  whether a future reuse plan should extract the exact `VR sweet-spot shader`
  packaging pattern as a standalone reference for `VR-apps-lab`.

## `zhukovv/upscale-injection`

- GitHub:
  [zhukovv/upscale-injection](https://github.com/zhukovv/upscale-injection)
- What it is:
  a generic `D3D11` proxy-DLL upscaling injector rather than a VR-specific
  project.
- Why it matters:
  even though it is not VR-first, it is a strong donor for the lowest-level
  hook and forwarding mechanics that VR rendering mods often rely on.
- Interesting ideas:
  keep the repo centered on a minimal `drop-in d3d11.dll` story; separate the
  hook plumbing from the actual upscale shader path.
- Interesting implementation choices:
  the practical donor value lives in `d3d11_proxy_dll/`, especially
  `hooking.cpp`, which makes the hook and forward pattern much easier to study
  than in some of the more VR-specialized forks.
- Code donor value:
  medium-high.
- Product reference value:
  low-medium.
- Architecture reference value:
  medium-high.
- Caveats:
  generic graphics-hook donor only; it does not teach VR runtime semantics by
  itself.
- What to inspect next:
  compare its low-level hook structure with the more VR-shaped proxy repos to
  see which parts are general and which parts are VR-specific.

## Main takeaways from Wave 20

- `Graphics-path utility` is now clearly a separate family from overlays,
  runtime switchers, or OpenXR layers.
- The strongest split inside the family is:
  - `practical DXGI proxy performance mod`
  - `backend-expanded fork line`
  - `dynamic focus-source experiment`
  - `VR shader bundle`
  - `generic hook donor`
- Honest donor labeling matters because some repos are valuable mainly for
  `hook mechanics` or `shader packaging`, not for end-user product framing.

## Reusable methods clarified by this wave

- `Runtime-aware DXGI proxy performance mod`
- `Single-pass VR sweet-spot shader bundle`

## Recommended next moves after this wave

1. Keep `VRPerfKit_RSF` and `OpenVRPerfKit` as the strongest donor pair in the
   rendering-mod family.
2. Treat `foveated-rendering` as an honest experimental branch, not as a mature
   eye-tracking reference.
3. Keep `reshade-vrtoolkit` visible as a product and UX donor even though it
   sits at the shader-pack level.
4. Reuse `upscale-injection` mainly for low-level hook study, not for VR
   product direction.
