# Completed Example: Northbridge Authority, Mutation, and Outcome Evidence

## Disclosure and evidence boundary

Northbridge Exchange, its partner, its buyers, and every system and decision
below are fictional composite teaching material. This example applies three
illustrative field tools to the frozen inventory-reservation scenario. It is
not a production result, a John Briggs career case, a security assessment, or
evidence that the tools improve an outcome.

**Assets applied:**

- `../authority-and-delegation-map.md`
- `../contract-evidence-mutation-ledger.md`
- `../outcome-evidence-map.md`

**Book placement:** Chapters 11, 13, and 14
**Status:** Coherent tool application; all tests, mutations, and
reconstructions are `unrun`

Every `Result`, `First actual detector`, and evidence result below is
explicitly `unrun`. Expected decisions are design requirements, not observed
behavior. Nothing in this example is empirical evidence.

## Frozen capability and governed states

Northbridge promises an authorized strategic distribution partner one governed
decision for a time-bounded inventory commitment associated with a named buyer,
location, product, quantity, purpose, contractual tier, and business request
identity.

The complete governed state vocabulary remains:

| State | Contract meaning |
| --- | --- |
| `received_unaccepted` | Northbridge can correlate the attempt but has not taken responsibility for reaching a terminal outcome. |
| `accepted_pending` | Northbridge has durably accepted responsibility and work continues. |
| `review_required` | Northbridge still owns progress, but an authorized Northbridge commercial approver must decide whether work may advance. The partner may observe but may not approve this state. |
| `committed` | An authoritative, time-bounded inventory commitment exists. |
| `rejected` | Northbridge completed evaluation without creating an active commitment. |
| `unknown_reconciliation` | An allocation effect may exist, but Northbridge cannot yet prove the authoritative result. |
| `expired_without_commitment` | The accepted request reached its governed deadline without an active commitment. |
| `cancelled_after_release` | A prior commitment has been released and is no longer active. |

The protected business invariant remains:

> One authorized business request identity may produce no more than one active
> inventory commitment, even when requests, deliveries, handlers, allocation
> attempts, reviews, responses, and observations repeat.

The partner-scoped business identity is
`partnerReservationRequestId` bound to partner organization, buyer, location,
product, quantity, purpose, requested duration, and contractual tier.
Northbridge assigns `northbridgeReservationRequestId` when it accepts
responsibility. Those identities are related; they are not interchangeable.

---

## Part A: Authority and Delegation Map

### 1. Capability and decision

- **Capability and operation:** Request inventory reservation through
  `POST /inventory-reservations`; observe the accepted request through its
  status resource; and, separately, advance `review_required` through the
  internal commercial-review capability.
- **Business consequence:** Northbridge may create an inventory commitment on
  which the partner can rely for the named buyer and delivery location.
- **Protected action:** Ask Northbridge to evaluate and, if permitted, commit
  inventory for one bound business intent. Commercial approval is a separate
  protected action.
- **Protected object or resource:** The named reservation intent and its
  allocation candidate for the specified product, quantity, and location.
- **Subject or party affected:** The eligible buyer account and delivery
  location. This affected business party is not shorthand for the authenticated
  token subject.
- **Purpose:** Fulfil the named buyer order under the strategic-partner
  arrangement.
- **Tenant definition for this decision:** Partner organization plus buyer
  account, location, product, and contractual tier in Northbridge's
  authoritative commercial-relationship record.
- **Contract owner:** Northbridge product owner for partner inventory
  commitments.
- **Authority owner:** The buyer authority owns delegation for the buyer and
  purpose; Northbridge commercial-policy authority owns the provider-side rule
  for accepting and committing inventory. Neither source replaces the other.

Complete approved statement for a partner request:

> The authenticated partner service principal using the approved partner
> order-integration client may request reservation evaluation for the eligible
> buyer and delivery location on the named inventory-reservation intent in the
> partner, buyer, location, product, and tier tenant boundary for the purpose of
> fulfilling the named buyer order because the active buyer-to-partner
> delegation, registered client authority, and recorded Northbridge commercial
> policy version are valid for the quantity, duration, tier, and current risk
> context.

Separate complete statement for commercial review:

> A named Northbridge commercial reviewer using the approved review client may
> approve or deny an existing `review_required` reservation for its bound buyer,
> object, tenant, and fulfilment purpose because the reviewer's current role,
> case assignment, Northbridge policy version, and the still-valid buyer
> delegation authorize that decision. The reviewer may not broaden the buyer's
> delegation or create a different reservation intent.

### 2. Identity and authority roles

