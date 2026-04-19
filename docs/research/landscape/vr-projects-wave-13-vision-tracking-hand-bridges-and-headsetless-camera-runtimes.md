# VR Projects Wave 13: Vision Tracking, Hand Bridges, and Headsetless Camera Runtimes

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet in `VR-apps-lab`, focusing on `vision-based tracking`,
  `camera-driven hand/body bridges`, and `headsetless camera runtimes` across
  `SteamVR/OpenVR` and `OpenXR`.

## Why this wave exists

The repository already had stronger coverage of:

- classic OpenVR/OpenXR overlays and diagnostics;
- tracker bridges, OSC tools, and driver tutorials;
- synthetic controllers, DIY hardware, and input-emulation sidecars;
- null-driver and no-HMD workflow helpers.

What was still missing was a denser layer of:

- `service-backed hand drivers` that wrap vendor tracking or foreign runtimes
  into SteamVR input;
- `camera CV sidecars` that can target either SteamVR drivers or OSC outputs;
- `modular body-tracking hosts` that normalize many input devices behind one
  calibration and output shell;
- `camera-driven runtime substitutes` that go beyond a null driver and
  implement a real runtime-facing fake hardware path.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with focused family-level queries;
2. deduplicate against the registry;
3. freeze a shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `ultraleap/driver_ultraleap` | Mature service-backed SteamVR hand-driver path with external input injection and optional elbow trackers |
| `Nordskog/HandOfLesser` | OpenXR hand-tracking bridge from Quest runtimes into SteamVR and VRChat |
| `NovaAshwolfDev/HandCameraDriver` | Small but useful webcam-hand-tracking WIP showing a Python-sidecar plus custom-driver split |
| `KinectToVR/KinectToVR` | Large legacy full-body tracking stack that emulates Vive trackers from Kinect and PSMove inputs |
| `KinectToVR/Amethyst` | Modern plugin-based successor that reframes alternative tracking as a host platform rather than one app |
| `ju1ce/Mediapipe-VR-Fullbody-Tracking` | Single-camera pose-tracking tool with both SteamVR-driver and VRChat OSC backends |
| `Wunder-Wulfe/NVIDIA-BodyTracking` | GPU-assisted camera body-tracking SteamVR driver with overlay and multi-tracker configuration |
| `chnoblouch/aethervr` | Webcam-driven custom OpenXR runtime plus tracker sidecar for headsetless use |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `ju1ce/Simple-OpenVR-Bridge-Driver` | Strong adjacent bridge-driver signal, but it belongs more to the generic tracker-ingress family than to this wave's camera-centric core |
| `MasonSakai/VR-AI-Full-Body-Tracking` | Useful signal around low-cost camera FBT, but the repository still reads more like an in-transition InputEmulator-era prototype than a clean next donor |

## Deep-pass notes by project

## `ultraleap/driver_ultraleap`

