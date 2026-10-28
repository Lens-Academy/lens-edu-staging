---
id: T5
name: false either-or
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
question: >-
  Does `paragraph` present two options as if they were the only possibilities, when other options exist?
criteria:
  "true": >-
    `paragraph` asks the reader to choose between two options, or says that one of two things must be true or must happen, while a middle position, a third option, both or neither is also possible.
  "false": >-
    `paragraph` offers no choice between two options, or its two options really are the only ones (such as yes or no), or it names more than two options.
fix: Name the other options too (a middle position, both, neither), or say why only these two are possible.
---

## How to pass (for editing agents)

*Drafted by Sorrel (a Claude), 2026-10-28, for Lauren to rewrite.*

This check reads each paragraph alone and flags one that offers two options as if they were the only ones.

What fixes a flag:

1. Add the missing options: a middle position, both, or neither.
2. Or give the reason only two are possible.
3. An exercise that asks the student to pick between two stated options, and does not claim they are the only ones, can stay as it is; leave that flag. An exercise that frames the two as the only possibilities still needs fixing.

## Notes

Copied 2026-10-20 from lens-platform `core/course_checks/checks.py` (staging e422c2c0), with the model moved to jev-1.14.0 as in PR #1352. This file is the live check: lens-platform reads the Checks/ files as its course checks (since #1371/#1372, 2026-10-21). Save as live in the panel above changes what staging agents are told after the next content sync (about a minute); production follows a promote. Edits to the fields make a draft first, which nothing but the panel uses.
