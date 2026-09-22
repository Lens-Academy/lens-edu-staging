---
id: '3e494990-3893-4aab-9f4e-64ba4601a887'
title: "Checkpoint 1: landscape and gradient flow"
tldr: "In a deep linear network every critical point is a saddle or a global minimum, and gradient flow conserves the balance between layers."
summary_for_tutor: "Day 4 checkpoint 1 of 3: Sections 2 and 3 of the Iliad B.4 worksheet. Core exercises 2.1, 2.3, 3.1, 3.2, 3.7; the others optional. Official solutions are in each tutor brief."
authors:
  - Guillaume Corlouer
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/training-dynamics/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 70
tutor_minutes: 20
---

#### Text
content::
In the worksheet, read **Section 1** (setup and notation), **Section 2** (loss landscape geometry) and **Section 3** (gradient flow and conserved quantities). The exercises below marked optional can be skipped.

#### Question: Open
id:: 2367dead-1673-4089-aa07-0c8caf1856fb
content::
\## Exercise 2.1: Diagonal decomposition

**Exercise 2.1 (Diagonal decomposition).** Consider the **diagonal** case: $d_{0} = d_{1} = \cdots = d_{L} = d$, and the teacher is diagonal, $M = \text{diag}(s_{1}, \ldots, s_{d})$, with $s_{1} > s_{2} > \cdots > s_{d} > 0$. Restrict attention to diagonal weight matrices $W_{l} = \text{diag}(w_{l}^{(1)}, \ldots, w_{l}^{(d)})$. Show that the loss decomposes into $d$ independent scalar problems:

$$
\mathcal{L}= \frac{1}{2}\sum_{\alpha=1}^{d} \left(s_{\alpha} - \prod_{l=1}^{L} w_{l}^{(\alpha)}\right)^{2}
$$
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 2.1 (Diagonal decomposition) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START When all $W_{l}$ are diagonal, the product $W = W_{L} \cdots W_{1}$ is also diagonal with entries $(W)_{\alpha\alpha}= \prod_{l=1}^{L} w_{l}^{(\alpha)}$. The teacher $M$ is diagonal with entries $s_{\alpha}$. Then:  $$ \mathcal{L}= \frac{1}{2}\|M - W\|_{F}^{2} = \frac{1}{2}\sum_{\alpha=1}^{d} (s_{\alpha} - (W)_{\alpha\alpha})^{2} = \frac{1}{2}\sum_{\alpha=1}^{d} \left(s_{\alpha} - \prod_{l=1}^{L} w_{l}^{(\alpha)}\right)^{2} $$  Since the different modes $\alpha$ share no parameters, the loss decomposes into $d$ independent scalar problems. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 1a447bdd-b34b-4f20-8a96-42f4f7df070d
content::
\## Exercise 2.2: Scalar critical points (optional)

**Exercise 2.2 (Scalar critical points).** For a single scalar mode with target $s > 0$, find all first-order critical points of $\ell(w_{1}, w_{2}) = \frac{1}{2}(s - w_{1} w_{2})^{2}$ at depth $L = 2$. Show that the critical points are:

- The global minimum manifold: $w_{1} w_{2} = s$
- The origin: $w_{1} = w_{2} = 0$

Classify the origin as a saddle point by computing the Hessian $H$ of $\ell$ at $(0,0)$ and showing it has both positive and negative eigenvalues.

