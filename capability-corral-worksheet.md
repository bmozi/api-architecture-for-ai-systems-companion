# Capability Corral Worksheet

Use this worksheet to turn a large API estate into a smaller, understandable
set of governed business capabilities and carefully chosen MCP surfaces.

This is a design and review aid. Completing it does not prove that a capability
is safe, authorized, reliable, or valuable. Mark work as `planned`, `unrun`,
`pass`, `fail`, or `unknown`, and keep the evidence that supports the mark.

## The idea in one page

Do not expose 2,100 APIs as 2,100 MCP tools. That makes the tool catalog another
form of API sprawl. Instead, move through these decisions:

```text
Technical API estate
  -> inventory, deduplicate, classify, and find authority
Business capabilities and bounded contexts
  -> assign outcomes, owners, boundaries, and policy
Capability façades or adapters
  -> preserve identity, authority, evidence, failure, and cost semantics
MCP servers and resources
  -> expose only the few AI-facing operations that have a real user purpose
Approved hosts, applications, and agents
  -> select and invoke within explicit authority and confirmation limits
```

The governing principle is:

> MCP should reduce the cognitive burden of the API estate without hiding its
> authority, risk, or operational truth.

An MCP server is an exposure and interoperability layer. It is not the business
authority, a replacement for an API contract, or permission for an agent to
invent a workflow. The host, client, server, underlying API, workflow, and
event each retain their distinct responsibilities. See the [API, MCP Tool,
Event, Workflow, or Agent Decision Guide](api-event-workflow-decision-tree.md)
and the [Agent-Ready API and MCP Capability Brief](agent-ready-api-and-mcp-capability-brief.md).

## How to use the worksheet

Run this with people who understand both the business outcome and the systems
that currently implement it. A catalog team alone cannot decide business
authority; a business group alone may not see duplicate effects or hidden
dependencies.

1. Choose a meaningful business outcome, not an API team or URL prefix.
2. Gather the APIs that contribute to, read, or mutate that outcome.
3. Record duplicates, aliases, wrappers, ownership gaps, and competing sources
   of truth. Do not silently choose a winner.
4. Draw the capability boundary: what belongs together, what must remain
   separate, and where a handoff occurs.
5. Name the canonical authority, accountable business owner, technical owner,
   and affected parties.
6. Decide which promises are API calls, MCP tools, MCP resources, events,
   durable workflows, or agent decisions.
7. Design the smallest useful AI-facing surface. Prefer business operations
   over CRUD operations and search over unrestricted enumeration.
8. Test authority, repetition, ambiguous outcomes, data disclosure, capacity,
   and recovery before expanding access.
9. Migrate in waves. Retire an API only after its consumers, authority, evidence,
   and rollback path have been accounted for.

Keep a stable capability ID. One capability may initially use many APIs and
later use fewer; its identity should not change merely because its plumbing
changes.

## 1. Capability record

**Record ID and version:**  
**Date and participants:**  
**Status:** planned / discovery / designed / piloting / operating / retired  
**Business capability name:**  
**One-sentence outcome:**  
**Plain-language description:**  
**Person, team, partner, or system needing the outcome:**  
**Recognizable situation that creates the need:**  
**Why the outcome matters:**  
**What failure would cost the person or business:**  
**In scope:**  
**Explicitly out of scope:**  
**Related capabilities and handoff points:**  
**Bounded-context or domain boundary:**  

Explain this capability without saying “the API does X.” The API is machinery;
the capability is the valuable, governed result.

## 2. Inventory and corral the API estate

Attach a catalog export or link to the source inventory. Include APIs that are
not currently healthy or documented; missing information is itself a finding.

| API or operation | Version | Read/query or mutation | Data/business outcome | Current owner | Claimed authority | Actual authority | Consumers | Duplicate or overlap | Status/evidence |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | | | |
| | | | | | | | | | |
| | | | | | | | | | |

For each candidate API, ask:

- Does it name a stable business promise, or only a technical resource?
- Does it make a decision, report a fact, start work, or merely forward a call?
- Which system is allowed to create or change the authoritative state?
- Are two APIs able to perform the same business action with different rules?
- Is the apparent duplication intentional (for example, a partner contract),
  accidental, or unknown?
