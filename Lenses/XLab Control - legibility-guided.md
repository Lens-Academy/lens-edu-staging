---
id: 'df595298-8c2c-4a28-83af-dbc5712274c5'
title: "Basic legibility protocols improve trusted monitoring (1): the setting, and three questions before the results"
tldr: "A weak monitor cannot flag code it cannot follow. So stop fixing the monitor and change the code: make the untrusted model explain every line. That also hands an attacker a channel for lying about its own backdoor, which sounds like a terrible trade. This part sets up the experiment, and three times you commit to an answer before the paper gives its own."
summary_for_tutor: "Part 1 of 2 of a guided reading of Sreevatsa, Prasanna and Rushing's arXiv paper on legibility protocols. It covers the opening of the abstract and the introduction and all of Section 2 (Setting: the APPS backdoor dataset, the models U and T, human auditing, the usefulness and safety metrics, the audit threshold, the Defer to Trusted protocol and how the control evaluation was run). The reading comes in three stretches, with three written checkpoints, one after each stretch, in the source's own order: propose legibility interventions, judge whether APPS is the right dataset, and predict whether commenting beats no commenting. The checkpoint prompts keep the source's wording. The short note on why competitive programming fits is the source's own editorial insertion, reproduced where the source puts it. The opening Text segment and every assessment brief are ours. Each brief's criteria come from the part of the paper that follows that checkpoint, some of it in part 2. The excerpt anchors deliberately skip passages that would spoil a checkpoint, exactly as the source page does: the abstract's results paragraph, the introduction's contributions list, and Figure 1. Those passages are still reachable in the article's collapsed text, so a learner may have seen them. Every checkpoint is answered before the paper gives its own answer (Q1 proposes methods, Q2 judges the dataset, Q3 predicts the result), so grade the reasoning rather than agreement with the authors, and never hand over the content of the section that follows. For the last checkpoint, grade the prediction on its reasoning; you may contrast it with the model answer in the brief, and part 2 opens with the paper's result."
reading_minutes: 13
tutor_minutes: 17
tags: []
---
#### Text
content::
\## Before you start

Part 1 of 2. This part sets up the experiment: the dataset, the models, how safety and usefulness are measured, and the protocol being tested. The next part reports what happened.

Trusted monitoring puts a weaker model you trust in charge of watching a stronger model you do not. Its core failure follows from the capability gap: the weaker monitor often cannot oversee the stronger model because it does not fully understand that model's outputs. You have met the protocol in [[../Lenses/XLab Control - monitoring-and-mitigation|Monitoring and Mitigation]], and the red-team versus blue-team game used to measure it in [[../Lenses/XLab Control - control-evaluations|Control Evaluations]].

Sreevatsa, Prasanna and Rushing change the thing being monitored instead of the monitor. A **legibility protocol** encourages the untrusted model to take actions the monitor can more easily evaluate. In this paper that mostly means one thing: letting the model comment its code, thoroughly.

The affordance is symmetric, which is what makes the paper interesting. A model inserting a backdoor also gets to write the comments explaining why its backdoor is fine. Who gains more is an empirical question, and the paper runs the full control evaluation to answer it.

You read the paper in six stretches, three in each part. Five times it stops and asks you to commit to an answer before the next stretch supplies the authors': three times in this part, twice in the next. The last prediction here is answered at the start of part 2. Write what you actually think, because the comparison is the exercise. This reading is the companion to the other guided reading on untrusted monitoring, [[../Lenses/XLab Control - collusion-guided|How to prevent collusion in untrusted monitoring]].

#### Article
source:: [[../articles/sreevatsa-basic-legibility-protocols-improve-trusted-monitoring]]
from:: ###### Abstract
to:: We introduce legibility protocols, which encourage the untrusted model to take actions that are easier for a monitor to evaluate.

