# SESSION LOG - 2026-06-01 - AIGM Companion Dialogue Breakthrough

## Summary

This session produced a working breakthrough in linked companion communication for Dakeyras and Danyal.

The practical result is that the two AIGM companions can now participate in linked dialogue behavior through a dedicated companion dialogue architecture instead of relying only on raw proximity speech.

## What Was Broken

Several overlapping issues were identified during live testing:

1. **Compile mismatch in relay code**
   - Legacy relay calls referenced `HandleRelayedCompanionSpeech(...)`, but the companion classes actually exposed `ReceiveSpeechBusEvent(...)`.

2. **Owner speech only worked by proximity**
   - The nearest companion heard the player directly through ServUO `OnSpeech(...)`.
   - The farther linked companion often did not receive the same command reliably.

3. **Relay authority was degraded on receipt**
   - Relayed owner speech could be processed as if the source companion were the authority instead of the original owner.

4. **Remote owner commands were blocked by distance gates**
   - Direct action policy still enforced a local range check even for relayed trusted owner instructions.

5. **Companion acknowledgement echo loops**
   - When generic companion reply speech was rebroadcast as actionable speech, the companions could spiral into repeated back-and-forth acknowledgements.

6. **Companion dialogue and owner speech were being treated as the same lane**
   - This created ambiguity between command execution, overheard speech, and peer-to-peer companion conversation.

## Architectural Direction Chosen

The system was split conceptually into separate speech lanes:

- **Owner command lane**
  - direct authority
  - direct execution allowed
  - can relay to linked companions

- **Owner/world speech lane**
  - conversational speech from the player
  - can enter the async speech queue

- **Companion dialogue lane**
  - explicit peer-to-peer companion communication
  - no longer treated purely as overheard owner speech
  - routed through a dedicated dialogue bus/event model

## Key Implemented Changes

### 1. Relay and authority fixes
- Corrected relay integration to use the actual receive-side speech bus method.
- Preserved original owner speaker identity on relayed speech.
- Allowed trusted relayed owner instructions to bypass the usual local 12-tile direct-action distance rejection.

### 2. Broader linked companion lookup
- Linked companion speech lookup moved away from narrow local-only relay assumptions.
- Same-owner companion enumeration on the same map was used for more reliable distribution.

### 3. Dedicated companion dialogue architecture
New dialogue-specific code surfaces were introduced:
- companion dialogue event model
- companion dialogue bus
- dialogue-mode request metadata sent through the middleware bridge
- dedicated receive-side companion dialogue handlers on Dakeyras and Danyal

### 4. Async reply promotion into dialogue
- A major missing bridge was identified: owner/world chatbot replies that were clearly addressed to another linked companion were being spoken locally but not promoted into the dedicated peer dialogue lane.
- This was corrected by detecting addressed companion replies and promoting them into the dialogue bus.

### 5. Dialogue instrumentation
To stop guessing and verify real runtime behavior, additional execution logging was added around:
- dialogue publish
- dialogue dedupe
- dialogue delivery
- queue rejection
- HTTP request start/done
- dialogue promotion from chatbot reply into peer dialogue

## Live Validation Notes

Live testing showed the following progression:

- early runs proved direct owner speech worked only on the nearest companion
- broader relay work made both companions react more consistently to owner-level commands
- echo-loop behavior confirmed that cross-companion propagation existed, but needed stricter handling
- log instrumentation eventually proved that the dedicated dialogue lane was not being entered during key tests
- the missing promotion step from companion-addressed chatbot replies into the dialogue bus was then added
- after that change, the session concluded with **total success** reported by live testing

## Why This Matters

This is important for Neo UO long-term because companion communication is now moving toward a maintainable architecture instead of accumulating fragile one-off relay patches.

The long-term value is:
- cleaner separation of speech intent
- less confusion between command handling and dialogue behavior
- a better foundation for future multi-companion coordination
- improved maintainability as the AIGM companion layer grows

## Follow-Through Recommendation

This session’s code changes should be preserved in the code repo as a coherent vetted feature slice, while this repository should retain the design and operational narrative explaining:
- what was broken
- why the previous model was insufficient
- what architecture replaced it
- how to reason about future companion communication work
