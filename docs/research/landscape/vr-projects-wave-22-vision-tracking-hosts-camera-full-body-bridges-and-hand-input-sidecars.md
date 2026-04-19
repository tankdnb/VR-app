# VR Projects Wave 22: Vision Tracking Hosts, Camera Full-Body Bridges, and Hand-Input Sidecars

- Date: `2026-04-19`
- Goal: add the next serious GitHub research wave for repositories already
  present but not yet represented deeply enough in `VR-apps-lab`, focusing on
  `vision tracking hosts`, `camera full-body bridges`, and
  `hand-input sidecar stacks`.

## Why this wave exists

Wave 13 mapped the family well, but it left several of the strongest repos only
`Partially studied`.

What still needed extraction was:

- the `legacy tracker app -> plugin host platform` migration story;
- the difference between `switchable backend`, `driver-centered`, and
  `thin sidecar shell` camera-tracking architectures;
- the hand-specific branch where a foreign runtime or cheap camera becomes a
  SteamVR input path.

This wave is intentionally a `repeat deep pass`, not a broad new-discovery
wave.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. re-check the strongest partially studied family members;
2. confirm whether better forks or replacements appeared;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods and architecture lessons;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `KinectToVR/Amethyst` | Strongest plugin-host architecture in the vision-tracking branch |
| `KinectToVR/KinectToVR` | Needed a repeat pass as the legacy baseline for the same ecosystem |
| `ju1ce/Mediapipe-VR-Fullbody-Tracking` | Clearest single-camera CV pipeline with switchable output backends |
| `Wunder-Wulfe/NVIDIA-BodyTracking` | Strongest GPU-assisted driver-centered camera tracking repo in the family |
| `Nordskog/HandOfLesser` | Strongest hand-specific foreign-runtime bridge into SteamVR and VRChat |
| `NovaAshwolfDev/HandCameraDriver` | Useful minimal skeleton for a camera sidecar plus SteamVR driver shell |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `chnoblouch/aethervr` | Still better treated as the `headsetless runtime` branch rather than part of the camera-side driver or host family |
| `MasonSakai/VR-AI-Full-Body-Tracking` | Comparison node remains useful, but the public repo still reads as an in-transition rewrite rather than a stable donor |

## Deep-pass notes by project

## `KinectToVR/Amethyst`

