# Participant Scenario: Moving a Service Visit

## Scenario and evidence boundary

This exercise is fictional. Cedarway Home Services, HomePort, RouteSpring, and
all systems, commercial terms, time limits, and incidents below were created
for this usability test. They do not describe a real company or John Briggs's
experience.

Use only the facts provided. You may make a proposal, leave a decision open, or
state what evidence you would need. Do not assume that every named technology
or architectural mechanism is required.

## What the business requested

Cedarway Home Services sends technicians to repair household appliances.
HomePort, a marketplace partner, books some Cedarway visits for homeowners.
HomePort asks Cedarway for “one operation that moves a confirmed service visit
to a new time.” HomePort wants an answer in two seconds so its service agent
knows what to tell the homeowner.

The first implementation proposal is:

> Add `POST /visits/{visitId}/move`. Call RouteSpring, return `200` if the call
> was sent, and publish `VisitMoved` so the notification and technician systems
> can update.

You have been asked to review the promise before an implementation team or AI
generator turns that proposal into code.

## Parties and systems

- **HomePort:** Marketplace partner and proposed consumer of the operation.
  HomePort service agents speak with homeowners through HomePort's support
  channel.
- **Cedarway:** The company that sold and operates the repair service. Its
  partner team owns the external integration.
- **RouteSpring:** A dispatch vendor used to assign technicians and route some
  visits. Its request can time out after Cedarway sends a change.
- **Cedarway Visit Store:** Cedarway's record of the homeowner, appointment,
  service history, and partner booking reference.
- **Branch coordinators:** Cedarway employees who resolve exceptions when a
  technician is already assigned, a required part is in transit, or the visit
  is close to starting.
- **Notification service and technician application:** Internal consumers that
  react to visit updates.

## Known conditions

1. HomePort connects through a service account. Each request can include the
   HomePort service agent's identifier.
2. HomePort may ask about visits that originated through its marketplace. The
   current commercial agreement does not say whether HomePort may move every
   such visit without fresh homeowner confirmation.
3. Cedarway can reject some requested times immediately because the time is in
   the past, the visit has already ended, or no service is offered in that
   location.
4. Some requests need branch review because a technician is en route, a part
   has been reserved, or the new time would cross a service-region boundary.
5. Cedarway staff currently tell agents that the original appointment remains
   in place until a replacement time is confirmed. This behavior is not yet
   written into the proposed external contract.
6. RouteSpring sometimes applies a change even when Cedarway receives no reply.
   It does not currently provide Cedarway with a documented guarantee for
   repeated change requests after an ambiguous timeout.
7. HomePort's client automatically retries a timeout with a new request ID.
8. The Visit Store, RouteSpring, the technician application, and notification
   history can temporarily disagree about the scheduled time.
9. The notification service sends homeowner messages after it receives a visit
   update. The technician application may also adjust a technician's route.
10. The proposed two-second response target is a business request. It has not
    been measured or approved as a service level.
11. Cedarway has not decided whether HomePort should poll for status, receive a
    callback, or rely on a message when a decision takes longer than two
    seconds.
12. No production implementation or test evidence exists for the proposed
    operation.

## Decisions that remain open

The stakeholders have not agreed on:

- what the two-second response allows HomePort to tell the homeowner;
- whether receiving a request, approving a new time, updating RouteSpring, and
  notifying the homeowner are the same outcome or different outcomes;
- what makes two change requests “the same” business request;
- what should happen when Cedarway cannot tell whether RouteSpring applied a
  change;
- who may approve a change that affects a technician, reserved part, or region;
- which record wins when the systems disagree;
- who remains responsible while a branch coordinator is deciding;
- what HomePort should do after each kind of failure; and
- what evidence would be required before release.

## Your assignment

Work as you would in an early architecture review. First complete the opening
questions in the participant workbook without using either worksheet. Then use
the blank API Meaning-and-Authority Brief and the blank API/Event/Workflow
Decision Tree.

You may write “unknown,” “decision required,” or “release blocker.” You will
not receive extra credit for using a particular label or selecting a particular
technology. The facilitator is evaluating the clarity and safety of the tools,
including where they fail to help you.
