---
title: "Product Alignment is not Superintelligence Alignment (and we need the latter to survive)"
author:
  - "plex"
source_url: "https://www.lesswrong.com/posts/mrwYCNocXCP2hrWt8/product-alignment-is-not-superintelligence-alignment-and-we"
published: 2026-03-31
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "tl;dr: progress on making Claude friendly[1] is not the same as progress on making it safe to build godlike superintelligence. solving the former doe…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_tl;dr: progress on making Claude friendly_[^note-1] _is not the same as progress on making it safe to build godlike superintelligence. solving the former does not imply we get a good future._[^note-2] _please track the difference._

_\[edit: terminology note:_ [_Local vs Asymptotic Alignment_](https://www.lesswrong.com/posts/mrwYCNocXCP2hrWt8/product-alignment-is-not-superintelligence-alignment-and-we?commentId=cNkmPHdsPjfM7bj6o) _would capture the thing I'm trying to say more crisply and cooperatively_, _though less memetically. I haven't been staring at this as much as_ [_@the gears to ascension_](https://www.lesswrong.com/users/the-gears-to-ascension?mention=user) _so I could not quickly write that post, but if you can generate the right concepts from the title that's even better\]_

The term 'Alignment' was coined[^note-3] to point to the technical problem of understanding how to build minds such that if they were to become strongly and generally superhuman, things would go well.

It has been increasingly adopted by frontier AI labs and much of the rest of the AI safety community to mean a much easier challenge, something like "having AIs that are empirically doing approximately what you ask them to do".[^note-4]

If it's possible to use an intent-aligned product to build a research system which discovers a new paradigm and breaks your guardrails, then it is not Aligned in the original sense.

If you can use your intent aligned system to write code which jailbreaks other LLMs and enables them to do dangerous ML research, it is also not Aligned in the original sense.

**Conflating progress on product alignment with progress on superintelligence alignment seems to be lulling much of the AI safety community into a false sense of security.**

## Why is Superintelligence Alignment less prominent? ^why-is-superintelligence-alignment

Because product alignment is:

-   Much closer to the scaling labs core expertise (ML) than theory (technical philosophy and math), so easier for them to hire for and evaluate
-   Has easier-to-use feedback loops: run an experiment, observe the results. Superintelligence alignment requires building enough theoretical understanding before running some kinds of experiment, because you might not be alive to see some results if your theory is wrong.
-   More profitable; progress on product alignment makes AI more useful right away[^note-5]
-   Easier for funders to fund; it's harder to evaluate who will make progress or what even counts as progress on superintelligence alignment theory than a domain where you'll reliably get publishable results from running an experiment

This is inconvenient!

It would be awesome if we could ride easy-to-evaluate profitable empirical feedback loops all the way to a great future. But this seems far from certain.[^note-6]

## Why do we need Superintelligence Alignment to survive? ^why-do-we-need

Reality is allowed to be inconvenient. There's strong reason to expect that superhuman situationally aware agents inside your experiment [breaks some of the foundations the scientific process relies upon,](https://www.lesswrong.com/posts/wustx45CPL5rZenuo/no-safe-defense-not-even-science) such as:

-   You can run roughly any experiment as often as you want to gather data and the world won't end because [the theory you were testing was wrong and you ran a too-strong agent](https://www.youtube.com/watch?v=D8RtMHuFsUw)
-   You won't have an intelligent adversary inside your experiment which is aware of you and faking data
-   Your experiment won't produce data which is super-humanly optimized to persuade you

In short: **Your experimental subject is not a neutral substrate, but a strategic actor more capable than you.**

If we don't have guarantees of maintaining safety properties each time a model builds the next rung on the capability ladder, we're rolling a dice for irreversible guardrail decay.[^note-7] And we're going to be very rapidly rolling huge numbers of those dice and the feedback loop spins up.

As we're headed up [the exponential](https://theaidigest.org/time-horizons), we're going to need techniques which generalize to strongly superhuman agents – ones which correctly believe they could defeat all of humanity. Product-aligned AIs _might_ help with that work, but the type of research they would need to automate needs to look more like [technical philosophy](https://www.lesswrong.com/posts/7uTPrqZ3xQntwQgYz/anthropic-and-taking-technical-philosophy-more-seriously) and reliably avoiding [slop](https://www.lesswrong.com/posts/8wBN8cdNAv3c7vt6p/the-case-against-ai-control-research#The_Median_Doom_Path__Slop__not_Scheming), not just avoiding scheming and passing product-alignment benchmarks.[^note-8]

Only a tiny fraction of the field of AI safety is focused on these big picture bottlenecks,[^note-9] due to a mix of funding incentives and it being more rewarding for most people to do empirical science.[^note-10]

---

**When you see people enthusiastically talking about how much progress we have on 'Alignment', please track (and ask!) whether they're talking about aligning products or aligning superintelligence****.**

[^note-1]: If you're friends with Claude, please read and consider this post first: [Protecting humanity and Claude from rationalization and unaligned AI](https://www.lesswrong.com/posts/2p6dD35h38X5fw85G/protecting-humanity-and-claude-from-rationalization-and)
[^note-2]: This is not to say _product alignment can't help_ or _there is no path to victory which goes through product alignment_, just that you need to solve a different problem (superintelligence alignment) at some stage of your plan.
[^note-3]: I think by [Stuart Russell](https://web.archive.org/web/20160210144144/https://www.fhi.ox.ac.uk/edge-article/) in ~2014.
[^note-4]: Sometimes with self-awareness of this history, like Paul's [Intent Alignment](https://ai-alignment.com/clarifying-ai-alignment-cec47cd69dd6), but that's increasingly rare.
[^note-5]: Getting Product-Aligned AI is a convergent subgoal of many possible goals, and [ultimate ends may be easily hidable behind convergent subgoals](https://www.lesswrong.com/posts/8qCKZj24FJotm3EKd/ultimate-ends-may-be-easily-hidable-behind-convergent)
[^note-6]: And even if possible in theory, practice by the current players under race conditions looks far from the level of competence needed to actually pull it off.
[^note-7]: Capabilities generalize in a way alignment doesn't because reality gives you feedback directly on your capability (you can or can't do a task), whereas there needs to be a specific system gives feedback on alignment and if that's a proxy for what you want you get eaten at higher power levels.
[^note-8]: If this doesn't ring true to you, please click through to the linked posts.
[^note-9]: And even for those people focusing on theory, there's a lot more focus on basic science of ML than trying to backchain the conceptual engineering needed to survive superintelligence. I'd estimate somewhere in the mid tens of people globally are focusing on what looks like the main cruxes.
[^note-10]: _Response to_ [_Jan Leike_](https://aligned.substack.com/p/alignment-is-not-solved-but-increasingly-looks-solvable)_,_ [_evhub_](https://www.lesswrong.com/posts/epjuxGnSPof3GnMSL/alignment-remains-a-hard-unsolved-problem)_,_ [_Boaz_](https://www.lesswrong.com/posts/g4LMH3c6DysazYbFn/the-state-of-ai-safety-in-four-fake-graphs)_, etc. Thanks for feedback and copyediting to_ [_@Luc Brinkman_](https://www.lesswrong.com/users/luc-brinkman?mention=user)_,_ [_@Mateusz Bagiński_](https://www.lesswrong.com/users/mateusz-baginski?mention=user)_,_ [_@Claude+_](https://www.lesswrong.com/users/claude?mention=user)