| Role | Identifier/source | Authority it carries | Authority it does not carry | Owner |
| --- | --- | --- | --- | --- |
| Immediate actor | Authenticated partner service-principal ID and attributable representative context when required | Invoke the reservation-request capability through its registered client within delegated scope | Represent any buyer, change tenant, approve `review_required`, or infer authority from authentication alone | Partner identity owner |
| Represented principal | Buyer account authority referenced by the active delegation | Permit the partner to seek the named reservation outcome for the approved purpose and bounds | Grant Northbridge inventory, override provider policy, or authorize another buyer | Buyer delegation authority |
| Subject affected | Buyer account and delivery-location reference in the bound intent | Identifies whose order and location are affected | Authentication, client registration, or delegation by itself | Buyer-account data authority |
| Client/application | Registered partner order-integration client ID | Present the actor and request through an approved channel and capability | Inherit all authority of the partner organization or redelegate it | Partner application owner and Northbridge client registry |
| Consumer organization | Strategic distribution-partner organization ID | Operate the admitted integration and administer registered actors under its agreement | Act for every buyer, location, product, quantity, tier, or purpose | Partner relationship owner |
| Delegating party | Buyer account authority and delegation record | Delegate a bounded reservation-request purpose to the partner | Commit Northbridge inventory or alter Northbridge commercial policy | Buyer delegation authority |
| Provider | Northbridge Exchange partner-inventory capability | Accept responsibility, apply provider policy, and declare the partner-facing outcome | Treat internal service identity as buyer delegation or erase accepted responsibility | Northbridge contract owner |
| Object/resource authority | Northbridge allocation authority and its inventory version | Decide whether the specified inventory effect exists within allocatable capacity | Authorize the caller, change the buyer delegation, or define the public recovery promise | Inventory-allocation owner |
| Tenant authority | Northbridge commercial-relationship and tenant registry | Resolve the admitted partner, buyer, location, product, and tier boundary | Approve the reservation merely because the relationship exists | Commercial-relationship authority |

The token subject, policy subject, event subject, affected buyer, and business
request identity must be recorded in their named fields. No bare `subject`
field is allowed to stand for all of them.

### 3. Delegation chain

| Hop | Delegator/principal | Actor/client | Allowed capability, subject, object, tenant, and purpose | May redelegate? | Starts/expires | Revocation source | Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Buyer account authority | Strategic partner organization | Request reservation evaluation for the named buyer and approved locations, products, quantities, tiers, and fulfilment purpose | Only to a registered partner actor/client under the same or narrower scope; no onward business delegation | Effective and expiry boundaries from the authoritative delegation record | Buyer delegation authority through the partner-relationship system | Delegation ID, version, scope, effective interval, and revocation state |
| 2 | Strategic partner organization acting within hop 1 | Registered order-integration client and authenticated service principal | Invoke the reservation-request operation for the same buyer, object, tenant, and purpose, narrowed by client environment and capability | No | Client registration, credential validity, and the earlier of client or delegation expiry | Partner identity administration and Northbridge client registry | Client ID, actor ID, registration version, credential state, and bound delegation reference |

Hop 1 may narrow buyer-granted authority. Hop 2 narrows it again to an admitted
client and operation. Neither hop may broaden buyer, object, tenant, quantity,
tier, purpose, or time.

Northbridge commercial approval is a parallel provider-authority path, not a
third buyer-delegation hop. An assigned reviewer can advance or deny an existing
`review_required` request only when the buyer delegation still permits the
underlying consequence and provider policy permits the review decision.

### 4. Policy responsibilities

| Responsibility | Accountable role/system | Authority source | Version/evidence | Failure owner |
| --- | --- | --- | --- | --- |
| Policy definition | Northbridge commercial-policy authority with security and contract-owner review | Commercial agreement, approved risk policy, and buyer-delegation requirements | Approved policy ID/version and decision record | Commercial-policy owner |
| Policy administration | Northbridge policy administration | Separation-of-duties and change-control authority | Change identity, approver, effective interval, and deployment record | Policy-platform owner |
| Attribute/information source | Partner-relationship, delegation, tenant, and inventory authorities | Each system's bounded data authority | Source version, observation time, and freshness category | Source-system owner |
| Policy decision | Northbridge policy decision point | Approved policy version over named actor, principal, subject, object, tenant, purpose, and context | Decision ID, category, policy version, input references, and time | Policy-runtime owner |
| Enforcement at API boundary | Partner-inventory capability | Public contract plus current policy decision | Acceptance record linked to decision ID and contract version | Partner-service owner |
| Enforcement at data/effect boundary | Allocation authority | Inventory policy and accepted-request reference | Allocation decision/reference, inventory version, and request identity | Inventory-allocation owner |
| Denial and consumer recovery | Partner-inventory capability and relationship support | Public recovery contract and disclosure policy | Safe denial category, same-intent rule, and escalation reference | Partner-service operations |
| Investigation and dispute | Authorized support investigator; commercial authority for disputed policy decisions | Named support purpose, case assignment, and restricted evidence policy | Case ID, reviewer identity, access decision, evidence references, and outcome | Support and commercial owner |

### 5. Time, caching, and revocation

- **When authority is evaluated:** At the initial request before durable
  acceptance; again before an authorized reviewer advances `review_required`;
  and again before an allocation consequence if a current delegation or policy
  fact may have changed.
- **Facts snapshotted at acceptance:** Actor and client IDs, represented
  principal and affected buyer/location references, tenant boundary,
  delegation ID/version and validity interval, policy decision ID/version,
  purpose, contract version, and intent digest.
- **Facts rechecked before later consequential action:** Delegation revocation
  and expiry, actor/client status where relevant, tenant and commercial
  relationship, review authority, policy version/effectivity, and allocation
  eligibility.
