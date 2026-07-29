# Phase64D1C Accepted Client Paperdoll Access

## Verdict

`PHASE64D1C_CLASSICUO_COMPANION_PAPERDOLL_SLEEVE_ACCESS_ACCEPTED_SERVER_AUTHORIZED`

## Milestone

Phase64D1C added a ClassicUO paperdoll Sleeve launcher for marker-positive AIGM companions.

The implementation preserved the existing profile scroll, added one `UMG Sleeve` scroll beside it for marked non-player paperdolls, and routed double-clicks through the ordinary `[umgsleeve 0xXXXXXXXX` command path.

## Source And Publication

- Pinned ClassicUO commit: `a7cf920e42436ce62b9f26b846da8665c9fd3364`
- Modified client source: `src/ClassicUO.Client/Game/UI/Gumps/PaperdollGump.cs`
- Implementation publication commit: `142742bc04ee272c922fc16d15d1d1e1618767f4`
- Client patch path in implementation repo: `client/classicuo/patches/phase64d1c-aigm-paperdoll-sleeve.patch`

## Hashes

- Server `Scripts.dll`: `4AC823D6532C723FC4ADD0A128E2FBE35A1A4C8F3E09DE0101832090AA7F3FF0`
- UMG `versions_v2.json`: `0EB27E13320CDC327597662334D8220F87DD47C94F5011DB2867E93A8D1D6C2F`
- D1C `cuo.dll`: `722D511EC94B6C6C10989454BEE3659E7E61075E27CB5C7B589E05100DED09FD`
- D1C `cuo.pdb`: `9F759AAA665A5807ED9146D1A1FA55848C5AB6D594363B8A607CEBB8AD833BE1`

## Runtime Proof

- Player paperdoll remained unchanged.
- Ordinary NPC paperdolls did not receive a broad UMG scroll.
- Marker-positive companions showed profile scroll plus exactly one UMG Sleeve scroll.
- Tooltip read `UMG Sleeve`.
- Scroll activation opened the server-authorized Sleeve Selector.
- Hewla paperdoll scroll produced command serial `0x00004DD9`.
- Primary command proof covered Druss `0x00000304`, Dardalion `0x00000193`, Miriel `0x00002AA5`, and Durmast `0x00003575`.
- Dynamic marker refresh removed the scroll when Hewla's marker hue was temporarily invalidated and restored exactly one scroll after hue `1175` was restored.

## Boundaries

- No custom packet.
- No packet-handler change.
- No profile-storage change.
- No tactical dispatch.
- No autonomous inventory use.
- No upstream ClassicUO push.
- No public upload of private audit ZIPs, saves, accounts, runtime sidecars, profiles, screenshots, or logs.

## Next

`Phase64D1D - Full Skills-Gump Sleeve Organizer`
