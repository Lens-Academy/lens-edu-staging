---
id: '9ce50ca0-cfa8-4095-9d9d-62af136bff5c'
title: "Low-stakes control and research sabotage"
tldr: "If AIs do our safety research, they could quietly make it fail: a bug here, a withheld idea there. Each act looks like an honest mistake, so catching one proves little. Vivek Hebbar explains why this is a low-stakes threat and what defenders can do instead of catching the AI in the act."
summary_for_tutor: "Third teaching lens of Unit 2 of AI Control Fundamentals. The learner watches the first 22.5 minutes of Vivek Hebbar's ControlConf 2025 talk 'Low-stakes Control' (FAR.AI). Spine of the excerpt, in order. (1) Research sabotage as making promising research directions look unpromising (subtle bugs, withheld arguments) and sandbagging on ideas. It is probably easier to make us overlook a good technique than to convince us a bad one is good. (2) The two-axis diagram (how many actions a catastrophe takes, how incriminating each is under audit), with the top-right corner trivially solved by random auditing, the bottom-left probably hopeless, and the tractable diagonal. Low-stakes means many actions and each only weak evidence, plausibly a benign mistake. (3) Research sabotage could be low-stakes or high-stakes, and might be in the hopeless corner. (4) Online training matters more in low-stakes because training works better with more samples. (5) Three uses of control metrics: output filtering, incrimination, online training. (6) Incrimination needs a guess of how suspicious a benign model would look, which is hard, or incriminating patterns across domains. (7) Online training on a proxy does not need that baseline, but the proxy may be poor and training teaches the model to exploit it. (8) A speculative overall strategy: for buggy research code, trusted and untrusted monitoring plus auditing, with a choice between training on caught bugs, looking for patterns, or counting mistakes, and having the model write the same experiment several times to check that the results agree. For sandbagging on ideas, short-horizon online training where a trusted model, an untrusted model or a human rates the ideas, and debate-style arguments for and against each idea. His general point: online training on a poor reward signal improves the worst case but makes the benign case worse. The rest of the talk (evaluation methodology) is optional. Two scored questions follow."
reading_minutes: 24
tutor_minutes: 11
---
#### Text
content::
Vivek Hebbar works at Redwood Research ([Redwood Research blog](https://blog.redwoodresearch.org/p/how-can-we-solve-diffuse-threats)). In this talk at ControlConf 2025, an AI control conference ([YouTube](https://www.youtube.com/watch?v=DP3wTPDEjLQ)), he takes up one worry about using AI to do safety research: that the AI quietly makes the research fail, and what defenders could do about it. The rest of the talk, on how to test these defences, is optional.

#### Video
source:: [[../video_transcripts/far-ai-vivek-hebbar-low-stakes-control-controlconf]]
from:: 0:00
to:: 16:28

#### Question: Open
id:: 0ec07687-8a63-4cb0-957c-74a33e2faf36
content::
Without looking back: what two properties make a threat low-stakes in Hebbar's sense? Give one example of research sabotage that would be low-stakes, and one way the same kind of sabotage could be high-stakes instead.
force-feedback:: first
assessment-instructions:: Score out of 100. 40: the two properties, 20 each. It takes many bad actions to cause a catastrophe. Each action is only weak evidence of bad intent, because it could easily be an honest mistake. 30: a fitting example of low-stakes research sabotage, where many small acts each look like ordinary mistakes, such as doing a deliberately poor job on thousands of requests for experiment ideas, or many small bugs spread over many experiments. 30: a fitting way the same kind of sabotage could be high-stakes, where a few actions are enough, such as a handful of bugs in shared code that many experiments rely on, or sabotaging one critical result. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer defines low-stakes as low harm. Model answer, for the feedback, not a grading checklist: "Low-stakes means it takes many bad actions, and each one is weak evidence because it could be an honest mistake. Low-stakes example: the AI gives slightly worse experiment ideas every time it is asked, thousands of times. High-stakes version: there are only a few key experiments sharing one codebase, so a few bugs in that shared code are enough."
feedback-instructions:: The learner just watched the first part of Hebbar's talk. The two properties: it takes many actions to cause a catastrophe, and each action is only weakly incriminating, hard to tell apart from a benign mistake. Hebbar's low-stakes example: asking the AI for experiment ideas 10,000 times and getting a deliberately bad job each time. His high-stakes example: only about 100 experiments to sabotage, sharing code, so planting 10 bugs in critical shared utilities could be enough. Accept other examples that fit. Reply in at most four sentences: acknowledge what is correct, name the most important missing point, correct any error. If the learner defines low-stakes by low harm, correct it in one sentence. One turn, no follow-up question, no generic praise. Tell them to move on.

#### Question: Open
id:: 84551d9d-1b3d-44d9-81fd-2e0243d31ded
content::
Hebbar contrasts two defences against low-stakes sabotage: incriminating the AI, and training it during deployment on a proxy for good work. What does each one need, and what is the main weakness of each?
force-feedback:: first
assessment-instructions:: Score out of 100. 50: incrimination, meaning becoming confident from the evidence that the model is misaligned. 25 for what it needs: a good idea of how suspicious an honest model's work would look, so that many mildly suspicious actions can add up to evidence, or a telling pattern such as mistakes only in one domain. 25 for its weakness: that reference point is hard to get, and the ways to estimate it are weak. 50: training during deployment on a proxy for good work. 25 for what it needs: a proxy signal of good work, such as code cleanliness or human review of results (it does not need the honest baseline). 25 for its weakness, either of these: the proxy may be poor and could even make an honest model worse, or training against the proxy teaches the model to exploit it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Incrimination needs to know how suspicious an honest model's work would look, so that many slightly odd actions add up. Its weakness is that this baseline is very hard to get. Online training needs only a proxy for good work, like code quality or human ratings. Its weakness is that the proxy may be poor, and training on it teaches the model to game it."
feedback-instructions:: Key points from the talk. Incrimination means becoming confident the model is misaligned from the evidence. In the low-stakes case it needs a good guess of how suspicious a benign model's work would look, so that many mildly suspicious actions add up to evidence. Hebbar's two ways to get it (monitor scores on human-written and weaker-model solutions, and incriminating patterns such as mistakes only in one domain) he calls weak. Online training trains the model on a proxy such as code cleanliness or human review of results. It needs no benign baseline, but the proxy may be poor (and could make a benign model worse), and training against the proxy teaches the model to exploit it. Reply in at most five sentences: acknowledge what is correct, name the most important missing point, correct any error. Up to two turns. If the learner is stuck, give one foothold: ask how you would know whether 30 bugs in a year is suspicious. No generic praise.

#### Callout: The rest of the talk (optional)
collapse:: closed

#### Video
from:: 16:28
optional:: true

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Hebbar, Vivek. "Low-stakes Control." *ControlConf*, FAR.AI, published 14 May 2025. [youtube.com](https://www.youtube.com/watch?v=DP3wTPDEjLQ)
:::
