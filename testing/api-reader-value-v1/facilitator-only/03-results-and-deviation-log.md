# Results and Deviation Log

**Packet:** API-RV-PILOT-001 version 1.2.5
**Status:** Blank controlled record; no result exists
**Run artifact identity:** `API-RUN-RESULTS` / `v1`
**Exact run filename:** `API-RUN-RESULTS-<ATTEMPT-ID>-v1.md`

**Revision note:** Version 1.2.5 makes this a run-specific pre-close result template while preserving version 1.2.4's exact immutable Stage A
live-update input. It preserves version 1.2.3's replay identity, verification
chronology, and external access logging and has no human or practitioner
validation.

Each attempt creates a new immutable run-specific result from this template.
Complete it after `STAGE_B_ENDED`, record `RUN_RESULTS_COMPLETED`, and only then
append `LOG_CLOSED`. This source template is never itself a run result.

## Run identity

- Attempt ID:
- Execution owner and authorization:
- Stage A participant or synthetic actor code:
- Stage B decision-owner or synthetic reviewer code:
- Facilitator:
- Evaluator and independence disclosure:
- Date, mode, and time:
- Exact Stage A start and end with timezone:
- Exact Stage B start and end with timezone:
- Facilitator execution/access log exact filename and SHA-256:
- Selected entry branch: human / synthetic; exactly one:
- Exact branch record filename, artifact ID/version, and SHA-256:
- Source `SHA256SUMS` identity/hash:
- Synthetic `ORCHESTRATION-INPUT-SHA256SUMS` identity/hash, or `NOT APPLICABLE — HUMAN`:
- Final pre-close execution-log checkpoint and continuity binding:
- Run-results completion timestamp/timezone:
- Run-results completion state: `RUN RESULTS COMPLETE`

## Consent, privacy, and freeze

- Human consent records, or exact synthetic context and
  `SYNTHETIC — NO HUMAN PARTICIPANT OR HUMAN DATA`:
- Branch omission/mixing check: none / deviation and stop
- Storage/access/retention authority:
- Run-specific SHA-256 manifest:
- Sealed flat Stage A input location and manifest:
- Sealed flat Stage B input location and manifest:
- Prepared-source manifest match:
- Supplied and withheld materials correct: yes / no / deviation
- Declared participant-input inventory matches item by item: yes / no /
  deviation
- Undeclared orchestration, run note, hidden prompt, facilitator file, or other
  control file in participant input: none / deviation ID
- Confidentiality or privacy concern:
- Initial Stage A artifacts completed before manifest creation: yes / no /
  deviation; IDs/versions and completion timestamps/timezones:
- Initial governing manifest filename/hash and observed verification
  timestamp/timezone:
- Initial detached verification record filename:
  `API-A-INITIAL-FREEZE-VERIFICATION-v1.md`
- Revision-phase input manifest exact filename/hash:
  `API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt` /
- Immutable live-update participant input exact filename/hash:
  `API-A-LIVE-UPDATE-v1.md` /
- Revision-phase input manifest hashes both initial artifacts, governing
  manifest, detached record, and exact live-update input: yes / no / deviation
- Live-update filename and bytes matched before opening; no omission, rename,
  regeneration, summary, substitution, or unbound delivery: yes / no /
  deviation

Final closed-log SHA-256 is not available before `LOG_CLOSED` and must not be
predicted here. Do not record a future closeout timestamp. The later external
closeout record binds the actual closed-log, closeout-manifest, and this
run-results file's hashes.

## Revised-detail and Stage B transfer verification

- Revised artifacts completed before governing manifest creation: yes / no /
  deviation
- Revised detached record created only after manifest verification: yes / no /
  deviation
- Detached record exact filename/hash:
  `API-A-REVISED-FREEZE-VERIFICATION-v1.md` /
- Revised governing manifest exact filename/hash:
  `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt` /
- Manifest observed verification timestamp/timezone:
- Manifest verified and lists neither itself nor the later record: yes / no /
  deviation
- Detached record claims no self-hash or future event: yes / no / deviation
- Handoff-phase input manifest hashes revised artifacts, governing manifest,
  and detached record: yes / no / deviation
- Any incomplete state or premature artifact self-declaration of `FROZEN`:
  none / deviation

