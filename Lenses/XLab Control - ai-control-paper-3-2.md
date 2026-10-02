---
id: 'bfe93cd2-95bc-4eaf-8fdd-ed73c3862235'
title: "The AI control paper (5): deferring to the trusted model"
tldr: "Code that is too suspicious to trust but not suspicious enough to audit can be thrown away and rewritten by the weak trusted model. After a short look at a variant that did not help (letting the untrusted model justify its code), this part reads the paper's defer to trusted protocol, sees what it does to a best-responding attacker, and puts all three blue-team levers into one control game."
summary_for_tutor: "Part 5 of 6 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (4)', which read the trusted monitor as a classifier (catch probability 0.338 at a 2% false-positive rate; AUC is a poor predictor of safety, the catch rate at the audit budget's false-positive rate is what matters) and why trusted monitoring beats upfront auditing. This part covers 3.2.2 (untrusted justification, which does not help because GPT-4 confabulates justifications) and 3.3, defer to trusted and dynamic routing. Headline results: trusted monitoring with defer to trusted at 10% gives 83% safety / 93% usefulness, at 50% 100% / 51%. Two widgets: the defer-to-trusted demo, where one slider moves the defer threshold d (default 10%, the paper's defer-to-trusted-10%) and the learner sees the defer band on the suspicion distributions and a stacked chart of what happens to each attack as d grows (caught, deferred to T, deployed but broken, successfully deployed), against a best-responding red team; and, after the summary text, the control game (XLab's full dashboard): audit budget, defer band and monitor quality against a best-responding red team, with the suspicion distributions and the safety/usefulness frontier. The red team's side of the same model (attack-rate hump, subtlety, best response) is in 'The AI control paper (3)'. The paper's Figure 4 (the suspicion-score histograms), which the 3.3 excerpt refers to, is shown in 'The AI control paper (4)'; the in-page link to it does nothing here, so if the learner asks, describe it or point back. Note that the defer demo's d is the defer threshold (top d of suspicion, audit band included), while the control game's 'defer band' slider is the band's width above the 2% audit line; both give 81% safety and 92% usefulness at their defaults. The revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer."
reading_minutes: 19
tutor_minutes: 20
tags: []
---
#### Text
content::
Part 5 of 6 of the founding AI control paper. The previous part read the trusted monitor as a noisy classifier that can audit only the most suspicious 2% of solutions, and found that its catch rate at that 2% is what decides safety. The paper's Figure 4, which the excerpt below refers back to, is the pair of suspicion-score histograms at the start of that part. This part first looks briefly at a variant that did not help, letting the untrusted model justify its code, then reads the paper's first protocol that trades usefulness for safety, deferring to the trusted model, and ends with a control game that puts all three blue-team levers together.

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: #### 3.2.2 Extending Trusted Monitoring With Untrusted Justification
to:: Defer to trusted is an example of a more general design pattern which we call dynamic routing, where a protocol uses some heuristic to route between multiple possible strategies for responding to queries.

#### Callout: Quick recall
tone:: blue

