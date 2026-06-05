# AIGM Companion Follow-up — 2026-06-04

Follow-up stabilization pass after the initial companion recovery.

## Confirmed improvements
- auto-healing now persists until full health instead of stopping at narrow thresholds
- Danyal received stronger self-support fallback behavior when bandaging does not cleanly engage
- Dardalion received melee-oriented close-pressure / pursuit behavior to improve engagement while out of melee range
- shared owner-hearing and owner-conversation reply flow were loosened so group interaction feels less blocked by queue cooldowns

## Current quality note
The talking layer is improved and usable, but still somewhat brittle in multi-party conversation. Shared hearing is substantially better than before, though there are still moments where reply timing / queue state can feel uneven.

## Authoritative code backup
The exact live implementation mirror remains the `neo-uo-code` repository.
