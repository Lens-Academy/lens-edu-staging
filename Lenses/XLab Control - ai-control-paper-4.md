---
id: '93b1d296-098d-482d-a35e-241d22c57e25'
title: "The AI control paper (4): untrusted monitoring, trusted editing and the limits of control"
tldr: "Ask GPT-4 to check GPT-4's code and it can simply lie about its own backdoors, so naive untrusted monitoring is 0% safe. The paper's fixes for that, and trusted editing after them, push the safety-usefulness frontier out. The paper then lists the difficulties its toy setting did not model."
summary_for_tutor: "Part 4 of 4 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (3)', which covered the monitor as a classifier and defer to trusted. This part covers 3.4 untrusted monitoring (naive untrusted monitoring is 0% safe because the monitor is the policy; synthetic inputs to check the monitor's honesty; collusion, signal jamming, redaction and paraphrasing), 3.4.3 defer to trusted with an untrusted monitor, 3.5 trusted editing, Table 7, 3.6, related work, section 5 on the difficulties of control evaluations in practice and of scaling control techniques, and why the paper did not consider training the model, and the conclusion. The acknowledgements, references and appendices are left outside the excerpt, collapsed for reference. Headline results: untrusted monitoring 79% / 96%, rising to 92% / 92% with 10% deferral; trusted editing at 20% 92% / 94%. The frontier widget plots every Table 7 protocol with its Pareto frontier. Two exercises: why naive untrusted monitoring has 0% safety, and moving along the frontier versus pushing it out; the revealed answers live in the assessment-instructions."
reading_minutes: 40
tutor_minutes: 5
tags: []
---
#### Text
content::
This is part 4 of 4 of the founding AI control paper. Parts 2 and 3 used the weak trusted model $T$ as the monitor. This part asks what happens if the capable untrusted model $U$ monitors itself, reads trusted editing, puts every protocol on one safety-usefulness plot, and ends with the paper's own list of what its toy setting leaves out. The acknowledgements, references and appendices after the conclusion stay collapsed if you want them.

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: ### 3.4 Untrusted Monitoring
to:: it is probably increasingly hard to find such signals that are robust to signal jamming.

#### Question: Open
id:: ea43f6ca-dbd0-4c90-8f88-0cd75f497d98
content:: Why does naive untrusted monitoring have 0% safety?
assessment-instructions:: Full marks for: because the monitor is the same untrusted model as the policy, it can simply report that real backdoors look fine while telling the truth about everything else, so until the blue team has some way to check the monitor's honesty its reports carry no safety value. Deduct if the learner attributes the failure to the monitor being bad at spotting backdoors, which is the opposite of the situation: GPT-4 is very good at spotting them.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

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
assessment-instructions:: Full marks for both. As the defer percentage rises the point moves up and to the left: safety climbs from 62% to 100% while usefulness falls from 97% to 51%. Pushing the frontier out is the opposite: a better method reaches points up and to the right of the existing curve, giving more safety at the same usefulness, or more usefulness at the same safety. Half marks for the direction without the contrast. Award credit for naming trusted editing as an example of the second, since Table 7 shows it Pareto dominating untrusted monitoring.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

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
