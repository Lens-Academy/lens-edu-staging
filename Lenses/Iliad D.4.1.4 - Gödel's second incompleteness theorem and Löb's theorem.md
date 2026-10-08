---
id: 'af8da75e-ea0d-43ca-a226-8c72a3c029bd'
title: "D.4.1.4 Gödel's second incompleteness theorem and Löb's theorem"
tldr: "Exercises on formal systems and programs: Gödel's second incompleteness theorem through a self-referencing program, and Löb's theorem with its application to FairBot cooperation."
summary_for_tutor: "Start of Section 3 'Exercises' of Iliad worksheet D.4.1 Agent Foundations: setup (formal system L, consistency, ProofSeeker, the provability predicate □P, L ⊢ P versus L ⊢ □P), then Exercise 3.1 (a-c, with hints and a remark on tiling agents and the Löbian obstacle) and Exercise 3.2 (a-e: necessitation, distribution, the Löb sentence λ ↔ (□λ → C), the proof of Löb's theorem, and FairBot against itself), with collapsed solutions. Keep the notation □, ⊢, ⊥, G := ¬Halts(Z(Z)). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/agent-foundations/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 3. Exercises

> *The following are exercises on agent foundations. Each problem is broken into a sequence of lemmas leading to a main theorem. **For each subquestion, try to prove the stated lemma before reading on.** If you get stuck, you may treat the lemma as given and proceed to the next part.*
>
>  *Before diving into a formal derivation, try to build an intuition for **why** the statement should be true. Even if you don't complete the proof, having a clear intuitive picture of what's going on is more valuable than a mechanical derivation you don't understand. Don't worry if some of the terminology is unfamiliar — the exercises are designed to be self-contained, and it should be possible to follow the questions from context.*

**Formal systems and programs.** A *formal system* is a precise set of rules for deriving mathematical statements from axioms. Fix a formal system $$L$$ that is powerful enough to reason about programs (for instance, it can express statements about arithmetic, and any program can be encoded as a mathematical object that $$L$$ can talk about). We write $$L \vdash \varphi$$ to mean that the statement $$\varphi$$ is *provable* in $$L$$, i.e. there exists a finite sequence of steps, each justified by the rules of $$L$$, that derives $$\varphi$$.

We say $$L$$ is *consistent* if it never proves a contradiction. We write $$\bot$$ for a fixed contradictory statement (such as $$0 = 1$$), so consistency means $$L \nvdash \bot$$. We assume throughout that $$L$$ is consistent.

**Programs.** By a *program* we mean a mechanical procedure that follows a fixed list of instructions. A program may *halt* (finish and produce an output) or *run forever* (keep executing without ever stopping). Since $$L$$ can reason about programs, it can express the statement "program $$M$$ halts", which we write as $$\mathsf{Halts}(M)$$.

**The bridge between $$L$$ and programs.** Formal systems and programs are intimately connected, and the key to these exercises is switching back and forth between the two perspectives:

- **From programs to $$L$$** (concrete outputs become proofs)**.** If a program concretely produces an output (e.g. it halts after some number of steps, or it finds a string with a certain property), then $$L$$ can verify this by tracing through the execution step by step. In particular: if a program actually halts, then $$L$$ can prove that it halts.
- **From $$L$$ to programs** (proofs can be found by search)**.** Proofs in $$L$$ are finite strings that can be checked mechanically. So for any statement $$P$$, we can write a program that searches through all possible strings, checks whether each one is a valid $$L$$-proof of $$P$$, and halts if it finds one:

$$
\texttt{ProofSeeker}(P) \;:=\; \text{``try every string; halt iff one is a valid $L$-proof of $P$.''}
$$

This program halts if and only if $$P$$ is provable in $$L$$.

