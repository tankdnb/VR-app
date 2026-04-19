# VR Projects Wave 24: Accessibility Captions, Assistive Speech Surfaces, and Micro-HUD Utilities

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `accessibility captions`, `assistive speech surfaces`, and
  `micro-HUD accessibility utilities`.

## Why this wave exists

`VR-apps-lab` already had enough nodes to prove that accessibility is a real VR
utility family:

- captions are not a fringe experiment anymore;
- microphone-state overlays solve a real communication problem;
- speech-to-text can feed several downstream surfaces, not only one overlay.

What the repo still lacked was a coherent code-level synthesis showing the
strong architectural splits inside the family.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with caption, assistive HUD, and mic-state queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Vinventive/live-captions-vr` | Strong speech-to-text sidecar plus native OpenVR overlay split |
| `MochiDoesVR/OpenVRCaptions` | Strong Windows-native captions app with a dedicated SteamVR renderer |
| `ctobin1114/UniversalVR-CC` | Useful browser-first closed-caption host that relies on an existing VR overlay surface |
| `gt0777/VRCLiveCaptionsMod` | Important comparison node for app-internal speech-hook captions instead of external overlays |
| `I5UCC/VRCTextboxSTT` | Best multi-output local transcription utility in this family |
| `rrazgriz/VRCMicOverlay` | Strong micro-donor for mic-state-only accessibility HUDs |
| `matzman666/OpenVR-MicrophoneControl` | Useful dashboard-side accessibility/control overlay with OS audio integration |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `Beyley/eepyxr` | Strong comfort/assistive overlay reference, but not a new captions donor |
| `Otter-Co/TurnSignal` | Important comfort micro-utility, but outside the speech and captions center of this pass |

## Deep-pass notes by project

## `Vinventive/live-captions-vr`

- GitHub:
  [Vinventive/live-captions-vr](https://github.com/Vinventive/live-captions-vr)
- What it is:
  a local live-captions utility that runs speech recognition out of process and
  renders the result into a VR overlay.
- Why it matters:
  it is the clearest donor in the repo for
  `Python speech sidecar -> Unity/OpenVR overlay`.
- Interesting ideas:
  keep transcription local; separate the recognition stack from the overlay
  renderer; support both CPU and CUDA paths; keep message lifetime and fade
  logic inside the VR surface.
- Interesting implementation choices:
  `aiears.py` owns local audio capture and recognition plumbing, while
  `TextOverlay.cs` acts as the overlay-side TCP client, message queue, and
  timed fade surface.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the speech pipeline is Python-heavy and hardware-sensitive.
- What to inspect next:
  whether the message transport could be generalized beyond this project into a
  reusable caption-sidecar contract.

## `MochiDoesVR/OpenVRCaptions`

- GitHub:
  [MochiDoesVR/OpenVRCaptions](https://github.com/MochiDoesVR/OpenVRCaptions)
- What it is:
  a Windows-native captions utility built around Vosk and a SteamVR overlay.
- Why it matters:
  it is the strongest donor in this family for
  `desktop config shell + dedicated native overlay renderer`.
- Interesting ideas:
  use an ordinary desktop UI for settings and setup; keep the VR surface
  focused only on captions; expose font and color controls; treat captions as a
  real end-user utility, not only a prototype.
- Interesting implementation choices:
  `Core/ApplicationConfig.cs` centralizes caption settings, and
  `Renderer/D2DCaptionRenderer.cs` shows a clear `Direct2D -> OpenVR overlay`
  rendering path with a separate WPF configuration shell.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  strongest on Windows and on its chosen rendering stack.
- What to inspect next:
  how much of the Direct2D text-rendering path could be reused in future
  high-legibility overlay experiments.

## `ctobin1114/UniversalVR-CC`

- GitHub:
  [ctobin1114/UniversalVR-CC](https://github.com/ctobin1114/UniversalVR-CC)
- What it is:
  a browser-first live-caption service that transcribes desktop audio and
  exposes captions over a local web surface.
- Why it matters:
  it is a strong donor for `caption service first, VR surface second`.
- Interesting ideas:
  captions do not have to be rendered by a native VR overlay app; a local web
  control surface can be enough when paired with an existing overlay host such
  as `OVR Toolkit`.
- Interesting implementation choices:
  `flask-app/universalCC.py` uses Flask, SocketIO, and Vosk-backed audio
  capture threads, while the HTML templates provide the actual caption surface.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  this is not a native SteamVR overlay donor by itself.
- What to inspect next:
  whether `browser-first assistive surfaces` should become a separate product
  branch inside the broader accessibility family.

## `gt0777/VRCLiveCaptionsMod`

- GitHub:
  [gt0777/VRCLiveCaptionsMod](https://github.com/gt0777/VRCLiveCaptionsMod)
- What it is:
  a VRChat-specific live-captions mod.
- Why it matters:
  it is the clearest comparison node for
  `app-internal voice hook -> subtitle UI`, which is meaningfully different
  from an external overlay utility.
- Interesting ideas:
  capture audio from the app's own voice path; run recognition on decompressed
  voice data; keep profanity filtering and subtitle presentation close to the
  host application.
- Interesting implementation choices:
  `GameSpecific/VRChat/USpeakHooker.cs` hooks VRChat voice flow,
  `TranscribeWorker.cs` owns recognizer session work, and `SubtitleUi.cs`
  handles the in-app caption surface.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  host-app specificity limits direct reuse.
- What to inspect next:
  use it mainly as a reference for `app-integrated captions`, not as a generic
  overlay platform donor.

## `I5UCC/VRCTextboxSTT`

- GitHub:
  [I5UCC/VRCTextboxSTT](https://github.com/I5UCC/VRCTextboxSTT)
- What it is:
  a local speech-to-text utility with several output targets, including a
  SteamVR overlay.
- Why it matters:
  it is the strongest donor in the repo for
  `one local STT host -> many output surfaces`.
- Interesting ideas:
  do not tie transcription to one UI; let the same speech host feed VRChat,
  OSC, browser or overlay surfaces; keep hardware and compute-path selection
  explicit.
- Interesting implementation choices:
  `src/transcribe.py` owns backend loading and compute choices,
  `src/ovr.py` shows overlay creation and action-manifest plumbing, and
  `src/osc.py` plus the rest of the tree make the multi-output architecture
  very explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broader than a pure accessibility overlay because it also targets VRChat and
  social workflows.
- What to inspect next:
  whether the `multi-output local STT host` pattern deserves its own reuse
  plan.

## `rrazgriz/VRCMicOverlay`

- GitHub:
  [rrazgriz/VRCMicOverlay](https://github.com/rrazgriz/VRCMicOverlay)
- What it is:
  a minimal overlay that exposes microphone state inside VR.
- Why it matters:
  it is a strong micro-donor for `one strong status hint` UX.
- Interesting ideas:
  keep the overlay tiny; watch the microphone state directly; rely on config
  and a simple loop instead of a broad utility shell.
- Interesting implementation choices:
  `MicListener.cs`, `OpenVRUtilities.cs`, and `Configuration.cs` make the
  `audio sense -> tiny overlay` path unusually clean and easy to study.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  intentionally narrow.
- What to inspect next:
  compare it with other mic-state and voice-status helpers to isolate the
  minimum useful accessibility micro-overlay pattern.

## `matzman666/OpenVR-MicrophoneControl`

- GitHub:
  [matzman666/OpenVR-MicrophoneControl](https://github.com/matzman666/OpenVR-MicrophoneControl)
- What it is:
  a dashboard-side microphone control overlay integrated with OS audio APIs.
- Why it matters:
  it is a useful donor for `dashboard accessibility/control overlay with real
  system integration`.
- Interesting ideas:
  expose mute and push-to-talk functionality directly inside VR; integrate with
  the Windows audio endpoint; keep the overlay tied to a high-value
  communication problem.
- Interesting implementation choices:
  `src/overlaycontroller.cpp` and `overlaywidget.cpp` show the overlay-side UI,
  while `audiomanagerwindows.cpp` makes the OS-audio boundary explicit.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  now mainly useful as a historical donor because the functionality later moved
  into `OpenVR-AdvancedSettings`.
- What to inspect next:
  compare its audio-control boundary with other dashboard-side utility surfaces
  when building accessibility or communication helpers.

## Main takeaways from Wave 24

- `Accessibility overlays` are now clearly a first-class product family in the
  repository.
- The strongest split inside the family is:
  - `native caption overlay renderer`
  - `multi-output local STT host`
  - `browser-first assistive surface`
  - `app-internal voice-hook captions`
  - `mic-state or communication-status micro-HUD`
- Very small repos still matter when they solve one assistive problem
  unusually well, as seen in `VRCMicOverlay`.

## Reusable methods clarified by this wave

- `Local speech-recognition sidecar feeding a native VR overlay`
- `Browser-first assistive surface that relies on an existing overlay host`
- `Multi-output local transcription utility with VR overlay as one consumer`

## Recommended next moves after this wave

1. Treat `accessibility overlays` as a real family, not as leftover overlay
   miscellaneous.
2. Use `OpenVRCaptions` and `live-captions-vr` as the main donors for native
   caption rendering paths.
3. Use `VRCTextboxSTT` as the main donor for multi-output local speech-host
   architecture.
4. Keep `UniversalVR-CC` and `VRCLiveCaptionsMod` as comparison nodes for
   `browser-hosted captions` and `app-integrated captions`, not as the same
   product category.
