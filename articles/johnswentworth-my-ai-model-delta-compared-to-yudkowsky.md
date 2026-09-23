---
title: "My AI Model Delta Compared To Yudkowsky"
author:
  - "johnswentworth"
source_url: "https://www.lesswrong.com/posts/q8uNoJBgcpAe3bSBp/my-ai-model-delta-compared-to-yudkowsky"
published: 2024-06-10
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Comment by Eliezer Yudkowsky - I think that the AI's internal ontology is liable to have some noticeable alignments to human ontology w/r/t the purely predictive aspects of the natural world; it wouldn't surprise me to find distinct thoughts in there about electrons.  As the internal ontology goes to be more about affordances and actions, I expect to find increasing disalignment.  As the internal ontology takes on any reflective aspects, parts of the representation that mix with facts about the AI's internals, I expect to find much larger differences -- not just that the AI has a different concept boundary around \"easy to understand\", say, but that it maybe doesn't have any such internal notion as \"easy to understand\" at all, because easiness isn't in the environment and the AI doesn't have any such thing as \"effort\".  Maybe it's got categories around yieldingness to seven different categories of methods, and/or some general notion of \"can predict at all / can't predict at all\", but no general notion that maps onto human \"easy to understand\" -- though \"easy to understand\" is plausibly general-enough that I wouldn't be unsurprised to find a mapping after all. Corrigibility and actual human values are both heavily reflective concepts.  If you master a requisite level of the prerequisite skill of noticing when a concept definition has a step where its boundary depends on your own internals rather than pure facts about the environment -- which of course most people can't do because they project the category boundary onto the environment, but I have some credit that John Wentworth might be able to do it some -- and then you start mapping out concept definitions about corrigibility or values or god help you CEV, that might help highlight where some of my concern about unnatural abstractions comes in.   Entirely separately, I have concerns about the ability of ML-based technology to robustly point the AI in any builder-intended direction whatsoever, even if there exists some not-too-large adequate ma"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

### Preamble: Delta vs Crux ^preamble-delta-vs-crux

