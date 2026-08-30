# Temporal Freeze Protocol and Record Templates

**Packet:** API-RV-PILOT-001 version 1.2.5
**Status:** Facilitator-only static validation note and blank run-record schema;
prepared and unrun

Version 1.2.5 extends the schema-3 protocol with full-route closure while preserving version 1.2.4's machine-readable protocol and mutation suite so the
exact immutable `API-A-LIVE-UPDATE-v1.md` is a route-declared participant input
bound into the revision phase. It preserves version 1.2.3's attempt, phase,
actor, facilitator, exact verification command/output/exit/time/timezone, later
record-completion timestamp/timezone, and execution-history controls. The
facilitator separately maintains the
[`execution and access log`](05-execution-and-access-log.md). Passing static
checks remains non-human evidence only.

Schema 3 now also declares exactly one human-consent or synthetic-context
entry branch, explicit Stage A and Stage B boundaries, scoring end, manifested
Section 6 debrief, immutable results before log close, later external closeout,
and the proof-gated one-page handoff target. These are full-route gates outside
the six scored freeze chains.

## Static protocol finding

Version 1.2.0 could ask a governed workbook or handoff to contain its own later
freeze timestamp, hash, or manifest reference. Those values cannot truthfully
exist until after the governed bytes are final. Version 1.2.1 removes that
temporal self-reference from the initial, revised, handoff, and all three Stage
B freezes.

The valid causal order is:

`COMPLETE ARTIFACT BYTES -> GOVERNING MANIFEST -> MANIFEST VERIFICATION ->`
`DETACHED VERIFICATION RECORD -> NEXT-PHASE SEALED INPUT MANIFEST`

Rules:

1. Every governed artifact contains its literal filename, ID/version,
   completion timestamp/timezone, and complete pre-hash state before hashing.
2. The governing manifest hashes only the completed governed artifacts. It
   never lists itself and cannot list the later record.
3. Verify the manifest from the sealed directory and observe the exact
   verification timestamp/timezone.
4. Only after that event, create the detached record. It describes the observed
   event and contains artifact identities/hashes plus manifest filename/hash.
   It is not governed by the manifest it describes and claims no self-hash.
5. Before the next phase opens, its sealed input manifest hashes the governed
   artifacts, governing manifest, and detached record, along with any newly
   released inputs.
6. A later correction never alters frozen bytes. Preserve the old three-part evidence set and
   issue new immutable artifact bytes, a new manifest, and a new detached
   verification record.
7. The sealed participant input contains only route-declared files. An
   `ORCHESTRATION.md`, run note, hidden prompt, facilitator file, or other
   undeclared control file is prohibited. Facilitation instructions and the
   item-by-item access history stay in the external execution/access log.

## Exact freeze inventory

| Freeze | Governed artifact(s) and required state | Governing manifest | Later detached verification record | Next-phase input manifest |
| --- | --- | --- | --- | --- |
| Stage A initial | `API-A-INITIAL-WORKBOOK-v1.md`; `API-A-INITIAL-CAPABILITY-BRIEF-v1.md`; `INITIAL COMPLETE` | `API-A-INITIAL-ARTIFACTS-SHA256SUMS-v1.txt` | `API-A-INITIAL-FREEZE-VERIFICATION-v1.md` | `API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt`, also binding exact new input `API-A-LIVE-UPDATE-v1.md` |
| Stage A revised | `API-A-REVISED-WORKBOOK-v1.md`; `API-A-REVISED-CAPABILITY-BRIEF-v1.md`; `REVISED COMPLETE` | `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt` | `API-A-REVISED-FREEZE-VERIFICATION-v1.md` | `API-A-HANDOFF-PHASE-INPUT-SHA256SUMS-v1.txt` |
| Stage A handoff | `API-A-ONE-SCREEN-HANDOFF-v1.md`; `HANDOFF COMPLETE` | `API-A-HANDOFF-SHA256SUMS-v1.txt` | `API-A-HANDOFF-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-1-INPUT-SHA256SUMS-v1.txt` |
| Stage B Section 1 | `API-B-SECTION-1-SCAN-v1.md`; `SECTION COMPLETE` | `API-B-SECTION-1-SHA256SUMS-v1.txt` | `API-B-SECTION-1-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-2-INPUT-SHA256SUMS-v1.txt` |
| Stage B Section 2 | `API-B-SECTION-2-DETAIL-v1.md`; `SECTION COMPLETE` | `API-B-SECTION-2-SHA256SUMS-v1.txt` | `API-B-SECTION-2-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-3-INPUT-SHA256SUMS-v1.txt` |
| Stage B Sections 3-5 | `API-B-SECTIONS-3-5-DECISION-v1.md`; `SECTION COMPLETE` | `API-B-SECTIONS-3-5-SHA256SUMS-v1.txt` | `API-B-SECTIONS-3-5-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-4-DEBRIEF-INPUT-SHA256SUMS-v1.txt` |

