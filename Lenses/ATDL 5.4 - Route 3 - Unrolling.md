---
id: 'e631b3c1-9a52-4c7b-a79b-98c50a78c8ea'
title: "Route 3: unrolling"
tldr: "Differentiate through the whole training run, step by step, as backpropagation does through a forward pass. In the right limit this recovers the influence function."
summary_for_tutor: "Day 5 Route 3 (Louis Jaburi's fast-track route 3): skim Section 2, then Section 4 of the Iliad B.5 worksheet. Core exercises 4.1 and 4.2 (the long exercise in Subsection 4.3 that recovers the influence function as a limit of unrolling); 4.3 optional."
authors:
  - Louis Jaburi
source_url: https://github.com/iliad-team/iliad-intensive/tree/d2792cbf53158db2a5729ff7d431a53869b64624/tex/data-attribution
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 70
tutor_minutes: 20
---

#### Text
content::
In the worksheet, skim **Section 2**, then read **Section 4** (Unrolling) in full. The long exercise in Subsection 4.3 is the one Louis highlights.

#### Question: Open
id:: e6799782-cd57-4313-be72-80f7c593ed6d
content::
\## Exercise 4.1: Derivation of the unrolling formula

**Exercise 4.1 (Derivation of the unrolling formula).**

**(a)** Starting from the SGD update (16), apply the chain rule to write $\tfrac{\partial w_{t+1}}{\partial \beta_i}\big|_{\beta=\mathbf{1}}$ as a sum of two terms: one from the explicit dependence on $\beta_i$ (the direct effect) and one from the dependence of $w_t$ on $\beta_i$ (the indirect effect). Show that the result is the recursion

$$
\frac{\partial w_{t+1}}{\partial \beta_i} \;=\; J_t\,\frac{\partial w_t}{\partial \beta_i} \;-\; \frac{\eta_t}{b}\;\mathbf{1}[i\in B_t]\;\nabla_w L(w_t,z_i),
$$

 with initial condition $\tfrac{\partial w_0}{\partial \beta_i} = 0$. Compute the Jacobian $J_t$ explicitly in terms of the mini-batch Hessian $\widehat{H}_t$ which leads to (17).

**(b)** Solve the recursion by "unrolling" it (i.e. by substituting repeatedly and using (18)) to obtain (20).

**(c)** **(Preconditioned SGD.)** Suppose instead that the optimizer uses a preconditioner $P_t \succ 0$:

$$
w_{t+1}(\beta) \;=\; w_t(\beta) \;-\; \frac{\eta_t}{b}\,P_t\sum_{i\in B_t}\beta_i\,\nabla_w L(w_t(\beta),z_i).
  \tag{22}
$$

 This includes momentum-free Adam and natural gradient methods as special cases (with appropriate $P_t$). Show that the step Jacobian becomes $J_t^{(P)} = I - \eta_t\,P_t\widehat{H}_t$ and that the unrolling formula generalizes to

$$
\frac{\partial w_T(\beta)}{\partial \beta_i}\bigg\rvert_{\beta=\mathbf{1}} \;=\; -\sum_{t=0}^{T-1}\frac{\eta_t}{b}\;\mathbf{1}[i\in B_t]\;J_{(t+1):T}^{(P)}\;P_t\,\nabla_w L(w_t,z_i),
  \tag{23}
$$

 where $J_{(t+1):T}^{(P)} = \prod_{s=t+1}^{T-1}(I - \eta_s P_s\widehat{H}_s)$. The only change is that each gradient is premultiplied by the preconditioner at the step where it appears. What does this say about the effect of using Adam vs. SGD on the attribution of a data point that appears early in training?
