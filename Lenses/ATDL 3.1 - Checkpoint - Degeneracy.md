---
id: 'e035740a-6e3d-484b-b75b-ba219ea417e3'
title: "Checkpoint 1: degeneracy"
tldr: "Degeneracy means you can move the parameters without changing the function. Here you find it in toy models and see how it shows up in the loss landscape."
summary_for_tutor: "Day 3 checkpoint 1 of 3 (SLT fast-track step 1): Exercises 2.1, 2.2, 2.9 or 2.10, and 2.14 and/or 2.15 from the Iliad B.3 worksheet, with the official solutions in each tutor brief."
authors:
  - Kai Ogden
  - Matthew Farrugia-Roberts
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/d2792cbf53158db2a5729ff7d431a53869b64624/tex/singular-learning-theory/main.tex
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 70
tutor_minutes: 20
---

#### Text
content::
In the worksheet, read **Subsection 2.1** (definition of degeneracy) and **Subsection 2.5** (degeneracy in the loss landscape). Answer each exercise below after you have worked it. The exercise text is repeated here so you do not have to switch pages.

#### Question: Open
id:: 5a7a44f3-4cac-42bd-9fdf-a1994ea7bcd0
content::
\## Exercise 2.1: Parametrising the space of constants

**Exercise 2.1 (Parametrising the space of constants).** Let $\mathcal{X} = \{\ast\}$ and $\mathcal{Y} = \mathbb{R}$, so that we have a hypothesis class of constants. Consider the scalar parameter space $\mathcal{W} = \mathbb{R}$ and the parameter function map that maps $w$ to $f_{w} = w$ (the output is just the parameter itself).

**(a)** What is the directional derivative of the parameter–function map in direction $v = 1$?
:::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

:::

**(b)** At which points in the parameter space is this parameter–function map degenerate, if any?
feedback-instructions:: The student is on Day 3 (Iliad B.3, Singular Learning Theory, by Kai Ogden, Matthew Farrugia-Roberts and Zach Furman) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (step 1 of 3: degeneracy of the parameter-function map and the loss landscape). They have attempted Exercise 2.1 (Parametrising the space of constants) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START 1. Since $\mathcal{W} = \mathbb{R}$ is one-dimensional, the directional derivative in direction $v = 1$ reduces to the ordinary derivative:  $$ \frac{\partial \Phi}{\partial w}= \frac{d}{dw}w = 1. $$ 2. The directional derivative is $1 \neq 0$ for all $w \in \mathcal{W}$. Therefore, the parameter–function map is *not degenerate* at any point. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: f9e0d8de-b06c-4408-99e3-d7cd428b3a4b
content::
\## Exercise 2.2: Degeneracy from raising a parameter to a power

**Exercise 2.2 (Degeneracy from raising a parameter to a power).** Again, consider a hypothesis class of constants and the scalar parameter space $\mathcal{W} = \mathbb{R}$. This time, define a parameter function map that maps $w$ to $f_{w} = w^{3}$.

**(a)** Show that this architecture indexes exactly the same hypothesis class as the architecture described in Exercise 2.1.

**(b)** What is the directional derivative of the parameter–function map in direction $v = 1$?
:::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

:::

**(c)** At which points in the parameter space is the parameter–function map degenerate, if any?
feedback-instructions:: The student is on Day 3 (Iliad B.3, Singular Learning Theory, by Kai Ogden, Matthew Farrugia-Roberts and Zach Furman) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (step 1 of 3: degeneracy of the parameter-function map and the loss landscape). They have attempted Exercise 2.2 (Degeneracy from raising a parameter to a power) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START 1. The hypothesis class of Exercise 2.1 is $\mathcal{F} = \{f_{w} = w : w \in \mathbb{R}\} = \mathbb{R}$. The hypothesis class here is $\mathcal{F} = \{f_{w} = w^{3} : w \in \mathbb{R}\}$. Since $w \mapsto w^{3}$ is a bijection on $\mathbb{R}$, as $w$ ranges over $\mathbb{R}$, $w^{3}$ takes every real value exactly once. So $\mathcal{F} = \mathbb{R}$ in both cases. 2. The directional derivative in direction $v = 1$ is the ordinary derivative:  $$ \frac{\partial \Phi}{\partial w}= \frac{d}{dw}w^{3} = 3w^{2}. $$ 3. The directional derivative $3w^{2} = 0$ if and only if $w = 0$. So the parameter–function map is degenerate at $w = 0$ only. It is somewhere degenerate but not everywhere degenerate. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 5244eea2-6764-42cf-88ea-630572df656a
content::
\## Exercise 2.9 or 2.10 (your choice)

