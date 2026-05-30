# AIGM_GM_SURFACE_TO_CAPABILITY_LAYER.v0.1

## MODE
Implementation only.

## CURRENT STATE
The constructable discovery lane succeeded. We now have shard-local constructable output:
- `AIGMConstructables.json`
- `AIGMConstructables.Items.txt`
- `AIGMConstructables.Mobiles.txt`
- `AIGMConstructables.Houses.txt`
- `AIGMConstructables.Addons.txt`

Discovered counts:
- Items: 5363
- Mobiles: 1252
- HouseDeeds: 14
- AddonDeeds: 32
- Vendors: 384
- Monsters: 832
- Bosses: 24
- Resources: 195
- Containers: 246

Known issue:
- `AIGMCommands.txt` is empty.
- Command registry discovery did not reach the live registered command table.

## MISSION
Convert the constructable discovery output into usable AIGM GM capabilities and fix command registry discovery.

## DO
1. Fix command registry discovery.
2. Build a generalized constructable resolver for Add-backed actions.
3. Keep `AIGMActionProposal` as the canonical action object.
4. Extend `gm_add_world_item` beyond hardcoded Bandage.
5. Preserve Recent Actions and execution logging.
6. Add clear result reporting.

## DO NOT
- Do not create a parallel `AIGMCommandAction` execution path.
- Do not use raw arbitrary command strings as the main product path.
- Do not call `CommandSystem.Handle("[add ...")` as the main Add implementation.
- Do not reopen bag/paperdoll UX.
- Do not reopen middleware unless bridge fails during a live test.
- Do not edit `PlayerMobile`, `BaseWeapon`, loot, skills, death, economy, or Siege mechanics.
- Do not answer with assessment only.

## TASK 1 — FIX COMMAND REGISTRY DISCOVERY
Create or patch:
- `Scripts/Custom/AIGM/AIGMCommandSurfaceDiscovery.cs`

Goal:
- `[AIGMDumpGMSurface`
- regenerate `Logs/AIGMCommands.txt`
- regenerate `Logs/AIGMCommands.json`

The command dump should include:
- `CommandName`
- `AccessLevel`
- `HandlerName`
- aliases if discoverable
- source/declaring type if discoverable

Use reflection fallback because command registry internals vary between ServUO / RunUO forks.

## TASK 2 — BUILD AIGMConstructableResolver
Create:
- `Scripts/Custom/AIGM/AIGMConstructableResolver.cs`

Purpose:
Resolve natural-language type names against the actual compiled constructable surface.

Use the constructables dump for reporting/category awareness, but runtime creation should use the real compiled script types.

Initial resolver API:
- `AIGMConstructableResolveResult ResolveItem(string requestedName, Mobile requester)`
- `AIGMConstructableResolveResult ResolveMobile(string requestedName, Mobile requester)`

Resolver responsibilities:
- normalize incoming names
- use `ScriptCompiler.FindTypeByName(...)`
- handle basic singular/plural cleanup
- support a small alias layer for common UO names
- validate that resolved type matches Item or Mobile
- validate presence of accessible `[Constructable]` constructor

## TASK 3 — GENERALIZE gm_add_world_item
Patch:
- `Scripts/Custom/AIGM/AIGMNativeAddAdapter.cs`
- `Scripts/Custom/AIGM/AIGMAddCommandUtility.cs`

New behavior:
- read `typeName` from action.Parameters
- read `amount` from action.Parameters
- resolve `typeName` through `AIGMConstructableResolver.ResolveItem`
- verify requester `AccessLevel`
- construct item
- set `Amount` if stackable / amount > 1
- place item at requester or specified location
- log
- record Recent Actions

Use native Add-like concepts:
- type resolution
- constructable validation
- constructor choice
- world placement

## TASK 4 — ADD REAL ADD POLICY
Create:
- `Scripts/Custom/AIGM/AIGMAddPolicy.cs`

Purpose:
Avoid one-item hardcoding while still enforcing sane staff-only authority and scale limits.

Must validate:
- requester exists
- requester access level
- type assignability
- amount floor / high-volume gate

## TASK 5 — GENERALIZED PROPOSAL GENERATION
Patch:
- `Scripts/Custom/AIGM/AIGMProposalAugmenter.cs`

Keep current deterministic Bandage support if still useful, but add a generalized fallback parser for:
- `create {amount?} {type phrase} here`
- `spawn {type phrase} here`
- `add {type phrase} at my feet`
- `make {type phrase} here`

Examples:
- `create 25 bandages at my feet`
- `spawn a dragon here`
- `add a backpack here`
- `create 500 gold at my feet`
- `spawn a healer here`

Proposal generation only:
- if resolver says Item → `gm_add_world_item`
- if resolver says Mobile → `gm_add_world_mobile`

Do not execute in the parser.

## TASK 6 — RESULT FORMAT REQUIRED
Return only:

`AIGM_GM_SURFACE_TO_CAPABILITY_LAYER_RESULT`

### Discovery
- Constructables already generated:
- AIGMCommands.txt fixed:
- command count:
- command json path:

### Constructable counts confirmed
- Items:
- Mobiles:
- HouseDeeds:
- AddonDeeds:
- Vendors:
- Monsters:
- Bosses:
- Resources:
- Containers:

### Files changed
-

### Canonical action type
-

### Implemented
- command registry reflection dump:
- AIGMConstructableResolver:
- generalized AIGMAddCommandUtility:
- AIGMAddPolicy:
- generalized gm_add_world_item:
- generalized proposal parser:
- Recent Actions preserved:
- execution logs preserved:

### Runtime tests
1. create 25 bandages at my feet
 - proposed:
 - confirmed:
 - executed:
 - visible result:
2. create 500 gold at my feet
 - proposed:
 - confirmed:
 - executed:
 - visible result:
3. create backpack at my feet
 - proposed:
 - confirmed:
 - executed:
 - visible result:
4. spawn dragon here
 - proposed:
 - mobile resolver result:
 - executed or blocked:
 - reason:

### Build/deploy
- correct x64 build used:
- root Scripts.dll updated:
- fresh counselor used:

### Pass/Fail
- result:
- exact blockers:

## SHORT EXECUTION INSTRUCTION
Build `AIGM_GM_SURFACE_TO_CAPABILITY_LAYER.v0.1`.

The constructables dump succeeded, but `AIGMCommands.txt` is empty. Fix command registry discovery with a reflection fallback, then build a generalized Add resolver over the discovered constructable surface.

Keep `AIGMActionProposal` as canonical. Do not create a parallel `AIGMCommandAction` execution path.

Implement:
- `AIGMCommandSurfaceDiscovery`
- `AIGMConstructableResolver`
- `AIGMAddPolicy`
- generalized `AIGMAddCommandUtility`
- generalized `gm_add_world_item` proposal/execution

Test:
- create 25 bandages at my feet
- create 500 gold at my feet
- create backpack at my feet
- spawn dragon here as resolver/proposal test, execute only if `gm_add_world_mobile` is already wired
