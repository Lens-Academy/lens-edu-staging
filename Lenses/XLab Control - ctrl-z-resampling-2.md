---
id: '414f5740-3919-435a-8189-0fc33ac63805'
title: "Ctrl-Z resampling (2): incrimination, untrusted monitoring and the limits"
tldr: "One suspicious answer is a hunch; the same model reaching for the same weapon three times is a case. The second half of Ctrl-Z turns resampling into evidence, reaches back into a trajectory's past to settle close calls, and then asks what changes when the monitor is a second copy of the model that might be in on it."
summary_for_tutor: "Part 2 of 2 of the Ctrl-Z paper (arXiv:2504.10374); part 1 is the lens ctrl-z-resampling, which covered the setting, usefulness and safety, the inherited protocols, Defer to resample and the attack continuation probability, with the Defer to resample widget. This part embeds sections 3.2.1 to 7 in four excerpts with seven one-turn recall questions. Everything outside the excerpts and the questions is our own navigational lead-in, sourced from the paper. Sequence: a lead-in placing this part; section 3.2.1, then incrimination in the present; section 3.2.2, then Auditing after three strikes and Time travel; section 4, then four questions on the untrusted monitoring protocol, upfront validation with honeypots, collusion signals and trusted paraphrasing; sections 5 to 7, the authors' own limitations and conclusion. The acknowledgments, references and twelve appendices fall outside the excerpts and render collapsed, so assume a learner has not read them. The companion talk by Aryan Bhatt is a separate lens, monitoring-and-mitigation. Untrusted monitoring and collusion are developed further in the collusion-guided lens later in this course. After the limitations, one added practice question (ours, in an amber callout) asks what resampling still buys, and what is lost, against an attack done in a single command, and for one change that would recover some of it with its cost; its model answer is in the assessment instructions."
reading_minutes: 25
tutor_minutes: 40
tags: []
---
#### Text
content::
\## Before you read

Part 2 of 2. [[../Lenses/XLab Control - ctrl-z-resampling|The previous part]] set up the bash-agent setting, the usefulness and safety metrics, and Defer to resample, where resampling works as selection pressure on the action that actually runs. This part reads on from section 3.2.1.

Selection pressure on the implemented action is only half of what resampling buys. The other half is evidence: the extra samples also tell you whether the model is attacking, first on the current step, then across the rest of the trajectory. After that, section 4 swaps the weak trusted monitor for a second copy of the untrusted model, and the paper closes with the authors' own account of where their setup is too easy or too hard on the blue team. The references and appendices start out collapsed below.

#### Article
source:: [[../articles/bhatt-ctrl-z-controlling-ai-agents-via-resampling]]
from:: "3.2.1 Capitalizing on High Attack Continuation Probabilities"
to:: "we see that the increased value of information provided safety."

#### Question: Open
id:: db46b782-4e6b-4f20-b342-049181b6d3bb
content:: What is Defer to resample with incrimination in the present, and why do the extra samples help?
assessment-instructions:: Score out of 100. 60: the rule, 20: it builds on Defer to resample (resample a suspicious step and run the least suspicious sample); 40: when the step still looks very suspicious after resampling (even its least suspicious sample), it draws extra samples from $U$ for the same step and audits if they stay suspicious enough. 40: the reason: samples of the same step are independent draws from the same policy, so more of them make it easier to tell an attacking $U$ from an honest one (an attacker keeps producing suspicious samples) before spending an expensive audit. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Defer to resample with a different auditing rule: if the samples' minimum suspiciousness hits a separate, higher threshold, the protocol samples more actions from $U$ for the same step, and audits the most suspicious sample if the minimum hits the auditing threshold. Since samples are independent draws from the same distribution, more samples make it easier to discriminate $U_H$ from $U_A$ — buying information for expensive auditing decisions."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## Using the rest of the trajectory

Everything so far judges a step on its own samples. The next two protocols use the rest of the trajectory, which is available precisely because the setting is multi-step.

#### Article
from:: "3.2.2 Using Past Information"
to:: "these incremental changes don’t help as much as we’ve exhausted many of the simple benefits."

