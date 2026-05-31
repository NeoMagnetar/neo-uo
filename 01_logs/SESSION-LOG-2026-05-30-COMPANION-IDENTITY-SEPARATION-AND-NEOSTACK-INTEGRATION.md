# SESSION LOG — 2026-05-30 — Companion Identity Separation and NeoStack Integration

## Summary

This session completed the critical identity-separation pass for the two Neo UO AI companions:

- Dakeyras
- Danyal

The system now supports them as distinct conversational entities rather than one shared companion identity leaking across multiple bodies.

This session also upgraded both companions with much richer personality grounding based on Waylander-era lore using companion-specific NeoStack profile material.

## Major breakthrough

### Companion identity separation now works
The long-running issue was that Danyal could spawn and speak, but she still sometimes identified herself as Dakeyras.

The eventual root cause was not in ServUO runtime identity alone. It was a layered middleware/session issue:

1. the shard was correctly sending companion identity fields
2. the middleware initially received those fields
3. but the middleware prompt path was still too counselor-generic
4. then it was discovered that `normalizeRequest(...)` was dropping companion identity fields before prompt/session logic saw them
5. it was also discovered that companion chat was sharing one OpenClaw conversation session id (`aigm-counselor`), causing cross-companion identity contamination

Once those layers were fixed, Dakeyras and Danyal began correctly answering as themselves.

## What was fixed

### 1. Middleware prompt identity contract
The middleware prompt builder was updated so `companion_speech` requests explicitly state:

- who the companion is
- that identity is fixed
- that the companion is not the counselor
- that the companion must not identify as another companion
- that companion memory/profile should be treated as authoritative

### 2. Companion-specific session separation
The middleware no longer routes all companion requests through one shared OpenClaw chat session.

Instead, companion-speech requests now derive a companion-specific session id from the companion identity fields. This prevents Dakeyras and Danyal from sharing one long-lived conversational self-model.

### 3. Request normalization bug fixed
A subtle but critical bug was found in `aigm-middleware-service.js`: the raw request body contained companion identity fields, but `normalizeRequest(...)` discarded them before later prompt/session logic used them.

This was the hidden reason the earlier identity-separation fixes appeared not to work.

### 4. Shard-side identity symmetry
Both companions were aligned so that:

- `runtime stamp` -> returns debug proof string
- `version` -> returns debug proof string
- `who are you` -> falls through to normal natural-language self-identification

This removed old debug-path asymmetry between Dakeyras and Danyal.

## Result

### Confirmed live outcome
After middleware and shard cleanup:

- Dakeyras answers as Dakeyras
- Danyal answers as Danyal
- both retain separate runtime stamp proof behavior
- Danyal no longer collapses into Dakeyras identity

This is the first clean proof that multiple companions can exist as distinct AI conversational entities on the shard.

## NeoStack integration

The session also converted expanded Waylander-inspired UMG / NeoStack material into real companion identity files.

### Updated long-form memory profiles
- `memory/dakeyras-profile.md`
- `memory/danyal-profile.md`

These now include:

- stronger core arc summaries
- trigger / directive / instruction structure
- conversational style
- relationship stance
- memory salience rules
- canonical anchors
- anti-identity-bleed guardrails

### Added compact operational identity summaries
- `memory/dakeyras-ops.md`
- `memory/danyal-ops.md`

These tighter files are designed as machine-usable operational identity anchors for future middleware or agent prompt usage.

## Why this matters

This session moved the companion project from:

- one successful primary companion with clone drift problems

to:

- two separate companion entities with distinct selfhood and reusable shared mechanics

That unlocks the next real design horizon:

- multi-companion command routing
- shared perception without shared identity collapse
- differentiated tactical behavior
- deeper autonomous personality expression
- tracking/navigation/memory systems that can be interpreted differently by Dakeyras and Danyal

## Recommended next steps

1. Improve multi-companion speech routing so nearest or explicitly addressed companion responds predictably.
2. Decide how much companions should passively hear each other versus only share structured perception.
3. Begin the tracking + coordinate-awareness design pass as the next mechanical cognition layer.
4. Update middleware to optionally prefer compact ops identity files for routine turns and longer soul/profile files when deeper grounding is needed.

## Milestone statement

Neo UO now has two separate AI companions — Dakeyras and Danyal — who correctly self-identify as distinct entities, use separate personality/memory grounding, and can serve as the foundation for richer world-aware autonomy.
