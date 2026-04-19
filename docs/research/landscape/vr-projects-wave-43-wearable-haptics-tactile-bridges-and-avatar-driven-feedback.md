# VR Projects Wave 43: Wearable Haptics, Tactile Bridges, and Avatar-Driven Feedback

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `wearable haptics`, `tactile bridge sidecars`, and
  `avatar-driven feedback systems`.

## Why this wave exists

`VR-apps-lab` already had tracker bridges, expressive-input families, and some
avatar-facing automation tools, but one tactile branch was still too diffuse:

- sidecars that translate avatar or `OSC` events into wearable haptic systems;
- editor tooling that prepares avatar content for wearable feedback;
- firmware and hardware reference stacks for DIY tactile wearables;
- bridge apps that connect avatar events to alternate devices or actuator
  ecosystems.

This wave exists to make
`wearable haptics, tactile bridges, and avatar-driven feedback`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with wearable-haptics, VRChat `OSC`, and tactile-hardware
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `OpenShock/ShockOSC` | Strong donor for a configurable wearable-haptics router with grouped outputs and change-tracked OSC values |
| `bhaptics/VRChatOSC` | Strong donor for Unity-side avatar setup tooling that injects bHaptics-specific animator and parameter assets |
| `senseshift/senseshift-firmware` | Strong donor for the firmware half of a modular DIY tactile wearable platform |
| `senseshift/senseshift-hardware` | Strong donor for the hardware-reference half of the same tactile platform |
| `Z4urce/VRC-Haptic-Pancake` | Focused donor for bridging VRChat or Resonite signals into haptic or pulse-style outputs |
| `lebaston100/vrc-patpatpat` | Strong donor for solving sparse avatar contact inputs into richer haptic placement across actuators |
| `shadorki/vrc-owo-suit` | Focused product reference for mapping avatar contact patterns into OWO suit intensity groups |
| `Python1320/vrcjoycon` | Focused donor for using alternative consumer devices as avatar-facing haptic bridges |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `OpenShock/OpenShock` | Broader platform context around the haptics ecosystem, but the VR-facing bridge lessons in this wave were clearer in `ShockOSC` itself |

## Deep-pass notes by project

## `OpenShock/ShockOSC`

