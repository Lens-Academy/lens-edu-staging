---
id: '37dadef7-7400-4d86-ab1f-513a1fe1cf27'
title: "Day 3: Start here"
tldr: "Singular learning theory starts from one observation: many different parameter settings compute the same function, and that redundancy shapes how networks learn."
summary_for_tutor: "Orientation for Day 3 of Alignment Theory of Deep Learning: Iliad B.3, Singular Learning Theory (Ogden, Farrugia-Roberts, Furman). Gives the authors' fast-track route, which is today's core path, how to type maths, and one predict-first question."
authors:
  - Kai Ogden
  - Matthew Farrugia-Roberts
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/singular-learning-theory/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 13
tutor_minutes: 5
---

#### Text
content::
Today is **B.3, Singular Learning Theory (SLT)**, a tutorial written for the Iliad Intensive by Kai Ogden, Matthew Farrugia-Roberts and Zach Furman. In their words, it aims "to distil the essence of singular learning theory (the notion of degeneracy and its role in learning), laying bare through simple examples and structured exercises the core intuitions driving research in the field." They believe understanding this essence "requires no more than undergraduate-level mathematics."

By the end of today you should be able to compute degeneracy in small models, and explain what the local learning coefficient measures and why it matters for how a network learns.

Start with this five-minute recorded introduction from Iliad.

#### Video
source:: [[../video_transcripts/iliad-deep-learning-is-singular-heres-what-that-means]]

#### Text
content::

\## Today's path: the authors' fast-track

The full tutorial is far more than a day. The authors give a fast-track route for readers "already somewhat comfortable with deep learning and Bayesian inference", and it is today's core path. Skip Section 1 of the worksheet and refer back only as needed. Then:

1. **Degeneracy.** Read Subsection 2.1 and complete Exercises 2.1 and 2.2. Complete either Exercise 2.9 or 2.10. Read Subsection 2.5 and complete Exercise 2.14 and/or 2.15.
2. **The local learning coefficient.** Read Subsection 3.1 and complete Exercises 3.1, 3.2, 3.4 and 3.7. Read Subsection 3.3 and Exercise 3.10.
3. **Degeneracy and Bayesian learning.** Read all of Section 4 ("it is shorter"). Complete Exercise 4.2.

The next page is the whole worksheet; use it as your textbook. After it come three checkpoint pages, one per step above, where you type your answer to each fast-track exercise and the tutor checks your working. Expect about 3.5 hours, plus the group meeting. The authors: "Once you are done, we hope you will consider taking the scenic route some other time."

The prerequisites the authors list are linear algebra (rank, eigenvalues, positive definiteness), multivariable calculus (gradient, Hessian, second-order Taylor expansion), multivariate integrals and change of variables, and basic probability including Bayes' rule and Gaussians.

\## How to answer

Work on paper or in your head, then type your key steps and final answer into the box. You can write maths in LaTeX between dollar signs (for example `$\lambda = 1/4$`) or in plain text (for example `lambda = 1/4`, `w^3`). Images of handwritten work are not supported yet. The worksheet has a collapsed official solution under each exercise; try the exercise before opening it, and use the tutor's reply to find where your reasoning and the solution part ways.

#### Question: Open
id:: 58d17800-9bf3-4345-b498-08d7fd57a80c
content::
\## Before you start

A network has $d$ parameters. In classical statistics, the number of parameters is a standard measure of how complex a model is (for example, the BIC penalty is $\frac{d}{2}\log n$).

In two or three sentences: can you think of a reason why, for a neural network, $d$ might overstate how complex the learned model really is? A guess is fine. You will come back to this at the end of the day.
feedback-instructions:: The student is starting Day 3 of a course built from the Iliad Intensive (B.3, Singular Learning Theory). Before any reading, they guessed why a network's parameter count d might overstate the effective complexity of the learned model. This is a predict-first question. In 2 to 4 sentences: restate their guess in one sentence; if it points at redundancy (different parameters giving the same function, symmetries, directions in which the loss is flat), say that today's worksheet makes that idea precise under the name degeneracy, without explaining how; if it points elsewhere (regularization, training time, early stopping), say that is a different mechanism and that today's candidate is about the geometry of parameter space. Do not teach the local learning coefficient yet. No praise words. Send them to the next page.
