# Collection and Bulk Decision Record

Use this before choosing pagination mechanics, flexible query grammar, or a
bulk envelope. A valid page or array is not evidence of complete traversal,
affordable execution, one transaction, or safe item recovery.

**Use boundary:** Illustrative field tool; Northbridge and independent-
practitioner validation remain unrun. Completion is not certification or proof
of production fitness.

## 1. Collection contract

- **Capability and collection:**
- **Membership claim:**
- **Member identity:**
- **Membership model:** live / fixed snapshot / bounded stale / unspecified
- **Effective time or snapshot identity:**
- **Total order, direction, and tie-breaker:**
- **Behavior under insert, delete, update, and equal sort keys:**
- **Authorization scope by tenant, object, property, filter, and projection:**
- **Count meaning, exactness, effective time, scope, and cost:**
- **Filter/query grammar and semantic authority:**
- **Query cost estimator, version, error, hard stops, and change authority:**

## 2. Continuation and expiry

- **Continuation mechanism and whether clients may inspect or construct it:**
- **Bound filter, projection, tenant, authorization, contract, and snapshot:**
- **Expiry and invalidation:**
- **Replay behavior:**
- **Public expiry or rejection meaning:**
- **Are prior pages still valid, and for which claim?:**
- **Allowed recovery:** resume same snapshot / start new snapshot / restart live
  traversal / reconcile processed identities / stop and escalate
- **Checkpoint or identity rule:**
- **Completeness after recovery:** preserved / new claim / abandoned / unknown
- **Disclosure boundary and protected evidence:**
- **Provider owner and evidence:**

## 3. Bulk contract

- **Aggregate business request and identity:**
- **Logical item intent and identity:**
- **Technical attempt identity:**
- **Admission meaning for the aggregate:**
- **Atomicity model:** atomic / independent partial / dependency ordered /
  asynchronous
- **Execution and result ordering:**
- **Dependency, skip, stop-after-error, compensation, and rollback rules:**
- **Duplicate aggregate and duplicate item behavior:**
- **Authorization per aggregate, item, object, and property:**
- **Item, payload, duration, concurrency, and cost boundaries:**
- **Aggregate and item status discovery and retention:**

## 4. Item outcomes and recovery

| Public item outcome | Accepted responsibility? | Can an effect remain? | Terminal? | Safe action | Identity, delay, attempt, and stop rule | Evidence and owner |
| --- | --- | --- | --- | --- | --- | --- |
| Unavailable before acceptance | | | | | | |
| Accepted but incomplete | | | | | | |
| Completed commitment | | | | | | |
| Terminal business rejection | | | | | | |
| Conflict or stale state | | | | | | |
| Compensated or compensation pending | | | | | | |
| Partially applied | | | | | | |
| Unknown outcome | | | | reconcile same identity; do not create replacement intent | | |

Use `rolled-back` only when the contract can prove the relevant effect does not
remain. Reusing an identity does not by itself make repetition safe.

## 5. Evidence and release

| Mutation | Expected bounded result | Evidence | Result | What it does not prove |
| --- | --- | --- | --- | --- |
| Insert/delete/update between pages | | | unrun/pass/fail/unknown | |
| Equal sort keys | | | | |
| Expired/cross-scope token | | | | |
| Count and traversal diverge | | | | |
| High-cost valid query | | | | |
| Duplicate aggregate/item | | | | |
| Reordered/dependent items | | | | |
| Partial failure and response loss | | | | |
| Unknown item effect | | | | |

- **Release blockers:**
- **Unrepresented consumers, data, timing, and topology:**
- **Hold, revise, or release:**
- **Evidence that would reverse the decision:**
