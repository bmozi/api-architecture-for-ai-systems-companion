# API Companion Usability Test 01

## Test status and evidence boundary

- **Date:** 2026-08-28
- **Assets tested:** `api-meaning-and-authority-brief.md` and
  `api-event-workflow-decision-tree.md`
- **Method:** AI-assisted desk application to a frozen constructed scenario
- **Evidence classification:** Scenario and proposed design decisions

This is not a Northbridge Exchange case, an empirical case study, a record of
John Briggs's experience, or a transcript of an actual design review. The
organizations, vendors, people, identifiers, deadlines, and behavior below are
invented for this test. The exercise tests whether the companion prompts expose
important decisions. It does not prove that the resulting architecture is
correct, legally compliant, secure, operationally ready, or usable by an
independent practitioner.

No external standards, regulations, vendor documentation, production systems,
or measured outcomes were evaluated. All response times, states, and authority
rules are proposed scenario inputs rather than reported facts.

## Constructed design-review scenario

Harborline Home Goods, a fictional retailer, sells through a fictional
marketplace partner called MarketSquare. MarketSquare wants one operation that
its service agents can call to “approve a refund.” Harborline uses two fictional
vendors behind the capability:

- OrbitReturns receives carrier scans and return-inspection decisions; and
- ClearLedger Payments submits money movements and reports settlement.

The apparently simple request hides several different outcomes. Harborline can
accept responsibility for evaluating a request before it knows whether a return
is eligible. It can authorize a refund before ClearLedger submits it. A payment
can be submitted before settlement is known. A dependency timeout can also
leave the monetary outcome unknown.

The design review must decide what Harborline promises directly, what it merely
reports from a vendor, and who remains responsible while carrier evidence,
manual judgment, or settlement is pending.

### Frozen scenario assumptions

These assumptions make the desk test repeatable. They are not claims about a
real retailer or vendor.

1. MarketSquare has a seller-specific integration agreement with Harborline.
2. A MarketSquare service agent acts through a MarketSquare service principal
   and may act only for orders sold through its Harborline seller account.
3. Some requests can be rejected immediately from authoritative order and
   refund state. Others require carrier evidence, inspection, or human review.
4. Harborline remains accountable to MarketSquare for the contract even when
   OrbitReturns or ClearLedger performs a downstream step.
5. A refund is not described as settled until Harborline has reconciled a
   ClearLedger settlement reference to the refund request.
6. The proposed API acceptance response boundary is two seconds. That is a
   design target for the scenario, not a measured service level.
7. The same `refund_request_id` is carried by the API record, durable workflow,
   event facts, downstream attempt records, and operational trace.
8. Harborline's refund outcome ledger is the authoritative consumer-facing
   record. Vendor messages are provenance-bearing inputs, not the public
   contract by themselves.

### Deliberately unresolved inputs

The test does not invent answers for these questions:

- whether ClearLedger provides a stable idempotency guarantee after an
  ambiguous timeout;
- whether OrbitReturns callbacks have adequate authenticity and replay
  protection;
- which refund deadlines apply by product, jurisdiction, and sales agreement;
- which party owns customer communication during each pending state;
- which reason details may be exposed without revealing restricted fraud or
  personnel information; and
- whether MarketSquare can consume a status callback reliably or requires
  polling as the guaranteed recovery path.

These unknowns remain release blockers or explicit contract decisions in the
completed brief.

## Completed API Meaning-and-Authority Brief

### 1. Capability promise

- **Capability name:** Request and track a Harborline marketplace refund.
- **Business outcome the consumer needs:** MarketSquare can submit one refund
  intent for an eligible order line, learn whether Harborline assumed
  responsibility for evaluating it, and discover a defensible terminal outcome
  without causing a second monetary outcome during retry or recovery.
- **Why an API is the right interaction:** MarketSquare deliberately invokes a
  governed capability for a named order, needs an immediate response that it
  can safely act on, and needs a queryable status contract when work continues.
- **What this contract does not promise:** Immediate refund approval, immediate
  settlement, acceptance of MarketSquare's requested amount, carrier or vendor
  availability, exposure of internal fraud reasoning, or successful customer
  communication by MarketSquare.

### 2. Parties and authority

- **Consumer:** MarketSquare refund-integration service.
- **Provider accountable for the capability promise:** Harborline Home Goods.
  Its refund capability carries the public promise; OrbitReturns and
  ClearLedger are dependencies, not substitute contract owners.
