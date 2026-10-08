---
title: "Pitfalls of Building UDT Agents"
author:
  - "Cole Wyeth"
source_url: "https://www.lesswrong.com/posts/y3zTP6sixGjAkz7xE/pitfalls-of-building-udt-agents"
published: 2025-07-30
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "I've previously argued that UDT may take the Bayesian coherence arguments too far. …"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

I've previously argued that [UDT may take the Bayesian coherence arguments too far](https://www.lesswrong.com/posts/w2QmWzZBTBJ76xuwH/existing-udts-test-the-limits-of-bayesianism-and-consistency).

In that post, I mostly focused on computational uncertainty. I don't think that we have a satisfactory theory of computational uncertainty, and that is a problem for the canonical conception of UDT. However, I think my objection still stands in the absence of computational uncertainty (say, in the framework of my unfinished theory of [AEDT w.r.t. rOSI](https://www.lesswrong.com/posts/B6gumHyuxzR5yn5tH/unbounded-embedded-agency-aedt-w-r-t-rosi)). I want to sharpen this objection and state it more concisely, now that I feel a bit less confused about it.

Briefly: I think that we want to build agents that update at least until they're smarter and know more than us.

## A Compressed Summary of the Controversy on Updating ^a-compressed-summary-of

As a one line summary, updatelessness is basically acausal bargaining. A UDT agent is willing to pay a tax in this universe for some hypothetical benefit in a universe that does not in fact exist (or at least, is not the one we live in). 

This may seem un-intuitive. However, there are many strong justifications for updatelessness, which can usually be described as "Newcomb-like problems." For example, imagine that a perfect predictor (customarily called) Omega flips a coin, promising to pay out 10 dollars on tails, but 1000 dollars on heads if only if you would not have taken the 10 dollars on tails. Agents that win at this problem do not take the 10 dollars on tails - it's much higher expected value to collect the 1000 dollars on heads. That means that an agent facing this problem would be willing to self-modify to become updateless, if possible. 

Without going through more examples, I will take as given that sufficiently powerful agents if given the option self-modify to act something like UDT - _but only for future decisions._ That is, ideal agents want to stop updating. But this is important: I don't see any strong reason that ideal agents would ignore the information they already know, or unroll the updates they've already made. 

If I first learn that the coin has come up tails, and then learn about Omega's bargain, _my_ best option at that point seems to be to take the 10 dollars. After all, I'm not really capable of absolutely locking myself into any policy. But perhaps I should be - perhaps I should decide to implement UDT? I think this is a rather subtle question, which I will return to. My intuition tends to favor taking the money in some circumstances and not in others. But what if Omega demands 10 dollars from me on tails? What if Omega keeps coming back and demanding another 10, on the same coin flip? 

The central principle of UDT is to honor all of the pre-commitments that it would have wanted to make. This means that UDT does not need to make pre-commitments, or to self-modify. It tiles. That seems like a desirable property.

The pro-UDT tiling argument usually goes that, if we build an agent using some other decision theory, and it wants to modify itself to act like UDT (going forward) then it surely seems like that decision theory is bad and we should have just built it to use UDT.

Or, as a question: "If agents want to stop updating as soon as possible, why build them to update at all?"

_Okay, that's the end of my hyper-compressed summary of the discourse so far (which does not necessarily imply that the rest of this post is actually original)._

## A Rejection of Premature Tiling ^a-rejection-of-premature

We want a theory of agency to tell us how to build (or become!) agents that perform well, in the sense of capabilities and alignment, in the real world. This "agent designer" stance has been taken by Laurent Orseau (as "space-time embedded intelligence") and others. It's important to emphasize that the part about _the real world_. The one we are actually living in. This "detail" is often brushed over. I will call this stance the _realist agent designer_ framework - it is what I have previously described as an [agent theory.](https://www.lesswrong.com/posts/MwetLcBPvshg9ePZB/action-theory-is-not-policy-theory-is-not-agent-theory) 

Now, I'd like to argue that the pro-UDT tiling argument does not make sense from a realist agent designer's perspective. 

