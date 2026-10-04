---
id: 'd7444383-f92c-40ed-8425-5bc531966811'
title: "The AI control paper (3): the red team's best response"
tldr: "If every attack had the same odds, the red team should attack on every problem. The paper's red team attacked rarely, and was right to. This part works out why: the odds are not fixed, and the red team has choices that change them. It shows why those choices have a sweet spot, and ends at the red team's best response to trusted monitoring."
summary_for_tutor: "Part 3 of 6 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (2)', which read section 3 up to trusted monitoring's 62% safety and rebuilt that number with a fixed-odds model: each attempt is caught with probability c = 24/71 and successfully deployed with probability s = 13/71, and P(red wins) = Term A, s/(s+c), the chance a decisive attempt is a deployed backdoor, times Term B, 1-(1-s-c)^k, the chance any attempt is decisive. That model predicts constant attacking, while the paper's red team attacked on 71 of 1,500 problems, because the odds are not fixed. This part has no new article text; it is the lesson's own analysis of trusted monitoring (section 3.2). The gap is explained by two decision factors, the opportunity cutoff g* (attack only on problems whose inherent opportunity g is high enough) and obfuscation effort sigma (subtler backdoors are caught less often but more often broken); s and c become the average odds over the attempts actually made, and each factor gives a hump-shaped win probability. Three widgets, in XLab's order: the attack-rate hump (opportunity cutoff, obfuscation fixed), the subtlety curve (obfuscation effort, at its best attack rate), and the red team's best response over the whole strategy plane (audit budget slider, about 65% safety and 0.2% attack rate at a 2% budget). They share one model with the control game widget of 'The AI control paper (5)', which adds the defer band; the model's assumptions are in a closed 'How the model is built' callout below the best-response widget. A short numerical practice question after the opportunity-cutoff question has the learner compute the win probability of a rare and a frequent strategy and name the limiting term of each. The lens ends with two questions on what the red team gains from knowing the protocol and its audit budget. The revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer."
reading_minutes: 20
tutor_minutes: 40
tags: []
---
#### Text
content::
Part 3 of 6 of the founding AI control paper. The previous part read the results for upfront auditing and trusted monitoring and rebuilt trusted monitoring's 62% safety from a fixed-odds model: each attempt is caught with probability $c$ and successfully deployed with probability $s$, so $P(\text{red wins}) = \frac{s}{s + c} \cdot \left(1 - (1 - s - c)^k\right)$, Term A, the chance that a decisive attempt is a win for the red team, times Term B, the chance that any of the $k$ attempts is decisive. That model says to attack as often as possible, yet the paper's red team attacked rarely. This part works out why, from the choices the red team has, and ends at its best response to trusted monitoring.

#### Text
content::
Attacking more only improves the red team's win probability if every attack is as good as the last, and the paper's red team knew that this was not the case. Compared to upfront auditing, trusted monitoring forces the red team to use much sneakier attacks. Under upfront auditing only the first stretch of solutions is ever audited, so the red team is not incentivized to obfuscate their backdoors, as human audited attacks are detected with close to perfect accuracy regardless of how sneaky the attack is. Under trusted monitoring every solution is scored for suspiciousness, and more obvious attacks are much more likely to get caught.

Thus the red team's best strategy involves obfuscating their attacks to avoid being caught by the monitor.

#### Question: Open
id:: 07cb7a03-7e36-4224-96a2-b73d05d9b1d7
content:: The red team wants its attack attempts to draw less suspicion from the monitor. What decision factors do they have for making their attacks subtler? Name at least two, and think about what each one costs.
assessment-instructions:: Score out of 100. 50: selectivity, 25 for attacking only when there is a good opportunity (problems whose complexity gives a backdoor natural cover), and 25 for its cost: fewer attacks, so the deployment may end before any attempt is decisive. 50: obfuscation, 25 for actively working to make the backdoor subtler, closer to normal code, and 25 for its cost: subtler backdoors are more often simply broken, so they fail instead of deploying. Another genuine way to draw less suspicion, with its real cost, earns the same credit as one of these. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Two decision factors. Selectivity: attack only when there seems to be a good opportunity, on problems whose complexity gives a backdoor natural cover; the cost is a lower attack rate, so a decisive attempt may never occur. Obfuscation effort: actively work to make the backdoor subtler; the cost is that subtler backdoors are more often simply broken, so they fail rather than deploy."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

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
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and the most important thing they missed, then give this answer so they leave with it: "Term B rises, because more attack attempts make it more likely that some decisive attempt occurs. But the added attempts are drawn from worse opportunities, where backdoors are inherently more visible, so the average $c$ rises and the average $s$ falls, and Term A, the probability that a decisive attempt is successfully deployed, drops. Near the rare end the Term B gain dominates and the win probability climbs; past some point the Term A decay takes over and it falls. The curve is hump-shaped and the red team's best attack rate is low but non-zero." No follow-up question. No generic praise.