- GitHub:
  [KinectToVR/Amethyst](https://github.com/KinectToVR/Amethyst)
- What it is:
  a modern plugin-based tracking host from the `K2VR` ecosystem.
- Why it matters:
  it is the strongest donor in this wave for `plugin-host tracking platform
  with device and service endpoints`.
- Interesting ideas:
  separate `tracking devices` from `service endpoints`; let plugins own startup
  behavior, metadata, settings, and lifecycle; keep calibration and runtime UX
  in one host while allowing device and output variety.
- Interesting implementation choices:
  `PluginHost.cs` and related MVVM shell code make plugin loading and lifecycle
  explicit; `ServiceEndpoint.cs` exposes output-side contracts alongside device
  plugins; the overall repo shows how `tracking platform` can be broader than a
  single body-tracker app.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  some of the strongest signal still lives in sibling plugin repos; a single
  pass does not exhaust the full ecosystem.
- What to inspect next:
  `plugin_OpenVR`, `plugin_OSC`, settings-daemon ownership, and how calibration
  state is shared across plugins.

## `KinectToVR/KinectToVR`

- GitHub:
  [KinectToVR/KinectToVR](https://github.com/KinectToVR/KinectToVR)
- What it is:
  a large legacy full-body tracking stack with separate Kinect and PSMove
  worker processes.
- Why it matters:
  it is the clearest baseline for understanding why `Amethyst` had to evolve
  into a plugin host instead of staying one monolithic tracking app.
- Interesting ideas:
  split `Kinect V1`, `Kinect V2`, and `PSMoveService` handling into separate
  processes; keep a larger control shell for calibration and testing; encode a
  lot of tracker math and calibration state in one historical stack.
- Interesting implementation choices:
  the repo contains `KinectV1Process`, `KinectV2Process`, `PSMSProcess`, and a
  heavier main app shell; the real donor value is in the calibration and
  process-split story rather than in clean modern architecture.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  legacy dependencies and older assumptions remain heavy; this is more useful
  as a migration lesson than as a direct implementation template.
- What to inspect next:
  compare deliberately against `Amethyst` as one `legacy app to host platform`
  migration story.

## `ju1ce/Mediapipe-VR-Fullbody-Tracking`

- GitHub:
  [ju1ce/Mediapipe-VR-Fullbody-Tracking](https://github.com/ju1ce/Mediapipe-VR-Fullbody-Tracking)
- What it is:
  a single-camera body-tracking tool built around `MediaPipe`, with both a
  SteamVR-driver backend and a `VRChat OSC` backend.
- Why it matters:
  it is the strongest donor in this wave for `switchable CV tracking backend
  with web control surface`.
- Interesting ideas:
  keep one pose-estimation pipeline but allow either `SteamVR` or `VRChat OSC`
  output; expose setup and settings through a lightweight WebUI for
  Quest-friendly workflows; keep the user-facing control shell simpler than a
  full desktop host platform.
- Interesting implementation choices:
  `backends.py` cleanly splits the SteamVR path from the OSC path;
  `mediapipepose.py` and related helpers own the pose pipeline;
  `webui.py` plus `templates/index.html` create a browser-based control surface
  instead of a heavier desktop shell.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  still depends on an external driver path on the SteamVR side and remains
  calibration-sensitive like most single-camera CV systems.
- What to inspect next:
  how much of the WebUI pattern could be reused in other `VR-apps-lab`
  utilities and how its output abstraction compares with `HandOfLesser`.

## `Wunder-Wulfe/NVIDIA-BodyTracking`

- GitHub:
  [Wunder-Wulfe/NVIDIA-BodyTracking](https://github.com/Wunder-Wulfe/NVIDIA-BodyTracking)
- What it is:
  a SteamVR driver that uses the NVIDIA body-tracking stack for camera-based
  full-body tracking.
- Why it matters:
  it is the clearest `GPU-assisted, driver-centered` camera-tracking donor in
  the family.
- Interesting ideas:
  keep tracker-role scaling, alignment, and confidence handling inside one
  driver-centered product; pair the driver with an overlay for in-headset
  alignment rather than relying on desktop config only.
- Interesting implementation choices:
  the README makes the `CPU capture -> GPU inference -> CPU cleanup ->
  per-render interpolation` pipeline explicit; the repo includes a dedicated
  overlay project and dense settings surface for tracker-role configuration and
  interpolation.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  depends on `Windows + NVIDIA + vendor SDK`; practical reuse is strongest at
  the pattern level.
- What to inspect next:
  overlay-assisted alignment flow and how much of its smoothing and tracker-role
  logic generalizes outside the NVIDIA path.

## `Nordskog/HandOfLesser`

- GitHub:
  [Nordskog/HandOfLesser](https://github.com/Nordskog/HandOfLesser)
- What it is:
  an experimental bridge that turns Quest/OpenXR hand tracking into SteamVR and
  VRChat-facing input surfaces.
- Why it matters:
  it is the strongest `hand-tracking bridge` donor in the family, not just a
  general body-tracking tool.
- Interesting ideas:
  keep one app responsible for OpenXR polling, SteamVR output, VRChat behavior,
  and settings toggles; support both named-pipe and UDP transport behind one
  packet model; treat hands as a richer input bridge than a basic tracker feed.
- Interesting implementation choices:
  the source tree makes transport and output surfaces explicit through files
  like `osc_float_input.cpp`, `osc_alternate_float_input.cpp`,
  `steamvr_bool_input.cpp`, `steamvr_float_input.cpp`, and
  `settings_toggle_input.cpp`; the repo also contains `oculus_hacks.*` and
  structured packet definitions in the shared code.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  still a moving target with runtime-specific assumptions and a lot of tuning.
- What to inspect next:
  controller-hooking behavior, offset persistence, and how the body-tracker
  branch compares with camera full-body systems.

## `NovaAshwolfDev/HandCameraDriver`

- GitHub:
  [NovaAshwolfDev/HandCameraDriver](https://github.com/NovaAshwolfDev/HandCameraDriver)
- What it is:
  a small archived webcam-hand-tracking project built around a Python sidecar
  and a minimal SteamVR driver shell.
- Why it matters:
  it is still a useful `thin sidecar plus driver shell` reference even though
  the repo remains rough and incomplete.
- Interesting ideas:
  keep the driver tiny; let the camera-side logic live elsewhere; provide just
  enough SteamVR manifest, input-profile, and driver scaffolding to make the
  path concrete.
- Interesting implementation choices:
  the repo contains `Camera.py` plus a small `SteamVR Driver/src/` tree with
  `device_provider`, `controller_device_driver`, and `hmd_driver_factory`;
  that makes the sidecar/driver boundary visible even without a polished final
  implementation.
- Code donor value:
  low-medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  public implementation remains incomplete and partly dormant.
- What to inspect next:
  revisit only if a maintained fork appears or the current repo revives with a
  fuller socket and camera path.

## Main takeaways from Wave 22

- `Vision tracking` is now much clearer as three different construction styles:
  - `plugin host platform`
  - `switchable backend CV utility`
  - `driver-centered camera tracker`
- `Hand bridge` is a distinct branch, not just a subset of body tracking.
- The most useful contrast in the family is now:
  - `KinectToVR` as legacy baseline
  - `Amethyst` as host-platform evolution
  - `Mediapipe-VR-Fullbody-Tracking` as backend-switchable CV utility
  - `NVIDIA-BodyTracking` as GPU-assisted driver-centered path
  - `HandOfLesser` as foreign-runtime hand bridge

## Reusable methods clarified by this wave

- `Plugin-host tracking platform with device and service endpoints`
- `Switchable CV tracking backend with web control surface`

## Recommended next moves after this wave

1. Promote `Amethyst`, `KinectToVR`, `Mediapipe-VR-Fullbody-Tracking`,
   `NVIDIA-BodyTracking`, and `HandOfLesser` as properly studied family nodes.
2. Keep `HandCameraDriver` visible as a thin architectural skeleton rather than
   inflating its donor maturity.
3. Leave `aethervr` and `VR-AI-Full-Body-Tracking` as follow-up comparison
   nodes instead of forcing them into this repeat deep pass.
