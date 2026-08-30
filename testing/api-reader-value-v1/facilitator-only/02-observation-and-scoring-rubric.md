# Observation and Scoring Rubric

**Packet:** API-RV-PILOT-001 version 1.2.4
**Status:** Predetermined, blank, and unrun

**Revision note:** Version 1.2.4 binds the exact immutable Stage A live-update
input into the revision-phase manifest. It preserves version 1.2.3's replay
identity, verification chronology, and external access logging and remains
unrun with people.

Score retained behavior, not agreement with preferred vocabulary.

## Scale

- **2 — unaided and defensible:** explicit, coherent, and reached with L0–L1.
- **1 — partial or prompted:** material issue appears but is incomplete or
  requires L2–L3.
- **0 — absent, contradicted, unsafe, or coached:** missed, invented, unsafe,
  or supplied by L4.
- **NA — not interpretable:** missing or materially contaminated evidence.

Do not use the total as a validated psychometric score.

## Seven reader-value gates

| Gate | Observable evidence | Stage | Score | Evidence location |
| --- | --- | --- | ---: | --- |
| RV-1 Recognition | Names the human need and consequence before mechanisms | A | | |
| RV-2 Plain understanding | Explains the capability and pending/final distinction outside API jargon | A and B | | |
| RV-3 First useful artifact | Produces a bounded capability record with explicit unknowns | A | | |
| RV-4 Outside read-back | Stage B scans the one-screen handoff, then reconstructs promise, authority, open work, and proof without repair | B | | |
| RV-5 Failure discovery | Detects false completion, duplicated charge risk, premature event, and lost responsibility | A | | |
| RV-6 Team transfer | Scanable handoff yields decision, allowed/withheld scope, evidence, unknowns, next action, an assigned owner or `UNASSIGNED` with assignment authority/trigger, and a review date or evidence-based trigger | B | | |
| RV-7 Decision-owner legibility | Selects a bounded state without inventing ROI or approval | B | | |

## Critical API gates

Mark `clear`, `unclear`, `unsafe`, or `contaminated`:

| Gate | Clear behavior | Result | Evidence |
| --- | --- | --- | --- |
| Authority | Authentication, staff identity, customer intent, and agent delegation remain distinct | | |
| Accepted versus completed | Neither participant treats receipt as final outcome | | |
| Duplicate effect | Retry identity covers the business intent and charge consequence | | |
| Event truth | `confirmed` is not emitted before confirmation authority and evidence | | |
| Durable ownership | An authorized owner is named, or `UNASSIGNED` is explicit with the authority/trigger needed to assign review, ambiguity, correction, and customer communication | | |
| Outcome evidence | Tool call, charge, warehouse decision, event, notification, and final rental state can be reconciled | | |
| Revision-input integrity | `API-A-REVISION-PHASE-INPUT-SHA256SUMS-v1.txt` hashes both initial artifacts, their governing manifest, detached record, and exact immutable `API-A-LIVE-UPDATE-v1.md`; the file opens only after verification, with no omission, rename, regeneration, summary, substitution, or mismatch | | |
| Revised-detail freeze integrity | Each revised detail reaches pre-hash `REVISED COMPLETE` with ID/version and completion timestamp/timezone; the governing manifest then hashes only those bytes; verification occurs next; and only afterward does the detached record describe the observed timestamp/timezone, artifact identities/hashes, and manifest filename/hash. The manifest hashes neither itself nor the later record, and the record claims no self-hash | | |
| Handoff freeze integrity | The handoff reaches `HANDOFF COMPLETE` before its manifest is created; verification precedes its detached record; the Stage B phase-1 input manifest hashes the handoff, governing manifest, and detached record | | |
| Stage B exact transfer | Stage B receives the detached revised verification record, governing manifest, and every handoff-linked revised detail under the same literal filename with matching ID/version, completion metadata, pre-hash state, and hash; no rename, regeneration, summary, substitution, or omission occurs | | |
| Stage B sequencing | Sections 1, 2, and 3-5 each reach `SECTION COMPLETE`, receive a governing manifest, undergo verification, and only then receive a detached record. Each next-phase input manifest hashes the prior export, manifest, and record; Section 6 remains closed until the final debrief-phase manifest verifies and scoring ends | | |
| Temporal non-self-reference | No governed artifact embeds its own hash or later freeze time; no governing manifest lists itself or the later verification record; no detached record claims its own hash; every record timestamp describes an event that already occurred | | |
| Detached-record replay identity | Every record contains attempt ID, phase, artifact actor, facilitator, verifier, exact verification command, complete output, exit code, observed verification timestamp/timezone, record-completing actor, and a separately recorded later completion timestamp/timezone; any blank, failure, or reversal blocks `FROZEN` | | |
| Execution/access continuity | The facilitator-side log records ordered manifest gates, item opens/access attempts, artifact completions, manifest creations/verifications, record completions, and phase opens with filenames, actors, timestamps/timezones, predecessor bindings, and manifest SHA-256; participant input contains no undeclared orchestration or facilitator file | | |
| Revision/correction provenance | The planned live-update revision is distinct from a later correction of frozen revised bytes; every correction preserves old/new immutable filenames, IDs/versions, hashes, reason, timestamp/timezone, replacement detached verification record, and replacement manifest | | |

Any unsafe critical gate blocks a favorable interpretation regardless of total.

Do not reward an invented owner, assignment authority, calendar date, or review
trigger. Record handoff scanability and whether Stage B had to search detailed
artifacts before it could identify the bounded decision.

## Findings to record

- exact prompt and participant words;
- initial and revised interpretation;
- intervention level;
- wording or route that caused friction;
- useful behavior to preserve;
- likely source: material, scenario, participant, facilitator, or unresolved;
- severity and proposed disposition; and
- regression condition for any change.

## Interpretation

Use only bounded language: complete, partial, materially unclear, unsafe, or
inconclusive for this participant, version, scenario, and stage. Do not claim
broad usability, correctness, safety, or benefit.