- Which fields establish tenant, actor, purpose, idempotency, evidence, and
  outcome state?
- What happens when the API is called twice, times out, or returns an error
  after the provider may have acted?

Do not deduplicate by matching names alone. Two endpoints named `reserve` may
have different subjects, authority, timing, or promises. Conversely, several
different names may mutate the same underlying business fact.

### Corral decision

**APIs grouped into this capability:**  
**APIs deliberately left outside and why:**  
**Suspected duplicate or conflict:**  
**Missing inventory or owner:**  
**Canonical authority candidate:**  
**Decision owner and date:**  
**Evidence or unresolved question:**  

## 3. Meaning, authority, and ownership

**Business owner accountable for the outcome:**  
**Technical owner accountable for operation:**  
**Data/system authority:**  
**Operational/support owner:**  
**Risk, privacy, or compliance owner:**  
**Consumers and affected parties:**  
**Tenant/account boundary:**  
**Permitted purpose:**  
**Actor and principal:**  
**Subject or resource affected:**  
**Delegation source, limits, and revocation:**  
**Confirmation or independent approval required:**  
**Who may not perform this action:**  

Write the outcome vocabulary explicitly:

| State | Meaning in this capability | Who may declare it | Durable record/evidence | Safe next action |
| --- | --- | --- | --- | --- |
| Received | | | | |
| Accepted | | | | |
| Pending | | | | |
| Completed | | | | |
| Denied | | | | |
| Rejected/invalid | | | | |
| Unknown after timeout | | | | |
| Reversed/corrected | | | | |

An agent seeing a tool does not thereby have authority. Enforcement must check
the actual actor, principal, subject, tenant, purpose, scope, and time at the
point where the consequential action is authorized.

## 4. Choose the right architectural role

| Promise or need | API | MCP tool | MCP resource | Event | Durable workflow | Agent decision |
| --- | --- | --- | --- | --- | --- | --- |
| Request an immediate governed action | | | | | | |
| Read an authorized current view | | | | | | |
| Notify subscribers that a fact occurred | | | | | | |
| Continue work across time and retries | | | | | | |
| Choose among permitted next actions | | | | | | |

Record the decision for each important promise:

**Primary API operation or capability façade:**  
**MCP needed? Why is a fixed integration insufficient?**  
**MCP tools proposed:**  
**MCP resources proposed:**  
**Events needed:**  
**Workflow needed:**  
**What remains a human or application decision:**  
**What is explicitly not exposed through MCP:**  
**Revisit condition:**  

MCP servers should expose focused, composable capabilities. Avoid a server
that becomes an unrestricted proxy, generic SQL endpoint, arbitrary HTTP
caller, or catalogue of internal CRUD methods.

## 5. Design the MCP surface

For each proposed tool, complete a separate row. A resource may be more honest
than a tool when the AI needs an authorized view rather than permission to act.

| Tool/resource name | User outcome | Read or mutate | Inputs and scope | API/adapter invoked | Authority check | Confirmation | Output and evidence | Stop/failure behavior |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | | |
| | | | | | | | | |
| | | | | | | | | |

For every tool, write both descriptions:

**Name:**  
**Description shown to the model:**  
**Use when:**  
**Do not use when:**  
**Input schema and validation:**  
**Output schema and state vocabulary:**  
**Mapping to API inputs and outcomes:**  
**Protocol errors versus business errors:**  
**Data intentionally omitted:**  
**Rate, value, quantity, and concurrency limit:**  
**Business identity/idempotency key:**  
**Correlation and outcome identifiers:**  
**Owner and versioning policy:**  

### Small-surface test

Before approving a tool, answer yes, no, or unknown:

- Can a reader name the business outcome in one sentence?
- Does the name describe that outcome rather than an internal table or URL?
- Does the tool have one clear authority and owner?
- Is the tool narrower than the underlying technical access it uses?
- Can a caller distinguish accepted, completed, denied, and unknown?
- Can the provider safely identify a repeated intent?
- Is the result useful without exposing unnecessary sensitive data?
- Is there a safe stop, reconciliation, and human escalation path?

Any `no` or `unknown` requires a design decision or an explicit boundary; it is
not a reason to conceal the gap in prose.

## 6. Worked example: Inventory Commitment

This is a constructed example for learning, not a claim about any employer.

