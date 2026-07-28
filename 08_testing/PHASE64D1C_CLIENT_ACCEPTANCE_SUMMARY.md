# Phase64D1C Client Acceptance Summary

## Build

- Pinned ClassicUO commit: `a7cf920e42436ce62b9f26b846da8665c9fd3364`.
- NativeAOT client publish: 0 errors.
- Combined build: 0 errors.
- Warning comparison: no new warning codes or messages caused by NeoUO changes.
- `cuo.dll`: `722D511EC94B6C6C10989454BEE3659E7E61075E27CB5C7B589E05100DED09FD`.
- `cuo.pdb`: `9F759AAA665A5807ED9146D1A1FA55848C5AB6D594363B8A607CEBB8AD833BE1`.

## Isolated Lane

- A separate `ClassicUO-Phase64D1C-Test` directory was created.
- Copied original `cuo.dll` and `cuo.pdb` were preserved in that lane.
- Test profile/data paths were isolated before launch.
- The normal client folder was left untouched until isolated proof passed.

## Visual Proof

- Player paperdoll stayed unchanged and did not show a UMG scroll.
- Ordinary NPC paperdolls did not receive marker-based access broadly.
- Marker-positive companions displayed the profile scroll and exactly one UMG Sleeve scroll.
- Tooltip text read `UMG Sleeve`.
- No duplicate scrolls were observed.
- No paperdoll corruption, continuous rebuild, or client crash was observed.

## Command Proof

- Hewla paperdoll scroll sent `umgsleeve 0x00004DD9`.
- The server opened Hewla's Sleeve Selector with `source:"Command"`.
- Druss `0x00000304`, Dardalion `0x00000193`, Miriel `0x00002AA5`, and Durmast `0x00003575` remained reachable through the accepted command path.

## Dynamic Refresh

- Hewla backpack `0x4002360F` was temporarily set to hue `0` while the paperdoll was open.
- The UMG scroll disappeared.
- The hue was restored to `1175`.
- Exactly one UMG scroll returned.
- The backpack was not removed or replaced.

## Live Deployment

- The live client was backed up.
- Only `cuo.dll` and `cuo.pdb` were replaced.
- `ClassicUO.exe` was not replaced.
- Normal local launcher connected after deployment.
- Rollback procedure was preserved.

## Regression

- Direct Sleeve command access still worked.
- Context-menu access still worked.
- Backpack button still worked.
- Preview remained dry-run/no-dispatch.
- Tactical adapter did not execute.
- Autonomous inventory use did not occur.
- Dialogue and movement behavior remained operational.
