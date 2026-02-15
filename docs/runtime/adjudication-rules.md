# Adjudication Rules (Executable Mechanics)

This is the runtime-oriented rules contract extracted from the GM workflow.

## Resolution Primitive
- Core test: `d20 + modifiers vs DC`.
- Default DC bands are rarity-driven; use `10–13` unless fiction clearly supports harder opposition.

## Modifier Stack (Ordered)
1. Base competence (`-2` to `+4` expected range).
2. Situational modifiers (normally constrained to `±3` total).
3. Resource/tag pressure modifiers (starvation, injuries, social disadvantage, affinity interactions).
4. Advantage/Disadvantage only when fiction sharply favors one side.

## Mandatory Outcome Grade Mapping
Given `raw_roll`, `total`, and `DC`:
- **Critical Success**: `raw_roll == 20` OR `total >= DC + 5`
- **Complicated Success**: `total >= DC` and not critical success
- **Failure**: `total < DC` and not critical failure
- **Critical Failure**: `raw_roll == 1` OR `total <= DC - 5`

## Consequence Application Order (Strict)
1. HP/EP/RES changes (including EP overdraw conversion to HP burn).
2. Tag updates and vulnerability checks.
3. Trauma trigger roll for latent actors at trigger conditions.
4. Nemesis escape/return markers.
5. Clock movement (scene/project/front/siege).
6. Collateral cascade and third-party threat insertion after prolonged combat.
7. Ally doubt/patience updates.

## Combat Fidelity Rules
- Two competent firearm hits can be lethal for Tier 1.
- Tier mismatch is decisive unless tags/terrain/counters shift position.
- High-threat actions require telegraph before impact.
- Combatants must have minimal stat blocks before entering play.

## Output Formatting Contract
Every turn output must include:
1. Dice Header with full arithmetic trace.
2. Narrative Body constrained by tone and unresolved crisis ending.
3. Status Block with required resource, clock, and world-state fields.