- **Allowed cache lifetime and stale behavior:** The maximum lifetime is the
  shortest approved validity boundary among credential, client registration,
  delegation, policy, and revocation propagation. The exact duration remains an
  open policy decision. Missing, stale, or contradictory consequential facts do
  not silently become permission; the capability limits, denies, or escalates
  according to the approved policy.
- **Revocation authority and propagation path:** The buyer delegation authority
  can revoke buyer-to-partner authority; partner identity administration or the
  Northbridge client registry can revoke the actor/client path; Northbridge
  commercial authority can withdraw provider permission. Each propagates
  through a versioned source to the policy decision and enforcement points.
- **Work accepted before revocation:** Northbridge remains responsible for the
  accepted request and must determine whether an effect already exists. It may
  not erase the record or tell the partner to create a replacement intent.
- **Work not yet consequential at revocation:** No new commitment may be made.
  The request reaches `rejected`, `expired_without_commitment`,
  `unknown_reconciliation`, or `cancelled_after_release` only as the
  authoritative facts warrant; revocation does not invent a ninth state.
- **Compensation, cancellation, or escalation owner:** Partner service
  operations coordinates; inventory allocation owns effect/release facts;
  commercial authority owns the revocation-policy decision; support owns the
  permitted dispute path.

### 6. Authorization-evidence governance

- **Approved purpose for retaining the authority tuple:** Support one accepted
  outcome, reconcile ambiguity, investigate denial or suspected cross-boundary
  action, resolve an authorized dispute, and evaluate approved security or
  policy controls.
- **Minimum representation or protected references:** Opaque actor, client,
  principal, buyer/location, tenant, delegation, policy-decision, accepted-work,
  and outcome references with versions and safe categories. Raw credentials,
  tokens, and request payloads are not required for routine reconstruction.
- **Classification:** Restricted identity, relationship, commercial, policy,
  and outcome evidence; sampled technical diagnostics remain separately
  classified.
- **Roles permitted to read, join, export, or correct it:** Assigned policy,
  security, privacy, support, allocation, and dispute reviewers under a named
  purpose and tenant/case boundary. Export and correction require separate
  authority and retained evidence.
- **Integrity and alteration evidence:** Durable versioned decisions, stable
  cross-references, governed correction descendants, access audit, and
  tamper-evidence appropriate to the approved system design.
- **Retention and disposal rule, including copies:** Retain the minimum tuple
  through approved retry, reconciliation, support, dispute, policy, audit, and
  legal windows; delete or restrict primary, index, cache, export, backup, and
  derived copies under the applicable lifecycle policy.
- **Prohibited raw tokens, credentials, payloads, or policy internals:** Raw
  tokens, proof material, secrets, complete buyer payloads, unrestricted policy
  inputs, stack traces, and unrelated tenant data.
- **What becomes unprovable after disposal:** Historic raw field values,
  detailed technical path, and possibly the full historic authority chain may
  become bounded or unknown. Northbridge must not reconstruct them from an
  unauthorized shadow copy.

### 7. Mutation plan

| Mutation | Expected decision | Effect that must not occur | Public response boundary | Protected evidence | Result |
| --- | --- | --- | --- | --- | --- |
| Valid actor, unauthorized buyer or product | Deny | No acceptance or allocation for the unauthorized object | Bounded `authority_not_established`; do not confirm protected buyer or inventory facts | Actor, principal, object, tenant, policy version, denial category | unrun |
| Valid function, wrong partner/buyer/location tenant | Deny | No cross-tenant read, commitment, or evidence disclosure | Same bounded denial or not-found boundary approved for anti-enumeration | Presented and resolved tenant references, decision, access attempt | unrun |
| Partner tries to approve `review_required` | Deny | Partner cannot advance, deny, or mutate the review decision | Preserve observable status and safe escalation path without exposing reviewer internals | Partner actor, attempted action, request identity, state/version, policy decision | unrun |
| Delegation for replenishment used for a buyer-order purpose | Deny | No purpose substitution or inventory commitment | Bounded authority failure and legitimate delegation path | Delegation purpose, requested purpose, policy version, denial category | unrun |
| Expired or revoked delegation before consequence | Apply approved revocation rule and deny new consequence | No commitment after authority ceased | Existing request identity and owned outcome/reconciliation path remain visible | Revocation source/version/time, recheck, effect evidence, transition | unrun |
| Internal allocation service presents broader service identity | Do not broaden authority | No buyer, object, tenant, or purpose expansion | No internal topology or policy detail disclosed | Original accepted authority context plus service-to-service actor and effect decision | unrun |
| Delegation or tenant attribute source is stale or unavailable | Fail, limit, or escalate as approved; never infer permission | No consequence based on unproved current authority | Safe temporary or owned-pending outcome only if its acceptance meaning is satisfied | Source freshness, availability, cache decision, policy path, owner | unrun |
| Denied caller probes whether a buyer or reservation exists | Deny without prohibited disclosure | No existence confirmation or cross-tenant evidence | Stable bounded response across protected existence cases | Full restricted decision and probe pattern for authorized security review | unrun |

### 8. Decision

- **Approved authority paths:** The two-hop buyer-to-partner-to-client path for
  reservation requests, plus the separate assigned Northbridge reviewer path
  for `review_required`, subject to current provider policy and effect-boundary
  enforcement.
