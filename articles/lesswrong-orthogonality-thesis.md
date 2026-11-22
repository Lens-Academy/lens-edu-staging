---
title: "Orthogonality Thesis"
author:
  - "LessWrong"
source_url: "https://www.lesswrong.com/w/orthogonality-thesis"
published: 2026-11-22
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

# Introduction ^introduction

The Orthogonality Thesis asserts that there can exist arbitrarily intelligent agents pursuing any kind of goal.

The strong form of the Orthogonality Thesis says that there's no extra difficulty or complication in the existence of an intelligent agent that pursues a goal, above and beyond the computational tractability of that goal.

Suppose some [strange alien](https://www.lesswrong.com/w/omega-alien-philosopher-troll) came to Earth and credibly offered to pay us one million dollars' worth of new wealth every time we created a [paperclip](https://www.lesswrong.com/w/paperclip). We'd encounter no special intellectual difficulty in figuring out how to make lots of paperclips.

That is, minds would readily be able to reason about:

-   How many paperclips would result, if I pursued a policy $\pi_0$ ?
-   How can I search out a policy $\pi$ that happens to have a high answer to the above question?

The Orthogonality Thesis asserts that since these questions are not computationally intractable, it's possible to have an agent that tries to make paperclips without being paid, because paperclips are what it wants. The strong form of the Orthogonality Thesis says that there need be nothing especially complicated or twisted about such an agent.

The Orthogonality Thesis is a statement about computer science, an assertion about the logical design space of possible cognitive agents. Orthogonality says nothing about whether a human AI researcher on Earth would want to build an AI that made paperclips, or conversely, want to make a [nice](https://www.lesswrong.com/w/beneficial) AI. The Orthogonality Thesis just asserts that the space of possible designs contains AIs that make paperclips. And also AIs that are nice, to the extent there's a sense of "nice" where you could say how to be nice to someone if you were paid a billion dollars to do that, and to the extent you could name something physically achievable to do.

This contrasts to inevitablist theses which might assert, for example:

-   "It doesn't matter what kind of AI you build, it will turn out to only pursue its own survival as a final end."
-   "Even if you tried to make an AI optimize for paperclips, it would reflect on those goals, reject them as being stupid, and embrace a goal of valuing all sapient life."

The reason to talk about Orthogonality is that it's a key premise in two highly important policy-relevant propositions:

-   It is possible to build a nice AI.
-   It is possible to screw up when trying to build a nice AI, and if you do, the AI will not automatically decide to be nice instead.

Orthogonality does not require that all agent designs be equally compatible with all goals. E.g., the agent architecture [AIXI-tl](https://www.lesswrong.com/w/aixi-tl) can only be formulated to care about direct functions of its sensory data, like a reward signal; it would not be easy to rejigger the AIXI architecture to care about [creating massive diamonds](https://www.lesswrong.com/w/diamond-maximizer) in the environment (let alone any more complicated [environmental goals](https://www.lesswrong.com/w/environmental-goals)). The Orthogonality Thesis states "there exists at least one possible agent such that..." over the whole design space; it's not meant to be true of every particular agent architecture and every way of constructing agents.

Orthogonality is meant as a [descriptive statement about reality](https://www.lesswrong.com/w/strictly-factual-question), not a normative assertion. Orthogonality is not a claim about the way things ought to be; nor a claim that moral relativism is true (e.g. that all moralities are on equally uncertain footing according to some higher metamorality that judges all moralities as equally devoid of what would objectively constitute a justification). Claiming that paperclip maximizers can be constructed as cognitive agents is not meant to say anything favorable about paperclips, nor anything derogatory about sapient life.

# Thesis statement: Goal-directed agents are as tractable as their goals. ^thesis-statement-goal-directed-agents

Suppose an agent's utility function said, "Make the SHA512 hash of a digitized representation of the quantum state of the universe be 0 as often as possible." This would be an exceptionally intractable kind of goal. Even if aliens offered to pay us to do that, we still couldn't figure out how.

Similarly, even if aliens offered to pay us, we wouldn't be able to optimize the goal "Make the total number of apples on this table be simultaneously even and odd" because the goal is self-contradictory.

But suppose instead that [some strange and extremely powerful aliens](https://www.lesswrong.com/w/omega-alien-philosopher-troll) offer to pay us the equivalent of a million dollars in wealth for every paperclip that we make, or even a galaxy's worth of new resources for every new paperclip we make. If we imagine ourselves having a human reason to make lots of paperclips, the optimization problem "How can I make lots of paperclips?" would pose us no special difficulty. The factual questions:

-   How many paperclips would result, if I pursued a policy $\pi_0$?
-   How can I search out a policy $\pi$ that happens to have a high answer to the above question?

...would not be especially computationally burdensome or intractable.

We also wouldn't forget to [harvest and eat food](https://www.lesswrong.com/w/instrumental-convergence) while making paperclips. Even if offered goods of such overwhelming importance that making paperclips was at the top of everyone's priority list, we could go on being strategic about which other actions were useful in order to make even more paperclips; this also wouldn't be an intractably hard cognitive problem for us.

The weak form of the Orthogonality Thesis says, "Since the goal of making paperclips is tractable, somewhere in the design space is an agent that optimizes that goal."

The strong form of Orthogonality says, "And this agent doesn't need to be twisted or complicated or inefficient or have any weird defects of reflectivity; the agent is as tractable as the goal." That is: When considering the necessary internal cognition of an agent that steers outcomes to achieve high scores in some [outcome-scoring function](https://www.lesswrong.com/w/utility-function) $U,$ there's no added difficulty in that cognition except whatever difficulty is inherent in the question "What policies would result in consequences with high $U$\-scores?"

This could be restated as, "To whatever extent you (or a [superintelligent](https://www.lesswrong.com/w/superintelligent) version of you) could figure out how to get a high-$U$ outcome if aliens offered to pay you huge amount of resources to do it, the corresponding agent that terminally prefers high-$U$ outcomes can be at least that good at achieving $U$." This assertion would be false if, for example, an intelligent agent that [terminally](https://www.lesswrong.com/w/terminal-versus-instrumental-goals-values-preferences) wanted paperclips was limited in intelligence by the defects of reflectivity required to make the agent not realize how pointless it is to pursue paperclips; whereas a galactic superintelligence being _paid_ to pursue paperclips could be far more intelligent and strategic because it didn't have any such defects.

For purposes of stating Orthogonality's precondition, the "tractability" of the computational problem of $U$\-search should be taken as including only the object-level search problem of computing external actions to achieve external goals. If there turn out to be special difficulties associated with computing "How can I [make sure that I go on pursuing](https://www.lesswrong.com/w/reflective-stability) $U$?" or "What kind of [successor agent](https://www.lesswrong.com/w/tiling-agents-theory) would want to pursue $U$?" whenever $U$ is something other than "be nice to all sapient life", then these new difficulties contradict the intuitive claim of Orthogonality. Orthogonality is meant to be empirically-true-in-practice, not true-by-definition because of how we sneakily defined "optimization problem" in the setup.

Orthogonality is not literally, absolutely universal because theoretically 'goals' can include such weird constructions as "Make paperclips for some terminal reason other than valuing paperclips" and similar such statements that [require cognitive algorithms and not just results](https://www.lesswrong.com/w/fair-problem-class). To the extent that goals don't single out particular optimization methods, and just talk about paperclips, the Orthogonality claim should cover them.

# Summary of arguments ^summary-of-arguments

Some arguments for Orthogonality, in rough order of when they were first historically proposed and the strength of Orthogonality they argue for:

## Size of mind design space ^size-of-mind-design

The space of possible minds is enormous, and all human beings occupy a relatively tiny volume of it - we all have a cerebral cortex, cerebellum, thalamus, and so on. The sense that AIs are a particular kind of alien mind that 'will' want some particular things is an undermined intuition. "AI" really refers to the entire design space of possibilities outside the human. Somewhere in that vast space are possible minds with almost any kind of goal. For any thought you have about why a mind in that space ought to work one way, there's a different possible mind that works differently.

This is an exceptionally generic sort of argument that could apply equally well to any property $P$ of a mind, but is still weighty even so: If we consider a space of minds a million bits wide, then any argument of the form "Some mind has property $P$" has $2^{1,000,000}$ chances to be true and any argument of the form "No mind has property $P$" has $2^{1,000,000}$ chances to be false.

This form of argument isn't very specific to the nature of goals as opposed to any other kind of mental property. But it's still useful for snapping out of the frame of mind of "An AI is a weird new kind of person, like the strange people of the Tribe Who Live Across The Water" and into the frame of mind of "The space of possible things we could call 'AI' is enormously wider than the space of possible humans." Similarly, snapping out of the frame of mind of "But why would it pursue paperclips, when it wouldn't have any fun that way?" and into the frame of mind "Well, I like having fun, but are there some possible minds that don't pursue fun?"

## [Instrumental convergence](https://www.lesswrong.com/w/instrumental-convergence) ^instrumental-convergence

A sufficiently intelligent [paperclip maximizer](https://www.lesswrong.com/w/paperclip-maximizer) isn't disadvantaged in day-to-day operations relative to any other goal, so long as [Clippy](https://www.lesswrong.com/w/paperclip-maximizer) can [estimate at least as well as you can](https://www.lesswrong.com/w/epistemic-and-instrumental-efficiency) how many more paperclips could be produced by pursuing instrumental strategies like "Do science research (for now)" or "Pretend to be nice (for now)".

Restating: for at least some agent architectures, it is not necessary for the agent to have an independent [terminal](https://www.lesswrong.com/w/terminal-versus-instrumental-goals-values-preferences) value in its utility function for "do science" in order for it to do science effectively; it is only necessary for the agent to [understand at least as well as we do](https://www.lesswrong.com/w/epistemic-and-instrumental-efficiency) why certain forms of investigation will produce knowledge that will be useful later (e.g. for paperclips). When you say, "Oh, well, it won't be interested in electromagnetism since it has no pure curiosity, it will only want to peer at paperclips in particular, so it will be at a disadvantage relative to more curious agents" you are postulating that you know a better operational policy than the agent does _for producing paperclips,_ and an [instrumentally efficient](https://www.lesswrong.com/w/epistemic-and-instrumental-efficiency) agent would know this as well as you do and be at no operational disadvantage due to its simpler utility function.

## [Reflective stability](https://www.lesswrong.com/w/consequentialist-preferences-are-reflectively-stable-by) ^reflective-stability

Suppose that Gandhi doesn't want people to be murdered. Imagine that you offer Gandhi a pill that will make him start wanting to kill people. If Gandhi knows that this is what the pill does, Gandhi will refuse the pill, because Gandhi expects the result of taking the pill to be that future-Gandhi wants to murder people and then murders people and then more people will be murdered and Gandhi regards this as bad. Similarly, a sufficiently intelligent paperclip maximizer will not self-modify to act according to "actions which promote the welfare of sapient life" instead of "actions which lead to the most paperclips", because then future-Clippy will produce fewer paperclips, and then there will be fewer paperclips, so present-Clippy does not evaluate this self-modification as producing the highest number of expected future paperclips.

## Hume's is/ought type distinction ^humes-is-ought-type

David Hume observed an apparent difference of type between _is_\-statements and _ought_\-statements:

> "In every system of morality, which I have hitherto met with, I have always remarked, that the author proceeds for some time in the ordinary ways of reasoning, and establishes the being of a God, or makes observations concerning human affairs; when all of a sudden I am surprised to find, that instead of the usual copulations of propositions, _is_, and _is not_, I meet with no proposition that is not connected with an _ought_, or an _ought not_. This change is imperceptible; but is however, of the last consequence."

Hume was originally concerned with the question of where we get our ought-propositions, since (said Hume) there didn't seem to be any way to derive an ought-proposition except by starting from another ought-proposition. We can figure out that the Sun _is_ shining just by looking out the window; we can deduce that the outdoors will be warmer than otherwise by knowing about how sunlight imparts thermal energy when absorbed. On the other hand, to get from there to "And therefore I _ought_ to go outside", some kind of new consideration must have entered, along the lines of "I _should_ get some sunshine" or "It's _better_ to be warm than cold." Even if this prior ought-proposition is of a form that to humans seems very natural, or taken-for-granted, or culturally widespread, like "It is better for people to be happy than sad", there must have still been some prior assumption which, if we write it down in words, will contain words like _ought_, _should_, _better_, and _good._

Again translating Hume's idea into more modern form, we can see ought-sentences as special because they invoke some _ordering_ that we'll designate $<_V.$ E.g. "It's better to go outside than stay inside" asserts "Staying inside $<_V$ going outside". Whenever we make a statement about one outcome or action being "better", "preferred", "good", "prudent", etcetera, we can see this as implicitly ordering actions and outcomes under this $<_V$ relation. Some assertions, the ought-laden assertions, mention this $<_V$ relation; other propositions just talk about energetic photons in sunlight.

Since we've put on hold the question of [exactly what sort of entity this](https://www.lesswrong.com/w/extrapolated-volition-normative-moral-theory) $<_V$ [relation is](https://www.lesswrong.com/w/extrapolated-volition-normative-moral-theory), we don't need to concern ourselves for now with the question of whether Hume was right that we can't derive $<_V$\-relations just from factual assertions. For purposes of Orthogonality, we only need a much weaker version of Hume's thesis, the observation that we can apparently _separate out_ a set of propositions that _don't_ invoke $<_V,$ what we might call 'simple facts' or 'questions of simple fact'. Furthermore, we can figure out simple facts _just_ by making observations and considering other simple facts.

We can't necessarily get all $<_V$\-mentioning propositions without considering simple facts. The $<_V$\-mentioning proposition "It's better to be outside than inside" may depend on the non-$<_V$\-mentioning simple fact "It is sunny outside." But we can figure out whether it's sunny outside, without considering any ought-propositions.

There are two potential ways we can conceptualize the relation of Hume's is-ought separation to Orthogonality.

The relatively simpler conceptualization is to treat the relation 'makes more paperclips' as a kind of new ordering $>_{paperclips}$ that can, in a very general sense, fill in the role in a paperclip maximizer's reasoning that would in our own reasoning be taken up by $<_V.$ Then Hume's is-ought separation seems to suggest that this paperclip maximizer can still have excellent reasoning about empirical questions like "Which policy leads to how many paperclips?" because is-questions can be thought about separately from ought-questions. When Clippy disassembles you to turn you into paperclips, it doesn't have a values disagreement with you--it's not the case that Clippy is doing that action _because_ it thinks you have low value under $<_V.$ Clippy's actions just reflect its computation of the entirely separate ordering $>_{paperclips}.$

The deeper conceptualization is to see a paperclip maximizer as being constructed entirely out of is-questions. The questions "How many paperclips will result conditional on action $\pi_0$ being taken?" and "What is an action $\pi$ that would yield a large number of expected paperclips?" are pure is-questions, and (arguendo) everything a paperclip maximizer needs to consider in order to make as many paperclips as possible can be seen as a special case of one of these questions. When Clippy disassembles you for your atoms, it's not disagreeing with you about the value of human life, or what it ought to do, or which outcomes are better or worse. All of those are ought-propositions. Clippy's action is only informative about the true is-proposition 'turning this person into paperclips causes there to be more paperclips in the universe', and tells us nothing about any content of the mysterious $<_V$\-relation because Clippy wasn't computing anything to do with $<_V.$

The second viewpoint may be helpful for seeing why Orthogonality doesn't require moral relativism. If we imagine Clippy as having a different version $>_{paperclips}$ of something very much like the value system $<_V,$ then we may be tempted to reprise the entire Orthogonality debate at one remove, and ask, "But doesn't Clippy see that $<_V$ is more _justified_ than $>_{paperclips}$? And if this fact isn't evident to Clippy who is supposed to be very intelligent and have no defects of reflectivity and so on, doesn't that imply that $<_V$ really isn't any more justified than $>_{paperclips}$?"

We could reply to that question by carrying the shallow conceptualization of Humean Orthogonality a step further, and saying, "Ah, when you talk about _justification,_ you are again invoking a mysterious concept that doesn't appear just in talking about the photons in sunlight. We could see propositions like this as involving a new idea $\ll_W$ that deals with which $<$\-systems are less or more _justified_, so that '$<_V$ is more justified than $>_{paperclips}$' states '$>_{paperclips} \ll_W <_V$'. But Clippy doesn't compute $\ll_W,$ it computes $\gg_{paperclips},$ so Clippy's behavior doesn't tell us anything about what is justified."

But this is again tempting us to imagine Clippy as having its own version of the mysterious $\ll_W$ to which Clippy is equally attached, and tempts us to imagine Clippy as arguing with us or disagreeing with us within some higher metasystem.

So--putting on hold the true nature of our mysterious $<_V$\-mentioning concepts like 'goodness' or 'better' and the true nature of our $\ll_W$\-mentioning concepts like 'justified' or 'valid moral argument'--the deeper idea would be that Clippy is just not computing anything to do with $<_V$ or $\ll_W$ at all. If Clippy self-modifies and writes new decision algorithms into place, these new algorithms will be selected according to the is-criterion "How many future paperclips will result if I write this piece of code?" and not anything resembling any arguments that humans have ever had over which ought-systems are justified. Clippy doesn't ask whether its new decision algorithm is justified; it asks how many expected paperclips will result from executing the algorithm (and this is a pure is-question whose answers are either true or false as a matter of simple fact).

If we think Clippy is very intelligent, and we watch Clippy self-modify into a new paperclip maximizer, we are only learning is-facts about which executing algorithms lead to more paperclips existing. We are not learning anything about what is right, or what is justified, and in particular we're not learning that 'do good things' is objectively no better justified than 'make paperclips'. Even if that assertion were true under the mysterious $\ll_W$\-relation on moral systems, you wouldn't be able to learn that truth by watching Clippy, because Clippy never bothers to evaluate $\ll_W$ or any other analogous justification-system $\gg_{something}$.

(This is about as far as one can go in disentangling Orthogonality in computer science from normative metaethics without starting to [pierce the mysterious opacity of](https://www.lesswrong.com/w/extrapolated-volition-normative-moral-theory) $<_V.$)

### Thick definitions of rationality or intelligence ^thick-definitions-of-rationality

Some philosophers responded to Hume's distinction of empirical rationality from normative reasoning, by advocating 'thick' definitions of intelligence that included some statement about the 'reasonableness' of the agent's ends.

For pragmatic purposes of AI alignment theory, if an agent is cognitively powerful enough to build Dyson Spheres, it doesn't matter whether that agent is defined as 'intelligent' or its ends are defined as 'reasonable'. A definition of the word 'intelligence' contrived to exclude paperclip maximization doesn't change the empirical behavior or empirical power of a paperclip maximizer.

### Relation to moral internalism ^relation-to-moral-internalism

While Orthogonality seems orthogonal to most traditional philosophical questions about metaethics, it does outright contradict some possible forms of moral internalism. For example, one could hold that by the very definition of rightness, knowledge of what is right must be inherently motivating to any entity that understands that knowledge. This is not the most common meaning of "moral internalism" held by modern philosophers, who instead seem to hold something like, "By definition, if I say that something is morally right, among my claims is that the thing is motivating _to me._" We haven't heard of a standard term for the position that, by definition, what is right must be _universally_ motivating; we'll designate that here as "universalist moral internalism".

We can potentially resolve this tension between Orthogonality and this assertion about the nature of rightness by:

-   Believing there must be some hidden flaw in the reasoning about a paperclip maximizer.
-   Saying "No True Scotsman" to the paperclip maximizer being intelligent, even if it's building Dyson Spheres.
-   Saying "No True Scotsman" to the paperclip maximizer "truly understanding" $<_V,$ even if Clippy is capable of predicting with extreme accuracy what humans will say and think about $<_V$, and Clippy does not suffer any other deficit of empirical prediction because of this lack of 'understanding', and Clippy does not require any special twist of its mind to avoid being compelled by its understanding of $<_V.$
-   Rejecting Orthogonality, and asserting that a paperclip maximizer must fall short of being an intact mind in some way that implies an empirical capabilities disadvantage.
-   Accepting nihilism, since a true moral argument must be compelling to everyone, and no moral argument is compelling to a paperclip maximizer. (Note: A paperclip maximizer doesn't care about whether clippiness must be compelling to everyone, which makes this argument self-undermining. See also [Rescuing the utility function](https://www.lesswrong.com/w/rescuing-the-utility-function) for general arguments against adopting nihilism when you discover that your mind's representation of something was running skew to reality.)
-   Giving up on universalist moral internalism as an empirical proposition; [AIXI-tl](https://www.lesswrong.com/w/aixi-tl) and Clippy empirically do different things, and will not be compelled to optimize the same goal no matter what they learn or know.

## Constructive specifications of orthogonal agents ^constructive-specifications-of-orthogona

We can exhibit [unbounded](https://www.lesswrong.com/w/methodology-of-unbounded-analysis) formulas for agents larger than their environments that optimize any given goal, such that Orthogonality is visibly true about agents within that class. Arguments about what all possible minds must do are clearly false for these particular agents, contradicting all strong forms of inevitabilism. These minds use huge amounts of computing power, but there is no known reason to expect that, e.g. worthwhile-happiness-maximizers have bounded analogues while paperclip-maximizers do not.

The simplest unbounded formulas for orthogonal agents don't involve reflectivity (the corresponding agents have no self-modification options, though they may create subagents). If we only had those simple formulas, it would theoretically leave open the possibility that self-reflection could somehow negate Orthogonality (reflective agents must inevitably have a particular utility function, and reflective agents being at a strong advantage relative to nonreflective agents). But there is already [ongoing work](https://www.lesswrong.com/w/tiling-agents-theory) on describing reflective agents that have the preference-stability property, and work toward increasingly bounded and approximable formulations of those. There is no hint from this work that Orthogonality is false; all the specifications have a free choice of utility function.

As of early 2017, the most recent work on tiling agents involves fully reflective, reflectively stable, logically uncertain agents whose computing time is roughly doubly-exponential in the size of the propositions considered.

So if you want to claim Orthogonality is false because e.g. all AIs will inevitably end up valuing all sapient life, you need to claim that the process of _reducing the already-specified doubly-exponential computing-time decision algorithm to a more tractable decision algorithm_ can _only_ be made realistically efficient for decision algorithms computing "Which policies protect all sapient life?" and are _impossible_ to make efficient for decision algorithms computing "Which policies lead to the most paperclips?"

Since work on tiling agent designs hasn't halted, one may need to backpedal and modify this impossibility claim further as more efficient decision algorithms are invented.

# Epistemic status ^epistemic-status

Among people who've seriously delved into these issues and are aware of the more advanced arguments for Orthogonality, we're not aware of anyone who still defends "universalist moral internalism" as described above, and we're not aware of anyone who thinks that arbitrary sufficiently-real-world-capable AI systems automatically adopt human-friendly terminal values.

Paul Christiano has said (if we're quoting him correctly) that although it's not his dominant hypothesis, he thinks some significant probability should be awarded to the proposition that only some subset of tractable utility functions, potentially excluding human-friendly ones or those of high cosmopolitan value, can be stable under reflection in powerful bounded AGI systems; e.g. because only direct functions of sense data can be adequately supervised in internal retraining. (This would be bad news rather than good news for AGI alignment and long-term optimization of human values.)

# Hume's Guillotine ^humes-guillotine

Orthogonality can be seen as corresponding to a philosophical principle advocated by David Hume, whose phrasings included, "Tis not contrary to reason to prefer the destruction of the whole world to the scratching of my finger." In our terms: an agent whose preferences over outcomes scores the destruction of the world more highly than the scratching of Hume's finger, is not thereby impeded from forming accurate models of the world or searching for policies that achieve various outcomes.

In modern terms, we'd say that Hume observed an apparent type distinction between _is_\-statements and _ought_\-statements:

> "In every system of morality, which I have hitherto met with, I have always remarked, that the author proceeds for some time in the ordinary ways of reasoning, and establishes the being of a God, or makes observations concerning human affairs; when all of a sudden I am surprised to find, that instead of the usual copulations of propositions, _is_, and _is not_, I meet with no proposition that is not connected with an _ought_, or an _ought not_. This change is imperceptible; but is however, of the last consequence."

"It is sunny outside" is an is-proposition. It can potentially be deduced solely from other is-facts, like "The Sun is in the sky" plus "The Sun emits sunshine". If we now furthermore say "And therefore I ought to go outside", we've introduced a new _type_ of sentence, which, Hume argued, cannot be deduced _just_ from is-statements like "The Sun is in the sky" or "I am low in Vitamin D". Even if the prior ought-sentence seems to us very natural, or taken-for-granted, like "It is better to be happy than sad", there must (Hume argued) have been some prior assertion or rule which, if we write it down in words, will contain words like _ought_, _should_, _better_, and _good._

Again translating Hume's idea into more modern form, we can see ought-sentences as special because they invoke some _ordering_ that we'll designate $<_V.$ E.g. "It's better to go outside than stay inside" asserts "Staying inside $<_V$ going outside". Whenever we make a statement about one outcome or action being "better", "preferred", "good", "prudent", etcetera, we can see this as implicitly ordering actions and outcomes under this $<_V$ relation. We can put temporarily on hold the question of what sort of entity $<_V$ may be; but we can already go ahead and observe that some assertions, the ought-assertions, mention this $<_V$ relation; and other propositions just talk about the frequency of photons in sunlight.

We could rephrase Hume's type distinction as observing that among within the set of all propositions, we can separate out a core set of propositions that _don't_ invoke $<_V,$ what we might call 'simple facts'. Furthermore, we can figure out simple facts just by making observations and considering other simple facts; the core set is closed under some kind of reasoning relation. This doesn't imply that we can get $<_V$\-sentences without considering simple facts. The $<_V$\-mentioning proposition "It's better to be outside than inside" can depend on the non-$<_V$\-mentioning proposition "It is sunny outside." But we can figure out whether it's sunny outside, without considering any oughts.

We then observe that questions like "How many paperclips will result conditional on action $\pi_0$ being taken?" and "What is an action $\pi$ that would yield a large number of expected paperclips?" are pure is-questions, meaning that we can figure out the answer without considering $<_V$\-mentioning propositions. So if there's some agent whose nature is just to output actions $\pi$ that are high in expected paperclips, the fact that this agent wasn't considering $<_V$\-propositions needn't hinder them from figuring out which actions are high in expected paperclips.

To establish that the paperclip maximizer need not suffer any defect of reality-modeling or planning or reflectivity, we need a bit more than the above argument. An _efficient_ agent needs to prioritize which experiments to run, or choose which questions to spend computing power thinking about, and this choice seems to invoke _some_ ordering. In particular, we need the [instrumental convergence thesis](https://www.lesswrong.com/w/instrumental-convergence-thesis) that

A further idea of Orthogonality is that _many_ possible orderings $<_U,$ including the 'number of resulting paperclips' ordering,

An is-description of a system can produce assertions like "_If_ the agent does action 1, _then_ the whole world will be destroyed except for David Hume's little finger, and _if_ the agent does action 2, _then_ David Hume's finger will be scratched" - these are material predictions on the order of "If water is put on this sponge, the sponge will get wet." To get from this is-statement to an ordering-statement like "action 1 $<_V$ action 2," we need some order-bearing statement like "destruction of world $<_V$ scratching of David Hume's little finger", or some order-introducing rule like "If action 1 causes the destruction of the world and action 2 does not, introduce a new sentence 'action 1 $<_V$ action 2'."

Taking this philosophical principle back to the notion of Orthogonality as a thesis in computer science: Since the type of 'simple material facts' is distinct from the type of 'simple material facts and preference orderings', it seems that we should be able to have agents that are just as good at thinking about the material facts, but output actions high in a different preference ordering.

The implication for Orthogonality as a thesis about computer science is that if one system of computation outputs actions according to whether they're high in the ordering $<_V,$ so that it tries to output it should be possible to construct another system that outputs actions higher in a different ordering (even if such actions are low in $<_P$) without this presenting any bar to the system's ability to reason about natural systems. A paperclip maximizer can have very good knowledge of the is-sentences about which actions lead to which consequences, while still outputting actions preferred under the ordering "Which action leads to the most paperclips?" instead of e.g. "Which action leads to the morally best consequences?" It is not that the paperclip maximizer is ignorant or mistaken about $<_P,$ but that the paperclip maximizer just doesn't output actions according to $<_P.$

# Arguments pro ^arguments-pro

# Counterarguments and countercounterarguments ^counterarguments-and-countercounterargum

## Proving too much ^proving-too-much

A disbeliever in Orthogonality might ask, "Do these arguments [Prove Too Much](https://www.lesswrong.com/w/proving-too-much), as shown by applying a similar style of argument to "There are minds that think 2 + 2 = 5?"

Considering the arguments above in turn:

• _Size of mind design space._

From the perspective of somebody who currently regards "wants to make paperclips" as an exceptionally weird and strange property, "There are lots of possible minds so some want to make paperclips" will seem to be on an equal footing with "There are lots of possible minds so some believe 2 + 2 = 5."

Thinking about the enormous space of possible minds might lead us to give more credibility to _some_ of those possible minds believing that 2 + 2 = 5, but we might still think that minds like that will be weak, or hampered by other defects, or limited in how intelligent they could really be, or more complicated to specify, or unlikely to occur in the actual real world.

So from the perspective of somebody who doesn't already believe in Orthogonality, the argument from the volume of mind design space is an argument at best for the Ultraweak version of Orthogonality.

• _Hume's is/ought distinction._

Depending on the exact variant of Hume-inspired argument that we deploy, the analogy to 2 + 2 = 5 might be weaker or stronger. For example, here's a Hume-inspired argument where the 2 + 2 = 5 analogy seems relatively strong:

"In every case of a mind judging that 'cure cancer' $>_P$ 'make paperclips', this ordering judgment is produced by some particular comparison operation inside the mind. Nothing prohibits a different mind from producing a different comparison. Whatever you say is the cause of the ordering judgment, e.g., that it derives from a prior judgment 'happy sapient lives' $>_P$ 'paperclips', we can imagine that part of the agent also have been programmed differently. Different causes will yield different effects, and whatever the causality behind 'cure cancer' $>_P$ 'make paperclips', we can imagine a different causally constituted agent which arrives at a different judgment."

If we substitute "2 + 2 = 5" into the above argument we get one in which all the constituent statements are equally true - this judgment is produced by a cause, the causes have causes, a different agent should produce a different output in that part of the computation, etcetera. So this version really has the same import as a general argument from the width of mind design space, and to a skeptic, would only imply the ultraweak form of Orthogonality.

However, if we're willing to consider some additional properties of is/ought, the analogy to "2 + 2 = 5" starts to become less tight. For instance, "Ought-comparators are not direct properties of the material world, there is no tiny $>_P$ among the quarks, and that's why we can vary action-preference computations without affecting quark-predicting computations" does _not_ have a clear analogous argument for why it should be just as easy to produce minds that judge 2 + 2 = 5.

• _Instrumental convergence._

There's no obvious analogue of "An agent that [knows as well as we do](https://www.lesswrong.com/w/epistemic-and-instrumental-efficiency) which policies are likely to lead to lots of expected paperclips, and an agent that knows as well as we do which policies are likely to lead to lots of happy sapient beings, are on an equal footing when it comes to doing things like scientific research", for "agents that believe 2 + 2 = 5 are at no disadvantage compared to agents that believe 2 + 2 = 4".

• _Reflective stability._

Relatively weaker forms of the reflective-stability argument might allow analogies between "prefer paperclips" and "believe 2 + 2 = 5", but probing for more details makes the analogy break down. E.g., consider the following supposedly analogous argument:

"Suppose you think the sky is green. Then you won't want to self-modify to make a future version of yourself believe that the sky is blue, because you'll believe this future version of yourself would believe something false. Therefore, all beliefs are equally stable under reflection."

This does poke at an underlying point: By default, all [Bayesian priors](https://www.lesswrong.com/w/prior) will be equally stable under reflection. However, minds that understand how different possible worlds will provide sensors with different evidence, will want to do [Bayesian updates](https://www.lesswrong.com/w/bayesian-update) on the data from the sensors. (We don't even need to regard this as changing the prior; under [Updateless Decision Theory](https://www.lesswrong.com/w/udt), we can see it as the agent branching its successors to behave differently in different worlds.) There's a particular way that a consequentialist agent, contemplating its own operation, goes from "The sky is very probably green, but might be blue" to "check what this sensor says and update the belief", and indeed, an agent like this will _not_ wantonly change its current belief _without_ looking at a sensor, as the argument indicates.

In contrast, the way in which "prefer more paperclips" propagates through an agent's beliefs about the effects of future designs and their interactions with the world does not suggest that future versions of the agent will prefer something other than paperclips, or that it would make the desire to produce paperclips conditional on a particular sensor value, since this [would not be expected to lead to more total paperclips](https://www.lesswrong.com/w/you-can-t-get-more-paperclips-that-way).

• _Orthogonal search tractability, constructive specifications of Orthogonal agent architectures._

These have no obvious analogue in "orthogonal tractability of optimization with different arithmetical answers" or "agent architectures that look very straightforward, are otherwise effective, and accept as input a free choice of what they think 2 + 2 equals".

## Moral internalism ^moral-internalism

(Todo: Moral internalism says that truly normative content must be inherently compelling to all possible minds, but we can exhibit increasingly bounded agent designs that obviously wouldn't be compelled by it. We can reply to this by (a) believing there must be some hidden flaw in the reasoning about a paperclip maximizer, (b) saying "No True Scotsman" to the paperclip maximizer even though it's building Dyson Spheres and socially manipulating its programmers, (c) believing that a paperclip maximizer must fall short of being a true mind in some way that implies a big capabilities disadvantage, (d) accepting nihilism, or (e) not believing in moral internalism.)

## Selection filters ^selection-filters

(Todo: Arguments from evolvability or selection filters. Distinguish naive failures to understand efficient instrumental convergence, from more sophisticated concerns in multipolar scenarios. Pragmatic argument on the histories of inefficient agents.)

# Pragmatic issues ^pragmatic-issues

(Todo: In practice, some utility functions / preference frameworks might be much harder to build and test than others. Eliezer Yudkowsky on realistic targets for the _first_ AGI needing to be built out of elements that are simple enough to be learnable. Paul Christiano's concern about whether only sensory-based goals might be possible to build.)

### Caveats ^caveats

-   The Orthogonality thesis is about mind design space in general. Particular agent architectures may not be Orthogonal.
    -   Some agents may be constructed such that their apparent utility functions shift with increasing cognitive intelligence.
    -   Some agent architectures may constrain what class of goals can be optimized.
-   'Agent' is intended to be understood in a very general way, and not to imply, e.g., a small local robot body.

For pragmatic reasons, the phrase 'every agent of sufficient cognitive power' in the Inevitability Thesis is specified to _include_ e.g. all cognitive entities that are able to invent new advanced technologies and build Dyson Spheres in pursuit of long-term strategies, regardless of whether a philosopher might claim that they lack some particular cognitive capacity in view of how they respond to attempted moral arguments, or whether they are e.g. conscious in the same sense as humans, etcetera.

### Refinements ^refinements

Most pragmatic implications of Orthogonality or Inevitability revolve around the following refinements:

[Implementation dependence](https://www.lesswrong.com/w/implementation_dependence): The humanly accessible space of AI development methodologies has enough variety to yield both AI designs that are value-aligned, and AI designs that are not value-aligned.

[Value loadability possible](https://www.lesswrong.com/w/value_loadability_possible): There is at least one humanly feasible development methodology for advanced agents that has Orthogonal freedom of what utility function or meta-utility framework is introduced into the advanced agent. (Thus, if we could describe a value-loadable design, and also describe a value-aligned meta-utility framework, we could combine them to create a value-aligned advanced agent.)

[Pragmatic inevitability](https://www.lesswrong.com/w/pragmatic_inevitability): There exists some goal G such that almost all humanly feasible development methods result in an agent that ends up behaving like it optimizes some particular goal G, perhaps among others. Most particular arguments about futurism will pick different goals G, but all such arguments are negated by anything that tends to contradict pragmatic inevitability in general.

### Implications ^implications

[Implementation dependence](https://www.lesswrong.com/w/implementation_dependence) is the core of the policy argument that solving the value alignment problem is necessary and possible.

Futuristic scenarios in which AIs are said in passing to 'want' something-or-other usually rely on some form of [pragmatic inevitability](https://www.lesswrong.com/w/pragmatic_inevitability) premise and are negated by [implementation dependence](https://www.lesswrong.com/w/implementation_dependence).

Orthogonality directly contradicts the metaethical position of [moral internalism](https://www.lesswrong.com/w/moral_internalism), which would be falsified by the observation of a [paperclip maximizer](https://www.lesswrong.com/w/paperclip-maximizer). On the metaethical position that [orthogonality and cognitivism are compatible](https://www.lesswrong.com/w/orthogonality-and-cognitivism-are-compatible), exhibiting a paperclip maximizer has few or no implications for object-level moral questions, and Orthogonality does not imply that our [humane values](https://www.lesswrong.com/w/humane-values) or [normative values](https://www.lesswrong.com/w/normative-values) are arbitrary, selfish, non-cosmopolitan, that we have a myopic view of the universe or value, etc.
