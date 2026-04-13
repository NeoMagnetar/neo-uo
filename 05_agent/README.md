# Agent

## Purpose

This lane holds machine-facing materials that help agents operate cleanly inside the Neo UO repository.

It exists to make future agent work:

- consistent
- structured
- reusable
- and easier to hand off across sessions

## What Belongs Here

- handoff blocks
- reusable prompts
- repo workflows
- templates for recurring doc tasks
- structured task-execution helpers

## What Does Not Belong Here

This lane should not become the source of truth for:

- game doctrine
- PRD content
- final system rules
- roadmap intent

Those belong elsewhere:

- doctrine and design in `06_design`
- governance in `00_governance`
- execution state in `04_tasks`
- testing truth in `08_testing`

## Agent Lane Role

The role of this lane is support, not authority.

It should help an agent:

- update files correctly
- create new pages consistently
- preserve repo structure
- avoid duplicating project truth in the wrong lane

## Good Agent Outputs

Good agent outputs should:

- target clearly named files
- preserve the numbered-lane repo grammar
- separate doctrine from execution notes
- avoid inventing unnecessary folders
- use consistent markdown structures when asked

## Current Templates

The templates folder exists to support repeated work such as:

- system page creation
- backlog item formatting
- decision logging
- playtest entry capture

## Current Direction

The agent lane should gradually become a quality-of-execution layer for Neo UO, improving consistency without replacing the project’s actual design files.
