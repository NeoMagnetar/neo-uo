# AIGM Companion Stabilization — 2026-06-04

Summary of live implementation work completed against the active runtime lane (`C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts`).

## Outcome
Mission accomplished on the active companion stabilization pass:
- persistent companions no longer use inherited `BaseHire` payroll deletion
- tracked pursuit / reactive combat path was hardened
- owner speech fanout was restored so nearby owned companions can hear the owner in parallel
- owner-relayed speech no longer causes linked companions to blindly mirror-execute commands
- reactive self-support was widened so companions can retry healing while still significantly injured

## Authoritative implementation backup
The exact implementation mirror / backup repo is:
- `neo-uo-code`

That repository was synchronized from the live `NeoUO-Dev\Scripts` runtime tree so it can serve as:
- code database
- rollback reference
- implementation backup of record
- future comparison point against live shard behavior

## Important repo split
- `neo-uo` = HQ / design / planning / operations context
- `neo-uo-code` = implementation and code backup surface

## Notes
This log is intentionally concise. Exact code lives in the code repo.
