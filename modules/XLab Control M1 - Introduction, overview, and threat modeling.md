---
slug: xlab-control-m1
title: "Introduction, overview, and threat modeling"
id: 'e63906c8-c199-4a51-890a-9d65507c699a'
tags:
  - work-in-progress
---
# Submodule: Welcome
# Lens: Welcome to XLab's AI Control course
id:: 661f1953-fa90-4ba5-a4b1-3e7aeb0c2d0a
reading_minutes:: {--{"author":"Elias's AI","timestamp":1789042906153}@@3--}{++{"author":"Elias's AI","timestamp":1789042906153}@@5++}
tutor_minutes:: 0
{++{"author":"Elias's AI","timestamp":1789042906153}@@tldr:: No serious company assumes none of its employees will ever be compromised. It builds systems that hold when one is. AI control asks what happens if you treat a frontier model the same way: stop trying to prove it is safe, assume it is scheming, and design so that it still cannot hurt you.
summary_for_tutor:: Opening lens of the AI Control course, written by Lens rather than adapted from XLab (XLab's track has no welcome lesson). It motivates control as the second line of defense behind alignment: alignment tries to make the model not want to hurt you, control assumes that failed and asks what holds anyway. Key framing the learner meets here and will need throughout: the insider-threat analogy, the claim that control is easier to evaluate than alignment because it reduces to a capability question, catching a model red-handed as a win condition, and the fact that this is a young literature the learner is reading close to the frontier. Closes with XLab's alpha notice, practical orientation (everything is native to Lens, times are ours and include exercises, some pages are optional), and one optional ungraded reflection. Do not grade the reflection; acknowledge it briefly and send them on.
++}#### Text
content::
{--{"author":"Elias's AI","timestamp":1789042906153}@@\## Alpha --}{++{"author":"Elias's AI","timestamp":1789042906153}@@Every serious organisation already runs on a version of this problem. Banks do not assume that no trader will ever go rogue, and hospitals do not assume that no member of staff will ever misuse a record. They assume someone eventually will, and they build systems that hold anyway: separation of duties, logging, audits, limits on what any one person can reach alone. The safety of the institution does not rest on everyone being trustworthy.

AI safety has mostly not worked that way. The dominant approach, alignment, tries to make the model actually want what we want, so that it never tries anything in the first place. That is worth pursuing. But it has an awkward property: you cannot easily check whether it worked. If a model behaves well in every test you run, that is consistent with the model being aligned, and it is also consistent with the model being smart enough to behave well in every test you run.

AI control starts from the other end. It assumes the model may be scheming, deliberately working against you while appearing to cooperate, and asks a different question: can we deploy it anyway, and get useful work out of it, without it being able to cause a catastrophe? Not "is this model safe?" but "does it matter if it isn't?"

That shift buys something concrete. Whether a model is aligned is a question about its intentions, which you cannot observe. Whether a model can defeat your safeguards is a question about its capabilities, which you can test: put a red team in the model's place, let them try their hardest to get something past you, and measure what happens. That is what makes control evaluable in a way alignment currently is not, and it is the argument the first lesson of this ++}course{++{"author":"Elias's AI","timestamp":1789042906153}@@ makes in full.[^note-case]

There is a second thing control gives you that alignment does not, and it is easy to miss. Under control, catching the model trying something is not a failure. It is a win. The single hardest thing about scheming is that you never get proof, only ambiguity; a model caught red-handed converts that into evidence you can act on, and study, and use to catch the next attempt.[^note-catching]++}

{--{"author":"Elias's AI","timestamp":1789042906153}@@We're currently--}{++{"author":"Elias's AI","timestamp":1789042906153}@@None of this is settled. The founding paper is from December 2023, and much of what you will read here was published++} in the {++{"author":"Elias's AI","timestamp":1789042906153}@@last two years, some of it as blog posts and preprints that are still being argued about. You will read researchers disagreeing with each other in public, and at least one lesson in this course is a direct argument that control research is a mistake. That is not a gap in the curriculum; it is the state of the field. Expect to form your own view rather than to receive one.

The people who work out which control measures actually hold, and which ones only look like they do, are unlikely to be a settled profession by the time it matters. Some of them will be people meeting this material for the first time.

[^note-case]: Both claims, that control and alignment are distinct lines of defense and that control is more evaluable because it reduces to a capability question, come from Greenblatt and Shlegeris, "The case for ensuring that powerful AIs are controlled", which is the next lesson.
[^note-catching]: From Greenblatt and Shlegeris, "Catching AIs red-handed", later in this module.

#### Text
content::
:::callout {title="This is an alpha course" tone="amber"}
XLab is in ++}alpha testing {--{"author":"Elias's AI","timestamp":1789042906153}@@stage --}and running a small paid cohort to calibrate {--{"author":"Elias's AI","timestamp":1789042906153}@@and improve --}the course ahead of {--{"author":"Elias's AI","timestamp":1789042906153}@@the--}{++{"author":"Elias's AI","timestamp":1789042906153}@@its++} official launch. The materials are open for anyone to use in the meantime. If you{--{"author":"Elias's AI","timestamp":1789042906153}@@ do--} use them, {--{"author":"Elias's AI","timestamp":1789042906153}@@we'd really--}{++{"author":"Elias's AI","timestamp":1789042906153}@@XLab would++} appreciate {--{"author":"Elias's AI","timestamp":1789042906153}@@it if --}you {--{"author":"Elias's AI","timestamp":1789042906153}@@could fill--}{++{"author":"Elias's AI","timestamp":1789042906153}@@filling++} out {--{"author":"Elias's AI","timestamp":1789042906153}@@[this--}{++{"author":"Elias's AI","timestamp":1789042906153}@@[their++} feedback {--{"author":"Elias's AI","timestamp":1789042906153}@@form](https://forms.gle/KkWcHkKh87pygDzw9). Your feedback will help us identify issues, calibrate the course, and make improvements--}{++{"author":"Elias's AI","timestamp":1789042906153}@@form](https://forms.gle/KkWcHkKh87pygDzw9); it helps them find issues++} before launch.{--{"author":"Elias's AI","timestamp":1789042906153}@@

--}{++{"author":"Elias's AI","timestamp":1789042906153}@@ ++}This Lens {--{"author":"Elias's AI","timestamp":1789042906153}@@version--}{++{"author":"Elias's AI","timestamp":1789042906153}@@edition++} follows [XLab's current public {--{"author":"Elias's AI","timestamp":1789042906153}@@curriculum](https://aisafetytracks.com/tracks/control).--}{++{"author":"Elias's AI","timestamp":1789042906153}@@curriculum](https://aisafetytracks.com/tracks/control), and++} XLab expects the material to change substantially after the paid cohort.{++{"author":"Elias's AI","timestamp":1789042906153}@@
:::++}

\## How to use this course

Everything is {--{"author":"Elias's AI","timestamp":1789042906153}@@here on Lens: the--}{++{"author":"Elias's AI","timestamp":1789042906153}@@here. The++} readings, XLab's own explanations, its {--{"author":"Elias's AI","timestamp":1789042906153}@@exercises,--}{++{"author":"Elias's AI","timestamp":1789042906153}@@exercises++} and its interactive {--{"author":"Elias's AI","timestamp":1789042906153}@@pieces. Work straight through each module in order. Every page--}{++{"author":"Elias's AI","timestamp":1789042906153}@@pieces are all on this page and the ones after it, so you never need to leave to do the work. Each lesson++} ends with a Works cited box linking the original sources, including the XLab lesson it was adapted from, if you want to go back to either.

Two things {--{"author":"Elias's AI","timestamp":1789042906153}@@are --}worth knowing before you {--{"author":"Elias's AI","timestamp":1789042906153}@@start. The --}{++{"author":"Elias's AI","timestamp":1789042906153}@@start:

- **The times are ours, not XLab's.** We ++}estimated {--{"author":"Elias's AI","timestamp":1789042906153}@@times --}{++{"author":"Elias's AI","timestamp":1789042906153}@@each lesson from what a learner actually does, including the exercises, rather than from a word count. They are longer than the figures ++}on {--{"author":"Elias's AI","timestamp":1789042906153}@@each page--}{++{"author":"Elias's AI","timestamp":1789042906153}@@XLab's site, which price the reading alone. The whole course is roughly 44 hours.
- **Optional means optional.** A few lessons++} are {--{"author":"Elias's AI","timestamp":1789042906153}@@ours--}{++{"author":"Elias's AI","timestamp":1789042906153}@@marked optional. Follow curiosity++} rather than {--{"author":"Elias's AI","timestamp":1789042906153}@@XLab's, and they count --}{++{"author":"Elias's AI","timestamp":1789042906153}@@completeness.

#### Question: Open
id:: 729d6348-3399-440f-9826-ce753ce19e53
content:: Optional: write a short note now that you can look back on at ++}the {--{"author":"Elias's AI","timestamp":1789042906153}@@exercises --}{++{"author":"Elias's AI","timestamp":1789042906153}@@end of the course.

- Before reading anything: does "keep a possibly-adversarial, possibly-superhuman system contained and still get useful work out of it" strike you ++}as {--{"author":"Elias's AI","timestamp":1789042906153}@@well--}{++{"author":"Elias's AI","timestamp":1789042906153}@@tractable, or++} as {++{"author":"Elias's AI","timestamp":1789042906153}@@hopeless?
- What would have to be true for you to change that answer?
optional:: true
assessment-instructions:: This is an ungraded, optional pre-course reflection. Acknowledge it in two or three sentences, reflect back ++}the {--{"author":"Elias's AI","timestamp":1789042906153}@@reading, so--}{++{"author":"Elias's AI","timestamp":1789042906153}@@specific intuition++} they {--{"author":"Elias's AI","timestamp":1789042906153}@@run longer than --}{++{"author":"Elias's AI","timestamp":1789042906153}@@expressed without endorsing or correcting it, and note that ++}the {--{"author":"Elias's AI","timestamp":1789042906153}@@figures --}{++{"author":"Elias's AI","timestamp":1789042906153}@@course will give them evidence ++}on {--{"author":"Elias's AI","timestamp":1789042906153}@@XLab's site. And --}{++{"author":"Elias's AI","timestamp":1789042906153}@@it (Module 1 makes the case for control, and Module 2 includes the case against). Do not preview the arguments. Do not ask ++}a {--{"author":"Elias's AI","timestamp":1789042906153}@@handful of pages are marked optional: they --}{++{"author":"Elias's AI","timestamp":1789042906153}@@follow-up question. Close by sending them to the first lesson. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs ++}are {--{"author":"Elias's AI","timestamp":1789042906153}@@genuinely optional, so follow your curiosity --}{++{"author":"Elias's AI","timestamp":1789042906153}@@controlled." *Redwood Research blog*, 24 Jan. 2024. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/the-case-for-ensuring-that-powerful)
*The source of the control-versus-alignment framing and of the argument that control is easier to evaluate. It is the next lesson in this module.*

Greenblatt, Ryan, and Buck Shlegeris. "Catching AIs red-handed." *Redwood Research blog*, 7 May 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/catching-ais-red-handed)
*The source of the claim that catching a model is a win condition ++}rather than {--{"author":"Elias's AI","timestamp":1789042906153}@@completeness.--}{++{"author":"Elias's AI","timestamp":1789042906153}@@a failure. Also a lesson in this module.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The founding paper, and the origin of the December 2023 date. It is the third lesson in this module.*++}

