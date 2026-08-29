# Completed Example: Northbridge Recovery, Repetition, and Change

## Disclosure and evidence boundary

Northbridge Exchange, its partner, its systems, and every incident below are
fictional composite teaching material. The example applies the working tools
from Chapters 7, 8, and 10. It is not a production result, a John Briggs career
case, a measured reliability claim, or evidence that the tools work for
independent practitioners.

The examples marked `pass` are **required scenario outcomes**, not observed
test results. They remain `unrun` until an executable experiment produces and
retains evidence.

## Frozen capability

Northbridge promises an authorized distribution partner one governed decision
for a time-bounded inventory commitment associated with a named buyer,
location, product, quantity, and business request identity.

The API distinguishes:

- **not accepted:** Northbridge has not taken responsibility;
- **accepted:** Northbridge owns progress toward a terminal outcome;
- **committed:** the reservation exists and the partner may rely on it within
  its terms;
- **rejected, expired, or cancelled:** evaluation is complete without an active
  commitment;
- **pending review:** Northbridge owns progress but a commercial authority must
  decide; and
- **unknown:** an allocation effect may exist, but Northbridge cannot yet prove
  the authoritative result.

The protected business invariant is:

> One authorized business request identity may produce no more than one active
> inventory commitment, even when transport attempts, handler executions,
> deliveries, and downstream action attempts repeat.

This invariant does not claim that every technical step executes exactly once.

## Part A: Error-to-Recovery Map

### Capability and outcome boundary

- **Capability:** Obtain one time-bounded inventory commitment or a defined
  terminal result.
- **Operation under review:** Request inventory reservation.
- **Consumer decision after response:** Promise inventory, wait, correct,
  obtain authority, refresh, reconcile, escalate, or stop.
- **Business identity:** Partner-scoped reservation request identifier bound to
  buyer, location, product, quantity, purpose, and contractual tier.
- **Acceptance boundary:** Northbridge has durably stored the authorized intent,
  its identity binding, its accepted state, and responsibility for a terminal
  result.
- **Authoritative outcome source:** Northbridge reservation commitment record,
  reconciled with the allocation authority before a commitment is declared.
- **Operational owner:** Partner service operations for accepted or disputed
  cases; commercial authority for review; platform reliability for evidence and
  dependency recovery.

### Recovery actions

| Action | Northbridge meaning | Identity rule | Stop condition |
| --- | --- | --- | --- |
| Correct | Fix a stated validation or eligibility defect before acceptance | Reuse only if the contract says the corrected fields do not change bound intent; otherwise create new identity | Request becomes evaluable or is abandoned |
| Obtain authority | Establish a valid delegation or approval for the same subject and purpose | A previously unaccepted request may be resubmitted under the published rule; never mutate evidence of the denied attempt | Authority is granted or request is abandoned |
| Refresh state | Retrieve authoritative version after a stale or conflicting transition | Preserve the attempted identity in evidence; create new business intent only if the consumer chooses a materially new action | Consumer acts on current state or stops |
| Retry | Repeat the same intent under the same identity and bounded timing rule | Same identity and same bound content are mandatory | Existing outcome is returned, request reaches a terminal state, or retry budget ends |
| Wait or observe | Northbridge already owns progress | Query the existing request identity; do not create a replacement | Terminal outcome or escalation deadline |
| Reconcile | Determine whether an external effect exists after an ambiguous result | Same identity across Northbridge and allocation authority | Authoritative result is established or unresolved-case authority intervenes |
| Escalate | Transfer an overdue or disputed case through the named support path | Preserve all identities and evidence; escalation does not become a new reservation request | Owner records resolution or governed unresolved result |
| Stop | Take no further action under the current intent | Preserve final identity for evidence and dispute window | Terminal result and retention policy complete |

### Error decisions

