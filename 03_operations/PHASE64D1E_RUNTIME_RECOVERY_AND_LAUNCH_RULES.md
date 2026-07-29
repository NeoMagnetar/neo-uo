# Phase64D1E Runtime Operations Record

## Launcher Authority

The durable CleanProof launcher is the authoritative local startup path for runtime proof. Transient agent-child server launches are prohibited for acceptance proof because they can disappear when an automation session ends.

The launcher must start the CleanProof server executable directly, preserve the CleanProof working directory, wait for the accepted shard port, check that the older dev port is unused, and then launch the accepted deployed client without replacing binaries.

## Account Safety

Account credential fields are immutable during startup and runtime repair. Startup or repair procedures must not rewrite account secrets. The previously quarantined startup-repair evidence must remain quarantined and must not be reused.

Public records must not include account names, account hashes, password values, stored credential values, saves, or account files.

## D1E Runtime Safety

D1E receipt storage is private runtime evidence. Private JSONL traces, screenshots, saves, and audit ZIP contents are not published.

Preview watch is disabled by default, opt-in per actor, bounded, coalesced, and stopped after proof.

