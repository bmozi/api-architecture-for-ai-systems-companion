# Completed Example: Northbridge Collection, Bulk, and Capacity Decisions

## Disclosure and evidence boundary

Northbridge Exchange, every system, policy, workload, and outcome below are
fictional composite teaching material. This example applies two working
companion tools to a frozen design scenario. It is not a John Briggs career
case, production design, load result, security assessment, or evidence that the
tools improve an outcome.

**Assets applied:**

- `../collection-and-bulk-decision-record.md`
- `../capacity-and-exhaustion-matrix.md`

**Status:** Coherent tool application; every mutation and scenario result is
`unrun`.

Expected behavior is a proposed contract requirement, not an observed result.

## Frozen scenario

An authorized partner can list its Northbridge reservation requests and submit
a batch asking Northbridge to cancel eligible requests. Northbridge also
provides same-identity reconciliation for accepted reservation outcomes.
Reconciliation protects responsibility already accepted; it does not authorize
new reservations, broader buyer access, or unlimited dependency traffic.

The exact governed nonterminal public state is `accepted_pending`. Only
`committed` permits the partner to rely on inventory. An `outcome_unknown` item
must be reconciled under its original identity rather than retried as
replacement intent.

---

## Part A: Collection and Bulk Decision Record

### 1. Collection contract

- **Capability and collection:** List the authenticated partner's authorized
  reservation requests for support, reconciliation, and order decisions.
- **Membership claim:** A changing view of reservation requests visible to the
  partner under the evaluated buyer, location, tenant, and field authority at
  each page request.
- **Member identity:** Stable Northbridge reservation-request identity.
- **Membership model:** Live, not a fixed snapshot. The collection does not
  promise exactly-once enumeration while membership changes.
- **Effective time:** Each page records its own observation time and contract
  version; no shared snapshot time is implied.
- **Total order:** `lastChangedAt` ascending, then reservation-request identity
  ascending as the unique tie-breaker.
- **Change behavior:** Inserts, deletes, visibility changes, and updates can
  move membership between page requests. The client must not infer a frozen
  total from a deterministic order.
- **Authorization scope:** Partner tenant, represented buyer relationship,
  permitted locations, permitted reservation objects, and approved fields.
  The filter grammar cannot cross those boundaries.
- **Count meaning:** Optional live authorized estimate at its own observation
  time. It is not an exact count for all pages and may be absent under cost or
  capacity policy.
- **Query grammar and cost:** Approved filters cover state, location, and a
  bounded change-time interval. Syntax acceptance does not establish
  affordable execution. The proposed cost model and thresholds remain
  undecided and untested.

### 2. Continuation and expiry

- **Mechanism:** Opaque provider-created continuation reference; consumers may
  neither inspect nor construct it.
- **Bound context:** Partner tenant, authorization version/category, filter,
  projection, contract version, last total-order position, and expiry.
- **Expiry/invalidation:** Proposed on retention expiry, incompatible contract
  change, or authority change. Exact duration remains undecided.
- **Replay:** Allowed only within the original bound context and lifetime;
  repetition can repeat page members and is not a business-effect operation.
- **Public expiry meaning:** The prior live traversal cannot be resumed under
  that token. This does not say that earlier members or a protected resource do
  or do not exist.
- **Prior-page validity:** Each earlier item retains the meaning it had at its
  recorded page observation. The pages do not combine into a frozen membership
  claim.
- **Allowed recovery:** Start a new live traversal, reconcile the client's
  already processed reservation identities, or stop and escalate if complete
  coverage is required.
- **Completeness:** Unknown after restart unless a separately approved
  reconciliation process establishes the required coverage.
- **Owner/evidence:** Partner API owner; token-policy version, bound-context
  digest, safe rejection category, page observation times, and permitted
  support reference. All tests remain `unrun`.

### 3. Bulk contract

- **Aggregate identity:** Partner cancellation-batch identity.
- **Item identity:** Original reservation-request identity plus the partner's
  cancellation-intent identity.
- **Attempt identity:** One transport or worker attempt; not a new business
  intent.
- **Admission meaning:** Durable aggregate acceptance means Northbridge owns a
  terminal item outcome for every admitted item. It does not mean every item
  will be cancelled.
- **Atomicity:** Independent partial outcomes. One array does not create one
  cross-item transaction.
- **Ordering/dependencies:** Input order is retained for correlation only;
  execution may reorder independent items. No item may infer success from a
  neighbor. A dependency must be explicit or the item is rejected before its
  consequence.
- **Rollback/compensation:** `rolled-back` is prohibited unless Northbridge can
  prove the relevant effect does not remain. The public vocabulary instead
  uses completed cancellation, terminal rejection, accepted incomplete,
  compensation pending, partially applied, or outcome unknown as facts warrant.
- **Duplicates:** Same aggregate and same item intent converge under their
  original identities; changed cancellation intent conflicts.
- **Authorization:** Every item rechecks partner, buyer, tenant, object, state,
  purpose, and applicable provider authority.
- **Limits:** Item, payload, cost, concurrency, and duration thresholds remain
  policy unknowns. Generation must not invent values.
- **Discovery:** Aggregate and per-item results remain discoverable under the
  accepted identity for a governed retention interval that is not yet decided.

### 4. Item outcome actions