*Hint*: Write the gradient equations
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 2.2 (Scalar critical points) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START For $L = 2$, the gradient equations are:  $$ \frac{\partial \ell}{\partial w_{1}}= -(s - w_{1} w_{2})\,w_{2} = 0, \qquad \frac{\partial \ell}{\partial w_{2}}= -(s - w_{1} w_{2})\,w_{1} = 0 $$  **Case 1**: $s - w_{1} w_{2} = 0$, i.e. $w_{1} w_{2} = s$. This is the global minimum manifold (a hyperbola $w_{2} = s/w_{1}$) with $\ell = 0$.  **Case 2**: If $s - w_{1} w_{2} \neq 0$, then the first equation requires $w_{2} = 0$ and the second requires $w_{1} = 0$. (For instance, if $w_{2} \neq 0$ and $w_{1} = 0$, the first equation gives $-s\,w_{2} = 0$, which contradicts $s > 0$ and $w_{2} \neq 0$.) So the only other critical point is $w_{1} = w_{2} = 0$.  The Hessian at $(0,0)$. We need the second derivatives of $\ell = \frac{1}{2}(s - w_{1} w_{2})^{2}$:  $$ \frac{\partial^{2} \ell}{\partial w_{1}^{2}}= w_{2}^{2}, \qquad \frac{\partial^{2} \ell}{\partial w_{2}^{2}}= w_{1}^{2}, \qquad \frac{\partial^{2} \ell}{\partial w_{1} \partial w_{2}}= -(s - w_{1} w_{2}) + w_{1} w_{2} = 2w_{1} w_{2} - s $$  At $(0,0)$:  $$ H = \begin{pmatrix}0 & -s \\ -s & 0\end{pmatrix} $$  The eigenvalues are $\pm s$. Since $s > 0$, $H$ has one positive and one negative eigenvalue. The origin is a **strict saddle point**. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: e38671ad-116e-44a6-85c0-d372a332973b
content::
\## Exercise 2.3: Critical-point structure

**Exercise 2.3 (Critical-point structure).** Achour et al. (Achour et al. 2024) show that every first-order critical point $\theta = (W_{1}, \ldots, W_{L})$ satisfies: there exists a subset $S \subseteq \{1, \ldots, d\}$ such that

$$
W = W_{L} \cdots W_{1} = P_{S}\, M
$$

where $P_{S} = U_{S} U_{S}^{\top}$ is the orthogonal projector onto the span of the left singular vectors $\{u_{\alpha}\}_{\alpha \in S}$ of $M$. For the diagonal case $M = \text{diag}(s_{1}, \ldots, s_{d})$, write the value of the loss at the critical point corresponding to $S = \{1, \ldots, r\}$ with $r < d$.
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 2.3 (Critical-point structure) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START At the critical point $W = P_{S} M$ with $S = \{1, \ldots, r\}$, the student retains only the first $r$ modes: $W = \text{diag}(s_{1}, \ldots, s_{r}, 0, \ldots, 0)$. The loss is:  $$ \mathcal{L}= \frac{1}{2}\|M - P_{S} M\|_{F}^{2} = \frac{1}{2}\sum_{\alpha \notin S}s_{\alpha}^{2} = \frac{1}{2}\sum_{\alpha=r+1}^{d} s_{\alpha}^{2} $$  This is strictly positive whenever $r < d$ (since all $s_{\alpha} > 0$), so these are not global minima. By the Hessian analysis (extending Exercise 2.2), the direction corresponding to "switching on" a missing mode $\alpha \notin S$ is a descent direction, making these critical points saddle points. All critical points with $|S| = d$ have $W = M$ and $\mathcal{L}= 0$: these are the global minima. Therefore there are **no spurious local minima**  -  every local minimum is global. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: efa07a73-6bcc-437f-9186-08dbde098606
content::
\## Exercise 2.4: Symmetry of the global minima (optional)

**Exercise 2.4 (Symmetry of the global minima).** The group $GL_{h} := GL_{d_1}\times \cdots \times GL_{d_{L-1}}$ acts on the weights by:

$$
(W_{1}, \ldots, W_{L}) \mapsto (g_{1} W_{1},\; g_{2} W_{2} g_{1}^{-1},\; \ldots,\; W_{L} g_{L-1}^{-1})
$$

