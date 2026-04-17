# VR Projects Wave 7: Depth Pass for Under-Documented Repos

- Date: `2026-04-11`
- Goal: identify the projects in `VR.app` that still had relatively light
  coverage, download them, inspect their current repository state, and add
  deeper notes that are useful for future implementation work.

## Why this pass was needed

The repository already had a large amount of VR utility research, but not every
project had the same information density.

The main gaps were:

- some early `overlay/helper` projects were only covered at first-pass level;
- some repositories had changed since the first sweep;
- some projects turned out to have more valuable architectural clues than their
  short README summaries suggested;
- at least one project, `openvr-metrics`, had a much richer public repository
  than what was available during the original pass.

## Coverage audit summary

After reviewing the current docs, the weakest-covered cluster was:

1. `glenimp617/DesktopXR`
2. `Hotrian/OpenVRDesktopDisplayPortal`
3. `benotter/OVRLay`
4. `OVRTools/WhereIsForward`
5. `OVRTools/OpenVRDeviceBattery`
6. `SDraw/openvr_widgets`
7. `CrispyPin/ovr-utils`
8. `r57zone/OpenVR-OpenTrack`
9. `zhangxuelei86/WMR-Passthrough`
10. `ethanporcaro/tracking-toolkit`
11. `Nyabsi/openvr-metrics`

These were selected because they had one or more of the following issues:

- only brief coverage in the original landscape;
- limited earlier source access;
- useful implementation details hidden in the repository structure;
- older or niche projects that still contain strong reusable patterns.

## Project-by-project deepening

### 1. `glenimp617/DesktopXR`

- Previous coverage weakness:
  we had the product idea, but not the practical repository limitation.
- What the repo actually shows now:
  the GitHub repository is almost entirely `documentation + images + notices`.
  There is no visible application source in the public repo snapshot we pulled.
- Interesting solutions and signals:
  the project is intentionally packaged like a product, not a source-first
  toolkit. The repo emphasizes `MSI installer`, `automatic layer
  registration`, `DX11/DX12 support`, and a lightweight `OpenXR API layer`
  positioning.
- Why that matters for `VR.app`:
  it is a useful reference for `distribution model`, `installer-driven OpenXR
  layer registration`, and a minimal user-facing pitch for an XR utility.
- Reuse value:
  product packaging strategy and positioning for a future `OpenXR utility`
  module.
- Caveat:
  still low as a direct code donor because the public repo is effectively
  binary/documentation-first.
