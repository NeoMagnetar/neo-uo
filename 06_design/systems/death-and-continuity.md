# Death and Continuity

## Purpose

Define how Neo UO treats death, defeat, character continuity, and player continuation.

This system is one of the central identity pillars of the project. Neo UO is not built on disposable character death. Character loss must matter. At the same time, total account-level ejection is too destructive for the intended player experience.

## Player Experience Goal

The player should feel that:
- death is serious,
- survival is meaningful,
- defeat can take more forms than simple deletion,
- and losing a major character hurts without ending their ability to continue playing.

## Design Position

Neo UO should distinguish between:
- character consequence,
- defeat consequence,
- and player continuity.

A character may die, be retired, be captured, or be politically leveraged.
The player should still have continuity through backup characters and other account-level structures.

## Core Design Laws

### Law 1 — Character Death Must Matter
A meaningful character death should create emotional and strategic loss.

### Law 2 — Defeat Should Not Always Collapse Into Instant Death
Some defeats, especially player-caused ones, may lead into negotiation, capture, ransom, or rescue structures.

### Law 3 — The Player Must Not Be Ejected
A player who loses a main character should still have viable continued play through weaker or developing characters.

### Law 4 — Continuity Must Not Trivialize Death
Backup paths are a continuity measure, not an undo button.

## Death State Model

Neo UO should eventually support a state-based defeat model rather than a binary alive/dead model.

### Suggested State Set
- Normal
- Downed
- Negotiation
- Captured
- Released
- Executed
- Dead / Retired

The MVP does not need the full model, but the long-term system should be built with state-aware thinking.

## Defeat Routing Doctrine

### Non-Player Defeat
If a creature, environmental danger, or non-player threat kills the player, the system should default toward real character death or retirement logic.

### Player-Caused Defeat
If a player or player-linked combat source causes the decisive defeat, the system may permit a negotiation or leverage layer before final death.

### Important Principle
The project should not treat every lethal event as identical.
Who defeated the player matters.
Where the defeat happened may matter.
What state the player was already in may matter.

## Continuity Model

### Account-Level Continuity
Players should be allowed to maintain multiple developing characters.

This exists to prevent complete restart paralysis when a main dies.

### Intended Feel
A player who loses a veteran character should feel:
- demoted,
- weakened,
- set back,
- but not erased from the game.

### Continuity Without Cheapening Loss
Backup characters should be:
- viable,
- weaker,
- less prestigious,
- less complete,
- and slower to grow safely than a long-lived main.

## Multiple Character Doctrine

### Why Multiple Characters Exist
- soften permadeath deflation
- support different roles or developmental paths
- allow a player to keep participating after major loss
- support later political and rescue systems

### What Multiple Characters Must Not Become
- unlimited mule networks
- riskless scouting webs
- economy exploit tools
- easy death replacement factories

## Experimental Directions

The following discussed ideas should remain preserved here as real design-space targets:

### Defeat Outcome Variants
- some important player-caused defeats may lead to negotiation instead of immediate death
- some major social defeats may later permit capture or ransom structures
- NPC or monster-caused death should remain harsher and closer to true loss

### Continuity Variants
- a player may maintain several developing characters
- those characters may be trained partly in safer conditions, but at heavily reduced efficiency
- the intent is to avoid full player ejection, not to nullify death

### Main vs Backup Philosophy
- a main should feel lived-in, prestigious, and hard-earned
- a backup should feel viable but clearly weaker
- death should create demotion, not total account paralysis

### Capture-State Concepts
- some defeated characters may later enter a captured state
- the player should still be able to use another character
- capture should create urgency and politics, not forced idle babysitting

### Hero-Loss Importance
- death or capture of a major long-lived character should matter to guilds and rivals
- not every life is equal once world memory develops

These are preserved discussion targets, not locked final rules.

## MVP Version

The MVP version of death and continuity should likely include:
- one clear death consequence model
- backup-character allowance
- clear difference between main-world loss and continued account participation
- no full capture politics yet unless the implementation path is unexpectedly easy

### MVP Objectives
- death hurts
- player can keep playing
- weaker backups are meaningfully helpful
- replacement is not instant equivalence

## Later Expansion Version

Later phases may add:
- negotiation windows
- capture states
- rescue states
- execution states
- prison or holding logic
- guild-level hostage leverage
- political exchange systems

## Not Yet Canonized

The following are still intentionally unresolved:
- exact number of backup characters
- exact death-vs-retirement handling model
- exact capture eligibility rules
- exact continuity progression speed
- exact guild leverage rules around living prisoners

## Design Risks

### Risk: Permadeath Deflation
Players may disengage completely after a meaningful death.

Mitigation:
- backup characters
- continuity framing
- clear post-loss viability

### Risk: Cheapened Death
Too much continuity may flatten the emotional importance of death.

Mitigation:
- make backup characters materially weaker
- keep dangerous progression superior
- preserve prestige loss

### Risk: Alt Abuse
Multiple characters may become optimization abuse tools.

Mitigation:
- limit active value overlap
- sharply separate continuity from exploitation
- keep risk and scarcity meaningful

## Implementation Notes

Early implementation should likely avoid overcomplicated prison or political logic.
Start with a stable death-routing foundation.

First likely implementation questions:
- where player death logic is intercepted
- how continuity is represented at account level
- what happens on character retirement
- how to preserve auditability and restore options during development

## Open Questions

- what exact number of backup characters is healthy?
- should character death be true deletion, retirement, or locked unavailability?
- what is the first version of player-caused defeat routing?
- when should capture become eligible?
- what account rules prevent alt abuse cleanly?

## Current Direction

Neo UO should treat death as meaningful character consequence while preserving player continuity through weaker alternate lives.
