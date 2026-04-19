# Foundational Waves 1-7 Retro Normalization

- Date: `2026-04-19`
- Goal: re-audit the foundational `VR-apps-lab` research corpus and supplement
  the early `waves 1-7` with a canonical repeat deep-pass in the same style now
  used by Waves `8-13`.

## Why this pass exists

The foundational research corpus already contained many of the right repos, but
it predated the repository's current `wave standard`.

That meant:

- the earliest broad pass lived inside `vr-utilities-repo-landscape.md` instead
  of a formal wave document;
- Waves `3-7` mixed discovery, gap-fill, and depth-pass work without one common
  structure;
- several high-value repos were still present only through older notes that did
  not match the level of `interesting idea`, `code donor value`, and
  `what to inspect next` used by Waves `12-13`;
- a few statuses needed correction because the repo had grown more disciplined
  than the original notes.

This document does not replace the early-wave history.

Instead, it acts as the canonical `retro-normalization pass` that tells a new
session:

- what the foundational waves really contributed;
- which early repos are now covered well enough;
- which ones are variants rather than separate mainline study targets;
- which foundational follow-ups still remain open.

## Better workflow used in this retro pass

This normalization pass reused the post-restructure workflow, even though the
source material came from older waves:

1. audit the foundational corpus against the current registry and family map;
2. freeze a shortlist of under-normalized old-wave repos;
3. sync current source into `.research-sources/github/`;
4. perform a repeat code-level pass;
5. correct statuses and family placement in canonical docs.

## Audit of the foundational corpus

### `vr-utilities-repo-landscape.md`

- Role in the repo:
  the effective `wave 1-2` foundation, even though it was stored as one broad
  landscape document.
- What it did well:
  established the first donor map for overlays, runtime layers, performance
  mods, calibration, passthrough, and official SDK anchors.
- What was missing by current standards:
  no frozen shortlist, no explicit backlog, and uneven distinction between
  `code donor`, `architecture reference`, and `product reference`.

### `vr-projects-wave-3-utilities.md`

- Role in the repo:
  expanded the corpus into runtime managers, remote-control overlays,
  accessibility tools, lighthouse automation, and utility suites.
- What held up:
  family discovery was directionally strong.
- What still needed normalization:
  `VnotifieR` and `OVROverlayManager` were useful enough to deserve a proper
  code-level re-pass and clearer family notes.

### `vr-projects-wave-4-gap-fill.md`

- Role in the repo:
  filled missing runtime switchers, device inventory tools, lighthouse helpers,
  and continuous-calibration variants.
- What held up:
  the gap-fill logic was good and still maps well to the current registry.
- What still needed normalization:
  `steamvr-exconfig` was strategically stronger than its old note implied.

### `vr-projects-wave-5-osc-tracking-tools.md`

- Role in the repo:
  made the `OSC`, `marker overlays`, `marker tracking`, and `room-state
  helpers` branches much more visible.
- What held up:
  the family discovery remains correct.
- What still needed normalization:
  `VirtualMotionTracker` had outgrown its earlier note and deserved promotion
  to a first-class `tracker platform` reference.

### `vr-projects-wave-6-driver-bridges.md`

- Role in the repo:
  early driver-heavy wave around vendor enhancement, tracker bridges, custom
  hardware, and narrow desktop helpers.
- What held up:
  it surfaced exactly the right architecture zone.
- What still needed normalization:
  this was the richest under-normalized wave, especially around
  `PSVR2Toolkit`, the WebSocket tracker-driver line, `VRBattery`,
  `EyeTrackVR` calibration, and `steamvr-exconfig`.

### `vr-projects-wave-7-depth-pass.md`

- Role in the repo:
  the first explicit attempt to deepen weak early entries.
- What held up:
  it correctly identified the weakest-covered overlay/helper cluster.
- What still needed normalization:
  it still predated the newer `wave 12-13` structure, so several useful repos
  lacked a clean `what to inspect next` and status correction pass.

## Repositories re-studied in this normalization pass

