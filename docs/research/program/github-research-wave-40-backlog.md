# GitHub Research Wave 40 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `VRChat chatbox workflows`, `speech-to-text sidecars`, and
  `avatar text-surface utilities`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for VRChat chatbox, textbox, STT, and overlay-keyboard utilities
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans broad chatbox composers, avatar text-surface generators, overlay-keyboard patches, and thin textbox tools
- `Done` Keep `VRCTextboxSTT` as an already-tracked overlap node instead of replacing the stronger new donors

## Work package B: Local source acquisition

- `Done` Confirm `vrcosc-magicchatbox` in local cache
- `Done` Confirm `TaSTT` in local cache
- `Done` Confirm `vrc-osc-scripts` in local cache
- `Done` Confirm `xsoverlay-keyboard-osc` in local cache
- `Done` Confirm `VRCTextboxOSC` in local cache
- `Done` Confirm `OSC-Chat-Tools` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect the module-driven chatbox composition flow in `vrcosc-magicchatbox`
- `Done` Inspect STT, SteamVR polling, and animator generation boundaries in `TaSTT`
- `Done` Inspect micro-script rate limiting and OSCQuery usage in `vrc-osc-scripts`
- `Done` Inspect Harmony patch points and chat-toggle flow in `xsoverlay-keyboard-osc`
- `Done` Inspect textbox persistence, trimming, and focus helpers in `VRCTextboxOSC`
- `Done` Inspect the status-provider composition model in `OSC-Chat-Tools`

## Work package D: Repository updates

- `Done` Add Wave 40 plan document
- `Done` Add Wave 40 backlog document
- `Done` Add Wave 40 synthesis document
- `Done` Update the project registry for VRChat chatbox and text-surface sidecars
- `Done` Update overlap families for chatbox composition, STT text surfaces, and overlay-entry helpers
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes
- `Done` Update the methods catalog with chatbox and text-surface methods
- `Done` Update documentation indexes to include Wave 40

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `vrcosc-magicchatbox` if a narrower pass on module/plugin boundaries or licensing constraints becomes worthwhile
- `Next` Compare `TaSTT`, `VRCTextboxOSC`, and `xsoverlay-keyboard-osc` directly as `avatar text surface`, `thin textbox`, and `patched overlay keyboard`
