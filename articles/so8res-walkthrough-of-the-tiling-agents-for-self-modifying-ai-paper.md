---
title: "Walkthrough of the Tiling Agents for Self-Modifying AI paper"
author:
  - "So8res"
source_url: "https://www.lesswrong.com/posts/QGrX3qK3qxQYK9D4C/walkthrough-of-the-tiling-agents-for-self-modifying-ai-paper"
published: 2013-12-13
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "This is my walkthrough of Tiling Agents for Self-Modifying AI, and the Löbian Obstacle. It's meant to summarize the paper and provide a slightly-less…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

This is my walkthrough of [Tiling Agents for Self-Modifying AI, and the Löbian Obstacle](http://intelligence.org/files/TilingAgents.pdf). It's meant to summarize the paper and provide a slightly-less-technical introduction to the content. I've also collected a number of typos and suggestions, which can be found at the end of the post.

# Motivation ^motivation

We want to be able to consider agents which build slightly better versions of themselves, which build slightly better versions of themselves, and so on. This is referred to as an agent "tiling" itself. This introduces a question: how can the parent agent trust its descendants?

We'll be dealing with logical systems, which are crisply deterministic. In such a setting, child agents can be "absolutely trustworthy": for example, if the child uses the same methods of proof and the same axioms as the parent, then the parent should be able to trust the child unconditionally: or, at least, the parent should trust the child at least as much as it trusts itself.

This turns out to be a huge problem, because modern logical systems _don't_ trust themselves (or any logical systems of equal strength), to say nothing of (supposedly more powerful) successor systems.

This problem of trust is rooted in a theorem stated by the mathematician Löb.

Assuming that we can surmount such difficulties, there are a number of other principles that we want in our tiling agents, such as the Vingean principle (the parent shouldn't have to know exactly what the children will do) and the Naturalistic principle (agents should think of themselves as part of the world). These will be discussed in detail later in the paper.

# Glossary ^glossary

-   I'll use @x to mean "the execution of x". (The paper uses x̄ instead.)
-   I'll use \[x\] denotes the Gödel number of x in some suitable encoding. (The paper uses  ⌈x⌉ instead).
-   □T\[x\] is read "There is a proof of x in T". It's the same as "∃y. Prooves\_T(y, \[x\])". The T is omitted when it's clear from the context.
-   A0, A1, … will denote agents. Note that A0 is the _child_ and A1 is the _parent_. I personally would have done things the other way around, but I'll stick to the paper's descending style.
-   G will be used to denote a world-state in which the agent's goals have been achieved.
-   ∅ will be used to denote a world-state wherein nothing of import has been changed by the agent. For more specificity, see the paper.
-   A ⊩ x is read "A has cognitively concluded x" or "A believes x".
-   PA is Peano Arithmetic, ZF is Zermelo-Fraenkel set theory.
-   T will denote a theory. In general, assume that T is at least as powerful as PA.
-   T+1 is T ∪ {¬□T\[⊥\]} (T plus the fact that T is consistent). T+2 is (T+1)+1, etc.

Here's a few reminders, just in case you're rusty:

-   φ\[x\\y\] denotes "φ, with all instances of x replaced by y". The slash disambiguates this from quoting.
-   ≜ means "is defined to be".
-   T ⊢ φ is pronounced "T derives φ".

So, for example, T ⊢ □T\[φ\] is read "T knows that there is a T-proof of φ."

In general, I'll be less formal than the paper. If I've left any ambiguities, see the paper for clarification.

# Trusting Yourself ^trusting-yourself

Imagine that we've got a parent agent A1. It wants to achieve the goal G. Among the things it can do is create more agents. What we want to do is find an agent A0 within the actions of A1 such that:

A1 ⊩ @A0 → (∀action ∈ Acts0. @action → □0\[@action → (∅ ∨ G)\])

Translated, this reads "A1 believes that, if it constructs A0, then for all actions available to A0, that action will only be taken if A0 has proven that taking the action leads to either nothing of import happening, or the goal being achieved."

(We also require A1 ⊩ @A0 → ((∀action ∈ Acts0. ¬@action) → ∅), which says "if A0 takes no actions then nothing will happen".)

We would further like A1 to be able to trust A0. Obviously, we don't want A1 to trust its children unconditionally. But assuming that A0's proofs use the same mechanism as A1's proofs, and assuming that A1 verifies that A0's proof system works _exactly_ like A1's own proof system, we would like to have the following:

A1 ⊩ @A0 → (∀action ∈ Acts0. @action → (∅ ∨ G))

ie, A1 believes that, if it constructs A0, then any action taken by A0 _actually will_ either cause nothing to happen or achieve the goal.

This is an important distinction, make sure you understand it before proceeding. We want A1 to _unwrap_ A0's proofs, to look at things inside the □0 and conclude that they actually are true. We want A1 to look at □0\[φ\] and actually conclude φ.

Unfortunately, this is impossible — at least, it's impossible when A1 has concluded that A0's proof system is identical to A1s proof system. Why? Because A1 can't even trust its own formalism. This is the famed Löb's theorem.

# The Löbstacle ^the-l-bstacle

Intuitively, Löb's theorem claims "No system T can trust its own proofs until it witnesses them." More formally, it states that in a theory T at least as powerful as PA, □T\[φ\] → φ ⇔ φ: T can only deduce φ from a T-proof of φ if φ is actually true.

You might expect that there are _some_ sentences ψ which T cannot prove, but for which T knows "if I _could_ prove ψ, then ψ would be true". This is not the case! There are _no_ sentences that T cannot prove, for which T will trust "but _if I could prove it_, then it would be true". T does not trust its own proofs until it witnesses them. Here's why:

Any T of sufficient power can define a sentence L ↔ □\[L\]→φ (L is true iff a proof of L implies φ.) T can deduce the following about such an L for _any_ φ.

1.  `L → (□[L]→φ)` (from the definition of L)
2.  `□[L→(□[L]→φ)]` (from 1 because T can prove the things it knows: T ⊢ x ⇒ T ⊢ □\[x\])
3.  `□[L]→□[□[L]→φ]` (from 2 because provability distributes over implication: T ⊢ □\[x→y\] ⇒ T ⊢ □\[x\]→□\[y\])
4.  `□[L]→(□[□[L]]→□[φ])` (from 3 because provability distributes over implication)
5.  `□[L]→□[□[L]]` (because T can prove things it knows)
6.  `□[L]→□[φ]` (from 4 and 5)

Note that φ here is general. This means that for _any_ φ, there is a sentence L such that φ is provable when L is provable, and also φ is true when L is provable. Now, _if_ T had □\[φ\]→φ then:

-   `□[φ]→φ` (assumption)
-   `□[L]→φ` (from 6 and assumption)
-   `L` (L ↔ □\[L\]→φ by definition, and we just deduced □\[L\]→φ)
-   `□[L]` (T can prove things it knows)
-   `φ`

We have now proved φ _in general_: such a T can prove anything. Notice what this means: any system of sufficient strength can derive a proof of any φ _from the mere fact that if provable then it is true._

(Fun fact: pick φ=⊥ to get a proof of the second incompleteness theorem. ¬□\[⊥\] means □\[⊥\]→⊥, so if you can prove ¬□\[⊥\] (that you don't prove a contradiction) then you prove ⊥ (a contradiction).)

Conclusion: A system cannot trust, in general, that □\[φ\] implies φ. It can't know that its proofs are valid.

This is going to make our lives difficult: our tiling agents will be generating situations where the parent agent verifies "my child will only execute actions that they've proven (in T) lead to good outcomes". By Löb's theorem, such agents, running on T, _cannot_ conclude "and so my child, also running on T, will only execute actions that lead to good outcomes" — because it cannot trust its own proof system.

# Finite Descent Problems ^finite-descent-problems

A system _can_ prove weaker systems consistent. For example, T+1 can prove T consistent, and T+2 can prove T+1 consistent, etc. You might think that we can work around the problem by having our initial system run on T+n for large n. But this fails.

First of all, if you pick a large finite n then your system has a finite "telomere", a trust-capacity that is running out. And even if you try to start with T+ω, it has to bequeath unto its child system a T+n where n is an ordinal less than ω. Though such an n may be arbitrarily large, it must be finite, and then we have the finite fuse again. In general, no matter how infinitely large an ordinal you start with, it will still suffer from a finite descent problem (because the ordinals are well-ordered).

And secondly, T+1 is far more powerful than T. Take, for example, the [hydra game](http://math.andrej.com/2008/02/02/the-hydra-game/). It turns out (spoiler alert) you can't lose: any strategy beats every hydra.

Now consider PA. Given an h denoting the height of the hydra, PA can prove that any strategy beats hydras of height h. But PA _cannot_ conclude that any strategy beats every hydra. Letting ψ(h) denote "hydras of height h can be killed by any strategy", it is the case that for all h, PA ⊢ ψ(h). But PA does NOT derive ∀h. ψ(h)! PA cannot rule out the possibility that there is _some_ height at which its proofs will fail: it only trusts proofs that it _witnesses_.

PA+1, on the other hand, has PA+1 ⊢ ∀h. ψ(h) because it knows that PA is consistent, and thus that there is no height at which PA's proofs start failing. Thus, in a very real sense, there are problems (like the hydra problem, or like checking whether a Goldstein sequence terminates) that can be solved in PA+1 but not PA.

In fact, an agent's strength is directly related to which ordinals it can well-order: the ability to well-order high ordinals directly translates into mathematical power. Child agents running on weaker mathematical systems correspond to a very real loss in capabilities.

Having each agent build a weaker child is untenable, and by Löb's theorem we can't have the child agent run on the same system as the parent (because the parent can't trust its own system). Yet we demand away to tile agents without having their trust drop below a certain baseline. Is this even possible? Experience with Gödelian problems may lead you to think that the answer is "No", but as we will see, we can gain a few technical victories.

# Failed Solutions ^failed-solutions

Here are a few ideas to get things rolling:

### Recursive Diving ^recursive-diving

Define Safe(x) to be (@x -> ∅ ∨ G): in other words, Safe(x) means "executing x leads to either no change, or the goal being achieved."

Instead of requiring the agent to know □\[Safe(x)\] → Safe(x), we instead define a proxy for safety. This proxy is ψ(x) ↔ Safe(x) ∨ □\[ψ(x)\]. Then the condition of action is ψ(x).

The idea is that instead of requiring the system to accept that a proof of safety makes things safe, we instead ask it to either know that an action is safe, or be able to prove ψ about the action (which means either we can prove the action safe or we can prove we can prove ψ about the action (which means either we can prove we can prove the action safe, or ...)). Naïvely, you might expect that the only way out of this recursive dive is for the system to accept Safe(x) at some depth of proof. But that's not what happens.

In fact, ψ(x) is accepted immediately, regardless of the safety of the action. ψ is in fact a Henkin sentence: It is of the form ψ(x) ↔ □\[ψ(x)\] (with a dangling ∨ Safe(x) that we can ignore). Henkin sentences are universally true. Our system can ignore the safety constraint, skip the recursive descent, and conclude any action is OK. This makes it… rather unsuited to the real world.

### Buck Tossing ^buck-tossing

Instead of requiring □T\[φ\] → φ, we construct a tower of theories. Each theory trusts the next theory, but not itself. So T0 has □T1\[φ\] → φ, and T1 has □T2\[φ\] → φ. This allows parents to trust their children without ever trusting themselves (and thus becoming inconsistent.)

Problem is, if T0 is as strong as PA then it can deduce that proofs in T0 are valid in T1: it just bumps all the appropriate 'n' up by 1. Then T0 deduces that □T0\[φ\] → □T1\[φ\], from which it deduces φ. Triumphant, T0 proudly concludes □T0\[φ\]→φ, and immediately bursts into inconsistent flames.

### Proof Stacking ^proof-stacking

It doesn't matter whether T trusts itself. WE trust T. If Safe(x), or T proves Safe(x), or T proves that T proves Safe(x), or if there is _any_ depth of proofiness such that Safe(x), then the agent may do x.

Let □^k\[x\] stand for "T proves that T proves that … (k times) … that Safe(x)". (Assume k nonzero throughout.) Because this stacking has a regular structure, there should be a compact formula expressing this. So what if we make T's criterion of action be (Safe(x) ∨ □^k\[x\])?

Then, when a child concludes (Safe(x) ∨ □^k\[x\]), the parent concludes that □\[Safe(x) ∨ □^k\[Safe(x)\]\].

Problem is, □\[Safe(x) ∨ □^k\[Safe(x)\]\] doesn't reduce to (Safe(x) ∨ □^j\[Safe(x)\]), no matter how much we want it to. This is because □^k\[φ\] is actually a formula like (∃ k. StackOProofs(k, φ)), and □\[∃ k. StackOProofs(k, x)\] does not reduce to (∃ j. StackOProofs(j, x)), precisely because T does not trust that □\[φ\]→φ. So this technique doesn't really dodge the Löbstacle at all.

---

Is it completely hopeless? No! Just mostly hopeless. We can, it turns out, achieve a few technical victories.

# Technically Solutions ^technically-solutions

### Infinite Descent ^infinite-descent

Idea 2 above (buck-tossing) is reparable. The idea, you remember, is that T0 trusts T1, which trusts T2, etc. The problem was that T0 could deduce that, by bumping all the n in a proof, things true in T0 were true in T1. It could then "lift" its proofs into T1, prove itself consistent, and become inconsistent.

This can be fixed, if we somehow find a way to allow Tn to trust Tn+1 without being able to trust that it can lift its own proofs upwards. For example, instead of having as an axiom of Tn that Tn+1\[φ\]→φ, we could guard the axiom by a formula ψ. Thus, the new axiom becomes ψ(n) → (Tn+1\[φ\] → φ).

Now, if only we could find a ψ such that ψ is true for all n, and T can prove ψ(n) for each individual n, but such that T cannot prove ∀n. ψ(n)…

And we can! We were just talking about such formulas earlier. We need a formula that T-0 can prove for every n, but that it can't prove it can prove for every in. (In other words, for all n we need T ⊢ ψ(n), but we also need that T can NOT derive ∀n. ψ(n).)

In order to do this, we're going to need a theory _more powerful_ than T: a theory Z such that T cannot prove Z consistent. (Why? We'll get to that later.) For concreteness, if T is PA then ZF is more powerful in the appropriate manner.

Now, here's an example guardian formula: ψ(n)≡¬ProofZ(n, \[⊥\]) or, in english, ψ(n)="n does not encode a proof of contradiction in Z".

For every n, T0 can prove ψ(n). But T0 cannot prove that ∀n. ψ(n). Thus, it can no longer "lift" its proofs into the higher system: "increasing all the n's" is no longer a safe operation. T0 does not expect ψ to hold forever.

We can prove this system consistent. I'll sketch the proof; see the paper for details. We'll construct a sound system T+ that trusts T and reasons about T0. We'll show that T+ does not prove T0 inconsistent, and that if T0 were consistent then T+ would know.

T+ is built from T, a new symbol "TRUE", and axioms stating both that T is consistent and TRUE is a truth predicate for T. We note that T+ is strong enough to reason about T0 and proofs in T0. T+ reasons as follows:

Suppose T0 is inconsistent. Then □T0\[⊥\]. Consider the proof. It has a bad line. The bad line can't come from the axioms of TRUE, nor from the use of T, as those are trusted. Therefore, it must come from the special axiom, and be of the form ψ(n) → (□Tn\[φ(x)\] → φ(x)). In order for this to be the point of failure, ψ(n) must be true, □Tn\[φ\] must be true, and φ must be false. Consider the Tn proof of φ. Recurse: its first bad line must also come from a ψ(n) axiom, and its first bad line must come from a ψ(n) axiom, and so on and so forth. Thus, ψ(n) must be true for all n. So, □T0\[⊥\]→(∀n. ψ(n)).

This reasoning shows that T+ knows that if T0 is inconsistent then ψ is true for all n. Furthermore, notice that if ψ is true for all n then Z is consistent.

If there were a proof of contradiction in T0, the proof could be fed to T+, and then T+ would be able to prove the consistency of Z.

We've established that T (and thus T+) cannot prove the consistency of Z. Therefore, T0 is consistent.

This is nice, but it's not without problems. For example, T0 ⊢ (∀n. ψ(n)) → ⊥: T0 knows that if ψ is true for all n, then it can bump its proofs upwards. It follows that T0 ⊢ ∃n. ¬ψ(n): T0 believes that some n encodes a proof of contradiction in Z. Concretely, when T=PA and Z=ZF, T thinks that ZF is inconsistent. This is… not the type of behavior that we strive for in real world agents, to say the least.

Also, this means that T0 has only nonstandard models: T0 is consistent, and thus has a model, but as we've seen, T0 only has models where T is consistent but ZF is inconsistent. This, too, is a hinderance.

Regardless, the paper has shown that you can tile agents without letting their trust fall below a certain minimum. (All of T0, T1, T2, ... trust T.) This system doesn't trust itself, and thinks ZF is inconsistent, but we've still shattered the Löbstacle. Via [technical tomfoolery](http://imgur.com/OldYeT6), we have a mathematical system that can trust a another system of the same power.

This is a cause for hope.

_Question: What if we use ψ(n)≡¬ProofT(n,¬□T\[⊥\]) (ie ψ(n) means "n does not encode a proof of T's consistency"). The existing proof of consistency fails because T+ proves T consistent, but can we prove T0's consistency by other means? The fact that T0 ⊢ ∃n. ¬ψ(n) in this case means that T0 believes T is consistent. This is far nicer than T believing Z to be inconsistent._ _I suspect that such a T0 can reason something like "If T is consistent then so am I", thus dooming itself, but I haven't had time to play with this yet._

_Update: This does fail. The actual proof path is T_ _⊢_ _□(__∀n. Tn_→_⊥)_→(_∀n. Tn_→_⊥), so by Löb's theorem T proves all such Tn inconsistent. In other words, if T could prove all Tn consistent then they would all know it, and would be inconsistent: and so, by Löb's theorem, they are._

### Parametric Polymorphism ^parametric-polymorphism

The trick that made the above approach work was that we gave the theory a trust condition that (from the perspective of the theory) "might run out". Only from outside the theory do we know that the trust will not run out.

The second approach — parametric polymorphism — makes that technique somewhat more explicit.

In parametric polymorphism, we require that the theory T under consideration can be modeled by the natural numbers. (This gives us some nice properties that we'll need to use for the consistency proof.)

We start by adding a new term 'k' to our logical language. This k, the "number of ineffable mystery", will be represented by a number (when N is the model), but T has no knowledge about k.

Remember that the goal is to have something like □\[φ\] → φ (though we can never achieve this). Instead, we add an axiom that (k > 0) → □Tk\[φ\] → φ\[k\\k-1\]. In other words, _so long as k is positive_ a proof in Tk of φ implies that φ is true after replacing all k by k-1.

T, in general, cannot prove that Tk\[φ\]→φ even for φ that do not mention k, becuase Tk doesn't know whether k is positive. However, it can prove that _when_ Tk is nonzero it can believe φ "at the next k-step". Proofs in Tk will need numerous guards concerning the positivity of Tk, but _in the positive branches_ it will be able to trust Tk proofs: and outside the system, we know that the positive branches will always be the ones taken.

Before we get excited, we have to check whether Tk is consistent. As a matter of fact, it is. We can show this by presenting a model of Tk: this we can do trivially. {N, k=0} (the naturals, with k modeled as 0) is trivially a model of Tk: N is a model of T, and when k=0 the new axiom schema is trivially true.

Models where k=0 are not exactly useful to us, though: in these models, the k=0 branches of the proofs are taken, and Tk never achieves self-trust. What we want is to show that there are models of Tk where k is arbitrarily large. We can prove this via induction.

We've already got a base case: {N, k=0} is a model of Tk. For the induction step, we need to show that if {N, k=n} is a model of Tk then {N, k=n+1} is a model of Tk. To show this, note:

1.  If {N, k=n+1} ⊧ □Tk\[φ\] then {N, k=n} ⊧ □Tk\[φ\]
2.  If {N, k=n} ⊧ □Tk\[φ\] then {N, k=n} ⊧ φ
3.  If {N, k=n} ⊧ φ then {N, k=n+1} ⊧ φ\[k\\k-1\]

(1) is true because □Tk has no access to k.

(2) is true because if □Tk\[φ\] is a proof _modeled_ _a standard model_ then φ is semantically derivable within Tk by a _standard_ (ie classical) proof. Whenever Γ → Δ via a classical proof, all models of Γ are also models of Δ. Since {N, k=n} is a model of Tk, it is also a model of all things provable in Tk via standard proof.

(3) is trivial by substitution.

We can extend these points to cover formulas free in one variable by noting that, because we are dealing with N as our model, every term x corresponds to a finite constant c.

Combining these three points we get that if {N, k=n+1} ⊧ □Tk\[φ\] then {N, k=n+1} ⊧ φ\[k\\k-1\], which completes the induction step.

We conclude that {N, k=n} is a model of Tk for any n.

We can use this to construct tiling agents. The proof is technical (there's a bit of finagling to do because when the child has proven an action safe for k steps, the parent concludes that it is safe for k-1 steps). The proof in the paper still has a number of typos. (See the end of the post.) I won't go over the proof in detail here. It suffices to say that when the child proves an action safe for k steps, the parent concludes that it's safe for at least k-1 steps and thus (conditional upon k being positive) A1 can construct A0. Outside the system, we know that k can be arbitrarily large, and so conclude that the system is safe for an arbitrary number of steps.

This system, like the last, would not be the best choice as a belief-system for a rational agent. It's not clear what k represents to the agent, nor what it would mean for a rational agent to "actually believe" Tk. As before, Tk is not presented as a realistic candidate for the mental system of a real agent. Rather, it is presented as yet another technical victory over the Löbstacle.

With that done, we can talk about self-modifying agents on a more general level, and will do so in the next few sections.

## Probabilistic Reflection ^probabilistic-reflection

The paper mentions the [Probabilistic Reflection](http://intelligence.org/wp-content/uploads/2013/03/Christiano-et-al-Naturalistic-reflection-early-draft.pdf) results, summarizes them, and notes that we don't yet have a formalism for agents using a probabilistic reflection principle. (We don't even yet know what knowledge of probabilistic reflection can appear inside a probabilistically reflective system).

A few days ago I did a that [write-up of that paper](https://www.lesswrong.com/lw/jbe/walkthrough_of_definability_of_truth_in), which may be helpful if you're looking for more walkthroughs such as this one.

# What Self-Modifying Agents Need ^what-self-modifying-agents-need

There are three principles that we really want our self-modifying agents to adhere to. I'll summarize these sections briefly, as they are not difficult to grasp. See the paper for more.

### The Vingean principle ^the-vingean-principle

Agents shouldn't have to predict precisely what their children do. If the parent knows precisely what the child will do — for example, by proving which action the child will take — then the child is hardly 'smarter' than the parent. In our logical systems, we follow the Vingean principle by requiring that the parent only discuss the child's actions within quantifiers. We can have a set representing the child-actions, and we can quantify over that set, but we can't have particular child-actions known ahead of time.

The parent may verify properties about all actions, e.g. by looking at the action system and verifying that the motors only activate when presented with a valid proof. The parent may not e.g. simulate the child's exact action.

### The tiling principle ^the-tiling-principle

Agents should be able to approve the construction of agents similar to themselves. This is what we've been searching for formalisms to allow in the above sections. This portion of the paper also discusses a formalism where the agent is divided into an untrusted proof suggestion component Σ and a trusted proof verification component Δ. This has some nice properties (especially in monotonic logic, where things that Σ knows but isn't telling Δ can't cause Δ to allow something it shouldn't), but would quickly break down outside the realm of logic.

### The naturalistic principle ^the-naturalistic-principle

Agents should think of themselves as part of the world. There shouldn't be a Cartesian boundary between "world-stuff" and "mind-stuff". Otherwise, you have to deal with weird boundary problems (attaching a new CPU requires things to cross the world/mind boundary).

Furthermore, having different rules for internal actions and external actions is not particularly safe. For example, if certain internal modifications are prohibited an agent could build an external thing that happens to apply the desired internal changes.

But _if you do_ allow a cartesian boundary then the Löbstacle is easy to avoid. You simply set as your criterion of action to be

ψ(action) =

(externalOK(action) → (@action → G)) ∧

(internalOk(action) → (@action → (∀ action' in Acts. @action' → □\[ψ(action')\])))

Translation: "The condition for action is this: \[when action is externalOK, if we execute it then it achieves the goal\] and \[when action is internalOk, if we execute it then it leaves us in a state where we only take actions that meet this condition\]."

_Note: There is a bit of ambiguity here. I believe that 'Acts' is meant to refer to the new action-set available after taking the internal action._

This is similar to our first failed solution, except that the Cartesian boundary allows ψ to avoid becoming a Henkin sentence.

_Note: On gut instinct, I'd consider exploring ψ(x) = @x → (G ∨ (∀y ∈ ActsX. @y → □\[ψ(y)\])), which is a version of the above that does not have a Cartesian boundary and does not immediately succumb to the Henkin-sentence problem._

# Sensors ^sensors

Then we try to add sensors, and everything blows up.

That's not exactly the case, but adding sensors and unknown variables certainly doesn't make the formalism any prettier.

Section six is long and somewhat involved, though it's saying something essentially simple. I'll summarize:

We want to allow our agents to have sensors, and indeed construct new sensors. We'll say things like

A0 ⊩ @sl ⇒ @Sl

to mean "A0 believes @sl only when sensor S takes on the state @Sl".

This causes a trust problem. We still want A1 to trust A0, despite the fact that A0 will have access to sensor data that A1 knows not. We can patch our trust framework by changing A0's criterion of action to be

@bi ⇒ A0 ⊩ (@sl ∧ @bi) → (∅ ∨ G)

(If bi is taken then A0 believes that, with the sensors in state sl, taking the action bi leads to either ∅ or G). Then, if this is known for every possible combination of sensor states, A1 can retain trust in A0.

This is messy, though. Additional sensors lead to exponentially more computing power required (on A1's part) to trust A0. This seems pathological. What we _want_ is for A1 to reason that, since it can verify that A0 ⊩ @sl only when @Sl (i.e. A1 trusts that the sensors take on state sl only when the world is actually in state Sl), anything that A0 does based on the sensor data is trusted.

And we can get this property — or something like it. However, this means that A1 must be able to express things like "A0's reasoning is such that, if we add only "true" sensor-data, it does not disturb our trust in A0." So A1 needs to not only trust A0, but must also trust A0 after A0 has had new "true axioms" added in the form of (trusted) sensor data.

Formalizing this requires full-on set theory, which can formalize things like "In all models X, all logical tautologies hold".

We then create a language in which there is a special set τ (the "territory") encoding a model of the environment. We then express A1's trust as follows:

A1 ⊩ @A0 → ∀\[φ\]. (τ ⊧τ \[A0 ⊩ "φ"\]) → (τ ⊧τ \[φ\])

Translation: A1 believes that, if it constructs A0, then for all quoted sentences _about the territory_, if it is true _in the territory_ that A0 believes some A0-encoding of φ, then it is actually true in the territory that φ.

Notice the two levels of quoting. A1 believes that A0's beliefs ("φ") correspond to statements true in the territory (\[φ\]).

This loosely represents how a programmer might reason about a program: A programmer (A1), who thinks that there is an object (φ) in the environment, will have an internal representation (\[φ\]) of the object. They will also know that the program (A2) has an object corresponding to Fred ("φ"), and they will retain a mental map between their representation of the object (\[φ\]) and their representation of the program's representation of the object (\["φ"\]).

The point is that we deploy set theory to represent this sort of logic. This logic, however, allows us to reason about sensors thusly (replacing ⊧τ with ⊧):

A1 ⊩ @A0 → ∀\[sl\]. (τ ⊧ \[A0 ⊩ "@sl"\]) → (τ ⊧ \[@Sl\])

Which basically says "A0 only believes @sl when, in reality, the sensor actually is in state l."

This is what we wanted, but it does not come cheap: We had to deploy full ZF in order to allow A1 to reason as we wanted. Worse, A2 (the parent of A1) must reason in ZF+1 in order to trust A1 (because it must believe that there is some model of ZF: otherwise A1 is meaningless). A3 must reason is ZF+2, and so on.

It is noted that this can probably be addressed via parametric polymorphism (ie A2 uses ZFk, and also trusts A1 to use ZFk), though no proof has been written out yet. A simplification of the above mechanism (without resorting to set theory, or at the least using a weaker set theory) is desired.

# Probability and Expected Utility ^probability-and-expected-utility

Adding expected utility satisfaction is somewhat difficult.

Probabilistic reasoning is non-monotonic. This leads to difficulties. For example, if you have an untrusted proof-suggester Σ and a proof-verifier Δ, then so long as Δ works you can't go wrong — in logic. At worst, Σ withholds a good proof and the system does nothing. But with probabilistic reasoning, Σ can withhold information from Δ with catastrophic results.

For example, imagine that the condition of action is E\[U\] ≥ $20, where E\[U\] is the expected utility. If we have a fair coin and a bet with payout of $50 on H and $10 on T, then the agent will take the bet. But if we later learn that the coin landed T, we should no longer take the bet: new information can invalidate actions that otherwise would have been taken. If the suggestion-device is untrusted, this can be particularly dangerous, because Σ can withhold information maliciously.

We can hack our way around this problem by requiring that every probabilistic variable be observed by A0 before it may choose an action. A1, knowing this, can proceed to trust A0. A formalization of this process is given on pages 35-36. The result is a technical success — the parent can still trust the child so long as the child observes all data before acting — but this formalism falls short on many counts.

For example, the given formalism cannot assign prior probabilities to variables. (In the given formalism, probabilistic variables are left unassigned until the observations comes in. If the system tried to assign ν=0.7 as a prior probability and later assigned ν=1 according to sensor data, the system would arrive at the contradictory 0.7=1.)

This is obviously a very rudimentary formalization of utility satisfaction, and there is much work to be done.

# Utility Management ^utility-management

The above section dealt with utility _satisfaction_, not utility maximization. This was intentional, as perfect utility maximization is impossible in all but the most trivial of situations.

Utility satisfaction, however, is far from ideal. To take an example from the paper, consider an agent built to satisfy at least E\[U\]=2\*10^15. If it finds an action that guarantees E\[U\]=10^16, then the agent may decide to randomize between a 30% probability of taking the 10^16, a 60% probability of doing nothing, and a 10% probability of burning 10^16 utils. This is… not ideal, to say the least.

> You get what you pay for, no more than you asked for, and exactly what you proved.

An alternative means of utility management is a "meliorizing" criteria of action, wherein an agent picks an action and then decides whether to swap its current action for another as opportunities arise. This strategy is not without its flaws. To lift another example from the paper, imagine an agent built to save humanity from a deadly asteroid. Imagine it starts with the default action of "do nothing". If the first action it comes across is "immediately take an action which will save 1000 humans, then shut down", it will take that action and then shut down — forgoing the opportunity to save billions of human lives. Also not ideal.

That said, meliorization at least shows a bit of promise, whereas satisficing is untenable and maximization is unrealistic. It's worth noting, though, that we don't even understand — not even at the highest possible level — how a probabilistic rational agent should go about pursuing its goals. This is the paper's ending note:

> The problem is very wide open indeed.

# Edits ^edits

### Typos ^typos

I'm pretty confident about most of these, but some may be due to a misunderstanding, and are suffixed with (?).

-   p10. ψ ↔ φ(x) ∨ □τ\[ψ(x)\], this should be ψ(x) ↔ … (?)
-   p17. (4.13) The leading A\_t^0 has a stray 't' after it.
-   p17. (4.14) is missing a b\_{i,u}\\bar inside the □\_0, before the "→ ∀υ".
-   p17. (4.14) is missing a b\_{i,t}\\bar before the "→ ∀ν".
-   p18. (4.23) there is a K that should be a κ.
-   p18. (4.24) there is an extraneous (A\_t^0 →) after the ⊩
-   p18. (4.24) there should be a -1 after ∀ν≤υ+κ. (Alternatively, change the ≤ to <) (?)
-   p18. (4.25) there is an extraneous (A\_t^0 →) after the ⊩
-   p18. (4.25) there should be a -1 after ∀υ≤t+κ. (Alternatively, change the ≤ to <) (?)
-   p18. (4.26) there should be a -1 after ∀υ≤t+κ. (Alternatively, change the ≤ to <) (?)
-   p28. "If we were in the shoes of A1 building A1 …" should be "… building A0 …".
-   p29. "… it should not disturb our trust in A1." should be "… in A0."
-   p31. (6.9) (τ ⊧ @A0) should be just @A0 (?)

### Nitpicks ^nitpicks

-   p10. "Either x implies (∅ ∨ G), or …" should read "Either the execution of x implies (∅ or G), or …"
-   p13. You use ≡ to introduce ψ and ≜ to introduce T-n. Later (p27) you use = to introduce a different ψ. Are these differences intentional?
-   p19. Using P() to denote the function P seems somewhat strange. The probabilistic reflection paper simply calls it P. Other texts I've read use the style P(—). I haven't seen the style P() before. (This may just be inexperience.)
-   In infinite descent, why do the theories walk downwards? Why not use T0, T1, T2, …? Walking downwards causes a bit of awkward syntax (T-(n+1)) that seems unnecessary.

And while I'm on the subject, it felt foreign that A0 is the _youngest_ agent. I would expect A0 to be the oldest agent. In one sense, I appreciated that A0 was the youngling: it lends itself well to the idea that we have this gigantic tower of agents building agents building agents, and then at the very end of the tower we have the final agent that affects the environment (which is why A0 is special). However, one of the nice things about this formalism is that it doesn't really treat environment-actions differently from agent-creating-actions, so we don't _need_ this distinction. I found it counter-intuitive to consider the "end" of the tiling schema, preferring to think of it from the other direction: we start with an agent running on trusted math (agent zero) and let it tile indefinitely.

All in all, it's not a particularly bad choice, it just felt unnatural to me.

### Structure ^structure

Section 5.2 seems like a non-sequitur. 5.1 and 5.3 discuss principles that agents should have. By contrast, 5.2 mentions tiling and gives examples of how trust can be decomposed. It was weird to be introduced to tiling after spending section 4 proving that tiling is possible while preserving trust. Also, the discussion about decomposition of trust didn't feel at home in a section detailing the tiling principle.

I'd recommend moving section 5 up to before section 3 or possibly before section 2. This would give us a better idea of what we're looking for in self-modifying agents before we are introduced to the obstacles. I'd also suggest breaking "decomposition of trust" out of the "tiling principle" section. 5.2 feels like it's trying to introduce one concept while explaining another.

### Confusions ^confusions

-   p17. Syntax question: Why are (4.15) and (4.17) indented more than everything else?
-   p27. I'm confused about the "split decision criterion". Acts denotes the set of actions that are available after the execution of the (internalOk) action act, yes?
