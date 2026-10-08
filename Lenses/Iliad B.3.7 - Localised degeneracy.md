---
id: '3e2b9bdb-8caa-4d4e-84d8-b6886d05b28f'
title: "B.3.7 Localised degeneracy"
tldr: "Studies degeneracy that exists only at some parameters: the product a*b, two-layer deep linear networks (counting degenerate directions) and redundant MLP units."
summary_for_tutor: "This is Section 2.3 of worksheet B.3 (singular learning theory). It covers localised symmetries and localised degeneracy. It contains Exercises 2.8 (localised symmetry for a*b), 2.9 (two-layer DLN; the degenerate directions have dimension m^2 + (m-r_A)(m-r_B), with a hint and a collapsed solution including an SVD alternative) and 2.10 (redundant units in an MLP). Remarks cover localised symmetries, the rank of a parameter and measure zero degenerate sets. Keep the notation r_A, r_B, delta A, delta B. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Kai Ogden (University of Oxford)
  - Matthew Farrugia-Roberts (University of Oxford)
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/singular-learning-theory/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.3 Localised degeneracy

We have seen that a non-trivial continuous symmetry traces out curves of functionally equivalent parameters throughout the entire parameter space, and the tangent directions to these curves are degenerate directions at every point. However, not all degenerate directions arise from globally continuous symmetries. In fact, the more interesting case is when degeneracy affects only some parameters and not others.

Within certain subsets of parameter space, many neural network architectures (including those studied in Exercises 2.6 and 2.7) exhibit degenerate directions that cannot be defined in terms of continuous transformations that are globally symmetries. In this section, we explore localised degeneracies of this kind.

We begin with some examples of transformations that are only continuous symmetries within certain subsets of parameter space.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.8 (Localised symmetry example).** Recall the parameter–function map from Exercise 2.3, with ${\mathcal{W}} = {\mathbb{R}}^{2}$ and with $(a, b) \in {\mathcal{W}}$ mapping to the constant function $f_{a,b}= a \cdot b$. Consider the two families of transformations $T^{(a)}_{t}, T^{(b)}_{t} : {\mathcal{W}} \to {\mathcal{W}}$ for $t \in {\mathbb{R}}$ such that

$$
T^{(a)}_{t}(a, b) = (a + t, b), \qquad\qquad T^{(b)}_{t}(a, b) = (a, b + t) .
$$

**(a)** Describe the effect of each family of transformations on the parameter space.

**(b)** In which subset of parameter space does each family of transformations constitute a symmetry for all $t\in{\mathbb{R}}$?

**(c)** Compare your results to your answer to Exercise 2.3(d).
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $T^{(a)}_{t}$ translates along the $a$-axis: it shifts the first coordinate by $t$ while leaving the second fixed. $T^{(b)}_{t}$ translates along the $b$-axis.

**(b)** $T^{(a)}_{t}$ is a symmetry at $(a, b)$ for all $t$ if and only if $f_{a+t,b}= f_{a,b}$ for all $t$, i.e., $(a+t)b = ab$ for all $t$. This simplifies to $tb = 0$ for all $t$, which requires $b = 0$. So $\{T^{(a)}_{t}\}$ is a symmetry when restricted to the $a$-axis $\{(a, 0) : a \in {\mathbb{R}}\}$.

Similarly, $\{T^{(b)}_{t}\}$ is a symmetry when restricted to the $b$-axis $\{(0, b) : b \in {\mathbb{R}}\}$.

**(c)** From Exercise 2.3(d), the coordinate directions $(1, 0)$ and $(0, 1)$ are degenerate precisely on the coordinate axes: $(1, 0)$ is degenerate on $\{b = 0\}$ and $(0, 1)$ is degenerate on $\{a = 0\}$. This matches exactly: the axis $\{b = 0\}$ is where the $a$-translation symmetry acts, providing the degenerate direction $(1, 0)$, and the axis $\{a = 0\}$ is where the $b$-translation symmetry acts, providing $(0, 1)$.

