# Emergence Runtime Runbook

Operational runbook for high-fidelity gameplay execution.

## Operating Mode
- Runtime mode is for running turns only.
- Development changes (scripts, schema, migrations, tooling) are out-of-scope for runtime mode.

## Script-First Rule
Before any runtime action:
1. Open `docs/scripts/index.md`.
2. Locate required command by canonical name.
3. Confirm `runtime-safe: yes`.
4. Execute exactly as documented.

If no runtime-safe command exists for a required step, stop immediately.

## Standard Turn Procedure
1. Confirm intended turn input and deterministic seed.
2. Run pre-validation script.
3. Run turn-application script.
4. Run regeneration script(s).
5. Run post-validation script.
6. Write turn receipt under an agreed log path (when scripts are available).

## Required Turn Output Format
For each turn, record:
- Commands executed.
- Exit status and key stdout/stderr snippets.
- State diff summary.
- Derived artifacts updated.
- Seed and determinism notes.
- Final pass/fail status for each turn stage.

## Current Limitation
No runtime-safe scripts are currently registered, so runtime turn execution is intentionally blocked until development mode introduces and validates those scripts.
