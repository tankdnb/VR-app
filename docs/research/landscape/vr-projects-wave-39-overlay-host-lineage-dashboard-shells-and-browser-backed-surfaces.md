# VR Projects Wave 39: Overlay Host Lineage, Dashboard Shells, and Browser-Backed Surfaces

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `overlay host lineage`, `dashboard shells`, and
  `browser-backed overlay surfaces`.

## Why this wave exists

`VR-apps-lab` already had many overlay references, but one branch was still not
clean enough:

- the old `ovr-utils` lineage where the public GitHub repo no longer contains
  the live source;
- suite shells that manage multiple overlays as reusable instances;
- modern utility hosts that run both as desktop app and SteamVR overlay;
- browser-backed toolkits that expose a general overlay construction pattern.

This wave exists to make `overlay host lineage and toolkit-level overlay
construction` clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with overlay-suite, dashboard-shell, and browser-overlay
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `CrispyPin/ovr-utils` | Important historical lineage node whose current GitHub state needed honest reclassification |
| `mittorn/ovr-utils-dashboard` | Strong donor for a settings-driven Godot overlay suite with reusable overlay instances |
| `hai-vr/h-view` | Strong donor for a broader utility host that spans desktop window, SteamVR overlay, OSCQuery, hardware views, and optional OCR |
| `BenWoodford/SteamVR-Webkit` | Strong donor for a browser-backed overlay toolkit with JS interop and dual dashboard or in-game surfaces |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `sh-akira/VROverlay` | Still a useful overlay sample, but weaker as a host-level donor than the broader suite and toolkit repos in this wave |

## Deep-pass notes by project

## `CrispyPin/ovr-utils`

- GitHub:
  [CrispyPin/ovr-utils](https://github.com/CrispyPin/ovr-utils)
- What it is:
  the GitHub snapshot is now mostly a relocation notice pointing to the live
  Codeberg home of the project.
- Why it matters:
  it still matters as a `historical utility-suite lineage` node, even though
  the current GitHub repo is no longer the real code donor.
- Interesting ideas:
  preserve lineage honestly; distinguish between a historically important
  product branch and a currently inspectable donor surface.
- Interesting implementation choices:
  the main public lesson here is not code structure, but the need to treat the
  GitHub state as an incomplete archival pointer rather than a strong direct
  donor.
- Code donor value:
  low.
- Product reference value:
  medium.
- Architecture reference value:
  low-medium.
- Caveats:
  the live source moved off GitHub, so this repo should not be over-promoted as
  a current direct donor.
- What to inspect next:
  revisit only if a future recovery pass explicitly follows the non-GitHub
  upstream.

## `mittorn/ovr-utils-dashboard`

- GitHub:
  [mittorn/ovr-utils-dashboard](https://github.com/mittorn/ovr-utils-dashboard)
- What it is:
  a Godot-based cross-platform SteamVR overlay shell with reusable overlays,
  settings sync, custom add-ons, and utility panels like keyboard, display, and
  battery views.
- Why it matters:
  it is the strongest donor in the repo for
  `settings-driven overlay suite with reusable overlay instances`.
- Interesting ideas:
  store overlays as data-driven instances; keep per-overlay persistence and sync
  in a dedicated node; build common overlay behavior as add-ons instead of
  repeating it in each panel.
- Interesting implementation choices:
  `src/overlay_manager.gd` and
  `src/overlay_settings_sync.gd`
  make the `load configured overlays -> instantiate reusable overlay scenes ->
  sync per-overlay settings` flow explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  platform-specific helper scripts and bundled artifacts exist around the core
  shell, but the reusable lesson is already clear enough.
- What to inspect next:
  keep it as the main donor whenever a future path needs
  `overlay suite shell + reusable instance + settings sync`.

## `hai-vr/h-view`

- GitHub:
  [hai-vr/h-view](https://github.com/hai-vr/h-view)
- What it is:
  a broader utility host that runs as desktop app and SteamVR overlay, with
  modules for OSCQuery, hardware views, avatar menus, optional OCR, networking,
  and overlay input variants.
- Why it matters:
  it is the clearest donor in the repo for
  `desktop-plus-overlay utility host with overlay-first UX but broader product
  scope`.
- Interesting ideas:
  keep desktop and overlay paths in the same host; let overlay mode coexist with
  broader utility modules; make the UI action-manifest-aware; keep modules like
  hardware, OSCQuery, networking, and processing inside one coherent shell.
- Interesting implementation choices:
  `h-view/src/Ui/MainApp/UiMainApplication.cs`,
  `h-view/src/Overlay/HVImGuiOverlay.cs`, and
  `h-view/src/OVR/HVOpenVRManagement.cs`
  make the `desktop window -> SteamVR overlay -> module-driven utility host`
  flow explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broad scope, but the public repo now makes that breadth visible enough to
  count as `Already studied`.
- What to inspect next:
  use its existing reuse plan whenever a future branch needs a
  `full utility host` rather than a thin overlay.

## `BenWoodford/SteamVR-Webkit`

- GitHub:
  [BenWoodford/SteamVR-Webkit](https://github.com/BenWoodford/SteamVR-Webkit)
- What it is:
  a toolkit for building browser-backed SteamVR overlays using offscreen
  rendering and JS interop.
- Why it matters:
  it is the clearest donor in the repo for
  `offscreen-browser overlay toolkit with dual dashboard and in-game surfaces`.
- Interesting ideas:
  separate overlay toolkit from finished product; support dashboard and in-game
  surfaces; expose JS interop and keyboard integration as reusable building
  blocks instead of app-specific hacks.
- Interesting implementation choices:
  `SteamVR-WebKit/WebKitOverlay.cs`
  makes the `Chromium offscreen browser -> OpenGL texture -> dashboard or
  in-game overlay -> keyboard and JS interop` flow explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  older stack, but still one of the cleanest public donors for
  `web-to-overlay toolkit` construction.
- What to inspect next:
  keep it visible whenever a future overlay branch needs
  `browser-backed UI as reusable VR surface`.

## Main takeaways from Wave 39

- `Overlay host lineage` is now clearer as more than a pile of overlay apps.
- The strongest split in this family is:
  - `historical lineage node with relocated source`
  - `settings-driven suite shell`
  - `full desktop-plus-overlay utility host`
  - `browser-backed overlay toolkit`
- The most reusable lesson is often the `host boundary`:
  - know when GitHub is only a lineage pointer
  - separate overlay instance lifecycle from individual overlay content
  - keep desktop and overlay modes inside one reusable utility host
  - expose browser-backed overlay creation as a toolkit, not only a finished app

## Reusable methods clarified by this wave

- `Offscreen-browser overlay toolkit with JS interop and dual dashboard/in-game surfaces`
- `Settings-driven overlay suite with reusable overlay instances and persistence sync`

## Recommended next moves after this wave

1. Keep `ovr-utils` in the repo as an honest lineage node, not as an
   over-promoted current code donor.
2. Treat `ovr-utils-dashboard` as the clearest donor for
   `data-driven suite shell + reusable overlay instances`.
3. Promote `h-view` to the mainline `Already studied` host references whenever
   a future branch needs a full utility shell instead of a thin overlay.
4. Keep `SteamVR-Webkit` as the best current toolkit donor for
   `browser-backed overlay surfaces`.
