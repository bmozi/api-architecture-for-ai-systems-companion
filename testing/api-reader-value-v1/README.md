# API Reader-Value Pilot Packet

**Packet ID:** API-RV-PILOT-001
**Version:** 1.2.6
**Status:** `PREPARED/UNRUN` for human participants; no participant recruited or
consented
**Scenario:** Stonebridge Equipment Rental, entirely fictional

Version 1.2.6 corrects the entry chronology: select exactly one human or
synthetic branch and record `ENTRY_BRANCH_SELECTED` before `RUN_STARTED`. It
preserves version 1.2.5's stage boundaries, scoring end, manifested
post-scoring Section 6 debrief, immutable run-specific results before log
close, later external closeout, and proof-gated one-page US Letter handoff
contract. These full-route boundaries remain separate from the six scored
freeze chains; layout evidence is not comprehension. Human evidence remains
`PREPARED/UNRUN` and real-world evidence remains `UNRUN`.

Version 1.2.4 exported the canonical Stage A update as the exact immutable
participant/run input `API-A-LIVE-UPDATE-v1.md` and requires the verified
revision-phase input manifest to bind it alongside the frozen initial artifact
set. It preserves version 1.2.3's non-self-referential freeze sequence,
auditable facilitator-side execution history, exact manifest-verification
command/output/exit/time/timezone, and later record-completion chronology.
This repair came from static and synthetic preflight, not a human or
practitioner session, and provides no usability, safety, architecture, or
business-value validation.

The normative release inventory and invariants are in
[`temporal-protocol.json`](temporal-protocol.json). The human instructions must
agree with that file; the repository validator checks both their exact frozen
bytes and their structured release rows.

## What this packet tests

This packet tests the complete reader-value chain for one API-first capability:

`RECOGNITION -> PLAIN EXPLANATION -> FIRST ARTIFACT -> FAILURE DISCOVERY ->`
`OUTSIDE READ-BACK -> CROSS-ROLE DECISION -> NEXT EVIDENCE`

It does not replace the older Cedarway technical-transfer packet. Cedarway
retains its frozen pre-MCP API/event/workflow scope. This packet separately
tests the newer Agent-Ready API and MCP Capability Brief, role paths, failure
lab, value ledger, and executive decision language.

## Sealed flat run inputs

Choose exactly one entry branch before the run begins. Create the facilitator-
side execution/access log and record `ENTRY_BRANCH_SELECTED` before
`RUN_STARTED`. Represent the selected branch with completed run-specific human
consent records, or one immutable run-specific
`API-SYNTHETIC-CONTEXT-<ATTEMPT-ID>-v1.md`. Never omit or mix branches, and
never fabricate consent. Verify the selected record in
`API-STAGE-A-CONTEXT-SHA256SUMS-v1.txt` before Stage A and
`API-STAGE-B-CONTEXT-SHA256SUMS-v1.txt` before Stage B. Any added synthetic
orchestration must be frozen and verified in `ORCHESTRATION-INPUT-SHA256SUMS`
before use and remains outside participant input.

Before either stage, copy the exact approved immutable files into a new sealed,
flat stage-input directory. Preserve every literal filename below. Do not
deliver repository-relative paths, aliases, regenerated copies, or summaries.
Create and verify a run-specific SHA-256 delivery manifest before the scored
stage starts. A manifest hashes other files; it never lists or hashes itself.
The sealed directory must contain only route-declared participant files. An
`ORCHESTRATION.md`, run note, hidden prompt, facilitator file, or other
undeclared control file is prohibited. Keep orchestration and every item-level
gate/open/completion/manifest/verification/record event in the separate
facilitator-only [execution and access log](facilitator-only/05-execution-and-access-log.md).

For every later freeze, use this exact temporal order:

1. finish the governed artifact bytes, including ID/version, completion
   timestamp/timezone, and complete pre-hash state;
2. create a governing manifest that hashes only those completed artifacts;
3. verify that manifest and observe the exact verification timestamp/timezone;
4. only then create a detached freeze-verification record describing the
   observed event, artifact and manifest identities, and hashes; and
5. have the next phase's sealed input manifest hash the completed artifacts,
   their governing manifest, and that later detached record.

The governing manifest never hashes itself or the later record that describes
its verification. The record never claims its own hash.

The planned live-update revision creates the first revised artifact set. It is
not a correction of already frozen revised bytes. If a revised byte changes
after its freeze, retain the old artifact and create a new immutable filename,
ID/version, hash, governing manifest, and detached verification record. Record the exact
reason and correction timestamp with timezone. Never overwrite, rename, or
relabel the prior evidence.

## Two stages

### Stage A — practitioner