#### Callout: Practice: put numbers on it
tone:: amber

#### Question: Open
id:: e998048d-d7f1-4cda-a819-b1bbd3d23dca
optional:: true
content:: A red team is choosing between two strategies against a protocol. Rare: attack on the 4 best opportunities, where each attempt is caught with probability $c = 0.05$ and deploys successfully with probability $s = 0.10$. Frequent: attack on 60 problems, where the average attempt has $c = 0.12$ and $s = 0.03$.

Compute $P(\text{red wins})$ for each strategy, say which one the red team prefers, and say which of the two terms holds each strategy back.
placeholder:: Show both calculations
assessment-instructions:: Score out of 100. 25: the rare strategy: Term A $0.10/0.15 \approx 0.67$, Term B $1 - 0.85^4 \approx 0.48$, so $P(\text{red wins}) \approx 0.32$. 25: the frequent strategy: Term A $0.03/0.15 = 0.2$, Term B $1 - 0.85^{60} \approx 1$, so $P(\text{red wins}) \approx 0.20$. 10: the red team prefers the rare strategy. 40: what holds each back, 20 each: the rare strategy is limited by Term B (with only four attempts, about half the time none is decisive before the deployment ends), and the frequent strategy by Term A (a decisive attempt is nearly certain, but it is a successful deployment only about one time in five). Accept numbers within about 0.02; an arithmetic slip carried forward loses credit only once. Cap at 30 if the answer adds up the chances of separate attempts instead of using the formula. Model answer, for the feedback, not a grading checklist: "Rare: Term A is $0.10/0.15 \approx 0.67$ and Term B is $1 - 0.85^4 \approx 0.48$, so $P(\text{red wins}) \approx 0.32$. Frequent: Term A is $0.03/0.15 = 0.2$ and Term B is $1 - 0.85^{60} \approx 1$, so $P(\text{red wins}) \approx 0.20$. The red team prefers the rare strategy. The rare strategy is held back by Term B: with only four attempts, about half the time none of them is decisive before the deployment ends. The frequent strategy is held back by Term A: nearly certain to produce a decisive attempt, but the worse odds make that attempt a successful deployment only one time in five."
feedback-instructions:: One turn, at most five sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
At high opportunity cutoffs, attack attempts are so rare that the deployment usually ends before an attack attempt is decisive and Term B, $1 - (1 - s - c)^k$, is very small. At the lower opportunity cutoffs, attempts are very frequent but increasingly drawn from problems with poor inherent subtlety, so the average catch rate climbs and Term A, $s/(s+c)$, becomes smaller. In between sits an interior optimum at a low but non-zero attack rate, which is why the paper's red team attacks on only a small fraction of problems. On the attack-rate curve in the widget below, obfuscation effort is held at a fixed level.

#### Widget
source:: [[../widgets/xlab-control-attack-rate-hump]]