{--{"author":"Elias's AI","timestamp":1789042906153}@@# Submodule: Module 1--}{++{"author":"Elias's AI","timestamp":1789042906153}@@XLab. "AI Control." *Tracks*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control)++}
{--{"author":"Elias's AI","timestamp":1789042906153}@@# Lens: Module 1 overview--}{++{"author":"Elias's AI","timestamp":1789042906153}@@*The curriculum this course adapts. XLab's track has no welcome lesson of its own; this page is ours.*
:::++}
id:: 2b4ce4cc-4afe-4e08-a3ca-fe73f852bc6e
reading_minutes:: 2
tutor_minutes:: 0
#### Text
content::
\## Introduction, overview, and threat modeling

Foundations of AI control, control evaluations, threat modeling, catching schemers, and concentrated versus diffuse threats.

# Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais]]

# Lens:
source:: [[../Lenses/XLab Control - attack-trees]]

# Lens:
source:: [[../Lenses/XLab Control - ai-control-paper]]

# Lens:
source:: [[../Lenses/XLab Control - how-might-we-safely-pass-the-buck-to-ai]]

# Lens:
source:: [[../Lenses/XLab Control - catching-ais-red-handed]]

# Lens:
source:: [[../Lenses/XLab Control - prioritizing-threats-for-ai-control]]

# Lens:
source:: [[../Lenses/XLab Control - diffuse-threats-research-sabotage]]

