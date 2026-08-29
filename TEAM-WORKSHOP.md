# API Capability Decision Workshop

**Duration:** 75 minutes
**Status:** Prepared and unrun
**Outcome:** One capability decision with named authority, failure, evidence,
owners, and next review date

This workshop is not an API design approval, security review, production test,
or measured benefit claim.

## Participants

Invite the smallest group that can answer the real questions:

- capability or product owner;
- provider engineer;
- representative consumer;
- security or identity reviewer;
- operations or support representative; and
- facilitator who is not rewarded for approving the design.

## Before the meeting

Bring one sentence describing the beneficiary and outcome. Do not bring a
finished endpoint diagram as the definition of the problem.

Copy blank versions of the [Meaning-and-Authority Brief](api-meaning-and-authority-brief.md),
[interaction decision guide](api-event-workflow-decision-tree.md), and
[Value and Evidence Ledger](VALUE-AND-EVIDENCE-LEDGER.md).

## Agenda

### 0–10 minutes: name the value

- Who benefits?
- What can they do afterward that they cannot do dependably now?
- What current delay, workaround, duplicate effort, or risk is visible?

### 10–25 minutes: write the promise

- What capability is being requested?
- What does each successful, rejected, failed, accepted, or unknown outcome
  permit the consumer to promise next?
- Which business meaning must not be inferred from transport success?

### 25–40 minutes: expose authority and composition

- Who is actor, principal, subject, provider, and consumer?
- Does AI need an MCP tool, or only an existing application path?
- Which facts belong in events and which unfinished promise belongs in a
  workflow?
- Which data product supplies information and for which named use?

### 40–55 minutes: interrupt the happy path

Use the [Failure Lab](FAILURE-LAB.md). Require an answer for duplicate intent,
timeout after effect, stale authorization, incompatible change, and missing
outcome evidence.

### 55–68 minutes: define evidence and ownership

- Which contract, consumer, mutation, and operational evidence is required?
- Who owns each unknown?
- Which result forces the team to narrow, hold, or stop?

### 68–75 minutes: make the next decision

Choose one: `EXPLORE`, `PROCEED BOUNDED`, `INVEST`, `HOLD`, or `STOP`.
Record owner and review date. Do not use “approved pending details.”

## Required outputs

- completed or explicitly incomplete capability brief;
- selected architecture roles and handoffs;
- one tested or planned failure path;
- value-and-evidence ledger;
- named owners for unknowns; and
- dated next decision.

## Facilitator stop conditions

Stop and record the gap when the group cannot name the beneficiary, provider,
consumer promise, authority, authoritative outcome source, or owner of an
unknown. A stopped workshop can be a successful discovery.
