# AIGM Current Status — 2026-05-29

## Current state

AIGM counselor work is now in a partially proven native-execution stage.

### Proven live
- counselor chat path works
- fresh counselors show improved paperdoll / backpack / clothing behavior
- live question/response/confirm/history gump path is active
- counselor-driven world-item mutation has been proven with visible item spawns
- constructables discovery dump is producing a useful shard-local capability inventory

### Not yet complete
- quantity correctness for stackable add requests
- generalized native Add-backed item resolution over the full constructable item surface
- container-targeted add lanes
- mobile/world spawn lanes for generalized constructable mobiles
- props read/write capability
- command registry discovery completion

## Immediate priority ladder
1. Generalize native Add-backed item creation
2. Fix command registry discovery
3. Add native Add-to-container support
4. Add native mobile/world spawn support
5. Add props-read capability

## Repo alignment note

HQ notes belong in `neo-uo`.
Intentional implementation surfaces and technical notes belong in `neo-uo-code`.
Runtime clutter and machine-local drift remain excluded.
