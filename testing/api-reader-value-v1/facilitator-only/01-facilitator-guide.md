# Facilitator Guide

**Packet:** API-RV-PILOT-001 version 1.2.3
**Status:** Facilitator-only; prepared and unrun

**Revision note:** Version 1.2.3 adds machine-enforced replay identity,
verification-command evidence, record-completion chronology, and external
access logging; it has no human or practitioner validation.

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

For each participant, record setup start before the consent notice is first
opened. Obtain consent, then record the exact stage start immediately before
the route is opened. Record the exact file-open order, each pause or question,
and every intervention with time and level. Do not reconstruct these from
memory after the session.

Maintain the facilitator-only
[`execution and access log`](05-execution-and-access-log.md) item by item. Log
every manifest gate, file open or attempted access, artifact completion,
manifest creation, manifest verification, detached-record completion, and next
phase open with exact actor, facilitator, timestamp, timezone, filename, and
continuity binding.

## Sealed flat delivery and manifest rule

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

1. Confirm consent and freeze identity. Record Stage A start before opening the
   participant route.
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
   verify a revision-phase input manifest that hashes the artifacts, governing
   manifest, and detached record.
5. Read the live update:

> Stonebridge's first billing request timed out after the provider committed a
> charge. The agent retried with a new tool-call and request identifier. A
> second charge is now pending. The proposed `RentalExtensionConfirmed` event
> was published after the first request was accepted, so the warehouse removed
> the generator from tomorrow's pickup list and the customer was told the
> extension succeeded. Warehouse review has not occurred, and Stonebridge
> cannot yet tell whether either charge can be reversed.

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
    alteration.

## Stage B sequence

1. Use a participant who did not create the Stage A artifact, obtain separate
   consent, verify the phase-1 input manifest over the handoff, its governing
   manifest, and detached verification record, and record exact Stage B start
   and timezone before opening the route.
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
   Keep Section 6 closed until a debrief-phase input manifest hashes the last
   export, governing manifest, and detached record and scoring ends.
6. Keep the Stage A participant unavailable until then. End scoring before
   allowing explanation or repair. Record exact Stage B end and timezone.

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
