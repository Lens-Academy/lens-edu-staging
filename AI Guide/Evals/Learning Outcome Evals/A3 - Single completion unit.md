---
eval-id: A3
target: statement
tags:
  - validator-ignore
---
# A3 — Single completion unit

**Binary question:** Is the statement a single unit of completion — one capability that stands or falls together — rather than a bundle of capabilities a learner could independently have or lack?

A learning outcome file is allowed to have multiple related learning outcomes, but only if they can roughly only be passed or failed together. Sufficiently independent learning outcomes should go in seperate learning outcome files.

## Pass boundary

The file is the unit of completion: a learner either has this outcome or doesn't. The governing human ruling: "When it's independently possible to fulfill one learning outcome but not another, they should be different learning outcome files."

The test: for each part of the statement, ask whether a learner could realistically demonstrate that part while failing another — and whether the parts could be taught, tested, and completed as separate files without losing anything. If yes for any part, this check fails. Facets that are constitutive of one understanding — a distinction plus its consequence, a claim plus the mechanism behind it, the steps of one integrated procedure where each step feeds the next — stand or fall together and pass.

Judge only the `learning-outcome:` statement. Whether the question actually tests the whole statement is a different defect; multiple questions in one file are fine as long as they test one outcome.

## Does NOT fail for

- Long or multi-clause statements whose clauses elaborate one capability (clause count is not the test — separability is).
- Enumerated instances of one skill exercised the same way (e.g. the same kind of facilitator move applied to four challenging-behaviour patterns, capped by their shared principle).
- A capability plus articulating why it works, or a definition plus applying it — the application evidences the understanding.
- Explicitly scoped selection ("for a selected agenda", "pick three of the five") — the learner completes one instance, not the union.
