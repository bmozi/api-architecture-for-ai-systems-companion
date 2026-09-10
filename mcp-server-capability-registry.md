# MCP Server and Capability Registry

Use this registry to govern an MCP server fleet. One row represents a business
capability surface, not merely a process, repository, or URL. A server may
contain several related surfaces only when one accountable owner can defend
their boundaries and lifecycle.

This is a design and operating record, not proof that a server is safe. Mark
each field `planned`, `unrun`, `pass`, `fail`, or `unknown`, and retain the
evidence behind the mark.

## Registry record

**Capability ID and version:**  
**MCP server name and version:**  
**Environment and endpoint/transport:**  
**Business capability and one-sentence outcome:**  
**In scope:**  
**Out of scope:**  
**Business owner:**  
**Technical owner:**  
**Security/privacy owner:**  
**Support and escalation owner:**  
**Canonical authority for each material fact:**  
**Consumers and approved hosts:**  
**Tenant and purpose boundary:**  
**Data classification:**  
**Protocol revision and SDK/implementation versions:**  
**Status:** planned / pilot / operating / suspended / retired  

## Surface inventory

| Name | Primitive | User outcome | Read/mutate | Underlying API or workflow | Authority check | Confirmation | Cost/limit | Evidence | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | tool/resource/prompt | | | | | | | | |
| | | | | | | | | | |

Reject names that describe a table, URL, generic HTTP call, or unrestricted
database access when the user actually needs a business outcome.

## Admission and review

- Is the business outcome understood without mentioning the server internals?
- Is the capability owner accountable for denied, delayed, duplicated, and
  unknown outcomes?
- Are actor, principal, subject, tenant, purpose, delegation, and revocation
  enforced at the consequential action?
- Does the surface preserve the underlying contract, or intentionally narrow it
  with an approved decision?
- Are tool descriptions, schemas, resources, prompts, and output annotations
  reviewed as potentially influential input rather than trusted authority?
- Are sensitive data, credentials, network destinations, and logs bounded?
- Can the server be disabled without leaving an unowned in-flight effect?
- Is a rollback, reconciliation, and retirement path named?

If an accountable owner is missing, hold admission until one accepts the
responsibility. A workflow preserves assigned responsibility; it does not
supply a missing owner. A read-only alternative is a separate proposal that
still needs an owner, purpose, access controls, and capacity budget.

## Lifecycle and portfolio decisions

**Duplicate or overlapping server/tool:**  
**Decision:** merge / retain separately / narrow / retire / unknown  
**Reason and evidence:**  
**Version-compatibility promise:**  
**Deprecation notice and consumer migration:**  
**Disablement trigger:**  
**Retirement evidence required:**  
**Next review date:**  

## Evidence links

Record the inventory source, authority decision, threat model, contract tests,
mutation results, deployment approval, monitoring dashboard, incident history,
and independent review. A green registry row without linked evidence is an
unproved claim.
