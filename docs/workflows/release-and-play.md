# Release and Play Handoff

This workflow bridges development and runtime play.

1. Ensure development changes are merged and documented.
2. Confirm script registry (`docs/scripts/index.md`) is current.
3. Validate runtime pipeline scripts are marked `runtime-safe: yes`.
4. Execute runtime turns only through `play-runbook.md` and `turn-loop.md`.

If runtime-safe scripts are missing, halt play and return to development mode.
