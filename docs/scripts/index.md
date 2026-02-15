# Canonical Scripts & Hooks Registry

This file is the single source of truth for runnable commands, scripts, hooks, and automation contracts in this repository.

## Registry Policy
- The Emergence runtime agent may only execute entries marked `runtime-safe: yes`.
- Any runnable command not listed here is out-of-contract and must be added before use.
- Unknown or broken commands must be marked explicitly and are unavailable to runtime mode.

## Inventory Coverage (Current Pass)
Inventory sources inspected:
- `scripts/`, `bin/`, `cli/` directories
- `Makefile`
- `package.json` script targets
- `.github/workflows/*.yml`
- `.git/hooks/*`

Result:
- No project-owned runtime scripts or automation entrypoints found.
- Only default Git sample hooks exist under `.git/hooks/*.sample`.

## Runtime Pipeline Contract
Required stages for an accepted turn:
1. Pre-validate state
2. Apply turn
3. Regenerate derived outputs
4. Post-validate state
5. Emit turn receipt

Status: **Blocked** — no runtime scripts currently implement these stages.

---

## Registry Entries

### `git-hook:pre-commit.sample`
- **Path:** `.git/hooks/pre-commit.sample`
- **Category:** utility (sample)
- **Purpose:** Demonstration script shipped by Git; not part of project runtime.
- **Inputs:** Git internal context.
- **Outputs:** None guaranteed.
- **Preconditions:** Hook manually copied/enabled by developer.
- **Postconditions:** N/A.
- **Example invocation:** `sh .git/hooks/pre-commit.sample` (diagnostic only)
- **Failure modes:** Not stable, not project-maintained.
- **runtime-safe:** no
- **Status:** out-of-scope sample

### `git-hook:pre-push.sample`
- **Path:** `.git/hooks/pre-push.sample`
- **Category:** utility (sample)
- **Purpose:** Demonstration script shipped by Git.
- **Inputs:** Git internal push arguments.
- **Outputs:** None guaranteed.
- **Preconditions:** Hook manually copied/enabled by developer.
- **Postconditions:** N/A.
- **Example invocation:** `sh .git/hooks/pre-push.sample` (diagnostic only)
- **Failure modes:** Not stable, not project-maintained.
- **runtime-safe:** no
- **Status:** out-of-scope sample

### `git-hook:commit-msg.sample`
- **Path:** `.git/hooks/commit-msg.sample`
- **Category:** utility (sample)
- **Purpose:** Demonstration commit-message validator from Git.
- **Inputs:** Commit message file path.
- **Outputs:** Exit code only.
- **Preconditions:** Hook manually copied/enabled by developer.
- **Postconditions:** N/A.
- **Example invocation:** `sh .git/hooks/commit-msg.sample .git/COMMIT_EDITMSG`
- **Failure modes:** Not stable, not project-maintained.
- **runtime-safe:** no
- **Status:** out-of-scope sample

---


## Planned Runtime CLI Commands (Spec Only)
These command names are reserved by the runtime contract in `docs/runtime/cli-contract.md`.
They are not implemented yet and therefore are **not runtime-safe**.

### `emg-state-validate`
- **Category:** runtime-stage
- **Purpose:** pre-validate canonical state schema and invariants.
- **runtime-safe:** no
- **Status:** planned (unimplemented)

### `emg-turn-apply`
- **Category:** runtime-stage
- **Purpose:** apply one turn deterministically using explicit input and seed.
- **runtime-safe:** no
- **Status:** planned (unimplemented)

### `emg-derived-regenerate`
- **Category:** runtime-stage
- **Purpose:** regenerate derived outputs from canonical state.
- **runtime-safe:** no
- **Status:** planned (unimplemented)

### `emg-state-postvalidate`
- **Category:** runtime-stage
- **Purpose:** validate cross-artifact consistency after turn application.
- **runtime-safe:** no
- **Status:** planned (unimplemented)

### `emg-receipt-write`
- **Category:** runtime-stage
- **Purpose:** emit machine-readable + human-readable turn receipts.
- **runtime-safe:** no
- **Status:** planned (unimplemented)

## Gaps / Follow-up Actions
1. Add project-owned scripts for the required runtime pipeline stages.
2. Add each script to this registry with complete IO contracts.
3. Reclassify runtime-safe entries only after dry-run validation.
4. Add CI check to ensure registry coverage for runnable targets.
