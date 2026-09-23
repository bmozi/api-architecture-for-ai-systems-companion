# API Architecture Gap-Closing Workbook

Use this workbook to turn a large API estate into a smaller, governed set of
business capabilities and, where justified, carefully bounded AI surfaces. It
extends the book's **Capability and Authority Contract** as an illustrative
field tool.

This is a design and learning aid, not proof that a production architecture is
safe, authorized, reliable, or economically worthwhile. Mark each conclusion
`planned`, `unrun`, `pass`, `fail`, or `unknown`; attach the evidence and keep
negative results. A constructed example can teach a method, but cannot prove a
real organization's readiness.

## The outcome in plain language

The goal is not to turn 2,100 APIs into 2,100 MCP tools. That would move API
sprawl into an AI tool catalog. The goal is to make the business outcome,
authority, limits, and evidence understandable enough that a person,
automation, or agent can act without guessing.

```text
API estate
  -> inventory, deduplicate, classify, and find authority
Business capability map
  -> name outcomes, boundaries, owners, and policy
Capability façade or adapter
  -> preserve identity, authorization, evidence, recovery, and cost
API, event, workflow, resource, or MCP tool
  -> expose only the role that is actually needed
Consumer or agent
  -> invoke within explicit authority and stopping rules
```

## 1. Establish the capability contract

**Record ID and version:**  
**Date and participants:**  
**Status:** planned / discovery / designed / piloting / operating / retired  
**Business capability:**  
**One-sentence outcome:**  
**Plain-language explanation:**  
**Person, team, partner, or system that needs the outcome:**  
**Situation that creates the need:**  
**Cost of a wrong, late, duplicated, or misleading outcome:**  
**In scope:**  
**Explicitly out of scope:**  
**Related capabilities and handoffs:**  
**Bounded context or domain boundary:**  

Explain the capability without saying “the API does X.” An API is machinery;
the capability is the valuable and governed result.

| Contract element | Decision | Owner | Evidence or open question | Status |
| --- | --- | --- | --- | --- |
| Business outcome | | | | |
| Subject and affected parties | | | | |
| Canonical authority | | | | |
| Permitted purpose | | | | |
| Actor and delegated principal | | | | |
| Success and completion meaning | | | | |
| Failure, uncertainty, and stopping rule | | | | |
| Reversal, correction, or dispute path | | | | |

## 2. Inventory and corral the estate

Attach a catalog export, system diagram, or query results. Include unhealthy,
undocumented, duplicated, and apparently abandoned APIs; missing information is
itself a finding.

| API or operation | Version | Read/mutate | Business outcome | Claimed authority | Actual authority | Consumers | Owner | Overlap/duplicate | Evidence/status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | | | |
| | | | | | | | | | |
| | | | | | | | | | | |

For every candidate, ask:

- Does it name a stable promise or only a resource, table, or URL?
- Which system may create or change the authoritative business fact?
- Can another endpoint perform the same action with different rules?
- Are apparent duplicates intentional, accidental, or unknown?
- Where are tenant, actor, purpose, idempotency, evidence, and outcome state
  represented?
- What happens when a call is repeated, times out, or errors after the provider
  may already have acted?

Do not deduplicate by matching names alone. Two operations called `reserve` may
have different subjects, authority, timing, or promises. Different names may
still mutate the same fact.

**APIs grouped into this capability:**  
**APIs left outside and why:**  
**Competing authorities or unresolved duplicates:**  
**Missing inventory, owner, or evidence:**  
**Corral decision and decision owner/date:**  

## 3. Select the architectural role

| Need or promise | API | MCP tool | MCP resource | Event | Durable workflow | Human/agent decision | Why |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Read an authorized current view | | | | | | | |
| Request an immediate governed action | | | | | | | |
| Notify that a fact occurred | | | | | | | |
| Continue work across time/retries | | | | | | | |
| Choose among permitted next actions | | | | | | | |
| Reconcile an unknown result | | | | | | | |

**Primary capability façade or API:**  
**Why an MCP surface is or is not needed:**  
**Proposed tools and resources:**  
**What remains outside the AI surface:**  
**Revisit trigger:**  

Prefer a business operation over CRUD. A server must not become a generic SQL
endpoint, arbitrary HTTP proxy, unrestricted search interface, or hidden
orchestrator. A tool's existence does not grant authority to its caller.

## 4. Define identity, authority, and outcomes

Write the complete authority statement:

> Actor `[ ]`, using client `[ ]`, may perform `[action]` for subject `[ ]` on
> object `[ ]` in tenant `[ ]` for purpose `[ ]` because delegation `[ ]` and
> policy version `[ ]` are valid in context `[ ]`.

| Role or fact | Identifier/source | Authority carried | Authority not carried | Owner/evidence |
| --- | --- | --- | --- | --- |
| Immediate actor | | | | |
| Represented principal | | | | |
| Affected subject | | | | |
| Client/host/agent | | | | |
| Delegating party | | | | |
| Tenant authority | | | | |
| System of record | | | | |

| State | Exact meaning here | Who may declare it | Durable evidence | Safe next action |
| --- | --- | --- | --- | --- |
| Received | | | | |
| Accepted | | | | |
| Pending | | | | |
| Completed | | | | |
| Denied/rejected | | | | |
| Unknown after timeout | | | | |
| Reversed/corrected | | | | |

