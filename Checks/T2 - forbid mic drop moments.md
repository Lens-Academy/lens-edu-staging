---
id: T2
enabled: true
name: "forbid mic drop moments"
model: jev-1.14.0
fail_at: 0.4
pass_below: 0.3
question: "Does `sentence` contain a mic drop moment, ie, a dramatic phrase that feels like a punchline to a buildup?"
criteria:
  "true": "`sentence` uses excessive intensity: \"the exact moment\", \"and that was when it happened\", \"and here's where it gets interesting\""
  "false": "`sentence` is reasonably sedate, or fits comfortably in its context without standing out dramatically"
fix: "Make the point plainly where it belongs. Cut the dramatic closing line, or fold what it says into the sentence before it."
view:
  sample: 400
presentation:
  context: lens
  question: sentence
  nest:
    - document
    - submodule
    - lens
    - section
    - paragraph
    - sentence
    - line
---

## How to pass (for editing agents)

*Drafted by Sorrel (a Claude), 2026-10-28, for Lauren to rewrite.*

This check asks about each sentence, with its whole lens shown, and flags a sentence written as a punchline: a short dramatic line that lands a point the paragraph has been building toward. Jev scores these low even when they are clear cases, so the line is set at 0.4.

What fixes a flag:

1. Put the point where it first comes up, in an ordinary sentence, instead of saving it for the end.
2. If the last sentence only restates the paragraph with more force ("And that changes everything."), delete it.
3. Cut staging words: "the exact moment", "and that is when", "here is where it gets interesting".
4. A strong claim is fine when the sentence gives its evidence or reason in the same breath.

A real case, from the AI Futures course: "They are Subgoal 2.B in person: the undeclared cluster the whole second half of the framework was built to find." passed after it became "They are the case Subgoal 2.B covers: an undeclared cluster, which the second half of the framework is built to find."

## Notes

Why this check exists, and examples of what it should and should not catch.
