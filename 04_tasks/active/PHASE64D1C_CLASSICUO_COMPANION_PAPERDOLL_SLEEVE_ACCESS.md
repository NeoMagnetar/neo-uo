# Phase64D1C - ClassicUO Companion Paperdoll Sleeve Access

## Status

Complete.

## Objective

Add a second UMG Sleeve scroll to marker-positive AIGM companion paperdolls in the pinned ClassicUO source, then build, test, and deploy through a reversible isolated-client lane.

## Accepted Baseline

- Server DLL SHA-256: `4AC823D6532C723FC4ADD0A128E2FBE35A1A4C8F3E09DE0101832090AA7F3FF0`
- UMG version baseline SHA-256: `0EB27E13320CDC327597662334D8220F87DD47C94F5011DB2867E93A8D1D6C2F`
- Companion roster: 22 registered live AIGM companions
- Inventory state: 22 normalized AIGM backpacks, exactly one per registered live companion
- Tactical dispatch: disabled
- Autonomous item use: not implemented

## Pinned Client Source

- Path: `C:\UO\Client\ClassicUO-Source-a7cf920e`
- Commit: `a7cf920e42436ce62b9f26b846da8665c9fd3364`

## Marker Contract

- Layer: `Layer.Backpack`
- ItemID: `0x0E75`
- Hue: `1175`
- MarkerVersion: `1`
- Server class: `AIGMCompanionBackpack`

MarkerVersion is server metadata. The ClassicUO launcher does not need to read it.

## Required Client Behavior

- Displayed no UMG scroll on the player paperdoll.
- Preserved the player profile and party-manifest scrolls.
- Preserved the existing non-player profile scroll.
- Added a second scroll beside it for marker-positive AIGM companion candidates.
- Revalidated the marker before double-click.
- Used the ordinary `[umgsleeve 0xXXXXXXXX` speech command path.
- Removed the scroll if the marker disappeared.
- Avoided duplicate controls and paperdoll rebuild flicker.

## Acceptance

Verdict:

`PHASE64D1C_CLASSICUO_COMPANION_PAPERDOLL_SLEEVE_ACCESS_ACCEPTED_SERVER_AUTHORIZED`

Final client hashes:

- `cuo.dll`: `722D511EC94B6C6C10989454BEE3659E7E61075E27CB5C7B589E05100DED09FD`
- `cuo.pdb`: `9F759AAA665A5807ED9146D1A1FA55848C5AB6D594363B8A607CEBB8AD833BE1`

The live client was deployed by replacing only `cuo.dll` and `cuo.pdb`; `ClassicUO.exe` was not replaced.

## Server Authority Rule

The client marker is discovery only. ServUO still decides registration, authorization, range, map, and Gump access.

## Explicit Non-Goals

- no custom packets
- no packet-handler changes
- no profile-storage changes
- no Selective Sleeve Descent
- no drag-and-drop Sleeve organizer
- no waypoint tools
- no movement overlays
- no autonomous inventory use
- no tactical dispatch
- no upstream ClassicUO push

## Next Queue

- `Phase64D1D - Full Skills-Gump Sleeve Organizer`
- `Phase64D1E - Selective Sleeve Descent Preview Runtime`
