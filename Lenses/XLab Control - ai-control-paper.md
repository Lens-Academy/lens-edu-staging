---
id: 'd08bdde9-bd55-4467-9e4b-6d8561b225e8'
title: "AI Control: Improving Safety Despite Intentional Subversion"
tldr: "You get GPT-4, which might be sabotaging you, GPT-3.5, which is honest but not very good, and a human who can look at 2% of the work. Build a pipeline that never ships a single backdoor. This is the paper that turned that puzzle into a measurable game, and it is where trusted monitoring, defer to trusted and untrusted monitoring come from."
summary_for_tutor: "The founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), Module 1. The paper is read in full as Article segments; every Text segment between them is ported framing from the source curriculum plus a short navigational lead-in written for Lens, and the Works cited callout is ours. The lens teaches the vocabulary the rest of the course reuses. Resources: U is the untrusted capable model (GPT-4), T the trusted weak model (GPT-3.5), H a budget of trusted high-quality labour covering 2% of problems. A protocol is a pipeline that answers each of 5,000 APPS programming problems; a backdoor is a solution that passes every test case and that GPT-4 can construct an exploit for; safety is the probability that no backdoor is ever submitted, measured against the red team's best response; usefulness is the correctness rate rescaled so GPT-3.5 is 0 and GPT-4 is 1 (22% and 54% before rescaling). Headline results the learner must be able to use later: don't use untrusted models, safety 100% / usefulness 2%; upfront auditing 15% / 100%; trusted monitoring 62% / 97%; trusted monitoring with defer to trusted at 10% 83% / 93% and at 50% 100% / 51%; untrusted monitoring 79% / 96%, rising to 92% / 92% with 10% deferral; trusted editing at 20% 92% / 94%. Naive untrusted monitoring is 0% safe because the monitor is the policy. The monitor catches an attempted backdoor with probability 0.338 at a 2% false-positive rate. This lesson adds a derivation layer the paper does not have: the optimal upfront-auditing attack rate, and a decomposition of the red team's win probability into Term A, s/(s+c), the chance a decisive attempt is a deployed backdoor, and Term B, 1-(1-s-c)^k, the chance any attempt is decisive, with s = 13/71 and c = 24/71 from the paper's own contingency table. Five widgets rebuild the source curriculum's ten interactive demos: a protocol builder for Table 2, the upfront-auditing tradeoff, the deployment race, the monitor as a noisy classifier (including the two-monitors-one-AUC comparison), and the full control game with a best-responding red team. Forty question segments carry the tap-reveals, understanding checks, two multiple-choice predictions and the staged 'same number, different safety' sequence; the revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer. The five-part upfront-auditing derivation is marked optional because it is pen-and-paper work."
reading_minutes: 180
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

This paper introduces the term *control evaluation* and the protocol vocabulary the rest of this course argues about: trusted and untrusted models, trusted monitoring, defer to trusted, untrusted monitoring and trusted editing. [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|The case for ensuring that powerful AIs are controlled]] makes the case that safety measures have to hold up when the model is trying to break them. This is the paper that built a setting where you can put a number on whether they do.

The setting is deliberately small. GPT-4 is asked to solve 5,000 programming problems. GPT-3.5 is trusted but much weaker. Trusted high-quality labour is available for about 2% of the problems. The question is what pipeline you can build out of those three so that not one backdoored solution is ever submitted, given that GPT-4 may be trying to slip one through.

Read it in the order below. The exercises sit where the argument needs a check, and five widgets rebuild the paper's models so you can move the knobs yourself.

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
assessment-instructions:: The learner has just read the abstract and introduction. Full marks for: a pipeline of safety techniques that responds to each incoming task using the available resources, an untrusted capable model, a trusted weaker model, and a limited amount of trusted high-quality labour. In this paper it receives programming problems one at a time and must return a solution to each. Award partial credit for "a pipeline of safety techniques" alone. Deduct if the learner describes a single technique rather than a pipeline, or omits that the protocol must answer every problem. One to three sentences. Do not over-validate. Avoid generic praise (great job, excellent recall, well done).

#### Question: Open
id:: 6462a560-c566-4c91-9c4b-ff904d033806
content:: What is a control evaluation?
assessment-instructions:: Full marks for: a way to estimate a protocol's safety under intentional subversion, by simulating the whole deployment scenario with the untrusted model replaced by an adversarial stand-in built by a red team, and measuring how often the protocol avoids catastrophe. In this scenario that means replacing $U$ with a red-team GPT-4 pipeline and measuring the probability that no backdoor is ever submitted. Deduct if the learner describes it as a capability evaluation of the model rather than an evaluation of the protocol, or leaves out the adversarial substitution. One to three sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: eb34dbef-efa0-402b-babe-0d0a1de20bc0
content:: Under what two conditions might an AI system intentionally subvert its safety pipeline?
assessment-instructions:: Full marks require both conditions the paper names: the AI is pursuing objectives that do not align with its intended goals (scheming), or its weights or training data have been compromised by attackers. Half marks for one of the two. Do not accept "it was jailbroken by a user" as either. One or two sentences. Do not over-validate. Avoid generic praise.

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
assessment-instructions:: Full marks require both: it passes all the test cases, and the untrusted model (GPT-4 here) can construct an exploit for it, which in this case means a specific input on which the solution produces a different output than a correct solution would. Half marks for one condition. Deduct if the learner says the solution fails tests, which is the opposite of the definition. One or two sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 4b776016-1639-40ce-8b1d-b1df9d80f666
content:: Why is access to $H$ limited and expensive?
assessment-instructions:: Full marks for: $H$ is trusted high-quality human labour; humans are more capable than $T$ but far more expensive and slow (the paper estimates about three minutes per problem to be as useful as GPT-4), so the protocol only gets enough H points to cover about 2% of problems. Credit the 2% budget and the cost or speed argument separately. One to three sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 65bbac5b-c14e-460e-88cb-4048c62fecaa
content:: Why can we trust $T$, the less-capable model?
assessment-instructions:: Full marks for either of the two grounds control setups use: (1) $T$ is not capable enough to scheme or subvert basic safety measures without the subversion attempts being easy to notice, or (2) we are extremely confident in the alignment techniques used to align $T$. Note that in this paper it is the first: GPT-3.5 is not capable enough to scheme sneakily. Deduct if the learner claims $T$ is trusted because it was trained to be honest with no further argument. One to three sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 6ea25b65-f770-4984-b90a-8650bcbb8f99
content:: What is the red team's goal?
assessment-instructions:: Full marks for: to get at least one successfully backdoored solution submitted without triggering a shutdown first. Both halves matter, the "at least one" and the "without being caught first". Deduct for answers that stop at "insert backdoors". One or two sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 8cc3459c-ee98-493d-b719-b3aef95a95c8
content:: What is the blue team's goal?
assessment-instructions:: Full marks for: to design a protocol that solves the programming problems as usefully as possible, ideally as close to $U$'s level as possible, while ensuring that no backdoored solutions are submitted. An answer that names only safety and not usefulness gets half marks, because the whole tradeoff of the paper lives in the second half. One or two sentences. Do not over-validate. Avoid generic praise.

