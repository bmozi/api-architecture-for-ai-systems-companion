# API Architecture for AI Systems — Companion

**Series:** *AI Systems Architecture Field Guides*
Turn one useful business capability into a promise that applications,
partners, automation, MCP clients, and AI agents can reuse without inventing
their own meaning, authority, or recovery rules.

## The problem you may recognize first

You may have arrived because you need an integration, an MCP server, a generated
SDK, or a safer way for an agent to update a system. If each consumer receives a
different route, meaning of success, or authority model, the problem is API
architecture before it is implementation.

This companion helps you produce a first reviewable result. It does not certify
an API, implementation, organization, or AI tool as secure, correct, or ready
for production.

## The book-and-companion contract

- **The book teaches the judgment:** what capability should exist, what the
  contract means, where authority stops, how failure affects consumers, and
  what evidence is persuasive.
- **The companion provides the moves:** blank templates, completed examples,
  decision guides, mutation exercises, and evidence records.
- **The book is required for the full exercise:** read the relevant chapter
  before using a worksheet. The book supplies the reasoning, story, tradeoffs,
  and evidence boundaries; this repository makes that judgment practice
  inspectable. The repository is not a substitute for the book.

## Start here

Use [START-HERE.md](START-HERE.md) to take one capability through a thirty-minute
first pass. You will produce a five-sentence capability promise and decide
whether the surrounding design also needs an MCP tool, event, workflow, or
agent.

For the intended result, keep *API Architecture for AI Systems* beside this
exercise and use [BOOK-TO-COMPANION-MAP.md](BOOK-TO-COMPANION-MAP.md) to read the
relevant chapter first. A completed worksheet without that chapter context is
a draft for discussion, not a complete architecture decision.

## Core assets

| Need | Start with |
| --- | --- |
| Define the capability and authority | [API Meaning-and-Authority Brief](api-meaning-and-authority-brief.md) |
| Choose API, MCP tool, event, workflow, or agent roles | [Interaction Decision Guide](api-event-workflow-decision-tree.md) |
| Expose an approved API to AI clients | [Agent-Ready API and MCP Capability Brief](agent-ready-api-and-mcp-capability-brief.md) |
| Direct generated API implementation | [AI-Ready OpenAPI Implementation Brief](ai-ready-openapi-implementation-brief.md) |
| Make failure usable to consumers | [Error-to-Recovery Map](error-to-recovery-map.md) |
| Test duplicates and unknown outcomes | [Idempotency and Outcome Test Matrix](idempotency-and-outcome-test-matrix.md) |
| Prove compatibility and outcomes | [Compatibility Evidence Matrix](compatibility-evidence-matrix.md) and [Outcome Evidence Map](outcome-evidence-map.md) |
| Separate fast lookup from a valid transaction | [Northbridge Data-Structures Architecture Bridge](examples/northbridge-data-structures-architecture-bridge.md) |

Use [INDEX.md](INDEX.md) for role- and outcome-based routes and
[BOOK-TO-COMPANION-MAP.md](BOOK-TO-COMPANION-MAP.md) to reconnect each tool to
the book's reasoning.

## Use it across roles

[Role-Based Paths](ROLE-BASED-PATHS.md) connect the technical tools to developer,
architect, manager, and executive decisions. The [Team Workshop](TEAM-WORKSHOP.md),
[Value and Evidence Ledger](VALUE-AND-EVIDENCE-LEDGER.md),
[Executive Decision Brief](EXECUTIVE-DECISION-BRIEF.md), and
[Failure Lab](FAILURE-LAB.md) turn one capability into a cross-role review.
The [Pilot and Usability Route](PILOT-AND-USABILITY.md) and reader-value packet
version 1.2.6 remain prepared and unrun with human participants. Version 1.2.6
preserves the complete version 1.2.5 closure contract and makes entry-branch
selection precede run start in both machine and reader-facing routes. The exact
five-member Stage A revision binding remains unchanged. Real-world evidence
remains unrun.

## Imagine and shape what comes next

Use the [Responsible Amplification and Possible Futures
Card](examples/responsible-amplification-and-possible-futures-card.md) to begin
with a beneficial possibility, trace bias and consequences through the whole
system, compare three plausible futures, and turn one future signal into a
reversible present decision. It is `PLANNED/UNRUN` and does not prove a
forecast, fairness, safety, legality, effectiveness, or reader learning.

## Evidence and use boundary

This is the public reader companion to *API Architecture for AI Systems*. It provides
editable tools and constructed examples; it does not certify a design,
implementation, organization, or AI system as safe, lawful, effective, or
production-ready. Preserve every `constructed`, `scenario`, `planned`,
`unrun`, `observed`, `tested`, `reported`, `inferred`, and `unknown`
label when adapting the material.

Written content is available under
[CC BY 4.0](LICENSE-CONTENT), and executable code is available under the
[Apache License 2.0](LICENSE-CODE). Source lineage is recorded in
[PROVENANCE.md](PROVENANCE.md); local integrity checks are documented in
[VALIDATION.md](VALIDATION.md). Human learner and practitioner validation
remains a separate evidence gate.

## Continue through the series

The five public companions follow the same evidence-bounded field-guide model:

1. [API Architecture for AI Systems](https://github.com/bmozi/api-architecture-for-ai-systems-companion)
2. [Event-Driven Architecture for AI Systems](https://github.com/bmozi/event-driven-architecture-for-ai-systems-companion)
3. [Durable Workflows for AI Systems](https://github.com/bmozi/durable-workflows-for-ai-systems-companion)
4. [Data Platform Architecture for AI Systems](https://github.com/bmozi/data-platform-architecture-for-ai-systems-companion)
5. [Agentic Systems Architecture](https://github.com/bmozi/agentic-systems-architecture-companion)
