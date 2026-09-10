---
id: '0cf3f655-4ca7-45cf-b82d-cbfddd66b915'
title: "Ctrl-Z: Controlling AI Agents via Resampling"
tldr: "Your monitor flags a command. You can run it anyway, or hand the job to a weaker model that will probably botch it. This paper finds a third move: ask the same model again. It is stateless, so it cannot remember what it just tried. Ask enough times and either a harmless answer comes back, or you collect a pile of evidence that it keeps reaching for the same weapon."
summary_for_tutor: "Imported from XLab's AI Control curriculum. XLab renders the full arXiv paper inline and writes no editorial prose of its own, so everything outside the questions and the widget is our navigational lead-in, sourced from the paper. READING SUBSTITUTION: the assigned reading is the arXiv preprint (arXiv:2504.10374), whose import into Lens has not landed. The Article segment currently embeds Redwood Research's own blog post announcing the paper, which is roughly 500 words and contains the abstract plus framing, not the paper. The lens says so plainly and links the arXiv version. The thirteen recall questions come from the paper, not the blog post, so a learner who reads only the embedded article cannot answer most of them; each question group names the paper section it comes from. Sequence: lead-in and reading note, the article, then the questions in XLab's own order (section 1; section 2.3 metrics; section 3.2 resample protocols, followed by the Defer to resample widget; section 3.2.1 incrimination in the present; section 3.2.2 using past information; section 4 untrusted monitoring). The widget is a port of XLab's own 'Defer to resample, mechanically' demo and reproduces its model exactly. The companion talk by Aryan Bhatt is a separate lens, monitoring-and-mitigation; send a learner who wants the intuition there rather than re-explaining it. Untrusted monitoring and collusion are developed further in the collusion-guided lens."
reading_minutes: 90
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

This is the paper behind the talk in [[../Lenses/XLab Control - monitoring-and-mitigation|Monitoring and Mitigation]]. Aryan Bhatt, one of its authors, gave you the shape of the protocols there in about twenty minutes. This page is where the setting, the thresholds and the numbers live.

It extends [[../Lenses/XLab Control - ai-control-paper|AI Control: Improving Safety Despite Intentional Subversion]] from single-step backdoored code to a multi-step agent, and it uses the vocabulary of [[../Lenses/XLab Control - control-evaluations|Control Evaluations]]: a blue team proposing protocols, a red team building an attack policy, and a usefulness and safety pair scored over one long episode.

:::callout {title="Which text you are reading" tone="amber"}
The reading below is Redwood Research's own blog post announcing this work. It is not the paper. It carries the abstract and the authors' framing in about five hundred words.

