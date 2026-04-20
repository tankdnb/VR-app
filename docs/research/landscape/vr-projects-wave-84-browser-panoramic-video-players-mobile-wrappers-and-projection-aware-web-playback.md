# VR Projects Wave 84: Browser Panoramic Video Players, Mobile Wrappers, and Projection-Aware Web Playback

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `browser panoramic video players`, `mobile wrappers`, and
  `projection-aware web playback plugins`.

## Why this wave exists

`VR-apps-lab` already had broader immersive playback coverage, but it still
lacked a cleaner answer to:

`what the strongest projection-aware playback donors look like when the player is web-first, plugin-shaped, or wrapped as a thin mobile bridge`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with browser panoramic player, Video.js VR plugin, and mobile
   360 wrapper queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `BIVROST/360WebPlayer` | Strong donor for a browser playback framework that explicitly splits media, stereoscopy, projection, and renderer modes |
| `yanwsh/videojs-panorama` | Strong donor for a plugin-first approach that upgrades an existing player with projection-aware canvas and hotspot behavior |
| `videojs/videojs-vr` | Strong donor for a mature `Video.js` projection plugin that models several 180, 360, stereo, and cubemap layouts explicitly |
| `flutterwtf/VR-Player` | Useful product and wrapper reference for a thin Flutter shell over native 360 playback SDKs |

## Deep-pass notes by project

## `BIVROST/360WebPlayer`

- GitHub:
  [BIVROST/360WebPlayer](https://github.com/BIVROST/360WebPlayer)
- What it is:
  a browser 360 and stereo media player framework that separates media source,
  projection model, stereoscopy handling, renderer mode, and player UI.
- Why it matters:
  it is the clearest donor in this wave for
  `projection-aware browser player architecture with explicit media and renderer splits`.
- Interesting ideas:
  treat projection and stereoscopy as first-class concepts instead of burying
  them inside one scene or shader; let filename and metadata heuristics
  pre-select likely layout; keep renderer modes such as mono, stereo, WebVR,
  and WebXR visible in code rather than hidden behind one render path.
- Interesting implementation choices:
  `src/bivrost-player.js`
  coordinates player state while `bivrost-media*.js`,
  `bivrost-projection-*.js`, and `bivrost-renderer-*.js`
  keep media type, projection family, and renderer choice separate;
  stereoscopy guessing and projection classification live close to media
  loading instead of being scattered through UI code.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the framework is broad enough that some media and renderer corners remain
  outside this one pass.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `browser playback framework with explicit projection taxonomy`
  donor.

## `yanwsh/videojs-panorama`

- GitHub:
  [yanwsh/videojs-panorama](https://github.com/yanwsh/videojs-panorama)
- What it is:
  a `Video.js` plugin that layers panoramic, fisheye, and stereo playback
  behaviors on top of an existing web video player.
- Why it matters:
  it is the clearest donor in this wave for
  `retrofit an existing player with projection-aware rendering instead of building a whole new playback shell`.
- Interesting ideas:
  keep the ordinary player ecosystem, then swap the rendering or canvas layer
  depending on projection type; let hotspots and VR button behavior sit beside
  the upgraded projection surface rather than inside a bespoke player app.
- Interesting implementation choices:
  `src/scripts/plugin_es6.js`
  coordinates plugin lifecycle while `Canvas.js`
  and `ThreeCanvas.js`
  provide different rendering paths based on `videoType`; the plugin keeps
  projection and interaction choices near the player integration boundary.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  strongest as an enhancement pattern over `Video.js`, not as a standalone
  immersive media product.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs an
  `existing player upgraded into panoramic playback`
  reference.

## `videojs/videojs-vr`

- GitHub:
  [videojs/videojs-vr](https://github.com/videojs/videojs-vr)
- What it is:
  an official-feeling `Video.js` VR plugin that supports several 180, 360,
  stereo, cubemap, and equi-angular layouts.
- Why it matters:
  it is the clearest donor in this wave for
  `projection enum plus player-plugin shell`
  rather than a whole separate web app.
- Interesting ideas:
  enumerate projection types explicitly; keep projection-specific behavior
  visible as configuration, not as naming convention only; let an ordinary
  media player gain immersive layouts without throwing away its existing
  controls and lifecycle.
- Interesting implementation choices:
  `src/plugin.js`
  owns projection selection, renderer bootstrapping, and UI integration while
  the plugin's public options make layout choice a deliberate surface for the
  embedding app.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  strongest as a plugin baseline and projection taxonomy donor rather than as a
  full product reference.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `projection-aware enhancement over an existing HTML5 video stack`
  donor.

## `flutterwtf/VR-Player`

- GitHub:
  [flutterwtf/VR-Player](https://github.com/flutterwtf/VR-Player)
- What it is:
  a Flutter package that wraps native 360 playback capabilities through
  platform views and thin mobile bridge code.
- Why it matters:
  it is the clearest reference in this wave for
  `cross-platform mobile wrapper over native immersive playback SDKs`.
- Interesting ideas:
  keep Flutter-facing API small while pushing actual immersive playback into
  native Android and iOS implementations; use a platform-view bridge instead of
  pretending the media surface is pure Dart UI.
- Interesting implementation choices:
  `lib/src/vr_player.dart`
  exposes the Flutter-facing surface while
  `VrPlayer.kt`, `VideoView.kt`, `VideoPlayerController.kt`,
  and `PlayerFlutterView.swift`
  show the platform-view and method-bridge pattern more clearly than the
  product shell itself.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  strongest as a wrapper pattern, not as a broad reusable playback framework.
- What to inspect next:
  revisit only when a future pass needs a stronger
  `Flutter or mobile wrapper over native XR playback`
  comparison set.

## Main takeaways from Wave 84

- `Projection-aware browser playback`
  now splits more cleanly into:
  - `full browser playback framework with media and renderer taxonomy`
  - `existing-player plugin with custom canvas or geometry path`
  - `projection-enum plugin over a mature web player`
  - `thin mobile wrapper over native immersive playback SDKs`
- The strongest lesson from this wave is that
  `web immersive playback`
  often becomes donor-worthy only when projection, stereoscopy, and renderer
  mode remain explicit in code.
- Another strong lesson is that
  `thin wrapper repos`
  still matter when they make platform-view and native bridge boundaries
  visible.

## Reusable methods clarified by this wave

- `Browser panoramic player core with explicit split across media source, stereoscopy, projection, and renderer mode`
- `Existing HTML5 player plugin that swaps rendering or canvas strategy based on projection and media layout`
- `Projection-aware Video.js VR plugin over an ordinary player shell`
- `Cross-platform mobile VR-player wrapper built as platform view plus native playback bridge`

## Recommended next moves after this wave

1. Keep `360WebPlayer` visible as one of the strongest browser playback donors
   in the current media branch.
2. Treat `videojs-panorama` and `videojs-vr` as useful
   `upgrade an existing player`
   comparison nodes rather than as separate product shells only.
3. Revisit `VR-Player` only when a future pass needs stronger coverage of
   mobile wrapper patterns and native playback SDK bridging.
