---
id: 'c9d57726-0881-4b9a-bb8a-8e9c4b8cee10'
title: "Topic: generalization"
tldr: "The same network fits real labels and random labels equally well, so whatever explains generalization cannot be a property of the network alone."
summary_for_tutor: "Day 2 optional topic page (Topic: generalization) from Zach Furman's Iliad B.2 reading guide: the assigned readings and his discussion questions."
authors:
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/mysteries-of-deep-learning/main.mdx
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 40
tutor_minutes: 15
---

#### Text
content::
This page is one of five topic pages for today. Do at least one; the rest are optional.

#### Article
source:: [[../articles/lawrencec-the-paper-that-killed-deep-learning-theory]]

#### Article
source:: [[../articles/wilson-deep-learning-is-not-so-mysterious-or-different]]

#### Question: Open
id:: 491028a9-baaa-45ac-986c-28b6f5e3fc4c
content::
\## Question 1

There are different notions of "generalization" that aren't equivalent. What precisely do these resources mean by the word "generalization"? How does it differ from out-of-distribution (OOD) generalization?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Topic: generalization. They just answered this discussion question from Zach's reading guide: "Question 1

There are different notions of "generalization" that aren't equivalent. What precisely do these resources mean by the word "generalization"? How does it differ from out-of-distribution (OOD) generalization?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "The resources here deliberately refer to *in-distribution generalization*, that is the gap between test loss and train loss where the train loss is sampled from the same distribution the test loss is evaluated over. This excludes OOD generalization, which would require evaluating the test loss against a different input/label distribution than the training samples are sampled from. Historically, the word 'generalization' within statistical learning theory has typically referred to in-distribution generalization, but in common ML usage the word increasingly refers to OOD generalization. It is therefore *very common* for students to conflate in-distribution and OOD generalization, but they are totally different notions within a statistical learning theory context, and OOD generalization is almost impossible to prove useful results about in generality (the test distribution can change to anything!) despite sounding more appealing. There is still no consensus explanation for in-distribution generalization, and OOD generalization is strictly harder to explain. * 'The framework imagined a data distribution $D$ over inputs $X$ and outputs $Y$ where the goal was to fit a hypothesis $h : X \to Y$ that minimized the expected test loss for a loss function $L : X \times Y \to R$ over $D$. A learning algorithm would receive $n$ samples from the data distribution, and would minimize the training loss averaged across the sample $L(h(x), y)$.'" In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

#### Question: Open
id:: bb4217c6-d494-47ab-91e2-cf29d0c250e0
content::
\## Question 2

Why are the experimental results of Zhang et al. fatal to capacity-based generalization bounds (VC dimension, Rademacher complexity, etc)? What does this imply for explanations about generalization and what they must depend on?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Topic: generalization. They just answered this discussion question from Zach's reading guide: "Question 2

Why are the experimental results of Zhang et al. fatal to capacity-based generalization bounds (VC dimension, Rademacher complexity, etc)? What does this imply for explanations about generalization and what they must depend on?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "the architecture and algorithm are *fixed* across the two runs, so any complexity measure that depends only on the hypothesis class and the (data-independent) algorithm must give the same number in both - yet one generalizes and one doesn't. Therefore generalization is not a property of the model; it's an emergent property of model × algorithm × *data structure*." In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

#### Question: Open
id:: d5bb34ec-762a-4bd6-b14b-1dbc5555d99f
content::
\## Stretch question

The first post is rather pessimistic in tone, declaring deep learning theory (or at least the theory surrounding generalization) to have been "killed." Meanwhile "Deep Learning is Not So Mysterious or Different" seems to take precisely the opposite attitude, that such empirical results are not too surprising under preexisting theoretical frameworks. Despite the difference in tone, how compatible are these results on the object level? What common picture do they paint?
optional:: true
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Topic: generalization. They just answered this discussion question from Zach's reading guide: "Stretch question

The first post is rather pessimistic in tone, declaring deep learning theory (or at least the theory surrounding generalization) to have been "killed." Meanwhile "Deep Learning is Not So Mysterious or Different" seems to take precisely the opposite attitude, that such empirical results are not too surprising under preexisting theoretical frameworks. Despite the difference in tone, how compatible are these results on the object level? What common picture do they paint?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "They're fully compatible - Zhang et al. is a negative result and Wilson is a positive proposal in the space it leaves open. Both say generalization is not a uniform property of the model class: capacity measures like VC dimension or Rademacher complexity can't explain it, since the same network generalizes on real data and memorizes random labels. Zhang stops there (an experimental result ruling out capacity-based explanations); Wilson supplies a candidate replacement - soft inductive biases, a flexible hypothesis space with a data-dependent preference for simpler solutions - which is exactly the kind of non-uniform, data-dependent explanation Zhang leaves room for. The 'killed vs not mysterious' clash is one of tone, not content." In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

