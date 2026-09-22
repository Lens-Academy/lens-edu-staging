---
id: '6b25ad0a-b06a-485c-8133-61155d74f42b'
title: "Day 2: Start here"
tldr: "Deep learning works better than the theory says it should. Today is a map of what nobody can yet explain, and of the candidate explanations."
summary_for_tutor: "Orientation for Day 2 of Alignment Theory of Deep Learning (Iliad Intensive B.2, Mysteries of Deep Learning, Zach Furman). States the day's outcomes and plan and administers Zach's first discussion question as a predict-first question."
authors:
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/mysteries-of-deep-learning/main.mdx
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 5
tutor_minutes: 10
---

#### Text
content::
Today is **B.2, Mysteries of Deep Learning**, written by Zach Furman (University of Melbourne) for the Iliad Intensive. His slides describe the goal of the day as "'awareness,' not deep knowledge": a broad but shallow overview of what the field is trying to explain, so that Days 3 to 5 can go deep on particular answers.

\## What you will be able to do by the end of today

In Zach's words:

- Students can explain and distinguish the three classical mysteries of why deep learning performs well: approximation, generalization, and optimization.
- Students understand why each of the three classical mysteries implicitly requires leveraging structure in reality: learning is not tractable for arbitrary tasks, so deep learning must be using non-generic properties of real-world tasks to succeed.
- Students are aware of the key empirical mysteries of deep learning: data-dependent generalization despite overparameterization, effectiveness of SGD on non-convex landscapes, representational alignment across architectures, and in-context learning.
- Students have encountered at least one candidate explanation for each mystery and can articulate what it does and doesn't explain.
- Students understand the "program synthesis" hypothesis as one proposed framework connecting deep learning to Solomonoff induction, and can evaluate its strengths and limitations.
- Students can articulate why solving these mysteries matters for AI safety: understanding the basic mechanisms by which deep learning works is necessary for any *systematic* (generalizing OOD) alignment interventions or measurements to even be possible.

\## How today runs

Zach's fast-track, which is today's core path: "read the lecture slides for the overall framing, then read 'Deep Learning as Program Synthesis' (skimming any sections one is already familiar with, and optionally deferring the 'path forward' section). This gives a high level overview of various empirical mysteries. Then skim as many papers on the list as you have time/interest (possibly none)."

Here that means: the slides (about 20 minutes), the program synthesis post with four discussion questions (about 90 minutes), then **at least one** of the five topic pages (approximation, generalization, optimization, representational alignment, in-context learning), about 40 minutes each. The topic pages you skip stay open to you all week. Core time is about 3 hours, plus the group meeting.

Zach assumes "basic awareness of Solomonoff induction and the high-level ideas behind it". If that name is new to you, the optional Iliad page on Solomonoff induction at the end of today's list covers it; the program synthesis post also explains what it needs.

#### Question: Open
id:: 5403f399-738e-406e-ab02-284baaacff8e
content::
\## Before you start

This is Zach's first discussion question. Answer it now from what you already think, in 100 to 200 words. You will come back to it at the end of the day.

From an AI safety perspective, why is it worth trying to scientifically figure out how deep learning works? Why would we need scientific understanding for safety if such understanding seems to have been unnecessary for capabilities?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Before you start (predict-first). They just answered this discussion question from Zach's reading guide: "Before you start

This is Zach's first discussion question. Answer it now from what you already think, in 100 to 200 words. You will come back to it at the end of the day.

From an AI safety perspective, why is it worth trying to scientifically figure out how deep learning works? Why would we need scientific understanding for safety if such understanding seems to have been unnecessary for capabilities?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "many answers are acceptable here. A few points one might mention: * It seems increasingly likely that AGI/ASI will be based on deep learning * Safety is intrinsically hard to hill-climb in the way that capabilities benchmarks are. Failures can be rare and have heavy-tail costs * Historical comparisons (steam engine safety, aviation safety, etc)" This is a predict-first question asked before any reading, so accept any reasoned position; your aim is to make their current view explicit, not to move it. In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".
