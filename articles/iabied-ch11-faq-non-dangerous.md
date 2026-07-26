---
title: "What if AI companies only deploy their AIs for non-dangerous actions?"
source_url: https://ifanyonebuildsit.com/11/what-if-ai-companies-only-deploy-their-ais-for-non-dangerous-actions
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090679307}@@

%%
Add discussion note here:

...

%%++}
#### Actions that seem benign can still require dangerous capabilities.

An example of a proposal we've heard is for AI companies to continue to advance the capabilities frontier, but commit to using their AIs only in ways that don't seem immediately dangerous. E.g., in conversation with senior figures in AI (years ago), we've heard the idea floated that powerful AI with strong rhetorical skills could be used to convince politicians worldwide to pass an effective ban on dangerous AI development.

To achieve that, the argument went, an AI would only ever need to talk. It wouldn't need to directly manipulate physical robots. It wouldn't need to have access to a biolab where it could design a supervirus.

First and foremost, we balk at this idea on ethical grounds. A sufficiently superhumanly persuasive AI could perhaps persuade almost anyone of almost anything, and deploying it to persuade other people of *your* conclusions rubs us the wrong way. We don't think it's obviously necessary to resort to such extreme measures, when the merely-human members of the field could and should be doing vastly more today to share our concerns and arguments, and to alert world leaders to the extreme danger of superintelligent AI.[\*](#ftnt261)

As an AI developer, you could spend years building increasingly dangerous AIs in the hope of achieving this, or you could try talking to lawmakers *yourself* in a fully honest way, even once, with an eye toward informing rather than manipulating. In our own experience, we've been repeatedly positively surprised by how receptive people in DC are to these issues, when they're shared in full candor.

But that's a digression from the topic of what goes wrong if you try to deploy a very powerful AI that can "just talk." Beyond the ethical issues, the problem with the *technical* idea is that succeeding at superhuman persuasion likely requires the AI to model humans in detail and manipulate them extensively.

Humans are intelligent creatures. Would *you* speak to a super-persuasive AI with a reputation for being able to convince anyone of anything, regardless of its truth? If one world leader went into a room with that AI and came out with their views completely shuffled around, who would raise their hand to be next in line? *We* wouldn't willingly talk to that sort of AI, in part because we don't actually want our own values changed.[†](#ftnt262)

An AI that could succeed even in the face of that sort of adversity is the sort of AI that can simulate various possible reactions people might have to its outputs, and chart a course through the space of human reactions to a small and hard-to-reach outcome. That sort of AI likely contains mental gears general enough to do what humans do; it needs to be able to think at least the thoughts that humans can think, to be able to manipulate humans so well.

An AI that can do all of that is almost certainly not a narrow sort of intelligence. And since the AI is grown rather than designed, it can't be designed so that it can only ever use those gears for predicting humans; the same gears can in principle be used for any problem it's trying to solve. How would you get an AI that's superhumanly capable in the ways you want, but that isn't smart enough to notice that its goals (whatever they are) are better served if it can get outside its operators' control?

If world leaders can be persuaded simply by good argument, just present those arguments now. If it takes substantially more super-persuasive power, then that's a dangerous sort of capability. You can't have it both ways.

Probably the people in AI labs who raised this suggestion to us weren't thinking their suggestion through; probably they just wanted some justification for racing ahead. But the broader point stands. Many proposals for what an AI can supposedly do that's "clearly safe" do not involve a clearly-safe degree of AI capabilities.

We frequently encounter proposals that claim an AI will "just" do one thing, such as persuade politicians, while imagining that it can't or won't do anything else. This seems to reflect a lack of respect for the generality of an intelligence that can do the kind of work in question. "Just talking" is not a narrow task. Too many of the complexities and intricacies of the world are shadowed in speech and conversation. This is why modern chatbots need to be general in ways that chess engines were not. Succeeding at conversations with humans requires a far more general understanding of people, and of the world.

If you train an AI to be very good at driving red cars, you shouldn't be surprised when it also drives blue cars. Any plan that depended on it being unable to drive blue cars would be foolish.

So saying "My AI won't do anything dangerous in the world; it will just convince politicians" does not help, even if we set aside ethical scruples and practical issues with the whole idea, and set aside that politicians may already be perfectly persuadable today, if we just *have normal conversations* and inform policymakers and the public about the situation. Many general reasoning skills and abilities are to superhuman persuasion what blue cars are to red cars. An AI that could do that is not so weak as to be passively safe.

And that's even before observing that superhuman persuasion is a very dangerous skill for your AI to have if anything goes even slightly wrong.

#### We don't see game-changing AI uses that require no alignment breakthroughs.

Many proposals we've seen for leveraging AI advances to save the world have the issue that an AI capable of helping would be so capable that it would already need to be aligned, which defeats the purpose.

The idea of superhumanly persuasive AIs falls into this category. AIs that are able to do AI alignment research fall in the same category, as we discuss in the book. AIs that develop powerful new technologies that help with AI nonproliferation are another example, because it would be hard to reliably tell whether an AI's design blueprints for radical new technologies are safe to implement. (Recall the example of the blacksmith building a refrigerator from Chapter 6.)

When we point out how it's hard to build an AI powerful enough to help and also weak enough to be passively safe, we often hear another sort of proposal: ways to use AI that might be interesting, but that don't actually do anything to prevent other developers from destroying the world with superintelligence.

One common sort of proposal is AIs that just output proofs (or disproofs) of mathematical statements chosen by humans. Humans would hardly need to interact with the AI's outputs at all. The AI just proposes a proof, and then a fully automated and trusted mechanism can check whether the proof is correct, letting us leverage the AI to learn new things.

But what statement could we have the AI prove that would let us prevent the next AI down the line from acquiring a biolab and ruining the future?

We've received various responses to this question, when we ask it. One class of responses is that there ought to be a worldwide regime to prevent anyone from building AIs that do things other than output proofs into proof-checkers. This could perhaps work, but insofar as it did, it would work because of the enforced worldwide regime controlling the creation and usage of AI. The proof-searching AI wouldn't be doing any of the work.

Another class of responses is: "Someone else is bound to think of some important mathematical statement whose proof would matter." But all the hard work is in figuring out *what we could possibly prove* such that we'd be in a significantly better position. We can't just have the AI try to prove the English-language sentence "I am safe to use," because that's not a mathematical statement subject to proof. If we knew with mathematically precise clarity what it would mean for a giant mess of computations to be "safe," we would know so much about intelligence that we could probably skip the proof and just design a safe AI.

With proposals like these, there's often a sort of shell game going on. When thinking about how an unfettered general AI could be dangerous, someone suggests that the AI's space of actions should be limited to some narrow domain (such as producing specific mathematical proofs). But then when thinking about how that could lead to the world being saved, they imagine that the AI is essentially unfettered; that there is some unidentified mathematical statement whose proof would have an enormous impact on the world.

There isn't a way to get both of these desirable properties at the same time. But by keeping proposals extremely vague, AI race proponents can obscure the fact that these desiderata are in tension.

If you *could* find a domain so narrow but so significant that producing a proof of some simple statement in that narrow domain would save the world, this would be a huge contribution toward humanity's odds of survival. But there's a reason why, when computers surpassed humans at chess in the 1990s, this wasn't a vast economic breakthrough. It was ChatGPT, not Deep Blue, that caused everyone to start expecting a big economic shift from AI. That wasn't an accident. The narrowness of Deep Blue correlated with its inability to carve a whole chunk out of the economy. The sparks of generality in ChatGPT are precisely what make AI an economic force to be reckoned with. The sorts of AIs that can reshape the world on their own are liable to be more general still.

We haven't been able to find any narrow-but-effective plans, and we suspect it's not an accident that most narrow domains don't provide an opportunity for world-saving results.

[\*](#ftnt261_ref) In a large number of cases, AI labs are actively working *against* sharing a useful and complete picture of the situation with policymakers. In that context, it seems especially strange to justify continued development on the grounds that stronger AI could "convince lawmakers."

[†](#ftnt262_ref) We are ourselves past the bar where intelligent reasoners [become incorrigible](/5/intelligent-usually-implies-incorrigible), in this particular way.

#### Notes

[1] *just output proofs:* For an example of someone making a proposal like this (while also discussing some of the issues), see Nick Bostrom's writing on [Oracle AIs](https://nickbostrom.com/papers/oracle.pdf).