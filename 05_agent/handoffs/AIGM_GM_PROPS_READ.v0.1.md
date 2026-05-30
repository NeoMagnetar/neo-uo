# AIGM_GM_PROPS_READ.v0.1

## MODE
Implementation only.

## CURRENT STATE
AIGM has live proof for:
- world item Add
- world mobile Add
- container item Add

Canonical action type remains:
- `AIGMActionProposal`

The next missing pillar is native inspection.

## MISSION
Build a first practical native `gm_props_read` lane so the counselor can inspect real shard objects and return structured, readable state.

## GOAL
Support inspection of:
- mobiles
- items
- containers
- nearby targetable world objects where practical

through the canonical AIGM proposal/executor path.

## DO
1. Keep `AIGMActionProposal` canonical.
2. Add native action kind `gm_props_read`.
3. Support deterministic targeting for v0.1.
4. Return structured + human-readable inspection output.
5. Preserve Recent Actions / execution logging.

## DO NOT
- do not build a second fake inspection engine
- do not reopen bag/paperdoll UX
- do not route this through arbitrary chat-only summaries if real target data is available
- do not modify unrelated gameplay systems

## TARGETING FOR v0.1
Support these initial selection modes:
- current target
- nearest mobile
- nearest item
- nearest container
- nearest door

## SUGGESTED FILES
Create or patch:
- `Scripts/Custom/AIGM/AIGMPropsReadAdapter.cs`
- `Scripts/Custom/AIGM/AIGMTargetResolver.cs` *(or patch existing targeting utility if one already exists)*
- `Scripts/Custom/AIGM/AIGMPropertySnapshot.cs`
- `Scripts/Custom/AIGM/AIGMActionExecutor.cs`
- `Scripts/Custom/AIGM/AIGMProposalAugmenter.cs`

## EXPECTED RESULT SHAPE
At minimum, capture and summarize fields like:
- Kind
- TypeName
- Name
- Serial
- Map
- X/Y/Z
- Hue
- Movable
- Deleted
- Alive (for mobiles)
- Blessed (when available)
- Amount (for items)
- container/item/mobile classification
- a small key property list where easy/safe

## EXAMPLE REQUESTS
- `inspect the nearest mobile`
- `inspect the nearest container`
- `inspect the nearest item`
- `what is this dragon`
- `read properties of my target`
- `inspect the nearest door`

## RESULT FORMAT GOAL
Readable summary first, structured enough for later follow-up capability work.

## NEXT LADDER AFTER SUCCESS
1. `gm_props_read`
2. deeper property enumeration
3. `gm_props_write`
4. `gm_view_equipment`
5. `gm_dupe_target`
6. `gm_go_location` / move / bring flows
