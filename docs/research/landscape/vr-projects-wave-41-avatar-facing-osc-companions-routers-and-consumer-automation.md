# VR Projects Wave 41: Avatar-Facing OSC Companions, Routers, and Consumer Automation

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `avatar-facing OSC companions`, `routing sidecars`, and
  `consumer automation utilities`.

## Why this wave exists

`VR-apps-lab` already had tracker bridges and direct `OSC` export references,
but one user-facing branch was still too mixed together:

- routers that sit between VRChat and other desktop or consumer systems;
- plugin hosts that turn headset telemetry into structured `OSC` signals and
  side effects;
- small tools that translate avatar parameters into audio controls,
  state replay, locomotion behavior, or physical device actions.

This wave exists to make
`avatar-facing OSC companions, routers, and consumer automation sidecars`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VRChat `OSC`, router, automation, and consumer-bridge
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `OscToys/OscGoesBrrr` | Strong donor for a broad Electron-based OSC companion platform with typed IPC, diagnostics, and `OSCQuery` services |
| `valuef/VRCRouter` | Focused donor for configuration-driven OSC routing with sidecar lifecycle and VRChat gating |
| `Sergey004/Quest2-VRC` | Strong donor for a plugin-based Quest telemetry host with modular consumers and `OSC` fan-out |
| `I5UCC/VRCMeeter` | Focused donor for mapping avatar parameters into Voicemeeter actions |
| `I5UCC/VRCAvatarParameterSync` | Focused donor for snapshotting and restoring avatar parameter sets across avatar changes |
| `ZenithVal/OSCLeash` | Focused donor for turning avatar or physbone state into desktop-side control logic |
| `ZenithVal/OSCLock` | Strong product reference for using avatar parameters to drive a real-world Bluetooth actuator workflow |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `lenoobkinda/VRCOSCUtils` | Useful overlap node, but weaker as a mainline donor than the clearer router, telemetry-host, and automation-sidecar repos above |

## Deep-pass notes by project

## `OscToys/OscGoesBrrr`

