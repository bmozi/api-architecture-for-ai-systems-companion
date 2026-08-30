# Stage A Practitioner Workbook

**Packet:** API-RV-PILOT-001 version 1.2.1
**Status:** Blank participant record

**Revision note:** Version 1.2.1 makes every freeze temporally ordered and
non-self-referential after static protocol review; it has no human or
practitioner validation.

- Participant code:
- Broad role and experience band, optional:
- Stage start recorded before first file read, with timezone, and end time:
- Exact file-open order:
- Frozen supplied-file manifest:

## 1. Recognition before terminology

- Who needs what outcome?
- What is frustrating, slow, unsafe, or impossible today?
- What could become newly possible if this capability were dependable?
- What could go wrong if “accepted” is mistaken for “complete”?

## 2. Explain it to someone outside the team

In no more than five sentences, explain the capability, who may use it, what
can remain pending, and how a final result becomes trustworthy.

## 3. Artifact record

- Completed brief file ID/version:
- Mechanisms selected and the one job assigned to each:
- Mechanisms rejected and why:
- Authority left unknown:
- Prohibited inference:
- Business identity that survives retries and tool calls:
- Authoritative record if systems disagree:
- Final completion evidence:
- Stop or escalation condition:

## 4. Monday-morning decision

- Smallest useful design or policy change:
- First failure to test:
- Owner of that test, or `UNASSIGNED` plus authority/trigger to assign one:
- Result that would block or reverse the design:

## 5. Live update

Record the update exactly as supplied.

This is the planned live-update revision that creates the first revised set.
It is not a correction of already frozen revised bytes.

- Initial answer now challenged:
- Safe action for the partner:
- Stonebridge's remaining obligation and authorized owner, or `UNASSIGNED`
  plus assignment authority/trigger:
- Duplicate, charge, event, or notification risk:
- Artifact fields revised:
- Evidence still missing:
- Interim instruction to the customer or partner:
- Who may issue that instruction:
- Evidence supporting the instruction:
- What must remain unsaid:

## 6. Cross-role handoff

Before opening the handoff, save and freeze exactly:

- `API-A-REVISED-WORKBOOK-v1.md`; and
- `API-A-REVISED-CAPABILITY-BRIEF-v1.md`.

Each file must record an artifact ID, version, completion timestamp/timezone,
and pre-hash state `REVISED COMPLETE`. Do not make the artifact self-declare
`FROZEN`. Create
`API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt` without listing or hashing the
manifest itself. Verify that manifest and capture the exact verification
timestamp/timezone. Only then complete
`API-A-REVISED-FREEZE-VERIFICATION-v1.md` from the detached record template.
The later record describes the observed event; it is not governed by the
manifest it describes and does not claim its own hash.

- Revised workbook artifact ID/version, completion timestamp/timezone, and
  pre-hash state:
- Revised capability-brief artifact ID/version, completion timestamp/timezone,
  and pre-hash state:
- Governing manifest filename:
  `API-A-REVISED-ARTIFACTS-SHA256SUMS-v1.txt`
- Detached verification record to inspect after this workbook is hashed:
  `API-A-REVISED-FREEZE-VERIFICATION-v1.md`
- Do not enter the later verification time, this workbook's hash, the manifest
  hash, or the record hash inside this governed workbook.
- No `DRAFT`, `PENDING`, `PENDING FREEZE`, `AWAITING FREEZE`, blank, or
  equivalent incomplete state remains: yes / no

Only after the manifest has verified, the detached record has been created,
and a sealed handoff-phase input manifest hashes the two revised artifacts,
their governing manifest, and that record, complete [the One-Screen Stage A
Handoff](05-one-screen-handoff.md) as
`API-A-ONE-SCREEN-HANDOFF-v1.md`. Link the literal filenames, IDs, versions,
and hashes. If no accountable owner is authorized, record `UNASSIGNED` and
name the authority or trigger needed to assign one. Use either a justified
calendar date or an evidence-based reconsideration trigger; do not invent one.

- Handoff freeze evidence: see the later detached
  `API-A-HANDOFF-FREEZE-VERIFICATION-v1.md`, governed for the next phase by the
  next sealed input manifest.

If any revised frozen byte later changes, preserve the old file and record the
exact old/new immutable filenames, IDs/versions, hashes, reason, correction
timestamp/timezone, replacement detached verification record, and replacement manifest. Do
not describe that post-freeze correction as the planned live-update revision.

## 7. Material feedback

- Prompt that changed your thinking:
- Term or field that was unclear:
- Important decision the materials missed:
- Any prompt that pushed you toward an unsupported answer:
- What this exercise cannot establish:
