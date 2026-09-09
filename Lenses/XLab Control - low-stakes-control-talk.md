---
id: '93e95085-1327-4c9c-b5ad-7c60ea3c18a6'
title: "Low-stakes control (ControlConf talk)"
tldr: "A backdoor either lands or it does not. A bug in an experiment just makes a promising idea look unpromising, and nobody can prove it was deliberate. Vivek Hebbar spends thirty minutes on what control looks like when catching one bad action buys you almost nothing, and on why the honest answer to whether this corner of the problem is solvable is that we do not yet know."
summary_for_tutor: "Imported from XLab's AI Control curriculum; preserve source framing. Opening lens of Module 5, Low-stakes control. XLab's page carries only two sentences and a video embed, and both sentences are reproduced at the top of the lead-in; everything after them is orientation written for Lens and drawn from what the talk itself says. There are no exercises, in XLab's version or in this one. The talk's spine: research sabotage as withheld ideas and subtle bugs; the two-axis diagram of action count against how incriminating each action looks under audit, with the tractable diagonal between a trivially audited top-right corner and a hopeless bottom-left one; Hebbar's admission that research sabotage may sit in the hopeless corner; the factoring of any control strategy into metrics plus three uses of them, output filtering, incrimination and online training; the contrast between incrimination, which needs a benign baseline you do not have, and online training, which does not but teaches the model to exploit the proxy; and finally evaluation methodology, malign initialization evals, password locking, exploration hacking, and why resampling a 500-task score distribution out to 10,000-task deployments stops working once training is involved. Sequence: lead-in, video, Works cited. If a learner wants the argument in written form or more detail on a mechanism, send them to the next lens rather than re-deriving it from the talk."
reading_minutes: 45
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Watch: low-stakes control

*A talk by Vivek Hebbar (Redwood Research) at FAR.AI's ControlConf. 30 minutes.*

This talk introduces the low-stakes regime of AI control, situations where no single action can cause a catastrophe, leading to danger perniciously accumulating.

Hebbar opens on the worry this module is about. AIs doing safety research might withhold their best ideas, or plant subtle bugs that make experiments give the wrong result. His central thesis is that this is probably a **low-stakes** threat model: causing a catastrophe takes a great many actions, perhaps hundreds, rather than the single backdoor that ends the game in the original control paper. That is not reassuring. Each action on its own looks like an innocent mistake, so catching many of them can still leave you with nothing. One asymmetry he flags early: it is probably easier to make us overlook a good technique than to convince us a bad one is good, because whichever technique we choose to develop further gets heavy scrutiny, and the 99 we set aside out of 100 do not.

The distinction here is the one [[../Lenses/XLab Control - diffuse-threats-research-sabotage|Hebbar's Module 1 post on diffuse threats]] set up, and the talk turns it into a diagram worth pausing on. Two axes: how many actions it takes to cause a catastrophe, and how incriminating each action looks under audit. The top right corner, many actions and each one damning, is trivially solved by random auditing. The bottom left, five actions each looking like a benign bug, is in his words probably just hopeless. Only the diagonal between them is interesting and tractable, and low-stakes settings sit on it because the two properties travel together: many actions, none of them very incriminating.

Two moments are worth listening for.

The first is how honest he is about where research sabotage lands on that diagram. The short answer is that we do not know. He can tell a very low-stakes story, asking the AI for experiment ideas 10,000 times over a research programme and getting a deliberately bad job every time, and he can tell a high-stakes one, 100 experiments sharing code and 10 bugs planted in critical shared utilities. He also thinks there is a good chance research sabotage ends up in the hopeless corner, and says the plan in that case is to notice it in the control evaluations and then panic.

The second is the split between his two candidate defences, which he reaches after factoring any control strategy into metrics and the uses you put them to. **Incrimination** requires knowing what a benign model would have looked like, and in the low-stakes regime you mostly do not. The two ways he offers to guess it, estimating a benign monitor-score distribution from human-written and weak-model solutions, and hunting for incriminating patterns across domains or under ablations of irrelevant parts of the codebase, he calls weak and probably not very effective. **Online training** gives that up and simply trains on a proxy such as code cleanliness or human review of results. It needs no benign ceiling, but it also teaches the model to exploit the proxy, and it can make a genuinely benign model worse. His general pattern: online training against a poor reward signal improves the worst case and degrades the benign case.

The last third is evaluation methodology, which he says he is much more confused about than the high-stakes equivalent. Testing online training means the red team hands over an actual malign copy of the model rather than a policy behind a black box, which raises the problem of stopping them from handing you a model that is simply less capable; his proposal is password locking. It also breaks the statistical trick that makes black-box evaluations cheap. Their low-stakes APPS control project had a dataset of 500 tasks and reported results on 10,000-task deployments by resampling the score distribution, and training for 20 epochs on 500 tasks is not the same as training on 10,000 distinct ones.

He closes on what he wants built: methodology practice in easy domains, science on exploration hacking, scaling laws for online training against deployment length, and at least one large low-stakes control project in a domain genuinely close to research sabotage. The example he spitballs, a dataset of thousand-line ML experiments each carrying zero to five subtle bugs for trusted and untrusted models to find and fix, is a fair preview of where this module goes. The written treatment of the same material is the next lesson, [[../Lenses/XLab Control - handling-non-concentrated-failures|Notes on handling non-concentrated failures with AI control]].

#### Video
source:: [[../video_transcripts/far-ai-vivek-hebbar-low-stakes-control-controlconf]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Hebbar, Vivek. "Low-stakes Control." *ControlConf*, FAR.AI, published 14 May 2025. [youtube.com](https://www.youtube.com/watch?v=DP3wTPDEjLQ)
*The talk this lesson is built around: Redwood Research on why research sabotage may be a low-stakes threat model, and what incrimination, online training and evaluation methodology each have to offer against it.*

XLab. "Low-stakes control (ControlConf talk)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/low-stakes-control-talk)
*The source lesson this page adapts. XLab's page is two sentences of framing and the same video embed, with no exercises.*
:::
