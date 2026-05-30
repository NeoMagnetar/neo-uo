# Session Log — 2026-05-29 — AIGM alignment and repo curation

## Summary

Reviewed the current local OpenClaw workspace, the local NeoUO dev shard tree, and the two GitHub repositories:
- `NeoMagnetar/neo-uo`
- `NeoMagnetar/neo-uo-code`

Established a concrete alignment model:
- `neo-uo` = HQ / doctrine / roadmap / handoffs / logs
- `neo-uo-code` = implementation surface / code / technical notes
- local runtime logs, saves, crash files, and transient middleware state remain excluded

## Key findings

- The `neo-uo` repository is already structured correctly as a project-memory / wiki / HQ repo.
- The `neo-uo-code` repository is scaffolded correctly but still sparse.
- The local workspace contains several HQ-ready AIGM design and handoff documents produced on 2026-05-29.
- The local shard tree contains real AIGM implementation changes under `Scripts/Custom/AIGM`, `Scripts/Gumps`, `Scripts/Mobiles/NPCs`, and `Scripts/Commands`.
- The local shard tree also contains unrelated or review-needed drift that should not be swept into repo sync blindly.

## Important implementation truth preserved

The project has crossed from a “chat-only counselor” into a partially proven native GM execution system.

Confirmed truths worth preserving at HQ level:
- stale serialized `AIGMCounselor` mobiles were causing misleading runtime behavior
- fresh counselors now behave much better
- the live gump execution path is confirmed
- first true counselor-driven world-item mutations are now proven
- `AIGMActionProposal` is the canonical live execution model
- generalized native Add-backed capability is the next technical ladder

## Next alignment steps

1. Curate AIGM HQ notes into `neo-uo`
2. Curate implementation notes and intentional code surfaces into `neo-uo-code`
3. Exclude runtime clutter and machine-specific drift
4. Commit both repositories cleanly so they reflect current state without accidental noise
