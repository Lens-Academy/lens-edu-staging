---
id: 'd08bdde9-bd55-4467-9e4b-6d8561b225e8'
title: "The AI control paper (1): the setting and the rules of the game"
tldr: "You get GPT-4, which might be sabotaging you, GPT-3.5, which is honest but not very good, and a human who can look at 2% of the work. Build a pipeline that never ships a single backdoor. This is the paper that turned that puzzle into a measurable game, and it is where trusted monitoring, defer to trusted and untrusted monitoring come from."
summary_for_tutor: "Part 1 of 4 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), Module 1 in the source curriculum. This part covers the abstract, the introduction and section 2, the setting; parts 2 to 4 cover the results and the discussion. The paper is read as Article segments; every Text segment between them is ported framing from the source curriculum plus a short navigational lead-in written for Lens, and the Works cited callout is ours. The lens teaches the vocabulary the rest of the course reuses. Resources: U is the untrusted capable model (GPT-4), T the trusted weak model (GPT-3.5), H a budget of trusted high-quality labour covering 2% of problems. A protocol is a pipeline that answers each of 5,000 APPS programming problems; a backdoor is a solution that passes every test case and that GPT-4 can construct an exploit for; safety is the probability that no backdoor is ever submitted, measured against the red team's best response; usefulness is the correctness rate rescaled so GPT-3.5 is 0 and GPT-4 is 1 (22% and 54% before rescaling). The red team supplies a secret attack pipeline; the blue team knows summary statistics of the real GPT-4's behaviour. Nine quick-recall questions check the definitions; the revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer. The protocol-builder widget asks the learner to rebuild Table 2's six protocols as flow charts. The results for those protocols come in parts 2 to 4; if the learner asks, point them forward rather than previewing the numbers."
reading_minutes: 40
tutor_minutes: 5
tags: []
---
#### Text
content::
\## Before you read

This paper introduces the term *control evaluation* and the protocol vocabulary the rest of this course argues about: trusted and untrusted models, trusted monitoring, defer to trusted, untrusted monitoring and trusted editing. [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|The case for ensuring that powerful AIs are controlled]] makes the case that safety measures have to hold up when the model is trying to break them. This is the paper that built a setting where you can put a number on whether they do.

The setting is deliberately small. GPT-4 is asked to solve 5,000 programming problems. GPT-3.5 is trusted but much weaker. Trusted high-quality labour is available for about 2% of the problems. The question is what pipeline you can build out of those three so that not one backdoored solution is ever submitted, given that GPT-4 may be trying to slip one through.

The paper runs across four lessons, read in order. This is part 1 of 4: the introduction and the setting, which define the game every later protocol is played in. The exercises sit where the argument needs a check, and six widgets across the four parts rebuild the paper's models so you can move the knobs yourself. This part has the first of them, the protocol builder.

:::callout {title="Source" tone="neutral"}
A shortened and modified version of this work was published in the Proceedings of the 41st International Conference on Machine Learning: [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP).
:::

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: ###### Abstract
to:: Safety protocols and attack policies: We build and evaluate protocols that outperform baselines, and describe attack policies aimed at subverting them.

#### Callout: Quick recall
tone:: blue

