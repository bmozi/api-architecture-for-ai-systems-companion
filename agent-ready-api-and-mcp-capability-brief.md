# Agent-Ready API and MCP Capability Brief

Use this brief when an existing or proposed API capability will be exposed to
an AI application, including through a Model Context Protocol (MCP) server.

**Use boundary:** Illustrative field tool; independent-practitioner usability
remains untested. Completing the template is not release, safety,
business-value, or production-fitness evidence.

## What this brief is for

An MCP tool can make a capability easier for an AI application to discover and
invoke. That is useful when the underlying capability is already meaningful,
authorized, recoverable, and observable. It is dangerous when the tool wrapper
hides the decisions the API was designed to preserve.

This brief keeps four things separate:

1. the business need a person or system is trying to satisfy;
2. the governed API capability that owns the promise;
3. the MCP tool that exposes the capability to an AI application; and
4. the agent, person, or fixed application path that decides whether to invoke
   it.

**Reader translation:** *Delegated authority* is the specific power a caller
may use, who granted it, and where the system enforces the limit. Authentication
and an API scope can show who called or what the software may technically try;
they do not by themselves prove legitimate authority to act for a person,
partner, or organization.

The official MCP specification defines protocol mechanisms through which
servers expose tools with descriptions and schemas for language models to
invoke. It does not define your business meaning, organizational authority, or
evidence floor. Record the exact protocol revision used by the implementation.

- **MCP specification revision and link:**
- **MCP SDK or implementation and version:**
- **Date reviewed:**

