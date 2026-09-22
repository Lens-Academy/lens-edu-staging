---
id: '3e494990-3893-4aab-9f4e-64ba4601a887'
title: "Checkpoint 1: landscape and gradient flow"
tldr: "In a deep linear network every critical point is a saddle or a global minimum, and gradient flow conserves the balance between layers."
summary_for_tutor: "Day 4 checkpoint 1 of 3: Sections 3 and 4 of the Iliad B.4 worksheet. Core exercises 2.1, 2.3, 3.1, 3.2, 3.7; the others optional. Official solutions are in each tutor brief."
authors:
  - Guillaume Corlouer
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/training-dynamics/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 70
tutor_minutes: 20
---

#### Text
content::
In the worksheet, read **Section 2** (setup and notation), **Section 3** (loss landscape geometry) and **Section 4** (gradient flow and conserved quantities). The exercises below marked optional can be skipped.

#### Question: Open
id:: c93c3e90-f3fb-4f7b-a884-aa9ef10e89c4
content::
\## Exercise 3.1: Diagonal decomposition

**Exercise 3.1 (Diagonal decomposition).**

Consider the **diagonal** case: $d_0 = d_1 = \cdots = d_L = d$, and the teacher is diagonal, $M = \text{diag}(s_1, \ldots, s_d)$, with $s_1 > s_2 > \cdots > s_d > 0$. Restrict attention to diagonal weight matrices $W_l = \text{diag}(w_l^{(1)}, \ldots, w_l^{(d)})$. Show that the loss decomposes into $d$ independent scalar problems:

$$
\mathcal{L} = \frac{1}{2}\sum_{\alpha=1}^d \left(s_\alpha - \prod_{l=1}^L w_l^{(\alpha)}\right)^2
$$
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 3.1 (Diagonal decomposition) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START When all $W_l$ are diagonal, the product $W = W_L \cdots W_1$ is also diagonal with entries $(W)_{\alpha\alpha} = \prod_{l=1}^L w_l^{(\alpha)}$. The teacher $M$ is diagonal with entries $s_\alpha$. Then:  $$ \mathcal{L} = \frac{1}{2}\|M - W\|_F^2 = \frac{1}{2}\sum_{\alpha=1}^d (s_\alpha - (W)_{\alpha\alpha})^2 = \frac{1}{2}\sum_{\alpha=1}^d \left(s_\alpha - \prod_{l=1}^L w_l^{(\alpha)}\right)^2 $$  Since the different modes $\alpha$ share no parameters, the loss decomposes into $d$ independent scalar problems. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 432556fe-9232-4364-96ef-48ec5fbcac88
content::
\## Exercise 3.2: Scalar critical points (optional)

**Exercise 3.2 (Scalar critical points).**

For a single scalar mode with target $s > 0$, find all first-order critical points of $\ell(w_1, w_2) = \frac{1}{2}(s - w_1 w_2)^2$ at depth $L = 2$. Show that the critical points are:

-   The global minimum manifold: $w_1 w_2 = s$

-   The origin: $w_1 = w_2 = 0$

Classify the origin as a saddle point by computing the Hessian $H$ of $\ell$ at $(0,0)$ and showing it has both positive and negative eigenvalues.

*Hint*: Write the gradient equations.
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 3.2 (Scalar critical points) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START For $L = 2$, the gradient equations are:  $$ \frac{\partial \ell}{\partial w_1} = -(s - w_1 w_2)\,w_2 = 0, \qquad \frac{\partial \ell}{\partial w_2} = -(s - w_1 w_2)\,w_1 = 0 $$  **Case 1**: $s - w_1 w_2 = 0$, i.e. $w_1 w_2 = s$. This is the global minimum manifold (a hyperbola $w_2 = s/w_1$) with $\ell = 0$.  **Case 2**: If $s - w_1 w_2 \neq 0$, then the first equation requires $w_2 = 0$ and the second requires $w_1 = 0$. (For instance, if $w_2 \neq 0$ and $w_1 = 0$, the first equation gives $-s\,w_2 = 0$, which contradicts $s > 0$ and $w_2 \neq 0$.) So the only other critical point is $w_1 = w_2 = 0$.  The Hessian at $(0,0)$. We need the second derivatives of $\ell = \frac{1}{2}(s - w_1 w_2)^2$:  $$ \begin{aligned} \frac{\partial^2 \ell}{\partial w_1^2} &= w_2^2, \qquad \frac{\partial^2 \ell}{\partial w_2^2} = w_1^2, \\ \frac{\partial^2 \ell}{\partial w_1 \partial w_2} &= -(s - w_1 w_2) + w_1 w_2 = 2w_1 w_2 - s \end{aligned} $$  At $(0,0)$:  $$ H = \begin{pmatrix} 0 & -s \\ -s & 0 \end{pmatrix} $$  The eigenvalues are $\pm s$. Since $s > 0$, $H$ has one positive and one negative eigenvalue. The origin is a **strict saddle point**. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 99c1a314-a6e6-4967-bab9-a7d4df76bc01
content::
\## Exercise 3.3: Critical-point structure

