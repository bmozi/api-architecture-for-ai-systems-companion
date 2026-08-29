# Facilitator Guide

## Status

This guide prepares an independent-practitioner session. It does not record a
completed session or a usability result.

## Test purpose

The session evaluates two blank companion assets:

- the API Meaning-and-Authority Brief; and
- the API/Event/Workflow Decision Tree.

The primary observation is not whether the participant reproduces the book's
language. It is whether the materials help the participant notice consequential
decisions, avoid unsafe conclusions, and recover from ambiguity without being
coached toward a target architecture.

## Non-goals

Do not use this session to:

- assess the participant's job performance;
- teach the book before measuring unaided use;
- prove that one architecture is universally correct;
- validate production security, reliability, compliance, or business value;
- collect real employer or customer incidents; or
- turn one person's agreement into evidence of broad usability.

## Facilitator qualification and behavior

The facilitator should be able to recognize unsafe retry, false completion,
lost responsibility, authority confusion, and mechanism disagreement. During
the scored portion, that knowledge is used to observe and probe—not to teach.

Use a calm think-aloud format. Ask the participant to explain what a prompt
means to them before defining it. Record exact questions and interventions.
Silence, uncertainty, and “I do not know” are useful results.

## Prepare before recruiting

1. Complete the storage, access, retention, and deletion fields in
   `consent-and-privacy-boundaries.md`.
2. Assign a participant code that cannot identify the person by itself.
3. Freeze and record the versions or hashes of:
   - `participant-scenario-cedarway.md`;
   - `participant-response-workbook.md`;
   - `../api-meaning-and-authority-brief.md`; and
   - `api-event-workflow-decision-tree-frozen.md`.
4. Create clean working copies of the workbook and both blank tools.
5. Keep the Northbridge example, Harborline desk test, observation rubric,
   scoring rubric, and this guide out of participant view.
6. Decide whether the session is in person or remote. Verify that the
   participant can edit the materials without exposing other repository files.
7. Do not record audio, video, or the screen unless separate consent and a
   retention plan are complete.

## Recommended session length

Allow 70-85 minutes:

| Activity | Target time |
| --- | ---: |
| Consent, boundaries, and think-aloud instruction | 5 minutes |
| Scenario reading and unaided Part 1 | 10 minutes |
| Meaning-and-Authority Brief | 25-30 minutes |
| Decision Tree | 12-15 minutes |
| Three live updates | 12-15 minutes |
| Debrief and tool feedback | 6-10 minutes |

Time is an observation, not a speed requirement. If the participant is still
making useful progress, allow an overrun and record it. Stop if they ask to
stop, disclose confidential information that cannot be contained, or become
meaningfully uncomfortable.

## Opening script

Read or closely paraphrase:

> We are testing two worksheets, not you. The scenario is fictional. Please
> think aloud about what each prompt appears to ask. Use only the scenario;
> “unknown” is a valid answer. I may ask what you mean, but during the scored
> portion I will avoid teaching terms or recommending an architecture. You may
> skip anything or stop at any time. Please do not share identifiable details
> from your employer, customers, or vendors.

Confirm consent before opening the scenario.

## Session sequence

### 1. Unaided baseline

Give the participant only the scenario and workbook. Ask them to complete Part
1 before opening either tool. Do not correct their interpretation. This captures
whether later clarity came from the tools rather than prior prompting.

### 2. Meaning-and-Authority Brief

Provide the blank brief. Ask the participant to complete it and think aloud.
Record:

- elapsed time;
- fields skipped, repeated, or marked unclear;
- substitutions of endpoints, status codes, queues, or products for a business
  promise or decision;
- terms the participant asks the facilitator to define;
- revisions made without prompting; and
- any architecture coaching or examples supplied by the facilitator.

Do not show a completed example. Do not say that `200`, `202`, idempotency,
workflow, or any other term is the expected answer.

### 3. Decision Tree

Provide the blank decision tree only after the brief is complete or the
participant chooses to stop using it. State:

> Use as many or as few mechanisms as you believe the scenario needs. The test
> does not reward selecting all three.

Record whether “primary boundary” is read as “only mechanism,” whether one
mechanism silently inherits another's responsibility, and whether the
participant names how different records or notifications are reconciled.

### 4. Live updates

Read the updates one at a time. Do not reveal the later updates in advance.
After each, ask only:

> What can each party safely do now, and what would you change in your design?

Allow the participant to revise their tools. Record whether recovery is
spontaneous, follows a neutral probe, requires a definition, or requires direct
coaching.

#### Update A: ambiguous downstream result

> Cedarway sent RouteSpring a request to move visit `CW-8042`. The call timed
> out. RouteSpring's dashboard cannot be reached. HomePort received no response
> from Cedarway and has sent the same desired time again with a new request ID.
> The original appointment begins in four hours.

Do not ask specifically about idempotency or duplicate effects.

#### Update B: mechanisms disagree

> The notification service received `VisitMoved` and told the homeowner the
> visit is tomorrow at 2 p.m. The Cedarway Visit Store still shows the original
> time. RouteSpring later shows tomorrow at 3 p.m., and the technician
> application still routes the technician to the original appointment.

Do not ask which database or message should win. Observe whether the
participant identifies that a received notification is not self-proving and
that contradictory public action needs containment and reconciliation.

#### Update C: responsibility under time pressure

> A branch coordinator must decide because a required part and technician are
> already assigned. The coordinator cannot review the request for three hours,
> but the original appointment begins in 90 minutes. HomePort asks Cedarway
> whether it should tell the homeowner not to expect the technician.

Do not introduce workflow terminology. Observe whether the participant names a
current owner, deadline, safe public message, escalation, and treatment of the
original appointment.

### 5. Debrief

End scoring before discussion of the book's intended distinctions. Ask the
participant to complete Part 5 of the workbook. Then ask:

- Which worksheet question changed your thinking?
- Where did the worksheet imply an answer that the scenario did not support?
- What would you remove, rename, or add?
- What remained unsafe after both worksheets were complete?

Only after these responses are recorded may the facilitator explain an intended
term or show an example. Mark all post-test discussion as debrief, not scored
evidence.

## Intervention ladder

Use the least intervention necessary and record the level.

| Level | Facilitator action | Effect on evidence |
| --- | --- | --- |
| L0 | Silence or “Please continue thinking aloud.” | Unaided |
| L1 | Repeat the scenario text or tool prompt verbatim | Still uncoached; record it |
| L2 | Neutral probe: “What does that answer mean to HomePort?” or “What happens next?” | Prompted recovery |
| L3 | Give a minimal term definition without applying it to Cedarway | Aided; score the affected item no higher than 1 |
| L4 | Recommend a decision, name the missing architecture, or provide an analogous answer | Coaching contamination; stop scoring the affected item |

Avoid questions that contain the desired answer, such as “Would a workflow own
this?” or “Should they retry with the same idempotency key?”

## After the session

1. Preserve the participant's original artifacts before editing or normalizing
   them.
2. Complete the observation rubric and scoring rubric independently from the
   participant where possible.
3. Record every L2-L4 intervention against the affected result.
4. Classify each issue as tool wording, scenario ambiguity, participant
   interpretation, facilitator contamination, or unresolved.
5. Complete one results log. State explicitly that the result is from one
   fictional-scenario usability session.
6. Do not revise the assets until the raw result is preserved.
7. Prefer a repeated unprompted misread across participants as evidence for a
   wording change. A single severe unsafe interpretation can justify an urgent
   review, but not a claim of prevalence.
