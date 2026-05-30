# AIGM / OpenClaw / NeoUO Detailed Handoff
_Date: 2026-05-29_

## Purpose

This handoff captures the current engineering state of the AI GM Counselor work inside the NeoUO dev shard, with emphasis on:
- what has been proven live
- what code/files were touched
- what runtime/build issues were discovered
- what the current architecture direction is
- what the next implementation priorities should be

This document is intended for direct continuation by another model or engineer.

---

# 1. Project goal

Build an **AI GM Counselor** inside NeoUO that can eventually:
- chat naturally in-world
- use real shard GM/admin powers through natural language
- create items
- create mobiles/NPCs/creatures
- inspect targets/properties
- manage inventory/containers
- later move/follow/navigate
- later support broader world mutation like houses, multis, region tools, etc.

The desired long-term standard is **real systems integration**, not patchwork.

---

# 2. High-level architecture direction

## Core conclusion
AIGM should become an:

> **AI orchestration layer over native NeoUO / ServUO GM/admin systems**

rather than a fake parallel GM engine.

## Native command/capability substrates already identified
- `Add` (`Scripts/Commands/Add.cs`)
- `Dupe` (`Scripts/Commands/Dupe.cs`)
- `Props` / `Properties` (`Scripts/Commands/Properties.cs`)
- command handlers in `Scripts/Commands/Handlers.cs`
  - `Go`
  - `Move`
  - `ViewEquip`
  - `Bank`
  - `Where`
  - etc.

## Capability-oriented long-term direction
Separate:
- conversation capability
- inventory capability
- spawn capability
- inspection capability
- movement capability
- targeting capability
- visible counselor shell

This avoids long-term inheritance traps like:
- `PlayerVendor` better for embodiment/inventory
- `BaseCreature` better for older movement code

---

# 3. Major runtime truth discovered

## The stale saved counselor problem was real
A large amount of earlier confusion was caused by stale serialized `AIGMCounselor` mobiles stored in `Saves\Mobiles\*`.

### Symptoms before reset
- counselor behavior looked inconsistent
- paperdoll/backpack/clothing work appeared to “not change” despite code changes
- world load failures on `Server.Mobiles.AIGMCounselor`
- broken runtime truth due to incompatible serialized instances

## What was done
The mobile save layer was reset by removing:
- `Saves\Mobiles\Mobiles.bin`
- `Saves\Mobiles\Mobiles.idx`
- `Saves\Mobiles\Mobiles.tdb`

### Consequence
This effectively reset all mobiles in the dev shard, including the player character, but it removed the corrupted/stale counselor state.

## Post-reset result
Fresh `AIGMCounselor` instances now behave much better.

### Confirmed improvements on fresh counselors
- chat works
- visible paperdoll works
- visible backpack works
- clothing/equip behavior is much improved
- live AIGM gump path is active and usable

This was a major breakthrough.

---

# 4. Live UI / execution path now confirmed

## Active gump family in the live shard
The UI the player is actually seeing corresponds to these files:

- `Scripts/Gumps/AIGMQuestionGump.cs`
- `Scripts/Gumps/AIGMResponseGump.cs`
- `Scripts/Gumps/AIGMConfirmActionGump.cs`
- `Scripts/Gumps/AIGMActionHistoryGump.cs`

### Visible titles / labels confirmed in runtime
- **AI GM Counselor**
- **Ask Follow-up**
- **Retarget**
- **History**
- **AI GM Recent Actions**
- **Confirm AI GM Action**

## Confirmed flow
`AIGMQuestionGump`
→ `AIGMBridgeClient.Ask(...)`
→ `AIGMResponse`
→ `AIGMProposalAugmenter`
→ `AIGMResponseGump`
→ optional `AIGMConfirmActionGump`
→ `AIGMActionExecutor`
→ adapter/backend
→ visible result / action history

### Important behavioral truth
Execution only happens if:
1. `ProposedActions` exist
2. the response-gump action is clicked
3. if mutate, the confirm action is clicked

This is central to the system design.

---

# 5. Build/deploy truth discovered

## Critical deployment issue
Successful `dotnet build` did **not always** mean the shard was running the updated code.

### Root cause
The live server loads:
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts.dll`

But many builds were outputting only to:
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts\bin\Debug\Scripts.dll`

which meant the live root `Scripts.dll` remained stale.

## Correct build command
The correct build invocation discovered was:

```powershell
dotnet build .\Scripts\Scripts.csproj -c Debug -p:Platform=x64
```

## Additional deployment rule
The build fails to update root `Scripts.dll` if `ServUO.exe` is still running and holding a file lock.

