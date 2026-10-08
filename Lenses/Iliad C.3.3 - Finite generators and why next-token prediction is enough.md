---
id: '57397096-51c0-4cfc-95c1-be5484edbbb2'
title: "C.3.3 Finite generators and why next-token prediction is enough"
tldr: "Compute causal states for three finite generators, then show that exact next-token prediction is enough to predict the whole future."
summary_for_tutor: "This is the second part of 'Predicting the future' in Iliad worksheet C.3 Computational Mechanics. It contains Exercise 3.3 (From finite generators to causal states: the Zero-One-Random Process, the Even Process and the Simple Nonunifilar Source, parts a-c) and Exercise 3.4 (Why next-token prediction is enough, parts a-c), each with a collapsed solution. Concepts: hidden-state generators with edge labels x:q, unifilar and nonunifilar sources, allowable prefixes, the conditional chain rule; keep the notation S_t, X_t and the edge label convention. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Xavier Poncini (Simplex)
  - Adam Shai (Simplex)
  - Paul Riechers (Simplex)
source_url: https://iliad-intensive.org/interpretability/computational-mechanics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
:::callout {title="Exercise" tone="amber"}
**Exercise 3.3 (From finite generators to causal states).** In this exercise, $$S_{t}$$ denotes the hidden state immediately before the transition that emits $$X_{t+1}$$. All parameters lie strictly between $$0$$ and $$1$$.

**(a)** **The Zero–One–Random Process.** Let $$S_{0}$$ be uniformly distributed over $$\{s_{0},s_{1},s_{R}\}$$. The process has transitions

$$
s_{0}\xrightarrow{\,0:1\,}s_{1}, \qquad s_{1}\xrightarrow{\,1:1\,}s_{R}, \qquad s_{R} \begin{cases}\xrightarrow{\,0:1-p\,}s_{0},\\[-1mm] \xrightarrow{\,1:p\,}s_{0}.\end{cases}
$$

An edge label $$x:q$$ means that the process emits $$x$$ and follows the edge with probability $$q$$.

1. List all possible histories of length two. For each history, determine whether it uniquely identifies the current hidden phase. When it does, identify that phase.
2. For each ambiguous length-two history, determine which additional observations resolve the ambiguity. Identify the resulting phase and explain why it remains known after every subsequent observation.
3. Assume that $$\epsilon(\emptyset)$$, $$\epsilon(0)$$, $$\epsilon(1)$$, and $$\epsilon(10)$$ are pairwise distinct. Show that the causal states have shortest-length representatives

$$
\emptyset,\quad 0,\quad 1,\quad 10,\quad 00,\quad 01,\quad 11.
$$

Explain why no additional causal states arise.
4. Under the assumption in part (iii), draw the automaton associated with the causal-state dynamics.

**(b)** **The Even Process.** Let $$S_{0}$$ be uniformly distributed over $$\{A,B\}$$ and consider the generator

$$
A\xrightarrow{\,0:q\,}A, \qquad A\xrightarrow{\,1:1-q\,}B, \qquad B\xrightarrow{\,1:1\,}A.
$$

Thus every run of $$1$$s between successive $$0$$s has even length.

1. For each of the length-one histories $$0$$ and $$1$$, determine whether the current hidden state can be identified exactly.
2. Starting from each ambiguous history in part (i), consider its possible one-symbol extensions. Which extensions resolve the ambiguity, and which remain ambiguous? You may use the fact that $$\epsilon(\emptyset)=\epsilon(11)$$. What does this imply for histories of the form $$1^{n}$$?
3. Assume additionally that $$\epsilon(\emptyset)\neq\epsilon(1)$$. Show that the causal states have shortest representatives

$$
\emptyset,\qquad 1,\qquad 0,\qquad 01,
$$

and explain why there are no additional causal states. You may distinguish causal states using possible and impossible future continuations.
4. Using $$\epsilon(\emptyset)=\epsilon(11)$$ and assuming $$\epsilon(\emptyset)\neq\epsilon(1)$$, draw the automaton associated with the causal-state dynamics.

**(c)** **The Simple Nonunifilar Source.** Let $$S_{0}$$ be uniformly distributed over $$\{A,B\}$$ and consider

$$
A\xrightarrow{\,0:1/2\,}A, \qquad A\xrightarrow{\,0:1/2\,}B, \qquad B\xrightarrow{\,0:1/2\,}B, \qquad B\xrightarrow{\,1:1/2\,}A.
$$

