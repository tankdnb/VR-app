# VR Projects Wave 93: VRChat Creator Diagnostics, Editor Inspection, Profiling, and Static-Analysis Helpers

- Date: `2026-04-21`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat creator diagnostics`, `editor inspection`, `profiling`, and
  `static-analysis helpers`.

## Why this wave exists

`VR-apps-lab` already had clearer coverage of creator runtime substrate than of:

`how creators reduce iteration cost before upload by simulating players, inspecting scene Udon state, instrumenting compile output, or receiving editor-time warnings for unsupported patterns`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with Udon testing, profiling, and analysis queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `GotoFinal/GotoUdon` | Strong donor for editor-side Udon emulation, event injection, and multi-client launch workflow |
| `Varneon/UdonExplorer` | Strong donor for sortable scene inspection of Udon behaviours and program metadata |
| `DeltaNeverUsed/UdonSharpProfiler` | Strong donor for compiler instrumentation and Perfetto trace output |
| `esnya/UdonRabbit.Analyzer` | Strong donor for static-analysis rules tailored to unsupported UdonSharp or networking patterns |

## Deep-pass notes by project

## `GotoFinal/GotoUdon`

- GitHub:
  [GotoFinal/GotoUdon](https://github.com/GotoFinal/GotoUdon)
- What it is:
  a Unity editor toolkit that emulates parts of the VRChat or Udon runtime,
  spawns simulated players, attaches event buttons to Udon behaviours, and can
  launch multiple VRChat profiles for quicker testing.
- Why it matters:
  it is the clearest donor in this wave for
  `editor-side world logic rehearsal before launching the real client`.
- Interesting ideas:
  simulate enough of the player and event surface to catch logic bugs early;
  add lightweight event buttons onto scene Udon behaviours; keep profile and
  client launch automation in the same creator tool so iteration paths shorten.
- Interesting implementation choices:
  `Assets/GotoUdon/VRC/VRCEmulator.cs`
  builds a local simulation host with delayed join events and hooks into
  `Networking` shims; `Assets/GotoUdon/Editor/UdonDebuggerEditor.cs`
  adds one-click event injection for common Udon lifecycle and pickup events.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the repo is explicit about simulation limits and does not attempt full
  networking fidelity, so it is best used as a creator iteration donor instead
  of a perfect runtime mirror.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `editor-side Udon rehearsal and event injection`
  reference.

## `Varneon/UdonExplorer`

- GitHub:
  [Varneon/UdonExplorer](https://github.com/Varneon/UdonExplorer)
- What it is:
  a Unity editor window that enumerates scene `UdonBehaviour`s and exposes
  sync mode, update order, program source, serialized asset size, and symbol
  lists in a sortable explorer.
- Why it matters:
  it is the clearest donor in this wave for
  `scene-wide creator inspection with fast drill-through into Udon metadata`.
- Interesting ideas:
  treat scene Udon state as a table, not as a click-through inspector chore;
  keep filters and sorting first-class; expose source-selection shortcuts right
  where metadata is displayed.
- Interesting implementation choices:
  `Packages/com.varneon.udonexplorer/Editor/UdonExplorerWindow.cs`
  manages a split-view inspector with auto-refresh and metadata panes;
  `UdonListView.cs`
  builds the sortable tree, scene refresh path, filters, and context actions.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is intentionally inspection-focused and does not mutate or validate scene
  behaviour beyond what the explorer itself surfaces.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `world scene diagnostics and Udon inventory`
  donor.

## `DeltaNeverUsed/UdonSharpProfiler`

- GitHub:
  [DeltaNeverUsed/UdonSharpProfiler](https://github.com/DeltaNeverUsed/UdonSharpProfiler)
- What it is:
  a profiling tool that patches the UdonSharp compiler, injects instrumentation
  into generated output, and emits traces that can be viewed in Perfetto.
- Why it matters:
  it is the clearest donor in this wave for
  `compile-time instrumentation of creator scripts instead of manual logging only`.
- Interesting ideas:
  insert profiling hooks where UdonSharp emits or compiles code; keep runtime
  controls minimal and export traces into an existing strong viewer rather than
  building a bespoke visualizer.
- Interesting implementation choices:
  `Packages/deltaneverused.udonsharpprofiler/Editor/Injections.cs`
  manages Harmony patching into the compiler pipeline;
  `EmitAllProgramsPatch.cs`
  injects reflection values into the emit flow;
  `Runtime/ProfilerController.cs`
  provides a tiny runtime control surface that toggles recording and writes the
  emit data back into logs for export.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  it depends on internal compiler structure and intentionally slows compiled
  programs while active.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `compiler-pipeline profiler or trace exporter`
  donor.

## `esnya/UdonRabbit.Analyzer`

- GitHub:
  [esnya/UdonRabbit.Analyzer](https://github.com/esnya/UdonRabbit.Analyzer)
- What it is:
  a Roslyn analyzer suite for Udon or UdonSharp that flags unsupported language
  features, invalid API patterns, and networking or visibility mistakes at edit
  time.
- Why it matters:
  it is the clearest donor in this wave for
  `static validation that knows the Udon or UdonSharp constraint model`.
- Interesting ideas:
  move unsupported-language detection earlier into the IDE; encode UdonSharp
  rules as analyzers and code fixes instead of only documenting them in wikis;
  treat networking and visibility contracts as machine-checkable.
- Interesting implementation choices:
  analyzer files such as `NotSupportTryCatchFinally.cs`
  attach directly to syntax kinds and report targeted diagnostics only for
  `UdonSharpBehaviour` contexts; `MethodCalledByCustomNetworkEventMustBePublic.cs`
  scans callers and reports rule violations around `SendCustomNetworkEvent`.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the project is broad and lightly maintained, so its strongest role is as a
  rule-pattern donor and ecosystem reference rather than a guaranteed
  up-to-date lint pack.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `creator IDE guardrail and static rule authoring`
  reference.

## Main takeaways from Wave 93

- `VRChat creator diagnostics`
  now splits more cleanly into:
  - editor-side world or player simulation;
  - scene inventory and metadata inspection;
  - compiler instrumentation and trace export;
  - static-analysis guardrails in the IDE.
- The strongest lesson from this wave is that
  `creator diagnostics`
  work best when they hit several phases of the workflow: before play,
  during compilation, and during static editing.
- Another strong lesson is that
  `inspection and validation`
  are different roles. One shows creator state; the other blocks or warns about
  invalid patterns before upload.

## Reusable methods clarified by this wave

- `Unity-editor Udon emulation with simulated players, event injection, and multi-client launch automation`
- `Sortable Udon behaviour explorer with source drill-through and sync metadata inspection`
- `Compiler-pipeline instrumentation that emits Perfetto-compatible traces for UdonSharp`
- `Roslyn analyzer suite for unsupported UdonSharp patterns and network-event contract validation`

## Recommended next moves after this wave

1. Keep `GotoUdon` visible as a strong
   `editor-side rehearsal and testing`
   donor.
2. Treat `UdonExplorer` as one of the strongest
   `scene inventory and metadata inspection`
   donors in the creator branch.
3. Use `UdonSharpProfiler` whenever future work needs a
   `trace-based compile instrumentation`
   reference instead of log spam alone.
4. Revisit `UdonRabbit.Analyzer` whenever future work needs a stronger
   `creator IDE guardrail or analyzer authoring`
   reference.
