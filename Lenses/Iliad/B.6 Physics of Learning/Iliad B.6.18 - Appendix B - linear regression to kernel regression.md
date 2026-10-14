---
id: 'efe5cf01-505d-456b-abd6-b04b9888f156'
title: "B.6.18 Appendix B: linear regression to kernel regression"
tldr: "Appendix B, first part: linear regression, normal equations and the geometry of least squares, and linear models on fixed nonlinear features."
summary_for_tutor: "Appendix B intro, B.1 and B.2 of Iliad worksheet B.6 Physics of Deep Learning. Covers the notation X, Y, Delta, the normal equations, the cases P<n and P>n, least squares as orthogonal projection, weighted least squares, and feature maps psi with the feature matrix Psi (linear in the parameters but nonlinear in x). Contains Exercise B.1 (least squares by hand) and Exercise B.2 (a three-point feature calculation), with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Aleksander Czejdo
  - Tudor Dimofte
  - Brianna Grado-White
  - Charles Renshaw-Whitman
source_url: https://iliad-intensive.org/learning/qft/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## B. From linear regression to kernel regression

This appendix is a self-contained review of models that are *linear in their parameters*: linear regression, regression on fixed nonlinear features, kernel regression, and kernel *ridge* regression. It ends with the observation that a neural network linearized around its initialization — the ansatz (4.1) of Section 4 — is exactly such a model, so that training it amounts to kernel ridge regression. Nothing here requires large width, gradient-flow asymptotics, or moving features; those are the subjects of Sections 3–5, and this appendix supplies the linear algebra they rest on. Readers who found the kernel formulas of Sections 4.1 and 4.6 appearing out of thin air may want to read it first. [^6]

We use the notation of Section 3.1: training data $$(x^{\mu},y^{\mu})_{\mu=1}^{n}$$ with $$x^{\mu}\in {\mathbb{R}}^{d}$$ and $$y^{\mu}\in{\mathbb{R}}$$; a model $$f_{\theta}:{\mathbb{R}}^{d}\to {\mathbb{R}}$$ with parameters $$\theta\in {\mathbb{R}}^{P}$$; and $$f^{\mu} := f_{\theta}(x^{\mu})$$ for its values on the training inputs. It is convenient to stack the data into matrices,

$$
X := \begin{pmatrix}(x^{1})^{T} \\ \vdots \\ (x^{n})^{T}\end{pmatrix} \in {\mathbb{R}}^{n\times d}\,,\qquad Y := \begin{pmatrix}y^{1} \\ \vdots \\ y^{n}\end{pmatrix} \in {\mathbb{R}}^{n}\,,\qquad f := \begin{pmatrix}f^{1} \\ \vdots \\ f^{n}\end{pmatrix} \in {\mathbb{R}}^{n}\,,
$$

so that $$X^{\mu}{}_{j} = x^{\mu}_{j}$$ is the $$j$$-th coordinate of the $$\mu$$-th input, and the inputs and their labels are stacked in the same way. Throughout, the loss is the MSE of Section 4.1.1,

$$
{{\mathcal L}}_{\theta} = \frac{1}{2}\sum_{\mu=1}^{n} (f^{\mu}-y^{\mu})^{2} = \frac{1}{2}\,|f-Y|^{2} = \frac{1}{2}\,\delta_{\mu\nu}\Delta^{\mu}\Delta^{\nu}\,,\qquad \Delta^{\mu} := f^{\mu} - y^{\mu}\,,
$$

with $$\Delta\in{\mathbb{R}}^{n}$$ the residual. Many references (including the notebook this appendix is drawn from) normalize the loss as $$\frac{1}{2n}|f-Y|^{2}$$ instead; this rescales the ridge parameter $$\lambda$$ below by a factor of $$n$$ and the learning rate $$\eta$$ by a factor of $$1/n$$, and changes nothing else.

\### B.1 Linear regression

The simplest model is linear in the inputs,

$$
f_{\theta}(x) = \theta\cdot x = \sum_{j=1}^{d} \theta^{j} x_{j}\,,\qquad \theta\in {\mathbb{R}}^{d}\,,
$$