Reference:
[MCP tools specification, revision 2026-07-28](https://modelcontextprotocol.io/specification/2026-07-28/server/tools)

## 1. Begin with the person and outcome

- **Person, team, partner, or system trying to accomplish something:**
- **Recognizable situation that creates the need:**
- **Outcome they need:**
- **Why that outcome matters:**
- **What happens to them if the action is wrong, duplicated, delayed, denied,
  or left ambiguous:**
- **Current manual, application, or integration path:**
- **What AI-mediated access would make easier or newly possible:**
- **What must not become less safe, understandable, or recoverable:**

If this section can only be answered with “use AI” or “add an MCP server,” the
capability has not been identified yet.

## 2. Name the underlying governed capability

- **Capability name:**
- **Owning API or governed operation:**
- **API contract version or baseline:**
- **Provider accountable for the promise:**
- **Consumer classes already supported:**
- **Exact business outcome promised:**
- **Meaning of received, accepted, pending, completed, denied, and unknown:**
- **Authoritative outcome record:**
- **What this capability explicitly does not promise:**
- **API Meaning-and-Authority Brief reference:**

Do not create the MCP tool before the underlying capability can be explained in
business language. If there is no API because the tool performs a local or
otherwise governed operation directly, document the equivalent capability
contract and owner here rather than pretending the protocol supplies one.

## 3. Decide whether MCP is the right exposure layer

- **AI host or application that needs the capability:**
- **Why a fixed application integration is insufficient:**
- **Why an MCP tool is useful for this consumer:**
- **Alternative exposure paths considered:**
- **Expected discovery and invocation behavior:**
- **Host responsibilities:**
- **MCP client responsibilities:**
- **MCP server responsibilities:**
- **Underlying API/provider responsibilities:**
- **Decision and revisit condition:**

MCP should improve interoperability or tool discovery. It should not create a
second business contract with weaker authority, failure, or evidence rules.

## 4. Define the tool as an honest view of the capability

- **Tool name:**
- **Plain-language title:**
- **Description shown to the model:**
- **When the tool should be considered:**
- **When the tool must not be used:**
- **Input schema reference:**
- **Output schema reference, if used:**
- **API operation or adapter invoked:**
- **Mapping from tool inputs to API inputs:**
- **Mapping from API outcomes to tool results:**
- **Protocol errors distinguished from business/tool-execution errors:**
- **Fields or context intentionally not exposed to the model:**

### Semantic preservation check

| API contract element | MCP tool representation | Preserved, narrowed, or changed? | Authority approving any change | Evidence required |
| --- | --- | --- | --- | --- |
| Actor and client | | | | |
| Principal and subject | | | | |
| Tenant or organization | | | | |
| Capability and purpose | | | | |
| Business identity/idempotency | | | | |
| Preconditions and invariants | | | | |
| Accepted versus completed | | | | |
| Denied and unknown outcomes | | | | |
| Rate, quota, and cost boundary | | | | |
| Evidence and correlation | | | | |

Any `changed` row creates a new contract decision. Do not hide it inside adapter
code or a more conversational tool description.

## 5. Define authority before agent behavior

- **Immediate actor:** person / fixed application / agent
- **Client presenting the MCP request:**
- **Principal whose authority is represented:**
- **Affected subject or business party:**
- **Tenant, organization, or account boundary:**
- **Source of delegated authority:**
- **Permitted purpose:**
- **Permitted objects, quantities, values, or action classes:**
- **Time, location, and context boundary:**
- **Revocation source and enforcement point:**
- **What the model may propose but not execute:**
- **What always requires confirmation or independent approval:**
- **What no person or agent may perform through this tool:**

A model selecting a visible tool is not an authorization decision. The
enforcement point must decide whether this actor may exercise this capability
for this principal, subject, tenant, purpose, and moment.

## 6. Bound the agent's decision

Complete this section only when an agent, rather than a fixed application path
or direct user choice, may select or sequence the tool.

- **Goal the agent may pursue:**
- **Information the agent may use:**
- **Information it must not receive or infer authority from:**
- **Tool-selection policy:**
- **Maximum action count, value, cost, or affected scope:**
- **Deadline or action budget:**
- **Required confirmation experience:**
- **Stop conditions:**
- **Escalation destination:**
- **Human or workflow owner after escalation:**
- **Prohibited tool sequences or loops:**
- **Evidence required before autonomy may expand:**

## 7. Preserve repetition, conflict, and outcome certainty

- **Business identity or idempotency key:**
- **How repeated agent plans map to the same or different business intent:**
- **Concurrency and stale-state rule:**
- **Timeout before provider acceptance:**
- **Timeout after possible effect:**
- **Safe reconciliation path:**
- **When automated retry is allowed:**
- **When retry must stop:**
- **How an unknown outcome is represented to the AI application and person:**
- **How tool, API, workflow, event, and outcome identities correlate:**

Never turn “the model can try again” into a retry policy for a consequential
business action.

## 8. Route facts and continuing responsibility

- **Facts the capability may produce:**
- **Authority permitted to declare each fact:**
- **Events published, if any:**
- **Open promise after the API response:**
- **Durable workflow responsible for progress, if any:**
- **Workflow owner and terminal outcomes:**
- **Human approval or exception step:**
- **How the requester discovers current and final outcome:**
- **What the agent may do after acceptance but before completion:**
- **What the agent may do after an unknown outcome:**

The MCP call is not the workflow, and the agent should not improvise ownership
of work that must survive its session.

## 9. Protect data, capacity, and operations

- **Data classification of inputs and outputs:**
- **Fields prohibited from model context, logs, or tool results:**
- **Output sanitization and disclosure rules:**
- **Rate, quota, concurrency, and cost boundaries:**
- **Abuse and anomalous-sequence controls:**
- **Dependency and capacity exhaustion behavior:**
- **Operational owner:**
- **Support and incident route:**
- **Retention and deletion requirements:**
- **Emergency narrowing or disable mechanism:**

## 10. Design the evidence before release

| Question to prove or disprove | Required evidence | Deliberate failure or mutation | Status/result | What remains unproved | Owner |
| --- | --- | --- | --- | --- | --- |
| Was the tool shown only to an eligible consumer? | | | planned/unrun/pass/fail/unknown | | |
| Did the exact actor have authority for the principal, subject, tenant, and purpose? | | | | | |
| Did the tool preserve the API's business meaning? | | | | | |
| Did one business intent produce the promised number of effects? | | | | | |
| Did confirmation or approval occur where required? | | | | | |
| Could the person interpret accepted, completed, denied, and unknown outcomes? | | | | | |
| Did events declare only facts that occurred? | | | | | |
| Did the workflow retain every open promise? | | | | | |
| Can an authorized reviewer reconstruct the decision and outcome? | | | | | |
| Can the system stop, narrow, revoke, or recover the capability? | | | | | |

### Required provenance chain

- **User or system intent reference:**
- **Agent decision or fixed routing decision:**
- **Approval or confirmation reference:**
- **MCP host, client, server, tool, and protocol versions:**
- **Tool inputs and bounded result:**
- **Underlying API request and contract version:**
- **Delegation and policy-decision references:**
- **Workflow and event identifiers, if used:**
- **Authoritative business outcome:**
- **Consumer communication:**
- **Retention and access policy:**

## 11. Stop, release, and reversal record

- **Decision:** hold / prototype / release narrowly / release / reverse
- **Exact consumers and conditions covered:**
- **Evidence gates passed:**
- **Evidence gates failed or unrun:**
- **Residual uncertainty and consequence:**
- **Operational and business owner:**
- **Automatic stop conditions:**
- **Manual disable or narrowing path:**
- **Reversal trigger:**
- **Expansion trigger and required evidence:**
- **Decision authority, date, and retained record:**

## Completion challenge

Ask a product or operations colleague to read only Sections 1, 2, 5, 8, and 11.
Can they explain what becomes possible, who may cause it, who remains
responsible, what can go wrong, and what evidence would stop release? If not,
the brief is not yet ready to direct implementation.
