# AIGM Companion Speech / Travel / Support Update

Date: 2026-06-01

## Intent

This update records the current design direction for Dakeyras and Danyal.

Desired behavior:
- both companions hear the owner
- both companions hear each other
- addressing determines who owns direct command execution
- general social/chatbot conversation remains broad
- tracking acts as route agitation / bounded excursion rather than hard mission replacement
- self-bandaging should feel like real in-game healing, using native timing

## What changed

### 1. Speech / hearing model
The speech path was adjusted so hearing stays broad while direct execution remains gated.

Key design principle:
- **addressing should control action execution, not hearing**

Companion-to-companion relay was moved closer to dialogue-first handling, and fragile relay-side speech rewriting was removed.

### 2. Dialogue behavior
Companion dialogue was prevented from being over-reinterpreted as direct action.

This was done to support:
- more normal chatbot conversation
- less accidental command pollution
- more stable companion-to-companion exchange

### 3. Travel and stop semantics
Travel behavior was cleaned up so travel start/stop does less stomping on native control order/state.

This supports:
- fewer conflicts between route travel and other behaviors
- cleaner transitions between follow / travel / tracking / pause-like states

### 4. Tracking philosophy
Tracking was shifted toward:
- bounded off-route excursions
- temporary target investigation
- route readjustment help around terrain
- route resumption after short pursuit

This better matches the intended use:
- keep companions active
- let them drift and readjust around mountains/obstacles
- allow occasional combat engagement without permanently stealing the travel objective

### 5. Self-bandaging
Reactive self-healing now uses the real shard bandage timer flow instead of fake instant healing.

That means:
- real bandage begin
- real delay
- more believable healing behavior
- auto trigger when under attack and injured

## Current practical outcome

The current build should now be closer to:
- shared conversational awareness
- narrower command authority
- less destructive travel/tracking conflict
- more believable automatic self-bandaging

## Remaining follow-up areas
- normalize non-self bandage/support paths onto native mechanics too
- improve combat persistence during tracking excursions
- continue parser/address tolerance work
- refine route return behavior after short engagement windows

## Repos
This note complements the code-facing note stored in the code repo docs.
