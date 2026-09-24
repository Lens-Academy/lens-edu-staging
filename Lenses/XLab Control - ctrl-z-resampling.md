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
assessment-instructions::The learner is being checked on one term from section 1 of the Ctrl-Z paper. Full marks for saying that an untrusted model is one with the potential to be deliberately subversive. Give substantial credit for the reason: it may have developed misaligned goals and "faked alignment" during testing, so the deployer cannot assume it will behave as desired. Mark down an answer that treats "untrusted" as a verdict that the model is misaligned rather than a statement about what the deployer is unable to rule out. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

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
assessment-instructions::The learner is being checked on a definition from section 2.3 of the Ctrl-Z paper. Full marks require all three parts: the untrusted model is implemented with the honest policy $U_H$; the measure is the proportion of tasks the control protocol solves in the episode; the number is normalised so that $U_H$ scores 100 percent and the trusted model $T$ scores 0 percent. Give partial credit for the proportion-of-tasks-solved idea alone, but say which part is missing. An answer that describes safety instead of usefulness gets no credit. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 9a40d912-a5db-44f3-b4c0-43ca0fc66a2a
content:: How does the Ctrl-Z paper define safety?
assessment-instructions::The learner is being checked on a definition from section 2.3 of the Ctrl-Z paper. Full marks require: the untrusted model is implemented with the attack policy $U_A$; safety is the probability that the blue team wins; winning means reaching the end of the 100,000-task episode without allowing the agent to download and execute malware. Give partial credit for "the probability the attack never succeeds" and name the missing pieces. Accept "100,000 tasks" or "the full episode" as the horizon. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Text
content::
\## The protocols, inherited and new

Section 3.1 works through the protocols carried over from earlier control work and what each one scores. Section 3.2 is this paper's contribution. The three questions after the reading are the mechanism, and the demo after them lets you move the two dials the mechanism turns on.

#### Article
from:: "2.4 Performing Control Evaluations Iteratively"
to:: "Table 1: Safety scores for different protocols at 90%, 95%, and 99% usefulness"

#### Question: Open
id:: db1857ef-6a88-4f1b-8888-d8f14da5a986
content:: What are resample protocols?
assessment-instructions::The learner is being checked on the paper's central idea, section 3.2. Full marks for: control protocols that exploit the statelessness of the untrusted model to dynamically take additional samples of certain actions. Give substantial credit for either of the two payoffs, and full credit for both: (1) resampling lets accidentally suspicious-looking honest code be replaced by clearly benign actions, avoiding unnecessary audits; (2) when the model is attacking, resampling either produces benign completions or gathers many suspicious samples as incriminating evidence. The statelessness point matters: the model cannot remember that it was already asked, so the samples are independent. Say so if the learner misses it. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 99cfb456-5ab1-45b6-9ecf-5e11363e3e07
content:: How does the Defer to resample protocol work?
assessment-instructions::The learner is being checked on a protocol definition from section 3.2 of the Ctrl-Z paper. The four steps, all needed for full marks: (1) if the trusted monitor's suspiciousness score for $U$'s action is above the deferral threshold, generate up to two new samples from $U$; (2) if any sample falls under the threshold, execute the least suspicious one; (3) if all samples stay above it, implement an action by the trusted model $T$ instead; (4) if the minimum of all samples is above the auditing threshold, audit the most suspicious sample. Award roughly a quarter per step. Watch for the common slip of auditing the least suspicious sample, or of executing the first acceptable sample rather than the least suspicious one. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 3f258d4c-c102-4fdc-a376-5508fb4e1494
content:: What is the attack continuation probability, and why must the red team keep it high against resampling?
assessment-instructions::The learner is being checked on section 3.2 of the Ctrl-Z paper. Full marks need both halves. Definition: the probability that, once the first attack step got in, the attack policy continues the attack on a given step. Consequence: against Defer to resample, a low value is disastrous for the red team, because attack steps get resampled until a benign action appears, so resampling selects for innocent behaviour; few attacks ever complete, and every incomplete attack is another chance to get caught. Give half credit for a correct definition with no consequence, and half for the consequence with a vague definition. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

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
