# Canonical State Model (Runtime)

This defines the minimum persisted data required to validate and replay turns.

## Required Top-Level Objects
- `meta`
  - `schema_version`
  - `campaign_id`
  - `last_updated_utc`
- `clock`
  - `date`
  - `time_local`
  - `regional_phase`
- `player`
  - `hp` / `hp_max`
  - `ep` / `ep_max`
  - `res`
  - `tier`
  - `affinity`
  - `moves[]`
  - `tags[]`
- `world_state`
  - exactly three active scales (name + value + band)
  - `world_epoch`
  - `social_resonance`
- `clocks`
  - `scene[]` (max 3 active)
  - `faction_projects[]` (max 4 active)
  - `fronts[]` (max 6 active)
- `entities`
  - combatant records including vulnerability thresholds and active tags
- `determinism`
  - `turn_id`
  - `rng_seed`
  - `rng_trace[]` (ordered roll log)

## Hard Constraints
- HP `0` means dead; never negative in persisted state.
- EP may go negative transiently during resolution but must settle after overdraw conversion.
- World state must contain exactly 3 active scales at all times.
- If a scale reaches `0` or `20`, epoch mutation must be recorded during that turn.

## Drift and Time Rules
- Short skip: time advance only (optionally +1 one front/project by fiction).
- Long skip: 3–10 day jump + drift rolls for active scales + meso clock advancement.
- Anti-stagnation: force long skip when trigger criteria are met.

## Persistence Rule
- Persist canonical state immediately after successful turn application and before output serialization.
- Derived artifacts (summaries/rendered status cards) are regenerated from canonical state only.
