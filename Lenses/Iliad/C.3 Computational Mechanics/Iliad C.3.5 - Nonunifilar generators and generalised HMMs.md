---
id: '03b92b74-0f35-46f9-8ee5-6ebb27762e1c'
title: "C.3.5 Nonunifilar generators and generalised HMMs"
tldr: "Build belief-state automata for nonunifilar sources such as Mess3, then define generalised HMMs and predictive vectors that need not be probability vectors."
summary_for_tutor: "This is the second part of 'Representing the past' in Iliad worksheet C.3 Computational Mechanics. It contains Exercise 4.3 (Nonunifilar generators and large belief-state automata: the Simple Nonunifilar Source and Mess3, parts a-b) and Exercise 4.4 (Generalised hidden Markov models and predictive vectors, parts a-d), each with a collapsed solution. Concepts: the belief update F_a(eta), mixed state presentation, d-dimensional GHMMs, predictive vectors, the probability matrix and minimal dimension; keep the notation F_a, eta and T^(a). Let the student attempt each exercise before revealing or paraphrasing a solution."
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
**Exercise 4.3 (Nonunifilar generators and large belief-state automata).** For a belief $$\eta$$ and a symbol $$a$$ satisfying $$\eta T^{(a)}\mathbf{1}>0$$, write

$$
F_{a}(\eta):=\frac{\eta T^{(a)}}{\eta T^{(a)}\mathbf{1}}.
$$

Thus the belief-state automaton contains the transition

$$
\eta\xrightarrow{\,a:\eta T^{(a)}\mathbf{1}\,}F_{a}(\eta).
$$

**(a)** **The Simple Nonunifilar Source.** Revisit the source from Part 2. With state order $$(A,B)$$, its symbol matrices and initial belief are

$$
T^{(0)}= \begin{bmatrix}\tfrac{1}{2}&\tfrac{1}{2}\\0&\tfrac{1}{2}\end{bmatrix}, \qquad T^{(1)}= \begin{bmatrix}0&0\\\tfrac{1}{2}&0\end{bmatrix}, \qquad \eta^{(\emptyset)}=\begin{bmatrix}\tfrac{1}{2}&\tfrac{1}{2}\end{bmatrix}.
$$

1. For $$n\geq0$$, show that

$$
\eta^{(10^n)}= \begin{bmatrix}\dfrac{1}{n+1}&\dfrac{n}{n+1}\end{bmatrix}, \qquad \eta^{(0^n)}= \begin{bmatrix}\dfrac{1}{n+2}&\dfrac{n+1}{n+2}\end{bmatrix}.
$$

Deduce that $$\eta^{(0^n)}=\eta^{(10^{n+1})}$$ and observe that $$\eta^{(\emptyset)}=\eta^{(10)}$$.
2. Show that, for every $$n\geq1$$,

$$
\eta^{(10^n1)}=\eta^{(1)}.
$$
3. Draw the first four states of the belief-state automaton and indicate its continuing structure with an ellipsis. Show that the beliefs $$\eta^{(10^n)}$$ are all distinct, identify their limiting point in the $$1$$-simplex, and explain why the two-state generator produces a countably infinite belief-state automaton.

**(b)** **Mess3.** Now take hidden-state and symbol sets both equal to $$\{0,1,2\}$$, with

$$
\alpha=\frac{1}{5},\qquad b=\frac{1-\alpha}{2}=\frac{2}{5}, \qquad x=\frac{3}{20},\qquad y=1-2x=\frac{7}{10},
$$

and

$$
\begin{aligned}T^{(0)}&= \begin{bmatrix}\alpha y&bx&bx\\ \alpha x&by&bx\\ \alpha x&bx&by\end{bmatrix},&T^{(1)}&= \begin{bmatrix}by&\alpha x&bx\\ bx&\alpha y&bx\\ bx&\alpha x&by\end{bmatrix},\\[1mm] T^{(2)}&= \begin{bmatrix}by&bx&\alpha x\\ bx&by&\alpha x\\ bx&bx&\alpha y\end{bmatrix},&\eta^{(\emptyset)}&= \begin{bmatrix}\tfrac{1}{3}&\tfrac{1}{3}&\tfrac{1}{3}\end{bmatrix}.\end{aligned}
$$

