# Research Operator Quick Reference

- Purpose: one-screen operational checklist for running a new research pass in
  `VR-apps-lab`.

## Before Starting

Read:

1. `docs/foundation/current-operating-context.md`
2. `docs/research/current-focus.md`
3. `docs/research/program/new-session-quickstart.md`
4. `docs/research/catalog/project-registry.md`
5. `docs/research/landscape/project-families.md`
6. `docs/research/landscape/not-yet-studied-deeply.md`

## Research Workflow

1. Choose one coherent family or theme.
2. Search GitHub for repositories in that family.
3. Deduplicate against the registry.
4. Freeze a shortlist.
5. Clone shortlisted repos into local-only cache:
   - `.research-sources/`
   - `.tmp/`
6. Read code, not just README.
7. Extract:
   - interesting idea
   - code donor value
   - product reference value
   - what to inspect next
8. Identify reusable methods, UX patterns, and architecture lessons.
9. Place every repo into a logical family.
10. Update repository docs.

## Canonical roles

- `project-registry.md`
  source of truth for per-repository status.
- `project-families.md`
  synthesis, overlap, and family-level product direction.
- `not-yet-studied-deeply.md`
  active deep-study queue and follow-up ordering.
- `vr-utility-methods-catalog.md`
  extracted reusable implementation methods.
- `current-focus.md`
  short current-state view, not full archive history.

## Must-Update Files

Update the relevant combination of:

- `docs/research/catalog/project-registry.md`
- `docs/research/landscape/project-families.md`
- `docs/research/landscape/not-yet-studied-deeply.md`
- `docs/research/methods/vr-utility-methods-catalog.md`
- one new wave document in `docs/research/landscape/`
- one plan/backlog pair in `docs/research/program/`

Update `docs/research/current-focus.md` only when the new wave materially
changes the repository's active priorities or strongest donor clusters.

## Validation

For research/doc changes, verify:

- structure is coherent
- navigation is still clear
- no obvious duplicate entries
- registry/families/methods/backlog stay aligned

## Finish

1. Check `git status`
2. Stage intended changes
3. Commit with a clear message
4. Push to GitHub
5. Confirm public repo contains the new wave
