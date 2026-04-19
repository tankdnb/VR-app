# VR Projects Wave 15: Overlay-First Utility Hosts, HUD Micro-Overlays, and Scaffolds

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `overlay-first utility hosts`, `HUD micro-overlays`, `web or scene overlay
  scaffolds`, and `engine-side overlay integration`.

## Why this wave exists

The repository already had strong coverage of:

- runtime diagnostics and OpenXR switchers;
- tracker bridges, OSC exporters, and no-HMD workflows;
- accessibility overlays and classic desktop-in-VR products;
- driver tutorials, custom-device plumbing, and motion-compensation paths.

What was still missing was a denser layer of:

- `overlay hosts` that treat overlay lifecycle as the product core rather than
  one visual afterthought;
- `UI-stack reuse` where overlays are fed by `WinForms`, `WPF`, `browser`, or
  `ImGui` surfaces;
- `scene-overlay scaffolds` that treat Unity scene content as the overlay body;
- `micro-overlays` that solve one small comfort or workflow problem with very
  little code;
- `engine-side OpenXR overlay hooks` that reveal where overlay support enters a
  larger runtime or engine stack.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with focused family-level overlay queries;
2. deduplicate against the registry;
3. freeze a shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, overlap, and donor value;
6. promote findings into the registry, families, methods, backlog, and
   relevant reuse docs.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `KainosSoftwareLtd/VRSceneOverlay` | Clear Unity scene-overlay scaffold rather than a generic flat dashboard |
| `artumino/SteamVR_HUDCenter` | Useful C# overlay library with notification API and desktop-UI rasterization paths |
| `LapisGit/LapisOverlay` | Strong in-progress overlay host with both dashboard and wrist-watch surfaces |
| `elvissteinjr/SteamVR-PrimaryDesktopOverlay` | Excellent micro-tool reference for patching an existing SteamVR overlay instead of building a new host |
| `Martin-Oehler/SteamVR-WebApps` | Web-app-backed overlay shells that sit on top of `SteamVR-Webkit` |
| `hai-vr/h-view` | Rich overlay-first utility host with desktop parity, ImGui rendering, OSCQuery, and device-status tooling |
| `LunarG/OpenXR-Overlays-UE4-Plugin` | Tiny but useful Unreal-side hook into provisional OpenXR overlay support |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `Denwa/vive-wireless-info-overlay` | Valuable as a micro-overlay product reference, but the GitHub snapshot is source-light and does not yet support a full code-level donor pass |
| `vrkit-platform/vrkit-platform` | Large sim-racing platform with promising overlay and plugin-system signals, but it needs a narrower future pass because the current repo scope is much broader than this wave |

## Deep-pass notes by project

## `KainosSoftwareLtd/VRSceneOverlay`

