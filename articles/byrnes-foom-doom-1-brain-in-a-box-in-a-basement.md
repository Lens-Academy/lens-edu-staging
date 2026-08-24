---
title: "Foom & Doom 1: “Brain in a box in a basement”"
author:
  - "Steven Byrnes"
source_url: "https://www.lesswrong.com/posts/yew6zFWAKG4AGs3Wk/foom-and-doom-1-brain-in-a-box-in-a-basement"
published: 2025-06-23
created: 2026-08-21
accessed: 2026-08-21
description: "This is a two-post series on AI “foom” (this post) and “doom” (next post). A decade or two ago, it was pretty common to discuss “foom & doom” scenarios, as advocated especially by Eliezer Yudkowsky. In a typical such scenario, a small team would build a system that would rocket (“foom”) from “unimpressive” to “Artificial Superintelligence” (ASI) within a very short time window (days, weeks, maybe months), involving very little compute (e.g. “brain in a box in a basement”), via recursive self-improvement. Absent some future technical breakthrough, the ASI would definitely be egregiously misaligned, without the slightest intrinsic interest in whether humans live or die. The ASI would be born into a world generally much like today’s, a world utterly unprepared for this new mega-mind. The extinction of humans (and every other species) would rapidly follow (“doom”). The ASI would then spend countless eons fulfilling its desires, desires which we humans would find to be bizarre and pointless."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

# 1.1 Series summary and Table of Contents

This is a two-post series on AI “foom” (this post) and “doom” ([next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard)).

