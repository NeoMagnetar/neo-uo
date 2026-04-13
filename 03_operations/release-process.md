# Release Process

## Purpose

Define how Neo UO records meaningful project progress as the repo moves from planning into implementation and testing.

This is not only about public releases. It is about creating a disciplined rhythm for:

- design shifts
- prototype drops
- test-state changes
- and later public milestone communication

## Core Release Philosophy

A release in Neo UO should mean:

- something changed
- that change can be described
- its purpose is known
- and its risks or open questions are visible

The project should not rely on vague “stuff changed” updates.

## Release Levels

Neo UO should eventually treat releases or milestones in tiers.

### Tier 1 — Documentation / Planning Release

Used when:

- major PRD or doctrine structure changes
- repo architecture stabilizes
- project direction is clarified in a meaningful way

### Tier 2 — Prototype Ruleset Release

Used when:

- a new testable ruleset change exists
- a system prototype becomes playable
- testers need to know what changed and why

### Tier 3 — Playtest Build Release

Used when:

- invited or external testers are expected to use the build
- a snapshot of the current intended experience needs to be communicated clearly

### Tier 4 — Public Milestone Release

Used much later when:

- the project reaches externally meaningful thresholds
- wider communication is needed
- public-facing change summaries matter

## Minimum Release Note Standard

Any meaningful release note should eventually include:

- title
- date
- release type
- scope
- summary of changes
- reason for changes
- known risks or rough edges
- what needs testing next

## Good Release Questions

Before recording a release, ask:

- what changed?
- why did it change?
- what player experience is this meant to affect?
- what still remains uncertain?
- what should be tested immediately after this change?

## Early Project Standard

While Neo UO is still early, a release note can remain lightweight as long as it clearly records:

- the change
- the purpose
- the next testing need

This should pair cleanly with:

- `01_logs/change-log.md`
- `04_tasks/roadmap-status.md`
- `08_testing/playtest-notes.md`

## Suggested Early Release Format

### Release Title

Short descriptive name.

### Type

Documentation, prototype, test build, or milestone.

### Summary

What changed.

### Intent

Why it changed.

### Immediate Risks

What may still be wrong or uncertain.

### Next Test Focus

What should be validated now.

## What This Process Prevents

A good release process helps prevent:

- forgotten context
- unclear project state
- test confusion
- undocumented design shifts
- drift between planning and implementation

## Risks

### Risk: Overformalizing Too Early

If every tiny change becomes a ceremony, iteration slows down.

Mitigation:

- keep early release notes lightweight
- formalize more only as the project grows

### Risk: Under-Documenting Meaningful Changes

If major changes are not recorded clearly, later iteration becomes harder.

Mitigation:

- record any change that affects identity, test expectations, or player-facing behavior

## Current Direction

Neo UO should use a lightweight but disciplined release process that records why meaningful project changes happened and what must be tested next.
