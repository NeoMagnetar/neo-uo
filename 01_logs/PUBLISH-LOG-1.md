# Neo UO — Publish Log 1

> Restored after HQ scaffold conversion. This log preserves the initial setup and environment-hardening history established before structured feature work begins.

---

## Entry 001 — Local ServUO Project Bootstrap
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Create the initial isolated local development environment for a Windows ServUO + ClassicUO shard.

**Summary**  
Set up a clean local project structure for server and client work, separate from Outlands. Cloned the ServUO repository, created client workspace folders, and prepared the foundation for local development and playtesting.

**Files / Paths Created**  
- `C:\UO\Server\`
- `C:\UO\Client\`
- `C:\UO\Server\ServUO\`
- `C:\UO\Client\ClassicUO\`
- `C:\UO\Client\UOFiles\`

**Behavior Impact**  
- Established an isolated local project structure for development
- Kept live Outlands install separate from new server/client environment

**Restart Required:** No  
**Test Status:** Structural setup complete  
**Notes / Risks:** None

---

## Entry 002 — ServUO Build Path Validation
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Validate the actual ServUO build/runtime requirements from the cloned repository and compile the server.

**Summary**  
Inspected the cloned ServUO repository and confirmed the current project targets `net48`. Installed/used the available local toolchain and successfully built the server core and scripts assemblies.

**Files / Paths Changed**  
- `C:\UO\Server\ServUO\Server\Server.csproj` (inspected)
- `C:\UO\Server\ServUO\Scripts\Scripts.csproj` (inspected)
- `C:\UO\Server\ServUO\ServUO.exe` (built)
- `C:\UO\Server\ServUO\Scripts.dll` (built)

**Behavior Impact**  
- Confirmed viable local compile path for server development
- Resolved runtime script compiler dependency/path issue during setup

**Restart Required:** Yes  
**Test Status:** Build succeeded  
**Notes / Risks:** Initial startup required correct client data before runtime could complete

---

## Entry 003 — Isolated Runtime Configuration
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Configure ServUO for isolated local testing on loopback and separate runtime assets.

**Summary**  
Configured the local shard to listen only on localhost, raised local account capacity, and pointed ServUO to a dedicated copied client-data folder rather than any live install path.

**Files Changed**  
- `C:\UO\Server\ServUO\Config\Server.cfg`
- `C:\UO\Server\ServUO\Config\Accounts.cfg`
- `C:\UO\Server\ServUO\Config\DataPath.cfg`

**Behavior Impact**  
- Server binds to `127.0.0.1:2593`
- Accounts per IP set to `10`
- Runtime data path isolated to `C:\UO\Client\UOFiles`

**Restart Required:** Yes  
**Test Status:** Passed  
**Notes / Risks:** Outlands was not used as the live runtime path

---

## Entry 004 — ClassicUO Client Deployment
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Deploy a standalone ClassicUO client for the local shard.

**Summary**  
Downloaded and extracted ClassicUO into the isolated client workspace and created a desktop launcher shortcut for local use.

**Files / Paths Created**  
- `C:\UO\Client\ClassicUO\`
- `C:\UO\Client\Launch-ClassicUO-Local.ps1`
- `C:\Users\Magne\Desktop\Local UO Client.lnk`

**Behavior Impact**  
- Local client can be launched independently from Outlands
- Client launch flow prepared for connection to local shard

**Restart Required:** No  
**Test Status:** Client launch path established  
**Notes / Risks:** Client required local settings adjustment before valid connection flow

---

## Entry 005 — Official Client Data Integration
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Populate the isolated runtime data folder using the official Ultima Online Classic client data.

**Summary**  
After the official client patcher completed, copied the proper classic client asset set into `C:\UO\Client\UOFiles`, replacing the temporary donor set. This resolved the missing `tiledata.mul` startup blocker.

**Files / Paths Updated**  
- `C:\UO\Client\UOFiles\*`

**Behavior Impact**  
- ServUO now has the classic runtime data it expects
- Startup can proceed past previous asset-format failure

**Restart Required:** Yes  
**Test Status:** Verified presence of `tiledata.mul`, `staidx0.mul`, `statics0.mul`, `map0LegacyMUL.uop`, `artLegacyMUL.uop`  
**Notes / Risks:** Official client data is now the authoritative source for isolated runtime assets

---

## Entry 006 — ClassicUO Local Configuration Fix
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Correct local ClassicUO configuration so it uses the isolated data path and shard address.

**Summary**  
Updated ClassicUO settings to point to the isolated `UOFiles` directory and the local ServUO shard endpoint.

**Files Changed**  
- `C:\UO\Client\ClassicUO\settings.json`

**Behavior Impact**  
- Client now targets `127.0.0.1:2593`
- Client uses `C:\UO\Client\UOFiles` for runtime data
- Prevented fallback behavior that redirected to the website

**Restart Required:** No  
**Test Status:** Passed  
**Notes / Risks:** Username/password remain user-controlled

---

## Entry 007 — First Local Startup / Owner Account Stage
**Status:** In Progress  
**Date:** 2026-04-10

**Task**  
Bring the local shard fully online and complete first owner-account creation.

**Summary**  
ServUO now reaches the first-run owner account prompt successfully. The shard is functionally close to operational, with the remaining step being final completion of the first account flow inside the interactive server console.

**Behavior Impact**  
- Server successfully loads configs, scripts, regions, and world
- Startup reaches owner account creation prompt

**Restart Required:** Possibly  
**Test Status:** Partial success  
**Notes / Risks:** Interactive first-run prompt behavior has been inconsistent through remote console handling; if needed, complete account creation directly in the visible server console window

---

## Entry 008 — Environment Hardening and Rollback Preparation
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Prepare the ServUO workspace for safe development before gameplay changes.

**Summary**  
Preserved the current shard as a baseline source, created isolated Dev and Staging copies, generated a timestamped baseline snapshot, separated environment ports, initialized version control in Dev, wrote an operations note, and verified the backup by restoring it into a validation folder.

**Files / Paths Created or Changed**  
- `C:\UO\Server\Neo Ultima Online\Production-Preserved-Original\`
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\`
- `C:\UO\Server\Neo Ultima Online\NeoUO-Staging\`
- `C:\UO\Server\Neo Ultima Online\Backups\20260410-165602-baseline-pre-felucca-lockdown.zip`
- `C:\UO\Server\Neo Ultima Online\Ops\SETUP-NOTE.txt`
- `C:\UO\Server\Neo Ultima Online\Ops\ENVIRONMENT-OPS-NOTE.txt`
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Config\Server.cfg`
- `C:\UO\Server\Neo Ultima Online\NeoUO-Staging\Config\Server.cfg`

