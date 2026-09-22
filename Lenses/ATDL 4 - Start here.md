---
id: 'b474b46b-1fc3-499c-a4e2-86b08262ec9f'
title: "Day 4: Start here"
tldr: "Deep linear networks are the simplest networks whose training can be solved exactly. They already show the rich and lazy regimes, and learning one feature at a time."
summary_for_tutor: "Orientation for Day 4 of Alignment Theory of Deep Learning: Iliad B.4, Training Dynamics (Guillaume Corlouer). The worksheet has no author fast-track, so this page states the Lens cut: which exercises are core and which are optional."
authors:
  - Guillaume Corlouer
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/training-dynamics/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 8
tutor_minutes: 5
---

#### Text
content::
Today is **B.4, Training Dynamics**, written by Guillaume Corlouer for the Iliad Intensive. His statement of the day's intent:

> "The goal of this day is to present a toy model perspective on the training dynamics of deep neural networks. The student should learn about the AI safety motivations of studying training dynamics. One motivation is that understanding the implicit biases of training deep neural networks is a central problem behind AI alignment. This is because implicit biases influence the generalization behaviour of a neural network including for example if that neural network will generalize in a helpful or harmful way out of distribution. Another motivation is interpretability. One key lesson of the day is that SGD learns from data in a structured way. For example in deep linear neural networks, under small initialization, it will first learn the features that explain the largest fraction of data covariance."

The learning outcomes are at the top of the worksheet, on the next page.

\## Today's path

Iliad ran this worksheet as a full day. Guillaume's advice to his students: "Use LLMs to help you out when you spend longer than the suggested time (but make sure that you understand). Make sure you keep at least 30 minutes to do problem 3." Problem 3 is the rich regime, Section 4 of the worksheet.

The worksheet gives no shorter route, so the Lens version marks some exercises as core and the rest as optional. **This cut is ours, not Guillaume's.** Core: Section 2 (Exercises 2.1 and 2.3), Section 3 (Exercises 3.1, 3.2 and 3.7), all of Section 4, and in Sections 5 and 6 one exercise each (5.2 and 6.2). Everything else, including the bonus Section 7 on stochastic implicit bias, is optional. Expect about 3.5 hours for the core path, plus the group meeting.

The next page is the whole worksheet; use it as your textbook. After it come three checkpoint pages, where you type your answers and the tutor checks your working, and an optional fourth for Section 7.

\## How to answer

Work on paper or in your head, then type your key steps and final answer into the box. You can write maths in LaTeX between dollar signs (for example `$\lambda = 1/4$`) or in plain text (for example `lambda = 1/4`, `w^3`). Images of handwritten work are not supported yet. The worksheet has a collapsed official solution under each exercise; try the exercise before opening it, and use the tutor's reply to find where your reasoning and the solution part ways.

#### Question: Open
id:: 2094d8dd-bb46-474e-8331-ab3c5c5f9471
content::
\## Before you start

A deep linear network computes $f(x) = W_L \cdots W_1 x$, which is just a linear map. Any linear map it can represent, a single matrix $W$ can represent too.

Predict, in two or three sentences: if you train the deep version and the single-matrix version by gradient descent on the same data, from small random initial weights, will they learn in the same way over time? If not, what might differ? A guess is fine.
feedback-instructions:: The student is starting Day 4 of a course built from the Iliad Intensive (B.4, Training Dynamics, Guillaume Corlouer). Before reading, they predicted whether gradient descent on a deep linear network and on a single-matrix linear model learn in the same way over time. This is a predict-first question. In 2 to 4 sentences: restate their prediction in one sentence. Do not give the answer. If they predicted 'the same', say that today's worksheet asks them to test this and that the key variables are depth and the scale of initialization. If they predicted a difference, ask them to write down which difference they expect to see first (for example in the order features are learned, or in how fast), so they can check it against Section 4. No praise words. Send them to the next page.
