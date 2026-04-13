# Codebase Audit

## Purpose

Map the most likely code and data areas that Neo UO will need to touch in early and mid-stage implementation.

This is not yet a full technical file map. It is a directional audit intended to keep implementation effort aligned with system priorities.

## Audit Philosophy

The early codebase audit should answer:

- where the first identity-defining systems probably live
- which systems are tightly coupled
- and what changes are most likely to cascade into other areas

The goal is to avoid blind implementation.

## Highest-Priority Early Audit Targets

### 1. Player Life-State Logic

#### Why It Matters

Neo UO’s identity depends heavily on death consequence, continuity thinking, negotiation possibility, wound aftermath, and recovery logic.

#### Likely Areas

- player death handlers
- player state transitions
- resurrection / post-death logic
- player status flags or persistent state storage

#### Early Questions

- where is player death routed now?
- what is easiest to intercept?
- how should custom states be stored cleanly?

### 2. Skill Gain and Progression Logic

#### Why It Matters

Safe-vs-dangerous growth and slower meaningful progression are central to the project.

#### Likely Areas

- skill gain calculations
- activity or context-sensitive gain logic
- safe-zone vs dangerous-zone checks
- account or character restrictions relevant to progression

#### Early Questions

- what controls gain rate now?
- how hard is it to apply contextual modifiers?
- what systems distinguish zone or context?

### 3. Combat and Damage Recovery Logic

#### Why It Matters

Combat pacing, incomplete recovery, and wound-state design all depend on this area.

#### Likely Areas

- damage resolution
- health recovery
- healing skills
- spell healing
- potion use and timing
- post-combat timers or states

#### Early Questions

- where are healing and recovery currently determined?
- what is easiest to prototype first: weaker healing, slower full recovery, or wound-state simulation?

### 4. Tracking Logic

#### Why It Matters

Tracking is one of the project’s clearest “this is not normal UO” identity systems.

#### Likely Areas

- tracking skill implementation
- tracking result UI
- target resolution logic
- skill reuse timing
- any directional output methods

#### Early Questions

- how is the current tracking arrow or output determined?
- can clue-based output replace it cleanly?
- what is the simplest first prototype?

### 5. Creature and NPC Behavior

#### Why It Matters

Sparse world pressure requires stronger behavioral distinction, not only fewer mobs.

#### Likely Areas

- creature AI
- patrol behavior
- target pursuit
- flee behavior
- movement or region constraints
- spawn density configuration

#### Early Questions

- how easy is it to tune pursuit persistence?
- how are prey-like behaviors currently handled?
- where is region-specific behavior easiest to hook?

### 6. Item, Storage, and Economy Logic

#### Why It Matters

Scarcity, stashes, and renowned item circulation all rely on later storage and economy work.

#### Likely Areas

- loot generation
- gold generation
- banking
- storage containers
- decay behavior
- item metadata or ownership/state extensions

#### Early Questions

- what is hardest-coded vs configurable?
- how can scarcity be tested without full economy rewrite?
- what storage assumptions are risky to change early?

### 7. Housing and Territory Extensions

#### Why It Matters

Strongholds and territory are later-phase systems, but future feasibility matters.

#### Likely Areas

- housing ownership
- placeable NPCs or vendors
- region control
- damageable entities
- house access and defense assumptions

#### Early Questions

- what can be leveraged for proxy-defense concepts?
- what existing structures are safest to extend later?

## Early Audit Priorities by Phase

### Immediate Audit Priority

- player death / life-state logic
- progression gain logic
- recovery and healing logic
- tracking implementation

### Secondary Audit Priority

- spawn density and ecology behavior
- item/storage assumptions

### Later Audit Priority

- housing / strongholds
- deeper political systems
- item renown and circulation layers

## Audit Output Standard

As the codebase becomes better known, each audited subsystem should eventually record:

- file(s) involved
- current behavior summary
- desired Neo UO behavior summary
- implementation difficulty guess
- risk notes
- prototype recommendation

## Current Direction

The codebase audit should stay tightly coupled to the identity-defining systems first: death, continuity, progression, recovery, tracking, and world pressure.
