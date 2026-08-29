# Idempotency and Outcome Test Matrix

Use this to test and record bounded evidence for a business-outcome invariant
across repeated, concurrent, stale, timed-out, and replayed intent.

## Status and purpose

**Status:** Working companion asset; independent practitioner and executable
testing remain open.

This matrix deliberately counts business outcomes rather than assuming one
handler invocation, one message delivery, or one transport response proves
idempotency.

It does not prove exactly-once execution across an unbounded distributed
system. It records the conditions under which attempts should converge on one
defined outcome and the evidence required when they do not.

## 1. Protected intent

- **Capability and operation:**
- **Business outcome that must occur once:**
- **Consumer-supplied identity:**
- **Provider scope for that identity:**
- **Material intent fields bound to the identity:**
- **Authority and tenant binding:**
- **Retention and expiry rule:**
- **Authoritative outcome source:**

## 2. Competing intent

- **State or capacity that different intents compete for:**
- **Invariant that must remain true:**
- **Conflict winner/loser/wait rule:**
- **Expected-version or conditional rule, if used:**
- **Authority entitled to establish the final state:**

## 3. Transaction boundaries

| Boundary | What changes together | What can succeed separately | Identity preserved across seam | Recovery owner | Evidence |
| --- | --- | --- | --- | --- | --- |
| Local atomic state | | | | | |
| Outbound message or delivery | | | | | |
| Remote service effect | | | | | |
| Human or physical action | | | | | |
| Business outcome | | | | | |

## 4. Outcome matrix

| Scenario | Expected response or discovery path | Expected consumer behavior | Required business invariant | Evidence | Result | What the result does not prove |
| --- | --- | --- | --- | --- | --- | --- |
| Same identity, same intent, after success | | | No second business outcome | | pass/fail/unknown | |
| Same identity, materially changed intent | | | Original intent is not silently reinterpreted | | | |
| Same identity, concurrent arrival | | | One protected effect path | | | |
| Distinct identities competing for scarce state | | | Domain capacity or uniqueness holds | | | |
| Timeout before durable acceptance | | | No accepted work is lost or invented | | | |
| Timeout after possible external effect | | | No unsafe replacement intent | | | |
| Downstream duplicate or replay | | | Allowed number of committed effects | | | |
| Stale expected version | | | Newer authoritative state is not overwritten | | | |
| Crash after local state but before outbound delivery | | | Durable intent to continue or reconcile exists | | | |
| Crash after effect but before local result | | | Unknown outcome remains discoverable and owned | | | |
| Replay at retention boundary | | | Contract does not claim evidence after it expires | | | |

## 5. Unknown-outcome path

- **How uncertainty is recorded:**
- **How unsafe replacement intent is prevented:**
- **Authority consulted for reconciliation:**
- **Evidence connecting external effect to business identity:**
- **Deadline and escalation owner:**
- **Allowed terminal outcomes:**
- **What happens if certainty cannot be restored:**

## 6. Counts and claims

Record these separately:

- **Transport attempts:**
- **Handler executions:**
- **Outbound deliveries:**
- **External action attempts:**
- **Technical successes:**
- **Distinct committed business effects:**
- **Terminal rejected outcomes:**
- **Unresolved outcomes:**

Then state the bounded claim:

> Under [identity scope, retention, topology, failure mutations, and test
> conditions], [attempts] converged on [allowed business outcomes]. This does
> not establish [untested boundaries].

## 7. Release decision

- **Protected invariant demonstrated:**
- **Failures or unknowns:**
- **Scope not exercised:**
- **Retention and privacy concerns:**
- **Recovery paths without an owner:**
- **Hold, revise, or release:**
- **Evidence that would reverse the decision:**

## Guardrails

- Repetition and competition are different problems.
- A key is not proof that clients reuse it correctly.
- A local transaction does not include a remote effect by declaration.
- Deduplicating delivery does not prove one end-to-end business effect.
- A rollback cannot erase an effect already committed elsewhere.

## Final review question

If every technical attempt ran more than once, which governed identity,
invariant, boundary, and evidence would still protect the promised number of
business outcomes?
