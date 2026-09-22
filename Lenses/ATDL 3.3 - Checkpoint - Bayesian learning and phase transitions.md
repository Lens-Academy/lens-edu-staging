---
id: '1d61e36d-93da-47f6-b810-0cdd6111f4a5'
title: "Checkpoint 3: Bayesian learning and phase transitions"
tldr: "Watanabe's free energy formula trades loss against the LLC. As data grows, the posterior can jump from a simple, worse solution to a complex, better one."
summary_for_tutor: "Day 3 checkpoint 3 of 3 (SLT fast-track step 3): all of Section 4 of the Iliad B.3 worksheet and Exercise 4.2 (phase transitions), with the official solution in the tutor brief."
authors:
  - Kai Ogden
  - Matthew Farrugia-Roberts
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/singular-learning-theory/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 40
tutor_minutes: 15
---

#### Text
content::
In the worksheet, read **all of Section 4**. Part (b) of the exercise asks for a plot; any plotting tool works, or sketch it and describe the shape in words.

#### Question: Open
id:: d27994f4-0652-4625-beca-d1ebccfc185f
content::
\## Exercise 4.2: Exploring phase transitions

**Exercise 4.2 (Exploring phase transitions).** We show how *phase transitions* can occur when different local free energies change at different rates.

**(a)** Suppose we partition the overall parameter space into a disjoint union $\mathcal{W} = \mathcal{U} \sqcup \mathcal{V}$. Denote the overall free energy by $F_{n}$ and the local free energies by $F_{n}(\mathcal{U})$ and $F_{n}(\mathcal{V})$, respectively. Show that the relationship

$$
F_{n} = -\log(e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})})
$$

holds.

**(b)** Suppose $F_{n}(\mathcal{U}) \approx 0.3n + 20 \log n$ and $F_{n}(\mathcal{V}) \approx 0.5n + 2 \log n$. Plot the overall free energy $F(n)$. Compare against $\min\{F_{n}(U), F_{n}(\mathcal{V})\}$. What happens around $n = 570$?

**(c)** In statistical physics, a phase transition is traditionally defined as a discontinuity (or rapid change, for finite-size systems) in the derivatives of the free energy. Plot $\frac{d}{dn}F_{n}$ and explain why this justifies calling the phenomenon from b) a phase transition.

**(d)** Change the coefficients of the terms in b). How does this change when a phase transition occurs? Does a phase transition always occur?
feedback-instructions:: The student is on Day 3 (Iliad B.3, Singular Learning Theory, by Kai Ogden, Matthew Farrugia-Roberts and Zach Furman) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (step 3 of 3: degeneracy in Bayesian learning, Watanabe's free energy formula and phase transitions). They have attempted Exercise 4.2 (Exploring phase transitions) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START 1. By definition, the partition function is  $$ Z_{n} = \int_{\mathcal{W}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw. $$  Since $\mathcal{W} = \mathcal{U} \sqcup \mathcal{V}$ is a disjoint union, the integral splits additively:  $$ Z_{n} = \int_{\mathcal{U}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw + \int_{\mathcal{V}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw = Z_{n}(\mathcal{U}) + Z_{n}(\mathcal{V}). $$  Recalling that $F_{n} = -\log Z_{n}$ and similarly for the local free energies,  $$ Z_{n} = e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})}, $$  and taking the negative logarithm gives  $$ F_{n} = -\log Z_{n} = -\log(e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})}). $$ 2. The curves $F_{n}$ and $\min(F_{n}(\mathcal{U}), F_{n}(\mathcal{V}))$ are nearly identical, both track whichever local free energy is smaller. However, $F_{n}$ is smooth whereas $\min(F_{n}(\mathcal{U}), F_{n}(\mathcal{V}))$ has a kink at $n \approx 570$, where $F_{n}(\mathcal{U}) = F_{n}(\mathcal{V})$. For $n \lesssim 570$ the simpler region $\mathcal{V}$ (lower $\lambda$) dominates; for $n \gtrsim 570$ the lower loss region $\mathcal{U}$ (lower loss coefficient) dominates. 3. Differentiating the log-sum-exp from (a),  $$ \frac{d}{dn}F_{n} = \frac{\frac{d}{dn}F_{n}(\mathcal{U})\,e^{-F_n(\mathcal{U})}+ \frac{d}{dn}F_{n}(\mathcal{V})\,e^{-F_n(\mathcal{V})}}{e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})}}, $$  Plotting this reveals a steep step around $n \approx 570$, transitioning from $\frac{d}{dn}F_{n}(\mathcal{V}) \approx 0.5$ to $\frac{d}{dn}F_{n}(\mathcal{U}) \approx 0.3$. This rapid change in the derivative of $F_{n}$ is a smooth approximation of a discontinuity, justifying the term *phase transition*. 4. Write $F_{n}(\mathcal{U}) \approx L_{\mathcal{U}} \, n + \lambda_{\mathcal{U}} \log n$ and $F_{n}(\mathcal{V}) \approx L_{\mathcal{V}} \, n + \lambda_{\mathcal{V}} \log n$, and set $\Delta L = L_{\mathcal{U}} - L_{\mathcal{V}}$ and $\Delta\lambda = \lambda_{\mathcal{U}} - \lambda_{\mathcal{V}}$. The critical sample size $n^{*}$ where the phase transition occurs satisfies  $$ \Delta L \cdot n^{*} = -\Delta\lambda \cdot \log n^{*}, \qquad\text{i.e.}\qquad \frac{n^{*}}{\log n^{*}}= -\frac{\Delta\lambda}{\Delta L} $$  Since $n^{*}/\log n^{*}$ is positive, a solution exists if and only if $-\Delta\lambda / \Delta L > 0$, i.e. $\Delta L$ and $\Delta\lambda$ have *opposite signs*. A phase transition occurs precisely when one region fits better while the other is simpler ($\Delta L$ and $\Delta\lambda$ have opposite signs). If both fit and complexity favour the same region, that region dominates for all $n$ and no phase transition occurs.  $n^{*}/\log n^{*}$ is monotonically increasing for $n > e$ so for such $n$, increasing $|\Delta \lambda|$ increases $n^{*}$ and increasing $\Delta L$ decreases $n^{*}$. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If some parts are right and another is wrong, confirm the right parts in one sentence and spend the rest of the reply on the wrong part. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, a simpler special case, or the idea of an earlier sub-part), and never state any result the exercise asks them to find. If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

