# Implementation Notes

## Purpose

Bridge the design doctrine into practical implementation thinking without prematurely locking every solution.

This file should help answer:

- what to prototype first
- what to postpone
- what should remain configurable
- and where design ambition must be narrowed to become testable

## Implementation Philosophy

Neo UO should be implemented in vertical slices where possible.

A vertical slice means:

- one clear design question
- one narrow implementation target
- one testable behavior change
- and one structured evaluation loop

This is better than making many disconnected partial changes at once.

## Early Implementation Principles

### Principle 1 — Implement Identity First

Prioritize the systems that most strongly prove Neo UO is different:

- death and continuity
- recovery and wounds
- tracking and hunts
- progression context
- ecology pressure

### Principle 2 — Prototype Narrow, Evaluate Wide

A prototype can be mechanically small but experientially important.

### Principle 3 — Avoid Full-System Ambition Too Early

Do not build the final capture network, final item renown system, or full siege architecture before the project proves its center.

### Principle 4 — Prefer Configurable Tuning Where Practical

Many early design questions are tuning questions.
Where possible, expose values so iteration does not require deep rewrites every time.

## Best Early Vertical Slices

### Slice 1 — Death and Continuity Skeleton

Question:
Can Neo UO create meaningful loss without ejecting the player?

Likely components:

- death-routing hook
- first continuity rules
- basic post-loss account behavior

### Slice 2 — Recovery and Wound Prototype

Question:
Can players survive a fight and remain meaningfully disadvantaged without feeling stuck?

Likely components:

- slower full recovery
- weaker instant reset healing
- first wounded-state representation

### Slice 3 — Tracking Prototype

Question:
Can clue-based tracking feel immediately distinct and readable?

Likely components:

- replacement for certainty output
- simple directional clue
- freshness / decay window

### Slice 4 — Progression Context Prototype

Question:
Can dangerous-world growth clearly outpace safe growth without making safe continuity useless?

Likely components:

- zone or context check
- gain-rate modifier
- initial category restrictions

### Slice 5 — Ecology Pressure Pass

Question:
Can the world feel quieter but more meaningful with lower density and more distinct threat behavior assumptions?

Likely components:

- density tuning
- pressure-region assumptions
- early behavior class notes

## Systems That Should Be Delayed

Delay full implementation of these until the center is proven:

- full capture / rescue mechanics
- full renowned item circulation systems
- stronghold and siege logic
- full deity and utility networks
- broad arena mode content set

## Tuning vs System Questions

Many Neo UO ideas must be separated into two categories.

### Tuning Questions

Examples:

- how much slower should recovery be?
- how much lower should safe gain be?
- how long should tracks persist?
- how much density reduction feels right?

### System Questions

Examples:

- does wound-state exist as a distinct layer?
- does tracking output use direction instead of certainty?
- does capture exist as a state?
- do hidden stashes exist later at all?

The system question should usually be answered first.
Then tuning should follow.

## Configuration Guidance

Where practical, prototype systems should expose:

- recovery timing
- gain multipliers
- tracking freshness window
- movement or burden modifiers
- density assumptions

This reduces iteration friction.

## Documentation Link Rule

Whenever a meaningful implementation slice begins, connect it to:

- one design file
- one task item
- one test plan target

This keeps the repo coherent.

## Current Direction

The next implementation-ready work should focus on vertical slices that prove:

- meaningful loss
- meaningful incomplete recovery
- evidence-based tracking
- contextual progression
- sparse but pressuring world behavior
