# Project UMG Context

## Purpose

Record how UMG structured cognition, Sleeves, and companion-facing authoring tools are being applied to Neo UO.

## Accepted State

UMG is now part of the active AIGM companion implementation lane.

- Composer authoring is available as PreviewOnly.
- Version records are immutable and rollback-capable.
- The accepted version baseline is `versions_v2.json`.
- The accepted version baseline SHA-256 is `0EB27E13320CDC327597662334D8220F87DD47C94F5011DB2867E93A8D1D6C2F`.
- The accepted record count is 10 total: 8 Druss, 1 Dardalion, and 1 Miriel.
- Druss remains Approved PreviewOnly.
- Preview execution remains dry-run and no-dispatch.

## Companion Access Model

Sleeve access is server authoritative. The current accepted access paths are:

- direct command access
- context-menu access
- server Gump access

Phase64D1C adds a ClassicUO paperdoll launcher for marker-positive companions. The launcher is only a client discovery affordance and must call the ordinary speech command path. It does not authorize access.

## Backpack Marker Contract

- Layer: `Layer.Backpack`
- ItemID: `0x0E75`
- Hue: `1175`
- MarkerVersion: `1`
- Server class: `AIGMCompanionBackpack`

The marker is a client discovery hint only. ServUO remains the identity and authorization authority.

## Future Selective Descent

Selective Sleeve Descent remains planned for Phase64D1E Preview work. It is not implemented in the accepted D1B baseline and is not part of D1C.

## Rule

UMG context should support the project's clarity and companion cognition interface without replacing Neo UO's actual game design content or weakening server authority.
