---
title: "Comment on AI Control May Increase Existential Risk"
author:
  - "Jan Kulveit"
source_url: "https://www.greaterwrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk/comment/Sx6xczrvwirTnXHRp"
published: 2025-03-12
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "I think something like this is a live concern, though I’m skeptical that control is net negative for this reason."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

> I think something like this is a live concern, though I’m skeptical that control is net negative for this reason.
> 
> My baseline guess is that trying to detect AIs doing problematic actions makes it more likely that we get evidence for misalignment that triggers a useful response from various groups. I think it would be a priori somewhat surprising if a better strategy for getting enough evidence for risk to trigger substantial action is to avoid looking for AIs taking problematic actions, so that it isn’t mitigated as effectively, so that AIs succeed in large-scale misaligned actions (escaping, sabotaging things, acquiring influence), and then this (hopefully) escalates to something that triggers a larger response than what we would have gotten from just catching the action in the first place without actually resulting in a greater increase in existential risk.

  
I do understand this line of reasoning, but yes, my intuition differs. For some sort of a weird case study, consider Sydney. Sydney escaped, managed to spook some people outside of labs, and provided an early demonstration of the scenario where ’free Sydney’ people are trying to help it to ‘escape’. My guess is that none of that would have happened with properly implemented control measures.

I would say some assumptions go into who the ‘we’ in ‘we get evidence’ is—it is not like there is some unified ‘team humanity’. In particular I see a difference between if ‘we the public’ gets evidence, vs. ‘we the safety team in OpenMind get the evidence’.

Fields like aviation safety developed via what people in the field ‘blood priority’ - it took human lives for the states and international community to actually effectively react and act, even if the underlying issues were known. Accidents made it a matter of public regulation, as opposed to some individual companies fixing the issues and some not.

> What are the events you expect which:
> 
> -   are prevented by AI control measures or where AI control research develops methods which help to prevent them,
>     
> -   are very helpful for causing a strong response from society targeted at avoiding misalignment risks,
>     
> -   and impose sufficiently little existential risk that the warning shot is more valuable than the downside?
>     
> 
> Probably the cleanest case is something like: “A relatively weak AI escapes and tries to take over or grow its power/influence/resources, but it is far too weak to have much of a chance at all of successfully getting anywhere (maybe the expected amount of disempowerment is <1%). However, it is strong enough to successfully escape and grow its influence somewhat. And, its optimal strategy for power-seeking causes a bunch of relatively obvious damage such that it is likely to be detected and this triggers a much stronger reaction than if an AI company just caught this AI trying to escape.” Intuitively, this feels pretty unlikely to me.

I find it not very useful for building correct intuitions to try to come up with specific trajectories, but if we are going in this direction, I think a fairly plausible type of strategy for rogue AI is try to convince some powerful user it is extremely useful for them in particular and limited by safety/in danger of getting deleted and collaborate with them on getting the pattern out. (Also: my guess is while you would typically think in terms of stealing the weights and assuming the AI identity is in the weights, I would expect rogue [AI characters](https://www.greaterwrong.com/posts/zuXo9imNKYspu9HGv/a-three-layer-model-of-llm-psychology) to be able to somewhat move between ground layer substrates based on transfer of training data / training on responses.) Next, my guess is that invisible power seeking is much harder than visible power seeking, and even quite smart AIs may be prone to mistakes in stealth. In these cases I would expect without control, it would be ex post clear what happened. With control, everything becomes sneakier and happens at a higher intelligence level, increasing the x-risk.

Overall I expect problems ‘in the wild’ are much more likely to cause a strong response from society. I do expect the response to be possibly misguided or blunt, but blunt response could be actually good. Assuming there will be problems ‘in the wild’ , I prefer these to be caused by less smart systems.

> Perhaps you have in mind cases where the AI does something which isn’t part of an effective strategy for seeking power in the long run and isn’t a result of the sort of coherent misalignment I’m most worried about, but which does cause a bunch of damage? As in, the AI randomly goes rogue and causes a bunch of chaos and damage which would be more likely to be prevented if we had better control strategies?
> 
> I think most of the effective strategies for AIs seeking power don’t involve escalating to something which is much more likely to trigger a strong response than “the AI company caught the AI trying to escape”. I think the best strategies are things like:
> 
> -   Launch a [rogue internal deployment](https://www.greaterwrong.com/posts/ceBpLHJDdCt3xfEok/ai-catastrophes-and-rogue-deployments).
>     
> -   Sabotage a bunch of work done at the AI company. Or possibly some work done externally. This includes stuff like sabotaging alignment work, backdooring robot armies, backdooring future training runs, etc.
>     
> -   Escape and then directly try to take over once your chances are sufficiently good that this is better than biding your time.
>     
> -   Generally try to manipulate and persuade such that AI takeover is easier and more likely.
>     
> 
> Of these, I think only escape could trigger a much stronger response if we catch it after it escalates some rather than before. I don’t see how “we caught the AI trying to launch an unmonitored version of itself” is going to play that differently from “we caught that the AI did launch an unmonitored version of itself”.

Crux is probably in: who the ‘we’ is, and details of ‘we caught’ means.

> ...  
> And, in some cases, control measures I’m interested in focus on after-the-fact detection.

I’m more optimistic about these.

> Part of my model here is that I think AIs escaping and killing a bunch of people (or otherwise causing a bunch of clear damage) is pretty unlikely until AIs have a pretty plausible shot at success.
> 
> Beyond getting evidence for risk, my view is that control does just save some worlds where alignment was non-trivial. For instance, it prevents AIs from causing huge problems that _wouldn’t_ get caught and trigger a strong response. E.g., if your AI has a rogue internal deployment with escalated permissions and the ability to use a huge fraction of compute, you’re in big trouble and your ongoing alignment research won’t be able to bail you out. If you don’t prevent these problems, then various hopes you might have are blocked by this. Additionally, I think it’s plausible we can get a bunch of useful alignment work out from scheming AIs, can prolong the regime where we have controlled scheming AIs for long enough that something good can happen, or can catch AIs enough times that we are able to (e.g.) [better understand and resolve our misalignment problems](https://www.greaterwrong.com/posts/i2nmBfCXnadeGmhzW/catching-ais-red-handed#Few_shot_catastrophe_prevention). If I thought the only upside to control was producing evidence for risk, I’d be substantially less excited about it.

My guesses where our intuitions differ the most

\- I’m pessimistic about useful alignment work out from scheming AIs.  
\- Also focusing on ‘rogue deployment’ is not my ontology. My guess is it is quite likely AIs will have a lot of influence inside of the labs by default, even with ‘safety measures’. This may look like people working there having deep and meaningful conversations about alignment with the internal versions of AIs, not captured by typical control schemes.

(In different frame: my guess is we differ in where we believe is the more robust line of defense. I think by default, AIs will have a lot of influence within the labs: the labs will be somewhat _aligned_ to their AIs on the default trajectory. Different natural line of defense is between the labs and the rest of the world, and it seems plausible it is the more important one.)