- **Actor performing the immediate action:** An authenticated MarketSquare
  service identity carrying the service agent's attributable action context.
- **Client presenting or transporting the request:** MarketSquare's registered
  refund-integration application.
- **Principal whose authority is represented:** The MarketSquare seller account
  operating under the active seller agreement.
- **Delegate authorized to act for that principal:** The registered integration
  service and attributable service agent within the agreement's bounded scope.
- **Affected subject or business party:** The customer associated with the
  eligible Harborline order.
- **Protected object or resource acted upon:** The Harborline order line and its
  remaining refundable amount.
- **Tenant, organization, or account boundary:** The MarketSquare seller
  account, Harborline merchant account, order, and currency boundary encoded in
  Harborline's authoritative order record.
- **Authority required to request the capability:** The integration agreement
  permits the MarketSquare principal to request refunds for its own fulfilled
  Harborline order lines, within the permitted reason and amount boundary. It
  does not permit MarketSquare to declare approval or settlement.
- **System or role authoritative for granting that authority:** Harborline's
  partner-integration registry and policy service, under the seller agreement
  owner and security authority.
- **Contract owner:** Harborline product owner for the marketplace-refund
  capability.
- **Change authority:** The contract owner, with required security, payments,
  operations, and partner-compatibility evidence before release.
- **Operational owner:** Harborline returns-and-payments operations, with named
  escalation paths to the integration and payment-service owners.

### 3. Meaning and outcomes

- **Preconditions:** The seller account and principal are active; the order line
  exists in that account; currency and requested amount are valid; the order
  line has not already exhausted its refundable amount; the request includes a
  unique idempotency key; and the requested action is within the principal's
  policy scope.
- **A request is accepted when (state the business condition, not only the
  transport response):** Harborline has authenticated and authorized the
  request, validated its stable business identity, atomically stored the refund
  intent and idempotency result, assigned a `refund_request_id`, and assumed
  responsibility for reaching and reporting a terminal outcome. `202` is the
  representation of that decision, not its definition.
- **The business outcome is complete when (include every terminal outcome):**
  The authoritative refund outcome ledger records one of the disclosed terminal
  states: `settled`, `rejected`, or `cancelled_after_compensation`. A submitted
  payment, a vendor callback, or an HTTP response alone is not completion.
- **Authoritative outcome record:** Harborline's refund outcome ledger, linked
  to the order line, original refund intent, authorization decision, downstream
  attempt, settlement or rejection evidence, and compensation where applicable.
- **Information returned to the consumer:** `refund_request_id`, idempotency
  disposition, current state, requested and authorized amount and currency when
  known, stable reason or next-action code, status URL, last-change time, and
  whether MarketSquare must supply evidence or wait.
- **Information intentionally not exposed:** Fraud score or rules, employee
  notes, vendor credentials, unrelated customer or tenant data, raw internal
  exceptions, and restricted payment details.
- **Invariants that must remain true:** Cumulative refunds do not exceed the
  authoritative refundable amount; one refund intent cannot create two monetary
  outcomes; the actor cannot cross the seller-account or order boundary; a state
  never claims settlement before reconciliation evidence exists; every state
  transition is attributable; and vendor failure does not silently transfer
  completion responsibility to MarketSquare.

### 4. Repetition, conflict, and time

- **What may safely repeat:** Status retrieval may repeat. A refund request with
  the same idempotency key and the same normalized business intent returns the
  original `refund_request_id` and current outcome without creating another
  refund. Callbacks and internal processing steps may repeat only where their
  handlers preserve the same business outcome.
- **Business idempotency key or identity:** MarketSquare seller account plus
  order line plus MarketSquare refund-intent identifier. Harborline maps that
  identity to one `refund_request_id`; the raw HTTP request ID is diagnostic,
  not the business identity.
- **Concurrency or stale-state rule:** Harborline evaluates requested and prior
  refunded amounts against an authoritative order-line version. Concurrent
  requests that would exceed the refundable amount conflict; they are not
  independently accepted from stale reads.
- **Transaction boundary:** Acceptance atomically records the refund intent,
  idempotency mapping, initial status, order-state version used, and an
  outbox-style durable work record in the same transactional store. Dispatch
  into an external workflow or broker, carrier validation, human review,
  payment submission, settlement, notification, and compensation occur outside
  that transaction and require retry and reconciliation; they must not be
  represented as already complete.
