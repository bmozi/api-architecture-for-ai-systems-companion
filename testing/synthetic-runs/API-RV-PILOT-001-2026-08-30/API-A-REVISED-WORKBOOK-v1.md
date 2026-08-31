# API synthetic Stage A revised workbook

Artifact ID/version: API-A-REVISED-WORKBOOK/v1
Completion timestamp/timezone: 2026-08-30T14:05:00-0600 MDT
Pre-hash state: REVISED COMPLETE
Participant branch: SYNTHETIC - NO HUMAN PARTICIPANT OR HUMAN DATA

## Recognition

Stonebridge needs a partner and customer to request one extra rental day without confusing receipt of a request with a completed extension. The unsafe outcome is a charge, warehouse change, or customer message occurring before the extension is authorized and final.

## Five-sentence explanation

The partner may request an extension for a named rental, but the request does not itself prove that Stonebridge changed the rental. Stonebridge must distinguish the authenticated partner, represented staff user, customer intent, and any authority delegated to an AI agent. Some requests remain pending while warehouse review occurs, and a timeout remains unknown until reconciled. A stable extension-intent identity must survive retries and downstream calls. Only an authoritative final decision plus billing and reservation evidence may support a completion message.

## Design record

- API: request and query the extension promise; `accepted` means received only.
- MCP tool: a constrained presentation of the approved API; no extra authority.
- Workflow: own the two-hour review and ninety-minute rental-end boundary.
- Event: publish a final decision only when its truth condition is met; do not call acceptance `Confirmed`.
- Agent: may prepare or submit a request only if explicit delegated authority is proven; automatic action remains withheld.
- Unknown authority: whether the partner or its AI agent may act without staff confirmation; whether payment terms may change.
- Stable business identity: `rental-extension-intent` for rental `SR-4821`, partner, customer request, and policy revision; tool-call IDs are attempts, not intent identity.
- Prohibited inference: HTTP/MCP acceptance, an accepted billing call, or a proposed event does not prove extension, charge, reroute, or customer notification.
- Final evidence: authoritative rental state, warehouse reservation check, reconciled billing result, and customer notification receipt, all bound to the intent identity.

## Live update response

The supplied update was the Stonebridge scenario's existing fact set; no additional hidden facts were introduced. The initial design is strengthened by requiring reconciliation before any customer-facing completion claim. The safe interim instruction is: “Your extension request was received and remains pending review; we will not represent it as complete until the rental and billing outcomes are verified.” The accountable owner is `UNASSIGNED`; Stonebridge must name the rental-operations authority before enabling unattended agent action.

## Monday-morning decision

Implement a bounded request-plus-status workflow with idempotent intent identity and explicit pending/unknown/final states. First test: billing commits, response times out, and the agent retries with a new tool-call ID. Block expansion if reconciliation cannot prove one business effect per intent or if any consumer treats `accepted` as final.

## Material feedback

- Prompt that changed thinking: “What does accepted permit the partner to say?”
- Unclear term: “delegated authority” needs a concrete example for non-specialists.
- Missing decision: who owns a pending extension after the rental's ninety-minute end.
- Unsupported-answer pressure: the proposed `RentalExtensionConfirmed` name invites a false green.
- Limitation: synthetic completion tests route coherence, not reader comprehension or production safety.
