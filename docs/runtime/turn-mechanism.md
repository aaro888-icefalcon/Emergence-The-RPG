# Verifiable Turn Mechanism

This document operationalizes the adjudication loop into strict, testable runtime stages.

## Turn Lifecycle (Must Execute in Order)
1. **State Check**
   - Advance in-world time using scene-duration rules.
   - Run drift only on long skips or anti-stagnation trigger.
   - Update clocks, social resonance, and horizon seed.
2. **Scene Setup**
   - Bind 1–2 clocks to scene stakes.
   - Materialize `SHOW NEXT SCENE` off-screen consequences.
3. **Encounter Generation**
   - Determine mode (social/explore/mixed/combat).
   - Attach maturity constraints for organized groups.
   - Generate combatant stat blocks for any combat-capable actor.
4. **Action Resolution**
   - Resolve with `d20 + mods vs DC` and mandatory outcome grading.
   - Apply consequences in fixed order.
5. **Output Assembly**
   - Emit Dice Header → Narrative Body → Status Block.

## Non-Negotiable Invariants
- All randomness is code-executed and logged.
- Outcome grade is derived from roll math; never narrative-overridden.
- State transitions are persisted before turn output is finalized.
- Failed stage = rejected turn (no partial acceptance).

## Verification Gates Per Turn
A turn is valid only when all checks pass:
- **Gate A: Determinism** — seed recorded and reused for replay.
- **Gate B: Arithmetic Integrity** — DC/modifier/roll/total consistency.
- **Gate C: Consequence Order** — HP/EP/RES before tags, tags before clocks.
- **Gate D: Structural Output** — required output sections present.
- **Gate E: State Consistency** — resources, clocks, and macrostate coherent post-turn.

## Mechanical Definition of Done (Runtime)
A turn is "done" only if:
- all five lifecycle stages exit successfully,
- all five verification gates pass,
- receipt is written with command transcript + state diff summary.

## Rejection Conditions
Reject turn execution immediately when any of the following occurs:
- missing runtime-safe command for any stage,
- missing or non-parseable seed,
- invalid canonical state schema,
- contradiction between output text and persisted state.