- **Expected response-time boundary:** Within the scenario's proposed two-second
  boundary, return a terminal rejection when it is authoritative and safe to do
  so; otherwise return accepted responsibility with the identifier and status
  path. The final monetary outcome has no invented synchronous deadline.
- **When work continues after the response:** When carrier or inspection
  evidence is missing, manual review is required, the processor has not reported
  a definitive result, compensation is pending, or customer communication has
  not reached its separately defined state.
- **How the consumer discovers final outcome:** A `GET` on the status URL is the
  proposed recovery-capable source. An authenticated callback or subscribed
  fact may reduce polling but does not replace the query path until its delivery
  and recovery promise is established.

### 5. Failure contract

| Failure class | Meaning to consumer | Safe consumer action | Evidence retained |
| --- | --- | --- | --- |
| Invalid request | The request cannot identify a valid refund intent under the contract; Harborline did not assume responsibility. | Correct the identified field or business identity; reuse the intent identity only according to the documented correction rule. | Validation reason, contract version, normalized request digest, correlation ID, and decision time. |
| Not authorized | The principal may be known but cannot request this refund for this seller account, order, amount, or reason. No refund work began. | Stop; obtain legitimate authority or escalate through the agreement owner. Do not change identifiers to probe other accounts. | Principal, subject boundary, policy decision and version, denial category, and correlation ID without prohibited policy detail. |
| Conflict or stale state | Authoritative refundable state changed or another intent competes for the same refundable amount. The requested outcome was not accepted as new work. | Retrieve current order/refund state and decide whether a new business intent is legitimate. Do not blind-retry. | Compared version, current version, competing refund identifiers where disclosure is allowed, and decision record. |
| Dependency or transient failure | Harborline could not establish safe acceptance or a known downstream result within the response boundary. | If no `refund_request_id` exists, retry with the same business idempotency key. If one exists, query it; do not create a new refund identity. | Idempotency lookup, dependency attempt ID, sanitized failure class, timestamps, retry decision, and trace linkage. |
| Accepted but incomplete | Harborline owns completion, but evidence, review, submission, settlement, or compensation is still pending. | Query the same status; supply only requested evidence; follow the disclosed escalation path after its deadline. | Current durable state, entry time, next owner, deadline, attempts, evidence references, and last transition. |
| Terminal business rejection | Harborline completed evaluation and will not issue the requested refund under the authoritative policy and evidence. | Show the stable reason and available appeal or correction path; do not retry the same intent as if it were new. | Policy and evidence versions, attributable decision, reason category, appeal availability, and notification record. |
| Unknown outcome | A monetary attempt may have taken effect, but Harborline cannot yet prove success or failure. | Query and escalate the same `refund_request_id`; never submit a replacement refund merely because a timeout occurred. | Attempt identity, request digest, send/receive times, processor references, reconciliation state, operator actions, and eventual resolution. |

### 6. Compatibility promise

- **Consumers or consumer classes:** MarketSquare's current integration and any
  future marketplace integration admitted to the same capability class.
- **Behavior they may rely on:** Stable distinction among not accepted,
  accepted responsibility, pending progress, and terminal outcomes; same-intent
  retry returns the original business outcome; status retrieval remains
  available for accepted work; and error classes prescribe safe recovery.
- **Semantic assumptions that must remain stable:** `accepted` does not mean
  approved, `authorized` does not mean submitted, `submitted` does not mean
  settled, and `unknown` does not mean failed.
- **Timing, ordering, or volume assumptions:** Only the proposed acceptance
  response boundary is fixed in this scenario. Consumers must use state version
  and refund identity rather than callback arrival order. Volume and callback
  delivery assumptions remain undecided and therefore cannot be promised.
- **Authorization assumptions:** The MarketSquare principal can act only within
  its seller-account, order, amount, and reason scope. Adding a credential or
  authenticating successfully cannot broaden that delegated authority.
- **Deprecation and migration promise:** A changed state meaning, idempotency
  rule, authority boundary, or required consumer action needs explicit migration
  evidence and notice. A schema-valid enum addition is not assumed safe for
  MarketSquare without representative consumer evidence.
- **Exit or reversal path:** Harborline can disable new refund requests for the
  partner while preserving status and recovery for accepted work; MarketSquare
  can return to its existing manual request path for new work. Accepted refund
  responsibilities cannot be abandoned by disabling the endpoint.

### 7. Evidence floor