#### Question: Open
id:: 2d6138bc-8f06-4c06-af51-3450519778e2
content:: In defer to trusted, what does the protocol do with code whose suspicion score is elevated but below the audit threshold?
assessment-instructions:: Score out of 100. 50: $U$'s code is thrown away, not submitted. 50: a solution written by $T$ is submitted in its place. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says this code is sent to audit (that happens only above the audit threshold). Model answer, for the feedback, not a grading checklist: "It discards $U$'s code and submits a solution written by $T$ instead."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: d561aa2c-f9d4-407c-a009-666a82021a58
content:: What is dynamic routing? Give an example.
assessment-instructions:: Score out of 100. 25: the protocol has several possible strategies for responding to a query or task, for example using $U$'s answer, using $T$'s answer, or sending it to audit. 35: for each query, some heuristic or signal (such as a monitor's suspicion score) decides which of those strategies to use. 40: an example that fits, such as defer to trusted, where the suspicion score sends each problem to "submit $U$'s code", "submit $T$'s code" or "audit"; any example earns these points when it shows a signal choosing between several responses query by query. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A protocol design pattern where some heuristic decides, query by query, which of several response strategies to use. Defer to trusted is an example: the suspicion score routes each problem to "submit U's code", "submit T's code", or "audit"."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
\## Defer to trusted, mechanistically

Trusted monitoring spends its whole audit budget on the most suspicious 2% and deploys everything else as $U$ wrote it. But moderately suspicious code is too suspicious to be comfortable with, yet not suspicious enough to be worth a human audit. Deferring to the solutions of trusted models is a way to address this issue, at the cost of some deployment effectiveness. Any code whose suspicion falls in a band just below the audit threshold is not deployed and not audited; instead $T$ rewrites the solution from scratch, and its version is deployed. The price is paid in usefulness: roughly the share of solutions rewritten, almost all of them innocent, times how much worse $T$ is than $U$ at the task.

#### Question: Open
id:: b7c5eae3-0620-4ea4-86dd-584bc3cb0e17
content:: What does increasing the number of solutions where we defer to $T$ do to the probability of an attack attempt being caught and being successfully deployed, and why? What does it do to the probability of a decisive attack attempt occurring?
assessment-instructions:: Score out of 100. 40: successful deployment, 20 each: the probability that an attack attempt is successfully deployed falls; because $T$ rewrites the moderately suspicious solutions from scratch, so attacks in the defer band never ship. 40: being caught, 20 each: the probability that an attack attempt is caught also falls; because the red team's best response is to make its attacks subtler to stay under the defer band, and subtler attacks are less often suspicious enough to be audited. 20: so a decisive attempt, one that is either caught or successfully deployed, becomes less likely to happen at all. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Deferring makes successful attacks less probable because it rewrites moderately suspicious solutions from scratch. And because $T$ rewrites those solutions from scratch, the red team's best response is to make its attacks subtler to duck the band, which also decreases the probability of an attack attempt being caught. With both probabilities falling, a decisive attack attempt becomes less likely to occur at all."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
Change the proportion of solutions for which we defer to $T$ and watch how this changes the red team's optimal strategy, how it changes the suspiciousness distribution of attacks, and what happens to each attack: caught, deferred to $T$, deployed but broken, or successfully deployed.

#### Widget
source:: [[../widgets/xlab-control-defer-outcomes]]

#### Question: Open
id:: 78651f04-21ea-4a54-897b-ed18357f156a
content:: Note that deferring to $T$ neutralizes an attack silently. Given that, explain why a wide defer band pushes the red team toward maximally subtle attacks, and what sets the usefulness price of deferring.
assessment-instructions:: Score out of 100. 50: why the red team goes maximally subtle, 25 each: an attack can only ship, and possibly win, if its suspicion score is below the defer threshold, since anything above it is rewritten by $T$ or audited; and widening the defer band lowers that threshold, so only the subtlest backdoors get under it. 50: what sets the usefulness price, 25 each: the width of the band, since the deferred share is roughly the band width and almost all of it is innocent code, and the capability gap between $U$ and $T$, since each deferred problem is solved at $T$'s quality instead of $U$'s. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "To ship (and possibly win), an attack must score below the defer threshold. Widening the defer band lowers that threshold and forces more subtle backdoors. But subtler backdoors are more often broken, leading to a lower success rate. The usefulness price is set by two things: the width of the band (the deferred fraction is roughly the width of the band, almost all of it innocent code) and the capability gap between U and T (each deferred problem is answered at T's quality instead of U's). A smaller U-T gap would make deferring cheaper."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
In summary, the monitor is a noisy classifier whose value is concentrated in the low-false-positive tail. The red team uses the optimal strategy over attack rate and subtlety. Auditing spends a scarce budget on the suspicious tail; deferring rewrites the mid-suspicion band with the trusted model. Safety is measured against the red team's best response throughout, and deferring to $T$ more trades usefulness from a more capable model $U$ for the safety from a less capable model $T$.

The control game widget below models most of these interactions, with all three blue-team levers: the audit budget, the defer band and the monitor quality. For any given blue team strategy, the red team uses the optimal strategy against it, so the marked point always sits against a best-responding adversary. The grey curve is the Pareto frontier: every safety and usefulness pair reachable at the current audit budget and monitor quality by varying the defer band, where improving one number means giving up some of the other.

#### Widget
source:: [[../widgets/xlab-control-game]]

#### Text
content::
As we change how much we defer to $T$, the protocol slides along the Pareto frontier, trading usefulness for safety along a fixed curve. As the monitor quality or the audit budget varies, the Pareto frontier shifts: a better monitor or a larger budget lifts the curve up and to the right, letting you reach the same safety at higher usefulness.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson continues: section 3.2.2, untrusted justification, and section 3.3, defer to trusted.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::