| Project | Why it entered the shortlist |
|---|---|
| `BnuuySolutions/PSVR2Toolkit` | Highest-value early vendor-enhancement repo still marked too loosely |
| `MuffinTastic/steamvr-exconfig` | Narrow but strong SteamVR hygiene micro-tool deserving a cleaner donor note |
| `zeroae/VRBattery` | Compact overlay-first battery utility that was still under-described |
| `John-Dean/OpenVR-Tracker-Websocket-Driver` | Mainline WebSocket tracker-service driver from the early bridge wave |
| `surplex-io/OpenVR-Driver` | Variant of the same WebSocket driver family that needed comparison, not duplicate treatment |
| `gpsnmeajp/VirtualMotionTracker` | One of the strongest old-wave tracker platforms and a central OSC donor |
| `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay` | Clear calibration-overlay node that deserved a real implementation note |
| `WiiPlayer2/VnotifieR` | Server-driven notification overlay that belonged in the canonical remote-control family |
| `BenWoodford/OVROverlayManager` | Tiny but useful Unity overlay toolkit/helper that was under-placed in the old corpus |
| `mittorn/ovr-utils-dashboard` | Overlay-shell variant that helps explain the gap between toolkit and utility suite |

## Deep-pass notes by project

## `BnuuySolutions/PSVR2Toolkit`