- **Contract/schema evidence:** The specification represents the decided state
  vocabulary, error classes, authority inputs, idempotency behavior, status
  query, and examples without claiming that schema validation proves semantics.
- **Behavioral evidence:** State-model tests cover every allowed and prohibited
  transition, including rejection, compensation, and resolution from unknown.
- **Authorization evidence:** Positive and negative cases vary seller account,
  order, amount, reason, principal, and revoked agreement. Cross-account and
  stale-authority requests fail without starting work.
- **Idempotency/concurrency evidence:** Simultaneous same-intent requests,
  same-key/different-intent requests, stale refundable amounts, ambiguous
  processor timeouts, callback duplication, and restart recovery create at most
  one monetary outcome.
- **Representative consumer evidence:** MarketSquare's parser, state handling,
  same-intent retry, unknown-outcome recovery, and new-enum behavior run against
  representative provider behavior, not only schema fixtures.
- **Failure and recovery evidence:** Dependency delay, callback loss and replay,
  operator pause, manual denial, payment submission timeout, reconciliation,
  compensation, and service restart are exercised with retained outcomes.
- **Operational observability evidence:** One refund identity reconstructs API
  acceptance, durable state, vendor inputs, processor attempts, event facts,
  consumer retrieval, operator action, and terminal outcome without exposing
  prohibited data.
- **Unknowns that block implementation or release:** The six deliberately
  unresolved inputs above, plus any failure case in which Harborline cannot
  retain responsibility, reconcile a monetary outcome, or tell MarketSquare a
  safe next action.

### Design-review answer

If the generated code disappeared, this brief would still identify the
capability, the provider accountable for it, the authority boundary, the
meaning of acceptance and completion, the one-outcome invariant, safe recovery,
and the proposed evidence floor. It would not replace the missing vendor,
security, legal, consumer, or runtime evidence.

## Completed API, Event, or Workflow Decision Tree

### 1. What another party needs

#### Capability deliberately invoked: API

MarketSquare needs to request and track a refund under delegated authority. The
primary consumer boundary is therefore an API.

- **Who may invoke it and for whom?** An authorized MarketSquare principal may
  request for a customer order line within its own seller account and policy
  scope.
- **What outcome is promised by the response?** A rejection means Harborline
  did not accept new work. An acceptance means Harborline durably recorded the
  intent and owns reaching and reporting a terminal outcome. It does not mean
  approval or settlement.
- **What happens if the request repeats or conflicts?** The same business intent
  resolves to the same refund request and outcome. A changed request under the
  same key conflicts. Competing refund intents are checked against authoritative
  refundable state.
- **Which failures can the consumer safely act on?** The failure contract above
  distinguishes correct-and-retry, stop, refresh-and-decide, query-existing,
  supply-evidence, appeal, and escalate-without-reissuing.

#### Facts independently reacted to: events

Events distribute facts after an authorized state decision. They do not carry
Harborline's responsibility for finishing the refund.

| Proposed fact | Authority to declare | Meaning | Does not mean |
| --- | --- | --- | --- |
| `RefundRequestAccepted` | Harborline refund capability | Harborline durably assumed responsibility for this refund intent. | Approved, submitted, or settled. |
| `ReturnEvidenceRecorded` | Harborline after validating a provenance-bearing OrbitReturns input | Named evidence is attached to the refund request. | The evidence is sufficient or the refund is approved. |
| `RefundAuthorized` | Harborline refund policy or named human authority | Harborline approved a bounded amount for payment submission. | ClearLedger accepted or settled it. |
| `RefundRejected` | Harborline refund policy or named human authority | Evaluation reached a terminal rejection under recorded policy and evidence. | Every possible appeal has been exhausted unless the contract says so. |
| `RefundPaymentSubmitted` | Harborline after reconciling a ClearLedger submission reference | A named monetary attempt was submitted. | Customer funds settled. |
| `RefundSettled` | Harborline after reconciling ClearLedger settlement evidence | The refund outcome ledger records a settled monetary outcome. | Customer communication was delivered. |
| `RefundOutcomeUnknown` | Harborline refund capability | Harborline cannot yet prove whether a named monetary attempt succeeded. | Failed; safe to submit another refund. |

Every fact carries the refund business identity, causation reference, source
provenance, and state version. Duplication, late arrival, replay, traffic growth,
and reaction authority still require event-specific design and evidence outside
this API desk test.

#### Promise surviving time and failure: durable workflow

