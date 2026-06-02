# AIGM Companion Reactive Self-Bandaging

Date: 2026-06-01

## Intent

This note records the change from fake instant self-healing to native shard-timed self-bandaging for Dakeyras and Danyal.

Desired behavior:
- companions should bandage themselves automatically when they take damage in combat
- self-bandaging should use the real shard healing timer
- healing should feel like in-game UO bandaging, not custom instant HP restoration

## Design outcome

Reactive self-healing now uses the shard's native bandage flow instead of a custom direct-hitpoint restore.

### Meaning
- real bandage begin
- real delay
- real success/failure timing
- avoids duplicate start while a bandage is already in progress

## Auto trigger behavior

Reactive support now attempts self-bandaging when:
- the companion is under attack
- the companion is injured at all

This replaces the older behavior that only attempted support healing once the companion dropped to a much lower health threshold.

## Practical outcome

The intended result is:
- companion takes damage
- companion begins self-bandaging automatically
- native shard timer resolves the heal
- repeated spam attempts are reduced while an active bandage context exists

## Remaining follow-up areas
- normalize non-self support/bandage paths onto native mechanics too
- refine how combat pressure and support timing interact during travel/tracking
