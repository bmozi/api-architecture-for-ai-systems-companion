# API synthetic revised capability brief

Artifact ID/version: API-A-REVISED-CAPABILITY-BRIEF/v1
Completion timestamp/timezone: 2026-08-30T14:06:00-0600 MDT
Pre-hash state: REVISED COMPLETE

## Capability promise

Stonebridge exposes a rental-extension request for an identified rental and customer intent. An authorized partner may submit the request and query its state. The service may return `accepted` only to confirm receipt and correlation, never as proof that the rental changed, a charge committed, or a reservation remained safe.

## Authority and boundaries

The partner service account identifies the caller. Staff identity and customer intent are separate claims. AI-agent authority without staff confirmation is `UNKNOWN` and therefore withheld. Payment-term changes are outside this promise until a policy authority approves them.

## State and recovery

States are `RECEIVED`, `PENDING_REVIEW`, `UNKNOWN`, `REJECTED`, and `COMPLETED`. A timeout requires lookup/reconciliation by the stable intent identity; a new tool-call identifier never authorizes a second business effect. A workflow owns unresolved review, and an event named `RentalExtensionCompleted` may be emitted only after the authoritative rental decision and required billing/reservation evidence exist.

## Evidence gate

Completion requires the rental record's final state, warehouse conflict decision, billing reconciliation, and notification receipt linked to the same intent. Production implementation, usability, security, and business-value evidence are not present.