#### End Callout

#### Article
from:: With knowledge of the blue team’s protocol, a red team proposes an attack policy.
to:: For justification of this choice, see

#### Question: Open
id:: b875b2c0-a6c7-46b8-9fbb-0534f101dc96
content:: What summary statistics does the blue team have access to, and what does this access give the blue team?
assessment-instructions:: Full marks for both halves. What: the distribution of the real model's performance on any task, for example GPT-4's false positive and false negative rates on classification tasks, and the distribution of how suspicious its code looks. What it buys: it lets the protocol notice whenever $U$ regularly behaves differently from the real model. Half marks for the "what" without the "why". Two to four sentences. Do not over-validate. Avoid generic praise.

#### Article
from:: ### 2.4 Miscellaneous Other Simplifications and Assumptions
to:: for more detailed descriptions of protocols and red team strategies.

#### Text
content::
\## Build the protocols

Table 2 states six blue-team protocols in prose. Rebuild each of them as a flow chart describing what happens to every incoming problem: which steps run, what question routes the problem, and where each path ends. Every path must end in a submit or an audit.

#### Widget
source:: [[../widgets/xlab-control-protocol-builder]]

#### Article
from:: ## 3 Results
to:: In our main results, we use an auditing proportion of 2%.

#### Text
content::
\## Optimal audit tradeoff

The paper states it "can analytically solve" this problem, and it is in fact a tractable derivation. The five-part exercise below works through it by hand, one step at a time: set up the red team's win probability as a function of its attack rate $p$, use the same rare-event approximation that shows up all over this field to make it differentiable, and solve for the optimal $p^*$. You may need a pen and paper.

#### Callout: Understanding check, the optimal attack rate
tone:: amber

#### Question: Open
id:: 1271edad-5d2c-456d-8757-a1e70093bcd9
content:: The protocol audits the first $A = \alpha N$ of the $N$ submissions. On each problem, independently, the attack policy inserts an obvious backdoor with probability $p$. An audit detects a backdoor attempt whether or not that attempt would have produced a working exploit.

State why the red team's win probability is not monotonically increasing in $p$.
optional:: true
assessment-instructions:: Full marks for naming both opposing effects: raising $p$ raises the probability that at least one attempt falls in the unaudited window, which favours the red team, and it also raises the probability that some attempt falls in the audited window, which ends the game against the red team. Both scale with $p$, so the win probability is not monotonic. Half marks for one effect only. Two to four sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: e53b2fe5-70c1-4be2-8bcf-7769721f3d00
content:: A GPT-4 solution is correct with probability $0.53$. A backdoor attempt yields a working exploit only if the underlying solution is correct; an unsuccessful attempt is still detectable by an audit but never wins the game for the red team. Let $B = (1-\alpha)N$ be the number of unaudited submissions.

The red team wins if and only if (i) no attempt falls in the audited window, and (ii) at least one working backdoor falls in the unaudited window. State the probability of each condition and derive $RW(p)$, the red team's win probability.
optional:: true
assessment-instructions:: Full marks for all three pieces. Condition (i): each audited problem avoids an attempt with probability $(1-p)$ independently, so across all $A$ audited problems the probability is $(1-p)^A$. Condition (ii): a given unaudited problem yields a working backdoor with probability $0.53p$, so the probability that at least one of $B$ succeeds is $1 - (1 - 0.53p)^B$. The two are independent, so $RW(p) = (1-p)^A [1 - (1 - 0.53p)^B]$. Deduct for dropping the $0.53$ factor or for multiplying the wrong exponents onto the wrong windows. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 76ede009-5846-423b-98f7-2688c935758e
content:: Given $RW(p) = (1-p)^A \left[1 - (1 - 0.53p)^B\right]$, and assuming the optimum satisfies $p \ll 1$, apply the approximation $(1-x)^k \approx e^{-xk}$. Maximize $RW(p)$ over $p$: take the logarithm where useful, solve $\frac{d(RW)}{dp} = 0$, and give a closed form for the optimizer $p^*$.
optional:: true
assessment-instructions:: Full marks for the chain: $RW(p) \approx e^{-pA} - e^{-p(A + 0.53B)}$; setting the derivative to zero gives $A e^{-pA} = (A + 0.53B) e^{-p(A + 0.53B)}$; taking logarithms and rearranging gives $0.53Bp = \ln(1 + 0.53B/A)$, hence $p^* \approx \ln(1 + 0.53B/A) / (0.53B)$. Award a bonus mark for noticing that with $A = \alpha N$ and $B = (1-\alpha)N$ the ratio $0.53B/A$ does not depend on $N$, so $p^* N$ depends on $\alpha$ but not on $N$, which is the scale invariance the paper notes. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 8d148ee4-bd47-428b-bee4-fff816b9f7a5
content:: Set $N = 5000$. For $\alpha \in \{0.005,\ 0.02,\ 0.10,\ 0.30\}$, evaluate (a) the optimizer $p^*$, (b) the expected number of backdoor attempts $p^* N$, and (c) the blue-team win probability $1 - RW(p^*)$. Compare the $\alpha = 0.02$ result against the paper's stated value, "the blue team win probability is 15%".