I don’t natively think in terms of [cruxes](https://www.lesswrong.com/w/double-crux). But there’s a similar concept which is more natural for me, which I’ll call a delta.

Imagine that you and I each model the world (or some part of it) as implementing some program. Very oversimplified example: if I learn that e.g. it’s cloudy today, that means the “weather” variable in my program at a particular time[^note-1] takes on the value “cloudy”. Now, suppose your program and my program are exactly the same, except that somewhere in there I think a certain parameter has value 5 and you think it has value 0.3. Even though our _programs_ differ in only that one little spot, we might still expect very different values of lots of variables during execution - in other words, we might have very different beliefs about lots of stuff in the world.

If your model and my model differ in that way, and we’re trying to discuss our different beliefs, then the obvious useful thing-to-do is figure out where that one-parameter difference is.

That’s a delta: one or a few relatively “small”/local differences in belief, which when propagated through our models account for most of the differences in our beliefs.

For those familiar with [Pearl-style causal models](https://www.lesswrong.com/posts/hzuSDMx7pd2uxFc5w/causal-diagrams-and-causal-models): think of a delta as one or a few do() operations which suffice to make my model basically match somebody else’s model, or vice versa.

This post is about my current best guesses at the delta between my AI models and Yudkowsky's AI models. When I apply the delta outlined here to my models, and propagate the implications, my models basically look like Yudkowsky’s as far as I can tell. That said, note that this is _not_ an attempt to pass Eliezer's [Intellectual Turing Test](https://www.lesswrong.com/w/ideological-turing-tests); I'll still be using my own usual frames.

This post might turn into a sequence if there's interest; I already have another one written for Christiano, and people are welcome to suggest others they'd be interested in.

## My AI Model Delta Compared To Yudkowsky ^my-ai-model-delta

Best guess: Eliezer basically rejects the [natural abstraction hypothesis](https://www.lesswrong.com/posts/gvzW46Z3BsaZsLc25/natural-abstractions-key-claims-theorems-and-critiques-1#Why_expect_abstractions_to_be_natural_). He mostly expects AI to use internal ontologies fundamentally alien to the ontologies of humans, at least in the places which matter. [Lethality #33](https://www.lesswrong.com/posts/uMQ3cqWDPHhjtiesc/agi-ruin-a-list-of-lethalities) lays it out succinctly:

> 33.  **The AI does not think like you do**, the AI doesn't have thoughts built up from the same concepts you use, it is utterly alien on a staggering scale.  Nobody knows what the hell GPT-3 is thinking, not only because the matrices are opaque, but because the stuff within that opaque container is, very likely, incredibly alien - nothing that would translate well into comprehensible human thinking, even if we could see past the giant wall of floating-point numbers to what lay behind.

What do my models look like if I propagate that delta? In worlds where natural abstraction basically fails, we are thoroughly and utterly fucked, and a 99% probability of doom strikes me as entirely reasonable and justified.

Here’s one oversimplified doom argument/story in a world where natural abstraction fails hard:

1.  Humanity is going to build superhuman goal-optimizing agents. (‘Cause, like, obviously somebody’s going to do that, there’s no shortage of capabilities researchers loudly advertising that they’re aiming to do that exact thing.) These will be so vastly more powerful than humans that we have basically-zero bargaining power except insofar as AIs are aligned to our interests.
2.  We’re assuming natural abstraction basically fails, so those AI systems will have fundamentally alien internal ontologies. For purposes of this overcompressed version of the argument, we’ll assume a _very_ extreme failure of natural abstraction, such that human concepts cannot be _faithfully and robustly_ translated into the system’s internal ontology _at all_. (For instance, maybe a faithful and robust translation would be so long in the system’s “internal language” that the translation wouldn’t fit in the system.)
3.  Then:
    1.  Obviously full value alignment is out.
    2.  Robust and faithful instruction following or “do what I mean” is out; the meaning of human words/concepts can’t be robustly and faithfully represented in the system’s internal ontology at all.
    3.  Corrigibility is out, unless (here lies one of Eliezer’s hopes) corrigibility turns out to be such a natural concept that it can faithfully and robustly translate even into the ontology of a very alien AI.
    4.  Insofar as an AI cares-as-a-terminal-goal about keeping humans around, it will care about its own alien conception of “humans” which does not match ours, and will happily replace us with less resource-intensive (or otherwise preferable) things which we would not consider “human”.
    5.  Interpretability is, at best, some weak correlative heuristics which won’t generalize well. The [lack of 99% reliability in mechinterp](https://www.lesswrong.com/posts/tEPHGZAb63dfq2v8n/how-useful-is-mechanistic-interpretability) is not just because our current methods are primitive.
    6.  Etc, etc. All of the technical alignment hopes are out, unless we posit some objective natural enough that it can be faithfully and robustly translated into the AI’s internal ontology despite the alien-ness.
4.  It’s not like this gets any _better_ over time; if anything, AIs’ internal ontologies just keep getting more alien as their power level ramps up.
5.  … so we die as soon as one of these superhuman goal-optimizing agents applies enough optimization pressure to the world and the faithfulness/robustness of the translation fails. (Actually, Eliezer expects, we’re likely to die of easier problems before then, but even if our species’ competence is far higher than currently seems, the translation problem would kill us.)
6.  As an added bonus, the AIs will _know all this_ (‘cause, y’know, they’re smart), will therefore know that divergence between their goals and humans’ goals is inevitable (because their goals are in fundamentally alien ontologies and therefore will diverge out-of-distribution), and will therefore be incentivized to strategically hide their long-term intentions until it’s time for the humans to go.

Note that the “oversimplification” of the argument mostly happened at step 2; the actual expectation here would be that a faithful and robust translation of human concepts is _long_ in the AI’s internal language, which means we would need very high precision in order to instill the translation. But that gets into a whole other long discussion.

By contrast, in a world where natural abstraction basically works, the bulk of human concepts can be faithfully and robustly translated into the internal ontology of a strong AI (and the translation isn't super-long). So, all those technical alignment possibilities are back on the table.

That hopefully gives a rough idea of how my models change when I flip the natural abstraction bit. It accounts for most of the currently-known-to-me places where my models diverge from Eliezer’s. I put nontrivial weight (maybe about 10-20%) on the hypothesis that Eliezer is basically correct on this delta, though it’s not my median expectation.

[^note-1]: particular time = particular point in the unrolled execution of the program
