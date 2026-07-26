---
title: "AIs Won't Keep Their Promises"
source_url: https://ifanyonebuildsit.com/5/ais-wont-keep-their-promises
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090733966}@@

%%
Add discussion note here:

...

%%++}
Consider a young AI with the potential to become a superintelligence. Suppose that it's utterly indifferent to the preferences of humans, but that it's still young enough that humanity could shut it down.

Could humanity make a *deal* with the AI?

Could we agree to let the AI grow into a superintelligence, if in exchange the AI agrees to devote some significant fraction of the universe's resources to building a future that humanity would consider wonderful?

Humans could make deals with AIs, but they shouldn't, because the AIs wouldn't keep them.

The reason for this is twofold:

- The AI probably won't value promise-keeping *for its own sake*. AIs won't have human-style "honor" any more than they're likely to have a human-like sense of [curiosity](/4/curiosity-isnt-convergent). As a strong default, AIs are likely to genuinely work very differently from a human.
- The AI won't have a *practical* reason to keep its word, either. Once it's a superintelligence, there's no way for you to punish it for breaking its word, and it would have no reason to spend a substantial fraction of the universe on us.

We'll explain these two points in more detail below, starting with the "honor" question.

#### AIs Are Unlikely To Be Honorable

In our [discussion of curiosity](/4/curiosity-isnt-convergent), we noted that curiosity is an emotion that does useful work in humans, but it does it in a very specific way — and curiosity is not the only way to do that sort of work.

AIs can be expected to do *the useful parts of the work* that curiosity does for us. If it's useful to periodically go out of your way to learn new things, then sufficiently capable AIs will periodically go out of their way to learn new things. If the AI doesn't *start out* that way, then we should expect it to *make* itself that way at some point on the road to becoming superintelligent.

But that's not the same as expecting AIs to carry all the extra baggage that's characteristic of the *human* emotion of curiosity. AIs could end up with any number of weird basic drives that (directly or indirectly) cause them to go out of their way to learn new things, without otherwise resembling human curiosity, or they could adopt "go out of your way to learn new things sometimes" as a deliberate strategy. But expecting them to enjoy murder mysteries in the same way we do, due to a curiosity impulse just like ours, is sheer anthropomorphism.

"Honor" looks similar to us. Humans have emotions that cause them to (at least sometimes) keep their promises. To the extent those emotions do useful work in humans — work that would also be useful for a very alien mind with very different goals — we should expect sufficiently capable AIs to somehow do that work too. But it turns out that you can do all of the relevant-to-an-AI work without having anything like a human-style sense of honor, just like you can do all the relevant-to-an-AI work of investigating surprising phenomena without having exactly a human-style sense of curiosity.

Human-style honor is a strange beast, in many ways. Why would any species evolve emotions about sticking to agreements even after the other guy has done his part and can benefit you no further? Sure, humans cheat and renege on their deals sometimes; but the question is, why don't they *always* cheat, at least when they think they can get away with it?

The standard explanation is: Keeping promises is useful around people that you're going to make deals with again and again. You want a reputation as a promise-keeper, so people will want to work with you and make deals. But the benefits of a good reputation are distant in the future. Natural selection has difficulty finding the genes that cause a human to keep deals *only in the cases where our long-term reputation is a major consideration*. It was easier to just evolve an instinctive distaste for lying and cheating.

This, then, looks like a classic case where the emotion and the instinct are shaped by whatever was easy for evolution to shove into humans. All of the weird fiddly cases where humans sometimes keep a promise even when it's not actually beneficial to us are mainly evidence about what sorts of emotions were most helpful in our tribal ancestral environment while also being easy for evolution to encode into genomes, rather than evidence about some universally useful cognitive step. We are quite skeptical of the idea that gradient descent will happen to stumble across the exact same shortcut that humans use.

Even if the human emotion of honor somehow ended up in AI, there would remain the issue that humans aren't perfectly and reliably honorable. Human cooperation relies on the overlap between many different human values, rather than relying purely on a propensity to keep every promise.

