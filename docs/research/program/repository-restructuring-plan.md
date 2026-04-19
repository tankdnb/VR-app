# Repository Restructuring Plan

- Date: `2026-04-19`
- Status: `Living reference`
- Goal: keep `VR-apps-lab` structured as a maintainable public research system
  where every tracked VR repository has:
  - a place in a logical family
  - a visible study status
  - a path toward deeper investigation
  - and a connection to future utility directions

## Problem statement

`VR-apps-lab` accumulated valuable research quickly, but without enough stable
structure a repository like this drifts toward:

1. chronology without clear information architecture
2. informal overlap knowledge instead of canonical families
3. scattered study status instead of one honest registry
4. obsolete artifacts or historical branches that confuse the public framing

## Target outcomes

The restructuring aims to preserve five things:

1. `clear topology`
   keep stable folders for `foundation` and `research`
2. `research operating model`
   define how new repositories should be studied and recorded
3. `canonical project tracking`
   keep one honest place for status and family placement
4. `clear backlog`
   turn vague future work into visible next steps
5. `navigation`
   make it easy for a new contributor to understand what to read first

## Non-goals

This plan does **not** claim that every tracked external repository is fully
audited.

What it does instead:

- makes current knowledge explicit
- captures study status honestly
- keeps obsolete app-first residue out of the mainline repository shape
- creates the scaffolding needed to deepen coverage repo by repo

## Target information architecture

```text
docs/
  foundation/
  research/

scripts/
  research/
```

Inside `docs/research/`, the durable sublayers are:

- `landscape/`
- `catalog/`
- `program/`
- `methods/`
- `discovery/`
- `reuse/`
- `templates/`

## Workstreams

### Workstream 1: Documentation topology

Purpose:

- keep public-facing docs simple and durable
- remove obsolete app-first and legacy experiment clutter from the mainline

### Workstream 2: Canonical research operating model

Purpose:

- make research repeatable instead of chat-history dependent

### Workstream 3: Canonical project tracking

Purpose:

- make every tracked repository discoverable in one place

### Workstream 4: Family synthesis

Purpose:

- cluster repositories by logical overlap instead of raw chronology

### Workstream 5: Reuse guidance

Purpose:

- turn especially strong donors into explicit reuse plans

## Ongoing rule

Whenever repository shape changes:

1. update public entry points first
2. keep registry, families, methods, and backlog aligned
3. remove obsolete tracked artifacts instead of leaving them as silent residue

## Active dedicated refactor block

The broader restructuring work now has one narrower active track focused on:

- documentation usability
- navigation scale
- canonical role separation

Track that work in:

- `documentation-navigation-refactoring-plan.md`
- `documentation-navigation-refactoring-backlog.md`