so that $$P=d$$ and the vector of training predictions is $$f = X\theta$$. (An intercept can be included by appending a constant coordinate $$x_{d+1}=1$$ to every input, as in Exercise B.1 below.) The loss $${{\mathcal L}}_{\theta} = \frac{1}{2}|X\theta - Y|^{2}$$ is a convex quadratic function of $$\theta$$, with gradient

$$
\nabla_{\theta} {{\mathcal L}} = X^{T}(X\theta - Y) = X^{T}\Delta\,.
$$

This has the shape that every gradient in these notes has: the transpose of the Jacobian $$\partial f^{\mu}/\partial\theta^{j}$$ — here the constant matrix $$X$$ — acting on the residual, *cf.* (4.10). Setting the gradient to zero gives the *normal equations*

$$
X^{T}X\,\theta = X^{T}Y\,.
$$

Since the loss is convex, every solution of (B.5) is a global minimizer, and there are no other critical points. What the solutions look like depends on how $$P=d$$ compares with $$n$$.

**Fewer parameters than data, $$P<n$$.**  If the columns of $$X$$ are linearly independent — the generic situation when $$d\leq n$$ — then $$X^{T}X$$ is positive definite, since $$v^{T}X^{T}Xv = |Xv|^{2}>0$$ for $$v\neq 0$$. There is a unique minimizer,

$$
\theta_{*} = (X^{T}X)^{-1}X^{T}Y\,.
$$

The normal equations say that the residual $$\Delta_{*} = X\theta_{*}-Y$$ is orthogonal to every column of $$X$$. Equivalently, the prediction $$X\theta_{*}$$ is the *orthogonal projection* of $$Y$$ onto the column space $$\mathrm{col}(X)\subset{\mathbb{R}}^{n}$$, the set of all prediction vectors the model can produce (Figure 10). Fitting is projecting. The projection $$X\theta_{*}$$ is unique even in cases where $$\theta_{*}$$ is not.

![Least squares, geometrically. The normal equations say that the residual is orthogonal to the column space of , so the fitted prediction vector is the orthogonal projection of onto . 'Orthogonal' refers to the Euclidean metric on the space of function values on the training set.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-lsq-projection-abb51df1.png)

Least squares, geometrically. The normal equations $$X^{T}\Delta_{*}=0$$ say that the residual is orthogonal to the column space of $$X$$, so the fitted prediction vector $$X\theta_{*}$$ is the orthogonal projection of $$Y$$ onto $$\mathrm{col}(X)$$. "Orthogonal" refers to the Euclidean metric $$\delta_{\mu\nu}$$ on the space $${\mathbb{R}}^{n}$$ of function values on the training set.

It is worth pausing on the word "orthogonal." Least squares minimizes the Euclidean ($$L^{2}$$) distance between $$X\theta$$ and $$Y$$, and the projection is orthogonal with respect to the Euclidean metric $$\delta_{\mu\nu}$$ on $${\mathbb{R}}^{n}$$ — the same metric on the space of function values that was made explicit in Section 4.1.1. This metric is a *choice*, hidden inside the phrase "mean squared error." It declares that an error of a given size counts the same at every data point, and that errors at different data points are independent. Any other positive-definite metric $$g_{\mu\nu}$$ on $${\mathbb{R}}^{n}$$ defines a different loss $${{\mathcal L}}^{g} = \frac{1}{2}g_{\mu\nu}\Delta^{\mu}\Delta^{\nu}$$, with a different minimizer

$$
\theta_{*}^{g} = (X^{T}gX)^{-1}X^{T}gY\,,
$$

which is the $$g$$-orthogonal projection of $$Y$$ onto $$\mathrm{col}(X)$$ ("weighted least squares"). Unless $$Y$$ already lies in $$\mathrm{col}(X)$$, different metrics give genuinely different fitted functions; see Exercise B.1(d). Note that $$g_{\mu\nu}$$ is a metric on the space of function values *indexed by* the data points, not a metric on the input space $${\mathbb{R}}^{d}$$.

