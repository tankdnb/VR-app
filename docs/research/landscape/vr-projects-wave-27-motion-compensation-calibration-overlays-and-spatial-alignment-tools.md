# VR Projects Wave 27: Motion Compensation, Calibration Overlays, and Spatial Alignment Tools

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `motion compensation`, `calibration overlays`, and
  `spatial alignment tools`.

## Why this wave exists

The repository already had important calibration repos, but the family still
needed a clearer comparison between its internal construction methods:

- `OpenVR driver hook` versus `OpenXR API layer`;
- one-shot calibration versus continuous correction;
- minimal overlay calibration UX versus larger shared-library ecosystems;
- spatial capture and reconstruction as an adjacent alignment tool.

This wave exists to make `alignment UX and pose rewriting` a stronger method
family inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with motion-compensation, space-calibration, and alignment
   family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `openvrmc/OpenVR-MotionCompensation` | Strongest OpenVR-side pose-rewrite donor in the current repo |
| `BuzzteeBear/OpenXR-MotionCompensation` | Strongest OpenXR-side comparison donor |
| `pushrax/OpenVR-SpaceCalibrator` | Foundational mixed-space calibration reference that anchors the family |
| `Marshall-vak/OpenVR-SpaceCalibrator2` | Important continuous-calibration continuation of the same line |
| `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay` | Minimal overlay-first calibration surface |
| `alexander-clarke/openvr-room-mapping` | Useful adjacent alignment node for pose capture plus scene reconstruction |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `tobexeon/PSVR2EyeTrackingCalibration` | Interesting real-time calibration client, but it depends on a custom PSVR2Toolkit fork instead of the main upstream line |

## Deep-pass notes by project

## `openvrmc/OpenVR-MotionCompensation`

