# One-Screen Stage A Handoff

**Packet:** API-RV-PILOT-001 version 1.2.6
**Status:** Blank; open only after the revised-detail governing manifest has
verified, its detached verification record exists, and the handoff-phase input
manifest verifies
**Revision note:** Version 1.2.5 adds a proof-gated one-page contract while preserving version 1.2.4's exact immutable Stage A live-update
input and preserves version 1.2.3's replay, chronology, and access-log
controls. It remains unrun with people.

The declared local target is US Letter portrait, exactly one page, margins of
at least 0.5 inch, body and table text of at least 9 points, no more than 450
reader-facing words excluding immutable provenance, and no clipping, overlap,
hidden overflow, or unreadable shrinking. Link detail instead of repeating it.
Use `UNKNOWN` rather than guessing. An owner may be `UNASSIGNED`; do not invent
an assignment or date. Complete this as `API-A-ONE-SCREEN-HANDOFF-v1.md` only
after `API-A-REVISED-FREEZE-VERIFICATION-v1.md` exists and the sealed
handoff-phase input manifest verifies.

Do not claim `LAYOUT PASSED` inside this governed handoff. After its freeze,
the facilitator must preserve the Markdown, PDF, page count, rendering command,
tool versions, PDF SHA-256, and clipping/overlap findings in
`API-A-HANDOFF-LAYOUT-PROOF-<ATTEMPT-ID>-v1.md`. A favorable `LAYOUT PASSED`
claim requires every proof row to pass. Layout evidence is not human
scanability, comprehension, usefulness, safety, or business-value evidence.

- Handoff ID/version:
- Handoff completion timestamp/timezone:
- Handoff pre-hash state: `HANDOFF COMPLETE` / invalid
- Linked scenario and input-template IDs/versions:
- Detached revised freeze-verification record exact local filename/hash:
  `API-A-REVISED-FREEZE-VERIFICATION-v1.md` /
- Governing revised-artifact manifest exact local filename/hash:
  `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt` /

## Exact revised-detail inventory

Stage B must receive both files under these literal local filenames. Copy the
IDs, versions, states, and hashes from the verified detached record. A rename,
regenerated copy, summary, substitution, omission, mismatch, pre-hash state
other than `REVISED COMPLETE`, or missing detached `FROZEN` verification stops
detailed read-back.

| Exact local filename | Artifact ID/version | Completion timestamp/timezone | Pre-hash state | SHA-256 | Detached freeze status |
| --- | --- | --- | --- | --- | --- |
| `API-A-REVISED-WORKBOOK-v1.md` | | | `REVISED COMPLETE` | | `FROZEN` |
| `API-A-REVISED-CAPABILITY-BRIEF-v1.md` | | | `REVISED COMPLETE` | | `FROZEN` |

## Decision transfer

- Current state:
- Evidence class (`REPORTED` / `INFERRED` / `PROPOSED` / `UNKNOWN`):
- Beneficiary and outcome:
- Decision needed now:
- Allowed now:
- Withheld:
- Accountable owner, or `UNASSIGNED`:
- If `UNASSIGNED`, authority or trigger needed to assign; use `UNKNOWN` if not
  known:
- Authority to act, or `UNKNOWN`:
- Known evidence:
- Unknowns:
- Unacceptable outcome:
- Immediate next action:
- Interim customer/partner instruction:
- Authority and evidence for that instruction:
- Review date **or** evidence-based reconsideration trigger:

After every field is final, retain `HANDOFF COMPLETE`, hash this handoff alone
in `API-A-HANDOFF-SHA256SUMS-v1.txt`, verify that manifest, and only then create
`API-A-HANDOFF-FREEZE-VERIFICATION-v1.md`. Do not put this handoff's later
verification timestamp, its own SHA-256, the manifest hash, or the detached
record hash inside this governed handoff. The Stage B phase-1 input manifest
hashes the handoff, governing manifest, and detached record.