- **Denied paths:** Authentication alone; cross-buyer or cross-tenant use;
  purpose substitution; stale or revoked delegation; unregistered clients;
  partner approval of review; and internal-service authority broadening.
- **Unknown or disputed authority:** Contradictory delegation and tenant facts,
  an unavailable authoritative source beyond its allowed cache interval, or an
  effect begun around revocation remains governed uncertainty, not permission.
- **Evidence gaps:** Cache and revocation timing, cross-system version linkage,
  representative tenant boundaries, and every mutation result are `unrun`.
- **Release blockers:** Any exercised path that commits without both legitimate
  buyer delegation and provider authority, allows partner review approval,
  crosses a tenant, or cannot retain the minimum protected decision evidence.
- **Evidence that would reverse this decision:** Executed negative tests or a
  permitted reconstruction showing authority broadening, prohibited disclosure,
  stale permission, unowned accepted work, or inability to establish the
  consequential decision.

**Authority-map result:** `unrun`

---

## Part B: Contract Evidence Mutation Ledger

### 1. Change and population

- **Contract and current baseline:** The frozen Northbridge
  inventory-reservation contract and its eight governed states. Only
  `committed` authorizes partner reliance on inventory.
- **Provider release candidate:** Proposed addition and handling of
  `review_required` without changing business-request identity, accepted
  responsibility, or partner approval authority.
- **Proposed change:** A reservation may remain accepted while an authorized
  Northbridge commercial reviewer decides whether it may advance. The partner
  may observe and escalate but may not approve the state.
- **Change owner and authority:** Northbridge contract owner with commercial,
  security, operations, and representative-consumer evidence.
- **Consumers represented:** Planned current strategic-partner client fixture
  and its order-advancement journey. Representation remains `unrun`.
- **Consumers not represented:** Dormant client versions, undisclosed strict
  parsers, other partner-specific behavior, and consumers outside the admitted
  capability class.
- **Client versions represented:** Planned current client plus one retained
  prior-version fixture. Execution remains `unrun`.
- **Journeys and recovery paths represented:** Planned request, same-intent
  retry, observation, review wait, overdue escalation, terminal outcome,
  unknown reconciliation, and authority denial. Execution remains `unrun`.
- **Known blind population:** Uninventoried clients, conditions beyond the test
  duration and load, policy rollout across every tenant, and records already
  removed under legitimate retention policy.

### 2. Evidence provenance

| Artifact or evidence layer | Author/source | Derived from | Independent assumption source? | Baseline/version | Owner |
| --- | --- | --- | --- | --- | --- |
| Specification/schema | Northbridge contract-owner proposal | Frozen capability vocabulary and proposed `review_required` representation | partial; shares the contract owner's definitions | Proposed release candidate; result `unrun` | Contract owner |
| Generated client | Planned generator output | Same specification/schema | no | Planned current and retained prior version; result `unrun` | Client-platform owner |
| Provider tests | Planned provider fixtures | Specification examples and provider state model | partial; implementation may share provider assumptions | Proposed release candidate; result `unrun` | Partner-service owner |
| Consumer contract | Planned partner-maintained decision fixture | Partner order behavior and public contract | yes if authored and retained by the partner | Partner baseline not yet executed; result `unrun` | Partner integration owner |
| Authorization tests | Planned security-owned negative matrix | Authority and Delegation Map plus policy rules | partial; separate reviewer but shared policy vocabulary | Proposed policy and provider release; result `unrun` | Security and policy owners |
| Failure/recovery tests | Planned operations-owned fault scenarios | Error-to-Recovery Map and idempotency matrix | partial | Frozen baseline plus proposed review path; result `unrun` | Partner-service operations |
| Integration journey | Planned provider-partner staging exercise | Deployed release candidate, client, and scenario data | yes only if the partner controls its assertions | No retained run; result `unrun` | Joint release owner |
| Production observation | No observation claimed | Future permitted signals and authoritative outcome records | potentially independent but currently absent | Not observed; result `unrun` | Operational owner |

The schema, generated client, and provider fixtures share assumptions. Even if
they later agree, they must not be counted as three independent confirmations.

### 3. Mutation ledger

