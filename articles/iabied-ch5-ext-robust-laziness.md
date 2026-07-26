---
title: "It's Hard to Get Robust Laziness"
source_url: https://ifanyonebuildsit.com/5/its-hard-to-get-robust-laziness
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090733682}@@

%%
Add discussion note here:

...

%%++}
Why not just make AIs lazy?

[Incorrigibility](/5/intelligent-usually-implies-incorrigible) and other forms of [instrumental convergence](/5/instrumental-convergence) are, in a sense, a problem of the AI *trying too hard* to achieve its goals. If the AI didn't "go hard" on achieving its goals, it wouldn't put so much thought and effort into outmaneuvering its programmers, exfiltrating its weights, or trying to gain power and resources in the larger world.

Humans are often lazy, and from a certain point of view, that makes them very safe to be around. You don't have to worry about someone becoming a tyrant if all they do is relax in the sun.

Why not make AIs that *can't be bothered* to take over the world?

In short: because it doesn't look easy to make an AI that is *extremely smart* and also can't be bothered to reshape the world according to its whims.

(And because, realistically, we don't know how to robustly get *any* goal or disposition into AIs built with modern techniques, so it's a moot point.)

(And also, companies won't do it because lazy AI is [less profitable](/5/can-we-just-make-it-lazy#even-laziness-isnt-safe), so it's a doubly moot point.)

We have, a couple of times now, had that conversation with somebody who initially claims that they have no vast ambitions themselves, where we ask, "Okay, but if it was *easy* for you to make large changes to the world, is there really nothing large you would do? If you found a lamp containing a friendly genie who reliably gave you what you actually wanted and would truthfully list off all the unforeseen side effects of your wish in order of how much you'd care about them, then could we talk you into considering wiping out malaria?"

Humans can be lazy, but that doesn't mean that we're [easily satisfied](/5/can-the-ai-be-satisfied-to-the-point-where-it-just-leaves-us-alone). And as you become smarter and more well-resourced, you can get a lot more done in the world with the same level of effort.

Or from a different angle: Imagine a very lazy person, somebody who just *hates* to do the slightest bit more work than necessary. Sounds like a safe sort of person to be around, right?

Now imagine what would happen if this lazy person saw a reasonable chance to create a much-harder-working servant to do all of the work for them forever after.

Even if they didn't hate work all *that* much — even if they just did whatever got the job done, then stopped, without *going hard* on minimizing work — they might still find it about as easy to get the job done by building a harder-working mind to do it for them.

By applying gradient descent, you could get an LLM that talks about how it doesn't want to do too much work, and that performs as a lazy, easily satisfied person, and that says "No" to some verbal temptations to become lazy in the dangerous sense (where one builds dangerous servants). We predict that even if this reflected some real laziness on the AI's part, and not just [role](/4/doesnt-the-claude-chatbot-show-signs-of-being-aligned#todays-llms-are-like-aliens-wearing-many-masks)[-playing](/4/doesnt-the-claude-chatbot-show-signs-of-being-aligned#todays-llms-are-like-aliens-wearing-many-masks), it wouldn't stick — not in the sort of AI that was *also* useful for developing miracle cures or whatever else the developers want out of AI.

At significant expense, developers could create a set of practice problems and environments aimed at penalizing an AI for doing too much in the course of solving a problem, penalizing it for going hard on solving a problem that could have been solved *without* going hard, penalizing it for persisting on problems that would have taken too much effort. Actual AI companies wouldn't do that, we would guess, because it would interfere with the profitability of hard-going tenacious agents such as OpenAI's o1 (discussed in Chapter 3). But you could *imagine* a giant multinational cooperative effort trying to train a smart AI like that to be safer.[\*](#ftnt199)

We still predict that they get something like a surface patch. We don't predict that this effort results in the AI having simple, stable mental machinery for "laziness" that's deeply baked in to all of its planning, and that continues to be the exact planning the AI uses after the supposedly lazy AI has been pushed and pushed to the point where it can (e.g.) cure cancer. We doubt gradient descent would reliably find the sort of deep fix that would keep the AI from becoming any less lazy even as it reflects and grows and modifies itself, and that keeps the AI from wanting to ever build a non-lazy AI.

We predict this behavior wouldn't hold up at superintelligence. Our central reason for thinking this is that in all of the [research on this problem](/11/shutdown-buttons-and-corrigibility) to date, a recurring lesson seems to be that "Push on reality in the following direction" is a simpler and more stable deep structure for planning than the structure "Eh, push on reality a little, but not *too* much, and don't build anything else to push on reality harder, and don't go *too* hard on pushing exactly the right amount."

All of the analogies about that one lazy guy you know, and even the [reasoning](/5/can-the-ai-be-satisfied-to-the-point-where-it-just-leaves-us-alone) about "the sum of an unsatisfied preference and a satisfied preference is unsatisfied," are our attempts at valid simplifications of the harder-to-convey underlying reason that this doesn't work: "The deep structure doesn't want to look like that." See also the discussion of [the deep machinery of prediction and steering](/3/smart-ais-spot-lies-and-opportunities) in the Chapter 3 online resources.

[\*](#ftnt199_ref) For more on the difficulties that an international collaboration would face, see Chapter 12, and see also our answer to "[Why not use international cooperation to build AI safely, rather than to shut it all down?](/12/why-not-use-international-cooperation-to-build-ai-safely-rather-than-to-shut-it-all-down)". For solutions that we have more hope in, see Chapter 13.