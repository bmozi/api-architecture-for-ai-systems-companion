# AI-Ready OpenAPI Implementation Brief

This brief directs generation after the capability contract is approved. It is
not a substitute for the Meaning-and-Authority Brief.

**Status:** Working companion asset; independent practitioner usability remains
untested.

## Approved inputs

- **Meaning-and-Authority Brief version:**
- **Domain vocabulary and definitions:**
- **Representative consumer journeys:**
- **Identity and authorization model:**
- **Data classification and prohibited fields:**
- **Compatibility baseline:**
- **Operational constraints:**

## Artifacts requested from AI

- [ ] OpenAPI specification
- [ ] provider interface or service shell
- [ ] client example
- [ ] contract tests
- [ ] failure and recovery tests
- [ ] authorization tests
- [ ] compatibility tests or diff rules
- [ ] observability design
- [ ] decision and assumption report

## Non-negotiable contract rules

- **Capability outcome:**
- **Actor/subject/tenant authority:**
- **Accepted versus completed meaning:**
- **Idempotency and concurrency:**
- **Error classes and safe recovery:**
- **Rate, quota, and abuse behavior:**
- **Compatibility and deprecation:**
- **Data exposure and privacy:**
- **Required evidence:**

## Generation constraints

- Do not invent business states, roles, permissions, error semantics, or
  compatibility promises.
- Represent unknowns explicitly.
- Do not convert an asynchronous or durable outcome into a synchronous success
  response for implementation convenience.
- Do not expose internal tables or services unless the approved capability
  contract requires that representation.
- Preserve provenance from each generated artifact to this brief and its
  approved inputs.

## Stop and escalate when

- authority or ownership is ambiguous;
- accepted and completed outcomes cannot be distinguished;
- idempotency or concurrency behavior is unspecified;
- the requested interface conflicts with data classification or policy;
- compatibility depends on an unverified consumer assumption;
- generated tests cannot observe the required business outcome; or
- an implementation choice would silently change the approved contract.

## Unknown register

Do not replace undecided policy or operational facts with plausible defaults.

| Unknown question | Consumer/operator consequence | Decision authority | Artifact or behavior blocked | Bounded placeholder permitted? | Evidence required to close | Current decision state |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | yes/no | | open/decided/retired |

## Stop and escalation ledger

| Trigger observed | Affected artifact or behavior | Release consequence | Owner/decision authority | Clearing evidence | Current state |
| --- | --- | --- | --- | --- | --- |
| | | hold/narrow/reverse/escalate | | | open/cleared/accepted risk |

## Provenance and freeze record

- **Capability-brief version and hash:**
- **Implementation-brief version and hash:**
- **Specification baseline/version and hash:**
- **Prompt or structured input version and hash:**
- **Tool/model/generator identity and configuration:**
- **Raw output version and hash:**
- **Generation date and environment:**
- **Reviewers, roles, and decision authority:**
- **Correction lineage and current candidate:**
- **Rejected alternatives and governing reasons:**
- **Release-evidence package reference:**

Preserve the raw output. Correct a new version rather than rewriting the
evidence of what generation originally produced.

## Verification and independence plan

| Evidence layer | Source/author/generator and authoritative input | Shared fixture or assumption provenance | Required test or observation | Failure mutation | Status and observed result | Retained artifact | Green blind layers | What this does not establish | Owner/interpreter authority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Schema | | | | | planned/unrun/pass/fail/unknown | | | | |
| Behavior | | | | | | | | | |
| Semantics | | | | | | | | | |
| Authorization | | | | | | | | | |
| Idempotency/concurrency | | | | | | | | | |
| Consumer compatibility | | | | | | | | | |
| Failure/recovery | | | | | | | | | |
| Outcome evidence | | | | | | | | | |
| Operations | | | | | | | | | |

Different layer names do not make evidence independent. Where consequence
warrants it, include counterevidence derived from an independently owned
consumer expectation, policy authority, or authoritative outcome source.

## Release record

- **Decision:** hold / release / narrow / reverse / expand
- **Artifacts and versions covered:**
- **Evidence gates passed:**
- **Evidence gates failed or still unrun:**
- **Residual uncertainty and consequence:**
- **Operational owner:**
- **Consumer population and conditions represented:**
- **Population and conditions not represented:**
- **Reversal or narrowing trigger:**
- **Expansion trigger and required evidence:**
- **Decision authority, date, and retained record:**

## Completion rule

Generation is complete only when requested artifacts exist. The capability is
ready only for the exact release boundary recorded above when its evidence
floor passes and remaining uncertainty has an owner, consequence, and reversal
decision. Completion of this blank is not practitioner-usability or release
evidence.
