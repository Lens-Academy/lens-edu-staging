---
id: '0d1bf136-6960-4c3f-83f6-faab584e3616'
title: "How can we solve diffuse threats like research sabotage with AI control?"
tldr: "One subtle bug in an experiment is something you could never prove was malice. A thousand subtle bugs is still not proof, but now you have a thousand training examples to work with. That trade is what separates concentrated failures from diffuse ones, and it decides which of your two defences, online training or incrimination, has any grip at all."
summary_for_tutor: "Unit 3 of AI Control 1; closes the threat half of the unit. The reading is Vivek Hebbar's Redwood post on diffuse threats, embedded in three Article excerpts. Sequence: (1) the setup, where research sabotage is defined and the diffuse/concentrated distinction is introduced, followed by two recall questions (what research sabotage is, the two properties of a diffuse threat model); (2) the deployer's two hopes, online training and incrimination, and the Pareto frontier between action count and action sneakiness, followed by a recall question on why incrimination fails at the diffuse end; (3) the remaining mitigation regimes, the sabotage strategies section, and Hebbar's open terminology question, followed by a practice question (added September 2026) that places three new cases on the spectrum, one at each end and one in the middle, and matches each to incrimination, untargeted training or training harder on suspicious outputs; its model answer is in the assessment-instructions. Then an editorial note on how Redwood's terminology settled, and a forward pointer to where the two ends are taken up: Unit 4 of AI Control 1 for the concentrated end, AI Control 2 for the diffuse end. The three recall questions are tap-reveal cards; grade them against the answers in the briefs, do not hand the answer over before the learner attempts it. If a learner conflates 'diffuse' with 'low-severity', the fix is action count and evidence per action, not stakes."
reading_minutes: 25
tutor_minutes: 5
tags: []
---
#### Article
source:: [[../articles/hebbar-how-can-we-solve-diffuse-threats-like-research-sabotage-with-ai-control]]
to:: Our question:Can we make this research go well, even if the AI agents doing the research want it to go poorly?

#### Question: Open
id:: cea44f81-747a-42fd-9a7e-783b08f2dde6
content:: What is research sabotage?
assessment-instructions:: The learner has just read the opening of Hebbar's post and is answering from memory. Full credit for an answer that says research sabotage is misaligned AIs making safety research go poorly, and names at least one of the post's mechanisms: withholding their best ideas, or putting subtle bugs in experiments. Partial credit if the mechanism is there but the intent is missing, or the reverse. Grade only against the material this page supplied.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: baeca979-c275-48a9-9d12-aaf0736ede11
content:: What two properties define a "diffuse" threat model?
assessment-instructions:: Full credit requires both properties: catastrophe requires numerous bad actions, and each bad action is only weak evidence of malign intent when investigated. Half credit for one of the two. An answer that describes diffuse threats as low-severity or low-stakes rather than many-actions-plus-weak-evidence has the wrong distinction. Grade only against the material this page supplied.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: ## Deployer strategies: Training and incrimination
to:: Therefore incrimination is only promising for the top left region (near the “concentrated failures” end of the spectrum).

#### Question: Open
id:: 7dd62651-6bd9-497a-98d0-93eecbde2abf
content:: Why does incrimination fail at the diffuse end of the spectrum?
assessment-instructions:: Full credit for an answer that gets the missing affordance: incriminating a model from a large volume of mildly suspicious actions would require knowing exactly how suspicious a benign model would look, and without that baseline no amount of mildly suspicious actions is enough. Partial credit for "each action is individually too weak" without the point about the benign baseline. An answer that says the actions are simply undetectable misses that they are detected, just not distinguishable from honest mistakes. Grade only against the material this page supplied.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: **Untargeted online training:**

#### Callout: Practice: where on the spectrum?
tone:: amber

#### Question: Open
id:: 244d671b-02e3-4a48-a366-1a0e71fd9e96
content:: Three new cases. A model that may be scheming could try any of these:

(a) During one routine deployment, it swaps the weights file the inference server loads for a copy it has quietly modified.
(b) Over months of writing interpretability code for a safety team, it regularly leaves out the follow-up experiments that would have been most informative.
(c) In about thirty of the few thousand code reviews it does in a year, it approves a change containing a bug that a careful reviewer would sometimes have caught.

