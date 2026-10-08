---
id: 'f9ba3db5-43b1-408b-975e-80227409b322'
title: "B.6.17 Appendix A: the replica method"
tldr: "Appendix A: why the annealed approximation errs, the replica method for the Ising perceptron, and the spherical perceptron with its power-law learning curve."
summary_for_tutor: "Appendix A (A.1-A.3) of Iliad worksheet B.6 Physics of Deep Learning. Covers Jensen's inequality for annealed vs quenched, the replica identity with E Z^Q and overlaps q^ab, replica symmetry, the two-basin result of Gyorgyi, and the spherical perceptron whose annealed learning curve decays as a power law with exponent one. Contains Exercise A.1 (the quenched calculation via replicas) and Exercise A.2 (annealed learning curve of the spherical perceptron), with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## A. The replica method

Section 2.3 introduced the quenched free energy $$-{\mathbb{E}}_{\rm data}\log Z$$ and the annealed approximation (2.18) that replaces it by $$-\log{\mathbb{E}}_{\rm data}Z$$, and Section 2.6 used that approximation to analyze the Ising perceptron. This appendix explains how the quenched average is computed exactly, by the *replica method*, and what the annealed approximation misses. We keep the Ising perceptron of Section 2.6 as the running example, in the notation and normalization of that section: $$N$$ binary weights $$\theta\in\{\pm1\}^{N}$$, a binary teacher $$\theta^{*}$$, Gaussian inputs, $$n=\alpha N$$ examples, and the partition function (2.39). The classic reference for everything here is Engel and Van den Broeck (Engel & Van den Broeck 2001).

\### A.1 What the annealed approximation gets wrong

Jensen's inequality gives $$\log{\mathbb{E}} Z\geq{\mathbb{E}}\log Z$$, so the annealed free energy $$-\log{\mathbb{E}} Z$$ is always a lower bound on the quenched one. To see what drives the gap, write $$Z = e^{-N\varphi}$$, where the free-energy density $$\varphi$$ fluctuates from dataset to dataset. Exponentiation turns modest fluctuations of $$\varphi$$ into enormous fluctuations of $$Z$$: a dataset whose $$\varphi$$ is below the typical value by a constant is exponentially rare, but it contributes an exponentially large $$Z$$, and the two exponentials compete at the same order in $$N$$. The average $${\mathbb{E}} Z$$ can therefore be dominated by vanishingly rare datasets, while the typical dataset, which is what $${\mathbb{E}}\log Z$$ describes, behaves differently. (This is the familiar behavior of lognormal random variables, whose mean sits far in the upper tail. The mean is a poor summary of a heavy-tailed quantity.)

