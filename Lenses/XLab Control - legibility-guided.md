---
id: 'df595298-8c2c-4a28-83af-dbc5712274c5'
title: "Basic legibility protocols improve trusted monitoring"
tldr: "A weak monitor cannot flag code it cannot follow. So stop fixing the monitor and change the code: make the untrusted model explain every line. That also hands an attacker a channel for lying about its own backdoor, which sounds like a terrible trade. Five times in this paper you predict the result before the authors report it."
summary_for_tutor: "Ported from XLab's AI Control curriculum, Module 4, the last lesson of the module and one of its two guided readings. Sreevatsa, Prasanna and Rushing's arXiv paper on legibility protocols is split into six reading stretches, and XLab's five written checkpoints sit between them in XLab's own order: propose legibility interventions, judge whether APPS is the right dataset, predict whether commenting beats no commenting, predict how the value of commenting moves as the monitor gets stronger, and state the overall update three ways. The checkpoint prompts are XLab's wording. Four short commentary blocks (the note on why competitive programming fits, 'A tempting objection that doesn't bite', 'A hump, and the honesty of only measuring half of it', and 'The transferable idea') are XLab's own editorial insertions, reproduced in the positions XLab puts them. The opening Text segment and every assessment brief are ours; each brief's criteria come from the part of the paper that follows that checkpoint. The excerpt anchors deliberately skip three passages that would spoil a checkpoint, exactly as XLab's page does: the abstract's results paragraph, the introduction's contributions list, and Figure 1. Those passages are still reachable in the article's collapsed text, so a learner may have seen them. Every checkpoint is a prediction written before the result has been read, so grade the reasoning rather than agreement with the authors, and never hand over the content of the section that follows."
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
assessment-instructions:: The learner has read only the abstract's opening paragraph and the first three paragraphs of the introduction, and has not yet seen any of the paper's interventions. Grade the interventions they propose and the mechanism they give for each, not agreement with the authors. The target answers, all from Section 3.1 and Appendix D.1, are: thorough commenting, meaning line-by-line comments, docstrings and file-level comments that explain the overall correctness of the algorithm, name sub-algorithms such as the Miller-Rabin primality test, and justify leaps of logic, design decisions and claims about optimality; small, modular functions; descriptive variable and function names; writing code without special cases or edge cases; and avoiding optimizations in favour of simpler, better-known algorithms even at a performance cost. Credit any of these. Credit more heavily an answer whose stated mechanism is that the monitor's false positives come mostly from failing to understand a correct solution, so the intervention has to transmit the reasoning rather than merely tidy the surface of the code. Credit noticing that the same affordance is available to an attacker. Do not require the learner to rank the interventions, and do not require commenting to be among them. Reply in 60 to 120 words, short paragraphs, no lists. Name what is present, name the single largest gap in one sentence, and stop: Section 3.1 supplies the authors' ranking much later in the lesson, so do not preview which intervention won. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold from the setup, for example asking why a monitor would call a correct but unfamiliar algorithm suspicious, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Article
from:: ## 2 Setting
to:: We use a smaller subset of APPS’s test split consisting of 499 problems with the most test cases.

#### Question: Open
id:: 5de450fc-77a3-431f-a713-32f743d74183
content::
\## Before you read on

The paper uses a competitive programming dataset (APPS) to perform its evaluations. Is the APPS dataset a good dataset to test if legibility helps a monitor? Furthermore, try to come up with a task that would make legibility look useless.

