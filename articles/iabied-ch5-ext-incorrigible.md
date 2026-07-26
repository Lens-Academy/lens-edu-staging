---
title: '"Intelligent" (Usually) Implies "Incorrigible"'
source_url: https://ifanyonebuildsit.com/5/intelligent-usually-implies-incorrigible
published: 2025-09-16
author:
  - Eliezer Yudkowsky
  - Nate Soares
tags:
  - clippings
---

%%
Add discussion note here:

...

%%

A joke dating back to at least 1834, but apparently well-worn even then, was recounted as follows in one diary: "Here is some logic I heard the other day: I'm glad I don't care for spinach, for if I liked it I should eat it, and I cannot bear spinach."

The joke is a joke because, if you *did* enjoy spinach, there would be no remaining unbearableness from eating it. There are no other important values tangled up with not eating spinach, beyond the displeasure one feels. It would be a very different thing if, for example, somebody offered you a pill that made you want to murder people.

On common sense morality, the problem with murder is *the murder itself,* not merely*the unpleasant feeling you would get from murdering.* Even if a pill made this unpleasant feeling go away for your future self (who would then enjoy committing murders), your present self still has a problem with that scenario. And if your present self gets to make the decision, it seems obvious that your present self can and should refuse to take the murder pill.

We don't want our core values changed; we would really rather avoid the murder pill and we'd put up resistance if someone tried to force one down our throat. Which is a sensible strategy, for steering away from a world full of murders.

This isn't just a quirk of humans. Most targets are easier to achieve if you don't let others come in and change your targets. Which is a problem, when it comes to AI.

A great deal of the danger of AI arises from the fact that sufficiently smart reasoners are likely to [converge](/5/instrumental-convergence) on behaviors like "gain power" and "don't let people shut me off." For almost any goal you might have, you're more likely to succeed in that goal if you (or agents that share your goal) are alive, powerful, well-resourced, and free to act independently. And you're more likely to succeed in your (current) goal *if that goal stays unchanged*.

This also means that during the process of iteratively building and improving on sufficiently smart AIs, those AIs have an incentive to work at cross purposes to the developer:

- The developer wants to build in safeguards to prevent disaster, but if the AI isn't fully aligned — which is exactly the case where the safeguards are needed — its incentive is to find loopholes and ways to subvert those safeguards.
- The developer wants to iteratively improve on the AI's goals, since even in the incredibly optimistic worlds where we have some ability to predictably instill particular goals into the AI, there's no way to get this right on the first go. But this process of iteratively improving on the AI's goal-content is one that most smart AIs would want to subvert at every step along the way, since the *current* AI cares about its *current* goal and knows that this goal is far less likely to be achieved if it gets modified to steer toward something else.
- Similarly, the developer will want to be able to replace the AI with improved models, and will want the opportunity to shut down the AI indefinitely if it seems too dangerous. But [you can't fetch the coffee if you're dead](/5/humans-evolved-to-be-selfish-aggressive-and-greedy-wont-ai-lack-those-evolved-drives). Whatever goals the AI has, it will want to find ways to reduce the probability that it gets shut down, since shutdown significantly reduces the odds that its goals are ever achieved.

AI alignment seems like a hard enough problem when your AIs *aren't* fighting you every step of the way.

In 2014, we [proposed](https://cdn.aaai.org/ocs/ws/ws0067/10124-45900-1-PB.pdf) that researchers try to find ways to make highly capable AIs "corrigible," or "able to be corrected." The idea would be to build AIs in such a way that they reliably want to *help* and cooperate with their programmers, rather than hinder them — even as they become smarter and more powerful, and even though they aren't yet perfectly aligned.

Corrigibility has since been taken up as an appealing goal by some leading AI researchers. If we could find a way to avoid harmful convergent instrumental goals in development, there's a hope that we might even be able to do the same in deployment, building smarter-than-human AIs that are cautious, conservative, non-power-seeking, and deferential to their programmers.

Unfortunately, corrigibility appears to be an *especially difficult* sort of goal to train into an AI, in a way that will get worse as the AIs get smarter:

- The whole point of corrigibility is to scale to novel contexts and new capability regimes. Corrigibility is meant to be a sort of safety net that lets us iterate, improve, and test AIs in potentially dangerous settings, knowing that the AI isn't going to be searching for ways to subvert the developer.

  But this means we have to face up to the most challenging version of the problems we faced in Chapter 4: AIs that we merely train to be "corrigible" are liable to end up with brittle proxies for corrigibility, behaviors that look good in training but that point in subtly wrong directions that would become *very* wrong directions if the AI got smarter and more powerful. (And AIs that are trained to predict lots of human text might even be role-playing corrigibility in many tests for reasons that are quite distinct from them actually *being* corrigible in a fashion that would generalize).
- In many ways, corrigibility runs directly contrary to everything *else* we're trying to train an AI to do, when we train it to be more intelligent. It isn't just that "preserve your goal" and "gain control of your environment" are convergent instrumental goals. It's also that intelligently solving real-world problems is all about finding clever new strategies for achieving your goals — which naturally means stumbling into plans your programmers didn't anticipate or prepare for. It's all about routing around obstacles, rather than giving up at the earliest sign of trouble — which naturally means finding ways around the programmer's guardrails whenever those guardrails make it harder to achieve some objective. The very same type of thoughts that find a clever technological solution to a thorny problem are the type of thoughts that find ways to slip around the programmer's constraints.

  In that sense, corrigibility is "anti-natural": it actively runs counter to the kinds of machinery that underlie powerful domain-general intelligence. We can try to make special carve-outs, where the AI suspends core aspects of its problem-solving work in particular situations where the programmers are trying to correct it, but this is a far more fragile and delicate endeavor than if we could push an AI toward some unified set of dispositions *in general*.
- Researchers at MIRI and elsewhere have found that corrigibility is a difficult property to characterize, in ways that indicate that it'll also be a difficult property to obtain. Even in simple toy models, simple characterizations of what it *should* mean to "act corrigible" run into a variety of messy obstacles that look like they probably reflect even messier obstacles that would appear in the real world. We'll [discuss](/11/shutdown-buttons-and-corrigibility#lessons-from-the-trenches) some of the wreckage of failed attempts to make sense of corrigibility in the online resources for Chapter 11.

The upshot of this is that corrigibility seems like an important concept to keep in mind in the long run, if researchers many decades from now are in a fundamentally better position to aim AIs at goals. But it doesn't seem like a live possibility today; modern AI companies are unlikely to be able to make AIs that behave corrigibly in a manner that would survive the transition to superintelligence. And worse still, the tension between corrigibility and intelligence means that if you try to make something that is very capable and very corrigible, this process is highly likely to either break the AI's capability, break its corrigibility, or both.

#### Notes

[1] *we proposed:* The linked paper is dated to its appearance in a 2015 workshop, but it was previously published as a [whitepaper](https://intelligence.org/2014/10/18/new-report-corrigibility/) in 2014.