1. Show that observing a $$1$$ identifies the new hidden state as $$A$$.
2. Starting from $$A$$, show that there are $$n+1$$ hidden paths that emit $$0^{n}$$, each with probability $$2^{-n}$$. How many of these paths can subsequently emit $$1$$? Hence calculate

$$
\Pr(X_{n+2}=1\mid X_{1:n+1}=10^{n}).
$$
3. Show that this probability is different for every $$n\geq0$$. Conclude that the histories

$$
1,10,100,\ldots
$$

belong to distinct causal states and that the process has infinitely many causal states.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)**
1. All four length-two histories are possible. Their resulting hidden phases are

$$
\begin{array}{c|cccc}x_{1:2} & 00 & 01 & 10 & 11\\ \hline S_2 & s_1 & s_R & \{s_0,s_1\} & s_0.\end{array}
$$

Thus $$00$$, $$01$$, and $$11$$ identify the phase exactly, while $$10$$ is ambiguous.
2. From the phases compatible with $$10$$, only $$s_{0}$$ can emit $$0$$, and only $$s_{1}$$ can emit $$1$$. Consequently, $$100$$ identifies the new phase as $$s_{1}$$, while $$101$$ identifies it as $$s_{R}$$. From each phase, the emitted symbol determines the next phase, so every later observation preserves synchronization.
3. The histories $$00$$, $$01$$, and $$11$$ identify $$s_{1}$$, $$s_{R}$$, and $$s_{0}$$, respectively. These phases induce distinct next-token distributions: $$s_{1}$$ emits only $$1$$, $$s_{0}$$ emits only $$0$$, and $$s_{R}$$ can emit either symbol. Hence they give three distinct causal states.

They are also distinct from the four states assumed in the question. This can be seen without calculating probabilities by comparing possible length-two continuations:

$$
\begin{array}{c|c}\text{representative} & \text{possible length-two continuations}\\ \hline \emptyset & \{00,01,10,11\}\\ 0 & \{01,10,11\}\\ 1 & \{00,01,10\}\\ 10 & \{01,10,11\}\\ 00 & \{10,11\}\\ 01 & \{00,10\}\\ 11 & \{01\}\end{array}
$$

The only repeated continuation set belongs to $$0$$ and $$10$$, whose causal states are assumed to be distinct. Finally, every history of length at least three identifies the phase by part (ii), and so belongs to one of the states represented by $$00$$, $$01$$, and $$11$$. No further causal states arise.
4. Appending each possible symbol gives the causal-state update:

$$
\begin{array}{c|cc}\text{state} & 0 & 1\\ \hline \epsilon(\emptyset) & \epsilon(0) & \epsilon(1)\\ \epsilon(0) & \epsilon(00) & \epsilon(01)\\ \epsilon(1) & \epsilon(10) & \epsilon(11)\\ \epsilon(10) & \epsilon(00) & \epsilon(01)\\ \epsilon(00) & \text{–} & \epsilon(01)\\ \epsilon(01) & \epsilon(11) & \epsilon(11)\\ \epsilon(11) & \epsilon(00) & \text{–}\end{array}
$$

Here a dash denotes an impossible extension. Drawing one node for each row and the indicated symbol-labelled edges gives the required automaton.

**(b)**
1. The history $$0$$ identifies the current state as $$A$$: only $$A$$ can emit $$0$$, and this transition returns to $$A$$. The history $$1$$ is ambiguous. If $$S_{0}=A$$, it leads to $$B$$, while if $$S_{0}=B$$, it leads to $$A$$.
2. From the two states compatible with the history $$1$$, only $$A$$ can emit $$0$$. Therefore $$10$$ resolves the ambiguity and identifies the new state as $$A$$. The extension $$11$$ remains ambiguous. Using the given equality and recursively updating after pairs of $$1$$s gives

$$
\epsilon(1^{2k})=\epsilon(\emptyset), \qquad \epsilon(1^{2k+1})=\epsilon(1), \qquad k\geq0.
$$
3. If a history contains a $$0$$, its final $$0$$ synchronizes the generator to $$A$$. An even number of trailing $$1$$s then leaves it in $$A$$, represented by $$0$$, while an odd number leaves it in $$B$$, represented by $$01$$. If the history contains no $$0$$, part (ii) shows that its causal state is represented by $$\emptyset$$ or $$1$$, according to the parity of its length. Thus no additional causal states arise.

