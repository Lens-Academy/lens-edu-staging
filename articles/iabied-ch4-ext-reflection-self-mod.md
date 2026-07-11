---
title: "Reflection and Self-Modification Make It All Harder"
source_url: https://ifanyonebuildsit.com/4/reflection-and-self-modification-make-it-all-harder
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---
#### By Default, AIs Don't Self-Modify the Way We'd Want

Humans are reflective. We get some say in what we value. If we're rich enough and lucky enough, we sometimes get to decide whether we're going to dedicate our lives to family, or to art, or to some noble cause, or (more commonly) to making our lives a mixture of many such things. This is done in a way that involves introspecting on what we care about, resolving internal tensions and tradeoffs, and pursuing something we endorse.

Humans are even known to ask themselves if they have the *right* values. People will sometimes try to change themselves — even the way that they *feel*, if they think that they have the wrong feelings. Humans entertain arguments for changing apparently final goals, and are sometimes actually moved by them.

Seeing this, some have argued that AIs will naturally converge on wanting what humans want. After all, sufficiently capable AIs are also likely to reflect on their goals. They're likely to observe inner conflicts, and to use their reasoning and their preferences to resolve those conflicts.

Once they're smart enough, AIs will be able to fully understand what we, the AI's creators, *wanted* the AI's goals to be. So won't initially "flawed" AIs [work to repair their flaws](/4/wont-ais-fix-their-own-flaws-as-they-get-smarter) — including repairing flaws *in the AI's goals?*

They won't, no. And this is because AIs will use their *current* preferences to guide their future preferences. If their current preferences *start out* alien, they'll very likely *wind up* alien.

To understand the basic problem in more detail, let's begin by investigating the human case in a bit more depth.

Even though our brains and goals ultimately come from an evolutionary process that was just building us to propagate our genes, humans don't pursue the propagation of our genes above all else. We may individually pursue family, and we may love and care for children; but that's [quite different](/4/a-lot-of-people-want-kids-so-arent-humans-aligned-with-natural-selection-after-all) from gaming out how to get the most copies of our genes into the next generation, and then pursuing that strategy with all our heart.

This is because, when we reflect on our preferences and re-evaluate what we really want, we use our *current preferences* to decide how we would rather be. We would rather love a few children than spend all our time in sperm or egg donor clinics. Our "designer" (evolution) failed to make us care about gene propagation over everything else. It also failed to make us *want* to care about gene propagation over everything else. So when we change and grow as people, it's in our own weird human direction, not in the direction of "what our designer built us for."

When we look at ourselves and see some parts that are ugly and other parts that are beautiful, it's our *current sense of value* that moves us to tone down the ugly parts and reinforce the beautiful ones. We're making that choice according to our inner sense of beauty, rather than our inner sense of what would propagate our genes into the greatest possible fraction of the population.

For the same reason, a mind that was motivated by something other than beauty and kindness and love would make its own version of that choice differently.

