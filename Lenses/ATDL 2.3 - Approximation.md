---
id: '79950229-bb4f-4a33-a177-c0d0d70516f9'
title: "Topic: approximation"
tldr: "Universal approximation says a wide enough network can represent anything, which is exactly why it explains nothing about deep learning's success."
summary_for_tutor: "Day 2 optional topic page (Topic: approximation) from Zach Furman's Iliad B.2 reading guide: the assigned readings and his discussion questions."
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

Zach assigns two readings. The first is below. The second is a review paper, [Poggio et al., *Why and When Can Deep, but Not Shallow, Networks Avoid the Curse of Dimensionality: a Review* (arXiv 1611.00740)](https://arxiv.org/pdf/1611.00740); read its introduction and the statement of its main depth-separation theorem on arXiv, and skim the rest.

#### Article
source:: [[../articles/hoogland-approximation-is-expensive-but-the-lunch-is-cheap]]

#### Question: Open
id:: 40f84e47-b4b6-4540-af95-260788f93eca
content::
\## Question 1

The Universal Approximation Theorem says a one-hidden-layer network can approximate any continuous function to arbitrary accuracy. Why is this *not* an explanation for deep learning's success?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Topic: approximation. They just answered this discussion question from Zach's reading guide: "Question 1

The Universal Approximation Theorem says a one-hidden-layer network can approximate any continuous function to arbitrary accuracy. Why is this *not* an explanation for deep learning's success?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "because the number of neurons required is exponential, for generic smooth functions. The UAT is essentially a proof that *with exponential resources you can build a continuous lookup table.* This would require more parameters than are atoms in the universe just to e.g. approximate MNIST" In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

#### Question: Open
id:: e4196f6f-7481-4d45-8050-cb3be45e2436
content::
\## Question 2

If approximating *arbitrary* smooth functions provably requires exponentially many parameters (the curse of dimensionality), then what must be true about the functions deep learning actually faces for it to work at all? What is a "depth separation" result and what does it suggest about the answer to this question?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Topic: approximation. They just answered this discussion question from Zach's reading guide: "Question 2

If approximating *arbitrary* smooth functions provably requires exponentially many parameters (the curse of dimensionality), then what must be true about the functions deep learning actually faces for it to work at all? What is a "depth separation" result and what does it suggest about the answer to this question?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "real target functions *provably* must have some non-generic structure beyond that of generic Lipschitz functions, if realistic-size deep neural networks are to be capable of representing them at all. Depth separation results are theoretical results showing that there exist target functions that require exponentially many more parameters for a shallow network to approximate compared to a deep network. They hint that the non-generic target structure neural networks are exploiting may be *compositional* structure, as deep but not shallow networks can exploit this structure. Bonus points for relating this to program structure discussed in the 'program synthesis' post" In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