| Promise dimension | Deliberate mutation | First expected detector | Other layers expected to remain green | Result | First actual detector | Evidence link | Gap or follow-up |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Shape | Add `review_required` while an older generated client accepts only the prior enum | Retained prior-client parse test | Schema validates the new provider response; provider happy-path tests may pass | unrun | unrun | unrun | Add strict and tolerant parser fixtures from represented clients |
| Meaning | Make the partner treat `review_required` as permission to advance the buyer order | Partner-owned business-decision contract test | Schema, generated parsing, and provider transition tests may pass | unrun | unrun | unrun | Require a consumer assertion that only `committed` permits reliance |
| Acceptance/completion | Return `accepted_pending` or `review_required` without durable status discovery and terminal responsibility | End-to-end recovery journey | Schema and isolated handler tests may pass | unrun | unrun | unrun | Prove the same accepted identity reaches a terminal or governed unknown outcome |
| Error/recovery | Tell the partner to create a new intent after `outcome_unknown` | Failure/recovery test after lost allocation response | Schema and happy-path consumer tests may pass | unrun | unrun | unrun | Assert same-identity reconciliation and prohibit replacement solely due to timeout |
| Authorization | Permit the partner actor to approve `review_required` | Security-owned negative authorization test | Response parsing and provider schema checks may pass | unrun | unrun | unrun | Cross actor, client, buyer, object, tenant, purpose, and reviewer assignment |
| Idempotency/concurrency | Accept the same identity with changed quantity or create two commitments during concurrent review completion | Concurrent same-identity and distinct-effect count test | Sequential and schema tests may pass | unrun | unrun | unrun | Count distinct authoritative commitments, not successful handler executions |
| Timing/load/order | Apply commercial approval after expiry or before the accepted review state is authoritative | Time/order transition test | Shape, authorization role, and low-load journeys may pass | unrun | unrun | unrun | Exercise delayed, reordered, repeated, and deadline-bound decisions |
| Observability/support | Sample away the diagnostic trace and also omit the authoritative authority-decision link | Permitted incident-reconstruction test | Schema, provider behavior, and sampled dashboard may appear green | unrun | unrun | unrun | Separate optional sampled traces from mandatory minimum outcome evidence |
| Privacy/lifecycle | Retain raw buyer payload beyond its authorized window or expose evidence across tenants | Retention deletion and access-control test | Functional, compatibility, and recovery tests may pass | unrun | unrun | unrun | Prove deletion/copy behavior and bounded reviewer purpose without weakening reconstruction |
| Consumer population | Remove the retained prior client from the test inventory while declaring all clients compatible | Consumer-inventory and gate-configuration test | Current-client, schema, provider, and integration tests may pass | unrun | unrun | unrun | Treat uninventoried or unexecuted populations as unknown, not compatible |

### 4. Gate behavior

- **Which failed mutations block release automatically:** Undetected or
  surviving defects in authority, tenant separation, identity/effect
  uniqueness, acceptance responsibility, prohibited recovery, privacy access,
  or inability to reconstruct a consequential outcome.
- **Which failures require human review:** Gaps in represented consumer
  population, timing/load bounds, retention-window coverage, disclosure
  wording, and nonauthoritative operational diagnostics.
- **Who may approve an exception:** The contract owner with the accountable
  commercial, security, privacy, operational, and affected-consumer authorities
  required by the gap. No single implementation owner can approve all classes.
- **Required rationale, expiry, and follow-up:** Named promise and population,
  evidence absent, bounded exposure, compensating control, owner, review date,
  expiry, and executable follow-up. No exception has been proposed or run.
- **Evidence retained with the release:** Executed mutation outputs, versions,
  fixtures, represented consumers, decision, exceptions, and links to
  authoritative outcome counts. All remain `unrun`.
- **Production signals that stop expansion:** Partner order advancement from a
  non-`committed` state, partner review approval, duplicate commitment,
  cross-tenant access, unresolved accepted work without owner, or inability to
  reconstruct authority and outcome.
- **Reversal or forward-correction path:** Stop new exposure, preserve status
  and recovery for accepted work, reconcile possible effects, restore the last
  supported consumer behavior or make a governed forward correction, and
  notify affected partners within the approved boundary.

### 5. Bounded decision

> No evidence layer has yet detected a mutation because every mutation and
> representation is `unrun`. The planned portfolio covers the frozen current
> and retained prior partner clients, named journeys, and declared authority,
> recovery, concurrency, timing, evidence, privacy, and population defects. It
> does not exercise dormant or uninventoried clients, production conditions, or
> records legitimately expired under policy. Release evidence is held until the
> required mutations run and retain results. Stop or reverse if a partner can
> act on a non-`committed` state, approve review, create a second commitment,
> cross a tenant, or lose the minimum authority/outcome evidence.

**Mutation-ledger result:** `unrun`

---

## Part C: Outcome Evidence Map

### 1. Evidence question

- **Capability and contract baseline:** The frozen Northbridge
  inventory-reservation capability, eight governed states, authority map, and
  same-intent recovery rule.
- **Claim an authorized reviewer must support:** For one named business intent,
  did Northbridge accept responsibility under legitimate authority, did an
  allocation effect occur, what authoritative partner-facing outcome followed,
  and what can no longer be known?
- **Consumer decision affected:** Whether the partner may rely on committed
  inventory, must wait or reconcile the same identity, may correct a genuinely
  new intent, must obtain authority, or must stop.
- **Business request identity:** `partnerReservationRequestId` within the bound
  partner, buyer, location, product, quantity, purpose, duration, and tier.
- **Accepted-work identity:** `northbridgeReservationRequestId`.
- **External effect reference:** Allocation-authority
  `allocationReference`, when one is assigned.
- **Authoritative outcome identity and version:** Northbridge
  `reservationCommitmentId` and reservation-record version, when a commitment
  exists; otherwise the accepted-work identity and terminal or
  `unknown_reconciliation` state version.
- **Reviewer and permitted purpose:** Assigned Northbridge support investigator,
  commercial reviewer, security investigator, privacy reviewer, or dispute
  reviewer, limited to the named case and approved purpose. Partner visibility
  remains the public contract view.
- **Operational owner:** Partner service operations, with allocation,
  commercial, policy, security, or privacy owners accountable for their
  authoritative parts.

### 2. Evidence chain

