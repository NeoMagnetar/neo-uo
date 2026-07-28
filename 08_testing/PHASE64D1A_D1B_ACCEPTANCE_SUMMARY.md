# Phase64D1A and D1B Acceptance Summary

## Scope

Sanitized acceptance summary for the server-side companion Sleeve access and inventory marker baseline.

## Phase64D1A

Verdict:

`PHASE64D1A_COMPANION_SLEEVE_ACCESS_FOUNDATION_ACCEPTED_PREVIEW_ONLY_WITH_AUTHORIZED_NONGM_RANGE_PROOF_DEFERRED`

Deferred closure:

`DEFERRED.D1A.AUTHORIZED_NONGM_RANGE_MATRIX_CLOSED`

Accepted proof summary:

- Direct Sleeve command route worked.
- Context-menu route worked.
- Sleeve Selector Gump route worked.
- Unauthorized access was denied server-side.
- Range and map checks remained server-side.
- PreviewOnly execution remained dry-run and no-dispatch.

Audit ZIP reference:

- `PHASE64D1A_COMPANION_SLEEVE_ACCESS_FOUNDATION_20260727-1351.zip`
- SHA-256: `7D647A76BF995E23558480E283723D17388E4504465CFA5D90C17A2FC24A3074`

## Phase64D1B

Verdict:

`PHASE64D1B_COMPANION_INVENTORY_NORMALIZED_AND_CLIENT_MARKER_ACCEPTED_NO_AUTONOMOUS_ITEM_USE`

Accepted proof summary:

- 22 registered live AIGM companions.
- 22 normalized AIGM backpacks.
- Exactly one backpack per registered live companion.
- Marker values matched the accepted contract.
- Tactical dispatch remained disabled.
- Autonomous item use was not implemented.
- Stock ClassicUO marker visibility was deferred to Phase64D1C.

Audit ZIP reference:

- `AIGM_AUDIT_PHASE64D1B_R1_EXISTING_BACKPACK_ADOPTION_20260728-0940.zip`
- SHA-256: `51DE6E9695074A0CD436CDCBB5EC9CC27FED619E9F8FF5F6ED7E0A6990FDA696`

## Marker Contract

- Layer: `Layer.Backpack`
- ItemID: `0x0E75`
- Hue: `1175`
- MarkerVersion: `1`
- Server class: `AIGMCompanionBackpack`

The marker is a client discovery hint only. ServUO remains the identity and authorization authority.
