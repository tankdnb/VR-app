# New Session Quickstart

- Date: `2026-04-19`
- Purpose: help a new session, contributor, or assistant recover repository
  intent quickly without needing prior chat history.

## When to use this file

Use this file when:

- opening `VR-apps-lab` in a fresh session
- returning after a long gap
- switching to a new local clone
- trying to understand what should be read before making changes

## Fast orientation

`VR-apps-lab` is not a single product repo.

Treat it as a combination of:

- `foundation`
- `research base`
- `pattern library`
- `working lab`

The most common mistake is to look for a hidden main application instead of the
canonical docs and research system.

## 5-10 minute recovery route

Do not start by reopening the entire research archive.

Read these first:

1. `docs/foundation/current-operating-context.md`
2. `docs/research/current-focus.md`
3. `docs/research/program/research-operator-quick-reference.md`

Then branch by task:

- `new research wave`
  read `docs/research/catalog/project-registry.md`,
  `docs/research/landscape/project-families.md`, and
  `docs/research/landscape/not-yet-studied-deeply.md`.
- `deepen or synthesize an existing family`
  read `docs/research/landscape/project-families.md`,
  `docs/research/catalog/project-registry.md`, and the latest relevant wave
  docs.
- `product direction or future repo priorities`
  read `docs/foundation/public-roadmap.md`,
  `docs/research/current-focus.md`, and
  `docs/research/methods/vr-utility-methods-catalog.md`.
- `repo structure or documentation work`
  read `docs/README.md`, `docs/research/README.md`, and the active
  refactor-track docs in `docs/research/program/`.

## If you need deeper archive history

Only go deeper if the task really needs it:

- `docs/research/README.md`
  short route into the broader research system.
- `docs/research/program/README.md`
  chronological plan/backlog archive.
- `docs/research/landscape/vr-projects-master-index.md`
  archive-grade wave and synthesis index.

## Local-only data model

Some useful research data should stay outside git history:

- `.research-sources/`
- `.tmp/`
- `artifacts/`

These support research work, but they are not part of the canonical public
repository history.

## Validation rule

For `documentation / research` changes:

- verify navigation
- verify link consistency
- verify registry, families, methods, and backlog alignment
- verify that new material lands in the correct canonical place

If a future change adds runnable examples, validate only the affected example.

## If the task is vague

If a new session only receives a vague instruction like:

- "continue the research"
- "find more VR projects"
- "expand the repo"

then the safest next step is:

1. inspect `docs/research/current-focus.md`
2. inspect `docs/research/landscape/not-yet-studied-deeply.md`
3. inspect the latest relevant `wave` documents
4. choose one coherent family for the next wave
5. continue using the operator quick reference

## If the task is about product direction

If the session is choosing what the repository should prioritize next, start
from:

1. `docs/foundation/public-roadmap.md`
2. `docs/research/current-focus.md`
3. `docs/research/landscape/project-families.md`
4. `docs/research/methods/vr-utility-methods-catalog.md`