Whenever you derive a fact about $$L$$ (e.g. that some statement is or isn't provable), ask what that implies for the corresponding proof-search program, and vice versa.

**The provability predicate $$\Box P$$.** We write $$\Box P$$ for the statement, *expressed within $$L$$ itself*, that "$$P$$ is provable in $$L$$." This is a genuine mathematical statement that $$L$$ can reason about, because it is equivalent to the claim that $$\texttt{ProofSeeker}(P)$$ halts, and $$L$$ can talk about programs.

The crucial distinction is between $$L \vdash P$$ and $$L \vdash \Box P$$:

- $$L \vdash P$$ means that $$P$$ is provable: there *exists* a concrete proof of $$P$$ in $$L$$. This is a fact about $$L$$ that we observe from the outside.
- $$L \vdash \Box P$$ means that $$L$$ has proved a statement *about itself*: namely, that a proof of $$P$$ exists (equivalently, that $$\texttt{ProofSeeker}(P)$$ halts). But this is a claim $$L$$ is making about the $$\texttt{ProofSeeker}(P)$$ program, not a direct certificate for $$P$$.

**Intuition.** To see why $$L \vdash P$$ and $$L \vdash \Box P$$ are conceptually distinct, consider the two different ways $$L$$ might prove that $$\texttt{ProofSeeker}(P)$$ halts. The first is to actually trace through its execution: if it halts after, say, a million steps, $$L$$ can verify this step by step, and the proof that $$\texttt{ProofSeeker}(P)$$ found along the way is itself a direct $$L$$-proof of $$P$$. In this case, $$L \vdash \Box P$$ and $$L \vdash P$$ seems to come hand in hand. But there is a second way: $$L$$ might reason *abstractly* about the program's behaviour without ever simulating it. (This is analogous to how you might argue that a sorting algorithm must eventually finish without tracing through every swap it makes.) Such a proof establishes that $$\texttt{ProofSeeker}(P)$$ halts — and therefore that *some* proof of $$P$$ exists — but the proof itself is about the *program*, not about $$P$$. It need not contain, or even hint at, what the actual proof of $$P$$ looks like. This is the gap that $$L$$ cannot close in general: knowing abstractly that a proof is "out there" is not the same as having the proof in hand.

**What "provable in $$L$$" means (and what it does not).** It is important to distinguish between being *convinced* that something is true and *proving it in $$L$$*. When we say "$$L$$ can carry out this argument" or "$$L$$ proves $$P$$," we do not mean that a reasonable person reading the argument would find it convincing. We mean something much more specific: that there exists a sequence of formulas, each of which is either an axiom of $$L$$ or follows from earlier formulas by one of $$L$$'s explicitly listed inference rules, and whose last line is $$P$$. The formal system $$L$$ is a *machine*: it has no understanding, no intuition, and no ability to say "well, this obviously follows." Every single step must be justified by a specific rule.

From the outside, we can see that if $$\texttt{ProofSeeker}(P)$$ halts then a proof of $$P$$ exists, so $$P$$ is provable. But can $$L$$ carry out this reasoning internally, always concluding $$P$$ from $$\Box P$$? Lob's theorem (Exercise 3.2) shows that the answer is no: any consistent $$L$$ that derives $$P$$ from $$\Box P$$ for all $$P$$ is in fact inconsistent.

::::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (Gödel's second incompleteness theorem).** **Key fact.** If a program $$M$$ actually halts (say, after 17 steps), then $$L$$ can verify this by checking the execution step by step, so $$L \vdash \mathsf{Halts}(M)$$. However, if $$M$$ runs forever, $$L$$ cannot necessarily prove $$\neg\mathsf{Halts}(M)$$. (Informally: it is easy to certify that something stops, because you just exhibit the stopping point; but certifying that something runs *forever* is much harder, because you cannot check infinitely many steps.)

In fact, no consistent formal system can correctly settle the question "does $$M$$ halt?" for *every* program $$M$$. To see why: if $$L$$ could do this, we could write a program that, given any $$M$$, searches for an $$L$$-proof of either $$\mathsf{Halts}(M)$$ or $$\neg\mathsf{Halts}(M)$$. Since $$L$$ is assumed to settle every case, this search would always find a proof and halt, giving us a mechanical procedure that decides whether any program halts. But such a procedure cannot exist (this is the *undecidability of the halting problem*, a fundamental result in computer science that we take as given here).

**A self-referencing program.** It is possible to write programs that refer to their own source code. (As a simple example, a program can carry its own source code as a string and then operate on it.) Using this idea, define the following program:

$$
Z(A) \;:=\; \text{``search for an $L$-proof of $\neg\mathsf{Halts}(A(A))$; halt if one is found.''}
$$

Here $$A(A)$$ means "run program $$A$$ with its own source code as input." So $$Z(A)$$ searches for a proof that the program $$A$$-run-on-itself runs forever.

Now consider feeding $$Z$$ its own source code. The program $$Z(Z)$$ searches for an $$L$$-proof that $$Z(Z)$$ runs forever. Define the statement:

$$
G \;:=\; \neg\mathsf{Halts}(Z(Z)).
$$

In words: $$G$$ says "$$Z(Z)$$ runs forever." Notice the self-referential structure: $$Z(Z)$$ halts if and only if it finds an $$L$$-proof of $$G$$ (i.e. a proof that $$Z(Z)$$ runs forever).

**(a)** Show that $$G$$ is true, assuming $$L$$ is consistent.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Consider two cases. Either $$Z(Z)$$ halts or it doesn't. In each case, use the bridge between programs and $$L$$ (if a program halts, $$L$$ can prove it; if $$L$$ proves something, the corresponding proof-search program finds that proof and halts) to derive what follows. One of the two cases leads to a contradiction with the consistency of $$L$$.

:::

**(b)** Show that if $$L$$ can prove its own consistency (i.e. $$L \vdash \neg\Box\bot$$), then $$L$$ is in fact inconsistent.

:::callout {title="Hint" tone="neutral" collapse="closed"}

In Exercise 3.1(a), you argued from outside $$L$$ that $$G$$ is true, and the argument used only one assumption about $$L$$: that $$L$$ is consistent. If $$L$$ can prove its own consistency, then every step of your outside argument can be carried out **inside** $$L$$ as a formal derivation. What would $$L$$ then be able to prove? And what would the corresponding program do?

:::

**(c)** Suppose $$L$$ can vouch for all of its own proofs, meaning $$L \vdash \Box P \to P$$ for every statement $$P$$. (Read this as: "whenever $$L$$ can prove $$P$$, then $$P$$ is actually true," and $$L$$ itself asserts this.) Show that $$L$$ is inconsistent, in two steps:

**(i)** First, show that $$L$$ proves it never proves anything false. That is: for any $$P$$ with $$L \vdash \neg P$$, show that $$L \vdash \neg\Box P$$.
:::callout {title="Hint" tone="neutral" collapse="closed"}

The statement "if $$A$$ then $$B$$" is logically equivalent to "if not $$B$$ then not $$A$$". Apply this to $$\Box P \to P$$.

:::

**(ii)** Apply (i) with $$P = \bot$$, using the fact that $$\neg\bot$$ ("a contradiction is false") is a tautology. Conclude that $$L \vdash \neg\Box\bot$$, and use Exercise 3.1(b) to finish.

:::callout {title="Note" tone="blue"}

**Remark (Self-trust, tiling agents, and the Löbian obstacle).** Any sufficiently advanced AI may eventually be able to modify its own code or build a successor system more capable than itself. But this raises a subtle problem. If the successor is genuinely smarter, the original agent *cannot* predict exactly what it will do — just as the programmers of a chess engine can reason that their program is "trying to win" without knowing its exact moves. So the original agent cannot verify its successor's safety by simulating it move by move. Instead, it must reason *abstractly* about the successor's design: "whatever my successor does, it will only take actions that it has proved lead to good outcomes."

This reasoning strategy is called *tiling*: the parent agent $$A_{1}$$ builds a child agent $$A_{0}$$, and wants to conclude not merely that $$A_{0}$$ will only take actions that $$A_{0}$$ has *proved to be safe*, but that those actions *actually are* safe. After all, $$A_{1}$$ can verify from $$A_{0}$$'s source code that $$A_{0}$$ says "only take action $$x$$ if I can prove that $$x$$ leads to good outcomes." But this only tells $$A_{1}$$ that $$A_{0}$$ acts on what $$A_{0}$$'s proof system certifies — it does not yet tell $$A_{1}$$ that what $$A_{0}$$'s proof system certifies is actually *true*. To close this gap, $$A_{1}$$ needs to be able to prove, within its own reasoning, that $$A_{0}$$'s proof system is *sound*: whenever $$A_{0}$$'s system proves $$P$$, then $$P$$ is actually true. When both agents use the same formal system $$L$$, this amounts to $$L \vdash \Box P \to P$$ for all $$P$$.

Exercise 3.1(c) shows this is impossible: any consistent system that asserts $$\Box P \to P$$ for all $$P$$ is already inconsistent. A consistent system cannot vouch for its own proofs in the abstract — it can only trust a proof once it has *witnessed* it directly. This is the **Lobian obstacle**: the barrier created by Lob's theorem to self-trusting formal reasoning.

One might hope to work around this by having the parent use a *stronger* proof system than the child: a stronger system *can* trust a weaker one's proofs. But this means each successive agent in a chain of self-improvements must use a strictly weaker proof system than its predecessor, resulting in a "telomere" of logical strength that shortens with each generation. Eventually the chain runs out of trust. The *tiling agents* research programme studies how (and whether) this obstacle can be overcome, seeking agent architectures that can undergo indefinite self-improvement without their reasoning guarantees degrading at each step.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Recall $$Z(A)$$ searches for an $$L$$-proof of $$\neg{\mathsf{Halts}}(A(A))$$ and halts if it finds one, and

$$
G \;:=\; \neg{\mathsf{Halts}}(Z(Z)).
$$

By construction $$Z(Z)$$ searches for an $$L$$-proof of $$G$$, so

$$
Z(Z)\text{ halts}\iff L\vdash G. \tag{$\star$}
$$

**(a)** $$G$$ is true (assuming $$L$$ consistent).

*Solution.*  Two cases.

- *$$Z(Z)$$ halts.* By ($$\star $$), $$L\vdash G$$, i.e. $$L\vdash\neg{\mathsf{Halts}}(Z(Z))$$. But $$Z(Z)$$ actually halts, so by the bridge $$L\vdash{\mathsf{Halts}}(Z(Z))$$. Then $$L$$ proves both $${\mathsf{Halts}}(Z(Z))$$ and its negation, contradicting consistency.
- *$$Z(Z)$$ runs forever.* Then $$\neg{\mathsf{Halts}}(Z(Z))$$, i.e. $$G$$, is true.

Consistency rules out the first case, so $$Z(Z)$$ runs forever and $$G$$ is true. $$\square$$

**(b)** If $$L\vdash\neg\Box K$$ (i.e. $$L$$ proves its own consistency) then $$L$$ is inconsistent.

*Solution.*  The argument of Exercise 3.1(a) used only the consistency of $$L$$, and each step is a finite manipulation of programs and proofs that $$L$$ can formalize. Reading it inside $$L$$: "$$Z(Z)$$ halts" yields $$\Box G$$ (by construction) and $$\Box{\mathsf{Halts}}(Z(Z))$$ (the bridge), hence $$\Box K$$; contrapositively $$L\vdash \neg\Box K \to G$$. If $$L\vdash\neg\Box K$$, modus ponens gives

$$
L\vdash G,\qquad\text{i.e.}\qquad L\vdash\neg{\mathsf{Halts}}(Z(Z)).
$$

But $$L\vdash G$$ means $$Z(Z)$$'s search finds a proof of $$G$$, so $$Z(Z)$$ halts; by the bridge $$L\vdash{\mathsf{Halts}}(Z(Z))$$. Now $$L$$ proves both $${\mathsf{Halts}}(Z(Z))$$ and $$\neg{\mathsf{Halts}}(Z(Z))$$, so $$L$$ is inconsistent. $$\square$$

**(c)** If $$L\vdash \Box P\to P$$ for every $$P$$, then $$L$$ is inconsistent.

*Solution.*  *(i)* Fix $$P$$ with $$L\vdash\neg P$$. The contrapositive of $$\Box P\to P$$ is $$\neg P\to\neg\Box P$$, so from $$L\vdash\Box P\to P$$ we get $$L\vdash\neg P\to\neg\Box P$$. With $$L\vdash\neg P$$, modus ponens gives $$L\vdash\neg\Box P$$.

*(ii)* Take $$P=K$$. Since $$\neg K$$ is a tautology, $$L\vdash\neg K$$, so by (i) $$L\vdash\neg\Box K$$. Thus $$L$$ proves its own consistency, and Exercise 3.1(b) makes $$L$$ inconsistent. $$\square$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 3.2 (Löb's theorem).** Lob's theorem says: if $$L \vdash \Box C \to C$$ (i.e. $$L$$ can prove "if $$C$$ is provable then $$C$$ is true"), then $$L \vdash C$$ (i.e. $$C$$ is already provable in $$L$$). In other words, the only statements for which $$L$$ can close the gap between "provably provable" and "provable" are the ones that were already provable to begin with.

The proof uses three properties of the provability predicate $$\Box$$. We state them here together with informal explanations of what they say about the proof-search program $$\texttt{ProofSeeker}$$.

| **(N)** | *Necessitation.* | If $$L \vdash \varphi$$ then $$L \vdash \Box\varphi$$. |
| --- | --- | --- |
| **(K)** | *Distribution.* | $$L \vdash \Box(\varphi \to \psi) \to (\Box\varphi \to \Box\psi)$$. |
| **(4)** | *Lob condition.* | $$L \vdash \Box\varphi \to \Box\Box\varphi$$. |

**(a)** **Understanding Necessitation.** Necessitation says: if $$\varphi$$ is provable in $$L$$, then $$L$$ can prove that $$\varphi$$ is provable. Explain why this is true from the perspective of $$\texttt{ProofSeeker}$$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

If a proof of $$\varphi$$ exists, then $$\texttt{ProofSeeker}(\varphi)$$ will find it and halt.

:::

**(b)** **Understanding Distribution.** It is helpful to think of a proof of $$\varphi \to \psi$$ by analogy with a *function*: given any proof of $$\varphi$$ as input, one can mechanically produce a proof of $$\psi$$ as output (by writing down the proof of $$\varphi$$, attaching the proof of $$\varphi \to \psi$$, and applying the logical rule that from $$\varphi$$ and $$\varphi \to \psi$$ one may conclude $$\psi$$).

With this analogy, $$\Box(\varphi \to \psi)$$ says that $$L$$ has proved such a "proof-transforming function" exists. Distribution then says: if $$L$$ knows that a function from $$\varphi$$-proofs to $$\psi$$-proofs exists, and $$L$$ knows that a $$\varphi$$-proof exists, then $$L$$ can conclude that a $$\psi$$-proof exists.

Explain why Distribution is true from the perspective of $$\texttt{ProofSeeker}$$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

If both $$\texttt{ProofSeeker}(\varphi \to \psi)$$ and $$\texttt{ProofSeeker}(\varphi)$$ halt, what can you do with their outputs? How can $$L$$ deduce that $$\texttt{ProofSeeker}(\psi)$$ halts?

:::

**(c)** We now prove Lob's theorem. The key ingredient is a self-referential sentence constructed using the same idea as in Exercise 3.1 (a sentence that talks about its own provability). Specifically, there exists a sentence $$\lambda$$ such that

$$
L \vdash \lambda \;\leftrightarrow\; (\Box\lambda \to C).
$$

In words: $$\lambda$$ says "if I am provable, then $$C$$ is true." (The existence of such a sentence is guaranteed by the same self-referential construction used to build $$G$$ in Exercise 3.1; we take it as given here.)

Show that $$L \vdash \Box\lambda \to \Box C$$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

The Lob sentence says $$L \vdash \lambda \to (\Box\lambda \to C)$$. Apply Necessitation to get this fact inside a $$\Box$$, then use Distribution twice (once to "unwrap" the outer implication, once to handle $$\Box\lambda \to C$$ inside). Use the Lob condition to handle the resulting $$\Box\Box\lambda$$.

:::

**(d)** Now assume $$L \vdash \Box C \to C$$. Using Exercise 3.2(c) and the Lob sentence, derive $$L \vdash C$$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

From Exercise 3.2(c), you have $$L \vdash \Box\lambda \to \Box C$$. Chain this with the assumption $$L \vdash \Box C \to C$$ to get $$L \vdash \Box\lambda \to C$$. Now compare this with what $$\lambda$$ says about itself.

:::

:::callout {title="Note" tone="blue"}

**Remark (The Santa Claus paradox and what Löb adds beyond Gödel).** The Lobian sentence $$\lambda \leftrightarrow (\Box\lambda \to C)$$ is a formal analogue of the *Santa Claus sentence* (also known as Curry's paradox). Consider the sentence $$S$$: "If this sentence is true, then Santa Claus exists." Let us try to determine whether $$S$$ is true or false.

Well, $$S$$ is an "if ... then ..." statement, so to check whether it is true, let us assume the "if" part and see whether the "then" part follows. So assume $$S$$ is true. Since $$S$$ says "if $$S$$ is true then Santa Claus exists," and we are assuming $$S$$ is true, it follows that Santa Claus exists. We have therefore shown: if $$S$$ is true, then Santa Claus exists. But that is exactly what $$S$$ says! So $$S$$ is true. And since $$S$$ is true and $$S$$ implies Santa Claus exists, Santa Claus exists. Since nothing about this argument was specific to Santa Claus, the same reasoning "proves" any statement whatsoever.

The reason $$L$$ does not fall prey to this paradox is that $$L$$ cannot form a sentence that refers to its own *truth*. (A fundamental result called Tarski's theorem shows that no sufficiently powerful formal system can define a truth predicate for itself.) What $$L$$ *can* do is refer to its own *provability*: the predicate $$\Box\varphi$$ is a legitimate statement within $$L$$. The Lobian sentence $$\lambda$$ therefore substitutes "provable" for "true," asserting "if I am *provable*, then $$C$$." The proof of Lob's theorem shows that this substitution is enough to force $$L \vdash C$$ — but only when $$\Box C \to C$$ is already assumed, not unconditionally.

This mirrors a pattern: replacing "true" with "provable" transforms semantic paradoxes into precise theorems. The liar's paradox ("this sentence is false") becomes Godel's sentence ("this sentence is not provable"), yielding the incompleteness theorems. The Santa Claus paradox ("if this sentence is true, then $$C$$") becomes the Lobian sentence ("if this sentence is provable, then $$C$$"), yielding Lob's theorem.

**What Lob adds beyond Godel.** Godel's second incompleteness theorem (Exercise 3.1) says that $$L$$ cannot prove its own consistency. This is already a serious obstacle, but one might hope that consistency is a special case — perhaps $$L$$ can still trust its proofs in less sweeping ways. Lob's theorem crushes this hope completely. It says that for *any* statement $$C$$, if $$L$$ can prove "my provability of $$C$$ implies $$C$$ is true" (i.e. $$L \vdash \Box C \to C$$), then $$C$$ was already provable. There are *no* statements, not for which $$L$$ can assert "well, if I *could* prove this, it would be true" without already being able to prove them. $$L$$ does not trust its own proofs until it has witnessed them directly.

This is what makes Lob's theorem, rather than Godel's, the fundamental obstacle for tiling agents. Recall the setup from Exercise 3.1: a parent agent $$A_{1}$$ builds a child $$A_{0}$$ that only takes actions it can prove to be safe. For $$A_{1}$$ to trust $$A_{0}$$, it needs to know that $$A_{0}$$'s proofs track reality — that is, $$A_{1}$$ needs $$\Box P \to P$$ for the statements $$P$$ that $$A_{0}$$ might act on. Godel tells us $$A_{1}$$ cannot prove $$A_{0}$$'s system is *consistent*. But Lob tells us something far stronger: $$A_{1}$$ cannot even trust $$A_{0}$$'s system on a *case-by-case* basis. For any individual statement $$C$$, the only way $$L$$ can derive "if my proof system proves $$C$$, then $$C$$ is really true" is if $$C$$ was already provable — in which case the trust was never needed in the first place.

:::

**(e)** In a one-shot Prisoner's Dilemma, two players each choose to either *cooperate* ($$C$$) or *defect* ($$D$$). In this variant, instead of choosing directly, each player submits a *program* that receives the opponent's source code as input and outputs $$C$$ or $$D$$. Consider the following agent, *FairBot*:

| **algorithm** $$\texttt{FairBot}(\text{opponent})$$: |
| --- |
| Search for an $$L$$-proof that $$\texttt{opponent}(\texttt{FairBot}) = C$$. |
| **if** proof found **then return** $$C$$ |
| **else return** $$D$$ |

In words: FairBot cooperates with an opponent if and only if it can find an $$L$$-proof that the opponent cooperates with FairBot. Note that FairBot is *unexploitable*: if $$L$$ is sound (i.e. $$L$$ only proves true statements), then FairBot never cooperates with an opponent that defects against it.

The interesting question is what happens when FairBot plays against itself. At first glance, both mutual cooperation and mutual defection seem like stable outcomes.

Consider two copies $$\texttt{FairBot}_{1}$$ and $$\texttt{FairBot}_{2}$$ (identical programs with different implementations). Let $$A$$ be the statement "$$\texttt{FairBot}_{1}(\texttt{FairBot}_{2}) = C$$" and $$B$$ be the statement "$$\texttt{FairBot}_{2}(\texttt{FairBot}_{1}) = C$$." Prove that $$L \vdash A \wedge B$$, i.e. that the two FairBots mutually cooperate. Use Lob's theorem.

:::callout {title="Hint" tone="neutral" collapse="closed"}

From FairBot's source code, $$\Box A$$ implies that $$\texttt{FairBot}_{2}$$ finds a proof that $$\texttt{FairBot}_{1}$$ cooperates, so $$\texttt{FairBot}_{2}$$ cooperates, i.e. $$B$$ is true. Similarly $$\Box B$$ implies $$A$$. Combine these to show $$L \vdash \Box(A \wedge B) \to (A \wedge B)$$, and apply Lob's theorem.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We use Necessitation (N) $$L\vdash\varphi\Rightarrow L\vdash\Box\varphi$$, Distribution (K) $$L\vdash\Box(\varphi\to\psi)\to(\Box\varphi\to\Box\psi)$$, and the Lob condition (4) $$L\vdash\Box\varphi\to\Box\Box\varphi$$.

**(a)** **Necessitation.** If $$L\vdash\varphi$$ there is a concrete proof of $$\varphi$$; searching all strings, $${\mathsf{ProofSeeker}}(\varphi)$$ meets it and halts. "$${\mathsf{ProofSeeker}}(\varphi)$$ halts" is exactly $$\Box\varphi$$, and a halting run is finite, so by the bridge $$L\vdash\Box\varphi$$. $$\square$$

**(b)** **Distribution.** A proof of $$\varphi\to\psi$$ turns a proof of $$\varphi$$ into one of $$\psi$$ (concatenate the two proofs and apply modus ponens). So if $${\mathsf{ProofSeeker}}(\varphi\to\psi)$$ and $${\mathsf{ProofSeeker}}(\varphi)$$ both halt, their outputs combine into a proof of $$\psi$$, whence $${\mathsf{ProofSeeker}}(\psi)$$ halts. This combining is a finite procedure $$L$$ can carry out, so $$L\vdash\Box(\varphi\to\psi)\to(\Box\varphi\to\Box\psi)$$. $$\square$$

**(c)** The Lob sentence $$\lambda$$ satisfies $$L\vdash\lambda\leftrightarrow(\Box\lambda\to C)$$.

$$L\vdash\Box\lambda\to\Box C$$.

*Solution.*  From $$L\vdash\lambda\to(\Box\lambda\to C)$$:

$$
\begin{aligned}\text{(N):}\quad&L\vdash \Box\!\big(\lambda\to(\Box\lambda\to C)\big),\\ \text{(K):}\quad&L\vdash \Box\lambda\to\Box(\Box\lambda\to C), \\ \text{(K):}\quad&L\vdash \Box(\Box\lambda\to C)\to(\Box\Box\lambda\to\Box C),\end{aligned}
$$

and chaining the last two, $$L\vdash\Box\lambda\to(\Box\Box\lambda\to\Box C)$$. By (4), $$L\vdash\Box\lambda\to\Box\Box\lambda$$. Propositionally, from $$\Box\lambda$$ we obtain $$\Box\Box\lambda$$ and then $$\Box C$$, so $$L\vdash\Box\lambda\to\Box C$$. $$\square$$

**(d)** Assuming $$L\vdash\Box C\to C$$, derive $$L\vdash C$$.

*Solution.*  Chaining $$L\vdash\Box\lambda\to\Box C$$ (Exercise 3.2(c)) with $$L\vdash\Box C\to C$$ gives $$L\vdash\Box\lambda\to C$$. The Lob equivalence gives the converse direction $$L\vdash(\Box\lambda\to C)\to\lambda$$, so $$L\vdash\lambda$$. By (N), $$L\vdash\Box\lambda$$; with $$L\vdash\Box\lambda\to C$$, modus ponens yields $$L\vdash C$$. $$\square$$

**(e)** **FairBot.** With $$A:=$$ "$${\mathsf{FairBot}}_{1}({\mathsf{FairBot}}_{2})=C$$" and $$B:=$$ "$${\mathsf{FairBot}}_{2}({\mathsf{FairBot}}_{1})=C$$", show $$L\vdash A\wedge B$$.

*Solution.*  From the source code, $${\mathsf{FairBot}}_{1}$$ returns $$C$$ iff it finds an $$L$$-proof that its opponent $${\mathsf{FairBot}}_{2}$$ returns $$C$$ against it, i.e. a proof of $$B$$; reading this off the code,

$$
L\vdash \Box B\to A,\qquad L\vdash \Box A\to B .
$$

For any $$\varphi$$, $$\Box(A\wedge B)\to\Box\varphi$$ whenever $$A\wedge B\to\varphi$$ is a tautology: indeed (N) gives $$\Box(A\wedge B\to\varphi)$$ and (K) then gives $$\Box(A\wedge B)\to\Box\varphi$$. Applying this to $$\varphi=A$$ and $$\varphi=B$$,

$$
L\vdash \Box(A\wedge B)\to\Box A,\qquad L\vdash \Box(A\wedge B)\to\Box B.
$$

Hence, assuming $$\Box(A\wedge B)$$: we get $$\Box A$$ and $$\Box B$$, then $$B$$ (from $$\Box A\to B$$) and $$A$$ (from $$\Box B\to A$$), so $$A\wedge B$$. Thus

$$
L\vdash \Box(A\wedge B)\to(A\wedge B),
$$

and Lob's theorem with $$C:=A\wedge B$$ gives $$L\vdash A\wedge B$$. $$\square$$

:::