**More parameters than data, $$P>n$$.**  If $$d>n$$, or more generally if the columns of $$X$$ are linearly dependent, then $$X^{T}X$$ is singular. The normal equations still have solutions (Exercise B.1(b)), but now infinitely many: an affine subspace of $${\mathbb{R}}^{P}$$ of dimension $$P-\mathrm{rank}(X)$$. If moreover $$X$$ has full row rank $$n$$, then $$Y\in\mathrm{col}(X)$$ and *every* solution interpolates the data exactly, $$X\theta = Y$$, with zero loss. The loss has no way to prefer one of them. Something else must make the choice; that is the subject of Appendix B.3, and it is where kernels come from. Far from being an edge case, $$P>n$$ is the normal situation for neural networks.

:::callout {title="Exercise" tone="amber"}
**Exercise B.1 (Least squares by hand).** **(a)** Differentiate $${{\mathcal L}}_{\theta} = \frac{1}{2}|X\theta-Y|^{2}$$ with respect to a single coordinate $$\theta^{j}$$, assemble the components into (B.4), and derive the normal equations (B.5). Explain geometrically why they say that the residual is orthogonal to every column of $$X$$.

**(b)** Show that if $$X$$ has full column rank then $$X^{T}X$$ is positive definite, so that (B.6) is the unique minimizer. Show that the normal equations are always consistent (*i.e.* $$X^{T}Y\in\mathrm{col}(X^{T}X)$$), and that if $$P>n$$ they have infinitely many solutions.

**(c)** Fit the affine function $$f(x) = \theta^{1} + \theta^{2} x$$ to the three points $$x\in\{-1,0,1\}$$ with labels $$y=x^{2}$$; that is, take

$$
X = \begin{pmatrix}1 & -1 \\ 1 & 0 \\ 1 & 1\end{pmatrix}\,,\qquad Y = \begin{pmatrix}1 \\ 0 \\ 1\end{pmatrix}\,.
$$

Find $$\theta_{*}$$, the predictions, the residual, and the loss. Is the remaining error a failure of optimization or of representation?

**(d)** Repeat (c) with the weighted loss (B.7) for $$g = \mathrm{diag}(1,4,1)$$, which trusts the middle data point four times as much as the others. Check that the fitted function changes.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$\partial{{\mathcal L}}/\partial\theta^{j} = \sum_{\mu} X^{\mu}{}_{j}\big(\sum_{k} X^{\mu}{}_{k}\theta^{k} - y^{\mu}\big) = [X^{T}(X\theta-Y)]_{j}$$. The $$j$$-th normal equation sets the inner product of the $$j$$-th column of $$X$$ with the residual to zero, so $$\Delta_{*}\perp\mathrm{col}(X)$$; hence $$X\theta_{*}$$ is the orthogonal projection of $$Y$$ onto $$\mathrm{col}(X)$$.

**(b)** $$v^{T}X^{T}Xv = |Xv|^{2}$$ vanishes only if $$Xv=0$$, which for $$v\neq 0$$ is impossible when the columns are independent; so $$X^{T}X$$ is positive definite and invertible. Consistency: $$\ker(X^{T}X) = \ker X$$ (if $$X^{T}Xv=0$$ then $$|Xv|^{2} = v^{T}X^{T}Xv = 0$$), and for any matrix $$A$$ one has $$\mathrm{col}(A^{T}) = (\ker A)^{\perp}$$, so $$\mathrm{col}(X^{T}X) = (\ker X)^{\perp} = \mathrm{col}(X^{T})\ni X^{T}Y$$. If $$P>n$$ then $$\dim\ker X = P-\mathrm{rank}(X)\geq P-n>0$$, and adding any element of $$\ker X$$ to a solution gives another.

**(c)** $$X^{T}X = \mathrm{diag}(3,2)$$, $$X^{T}Y = (2,0)^{T}$$, so $$\theta_{*} = (2/3,0)^{T}$$: the constant function $$2/3$$. Predictions $$(2/3,2/3,2/3)^{T}$$, residual $$(-1/3,2/3,-1/3)^{T}$$, loss $$\frac{1}{2}\cdot\frac{6}{9}= \frac{1}{3}$$. The optimization is exact (the problem is convex and was solved in closed form); the error is representational — no affine function agrees with $$x^{2}$$ at three points. Exercise B.2 repairs it by adding a feature.

