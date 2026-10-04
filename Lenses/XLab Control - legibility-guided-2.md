---
id: 'f217a26e-d6af-4047-a1cd-b01088424e0e'
title: "Basic legibility protocols improve trusted monitoring (2): results, mechanisms and limits"
tldr: "Part 1 ended with your prediction. This part reports whether letting the model explain its code helped the blue team or the attacker more, and why. Then you predict how the effect scales with the monitor's strength, and state what the paper does and does not show."
summary_for_tutor: "Part 2 of 2 of a guided reading of Sreevatsa, Prasanna and Rushing's arXiv paper on legibility protocols. Part 1 covered the setting (APPS backdoors, U = o4-mini, T = GPT-4.1-nano, perfect auditing at 2%, Defer to Trusted) and ended with the learner predicting whether commenting beats no commenting. This part reads Section 3 (the results, the effect of commenting on the benign and attack policies, and the mechanisms: variance reduction, and backdoors being harder to justify than honest code), Figure 6 and Section 3.3 (varying the trusted monitor), and Sections 4 and 5 (related work, limitations, future work). It does this in three stretches, with two written checkpoints between them in the source's own order: predict how the value of commenting moves as the monitor gets stronger, and state the overall update three ways. The checkpoint prompts keep the source's wording. Three commentary blocks ('A tempting objection that doesn't bite', 'A hump, and the honesty of only measuring half of it', and 'The transferable idea') are the source's own editorial insertions, reproduced in the positions the source puts them. The opening Text segment and every assessment brief are ours. Each brief's criteria come from the part of the paper that follows that checkpoint. Part 1's excerpts skip the abstract's results paragraph, the introduction's contributions list and Figure 1, so as not to spoil checkpoints. Abstract finding (iii) and the last contribution bullet state the monitor-strength result that Q4 asks the learner to predict, and both are still reachable in the article's collapsed text, so a learner may have seen them. Figure 1 is not shown in either part, although Section 3 cites it for the headline result; if a learner asks, it is in the article's collapsed text. Both checkpoints are answered before the paper gives its own answer, so grade the reasoning rather than agreement with the authors, and never hand over the content of the section that follows. The appendices and the prompt files are optional further reading."
reading_minutes: 26
tutor_minutes: 16
tags: []
---
#### Text
content::
Part 2 of 2. The previous part set up the experiment: APPS backdoors, o4-mini as the untrusted model U, GPT-4.1-nano as the trusted monitor T, a 2% auditing budget, and the Defer to Trusted protocol run with and without comments. It ended with your prediction of whether commenting beats no commenting. This part opens with the answer and the paper's explanation of why, then asks you how the effect changes with a stronger monitor and what the paper has not shown. Two more checkpoints ask you to commit before you read on.

#### Article
source:: [[../articles/sreevatsa-basic-legibility-protocols-improve-trusted-monitoring]]
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
{>>{"author":"James agent legibility-guided's AI","timestamp":1790940116242}@@The from anchor is the first image of Figure 6. XLab moves Figure 6 out of the end of Section 3.2.3 and into Section 3.3, so it sits with the scaling result it reports and behind the checkpoint that asks the learner to predict that result. Starting the excerpt at the figure reproduces both effects.<<}

#### Text
content::
:::callout {title="A hump, and the honesty of only measuring half of it" tone="neutral"}
The measured trend runs the way the second driver predicts: as the monitor gets stronger it distinguishes genuine justifications from superficially-plausible ones better, so more backdoors stay suspicious even when commented, and commenting helps the blue team more. But note the shape of the *full* claim. At both extremes commenting is worthless, since a random monitor can't be helped and a perfect monitor is already at 100% safety, so the real curve is a hump, and the experiments only climb its left side. The authors say so plainly, and Appendix G.3 is candid about why they stop: pushed to stronger monitors, their setup springs a new leak (a strong monitor flags the honest policy's *genuine mistakes*, inflating benign suspicion), and fixing it would mean re-running the whole red-team/blue-team game for each monitor. Knowing which part of a predicted curve you have actually earned, and saying so, is part of the craft.
:::
{>>{"author":"James agent legibility-guided's AI","timestamp":1790940116242}@@XLab's own commentary. XLab places it inside Section 3.3, before the paper's closing paragraph about not running a separate control evaluation for each T; here it follows the whole section.<<}

