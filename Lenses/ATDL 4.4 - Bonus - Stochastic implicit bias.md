---
id: '201a13d8-6ec0-47d8-ac9e-8b4e4700f778'
title: "Bonus: stochastic implicit bias"
tldr: "SGD noise is not just noise: it pushes training toward flatter regions, in a direction set by the shape of the noise."
summary_for_tutor: "Day 4 optional bonus: Section 7 of the Iliad B.4 worksheet (stochastic implicit bias), Exercises 7.1 to 7.3, with official solutions in each tutor brief."
authors:
  - Guillaume Corlouer
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/training-dynamics/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 40
tutor_minutes: 10
---

#### Text
content::
Optional. In the worksheet, read **Section 7** (stochastic implicit bias, marked bonus by the author).

#### Question: Open
id:: 694c9c0e-b3cc-4826-8522-9804543667fa
content::
\## Exercise 7.1: Boltzmann equilibrium (optional)

**Exercise 7.1 (Boltzmann equilibrium).** The probability density $p(\theta, t)$ of the parameters evolves according to the Fokker–Planck equation:

$$
\partial_{t} p = -\nabla \cdot \mathbf{j}, \qquad \mathbf{j}= -\nabla \mathcal{L}(\theta)\,p(\theta) - \frac{\eta}{2}\nabla \cdot \left(\Sigma(\theta)\,p(\theta)\right)
$$

where $\mathbf{j}$ is the probability current. Assume: (i) stationarity $\partial_{t} p^{*} = 0$, (ii) thermal equilibrium $\mathbf{j}= 0$, and (iii) isotropic noise $\Sigma = \sigma^{2} I$. Show that the equilibrium distribution is the Boltzmann distribution:

$$
p^{*}(\theta) \propto \exp\left(-\frac{2}{\eta \sigma^{2}}\mathcal{L}(\theta)\right)
$$

*Hint*: Setting $\mathbf{j}= 0$ with $\Sigma = \sigma^{2} I$ gives $\nabla \mathcal{L}\, p + \frac{\eta\sigma^{2}}{2}\nabla p = 0$. This is a first-order ODE for $p$ in terms of $\mathcal{L}$. Try the ansatz $p \propto e^{-\beta \mathcal{L}}$ and solve for $\beta$.
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (optional bonus: stochastic implicit bias (Section 7)). They have attempted Exercise 7.1 (Boltzmann equilibrium) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Setting $\mathbf{j}= 0$ (thermal equilibrium) with isotropic noise $\Sigma = \sigma^{2} I$:  $$ 0 = -\nabla\mathcal{L}(\theta)\,p^{*}(\theta) - \frac{\eta\sigma^{2}}{2}\nabla p^{*}(\theta) $$  Rearranging:  $$ \frac{\nabla p^{*}}{p^{*}}= -\frac{2}{\eta\sigma^{2}}\nabla\mathcal{L} $$  The left-hand side is $\nabla\ln p^{*}$, so:  $$ \nabla\ln p^{*}(\theta) = -\frac{2}{\eta\sigma^{2}}\nabla\mathcal{L}(\theta) $$  Integrating both sides:  $$ \ln p^{*}(\theta) = -\frac{2}{\eta\sigma^{2}}\mathcal{L}(\theta) + \text{const} $$  $$ \boxed{p^*(\theta) \propto \exp\!\left(-\frac{2}{\eta\sigma^{2}}\mathcal{L}(\theta)\right)} $$  This is the Boltzmann distribution with inverse temperature $\beta = 2/(\eta\sigma^{2})$. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: ffa943c0-46bb-4ebf-b3ee-ca363f08d8a0
content::
\## Exercise 7.2: Temperature and flatness (optional)

**Exercise 7.2 (Temperature and flatness).** The ratio $\frac{2}{\eta \sigma^{2}}$ plays the role of an inverse temperature $\beta$. Interpret what happens to the equilibrium distribution when:

- $\eta$ is very small (low temperature)
- $\eta$ is very large (high temperature)

Which regime favors flatter minima, and why might this be beneficial for generalization?
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (optional bonus: stochastic implicit bias (Section 7)). They have attempted Exercise 7.2 (Temperature and flatness) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START The effective temperature is $T = \eta\sigma^{2}/2$.  **Small $\eta$ (low temperature, $\beta \to \infty$):** The distribution concentrates sharply on the global minima of $\mathcal{L}$. SGD converges to the lowest-loss minimizer without exploring.  **Large $\eta$ (high temperature, $\beta \to 0$):** The distribution becomes nearly uniform over parameter space. SGD explores broadly and does not settle into any particular minimum.  **Flat vs. sharp minima:** At moderate temperature, the Boltzmann distribution assigns more probability mass to **broad basins** (flat minima) than to narrow ones. This is because a flat minimum occupies a larger volume of parameter space at any given loss level  -  the width of the basin acts as an entropic contribution. Flat minima tend to generalize better because small perturbations to the parameters (or slight distribution shift in the data) do not dramatically change the loss. Thus the implicit bias of SGD noise toward flat minima is beneficial for generalization. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: a7317248-291d-4f1c-bad7-39cad1de7942
content::
\## Exercise 7.3: Anisotropic noise (optional)

**Exercise 7.3 (Anisotropic noise).** In practice, SGD noise is **not** isotropic: $\Sigma(\theta)$ depends on both the loss landscape and the data. Without solving anything, explain qualitatively why anisotropic noise can introduce an implicit bias that goes beyond what the loss function $\mathcal{L}$ alone would select. Specifically, why might SGD preferentially escape sharp directions of the loss while remaining stable along flat directions?
optional:: true
feedback-instructions:: The student is on Day 4 (Iliad B.4, Training Dynamics, by Guillaume Corlouer) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (optional bonus: stochastic implicit bias (Section 7)). They have attempted Exercise 7.3 (Anisotropic noise) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START When $\Sigma(\theta)$ is anisotropic, the noise strength varies by direction. The Fokker-Planck current becomes:  $$ \mathbf{j}= -\nabla\mathcal{L}\,p - \frac{\eta}{2}\nabla\cdot(\Sigma(\theta)\,p) $$  The second term introduces an **Itô drift** $\frac{\eta}{2}\nabla\cdot\Sigma(\theta)$ that depends on the spatial variation of the noise covariance. In directions where $\Sigma$ has large eigenvalues (high noise), the effective diffusion is strong and the system escapes easily from sharp regions of the loss landscape. In directions where $\Sigma$ has small eigenvalues (low noise), the system is more stable and tends to remain there.  This creates a **direction-dependent regularizer**: SGD preferentially pushes parameters out of sharp directions (high gradient variance → large noise eigenvalue → fast escape) while preserving parameters along flat directions (low gradient variance → small noise eigenvalue → stability). This goes beyond what the Boltzmann distribution on $\mathcal{L}$ alone would predict. In general, detailed balance $\mathbf{j}= 0$ may not hold for anisotropic, state-dependent noise, leading to persistent probability currents and non-equilibrium steady states that further modify the implicit bias. $\square$ OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

