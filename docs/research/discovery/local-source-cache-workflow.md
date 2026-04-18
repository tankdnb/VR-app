# Local Source Cache Workflow

- Date: `2026-04-18`
- Goal: define how `VR.app` should download GitHub repositories for code-level
  inspection without bloating the main repo.

## Why this exists

Serious repository research needs more than README reading.

To extract implementation ideas, we often need:

- top-level structure;
- build files;
- app/driver/service split;
- key source modules;
- config and manifest layout.

That means cloning repositories locally. However, cloning everything into the
main git history would make `VR.app` noisy and heavy.

## Rule

Use a `local-only source cache`:

- path: `.research-sources/github/`
- status: ignored by git
- purpose: temporary or refreshable working copies for deep-study passes

## Folder layout

```text
.research-sources/
  github/
    owner-a/
      repo-1/
      repo-2/
    owner-b/
      repo-3/
```

## How to sync repositories

Use:

- [Sync-GitHubResearchSources.ps1](../../../scripts/research/Sync-GitHubResearchSources.ps1)

Examples:

```powershell
.\scripts\research\Sync-GitHubResearchSources.ps1 `
  -Repo sh-akira/VROverlay,BenWoodford/SteamVR-Webkit
```

```powershell
.\scripts\research\Sync-GitHubResearchSources.ps1 `
  -RepoFile .\some-shortlist.txt `
  -UpdateExisting
```

## What should be cloned

Clone only repositories that pass discovery triage and are in the current wave
shortlist.

Do not clone:

- every result from GitHub search;
- obvious duplicates before the upstream is understood;
- abandoned repos with no product or technical signal;
- forks that have no meaningful changes.

## Recommended research order

1. Search GitHub and capture candidates.
2. Add candidates to the registry with honest status when useful.
3. Freeze a shortlist for the current wave.
4. Clone only the shortlist into `.research-sources/github/`.
5. Perform a code-level pass.
6. Extract ideas into `landscape/`, `methods/`, `catalog/`, and `families`.

## Quality gate

A repository should not be marked `Already studied` from search results alone.

For that status, we should have:

- local source inspection or an equally strong code-level pass;
- extracted implementation notes;
- updated family placement;
- updated method or product impact where relevant.

