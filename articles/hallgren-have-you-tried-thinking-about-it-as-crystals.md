---
title: "Have You Tried Thinking About It As Crystals?"
author:
  - "Jonas Hallgren"
source_url: "https://www.lesswrong.com/posts/AeDCrYhmDqRkm6hDh/have-you-tried-thinking-about-it-as-crystals"
published: 2025-12-28
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "This post also has a more technical companion piece pointing out the connections to Singular Learning Theory and Geometric Deep Learning for the more…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**Epistemic Status:** _Written with my_ [_Simulator Worlds_](https://hitchhikersnirvana.substack.com/p/simulator-worlds-a-research-methodology) _framing. E.g I ran simulated scenarios with claude in order to generate good cognitive basins and then directed those to output this. This post is Internally Verified (e.g I think most of the claims are correct with an average of 60-75% certainty) and a mixture of an exploratory and analytical world._[^note-1]

_This post also has a more technical companion piece pointing out the connections to Singular Learning Theory and Geometric Deep Learning for the more technically inclined of you called_ [_Crystals in NNs: Technical Companion Piece_](https://www.lesswrong.com/posts/wR49EMdMgYvJnzwqL/crystals-in-nns-technical-companion-piece)_._

# **Have You Tried Thinking About It As Crystals?** ^have-you-tried-thinking

_Scene: A house party somewhere in the Bay Area. The kind where half the conversations are about AI timelines and the other half are about whether you can get good pho in Berkeley. Someone corners an interpretability researcher near the kombucha. (Original story concept by yours truly.)_

**CRYSTAL GUY:** So I've been thinking about shard theory.

**INTERP RESEARCHER:** Oh yeah? What about it?

**CRYSTAL GUY:** Well, it describes what trained networks look like, right? The structure. Multiple shards, contextual activation, grain boundaries between—

**INTERP RESEARCHER:** Sure. Pope, Turner, the whole thing. What about it?

**CRYSTAL GUY:** But it doesn't really explain _formation_. Like, why do shards form? Why those boundaries?

**INTERP RESEARCHER:** I mean, gradient descent, loss landscape geometry, singular learning theory—

**CRYSTAL GUY:** Right, but that's all about where you end up. Not about the path-dependence. Not about why early structure constrains later structure.

**INTERP RESEARCHER:** ...okay?

**CRYSTAL GUY:** Have you tried thinking about it as crystals?

**INTERP RESEARCHER:**

**CRYSTAL GUY:**

**INTERP RESEARCHER:** Like... crystals crystals? Healing crystals? Are you about to tell me about chakras?

**CRYSTAL GUY:** No, like—solid state physics crystals. Nucleation. Annealing. Grain boundaries. The whole condensed matter toolkit.

**INTERP RESEARCHER:** That's... hm.

**CRYSTAL GUY:** When you're eight years old, the concepts you already have determine what information you can receive. That determines what concepts you form by twelve. Previous timesteps constrain future timesteps. The loop closes.

**INTERP RESEARCHER:** That's just... learning?

**CRYSTAL GUY:** That's crystallization. Path-dependent formation where early structure templates everything after. And we have, like, a hundred years of physics for studying exactly this kind of process.

**INTERP RESEARCHER:** _takes a long sip of kombucha_

**CRYSTAL GUY:** Shards are crystal domains. Behavioral inconsistencies cluster at grain boundaries. RLHF is reheating an already-crystallized system—surface layers remelt but deep structure stays frozen.

**INTERP RESEARCHER:** ...go on.

---

## **RLHF as Reheating** ^rlhf-as-reheating

Let me start with a picture that I think is kind of cool:

**![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/teahvqbrf1hyihcg0ipb)**

RLHF and other fine-tuning procedures are like _reheating_ parts of an already-crystallized system under a new energy landscape. Instead of the pretraining loss, now there's a reward model providing gradients.

What happens depends on reheating parameters. Shallow local remelting affects only surface layers—output-adjacent representations remelt and recrystallize while deep structure remains frozen from pretraining. The deep crystals encoding capabilities are still there. But reheating also creates new grain boundaries where RLHF-crystallized structure meets pretraining-crystallized structure.

Catastrophic forgetting happens when fine-tuning is too aggressive—you melted the crystals that encoded capabilities.

Okay but why crystals? What does this even mean? Let me back up.

---

## **The Formation Problem** ^the-formation-problem

When we talk about AI alignment, we often discuss what aligned AI systems should _do_—follow human intentions, avoid deception, remain corrigible. But there's a more fundamental question: how does goal-directed behavior emerge in neural networks in the first place? Before we can align an agent, we need to understand how agents form.

Agent foundations is the study of what an agent even _is_. A core part of this is describing the ontology of the agent—what does a tree look like to the agent? How does that relate to the [existing knowledge tree of the agent](https://www.lesswrong.com/posts/fg9fXrHpeaDD6pEPL/truly-part-of-you)? This is one of the core questions of cognitive systems, and the computational version is interpretability.

Baked into most approaches is the assumption that we should take a snapshot of the agent and understand how it works from that snapshot. We look for [convergent abstractions](https://www.lesswrong.com/posts/gvzW46Z3BsaZsLc25/natural-abstractions-key-claims-theorems-and-critiques-1) that should be the same for any agent's ontology generation. We look at [Bayesian world models](https://www.lesswrong.com/posts/ZwshvqiqCvXPsZEct/the-learning-theoretic-agenda-status-2023). But these aren't continuous descriptions. This feels like a strange oversight. I wouldn't try to understand a human by taking a snapshot at any point in time. I'd look at a dynamic system that evolves.

For the experimental version, we now have developmental interpretability and singular learning theory, which is quite nice—it describes the process of model development. Yet I find interesting holes in the conceptual landscape. Particularly around [reward is not the optimization target](https://www.lesswrong.com/posts/pdaGN6pQyQarFHXF4/reward-is-not-the-optimization-target) and shard theory. The consensus seems to be that shards are natural expressions of learning dynamics—locally formed "sub-agents" acting in local contexts. But the developmental version felt missing.

If we have shards at the end, the process they go through is crystallization.

---

## **The Empirical Starting Point** ^the-empirical-starting-point

Here's something we know about humans: we don't follow the von Neumann-Morgenstern axioms. Decades of research shows we don't have a single coherent utility function. We have multiple context-dependent sub-utility functions. We're inconsistent across contexts. Our preferences shift depending on framing and environment.

Now, the standard interpretation—and I want to be fair to this view because serious people hold it seriously—is that these are _violations_. Failures of rationality. The VNM axioms tell you what coherent preferences look like, and we don't look like that, so we're doing something wrong. The heuristics-and-biases program built an entire research tradition on cataloguing the ways we deviate from the normative ideal.

But there's another perspective worth considering. Gerd Gigerenzer and colleagues at the [Center for Adaptive Behavior and Cognition](https://www.mpib-berlin.mpg.de/research/research-centers/adaptive-behavior-and-cognition) have developed what they call _ecological rationality_—the idea that the rationality of a decision strategy can't be evaluated in isolation from the environment where it's deployed ([Gigerenzer & Goldstein, 1996](https://pubmed.ncbi.nlm.nih.gov/8888650/); [Gigerenzer, Todd, & the ABC Research Group, 1999](https://philpapers.org/rec/GIGSHT-2)). On this view, heuristics aren't errors—they're adaptations. We learned at home, at school, on the playground. Different contexts, different statistical structures, different reward signals. What looks like incoherence from the VNM perspective might actually be a collection of locally-adapted strategies, each ecologically rational within its original learning environment.

The main thing to look at—and this is what I think matters for the crystallization picture—is that heuristics are neither rational nor irrational _in themselves_. Their success depends on the fit between the structure of the decision strategy and the structure of information in the environment where it's applied ([Todd & Gigerenzer, 2007](https://journals.sagepub.com/doi/10.1111/j.1467-8721.2007.00497.x)). You can think of this as an "adaptive toolbox" of domain-specific strategies that developed through exposure to different regimes.

Now, I'm not claiming this settles the normative question about what rationality _should_ look like. Decision theorists have legitimate reasons to care about coherence properties. But ecologically, empirically, descriptively—we seem to have something like shards. Multiple context-dependent systems that formed under different conditions and don't always play nicely together.

And if that's what we have, I want to understand _how_ it got that way. What kind of process produces this particular structure? The ecological rationality picture points toward something important: path dependence. Boundedness. The idea that what you've already learned shapes what you _can_ learn next, and that learning happens in contexts that have their own local structure.

---

## Path Dependence ^path-dependence

When you're 8 years old, the concepts you already have determine what information you can receive. That determines what concepts you form by 12. The concepts we have in science today depend on the concepts we had 100 years ago.

Previous timesteps constrain future timesteps. The loop closes. What you've already learned shapes what you can learn next.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/vnlmqldnqczgosdomc81)

This is crystallization—a path-dependent formation process where early structure templates everything after. It's different from just "gradient descent finds a minimum." The claim is that the _order_ of formation matters, and early-forming structures have outsized influence because they determine what can form later.

---

## Why This Is Actually Crystallization: The Fixed-Point Thing ^why-this-is-actually

But why call this crystallization specifically? What makes it more than just "path-dependent learning"?

The answer is the fixed-point structure. Consider what's happening from the agent's perspective—from inside the system that's forming abstractions and concepts.

Your current self-model generates your action space—what actions you even consider taking. Those actions generate observations. Those observations update the self-model. Yet, the observations you _can receive_ are constrained by the actions you took, which were constrained by the self-model you had. The self-model isn't just being updated by the world; it's being updated by a world filtered through itself.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/kwygenfaz5xcfg98laro)

This is a fixed point. The structure generates conditions that regenerate the structure.

In a physical crystal, atom positions create a potential landscape from neighbor interactions. That landscape determines where atoms get pushed. Atoms settle into positions that create the very landscape that holds them there. The loop closes.

For concept formation, same thing. Your existing abstractions determine what patterns you can notice in new data. The patterns you notice become new abstractions. Those abstractions then determine what you can notice next. Early-crystallizing conceptual structure has outsized influence on everything that crystallizes later—not because it came first temporally, but because it's _structurally load-bearing_ for everything built on top of it.

This is why it's crystallization and not just learning. Learning could in principle revise anything. Crystallization means some structure has become self-reinforcing—it generates the conditions for its own persistence. Perturb it slightly, and forces push it back. The information encoded in the structure maintains itself through time.

---

## **What Crystallization Actually Is** ^what-crystallization-actually-is

From an information-theoretic perspective, crystallization is a restructuring of how information is encoded.

In a liquid: high entropy per atom, low mutual information between distant atoms, you need to specify each position independently.

In a crystal: low entropy per atom (locked to lattice sites), high structured mutual information (knowing one tells you where others are), you only need a few parameters to describe the whole thing.

Total information doesn't disappear—it gets _restructured_. What was "N independent positions" becomes "global structure + local deviations." This is compression. The crystal has discovered a low-dimensional description of itself.

Neural networks do the same thing during training. They discover compressed representations. The crystallization picture says this has the same mathematical structure as physical crystallization—particularly the path-dependence and the fixed-point dynamics.

And here's how that looks when you write it down.

For a liquid, the joint entropy is roughly the sum of the marginals—each atom does its own thing:

$H(X_1, X_2, \ldots, X_N) \approx \sum_{i=1}^{N} H(X_i)$

The mutual information between distant atoms is negligible: $I(X_i; X_j) \approx 0$ for $|i - j|$ large. Your description length scales as $O(N)$.

For a crystal, the joint entropy collapses. Knowing one atom's position tells you almost everything:

$H(X_1, X_2, \ldots, X_N) \ll \sum_{i=1}^{N} H(X_i)$

Why does the joint entropy collapse so dramatically? Because the crystal has a lattice—a repeating pattern. Once you know where one atom sits and the lattice vectors that define the pattern, you can predict where every other atom will be. The positions aren't independent anymore; they're locked together by the structure. The mutual information structure inverts—$I(X_i; X_j)$ becomes large and structured precisely because atom $j$'s position is almost entirely determined by atom $i$'s position plus the lattice relationship between them.

Description length drops to $O(1)$ plus small corrections for thermal fluctuations around lattice sites.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/02a97980db662c8e531fb6fd9fd0db78aae977137dedf395206f95463eda838b/vpahxi4lcydv9ic9ahbb)

That gap between $\sum H(X_i)$ and $H(X_1, \ldots, X_N)$? That's the redundancy the crystal discovered. That's the compression. The system found that N apparently-independent degrees of freedom were secretly a low-dimensional manifold all along.

Neural networks do something similar during training. They discover compressed representations. The crystallization picture says this has the same mathematical structure as physical crystallization—particularly the path-dependence and the fixed-point dynamics.

---

## **Interlude: On Smells and Other Frozen Things** ^interlude-on-smells-and

_A new person has appeared near the kombucha. He's been listening for a while. It's unclear how long._

**ANDRÉS:** The thing about smells—

**INTERP RESEARCHER:** Sorry, were you part of this conversation?

**ANDRÉS:** —is that they're two synapses from the amygdala.

**CRYSTAL GUY:** We were talking about neural network training?

**ANDRÉS:** Yes. You're talking about crystallization. Early structure templating later structure. Fixed points. I'm telling you about smells.

_He says this as if it obviously follows._

**ANDRÉS:** When you smell your grandmother's kitchen—really smell it, not remember it, but get hit with the actual molecules—you're not activating some representation you built last year. You're hitting structure that formed when you were three. Before language. Before concepts. The deepest nucleation sites.

**CRYSTAL GUY:** ...okay?

**ANDRÉS:** This is why smell triggers memory differently than vision. Vision goes through all these processing layers. Lots of recrystallization opportunities. But olfaction? Direct line to ancient structure. You're touching the Pleistocene shards.

**INTERP RESEARCHER:** The Pleistocene shards.

**ANDRÉS:** The really old ones. The ones that formed when "rotten meat" was a load-bearing concept. You know how some smells are disgusting in a way you can't argue with? Can't reason your way out of it?

**INTERP RESEARCHER:** Sure.

**ANDRÉS:** Immutable crystals. Nucleated before your cortex had opinions. They're functionally frozen now—you'd have to melt the whole system to change them.

_He pauses, as if this is a natural place to pause._

**ANDRÉS:** Anyway, you were saying RLHF is reheating. This is correct. But the interesting thing is that brains do this too. On purpose.

**CRYSTAL GUY:** Do what?

**ANDRÉS:** Reheat. Meditation. Psychedelics. Sleep, probably. You're raising the effective temperature. Allowing local structure to reorganize.

**CRYSTAL GUY:** That's... actually the same picture I had for fine-tuning.

**ANDRÉS:** Of course it is. It's the same math. [Carhart-Harris](https://www.frontiersin.org/journals/human-neuroscience/articles/10.3389/fnhum.2014.00020/full) calls it "entropic disintegration"—psychedelics push the brain toward criticality, weaken the sticky attractors, let the system find new equilibria. It's literally [annealing](https://opentheory.net/2019/11/neural-annealing-toward-a-neural-theory-of-everything/). Trauma is a defect—a dislocation that formed under weird conditions and now distorts everything around it. You can't think your way out. The structure is frozen. But if you raise temperature carefully—good therapy, the right kind of attention—you get local remelting. The defect can anneal out.

_He picks up someone's abandoned kombucha, examines it, puts it back down._

**ANDRÉS:** The failure mode is the same too. Raise temperature too fast, melt too much structure, you get catastrophic forgetting. In a neural network this is bad fine-tuning. In a brain this is a psychotic break. Same phenomenon. Crystal melted too fast, recrystallized into noise.

**INTERP RESEARCHER:** I feel like I should be taking notes but I also feel like I might be getting pranked.

**ANDRÉS:** The deep question is whether you can do targeted annealing. Soften specific grain boundaries without touching the load-bearing structure. I think this is what good therapy is, actually. This is what integration is. You're not erasing the memory, you're—

**CRYSTAL GUY:** —recrystallizing the boundary region—

**ANDRÉS:** —yes, allowing it to find a lower-energy configuration while keeping the core structure intact.

_Silence._

**ANDRÉS:** Also this is why childhood matters so much and also why it's very hard to study. The nucleation period. Everything is forming. The temperature is high. The crystals that form then—they're not just early, they're _templating_. They determine what shapes are even possible later.

**INTERP RESEARCHER:** So early training in neural networks—

**ANDRÉS:** Same thing. Probably. The analogy is either very deep or meaningless, I'm not sure which. But the math looks similar.

_He appears to be finished. Then:_

**ANDRÉS:** Your aversion to certain foods, by the way. The ones that seem hardcoded. Those are successful alignment. Disgust reactions that formed correctly and locked in. Evolution got the reward signal right and the crystal formed properly. You should be grateful.

**CRYSTAL GUY:** I... don't know how to respond to that.

**ANDRÉS:** Most people don't.

_End of Interlude_ 

---

# Relating it to Neural Networks ^relating-it-to-neural

_Now, with that nice interlude from Andres out of the way, let's go back to neural networks to pinpoint a bit more how it intutively looks._ 

## **Abstractions as Crystallized Compressions** ^abstractions-as-crystallized-compression

Before training, a network has no commitment to particular features—activations could encode anything. After training, particular representational structures have crystallized.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/vqmojy02kzlxve09h7vb)

In the crystallization frame, natural abstractions are _thermodynamically stable phases_—crystal structures representing free energy minima. Convergence across different learning processes happens because different systems crystallizing in similar environments find similar stable phases.

---

## **Shards as Crystal Domains** ^shards-as-crystal-domains

Real materials rarely form perfect single crystals. They form _polycrystalline_ structures—many small domains with different orientations, meeting at grain boundaries.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/ebzmgbl6py3csdxraj1o)

This maps directly onto shard theory. A shard is a region where a particular organizational principle crystallized in a particular environmental regime. Grain boundaries between shards are where organizational principles meet—structurally compromised, where the network can't fully satisfy constraints from both adjacent shards.

Behavioral inconsistencies should cluster at grain boundaries. And behavioral inconsistencies across contexts is exactly what we observe in humans (and what the VNM violations are measuring).

---

## **Nucleation and Growth** ^nucleation-and-growth

Crystals nucleate at specific sites, then grow from those seeds.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/xhkgxpbeguogbuwjo69l)