For each, say where it sits between concentrated and diffuse, and which mitigation has the most grip on it: incrimination, training on the model's outputs evenly, or training harder on its most suspicious outputs. Say why the others have less.
placeholder:: Take (a), (b), then (c)
assessment-instructions:: This is practice on three new cases, applying the reading. Model answer. (a) Concentrated: one action, and swapping in a modified weights file is highly incriminating if seen. Incrimination has grip: flag and hold such actions for review before they take effect, and a confirmed instance is strong evidence of intent. Training has little grip: there is one example at most, and the harm is done before training could act. (b) Diffuse: it needs many actions, and each omission is at most weak evidence, since leaving out an experiment looks like an honest judgement call. Training has more grip: training on a signal of research quality across all of its work uses the many samples. Incrimination has little grip: without knowing how often an honest model would leave out such experiments, no number of mildly suspicious omissions proves intent. (c) In the middle: dozens of actions, each mildly to moderately suspicious (a missed bug is often an honest miss, but some are the kind a careful reviewer would flag). Training harder on the most suspicious reviews has the most grip: a monitor can pick out the reviews where approved bugs look worst and the model can be trained hardest on those, which works where bad actions are too rare among all reviews for even training to have much effect. Incrimination is weak, since each miss is plausibly honest, though a pattern across many misses might become evidence if one knew how often an honest reviewer misses such bugs; evenly spread training has too few bad examples among thousands of reviews. Full credit for all three placements by action count and incrimination per action, the matching mitigation for each, and a reason the others fail. Half credit if the placements are right but the reasons for the failing mitigations are missing. If the learner sorts by how harmful each is, say that the axis is how many actions are needed and how incriminating each is. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed. If they sorted by harm, say plainly that the axis is action count and evidence per action. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Note on terminology" tone="blue"}
This post uses "concentrated"/"diffuse" to describe failures involving few or many actions, while explicitly noting that this wasn't settled. Earlier Redwood writing used "auditing failures," "distributed threats," and "[[../Lenses/XLab Control - handling-non-concentrated-failures|non-concentrated failures]]" for the diffuse category, and in conversation Redwood had mostly used "high-stakes"/"low-stakes", a pair they avoided in writing because "low-stakes" confuses readers unfamiliar with Paul Christiano's [low-stakes alignment](https://www.alignmentforum.org/posts/TPan9sQFuPP6jgEJo/low-stakes-alignment) decomposition, from which the pair descends (Redwood's 2022 adversarial-training project was already framed as "high-stakes alignment"). This post closes by polling readers on which pair to use going forward, but since writing, Redwood's usage has mostly become standardized:

- **For failures and threats themselves: "concentrated" vs. "diffuse."** A *concentrated* failure is one where catastrophe arrives in so few actions or so short a time window ("latency-concentrated") that auditing never gets a look before it's too late; each bad action is highly incriminating if caught. A *diffuse* failure is one where catastrophe requires many actions over a long horizon, each of which looks only weakly suspicious under investigation (research sabotage, sandbagging).
- **For the two subfields of control: "high-stakes control" and "diffuse control."** That is, "high-stakes" won on the concentrated side and "diffuse" won on the other, which is asymmetric, but both are short adjectives that compose well ("diffuse control team," "high-stakes control setting"). "Concentrated control" and "low-stakes control" did not catch on in writing.
:::

\## Where this goes next

The concentrated/diffuse split is the seam the rest of the curriculum is cut along. The concentrated end starts in Unit 4, with [[../Lenses/XLab Control - high-stakes-control-talk|The high-stakes control roadmap]]. The diffuse end is in AI Control 2, whose first unit covers [[../Lenses/XLab Control - low-stakes-control-talk|Low-stakes control]] and then takes up the sibling of this reading, [[../Lenses/XLab Control - handling-non-concentrated-failures|Notes on handling non-concentrated failures with AI control]].

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Hebbar, Vivek. "How can we solve diffuse threats like research sabotage with AI control?" *Redwood Research blog*, 30 Apr. 2025. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/how-can-we-solve-diffuse-threats)
*The reading for this lens: the post that introduces the concentrated-to-diffuse spectrum and argues that online training and incrimination cover opposite ends of it.*

Christiano, Paul. "Low-stakes alignment." *AI Alignment Forum*, 30 Apr. 2021. [alignmentforum.org](https://www.alignmentforum.org/posts/TPan9sQFuPP6jgEJo/low-stakes-alignment)
*The decomposition the "high-stakes"/"low-stakes" pair descends from, and the reason Redwood avoided that pair in writing.*

XLab. "How can we solve diffuse threats like research sabotage with AI control?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/diffuse-threats-research-sabotage)
*The source lesson this page adapts.*
:::
