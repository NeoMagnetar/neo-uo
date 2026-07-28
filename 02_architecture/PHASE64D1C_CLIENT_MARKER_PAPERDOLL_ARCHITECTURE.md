# Phase64D1C Client Marker Paperdoll Architecture

## Purpose

Phase64D1C gives ClassicUO a companion-facing Sleeve access affordance while keeping ServUO as the only authority.

## Data Flow

1. ServUO equips a registered AIGM companion with an `AIGMCompanionBackpack`.
2. The backpack occupies `Layer.Backpack`.
3. ClassicUO receives the normal equipment state.
4. `PaperdollGump` detects the marker tuple on non-player paperdolls.
5. ClassicUO adds one UMG Sleeve scroll beside the existing profile scroll.
6. On double-click, ClassicUO sends ordinary speech text: `[umgsleeve 0xXXXXXXXX`.
7. ServUO validates registration, authorization, range, map, and PreviewOnly boundaries.
8. ServUO opens or denies the Sleeve Selector.

## Marker Tuple

- Layer: `Layer.Backpack`
- ItemID/graphic: `0x0E75`
- Hue: `1175`
- MarkerVersion: `1`
- Server class: `AIGMCompanionBackpack`

The client does not read marker version. It only uses item graphic and normalized hue as a discovery hint.

## Client Responsibilities

- Detect marker-positive non-player paperdolls.
- Preserve the existing paperdoll layout.
- Add and remove the UMG scroll idempotently as equipment state changes.
- Revalidate marker presence before sending the command.
- Use only the normal speech-command path.

## Server Responsibilities

- Maintain companion identity.
- Maintain backpack marker correctness.
- Validate access.
- Enforce range and map.
- Enforce PreviewOnly/no-dispatch.
- Reject unauthorized users even if the client displays a marker-based control.

## Non-Protocol Boundary

D1C intentionally does not add a packet, opcode, profile field, sidecar, or client-local authorization cache.

This keeps the client overlay reversible and keeps the server as the source of truth.
