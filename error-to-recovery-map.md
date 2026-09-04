# Error-to-Recovery Map

Use this before assigning transport codes or generating an error schema.

## Status and purpose

**Use boundary:** Illustrative field tool; independent-practitioner use remains
unrun. Completion is not certification or proof of production fitness.

The map tests whether every published failure gives the consumer a safe,
bounded next action without exposing protected information or unstable
implementation detail.

It does not prove that an error classification is complete, secure, or
appropriate for every API. Validate it against representative consumers,
failure injection, authorization policy, and operational recovery.

## 1. Capability and outcome boundary

- **Capability:**
- **Operation under review:**
- **Consumer decision after the response:**
- **Business identity that survives retry or reconciliation:**
- **Acceptance boundary:**
- **Authoritative outcome source:**
- **Operational owner:**

## 2. Recovery actions

Define what each verb means for this contract. Remove any action that is not
allowed; add domain-specific actions when needed.

| Action | Meaning in this contract | Who may take it | Identity rule | Stop condition |
| --- | --- | --- | --- | --- |
| Correct | | | | |
| Obtain authority | | | | |
| Refresh state | | | | |
| Retry | | | | |
| Wait or observe | | | | |
| Reconcile | | | | |
| Escalate | | | | |
| Stop | | | | |

## 3. Error-to-recovery decisions

Do not fill the first column with exception class names. Use stable meanings a
consumer may rely on.

| Public outcome | Meaning to consumer | Accepted responsibility? | Can an effect already exist? | Safe consumer action | Identity and timing rule | Public detail | Protected evidence | Provider owner |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Invalid request | | yes/no | yes/no/unknown | | | | | |
| Not authorized | | | | | | | | |
| Conflict or stale state | | | | | | | | |
| Unavailable before acceptance | | | | | | | | |
| Accepted but incomplete | | | | | | | | |
| Terminal business rejection | | | | | | | | |
| Unknown outcome | | | | | | | | |

## 4. Disclosure check

For every public detail, ask:

- Does the consumer need this information to make the allowed recovery
  decision?
- Is the caller authorized to know whether the referenced subject, object, or
  policy exists?
- Does the detail expose internal topology, dependency names, stack traces,
  secrets, protected data, or a probing oracle?
- Will a consumer couple to an implementation category that may disappear?
- Can a safe correlation reference replace raw diagnostic detail?
- Does the protected evidence still let an authorized operator reconstruct the
  decision?

## 5. Failure evidence

| Mutation | Expected consumer behavior | Invariant | Evidence | Result | What the result does not prove |
| --- | --- | --- | --- | --- | --- |
| Invalid field or business precondition | | | | pass/fail/unknown | |
| Unauthorized actor, subject, tenant, or purpose | | | | | |
| Stale version or competing transition | | | | | |
| Timeout before durable acceptance | | | | | |
| Timeout after a possible external effect | | | | | |
| Duplicate response or request | | | | | |
| Partial item completion | | | | | |
| Accepted work exceeds its deadline | | | | | |
| Protected subject does not exist versus is merely forbidden | | | | | |

## 6. Release decision

- **Errors that support one safe action:**
- **Errors that still force the consumer to guess:**
- **Information-disclosure failures:**
- **Accepted or unknown outcomes without an owner:**
- **Evidence gaps that block release:**
- **Hold, revise, or release:**
- **Evidence that would reverse the decision:**

## Guardrails

- “Transient” is a recovery promise, not a synonym for an exception or
  dependency failure.
- “Terminal rejection” can be a completed business outcome.
- A timeout can conceal an existing effect.
- More detail is not automatically more useful.
- Less detail is not automatically safer when it makes recovery impossible.

## Final review question

Can a representative consumer choose one or more explicitly permitted actions
for every public outcome, under stated conditions and with a clear stop rule,
without knowing the provider's internal architecture?
