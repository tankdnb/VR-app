# VR Projects Wave 76: OpenXR Capability-Injection Layers, Input Remappers, and Peripheral Extension Bridges

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `OpenXR capability-injection layers`, `input remappers`, and
  `peripheral extension bridges`.

## Why this wave exists

`VR-apps-lab` already had strong coverage of OpenXR runtime inspectors,
platform shells, and view-shaping layers, but it still lacked a clearer answer
to:

`what the best OpenXR layers look like when their job is to add capabilities or remap semantics rather than only inspect or patch rendering`.

This wave exists to make that family clearer:

- archived but still instructive capability-injection layers;
- input-remapping layers powered by an external runtime;
- tiny Rust baselines for new capability-layer experiments.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with capability-injection, hand-tracking, and remapping
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `ultraleap/OpenXRHandTracking` | Strong product reference for an implicit layer that injects `XR_EXT_hand_tracking` support from external hardware |
| `Sorenon/openxr_remapping_layer` | Strong donor for OpenXR action remapping through an external input runtime |
| `verncat/OpenXR_ApiLayer_Patstrap` | Useful lower-bound donor for a tiny Rust API-layer skeleton |

## Deep-pass notes by project

## `ultraleap/OpenXRHandTracking`

- GitHub:
  [ultraleap/OpenXRHandTracking](https://github.com/ultraleap/OpenXRHandTracking)
- What it is:
  an archived implicit OpenXR API layer that exposes
  `XR_EXT_hand_tracking` and `XR_EXT_hand_joints_motion_range`
  from Ultraleap hardware without requiring application changes.
- Why it matters:
  it is the clearest product reference in this wave for
  `capability injection layer that overrides or supplements runtime support`.
- Interesting ideas:
  implement a capability as an implicit layer instead of a separate app;
  allow the layer to override the runtime's own extension implementation when
  necessary; keep hardware mount position, tilt, disable flags, and logging
  operator-configurable through environment variables.
- Interesting implementation choices:
  the public snapshot is thin and release-oriented, but
  `README.original.md`
  still exposes the core design clearly: implicit activation, extension
  advertisement, mount calibration through env vars, and log-level control.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the public repo is archived and source-thin, so it is stronger as a product
  and architecture reference than as a direct code donor.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `capability-injection OpenXR layer`
  reference rather than another diagnostics layer.

## `Sorenon/openxr_remapping_layer`

- GitHub:
  [Sorenon/openxr_remapping_layer](https://github.com/Sorenon/openxr_remapping_layer)
- What it is:
  a Rust OpenXR API layer that routes input remapping through the external
  `SuInput` runtime.
- Why it matters:
  it is the clearest donor in this wave for
  `OpenXR action remapping layer with external runtime ownership`.
- Interesting ideas:
  treat input remapping as a layer concern instead of an engine plugin; detect
  the active runtime and adjust behavior accordingly; keep per-instance handle
  state inside wrapper registries rather than one global blob.
- Interesting implementation choices:
  `layer_entry/src/lib.rs`
  handles negotiation and initialization while
  `layer_core/src/entry.rs`
  creates the downstream instance, detects runtime identity, and creates the
  `SuInput` driver surface; the `openxr_overrides` module exposes the hook
  table behind `xrGetInstanceProcAddr`.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  still TODO-heavy as a product, but the hook and wrapper boundaries are
  already donor-worthy.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `layer-level input remapping`
  donor.

## `verncat/OpenXR_ApiLayer_Patstrap`

- GitHub:
  [verncat/OpenXR_ApiLayer_Patstrap](https://github.com/verncat/OpenXR_ApiLayer_Patstrap)
- What it is:
  a very small Rust OpenXR API-layer skeleton with explicit negotiation and
  forwarding hooks.
- Why it matters:
  it is the clearest lower-bound donor in this wave for
  `small Rust capability-layer baseline`.
- Interesting ideas:
  keep the exported layer entry points visible; store the next
  `xrGetInstanceProcAddr`
  function pointer centrally; use a minimal dependency surface to make the
  lower bound obvious.
- Interesting implementation choices:
  `src/lib.rs`
  exports `_xrGetInstanceProcAddr`, `_xrCreateApiLayerInstance`, and
  `xrNegotiateLoaderApiLayerInterface`, forwards to the next layer, and logs
  function names as they pass through.
- Code donor value:
  medium-high.
- Product reference value:
  low-medium.
- Architecture reference value:
  medium-high.
- Caveats:
  extremely small and not productized, but useful precisely because it shows
  the baseline without abstraction fog.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `tiny Rust OpenXR API-layer starter`
  reference.

## Main takeaways from Wave 76

- `OpenXR capability layers` now split more cleanly into:
  - `implicit extension-injection layer`
  - `external-runtime input remapping layer`
  - `tiny negotiation-and-forwarding skeleton`
- The strongest lesson from this wave is that
  `OpenXR API layer`
  is not only a diagnostics or rendering patch surface. It is also a place
  where new capabilities and semantics can be injected before an engine ever
  sees them.
- Another strong lesson is that even an archived or source-thin repo can still
  matter if it exposes the product shape of a useful capability-injection
  pattern.

## Reusable methods clarified by this wave

- `Implicit OpenXR capability-injection layer that surfaces external hardware support through extension emulation or override`
- `OpenXR input-remapping layer with external input-runtime ownership and per-handle wrapper registries`
- `Minimal Rust OpenXR API-layer skeleton with explicit loader negotiation and forwarding hooks`

## Recommended next moves after this wave

1. Keep `OpenXRHandTracking` visible as a product reference whenever
   `VR-apps-lab` needs a
   `capability injection`
   comparison.
2. Treat `openxr_remapping_layer` as the clearest donor in this wave for
   `layer-level input remapping`.
3. Treat `OpenXR_ApiLayer_Patstrap` as a useful lower-bound baseline whenever a
   future branch needs a
   `small Rust API-layer starter`.
