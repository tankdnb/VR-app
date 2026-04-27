# VR Projects Wave 98: Udon Sync, Events, Runtime Logging, and Shared Helper Micro-Frameworks

- Date: `2026-04-27`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `Udon sync`, `event dispatch`, `runtime logging`, and
  `shared helper micro-frameworks`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of creator mechanics and broader
utility foundations than of:

`the mid-layer runtime frameworks that actually let larger creator systems route events, ship typed network payloads, inspect state in-world, or keep reusable sync substrate coherent`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with Udon event, networking, logging, and sync-helper
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Varneon/VUdon-Events` | Strong donor for UnityEvent-like routing into Udon through build-time resolution and runtime dispatch |
| `DeltaNeverUsed/UdonSharpNetworkingLib` | Strong donor for typed parameterized networking over synced byte arrays |
| `MMMaellon/LightSync` | Useful lineage donor for a stateful synced-object substrate, even though the repository is currently unstable |
| `Varneon/VUdon-Logger` | Strong donor for in-world diagnostics through an abstract logger plus console prefab |

## Deep-pass notes by project

## `Varneon/VUdon-Events`

- GitHub:
  [Varneon/VUdon-Events](https://github.com/Varneon/VUdon-Events)
- What it is:
  a creator package that gives UdonSharp a more UnityEvent-like serialized
  event surface.
- Why it matters:
  it is the clearest donor in this wave for
  `persistent call-graph authoring that still resolves down to ordinary Udon event addresses`.
- Interesting ideas:
  separate editor resolution from runtime dispatch; serialize event calls into
  `DataList`; keep one singleton dispatcher that injects argument or target
  program variables before invoking the actual encoded Udon event address.
- Interesting implementation choices:
  `Runtime/UdonEventResolver.cs`
  loads JSON address lookup data and resolves method or argument addresses;
  `Runtime/Udon Programs/UdonEventHandler.cs`
  dispatches serialized call descriptions through `SetProgramVariable` and
  `SendCustomEvent`; `Editor/UdonEventBuildPostProcessor.cs`
  injects or populates the handler during scene processing.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  very high.
- Caveats:
  the design is heavily shaped by Udon serialization and build-pipeline limits,
  so its complexity is inseparable from that target.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `serialized event-routing`
  donor.

## `DeltaNeverUsed/UdonSharpNetworkingLib`

- GitHub:
  [DeltaNeverUsed/UdonSharpNetworkingLib](https://github.com/DeltaNeverUsed/UdonSharpNetworkingLib)
- What it is:
  a compiler-patched UdonSharp networking layer that adds parameterized network
  events on top of synced byte arrays.
- Why it matters:
  it is the clearest donor in this wave for
  `typed RPC semantics built above ordinary Udon sync primitives`.
- Interesting ideas:
  annotate methods with network-target metadata; patch the compiler to generate
  the routing surface; serialize parameters into byte arrays; separate target
  modes such as `All`, `Master`, `Specific`, or `Local`.
- Interesting implementation choices:
  `Editor/CompilePatch.cs`
  injects a syntax-rewrite step into the UdonSharp pipeline; `Runtime/Serializer.cs`
  provides explicit packing and unpacking for primitives, arrays, vectors,
  quaternions, and `VRCPlayerApi`; `NetworkingLibUdonSharpBehaviour.cs`
  layers owner checks, target routing, and generated function dispatch over the
  synced `_data`
  payload.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  very high.
- Caveats:
  the README is explicit that newer VRChat releases reduce the need for some of
  this package's core value, but the architecture remains a strong donor.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs stronger
  `parameterized creator networking`
  comparisons.

## `MMMaellon/LightSync`

- GitHub:
  [MMMaellon/LightSync](https://github.com/MMMaellon/LightSync)
- What it is:
  a broad synced-object package for VRChat with custom state components, helper
  loopers, data separation, and editor auto-setup, but currently marked by its
  author as broken and unstable.
- Why it matters:
  it is the clearest lineage donor in this wave for
  `ambitious stateful object-sync substrate`
  even though it is not a safe direct recommendation right now.
- Interesting ideas:
  keep built-in synced-object states as negative IDs; allow custom positive
  states through attached `LightSyncState`
  components; separate sync data into a sibling object; auto-assign ids and
  singleton ownership at editor time.
- Interesting implementation choices:
  `Runtime/Scripts/LightSync.cs`
  exposes the large state model and built-in state constants;
  `Helpers/LightSyncState.cs`
  formalizes state lifecycle and lerp callbacks; `Helpers/Singleton.cs`
  handles editor auto-setup and id assignment across tracked objects.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  the author explicitly marks the package as broken and recommends
  `SmartObjectSync`
  instead, so it should be treated as lineage and pattern reference first.
- What to inspect next:
  revisit only when `VR-apps-lab` needs a broader
  `custom object-sync lineage`
  comparison.

## `Varneon/VUdon-Logger`

- GitHub:
  [Varneon/VUdon-Logger](https://github.com/Varneon/VUdon-Logger)
- What it is:
  a creator-world runtime logger with an abstract base class plus an in-world
  console prefab.
- Why it matters:
  it is the clearest donor in this wave for
  `runtime diagnostics that feel like a real console surface instead of scattered Debug.Log calls`.
- Interesting ideas:
  separate a generic `UdonLogger`
  base from one concrete UI implementation; let the console filter by log type,
  toggle timestamps, adjust font size, and cap retained entries.
- Interesting implementation choices:
  `Runtime/Udon Programs/Abstract/UdonLogger.cs`
  mirrors a small logger interface surface for UdonSharp; `UdonConsole.cs`
  stores log type and timestamp in object names, recycles UI entries, filters
  them through toggles, and initializes references during build post-process.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  it is UI-oriented and not a full external trace or profiling system.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `in-world runtime diagnostics`
  donor.

## Main takeaways from Wave 98

- `creator runtime helper framework`
  is a real family of its own, not just leftover glue between larger systems.
- The strongest architectural lesson from this wave is that
  `build-time and compile-time intervention`
  often matter more than the runtime API surface in constrained creator
  ecosystems.
- Event routing, parameterized networking, runtime logging, and object sync are
  separate donor branches even when creators often mentally lump them together.
- A repo can still be useful as lineage even when it is no longer safe as a
  direct recommendation, as `LightSync`
  shows.

## Reusable methods clarified by this wave

- `Build-time event resolver with serialized DataList call graph and singleton runtime dispatcher`
- `Compile-time generated RPC surface over synced byte arrays with target-routing semantics`
- `In-world runtime console with abstract logger base, log-type filters, timestamps, and font controls`

## Recommended next moves after this wave

1. Keep `VUdon-Events` visible as one of the strongest
   `serialized event routing`
   donors in the repo.
2. Keep `UdonSharpNetworkingLib` visible as one of the strongest
   `parameterized creator networking`
   donors in the repo.
3. Treat `LightSync` as an honest
   `lineage and pattern reference`
   until a future comparison pass puts it beside stronger current sync systems.
4. Revisit `VUdon-Logger` whenever future creator diagnostics work needs a
   smaller
   `runtime console`
   donor rather than a full profiling or analyzer system.
