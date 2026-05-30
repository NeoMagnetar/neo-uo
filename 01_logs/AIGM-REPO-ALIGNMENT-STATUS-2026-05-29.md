# AIGM Repo Alignment Status
_Date: 2026-05-29_

## Alignment outcome so far

The Neo UO repos are now materially closer to the true current AIGM work.

### `neo-uo`
Now contains:
- current HQ-side handoff material
- architecture findings
- active-work status notes
- session log of alignment work

### `neo-uo-code`
Now contains:
- runtime and architecture notes for current AIGM counselor work
- a dated preserved snapshot of the live shard AIGM code
- a documented long-term AIGM script lane for normalization

## Current alignment philosophy

Do not pretend the repos are a perfect mirror of the live shard.
Instead, preserve:
- what is intentional
- what is current
- what is explainable
- what can be safely evolved without dragging along unrelated machine drift

## Next alignment move

Promote stable AIGM implementation surfaces from the dated snapshot into the long-term curated AIGM lane inside `neo-uo-code`.