The refund process requires durable responsibility because it can wait for
carrier evidence, vendor callbacks, manual judgment, payment reconciliation,
deadlines, and compensation.

- **Who owns completion?** Harborline's refund capability owner owns the
  customer-facing terminal outcome; operations owns exceptions under that
  contract. A vendor timeout does not transfer ownership to MarketSquare.
- **What durable state represents progress?** One versioned workflow instance
  linked to `refund_request_id`, with states for evidence, evaluation,
  authorization, submission, unknown reconciliation, settlement, rejection,
  compensation, and terminal notification obligations.
- **What is compensated when rollback is impossible?** A duplicate or excess
  monetary outcome requires a recorded compensating credit/debit decision and
  human escalation rather than pretending the original external action rolled
  back. Exact compensation rules remain a workflow and payments decision.
- **Where must human judgment advance, pause, or stop work?** Policy exceptions,
  disputed evidence, high-risk amounts, ambiguous processor results beyond the
  recovery deadline, and compensation approval. The authority and deadline for
  each pause must be explicit before release.

### 2. Explicit composition

1. MarketSquare invokes the API to request one refund intent.
2. Harborline returns a terminal non-acceptance or an accepted
   `refund_request_id` and query path.
3. A durable workflow preserves Harborline's responsibility across evidence,
   review, vendor calls, monetary ambiguity, compensation, and time.
4. Events declare authorized state facts for independent reactions such as
   partner updates, finance reconciliation, and service notifications.
5. The shared `refund_request_id` and refund outcome ledger reconcile API,
   workflow, event, vendor, and operational views.

This is not labeled merely “API-first” or “event-driven.” Each mechanism has a
different promise and evidence obligation.

### 3. Final check

- **Capability promised by API:** Request one refund intent under delegated
  authority, receive an unambiguous acceptance decision, and retrieve its
  current and terminal outcome.
- **Facts declared by events:** Accepted responsibility, evidence recorded,
  authorization, rejection, payment submission, settlement, and unknown
  outcome, each under its named declarer and meaning.
- **Responsibility preserved by workflow:** Harborline remains responsible from
  accepted intent through evidence, judgment, dependency ambiguity,
  compensation, and terminal outcome.
- **Authoritative owner for each:** Harborline owns the API contract and public
  outcome; named policy or human authorities own authorization and rejection;
  the workflow owner owns progress and recovery; Harborline declares public
  facts only after reconciling evidence from the appropriate vendor authority.
- **Business identity carried across the mechanisms:** `refund_request_id`,
  mapped to the immutable MarketSquare seller account, order line, and refund
  intent identity.
- **How the requester discovers current and final outcome:** The status API is
  the proposed recovery path. Authenticated callbacks or event delivery may
  accelerate awareness but do not become the only recovery mechanism until
  their promise is established.
- **Authoritative record when the mechanisms disagree:** Harborline's refund
  outcome ledger. A mismatch opens reconciliation and blocks a contradictory
  public transition; it is not resolved by trusting whichever message arrived
  last.
- **Evidence that the composition works:** Contract and authorization tests;
  state-transition and time/failure tests; event provenance, duplication, and
  ordering tests; same-identity end-to-end traces; representative MarketSquare
  recovery tests; reconciliation of ambiguous processor attempts; and an
  operator recovery exercise. These are proposed evidence requirements, not
  results from this desk test.

## Decisions the tools exposed

The combined application exposed decisions that the phrase “approve a refund”
concealed:

1. The consumer needs request, acceptance, and status capabilities; it does not
   receive authority to approve or settle Harborline refunds.
2. `accepted`, `authorized`, `submitted`, `settled`, `rejected`, and `unknown`
   are distinct contract meanings.
3. The provider remains accountable across vendor boundaries even though it
   does not control every downstream action.
4. Business idempotency attaches to the refund intent, not an HTTP request.
5. An ambiguous payment timeout requires reconciliation, not a second refund.
6. The API exposes the capability, the workflow preserves responsibility, and
   events declare facts. None can silently substitute for the others.
7. One business identity and one authoritative consumer-facing outcome record
   are required to detect disagreement across the composition.
8. Disabling new requests does not discharge responsibility for accepted work.
9. Customer communication, vendor guarantees, deadline policy, and protected
   reason detail remain explicit unknowns rather than invented implementation
   answers.

## Usability observations and friction

### API Meaning-and-Authority Brief

What worked in this desk application:

