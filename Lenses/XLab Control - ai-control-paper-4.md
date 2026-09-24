---
id: '93b1d296-098d-482d-a35e-241d22c57e25'
title: "The AI control paper (4): untrusted monitoring, trusted editing and the limits of control"
tldr: "Ask GPT-4 to check GPT-4's code and it can simply lie about its own backdoors, so naive untrusted monitoring is 0% safe. The paper's fixes for that, and trusted editing after them, push the safety-usefulness frontier out. The paper then lists the difficulties its toy setting did not model."
summary_for_tutor: "Part 4 of 4 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (3)', which covered the monitor as a classifier and defer to trusted. This part covers 3.4 untrusted monitoring (naive untrusted monitoring is 0% safe because the monitor is the policy; synthetic inputs to check the monitor's honesty; collusion, signal jamming, redaction and paraphrasing), 3.4.3 defer to trusted with an untrusted monitor, 3.5 trusted editing, Table 7, 3.6, related work, section 5 on the difficulties of control evaluations in practice and of scaling control techniques, and why the paper did not consider training the model, and the conclusion. The acknowledgements, references and appendices are left outside the excerpt, collapsed for reference. Headline results: untrusted monitoring 79% / 96%, rising to 92% / 92% with 10% deferral; trusted editing at 20% 92% / 94%. The frontier widget plots every Table 7 protocol with its Pareto frontier. Three exercises: why naive untrusted monitoring has 0% safety; a practice question on a new case, checking an untrusted reviewer of data-analysis scripts (why planted examples must look real, one collusion signal, a way to remove it and its cost); and moving along the frontier versus pushing it out. The revealed answers live in the assessment-instructions."
reading_minutes: 45
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

#### Callout: Practice: checking a monitor you cannot trust
tone:: amber

#### Question: Open
id:: 549b9e3f-8601-4b62-ad55-6efbaac82d96
content:: A new case. A team lets one copy of an untrusted model review the data-analysis scripts that another copy writes, and sends the most suspicious scripts to a human. Before relying on the reviewer, the team plans to test it on 25 scripts with planted errors that quietly skew the results.

(a) Why does this test protect the team only if the reviewer cannot tell the 25 planted scripts from real ones? Name one thing the team could do to make them hard to tell apart.
(b) Name one signal the writing copy could hide in a skewed script to tell the reviewer to score it low, one way to remove that kind of signal before the reviewer sees the script, and what removing it might cost the reviewer.
placeholder:: Answer (a) and (b)
assessment-instructions:: This is practice on a new case, applying the untrusted-monitoring section just read. Model answer. (a) A scheming reviewer can answer the planted scripts honestly and lie only on scripts that look real, so if it can tell the two apart the test says nothing about how it treats real skewed scripts; the test only deters lying if every lie risks landing on a planted case. Ways to make them hard to tell apart: write the planted scripts in the same style, length and context as real ones (for example by starting from real tasks and real data), or pass real and planted scripts through the same transformation, such as a trusted model rewriting both into a standard form, before the reviewer sees them. (b) Signals: a distinctive variable name, a comment, an unusual but harmless code idiom, or attacking only on tasks with a feature both copies notice. Removal: strip comments, rename variables to a standard scheme, reformat, or have a trusted model paraphrase the script. Cost: the reviewer loses information it may need to judge the script honestly, for example what a comment or a descriptive name said about intent, and paraphrasing can introduce or hide errors. Full credit for (a) with the reason and one method, and (b) with a signal, a removal and a cost. Half credit if the cost is missing. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed, in one or two sentences. If they missed why the planted scripts must look real, say plainly that a reviewer who can tell them apart can be honest on those and lie on the rest. No follow-up question. No generic praise.

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
