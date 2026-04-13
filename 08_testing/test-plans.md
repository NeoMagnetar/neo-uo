# Test Plans

## Purpose

Define how Neo UO testing should be structured so that the project learns from play instead of collecting vague impressions.

The goal of testing is not just to find bugs. It is to verify whether the intended experience is actually happening.

## Testing Philosophy

Neo UO testing should answer both kinds of questions:

### Mechanical Questions

- does the system function?
- does it break?
- does it behave consistently?

### Experience Questions

- does this feel like Neo UO?
- does it create tension instead of annoyance?
- does it preserve consequence without paralysis?
- does it feel distinct from ordinary UO?

## Core Testing Rule

Every meaningful test should be built around:

- a specific hypothesis
- a repeatable setup
- a narrow focus
- and a recorded interpretation

## Test Structure Template

Each test plan should eventually document:

- title
- purpose
- systems touched
- setup
- execution steps
- expected result
- failure signals
- notes to record
- next likely action

## Phase-Oriented Test Priorities

### Test Group A — Local Baseline

#### A1 — World Entry and Control

Purpose:
Confirm that local entry, movement, and basic action flow work reliably.

Questions:

- can test characters enter reliably?
- can they move and interact normally?
- can setup be repeated without major friction?

#### A2 — Baseline Combat Feel

Purpose:
Establish what stock or current combat pacing feels like before major changes.

Questions:

- how fast do fights resolve?
- how much recovery currently exists?
- what feels disposable or too immediate?

### Test Group B — Death and Continuity

#### B1 — Loss Meaningfulness Test

Purpose:
Check whether loss feels meaningful rather than cosmetic.

Questions:

- does a defeat change future play meaningfully?
- does the player still have a reason to continue?

#### B2 — Continuity Viability Test

Purpose:
Check whether weaker alternate characters preserve play without trivializing loss.

Questions:

- does the backup feel viable but weaker?
- does the main still feel more valuable?

#### B3 — Deflation Risk Test

Purpose:
Check whether a defeat creates disengagement instead of tension.

Questions:

- after loss, does the tester still want to keep playing?
- does the project feel harsh in a good way or a bad way?

### Test Group C — Recovery and Wounds

#### C1 — Stabilization vs Full Recovery

Purpose:
Test whether players can remain active after a bad fight without feeling fully reset.

Questions:

- can a player recover enough to keep moving?
- do they still feel vulnerable?
- does the system create consequence without dead time?

#### C2 — Re-Engagement Risk

Purpose:
Test what it feels like to re-enter danger while not fully restored.

Questions:

- does a wounded player make meaningfully different decisions?
- does the game create real caution?

### Test Group D — Tracking and Hunts

#### D1 — Tracking Readability

Purpose:
Test whether clue-based tracking is understandable.

Questions:

- can a player interpret the clue?
- can they use it to make a real decision?
- is it too precise or too vague?

#### D2 — Hunt Flow Test

Purpose:
See whether tracking plus movement creates an actual hunt instead of a button press.

Questions:

- does the target still have room to evade?
- does the tracker feel rewarded for geography and timing?

### Test Group E — Combat Identity

#### E1 — Slower Fight Tension Test

Purpose:
Test whether increased survivability or reduced reset healing feels more tactical rather than spongey.

Questions:

- do fights stay intense?
- do they produce aftermath?
- do they remain readable?

#### E2 — Anti-Zerg Pressure Test

Purpose:
Test whether dense group behavior loses efficiency in a way that feels learnable and fair.

Questions:

- can groups still coordinate effectively?
- does brainless stacking feel weaker?
- does solo survival improve meaningfully?

### Test Group F — Ecology and Movement Pressure

#### F1 — Sparse World Tension Test

Purpose:
Check whether reduced density still leaves the world feeling alive and dangerous.

Questions:

- does the world feel quieter without feeling dead?
- do remaining encounters matter more?

#### F2 — Burden and Extraction Test

Purpose:
Check whether weight and carrying choices create meaningful tradeoffs.

Questions:

- do players feel pressure when loaded?
- do route and stash choices become more meaningful?

#### F3 — Pursuit Spillover Test

Purpose:
Check whether fleeing one danger into another creates real geography instead of annoyance.

Questions:

- does the map start to feel strategically alive?
- does escape remain possible?

## Testing Notes Standard

For every major test, record:

- what the hypothesis was
- what actually happened
- what felt strong
- what felt bad
- whether the result was design failure, tuning failure, or setup failure
- what should happen next

## Early Test Priority Order

The first major test priority order should be:

- baseline local stability
- death and continuity feel
- recovery and wound-state feel
- tracking clue readability
- combat pacing direction
- ecology and movement pressure
- anti-zerg pressure
- later social and item systems

## Current Direction

Neo UO testing should be hypothesis-driven and experience-aware, with early focus on proving the project’s identity rather than broad feature coverage.
