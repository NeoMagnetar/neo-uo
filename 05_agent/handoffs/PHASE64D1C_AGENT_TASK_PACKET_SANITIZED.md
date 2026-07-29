# Phase64D1C Agent Task Packet - Sanitized

## Mission

Implement ClassicUO companion paperdoll Sleeve access for marker-positive AIGM companions, prove the isolated client lane, deploy reversibly only after proof, and update the existing GitHub publication PRs without merging them.

## Baseline

- Accepted server DLL SHA-256: `4AC823D6532C723FC4ADD0A128E2FBE35A1A4C8F3E09DE0101832090AA7F3FF0`
- Accepted UMG version SHA-256: `0EB27E13320CDC327597662334D8220F87DD47C94F5011DB2867E93A8D1D6C2F`
- UMG version records: 10 total, 8 Druss, 1 Dardalion, 1 Miriel
- Accepted companion inventory: 22 registered live AIGM companions, 22 normalized AIGM backpacks
- Tactical dispatch: disabled
- Autonomous item use: not implemented

## Pinned ClassicUO Source

- Source path: `C:\UO\Client\ClassicUO-Source-a7cf920e`
- Commit: `a7cf920e42436ce62b9f26b846da8665c9fd3364`

## Marker Contract

- Layer: `Layer.Backpack`
- ItemID: `0x0E75`
- Hue: `1175`
- MarkerVersion: `1`
- Server class: `AIGMCompanionBackpack`

## Work Boundaries

Do not modify packet handlers, profile storage, server PlayerMobile/Profile files, AIGM memory loader, or AIGM turn coordinator. Do not add custom packets, autonomous inventory use, tactical dispatch, server inventory migration, or upstream ClassicUO changes.

## Publication Controls

Use the existing GitHub publication branches and PRs. Do not force-push. Do not merge. Do not upload private runtime artifacts, saves, accounts, logs, audit ZIP contents, profiles, credentials, DLLs, EXEs, PDBs, or screenshots containing private account information.

## Acceptance Target

Use the final verdict only after all proof passes:

`PHASE64D1C_CLASSICUO_COMPANION_PAPERDOLL_SLEEVE_ACCESS_ACCEPTED_SERVER_AUTHORIZED`

If deployment remains intentionally isolated test-client only:

`PHASE64D1C_CLASSICUO_COMPANION_PAPERDOLL_SLEEVE_ACCESS_ACCEPTED_TEST_CLIENT_ONLY`