Record where authority is evaluated, which facts are rechecked before effect,
how revocation propagates, and who owns work accepted before revocation.

## 5. Design and govern the AI surface

If no consumer needs an AI surface, record that decision and skip this section.
A conventional API can remain the appropriate interface.

| Tool/resource | User outcome | Read/mutate | Inputs/scope | Authority check | Confirmation | Output/evidence | Stop/failure rule |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |

For each proposed surface:

**Name and model-visible description:**  
**Use when / do not use when:**  
**Input validation and data intentionally omitted:**  
**Underlying API/adapter and outcome mapping:**  
**Protocol errors versus business errors:**  
**Idempotency and correlation identifiers:**  
**Rate, value, quantity, and concurrency limits:**  
**Owner, versioning, deprecation, and emergency disablement:**  
**Human confirmation or independent approval:**  

### Small-surface release test

Mark each `yes`, `no`, or `unknown` and attach evidence:

- A reader can name the business outcome in one sentence.
- The name describes an outcome rather than an internal table or URL.
- One accountable authority and owner are clear.
- The surface is narrower than the technical access underneath.
- Accepted, completed, denied, and unknown are distinguishable.
- Repeated intent cannot silently create a duplicate effect.
- Sensitive data is minimized and purpose-bound.
- A safe stop, reconciliation, and human escalation path exists.

Any `no` or `unknown` is a decision or release boundary, not something to hide
in prose.

## 6. Migration and coexistence plan

| Wave | Capability slice | Existing consumers | New façade/surface | Authority during coexistence | Compatibility evidence | Rollback/reconciliation | Exit condition |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0: discover | | | | | | | |
| 1: shadow/read | | | | | | | |
| 2: bounded action | | | | | | | |
| 3: expand | | | | | | | |
| 4: retire or retain | | | | | | | |

Answer explicitly:

- Which path is authoritative while old and new paths coexist?
- How are duplicate side effects prevented?
- How are old clients warned, migrated, or kept intentionally?
- How are unknown outcomes reconciled before retry?
- What evidence permits retirement, and what would reverse it?

## 7. Fleet, threat, geography, and economics review

| Review area | Decision or constraint | Owner | Test/evidence | Status |
| --- | --- | --- | --- | --- |
| MCP server registry and capability ID | | | | |
| Duplicate/overlapping tool admission | | | | |
| Tool poisoning and prompt injection | | | | |
| Identity/delegation and confused deputy | | | | |
| Cross-tenant/data leakage | | | | |
| Supply chain and outbound network | | | | |
| Region, residency, sovereignty, and failover | | | | |
| Token/context and hosting cost | | | | |
| Rate, quota, concurrency, fairness | | | | |
| Expensive/irreversible action approval | | | | |
| Observability, evidence, and retirement | | | | |

For regional or data-boundary decisions, name where data, prompts, tool
descriptions, logs, cached resources, task results, and backups may travel.
For economics, record the cost of discovery, invocation, retries, review,
hosting, and failure—not only the API gateway bill.

## 8. Evidence and adversarial release gate

| Claim or promise | Claim class | Test or source | Result | What remains unproved |
| --- | --- | --- | --- | --- |
| Protocol/schema conforms | observed/tested | | | |
| Caller is authorized | observed/tested | | | |
| Outcome semantics are correct | observed/tested | | | |
| Unknown-after-effect is recoverable | tested/unrun | | | |
| Tenant and purpose boundaries hold | tested/unrun | | | |
| Tool descriptions resist poisoning | tested/unrun | | | |
| Capacity and cost are acceptable | measured/estimated | | | |
| Business value is realized | reported/inferred | | | |

At minimum, test unauthorized subject/tenant/purpose, expired delegation,
replayed intent, timeout-after-effect, partial multi-server success, stale
resource, prompt injection, malicious tool description, server loss, reconnect,
and emergency disablement. Record negative and unrun results. Local tests do
not establish independent practitioner usability, production safety, or market
demand.

## 9. 30/60/90-day small-start adoption path

| Horizon | Deliverable | Scope and owner | Evidence required | Stop/expand decision |
| --- | --- | --- | --- | --- |
| Days 0–30 | Choose one capability; inventory APIs; name authority, risk, and outcome states | | | |
| Days 31–60 | Build a read-first façade or narrow tool; run identity, boundary, replay, and unknown-outcome tests | | | |
| Days 61–90 | Pilot with bounded consumers; measure usefulness, latency, cost, denials, recovery, and operator burden | | | |

Do not expand because a demo worked. Expand only when the evidence supports the
next scope, the owner accepts residual risk, and a reversal path exists. If the
small slice fails, preserve the failure and revise the capability boundary.

## Final handoff: explain it without the machinery

Explain the completed record to someone unfamiliar with the platform:

1. What valuable result does this capability produce?
2. Who may cause it, for whom, and under what purpose?
3. Which system is allowed to say what happened?
4. What may a consumer safely do after each outcome state?
5. What happens when the call is late, repeated, replayed, forged, revoked, or
   generated by an AI participant?
6. What evidence would make us stop or reverse the rollout?

If the explanation depends on a vendor name, endpoint nickname, or product
feature, the architecture is not yet portable.
