---
title: "Five theses, two lemmas, and a couple of strategic implications"
author:
  - "Eliezer Yudkowsky"
source_url: "https://intelligence.org/2013/05/05/five-theses-two-lemmas-and-a-couple-of-strategic-implications/"
published: 2013-05-05
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "MIRI's primary concern about self-improving AI isn't so much that it might be created by 'bad' actors rather than 'good' actors in the global sphere; rather"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

MIRI’s primary concern about self-improving AI isn’t so much that it might be created by ‘bad’ actors rather than ‘good’ actors in the global sphere; rather most of our concern is in remedying the situation in which _no one knows at all_ how to create a self-modifying AI with known, stable preferences. (This is why we see the main problem in terms of [doing research](http://intelligence.org/research/) and encouraging others to perform relevant research, rather than trying to stop ‘bad’ actors from creating AI.)

This, and a number of other basic strategic views, can be summed up as a consequence of 5 theses about purely factual questions about AI, and 2 lemmas we think are implied by them, as follows:

**Intelligence explosion thesis**. A sufficiently smart AI will be able to realize large, reinvestable cognitive returns from things it can do on a short timescale, like improving its own cognitive algorithms or purchasing/stealing lots of server time. The intelligence explosion will hit very high levels of intelligence before it runs out of things it can do on a short timescale. See: [Chalmers (2010)](http://www.consc.net/papers/singularityjcs.pdf); [Muehlhauser & Salamon (2013)](https://intelligence.org/files/IE-EI.pdf); [Yudkowsky (2013)](https://intelligence.org/files/IEM.pdf).

**Orthogonality thesis**. Mind design space is huge enough to contain agents with almost any set of preferences, and such agents can be instrumentally rational about achieving those preferences, and have great computational power. For example, mind design space theoretically contains powerful, instrumentally rational agents which act as expected paperclip maximizers and always consequentialistically choose the option which leads to the greatest number of expected paperclips. See: [Bostrom (2012)](http://www.nickbostrom.com/superintelligentwill.pdf); [Armstrong (2013)](http://lesswrong.com/lw/h0k/arguing_orthogonality_published_form/).

**Convergent instrumental goals thesis**. Most utility functions will generate a subset of instrumental goals which follow from most possible final goals. For example, if you want to build a galaxy full of happy sentient beings, you will need matter and energy, and the same is also true if you want to make paperclips. This thesis is why we’re worried about very powerful entities even if they have no explicit dislike of us: “The AI does not love you, nor does it hate you, but you are made of atoms it can use for something else.” Note though that by the Orthogonality Thesis you can always have an agent which explicitly, terminally prefers not to do any particular thing — an AI which does love you will not want to break you apart for spare atoms. See: [Omohundro (2008)](http://selfawaresystems.files.wordpress.com/2008/01/ai_drives_final.pdf); [Bostrom (2012)](http://www.nickbostrom.com/superintelligentwill.pdf).

**Complexity of value thesis**. It takes a large chunk of Kolmogorov complexity to describe even idealized human preferences. That is, what we ‘should’ do is a computationally complex mathematical object even after we take the limit of reflective equilibrium (judging your own thought processes) and other standard normative theories. A superintelligence with a randomly generated utility function would not do anything we see as worthwhile with the galaxy, because it is unlikely to accidentally hit on final preferences for having a diverse civilization of sentient beings leading interesting lives. See: [Yudkowsky (2011)](https://intelligence.org/files/ComplexValues.pdf); [Muehlhauser & Helm (2013)](https://intelligence.org/files/IE-ME.pdf).

**Fragility of value thesis**. Getting a goal system 90% right does not give you 90% of the value, any more than correctly dialing 9 out of 10 digits of my phone number will connect you to somebody who’s 90% similar to Eliezer Yudkowsky. There are multiple dimensions for which eliminating that dimension of value would eliminate almost all value from the future. For example an alien species which shared almost all of human value except that their parameter setting for “boredom” was much lower, might devote most of their computational power to replaying a single peak, optimal experience over and over again with slightly different pixel colors (or the equivalent thereof). Friendly AI is more like a satisficing threshold than something where we’re trying to eke out successive 10% improvements. See: Yudkowsky ([2009](http://lesswrong.com/lw/y3/value_is_fragile/), [2011](https://intelligence.org/files/ComplexValues.pdf)).

These five theses seem to imply two important lemmas:

**Indirect normativity**. Programming a self-improving machine intelligence to implement a grab-bag of things-that-seem-like-good-ideas will lead to a bad outcome, regardless of how good the apple pie and motherhood sounded. E.g., if you give the AI a final goal to “make people happy” it’ll just turn people’s pleasure centers up to maximum. “Indirectly normative” is Bostrom’s term for an AI that calculates the ‘right’ thing to do via, e.g., looking at human beings and modeling their decision processes and idealizing those decision processes (e.g. what you would-want if you knew everything the AI knew and understood your own decision processes, reflective equilibria, ideal advisor theories, and so on), rather than being told a direct set of ‘good ideas’ by the programmers. Indirect normativity is how you deal with Complexity and Fragility. If you can succeed at indirect normativity, then small variances in essentially good intentions may not matter much — that is, if two different projects do indirect normativity correctly, but one project has 20% nicer and kinder researchers, we could still hope that the end results would be of around equal expected value. See: [Muehlhauser & Helm (2013)](https://intelligence.org/files/IE-ME.pdf).

**Large bounded extra difficulty of Friendliness**. You can build a Friendly AI (by the Orthogonality Thesis), but you need a lot of work and cleverness to get the goal system right. Probably more importantly, the rest of the AI needs to meet a higher standard of cleanness in order for the goal system to remain invariant through a billion sequential self-modifications. Any sufficiently smart AI to do clean self-modification will tend to do so regardless, but the problem is that intelligence explosion might get started with AIs substantially less smart than that — for example, with AIs that rewrite themselves using genetic algorithms or other such means that don’t preserve a set of consequentialist preferences. In this case, building a Friendly AI could mean that our AI has to be smarter about self-modification than the minimal AI that could undergo an intelligence explosion. See: [Yudkowsky (2008)](https://intelligence.org/files/AIPosNegFactor.pdf) and [Yudkowsky (2013)](https://intelligence.org/files/IEM.pdf).

These lemmas in turn have two major strategic implications:

1.  We have a lot of work to do on things like indirect normativity and stable self-improvement. At this stage a lot of this work looks really foundational — that is, we can’t describe how to do these things using infinite computing power, let alone finite computing power. We should get started on this work as early as possible, since basic research often takes a lot of time.
2.  There needs to be a Friendly AI project that has some sort of boost over competing projects which don’t live up to a (very) high standard of Friendly AI work — a project which can successfully build a stable-goal-system self-improving AI, before a less-well-funded project hacks together a much sloppier self-improving AI. Giant supercomputers may be less important to this than being able to bring together the smartest researchers (see the open question posed in [Yudkowsky 2013](https://intelligence.org/files/IEM.pdf)) but the required advantage cannot be left up to chance. Leaving things to default means that projects less careful about self-modification would have an advantage greater than casual altruism is likely to overcome.
