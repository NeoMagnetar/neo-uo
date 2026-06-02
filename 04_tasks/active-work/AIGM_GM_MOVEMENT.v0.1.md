# AIGM_GM_MOVEMENT.v0.1

## Purpose
Add the first practical embodied movement/control lane for the counselor.

## Why now
AIGM now has mutation and first-pass inspection capability. The next major step is making the counselor behave like an in-world agent instead of only a stationary execution surface.

## Core action model
- canonical action type: `AIGMActionProposal`
- initial action kinds:
  - `gm_follow_requester`
  - `gm_stop_follow`
  - `gm_resume_follow`
  - `gm_go_to_requester`

## Initial v0.1 scope
- follow requester
- stop following
- resume following
- come here / go to requester

## Why it matters
This is the first movement capability family and the base for later:
- target following
- local navigation
- named destination travel
- longer autonomous world movement

## Important note
Movement should stay an explicit capability lane and should not re-entangle the counselor class design around old inheritance assumptions.
