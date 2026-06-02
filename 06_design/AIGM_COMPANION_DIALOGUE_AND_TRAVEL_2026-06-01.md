# AIGM Companion Dialogue and Travel Update

Date: 2026-06-01

## Intent

This note records the dialogue, hearing, travel, and tracking direction for Dakeyras and Danyal.

Desired behavior:
- both companions hear the owner
- both companions hear each other
- addressing determines who owns direct command execution
- general social/chatbot conversation remains broad
- tracking acts as route agitation / bounded excursion rather than hard mission replacement

## Dialogue and hearing model

The speech path was adjusted so hearing stays broad while direct execution remains gated.

Key design principle:
- **addressing should control action execution, not hearing**

Companion-to-companion relay was moved closer to dialogue-first handling, and fragile relay-side speech rewriting was removed.

### Practical outcome
- companions can remain socially aware of owner and linked-companion speech
- direct commands stay more isolated to the intended target
- ordinary conversation is less likely to be polluted by command-lane logic

## Dialogue handling changes

Companion dialogue was prevented from being over-reinterpreted as direct action.

This supports:
- more normal chatbot conversation
- less accidental command pollution
- more stable companion-to-companion exchange

## Travel and stop semantics

Travel behavior was cleaned up so travel start/stop does less stomping on native control order/state.

This supports:
- fewer conflicts between route travel and other behaviors
- cleaner transitions between follow / travel / tracking / pause-like states

## Tracking philosophy

Tracking was shifted toward:
- bounded off-route excursions
- temporary target investigation
- route readjustment help around terrain
- route resumption after short pursuit

This better matches the intended use:
- keep companions active
- let them drift and readjust around mountains/obstacles
- allow occasional combat engagement without permanently stealing the travel objective

## Current practical outcome

The current build should now be closer to:
- shared conversational awareness
- narrower command authority
- less destructive travel/tracking conflict

## Remaining follow-up areas
- improve combat persistence during tracking excursions
- continue parser/address tolerance work
- refine route return behavior after short engagement windows
