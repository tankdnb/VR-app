# VR Projects Wave 92: VRChat World Persistence, Inventory, Save-Manager Companions, and External-Data Bridges

- Date: `2026-04-21`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat world persistence`, `inventory helpers`, `save-manager companions`,
  and `external-data bridges`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of creator-facing media, UI, and
runtime helpers than of:

`how VRChat-adjacent systems keep or recover state when they need save slots, world inventory, or data flows that the platform does not expose directly`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VRChat persistence, save-manager, inventory, and
   external-data helper queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Nestorboy/NUSaveState` | Strong donor for avatar-encoded creator-world persistence and build-time slot materialization |
| `ChrisFeline/ToNSaveManager` | Strong product reference for a log-parsed save companion that fans state into notifications, OSC, WebSocket, and plugins |
| `TealOrangeCat/InventorySystem` | Strong donor for synced holster inventory and automatic pickup registration in VRChat worlds |
| `DarthShader/Udon-MIDI-Web-Helper` | Strong donor for terms-compliant external web and local-storage access from Udon via helper process plus MIDI |

## Deep-pass notes by project

## `Nestorboy/NUSaveState`

- GitHub:
  [Nestorboy/NUSaveState](https://github.com/Nestorboy/NUSaveState)
- What it is:
  a VRChat world persistence system that writes data into avatar parameters and
  reads it back through avatar bone rotations, with editor tooling for slot and
  instruction management.
- Why it matters:
  it is the clearest donor in this wave for
  `creator-world persistence that remains fully in-platform by encoding state through data avatars`.
- Interesting ideas:
  use data avatars as portable save carriers; separate runtime save or load flow
  from editor-side slot authoring; let one behaviour orchestrate writing
  stations, avatar pedestals, buffer pages, and callback events.
- Interesting implementation choices:
  `Scripts/U#/NUSaveState.cs`
  owns the runtime state machine, buffer preparation, avatar switching, and
  callback flow; `Scripts/Mono/NUSaveStateData.cs`
  materializes avatar slots into private runtime fields and buffer instruction
  arrays; `Scripts/Editor/NUSaveStateBuildCallback.cs`
  applies slot data on world builds and strips editor-only helper data after
  scene processing.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  this technique is very platform-specific and leans on avatar and parameter
  constraints, so it is best treated as a clever constrained-data donor rather
  than a general persistence baseline.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `pure in-platform persistence under tight platform limits`
  donor.

## `ChrisFeline/ToNSaveManager`

- GitHub:
  [ChrisFeline/ToNSaveManager](https://github.com/ChrisFeline/ToNSaveManager)
- What it is:
  a Windows save companion for one VRChat world that watches logs, stores save
  history locally, emits notifications, exposes a local WebSocket API, and
  supports JavaScript extensions plus OSC or chatbox outputs.
- Why it matters:
  it is the clearest product reference in this wave for
  `world-specific save manager as a sidecar application rather than a world prefab`.
- Interesting ideas:
  treat log parsing as the stable recovery surface; keep the save timeline in a
  local database; expose the recovered game state to several outputs at once:
  XSOverlay-style notifications, Discord webhook backup, OSC parameters,
  chatbox strings, local WebSocket clients, and JS plugins.
- Interesting implementation choices:
  `Program.cs`
  centralizes application boot, local data location, update flow, and window
  lifetime; `Utils/LogParser/LogWatcher.cs`
  maintains incremental log contexts with stored offsets and validation;
  `Utils/API/WebSocketAPI.cs`
  exposes loopback WebSocket events for clients; `Utils/JSPlugins/JSEngine.cs`
  builds a plugin host with queued event dispatch and a bounded JS runtime.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  it is tightly scoped to a specific world and product context, so the best
  reusable lessons are its sidecar shape, parser model, and fan-out surfaces
  rather than its domain data model.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `world-companion save manager with scripting and realtime event outputs`
  reference.

## `TealOrangeCat/InventorySystem`

- GitHub:
  [TealOrangeCat/InventorySystem](https://github.com/TealOrangeCat/InventorySystem)
- What it is:
  a VRChat world holster inventory that auto-registers pickupable objects,
  assigns them to players, and manages holster occupancy through synced owner
  arrays instead of manual per-item setup.
- Why it matters:
  it is the clearest donor in this wave for
  `creator-world inventory as a reusable ownership and holster-management layer`.
- Interesting ideas:
  precompute the inventory graph at build or edit time; identify holsterable
  pickups by layer and `VRC_Pickup` presence; sync only the player or item
  ownership mapping while local holsters manage placement, haptics, and access.
- Interesting implementation choices:
  `SetupInventory.cs`
  scans the scene for holsters and pickups, caches rigidbody and respawn data,
  and hooks both edit-mode exit and VRC build callbacks; `Inventory.cs`
  stores the synced per-item player ownership array and drives networked
  drop or respawn behaviour; `Holster.cs`
  handles local trigger interactions, hand-collider gating, haptics, and item
  assignment without requiring per-pickup author scripting.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the model is optimized for holsters and pickups, not for arbitrary nested RPG
  inventory semantics.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `synced world inventory or holster utility`
  donor.

## `DarthShader/Udon-MIDI-Web-Helper`

- GitHub:
  [DarthShader/Udon-MIDI-Web-Helper](https://github.com/DarthShader/Udon-MIDI-Web-Helper)
- What it is:
  an external Windows helper plus Udon-side handler that lets VRChat worlds ask
  for HTTP, WebSocket, browser-open, and local-storage operations through log
  commands and virtual MIDI frames.
- Why it matters:
  it is the clearest donor in this wave for
  `terms-compliant external helper that extends creator worlds without modifying the client`.
- Interesting ideas:
  keep the untrusted world on the log-printing side and move web execution into
  a local helper; use MIDI as the response transport back into the world;
  reserve one prioritized loopback connection for status; support local
  persistence through the same bridge; expose a single Udon behaviour that
  fronts all requests.
- Interesting implementation choices:
  `Udon-MIDI-Web-Helper/UdonMIDIWebHelper.cs`
  boots log capture and MIDI handling in a dedicated process;
  `Udon-MIDI-Web-Handler/UdonMIDIWebHandler.cs`
  owns connection IDs, request APIs, ping or ready flow, local storage calls,
  and world callbacks; the protocol explicitly budgets around frame-size and
  crash limits while keeping one loopback channel reserved for status.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  very high.
- Caveats:
  this is security-sensitive and Windows-specific; its README is also explicit
  about the threat model and abuse risks around log injection and world trust.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `external sidecar over constrained in-world transport`
  donor.

## Main takeaways from Wave 92

- `VRChat persistence and external data`
  now splits more cleanly into:
  - in-platform avatar-carried save state;
  - out-of-world log-parsed save companions;
  - synced runtime inventory ownership systems;
  - external helper bridges for web and local data access.
- The strongest lesson from this wave is that
  `persistence in creator worlds`
  is not one implementation lane. It can live entirely in-world, entirely out
  of world, or in a bridge between the two.
- Another strong lesson is that
  `sidecar companions`
  become especially valuable when they fan recovered state into several other
  surfaces such as notifications, webhooks, WebSocket clients, OSC, or scripts.

## Reusable methods clarified by this wave

- `Avatar-parameter persistence through data avatars, parameter writers, and finger-bone readback`
- `World save companion that parses logs and fans state into local history, notifications, OSC, WebSocket, and plugins`
- `Auto-registered holster inventory with per-item owner mapping and hand-collider access control`
- `Terms-compliant external web and local-storage bridge using log commands plus virtual MIDI`

## Recommended next moves after this wave

1. Keep `NUSaveState` visible as one of the strongest
   `in-world constrained persistence`
   donors in the creator-world branch.
2. Treat `ToNSaveManager` as a strong
   `world-specific companion app`
   reference whenever future work needs log parsing plus output fan-out.
3. Use `InventorySystem` as a baseline donor whenever future work needs
   `synced holster inventory and pickup ownership`.
4. Revisit `Udon-MIDI-Web-Helper` whenever a future pass needs sharper work on
   `external helper threat models, local storage, or bridge transport`.
