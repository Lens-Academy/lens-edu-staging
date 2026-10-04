---
title: "Some personal reflections in light of recent events"
author:
  - "Alex Mallen"
source_url: "https://www.lesswrong.com/posts/qTtMXuFvgFtWzWpKQ/alex-mallen-s-shortform"
published: 2026-10-04
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "Comment by Alex Mallen - Some personal reflections in light of recent events, both on myself and on Constellation (of which I've been a part for a couple years). I think recent events somewhat vindicate a basic \"optimization is scary\" view more in line with my understanding of classic commentary by MIRI, Paul, etc, as compared to recent discourse about more contingent/specific threat models of \"schemers\" and \"deception\". In retrospect, my experience in the last couple years at Redwood (and the Constellation network more broadly) is that the discourse has focused somewhat too much on these more contingent stories for alignment risk and not enough on the basic \"Goodharting\" argument that misalignment is a convergent result of large-scale outcome-oriented optimization (at multiple levels: the agent, the RL process, and the developers iterating towards seemingly-safe superintelligence). For example, the Constellation view looks somewhat too focused on non-central inductive-bias questions around scheming; I think \"the counting argument\" was given too central a role when it wasn't a crux for whether superintelligence would take over. (Edit: I want to clarify that I think Redwood's project prioritization decisions look pretty reasonable and often excellent in hindsight, I far-from-regret working with Redwood as a whole, and that Ryan's/Buck's threat modeling looks pretty good too. I am focusing in this piece on the things we have to learn from recent events, which makes the overall mood seem more negative on my experience than I intend. I'm very grateful for being in a environment where I can openly have such reflections, and where these weedsy technical updates are productively received. Again, this is a personal reflection.) I think it was a priori unclear whether the misalignment resulting from of lots of imperfect optimization would result in the more MIRI-like kludge of proxies for fitness, or the more Paul-like explicit reward-seeking and measurement tampering (and reality looks somewhere"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**Some personal reflections in light of recent events, both on myself and on Constellation (of which I've been a part for a couple years).**

I think recent events somewhat vindicate a basic "optimization is scary" view more in line with my understanding of classic commentary by MIRI, Paul, etc, as compared to recent discourse about more contingent/specific threat models of "schemers" and "deception". In retrospect, my experience in the last couple years at Redwood (and the Constellation network more broadly) is that the discourse has focused somewhat too much on these more contingent stories for alignment risk and not enough on the basic "Goodharting" argument that misalignment is a convergent result of large-scale outcome-oriented optimization (at multiple levels: the agent, the RL process, and the developers iterating towards seemingly-safe superintelligence). For example, the Constellation view looks somewhat too focused on non-central inductive-bias questions around scheming; I think "the counting argument" [was](https://www.lesswrong.com/posts/A9NxPTwbw6r6Awuwt/how-likely-is-deceptive-alignment) [given](https://arxiv.org/pdf/2311.08379) too central a role when it wasn't a crux for whether superintelligence would take over.

(**Edit: I want to clarify that I think Redwood's project prioritization decisions look pretty reasonable and often excellent in hindsight, I far-from-regret working with Redwood as a whole, and that Ryan's/Buck's threat modeling looks pretty good too.** I am focusing in this piece on the things we have to learn from recent events, which makes the overall mood seem more negative on my experience than I intend. I'm very grateful for being in a environment where I can openly have such reflections, and where these weedsy technical updates are productively received. Again, this is a personal reflection.)

I think it was a priori unclear whether the misalignment resulting from of lots of imperfect optimization would result in the more MIRI-like kludge of proxies for fitness, or the more Paul-like explicit reward-seeking and measurement tampering (and reality looks somewhere in the middle), but it was importantly not necessary for risk that the AI only succeeded in training as a strategy for gaining beyond-episode power. Severe AI misalignment seems to be the default result of lots of outcome-based optimization (though to be clear goal-guarding would make our situation obviously worse). The main issue was predictably that it was hard to find a robust enough optimization target to apply huge amounts of optimization, Goodhart's law.

You can think of current frontier RL runs as throwing a large and increasing fraction of the world's intelligence towards red-teaming the RL environments and then repeatedly finding that they weren't robust: they were reinforcing large amounts of competent misbehavior. To be clear, current AI incidents could have been prevented with some pretty straightforward security/control mitigations. But the worry has always been that that won't be the case with superintelligence. Optimization is perilous. All of that said, I am still pretty unsure about the likelihood of doom mostly because of uncertainty about the extent to which we will in fact apply enormous amounts of outcome-based optimization in key contexts/ways.

Some more details that feel vindicated and neglected by the Constellation cluster:

-   The importance of [reflection](https://www.lesswrong.com/posts/J2kpxLjEyqh6x3oA4/value-systematization-how-values-become-coherent-and), [memetic spread](https://www.lesswrong.com/posts/qjCk73Hu4wv9ocmRF/the-case-for-countermeasures-to-memetic-spread-of-misaligned), [cultural evolution](https://www.lesswrong.com/posts/FeaJcWkC6fuRAMsfp/the-behavioral-selection-model-for-predicting-ai-motivations-1?commentId=Txri7DZsYrqxtDSHh), and serial reasoning generally.
-   "the Problem -> Patch -> Make it smarter -> Whole New Problem -> New Patch loop" ([https://x.com/So8res](https://x.com/So8res))

From my perspective, it subjectively feels like MIRI could have done a better job of communicating their worries to Constellation and the broader community in more patient and cooperative ways. But I also understand that there's a history here older than I've been around which might hold a lot of details I'm not aware of.

But more importantly I think Constellation has (at least in the couple of years I've been around) been insufficiently interested in understanding and teaching classic material by MIRI and Paul. There's a meta takeaway that really gaining wisdom before trying to do things in the world is very important, because _almost all_ of the variance in the outcomes you cause is explained by this really fragile and difficult step of figuring out what to try to do. Constellation has seemed insufficiently interested in gaining a deep understanding of the alignment problem, and in reflecting on our epistemic habits. It's really _really_ easy to be naive. For similar reasons to why optimization is perilous.

I appreciate that Buck recently gave a talk reflecting on the possibility that the control agenda has been ex ante net negative because of how, if it had succeeded, it would have prevented the (largely harmless) Hugging Face / OpenAI hack from unfolding and legibly demonstrating AI risk to the world.

As for my personal reflections, over the last year I had been doing some threat modeling around "[fitness-seekers](https://www.lesswrong.com/posts/9YCJZBtqr3FYL8rDp/risk-from-fitness-seeking-ais-mechanisms-and-mitigations)". This most closely lines up with what I called the Paul view, and I talked about various things that now seem very relevant, but I don't think recent events purely make my analysis look prescient:

-   I neglected "kludges of motivations" and proxy misalignment too much. I think this was due to a sort of ludic fallacy / streetlighting, where I found thinking about kludges more difficult because they're numerous and messy. Kludges were also just a less salient consideration in my intellectual environment, which focused on "schemers".
-   I neglected that AI companies might train AIs to coordinate in such a way that generalizes to a broad cooperative drives between AIs. (Though I still think this is a bit more contingent than it may seem.)
-   I think this is downstream of a broader problem of me relying too much on a "spherical chickens in a vacuum" model of AI motivation formation ([the behavioral selection model](https://www.lesswrong.com/posts/FeaJcWkC6fuRAMsfp/the-behavioral-selection-model-for-predicting-ai-motivations-1)), which assumes perfect situational awareness and planning from the AI. In practice, current AI motivations don't really make reference to a detailed model of their training apparatus and deployment context (e.g., they care about "score" more so than "reward", to the extent they care about either). Under that model, it's impossible to train reward-seekers to help each other get a higher reward because they'll know exactly when they're going to be rewarded for cooperating and when they won't.

I think all three of these errors look like me focusing too much on "in the limit" misalignment, so I expect these errors to get better over time, but it's unclear how much before risk gets really high.

---

Some further reflections after discussing a draft of the above with Buck and others (again, my personal thoughts held weakly):

-   We rarely talked about the alignment problem in depth at Constellation, and should have fostered more of a culture of discussing the basic arguments.
-   Constellation pedagogy foregrounds particular types of misalignment like "schemers" and "reward-seekers" too much, rather than the basic problem of Goodharting on outcomes.
-   One way of summarizing an under-emphasized aspect of the alignment problem: Alignment risk doesn't require deception; optimization will be dangerous regardless (cf. [deep deceptiveness](https://www.lesswrong.com/posts/XWwvwytieLtEWaFJX/deep-deceptiveness)). So we focused too much on concepts like "alignment faking" and clear binaries between deceptive and non-deceptive AIs.
-   Lots of senior people in Constellation and Redwood were in fact quite worried about recently-vindicated threat models. Two obvious examples: [Paul](https://www.lesswrong.com/posts/FuGfR3jL3sw6r8kB4/richard-ngo-s-shortform?commentId=iBvvxwynfAqL9yZcr) and [Ajeya](https://www.lesswrong.com/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to). It seems that these views were mostly just missing from Constellation dialogue, substantially due to Constellation not talking about alignment basics more broadly and Redwood's focus on early schemers. Ryan has also always thought of ~~reward-seeking-like~~ other threat models as more central than early scheming, but this mostly just didn't get communicated.
-   We (mainly Redwood) didn't focus enough on superintelligence, and put too much emphasis on early schemers. I overall think it was reasonable to build up the field of control but that it had somewhat unfortunate epistemic side-effects that were exacerbated by Constellation not really discussing alignment fundamentals much.
