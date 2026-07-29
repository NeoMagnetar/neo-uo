# Phase64D1E Runtime Activation Graph

Phase64D1E derives a non-persistent Runtime Activation Graph from the actor's approved PreviewOnly Operational Layout.

## Model

The graph is built from:

- family roots
- Operational NeoStacks
- NeoBlock references
- canonical definitions
- typed trigger profiles
- capability gates
- governance gates
- typed intent proposals
- adapter mapping nodes

The graph is acyclic and cached only by actor serial, approved layout version, and graph fingerprint. A layout version change invalidates the cache.

## Selection

Selection is deterministic:

1. hard governance restrictions
2. explicit stop, hold, stand-down, or cancellation
3. owner or commander authority
4. structural validity
5. enabled configuration state
6. capability validity
7. trigger match and severity
8. stable selected branch and hysteresis
9. configured branch priority
10. configured stack order
11. stable stack ID tie-break
12. stable definition ID tie-break

Combat, Positioning, Resources, and Protection may each select independently, but no family may select more than one leading branch. Losing eligible siblings are marked `SuspendedBySelector`.

## Boundaries

The runtime compiles a typed preview intent and maps it to a future deterministic adapter name, but the no-dispatch boundary returns `PREVIEW_ONLY_NOT_DISPATCHED` before any gameplay adapter can be invoked.

Receipts contain structured evidence and decision factors, not hidden reasoning.

