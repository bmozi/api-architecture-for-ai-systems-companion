# Role-Based Paths

Use one capability from your real work. Do not try to complete every asset
before you have one useful decision.

**Status:** Prepared development routes. They have not yet been validated with
representative readers.

## Developer or API designer

**What you need:** A contract you can implement without guessing what success,
failure, repetition, or authority means.

1. Complete [Start Here](START-HERE.md).
2. Use the [Meaning-and-Authority Brief](api-meaning-and-authority-brief.md).
3. Translate it into the [AI-Ready OpenAPI Brief](ai-ready-openapi-implementation-brief.md).
4. Run the [Failure Lab](FAILURE-LAB.md).
5. Preserve every unknown as a design question instead of filling it with a
   generated assumption.

**Useful result:** One implementable capability brief plus a failure the
contract must survive.

## Architect or staff/principal engineer

**What you need:** A defensible boundary across API, MCP, event, workflow, data,
and agent responsibilities.

1. Complete the [interaction decision guide](api-event-workflow-decision-tree.md).
2. Add the [Authority and Delegation Map](authority-and-delegation-map.md).
3. Challenge repetition and evolution with the
   [Idempotency Matrix](idempotency-and-outcome-test-matrix.md) and
   [Compatibility Matrix](compatibility-evidence-matrix.md).
4. Join the result in the [Outcome Evidence Map](outcome-evidence-map.md).

**Useful result:** A reviewable capability boundary with explicit handoffs and
evidence.

## Engineering, product, service, or operations manager

**What you need:** A repeatable review that produces owners and decisions rather
than another architecture meeting.

1. Bring one requested capability to the [Team Workshop](TEAM-WORKSHOP.md).
2. Use the [Value and Evidence Ledger](VALUE-AND-EVIDENCE-LEDGER.md) to connect
   the contract to customer, delivery, support, and operating outcomes.
3. Assign owners for unresolved meaning, authorization, capacity, compatibility,
   and evidence.
4. Schedule the reconsideration review before implementation confidence becomes
   release confidence.

**Useful result:** A bounded decision, accountable owners, and a dated evidence
plan.

## CTO, CIO, business executive, or portfolio decision-maker

**What you need:** To decide whether a reusable capability deserves investment
and whether its operating commitment is understood.

1. Read the [Executive Decision Brief](EXECUTIVE-DECISION-BRIEF.md).
2. Ask which customers, applications, automations, or agents can reuse the
   capability and which powers remain withheld.
3. Review the value ledger's costs, dependencies, leading evidence, and stop
   condition.
4. Choose `EXPLORE`, `PROCEED BOUNDED`, `INVEST`, `HOLD`, or `STOP`.

**Useful result:** A legible investment decision without pretending an endpoint
or demonstration proves business value.

## Cross-role read-back

After any path, ask someone in another role to explain:

- what capability is promised;
- who may invoke it and for whom;
- what the consumer may promise next;
- what happens after a duplicate or unknown outcome; and
- which evidence determines the next decision.

If the explanation requires unwritten team history, the artifact is not ready
to govern implementation.