Do **one** of these two, and say which one you chose at the top of your answer.

**Exercise 2.9 (Degeneracy in the two-layer DLN).** Consider the two-layer DLN from Example 1.3, with $h=m$. The parameter space encodes two matrices $A, B \in \mathbb{R}^{m \times m}$, and the parameter–function map sends $(A, B)$ to the function $\Phi(A,B) = f_{A,B}: \mathbb{R}^{m} \to \mathbb{R}^{m}$ such that $f_{A,B}(x) = BAx$ for $x \in \mathbb{R}^{m}$.

**(a)** Let $(\delta\!A, \delta\!B)$ be a unit perturbation in parameter space (a unit vector in the underlying parameter space $\mathbb{R}^{2m^2}$, decoded into a pair of matrices). Show that the directional derivative of the parameter–function map at $(A, B)$ in direction $(\delta\!A, \delta\!B)$ is the linear map

$$
D_{(\delta\!A, \delta\!B)}\Phi(A, B) = B\,\delta\!A + \delta\!B\, A.
$$

That is, $D_{(\delta\!A, \delta\!B)}\Phi(A, B) x = (B\,\delta\!A + \delta\!B\, A) x$.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Use the limit definition, (20).

:::

**(b)** Show that at the zero parameter $(A, B) = (0, 0)$, every direction in parameter space is degenerate. Count the number of dimensions in the subspace of degenerate directions.

**(c)** Suppose both $A$ and $B$ are invertible. Show that $(\delta\!A, \delta\!B)$ is a degenerate direction if and only if $\delta\!B = -B\,\delta\!A\, A^{-1}$. Count the number of dimensions in the subspace of degenerate directions.

**(d)** Now consider the general case. Fix $A$ and $B$, and let $r_{A} = \mathrm{rank}(A)$ and $r_{B} = \mathrm{rank}(B)$. Show that the dimensionality of the space of degenerate directions is