#### Text
content::
As aforementioned, the red team's other decision factor is obfuscation effort. Every attack opportunity affords some inherent subtlety, and efforts to make an attack more subtle will come at the cost of the attack's deployment success probability.

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
content:: Suppose the red team decreases its obfuscation effort. With $s$ and $c$ read as the average odds of its attempts, what happens to each term of $P(\text{red wins}) = \frac{s}{s + c} \cdot \left(1 - (1 - s - c)^k\right)$, and why? What happens to the red team's overall win probability?
assessment-instructions:: Score out of 100. 30: Term B, 15 for: it rises, and 15 for why: blatant backdoors are caught more often and are broken less often, so fewer attempts fail harmlessly, $s + c$ rises and a decisive attempt becomes more likely. 35: Term A, 15 for: its direction is not fixed, it can rise or fall, and 20 for why: it is pulled down because the monitor catches blatant backdoors more often ($c$ rises) and pulled up because more of the backdoors actually work ($s$ rises), so it depends on which effect is stronger. 35: overall: the win probability has a sweet spot in obfuscation effort, so lowering effort helps the red team only if it was obfuscating too much, and from its best obfuscation level any decrease lowers its win probability. An answer that says the overall effect depends on where the red team started, helping if it obfuscated too much and hurting if it was at or below its best level, earns this in full. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Term B rises: blatant backdoors are caught more often and broken less often, so fewer attempts fail harmlessly, $s + c$ goes up and a decisive attempt becomes more likely. Term A, $s/(s+c)$, can go either way: the higher catch rate pulls it down, and the larger share of backdoors that work pulls it up. Overall the win probability has a sweet spot in obfuscation effort: from the red team's best level, lowering effort lowers its win probability; it helps only if the red team was obfuscating too much to begin with."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
Raising $\sigma$ does two things to every attack attempt: it lowers the catch probability $c$, and it lowers the reliability of the attack, the probability the attack is not broken, $p_{\text{works}}(\sigma)$. The widget below plots the per-attack outcome probabilities and $P(\text{red wins})$ as a function of $\sigma$.

#### Widget
source:: [[../widgets/xlab-control-subtlety]]

#### Text
content::
Given these decision factors and some priors about the blue team's strategy, the best strategy is to attack rarely, only on the very best opportunities (about 0.2% of problems), with moderate obfuscation effort. The widget below plots the red team's win probability over the whole strategy space and marks that best response with a ring.

#### Widget
source:: [[../widgets/xlab-control-best-response]]

#### Text
content::
:::callout {title="How the model is built" tone="neutral" collapse="closed"}
A model built for intuition, not a re-run of the paper's experiments. Opportunity quality is drawn from a Beta(2,5), a subtler backdoor is caught less often but is more often simply broken, and usefulness is charged as the share of problems handed to the weaker model.
:::

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 4a5d6167-c916-4b75-abc5-ce41909fccb5
content:: If the red team knew that the blue team was using trusted monitoring, but was unaware of the audit budget, what would that mean for the effectiveness of its strategy, and why?
assessment-instructions:: Score out of 100. 60: the consequence: its strategy will generally be less effective than its best response, winning less often (at best equally often, if its guess happens to be right); either wording earns all 60. 40: why: the red team's best strategy (how often and how subtly to attack) depends on the audit budget, so without knowing it the red team has to guess the budget and will usually be off. An answer that says the right attack rate or subtlety depends on how much gets audited, so the red team must guess, earns all 40. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Its strategy will generally be less effective. How often and how subtly it should attack depends on how much gets audited, so it has to guess the budget, and with a wrong guess it wins less often than it could; it does as well only if the guess happens to be right."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 567a29cb-042e-488e-89c0-d8960ab90f8d
content:: Is it better for the red team to be aware that the blue team is using trusted monitoring, or unaware that the blue team is using trusted monitoring? For each case, list the benefits and drawbacks.
assessment-instructions:: Score out of 100. 30: benefits of being aware: the red team can tailor its attacks to the monitor it actually faces (for example when to attack, how subtle to be, or exploiting how the protocol works), so it plays close to its best response. 30: drawbacks of being unaware: it cannot tailor its strategy and generally plays far from the best response, for example attacking blatantly into a monitor that catches it. 20: deterrence, the other side: a red team that knows it faces a strong protocol may rationally attack very little or not at all, while an unaware red team still attempts attacks. 20: a verdict that weighs the two sides, for example that awareness mostly helps the red team. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mostly, awareness helps the red team: knowing the protocol lets it play its best response, tuning its opportunity cutoff and obfuscation effort to the monitor it actually faces, and knowing the protocol's mechanics can make targeted obfuscation or exploitation easier. Unaware, the red team cannot tailor its strategy, so it will generally play far from the best response, for example attacking blatantly into a monitor that catches it. Awareness can also function as deterrence. If the blue team's protocol is powerful (like Ctrl-Z, a later control protocol), a red team that knows this may rationally attack very little or not at all, so exposing a strong protocol can itself deter attacks, while hiding it invites attempts the protocol then catches."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper whose trusted-monitoring results (section 3.2) this part analyses; "when there seems to be a good opportunity" is its Table 2's description of the red team's attack policy.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::