**Exercise 3.3 (Critical-point structure).**

Achour et al. (Achour, Malgouyres, and Gerchinovitz 2024) show that every first-order critical point $\theta = (W_1, \ldots, W_L)$ satisfies: there exists a subset $S \subseteq \{1, \ldots, d\}$ such that

$$
W = W_L \cdots W_1 = P_S\, M
$$

where $P_S = U_S U_S^\top$ is the orthogonal projector onto the span of the left singular vectors $\{u_\alpha\}_{\alpha \in S}$ of $M$. For the diagonal case $M = \text{diag}(s_1, \ldots, s_d)$, write the value of the loss at the critical point corresponding to $S = \{1, \ldots, r\}$ with $r < d$.
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 3.3 (Critical-point structure) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START At the critical point $W = P_S M$ with $S = \{1, \ldots, r\}$, the student retains only the first $r$ modes: $W = \text{diag}(s_1, \ldots, s_r, 0, \ldots, 0)$. The loss is:  $$ \mathcal{L} = \frac{1}{2}\|M - P_S M\|_F^2 = \frac{1}{2}\sum_{\alpha \notin S} s_\alpha^2 = \frac{1}{2}\sum_{\alpha=r+1}^d s_\alpha^2 $$  This is strictly positive whenever $r < d$ (since all $s_\alpha > 0$), so these are not global minima. By the Hessian analysis (extending Exercise 3.2), the direction corresponding to "switching on" a missing mode $\alpha \notin S$ is a descent direction, making these critical points saddle points. All critical points with $|S| = d$ have $W = M$ and $\mathcal{L} = 0$: these are the global minima. Therefore there are **no spurious local minima** --- every local minimum is global. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 53a20160-f585-4a67-bef1-c8d10902c04e
content::
\## Exercise 3.4: Symmetry of the global minima (optional)

**Exercise 3.4 (Symmetry of the global minima).**

The group $GL_h := GL_{d_1} \times \cdots \times GL_{d_{L-1}}$ acts on the weights by:

$$
(W_1, \ldots, W_L) \mapsto (g_1 W_1,\; g_2 W_2 g_1^{-1},\; \ldots,\; W_L g_{L-1}^{-1})
$$

Verify that the student map $\mu(\theta) = W_L \cdots W_1$ is invariant under this action: $\mu(g \cdot \theta) = \mu(\theta)$.
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 3.4 (Symmetry of the global minima) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Under the group action:  $$ \mu(g \cdot \theta) = W_L g_{L-1}^{-1} \cdot g_{L-1} W_{L-1} g_{L-2}^{-1} \cdot \ldots \cdot g_1 W_1 = W_L W_{L-1} \cdots W_1 = \mu(\theta) $$  All $g_l$ and $g_l^{-1}$ factors cancel telescopically. This means every parameter point in the orbit $\mathcal{O}_\theta = GL_h \cdot \theta$ maps to the same student $W$. $\square$  For the dimension of the set of global minima, this invariance means the following. The global minima form the fiber $\mu^{-1}(M)$, which contains the entire orbit $GL_h \cdot \theta^*$ for any global minimizer $\theta^*$. The orbit has dimension $\sum_{l=1}^{L-1} d_l^2$ (the dimension of $GL_h$), so the set of global minima is a **continuous manifold of very high dimension** --- far from being isolated points. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: c8c84830-c7d1-492c-9694-64a8d77c89bf
content::
\## Exercise 4.1: Gradient-flow equations

**Exercise 4.1 (Gradient-flow equations).**

For a two-layer DLN ($L=2$), the loss is given by $\mathcal{L} = \frac{1}{2}\|M - W_2 W_1\|_F^2$. Assume that each weight matrix $W_i$ is diagonal. Derive the gradient flow equations for each layer. In particular, show that:

