# Emergence Runtime Turn Loop (Strict Protocol)

This is the mandatory protocol for a valid game turn.

## Fidelity Pledge
Run mechanics using documented scripts and rules only. Do not improvise missing mechanics.

## Linked Runtime Specs
- Turn mechanism and verification gates: `../runtime/turn-mechanism.md`
- Canonical state model: `../runtime/state-model.md`
- Adjudication rules: `../runtime/adjudication-rules.md`
- CLI contract: `../runtime/cli-contract.md`
- Receipts and audit trail: `../runtime/receipts-and-audit.md`

## Truth Model
- Canonical state: project state files (defined by runtime scripts).
- Derived outputs: regenerated artifacts only; never hand-edit derived outputs.
- Determinism: RNG seed must be recorded in canonical state and in turn receipts.

## Turn Acceptance Criteria
A turn is accepted only if all stages succeed in order:
1. **Pre-validate** canonical state.
2. **Apply turn** with explicit input and seed.
3. **Regenerate** derived outputs.
4. **Post-validate** state and derived consistency.
5. **Record receipt** containing commands run, key outputs, and changed-file summary.

No partial turns are accepted.

## Script Binding Rule
Each stage must map to scripts in `docs/scripts/index.md` marked `runtime-safe: yes`.

Current status: blocked because no runtime-safe scripts are registered.

## Failure Handling
- If any required stage script is missing, unspecified, or fails: halt turn.
- Log gap and switch to development mode in a separate task/PR.
- Do not perform silent/manual repairs during runtime play.