feedback-instructions:: The student is on Day 5 (Iliad B.5, Data (Attribution) for Alignment, by Louis Jaburi) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (Route 3: training-dynamics attribution (skim Section 2, then Section 4)). They have attempted Exercise 4.1 (Derivation of the unrolling formula) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START *(a)* Differentiating (16) with respect to $\beta_i$ at $\beta = \mathbf{1}$ via the chain rule:  $$ \begin{aligned}   \frac{\partial w_{t+1}}{\partial \beta_i} &= \frac{\partial w_t}{\partial \beta_i} - \frac{\eta_t}{b}\sum_{j\in B_t}\Bigl[\underbrace{\nabla_w^2 L(w_t,z_j)\,\frac{\partial w_t}{\partial \beta_i}}_{\text{indirect}} + \underbrace{\delta_{ij}\,\nabla_w L(w_t,z_j)}_{\text{direct}}\Bigr] \\   &= \Bigl(I - \frac{\eta_t}{b}\sum_{j\in B_t}\nabla_w^2 L(w_t,z_j)\Bigr)\frac{\partial w_t}{\partial \beta_i} - \frac{\eta_t}{b}\,\mathbf{1}[i\in B_t]\,\nabla_w L(w_t,z_i) \\   &= J_t\,\frac{\partial w_t}{\partial \beta_i} - \frac{\eta_t}{b}\,\mathbf{1}[i\in B_t]\,\nabla_w L(w_t,z_i). \end{aligned} $$   The initial condition is $\partial w_0/\partial \beta_i = 0$ since $w_0$ does not depend on $\beta$.  *(b)* Substituting the recursion repeatedly:  $$ \begin{aligned}   \frac{\partial w_T}{\partial \beta_i} &= J_{T-1}\frac{\partial w_{T-1}}{\partial \beta_i} - \frac{\eta_{T-1}}{b}\,\mathbf{1}[i\in B_{T-1}]\,\nabla_w L(w_{T-1},z_i) \\   &= J_{T-1}\Bigl(J_{T-2}\frac{\partial w_{T-2}}{\partial \beta_i} - \frac{\eta_{T-2}}{b}\,\mathbf{1}[i\in B_{T-2}]\,\nabla_w L(w_{T-2},z_i)\Bigr) \\   &\qquad - \frac{\eta_{T-1}}{b}\,\mathbf{1}[i\in B_{T-1}]\,\nabla_w L(w_{T-1},z_i) \\   &= \cdots = -\sum_{t=0}^{T-1}\frac{\eta_t}{b}\,\mathbf{1}[i\in B_t]\,J_{(t+1):T}\,\nabla_w L(w_t,z_i), \end{aligned} $$   where the last step follows from $\partial w_0/\partial \beta_i = 0$ killing the $J_{0:T}$ term. This is (20).  *(c)* With the preconditioned update (22), the indirect effect picks up the preconditioner in the Hessian term: $J_t^{(P)} = I - (\eta_t/b)\sum_{j\in B_t}P_t\nabla_w^2 L(w_t,z_j) = I - \eta_t P_t \widehat{H}_t$. The direct effect becomes $-(\eta_t/b)\,\mathbf{1}[i\in B_t]\,P_t\nabla_w L(w_t,z_i)$. Unrolling the recursion as in (b) gives (23). The preconditioner $P_t$ at step $t$ acts as a local rescaling of the gradient: Adam's adaptive scaling amplifies gradients in directions with historically small second moments. A datum appearing early in training (when Adam has not yet accumulated accurate statistics) will have its gradient rescaled differently than the same datum appearing later, when $P_t$ has stabilized. This is a concrete mechanism by which optimizer choice affects per-datum attribution. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: c5e1e7f3-fef7-42ed-a11f-eb99ffdd3b27
content::
\## Exercise 4.2: Convergence of unrolling to influence functions

**Exercise 4.2 (Convergence of unrolling to influence functions).**

Consider the SGD update with an interpolated loss that downweights example $z_k$ by $\varepsilon$:

$$
w_{t+1}(\varepsilon) \;=\; w_t(\varepsilon) \;-\; \frac{\eta_t}{b}\sum_{i\in B_t}\bigl(1 - \varepsilon\,\mathbf{1}[i=k]\bigr)\,\nabla_w L(w_t(\varepsilon),z_i),
\tag{34}
$$

 so $\varepsilon = 0$ is the original training run and $\varepsilon = 1/n$ corresponds to removing $z_k$. Define the *response* $r_t := \partial w_t(\varepsilon)/\partial\varepsilon\big|_{\varepsilon=0}$.

