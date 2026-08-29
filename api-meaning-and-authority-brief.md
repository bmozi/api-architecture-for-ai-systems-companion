# API Meaning-and-Authority Brief

Use this before selecting endpoints, schemas, frameworks, or generated code.

## Ten-minute first pass

Do not begin by completing every field. Begin with five sentences:

1. **The person or system needs to:** name the outcome, not the endpoint.
2. **This API promises to:** state the capability in ordinary business language.
3. **It may be requested by:** name who may act, for whom, and within which
   account, tenant, or organizational boundary.
4. **The consumer will know the outcome when:** distinguish received,
   accepted, completed, rejected, and unknown.
5. **The promise is owned and proved by:** name the accountable owner,
   authoritative outcome record, and one piece of evidence.

If those sentences cannot be completed without words such as “probably,”
“usually,” or “the service handles that,” stop before generating the interface.
The uncertainty is the design work.

### Miniature example

| First-pass question | Northbridge reservation answer |
| --- | --- |
| Who needs what? | A distribution partner needs to request an inventory commitment for an eligible buyer and learn the final outcome. |
| What does the API promise? | Northbridge will accept or reject responsibility for the request, then report whether inventory was committed, rejected, expired, or released. |
| Who may request it? | The registered partner application may act only for a buyer, product, location, and quantity covered by current delegated authority. |
| How is completion known? | The authoritative reservation record reaches a named terminal outcome; `202 Accepted` alone is not completion. |
| Who owns and proves it? | The Northbridge capability owner owns the contract, service operations owns unresolved work, and the reservation record plus linked request evidence proves the outcome. |

This example is deliberately small. See the
[completed Northbridge Meaning-and-Authority Brief](examples/northbridge-inventory-reservation-meaning-authority-example.md)
for the comprehensive version and its evidence limits.

## Plain-language vocabulary

- **Actor:** the identity taking the immediate action.
- **Client:** the application carrying the request.
- **Principal:** the person or organization whose authority is being used.
- **Delegate:** a party permitted to act for the principal within stated limits.
- **Subject:** the person, account, order, or other party affected.
- **Protected object:** the record, funds, inventory, device, or resource the
  action can change.
- **Idempotency:** the rule that prevents one business intent from creating a
  second outcome when a request is repeated.
- **Authoritative outcome record:** the record the organization is willing to
  rely on when systems disagree about what finally happened.

These roles may belong to the same party in a simple API. Naming them separately
prevents a more complex integration or AI caller from silently combining powers.

## 1. Capability promise

- **Capability name:**
- **Business outcome the consumer needs:**
- **Why an API is the right interaction:**
- **What this contract does not promise:**

## 2. Parties and authority

- **Consumer:**
- **Provider accountable for the capability promise:**
- **Actor performing the immediate action:**
- **Client presenting or transporting the request:**
- **Principal whose authority is represented:**
- **Delegate authorized to act for that principal:**
- **Affected subject or business party:**
- **Protected object or resource acted upon:**
- **Tenant, organization, or account boundary:**
- **Authority required to request the capability:**
- **System or role authoritative for granting that authority:**
- **Contract owner:**
- **Change authority:**
- **Operational owner:**

## 3. Meaning and outcomes

- **Preconditions:**
- **A request is accepted when (state the business condition, not only the transport response):**
- **The business outcome is complete when (include every terminal outcome):**
- **Authoritative outcome record:**
- **Information returned to the consumer:**
- **Information intentionally not exposed:**
- **Invariants that must remain true:**

## 4. Repetition, conflict, and time

- **What may safely repeat:**
- **Business idempotency key or identity:**
- **Concurrency or stale-state rule:**
- **Transaction boundary:**
- **Expected response-time boundary:**
- **When work continues after the response:**
- **How the consumer discovers final outcome:**

## 5. Failure contract

| Failure class | Meaning to consumer | Safe consumer action | Evidence retained |
| --- | --- | --- | --- |
| Invalid request | | | |
| Not authorized | | | |
| Conflict or stale state | | | |
| Unavailable before acceptance | | | |
| Accepted but incomplete | | | |
| Terminal business rejection | | | |
| Unknown outcome | | | |

## 6. Compatibility promise

- **Consumers or consumer classes:**
- **Behavior they may rely on:**
- **Semantic assumptions that must remain stable:**
- **Timing, ordering, or volume assumptions:**
- **Authorization assumptions:**
- **Deprecation and migration promise:**
- **Exit or reversal path:**

## 7. Evidence floor

- **Contract/schema evidence:**
- **Behavioral evidence:**
- **Authorization evidence:**
- **Idempotency/concurrency evidence:**
- **Representative consumer evidence:**
- **Failure and recovery evidence:**
- **Operational observability evidence:**
- **Unknowns that block implementation or release:**

## Design-review question

If the generated code disappeared tomorrow, would this brief still tell another
team what the provider promised and how to prove it?

Give the five first-pass sentences—not the implementation—to someone outside
the producing team. Ask them to explain what the consumer may request, what
`accepted` means, how completion is discovered, and what must not happen on a
retry. If their answer depends on private team knowledge, revise the brief
before implementation.

## Optional worksheet A: Shape comparison

Use this worksheet when more than one public interface shape is materially
plausible. Include at least three credible candidates; do not manufacture a
resource, operation, RPC, query, or hybrid candidate merely to fill a row.

| Candidate and public shape | Consumer intent and enduring concept | Authority granted and retained | Acceptance, completion, and recovery | Identity, repetition, and conflict | Compatibility and operational burden | Select or reject, with governing reason and revisit condition |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | | | |
| | | | | | | |
| | | | | | | |

## Optional worksheet B: Command outcomes

| Public state or outcome | Terminal? | Responsibility owner | What the consumer may rely on | Safe next action | Discovery, deadline, or escalation |
| --- | --- | --- | --- | --- | --- |
| Not accepted - classify by the published failure contract | | | | | |
| Accepted or in progress | | | | | |
| Terminal commitment | | | | | |
| Terminal noncommitment | | | | | |
| Unknown outcome | | | | | |

## Optional worksheet C: Query claims

| Query or projection | Exact claim returned | Authoritative source and effective time | Freshness, consistency, and completeness boundary | Authorized subjects and fields | Ordering, pagination, cost, and capacity boundary | Permitted consumer decision | What this answer does not prove |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | |
