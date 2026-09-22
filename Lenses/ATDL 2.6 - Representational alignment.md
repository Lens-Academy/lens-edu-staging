---
id: 'f72ba2c7-d5c7-4117-8d70-a55d227107cc'
title: "Topic: representational alignment"
tldr: "Different networks trained on different data often end up with similar internal representations. One paper argues they are converging on a model of reality itself."
summary_for_tutor: "Day 2 optional topic page (Topic: representational alignment) from Zach Furman's Iliad B.2 reading guide: the assigned readings and his discussion questions."
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
Read [*The Platonic Representation Hypothesis*](https://arxiv.org/abs/2405.07987) (Huh, Cheung, Wang and Isola, 2024). The paper is not reproduced here yet; read it at the link, then come back to answer.

#### Question: Open
id:: 38154f68-acce-427f-a51c-19235fe39daa
content::
\## Question 1

What is the new hypothesis that paper promotes, versus what are the observations already established by prior literature? What evidence do they cite for their hypothesis? What distinguishes their hypothesis from merely "models converge to shared representations"?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Topic: representational alignment. They just answered this discussion question from Zach's reading guide: "Question 1

What is the new hypothesis that paper promotes, versus what are the observations already established by prior literature? What evidence do they cite for their hypothesis? What distinguishes their hypothesis from merely "models converge to shared representations"?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "The *observation* that independently trained models learn similar representations is old and well-established - it predates the paper by years (model stitching, CKA/RSA similarity, 'convergent learning,' universal Gabor filters, vision models predicting visual cortex). What's *new* is not that models resemble each other but a claim about where they're heading: representations are converging toward a single endpoint, and that endpoint is a representation of the underlying reality - the statistical structure of the world that generated the data (their 'platonic' representation, idealized as a kernel reflecting how real-world events co-occur). The evidence they cite for *this* is (i) convergence that grows with model scale and competence, (ii) convergence that holds *across modalities* - vision and language models becoming more alignable as they get more capable - and (iii) a theoretical argument that multitask pressure, capacity, and simplicity bias funnel diverse models toward the same solution. The distinction from 'models converge to shared representations' is the addition of a *limit point* and its *identity*: plain convergence is just pairwise similarity, and is equally consistent with models merely sharing architectures, objectives, or training data; PRH claims they share a *destination*, and that the destination is reality's structure - which is what licenses its signature prediction that convergence should cross modalities. That cross-modal and scaling evidence is exactly the novel, load-bearing, and most-contested part; the bare convergence phenomenon is the consensus part. * Note that papers like '[Revisiting the PRH: An Aristotelian View](https://arxiv.org/abs/2602.14486)' have criticized some of the evidence in the PRH paper and propose a slightly weaker hypothesis. However their critiques only apply to evidence based on CKA, a particular technique, and other evidence appears to survive" In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

