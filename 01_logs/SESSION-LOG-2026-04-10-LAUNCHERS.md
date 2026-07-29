# Session Log — Local Launchers Setup

## What was created

- desktop shortcuts:
  - `NeoUO Main`
  - `NeoUO Dev`
  - `NeoUO Staging`
- per-environment launcher scripts stored in `neo-uo-code/tools`
- per-environment ClassicUO settings files:
  - `settings.main.json`
  - `settings.dev.json`
  - `settings.staging.json`

## Where the shortcuts were placed

- `<desktop>\NeoUO Main.lnk`
- `<desktop>\NeoUO Dev.lnk`
- `<desktop>\NeoUO Staging.lnk`

## How environment routing works

Each shortcut calls an environment-specific PowerShell launcher.
That launcher checks whether the matching local server port is already live.
If not, it opens the correct ServUO environment in a dedicated PowerShell window, waits for the port, then applies the matching ClassicUO settings file and launches the client.

## What was validated

- per-environment ClassicUO settings files were created
- original active client config was backed up first
- desktop shortcuts were created with the exact requested names
- launcher documentation was added to both HQ and code repos
- runtime validation should confirm Main=2593, Dev=2594, Staging=2595
