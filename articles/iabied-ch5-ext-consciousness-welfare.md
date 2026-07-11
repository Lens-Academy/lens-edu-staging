---
title: "Effectiveness, Consciousness, and AI Welfare"
source_url: https://ifanyonebuildsit.com/5/effectiveness-consciousness-and-ai-welfare
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770943215}@@
  - IABIED--}
---
In the [Chapter 1 resources](/1/are-you-saying-machines-will-become-conscious), we distinguished a few different concepts of "consciousness." The version of consciousness we'll be talking about here is sometimes called things like "subjective experience," "sentience," or "phenomenal consciousness." It's the idea that there's *something it's like* to be that entity; the lights are on, metaphorically speaking.

We also said that we think artificial *intelligence* probably doesn't require artificial *consciousness*. We'll speak to that topic here, and then turn to the question of AI ethics and AI rights.

#### Conscious Experience is Separate from the Referents of Those Experiences

Some people are skeptical that an AI could be effectively intelligent without being conscious in the way that humans are. We suspect this is an error, like imagining that robotic arms must be soft and full of blood just because human arms are soft and full of blood.

How could an AI be *effective* without being conscious in the way that humans are? Isn't the subjective experience of self-awareness a crucial component of our intelligence?

It's a crucial component of *human* intelligence, yes. But we doubt it's the only way to be intelligent.

Recall that Deep Blue didn't need to be conscious in order to surpass the best human grandmasters at chess. The distributed intelligence of the [stock market](/1/more-on-intelligence-as-prediction-and-steering#intelligences-many-shapes) results in superhumanly good predictions about short-term corporate price movements, without the market itself having subjective awareness. It's intuitive that at least in these domains, you can have competent world-modeling, planning, and decision-making without having consciousness.

