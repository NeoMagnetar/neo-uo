# Local Dev Operations

## Purpose

Define the working operational baseline for local Neo UO development and testing.

This file is not a generic runbook for every future environment. It exists to support repeatable local iteration during the early project phases, when the main need is to get into the game quickly, test specific systems, and record findings without unnecessary setup friction.

## Operational Goal

Local development should support:

- repeatable startup
- rapid test execution
- safe experimentation
- quick rollback or reset when needed
- and simple handoff between planning and actual playtesting

The local environment exists to answer design questions, not to simulate final live operations.

## Core Operating Principle

The local environment should optimize for:

- speed to test
- clarity
- and stability of iteration

It should not optimize first for:

- full production realism
- large player concurrency
- or public polish

## Local Dev Use Cases

### Use Case 1 — Solo Verification

Confirm that a system builds, launches, and behaves directionally as expected.

### Use Case 2 — Two-Person Loop Testing

Allow the project owner and a second tester to validate combat, tracking, movement, death, or recovery behavior in real play.

### Use Case 3 — GM-Aided Rapid Iteration

Use controlled commands or setup shortcuts to repeatedly place characters in meaningful test states without wasting time.

### Use Case 4 — Focused Systems Testing

Test one specific rule area at a time:

- death-routing
- backup continuity assumptions
- tracking clue output
- wound and recovery behavior
- ecology and movement pressure
- burden and extraction pressure later

## Local Environment Standard

The local build should eventually support the following minimum conditions:

- shard launches reliably
- test accounts can log in reliably
- GM or equivalent administrative access exists for setup
- characters can be placed into test states quickly
- server restart flow is understood
- important config assumptions are documented

## Early Local Testing Principles

### Principle 1 — Test One Meaningful Thing at a Time

Avoid broad messy play sessions where too many systems overlap before their baseline is understood.

### Principle 2 — Favor Repeatable Scenarios

A good local test is something that can be rerun with only a few changed variables.

### Principle 3 — Separate Design Discovery From Operational Noise

If a test fails because of setup friction, note the operational failure separately from the design question.

### Principle 4 — Preserve a Fast Return to Play

Local development loses value if every test session requires too much setup or recovery work.

## Minimum Local Session Flow

A healthy local session should eventually look like this:

- launch local server
- confirm login and admin access
- prepare test characters
- run a single focused test scenario
- record outcome immediately
- restart or reset if needed
- rerun with one or two changed assumptions

## Early Operational Needs

The following items should be documented as soon as they become stable:

- startup sequence
- local file/config assumptions
- GM setup steps
- account creation assumptions
- character setup shortcuts
- restart flow
- known failure states
- recovery steps after bad test changes

## Recommended Operational Boundaries

### Keep Local Testing Lean

Do not wait for full polish before starting practical testing.

### Allow Controlled Shortcuts

During local iteration, it is acceptable to use setup tools that would not exist in the final player-facing game.

### Avoid Polluting Design Findings

When using shortcuts, always note that the scenario was artificially prepared.

## Session Documentation Standard

Every meaningful local session should eventually record:

- date
- tester(s)
- build or rule state
- test focus
- setup assumptions
- observed result
- interpretation
- next action

This should pair with `08_testing/playtest-notes.md` and `08_testing/test-plans.md`.

## Immediate Next Operational Tasks

The next operational pass should eventually add:

- exact local startup steps
- exact local login/test account flow
- exact GM setup notes
- exact repeatable test workflow

Those details are intentionally not invented here until the local environment is confirmed.

## Current Direction

Local development operations should stay lightweight, repeatable, and fast enough to support frequent identity-focused testing.