### Starting estate

Suppose an organization has these APIs:

| Existing API group | Apparent job | Discovery finding |
| --- | --- | --- |
| Inventory availability | Returns quantities by location | Read-only view; stale by up to a documented interval |
| Reservation | Holds stock for an order | Creates a time-bounded commitment |
| Allocation | Assigns stock to a fulfillment path | Different authority; may run asynchronously |
| Replenishment | Requests inbound stock | Separate supplier and funding authority |
| Order status | Reports order state | Downstream fact, not inventory authority |

The first temptation is to publish every endpoint as an MCP tool. Instead, the
team identifies a business outcome: a permitted actor needs to determine
whether a requested quantity can be committed, request that commitment, and
check its resulting status.

### Capability record

**Capability:** Inventory Commitment  
**Outcome:** Make and report a bounded, time-limited commitment of available
inventory for an eligible order or business request.  
**In scope:** availability assessment, commitment request, commitment status.  
**Out of scope:** supplier replenishment, final shipment allocation, pricing,
and arbitrary inventory mutation.  
**Canonical mutation authority:** Reservation service, subject to tenant,
order, quantity, and policy checks.  
**Business owner:** Inventory operations.  
**Technical owner:** Commitment platform team.  
**Open promise:** An accepted request may remain pending; the workflow owns
progress and publishes the terminal result.  

### Proposed MCP surface

| MCP surface | Purpose | Underlying calls | Important boundary |
| --- | --- | --- | --- |
| `check_inventory_commitment` | Explain whether a requested commitment appears possible | Availability plus policy/read APIs | Does not reserve or promise final success |
| `request_inventory_commitment` | Request one bounded commitment | Reservation command through the authority façade | Requires authorization, idempotency, limits, and confirmation where required |
| `get_commitment_status` | Retrieve current status and evidence | Commitment status/read API | Reports facts; does not retry or mutate |

The tool descriptions should say that availability is an assessment, not a
guarantee; that accepted is not completed; and that an unknown result must be
reconciled before another request is attempted. The MCP adapter preserves the
tenant, actor, principal, order, quantity, purpose, idempotency key, and
correlation ID instead of asking the model to supply authority in natural
language.

### Example decision path

```text
Person asks: Can we commit 40 units for order O-17?
  -> agent calls check_inventory_commitment
  -> result: possible, subject to policy; no mutation occurred
Person confirms the bounded request
  -> agent calls request_inventory_commitment with business idempotency key
  -> result: accepted, commitment C-91, pending
Workflow continues independently of the agent session
  -> get_commitment_status reports completed, denied, or still pending
```

If the request times out after the reservation service may have acted, the
agent must call `get_commitment_status` using the original business identity.
It must not issue a second reservation merely because the first answer was
missing.

### Deliberately excluded surfaces

- `update_inventory_row`: exposes storage mechanics, not a governed outcome.
- `reserve_any_quantity`: hides quantity, policy, and cost limits.
- `call_inventory_api`: turns the MCP server into unrestricted proxy access.
- `retry_reservation`: makes repetition a conversational choice instead of a
  controlled business rule.

## 7. Conway and inverse-Conway review

Use this section to notice whether the proposed surface merely reproduces the
current organization. If servers follow existing technical team boundaries,
the AI surface may preserve every silo and duplicate. A capability boundary can
instead clarify durable business responsibility, but it must not be used to
erase real authority or ownership.

**Current team/repository boundaries:**  
**Business responsibility that should be durable:**  
**Where current boundaries split one outcome:**  
**Where one team owns unrelated outcomes:**  
**Proposed capability owner:**  
**Teams/repositories that must align or collaborate:**  
**Decision rights that remain separate:**  
**Organizational change implied:**  
**What is an architectural hypothesis rather than an observed fact:**  

Review question: if the team names, repository names, or vendor products
changed tomorrow, would this capability still make sense to a customer or
operator? If not, the boundary may be a team map rather than a business map.

## 8. Risk, evidence, and release gate