**Behavior Impact**  
- Original shard preserved as baseline source
- Dev and Staging now isolated as independent working copies
- Port conflicts resolved for concurrent launch scenarios
- Rollback path documented and restore-tested

**Restart Required:** No  
**Test Status:** Restore validation passed by extraction and structural verification  
**Notes / Risks:** No gameplay logic, maps, spawns, facets, or shard-rule code changed during this task

---

## Project Operating Rule
From this point forward, every completed task should be followed by a new publish-log entry documenting:
- task
- status
- summary
- files/paths changed
- behavior impact
- restart requirement
- test status
- notes/risks
- next recommended step

---

## Entry 009 � Dev Shard Felucca-Only Britain Start and Trammel Lockdown
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Convert the Dev shard to a practical Felucca-only player flow without unregistering Trammel from the engine.

**Summary**  
Created a pre-change Dev snapshot, forced all new characters in Dev to start in Britain / The Wayfarer's Inn / Felucca using the built-in siege start definition, restricted the public moongate system to Felucca-only routing, and patched the physically stuck flow so it no longer routes players into Trammel.

**Files Changed**  
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts\Misc\CharacterCreation.cs`
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts\Items\Functional\PublicMoongate.cs`
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts\Services\Help\StuckMenu.cs`

**Behavior Impact**  
- New Dev-shard characters now start at Britain / The Wayfarer's Inn / Felucca
- Default public moongate routing now exposes Felucca only in Dev
- Physically stuck no longer routes players into Trammel in Dev
- Trammel remains registered in code for stability but is removed from the default player flow patched in this task

**Restart Required:** Yes  
**Test Status:** Dev build succeeded and Dev shard booted cleanly on `127.0.0.1:2594`  
**Notes / Risks:** Narrow-scope patch only; larger travel surfaces such as custom portals, recall/gate systems, veteran reward portals, and other specialty transport surfaces were not broadly redesigned in this task  
**Next recommended step:** perform manual in-client verification of fresh character start, public moongate menu, and physically stuck menu on Dev, then decide whether the Dev shard is ready for staging review

---

## Entry 010 � Desktop Launchers for Main, Dev, and Staging
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Create one-click desktop launchers for Main, Dev, and Staging with automatic client routing.

**Summary**  
Backed up the existing ClassicUO active config, created separate environment-specific ClassicUO settings files, created three environment-aware launcher scripts, placed three desktop shortcuts with the exact requested names, and documented the launcher system in both HQ and code repositories.

**Files Changed or Created**  
- `C:\UO\Client\ConfigBackups\settings-20260410-181228-pre-launchers.json`
- `C:\UO\Client\ClassicUO\settings.main.json`
- `C:\UO\Client\ClassicUO\settings.dev.json`
- `C:\UO\Client\ClassicUO\settings.staging.json`
- `C:\Users\Magne\Desktop\NeoUO Main.lnk`
- `C:\Users\Magne\Desktop\NeoUO Dev.lnk`
- `C:\Users\Magne\Desktop\NeoUO Staging.lnk`
- `C:\Users\Magne\Desktop\neo uo\03_operations\local-launchers.md`
- `C:\Users\Magne\Desktop\neo uo\01_logs\SESSION-LOG-2026-04-10-LAUNCHERS.md`
- `C:\Users\Magne\Desktop\neo-uo-code\tools\NeoUO-Main-Launcher.ps1`
- `C:\Users\Magne\Desktop\neo-uo-code\tools\NeoUO-Dev-Launcher.ps1`
- `C:\Users\Magne\Desktop\neo-uo-code\tools\NeoUO-Staging-Launcher.ps1`
- `C:\Users\Magne\Desktop\neo-uo-code\docs\implementation-notes\local-desktop-launchers.md`

**Behavior Impact**  
- Operator now has one-click startup choices for Main, Dev, and Staging
- Manual port editing is no longer required for normal local environment switching
- Client routing now follows the selected environment launcher

**Restart Required:** No  
**Test Status:** Launcher artifacts created and documented; environment routing validated by configuration design and port mapping  
**Notes / Risks:** Launchers rewrite the active ClassicUO `settings.json` at launch time using backed-up, environment-specific copies; this is intentional and backed by a saved original config  
**Next recommended step:** perform a quick live click-test of each desktop launcher once to confirm Main=2593, Dev=2594, and Staging=2595 in actual operator use

---

## Entry 011 — Dev Felucca Start Fix via Siege Activation
**Status:** Complete  
**Date:** 2026-04-10

**Task**  
Fix the failed Dev validation where fresh characters were still spawning in Britain on the Trammel facet.

**Summary**  
A controlled Dev-only retest proved that the previous CharacterCreation patch corrected the start location but not the final facet. Deeper tracing found a built-in downstream map correction path in `PlayerMobile.cs` that only forces Trammel players to Felucca when `Siege.SiegeShard` is enabled. The Dev shard still had `IsSiege=false`, so the intended Felucca enforcement path never activated. Dev siege mode was enabled, the shard was restarted, and the fresh-character retest then passed.

**Files Changed**  
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Config\Siege.cfg`
- `C:\Users\Magne\Desktop\neo uo\01_logs\SESSION-LOG-2026-04-10-FELUCCA-START-FIX.md`
- `C:\Users\Magne\Desktop\neo uo\01_logs\PUBLISH-LOG-1.md`