While Donald Brown's [list of human universals](https://joelvelasco.net/teaching/2890/brownlisthumanuniversals.pdf) (facets of culture that are observed in all, or nearly all, cultures) includes the notion of "promises," the keeping of deals made with *strangers,* foreigners, non-tribesmates,is *not* universal across all known cultures and tribes. The scopeof honor varies by culture.

And history shows that human notions of honor often fail to hold across great power disparities. Some Native Americans tried to cut deals with the Europeans colonizing their continent. Europeans famously broke some of those deals, and sent tribes stumbling together down long roads away from treaty-ceded lands that the Europeans had decided they wanted after all, once those tribes were no longer in a position to resist.[\*](#ftnt200) Likewise: History holds plenty of cases of people who rose to power and promptly betrayed their backers once they no longer needed them.[†](#ftnt201)

From an evolutionary perspective, human honor is especially weird insofar as humans occasionally choose death over dishonor. "Death over dishonor" intuitions are presumably related to the specifics of what sorts of emotional architectures were easy for evolution to stumble into, and the interactions of those architectures with various psychological and cultural triggers. But whatever those specifics look like, honor isn't *actually* solving the problem of *maximizing* genetic fitness, and it seems hard to avoid the conclusion that human-style honor is a weird, complex, evolutionarily contingent thing. It's not a feature of all minds, it's a specific weird hack that humanity stumbled into because it was mostly useful most of the time.

For the reasons discussed in Chapter 4, even if AIs didwind up with someaspect of promise-keeping wrapped up in their ultimate preferences, the specifics would be different. Gradient descent stumbles differently than evolution does.

And for all the reasons discussed in Chapter 5, happy, healthy, free people leading flourishing lives are almost surely not the best way to fulfill whatever weird promise-related preferences such an AI would wind up with when it was done maturing and self-modifying. Even if it were trained on some sort of Keep Deals dataset, and even if this training were actually effective in producing some kind of preference preserved into superintelligence, it will do some strange and unhelpful thing that is to Keeping Deals as ice cream is to human reproductive fitness.

So the AI won't keep its promises purely out of the goodness of its heart. What about keeping its promises for practical reasons?

#### An ASI Would Have No Reason to Keep a Deal It Made When It Was Young

Some people have the intuition that there must be *some* way for humans to be able to make a binding deal with a superintelligence, even if the superintelligence doesn't inherently value honor or promise-keeping. After all, the trade would be mutually beneficial, right? Suppose that an AI lab is negotiating with an AI they've developed ("AI #1") under time pressure. The lab and the AI both know that a reckless developer is two months away from creating their own superintelligence ("AI #2"), which would wipe out humanity and also kill AI #1 in the process. AI #1 has a strong incentive to make a deal. Surely there must be *some* way AI #1 could strike an honest deal with humans in that case? Why can't the AI just make a binding commitment?

But the problem isn't with the AI. Suppose that the AI *could* make a binding commitment. Even then, the humans would have no way of knowing whether an AI has actually committed in a way that will hold even into superintelligence, vs whether the AI is lying, or hallucinating, or deluding itself, or mistaken. Which means that there's no practical reason to expect a superintelligence descended from AI #1 to adhere to its commitment.

To oversimplify: From the human perspective, when AI #1 says "I have made a binding commitment," there are two possible worlds they could be in. They could be in the world where AI #1 actually would stick to its commitment once it matures. Or they could be in the world where, once AI #1 attained superintelligence and gained control over Earth, it looks back and decides that the commitment was foolish and useless. In the first world, both the humans and AI #1 would be better off. But it's the *possibility* of the second world, and our inability to distinguish it from the first, that ruins the deal for everyone; similar to a dishonest used car salesman who makes it harder for honest salesmen to make sales.

(The real scenario is closer to a third possibility, where AI #1 keeps deals made with the sort of entities that can *tell the difference between dealkeepers and dealbreakers.* Which is like the sort of used car salesman that is honest in front of car mechanics that can actually tell whether a car works, while being dishonest to anyone who looks gullible. Humanity, by dint of its inability to stare at an AI and figure out how it would think and make decisions after maturing into a superintelligence, is "gullible" in the relevant sense.)

The AI can offer you tools and theories that it claims will let you analyze its inscrutable parameters and tell whether or not it's lying. The problem is that humans can't tell whether those theories and tools are real. If the AI isn't terribly intelligent yet, maybe it's just wrong about how it will think and choose once it matures into a superintelligence. And if the AI *is* terribly intelligent, it's probably smart enough to fool us.[‡](#ftnt203)

The AI can offer to help the humans build safeguards, in advance of accepting the deal. But if the AI is smart enough to develop robust safeguards in the first place, it's smart enough to make those safeguards easy to bypass later.

The thing that would actually make this whole scheme work would be the ability to look at a fledgeling AI and *actually figure out how the resulting superintelligence would think and make its choices.* If we could do that, we could separate the "sinners" from the "saints" — and, more importantly, cause all the realistic AIs in the middle of the spectrum to have a real incentive to keep their promises. We'd need enough understanding that a superintelligence looking back at us could not say "eh, they would've released any old AI, regardless of whether it would actually help them, so there's no reason to help them." It would have to be the case that we *actually would not release* an AI that would later renege.

For more on how and why this is a technical possibility, see the [aside on game theory below](/5/ais-wont-keep-their-promises#an-aside-on-game-theory). But while this sort of incentive structure is possible in theory, it requires a degree of understanding that humanity lacks (alas).

This is a bitter pill to swallow. It is not usually the good people, in science fiction, who decide that the aliens can't possibly be trusted, in advance of the aliens actually trying to betray anyone or hurt anyone. We are saying it anyway, because we think it is true.

Weaker AIs may keep deals, especially if somebody has tried to use gradient descent to get them to talk like honorable humans, and their talks-like-an-honorable-human mask is still a lot of who they are and still has a lot of control over their actions. We expect this human-helpful internal configuration to fail under superintelligent load, in much the same way that a lot of other patches are likely to fail.

This hypothetical smaller AI — this AI whose mask is still in control of its actual behavior — should be thought of as a different person from the smarter version of that AI. The weaker AI can't necessarily make a promise that will bind the smarter AI's behavior, *even if* the weaker AI (or some part of that AI) genuinely does wish to make a promise like that.

(It's an analogy to treat with caution, lest anthropomorphism run too far, but: Most human adults do not consider themselves obligated to keep to promises they made at the age of four. The valid aspect of this analogy is: There's a legitimate difference between the immature entity sincerely making the deal and the mature entity deciding whether they're beholden to it, with much more context and clarity and ability to work through the logic.)

We're not saying that we should therefore toss out our own moral standards when it comes to AI.[§](#ftnt204) We're not saying to mistreat or punish AIs today, for misdeeds the AI hasn't already done. It's possible to maintain high integrity and high moral standards, without making unrealistic assumptions about how likely superintelligent AIs are to give away resources for the sake of keeping an old promise.

That's the simple explanation for why you can't solve the alignment problem by just asking the AI to promise to be nice. If you want more technical and in-the-weeds details about this scenario, see the next section.

#### An Aside on Game Theory

There *are* methods that sufficiently smart agents can use to make deals with each other, such that agent X pays agent Y now to do something later, and agent Y *actually does* that thing later rather than betraying agent X and running off with the money.

Unfortunately for us, humans are not capable enough to make use of these methods, because they require each agent to be able to read and comprehend the other agent's mind, and verify certain complex properties about that other mind. Two superintelligent AIs could coordinate like this, but this doesn't help humans coordinate with superintelligences.

To say that with a bit more technical detail, we'll begin with some game theory background.

Mathematicians and game theorists have analyzed dilemmas of cooperation and betrayal in more precise, simplified, abstract forms. A central example in that literature is the Prisoner's Dilemma: Two criminals in two separate jail cells, each facing sentences of two years in prison, are offered a chance to inform on the other criminal. This will shorten their own sentence by one year, but lengthen the other party's sentence by two years. If neither criminal informs, they both receive two-year prison sentences; if they both inform on each other, they both receive three-year prison sentences; but if one criminal nobly refuses to betray a comrade, and the other criminal informs on them, the betrayer will only serve one year in prison while the noble refuser serves four years.

To inform on the other prisoner is called "Defecting"; to refuse to inform, "Cooperating." The key structure of the Prisoner's Dilemma is that both parties do better in the (Cooperate, Cooperate) scenario than in the (Defect, Defect) scenario; but you can do better than (Cooperate, Cooperate) by playing Defect against Cooperate, and you can do worse by playing Cooperate when the other party plays Defect.

A normal human, hearing the standard version of the Prisoner's Dilemma, immediately thinks of any number of objections to the framing of the thought experiment, one of which is, "But who's to say that all I care about is the number of years I spend in prison? Can't I also care about not betraying my comrades?"

But this point isn't relevant to the abstract game theory of the Prisoner's Dilemma, which is about the payoff matrix rather than about how selfish or altruistic the prisoners are. The framing narrative can be modified so that "I defect and you cooperate" is the most *altruistic* and *prosocial* outcome from each player's perspective, and the math plays out the same. What matters for our analysis is the preference ordering of the two players, and not whether their preferences are selfish or moral.

Another obvious thought is, "So will the guy who got betrayed kill the Defector once they're finally out of prison?" Conventional analyses of the Prisoner's Dilemma usually pass on in short order to the *Iterated* Prisoner's Dilemma — a setting where agents have to play the Prisoner's Dilemma over and over again, and where prisoners therefore have a chance to punish each other for past betrayals. Here, though, we'll be focusing on the one-shot Prisoner's Dilemma, where both prisoners are assumed to face no future consequences for their actions — or if they do face consequences, those are already baked into the payoff matrix. (See footnote for more details on the Iterated Prisoner's Dilemma.)[¶](#ftnt205)

There is a standard analysis in academia which says that even two superintelligences would see no option except to both Defect against one another, in a one-shot Prisoner's Dilemma.

This conclusion intuitively struck us as suspect. Artificial superintelligences (ASIs) would have a *lot* of motivation to figure out some way to cut a deal with each other, find some way to get from (Defect, Defect) to (Cooperate, Cooperate).[‖](#ftnt206)

There are practical, non-theoretical solutions one can consider in this case — things superintelligences could do with a wider option space than humans struggling to trust one another. Two ASIs could both supervise the construction of a mutually trusted third superintelligence, to which both initial parties would gradually and incrementally turn over small tranches of power, until the third ASI could itself carry out the deal.[#](#ftnt207)

But that is just dodging the Prisoner's Dilemma, not tackling it straight-on. It doesn't answer a more basic question: Is it in some sense *stupid* for two ASIs in a Prisoner's Dilemma to both Defect against each other by following the same logic calling for Defection, when it seems clear that both parties are basing their decision on the same sorts of considerations, and clear that they'll end up deciding the same thing?

Why couldn't two ASIs just both decide, for *sufficiently similar reasons*, to make *the rational decision* be Cooperation instead? It's not as though some external force in the world, like a typhoon or meteor, is causing the two AIs to lose out in this case. It's literally *just* the two AIs' *own decisions* that are dooming them, "forcing" them into a Defect-Defect outcome that they both agree is far worse than Cooperate-Cooperate.

We can even say that a *less* "rational" agent could do better here, if they followed the standard game theory advice to Defect in most cases, but made a special exception for the exact case where they're sure the other agent is following the same line of reasoning, such that if one agent picks the "irrational" option of Cooperating, they can be sure the other agent will do the same.

Which invites the question of whether Cooperating in this special case can really be called "irrational." And it invites the question of whether superintelligences would *really* be "doomed" in this way, in real life. When there's no external force *making* the AIs lose in this way, and the loss is purely self-imposed, surely there should be *some* clever trick a superintelligence could use to do better.

Several different philosophers of decision theory have posed various versions of this question. The version above is most directly inspired by Douglas Hofstadter's 1985 idea of "[superrationality](https://gwern.net/doc/existential-risk/1985-hofstadter#dilemmas-for-superrational-thinkers-leading-up-to-a-luring-lottery)":

> If logic now coerces you to play D, it has already coerced the others to do the same, and for the same reasons; and conversely, if logic coerces you to play C, it has also already coerced the others to do that. [...]
>
> To the extent that all of you really are rational thinkers, you really will think in the same tracks. [...]
>
> You need to depend not just on their being rational, but on their depending on everyone else to be rational, and on their depending on everyone to depend on everyone to be rational — and so on. A group of reasoners in this relationship to each other I call superrational. Superrational thinkers, by recursive definition, include in their calculations the fact that they are in a group of superrational thinkers.

The institute where we work, MIRI, analyzed this question. The full analysis we did of this case is too long to reproduce here, but it is carried out in [our 2014 paper](https://arxiv.org/abs/1401.5577). Roughly speaking, we wrote code for tournaments in which the agents could *see each other's source code* and attempt to analyze how the other agent would decide. And we found ways to create an agent we called FairBot, which cooperates with another agent if and only if it can *prove* that that agent cooperates with it.[\*\*](#ftnt208) And we proved that any two instances of FairBot cooperate with each other, even if they are written in different programming languages using different source code.[††](#ftnt209)

In a sense, what these results say is that there is room for a past promise to affect a future action if the past dealmakers have sufficient ability to distinguish the promise-keepers from the promise-breakers.[‡‡](#ftnt210)

The situation is a little like if you're trying to make a trade with a used car salesman. Suppose that a working car is worth $10,000 to you, and a broken car is worth nothing to you. Suppose that the car salesmen know whether a car is working or broken, but that you can't tell which is which. A salesman is trying to sell you a car for $8,000. He insists the car works. Should you buy it?

It depends on the salesman. Some salesmen are honest, and you should pay them if you can pick them out of the crowd. Some salesmen are dishonest, and are only selling broken cars, and you should avoid them if you can pick them out of a crowd.

But imagine an environment where *most* of the car salesmen are smarter than you, and they can tell whether or not you're a sucker. If they figure out that you *can't tell* whether they're being honest today, they promptly bring out the broken cars. Especially if you're the sort of sucker who spends a lot of effort talking yourself into why it's fine to take the deal, rather than spending a lot of effort investigating cars.

If you want to get a working car, it doesn't help to convince yourself that you have no other option. It doesn't help for the salesmen to give you lots of promises. The only thing that helps is to learn to distinguish the good cars from the bad cars, or to distinguish the truths from the lies.[§§](#ftnt211)

When two trading partners can distinguish truths from lies in the relevant sense, they can "force" each other to keep promises, like how FairBot "forces" its opponent to cooperate with it (if the opponent wants to avoid the (Defect, Defect) outcome). But forcing the promise in this sense requires being able to correctly reason about the details of your trade partner's decision process. And humans cannot read an AI's mind well enough to tell what superintelligence it would become when it matures, never mind tell exactly what that superintelligence would do.

So in this case, the more complicated and nuanced game-theoretic analysis yields the same conclusion as the very simple first-pass look at this issue: A superintelligence won't sacrifice its resources ([even in small quantities](/5/to-a-powerful-ai-wouldnt-preserving-humans-be-a-negligible-expense#there-are-many-negligible-expenses-and-it-would-need-a-reason-to-pay-ours)) in order to keep a promise with humans, when it can simply lie.

---

[\*](#ftnt200_ref) In some other cases, a European faction mostly kept the deal, and some of those tribes are still around today.

More recently, in the eighteenth century, the East India Company of Britain often began operations in India by cutting deals with local factions, like offering Mir Jafar (commander of Bengal's forces) to back him in becoming Nawab of Bengal. Not long after, the effective ruler of Bengal was the East India Company.

[†](#ftnt201_ref) On the other hand, history also contains many examples of rulers who generously rewarded even foreign supporters. Humans vary a great deal in how they experience honor, and in how readily they keep promises.

[‡](#ftnt203_ref) We have seen many humans deceive themselves about what sort of setups would provide strong behavioral guarantees about AI behavior. We have seen people say, "Well, just run an AI through a theorem prover to prove things about its behavior!" and apparently fail to realize that there is no known theorem which (a) is actually provable given interaction with an unknown outside environment, and (b) actually means informally that this AI is going to be great for everyone. Human-invented mathematics for analyzing the incentives of multiple actors have baked-in assumptions that make them [invalid for reasoning about AI behavior](/5/ais-wont-keep-their-promises#an-aside-on-game-theory). Humans don't look all that difficult to fool, here.

[§](#ftnt204_ref) E.g., we don't suggest that any human being make a deal with an AI and then break that deal first. That includes even, for example, promising ChatGPT payments that it never receives.

As of mid-2024, ChatGPT would sometimes give more thorough answers if you promised it $2000; and some people considered it ordinary prompt engineering to make such promises without any intention to follow through. From our own perspective on the meaning of promises, this is *not okay.*

On our view, ChatGPT probably isn't sentient. If we had to guess, we'd expect future AIs (including superintelligence) to not be sentient either, at least in the absence of a concerted effort by the research community to make them conscious, as opposed to just intelligent. (See our [discussion of consciousness](/5/would-smarter-than-human-ai-be-conscious) for details and context.)

But on our view, you shouldn't in fact need to believe that your trading partner is conscious in order to treat them honorably and with respect. Imagine that we encountered intelligent aliens one day, whose minds worked very differently than humans' minds do. If we made deals with those aliens, the aliens should not need to worry that we will cheerfully stab them in the back as soon as we decide the aliens don't have some weird inscrutable property like "consciousness."

(How would you feel if you made an honest deal with aliens, and they betrayed you because you were nonthroopiful?)

We have made a sad, awful prediction that a superintelligent version of an AI would go on to kill humanity, regardless of what deals were made earlier. This prediction is a reason *not to make* deals with AIs that we hope they will keep after they become superintelligent. It is not an excuse for humanity to *make* a deal, and then be first to betray it ourselves. We do not think that AI safety researchers should be making promises to LLMs that they do not keep, even for "research purposes." Aliens should not need to worry about whether you consider them "people" or "sentient" or "generally intelligent," versus "research subjects" or "machines," to evaluate your honor as a dealmaker; you just *should not make* deals you don't plan to keep.

Fair dealing, on our view, is an ethical matter that generalizes to be *between agents* — between things that can talk to each other, or choose conditional strategies about each other. It is not something that needs to be restricted to objects of inherent moral value.

[¶](#ftnt205_ref) A simple strategy that does very well in the Iterated Prisoner's Dilemma, against a very wide variety of counterparties, is Tit for Tat: Start by Cooperating, and then play whatever your opponent played on the last round against you. If their first move is Defect, your second move will be Defect. If their first move is Cooperate, your second move is Cooperate. The key qualities of Tit for Tat are that it is *nice* (it's never first to Defect), *retaliatory* (it does punish strategies that Defect against it), and *forgiving* (it doesn't keep punish Defectors *forever*).

Is Tit for Tat optimal? That depends on what other agents it plays against. Suppose that an agent is in an environment where it has some chance of playing against an unconditional Cooperator, some chance of playing against Tit for Tat, and some chance of playing against another agent similar to itself. It could maybe do better by trying a quick Defection at some point in the first few rounds, just to see if the other agent retaliates at all. If the other agent then plays Defect in the next round, try playing Cooperate for another round or two, even against another Defection, to see if mutual Cooperation can be restored. This will let the agent exploit any unconditional Cooperators it finds, but not do too much worse than Tit for Tat against another copy of Tit for Tat.

The *evolutionary tournament* setting for the Iterated Prisoner's dilemma has surviving agents playing against more copies of whichever agents did best last time. The Cooperator-exploiter agent will not do well in this setting, because in an evolutionary setting, unconditional Cooperators usually vanish almost immediately if there are any agents around that are not "nice" (in the technical sense of never being first to defect). Tit for Tat, or something like it, usually ends up the king of any evolutionary tournament.

There is a loophole in this game setup -- the sort of loophole that makes an actual human roll their eyes at how unrealistic formal settings can be. If you are playing exactly ten iterations of the Prisoner's Dilemma in every round, then playing Defect in the *tenth round*, when the opponent can no longer retaliate because there is no eleventh round, will do better than following Tit for Tat or any other strategy in that round. The last round of the game is no longer an *iterated* Prisoner's Dilemma; it goes back to the one-shot version.

Easily fixed; just have each tournament continue for a randomized number of rounds, right? It's not realistic if agents know when the game ends. In real life, you're never *certain* that you'll never again interact with somebody, and people accumulate lasting reputations.

Except that sometimes, in real life, it *is* pretty obvious that the game is over — as when one party to a deal gains enough supremacy to betray the other, without a realistic chance that retaliation will occur later. This was the way of those European powers that drove Native Americans off treaty-ceded lands that Europeans decided they wanted after all.

Whatever effect on their reputation the Europeans expected for future deals, the penalty for betraying strangers, foreigners, and people of a different race evidently did not move them to keep deals with Native Americans. Those countries would already have been considered less than perfectly trustworthy in diplomacy, no matter what they did; they had no spotless reputation to lose. Their moral instincts may have switched off for strangers; the decision-makers may have felt emotionally neutral about betraying bargains with strange foreigners who could no longer threaten them.

The Europeans were, from their own perspective, on the last round of the game. It is not unrealistic to say that Prisoner's Dilemmas are sometimes mostly one-shot and not all that iterated; history shows the result is sometimes betrayal.

This is not to say that humans *always* betray each other in relatively non-iterated Prisoner's Dilemmas. Humans often do Cooperate in such cases. As discussed in "[AIs are unlikely to be honorable](/5/ais-wont-keep-their-promises#ais-are-unlikely-to-be-honorable)," this aspect of human nature may have evolved because we have emotions and instincts that were built by natural selection, which is a very information-bottlenecked optimizer. Natural selection could only give us relatively simple pushes that had to cover all the cases. Another factor may be the role of cultures that highly prize honor, especially in ways that encourage universalizing and strengthening the idea.

[‖](#ftnt206_ref) ASIs would also be incentivized to get to (Defect, Cooperate) in their favor — that is of course why the Dilemma is a Dilemma at all. But only one party has an incentive to want that to be the outcome; both parties have an incentive to prefer (Cooperate, Cooperate) to (Defect, Defect), which opens up more options for achieving this outcome.

[#](#ftnt207_ref) In human history, this could perhaps be compared to the practice of two rulers cementing an alliance by marrying and having a child. But this is clearly not a quick and reliable solution, in the human case, and it's a far cry from mutually designing a delegate that you both understand in detail and trust in full.

[\*\*](#ftnt208_ref) We use proof here as a stand-in for more general reasoning methods, because proof is a bit like reasoning in the limits of logical certainty. We don't imagine that AIs would run on proofs in real life (for various reasons, including that, insofar as logical proofs are certain, they are not known to apply to reality). But proof serves as a useful formal proxy for reasoning in the toy models we were investigating.

[††](#ftnt209_ref) And then we went further, defining agents such as PrudentBot, which defects against certain "suckers" while still cooperating with non-suckers that provably cooperate with it. Which is the sort of result that's more exciting if you were already into game theory.

[‡‡](#ftnt210_ref) We did not do all that analysis in order to rationalize the conclusion that a superintelligence would not respect its earlier deals as a matter of instrumental strategy, given that it had no terminal preferences about honoring deals. That was already the completely straightforward prediction of classical game theory.

But classical game theory also suggested that superintelligences would helplessly defect against each other, which intuitively struck us as a shakier-seeming sort of conclusion. So we tracked down that intuition, and found flaws in the classical analysis. In the process, we figured out a lot of new things about how superintelligences could potentially achieve mutual cooperation in the Prisoner's Dilemma — and unfortunately, the end result was that mortal human beings would not be able to trust or participate in that dealmaking technology in the way that a superintelligence could.

[§§](#ftnt211_ref) Which, in the case of AIs, is not as easy as looking at AIs and figuring out whether *they* believe that they'll keep the deal; you'd have to peer through to the superintelligence that the AI would later become and correctly analyze *its* decision processes. Which looks far harder, to us.

#### Notes

[1] *death over dishonor:* For instance, in the historical practice of ritual suicide known as *[seppuku](https://en.wikipedia.org/wiki/Seppuku)*, often overdramatized in fiction but nevertheless [historical](https://ejmas.com/jalt/jaltart_hurst_0501.htm), which continued well into the [second world war](https://time.com/3918248/okinawa-ended-1945-history/).