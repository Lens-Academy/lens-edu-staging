---
title: "Why we should expect ruthless sociopath ASI"
author:
  - "Steven Byrnes"
source_url: "https://www.lesswrong.com/posts/ZJZZEuPFKeEdkrRyf/why-we-should-expect-ruthless-sociopath-asi"
published: 2026-02-18
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "(Fictional) Optimist: So you expect future artificial superintelligence (ASI) “by default”, i.e. in the absence of yet-to-be-invented techniques, to be a ruthless sociopath, happy to lie, cheat, and steal, whenever…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## The conversation begins ^the-conversation-begins

**(Fictional) Optimist:** So you expect future artificial superintelligence (ASI) “by default”, i.e. in the absence of yet-to-be-invented techniques, to be a ruthless sociopath, happy to lie, cheat, and steal, whenever doing so is selfishly beneficial, and with callous indifference to whether anyone (including its own programmers and users) lives or dies?

**Me:** Yup! (Alas.)

**Optimist:** …Despite all the evidence right in front of our eyes from humans and LLMs.

**Me:** Yup!

**Optimist:** OK, well, I’m here to tell you: that is a very specific and strange thing to expect, especially in the absence of any concrete evidence whatsoever. There’s no reason to expect it. If you think that ruthless sociopathy is the “true core nature of intelligence” or whatever, then [you should really look at yourself in a mirror and ask yourself where your life went horribly wrong](https://www.lesswrong.com/posts/d4HNRdw6z7Xqbnu5E/6-reasons-why-alignment-is-hard-discourse-seems-alien-to?commentId=v2WfXTLaoJuSw9QQG).

**Me:** Hmm, I think the “true core nature of intelligence” is above my pay grade. We should probably just talk about the issue at hand, namely future AI algorithms and their properties.

…But I actually agree with you that ruthless sociopathy is a very specific and strange thing for me to expect.

**Optimist:** Wait, you—what??

**Me:** Yes! Like, if you show me some random thing, there’s a 99.999…% chance that it’s not a ruthless sociopath. Instead it might be, like, a dirt clod. Dirt clods are not ruthless sociopaths, because they’re not intelligent at all.

**Optimist:** Oh c’mon, you know what I mean. I’m not talking about dirt clods. I’m saying, if you pick some random _mind_,  there is no reason at all to expect it to be a ruthless sociopath.

**Me:** How do you “pick some random mind”? Minds don’t just appear out of nowhere.

**Optimist:** Like, a human. Or an AI.

**Me:** Different humans are different to some extent, and different AI algorithms are different to a much, much greater extent. “AI” includes everything from [A\* search](https://en.wikipedia.org/wiki/A*_search_algorithm) to [MuZero](https://en.wikipedia.org/wiki/MuZero) to LLMs. Is A\* search a ruthless sociopath? Well, I mean, it does seem rather maniacally obsessed with graph traversal! Right?

**Optimist:** Haha, very funny. Please stop being annoyingly pedantic. I obviously didn’t mean “AI” in the sense of the academic discipline. I meant, like, AI in the colloquial sense, AI that qualifies as a mind, like LLMs. I’m mainly talking about human minds and LLM “minds”, i.e. all the minds we’ve ever seen in the real world, rather than in sci-fi. And hey, what a coincidence, ≈100% of those minds are _not_ ruthless sociopaths.

**Me:** As it happens, the threat model I’m working on is not LLMs, but rather [“brain-like” Artificial General Intelligence (AGI)](https://www.lesswrong.com/s/HzcM2dkCq7fwXBej8), which (from a safety perspective) is more-or-less a type of actor-critic model-based reinforcement learning (RL) agent. LLMs are profoundly different from what I’m working on. Saying that LLMs will be similar to RL-agent AGI because “both are AI” is like saying that LLMs will be similar to the A\* search algorithm because “both are AI”, or that a [frogfish](https://youtu.be/uRP4nAGMYCY?si=uF543PG-v_9DzdwS) will be similar to a human because “both are animals”. They can still be wildly different in every way that matters.

## Are people worried about LLMs causing doom? ^are-people-worried-about

**Optimist:** OK, but lots of other doomers talk about LLMs causing doom.

**Me:** Well, kinda. I think we need to tease apart two groups of people. Both are sometimes called “doomers”, but one is much more pessimistic than the other. This is very caricatured, but:

-   The comparatively-less-pessimistic group (say, P(doom) \[probability of human extinction from AI, assuming progress continues\] in the 5%–50% range) is a bigger group, and I vaguely associate them with the center-of-gravity of the Effective Altruism movement and [Anthropic employees](https://www.nytimes.com/2023/07/11/technology/anthropic-ai-claude-chatbot.html). They definitely do _not_ expect ruthless sociopath ASI as the default path we’re on, absent a technical breakthrough, like I’m arguing for here. At most, they’ll entertain the idea of ruthless sociopath ASI as an odd hypothetical, or as a result of a competitive race-to-the-bottom, or from egregiously careless programmers, or bad actors, etc. They’re probably equally or more concerned about lots of other potential AI problems—AI-assisted bioterrorism, dictatorships, etc.[^note-1]
-   I’m part of an even more pessimistic group (motto: [_If Anyone Builds It, Everyone Dies_](https://ifanyonebuildsit.com/)), which generally _does_ expect ruthless sociopath ASI as the default path we’re on, absent a technical breakthrough (along with [other miracles](https://www.lesswrong.com/posts/btHmC88KCZdzimBCM/steve-byrnes-s-shortform?commentId=vzWgcoP3isSBQbDbe)). We tend to think “50% chance that humans will survive continued AI development” is deliriously over-optimistic.

Anyway, the extra heap of concern in that latter camp is not from the LLMs _of today_ causing near-certain doom, or even the somewhat-better LLMs of tomorrow, but rather the wildly better ASIs of … maybe soon, maybe not, who knows. But even if it’s close in calendar time, and even if it comes out of LLM research, such an ASI would still be systematically different from LLMs as we know them today—

**Optimist:** —a.k.a., you have no evidence—

**Me:** —[_no evidence either way_](https://www.astralcodexten.com/p/the-phrase-no-evidence-is-a-red-flag), at least no evidence of that type. Anyway, as I was saying, ASI would be systematically different from today’s LLMs because … umm, where do I start …

…Actually, it would be much easier for me to explain if we _start_ with the ASI threat model that I spend all my time on, and then we can circle back to LLMs afterwards. Is that OK?

## Positive argument that “brain-like” RL-agent ASI would be a ruthless sociopath ^positive-argument-that-brain-like

**Optimist:** Sure. We can pause the discussion of LLMs for a few minutes, and start in your comfort zone of actor-critic model-based RL-agent “brain-like” ASI. Doesn’t really matter anyway: regardless of the exact algorithm, you clearly need some _positive_ reason to believe that this kind of ASI would be a ruthless sociopath. You can’t just unilaterally declare that your weird unprecedented sci-fi belief is the “default”, and push the burden of proof onto people who disagree with you.

**Me:** OK. Maybe a good starting point would be my posts [LeCun’s ‘A Path Towards Autonomous Machine Intelligence’ has an unsolved technical alignment problem](https://www.lesswrong.com/posts/C5guLAx7ieQoowv3d/lecun-s-a-path-towards-autonomous-machine-intelligence-has-1), or [‘The Era of Experience’ has an unsolved technical alignment problem](https://www.lesswrong.com/posts/TCGgiJAinGgcMEByt/the-era-of-experience-has-an-unsolved-technical-alignment).

**Optimist:** I’ve read those, but I’m not seeing how they answer my question. Again, what’s your _positive_ argument for ruthless sociopathy? Lay it on me.

**Me:** Sure. Back at the start of the conversation, I mentioned that random objects like dirt clods are not able to accomplish impressive feats. I didn’t (just) bring up dirt clods to troll you, rather I was laying the groundwork for a key point: If we’re thinking about AI that can autonomously found, grow, and staff innovative companies for years, or autonomously invent new scientific paradigms, then clearly it’s not a “random object”, but rather a thing that is able to accomplish impressive feats. And the question we should be asking is: _how does it do that_? Those things would be astronomically unlikely to happen if the AI were choosing actions at random. So **there has to be some explanation for how the AI finds actions that accomplish those impressive feats**.[^note-2]

So an explanation has to exist! What is it? I claim there are really only two answers that work in practice.

The first possible explanation is **consequentialism**: the AI accomplishes impressive feats by (what amounts to) having desires about what winds up happening in the future, and running some search process to find actions that lead to those desires getting fulfilled. **This is the main thing that you get from RL agents, and from model-based planning algorithms.** (My “brain-like AGI” scenario would involve both of those at once.) The whole point of those subfields of AI is: these are algorithms designed to find actions that maximize an objective, by any means available.

I.e., you get ruthless sociopathic behavior by default.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ZJZZEuPFKeEdkrRyf/wpuuewhb4bx91w6hrz0f)

[Source](https://www.youtube.com/watch?v=00Jjj6oI5fg)

And this is not just my armchair theorizing. Go find someone who was in AI in the 2010s or earlier, before LLMs took over, and they may well have spent a lot of time building or using RL agents and/or model-based planning algorithms. If so, they’ll tell you, based on their lived experience, that these kinds of algorithms are ruthless by default (when they work at all), unless the programmers go out of their way to make them non-ruthless. See e.g. [this 2020 DeepMind blog post on “specification gaming”](https://deepmind.google/blog/specification-gaming-the-flip-side-of-ai-ingenuity/).

And how would the programmers “go out of their way to make them non-ruthless”? I claim that the answer is not obvious, indeed not even known. See my [LeCun post](https://www.lesswrong.com/posts/C5guLAx7ieQoowv3d/lecun-s-a-path-towards-autonomous-machine-intelligence-has-1), and my [Silver & Sutton post](https://www.lesswrong.com/posts/TCGgiJAinGgcMEByt/the-era-of-experience-has-an-unsolved-technical-alignment), and more generally my post [“‘Behaviorist’ RL reward functions lead to scheming”](https://www.lesswrong.com/posts/FNJF3SoNiwceAQ69W/behaviorist-rl-reward-functions-lead-to-scheming) for why obvious approaches to non-ruthlessness won’t work.

Rather, algorithms in this class are naturally, umm, let’s call them, “ruthless-ifiers”, in the sense that they transmute even innocuous-sounding objectives like “it’s good if the human is happy” into scary-sounding ones like “ruthlessly maximize the probability that the human is happy”, which in turn suggest strategies such as forcibly drugging the human. Likewise, the innocuous-sounding “it’s bad to lie” gets ruthless-ified into “it’s bad to get caught lying”, and so on.

Of course, evolution _did_ go out of its way to make humans non-ruthless, by endowing us with [social instincts](https://www.lesswrong.com/posts/kYvbHCDeMTCTE9TAj/neuroscience-of-human-social-instincts-a-sketch). Maybe future AI programmers will likewise go out of _their_ way to make ASIs non-ruthless? I hope so—but [we need to figure out how](https://www.lesswrong.com/posts/oxvnREntu82tffkYW/we-need-a-field-of-reward-function-design).

To be clear, ruthless consequentialism isn’t always bad. I’m happy for ruthless consequentialist AIs to be [playing chess](https://en.wikipedia.org/wiki/AlphaZero), [designing chips](https://deepmind.google/blog/how-alphachip-transformed-computer-chip-design/), etc. In principle, I’d even be happy for a ruthless consequentialist AI to be emperor of the universe, creating an awesome future for all—but making that actually happen would be _super_ dangerous for [lots of reasons](https://www.lesswrong.com/posts/wucncPjud27mLWZzQ/intro-to-brain-like-agi-safety-10-the-technical-alignment) (e.g. you might need to operationalize “creating an awesome future for all” in a loophole-free way; see also [“‘The usual agent debugging loop’, and its future catastrophic breakdown”](https://www.lesswrong.com/posts/wucncPjud27mLWZzQ/intro-to-brain-like-agi-safety-10-the-technical-alignment#10_3_3_1__The_usual_agent_debugging_loop___and_its_future_catastrophic_breakdown)).

…So that’s consequentialism, one possible answer for how an AI might accomplish impressive feats, and it’s an answer that brings in ruthlessness by default.

## Circling back to LLMs: imitative learning vs ASI ^circling-back-to-llms

…And then there’s a second, different possible answer to how an AI might accomplish impressive feats: **imitative learning** from humans. You train an AI to predict what actions a skilled human would take in many different contexts, and then have the AI take that same action itself. I claim that **LLMs** get their impressive capabilities almost entirely from imitative learning.[^note-3] By contrast, “true” imitative learning is entirely absent (and impossible) in humans and animals.[^note-4]

Imitative-learning AIs do _not_ have ruthless sociopathy by default, because of course the thing they’re imitating is non-ruthless humans.[^note-5]

**Optimist:** Huh … Wait … So you’re an optimist about superintelligence (ASI) being non-ruthless, as long as people stick to LLMs?

**Me:** Alas, no. I think that the full power of consequentialism is super dangerous by default, _and_ I think that the full power of consequentialism is the only way to get ASI, and so AI researchers are going to keep working until they eventually learn to fully tap that power.

In other words, I see a disjunction:

-   EITHER, LLMs will always get their powers primarily from imitative learning, as I claim they do today—in which case they will never be able to figure things out way beyond the human-created training data, and will thus never reach ASI. And then eventually we’ll get ASI via a _different_ AI paradigm, one that _can_ rocket arbitrarily far past any human data. And that paradigm will have to draw its powers from consequentialism, which brings in ruthlessness-by-default.
-   OR, someone will figure out how to get LLMs themselves to rocket arbitrarily far past human training data and into ASI. But the only way to do that is to somehow modify LLMs to draw on the full powers of consequentialism. In which case, again, we get ruthlessness-by-default.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ZJZZEuPFKeEdkrRyf/qpukod1h632c86hi5wqw)

[Source](https://www.youtube.com/watch?v=aFW6FGV_tls)

For what it’s worth, I happen to expect that ASI will come from the former (future paradigm shift) rather than the latter (LLM modifications). But it hardly matters in this context.

**Optimist:** I dunno, if you’re willing to concede that LLMs today are not maximally ruthless, well, LLMs today don’t seem that far from superintelligence. I mean, humans don’t “rocket arbitrarily far past any training data” either. They usually do things that have been done before, or at most (for world experts on the bleeding edge) go just one little step beyond it. LLMs can do both, right?

**Me:** Yes, but humans _collectively and over time_ can get way, way, way beyond our training data. We’re still using the same brain design that we were using in Pleistocene Africa. Between then and now, there were no angels who dropped training data from the heavens, but humans nevertheless invented language, science, technology, industry, culture, and everything else in the $100T global economy _entirely from scratch_. We did it all by ourselves, by our own bootstraps, ultimately via the power of consequentialism, as implemented in the RL and model-based planning algorithms in our brains.

(See [“Sharp Left Turn” discourse: An opinionated review](https://www.lesswrong.com/posts/2yLyT6kB7BQvTfEuZ/sharp-left-turn-discourse-an-opinionated-review).)

By the same token, if humanity survives another 1000 years, we will invent wildly new scientific paradigms, build wildly new industries and ways of thinking, etc.

[There’s a quadrillion-dollar market](https://www.lesswrong.com/posts/xJWBofhLQjf3KmRgg/four-ways-learning-econ-makes-people-dumber-re-future-ai) for AIs that can likewise do that kind of thing, as humans can. If the LLMs of today don’t pass that bar (and they don’t), then I expect that, sooner or later, either someone will figure out how to get LLMs to pass that bar, or else someone will invent a new non-LLM AI paradigm that passes that bar. Either way, imitative learning is out, consequentialism is in, and we get ruthless sociopath ASIs by default, in the absence of yet-to-be-invented theoretical advances in technical alignment. (And then everyone dies.)

_Thanks Jeremy Gillen, Seth Herd, and Justis Mills for critical comments on earlier drafts._

**Changelog:** 2026-02-23 and 2026-07-24: Edits to footnote 3.

[^note-1]: We should definitely also be thinking about these other potential problems, don’t get me wrong!
[^note-2]: Related: the [so-called “Follow-the-Improbability Game”](https://www.lesswrong.com/posts/k6EPphHiBH4WWYFCj/gazp-vs-glut).
[^note-3]: For details, see: [LLMs are (still) mostly powered by imitative learning, not RL](https://www.lesswrong.com/posts/wYpjXRLqbLbnmjbJP/llms-are-still-mostly-powered-by-imitative-learning-not-rl).
[^note-4]: E.g. if my brain is predicting what someone else will say, that’s related to auditory inputs, and if my brain is speaking, that involves motor-control commands going to my larynx etc. There is no straightforward mechanical translation from one to the other, analogous to the straightforward mechanical translation from “predict the next token” to “output the next token” in LLM pretraining. More in [“Foom & Doom” §2.3.2](https://www.lesswrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard#2_3_2_LLM_pretraining_magically_transmutes_observations_into_behavior__in_a_way_that_is_profoundly_disanalogous_to_how_brains_work).
[^note-5]: See [GPTs are Predictors, not Imitators](https://www.lesswrong.com/posts/nH4c3Q9t9F3nJ7y8W/gpts-are-predictors-not-imitators) for an even-more-pessimistic-than-me counterargument, and [“Foom & Doom” §2.3.3](https://www.lesswrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard#2_3_3_To_what_extent_should_we_think_of_LLMs_as_imitating_) for why I don’t buy that counterargument.
