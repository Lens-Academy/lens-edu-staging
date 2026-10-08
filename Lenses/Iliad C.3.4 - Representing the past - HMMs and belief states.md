---
id: '262a76de-3b6b-4f1c-aa21-a2a3f7c1ca76'
title: "C.3.4 Representing the past: HMMs and belief states"
tldr: "Translate between HMM diagrams and transition matrices, then compute belief states for the Zero-One-Random HMM and the next-token readout from them."
summary_for_tutor: "This is the first part of 'Representing the past' in Iliad worksheet C.3 Computational Mechanics. It contains Exercise 4.1 (Translating between HMM diagrams and matrices, parts a-d, using the Zero-One-Random and Even Process HMMs) and Exercise 4.2 (Belief states and a lossy next-token readout, parts a-f), each with a collapsed solution. Concepts: edge-emitting HMMs with symbol matrices T^(a), belief states eta^(x), belief-state diagrams compared with causal-state automata, next-token probabilities from beliefs; keep the notation T^(a) and eta. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## 4. Representing the past

:::callout {title="Instructions" tone="blue"}

Give a clear justification for each answer. You may use results proved in the lecture unless an exercise asks you to establish them. Questions marked **Extension** are optional.

:::

%% iliad:solutionsonly:start %%

:::callout {title="Instructions" tone="blue"}

These notes reproduce each exercise before its solution. Equivalent arguments, diagrams, and notation should receive full credit when the mathematical reasoning is correct.

:::

%% iliad:solutionsonly:end %%

:::callout {title="Exercise" tone="amber"}
**Exercise 4.1 (Translating between HMM diagrams and matrices).** For an edge-emitting hidden Markov model, use the convention

$$
T^{(a)}_{ij}:=\Pr(X_{t+1}=a,S_{t+1}=j\mid S_{t}=i).
$$

Thus rows index the current hidden state, columns index the next hidden state, and the superscript records the emitted symbol. Throughout this exercise, $$0<p,q<1$$.

**(a)** Suppose that $$T^{(a)}_{ij}=r$$. Explain each component of the following diagram:

$$
i\xrightarrow{\,a:r\,}j.
$$

What does a zero entry mean? Why is the matrix $$T:=\sum_{a\in\mathcal{X}}T^{(a)}$$ row-stochastic?

**(b)** **From matrices to a diagram: Zero–One–Random.** Take the state order to be $$(0,1,R)$$ and suppose that

$$
\eta^{(\emptyset)}=\begin{bmatrix}\tfrac{1}{3}&\tfrac{1}{3}&\tfrac{1}{3}\end{bmatrix}, \qquad T^{(0)}= \begin{bmatrix}0&1&0\\ 0&0&0\\ 1-p&0&0\end{bmatrix}, \qquad T^{(1)}= \begin{bmatrix}0&0&0\\ 0&0&1\\ p&0&0\end{bmatrix}.
$$

1. Draw the corresponding edge-emitting HMM. Describe informally the three phases represented by $$0$$, $$1$$, and $$R$$.
2. Calculate $$\Pr(X_{1:3}=011)$$ and $$\Pr(X_{1:3}=000)$$ in two ways: first by tracing paths through your diagram, and then from

$$
\Pr(X_{1:3}=x_{1:3}) =\eta^{(\emptyset)}T^{(x_1)}T^{(x_2)}T^{(x_3)}\mathbf{1}.
$$

**(c)** **From a diagram to matrices: the Even Process.** Consider the edge-emitting HMM

$$
A\xrightarrow{\,0:q\,}A, \qquad A\xrightarrow{\,1:1-q\,}B, \qquad B\xrightarrow{\,1:1\,}A,
$$

with no other edges. Take the state order to be $$(A,B)$$ and let $$\eta^{(\emptyset)}=\begin{bmatrix}\tfrac{1}{2}&\tfrac{1}{2}\end{bmatrix}$$.

1. Construct $$T^{(0)}$$ and $$T^{(1)}$$. Account explicitly for every zero entry in the two matrices.
2. Form $$T=T^{(0)}+T^{(1)}$$ and verify that it is row-stochastic.
3. Calculate $$\Pr(X_{1:3}=011)$$ and $$\Pr(X_{1:3}=010)$$ both by tracing paths through the diagram and by multiplying the appropriate symbol matrices. Explain how the second calculation reflects the defining constraint of the Even Process.