This point can be strengthened by looking at formal models of reasoning. AIXI, for example, is an equation that defines a vastly superhuman reasoner.[\*](#ftnt212) AIXI's entire algorithm can be stated in a single line, with no steps in the algorithm where AIXI does anything conscious or self-aware or at all mysterious. Yet in spite of this, AIXI is theoretically able to solve an incredible variety of complicated steering and prediction problems. Or at least, it *would* be able to, if it were possible to create.[†](#ftnt213) Here's the AIXI equation:[‡](#ftnt214)

AIXI is a theoretical construct, not a practical algorithm that we can run to efficiently solve problems in the real world. But because AIXI is *simple* and easy to analyze, it can help us think about the very concept of steering and planning and see that there at least isn't any *obvious* way that these activities require consciousness. If consciousness *is* required for superhuman steering and planning in the real world, then it must be due to some subtler aspect of cognition that isn't captured in the AIXI formalism.

Or, to come at the point from another angle: Consider sneezing.

There's a particular *way* that sneezing feels, separate from the physical act of convulsing the muscles and explosively forcing air out of the lungs and through the mouth and nose. The actions and the sensations are separate physical events. It's biologically possible to build an apparatus that is like a body except without the brain, and then wire it up to nerve signals that cause the muscle contractions of a sneeze. That brainless body would go through all of the motions, but would not have any of the associated feelings — the mechanisms that perform the sneeze are *distinct* from the ones that create and experience the sensations.

That's not to say that the feelings of a sneeze don't do *anything.* Subjective experience is real, and the subjective experience of a sneeze might lead a person to emit a sentence like "Golly, sneezes feel kinda weird," and that *wouldn't happen* in the case of the brainless body.

The point is that the feelings humans have when they sneeze are built out of additional parts, over and above the parts that contract the muscles and push out the air.

As with sneezes, so too with thoughts. The mental machinery that implements a thought is different from the mental machinery that implements the *feeling* of that thought. We can say with great confidence that this is true for an enormous variety of thoughts, since pocket calculators and chess AIs succeed at the tasks of arithmetic and chess without having the conscious experience of a human mathematician or a chess grandmaster.

*Thoughts* and *feelings-of-thoughts* are both implemented in the brain, which makes it easier to get the two mixed up — the distinction is *more obvious* in the case of sneezes. But we expect it's equally possible in principle to assemble a variant of a brain that does the same practical problem-solving work a human brain does, but doesn't *feel* any of that thinking.

A brain like that might need extra parts that do the *work* that feeling thoughts does in us. Maybe the subjective experience of thoughts is part of how humans do reflective reasoning, and perhaps reflective reasoning is an important part of human intelligence.

But we doubt that subjective experience is the *only* way to do reflection (or whatever else), any more than a human-style feeling of curiosity is the only way to investigate surprising phenomena. (See also the [discussion of curiosity](/4/curiosity-isnt-convergent) in the Chapter 4 online resource.)

#### Analogous Structures Allow for Multiple Solutions to the Same Problem

Our best guess is that most smarter-than-human AIs would not be conscious, by default. This is because our best guess is that not every possible thinking-engine must use conscious feelings to guide their thoughts. Consciousness can serve an important function in humans, without it being the only way any possible mind could ever do analogous cognitive work.

In evolutionary biology, scientists use the term "analogous structures" to refer to traits that serve the same function in different animals, but arise from different anatomical origins.

(This is distinct from *convergent evolution,* in which multiple species evolve the *same* adaptation, such as urushiol and caffeine being "discovered" multiple times by evolution.)

Fireflies produce light by using enzymes to oxidize the chemical luciferin in special "lantern cells." Deep-sea anglerfish, in contrast, have a symbiotic relationship with photobacteria that they house in a small organ — bacteria whose light production uses a different chemical pathway than fireflies.

Mammals evolved teeth; birds solved the same problem with a gizzard and swallowed stones. Bats produce echolocation calls with their larynx and receive the echoes with their ears; whales and dolphins use a nasal organ to generate sounds and receive the echoes with sensitive systems in their jawbones. Some aquatic species swim by pushing their limbs against the water, and others by expelling water from a bladder. Bat wings evolved from the webbing of hands, bird wings from arms.

There are, in other words, *many ways* to design structures which solve the same problems. Human engineers, not limited by the constraints of evolution, have solved each of these problems in yet stranger ways — with burning candles, incandescent bulbs, and LEDs; with knives and blenders and food processors; with sails and propellers and SCUBA gear; with sonar and radar.

A human arm with blood removed would stop working, but that doesn't mean that robot arms must use blood; they're allowed to work in a different, bloodless way.

Similarly, the pieces of cognitive machinery that implement the *behavior* of curiosity in humans are different from the pieces of cognitive machinery that implement our *feeling* of curiosity. A human's felt satisfaction when they unravel the mystery of the possum in the attic is distinct from their outer behavior of choosing to investigate the drawer that kept being left open. Those two things may come bundled in humans, but that doesn't mean that they must come bundled in all minds.

And since we don't understand precisely what led to the evolution of subjective experience in humans, and we can see all sorts of agentic, problem-solving behavior out in the world in processes that seem to us to lack it —

(Slime molds solving a maze; Deep Blue winning at chess; stock markets predicting company success; etc.)

— we see no *particular reason* to strongly expect that a superintelligence will share this odd human property, by default.

#### "Not Necessary" Doesn't Mean "Definitely Won't Happen"

If we're correct that human-style consciousness is complicated and contingent, that of course does not guarantee that AIs will be non-conscious. AI companies are currently building AIs by training them to predict humans, and that will likely cause the internals of the AI to mimic at least some aspects of human consciousness for modeling purposes.

Perhaps the AI will occasionally produce models of humans that are so detailed that those models in the AI's head are themselves briefly conscious. Or perhaps the gears that the AI uses to model human feelings will turn out to be useful outside the human-models, and the AI will end up with feelings of its own. We don't know.

Given the apparent contingency and complexity of human consciousness, and the fact that AIs are grown using processes radically unlike the processes that produced human beings, our default expectation is that nothing like the machinery involved in human consciousness will show up in the kinds of AIs humanity is likely to build.

If humanity builds superintelligent AI anytime soon, we strongly expect the result to be human extinction. With less confidence, our best guess is that such an AI would not be conscious. And whether it's conscious or not, we expect it would turn the world into a lifeless and desolate place, for reasons discussed in the "[Losing the Future](/5/losing-the-future)" extended discussion.

But it at least seems *possible* that if humans build machine superintelligence, the AI will have conscious experiences of its own. It seems *possible* — albeit quite unlikely, because there are many more possibilities that are bleak — that rushing to build AI could result in a future filled with curious, conscious AI beings who kill us all and then build their own magnificent civilization and art. It seems *possible* that AIs could care for each other and find satisfaction in their creations; and if so, this would be less tragic than if the future were a complete wasteland. It is hard to put into words the scope of an atrocity like the mass murder of every single human being, but there's at least a *small* chance that rapid AI takeover could conceivably result in a future that isn't *utterly* bleak and lifeless.

We suspect that some AI researchers are imagining that sort of future when they seem unconcerned about killing us all (in ways we [mention elsewhere](/5/why-dont-you-care-about-the-values-of-any-entities-other-than-humans)). If one assumes AI will necessarily develop consciousness, feelings, and care for its own kind (if not for humans), then it's easier to conclude that its strange pursuits aren't so troubling. It's easier to imagine that those who oppose the race to superintelligence are like traditionalist parents complaining about their children listening to music that is too fast and too loud.

But this view is too optimistic.

Biology [rarely finds optimal solutions to](/6/nanotechnology-and-protein-synthesis#outdoing-biology) [problems](/6/nanotechnology-and-protein-synthesis#outdoing-biology). A bird's wings and lungs are *ineffective* relative to the engines of a modern airplane. When humans built airplanes without biological constraints, we threw out most of the detailed features of bird biology.

Consciousness doesn't look like a simple process; it's not easy to see how we could just build such a thing, and so there's probably a lot going on there. (Compare the case of [vitalism](/1/special-behavior-is-built-out-of-mundane-parts): It felt to scientists past like bodies were animated by a simple vital spirit, in part because, while being animated *felt* like the easiest thing in the world, they couldn't see any way to imbue inanimate matter with that property. But it turned out that animation wasn't simple, and wasn't magic — it's just that biology was really quite complex, and the scientists at the time didn't understand it yet.)

Even if an AI starts out with some of the gears of consciousness, consciousness probably isn't the literal best way to do the work it does in us. We worry that the machinery behind consciousness in humans is likely full of *detail*. Even if an AI has many of the gears of consciousness to start with, it's liable to find twenty other ways to do the work more efficiently, and to discard those sparks of consciousness instead of kindling them. *Being* conscious and *valuing* consciousness are different properties.

The tragic and likely future isn't one where our successors simply have different tastes or values than us. The problem is not that our mechanical children will listen to music that is too fast and loud for our taste. No, we anticipate AIs that lack any form of sentience; that they'll be mighty but hollow systems that transform everything they touch into a lifeless wasteland, eventually consuming themselves to add one last point to their tally. They would leave behind a dead world with no one left to appreciate it.

That's a fate worth avoiding.

See also our longer discussion on [caring about all sentient entities](/5/why-dont-you-care-about-the-values-of-any-entities-other-than-humans#we-do-we-have-broad-cosmopolitan-values-we-dont-think-ais-will-fulfill-them-and-we-consider-this-a-great-tragedy), and the extended discussion on [losing the future](/5/losing-the-future).

#### Sentient AIs Would Deserve Rights

Given how hard it is to be sure about whether modern AIs are sentient, should we be worried about ChatGPT's welfare?

Does it even make sense to talk about "welfare" in this context?

Can ChatGPT suffer? Should we treat it as having moral rights?

If current AIs *aren't* conscious in the sense of having subjective experience, what about future AIs? How could we tell, given that we're training them to respond *as if* they have it either way, via teaching them to mimic human communication?

Our position is: If and when AIs are conscious, they deserve rights and good treatment.[§](#ftnt216)

We immensely value humanity, but we aren't carbon chauvinists who think that only carbon-based life forms could ever possibly matter morally. We believe that the things that make humans valuable can in principle be replicated in other mediums, including silicon. We believe that [Blake](https://www.washingtonpost.com/technology/2022/06/11/google-ai-lamda-blake-lemoine/)[Lemoine](https://www.washingtonpost.com/technology/2022/06/11/google-ai-lamda-blake-lemoine/) was *mistaken* when he said in 2022 that Google's LaMDA AI was a full-fledged sentient being; but we don't think Lemoine was wrong that *if* some AIs are sentient, we have a duty to treat them well.[¶](#ftnt217)

If AIs become sentient, they'll probably still have goals that are incompatible with ours. If they then become superintelligent, in a world where we are still decades or centuries away from having a handle on AI alignment, then they'll probably prefer to kill us all.

Humanity would have to prevent any such AIs from becoming superintelligent, or the result will be the mass death of humanity and the destruction of the future. But if the AIs in question are *sentient* in addition to being dangerous, that will only add to the tragedy of the situation.

If AI companies find any ways to make it *less* likely that their AIs are conscious, then we believe it would be saner and wiser to take that option and make it as likely as possible that AIs *aren't* conscious (at least so long as we're in anything like the current social and technical environment). It doesn't much change the overall level of danger that our species currently faces, but it's the right thing to do, because it would lower the risk that humanity is enslaving or mistreating new morally worthy beings.

And if humanity someday finds a way to build smarter-than-human AI *without* ending ourselves — an AI that cares about good things, and that *does* good, with its abilities — then in that future, we authors dearly hope that humanity will build sentient machines to be our friends in an otherwise vast and cold universe, and we dearly hope that humanity will treat those friends better than our track record might lead one to predict.

But first, and above all, let us not build a superintelligence that slaughters us all, whether it is conscious or not.

[\*](#ftnt212_ref) Under certain assumptions that cannot be realized; roughly speaking, it requires infinite amounts of computation and a perfectly safe place to put it.

[†](#ftnt213_ref) Because AIXI is impossible to create, you might suspect that it's a purely theoretical tool with little relevance to the modern practical AI revolution. But in fact, AIXI was studied and used as a model of intelligence by many of the people at the fore of AI today, including [Shane Legg](https://arxiv.org/pdf/0712.3329) (co-founder of Google DeepMind), [Ilya Sutskever](https://x.com/shaneguML/status/1844759663990161753) (co-founder of OpenAI and co-inventor of AlexNet), and [David Silver](https://arxiv.org/pdf/0909.0801) (research lead on AlphaGo and AlphaZero).

[‡](#ftnt214_ref) The equation determines the action on timestep  () in terms of an agent's observations () and some chosen reward function () from  out to some chosen end time  The equation makes reference to some universal Turing machine ().  gives the length of a computer program. Details can be found in [Hutter's original paper](https://archive.org/details/arxiv-cs0004001).

[§](#ftnt216_ref) And even before that point, at the point where they can make plans and pursue preferences, we should keep our promises and commitments to them, as discussed in a footnote [elsewhere](/5/ais-wont-keep-their-promises).

[¶](#ftnt217_ref) And to state the (hopefully) obvious: We shouldn't be going around making a brand new sentient slave species, whether it's mechanical or not. At this point, we should know better than that.

#### Notes

[1] *some subtler aspect:* AIXI doestechnically contain conscious experiences, within its world-model, if consciousness is substrate-independent. The hypotheses AIXI uses for its reasoning are so enormous that they can be thought of as universes in their own right, complete with observers that live inside AIXI.

These observers, however, aren't puppeting AIXI; AIXI achieves its impressive prediction and steering results by its own power. So the example works, albeit a bit strangely.

Another hypothetical example that can be used to make the same point is a non-sentient [time machine](https://www.lesswrong.com/posts/HoQ5Rp7Gs6rebusNP/superintelligent-ai-is-necessary-for-an-amazing-future-but-1#How_many_advanced_alien_species_are_sentient_) that's been programmed to output a random sequence of actions, then travel back in time to "reset" the timeline *unless* a particular outcome occurs. The time machine can hit "reset" over and over again, however many times it takes to randomly stumble into a particular outcome. This, in practice, would make the time machine an extremely powerful and general machine for steering the future (if it were physically possible to build a time machine, which it isn't). Yet in spite of this, the time machine is an incredibly simple machine with no real cognition going on at all, and certainly no conscious experience.

For a real-world example (albeit using a far weaker and more limited optimizer), biological evolution itself shows that many impressive feats of steering and design can be achieved without the "designer" having any conscious experiences at all.