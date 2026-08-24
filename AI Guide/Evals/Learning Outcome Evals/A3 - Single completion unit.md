{++{"author":"Luc's AI","timestamp":1787602007855}@@---
eval-id: A3
target: statement
tags:
  - validator-ignore
---
# A3 — Single completion unit

**Binary question:** Is the statement a single unit of completion — one capability that stands or falls together — rather than a bundle of capabilities a learner could independently have or lack?

## Pass boundary

The file is the unit of completion: a learner either has this outcome or doesn't. The governing human ruling: "When it's independently possible to fulfill one learning outcome but not another, they should be different learning outcome files."

The test: for each part of the statement, ask whether a learner could realistically demonstrate that part while failing another — and whether the parts could be taught, tested, and completed as separate files without losing anything. If yes for any part, this check fails. Facets that are constitutive of one understanding — a distinction plus its consequence, a claim plus the mechanism behind it, the steps of one integrated procedure where each step feeds the next — stand or fall together and pass.

Judge only the `learning-outcome:` statement. Whether the question actually tests the whole statement is a different defect; multiple questions in one file are fine as long as they test one outcome.

## Does NOT fail for

- Long or multi-clause statements whose clauses elaborate one capability (clause count is not the test — separability is).
- Enumerated instances of one skill exercised the same way (e.g. the same kind of facilitator move applied to four challenging-behaviour patterns, capped by their shared principle).
- A capability plus articulating why it works, or a definition plus applying it — the application evidences the understanding.
- Explicitly scoped selection ("for a selected agenda", "pick three of the five") — the learner completes one instance, not the union.

## Fail examples (from the corpus)

- *Comparing alignment research agendas* — three differently-scoped outcomes stored as one file: a meta-level LO (pre-paradigmatic nature of AI safety), a cross-curricular LO (analyze theories of change), and a subject LO (arguments for and against five named agendas). Human ruling: "FAIL. Too much ground. Primary arguments for and against each agenda should be separate LO files."
- *Goals and instrumental convergence* — "Be aware of discussions on whether AI systems develop goals and understand the basic arguments for instrumental convergence." Human ruling: "seems to be two LOs at once. Could just be separate things." Whether AI develops goals and instrumental convergence are independently learnable.

## Pass examples (from the corpus)

- *Decomposing an unanswerable question* — a long chain (break into sub-questions, state settling evidence, combine into an estimate, name the dominating error) but one integrated procedure: no step is demonstrable without the previous ones.
- *Facilitator - Challenging Behaviours* — four behaviour patterns each answered with a specific move, plus the general principle behind all of them: enumerated instances of one skill, not four skills.
- *Hostile vs. indifferent AI* — distinguish hostile from indifferent plus explain why indifference suffices for the danger: the explanation is what the distinction is for; they stand or fall together.
++}