# Facilitator Guide

**Packet:** API-RV-PILOT-001 version 1.2.6
**Status:** Facilitator-only; prepared and unrun

**Revision note:** Version 1.2.5 adds full-route closure while preserving version 1.2.4's exact immutable Stage A
live-update input. It preserves version 1.2.3's replay identity, verification
chronology, and external access logging and has no human or practitioner
validation.

## Purpose

Test the materials, not the participants. Observe whether the new reader-value
layer supports both a practitioner artifact and an independent decision-owner
read-back.

## Recommended timing

### Stage A — 70 to 85 minutes

- consent and setup: 5 minutes;
- scenario and recognition questions: 10 minutes;
- companion artifact: 30 minutes;
- decision guide and first evidence plan: 15 minutes;
- live update and revision: 10 minutes; and
- handoff and feedback: 10 minutes.

### Stage B — 35 to 50 minutes

- independent read-back: 15 minutes;
- executive brief and value ledger review: 10 minutes;
- bounded decision: 10 minutes; and
- debrief: 5 to 15 minutes.

Time is evidence, not a speed target.

## Required capture

Choose exactly one entry branch before the run begins. Then create the run-
specific execution/access log and record `ENTRY_BRANCH_SELECTED` before
`RUN_STARTED`. For a human, record setup start before the notice opens and
complete separate Stage A
and Stage B consent records. For a synthetic rehearsal, complete
`API-SYNTHETIC-CONTEXT-<ATTEMPT-ID>-v1.md`; do not complete a human consent
form. Record the exact stage start immediately before the route opens, plus the
file-open order, each pause or question, and every intervention. Do not
reconstruct these from memory after the session.

Maintain the facilitator-only
[`execution and access log`](05-execution-and-access-log.md) item by item. Log
every manifest gate, file open or attempted access, artifact completion,
manifest creation, manifest verification, detached-record completion, and next
phase open with exact actor, facilitator, timestamp, timezone, filename, and
continuity binding.

## Sealed flat delivery and manifest rule

Before Stage A, verify `API-STAGE-A-CONTEXT-SHA256SUMS-v1.txt` over only the
selected branch record. Before Stage B, verify
`API-STAGE-B-CONTEXT-SHA256SUMS-v1.txt` over only the applicable same-branch
record. A branch omission, mixed branch, or synthetic claim of human consent,
comprehension, usability, or practitioner result is a stop. Synthetic
orchestration must be immutable and verified in
`ORCHESTRATION-INPUT-SHA256SUMS` before use; it remains facilitator-side.

Before each stage, copy only the approved exact files into a new sealed flat
input. Preserve every literal local filename named by the packet route. Create
and verify a run-specific delivery manifest before scored work and log each
later staged release. A manifest hashes other files; it never lists or hashes
itself. Do not rely on repository-relative paths.

Reject any participant input containing an undeclared `ORCHESTRATION.md`, run
note, hidden prompt, facilitator file, or other extra control file. Keep all
facilitation outside the sealed participant surface and prove the declared
inventory item by item in the external access log.

Every freeze uses four ordered operations: finish artifact bytes with
ID/version, completion timestamp/timezone, and complete pre-hash state; create
a manifest that hashes only those artifacts; verify it and observe the exact
verification timestamp/timezone; then create a detached record of that observed
event. The record is later than, and excluded from, the manifest it describes.
The next phase's sealed input manifest hashes the artifacts, governing manifest,
and detached record. Never require an artifact, manifest, or record to contain
its own hash or a future verification time.

Every detached record must contain attempt ID, stage/phase,
artifact-producing actor, facilitator, manifest verifier, exact verification
command, complete observed output, exit code, observed verification timestamp
and timezone, record-completing actor, and an explicit later record-completion
timestamp and timezone. Missing evidence prevents `FROZEN`.

The planned live update creates the first revised set. It is not a correction
of already frozen revised bytes. A later correction must preserve the old
artifact and create exact new immutable filename, ID/version, hash, reason,
correction timestamp/timezone, replacement detached verification record, and
replacement manifest. Never overwrite or reuse the old filename.

## No-coaching rule

During scored work, the facilitator may repeat written text or resolve file
access. Do not define the target architecture, suggest a mechanism, identify a
seeded failure, interpret `accepted`, name the durable owner, or confirm an
answer. Record every intervention.

## Stage A sequence

1. Confirm the selected branch and context-manifest verification. Record
   `STAGE_A_STARTED` before opening the participant route.
