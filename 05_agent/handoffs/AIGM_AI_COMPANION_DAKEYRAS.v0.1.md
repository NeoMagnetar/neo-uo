# AIGM_AI_COMPANION_DAKEYRAS.v0.1

## MODE
Implementation only.

## CURRENT STATE
The GM counselor shell is strong for:
- natural-language chat
- Add-backed world/container mutation
- first-pass props read
- administrative / visible management UX

But it is a poor immediate fit for creature-style movement and embodied combat because it is currently vendor-backed.

## MISSION
Create the first embodied AI companion actor: **Dakeyras**.

This actor should be movement-capable, follow-capable, gear-capable, and positioned as the first step toward a true AI-controlled in-world companion that can later fight, equip gear, use items, and develop skills.

## GOAL FOR v0.1
Build the first live Dakeyras companion with:
- name: `Dakeyras`
- movement-capable base class
- basic summon/spawn path
- follow me
- stop following
- come here / go to me
- basic companion inventory/equipment interaction
- baseline starting skills:
  - Archery
  - Healing
  - Fencing
  - Magic Resist

## IMPORTANT DESIGN INTENT
This is **not** the GM counselor shell.
This is a distinct embodied companion lane.

The counselor can remain the planning / admin / command shell.
Dakeyras becomes the first mobile actor able to physically inhabit the world.

## DO
1. Use a movement-capable base suited to escort/follow/combat-style behavior.
2. Keep the design compatible with later:
   - equipping weapons/armor
   - combat
   - skill growth
   - item interaction
3. Preserve a clean path for OpenClaw / AIGM chat integration later.
4. Start with stable native movement/follow behavior before broader autonomy.

## DO NOT
- do not overload the vendor-backed counselor shell into this role
- do not pretend Dakeyras is already a full autonomous player in v0.1
- do not entangle unrelated shard systems

## INITIAL REQUESTS TO SUPPORT
- spawn Dakeyras
- follow me
- stop following
- come here

## INITIAL SKILLS
Set baseline starter skills for Dakeyras:
- Archery
- Healing
- Fencing
- Magic Resist

Use sane starting values appropriate for a starter companion rather than maxed-out GM values.

## SUGGESTED FILES
Create or patch:
- `Scripts/Custom/AIGM/AIGMCompanionProfile.cs`
- `Scripts/Mobiles/NPCs/AIGMCompanionDakeyras.cs`
- `Scripts/Custom/AIGM/AIGMCompanionController.cs`
- `Scripts/Commands/AIGMCompanionCommand.cs`
- later integrate with proposal/executor flows as needed

## v0.1 SUCCESS CRITERIA
- Dakeyras can be created in the world
- Dakeyras can move/follow/stop/come here
- Dakeyras has the requested starter skills
- Dakeyras can hold/equip basic items in a way compatible with later expansion

## LATER LADDER
1. stable embodiment + movement
2. inventory/equipment handling
3. combat behavior
4. item use / healing / ammo handling
5. stronger AI autonomy and OpenClaw-backed decision loops
