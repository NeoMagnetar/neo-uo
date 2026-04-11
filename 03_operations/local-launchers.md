# Local Launchers

These desktop shortcuts are the normal one-click way to open the local NeoUO environments.

## Desktop shortcuts

- `NeoUO Main`
- `NeoUO Dev`
- `NeoUO Staging`

## What each launcher does

Each launcher:
1. checks whether the matching server is already listening on its assigned local port
2. if not, opens a clearly titled PowerShell server window and starts the correct ServUO environment
3. waits for the target port to come up
4. swaps the ClassicUO active settings file to the matching environment routing
5. launches the local ClassicUO client

## Environment mapping

### NeoUO Main
- server path: `C:\UO\Server\ServUO`
- host: `127.0.0.1`
- port: `2593`
- server window title: `NeoUO Main Server`

### NeoUO Dev
- server path: `C:\UO\Server\Neo Ultima Online\NeoUO-Dev`
- host: `127.0.0.1`
- port: `2594`
- server window title: `NeoUO Dev Server`

### NeoUO Staging
- server path: `C:\UO\Server\Neo Ultima Online\NeoUO-Staging`
- host: `127.0.0.1`
- port: `2595`
- server window title: `NeoUO Staging Server`

## Operator guidance

- click `NeoUO Main` for the baseline/source environment
- click `NeoUO Dev` for development testing
- click `NeoUO Staging` for clean validation work
- no manual port editing should be needed for normal local startup

## Client routing method

ClassicUO uses environment-specific settings files:
- `settings.main.json`
- `settings.dev.json`
- `settings.staging.json`

The launcher copies the correct environment file over the active `settings.json` immediately before launching the client.

## Safety note

The original working ClassicUO settings were backed up before this launcher system was created.