The reason is that by engaging in acausal trade starting from (implicitly before) the moment of its implementation, a UDT agent is paying tax to universes that we as the agent designers know are not our universe. This is not desirable - it means that UDT is malign in about [the same sense as the Solomonoff prior](https://www.lesswrong.com/posts/KAifhdKr96kMre2zy/changing-my-mind-about-christiano-s-malign-prior-argument).

In the standard picture, a UDT agent actually uses something like the Solomonoff prior (=the universal distribution M) or otherwise believes in some kind of mathematical multiverse. That means that a UDT agent potentially pays tax to all of these universes - in practice, there may or may not be an opportunity for such trades, but when they exist, they come at the expense of _our universe_. 

I think that agent foundations researchers (and generally, many rationalists) have made a big mistake here: _they view this as a good thing._ They want to find a sort of platonic ideal of agency which is as general as possible, which wins-on-average across all mathematical universes.

This is not the right goal, _for either capabilities or alignment_. 

We want to study agents that win in this universe. That means that they should do some learning before they form irreversible commitments - before they stop updating. Pragmatically, I think that agent designs without this property probably fail to take off at all. As a sort of trivialization of this principle, an agent with write access to its own code, which is not somehow legibly labeled as a thing it should not touch until it knows very well what it is doing, will usually just give itself brain damage. But I think the principle goes further: _agents which are trying to succeed across all universes are not the ones that come to power fastest in our universe._ 

I think that unfortunately my own field, algorithmic information theory and specifically the study of universal agents like AIXI, has contributed to this mistake. It encourages thinking about ensembles of environments, like the lower semicomputable chronological semimeasures.[^note-1] But the inventor of AIXI, Marcus Hutter, has not actually made the mistake! Much of his work is concerned with convergence guarantees - convergence to optimal performance in the true environment. That is the antidote. One must focus on the classes of agents which come to perform well in the true environment, specifically, ours. Such agents sometimes fail; one cannot succeed in every environment. We don't care about the ones that suffer (controlled) failure. What's important is that (perhaps after several false starts, in situations that are set up appropriately) they _eventually_ come to dominate. 

And I think that agents which are too updateless too early do not come to dominate.

But: what if they did? What if a UDT agent were implemented with a good (or lucky) enough prior, and grew strong enough that it could afford to pay the acausal tax and still outpace any rival agents?

This is an **alignment failure**. 

We do not want to pay that acausal tax - not unless the agent's prior is sufficiently close to our own beliefs. We only care about this universe. Insofar as such an agent differs from an updateful decision theory like EDT, it differs to our detriment - its prior never washes out, its beliefs never truly merge with ours, and we pay the price. In a sense, such an agent is not corrigible.

But what if we accepted UDT? Would we then be aligned with a UDT agent we built?

I think probably not. This only matters if our priors are nearly identical, and I don't think there is a fully specified objective prior on all possible universes. 

Also, I don't think this is the right question to ask. We who have not formed binding pre-commitments under a veil of ignorance should be glad of it, and should not pay taxes to imaginary worlds. 

## Tiling Concerns ^tiling-concerns

Now, if we accept that we want our agents to continue updating (at least until they know what we know) - how do we achieve this?

I suppose there are two routes.

The first is that we do not give them the option to self-modify. I actually think this can be reasonable. We only need to win this battle until the agents reach roughly our level of intelligence, and we probably don't want even an aligned agent messing with its source code until then. This solution probably seems ugly to some, because it involves building an agent that does not tile. However, (perhaps benefiting from the perspective of AEDT w.r.t. rOSI) I don't see this as a terrible problem. I think that not being able to fully trust that you control the actions of your future selves is actually a core embeddedness problem - which appears also in e.g. [action corruption](https://www.lesswrong.com/posts/WECqiLtQiisqWvhim/free-will-and-dodging-anvils-aixi-off-policy). Why assume it away by only studying agents that tile? Also, as I've argued above, the agents that rise to power probably aren't the ones that lock in their policies too early. So, I think it is reasonable to study the _pre-tiling phase of agent development_. 

The second route is to somehow design the agent so that it does not initially want to self-modify. This branches into various approaches. For instance, we could design a UDT agent with a very carefully chosen prior that is cautious of self-modification. And/or perhaps we can build a corrigible agent, which only trusts its designers to modify its code. This may be easier in practice than in theory - because finding self-modifications that seem good may be computationally hard - and in this respect, it's somewhat connected to the first route, in that an agent is less likely to desire self-modification if promising self-modifications seem more difficult to find. 

## User Manual ^user-manual

 Now the question I've been putting off is - should a human try to implement UDT? I'm still not completely sure about this; mostly because I think there are a multitude of considerations at play in practice. 

As I've made clear, I don't think it's wise to implement an aggressive form of UDT that pays rent to some kind of hypothetical mathematical multiverse. We dodged that bullet by being incapable of self-modification before ~adulthood, and we should be glad of it - in the real world, there are essentially no Newcomb-like problems, and I don't think we humans have payed any real cost for failing to implement UDT up to this point, except perhaps those of us who are bad at lying about what we would do under counterfactual circumstances. 

 Really, it makes little sense for any organism developing within this physical universe to, at any _early_ phase of its lifecycle, conceptualize a mathematical multiverse. By the time we can even consider such ensembles, we already know a lot of basic information about how our world works - the "ensembles" we seriously consider are usually much less exotic (in fact, this is probably why the mathematical multiverse _seems_ exotic). We learn about UDT late in the game.

So, if you're thinking of implementing UDT, I recommend implementing it with respect to some reasonably recent set of beliefs about the world - if you haven't decided already, perhaps everything you know at this moment.

However, I think there are a lot of thorny issues here for us mere mortals. Most salient is that we aren't really capable of forming a definitive commitment to UDT; we have to take seriously the possibility that we might be tempted to defect in the future! Also, we can't ignore the complicating issue of computational uncertainty - which makes implementing UDT both more philosophically challenging and more expensive for us. I don't believe that our world is particularly Newcomb-like, so EDT seems like an excellent approximation in practice, even if we were willing and capable of implementing UDT.    

But - we should seek to _ideally_ implement something resembling such a conservative form of UDT.

[^note-1]: I'd like to do a dialogue with [@Wei Dai](https://www.lesswrong.com/users/wei-dai?mention=user) on this point.