:::

The above example is technically a two-layer DLN with $m=h=1$. Let us now explore localised degeneracy in a general two-layer DLN and then in a non-trivial MLP.

::::callout {title="Exercise" tone="amber"}
**Exercise 2.9 (Degeneracy in the two-layer DLN).** Consider the two-layer DLN from Example 1.3, with $h=m$. The parameter space encodes two matrices $A, B \in {\mathbb{R}}^{m \times m}$, and the parameter–function map sends $(A, B)$ to the function $\Phi(A,B) = f_{A,B}: {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$ such that $f_{A,B}(x) = BAx$ for $x \in {\mathbb{R}}^{m}$.

**(a)** Let $(\delta\!A, \delta\!B)$ be a unit perturbation in parameter space (a unit vector in the underlying parameter space ${\mathbb{R}}^{2m^2}$, decoded into a pair of matrices). Show that the directional derivative of the parameter–function map at $(A, B)$ in direction $(\delta\!A, \delta\!B)$ is the linear map

$$
D_{(\delta\!A, \delta\!B)}\Phi(A, B) = B\,\delta\!A + \delta\!B\, A.
$$

That is, $D_{(\delta\!A, \delta\!B)}\Phi(A, B) x = (B\,\delta\!A + \delta\!B\, A) x$.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Use the limit definition, (20).

:::

**(b)** Show that at the zero parameter $(A, B) = (0, 0)$, every direction in parameter space is degenerate. Count the number of dimensions in the subspace of degenerate directions.

**(c)** Suppose both $A$ and $B$ are invertible. Show that $(\delta\!A, \delta\!B)$ is a degenerate direction if and only if $\delta\!B = -B\,\delta\!A\, A^{-1}$. Count the number of dimensions in the subspace of degenerate directions.

**(d)** Now consider the general case. Fix $A$ and $B$, and let $r_{A} = {\mathrm{rank}}(A)$ and $r_{B} = {\mathrm{rank}}(B)$. Show that the dimensionality of the space of degenerate directions is

$$
m^{2} + (m-r_{A})(m-r_{B}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

The following is a guide to one possible approach.

1. Describe the image of the linear map $T_{A}$ sending $\delta\!B \in {\mathbb{R}}^{m^2}$ to $\delta\!B\, A \in {\mathbb{R}}^{m^2}$ in terms of the row space of $A$. Show that the dimensionality of this image (the rank of the linear map $T_{A}$) is $m r_{A}$.
2. Similarly, describe the image of the linear map $T_{B}$ sending $\delta\!A \in {\mathbb{R}}^{m^2}$ to $B\, \delta\!A \in {\mathbb{R}}^{m^2}$ in terms of the column space of $B$. Show that the dimensionality of this image (the rank of the linear map $T_{B}$) is $m r_{B}$.
3. Describe the intersection of the images of $T_{A}, T_{B}$ in terms of the row/column spaces of $A, B$. Show that the dimensionality of this intersection is $r_{A} r_{B}$.
4. Consider a third linear map, $T_{D}$, sending $(\delta\!A, \delta\!B) \in {\mathbb{R}}^{2m^2}$ to $B\,\delta\!A + \delta\!B\, A \in {\mathbb{R}}^{m^2}$. Describe the image of this linear map in terms of those of $T_{A}$ and $T_{B}$. Compute the rank of this linear map using Grassmann's identity.
5. What is the nullity of $T_{D}$? Why is this the same as the dimensionality of the space of degenerate directions?

Alternatively: substitute singular value decompositions $A = U_{1} \Sigma_{1} V_{1}^{\top}$ and $B = U_{2} \Sigma_{2} V_{2}^{\top}$ into the degeneracy condition $B\,\delta\!A + \delta\!B\, A = 0$, and change variables to absorb the orthogonal factors. The condition becomes an equation between two diagonally-scaled matrices, whose solutions can be counted entry by entry.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Encoding $(A, B)$ and $(\delta\!A, \delta\!B)$ as vectors in the underlying parameter space ${\mathbb{R}}^{2m^2}$, the directional derivative is

$$
D_{(\delta\!A, \delta\!B)}\Phi(A, B)(x) = \lim_{\epsilon \to 0}\frac{ f_{A + \epsilon\delta\!A,\, B + \epsilon\delta\!B}(x) - f_{A,B}(x) }{\epsilon}.
$$

Expanding the matrix product:

$$
\begin{aligned}f_{A + \epsilon\delta\!A,\, B + \epsilon\delta\!B}(x)&= (B + \epsilon\delta\!B)(A + \epsilon\delta\!A)\,x \\&= BAx + \epsilon(B\,\delta\!A + \delta\!B\, A)\,x + \epsilon^{2} \delta\!B\,\delta\!A\, x.\end{aligned}
$$

Subtracting $f_{A,B}(x) = BAx$, dividing by $\epsilon$, and taking $\epsilon \to 0$ gives

$$
D_{(\delta\!A, \delta\!B)}\Phi(A, B)(x) = (B\,\delta\!A + \delta\!B\, A)\,x.
$$

**(b)** At $(A, B) = (0, 0)$, part (a) gives $D_{(\delta\!A, \delta\!B)}\Phi(0, 0)(x) = (0 \cdot \delta\!A + \delta\!B \cdot 0)\,x = 0$ for every $(\delta\!A, \delta\!B)$ and every $x$. Every non-zero direction is therefore degenerate. The subspace of degenerate directions is the entire parameter space ${\mathbb{R}}^{2m^2}$, which has dimension $2m^{2}$.

**(c)** By part (a), $(\delta\!A, \delta\!B)$ is a degenerate direction if and only if $B\,\delta\!A + \delta\!B\, A = 0$, that is, $\delta\!B\, A = -B\,\delta\!A$. Since $A$ is invertible, right-multiplying by $A^{-1}$ gives $\delta\!B = -B\,\delta\!A\, A^{-1}$. Since $\delta\!A \in {\mathbb{R}}^{m \times m}$ is free and $\delta\!B$ is uniquely determined, the subspace of degenerate directions has dimension $m^{2}$.

**(d)**
1. The $i$-th row of $\delta\!B\, A$ is $(\delta\!B)_{i} A$, a linear combination of the rows of $A$. Therefore the image of $T_{A}$ consists of all matrices whose rows lie in the row space of $A$. Each of the $m$ rows can be any vector in the $r_{A}$-dimensional row space, so ${\mathrm{rank}}(T_{A}) = m\,r_{A}$.
2. Similarly, the $j$-th column of $B\,\delta\!A$ is $B\,(\delta\!A)^{j}$, a linear combination of the columns of $B$. The image of $T_{B}$ consists of all matrices whose columns lie in the column space of $B$, and ${\mathrm{rank}}(T_{B}) = m\,r_{B}$.
3. A matrix lies in ${\mathrm{im}}(T_{A}) \cap {\mathrm{im}}(T_{B})$ if and only if its rows lie in the row space of $A$ and its columns lie in the column space of $B$. Such a matrix can be written as $U \Lambda V$ where $U \in {\mathbb{R}}^{m \times r_B}$ has columns spanning the column space of $B$ and $V \in {\mathbb{R}}^{r_A \times m}$ has rows spanning the row space of $A$, with $\Lambda \in {\mathbb{R}}^{r_B \times r_A}$ free. The dimensionality of this intersection is therefore $r_{A}\,r_{B}$.
4. The image of $T_{D}$ is ${\mathrm{im}}(T_{D}) = {\mathrm{im}}(T_{B}) + {\mathrm{im}}(T_{A})$, since for any $(\delta\!A, \delta\!B)$ we have $T_{D}(\delta\!A, \delta\!B) = T_{B}(\delta\!A) + T_{A}(\delta\!B)$, and conversely any element of ${\mathrm{im}}(T_{B}) + {\mathrm{im}}(T_{A})$ can be realised by choosing appropriate $\delta\!A$ and $\delta\!B$. By Grassmann's identity,

$$
\begin{aligned}{\mathrm{rank}}(T_{D})&= \dim({\mathrm{im}}(T_{A}) + {\mathrm{im}}(T_{B})) \\&= {\mathrm{rank}}(T_{A}) + {\mathrm{rank}}(T_{B}) - \dim({\mathrm{im}}(T_{A}) \cap {\mathrm{im}}(T_{B})) \\&= m\,r_{A} + m\,r_{B} - r_{A}\,r_{B}.\end{aligned}
$$
5. By the rank–nullity theorem, the nullity of $T_{D}$ is

$$
\begin{aligned}&\mathrel{\phantom{=}}2m^{2} - (m\,r_{A} + m\,r_{B} - r_{A}\,r_{B}) \\&= 2m^{2} - m\,r_{A} - m\,r_{B} + r_{A}\,r_{B} \\&= m^{2} + (m - r_{A})(m - r_{B}).\end{aligned}
$$

The kernel of $T_{D}$ is exactly the set of $(\delta\!A, \delta\!B)$ such that $B\,\delta\!A + \delta\!B\, A = 0$, which by part (a) is precisely the subspace of degenerate directions.

**Alternative solution to (d), via the SVD.**  Take singular value decompositions $A = U_{1} \Sigma_{1} V_{1}^{\top}$ and $B = U_{2} \Sigma_{2} V_{2}^{\top}$, where $U_{1}, V_{1}, U_{2}, V_{2} \in {\mathbb{R}}^{m \times m}$ are orthogonal and $\Sigma_{1}, \Sigma_{2} \in {\mathbb{R}}^{m \times m}$ are diagonal with non-negative entries, ordered so that the $r_{A}$ non-zero entries of $\Sigma_{1}$ and the $r_{B}$ non-zero entries of $\Sigma_{2}$ come first. By part (a), $(\delta\!A, \delta\!B)$ is a degenerate direction if and only if $B\,\delta\!A + \delta\!B\, A = 0$. Change variables by the linear map

$$
X = V_{2}^{\top}\, \delta\!A\, V_{1}, \qquad Y = -U_{2}^{\top}\, \delta\!B\, U_{1},
$$

so that $\delta\!A = V_{2} X V_{1}^{\top}$ and $\delta\!B = -U_{2} Y U_{1}^{\top}$. This map is invertible, so it preserves the dimensionality of subspaces, and we may count degrees of freedom in the new variables. Substituting,

$$
\begin{aligned}B\,\delta\!A + \delta\!B\, A = 0&\iff U_{2} \Sigma_{2} V_{2}^{\top}\, V_{2} X V_{1}^{\top} = U_{2} Y U_{1}^{\top}\, U_{1} \Sigma_{1} V_{1}^{\top} \\&\iff U_{2} \left( \Sigma_{2} X \right) V_{1}^{\top} = U_{2} \left( Y \Sigma_{1} \right) V_{1}^{\top} \\&\iff \Sigma_{2} X = Y \Sigma_{1},\end{aligned}
$$

using orthogonality ($V_{2}^{\top} V_{2} = U_{1}^{\top} U_{1} = I$) in the second step and invertibility of $U_{2}$ and $V_{1}$ in the third.

It remains to count the dimensionality of the space of pairs $(X, Y)$ satisfying $\Sigma_{2} X = Y \Sigma_{1}$. Write $\sigma_{i}$ for the $i$-th diagonal entry of $\Sigma_{2}$ and $\tau_{j}$ for the $j$-th diagonal entry of $\Sigma_{1}$. Multiplying by a diagonal matrix on the left scales rows, and on the right scales columns, so entry $(i, j)$ of the equation reads

$$
\sigma_{i} X_{ij}= \tau_{j} Y_{ij}.
$$

Each such equation involves only the pair of entries $(X_{ij}, Y_{ij})$, and each pair appears in exactly one equation, so the system decouples into $m^{2}$ independent cells. The picture is as follows: the bottom $m - r_{B}$ rows of $\Sigma_{2} X$ and the rightmost $m - r_{A}$ columns of $Y \Sigma_{1}$ vanish identically, so a cell in their overlap yields the trivial equation $0 = 0$, while every other cell yields one non-trivial constraint.

![diagram](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-slt-figure-9c884654.png)

Concretely: the equation for cell $(i, j)$ is trivial if and only if $\sigma_{i} = \tau_{j} = 0$, that is, $i > r_{B}$ and $j > r_{A}$, leaving both entries free (two degrees of freedom); there are $(m - r_{B})(m - r_{A})$ such cells. Every other cell imposes one non-trivial linear constraint on $(X_{ij}, Y_{ij})$, leaving one degree of freedom; there are $m^{2} - (m - r_{A})(m - r_{B})$ such cells. The dimensionality of the space of degenerate directions is therefore

$$
\begin{aligned}&2 (m - r_{A})(m - r_{B}) + \left( m^{2} - (m - r_{A})(m - r_{B}) \right) \\&\quad= m^{2} + (m - r_{A})(m - r_{B}).\end{aligned}
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.10 (Redundant units in an MLP).** Consider a single-hidden-layer MLP with scalar inputs and outputs, $h$ hidden units with activation function $\sigma : {\mathbb{R}} \to {\mathbb{R}}$, and an output bias. The parameter space is ${\mathcal{W}} = {\mathbb{R}}^{3h+1}$ with parameters $w = (a_{1}, b_{1}, c_{1}, \ldots, a_{h}, b_{h}, c_{h}, d)$, and the parameter–function map is

$$
f_{w}(x) = d + \sum_{i=1}^{h}a_{i} \, \sigma(b_{i} x + c_{i}).
$$

Here, for each hidden unit $i$, $a_{i}$ is the outgoing weight, $b_{i}$ is the incoming weight, and $c_{i}$ is the bias. The output bias is $d$.

**(a)** Suppose $a_{i} = 0$ (unit $i$ has zero outgoing weight). Show that the directions $\delta b_{i}$ and $\delta c_{i}$ are degenerate at $w$.

**(b)** Suppose $b_{i} = 0$ (unit $i$ has zero incoming weight). Show that the direction $(\delta a_{i}, \delta d) = (1, -\sigma(c_{i}))$ (with all other components zero) is degenerate at $w$.

**(c)** Suppose $h \geq 2$ and $(b_{i}, c_{i}) = (b_{j}, c_{j})$ for some $i \neq j$ (units $i$ and $j$ have the same incoming weights and biases). Show that the direction $(\delta a_{i}, \delta a_{j}) = (1, -1)$ (with all other components zero) is degenerate at $w$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** At $a_{i} = 0$, the parameter–function map reduces to

$$
f_{w}(x) = d + 0 \cdot \sigma(b_{i} x + c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) = d + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}).
$$

