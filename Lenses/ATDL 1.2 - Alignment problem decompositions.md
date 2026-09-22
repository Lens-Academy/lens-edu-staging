---
id: '4b5cd5c2-1cfc-43cb-9e50-ca25e0134481'
title: "Session 2: Alignment problem decompositions"
tldr: "Session 2 of Day 1. Read about 20 minutes, concentrating on whichever text interests you most, then write an answer to one discussion prompt."
summary_for_tutor: "Day 1, session 2 (Alignment problem decompositions) of Alignment Theory of Deep Learning, adapted from Leon Lang's Iliad Intensive A.1 worksheet (CC BY 4.0). Student-facing text keeps Leon's session intent, readings and prompts; the in-person group discussion becomes a written answer with tutor feedback, and the group meeting picks it up."
authors:
  - Leon Lang
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/ai-alignment-intro/main.mdx
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 25
tutor_minutes: 15
---

#### Text
content::
:::callout {title="What this session is for (Leon Lang)" tone="neutral"}

The participants learn to reason about how to decompose the *technical* problem of AI alignment (in a machine learning context) into subproblems via training stories and outer/inner misalignment. They also learn about inductive biases, which govern the generalization behavior of AI systems. After this session, students know what questions to ask when reasoning about whether a procedure leads to an aligned AI.

:::

Spend about **20 minutes** reading the following texts, concentrating on the one most interesting to you.

::card[[../Lenses/evhub-how-do-we-become-confident-in-the-safety-of-a-machine-learning-system|Training stories]]

> Read everything before the section "How mechanistic does [...]"

::card[[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|Reward misspecification]]

::card[[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards|Goal misgeneralization]]

::card[[../Lenses/wilson-deep-learning-is-not-so-mysterious-or-different|On soft inductive biases]]

#### Question: Open
id:: 2f54a7c0-ce49-472e-95d1-5f5dedb38e5c
content::
\## Your answer (about 15 minutes)

Pick **one** of Leon's discussion prompts and write 150 to 300 words. Floor: take a clear position and support it with one concrete example. Stretch: also state the strongest objection to your own position, and whether it changes your answer.

- Think of well-known or imagined misalignment scenarios: Can you think of some that clearly fall into the reward misspecification or goal misgeneralization category? Are some not clearly in either of them?
- What problem with "outer" and "inner" misalignment is the terminology of "training stories" trying to solve? Construct examples where training stories seem more appropriate than inner/outer alignment as a framework.
- Think of concrete ways in which modern deep learning systems generalize beyond their explicit training examples. What inductive biases may underlie these examples? Is it always possible to come up with a "clean description" of those biases? Is the inductive bias you come up with enforced in the architecture, or more implicit? (Perhaps: discuss this explicitly for the case of "emergent misalignment".)

Start your answer by saying which prompt you chose.
feedback-instructions:: The student is on Day 1 of a one-week online course built from the Iliad Intensive (Leon Lang's A.1, AI Alignment Introduction), session 2: Alignment problem decompositions. They chose one or more of these readings and have written an answer to one discussion prompt of their choice. In the Iliad classroom these prompts were 30-minute group discussions, so there is no single right answer. The session's intent, in Leon's words: "The participants learn to reason about how to decompose the *technical* problem of AI alignment (in a machine learning context) into subproblems via training stories and outer/inner misalignment. They also learn about inductive biases, which govern the generalization behavior of AI systems. After this session, students know what questions to ask when reasoning about whether a procedure leads to an aligned AI." Leon's teaching note: "Training stories seem like a rather forgotten framework, a bit akin to the modern instantiation of a safety case. I like it since it's more general than the more often used framework of outer and inner misalignment." Key concepts the readings supply: training story = training goal plus training rationale for why the setup produces a model meeting it; outer misalignment = the reward rewards the wrong thing already on the training distribution (specification gaming); inner misalignment / goal misgeneralization = correct reward, but the learned goal generalizes wrongly out of distribution because several goals fit the training data; inductive biases decide which of those goals is learned; Wilson's soft inductive biases = flexible hypothesis space with a preference for simpler (more compressible) solutions; the inner/outer split is contested. The prompts were: Think of well-known or imagined misalignment scenarios: Can you think of some that clearly fall into the reward misspecification or goal misgeneralization category? Are some not clearly in either of them? / What problem with "outer" and "inner" misalignment is the terminology of "training stories" trying to solve? Construct examples where training stories seem more appropriate than inner/outer alignment as a framework. / Think of concrete ways in which modern deep learning systems generalize beyond their explicit training examples. What inductive biases may underlie these examples? Is it always possible to come up with a "clean description" of those biases? Is the inductive bias you come up with enforced in the architecture, or more implicit? (Perhaps: discuss this explicitly for the case of "emergent misalignment".) Your job, in one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence which prompt they answered and what their position is, in their terms; (2) name the strongest part of their reasoning by pointing at the specific move, without praise words; (3) raise one consideration from the readings or concepts above that pushes against or complicates their answer, and ask one question they could bring to their group meeting. If they misuse one of the key concepts above (for example calling a reward-misspecification case goal misgeneralization), correct it in one sentence. Grade nothing and give no score. Only use criteria from the prompts, the session intent and the readings above. Do not over-validate: no "great", "excellent", "insightful". If the answer is very short or vague, ask for one concrete example before anything else. If the student says they do not understand the prompt, do not repeat it: give one concrete foothold from the readings (an example the reading contains, or one part of the prompt isolated). If their next message still does not attempt it, rephrase the whole prompt in different words. If they ask for more discussion, continue for up to two more turns, then point them to the next session.
