---
id: 'ece6213c-27f1-4577-a569-e7f14f767041'
title: "Day 5: Start here"
tldr: "Which training examples caused a model to behave the way it does? Today treats that as a causal question and works through three families of answers."
summary_for_tutor: "Orientation for Day 5 of Alignment Theory of Deep Learning: Iliad B.5, Data (Attribution) for Alignment (Louis Jaburi, EleutherAI). Gives the author's three self-contained fast-track routes; the student reads Section 1 and chooses at least one route."
authors:
  - Louis Jaburi
source_url: https://github.com/iliad-team/iliad-intensive/tree/d2792cbf53158db2a5729ff7d431a53869b64624/tex/data-attribution
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 8
tutor_minutes: 5
---

#### Text
content::
Today is **B.5, Data (Attribution) for Alignment**, written by Louis Jaburi (EleutherAI) for the Iliad Intensive. It opens with the question the whole day is about: "**Which training examples caused a model to behave the way it does?** If mechanistic interpretability aims for the causal analysis of a forward pass, data attribution aims for the causal analysis of a training run."

By the end of today you should be able to derive influence functions, state when their approximations fail, and compare them with Bayesian and unrolling methods.

\## Today's path: pick a route

Louis's note: "There is more material here than comfortably fits into a single day. Readers short on time may prefer one of the following routes; each is self-contained." His three routes:

1. *From classical to modern influence functions.* Skim Section 1 for motivation, then read Section 2 in full, including the derivation exercise.
2. *The Bayesian perspective.* Read Subsection 2.1 for the influence function formula, then Section 3 in full. The connection exercise (Subsection 3.2) is the conceptual payoff.
3. *Training-dynamics attribution.* Skim Section 2, then read Section 4 in full. The long exercise in Subsection 4.3 recovers the influence function as a limit of unrolling.

"All three routes depend on the motivational material in Section 1. If reading only one section, read that one."

So: everyone reads **Section 1** and answers one question about it. Then choose **at least one route**; each has its own checkpoint page, and the other two stay open to you. Route 2 connects to Day 3 (singular learning theory) and Route 3 to Day 4 (training dynamics), if you want to pick by what you enjoyed. Expect about 3.5 hours, plus the group meeting.

This worksheet was converted for Lens from the Iliad LaTeX source, so its layout differs slightly from the Iliad website. Sections 5 and 6 of the source are not included because both are marked "Under construction".

\## How to answer

Work on paper or in your head, then type your key steps and final answer into the box. You can write maths in LaTeX between dollar signs (for example `$\lambda = 1/4$`) or in plain text (for example `lambda = 1/4`, `w^3`). Images of handwritten work are not supported yet. The worksheet has a collapsed official solution under each exercise; try the exercise before opening it, and use the tutor's reply to find where your reasoning and the solution part ways.

#### Question: Open
id:: b91b6936-bc33-4a04-8502-e518f2b38b8e
content::
\## Before you start

Suppose a language model can answer a question about an obscure fact, and exactly two documents in its training set state that fact. Predict: if you retrained the model with one of those two documents removed, how much would its ability to answer change? What does your answer suggest about using "remove it and retrain" to decide which document caused the ability?
feedback-instructions:: The student is starting Day 5 of a course built from the Iliad Intensive (B.5, Data Attribution, Louis Jaburi). Before reading, they predicted what happens when one of two documents stating the same fact is removed, and what that means for leave-one-out attribution. This is a predict-first question. In 2 to 4 sentences: restate their prediction. If they predict little or no change, say that Section 1 of the worksheet gives this pattern a name (overdetermination) and a worked example, without explaining further. If they predict a large change, ask them what would have to be true of training for one copy to be insufficient. Do not teach Shapley values yet. No praise words. Send them to the worksheet.