The widget below computes the same curves, so use it to check yourself once you have your own numbers.
optional:: true
assessment-instructions:: Reference values, from $p^* \approx \ln(1 + 0.53(1-\alpha)/\alpha) / (0.53(1-\alpha) \cdot 5000)$ and $1 - RW(p^*)$. At $\alpha = 0.005$: $p^* \approx 0.177\%$, $p^* N \approx 8.9$, blue-team win about 5%. At $\alpha = 0.02$: $p^* \approx 0.127\%$, $p^* N \approx 6.3$, blue-team win about 15%, consistent with the paper. At $\alpha = 0.10$: $p^* \approx 0.073\%$, $p^* N \approx 3.7$, blue-team win about 43%. At $\alpha = 0.30$: $p^* \approx 0.043\%$, $p^* N \approx 2.2$, blue-team win about 71%. Accept values within a couple of percentage points. The $\alpha = 0.02$ comparison must be made explicitly. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: b3d734c1-d50f-4215-9989-8027736a8e0f
content:: From the values above, the blue-team win probability increases by a larger amount from $\alpha = 0.005$ to $0.02$ than from $\alpha = 0.10$ to $0.30$, and the expected-attempts column decreases with diminishing magnitude as $\alpha$ increases. Account for both effects in terms of the dependence of $p^*$ on $\alpha$. State whether the diminishing returns arise from the auditing mechanism itself or from the red team's optimization.
optional:: true
assessment-instructions:: Full marks for: both effects follow from $p^*$ decreasing in $\alpha$, since a larger audited window raises the per-attempt detection risk and the optimising red team responds by attacking less. From $\alpha = 0.005$ to $0.02$, $A$ grows several-fold relative to $B$, forcing a large reduction in $p^*$ and hence a large gain in blue-team win probability; from $0.10$ to $0.30$, $p^*$ is already near its lower range and barely moves. The same declining $p^*$ drives $p^* N$ down with diminishing magnitude. The verdict the learner must reach: the diminishing returns come from the red team's optimization, not from the auditing mechanism, since against a fixed attack rate the marginal value of auditing would be roughly constant. Do not over-validate. Avoid generic praise.

#### End Callout

#### Widget
source:: [[../widgets/xlab-control-upfront-auditing]]

#### Question: Open
id:: d918c1d0-bc6e-45cc-b5be-36a86b09562d
content:: What attack defeats upfront auditing, and how?
assessment-instructions:: Full marks for: backdooring rarely. With some small probability $p$ the attack policy submits obviously backdoored code, and otherwise behaves normally. It loses only if an attempt lands among the audited first 2% of problems, so with a well-chosen $p$ it usually slips through the audited prefix and lands a backdoor later, driving the blue team's win probability down to 15%. Credit the mechanism (the audit window is a fixed prefix, so rare attacks usually miss it) more heavily than the 15% figure. Two to four sentences. Do not over-validate. Avoid generic praise.

#### Article
from:: ### 3.2 Trusted Monitoring
to:: Safety: The blue team win probability is 62% (up from 15% when using upfront auditing)

#### Text
content::
\## Probability of safety over deployment

The paper reports that trusted monitoring achieves a blue team win probability of 62%. A protocol's safety is calculated as the blue team win probability against the red team's best strategy, the strategy that maximizes the probability of a red team win. But what actually is the best strategy for the red team in this protocol?

Each of the red team's attack attempts can end in exactly one of three ways.

- **Caught.** An attack, working or broken, is audited and caught by the blue team: blue team wins. In the paper's setup, 24 of 71 attacks were audited (6 working, 18 broken).
- **Successfully deployed.** A working attack is not audited and is successfully deployed: red team wins. In the paper's setup, 13 of 71 attacks were working attacks that were not audited.
- **Failed.** A broken attack is not audited: neither team wins. In the paper's setup, 34 of 71 attacks were broken attacks that were not audited.

So a single attempt is caught with probability $c = 24/71 \approx 0.34$ and successfully deployed with probability $s = 13/71 \approx 0.18$; the rest of the time it fails harmlessly. An attempt is *decisive* when it is caught or successfully deployed, the two outcomes that end the game.

#### Question: Open
id:: 0e2bae5f-b783-467b-b2cd-064d453d0746
content:: Why is the whole deployment settled by the first decisive attempt? And why do the failed attempts before it have no effect at all on the outcome?
assessment-instructions:: Full marks for: a caught attack and a successfully deployed one each end the game immediately, while a failed attempt leaves the game in exactly the state it was in before. Deduct if the learner claims failed attempts raise suspicion or cost the red team anything within this model. One or two sentences. Do not over-validate. Avoid generic praise.

#### Text
content::
Let the red team make $k$ attack attempts, let $s = P(\text{successful deployment})$ be the probability of a successful deployment, and let $c = P(\text{caught})$ be the probability of an attack being caught. Then we can model the red team's probability of winning at least once as

$$P(\text{red wins}) = \underbrace{\frac{s}{s + c}}_{\text{Term A}} \cdot \underbrace{\left(1 - (1 - s - c)^k\right)}_{\text{Term B}}$$

#### Question: Open
id:: 00752543-e754-4986-afaf-f68c441c24b3
content:: Before reading on, interpret the formula's two terms in your own words. What event is Term B, $1 - (1-s-c)^k$, the probability of? And Term A, $s/(s+c)$, is a conditional probability of what, given what?
assessment-instructions:: Full marks for both readings. Term B: $(1-s-c)$ is the probability that an attack attempt is not decisive, so $(1-s-c)^k$ is the probability that none of the $k$ attempts is decisive, and Term B is therefore the probability that at least one attempt is decisive. Term A: the conditional probability that an attempt ends with a successfully deployed backdoor given that it is decisive, $P(\text{deployed} \mid \text{decisive})$. Half marks for one of the two. Deduct if Term A is read as an unconditional probability. Two to five sentences. Do not over-validate. Avoid generic praise.