This expression does not involve $b_{i}$ or $c_{i}$ at all. Therefore $\Phi$ is constant in the $b_{i}$ and $c_{i}$ directions at this point, so $D_{\delta b_i}\Phi(w) = 0$ and $D_{\delta c_i}\Phi(w) = 0$. Both are degenerate directions.

Note that this argument is purely algebraic, following from the multiplicative structure $a_{i} \cdot \sigma(\ldots)$, and requires no conditions on $\sigma$ (not even continuity or differentiability).

**(b)** At $b_{i} = 0$, unit $i$ computes the constant $\sigma(0 \cdot x + c_{i}) = \sigma(c_{i})$ for all $x$, so

$$
f_{w}(x) = d + a_{i}\,\sigma(c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}).
$$

In the direction $(\delta a_{i}, \delta d) = (1, -\sigma(c_{i}))$, we compute

$$
\begin{aligned}f_{w + \epsilon\,v}(x)&= (d - \epsilon\,\sigma(c_{i})) + (a_{i} + \epsilon)\,\sigma(c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) \\&= d + a_{i}\,\sigma(c_{i}) + \epsilon\bigl(\sigma(c_{i}) - \sigma(c_{i})\bigr) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) = f_{w}(x).\end{aligned}
$$

So $D_{(\delta a_i, \delta d)}\Phi(w) = 0$ and this direction is degenerate. Intuitively, increasing $a_{i}$ scales up the constant contribution $a_{i}\,\sigma(c_{i})$ to the output, and decreasing $d$ by the same amount compensates exactly.

