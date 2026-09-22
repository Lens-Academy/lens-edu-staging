---
id: 'ae1b5dd2-79a7-4307-8160-582e796218cb'
title: "The lecture: three classical mysteries"
tldr: "Approximation, generalization and optimization are three different questions about why training works, and only one of them is about the training procedure."
summary_for_tutor: "Day 2 lecture page: Zach Furman's 15-slide deck for Iliad B.2 (recap of learning machines and Solomonoff induction, then approximation, generalization, optimization, representational alignment, in-context learning), followed by his second discussion question."
authors:
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/mysteries-of-deep-learning/main.mdx
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 20
tutor_minutes: 10
---

#### Text
content::
Read Zach's lecture slides (15 slides, about 20 minutes). The text of the slides is below; the original PDF is in [Zach's slides folder](https://drive.google.com/drive/folders/1SV-VYOSTzEGcRxw5GuDBCLbwQWj3k0Ym).

The slides open with a recap of a lecture Iliad students heard the day before, on learning machines and Solomonoff induction. The recap is enough to follow the rest.

#### Article
source:: [[../articles/furman-mysteries-of-deep-learning]]

#### Question: Open
id:: 779df7f1-11b7-4552-a006-25759f2cafea
content::
\## Discussion question

What distinguishes the three classical mysteries discussed in the talk from each other? Which ones depend on the training procedure?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: The lecture. They just answered this discussion question from Zach's reading guide: "Discussion question

What distinguishes the three classical mysteries discussed in the talk from each other? Which ones depend on the training procedure?" Zach has not written an answer to this question yet. Judge the answer against the readings and the lecture slides. The slides define them: approximation asks why the hypothesis class contains any low-loss hypothesis at all (why some parameter of the network gets low loss; approximating generic K-Lipschitz functions provably needs exponentially many parameters, so networks must exploit non-generic structure). Generalization asks why training selects parameters with a small gap between test and train loss (in-distribution). Optimization asks how and when SGD finds a good solution quickly instead of getting stuck, given that one exists. The slides also say Solomonoff induction answers approximation and generalization but leaves optimization unsolved. Approximation is a property of the architecture's hypothesis class alone; optimization depends on the training procedure by definition; generalization depends on which low-train-loss solution the procedure selects, so it depends on the procedure too (and on the data). In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".