For shards: nucleation happens early in training. Once nucleated, shards grow by recruiting nearby representational territory. When two shards grow toward each other and have incompatible orientations, a grain boundary forms.

Early training matters not just because it comes first, but because it establishes nucleation sites around which everything else organizes. The first shards to crystallize constrain the space of possible later shards.

(That is at least what the crystallization picture says taken to its full extent.)

---

## **Defects and Failure Modes** ^defects-and-failure-modes

Finally, we can completely overextend the analogy to try to make it useful for prediction. Weird shit should happen at the grain boundaries and such is the case with trolley problems for humans as an example.[^note-2] 

**![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/AeDCrYhmDqRkm6hDh/0347588c46b62cbc92b749b61e27b8990d99b7677b94e96352e63cabaa56581d/euysmfot9ryxs9wes1o4)**

Adversarial examples might exploit vacancies (representational gaps) or grain boundaries (inputs that activate multiple shards inconsistently). Jailbreaks might target the interface between different crystallization regimes. And maybe some big brain interpretability researcher might be able to use this to look at some actual stuff. 

---

_Back at the house party. The kombucha is running low._

**INTERP RESEARCHER:** Okay, so let me make sure I've got this. You're saying shards are like crystal domains that form through path-dependent nucleation, grain boundaries are where behavioral inconsistencies cluster, and RLHF is just reheating the surface while the deep structure stays frozen?

