# Exact Participant Route

**Packet:** API-RV-PILOT-001 version 1.2.1
**Human execution:** `PREPARED/UNRUN`
**Revision note:** Version 1.2.1 makes every freeze temporally ordered and
non-self-referential after static protocol review; it has no human or
practitioner validation.

Use only the exact local files in the sealed flat input. Do not search the repository
or open a link to an unlisted miniature, full worked or comprehensive example,
completed example, Failure Lab, facilitator file, or answer key. Short generic
examples already visible inside a supplied file may be read; they are not
scenario answers. Record any tempting or confusing omitted link instead of
opening it.

Human consent is required for a real run. Complete
[the consent notice](01-consent-and-privacy.md) before scored work. The
facilitator records setup start before that notice is first opened, verifies a
run-specific manifest that does not hash itself, then records the exact stage
start and timezone immediately before this route is opened. Every file-open,
pause, question, intervention, filename, and staged release is recorded.

## Stage A order

1. Open this route.
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
   `API-A-INITIAL-FREEZE-VERIFICATION-v1.md`. Before the update opens, seal an
   input manifest that hashes the initial artifacts, governing manifest, and
   detached verification record.
8. Receive the live update. This planned revision creates the first revised
   set; it is not a correction of frozen revised bytes. Complete workbook
   Section 5 and save exactly `API-A-REVISED-WORKBOOK-v1.md` and
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
12. Complete workbook Sections 6-7.

If a revised frozen byte changes after step 10, do not overwrite or reuse its
filename. Preserve the old file and record exact old/new immutable filenames,
IDs/versions, hashes, reason, correction timestamp/timezone, replacement
detached verification record, and replacement manifest before any corrected set
may continue.

## Stage B order

After separate consent, the facilitator records Stage B start and timezone
before opening this route.

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
7. Keep Section 6 closed until scoring ends and a debrief-phase input manifest
   hashes the Sections 3-5 export, governing manifest, and detached verification
   record. Only then may Stage A explanation or repair begin.

For every freeze, the artifact records completion metadata before hashing; the
governing manifest hashes only completed artifacts; and a later detached record
records the observed verification timestamp/timezone, literal identities,
hashes, and manifest filename/hash. No artifact or manifest records its own
future hash. A route or provenance mismatch is a stop and recorded deviation,
not permission to repair in place.
