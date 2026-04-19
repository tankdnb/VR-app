# VR Projects Wave 36: Runtime Service Hosts, OpenXR Utility Platforms, and Layer Doctoring

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `runtime-side service hosts`, `broader OpenXR utility platforms`, and
  `layer diagnostics and fixers`.

## Why this wave exists

`VR-apps-lab` already had many smaller OpenXR tools, but it still needed a
clearer picture of the `platform-shaped` end of the family:

- service hosts that split UI, landing-space, and runtime-layer concerns;
- larger monitor or overlay platforms that feel closer to a product shell than
  a one-shot tool;
- layer-management tools that model real errors and fixes instead of only
  listing manifests.

This wave exists to make `runtime utility platform design` clearer inside
`VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with OpenXR service-host, layer-manager, and utility-platform
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `clear-xr/clearxr-server` | Strongest donor for a runtime-side platform split across a desktop host, a landing-space app, and an OpenXR API layer |
| `vrkit-platform/vrkit-platform` | Strongest donor for a plugin-shaped overlay or monitor platform with Electron shell and native overlay interop |
| `maluoi/openxr-explorer` | Strongest polished reference for `runtime explorer plus switching helper` design |
| `fredemmott/OpenXR-API-Layers-GUI` | Strongest donor for a layer doctor built around lint rules and fixable problems rather than simple toggles |

## Secondary candidates surfaced in the same wave

No separate secondary repo was promoted beyond the frozen shortlist in this
pass.

## Deep-pass notes by project

## `clear-xr/clearxr-server`

- GitHub:
  [clear-xr/clearxr-server](https://github.com/clear-xr/clearxr-server)
- What it is:
  a broader Clear XR platform whose most reusable public slice is the split
  between `clearxr-streamer`, `clearxr-space`, and `clearxr-layer`.
- Why it matters:
  it is the clearest donor in the repo for
  `desktop host + landing-space app + API layer` as one coordinated runtime
  utility platform.
- Interesting ideas:
  keep the desktop app responsible for session orchestration, pairing, and
  service logic; keep the landing-space app separate; keep runtime adaptation
  in a dedicated API layer instead of burying it in the shell.
- Interesting implementation choices:
  `clearxr-streamer/src/main.rs`,
  `clearxr-space/src/main.rs`, and
  `clearxr-layer/src/lib.rs`
  make the `desktop shell -> native OpenXR space -> action-rewriting layer`
  split explicit. The layer is especially useful because it translates
  transport-specific opaque data into standard OpenXR action state.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the broader CloudXR and pairing stack is larger than the main donor lesson;
  the reusable value is the split, not every feature around it.
- What to inspect next:
  keep it as the main donor whenever a future `VR-apps-lab` branch needs a
  `service host + runtime-side layer + companion app` architecture.

## `vrkit-platform/vrkit-platform`

- GitHub:
  [vrkit-platform/vrkit-platform](https://github.com/vrkit-platform/vrkit-platform)
- What it is:
  a broad Electron and native-interop platform whose current public snapshot
  spans overlays, monitors, builder tools, plugins, and domain-specific app
  concerns.
- Why it matters:
  it is the strongest donor in the repo for
  `plugin-shaped overlay platform with desktop shell and native interop`.
- Interesting ideas:
  drive overlays from a desktop host instead of a monolithic VR-only process;
  make plugins first-class; keep overlay state, editors, and persistence inside
  platform services rather than one-off windows.
- Interesting implementation choices:
  `packages/js/vrkit-app/src/main/services/overlay-manager/OverlayManager.ts`
  and
  `packages/js/vrkit-app/src/main/services/plugin-manager/PluginManager.ts`
  make the overlay lifecycle, native interop, plugin install flow, manifest
  handling, and persistence boundaries explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the public repo is broad and scope-shifted enough that it still deserves a
  narrower future pass.
- What to inspect next:
  keep a future pass focused on plugin manifests, native overlay-manager
  interop, and where OpenXR-specific logic actually begins and ends.

## `maluoi/openxr-explorer`

- GitHub:
  [maluoi/openxr-explorer](https://github.com/maluoi/openxr-explorer)
- What it is:
  a polished OpenXR runtime explorer with shared inspection core, GUI, CLI, and
  a separate helper for runtime switching.
- Why it matters:
  it remains the strongest single product reference in the repo for an
  `OpenXR doctor` direction.
- Interesting ideas:
  share runtime enumeration and manifest parsing between GUI and CLI; keep
  privileged runtime switching in a separate helper; make runtime state human
  readable for both developers and power users.
- Interesting implementation choices:
  `src/common/xrruntime.cpp`,
  `src/openxrexplorer/app_cli.cpp`, and
  `src/xrsetruntime/`
  make runtime enumeration, manifest naming, duplicate filtering, and
  helper-assisted switching easy to inspect.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the core runtime-explorer lesson was already visible in earlier research; the
  new value here is stronger code-level evidence for its shared-core design.
- What to inspect next:
  keep it as the baseline comparison repo whenever a future branch needs
  `runtime inventory, manifest inspection, and switching UX`.

## `fredemmott/OpenXR-API-Layers-GUI`

- GitHub:
  [fredemmott/OpenXR-API-Layers-GUI](https://github.com/fredemmott/OpenXR-API-Layers-GUI)
- What it is:
  a Windows layer-management tool that detects, explains, and fixes common
  OpenXR API-layer problems.
- Why it matters:
  it is the clearest donor in the repo for
  `layer doctor built around lint errors and fix objects`.
- Interesting ideas:
  treat bad runtime state as structured lint results; model repairs explicitly;
  keep layer ordering, invalid state, and known-bad layers inside a diagnostics
  rule system rather than a plain settings UI.
- Interesting implementation choices:
  `src/Linter.cpp`,
  `src/LayerRules.cpp`, and
  `src/linters/`
  make the `rule registry -> lint problem -> fixable action` flow explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  Windows-only, but the fix-oriented structure is the reusable lesson rather
  than the exact platform bindings.
- What to inspect next:
  keep it as the main donor whenever a future `VR-apps-lab` tool needs
  `structured runtime repair` instead of simple runtime listing.

## Main takeaways from Wave 36

- `Runtime utility platforms` are not one thing; the strongest split in this
  family is:
  - `service host + landing-space app + API layer`
  - `desktop shell + plugin manager + native overlay interop`
  - `runtime explorer with shared GUI/CLI core`
  - `fix-oriented layer doctor with lint rules`
- The best donor lesson is often the `responsibility split`, not the whole
  product:
  - service orchestration separated from runtime adaptation
  - plugin management separated from overlay instances
  - inspection core separated from switching helper
  - lint rules separated from repair actions

## Reusable methods clarified by this wave

- `Runtime-side XR utility platform split across desktop host, landing-space app, and API layer`
- `Plugin-manifest overlay platform with Electron control shell and native overlay interop`

## Recommended next moves after this wave

1. Treat `clearxr-server` as the strongest donor for
   `service host + runtime layer + companion app` splits.
2. Keep `vrkit-platform` visible as the best current donor for
   `plugin-shaped runtime utility platform`, but retain an honest
   `Partially studied` status.
3. Keep `openxr-explorer` as the default baseline for
   `OpenXR doctor` and runtime-inspection UX.
4. Keep `OpenXR-API-Layers-GUI` as the strongest reference for
   `fix-oriented layer diagnostics`.
