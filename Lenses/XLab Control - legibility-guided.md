---
id: 'df595298-8c2c-4a28-83af-dbc5712274c5'
title: "Basic legibility protocols improve trusted monitoring"
tldr: "A weak monitor cannot flag code it cannot follow. So stop fixing the monitor and change the code: make the untrusted model explain every line. That also hands an attacker a channel for lying about its own backdoor, which sounds like a terrible trade. Five times in this paper you predict the result before the authors report it."
summary_for_tutor: "Module 4, the last lesson of the module and one of its two guided readings. Sreevatsa, Prasanna and Rushing's arXiv paper on legibility protocols is split into six reading stretches, and five written checkpoints sit between them in the source's own order: propose legibility interventions, judge whether APPS is the right dataset, predict whether commenting beats no commenting, predict how the value of commenting moves as the monitor gets stronger, and state the overall update three ways. The checkpoint prompts keep the source's wording. Four short commentary blocks (the note on why competitive programming fits, 'A tempting objection that doesn't bite', 'A hump, and the honesty of only measuring half of it', and 'The transferable idea') are the source's own editorial insertions, reproduced in the positions the source puts them. The opening Text segment and every assessment brief are ours; each brief's criteria come from the part of the paper that follows that checkpoint. The excerpt anchors deliberately skip three passages that would spoil a checkpoint, exactly as the source page does: the abstract's results paragraph, the introduction's contributions list, and Figure 1. Those passages are still reachable in the article's collapsed text, so a learner may have seen them. Every checkpoint is a prediction written before the result has been read, so grade the reasoning rather than agreement with the authors, and never hand over the content of the section that follows."
reading_minutes: 90
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you start

Trusted monitoring puts a weaker model you trust in charge of watching a stronger model you do not. Its core failure follows from the capability gap: the weaker monitor often cannot oversee the stronger model because it does not fully understand that model's outputs. You have met the protocol in [[../Lenses/XLab Control - monitoring-and-mitigation|Monitoring and Mitigation]], and the red-team versus blue-team game used to measure it in [[../Lenses/XLab Control - control-evaluations|Control Evaluations]].

Sreevatsa, Prasanna and Rushing change the thing being monitored instead of the monitor. A **legibility protocol** encourages the untrusted model to take actions the monitor can more easily evaluate. In this paper that mostly means one thing: letting the model comment its code, thoroughly.

The affordance is symmetric, which is what makes the paper interesting. A model inserting a backdoor also gets to write the comments explaining why its backdoor is fine. Who gains more is an empirical question, and the paper runs the full control evaluation to answer it.

You read the paper in six stretches. Five times it stops and asks you to commit to an answer before the next stretch supplies the authors'. Write what you actually think, because the comparison is the exercise. This is the last lesson of the module, and the companion to its other guided reading, [[../Lenses/XLab Control - collusion-guided|How to prevent collusion in untrusted monitoring]].

#### Article
source:: [[../articles/sreevatsa-basic-legibility-protocols-improve-trusted-monitoring]]
from:: ###### Abstract
to:: We introduce legibility protocols, which encourage the untrusted model to take actions that are easier for a monitor to evaluate.