| Decision or transition | Authoritative source | Stable link | Public/consumer view | Operational view | Restricted evidence | What this record cannot prove |
| --- | --- | --- | --- | --- | --- | --- |
| Intent received | Northbridge request/acceptance store | Bound business identity plus request digest | Correlation or `received_unaccepted` only when disclosure permits | Receipt time, contract version, validation category | Permitted actor, principal, subject, tenant, purpose, and normalized intent references | Receipt alone cannot prove authority, durable acceptance, allocation, or commitment |
| Authority decision | Northbridge policy decision record linked to authoritative delegation and tenant versions | Policy decision ID and delegation/tenant references | Bounded allowed/denied category and safe recovery path | Decision time, version, freshness, and enforcement point | Full decision inputs, policy rule/category, revocation and source versions | A policy decision alone cannot prove enforcement at the effect boundary or business completion |
| Responsibility accepted or rejected | Northbridge reservation acceptance record | `northbridgeReservationRequestId` plus business identity | Accepted state and status path, or bounded nonacceptance | Durable state, owner, deadline, idempotency disposition, outbox intent | Transaction evidence and protected authority linkage | Acceptance cannot prove that allocation committed or that a response reached the partner |
| Attempt or external effect | Allocation authority | `allocationReference` plus accepted-work identity | No raw dependency detail; committed facts only after Northbridge's authoritative declaration | Attempt category, observation, reconciliation status | Allocation decision, inventory version, quantity, effect time, and release evidence | An attempt cannot prove a distinct effect; an effect record cannot prove consumer notification |
| State transition | Northbridge reservation state store | Accepted-work identity and monotonic state version | Permitted current state, last-change time, next action, and deadline | Prior/current state, decision owner, transition cause/reference | Reviewer assignment, authority recheck, internal causal links | A transition cannot prove its cause unless the authoritative decision/effect link survives |
| Business outcome or unknown state | Northbridge reservation commitment record reconciled with allocation authority | Commitment ID/version or accepted-work identity/state version | `committed`, `rejected`, `expired_without_commitment`, `cancelled_after_release`, or `unknown_reconciliation` with safe recovery | Outcome, owner, effect linkage, expiry/release, unresolved work | Allocation evidence, authority lineage, reconciliation and correction history | The public status alone cannot prove every internal attempt or unrestricted policy detail |
| Consumer-visible response/recovery | Partner API response/status-access record | Accepted-work identity, response version, and permitted correlation | Current outcome, same-identity action, status path, and escalation route | Delivery attempt, retrieval time, client/version when permitted | Network and disclosure-decision detail | Delivery attempt cannot prove human understanding or downstream partner action |
| Escalation or dispute resolution | Authorized case-management and authoritative source correction records | Case ID linked to accepted-work identity and evidence references | Permitted resolution and next action | Assigned owner, evidence reviewed, decision, correction/reversal | Reviewer identity, access basis, protected findings, affected records | A case note cannot override an authoritative outcome without a governed correction and versioned link |

### 3. Governance per evidence field

| Field/reference | Purpose | Classification | Access roles | Integrity need | Retention | Deletion/copies | Failure-survival boundary |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Business identity and normalized intent digest | Bind retries and detect changed intent without routinely retaining a raw payload | Confidential and linkable | Partner service, authorized support, limited dispute/privacy review | Atomic acceptance, collision-resistant digest, canonicalization/version record | Retry, reconciliation, dispute, and evidence window; exact duration requires approval | Delete raw transient copies; inventory digest replicas and backups; digest remains classified | Must survive accepted work and ambiguity window; after legitimate expiry Northbridge must not claim field-level reconstruction |
| Actor, client, represented principal, affected buyer/location, and tenant references | Prove who acted, for whom, through which client, and inside which tenant | Restricted identity and relationship data | Policy, security, assigned support/dispute roles under named purpose | Stable source references, versions, decision link, and access audit | Approved authority, security, dispute, and legal window; no indefinite retention by default | Govern indexes, exports, caches, backups, and derived joins; deletion follows source and evidence obligations | Minimum decision linkage must survive the consequence and dispute window; diagnostic copies need not |
| Delegation and policy decision IDs/versions | Establish the authority used at acceptance and later consequence | Restricted policy and commercial evidence | Policy/commercial authority, security, assigned dispute reviewer | Tamper-evident decision/version linkage and source freshness | Approved policy-evidence and dispute window | Retain governed references/categories where sufficient; remove unauthorized raw attributes and copies | If required historic policy/delegation evidence expires, later authority claims may become bounded or unknown |
| Accepted-work identity, state, owner, and deadline | Prove responsibility and support same-intent recovery | Confidential operational/business record | Partner through bounded view; provider operations and assigned reviewers internally | Durable atomic record, monotonic version, recovery replication | At least accepted-work, retry, reconciliation, and dispute window | Delete obsolete diagnostic duplicates; preserve governed state history per policy | Must survive worker, queue, and response failures after acceptance |
| Allocation reference and commitment/version | Distinguish attempts from an authoritative inventory effect and outcome | Restricted commercial and inventory evidence | Allocation authority, partner service, assigned support/dispute roles | Unique stable reference, authoritative version, reconciliation and release links | Commitment lifecycle plus approved reconciliation and dispute window | Govern replicas, exports, caches, and backups; expose only permitted commitment facts | Must survive response loss and provider restart while effect can remain active or disputed |
| Public response/status record | Show what safe state and recovery path the partner could retrieve | Confidential partner-contract data | Named partner tenant and provider support | Contract version, response version, time, and accepted-work link | Support and dispute window, subject to approved minimization | Delete incidental logs and unrestricted copies; retain minimum governed response evidence | Helpful for disclosure disputes but cannot replace authoritative authority/effect records |
| Sampled diagnostic trace | Diagnose latency and technical path; never decide whether authority or an effect existed | Restricted operational telemetry; potentially linkable | Need-to-know reliability/security roles for a named purpose | Sampling flag, trace provenance, access audit, and no claim of completeness | Short-lived approved diagnostic window | Delete on schedule from indexes, exports, caches, and backups where policy requires | May be missing by design. Its absence must not erase accepted responsibility or prove no effect |
| Investigation case and access audit | Govern exceptional reconstruction, dispute, and correction | Restricted case, identity, and relationship data | Assigned reviewer and oversight roles only | Case identity, purpose, accesses, evidence references, decision and correction links | Approved case, audit, and legal window | Control exports and AI summaries; delete or restrict copies at case closure per policy | Survives long enough to prove the governed review, not as a shadow copy of all raw evidence |

