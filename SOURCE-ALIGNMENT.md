# Source Alignment and Permitted Drift

**Book source:** `bmozi/architecting-apis-in-the-age-of-ai`, `companion/`
**Original standalone seed:** book commit `48a1d47`
**Current rule:** explicit operational drift is permitted; silent conceptual
drift is not

The embedded companion gives the manuscript an edition-bound teaching
snapshot. This standalone repository adds reader navigation, working terms,
validation, facilitator separation, and versioned pilot materials. Those jobs
require some different files and links.

Permitted differences are:

- standalone repository governance, routing, licensing-status, and validation
  files;
- portable links that replace a book-relative path with its exact repository
  URL;
- standalone-only reader-value, facilitator, decision-owner, and integrity
  materials; and
- a frozen packet that remains tied to the exact version used in a completed
  attempt while later source work advances.

The current intentional common-file differences are the distribution-specific
`README.md` and the `testing/README.md` route to the newer API reader-value
packet.

Meaning, authority, constraints, prohibited behavior, invariants, evidence
states, example facts, scoring criteria, and safety boundaries may not diverge
silently. Change those in both maintained copies or create a named new version
with a provenance entry and migration decision.

The collection validator in the private portfolio repository checks that no
book-source file is missing from the standalone copy, normalized common files
match unless explicitly classified, and standalone-only paths fit declared
distribution categories. Repository validation and source alignment do not
prove usability, correctness, safety, or publication readiness.