| Question to prove or disprove | Test or evidence required | Deliberate failure/mutation | Status | What remains unproved | Owner |
| --- | --- | --- | --- | --- | --- |
| Only eligible consumers discover the surface | | | planned/unrun/pass/fail/unknown | | |
| Actor has authority for principal, subject, tenant, and purpose | | | | | |
| Tool preserves API meaning and narrows access where intended | | | | | |
| One business intent produces the promised number of effects | | | | | |
| Repeated and concurrent requests are safe | | | | | |
| Accepted, pending, completed, denied, and unknown are distinguishable | | | | | |
| Timeout-after-effect has a reconciliation path | | | | | |
| Sensitive data is not disclosed to model, logs, or unauthorized users | | | | | |
| Rate, quota, cost, and dependency exhaustion are bounded | | | | | |
| Events and workflows declare only facts and responsibility they own | | | | | |
| An authorized reviewer can reconstruct request, decision, and outcome | | | | | |
| Capability can be narrowed, revoked, disabled, and recovered | | | | | |

### Minimum provenance chain

Record identifiers, not just screenshots or model text:

- user/system intent reference;
- host, MCP client, and server identity and versions;
- actor, principal, subject, tenant, purpose, and delegation decision;
- tool name, schema version, inputs after validation, and policy decision;
- underlying API request and response/correlation IDs;
- idempotency key and retry history;
- event/workflow/commitment identity, if applicable;
- final outcome authority, timestamp, and evidence location;
- reviewer, test environment, test data, and unresolved limitations.

Do not call a capability “AI-ready” because a tool can be invoked. Release only
when the evidence floor appropriate to the consequence has been met.

## 9. Migration waves and retirement

Start with a capability that has a clear owner, meaningful demand, bounded
consequence, and enough evidence to learn safely. Do not begin by wrapping the
largest or most politically visible API group simply because it has the most
endpoints.

| Wave | Capability/API scope | Consumer impact | New façade or MCP surface | Parallel period | Success evidence | Rollback/narrowing | Retirement decision |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0: discover | | | | | | | |
| 1: read-only | | | | | | | |
| 2: bounded action | | | | | | | |
| 3: migrate consumers | | | | | | | |
| 4: retire or retain | | | | | | | |

Before retiring an API, confirm:

- every consumer and contractual use is known or explicitly accepted as
  unknown;
- the replacement preserves meaning, authority, compatibility, errors,
  idempotency, evidence, and support obligations;
- migration and rollback have been exercised;
- historical records remain interpretable;
- the old endpoint cannot still be reached through an MCP proxy or forgotten
  integration;
- an accountable owner has approved the retirement and communicated the date.

An API may remain for a legitimate fixed application or partner even when an
MCP façade becomes the preferred AI-facing path. “Not exposed through MCP” does
not mean “obsolete.”

## Reader exercise: corral your own API estate

Choose a real or anonymized domain with at least ten APIs. Do not start with
MCP. Complete the following on paper or in a copy of this worksheet:

1. Name three user or business outcomes that matter in that domain.
2. Select one outcome and list every API that reads, decides, or mutates it.
3. Mark each API's claimed and actual authority as known, conflicting, or
   unknown.
4. Draw the capability boundary and name what is out of scope.
5. Define the outcome vocabulary, including timeout-after-possible-effect.
6. Propose no more than three MCP tools and two resources. Explain every API
   you intentionally do not expose.
7. Identify the agent's maximum authority, confirmation point, stop condition,
   and reconciliation path.
8. Design one deliberate failure test for duplicate intent, stale state,
   unauthorized access, and sensitive-data disclosure.
9. Choose a migration wave and name the owner and rollback evidence.
10. Ask a reviewer from the business, platform, security/privacy, and operations
    perspectives to mark each unknown. Do not turn unreviewed assumptions into
    tool descriptions.

**What I learned about the business outcome:**  
**The smallest useful MCP surface is:**  
**The most dangerous hidden assumption is:**  
**Evidence still missing:**  
**Next design-review question:**  

## References and boundaries

The [MCP architecture specification](https://modelcontextprotocol.io/specification/2025-06-18/architecture)
describes the host, client, and server relationship and capability negotiation.
The [MCP tools specification](https://modelcontextprotocol.io/specification/2025-06-18/server/tools)
describes protocol-level tool exposure. Those specifications do not decide your
business meaning, authority, ownership, data policy, recovery contract, or
evidence floor. Record the exact specification and SDK revision used by an
implementation and recheck it when the implementation changes.
