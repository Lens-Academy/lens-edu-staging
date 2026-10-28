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

Why this check exists, and examples of what it should and should not catch.