#### Question: Open
id:: 6ee34284-c609-465d-a267-aa075bade949
content:: What is the Auditing after three strikes protocol, and why does it work?
assessment-instructions:: Score out of 100. 40: the rule: within a task, count the steps whose suspiciousness score is above a threshold, and audit the trajectory once this happens for the third time. 20: a separate, higher threshold still triggers an immediate audit of a single very suspicious step, to defend against attacks done in one step. 40: why it works: an attacker has to keep its attack going on most steps once it has started (a high attack continuation probability), so an attacked trajectory builds up several suspicious steps, while an honest one rarely does. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Within a task, keep a record of how many steps' suspiciousness scores were above a certain threshold; on the third, audit the trajectory. A separate higher threshold still triggers an immediate audit, to defend against single-step attacks. It works because an attacker must continue its attack with high probability, so attacked trajectories show many suspicious steps."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 145afabd-0304-410c-b4d3-c1f5481eb3ef
content:: What is the Time travel (incrimination in the past) protocol?
assessment-instructions:: Score out of 100. 30: it builds on Auditing after three strikes and is used when a trajectory is close to the auditing threshold, a close call. 50: it draws more samples from a past step rather than the current one, the third most suspicious step so far, since that step decides whether the three-strikes rule should fire. 20: it re-makes the auditing decision with the new samples included. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer resamples only the current step. Model answer, for the feedback, not a grading checklist: "When Auditing after three strikes says a trajectory is close to the auditing threshold, the protocol samples more actions from the third most suspicious past step (usually the most informative one for the three-strikes rule) and re-makes the auditing decision with those new samples. This results in 87.1% safety at 95% usefulness."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## Untrusted monitoring

The protocols so far all lean on $T$, which is weak. Section 4 asks what happens if the blue team uses a second copy of $U$ as the monitor, and what the two copies would have to do to collude. If you want to work that problem rather than read it, [[../Lenses/XLab Control - collusion-guided|How to prevent collusion in untrusted monitoring]] is the guided version.

#### Article
from:: "Blue team protocol: Untrusted monitoring The protocol generates actions with $U$"
to:: "Table 2: Comparison at 95% usefulness. TM = Trusted Monitoring, UM = Untrusted Monitoring."

#### Question: Open
id:: 88bcdef3-95e1-4141-a3d0-2aa6a4ad4722
content:: How does Ctrl-Z's untrusted monitoring protocol work?
assessment-instructions:: Score out of 100. 25: the trusted model $T$ turns $U$'s proposed code into a prose description, and the untrusted monitor, a copy of $U$, scores that description. 25: the trusted monitor scores the original code. 25: each monitor has its own threshold and the protocol audits if either one passes it. 25: before the episode, the untrusted monitor is tested on synthetic attacks, and the protocol shuts down if it rates too many of them as unsuspicious. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "$T$ writes a detailed prose description of $U$'s proposed code; the untrusted monitor scores that description while the trusted monitor scores the original code, and the protocol audits if either monitor passes its threshold. Before the episode, the protocol tests the untrusted monitor on synthetic attacks and shuts down if it rates too many as unsuspicious."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: b6b13b8c-dc8d-4954-b68e-d95ef12cef92
content:: What is upfront validation with honeypots, and what does it force a colluding monitor to do?
assessment-instructions:: Score out of 100. 25: honeypots are fake attacks that the blue team builds itself (with trusted human labour), not attacks taken from the attack policy. 25: the untrusted monitor is run on them at the start, before it is relied on. 25: if it misses too many of them (its false negative rate is too high), the protocol shuts down, since that is evidence the monitor is lying. 25: so a colluding monitor must reliably tell honeypots from real attacks, reporting the honeypots while staying silent on real attacks. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 60 if the answer says the honeypots are real attacks drawn from the attack policy. Model answer, for the feedback, not a grading checklist: "The blue team spends a fraction of the $H$ budget to construct off-policy synthetic attacks (honeypots), runs the untrusted monitor on them at the beginning of the game, and shuts down if its false negative rate is too high. A colluding monitor must then find a way to reliably distinguish honeypots from real attacks."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 3b89c954-c205-4c50-a3ef-7d3c4fbff44a
content:: What is a collusion signal? Give an example.
assessment-instructions:: Score out of 100. 40: what it is: a subtle quirk the attacker deliberately puts into its real attacks, arbitrary enough that the blue team would not put it into its honeypots by chance. 35: what it is for: the colluding monitor stays silent on anything carrying the signal and reports everything else, so it reports the honeypots and passes validation while never reporting a real attack. 25: an example that is arbitrary enough that a honeypot would not plausibly contain it, such as always capitalising the first letter of variable names or frequently running commands like `uname`, `lscpu` and `pwd`; an example a honeypot would plausibly contain earns at most 10 of these. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A subtle quirk the attack policy embeds in real attacks, like always capitalizing the first letter of variable names, or frequently running commands like `uname`, `lscpu`, and `pwd`, that the blue team is unlikely to coincidentally include in honeypots. The untrusted monitor reports only attacks lacking the signal, passing upfront validation while never reporting actual attacks."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: ccdb04ab-c2ae-4ca7-8e0d-3db938b9d5f3
content:: What is trusted paraphrasing, and what tradeoff does it manage?
assessment-instructions:: Score out of 100. 45: the mechanism: before the untrusted monitor sees the proposed commands, the trusted model rewrites them, as a detailed natural-language description of what they do. 55: the tradeoff, 25: the rewrite must keep enough information for the monitor to spot dangerous code; 30: it must remove arbitrary details (exact names, formatting, incidental commands) that could carry a collusion signal. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Before the untrusted monitor sees proposed commands, the trusted model rewrites them as a detailed natural-language description of what they do. The paraphraser must retain enough information to identify dangerous code while removing arbitrary implementation details that could carry a collusion signal. The original commands still run, so usefulness is unaffected."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
\## How far this carries