- GitHub:
  [openvrmc/OpenVR-MotionCompensation](https://github.com/openvrmc/OpenVR-MotionCompensation)
- What it is:
  an OpenVR-side motion-compensation stack built around driver hooks, a shared
  library, and a dashboard configuration surface.
- Why it matters:
  it is the strongest donor in the repo for
  `driver-side pose rewrite with overlay configuration`.
- Interesting ideas:
  hook pose flow before it reaches the runtime; expose configuration through an
  in-VR dashboard; keep a separate reusable library contract for clients and
  helpers.
- Interesting implementation choices:
  the repo makes the split explicit through
  `driver_vrmotioncompensation/src/devicemanipulation/MotionCompensationManager.cpp`,
  several hook modules under `src/hooks/*`,
  `client_overlay/src/overlaycontroller.cpp`, and the public
  `lib_vrmotioncompensation` API.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  deep hook logic raises compatibility and maintenance risk.
- What to inspect next:
  compare it directly with `OpenXR-MotionCompensation` to isolate when a
  `driver hook` is better than an `API layer`.

## `BuzzteeBear/OpenXR-MotionCompensation`

- GitHub:
  [BuzzteeBear/OpenXR-MotionCompensation](https://github.com/BuzzteeBear/OpenXR-MotionCompensation)
- What it is:
  an OpenXR motion-compensation stack built around an API layer and matching
  control surfaces.
- Why it matters:
  it is the clearest comparison donor for
  `runtime-side compensation via OpenXR API layer`.
- Interesting ideas:
  keep compensation inside the runtime extension layer; pair it with a separate
  dashboard or desktop configuration flow; avoid a new OpenVR driver when the
  OpenXR boundary is the cleaner place to adapt.
- Interesting implementation choices:
  the source exposes `layer.cpp`, `modifier.cpp`, `overlay.cpp`, `tracker.cpp`,
  `config.cpp`, and layer manifests, which makes the API-layer construction
  method very visible.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  OpenXR layer behavior depends on runtime support and deployment details.
- What to inspect next:
  compare it with driver-side approaches to see where configuration ownership
  and correction timing meaningfully differ.

## `pushrax/OpenVR-SpaceCalibrator`

- GitHub:
  [pushrax/OpenVR-SpaceCalibrator](https://github.com/pushrax/OpenVR-SpaceCalibrator)
- What it is:
  the foundational mixed-space calibration tool in this repository family.
- Why it matters:
  it remains the main reference for `guided multi-space calibration UX`.
- Interesting ideas:
  align different tracking systems; use a visible calibration flow rather than
  hidden offsets; preserve profiles and chaperone context; pair overlay UX with
  driver-side helpers.
- Interesting implementation choices:
  `Calibration.cpp`, `UserInterface.cpp`, and `IPCClient.cpp` make the overlay,
  calibration math, and driver communication boundaries easy to study.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  mature and broad, so it teaches several things at once.
- What to inspect next:
  treat it as the main baseline for future comparisons inside the entire
  calibration family.

## `Marshall-vak/OpenVR-SpaceCalibrator2`

- GitHub:
  [Marshall-vak/OpenVR-SpaceCalibrator2](https://github.com/Marshall-vak/OpenVR-SpaceCalibrator2)
- What it is:
  a continuation of the SpaceCalibrator line with stronger continuous
  calibration support.
- Why it matters:
  it is the clearest donor in the repo for `continuous calibration extension`.
- Interesting ideas:
  extend one-shot calibration into an ongoing correction workflow; expose
  metrics and debug views; keep the overlay and driver IPC split visible.
- Interesting implementation choices:
  the repo exposes `src/driver/IPCServer.cpp` and several overlay-side modules
  such as `Calibration.cpp`, `CalibrationCalc.cpp`, `CalibrationMetrics.cpp`,
  `Configuration.cpp`, and `IPCClient.cpp`.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  best understood as an evolution of the original SpaceCalibrator model, not a
  separate unrelated family.
- What to inspect next:
  compare it directly with `OpenVR-SpaceCalibrator` to isolate the minimum
  architecture changes required for continuous calibration.

## `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay`

- GitHub:
  [RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay](https://github.com/RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay)
- What it is:
  a minimal overlay-first calibration tool for eye tracking.
- Why it matters:
  it is the best small donor in the repo for
  `overlay-first calibration surface with almost no extra product baggage`.
- Interesting ideas:
  keep calibration extremely focused; use a simple point sequence; separate the
  overlay and the external communication path.
- Interesting implementation choices:
  `src/main.cpp` and `OpenVR_Overlay_Communication.py` make the minimal
  overlay-plus-communication architecture easy to understand.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  intentionally narrow and minimal.
- What to inspect next:
  compare it with larger calibration suites to identify the minimum useful
  calibration UX surface.

## `alexander-clarke/openvr-room-mapping`

- GitHub:
  [alexander-clarke/openvr-room-mapping](https://github.com/alexander-clarke/openvr-room-mapping)
- What it is:
  a pose-plus-image capture pipeline that reconstructs room geometry from
  OpenVR-tracked data.
- Why it matters:
  it is a useful adjacent donor for
  `pose capture -> reconstruction -> spatial alignment`.
- Interesting ideas:
  capture headset pose and images together; treat spatial understanding as an
  external pipeline instead of a live overlay; use reconstruction tooling to
  turn runtime capture into later alignment artifacts.
- Interesting implementation choices:
  `openvr_camera.py`, `reconstruct.py`, and the supporting COLMAP-oriented files
  make the capture and reconstruction split explicit.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  more of an adjacent spatial-alignment tool than a direct calibration utility.
- What to inspect next:
  compare it with passthrough and room-scan experiments only when a later wave
  needs stronger spatial-environment overlap.

## Main takeaways from Wave 27

- `Alignment tooling` is now clearer as more than one calibration overlay.
- The strongest split inside the family is:
  - `driver-side motion compensation`
  - `OpenXR API-layer compensation`
  - `guided mixed-space calibration`
  - `continuous calibration extension`
  - `minimal overlay-first calibration`
  - `spatial capture and reconstruction`
- The best calibration donor is often about `UX and persistence`, not only
  tracking math.

## Reusable methods clarified by this wave

- `Driver-side pose rewrite with shared library and overlay configuration`
- `Continuous calibration overlay layered on top of a one-shot alignment baseline`
- `Pose capture to reconstruction pipeline for spatial alignment experiments`

## Recommended next moves after this wave

1. Treat `OpenVR-MotionCompensation` and `OpenXR-MotionCompensation` as a core
   comparison pair whenever a future tool idea touches runtime correction.
2. Keep `OpenVR-SpaceCalibrator` as the family baseline and
   `OpenVR-SpaceCalibrator2` as the main `continuous calibration` extension.
3. Use `EyeTrackVR-OpenVR-Calibration-Overlay` as the best minimal reference
   for focused overlay-first calibration UI.
4. Keep `openvr-room-mapping` visible as an adjacent alignment donor rather
   than forcing it into a pure passthrough-only bucket.
