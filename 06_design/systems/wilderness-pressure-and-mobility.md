# Wilderness Pressure and Mobility

## Purpose

Define how movement, pursuit, burden, territory, predators, prey, and patrols create pressure during travel.

This system turns the world into an active force rather than a backdrop between fights.

## Player Experience Goal

The player should feel that:

- travel itself is gameplay
- moving through the world requires decisions
- the wilderness pressures them differently depending on what they are, what they carry, and where they go
- and escape is possible but not trivial

## Design Position

Neo UO should use behavioral asymmetry rather than only stat inflation to make creatures and patrols meaningful.

Different entities should create different world problems.

## Core Doctrine

### Law 1 — Travel Must Matter

Movement should not be empty dead time between events.

### Law 2 — Pressure Must Be Layered

A player should not face only one threat at a time. Route and territory can turn one escape into another risk.

### Law 3 — Escape Must Usually Be Possible

The world should pressure movement, not simply trap the player unfairly.

## Behavioral Asymmetry Model

Different entities should create different pressures.

### Apex Predators

Examples:

- territorial pressure
- pursuit over distance
- punishment for entering the wrong space
- forced rerouting

### Prey Animals

Examples:

- evasive movement
- speed advantage
- requirement for correct tools or ambush
- hunt stages that change after wounding

### Patrol NPCs

Examples:

- road control
- scanning behavior
- visibility pressure
- area denial or forced detour

### Monsters

Examples:

- zone threat
- pursuit variation
- tactical ability pressure
- environmental danger overlap

## Mobility Doctrine

Movement should be affected eventually by:

- burden
- wound state
- terrain
- preparedness
- possibly later weather or region identity if ever desired

Neo UO does not need every realism layer at once. It needs meaningful movement choices.

## Pursuit Doctrine

Pursuit should:

- create pressure
- force decisions
- sometimes deny the shortest route
- sometimes push players into worse terrain or rival territory

Pursuit should not:

- guarantee death
- remain infinite without logic
- remove all player agency

## Territorial Spillover

One of the strongest intended world behaviors is that escaping one danger may carry the player into another.

This creates:

- real geography
- route knowledge value
- local survival expertise
- dynamic risk chains

## MVP Version

The MVP should likely include:

- early burden or movement-pressure assumptions
- simple behavioral differentiation in design targets
- some basic pursuit identity ideas for later implementation
- no need for full apex behavior simulation immediately

### MVP Goal

Make the team think about travel as gameplay from the start.

## Later Expansion Version

Later versions may add:

- true predator tracking behavior
- wounded prey behavior
- patrol scan and pursuit logic
- burden-linked movement penalties
- region-specific travel pressure
- stronger escape / concealment interactions

## Design Risks

### Risk: Pursuit Becomes Sticky Misery

Players may feel constantly dragged by unavoidable follow logic.

Mitigation:

- preserve eventual disengage rules
- use territory and distance logic
- keep pressure high without making survival impossible

### Risk: Mobility Pressure Becomes Tedium

Carrying or routing choices may stop feeling interesting and start feeling annoying.

Mitigation:

- tune pressure carefully
- preserve meaningful choices instead of excessive restriction

### Risk: Behavior Is Unclear

If players cannot learn why entities behave as they do, the world feels arbitrary.

Mitigation:

- keep behavior readable
- teach by repeated consistent rules

## Implementation Notes

Do not attempt the final deep ecology simulation first.

Start by documenting:

- desired behavior classes
- desired pressure outcomes
- what burden and pursuit are supposed to change in player decisions

## Open Questions

- how long should apex pursuit last?
- how should wounded prey change?
- what are the first burden penalties worth testing?
- how much should patrols control road use?
- how should players recognize that they are entering different danger logic?

## Current Direction

Neo UO should make travel, pursuit, and territorial movement part of the core game rather than mere transition time.