**(d)** $$X^{T}gX = \mathrm{diag}(6,2)$$ and $$X^{T}gY = (2,0)^{T}$$, so $$\theta^{g}_{*} = (1/3,0)^{T}$$: the constant function $$1/3$$, pulled toward the heavily weighted middle label $$y=0$$. Residual $$(-2/3,1/3,-2/3)^{T}$$. A different metric on $${\mathbb{R}}^{n}$$ gives a different fit.

:::

\### B.2 Linear regression with nonlinear features

"Linear model" is a statement about how the parameters enter, not about the shape of the fitted function. Choose, *before looking at any labels*, a *feature map*

$$
\psi:{\mathbb{R}}^{d}\to {\mathbb{R}}^{P}\,,\qquad \psi(x) = \big(\psi_{1}(x),\ldots,\psi_{P}(x)\big)\,,
$$

and consider the model

$$
f_{\theta}(x) = \theta\cdot\psi(x) = \sum_{i=1}^{P} \theta^{i}\,\psi_{i}(x)\,,\qquad \theta\in{\mathbb{R}}^{P}\,.
$$

This is a weighted sum of $$P$$ fixed shapes $$\psi_{i}$$. It can be as nonlinear in $$x$$ as the shapes are, but it is linear in $$\theta$$. Standard choices include monomials in the coordinates of $$x$$ up to some degree $$m$$ (giving $$P=\binom{d+m}{m}$$), Fourier modes, Gaussian bumps $$e^{-|x-c_k|^2/2\sigma^2}$$ centered at chosen points $$c_{k}$$, and *random features* $$\psi_{i}(x) = \phi(a_{i}\cdot x)$$ with the $$a_{i}$$ drawn at random and then frozen — the last being a one-hidden-layer network whose first layer is never trained.

Stacking the feature vectors of the training inputs into the $$n\times P$$ *feature matrix*

$$
\Psi^{\mu}{}_{i} := \psi_{i}(x^{\mu})\,,
$$

the training predictions are $$f = \Psi\theta$$. Note that $$\Psi^{\mu}{}_{i} = \partial f^{\mu}/\partial\theta^{i}$$: the feature matrix is precisely the Jacobian $$J$$ of Section 4.2, which for a linear model is a constant. Linear regression is the special case $$\psi(x) = x$$, $$\Psi = X$$, and *everything* in Appendix B.1 goes through verbatim with $$X$$ replaced by $$\Psi$$: the normal equations are $$\Psi^{T}\Psi\,\theta = \Psi^{T}Y$$; if $$P\leq n$$ and $$\Psi$$ has full column rank, the unique minimizer is $$\theta_{*} = (\Psi^{T}\Psi)^{-1}\Psi^{T}Y$$; and if $$P>n$$ there are infinitely many interpolants.

![Choosing is choosing the model. The same seven data points (black), interpolated exactly by three different fixed feature maps with : polynomials of degree six, trigonometric functions of period one with three harmonics, and Gaussian bumps centered at the data. All three drive the training loss to zero; they disagree everywhere outside the training range (shaded), and that disagreement was decided before the labels were read.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-feature-maps-a29ab07e.png)

Choosing $$\psi$$ is choosing the model. The same seven data points (black), interpolated exactly by three different fixed feature maps with $$P=n=7$$: polynomials of degree six, trigonometric functions of period one with three harmonics, and Gaussian bumps centered at the data. All three drive the training loss to zero; they disagree everywhere outside the training range (shaded), and that disagreement was decided before the labels were read.

Replacing $$X$$ by $$\Psi$$ changes the algebra not at all, and changes the model completely. Figure 11 shows three feature maps, each with $$P=n$$, fitted to the same seven points. Each interpolates the data exactly, and they disagree everywhere else. Which is right? The data cannot say: the behavior away from the training set was fixed by the choice of $$\psi$$, which was made before the labels were seen. The feature map is the model's *inductive bias*, made explicit.