## Exact Stage A revision-phase input inventory

Create `API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt` over every and only the
following five immutable local filenames, then verify it before the live-update
file is opened:

1. `API-A-INITIAL-WORKBOOK-v1.md`;
2. `API-A-INITIAL-CAPABILITY-BRIEF-v1.md`;
3. `API-A-INITIAL-ARTIFACTS-SHA256SUMS-v1.txt`;
4. `API-A-INITIAL-FREEZE-VERIFICATION-v1.md`; and
5. `API-A-LIVE-UPDATE-v1.md`.

- Revision-phase input manifest exact filename and SHA-256:
- Live-update exact filename and SHA-256:
- All five exact names and bytes matched before phase open: yes / no
- Omission, rename, regenerated copy, summary, substitution, or unbound update:
  none / stop and deviation

The live-update bytes are canonical participant input, not facilitator speech
to reconstruct later. The planned revision remains distinct from a correction
of already frozen revised bytes.

This exact five-member manifest remains immutable in version 1.2.5. None of
the entry, debrief, results, closeout, or layout records may be inserted into,
renamed within, or substituted for one of its five members.

## Full-route records outside the six freezes

- Select exactly one run-specific human-consent or synthetic-context record;
  verify it through the two stage context manifests.
- After the handoff freeze, complete `API-A-MATERIAL-FEEDBACK-v1.md`, record
  `STAGE_A_FEEDBACK_COMPLETED`, then `STAGE_A_ENDED` in the facilitator log.
- After the Sections 3-5 freeze, record `SCORING_ENDED`; verify the four-member
  `API-B-PHASE-4-DEBRIEF-INPUT-SHA256SUMS-v1.txt`; complete
  `API-B-SECTION-6-DEBRIEF-v1.md`; then record `DEBRIEF_COMPLETED` and
  `STAGE_B_ENDED`.
- Complete `API-RUN-RESULTS-<ATTEMPT-ID>-v1.md` with state
  `RUN RESULTS COMPLETE` before `LOG_CLOSED`. Never predict the final log hash
  or future closeout timestamp.
- After close, validate and copy the log byte-identically, create
  `API-RUN-CLOSEOUT-SHA256SUMS-v1.txt`, and complete the later external
  closeout record binding log, manifest, and results hashes.
- A favorable one-page claim requires the completed US Letter layout proof;
  local layout is not human comprehension.

Six scored freeze chains complete is not full-route completion.

## Detached verification-record schema

Create one record for each inventory row under that row's exact record
filename. Do not place the later observed values back into a governed artifact.

- Attempt ID:
- Stage and phase:
- Freeze-verification record ID/version:
- Artifact-producing actor code:
- Facilitator name/code:
- Manifest verifier name/code and relationship:
- Exact manifest-verification command:
- Complete observed command output:
- Observed command exit code:
- Verification result: pass / fail / deviation
- Observed manifest-verification timestamp:
- Observed manifest-verification timezone:
- Record-completing actor name/code:
- Record completion timestamp, explicitly later than verification:
- Record completion timezone:
- Governing manifest exact filename:
- Governing manifest SHA-256:
- Manifest excludes itself: yes / no
- Manifest excludes this later detached verification record: yes / no
- Record created only after manifest verification: yes / no
- All required attempt, phase, actor, facilitator, command, output, exit,
  verification-time, and later record-completion fields present: yes / no

| Governed artifact exact literal filename | Artifact ID/version | Artifact completion timestamp/timezone | Pre-hash state | SHA-256 | Matches manifest |
| --- | --- | --- | --- | --- | --- |
| | | | | | |

- Stop/deviation, if any:
- Record claims no self-hash: yes / no
- Freeze state for the listed verified hashes: `FROZEN` / not established
- Next-phase input manifest exact filename:
- Next-phase input manifest includes every governed artifact, the governing
  manifest, and this completed record: yes / no / not yet created

The facilitator copies these observed values from the immutable command result
and execution/access log. Do not infer missing times, actors, output, or exit
codes after the fact. Any blank required field prevents `FROZEN`.

## Post-freeze correction schema

- Correction ID and reason:
- Exact correction timestamp/timezone:
- Prior artifacts, manifest, and detached record preserved: yes / no
- New immutable artifact filenames and IDs/versions:
- Replacement governing manifest filename/hash:
- Replacement manifest observed verification timestamp/timezone:
- Replacement detached verification-record filename:
- Affected route stopped until authorized review: yes / no

This static review proves only that the written protocol has a coherent causal
order. It is not evidence that a human session occurred, that the files fit on
one screen, or that the architecture, safety, usability, or business value is
valid.