$$
\dot{W}_1 = W_2^\top(M - W_2 W_1), \qquad \dot{W}_2 = (M - W_2 W_1) W_1^\top
$$

*Note*: these equations also hold for general (non-diagonal) $W_1$ and $W_2$.
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 4.1 (Gradient-flow equations) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START We have $\mathcal{L} = \frac{1}{2}\|M - W_2 W_1\|_F^2 = \frac{1}{2}\text{Tr}\left[(M - W_2 W_1)^\top(M - W_2 W_1)\right]$.  **General matrix derivation.** Expand:  $$ \mathcal{L} = \frac{1}{2}\text{Tr}(M^\top M) - \text{Tr}(M^\top W_2 W_1) + \frac{1}{2}\text{Tr}(W_1^\top W_2^\top W_2 W_1) $$  Differentiating with respect to $W_1$, using $\frac{\partial}{\partial A}\text{Tr}(B^\top A) = B$ and $\frac{\partial}{\partial A}\text{Tr}(A^\top C A) = (C + C^\top)A$:  $$ \nabla_{W_1}\mathcal{L} = -W_2^\top M + W_2^\top W_2 W_1 = -W_2^\top(M - W_2 W_1) $$  So $\dot{W}_1 = -\nabla_{W_1}\mathcal{L} = W_2^\top(M - W_2 W_1)$.  Similarly, $\nabla_{W_2}\mathcal{L} = -(M - W_2 W_1)W_1^\top$, giving $\dot{W}_2 = (M - W_2 W_1)W_1^\top$.  **Diagonal shortcut.** For diagonal matrices $W_1 = \text{diag}(a_\alpha)$, $W_2 = \text{diag}(b_\alpha)$, $M = \text{diag}(s_\alpha)$: the loss decouples as $\mathcal{L} = \frac{1}{2}\sum_\alpha(s_\alpha - b_\alpha a_\alpha)^2$. Then $\dot{a}_\alpha = -\partial\mathcal{L}/\partial a_\alpha = b_\alpha(s_\alpha - b_\alpha a_\alpha)$ and $\dot{b}_\alpha = a_\alpha(s_\alpha - b_\alpha a_\alpha)$, which is the diagonal version of the matrix equations above. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 71386f28-606f-46d2-a2d8-762523883d5f
content::
\## Exercise 4.2: Balancedness is conserved

**Exercise 4.2 (Balancedness is conserved).**

Define the **balancedness matrix**:

$$
G := W_2^\top W_2 - W_1 W_1^\top
$$

Show that $G$ is conserved under the gradient flow, i.e. $\dot{G} = 0$. In other words, gradient flow is constrained to the balanced manifold

$$
\mathcal{M}_{\beta}
    :=
    \{\theta\in\Omega\mid
    W_{\ell+1}^{\top}W_{\ell+1}
    -
    W_{\ell}W_{\ell}^{\top}
    =
    \beta_\ell,\;
    \ell=1,\ldots,L-1\}.
$$

*Hint*: Compute $\dot{G}$, substitute the gradient flow equations and verify that the terms cancel pairwise.
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 4.2 (Balancedness is conserved) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Let $E := M - W_2 W_1$ denote the residual. Compute:  $$ \dot{G} = \dot{W}_2^\top W_2 + W_2^\top \dot{W}_2 - \dot{W}_1 W_1^\top - W_1 \dot{W}_1^\top $$  Substitute the gradient flow equations. Using $\dot{W}_2 = E W_1^\top$ and $\dot{W}_1 = W_2^\top E$:  $$ \dot{W}_2^\top W_2 = (E W_1^\top)^\top W_2 = W_1 E^\top W_2 $$  $$ W_2^\top \dot{W}_2 = W_2^\top E W_1^\top $$  $$ \dot{W}_1 W_1^\top = W_2^\top E W_1^\top $$  $$ W_1 \dot{W}_1^\top = W_1(W_2^\top E)^\top = W_1 E^\top W_2 $$  Therefore:  $$ \dot{G} = W_1 E^\top W_2 + W_2^\top E W_1^\top - W_2^\top E W_1^\top - W_1 E^\top W_2 = 0 $$  The terms cancel pairwise. $G$ is conserved. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 5a77a90a-ec66-48c6-b61b-b8a1df07a102
content::
\## Exercise 4.3: Function-space velocity (optional)

**Exercise 4.3 (Function-space velocity).**

