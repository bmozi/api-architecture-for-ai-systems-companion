# API, MCP Tool, Event, Workflow, or Agent? Decision Guide

Start with what a person or system needs to accomplish. Name the architecture
only after the need and consequence are clear.

**Status:** Working companion asset; independent practitioner usability remains
untested.

## A plain-language first pass

| Somebody needs to... | Start by considering... | Because... |
| --- | --- | --- |
| ask a provider to do something or return dependable information | an **API** | another consumer needs a governed request and response contract |
| let an approved AI application discover and invoke that capability | an **MCP tool** | the capability needs an AI-facing exposure and interoperability layer |
| tell interested participants that something actually happened | an **event** | authorized participants need to react to a declared fact |
| keep an unfinished promise moving through time, failure, or human judgment | a **durable workflow** | somebody must preserve responsibility, progress, recovery, and completion |
| decide which approved action fits the current situation | an **agent** | bounded reasoning and tool selection are part of the design |

These roles can compose. They are not interchangeable.

## 1. Does another party need a governed capability?

Examples: reserve inventory, calculate a quote, retrieve an account view.

Use an **API** as the primary boundary when a consumer needs to deliberately
invoke a capability or query with an explicit request and response contract.

Ask:

- Who may invoke it and for whom?
- What outcome is promised by each response?
- What happens if the request repeats or conflicts?
- Which failures can the consumer safely act on?
- Which consumer assumptions must survive change?

An endpoint is not enough. The API must preserve the business promise beneath
the transport.

## 2. Does an AI application need to discover and invoke the capability?

Examples: an approved service assistant requests a reservation, an engineering
assistant queries deployment evidence, or an operations assistant opens a
bounded recovery action.

Use an **MCP tool** when an MCP-compatible AI application needs a protocol-level
description and invocation path for an approved capability.

Ask:

- Which underlying API or governed operation supplies the capability?
- Does the tool preserve actor, principal, subject, tenant, and delegation?
- Which arguments may the model propose, and which require user confirmation?
- How are idempotency, errors, unknown outcomes, rate limits, and evidence
  preserved across the wrapper?
- What does the MCP client, host, and server each enforce—and what remains the
  provider's responsibility?

MCP makes a tool discoverable and invocable. It does not make an unsafe API
safe, turn authentication into business authority, or decide what the
capability means.

## 3. Does another party need to react to a fact?

Examples: inventory was reserved, an order was accepted, a policy changed.

Use an **event** as the primary boundary when a fact has occurred and authorized
participants may react without the declarer coordinating each response.

Ask:

- Who has authority to declare the fact?
- What caused it and what invariants does it assert?
- May it duplicate, arrive late, or be replayed?
- How can reactions multiply traffic, cost, or autonomous action?

A command with a past-tense name is not automatically a fact.

## 4. Must responsibility survive time, failure, or human delay?

Examples: resolve a dispute, complete partner onboarding, approve and issue a
credit.

Use a **durable workflow** when responsibility, progress, compensation,
deadlines, and recovery must persist across steps.

Ask:

- Who owns completion?
- What durable state represents progress?
- What is compensated when rollback is impossible?
- Where must human judgment advance, pause, or stop work?
- How does the requester discover the authoritative current and final outcome?

Several successful local steps do not prove that somebody owns the open
promise.

## 5. Must a system choose among tools or actions?

Examples: an agent decides which evidence to gather, proposes a recovery path,
or selects an approved capability for a stated goal.

Use an **agent** when bounded reasoning, planning, or tool selection is a real
part of the system rather than a fixed application path.

Ask:

- What may the agent perceive, decide, and do?
- Whose authority is it exercising, for which subject and purpose?
- Which tools are available, and which actions require approval?
- What budget, deadline, or blast-radius boundary stops action?
- What provenance and outcome evidence must survive every invocation?
- When must the agent stop, escalate, or hand responsibility to a person or
  durable workflow?

An agent is a participant using governed paths. It is not the owner of the API
contract or a substitute for business authority.

## 6. Compose the roles explicitly

For one business outcome, complete this sentence before drawing the technology
diagram:

> **[Consumer]** uses **[API]** to request **[capability]**. If an approved AI
> application needs access, **[MCP tool]** exposes the same governed capability.
> **[Agent or person]** may select or approve the invocation under **[delegated
> authority]**. **[Workflow owner]** preserves responsibility until **[terminal
> outcome]**. **[Event authority]** declares **[facts]**. **[Authoritative
> record]** and **[evidence]** reconcile the result.

Do not call the composition “event-driven,” “API-first,” or “agentic” and leave
ownership implicit. Name which role carries which promise.

## Decision record

- **Person, team, or system trying to accomplish something:**
- **Visible consequence if the design is wrong:**
- **Capability promised by the API:**
- **API consumer and provider:**
- **MCP tool, if an AI-facing exposure is needed:**
- **Underlying capability and contract version used by the tool:**
- **Agent decision, if bounded tool selection is needed:**
- **Delegated authority and approval boundary:**
- **Facts declared by events:**
- **Responsibility preserved by workflow:**
- **Authoritative owner for each role:**
- **Business identity carried across the mechanisms:**
- **How the requester discovers current and final outcome:**
- **Authoritative record when observations disagree:**
- **Failure that would expose a confused boundary:**
- **Evidence that the composition works:**
- **Evidence still missing or unrun:**

## Final challenge

Remove the technology names from your completed record. Can a product,
security, operations, or partner representative still explain who may ask for
what, who remains responsible, what facts others may trust, and how an AI tool
changes the route without changing the promise?