For the human branch, record setup start before the consent notice opens and
complete consent before scored work. For either branch, verify the Stage A
context manifest, record `STAGE_A_STARTED` and the exact start/timezone before
the route opens, and follow its exact order. Supply only these exact local
filenames:

1. the selected run-specific [human consent](participant/01-consent-and-privacy.md)
   or [synthetic context](participant/01-synthetic-context-record.md) record,
   never both
2. `00-packet-route.md`
3. `02-scenario-and-task.md`
4. `03-practitioner-workbook.md`
5. `START-HERE.md`
6. `agent-ready-api-and-mcp-capability-brief.md`
7. `api-event-workflow-decision-tree.md`
8. only after the revision-phase input manifest verifies,
   `API-A-LIVE-UPDATE-v1.md`;
9. after the live-update revision, `06-revised-artifact-freeze-record.md`; and
10. only after that record verifies, the blank `05-one-screen-handoff.md`; and
11. after the handoff freeze, `08-stage-a-material-feedback.md`.

The short generic examples already embedded in supplied files are allowed.
Do not follow their links to the Northbridge miniature, any comprehensive or
completed example, or other omitted material. All full worked examples are
withheld. Do not supply the repository
failure lab, facilitator materials, executive brief, or value ledger during
Stage A. Before the live update, freeze the initial workbook and capability
brief as `API-A-INITIAL-WORKBOOK-v1.md` and
`API-A-INITIAL-CAPABILITY-BRIEF-v1.md`, each marked `INITIAL COMPLETE` with an
ID/version and completion timestamp/timezone. Govern them with
`API-A-INITIAL-ARTIFACTS-SHA256SUMS-v1.txt`, verify it, and only then create
`API-A-INITIAL-FREEZE-VERIFICATION-v1.md`. The sealed
`API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt` must hash the two initial
artifacts, that governing manifest, the detached verification record, and the
exact immutable `API-A-LIVE-UPDATE-v1.md`. Verify that five-member manifest
before the live-update file is opened. An omitted, renamed, regenerated,
summarized, or unmanifested update is a stop and deviation.

The required revised detail filenames are:

- `API-A-REVISED-WORKBOOK-v1.md`; and
- `API-A-REVISED-CAPABILITY-BRIEF-v1.md`.

Each revised file must contain its artifact ID, version, completion
timestamp/timezone, and pre-hash state `REVISED COMPLETE`; `DRAFT`, `PENDING`,
`PENDING FREEZE`, `AWAITING FREEZE`, a blank state, or an equivalent marker is
not complete. The governing manifest is
`API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt`. It hashes the two revised detail
files and does not hash itself. After verifying that manifest, complete
`API-A-REVISED-FREEZE-VERIFICATION-v1.md` from the supplied
[detached record template](participant/06-revised-artifact-freeze-record.md).
That record must verify exact filenames, IDs, versions, completion
timestamps/timezones, pre-hash states, hashes, and manifest filename/hash and
record the observed manifest-verification timestamp/timezone. It is created
after the manifest and is not governed by the manifest it describes. Before
the blank handoff opens, a sealed handoff-phase input manifest must hash the
revised artifacts, governing manifest, and detached record.

Complete the handoff as `API-A-ONE-SCREEN-HANDOFF-v1.md` with an ID/version,
completion timestamp/timezone, and `HANDOFF COMPLETE` state. Hash only that
completed handoff in `API-A-HANDOFF-SHA256SUMS-v1.txt`, verify the manifest,
and then create `API-A-HANDOFF-FREEZE-VERIFICATION-v1.md`. The Stage B phase-1
input manifest must hash the handoff, its governing manifest, and its detached
verification record.

After the handoff detached record, complete
`API-A-MATERIAL-FEEDBACK-v1.md` from the separate feedback template and record
`STAGE_A_FEEDBACK_COMPLETED`. Then record `STAGE_A_ENDED` and the exact end in
the facilitator log. Do not change the frozen workbook or handoff.

### Stage B — independent decision owner

For the human branch, complete the Stage B participant's separate consent. For
either branch, verify the Stage B context manifest and record
`STAGE_B_STARTED` and exact start/timezone before the route opens. Build a
separate sealed flat Stage B input and supply in the route's exact order:

1. the applicable same-branch human consent or synthetic context record, never
   both;
2. `00-packet-route.md`;
3. `API-A-ONE-SCREEN-HANDOFF-v1.md` as the first substantive decision content,
   plus its governing manifest and detached verification record as sealed
   provenance;
4. `04-decision-owner-workbook.md`;
5. after the Section 1 freeze, `02-scenario-and-task.md`,
   `API-A-REVISED-FREEZE-VERIFICATION-v1.md`,
   `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt`,
   `API-A-REVISED-WORKBOOK-v1.md`, and
   `API-A-REVISED-CAPABILITY-BRIEF-v1.md`;