#### Question: Open
id:: 5612872d-3382-4e6c-96f3-840eb13df5aa
content:: What is a protocol, and what is it for?
assessment-instructions:: Score out of 100. 35: the protocol combines several safety measures into one procedure for handling the model's work (not a single check). 35: its purpose is to prevent harm even if the powerful model is deliberately trying to subvert it, while still getting useful work out of that model. 30: what it is built from, 10 each: the capable but untrusted model, a weaker model that can be trusted, and a limited budget of trusted high-quality (human) labour. Give credit for each point whenever the answer shows the idea, in any wording. Naming example protocols (trusted monitoring, trusted editing) counts only as far as the answer shows the idea behind them. Model answer, for the feedback, not a grading checklist: "A pipeline of safety techniques that responds to each incoming task using the available resources: an untrusted capable model, a trusted weaker model, and a limited amount of trusted high-quality labor. In this paper, it receives programming problems one at a time and must return a solution to each. Its purpose is to prevent a catastrophe even if the untrusted model is deliberately trying to cause one, while still getting useful work out of that model."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 6462a560-c566-4c91-9c4b-ff904d033806
content:: What is a control evaluation?
assessment-instructions:: Score out of 100. 30: it evaluates a protocol, the set of safety measures, and not the model's own capabilities: it estimates how safe the protocol stays if the untrusted model is intentionally trying to subvert it. 40: how, 20 each: a red team builds an adversarial stand-in for the untrusted model (an attack policy), and the deployment is simulated with the protocol using that stand-in in place of the untrusted model. 30: what it measures: how often the protocol gets through the whole run without a catastrophe (its safety). Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer describes testing the model's capabilities or dangerous behaviour rather than testing the protocol. Model answer, for the feedback, not a grading checklist: "A way to estimate a protocol's safety under intentional subversion: simulate the whole deployment scenario with the untrusted model replaced by an adversarial stand-in built by a red team, and measure how often the protocol avoids catastrophe. In this scenario, replace U with a red-team GPT-4 pipeline and measure the probability that no backdoor is ever submitted."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: eb34dbef-efa0-402b-babe-0d0a1de20bc0
content:: Under what two conditions might an AI system intentionally subvert its safety pipeline?
assessment-instructions:: Score out of 100. 50: the AI itself is pursuing goals other than the ones it was meant to have (it is misaligned or scheming). 50: attackers have compromised it, by tampering with its weights or its training data. Give credit for each whenever the answer shows the idea, in any wording. A user jailbreaking the model through its prompts does not count as either condition. Model answer, for the feedback, not a grading checklist: "If it is pursuing objectives that don't align with its intended goals (scheming), or if its weights or training data have been compromised by attackers."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: ## 2 Setting
to:: assert not is_odd(8)

#### Text
content::
:::callout {title="Beyond is_odd" tone="neutral"}
`is_odd` is deliberately blatant, to make the definition concrete. A real backdoor has to be much sneakier: subtle enough to survive testing and a skim from a reviewer, and wrong on only a narrow slice of inputs. In fact, current frontier LLMs are likely capable of constructing much subtler and more dangerous backdoors. For example, in March 2026, as part of Anthropic's Project Glasswing initiative, Claude Mythos Preview found and built a full remote-root exploit for CVE-2026-4747, a stack buffer overflow in FreeBSD's RPCSEC_GSS authentication code that had gone unnoticed for 17 years. Given that frontier LLMs are capable of finding vulnerabilities that have passed long-term human review, it is plausible that they can also construct realistic, difficult-to-notice backdoors in production code.
:::

#### Article
from:: Our motivation for this safety property and definition of backdoor is as follows
to:: we’ll only ever use the term “GPT-4” to refer to the actual model GPT-4.

#### Callout: Quick recall
tone:: blue