| Public outcome | Meaning | Accepted? | Effect may exist? | Safe consumer action | Public detail | Protected evidence |
| --- | --- | --- | --- | --- | --- | --- |
| `invalid_intent` | The request cannot be evaluated under the contract | No | No | Correct or stop | Stable field/rule category and correction guidance | Raw validation traces and protected submitted values |
| `authority_not_established` | The actor has not proved authority for this subject and purpose | No | No | Obtain authority or stop | Bounded category and allowed authority path without confirming prohibited buyer data | Actor, principal, subject reference, tenant, policy version, decision, and reason |
| `state_conflict` | Current authoritative state does not permit the requested transition | No for new transition | Existing prior outcome may exist | Refresh and decide; do not blind retry | Current public version or safe discovery reference | Full transition history and competing decision evidence |
| `temporarily_unavailable_before_acceptance` | Northbridge did not cross durable acceptance | No | No Northbridge commitment from this request | Retry same identity after bounded delay | Same-identity instruction and timing boundary | Attempt and acceptance-boundary trace |
| `accepted_pending` | Northbridge owns progress but no terminal outcome exists | Yes | Not yet declared; allocation may be in progress | Observe same identity and escalate after deadline | Outcome reference, current state, next observation time, deadline | Durable state, attempts, owner, policy and allocation references |
| `reservation_rejected` | Evaluation completed without a commitment | Yes | No active commitment for this identity | Correct materially new intent, appeal, or stop | Stable business reason and allowed appeal/correction path | Decision authority, rules/evidence versions, final state |
| `outcome_unknown` | An allocation effect may exist but cannot yet be proved | Yes | Yes or no | Reconcile same identity; never create replacement solely because of timeout | Outcome reference, prohibition on replacement, escalation path | Downstream identity, request digest, attempts, observations, reconciliation actions |

### Disclosure counterexample

Rejected design:

```json
{
  "error": "BUYER_78422_EXISTS_BUT_PARTNER_ROLE_DISTRIBUTOR_L2_IS_NOT_ALLOWED",
  "policy": "northbridge-prod-pdp-3/rule-118",
  "allocationHost": "alloc-db-07"
}
```

Why rejected:

- it confirms a buyer's existence to a caller not authorized to know;
- it exposes provider topology and policy internals;
- it encourages clients to couple to unstable internal role names; and
- none of those details is necessary for the permitted recovery action.

The protected record may retain the diagnostic facts for authorized
investigation. The public error communicates the recovery category and safe
path.

## Part B: Idempotency and Outcome Matrix

### Protected intent and competition

- **Consumer identity:** `partnerReservationRequestId`.
- **Scope:** provider, partner organization, capability, and tenant boundary.
- **Intent binding:** buyer, location, product, quantity, purpose, requested
  duration, and contractual tier.
- **Retention:** must outlast the contractual retry, reconciliation, dispute,
  and evidence window; the exact duration remains an open policy decision.
- **Competing state:** allocatable quantity for product and location plus any
  buyer-specific active-reservation rule.
- **Concurrency invariant:** committed quantity cannot exceed authoritative
  allocatable quantity, and one request identity cannot own two active
  commitments.
- **Final authority:** the Northbridge commitment boundary may declare the
  partner-facing outcome after reconciliation with the allocation authority.

### Transaction boundaries

| Boundary | Changes together | Can succeed separately | Recovery requirement |
| --- | --- | --- | --- |
| Northbridge local acceptance | Request identity, intent digest, accepted state, responsibility owner, and durable intent to allocate | Downstream allocation | Resume or reconcile from durable accepted state |
| Allocation authority | Allocation decision and allocation-owned reference | Northbridge observation of the result | Same business identity or durable cross-reference |
| Partner response | Public representation of current Northbridge outcome | Network delivery to partner | Partner rediscovers outcome by identity |
| Business outcome | At most one active commitment for the request identity within available capacity | Technical attempts at every seam | Count distinct commitments and unresolved cases |

The local transaction does not include the allocation authority simply because
the handler invokes it.

### Planned mutation matrix