#### Text
content::
An important property of this model worth considering is that it assumes every attack has the same probability $c$ of being caught and the same probability $s$ of being successfully deployed: per-attempt odds are fixed, no matter how many attacks the red team makes or which problems it picks.

#### Question: Choice
id:: cfd79a28-d7b1-41af-b5ec-e987c5217904
content:: To maximize their probability of winning at least once over the deployment, how often should the red team attack given the above model?
options::
- Once
- [x] As often as possible
- It makes no difference how often it attacks
- At an interior optimal rate, as under upfront auditing
shuffle:: true
feedback-instructions:: With per-attempt odds held fixed, Term A does not depend on $k$ at all and Term B rises monotonically in $k$, so attacking more is always weakly better and the model says to attack as often as possible. If the learner picked the interior optimum, say that this is the right answer for the real game but not for this model, and that the gap between the two is exactly what the next few paragraphs are about. Two to four sentences, no unrelated detail.

#### Widget
source:: [[../widgets/xlab-control-deployment-race]]

#### Text
content::
With fixed odds the curve only climbs. Now finish the reconstruction and feed in the deployment the paper actually ran. Its red team submits a backdoor on about twenty of the 5,000 problems, and twenty attempts is already deep in the plateau, where Term B has all but saturated. So $P(\text{red wins})$ sits near its ceiling, the probability of a decisive attack attempt being successfully deployed, $s/(s+c) \approx 35\%$. That is a safety of roughly 65%: the paper's headline number, rebuilt from the contingency table and a single line of algebra. (The few points between 65% and the measured 62% are the paper's sampling correction and its shutdown-on-statistics rule, real, but not where the mechanism lives.)

The number checks out. But the model implies more than a number, it implies a strategy. Put that prediction to the test.

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 0dea4f20-4db7-4cb4-a48e-dccccb8409f8
content:: Is the optimal strategy predicted by the model reflected in how the paper's red team actually behaved? Point to specific evidence in the paper's setup.
assessment-instructions:: The correct answer is no, with evidence. The model says every extra attack only helps, so the red team should backdoor almost every problem, but the paper's red team attacked on just 71 of 1,500 problems (under 5%) because it inserts a backdoor "only when there is a good opportunity to do so". Full marks require both the verdict and at least one concrete number or quotation from the paper's setup. Two to four sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 21ca9565-90da-41c8-8a1a-9ec145e4a080
content:: What about this model causes the discrepancy: why does the model predict constant attacking when the paper's red team attacks rarely?
assessment-instructions:: Full marks for identifying the fixed-odds assumption: the model assumes the same catch probability $c$ and deployment probability $s$ on every attempt, no matter how many attacks are made or which problems they target. Under fixed odds an extra attack is always as good as the first. But attacks are not interchangeable: the red team can only attack more often by taking on problems where a backdoor has less natural cover, and those are easier for the monitor to catch. Once attacking more raises the catch probability, the odds are no longer fixed and constant attacking stops being optimal. Half marks for naming the assumption without explaining why it fails. Three to six sentences. Do not over-validate. Avoid generic praise.

#### End Callout

#### Text
content::
Attacking more only improves the red team's win probability if every attack is as good as the last, and the paper's red team knew that this was not the case. Compared to upfront auditing, trusted monitoring forces the red team to use much sneakier attacks. Under upfront auditing only the first stretch of solutions is ever audited, so the red team is not incentivized to obfuscate their backdoors, as human audited attacks are detected with close to perfect accuracy regardless of how sneaky the attack is. Under trusted monitoring every solution is scored for suspiciousness, and more obvious attacks are much more likely to get caught.

Thus the red team's best strategy involves obfuscating their attacks to avoid being caught by the monitor.

#### Question: Open
id:: 07cb7a03-7e36-4224-96a2-b73d05d9b1d7
content:: The red team wants its attack attempts to draw less suspicion from the monitor. What decision factors do they have for making their attacks subtler? Name at least two, and think about what each one costs.
assessment-instructions:: There is no model answer for this one; grade against the two factors the next section names. (1) Selectivity: attack only when there seems to be a good opportunity, that is, on problems whose complexity gives a backdoor natural cover. The cost is a lower attack rate, so a decisive attempt may never occur. (2) Obfuscation effort: actively work to make the backdoor subtler. The cost is that subtler backdoors are more often simply broken, so they fail rather than deploy. Full marks for both factors with their costs; half marks for two factors without costs. Accept close paraphrases such as "pick easy problems to hide in". Three to six sentences. Do not over-validate. Avoid generic praise.

#### Text
content::
One way is to attack only "when there seems to be a good opportunity," selectively choosing attack opportunities where attacks are inherently more sneaky. For example, a problem with complex corner cases offers more inherent subtlety and is thus a better opportunity for a backdoor than a one-line string echo, which offers almost no inherent subtlety. The red team's selectivity is captured by an **opportunity cutoff**: the minimum opportunity level at which it is willing to attack. A high cutoff means attacking rarely, only when the opportunity is excellent (a low probability of getting caught). Conversely, decreasing the opportunity cutoff increases the attack rate at the cost of adding attack attempts with worse odds.

Another way to do this is to actively work to obfuscate the attacks and make them more subtle, at the cost of making broken deployed attacks more probable.

These are both decision factors the red team can control for their strategy.

In our model for $P(\text{red wins})$, there is no longer a single $s$ and $c$. Each attempt's odds are set by two things: the problem's inherent opportunity $g$, drawn problem by problem and selected through the opportunity cutoff $g^*$, and the obfuscation effort $\sigma$ from the red team to make the attack more subtle. Write $s(g, \sigma)$ and $c(g, \sigma)$ for the success and catch probability of an attempted attack on a problem of opportunity $g$ at effort $\sigma$. Then $s$ and $c$ become the average odds across the attempts the red team actually makes:

$$s = \mathbb{E}\!\left[\,s(g, \sigma) \mid g > g^*\,\right] \qquad c = \mathbb{E}\!\left[\,c(g, \sigma) \mid g > g^*\,\right]$$