These four states are distinct. The state represented by $$01$$ cannot emit $$0$$, whereas the other three can. The continuation $$10$$ is impossible after $$0$$ but possible after $$\emptyset$$ and $$1$$. Finally, $$\epsilon(\emptyset)\neq\epsilon(1)$$ by assumption. Hence the displayed representatives are also shortest.
4. Appending each possible symbol gives the causal-state update:

$$
\begin{array}{c|cc}\text{state} & 0 & 1\\ \hline \epsilon(\emptyset) & \epsilon(0) & \epsilon(1)\\ \epsilon(1) & \epsilon(0) & \epsilon(\emptyset)\\ \epsilon(0) & \epsilon(0) & \epsilon(01)\\ \epsilon(01) & \text{–} & \epsilon(0)\end{array}
$$

Here a dash denotes an impossible extension. Drawing one node for each row and the indicated symbol-labelled edges gives the required automaton.

**(c)**
1. The only transition that emits $$1$$ starts from $$B$$, and that transition leads to $$A$$. Thus the hidden state immediately after observing $$1$$ is $$A$$.
2. One path remains in $$A$$ while emitting all $$n$$ zeros. Each of the other $$n$$ paths moves from $$A$$ to $$B$$ on one of the $$n$$ transitions and then remains in $$B$$. Thus there are $$n+1$$ paths, each with probability $$2^{-n}$$, and

$$
\Pr(0^{n}\mid S=A)=(n+1)2^{-n}.
$$

The $$n$$ paths that end in $$B$$ can subsequently emit $$1$$. Including this final transition, each has probability $$2^{-(n+1)}$$, so

$$
\Pr(X_{n+2}=1\mid X_{1:n+1}=10^{n}) =\frac{n2^{-(n+1)}}{(n+1)2^{-n}}=\frac{n}{2(n+1)}.
$$
3. Since

$$
\frac{n}{2(n+1)}=\frac{1}{2}-\frac{1}{2(n+1)},
$$

this probability is strictly increasing with $$n$$. Hence every pair of histories $$10^{n}$$ and $$10^{m}$$, with $$n\neq m$$, already has a different next-token distribution. They must lie in different causal states. The source consequently has infinitely many causal states despite its two-state generator.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.4 (Why next-token prediction is enough).** Recall that

$$
\mathcal{X}_{+}^{*} :=\left\{x\in\mathcal{X}^{*}: \Pr\!\left(X_{1:|x|}=x\right)>0\right\}
$$

is the set of allowable histories.

Consider a model with parameters $$\theta$$ satisfying

$$
h_{n}=f_{\theta}(h_{n-1},x_{n}), \qquad y_{n}=g_{\theta}(h_{n-1},x_{n}).
$$

Fix the initial hidden state $$h_{0}$$ and suppose that the model predicts the next-token distribution exactly: for every $$n\geq1$$,

$$
y_{n} =\Pr\!\left( X_{n+1}\mid X_{1:n}=x_{1:n}\right), \qquad \forall\,x_{1:n}\in\mathcal{X}_{+}^{*}.
$$

For every nonempty allowable history, define

$$
R(x_{1:n}):=(h_{n-1},x_{n}).
$$

For $$a\in\mathcal{X}$$, define the deterministic update

$$
\Phi_{a}(h,x):=\bigl(f_{\theta}(h,x),a\bigr).
$$

For a word $$z_{1:j}$$, write

$$
\Phi_{z_{1:j}}:=\Phi_{z_j}\circ\cdots\circ\Phi_{z_1}, \qquad \Phi_{z_{1:0}}:=\operatorname{id}.
$$

**(a)** Show that, whenever $$x_{1:n}z_{1:j}$$ is allowable,

$$
R(x_{1:n}z_{1:j}) =\Phi_{z_{1:j}}\!\left(R(x_{1:n})\right).
$$

