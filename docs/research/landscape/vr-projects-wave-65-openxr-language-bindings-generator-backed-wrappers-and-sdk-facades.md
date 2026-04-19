# VR Projects Wave 65: OpenXR Language Bindings, Generator-backed Wrappers, and SDK Facades

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `OpenXR language bindings`, `generator-backed wrappers`, and `SDK facades`.

## Why this wave exists

`VR-apps-lab` already had better coverage for OpenXR runtimes and overlays than
for the lower-level question of
`how OpenXR is wrapped, generated, and made usable from different host languages`.

This wave exists to make that family clearer:

- raw and ergonomic binding stacks;
- wrappers generated from the Khronos registry;
- host-language adaptations that preserve the native dispatch model;
- higher-level facades that stay close enough to the native API to remain
  useful donors.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with OpenXR binding, Rust wrapper, Python binding, `.NET`
   binding, and Zig generator queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Ralith/openxrs` | Strong donor for a layered `safe + raw` OpenXR stack with real usage examples |
| `cmbruns/pyopenxr` | Strong donor for registry-driven Python bindings plus a higher-level scripting facade and optional API-layer helper |
| `EvergineTeam/OpenXR.NET` | Strong donor for `.NET` OpenXR bindings generated from `xr.xml` with explicit native-library resolution |
| `s-ol/openxr-zig` | Useful donor for build-integrated code generation and Zig-native naming adaptation |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `drypy/openxr.py` | Useful comparison node, but thinner and less systematized than `pyopenxr` in this pass |
| `FireFlyForLife/rlOpenXR` | Interesting wrapper experiment, but more of an app-facing helper than a strong binding-construction donor |

## Deep-pass notes by project

## `Ralith/openxrs`

- GitHub:
  [Ralith/openxrs](https://github.com/Ralith/openxrs)
- What it is:
  a Rust OpenXR stack that keeps an ergonomic `openxr` layer above a lower-level
  `sys` binding surface.
- Why it matters:
  it is the clearest donor in this wave for
  `safe + raw binding stack with explicit loader and feature boundaries`.
- Interesting ideas:
  keep ergonomic wrappers above a still-available raw layer; expose feature
  flags for different loader strategies; ship real examples instead of only the
  binding crate itself.
- Interesting implementation choices:
  `openxr/src/lib.rs`
  defines the higher-level wrapper surface,
  `sys/src/loader.rs`
  carries loader-negotiation metadata, and
  `openxr/examples/vulkan.rs`
  shows how the higher-level API is expected to be consumed.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  binding-first rather than utility-first, but that is exactly why it matters
  here.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `raw plus ergonomic wrapper split`
  for OpenXR-facing tooling.

## `cmbruns/pyopenxr`

- GitHub:
  [cmbruns/pyopenxr](https://github.com/cmbruns/pyopenxr)
- What it is:
  a Python OpenXR binding stack with registry-driven generation, a higher-level
  Python facade, and even an optional helper for building Python-facing API
  layers.
- Why it matters:
  it is the clearest donor in this wave for
  `generated scripting facade over a native OpenXR API`.
- Interesting ideas:
  split raw generated bindings from higher-level helper functions; make loader
  discovery platform-aware; let scripting-first tools still participate in
  API-layer experimentation.
- Interesting implementation choices:
  `src/generate/xrg/registry.py`
  loads the registry,
  `src/xr/functions.py`
  exposes more Pythonic helper layers,
  `src/xr/library/__init__.py`
  handles packaged loader selection, and
  `src/generate/py_api_layer/py_api_layer.cpp`
  makes the optional API-layer bridge explicit.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  a scripting-heavy donor rather than a direct runtime tool, but unusually rich
  for method extraction.
- What to inspect next:
  keep it visible whenever a future branch needs a
  `generated Python XR facade`
  or a scripting-side OpenXR experimentation path.

## `EvergineTeam/OpenXR.NET`

- GitHub:
  [EvergineTeam/OpenXR.NET](https://github.com/EvergineTeam/OpenXR.NET)
- What it is:
  a `.NET` OpenXR binding stack with generator code that consumes `xr.xml` and
  emits native interop surfaces.
- Why it matters:
  it is the clearest donor in this wave for
  `.NET registry-driven OpenXR bindings with explicit proc-address fallback`.
- Interesting ideas:
  treat generator code as a first-class part of the repo; centralize native
  library loading; preserve the native dispatch model even while exposing a
  managed-language binding.
- Interesting implementation choices:
  `OpenXRGen/OpenXRGen/Program.cs`
  owns the generator entry point while
  `OpenXRGen/Evergine.Bindings.OpenXR/NativeLibrary.cs`
  handles export resolution and fallback through `xrGetInstanceProcAddr`.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  lower-level and binding-focused, but exactly the right donor if
  `VR-apps-lab` later wants a managed-language OpenXR foundation.
- What to inspect next:
  keep it visible whenever a future branch needs a `.NET`-first OpenXR donor
  or registry-driven generation notes.

## `s-ol/openxr-zig`

- GitHub:
  [s-ol/openxr-zig](https://github.com/s-ol/openxr-zig)
- What it is:
  a Zig OpenXR wrapper that integrates code generation into the build flow and
  adapts the resulting API surface to Zig conventions.
- Why it matters:
  it is a strong donor for
  `build-integrated binding generation rather than pre-generated wrapper code`.
- Interesting ideas:
  let the build emit the binding; adapt naming and surfaces to the host
  language; keep code generation visible instead of hiding it behind shipped
  artifacts only.
- Interesting implementation choices:
  `generator/index.zig`
  owns the emission logic,
  `generator/openxr/build_integration.zig`
  wires generation into the build, and
  `examples/test.zig`
  shows how the resulting wrapper is consumed.
- Code donor value:
  medium-high.
- Product reference value:
  low-medium.
- Architecture reference value:
  high.
- Caveats:
  narrower ecosystem impact than Rust or Python here, but strong as a method
  donor.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a
  `build step emits wrapper code`
  comparison.

## Main takeaways from Wave 65

- `OpenXR binding donors` split more cleanly into:
  - `safe + raw layered stack`
  - `generated scripting facade`
  - `registry-driven managed-language binding emitter`
  - `build-integrated host-language wrapper generation`
- The strongest lesson from this wave is that
  `binding construction`
  is its own reusable family with direct implications for future tooling.
- Another strong lesson is that the generator boundary itself is often the most
  valuable donor, not just the emitted wrapper API.

## Reusable methods clarified by this wave

- `Safe and raw OpenXR binding stack generated from the Khronos registry`
- `Build-integrated binding generator that adapts API naming to host-language conventions`
- `Packaged Python OpenXR facade over generated raw calls with optional API-layer insertion`

## Recommended next moves after this wave

1. Treat `openxrs` as the clearest donor for
   `safe wrapper plus raw binding layer`.
2. Treat `pyopenxr` as the strongest donor in this wave for a
   `generated scripting-facing OpenXR facade`.
3. Keep `OpenXR.NET` visible whenever `VR-apps-lab` needs a `.NET`-first
   OpenXR comparison node.
4. Keep `openxr-zig` visible whenever a future branch needs a stronger
   `build-integrated wrapper generation`
   reference.
