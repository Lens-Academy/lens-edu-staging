---
id: '682fd43f-1124-42b9-a8f1-2a730b906769'
title: "B.6.4 The Ising perceptron and the link to QFT"
tldr: "The Ising perceptron as a learning problem with a first-order transition to perfect generalization as data increases, and a short guide comparing the notes to QFT."
summary_for_tutor: "Sections 2.6-2.7 of Iliad worksheet B.6 Physics of Deep Learning. Sets up the teacher-student Ising perceptron with load alpha=n/N, and Exercise 2.3 (overlap R as magnetization, generalization error arccos(R)/pi, entropy, annealed action s(R), teacher basin at R=1, transition near alpha about 1.45, dictionary with the magnet) with a collapsed solution. Section 2.7 translates the vocabulary to QFT: Euclidean weights, no i/hbar, hbar played by temperature, 1/N or 1/n. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 2.6 The Ising perceptron: a first-order transition in learning

We close the physics part of this section with a complete statistical-mechanics analysis of a learning problem, built to run in parallel with the Ising magnet. It is the simplest model we know in which *more data* produces a genuine phase transition to *perfect generalization*, and it goes back to Gyorgyi (Gy"orgyi 1990); see (Engel & Van den Broeck 2001, Chapter 7). It is presented as a walk-through exercise; solutions are in Appendix C, but try each part before reading them.

*Setup.* A *teacher* is a fixed vector of binary weights $$\theta^{*}\in\{\pm1\}^{N}$$. Inputs are Gaussian, $$x\sim{{\mathcal N}}(0,I_{N})$$, and the teacher labels them by

$$
y(x) = \mathrm{sign}(\theta^{*}\cdot x)\,.
$$

A *student* is another binary vector $$\theta\in\{\pm1\}^{N}$$, guessing labels the same way, $$f_{\theta}(x) = \mathrm{sign}(\theta\cdot x)$$. This model is called the *Ising perceptron*, because its weights take the values of Ising spins. We observe $$n$$ examples $$(x^{\mu},y^{\mu})$$ with $$y^{\mu} = y(x^{\mu})$$, and do Bayesian learning at zero temperature with a uniform prior, in the sense of Section 2.2: the per-sample loss is $$0$$ if the student classifies the example correctly and $$\infty$$ otherwise, so the posterior is uniform on the students that classify *every* example correctly. Since teacher and student agree on $$x$$ exactly when $$y(x)\,(\theta\cdot x)>0$$,

$$
p(\theta) \;\propto\; \prod_{\mu=1}^{n}\Theta\big(y^{\mu}\,(\theta\cdot x^{\mu})\big)\,,\qquad Z = \frac{1}{2^{N}}\sum_{\theta\in\{\pm1\}^N}\;\prod_{\mu=1}^{n}\Theta\big(y^{\mu}\,(\theta\cdot x^{\mu})\big)\,,
$$

with $$\Theta(u) = 1$$ for $$u>0$$ and $$0$$ otherwise. With the factor $$1/2^{N}$$, $$Z$$ is the fraction of all students consistent with the data. Both $$N$$ and $$n$$ will be taken large, at fixed ratio: the *load*

$$
\alpha := \frac{n}{N}\,,
$$

the number of examples per parameter, is the control parameter of the problem.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.3 (★) (The Ising perceptron).** **(a)** *The order parameter is a magnetization.* Define the *overlap* $$R(\theta) = \frac{1}{N}\theta\cdot\theta^{*}\in[-1,1]$$ and the alignment variables $$s_{i} := \theta_{i}\theta_{i}^{*}\in\{\pm1\}$$. Show that $$R = \frac{1}{N}\sum_{i} s_{i}$$: the overlap *is* the magnetization of the spins $$s_{i}$$. Learning the teacher means magnetizing them to $$R=1$$.

**(b)** *Generalization error.* Show that a student at overlap $$R$$ misclassifies a fresh Gaussian input with probability

$$
\varepsilon(R) = \frac{\arccos R}{\pi}\,.
$$

[*Hint:* project $$x$$ onto the plane spanned by $$\theta$$ and $$\theta^{*}$$; the projection is an isotropic two-dimensional Gaussian, and the two decision boundaries are diameters meeting at angle $$\arccos R$$. When do the signs disagree?]

**(c)** *Entropy: the same $$h$$ as the magnet.* Show that the number of students at overlap $$R$$ is $$\binom{N}{\frac{1+R}{2}N}$$, so that by Stirling's formula

$$
\begin{aligned}\frac{1}{N}\log\#\{\theta : R(\theta) = R\} \;\to\; h(R) &= \log 2 - \frac{1-R}{2}\log(1-R) \\ &\quad - \frac{1+R}{2}\log(1+R)\,,\end{aligned}
$$

*identical* to the magnet's entropy (2.24) with $$m\to R$$.

**(d)** *Push forward to one variable.* Average $$Z$$ over datasets. The examples are independent, and each is classified correctly by a student at overlap $$R$$ with probability $$1-\varepsilon(R)$$, so

$$
{\mathbb{E}}_{x} Z = \frac{1}{2^{N}}\sum_{\theta}\big(1-\varepsilon(R(\theta))\big)^{n}\,.
$$

Trade the sum over $$\theta$$ for an integral over $$R$$ using (c), and show that at fixed load $$\alpha$$ and large $$N$$,

$$
{\mathbb{E}}_{x} Z \;\approx\; \int_{-1}^{1}dR\; e^{-N\,s(R)}\,,\qquad s(R) = \log 2 - h(R) - \alpha\log\big(1-\varepsilon(R)\big)\,.
$$

This is the exact analogue of the magnet's (2.25): an entropy term counting states, and a "field" term rewarding alignment. The aligning field is now the *data*, and its strength is the load $$\alpha$$. (Averaging $$Z$$ rather than $$\log Z$$ is the annealed approximation (2.18). It preserves all the qualitative structure here and shifts the numbers only slightly; Appendix A explains how to do the exact calculation.)

**(e)** Plot $$s(R)$$ for several values of $$\alpha$$ and locate its critical points. Do you expect a phase transition? At which $$\alpha$$?

**(f)** *The teacher basin.* $$R=1$$ is the perfectly aligned state, where the student is the teacher. Show that $$s(1) = \log 2$$ for *every* $$\alpha$$ (zero entropy, but zero data cost), and that $$R=1$$ is always a local minimum: writing $$\delta = 1-R$$, deviating from the teacher gains entropy $$\sim\frac{\delta}{2}\log(1/\delta)$$ but costs data-fit $$\alpha\varepsilon\sim\alpha\sqrt{2\delta}/\pi$$ (expand $$\arccos$$), and $$\sqrt{\delta}\gg\delta\log(1/\delta)$$. This differs from the magnet, where the aligned state sat at the bottom of a smooth well and was not always a minimum.

**(g)** *The interior basin, the crossing, and the transition.* At $$\alpha=0$$, $$s$$ is minimized at $$R=0$$ with $$s(0) = 0 < s(1)$$: the disordered cloud of typical students dominates. As $$\alpha$$ grows, this interior minimum $$R^{*}(\alpha)$$ drifts toward $$1$$ and its value rises. Numerically, find the load $$\alpha_{c}$$ at which the two basins exchange dominance, $$s(R^{*}(\alpha_{c})) = s(1)$$. You should find $$\alpha_{c}\approx 1.45$$, with the interior minimum still at $$R^{*}\approx 0.70$$, that is, generalization error $$\varepsilon^{*}\approx 0.25$$. Conclude that at $$\alpha_{c}$$ the typical student jumps from $$25\%$$ error to *zero* error: a first-order transition to perfect generalization. Then connect to Exercise 2.2 with $$\alpha$$ as the control parameter: what do $$\partial_{\alpha}\varphi$$ and $$-\partial_{\alpha}^{2}\varphi$$ look like at finite $$N$$, and what plays the role of the latent heat? Finally, find the load at which the interior minimum disappears altogether, and explain what happens in between in the light of the metastability discussion of Section 2.5.

**(h)** *The dictionary.* Complete the table:

| **Ising magnet** | **Ising perceptron** |
| --- | --- |
| spins $$s_{i}\in\{\pm1\}$$ | alignments $$s_{i}= \theta_{i}\theta_{i}^{*}\in\{\pm1\}$$ |
| magnetization $$m$$ | overlap $$R$$ |
| entropy $$h(m)$$ | entropy $$h(R)$$ *(the same function)* |
| aligning field $$B$$ | ? |
| knob swept across the transition | ? |
| ordered phase $${\mathbb{E}}(m)\approx\pm1$$ | ? |
| jump in $${\mathbb{E}}(m)$$ as a function of $$B$$ | ? |

Also articulate one structural *difference*: in the magnet the two competing minima are symmetry partners; what are they here, and which ingredient of (c) made a sharp transition possible at all? (What would change for spherical weights $$\theta\in{\mathbb{R}}^{N}$$, $$|\theta|^{2} = N$$, where the slice at overlap $$R$$ has volume $$\propto(1-R^{2})^{N/2}$$? Appendix A.3 works this case out.)
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$R = \frac{1}{N}\sum_{i}\theta_{i}\theta_{i}^{*} = \frac{1}{N}\sum_{i}s_{i}$$ since $$(\theta_{i}^{*})^{2} = 1$$. The map $$\theta\mapsto s$$ is a bijection of the hypercube (a "gauge transformation"), so the uniform measure goes to the uniform measure, and the perceptron's order parameter is literally a magnetization.

**(b)** Both labels depend only on the projection of $$x$$ onto $$\mathrm{span}(\theta,\theta^{*})$$, which is an isotropic two-dimensional Gaussian. The decision boundaries are two diameters at angle $$\vartheta = \arccos R$$; the signs disagree exactly on the double wedge between them, of angular fraction $$2\vartheta/2\pi = \vartheta/\pi$$. Note that the answer does not depend on $$N$$, and holds for any $$\theta$$ with $$|\theta|^{2} = N$$, binary or not.

**(c)** A student at overlap $$R$$ agrees with the teacher on exactly $$\frac{1+R}{2}N$$ coordinates ($$s_{i} = +1$$), giving the binomial count; Stirling gives $$h(R)$$, the binary entropy at magnetization $$R$$. Note $$h(0) = \log2$$ and $$h(1) = 0$$: the latter is *finite*, because exactly one state sits at $$R=1$$.

**(d)** Independence over examples gives the $$n$$-th power. Trading the sum for an integral, $$\frac{1}{2^{N}}\sum_{\theta}\to\int dR\,e^{N[h(R)-\log2]}$$, and $$(1-\varepsilon)^{n} = e^{N\alpha\log(1-\varepsilon)}$$; collecting exponents gives $$s(R)$$ as stated. (The $$\log2$$ normalizes $$s(0) = 0$$ at $$\alpha=0$$.)

**(e)** The curves are shown in Figure 15. At $$\alpha=0$$, $$s = \log2-h(R)$$ has a single minimum at $$R=0$$, the bulk of the hypercube. As $$\alpha$$ grows, the interior minimum drifts toward larger $$R$$ and its value rises (note $$s(0) = \alpha\log2$$), while $$R=1$$ stays pinned at $$s(1) = \log2$$. For $$\alpha$$ large enough there are two competing local minima separated by a barrier: exactly the two-basin structure of Exercise 2.2. One should therefore expect a first-order transition at the load where the interior minimum's value crosses $$\log2$$, near $$\alpha\approx1.45$$ from the plot; at $$\alpha=1.7$$ the interior minimum survives only as a metastable dip above $$\log2$$. No transition is expected at small $$\alpha$$, where the interior minimum is the only relevant one and moves smoothly.
![The annealed action of the Ising perceptron, (2.44), for several loads. Interior local minima are marked with circles; the teacher state , where exactly, with squares. The two basins exchange dominance near .](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-ising-perceptron-action-6c8259f6.png)

The annealed action $$s(R)$$ of the Ising perceptron, (2.44), for several loads. Interior local minima are marked with circles; the teacher state $$R=1$$, where $$s(1) = \log2$$ exactly, with squares. The two basins exchange dominance near $$\alpha\approx1.45$$.

**(f)** At $$R=1$$: $$h(1) = 0$$ and $$\varepsilon(1) = 0$$, so $$s(1) = \log2$$ for all $$\alpha$$. Near $$R=1$$ with $$\delta = 1-R$$: $$h(1-\delta) = \frac{\delta}{2}\log\frac{2}{\delta}+O(\delta)$$, while $$\arccos(1-\delta)\approx\sqrt{2\delta}$$ gives data cost $$-\alpha\log(1-\varepsilon)\approx\alpha\sqrt{2\delta}/\pi$$. Since $$\sqrt{\delta}\gg\delta\log(1/\delta)$$ as $$\delta\to0$$, $$s(1-\delta)>s(1)$$: a basin around the teacher at every $$\alpha>0$$. It is protected by the singular cost of the first errors, which is what a smooth well cannot provide.

**(g)** Minimizing $$s$$ over the interior numerically (Figure 16, left), the interior branch value crosses $$s(1) = \log2$$ at $$\alpha_{c}\approx1.45$$, with minimizer $$R^{*}\approx0.70$$ and $$\varepsilon^{*} = \arccos(0.70)/\pi\approx0.25$$. The order parameter jumps from $$0.70$$ to $$1$$ (middle panel). With $$\alpha$$ as the control parameter of Exercise 2.2: $$\varphi(\alpha) = \min_{R}s(R)$$ has a kink at $$\alpha_{c}$$; at finite $$N$$, $$\partial_{\alpha}\varphi = {\mathbb{E}}[-\log(1-\varepsilon(R))]$$ is a sigmoid interpolating between the branch slopes $$-\log(1-\varepsilon(R^{*}))\approx0.29$$ and $$0$$, over a window of width $$\sim1/(N\Delta\varphi')$$ (right panel), and $$-\partial_{\alpha}^{2}\varphi$$ is a peak of height $$\propto N$$. The role of the latent heat is played by the jump in $$-\log(1-\varepsilon)$$, the per-example log-likelihood released when the student snaps onto the teacher. Past $$\alpha_{c}$$ the interior minimum survives as a local minimum until the *spinodal* $$\alpha\approx1.73$$, where it merges with the barrier and disappears. In the window $$1.45\lesssim\alpha\lesssim1.73$$ a local learning dynamics (flipping a few weights at a time to improve alignment) can stay stuck at $$\varepsilon\approx0.25$$ even though perfect generalization is thermodynamically dominant: the information needed to identify the teacher is present in the data before the dynamics can find it, and generalization arrives abruptly and later than the data first permits. This is the metastability of Section 2.5, and a prototype of the delayed transitions of Section 5.7. (The exact, quenched treatment (Gy"orgyi 1990; Engel & Van den Broeck 2001) moves the transition to $$\alpha_{c}\approx1.245$$ but changes nothing structurally.)
![The Ising perceptron's phase transition. Left: the free-energy densities of the interior basin, , and of the teacher basin, , cross at ; the limiting is their minimum, with a kink. Middle: the order parameter jumps from to ; the dashed continuation is the metastable interior minimum, which disappears at the spinodal . Right: at finite , , computed from the integral (2.44), is a sigmoid sharpening into the step of height .](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-ising-perceptron-phase-432f1fea.png)

The Ising perceptron's phase transition. Left: the free-energy densities of the interior basin, $$s(R^{*}(\alpha))$$, and of the teacher basin, $$s(1) = \log2$$, cross at $$\alpha_{c}\approx1.45$$; the limiting $$\varphi(\alpha)$$ is their minimum, with a kink. Middle: the order parameter $$R^{*}(\alpha)$$ jumps from $$0.70$$ to $$1$$; the dashed continuation is the metastable interior minimum, which disappears at the spinodal $$\alpha\approx1.73$$. Right: at finite $$N$$, $$\partial_{\alpha}\varphi = {\mathbb{E}}[-\log(1-\varepsilon)]$$, computed from the integral (2.44), is a sigmoid sharpening into the step of height $$\approx0.29$$.

**(h)** Field $$B\leftrightarrow$$ the data term, the per-example log-likelihood $$\log(1-\varepsilon(R))$$, with strength $$\alpha$$; the knob swept $$=$$ the load $$\alpha = n/N$$, the amount of data; the ordered phase $$\leftrightarrow$$ perfect generalization $$R=1$$; the jump in $${\mathbb{E}}(m)$$ as a function of $$B$$ $$\leftrightarrow$$ the discontinuous drop of $$\varepsilon(R^{*})$$ from $$0.25$$ to $$0$$ as a function of $$\alpha$$. The structural difference: in the magnet the two competing minima are symmetry partners, while here they are an entropy-dominated basin and a data-dominated basin. The ingredient that makes the sharp transition possible is $$h(1) = 0$$ being *finite*: discreteness gives the perfectly aligned state a finite entropy, so it can compete as a separate basin. For spherical weights the slice entropy $$\frac{1}{2}\log(1-R^{2})$$ diverges to $$-\infty$$ as $$R\to1$$, the perfectly aligned state is infinitely penalized, the minimum always sits in the interior and slides continuously with $$\alpha$$, and there is no transition; the generalization error then decays smoothly, as $$\varepsilon\simeq0.625/\alpha$$ in the exact treatment (Appendix A.3).

:::

\### 2.7 Comparison with QFT

This short subsection is a translation guide, aimed mainly at readers arriving from high-energy or condensed-matter physics — if the words "action" and "path integral" mean more to you than "posterior" and "marginal likelihood," read on; everyone else may safely skip ahead.

Nearly everything in these notes lives, in the first instance, in *Euclidean equilibrium statistical mechanics*: probability distributions of Boltzmann–Gibbs form $$P \propto e^{-\beta E}$$, partition functions, free energies. For a field theorist, a partition function with sources,

$$
Z[J] = \int \mathcal{D}\phi\; e^{-S[\phi] \,+ \int J\,\phi}\,,
$$

is a moment generating functional; its logarithm generates connected correlation functions (cumulants); the action $$S$$ encodes the microscopic rules of the system, and a quadratic action means a free (Gaussian) theory, with everything else treated by perturbing around it. In these notes the role of the field $$\phi$$ is played variously by the weights $$\theta$$ of a network, by an order parameter such as the magnetization $$m$$ or the overlap $$R$$ of Sections 2.4 and 2.6, or — most usefully — by the network function $$f(x)$$ itself, with the input $$x$$ playing the role of the spacetime coordinate. Functional integrals over the network function are developed carefully in Sections 3.3 and 3.5, and the reader coming from QFT will find many familiar ingredients there dressed up as learning theory: Wick's theorem, sources, cumulants, effective actions.

If your instincts were trained on Lorentzian signature, picture everything here as already Wick-rotated. There is no $$i/\hbar$$: the weights $$e^{-S}$$ are real and positive, as after the standard continuation

$$
Z_{\rm QFT}= \int \mathcal{D}\phi\; e^{\frac{i}{\hbar} S[\phi]}\;\;\xrightarrow{\;\tau\,=\,it\;}\;\; Z_{\rm E}= \int \mathcal{D}\phi\; e^{- S_E [\phi]/\hbar}\,.
$$

The role of $$\hbar$$ — the parameter controlling the size of fluctuations around saddle points — is played here by temperature, or by $$1/N$$ at large width, or by $$1/n$$ at large sample size.

When we eventually study the *dynamics* of training as a field theory in Section 6, a genuinely real-time formalism does appear — a path integral over trajectories with a causal structure and a response field. That's the closest object in these notes to a Lorentzian field theory, and is precisely the Martin–Siggia–Rose construction of non-equilibrium statistical mechanics.

For readers who would like physics references alongside the learning-theory ones: David Tong's lecture notes (Tong 2012; Tong 2012; Tong 2012; Tong 2006) are a friendly introduction to statistical physics, statistical field theory, kinetic theory, and QFT respectively; Lancaster and Blundell (Lancaster & Blundell 2014) is a gentle conceptual route into QFT; Altland and Simons (Altland & Simons 2010) bridges toward condensed-matter field theory (and contains the Langevin/MSRJD material used in Section 6); Pathria (Pathria & Beale 2011) is a standard graduate statistical mechanics text; Goldenfeld (Goldenfeld 2018) is the classic on phase transitions and the renormalization group; and Zinn-Justin (Zinn-Justin 2002) is the encyclopedic reference for the functional formalism.