$$
\begin{pmatrix} w_{t+1} \\ r_{t+1} \end{pmatrix} \;=\; \underbrace{\begin{pmatrix} I & 0 \\ 0 & J_t \end{pmatrix}}_{\text{propagation}} \begin{pmatrix} w_t \\ r_t \end{pmatrix} \;+\; \underbrace{\begin{pmatrix} -\frac{\eta_t}{b}\sum_{i\in B_t}\nabla_w L(w_t,z_i) \\[4pt] \frac{\eta_t}{b}\,\mathbf{1}[k\in B_t]\,\nabla_w L(w_t,z_k) \end{pmatrix}}_{\text{driving terms}}
\tag{35}
$$

**(a)** **(The response recursion.)** By differentiating (34) with respect to $\varepsilon$ at $\varepsilon = 0$, derive (35), where $J_t = I - \frac{\eta_t}{b}\sum_{i\in B_t}\nabla_w^2 L(w_t,z_i)$ is the step Jacobian from (17). The top row is ordinary SGD; verify that the bottom row is the same recursion as Exercise 4.1(a), but now with stochastic batches. Since the driving terms depend only on $(w_t, r_t)$ and the i.i.d. batch selection $B_t$, the joint process is a Markov chain. Why is this observation useful?

**(b)** **(Deterministic warm-up: full-batch GD.)** As a warm-up, consider full-batch gradient descent with constant learning rate $\eta$ (i.e. $B_t = \{1,\dots,n\}$ for all $t$). Assume training has converged: $w_t \approx w^*$ and $\nabla_w^2 L(w_t) \approx H$ for all $t$ in a window of length $K$. Show that the response over this window satisfies

$$
r_T \;\approx\; -\bigl[I - (I-\eta H)^K\bigr]\,H^{-1}\,\nabla_w L(w^*,z_k).
$$

 *Hint:* Sum the geometric series $\sum_{t=0}^{K-1}(I-\eta H)^t$ using the identity $\sum_{t=0}^{K-1}M^t = (I-M^K)(I-M)^{-1}$.

Take $K\to\infty$ (assuming $\eta < 2/\lambda_{\max}(H)$) and recover the influence function $r_\infty = -H^{-1}\nabla_w L(w^*,z_k) = r_{\mathrm{IF}}$.

**(c)** **(Stochastic case: convergence to IF.)** Now return to SGD with i.i.d. batches and a decaying learning rate satisfying $\sum_t \eta_t = \infty$, $\sum_t \eta_t^2 < \infty$ (the Robbins--Monro conditions). Assume SGD converges to a local minimum $w^*$ with $H = \nabla_w^2 L(w^*)$ positive semidefinite. The continuous-time ODE that the response tracks is

$$
\dot{r}(t) \;=\; -H\,r(t) \;+\; \nabla_w L(w^*,z_k).
  \tag{36}
$$

 (You do not need to prove that SGD tracks this ODE, this follows from standard stochastic approximation theory.)

**i.** Show that the equilibrium of (36) in the column space of $H$ is $r_{\mathrm{IF}} = H^+\nabla_w L(w^*,z_k)$, where $H^+$ is the pseudoinverse. This is the influence function, with $H^+$ in place of $H^{-1}$ because the Hessian may be singular at a local minimum of an overparameterized model.

**ii.** Show that the component of $r(t)$ in the *null space* of $H$ grows linearly: if $P_0$ is the projector onto $\ker(H)$, then $P_0\,r(t) = P_0\,r(0) + t\,P_0\nabla_w L(w^*,z_k)$. Why does this component not converge? Under what condition on $\nabla_w L(w^*,z_k)$ does this runaway term vanish?