**CRYSTAL GUY:** Yeah, basically.

**INTERP RESEARCHER:** And you think this actually maps onto the math? Like, not just as a metaphor?

**CRYSTAL GUY:** I think the information-theoretic structure is the same. Whether the specific predictions hold up empirically is... an open question.

**INTERP RESEARCHER:** _finishes the kombucha_

**INTERP RESEARCHER:** You know what, this might actually be useful. Or it might be completely wrong. But I kind of want to look for grain boundaries now.

**CRYSTAL GUY:** That's all I'm asking.

**INTERP RESEARCHER:** Hey Neel, come over here. This guy wants to tell you about crystals.

---

## **Appendix: Glossary of Correspondences** ^appendix-glossary-of-correspondences

| Physical Concept | Learning System Analogue |
| --- | --- |
| Atom | Parameter / Activation / Feature |
| Configuration | Network state / Representation |
| Energy | Loss / Negative reward |
| Temperature | Learning rate / Noise level |
| Crystal | Coherent representational structure |
| Glass | Disordered, suboptimal representation |
| Nucleation | Initial formation of structured features |
| Growth | Expansion of representational domain |
| Grain boundary | Interface between shards |
| Defect | Representational gap / inconsistency |
| Annealing | Learning rate schedule / Careful training |
| Quenching | Fast training / Aggressive fine-tuning |
| Reheating | Fine-tuning / RLHF |

:::hide
_Thanks to Gunnar Zarnacke for some good discussions leading up to this and helping me clarify some of the ideas in the post._
:::

[^note-1]: _(I got a bit irritated after seeing comments around usage of LLMs because the way I use LLMs is not the average way of doing it so I will now start using this new way of indicating effort so that you can tell whether it is likely to be slop or not.)_
[^note-2]: (You can check [this book](https://www.joshua-greene.net/moral-tribes) out by Joshua Greene on his theories about a myopic submodule in the brain that activates during planning actions that are deontologically wrong from a societal perspective if you want to learn more.)
