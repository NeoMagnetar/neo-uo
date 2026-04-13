# Launcher Operations

## Purpose

Define how Neo UO should think about launching, session entry, and player-facing access flow over time.

This file is not yet a final launcher specification. It exists to keep operational thinking organized as the project moves from local testing toward a more public-facing state.

## Operational Role

Launcher operations should eventually support three distinct phases:

### Phase A — Internal Local Use

Used by the project owner and trusted testers to:

- launch the local shard
- confirm build state
- enter test sessions quickly
- reduce startup friction

### Phase B — Controlled External Testing

Used by invited playtesters or limited participants to:

- understand the current test state
- enter the right environment
- know the current ruleset or test focus
- avoid confusion about what is and is not active

### Phase C — Public-Facing Access

Used by future public players to:

- understand what Neo UO is
- understand what state the project is in
- enter the shard cleanly
- access version and change-state information

## Current Priority

The current priority is not a polished public launcher.
The current priority is a stable and understandable session-start flow for local and controlled testing.

## Core Launcher Principles

### Principle 1 — Clarity Over Flash

The launcher or entry flow should always communicate what environment the user is entering.

### Principle 2 — State Must Be Visible

Players and testers should be able to tell:

- what build or phase they are on
- whether systems are experimental
- whether a session is test-focused or general

### Principle 3 — Access Must Match Environment

Local development, invited testing, and public-facing use may require different entry assumptions.

### Principle 4 — The Launcher Is Part of the Experience Framing

Even before the game begins, the player should understand that Neo UO is a distinct world, not just an ordinary shard.

## Early Operational Needs

Before a real launcher is designed, the repo should still support a consistent launch-entry understanding.

The following should eventually be clear:

- how the shard is launched locally
- how testers know what they are joining
- how current build status is communicated
- where release or patch notes live
- what changes are active in the current test state

## Session-State Communication

Any future launcher or access layer should ideally show:

- environment name
- build or ruleset label
- current test focus if applicable
- known experimental systems
- latest notable changes

This helps avoid confusion during rapid iteration.

## Local-First Practical Standard

Until public access is relevant, launcher operations should stay lightweight.

That means:

- quick startup
- low friction
- easy confirmation of current environment
- no premature overdesign

## Future Public-Face Role

Later, launcher operations may become one of the strongest public-framing surfaces for the project.

A future launcher could help communicate:

- the survival-war identity
- the difference between world mode and arena mode
- current server state
- current testing or release notes
- entry expectations

## Risks

### Risk: Overbuilding Too Early

Creating a polished launcher before the core experience is proven wastes focus.

Mitigation:

- keep launcher thinking lightweight for now
- prioritize clarity, not feature depth

### Risk: Session Confusion

Testers may not understand which systems are active or unstable.

Mitigation:

- expose build or ruleset state clearly
- connect launcher-facing info to release notes and change log

## Current Direction

Launcher operations should remain lightweight for now, but must eventually communicate project state clearly enough that both testers and future public players understand what kind of Neo UO experience they are entering.