**(c)** When $(b_{i}, c_{i}) = (b_{j}, c_{j})$, units $i$ and $j$ compute the same activation, so their combined contribution to $f_{w}$ is

$$
a_{i}\,\sigma(b_{i} x + c_{i}) + a_{j}\,\sigma(b_{j} x + c_{j}) = (a_{i} + a_{j})\,\sigma(b_{i} x + c_{i}).
$$

In the direction $(\delta a_{i}, \delta a_{j}) = (1, -1)$, this combined contribution changes by $\sigma(b_{i} x + c_{i}) - \sigma(b_{j} x + c_{j}) = 0$. All other terms in $f_{w}$ are unchanged, so $D_{(1,-1)}\Phi(w) = 0$. Again, no conditions on $\sigma$ are needed.

:::

:::callout {title="Note" tone="blue"}

**Remark (Localised symmetries in neural networks).** Each degenerate direction identified in the exercises above corresponds to a localised symmetry: a curve of functionally equivalent parameters that continuously extends only within a subset of parameter space.

1. In the DLN, the global change-of-basis symmetry $(A, B) \mapsto (G A, B G^{-1})$ for invertible $G \in {\mathbb{R}}^{m\times m}$ accounts for $m^{2}$ degenerate directions. These directions are present even when $A$ and $B$ have full rank. However, as we showed in Exercise 2.9, when $A$ or $B$ drops rank, $(m - r_{A})(m - r_{B})$ additional degenerate directions open up. These extra directions are localised to the rank-deficient region of parameter space.
2. In the MLP, at a parameter with $a_{i} = 0$, the path $t \mapsto (\ldots, a_{i}, b_{i} + t, c_{i}, \ldots)$ traces equivalent parameters within $\{a_{i} = 0\}$ (since $f_{w}$ does not depend on $b_{i}$ when $a_{i} = 0$), but this does not extend to a symmetry at nearby parameters with $a_{i} \neq 0$. Similarly, at a parameter with $(b_{i}, c_{i}) = (b_{j}, c_{j})$, the path transferring weight between units $i$ and $j$ is a localised version of the sum symmetry from Exercise 2.5.