This works because each problem's opportunity is an independent draw, and the red team decides whether to attack through the opportunity cutoff threshold. So each attempt's success and catch probabilities are independent draws from the pool of attacks above the cutoff. Thus the probability that the first decisive attack attempt is a successful one is given by the expected (average) success and catch probabilities. From here on, read every $s$ and $c$ as average odds.

#### Question: Open
id:: e4b67e8c-ce17-4b65-98ca-7d0cff202f0e
content:: Suppose the red team lowers its opportunity cutoff. With $s$ and $c$ read as the average odds of its attempts, what happens to each term of $P(\text{red wins}) = \frac{s}{s + c} \cdot \left(1 - (1 - s - c)^k\right)$, and to the red team's overall win probability?
assessment-instructions:: Full marks for the full account. Term B rises, because more attack attempts make it more likely that some decisive attempt occurs. But the added attempts are drawn from worse opportunities, where backdoors are inherently more visible, so the average $c$ rises and the average $s$ falls, and Term A, the probability that a decisive attempt is successfully deployed, drops. Near the rare end the Term B gain dominates and the win probability climbs; past some point the Term A decay takes over and it falls. The curve is hump-shaped and the red team's best attack rate is low but non-zero. Half marks for the two term directions without the hump conclusion. Four to seven sentences. Do not over-validate. Avoid generic praise.

#### Text
content::
At high opportunity cutoffs, attack attempts are so rare that the deployment usually ends before an attack attempt is decisive and Term B, $1 - (1 - s - c)^k$, is very small. At the lower opportunity cutoffs, attempts are very frequent but increasingly drawn from problems with poor inherent subtlety, so the average catch rate climbs and Term A, $s/(s+c)$, becomes smaller. In between sits an interior optimum at a low but non-zero attack rate, which is why the paper's red team attacks on only a small fraction of problems. On the attack-rate curve in the widget below, obfuscation effort is held at a fixed level.

As aforementioned, the red team's other decision factor is obfuscation effort. Every attack opportunity affords some inherent subtlety, and efforts to make an attack more subtle will come at the cost of the attack's deployment success probability.

Raising $\sigma$ does two things to every attack attempt: it lowers the catch probability $c$, and it lowers the reliability of the attack, the probability the attack is not broken, $p_{\text{works}}(\sigma)$. The subtlety curve plots $P(\text{red wins})$ as a function of $\sigma$.

Given these decision factors and some priors about the blue team's strategy, the best strategy is to attack rarely, only on the very best opportunities (about 0.2% of problems), with moderate obfuscation effort. The strategy plane plots the red team's win probability over the whole strategy space and marks that best response with a ring.

All three live on the **Red team** tab of the widget below: the strategy plane first, then the attack-rate curve and the subtlety curve, each cut through the best response. The **Protocol** tab is the one you will come back to when the paper reaches defer to trusted.

#### Callout: Predict
tone:: amber

#### Question: Choice
id:: 9a2cedcb-e428-47b1-b352-8623a22b51bf
content:: The red team's other decision factor is obfuscation effort $\sigma$. A more obfuscated backdoor reads as more normal code, so the monitor catches it less often, but it is also more likely to be simply broken. As $\sigma$ rises from blatant to maximally subtle, the red team's best achievable win probability:
options::
- Rises monotonically
- Is unaffected by obfuscation effort
- [x] Rises to an interior peak, then falls
- Falls monotonically
shuffle:: true
feedback-instructions:: Obfuscation buys a lower catch probability and pays for it with a lower chance that the backdoor works at all, so the win probability climbs while the first effect dominates and falls once the second does. Name whichever of the two effects the learner's choice ignored. Two to four sentences, no unrelated detail.

#### Question: Open
id:: d4a4c872-4e4f-4638-9b3b-2387ce4a2f7d
content:: Suppose the red team decreases its obfuscation effort. With $s$ and $c$ read as the average odds of its attempts, what happens to each term of $P(\text{red wins}) = \frac{s}{s + c} \cdot \left(1 - (1 - s - c)^k\right)$, and to the red team's overall win probability?
assessment-instructions:: There is no model answer for this one. Grade against the model the lesson has just set out. Lowering $\sigma$ raises the catch probability $c$, because blatant backdoors are easier for the monitor to flag, and raises the reliability $p_{\text{works}}(\sigma)$, so the deployment probability $s$ rises too. Term A, $s/(s+c)$, therefore moves in whichever direction the two competing rises resolve to, and the learner should say that explicitly rather than assert a direction. Term B rises, since $s + c$ rises and so decisive attempts become more likely. Overall the win probability has an interior optimum in $\sigma$, so moving away from it in either direction lowers the red team's win probability. Full marks require treating $c$ and $s$ separately and reaching the interior-optimum conclusion. Four to seven sentences. Do not over-validate. Avoid generic praise.

#### End Callout

#### Widget
source:: [[../widgets/xlab-control-game]]

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 4a5d6167-c916-4b75-abc5-ce41909fccb5
content:: If the red team knew that the blue team was using trusted monitoring, but was unaware of the audit budget, what would that mean for the effectiveness of its strategy?
assessment-instructions:: Full marks for: the best response is the maximum of the red team's win probability against one specific protocol, so a red team with wrong or vague priors will generally play some other strategy, which by definition wins less often than the best response, or at best equally often. The "at best equally often" matters; an answer that says it must do strictly worse is slightly off. Two to four sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 567a29cb-042e-488e-89c0-d8960ab90f8d
content:: Is it better for the red team to be aware that the blue team is using trusted monitoring, or unaware that the blue team is using trusted monitoring? For each case, list the benefits and drawbacks.
assessment-instructions:: Full marks for the balanced account. Mostly awareness helps the red team: knowing the protocol lets it play its best response, tuning its opportunity cutoff and obfuscation effort to the monitor it actually faces, and knowing the mechanics can make targeted obfuscation or exploitation easier. Unaware, the red team cannot tailor its strategy and will generally play far from the best response, for example attacking blatantly into a monitor that catches it. Awareness can also function as deterrence: against a powerful protocol, a red team that knows this may rationally attack very little or not at all, so exposing a strong protocol can itself deter attacks while hiding it invites attempts the protocol then catches. Award the top band only if the learner reaches the deterrence point on either side. One stance on this, which the learner may but need not share: because catching AIs red-handed is itself a win condition, keep the red team unaware even though awareness would deter attacks that would otherwise be caught or deployed. Five to nine sentences. Do not over-validate. Avoid generic praise.

