# Runtime Spec Index (Hierarchical Source of Truth)

This section converts the GM workflow into a **verifiable, CLI-driven runtime contract**.

## Reading Order (Top → Detail)
1. `../workflows/turn-loop.md` — stage-gated protocol and acceptance criteria.
2. `turn-mechanism.md` — deterministic turn lifecycle and required invariants.
3. `state-model.md` — canonical state schema and persistence rules.
4. `adjudication-rules.md` — executable mechanics and outcome grading constraints.
5. `cli-contract.md` — command-level interface and machine-checkable exit criteria.
6. `receipts-and-audit.md` — turn receipt format and reproducibility evidence.

## Scope
- Applies to runtime play execution only.
- Development tasks (adding scripts, schema migrations, tooling) remain governed by `../workflows/dev-loop.md`.

## Status
- This documentation defines the runtime contract.
- Runtime remains blocked until matching scripts are implemented and registered as `runtime-safe: yes` in `../scripts/index.md`.
