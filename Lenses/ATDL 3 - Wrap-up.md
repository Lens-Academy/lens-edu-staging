---
id: '081b3eec-7c4b-4419-8270-9639b2acfe43'
title: "Day 3: Wrap-up"
tldr: "Use today's tools on a case the worksheet did not do, then go back to your guess from the start of the day."
summary_for_tutor: "Closing page for Day 3 (Iliad B.3, SLT). One transfer question computing an LLC and Hessian rank for a case not in the worksheet, then a revisit of the predict-first answer."
authors:
  - Kai Ogden
  - Matthew Farrugia-Roberts
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/singular-learning-theory/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 5
tutor_minutes: 15
---

#### Question: Open
id:: b9e324d2-6749-4ec9-be39-bfce1e5e2a14
content::
\## A case the worksheet did not do

Consider the loss $L(x, y, z) = x^{2} + y^{4} + z^{6}$ near its minimum at the origin. What is the rank of the Hessian at the origin, and what is the local learning coefficient $\lambda$? Compare $\lambda$ with $d/2$, the value it would take if the minimum were non-degenerate. Show the step that gets you $\lambda$.
feedback-instructions:: The student is finishing Day 3 of a course built from the Iliad Intensive (B.3, Singular Learning Theory). This transfer question is not in the worksheet. Correct answer: the Hessian at the origin is diag(2, 0, 0), rank 1. For a sum of monomials in separate variables, the volume of the sublevel set {L < epsilon} scales like epsilon^(1/2) times epsilon^(1/4) times epsilon^(1/6) (each coordinate independently up to constants, as in the worksheet's Exercise 3.4(c) and (d)), so lambda = 1/2 + 1/4 + 1/6 = 11/12, below d/2 = 3/2. The Hessian rank alone would suggest an effective dimension of 1 (lambda 1/2), which undercounts, and d/2 = 3/2 overcounts; the LLC sits between. Reply in 80 to 150 words with LaTeX between dollar signs. If correct, say so in one sentence and ask them what the gap between 11/12 and 3/2 means for the Bayesian free energy of this minimum compared with a regular one (answer: a smaller log n penalty, so it is favoured). If wrong, point at the first wrong step and ask a question that repairs it, referring them to Exercise 3.4. If they are stuck, give the foothold: compute the volume of {x^2 < epsilon} alone first. No praise words, no score.

#### Question: Open
id:: 069cd2e1-3971-4fff-b87d-a816a4cf2701
content::
\## Back to your first guess

Scroll back to **Day 3: Start here**, copy your guess about why parameter count might overstate a network's complexity, and paste it at the top. Then in two or three sentences, say what you would now write instead, using the terms degeneracy and local learning coefficient. Bring one question you still have to the group meeting.
feedback-instructions:: The student is finishing Day 3 (Iliad B.3, Singular Learning Theory) and revisiting their predict-first guess about why a network's parameter count d overstates effective complexity. Today's key ideas: degeneracy of the parameter-function map (directions in parameter space that do not change the function) and of the loss landscape; the local learning coefficient lambda as the volume-scaling exponent of near-optimal parameters, equal to d/2 at a non-degenerate minimum and smaller at degenerate ones; Watanabe's free energy formula F_n approximately n L_n(w*) + lambda log n, so degenerate minima pay a smaller complexity penalty; phase transitions when local free energies cross as n grows. In 60 to 120 words: check each use of 'degeneracy' and 'local learning coefficient' is correct, correcting a misuse in one sentence; name what changed between their two answers. If they did not paste the first guess, ask them to. No praise words.