**(d)** **Extension.** Let $$\mathcal{X}$$ be the observation alphabet of an arbitrary finite-state HMM, let $$T=\sum_{a\in\mathcal{X}}T^{(a)}$$, and let $$\eta^{(\emptyset)}$$ be a probability distribution. Prove that, for every $$n\geq 0$$,

$$
\sum_{w\in\mathcal{X^n}}\Pr(X_{1:n}=w) =\eta^{(\emptyset)}T^{n}\mathbf{1} =1.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** In the diagram, $$i$$ is the current hidden state, $$j$$ is the next hidden state, $$a$$ is the emitted symbol, and $$r$$ is the probability of that joint emission-transition event conditional on starting in $$i$$. Thus the edge records $$T^{(a)}_{ij}=\Pr(X_{t+1}=a,S_{t+1}=j\mid S_{t}=i)=r$$. A zero entry means that no such emission-transition pair is possible. For a fixed current state $$i$$, the events indexed by all pairs $$(a,j)$$ exhaust the possible emitted symbols and next states. Consequently,

$$
\sum_{a\in\mathcal{X}}\sum_{j} T^{(a)}_{ij}=1.
$$

Since

$$
T_{ij}=\sum_{a\in\mathcal{X}}T^{(a)}_{ij},
$$

every entry of $$T$$ is nonnegative and its $$i$$th row sums to

$$
\sum_{j}T_{ij}=\sum_{j}\sum_{a\in\mathcal{X}}T^{(a)}_{ij}=1.
$$

Hence $$T$$ is row-stochastic.

**(b)**
1. The nonzero entries give the transitions

$$
0\xrightarrow{\,0:1\,}1, \qquad 1\xrightarrow{\,1:1\,}R, \qquad R\xrightarrow{\,0:1-p\,}0, \qquad R\xrightarrow{\,1:p\,}0.
$$

Thus the diagram is a three-state cycle, with two differently labelled edges from $$R$$ to $$0$$. State $$0$$ is the phase that emits $$0$$ deterministically, state $$1$$ is the phase that emits $$1$$ deterministically, and state $$R$$ is the random phase, which emits $$1$$ with probability $$p$$ and $$0$$ with probability $$1-p$$.
2. For $$011$$, the only possible initial state is $$0$$. The model then follows

$$
0\xrightarrow{\,0:1\,}1 \xrightarrow{\,1:1\,}R \xrightarrow{\,1:p\,}0.
$$

Including the initial probability $$1/3$$ gives $$\Pr(011)=p/3$$. Matrix multiplication gives the same result:

$$
\eta^{(\emptyset)}T^{(0)}T^{(1)}T^{(1)}=\begin{bmatrix}p/3&0&0\end{bmatrix}, \qquad \Pr(011)=p/3.
$$

No state permits a path labelled $$000$$: starting from $$0$$, the first $$0$$ moves to state $$1$$, which cannot emit $$0$$; starting from $$1$$, even the first $$0$$ is impossible; and starting from $$R$$, the first two zeros move through $$R\to0\to1$$, after which a third zero is impossible. Correspondingly,

$$
\eta^{(\emptyset)}T^{(0)}T^{(0)}T^{(0)}=\begin{bmatrix}0&0&0\end{bmatrix}, \qquad \Pr(000)=0.
$$

**(c)**
1. In state order $$(A,B)$$, the matrices are

$$
T^{(0)}= \begin{bmatrix}q&0\\ 0&0\end{bmatrix}, \qquad T^{(1)}= \begin{bmatrix}0&1-q\\ 1&0\end{bmatrix}.
$$

In $$T^{(0)}$$, the entry $$(A,B)$$ is zero because no $$0$$-edge connects $$A$$ to $$B$$, while the entire $$B$$ row is zero because state $$B$$ cannot emit $$0$$. In $$T^{(1)}$$, the diagonal entries are zero because neither $$1$$-edge is a self-loop. The two off-diagonal entries record $$A\xrightarrow{1:1-q}B$$ and $$B\xrightarrow{1:1}A$$.
2. We have

$$
T= \begin{bmatrix}q&1-q\\ 1&0\end{bmatrix}.
$$

Its entries are nonnegative and both rows sum to one.
3. The word $$011$$ can be produced only by starting from $$A$$ and following