**Behavior Impact**  
- Dev shard now runs with siege mode enabled
- Fresh Dev characters now start in Britain on Felucca as intended
- Prior ambiguity between correct coordinates and wrong facet was resolved through the proper built-in siege path

**Restart Required:** Yes — completed for Dev  
**Test Status:** Passed  
**Notes / Risks:** This was a Dev-only fix. Siege activation may have broader ruleset implications in Dev beyond start-facet behavior, but it aligns with the intended hardcore/Felucca direction for this environment.  
**Next recommended step:** continue Dev-only shard work with the assumption that Felucca-first behavior is now the active baseline for Dev

---

## Entry 012 � Dev NeoWall Painter Added and Validated
**Status:** Complete  
**Date:** 2026-04-11

**Task**  
Add a Dev-only GM wall painter so perimeter shapes can be sketched live in-world one tile at a time.

**Summary**  
Implemented `NeoWallStart`, `NeoWallStop`, and `NeoWallClear` in the Dev shard and rebuilt/restarted Dev successfully. The operator later confirmed that the wall painter works in live Dev use, providing a reliable manual perimeter-sketching tool for the League prototype zone.

**Files Changed**  
- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts\Custom\NeoWallPainter.cs`
- `C:\Users\Magne\Desktop\neo uo\01_logs\SESSION-LOG-2026-04-11-NEOWALL-PAINTER.md`
- `C:\Users\Magne\Desktop\neo uo\01_logs\PUBLISH-LOG-1.md`

**Behavior Impact**  
- Dev GM can now paint wall sections interactively while moving
- painted wall sections can be cleared and redrawn cleanly
- perimeter shaping no longer depends on blind pre-scripted coordinate guesses

**Restart Required:** Yes � already completed for Dev  
**Test Status:** Passed  
**Notes / Risks:** First version uses a single solid wall tile type; future refinement can add orientation or alternate tile sets if needed  
**Next recommended step:** use the wall painter to sketch the full intended south/east boundary, then capture anchor coordinates for any future scripted cleanup or conversion work
