# API Reader-Value Pilot Packet

**Packet ID:** API-RV-PILOT-001
**Version:** 1.1.0
**Status:** `PREPARED/UNRUN` for human participants; no participant recruited or
consented
**Scenario:** Stonebridge Equipment Rental, entirely fictional

Version 1.1.0 incorporates source repairs identified by a synthetic route
preflight. That internal exercise was not a human or practitioner session and
provides no usability, safety, architecture, or business-value validation.

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

Record setup start before the consent notice is first opened. Complete consent
before scored work. Then record the Stage A start before the route is opened
and follow its exact order. Supply only:

1. [Consent and privacy notice](participant/01-consent-and-privacy.md), during
   setup rather than as scored architecture work
2. [Exact packet route](participant/00-packet-route.md)
3. [Scenario and task](participant/02-scenario-and-task.md)
4. [Practitioner workbook](participant/03-practitioner-workbook.md)
5. [Start Here](../../START-HERE.md)
6. [Agent-Ready API and MCP Capability Brief](../../agent-ready-api-and-mcp-capability-brief.md)
7. [API, MCP Tool, Event, Workflow, or Agent Decision Guide](../../api-event-workflow-decision-tree.md)
8. after the live update only, the blank
   [One-Screen Handoff](participant/05-one-screen-handoff.md)

The short generic examples already embedded in supplied files are allowed.
Do not follow their links to the Northbridge miniature, any comprehensive or
completed example, or other omitted material. All full worked examples are
withheld. Do not supply the repository
failure lab, facilitator materials, executive brief, or value ledger during
Stage A. Freeze the initial detailed outputs before the live update. After the
update, freeze the revised detailed outputs and completed one-screen handoff.

### Stage B — independent decision owner

Record setup start before the consent notice is first opened. Complete consent,
then record the Stage B start before the route is opened. Follow the route and
supply:

1. [Consent and privacy notice](participant/01-consent-and-privacy.md), during
   setup;
2. the [Exact packet route](participant/00-packet-route.md);
3. the frozen completed [One-Screen Handoff](participant/05-one-screen-handoff.md)
   as the first decision content;
4. the frozen scenario and revised Stage A detailed artifacts;
5. [Decision-owner workbook](participant/04-decision-owner-workbook.md);
6. [Executive Decision Brief](../../EXECUTIVE-DECISION-BRIEF.md); and
7. [Value and Evidence Ledger](../../VALUE-AND-EVIDENCE-LEDGER.md).

The first calibration round uses a different person for Stage B. Stage B reads
the one-screen handoff before the scenario or detailed artifacts and may then
inspect the detail. Do not let the Stage A participant explain or repair any
artifact during the initial read-back.

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
