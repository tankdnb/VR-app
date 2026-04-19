# VR Projects Wave 17: OpenXR Runtime Managers, Layers, and Service Hosts

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `runtime managers`, `experimental OpenXR API layers`, and
  `runtime-side service hosts`.

## Why this wave exists

The repository already had strong coverage of:

- mainstream runtime switchers and diagnostics tools;
- overlay hosts and dashboard surfaces;
- tracker bridges and no-HMD workflows;
- synthetic devices and vision-side tracking experiments.

What still needed a clearer architecture map was the zone between:

- `registry-based runtime switching`;
- `API-layer injection`;
- `remote overlay sessions over a layer`;
- `runtime-side service hosts` that combine registration, UI, and protocol
  adaptation.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with runtime-manager and API-layer family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, overlap, and donor value;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `PlutoVR/OpenXR-OverlayLayer-1` | Important remote-overlay experiment that makes the layer/client split explicit |
| `Ybalrid/OpenXR-Runtime-Manager` | Useful smaller runtime-manager reference with explicit registry and probe logic |
| `pembem22/etvr-openxr-layer` | Unusual API-layer path that adapts eye-tracking OSC data into OpenXR gaze surfaces |
| `clear-xr/clearxr-server` | Broader platform whose runtime registration, OpenXR layer, and service split deserved classification |

## Secondary candidate surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `vrkit-platform/vrkit-platform` | The current public snapshot looked too broad and domain-shifted to treat as a clean OpenXR utility donor in this wave |

## Deep-pass notes by project

## `PlutoVR/OpenXR-OverlayLayer-1`

