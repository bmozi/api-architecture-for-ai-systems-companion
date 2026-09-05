# Try the decision before completing a form

No workplace access is needed to begin. Each numbered chapter now supplies a
short fictional case, a worked answer, and a changed assumption. Attempt the
case before reading its answer. Then transfer one decision into the relevant
blank companion form. A completed form is a proposal until its evidence exists.

## A transfer case: equipment checkout

A library lends cameras. A patron may request one camera for a weekend; the
library approves the loan only after eligibility and availability checks.
A kiosk returns `accepted`, but the camera has not been allocated. A timeout
causes the kiosk to submit another request with a fresh identifier.

Write five sentences: capability, authorized party, acceptance meaning,
completion evidence, and recovery after the timeout. Use the
[Capability and Authority Contract](api-meaning-and-authority-brief.md).

## Worked reasoning

The capability is requesting a bounded loan and learning its outcome. The
patron acts for their own library account; a kiosk credential alone does not
approve eligibility. Acceptance must name the library's responsibility and
an outcome lookup. An authoritative allocated-loan record permits collection
within the agreed time window. A lost response calls for discovery of the
original intent, not a fresh identity that could allocate another camera.

Change one assumption: the patron intentionally requests a second camera and
the policy permits two. That is a new intent. Deduplication must not silently
collapse the two legitimate requests. The quantity policy and identity rule
answer different questions.

This is a constructed transfer exercise with an editorial answer. It has not
been attempted by an independent practitioner and is not evidence of a working
library implementation. Existing frozen usability packets remain unchanged.
