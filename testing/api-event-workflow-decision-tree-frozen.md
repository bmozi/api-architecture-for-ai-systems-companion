# API, Event, or Workflow Decision Tree

Start with the promise, not the technology already in the platform.

## 1. What does another party need?

### A capability it may deliberately invoke

Examples: reserve inventory, calculate a quote, retrieve an account view.

Use an **API** as the primary boundary when the consumer needs a governed
capability or query with an explicit request and response contract.

Ask:

- Who may invoke it and for whom?
- What outcome is promised by the response?
- What happens if the request repeats or conflicts?
- Which failures can the consumer safely act on?

### A fact it may independently react to

Examples: inventory was reserved, an order was accepted, a policy changed.

Use an **event** as the primary boundary when a fact has occurred and authorized
participants may react without the declarer coordinating each response.

Ask:

- Who has authority to declare the fact?
- What caused it and what invariants does it assert?
- May it duplicate, arrive late, or be replayed?
- How can reactions multiply traffic, cost, or autonomous action?

### A promise that must survive time, failure, and human delay

Examples: resolve a dispute, complete partner onboarding, approve and issue a
credit.

Use a **durable workflow** as the primary boundary when responsibility,
progress, compensation, deadlines, and recovery must persist across steps.

Ask:

- Who owns completion?
- What durable state represents progress?
- What is compensated when rollback is impossible?
- Where must human judgment advance, pause, or stop work?

## 2. Is the answer more than one?

Compose the mechanisms explicitly:

1. an API may accept a capability request;
2. a workflow may preserve responsibility for long-running completion; and
3. events may declare accepted, progressed, completed, or failed facts; and
4. one business identity and authoritative outcome record must reconcile the
   mechanisms.

Do not call the composition “event-driven” or “API-first” and leave ownership
implicit. Name which mechanism carries which promise.

## 3. Final check

- **Capability promised by API:**
- **Facts declared by events:**
- **Responsibility preserved by workflow:**
- **Authoritative owner for each:**
- **Business identity carried across the mechanisms:**
- **How the requester discovers current and final outcome:**
- **Authoritative record when the mechanisms disagree:**
- **Evidence that the composition works:**
