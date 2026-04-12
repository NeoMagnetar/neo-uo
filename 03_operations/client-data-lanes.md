# Client Data Lanes

## Purpose
Prevent map editing and experimental client-side asset changes from contaminating the shared runtime asset surface.

## Current lanes
- `C:\UO\Client\UOFiles` = current working runtime asset set
- `C:\UO\Client\UOFiles-Editor` = editor-only client data lane for map tools
- `C:\UO\Client\UOFiles-Test` = test validation lane before any later promotion

## Policy
- Do not point map editors at `C:\UO\Client\UOFiles` unless explicitly intended.
- Prefer `UOFiles-Editor` for map editing tools.
- Prefer `UOFiles-Test` for validation of edited output.
- Treat baseline/source server data as read-only by policy.
- Do not edit `C:\UO\Server\ServUO` directly for map experimentation.

## Operational note
The current server-side environment split is already:
- Main / baseline reference
- Dev
- Staging
- preserved original

This client-lane split mirrors that discipline on the asset side.