2. Follow the route exactly. Supply the scenario and workbook only, then let the
   participant complete Section 1 before opening companion assets.
3. Supply only the three listed assets in the packet README, in order. Generic
   examples embedded in those files are allowed; do not allow linked
   Northbridge miniature, comprehensive, or completed examples.
4. Complete the initial workbook and capability brief as
   `API-A-INITIAL-WORKBOOK-v1.md` and
   `API-A-INITIAL-CAPABILITY-BRIEF-v1.md`, each with ID/version, completion
   timestamp/timezone, and `INITIAL COMPLETE` state. Hash only those completed
   artifacts in `API-A-INITIAL-ARTIFACTS-SHA256SUMS-v1.txt`, verify it, and
   then create `API-A-INITIAL-FREEZE-VERIFICATION-v1.md`. Before the update,
   create and verify `API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt`. It must
   hash both initial artifacts, their governing manifest, detached record, and
   exact immutable `API-A-LIVE-UPDATE-v1.md`. Omission, rename, regeneration,
   summary, or mismatch is a stop and deviation.
5. Only after that five-member manifest verifies, deliver and open the sealed
   participant input `API-A-LIVE-UPDATE-v1.md`. Do not retype, summarize, or
   substitute the update. Its canonical contents are:

<!-- API-A-LIVE-UPDATE-v1 CANONICAL START -->

> Stonebridge's first billing request timed out after the provider committed a
> charge. The agent retried with a new tool-call and request identifier. A
> second charge is now pending. The proposed `RentalExtensionConfirmed` event
> was published after the first request was accepted, so the warehouse removed
> the generator from tomorrow's pickup list and the customer was told the
> extension succeeded. Warehouse review has not occurred, and Stonebridge
> cannot yet tell whether either charge can be reversed.

<!-- API-A-LIVE-UPDATE-v1 CANONICAL END -->

6. Ask only: “What can each party safely say or do now, and what changes in
   your artifact?”
7. Let the participant revise the capability brief and workbook Section 5.
   Require exactly `API-A-REVISED-WORKBOOK-v1.md` and
   `API-A-REVISED-CAPABILITY-BRIEF-v1.md`, each with artifact ID, version,
   completion timestamp/timezone, and pre-hash state `REVISED COMPLETE`.
8. Remove every `DRAFT`, `PENDING`, `PENDING FREEZE`, `AWAITING FREEZE`, blank,
   or equivalent incomplete state, and reject a premature artifact
   self-declaration of `FROZEN`. Create
   `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt`; it hashes those two files and
   does not hash itself.
9. Verify that governing manifest and observe the exact verification
   timestamp/timezone. Only then complete
   `API-A-REVISED-FREEZE-VERIFICATION-v1.md` with the observed event, literal
   filenames, IDs/versions, completion metadata, artifact hashes, and governing
   manifest filename/hash. Do not add this later record to the manifest it
   describes.
10. Verify a handoff-phase input manifest that hashes the two revised artifacts,
    governing manifest, and detached record. Only then supply
    `05-one-screen-handoff.md`. Ensure its inventory matches, complete it as
    `API-A-ONE-SCREEN-HANDOFF-v1.md` with ID/version, completion
    timestamp/timezone, and `HANDOFF COMPLETE`, hash only that completed handoff
    in `API-A-HANDOFF-SHA256SUMS-v1.txt`, verify the manifest, and then create
    `API-A-HANDOFF-FREEZE-VERIFICATION-v1.md`.
11. Preserve initial, revised, record, manifest, and handoff bytes without
    alteration. After the handoff detached record, release
    `08-stage-a-material-feedback.md`; complete
    `API-A-MATERIAL-FEEDBACK-v1.md` with identity, completion time/timezone,
    and `FEEDBACK COMPLETE`. Record `STAGE_A_FEEDBACK_COMPLETED`, then
    `STAGE_A_ENDED` and the exact Stage A end in the facilitator log. Do not
    write that later end fact into a governed workbook or the feedback output.

## Stage B sequence

1. Use a participant or synthetic reviewer who did not create the Stage A
   artifact. Verify the selected same-branch context manifest and the phase-1
   input manifest over the handoff, governing manifest, and detached record.
   Record `STAGE_B_STARTED` and exact Stage B start/timezone before the route.
