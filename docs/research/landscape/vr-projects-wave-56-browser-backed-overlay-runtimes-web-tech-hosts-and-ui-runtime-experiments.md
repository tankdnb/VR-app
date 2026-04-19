# VR Projects Wave 56: Browser-Backed Overlay Runtimes, Web-Tech Hosts, and UI Runtime Experiments

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `browser-backed overlay runtimes`, `web-tech hosts`, and
  `UI runtime experiments`.

## Why this wave exists

`VR-apps-lab` already had overlay products, thin texture-bridge samples, and
engine-native overlay extensions, but another adjacent donor line still needed
a cleaner map:

- overlay backends that treat a browser or web-style runtime as the UI surface;
- local daemon or `HTTP` models where the overlay host and the actual app are
  deliberately separate;
- offscreen desktop UI runtimes where the browser window is only a frame
  producer for `OpenVR`;
- experimental UI stacks that prove `OpenVR overlay` does not have to mean
  `Win32` or `ImGui`.

This wave exists to make
`browser-backed overlay runtimes, web-tech hosts, and UI runtime experiments`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with browser-overlay, `Electron`, `CEF`, and UI-runtime
   overlay queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `mekanoe/ovrsalt` | Strong donor for a split `backend/runtime/frontend` overlay architecture where the `OpenVR` connector, the frame-producing runtime, and the web-facing app shell are intentionally separate |
| `mekanoe/electron-openvr` | Strong donor for the thinnest possible `Electron offscreen window -> OpenVR texture` path |
| `joshperry/ovrly` | Strong donor for a `CEF` overlay host with per-app daemons, local `HTTP`, and explicit in-page API bridging |
| `ephemeral-laboratories/ComposeVR` | Useful donor for a more experimental `Compose Multiplatform -> OpenVR overlay` runtime bridge |

## Deep-pass notes by project

## `mekanoe/ovrsalt`

- GitHub:
  [mekanoe/ovrsalt](https://github.com/mekanoe/ovrsalt)
- What it is:
  a scrapped but still instructive overlay platform split into a native
  `Backend`, a Node-based `Runtime`, and a React or Pixi `Frontend`.
- Why it matters:
  it is one of the clearest donors in the repo for
  `native overlay backend plus web-runtime frontend with explicit process boundaries`.
- Interesting ideas:
  treat `OpenVR` handle lifecycle, process launching, shared memory, and
  browser-facing UI as separate concerns; make the overlay runtime send raw
  frame buffers rather than tying the whole tool to one render stack; let the
  frontend behave like an app layer instead of a hardcoded overlay scene.
- Interesting implementation choices:
  `Backend/main.cpp`
  plus `Backend/Overlay.cpp`
  expose the Windows-side `OpenVR`, shared-memory, and process-launch path,
  while the repo structure itself makes the
  `backend -> runtime -> frontend`
  split unusually explicit.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  the repo is abandoned and openly scrapped, so the value is mostly in the
  architecture decomposition rather than a production-ready host.
- What to inspect next:
  keep it visible whenever a future branch needs
  `browser-backed overlay runtime with a native host shell`.

## `mekanoe/electron-openvr`

- GitHub:
  [mekanoe/electron-openvr](https://github.com/mekanoe/electron-openvr)
- What it is:
  a tiny proof of concept that uses an offscreen `Electron BrowserWindow`,
  captures the rendered page, and streams the pixel buffer into an `OpenVR`
  overlay texture.
- Why it matters:
  it is the clearest lower-bound donor in the repo for
  `offscreen browser window mirrored directly into OpenVR`.
- Interesting ideas:
  keep the host extremely small; let a normal browser page become overlay
  content without a larger daemon model; treat `capturePage()` plus
  `setTextureFromBuffer` as the whole bridge.
- Interesting implementation choices:
  `index.js`
  makes the
  `offscreen BrowserWindow -> bitmap capture -> overlay texture submit`
  path explicit in a way that most larger browser-overlay hosts hide.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  extremely small and old, so it is stronger as a method donor than as a
  finished product reference.
- What to inspect next:
  keep it visible whenever a future branch needs the quickest
  `Electron -> overlay` experiment path.

## `joshperry/ovrly`

- GitHub:
  [joshperry/ovrly](https://github.com/joshperry/ovrly)
- What it is:
  a `CEF`-based overlay host where each app can run as its own daemon
  process and expose a local `HTTP` surface that the overlay browser loads.
- Why it matters:
  it is the clearest donor in the repo for
  `browser overlay host with per-app daemons and in-page API bridge`.
- Interesting ideas:
  let `ovrlies` behave like mini local web apps instead of bundling all UI into
  one overlay executable; bind native capabilities into the page runtime; make
  local daemon discovery and `HTTP` routing part of the product model.
- Interesting implementation choices:
  `src/appovrly.cc`
  shows the daemon and browser-host lifecycle,
  `resource/scene.js`
  exposes the in-page API surface, and the repo structure makes the
  `browser shell + daemon app`
  split very explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  older `CEF` host with a heavier browser stack than many future tools would
  want, but that is also what makes the daemon model so concrete.
- What to inspect next:
  keep it visible whenever a future branch needs
  `overlay host as a browser runtime platform` rather than a single tool.

## `ephemeral-laboratories/ComposeVR`

- GitHub:
  [ephemeral-laboratories/ComposeVR](https://github.com/ephemeral-laboratories/ComposeVR)
- What it is:
  an experimental `Compose Multiplatform` overlay framework that uses
  `Skia`, `LWJGL`, hidden `GLFW`, and `OpenVR` to render a declarative UI into
  a tracked overlay surface.
- Why it matters:
  it is the clearest donor in the repo for
  `modern declarative UI runtime -> OpenVR overlay` outside the browser stack.
- Interesting ideas:
  treat `OverlayState` as the UI-facing model for pose and visibility; let
  `Compose` own the UI tree while `OpenVR` remains a host boundary; preserve a
  more modern declarative mental model than the usual `Win32`, `Unity`, or
  `ImGui` path.
- Interesting implementation choices:
  `framework/src/jvmMain/kotlin/ComposeVR.kt`
  plus `OverlayState.kt`
  and `openvr/VROverlay.kt`
  make the
  `Compose scene -> Skia render surface -> OpenVR overlay wrapper`
  boundary explicit.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  clearly experimental and still a little cursed, so it is best treated as a
  method donor rather than a stable overlay platform.
- What to inspect next:
  keep it visible whenever a future branch needs
  `declarative Kotlin UI as overlay content`.

## Main takeaways from Wave 56

- `Browser-backed overlay runtimes` are clearer when split into:
  - `native backend plus web runtime`
  - `offscreen browser-window mirroring`
  - `browser host plus local daemon apps`
  - `non-browser declarative UI runtime experiments`
- The strongest lesson from this wave is that `overlay host` and `overlay app`
  do not need to be the same process.
- Another strong lesson is that the real reusable boundary often lives at
  `frame production plus local protocol`, not at a specific scene graph.

## Reusable methods clarified by this wave

- `Browser runtime overlay host with native backend, child app daemons, and local HTTP or IPC contracts`
- `Offscreen desktop UI runtime mirrored directly into an OpenVR texture stream`

## Recommended next moves after this wave

1. Treat `ovrsalt` and `ovrly` as the main architecture donors for future
   `overlay host platform` ideas.
2. Keep `electron-openvr` visible as the quickest lower-bound
   `browser window -> overlay texture` reference.
3. Keep `ComposeVR` visible whenever `VR-apps-lab` wants a more modern
   declarative UI runtime comparison instead of another immediate-mode sample.