| Handoff-linked exact local filename | Artifact ID/version | Completion timestamp/timezone | Pre-hash state | SHA-256 | Matched later record/manifest | Supplied to Stage B under same filename |
| --- | --- | --- | --- | --- | --- | --- |
| `API-A-REVISED-WORKBOOK-v1.md` | | | `REVISED COMPLETE` | | | |
| `API-A-REVISED-CAPABILITY-BRIEF-v1.md` | | | `REVISED COMPLETE` | | | |

A rename, regenerated copy, summary, substitution, omission, missing record or
manifest, mismatch, wrong pre-hash state, or missing detached verification
stops detailed read-back.

## Artifact freezes

| Freeze | Governed artifact exact filename and pre-hash state | Governing manifest filename/hash | Observed manifest-verification timestamp/timezone | Later detached verification-record filename | Next-phase input manifest filename/hash | Preserved location |
| --- | --- | --- | --- | --- | --- | --- |
| Stage A initial | `API-A-INITIAL-WORKBOOK-v1.md`; `API-A-INITIAL-CAPABILITY-BRIEF-v1.md`; `INITIAL COMPLETE` | `API-A-INITIAL-ARTIFACTS-SHA256SUMS-v1.txt` / | | `API-A-INITIAL-FREEZE-VERIFICATION-v1.md` | `API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt` /; includes `API-A-LIVE-UPDATE-v1.md` | |
| Stage A revised | `API-A-REVISED-WORKBOOK-v1.md`; `API-A-REVISED-CAPABILITY-BRIEF-v1.md`; `REVISED COMPLETE` | `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt` / | | `API-A-REVISED-FREEZE-VERIFICATION-v1.md` | `API-A-HANDOFF-PHASE-INPUT-SHA256SUMS-v1.txt` / | |
| Stage A handoff | `API-A-ONE-SCREEN-HANDOFF-v1.md`; `HANDOFF COMPLETE` | `API-A-HANDOFF-SHA256SUMS-v1.txt` / | | `API-A-HANDOFF-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-1-INPUT-SHA256SUMS-v1.txt` / | |
| Stage B Section 1 | `API-B-SECTION-1-SCAN-v1.md`; `SECTION COMPLETE` | `API-B-SECTION-1-SHA256SUMS-v1.txt` / | | `API-B-SECTION-1-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-2-INPUT-SHA256SUMS-v1.txt` / | |
| Stage B Section 2 | `API-B-SECTION-2-DETAIL-v1.md`; `SECTION COMPLETE` | `API-B-SECTION-2-SHA256SUMS-v1.txt` / | | `API-B-SECTION-2-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-3-INPUT-SHA256SUMS-v1.txt` / | |
| Stage B Sections 3-5 | `API-B-SECTIONS-3-5-DECISION-v1.md`; `SECTION COMPLETE` | `API-B-SECTIONS-3-5-SHA256SUMS-v1.txt` / | | `API-B-SECTIONS-3-5-FREEZE-VERIFICATION-v1.md` | `API-B-PHASE-4-DEBRIEF-INPUT-SHA256SUMS-v1.txt` / | |

## Detached-record required-field audit

Do not infer missing history. Each row must match the detached record and the
facilitator execution/access log. Any blank, failed verification, output
omission, or record completion that is not explicitly later blocks `FROZEN`.

| Scope | Attempt ID | Phase | Artifact actor | Facilitator | Manifest verifier | Exact command | Complete observed output | Exit code | Verification timestamp/timezone | Record-completing actor | Later record-completion timestamp/timezone | Chronology and log match |
| --- | --- | --- | --- | --- | --- | --- | --- | ---: | --- | --- | --- | --- |
| Stage A initial | | | | | | | | | | | | |
| Stage A revised | | | | | | | | | | | | |
| Stage A handoff | | | | | | | | | | | | |
| Stage B Section 1 | | | | | | | | | | | | |
| Stage B Section 2 | | | | | | | | | | | | |
| Stage B Sections 3-5 | | | | | | | | | | | | |

## Declared counts and full-route closure

- Declared participant-input count:
- Actual release count:
- Actual open/read count:
- Governed scored artifact count:
- Manifest-verification count:
- Detached-record count; expected six:
- Stage-boundary event count/result:
- Debrief input/output count/result:
- Five-member Stage A revision binding result:

