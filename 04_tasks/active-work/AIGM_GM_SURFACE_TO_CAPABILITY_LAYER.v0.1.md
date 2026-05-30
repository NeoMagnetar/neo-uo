# AIGM_GM_SURFACE_TO_CAPABILITY_LAYER.v0.1

## Purpose
Turn the successful constructables dump into a usable AIGM GM capability layer while fixing command registry discovery.

## Current state
- Constructable discovery succeeded and produced shard-local output.
- `AIGMCommands.txt` is empty.
- The live canonical action object is `AIGMActionProposal`.
- The live execution chain remains:
  - `AIGMQuestionGump`
  - `AIGMBridgeClient.Ask(...)`
  - `AIGMResponse`
  - `AIGMProposalAugmenter`
  - `AIGMResponseGump`
  - `AIGMConfirmActionGump`
  - `AIGMActionExecutor`
  - native adapter/backend
  - visible result / Recent Actions

## Mission
1. Fix command registry discovery so `AIGMCommands.txt` and `AIGMCommands.json` populate.
2. Build a generalized Add-backed constructable resolver.
3. Extend `gm_add_world_item` beyond hardcoded single-type logic.
4. Preserve `AIGMActionProposal` as canonical.

## Explicit non-goals
- no bag/paperdoll detour work
- no middleware detour work unless bridge breaks
- no fake parallel command execution model
- no broad unrelated shard-mechanics edits

## Expected next ladder after this lane
1. `gm_add_world_item`
2. `gm_add_container_item`
3. `gm_add_world_mobile`
4. `gm_props_read`
5. `gm_props_write`
6. `gm_go_location`
7. `gm_move_target` / `gm_bring_mobile`
8. `gm_view_equipment`
9. `gm_dupe_target`
10. `gm_house_deed` / `gm_place_house`
11. delete / wipe tools
12. account/admin enforcement tools
