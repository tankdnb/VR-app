# VR Projects Wave 16: Device Monitors, Pose Exporters, and Environment Helpers

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `battery and device monitors`, `pose-inspection and export helpers`, and
  `SteamVR environment-side utilities`.

## Why this wave exists

The repository already had strong coverage of:

- overlay hosts and dashboard surfaces;
- tracker bridges and OSC exporters;
- runtime switchers and OpenXR diagnostics;
- accessibility helpers and custom-driver learning paths.

What was still under-modeled was the practical utility layer around `day-to-day
SteamVR operations`:

- small tools that watch `charging state` and react to transitions;
- helpers that export `live device poses` into creator-friendly artifacts;
- micro-tools that are intentionally `desktop-side`, not in-headset products;
- environment helpers that solve real SteamVR pain points without being classic
  overlays.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with device-monitor and SteamVR-helper family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `jangxx/openvr-battery-monitoring` | Strong battery-alert reference centered on charging-state transitions and notification channels |
| `mutr/openvr_battery_monitor` | Distinct battery-monitor variant that logs to InfluxDB instead of behaving as an end-user notifier |
| `KaftanOS/SteamVR-Battery-Checker` | Honest tiny one-shot battery inspector rather than a resident app |
| `MuffinTastic/openvr-device-positions` | Valuable creator-facing helper that turns live SteamVR poses into FBX output and also ships a VR overlay |
| `DavidRisch/steamvr_utils` | Linux-side SteamVR helper collection with daemonized base-station and audio behavior |

## Secondary candidate surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `Denwa/vive-wireless-info-overlay` | Good product reference for narrow device-health overlays, but the public GitHub snapshot is still too source-light for a stronger donor classification |

## Deep-pass notes by project

## `jangxx/openvr-battery-monitoring`

