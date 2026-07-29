# Phase64D1F Preparation Packet

## Next Task

Movement and Waypoint Observability.

## Starting Point

D1E can propose movement-related typed intents such as `RepositionPreview` and `HoldPositionPreview`, but cannot dispatch movement. Future movement work must begin by observing movement ownership, lease state, waypoint inputs, route validity, and cancellation/hold governance.

## Proof Expectations

- Compare movement owner, operational mode, current mission, target, location, warmode, Combatant, FocusMob, and inventory before and after observation commands.
- Keep movement execution disabled unless a later phase explicitly authorizes it.
- Reuse existing movement ownership and operational control services.
- Preserve the D1E receipt boundary while adding movement observability receipts.