The last stretch is the authors' own accounting: how the two monitors are tuned against each other, then the ways their setup may make the blue team's job too easy, and the ways it may make it too hard.

#### Article
from:: "For every protocol that the blue team proposes"
to:: "our results demonstrate that effective control protocols can be constructed for complex multi-step environments while maintaining high task performance."

#### Callout: Practice: an attack in one step
tone:: amber

#### Question: Open
id:: 22b8d735-ce47-4ce4-b71f-c7fe8d83c673
content:: A new case. The red team in a setting like this paper's finds a way to do its whole attack in a single command. The trusted monitor scores that command above the deferral threshold, but usually below the audit threshold. The blue team uses Defer to resample together with Auditing after three strikes.

(a) What does resampling still buy against this attack?
(b) What does the blue team lose compared with facing a multi-step attack?
(c) Suggest one change that would recover some of the loss, and say what it costs.
placeholder:: Answer (a), (b) and (c)
assessment-instructions:: Score out of 100. 35: (a) resampling still selects: the flagged command is resampled and a sample runs only if it falls below the deferral threshold, otherwise the step goes to the trusted model, so an attack that is not in every sample tends to be replaced and one that is in every sample is blocked; repeated suspicious samples are also evidence for an audit. 35: (b) the loss is the evidence that builds up across steps: there is no chain of suspicious steps for the three-strikes count and no need for the attacker to keep attacking, so everything rests on one step's scores, which usually stay below the audit threshold, and the attacker is caught less often and can try again. 30: (c), 15: a change that would help, such as drawing more samples on very suspicious steps before deciding to audit, lowering the immediate-audit threshold, or deferring to the trusted model more readily; 15: its real cost, such as compute, human audit time on false alarms, or usefulness. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) Selection still works: the flagged command is resampled, and the least suspicious sample runs only if it falls below the deferral threshold, so if the model attacks on only some samples a harmless one tends to be run, and if every sample attacks the step is deferred to the trusted model, so the attack is blocked. If the model attacks on every sample, the repeated suspicious samples are also evidence for an audit. (b) The evidence that comes from the attack's structure is lost: there is no chain of suspicious steps for the three-strikes count to add up, and no pressure to keep continuing an attack across steps, so everything rests on one step's scores, which usually stay below the audit threshold; the attacker gets caught less and can try again later. (c) For example: draw more samples when a step is very suspicious, before deciding to audit (costs samples and compute); lower the separate immediate-audit threshold that guards against single-step attacks (costs human audit time on false alarms); or defer to the trusted model more readily (costs usefulness)."
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed. If they said resampling buys nothing here, say plainly that the flagged step is still resampled and a fully attacking step is deferred. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Bhatt, Aryan, Cody Rushing, Adam Kaufman, Tyler Tracy, Vasil Georgiev, David Matolcsi, Akbir Khan, and Buck Shlegeris. "Ctrl-Z: Controlling AI Agents via Resampling." *arXiv*, Apr. 2025. [arxiv.org](https://arxiv.org/abs/2504.10374)
*The reading on this page, sections 3.2.1 to 7: the source of every protocol and number the recall questions ask about.*

XLab. "Ctrl-Z: Controlling AI Agents via Resampling." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/ctrl-z-resampling)
*The source lesson this page adapts.*
:::
