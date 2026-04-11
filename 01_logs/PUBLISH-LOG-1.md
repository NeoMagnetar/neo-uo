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
