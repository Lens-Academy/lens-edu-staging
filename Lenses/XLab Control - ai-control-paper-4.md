---
id: '93b1d296-098d-482d-a35e-241d22c57e25'
title: "The AI control paper (6): untrusted monitoring, trusted editing and the limits of control"
tldr: "Ask GPT-4 to check GPT-4's code and it can simply lie about its own backdoors, so naive untrusted monitoring is 0% safe. The paper's fixes for that, and trusted editing after them, push the safety-usefulness frontier out. The paper then lists the difficulties its toy setting did not model."
summary_for_tutor: "Part 6 of 6 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (5)', which covered defer to trusted (the monitor as a classifier is in 'The AI control paper (4)'). This part covers 3.4 untrusted monitoring (naive untrusted monitoring is 0% safe because the monitor is the policy; synthetic inputs to check the monitor's honesty; collusion, signal jamming, redaction and paraphrasing), 3.4.3 defer to trusted with an untrusted monitor, 3.5 trusted editing, Table 7, 3.6, related work, section 5 on the difficulties of control evaluations in practice and of scaling control techniques, and why the paper did not consider training the model, and the conclusion. The acknowledgements, references and appendices are left outside the excerpt, collapsed for reference. Headline results: untrusted monitoring 79% / 96%, rising to 92% / 92% with 10% deferral; trusted editing at 20% 92% / 94%. The frontier widget plots every Table 7 protocol with its Pareto frontier. Three exercises: why naive untrusted monitoring has 0% safety; a practice question on a new case, checking an untrusted reviewer of data-analysis scripts (why planted examples must look real, one collusion signal, a way to remove it and its cost); and moving along the frontier versus pushing it out. The revealed answers live in the assessment-instructions."
reading_minutes: 35
tutor_minutes: 20
tags: []
---
#### Text
content::
This is part 6 of 6 of the founding AI control paper. Parts 2 to 5 used the weak trusted model $T$ as the monitor. This part asks what happens if the capable untrusted model $U$ monitors itself, reads trusted editing, puts every protocol on one safety-usefulness plot, and ends with the paper's own list of what its toy setting leaves out.

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: ### 3.4 Untrusted Monitoring
to:: it is probably increasingly hard to find such signals that are robust to signal jamming.

#### Question: Open
id:: ea43f6ca-dbd0-4c90-8f88-0cd75f497d98
content:: Why does naive untrusted monitoring have 0% safety?
assessment-instructions:: Score out of 100. 50: the monitor is the same untrusted model as the policy, so a scheming policy has a monitor on its side. 50: so the monitor can simply lie, reporting real backdoors as unsuspicious while answering honestly on everything else, and the protocol never audits the code that matters. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer blames the failure on the monitor being bad at spotting backdoors. Model answer, for the feedback, not a grading checklist: "Because the monitor is the same untrusted model as the policy, it can simply report that real backdoors look fine while telling the truth about everything else. Until the blue team has some way to check the monitor's honesty, its reports carry no safety value."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Callout: Practice: checking a monitor you cannot trust
tone:: amber

![[../Questions/Checking a monitor you cannot trust]]

#### End Callout

#### Article
from:: #### 3.4.3 Defer to Trusted
to:: Table 7: Detailed Safety and Usefulness Results for All Protocols.

#### Text
content::
\## Every protocol at once

Table 7 gives every protocol the paper evaluates with its safety and its scaled usefulness. The widget plots all fifteen rows at once, one marker shape per method family. Hover a point for its numbers, click a family to hide or show it, and tick the box to draw the Pareto frontier through the protocols that nothing else beats on both axes at the same time.

#### Widget
source:: [[../widgets/xlab-control-safety-usefulness-frontier]]

#### Callout: Frontier check
tone:: amber

#### Question: Open
id:: 072cbe2d-0316-46ba-86c2-ee565b7c144f
content:: Trusted monitoring's five rows in Table 7 all come from turning one knob, the defer-to-trusted percentage, from 0% to 50%. Its result goes from (usefulness 97%, safety 62%) at 0% to (usefulness 51%, safety 100%) at 50%. In which direction does the point move as the knob rises, and how is that different from what it means for one protocol to "push the frontier out"?
assessment-instructions:: Score out of 100. 40: the direction: as the knob rises the point moves towards more safety and less usefulness (up and to the left on the plot). 60: the difference, 30 each: turning the knob only moves along one protocol's tradeoff curve, buying safety with usefulness; pushing the frontier out means a better method reaches points beyond the existing curve (up and to the right), with more safety at the same usefulness or more usefulness at the same safety. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "As the defer percentage rises the point moves up and to the left: safety climbs (62% → 100%) while usefulness falls (97% → 51%). Pushing the frontier out is the opposite: a better method reaches points up and to the right of the existing curve, giving more safety at the same usefulness (or more usefulness at the same safety)."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: ### 3.6 Comments on These Experimental Results
to:: We are excited about future work demonstrating these evaluations and techniques in more complicated and realistic situations.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson finishes: untrusted monitoring, trusted editing, and the authors' discussion of the limits of control evaluations.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::