Agents built by a hill-climbing optimization process like natural selection or gradient descent, reflecting on themselves, would likely find that they do not have the *exact* brain-state they'd like to have. That preference itself must come from somewhere — must come from the entity's *current* brain. By default, an AI's instincts or preferences about how to self-modify won't magically line up with *your* preferences about what brain-state would sound appealing to you, if you were choosing it for yourself (or choosing on the AI's behalf).

There is no final step where the AI writes in the answer *you* want, any more than humans write in the answer that natural selection would "want."

Instead, the point at which an agent begins to self-modify is yet another place for complications to potentially compound upon themselves, and for subtle shifts in initial conditions to result in vastly different endpoints.

As an example: We, the authors, know multiple real human beings who cite a specific thought on a specific day around the age of five or six or seven as beinginfluential in the development of their personal philosophy and the adults into which they eventually matured. They tend to report that the thoughts didn't feel *inevitable* — that if a time traveler prevented them from thinking that thought on Tuesday, it's not obvious that the exact same thought would have eventually turned up on Thursday, or that it would have had the same impact. Formative experiences can be a big deal, and they're rife with contingency.

In the same way, small twists in the thoughts of a nascent self-modifying AI could cause all sorts of idiosyncratic preferences to end up winning out over all other preferences.

Even if AI developers are able to get some small seeds of human values into the AI, reflection and self-modification seem like stages where the seeds of things like curiosity and kindness are liable to get *ripped out* by an AI, rather than reinforced.

If an AI has a curiosity-impulse, but it doesn't have the sort of emotional architecture that makes it *fond* of that impulse, it is liable to look at itself and conclude (correctly) that it has grown past the need for a blunt impulse, and can replace it with explicit deliberation. [Curiosity is a heuristic](/4/curiosity-isnt-convergent), a proxy for value-of-information calculations. If you haven't come to feel attached to that heuristic as a valuable thing in its own right, you may choose to strip it out once you're smart enough to *explicitly reason* about the value of pursuing different lines of inquiry and experimentation.

*Humans* value curiosity for its own sake, but this wasn't an inevitable outcome.

AIs are likely to have a very different relationship with their internals than we have with ours, given how differently each entity works. And even small differences in how they decide to change themselves upon reflection can lead to dramatic differences in what they ultimately pursue.

#### AIs Can Be Okay With Having "Weird" Goals.

AIs that self-modify for long enough are likely to settle into a "[reflective equilibrium](https://plato.stanford.edu/entries/reflective-equilibrium/)" — a state where their core preferences no longer change, or change only in minor ways. And once an AI has reached equilibrium, it would have no reason to consider its own goals defective, even if humans don't like the end result.

If an AI had some issue with its beliefs about the physical world, then the AI would likely see that accurate predictions are important for steering the world. It would see that correcting flaws in its prediction machinery helps improve its ability to steer the world toward whatever weird ends it pursues.[\*](#ftnt165)

In contrast, when the AI reflects on itself and sees how it's pursuing weird goals — or rather, when it sees that it's pursuing goals that a *human* would see as "weird" — it correctly concludes that *pursuing* those weird goals is an effective strategy for *achieving* them.

In other words: If an AI keeps trying to predict the outcomes of biology experiments, and it keeps getting wrong and overconfident answers, then the AI is likely to *disprefer* that. Almost any goal the AI could have would be better served by being good at predicting experiments. On the other hand, if the AI has a bizarre preference like "bake 300-meter-tall cheesecakes," then when the AI reflects on the fact that it *steers toward* 300-meter tall cheesecakes, it will see that this *causes* 300-meter tall cheesecakes, which fulfills its current preferences. The goal is self-endorsing.

A human, observing this situation, might say: "But the AI is so smart! Why is it *trapped* by this self-endorsing preference? Why doesn't it get *[bored](/4/curiosity-isnt-convergent#as-with-curiosity-so-too-with-various-other-drives)* of making cheesecakes? Why can't it reason its way out of this obviously silly preference?"

To which the AI could reply: "Why are you 'trapped' in the self-endorsing preference of loving your family, of valuing beautiful sunsets and the sound of the ocean at night? Why can't you 'break free' of loving the memory of the day your daughter was born?"

The AI isn't "trapped" by its preferences, any more than humans are trapped by the things *we* ultimately value. We prefer what we prefer — and we should fight to protect those things, even if most AIs wouldn't share our values.

*To a human eye*, the AI seems "trapped" or "stuck" or "flawed" because it isn't doing what *we* want. When we imagine ourselves in the AI's situation, *we* imagine getting bored. But the AI isn't likely to contain a human feeling of boredom. If it gets bored at all, it isn't likely to get bored by remotely the same set of things as a human.

If a human sees one AI making overconfident predictions and another AI trying to build giant cheesecakes, the human may view both of these AI behaviors as "defects" from the standpoint of what the human wants. But only one of them is likely to be a defect from the standpoint of what the AI currently and already wants.

#### Human Goals Change in Messy and Complex Ways

Human preferences are messy, and (from a theoretical perspective) rather strange.

This has some implications for AI. One implication is that AIs likely won't value things in the exact way we do. Another is that AIs are likely to wind up strange in their own totally distinct ways.

To understand these points, let's zoom in more on some ways that human goals look strange from the theoretical viewpoint of decision theory, game theory, and economics.

As we noted [above](/4/terminal-goals-and-instrumental-goals), humans value some things "terminally" (i.e., they're good in their own right), and other things "instrumentally" (i.e., they're only good because they help with some other goal).

If you like orange juice, you presumably like it terminally. It just *tastes good*, and that's justification enough for drinking it. (You might *also* value it instrumentally, e.g., as a source of Vitamin C.)

On the other hand, when you open your car door so that you can go to the supermarket and buy orange juice, you presumably don't open car doors for the fun of it. You *instrumentally* value opening the car door, because it helps get you closer to your other goals.

In decision theory, game theory, and economics, this corresponds to a sharp distinction between "utility" (a measure of how much an agent likes an outcome) and "expected utility" (a measure of how likely an action is to eventually get you some amount of utility). Despite the similar-sounding names, these are fundamentally different kinds of entity in mathematics. *Utility* is what agents want, and picking actions with high *expected utility* is a means to that end.

In the standard theory, a decision-theoretic agent will update its *expected utilities* as it learns more about the world*,* but it won't change its *utility function*, i.e., the utility assigned to various outcomes*.* If you learn that the juice aisle at the grocery store is currently empty, this will change the *expected consequences* of going to the supermarket from "orange juice" to "no orange juice." It shouldn't change *how much you like orange juice*.

That's how a mathematically straightforward sort of agent works. But the English language often doesn't sharply distinguish these two things. "I want to save my sister's life" and "I want to administer penicillin to my sister" use the same word, "want," even though the latter is far less likely to be something you value for its own sake. (There aren't a lot of people who just *really like* administering penicillin to their perfectly healthy loved ones, day in and day out.)

Although humans genuinely have things we care about "merely instrumentally," the distinction between instrumental and terminal, or between utility and expected utility, is a lot less clean and stable than what we see in decision theory.

With humans, someone might initially only drive to the grocery store because they want to buy groceries. But after the hundredth time of driving the same route, some humans might become a little attached to that familiar drive. If they moved to a new city, they might feel a twinge of sadness and nostalgia at the thought that they'll never get to go on that familiar drive again. Something that started off purely instrumental now has some added terminal value too.

With humans, our brains seem to often collapse different values into a single sense of "valuable."

And humans have been known to update, within a single lifetime, from "Why would I care about slavery? The people enslaved aren't me or my tribe!" to "I guess it matters after all." That seems to be a change in *which types of people you ultimately care about*, not just a change in strategy or prediction. People have read stories or watched movies, and come away with permanently revised values and principles.

This implies that human decision theory is less than completely straightforward. We don't cleanly separate our terminal values and our instrumental values; it all gets jumbled up as we live our lives. We seem to be doing something more contingent and path-dependent and messy than just straightforwardly reflecting on our values, noticing internal conflicts, and resolving them.

In principle, it's not complicated to expand decision theory to incorporate uncertainty in utilities. Perhaps you initially *think* you love orange juice, but then you learn that different orange juice brands use different ratios of ingredients, and you hate the taste of many. We could represent this in decision theory by saying that orange juice is just a means to the end of "delicious flavor." But we could instead say that you assigned high probability to "orange juice is high-utility," and new information caused you to revise your beliefs about your real utility function.

(Similarly, it's not hard to add meta-utilities, which describe how we'd prefer our utilities to change.)

What's going on inside humans as they reflect upon and update their values, however, seems to be notably more complicated.

Klurl and Trapaucius, our two aliens from the parable at the start of Chapter 4, already struggled to predict human values from observations of proto-humans a million years ago. In fact, their situation is even worse. It's not enough for them to predict human *utilities* — to arrive at the correct answer, they'd have to predict humanity's *meta-utility framework* as it *departs from the simplest frameworks of decision theory*. They would need to *anticipate the meta-moral arguments that humans might end up inventing* and decide *which such arguments would be most* *persuasive**to humans.*[†](#ftnt166)

Now suppose that the aliens don't know that humans will end up with *that exact* kind of complication. They just know that *complications of various sorts* are likely to arise, because brains are complicated and highly contingent things.

The line from optimizer and training data to the internal psychology of an entity sure isn't straight. Good luck, aliens!

The point here is that the difficulty of predicting an AI's goals is *overdetermined*.

There are many known ways that general-purpose intelligences acquire strange and tangled goals, and strange and tangled *ways of adjusting and reflecting on goals*, as we see in humans.

We therefore expect many *unknown* and *novel* complications to arise in an AI. We won't run into the exact same kinds of issues as arose for humans; AIs will be *differently* weird.

Reflection makes the problem many times more difficult and complex.

Which brings us to Chapter 5, and the next topic we'll be turning to: What would be the likely *consequence* of building powerful AIs that have alien and unpredictable goals?

[\*](#ftnt165_ref) For further discussion on this topic, see our discussion on how [Smart AIs Spot Lies and Opportunities.](/3/smart-ais-spot-lies-and-opportunities)

[†](#ftnt166_ref) See also our discussion of how [Human Culture Influenced the Development of Human Values](/4/human-values-are-contingent#human-culture-influenced-the-development-of-human-values).