- GitHub:
  [ultraleap/driver_ultraleap](https://github.com/ultraleap/driver_ultraleap)
- What it is:
  a `SteamVR/OpenVR` driver for `Ultraleap` hand-tracking devices.
- Why it matters:
  it is one of the clearest public references for a `service-backed hand
  driver` that turns an external tracking service into first-class SteamVR hand
  devices instead of a generic tracker bridge.
- Interesting ideas:
  switch cleanly between `hmd` and `desktop` mounting modes; expose optional
  `elbow trackers`; keep a documented `DebugRequest` JSON API so external tools
  can override or inject driver inputs.
- Interesting implementation choices:
  `LeapDeviceProvider` owns the virtual hand and elbow devices; separate driver
  settings map SteamVR config keys like `tracking_mode` and offsets into atomic
  state; input surfaces include pinch, grip, and thumbstick-style paths rather
  than raw skeleton only.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  depends on proprietary `Ultraleap Tracking Service` and specific hardware;
  the README still frames the result as `alpha-quality`.
- What to inspect next:
  failure recovery when the tracking service disappears, and the full practical
  envelope of the `DebugRequest` external-input path.

## `Nordskog/HandOfLesser`

- GitHub:
  [Nordskog/HandOfLesser](https://github.com/Nordskog/HandOfLesser)
- What it is:
  an experimental bridge that uses `OpenXR` hand-tracking extensions on Quest
  runtimes and feeds the result into `SteamVR` and `VRChat`.
- Why it matters:
  it is a rare public example of `foreign-runtime hand tracking -> SteamVR
  controller and skeletal input`, with extra VRChat-facing product framing.
- Interesting ideas:
  keep one core app responsible for OpenXR polling, SteamVR output, VRChat OSC,
  and UI; ship Unity assets for VRChat avatar gesture hookup; support both
  `named pipe` and `UDP` transports under a shared packet protocol.
- Interesting implementation choices:
  `HandOfLesserCore` owns `HandTracking`, `BodyTracking`, UI, SteamVR input,
  VRChat input, and transport threads; `HandOfLesserCommon` defines typed native
  packets for controller input, skeletal data, body trackers, settings, and
  driver/app state; the driver and app are separated but speak a structured,
  versionable packet format instead of ad-hoc strings.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  still a moving `WIP`; setup is developer-oriented; practical use requires
  heavy curl/splay tuning and runtime-specific assumptions.
- What to inspect next:
  how its controller-hooking path works in practice, how offsets are persisted,
  and whether the body-tracker branch is stable enough to compare with camera
  full-body systems.

## `NovaAshwolfDev/HandCameraDriver`

- GitHub:
  [NovaAshwolfDev/HandCameraDriver](https://github.com/NovaAshwolfDev/HandCameraDriver)
- What it is:
  a `WIP` webcam or phone-camera hand-tracking path built around a Python
  sidecar and a small custom SteamVR driver.
- Why it matters:
  even though it is rough, it exposes the smallest public skeleton in this wave
  for `camera sidecar + custom driver` architecture.
- Interesting ideas:
  let a cheap webcam or phone camera feed SteamVR hand input; target
  `VRChat SteamVR Input 2.0` explicitly; keep a dedicated input profile and
  driver manifest instead of staying at script-only level.
- Interesting implementation choices:
  the repo contains a real SteamVR driver tree with manifest, resources,
  settings, and `controller_device_driver` / `device_provider` classes; the
  driver README describes a local socket boundary between the Python tracker and
  the C++ driver.
- Code donor value:
  low-medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  the project is incomplete; `Camera.py` is empty in the current GitHub state;
  the docs are unfinished and read more like an intent statement than a stable
  implementation guide.
- What to inspect next:
  whether a maintained fork or successor exists, and whether the current driver
  side actually implements enough socket logic to be reusable.

## `KinectToVR/KinectToVR`

- GitHub:
  [KinectToVR/KinectToVR](https://github.com/KinectToVR/KinectToVR)
- What it is:
  a legacy full-body tracking application that emulates `Vive` trackers in
  SteamVR from `Kinect` sensors or `PSMoveService`.
- Why it matters:
  it is a dense reference for `legacy multi-process tracking stacks`, where the
  real donor value lies in calibration, orientation math, sensor workers, and
  practical deployment constraints rather than in clean modern architecture.
- Interesting ideas:
  split `Kinect V1`, `Kinect V2`, and `PSMoveService` handling into separate
  worker processes; keep a large desktop control shell for calibration and
  runtime testing; explicitly warn about non-ASCII install paths because OpenVR
  bindings can break there.
- Interesting implementation choices:
  the repo is divided into `SFMLProject`, `KinectV1Process`,
  `KinectV2Process`, and `PSMSProcess`; `KinectSettings.cpp` centralizes a very
  large amount of tracker math, yaw handling, offsets, and calibration-state
  manipulation; the main app pulls in shared-memory, networking, and UI code in
  one long-lived host process.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  this is an end-of-line legacy branch with heavy dependencies, older UI
  assumptions, and a lot of historical baggage that the maintainers later moved
  away from.
- What to inspect next:
  the actual SteamVR output boundary, how much depends on legacy
  `VRInputEmulator`-era assumptions, and where the modern `Amethyst` rewrite
  intentionally diverges.

## `KinectToVR/Amethyst`

- GitHub:
  [KinectToVR/Amethyst](https://github.com/KinectToVR/Amethyst)
- What it is:
  a modern plugin-based tracking host from the `K2VR` ecosystem, positioned as
  a modular replacement for older single-app tracking stacks.
- Why it matters:
  it reframes alternative tracking as a `platform` with device plugins and
  service endpoints, which is a much stronger product and architecture pattern
  than a one-off tracker app.
- Interesting ideas:
  separate `tracking devices` from `service endpoints`; give plugins metadata,
  dependency hooks, settings daemons, and auto-start behavior; keep calibration
  and runtime UX in one host app while letting actual tracking hardware vary.
- Interesting implementation choices:
  `Amethyst.Plugins.Contract` defines interfaces like `ITrackingDevice` and
  `IServiceEndpoint`; the main WinUI app hosts plugin loading, update bars,
  calibration UX, and service lifecycle; the repo pairs managed plugin contracts
  with a native support layer.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  developer docs are still incomplete; build guidance mostly points at CI
  rather than a clean local setup; a lot of real signal lives across sibling
  plugin repositories in the org.
- What to inspect next:
  the `plugin_OpenVR`, `plugin_OSC`, and device-plugin repos; how calibration
  state is shared across plugins; and whether this model could inspire a future
  `tracking lab host` inside `VR-apps-lab`.

## `ju1ce/Mediapipe-VR-Fullbody-Tracking`

- GitHub:
  [ju1ce/Mediapipe-VR-Fullbody-Tracking](https://github.com/ju1ce/Mediapipe-VR-Fullbody-Tracking)
- What it is:
  a single-camera body-tracking tool using `MediaPipe`, with both a SteamVR
  driver backend and a `VRChat OSC` backend.
- Why it matters:
  it is one of the clearest repositories in the wave for `backend-swappable
  pose output`, proving that one CV pipeline can target either a SteamVR driver
  or a Quest-friendly OSC path.
- Interesting ideas:
  choose between `SteamVR` and `VRChatOSC` backends at runtime; add a simple
  `WebUI` so Quest standalone users can calibrate without desktop access; spawn
  either the minimum tracker set or a skeleton preview depending on mode.
- Interesting implementation choices:
  `backends.py` cleanly separates the SteamVR text-command path from the OSC
  bundle path; `helpers.py` computes body and hand rotations from Mediapipe
  joints; `init_gui.py` persists settings and exposes backend choice, web UI,
  smoothing, and camera parameters; `mediapipepose.py` boots a Flask control
  surface when requested.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the SteamVR path still depends on an external driver installation; depth and
  room constraints remain serious; the body model is inherently noisy and
  calibration-sensitive.
- What to inspect next:
  the exact SteamVR driver protocol it expects, how its WebUI could generalize
  into other calibration tools, and how its pose cleanup compares with
  `NVIDIA-BodyTracking`.

## `Wunder-Wulfe/NVIDIA-BodyTracking`

- GitHub:
  [Wunder-Wulfe/NVIDIA-BodyTracking](https://github.com/Wunder-Wulfe/NVIDIA-BodyTracking)
- What it is:
  a `SteamVR` driver that uses the `NVIDIA AR / Broadcast SDK` for
  camera-based body tracking.
- Why it matters:
  it strengthens the `GPU-assisted camera body-tracking driver` branch, which
  differs materially from Python-sidecar or InputEmulator-era approaches.
- Interesting ideas:
  expose tracker layouts from `4-point` through `18-point`; keep alignment,
  mirroring, and camera switching in one driver-centered product; pair the
  driver with an overlay for in-headset feedback instead of desktop config only.
- Interesting implementation choices:
  `CServerDriver` coordinates the camera driver, NV SDK interface, virtual
  trackers, bindings, and interpolation state; `CCameraDriver` enumerates and
  streams camera input asynchronously; `settings.ini` exposes tracker-role
  selection, interpolation mode, and scaling; a dedicated `Overlay` project
  manages dashboard visualization.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  `Windows + RTX + NVIDIA SDK` dependence makes it highly vendor-specific; the
  repo remains an active `WIP` rather than a finished consumer product.
- What to inspect next:
  overlay-assisted alignment flow, confidence thresholds, and how much of the
  tracker smoothing logic is reusable outside NVIDIA's SDK path.

## `chnoblouch/aethervr`

- GitHub:
  [chnoblouch/aethervr](https://github.com/chnoblouch/aethervr)
- What it is:
  a custom `OpenXR` runtime that uses a webcam plus a Python tracker to fake an
  HMD and controllers without real VR hardware.
- Why it matters:
  it is the clearest public example in the repo so far of a `headsetless camera
  runtime`, not just a null-driver recipe.
- Interesting ideas:
  split the system into a `runtime` and a `tracker` connected over local TCP;
  let the GUI set itself as the active system OpenXR runtime; use gesture
  recognition to synthesize controller buttons and thumbstick behavior.
- Interesting implementation choices:
  the runtime lives in a separate `openxr_runtime` tree and is implemented in
  `Banjo`; the Python tracker owns MediaPipe head/hand tracking, gesture
  mapping, and GUI; `runtime_connection.py` defines a binary TCP protocol for
  runtime info, image registration, image presentation, and tracking state;
  `system_openxr_config.py` handles Windows registry and Linux XDG runtime
  registration.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  explicitly a `proof of concept`; hand tracking is unstable; head position is
  still limited; the runtime code is substantial and not fully exhausted by one
  pass.
- What to inspect next:
  pose prediction and head-position strategy, runtime graphics interop, and how
  far this pattern could go as a repeatable `headsetless QA harness`.

## Cross-wave synthesis

Wave 13 made the `vision-driven tracking` branch of `VR-apps-lab` much denser
and more coherent:

- `Service-backed hand drivers`
  became clearer through `driver_ultraleap`, which shows a mature hardware
  service -> SteamVR driver path with extra input injection and optional elbow
  devices.
- `Foreign-runtime hand bridges`
  became much more concrete through `HandOfLesser`, which connects OpenXR hand
  tracking, SteamVR controller/skeletal output, and VRChat-facing behaviors in
  one coordinated app-plus-driver system.
- `Camera CV sidecars with backend choice`
  became a distinct sub-pattern through `Mediapipe-VR-Fullbody-Tracking` and
  the smaller `HandCameraDriver`, where one vision pipeline can feed either a
  SteamVR path or a non-SteamVR fallback such as OSC.
- `Legacy app to plugin platform migration`
  became visible through the `KinectToVR -> Amethyst` progression, which is
  useful as both a product and architecture lesson.
- `Headsetless camera runtimes`
  became a real category through `aethervr`, which goes beyond null-driver
  tricks and exposes a runtime-plus-tracker split with explicit registration and
  image transport.

## Most reusable methods clarified by this wave

- `service-backed hand driver with documented external input injection`
- `OpenXR hand-tracking bridge into SteamVR and VRChat`
- `camera-tracking sidecar with switchable SteamVR and OSC backends`
- `plugin-based tracking host with device and service contracts`
- `headsetless camera runtime with runtime/tracker TCP split`

## Best follow-up work after this wave

1. deepen `Nordskog/HandOfLesser`, especially driver/app synchronization and
   controller-hooking behavior;
2. compare `KinectToVR/KinectToVR` and `KinectToVR/Amethyst` as one
   `legacy app -> modular platform` story;
3. compare `ju1ce/Mediapipe-VR-Fullbody-Tracking`,
   `Wunder-Wulfe/NVIDIA-BodyTracking`, and `chnoblouch/aethervr` as one
   `camera-driven tracking backend` family;
4. inspect whether `driver_ultraleap` and `HandOfLesser` can sharpen a reusable
   `SteamVR hand-input bridge` template;
5. treat `NovaAshwolfDev/HandCameraDriver` as a low-confidence but still useful
   cautionary node unless a healthier successor appears.
