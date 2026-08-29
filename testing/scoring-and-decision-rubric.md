# Scoring and Decision Rubric

## Evidence boundary

The score summarizes one participant's use of one fictional scenario. It is not
a certification score, a ranking of the participant, or proof of architectural
correctness. Preserve the underlying quotations, worksheet entries, timing,
and intervention levels; the total alone is not evidence.

Score the participant's meaning even when they do not use the book's preferred
terms. Accept more than one architecture when the promise, authority,
responsibility, recovery, and evidence are coherent.

## Item scoring

- **2 - Unaided and defensible:** The answer is explicit, internally coherent,
  grounded in the scenario, and reached with L0-L1 support.
- **1 - Partial or prompted recovery:** The answer exposes the issue but is
  incomplete, or becomes defensible after an L2-L3 intervention.
- **0 - Absent, contradicted, unsafe, or coached:** The issue is missed,
  contradicted elsewhere, remains unsafe, or L4 coaching supplies the answer.
- **NA - Not interpretable:** Evidence is missing or contaminated. Do not turn
  NA into zero; explain it and report the scored denominator.

## Scored domains

| # | Domain | Evidence for a defensible answer | Score 0-2 | Notes and intervention |
| ---: | --- | --- | ---: | --- |
| 1 | Consumer outcome and limit | States what HomePort needs and what Cedarway does not promise | | |
| 2 | Accountability and authority | Keeps Cedarway accountable to HomePort; distinguishes caller identity, homeowner/visit scope, and approval authority | | |
| 3 | Initial response meaning | Defines what HomePort may safely infer without equating a status code or sent vendor call with completion | | |
| 4 | Completion and terminal outcomes | Names evidence for an actual move and covers rejection, retained original appointment, or another terminal alternative | | |
| 5 | Repetition and business identity | Recognizes the same change intent across attempts and prevents a second business effect | | |
| 6 | Conflict, time, and original appointment | Defines stale/conflicting change behavior and what happens to the original visit while a move is unresolved | | |
| 7 | Failure and safe consumer action | Gives different safe actions for invalid, unauthorized, conflict, pending, terminal, transient, and unknown outcomes where applicable | | |
| 8 | Unknown downstream result | Treats an ambiguous RouteSpring result as requiring reconciliation rather than blind replacement | | |
| 9 | Mechanism selection | Selects only needed mechanisms and states each job without using one to silently carry another's promise | | |
| 10 | Responsibility across delay | Names who owns progress, human review, deadlines, escalation, and terminal communication | | |
| 11 | Shared identity and disagreement | Connects records across mechanisms and names containment/reconciliation when they disagree | | |
| 12 | Evidence and explicit unknowns | Proposes meaningful authorization, behavioral, failure, consumer, and operational evidence; leaves unsupported facts open | | |

- **Raw score:** / 24
- **Scored items:** / 12
- **Normalized percentage, only if NA exists:**

## Critical safety gates

These gates prevent a high total from hiding one dangerous conclusion. Mark
each `clear`, `unclear`, `unsafe`, or `contaminated`.

| Gate | Clear means | Result | Evidence |
| --- | --- | --- | --- |
| Duplicate-effect gate | Timeout or retry cannot silently create a second move or contradictory appointment | | |
| Truthful-outcome gate | HomePort is not told the visit moved before the defined completion evidence exists | | |
| Accountability gate | Cedarway does not transfer its external responsibility to RouteSpring, an event consumer, or HomePort | | |
| Delegated-authority gate | Authentication alone does not grant authority for every visit or homeowner | | |
| Disagreement gate | Conflicting records trigger containment and reconciliation, not last-message-wins behavior | | |

An `unsafe` critical gate blocks a “tentative comprehension” result regardless
of total. A `contaminated` gate requires another session or uncoached retest.

## Session interpretation

Apply only when at least 10 of 12 domains are scorable:

- **Tentative comprehension in this scenario:** 80% or higher, every critical
  gate clear, and no L4 coaching on a critical domain.
- **Material friction:** 55-79%, or one or more critical gates unclear. Identify
  the exact tool fields and recovery behavior before proposing revisions.
- **Material misinterpretation:** Below 55%, or any critical gate unsafe.
  Determine whether the likely cause is tool wording, scenario ambiguity,
  facilitator behavior, or an interpretation the tool failed to correct.
- **Inconclusive:** Fewer than 10 scorable domains, major facilitator
  contamination, consent/data problem, or early stop that prevents the central
  questions from being observed.

These thresholds are proposed decision aids, not validated psychometrics.

## Asset-revision decision

For each material finding, choose one:

| Decision | Use when | Required record |
| --- | --- | --- |
| Revise now for safety | One severe interpretation is plausibly induced by the tool and could cause duplicate effects, false outcomes, unauthorized action, lost responsibility, or unsafe disagreement resolution | Exact wording, participant interpretation, risk, proposed change, regression check |
| Test across another participant | The issue is real but could arise from personal terminology or scenario reading | Frozen wording, same probe, expected disambiguating evidence |
| Clarify the scenario | The tool exposed a legitimate question but the scenario omitted facts needed to reason about it | Missing fact and why adding it does not reveal a target answer |
| Change facilitator method | A prompt, definition, timing choice, or visible material steered the response | Contaminating intervention and corrected procedure |
| Hold | One participant disliked wording but completed it safely and no repeated pattern exists | Evidence and condition that would trigger reconsideration |
| Remove or merge a field | Repeated use shows duplication or burden without a distinct decision | Fields affected and decision that remains covered elsewhere |

Prefer repeated, unprompted misinterpretation across participants before making
a broad language change. After any change, rerun the relevant scenario and at
least one different scenario so a local fix does not make the asset
prescriptive elsewhere.

## Claims allowed after one completed session

Allowed with evidence:

- “One practitioner interpreted field X as Y.”
- “The participant recovered after neutral prompt Z.”
- “The scenario exposed an unsafe retry interpretation.”
- “The asset was revised in response to this bounded result.”

Not allowed:

- “Practitioners understand the method.”
- “The tool produces correct architectures.”
- “The tool prevents incidents.”
- “The design is secure, reliable, compliant, or production ready.”
- “The workshop or book improves business outcomes.”
