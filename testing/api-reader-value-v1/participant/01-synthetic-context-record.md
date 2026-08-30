# Synthetic Context Record Template

**Packet:** API-RV-PILOT-001 version 1.2.6
**Status:** Blank source template; not a completed run record
**Artifact identity:** `API-SYNTHETIC-CONTEXT` / `v1`
**Exact run filename:** `API-SYNTHETIC-CONTEXT-<ATTEMPT-ID>-v1.md`

Use this template only after the attempt selects the synthetic entry branch. A
synthetic rehearsal has no human participant and cannot obtain or claim human
consent. Do not complete, copy, or deliver
`01-consent-and-privacy.md` in the same attempt.

## Required immutable run context

- Packet ID/version: `API-RV-PILOT-001` / `1.2.6`
- Attempt ID:
- Required state literal: `SYNTHETIC — NO HUMAN PARTICIPANT OR HUMAN DATA`
- Scenario boundary: `FICTIONAL SCENARIO ONLY`
- Human-evidence boundary: `No human consent, comprehension, usability, or practitioner result`
- Synthetic Stage A actor code:
- Synthetic Stage B reviewer code:
- Facilitator code:
- Orchestration status: `ORCHESTRATION-AIDED`
- Exact orchestration manifest filename and SHA-256:
  `ORCHESTRATION-INPUT-SHA256SUMS` /
- Evidence root:
- Retention boundary:
- Access boundary:
- Synthetic context start timestamp/timezone:
- Pre-scored execution-log checkpoint sequence and continuity binding:

The checkpoint names an already-recorded event. It must not predict the
context-manifest verification, a future stage boundary, the final log hash, or
an external closeout timestamp.

## Manifest and delivery rule

Create and verify `API-STAGE-A-CONTEXT-SHA256SUMS-v1.txt` over this completed
exact run record before any Stage A scored file opens. Before Stage B starts,
create and verify `API-STAGE-B-CONTEXT-SHA256SUMS-v1.txt` over the same
immutable record. Log both verification events. The synthetic actor receives
this manifest-bound record instead of a completed human consent form.

If either context manifest includes a human-consent record, the selected branch
changes between stages, or this record claims any human result, record a
deviation and stop the attempt.
