# AIGM Counselor Capability Architecture
_Date: 2026-05-29_

## Core finding

The AI GM counselor should not be treated as a single-class problem.

Native ServUO / NeoUO mechanic surfaces split responsibilities across incompatible class models:
- `PlayerVendor` is stronger for visible embodiment, paperdoll, backpack, clothing, and owner-style inventory interaction.
- `BaseCreature` is stronger for current follow/pathing/movement behavior through existing control-order semantics.

## Consequence

Trying to force one inheritance base to satisfy all counselor responsibilities creates architectural drag and unstable compromises.

## Recommended direction

Move toward a capability-oriented actor model.

### Suggested capability split
- `ConversationCapability`
- `InventoryCapability`
- `SpawnCapability`
- `InspectionCapability`
- `MovementCapability`
- `TargetingCapability`
- visible counselor shell / embodiment

## Design implication

The visible counselor should become the stable AI-facing shell, while individual GM or movement abilities should be implemented through whichever native game mechanic is best suited for that capability.

This keeps the long-term direction aligned with native shard systems instead of building a fake parallel GM engine.

## Immediate engineering implications

- preserve `AIGMActionProposal` as the canonical live execution contract
- keep capability adapters explicit
- avoid re-entangling movement assumptions directly into every counselor path
- treat inventory/paperdoll UX and movement as separable concerns