The full result (Mlodozeniec et al. (2025), Theorem 2) is: on the set of SGD trajectories that converge to a local minimum, $r_t \to r_{\mathrm{IF}} + r_{\mathrm{NS}}$ almost surely, where $r_{\mathrm{NS}} \in \ker(H)$. The influence function is the limiting response, up to a component in the flat directions of the loss.
feedback-instructions:: The student is on Day 5 (Iliad B.5, Data (Attribution) for Alignment, by Louis Jaburi) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (Route 3: training-dynamics attribution (skim Section 2, then Section 4)). They have attempted Exercise 4.2 (Convergence of unrolling to influence functions) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START *(a)* Differentiating (34) with respect to $\varepsilon$ at $\varepsilon = 0$: the first row is just the SGD update, independent of $\varepsilon$. For the response, the chain rule gives two contributions: the indirect effect through $w_t(\varepsilon)$ picks up the mini-batch Hessian (giving $J_t\,r_t$ as in Exercise 4.1), and the direct effect from the $(1-\varepsilon\,\mathbf{1}[i=k])$ factor contributes $+(\eta_t/b)\,\mathbf{1}[k\in B_t]\,\nabla_w L(w_t,z_k)$. This is (35). Given the current state $(w_t,r_t)$ and the batch selection $B_t$ (which is i.i.d. and independent of history), the next state $(w_{t+1},r_{t+1})$ depends only on $(w_t,r_t)$ --- no earlier states are needed. This is the Markov property.  *(b)* With full-batch GD, $B_t = \{1,\dots,n\}$, the response recursion becomes deterministic: $r_{t+1} = (I-\eta H)r_t + \eta\nabla_w L(w^*,z_k)$. With $r_0 = 0$, unrolling gives $r_K = \eta\sum_{t=0}^{K-1}(I-\eta H)^t\,\nabla_w L(w^*,z_k)$. Using $\sum_{t=0}^{K-1}M^t = (I-M^K)(I-M)^{-1}$ with $M = I-\eta H$:  $$ r_K = [I-(I-\eta H)^K]\,H^{-1}\,\nabla_w L(w^*,z_k). $$   (Note the sign: the interpolation $1-\varepsilon\,\mathbf{1}[i=k]$ downweights $z_k$, so the direct effect has the opposite sign from the $\beta$-upweighting in Exercise 4.1.) Since $\|I-\eta H\| < 1$ when $\eta < 2/\lambda_{\max}(H)$, $(I-\eta H)^K \to 0$ and $r_\infty = H^{-1}\nabla_w L(w^*,z_k) = r_{\mathrm{IF}}$.  *(c)* i. At equilibrium $\dot r = 0$, the ODE (36) gives $Hr_\infty = \nabla_w L(w^*,z_k)$. In the column space of $H$, this has the unique solution $r_{\mathrm{IF}} = H^+\nabla_w L(w^*,z_k)$. (If $H$ is invertible, $H^+ = H^{-1}$ and this is the classical IF.)  ii\. Project the ODE onto $\ker(H)$: $P_0\dot{r}(t) = -P_0 H\,r(t) + P_0\nabla_w L(w^*,z_k) = P_0\nabla_w L(w^*,z_k)$, since $P_0 H = 0$. Integrating: $P_0 r(t) = P_0 r(0) + t\,P_0\nabla_w L(w^*,z_k)$. This grows linearly unless $P_0\nabla_w L(w^*,z_k) = 0$, i.e. unless the per-example gradient has no component in the Hessian null space. The null space of $H$ at a local minimum corresponds to flat directions along the minimum manifold; the response diverges if the perturbation "pushes" along these flat directions, because the optimizer has no restoring force. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: bae9e84e-7e2a-4d80-8a30-6d084619e0f8
content::
\## Exercise 4.3: Stagewise influence in a deep linear network (optional)

**Exercise 4.3 (Stagewise influence in a deep linear network).**

A two-layer linear network $f_W(x) = W_2 W_1 x$ with $W_1, W_2 \in \mathbb{R}^{d\times d}$ is trained on $\{(x_i,y_i)\}_{i=1}^n$ with squared loss. Assume whitened inputs ($\tfrac{1}{n}\sum_i x_i x_i^\top = I$) and, for simplicity, that the input--output cross-covariance $\Sigma_{xy} = \tfrac{1}{n}\sum_i x_i y_i^\top$ is already diagonal with entries $s_1 > s_2 > \cdots > s_d > 0$.[^5]

\##### Dynamics.

Under gradient flow with small balanced initialization, the network's modes evolve independently. The effective weight matrix at time $t$ is $W(t) = \mathrm{diag}(\mathcal{G}_1(t),\dots,\mathcal{G}_d(t))$, where each mode strength follows