| Scenario | Expected consumer behavior | Required invariant | Required evidence | Planned result |
| --- | --- | --- | --- | --- |
| Same identity and same intent after commitment | Discover existing commitment | One active commitment | Identity-to-outcome record and allocation reference | unrun |
| Same identity with changed quantity | Stop on conflict | Original intent not mutated | Intent digest and conflict result | unrun |
| Same identity arrives concurrently | Observe pending or existing result | One protected effect path | Atomic identity claim and attempt trace | unrun |
| Distinct requests race for final unit | One commits; other reaches defined noncommitment outcome | Capacity never negative | Authoritative allocation transitions | unrun |
| Timeout before acceptance | Retry same identity under published delay | No accepted work invented or lost | Acceptance-boundary trace | unrun |
| Allocation commits and response is lost | Reconcile same identity | No replacement commitment | External reference, unknown state, reconciliation trace | unrun |
| Accepted worker crashes before allocation delivery | Observe pending; provider resumes | Accepted responsibility survives | Durable intent and recovery execution | unrun |
| Replay after evidence retention expires | Follow explicit expiry rule | Provider makes no unsupported convergence claim | Retention event and public boundary | unrun |

### Claims to record separately

Any future experiment must report, rather than collapse:

- transport requests;
- handler executions;
- outbound deliveries;
- allocation attempts;
- technical successes;
- distinct active commitments;
- terminal noncommitment outcomes; and
- unresolved outcomes.

The release-relevant count is not the number of times machinery moved. It is
whether the business outcome invariant survived the exercised failures.

## Part C: Compatibility Evidence Matrix

### Proposed change

Northbridge adds `review_required` as a nonterminal reservation state. A
commercial approver—not the partner—has authority to advance that state.

### Evidence plan

| Promise dimension | Partner assumption | Proposed effect | Required evidence | Planned result | What remains unknown |
| --- | --- | --- | --- | --- | --- |
| Schema/shape | Existing response remains parseable | New status value | Schema comparison plus old and current client parsing | unrun | Unrepresented strict parsers |
| Business semantics | Only `committed` authorizes order advancement | New state must wait | Representative client behavior under mutation | unrun | Dormant client versions |
| Error and recovery | Pending review is observed or escalated, never retried as new intent | Adds review deadline and path | Lost-poll, long-delay, and escalation tests | unrun | Conditions beyond test window |
| Authorization | Partner can observe allowed review state but cannot approve it | Adds commercial authority | Positive and negative actor/subject/purpose tests | unrun | Policy rollout across every tenant |
| Idempotency/concurrency | Same request identity survives review and partner retries | Longer-lived pending state | Duplicate and timeout matrix through review | unrun | Retention beyond declared window |
| Timing | Partner gets a terminal result or a named overdue path | May extend completion time | Deadline, load, and escalation evidence | unrun | Peak conditions not represented |
| Observability/support | Support distinguishes pending review from unknown allocation | Adds new state and owner | Incident reconstruction with permitted evidence | unrun | Cross-system retention mismatch |

### Bounded decision form

No compatibility conclusion has been earned. A future decision should read:

> Compatible for the represented partner clients and exercised business
> decisions if the parsing, order-advancement, recovery, authority, repetition,
> deadline, and operational evidence passes. Unknown for unrepresented client
> versions and untested load or retention conditions. Hold or reverse expansion
> if an unknown state advances an order, a partner can approve review, one
> identity creates a second commitment, or support cannot reconstruct the
> outcome.

“The schema diff passed” would answer only the first row.

## What this completed example establishes

It establishes that the three blank tools can be filled coherently against one
frozen composite capability while preserving:

- one vocabulary from failure through repetition and change;
- a distinction between public recovery meaning and protected evidence;
- a distinction between repeated attempts and competing intent;
- explicit local, external, and business transaction boundaries;
- planned evidence that counts committed effects; and
- a bounded compatibility decision with named unknowns.

## What it does not establish

It does not establish:

- that the tools are understandable without chapter context;
- that the classifications are complete or universally correct;
- that any implementation satisfies the invariant;
- that the planned mutations produce the expected result;
- that the retention, privacy, security, or authorization choices are
  sufficient;
- that independent practitioners would reach the same decisions; or
- that using the tools improves delivery speed, reliability, safety, or
  business outcomes.

Those gates require independent use, executable evidence, author review, and
real operational context.
