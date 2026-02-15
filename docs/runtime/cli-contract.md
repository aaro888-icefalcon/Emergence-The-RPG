# Runtime CLI Contract (Deterministic Programming Interface)

This defines command interfaces needed to run a verifiable turn pipeline.

## Command Set (Canonical Names)
1. `emg-state-validate`
   - Purpose: schema + invariants validation for canonical state.
2. `emg-turn-apply`
   - Purpose: apply one player action against canonical state.
3. `emg-derived-regenerate`
   - Purpose: regenerate derived artifacts from canonical state.
4. `emg-state-postvalidate`
   - Purpose: post-apply consistency checks across state and derived outputs.
5. `emg-receipt-write`
   - Purpose: emit machine-readable and human-readable turn receipt.

## Required Flags
- `--state <path>` canonical state file.
- `--turn-input <path>` structured turn action input.
- `--seed <int|string>` deterministic RNG seed.
- `--out <path>` output path for generated artifacts (where relevant).

## Exit Code Contract
- `0`: success
- `2`: validation failure (state or input)
- `3`: determinism failure (missing/invalid seed, RNG trace mismatch)
- `4`: adjudication failure (rule execution bug, impossible state transition)
- `5`: IO contract failure (missing file/path/write error)

## JSON Output Contract (All Commands)
Each command must print one terminal JSON envelope:
- `command`
- `status` (`pass|fail`)
- `exit_code`
- `turn_id` (if known)
- `seed` (if provided)
- `checks[]` with `{name, status, detail}`
- `artifacts[]`

## Determinism Guarantees
- `emg-turn-apply` must write ordered RNG trace entries in canonical state.
- Replay with same input + seed + prior state must produce byte-identical state and receipt outputs.

## Implementation Status
- This interface is specified but not yet implemented.
- Runtime execution remains blocked until these commands exist and are listed as `runtime-safe: yes` in `../scripts/index.md`.