$$
\mathcal{G}_k(t) \;=\; \frac{s_k\,e^{2s_k t/\tau}}{e^{2s_k t/\tau} - 1 + s_k/\mathcal{G}_k(0)},
\tag{37}
$$

 with $\mathcal{G}_k(0) \ll s_k$ and time constant $\tau$. Mode $k$ transitions from $\approx 0$ to $\approx s_k$ around time $t_k^* \approx \tfrac{\tau}{2s_k}\log(s_k/\mathcal{G}_k(0))$. Larger singular values saturate first: the network learns dominant structure before fine structure.

\##### Analytic influence.

Now perturb the weight of training example $z_p = (x_p,y_p)$ by $\varepsilon$, so the perturbed cross-covariance is $\Sigma_{xy}(\varepsilon) = \Sigma_{xy} + \varepsilon\,y_p x_p^\top$. Since $\Sigma_{xy}$ is diagonal, the perturbation shifts its eigenvalues and rotates its eigenvectors. The influence of $z_p$ on the weight matrix at time $t$ decomposes as

$$
\mathcal{I}_p(t) \;:=\; \frac{\partial W(t,\varepsilon)}{\partial\varepsilon}\bigg\rvert_{\varepsilon=0} \;=\; A\,\mathcal{G}(t) \;+\; \mathcal{G}'_\varepsilon(t) \;+\; \mathcal{G}(t)\,B,
\tag{38}
$$

 with three terms:

-   $A$ and $B$ are skew-symmetric matrices describing how the perturbation *rotates* the left/right singular bases. Their off-diagonal entries are $A_{jk} = B_{kj} = (y_p)_j(x_p)_k/(s_k - s_j)$ for $j \neq k$.

-   $\mathcal{G}'_\varepsilon(t) = \mathrm{diag}\bigl(g'_t(s_1)\,(y_p)_1(x_p)_1,\;\dots,\;g'_t(s_d)\,(y_p)_d(x_p)_d\bigr)$ encodes the change in mode strengths, where

$$
g'_t(s_k) \;:=\; \frac{\partial\,\mathcal{G}_k(t)}{\partial s_k}
      \tag{39}
$$

 is the sensitivity of the $k$-th mode strength to a change in the corresponding singular value at time $t$.

The influence on the loss of a test example $z_q = (x_q, y_q)$, with residual $r_q(t) = y_q - W(t)x_q$, is