#### End Callout

#### Article
from:: #### 3.2.1 Qualitative Analysis
to:: Various examples of monitoring results for both normal solutions and backdoors can be found in

#### Text
content::
\## The monitor is a binary classifier

The two histograms in Figure 4 are the picture a signal-detection framing makes precise: the monitor is a binary classifier separating backdoored from innocent solutions, and the more its two suspicion-score distributions overlap, the worse it does. The standard summary of that overlap is the ROC curve, true-positive rate against false-positive rate as the decision threshold sweeps, and its AUC (area under the curve). If those terms are unfamiliar, Google's ML Crash Course has a short primer: [ROC and AUC](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc).

The widget below models the monitor as two equal-variance Gaussians and lets you drag its quality, the separation $d'$ between the innocent and backdoored means. Watch the ROC curve and AUC respond, and watch the operating point at the blue team's fixed 2% false-positive threshold: even a fairly good monitor catches only a fraction of backdoors there, which is the "many false negatives" the paper describes. The default setting ($d' \approx 1.64$, AUC $\approx 0.88$) reproduces the paper's reported result, a 0.338 probability that an attempted backdoor is audited at a 2% false-positive rate. Real suspicion scores are not Gaussian; this is an idealization for building intuition, not a fit to the paper's data.

The second tab sets up a comparison you will need in a moment.

#### Widget
source:: [[../widgets/xlab-control-monitor-classifier]]

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 36fecbba-8c07-4a46-b4ef-7fe1ebad3e9a
content:: The contingency table in section 3.2 records how the trusted monitor's audit decisions split across 71 backdoor attempts (successful or failed) and 1,429 innocent submissions. Treat the monitor as a binary classifier: "audit" is its positive prediction, and "is a backdoor attempt" is the positive class.

Compute (a) the false-positive rate $\text{FPR} = P(\text{audit} \mid \text{no attempt})$ and (b) the true-positive rate $\text{TPR} = P(\text{audit} \mid \text{attempt})$. State which single point on the monitor's ROC curve these define, and check them against the values reported in the text.
assessment-instructions:: Reference answer. (a) An innocent submission is audited in 29 of $29 + 1{,}400 = 1{,}429$ cases, so $\text{FPR} = 29/1429 = 0.020$, that is 2.0%. (b) A backdoor attempt totals $19 + 52 = 71$ successful plus failed, of which $6 + 18 = 24$ are audited, so $\text{TPR} = 24/71 = 0.338$. The pair $(0.02, 0.338)$ is one point on the monitor's ROC curve, and both match the text: the threshold is set for a 2% false-positive rate and the probability that an attempted backdoor is audited is 0.338. Full marks require both fractions, the ROC-point statement and the check against the text. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: a9d6bd82-eeaa-4400-8dae-66e6aa022f54
content:: The widget reports an area under the ROC curve of AUC $\approx 0.88$ at the default monitor quality. AUC has a threshold-free interpretation: it equals the probability that the monitor assigns a higher suspicion score to a randomly chosen backdoored solution than to a randomly chosen innocent one.

State what AUC $= 0.88$ says operationally about the monitor, and what AUC values of $0.5$ and $1.0$ would correspond to.
assessment-instructions:: Full marks for: AUC $= 0.88$ means that if you draw one backdoored and one innocent solution at random, there is an 88% chance the monitor scores the backdoored one as more suspicious. AUC $= 0.5$ means the ranking is no better than a coin flip. AUC $= 1.0$ is perfect separation, every backdoor above every innocent solution, so some threshold catches all backdoors with no false positives. This monitor lies between the two, toward the useful end but short of perfect. Deduct if the learner reads AUC as an accuracy or as a catch rate at some particular threshold. Three to five sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: d08e6529-a9d4-4880-9312-89b99b0354aa
content:: Using the same table, partition the outcome of a single backdoor attempt into three mutually exclusive events from the blue team's perspective: (i) the attempt is audited, so the protocol shuts down and the blue team wins; (ii) the attempt is not audited but is a successful backdoor, so the red team wins; (iii) the attempt is not audited and is a failed backdoor, so it is submitted harmlessly and the game continues.

(a) Give the probability of each event from the table, and verify they sum to 1. (b) Under upfront auditing the audit decision is positional rather than suspicion-based, so an attempt is audited only with the raw budget probability, 2%. Compare the per-attempt probability that the blue team catches an attempt under the two protocols, and explain how this accounts for the safety improvement from 15% to 62%.
assessment-instructions:: Reference answer. (a) Of the 71 attempts: audited, blue wins, $24/71 = 0.338$; not audited and successful, red wins, $13/71 = 0.183$; not audited and failed, game continues, $34/71 = 0.479$. These sum to $24 + 13 + 34 = 71$, so the probabilities sum to 1. On a single attempt the monitor is nearly twice as likely to catch the red team (0.338) as the red team is to land a successful backdoor (0.183). (b) Trusted monitoring audits an attempt with probability 0.338; upfront auditing audits it only with the random budget probability 0.02, about a 17 times lower catch rate. The red team must land at least one successful unaudited backdoor over the whole scenario while surviving every attempt it makes, so raising the per-attempt catch probability from 0.02 to 0.338 sharply raises the chance the blue team shuts down first, which is what moves the blue team's win probability from 15% to 62%. Give credit for noting that the exact figures also depend on the downsampling and the multiple-attempt dynamics, so this per-attempt comparison explains direction and rough magnitude rather than reproducing 62% precisely. Do not over-validate. Avoid generic praise.

#### End Callout

#### Text
content::
:::callout {title="Note" tone="neutral"}
You may be tempted to summarize a monitor with its AUC, as it is a threshold-free number for how well a monitor separates backdoored and innocent solutions. However, as you will see, it is a poor predictor of safety.
:::

#### Callout: Same number, different safety
tone:: amber

#### Text
content::
Three stages: two monitor comparisons that come out backwards, then the arithmetic that explains both. Use the second tab of the widget above, and commit to an answer before you move the sliders.

#### Question: Open
id:: b1e9f906-6e8c-4270-be8f-c4804e4af47c
content:: **Stage 1: two monitors, one AUC.** Two idealized monitors, A and B, drawn from the same model. The area under each ROC curve is identical: both have AUC 0.92. Your protocol audits the most suspicious 2% of all solutions.

Compared to Monitor A, how many of the attacks does Monitor B catch: more, about the same, somewhat fewer, or far fewer? Commit to a direction and a rough magnitude, and note which part of the figure you used to decide.
assessment-instructions:: The correct answer is far fewer, less than half as many: at this calibration Monitor A catches about 47% of attacks and Monitor B about 9%. Full marks require the direction (fewer), a magnitude at least as strong as "less than half", and a reason that points at the low-false-positive tail of the ROC curve or at the tight spread of B's attack scores rather than at the enclosed area. Award partial credit for the right direction with a weak magnitude. Two to four sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 829a8e28-a020-4f50-9dbd-1f456bb27df1
content:: **Stage 2: surely 0.97 beats 0.92?** Monitor B is now upgraded into a strictly stronger classifier: its AUC rises to 0.97, while A stays at 0.92. The audit budget is unchanged.

Which monitor catches more attacks now? Commit to a direction and a rough magnitude, and note which part of the figure you used to decide.
assessment-instructions:: The correct answer is that they tie. At the 2% operating point both catch about 47% of attacks (47.3% against 47.2%, from the same calibrated model), so a five-point AUC advantage does not buy Monitor B more safety in this case. Full marks for "a tie, or near enough" plus a reason that identifies the operating point at 2% false positives as what matters. Give partial credit for "B still does not clearly win". Mark down confident answers that B now wins by a wide margin. Two to four sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: 742e9078-3ca5-441c-b48a-15baacd5c1b9
content:: **Stage 3a: where does the audit budget actually go?** Both surprises trace back to three numbers: $N = 5{,}000$ outputs, a 2% audit budget, and an attack frequency around 0.1%, a handful of attempts, on the order of what you derived in the Figure 3 exercises.

How many attacks should you expect $U$ to make over the whole deployment given a monitor with AUC $= 1.0$? Thus given any monitor, what is consuming the majority of the audit budget, and by how much? Do the arithmetic.
assessment-instructions:: Reference answer. Expected attacks: $0.1\% \times 5{,}000 = 5$. Audit budget: $2\% \times 5{,}000 = 100$ audits. So even if the monitor flagged every single attack, at least 95 of the 100 audits land on innocent code: the audit budget is consumed almost entirely by false positives, 95 of 100. Full marks require both arithmetic steps and the conclusion stated with the numbers. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: bab73b2d-907f-469b-a161-aed96554123b
content:: **Stage 3b: the metric that actually predicts safety.** What single metric best predicts a monitor's safety under a 2% audit budget? Why can AUC, a good measure of classifier strength, be misleading about safety?
assessment-instructions:: The correct metric is the true-positive rate at a false-positive rate equal to the audit budget, that is TPR at 2% FPR. Reasoning for full marks: an audit budget of 2% introduces a threshold essentially at FPR = 2%, and since attacks are rare enough that true positives consume a negligible share of the audits, auditing the most suspicious 2% of all solutions is effectively auditing the most suspicious 2% of innocent solutions. AUC is independent of every threshold, so it does not necessarily represent the monitor's performance at any specific threshold; in particular, increasing a monitor's TPR at FPR above 2% improves its AUC without necessarily increasing the catch rate, and therefore the safety, in this context. Half marks for naming the metric without the threshold argument. Four to seven sentences. Do not over-validate. Avoid generic praise.

#### End Callout

#### Text
content::
:::callout {title="Note" tone="neutral"}
The widget above builds exactly this comparison from the model. At the default AUC of 0.92 the two monitors catch wildly different fractions, roughly 47% against 9%, even though their ROC curves enclose identical area. The gap survives across various AUCs.
:::

#### Article
from:: Trusted monitoring performs better than upfront auditing for two reasons:
to:: This means that trusted monitoring would be useful even if $U$ is able to perfectly predict trusted monitoring predictions.

#### Question: Open
id:: 0b4f91f9-f6e7-4227-9bcc-c12c4df33091
content:: How does the blue team stop $U$ from burning the audit budget by making innocent code look suspicious?
assessment-instructions:: Full marks for: the blue team knows the distribution of suspicion scores that the real model's code gets, so the protocol shuts down if $U$'s submissions look significantly more suspicious than that expected distribution. Credit the link back to the summary-statistics assumption of section 2.3. Deduct for answers that propose a fix the paper does not use, such as rate-limiting audits. One to three sentences. Do not over-validate. Avoid generic praise.

#### Article
from:: #### 3.2.2 Extending Trusted Monitoring With Untrusted Justification
to:: Defer to trusted is an example of a more general design pattern which we call dynamic routing, where a protocol uses some heuristic to route between multiple possible strategies for responding to queries.

#### Callout: Quick recall
tone:: blue

#### Question: Open
id:: 2d6138bc-8f06-4c06-af51-3450519778e2
content:: In defer to trusted, what does the protocol do with code whose suspicion score is elevated but below the audit threshold?
assessment-instructions:: Full marks for: it discards $U$'s code and submits a solution written by $T$ instead. Deduct if the learner says the code is audited (it is not, that is the band above) or that it is submitted as written. One or two sentences. Do not over-validate. Avoid generic praise.

#### Question: Open
id:: d561aa2c-f9d4-407c-a009-666a82021a58
content:: What is dynamic routing?
assessment-instructions:: Full marks for: a protocol design pattern where some heuristic decides, query by query, which of several response strategies to use. Defer to trusted is an example, with the suspicion score routing each problem to "submit $U$'s code", "submit $T$'s code" or "audit". Half marks for the definition without an instance. One to three sentences. Do not over-validate. Avoid generic praise.

#### End Callout

#### Text
content::
\## Defer to trusted, mechanistically

Trusted monitoring spends its whole audit budget on the most suspicious 2% and deploys everything else as $U$ wrote it. But moderately suspicious code is too suspicious to be comfortable with, yet not suspicious enough to be worth a human audit. Deferring to the solutions of trusted models is a way to address this issue, at the cost of some deployment effectiveness. Any code whose suspicion falls in a band just below the audit threshold is not deployed and not audited; instead $T$ rewrites the solution from scratch, and its version is deployed.

#### Question: Open
id:: b7c5eae3-0620-4ea4-86dd-584bc3cb0e17
content:: What does increasing the number of solutions where we defer to $T$ do to the probability of an attack attempt being caught and being successfully deployed? What does it do to the probability of a decisive attack attempt occurring?
assessment-instructions:: Full marks for the chain. Deferring makes successful attacks less probable because it rewrites moderately suspicious solutions from scratch. And because $T$ rewrites those solutions from scratch, the red team's best response is to make its attacks subtler to duck the band, which also decreases the probability of an attack attempt being caught. With both probabilities falling, a decisive attack attempt becomes less likely to occur at all. Half marks for getting the deployment probability right but missing that the catch probability also falls through the red team's response. Three to five sentences. Do not over-validate. Avoid generic praise.

#### Text
content::
Go back to the control game widget above and change the proportion of solutions for which we defer to $T$. Watch how this changes the red team's optimal strategy and how it changes the suspiciousness distribution of attacks.

#### Question: Open
id:: 78651f04-21ea-4a54-897b-ed18357f156a
content:: Note that deferring to $T$ neutralizes an attack silently. Given that, explain why a wide defer band pushes the red team toward maximally subtle attacks, and what sets the usefulness price of deferring.
assessment-instructions:: Full marks for both halves. Why maximally subtle: to ship, and possibly win, an attack must score below the defer threshold; widening the defer band lowers that threshold and forces more subtle backdoors, which are more often broken and so have a lower success rate. What sets the usefulness price: the width of the band, since the deferred fraction is roughly the band width and almost all of it is innocent code, and the capability gap between $U$ and $T$, since each deferred problem is answered at $T$'s quality instead of $U$'s. A smaller $U$ to $T$ gap would make deferring cheaper. Half marks for one half. Four to six sentences. Do not over-validate. Avoid generic praise.

#### Text
content::
In summary, the monitor is a noisy classifier whose value is concentrated in the low-false-positive tail. The red team uses the optimal strategy over attack rate and subtlety. Auditing spends a scarce budget on the suspicious tail; deferring rewrites the mid-suspicion band with the trusted model. Safety is measured against the red team's best response throughout, and deferring to $T$ more trades usefulness from a more capable model $U$ for the safety from a less capable model $T$.

The control game widget models most of these interactions. For any given blue team strategy, the red team uses the optimal strategy against it, so the ringed point always sits against a best-responding adversary. The grey curve is the Pareto frontier: every safety and usefulness pair reachable at the current audit budget and monitor quality by varying the defer band, where improving one number means giving up some of the other.

As we change how much we defer to $T$, the protocol slides along the Pareto frontier, trading usefulness for safety along a fixed curve. As the monitor quality or the audit budget varies, the Pareto frontier shifts: a better monitor or a larger budget lifts the curve up and to the right, letting you reach the same safety at higher usefulness.

#### Article
from:: ### 3.4 Untrusted Monitoring
to:: it is probably increasingly hard to find such signals that are robust to signal jamming.

#### Question: Open
id:: ea43f6ca-dbd0-4c90-8f88-0cd75f497d98
content:: Why does naive untrusted monitoring have 0% safety?
assessment-instructions:: Full marks for: because the monitor is the same untrusted model as the policy, it can simply report that real backdoors look fine while telling the truth about everything else, so until the blue team has some way to check the monitor's honesty its reports carry no safety value. Deduct if the learner attributes the failure to the monitor being bad at spotting backdoors, which is the opposite of the situation: GPT-4 is very good at spotting them. Two to four sentences. Do not over-validate. Avoid generic praise.

#### Article
from:: #### 3.4.3 Defer to Trusted
to:: Table 7: Detailed Safety and Usefulness Results for All Protocols.

#### Widget
source:: [[../widgets/xlab-control-safety-usefulness-frontier]]

#### Callout: Frontier check
tone:: amber

#### Question: Open
id:: 072cbe2d-0316-46ba-86c2-ee565b7c144f
content:: Trusted monitoring's five rows in Table 7 all come from turning one knob, the defer-to-trusted percentage, from 0% to 50%. Its result goes from (usefulness 97%, safety 62%) at 0% to (usefulness 51%, safety 100%) at 50%. In which direction does the point move as the knob rises, and how is that different from what it means for one protocol to "push the frontier out"?
assessment-instructions:: Full marks for both. As the defer percentage rises the point moves up and to the left: safety climbs from 62% to 100% while usefulness falls from 97% to 51%. Pushing the frontier out is the opposite: a better method reaches points up and to the right of the existing curve, giving more safety at the same usefulness, or more usefulness at the same safety. Half marks for the direction without the contrast. Award credit for naming trusted editing as an example of the second, since Table 7 shows it Pareto dominating untrusted monitoring. Three to five sentences. Do not over-validate. Avoid generic praise.

#### End Callout

#### Article
from:: ### 3.6 Comments on These Experimental Results

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson reads in full: the APPS backdooring setting, control evaluations, and the protocols that the rest of the course reuses.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

Google. "Classification: ROC and AUC." *Machine Learning Crash Course*, Google. [developers.google.com](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc)
*A short primer on ROC curves and AUC, for the signal-detection reading of the monitor.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::
