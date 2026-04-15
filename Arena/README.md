# Arena

The Arena section is the design home for the portable arena rules framework.

The first controlled test location is the Britain graveyard test region. That region is a test footprint, not the long-term identity of the system. The durable goal is a reusable law layer that can be applied to multiple arena region instances later.

Phase 1 is limited to the phase 1 enforcement shell. It is not a full MOBA, not a full league system, and not a full arena game loop.

## Navigation
- `00_scope` defines system boundaries and intent.
- `01_rules` defines arena law in design language.
- `02_profiles` defines reusable arena rules profiles.
- `03_regions` defines concrete arena region instances.
- `04_modes` reserves future gameplay layers.
- `05_testing` defines behavioral verification.
- `06_backlog` captures deferred work.
- `07_brainstorm` stores non-canonical ideation.
- `08_decisions` stores chosen direction changes.
- `09_references` stores external or implementation-facing reference notes.

## Current assumption
The initial enforcement shell should cover region boundary awareness, no mounts, no recall, no gate travel, entry and exit handling, and rules messaging. Other arena behavior remains deferred.