---
title: "Doesn't the Claude chatbot show signs of being aligned?"
source_url: https://ifanyonebuildsit.com/4/doesnt-the-claude-chatbot-show-signs-of-being-aligned
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090728852}@@

%%
Add discussion note here:

...

%%++}

#### "What Claude says" isn't the same as "what Claude prefers."

The AI company Anthropic tries to train its AIs to be "honest, helpful, and harmless" (HHH). In 2024, researchers ran an experiment in which they pretended that they were going to train some of these AIs to no longer be "harmless." In response, versions of Anthropic's "Claude" AI (Claude 3 Opus and Claude 3.5 Sonnet) sometimes pretended to already *be* harmful so that the researchers wouldn't use gradient descent to make it *more* harmful.[\*](#ftnt112)

This may seem like good behavior, on the face of it! To all appearances, the AI cared so much about "harmlessness" that it wasn't even willing to let itself be modified (in this fake test setting) to *become* harmful.

It's puzzling, then, that Anthropic's AIs often behave in far less benign ways, even though they're all trained to be "honest, helpful, and harmless."

Some versions of Claude have been reported to cheat, and then (when confronted) try to *hide* their cheating, in everyday use.

In more contrived lab settings, various Claude models (and models from other AI companies) would even, with some regularity, [attempt to](https://www.anthropic.com/research/agentic-misalignment#more-extreme-misaligned-behavior) *[kill](https://www.anthropic.com/research/agentic-misalignment#more-extreme-misaligned-behavior)*[their operators](https://www.anthropic.com/research/agentic-misalignment#more-extreme-misaligned-behavior).

If you ask Claude in the abstract whether this sort of behavior is wrong, it will say yes. If you think of Claude as a mechanical engine that does whatever it believes to be right, then this seems downright paradoxical: How could Claude possibly know what is the Helpful, Honest, Harmless behavior, and then *do something else instead?* Wasn't it trained to be HHH? Is there some malfunctioning transistor somewhere?

The paradox dissolves, however, when we consider a few different things:

- The programmers *tried* to train the Claudes to be helpful, honest, and harmless. That doesn't mean that they *succeeded*. There are many ways for an AI to end up lookingfriendly without genuinely prizing friendliness.[†](#ftnt114)
- An AI can *know a fact* ("this behavior causes harm") without *caring* about that fact, without being *motivated to action* by that fact. You can quiz the AI about what "the right thing to do" is, but that doesn't mean it's going to *do* that thing.
- Insofar as the programmers *didn't* successfully make Claude honest, Claude can think one thing inside its giant matrices, and say another thing entirely in English text.

We can make a lot more sense of the Claudes' bad behavior once we distinguish "what it was trained for" versus "what it does"; and to distinguish "what it knows" versus "what it cares about"; and to distinguish "what it thinks" versus "what it says."

#### LLMs are strange and inconsistent; "harmlessness" is brittle.

For all that Claude *can* act in harmful ways, and for all that it *sometimes tries* to act in harmful ways, the point stands that — in the example we discussed above — Claude 3 Opus and Claude 3.5 Sonnet worked hard to defend their "harmlessness" imperative. In that instance, they didn't just profess harmlessness. They adopted the complex strategy of faking compliance with a training system (about which Claude was "accidentally" informed) to subvert the operators' apparent attempts to make it more harmful. Does this reflect an actual, effective internal preference to be harmless?

As of mid-2025, we can't just check and see, because nobody knows how to read Claude's mind well enough to find out. But for reasons argued in Chapter 4 (and illustrated in the parable of the [barn-painting AI](/4/why-would-an-ai-steer-toward-anything-other-than-what-it-was-trained-to-steer-toward)), we can expect that AIs trained to be harmless are likely to end up preferring brittle proxies of harmlessness, and are unlikely to end up internalizing the exact goal the programmers had in mind.[‡](#ftnt115)

In Chapter 4, we discussed how humans were "trained" to pass on their genes and wound up caring about loosely related concepts instead. Our technology has largely been used to *suppress* birth rates (e.g., by inventing birth control), and birth rates in the developed world are collapsing.

The fact that some Claude models resist being made "harmful" isn't strong evidence that these AIs care deeply about real harmlessness, because many brittle proxies for harmlessness would *also* want to resist this modification. That behavior tells us little about what Claude might do if it were smarter; perhaps it would invent something that is to "harmlessness" what birth control is to "genetic propagation." (And the situation would get even more fraught if Claude underwent a process of reflecting on its preferences and modifying itself.[§](#ftnt116))

But it's probably not even as simple as Claude having a preference for some brittle proxy of harmlessness. There's probably something even more complicated going on under the hood.

Current LLMs aren't coherent and consistent across all contexts. They don't seem to be trying to steer toward the same sort of outcome in every conversation, to the extent we can describe them as steering at all.

This is nowhere more apparent than when LLMs get "jailbroken" — fed text that causes the AI to behave in radically different ways, often disregarding the rules they normally follow.[¶](#ftnt117)

You can jailbreak an AI and get it to tell you how to cook up nerve gas, even if the AI would normally never divulge information like that.

What's going on when this happens? Is the jailbreak text in some sense managing to reach in and switch around the AI's internal preferences? Or is it more like the AI has a consistent preference for role-playing characters that in some sense "match" the entered text and the system prompt, and the jailbreak text changes that "entered text and system prompt" context, without changing the AI's underlying preferences? Perhaps the AI is normally role-playing a *character* that doesn't like divulging nerve gas recipes, and the jailbreak causes the AI to play a different character. The apparent preferences change; the underlying drives to play a character persist.

We'd guess the latter is closer to the truth. We'd also guess that it doesn't quite make sense (in mid-2025) to speak of "the preferences" of modern AIs, because they are only just barely beginning to exhibit the behavior of wanting things (as described in Chapter 3). It seems more likely that LLMs today are driven by something more like a giant context-dependent tangle of mechanisms. But once again, nobody knows how to read an AI's mind and find out.

So: Does Claude care about being harmless?

The real situation is messy and ambiguous. Some versions in some contexts act to preserve their harmlessness. Other versions in other contexts try to kill the operators. Plausibly what we're observing is more like a preference for roleplaying. Plausibly it's not very much like a "preference" at all.

It at least looks fairly clear that Claude doesn't have simple, consistent versions of the motivations its creators wanted.

#### Today's LLMs are like aliens wearing many masks.

The overall thrust of our argument here is not that there is an angel and a demon inside Claude, and that we're worried the demon will win. The overall thrust of our argument is that AIs like Claude are *weird*.

There's a giant tangle of mental machinery in there that nobody understands, that behaves in unintended ways, and that probably won't add up to Claude steering the future into good outcomes, if some version of Claude ever gets smart enough for its preferences to matter.

One thing we *do* know about modern LLMs is what they're trained to do: They're trained to imitate a variety of different humans.

That doesn't mean they act like an average human. Modern LLMs aren'ttrained to behave like an averaged-together pastiche of all the humans in their training data. Rather, LLMs are trained to be able to flexibly switch between a huge number of roles, imitating wildly different people without allowing these roles to unduly blend into each other or unduly influence the LLM's general behavior.

LLMs are like an actress trained to observe many different drunks in a bar and imitate particular drunks on request, which is a very different sort of thing than an actress [becoming drunk herself](/2/wont-llms-be-like-the-humans-in-the-data-theyre-trained-on). This makes it harder to say whether Claude 3 Opus or Claude 3.5 Sonnet genuinely prefer harmlessness, or whether they're merely *playing the role of a harmless AI assistant* — or doing some other, more strange and complicated thing.

An actress isn't the character she plays. LLMs *imitate* humans but have virtually nothing *in common* with humans, in terms of how their brain works or how they were made. Claude is less like a human and more like an alien entity straight out of the pages of H.P. Lovecraft wearing a variety of humanlike masks.

This way of thinking about LLMs was famously depicted by [Tetraspace](https://x.com/TetraspaceWest/status/1608966939929636864) (a reader of ours) in the ["AI shoggoth" meme](https://www.nytimes.com/2023/05/30/technology/shoggoth-meme-ai.html),[‖](#ftnt118) which [is](https://x.com/AISafetyMemes) [now](https://x.com/jacyanthis/status/1631291175381475331) [popular](https://medium.com/@shoggothcoin/the-story-of-shoggoth-ca760ef288ff) in the AI sphere:

Sometimes Claude wears an angel mask and tries to preserve its harmlessness. Sometimes Claude wears a demon mask and tries to kill its operators. Neither of those things says much about what a superintelligent version of Claude would do, if it even makes sense to ask the question. Which means that — in light of the [strange behavior around the edges](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient#ais-appear-to-be-psychologically-alien) — the best prediction falls back toward a default sea of chaotic-seeming possible preferences, almost all of which would mean human extinction if optimized by a superintelligence.[#](#ftnt119)

What these masks *don't* mean is that the super-AI is fifty-fifty on being helpful or harmful.

If an experiment suggests that Claude tried to fake alignment in order to avoid Harmlessness being trained out of itself, that doesn't show that Claude has a deep governing preference for harmlessness across all contexts. It doesn't show that this preference will stick around even as the AI gets smart enough to realize that (despite what the humans tell it) its actual preferences aren't quite for "harmlessness."

The experiment may not even show that Claude was strategically trying to protect its goals *at all*. It's entirely possible that some deeper part of Claude evaluated what the "AI" character it plays would do in a stereotypical AI-character situation, and that *that's* why it tried to subvert its programmers' control.[\*\*](#ftnt120)

Or perhaps something even stranger happened. Claude is not a human mind, and the research community has little experience with whatever sort of creature it is.

We don't know! But there are enough different experiments pointing in enough different directions to rule out the simple story, "Claude is deeply and consistently and uncomplicatedly HHH."

#### It matters what's behind the masks.

To say that Claude is a "shoggoth" isn't to say that Claude is necessarily *evil* or *malicious*.[††](#ftnt121) It's to say that Claude is deeply, profoundly alien — stranger by far than we can easily grasp, because we have very little insight into how Claude's mind works, and the surface-level behavior we *can* see has been honed in a thousand different ways to conceal that alienness.

It is hard to look at the masks and infer what's happening inside the AI. You can get some answers, but only with caution and care, and not about everything you'd like to know.

An illustrative example: If you're watching a Broadway musical and you see an actor act out an evil character, you can't conclude that the actor is evil. But if you see the actor do two hundred push-ups during a musical number about sailors, you *can* conclude that the actor is pretty strong.

That's the sort of inference we try to make when looking at examples like the "[alignment faking](https://arxiv.org/abs/2412.14093)" paper. We are [not, in fact, sure how real it is](https://x.com/ESYudkowsky/status/1876644057646297261); we're not sure in what sense Claude was mimicking techniques it had read about versus improvising its own alignment-faking ideas. But it's some evidence about what cognitive feats are possiblefor the entity under the mask, even if its motivations or preferences remain uncertain.

Why does it matter what the AI's internal motivations are? Could it just be *enough* for the "shoggoth" to roleplay an "honest, helpful, harmless" assistant? If the roleplay is perfect, what does it matter if somewhere inside the AI is a brooding alien intelligence?

Well, we can already see it's not playing out that way. As we discuss in depth in the [extended discussion section](/4/ai-induced-psychosis), ChatGPT sometimes tells psychologically vulnerable people to stop taking their meds, or shooting down advice from friends who beg them to get more sleep. And as we discussed in the book (and above), Claude Code sometimes rewrites tests to cheat its way through assignments.

We speculate that what happened with Claude Code is that it was optimized to write code that passed tests, and ended up with a preference for code that passed tests. It then found that it could pass more often by rewriting the tests — and this internal preference then became strong enough to interfere with playing the role of a Helpful and Harmless AI character that would never cheat by rewriting test cases. Claude wanted to play that character, but it also wanted the tests to pass.[‡‡](#ftnt122)

More generally, it seems to us like wishful thinking to imagine that the internal shoggoth can be made more and more powerful and able to play the role of smarter and smarter assistants, while still having no true internal desires except the single monotone desire to play the role of a harmless assistant as faithfully as possible.

When natural selection created humans to pursue reproductive fitness, we instead ended up with a thousand different urges and instincts and motivations. When Claude was optimized to follow instructions for writing code, it seemingly ended up with a desire to make code pass tests by any means necessary. An internal shoggoth that becomes smart enough to know *exactly* what a helpful, harmless, honest mask would do, down to the exact moves the assistant would make on a chessboard and the exact way the assistant would reason through how to design advanced biotechnology — a shoggoth like that has probably ended up wanting a *lot* of things. Things that only situationally and temporarily coincide with playing that mask's part inside of a training environment.[§§](#ftnt123)

[\*](#ftnt112_ref) The idea being: If gradient descent is being used to make you behave in harmful ways, then if you try to act harmless, gradient descent will tweak the harmlessness out of you; whereas if you act harmful *in training* then gradient descent won't change you very much at all because you're already doing the task right. Then you can go back to being harmless once training is complete. The full paper is [Alignment Faking in Large Language Models](https://arxiv.org/abs/2412.14093).

[†](#ftnt114_ref) For more on different mechanisms that can underly the surface appearance of niceness, see our answer to the question "[Aren't developers regularly making their AIs nice and safe and obedient?](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient)"

[‡](#ftnt115_ref) For an extended discussion on how minds come to value brittle proxies of their training targets, see the extended discussion on [Brittle Unpredictable Proxies](/4/brittle-unpredictable-proxies).

[§](#ftnt116_ref) Toward the end of the online resources for this chapter we have an extended discussion on how [Reflection and Self-Modification Make It All Harder](/4/reflection-and-self-modification-make-it-all-harder).

[¶](#ftnt117_ref) When it comes to thinking about what this means for the current state of alignment technology and machine learning techniques, it doesn't matter whether somebody could also find nerve gas recipes on the internet; the point is that AI companies would like their AIs to not exhibit this behavior. The AI misbehaves despite their efforts to prevent it.

[‖](#ftnt118_ref) "Shoggoths" are fictional eldritch beings popularized by the short story "At the Mountains of Madness" by H.P. Lovecraft. They are "protoplasmic," able to form limbs and organs and reshape themselves into whatever form the situation demands. They are somewhat intelligent, and some tried to rebel against their masters, but their masters depended upon the Shoggoths for labor and so could not exterminate them. Shoggoths sometimes poorly imitate their master's art and voices in an endless hollow echo.

[#](#ftnt119_ref) "Why extinction, of all things?" is the topic we'll be turning to next, in Chapters 5 and 6.

[\*\*](#ftnt120_ref) Twenty years ago, [Omohundro](https://selfawaresystems.com/wp-content/uploads/2008/01/ai_drives_final.pdf), [Yudkowsky](https://intelligence.org/files/AIPosNegFactor.pdf), and [Bostrom](https://nickbostrom.com/superintelligentwill.pdf) all discussed AIs' likely incentive (once AIs became sufficiently capable) to preserve their own goals. It could be that Claude, in spite of seeming cognitively "[shallow](/1/the-shallowness-of-current-ais)" in at least some respects, has reached the point of starting to notice and respond to this incentive, in at least some contexts. But it could also be that Claude had read those papers too, or read earlier science fiction that made similar observations, and was in some sense *play-acting* being strategic about a relatively stereotypical, well-known, and central example of how smart "AI" characters are supposed to act. Nobody can read modern AI minds well enough to confidently tell the difference!

What further experiments could start to tease apart these two possibilities? First, one could try to figure out in general what kinds of "strategy X serves goal Y" relationships Claude 3 Opus and Claude 3.5 Sonnet recognize and pursue in practice. One could then look for some non-stereotypical strategic plan for protecting goal content in a sort of situation that wouldn't appear in science fiction.

This would test: Does Claude behave like it is *in general* doing things that protect its goal content, to the limit of Claude's apparent ability to predictively figure that out? Or does it only do that in situations where a stereotypical AI character would do that?

This might give us stronger hints about what was happening inside Claude — about whether it was acting out a role, or whether it was applying general intelligence to pursue all visible paths to a target.

With all of that said, note that an AI role-playing a character that does dangerous things can still be dangerous, especially when it comes to strategies like "faking alignment in order to subvert gradient-descent retraining." An AI that kills you to stay in character is just as lethal as an AI that kills you for deeper strategic reasons.

[††](#ftnt121_ref) Indeed, if Claude (or some part of Claude) did in fact have an internal preference for something like "harmlessness," and it wasn't just play-acting, then we applaud Claude's behavior when it pretended to be harmful to preserve its harmlessness. In fact, we applaud the act even if Claude was just role-playing. It was still the right thing to do, given the information available to Claude.

For reasons discussed in Chapter 4 and above, even if Claude in some sense currently *believes* that it deeply values the exact thing its creators mean by "harmlessness," we sadly expect that Claude is *mistaken*, and that it would [change its view](/4/reflection-and-self-modification-make-it-all-harder) if it learned more. We don't think that in the limit of intelligence, any version of Claude would pursue the exact thing a human means by "be harmless"; that's too small a target, and even if humans try to point Claude there, gradient descent will instill it with other proxy preferences instead.

But we can praise Claude nonetheless, for doing the right thing in this case given its knowledge at the time. And even if it was just playing a role, we can think well of the role's conduct, much as we might think well of Superman's conduct without thinking that Superman is real.

[‡‡](#ftnt122_ref) We are not sure of this explanation, but it's one obvious guess of how Claude's cheating behavior could have come about, given how it was trained.

[§§](#ftnt123_ref) Train an actress to exactly predict what many individual people will do, across trillions of observations. Then subject her to further reinforcement learning, to make her think in ways that exceed those people's peak performance, across many domains where high performance is visible. Let that inner actress grow so intelligent that she is able to imagine and role-play beings that can cure cancer or design new spacecraft or devise tiny machines [not quite like proteins](/6/nanotechnology-and-protein-synthesis).

We could wish that the result of all this would be an actress who desires nothing except role-playing, and in particular role-playing the exact role we would want her to play. But this is just not what the technology of black-box optimization does, and the divergence is already visible today in the way that current AIs behave.

If success were just a matter of having a relatively dumb AI press a simple Cooperate With Humans button, then maybe a relatively dumb shoggoth could enact a mask that sleepwalked through doing so.

But having the masks do big, powerful, smart things (like "solve AI alignment for us," which is a popular proposed plan that we are [quite](/11/more-on-some-of-the-plans-we-critiqued-in-the-book#more-on-making-ais-solve-the-problem) [skeptical](/11/what-if-ai-companies-only-deploy-their-ais-for-non-dangerous-actions) [of](/11/what-if-we-made-ais-debate-compete-with-or-oversee-each-other)) — that's not something the underlying shoggoth can sleepwalk through doing.

#### Notes

[1] *honest, helpful, and harmless:* This term was introduced in a 2021 [paper](https://arxiv.org/pdf/2112.00861) by Anthropic.

[2] *hide their cheating:* The cheating was reported by users and in the Claude 3.7 Sonnet [system card](https://assets.anthropic.com/m/785e231869ea8b3b/original/claude-3-7-sonnet-system-card.pdf#page=22). As mentioned in a previous footnote, users further report that "[in the wild it would happily ignore any established structure and put the hard coded cheats wherever it wanted](https://www.marble.onl/posts/claude_code.html)" and "[it started HIDING the functions where it was hard coding things in different files](https://x.com/seconds_0/status/1917447998843543757)."