Compute $\dot{W} := \frac{d}{dt}(W_2 W_1)$ using the gradient flow equations from Exercise 4.1. Show that:

$$
\dot{W} = (M - W)\, W_1^\top W_1 + W_2 W_2^\top\, (M - W)
$$
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 4.3 (Function-space velocity) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Apply the product rule:  $$ \dot{W} = \dot{W}_2 W_1 + W_2 \dot{W}_1 = (M - W_2 W_1)W_1^\top \cdot W_1 + W_2 \cdot W_2^\top(M - W_2 W_1) $$  Writing $W = W_2 W_1$:  $$ \dot{W} = (M - W)\,W_1^\top W_1 + W_2 W_2^\top\,(M - W) \qquad \square $$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 5ee6b3f4-051a-4e9d-bd50-f571a933b032
content::
\## Exercise 4.4: $W_1^\top W_1$ in terms of $W$ (optional)

**Exercise 4.4 ($W_1^\top W_1$ in terms of $W$).**

We now need to express $W_1^\top W_1$ and $W_2 W_2^\top$ in terms of $W = W_2 W_1$. Show that:

$$
W_1^\top W_1 = (W^\top W)^{1/2}
$$
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 4.4 ($W_1^\top W_1$ in terms of $W$) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Balancedness gives $W_2^\top W_2 = W_1 W_1^\top$, so  $$ W^\top W = W_1^\top \left(W_2^\top W_2\right) W_1 = W_1^\top \left(W_1 W_1^\top\right) W_1 = \left(W_1^\top W_1\right)^2 $$  Both $W^\top W$ and $W_1^\top W_1$ are positive semidefinite. A positive semidefinite matrix has a unique positive semidefinite square root, so it follows that  $$ (W^\top W)^{1/2} = W_1^\top W_1 \qquad \square $$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 9f8efa34-9c52-412a-b553-c61c160faa0b
content::
\## Exercise 4.5: $W_2 W_2^\top$ in terms of $W$ (optional)

**Exercise 4.5 ($W_2 W_2^\top$ in terms of $W$).**

Similarly, show that $W_2 W_2^\top = (W W^\top)^{1/2}$.
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 4.5 ($W_2 W_2^\top$ in terms of $W$) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Analogous to Exercise 4.4. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: c181e939-8891-4f8d-b694-637871ed1fc1
content::
\## Exercise 4.6: The balanced function-space ODE (optional)

**Exercise 4.6 (The balanced function-space ODE).**

Substitute the results of Exercise 4.4 and Exercise 4.5 into Exercise 4.3 to obtain:

$$
\dot{W} = (W W^\top)^{1/2}(M - W) + (M - W)(W^\top W)^{1/2}
$$
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 4.6 (The balanced function-space ODE) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Substituting into Exercise 4.3:  $$ \dot{W} = (M - W)(W^\top W)^{1/2} + (WW^\top)^{1/2}(M - W) \qquad \square $$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 4afd0eba-1922-40bf-b4f6-d2a0c8472454
content::
\## Exercise 4.7: The NTK operator

**Exercise 4.7 (The NTK operator).**

Define the NTK operator for $L = 2$ as:

$$
K[F] := (WW^\top)^{1/2}\, F + F\, (W^\top W)^{1/2}
$$

Show that the gradient flow from Exercise 4.6 can be written as $\dot{W} = K[M - W]$.

It turns out that this result generalizes to depth $L$ on the balanced manifold:

$$
\dot{W} = \sum_{k=1}^{L} (WW^\top)^{\frac{L-k}{L}} (M - W) (W^\top W)^{\frac{k-1}{L}}
$$

 This is the NTK equation in the case of DLNs. The NTK equation is a gradient flow in function space with NTK being a preconditioning operator for the gradient.
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 3 and 4)). They have attempted Exercise 4.7 (The NTK operator) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START With $F = M - W$, the equation from Exercise 4.6 reads:  $$ \dot{W} = (WW^\top)^{1/2}\,F + F\,(W^\top W)^{1/2} = K[F] = K[M - W] \qquad \square $$  The general depth-$L$ result $\dot{W} = \sum_{k=1}^{L}(WW^\top)^{(L-k)/L}(M-W)(W^\top W)^{(k-1)/L}$ follows from the same approach applied to the $L$-fold balanced conditions $W_{l+1}^\top W_{l+1} = W_l W_l^\top$ for all $l$. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".


