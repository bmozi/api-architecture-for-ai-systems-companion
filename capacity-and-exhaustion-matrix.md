# Capacity and Exhaustion Matrix

Use this to define consumer-visible behavior when demand, cost, present
capacity, entitlement, or abuse policy constrains a capability.

**Status:** Working companion asset; Northbridge and independent practitioner
validation remain open.

## 1. Protected boundary

- **Capability and consumer outcome:**
- **Resource, invariant, agreement, or population protected:**
- **Boundary type:** rate / quota / concurrency / cost / current capacity /
  abuse / priority-entitlement / degradation
- **Scope:** actor / client / principal / subject / tenant / capability / region
  / dependency / accepted-work class / other
- **Counted unit:**
- **Window, concurrency interval, or lifecycle:**
- **Cost estimator, version, error, and hard stops:**
- **Evasion and distributed-use boundary:**
- **Privacy-minimized identity and evidence:**

## 2. Policy, fairness, and authority

- **Entitlement or allocation rule:**
- **Why this rule is legitimate for the protected outcome:**
- **Competing work classes and protected minimums:**
- **Who defines, approves, administers, and enforces the policy:**
- **Who may change it dynamically or in an emergency:**
- **Minimum/maximum bounds and prohibited changes:**
- **Appeal, exception, and abuse-response authority:**
- **Effective time, policy version, communication, and audit:**

## 3. Exhaustion and consumer action

| Condition | Scope and unit | Acceptance/effect meaning | Safe consumer action | Identity, delay, attempt, and stop rule | Provider owner and evidence |
| --- | --- | --- | --- | --- | --- |
| Caller policy exhausted | | | | | |
| Service/dependency unavailable | | | | | |
| Request too large or costly | | | | | |
| Sensitive-flow abuse suspected | | | | | |
| Accepted work constrained | | | | | |
| Response absent or outcome ambiguous | | | reconcile if effect may exist | | |

Do not infer no acceptance, no effect, or safe retry from `429`, `503`,
`Retry-After`, a gateway counter, or transport failure alone.

## 4. Degraded behavior

### In-contract degraded state

- **Declared trigger and detecting evidence:**
- **Bounded loss in availability, fidelity, freshness, timing, or features:**
- **Consumer-visible signal and allowed action:**
- **Acceptance rule for new work:**
- **Protection and discovery for already accepted work:**
- **Restoration trigger, owner, and evidence:**

### Out-of-contract emergency change

- **Behavior the current promise no longer satisfies:**
- **Affected consumer population and exposure:**
- **Emergency authority and containment:**
- **Communication and safe recovery:**
- **Accepted-work protection:**
- **Retained unknowns:**
- **Reversal, migration, and incident evidence:**

## 5. Evidence and release

| Scenario | Protected outcome and expected bounded result | Negative result to retain | Evidence | Result |
| --- | --- | --- | --- | --- |
| Legitimate burst and sustained use | | | | unrun/pass/fail/unknown |
| Shared-tenant contention | | | | |
| Weighted query/bulk cost | | | | |
| Retry storm and ambiguous response | | | | |
| Distributed low-rate abuse | | | | |
| Emergency override | | | | |
| In-contract degradation and restoration | | | | |
| Out-of-contract change and reversal | | | | |

- **Legitimate work wrongly denied:**
- **Harmful work wrongly admitted:**
- **Unrepresented identities, workloads, dependencies, and timing:**
- **Release blockers:**
- **Hold, revise, or release:**
- **Evidence that would reverse the decision:**
