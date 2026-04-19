# VR Projects Wave 38: SteamVR Validation, Patchers, and Environment-Hygiene Micro-Tools

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `SteamVR validation helpers`, `config patchers`, and
  `environment-hygiene micro-tools`.

## Why this wave exists

`VR-apps-lab` already tracked many environment helpers, but it still needed one
cleaner comparative pass on the `small but high-leverage` tool family:

- validation tools that catch broken SteamVR metadata before runtime;
- one-shot config patchers with backup and rollback behavior;
- small prelaunch utilities that disable unwanted runtime state outside
  SteamVR;
- background helpers that continuously sync one environment setting from live
  runtime data.

This wave exists to make `workflow micro-tool design` clearer inside
`VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with SteamVR validation, patcher, and environment-helper
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `username223/SteamVR-ActionsManifestValidator` | Strong donor for a CI-friendly SteamVR metadata linter with explicit warning gates |
| `Erimelowo/Lighthouse-Scale-Fix` | Strong donor for a backup-safe one-shot JSON patcher with one clear user value |
| `MuffinTastic/steamvr-exconfig` | Strong donor for a prelaunch config toggler that disables autolaunch apps and always-on drivers before startup |
| `Virus-vr/SteamVRAdaptiveBrightness` | Strong donor for a runtime feedback daemon that samples compositor output and continuously rewrites one SteamVR setting |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `username223/SteamVRNoHeadset` | Strong comparison node for null-driver and no-HMD workflows, but weaker as a focused micro-tool donor than the mainline shortlist |
| `shieldmeidunn/SteamVRNullFlipper` | Strong comparison node for backup-safe null-driver flipping, but too narrow to displace the broader mainline donors |

## Deep-pass notes by project

## `username223/SteamVR-ActionsManifestValidator`

- GitHub:
  [username223/SteamVR-ActionsManifestValidator](https://github.com/username223/SteamVR-ActionsManifestValidator)
- What it is:
  a Python validator for SteamVR action manifests meant to run locally or in
  CI.
- Why it matters:
  it is the clearest donor in the repo for
  `CI-friendly linter over SteamVR action metadata`.
- Interesting ideas:
  reject duplicate JSON keys up front; keep checks individually disableable;
  treat missing sections and localization mistakes as explicit workflow errors
  instead of relying on SteamVR to surface them.
- Interesting implementation choices:
  `checks.py` makes the `parse -> duplicate-key rejection -> rule checks ->
  explicit error code` flow easy to inspect.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  narrow scope by design, but that focus is exactly what makes it useful.
- What to inspect next:
  keep it as the baseline donor whenever a future `VR-apps-lab` helper needs
  `preflight validation` over SteamVR metadata.

## `Erimelowo/Lighthouse-Scale-Fix`

- GitHub:
  [Erimelowo/Lighthouse-Scale-Fix](https://github.com/Erimelowo/Lighthouse-Scale-Fix)
- What it is:
  a tiny Go utility that backs up `lighthouse_scale.json`, sets every scale to
  `1`, and exits.
- Why it matters:
  it is one of the clearest product references in the repo for
  `one-shot patcher with one strong user value`.
- Interesting ideas:
  keep the tool narrowly scoped; create a backup before touching the file; make
  manual rollback obvious instead of hiding it behind a complex UI.
- Interesting implementation choices:
  `lh_scale_fix.go` makes the full flow explicit:
  `read file -> create .bkp -> rewrite selected values -> save`.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  intentionally tiny, with hardcoded path assumptions, but that simplicity is
  part of the product lesson.
- What to inspect next:
  keep it visible whenever a future tool needs a
  `backup-safe one-shot repair` pattern.

## `MuffinTastic/steamvr-exconfig`

- GitHub:
  [MuffinTastic/steamvr-exconfig](https://github.com/MuffinTastic/steamvr-exconfig)
- What it is:
  a Windows desktop utility that lists SteamVR autolaunch apps and always-on
  drivers so they can be toggled before startup.
- Why it matters:
  it is the clearest donor in the repo for
  `prelaunch runtime hygiene UI over SteamVR config`.
- Interesting ideas:
  keep the utility outside SteamVR; build the UI from the config model rather
  than hardcoding individual toggles; separate `app settings`, `driver
  settings`, and `save`.
- Interesting implementation choices:
  `SteamVR ExConfig/MainForm.cs`
  makes the `load setting models -> render toggle rows -> save updated config`
  flow easy to inspect.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  specific to one class of SteamVR config changes, but that sharp focus is what
  makes the product useful.
- What to inspect next:
  keep it as the main donor whenever a future helper needs a
  `SteamVR prelaunch toggle editor`.

## `Virus-vr/SteamVRAdaptiveBrightness`

- GitHub:
  [Virus-vr/SteamVRAdaptiveBrightness](https://github.com/Virus-vr/SteamVRAdaptiveBrightness)
- What it is:
  a background utility that samples the SteamVR mirror texture, computes scene
  brightness, and rewrites `analogGain` continuously.
- Why it matters:
  it is the clearest donor in the repo for
  `runtime feedback daemon driven by compositor output`.
- Interesting ideas:
  register the utility as an auto-launch overlay app; use mirror texture data
  as input instead of requiring deep app integration; keep the output path to a
  single SteamVR setting.
- Interesting implementation choices:
  `AdaptiveBrightness.cpp`
  makes the `OpenVR init -> manifest registration -> D3D mirror texture ->
  compute shader -> analogGain write loop` flow explicit.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  more specialized than the other tools in this wave, but that specialization
  reveals a very reusable pattern.
- What to inspect next:
  treat it as the main donor whenever a future branch needs
  `live compositor data -> single runtime setting feedback loop`.

## Main takeaways from Wave 38

- `Environment hygiene micro-tools` are a distinct product family, not only a
  grab bag of small scripts.
- The strongest split in this family is:
  - `metadata validator`
  - `backup-safe one-shot patcher`
  - `prelaunch toggler UI`
  - `continuous runtime feedback daemon`
- The most reusable lesson is often the `scope discipline`:
  - validate one file format well
  - patch one config area safely
  - toggle one narrow runtime concern before startup
  - continuously sync one runtime setting from one live data source

## Reusable methods clarified by this wave

- `CI-friendly SteamVR manifest linter with disableable warning gates`
- `Mirror-texture feedback daemon that continuously rewrites runtime settings`

## Recommended next moves after this wave

1. Keep `SteamVR-ActionsManifestValidator` as the baseline donor for
   `SteamVR metadata preflight checks`.
2. Keep `Lighthouse-Scale-Fix` as the clearest product reference for
   `backup-safe one-shot repair`.
3. Keep `steamvr-exconfig` as the strongest donor for
   `prelaunch SteamVR toggle editors`.
4. Keep `SteamVRAdaptiveBrightness` as the main donor for
   `live compositor signal -> runtime setting feedback`.