$$
A\xrightarrow{\,0:q\,}A \xrightarrow{\,1:1-q\,}B \xrightarrow{\,1:1\,}A.
$$

Thus

$$
\Pr(011)=\frac{1}{2}q(1-q).
$$

The matrix calculation is

$$
\eta^{(\emptyset)}T^{(0)}T^{(1)}T^{(1)}=\begin{bmatrix}\tfrac{1}{2}q(1-q)&0\end{bmatrix}, \qquad \Pr(011)=\frac{1}{2}q(1-q).
$$

The word $$010$$ would require the path to emit a $$0$$ immediately after the transition $$A\xrightarrow{1}B$$, but state $$B$$ cannot emit $$0$$. Hence there is no such path. Equivalently,

$$
\eta^{(\emptyset)}T^{(0)}T^{(1)}T^{(0)}=\begin{bmatrix}0&0\end{bmatrix}, \qquad \Pr(010)=0.
$$

This is the shortest example of an odd run of $$1$$s occurring between two $$0$$s, which the Even Process forbids.

**(d)** Expanding the product of the sum of the symbol matrices gives

$$
T^{n} =\left(\sum_{a\in\mathcal{X}}T^{(a)}\right)^{n} =\sum_{w\in\mathcal{X^n}}T^{(w_1)}\cdots T^{(w_n)}.
$$

Multiplying on the left by $$\eta^{(\emptyset)}$$ and on the right by $$\mathbf{1}$$ therefore yields

$$
\eta^{(\emptyset)}T^{n}\mathbf{1} =\sum_{w\in\mathcal{X^n}}\eta^{(\emptyset)}T^{(w_1)}\cdots T^{(w_n)}\mathbf{1} =\sum_{w\in\mathcal{X^n}}\Pr(w).
$$

Since $$T$$ is row-stochastic, $$T\mathbf{1}=\mathbf{1}$$ and hence $$T^{n}\mathbf{1}=\mathbf{1}$$. Finally, $$\eta^{(\emptyset)}\mathbf{1}=1$$, because the initial vector is a probability distribution. The required sum is therefore one.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.2 (Belief states and a lossy next-token readout).** Continue with the Zero–One–Random HMM from Exercise 4.1, using state order $$(0,1,R)$$. For an allowable history $$x_{1:n}=x_{1}\cdots x_{n}$$, compute its belief from scratch as

$$
\eta^{(x_{1:n})}:=\frac{\eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}}{\eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\mathbf{1}}.
$$

Here $$\eta_{i}^{(x_{1:n})}=\Pr(S_{n}=i\mid X_{1:n}=x_{1:n})$$. For an allowable extension $$x_{1:n+1}=x_{1:n}a$$, update recursively as

$$
\eta^{(x_{1:n+1})}=\frac{\eta^{(x_{1:n})}T^{(a)}}{\eta^{(x_{1:n})}T^{(a)}\mathbf{1}}.
$$

**(a)** Compute $$\eta^{(0)}$$ and $$\eta^{(1)}$$. Interpret their components as posterior probabilities over the three hidden phases.

**(b)** Show that the seven beliefs

$$
\mathcal{B}= \bigl\{ \eta^{(\emptyset)},\eta^{(0)},\eta^{(1)},\eta^{(00)}, \eta^{(01)},\eta^{(10)},\eta^{(11)}\bigr\}
$$

are distinct and that $$\mathcal{B}$$ is closed under every allowable symbol update. Draw the symbol-labelled transition diagram on $$\mathcal{B}$$.

**(c)** Compare your belief-state diagram with both the causal-state automaton constructed in Part 2 and the three-state generative HMM from Exercise 4.1.
1. Match each belief to the causal state with the same shortest-length representative. Do the symbol-labelled transitions agree?
2. Which beliefs correspond to knowing the hidden phase exactly, and which represent uncertainty over several phases? Show that the hidden phase becomes known after at most three observations and remains known thereafter.
3. Observe that the finite-history belief-state presentation has seven states while the generative HMM has only three. What does this suggest about the possible relative difficulty of generation and inference?

**(d)** For each belief $$\eta^{(x_{1:n})}\in\mathcal{B}$$ from part (b), compute its associated next-token probability vector

$$
\begin{gathered}p^{(x_{1:n})} :=\left( \Pr(X_{n+1}=a\mid X_{1:n}=x_{1:n}) \right)_{a\in\{0,1\}} =\eta^{(x_{1:n})}A,\\[1mm] A_{ia}:=\sum_jT^{(a)}_{ij}.\end{gathered}
$$

