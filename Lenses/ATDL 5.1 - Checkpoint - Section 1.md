---
id: '3dfd2a93-294e-4d42-9cb1-f58c6bc6dac9'
title: "Checkpoint: Section 1"
tldr: "Counterfactual attribution misses redundant causes and chains of causes. Shapley values fix part of the first problem, at an impossible price."
summary_for_tutor: "Day 5 checkpoint for Section 1 of the Iliad B.5 worksheet (causality and counterfactuals, overdetermination, non-transitivity, Shapley values). Section 1 has no exercises, so the question is a small Lens-written computation applying Definitions 1.1 and 1.4 to the duplicate-document case from the start page."
authors:
  - Louis Jaburi
source_url: https://github.com/iliad-team/iliad-intensive/tree/d2792cbf53158db2a5729ff7d431a53869b64624/tex/data-attribution
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 30
tutor_minutes: 10
---

#### Text
content::
In the worksheet, read **Section 1** (Causality and Counterfactuals). It has no exercises; this page gives you one.

#### Question: Open
id:: 48e15fa6-f524-463f-a73b-54580f343fdd
content::
\## Two copies of one fact

Return to the case from the start page. The training set has $n$ documents; exactly two of them, $z_1$ and $z_2$, state the fact. Model the behaviour as a game $v(S) = 1$ if the training subset $S$ contains $z_1$ or $z_2$, and $v(S) = 0$ otherwise.

1. What is the leave-one-out (counterfactual) attribution of $z_1$, taking the full training set as the baseline?
2. Using Definition 1.4, what are the Shapley values of $z_1$, of $z_2$, and of any other document? (Hint: look for a symmetry, and use the fact that Shapley values sum to $v([n]) - v(\emptyset)$.)
3. Louis's Remark "Shapley still dilutes credit" says each redundant cause gets about half the credit. Is that what you found? In one sentence, is that the right answer here?

This question was written for Lens and is not part of the Iliad worksheet.
feedback-instructions:: The student is on Day 5 of a course built from the Iliad Intensive (B.5, Data Attribution, Louis Jaburi), checking Section 1 (counterfactual attribution, overdetermination, non-transitivity, Shapley values; Definition 1.1 counterfactual attribution, Definition 1.4 Shapley value, and the Remark 'Shapley still dilutes credit'). This question was written for Lens. Correct answers: (1) Leave-one-out attribution of z1 is v([n]) - v([n] minus z1) = 1 - 1 = 0, because z2 still supplies the fact; the same for z2. This is overdetermination, as in the worksheet's bakery example with butter and yeast. (2) Every other document is a null player (adding it never changes v), so its Shapley value is 0. By symmetry z1 and z2 get equal values, and the values sum to v([n]) - v(empty) = 1, so each gets 1/2. (3) Yes, this matches the Remark; whether 1/2 is 'right' is a judgement call: the Remark notes each alone is sufficient, so one could argue each deserves full credit, and Shapley's efficiency axiom forces the credits to sum to 1. Accept either view with a reason. Reply in 80 to 180 words with LaTeX between dollar signs. If all three parts are right, say so in one sentence and ask which of the two views in part 3 they hold and why. If a part is wrong, point at the first wrong step and ask a question that repairs it, without giving the number. If they are stuck on (2), give the foothold: what does adding a document other than z1 or z2 ever change? No praise words, no score.