A decade or two ago, it was pretty common to discuss “foom & doom” scenarios, as advocated especially by Eliezer Yudkowsky. In a typical such scenario, a small team would build a system that would rocket (“foom”) from “unimpressive” to “Artificial Superintelligence” (ASI) within a very short time window (days, weeks, maybe months), involving very little compute (e.g. [“brain in a box in a basement”](https://intelligence.org/files/AIFoomDebate.pdf#page=447)), via [recursive self-improvement](https://www.greaterwrong.com/w/recursive-self-improvement). Absent some future technical breakthrough, the ASI would definitely be egregiously misaligned, without the slightest intrinsic interest in whether humans live or die. The ASI would be born into a world generally much like today’s, a world utterly unprepared for this new mega-mind. The extinction of humans (and every other species) would rapidly follow (“doom”). The ASI would then spend countless eons fulfilling its desires, desires which we humans would find to be bizarre and pointless.

Now, I don’t endorse every word of that foom & doom scenario above—for example, I don’t think “foom” requires recursive self-improvement. But I’m in _much_ closer agreement with that scenario than the vast majority of AI safety & alignment researchers today, who tend to see the “foom & doom” scenario above as somewhere between “extraordinarily unlikely” and _“already falsified”_!

Those researchers are not asking each other “is it true?”, but rather “lol, can you believe that some people used to believe that?”.[^1] Oh well. Laugh all you want. It’s still what I believe.

Conversely, from my perspective as a foom & doomer, it’s the mainstream contemporary AI alignment discourse that feels increasingly foreign and strange. How, I ask myself, do so many seemingly reasonable people wind up with such wildly, bafflingly over-optimistic beliefs as “P(doom)≲50%”??

Anyway, my main goal in these two posts is to explore how I wind up in such a different place as most other alignment researchers do today, on the question of foom & doom. I don’t particularly expect to win skeptical readers over to my side, but would at least like to convey that foom & doom is a story that hangs together and deserves a modicum of consideration.

## 1.1.2 Should I stop reading if I expect LLMs to scale to ASI?

These posts are mainly exploring my disagreement with a group of researchers who think of LLMs[^2] as being on a smooth, continuous path towards ASI. This group comprises probably >95% of people working on AI alignment, safety, and governance today[^3].

(For many people in this group, if you ask them directly whether there might be important changes in AI algorithms, training approaches, etc., between today and ASI, they’ll say “Oh yes, of course that’s possible”. But if you ask them _any other_ question about the future of AI, they’ll answer as if they expect no such change.)

There’s a very short answer to why I disagree with those LLM-focused researchers on foom & doom: They expect LLMs to scale to ASI, and I don’t. Instead I expect that ASI will be a very different AI paradigm: [“brain-like AGI”](https://www.greaterwrong.com/s/HzcM2dkCq7fwXBej8) (more on which below and in the [next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard)).

So if you’re an LLM-focused reader, you may be thinking: “Well, Steve is starting from a weird premise, so no wonder he gets a weird conclusion. Got it. Cool. …Why should I bother reading 15,000 more words about this topic?”

But before you go, I do think there are lots of interesting details in the story of _exactly how_ those different starting premises (LLMs vs a different paradigm) flow down to wildly divergent views on foom & doom.

And some of those details will also, incidentally, clarify disagreements _within_ the LLM-focused community. For example,

-   I might say _“I expect next-paradigm AIs to be different from (and more dangerous than) current LLMs because of X, Y, Z”_;
    
-   and meanwhile, an LLM-focused doomer might say _“I expect future, more powerful, LLMs to be different from (and more dangerous than) current LLMs because of one or more of the very same X, Y, Z!”_
    

So I’m hopeful that these posts will have some “food for thought” for doomers like me trying to understand where those P(doom)≲50% “optimists” are coming from, and likewise for “optimists” trying to better understand doomers.

# 1.2 Post summary and Table of Contents

This post covers “foom”, my belief that there will be a sharp localized takeoff, in which a far more powerful and compute-efficient kind of AI emerges suddenly into an utterly unprepared world. I explore the scenario, various arguments against it and why I don’t find them compelling, and the terrifying implications (if true) on our prospects for AI governance, supervised oversight, testing, and more. Here’s the outline:

-   In **Section 1.3**, I argue that there is a yet-to-be-discovered “simple(ish) core of intelligence”, which would constitute a future AI paradigm. I offer the human brain as an existence proof, and I argue that most LLM-focused researchers—even researchers who think of themselves as “AGI-pilled”—have an insufficiently radical picture in their head for what real AGI could do.
    
-   Then in **Section 1.4**, I respond to four popular counterarguments, including _“If such a thing existed, then somebody would have already found it!”_ and _“So what? A new paradigm would just be another variety of ML.”_.
    
-   In **Section 1.5,** I suggest that this new paradigm will involve frighteningly little training compute, compared to what we’re used to from LLMs.
    
-   **Section 1.6** then explores some consequences of “frighteningly little training compute”, particularly my pessimism about efforts to delay or govern ASI. Worse, those efforts tend to involve public messaging that sounds like _“boo LLMs”_, and these messages are getting co-opted by precisely those AI researchers whose work is most dangerous—namely, the researchers trying to replace LLMs with a more powerful AI paradigm.
    
-   In **Section 1.7**, I argue that the amount of R&D required for this future scary AI paradigm to cross the gap from “seemingly irrelevant” to superintelligence will probably be _tiny_, like maybe 0–30 person-years. This belief is unusual, and wildly different from what’s happened with LLMs; indeed, [AI-2027 envisions _millions_ of person-years of R&D](https://www.greaterwrong.com/posts/btHmC88KCZdzimBCM/steve2152-s-shortform#comment-fqYrmHE9bdRoSBFy8) to cross that same capabilities gap.
    
-   **Section 1.8** explores some consequences that would follow from that “very little R&D” hypothesis, including probably an extremely sharp and local takeoff _even without_ recursive self-improvement; a lack of any pre-takeover ‘deployment’ (internal or external) of this future scary paradigm AI; and an AI getting a decisive strategic advantage (opportunity to kill everyone and run the world by itself).
    
-   **Section 1.9** is a brief discussion of timelines-to-AGI. I throw out some numbers (“probably 5–25 years”), but who knows really.
    

# 1.3 A far-more-powerful, yet-to-be-discovered, “simple(ish) core of intelligence

LLMs are very impressive, but they’re not AGI yet—not [by my definition](https://www.greaterwrong.com/posts/PDx4ueLpvz5gxPEus/why-i-m-not-working-on-debate-rrm-elk-natural-abstractions#1_3_Why_I_want_to_move_the_goalposts_on__AGI_). For example, existing AIs are nowhere near capable of autonomously writing a business plan and then founding a company and growing it to $1B/​year revenue, all with zero human intervention. By analogy, if humans were like current AIs, then humans would be able to do some narrow bits of founding and running companies by ourselves, but we would need some intelligent non-human entity (angels?) to repeatedly intervene, assign tasks to us humans, and keep the larger project on track.

Of course, humans (and groups of humans) don’t need the help of angels to conceive and carry out ambitious projects, like building businesses or going to the moon. We can do it all by ourselves. So by the same token, future AGIs (and groups of AGIs) won’t need the help of humans.

…So that’s my pitch that AGI doesn’t exist yet. And thus, the jury is still out on what AGI (and later, ASI) will look like, or how it will be made.

My expectation is that, for better or worse, LLMs will _never_ be able to carry out those kinds of projects, even after future advances in scaffolding, post-training, and so on. If I’m right, that wouldn’t mean that those projects are beyond the reaches of AI—it’s clearly possible for _some_ algorithm to do those things, because humans can! Rather it would mean that LLMs are the wrong algorithm class. Instead, I think sooner or later someone will figure out a different AI paradigm, and then we’ll get superintelligence with _shockingly little_ compute, _shockingly little_ effort, and in _shockingly little_ time. (I’ll quantify that later.)

Basically, I think that there’s a “simple(ish) core of intelligence”, and that LLMs don’t have it. Instead, people are hacking together workarounds via _prodigious_ quantities of (in [Ajeya’s terminology](https://www.planned-obsolescence.org/scale-schlep-and-systems/)) “scale” (a.k.a. compute, §1.5 below) and “schlep” (a.k.a. R&D, §1.7 below). And researchers are then extrapolating that process into the future, imagining that we’ll turn LLMs into ASI via _even more_ scale and _even more_ schlep, up to quantities of scale and schlep that strike me as ludicrously unnecessary and implausible.

## 1.3.1 Existence proof: the human cortex

The whole cortex is [(more-or-less)](https://www.greaterwrong.com/posts/wBHSYwqssBGCnwvHg/intro-to-brain-like-agi-safety-2-learning-from-scratch-in#2_5_3__Uniformity__evidence) a uniform [randomly-initialized](https://www.greaterwrong.com/posts/wBHSYwqssBGCnwvHg/intro-to-brain-like-agi-safety-2-learning-from-scratch-in#2_5_Evidence_on_whether_the_cortex__striatum__and_cerebellum_learn_from_scratch) learning algorithm, and I think it’s basically the secret sauce of human intelligence. Even if you disagree with that, we can go up a level to the whole brain: the human brain algorithm has to be simple enough to fit in our (rather small) genome.[^4] And not much evolution happened between us and chimps. And yet our _one_ brain design, without modification, was able to invent farming and science and computers and rocket ships and everything else, none of which has any straightforward connection to tasks on the African savannah.

Anyway, the human cortex is this funny thing with [100,000,000 repeating units](https://en.wikipedia.org/wiki/Cortical_minicolumn), each with 6-ish characteristic layers with correspondingly different neuron types and connection patterns, and so on. Nobody knows how it works. You can look up dozens of theories explaining what each of the 6-ish layers is doing and how, but they all disagree with each other. Some of the theories are supported by simulations, but those simulations are unimpressive toy models with no modern practical applications whatsoever.

Remember, if the theories were correct and complete, then they could be turned into simulations able to do all the things that the _real_ human cortex can do[^5]—vision, language, motor control, reasoning, inventing new scientific paradigms from scratch, founding and running billion-dollar companies, and so on.

So here is a very different kind of learning algorithm waiting to be discovered, one which we know can scale to AGI, and then to ASI beyond that (per §1.7.2 below). And people are working on it as we speak, and they haven’t succeeded yet, despite decades of work and billions of dollars of resources devoted to figuring it out.

(To be clear, I desperately hope they continue to fail! At least until we have a much better plan for [Safe & Beneficial brain-like AGI](https://www.greaterwrong.com/s/HzcM2dkCq7fwXBej8). See especially §1.8.4 below and the [next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard).)

## 1.3.2 Three increasingly-radical perspectives on what AI capability acquisition will look like

Here are three perspectives:

1.  _Economists and other people who see AI as a normal technology:_ “If we want AI to work in some new application area, like some particular industrial design workflow, then humans need to do a lot of R&D work to develop and integrate the AI into this task.”
    
2.  _LLM-focused AGI person:_ “Ah, that’s true today, but eventually other AIs can do this ‘development and integration’ R&D work for us! No human labor need be involved!”
    
3.  _Me:_ “No! That’s still not radical enough! In the future, that kind of ‘development and integration’ R&D work just won’t need to be done at all—not by humans, not by AIs, not by anyone! Consider that there are 8 billion copies of basically _one_ human brain design, and if a copy wants to do industrial design, it can just figure it out. By the same token, there can be basically _one_ future AGI design, and if a copy wants to do industrial design, it can just figure it out!”
    

Another place this comes up is robotics:

1.  _Economists:_ “Humans will need to do R&D to invent good robotics algorithms.”
    
2.  _LLM-focused AGI person:_ “Future powerful AIs will need to do R&D to invent good robotics algorithms.”
    
3.  _Me:_ “Future powerful AI will _already be_ a good robotics algorithm!”[^6]
    

…After all, if a human wants to use a new kind of teleoperated robot, nobody needs to do a big R&D project or breed a new subspecies of human. You just take an off-the-shelf bog-standard human brain, and if it wants to pilot a new teleoperated robot, it will just autonomously figure out how to do so, getting rapidly better within a few hours. By the same token, there can be _one_ future AGI design, and it will be able to do that same thing.

# 1.4 Counter-arguments to there being a far-more-powerful future AI paradigm, and my responses

## 1.4.1 Possible counter: “If a different, much more powerful, AI paradigm existed, then someone would have already found it.”

I think of this as a classic [@paulfchristiano](https://www.greaterwrong.com/users/paulfchristiano?mention=user)\-style rebuttal (see e.g. [Yudkowsky and Christiano discuss “Takeoff Speeds”](https://www.greaterwrong.com/posts/vwLxd6hhFvPbvKmBH/yudkowsky-and-christiano-discuss-takeoff-speeds), 2021).

In terms of reference class forecasting, I concede that it’s rather rare for technologies with extreme profit potential to have sudden breakthroughs unlocking massive new capabilities (see [here](https://aiimpacts.org/discontinuous-progress-investigation/)), that “could have happened” many years earlier but didn’t. But there are at least a _few_ examples, like the [2025 baseball “torpedo bat”](https://en.wikipedia.org/wiki/Baseball_bat#Innovations), wheels on suitcases, the original Bitcoin, and (arguably) nuclear chain reactions.[^7]

Also, there’s long been a $1M cash bounty plus eternal fame and glory for solving the Riemann Hypothesis. Why hasn’t someone already solved it? I dunno! I guess it’s hard.

“Ah, but if companies had been putting billions of dollars into solving the Riemann Hypothesis over the last decade, as they have been doing for AI, _then_ the Riemann Hypothesis surely would have been solved by now, right?” I dunno! Maybe! But not necessarily.

“Ah, but if the Riemann Hypothesis is that hard to solve, it must be because the proof is extraordinarily intricate and complicated, right?” I dunno! Maybe! But not necessarily. I think that lots of math proofs are elegant in hindsight, but took a lot of work to discover.

As another example, there was widespread confusion about causal inference for decades before Judea Pearl and others set us straight, with a simple and elegant framework.

So likewise, there can be a “simple(ish) core of intelligence” (§1.3 above) that is taking people a while to discover.

Of course, the strongest argument to me is the one in §1.3.1 above: the human cortex is an existence proof that there are important undiscovered insights in the world of learning algorithms.

## 1.4.2 Possible counter: “But LLMs will have already reached ASI before any other paradigm can even put its shoes on”

Well, I don’t think LLMs will scale to ASI. Not with multimodal data, not with RL from Verifiable Rewards post-training, not with scaffolding, not with anything else, not soon, not ever. That’s my belief, which I won’t argue for here. Seems like we’ll find out one way or the other quite soon.

(To be clear, I could be wrong, and certainly don’t want to discourage people from contingency-planning for the possibility that souped-up future LLM systems will scale to ASI.)

## 1.4.3 Possible counter: “If ASI will be part of a different paradigm, who cares? It’s just gonna be a different flavor of ML.”

I dispute the word “just”. Different ML algorithms can be quite different from each other!

I think the new paradigm will bring a shocking phase shift allowing dramatically more capabilities from dramatically less compute (see later sections), along with a shocking phase shift in the difficulty of technical alignment, including proneness to egregious scheming and deception ([next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard)), as compared to current and future LLMs.

## 1.4.4 Possible counter: “If ASI will be part of a different paradigm, the new paradigm will be discovered by LLM agents, not humans, so this is just part of the continuous ‘AIs-doing-AI-R&D’ story like I’ve been saying”

I have two responses.

First, I disagree with that prediction. Granted, probably LLMs will be a _helpful research tool_ involved in finding the new paradigm, but there have always been helpful research tools, like PyTorch and arXiv and Google, and I don’t expect LLMs to be in a fundamentally different category from those other helpful research tools.

Second, even if it’s true that LLMs _will_ discover the new paradigm by themselves (or almost by themselves), I’m just not sure I even care. I see the pre-paradigm-shift AI world as a lesser problem, one that LLM-focused AI alignment researchers (i.e. the vast majority of them) are already focusing on. Good luck to them. And I want to talk about what happens in the crazy world that we enter _after_ that paradigm shift.

# 1.5 Training compute requirements: Frighteningly little

We already know that different ML approaches can have different quantitative relationships between compute and performance. For example, Fig. 7 of the [classic 2020 “Scaling Laws” paper](https://arxiv.org/abs/2001.08361) shows perplexity scaling laws for LSTMs and transformers, and they do not overlay. I expect the next paradigm to be a very different learning algorithm, so the compute-versus-performance curves that we’re used to today are just irrelevant, from my perspective. After the new paradigm, all bets are off.

Instead, my guess (based largely on lots of opinions about exactly what computations the human brain is doing and how) is that human-level human-speed AGI will require not a data center, but rather something like one consumer gaming GPU—and not just for inference, but even for training from scratch.

So, whereas most people would say “Groups of humans can create $1B/​year companies from scratch without any divine intervention, but groups of LLMs _cannot_ create $1B/​year companies from scratch without any human intervention. Welp, I guess we need _even more_ training compute…”

…I would instead say “The latest LLMs are the wrong AI paradigm, but next-paradigm AI will be able to do things like that, starting from random initialization, with 1000× _less_ training compute than was being used to train LLMs in 2022![^8]

I won’t defend that here; see [Thoughts on hardware /​ compute requirements for AGI](https://www.greaterwrong.com/posts/LY7rovMiJ4FhHxmH5/thoughts-on-hardware-compute-requirements-for-agi) for some of my thinking.

Instead, I’ll focus on how very low training compute feeds into many of my other beliefs.

# 1.6 Downstream consequences of “new paradigm with frighteningly little training compute”

## 1.6.1 I’m broadly pessimistic about existing efforts to delay AGI

I feel strongly that it would be better if AGI were invented later than sooner (other things equal, on the current margin), because I think we have a lot more work to do on technical alignment (among many other things), and we’re making progress but are nowhere near ready, and we need to be doing this work way ahead of time (§1.8.4 below).

…But I’m not sure that actual existing efforts towards delaying AGI are helping.

I think the path from here to AGI is bottlenecked by researchers playing with toy models, and publishing stuff on arXiv and GitHub. And I don’t think most existing public advocacy against building AGI will dissuade those researchers.

The problem is: public advocacy is way too centered on LLMs, from my perspective.[^9] Thus, those researchers I mentioned, who are messing around with new paradigms on arXiv, are in a great position to twist “Pause AI” type public advocacy into _support_ for what they’re doing!

_“You don’t like LLMs?”_, the non-LLM AGI capabilities researchers say to the Pause AI people, _“Well how about that! I don’t like LLMs either! Clearly we are on the same team!”_

This is not idle speculation—_**almost everyone**_ **that I can think of who is doing the most dangerous kind of AI capabilities research, the kind aiming to develop a new more-powerful-than-LLM AI paradigm, is** _**already**_ **branding their work in a way that vibes with safety**. For example, see [here](https://x.com/steve47285/status/1902759911592767999) where I push back on someone using the word “controllability” to talk about his work advancing AI capabilities beyond the limits of LLMs. Ditto for “robustness” ([example](https://neuroaisafety.com/1-introduction)), “adaptability” (e.g. in the paper I was criticizing [here](https://www.greaterwrong.com/posts/TCGgiJAinGgcMEByt/the-era-of-experience-has-an-unsolved-technical-alignment)), and even “interpretability” ([details](https://www.greaterwrong.com/posts/gebzzEwn2TaA6rGkc/deep-learning-systems-are-not-less-interpretable-than-logic#comment-i4wN3eG2T88Q9ymHW)).

I think these people are generally sincere but mistaken, and I expect that, just as they have fooled themselves, they will also successfully fool their friends, their colleagues, and government regulators. Well, the government regulators hardly matter anyway, since regulating the activity of “playing with toy models, and publishing stuff on arXiv and GitHub” is a _hell_ of an ask—I think it’s so unlikely to happen that it’s a waste of time to even talk about it, even if it _were_ a good idea all-things-considered.[^10]

(I think non-LLM-focused x-risk outreach and education is good and worthwhile. I expect it to be only slightly helpful for delaying AGI, but “slightly helpful” is still helpful, and more importantly outreach and education has many other good effects like bolstering safety research.)

## 1.6.2 I’m broadly pessimistic about existing efforts towards regulating AGI

Once the new paradigm is known and developed (see below), the actors able to train ASI from scratch will probably number in the tens of thousands, spread all around the world. We’re not just talking about five giant firms with gazillion-dollar data centers, as LLM-focused people tend to imagine.

Thus, for example, if governments know where all the giant data centers are and what code they’re running—well, I guess that’s probably better than governments _not_ knowing that. But I think it’s only marginally helpful, in itself.

(That’s not to say that there is nothing useful happening in the space of regulating AGI. There are various things that would be slightly helpful,[^11] and again, slightly helpful is still helpful.)

## 1.6.3 I expect that, almost as soon as we have AGI at all, we will have AGI that could survive indefinitely without humans

A classic x-risk argument says that ambitious callous AGIs would be motivated to wipe out humans in order to better accomplish their goals. And then a classic anti-x-risk counterargument replies that no, wiping out humans would be a murder-suicide, because there would be no one to run the electrical grid and chip factories etc. And while murder-suicide is a _possible_ AGI motivation, it’s a less likely motivation than the AGI having long-term goals that benefit from its own survival.

Then what’s the pro-x-risk _counter_\-counter-argument?

One approach is to tell a story that involves AGI maneuvering into power, then the world builds ever more chips and robots over a few decades, and _then_ human extinction happens (more in [“Response to Dileep George: AGI safety warrants planning ahead” §3.3.4](https://www.greaterwrong.com/posts/LJD4C7KAr64onL8fq/response-to-dileep-george-agi-safety-warrants-planning-ahead#3_3_4_The_timescale_of_recent_progress_in_industrial_automation_and_robotics_is_not_necessarily_indicative_of_how_quickly_AGI_may_pose_an_extinction_risk_) or [this Carl Shulman interview](https://www.dwarkeshpatel.com/p/carl-shulman-2)).

…But what I really believe is that AGIs could wipe out humans and bootstrap their way back to running the world on their own, after _very_ little prep work—see [“What does it take to defend the world against out-of-control AGIs?” §3.3.3](https://www.greaterwrong.com/posts/LFNXiQuGrar3duBzJ/what-does-it-take-to-defend-the-world-against-out-of-control#3_3_3_What_do_we_learn_about_societal_resilience_against_AGIs__from_the_fact_that_we_humans_have_not_already_wiped_ourselves_out__:~:text=AGIs%20are%20reliant%20on%20a%20functioning%20human%20civilization) for details. And this hypothesis starts seeming much more plausible if there are already enough chips lying around to run hundreds of millions of human-level human-speed AGIs. And that’s what I expect to be the case.

So again, this isn’t much of a crux for doom, but I still feel like it’s an important ingredient of the picture in my head.

# 1.7 Very little R&D separating “seemingly irrelevant” from ASI

I think that, once this next paradigm is doing _anything at all_ that seems impressive and proto-AGI-ish,[^12] there’s just very little extra work required to get to ASI (≈ figuring things out much better and faster than humans in essentially all domains). How much is “very little”? I dunno, maybe **0–30 person-years of R&D**? Contrast that with [AI-2027’s estimate that crossing that gap will take _millions_ of person-years of R&D](https://www.greaterwrong.com/posts/btHmC88KCZdzimBCM/steve2152-s-shortform#comment-fqYrmHE9bdRoSBFy8).

Why am I expecting this? I think the main reason is what I wrote about the “simple(ish) core of intelligence” in §1.3 above.

But here are a couple additional hints about where I’m coming from:

## 1.7.1 For a non-imitation-learning paradigm, getting to “relevant at all” is only slightly easier than getting to superintelligence

I’m definitely not saying that it will be easy to develop the future scary paradigm to ASI _from scratch_. Instead I’m talking about getting to ASI from the point where the paradigm has already crossed the threshold of being clearly relevant to AGI. (LLMs are already well past this threshold, but the future scary paradigm is obviously not.) In particular, this would be the stage where lots of people believe it’s a path to AGI in the very near future, where it’s being widely used for intellectual work, and/​or it’s doing stuff clearly related to the Safe & Beneficial AGI problem, by creating visibly impressive and proto-AGI-ish useful artifacts.

It takes a lot of work to get past that threshold! Especially given the existence of LLMs. (That is: the next paradigm will struggle to get much attention, or make much money, until the next paradigm is doing things that LLMs can’t do—and LLMs can do a lot!)

![](https://www.greaterwrong.com/proxy-assets/254U0IE0CIFU8KF6NJ1TBH8NEI)

Why do I think getting to “relevant at all” takes most of the work? This comes down to a key disanalogy between LLMs and brain-like AGI, one which I’ll discuss much more in the [next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard).

The power of LLMs comes almost entirely from imitation learning on human text. This leads to powerful capabilities quickly, but with a natural ceiling (i.e., existing human knowledge), beyond which it’s unclear how to make AI much better.

Brain-like AGI does not involve that kind of imitation learning (again, more in the [next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard)). Granted, I expect brain-like AGI to also “learn from humans” in a loose sense, just as humans learn from other humans. But the details are profoundly different from the kind of imitation learning used by LLMs. For example, if Alice says something I don’t understand, I will _be aware_ of that fact, and I’ll reply “huh?”. I won’t (usually) just start repeating what Alice says in that same context. Or if I do, this will not get me to any new capability that LLMs aren’t already covering much better. LLMs, after all, are _virtuosos_ at simply repeating what they heard people say during pretraining, doing so with extraordinary nuance and contextual sensitivity.

As another suggestive example, kids growing up exposed to grammatical language will learn that language, but kids growing up _not_ exposed to grammatical language will simply create a new grammatical language from scratch, as in [Nicaraguan Sign Language](https://en.wikipedia.org/wiki/Nicaraguan_Sign_Language) and [creoles](https://en.wikipedia.org/wiki/Creole_language). (Try training an LLM from random initialization, with zero tokens of grammatical language anywhere in its training data or prompt. It’s not gonna spontaneously emit grammatical language!) I think that’s a good illustration of why imitation learning is just entirely the wrong way to think about what’s going on with brain algorithms and brain-like AGI.

For brain-like AGI, all the potential blockers to ASI that I can imagine, would _also_ be potential blockers for crossing that earlier threshold of being clearly relevant to AGI at all, a threshold that requires using language, performing meaningful intellectual work that LLMs can’t do, and so on.

Instead of imitation learning, a better analogy is to AlphaZero, in that the model starts from scratch and has to laboriously work its way up to human-level understanding. It can’t just regurgitate human-level understanding for free. And I think that, if it can climb up to human-level understanding, it can climb _past_ human-level understanding too, with a trivial amount of extra R&D work and more training time—just as, by analogy, it takes a lot of work to get AlphaZero to the level of a skilled human, but then takes very little _extra_ work to make it strongly superhuman.

![](https://www.greaterwrong.com/proxy-assets/2VQHI4LC2ECG4B6Q0NFURSIE59)

Imitation learning, e.g. LLM pretraining ([§2.3.2 of the next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard#2_3_2_LLM_pretraining_magically_transmutes_observations_into_behavior__in_a_way_that_is_profoundly_disanalogous_to_how_brains_work)), _starts_ at human-level understanding, getting that part “for free”. Whereas in the absence of imitation learning, the model needs to climb its way up to human-level understanding. And once it can do that, I think it shouldn’t take much new R&D (if any) to climb _past_ human-level understanding.

And speaking of strongly superhuman:

## 1.7.2 “Plenty of room at the top”

The human brain algorithm has lots of room for capabilities improvement, including (1) more neurons, (2) speed, (3) motivation (e.g. intellectual curiosity, being interested in ideas and getting things done rather than status and gossip), (4) anything else that makes human geniuses tower over human midwits, but much more of it, (5) things like cloning, merging weight-updates from clones, high-bandwidth communication, etc. More at [Response to Blake Richards: AGI, generality, alignment, & loss functions §3.2](https://www.greaterwrong.com/posts/rgPxEKFBLpLqJpMBM/response-to-blake-richards-agi-generality-alignment-and-loss#3_2_Cranking_up_our_example_beyond_John_von_Neumann).

## 1.7.3 What’s the rate-limiter?

One Paul-Christiano-style counterargument (cf. his post [“Takeoff speeds”](https://sideways-view.com/2018/02/24/takeoff-speeds/)) would be: “All those things you listed under ‘plenty of room at the top’ above for why AGIs can outperform humans—scale, speed, cloning, etc.—are things that could happen before, not after, human-level, making up for some other deficiency, as opposed to your implied suggestion that we’ll get to human-level in a human-brain-like way _first_, and only _then_ rapidly scale, speed it up, clone many copies, etc.”

My rebuttal is: for a smooth-takeoff view, there has to be _some_ correspondingly-slow-to-remove bottleneck that limits the rate of progress. In other words, you can say “If Ingredient X is an easy huge source of AGI competence, then it won’t be the rate-limiter, instead something else will be”. But you can’t say that about _every_ ingredient! There has to be a “something else” which is an actual rate-limiter, that _doesn’t_ prevent the paradigm from doing impressive things clearly on track towards AGI, but that _does_ prevent it from being ASI, even after hundreds of person-years of experimentation.[^13] And I’m just not seeing what that could be.

Another point is: once people basically understand how the human brain figures things out in broad outline, there will be a “neuroscience overhang” of 100,000 papers about how the brain works in excruciating detail, and (I claim) it will rapidly become straightforward to understand and integrate all the little tricks that the brain uses into AI, if people get stuck on anything.

**\[ADDED JULY 2026:** See also my later post [“The nature of LLM algorithmic progress”](https://www.greaterwrong.com/posts/sGNFtWbXiLJg2hLzK/the-nature-of-llm-algorithmic-progress), especially [§4](https://www.greaterwrong.com/posts/sGNFtWbXiLJg2hLzK/the-nature-of-llm-algorithmic-progress#4__Optional_bonus_section__why_does_this_matter_), discussing the popular narrative that LLMs have a long tail of algorithmic improvements, adding up to many orders of magnitude over many years. In the post, I argue that this narrative is somewhat misleading, but to the extent that it’s true, it’s coming from specific aspects of LLMs that would not apply to brain-like AGI, particularly LLMs’ reliance on data and compute.\]

# 1.8 Downstream consequences of “very little R&D separating ‘seemingly irrelevant’ from ‘ASI’”

## 1.8.1 Very sharp takeoff in wall-clock time

I wind up feeling like the wall-clock time between the new paradigm being “seemingly irrelevant to AGI” and ASI is, I dunno, two years on the high side, and zero on the low side.

Specifically, on the low side, I wouldn’t rule out the possibility that a _single training run_ is the first to surpass both the “clearly relevant to AGI” threshold and the ASI threshold, in which case they would happen basically simultaneously (perhaps within the same week).

![](https://www.greaterwrong.com/proxy-assets/25GR5M2UI17CA5KNUQKJMNF3PI)

{--{"author":"AI","timestamp":1787568107653}@@Source: [waitbutwhy](https://waitbutwhy.com/2015/01/artificial-intelligence-revolution-2.html)--}{++{"author":"AI","timestamp":1787568107653}@@_Source: [waitbutwhy](https://waitbutwhy.com/2015/01/artificial-intelligence-revolution-2.html)_++}

To be clear, the resulting ASI after those 0–2 years would not be an AI that _already_ knows everything about everything. AGI and ASI (in my opinion) aren’t about _already_ knowing things, but rather they’re about _not_ knowing things, yet being able to autonomously figure them out (§1.7.1 above). So the thing we get after the 0–2 years is an AI that knows a lot about a lot, and if it wants to dive deeper into some domain, it can do so, picking it up with _far_ more speed, depth, and insight than any human could.

Think of an army of [a million super-speed telepathic scaled-up John von Neumann clones](https://www.greaterwrong.com/posts/rgPxEKFBLpLqJpMBM/response-to-blake-richards-agi-generality-alignment-and-loss#3_2_Cranking_up_our_example_beyond_John_von_Neumann). If you ask them some question about cryptocurrency, then maybe they won’t know the answer off the top of their head, because maybe it happens that there wasn’t any information about cryptocurrency in their training environment to date. But then they’ll go spend a day of wall-clock time (≈ months or years of subjective time) reading up on cryptocurrency and all its prerequisites, and playing with the code, and so on, and _then_ they’ll have a deep, beyond-world-expert-level understanding.

### 1.8.1.1 But what about training time?

Even if the next paradigm requires very few person-years of R&D to get from “clearly relevant to ASI” to “actual ASI”, it may take a long time if the individual training runs are slow. But I don’t think that will be much of a limiter.

Instead, I expect that the next paradigm will involve so little compute, and be so amenable to parallelization, that trainings from “birth” (random initialization) to adult-human-level will take maybe a couple weeks, notwithstanding the fact that human brains require decades.[^14] And I think picking the low-hanging fruit of efficiency and parallelization will happen early on, probably during the earlier “seemingly irrelevant” stage—why would anyone ever run a year-long training, when they can instead spend a few months accelerating and parallelizing the algorithm, and then run the same training much faster?

### 1.8.1.2 But what if we _try_ to make takeoff smoother?

The wall-clock time for takeoff depends in part on people making decisions, and people could _decide_ to go actually slowly and incrementally. Even in the “single training run” case, heck, in principle, that training run could happen over the course of a zillion years, with gradient descent being performed by one guy with an abacus. But given how little compute and R&D are involved in getting to ASI, I think the only way to get deliberate slowdown would involve excellent secrecy on the algorithms, and one group (or consortium) way in the lead, and then this one group “burns their lead” in order to do incremental testing and other safety interventions.[^15]

We should keep possibilities like that in mind. But I see it as realistically making takeoff smoother by months, at best, not years.

## 1.8.2 Sharp takeoff even without recursive self-improvement

As mentioned above, some LLM-focused people like the [AI-2027](https://ai-2027.com/) authors agree with me about takeoff being pretty sharp, with the world radically changing over the course of months rather than years. But they get that conclusion via a very different path than I do.

Recall from [Bostrom (2014)](https://en.wikipedia.org/wiki/Superintelligence:_Paths,_Dangers,_Strategies) the (qualitative) formula:

The LLM-focused people get fast “rate of change of intelligence” under an assumption that “recalcitrance” (difficulty of improving AI) is high and steeply increasing, but the “optimization power” brought to bear on improving AI is _even higher_, and _even more_ steeply increasing.

Whereas I think we’re in the wrong paradigm today, but when that changes, recalcitrance will be quite low, at least across the range from “doing anything impressive whatsoever” to ASI. So we’ll get sharp takeoff (across that range) even without any particular increase in optimization power being applied to AI research.

### 1.8.2.1 …But recursive self-improvement could also happen

Of course, somewhere between “doing anything impressive whatsoever” and ASI, we’ll get AIs that can do excellent AI capabilities research. And that could make takeoff faster still.[^16] But I don’t think that would change my general picture very much; it would just shorten this already-short period a bit further, by effectively clipping off the end of it.

This is an area where I kinda disagree with not just Paul Christiano but also Eliezer, who historically has seemed to put a lot of emphasis on the ability of AI to do excellent AI R&D. I think where Eliezer was coming from (see e.g. [Intelligence Explosion Microeconomics (2013) p56](https://intelligence.org/files/IEM.pdf#page=56)) was: human brains are comically inefficient (in his view), and human institutions even more so, and thus AI is going to be much better than humans at AI R&D, leading to rapid self-improvement. Whereas I think that’s kinda missing the point, because by the time AI is already that good at AI R&D, we’re already _after_ the critical and controversial part. Remember the “simple(ish) core of intelligence” in §1.3 above—I think AI will get that good at AI R&D via a kind of competence that generalizes into every other domain too.

In other words, I think that, if you understand the secret sauce of the human brain, then you straightforwardly and quickly get to a ASI at the level of [a million super-speed telepathic scaled-up John von Neumann clones](https://www.greaterwrong.com/posts/rgPxEKFBLpLqJpMBM/response-to-blake-richards-agi-generality-alignment-and-loss#3_2_Cranking_up_our_example_beyond_John_von_Neumann). Then Eliezer would respond: “Ah, but then that super John von Neumann clone army would be able to do some kick-ass AI research to make their algorithms _even more powerful still_!” And, yeah! That’s true! But by that point, does it even matter?

## 1.8.3 Next-paradigm AI probably won’t be “deployed” at all, and ASI will probably show up in a world not wildly different from today’s

A lot of things seem to point in that direction, including:

-   As above, I expect that, within 2 years (or much less) before ASI, the next-paradigm AIs will not be able to appreciably help in any intellectual work of note, and to be generally unimpressive, little-known, little-used, and incapable of doing anything at all that superficially rings of AGI (i.e., far less impressive and useful than LLMs today);
    
-   The compute requirements will be so low that there will be little pressure to get immediate revenue—the R&D won’t be bottlenecked on getting new investments to buy or rent ever more compute;
    
-   Any engineer working towards deploying the current best model could instead be spending her time on making the model work much better—a project which will have a ton of very obvious low-hanging fruit, and be amenable to cheap parallel experimentation;
    
-   There may be safety or ethical[^17] concerns delaying the deployment of these new-paradigm AIs;
    
-   Or more generally, it might just take some time while people are studying and getting a sense for these AIs, before offering them as a widespread service. (And even longer before many people start using this new service.)
    

Indeed, I’m not even sure if there will be much “internal deployment” to speak of, for the same reasons. I think ASI may well arrive before the developers have really gotten past the stage of testing and exploration.

So I think the Eliezer-ish scenario where strong superintelligence escapes onto the internet, in a world otherwise much like today, is quite plausible, and is my central expectation right now.

Of course, the future world won’t be _exactly_ like today. It will presumably have more and better chips. It will have better, cheaper, and far more widespread LLMs, and people will take them for granted, complain about them, and/​or forget what life was like before them, just as we do now for cell phones and social media. The already-ongoing [semantic bleaching](https://www.merriam-webster.com/grammar/very-actually-and-other-examples-of-semantic-bleaching) of the terms “AGI” and “ASI” will continue, until the terms become just meaningless AI company marketing speak. Various things will happen in geopolitics. Perhaps some early version of next-paradigm-AI will be getting used profitably in e.g. the robotics sector.

…But nothing like the kind of obvious common-knowledge pre-ASI craziness envisioned in Paul-style smooth-takeoff scenarios ([e.g.](https://www.greaterwrong.com/posts/vwLxd6hhFvPbvKmBH/yudkowsky-and-christiano-discuss-takeoff-speeds) “There will be a complete 4 year interval in which world output doubles, before the first 1 year interval in which world output doubles.”).

## 1.8.4 We better sort out technical alignment, sandbox test protocols, etc., before the new paradigm seems even relevant at all, let alone scary

Needless to say, if I’m right, then we need to be doing serious prep work for this next-paradigm AI, even while this next-paradigm AI is obscure, seemingly irrelevant, and only good for running toy-model demos or unsexy niche applications. Or maybe before they’re even good for any of that!

Luckily, if the next paradigm is brain-like AGI, as I expect, then we can study brains right now, and thus have at least _something_ to go on in understanding the nature of the threat and what to do about it. That’s of course [what I’m working on myself](https://www.greaterwrong.com/s/HzcM2dkCq7fwXBej8).

## 1.8.5 AI-assisted alignment research seems pretty doomed

The obvious, well-known problem with AI-assisted alignment research is the chicken-and-egg problem. Unaligned AIs won’t _actually_ care about robustly solving the alignment problem. So at best, the AIs will care only about impressing us—and we have abundant empirical evidence that people can be impressed by incorrect alignment ideas. At worst, the AIs will be trying to deceive and manipulate us. See further discussion in [§4 of my post “Reward Button Alignment”](https://www.greaterwrong.com/posts/JrTk2pbqp7BFwPAKw/reward-button-alignment#4__Can__reward_button_alignment__be_used_as_the_first_stage_of_a_bootstrapping____AI_control__ish_plan_).

But in the context of this post, we have an additional problem on top of that: I expect that, once the next-paradigm AIs are competent enough to meaningfully contribute to alignment research at all, they will be _very easily_ able to invent ASI. Inventing ASI will be (at that point) much, much easier than alignment research—the former will entail just a bit more iteration and putting pieces together (since we’ll already be almost there!), whereas the latter will entail tricky conceptual work, anticipating novel problems, and out-of-the-box thinking.

(I’m talking specifically about getting help from AI-of-the-next-paradigm. A different topic is getting help from LLMs. I’m all for getting help from LLMs where possible! But as I mentioned in §1.4.4 above, I expect that the role of LLMs is, and will continue to be, as a mundane productivity enhancer in the same bucket as Integrated Development Environments (IDEs), PyTorch, arXiv, google, etc.,[^18] as opposed to an autonomous researcher akin to humans. I just don’t think they’ll get _that_ good.)

## 1.8.6 The rest of “AI for AI safety” seems pretty doomed too

[@Joe Carlsmith](https://www.greaterwrong.com/users/joe-carlsmith?mention=user)’s “[AI for AI safety](https://www.greaterwrong.com/posts/F3j4xqpxjxgQD3xXh/ai-for-ai-safety)” brings up three categories of things to do with AI to make the ASI risk situation better:

> -   _Safety progress_: our ability to develop new levels of AI capability safely,
>     
> -   _Risk evaluation_: our ability to track and forecast the level of risk that a given sort of AI capability development involves, and
>     
> -   _Capability restraint_: our ability to steer and restrain AI capability development when doing so is necessary for maintaining safety.
>     

I don’t really see any of these things working, at least not in the form that Joe and the other [“AI Control”](https://www.greaterwrong.com/w/ai-control) people seem to be imagining. Takeoff, sharp as it is, will get very much sharper still if word gets out about how this kind of AI works, and then there’d be no time to get anything done. (And “capability restraint” via governance would be off the table, given how little compute is required, see §1.5–§1.6 above.) Or if things stay mum, then that rules out public risk evaluations, widespread alignment research, or most kinds of AI-assisted societal resilience.

Moreover, the continuous learning nature of the future paradigm (see [§1 of “Sharp Left Turn” discourse: An opinionated review](https://www.greaterwrong.com/posts/2yLyT6kB7BQvTfEuZ/sharp-left-turn-discourse-an-opinionated-review#1__Background__Autonomous_learning)) would mean that “AI capabilities” are hard to pin down through capabilities elicitation—the AI might not understand something when you test it, but then later it could figure it out.

![](https://www.greaterwrong.com/proxy-assets/4A1JARH0FKM47DG1155PRMKPLH)

In continuous learning, the notion of pinning down the capabilities of an AI—e.g. its skill at cybersecurity—becomes more fraught, because it’s a moving target.

(See also [§2.6 of the next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard#2_6_Problems_with__amplified_oversight_) on further challenges of weaker AIs supervising stronger AIs.)

Instead, the only forms of “AI for AI safety” that seem plausible to me are much closer to what Eliezer and others were talking about a decade ago: (1) [“pivotal acts”](https://www.greaterwrong.com/w/pivotal-act) (which, [as Scott Alexander points out](https://www.greaterwrong.com/posts/Jo89KvfAs9z7owoZp/pivotal-act-intentions-negative-consequences-and-fallacious#comment-sYyrcRgcFLYdgPRLd), will feel quite different if people actually find themselves living inside the scenario that I expect), and (2) very powerful AIs with good motivations, not straightforwardly following human instructions, but rather doing what they think is best. I won’t justify that in detail; it’s out of scope.

## 1.8.7 Decisive Strategic Advantage (DSA) seems hard to avoid

An AI with a DSA is one that could unilaterally crush or co-opt all competition, should it choose to. This would constitute a terrifying single-point-of-failure for the whole future. Thus, some people understandably wonder whether we could just, y’know, not have that happen. For example, [@Joe Carlsmith](https://www.greaterwrong.com/users/joe-carlsmith?mention=user)’s [On “first critical tries” in AI alignment](https://www.greaterwrong.com/posts/qs7SjiMFoKseZrhxK/on-first-critical-tries-in-ai-alignment): “I think we should try to make it the case that no AI system is ever in a position to kill everyone and take over the world.”

I’ll leave aside the question of whether DSAs are bad—wait, sorry, they’re definitely bad. But maybe every option is bad, in which case we would have to figure out which option is _least_ bad.[^19] Anyway, my goal in this subsection is to argue that, _assuming_ we want to avoid a DSA, I don’t see any way to do that.

A useful notion (after [Eliezer](https://www.greaterwrong.com/posts/yPLr2tnXbiFXkMWvk/an-equilibrium-of-no-free-energy) via [Paul Christiano](https://www.greaterwrong.com/posts/CoZhXrhpQxpy9xw9y/where-i-agree-and-disagree-with-eliezer)) is “free energy”, meaning unexploited opportunities that an AI might use to gain power and influence. It includes profitable opportunities that have not yet been taken. It includes chips that have neither been already hacked into, nor secured, nor had their rental price massively bid upwards. It includes brainwashable humans who have neither been already brainwashed, nor been defended against further brainwashing. Things like that.

Free energy depends on competence: the very same environment may have no free energy for a human, nor for a midwit AI, but tons of free energy for a superintelligent AI.

(Free energy also depends on motivation: an opportunity to extort humans by threatening a bioweapon would constitute “free energy” for an AI that doesn’t care about human welfare or norms, but not for an AI that does. But I’ll put that aside—that gets into offense-defense balance and other issues outside the scope of this series.)

Anyway, Paul Christiano [suggests](https://www.greaterwrong.com/posts/CoZhXrhpQxpy9xw9y/where-i-agree-and-disagree-with-eliezer) that “aligned AI systems can reduce the period of risk of an unaligned AI by … consuming the ‘[free energy](https://www.greaterwrong.com/posts/yPLr2tnXbiFXkMWvk/an-equilibrium-of-no-free-energy)’ that an unaligned AI might have used to grow explosively.”

Well, my concern is that when this next paradigm goes from “basically useless” to “million super-speed scaled-up telepathic John von Neumanns” in two years, or maybe much less than two years, there’s just an _extraordinary_ amount of free energy appearing on the scene, very fast. It’s like a Mount-Everest-sized pile of gunpowder that will definitely be consumed within a matter of months. It’s pleasant to imagine this happening via a very distributed and controlled gradual burn. But _c’mon_. There’s gonna be a massive explosion.

Like, suppose I’m wrong about blasting through human level, and instead we get midwit AGIs for five years, and they get deployed in a widespread, distributed way on chips around the world. Does that use up the free energy? No, because the million-John-von-Neumann ASI is still going to come along after that, and wherever it shows up, it can (if it chooses to) crush or outbid all the midwit AGIs, make crazy nanotech stuff, etc.

Ah, but what if there are not two but _three_ steps from world-very-much-like-today to ASI? Midwit AI for a couple years, then genius AI for a couple years, then million-super-speed-John-von-Neumann ASI after that? Then I claim that at least one of those three steps will unlock an extraordinary amount of free energy, enough to easily crush everything that came before and grab unprecedented power. Ah, but what if it’s five steps instead of three? Ditto. The amount of gradualism necessary to fundamentally change this dynamic is far more gradual than I see as plausible. (Again, my central guess is that there will be no deployment at all before ASI.)

Ah, but what if we ban closed-source AI? Nope, I don’t think it helps. For one thing, that will just make takeoff even sharper in wall-clock time. For another thing, I don’t think that’s realistically enforceable, in this context where a small group with a few chips can put the pieces together into a system of vastly greater competence. For yet another thing, I think there are first-mover advantages, and an unstable dynamic in which **“power begets power”** for these future AIs. For example, the first AI to steal some chips will have extra competence with which to go after more chips—recall the zombie apocalypse movies, where ever more zombies can create ever more zombies. (Except that here, the zombies are superhumanly ambitious, entrepreneurial, patient, etc.) Or they can use the extra compute to self-improve in other ways, or subvert competition.

Ah, but what if some AI safely detonates the free energy by making the world resilient against other powerful AIs—e.g. it autonomously hacks into every data center on Earth, hardens the security (or just destroys the chips!), maybe deploys a “gray goo defense system” or whatever, and then deletes itself? Well, that same AI clearly had a DSA! It’s just that it didn’t use its extraordinary power to install itself as a permanent Singleton—cf. [“AI nanny”](https://www.greaterwrong.com/w/nanny-ai) or [“pivotal act”](https://www.greaterwrong.com/w/pivotal-act). By the same token, one could imagine good outcomes like an AI that sets up a [“long reflection”](https://ea.greaterwrong.com/topics/long-reflection) and defers to the results, shutting itself down when appropriate. Or an AI could gather power and hand it over to some particular human or institution. Many possibilities. But they still involve some AI having a DSA at some point. So they still involve a giant terrifying single point of failure.

# 1.9 Timelines

I don’t know when the next paradigm will arrive, and nobody else does either. I tend to say things like **“probably 5 to 25 years”**. But who knows! For what it’s worth, here are some thoughts related to why I picked those numbers:

_For long-timeline readers who think “probably 5-25 years” is too low:_

I don’t think 2030 is too soon to strongly rule out ASI. A lot can happen in five years. Five years is how long it took to get from “LLMs don’t even exist at all” in 2018 to GPT-4 in 2023. And that’s an _under_\-estimation of how fast things can move. The path from 2018 to GPT-4 involved a number of bottlenecks that the next paradigm won’t—particularly building huge data centers and training up a huge pool of experts in machine learning, parallelization, hardware acceleration and so on.

If we go a bit further, the entirety of deep learning was a backwater as recently as 2012, a mere 13 years ago.

A different argument goes: “the brain is so ridiculously complicated, and we’re so far from reverse-engineering it, that brain-like AGI could very well take much longer than 25 years”. For my response to that school of thought, see [Intro to Brain-Like-AGI Safety §2.8](https://www.greaterwrong.com/posts/wBHSYwqssBGCnwvHg/intro-to-brain-like-agi-safety-2-learning-from-scratch-in#2_8_Timelines_to_brain_like_AGI_part_1_3__how_hard_will_it_be_to_reverse_engineer_the_learning_from_scratch_parts_of_the_brain__well_enough_for_AGI_), [§3.7](https://www.greaterwrong.com/posts/hE56gYi5d68uux9oM/intro-to-brain-like-agi-safety-3-two-subsystems-learning-and#3_7_Timelines_to_brain_like_AGI_part_2_of_3__how_hard_will_it_be_to_reverse_engineer_the_Steering_Subsystem_well_enough_for_AGI_), and [§3.8](https://www.greaterwrong.com/posts/hE56gYi5d68uux9oM/intro-to-brain-like-agi-safety-3-two-subsystems-learning-and#3_8_Timelines_to_brain_like_AGI_part_3_of_3__scaling__debugging__training__etc_). To be clear, it _could_ be more than 25 years. Technological forecasting is very hard. Can’t rule anything out. What do I know?

_For short-timeline readers who think “probably 5-25 years” is too high:_

I don’t think 2050 is so far away that we can confidently rule out that ASI will take that long. See discussion in §1.4.1 above.

I’m also skeptical that people will get there in under 5 years, just based on my own inside view of where people are at right now and the pace of recent progress. But again, who knows? I don’t rule anything out.

## 1.9.1 Downstream consequences of timelines

A lot of people seem to believe that _either_ LLMs will scale to AGI within the next couple years, _or_ this whole AGI thing is stupid hype.

That’s just so insane to me. If AGI is 25 years away (for the sake of argument), that still _obviously_ warrants urgent planning right now. People routinely plan that far out in every other domain—climate change, building infrastructure, investing in personal health, saving for retirement, etc.

For example, if AGI is 25 years away, then, in my estimation, I’m much more likely to die from ASI apocalypse than from all other causes combined. And I’m not even that young! This is a real thing coming up, not a far-off abstract fantasy-land scenario.

Other than that, I don’t think it’s terribly decision-relevant whether we get ASI in 5 years versus 25 years, and accordingly I don’t spend much time thinking about it. We should obviously be contingency-planning for both.

# 1.10 Conclusion

Now you know the kind of “foom” I’m expecting: the development of strong superintelligence from a small group working on a new AI paradigm, with essentially no warning and little resources, and leaving us with meagre hope to constrain this radical transition via conventional balance-of-power or governance mechanisms, and very little opportunity to test and iterate on any system remotely similar to the future scary ones.

So we need to be working frantically on technical alignment, sandbox test protocols, and more generally _having a plan_, right now, long before the future scary paradigm seems obviously on the path to AGI.

(And no, _inventing_ that next AI paradigm is not part of the solution, but rather part of the problem, despite the safety-vibed rhetoric of the researchers who are doing exactly that as we speak—see §1.6.1.)

I am very unhappy to hold that belief, and it’s an unpopular belief in the era of LLMs, but I still think it’s true.

If that’s not bad enough, the [next post](https://www.greaterwrong.com/posts/bnnKGSCHJghAvqPjS/foom-and-doom-2-technical-alignment-is-hard) will argue that, absent some future conceptual breakthrough, this kind of AI will be egregiously misaligned, deceptive, and indifferent to whether its users, programmers, or anyone else lives or dies. Next post: doom!

_Thanks Charlie Steiner, Ishaan Koratkar, Seth Herd, and Justis Mills for critical comments on earlier drafts._

[^1]: For example, (1) On the foom side, Paul Christiano brings up Eliezer Yudkowsky’s past expectation that ASI “would likely emerge from a small group rather than a large industry” as evidence against Eliezer’s judgment and expertise [here \[disagreement 12\]](https://www.greaterwrong.com/posts/CoZhXrhpQxpy9xw9y/where-i-agree-and-disagree-with-eliezer#Disagreements) and as “improbable and crazy” [here](https://www.greaterwrong.com/posts/ZEgQGAjQm5rTAnGuM/beware-boasting-about-non-existent-forecasting-track-records#comment-TG6w2aszHz4m5kcir). (2) On the doom side, the “literal genie” /​ “monkey’s paw” thing, where an AI would follow a specification literally, with catastrophic consequences, as opposed to interpreting natural-language requests with common sense, has likewise largely shifted from a doomer talking point to an anti-doomer mocking point. But I still believe in both those things—see §1.7 and §2.4 respectively.
[^2]: “LLM” means “Large Language Model”. I’m using it as a synonym for a big class of things, also called “foundation models”, that often include multi-modal capabilities, post-training, tool use, scaffolding, and so on.
[^3]: For example, this category includes pretty much everyone at OpenAI, Anthropic, DeepMind, OpenPhil, GovAI, CSET, the AISI’s, and on and on. As another example, I just randomly opened up [Alignment Forum](https://www.alignmentforum.org/allPosts), and had to scroll through 20 posts before I found even one that was not related to the alignment properties of today’s LLMs, or otherwise premised on LLMs scaling continuously to ASI. More broadly, it’s increasingly common in the discourse for people to simply equate “AI” with “LLMs” (as if no other type of AI exists?), and to equate “ASI” with “ASI before 2030 via pure scaling of LLMs” (as if 2040 or 2050 were a distant abstract fantasy-land?). This leads to an endless fountain of bad takes from all sides, which I frequently complain about ([1](https://www.greaterwrong.com/posts/KJRBb43nDxk6mwLcR/ai-doom-from-an-llm-plateau-ist-perspective), [2](https://ea.greaterwrong.com/posts/xkNjpGNfnAYmkFz3s/on-january-1-2030-there-will-be-no-agi-and-agi-will-still#comment-aFKRox2m4qarsoEYs), [3](https://www.greaterwrong.com/posts/YyosBAutg4bzScaLu/thoughts-on-ai-is-easy-to-control-by-pope-and-belrose#comment-Pjvq3KAPJvjaK2awD), [4](https://ea.greaterwrong.com/posts/CwpB3czyjKiG6Pzo8/ai-is-not-taking-over-material-science-for-now-an-analysis#comment-A8iAREausTCvurvkE), …).
[^4]: We have a mere 25,000 genes, and moreover they are tasked with storing not only the full design of our brain algorithm, but also the designs for the nuclear pore complex and hair follicles and everything else. More discussion at [1](https://www.greaterwrong.com/posts/6hDvwJyrwLtxBLHWG/mechanisms-too-simple-for-humans-to-design#comment-MAj5QBYfGDmp7hpGo), [2](https://www.greaterwrong.com/posts/6hDvwJyrwLtxBLHWG/mechanisms-too-simple-for-humans-to-design#comment-2DeQ3NzcqhdK55f69), [3](https://www.greaterwrong.com/posts/AND5pisFSPSpuqo5B/straightforward-steps-to-marginally-improve-odds-of-whole#comment-uFr2ekciLinzej6ib).
[^5]: …in conjunction with the thalamus, basal ganglia, etc.
[^6]: Someone still needs to do R&D for the _hardware_ side of robotics, but not much! Indeed, teleoperated robots seem to be [quite capable and inexpensive](https://www.greaterwrong.com/posts/6Jo4oCzPuXYgmB45q/how-quickly-could-robots-scale-up#comment-h4ZZGaFAJ3ncSqwuw) already today, despite very low demand.
[^7]: Could nuclear chain reactions have happened many years earlier? The obvious answer is no: they were bottlenecked by advances in nuclear physics. Ah, but what if we lump together the nuclear chain reactions with all the supporting theory, and ask why _that whole package_ couldn’t have happened many years earlier? But more to the point, if a historical lack of understanding of nuclear physics was a bottleneck delaying nuclear chain reactions, isn’t it likewise possible that a _current_ lack of understanding of \[????\] is a bottleneck delaying that next AI paradigm today?
[^8]: The training of GPT-4 used 2e25 FLOP (source: [Epoch](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year)), and it probably happened mostly during 2022.
[^9]: I imagine public advocates responding by saying something like: > Well, we _could_ remove LLMs from the narrative, and talk in more general terms about how AGI /​ ASI is some future technology, to be invented at some future date, and here’s why it’s dangerous and why we should urgently prepare for it right now via safety research, institution building, etc. Indeed, we x-risk people were saying exactly that message 10 years ago, and we were saying it 20 years ago, and we were saying it all the way back to [Alan Turing](https://turingarchive.kings.cam.ac.uk/publications-lectures-and-talks-amtb/amt-b-4) 75 years ago. And nobody gave a shit! The vast majority of people, even AI experts, only started paying the slightest attention to AI x-risk when the message changed to: ‘Y’know, those LLMs, the ones that you can see with your own eyes? We’re talking about those. Or maybe, at most, the next generation of those, which are already being built.’. And that message—man, it’s not even _our_ message! It’s a mutant cousin of our message, which, being far more memetically fit, drowned out our actual more nuanced message in the popular discourse. And … yeah, sigh, I dunno.
[^10]: You can’t put nuclear secrets on arXiv, but I find it hard to imagine AI toy model papers ever winding up in that category, even if it were objectively a good idea. See also the time that the [USA put export restrictions on an algorithm](https://en.wikipedia.org/wiki/Export_of_cryptography_from_the_United_States); not only did the restrictions utterly fail to prevent proliferation, but they were also [struck down as unconstitutional](https://en.wikipedia.org/wiki/Bernstein_v._United_States)!
[^11]: Other examples of probably-helpful-on-the-margin governance work: (1) it would be nice if governments would publicly announce that AI companies can collaborate for safety reasons without falling afoul of antitrust law; (2) maybe something about liability, e.g. [this idea](https://x.com/ESYudkowsky/status/1662603303556087809)? No strong opinions, I haven’t thought about it much.
[^12]: Things that qualify as “impressive and proto-AGI-ish” would include helping with AI alignment research, or AI capabilities research, or bioweapons research, or unlocking huge new commercial opportunities, or even just being “visibly intelligent”. LLMs (unlike next-paradigm AIs) are already well into the “impressive and proto-AGI-ish” stage, which by the way is a much lower bar than what Redwood Research people [call](https://www.greaterwrong.com/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled) “transformatively useful AI”. An important aspect is the question of whether there’s widespread belief that this paradigm is a path to AGI, versus whether it’s just another exploratory subfield of AI. As an analogy, think of [probabilistic programming](https://en.wikipedia.org/wiki/Probabilistic_programming) today—it beats a few benchmarks, and it has a few niche commercial applications, and it has some enthusiastic boosters, but mostly nobody cares. (No offense!) My claim is that, _very_ shortly before ASI (in terms of both wall-clock time and R&D effort), the algorithms that will develop into ASI will be similarly niche. That could be true even if the algorithms have some profitable commercial applications in robotics or whatever.
[^13]: Or I suppose the rate-limiter could be that there are 10,000 “something else”s; but see discussion of “simple(ish) core of intelligence” in §1.3 above.
[^14]: I’m assuming 100+-fold speedup compared to humans from a mix of serial speedup, parallelization (see discussion of “parallel experiences” [here](https://www.greaterwrong.com/posts/W6wBmQheDiFmfJqZy/brain-inspired-agi-and-the-lifetime-anchor#comment-DgDKjcuk5saqP293a)), and various human inefficiencies (relative to our goals with AGI). By the way, I mentioned in §1.5 that I think training-from-scratch will be possible with _extraordinarily_ little compute, like a single consumer GPU—and if a single consumer GPU is really all that a researcher had, then maybe training-from-scratch would take many months. But what I actually expect is that researchers will at least be using ten H100s or whatever for their training runs, which is far more powerful, while still being very inexpensive, widely available, and all-but-impossible to track or govern.
[^15]: I’m stating a possibility, not saying that I expect people to actually do this. As the doomer refrain goes: “I do not expect us to [die with that much dignity](https://www.greaterwrong.com/posts/j9Q8bRmwCgXRYAgcJ/miri-announces-new-death-with-dignity-strategy).” See also: [“Aligning an AGI adds significant development time”](https://www.greaterwrong.com/w/aligning-an-agi-adds-significant-development-time) (which I mostly agree with).
[^16]: I say “could” instead of “will” because it’s at least conceivable that humans will remain in control and choose to not have AIs work on AI capabilities research.
[^17]: I expect the future-scary-paradigm AIs to have a pretty obvious ([and IMO legitimate](https://www.greaterwrong.com/posts/32ca3B7rJ93xo9tvb/thoughts-on-agi-consciousness-sentience)) claim to phenomenal consciousness and moral patienthood, much more than LLMs do, thanks to the future scary AIs operating on human-brain-like algorithmic principles. Of course, I don’t know whether future developers will notice or care, and if they do, I don’t know how they’ll act on it. But still, I think the general dismissal of LLM welfare today (_pace_ [Anthropic hiring one guy to think about it](https://arstechnica.com/ai/2024/11/anthropic-hires-its-first-ai-welfare-researcher/)) is not necessarily indicative of what will happen with the next paradigm.
[^18]: For the record, a [poll of my X followers](https://x.com/steve47285/status/1928409263036084290) says that LLMs are a bigger boon to programming than IDEs, although a substantial minority disagreed. Note the obvious caveats that future LLMs will be better than today’s LLMs and that some of my X followers may not be skilled users of LLMs (or IDEs, for that matter).
[^19]: E.g. Michael Nielsen’s [ASI existential risk: reconsidering alignment as a goal](https://michaelnotebook.com/xriskbrief/) emphasizes that multipolar AI scenarios may lead to doom via unsolvable coordination problems related to destructive technologies, related to [Vulnerable World Hypothesis](https://nickbostrom.com/papers/vulnerable.pdf). That seems bad! But the DSA thing seems bad too! Again, I’m not taking a stand here, just trying to understand the situation.
