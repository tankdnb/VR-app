# VR.app Repository Positioning

- Date: `2026-04-18`
- Goal: define what `VR.app` is as a public repository and how it should be
  presented to new users and contributors.

## Short version

`VR.app` is not just one VR program.

It is a public `knowledge repository`, `pattern library`, and `working base`
for building VR utilities, overlays, diagnostics tools, tracking helpers, and
experimental runtime integrations.

## What the repository is

`VR.app` combines three layers:

1. `Knowledge repository`
   - curated notes on public VR-related repositories
   - extracted methods and implementation patterns
   - overlap families and research waves
   - reusable product and architecture references

2. `Working foundation`
   - reusable `OpenVR` overlay prototype code
   - shared abstractions and experiment code
   - scripts and workflows for deeper research

3. `Experiment archive`
   - passthrough and camera experiments
   - dead ends that still produced useful engineering findings
   - hardware-specific feasibility notes

## Who this repository is for

This repo should be useful for:

- VR developers looking for implementation references
- people building overlays, utility apps, and tool-like XR software
- researchers comparing public VR projects and extracting methods
- power users who want to understand the current utility landscape
- contributors who want to add new projects and structured findings

## What users should expect to find here

- a map of public VR utility projects
- reusable implementation methods
- grouped families of overlapping tools
- backlog-driven research waves
- local workflows for code-level repository study
- prototypes and experiment code that support the research

## What users should not expect

This repository should not present itself as:

- a single polished end-user VR product
- a promise that every experiment is production-ready
- a universal runtime compatibility layer
- a finished SDK for every class of VR software

The right framing is:

- `curated knowledge first`
- `working prototypes second`
- `future products and utilities third`

## Public-facing messaging rule

When describing `VR.app` publicly, prefer wording like:

- `knowledge repository for VR utility development`
- `curated research base for VR tools and overlays`
- `pattern library and implementation reference for VR utilities`

Avoid describing it only as:

- `an overlay app`
- `a passthrough prototype`
- `a single VR program`

Those are parts of the repo, not the full identity of the project.

## Why this positioning matters

This framing is better because it:

- matches the real shape of the repository today
- makes the large research corpus feel intentional
- lowers confusion about what is experimental versus reusable
- makes public contributions easier
- supports long-term growth without forcing one product narrative

## Repository growth rule

New content should strengthen at least one of these:

- the `knowledge base`
- the `methods catalog`
- the `research system`
- the `prototype foundation`

If it does not clearly improve one of those layers, it probably does not belong
in the main repository.
