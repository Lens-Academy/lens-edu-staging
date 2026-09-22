---
id: 'fa1dfc80-de5b-4f38-b7f4-2998750c7d26'
title: "Day 4: Wrap-up"
tldr: "Check your prediction from the start of the day, then connect the regimes to the question of how a trained network will generalize."
summary_for_tutor: "Closing page for Day 4 (Iliad B.4, Training Dynamics). Revisit the predict-first answer and one question linking training regimes to alignment, for the group meeting."
authors:
  - Guillaume Corlouer
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/training-dynamics/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 3
tutor_minutes: 15
---

#### Question: Open
id:: 9fc0ad66-ecdf-4c27-b491-97e67ddd5f24
content::
\## Check your prediction

Scroll back to **Day 4: Start here**, copy your prediction, and paste it at the top. Then say in two to four sentences what the worksheet showed: does a deep linear network learn like a single matrix? What role do depth and initialization scale play?
feedback-instructions:: The student is finishing Day 4 of a course built from the Iliad Intensive (B.4, Training Dynamics, Guillaume Corlouer) and checking their predict-first answer: does gradient descent on a deep linear network learn like a single-matrix linear model? What the worksheet shows: with small initialization and depth, learning is rich or saddle-to-saddle, the singular modes of the teacher matrix are learned one at a time, largest singular value first, with timescales separated (larger singular values learned faster, in sudden steps), which is an implicit bias toward low rank; with large initialization the dynamics are lazy, the NTK is essentially frozen, and all modes are learned together without timescale separation, like a linear model; mixed dynamics interpolate between the two. In 80 to 150 words: say whether their prediction matched, name the one mechanism they missed if any, and correct any misuse of 'rich', 'lazy' or 'NTK' in one sentence. If they did not paste the prediction, ask them to. No praise words.

#### Question: Open
id:: 244799b4-e42f-417e-8c6b-1618658a02ac
content::
\## For the group meeting

Guillaume's intent statement says implicit biases "influence the generalization behaviour of a neural network including for example if that neural network will generalize in a helpful or harmful way out of distribution." In three to five sentences: using the rich regime's order of learning as your example, describe one way an implicit bias of training could decide which of two behaviours a network ends up with, when both fit the training data equally well. Bring this to the meeting.
feedback-instructions:: The student is finishing Day 4 (Iliad B.4, Training Dynamics) and connecting implicit bias to out-of-distribution generalization, using the rich regime (modes learned in order of singular value, low-rank bias) as the example. Day 1 of the course covered goal misgeneralization (two goals both fit training data, the learned one generalizes wrongly). In 80 to 150 words: say whether their example actually has two behaviours that fit the training data equally well; if not, point that out and ask them to name the two. If their story is sound, ask one question about what would have to be true of real networks for the toy-model mechanism to carry over (for example non-linearity, or the neural race reduction the worksheet mentions). Do not argue for a conclusion. No praise words.
