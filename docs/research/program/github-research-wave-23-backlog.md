# GitHub Research Wave 23 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `glove platforms`,
  `poser stacks`, and `nonstandard hardware bridge drivers`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for glove ecosystems with both firmware and SteamVR driver surfaces
- `Done` Search GitHub for external-protocol and poser-driven SteamVR stacks
- `Done` Search GitHub for niche hardware bridges such as HOTAS, Hydra, and remote-tracker relays
- `Done` Search GitHub for OSVR-to-SteamVR compatibility bridges with visible public source
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record `puresoul/Barebone` and `TrueOpenVR/SteamVR-TrueOpenVR` as follow-up comparison nodes instead of over-expanding the wave

## Work package B: Local source acquisition

- `Done` Confirm `LucidVR/opengloves-driver` in local cache
- `Done` Confirm `LucidVR/lucidgloves` in local cache
- `Done` Confirm `HoboVR-Labs/hobo_vr` in local cache
- `Done` Confirm `Copprhead/hotas-vr-controller` in local cache
- `Done` Confirm `SophiaH67/soph_wireless` in local cache
- `Done` Confirm `SophiaH67/soph_wireless_transmitter` in local cache
- `Done` Confirm `OSVR/SteamVR-OSVR` in local cache
- `Done` Confirm `terminal29/OSVR-SteamVR-Bridge` in local cache
- `Done` Confirm `r57zone/Razer-Hydra-SteamVR-driver` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect driver, service, and overlay split in `opengloves-driver`
- `Done` Inspect firmware transports, encoding, and controller subsystems in `lucidgloves`
- `Done` Inspect bindings, poser protocol, and external driver contract in `hobo_vr`
- `Done` Inspect offset and click-interception model in `hotas-vr-controller`
- `Done` Inspect remote-tracker relay driver in `soph_wireless`
- `Done` Inspect paired sender utility in `soph_wireless_transmitter`
- `Done` Inspect compatibility-driver layering in `SteamVR-OSVR`
- `Done` Inspect the smaller alias-mapping comparison node in `OSVR-SteamVR-Bridge`
- `Done` Inspect Hydra-to-SteamVR device mapping and monitor helper in `Razer-Hydra-SteamVR-driver`

## Work package D: Repository updates

- `Done` Add Wave 23 plan document
- `Done` Add Wave 23 backlog document
- `Done` Add Wave 23 synthesis document
- `Done` Update the project registry for the newly clarified glove, poser, and bridge-driver repos
- `Done` Update overlap families for custom hardware and compatibility bridges
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new custom-hardware ecosystem methods
- `Done` Update documentation indexes to include Wave 23

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `opengloves-driver`, `lucidgloves`, and `hobo_vr` directly as one `ecosystem + protocol + driver` story
- `Next` Revisit `puresoul/Barebone` and `TrueOpenVR/SteamVR-TrueOpenVR` only if a future bridge-driver wave needs thinner comparison nodes
- `Next` Revisit `soph_wireless` if the relay protocol grows beyond the current paired sender/receiver design
- `Next` Decide whether `LucidVR` deserves a dedicated reuse plan as the strongest current glove ecosystem in the repo