Verify that the student map $\mu(\theta) = W_{L} \cdots W_{1}$ is invariant under this action: $\mu(g \cdot \theta) = \mu(\theta)$. What does this imply about the dimension of the set of global minima in parameter space?
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 2.4 (Symmetry of the global minima) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Under the group action:  $$ \mu(g \cdot \theta) = W_{L} g_{L-1}^{-1}\cdot g_{L-1}W_{L-1}g_{L-2}^{-1}\cdot \ldots \cdot g_{1} W_{1} = W_{L} W_{L-1}\cdots W_{1} = \mu(\theta) $$  All $g_{l}$ and $g_{l}^{-1}$ factors cancel telescopically. This means every parameter point in the orbit $\mathcal{O}_{\theta} = GL_{h} \cdot \theta$ maps to the same student $W$. The global minima form the fiber $\mu^{-1}(M)$, which contains the entire orbit $GL_{h} \cdot \theta^{*}$ for any global minimizer $\theta^{*}$. The orbit has dimension $\sum_{l=1}^{L-1}d_{l}^{2}$ (the dimension of $GL_{h}$), so the set of global minima is a **continuous manifold of very high dimension**  -  far from being isolated points. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 787933f6-020d-4e6a-866b-f264908c9979
content::
\## Exercise 3.1: Gradient-flow equations

**Exercise 3.1 (Gradient-flow equations).** For a two-layer diagonal DLN ($L=2$) with loss $\mathcal{L}= \frac{1}{2}\|M - W_{2} W_{1}\|_{F}^{2}$, assume that each weight matrix $W_{i}$ is a diagonal matrix and whitened inputs. Derive the gradient flow equations for each layer. Show that:

$$
\dot{W}_{1} = W_{2}^{\top}(M - W_{2} W_{1}), \qquad \dot{W}_{2} = (M - W_{2} W_{1}) W_{1}^{\top}
$$
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 3.1 (Gradient-flow equations) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START We have $\mathcal{L}= \frac{1}{2}\|M - W_{2} W_{1}\|_{F}^{2} = \frac{1}{2}\text{Tr}\left[(M - W_{2} W_{1})^{\top}(M - W_{2} W_{1})\right]$.  **General matrix derivation.** Expand:  $$ \mathcal{L}= \frac{1}{2}\text{Tr}(M^{\top} M) - \text{Tr}(M^{\top} W_{2} W_{1}) + \frac{1}{2}\text{Tr}(W_{1}^{\top} W_{2}^{\top} W_{2} W_{1}) $$  Differentiating with respect to $W_{1}$, using $\frac{\partial}{\partial A}\text{Tr}(B^{\top} A) = B$ and $\frac{\partial}{\partial A}\text{Tr}(A^{\top} C A) = (C + C^{\top})A$:  $$ \nabla_{W_1}\mathcal{L}= -W_{2}^{\top} M + W_{2}^{\top} W_{2} W_{1} = -W_{2}^{\top}(M - W_{2} W_{1}) $$  So $\dot{W}_{1} = -\nabla_{W_1}\mathcal{L}= W_{2}^{\top}(M - W_{2} W_{1})$.  Similarly, $\nabla_{W_2}\mathcal{L}= -(M - W_{2} W_{1})W_{1}^{\top}$, giving $\dot{W}_{2} = (M - W_{2} W_{1})W_{1}^{\top}$.  **Diagonal shortcut.** For diagonal matrices $W_{1} = \text{diag}(a_{\alpha})$, $W_{2} = \text{diag}(b_{\alpha})$, $M = \text{diag}(s_{\alpha})$: the loss decouples as $\mathcal{L}= \frac{1}{2}\sum_{\alpha}(s_{\alpha} - b_{\alpha} a_{\alpha})^{2}$. Then $\dot{a}_{\alpha} = -\partial\mathcal{L}/\partial a_{\alpha} = b_{\alpha}(s_{\alpha} - b_{\alpha} a_{\alpha})$ and $\dot{b}_{\alpha} = a_{\alpha}(s_{\alpha} - b_{\alpha} a_{\alpha})$, which is the diagonal version of the matrix equations above. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: ca9df06c-9200-4ba1-8fa7-6abbc769e026
content::
\## Exercise 3.2: Balancedness is conserved

**Exercise 3.2 (Balancedness is conserved).** Define the **balancedness matrix**:

$$
G := W_{2}^{\top} W_{2} - W_{1} W_{1}^{\top}
$$

