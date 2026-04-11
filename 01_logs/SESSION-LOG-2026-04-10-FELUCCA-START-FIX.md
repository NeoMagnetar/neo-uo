# Session Log — Dev Felucca Start Fix

## Task
Fix failed Dev validation for Felucca-only new-character start.

## What failed first
A controlled Dev-only retest showed a fresh new character spawning at the intended Britain coordinates but still on the Trammel facet.

Observed result from manual validation:
- coordinates: `1602 1591 20`
- region: `Britain`
- facet: `Trammel`

## Investigation summary
The visible final placement block in `Scripts/Misc/CharacterCreation.cs` had already been changed to use the existing Felucca Britain siege start definition (`m_SiegeInfo`) and `Map.Felucca`.

Deeper tracing identified a built-in downstream correction path in `Scripts/Mobiles/PlayerMobile.cs` that only forces Trammel players to Felucca when `Siege.SiegeShard` is enabled.

The Dev environment still had:
- `Config/Siege.cfg`
- `IsSiege=false`

That meant the intended downstream Felucca enforcement path was not active.

## What was changed
Dev-only change:
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Config\Siege.cfg`
- changed `IsSiege=false` to `IsSiege=true`

## Validation result
After enabling Dev siege mode and restarting the Dev shard:
- Dev booted successfully on `127.0.0.1:2594`
- siege initialization confirmed in startup log
- fresh-character manual retest passed
- `[where` now resolves to Britain on Felucca for the new Dev character

## Result
The Dev-only Felucca-start issue is resolved for the current intended shard direction.

## Scope note
This work was limited to Dev and did not modify baseline/source or staging.
