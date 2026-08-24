---
id: fa70656b-dd50-46fe-840e-581f90631773
tldr: "How do you summarize a whole book you'll never fully read? Break it into chapters, pages, paragraphs, each small enough to check. Task decomposition splits problems too big to oversee into verifiable pieces, and asks whether human thinking itself can be factored the same way so machines can imitate it."
summary_for_tutor: "Explains task decomposition as breaking complex tasks into smaller, independently solvable subtasks to make oversight and verification tractable, using book summarization as the running example. Covers recursive decomposition and the properties of a good decomposition (recursive decomposability, independence/modularity, composability), and why simpler subtasks yield easier training signals. Then introduces factored cognition, which decomposes human thinking itself into small tasks machines can imitate, highlighting delegation and meta-reasoning, and notes this underpins later methods like IDA and debate."
title: "Task Decomposition"
{++{"author":"Elias's AI","timestamp":1787570614116}@@reading_minutes: 13
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Scalable Oversight - Task Decomposition|Task Decomposition]]{++{"author":"Elias's AI","timestamp":1787570614116}@@

#### Text
optional:: true
content::
Decomposition works when a problem splits into checkable pieces, and factored cognition extends that idea to human thinking itself. Did you find the extension convincing? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Task decomposition as a way of making oversight tractable: break a task too large to supervise into smaller subtasks each small enough to check, with summarising a whole book as the running example, split into chapters, then pages, then paragraphs. It covers recursive decomposition, where subtasks are themselves decomposed, and the properties a good decomposition needs: that it can be applied recursively, that the pieces are independent enough to be solved separately, and that the results compose back into an answer to the original task. Simpler subtasks give easier training signals, which is the point. It then introduces factored cognition, which applies the same move to human thinking, decomposing reasoning into small steps a machine could imitate, and highlights delegation and meta-reasoning as the parts that make this work. The section notes this idea underpins the later methods, iterated amplification and debate.

topics to explore:
- Composability is doing a lot of work: the pieces have to add back up. Which kinds of task do you think fail that test?
- A book summary decomposes cleanly. Would a judgement, a strategy, or a diagnosis?
- Factored cognition assumes thinking is made of steps that can be separated. Does that match how you experience solving something hard?
- If a task cannot be decomposed, is it out of reach of this whole family of methods?
- Decomposition makes each piece checkable but adds many pieces. Where does the error accumulate?

Amplification and debate build on this and come later, so point at them rather than teaching them here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