- Sources:
  [repo](https://github.com/glenimp617/DesktopXR)

### 2. `Hotrian/OpenVRDesktopDisplayPortal`

- Previous coverage weakness:
  we knew it was an older desktop overlay, but not how feature-rich its model
  actually was.
- New findings from the repo:
  the project is a Unity app with a strong desktop-side utility framing and a
  surprisingly complete interaction model.
- Interesting solutions:
  `world`, `screen/HUD`, and `controller` attachment modes; click/scroll input
  passthrough; move/rotate/scale from VR; configurable capture FPS; crop
  region; outline styling; animated behavior when looked at; haptics; and
  save/load overlay profiles.
- Why that matters:
  this is one of the clearest early references for the exact class of product
  we were originally exploring: `small but configurable utility overlays`.
- Reuse value:
  attachment model, profile thinking, interaction model, controller-first
  window manipulation, and the distinction between `desktop capture settings`
  and `overlay settings`.
- Caveat:
  old capture approach was `GDI`-bound and the repo is effectively legacy,
  superseded by `OVRdrop`.
- Sources:
  [repo](https://github.com/Hotrian/OpenVRDesktopDisplayPortal)

### 3. `benotter/OVRLay`

- Previous coverage weakness:
  it was listed mainly as a Unity overlay toolkit, but not as a structured
  prefab-based development kit.
- New findings from the repo tree:
  the code is clearly split into `Unity_Overlay`, `Unity_SteamVR_Handler`, and
  internal `OpenVR` abstractions for handler, overlay, pose, events, getters,
  and mouse interaction.
- Interesting solutions:
  drag-and-drop prefab bootstrap; own OpenVR connection handling instead of
  depending on the SteamVR Unity plugin; wrapper classes around overlay
  handles/settings; Unity UI interaction via simulated mouse coordinates; and
  render-model support from OBJ assets.
- Why that matters:
  this is a strong reference for `rapid Unity overlay prototyping` and for how
  to isolate `overlay primitives` from the higher-level scene.
- Reuse value:
  prefab-based overlay bootstrap, OpenVR wrapper abstraction, event routing,
  and Unity UI bridge patterns.
- Caveat:
  older Unity-era code and not suited as a modern foundation without cleanup.
- Sources:
  [repo](https://github.com/benotter/OVRLay)

### 4. `OVRTools/WhereIsForward`

- Previous coverage weakness:
  we treated it as a tiny novelty overlay, but its simplicity is exactly the
  point and is architecturally useful.
- New findings from the code:
  it is an extremely small `.NET 5` app built on `OVRSharp`, with a manifest
  registration flow, a utility-app bootstrap, and a single texture-based floor
  overlay.
- Interesting solutions:
  `--register` and `--deregister` flows for manifest management; no heavy UI;
  utility app lifecycle kept minimal; resource file packaging; one image
  texture; one transform; one purpose.
- Why that matters:
  it is an almost ideal reference for `micro-utilities` that do one clear thing
  and stay out of the way.
- Reuse value:
  overlay micro-tool pattern, manifest registration UX, and minimal OpenVR app
  architecture.
- Caveat:
  very intentionally tiny; not a framework donor.
- Sources:
  [repo](https://github.com/OVRTools/WhereIsForward)

### 5. `OVRTools/OpenVRDeviceBattery`

- Previous coverage weakness:
  it was described as a battery helper, but not as a nice example of a
  background desktop utility.
- New findings from the code:
  this is a `WinForms` tray app running as `VRApplication_Background`, polling
  tracked devices every second and exposing contextual details via a right/left
  click tray menu and per-device info forms.
- Interesting solutions:
  taskbar-only UX; lightweight polling; grouping devices by tracked-device
  class; human-readable role naming; click-through to a detail form; and
  explicit support for devices that do not provide battery state.
- Why that matters:
  this is one of the clearest examples of a `desktop-side companion utility`
  that complements VR usage without needing an in-headset UI.
- Reuse value:
  tray-agent architecture, periodic OpenVR polling, device grouping UX, and
  background-service-first utility design.
- Caveat:
  explicitly rough UX and legacy `.NET Framework 4.7.2` app style.
- Sources:
  [repo](https://github.com/OVRTools/OpenVRDeviceBattery)

### 6. `SDraw/openvr_widgets`

- Previous coverage weakness:
  we knew it had widgets, but not how structured the implementation was.
- New findings from the repo:
  it is a real `widget suite`, not a demo. The repo has explicit `Core`,
  `Gui`, `Managers`, `Widgets`, `Utils`, and `vendor` layers.
- Interesting solutions:
  `WidgetManager` and `ConfigManager`; separate widget classes for `stats`,
  `window capture`, and `keyboard`; `WindowCapturer`; `VRDashOverlay` plus
  general `VROverlay`; XML-configured settings; and controller-driven widget
  activation patterns.
- Why that matters:
  it is one of the strongest public references for treating VR utilities as a
  `family of reusable widgets` rather than a single overlay application.
- Reuse value:
  widget-suite architecture, dashboard + floating-overlay split, control
  affordances, and settings-driven widget registration.
- Caveat:
  some capture/input paths are old and platform-specific, especially for Linux.
- Sources:
  [repo](https://github.com/SDraw/openvr_widgets)

### 7. `CrispyPin/ovr-utils`

- Previous coverage weakness:
  the repo was effectively a placeholder when we revisited it.
- New findings from GitHub:
  the GitHub repository currently contains almost no source and simply points to
  a new home on `Codeberg`.
- Interesting solutions:
  from the GitHub snapshot alone, there is no current implementation detail to
  mine.
- Why that matters:
  this is a good reminder that `repository mobility` matters in long-lived
  research indexes, and GitHub mirrors can become stale.
- Reuse value:
  none from the current GitHub snapshot beyond tracking the migration.
- Caveat:
  this project remains under-documented inside `VR.app` unless we decide to
  explicitly follow the non-GitHub upstream later.
- Sources:
  [repo](https://github.com/CrispyPin/ovr-utils)

### 8. `r57zone/OpenVR-OpenTrack`

- Previous coverage weakness:
  it was noted as a DIY tracking bridge, but not as a configurable `headset
  emulation` path.
- New findings from the repo:
  this is not just a tracker helper; it is a bridge for DIY VR based on
  `OpenTrack`, with separate `FreeTrack` and `UDP` driver variants and a
  configuration model that covers headset optics and display layout.
- Interesting solutions:
  external tracking source -> OpenVR HMD bridge; explicit config for `FOV`,
  `IPD`, distortion coefficients, render size, window placement, refresh rate,
  crouch communication, and multi-monitor placement.
- Why that matters:
  it shows how a VR utility can be both a `tracking bridge` and a
  `headset-parameter tool`, which is a richer pattern than a plain input proxy.
- Reuse value:
  config schema ideas, DIY hardware bridge patterns, and external
  tracker-to-OpenVR translation.
- Caveat:
  niche and strongly tied to DIY headset workflows.
- Sources:
  [repo](https://github.com/r57zone/OpenVR-OpenTrack)

### 9. `zhangxuelei86/WMR-Passthrough`

- Previous coverage weakness:
  we had the high-level idea, but not the implementation shape.
- New findings from the repo:
  this is a serious `OpenXR API layer` project with a framework/dispatch
  generator, PowerShell install scripts, an external camera client wrapper, and
  `D3D11/D3D12` graphics-resource handling.
- Interesting solutions:
  insertion of an `alpha-blend` passthrough layer behind the app; explicit
  `XRmonitors` service dependency; generated dispatch framework; camera-client
  wrapper process boundary; view-space reference handling; and shared rendering
  code for imported camera textures.
- Why that matters:
  this is one of the strongest references for `API layer + external camera
  service` architecture, which is directly relevant to any future XR
  passthrough or compositing experiments.
- Reuse value:
  OpenXR layer framework patterns, external-service dependency model, generated
  dispatch approach, and graphics interop design.
- Caveat:
  experimental, WMR-specific, and dependent on another project for camera
  access.
- Sources:
  [repo](https://github.com/zhangxuelei86/WMR-Passthrough)

### 10. `ethanporcaro/tracking-toolkit`

- Previous coverage weakness:
  we mostly treated it as a general tracking tool, but the repository reveals a
  much stronger creator-tool pattern.
- New findings from the repo:
  this is a Blender extension with clear separation between UI, preferences,
  operators, and `xr_core`, including direct OpenXR session setup, headless
  compatibility handling, and tracker recording into NLA actions with timecode.
- Interesting solutions:
  `OpenXR in Blender` as a capture backend; headless OpenXR compatibility mode
  for Blender's OpenGL constraints; runtime-name reporting; action-space
  creation for controllers and Vive trackers; recording with interpolation; and
  offset/reference objects separate from raw tracking objects.
- Why that matters:
  this is a great reference for `creator-facing VR tools`, `data logging`, and
  `record-first` workflows rather than just overlays.
- Reuse value:
  diagnostics/recording UI patterns, tracker abstraction, runtime capability
  checks, and creator-tool architecture.
- Caveat:
  it is a Blender extension, so only part of the design transfers directly to
  standalone utilities.
- Sources:
  [repo](https://github.com/ethanporcaro/tracking-toolkit)

### 11. `Nyabsi/openvr-metrics`

- Previous coverage weakness:
  the original note in `VR.app` relied on store metadata because repo access was
  unreliable at that time.
- New findings from the current repo:
  the project is fully inspectable and significantly richer than the earlier
  summary suggested. It uses `CMake`, `Vulkan`, `SDL3`, `ImGui`, `ImPlot`, and
  a clear overlay split between `controller` and `dashboard` overlays.
- Interesting solutions:
  per-process metrics; explicit `ControllerOverlay` and `DashboardOverlay`;
  auto-launch registration with SteamVR; device monitoring hooks driven by
  `VREvent`s; background update loop timed to HMD refresh rate; in-overlay
  SteamVR resolution changes; device battery monitoring; and display color
  adjustment controls.
- Why that matters:
  this is now one of the strongest references in the repo for a polished
  `metrics + control overlay` product.
- Reuse value:
  dual-overlay architecture, background event loop, renderer split, monitoring
  model, and metrics-oriented UI composition.
- Caveat:
  licensed under `Source First License 1.1`, so treat it carefully as a code
  donor.
- Sources:
  [repo](https://github.com/Nyabsi/openvr-metrics)

## Most useful new patterns from this depth pass

### 1. Micro-utilities are worth building

Projects like `WhereIsForward` and `OpenVRDeviceBattery` are reminders that a
VR tool can be very small and still be worth shipping.

### 2. Desktop-side companions matter as much as in-headset UI

`OpenVRDeviceBattery`, `DesktopXR`, and `OpenVRDesktopDisplayPortal` all show
that some of the most useful VR tools are really `Windows helpers with VR
awareness`.

### 3. Widget suites are a distinct architecture

`openvr_widgets` and `openvr-metrics` both point toward a model where the
product is not a single overlay but a `container for multiple utility views`.

### 4. External services plus API layers are a real pattern

`WMR-Passthrough` shows a strong architecture pattern:

- runtime API layer
- separate camera/service dependency
- explicit install/uninstall tooling
- rendering/interception layer in the middle

### 5. VR creator tools deserve their own track

`tracking-toolkit` shows that there is a serious opportunity in `recording`,
`inspection`, `export`, and `creator-facing XR utilities`, not just overlays
for headset users.

## Best backlog updates for `VR.app`

Based on this pass, these additions are now better justified:

1. `VR micro-utilities`
   inspired by `WhereIsForward` and `OpenVRDeviceBattery`.
2. `Widget container / utility suite shell`
   inspired by `openvr_widgets` and `openvr-metrics`.
3. `Desktop companion + background agent`
   inspired by `DesktopXR`, `OpenVRDeviceBattery`, and `OpenVRDesktopDisplayPortal`.
4. `API layer + external service experiments`
   inspired by `WMR-Passthrough`.
5. `Creator tools / recording branch`
   inspired by `tracking-toolkit`.

## Bottom line

This pass confirmed that the weakest-covered projects in `VR.app` were not
unimportant projects. In several cases, they were some of the best references
for:

- micro-utility scope discipline
- desktop-side companion apps
- widget-container architecture
- API-layer plus service design
- creator-oriented XR tooling

That makes them worth keeping visible in the repository, not just as names in
an index, but as actionable references for future implementation work.
