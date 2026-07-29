# Phase64D1D Operational Layout Model

Phase64D1D adds a dedicated Operational Layout subsystem beside the Phase64C2 Composer. Composer records stay Schema V2. Layout records use Operational Layout Schema Version 1.

Persistence design:
- Dedicated sidecars were selected instead of extending existing Composer version records.
- This preserves Phase64C2 rollback history and avoids Schema V3 churn.
- Existing canonical definitions, assignments, and version snapshots remain immutable and readable.

Operational hierarchy:
- Family
- Operational NeoStack
- NeoBlock Reference

Identity:
- Composer import still uses canonical actor IDs such as `dardalion`.
- Layout persistence uses serial-specific operational keys such as `dardalion.serial.00000193`.
- Duplicate-name actors therefore cannot overwrite or inherit another instance's saved layout.

Versioning:
- Save Draft clones the working layout into a new immutable Draft version.
- Approve Preview clones into a new Approved PreviewOnly version and does not alter Draft history.
- Rollback clones a historical version into a new Draft version.
- Historical versions are never mutated or reused.

Runtime boundary:
- Layout organization is configuration only.
- Runtime activation state is separate.
- Preview compiles organization eligibility and returns `PREVIEW_ONLY_NOT_DISPATCHED`.
- No gameplay adapter is invoked by organizer operations.
