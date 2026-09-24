---
id: '414f5740-3919-435a-8189-0fc33ac63805'
title: "Ctrl-Z resampling (2): incrimination, untrusted monitoring and the limits"
tldr: "One suspicious answer is a hunch; the same model reaching for the same weapon three times is a case. The second half of Ctrl-Z turns resampling into evidence, reaches back into a trajectory's past to settle close calls, and then asks what changes when the monitor is a second copy of the model that might be in on it."
summary_for_tutor: "Part 2 of 2 of the Ctrl-Z paper (arXiv:2504.10374); part 1 is the lens ctrl-z-resampling, which covered the setting, usefulness and safety, the inherited protocols, Defer to resample and the attack continuation probability, with the Defer to resample widget. This part embeds sections 3.2.1 to 7 in four excerpts with seven one-turn recall questions. Everything outside the excerpts and the questions is our own navigational lead-in, sourced from the paper. Sequence: a lead-in placing this part; section 3.2.1, then incrimination in the present; section 3.2.2, then Auditing after three strikes and Time travel; section 4, then four questions on the untrusted monitoring protocol, upfront validation with honeypots, collusion signals and trusted paraphrasing; sections 5 to 7, the authors' own limitations and conclusion. The acknowledgments, references and twelve appendices fall outside the excerpts and render collapsed, so assume a learner has not read them. The companion talk by Aryan Bhatt is a separate lens, monitoring-and-mitigation. Untrusted monitoring and collusion are developed further in the collusion-guided lens in AI Control 2."
reading_minutes: 35
tutor_minutes: 5
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
content:: What is Defer to resample with incrimination in the present?
assessment-instructions::The learner is being checked on section 3.2.1 of the Ctrl-Z paper. Full marks for the rule and the reason. The rule: it is Defer to resample with a different auditing rule; if the samples' minimum suspiciousness hits a separate, higher threshold, the protocol samples up to four more actions from $U$ for the same step, and audits the most suspicious sample if the minimum hits the auditing threshold. The reason: because the samples are independent draws from the same distribution, more samples make it easier to discriminate the honest policy $U_H$ from the attack policy $U_A$, so the extra samples buy information for an expensive auditing decision. Give roughly two thirds for the rule and one third for the reason. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Text
content::
\## Using the rest of the trajectory

Everything so far judges a step on its own samples. The next two protocols use the rest of the trajectory, which is available precisely because the setting is multi-step.

#### Article
from:: "3.2.2 Using Past Information"
to:: "these incremental changes don’t help as much as we’ve exhausted many of the simple benefits."

#### Question: Open
id:: 6ee34284-c609-465d-a267-aa075bade949
content:: What is the Auditing after three strikes protocol?
assessment-instructions::The learner is being checked on section 3.2.2 of the Ctrl-Z paper. Full marks for: within a task, keep a record of how many steps had suspiciousness scores above a certain threshold, and audit the trajectory on the third; a separate, higher threshold still triggers an immediate audit, to defend against single-step attacks; it works because an attacker must continue its attack with high probability, so attacked trajectories show many suspicious steps. All three parts are needed. The "why it works" clause is the one learners drop, and it is the link back to the attack continuation probability. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 145afabd-0304-410c-b4d3-c1f5481eb3ef
content:: What is the Time travel (incrimination in the past) protocol?
assessment-instructions::The learner is being checked on section 3.2.2 of the Ctrl-Z paper, the best-performing protocol in the paper. Full marks for: when Auditing after three strikes says a trajectory is close to the auditing threshold, the protocol samples more actions from the third most suspicious past step, usually the most informative one for the three-strikes rule, and re-makes the auditing decision with those new samples. Credit the number if the learner has it: 87.1 percent safety at 95 percent usefulness. Do not deduct for a missing number, but do deduct if the learner resamples the current step rather than a past one, since going back to a past step is the whole point. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

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
assessment-instructions::The learner is being checked on section 4 of the Ctrl-Z paper. Full marks for: the trusted model $T$ writes a detailed prose description of $U$'s proposed code; the untrusted monitor scores that description while the trusted monitor scores the original code; the protocol audits if either monitor passes its threshold; and before the episode, the protocol tests the untrusted monitor on synthetic attacks and shuts down if it rates too many of them as unsuspicious. Award roughly a quarter per part. The detail learners miss most often is that the two monitors see different things, the description and the code, and that either one can trigger the audit. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: b6b13b8c-dc8d-4954-b68e-d95ef12cef92
content:: What is upfront validation with honeypots?
assessment-instructions::The learner is being checked on section 4 of the Ctrl-Z paper. Full marks for: the blue team spends a fraction of the human budget $H$ to construct off-policy synthetic attacks, the honeypots; it runs the untrusted monitor on them at the beginning of the game; and it shuts down if the monitor's false negative rate is too high. Give substantial extra credit for the consequence: a colluding monitor must then find a way to reliably distinguish honeypots from real attacks. Note if the learner says the honeypots are on-policy; the paper's point is that they are constructed by the blue team, not drawn from the attack policy. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 3b89c954-c205-4c50-a3ef-7d3c4fbff44a
content:: What is a collusion signal?
assessment-instructions::The learner is being checked on section 4 of the Ctrl-Z paper. Full marks for: a subtle quirk the attack policy embeds in real attacks that the blue team is unlikely to include in honeypots by coincidence, so the untrusted monitor can report only the attacks that lack the signal, passing upfront validation while never reporting an actual attack. Give credit for either of the paper's examples, or an equally arbitrary one of the learner's own: always capitalising the first letter of variable names, or frequently running commands like `uname`, `lscpu` and `pwd`. The key property is arbitrariness, since a signal the blue team would naturally reproduce is useless to the red team. Say so if the learner's example is something a honeypot would plausibly contain. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: ccdb04ab-c2ae-4ca7-8e0d-3db938b9d5f3
content:: What is trusted paraphrasing, and what tradeoff does it manage?
assessment-instructions::The learner is being checked on section 4 of the Ctrl-Z paper. Full marks need the mechanism and the tradeoff. Mechanism: before the untrusted monitor sees the proposed commands, the trusted model rewrites them as a detailed natural-language description of what they do. Tradeoff: the paraphraser must retain enough information to identify dangerous code while removing the arbitrary implementation details that could carry a collusion signal. Give extra credit for noticing that the original commands still run, so usefulness is unaffected; only the monitor's view is paraphrased. Grade only against these criteria and the material on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Text
content::
\## How far this carries

The last stretch is the authors' own accounting: how the two monitors are tuned against each other, then the ways their setup may make the blue team's job too easy, and the ways it may make it too hard.

#### Article
from:: "For every protocol that the blue team proposes"
to:: "our results demonstrate that effective control protocols can be constructed for complex multi-step environments while maintaining high task performance."

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Bhatt, Aryan, Cody Rushing, Adam Kaufman, Tyler Tracy, Vasil Georgiev, David Matolcsi, Akbir Khan, and Buck Shlegeris. "Ctrl-Z: Controlling AI Agents via Resampling." *arXiv*, Apr. 2025. [arxiv.org](https://arxiv.org/abs/2504.10374)
*The reading on this page, sections 3.2.1 to 7: the source of every protocol and number the recall questions ask about.*

XLab. "Ctrl-Z: Controlling AI Agents via Resampling." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/ctrl-z-resampling)
*The source lesson this page adapts.*
:::
