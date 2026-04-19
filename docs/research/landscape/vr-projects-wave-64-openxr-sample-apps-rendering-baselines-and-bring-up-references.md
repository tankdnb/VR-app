# VR Projects Wave 64: OpenXR Sample Apps, Rendering Baselines, and Bring-up References

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `OpenXR sample apps`, `rendering baselines`, and `bring-up references`.

## Why this wave exists

`VR-apps-lab` already had better coverage for overlays, runtime tools, and
tracking helpers than for the lower-bound question of
`how a new OpenXR app actually gets from zero to a working frame loop`.

This wave exists to make that donor branch clearer:

- small worked examples that show instance, session, and swapchain bring-up;
- sample apps that split headset, controllers, graphics, and mirror output
  cleanly;
- platform-specific sample suites that reuse one shared OpenXR core.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with OpenXR sample-app, Vulkan example, GLES sample, and
   minimal bootstrap queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `maluoi/OpenXRSamples` | Strong donor for one-file OpenXR bring-up with explicit `D3D11` graphics and action-space setup |
| `janhsimon/openxr-vulkan-example` | Strong donor for a structured sample-app split across context, headset, controllers, mirror view, and renderer |
| `philpax/wgpu-openxr-example` | Useful donor for staged `desktop -> XR` migration in a modern Rust or `wgpu` stack |
| `terryky/android_openxr_gles` | Strong donor for a shared OpenXR utility core reused across several Android feature samples |
| `KHeresy/openxr-simple-example` | Useful lower-bound donor for minimal SDL/OpenGL OpenXR bring-up |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `jherico/OpenXR-Samples` | Historically useful, but this pass found clearer donor value in the other shortlisted repos |

## Deep-pass notes by project

## `maluoi/OpenXRSamples`

