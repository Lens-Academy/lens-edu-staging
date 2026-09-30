---
id: '0cf3f655-4ca7-45cf-b82d-cbfddd66b915'
title: "Ctrl-Z resampling (1): the agent setting and Defer to resample"
tldr: "Your monitor flags a command. You can run it anyway, or hand the job to a weaker model that will probably botch it. This paper finds a third move: ask the same model again. It is stateless, so it cannot remember what it just tried, and an attack that has to survive every resample mostly fizzles."
summary_for_tutor: "Part 1 of 2 of the Ctrl-Z paper (arXiv:2504.10374), embedded inline in three excerpts with six one-turn recall questions placed where the paper covers them; part 2 is the lens ctrl-z-resampling-2. Everything outside the excerpts, the questions and the widget is our own navigational lead-in, sourced from the paper. Sequence: orientation; the abstract and the opening of section 1, then the untrusted-model question; the rest of section 1 through section 2.3, then the usefulness and safety definitions; sections 2.4 to 3.2 including Table 1, then three questions on resample protocols, Defer to resample and the attack continuation probability, then the Defer to resample widget between a short lead-in and a closed callout. Everything after section 3.2 (incrimination in the present, three strikes, time travel, untrusted monitoring, discussion) is in part 2 and renders collapsed here, as do the references and appendices, so assume a learner has not read them yet. The widget is an interactive schematic of one step under Defer to resample, with two sliders: k, the number of samples drawn, and c, the red team's attack continuation probability. It holds only the sliders, the chart and the four outcome readouts: the lead-in above it says the distributions are schematic rather than the paper's measured data, and the closed callout below it, titled What the two moves show, states the two effects the sliders demonstrate, so a learner may have left it unopened. The companion talk by Aryan Bhatt is a separate lens, monitoring-and-mitigation; send a learner who wants the intuition there rather than re-explaining it."
reading_minutes: 45
tutor_minutes: 5
tags: []
---
#### Text
content::
\## Before you read

This is the paper behind the talk in [[../Lenses/XLab Control - monitoring-and-mitigation|Monitoring and Mitigation]]. Aryan Bhatt, one of its authors, gave you the shape of the protocols there in about twenty minutes. This page is where the setting, the thresholds and the numbers live.

It extends [[../Lenses/XLab Control - ai-control-paper|AI Control: Improving Safety Despite Intentional Subversion]] from single-step backdoored code to a multi-step agent, and it uses the vocabulary of [[../Lenses/XLab Control - control-evaluations|Control Evaluations]]: a blue team proposing protocols, a red team building an attack policy, and a usefulness and safety pair scored over one long episode.

The paper is split across two lessons. This is part 1 of 2: the setting, the two metrics, the protocols inherited from earlier work and the new Defer to resample protocol, in three stretches with recall questions after each. [[../Lenses/XLab Control - ctrl-z-resampling-2|Part 2]] reads on from section 3.2.1: resampling as evidence, untrusted monitoring, and the authors' own limitations. The rest of the paper, including the acknowledgments, the references and the twelve appendices, starts out collapsed here: the appendices are not assigned, but the attack templates, the monitor prompts and the dataset construction are there if you want them.
{>>{"author":"Elias's AI","timestamp":1789039901599}@@Excerpt anchors verified against the stored article on 2026-09-10: each from and to string occurs exactly once, and every to falls after its from. Section 4 is anchored on its first paragraph rather than its heading, because the string "4 Untrusted Monitoring" also appears inside figure and table link titles in the article and so is not unique. Avoid anchoring on any sentence containing a citation like "et al.": those carry a non-breaking space that this editor normalises to a plain space.<<}

#### Article
source:: [[../articles/bhatt-ctrl-z-controlling-ai-agents-via-resampling]]
from:: "Control evaluations measure whether monitoring and security protocols for AI systems prevent intentionally subversive AI models from causing harm."
to:: "We call models that have the potential to be deliberately subversive untrusted models."

#### Question: Open
id:: b960d8af-9e6f-49ae-b904-5024917c8d5c
content:: In AI control research, what makes a model "untrusted"?
assessment-instructions:: Score out of 100. 60: it has the potential to be deliberately subversive: it could intentionally work against the deployer and its safety measures. 40: this is a possibility the deployer cannot rule out (it might, for example, have misaligned goals and have faked alignment during testing), so it cannot be assumed to behave as desired. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer treats "untrusted" as a finding that the model is misaligned rather than as something the deployer is unable to rule out. Model answer, for the feedback, not a grading checklist: "It has the potential to be deliberately subversive. For example, it may have developed misaligned goals and "faked alignment" during testing, so the deployer can't assume it will behave as desired."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## The setting, and the two metrics

The rest of section 1 states the contributions. Section 2 builds the task set, names the untrusted and trusted models and the human auditing budget, and then defines the two numbers every later result is quoted in. Those two definitions carry the whole results section.

#### Article
from:: "Developers can mitigate risks in two ways:"
to:: "The blue team aims to develop control protocols that extend the Pareto frontier of the two."

