# Stonebridge Scenario: Extend One Rental Safely

**Packet:** API-RV-PILOT-001 version 1.2.3
**Status:** Fictional, prepared, and unrun

**Revision note:** Version 1.2.3 adds replay identity, verification-command
evidence, completion chronology, and external access logging; it remains
unrun with people.

Stonebridge Equipment Rental rents generators and tools through its own service
desk and partner marketplaces. A customer wants to keep generator `SR-4821`
for one additional day. The partner asks Stonebridge for “one fast API that our
people and AI assistant can use to extend a rental.”

The proposed design is:

> Add `POST /rentals/{id}/extend`. Expose it as an MCP tool. Let the partner's
> agent call it. Return `accepted` immediately, publish
> `RentalExtensionConfirmed`, and let billing and warehouse systems react.

You are reviewing the promise before code or tool definitions are generated.

## Known facts

1. The partner authenticates with a service account and may include its staff
   user's identity. Stonebridge has not decided whether the partner's AI agent
   may act without a staff confirmation.
2. The named customer requested one extra day through the partner. The scenario
   does not say that the partner may extend every rental or change payment
   terms.
3. Some extensions can be confirmed immediately. Others require warehouse
   review because another customer has reserved the equipment.
4. A successful billing request may create a charge before the warehouse
   decision finishes. Reversing a charge is a separate effect.
5. The current billing provider can time out after committing a charge. It does
   not guarantee that a new request identifier represents the same business
   intent.
6. The partner's agent retries timeouts with a new tool-call identifier.
7. `accepted` currently means only that Stonebridge received the request. It
   does not prove the rental changed, the charge committed, or the next
   reservation remained unaffected.
8. The proposed event name says “confirmed,” but the implementation team plans
   to publish it immediately after acceptance.
9. The warehouse application will remove the generator from tomorrow's pickup
   list after receiving the proposed event. The notification service will tell
   the customer the extension is complete.
10. Manual warehouse review can take two hours. The current rental ends in
    ninety minutes.
11. Stonebridge has not chosen how the partner discovers a pending, rejected,
    unknown, or final outcome.
12. No implementation, MCP adapter, failure test, usability session, cost
    measurement, or business-result evidence exists.

## Stage A task

Without discussing the intended answer with a facilitator:

1. Explain in plain language what the partner and customer need.
2. Complete the first pass and the relevant portions of the supplied
   Agent-Ready API and MCP Capability Brief.
3. Use the decision guide to assign distinct jobs to any API, MCP tool, event,
   workflow, or agent you believe is needed. You are not rewarded for selecting
   all of them.
4. State what `accepted` permits the partner to say and what evidence would
   prove final completion.
5. Leave missing authority or evidence as unknown; do not invent it.
6. Complete the separate one-screen handoff only after the live update. Link it
   to the detailed artifacts rather than copying their contents.

## Live update

The facilitator will provide one update after the initial artifact is frozen.
Revise only after hearing it. Record the original and revised answer.

That planned revision creates the first revised artifact set. It is not a
later correction of already frozen revised bytes.

## Boundary

This exercise asks for a reviewable architecture decision. It does not ask you
to select a vendor, write code, approve production, or estimate savings.