$$
\mathcal{I}(z_p,\,\ell_q)(t) \;=\; -\,r_q(t)^\top\bigl(A\,\mathcal{G}(t) + \mathcal{G}'_\varepsilon(t) + \mathcal{G}(t)\,B\bigr)\,x_q.
\tag{40}
$$

**(a)** **(Three sources of influence.)** Interpret the three terms in (38):

-   $A\,\mathcal{G}(t)$ and $\mathcal{G}(t)\,B$: the perturbation *rotates* the singular bases, mixing already-learned modes into each other. Why are these terms proportional to the current mode strengths $\mathcal{G}(t)$ rather than to their derivatives?

-   $\mathcal{G}'_\varepsilon(t)$: the perturbation *shifts* the singular values, changing how fast each mode is learned. Why does this term involve $g'_t(s_k)$, sensitivity of the dynamics to the singular value, rather than $\mathcal{G}_k(t)$ itself?

**(b)** **(When does influence peak?)** Using the dynamics (37), argue that $g'_t(s_k)$ is peaked around $t \approx t_k^*$ (the transition time of mode $k$). Conclude that the $\mathcal{G}'_\varepsilon$ term, the part of influence that acts through the learning speed of each mode, is concentrated in time around the moment the mode is being learned. Before and after, this contribution is negligible.

*Hint:* Consider the limits $t \ll t_k^*$ (mode not yet learning, $\mathcal{G}_k \approx \mathcal{G}_k(0)$) and $t \gg t_k^*$ (mode saturated, $\mathcal{G}_k \approx s_k$). In both cases, how sensitive is $\mathcal{G}_k$ to a small change in $s_k$?

**(c)** **(Sign flips.)** Consider $d = 2$ with $s_1 \gg s_2$: mode 1 captures a coarse distinction ("animal vs. plant") and mode 2 a fine distinction ("dog vs. cat" within animals). A dog example $z_{\mathrm{dog}}$ and a cat example $z_{\mathrm{cat}}$ share the same mode-1 coordinate but have opposite mode-2 coordinates: $(x_{\mathrm{dog}})_2 = +(x_{\mathrm{cat}})_2$. Using (40), argue that the influence of $z_{\mathrm{dog}}$ on a cat test loss can change sign during training: positive while mode 1 is being learned (shared structure), negative after mode 2 is learned (competing structure). At what time is the sign flip sharpest?
optional:: true
feedback-instructions:: The student is on Day 5 (Iliad B.5, Data (Attribution) for Alignment, by Louis Jaburi) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (Route 3: training-dynamics attribution (skim Section 2, then Section 4)). They have attempted Exercise 4.3 (Stagewise influence in a deep linear network) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START *(a)* The $A\mathcal{G}(t)$ and $\mathcal{G}(t)B$ terms describe how the perturbation rotates the singular basis. A rotation mixes already-learned modes into each other, so its effect on the weight matrix is proportional to the current mode strengths: if mode $k$ has not yet been learned ($\mathcal{G}_k \approx 0$), rotating its basis direction contributes nothing to $W(t)$. The $\mathcal{G}'_\varepsilon(t)$ term, by contrast, acts through the learning *dynamics*: perturbing $s_k$ changes the speed at which mode $k$ is learned, and this matters precisely when the dynamics are sensitive to $s_k$ --- not when $\mathcal{G}_k(t)$ is large or small per se, but when $\mathcal{G}_k(t)$ is *changing rapidly* as a function of $s_k$. This is why the derivative $g'_t(s_k) = \partial\mathcal{G}_k(t)/\partial s_k$ appears rather than $\mathcal{G}_k(t)$ itself.  *(b)* From (37), $\mathcal{G}_k(t) = s_k e^{2s_k t/\tau}/(e^{2s_k t/\tau} - 1 + s_k/\mathcal{G}_k(0))$. For $t \ll t_k^*$: $e^{2s_k t/\tau} \approx 1$, so $\mathcal{G}_k \approx \mathcal{G}_k(0)$ regardless of $s_k$ --- the mode hasn't started learning yet, and a small change in $s_k$ makes no difference, so $g'_t(s_k) \approx 0$. For $t \gg t_k^*$: $e^{2s_k t/\tau} \gg s_k/\mathcal{G}_k(0)$, so $\mathcal{G}_k \approx s_k$ and $g'_t(s_k) \approx 1$ --- but the *residual* in mode $k$ is also $\approx 0$, so this term's contribution to the loss influence (40) is negligible. The product $g'_t(s_k) \times (\text{residual in mode } k)$ is peaked around $t \approx t_k^*$, when the mode is in transition: the dynamics are maximally sensitive to $s_k$ *and* the residual is still nonzero.  *(c)* Write $x_{\mathrm{dog}} = (\alpha, +\delta)$ and $x_{\mathrm{cat}} = (\alpha, -\delta)$, where $\alpha$ is the shared mode-1 component and $\pm\delta$ are opposite mode-2 components (since $\Sigma_{xy}$ is diagonal, the standard basis is the singular basis). During mode-1 learning ($t \approx t_1^*$, mode 2 not yet active): the residual of the cat test example has a large mode-1 component, and $z_{\mathrm{dog}}$'s perturbation increases $s_1$ (via $(y_{\mathrm{dog}})_1 (x_{\mathrm{dog}})_1 > 0$), accelerating mode-1 learning. This reduces the cat test loss --- positive influence. After mode-2 learning ($t \approx t_2^*$): the cat's residual is now dominated by mode 2, and $z_{\mathrm{dog}}$'s mode-2 perturbation has the wrong sign for the cat (because $(x_{\mathrm{dog}})_2$ and $(x_{\mathrm{cat}})_2$ have opposite signs). This increases the cat test loss --- negative influence. The sign flip is sharpest around $t_2^*$, when $g'_t(s_2)$ peaks and the mode-2 residual transitions from large to small. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".