1. Verify that $$T=\sum_{a=0}^{2}T^{(a)}$$ is row-stochastic and explain why this generator is nonunifilar. Compute $$\eta^{(0)},\eta^{(1)}$$, and $$\eta^{(2)}$$.
2. Compute $$\eta^{(00)},\eta^{(01)}$$, and $$\eta^{(02)}$$. Use the cyclic symmetry of the process to sketch the first two generations of the belief-state automaton, including the symbol labels.
3. Compute the next-token matrix $$A$$, with $$A_{ia}=\sum_{j}T^{(a)}_{ij}$$, and show that it is invertible. What does this imply about whether distinct beliefs can be merged by the map $$p^{(x_{1:n})}=\eta^{(x_{1:n})}A$$? Contrast this with Exercise 4.2.
4. Using a short program, form

$$
\mathcal{B}_{d}:= \bigl\{\eta^{(x_{1:d})}:x_{1:d}\in\{0,1,2\}^{d}\bigr\}, \qquad 0\leq d\leq7.
$$

Record the number of distinct beliefs at each depth. Visualise $$\mathcal{B}_{7}$$ on the hidden-state $$2$$-simplex, colouring each point by its final symbol. Also visualise the associated next-token vectors on the symbol $$2$$-simplex. Describe the geometric structure that emerges and how the three maps $$F_{0},F_{1},F_{2}$$ generate the outgoing transitions of the belief-state automaton.
5. Explain why the belief-state automata constructed in this exercise are unifilar even though their generators are not. Compare the ladder-with-resets structure of the Simple Nonunifilar Source with the branching structure of Mess3. Finally, explain why the set of beliefs reached by finite histories is countable even though its closure can have a much richer fractal geometry.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)**
1. After observing $$1$$, the hidden state is $$A$$. A path emitting the following $$0^{n}$$ either remains in $$A$$ throughout or moves from $$A$$ to $$B$$ after one of the $$n$$ emissions. These $$n+1$$ paths have equal weight $$2^{-n}$$; one ends in $$A$$ and $$n$$ end in $$B$$. Thus

$$
\eta^{(1)}(T^{(0)})^{n} =2^{-n}\begin{bmatrix}1&n\end{bmatrix}, \qquad \eta^{(10^n)}= \begin{bmatrix}\dfrac{1}{n+1}&\dfrac{n}{n+1}\end{bmatrix}.
$$

Starting instead from the uniform initial belief gives

$$
\eta^{(\emptyset)}(T^{(0)})^{n} =2^{-(n+1)}\begin{bmatrix}1&n+1\end{bmatrix}, \qquad \eta^{(0^n)}= \begin{bmatrix}\dfrac{1}{n+2}&\dfrac{n+1}{n+2}\end{bmatrix}.
$$

Hence $$\eta^{(0^n)}=\eta^{(10^{n+1})}$$, and the case $$n=0$$ gives $$\eta^{(\emptyset)}=\eta^{(10)}$$.
2. For $$n\geq1$$, direct multiplication gives

$$
\eta^{(10^n)}T^{(1)}=\begin{bmatrix}\dfrac{n}{2(n+1)}&0\end{bmatrix}.
$$

Normalising yields $$\eta^{(10^n1)}=\begin{bmatrix}1&0\end{bmatrix}=\eta^{(1)}$$.
3. The automaton begins

$$
\eta^{(1)}\xrightarrow{\,0\,}\eta^{(10)}\xrightarrow{\,0\,}\eta^{(100)}\xrightarrow{\,0\,}\eta^{(1000)}\xrightarrow{\,0\,}\cdots,
$$

and every $$\eta^{(10^n)}$$ with $$n\geq1$$ has a $$1$$-transition back to $$\eta^{(1)}$$. Since the first coordinate $$1/(n+1)$$ is different for each $$n$$, the beliefs are distinct, and

$$
\lim_{n\to\infty}\eta^{(10^n)}=\begin{bmatrix}0&1\end{bmatrix}.
$$

This limiting belief is not reached after any finite history. Hence the two hidden generator states induce countably infinitely many reachable beliefs.

**(b)**
1. Substitution gives $$\alpha y=7/50$$, $$bx=3/50$$, $$\alpha x=3/100$$, and $$by=7/25$$. Each entry is positive, and every state has several possible destinations for each emitted symbol, so the generator is nonunifilar. The rows of $$T^{(0)}+T^{(1)}+T^{(2)}$$ each sum to one. By multiplying the uniform belief and normalising,

