# API Reader-Value Pilot Packet

**Packet ID:** API-RV-PILOT-001
**Version:** 1.0.0
**Status:** Prepared and unrun; no participant recruited or consented
**Scenario:** Stonebridge Equipment Rental, entirely fictional

## What this packet tests

This packet tests the complete reader-value chain for one API-first capability:

`RECOGNITION -> PLAIN EXPLANATION -> FIRST ARTIFACT -> FAILURE DISCOVERY ->`
`OUTSIDE READ-BACK -> CROSS-ROLE DECISION -> NEXT EVIDENCE`

It does not replace the older Cedarway technical-transfer packet. Cedarway
retains its frozen pre-MCP API/event/workflow scope. This packet separately
tests the newer Agent-Ready API and MCP Capability Brief, role paths, failure
lab, value ledger, and executive decision language.

## Two stages

### Stage A — practitioner

Supply only:

1. [Consent and privacy notice](participant/01-consent-and-privacy.md)
2. [Scenario and task](participant/02-scenario-and-task.md)
3. [Practitioner workbook](participant/03-practitioner-workbook.md)
4. [Start Here](../../START-HERE.md)
5. [Agent-Ready API and MCP Capability Brief](../../agent-ready-api-and-mcp-capability-brief.md)
6. [API, MCP Tool, Event, Workflow, or Agent Decision Guide](../../api-event-workflow-decision-tree.md)

Do not supply completed examples, the repository failure lab, facilitator
materials, the executive brief, or the value ledger during Stage A.

### Stage B — independent decision owner

Supply:

1. the frozen scenario;
2. the unchanged Stage A artifact and practitioner handoff;
3. [Decision-owner workbook](participant/04-decision-owner-workbook.md);
4. [Executive Decision Brief](../../EXECUTIVE-DECISION-BRIEF.md); and
5. [Value and Evidence Ledger](../../VALUE-AND-EVIDENCE-LEDGER.md).

The first calibration round uses a different person for Stage B. Do not let the
Stage A participant explain or repair the artifact during the initial read-
back.

## Facilitator only

- [Facilitator guide](facilitator-only/01-facilitator-guide.md)
- [Observation and scoring rubric](facilitator-only/02-observation-and-scoring-rubric.md)
- [Results and deviation log](facilitator-only/03-results-and-deviation-log.md)

Never supply these files before either scored stage ends.

## Execution prerequisites

Before recruitment:

1. assign an accountable execution owner;
2. approve storage, access, retention, redaction, and deletion;
3. decide whether further ethics, legal, privacy, or organizational review is
   required;
4. freeze the exact files and referenced asset bytes;
5. record SHA-256 values in a run-specific evidence manifest;
6. keep scheduling identity separate from participant codes; and
7. assign a facilitator and evaluator with disclosed relationships.

The checked-in `SHA256SUMS` records the prepared source packet. A run-specific
copy must also hash the supplied referenced assets. Any byte change requires a
new manifest and, when meaning changes, a new packet version.

## Evidence boundary

A completed pair can reveal wording defects, unsafe interpretations, transfer
failures, and useful behavior for the exact participants and materials. It
cannot prove API correctness, agent safety, business value, broad usability,
or publication readiness.
