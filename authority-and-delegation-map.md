# Authority and Delegation Map

Use this to define who may exercise one consequential capability for whom,
under which authority and time boundary.

## Status and evidence boundary

**Status:** Working companion asset; independent use and executable mutation
testing remain open.

This map does not make policy legitimate or complete. The accountable business,
security, contractual, legal, and operational authorities must approve the
rules that apply.

## 1. Capability and decision

- **Capability and operation:**
- **Business consequence:**
- **Protected action:**
- **Protected object or resource:**
- **Subject or party affected:**
- **Purpose:**
- **Tenant definition for this decision:**
- **Contract owner:**
- **Authority owner:**

Write the complete approved statement:

> Actor [ ] using client [ ] may perform action [ ] for subject [ ] on object
> [ ] in tenant [ ] for purpose [ ] because delegation [ ] and policy version
> [ ] are valid under context [ ].

## 2. Identity and authority roles

| Role | Identifier/source | Authority it carries | Authority it does not carry | Owner |
| --- | --- | --- | --- | --- |
| Immediate actor | | | | |
| Represented principal | | | | |
| Subject affected | | | | |
| Client/application | | | | |
| Consumer organization | | | | |
| Delegating party | | | | |
| Provider | | | | |
| Object/resource authority | | | | |
| Tenant authority | | | | |

Do not use the same bare word `subject` for token subject, access-control
subject, event subject, and affected business party without mapping them.

## 3. Delegation chain

| Hop | Delegator/principal | Actor/client | Allowed capability, subject, object, tenant, and purpose | May redelegate? | Starts/expires | Revocation source | Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | | | | | | | |
| 2 | | | | | | | |
| 3 | | | | | | | |

At each hop, state whether authority narrows, remains equal, or broadens. Any
broadening requires explicit legitimate authority and review.

## 4. Policy responsibilities

| Responsibility | Accountable role/system | Authority source | Version/evidence | Failure owner |
| --- | --- | --- | --- | --- |
| Policy definition | | | | |
| Policy administration | | | | |
| Attribute/information source | | | | |
| Policy decision | | | | |
| Enforcement at API boundary | | | | |
| Enforcement at data/effect boundary | | | | |
| Denial and consumer recovery | | | | |
| Investigation and dispute | | | | |

## 5. Time, caching, and revocation

- **When authority is evaluated:**
- **Facts snapshotted at acceptance:**
- **Facts rechecked before later consequential action:**
- **Allowed cache lifetime and stale behavior:**
- **Revocation authority and propagation path:**
- **Work accepted before revocation:**
- **Work not yet consequential at revocation:**
- **Compensation, cancellation, or escalation owner:**

## 6. Authorization-evidence governance

- **Approved purpose for retaining the authority tuple:**
- **Minimum representation or protected references:**
- **Classification:**
- **Roles permitted to read, join, export, or correct it:**
- **Integrity and alteration evidence:**
- **Retention and disposal rule, including copies:**
- **Prohibited raw tokens, credentials, payloads, or policy internals:**
- **What becomes unprovable after disposal:**

## 7. Mutation plan

| Mutation | Expected decision | Effect that must not occur | Public response boundary | Protected evidence | Result |
| --- | --- | --- | --- | --- | --- |
| Valid actor, unauthorized object | deny | | | | unrun |
| Valid function, wrong tenant | deny | | | | unrun |
| Correct object, unauthorized action | deny | | | | unrun |
| Delegation for wrong purpose | deny | | | | unrun |
| Expired or revoked delegation | governed rule | | | | unrun |
| Internal service with broader identity | no authority broadening | | | | unrun |
| Policy or attribute source stale/unavailable | fail/limit/escalate as approved | | | | unrun |
| Denied caller probes object existence | no prohibited disclosure | | | | unrun |

## 8. Decision

- **Approved authority paths:**
- **Denied paths:**
- **Unknown or disputed authority:**
- **Evidence gaps:**
- **Release blockers:**
- **Evidence that would reverse this decision:**

## Final review question

If a valid caller changes only the buyer, object, tenant, purpose, delegation,
or time, which explicit decision prevents the capability from crossing its
legitimate authority boundary?
