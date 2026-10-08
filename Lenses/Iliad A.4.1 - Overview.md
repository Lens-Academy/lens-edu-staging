---
id: '3a5b3e94-ae1e-4409-89eb-9b10233789cd'
title: "A.4.1 Overview"
tldr: "Prerequisites, learning goals and the reading list for the reward learning theory session: slides, the exercise sheet and Joar Skalse's lecture and agenda post."
summary_for_tutor: "This is the overview of Iliad worksheet A.4 Reward Learning Theory. It lists prerequisites (RL, RLHF, AI alignment basics), the learning goals (place of reward learning in alignment, conditions under which RLHF via trajectory comparisons yields an aligned objective, underspecification and misspecification, assistance games), a fast-track and the main content. The exercise sheet is based on Lang et al. 2024 (partial observability in RLHF) and Benefits of Assistance over Reward Learning. The facilitator roadmap is hidden from learners."
authors:
  - Leon Lang (Iliad)
  - Joar Skalse (Deducto Limited, King’s College London)
source_url: https://iliad-intensive.org/alignment/reward-learning-theory/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Prerequisites

It is useful to know the basics of reinforcement learning, reinforcement learning from human feedback (RLHF), and AI alignment, as taught in other modules of this course.

:::callout {title="What you'll learn" tone="neutral"}

- learn the place of reward learning in the AI alignment landscape;
- can reason about the (speculative) assumptions that motivate this research area as a whole;
- understand the strong conditions under which the simplest reward learning technique, RLHF via trajectory comparisons, would lead to an aligned objective;
- can reason about situations where such conditions do not hold, like underspecification and misspecification, and efforts to account for, or correct, such issues;
- and understand how reward learning can be embedded into the framework of assistance games, which can be regarded as one conceptualization of the entire alignment problem.

:::

%% Facilitator logistics (hidden from learners):
\## Roadmap for the day (as taught in the April 2026 Iliad Intensive)

- 10:00 – 11:30 Lecture and questions
- 11:30 – 12:30: Exercise block 1
- 12:30 – 13:30: Lunch break
- 13:30 – 14:30: Exercise block 2
- 14:30 – 15:30: Guest lecture by Richard Ngo
- 15:30 – 16:00: Break
- 16:00 – 17:30: Guest lecture by Joar Skalse
- 17:30 – 18:30: Discussions, feedback, and wrap-up
%%

\## Content

\### Fast-track

Simply read the lecture slides of the first lecture. If you have more time, do the first exercise on partial observability as one instantiation of misspecification.

\### Main content

- [Lecture slides: Intro to Reward Learning Theory by Leon Lang](https://docs.google.com/presentation/d/1cG2M68gj8osmrse97bza9cgCqqwoFXBvDIGpkv-HVgA/edit?usp=drive_link)
- Reward Learning Theory: Exercises (also available without solutions). The exercise sheet is based on the following two papers:
  - [When Your AIs Deceive You: Challenges of Partial Observability in Reinforcement Learning from Human Feedback](https://arxiv.org/abs/2402.17747)
  - [Benefits of Assistance over Reward Learning](https://people.eecs.berkeley.edu/~russell/papers/neurips20ws-assistance)
- [Lecture slides: Towards a Formal Theory of Reward Learning, With Application to Inverse Reinforcement Learning](https://drive.google.com/file/d/1WLC-HILvYGmXo9kqUGEvekK6scURXQBl/view?usp=sharing) by Joar Skalse. More context:
  - [The Theoretical Reward Learning Research Agenda: Introduction and Motivation](https://www.lesswrong.com/s/TEybbkyHpMEB2HTv3/p/pJ3mDD7LfEwp3s5vG) by Joar Skalse
