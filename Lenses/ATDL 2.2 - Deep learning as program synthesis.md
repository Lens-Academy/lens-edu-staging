---
id: 'cd67daea-7087-4bc4-85ad-0c2f889b0eb5'
title: "Deep learning as program synthesis"
tldr: "An opinionated hypothesis, that deep learning does something like Solomonoff induction by searching for programs, alongside a consensus tour of what deep learning theory cannot yet explain."
summary_for_tutor: "Day 2 core reading: Zach Furman's post 'Deep learning as program synthesis' (LessWrong), with four of his discussion questions. Zach notes the post is shared mainly for its survey of empirical mysteries; the hypothesis itself is opinionated."
authors:
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/mysteries-of-deep-learning/main.mdx
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 60
tutor_minutes: 25
---

#### Text
content::
Zach's note on this reading: "this post presents an opinionated hypothesis (deep learning is performing something analogous to Solomonoff induction) alongside relatively consensus discussion of empirical mysteries. The post is largely being shared for the latter, though students may find the hypothesis itself useful pedagogically."

Skim any section you already know. You may defer "The path forward", but the third question below asks about its "search problem" part.

#### Article
source:: [[../articles/furman-deep-learning-as-program-synthesis]]

#### Question: Open
id:: 334b4529-a27e-4f9d-a09a-c84aedeb0a04
content::
\## Question 1

Intuitively, what is Solomonoff induction and why do we care about it?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Deep learning as program synthesis. They just answered this discussion question from Zach's reading guide: "Question 1

Intuitively, what is Solomonoff induction and why do we care about it?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "people should mention the universality hypothesis class, the simplicity prior, optimality results." In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

#### Question: Open
id:: 37feaf45-9c97-4e9d-812f-d75e2e81776c
content::
\## Question 2

One can trivially say that a neural network "learns programs" because a neural network runs on a computer. Then one could say that e.g. linear regression "learns programs" too. What distinguishes the author's hypothesis from this more trivial fact?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Deep learning as program synthesis. They just answered this discussion question from Zach's reading guide: "Question 2

One can trivially say that a neural network "learns programs" because a neural network runs on a computer. Then one could say that e.g. linear regression "learns programs" too. What distinguishes the author's hypothesis from this more trivial fact?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "this is answered in the post under the 'Clarifying the hypothesis' expandable section. See in particular the FPGA analogy and the point about general-purpose search. It is also discussed further in the 'representation problem' section where a possible mechanism is sketched" In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

#### Question: Open
id:: f860506a-e282-47e4-95b1-855465101a1a
content::
\## Question 3

Where in the post do the three theoretical mysteries from the opening lecture (approximation, generalization, optimization) appear? Why does the post put the section related to "optimization" in a separate place from the other two mysteries?
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Deep learning as program synthesis. They just answered this discussion question from Zach's reading guide: "Question 3

Where in the post do the three theoretical mysteries from the opening lecture (approximation, generalization, optimization) appear? Why does the post put the section related to "optimization" in a separate place from the other two mysteries?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "they map to the 'paradox of approximation' section, the 'paradox of generalization' section, and the 'search problem' section. Optimization shows up in the 'search problem' section within 'path forward' because it's the only one of the three mysteries which Solomonoff induction can't explain." In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".

#### Question: Open
id:: 36ea0455-cb48-497d-866d-37df56aabf11
content::
\## Question 4 (stretch)

The post insists on maintaining the distinction between "functions" and "programs". Why? Why would we care to distinguish two networks that implement the same function by different means?
optional:: true
feedback-instructions:: The student is on Day 2 of a one-week online course built from the Iliad Intensive: B.2, Mysteries of Deep Learning, by Zach Furman. Section: Deep learning as program synthesis. They just answered this discussion question from Zach's reading guide: "Question 4 (stretch)

The post insists on maintaining the distinction between "functions" and "programs". Why? Why would we care to distinguish two networks that implement the same function by different means?" Zach's own notes on the answer, written for teaching assistants and not published to students (so never paste or paraphrase them as a model answer; use them only to diagnose): "they may *train* differently; the gradients can be different even if the function implemented is the same. For instance, suppose network A is an LLM that has never learned about bioweapons, and network B is an LLM who learned about bioweapons but was trained to suppress this knowledge in the last layer. They may behave the same right now, but under fine-tuning one can easily recover dangerous capabilities in B but not A. * One may be tempted to say that we should care because even if networks implement the same function in-distribution, they may behave differently out-of-distribution. But, while true and important, this is actually denying the premise of the question, because behaving differently out-of-distribution means the two functions really *are* different. The strong claim here is that you should care about implementation *even if no possible input/output test could distinguish between the two networks*." In one reply of 100 to 180 words, short paragraphs, no lists: (1) say in one sentence what their answer claims; (2) if it contains the central point of the notes, say which part carries it, plainly and without praise words; (3) if it misses or contradicts that point, do not state the point: ask one question that would lead them to it, pointing at the specific section of the reading where it is; (4) if something they wrote is false, correct it in one sentence. There is no score. Only use criteria from the question, the readings and the notes above. If the student says they do not understand, do not repeat the question: give one concrete foothold from the reading (an example it contains, or one part of the question isolated). If their next message still does not attempt it, rephrase the question in different words. Allow up to two follow-up turns, then send them on. No "great", "excellent", "insightful".
