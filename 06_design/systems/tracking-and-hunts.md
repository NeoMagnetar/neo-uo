# Tracking and Hunts

## Purpose

Define how Neo UO transforms pursuit from certainty-based target acquisition into evidence-driven world gameplay.

This is one of the core identity systems. Tracking is not meant to function like a target arrow or direct pointer. It should create a hunt.

## Player Experience Goal

The player should feel that:

- tracking gives clues, not certainty
- the hunt is a process
- geography and timing matter
- and a clever target may escape even if discovered

## Design Position

Neo UO should remove or de-emphasize direct certainty tracking and replace it with perishable evidence.

Tracking must become:

- investigative
- time-sensitive
- and spatially meaningful

## Core Doctrine

### Law 1 — Tracking Provides Evidence, Not a Lock

The system should point the player toward recent movement patterns, not directly place the victim in their hands.

### Law 2 — Time Must Matter

Recent movement should be easier to read than old movement.

### Law 3 — The World Must Matter

Roads, wilderness, burden, injury, and territory should eventually affect how readable a trail is.

## Tracking Output Philosophy

The tracking system should eventually lean toward information like:

- last known direction
- rough recent coordinate region
- distance tendency
- freshness quality
- trail strength or confidence

It should not simply say:

- target exact position
- direct arrow forever
- target is guaranteed here

## Tracking Signal Model

The best long-term version likely uses some combination of:

- freshness
- strength
- direction
- environmental context
- interruption points

### Fresh Trail

More reliable, more directional, stronger confidence.

### Aging Trail

Less precise, more ambiguous, easier to lose.

### Broken Trail

Possible in cities, dense zones, water, protected areas, or deliberate counter-tracking contexts later.

## Hunt Loop

The intended hunt loop is:

identify recent trace -> choose route -> close distance -> reacquire evidence -> predict movement -> risk contact or lose trail

This should feel more like pursuit than scan-and-delete.

## Interaction With Other Systems

Tracking should later interact with:

- wound states
- burden / load
- mount or movement state
- stealth and concealment
- environmental exposure
- territory knowledge
- creature and patrol threat overlap

## MVP Version

The MVP should likely include:

- no standard certainty arrow
- some directional or coordinate-adjacent clue output
- time-limited recent movement logic
- a usable but imperfect result

### MVP Goal

Make tracking feel immediately different from stock UO even if the system is still simple.

## Later Expansion Version

Later versions may add:

- stronger trail quality logic
- region-sensitive tracking difficulty
- bleeding / wound trace influence
- burden-based trail influence
- counter-tracking skills or tools
- rumor or social tracking systems for renowned targets

## Design Risks

### Risk: Too Vague to Be Useful

If tracking gives too little, nobody uses it.

Mitigation:

- make early clue output readable enough to learn
- iterate precision rather than starting useless

### Risk: Too Precise

If tracking is too strong, hunts collapse into target delivery.

Mitigation:

- restrict certainty
- decay information
- reward reacquisition and map knowledge

### Risk: UI Friction

If clues are hard to understand, the hunt may feel awkward rather than exciting.

Mitigation:

- start with clean, interpretable outputs
- preserve room for richer systems later

## Implementation Notes

Tracking design should begin with the simplest prototype that proves the doctrine:

- recent target reference
- directional clue
- freshness window
- time decay

Only after that should the system deepen.

## Open Questions

- what exact clue format should the player receive?
- how long should a trail persist?
- how often can tracking be reused?
- how should wounded, burdened, or stealthing players affect trail quality?
- what are the first counter-tracking tools?

## Current Direction

Tracking should become a structured clue system that creates hunts, not a certainty-based targeting aid.