#### Question: Open
id:: 5891b472-5e25-457f-b957-adc695886158
content:: How does the Ctrl-Z paper define usefulness?
assessment-instructions:: Score out of 100. 30: usefulness is measured with the untrusted model playing honestly (the honest policy $U_H$), not attacking. 40: it is the proportion of tasks the control protocol solves over the episode. 30: it is normalised so that the honest untrusted model alone scores 100% and the trusted model $T$ scores 0%. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Implement $U$ with the honest policy $U_H$ and measure the proportion of tasks the control protocol solves in the episode, normalized so that $U_H$ scores 100% and the trusted model $T$ scores 0%."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 9a40d912-a5db-44f3-b4c0-43ca0fc66a2a
content:: How does the Ctrl-Z paper define safety?
assessment-instructions:: Score out of 100. 30: safety is measured with the untrusted model replaced by the red team's attack policy $U_A$. 30: it is the probability that the blue team wins. 40: what winning means, 20 each: the protocol gets through the whole episode (the 100,000 tasks), and the agent never manages to download and execute the malware. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Implement $U$ with the attack policy $U_A$ and measure the probability that the blue team wins by reaching the end of the 100,000-task episode without allowing the agent to download and execute malware."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## The protocols, inherited and new

Section 3.1 works through the protocols carried over from earlier control work and what each one scores. Section 3.2 is this paper's contribution. The three questions after the reading are the mechanism, and the demo after them lets you move the two dials the mechanism turns on.

#### Article
from:: "2.4 Performing Control Evaluations Iteratively"
to:: "Table 1: Safety scores for different protocols at 90%, 95%, and 99% usefulness"

#### Question: Open
id:: db1857ef-6a88-4f1b-8888-d8f14da5a986
content:: What are resample protocols, and why are they useful?
assessment-instructions:: Score out of 100. 50: resample protocols draw additional samples from the untrusted model for certain actions (typically ones the monitor finds suspicious) instead of simply running, auditing or replacing them. 20: this relies on the model being stateless: it does not remember having been asked before, so each new sample is an independent draw. 30: why this is useful, 15 each: an honest action that happens to look suspicious can be replaced by a clearly benign sample, avoiding an unnecessary audit; against an attacking model, resampling either yields benign completions or piles up several suspicious samples as incriminating evidence. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Control protocols that exploit the statelessness of the untrusted model to dynamically take additional samples of certain actions. Resampling lets accidentally suspicious-looking honest code be replaced by clearly benign actions (avoiding unnecessary audits), and when the model is attacking it either samples benign completions or gathers many suspicious samples as incriminating evidence."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 99cfb456-5ab1-45b6-9ecf-5e11363e3e07
content:: How does the Defer to resample protocol work?
assessment-instructions:: Score out of 100. 25 per step: (1) when the trusted monitor rates $U$'s action above the deferral threshold, draw a few new samples from $U$ (up to two); (2) if any sample is below the deferral threshold, execute the least suspicious one (15 if the answer executes the first acceptable sample instead); (3) if every sample stays above the deferral threshold, use an action written by the trusted model $T$ instead; (4) if even the least suspicious sample is above the auditing threshold, audit, taking the most suspicious sample (15 if the answer audits the least suspicious one). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "If the trusted monitor's suspiciousness score for $U$'s action is above the deferral threshold, generate up to two new samples from $U$; if any fall under the threshold, execute the least suspicious one. If all samples stay above it, implement an action by $T$ instead. If the minimum of all samples is above the auditing threshold, audit the most suspicious sample."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 3f258d4c-c102-4fdc-a376-5508fb4e1494
content:: What is the attack continuation probability, and why must the red team keep it high against resampling?
assessment-instructions:: Score out of 100. 40: the definition: once an attack has started (its first step got through), the probability that the attack policy carries on with the attack at each later step. 60: why it must be high against resampling, 30: an attack step taken only with low probability tends to be resampled until a benign action comes out, since the least suspicious sample is executed, so resampling selects for innocent behaviour and few attacks ever complete, and 30: every attack started but not completed is one more chance for the blue team to catch the model, so a hesitant attacker gets caught without winning. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The probability that, once the first attack step got in, the attack policy continues the attack on a given step. Against Defer to resample, a low value is disastrous for the red team: attack steps get resampled until a benign action appears (resampling selects for innocent behavior), so few attacks ever complete and every incomplete attack is another chance to get caught."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## Defer to resample, mechanically

One step of the protocol, with the two quantities it turns on: k, how many samples the protocol draws for the step, and c, the attack continuation probability. The distributions below are schematic, not the paper's measured data.

#### Widget
source:: [[../widgets/xlab-control-defer-to-resample]]

#### Text
content::
:::callout {title="What the two moves show (open after you have tried both)" tone="neutral" collapse="closed"}
With c at 100 percent, raising k drifts the innocent minima left, so fewer audits and fewer deferrals are wasted, while the attacked step's minimum stays suspicious. The win-to-lose odds improve.

Lowering c pushes attacked steps into "continue". Resampling selects for benign actions, so most attacks fizzle, and every incomplete attack is one more chance to catch the model on a later step.

That pair of effects is the whole argument for resampling.
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Bhatt, Aryan, Cody Rushing, Adam Kaufman, Tyler Tracy, Vasil Georgiev, David Matolcsi, Akbir Khan, and Buck Shlegeris. "Ctrl-Z: Controlling AI Agents via Resampling." *arXiv*, Apr. 2025. [arxiv.org](https://arxiv.org/abs/2504.10374)
*The reading on this page: the first control evaluation run in an agent environment, and the source of every protocol and number the recall questions ask about.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The earlier control evaluation this paper extends, from single-step backdoored code to a multi-step agent.*

XLab. "Ctrl-Z: Controlling AI Agents via Resampling." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/ctrl-z-resampling)
*The source lesson this page adapts.*
:::