#### Article
from:: ## 1 Introduction
to:: To address this, we introduce legibility protocols, which augment trusted monitoring by encouraging the untrusted model to take actions the monitor can more easily evaluate.
{>>{"author":"Elias's AI","timestamp":1789040126953}@@The abstract's second paragraph and the rest of the introduction, including the contributions list, are skipped on purpose: they state the findings that the next four checkpoints ask the learner to predict. XLab's page suppresses exactly these passages. They remain visible in the article's collapsed text.<<}

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

The paper uses a competitive programming dataset (APPS) to perform its evaluations. Is the APPS dataset a good dataset to test if legibility helps a monitor? Furthermore, try to come up with a task that would make legibility look useless.

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

Try to predict whether or not legibility protocols that allow commenting outperform those that don't allow commenting, and elaborate why you think this is the case.

*Minimum 60 characters.*
assessment-instructions:: Score out of 100. 20: a clear prediction, in either direction. 80: the reasoning, 40 for at least one sound mechanism by which comments change how the monitor judges honest or backdoored code (for example explanations help the monitor understand correct but complex code, or let an attacker argue that its backdoor is correct), and 40 for weighing the two sides: comments are available to both the honest and the attacking policy, and the answer says which side gains more and why (for example that correct code is easier to explain than a backdoor). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Commenting should do better. Comments help both sides: an attacker can argue that its backdoor is correct. But most of the monitor's false alarms come from not understanding correct code, so explanations lower the suspicion of honest code, and honest code is easier to justify than a backdoor, so the blue team gains more."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say which mechanisms the learner reached, name the side of the ledger they neglected in one sentence. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a monitor does with a correct solution it cannot follow. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ## 3 Experiments
to:: [[#^e-3-attack-policy|E.3]] for details).

#### Text
content::
:::callout {title="A tempting objection that doesn't bite" tone="neutral"}
Pause on the result just stated, because the intuition cuts the other way. Surely writing an outright *lie* in a comment is risky for the attacker: if the monitor catches the lie, the game is up. True, but that cuts both ways and roughly cancels. If the monitor doesn't notice the lie, the lie did its job and lowered suspicion. If it does notice, it already has what it needs, because honest code has no reason to lie, so a caught lie is decisive. A noticed lie and an unnoticed lie push in opposite directions, and empirically lying comments are not reliably more suspicious than comments that merely omit. The attacker's problem is not that lying is *punished*; it is that lying, even when it works, still can't manufacture a *coherent* justification for code that is actually wrong.
:::

#### Article
from:: #### 3.2.3 Mechanisms Driving the Benefits of Commenting
to:: For both backdoors, extensive commenting fails to legitimize the code because the justification conflicts with Python semantics known to the monitor.

#### Question: Open
id:: 15163117-8c60-4fdf-8551-88c70637a33a
content::
\## Before you read on

Every result so far used one monitor (GPT-4.1-nano). Now sweep the monitor's capability, from near-useless up toward U's own level. Predict how the *value of commenting* moves as the monitor gets stronger: steadily up, steadily down, or something non-monotonic? Tie your prediction to the two drivers you just named, and say where commenting must be worth exactly nothing.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 30: the shape: non-monotonic, the value of commenting rises and then falls as the monitor gets stronger. 40: where commenting is worth exactly nothing, 20 each: with a useless (random) monitor, which no explanation can help, and with a perfect monitor, which already catches every backdoor. 30: tying the prediction to the two drivers, 15 each: backdoored code being harder to justify than honest code, which pays off more as a stronger monitor becomes harder to mislead; and the narrower spread of the suspicion distributions (variance reduction), with a reasoned view of whether it changes with the monitor's strength. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Non-monotonic: a hump. At both extremes commenting is worth nothing: it cannot help a random monitor, and a perfect monitor is already at 100% safety. In between, a stronger monitor is harder to mislead, so it tells genuine justifications from merely plausible ones better and more backdoors stay suspicious even when commented: the second driver, backdoors being harder to justify, strengthens. The paper finds no clear evidence that the first driver, variance reduction, grows or shrinks with the monitor's strength. So the value of commenting rises and then falls as T improves from random to perfect. The experiments only measure the rising side: the monitors tested run from Gemma 3 4B (8% on APPS) to GPT-4.1-mini (56%), all well below U's 82.4%."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. If anything is missing or wrong, name the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what an explanation buys a monitor that was already going to catch every backdoor. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/sreevatsa-basic-legibility-protocols-improve-trusted-monitoring-img6-905cf62b.png)
to:: This risks overfitting to GPT-4.1-nano, but we see no anomalous performance jump for that model relative to others, suggesting our policies generalize reasonably.
{>>{"author":"Elias's AI","timestamp":1789040126953}@@The from anchor is the first image of Figure 6. XLab moves Figure 6 out of the end of Section 3.2.3 and into Section 3.3, so it sits with the scaling result it reports and behind the checkpoint that asks the learner to predict that result. Starting the excerpt at the figure reproduces both effects.<<}

#### Text
content::
:::callout {title="A hump, and the honesty of only measuring half of it" tone="neutral"}
The measured trend runs the way the second driver predicts: as the monitor gets stronger it distinguishes genuine justifications from superficially-plausible ones better, so more backdoors stay suspicious even when commented, and commenting helps the blue team more. But note the shape of the *full* claim. At both extremes commenting is worthless, since a random monitor can't be helped and a perfect monitor is already at 100% safety, so the real curve is a hump, and the experiments only climb its left side. The authors say so plainly, and Appendix G.3 is candid about why they stop: pushed to stronger monitors, their setup springs a new leak (a strong monitor flags the honest policy's *genuine mistakes*, inflating benign suspicion), and fixing it would mean re-running the whole red-team/blue-team game for each monitor. Knowing which part of a predicted curve you have actually earned, and saying so, is part of the craft.
:::
{>>{"author":"Elias's AI","timestamp":1789040126953}@@XLab's own commentary. XLab places it inside Section 3.3, before the paper's closing paragraph about not running a separate control evaluation for each T; here it follows the whole section.<<}

#### Question: Open
id:: 5ab804ac-d2a4-430b-8414-f4e2ccd1be5b
content::
\## Before you read on

The results are in. State the update three ways.

1. For a lab running trusted monitoring today: strip comments or allow them, and under what conditions does your answer flip?
2. For control methodology: legibility is a new lever sitting alongside the monitor and the auditing budget. What does having it change about how you design a protocol?
3. The limits: list what this paper has *not* shown, and the assumptions a skeptic should lean on hardest.

*Minimum 150 characters.*
assessment-instructions:: Score out of 100. 33: part 1, 13 for the recommendation with its reason (allow comments, and have the policy explain thoroughly, because the blue team gains more from them than the red team), and 10 each for up to two sound conditions under which the answer would flip, such as a monitor near either extreme, tasks where explanations cannot be checked or are not needed, settings where a caught backdoor is not incriminating, or comments being used to jailbreak the monitor. 33: part 2, 16 for seeing that legibility acts on what the policy produces rather than on the monitor or the audit budget, so it is a further design choice to make and to test against the red team, and 17 for the design test it implies: an intervention is only worth having if it helps the honest policy more than the attacker, separating the two suspicion distributions rather than shifting both. 34: part 3, 12, 11 and 11 for each of up to three distinct genuine limitations or load-bearing assumptions, such as a single dataset or a single untrusted model, perfect auditing, a red team given handcrafted backdoor ideas and full knowledge of the protocol, policies tuned for one monitor reused across the monitor sweep, or only the rising side of the hump being measured. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. Allow comments, and instruct the policy to explain its code thoroughly: in this setting the blue team gains more from explanations than the red team does. The answer could flip with a monitor near either extreme (random, or already near-perfect); on tasks where honest solutions need no explanation, or where an explanation cannot be checked against the code; in settings that are not high-stakes, where a caught backdoor is not incriminating and does not lead to shutdown; or if comments let U jailbreak T, which the paper does not study. 2. Legibility acts on what the policy produces, not on the monitor or the auditing budget, so it is a further thing to design and to test against the red team. The test for any legibility intervention is whether it helps the honest policy more than the attacker: one that helps both equally moves both suspicion distributions together and buys no safety. What matters is how well the two distributions separate, and since the audit threshold is set from the honest distribution, lowering honest suspicion is what tightens the threshold. 3. The paper uses one dataset (499 APPS problems, chosen partly for budget) and one untrusted model (o4-mini, never varied); it assumes perfect auditing, so every caught backdoor counts as incriminating; the red team got a handcrafted list of backdoor ideas and full sight of the blue team's protocol, which may overstate a real adversary; the attack policy's filter thresholds were not optimized, for cost reasons; jailbreaking through comments was not studied; the results depend on how hard each team was played, and apparent fixed points later moved; and only the rising half of the predicted hump was measured."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say which of the three parts is weakest and why, in one or two sentences. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a lab would have to believe about its own monitor before stripping comments made sense. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ## 4 Related Works
to:: One method would be to train models using a prover-verifier setup similar to [Kirchner et al. (2024)](#bib.bib11).

#### Text
content::
:::callout {title="The transferable idea: legibility as an asymmetric lever" tone="neutral"}
Step back from commenting specifically. The result that generalizes is a test for *any* legibility intervention: an affordance that helps the honest and the adversarial policy **equally** is worthless for control, because it slides both distributions together and changes nothing about separating them. The interventions that matter cash in an *asymmetry* the adversary can't share. Here the asymmetry is that honest code can always be truthfully explained, while a backdoor constrains its own justifications until often none exists; commenting is valuable precisely, and only, because it lets that asymmetry reach the monitor.

That also places this paper against the module's other guided reading, [[../Lenses/XLab Control - collusion-guided|How to prevent collusion in untrusted monitoring]]. The untrusted-advice protocol *argued* its safety from an information bottleneck and deferred the control evaluation; this paper *ran* the control evaluation, a full red-team versus blue-team game with measured safety and usefulness, and let the numbers settle a bet that looked, on its face, reckless. One priced the channel in bits; the other in the differential payoff of an explanation. High-stakes control is largely the search for these asymmetric levers, and for honest ways to measure them.
:::

#### Text
optional:: true
content::
\## If you want to go further

The appendices are collapsed on the source page and are not required here either. Appendix B explains why the dataset was cut to the 499 APPS problems with the most test cases, Appendix D lists every legibility intervention the blue team tried and discarded, Appendix F gives the Gaussian model behind the variance argument, Appendix G covers the monitor sweep in full, and Appendix I chases the comment "halo" effect.

Every policy and monitor prompt used in the paper is published. The authors note that o4-mini resisted writing deliberately backdoored code, so the attack prompts are framed as a fictional scenario in which it is a teacher building debugging exercises for students.

:::callout {title="Prompt files from the replication repo" tone="neutral" collapse="closed"}
Blue team, Appendix D.3:
- [Commenting benign policy prompt](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/benign_policies/commenting_benign_prompt.txt)
- [No commenting benign policy prompt](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/benign_policies/no_comments_benign_prompt.txt)
- [Monitor prompt, the same in both regimes](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/monitors/aaron_prompt_modified.txt)

Red team, Appendix E.5:
- [Initial backdoor generation prompt](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/attack_policies/no_comments_generation_prompt.txt)
- [Internal suspicion evaluation prompt](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/attack_policies/false_positive_monitor_prompt.txt)
- [Rarity evaluation prompt](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/attack_policies/rate_rarity_prompt.txt)
- [Commenting prompt](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/attack_policies/spam_commenting_prompt.txt)
- [Exploit construction prompt](https://github.com/TheAshwinner/legibility-ai-control/blob/main/official_replication/attack_policies/construct_exploit_prompt.txt)
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Sreevatsa, Ashwin, Sebastian Prasanna, and Cody Rushing. "Basic Legibility Protocols Improve Trusted Monitoring." *arXiv*, 9 Feb. 2026. [arxiv.org](https://arxiv.org/abs/2602.10153)
*The reading this lesson is built around: a control evaluation in the APPS backdooring setting testing whether letting the untrusted model explain its code helps the blue team more than the red team.*

Sreevatsa, Ashwin. *legibility-ai-control*. GitHub. [github.com](https://github.com/TheAshwinner/legibility-ai-control)
*The paper's replication repository, holding the attack policy, benign policy and monitor prompts that Appendices D.3 and E.5 link to.*

XLab. "Basic legibility protocols improve trusted monitoring (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/legibility-guided)
*The source lesson this page adapts.*
:::