Visualise the belief geometry on the $$2$$-simplex over hidden states $$(0,1,R)$$ and the next-token geometry on the $$1$$-simplex over symbols $$(0,1)$$.

**(e)** Calculate

$$
\Pr(X_{3:4}=00\mid X_{1:2}=10) \qquad\text{and}\qquad \Pr(X_{3:4}=00\mid X_{1:2}=01).
$$

Deduce that the next-token probability vector need not be sufficient for predicting the entire future.

**(f)** **Extension.** Let $$\delta:=\eta^{(10)}-\eta^{(01)}$$. Show that

$$
\delta A=0 \qquad\text{but}\qquad \delta T^{(0)}T^{(0)}\mathbf{1}\neq0.
$$

Interpret these two statements in terms of one-step and longer-horizon prediction.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Multiplying the initial belief by the two symbol matrices gives

$$
\eta^{(\emptyset)}T^{(0)}=\begin{bmatrix}(1-p)/3&1/3&0\end{bmatrix}, \qquad \eta^{(\emptyset)}T^{(1)}=\begin{bmatrix}p/3&0&1/3\end{bmatrix}.
$$

Their row sums are respectively $$(2-p)/3$$ and $$(1+p)/3$$. Normalising therefore gives

$$
\eta^{(0)}=\begin{bmatrix}\dfrac{1-p}{2-p}&\dfrac{1}{2-p}&0\end{bmatrix}, \qquad \eta^{(1)}=\begin{bmatrix}\dfrac{p}{1+p}&0&\dfrac{1}{1+p}\end{bmatrix}.
$$

After observing $$0$$, the current phase is either $$0$$ or $$1$$ with the displayed posterior probabilities, and cannot be $$R$$. After observing $$1$$, it is either $$0$$ or $$R$$, and cannot be $$1$$.

**(b)** Direct evaluation gives

$$
\begin{aligned}\eta^{(00)}&=\begin{bmatrix}0&1&0\end{bmatrix},&\eta^{(01)}&=\begin{bmatrix}0&0&1\end{bmatrix},\\ \eta^{(10)}&=\begin{bmatrix}1-p&p&0\end{bmatrix},&\eta^{(11)}&=\begin{bmatrix}1&0&0\end{bmatrix}.\end{aligned}
$$

Thus the pure beliefs are $$\eta^{(11)}$$, $$\eta^{(00)}$$, and $$\eta^{(01)}$$. The pure beliefs are distinct. The beliefs $$\eta^{(\emptyset)}$$, $$\eta^{(0)}$$, and $$\eta^{(1)}$$ have different supports from one another and from the pure beliefs. The only remaining comparison is between $$\eta^{(0)}$$ and $$\eta^{(10)}$$, which both have support $$\{0,1\}$$. Equality would require $$1/(2-p)=p$$, or $$(1-p)^{2}=0$$, contrary to $$p<1$$.

The allowable updates are

$$
\begin{array}{c|cc}\text{current belief} & 0 & 1\\ \hline \eta^{(\emptyset)} & \eta^{(0)} & \eta^{(1)}\\ \eta^{(0)} & \eta^{(00)} & \eta^{(01)}\\ \eta^{(1)} & \eta^{(10)} & \eta^{(11)}\\ \eta^{(10)} & \eta^{(00)} & \eta^{(01)}\\ \eta^{(11)} & \eta^{(00)} & \text{impossible}\\ \eta^{(00)} & \text{impossible} & \eta^{(01)}\\ \eta^{(01)} & \eta^{(11)} & \eta^{(11)}\end{array}
$$

This table specifies the requested symbol-labelled diagram and shows that every allowable update stays in $$\mathcal{B}$$.

**(c)**
1. Under the assumptions used in Part 2, the correspondence is

$$
\begin{aligned}\epsilon(\emptyset)&\longleftrightarrow\eta^{(\emptyset)},&\epsilon(0)&\longleftrightarrow\eta^{(0)},&\epsilon(1)&\longleftrightarrow\eta^{(1)},\\ \epsilon(10)&\longleftrightarrow\eta^{(10)},&\epsilon(11)&\longleftrightarrow\eta^{(11)},&\epsilon(00)&\longleftrightarrow\eta^{(00)},\\ \epsilon(01)&\longleftrightarrow\eta^{(01)}.\end{aligned}
$$