$$
\eta^{(0)}=\begin{bmatrix}\tfrac{1}{5}&\tfrac{2}{5}&\tfrac{2}{5}\end{bmatrix}, \quad \eta^{(1)}=\begin{bmatrix}\tfrac{2}{5}&\tfrac{1}{5}&\tfrac{2}{5}\end{bmatrix}, \quad \eta^{(2)}=\begin{bmatrix}\tfrac{2}{5}&\tfrac{2}{5}&\tfrac{1}{5}\end{bmatrix}.
$$
2. Updating $$\eta^{(0)}$$ by each symbol gives

$$
\begin{gathered}\eta^{(00)}= \begin{bmatrix}\tfrac{13}{87}&\tfrac{37}{87}&\tfrac{37}{87}\end{bmatrix},\\[1mm] \eta^{(01)}= \begin{bmatrix}\tfrac{52}{163}&\tfrac{37}{163}&\tfrac{74}{163}\end{bmatrix}, \quad \eta^{(02)}= \begin{bmatrix}\tfrac{52}{163}&\tfrac{74}{163}&\tfrac{37}{163}\end{bmatrix}.\end{gathered}
$$

Cyclically permuting both the state coordinates and symbol labels gives the remaining six depth-two beliefs. The root has three symbol-labelled children, and each of those children again has three symbol-labelled successors.
3. Summing over destination states gives

$$
A=\begin{bmatrix}\tfrac{13}{50}&\tfrac{37}{100}&\tfrac{37}{100}\\ \tfrac{37}{100}&\tfrac{13}{50}&\tfrac{37}{100}\\ \tfrac{37}{100}&\tfrac{37}{100}&\tfrac{13}{50}\end{bmatrix}.
$$

Its eigenvalues are $$1,-11/100,-11/100$$, so $$\det A=121/10000\neq0$$. Consequently $$\eta A=\eta' A$$ implies $$\eta=\eta'$$: the next-token readout does not merge distinct Mess3 beliefs. In Exercise 4.2 the corresponding matrix has a nontrivial kernel and maps $$\eta^{(01)}$$ and $$\eta^{(10)}$$ to the same next-token vector.
4. For these parameters, numerical enumeration gives

$$
\begin{array}{c|rrrrrrrr}d&0&1&2&3&4&5&6&7\\ \hline |\mathcal{B_d|}&1&3&9&27&81&243&729&2187\end{array}
$$

with no coincidences at the displayed depths. The plots show three recursively repeated clusters forming a fractal pattern. The next-token plot is an invertible linear image of the belief plot, so it preserves the distinct points and their recursive organisation.

![figure](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-computational-mechanics-mess3-belief-and-next-token-ge-930059d4.png)

At a point $$\eta$$, the three outgoing edges are obtained by applying $$F_{0},F_{1},F_{2}$$ and have probabilities given by the three coordinates of $$\eta A$$. Thus the three geometric copies visible at the next depth are also the three symbol-labelled branches of the belief-state automaton.
5. A belief and the observed symbol determine a unique updated belief $$F_{a}(\eta)$$, so the belief-state presentation is unifilar. The original generator is nonunifilar because its current hidden state and emitted symbol can leave several possible next hidden states. For the Simple Nonunifilar Source the reachable beliefs form a one-dimensional ladder, with each $$1$$-edge resetting to $$\eta_{0}$$. For Mess3 every symbol remains possible and the three update maps generate a rapidly branching, self-similar geometry. Finally, finite words form a countable set, so their image under the belief map is countable. Taking the closure adds limiting beliefs and can produce an uncountable fractal set.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.4 (Generalised hidden Markov models and predictive vectors).** A $$d$$-dimensional generalised hidden Markov model (GHMM) consists of a finite alphabet $$\mathcal{X}$$, real $$d\times d$$ matrices $$(T^{(a)})_{a\in\mathcal{X}}$$, an initial row vector $$\eta^{(\emptyset)}$$, and a column vector $$\phi$$. Writing

$$
T:=\sum_{a\in\mathcal{X}}T^{(a)},
$$

these objects satisfy

$$
T\phi=\phi,\qquad \eta^{(\emptyset)}\phi=1,\qquad \eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\phi\geq0
$$