- GitHub:
  [BnuuySolutions/PSVR2Toolkit](https://github.com/BnuuySolutions/PSVR2Toolkit)
- What it is:
  an unofficial enhancement layer over the official `PlayStation VR2` PC
  driver/app that exposes extra headset and controller capabilities.
- Why it matters:
  it is still the strongest foundational-wave reference for `vendor stack
  augmentation` instead of full runtime replacement.
- Interesting ideas:
  keep the official vendor driver in place as `driver_playstation_vr2_orig.dll`,
  then wrap it with a patched loader; expose gaze and trigger-effect features
  through a versioned IPC surface instead of burying everything inside one DLL.
- Interesting implementation choices:
  `HmdDriverLoader` explicitly loads the original vendor DLL next to the
  replacement; `CaesarManagerHooks` inject gaze-related behavior by patching
  offsets inside the vendor module; `IpcServer` and `PSVR2Toolkit.IPC` share a
  versioned command protocol for handshakes, gaze polling, and trigger-effect
  requests; `TriggerEffectManager` maps IPC commands onto
  `scePadSetTriggerEffect`.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  depends on reverse-engineered vendor internals, a changing official driver,
  and non-commercial licensing constraints; some functionality remains
  intentionally closed or update-fragile.
- What to inspect next:
  how resilient the hook offsets are across vendor updates, what the actual
  external developer API usage looks like, and where the closed-source boundary
  begins in practice.

## `MuffinTastic/steamvr-exconfig`

- GitHub:
  [MuffinTastic/steamvr-exconfig](https://github.com/MuffinTastic/steamvr-exconfig)
- What it is:
  a small Windows configurator for disabling SteamVR drivers and autolaunch
  apps before starting a session.
- Why it matters:
  it is one of the cleanest foundational references for a `SteamVR hygiene
  micro-tool` that saves startup time without trying to become a full doctor
  suite.
- Interesting ideas:
  operate directly on `openvrpaths.vrpath`, `.vrappconfig`, and
  `steamvr.vrsettings`; separate `autolaunch app` toggles from `always-activate
  driver` toggles; create a backup only where the tool actually mutates
  SteamVR's config.
- Interesting implementation choices:
  `OpenVRPaths` resolves the OpenVR registry file from
  `%LocalAppData%\\openvr\\openvrpaths.vrpath`; `VRAppSetting` enumerates and
  rewrites `.vrappconfig` files; `SteamVRConfig` rewrites only the
  `driver_*` entries in `steamvr.vrsettings` while preserving a
  `.excfg.bkp` backup; the WinForms UI is generated from generic `IVRSetting`
  instances rather than hardcoded per-driver controls.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  narrowly scoped, Windows-only, and intentionally pre-launch oriented; it does
  not attempt live runtime inspection.
- What to inspect next:
  whether the same model should grow into a broader preflight/repair utility,
  or stay intentionally tiny as a focused `SteamVR environment helper`.

## `zeroae/VRBattery`

- GitHub:
  [zeroae/VRBattery](https://github.com/zeroae/VRBattery)
- What it is:
  a very small `Qt` overlay that surfaces SteamVR battery state in-headset.
- Why it matters:
  it remains one of the best early references for `micro-utility overlay`
  thinking: one job, one surface, minimal product sprawl.
- Interesting ideas:
  battery-only overlay UX; no attempt to become a full device suite; use a
  regular UI toolkit widget and render it into OpenVR instead of building a
  custom in-headset renderer.
- Interesting implementation choices:
  `main.cpp` boots a `BatteryInfoWidget` and hands it to a singleton
  `COpenVROverlayController`; `openvroverlaycontroller.cpp` creates a dashboard
  overlay, renders the widget into an offscreen OpenGL FBO, and pumps overlay
  mouse events on a timer; the overlay path is effectively a `Qt widget ->
  offscreen scene -> OpenVR texture` bridge.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  small, old, and intentionally limited; donor value comes more from shape than
  from modern framework quality.
- What to inspect next:
  whether the same offscreen-widget pattern is worth keeping as a lightweight
  fallback for ultra-small tools, or whether `VR-apps-lab` should prefer a more
  modern native overlay host for similar utilities.

## `John-Dean/OpenVR-Tracker-Websocket-Driver`

- GitHub:
  [John-Dean/OpenVR-Tracker-Websocket-Driver](https://github.com/John-Dean/OpenVR-Tracker-Websocket-Driver)
- What it is:
  an OpenVR driver that hosts a local `WebSocket` service for spawning and
  updating trackers while also echoing active VR device poses back to the
  client.
- Why it matters:
  it is still the clearest foundational-wave reference for `driver-hosted local
  tracker services`.
- Interesting ideas:
  let web apps and small local tools talk to SteamVR without writing their own
  driver; expose tracker creation through JSON messages; add a local HTTP page
  for quick testing; echo current runtime state back through the same service.
- Interesting implementation choices:
  the code keeps tutorial-style `HMD`, `controller`, `tracker`, and tracking
  reference device classes, but wraps them inside a `Boost.Beast` service host;
  the driver keeps shared JSON and echo state under explicit mutexes; trackers
  are created and updated dynamically by ID while still using standard Vive
  tracker render models and input profiles.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the networking layer is heavier than the narrow tracker use case really
  needs, and the repo remains much more of a bridge service than a polished end
  user tool.
- What to inspect next:
  compare its protocol and lifecycle choices against newer bridge-driver lines
  like `Simple-OpenVR-Bridge-Driver`, especially around tracker role metadata
  and transport simplicity.

## `surplex-io/OpenVR-Driver`

- GitHub:
  [surplex-io/OpenVR-Driver](https://github.com/surplex-io/OpenVR-Driver)
- What it is:
  a near-lineage fork of the John-Dean WebSocket tracker-driver architecture.
- Why it matters:
  it is useful as a `comparison variant`, not as a fully separate mainline
  architecture.
- Interesting ideas:
  keep the same WebSocket tracker-service model while adding explicit tracker
  role mapping support.
- Interesting implementation choices:
  compared file-for-file against the John-Dean line, the only substantive extra
  source files are `TrackerRole.cpp/.hpp`, which add SlimeVR-style role and
  device-type mapping while the rest of the driver layout remains essentially
  the same.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  low-medium.
- Caveats:
  it does not currently justify equal weight with the main upstream line; its
  value is mostly in the delta.
- What to inspect next:
  only revisit it if the fork evolves substantially beyond role mapping or
  becomes the more actively maintained line in this family.

## `gpsnmeajp/VirtualMotionTracker`

- GitHub:
  [gpsnmeajp/VirtualMotionTracker](https://github.com/gpsnmeajp/VirtualMotionTracker)
- What it is:
  a mature virtual tracker platform for SteamVR that accepts external pose and
  skeletal input over `OSC`.
- Why it matters:
  it is one of the strongest foundational-wave donors in the entire
  `virtual tracker` family.
- Interesting ideas:
  treat `custom trackers` as a reusable platform capability rather than a one-off
  hack; support both normal pose updates and skeletal/glove input; provide a
  manager app, docs, API references, and samples next to the driver.
- Interesting implementation choices:
  the repo is explicitly split into `vmt_driver` and `vmt_manager`; the driver
  has a dedicated `CommunicationManager` and `DirectOSC` transport layer; OSC
  addresses distinguish between room-space and raw-space updates and also expose
  outbound `alive`, `haptic`, `devices`, and subscribed-device messages; the
  manager runs its own OSC receive thread and ships API-facing helper code.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the public docs and source comments are mixed-language, and the project is
  broad enough that a future deeper protocol matrix could still be useful.
- What to inspect next:
  compare its direct OSC contract with the simpler WebSocket driver lines and
  with newer bridge drivers that want a thinner transport layer.

## `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay`

- GitHub:
  [RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay](https://github.com/RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay)
- What it is:
  a small OpenVR overlay dedicated to `EyeTrackVR` calibration.
- Why it matters:
  it is a strong foundational example of an `overlay-first calibration wizard`
  with almost no unnecessary product weight.
- Interesting ideas:
  support both `center-only` calibration and a full `9-point` sequence; keep
  the user-facing calibration UI fully inside VR while the tracker side listens
  over UDP.
- Interesting implementation choices:
  the entire utility is basically one `main.cpp` that creates an overlay,
  animates a dot through HMD-relative positions, and sends integer calibration
  states to a local UDP peer; the included Python helper makes the expected
  wire format explicit instead of hiding it behind undocumented runtime magic.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  tiny scope by design; it is a calibration surface, not a larger eye-tracking
  platform.
- What to inspect next:
  compare its minimal UDP signaling and point-sequencing logic with other
  calibration tools that need richer progress, failure, or profile handling.

## `WiiPlayer2/VnotifieR`

- GitHub:
  [WiiPlayer2/VnotifieR](https://github.com/WiiPlayer2/VnotifieR)
- What it is:
  a Unity-based local notification server and OpenVR overlay.
- Why it matters:
  it is one of the cleanest early examples of a `server-driven notification
  overlay`, which is exactly the kind of product family `VR-apps-lab` keeps
  revisiting.
- Interesting ideas:
  accept notifications by local HTTP `POST`; keep all behavior configurable in
  `server.ini`; let the panel behave differently when the dashboard is open
  versus when it is passively fading after a notification.
- Interesting implementation choices:
  `NotificationServer.cs` uses `HttpListener` and a `/notification` endpoint;
  config is split cleanly into `Main`, `Server`, `Panel`, and `Overlay`
  sub-configs; the overlay registers its own autostart manifest through the
  `OVRLay` wrapper; `NotificationPanel.cs` keeps separate opacities and a
  fade-timer model for passive versus dashboard-visible states.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  older Unity stack and OVRLay dependency; not a general automation bus, but a
  focused notification surface.
- What to inspect next:
  compare it directly with `OpenVROverlayPipe`, `OpenVRNotificationPipe`, and
  `OpenVR2WS` as a `notification ingress` family rather than treating them as
  isolated one-offs.

## `BenWoodford/OVROverlayManager`

- GitHub:
  [BenWoodford/OVROverlayManager](https://github.com/BenWoodford/OVROverlayManager)
- What it is:
  a tiny Unity helper layer for projecting render textures into OpenVR overlays
  and feeding overlay input back into Unity UI.
- Why it matters:
  it is not a full product, but it is a very useful `overlay toolkit
  scaffolding` reference from the foundational waves.
- Interesting ideas:
  separate overlay initialization from the overlay projector component; let
  dashboard and in-game overlays share one toolkit; translate OpenVR mouse
  events into Unity `EventSystem` input instead of rebuilding a new UI stack.
- Interesting implementation choices:
  `OverlayManager.cs` initializes OpenVR as an overlay app and exposes
  `System`, `Compositor`, and `OverlayFactory`; `OverlayProjector.cs` owns
  render-texture submission, overlay creation, width changes, dashboard icons,
  and event polling; `OverlayInputModule.cs` converts overlay mouse state into
  standard Unity pointer events.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  tiny scope, rough docs, and old Unity assumptions; it is best treated as a
  donor scaffold, not as a finished utility.
- What to inspect next:
  compare it against `OVRLay`, `SteamVR-Webkit`, and newer overlay templates to
  identify which parts of the Unity-side input bridge still generalize cleanly.

## `mittorn/ovr-utils-dashboard`

- GitHub:
  [mittorn/ovr-utils-dashboard](https://github.com/mittorn/ovr-utils-dashboard)
- What it is:
  a Godot-based cross-platform overlay shell intended to host many small
  SteamVR utility surfaces in one runtime.
- Why it matters:
  it helps explain the middle ground between `overlay toolkit` and
  `finished utility suite`.
- Interesting ideas:
  load overlays from settings instead of hardcoding them; treat keyboard,
  display capture, battery, clock, image viewer, and utility windows as
  pluggable overlay scenes; keep tracking targets and per-anchor offsets inside
  a structured settings schema.
- Interesting implementation choices:
  `overlay_manager.gd` restores overlay instances from a settings store;
  `settings_definition.gd` defines overlay visibility, size, alpha, target,
  fallback targets, and per-anchor pose offsets in one persistent schema; the
  repo is organized around reusable add-ons such as `godot-openvr`,
  `openvr_overlay`, and `settings-manager` rather than one monolithic script.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  README coverage is light and the repo still depends on a specific Godot and
  plugin stack; donor value comes from structure more than from polished user
  docs.
- What to inspect next:
  compare it directly with `openvr_widgets`, `OVRLay`, and `OVROverlayManager`
  as one `overlay toolkit versus overlay shell` lineage.

## Cross-wave synthesis after normalization

### 1. The foundational corpus was directionally right

The early waves had already identified several of the best long-term families:

- remote-control and notification overlays;
- battery and device micro-tools;
- tracker bridges and virtual trackers;
- vendor-enhancement layers;
- SteamVR environment helpers;
- overlay implementation scaffolds.

What they lacked was consistent `depth and classification`, not family
intuition.

### 2. Several foundational statuses were promoted

This retro pass is strong enough to promote the following repos to
`Already studied` in the canonical registry:

- `MuffinTastic/steamvr-exconfig`
- `zeroae/VRBattery`
- `gpsnmeajp/VirtualMotionTracker`
- `John-Dean/OpenVR-Tracker-Websocket-Driver`
- `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay`
- `WiiPlayer2/VnotifieR`
- `BenWoodford/OVROverlayManager`
- `mittorn/ovr-utils-dashboard`

### 3. One early bridge repo is better treated as a variant

`surplex-io/OpenVR-Driver` is currently closer to `Fork / variant only` than a
fully separate mainline architecture target.

Its present value is mostly the delta over the John-Dean upstream line,
especially explicit tracker-role mapping.

### 4. `PSVR2Toolkit` remains strategically important, but not fully exhausted

It stays `Partially studied` because its most interesting boundaries are also
its riskiest ones:

- vendor update fragility;
- reverse-engineered hook offsets;
- non-commercial licensing;
- partially closed and vendor-coupled behavior.

### 5. The foundational corpus exposed a real reusable method

The early waves also made one reusable method much clearer than before:

- `overlay toolkit and prefab scaffolding`

This sits between `finished overlay product` and `tiny one-off demo`, and is
useful for turning Unity or Godot scenes into reusable overlay building blocks.

## Remaining foundational follow-up gaps

The foundational waves are in much better shape now, but a few high-value
follow-ups remain:

1. `CrispyPin/ovr-utils`
   GitHub is no longer the real upstream, so the next honest step is a
   non-GitHub source pass rather than more inference from a stale mirror.
2. `PSVR2Toolkit`
   still deserves a dedicated deeper pass on update resilience, developer API
   usage, and closed-source boundaries.
3. `OpenVR-Tracker-Websocket-Driver` comparison family
   the main upstream is now understood better, but `Simple-OpenVR-Bridge-Driver`
   and the `3NekoSystem` / `v0xie` variants still deserve comparison treatment.
4. `Custom-device learning path`
   `opengloves-driver`, `hobo_vr`, `GlassVr`, and
   `Simple-OpenVR-Driver-Tutorial` remain one of the strongest early-wave
   follow-up clusters.

## Bottom line

The foundational research corpus is no longer just a historical pile of early
notes.

After this pass, `waves 1-7` have a cleaner modern bridge into the canonical
research system:

- old-wave context is preserved;
- high-value early repos now have wave-12/13-style deep notes;
- several statuses are corrected;
- remaining early gaps are clearer and more honest.
