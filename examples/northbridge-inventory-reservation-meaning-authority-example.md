# Completed Example: Northbridge Inventory Reservation

## Evidence and provenance boundary

Northbridge Exchange and every detail below are fictional composite teaching
material. This example demonstrates how the brief changes a design conversation.
It is not a record of a real John Briggs engagement, empirical evidence that the
method improves delivery, or proof that this proposed contract is production
ready.

**Asset applied:** `../api-meaning-and-authority-brief.md`
**Book placement:** Chapters 1-3
**Status:** Worked example pending author and practitioner review

## The answer the team rejected

The first generation brief effectively said:

> Create `POST /inventory-reservations`. Accept product, location, buyer,
> quantity, and duration. Return `202 Accepted`, a reservation ID, and status.

The answer was technically usable, but it left the business meaning of
`accepted`, the source of partner authority, the one-commitment invariant,
unknown outcomes, and provider responsibility undecided.

## 1. Capability promise

- **Capability name:** Request and manage a time-bounded Northbridge inventory
  commitment.
- **Business outcome the consumer needs:** An authorized distribution partner
  can seek a commitment for an eligible buyer and location, learn whether
  Northbridge accepted responsibility for reaching an outcome, and discover
  whether the commitment was made without creating a second commitment during
  retry or recovery.
- **Why an API is the right interaction:** The partner deliberately invokes a
  governed Northbridge capability for a named buyer and needs an immediate,
  unambiguous response plus a queryable outcome when work continues.
- **What this contract does not promise:** Every requested quantity is
  available; `accepted` means committed; partner authentication grants
  authority for every buyer; or every commitment completes inside the initial
  response.

## 2. Parties and authority

- **Consumer:** The strategic distribution partner's order-integration system.
- **Provider accountable for the capability promise:** Northbridge Exchange.
  The partner inventory capability carries the public promise; warehouse and
  allocation systems are participating dependencies, not replacement contract
  owners.
- **Actor performing the immediate action:** The authenticated partner service
  identity attributable to the registered order-integration context.
- **Client presenting or transporting the request:** The strategic partner's
  registered order-integration application.
- **Principal whose authority is represented:** The eligible buyer account whose
  bounded authority is represented through an active delegation.
- **Delegate authorized to act for that principal:** The strategic partner,
  narrowed to the registered actor and client.
- **Affected subject or business party:** The named eligible buyer.
- **Protected object or resource acted upon:** The requested product inventory
  at the delivery location under the stated quantity and duration.
- **Tenant, organization, or account boundary:** The partner organization,
  buyer account, location, product, and contractual tier in Northbridge's
  authoritative commercial relationship record.
- **Authority required to request the capability:** The partner may seek a
  commitment only for buyers, locations, products, quantities, and tiers covered
  by an active delegation and Northbridge policy.
- **System or role authoritative for granting that authority:** The buyer's
  delegation and Northbridge commercial-policy authority, represented through
  the partner relationship and policy systems.
- **Contract owner:** Northbridge product owner for partner inventory
  commitments.
- **Change authority:** The contract owner with required commercial, security,
  operations, and representative-consumer evidence.
- **Operational owner:** Northbridge partner service operations, with escalation
  to inventory-allocation and relationship owners.

## 3. Meaning and outcomes

- **Preconditions:** Active partner and buyer relationship; valid delegation;
  eligible product and location; positive quantity within policy limits; valid
  requested duration; stable business-intent identity; and sufficient current
  information to accept responsibility safely.
- **A request is accepted when:** Northbridge has authenticated and authorized
  the request, validated the business identity, atomically recorded the intent
  and idempotency disposition, assigned a reservation request ID, and taken
  responsibility for reaching and reporting a terminal outcome.
- **The business outcome is complete when:** The authoritative reservation
  record reaches `committed`, `rejected`, `expired_without_commitment`, or
  `cancelled_after_release`, with the evidence required for that outcome.
- **Authoritative outcome record:** Northbridge's reservation commitment record,
  linked to request intent, authority decision, allocation evidence, expiry,
  release, and any reconciliation work.
- **Information returned to the consumer:** Reservation request ID,
  idempotency disposition, current state, committed quantity and expiry when
  known, safe reason/next-action code, current version, status path, and last
  change time.
- **Information intentionally not exposed:** Other buyers' allocations,
  restricted commercial priority, internal queue names, raw dependency errors,
  employee notes, and protected policy detail.
- **Invariants that must remain true:** One business intent cannot create two
  commitments; total commitments cannot exceed the authoritative allocatable
  quantity under policy; the actor cannot cross buyer, location, or tenant
  boundaries; `committed` is never reported without allocation evidence; and
  dependency ambiguity does not silently transfer responsibility to the
  partner.

## 4. Repetition, conflict, and time

- **What may safely repeat:** Outcome retrieval. The same reservation intent may
  be resubmitted with the same business identity and normalized content to
  retrieve the original request and outcome.
- **Business idempotency key or identity:** Partner organization plus buyer,
  location, partner reservation-intent ID, and normalized commitment purpose.
- **Concurrency or stale-state rule:** Requests are evaluated against an
  authoritative inventory/allocation version. Conflicting commitments return a
  defined conflict or remain pending for owned reconciliation; stale success is
  not invented.
- **Transaction boundary:** Acceptance atomically records request identity,
  authority decision, idempotency mapping, initial state, and an outbox-style
  durable work record in the same transactional store. Dispatch into an
  external workflow or broker and allocation across downstream systems occur
  outside that transaction and require retry and reconciliation.