| Closure layer | State | Evidence and negative boundary |
| --- | --- | --- |
| Six scored freeze chains | complete / partial / deviated / not interpretable | |
| Selected entry branch and both context gates | complete / partial / deviated | |
| Stage A start/feedback/end | complete / partial / deviated | |
| Stage B start/scoring end/debrief/end | complete / partial / deviated | |
| Immutable run-specific results before log close | complete / partial / deviated | |
| Later external closeout | pending until after log close / complete / deviated | |

Do not call the full route complete while external closeout is pending or
deviated. Six scored freeze chains complete is not full-route completion.

## Timing and interventions

- Exact `STAGE_A_STARTED` checkpoint:
- Exact Stage A material-feedback completion and `STAGE_A_FEEDBACK_COMPLETED` checkpoint:
- Exact Stage A end and `STAGE_A_ENDED` checkpoint:
- Exact `STAGE_B_STARTED` checkpoint:
- Exact scoring end and `SCORING_ENDED` checkpoint:
- Exact debrief-input verification checkpoint:
- Exact Section 6 completion and `DEBRIEF_COMPLETED` checkpoint:
- Exact Stage B end and `STAGE_B_ENDED` checkpoint:

| Stage/activity | Start | End | Elapsed | Notes |
| --- | --- | --- | ---: | --- |
| A selected-branch setup before branch-record read | | | | |
| A start before first file read | | | | |
| A recognition | | | | |
| A artifact | | | | |
| A live update | | | | |
| A handoff | | | | |
| A material feedback after handoff freeze | | | | |
| B selected-branch setup before branch-record read | | | | |
| B start before first file read | | | | |
| B one-screen read-back | | | | |
| B Section 1 freeze | | | | |
| B revised-detail verification | | | | |
| B Section 2 freeze | | | | |
| B Sections 3-5 freeze | | | | |
| B Section 6 debrief | | | | |
| B decision | | | | |

| Stage | Sequence | File opened | Open time | Close time | Notes |
| --- | ---: | --- | --- | --- | --- |
| | | | | | |

| Time | Stage | Pause, question, or observable route friction | Response or intervention | Level |
| --- | --- | --- | --- | --- |
| | | | | |

| Time | Exact intervention | Level | Gate affected | Interpretation effect |
| --- | --- | --- | --- | --- |
| | | | | |

## Gate results

### Handoff layout proof

- Handoff Markdown exact filename/hash:
- PDF exact filename/hash:
- Layout-proof record exact filename/hash:
- US Letter portrait, one page, margins at least 0.5 inch, body/table text at
  least 9 points, reader-facing words no more than 450 excluding immutable
  provenance, no clipping, overlap, hidden overflow, or unreadable shrinking:
  pass / hold / unrun
- Layout finding and retained failure, if any:
- Human scanability/comprehension evidence: `UNRUN` unless separately consented

| Gate | Score/state | Exact evidence | Negative or boundary finding |
| --- | --- | --- | --- |
| RV-1 | | | |
| RV-2 | | | |
| RV-3 | | | |
| RV-4 | | | |
| RV-5 | | | |
| RV-6 | | | |
| RV-7 | | | |

- One-screen handoff scanability evidence:
- Owner recorded as assigned or `UNASSIGNED`; assignment authority/trigger:
- Review date or evidence-based trigger; basis:

## Deviations and stops

The planned live-update revision is not a correction of frozen revised bytes.
For every later correction, retain both old and new immutable artifacts and
their governing records.

| ID | Condition/reason | Correction timestamp/timezone | Exact old filename, ID/version, SHA-256, manifest, verification record | Exact new filename, ID/version, SHA-256, manifest | Replacement detached verification record | Action/effect |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | | | |

## Findings and disposition

| ID | Finding | Source | Severity | Revise / retest / hold / remove | Owner | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | | | |

## Truthful state statement

- What this exact pair establishes:
- What it does not establish:
- Protocol integrity state:
- Synthetic behavior state:
- Local layout state:
- Human evidence state: `PREPARED/UNRUN` unless a consented human run occurred
- Real-world evidence state: `UNRUN`
- Packet state after authorized review:
- Files changed only after raw evidence was preserved:
- Next attempt and version:

## Pre-close completion

- Every required field complete: yes / no / deviation
- `RUN_RESULTS_COMPLETED` event ID/continuity binding:
- Run-results completion timestamp/timezone:
- Run-results state: `RUN RESULTS COMPLETE` / invalid
- Authorized next event: `LOG_CLOSED` only after this record is immutable