For the Ising perceptron the direction of the error follows. The datasets that dominate $${\mathbb{E}} Z$$ are those that constrain the student unusually weakly, and weakly constrained students sit at low overlap. The annealed average therefore overweights poorly aligned students, and overestimates the amount of data needed to learn: it puts the transition to perfect generalization at $$\alpha_{c}^{\rm ann}\approx1.45$$, where the exact calculation sketched below gives $$\alpha_{c}\approx1.245$$ (Gy"orgyi 1990). The structure of the transition, two basins exchanging dominance, is the same in both.

:::callout {title="Note" tone="blue"}

**Remark.** Annealing does not always err so gently. Here the model is realizable (a teacher exists) and the fluctuations of $$\varphi$$ are tame, so annealing shifts a number without changing the picture. In general the annealed computation can fail qualitatively, most famously for models with discrete weights at large load, where it can predict negative entropies (fewer than one consistent student, nonsense for a count) and spurious transition points.

:::

\### A.2 Replicas

The full calculation computes $${\mathbb{E}}_{\rm data}\log Z$$ through the identity

$$
{\mathbb{E}}\log Z = \lim_{Q\to0}\frac{{\mathbb{E}} Z^{Q} - 1}{Q}\qquad\big(\text{from }Z^{Q} = e^{Q\log Z}= 1 + Q\log Z + O(Q^{2})\big)\,.
$$

The strategy is to compute $${\mathbb{E}} Z^{Q}$$ for *integer* $$Q$$, where it has a transparent meaning, obtain a formula analytic in $$Q$$, and continue it to $$Q\to0$$. For integer $$Q$$, $$Z^{Q}$$ is the partition function of $$Q$$ independent copies, or *replicas*, of the student, all judged against the same dataset. For the Ising perceptron, from (2.39),

$$
{\mathbb{E}} Z^{Q} = \frac{1}{2^{NQ}}\sum_{\theta^1,\ldots,\theta^Q\in\{\pm1\}^N}\;{\mathbb{E}}_{\rm data}\prod_{\mu=1}^{n}\prod_{a=1}^{Q}\Theta\big(y^{\mu}\,(\theta^{a}\cdot x^{\mu})\big)\,.
$$

The data average is easy, because the inputs are Gaussian. For fixed replicas and teacher, each example enters only through the $$Q+1$$ numbers $$u^{a} = \theta^{a}\cdot x^{\mu}/\sqrt{N}$$ and $$v = \theta^{*}\cdot x^{\mu}/\sqrt{N}$$, which are exactly jointly Gaussian (they are linear in $$x^{\mu}$$), with mean zero and a covariance determined entirely by the *overlap matrix*

$$
\begin{aligned}q^{ab}&= \frac{\theta^a\cdot\theta^b}{N}\,,\qquad R^{a} = \frac{\theta^a\cdot\theta^*}{N}\,: \\ {\mathbb{E}}[u^{a}u^{b}]&= q^{ab}\,,\quad {\mathbb{E}}[u^{a}v] = R^{a}\,,\quad {\mathbb{E}}[v^{2}] = 1\,.\end{aligned}
$$

The product of step functions asks that every $$u^{a}$$ have the sign of $$v$$, and the probability of that event is some function $$e^{-e(q,R)}$$ of the overlaps alone: a Gaussian orthant probability in $$Q+1$$ dimensions. Since the examples are independent, the data average of the product over $$\mu$$ is the $$n$$-th power, $$e^{-n\,e(q,R)}= e^{-\alpha N\,e(q,R)}$$. For $$Q=1$$ the only overlap is $$R$$, the orthant is a wedge, and $$e(R) = -\log(1-\varepsilon(R))$$ is the energy term of Section 2.6.

The disorder is gone. In its place, the replicas are coupled through the overlaps $$q^{ab}$$, and the sum over the $$Q$$ binary vectors can be organized by the value of the overlaps, exactly as the sum over one binary vector was organized by $$R$$ in Exercise 2.3(c). Writing $$e^{N\,h(q,R)}$$ for the number of $$Q$$-tuples of students with prescribed overlaps (for $$Q=1$$ this is the binomial count of Exercise 2.3(c)), and replacing the sum over overlaps by an integral,

$$
{\mathbb{E}} Z^{Q} \;\approx\; \int dq\,dR\; e^{-N\,s_Q(q,R)}\,,\qquad s_{Q}(q,R) := Q\log 2 - h(q,R) + \alpha\,e(q,R)\,.
$$

This is the replicated version of the one-variable action (2.44) of Section 2.6, to which it reduces at $$Q=1$$. At large $$N$$ the integral is dominated by the minimum of $$s_{Q}$$ over the overlaps, and the replica identity (A.1) then gives the quenched free-energy density

$$
\Phi(\alpha) := -\frac{1}{N}\,{\mathbb{E}}_{\rm data}\log Z \;=\; \lim_{Q\to0}\;\frac{1}{Q}\,\min_{q,R}\,s_{Q}(q,R)\,.
$$

Compare the annealed approximation, which is $$\min_{R} s_{1}(R)$$: the annealed calculation keeps a *single* replica, and so never sees the coupling $$q^{ab}$$ between replicas that the shared data induce. That coupling is precisely the information about dataset-to-dataset fluctuations that Appendix A.1 found missing.

*Replica symmetry.* To make (A.5) concrete one needs $$h$$ and $$e$$ as functions of the $$Q(Q+1)/2$$ overlaps, and a way to continue the result in $$Q$$. The standard ansatz, *replica symmetry*, is to take $$q^{ab}= q$$ for all $$a\neq b$$ and $$R^{a} = R$$. It is natural, since the saddle-point equations are symmetric under permuting replicas, and it reduces the problem to two scalars. Under it, both $$h$$ and $$e$$ become one-dimensional Gaussian integrals: the orthant probability collapses to an integral over a single shared Gaussian "field" of the Gaussian tail function $$H(x) = \int_{x}^{\infty}\frac{dz}{\sqrt{2\pi}}e^{-z^2/2}$$, and the count $$h$$ is handled by introducing conjugate variables for the constraints, which reduces it to a one-site problem in the manner of the mean-field Ising model of Section 2.4. The resulting expression is analytic in $$Q$$ and can be differentiated at $$Q=0$$. As a caution, symmetric equations *can* have asymmetric solutions, and this happens in physical systems, famously in spin glasses; the assumption must be checked, and for the perceptron problems considered here it holds.

*The result.* For the Ising perceptron, the replica-symmetric calculation (Gy"orgyi 1990) reproduces the two-basin structure found in Exercise 2.3: an interior solution with $$R^{*}(\alpha)<1$$ that drifts toward the teacher as data accumulate, and the teacher solution $$R=1$$, which exchange dominance in a first-order transition. Only the number moves, from $$\alpha_{c}^{\rm ann}\approx1.45$$ to $$\alpha_{c}\approx1.245$$. A guided walk through the calculation follows.

:::callout {title="Exercise" tone="amber"}
**Exercise A.1 (The quenched calculation, via replicas).** Work through the following program for the Ising perceptron, in as much detail as your appetite allows; full details are in (Engel & Van den Broeck 2001, chs. 2 and 7).

**(a)** *Replicate.* For integer $$Q$$, write $${\mathbb{E}} Z^{Q}$$ as in (A.2): a $$Q$$-fold copy of the system, coupled only through the shared data.

**(b)** *Average over data.* Show that for fixed replicas and teacher, $$u^{a} = \theta^{a}\cdot x/\sqrt{N}$$ and $$v = \theta^{*}\cdot x/\sqrt{N}$$ are exactly jointly Gaussian with the covariance (A.3), and that the data average factorizes across examples, each contributing the same function $$e^{-e(q,R)}$$ of the overlaps. Check that at $$Q=1$$, $$e(R) = -\log(1-\varepsilon(R))$$ with $$\varepsilon$$ the wedge formula (2.41).

**(c)** *Push forward to the order parameters.* Insert delta functions fixing $$q^{ab}$$ and $$R^{a}$$ (in integral representation, with conjugate variables $$\hat q^{ab}$$, $$\hat R^{a}$$), so that the sum over the binary vectors factorizes over sites $$i=1,\ldots,N$$ and becomes the $$N$$-th power of a $$Q$$-spin sum. Conclude that $${\mathbb{E}} Z^{Q}$$ takes the form (A.4), and that the annealed action (2.44) is its $$Q=1$$ case.

**(d)** *Replica symmetry.* Take $$q^{ab}= q$$ for $$a\neq b$$ and $$R^{a} = R$$ (and likewise for the conjugates). Show that the orthant probability becomes $$e^{-e_{\rm RS}}= 2\int Dt\,H(\cdot)^{Q}$$ for an appropriate argument of the tail function $$H$$, built from $$q$$, $$R$$, and a single Gaussian variable $$t$$, and that the site sum becomes a one-dimensional Gaussian integral of $$(2\cosh(\cdot))^{Q}$$. Continue both in $$Q$$ and expand to first order at $$Q=0$$.

**(e)** *Use the symmetry of Gibbs learning.* A student drawn uniformly from the consistent set is statistically indistinguishable from the teacher, since the teacher is itself a uniformly random binary vector consistent with the data. Argue that this forces $$q = R$$ at the saddle: the overlap between two Gibbs students equals their overlap with the teacher. One scalar remains, with one conjugate.

**(f)** *Solve.* The saddle-point equations for $$R(\alpha)$$ are transcendental. Solve them numerically and show that there are two competing solutions, an interior one and $$R=1$$, whose free energies cross at $$\alpha_{c}\approx1.245$$. Compare with the annealed $$\alpha_{c}^{\rm ann}\approx1.45$$ of Exercise 2.3(g), and explain the direction of the shift using Appendix A.1.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The six steps are their own outline; we record only the checkpoints. (Step 2) Conditioned on the $$\theta^{a}$$ and $$\theta^{*}$$, the $$u^{a}$$ and $$v$$ are linear in the Gaussian vector $$x$$, hence exactly Gaussian, with the covariances (A.3); independence over examples gives the $$n$$-th power, so the per-example factor is $$e^{-e(q,R)}$$ with $$e = -\log P[\text{all }Q\text{ replicas agree with the teacher}]$$, a $$(Q{+}1)$$-dimensional Gaussian orthant probability. At $$Q=1$$ the orthant is the double wedge of Exercise 2.3(b), of probability $$1-\varepsilon(R)$$. (Step 3) With $$\delta(Nq^{ab}-\theta^{a}\cdot\theta^{b}) = \int\frac{d\hat q^{ab}}{2\pi}e^{i\hat q^{ab}(Nq^{ab}-\sum_i\theta^a_i\theta^b_i)}$$ and likewise for $$R^{a}$$, the exponent is a sum over sites of identical terms, so $$\sum_{\{\theta\}}= \big(\sum_{\theta^1_i,\ldots,\theta^Q_i=\pm1}e^{-i\sum_{a<b}\hat q^{ab}\theta^a\theta^b - i\sum_a\hat R^a\theta^a\theta^*}\big)^{N}$$; the saddle point over the conjugates then defines $$h(q,R)$$. At $$Q=1$$ only $$\hat R$$ survives and the site sum is $$2\cosh\hat R$$, reproducing the binomial entropy after the saddle in $$\hat R$$. (Step 4) Under replica symmetry, the $$Q$$ correlated Gaussians $$u^{a}$$ can be written as $$\sqrt{q}\,t + \sqrt{1-q}\,z^{a}$$ with $$t$$ shared and the $$z^{a}$$ independent, and $$v$$ correlated with $$t$$ through $$R$$; integrating out the $$z^{a}$$ gives the orthant probability as $$2\int Dt\,H(\cdot)^{Q}$$, where the argument of $$H$$ is linear in $$t$$ with coefficients built from $$q$$ and $$R$$. The site sum becomes $$\int Dz\,\big(2\cosh(\sqrt{\hat q}\,z+\hat R)\big)^{Q}$$ after decoupling the $$\hat q\,\theta^{a}\theta^{b}$$ term by the same trick. Both are analytic in $$Q$$, and $$\frac{1}{Q}\log\int(\cdots)^{Q}\to\int(\cdots)\log(\cdots)$$ as $$Q\to0$$. (Step 5) The teacher is a uniformly random binary vector consistent with every example, exactly as a Gibbs student is, so the two are exchangeable, and $${\mathbb{E}}[\theta^{a}\cdot\theta^{b}] = {\mathbb{E}}[\theta^{a}\cdot\theta^{*}]$$ at the saddle: $$q = R$$. (Step 6) Solving the remaining pair of equations numerically, the interior solution exists for all $$\alpha$$ up to a spinodal and the teacher solution $$R=1$$ always exists; their free energies cross at $$\alpha_{c}\approx1.245$$ (Gy"orgyi 1990), below the annealed $$1.45$$. The annealed average is dominated by rare, weakly constraining datasets, which overweight poorly aligned students and so require more data before the teacher basin wins; removing that bias moves the transition earlier.

:::

\### A.3 A variant: the spherical perceptron

The replica method is easiest to push all the way to closed form in a variant of the problem with *continuous* weights, which is also the classic case in which the annealed and quenched learning curves can be compared analytically. Keep everything in Section 2.6 the same, but let the weights be real, $$\theta,\theta^{*}\in{\mathbb{R}}^{N}$$. Since $$f_{\theta} = \mathrm{sign}(\theta\cdot x)$$ is invariant under $$\theta\to\lambda\theta$$ with $$\lambda>0$$, remove the redundant scale by putting the weights on a sphere,

$$
|\theta|^{2} = |\theta^{*}|^{2} = N\,,
$$

normalized so that individual weights stay of order one, and let the prior be the uniform measure $$\pi(\theta)\,d\theta$$ on the sphere. This is the *spherical perceptron*. The wedge formula (2.41) for the generalization error is unchanged, since its derivation used only that $$(\theta\cdot x,\theta^{*}\cdot x)/\sqrt{N}$$ is a Gaussian pair with correlation $$R$$, which holds for any $$\theta$$ with $$|\theta|^{2} = N$$. What changes is the entropy: the number of students at overlap $$R$$ becomes the *volume* of the slice of the sphere at overlap $$R$$. Decompose $$\theta = R\,\theta^{*} + \theta_{\perp}$$ with $$\theta_{\perp}\perp\theta^{*}$$. The constraint (A.6) gives $$|\theta_{\perp}|^{2} = N(1-R^{2})$$, so the slice is a sphere of radius $$\sqrt{N(1-R^{2})}$$ in the $$(N-1)$$-dimensional orthogonal complement, of volume $$\propto\big(N(1-R^{2})\big)^{(N-2)/2}$$, and

$$
\frac{1}{N}\log\int_{\theta:\,R(\theta)=R}d\theta\,\pi(\theta) \;=\; h(R) = \tfrac{1}{2}\log(1-R^{2}) + \text{const}+ O\big(\tfrac{1}{N}\log N\big)\,.
$$

Repeating the annealed calculation of Exercise 2.3(d) with this entropy gives

$$
\begin{aligned}{\mathbb{E}}_{\rm data}Z&\approx \int_{-1}^{1} dR\; e^{-N\,S_{\rm ann}(R)}\,, \\ S_{\rm ann}(R)&:= \underbrace{-\tfrac{1}{2}\log(1-R^2)}_{\text{entropy}}\;\underbrace{-\;\alpha\log\big(1-\varepsilon(R)\big)}_{\text{energy}}\,,\end{aligned}
$$

and the annealed free-energy density is

$$
\Phi_{\rm ann}(\alpha) := \min_{R} S_{\rm ann}(R)\,.
$$

Figure 9 shows $$S_{\rm ann}$$ for several loads. The entropy–energy competition is the same as for the Ising perceptron, but the outcome is different: the entropy $$-\frac{1}{2}\log(1-R^{2})$$ diverges as $$R\to1$$, so the perfectly aligned state is infinitely penalized, the minimum always sits in the interior, and it slides continuously from $$R=0$$ toward $$R=1$$ as $$\alpha$$ grows. There is no phase transition. This is the answer to the closing question of Exercise 2.3(h): the binary weights of the Ising perceptron give the aligned state finite entropy, $$h(1)=0$$, and that is what allows it to compete as a separate basin.

![The annealed action of the spherical perceptron, (A.8), for (bottom to top at ), with the minimizer marked on each curve. The entropy pins the minimum at when ; increasing the load slides it smoothly toward larger overlap, and the entropic wall at keeps it in the interior. One basin at every , moving continuously: no phase transition.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-spherical-action-38e3cfe7.png)

The annealed action $$S_{\rm ann}(R)$$ of the spherical perceptron, (A.8), for $$\alpha\in\{0,0.25,0.5,0.75,1\}$$ (bottom to top at $$R=0$$), with the minimizer marked on each curve. The entropy pins the minimum at $$R=0$$ when $$\alpha=0$$; increasing the load slides it smoothly toward larger overlap, and the entropic wall at $$R=1$$ keeps it in the interior. One basin at every $$\alpha$$, moving continuously: no phase transition.

*The learning curve.* The large-$$\alpha$$ behavior follows by expanding near $$R=1$$. Writing $$R = \cos(\pi\varepsilon)$$, so that $$\varepsilon$$ is the generalization error itself, $$1-R^{2}\approx(\pi\varepsilon)^{2}$$ and

$$
S_{\rm ann}\approx -\log(\pi\varepsilon) + \alpha\,\varepsilon + \text{const}\,,
$$

which is minimized at

$$
\varepsilon_{\rm ann}(\alpha) \simeq \frac{1}{\alpha}\,.
$$

The generalization error decays as a *power law* in the amount of data, with exponent one: the simplest instance of the scaling laws of Section 7. The exact, quenched treatment (Seung et al. 1992; Engel & Van den Broeck 2001) runs through the replica steps of Exercise A.1 with the volume entropy (A.7) in place of the count (here replica symmetry can be justified by the convexity of the region of the sphere consistent with the data), and yields

$$
\varepsilon_{\rm Gibbs}(\alpha)\simeq\frac{0.625}{\alpha}\,:
$$

the same exponent, with a different constant. As in Appendix A.1, the annealed average overweights poorly aligned students and overestimates the error, $$1/\alpha>0.625/\alpha$$; and since the model is realizable, the exponent survives the approximation even though the constant does not.

:::callout {title="Exercise" tone="amber"}
**Exercise A.2 (The annealed learning curve of the spherical perceptron).** **(a)** Derive the slice entropy (A.7), and assemble the annealed action (A.8) by repeating the steps of Exercise 2.3(d).

**(b)** Derive the saddle-point condition for (A.9), and show that $$R=1$$ is never a minimum, in contrast with Exercise 2.3(f).

**(c)** Verify the large-$$\alpha$$ learning curve (A.11), and show that at small $$\alpha$$ the annealed theory predicts $$R\propto\alpha$$. Sketch the full learning curve $$\varepsilon(\alpha)$$.

**(d)** Which steps of Exercise A.1 change when the count of binary students is replaced by the volume (A.7), and which do not?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Decompose $$\theta = R\,\theta^{*} + \theta_{\perp}$$. The spherical constraint $$|\theta|^{2} = N$$ forces $$|\theta_{\perp}|^{2} = N(1-R^{2})$$, so the slice at fixed $$R$$ is a sphere of radius $$\sqrt{N(1-R^{2})}$$ in the $$(N-1)$$-dimensional orthogonal complement, of volume $$\propto\big(N(1-R^{2})\big)^{(N-2)/2}= e^{\frac{N}{2}\log(1-R^2)+O(\log N)}$$, giving $$h(R) = \frac{1}{2}\log(1-R^{2})$$ up to constants. The data factor $$(1-\varepsilon(R))^{n} = e^{N\alpha\log(1-\varepsilon)}$$ is as in Exercise 2.3(d), and collecting exponents gives (A.8).

**(b)** Setting $$S_{\rm ann}'(R) = 0$$ with $$\varepsilon(R) = \arccos(R)/\pi$$ gives

$$
\frac{R}{1-R^{2}}= \frac{\alpha}{\pi\sqrt{1-R^{2}}\,\big(1-\varepsilon(R)\big)}\quad\Longleftrightarrow\quad \frac{R}{\sqrt{1-R^{2}}}= \frac{\alpha}{\pi\,(1-\varepsilon(R))}\,.
$$

As $$R\to1$$ the entropy term $$-\frac{1}{2}\log(1-R^{2})\to+\infty$$ while the energy term stays finite, so $$S_{\rm ann}\to+\infty$$ and $$R=1$$ is never a minimum; the minimizer is always interior.

**(c)** With $$R = \cos(\pi\varepsilon)$$ and $$\varepsilon\to0$$: $$1-R^{2} = \sin^{2}(\pi\varepsilon)\approx(\pi\varepsilon)^{2}$$, so $$S_{\rm ann}\approx-\log(\pi\varepsilon)+\alpha\varepsilon+\text{const}$$, minimized at $$\varepsilon = 1/\alpha$$. For small $$R$$ the entropic part is $$\approx R^{2}/2$$ and $$\varepsilon(R)\approx\frac{1}{2}-R/\pi$$, so $$-\alpha\log(1-\varepsilon)\approx-\alpha\log\frac{1}{2}-\frac{2\alpha}{\pi}R$$, and minimizing $$R^{2}/2-\frac{2\alpha}{\pi}R$$ gives $$R^{*} = 2\alpha/\pi\propto\alpha$$. The learning curve rises linearly from $$R=0$$, bends over, and approaches $$R=1$$ with the power-law tail $$\varepsilon\simeq1/\alpha$$.

**(d)** Steps 1, 2, 5, and 6 are unchanged: the data average sees only the overlaps, and the Gibbs-symmetry argument holds for any prior invariant under the symmetries of the problem. Step 3 changes: the sum over binary vectors becomes an integral over $$Q$$ points of the sphere, and the count $$h(q,R)$$ becomes the log-volume of the set of $$Q$$-tuples with prescribed overlaps, a Gaussian integral with a $$\log\det$$ of the overlap matrix; under replica symmetry it is $$\frac{1}{2}\big[(Q-1)\log(1-q) + \log(1-q+Qq-QR^{2})\big]$$ up to constants, whose $$Q\to0$$ derivative reproduces (A.7) at $$q=R$$. Step 4 is then the same $$H$$-function integral. The outcome differs because this entropy diverges at $$R\to1$$: no competing basin, no transition, and a learning curve $$\varepsilon\simeq0.625/\alpha$$ (Seung et al. 1992).

:::
