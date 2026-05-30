# AIGM Props Read Status — 2026-05-29

## Current status

`gm_props_read` is now live in a useful first-pass form.

### Working live
- inspect nearest mobile
- inspect nearby creature / world target
- inspect self / requester
- open structured native props-read gump

### Structured output now available
The live props gump is returning practical exact details like:
- type
- serial
- map
- location
- hue
- alive/deleted/movable
- hits / mana / stam
- stats
- access level
- item id / weight / layer / amount where relevant

### Not yet reliable
- `inspect the katana in my bag`
- exact named item resolution in cluttered scenes
- some named-target disambiguation cases

## Architecture status
- canonical action type: `AIGMActionProposal`
- action kind: `gm_props_read`
- loose conversational recognition preserved
- explicit deeper inspect action path present
- native props-read execution path present

## Recommended next focus later
- named item resolution in backpack / container / ground contexts
- stronger mobile-name targeting
- then resume movement / travel lane when ready
