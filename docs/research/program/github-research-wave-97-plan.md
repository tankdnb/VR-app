# GitHub Research Wave 97 Plan

- Date: `2026-04-27`
- Goal: run the next focused GitHub research wave for repositories that map
  `Udon encoding`, `token verification`, `query helpers`, and
  `structured-data micro-libraries`.

## Why this wave exists

`VR-apps-lab` already had broader creator utility foundations and collection
helpers, but thinner coverage of:

`small protocol, text, query, and structured-data libraries that creators reach for when the platform surface is too narrow or too awkward on its own`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- Udon or UdonSharp encoding helpers;
- token or signature verification helpers;
- LINQ-like or query-oriented micro-libraries;
- lightweight XML or structured-data parsing helpers for creator worlds.

## Frozen shortlist for code-level study

- `koyashiro/udon-encoding`
- `koyashiro/udon-jwt`
- `aiczk/ULinq`
- `m-hayabusa/UdonXMLParser`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `koyashiro/udon-sha2`
  stayed outside this pass because the shortlist already had a stronger
  cryptography donor through the JWT verifier;
- several generic utility repos surfaced again, but they overlapped too much
  with the broader collection and utility-substrate waves already completed.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for Udon encoding, JWT, query, and XML helpers;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where small but reusable constrained-runtime techniques are
  visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `protocol and structured-data micro-libraries`
  rather than general utility packages;
- allow archived historical donors when they still reveal strong constrained
  runtime patterns.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the repo works around Udon constraints;
- whether the public API is author-friendly despite those constraints;
- what reusable micro-patterns belong in the methods catalog.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 97 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- historical libraries are described honestly when native alternatives now
  exist;
- narrow micro-libraries are treated as first-class donors when they reveal
  reusable constrained-runtime patterns;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 97 synthesis document exists with code-level findings;
4. the registry and families represent Udon protocol and structured-data
   micro-libraries more clearly;
5. new methods are captured where this wave clarified reusable constrained
   runtime patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
