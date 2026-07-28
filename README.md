# Neo UO

Neo UO is a survival-war sandbox built on the Ultima Online chassis.

This repository is the project headquarters for Neo UO. It organizes game vision, system doctrine, milestone records, architecture notes, task packets, testing summaries, and future public-facing project material.

## What This Repository Is

This repo supports both internal build work and later public-facing presentation. Neo UO is not being designed as a conventional UO shard with minor modifiers. It is being built as a distinct open-world survival-war experience where life has weight, movement has consequence, and conflict often becomes a hunt rather than a disposable reset fight.

## Repository Structure

- `00_governance` - project charter, design constitution, decision principles
- `01_logs` - change tracking, decision history, milestone records, session notes
- `02_architecture` - repo map, codebase audit, implementation architecture
- `03_operations` - local development and operational workflows
- `04_tasks` - backlog, milestones, current roadmap execution state
- `05_agent` - handoffs, task packets, prompts, and execution workflows for agents
- `06_design` - master PRD, roadmap, system doctrine, core design pages
- `07_umg` - UMG-specific project overlays and context
- `08_testing` - test plans, acceptance summaries, playtest notes, and balance observations
- `09_reference` - glossary, genre framing, and reference notes

## Current Project State

Neo UO has moved beyond early planning into accepted AIGM companion implementation work.

The current accepted baseline includes:

- a functioning AIGM companion framework
- persistent UMG Sleeves
- a PreviewOnly Composer authoring path
- immutable version rollback with encoding repair
- server-side Sleeve access through command, context menu, and Gump flows
- normalized companion inventories for the registered live AIGM roster
- a server-authoritative backpack marker contract for client discovery
- a reproducible ClassicUO NativeAOT build lane
- accepted ClassicUO companion paperdoll Sleeve access through a source-only client overlay
- a reversible live-client deployment lane with rollback artifacts preserved

Accepted server hash:

`4AC823D6532C723FC4ADD0A128E2FBE35A1A4C8F3E09DE0101832090AA7F3FF0`

Accepted UMG version baseline hash:

`0EB27E13320CDC327597662334D8220F87DD47C94F5011DB2867E93A8D1D6C2F`

## Current Task

Active task:

`Phase64D1D - Full Skills-Gump Sleeve Organizer`

Next queued tasks:

- `Phase64D1E - Selective Sleeve Descent Preview Runtime`
- movement and waypoint observability after cognition interface work

## Publication Boundary

This repository records sanitized project memory, architecture, task, and test state. It must not contain private saves, accounts, runtime databases, credentials, logs with account data, audit ZIP contents, built DLL/EXE/PDB artifacts, or private screenshots.

## Notes

This repository is expected to evolve. The structure should remain stable while the project state deepens.
