# AIGM_GM_PROPS_READ.v0.1

## Purpose
Add a first practical native inspection lane so the counselor can read real shard state instead of only mutating it.

## Why now
AIGM now has live proof for:
- world item Add
- world mobile Add
- container item Add

The next balanced capability is inspection.

## Core action
- canonical action type: `AIGMActionProposal`
- new action kind: `gm_props_read`

## Initial v0.1 scope
Targeting:
- current target
- nearest mobile
- nearest item
- nearest container
- nearest door

Readable output should cover:
- Type
- Name
- Serial
- Map
- Location
- Hue
- Alive / Deleted
- Amount where relevant
- key object classification details

## Why it matters
This gives the counselor a real “look before touch” power and sets up later property-writing, equipment inspection, and smarter admin workflows.