6. after the Section 2 freeze, `EXECUTIVE-DECISION-BRIEF.md`; and
7. `VALUE-AND-EVIDENCE-LEDGER.md`; and
8. only after `SCORING_ENDED` and verified debrief input,
   `07-section-6-debrief.md`.

The handoff's literal detail inventory, detached record, governing manifest,
and delivered Stage B files must match exactly. A rename, regenerated copy,
summary, substitution, omission, hash mismatch, pre-hash state other than
`REVISED COMPLETE`, or missing detached `FROZEN` verification stops detailed
read-back and is recorded as a deviation.

The first calibration round uses a different person for Stage B. For each of
the three exports, complete its ID/version, completion timestamp/timezone, and
`SECTION COMPLETE` state before hashing it. Create a governing manifest that
hashes only that export, verify it, and then create a detached verification
record. The next phase's sealed input manifest hashes the export, its manifest,
and its detached record. Apply this sequence to Section 1 from the handoff
alone, Section 2 after exact detail verification, and Sections 3-5 after the
executive files. Keep Section 6 closed until the Sections 3-5 record verifies
and the debrief-phase input manifest seals the last export, manifest, and
record. Do not let the Stage A participant explain or repair an artifact before
then.

After the three Stage B scored freezes, record `SCORING_ENDED`; verify the
four-member debrief manifest, complete `API-B-SECTION-6-DEBRIEF-v1.md`, and
record `DEBRIEF_COMPLETED` and `STAGE_B_ENDED`. Complete and hash immutable
run-specific results before `RUN_RESULTS_COMPLETED`, append `LOG_CLOSED` only
afterward, and create the later external closeout binding. The six scored
freeze chains do not substitute for full-route closure.

Render the frozen handoff to US Letter portrait and complete the run-specific
layout proof. A favorable `LAYOUT PASSED` claim requires exactly one page,
margins at least 0.5 inch, body/table type at least 9 points, no more than 450
reader-facing words excluding immutable provenance, and no clipping, overlap,
hidden overflow, or unreadable shrinking. This local proof is not evidence of
human comprehension or scanability.

After Stage B ends, create `API-RUN-RESULTS-<ATTEMPT-ID>-v1.md` with identity
`API-RUN-RESULTS` / `v1` and state `RUN RESULTS COMPLETE`. Preserve the exact
five-member manifest finding, all six scored chains, stage/debrief boundaries,
counts, negative findings, and separate protocol/synthetic/layout/human/real-
world states. It must not predict a final log hash or future closeout time.
Record `RUN_RESULTS_COMPLETED` before `LOG_CLOSED`; then bind the observed
closed-log and results hashes through the later external closeout template.

## Facilitator only

- [Facilitator guide](facilitator-only/01-facilitator-guide.md)
- [Observation and scoring rubric](facilitator-only/02-observation-and-scoring-rubric.md)
- [Results and deviation log](facilitator-only/03-results-and-deviation-log.md)
- [Temporal freeze protocol and record templates](facilitator-only/04-temporal-freeze-protocol-and-record-templates.md)
- [Execution and access log](facilitator-only/05-execution-and-access-log.md)
- [Handoff layout proof record](facilitator-only/06-handoff-layout-proof-record.md)
- [External closeout record](facilitator-only/07-external-closeout-record.md)

Never supply these files before either scored stage ends.

## Execution prerequisites

Before recruitment:

1. assign an accountable execution owner;
2. approve storage, access, retention, redaction, and deletion;
3. decide whether further ethics, legal, privacy, or organizational review is
   required;
4. create sealed flat stage inputs and freeze the exact files and referenced
   asset bytes;
5. record SHA-256 values and observed verification timestamps/timezones in
   detached run-specific evidence;
6. retain the exact verification command, complete output, exit code, actors,
   facilitator, and later record-completion timestamp/timezone for every
   detached record;
7. maintain the external item-by-item execution/access log and prove the
   participant input contains no undeclared orchestration file;
8. keep scheduling identity separate from participant codes; and
9. assign a facilitator and evaluator with disclosed relationships.

The checked-in `SHA256SUMS` records the prepared source packet. See the
[static protocol validation note](facilitator-only/04-temporal-freeze-protocol-and-record-templates.md)
for the exact freeze inventory and record schema. A run-specific
delivery manifest must also hash every supplied referenced asset under its
exact local filename while excluding itself. Any byte change requires a new
manifest and, when meaning changes, a new packet version.

## Evidence boundary

A completed pair can reveal wording defects, unsafe interpretations, transfer
failures, and useful behavior for the exact participants and materials. It
cannot prove API correctness, agent safety, business value, broad usability,
or publication readiness.