$$
m^{2} + (m-r_{A})(m-r_{B}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

The following is a guide to one possible approach.

1. Describe the image of the linear map $T_{A}$ sending $\delta\!B \in \mathbb{R}^{m^2}$ to $\delta\!B\, A \in \mathbb{R}^{m^2}$ in terms of the row space of $A$. Show that the dimensionality of this image (the rank of the linear map $T_{A}$) is $m r_{A}$.
2. Similarly, describe the image of the linear map $T_{B}$ sending $\delta\!A \in \mathbb{R}^{m^2}$ to $B\, \delta\!A \in \mathbb{R}^{m^2}$ in terms of the column space of $B$. Show that dimensionality of this image (the rank of the linear map $T_{B}$) is $m r_{B}$.
3. Describe the intersection of the images of $T_{A}, T_{B}$ in terms of the row/column spaces of $A, B$. Show that the dimensionality of this intersection is $r_{A} r_{B}$.
4. Consider a third linear map, $T_{D}$, sending $(\delta\!A, \delta\!B) \in \mathbb{R}^{2m^2}$ to $B\,\delta\!A + \delta\!B\, A \in \mathbb{R}^{m^2}$. Describe the image of this linear map in terms of those of $T_{A}$ and $T_{B}$. Compute the rank of this linear map using Grassmann's identity.
5. What is the nullity of $T_{D}$? Why is this the same as the dimensionality of the space of degenerate directions?

:::

**or**

**Exercise 2.10 (Redundant units in an MLP).** Consider a single-hidden-layer MLP with scalar inputs and outputs, $h$ hidden units with activation function $\sigma : \mathbb{R} \to \mathbb{R}$, and an output bias. The parameter space is $\mathcal{W} = \mathbb{R}^{3h+1}$ with parameters $w = (a_{1}, b_{1}, c_{1}, \ldots, a_{h}, b_{h}, c_{h}, d)$, and the parameter–function map is

$$
f_{w}(x) = d + \sum_{i=1}^{h}a_{i} \, \sigma(b_{i} x + c_{i}).
$$

Here, for each hidden unit $i$, $a_{i}$ is the outgoing weight, $b_{i}$ is the incoming weight, and $c_{i}$ is the bias. The output bias is $d$.

**(a)** Suppose $a_{i} = 0$ (unit $i$ has zero outgoing weight). Show that the directions $\delta b_{i}$ and $\delta c_{i}$ are degenerate at $w$.

**(b)** Suppose $b_{i} = 0$ (unit $i$ has zero incoming weight). Show that the direction $(\delta a_{i}, \delta d) = (1, -\sigma(c_{i}))$ (with all other components zero) is degenerate at $w$.

**(c)** Suppose $h \geq 2$ and $(b_{i}, c_{i}) = (b_{j}, c_{j})$ for some $i \neq j$ (units $i$ and $j$ have the same incoming weights and biases). Show that the direction $(\delta a_{i}, \delta a_{j}) = (1, -1)$ (with all other components zero) is degenerate at $w$.
feedback-instructions:: The student is on Day 3 (Iliad B.3, Singular Learning Theory, by Kai Ogden, Matthew Farrugia-Roberts and Zach Furman) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (step 1 of 3: degeneracy of the parameter-function map and the loss landscape). They have attempted Exercise 2.9 (Degeneracy in the two-layer DLN) or Exercise 2.10 (Redundant units in an MLP), their choice from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Solution to Exercise 2.9: 1. Encoding $(A, B)$ and $(\delta\!A, \delta\!B)$ as vectors in the underlying parameter space $\mathbb{R}^{2m^2}$, the directional derivative is  $$ D_{(\delta\!A, \delta\!B)}\Phi(A, B)(x) = \lim_{\epsilon \to 0}\frac{ f_{A + \epsilon\delta\!A,\, B + \epsilon\delta\!B}(x) - f_{A,B}(x) }{\epsilon}. $$  Expanding the matrix product:  $$ \begin{aligned}f_{A + \epsilon\delta\!A,\, B + \epsilon\delta\!B}(x)&= (B + \epsilon\delta\!B)(A + \epsilon\delta\!A)\,x \\&= BAx + \epsilon(B\,\delta\!A + \delta\!B\, A)\,x + \epsilon^{2} \delta\!B\,\delta\!A\, x.\end{aligned} $$  Subtracting $f_{A,B}(x) = BAx$, dividing by $\epsilon$, and taking $\epsilon \to 0$ gives  $$ D_{(\delta\!A, \delta\!B)}\Phi(A, B)(x) = (B\,\delta\!A + \delta\!B\, A)\,x. $$ 2. At $(A, B) = (0, 0)$, part (a) gives $D_{(\delta\!A, \delta\!B)}\Phi(0, 0)(x) = (0 \cdot \delta\!A + \delta\!B \cdot 0)\,x = 0$ for every $(\delta\!A, \delta\!B)$ and every $x$. Every non-zero direction is therefore degenerate. The subspace of degenerate directions is the entire parameter space $\mathbb{R}^{2m^2}$, which has dimension $2m^{2}$. 3. By part (a), $(\delta\!A, \delta\!B)$ is a degenerate direction if and only if $B\,\delta\!A + \delta\!B\, A = 0$, that is, $\delta\!B\, A = -B\,\delta\!A$. Since $A$ is invertible, right-multiplying by $A^{-1}$ gives $\delta\!B = -B\,\delta\!A\, A^{-1}$. Since $\delta\!A \in \mathbb{R}^{m \times m}$ is free and $\delta\!B$ is uniquely determined, the subspace of degenerate directions has dimension $m^{2}$. 4. 1. The $i$-th row of $\delta\!B\, A$ is $(\delta\!B)_{i} A$, a linear combination of the rows of $A$. Therefore the image of $T_{A}$ consists of all matrices whose rows lie in the row space of $A$. Each of the $m$ rows can be any vector in the $r_{A}$-dimensional row space, so $\mathrm{rank}(T_{A}) = m\,r_{A}$. 2. Similarly, the $j$-th column of $B\,\delta\!A$ is $B\,(\delta\!A)^{j}$, a linear combination of the columns of $B$. The image of $T_{B}$ consists of all matrices whose columns lie in the column space of $B$, and $\mathrm{rank}(T_{B}) = m\,r_{B}$. 3. A matrix lies in $\mathrm{im}(T_{A}) \cap \mathrm{im}(T_{B})$ if and only if its rows lie in the row space of $A$ and its columns lie in the column space of $B$. Such a matrix can be written as $U \Lambda V$ where $U \in \mathbb{R}^{m \times r_B}$ has columns spanning the column space of $B$ and $V \in \mathbb{R}^{r_A \times m}$ has rows spanning the row space of $A$, with $\Lambda \in \mathbb{R}^{r_B \times r_A}$ free. The dimensionality of this intersection is therefore $r_{A}\,r_{B}$. 4. The image of $T_{D}$ is $\mathrm{im}(T_{D}) = \mathrm{im}(T_{B}) + \mathrm{im}(T_{A})$, since for any $(\delta\!A, \delta\!B)$ we have $T_{D}(\delta\!A, \delta\!B) = T_{B}(\delta\!A) + T_{A}(\delta\!B)$, and conversely any element of $\mathrm{im}(T_{B}) + \mathrm{im}(T_{A})$ can be realised by choosing appropriate $\delta\!A$ and $\delta\!B$. By Grassmann's identity,  $$ \begin{aligned}\mathrm{rank}(T_{D})&= \dim(\mathrm{im}(T_{A}) + \mathrm{im}(T_{B})) \\&= \mathrm{rank}(T_{A}) + \mathrm{rank}(T_{B}) - \dim(\mathrm{im}(T_{A}) \cap \mathrm{im}(T_{B})) \\&= m\,r_{A} + m\,r_{B} - r_{A}\,r_{B}.\end{aligned} $$ 5. By the rank–nullity theorem, the nullity of $T_{D}$ is  $$ \begin{aligned}&\mathrel{\phantom{=}}2m^{2} - (m\,r_{A} + m\,r_{B} - r_{A}\,r_{B}) \\&= 2m^{2} - m\,r_{A} - m\,r_{B} + r_{A}\,r_{B} \\&= m^{2} + (m - r_{A})(m - r_{B}).\end{aligned} $$  The kernel of $T_{D}$ is exactly the set of $(\delta\!A, \delta\!B)$ such that $B\,\delta\!A + \delta\!B\, A = 0$, which by part (a) is precisely the subspace of degenerate directions.  Solution to Exercise 2.10: 1. At $a_{i} = 0$, the parameter–function map reduces to  $$ f_{w}(x) = d + 0 \cdot \sigma(b_{i} x + c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) = d + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}). $$  This expression does not involve $b_{i}$ or $c_{i}$ at all. Therefore $\Phi$ is constant in the $b_{i}$ and $c_{i}$ directions at this point, so $D_{\delta b_i}\Phi(w) = 0$ and $D_{\delta c_i}\Phi(w) = 0$. Both are degenerate directions.  Note that this argument is purely algebraic, following from the multiplicative structure $a_{i} \cdot \sigma(\ldots)$, and requires no conditions on $\sigma$ (not even continuity or differentiability). 2. At $b_{i} = 0$, unit $i$ computes the constant $\sigma(0 \cdot x + c_{i}) = \sigma(c_{i})$ for all $x$, so  $$ f_{w}(x) = d + a_{i}\,\sigma(c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}). $$  In the direction $(\delta a_{i}, \delta d) = (1, -\sigma(c_{i}))$, we compute  $$ \begin{aligned}f_{w + \epsilon\,v}(x)&= (d - \epsilon\,\sigma(c_{i})) + (a_{i} + \epsilon)\,\sigma(c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) \\&= d + a_{i}\,\sigma(c_{i}) + \epsilon\bigl(\sigma(c_{i}) - \sigma(c_{i})\bigr) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) = f_{w}(x).\end{aligned} $$  So $D_{(\delta a_i, \delta d)}\Phi(w) = 0$ and this direction is degenerate. Intuitively, increasing $a_{i}$ scales up the constant contribution $a_{i}\,\sigma(c_{i})$ to the output, and decreasing $d$ by the same amount compensates exactly. 3. When $(b_{i}, c_{i}) = (b_{j}, c_{j})$, units $i$ and $j$ compute the same activation, so their combined contribution to $f_{w}$ is  $$ a_{i}\,\sigma(b_{i} x + c_{i}) + a_{j}\,\sigma(b_{j} x + c_{j}) = (a_{i} + a_{j})\,\sigma(b_{i} x + c_{i}). $$  In the direction $(\delta a_{i}, \delta a_{j}) = (1, -1)$, this combined contribution changes by $\sigma(b_{i} x + c_{i}) - \sigma(b_{j} x + c_{j}) = 0$. All other terms in $f_{w}$ are unchanged, so $D_{(1,-1)}\Phi(w) = 0$. Again, no conditions on $\sigma$ are needed. OFFICIAL SOLUTION END The student was asked to say which of the two they chose; if they did not, work it out from their answer. Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: beca8918-9b0a-42d9-8e1c-6fefc3f30fa3
content::
\## Exercise 2.14 or 2.15 (your choice; do both if you have time)

Do **one** of these two, and say which one you chose at the top of your answer.

**Exercise 2.14 (Some examples of loss landscape degeneracy).** Consider the parameter space $\mathcal{W} = \mathbb{R}^{2}$ with the identity parameter–function map $\Phi = \mathrm{id}$, so that we identify parameters with the functions they implement (cf., Exercise 2.1). Consider the family of loss functions $L_{k,l}(a,b) = a^{2k}+ b^{2l}$ for non-negative integers $k$ and $l$.

**(a)** Show that the origin is a global minimum of $L_{k,l}$ for all non-negative $k$ and $l$. For which $k$ and $l$ is it the unique global minimum?

**(b)** Show that if $k = l = 1$, then the origin is a non-degenerate (regular) minimum.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Compute the Hessian.

:::

**(c)** Show that if $k > 1$ and $l \geq 1$, then the origin is a degenerate minimum.

**(d)** Show that if $k = 0$ and $l \geq 1$, then the origin is a degenerate minimum.

**or**

**Exercise 2.15 (Realisable models and Hessian degeneracy).** Let $\Psi : \mathcal{W} \to \mathcal{D}$ be a parameter–distribution map with positive densities $p(y \mid x, w)$, twice-differentiable in $w$. Suppose data is generated from a fixed true parameter $w_{0} \in \mathcal{W}$, meaning $q(y \mid x) = p(y \mid x, w_{0})$. Consider the population negative log-likelihood loss

$$
L(w) = -\mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}\!\bigl[\log p(y \mid x, w)\bigr].
$$