- GitHub:
  [OscToys/OscGoesBrrr](https://github.com/OscToys/OscGoesBrrr)
- What it is:
  a broad Electron and TypeScript companion platform that exposes a frontend,
  backend bridge, configuration services, diagnostics, and `OSCQuery`
  integration.
- Why it matters:
  it is the clearest donor in the repo for
  `broad avatar-facing OSC companion platform with typed desktop IPC`.
- Interesting ideas:
  keep a typed frontend/backend contract; expose diagnostics and routing as
  first-class UI surfaces; separate configuration services, transport, and
  discovery instead of collapsing everything into one script.
- Interesting implementation choices:
  `ipcContract.ts`,
  `bridge.ts`,
  `OscConnection.ts`,
  `ConfigService.ts`,
  `OscQueryHttpServerService.ts`, and
  `VrchatOscqueryService.ts`
  make the `desktop shell -> typed IPC -> OSC and OSCQuery services` split
  unusually explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broad platform scope means it is better classified as `Partially studied`
  than over-claimed as exhausted.
- What to inspect next:
  revisit when a future branch needs a deeper comparison of
  `desktop host + diagnostics surface + service backplane`.

## `valuef/VRCRouter`

- GitHub:
  [valuef/VRCRouter](https://github.com/valuef/VRCRouter)
- What it is:
  a focused router that forwards `OSC` routes, waits for VRChat when needed,
  launches sidecar apps, and handles cleanup or auto-close behavior.
- Why it matters:
  it is the clearest donor in the repo for
  `configuration-driven OSC router with companion lifecycle management`.
- Interesting ideas:
  model routes as presets; treat companion process startup as part of the
  routing product; optionally wait for the main VR consumer before activating
  routes.
- Interesting implementation choices:
  `Program.cs`
  makes the `load route preset -> optionally launch apps -> wait for VRChat ->
  route packets -> clean up on exit` flow explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  the architecture is intentionally narrow, so its strongest lesson is product
  sharpness rather than platform breadth.
- What to inspect next:
  keep it visible whenever a future branch needs a
  `router plus lifecycle sidecar`, not a broad multi-feature host.

## `Sergey004/Quest2-VRC`

- GitHub:
  [Sergey004/Quest2-VRC](https://github.com/Sergey004/Quest2-VRC)
- What it is:
  a plugin-based Quest telemetry host that pulls device information and fans it
  out through `OSC` and other desktop integrations.
- Why it matters:
  it is the clearest donor in the repo for
  `per-device telemetry host with plugin modules and OSC side effects`.
- Interesting ideas:
  keep device acquisition modular; load plugins dynamically; expose one headset
  telemetry surface to multiple consumers such as lighting, media, or status
  outputs.
- Interesting implementation choices:
  `PluginLoader.cs`,
  `IPlugin.cs`, and
  `OSC.cs`
  make the `Quest device data -> plugin dispatch -> OSC and side integrations`
  split explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  Quest-specific acquisition narrows hardware reach, but the plugin-host lesson
  generalizes well.
- What to inspect next:
  use it whenever a future branch needs `device telemetry plus modular
  consumers` rather than a single narrow desktop action.

## `I5UCC/VRCMeeter`

- GitHub:
  [I5UCC/VRCMeeter](https://github.com/I5UCC/VRCMeeter)
- What it is:
  a Python bridge that maps avatar parameters into Voicemeeter actions and
  presets with `OSCQuery` awareness.
- Why it matters:
  it is one of the cleanest donors for
  `avatar parameter -> external desktop action`.
- Interesting ideas:
  keep one desktop tool in sync with avatar state; use `OSCQuery` discovery
  instead of static assumptions; make the bridge legible and focused.
- Interesting implementation choices:
  `src/main.py`
  shows a tight `discover VRChat parameters -> watch state -> dispatch desktop
  audio actions` flow.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  narrow scope means it is mainly a strong method donor, not a broader platform
  reference.
- What to inspect next:
  keep it visible whenever a future path needs
  `avatar parameters as desktop automation triggers`.

## `I5UCC/VRCAvatarParameterSync`

- GitHub:
  [I5UCC/VRCAvatarParameterSync](https://github.com/I5UCC/VRCAvatarParameterSync)
- What it is:
  a small utility that snapshots selected avatar parameters and replays them
  after avatar changes.
- Why it matters:
  it is the clearest donor in the repo for
  `avatar-state mirror and replay across avatar swaps`.
- Interesting ideas:
  define a keep-list of parameters; use `OSCQuery` to rediscover the new avatar
  parameter surface; replay prior values only where meaningful.
- Interesting implementation choices:
  `src/main.py`
  makes the `observe selected parameters -> cache values -> rediscover target ->
  resend state` path explicit.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  a deliberately narrow tool, but that narrowness is also its strength.
- What to inspect next:
  reuse whenever a future branch needs `state continuity across runtime or
  avatar context changes`.

## `ZenithVal/OSCLeash`

- GitHub:
  [ZenithVal/OSCLeash](https://github.com/ZenithVal/OSCLeash)
- What it is:
  a sidecar that turns avatar or physbone stretch state into locomotion or
  control behavior using config-defined thresholds and optional `OSCQuery`.
- Why it matters:
  it shows the `avatar parameter as live control input` branch in a very
  explicit way.
- Interesting ideas:
  model avatar-driven behavior as thresholded control logic; keep config and
  data flow separate; treat avatar state as an external desktop input source.
- Interesting implementation choices:
  `OSCLeash.py` and
  `Controllers/DataController.py`
  show the `observe avatar parameter -> apply config thresholds -> drive local
  behavior` loop clearly.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  specialized product framing narrows reuse, but the control-loop method is
  still valuable.
- What to inspect next:
  compare with other `avatar state -> side effect` tools whenever a future
  branch needs more than simple toggles.

## `ZenithVal/OSCLock`

- GitHub:
  [ZenithVal/OSCLock](https://github.com/ZenithVal/OSCLock)
- What it is:
  a desktop utility that turns avatar state and timers into a physical
  Bluetooth lock workflow or similar actuator behavior.
- Why it matters:
  it is one of the clearest product references in the repo for
  `consumer automation sidecar with a real-world actuator`.
- Interesting ideas:
  let avatar parameters gate a timer-based workflow; bridge to physical
  Bluetooth hardware; preserve a usable desktop control path for configuration
  and safety.
- Interesting implementation choices:
  `Program.cs`,
  `VRChatConnector.cs`,
  `OSCTimer.cs`, and
  `ESmartLock*.cs`
  make the `avatar signal -> timer logic -> Bluetooth actuator` flow explicit.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  device specificity narrows direct reuse, but the broader
  `avatar-driven actuator sidecar` lesson is strong.
- What to inspect next:
  keep it visible whenever a future branch needs
  `avatar state -> consumer hardware or desktop automation`.

## Main takeaways from Wave 41

- `Avatar-facing OSC companions` are now a distinct family, not just a thin
  appendix to tracker export or social overlays.
- The strongest split in this family is:
  - `broad desktop companion platform`
  - `focused OSC router with sidecar lifecycle`
  - `plugin-based headset telemetry host`
  - `avatar parameter -> desktop action bridge`
  - `avatar-state persistence helper`
  - `consumer actuator sidecar`
- The most reusable lesson is that avatar parameters can act as a
  `general-purpose automation bus`, but only if routing, discovery, lifecycle,
  and safety are handled deliberately.

## Reusable methods clarified by this wave

- `Configuration-driven OSC router with companion-process lifecycle management`
- `Plugin-based device telemetry host with modular consumers and OSC side effects`
- `OSCQuery-aware avatar parameter bridge for desktop services, replay, and actuator control`

## Recommended next moves after this wave

1. Keep `VRCRouter` visible whenever a future branch needs
   `routing plus sidecar lifecycle`, not a broad platform.
2. Treat `Quest2-VRC` as the main donor for
   `plugin-based device telemetry hosts`.
3. Keep `VRCMeeter`, `VRCAvatarParameterSync`, `OSCLeash`, and `OSCLock`
   together as the clearest examples of
   `avatar state -> desktop or consumer action`.
4. Revisit `OscGoesBrrr` only when a future branch needs a deeper
   `desktop host + typed IPC + service backplane` comparison.
