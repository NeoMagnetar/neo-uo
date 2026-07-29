# Phase64D1B AIGM Companion UMG Architecture

## Composer Boundary

The Composer produces UMG Sleeve versions in PreviewOnly mode. Accepted Phase64C2 behavior keeps authoring separate from tactical execution:

- Composer output creates immutable version records.
- Rollback selects prior immutable versions.
- Preview execution is dry-run.
- No tactical adapter executes from Preview.
- No assignment or dispatch side effect is created by previewing.

## Sleeve Access Boundary

Phase64D1A establishes server-side access to companion Sleeves through command, context menu, and Sleeve Selector Gump surfaces.

ServUO remains responsible for:

- resolving the target serial
- confirming the target is a registered AIGM companion
- checking caller authorization
- checking range and map constraints
- deciding whether a Gump may open

Client controls may request access, but they do not grant it.

## Companion Inventory Authority

Phase64D1B normalizes the live companion inventory state:

- 22 registered live AIGM companions
- 22 normalized AIGM backpacks
- exactly one backpack per registered live companion

The backpack exists as ordinary server inventory state. It is not an autonomous behavior layer and does not permit item use by companions.

## Marker Contract

The accepted marker is:

- Layer: `Layer.Backpack`
- ItemID: `0x0E75`
- Hue: `1175`
- MarkerVersion: `1`
- Server class: `AIGMCompanionBackpack`

The marker is a client discovery hint only. It must not be treated as identity or authorization.

## Client Discovery Versus Server Authorization

Phase64D1C may display a ClassicUO paperdoll launcher when a non-player mobile visibly carries the accepted marker backpack. The launcher must route through the ordinary speech command:

`[umgsleeve 0xXXXXXXXX`

Server-side access validation remains mandatory. A visible marker cannot bypass registration, authorization, range, or map checks.

## Planned Selective Sleeve Descent

Selective Sleeve Descent remains a future Preview runtime model queued after D1C and D1D. It is not part of D1B and must not be implemented as part of the D1C paperdoll launcher.
