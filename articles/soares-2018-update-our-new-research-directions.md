---
title: "2018 Update: Our New Research Directions"
author:
  - "Nate Soares"
source_url: "https://intelligence.org/2018/11/22/2018-update-our-new-research-directions/"
published: 2018-11-22
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "For many years, MIRI’s goal has been to resolve enough fundamental confusions around alignment and intelligence to enable humanity to think clearly about"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

For many years, MIRI’s goal has been to resolve enough fundamental confusions around [alignment](https://intelligence.org/2016/12/28/ai-alignment-why-its-hard-and-where-to-start/) and intelligence to enable humanity to think clearly about technical AI safety risks—and to do this before this technology advances to the point of potential catastrophe. This goal has always seemed to us to be difficult, but possible.[^note-byline]

Last year, we said that we were beginning a new research program aimed at this goal.[^cite-2017-posts] Here, we’re going to provide background on how we’re thinking about this new set of research directions, lay out some of the thinking behind our recent decision to do less default sharing of our research, and make the case for interested software engineers to [join our team](https://intelligence.org/careers/software-engineer/) and help push our understanding forward.

### Contents: ^contents

1.  [[#^1-our-research|Our research]]
2.  [[#^2-why-deconfusion-is|Why deconfusion is so important to us]]
3.  [[#^3-nondisclosed-by-default-research-and|Nondisclosed-by-default research, and how this policy fits into our overall strategy]]
4.  [[#^4-joining-the-miri|Joining the MIRI team]]

### 1\. Our research ^1-our-research

In 2014, MIRI published its first research agenda, “[Agent Foundations for Aligning Machine Intelligence with Human Interests](https://intelligence.org/technical-agenda/).” Since then, one of our main research priorities has been to develop a better conceptual understanding of [embedded agency](https://www.alignmentforum.org/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version): formally characterizing reasoning systems that lack a crisp agent/environment boundary, are smaller than their environment, must reason about themselves, and risk having parts that are working at cross purposes. These research problems continue to be a major focus at MIRI, and are being studied in parallel with our new research directions (which I’ll be focusing on more below).[^note-alternative-lines]

From our perspective, the point of working on these kinds of problems isn’t that solutions directly tell us how to build well-aligned AGI systems. Instead, the point is to resolve confusions we have around ideas like “alignment” and “AGI,” so that future AGI developers have an unobstructed view of the problem. Eliezer illustrates this idea in “[The Rocket Alignment Problem](https://intelligence.org/2018/10/03/rocket-alignment/),” which imagines a world where humanity tries to land on the Moon before it understands Newtonian mechanics or calculus.

Recently, some MIRI researchers developed new research directions that seem to enable more scalable progress towards resolving these fundamental confusions. Specifically, the progress is more scalable in researcher hours—it’s now the case that we believe excellent engineers coming from a variety of backgrounds can have their work efficiently converted into research progress at MIRI—where previously, we only knew how to speed our research progress with a (relatively atypical) breed of mathematician.

At the same time, we’ve seen some significant [financial success](https://intelligence.org/2018/01/10/fundraising-success/) over the past year—not so much that funding is no longer a constraint at all, but enough to pursue our research agenda from new and different directions, in addition to the old.

Furthermore, our view implies that haste is essential. We see AGI as [a likely cause of existential catastrophes](https://www.econlib.org/archives/2016/03/so_far_unfriend.html), especially if it’s developed with relatively brute-force-reliant, difficult-to-interpret techniques; and although we’re [quite uncertain](https://intelligence.org/2017/10/13/fire-alarm/) about when humanity’s collective deadline will come to pass, many of us are somewhat alarmed by the speed of recent machine learning progress.

For these reasons, we’re eager to locate the right people quickly and offer them work on these new approaches; and with this kind of help, it strikes us as very possible that we can resolve enough fundamental confusion in time to port the understanding to those who will need it before AGI is built and deployed.

#### Comparing our new research directions and Agent Foundations ^comparing-our-new-research-directions

Our new research directions involve building software systems that we can use to test our intuitions, and building infrastructure that allows us to rapidly iterate this process. Like the Agent Foundations agenda, our new research directions continue to focus on “deconfusion,” rather than on, e.g., trying to improve robustness metrics of current systems—our sense being that even if we make major strides on this kind of robustness work, an AGI system built on principles similar to today’s systems would still be too opaque to align in practice.

In a sense, you can think of our new research as tackling the same sort of problem that we’ve always been attacking, but from new angles. In other words, if you aren’t excited about [logical inductors](https://intelligence.org/2016/09/12/new-paper-logical-induction/) or [functional decision theory](https://arxiv.org/abs/1710.05060), you probably wouldn’t be excited by our new work either. Conversely, if you already have the sense that becoming less confused is a sane way to approach AI alignment, and you’ve been wanting to see those kinds of confusions attacked with software and experimentation in a manner that yields theoretical satisfaction, then you may well want to work at MIRI. (I’ll have more to say about this [[#^4-joining-the-miri|below]].)

Our new research directions stem from some distinct ideas had by Benya Fallenstein, Eliezer Yudkowsky, and myself (Nate Soares). Some high-level themes of these new directions include:

1.  **Seeking entirely new low-level foundations for optimization**, designed for transparency and alignability from the get-go, as an alternative to gradient-descent-style machine learning foundations.
    
    Note that this does not entail trying to beat modern ML techniques on computational efficiency, speed of development, ease of deployment, or other such properties. However, it does mean developing new foundations for optimization that are broadly applicable in the same way, and for some of the same reasons, that gradient descent scales to be broadly applicable, while possessing significantly better alignment characteristics.
    
    We’re aware that there are many ways to attempt this that are shallow, foolish, or otherwise doomed; and in spite of this, we believe our own research avenues have a shot.
    
2.  **Endeavoring to figure out parts of cognition that can be very transparent as cognition**, without being GOFAI or completely disengaged from subsymbolic cognition.
3.  **Experimenting with some specific alignment problems** that are deeper than problems that have previously been put into computational environments.

In common between all our new approaches is a focus on using high-level theoretical abstractions to enable coherent reasoning about the systems we build. A concrete implication of this is that we write lots of our code in Haskell, and are often thinking about our code through the lens of type theory.

We aren’t going to distribute the technical details of this work anytime soon, in keeping with the recent MIRI policy changes [[#^3-nondisclosed-by-default-research-and|discussed below]]. However, we have a good deal to say about this research on the meta level.

We are excited about these research directions, both for their present properties and for the way they seem to be developing. When Benya began the predecessor of this work ~3 years ago, we didn’t know whether her intuitions would pan out. Today, having watched the pattern by which research avenues in these spaces have opened up new exciting-feeling lines of inquiry, none of us expect this research to die soon, and some of us are hopeful that this work may eventually open pathways to attacking the entire list of basic alignment issues.[^note-limited-tasks] ^section1-excited

We are similarly excited by the extent to which useful cross-connections have arisen between initially-unrelated-looking strands of our research. During a period where I was focusing primarily on new lines of research, for example, I stumbled across a solution to the original version of the [tiling agents problem](https://intelligence.org/files/TilingAgentsDraft.pdf) from the Agent Foundations agenda.[^note-tiling-paper]

This work seems to “give out its own guideposts” more than the Agent Foundations agenda does. While we used to require extremely close fit of our hires on research taste, we now think we have enough sense of the terrain that we can relax those requirements somewhat. We’re still looking for hires who are scientifically innovative and who are _fairly_ close on research taste, but our work is now much more scalable with the number of good mathematicians and engineers working at MIRI.

With all of that said, and despite how promising the last couple of years have seemed to us, this is still “blue sky” research in the sense that we’d guess most outside MIRI would still regard it as of academic interest but of no practical interest. The more principled/coherent/alignable optimization algorithms we are investigating are not going to sort cat pictures from non-cat pictures anytime soon.

The thing that generally excites us about research results is the extent to which they grant us “deconfusion” in the sense described in the next section, not the ML/engineering power they directly enable. This “deconfusion” that they allegedly reflect must, for the moment, be discerned mostly via abstract arguments supported only weakly by concrete “look what this understanding lets us do” demos. Many of us at MIRI regard our work as being of strong practical relevance nonetheless—but that is because we have long-term models of what sorts of short-term feats indicate progress, and because we view becoming less confused about alignment as having a strong practical relevance to humanity’s future, for reasons that I’ll sketch out next.

### 2\. Why deconfusion is so important to us ^2-why-deconfusion-is

#### What we mean by deconfusion ^what-we-mean-by-deconfusion

Quoting Anna Salamon, the president of the Center for Applied Rationality and a MIRI board member:

> If I didn’t have the concept of deconfusion, MIRI’s efforts would strike me as mostly inane. MIRI continues to regard its own work as significant for human survival, despite the fact that many larger and richer organizations are now talking about AI safety. It’s a group that got all excited about [Logical Induction](https://intelligence.org/2016/09/12/new-paper-logical-induction/) (and tried paranoidly to make sure Logical Induction “wasn’t dangerous” [before](https://www.alignmentforum.org/posts/iBBK4j6RWC7znEiDv/history-of-the-development-of-logical-induction) releasing it)—even though Logical Induction had only a moderate amount of math and no practical engineering at all (and did something similar with [Timeless Decision Theory](https://intelligence.org/files/TDT.pdf), to pick an even more extreme example). It’s a group that continues to stare mostly at basic concepts, sitting reclusively off by itself, while mostly leaving questions of politics, outreach, and how much influence the AI safety community has, to others.
> 
> However, I do have the concept of deconfusion. And when I look at MIRI’s activities through that lens, MIRI seems to me much more like “oh, yes, good, someone _is_ taking a straight shot at what looks like the critical thing” and “they seem to have a fighting chance” and “gosh, I hope they (or someone somehow) solve many many more confusions before the deadline, because without such progress, humanity sure seems kinda sunk.”

I agree that MIRI’s perspective and strategy don’t make much sense without the idea I’m calling “deconfusion.” As someone reading a MIRI strategy update, you probably already partly have this concept, but I’ve found that it’s not trivial to transmit the full idea, so I ask your patience as I try to put it into words.

By deconfusion, I mean something like “making it so that you can think about a given topic without continuously accidentally spouting nonsense.”

To give a concrete example, my thoughts about infinity as a 10-year-old were made of rearranged confusion rather than of anything coherent, as were the thoughts of even the best mathematicians from 1700. “How can 8 plus infinity still be infinity? What happens if we subtract infinity from both sides of the equation?” But my thoughts about infinity as a 20-year-old were _not_ similarly confused, because, by then, I’d been exposed to the more coherent concepts that later mathematicians labored to produce. I wasn’t as smart or as good of a mathematician as Georg Cantor or the best mathematicians from 1700; but deconfusion can be transferred between people; and this transfer can spread the ability to think actually coherent thoughts.

In 1998, conversations about AI risk and technological singularity scenarios often went in circles in a funny sort of way. People who are serious thinkers about the topic today, including my colleagues Eliezer and Anna, said things that today sound confused. (When I say “things that sound confused,” I have in mind things like “isn’t intelligence an [incoherent](https://arbital.com/p/general_intelligence/) concept,” “but the economy’s [already](http://slatestarcodex.com/2015/12/27/things-that-are-not-superintelligences/) superintelligent,” “if a superhuman AI is smart enough that it could kill us, it’ll also be [smart enough](https://arbital.com/p/orthogonality/) to see that that isn’t what the good thing to do is, so we’ll be fine,” “we’re Turing-complete, so it’s impossible to have something dangerously [smarter](https://intelligence.org/2017/12/06/chollet/) than us, because Turing-complete computations can emulate anything,” and “anyhow, we could just [unplug](https://intelligence.org/2018/02/28/sam-harris-and-eliezer-yudkowsky/#3) it.”) Today, these conversations are different. In between, folks worked to make themselves and others less fundamentally confused about these topics—so that today, a 14-year-old who wants to skip to the end of all that incoherence can just pick up a copy of Nick Bostrom’s [_Superintelligence_](https://en.wikipedia.org/wiki/Superintelligence:_Paths,_Dangers,_Strategies).[^cite-flynn-careers]

Of note is the fact that the “take AI risk and technological singularities seriously” meme started to spread to the larger population of ML scientists only after its main proponents attained sufficient deconfusion. If you were living in 1998 with a strong intuitive sense that AI risk and technological singularities should be taken seriously, but you still possessed a host of confusion that caused you to occasionally spout nonsense as you struggled to put things into words in the face of various confused objections, then evangelism would do you little good among serious thinkers—perhaps because the respectable scientists and engineers in the field can smell nonsense, and can tell (correctly!) that your concepts are still incoherent. It’s by accumulating deconfusion until your concepts cohere and your arguments become well-formed that your ideas can become memetically fit and spread among scientists—and can serve as foundations for future work by those same scientists.

Interestingly, the history of science is in fact full of instances in which individual researchers possessed a mostly-correct body of intuitions for a long time, and then eventually those intuitions were formalized, corrected, made precise, and transferred between people. Faraday discovered a wide array of electromagnetic phenomena, guided by an intuition that he wasn’t able to formalize or transmit except through hundreds of pages of detailed laboratory notes and diagrams; Maxwell later invented the language to describe electromagnetism formally by reading Faraday’s work, and expressed those hundreds of pages of intuitions in three lines.

An even more striking example is the case of Archimedes, who intuited his way to the ability to do useful work in both integral and differential calculus thousands of years before calculus became a simple formal thing that could be passed between people.

In both cases, it was the eventual formalization of those intuitions—and the linked ability of these intuitions to be passed accurately between many researchers—that allowed the fields to begin building properly and quickly.[^note-historical-examples]

#### Why deconfusion (on our view) is highly relevant to AI accident risk ^why-deconfusion-is-highly-relevant

If human beings eventually build smarter-than-human AI, and if smarter-than-human AI is as powerful and hazardous as we currently expect it to be, then AI will one day bring enormous forces of optimization to bear.[^note-hazardous-upside] We believe that when this occurs, those enormous forces need to be brought to bear on real-world problems and subproblems deliberately, in a context where they’re theoretically well-understood. The larger those forces are, the more precision is called for when researchers aim them at cognitive problems.

We suspect that today’s concepts about things like “optimization” and “aiming” are incapable of supporting the necessary precision, even if wielded by researchers who care a lot about safety. Part of why I think this is that if you pushed me to explain what I mean by “optimization” and “aiming,” I’d need to be careful to avoid spouting nonsense—which indicates that I’m still confused somewhere around here.

A worrying fact about this situation is that, as best I can tell, humanity _doesn’t_ need coherent versions of these concepts to [hill-climb](https://en.wikipedia.org/wiki/Hill_climbing) its way to AGI. Evolution hill-climbed that distance, and evolution had no model of what it was doing. But as evolution applied massive optimization pressure to genomes, those genomes started coding for brains that _internally_ optimized for targets that merely correlated with genetic fitness. Humans find ever-smarter ways to satisfy our own goals (video games, ice cream, birth control…) even when this runs directly counter to the selection criterion that gave rise to us: “propagate your genes into the next generation.”

If we are to avoid a similar fate—one where we attain AGI via huge amounts of gradient descent and other optimization techniques, only to find that the resulting system has internal optimization targets that are very different from the targets we externally optimized it to be adept at pursuing—then we must be more careful.

As AI researchers explore the space of optimizers, what will it take to ensure that the first highly capable optimizers that researchers find are optimizers they know how to aim at chosen tasks? I’m not sure, because I’m still in some sense confused about the question. I can tell you vaguely how the problem relates to [convergent instrumental incentives](https://en.wikipedia.org/wiki/Instrumental_convergence), and I can observe various reasons why we shouldn’t expect the strategy “train a large cognitive system to optimize for _X_” to actually result in a system that [internally optimizes](https://intelligence.org/2017/04/12/ensuring/#3) for _X_, but there are still wide swaths of the question where I can’t say much without saying nonsense.

As an example, AI systems like Deep Blue and AlphaGo cannot reasonably be said to be reasoning about the whole world. They’re reasoning about some much simpler abstract platonic environment, such as a Go board. There’s an intuitive sense in which we don’t need to worry about these systems taking over the world, for this reason (among others), even in the world where those systems are run on implausibly large amounts of compute.

Vaguely speaking, there’s a sense in which some alignment difficulties don’t arise until an AI system is “reasoning about the real world.” But what does that mean? It doesn’t seem to mean “the space of possibilities that the system considers literally concretely includes reality itself.” Ancient humans did perfectly good general reasoning even while utterly lacking the concept that the universe can be described by specific physical equations.

It looks like it must mean something more like “the system is building internal models that, in some sense, are little representations of the whole of reality.” But what counts as a “little representation of reality,” and why do a hunter-gatherer’s confused thoughts about a spirit-riddled forest count while a chessboard doesn’t? All these questions are likely confused; my goal here is not to name coherent questions, but to gesture in the direction of a confusion that prevents me from precisely naming a portion of the alignment problem.

Or, to put it briefly: precisely naming a problem is half the battle, and we are currently confused about how to precisely name the alignment problem.

For an alternative attempt to name this concept, refer to Eliezer’s [rocket alignment](https://intelligence.org/2018/10/03/rocket-alignment/) analogy. For a further discussion of some of the reasons today’s concepts seem inadequate for describing an aligned intelligence with sufficient precision, see Scott and Abram’s [recent write-up](https://www.alignmentforum.org/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version). (Or come discuss with us in person, at an “[AI Risk for Computer Scientists](https://intelligence.org/ai-risk-for-computer-scientists/)” workshop.)

#### Why this research may be tractable here and now ^why-this-research-may-be-tractable

Many types of research become far easier at particular places and times. It seems to me that for the work of becoming less confused about AI alignment, MIRI in 2018 (and for a good number of years to come, I think) is one of those places and times.

Why? One point is that MIRI has some history of success at deconfusion-style research (according to me, at least), and MIRI’s researchers are beneficiaries of the local research traditions that grew up in dialog with that work. Among the bits of conceptual progress that MIRI contributed to are:

-   today’s understanding that AI accident risk is important;
-   today’s understanding that an aligned AI is at least a theoretical possibility (the [Gandhi argument](https://intelligence.org/files/ComplexValues.pdf) that consequentialist preferences are reflectively stable by default, etc.), and that it’s worth investing in basic research toward the possibility of such an AI in advance;
-   early statements of subproblems like [corrigibility,](https://arbital.com/p/updated_deference/) the [Löbian obstacle](https://intelligence.org/files/TilingAgentsDraft.pdf), and [subsystem alignment](https://intelligence.org/2018/11/06/embedded-subsystems/), including descriptions of various problems in the [Agent Foundations](https://intelligence.org/technical-agenda/) research agenda;
-   [timeless decision theory](https://intelligence.org/files/TDT.pdf) and its successors ([updateless decision theory](https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory) and [functional decision theory](https://intelligence.org/2017/10/22/fdt/));
-   [logical induction](https://intelligence.org/2016/09/12/new-paper-logical-induction/);
-   [reflective oracles](https://arxiv.org/abs/1508.04145); and
-   many smaller results in the vicinity of the Agent Foundations agenda, notably [robust cooperation](https://intelligence.org/2014/02/01/robust-cooperation-a-case-study-in-friendly-ai-research/) in the one-shot prisoner’s dilemma, [universal inductors](https://agentfoundations.org/item?id=941), and [model polymorphism](https://www.lesswrong.com/posts/DDJr5fuR5jeD47k9g/an-angle-of-attack-on-open-problem-1), [HOL-in-HOL](https://intelligence.org/2015/12/04/new-paper-proof-producing-reflection-for-hol/), and more recent progress on Vingean reflection.

Logical inductors, as an example, give us at least a clue about why we’re apt to informally use words like “probably” in mathematical reasoning. It’s not a full answer to “how does probabilistic reasoning about mathematical facts work?”, but it does feel like an interesting hint—which is relevant to thinking about how “real-world” AI reasoning could possibly work, because AI systems might well also use probabilistic reasoning in mathematics.

A second point is that, if there is something that unites most folks at MIRI _besides_ a drive to increase the odds of human survival, it is probably a taste for getting our understanding of the foundations of the universe right. Many of us came in with this taste—for example, many of us have backgrounds in physics (and fundamental physics in particular), and those of us with a background in programming tend to have an interest in things like type theory, formal logic, and/or probability theory.

A third point, as noted [[#^section1-excited|above]], is that we are excited about our current bodies of research intuitions, and about how they seem increasingly transferable/cross-applicable/concretizable over time.

Finally, I observe that the field of AI at large is currently highly vitalized, largely by the deep learning revolution and various other advances in machine learning. We are not particularly focused on deep neural networks ourselves, but being in contact with a vibrant and exciting practical field is the sort of thing that tends to spark ideas. 2018 really seems like an unusually easy time to be seeking a theoretical science of AI alignment, in dialog with practical AI methods that are beginning to work.

### 3\. Nondisclosed-by-default research, and how this policy fits into our overall strategy ^3-nondisclosed-by-default-research-and

MIRI recently decided to make most of its research “nondisclosed-by-default,” by which we mean that going forward, most results discovered within MIRI will remain internal-only unless there is an explicit decision to release those results, based usually on a specific anticipated safety upside from their release.

I’d like to try to share some sense of why we chose this policy—especially because this policy may prove disappointing or inconvenient for many people interested in AI safety as a research area.[^note-explaining] MIRI is a nonprofit, and there’s a natural default assumption that our mechanism for good is to regularly publish new ideas and insights. But we don’t think this is currently the right choice for serving our nonprofit mission.

The short version of why we chose this policy is:

-   we’re in a hurry to decrease existential risk;
-   in the same way that Faraday’s journals aren’t nearly as useful as Maxwell’s equations, and in the same way that logical induction isn’t all that useful to the average modern ML researcher, we don’t think it would be that useful to try to share lots of half-confused thoughts with a wider set of people;
-   we believe we can have more of the critical insights faster if we stay focused on making new research progress rather than on exposition, and if we aren’t feeling pressure to justify our intuitions to wide audiences;
-   we think it’s not unreasonable to be anxious about whether deconfusion-style insights could lead to capabilities insights, and have empirically observed we can think more freely when we don’t have to worry about this; and
-   even when we conclude that those concerns were paranoid or silly upon reflection, we benefited from moving the cognitive work of evaluating those fears from “before internally sharing insights” to “before broadly distributing those insights,” which is enabled by this policy.

The somewhat longer version is below.

I’ll caveat that in what follows I’m attempting to convey what I believe, but not necessarily why—I am not trying to give an argument that would cause any rational person to take the same strategy in my position; I am shooting only for the more modest goal of conveying how I myself am thinking about the decision.

I’ll begin by saying a few words about how our research fits into our overall strategy, then discuss the pros and cons of this policy.

#### When we say we’re doing AI alignment research, we really genuinely don’t mean outreach ^when-we-say-were-doing-ai

At present, MIRI’s aim is to make research progress on the alignment problem. Our focus isn’t on shifting the field of ML toward taking AGI safety more seriously, nor on any other form of influence, persuasion, or field-building. We are simply and only aiming to directly make research progress on the core problems of alignment.

This choice may seem surprising to some readers—field-building and other forms of outreach can obviously have hugely beneficial effects, and throughout MIRI’s history, we’ve been much more outreach-oriented than the typical math research group.

Our impression is indeed that well-targeted outreach efforts can be highly valuable. However, attempts at outreach/influence/field-building seem to us to currently constitute a large majority of worldwide research activity that’s motivated by AGI safety concerns,[^note-outreach-focus] such that MIRI’s time is better spent on taking a straight shot at the core research problems. Further, we think our own comparative advantage lies here, and not in outreach work.[^note-straight-shot]

My beliefs here are connected to my beliefs about the mechanics of deconfusion described [[#^2-why-deconfusion-is|above]]. In particular, I believe that the alignment problem might start seeming significantly easier once it can be precisely named, and I believe that precisely naming this sort of problem is likely to be a serial challenge—in the sense that some deconfusions cannot be attained until other deconfusions have matured. Additionally, my read on history says that deconfusions regularly come from relatively small communities thinking the right kinds of thoughts (as in the case of Faraday and Maxwell), and that such deconfusions can spread rapidly as soon as the surrounding concepts become coherent (as exemplified by Bostrom’s _Superintelligence_). I conclude from all this that trying to influence the wider field isn’t the best place to spend our own efforts.

#### It is difficult to predict whether successful deconfusion work could spark capability advances ^it-is-difficult-to-predict

We think that most of MIRI’s expected impact comes from worlds in which our deconfusion work eventually succeeds—that is, worlds where our research eventually leads to a principled understanding of alignable optimization that can be communicated to AI researchers, more akin to a modern understanding of calculus and differential equations than to Faraday’s notebooks (with the caveat that most of us aren’t expecting solutions to the alignment problem to compress nearly so well as calculus or Maxwell’s equations, but I digress).

One pretty plausible way this could go is that our deconfusion work makes alignment possible, without much changing the set of available pathways to AGI.[^note-easiest-path] To pick a trivial analogy illustrating this sort of world, consider [interval arithmetic](https://en.wikipedia.org/wiki/Interval_arithmetic) as compared to the usual way of doing floating point operations. In interval arithmetic, an operation like _sqrt_ takes two floating point numbers, a lower and an upper bound, and returns a lower and an upper bound on the result. Figuring out how to do interval arithmetic requires some careful thinking about the error of floating-point computations, and it certainly won’t speed those computations up; the only reason to use it is to ensure that the error incurred in a floating point operation isn’t larger than the user assumed. If you discover interval arithmetic, you’re at no risk of speeding up modern matrix multiplications, despite the fact that you really have found a new way of doing arithmetic that has certain desirable properties that normal floating-point arithmetic lacks.

In worlds where deconfusing ourselves about alignment leads us primarily to insights similar (on this axis) to interval arithmetic, it would be best for MIRI to distribute its research as widely as possible, especially once it has reached a stage where it is comparatively easy to communicate, in order to encourage AI capabilities researchers to adopt and build upon it.

However, it is also plausible to us that a successful theory of alignable optimization may itself spark new research directions in AI capabilities. For an analogy, consider the progression from classical probability theory and statistics to a modern deep neural net classifying images. Probability theory alone does not let you classify cat pictures, and it is possible to understand and implement an image classification network without thinking much about probability theory; but probability theory and statistics were central to the way machine learning was actually discovered, and still underlie how modern deep learning researchers think about their algorithms.

In worlds where deconfusing ourselves about alignment leads to insights similar (on this axis) to probability theory, it is much less clear whether distributing our results widely would have a positive impact. It goes without saying that we want to have a positive impact (or, at the very least, a neutral impact), even in those sorts of worlds.

The latter scenario is relatively less important in worlds where [AGI timelines](https://intelligence.org/2017/10/13/fire-alarm/) are short. If current deep learning research is already on the brink of AGI, for example, then it becomes less plausible that the results of MIRI’s deconfusion work could become a relevant influence on AI capabilities research, and most of the potential impact of our work would come from its direct applicability to deep-learning-based systems. While many of us at MIRI believe that short timelines are at least plausible, there is significant uncertainty and disagreement about timelines inside MIRI, and I would not feel comfortable committing to a course of action that is safe only in worlds where timelines are short.

In sum, if we continue to make progress on, and eventually substantially succeed at, figuring out the actual “cleave nature at its joints” concepts that let us think coherently about alignment, I find it quite plausible that those same concepts may also enable capabilities boosts (especially in worlds where there’s a lot of time for those concepts to be pushed in capabilities-facing directions). There is certainly strong historical precedent for deep scientific insights yielding unexpected practical applications.

By the nature of deconfusion work, it seems very difficult to predict in advance which other ideas a given insight may unlock. These considerations seem to us to call for conservatism and delay on information releases—potentially very long delays, as it can take quite a bit of time to figure out where a given insight leads.

#### We need our researchers to not have walls within their own heads ^we-need-our-researchers-to

We take our research seriously at MIRI. This means that, for many of us, we know in the back of our minds that deconfusion-style research could sometimes (often in an unpredictable fashion) open up pathways that can lead to capabilities insights in the manner discussed above. As a consequence, many MIRI researchers flinch away from having insights when they haven’t spent a lot of time thinking about the potential capabilities implications of those insights down the line—and they usually haven’t spent that time, because it requires a bunch of cognitive overhead. This effect has been evidenced in reports from researchers, myself included, and we’ve empirically observed that when we set up “closed” research retreats or research rooms,[^note-closed-retreats] researchers report that they can think more freely, that their brainstorming sessions extend further and wider, and so on.

This sort of inhibition seems quite bad for research progress. It is not a small area that our researchers were (un- or semi-consciously) holding back from; it’s a reasonably wide swath that may well include most of the deep ideas or insights we’re looking for.

At the same time, this kind of caution is an unavoidable consequence of doing deconfusion research in public, since it’s very hard to know what ideas may follow five or ten years after a given insight. AI alignment work and AI capabilities work are close enough neighbors that many insights in the vicinity of AI alignment are “potentially capabilities-relevant until proven harmless,” both for reasons discussed above and from the perspective of the conservative [security mindset](https://intelligence.org/2017/11/25/security-mindset-ordinary-paranoia/) we try to encourage around here.

In short, if we request that our brains come up with alignment ideas that are fine to share with everybody—and this is what we’re implicitly doing when we think of ourselves as “researching publicly”—then we’re requesting that our brains cut off the massive portion of the search space that is only probably safe.

If our goal is to make research progress as quickly as possible, in hopes of having concepts coherent enough to allow rigorous safety engineering by the time AGI arrives, then it seems worth finding ways to allow our researchers to think without constraints, even when those ways are somewhat expensive.

#### Focus seems unusually useful for this kind of work ^focus-seems-unusually-useful

There may be some additional speed-up effects from helping free up researchers’ attention, though we don’t consider this a major consideration on its own.

Historically, early-stage scientific work has often been done by people who were solitary or geographically isolated, perhaps because this makes it easier to slowly develop a new way to factor the phenomenon, instead of repeatedly translating ideas into the current language others are using. It’s difficult to describe how much mental space and effort turns out to be taken up with thoughts of how your research will look to other people staring at you, until you try going into a closed room for an extended period of time with a promise to yourself that all the conversation within it really won’t be shared at all anytime soon.

Once we realized this was going on, we realized that in retrospect, we may have been ignoring common practice, in a way. Many startup founders have reported finding stealth mode, and funding that isn’t from VC outsiders, tremendously useful for focus. For this reason, we’ve also recently been encouraging researchers at MIRI to worry less about appealing to a wide audience when doing public-facing work. We want researchers to focus mainly on whatever research directions they find most compelling, make exposition and distillation a secondary priority, and not worry about optimizing ideas for persuasiveness or for being easier to defend.

#### Early deconfusion work just isn’t that useful (yet) ^early-deconfusion-work

ML researchers aren’t running around using logical induction or functional decision theory. These theories don’t have practical relevance to the researchers on the ground, and they’re not supposed to; the point of these theories is just deconfusion.

To put it more precisely, the theories themselves aren’t the interesting novelty; the novelty is that a few years ago, we couldn’t write down _any_ theory of how in principle to assign sane-seeming probabilities to mathematical facts, and today we can write down logical induction. In the journey from point _A_ to point _B_, we became less confused. The logical induction paper is an artifact witnessing that deconfusion, and an artifact which granted its authors additional deconfusion as they went through the process of writing it; but the thing that excited me about logical induction was not any one particular algorithm or theorem in the paper, but rather the fact that we’re a little bit less in-the-dark than we were about how a reasoner can reasonably assign probabilities to logical sentences. We’re not fully out of the dark on this front, mind you, but we’re a little less confused than we were before.[^note-academic-papers]

If the rest of the world were talking about how confusing they find the AI alignment topics we’re confused about, and were as concerned about their confusions as we are concerned about ours, then failing to share our research would feel a lot more costly to me. But as things stand, most people in the space look at us kind of funny when we say that we’re excited about things like logical induction, and I repeatedly encounter deep misunderstandings when I talk to people who have read some of our papers and tried to infer our research motivations, from which I conclude that they weren’t drawing a lot of benefit from my current ramblings anyway.

And in a sense most of our current research is a form of rambling—in the same way, at best, that Faraday’s journal was rambling. It’s OK if most practical scientists avoid slogging through Faraday’s journal and wait until Maxwell comes along and distills the thing down to three useful equations. And, if Faraday expects that physical theories eventually distill, he doesn’t need to go around evangelizing his journal—he can just wait until it’s been distilled, and then work to transmit some less-confused concepts.

We expect our understanding of alignment, which is currently far from complete, to eventually distill, and I, at least, am not very excited about attempting to push it on anyone until it’s significantly more distilled. (Or, barring full distillation, until a project with a commitment to the common good, an adequate [security mindset](https://intelligence.org/2017/11/25/security-mindset-ordinary-paranoia/), and a large professed interest in deconfusion research comes knocking.)

In the interim, there are of course some researchers outside MIRI who care about the same problems we do, and who are also pursuing deconfusion. Our nondisclosed-by-default policy will negatively affect our ability to collaborate with these people on our other research directions, and this is a real cost and not worth dismissing. I don’t have much more to say about this here beyond noting that if you’re one of those people, you’re very welcome to [get in touch with us](mailto:contact@intelligence.org) (and you may want to consider [[#^4-joining-the-miri|joining the team]])!

#### We’ll have a better picture of what to share or not share in the future ^well-have-a-better-picture

In the long run, if our research is going to be useful, our findings will need to go out into the world where they can impact how humanity builds AI systems. However, it doesn’t follow from this need for eventual distribution (of some sort) that we might as well publish all of our research immediately. As discussed above, as best I can tell, our current research insights just aren’t that practically useful, and sharing early-stage deconfusion research is time-intensive.

Our nondisclosed-by-default policy also allows us to preserve options like:

-   deciding which research findings we think should be developed further, while thinking about [differential technological development](https://nickbostrom.com/existential/risks.html); and
-   deciding which group(s) to share each interesting finding with (e.g., the general public, other closed safety research groups, groups with strong commitment to security mindset and the common good, etc.).

Future versions of us obviously have better abilities to make calls on these sorts of questions, though this needs to be weighed against many facts that push in the opposite direction—the later we decide what to release, the less time others have to build upon it, and the more likely it is to be found independently in the interim (thereby wasting time on duplicated efforts), and so on.

Now that I’ve listed reasons in favor of our nondisclosed-by-default policy, I’ll note some reasons against.

#### Considerations pulling against our nondisclosed-by-default policy ^considerations-pulling-against

There are a host of pathways via which our work will be harder with this nondisclosed-by-default policy:

-   a. We will have a harder time attracting and evaluating new researchers; sharing less research means getting fewer chances to try out various research collaborations and notice which collaborations work well for both parties.
-   b. We lose some of the benefits of accelerating the progress of other researchers outside MIRI via sharing useful insights with them in real time as they are generated.
-   c. We will be less able to get useful scientific insights and feedback from visitors, remote scholars, and researchers elsewhere in the world, since we will be sharing less of our work with them.
-   d. We will have a harder time attracting funding and other indirect aid—with less of our work visible, it will be harder for prospective donors to know whether our work is worth supporting.
-   e. We will have to pay various costs associated with keeping research private, including social costs and logistical overhead.

We expect these costs to be substantial. We will be working hard to offset some of the losses from _a_, as I’ll discuss in the next section. For reasons discussed [[#^early-deconfusion-work|above]], I’m not presently very worried about _b_. The remaining costs will probably be paid in full.

These costs are why we didn’t adopt this policy (for most of our research) years ago. With outreach feeling less like our comparative advantage than it did in the [pre-Puerto-Rico](https://intelligence.org/2015/07/16/an-astounding-year/) days, and funding seeming like less of a bottleneck than it used to (though still something of a bottleneck), this approach now seems workable.

We’ve already found it helpful in practice to let researchers have insights first and sort out the safety or desirability of publishing later. On the whole, then, we expect this policy to cause a significant net speed-up to our research progress, while ensuring that we can responsibly investigate some of the most important technical questions on our radar.

### 4\. Joining the MIRI team ^4-joining-the-miri

I believe that MIRI is, and will be for at least the next several years, a focal point of one of those rare scientifically exciting points in history, where the conditions are just right for humanity to substantially deconfuse itself about an area of inquiry it’s been pursuing for centuries—and one where the output is directly impactful in a way that is rare even among scientifically exciting places and times.

What can we offer? On my view:

-   Work that Eliezer, Benya, myself, and a number of researchers in AI safety view as having a significant chance of boosting humanity’s survival odds.
-   Work that, if it pans out, visibly has central relevance to the alignment problem—the kind of work that has a meaningful chance of shedding light on problems like “is there a loophole-free way to upper-bound the amount of optimization occurring within an optimizer?”.
-   Problems that, if your tastes match ours, feel closely related to fundamental questions about intelligence, agency, and the structure of reality; and the associated thrill of working on one of the great and wild frontiers of human knowledge, with large and important insights potentially close at hand.
-   An atmosphere in which people are taking their own and others’ research progress seriously. For example, you can expect colleagues who come into work every day looking to actually make headway on the AI alignment problem, and looking to pull their thinking different kinds of sideways until progress occurs. I’m consistently impressed with MIRI staff’s drive to get the job done—with their visible appreciation for the fact that their work really matters, and their enthusiasm for helping one another make forward strides.
-   As an increasing focus at MIRI, empirically grounded computer science work on the AI alignment problem, with clear feedback of the form “did my code type-check?” or “do we have a proof?”.
-   Finally, some good, old-fashioned fun—for a certain very specific brand of “fun” that includes the satisfaction that comes from making progress on important technical challenges, the enjoyment that comes from pursuing lines of research you find compelling without needing to worry about writing grant proposals or otherwise raising funds, and the thrill that follows when you finally manage to distill a nugget of truth from a thick cloud of confusion.

Working at MIRI also means working with other people who were drawn by the very same factors—people who seem to me to have an unusual degree of care and concern for human welfare and the welfare of sentient life as a whole, an unusual degree of creativity and persistence in working on major technical problems, an unusual degree of cognitive reflection and skill with perspective-taking, and an unusual level of efficacy and grit.

My own experience at MIRI has been that this is a group of people who really want to help Team Life get good outcomes from the large-scale events that are likely to dramatically shape our future; who can tackle big challenges head-on without appealing to [false narratives](https://www.lesswrong.com/posts/st7DiQP23YQSxumCt/on-doing-the-improbable) about how likely a given approach is to succeed; and who are remarkably good at fluidly updating on new evidence, and at creating a really fun environment for collaboration.

#### Who are we seeking? ^who-are-we-seeking

We’re seeking anyone who can cause our “become less confused about AI alignment” work to go faster.

In practice, this means: people who natively think in math or code, who take seriously the problem of becoming less confused about AI alignment (quickly!), and who are generally capable. In particular, we’re looking for high-end Google programmer levels of capability; you don’t need a 1-in-a-million test score or a [halo](https://www.lesswrong.com/posts/5o4EZJyqmHY4XgRCY/einstein-s-superpowers) [of](https://equilibriabook.com/toc/) [destiny](https://www.lesswrong.com/posts/dhj9dhiwhq3DX6W8z/hero-licensing). You also don’t need a PhD, explicit ML background, or even prior research experience.

Even if you’re not pointed towards our research agenda, we intend to fund or help arrange funding for any deep, good, and truly new ideas in alignment. This might be as a hire, a fellowship grant, or whatever other arrangements may be needed.

#### What to do if you think you might want to work here ^what-to-do-if-you-think

If you’d like more information, there are several good options:

-   Chat with **[Buck Shlegeris](mailto:buck@intelligence.org)**, a MIRI computer scientist who helps out with our recruiting. In addition to answering any of your questions and running interviews, Buck can sometimes help skilled programmers take some time off to skill-build through our [**AI Safety Retraining Program**](https://intelligence.org/2018/09/01/summer-miri-updates/#2).
-   If you already know someone else at MIRI and talking with them seems better, you might alternatively **reach out to that person**—especially [Blake Borgeson](mailto:blake@intelligence.org) (a new MIRI board member who helps us with technical recruiting) or [Anna Salamon](mailto:annasalamon@gmail.com) (a MIRI board member who is also the president of CFAR, and is helping run some MIRI recruiting events).
-   Come to a 4.5-day [**AI Risk for Computer Scientists**](https://intelligence.org/ai-risk-for-computer-scientists/) workshop, co-run by MIRI and CFAR. These workshops are open only to people who Buck arbitrarily deems “probably above MIRI’s technical hiring bar,” though their scope is wider than simply hiring for MIRI—the basic idea is to get a bunch of highly capable computer scientists together to try to fathom AI risk (with a good bit of rationality content, and of trying to fathom the way we’re failing to fathom AI risk, thrown in for good measure).
    
    These are a great way to get a sense of MIRI’s culture, and to pick up a number of thinking tools whether or not you are interested in working for MIRI. If you’d like to either apply to attend yourself or nominate a friend of yours, [send us your info here](https://goo.gl/forms/Qmv9fy4N3pcEH4Q12).
    
-   Come to next year’s **MIRI Summer Fellows program**, or be a **summer intern** with us. This is a better option for mathy folks aiming at Agent Foundations than for computer sciencey folks aiming at our new research directions. This last summer we took 6 interns and 30 MIRI Summer Fellows (see Malo’s [Summer MIRI Updates](https://intelligence.org/2018/09/01/summer-miri-updates/) post for more details). Also, note that “summer internships” need not occur during summer, if some other schedule is better for you. Contact [Colm Ó Riain](mailto:colm@intelligence.org) if you’re interested.
-   You could just try [applying for a job](https://intelligence.org/careers/).

#### Some final notes ^some-final-notes

**A quick note on “[inferential distance](https://wiki.lesswrong.com/wiki/Inferential_distance),” or on what it sometimes takes to understand MIRI researchers’ perspectives:** To many, MIRI’s take on things is really weird. Many people who bump into our writing somewhere find our basic outlook pointlessly weird/silly/wrong, and thus find us uncompelling forever. Even among those who do ultimately find MIRI compelling, many start off thinking it’s weird/silly/wrong and then, after some months or years of MIRI’s worldview slowly rubbing off on them, eventually find that our worldview makes a bunch of unexpected sense.

If you think that you may be in this latter category, and that such a change of viewpoint, should it occur, [would](http://slatestarcodex.com/2017/03/24/guided-by-the-beauty-of-our-weapons/) [be](https://wiki.lesswrong.com/wiki/Litany_of_Tarski) [because](https://arbital.com/p/bayes_rule/?l=1zq) MIRI’s worldview is onto something and not because we all got tricked by [false-but-compelling](https://www.readthesequences.com/Death-Spirals-Sequence) ideas… you might want to start exposing yourself to all this funny worldview stuff now, and see where it takes you. Good starting-points are [_Rationality: From AI to Zombies_](https://intelligence.org/rationality-ai-zombies/); [_Inadequate Equilibria_](http://equilibriabook.com/toc); [_Harry Potter and the Methods of Rationality_](http://www.hpmor.com/); the “[AI Risk for Computer Scientists](https://intelligence.org/ai-risk-for-computer-scientists/)” workshops; ordinary [CFAR workshops](http://www.rationality.org/workshops/upcoming); or just hanging out with folks in or [near](http://intelligence.org/MIRIx) MIRI.

I suspect that I’ve failed to communicate some key things above, based on past failed attempts to communicate my perspective, and based on some readers of earlier drafts of this post missing key things I’d wanted to say. I’ve tried to clarify as many points as possible—hence this post’s length!—but in the end, “we’re focusing on research and not exposition now” holds for me too, and I need to get back to the work.[^note-contact]

**A note on the state of the field:** MIRI is one of the dedicated teams trying to solve technical problems in AI alignment, but we’re not the only such team. There are currently three others: the [Center for Human-Compatible AI](http://humancompatible.ai/) at UC Berkeley, and the safety teams at [OpenAI](https://openai.com/) and at [Google DeepMind](https://deepmind.com/). All three of these safety teams are highly capable, top-of-their-class research groups, and we recommend them too as potential places to join if you want to make a difference in this field.

There are also solid researchers based at many other institutions, like the Future of Humanity Institute, whose [Governance of AI Program](https://www.fhi.ox.ac.uk/governance-ai-program/) focuses on the important social/coordination problems associated with AGI development.

To learn more about AI alignment research at MIRI and other groups, I recommend the MIRI-produced [Agent Foundations](https://intelligence.org/technical-agenda) and [Embedded Agency](https://www.alignmentforum.org/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version) write-ups; Dario Amodei, Chris Olah, et al.’s [Concrete Problems](https://arxiv.org/abs/1606.06565) agenda; the [AI Alignment Forum](https://www.alignmentforum.org/); and [Paul Christiano](https://ai-alignment.com/) and the [DeepMind safety team](https://medium.com/@deepmindsafetyresearch/)’s blogs.

**On working here:** Salaries here are more flexible than people usually suppose. I’ve had a number of conversations with folks who assumed that because we’re a nonprofit, we wouldn’t be able to pay them enough to maintain their desired standard of living, meet their financial goals, support their family well, or similar. This is false. If you bring the right skills, we’re likely able to provide the compensation you need. We also place a high value on weekends and vacation time, on avoiding burnout, and in general on people here being happy and thriving.

You do need to be physically in Berkeley to work with us on the projects we think are most exciting, though we have pretty great relocation assistance and ops support for moving.

Despite all of the great things about working at MIRI, I would consider working here a pretty terrible deal if all you wanted was a job. Reorienting to work on major global risks isn’t likely to be the most hedonic or relaxing option available to most people.

On the other hand, if you like the idea of an epic calling with a group of people who somehow claim to take seriously a task that sounds more like it comes from a science fiction novel than from a _Dilbert_ strip, while having a lot of scientific fun; or you just care about humanity’s future, and want to help however you can… give us a call.

[^note-byline]: This post is an amalgam put together by a variety of MIRI staff. The byline saying “Nate” means that I (Nate) endorse the post, and that many of the concepts and themes come in large part from me, and I wrote a decent number of the words. However, I did not write all of the words, and the concepts and themes were built in collaboration with a bunch of other MIRI staff. (This is roughly what bylines have meant on the MIRI blog for a while now, and it’s worth noting explicitly.)

[^cite-2017-posts]: See our 2017 [strategic update](https://intelligence.org/2017/04/30/2017-updates-and-strategy/) and [fundraiser](https://intelligence.org/2017/12/01/miris-2017-fundraiser/) posts for more details.

[^note-alternative-lines]: In [past](https://intelligence.org/2015/07/17/miris-2015-summer-fundraiser/) [fundraisers](https://intelligence.org/2015/12/01/miri-2015-winter-fundraiser/), we’ve said that with sufficient funding we would like to spin up alternative lines of attack on the alignment problem. Our new research directions can be seen as following this spirit, and indeed, at least one of our new research directions is heavily inspired by alternative approaches I was considering back in 2015. That said, unlike many of the ideas I had in mind when writing our 2015 fundraiser posts, our new work is quite contiguous with our Agent-Foundations-style research.

[^note-limited-tasks]: That is, the requisites for aligning AGI systems to perform limited [tasks](https://arbital.com/p/task_goal/); not all of the requisites for aligning a full [CEV](https://arbital.com/p/3c5/)-class [autonomous AGI](https://arbital.com/p/Sovereign/). Compare Paul Christiano’s distinction between [ambitious and narrow value learning](https://ai-alignment.com/ambitious-vs-narrow-value-learning-99bd0c59847e) (though note that Paul thinks narrow value learning is sufficient for strongly autonomous AGI).

[^note-tiling-paper]: This result is described more in a paper that will be out soon. Or, at least, eventually. I’m not putting a lot of time into writing papers these days, for reasons discussed below.

[^cite-flynn-careers]: For more discussion of this concept, see “[Personal Thoughts on Careers in AI Policy and Strategy](http://effective-altruism.com/ea/1fa/personal_thoughts_on_careers_in_ai_policy_and/)” by Carrick Flynn.

[^note-historical-examples]: Historical examples of deconfusion work that gave rise to a rich and healthy field include the distillation of Lagrangian and Hamiltonian mechanics from Newton’s laws; Cauchy’s overhaul of real analysis; the slow acceptance of the usefulness of complex numbers; and the development of formal foundations of mathematics.

[^note-hazardous-upside]: I should emphasize that from my perspective, humanity never building AGI, never realizing our potential, and failing to make use of the [cosmic endowment](https://nickbostrom.com/astronomical/waste.html) would be a tragedy comparable (on an [astronomical](https://nickbostrom.com/astronomical/waste.html) scale) to AGI wiping us out. I say “hazardous”, but we shouldn’t lose sight of the upside of humanity getting the job done right.

[^note-explaining]: My own feeling is that I and other senior staff at MIRI have never been particularly _good_ at explaining what we’re doing and why, so this inconvenience may not be a new thing. It’s new, however, for us to not be making it a priority to _attempt_ to explain where we’re coming from.

[^note-outreach-focus]: In other words, many people are explicitly focusing only on outreach, and many others are selecting technical problems to work on with a stated goal of strengthening the field and drawing others into it.

[^note-straight-shot]: This isn’t meant to suggest that nobody else is taking a straight shot at the core problems. For example, OpenAI’s [Paul Christiano](https://ai-alignment.com/) is a top-tier researcher who is doing exactly that. But we nonetheless want more of this on the present margin.

[^note-easiest-path]: For example, perhaps the easiest path to unalignable AGI involves following descendants of today’s gradient descent and deep learning techniques, and perhaps the same is true for alignable AGI.

[^note-closed-retreats]: In other words, retreats/rooms where it is common knowledge that all thoughts and ideas are not going to be shared, except perhaps after some lengthy and irritating bureaucratic process and with everyone’s active support.

[^note-academic-papers]: As an aside, perhaps my main discomfort with attempting to publish academic papers is that there appears to be no venue in AI where we can go to say, “Hey, check this out—we used to be confused about _X_, and now we can say _Y_, which means we’re a little bit less confused!” I think there are a bunch of reasons behind this, not least the fact that the nature of confusion is such that _Y_ usually sounds obviously true once stated, and so it’s particularly difficult to make such a result sound like an impressive practical result.

    A side effect of this, unfortunately, is that all MIRI papers that I’ve ever written with the goal of academic publishing do a pretty bad job of saying what I was previously confused about, and how the “result” is indicative of me becoming less confused—for which I hereby apologize.

[^note-contact]: If you have more questions, I encourage you to shoot us an email at [contact@intelligence.org](mailto:contact@intelligence.org).