- **Expected response-time boundary:** The initial response returns a terminal
  non-acceptance when that decision is authoritative or an accepted-responsibility
  record when work continues. A measurable response target remains an open
  service decision, not an invented scenario fact.
- **When work continues after the response:** When allocation, policy
  reconciliation, dependency recovery, or authorized human review remains open.
- **How the consumer discovers final outcome:** The status API is the recovery
  path. Permitted events may accelerate awareness but do not replace the
  authoritative query contract unless their recovery promise is separately
  established.

## 5. Failure contract

| Failure class | Meaning to consumer | Safe consumer action | Evidence retained |
| --- | --- | --- | --- |
| Invalid request | Northbridge did not accept responsibility because the intent could not be evaluated under the contract | Correct the stated issue and follow the documented identity-reuse rule | Validation category, contract version, request digest, correlation |
| Not authorized | The actor cannot seek this commitment for this buyer, location, product, quantity, or tier | Stop and obtain legitimate delegation or escalate through the relationship owner | Principal, subject boundary, policy version, denial category |
| Conflict or stale state | Current allocation state conflicts with the proposed commitment | Retrieve current state and decide whether a new intent is legitimate; do not blind-retry | Compared version, current version, conflict record where disclosure permits |
| Unavailable before acceptance | Northbridge proved that it did not accept responsibility or create a commitment inside the response boundary | Reuse the same business identity after the bounded delay | Acceptance-boundary evidence, idempotency lookup, sanitized failure, timing |
| Accepted but incomplete | Northbridge owns completion, but allocation or reconciliation remains pending | Query the same request and use the named escalation path after its deadline | Durable state, owner, deadline, attempts, last transition |
| Terminal business rejection | Northbridge completed evaluation and made no commitment | Use the stable reason, correction, or appeal path; do not resubmit as new without changed intent | Decision authority, policy/evidence versions, reason category |
| Unknown outcome | A commitment may exist, but Northbridge cannot yet prove the result | Query and escalate the same request; never create a replacement intent merely because of timeout | Attempt identity, allocation references, reconciliation state, operator actions |

## 6. Compatibility promise

- **Consumers or consumer classes:** The strategic partner integration and
  future partner integrations admitted to the same capability class.
- **Behavior they may rely on:** Stable distinction among not accepted,
  accepted responsibility, pending progress, and terminal outcomes; same-intent
  retry returns the original request; and accepted work retains a recovery path.
- **Semantic assumptions that must remain stable:** `accepted` does not mean
  committed; `pending` does not mean safe to replace; `unknown` does not mean
  rejected; and `expired` names a terminal contract outcome.
- **Timing, ordering, or volume assumptions:** None are promised until measured
  and approved. Consumers use state version and business identity rather than
  event arrival order.
- **Authorization assumptions:** Authentication never broadens buyer, location,
  product, quantity, or tier delegation.
- **Deprecation and migration promise:** Changes to outcome meaning, identity,
  authority, recovery, or required consumer behavior need explicit migration
  evidence and notice even when schema remains valid.
- **Exit or reversal path:** Northbridge may stop accepting new requests while
  preserving outcome and recovery access for already accepted work. Accepted
  responsibility does not disappear when the submission endpoint is disabled.

## 7. Evidence floor

- **Contract/schema evidence:** The specification represents the decided state,
  errors, authority inputs, identity, and examples without claiming syntax
  proves meaning.
- **Behavioral evidence:** Allowed and prohibited transitions, expiry, release,
  rejection, and unknown reconciliation are exercised.
- **Authorization evidence:** Positive and negative cases cross partner, buyer,
  location, product, quantity, tier, and revoked delegation boundaries.
- **Idempotency/concurrency evidence:** Simultaneous same-intent requests,
  same-key/different-intent requests, stale allocation state, lost responses,
  and delayed completion create at most one commitment.
- **Representative consumer evidence:** The partner handles every outcome,
  retries the same intent safely, and does not interpret acceptance as
  commitment.
- **Failure and recovery evidence:** Dependency timeout, duplicate processing,
  delayed event, restart, reconciliation, expiry, and release are exercised.
- **Operational observability evidence:** One reservation identity reconstructs
  request, authority, acceptance, allocation attempts, outcome, events,
  consumer retrieval, and operator actions without prohibited detail.
- **Unknowns that block implementation or release:** Unresolved allocation
  idempotency, authority propagation, outcome reconciliation, support ownership,
  or any consumer path that cannot take a safe action.

## What changed because the fields were completed

1. Northbridge's application contract attached responsibility for a terminal
   answer to its `202 Accepted` response. The HTTP status alone did not create
   that business meaning or prove durable acceptance.
2. Partner identity stopped standing in for authority over every buyer and
   location.
3. The public reservation stopped mirroring four internal records.
4. Retry attached to one business intent rather than one HTTP request.
5. Unknown allocation outcome became a reconciliation state rather than an
   invitation to submit again.
6. The API, workflow, and event roles could be separated without splitting the
   consumer's business identity.
7. The evidence plan included denial, duplication, delay, and disagreement—not
   only successful schema and local tests.

## Remaining limits

This completed example is still a proposed composite design. It has not been
implemented, independently tested, reviewed by a partner, or supported by
measured service evidence. Its value is that unresolved decisions are now
visible enough to challenge.
