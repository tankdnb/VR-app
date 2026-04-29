# VR Projects Wave 103: VRChat Avatar Text, Speech, Translation, and Viseme Sidecars

- Date: `2026-04-30`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat avatar text`, `speech`, `translation`, and `viseme sidecars`.

## Why this wave exists

`VR-apps-lab` already tracked some text and chatbox tooling, but it needed
clearer coverage of
`the creator-facing speech stack where STT, TTS, translation, overlays, avatar
text, and viseme timing meet`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with avatar text, TTS, translation, overlay, and viseme
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `VRCWizard/TTS-Voice-Wizard` | Strong donor for a queue-based speech and translation hub with broad VRChat-facing outputs |
| `YusufOzmen01/kikitan-translator` | Strong donor for a hybrid Tauri plus overlay translator sidecar |
| `met4citizen/HeadTTS` | Strong donor for viseme-aware TTS substrate that works in-browser or through a server |
| `Frosty704/Billboard` | Valuable product reference for an avatar-visible speech surface built on avatar-text substrate |

## Comparison nodes already tracked outside the main shortlist

- `yum-food/TaSTT`
- `killfrenzy96/KillFrenzyAvatarText`
- `I5UCC/VRCTextboxSTT`

These already mattered in the repo, but this wave focused on new speech-hub,
translation, viseme, and avatar-surface donors rather than redoing older text
lines from scratch.

## Deep-pass notes by project

## `VRCWizard/TTS-Voice-Wizard`

- GitHub:
  [VRCWizard/TTS-Voice-Wizard](https://github.com/VRCWizard/TTS-Voice-Wizard)
- What it is:
  a large Windows speech hub that combines STT, TTS, translation, OSC fan-out,
  chatbox text, avatar text, media helpers, and device integrations.
- Why it matters:
  it is the clearest donor in this wave for
  `speech and translation as one operator-controlled sidecar platform`.
- Interesting ideas:
  queue TTS messages instead of speaking immediately; listen to VRChat OSC
  state to trigger speech workflows; support multiple downstream outputs rather
  than only one avatar or chatbox surface.
- Interesting implementation choices:
  `TTSMessageQueue.cs`
  turns speech into a queueing and splitting system with explicit settings
  bundles; `VRChatListener.cs`
  consumes avatar state and AFK or speech triggers from VRChat OSC; the
  surrounding service split treats recognition, translation, synthesis, and
  integrations as separate layers.
- Code donor value:
  very high.
- Product reference value:
  very high.
- Architecture reference value:
  high.
- Caveats:
  it is broad enough that later work could still isolate media control, device
  telemetry, and avatar-text branches more deeply.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `speech hub`
  donor.

## `YusufOzmen01/kikitan-translator`

- GitHub:
  [YusufOzmen01/kikitan-translator](https://github.com/YusufOzmen01/kikitan-translator)
- What it is:
  a translator sidecar that combines a React or Tauri desktop shell, Rust OSC
  output, and a C# OpenVR image overlay helper.
- Why it matters:
  it is the clearest donor in this wave for
  `multi-surface translation tooling where desktop UI, OSC, and overlay output all matter`.
- Interesting ideas:
  keep recognizer and desktop-capture logic in one operator-facing surface; let
  Rust handle OSC egress; show translated or recognized content inside VR
  through a simple image overlay queue.
- Interesting implementation choices:
  `Kikitan.tsx`
  coordinates recognizer choice, VAD, capture, notification, and output flow;
  `data_out.rs`
  keeps OSC output minimal and explicit; `OpenVROverlay.cs`
  shows a timed image-queue overlay pattern where generated content is saved to
  a temp file and displayed in front of the HMD.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  some of the value sits in integration glue rather than in one deep internal
  algorithm.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `translation sidecar with overlay output`
  donor.

## `met4citizen/HeadTTS`

- GitHub:
  [met4citizen/HeadTTS](https://github.com/met4citizen/HeadTTS)
- What it is:
  a JavaScript TTS substrate that outputs audio plus phoneme timestamps and
  Oculus visemes, either in-browser or through a Node server.
- Why it matters:
  it is the clearest donor in this wave for
  `viseme-aware TTS as reusable substrate rather than as one monolithic desktop app`.
- Interesting ideas:
  keep one client API that can prefer WebGPU, WASM, or WebSocket server
  endpoints; split text into grapheme-safe chunks; expose viseme timing and
  audio output together so lip-sync and speech stay aligned.
- Interesting implementation choices:
  `headtts.mjs`
  manages endpoint preference, connection handling, split logic, queueing, and
  event emission; `headtts-node.mjs`
  turns the same model into a worker-backed Node WebSocket or REST server; the
  overall design treats `browser or server`
  as deployment choice instead of separate products.
- Code donor value:
  very high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  it currently targets English and newer browser or model constraints, so the
  most reusable value is in architecture and viseme-timing surface rather than
  universal coverage.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `viseme-aware speech engine`
  donor.

## `Frosty704/Billboard`

- GitHub:
  [Frosty704/Billboard](https://github.com/Frosty704/Billboard)
- What it is:
  a ready-to-install speech-bubble prefab for avatar text workflows built on
  KillFrenzyAvatarText and fed by tools such as `TTS-Voice-Wizard` or
  `VRCTextboxSTT`.
- Why it matters:
  it is the clearest product reference in this wave for
  `avatar-visible speech surface`
  instead of for speech recognition or TTS itself.
- Interesting ideas:
  keep the speech bubble pick-up-able and droppable in the world; design for
  fallback visibility when shaders or custom animation are hidden; make the
  speech surface customizable while staying parameter-budget aware.
- Interesting implementation choices:
  the public repo is heavier on prefab packaging and product documentation than
  on transparent code, but its requirements and README surface strong design
  constraints around parameter-space budgets, write-default expectations, world
  interaction, and visual fallbacks.
- Code donor value:
  medium.
- Product reference value:
  very high.
- Architecture reference value:
  medium.
- Caveats:
  it is more prefab and product reference than open code donor, so it stays
  stronger as a reference node than as a fully transparent implementation
  source.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `avatar-visible speech surface`
  reference or future public install automation appears.

## Main takeaways from Wave 103

- `avatar-facing speech tooling`
  is a coherent research branch, not just a thin extension of generic STT or
  chatbox tools.
- The strongest lesson from this wave is that the branch splits into at least
  four layers:
  `speech hub`,
  `translator sidecar`,
  `viseme-aware engine`,
  and
  `avatar-visible speech surface`.
- `HeadTTS`
  and `TTS-Voice-Wizard`
  are especially strong because they expose reusable speech substrate and
  sidecar architecture rather than only one end-user app.
- `Billboard`
  matters even with thinner code visibility because it captures real avatar UX
  constraints that the speech engines alone do not show.

## Reusable methods clarified by this wave

- `Queue-based multi-engine speech hub with VRChat listener triggers and OSC or chatbox or avatar-text fan-out`
- `Browser-or-server TTS pipeline with phoneme timestamps, viseme outputs, and WebSocket or WebWorker backends`
- `Translator shell that combines desktop UI, OSC output, and timed OpenVR image overlays`
- `World-droppable speech billboard prefab built on avatar-text parameter budgets and fallback visual states`

## Recommended next moves after this wave

1. Keep `TTS-Voice-Wizard`
   visible as the strongest current
   `speech hub`
   donor in the repository.
2. Keep `HeadTTS`
   visible as one of the clearest
   `viseme-aware TTS substrate`
   references in the repo.
3. Compare `TTS-Voice-Wizard`, `kikitan-translator`, and `HeadTTS`
   whenever future work needs a sharper split between
   `operator hub`,
   `translator sidecar`,
   and
   `speech engine`.
4. Keep `Billboard`
   visible as a strong
   `avatar-visible speech surface`
   product reference even though it is not the most transparent code donor in
   the wave.