for every $$x_{1:n}\in\mathcal{X}^{n}$$ and every $$n\geq0$$.

**(a)** **A probability law from matrix products.** Consider

$$
\Pr(X_{1:n}=x_{1:n}) =\eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\phi.
$$

1. Show that these quantities are nonnegative and that

$$
\sum_{x_{1:n}\in\mathcal{X^n}}\Pr(X_{1:n}=x_{1:n})=1
$$

for every $$n\geq0$$.
2. Show that

$$
\sum_{a\in\mathcal{X}}\Pr(X_{1:n+1}=x_{1:n}a) =\Pr(X_{1:n}=x_{1:n}).
$$

Explain why this is the consistency condition needed to define a one-sided stochastic process.
3. The GHMM conditions do not require $$\eta^{(\emptyset)}T=\eta^{(\emptyset)}$$. Explain why the process need not therefore be stationary. Show that this additional equality is sufficient for stationarity.

**(b)** **Predictive vectors.** For any $$x_{1:n}$$ satisfying $$\Pr(X_{1:n}=x_{1:n})>0$$, define its predictive vector by

$$
\eta^{(x_{1:n})}:=\frac{\eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}}{\eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\phi}.
$$

1. Show that

$$
\eta^{(x_{1:n})}\phi=1
$$

and, for every continuation $$y_{1:m}$$,

$$
\Pr(X_{n+1:n+m}=y_{1:m}\mid X_{1:n}=x_{1:n}) =\eta^{(x_{1:n})}T^{(y_1)}\cdots T^{(y_m)}\phi.
$$
2. Derive the recursive update and identify its normalising factor:

$$
\eta^{(x_{1:n}a)}=\frac{\eta^{(x_{1:n})}T^{(a)}}{\eta^{(x_{1:n})}T^{(a)}\phi}, \quad \Pr(X_{n+1}=a\mid X_{1:n}=x_{1:n}) =\eta^{(x_{1:n})}T^{(a)}\phi.
$$
3. Conceptually contrast an HMM belief state with a GHMM predictive vector. Compare the meaning of their coordinates, their positivity and normalisation properties, and how they encode predictions of future observations.

**(c)** **Predictive vectors need not be probability vectors.** Consider the two-state HMM

$$
M^{(0)}= \begin{bmatrix}\tfrac{4}{5}&0\\0&\tfrac{1}{5}\end{bmatrix}, \qquad M^{(1)}= \begin{bmatrix}\tfrac{1}{5}&0\\0&\tfrac{4}{5}\end{bmatrix}, \qquad \alpha=\begin{bmatrix}\tfrac{1}{2}&\tfrac{1}{2}\end{bmatrix}.
$$

Thus a hidden state is selected initially and thereafter emits a biased coin without changing state. Let

$$
S=\begin{bmatrix}2&-1\\0&1\end{bmatrix}, \qquad T^{(a)}:=S^{-1}M^{(a)}S,\qquad \eta^{(\emptyset)}:=\alpha S,\qquad \phi:=S^{-1}\mathbf{1}.
$$

1. Compute $$T^{(0)},T^{(1)},\eta^{(\emptyset)}$$, and $$\phi$$. Show that, for every $$x_{1:n}$$,

$$
\eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\phi = \alpha M^{(x_1)}\cdots M^{(x_n)}\mathbf{1}.
$$

Deduce that this change of coordinates gives a valid GHMM for the same process.
2. Compute $$\eta^{(0)}$$ and $$\eta^{(1)}$$. Verify directly from $$\eta^{(0)}$$ that

$$
\Pr(X_{2}=0\mid X_{1}=0)=\frac{17}{25}, \qquad \Pr(X_{2}=1\mid X_{1}=0)=\frac{8}{25}.
$$

Explain why the entries of a GHMM predictive vector need not themselves be probabilities.

**(d)** **The probability matrix and minimal dimension.** For finite sets $$\mathcal{U},\mathcal{V}\subseteq\mathcal{X}^{*}$$, define the probability matrix by

$$
\mathsf{P}_{\mathcal{U},\mathcal{V}}(u,v) :=\Pr(X_{1:|u|+|v|}=uv), \qquad u\in\mathcal{U},\quad v\in\mathcal{V}.
$$