:::

:::callout {title="Note" tone="blue"}

**Remark (Rank of a neural network parameter).** In both exercises above, the degree of degeneracy at a parameter is controlled by the amount of redundant capacity in the network. For the two-layer DLN, this is measured by the rank of the product $BA$: a rank-$r$ linear map can be implemented with a hidden dimension of $r$, leaving $m - r$ dimensions redundant. For a general single-hidden-layer MLP, this idea generalises in that we can define the rank of a parameter $w$ as the minimum number of hidden units needed to implement $f_{w}$ (Farrugia-Roberts 2022; Farrugia-Roberts 2024). In the linear case, this "neural network rank" coincides with the matrix rank of $BA$. In both settings, lower rank corresponds to a higher number of degenerate directions.

:::

:::callout {title="Note" tone="blue"}

**Remark (Measure zero degenerate sets).** When a parameter–function map is degenerate somewhere but not everywhere, it is often the case that it is degenerate only within a measure-zero subset of parameter space. This means that sampling parameters uniformly at random results in a degenerate parameter with probability zero. However, this does not mean that the degeneracies can be dismissed. The learning process applies a non-random selection pressure and may select parameters from a measure-zero set. Moreover, the existence of degenerate parameters can have practical consequences for nearby non-degenerate parameters, and the collective neighbourhoods of all degenerate parameters comprise a non-measure-zero subset of parameter space.

:::
