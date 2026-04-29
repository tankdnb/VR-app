# GitHub Research Wave 103 Backlog

- Date: `2026-04-30`
- Scope: next GitHub discovery wave focused on
  `VRChat avatar text`, `speech`, `translation`, and `viseme sidecars`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for avatar-facing TTS, translation, viseme-output, and
  speech-surface repos
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning speech hubs, overlay-backed
  translation, reusable TTS substrate, and avatar-visible speech surfaces

## Work package B: Local source acquisition

- `Done` Confirm `TTS-Voice-Wizard` in local cache
- `Done` Confirm `kikitan-translator` in local cache
- `Done` Confirm `HeadTTS` in local cache
- `Done` Confirm `Billboard` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect queueing, VRChat listener flow, and OSC fan-out in
  `TTS-Voice-Wizard`
- `Done` Inspect Tauri UI flow, Rust OSC egress, and OpenVR overlay sidecar in
  `kikitan-translator`
- `Done` Inspect browser-side client, worker or server fallback, and viseme
  timestamp generation in `HeadTTS`
- `Done` Inspect product framing, runtime requirements, and avatar-text surface
  tradeoffs in `Billboard`

## Work package D: Repository updates

- `Done` Add Wave 103 plan document
- `Done` Add Wave 103 backlog document
- `Done` Add Wave 103 synthesis document
- `Done` Update the project registry for avatar-facing speech and text donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new TTS, viseme, translation, and
  avatar-surface patterns
- `Done` Update documentation indexes to include Wave 103

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `kikitan-translator`
  whenever a future pass needs a deeper map of its overlay process,
  recognizer matrix, or translation-provider abstraction
- `Next` Compare `TTS-Voice-Wizard`, `HeadTTS`, and `Billboard`
  whenever `VR-apps-lab` needs a sharper split between
  `speech engine`, `sidecar hub`, and `avatar-visible speech surface`
