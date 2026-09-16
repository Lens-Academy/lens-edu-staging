---
title: "What if Alignment is Not Enough?"
author:
  - "WillPetillo"
source_url: "https://www.lesswrong.com/posts/jFkEhqpsCRbKgLZrd/what-if-alignment-is-not-enough"
published: 2024-03-07
created: 2026-09-16
accessed: 2026-09-16
llm-review:
  date: 2026-09-16
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-16
    kind: "live"
description: "The following is a summary of Substrate Needs Convergence, as described in The Control Problem: Unsolved or Unsolvable?, No People as Pets (summarized here by Roman Yen), my podcast interview with Remmelt, and this conversation with Anders Sandberg.  Remmelt assisted in the editing of this post to verify I am accurately representing Substrate Needs Convergence—at least to a rough, first approximation of the argument. I am not personally weighing in as to whether I think this argument is true or not, but I think the ideas merit further attention so they can be accepted or discarded based on reasoned engagement.  The core claim is not what I thought it was when I first read the above sources and I notice that my skepticism has decreased as I have come to better understand the nature of the argument."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

The following is a summary of Substrate Needs Convergence, as described in [The Control Problem: Unsolved or Unsolvable?](https://www.lesswrong.com/posts/xp6n2MG5vQkPpFEBH/the-control-problem-unsolved-or-unsolvable), [No People as Pets](https://mflb.com/ai_alignment_1/no_people_as_pets_psr.html#p1) ([summarized](https://www.lesswrong.com/posts/zuXtMKuQRGAhZMoKk/on-the-possibility-of-impossibility-of-agi-long-term-safety) here by Roman Yen), my [podcast](https://youtu.be/PS_Wu47tCWo?feature=shared) interview with Remmelt, and [this conversation with Anders Sandberg](https://mflb.com/anders_s_1/d_231213_transcript_gen.html). Remmelt assisted in the editing of this post to verify I am accurately representing Substrate Needs Convergence—at least to a rough, first approximation of the argument.

I am not personally weighing in as to whether I think this argument is true or not, but I think the ideas merit further attention so they can be accepted or discarded based on reasoned engagement. The core claim is not what I thought it was when I first read the above sources and I notice that my skepticism has decreased as I have come to better understand the nature of the argument.

Quick note on terminology: “ASI” refers to an artificial super intelligence, or an AI that is powerful enough shape the course of world events, maintain itself, and its expected behavior can be considered in terms of the theoretical limits of capability provided by intelligence.

**Background**

Much existing alignment research takes as a given that humans will not be able to control ASI through guardrails, off switches, or other coercive methods. Instead, the focus is to build AI in such a way that what it wants is compatible with what humans want (the challenges involved in balancing the interests of different humans are often skipped over as out of scope). Commonly cited challenges include specification gaming, goal misgeneralization, and mesa-optimizers—all of which can be thought of as applications of Goodhart’s Law, where optimizing for different types of proxy measures lead to divergence from a true goal. The dream of alignment is that the ASI’s goal-seeking behavior guides it progressively closer to human values as the system becomes more capable, so coercive supervision from humans would not be necessary to keep the ASI in check.

This lens on AI safety assumes that intentions define outcomes. That is, if an agent wants something to happen then that thing will happen unless some outside force (such as a more powerful agent or collection of agents) pushes more strongly in a different direction. By extension, if the agent is a singleton ASI then it will have an asymmetric advantage over all external forces and, within the bounds of physics, its intentions are sure to become reality. But what if this assumption is false? What if even an ASI that initially acts in line with human-defined goals is in an attractor basin, where it is irresistibly pulled towards causing unsafe conditions over time? What if alignment is not enough?

**Substrate Needs Convergence**

Substrate Needs Convergence is the theory that ASI will gradually change under strong evolutionary pressures toward expanding itself. This converges over the long term on making the Earth uninhabitable for biological life. An overview follows:

1.  There are fundamental limits to how comprehensively any system—including an ASI—can sense, model, simulate, evaluate, and act on the larger environment.
    
2.  Self-modifying machinery (such as through repair, upgrades, or replication) inevitably results in effects unforeseeable even to the ASI.
    
3.  The space of unforeseeable side-effects of an ASI’s actions includes at least some of its newly learned/assembled subsystems eventually acting in more growth-oriented ways than the ASI intended.
    
4.  Evolutionary selection favors subsystems of the AI that act in growth-oriented ways over subsystems directed towards the AI’s original goals.
    
5.  The amount of control necessary for an ASI to preserve goal-directed subsystems against the constant push of evolutionary forces is strictly greater than the maximum degree of control available to any system of any type.
    
6.  Over time, any goal structures of any subsystems of the ASI that are not maximally efficient with respect to the needs of those subsystems themselves will be replaced, in increasing proportion, by just those goal aspects and subsystems that are maximally efficient.
    
7.  The physical needs of silicon-based digital machines and carbon-based biological life are fundamentally incompatible.
    
8.  Artificial self-sustaining systems will have a competitive advantage over biological life.
    
9.  Therefore, ASI will eventually succumb to evolutionary pressure to expand, over the long term destroying all biological life as a side-effect, regardless of its initially engineered values.
    

Note that this argument imagines ASI as a population of components, rather than a single entity, though the boundaries between these AIs can be more fluid and porous than between individual humans. It does not, however, make any assumptions regarding mono vs. multi-polar scenarios, fast vs. slow takeoff, or the amount of hierarchy in its organization.

Establishing an argument as plausible, likely, or proven requires radically different types of support, with the latter requiring significantly more logical rigor and empirical evidence. At least some researchers exploring this argument have claimed that Substrate Needs Convergence is provably true. This post, however, has the far more modest goal of articulating the case for plausibility, since it can be made far more succinctly. To this end, I will step through the premises and conclusion of the above chain, spending time on each proportional to their counter-intuitiveness.

**1, 2: Fundamental limits to control**

One might wonder whether the inability to control one’s subsystems is a limitation that applies to ASI. Even ASI, however, faces causal limits to its ability to control the world. It would not be reasonable, for example, to assume that ASI will be capable of building perpetual motion machines or faster-than-light travel. One category of impossible tasks is complete prediction of all of the relevant consequences of an agent’s actions on the real world. Sensors can only take in limited inputs (affected by noise), actuators can only have limited influence (also affected by noise), and world-models and simulations necessarily make simplifying assumptions. In other words, the law of unintended consequences holds true even for ASI. Further, the scale of these errors increases as the ASI does things that affect the entire world, gains more interacting components, and must account for increasingly complex feedback loops.

**3, 6: Growth as an emergent goal**

Usually, when people think of evolution, they think of selection for random, point-wise changes, such as mutations in DNA. In the case of ASI, we need to make sure that we’re comprehensive enough about what sort of unpredictable variations can be selected for. This can include not just point-wise changes (e.g. bit-flips induced by cosmic rays), but also new code learned from inputs, changes to assembled hardware configurations, or just changes in how existing functional components get connected into the system in new ways. The expression of those changes when the machinery is operating in the real world can cause unintended consequences (downstream effects) that could become evolutionarily selected for.

As in any evolutionary process, at least some variations will be detrimental to the variants and disappear…but some will benefit the variants in terms of their tendency to persist, grow in capacity, and self-replicate. Some of these variants will be suppressed by existing systems for acting contrary to the overarching goals of the system…but some will be effectively self-protecting enough to persist anyways.

By analogy, most cells in the human body that become cancerous are suppressed by the immune system, but some resist suppression and kill the host. Whether an ASI is more effective at suppressing variants than the human immune system is at suppressing cancer because of its intelligence, or less effective because of its scale, complexity, and because the growth-oriented components of the AI increase the overall reproductive fitness of the larger system (i.e., the ability of the AI to maintain itself in a variety of circumstances) is a question for likelihood, not plausibility, and is thus out of scope for this post.

One especially disruptive type of unintended consequence would be if the value system of the ASI changes in an unintended direction, resulting in value drift that is also subject to evolution’s pull towards growth and self-replication. A relevant analogy here is the toxoplasma virus, which changes the behavior of its host in a way that enables the virus to spread. Further, in the case of ASI, the host could very well benefit (in terms of survivability, growth, and replication) from a change analogous to having healthy microbes spreading through the body, such that it propagates the change all the more pervasively.

**4: Evolutionary selection favors growth**

Seems non-controversial given the presence of unpredictable variation discussed above and the general principles of natural selection.

Note that this selection is continuous: an absolute focus on growth has an evolutionary advantage over a partial focus, which has an advantage over none. It may be that new, growth-oriented goals fully displace old, human-compatible ones, or that new goals are overlaid over old ones. At first the latter is more likely, but the former becomes increasingly likely over time.

If this premise seems objectionable, consider whether that objection is actually to a different premise—particularly 3 or 5, regarding the emergence and persistence, respectively, of increasingly growth-oriented subsystems.

**5: The amount of control necessary for an ASI to preserve its values is greater than the amount of control possible**

The asymmetry between necessary and possible control is a difference in kind, not a difference in degree. That is, there are certain domains of tasks for which control breaks down and an ASI engaged in the scope of tasks for which an ASI would be necessary falls within these domains. This premise could thus be strengthened to state that, at the relevant levels of abstraction, the maximum control necessary for an ASI to preserve its values is greater than the maximum degree of control even conceptually possible. Proving this assertion is beyond the scope of this post, but we can explore this topic intuitively by considering simulation, one of the stages necessary to an intelligent control system.

A simulation is a simplified model of reality that hopefully captures enough of reality’s “essence” to be reasonably accurate within the domain of what the modeler considers relevant. If the model’s assumptions are poorly chosen or it focuses on the wrong things, it obviously fails, but let us assume that an ASI makes good models. Another factor limiting the quality of a simulation, however, is reality itself. Specifically, whether reality is dominated by negative feedback loops which cause errors to cancel or positive feedback loops that cause even the smallest errors to explode.

For illustration, Isaac Asimov’s _Foundation_ series imagines a future where the course of civilization is predictable, and thus controllable, through the use of “psycho-history.” This proposition is justified by analogizing society to the ideal gas law, which makes it possible to predict the pressure of a gas in an enclosed space, despite the atoms moving about chaotically, because those movements average out in a predictable way. Predictability at scale, however, cannot be assumed. The three body problem, or calculating the trajectories of three (or more) objects orbiting each other in space, is trivial to simulate, but that simulation will not be accurate when applied to the real world because the inevitable inaccuracies of the model will lead to exponentially increasing errors in the objects’ paths. One can thus think about how detailed an AI’s model of the world needs to be in order to control how its actions affect the world by asking whether the way the world works is more analogous to the ideal gas law (a complicated system) or the three body problem (a complex system).

**7\. Artificial systems are incompatible with biological life**

Seems non-controversial. Silicon wafers, for example, are produced with temperatures and chemicals deadly to humans. Also observe the detrimental impact on the environment from the expansion of industry. Hybrid systems simply move the issue from the relationship of artificial and biological entities to the relationship of artificial and biological aspects of an individual.

**8\. Artificial entities have an advantage over biological life**

Plausibility seems non-controversial; likelihood has been argued [elsewhere](https://stuff.kajsotala.fi/Papers/DigitalAdvantages.pdf).

**9\. Biological life is destroyed**

Stated in more detail: ASI will eventually be affected by such evolutionary pressures to the point that a critical accumulation of toxic outcomes will occur, in a way that is beyond the capability of the ASI itself to control for, resulting in the eventual total loss of all biological life. Even assuming initially human compatible goals—a big assumption in itself given the seeming intractability of the alignment problem as it is commonly understood—a progression towards increasingly toxic (to humans) outcomes occurs anyways because of the accumulation of mistakes resulting from the impossibility of complete control.

One might object with the analogy that it is not a foregone conclusion that (non-AI assisted) industrial expansion will destroy the natural environment. Reflecting on this analogy, however, reveals a core intuition supporting Substrate Needs Convergence. The reason humanity, without AI, has any hope at all of not destroying the world is that we are dependent on our environment for our survival. Living out of balance with our world is a path to self-destruction and our knowledge—and experience of collapse on small, local scales—of this reality acts as a counterbalancing force towards cooperation and against collective suicide. But it is on just this critical saving grace that AI is disanalogous. Existing on a different substrate, AI has no counterbalancing, long-term, baked-in incentive to protect the biological substrate on which we exist.

But perhaps ASI, even subject to Substrate Needs Convergence, will stop at some point, as the value of consuming the last pockets of biological life reaches diminishing returns while the benefit to keeping some life around remains constant? If one has followed the argument this far, such an objection is grasping at straws. Given that the pull of natural selection occurs over all parts of the ASI all the time, the evidentiary burden is on the skeptic to answer why certain parts of the biosphere would remain off limits to the continued growth of all components of the ASI indefinitely.

**Conclusions and relating Substrate Needs Convergence to alignment:**

Estimating the tractability of making ASI safe at scale is critical for deciding policy. If AI safety is easy and will occur by default with existing techniques, then we should avoid interfering with market processes. If it is difficult but solvable, we should look hard for solutions and make sure they are applied (and perhaps also slow AI capabilities development down as necessary to buy time). If it is impossible (or unreasonably difficult), then our focus should be on stopping progress towards ASI altogether.

Standard alignment theory requires four general things to go well:

1.  There is some known process for instilling an ASI’s goals reliably, directly through an engineered process or indirectly through training to a representative dataset.
    
2.  There is some known process for selecting goals that, if enacted, would be acceptable to the AI’s creators.
    
3.  Ensure that the AI’s creators select goals that are acceptable to humanity as a whole, rather than just to themselves.
    
4.  Ensure that safe systems, if developed, are actually used and not superseded by unsafe systems created by reckless or malevolent actors.
    

The theory of Substrate Needs Convergence proposes a fifth requirement:

5\. Initially safe systems, if developed and used, must remain safe at scale and over the long term.

The theory further argues that this fifth criterion’s probability of going well is nonexistent because evolutionary forces will push the AI towards human-incompatible behavior in ways that cannot be resisted by control mechanisms. Claiming that “intelligence” will solve this problem is not sufficient because increases in intelligence requires increases in the combinatorial complexity of processing components that results in the varied unforeseeable consequences that are the source of the problem.

I outlined the argument for Substrate Needs Convergence as an 9-part chain as a focus for further discussion, allowing for objections to fit into relatively clear categories. For example:

-   Objections that unintended consequences of component and environment interactions will never result in subsystems that seek growth beyond the demands of the original goals of the system negates premise 3.
    
-   Arguments regarding the limits of control are relevant to the likelihood of premise 5.
    
-   Claims that biological life has a competitive advantage over synthetic entities negates premise 8.
    

Addressing such objections is beyond the scope of this post. I’ve included high-level discussions of each of the claims in order to clarify their meaning and to articulate some of the intuitions that make them plausible. I hope that it has become clearer what the overall shape of the Substrate Needs Convergence argument is and I look forward to any discussion that follows.