- GitHub:
  [KainosSoftwareLtd/VRSceneOverlay](https://github.com/KainosSoftwareLtd/VRSceneOverlay)
- What it is:
  a Unity project that packages `scene-overlay` setups around tracked objects,
  Leap Motion hands, and simple environment augmentation rather than only flat
  dashboard panels.
- Why it matters:
  it is one of the clearest references in the repo for `scene as overlay
  scaffold`, which is a different design branch from `desktop texture on a
  quad`.
- Interesting ideas:
  treat the overlay as a small reusable scene; keep tracker or HMD helpers in
  regular Unity scripts; combine Leap hands, simple object toggles, and audio
  cues inside the same overlay scene.
- Interesting implementation choices:
  `Assets/Scripts/overlay.cs` wraps OpenVR overlay creation, texture
  submission, UV bounds, and tracked-device-relative transform updates;
  `EnforceTracker.cs` locates a Vive Tracker by render-model name;
  `CheckInput.cs` shows a tiny interaction hook; `MicTracker.cs` uses the local
  microphone as a scene-side animation trigger.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  it is an older Unity plus SteamVR plus Leap Motion stack; much of the value
  is in the scaffold and composition idea, not in modern runtime polish.
- What to inspect next:
  compare it with `OVROverlayManager`, `VROverlay`, and other Unity helpers as
  one `scene-overlay scaffold` subfamily.

## `artumino/SteamVR_HUDCenter`

- GitHub:
  [artumino/SteamVR_HUDCenter](https://github.com/artumino/SteamVR_HUDCenter)
- What it is:
  a C# overlay helper library for OpenVR that wraps overlay creation,
  notifications, dashboard widgets, and desktop-UI-backed overlays.
- Why it matters:
  it is one of the best public references in the repo for `existing desktop UI
  stack -> OpenVR overlay texture`, especially for `WinForms` and `WPF`
  surfaces.
- Interesting ideas:
  treat overlay objects as reusable `Handlable` instances; keep a singleton
  controller that owns lifecycle and event polling; expose a small
  developer-friendly notification API; let forms and controls render into a VR
  surface instead of rebuilding the UI in VR-native widgets.
- Interesting implementation choices:
  `HUDCenterController.cs` creates a background OpenVR polling loop;
  `Overlay.cs` cleanly distinguishes dashboard widgets from normal overlays;
  `FormOverlay.cs` translates overlay mouse input back into WinForms events and
  copies control bitmaps into an OpenGL texture; `VRUserControl.xaml.cs` shows
  a parallel WPF rasterization path through `RenderTargetBitmap`.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  older `.NET`, `OpenTK`, and WinForms/WPF assumptions make it more of a donor
  than a modern end-user product reference.
- What to inspect next:
  compare it directly with `SteamVR-WebApps` and `h-view` as one
  `desktop UI stack -> overlay texture and input bridge` family.

## `LapisGit/LapisOverlay`

- GitHub:
  [LapisGit/LapisOverlay](https://github.com/LapisGit/LapisOverlay)
- What it is:
  a work-in-progress open-source SteamVR overlay suite that already shows a
  useful split between a `dashboard overlay`, a `watch or wrist overlay`, and a
  thin external media sidecar.
- Why it matters:
  it is one of the clearest public references for `overlay-first utility host
  with multiple presentation surfaces` inside the current repo.
- Interesting ideas:
  keep one dashboard for larger interaction and a smaller watch overlay for
  quick glances; reuse Unity UI with overlay mouse translation; let media data
  come from a tiny sidecar executable that writes JSON instead of coupling media
  retrieval to the overlay host itself.
- Interesting implementation choices:
  `DashboardOverlay.cs` creates a dashboard overlay, sets mouse scale, feeds a
  render texture into OpenVR, and routes overlay click coordinates back through
  `GraphicRaycaster`;
  `WatchOverlay.cs` anchors a second overlay to a controller role with editable
  offsets and rotations;
  `MediaViewer.cs` launches `LapisOverlayMediaManager.exe`, watches a JSON log,
  and updates the UI from title, artist, and base64 thumbnail data.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  still visibly in progress, with several values configured directly in the
  Unity scene or inspector rather than in a mature runtime settings layer.
- What to inspect next:
  compare it directly with `h-view` as one `dashboard plus secondary surface`
  design branch and inspect whether the media-sidecar contract generalizes.

## `elvissteinjr/SteamVR-PrimaryDesktopOverlay`

- GitHub:
  [elvissteinjr/SteamVR-PrimaryDesktopOverlay](https://github.com/elvissteinjr/SteamVR-PrimaryDesktopOverlay)
- What it is:
  a tiny Windows utility that finds the existing Steam desktop overlay and crops
  it to the primary monitor by changing texture bounds.
- Why it matters:
  it proves a very different overlay pattern: `patch an existing runtime-owned
  overlay` instead of creating a new overlay host.
- Interesting ideas:
  calculate the primary monitor UV region from Windows virtual-desktop metrics;
  auto-register the app manifest on first run; set the utility to auto-launch
  with SteamVR; keep the whole product honest and single-purpose.
- Interesting implementation choices:
  `main.cpp` computes `VRTextureBounds_t` from `GetSystemMetrics`, waits up to
  a minute for `valve.steam.desktop` to appear, then calls
  `SetOverlayTextureBounds` on that existing overlay handle instead of building
  its own rendering stack.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  Windows-only, extremely narrow, and dependent on SteamVR's existing desktop
  overlay key plus external tools such as `OpenVR-AdvancedSettings` for
  comfortable placement and scale.
- What to inspect next:
  compare it with `DesktopPlus` and `OpenVRDesktopDisplayPortal` as one
  `patch existing desktop surface vs render a new desktop surface` study.

## `Martin-Oehler/SteamVR-WebApps`

- GitHub:
  [Martin-Oehler/SteamVR-WebApps](https://github.com/Martin-Oehler/SteamVR-WebApps)
- What it is:
  a collection of small dashboard apps built on `SteamVR-Webkit`, using
  `CefSharp` to wrap websites such as Spotify and WhatsApp into SteamVR
  dashboard overlays.
- Why it matters:
  it shows the thinnest possible `web app -> dashboard overlay` wrapper pattern
  once the underlying browser-backed overlay toolkit already exists.
- Interesting ideas:
  treat a web service as the UI and keep the host app very small; persist
  browser cookies to keep sessions alive; inject custom JavaScript after page
  load; register small JS objects such as notifications or metadata bridges.
- Interesting implementation choices:
  each app calls `SteamVR_WebKit.Init(...)`, creates a `WebKitOverlay` of type
  `Dashboard`, configures thumbnail and cache path, installs the SteamVR app
  manifest, then injects JavaScript through `ExecuteJavaScriptAsync(...)` after
  page load.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  much of the real implementation weight lives in `SteamVR-Webkit`; security
  and maintenance tradeoffs inherit the risks of embedding remote websites in
  a VR overlay.
- What to inspect next:
  compare it with `SteamVR_HUDCenter` and `h-view` as one family of
  `existing UI stack reused inside an overlay host`.

## `hai-vr/h-view`

- GitHub:
  [hai-vr/h-view](https://github.com/hai-vr/h-view)
- What it is:
  a broad utility application that can run as a desktop app and, when SteamVR
  is available, also create a dashboard overlay backed by `ImGui.NET` and
  `Veldrid`.
- Why it matters:
  it is the strongest overlay-host donor in this wave because it combines
  `desktop parity`, `overlay rendering`, `input translation`, `saved settings`,
  `hardware inventory`, `OSCQuery`, and even `eye-tracking-based overlay input`
  into one coherent host shell.
- Interesting ideas:
  one app can expose both desktop and VR surfaces; OpenVR support is optional
  at compile time; keep a windowless or hidden rendering path alive for the VR
  overlay; persist hardware layout and theme preferences in JSON; use eye
  tracking as another overlay pointer source.
- Interesting implementation choices:
  `HVImGuiOverlay.cs` creates either a dashboard or normal overlay, feeds it a
  DirectX texture pointer from `Veldrid`, polls overlay events into a dedicated
  input snapshot, and uses `ComputeOverlayIntersection` for eye-tracking-based
  pointer movement;
  `HVOpenVRManagement.cs` starts as a background OpenVR app, loads a custom
  action manifest, tracks predicted poses, and runs a synchronized overlay loop
  around `WaitFrameSync`;
  `SavedData.cs` gives the app a robust JSON plus backup persistence layer for
  hardware preferences and UI theme values.
- Code donor value:
  very high.
- Product reference value:
  very high.
- Architecture reference value:
  very high.
- Caveats:
  this repo is much broader than the overlay slice alone, so the overlay
  portion is now understood but the full project should still stay
  `Partially studied` until the rest of the app boundaries are mapped.
- What to inspect next:
  revisit the repo beyond its overlay slice to inspect `OSCQuery`, hardware
  inventory, OCR, and external-service boundaries in a future follow-up pass.

## `LunarG/OpenXR-Overlays-UE4-Plugin`

- GitHub:
  [LunarG/OpenXR-Overlays-UE4-Plugin](https://github.com/LunarG/OpenXR-Overlays-UE4-Plugin)
- What it is:
  a very small Unreal Engine 4 plugin that enables provisional `XR_EXTX_overlay`
  support through the engine's OpenXR extension-plugin path.
- Why it matters:
  even though it is tiny, it is a clear engine-side reference for where overlay
  support enters an `OpenXR host` before there is a larger end-user product.
- Interesting ideas:
  enumerate available instance extensions first; opt in only when the overlay
  extension is present; inject `XrSessionCreateInfoOverlayEXTX` into the
  session-create chain; keep the implementation almost entirely inside the
  engine-extension boundary.
- Interesting implementation choices:
  `EXTXOverlays.cpp` registers an `IOpenXRExtensionPlugin`, checks for the
  extension name, and returns a minimal `XrSessionCreateInfoOverlayEXTX` in
  `OnCreateSession(...)`;
  the header file explicitly documents remaining limitations such as blend-mode
  handling, projection-layer properties, and a more explicit D3D11 check.
- Code donor value:
  medium.
- Product reference value:
  low-medium.
- Architecture reference value:
  medium-high.
- Caveats:
  Unreal-specific, very small in scope, and built around a provisional OpenXR
  extension that is not a strong shipping baseline.
- What to inspect next:
  compare it with `OpenXR-OverlayLayer`, `PlutoVR/OpenXR-OverlayLayer-1`, and
  `vrkit-platform` as one `OpenXR overlay host and integration boundary` family.

## Cross-project synthesis

## Strongest donor patterns from this wave

### 1. `existing UI stack -> overlay texture and input bridge`

This is the clearest reusable pattern across the wave:

- `SteamVR_HUDCenter` does it with `WinForms` and `WPF`;
- `SteamVR-WebApps` does it with a browser and injected JavaScript;
- `h-view` does it with `ImGui.NET` and `Veldrid`.

This matters because `VR-apps-lab` does not have to choose between
`desktop-quality UI tooling` and `VR overlay delivery`. The bridge itself is
often the real reusable unit.

### 2. `overlay-first host with multiple presentation surfaces`

`LapisOverlay` and `h-view` both show that a useful utility host can expose:

- one larger dashboard surface;
- one smaller quick-glance or always-on surface;
- one desktop fallback or companion view.

This is stronger evidence for a future `overlay utility suite shell` than a
single full-screen desktop mirror.

### 3. `overlay patch micro-tool`

`SteamVR-PrimaryDesktopOverlay` shows a distinct product branch:

- do not build a new overlay renderer;
- find the runtime-owned overlay that already exists;
- patch its bounds or behavior;
- keep the tool tiny and honest.

This is exactly the sort of narrow helper that can still be valuable in
`VR-apps-lab`.

### 4. `scene-overlay scaffold`

`VRSceneOverlay` reminds the repo that not every overlay must begin as a flat
panel. Unity scene content, tracker helpers, and sensor add-ons can be treated
as a reusable overlay scaffold in their own right.

## Product directions reinforced by this wave

This wave strongly reinforces four future product branches inside
`VR-apps-lab`:

1. `overlay utility host` with desktop parity and multiple VR surfaces;
2. `UI-to-overlay bridge` for browser, forms, or immediate-mode UI stacks;
3. `micro-overlay patches` that solve one problem with almost no host overhead;
4. `scene-overlay experiments` for more embodied or tracker-aware utility
   concepts.

## What this wave changes in the repository

After this wave:

- the repo has better coverage of `overlay host architecture`, not only of
  finished overlay products;
- `HUDCenter`, `SteamVR-WebApps`, `PrimaryDesktopOverlay`, `VRSceneOverlay`,
  and `LunarG/OpenXR-Overlays-UE4-Plugin` are no longer vague backlog nodes;
- `h-view` is now recognized as a strong overlay donor and a justified reuse
  candidate;
- the remaining honest follow-ups are mostly `source-light` or
  `too-large-for-this-wave` nodes, not missing obvious overlay donors.
