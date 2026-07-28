# Phase64D1C Paperdoll Launcher UMG Context

## Accepted State

The UMG Sleeve system now has a ClassicUO paperdoll entry point for marker-positive AIGM companions.

The paperdoll scroll is not an authority mechanism. It is a discovery affordance that reaches the existing server-authoritative Sleeve access service.

## Route

```text
ClassicUO paperdoll marker -> UMG Sleeve scroll -> GameActions.Say("[umgsleeve 0xXXXXXXXX") -> ServUO access validation -> Sleeve Selector
```

## Invariants

- Marker tuple remains `Layer.Backpack`, item id `0x0E75`, hue `1175`, version `1`.
- Server class remains `AIGMCompanionBackpack`.
- PreviewOnly remains dry-run/no-dispatch.
- Tactical dispatch remains disabled.
- Autonomous inventory use remains unimplemented.
- Client marker visibility does not grant authorization.

## Future Model

Phase64D1D should improve organization and usability of Sleeve inspection.

Phase64D1E may introduce Selective Sleeve Descent as Preview work, but it must still preserve server authority and must not turn paperdoll visibility into permission.