![One fixed extra feature can make a hard problem linear. Left: two classes of points in the plane, on concentric rings. No line separates them, since the convex hull of each class contains the origin. Right: after appending the single feature , the rings sit at two different heights, and a horizontal plane separates them. Nothing has been learned: we supplied the radial coordinate.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-radial-lift-9f1ae3c1.png)

One fixed extra feature can make a hard problem linear. Left: two classes of points in the plane, on concentric rings. No line separates them, since the convex hull of each class contains the origin. Right: after appending the single feature $$\psi_{3}= c\,(u^{2}+v^{2})$$, the rings sit at two different heights, and a horizontal plane $$\psi_{3}= c\,r_{0}^{2}$$ separates them. Nothing has been learned: we supplied the radial coordinate.

Why would one ever want a very large $$P$$? Figure 12 gives the classic answer. Two classes of points on concentric rings cannot be separated by a line in the plane. Append one fixed feature, $$\psi(u,v) = (u,\,v,\,c\,(u^{2}+v^{2}))$$, and the classes become separable by a plane in $${\mathbb{R}}^{3}$$: a model that is linear in the lifted coordinates is a circle in the original ones. The price is that $$P$$ grows fast. All monomials of degree $$3$$ in $$d=1000$$ input coordinates already give $$P = \binom{1002}{3}\approx 1.7\times 10^{8}$$, and Gaussian bumps centered at every point of a continuum give $$P=\infty$$. Yet there are only $$n$$ data points, and the fit is determined by $$n$$ numbers. Nothing about the problem should require a $$P\times P$$ inverse — so where does $$P$$ actually enter? Answering that question honestly is the content of the next two sections.

:::callout {title="Exercise" tone="amber"}
**Exercise B.2 (A three-point feature calculation).** Take the same three points $$x\in\{-1,0,1\}$$ with labels $$y=x^{2}$$ as in Exercise B.1(c), but now the feature map $$\psi(x) = (1,\,\sqrt{2}\,x,\,x^{2})$$.

**(a)** Form the feature matrix $$\Psi$$ and find coefficients $$\theta$$ that interpolate all three labels. The representational failure of Exercise B.1(c) is gone: what changed?

**(b)** Explain precisely how the predictor can be nonlinear in $$x$$ while the regression problem remains linear.

**(c)** If the last feature is replaced by $$c\,x^{2}$$ for some $$c\neq 0$$, what changes: the fitted function, its coefficient, or both?

**(d)** Write the inner product $$K(x,z) := \psi(x)\cdot\psi(z)$$ in closed form, without vector notation. This is a preview of Appendix B.3.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$\Psi = \begin{pmatrix}1 & -\sqrt{2} & 1 \\ 1 & 0 & 0 \\ 1 & \sqrt{2} & 1\end{pmatrix}$$, which is invertible ($$P=n=3$$), so exactly one $$\theta$$ interpolates: $$\theta = (0,0,1)^{T}$$, giving $$f_{\theta}(x) = x^{2}$$ and predictions $$(1,0,1)^{T}$$. What changed is that $$Y$$ now lies in $$\mathrm{col}(\Psi) = {\mathbb{R}}^{3}$$.

**(b)** All nonlinearity in $$x$$ sits inside the fixed functions $$\psi_{i}$$; $$f_{\theta} = \sum_{i}\theta^{i}\psi_{i}$$ depends on $$\theta$$ linearly, so the loss is quadratic in $$\theta$$ and the normal equations are linear.

**(c)** The coefficient becomes $$1/c$$, the product $$\theta^{3}\psi_{3} = x^{2}$$ is unchanged, and so is the fitted function. (With the ridge penalty of Appendix B.4 the rescaling *would* change the fit, since $$|\theta|^{2}$$ is not invariant under it.)

**(d)** $$K(x,z) = 1+2xz+x^{2}z^{2} = (1+xz)^{2}$$.

:::

[^6]: This appendix adapts a lecture and an exercise notebook prepared by Charles Renshaw-Whitman for the Iliad Intensive, translated into the notation of Section 3.1.
