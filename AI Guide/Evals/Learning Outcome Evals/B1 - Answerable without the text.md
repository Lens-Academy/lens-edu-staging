{++{"author":"AI","timestamp":1787136933754}@@---
eval-id: B1
target: question
tags:
  - validator-ignore
---
# B1 — Answerable without the text

**Binary question:** Could someone who has the capability but never read the assigned text answer this question as posed?

## Pass boundary

The question must be **self-contained**: it supplies whatever context it needs, so it could be asked at a random moment — e.g. as spaced repetition two months later — and still make sense. Human ruling (*Hard calls vs. easy calls* question): "you should be able to randomly ask a question from a learning outcome at a random moment … so it should self-contain enough context."

It **fails** when a specific text is load-bearing scaffolding: references to chapters, authors, "the Coda", "as the authors define them", "the example from the chapter", or a framing that only a reader of that text can parse.

Judge each question in the file separately; the check fails if any question fails.

## Does NOT fail for

- Recall demands per se — recall can be legitimate; this check is only about text-dependence, not about memorization.
- A scenario originally from the reading, **if the question restates it fully** so no outside knowledge of the text is needed.
- Naming field-canonical frameworks or concepts (same allowance as A2).

## Fail examples (from the corpus)

- "Chapter 2 draws a sharp contrast between AI systems that are 'grown' and systems that are 'crafted.' What is that distinction?…" (*AI is grown, not crafted*) — human ruling: "A test question of a learning outcome shouldn't refer to specific reading materials."
- The *Human welfare as an instrumental variable* question — human ruling: "Shouldn't be about a specific reading."
- The *Hard calls vs. easy calls* question — statement passes A2, but the question leans on the book's context instead of self-containing it.
- "The Coda makes a careful distinction between two kinds of prediction… Use the analogy the authors give to explain it." (*Path vs. outcome prediction*)

## Pass examples (from the corpus)

- The *Trajectories with mechanisms and falsifiers* question (solar electricity cost trajectories) — deliberately set outside the course material; fully self-contained.
- The *Decomposing an unanswerable question* question (driverless-taxi estimate) — supplies its whole scenario.
++}