| Public item outcome | Safe consumer action | Required identity/evidence | Result |
| --- | --- | --- | --- |
| Unavailable before acceptance with published retry permission | Retry the same item intent after the stated delay and within its attempt budget | No-acceptance evidence, item identity, policy version | unrun |
| `accepted_pending` | Observe the same item identity and escalate after its deadline | Accepted-work record, owner, deadline | unrun |
| Completed cancellation | Stop repeating; continue the post-cancellation process | Authoritative terminal version and release evidence | unrun |
| Terminal rejection | Correct materially new intent, appeal, or stop as the category permits | Stable rejection class and safe public detail | unrun |
| Conflict or stale state | Refresh authoritative state, then decide whether new intent is legitimate | Compared version and current public state | unrun |
| Compensation pending or partially applied | Observe and escalate; do not infer rollback | Effect and compensation references under the same item identity | unrun |
| `outcome_unknown` | Reconcile the same item identity; do not create replacement intent | Effect-correlating identity, protected evidence, owner | unrun |

### 5. Collection and bulk release decision

**Decision:** `hold`. The design record is coherent enough to direct tests, but
token lifetime, query-cost bounds, bulk limits, retention, and every mutation
result remain unknown or unrun.

**Release blockers:** Cross-tenant token reuse, a traversal that claims
completeness after a live restart, aggregate retry that repeats a completed or
owned item, generic retry of `failed` or unknown items, or a `rolled-back`
claim while an effect may remain.

---

## Part B: Capacity and Exhaustion Matrix

### 1. Protected boundary

- **Protected outcome:** Ordinary authorized reservation access must remain
  available while bounded reconciliation can resolve work Northbridge already
  accepted.
- **Boundary types:** Separate request rate, reconciliation concurrency,
  dependency cost, caller quota, present service capacity, sensitive-flow
  abuse, accepted-work priority, and degraded behavior.
- **Scope:** Partner/client/tenant/capability plus distinct new-intent and
  accepted-reconciliation work classes.
- **Counted units:** Requests are insufficient alone. Proposed units include
  item count, dependency attempts, concurrent reconciliations, query work, and
  accepted-work identities. Exact weights and limits are undecided.
- **Evasion boundary:** A recovery label never broadens buyer, tenant, object,
  or purpose authority. Distributed low-rate inventory holding and probing
  remain business-flow abuse candidates even below traffic counters.
- **Privacy:** Evidence uses opaque partner, accepted-work, policy, and outcome
  references; it does not require raw credentials or unrestricted buyer data.

### 2. Policy, fairness, and authority

- **Allocation rule:** Proposed bounded minimum share for legitimate
  same-identity accepted-work reconciliation, with concurrency, dependency,
  attempt, and time hard stops. Remaining capacity follows the approved tenant
  and commercial policy.
- **Legitimacy:** Northbridge already owns the accepted outcome, but that
  responsibility does not justify unlimited recovery or evasion of ordinary
  authority.
- **Authority:** Product, operations, security, commercial authority, and the
  contract owner approve the policy. The gateway enforces it but does not
  invent it. Emergency change requires named incident authority and reversal.
- **Appeal/abuse:** A protected review process may challenge a suspected abuse
  decision. Cost or anomaly alone does not prove malicious intent.

### 3. Exhaustion and consumer action

| Condition | Consumer meaning and safe action | Evidence requirement | Result |
| --- | --- | --- | --- |
| Named caller-policy exhaustion proved before acceptance | No new responsibility was accepted; retry only if that failure class explicitly permits it under same identity, delay, and budget | Admission-boundary and policy-version evidence; not a bare `429` | unrun |
| Present service or dependency unavailability | Follow the original-outcome and transport-failure contract; query accepted work before repeating | Health/capacity evidence plus accepted-work lookup | unrun |
| Accepted reconciliation constrained | Northbridge still owns the outcome; observe and escalate without replacement intent | Accepted identity, deadline, allocation, and owner | unrun |
| Response absent or effect ambiguous | Reconcile; a delay header cannot establish no effect or safe retry | Same business identity and protected effect evidence | unrun |
| Sensitive-flow abuse suspected | Follow the permitted challenge, review, or denial path; do not evade | Governed detection, authority, privacy, and appeal record | unrun |

### 4. Degraded behavior

**Proposed in-contract state:** Reduce optional projections and cap page or batch
size while preserving documented core fields, accepted-work discovery, safe
error meaning, and the separate acceptance rule for new work. Trigger, exact
bounds, consumer signal, and restoration evidence remain undecided and unrun.

**Out-of-contract emergency change:** Loss of accepted-outcome discovery,
unannounced stale commitment data, or shedding already accepted responsibility
is outside the promise. Treat it as an incident and compatibility breach:
identify affected consumers, authorize containment, communicate, preserve
known and unknown outcomes, and reverse or migrate. A visible banner or status
code would not make that loss compatible.

### 5. Capacity release decision

**Decision:** `hold`. No load, retry-storm, shared-tenant, low-rate abuse,
emergency override, or restoration scenario has run.

**Release blockers:** A policy that infers safe retry from `Retry-After`, lets
recovery identity broaden authority, cannot protect accepted responsibility,
silently changes the contract, or lacks an owner and reversal trigger.

## What this application establishes

It establishes that the two blank assets can represent the frozen scenario
without collapsing continuation into completeness, aggregate admission into
item outcome, `Retry-After` into safe retry, or degraded state into a compatible
change. It does not establish that the proposed decisions are correct, complete,
usable by an independent practitioner, implementable, fair, secure, reliable,
or beneficial.
