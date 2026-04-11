# Neo UO

This repository is the project headquarters for the hardcore one-life Felucca shard.

It exists to hold project memory, planning, logs, architecture decisions, operations guidance, testing notes, agent instructions, and project-specific UMG materials.

This is not the main implementation repository. Routine code changes should not be centered here.

## Purpose

This repo is the operating brain of the project.

It is meant to preserve:
- continuity
- planning clarity
- decision history
- agent alignment
- documentation discipline
- long-term project memory

## Repository rules

- Read this README first.
- Treat approved architecture and operations docs as higher authority than brainstorm notes.
- Do not assume idea files are approved implementation unless they are explicitly marked approved.
- Do not store secrets, credentials, tokens, or private keys here.
- Do not store large binary backups or runtime save archives here.
- Do not use this repo as a general dumping ground for random scratch files.
- Keep this repo focused on planning, documentation, guidance, and structured project memory.

## Primary usage

Use this repo for:
- publish logs
- session notes
- decision tracking
- architecture planning
- operations procedures
- task packets
- agent guidance
- shard design documents
- testing notes
- project-specific UMG structure

## Directory intent

### `00_governance`
Project rules, authority boundaries, operating rules, and repo governance.

### `01_logs`
Publish logs, session logs, decision logs, and project history.

### `02_architecture`
Approved structural documents describing how the shard and project are organized.

### `03_operations`
Environment setup, backup procedures, restore procedures, ports, paths, and operator-facing run guidance.

### `04_tasks`
Structured work packets and task state.

- `active` = current work
- `backlog` = queued work
- `completed` = finished work
- `archived` = old or retired work

### `05_agent`
OpenClaw-facing instructions, rules of engagement, templates, and agent operating notes.

### `06_design`
Shard design documents, system concepts, mode concepts, world-shape planning, and gameplay design notes.

### `07_umg`
Project-relevant UMG sleeves, NeoBlocks, stacks, and MOLT maps.

### `08_testing`
Test plans, test notes, validation records, and bug triage.

### `09_reference`
Glossary, stable references, tool notes, and supporting project reference material.

## OpenClaw startup behavior

When OpenClaw is pointed at this repo, it should:
1. read this README first
2. read the relevant file in `05_agent`
3. read the active task packet in `04_tasks/active` if one exists
4. read the relevant architecture or operations docs before performing structured work
5. avoid treating brainstorm material as approved implementation unless explicitly marked approved

## Bootstrap note

This repo is intentionally scaffold-only at initial setup.

Most directories exist only to establish a stable operating structure.
Do not auto-populate the repo beyond the root README and `.gitkeep` placeholders unless explicitly instructed.
