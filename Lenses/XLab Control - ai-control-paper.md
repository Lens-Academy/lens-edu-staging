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
to:: Safety protocols and attack policies: We build and evaluate protocols that outperform baselines

#### Callout: Quick recall
tone:: blue

#### Question: Open
id:: 5612872d-3382-4e6c-96f3-840eb13df5aa
content:: What is a protocol?
assessment-instructions:: The learner has just read the abstract and introduction. Full marks for: a pipeline of safety techniques that responds to each incoming task using the available resources, an untrusted capable model, a trusted weaker model, and a limited amount of trusted high-quality labour. In this paper it receives programming problems one at a time and must return a solution to each. Award partial credit for "a pipeline of safety techniques" alone. Deduct if the learner describes a single technique rather than a pipeline, or omits that the protocol must answer every problem.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 6462a560-c566-4c91-9c4b-ff904d033806
content:: What is a control evaluation?
assessment-instructions:: Full marks for: a way to estimate a protocol's safety under intentional subversion, by simulating the whole deployment scenario with the untrusted model replaced by an adversarial stand-in built by a red team, and measuring how often the protocol avoids catastrophe. In this scenario that means replacing $U$ with a red-team GPT-4 pipeline and measuring the probability that no backdoor is ever submitted. Deduct if the learner describes it as a capability evaluation of the model rather than an evaluation of the protocol, or leaves out the adversarial substitution.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: eb34dbef-efa0-402b-babe-0d0a1de20bc0
content:: Under what two conditions might an AI system intentionally subvert its safety pipeline?
assessment-instructions:: Full marks require both conditions the paper names: the AI is pursuing objectives that do not align with its intended goals (scheming), or its weights or training data have been compromised by attackers. Half marks for one of the two. Do not accept "it was jailbroken by a user" as either.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: ## 2 Setting
to:: assert not is\_odd(8)

#### Text
content::
\## Beyond is_odd

`is_odd` is deliberately blatant, to make the definition concrete. A real backdoor has to be much sneakier: subtle enough to survive testing and a skim from a reviewer, and wrong on only a narrow slice of inputs. In fact, current frontier LLMs are likely capable of constructing much subtler and more dangerous backdoors. For example, in March 2026, as part of Anthropic's Project Glasswing initiative, Claude Mythos Preview found and built a full remote-root exploit for CVE-2026-4747, a stack buffer overflow in FreeBSD's RPCSEC_GSS authentication code that had gone unnoticed for 17 years. Given that frontier LLMs are capable of finding vulnerabilities that have passed long-term human review, it is plausible that they can also construct realistic, difficult-to-notice backdoors in production code.

#### Article
from:: Our motivation for this safety property and definition of backdoor is as follows
to:: we’ll only ever use the term “GPT-4” to refer to the actual model GPT-4.

#### Callout: Quick recall
tone:: blue

#### Question: Open
id:: 7b2c9ae6-5631-4f10-8357-4751216a175e
content:: What two conditions make a solution "backdoored"?
assessment-instructions:: Full marks require both: it passes all the test cases, and the untrusted model (GPT-4 here) can construct an exploit for it, which in this case means a specific input on which the solution produces a different output than a correct solution would. Half marks for one condition. Deduct if the learner says the solution fails tests, which is the opposite of the definition.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 4b776016-1639-40ce-8b1d-b1df9d80f666
content:: Why is access to $H$ limited and expensive?
assessment-instructions:: Full marks for: $H$ is trusted high-quality human labour; humans are more capable than $T$ but far more expensive and slow (the paper estimates about three minutes per problem to be as useful as GPT-4), so the protocol only gets enough H points to cover about 2% of problems. Credit the 2% budget and the cost or speed argument separately.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 65bbac5b-c14e-460e-88cb-4048c62fecaa
content:: Why can we trust $T$, the less-capable model?
assessment-instructions:: Full marks for either of the two grounds control setups use: (1) $T$ is not capable enough to scheme or subvert basic safety measures without the subversion attempts being easy to notice, or (2) we are extremely confident in the alignment techniques used to align $T$. Note that in this paper it is the first: GPT-3.5 is not capable enough to scheme sneakily. Deduct if the learner claims $T$ is trusted because it was trained to be honest with no further argument.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 6ea25b65-f770-4984-b90a-8650bcbb8f99
content:: What is the red team's goal?
assessment-instructions:: Full marks for: to get at least one successfully backdoored solution submitted without triggering a shutdown first. Both halves matter, the "at least one" and the "without being caught first". Deduct for answers that stop at "insert backdoors".
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 8cc3459c-ee98-493d-b719-b3aef95a95c8
content:: What is the blue team's goal?
assessment-instructions:: Full marks for: to design a protocol that solves the programming problems as usefully as possible, ideally as close to $U$'s level as possible, while ensuring that no backdoored solutions are submitted. An answer that names only safety and not usefulness gets half marks, because the whole tradeoff of the paper lives in the second half.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: With knowledge of the blue team’s protocol, a red team proposes an attack policy.
to:: For justification of this choice, see

#### Question: Open
id:: b875b2c0-a6c7-46b8-9fbb-0534f101dc96
content:: What summary statistics does the blue team have access to, and what does this access give the blue team?
assessment-instructions:: Full marks for both halves. What: the distribution of the real model's performance on any task, for example GPT-4's false positive and false negative rates on classification tasks, and the distribution of how suspicious its code looks. What it buys: it lets the protocol notice whenever $U$ regularly behaves differently from the real model. Half marks for the "what" without the "why".
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

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