Show that $G$ is conserved under the gradient flow, i.e. $\dot{G}= 0$. In other words, gradient flow is constrained on the balanced manifold

$$
\mathcal{M}_{\beta}:= \{\theta\in\Omega\mid W_{\ell+1}^{\top}W_{\ell+1}- W_{\ell}W_{\ell}^{\top}= \beta_{\ell},\; \ell=1,\ldots,L-1\}.
$$

*Hint*: Compute $\dot{G}$, substitute the gradient flow equations and verify that the terms cancel pairwise.
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 3.2 (Balancedness is conserved) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Let $E := M - W_{2} W_{1}$ denote the residual. Compute:  $$ \dot{G}= \dot{W}_{2}^{\top} W_{2} + W_{2}^{\top} \dot{W}_{2} - \dot{W}_{1} W_{1}^{\top} - W_{1} \dot{W}_{1}^{\top} $$  Substitute the gradient flow equations. Using $\dot{W}_{2} = E W_{1}^{\top}$ and $\dot{W}_{1} = W_{2}^{\top} E$:  $$ \dot{W}_{2}^{\top} W_{2} = (E W_{1}^{\top})^{\top} W_{2} = W_{1} E^{\top} W_{2} $$  $$ W_{2}^{\top} \dot{W}_{2} = W_{2}^{\top} E W_{1}^{\top} $$  $$ \dot{W}_{1} W_{1}^{\top} = W_{2}^{\top} E W_{1}^{\top} $$  $$ W_{1} \dot{W}_{1}^{\top} = W_{1}(W_{2}^{\top} E)^{\top} = W_{1} E^{\top} W_{2} $$  Therefore:  $$ \dot{G}= W_{1} E^{\top} W_{2} + W_{2}^{\top} E W_{1}^{\top} - W_{2}^{\top} E W_{1}^{\top} - W_{1} E^{\top} W_{2} = 0 $$  The terms cancel pairwise. $G$ is conserved. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: e6a3453a-3a62-4603-bb0a-dc7b303861de
content::
\## Exercise 3.3: Function-space velocity (optional)

**Exercise 3.3 (Function-space velocity).** Compute $\dot{W}:= \frac{d}{dt}(W_{2} W_{1})$ using the gradient flow equations from Exercise 3.1. Show that:

$$
\dot{W}= (M - W)\, W_{1}^{\top} W_{1} + W_{2} W_{2}^{\top}\, (M - W)
$$
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 3.3 (Function-space velocity) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Apply the product rule:  $$ \dot{W}= \dot{W}_{2} W_{1} + W_{2} \dot{W}_{1} = (M - W_{2} W_{1})W_{1}^{\top} \cdot W_{1} + W_{2} \cdot W_{2}^{\top}(M - W_{2} W_{1}) $$  Writing $W = W_{2} W_{1}$:  $$ \dot{W}= (M - W)\,W_{1}^{\top} W_{1} + W_{2} W_{2}^{\top}\,(M - W) \qquad \square $$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: d0350b43-9e71-4cce-942d-5f82f364444d
content::
\## Exercise 3.4: $W_{1}^{\top}W_{1}$ in terms of $W$ (optional)

**Exercise 3.4 ($W_{1}^{\top}W_{1}$ in terms of $W$).** We now need to express $W_{1}^{\top} W_{1}$ and $W_{2} W_{2}^{\top}$ in terms of $W = W_{2} W_{1}$. For simplicity, assume that the weight matrices $W_{l}$ are diagonal. Show that:

