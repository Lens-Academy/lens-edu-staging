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

Copied 2026-10-20 from lens-platform `core/course_checks/checks.py` (staging e422c2c0), with the model moved to jev-1.14.0 as in PR #1352. Not yet read by the platform: the live check is still the Python constant.
