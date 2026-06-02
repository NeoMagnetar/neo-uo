# AIGM_GM_MOVEMENT.v0.1

## MODE
Implementation only.

## CURRENT STATE
AIGM has live proof for:
- world item Add
- world mobile Add
- container item Add
- first-pass native props read

The next missing capability family is embodied movement.

## MISSION
Build the first practical movement/control lane for the counselor using explicit canonical actions, starting with follow/stop/come-to-requester behavior.

## GOAL
Support a first reliable movement/control ladder for the counselor:
- follow requester
- stop following
- resume following
- go to requester / come here

## DO
1. Keep `AIGMActionProposal` canonical.
2. Add explicit movement action kinds.
3. Use existing native/pathing mechanics where practical.
4. Preserve Recent Actions / execution logging.
5. Keep movement capability isolated from unrelated systems.

## DO NOT
- do not reopen bag/paperdoll UX
- do not collapse movement into arbitrary raw command strings as the main product path
- do not entangle unrelated gameplay systems
- do not claim long-range autonomous travel is complete in v0.1

## INITIAL ACTION KINDS
- `gm_follow_requester`
- `gm_stop_follow`
- `gm_resume_follow`
- `gm_go_to_requester`

## EXAMPLE REQUESTS
- `follow me`
- `come here`
- `go to me`
- `stop following`
- `resume following`

## SUGGESTED FILES
Create or patch:
- `Scripts/Custom/AIGM/AIGMMovementAdapter.cs`
- `Scripts/Custom/AIGM/AIGMMovementController.cs` *(patch if already present)*
- `Scripts/Custom/AIGM/AIGMActionExecutor.cs`
- `Scripts/Custom/AIGM/AIGMProposalAugmenter.cs`

## v0.1 SUCCESS CRITERIA
- the counselor can follow the requester reliably
- the counselor can stop following reliably
- the counselor can resume following reliably
- the counselor can respond to a direct come-here/go-to-me request
- action history and clear user-visible result messages are preserved

## LATER LADDER
1. follow requester / stop / resume / go to requester
2. follow selected target mobile
3. go to nearby object / tile / mobile
4. named local destination movement
5. longer autonomous destination travel with recovery
