---
tags:
  - validator-ignore
---
# Writing Lenses (AI Guide)

A lens (`Lenses/<Name>.md`) is the actual learning content: a **flat file** of frontmatter + `####` segments. No H1–H3 structure, and segment headers take no title (`#### Text: Intro` is an error — the lens title lives in frontmatter).

Frontmatter: required `id`; optional `title`, `tldr` (one-sentence takeaway, ≤80 words — speaks to the learner; an analogy beats a summary), `summary_for_tutor` (AI-facing: what the lens teaches and how its parts sequence), `tags`, `min_chat_messages` (0–20, gates progression on chat participation), `add_to_ai_context` (injects source material into the tutor's context — use when the tutor must discuss a text the student read elsewhere).

Read next:

- **Segment syntax** (the 6 types — Text, Chat, Article, Video, Question, Roleplay — and their fields): `Lens Edu/AI Guide/Element Reference.md`.
- **Proven lens structures** (the five-beat reading lens, the pre-reading question lens, `assessment-instructions::` house style): `Lens Edu/AI Guide/Quality Patterns.md`. Canonical example: `Lens Edu/Lenses/IABIED - AI Is Grown, Not Crafted.md`.