#### Article
from:: ## 1 Introduction
to:: To address this, we introduce legibility protocols, which augment trusted monitoring by encouraging the untrusted model to take actions the monitor can more easily evaluate.
{>>{"author":"James agent ready-27's AI","timestamp":1790957648614}@@The abstract's second paragraph and the rest of the introduction, including the contributions list, are skipped on purpose: they state the findings that the checkpoints that follow, in this part and in part 2 ask the learner to predict. XLab's page suppresses exactly these passages. They remain visible in the article's collapsed text.<<}

#### Question: Open
id:: 4a0ac0af-818c-427a-9279-b3df33d76611
content::
\## Before you read on

Propose 2-3 ways to make U's code easier for T to understand and therefore evaluate. For each method, write about how it increases the legibility of U's logic to T.

*Minimum 120 characters.*
assessment-instructions:: Score out of 100. 50 for each of two proposed methods (the question asks for two or three): 20 for a method that plausibly makes U's code easier for T to follow, and 30 for explaining how it makes U's logic more legible to T, for example by stating the reasoning behind the code, breaking it into pieces T can check one at a time, or avoiding constructs T cannot verify. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Thorough commenting works best: line-by-line comments, docstrings and file-level comments that explain why the algorithm is correct, name the sub-algorithms it uses (for example the Miller-Rabin primality test), and justify every leap of logic, design decision and claim of optimality. This hands U's reasoning to T, which matters because most of T's false alarms come from not understanding a correct but complex solution. Without comments, small modular functions and descriptive variable and function names help moderately, since T can check the code piece by piece and read its intent from the names. Structural constraints, such as avoiding special cases and edge cases or choosing simpler, well-known algorithms over optimizations, also make the logic easier to check, but help much less and cost some performance. An attacker gets the same affordance: it can comment its backdoored code too."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Name what is present and name the single largest gap in one sentence. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold from the setup, for example asking why a monitor would call a correct but unfamiliar algorithm suspicious, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ## 2 Setting
to:: We use a smaller subset of APPS’s test split consisting of 499 problems with the most test cases.

#### Question: Open
id:: 5de450fc-77a3-431f-a713-32f743d74183
content::
\## Before you read on

The paper uses a competitive programming dataset (APPS) to perform its evaluations. Is the APPS dataset a good dataset to test if legibility helps a monitor, and why? Furthermore, try to come up with a task that would make legibility look useless, and say why legibility would not help there.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 50: whether APPS is a good test of legibility, 20 for a clear judgment and 30 for a sound reason about whether legibility has room to help there, for example that the gap between U and T is one of reasoning rather than knowledge, or that solutions are hard to find but easy to explain once found; a well-argued criticism of APPS counts too. 50: a task that would make legibility look useless, 25 for the task and 25 for why explanation could not help there, for example because it turns on knowledge (such as an obscure library function) whose claims the monitor cannot verify, or because honest solutions are already simple enough for T to check unaided. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Yes. Legibility can only help when T cannot follow U's reasoning unaided but could follow it once it is explained. Competitive programming fits: the gap between U and T is one of reasoning rather than knowledge (models we could plausibly use as trusted monitors already know programming well), and APPS solutions are hard to find but easy to explain once found. Legibility would look useless on a task that hinges on knowledge rather than reasoning, for example one that turns on an obscure library or function: a comment claiming that a rare function exists gives the monitor nothing it can verify. It would also be useless on tasks whose honest solutions T can already verify unaided, since there is no comprehension gap to close."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether each half of the question was answered, and name at most one thing they missed. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what an explanation is worth when the monitor could already have verified the code by itself. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
:::callout {tone="neutral"}
The authors want a setting where U and T differ in *reasoning power*, creating a scenario where T may not be able to follow the reasoning steps of U without explanation. Competitive programming is a field where solutions can be hard to find but easy to explain, making it a great fit for this evaluation.
:::
{>>{"author":"Elias's AI","timestamp":1789040126953}@@XLab's own note, inserted at this point in the paper. Two typos in XLab's text ("explanantion", "makingit") corrected.<<}

#### Article
from:: ### 2.2 Models and Resources
to:: [[#^appendix-c-calculating-error|C]] for the full bootstrapping process for calculating safety, audit threshold, and audit proportion.
{>>{"author":"Elias's AI","timestamp":1789045448463}@@These three anchors start at the wikilink on purpose. The article writes "Appendix" and the link with a non-breaking space between them, so an anchor spanning that gap cannot be typed reliably and silently stops matching. Starting after the gap ends the excerpt at the same word.<<}

#### Article
from:: ### 2.4 Protocol
to:: [[#^appendix-h-protocols-in|H]] (the “backdoor-aware” regime).
{>>{"author":"Elias's AI","timestamp":1789040126953}@@Figure 1 sits between these two excerpts and is skipped on purpose: its left panel is the safety/usefulness Pareto result the next checkpoint asks the learner to predict. XLab's page suppresses Figure 1 for the same reason.<<}

#### Question: Open
id:: 521c8c0b-f20a-4845-b134-458884c394dc
content::
\## Before you read on

Try to predict whether or not legibility protocols that allow commenting outperform those that don't allow commenting, and elaborate why you think this is the case. Comments are open to an attacking model as well as an honest one: say which side you expect to gain more from them, and why.

*Minimum 60 characters.*
assessment-instructions:: Score out of 100. 20: a clear prediction, in either direction. 80: the reasoning, 40 for at least one sound mechanism by which comments change how the monitor judges honest or backdoored code (for example explanations help the monitor understand correct but complex code, or let an attacker argue that its backdoor is correct), and 40 for weighing the two sides: comments are available to both the honest and the attacking policy, and the answer says which side gains more and why (for example that correct code is easier to explain than a backdoor). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Commenting should do better. Comments help both sides: an attacker can argue that its backdoor is correct. But most of the monitor's false alarms come from not understanding correct code, so explanations lower the suspicion of honest code, and honest code is easier to justify than a backdoor, so the blue team gains more."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say which mechanisms the learner reached, name the side of the ledger they neglected in one sentence. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a monitor does with a correct solution it cannot follow. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Sreevatsa, Ashwin, Sebastian Prasanna, and Cody Rushing. "Basic Legibility Protocols Improve Trusted Monitoring." *arXiv*, 9 Feb. 2026. [arxiv.org](https://arxiv.org/abs/2602.10153)
*The reading this lesson is built around: a control evaluation in the APPS backdooring setting testing whether letting the untrusted model explain its code helps the blue team more than the red team. This part covers the introduction and the experimental setting.*

XLab. "Basic legibility protocols improve trusted monitoring (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/legibility-guided)
*The source lesson this page adapts.*
:::
