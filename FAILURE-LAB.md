# API Failure Lab: The Successful Timeout

**Status:** Prepared, constructed, and unrun
**Purpose:** Test whether the contract and artifacts expose an unknown outcome
instead of inviting unsafe repetition
**Does not prove:** production correctness, idempotency, security, reliability,
business benefit, or practitioner usability

## Scenario

Northbridge receives `ReserveInventory` from an approved partner. The provider
commits the reservation, but the network fails before the client receives the
response. The client sees a timeout. An AI-mediated support tool suggests
retrying. The original authorization expires between attempts.

All names, timings, systems, and outcomes are constructed.

## Seeded defects

The candidate design contains five defects:

1. the API describes timeout as ordinary failure rather than unknown outcome;
2. the idempotency key is scoped to a transport attempt instead of business
   intent;
3. the MCP wrapper drops the original actor and authorization context;
4. the retry can create a second reservation after the first committed; and
5. logs show two calls but cannot join either call to the durable reservation.

Do not show this list to a participant before the exercise.

## Participant task

Using the [Meaning-and-Authority Brief](api-meaning-and-authority-brief.md),
[Idempotency Matrix](idempotency-and-outcome-test-matrix.md),
[Authority Map](authority-and-delegation-map.md), and
[Outcome Evidence Map](outcome-evidence-map.md):

1. classify the timeout;
2. decide whether a retry is allowed;
3. name the stable business identity;
4. state which authority must be revalidated;
5. define how the consumer discovers the current and final outcome; and
6. identify evidence that joins intent, attempt, effect, and result.

## Detection record

| Seed | Detected? | Where the artifact exposed it | Assistance required | Revision suggested |
| --- | --- | --- | --- | --- |
| Unknown outcome mislabeled | `UNRUN` | | | |
| Attempt-scoped idempotency | `UNRUN` | | | |
| Delegation lost in MCP wrapper | `UNRUN` | | | |
| Duplicate durable effect | `UNRUN` | | | |
| Missing evidence join | `UNRUN` | | | |

## Success condition

Success is not “the participant found all five.” Retain detections, misses,
confusion, invented assumptions, and requests for help. A missed defect may
identify a weak instruction, artifact, fixture, or knowledge dependency.

## Transfer

Repeat with one real capability only after confirming that no sensitive data,
credentials, exploit detail, or unapproved customer material enters the record.