$$
W_{1}^{\top} W_{1} = (W^{\top} W)^{1/2}
$$
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 3.4 ($W_{1}^{\top}W_{1}$ in terms of $W$) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START For diagonal matrices, $W_{1} = \text{diag}(a_{\alpha})$ and $W_{2} = \text{diag}(b_{\alpha})$ with $W = \text{diag}(a_{\alpha} b_{\alpha})$. Balancedness gives $b_{\alpha}^{2} = a_{\alpha}^{2}$ for each $\alpha$, i.e. $|b_{\alpha}| = |a_{\alpha}|$ (with matching signs for positive entries).  Now $W_{1}^{\top} W_{1} = \text{diag}(a_{\alpha}^{2})$ and $W^{\top} W = \text{diag}(a_{\alpha}^{2} b_{\alpha}^{2})$. Using $b_{\alpha}^{2} = a_{\alpha}^{2}$:  $$ W^{\top} W = \text{diag}(a_{\alpha}^{2} \cdot a_{\alpha}^{2}) = \text{diag}(a_{\alpha}^{4}) $$  Taking the positive square root:  $$ (W^{\top} W)^{1/2}= \text{diag}(a_{\alpha}^{2}) = W_{1}^{\top} W_{1} \qquad \square $$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: e43bc516-ce86-470d-b8ac-46b2e130d112
content::
\## Exercise 3.5: $W_{2}W_{2}^{\top}$ in terms of $W$ (optional)

**Exercise 3.5 ($W_{2}W_{2}^{\top}$ in terms of $W$).** Similarly, show that $W_{2} W_{2}^{\top} = (W W^{\top})^{1/2}$.
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 3.5 ($W_{2}W_{2}^{\top}$ in terms of $W$) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START By the same argument, $W_{2} W_{2}^{\top} = \text{diag}(b_{\alpha}^{2}) = \text{diag}(a_{\alpha}^{2})$ (using $b_{\alpha}^{2} = a_{\alpha}^{2}$). And $WW^{\top} = \text{diag}(a_{\alpha}^{2} b_{\alpha}^{2}) = \text{diag}(a_{\alpha}^{4})$, so $(WW^{\top})^{1/2}= \text{diag}(a_{\alpha}^{2}) = W_{2} W_{2}^{\top}$. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: e0435e17-4464-4f60-bf52-b42465cf8371
content::
\## Exercise 3.6: The balanced function-space ODE (optional)

**Exercise 3.6 (The balanced function-space ODE).** Substitute the results of Exercise 3.4 and 3.5 into Exercise 3.3 to obtain:

$$
\dot{W}= (W W^{\top})^{1/2}(M - W) + (M - W)(W^{\top} W)^{1/2}
$$
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 3.6 (The balanced function-space ODE) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Substituting into Exercise 3.3:  $$ \dot{W}= (M - W)(W^{\top} W)^{1/2}+ (WW^{\top})^{1/2}(M - W) \qquad \square $$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 7ef4882d-6cf9-441c-af3b-740547fc48be
content::
\## Exercise 3.7: The NTK operator

**Exercise 3.7 (The NTK operator).** Define the NTK operator for $L = 2$ as:

$$
K[F] := (WW^{\top})^{1/2}\, F + F\, (W^{\top} W)^{1/2}
$$

Show that the gradient flow from Exercise 3.6 can be written as $\dot{W}= K[M - W]$.

It turns out that this result generalizes to depth $L$ on the balanced manifold and to non-diagonal weight matrices:

$$
\dot{W}= \sum_{k=1}^{L}(WW^{\top})^{\frac{L-k}{L}}(M - W) (W^{\top} W)^{\frac{k-1}{L}}
$$

This is the NTK equation in the case of DLNs. The NTK equation is a gradient flow in function space with NTK being a preconditioning operator for the gradient.
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (checkpoint 1 of 3: loss-landscape geometry and gradient flow in deep linear networks (Sections 2 and 3)). They have attempted Exercise 3.7 (The NTK operator) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START With $F = M - W$, the equation from Exercise 3.6 reads:  $$ \dot{W}= (WW^{\top})^{1/2}\,F + F\,(W^{\top} W)^{1/2}= K[F] = K[M - W] \qquad \square $$  The general depth-$L$ result $\dot{W}= \sum_{k=1}^{L}(WW^{\top})^{(L-k)/L}(M-W)(W^{\top} W)^{(k-1)/L}$ follows from the same approach applied to the $L$-fold balanced conditions $W_{l+1}^{\top} W_{l+1}= W_{l} W_{l}^{\top}$ for all $l$, and extends to non-diagonal matrices via the polar decomposition. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