- GitHub:
  [OpenShock/ShockOSC](https://github.com/OpenShock/ShockOSC)
- What it is:
  a desktop module that groups wearable outputs, exposes settings and debug
  tabs, and bridges VRChat-facing `OSC` into hardware behavior.
- Why it matters:
  it is the clearest donor in the repo for
  `wearable-haptics bridge with change-tracked outputs and grouped routing`.
- Interesting ideas:
  group outputs by hardware behavior; expose settings, chatbox, and debug
  surfaces in one host; track only changed `OSC` parameters to avoid wasteful
  update patterns.
- Interesting implementation choices:
  `ShockOSCModule.cs`,
  `ShockOscConfig.cs`, and
  `ChangeTrackedOscParam.cs`
  make the `observe avatar signal -> track changes -> apply grouped haptic
  actions` flow explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  ecosystem-specific assumptions remain, but the routing model generalizes.
- What to inspect next:
  keep it visible whenever a future branch needs
  `avatar-facing hardware groups with a real settings surface`.

## `bhaptics/VRChatOSC`

- GitHub:
  [bhaptics/VRChatOSC](https://github.com/bhaptics/VRChatOSC)
- What it is:
  a Unity package that injects avatar-side setup for bHaptics-driven VRChat
  wearables.
- Why it matters:
  it is the clearest donor in the repo for
  `editor-side avatar setup tooling for wearable haptics`.
- Interesting ideas:
  move repetitive avatar setup into editor tooling; generate or inject the
  needed assets instead of relying on manual wiring; keep the runtime bridge and
  avatar content relationship explicit.
- Interesting implementation choices:
  `bHapticsOSCIntegration.cs` and
  `bAvatar.cs`
  make the `editor-time avatar setup -> wearable-specific parameters and
  animator content` path explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  vendor-specific target narrows direct reuse, but the editor tooling method is
  strong.
- What to inspect next:
  keep it visible whenever a future branch needs `avatar authoring helpers` for
  a hardware ecosystem.

## `senseshift/senseshift-firmware`

- GitHub:
  [senseshift/senseshift-firmware](https://github.com/senseshift/senseshift-firmware)
- What it is:
  a PlatformIO-based firmware stack for DIY tactile wearables that targets
  multiple hardware and protocol paths.
- Why it matters:
  it is the clearest firmware donor in the repo for
  `DIY tactile wearable platform design`.
- Interesting ideas:
  support multiple hardware environments in one firmware tree; keep the
  firmware branch reusable even when higher-level host software changes.
- Interesting implementation choices:
  `platformio.ini`
  and the repo's modular environment layout make the
  `board or protocol variant -> shared tactile logic` split visible.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  the full product lesson only becomes complete when paired with the hardware
  reference repo.
- What to inspect next:
  keep it paired with `senseshift-hardware` whenever a future branch needs a
  `firmware plus fabrication` donor line.

## `senseshift/senseshift-hardware`

- GitHub:
  [senseshift/senseshift-hardware](https://github.com/senseshift/senseshift-hardware)
- What it is:
  the PCB, schematic, and hardware-reference companion to the SenseShift
  firmware ecosystem.
- Why it matters:
  it complements the firmware repo by making the `hardware donor surface`
  explicit rather than implicit.
- Interesting ideas:
  document the physical platform alongside firmware; keep fabrication artifacts
  versioned and inspectable; treat hardware as a first-class part of the donor
  story.
- Interesting implementation choices:
  the repo keeps fabrication and board assets separate enough that the
  `physical platform reference` can be studied independently of firmware.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is a hardware donor more than a software donor, so its main value is in
  system completeness.
- What to inspect next:
  keep it tied to the firmware repo whenever `VR-apps-lab` needs a realistic
  `hardware plus firmware` comparison node.

## `Z4urce/VRC-Haptic-Pancake`

- GitHub:
  [Z4urce/VRC-Haptic-Pancake](https://github.com/Z4urce/VRC-Haptic-Pancake)
- What it is:
  a bridge app that maps VRChat `OSC` or Resonite websocket inputs into haptic
  or pulse-style output targets.
- Why it matters:
  it is one of the clearest donors in the repo for
  `thin bridge app between avatar consumers and external haptic hardware`.
- Interesting ideas:
  accept more than one avatar-facing transport; keep the bridge host lightweight
  and GUI-driven; reuse existing desktop protocols rather than owning the whole
  hardware stack.
- Interesting implementation choices:
  `BridgeApp/main.py`
  makes the `avatar signal source -> bridge normalization -> output hardware`
  path explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  the exact output devices vary, so the strongest lesson is the bridge pattern
  itself.
- What to inspect next:
  keep it visible whenever a future branch needs `multi-transport haptic
  bridge` ideas.

## `lebaston100/vrc-patpatpat`

- GitHub:
  [lebaston100/vrc-patpatpat](https://github.com/lebaston100/vrc-patpatpat)
- What it is:
  a bridge that uses sparse avatar contact receivers and solves them into richer
  haptic placement across actuators.
- Why it matters:
  it is the clearest donor in the repo for
  `sparse avatar contact solving into richer multi-actuator feedback`.
- Interesting ideas:
  do not require dense authoring everywhere; infer a richer output from sparse
  receiver placement; treat solver logic as the main product value, not only
  the hardware endpoint.
- Interesting implementation choices:
  `Solver.py`,
  `VrcConnector.py`, and
  `main.py`
  make the `receive sparse avatar contacts -> solve placement -> dispatch
  actuator outputs` path explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the solver is the clearest donor; the rest of the product shell is secondary.
- What to inspect next:
  keep it visible whenever a future branch needs
  `contact-to-actuator inference` instead of direct one-to-one mappings.

## `shadorki/vrc-owo-suit`

- GitHub:
  [shadorki/vrc-owo-suit](https://github.com/shadorki/vrc-owo-suit)
- What it is:
  a focused VRChat-to-OWO integration that maps avatar contact patterns into
  suit intensity groups.
- Why it matters:
  it is a strong product reference for a
  `narrow hardware-specific wearable bridge`.
- Interesting ideas:
  keep the runtime story simple; pair avatar contact authoring with a small
  desktop executable; express hardware behavior through understandable intensity
  groups.
- Interesting implementation choices:
  the repo emphasizes the `avatar setup plus desktop executable` shape over a
  broad platform story, which is exactly what makes it a useful comparison node.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  narrow device targeting means the strongest reuse lesson is product framing
  rather than architecture.
- What to inspect next:
  compare against `VRChatOSC` and `ShockOSC` whenever a future branch needs to
  separate `avatar authoring`, `bridge host`, and `device grouping`.

## `Python1320/vrcjoycon`

- GitHub:
  [Python1320/vrcjoycon](https://github.com/Python1320/vrcjoycon)
- What it is:
  a bridge that uses Joy-Con input and rumble as a VRChat or ChilloutVR-facing
  haptic side path.
- Why it matters:
  it is a good comparison node for
  `nontraditional consumer hardware reused as a tactile bridge`.
- Interesting ideas:
  reuse cheap consumer hardware; pair remapping with avatar-facing logic; keep
  the bridge focused instead of building a full platform.
- Interesting implementation choices:
  `src/main.py`
  makes the `consumer controller -> local bridge logic -> avatar-facing haptic
  behavior` path explicit.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  narrower than the wearable ecosystems above, but still valuable as a
  `thin bridge` comparison node.
- What to inspect next:
  keep it visible whenever a future branch needs
  `consumer-device repurposing` rather than dedicated wearables.

## Main takeaways from Wave 43

- `Wearable haptics` are now a distinct family, not just an odd corner of
  avatar automation.
- The strongest split in this family is:
  - `desktop router to wearable hardware groups`
  - `editor-side avatar setup tooling`
  - `DIY firmware platform`
  - `hardware reference platform`
  - `thin bridge app across multiple transports`
  - `contact-to-actuator solver`
  - `narrow hardware-specific integration`
  - `consumer-device repurposing`
- The most reusable lesson is that tactile tooling works best when the family is
  separated into `authoring`, `bridge`, `solver`, and `hardware platform`
  layers instead of one indistinct haptics bucket.

## Reusable methods clarified by this wave

- `Wearable-haptics bridge with grouped outputs and change-tracked OSC routing`
- `Sparse avatar contact solving into richer multi-actuator haptic placement`
- `DIY tactile wearable platform split across firmware and hardware-reference repos`

## Recommended next moves after this wave

1. Keep `ShockOSC` visible as the main donor for
   `wearable router plus grouped hardware behavior`.
2. Keep `vrc-patpatpat` visible as the clearest donor for
   `contact-to-actuator solver logic`.
3. Treat `senseshift-firmware` and `senseshift-hardware` as a paired donor line
   whenever a future branch needs realistic `DIY tactile wearable` references.
4. Use `VRChatOSC`, `vrc-owo-suit`, and `vrcjoycon` as comparison nodes for
   `editor tooling`, `narrow hardware bridge`, and
   `repurposed consumer-device bridge` respectively.