- GitHub:
  [PlutoVR/OpenXR-OverlayLayer-1](https://github.com/PlutoVR/OpenXR-OverlayLayer-1)
- What it is:
  an experimental implementation of `XR_EXTX_overlay` split into an OpenXR API
  layer and a separate remote overlay application.
- Why it matters:
  it is one of the clearest public references for `overlay session inside an
  unaware host app` rather than a classic companion overlay model.
- Interesting ideas:
  keep the overlay client out of process; let the API layer own the OpenXR
  interception; communicate over shared-memory RPC; support a single overlay
  session layered over a host OpenXR app.
- Interesting implementation choices:
  `overlay_remote.cpp` builds the remote client, creates D3D11 textures, and
  drives the overlay-side OpenXR session;
  the layer side exposes manifest and loader integration under
  `XR_overlay_ext/`;
  the README is unusually honest about missing RPC families such as actions,
  D3D12, OpenGL, Vulkan, haptics, and debug-utils support.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  experimental, older, and tightly constrained; the value is architectural, not
  production readiness.
- What to inspect next:
  compare it directly with `LunarG/OpenXR-OverlayLayer` as one
  `remote overlay via API layer` lineage.

## `Ybalrid/OpenXR-Runtime-Manager`

- GitHub:
  [Ybalrid/OpenXR-Runtime-Manager](https://github.com/Ybalrid/OpenXR-Runtime-Manager)
- What it is:
  a small Windows WPF utility that shows the active OpenXR runtime and lets the
  user select another known runtime.
- Why it matters:
  it is a good comparison node against larger runtime switchers because it
  explicitly combines `registry enumeration` with `well-known manifest probes`
  and optional SteamVR path discovery through OpenVR.
- Interesting ideas:
  treat the registry as authoritative when possible, but supplement it with
  known manifest paths; probe SteamVR through `OpenVRInterop.GetRuntimePath`;
  keep the UI surface extremely small and purpose-built.
- Interesting implementation choices:
  `RuntimeManager.cs` reads `ActiveRuntime`, scans `AvailableRuntimes`,
  deserializes runtime manifests, probes SteamVR through OpenVR, and falls back
  to default paths when needed;
  `MainWindow.xaml.cs` is intentionally thin and delegates discovery and
  switching logic to the manager layer.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  Windows-only, admin-dependent, and narrower than `openxr-explorer`.
- What to inspect next:
  compare it with `xr-picker`, `openxr-explorer`, and other switchers as one
  `registry-plus-probe runtime switcher` family.

## `pembem22/etvr-openxr-layer`

- GitHub:
  [pembem22/etvr-openxr-layer](https://github.com/pembem22/etvr-openxr-layer)
- What it is:
  a Rust-based Android OpenXR API layer intended to be patched into a Steam Link
  APK and used with a loader that supports implicit API layers.
- Why it matters:
  it shows a rare `protocol adapter layer` pattern where foreign eye-tracking
  data is transformed into an OpenXR-facing capability rather than routed
  through a desktop sidecar or a SteamVR driver.
- Interesting ideas:
  advertise `XR_EXT_eye_gaze_interaction`; keep the layer small; ingest
  `EyeTrackVR`-style data over UDP OSC; translate that data into OpenXR spaces
  and view-level outputs.
- Interesting implementation choices:
  `lib.rs` implements `xrNegotiateLoaderApiLayerInterface`;
  `layer.rs` tracks extension exposure, action spaces, and view interception;
  `server.rs` binds UDP port `9000`, parses OSC packets such as
  `/tracking/eye/LeftRightPitchYaw`, and stores converted gaze vectors.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  niche, Android-specific, and dependent on patched loader behavior.
- What to inspect next:
  compare it with `OpenXR-Layer-Template` and eye-tracker integration repos as
  one `foreign service -> OpenXR extension surface` branch.

## `clear-xr/clearxr-server`

- GitHub:
  [clear-xr/clearxr-server](https://github.com/clear-xr/clearxr-server)
- What it is:
  a broader streaming platform organized around a desktop server app, an OpenXR
  app, and an OpenXR API layer.
- Why it matters:
  even though it is not a narrow utility repo, it clarifies how a larger
  runtime-side product can split `service host`, `OpenXR layer`, and
  `registration helper` responsibilities.
- Interesting ideas:
  keep privileged registration in elevated helper modes;
  use a Tauri shell for the main server UI;
  stage vendor files locally rather than redistributing them in source;
  maintain a dedicated API layer for controller or input fixes separate from
  the main streamer shell.
- Interesting implementation choices:
  `clearxr-streamer/src/lib.rs` exposes elevated registration and deregistration
  helper modes plus many Tauri commands for runtime and session state;
  `clearxr-layer/src/lib.rs` intercepts OpenXR action-state and haptic paths to
  patch CloudXR controller behavior;
  `clearxr-space/src/main.rs` provides a simple OpenXR landing space app;
  the vendor reconstruction script assembles CloudXR dependencies locally.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  this is a large platform with streaming and vendor constraints, so the
  runtime-side slice is stronger than the overall repo as a direct donor.
- What to inspect next:
  narrow future work to `registration`, `layer`, and `service host` boundaries
  rather than trying to absorb the whole platform at once.

## `vrkit-platform/vrkit-platform`

- GitHub:
  [vrkit-platform/vrkit-platform](https://github.com/vrkit-platform/vrkit-platform)
- What it is:
  currently a follow-up node whose public snapshot did not line up cleanly with
  the OpenXR utility angle expected from earlier references.
- Why it matters:
  it is a reminder to keep wave scope honest instead of forcing a large or
  mismatched repo into the wrong family just because the name sounds relevant.
- Code donor value:
  unknown.
- Product reference value:
  low-medium.
- Architecture reference value:
  unknown.
- Caveats:
  current snapshot needs a separate verification pass before it should be
  promoted further.
- What to inspect next:
  confirm whether the repo once again exposes meaningful OpenXR monitor,
  overlay, or plugin-platform surfaces.

## Main takeaways from Wave 17

- `OpenXR runtime-side tooling` is not one flat family.
- The most useful split is:
  - `registry-plus-probe runtime switcher`
  - `remote overlay session via API layer`
  - `protocol-adapter API layer`
  - `runtime-side service host with registration helpers`
- Larger platforms such as `clearxr-server` are still useful if the studied
  slice is kept explicit.

## Reusable methods clarified by this wave

- `Remote overlay session via API layer plus out-of-process client`
- `Registry-plus-probe runtime switcher`
- `Protocol-adapter OpenXR layer for foreign sensor data`

## Recommended next moves after this wave

1. Compare `OpenXR-OverlayLayer-1` with the LunarG overlay-layer line as one
   architecture branch.
2. Revisit `clearxr-server` only with a narrow runtime-registration and layer
   scope.
3. Leave `vrkit-platform` as a follow-up node until the public snapshot is
   clearly aligned again.
