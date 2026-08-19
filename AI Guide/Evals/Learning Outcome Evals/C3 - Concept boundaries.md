{++{"author":"AI","timestamp":1787136969597}@@---
eval-id: C3
target: rubric
tags:
  - validator-ignore
---
# C3 — Concept boundaries

**Binary question:** Does each criterion define what must be conveyed *in any wording*, rather than requiring a specific phrasing, analogy, example, or memorized detail?

## Pass boundary

A criterion is a **concept boundary**: it states the idea that must be present (in the student's own words), and ideally what does and does not count as having expressed it. Analogies, terminology, named examples, and quantitative details may appear only as illustrations or acceptable routes ("…or an equivalent example") — never as hard requirements, unless recall of that specific item *is* the declared capability.

Criterion text must also be **literally true** as written, because a judge applies it literally. (Corpus case: "engineers cannot read the trained weights" — false as written; they can read the numbers but cannot interpret them. A student who says "you can read them but they're meaningless" would be wrongly failed.)

## Does NOT fail for

- "X or equivalent" formulations — naming an analogy as one acceptable route.
- Worked example answers clearly marked as examples of a passing response.
- Requiring a concrete example when the question explicitly asks for one.
- Requiring specific facts when the capability is declared as recall of those facts.

## Fail examples (from the corpus)

- *AI is grown, not crafted* — the pass level embeds "(the DNA analogy: readable but not interpretable)" inside the required explanation; human ruling: "DNA analogy doesn't seem required." Same rubric's "cannot read the resulting weights" fails the literal-truth requirement.
- *Verifying inference to catch exfiltration* — the pass level hard-requires reciting the paper's quantitative results.

## Pass examples (from the corpus)

- *Intelligence as prediction plus steering* — each check names the idea ("distinguishes forming expectations from selecting actions") without mandating any phrasing, plus explicit fail conditions ("Fail if the answer conflates prediction with preference…") and "Grade the student's reasoning, not whether they use the authors' exact wording."
++}