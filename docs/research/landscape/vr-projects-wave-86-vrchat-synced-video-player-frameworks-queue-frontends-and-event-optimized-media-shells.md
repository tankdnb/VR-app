# VR Projects Wave 86: VRChat Synced Video Player Frameworks, Queue Frontends, and Event-Optimized Media Shells

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat synced video player frameworks`, `queue frontends`, and
  `event-optimized media shells`.

## Why this wave exists

`VR-apps-lab` already had creator-facing audio and synced media coverage, but
it still lacked a cleaner answer to:

`what the best creator-side video donors look like when sync, playlists, queue flow, audio routing, and screen surfaces split into reusable modules`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VRChat video player, Udon sync player, and creator media
   frontend queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `vrctxl/VideoTXL` | Strong donor for a package-level creator-side video system with separate video, audio, and screen managers |
| `UdonVR/UdonVideoplayer` | Strong donor for a compact owner-synced Udon video player with backend switching and resync logic |
| `koorimizuw/YamaPlayer` | Strong product and architecture reference for a modular creator-facing player with playlists, handlers, and multiple integration modules |

## Deep-pass notes by project

## `vrctxl/VideoTXL`

- GitHub:
  [vrctxl/VideoTXL](https://github.com/vrctxl/VideoTXL)
- What it is:
  a package-based VRChat video system that separates video playback, screen
  management, audio routing, sync logic, and auxiliary integrations.
- Why it matters:
  it is the clearest donor in this wave for
  `prefab shell plus manager split`
  in a creator-side media system.
- Interesting ideas:
  treat video, audio, and screen surfaces as distinct manager domains; keep
  sync-aware and local-only playback variants visible; integrate output-side
  systems such as AudioLink and related visual pipelines without collapsing the
  core player abstraction.
- Interesting implementation choices:
  `TXLVideoPlayer.cs`
  and `SyncPlayer.cs`
  keep playback and synchronization separate while `VideoManager.cs`,
  `AudioManager.cs`, and `ScreenManager.cs`
  expose a clearer subsystem split than most older Udon video shells.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broad enough that some integration modules remain outside this first pass.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `modular creator-side video system`
  donor.

## `UdonVR/UdonVideoplayer`

- GitHub:
  [UdonVR/UdonVideoplayer](https://github.com/UdonVR/UdonVideoplayer)
- What it is:
  a compact synchronized Udon video player with backend switching, ownership,
  late-join support, and re-sync heuristics.
- Why it matters:
  it is the clearest donor in this wave for
  `single-script synced player core`
  rather than a broader package ecosystem.
- Interesting ideas:
  keep ownership and sync state concentrated in one obvious place; support
  multiple video backends while keeping the sync shell stable; repair state for
  late joiners without requiring a much larger framework.
- Interesting implementation choices:
  `UdonSyncVideoPlayer.cs`
  and `PlayMovie.cs`
  show the owner-routed timing flow, backend split, and re-sync path more
  directly than many newer but larger repos.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  narrower and older than newer package ecosystems, but useful precisely
  because the sync core is easier to see.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `lean synced Udon player`
  baseline.

## `koorimizuw/YamaPlayer`

- GitHub:
  [koorimizuw/YamaPlayer](https://github.com/koorimizuw/YamaPlayer)
- What it is:
  a broad creator-facing player package with playlist, history, sync, handler,
  localization, and module surfaces.
- Why it matters:
  it is the clearest product and architecture reference in this wave for
  `modular creator-facing media frontend`
  rather than only one sync script.
- Interesting ideas:
  separate controller partials by concern; model handlers and modules as an
  extension surface; keep playlist, queue, history, and integration modules
  visible as first-class product features instead of hiding them behind one
  monolithic player component.
- Interesting implementation choices:
  `Controller.Sync.cs`
  and `Controller.Playlist.cs`
  reveal controller decomposition while `PlayerHandler.cs`,
  `YamaPlayer.cs`, and the `Modules/`
  tree show a broader system that can adapt to several creator-side add-ons and
  workflows.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broad enough that this pass remains only
  `Partially studied`
  for the full module ecosystem.
- What to inspect next:
  revisit when a future pass needs deeper coverage of handler abstraction,
  module boundaries, and creator-side playlist workflows.

## Main takeaways from Wave 86

- `Creator-side video systems`
  now split more cleanly into:
  - `manager-split package with separate video, audio, and screen domains`
  - `lean owner-synced Udon player core`
  - `broad modular creator-facing frontend with playlists and handlers`
- The strongest lesson from this wave is that
  `synced video shell`
  is not only a timing problem. The reusable value often sits in how sync,
  queue, handler, screen, and audio concerns are separated.
- Another strong lesson is that
  `event or creator workflows`
  matter as much as the playback engine itself when a repo is intended for
  shared virtual spaces.

## Reusable methods clarified by this wave

- `Prefab-level creator-side video system split into video manager, audio manager, and screen manager`
- `Owner-synced Udon video player with backend switching, late-join sync, and re-sync heuristics`
- `Modular creator-facing media frontend with playlist, queue, history, and handler extension surfaces`

## Recommended next moves after this wave

1. Treat `VideoTXL` as one of the strongest creator-side video donors now
   present in the repository.
2. Keep `UdonVideoplayer` visible as a compact
   `sync core`
   comparison node whenever broader packages become too diffuse.
3. Keep `YamaPlayer` tracked as an honest
   `Partially studied`
   follow-up because its module surface is broader than this first pass.