Assume that for each $x$, the operations $\nabla_{w}$ (and $\nabla_{w}^{2}$) and $\int_{\mathcal{Y}} \cdot\, dy$ may be exchanged.

**(a)** *(Bartlett identity.)* Show that for each $x \in \mathcal{X}$ and $w \in \mathcal{W}$,


$$
-\mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr] = \mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr],
$$


^eq-bartlett


where $s$ is the score function from Definition 2.3.
:::callout {title="Hint" tone="neutral" collapse="closed"}

differentiate the identity $\mathbb{E}_{y \sim p(y \mid x, w)}[s(x, y, w)] = 0$ (established in Exercise 2.11) with respect to $w$.

:::

**(b)** Show that the Hessian of $L$ at the true parameter $w_{0}$ equals the Fisher information matrix (Definition 2.4):


$$
H(w_{0}) = I(w_{0}).
$$


^eq-fim-hessian


:::callout {title="Hint" tone="neutral" collapse="closed"}

compute $H(w) = -\mathbb{E}_{x}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}[\nabla_{w}^{2} \log p(y \mid x, w)]$, evaluate at $w = w_{0}$, and apply part (a).

:::

**(c)** Using the result of Exercise 2.12, conclude: if $\Psi$ is degenerate at $w_{0}$ in direction $v$, then $H(w_{0})\, v = 0$. Contrapositively, if $H(w_{0})$ is positive definite, then $\Psi$ is non-degenerate at $w_{0}$.
feedback-instructions:: The student is on Day 3 (Iliad B.3, Singular Learning Theory, by Kai Ogden, Matthew Farrugia-Roberts and Zach Furman) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (step 1 of 3: degeneracy of the parameter-function map and the loss landscape). They have attempted Exercise 2.14 (Some examples of loss landscape degeneracy) or Exercise 2.15 (Realisable models and Hessian degeneracy), their choice from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Solution to Exercise 2.14: 1. Since $a^{2k}\geq 0$ and $b^{2l}\geq 0$ for all $a, b \in \mathbb{R}$ (using the convention $0^{0} = 1$), we have $L_{k,l}(a,b) \geq 0$ for $k, l \geq 1$, $L_{k,l}(a,b) \geq 1$ if $k = 0$ or $l = 0$, and $L_{k,l}(a,b) = 2$ if $k = l = 0$. At the origin, $L_{k,l}(0,0) = 0^{2k}+ 0^{2l}$, which equals $0$ if $k \geq 1$ and $l \geq 1$, equals $1$ if exactly one of $k, l$ is $0$, and equals $2$ if $k = l = 0$. In each case this matches the lower bound, so the origin is a global minimum.  The origin is the *unique* global minimum if and only if $k \geq 1$ and $l \geq 1$: then $L_{k,l}(a,b) = 0$ requires both $a^{2k}= 0$ and $b^{2l}= 0$, forcing $a = b = 0$. If $k = 0$, then $L_{0,l}(a,0) = 1$ for all $a$, so the entire $a$-axis achieves the minimum. Similarly if $l = 0$. If $k = l = 0$, then all parameters achieve the minimum. 2. For $k = l = 1$: $L_{1,1}(a,b) = a^{2} + b^{2}$. The Hessian at the origin is  $$ H(0,0) = \begin{pmatrix}2 & 0 \\ 0 & 2\end{pmatrix}, $$  which is positive definite. The origin is a non-degenerate minimum. 3. For $k > 1$ and $l \geq 1$: $\frac{\partial^{2} L_{k,l}}{\partial a^{2}}= 2k(2k{-}1)\, a^{2k-2}$. At the origin, $a^{2k-2}= 0$ since $2k - 2 \geq 2$, so this entry vanishes. The Hessian at the origin is therefore  $$ H(0,0) = \begin{pmatrix}0&0 \\ 0&2l(2l{-}1) \cdot 0^{2l-2}\end{pmatrix}, $$  which has a zero eigenvalue (from the first diagonal entry) regardless of the value of the second. The origin is a degenerate minimum. 4. For $k = 0$ and $l \geq 1$: $L_{0,l}(a,b) = 1 + b^{2l}$. Since $L_{0,l}$ is independent of $a$, both $\frac{\partial L}{\partial a}$ and $\frac{\partial^{2} L}{\partial a^{2}}$ vanish identically. The Hessian at the origin has a zero first diagonal entry, so it is singular. The origin is a degenerate minimum.  Solution to Exercise 2.15: 1. From Exercise 2.11, $\mathbb{E}_{y \sim p(y \mid x, w)}[s_{j}(x,y,w)] = 0$ for each component $j$ of the score, where $s_{j} = \frac{\partial}{\partial w_{j}}\log p(y \mid x, w)$. Differentiating with respect to $w_{k}$ and exchanging the derivative with the integral:  $$ \begin{aligned}0&= \frac{\partial}{\partial w_{k}}\int_{\mathcal{Y}} s_{j}(x,y,w)\, p(y \mid x, w)\, dy \\&= \int_{\mathcal{Y}} \frac{\partial s_{j}}{\partial w_{k}}\, p\, dy + \int_{\mathcal{Y}} s_{j}\, \frac{\partial p}{\partial w_{k}}\, dy. \quad\text{(product rule)}\end{aligned} $$  Using the score identity $\frac{\partial p}{\partial w_{k}}= p \cdot s_{k}$ (24), the second integral becomes $\int_{\mathcal{Y}} s_{j}\, s_{k}\, p\, dy = \mathbb{E}_{y}[s_{j}\, s_{k}]$. Therefore  $$ \mathbb{E}_{y \sim p(y \mid x, w)}\!\left[ \frac{\partial^{2} \log p}{\partial w_{j} \partial w_{k}}\right] = -\mathbb{E}_{y \sim p(y \mid x, w)}[s_{j}\, s_{k}]. $$  Assembling all components into a matrix gives  $$ -\mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr] = \mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr]. $$ 2. The population negative log-likelihood is $L(w) = -\mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}[\log p(y \mid x, w)]$. Taking the Hessian with respect to $w$ (exchanging differentiation and integration):  $$ H(w) = -\mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr]. $$  At $w = w_{0}$, the inner expectation is over $y \sim p(y \mid x, w_{0})$, which matches the distribution in the Bartlett identity. Applying part (a):  $$ \begin{aligned}H(w_{0})&= \mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}\!\bigl[ s(x,y,w_{0})\, s(x,y,w_{0})^{\top} \bigr] \\&= I(w_{0}). \quad\text{(by Theorem 2.4)}\end{aligned} $$ 3. By Exercise 2.12, $\ker I(w_{0}) = \{v \in \mathbb{R}^{d} : D_{v} \Psi(w_{0}) = 0\}$. Since $H(w_{0}) = I(w_{0})$, if $\Psi$ is degenerate at $w_{0}$ in direction $v$, then $v \in \ker I(w_{0}) = \ker H(w_{0})$, so $H(w_{0})\, v = 0$.  Contrapositively: if $H(w_{0})$ is positive definite, then $\ker H(w_{0}) = \{0\}$, so $\ker I(w_{0}) = \{0\}$, and $\Psi$ is non-degenerate at $w_{0}$. OFFICIAL SOLUTION END The student was asked to say which of the two they chose; if they did not, work it out from their answer. Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