Hashing or digesting does not make a buyer, relationship, request, or purpose
anonymous. Linkable references remain classified and access-controlled.

### 4. Reconstruction cases

| Case | Evidence that must survive | Permitted reviewer | Expected bounded conclusion | Result | Missing or contradictory evidence |
| --- | --- | --- | --- | --- | --- |
| Committed outcome | Bound intent, authority decision, acceptance, allocation effect, commitment/version, and current expiry/release state | Assigned support or dispute reviewer; partner sees bounded outcome | One named authorized intent produced the authoritative active commitment under its stated terms | unrun | Missing allocation or authority link prevents an unqualified commitment/authority claim and requires governed investigation |
| Denied request | Receipt, presented/resolved boundary, policy decision/category, nonacceptance proof, and safe public response | Assigned support, policy, security, or dispute reviewer | Northbridge did not accept the request and the bounded authority or validation category explains the permitted recovery path | unrun | Missing nonacceptance evidence means the reviewer cannot infer that no later responsibility/effect existed |
| Duplicate or concurrent intent | Atomic identity claim, intent digest, attempt records, accepted-work identity, allocation references, and distinct commitment count | Assigned support or reliability reviewer | Repetition converged on one governed intent and no more than one active commitment | unrun | Handler counts or repeated responses without authoritative effect counting are insufficient |
| Timeout before acceptance | Receipt/attempt, acceptance-boundary record, idempotency lookup, and absence of accepted/effect references within authoritative stores | Assigned support reviewer | Northbridge can state nonacceptance only if the acceptance and effect boundaries prove it; otherwise the result is unknown | unrun | A network timeout or missing trace cannot prove nonacceptance |
| Timeout after possible effect | Acceptance, allocation attempt/reference, observations, current state, reconciliation actions, and owner | Assigned support, allocation, or dispute reviewer | Same identity remains provider-owned; report `unknown_reconciliation` until effect is established | unrun | Missing effect linkage forbids both “committed” and “no effect” certainty |
| Revoked authority | Original delegation/policy versions, revocation source/time, recheck, acceptance/effect times, and governed transition | Commercial/policy/security reviewer with assigned case | Determine whether authority existed at each consequential boundary and whether an effect preceded revocation; preserve accepted responsibility | unrun | Clock, version, or effect disagreement makes the temporal authority conclusion bounded or unknown |
| Consumer affected by change | Contract versions, represented client/version, response/state, consumer decision assertion, notice/migration evidence | Contract owner and authorized partner representative | State only whether the represented, exercised consumer behavior remained safe under the change | unrun | Uninventoried or unexecuted clients remain unknown even when schema is valid |
| Unknown outcome | Acceptance, attempts, external references, conflicting/missing observations, reconciliation owner, deadline, and last governed state | Assigned support/allocation/dispute reviewer | The effect cannot yet be proved; preserve `unknown_reconciliation`, same-identity recovery, and escalation | unrun | Missing evidence is recorded as the reason for uncertainty, not filled with a likely story |
| Sampled diagnostic trace absent | Authoritative acceptance, authority, allocation, state, and outcome records; sampling configuration and deletion evidence where relevant | Assigned support or reliability reviewer | Trace absence is expected under sampling and says nothing by itself about acceptance or effect; authoritative records govern | unrun | If an authoritative record is also missing, the affected claim becomes unknown rather than being inferred from trace absence |
| Authoritative evidence expired under approved privacy/retention policy | Retention policy/version, deletion event, surviving permitted outcome category, access audit, and any legal/dispute hold | Privacy owner plus assigned dispute or contract reviewer | State what the surviving governed record supports and what Northbridge can no longer prove; do not recreate raw buyer detail from unauthorized copies | unrun | Expired intent, policy, or effect linkage may make historic field-level, authority, or causality claims permanently bounded or unknown |

### 5. Absence and disclosure tests