The transition table from part (b) agrees with the causal-state automaton after making these substitutions.
2. The pure beliefs $$\eta^{(11)}$$, $$\eta^{(00)}$$, and $$\eta^{(01)}$$ identify the hidden phase exactly. The other four beliefs assign positive probability to more than one phase and therefore represent uncertainty. After two observations only the history $$10$$ leaves a mixed belief. Either allowable third symbol sends $$\eta^{(10)}$$ to a pure belief. Once the belief is pure, every allowable transition in the table leads to another pure belief, so the phase remains known.
3. The generator has access to its actual hidden phase and needs only the three states $$0$$, $$1$$, and $$R$$. An observer begins with an unknown phase and must also represent four transient posterior distributions before synchronising with the generator. This example therefore shows that inference can require a richer state description than a particular generative presentation.

**(d)** The probability of each symbol from a hidden phase is obtained by summing the corresponding row of its symbol matrix over destination states. With column order $$(0,1)$$, this gives

$$
A= \begin{bmatrix}1&0\\ 0&1\\ 1-p&p\end{bmatrix}.
$$

Hence

$$
\begin{array}{c|c}\text{belief} & \text{next-token vector}\\ \hline \eta^{(\emptyset)} & p^{(\emptyset)}= \left(\dfrac{2-p}{3},\dfrac{1+p}{3}\right)\\[1mm] \eta^{(0)} & p^{(0)}= \left(\dfrac{1-p}{2-p},\dfrac{1}{2-p}\right)\\[1mm] \eta^{(1)} & p^{(1)}= \left(\dfrac{1}{1+p},\dfrac{p}{1+p}\right)\\[1mm] \eta^{(00)} & p^{(00)}=(0,1)\\ \eta^{(01)} & p^{(01)}=(1-p,p)\\ \eta^{(10)} & p^{(10)}=(1-p,p)\\ \eta^{(11)} & p^{(11)}=(1,0)\end{array}
$$

On the belief $$2$$-simplex, $$\eta^{(11)}$$, $$\eta^{(00)}$$, and $$\eta^{(01)}$$ are the three vertices, while $$\eta^{(\emptyset)}$$ is the barycentre. The beliefs $$\eta^{(0)}$$ and $$\eta^{(10)}$$ lie on the edge joining $$\eta^{(11)}$$ to $$\eta^{(00)}$$, and $$\eta^{(1)}$$ lies on the edge joining $$\eta^{(11)}$$ to $$\eta^{(01)}$$.

On the next-token $$1$$-simplex, each point is located by the second coordinate in the table, namely its probability of emitting $$1$$. The relation $$p^{(x_{1:n})}=\eta^{(x_{1:n})}A$$ maps the two distinct beliefs $$\eta^{(01)}$$ and $$\eta^{(10)}$$ to the same point $$p^{(01)}=p^{(10)}=(1-p,p)$$.

**(e)** Starting from $$\eta^{(10)}=(1-p,p,0)$$, observing a $$0$$ can only come from phase $$0$$ and moves the process to phase $$1$$, which cannot emit a second $$0$$. Hence

$$
\Pr(X_{3:4}=00\mid X_{1:2}=10) =\eta^{(10)}T^{(0)}T^{(0)}\mathbf{1}=0.
$$

Starting from $$\eta^{(01)}=(0,0,1)$$, the first $$0$$ has probability $$1-p$$ and moves the process to phase $$0$$, which emits the second $$0$$ deterministically. Therefore

$$
\Pr(X_{3:4}=00\mid X_{1:2}=01) =\eta^{(01)}T^{(0)}T^{(0)}\mathbf{1}=1-p.
$$

The histories agree about the next symbol but disagree about a two-symbol continuation, so their shared next-token vector is not sufficient for the entire future.

**(f)** We have

$$
\delta =\begin{bmatrix}1-p&p&-1\end{bmatrix}.
$$

Direct multiplication gives

$$
\delta A=\begin{bmatrix}0&0\end{bmatrix}, \qquad \delta T^{(0)}T^{(0)}\mathbf{1}=-(1-p)\neq0.
$$

Thus the difference between the beliefs is invisible to the one-step readout but visible to a readout associated with the two-symbol future $$00$$.

:::