*Minimum 100 characters.*
assessment-instructions:: The learner has read the setting and the dataset description and is judging the choice before XLab's note and Appendix B.2 answer it. The criteria in favour of APPS: legibility only has work to do when U and T differ in reasoning power rather than in knowledge, so that T cannot follow U's steps without an explanation, and competitive programming emphasises exactly that intelligence advantage; APPS solutions are hard to discover but easy to explain once found, which is the shape a legibility intervention needs; and models plausibly usable as trusted monitors are already highly knowledgeable about programming, so a reasoning gap is the faithful proxy for future control settings. Credit as an extra the point that the setting needs enough test cases for a caught backdoor to be incriminating rather than passable as an honest mistake, which is why the authors kept only the 499 APPS problems with the most test cases. For the second half, the target is a task that hinges on knowledge rather than reasoning, for example one turning on an obscure library or function, where a comment asserting that a rare function exists gives the monitor nothing verifiable and could simply be fabricated; a monitor able to check such a claim could have checked it without the comment. Credit any equivalent construction, including a task whose honest solutions are already simple enough for T to verify unaided, so there is no comprehension gap to close. Reply in 60 to 120 words, short paragraphs, no lists. Say whether each half of the question was answered, and name at most one thing they missed in a few words without explaining it, since the next block and Appendix B.2 do. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what an explanation is worth when the monitor could already have verified the code by itself. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: The learner has read the setting but none of the results, and is predicting the paper's headline finding. The finding is that commenting protocols outperform no-comments protocols across the safety and usefulness metrics. Grade the reasoning, not the direction of the guess: a well-argued prediction that commenting loses earns close to full credit if it names real mechanisms. The mechanisms that favour the blue team, from Sections 3.1 and 3.2.3, are: most monitor false positives come from the monitor failing to understand a correct solution, so explanation lowers benign suspicion and pulls the audit threshold down; commenting shrinks the variance of both the benign and the attack suspicion distributions, and shrinking both makes them more separable; and justifying benign code is easier than justifying a backdoor, because a backdoor constrains the explanations available to it until often no coherent one exists. The mechanisms that favour the red team, from Section 3.2.2, are: comments let the attack policy argue that backdoored code is necessary or correct, comments explain the correct parts of an attacked solution just as they do for benign code, and commented code draws lower scores even when the monitor names no reason. Credit an answer that sees the affordance is symmetric and asks which side gains more; that framing is worth more than a bare verdict. Reply in 60 to 120 words, short paragraphs, no lists. Say which mechanisms the learner reached, name the side of the ledger they neglected in one sentence, and do not settle the question: Section 3 does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a monitor does with a correct solution it cannot follow. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: The learner has just read Section 3.2.3 and is predicting Section 3.3 before reading it. The two drivers they have just named are (1) variance reduction of the benign and attack suspicion distributions, which separates them, and (2) backdoored code being harder to justify than benign code. The target answer is non-monotonic: a hump. The two zero points are the part that must be present for full credit, because the question asks for them directly: commenting cannot help a random monitor, and it cannot help a perfect monitor that is already at 100 percent safety, so its value rises and then falls as T improves from random to perfect. Credit the mechanism for the rising side: as T improves it is harder to mislead, so more backdoors stay suspicious even when commented, which is driver 2 strengthening. Credit noticing that the paper reports no clear evidence that driver 1 grows or shrinks with T's capability. Credit as an extra the observation that the experiments can only climb the left side of the hump, since the monitors tested run from Gemma 3 4B at 8 percent APPS performance to GPT 4.1-mini at 56 percent, all well below U's 82.4 percent. An answer that predicts a steady monotonic trend without naming a zero point is partial credit at best. Reply in 60 to 120 words, short paragraphs, no lists. Say whether the shape and both zero points are present, and do not explain the mechanism they missed: Section 3.3 and the commentary after it do. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what an explanation buys a monitor that was already going to catch every backdoor. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: This is the closing synthesis, written before the learner reads Sections 4 and 5. Grade all three parts. Part 1: the paper's answer is to allow comments, and to instruct the policy to explain thoroughly, because the blue team's gain outweighs the red team's. Credit flip conditions drawn from what the learner has read: a monitor near either extreme, random or already near-perfect; a task where the honest solution needs no explanation, or where an explanation cannot be checked against the artifact; a setting that is not high-stakes, so a caught backdoor is not incriminating and the protocol would not shut the model down; and the possibility, which the authors explicitly do not study, that comments let U jailbreak T. Part 2: the criterion is that legibility acts on the policy rather than on the monitor or the audit budget, and that the test for any legibility intervention is whether it helps the honest policy more than the adversarial one. An intervention that helps both equally moves both distributions together and buys no safety. Credit connecting this to separability, and to the fact that the audit threshold is set from the benign distribution, so lowering benign suspicion is what tightens the threshold. Part 3, from Section 5.1: one dataset, 499 APPS problems, chosen partly for budget; one untrusted model, o4-mini, never varied; perfect auditing assumed, so every caught backdoor is treated as incriminating; the red team handed a handcrafted list of backdoor ideas and full sight of the blue team's protocol, which may overstate a real adversary; attack-policy filter thresholds left unoptimized for cost reasons; jailbreaking through comments not studied; results dependent on how hard each team was played, with the authors reporting apparent fixed points that later moved; and only the left half of the predicted hump measured. Reply in 60 to 120 words, short paragraphs, no lists. Say which of the three parts is weakest and why, in one or two sentences, and do not supply the limitations they missed: Section 5.1 lists them. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a lab would have to believe about its own monitor before stripping comments made sense. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