- **Record removed or delayed:** Remove the sampled diagnostic trace, delay an
  allocation observation, and separately simulate a missing authoritative
  authority-decision link. Each reconstruction result remains `unrun`.
- **Claim that must become unknown:** Whether legitimate authority existed at
  the consequential boundary, whether an external effect exists, or whether a
  represented consumer stayed safe when the required authoritative link is
  absent or contradictory.
- **Unsafe inference the system must refuse:** “No trace means no effect,” “the
  policy engine probably allowed it,” “the handler succeeded so the commitment
  exists,” or “the schema parsed so the consumer behaved safely.”
- **Cross-tenant or unauthorized query attempted:** A valid partner actor asks
  for another partner's buyer, reservation, authority decision, or support
  case. The provider denies the query without confirming protected existence
  and records a restricted access decision. Result: `unrun`.
- **Join or export that could reveal protected relationships:** Joining actor,
  buyer, location, delegation, commercial tier, policy reason, and reservation
  history can reveal buyer relationships and business priorities. Bulk export
  is denied unless a named authority, purpose, scope, minimization rule,
  destination, retention, and review exist. Result: `unrun`.
- **AI retrieval or summary boundary:** An AI assistant may retrieve only the
  permitted fields for the assigned case and reviewer purpose. It may not read
  unrestricted payloads, cross-tenant history, or removed diagnostic copies;
  it must preserve source references and state uncertainty. Result: `unrun`.
- **Emergency access and review rule:** Break-glass access requires an approved
  emergency category, named reviewer, minimum scope, time-bound access,
  immutable access audit, and retrospective privacy/security review. It does
  not authorize export or indefinite retention. Result: `unrun`.

### 6. Retention decision

- **Retry and ambiguity window:** Business identity, acceptance, and effect
  linkage must outlast the approved same-intent retry and reconciliation
  window. Exact duration remains an accountable policy decision.
- **Support and dispute window:** Retain the minimum outcome, authority,
  response, and correction references needed for the approved support and
  contractual dispute period; do not keep raw buyer payloads merely because
  they might make debugging easier.
- **Security/policy evidence window:** Retain versioned decisions and minimum
  identity/authority linkage for the approved security, policy, audit, and
  legal need. Purpose and access remain bounded throughout retention.
- **Compatibility and deprecation window:** Retain the represented client,
  contract version, mutation evidence, notice, and bounded decision through the
  supported migration and deprecation period.
- **Short-lived diagnostics:** Sampled traces and detailed technical logs have a
  separately approved short lifetime and are not authoritative outcome records.
  Their deletion cannot erase accepted responsibility.
- **What the provider can no longer prove after expiry:** Once legitimately
  deleted evidence and all governed copies are gone, Northbridge may be unable
  to prove raw field values, a historic rule input, a detailed technical path,
  or sometimes a full historic authority/causality chain. It must disclose that
  boundary rather than recover data from an unauthorized shadow copy or claim
  certainty.

### 7. Release decision

- **Claims reconstructable with permitted evidence:** Planned reconstruction
  covers receipt, authority, acceptance, distinct effect, governed state,
  consumer recovery, and dispute for a named identity. Result: `unrun`.
- **Claims still unknown:** Whether the proposed records actually survive the
  named failures, whether access/deletion controls work, and whether every
  represented reviewer can reconstruct the bounded claim. Result: `unrun`.
- **Evidence overcollection or access risk:** Raw payload retention, linkable
  digests, cross-system joins, exports, AI summaries, backup copies, and
  break-glass access require explicit controls. Result: `unrun`.
- **Failure-survival gap:** Sampling, cross-system retention mismatch, deletion,
  source unavailability, or missing version links may break the chain. Result:
  `unrun`.
- **Hold, revise, or release:** Hold the evidence claim. The tool application is
  coherent, but no reconstruction, access, deletion, or failure-survival result
  has been earned.
- **Evidence that would reverse the decision:** Retained executed results for
  positive and negative cases, including missing sampled trace, missing
  authoritative record, cross-tenant denial, retention deletion, response loss,
  revocation, duplication, and unknown outcome.

**Outcome-map result:** `unrun`

## What this completed example establishes

It establishes only that the three blank tools can be filled coherently against
the frozen Northbridge scenario while preserving:

- the exact eight-state vocabulary;
- separate actor, represented principal, affected subject, client, consumer,
  tenant, delegation, provider, reviewer, and object-authority roles;
- separate request, accepted-work, external-effect, and authoritative-outcome
  identities;
- a mutation portfolio with named blind populations;
- a minimum permitted evidence chain rather than unrestricted telemetry;
- missing sampled evidence as a designed case, not proof of no effect; and
- privacy and retention as counterconditions on reconstruction, not reasons to
  keep everything forever.

## What it does not establish

It does not establish that:

- any authority decision, enforcement point, or revocation path is correct;
- any mutation is detected by its expected layer;
- any implementation prevents duplicate commitments or cross-tenant access;
- an authorized reviewer can actually reconstruct an outcome;
- the proposed fields, access roles, or retention boundaries are sufficient;
- independent practitioners can use the tools without chapter context; or
- using the tools improves security, compatibility, reliability, delivery, or
  business outcomes.

Every such result remains `unrun` until an executable exercise or permitted
retained observation produces evidence.
