# Exact Participant Route

**Packet:** API-RV-PILOT-001 version 1.2.5
**Human execution:** `PREPARED/UNRUN`
**Revision note:** Version 1.2.5 adds mutually exclusive entry and complete
route-closure gates while preserving version 1.2.4's exact immutable Stage A
live-update binding in the revision-phase input manifest. It preserves version 1.2.3's
replay identity, verification chronology, and external access logging and has
no human or practitioner validation.

Use only the exact local files in the sealed flat input. Do not search the repository
or open a link to an unlisted miniature, full worked or comprehensive example,
completed example, Failure Lab, facilitator file, or answer key. Short generic
examples already visible inside a supplied file may be read; they are not
scenario answers. Record any tempting or confusing omitted link instead of
opening it.

## Before either stage

The facilitator first creates the run-specific execution/access log and records
`RUN_STARTED`. Choose exactly one entry branch for the entire attempt and
record `ENTRY_BRANCH_SELECTED`. The branches are mutually exclusive and may
not change or mix between stages:

- **Human branch:** complete every required field in
  `01-consent-and-privacy.md`. Use separate run-specific consent records for
  Stage A and Stage B. A blank prerequisite or missing consent is a stop. Do
  not create or deliver a synthetic-context record.
- **Synthetic branch:** do not complete or deliver the human notice. Complete
  `API-SYNTHETIC-CONTEXT-<ATTEMPT-ID>-v1.md` from
  `01-synthetic-context-record.md`, artifact identity
  `API-SYNTHETIC-CONTEXT` / `v1`, with the literal
  `SYNTHETIC — NO HUMAN PARTICIPANT OR HUMAN DATA`. It must state the fictional
  scenario, orchestration-aided status, and absence of human consent,
  comprehension, usability, or practitioner results.

Before Stage A scored input, verify
`API-STAGE-A-CONTEXT-SHA256SUMS-v1.txt` over only the selected branch record and
record `STAGE_A_CONTEXT_MANIFEST_VERIFIED`. Before Stage B starts, verify
`API-STAGE-B-CONTEXT-SHA256SUMS-v1.txt` over only the applicable same-branch
record and record `STAGE_B_CONTEXT_MANIFEST_VERIFIED`. Branch omission,
mixing, or a synthetic human-result claim is a deviation and stop. Any added
synthetic orchestration must be immutable, declared in
`ORCHESTRATION-INPUT-SHA256SUMS`, verified, and logged before use; it remains
outside participant input.

The sealed input contains only files declared by this route and its current
phase release. Do not open or follow an `ORCHESTRATION.md`, run note, hidden
prompt, facilitator file, or other undeclared control file. Its presence is a
stop and deviation. The facilitator keeps instructions and the item-by-item
access history outside this input.

Human consent is required only for the human branch. Complete
[the consent notice](01-consent-and-privacy.md) before human scored work. For
either branch, the facilitator records `STAGE_A_STARTED` or `STAGE_B_STARTED`
and the exact stage start/timezone immediately before this route is opened.
Every file-open, pause, question, intervention, filename, and staged release is
recorded.

For every detached verification record named below, record the attempt ID,
stage/phase, artifact-producing actor, facilitator, manifest verifier, exact
verification command, complete observed output, exit code, observed
verification timestamp and timezone, record-completing actor, and explicit
later record-completion timestamp and timezone. A blank field, failed command,
or missing chronological separation prevents `FROZEN` and stops release.

## Stage A order

1. After the selected context manifest verifies, record `STAGE_A_STARTED` and
   open this route.
2. Open [the scenario](02-scenario-and-task.md).
3. Open [the practitioner workbook](03-practitioner-workbook.md) and complete
   only Section 1, recognition before terminology.
4. Open `START-HERE.md` for orientation; do not follow its example links.
5. Open `agent-ready-api-and-mcp-capability-brief.md` and create the detailed
   artifact.
6. Open `api-event-workflow-decision-tree.md` and revise the detailed artifact
   if needed.
