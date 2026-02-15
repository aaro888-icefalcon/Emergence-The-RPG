# Receipts, Audit Trail, and Replay Evidence

Every accepted turn must produce durable evidence sufficient for independent replay.

## Required Receipt Artifacts
- `receipts/<turn_id>.json` (machine-verifiable)
- `receipts/<turn_id>.md` (human review)

## Receipt JSON Minimum Fields
- `turn_id`
- `timestamp_utc`
- `seed`
- `commands[]` with exact argv and exit codes
- `checks[]` with pass/fail per runtime stage
- `files_changed[]`
- `state_hash_before`
- `state_hash_after`
- `derived_hashes[]`
- `result` (`accepted|rejected`)
- `rejection_reason` (required if rejected)

## Receipt Markdown Structure
1. Turn identity and deterministic seed.
2. Stage-by-stage command transcript.
3. Key adjudication math summary (DC/mod/roll/total/outcome).
4. State deltas (resources, tags, clocks, world scales).
5. Final acceptance statement.

## Replay Procedure
To verify a past turn:
1. Restore `state_hash_before` snapshot.
2. Re-run recorded `emg-*` command sequence using recorded seed.
3. Compare resulting state + derived hashes with receipt.
4. Mark replay as pass only on full hash match.

## Audit Failures
If replay hash diverges:
- mark receipt `audit_failed`,
- retain conflicting artifacts,
- open development task for deterministic defect triage.
