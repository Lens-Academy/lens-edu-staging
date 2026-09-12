---
id: 'f7fc3c2c-c3a6-49bc-888c-caf2062cd9ba'
slug: xlab-control-p1-d1
title: "Why control"
tags:
  - work-in-progress
---
%% Day 1 of AI Control Part 1 (five-day split of XLab's seven-module track, September 2026). Core self-study 217 minutes. Lens order follows XLab's track. %%

# Submodule: Welcome
# Lens: Welcome to XLab's AI Control course
id:: 661f1953-fa90-4ba5-a4b1-3e7aeb0c2d0a
reading_minutes:: 5
tutor_minutes:: 0
tldr:: No serious company assumes none of its employees will ever be compromised. It builds systems that hold when one is. AI control asks what happens if you treat a frontier model the same way: stop trying to prove it is safe, assume it is scheming, and design so that it still cannot hurt you.
summary_for_tutor:: Opening lens of AI Control Part 1, written by Lens rather than adapted from XLab (XLab's track has no welcome lesson). It motivates control as the second line of defense behind alignment: alignment tries to make the model not want to hurt you, control assumes that failed and asks what holds anyway. Key framing the learner meets here and will need throughout: the insider-threat analogy, the claim that control is easier to evaluate than alignment because it reduces to a capability question, catching a model red-handed as a win condition, and the fact that this is a young literature the learner is reading close to the frontier. Closes with XLab's alpha notice, practical orientation (everything is native to Lens, times are ours and include exercises, the track is split into two five-day courses, some pages are optional), and one optional ungraded reflection. Do not grade the reflection; acknowledge it briefly and send them on.
#### Text
content::
Every serious organisation already runs on a version of this problem. Banks do not assume that no trader will ever go rogue, and hospitals do not assume that no member of staff will ever misuse a record. They assume someone eventually will, and they build systems that hold anyway: separation of duties, logging, audits, limits on what any one person can reach alone. The safety of the institution does not rest on everyone being trustworthy.

AI safety has mostly not worked that way. The dominant approach, alignment, tries to make the model actually want what we want, so that it never tries anything in the first place. That is worth pursuing. But it has an awkward property: you cannot easily check whether it worked. If a model behaves well in every test you run, that is consistent with the model being aligned, and it is also consistent with the model being smart enough to behave well in every test you run.

AI control starts from the other end. It assumes the model may be scheming, deliberately working against you while appearing to cooperate, and asks a different question: can we deploy it anyway, and get useful work out of it, without it being able to cause a catastrophe? Not "is this model safe?" but "does it matter if it isn't?"

That shift buys something concrete. Whether a model is aligned is a question about its intentions, which you cannot observe. Whether a model can defeat your safeguards is a question about its capabilities, which you can test: put a red team in the model's place, let them try their hardest to get something past you, and measure what happens. That is what makes control evaluable in a way alignment currently is not, and it is the argument the first lesson of this course makes in full.[^note-case]

There is a second thing control gives you that alignment does not, and it is easy to miss. Under control, catching the model trying something is not a failure. It is a win. The single hardest thing about scheming is that you never get proof, only ambiguity; a model caught red-handed converts that into evidence you can act on, and study, and use to catch the next attempt.[^note-catching]

None of this is settled. The founding paper is from December 2023, and much of what you will read here was published in the last two years, some of it as blog posts and preprints that are still being argued about. You will read researchers disagreeing with each other in public, and at least one lesson in this course is a direct argument that control research is a mistake. That is not a gap in the curriculum; it is the state of the field. Expect to form your own view rather than to receive one.

The people who work out which control measures actually hold, and which ones only look like they do, are unlikely to be a settled profession by the time it matters. Some of them will be people meeting this material for the first time.

[^note-case]: Both claims, that control and alignment are distinct lines of defense and that control is more evaluable because it reduces to a capability question, come from Greenblatt and Shlegeris, "The case for ensuring that powerful AIs are controlled", which is the next lesson.
[^note-catching]: From Greenblatt and Shlegeris, "Catching AIs red-handed", on Day 3.

#### Text
content::
:::callout {title="This is an alpha course" tone="amber"}
XLab is in alpha testing and running a small paid cohort to calibrate the course ahead of its official launch. The materials are open for anyone to use in the meantime. If you use them, XLab would appreciate you filling out [their feedback form](https://forms.gle/KkWcHkKh87pygDzw9); it helps them find issues before launch. This Lens edition follows [XLab's current public curriculum](https://aisafetytracks.com/tracks/control), and XLab expects the material to change substantially after the paid cohort.
:::

\## How to use this course

Everything is here. The readings, XLab's own explanations, its exercises and its interactive pieces are all on this page and the ones after it, so you never need to leave to do the work. Each lesson ends with a Works cited box linking the original sources, including the XLab lesson it was adapted from, if you want to go back to either.

Three things worth knowing before you start:

- **Two courses, five days each.** XLab's seven-module track is split into AI Control Part 1 and Part 2, roughly 22 hours each. Each day is about four to five hours of reading and exercises and ends with a group meeting.
- **The times are ours, not XLab's.** We estimated each lesson from what a learner actually does, including the exercises, rather than from a word count. They are longer than the figures on XLab's site, which price the reading alone.
- **Optional means optional.** A few lessons are marked optional. Follow curiosity rather than completeness.

#### Question: Open
id:: 729d6348-3399-440f-9826-ce753ce19e53
content:: Optional: write a short note now that you can look back on at the end of the course.

- Before reading anything: does "keep a possibly-adversarial, possibly-superhuman system contained and still get useful work out of it" strike you as tractable, or as hopeless?
- What would have to be true for you to change that answer?
optional:: true
assessment-instructions:: This is an ungraded, optional pre-course reflection. Acknowledge it in two or three sentences, reflect back the specific intuition they expressed without endorsing or correcting it, and note that the course will give them evidence on it (Day 1 makes the case for control, and Day 3 includes the case against). Do not preview the arguments. Do not ask a follow-up question. Close by sending them to the first lesson. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *Redwood Research blog*, 24 Jan. 2024. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/the-case-for-ensuring-that-powerful)
*The source of the control-versus-alignment framing and of the argument that control is easier to evaluate. It is the next lesson in this module.*

Greenblatt, Ryan, and Buck Shlegeris. "Catching AIs red-handed." *Redwood Research blog*, 7 May 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/catching-ais-red-handed)
*The source of the claim that catching a model is a win condition rather than a failure. It is a lesson on Day 3.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The founding paper, and the origin of the December 2023 date. It opens Day 2.*

XLab. "AI Control." *Tracks*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control)
*The curriculum this course adapts. XLab's track has no welcome lesson of its own; this page is ours.*
:::

# Submodule: Day 1
# Lens: Day 1 overview
id:: 98d6d5d2-65a6-4661-8bce-1cfd186745fc
reading_minutes:: 2
tutor_minutes:: 0
#### Text
content::
\## Day 1: Why control

Why assume a frontier model may be scheming and design so it still cannot hurt you: the case for control as a second line of defense behind alignment, and attack trees as the way to think about what a model could do to you.

About 3.6 hours of reading and exercises.

# Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais]]

# Lens:
source:: [[../Lenses/XLab Control - attack-trees]]

