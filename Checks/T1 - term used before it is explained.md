---
id: T1
name: term used before it is explained
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
# Question files are read inside a lens, after the lens text that explains their terms.
skip_folders: [ Questions ]
question: >-
  Does `paragraph` use a technical term or acronym without explaining what it means?
criteria:
  "true": >-
    `paragraph` uses a specialist term or an acronym, for example METR, OOMs, RLHF or gradient descent, and the sentence where it first appears does not say what it means.
  "false": >-
    Every specialist term and acronym in `paragraph` is explained in the sentence where it first appears, or `paragraph` uses only everyday words and names, such as AI, ChatGPT, OpenAI or computer.
fix: Say what the term means, in plain words, in the sentence where it first appears.
view:
  sample: 100
presentation:
  context: document
  question: paragraph
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

This check reads each paragraph with the whole document shown, and flags a technical term or acronym that is used without being explained. A term explained earlier in the same document passes. A term explained only later on the page, or only on another page, does not: a student reads top to bottom, and may arrive at this page first.

What fixes a flag:

1. Add a short plain-words explanation in the sentence where the term first appears on this page, as an appositive or a clause: "the METR horizon trend, the length of task (in human working time) that AI agents can finish".
2. If the term is not needed, use the plain description instead of the term.
3. A link alone does not pass; the explanation has to be in the text.

A flag on a paragraph you did not change can mean the explanation it relied on was removed or moved below it.

## Notes

Copied 2026-10-20 from lens-platform `core/course_checks/checks.py` (staging e422c2c0), with the model moved to jev-1.14.0 as in PR #1352. This file is the live check: lens-platform reads the Checks/ files as its course checks (since #1371/#1372, 2026-10-21). Save as live in the panel above changes what staging agents are told after the next content sync (about a minute); production follows a promote. Edits to the fields make a draft first, which nothing but the panel uses.