1. Use the GHMM matrix product to factor $$\mathsf{P}_{\mathcal{U},\mathcal{V}}$$ as a matrix of prefix row vectors times a matrix of continuation column vectors. Deduce that

$$
\operatorname{rank}\mathsf{P}_{\mathcal{U},\mathcal{V}}\leq d
$$

for every $$d$$-dimensional GHMM realisation.
2. For the process in part (c), take $$\mathcal{U}=\mathcal{V}=\{\emptyset,0,1\}$$. Compute $$\mathsf{P}_{\mathcal{U},\mathcal{V}}$$ and use an SVD to find its singular values. Deduce that the two-dimensional GHMM is minimal-dimensional.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)**
1. Nonnegativity is one of the GHMM assumptions. Expanding the product of the sum of the symbol matrices gives

$$
\sum_{x_{1:n}\in\mathcal{X^n}}T^{(x_1)}\cdots T^{(x_n)}=T^{n}.
$$

Hence

$$
\sum_{x_{1:n}\in\mathcal{X^n}}\Pr(X_{1:n}=x_{1:n}) =\eta^{(\emptyset)}T^{n}\phi =\eta^{(\emptyset)}\phi=1,
$$

where $$T^{n}\phi=\phi$$ follows from $$T\phi=\phi$$. For $$n=0$$ this also says that the empty history has probability one.
2. Summing over the final symbol gives

$$
\begin{aligned}\sum_{a\in\mathcal{X}}\Pr(X_{1:n+1}=x_{1:n}a)&= \eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\left(\sum_{a\in\mathcal{X}}T^{(a)}\right)\phi\\&= \eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}T\phi\\&=\Pr(X_{1:n}=x_{1:n}).\end{aligned}
$$

Thus the length-$$n$$ distribution is the marginal of the length-$$(n+1)$$ distribution over its final coordinate, as required for a process indexed by $$1,2,\ldots$$.
3. The displayed GHMM conditions relate distributions at successive lengths but do not say that a block has the same distribution after shifting its time indices. If $$\eta^{(\emptyset)}T=\eta^{(\emptyset)}$$, then

$$
\begin{aligned}\sum_{a\in\mathcal{X}}\Pr(X_{1:n+1}=a x_{1:n})&= \eta^{(\emptyset)}T T^{(x_1)}\cdots T^{(x_n)}\phi\\&= \eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\phi\\&=\Pr(X_{1:n}=x_{1:n}).\end{aligned}
$$

The left side is $$\Pr(X_{2:n+1}=x_{1:n})$$, so the block distributions are invariant under a one-step shift. Iteration gives stationarity.

**(b)**
1. The denominator in the definition is $$\Pr(X_{1:n}=x_{1:n})$$, and so

$$
\eta^{(x_{1:n})}\phi=1.
$$

By the definition of conditional probability,

$$
\begin{aligned}&\Pr(X_{n+1:n+m}=y_{1:m}\mid X_{1:n}=x_{1:n})\\&\quad= \frac{\eta^{(\emptyset)} T^{(x_1)}\cdots T^{(x_n)} T^{(y_1)}\cdots T^{(y_m)}\phi}{\eta^{(\emptyset)} T^{(x_1)}\cdots T^{(x_n)}\phi}\\&\quad= \eta^{(x_{1:n})}T^{(y_1)}\cdots T^{(y_m)}\phi.\end{aligned}
$$
2. Taking $$m=1$$ in part (i) gives

$$
\Pr(X_{n+1}=a\mid X_{1:n}=x_{1:n}) =\eta^{(x_{1:n})}T^{(a)}\phi, \quad \eta^{(x_{1:n}a)}=\frac{\eta^{(x_{1:n})}T^{(a)}}{\eta^{(x_{1:n})}T^{(a)}\phi}.
$$

The first quantity is exactly the normalising factor in the update shown by the second equality.
3. An HMM belief state has coordinates $$\Pr(S_{n}=i\mid X_{1:n}=x_{1:n})$$, so they are nonnegative, sum to one, and refer to mutually exclusive hidden states. Predictive vectors are coordinates in a linear realisation: they need only satisfy $$\eta^{(x_{1:n})}\phi=1$$ and may have negative entries. Both summarise the history sufficiently to compute future-word probabilities through symbol-matrix products.

**(c)**
1. Since

$$
S^{-1}= \begin{bmatrix}\tfrac{1}{2}&\tfrac{1}{2}\\0&1\end{bmatrix},
$$

