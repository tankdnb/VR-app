# VR Projects Wave 77: OpenXR Helper Stacks, Layer Toolchains, and Runtime Adaptation Helpers

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `OpenXR helper stacks`, `layer toolchains`, and
  `runtime adaptation helpers`.

## Why this wave exists

`VR-apps-lab` already had strong coverage of OpenXR bindings, sample apps, and
runtime platforms, but it still lacked a clearer answer to:

`what the best medium-small helper repos look like when they are not full platforms and not only sample apps`.

This wave exists to make that family clearer:

- authoring frameworks for OpenXR API layers;
- tiny graphics-facing wrappers over OpenXR boilerplate;
- registry-backed layer hygiene micro-tools;
- runtime-side adaptation layers that are more productized than a template.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with helper-stack, toolchain, and runtime-adaptation queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `technobaboo/quark` | Strong donor for macro-generated OpenXR API-layer authoring |
| `doraibu/rayxr` | Strong donor for a tiny C wrapper that turns OpenXR boilerplate into a graphics-facing facade |
| `fredemmott/openxr-layer-scripts` | Strong donor for Windows-specific layer inspection and reorder tooling |
| `elliotttate/OpenXR-CAS` | Strong donor for a mature post-process API layer with config and live reload |

## Deep-pass notes by project

## `technobaboo/quark`

- GitHub:
  [technobaboo/quark](https://github.com/technobaboo/quark)
- What it is:
  a Rust framework for authoring OpenXR API layers with macros, typed handle
  registries, and helper traits.
- Why it matters:
  it is the clearest donor in this wave for
  `OpenXR API-layer authoring framework with typed per-handle data`.
- Interesting ideas:
  let a macro generate the sensitive loader plumbing; keep layer authors in
  normal Rust function land; attach typed data to raw handles through a
  registry instead of scattering unsafe global maps.
- Interesting implementation choices:
  `src/lib.rs`
  reexports the macro surface and `openxr` fork while
  `src/handle.rs`
  implements typed handle data registries; the `api_layer_test` sample shows
  how action-set hooks can be written on top of the framework without hand
  reimplementing all loader glue.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  it is framework-oriented rather than user-facing, but that is exactly why it
  matters here.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `Rust OpenXR layer-authoring baseline`
  donor.

## `doraibu/rayxr`

- GitHub:
  [doraibu/rayxr](https://github.com/doraibu/rayxr)
- What it is:
  a minimal C wrapper that integrates OpenXR with raylib by hiding the
  repetitive boilerplate behind a very small graphics-facing surface.
- Why it matters:
  it is the clearest donor in this wave for
  `tiny graphics-facing OpenXR facade`.
- Interesting ideas:
  wrap only the boilerplate that repeatedly gets in the way; expose raw
  `instance`, `session`, and eye-frame flow while refusing to become a giant
  framework; keep the public API small enough to understand in one header.
- Interesting implementation choices:
  `include/rayxr/rayxr.h`
  makes the public surface obvious while
  `src/rayxr_core.c`
  and `src/rayxr_session.c`
  own instance, session, space, swapchain, and event handling on behalf of the
  app.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  Linux and GLX focused, but useful precisely because it keeps the wrapper
  boundary narrow.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `small graphics-engine OpenXR helper`
  donor.

## `fredemmott/openxr-layer-scripts`

- GitHub:
  [fredemmott/openxr-layer-scripts](https://github.com/fredemmott/openxr-layer-scripts)
- What it is:
  a pair of Windows PowerShell scripts for listing, enabling, disabling, and
  reordering installed OpenXR layers.
- Why it matters:
  it is the clearest donor in this wave for
  `registry-backed layer hygiene micro-tool`.
- Interesting ideas:
  treat layer state as an operator surface; inspect both user and machine
  registry locations; expose ordering and enablement as direct commands instead
  of burying them in another GUI.
- Interesting implementation choices:
  `list-openxr-layers.ps1`
  enumerates and reports layer manifests while
  `edit-openxr-layers.ps1`
  supports `Enable`, `Disable`, `Remove`, `First`, `Last`, `Before`, and
  `After` operations over the registry-backed layer list.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  Windows-only and intentionally tiny, but unusually useful as an operator
  workflow donor.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs
  `OpenXR layer hygiene`
  utilities.

## `elliotttate/OpenXR-CAS`

- GitHub:
  [elliotttate/OpenXR-CAS](https://github.com/elliotttate/OpenXR-CAS)
- What it is:
  a D3D11 OpenXR layer that applies CAS sharpening and optional image
  adjustments at frame-end with config files, overrides, and live reload.
- Why it matters:
  it is the clearest donor in this wave for
  `runtime adaptation layer with mature config and live reload`.
- Interesting ideas:
  treat image processing as an OpenXR layer concern instead of an engine patch;
  support multiple config sources with a clear precedence order; allow live
  reload and optional stages rather than one hard-coded shader pass.
- Interesting implementation choices:
  `openxr-api-layer/layer.cpp`
  owns D3D11 device state, texture pools, config resolution, optional
  post-processing stages, and frame-end intervention around the layer's hook
  path.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  graphics-backend specific, but exactly the kind of mature narrow layer that
  expands the repo's understanding of `runtime adaptation utility`.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `post-process API layer`
  donor.

## Main takeaways from Wave 77

- `OpenXR helper repos` now split more cleanly into:
  - `layer authoring framework`
  - `tiny graphics-facing wrapper`
  - `registry-backed layer micro-tool`
  - `runtime adaptation layer`
- The strongest lesson from this wave is that some of the most reusable OpenXR
  donors live between
  `sample app`
  and
  `platform`.
- Another strong lesson is that tiny operator tools and narrow graphics facades
  can be just as donor-worthy as bigger platforms when their boundaries are
  unusually clear.

## Reusable methods clarified by this wave

- `Macro-generated OpenXR API-layer framework with typed per-handle data registries`
- `Tiny graphics-facing OpenXR facade that collapses session, frame, and swapchain boilerplate`
- `Registry-backed OpenXR layer inspection and reordering micro-tool`
- `Configurable runtime post-process OpenXR layer with live reload and staged image effects`

## Recommended next moves after this wave

1. Treat `quark` as the strongest donor in this wave for
   `OpenXR API-layer authoring`.
2. Keep `rayxr` visible whenever `VR-apps-lab` needs a
   `small renderer-facing OpenXR helper`
   reference.
3. Keep `openxr-layer-scripts` visible as a thin but useful
   `layer-state workflow`
   donor.
4. Treat `OpenXR-CAS` as the clearest mature donor in this wave for
   `runtime adaptation layer`
   work.