- GitHub:
  [maluoi/OpenXRSamples](https://github.com/maluoi/OpenXRSamples)
- What it is:
  a set of sample apps with an especially strong
  `SingleFileExample/main.cpp` that keeps the whole OpenXR bring-up path in one
  readable file.
- Why it matters:
  it is the clearest donor in this wave for
  `minimum viable OpenXR bootstrap with real graphics requirements`.
- Interesting ideas:
  filter extensions explicitly instead of hiding them behind a larger engine;
  keep swapchain creation, `D3D11` texture handling, and action-space setup
  readable in one place; use a one-file example as an honest lower-bound donor
  even if the broader repo contains more samples.
- Interesting implementation choices:
  `SingleFileExample/main.cpp`
  performs instance creation, graphics-requirements checks, swapchain image
  handling, action-set creation, hand-space creation, and the frame loop in one
  place without losing the runtime-facing details.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  sample-oriented rather than product-oriented, but unusually valuable as a
  bring-up reference.
- What to inspect next:
  keep it visible whenever a future branch needs a
  `single-file OpenXR bootstrap` donor or a minimal `D3D11` reference.

## `janhsimon/openxr-vulkan-example`

- GitHub:
  [janhsimon/openxr-vulkan-example](https://github.com/janhsimon/openxr-vulkan-example)
- What it is:
  a Vulkan-based OpenXR sample app that splits runtime bring-up across
  `Context`, `Headset`, `Controllers`, `MirrorView`, and renderer modules.
- Why it matters:
  it is the clearest donor in this wave for
  `structured sample-app architecture instead of a one-file tutorial`.
- Interesting ideas:
  keep graphics bring-up separate from headset lifecycle; let controllers own
  bindings and spaces; make mirror output a first-class module rather than
  incidental debug code.
- Interesting implementation choices:
  `src/Context.h`
  owns Vulkan and OpenXR bring-up,
  `src/Headset.h`
  formalizes frame states such as `RenderFully` or `SkipRender`,
  `src/Controllers.cpp`
  owns action bindings and spaces, and
  `src/Main.cpp`
  makes the module split visible instead of hiding it behind an engine shell.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  still a sample app, but much closer to a reusable scaffold than many minimal
  tutorials.
- What to inspect next:
  keep it visible whenever a future branch needs
  `Context + Headset + Controllers + MirrorView`
  as a reusable OpenXR app split.

## `philpax/wgpu-openxr-example`

- GitHub:
  [philpax/wgpu-openxr-example](https://github.com/philpax/wgpu-openxr-example)
- What it is:
  a Rust sample that moves from desktop rendering toward full XR rendering
  through staged modes and explicit `OpenXR + Vulkan + wgpu` glue.
- Why it matters:
  it is a useful donor for
  `incremental desktop-first bring-up before full XR mode`.
- Interesting ideas:
  expose intermediate modes instead of forcing `XR only`; treat `desktop`,
  `desktop with XR resolution`, and `XR` as explicit product states; keep the
  XR boundary readable even when a higher-level graphics stack is used.
- Interesting implementation choices:
  `src/main.rs`
  defines the staged execution modes while
  `src/xr.rs`
  owns OpenXR initialization, swapchain image flow, action-space wiring, and
  the Vulkan integration required for `wgpu`.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  less of a finished utility donor than the Vulkan sample, but stronger for
  `incremental migration` lessons.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `desktop first, XR second`
  bring-up pattern.

## `terryky/android_openxr_gles`

- GitHub:
  [terryky/android_openxr_gles](https://github.com/terryky/android_openxr_gles)
- What it is:
  an Android and GLES OpenXR sample suite that reuses one utility layer across
  several focused examples such as `imgui` or passthrough demos.
- Why it matters:
  it is the clearest donor in this wave for
  `shared OpenXR utility core reused across many small feature samples`.
- Interesting ideas:
  centralize loader and session bring-up in shared utilities; keep feature
  samples small; use the sample suite as a way to compare feature-specific code
  against one common runtime baseline.
- Interesting implementation choices:
  `common/util_oxr.cpp`
  owns much of the shared OpenXR setup while sample-specific app engines keep
  `imgui`, passthrough, or other feature logic local to each variant.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  Android-specific and feature-sample-oriented, but unusually useful when
  `shared core plus small sample leaves` is the lesson.
- What to inspect next:
  keep it visible whenever a future branch needs
  `shared OpenXR utility layer` references or Android sample comparisons.

## `KHeresy/openxr-simple-example`

- GitHub:
  [KHeresy/openxr-simple-example](https://github.com/KHeresy/openxr-simple-example)
- What it is:
  a small SDL and OpenGL OpenXR example that stays close to the lower-bound
  `bring up XR, draw simple geometry, and keep the flow visible` pattern.
- Why it matters:
  it is a useful lower-bound donor for
  `minimal cross-platform OpenXR sample without a large framework`.
- Interesting ideas:
  keep the graphics path simple; expose spaces, view config, and rendering
  logic directly; preserve a small enough codebase to read end to end.
- Interesting implementation choices:
  `main.cpp`
  owns most of the OpenXR and SDL bring-up while
  `glimpl.cpp`
  keeps the OpenGL-side rendering logic local and explicit.
- Code donor value:
  medium.
- Product reference value:
  low-medium.
- Architecture reference value:
  medium.
- Caveats:
  smaller and older than some other donors here, but still useful as a lower
  bound.
- What to inspect next:
  revisit whenever a future branch needs a compact `SDL/OpenGL OpenXR` donor.

## Main takeaways from Wave 64

- `OpenXR bring-up references` split more cleanly into:
  - `single-file bootstrap`
  - `structured sample app`
  - `desktop-to-XR migration path`
  - `shared utility core plus focused samples`
  - `minimal SDL/OpenGL lower bound`
- The strongest lesson from this wave is that
  `bring-up references`
  are a reusable family of their own, not just incidental sample code.
- Another strong lesson is that sample-app architecture matters even when the
  repo is not a product, because the module boundaries often become direct
  donors for future tools.

## Reusable methods clarified by this wave

- `Single-file OpenXR bootstrap with explicit extension filtering and graphics bring-up`
- `Structured OpenXR app split into context, headset, controllers, mirror view, and renderer`
- `Shared OpenXR utility core reused across many tiny feature samples`

## Recommended next moves after this wave

1. Treat `OpenXRSamples` as the clearest donor for
   `minimum viable OpenXR bootstrap`.
2. Treat `openxr-vulkan-example` as the strongest donor in this wave for a
   reusable non-engine sample-app split.
3. Keep `wgpu-openxr-example` visible whenever `VR-apps-lab` needs a stronger
   migration story from desktop rendering into XR.
4. Keep `android_openxr_gles` visible whenever a future branch needs
   `shared OpenXR core + feature samples`
   rather than one monolithic example.
