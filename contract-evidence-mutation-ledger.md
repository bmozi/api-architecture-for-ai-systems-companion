# Contract Evidence Mutation Ledger

Use this to test whether each evidence layer can detect the contract failure it
is assigned to protect.

## Status and evidence boundary

**Status:** Working companion asset; no mutation result exists until an
executable test or retained observation is attached.

A generated test, planned mutation, or green schema is not evidence that the
business promise survived.

## 1. Change and population

- **Contract and current baseline:**
- **Provider release candidate:**
- **Proposed change:**
- **Change owner and authority:**
- **Consumers represented:**
- **Consumers not represented:**
- **Client versions represented:**
- **Journeys and recovery paths represented:**
- **Known blind population:**

## 2. Evidence provenance

| Artifact or evidence layer | Author/source | Derived from | Independent assumption source? | Baseline/version | Owner |
| --- | --- | --- | --- | --- | --- |
| Specification/schema | | | yes/no/partial | | |
| Generated client | | | | | |
| Provider tests | | | | | |
| Consumer contract | | | | | |
| Authorization tests | | | | | |
| Failure/recovery tests | | | | | |
| Integration journey | | | | | |
| Production observation | | | | | |

Shared generation or fixtures can create correlated blind spots. Record them
rather than counting each artifact as independent agreement.

## 3. Mutation ledger

| Promise dimension | Deliberate mutation | First expected detector | Other layers expected to remain green | Result | First actual detector | Evidence link | Gap or follow-up |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Shape | | | | unrun | | | |
| Meaning | | | | unrun | | | |
| Acceptance/completion | | | | unrun | | | |
| Error/recovery | | | | unrun | | | |
| Authorization | | | | unrun | | | |
| Idempotency/concurrency | | | | unrun | | | |
| Timing/load/order | | | | unrun | | | |
| Observability/support | | | | unrun | | | |
| Privacy/lifecycle | | | | unrun | | | |
| Consumer population | | | | unrun | | | |

If no layer fails, retain the negative result. The portfolio has exposed an
evidence gap.

## 4. Gate behavior

- **Which failed mutations block release automatically:**
- **Which failures require human review:**
- **Who may approve an exception:**
- **Required rationale, expiry, and follow-up:**
- **Evidence retained with the release:**
- **Production signals that stop expansion:**
- **Reversal or forward-correction path:**

## 5. Bounded decision

> These evidence layers detected [mutations] for [represented consumers,
> versions, and conditions]. They did not detect or did not exercise [gaps].
> Release is [held/bounded/approved] under [constraints]. Reverse or stop if
> [evidence].

## Final review question

Which deliberate contract defect can still pass every required gate, and who
owns closing or accepting that evidence gap?