### Correct practical sequence
1. stop ServUO
2. build with `-p:Platform=x64`
3. verify root `Scripts.dll` timestamp changed
4. restart ServUO
5. use a **fresh counselor** for testing

This is now a required operational rule.

---

# 6. Bridge / middleware state

## Workspace path
`C:\.openclaw\workspace-ultima-online`

## Relevant middleware/tooling files
Examples present in workspace:
- `aigm-bridge.js`
- `aigm-middleware-service.js`
- `aigm-supervisor.ps1`
- `aigm_supervisor.py`
- various restart/start/stop wrapper scripts

## Middleware endpoint
- `http://127.0.0.1:4876/aigm/query`
- health:
  - `http://127.0.0.1:4876/health`

## Current conclusion
Bridge/middleware health is **not** the main blocker anymore.
The system can chat and return responses.

The current blocker is:

> **natural language → real GM execution**

---

# 7. Current live execution proof status

## What has now been proven live
### First true end-to-end mutation proof
A fresh counselor successfully created at least one real visible world item through the live natural-language UI path.

### Example proven item spawns
At runtime, the user observed successful creation of:
- `scissors`
- `katana`
- `apple`
- `torch`

through the counselor path using natural language and the current response/confirm/executor lane.

This is the first real evidence that the AIGM counselor can do more than chat.

## What is not yet fully proven/clean
- quantity handling remains imperfect (`25 bandages` may still create `1 bandage`)
- native Add-backed path vs temporary safe fallback path may still vary by item/constructor path
- broader generalized GM capability port is not yet complete

Still, the first live world-item mutation proof is a major milestone.

---

# 8. Canonical action model

## Important finding
The live action path uses:
- **`AIGMActionProposal`**

and not a separate parallel execution model.

### Files depending on it
- `AIGMResponse.cs`
- `AIGMResponseGump.cs`
- `AIGMConfirmActionGump.cs`
- `AIGMActionExecutor.cs`

## Key rule
Do **not** create a second parallel action path using `AIGMCommandAction` if the live gump/executor chain consumes `AIGMActionProposal`.

That split was identified as a major risk.

---

# 9. Current AIGM code surfaces touched

## Under `Scripts/Custom/AIGM/`
Important touched/created files include:
- `AIGMActionExecutor.cs`
- `AIGMActionPreview.cs`
- `AIGMActionProposal.cs`
- `AIGMBridgeClient.cs`
- `AIGMCommandAction.cs`
- `AIGMResponse.cs`
- `AIGMStubResponder.cs`
- `AIGMMovementController.cs`
- `AIGMProfileHooks.cs`
- `IAIGMActor.cs`
- `IAIGMInventoryCapability.cs`
- `AIGMCounselorInventoryCapability.cs`
- `AIGMProposalAugmenter.cs`
- `AIGMAddAdapter.cs`
- `AIGMNativeAddAdapter.cs`
- `AIGMAddCommandUtility.cs`
- `AIGMExecutionResult.cs`
- `AIGMExecutionLog.cs`

## Under `Scripts/Gumps/`
- `AIGMQuestionGump.cs`
- `AIGMResponseGump.cs`
- `AIGMConfirmActionGump.cs`
- `AIGMActionHistoryGump.cs`
- `AIGMCounselorManagementGump.cs`

## Under `Scripts/Mobiles/NPCs/`
- `AIGMCounselor.cs`
- `AIGMCounselorVendorBackpack.cs`

## Under `Scripts/Commands/`
- `AIGMCommand.cs`
- `AIGMProofCommand.cs` *(probe/harness only; not intended long-term product path)*
- `AIGMDiscoveryCommand.cs`

---

# 10. Native Add-backed world item lane

## Current proof direction
The current native world-item proof lane uses an action kind conceptually equivalent to:
- `gm_add_world_item`

through the live AIGM action path.

## Current deterministic phrase used
The main proof phrase evolved around:
- `create 25 bandages at my feet`

### Important note
Quantity may still not be fully correct, but the world-item spawn lane itself has now shown visible success.

## Current adapter/backing files
- `AIGMNativeAddAdapter.cs`
- `AIGMAddCommandUtility.cs`

## Current behavior
The system attempts to use real native Add-backed logic where possible:
- type resolution via native script surfaces
- constructable checks
- constructor/placement path reuse where possible

A temporary safe fallback utility exists for proof stability when the exact native constructor path is not cleanly reusable for all cases yet.

This fallback should be treated as temporary scaffolding, not the final architecture.

---

# 11. GM surface discovery lane

## New discovery command
A new in-game GM command was added:

```text
[AIGMDumpConstructables
```

## Purpose
Generate a shard-local inventory of:
- constructable items
- constructable mobiles
- house/addon deeds
- command surface (attempted)