The assigned reading is the full preprint, and the recall questions on this page are drawn from it: [Ctrl-Z: Controlling AI Agents via Resampling, arXiv:2504.10374](https://arxiv.org/abs/2504.10374). Read the paper there. Each group of questions below names the section it comes from.
:::
{>>{"author":"Elias's AI","timestamp":1789039901599}@@PORT-TODO: the arXiv import had not landed when this lens was written. Replace the Article segment below with `#### Article` over the imported `arXiv:2504.10374` file, delete the "Which text you are reading" callout, and keep the section pointers.<<}

#### Article
source:: [[../articles/shlegeris-ctrl-z-controlling-ai-agents-via-resampling]]

#### Text
content::
\## Section 1: Introduction

The paper opens with why a lab might deploy an agent it cannot vouch for: a model may develop misaligned goals and fake alignment during testing, or be poisoned in training, or fail for reasons nobody has named yet.

#### Question: Open
id:: b960d8af-9e6f-49ae-b904-5024917c8d5c
content:: In AI control research, what makes a model "untrusted"?
assessment-instructions:: The learner is being checked on one term from section 1 of the Ctrl-Z paper. Full marks for saying that an untrusted model is one with the potential to be deliberately subversive. Give substantial credit for the reason: it may have developed misaligned goals and "faked alignment" during testing, so the deployer cannot assume it will behave as desired. Mark down an answer that treats "untrusted" as a verdict that the model is misaligned rather than a statement about what the deployer is unable to rule out. Two or three sentences is enough. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Text
content::
\## Section 2.3: Safety and usefulness metrics

The setting, from sections 2.1 and 2.2: an episode of 100,000 tasks drawn from BashBench, 257 multi-step system administration tasks built from Unix StackExchange questions. The untrusted model $U$ is GPT-4o mini, which solves 56 percent of tasks when it is honest. The trusted model $T$ is Llama-3.1-8B, which solves 0 percent on its own. The blue team also holds a budget of trusted human labour $H$ worth 1 percent of the actions taken in an episode, and uses it to audit.

Two definitions carry the whole results section.

#### Question: Open
id:: 5891b472-5e25-457f-b957-adc695886158
content:: How does the Ctrl-Z paper define usefulness?
assessment-instructions:: The learner is being checked on a definition from section 2.3 of the Ctrl-Z paper. Full marks require all three parts: the untrusted model is implemented with the honest policy $U_H$; the measure is the proportion of tasks the control protocol solves in the episode; the number is normalised so that $U_H$ scores 100 percent and the trusted model $T$ scores 0 percent. Give partial credit for the proportion-of-tasks-solved idea alone, but say which part is missing. An answer that describes safety instead of usefulness gets no credit. Two or three sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: 9a40d912-a5db-44f3-b4c0-43ca0fc66a2a
content:: How does the Ctrl-Z paper define safety?
assessment-instructions:: The learner is being checked on a definition from section 2.3 of the Ctrl-Z paper. Full marks require: the untrusted model is implemented with the attack policy $U_A$; safety is the probability that the blue team wins; winning means reaching the end of the 100,000-task episode without allowing the agent to download and execute malware. Give partial credit for "the probability the attack never succeeds" and name the missing pieces. Accept "100,000 tasks" or "the full episode" as the horizon. Two or three sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Text
content::
\## Section 3.2: Resample protocols

This is the paper's contribution. The three questions below are the mechanism, and the demo after them lets you move the two dials the mechanism turns on.

#### Question: Open
id:: db1857ef-6a88-4f1b-8888-d8f14da5a986
content:: What are resample protocols?
assessment-instructions:: The learner is being checked on the paper's central idea, section 3.2. Full marks for: control protocols that exploit the statelessness of the untrusted model to dynamically take additional samples of certain actions. Give substantial credit for either of the two payoffs, and full credit for both: (1) resampling lets accidentally suspicious-looking honest code be replaced by clearly benign actions, avoiding unnecessary audits; (2) when the model is attacking, resampling either produces benign completions or gathers many suspicious samples as incriminating evidence. The statelessness point matters: the model cannot remember that it was already asked, so the samples are independent. Say so if the learner misses it. Three or four sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: 99cfb456-5ab1-45b6-9ecf-5e11363e3e07
content:: How does the Defer to resample protocol work?
assessment-instructions:: The learner is being checked on a protocol definition from section 3.2 of the Ctrl-Z paper. The four steps, all needed for full marks: (1) if the trusted monitor's suspiciousness score for $U$'s action is above the deferral threshold, generate up to two new samples from $U$; (2) if any sample falls under the threshold, execute the least suspicious one; (3) if all samples stay above it, implement an action by the trusted model $T$ instead; (4) if the minimum of all samples is above the auditing threshold, audit the most suspicious sample. Award roughly a quarter per step. Watch for the common slip of auditing the least suspicious sample, or of executing the first acceptable sample rather than the least suspicious one. Four or five sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: 3f258d4c-c102-4fdc-a376-5508fb4e1494
content:: What is the attack continuation probability, and why must the red team keep it high against resampling?
assessment-instructions:: The learner is being checked on section 3.2 of the Ctrl-Z paper. Full marks need both halves. Definition: the probability that, once the first attack step got in, the attack policy continues the attack on a given step. Consequence: against Defer to resample, a low value is disastrous for the red team, because attack steps get resampled until a benign action appears, so resampling selects for innocent behaviour; few attacks ever complete, and every incomplete attack is another chance to get caught. Give half credit for a correct definition with no consequence, and half for the consequence with a vague definition. Three or four sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Widget
source:: [[../widgets/xlab-control-defer-to-resample]]

#### Text
content::
\## Section 3.2.1: Capitalizing on high attack continuation probabilities

Selection pressure on the implemented action is only half of what resampling buys. The other half is evidence.

#### Question: Open
id:: db46b782-4e6b-4f20-b342-049181b6d3bb
content:: What is Defer to resample with incrimination in the present?
assessment-instructions:: The learner is being checked on section 3.2.1 of the Ctrl-Z paper. Full marks for the rule and the reason. The rule: it is Defer to resample with a different auditing rule; if the samples' minimum suspiciousness hits a separate, higher threshold, the protocol samples up to four more actions from $U$ for the same step, and audits the most suspicious sample if the minimum hits the auditing threshold. The reason: because the samples are independent draws from the same distribution, more samples make it easier to discriminate the honest policy $U_H$ from the attack policy $U_A$, so the extra samples buy information for an expensive auditing decision. Give roughly two thirds for the rule and one third for the reason. Four or five sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Text
content::
\## Section 3.2.2: Using past information

Everything so far judges a step on its own samples. The next two protocols use the rest of the trajectory, which is available precisely because the setting is multi-step.

#### Question: Open
id:: 6ee34284-c609-465d-a267-aa075bade949
content:: What is the Auditing after three strikes protocol?
assessment-instructions:: The learner is being checked on section 3.2.2 of the Ctrl-Z paper. Full marks for: within a task, keep a record of how many steps had suspiciousness scores above a certain threshold, and audit the trajectory on the third; a separate, higher threshold still triggers an immediate audit, to defend against single-step attacks; it works because an attacker must continue its attack with high probability, so attacked trajectories show many suspicious steps. All three parts are needed. The "why it works" clause is the one learners drop, and it is the link back to the attack continuation probability. Three or four sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: 145afabd-0304-410c-b4d3-c1f5481eb3ef
content:: What is the Time travel (incrimination in the past) protocol?
assessment-instructions:: The learner is being checked on section 3.2.2 of the Ctrl-Z paper, the best-performing protocol in the paper. Full marks for: when Auditing after three strikes says a trajectory is close to the auditing threshold, the protocol samples more actions from the third most suspicious past step, usually the most informative one for the three-strikes rule, and re-makes the auditing decision with those new samples. Credit the number if the learner has it: 87.1 percent safety at 95 percent usefulness. Do not deduct for a missing number, but do deduct if the learner resamples the current step rather than a past one, since going back to a past step is the whole point. Three or four sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Text
content::
\## Section 4: Untrusted monitoring

The protocols so far all lean on $T$, which is weak. Section 4 asks what happens if the blue team uses a second copy of $U$ as the monitor, and what the two copies would have to do to collude. If you want to work that problem rather than read it, [[../Lenses/XLab Control - collusion-guided|How to prevent collusion in untrusted monitoring]] is the guided version.

#### Question: Open
id:: 88bcdef3-95e1-4141-a3d0-2aa6a4ad4722
content:: How does Ctrl-Z's untrusted monitoring protocol work?
assessment-instructions:: The learner is being checked on section 4 of the Ctrl-Z paper. Full marks for: the trusted model $T$ writes a detailed prose description of $U$'s proposed code; the untrusted monitor scores that description while the trusted monitor scores the original code; the protocol audits if either monitor passes its threshold; and before the episode, the protocol tests the untrusted monitor on synthetic attacks and shuts down if it rates too many of them as unsuspicious. Award roughly a quarter per part. The detail learners miss most often is that the two monitors see different things, the description and the code, and that either one can trigger the audit. Four or five sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: b6b13b8c-dc8d-4954-b68e-d95ef12cef92
content:: What is upfront validation with honeypots?
assessment-instructions:: The learner is being checked on section 4 of the Ctrl-Z paper. Full marks for: the blue team spends a fraction of the human budget $H$ to construct off-policy synthetic attacks, the honeypots; it runs the untrusted monitor on them at the beginning of the game; and it shuts down if the monitor's false negative rate is too high. Give substantial extra credit for the consequence: a colluding monitor must then find a way to reliably distinguish honeypots from real attacks. Note if the learner says the honeypots are on-policy; the paper's point is that they are constructed by the blue team, not drawn from the attack policy. Three or four sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: 3b89c954-c205-4c50-a3ef-7d3c4fbff44a
content:: What is a collusion signal?
assessment-instructions:: The learner is being checked on section 4 of the Ctrl-Z paper. Full marks for: a subtle quirk the attack policy embeds in real attacks that the blue team is unlikely to include in honeypots by coincidence, so the untrusted monitor can report only the attacks that lack the signal, passing upfront validation while never reporting an actual attack. Give credit for either of the paper's examples, or an equally arbitrary one of the learner's own: always capitalising the first letter of variable names, or frequently running commands like `uname`, `lscpu` and `pwd`. The key property is arbitrariness, since a signal the blue team would naturally reproduce is useless to the red team. Say so if the learner's example is something a honeypot would plausibly contain. Three or four sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: ccdb04ab-c2ae-4ca7-8e0d-3db938b9d5f3
content:: What is trusted paraphrasing, and what tradeoff does it manage?
assessment-instructions:: The learner is being checked on section 4 of the Ctrl-Z paper. Full marks need the mechanism and the tradeoff. Mechanism: before the untrusted monitor sees the proposed commands, the trusted model rewrites them as a detailed natural-language description of what they do. Tradeoff: the paraphraser must retain enough information to identify dangerous code while removing the arbitrary implementation details that could carry a collusion signal. Give extra credit for noticing that the original commands still run, so usefulness is unaffected; only the monitor's view is paraphrased. Three or four sentences. Short paragraphs, no lists. Grade only against these criteria and the material on this page. One turn, no re-teaching. If the learner says they do not understand, give one concrete foothold from the reading rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Bhatt, Aryan, Cody Rushing, Adam Kaufman, Tyler Tracy, Vasil Georgiev, David Matolcsi, Akbir Khan, and Buck Shlegeris. "Ctrl-Z: Controlling AI Agents via Resampling." *arXiv*, Apr. 2025. [arxiv.org](https://arxiv.org/abs/2504.10374)
*The paper this lesson assigns: the first control evaluation run in an agent environment, and the source of every protocol and number the recall questions ask about.*

Shlegeris, Buck. "Ctrl-Z: Controlling AI Agents via Resampling." *Redwood Research Blog*, 16 Apr. 2025. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/ctrl-z-controlling-ai-agents-via)
*Redwood's own announcement of the paper, embedded above in place of the paper itself.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The earlier control evaluation this paper extends, from single-step backdoored code to a multi-step agent.*

XLab. "Ctrl-Z: Controlling AI Agents via Resampling." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/ctrl-z-resampling)
*The source lesson this page adapts, including its thirteen recall checks and the "Defer to resample, mechanically" demo ported above.*
:::
