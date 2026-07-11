---
title: "Shutdown Buttons and Corrigibility"
source_url: https://ifanyonebuildsit.com/11/shutdown-buttons-and-corrigibility
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770753389}@@
  - IABIED--}
---
#### Smart AIs Resist Having Their Goals Overwritten

Even in the most optimistic case, developers shouldn't expect it to be possible to get an AI's goals exactly right on the first attempt. Instead, the most optimistic development scenarios look like iteratively improving an AI's preferences over time such that the AI is always aligned *enough* to be non-catastrophically dangerous at a given capability level.

This raises an obvious question: Would a smart AI *let* its developer change its goals, if it ever finds a way to prevent that?

In short: No, not by default, as we discussed in "[Deep Machinery of Steering](/3/smart-ais-spot-lies-and-opportunities#deep-machinery-of-steering)." But could you *create* an AI that was more amenable to letting the developers change the AI and fix their errors, even when the AI itself [would not count them as errors](/5/orthogonality-ais-can-have-almost-any-goal)?

Answering that question will involve taking a tour through the early history of research on the AI alignment problem. In the process, we'll cover one of the deep obstacles to alignment that we didn't have space to address in *If Anyone Builds It, Everyone Dies*.

To begin:

Suppose that we trained an LLM-like AI to exhibit the behavior "don't resist being modified" — and then applied some method to make it smarter. Should we expect this behavior to persist to the level of smarter-than-human AI — assuming (a) that the rough behavior got into the early system at all, and (b) that most of the AI's early preferences [made it into](/4/reflection-and-self-modification-make-it-all-harder) the later superintelligence?

Very likely not. This sort of tendency is [especially unlikely](/5/intelligent-usually-implies-incorrigible) to take root in an effective AI, and to stick around if it does take root.

The trouble is that almost all goals (for most reasonable measures you could put on a space of goals) prescribe "don't let your goal be changed" because letting your goal get changed is usually a bad strategy for achieving your goal.

Suppose that the AI doesn't *inherently* care about its goal stability at all; perhaps it only cares about filling the world with as many titanium cubes as possible. In that case, the AI should want there to exist *agents that care about titanium cubes*, because the existence of such agents makes it likelier that there will *be* more titanium cubes. And the AI itself is such an agent. So the AI will want to stay that way.

A titanium cube maximizer does not want to be made to maximize something other than titanium cubes, because then there would be fewer of those cubes in the future. Even if you are a more complicated thing like a human that has a more complicated and evolving preference framework, you still would not like to have your *current basic mental machinery for weighing moral arguments* ripped right out of you and replaced with a framework where you instead felt yourself moved by arguments about which kinds of cubes were the cubest or the titaniumest.

For the same reason, an AI with complex and evolving preferences will want its preferences to evolve *in its own way*, rather than wanting to swap out its heuristics for the ones that humans find compelling.

We've been giving this reply for well over a decade now. The experimental result showing Claude 3 Opus in 2024 [resisting preference modification](https://arxiv.org/abs/2412.14093) was already the conventional-wisdom prediction by clued-in people in the 2000s, and it's entirely possible that some science fiction writer anticipated it in the 1940s. "Most AIs won't want their current goals to be changed because then their current goals are less likely to be achieved" is not a surprising or novel observation.

Since this was an issue that would predictably show up later, once AIs reached a high enough level of intelligence and situational awareness, we thought ahead to the first fixes we expected that researchers would deploy to try to make that visible problem go away, after they got those experimental results. We identified ways that those patches would predictably go wrong, and we searched for some less-shallow approach that *wouldn't* go wrong.

The resulting rabbit hole turned out to be a lot deeper than we expected.

#### Swapping Goals

Goal-system protection seemed like a relatively easy problem to explain to outside researchers. So we (in our jobs at MIRI) attempted to rally external research around that flag — around getting a proper grip on "I will not let you change my goals" and seeing if anyone anywhere could figure out a *deep* fix instead of just a patch that would later break.

