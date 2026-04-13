# Combat Recovery and Wounds

## Purpose

Define how Neo UO handles injury, stabilization, incomplete recovery, and prolonged combat aftermath.

This system is critical to the survival-war identity. Neo UO should not feel like a game where every fight resets cleanly after a few seconds. At the same time, it should not trap players in excessive downtime.

## Player Experience Goal

The player should feel that:

- surviving a fight matters
- escaping does not erase the cost of the fight
- wounds affect future choices
- and full readiness is something that must be regained rather than assumed

## Design Position

Neo UO should use layered recovery rather than a single flat health recovery model.

The project should prefer:

- stabilization
- wounded functionality
- and delayed full restoration

over:

- instant combat reset
- or
- being stuck at near-death for hours

## Core Recovery Doctrine

### Law 1 — Escaping Should Save a Life, Not Erase a Fight

If a player barely survives, they should not instantly become fresh again.

### Law 2 — Recovery Must Matter Without Becoming Dead Time

The aftermath of combat must feel meaningful, but the player must still be able to continue participating.

### Law 3 — Wounds Are Better Than Long-Term Low HP

The best way to preserve consequence is not necessarily to leave players at tiny HP values for long periods. A better model is to stabilize the player while reducing their deeper readiness.

## Layered Recovery Model

Neo UO should distinguish at least three layers.

### Layer 1 — Immediate Current HP

The visible health currently available in active combat.

### Layer 2 — Wounded Capacity

A reduced effective readiness caused by severe injury.
This may lower practical combat ceiling even if current HP rises somewhat.

### Layer 3 — Full Restoration

The return to true peak readiness.
This should take longer and require better conditions.

## Desired Player Experience

A player should be able to say:

I got away
I am alive
I can still move and function
but I am not ready for another full fight

That is the target feel.

## Stabilization Doctrine

Stabilization should:

- prevent immediate collapse
- restore minimal playability
- allow retreat, travel, hiding, and short-term survival
- not fully reset the player

This is the most important distinction in the system.

## Full Recovery Doctrine

Full recovery should be:

- slower
- more meaningful
- safer to do in controlled conditions
- potentially assisted by place, skill, supply, or later support systems

Neo UO should create a real difference between being alive and being fully battle-ready.

## Wound-State Effects

Possible wound-state effects later may include:

- reduced effective combat durability
- reduced sprint or pursuit capacity
- altered tracking trace quality
- worse stealth under pressure
- lower combat confidence or sustain potential

The MVP should not overload wound states with too many penalties at once.

## MVP Version

The MVP should likely include a simplified version of this system:

- slower full recovery than stock UO
- significantly weaker instant healing reset
- meaningful post-fight vulnerability
- a clear distinction between “not dying” and “fully restored”

### MVP Target

Test the feeling of incomplete recovery before introducing large numbers of layered penalties.

## Later Expansion Version

Later versions may add:

- true wound-state categories
- deeper recovery actions
- safe shelter recovery bonuses
- supply-dependent full restoration
- interaction with mobility, stealth, and tracking
- bleeding, trauma, or injury-specific states if they remain readable

## What This System Must Not Become

- pure downtime
- a mandatory logoff tax
- a state where players feel hostage to their session
- a punishment so extreme that they never leave safety

## Design Risks

### Risk: Recovery Downtime Trap

Players spend too much time waiting instead of playing.

Mitigation:

- stabilization before full recovery
- wound state over flat low-HP imprisonment
- careful tuning of recovery windows

### Risk: Combat Feels Mushy

If health is too high without the right recovery structure, fights may lose intensity.

Mitigation:

- distinguish survivability from sponge design
- preserve danger even while slowing reset loops

### Risk: Too Many Penalties

If wounds affect too many systems at once, the player may feel crushed instead of pressured.

Mitigation:

- add wound effects in layers over time
- keep MVP focused

## Implementation Notes

This system should likely be implemented with clear state separation rather than many scattered modifiers.

Likely early implementation concerns:

- health regeneration behavior
- healing spell and potion tuning
- post-combat recovery timing
- wound-state flag or capacity model

## Open Questions

- what is the right stabilization time window?
- what is the right full-recovery time window?
- what removes wound-state penalties?
- how much should wounds affect movement, stealth, or tracking?
- should safe territory or shelter accelerate recovery?

## Current Direction

Neo UO should favor long-term wounds and incomplete readiness over instant reset healing or extreme long-term low-HP imprisonment.