7. Complete workbook Sections 2-4. Save the initial workbook and capability
   brief as `API-A-INITIAL-WORKBOOK-v1.md` and
   `API-A-INITIAL-CAPABILITY-BRIEF-v1.md`. Put an ID/version, completion
   timestamp/timezone, and `INITIAL COMPLETE` state inside each artifact before
   hashing. Create `API-A-INITIAL-ARTIFACTS-SHA256SUMS-v1.txt` over only those
   completed artifacts, verify it, and only then create
   `API-A-INITIAL-FREEZE-VERIFICATION-v1.md`. Before the update opens, create
   and verify `API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt`. It must hash the
   two initial artifacts, `API-A-INITIAL-ARTIFACTS-SHA256SUMS-v1.txt`,
   `API-A-INITIAL-FREEZE-VERIFICATION-v1.md`, and the exact immutable
   `API-A-LIVE-UPDATE-v1.md`. Omission, rename, regeneration, summary, or hash
   mismatch stops the revision phase.
8. Only after that five-member input manifest verifies, open
   `API-A-LIVE-UPDATE-v1.md` and record its contents exactly. This planned
   revision creates the first revised set; it is not a correction of frozen
   revised bytes. Complete workbook Section 5 and save exactly
   `API-A-REVISED-WORKBOOK-v1.md` and
   `API-A-REVISED-CAPABILITY-BRIEF-v1.md`.
9. Finish both revised artifacts. Give each an artifact ID, version, completion
   timestamp/timezone, and pre-hash state `REVISED COMPLETE`. Remove every
   `DRAFT`, `PENDING`, `PENDING FREEZE`, `AWAITING FREEZE`, blank, or equivalent
   incomplete state. Do not make either artifact self-declare `FROZEN`.
10. Create `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt`, hashing those two
    revised artifacts but not the manifest itself. Verify it and capture the
    exact verification timestamp/timezone. Only afterward open
    `06-revised-artifact-freeze-record.md` and complete it as
    `API-A-REVISED-FREEZE-VERIFICATION-v1.md`. Record that observed
    verification event, literal filenames, IDs/versions, completion metadata,
    artifact hashes, and governing manifest filename/hash. This later record is
    not governed by the manifest it describes and does not claim its own hash.
11. Create and verify `API-A-HANDOFF-PHASE-INPUT-SHA256SUMS-v1.txt` over the two
    revised artifacts, governing manifest, and detached verification record.
    Only then open the blank `05-one-screen-handoff.md`. List those same literal
    revised filenames and complete `API-A-ONE-SCREEN-HANDOFF-v1.md` with an
    ID/version, completion timestamp/timezone, and `HANDOFF COMPLETE` state.
    Hash only that completed handoff in `API-A-HANDOFF-SHA256SUMS-v1.txt`,
    verify it, and then create
    `API-A-HANDOFF-FREEZE-VERIFICATION-v1.md`.
12. After the handoff detached record is complete, open
    `08-stage-a-material-feedback.md` and complete
    `API-A-MATERIAL-FEEDBACK-v1.md` with ID/version, completion
    timestamp/timezone, and `FEEDBACK COMPLETE`. Record
    `STAGE_A_FEEDBACK_COMPLETED`, then record `STAGE_A_ENDED` and the exact end
    timestamp/timezone in the facilitator log. Do not alter the frozen workbook
    or handoff. A handoff freeze without these events is not a complete Stage A
    route.

If a revised frozen byte changes after step 10, do not overwrite or reuse its
filename. Preserve the old file and record exact old/new immutable filenames,
IDs/versions, hashes, reason, correction timestamp/timezone, replacement
detached verification record, and replacement manifest before any corrected set
may continue.

## Stage B order

After the applicable same-branch context manifest verifies, the facilitator
records `STAGE_B_STARTED` and the exact Stage B start/timezone before opening
this route.

1. Verify the phase-1 input manifest over `API-A-ONE-SCREEN-HANDOFF-v1.md`,
   `API-A-HANDOFF-SHA256SUMS-v1.txt`, and
   `API-A-HANDOFF-FREEZE-VERIFICATION-v1.md`; then open this route and the
   handoff as the first substantive artifact.
2. Open `04-decision-owner-workbook.md`, complete Section 1 from the handoff
   alone, and export it as `API-B-SECTION-1-SCAN-v1.md` with ID/version,
   completion timestamp/timezone, and `SECTION COMPLETE` state. Hash only that
   export in `API-B-SECTION-1-SHA256SUMS-v1.txt`, verify it, and then create
   `API-B-SECTION-1-FREEZE-VERIFICATION-v1.md`.