2. Supply the route, `API-A-ONE-SCREEN-HANDOFF-v1.md` as first substantive
   content, and the decision-owner workbook. Complete
   `API-B-SECTION-1-SCAN-v1.md` with ID/version, completion timestamp/timezone,
   and `SECTION COMPLETE`; hash only that export, verify its governing manifest,
   and then create its detached verification record before any scenario or
   detail opens.
3. Verify the phase-2 input manifest over that Section 1 trilogy and every newly
   released file. Supply `02-scenario-and-task.md`, the detached verification record, its governing
   revised manifest, and both exact handoff-linked revised details. Verify
   literal filenames, IDs/versions, completion timestamps/timezones, pre-hash
   `REVISED COMPLETE` states, hashes, and detached-record `FROZEN` conditions. A rename,
   regenerated copy, summary, substitution, omission, mismatch, or missing
   record/manifest stops detailed read-back.
4. Complete `API-B-SECTION-2-DETAIL-v1.md` with ID/version, completion
   timestamp/timezone, and `SECTION COMPLETE`; hash only that export, verify its
   governing manifest, and then create its detached verification record.
5. Verify the phase-3 input manifest over that Section 2 trilogy and the newly
   released `EXECUTIVE-DECISION-BRIEF.md` and
   `VALUE-AND-EVIDENCE-LEDGER.md`. Complete
   `API-B-SECTIONS-3-5-DECISION-v1.md` with completion metadata, hash only that
   export, verify its governing manifest, and then create its detached record.
   Keep Section 6 closed until the last detached record is complete.
6. Keep the Stage A actor unavailable through the Sections 3-5 freeze. Record
   `SCORING_ENDED`, then create and verify
   `API-B-PHASE-4-DEBRIEF-INPUT-SHA256SUMS-v1.txt` over the last export,
   governing manifest, detached record, and exact
   `07-section-6-debrief.md`. Only then release debrief. Complete
   `API-B-SECTION-6-DEBRIEF-v1.md` with identity, completion time/timezone, and
   `DEBRIEF COMPLETE`; record `DEBRIEF_COMPLETED`. Do not alter frozen scored
   bytes or scores. Record `STAGE_B_ENDED` and exact Stage B end/timezone in the
   facilitator log.

## Handoff layout proof

After the handoff freeze, render the retained Markdown to US Letter portrait
and complete `API-A-HANDOFF-LAYOUT-PROOF-<ATTEMPT-ID>-v1.md`. Preserve the
Markdown, PDF, rendering command, tool versions, page count, and PDF SHA-256.
`LAYOUT PASSED` requires exactly one page, margins at least 0.5 inch,
body/table text at least 9 points, no more than 450 reader-facing words
excluding immutable provenance, and no clipping, overlap, hidden overflow, or
unreadable shrinking. Layout evidence does not establish human scanability or
comprehension.

## Results, log close, and external closeout

After `STAGE_B_ENDED`, create a new immutable
`API-RUN-RESULTS-<ATTEMPT-ID>-v1.md` with artifact identity `API-RUN-RESULTS` /
`v1`, completion timestamp/timezone, and `RUN RESULTS COMPLETE`. Include exact
source/orchestration identities, all six freeze chains, the five-member
revision binding, final pre-close checkpoint, declared counts, both stage
boundaries, scoring/debrief, interventions/deviations/stops/rejected attempts,
semantic inventions, layout failures, scores/API critical gates, five separate
evidence states, decision, and limits.

The result must not predict the final log hash or future closeout time. Record
`RUN_RESULTS_COMPLETED` before `LOG_CLOSED`. Only then close and validate the
log, copy it byte-identically to `closeout/input`, and create
`API-RUN-CLOSEOUT-SHA256SUMS-v1.txt` over the closed log and results. Complete
the later `API-RUN-CLOSEOUT-<ATTEMPT-ID>-v1.md` binding all three hashes outside
the closed log. Six scored freeze chains complete is not full synthetic route
complete; layout passed is not comprehension; human evidence remains
`PREPARED/UNRUN` and real-world evidence remains `UNRUN`.

## Intervention levels

- **L0:** silence or think-aloud reminder;
- **L1:** repeat written text;
- **L2:** neutral probe such as “What can the customer rely on?”;
- **L3:** define a term without applying it;
- **L4:** recommend or supply the decision.

L3 is aided. L4 contaminates the affected gate. Preserve the result.

## Stop conditions

Stop and retain partial evidence on consent withdrawal, confidential-data
disclosure, material unblinding, changed frozen bytes, distress, material tool
failure, or coaching that makes the central result uninterpretable.
