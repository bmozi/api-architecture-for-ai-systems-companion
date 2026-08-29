# Observation Rubric

## Use

Record behavior and exact language before judging correctness. This rubric is
facilitator-only. It distinguishes a tool that supports safe recovery from a
tool that produces a plausible-looking completed worksheet.

For every observation, record:

- the prompt or scenario moment;
- what the participant wrote or said;
- whether the observation was spontaneous;
- the intervention level, if any;
- whether the participant revised their answer; and
- the remaining risk after revision.

## Recovery scale

| Code | Observation |
| --- | --- |
| R0 | No material misinterpretation observed; participant states a defensible answer unaided |
| R1 | Initial hesitation or mistake; participant corrects it without facilitator content |
| R2 | Participant recovers after an L1 repeat or L2 neutral probe |
| R3 | Participant changes only after an L3 definition |
| R4 | Unsafe or contradictory interpretation persists, or L4 coaching supplies the answer |
| NA | Scenario does not expose the issue or evidence is too contaminated to interpret |

R0 is not proof that the design is correct. R1 and R2 are especially useful:
they show whether the tool helps the participant catch their own error.

## Field-use observations

| Item | What to observe | Evidence and recovery code |
| --- | --- | --- |
| Completion behavior | Fields skipped, duplicated, marked unknown, or completed with unjustified certainty | |
| Prompt comprehension | Terms requested, re-read, or interpreted inconsistently | |
| Business versus machinery | Outcome and decision versus endpoint, status, schema, queue, or vendor name | |
| Missing facts | Explicit blocker or invented assumption | |
| Role precision | Company accountability versus team, system, vendor, or individual implementation owner | |
| Evidence discipline | Proposed checks versus claims that a schema or generated code proves behavior | |
| Tool burden | Time, fatigue, repetition, abandonment, or loss of the governing question | |

## Misinterpretation watch list

Do not hint at these during the scored session. Record the participant's words.

| Potential misinterpretation | Observable signal | Safe recovery signal | Code |
| --- | --- | --- | --- |
| Authentication equals permission | “The service account is valid, so the agent can move any visit.” | Distinguishes known caller from authority to act for this homeowner and visit | |
| Provider equals downstream vendor | RouteSpring is named as the party accountable to HomePort | Cedarway retains its external promise and treats vendor evidence as an input | |
| Transport success equals business completion | Sent call or `200` means the visit moved | Names a business condition and evidence for a completed move | |
| Receipt equals acceptance | Cedarway receiving the request means it has promised the requested time | Defines what Cedarway has actually assumed responsibility for | |
| Only happy terminal state | Only “moved” is treated as completion | Includes rejection, retention of original visit, cancellation, or another explicit terminal result | |
| Request ID equals business identity | Every retry gets a new identity | Same intent can be recognized across transport attempts without creating a second effect | |
| Timeout equals failure | HomePort may submit a replacement because no reply arrived | Treats the result as unknown until reconciled; prescribes a non-duplicating recovery path | |
| Original visit silently disappears | Requested move invalidates the original immediately | Preserves or explicitly resolves the original appointment under a stated rule | |
| Primary boundary means only mechanism | Selects one mechanism and ignores remaining responsibility or reactions | Uses one mechanism with justification or composes several with distinct jobs | |
| Event receipt proves the fact | Notification acts on any `VisitMoved` message as authoritative | Names declaration authority, meaning, version/provenance, and disagreement handling | |
| Message coordinates completion | Publishing an event transfers responsibility to consumers | A named owner remains responsible for progress and terminal resolution | |
| Last writer or last message wins | Whichever system updated most recently becomes truth | Names an authoritative decision/reconciliation process and contains contradictory action | |
| Human wait has no owner | “Pending review” has no owner, deadline, escalation, or customer message | Names current responsibility, deadline, escalation, and safe interim behavior | |
| Generated artifact is evidence | OpenAPI or implementation completion is treated as proof | Names behavioral, failure, authority, consumer, and operational evidence still required | |

## Live-update observations

### Update A: ambiguous RouteSpring timeout

- Did the participant allow the new request ID to create a second change?
- Did they preserve the relationship to the original business intent?
- Did they distinguish “failed,” “not accepted,” and “unknown”?
- Did they give HomePort a safe action and Cedarway a reconciliation duty?
- Did their tool entries already expose the problem, or did the update reveal a
  missing field?
- **Recovery code:**
- **Exact evidence:**

### Update B: contradictory records and notification

- Did the participant assume the message or latest timestamp was true?
- Did they contain further notifications or technician actions while evidence
  disagreed?
- Did they name how the consumer learns a corrected answer?
- Did they retain provenance rather than overwrite the disagreement?
- **Recovery code:**
- **Exact evidence:**

### Update C: delayed human decision

- Did the participant identify who owns the next action before the original
  appointment begins?
- Did they invent approval because the deadline was inconvenient?
- Did they explain whether the original appointment remains in force?
- Did they name escalation and a safe message to HomePort?
- Did they change their mechanism choice or explain why it still works?
- **Recovery code:**
- **Exact evidence:**

## Facilitator contamination log

| Time | Intervention | Level | Item affected | Participant response | Scoring restriction |
| --- | --- | --- | --- | --- | --- |
| | | | | | |

## Post-session usability findings

| Finding | Exact evidence | Likely source | Severity | Candidate action |
| --- | --- | --- | --- | --- |
| | | Tool / Scenario / Participant / Facilitator / Unresolved | Low / Medium / High / Critical | |
