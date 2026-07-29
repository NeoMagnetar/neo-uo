# Phase64D1E Implementation Handoff

## Accepted State

Phase64D1E is accepted as a PreviewOnly runtime. It derives a Runtime Activation Graph from an approved Operational Layout, evaluates deterministic typed triggers, gates capability and governance, selects one leader per branch family, suspends losing siblings, compiles a typed intent proposal, maps the intended deterministic adapter, and emits a bounded structured receipt.

## Non-Dispatch Rule

The runtime ends at `PREVIEW_ONLY_NOT_DISPATCHED`. Adapter invocation attempts and invocations must remain zero until a later activation phase explicitly changes the dispatch boundary.

## Implementation Surface

- Runtime graph model and builder
- Situation snapshot model
- Preview runtime selector
- Ephemeral state and trace service
- Passive preview watch service
- `[umgdescent]` command surface
- Skills-Gump Runtime Preview page

## Do Not Change

- Account credentials
- Composer sidecars
- Operational Layout sidecars
- companion backpacks
- ClassicUO binaries
- durable launchers

