# Phase64D1D Implementation Handoff

Use the Phase64D1D organizer as the baseline for the next PreviewOnly runtime work.

Key implementation surfaces:
- `AIGMUMGOperationalLayoutModel`
- `AIGMUMGOperationalLayoutService`
- `AIGMUMGSleeveSelectorGump`
- `[umglayout]` diagnostics
- `[umglayoutproof]` controlled proof trigger

Important design constraints:
- Operational layout records reference canonical definitions; they do not copy or rewrite definitions.
- Layout actor keys are serial-specific.
- Draft and Approved PreviewOnly layout versions are immutable.
- Rollback creates a new Draft version from a clone.
- Preview must end with `PREVIEW_ONLY_NOT_DISPATCHED`.

D1E preparation:
- Use the approved PreviewOnly layout as input.
- Produce decision receipts suitable for operator inspection.
- Keep descent PreviewOnly and non-dispatching.
- Do not implement tactical branch execution in D1E.