3. Verify a phase-2 input manifest that hashes the Section 1 export, its
   governing manifest, and detached verification record, plus every newly
   released file. Then open `02-scenario-and-task.md`,
   `API-A-REVISED-FREEZE-VERIFICATION-v1.md`, and
   `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt`.
4. Verify that the handoff, detached record, governing manifest, and delivered
   `API-A-REVISED-WORKBOOK-v1.md` and
   `API-A-REVISED-CAPABILITY-BRIEF-v1.md` match in literal filename,
   ID/version, completion timestamp/timezone, pre-hash `REVISED COMPLETE`
   state, hash, and detached-record `FROZEN` condition. Do not accept a rename,
   regenerated copy, summary, substitution, omission, or mismatch.
5. Complete Section 2 and export it as
   `API-B-SECTION-2-DETAIL-v1.md` with ID/version, completion
   timestamp/timezone, and `SECTION COMPLETE` state. Hash only that export in
   `API-B-SECTION-2-SHA256SUMS-v1.txt`, verify it, and then create
   `API-B-SECTION-2-FREEZE-VERIFICATION-v1.md`.
6. Verify a phase-3 input manifest that hashes the Section 2 export, its
   governing manifest, and detached verification record, plus the newly
   released executive files. Then open `EXECUTIVE-DECISION-BRIEF.md`, followed
   by `VALUE-AND-EVIDENCE-LEDGER.md`. Complete Sections 3-5 and export them as
   `API-B-SECTIONS-3-5-DECISION-v1.md` with ID/version, completion
   timestamp/timezone, and `SECTION COMPLETE` state. Hash only the completed
   Sections 3-5 export in
   `API-B-SECTIONS-3-5-SHA256SUMS-v1.txt`, verify it, and then create
   `API-B-SECTIONS-3-5-FREEZE-VERIFICATION-v1.md`.
7. After the Sections 3-5 detached record is complete, record `SCORING_ENDED`.
   Keep Section 6 closed until
   `API-B-PHASE-4-DEBRIEF-INPUT-SHA256SUMS-v1.txt` hashes the exact Sections
   3-5 export, governing manifest, detached verification record, and blank
   `07-section-6-debrief.md`, then verifies. Only afterward may Stage A
   explanation begin. Complete `API-B-SECTION-6-DEBRIEF-v1.md` with artifact
   ID/version, completion timestamp/timezone, and `DEBRIEF COMPLETE`. It must
   not rewrite frozen scored bytes or scores. Record `DEBRIEF_COMPLETED`, then
   `STAGE_B_ENDED` and exact Stage B end/timezone in the facilitator log.

For every freeze, the artifact records completion metadata before hashing; the
governing manifest hashes only completed artifacts; and a later detached record
records the observed verification timestamp/timezone, literal identities,
hashes, and manifest filename/hash. No artifact or manifest records its own
future hash. A route or provenance mismatch is a stop and recorded deviation,
not permission to repair in place.

## Results, log close, and later external closeout

The six scored freeze chains and the full route are separate results. Six
valid detached records establish only **six scored freeze chains complete**.

After Stage B ends, complete a new immutable result as
`API-RUN-RESULTS-<ATTEMPT-ID>-v1.md`, artifact identity `API-RUN-RESULTS` /
`v1`, state `RUN RESULTS COMPLETE`. Include the exact five-member revision
binding, all six chains, both stage boundaries, scoring/debrief, declared
counts, scores and API critical gates, deviations/stops/rejected attempts,
layout evidence, and separate protocol/synthetic/layout/human/real-world
states. Record `RUN_RESULTS_COMPLETED` before `LOG_CLOSED`. Do not predict the
future final closed-log hash or a future closeout timestamp.

Only after results completion may the facilitator append `LOG_CLOSED`,
validate the log, and copy it without byte change to `closeout/input`. Create
`API-RUN-CLOSEOUT-SHA256SUMS-v1.txt` over the closed-log copy and run-results
file. Then create `API-RUN-CLOSEOUT-<ATTEMPT-ID>-v1.md` binding the observed
closed-log, closeout-manifest, and run-results hashes. Only this later external
binding can support **full synthetic route complete**. It is not retroactively
inserted into the closed log.