direct calculation gives

$$
T^{(0)}= \begin{bmatrix}\tfrac{4}{5}&-\tfrac{3}{10}\\0&\tfrac{1}{5}\end{bmatrix}, \qquad T^{(1)}= \begin{bmatrix}\tfrac{1}{5}&\tfrac{3}{10}\\0&\tfrac{4}{5}\end{bmatrix},
$$

and

$$
\eta^{(\emptyset)}=\begin{bmatrix}1&0\end{bmatrix}, \qquad \phi=\begin{bmatrix}1\\1\end{bmatrix}.
$$

In particular $$T=T^{(0)}+T^{(1)}=I$$, so $$T\phi=\phi$$, and $$\eta^{(\emptyset)}\phi=1$$. In a product, adjacent factors $$SS^{-1}$$ cancel:

$$
\begin{aligned}\eta^{(\emptyset)}T^{(x_1)}\cdots T^{(x_n)}\phi&= \alpha S(S^{-1}M^{(x_1)}S)\cdots (S^{-1}M^{(x_n)}S)S^{-1}\mathbf{1}\\&=\alpha M^{(x_1)}\cdots M^{(x_n)}\mathbf{1}.\end{aligned}
$$

The right side is an HMM sequence probability and is therefore nonnegative. All GHMM conditions are satisfied, and both realisations define the same process.
2. Both first-symbol probabilities are $$1/2$$. Normalising gives

$$
\eta^{(0)}=\begin{bmatrix}\tfrac{8}{5}&-\tfrac{3}{5}\end{bmatrix}, \qquad \eta^{(1)}=\begin{bmatrix}\tfrac{2}{5}&\tfrac{3}{5}\end{bmatrix}.
$$

Moreover,

$$
T^{(0)}\phi =\begin{bmatrix}\tfrac{1}{2}\\[1mm]\tfrac{1}{5}\end{bmatrix}, \qquad T^{(1)}\phi =\begin{bmatrix}\tfrac{1}{2}\\[1mm]\tfrac{4}{5}\end{bmatrix}.
$$

Hence

$$
\eta^{(0)}T^{(0)}\phi=\frac{17}{25}, \qquad \eta^{(0)}T^{(1)}\phi=\frac{8}{25}.
$$

Although the second coordinate of $$\eta^{(0)}$$ is negative, all continuation probabilities obtained from it are valid. The predictive vector consists of coordinates in a chosen linear representation; unlike an HMM belief, its entries do not have to describe mutually exclusive hidden events.

**(d)**
1. For $$u=u_{1}\cdots u_{r}$$ and $$v=v_{1}\cdots v_{s}$$,

$$
\mathsf{P}_{\mathcal{U},\mathcal{V}}(u,v) = \bigl(\eta^{(\emptyset)}T^{(u_1)}\cdots T^{(u_r)}\bigr) \bigl(T^{(v_1)}\cdots T^{(v_s)}\phi\bigr).
$$

Collecting the first factors as rows and the second factors as columns gives the requested factorisation through $$\mathbb{R}^{d}$$. The rank of the product is therefore at most $$d$$.
2. The required probabilities are

$$
\begin{aligned}\Pr(X_{1}=0)=\Pr(X_{1}=1)&=\frac{1}{2},\\ \Pr(X_{1:2}=00)=\Pr(X_{1:2}=11)&=\frac{17}{50},\\ \Pr(X_{1:2}=01)=\Pr(X_{1:2}=10)&=\frac{4}{25}.\end{aligned}
$$

Thus, in the order $$(\emptyset,0,1)$$,

$$
\mathsf{P}_{\mathcal{U},\mathcal{V}}= \begin{bmatrix}1&\tfrac{1}{2}&\tfrac{1}{2}\\ \tfrac{1}{2}&\tfrac{17}{50}&\tfrac{4}{25}\\ \tfrac{1}{2}&\tfrac{4}{25}&\tfrac{17}{50}\end{bmatrix}, \qquad \sigma(\mathsf{P}_{\mathcal{U},\mathcal{V}}) =\left(\frac{3}{2},\frac{9}{50},0\right).
$$

It therefore has rank two. Every GHMM realisation must have dimension at least two, while part (c) supplies a two-dimensional realisation. It is minimal-dimensional.

:::
