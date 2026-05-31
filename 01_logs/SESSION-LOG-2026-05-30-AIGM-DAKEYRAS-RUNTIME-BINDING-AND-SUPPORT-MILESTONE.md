# SESSION LOG — 2026-05-30 — AIGM Dakeyras Runtime Binding and Support Milestone

## Summary

This session produced a meaningful AIGM companion milestone for Dakeyras on the NeoUO-Dev lane.

The most important breakthrough was not originally the support command parser itself. The real blocker was proving and fixing the live runtime/deploy path for `AIGMCompanionDakeyras` so the shard would actually execute the edited speech code.

Once runtime binding was proven and the correct `Scripts.dll` deployment path was used, Dakeyras support commands began executing locally as intended.

## What was proven

### 1. The runtime mismatch was real
Earlier evidence showed old speech log labels still appearing at runtime even after source edits. This was not imagined. The shard was continuing to run an older effective script assembly path.

### 2. The correct local build output was not automatically becoming the live root script assembly
`dotnet build .\Scripts\Scripts.csproj -c Debug -p:x64` succeeded, but the root live assembly timestamp for:

- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts.dll`

remained stale.

The actual built output that reflected current edits was:

- `C:\UO\Server\Neo Ultima Online\NeoUO-Dev\Scripts\bin\Debug\Scripts.dll`

Copying that built DLL onto the root `Scripts.dll` was the breakthrough that made the patched Dakeyras runtime go live.

### 3. Runtime binding proof succeeded
A unique runtime stamp was added to `AIGMCompanionDakeyras`:

- `DAK_RUNTIME_BINDING_PROOF_20260531_V1`

This was exposed through trusted speech probes and runtime log labels so the live NPC could prove which code path was actually executing.

After correct DLL deployment, Dakeyras successfully entered the new speech path and produced the expected `DAK_*` logging.

## Companion support milestone achieved

### Confirmed direct local support behavior
The following support intent lanes were successfully wired into the local trusted companion action path rather than default async queue behavior:

- `bandage self`
- `bandage yourself`
- `heal yourself`
- `cure yourself`

The shard logs confirm that these commands are now:

1. parsed locally
2. approved by direct-action policy
3. executed locally through companion action/skill executors
4. no longer dependent on the old async companion paraphrase path for exact recognized phrases

### Terminology mapping established
Support terminology was aligned into clearer intent groups:

- bandage terms -> use bandages
- heal terms -> use heal spell path
- cure self -> use cure potion path
- cure me -> use cure spell path

This is still early implementation logic rather than final production spell/equipment realism, but it establishes the command surface correctly.

## Important findings from validation

### Local parser path now works
Logs showed direct local routing such as:

- `DAK_PARSE_RESULT parsed=True kind=bandage_self`
- `DAK_POLICY_RESULT ... decision=DirectExecute`
- `DAK_DIRECT_EXECUTE_RESULT ... executed=True`

### Local skill execution now works for at least one real support case
Execution logs confirmed actual bandage consumption and healing application for Dakeyras self-bandaging.

### Typo and paraphrase rescue still exists
Misspelled variants such as `heal yoruself` / `heal youyrself` did not parse locally, but the async reply extractor later inferred `heal_self` from the AI paraphrase and attempted direct execution on apply.

This means the system currently has two support lanes:

- clean direct local lane for recognized phrases
- async rescue lane for malformed input or paraphrase recovery

### Remaining polish bug
When async trusted-action extraction recognizes a support action but direct execution then fails locally (for example cooldown), the NPC may still speak the async paraphrase rather than the local failure reason.

That is now a clear cleanup target rather than an unknown system failure.

## Strategic significance

This is a genuine milestone because it resolves a class of false-negative debugging problems.

Before this work, it was impossible to trust many behavior conclusions because source edits were not reliably becoming live runtime behavior.

After this session:

- the deploy truth is understood
- Dakeyras runtime binding can be proven explicitly
- direct trusted support action execution is confirmed live
- future Dakeyras support work can proceed from real runtime evidence instead of guesswork

## Recommended next steps

1. Normalize the local deployment workflow so the correct built `Scripts.dll` always becomes the live root assembly.
2. Harden the support parser for common misspellings / fuzzy variants.
3. Ensure trusted support intents never fall back to async queue when they should resolve locally.
4. When async rescue extraction does occur, prefer local failure reasons over AI paraphrase text if execution fails.
5. Extend the support spell lane with more faithful magery implementation, reagent/spellbook checks, and later greater-heal support.

## Milestone statement

Neo UO now has a proven live Dakeyras trusted-support command lane with runtime-binding proof and at least one confirmed real self-bandage execution path working on the live dev shard.
