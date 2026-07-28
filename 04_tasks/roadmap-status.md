# Roadmap Status

## Current Overall State

Project state: accepted AIGM companion implementation baseline with client integration entering Phase64D1C.

The repository now tracks both long-range product doctrine and the concrete implementation lane for AIGM companion UMG systems. The accepted baseline through Phase64D1B includes PreviewOnly UMG Composer work, server-authoritative Sleeve access, normalized companion backpacks, and a marker contract for ClassicUO client discovery.

## Accepted Technical Baseline

- Phase64C2: Composer authoring PreviewOnly accepted with version encoding repair.
- Phase64D1A: Companion Sleeve access foundation accepted, PreviewOnly, with server authorization and range validation.
- Phase64D1B: Companion inventories normalized and client marker accepted with no autonomous item use.
- Deferred D1A authorized non-GM range matrix: closed.
- Stock ClassicUO companion marker visibility: deferred to Phase64D1C.

## Current Active Task

`Phase64D1C - ClassicUO Companion Paperdoll Sleeve Access`

Goal: add a second paperdoll scroll to marker-positive AIGM companion paperdolls in the pinned ClassicUO source, route it through the ordinary `[umgsleeve 0xXXXXXXXX` speech command, and preserve server-side identity, authorization, range, and map checks.

## Queued Tasks

- `Phase64D1D - Full Skills-Gump Sleeve Organizer`
- `Phase64D1E - Selective Sleeve Descent Preview Runtime`
- movement and waypoint observability after cognition interface work

## Current Green Lights

- UMG versions are immutable and rollback-capable.
- Composer output remains PreviewOnly.
- Sleeve access is server-authoritative.
- Companion inventory normalization is accepted.
- Backpack marker contract is accepted for client discovery.
- Registered live companion roster is normalized: 22 of 22.
- Tactical dispatch remains disabled.
- Autonomous inventory use remains unimplemented.

## Current Boundaries

- No custom network packets.
- No client-side authorization shortcuts.
- No server inventory migration for D1C.
- No tactical dispatch.
- No autonomous item use.
- No protected server or packet/profile file changes.
- No public upload of private audit ZIPs, saves, accounts, logs, runtime sidecars, or profiles.

## Immediate Next Transition

Move from server-only accepted Sleeve access to a reversible, isolated custom-client lane. Phase64D1C is accepted only after the marker-positive paperdoll launcher is built, tested, and proven without weakening server authorization.

## Current Project Rule

Client affordances may discover server-authorized systems, but ServUO remains the identity and authorization authority.
