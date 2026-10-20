---
id: T1
name: term used before it is explained
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
question: >-
  Does `paragraph` use a technical term or acronym without explaining what it means?
criteria:
  "true": >-
    `paragraph` uses a specialist term or an acronym, for example METR, OOMs, RLHF or gradient descent, and the sentence where it first appears does not say what it means.
  "false": >-
    Every specialist term and acronym in `paragraph` is explained in the sentence where it first appears, or `paragraph` uses only everyday words and names, such as AI, ChatGPT, OpenAI or computer.
fix: Say what the term means, in plain words, in the sentence where it first appears.
---

Copied 2026-10-20 from lens-platform `core/course_checks/checks.py` (staging e422c2c0), with the model moved to jev-1.14.0 as in PR #1352. Not yet read by the platform: the live check is still the Python constant. {>>{"author":"lauren","timestamp":1792504111887}@@test of criticmarkup<<}Edit freely to try phrasings; the panel above runs whatever this file says now.