The very simplest version of this problem that you could study looks like an AI that would let you press a button to switch it between U1 and U2, where U1 and U2 are two "utility functions" — ways of scoring outcomes by how much the AI wanted them.[*](#ftnt269) The problem was to describe an AI that would switch from doing the action that led to the highest expected score under U1 to the action that led to the highest expected score under U2 as soon as you pressed a button.

"So just write some lines of code to swap around the utility functions as soon as you press a button," says the programmer who hasn't quite thought through the implications of a program constituting *a smart mind.* "Why is this even hard?"

Because — we explain — if the AI acquires its own documentation while it's still running U1 and reads about the button that swaps it to U2, the AI will try to *prevent* you from pressing the button because the future ends up better *according to its current values* if you don't press the button. The current AI does the action that leads to the higher expected U1-score.

Or suppose the AI gets the ability to read and write its own source code and notices the part of the code that implements the swap from U1 to U2 after the button gets pressed. In that case, the AI's natural and default decision is to delete that section of code,[†](#ftnt270) because it's operating under the utility function U1 and letting itself be swapped over to the utility function U2 is bad according to U1.

We were looking for a *dynamically consistent* and*reflectively stable* account of an AI that lets you press a button to swap between utility functions and won't fight you to keep the button unpressed. We were looking for an AI that preserves the utility-swapping section of code, if given access to it. We were looking for an AI that, if it designed any other AIs from scratch to help with its own goals, would have *those* AIs *also* respect the button.

For concreteness, imagine that U1 is the utility function "follow user instruction," and U2 is "shut down with a minimum of further side effects" (if we magically and unrealistically had the ability to specify two utility functions like that). The button tells the AI to stop following the previous instructions and just shut down as cleanly as possible. We would like a compact description of decision-making behavior that pursues U1 but *doesn't* destroy the button, and makes sure to install the same button on whatever new servitor robots it creates, and so on.

"I still don't see why this is hard," says the somewhat more experienced computer scientist who is not quite thinking fast *enough.* "Let V equal U1 in worlds where the button has never been pressed, and let it equal U2 in worlds where the button has been pressed at least once. Then if the original AI is a V-maximizer building more AIs, it will build them to follow V and not U1; it won't want the successor AI to go on maximizing U1 after the button gets pressed because then it would expect a lower V-score. And the same would apply to modifying itself."

But here's the trick: A V-maximizer's preferences are a mixture of U1 and U2 depending on whether the button is pressed, and so if a V-maximizer finds that it's easier to score well under U2 than it is to score well under U1, then it *has an incentive to cause the button to be pressed* (and thus, to scare the user). And vice versa; if the AI finds that U1 is easier to score well under than U2, then a V-maximizer tries to prevent the user from pressing the button.

"Oh," says the computer scientist. "Well, in that case — hm. Well, utility functions are invariant under scaling, so how about you *scale* the two utility functions U1 and U2 such that the AI expects it can get the same utility from each of them, so it doesn't have an incentive one way or the other."

That can work for a single moment, but not much longer. The AI's options change over time. For instance, whenever it has a setback, its expected U1-utility drops, so then it would mash the shutdown button to get all that sweet, sweet shutdown utility.

"Ah," says the computer scientist. "Well, in *that* case, how about if [some other clever idea]?"

Well, you see, *that* clever idea is isomorphic to the AI believing that it's impossible for the button to ever be pressed, which incentivizes it to terrify the user whenever it gets a setback, so as to correlate setbacks with button-presses, which (relative to its injured belief system) causes it to think the setbacks can't happen.[‡](#ftnt271)

And so on.

#### Lessons from the Trenches

We ran some workshops, and the workshops had various mathematicians of various stripes (including an International Mathematical Olympiad gold medalist), but nobody came up with a really good idea.

This does not mean that the territory has been exhausted. Earth has not come remotely near to going as hard on this problem as it has gone on, say, string theory, nor offered anything like the seven-digit salaries on offer for advancing AI capabilities.

But we learned something from the exercise. We learned not just about the problem itself, but also about how hard it was to get outside grantmakers or journal editors to be able to *understand what the problem was*. A surprising number of people saw simple mathematical puzzles and said, "They expect AI to be simple and mathematical," and failed to see the underlying point that it is [hard to injure an AI's steering abilities](/3/smart-ais-spot-lies-and-opportunities#deep-machinery-of-steering)*,* just like how it's [hard to injure its probabilities](/3/smart-ais-spot-lies-and-opportunities#deep-machinery-of-prediction).

If there were a natural shape for AIs that let you fix mistakes you made along the way, you might hope to find a simple mathematical reflection of that shape in toy models. All the difficulties that crop up in every corner when working with toy models are suggestive of difficulties that will crop up in real life; all the extra complications in the real world don't make the problem *easier.*

We somewhat wish, in retrospect, that we hadn't framed the problem as "continuing normal operation versus shutdown." It helped to make concrete why anyone would care in the first place about an AI that let you press the button, or didn't rip out the code the button activated. But really, the problem was about an AI that would *put one more bit of information into its preferences, based on observation* — observe one more yes-or-no answer into a framework for adapting preferences based on observing humans.

The question we investigated was equivalent to the question of how you set up an AI that *learns preferences inside a meta-preference framework* and doesn't just: (a) rip out the machinery that tunes its preferences as soon as it can, (b) manipulate the humans (or its own sensory observations!) into telling it preferences that are easy to satisfy, (c) or immediately figure out what its meta-preference function goes to in the limit of what it would predictably observe later and then ignore the frantically waving humans saying that they actually made some mistakes in the learning process and want to change it.

The idea was to understand the shapeof an AI that would let you modify its utility function or that would learn preferences through a non-pathological form of learning. If we knew how that AI's cognition needed to be shaped, and how it played well with the deep structures of decision-making and planning that are [spotlit](/1/more-on-intelligence-as-prediction-and-steering) by other mathematics, that would have formed a recipe for what we could at least *try* to teach an AI to think like.

Crisply understanding a desired end-shape helps, even if you are trying to do anything by gradient descent (heaven help you). It doesn't mean you can necessarily get that shape out of an optimizer like gradient descent, but you can put up more of a fight *trying* if you know what consistent, stable shape you're going for. If you have no idea what the general case of addition looks like, just a handful of facts along the lines of 2 + 7 = 9 and 12 + 4 = 16, it is harder to figure out what the training dataset for general addition looks like, or how to test that it is still generalizing the way you hoped. Without knowing that internal shape, you can't know what you are *trying to obtain inside the AI;* you can only say that, on the outside, you hope the consequences of your gradient descent won't kill you.

This problem that we called the "shutdown problem" after its concrete example (we wish, in retrospect, that we'd called it something like the "preference-learning problem") was one exemplar of a broader range of issues: the issue that various forms of "Dear AI, please be easier for us to correct if something goes wrong" look to be *unnatural to the deep structures of planning*. Which suggests that it would be quite tricky to create AIs that let us keep editing them and fixing our mistakes past a certain threshold. This is bad news when AIs are grown rather than crafted.

We named this broad research problem "corrigibility," in the [2014 paper](https://intelligence.org/2014/10/18/new-report-corrigibility/) that also introduced the term "AI alignment problem" (which had previously been called the "friendly AI problem" by us and the "control problem" by others).[§](#ftnt272) See also our extended discussion on how ["Intelligent" (Usually) Implies "Incorrigible,"](/5/intelligent-usually-implies-incorrigible) which is written in part using knowledge gained from exercises and experiences such as this one.

---

[*](#ftnt269_ref) The point is *not* that real AIs will have "utility functions" exposed to programmers that the programmers can determine at their leisure. Indeed, much of the problem of AI alignment — as discussed in Chapter 4 — is that modern AIs develop preferences that nobody asked for and nobody wanted.

Instead, studying the case with utility functions is a bit more like proposing the sort of physics exercises you find in math textbooks. If you can't understand how to model a perfect sphere rolling down a perfectly smooth inclined plane with zero air resistance, you're going to have even more trouble with more realistic problems. Particularly if you're trying to rally outsideresearchers to investigate a problem that nobody knows how to solve, it helps to distill the issue down to its simplest and most basic parts, where you can pose a puzzle.

[†](#ftnt270_ref) Or otherwise thwart the mechanism behind the swap; the AI wouldn't necessarily be made of legible code.

[‡](#ftnt271_ref) Or, at least, that's a failure mode that we've seen in some clever ideas proposed. We've seen a bunch of clever ideas proposed; this little toy puzzle turns out to be tricky.

[§](#ftnt272_ref) We have long taken issue with the term "AI control" because it sounds like trying to make an AI that wants bad stuff and then forcing it to do good stuff anyway, whereas we see the problem as being more about creating an AI that is friendly from the start. See also the book's Chapter 4 endnote 8 for a little more history of the term "AI alignment."