#### Question: Open
id:: 5ab804ac-d2a4-430b-8414-f4e2ccd1be5b
content::
\## Before you read on

The results are in. State the update three ways.

1. For a lab running trusted monitoring today: strip comments or allow them, and why? Under what conditions does your answer flip?
2. For control methodology: legibility is a new lever sitting alongside the monitor and the auditing budget. What does having it change about how you design a protocol, and what would any new legibility intervention have to do to be worth adding?
3. The limits: list what this paper has *not* shown, and the assumptions a skeptic should lean on hardest.

*Minimum 150 characters.*
assessment-instructions:: Score out of 100. 33: part 1, 13 for the recommendation with its reason (allow comments, because the blue team gains more from them than the red team), and 10 each for up to two sound conditions under which the answer would flip, such as a monitor near either extreme, tasks where explanations cannot be checked or are not needed, settings where a caught backdoor is not incriminating, or comments being used to jailbreak the monitor. 33: part 2, 16 for seeing that it adds a further design choice, about what the policy is asked to produce, that has to be chosen and tested against the red team together with the monitor and the audit budget, and 17 for what an intervention has to do: help the honest policy more than the attacker (said either way: it must separate the honest and attack suspicion levels rather than lower both). 34: part 3, 12, 11 and 11 for each of up to three distinct genuine limitations or load-bearing assumptions, such as a single dataset or a single untrusted model, perfect auditing, a red team given handcrafted backdoor ideas and full knowledge of the protocol, policies tuned for one monitor reused across the monitor sweep, or only the rising side of the hump being measured. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. Allow comments, and instruct the policy to explain its code thoroughly: in this setting the blue team gains more from explanations than the red team does. The answer could flip with a monitor near either extreme (random, or already near-perfect); on tasks where honest solutions need no explanation, or where an explanation cannot be checked against the code; in settings that are not high-stakes, where a caught backdoor is not incriminating and does not lead to shutdown; or if comments let U jailbreak T, which the paper does not study. 2. Legibility acts on what the policy produces, not on the monitor or the auditing budget, so it is a further thing to design and to test against the red team. The test for any legibility intervention is whether it helps the honest policy more than the attacker: one that helps both equally moves both suspicion distributions together and buys no safety. What matters is how well the two distributions separate, and since the audit threshold is set from the honest distribution, lowering honest suspicion is what tightens the threshold. 3. The paper uses one dataset (499 APPS problems, chosen partly for budget) and one untrusted model (o4-mini, never varied); it assumes perfect auditing, so every caught backdoor counts as incriminating; the red team got a handcrafted list of backdoor ideas and full sight of the blue team's protocol, which may overstate a real adversary; the attack policy's filter thresholds were not optimized, for cost reasons; jailbreaking through comments was not studied; the results depend on how hard each team was played, and apparent fixed points later moved; and only the rising half of the predicted hump was measured."
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
*The reading this lesson is built around: a control evaluation in the APPS backdooring setting testing whether letting the untrusted model explain its code helps the blue team more than the red team. This part covers the results, the mechanisms, the monitor sweep and the limitations.*

Sreevatsa, Ashwin. *legibility-ai-control*. GitHub. [github.com](https://github.com/TheAshwinner/legibility-ai-control)
*The paper's replication repository, holding the attack policy, benign policy and monitor prompts that Appendices D.3 and E.5 link to.*

XLab. "Basic legibility protocols improve trusted monitoring (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/legibility-guided)
*The source lesson this page adapts.*
:::