- GitHub:
  [jangxx/openvr-battery-monitoring](https://github.com/jangxx/openvr-battery-monitoring)
- What it is:
  a Python tray utility that monitors SteamVR devices and warns when a device
  that was charging begins discharging again.
- Why it matters:
  it shows the cleanest `state-transition watcher` pattern in this family
  instead of merely polling and printing current battery levels.
- Interesting ideas:
  keep a per-device state table; allow per-serial muting; support both desktop
  notifications and `OVRT`-style in-headset notifications; stay resident and
  reconnect automatically when SteamVR returns.
- Interesting implementation choices:
  `main.py` owns a `pystray` menu, mute persistence, notification channel
  toggles, and a `BatteryReader`; the warning is triggered when charging flips
  to discharging or when the level trend reverses unexpectedly; configuration
  persists muted devices and channel settings under a local config directory.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  Python plus tray-app dependencies make it more of a desktop-helper donor than
  a minimal native reference.
- What to inspect next:
  compare it directly with `mutr/openvr_battery_monitor` and
  `SteamVR-Battery-Checker` as one `watch and alert` vs `log and measure` vs
  `one-shot inspect` family note.

## `mutr/openvr_battery_monitor`

- GitHub:
  [mutr/openvr_battery_monitor](https://github.com/mutr/openvr_battery_monitor)
- What it is:
  a Windows background application that samples OpenVR battery percentages and
  writes them into `InfluxDB v2`.
- Why it matters:
  it proves that the battery-monitor family is not only about UI; it can also
  be a `telemetry exporter` for longer-term device-health analysis.
- Interesting ideas:
  install as a SteamVR auto-start utility; keep configuration in a flat config
  file; export metrics using line protocol instead of focusing on notifications;
  write both serial number and device class into the metrics stream.
- Interesting implementation choices:
  `openvr_battery_monitor.cpp` initializes OpenVR as a background app, reads a
  simple key-value config, collects battery percentages per connected device,
  formats InfluxDB line protocol, and sends it over HTTP using `Boost.Beast`.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  this is a metrics logger, not a polished user-facing health dashboard.
- What to inspect next:
  compare it with `openvr-metrics` and `clovr` as one small `runtime telemetry
  exporter` branch.

## `KaftanOS/SteamVR-Battery-Checker`

- GitHub:
  [KaftanOS/SteamVR-Battery-Checker](https://github.com/KaftanOS/SteamVR-Battery-Checker)
- What it is:
  a tiny Python script that lists connected SteamVR devices and prints battery
  levels when available.
- Why it matters:
  it is the most honest `one-shot CLI inspector` in this family and shows where
  a utility can stay useful without pretending to be a full product.
- Interesting ideas:
  do only one job; expose the current battery snapshot and exit; tolerate
  missing properties gracefully; keep the dependency surface extremely small.
- Interesting implementation choices:
  `steamvr_battery.py` initializes OpenVR in background mode, loops through
  tracked devices, prints class, serial, and `Prop_DeviceBatteryPercentage`,
  then shuts down immediately.
- Code donor value:
  low-medium.
- Product reference value:
  medium.
- Architecture reference value:
  low.
- Caveats:
  very small; no persistence, no notifications, no background behavior.
- What to inspect next:
  treat it as a good `minimum useful value` reference, not as a long-term
  architecture donor.

## `MuffinTastic/openvr-device-positions`

- GitHub:
  [MuffinTastic/openvr-device-positions](https://github.com/MuffinTastic/openvr-device-positions)
- What it is:
  a Windows utility that can show a small OpenVR dashboard overlay and export
  tracked-device poses into an `FBX` scene, optionally with SteamVR render
  models.
- Why it matters:
  it broadens the device-monitor family into a `creator and diagnostics`
  direction: not just watch current state, but capture it as a reusable asset.
- Interesting ideas:
  center exported transforms around the HMD on the XZ plane; optionally bake in
  actual render models; pair a desktop app with a dashboard overlay; let the
  utility be useful for avatar proportioning and staging, not only debugging.
- Interesting implementation choices:
  `Program.cs` runs both the Windows app and a separate overlay thread;
  `OVRManager.cs` wraps OpenVR init, refresh-rate detection, overlay creation,
  and render-model lookup;
  `OverlayThread.cs` uses `Veldrid` plus `ImGui` to render a dashboard surface;
  `Devices.cs` reads tracked poses, transforms them relative to the HMD, and
  writes a binary `FBX` scene through `Aspose.ThreeD`.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  the creator/export side is stronger than the end-user overlay UX.
- What to inspect next:
  compare it with `OpenKneeboard`, `clovr`, and `triad_openvr` as one
  `runtime state -> exportable artifact` design branch.

## `DavidRisch/steamvr_utils`

- GitHub:
  [DavidRisch/steamvr_utils](https://github.com/DavidRisch/steamvr_utils)
- What it is:
  a Linux helper collection that turns base stations on or off and rewires
  PulseAudio streams around SteamVR usage, optionally through a daemon.
- Why it matters:
  it is one of the clearest `SteamVR environment hygiene` references in the
  repo and helps define this as a legitimate utility family outside overlays.
- Interesting ideas:
  use one daemon stage machine for `before SteamVR`, `during SteamVR`, and
  `after SteamVR`; repeat audio routing while SteamVR is active; create launch
  options and desktop files automatically; drive behavior from a documented
  YAML config with regex-based exclusions.
- Interesting implementation choices:
  `steamvr_utils.py` selects actions and initializes base-station and audio
  helpers;
  `steamvr_daemon.py` implements a staged process watcher around the SteamVR
  lifecycle;
  `audio/audio_switcher.py` and related `pactl_interface` modules switch sinks
  and sources rather than merely changing defaults;
  `install.py` prints SteamVR launch options and writes desktop shortcuts.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  Linux-specific and partly superseded by later SteamVR behavior for some users.
- What to inspect next:
  compare it with `steamvr-exconfig`, `SteamVR-Toggle`, and `dashfix` as one
  `environment helper` subfamily rather than leaving it in a generic misc
  bucket.

## `Denwa/vive-wireless-info-overlay`

- GitHub:
  [Denwa/vive-wireless-info-overlay](https://github.com/Denwa/vive-wireless-info-overlay)
- What it is:
  a narrow overlay that shows Vive Wireless Adapter temperatures at a fixed
  refresh cadence.
- Why it matters:
  it demonstrates how small and honest a useful VR health utility can be.
- Interesting ideas:
  pick one device-specific pain point; keep the product framing obvious; live as
  a tiny compatibility-friendly overlay instead of becoming a full suite.
- Code donor value:
  low.
- Product reference value:
  medium.
- Architecture reference value:
  low.
- Caveats:
  the public GitHub snapshot is effectively source-light.
- What to inspect next:
  revisit only if a fuller source mirror appears.

## Main takeaways from Wave 16

- `Device monitor` is now clearly a multi-branch family, not one flat bucket.
- The most useful split is:
  - `state-transition notifier`
  - `metrics logger`
  - `one-shot inspector`
  - `creator-side pose exporter`
  - `environment daemon`
- The repo now has stronger evidence that `desktop-side helpers` deserve equal
  treatment alongside in-headset overlays.

## Reusable methods clarified by this wave

- `State-transition device watcher with multi-channel alerts`
- `Pose inventory snapshot exporter`
- `SteamVR lifecycle daemon with environment side effects`

## Recommended next moves after this wave

1. Compare the battery-monitor subfamily directly instead of tracking each repo
   in isolation.
2. Revisit `Denwa/vive-wireless-info-overlay` only if stronger source appears.
3. Treat `openvr-device-positions` as part of the creator-tools branch, not as
   just another battery or inventory helper.
4. Keep `steamvr_utils` visible in the SteamVR hygiene family so Linux-side
   helpers do not disappear under overlay-heavy research.
