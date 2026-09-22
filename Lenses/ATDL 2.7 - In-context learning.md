---
id: 'ac3ae06b-aead-4ff6-91f2-568d72ed7aff'
title: "Topic: in-context learning"
tldr: "Language models learn new tasks from the prompt alone. Induction heads are one mechanism that appears at the same moment in training as that ability."
summary_for_tutor: "Day 2 optional topic page (Topic: in-context learning) from Zach Furman's Iliad B.2 reading guide: the assigned readings and his discussion questions."
authors:
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/mysteries-of-deep-learning/main.mdx
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 25
tutor_minutes: 15
---

#### Text
content::
This page is one of five topic pages for today. Do at least one; the rest are optional.

#### Text
content::
Read [*In-context Learning and Induction Heads*](https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/index.html) (Olsson et al., Anthropic, 2022). The paper is not reproduced here yet; read it at the link, then come back to answer.

#### Question: Open
id:: 4db7658a-1ab8-4a1a-8db0-012a1f50547e
content::
\## Question 1

What is an induction head, and what relationship does the paper draw between induction-head formation and in-context learning over training? Why treat the simultaneity as evidence of a mechanistic link rather than coincidence?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Topic: in-context learning. They just answered this discussion question from Zach's reading guide: "Question 1

What is an induction head, and what relationship does the paper draw between induction-head formation and in-context learning over training? Why treat the simultaneity as evidence of a mechanistic link rather than coincidence?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "An induction head is a circuit implementing the rule \[A\]\[B\] … \[A\] → \[B\] - find the previous occurrence of the current token, see what followed it, predict that again ('complete the pattern' by copying). Mechanically it's two heads composed across layers (a previous-token head feeding the induction head), so it cannot exist in a 1-layer model. In-context learning is operationalized as the drop in loss from early to late token positions (the model predicting better the more context it has seen). Early in training there is a phase change, visible as a bump in the training loss, during which induction heads form and the bulk of in-context-learning ability appears simultaneously - for models of every size with more than one layer. Simultaneity alone would only be suggestive; the case is carried by co-perturbation (when they modify the architecture to move when induction heads can form, the in-context-learning jump moves to match) and by direct ablation (knocking out induction heads in small models sharply reduces in-context learning)" In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

