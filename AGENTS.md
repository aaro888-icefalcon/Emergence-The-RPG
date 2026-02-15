# Overall AGENTS.md — Engineering Harness

This file defines the repository-wide engineering harness for development work, orchestration, and reliability-focused execution.

## Purpose
- Govern **development mode** (code/docs/schema changes).
- Route **runtime play execution** to the Emergence runtime runbook.
- Keep durable truth in versioned artifacts, not chat memory.

## Scope Discipline
- Make the smallest diff that satisfies the objective.
- Do not refactor adjacent code unless explicitly requested.
- If a change spans more than two major surfaces (state schema, rules logic, renderer, validation/CI), split into phased PRs.

## Plan-First Contract
Before editing, write a short plan with:
1. Files to touch.
2. Commands/scripts to run.
3. Mechanical definition of done.

## Mechanical Definition of Done
- Do not claim completion unless required checks pass.
- If checks cannot run, report exactly which checks were skipped, why, and what substitute evidence was gathered.

## Approval Gates (Stop-and-confirm boundaries)
Treat these as guarded operations:
- Destructive operations.
- Dependency/build-system changes.
- `schema_version` bumps.
- Migrations/backfills rewriting canonical state.
- Turn-loop contract changes.

## Durable Truth Policy
- Decisions that must persist go into repo docs/tests/schema.
- If ambiguous, create or update a source-of-truth artifact rather than improvising.

## Determinism & Reproducibility
- Use stable ordering in lists/outputs.
- Any randomness must be seeded and the seed recorded in canonical state/turn records.

## Builder/Reviewer Separation
- After implementing, run a separate diff-based review pass.
- Address findings before finalizing.

## Sub-agent Orchestration Rules
- **Development mode:** follow this file and applicable local AGENTS docs.
- **Emergence runtime mode (gameplay turns):** follow `docs/workflows/play-runbook.md` and `docs/workflows/turn-loop.md` strictly.
- Runtime mode may only invoke scripts marked `runtime-safe` in the canonical scripts registry.

## Canonical Documentation Map
- Docs map: `docs/index.md`
- Dev loop: `docs/workflows/dev-loop.md`
- Release/play flow: `docs/workflows/release-and-play.md`
- Runtime turn protocol: `docs/workflows/turn-loop.md`
- Runtime runbook: `docs/workflows/play-runbook.md`
- Scripts registry (single source of truth): `docs/scripts/index.md`