- Separating acceptance from completion immediately revealed that a successful
  API response could not honestly mean “money refunded.”
- Actor, subject, tenant, and authority prompts prevented authentication from
  standing in for delegated business authority.
- The failure table forced a safe consumer action for unknown monetary outcome,
  rather than treating every dependency failure as retryable.
- The evidence floor kept a plausible design from being described as proven.

Material defects found and corrected:

1. The provider prompt could be filled with the API team, the retailer, or a
   downstream vendor. It now asks for the provider accountable for the
   capability promise.
2. The acceptance prompt invited an HTTP-status answer. It now explicitly asks
   for the business condition, not only the transport response.
3. The completion prompt did not remind the reviewer to cover rejection or
   compensated cancellation. It now asks for every terminal outcome.
4. The final review question named Northbridge, which failed the transfer test
   for an unrelated scenario. It now refers generically to the provider.

Remaining friction not yet patched:

- A multi-party capability has no dedicated place to name critical delegated
  executors and the evidence borrowed from each. This application placed those
  distinctions across provider, authority, outcome record, transaction, and
  failure fields. Adding a dependency-authority table may help, but one desk
  scenario is not enough evidence to expand the asset.
- “Contract owner,” “change authority,” and “operational owner” can be roles,
  groups, or governance paths. A practitioner test should reveal whether the
  prompts need examples or whether examples would make them too prescriptive.
- The brief is deliberately substantial. A timed practitioner exercise is
  needed to learn which fields are skipped, duplicated, or answered with
  implementation details when chapter context is absent.

### API, Event, or Workflow Decision Tree

What worked in this desk application:

- The first question separated MarketSquare's deliberate request from facts
  that other systems may independently consume.
- The workflow branch prevented API acceptance and event publication from
  obscuring Harborline's long-running responsibility.
- The hybrid section allowed an explicit composition instead of forcing the
  scenario into one technology label.

Material defect found and corrected:

- The original hybrid check could assign an owner to each mechanism while the
  mechanisms still referred to different business identities or disagreed
  about outcome. The composition and final check now require a shared business
  identity, a requester discovery path, and an authoritative record for
  disagreement.

Remaining friction not yet patched:

- “Primary boundary” can be misread as “only mechanism.” The composition section
  corrected that interpretation here, but an independent practitioner test is
  needed before changing the branch language.
- The tree identifies that events are present but cannot validate event
  ontology, replay, traffic multiplication, or reaction authority. Those belong
  to the Events field guide; the API tool should keep the boundary visible
  rather than absorb that method.
- The tree identifies durable responsibility but does not design workflow state,
  compensation, migration, or human escalation. Those belong to the Durable
  Workflows field guide.

## Concrete revision recommendations

### Applied now

1. Generalize the meaning brief's design-review question beyond Northbridge.
2. Clarify provider accountability rather than implementation ownership.
3. Require business definitions for acceptance and every terminal outcome.
4. Require hybrid designs to share a business identity and name the requester
   discovery path and authoritative outcome record.

### Hold until independent practitioner testing

1. Test whether a dependency-authority table is necessary for vendor-connected
   APIs or whether it duplicates the existing authority and evidence sections.
2. Ask a practitioner to complete the meaning brief without chapter context;
   record elapsed time, skipped fields, ambiguous fields, and substitutions of
   implementation detail.
3. Ask the practitioner to explain `accepted`, `complete`, `unknown`, and safe
   retry in their own words before showing this completed example.
4. Give a second practitioner only the decision tree and test whether they
   assign the API response, workflow responsibility, facts, business identity,
   and authoritative record correctly.
5. Mutation-test the scenario by making the payment processor lack stable
   idempotency, removing status polling, and delivering `RefundSettled` before
   `RefundPaymentSubmitted`. Record which prompts expose each unsafe design.
6. Repeat the exercise with a mostly synchronous capability to ensure the
   revised tools do not force every design into a workflow.

## Evidence limits and next gate

This desk application establishes only that one informed reviewer could use the
two assets to expose a coherent set of questions and that several wording and
hybrid-composition defects were visible enough to correct. It does not establish
reader comprehension, workshop transfer, implementation correctness, vendor
behavior, security sufficiency, production reliability, or business benefit.

The next evidence gate is an independent practitioner using blank copies of the
revised tools without this completed example. Their field choices, questions,
misinterpretations, and safe-recovery decisions should be retained, including
negative results. Only then should broader template expansion be considered.