Hence show that, if $$R(x_{1:n})=R(x'_{1:m})$$ and both extended histories are allowable, then

$$
R(x_{1:n}z_{1:j})=R(x'_{1:m}z_{1:j}).
$$

**(b)** Let $$R(x_{1:n})=R(x'_{1:m})$$ and fix $$z_{1:k}\in\mathcal{X}^{k}$$. As the symbols of $$z_{1:k}$$ are read from left to right, use part (a) and exact next-token prediction to show that for each $$0\leq j<k$$ such that the prefixes through $$z_{1:j}$$ are allowable,

$$
\begin{aligned}&\Pr\!\left( X_{n+j+1}=z_{j+1}\mid X_{1:n+j}=x_{1:n}z_{1:j}\right)\\&\qquad= \Pr\!\left( X_{m+j+1}=z_{j+1}\mid X_{1:m+j}=x'_{1:m}z_{1:j}\right).\end{aligned}
$$

Deduce that either the same first zero-probability extension is encountered after both histories, or every prefix of $$z_{1:k}$$ is allowable after both histories.

**(c)** In the case where every prefix is allowable, use the conditional chain rule to write

$$
\begin{aligned}&\Pr\!\left( X_{n+1:n+k}=z_{1:k}\mid X_{1:n}=x_{1:n}\right)\\&\qquad= \prod_{j=0}^{k-1}\Pr\!\left( X_{n+j+1}=z_{j+1}\mid X_{1:n+j}=x_{1:n}z_{1:j}\right).\end{aligned}
$$

Write the analogous product after $$x'_{1:m}$$ and compare its factors. Deal separately with the zero-probability case from part (b), and conclude directly that

$$
\begin{gathered}R(x_{1:n})=R(x'_{1:m}) \quad\Longrightarrow\\[1mm] \Pr\!\left( X_{n+1:n+k}=z_{1:k}\mid X_{1:n}=x_{1:n} \right) = \Pr\!\left( X_{m+1:m+k}=z_{1:k}\mid X_{1:m}=x'_{1:m} \right).\end{gathered}
$$

Hence $$R(x_{1:n})=(h_{n-1},x_{n})$$ is a sufficient statistic for predicting the entire future.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Appending one symbol $$a$$ gives

$$
R(x_{1:n}a) =\bigl(f_{\theta}(h_{n-1},x_{n}),a\bigr) =\Phi_{a}\!\left(R(x_{1:n})\right).
$$

Repeatedly applying this deterministic update along $$z_{1:j}$$ gives

$$
R(x_{1:n}z_{1:j}) =\Phi_{z_j}\circ\cdots\circ\Phi_{z_1}\!\left(R(x_{1:n})\right) =\Phi_{z_{1:j}}\!\left(R(x_{1:n})\right).
$$

If $$R(x_{1:n})=R(x'_{1:m})$$ and both extended histories are allowable, applying the same composite function to the equal starting representations gives

$$
R(x_{1:n}z_{1:j})=R(x'_{1:m}z_{1:j}).
$$

**(b)** Suppose that the prefixes through $$z_{1:j}$$ are allowable after both histories. Part (a) gives

$$
R(x_{1:n}z_{1:j}) =R(x'_{1:m}z_{1:j}).
$$

The two representations give the same arguments to $$g_{\theta}$$, so exact next-token prediction gives

$$
\begin{aligned}&\Pr\!\left( X_{n+j+1}=z_{j+1}\mid X_{1:n+j}=x_{1:n}z_{1:j}\right)\\&\qquad= \Pr\!\left( X_{m+j+1}=z_{j+1}\mid X_{1:m+j}=x'_{1:m}z_{1:j}\right).\end{aligned}
$$

Thus the next extension has positive probability after one history exactly when it has positive probability after the other. Following the word from left to right, either both encounter their first zero at the same position or all its prefixes are allowable after both.

**(c)** If every prefix is allowable, the conditional chain rule gives the product in the question and

$$
\begin{aligned}&\Pr\!\left( X_{m+1:m+k}=z_{1:k}\mid X_{1:m}=x'_{1:m}\right)\\&\qquad= \prod_{j=0}^{k-1}\Pr\!\left( X_{m+j+1}=z_{j+1}\mid X_{1:m+j}=x'_{1:m}z_{1:j}\right).\end{aligned}
$$

Part (b) shows that the factors in the two products are equal, so the products are equal. If a first zero-probability extension is encountered instead, part (b) shows that it occurs after both histories; consequently both probabilities of the complete continuation are zero.

Therefore equal values of $$R$$ imply equal conditional probabilities for every finite continuation. By the definition of sufficiency,

$$
R(x_{1:n})=(h_{n-1},x_{n})
$$

is a sufficient statistic for predicting the entire future.

:::