## Output files under `Logs\`
- `AIGMConstructables.json`
- `AIGMConstructables.Items.txt`
- `AIGMConstructables.Mobiles.txt`
- `AIGMConstructables.Houses.txt`
- `AIGMConstructables.Addons.txt`
- `AIGMCommands.txt`

## Latest observed discovery results
From the in-game dump result:
- **Items:** 5363
- **Mobiles:** 1252
- **HouseDeeds:** 14
- **AddonDeeds:** 32
- **Vendors:** 384
- **Monsters:** 832
- **Bosses:** 24
- **Resources:** 195
- **Containers:** 246

### Important caveat
- `AIGMCommands.txt` was generated but empty

This means:
- constructable discovery is working
- command registry discovery is still incomplete and should be fixed later

Still, the constructables inventory is a huge foundation for generalized native GM capability work.

---

# 12. Current practical product truth

## Working enough now
- fresh counselor instances
- chat / bridge path
- visible paperdoll
- visible backpack
- improved clothing behavior
- live AIGM gump path
- response/confirm/history UI
- first real item world spawn proof via counselor
- constructables discovery dump

## Not yet complete
- quantity correctness for stackable proof requests
- generalized native Add across all safe item types
- native Add-to-container lane
- native Add-to-mobile lane
- native Props read/write lane
- native Dupe lane
- movement/follow reintroduction
- housing/multi placement workflows
- complete GM command registry dump

The project should now be treated as:

> **partially proven native execution system with a clear next engineering ladder**

—not as “still only a chatbot.”

---

# 13. Current best next implementation priorities

## Priority 1 — Generalized native Add item capability
Now that several real item spawns work, the next major step is:
- stop hardcoding tiny allowlists item-by-item forever
- generalize item resolution over the discovered constructable item surface
- keep safety rules / allow/deny policy

### Goal
Support many real item types through the same `gm_add_world_item` style native lane.

## Priority 2 — Fix command discovery
Make `AIGMCommands.txt` actually enumerate the registered GM command surface.

This is important for mapping later capability adapters.

## Priority 3 — Native Add container path
Support:
- requester backpack
- counselor backpack
- targeted container

This will eventually reconnect to the bag/inventory workflow in a more native way.

## Priority 4 — Native Add mobile/world path
Spawn constructable mobiles/NPCs/creatures into the world using the same capability spine.

## Priority 5 — Props read
Implement:
- `gm_props_read`
- inspect type/properties/target state

## Priority 6 — Later GM ladder
Then continue with:
- `Dupe`
- `Go`
- `Move`
- `ViewEquip`
- `Bank`
- housing / multis
- high-risk admin actions (ban, wipe, delete, etc.)

---

# 14. Recommended implementation order from here

Suggested next ladder:
1. Generalized native item resolution for Add-backed world item creation
2. Native Add to container
3. Native Add mobile to world
4. Props read
5. Props write (approval-gated)
6. Dupe target
7. Go / Move / Bring / admin travel
8. ViewEquip / bank/container admin views
9. Housing / multis / placement
10. High-risk admin actions

This aligns with the current architecture and the newly proven runtime baseline.

---

# 15. Important guardrails for continuation

## Do use
- fresh `AIGMCounselor` instances only
- root `Scripts.dll` deployment discipline
- `AIGMActionProposal` as canonical live action model
- explicit action kinds for each native GM capability
- deterministic augmentation where needed for proof lanes
- native GM backends where available
- capability-based architecture over time

## Do not reopen first
- paperdoll/bag affordance detours as the primary blocker
- bridge/middleware debugging unless a new real failure appears
- broad arbitrary GM string parsing
- a fake parallel GM engine detached from native shard systems
- stale serialized counselor instances as evidence

---

# 16. Short handoff summary

> Fresh `AIGMCounselor` instances now behave much better after resetting stale mobile saves. The counselor now chats, shows a paperdoll, has a visible backpack, and has improved clothing behavior. The live AIGM gump path is confirmed to be `AIGMQuestionGump -> AIGMResponseGump -> AIGMConfirmActionGump -> AIGMActionHistoryGump`. The first real world-item mutation proof through the counselor is now working well enough to create visible items such as scissors, katana, apple, and torch. The project is no longer stuck at “chat only.” The current next engineering target is to generalize native Add-backed item creation over the discovered constructable item surface (5363 constructable items, 1252 constructable mobiles, etc.), fix command registry discovery, and continue porting native GM capabilities one adapter at a time (`Add`, `Props`, `Dupe`, `Go`, `Move`, `ViewEquip`, etc.) through the live AIGM action path using `AIGMActionProposal` as the canonical execution model.