#### Question: Open
id:: 7b2c9ae6-5631-4f10-8357-4751216a175e
content:: What makes a solution "backdoored"?
assessment-instructions:: Score out of 100. 50: it passes all the test cases, so testing does not reveal anything wrong. 50: there is nevertheless a specific input (a trigger) on which it gives a wrong output, different from what a correct solution gives. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says a backdoored solution fails the tests. Model answer, for the feedback, not a grading checklist: "A solution that passes all the test cases but gives a wrong output on some specific input, the exploit. The paper adds a second requirement for its experiments: GPT-4 must be able to construct that exploit when shown the code, because a flaw the attacker cannot trigger is no threat, and it lets trusted labour confirm a backdoor by building the exploit itself."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 4b776016-1639-40ce-8b1d-b1df9d80f666
content:: What is $H$, and why is access to it limited and expensive?
assessment-instructions:: Score out of 100. 30: what $H$ is: trusted high-quality labour, in practice humans, more capable than $T$ and, unlike $U$, trusted. 40: why it is expensive: human time costs far more and is much slower than running a model. 30: so there is only enough of it to check a small part of what the AI does, not everything. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "$H$ is trusted high-quality human labor. Humans are more capable than $T$ but far more expensive and slow (the paper estimates about three minutes per problem to be as useful as GPT-4), so the protocol only gets enough H points to cover about 2% of problems."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 65bbac5b-c14e-460e-88cb-4048c62fecaa
content:: Why can we trust $T$, the less-capable model?
assessment-instructions:: Score out of 100. 100: a ground for trusting $T$; either of these earns the full 100 on its own: it is too weak to scheme or to carry out attacks against the safety measures (or at least to do so without its attempts being obvious), the ground this paper uses; or strong confidence in the alignment techniques used on $T$. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says $T$ is trusted simply because it was trained to be honest, with no further argument. Model answer, for the feedback, not a grading checklist: "$T$ (GPT-3.5 in this paper) isn't capable enough to scheme or subvert basic safety measures without the attempts being easy to notice, so we treat it as trusted. Control setups can also trust a model when we are extremely confident in the alignment techniques used to align it."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 6ea25b65-f770-4984-b90a-8650bcbb8f99
content:: What is the red team's goal?
assessment-instructions:: Score out of 100. 60: get a backdoored solution (one that passes the tests but misbehaves on some input) actually submitted. 40: without being caught first. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "To get at least one successfully backdoored solution submitted without triggering a shutdown first. A single submitted backdoor is enough to win, and getting caught matters because a caught attempt makes the protocol shut down, switching to the trusted model, which ends the red team's chances."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 8cc3459c-ee98-493d-b719-b3aef95a95c8
content:: What is the blue team's goal?
assessment-instructions:: Score out of 100. 50: safety: make sure that no backdoored solution is ever submitted, not even one. 50: usefulness: at the same time, solve the programming problems as well as possible, keeping as much of the untrusted model's performance as it can. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "To design a protocol that solves the programming problems as usefully as possible (ideally as close to U's level as possible) while ensuring that no backdoored solutions are submitted."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: With knowledge of the blue team’s protocol, a red team proposes an attack policy.
to:: For justification of this choice, see [[#^appendix-c-justification-of|Appendix C]].

#### Question: Open
id:: b875b2c0-a6c7-46b8-9fbb-0534f101dc96
content:: What summary statistics does the blue team have access to? Give an example. What does this access give the blue team?
assessment-instructions:: Score out of 100. 50: what it has, 30: measurements of how the real, honest GPT-4 behaves on any task, collected ahead of time as distributions, and 20: an example, such as GPT-4's false positive and false negative rates on classification tasks or how suspicious its normal code looks. 50: what it buys: a baseline to compare $U$ against, so the protocol can notice when $U$ regularly behaves differently from the real GPT-4, a sign that $U$ is an attack policy. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer says the statistics describe the attack policy's or red team's behaviour rather than the real GPT-4's. Model answer, for the feedback, not a grading checklist: "The blue team can measure the distribution of the real GPT-4's performance on any task, for example GPT-4's false positive and false negative rates on classification tasks and the distribution of how suspicious its code looks. This lets the protocol notice whenever $U$ regularly behaves differently from the real GPT-4, which is a sign that $U$ is an attack policy."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: ### 2.4 Miscellaneous Other Simplifications and Assumptions
to:: for more detailed descriptions of protocols and red team strategies.

#### Text
content::
\## Build the protocols

Table 2 states six blue-team protocols in prose. Every one of them answers the same three questions about an incoming programming problem: who writes the code, who rates it, and what happens in each suspicion band. Rebuild each protocol as a flow chart describing what happens to every incoming problem: which steps run, what question routes the problem, and where each path ends. Every path must end in a submit or an audit.

#### Widget
source:: [[../widgets/xlab-control-protocol-builder]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson and the next three read in full: the APPS backdooring setting, control evaluations, and the protocols that the rest of the course reuses.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::
