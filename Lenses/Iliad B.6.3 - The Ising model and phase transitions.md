---
id: '933cc34c-8bad-4798-8f46-501477bc8c48'
title: "B.6.3 The Ising model and phase transitions"
tldr: "The mean-field Ising model solved by a saddle point, then Landau theory of first-order and second-order phase transitions, and Exercise 2.2 on finite-size signatures."
summary_for_tutor: "Sections 2.4-2.5 of Iliad worksheet B.6 Physics of Deep Learning. Covers the Ising model, magnetization as order parameter, mean-field approximation, entropy h(m) and the action s(m), the saddle-point equation m = tanh(beta(dJ m + B)), self-consistency, Landau expansion, first-order transition with metastability and hysteresis, and the second-order transition with the square-root law. Contains Exercise 2.2 (anatomy of a first-order transition) with a collapsed solution. Keep s(m), beta, J, B, d, N. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 2.4 A physics example: the Ising model

The analogy with thermal physics opens up a bag of well-developed approximation methods. We illustrate two of them, the *mean-field approximation* and the *saddle-point approximation at large $$N$$*, on the most famous model in statistical mechanics. For the physics of this example, well beyond what we cover here, see (Tong 2012, Chapter 1).

*The model.* Let $$\Lambda$$ be a graph with $$N$$ vertices and undirected edges $$\langle ij\rangle$$; typically $$\Lambda$$ is a regular lattice in $$D$$ dimensions, and every vertex has the same number $$d$$ of neighbors ($$d=2D$$ for a hypercubic lattice). At each vertex $$i$$ sits a *spin* $$s_{i}\in\{\pm 1\}$$. A state of the system is a choice of all $$N$$ spins, so there are $$2^{N}$$ states, and the energy of a state is

$$
E(s) = -J\!\!\sum_{\text{edges }\langle ij\rangle}\!\! s_{i} s_{j} \;-\; B\sum_{i=1}^{N} s_{i}\,.
$$

The *coupling* $$J>0$$ rewards neighboring spins for aligning with each other, and the *external magnetic field* $$B$$ rewards spins for aligning with it. At inverse temperature $$\beta$$ the Boltzmann distribution is $$p_{\beta}(s) = e^{-\beta E(s)}/Z$$ with $$Z(\beta,J,B) = \sum_{s\in\{\pm1\}^N}e^{-\beta E(s)}$$. Dimensionally, only the combinations $$\beta J$$ and $$\beta B$$ matter.

The simplest macroscopic quantity describing a state is its *magnetization*, the average spin,

$$
m(s) = \frac{1}{N}\sum_{i=1}^{N} s_{i} \;\in\; [-1,1]\,.
$$

It is our first example of an *order parameter*: a single number that summarizes an $$N$$-dimensional microscopic state for the purpose of the questions we want to ask. The question here is whether the spins align ($$|m|$$ close to $$1$$, an *ordered* phase) or not ($$m$$ near $$0$$, a *disordered* phase), and how this depends on $$\beta$$, $$J$$, and $$B$$.

*Mean-field approximation.* We would like to push the distribution $$p_{\beta}(s)$$ over $$2^{N}$$ states forward to a distribution over the single variable $$m$$. The interaction term stands in the way, since it couples each spin to its particular neighbors. The mean-field approximation replaces the neighbors of each spin by their average: suppose that each spin feels only the *average* field of all the others, so that in the neighbor sum we may replace each $$s_{j}$$ by $$m$$,

$$
\sum_{\langle ij\rangle}s_{i} s_{j} = \frac{1}{2}\sum_{i} s_{i} \underbrace{\sum_{j\sim i} s_j}_{\approx\, d\,m}\;\approx\; \frac{d\,m}{2}\sum_{i} s_{i} = \frac{N d}{2}\,m^{2}\,.
$$

(The factor $$\frac{1}{2}$$ compensates for counting each edge twice.) The energy becomes a function of $$m$$ alone,

$$
E(s) \;\approx\; -N\Big(\frac{dJ}{2}\,m^{2} + B\,m\Big)\,.
$$

This is an uncontrolled approximation for a lattice in low dimension, where a spin's few neighbors fluctuate along with it, but it turns out to be qualitatively right for $$D\geq 2$$ and quantitatively right for $$D\geq 4$$ (Tong 2012, Chapter 1). It becomes exact for a model in which every spin couples weakly to every other; that model, the Curie–Weiss magnet, returns in Section 5.1 as the prototype of mean-field limits of neural networks.

*Entropy, and the reduction to one variable.* With the energy depending only on $$m$$, the sum over states can be organized by the value of $$m$$:

$$
Z \;\approx\; \sum_{m}\Omega(m)\; e^{N\beta\left(\frac{dJ}{2}m^2 + Bm\right)}\,,\qquad \Omega(m) := \#\{s : m(s) = m\} = \binom{N}{\frac{1+m}{2}N}\,,
$$

since a state with magnetization $$m$$ has exactly $$\frac{1+m}{2}N$$ spins up. Stirling's formula gives

$$
\begin{aligned}\frac{1}{N}\log\Omega(m) \;&\xrightarrow{N\to\infty}\; h(m)\,, \\ h(m) &:= \log 2 - \frac{1-m}{2}\log(1-m) - \frac{1+m}{2}\log(1+m)\,,\end{aligned}
$$

the *entropy* per site at magnetization $$m$$: the log of the number of microscopic states compatible with the macroscopic value $$m$$. It is largest at $$m=0$$, where $$h = \log 2$$ and almost all of the $$2^{N}$$ states live, and it vanishes at $$m=\pm1$$, where exactly one state lives. Replacing the sum over $$m$$ by an integral (the spacing is $$2/N$$), the partition function becomes a one-dimensional integral,

$$
Z \;\approx\; \int_{-1}^{1}dm\; e^{-N\beta\, s(m)}\,,\qquad s(m) := -\frac{dJ}{2}m^{2} - Bm - \beta^{-1}h(m)\,.
$$

The function $$s(m)$$ is called the effective *action*, or the free-energy density at fixed $$m$$: energy minus temperature times entropy, per site. *We have reduced the problem from $$N$$ variables to one.* This is the general shape of every calculation in this section: push the microscopic distribution forward to an order parameter, at the price of an entropy term that counts how many microstates sit at each value.

*Saddle points.* At large $$N$$ the integrand $$e^{-N\beta s(m)}$$ is exponentially peaked at the *minima* of $$s$$, and the integral is dominated by a window of width $$\sim 1/\sqrt{N}$$ around the lowest one. This is the saddle-point approximation (also called Laplace's method), and it gives

$$
\varphi(\beta,J,B) = -\frac{1}{N}\log Z \;\xrightarrow{N\to\infty}\; \beta\,\min_{m} s(m)\,.
$$

The free energy is minimized, in exactly the sense promised in Section 2.3. The minimizer $$\bar m$$ is the magnetization the system actually displays. Setting $$\partial s/\partial m = 0$$ and using $$h'(m) = -\tanh^{-1}(m)$$,

$$
dJ\,\bar m + B = \beta^{-1}\tanh^{-1}(\bar m)\,,\qquad\text{that is,}\qquad \boxed{\;\bar m = \tanh\big(\beta\,(dJ\,\bar m + B)\big)\;}\,.
$$

This transcendental equation is best solved graphically (Figure 1). Depending on $$\beta$$, $$J$$, and $$B$$ it has one solution, or three; when there are three, the outer two are minima of $$s$$ and the middle one is a maximum.

![Graphical solution of the mean-field equation (2.27): intersections of with the diagonal. Left: high temperature, one solution at . Middle: low temperature at , three solutions, of which is a maximum of and are degenerate minima. Right: low temperature with , three solutions, with the positive one the global minimum.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-ising-tanh-00a269a2.png)

Graphical solution of the mean-field equation (2.27): intersections of $$\tanh\beta(dJ\bar m+B)$$ with the diagonal. Left: high temperature, one solution at $$\bar m=0$$. Middle: low temperature at $$B=0$$, three solutions, of which $$\bar m=0$$ is a maximum of $$s$$ and $$\pm\bar m$$ are degenerate minima. Right: low temperature with $$B>0$$, three solutions, with the positive one the global minimum.

*Self-consistency (an aside).* There is another route to (2.27), which is the form in which mean-field theory usually appears and which we will use in Section 5. Look at the effective field felt by a single spin $$s_{i}$$:

$$
B^{\rm eff}_{i} = -\frac{\partial E}{\partial s_{i}}= J\sum_{j\sim i}s_{j} + B \;\approx\; dJ\,m + B\,.
$$

A single spin in this field has partition function $$Z_{i} = \sum_{s_i=\pm1}e^{\beta B^{\rm eff}s_i}= 2\cosh\beta(dJm+B)$$ and mean $${\mathbb{E}}(s_{i}) = \beta^{-1}\partial_{B}\log Z_{i} = \tanh\beta(dJm+B)$$. If the approximation is to be consistent, the average that comes out must equal the average we put in, $$m = {\mathbb{E}}(s_{i})$$, and that is (2.27). Solve the one-body problem in the average environment, then demand that the average be reproduced: this is the prototype of every mean-field theory.

\### 2.5 Phases and phase transitions

Now we analyze the structure of the minima of $$s(m)$$, which control where the probability concentrates, as $$\beta$$, $$J$$, and $$B$$ are varied. Taylor-expanding the entropy, $$h(m) = \log 2 - \frac{m^{2}}{2}- \frac{m^{4}}{12}- \ldots$$, the action is

$$
s(m) \;\approx\; \text{const}- B\,m + \frac{1}{2}\big(\beta^{-1}- dJ\big)\,m^{2} + \frac{\beta^{-1}}{12}\,m^{4} + \ldots
$$

This expansion of a free energy in powers of an order parameter is called a *Landau theory*, and the qualitative analysis below depends only on its form, not on the microscopic model behind it.

*The ordered phase and a first-order transition.* Take $$dJ > \beta^{-1}$$: the coupling beats the temperature, the quadratic coefficient in (2.29) is negative, and $$s(m)$$ is a double well (Figure 2). The system wants to be ordered, with neighboring spins aligned; but aligned which way? The field decides. For $$B<0$$ the global minimum is near $$m=-1$$, for $$B>0$$ near $$m=+1$$, and at $$B=0$$ the two minima are exactly degenerate. As $$B$$ is swept through $$B_{c} = 0$$, the magnetization the system displays jumps from $$\bar m\approx -1$$ to $$\bar m\approx +1$$. This is a *first-order phase transition*.

![The action of (2.25) in the ordered phase (), for a negative, zero, and positive external field. The two minima tilt with ; the global minimum (orange) switches sides at . The suppressed minimum (grey) survives as a metastable state.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-ising-wells-b0a7fc0a.png)

The action $$s(m)$$ of (2.25) in the ordered phase ($$\beta dJ = 1.5$$), for a negative, zero, and positive external field. The two minima tilt with $$B$$; the global minimum (orange) switches sides at $$B=0$$. The suppressed minimum (grey) survives as a metastable state.

The structure of this transition is universal, in the sense that it follows from two isolated minima crossing and not from any detail of the model. Consider the expected magnetization, which by (2.14) is a derivative of the free energy with respect to the field:

$$
{\mathbb{E}}(m) = \frac{1}{N}\sum_{i}{\mathbb{E}}(s_{i}) = -\frac{1}{\beta}\frac{\partial\varphi}{\partial B}\,.
$$

At finite $$N$$, the two minima of $$s$$ are two competing *phases*, and $${\mathbb{E}}(m)$$ is a probability-weighted average of their magnetizations. As $$N\to\infty$$ the saddle-point approximation puts all the weight on the lower minimum, so $${\mathbb{E}}(m)$$ develops a discontinuity at $$B_{c}$$, and $$\varphi$$ itself develops a kink (Figure 3, left). *A discontinuity in a first derivative of the free-energy density, in the thermodynamic limit, is the definition of a first-order transition.* Its second derivative, the *susceptibility*

$$
\chi := \frac{\partial\,{\mathbb{E}}(m)}{\partial B}= -\frac{1}{\beta}\frac{\partial^{2}\varphi}{\partial B^{2}}= N\beta\,\mathrm{Var}(m)\,,
$$

is a peak whose height grows like $$N$$ and whose width shrinks like $$1/N$$: a nascent delta function (Figure 3, right). Genuine non-analyticity can occur only at $$N=\infty$$: at finite $$N$$ the partition function is a finite sum of analytic functions of $$B$$, so everything is smooth, and what one sees is a rapid *crossover* that sharpens as $$N$$ grows. Watching the peak in $$\chi$$ grow with $$N$$, rather than saturate, is the standard numerical diagnostic that separates a true transition from a crossover. Exercise 2.2 works out the shapes of these curves for a general first-order transition; they are worth remembering whenever "emergent capabilities" in models of growing size are under discussion (Section 7.6).

![Fingerprints of a first-order transition, in the mean-field Ising model at , computed from the one-dimensional integral (2.25) at finite . Left: the expected magnetization as a function of the field is a sigmoid of width , sharpening into a step. Right: the susceptibility is a peak of height and width .](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-ising-firstorder-b09cb8f4.png)

Fingerprints of a first-order transition, in the mean-field Ising model at $$\beta dJ = 1.5$$, computed from the one-dimensional integral (2.25) at finite $$N$$. Left: the expected magnetization as a function of the field is a sigmoid of width $$\propto 1/N$$, sharpening into a step. Right: the susceptibility $$\chi = \partial_{B}{\mathbb{E}}(m)$$ is a peak of height $$\propto N$$ and width $$\propto 1/N$$.

*Metastability and hysteresis.* The suppressed minimum in Figure 2 does not disappear when it stops being the global one. A system that starts there and evolves by local dynamics (flipping one spin at a time) must climb over the barrier to reach the true minimum, which takes a time exponential in $$N$$. In practice the system stays in the *metastable* phase until the field is pushed well past $$B_{c}$$, and the transition observed dynamically *lags* the thermodynamic one. This is *hysteresis*, familiar from real magnets. It is the reason the "$$\beta\leftrightarrow$$ training time" analogy of Section 2.1 must be handled with care at first-order transitions, and we will meet it again in the guise of delayed generalization (grokking) in Section 5.7.

*A second-order transition.* An *$$n$$-th order* phase transition is a discontinuity in the $$n$$-th derivative of the free-energy density as $$N\to\infty$$. The Ising model has a second-order transition too, at fixed $$B=0$$, as the temperature $$T=\beta^{-1}$$ crosses $$T_{c} = dJ$$ (Figure 4). Here nothing crosses anything: the single basin at $$m=0$$ flattens and splits into two symmetric ones. The quadratic coefficient in (2.29) changes sign at $$T_{c}$$, and the minima sit at

$$
\bar m^{2} = 3\,(\beta dJ - 1) \;\approx\; 3\,\Big(1-\frac{T}{T_{c}}\Big)\qquad (T\lesssim T_{c})\,,
$$

so the order parameter $$\bar m \propto (T_{c} - T)^{1/2}$$ moves *continuously* but not smoothly; $$\varphi$$ and $$\partial_{T}\varphi$$ are continuous, and the discontinuity sits in $$\partial_{T}^{2}\varphi$$ (the heat capacity). The point $$(T,B) = (T_{c},0)$$ is a *critical point*. Below it the two ordered states $$\pm\bar m$$ are exact mirror images, and the system must pick one: this is *spontaneous symmetry breaking*, the $$\mathbb{Z}_{2}$$ symmetry $$s\to -s$$ of the energy at $$B=0$$ being broken by the state. The exponent $$\frac{1}{2}$$ in (2.32) is an example of a *critical exponent*. Mean-field theory predicts it in every dimension, and it is wrong in low dimension: the exact value is $$\frac{1}{8}$$ in $$D=2$$ (Onsager), and there is no transition at all in $$D=1$$. Mean-field exponents become exact for $$D\geq 4$$. Understanding why is the subject of the renormalization group, for which see (Tong 2012).

![The second-order transition of the mean-field Ising model at . Left: the action for temperatures above, at, and below ; a single basin flattens and splits into two symmetric ones. Right: the resulting magnetization , continuous at but with the square-root singularity (2.32) (dashed).](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-ising-secondorder-35895785.png)

The second-order transition of the mean-field Ising model at $$B=0$$. Left: the action $$s(m)$$ for temperatures above, at, and below $$T_{c}= dJ$$; a single basin flattens and splits into two symmetric ones. Right: the resulting magnetization $$\bar m(T)$$, continuous at $$T_{c}$$ but with the square-root singularity (2.32) (dashed).

*Back to learning.* In the Bayesian model of Section 2.1, the natural control parameter is $$n\beta$$, the amount of data or training. The Ising analogue is sweeping $$\beta$$ at fixed $$B=0$$, which sees the second-order transition. First-order transitions in learning arise when two qualitatively different families of solutions compete, one entropically favored and one favored by the data; the Ising perceptron of Section 2.6 is the cleanest example. Before turning to it, the following exercise establishes what *every* first-order transition looks like at finite $$N$$.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.2 (★) (Anatomy of a first-order transition).** Consider any system whose partition function has the form $$Z(B) = \int d\theta\, e^{-N E(\theta,B)}$$, depending on *some* hyperparameter $$B$$. Here $$B$$ could be the inverse temperature, an external field, or the load $$\alpha$$ of Section 2.6; we have absorbed $$\beta$$ into $$E$$ to keep the setup general. Suppose that $$E(\theta,B)$$ has exactly two isolated minima, at $$\theta_{1}$$ and $$\theta_{2}$$. Then at large $$N$$ the integral is dominated by two competing phases. Letting $$U_{1},U_{2}$$ be small neighborhoods of $$\theta_{1},\theta_{2}$$,

$$
Z(B) \;\approx\; \int_{U_1}d\theta\,e^{-N E(\theta,B)}+ \int_{U_2}d\theta\,e^{-N E(\theta,B)}\;=\; e^{-N\varphi_1(B)}+ e^{-N\varphi_2(B)}\,,
$$

with $$\varphi_{i}(B) = -\frac{1}{N}\log\int_{U_i}d\theta\,e^{-NE(\theta,B)}= E(\theta_{i},B) + o(1)$$ the free-energy densities of the two basins. Suppose further that as $$B$$ crosses a critical value $$B_{c}$$ the two minimum values cross: $$\varphi_{1}(B_{c}) = \varphi_{2}(B_{c})$$ with $$\varphi_{1}'(B_{c})\neq\varphi_{2}'(B_{c})$$, where a prime denotes $$\partial_{B}$$.

**(a)** *Occupation.* Show that the probability of finding the system in basin $$i$$ is

$$
p_{i}(B) = \frac{e^{-N\varphi_i(B)}}{e^{-N\varphi_1(B)}+e^{-N\varphi_2(B)}}\,,
$$

and that, expanding to first order in $$\Delta B := B - B_{c}$$,

$$
p_{2}(B) \approx \frac{1}{1+e^{-N\,\Delta\varphi'\,\Delta B}}\,,\qquad \Delta\varphi' := \varphi_{1}'(B_{c}) - \varphi_{2}'(B_{c})\,,
$$

a logistic function of $$N\,\Delta\varphi'\,\Delta B$$. Over what window of $$B$$ does the system switch allegiance?

**(b)** *First derivative.* Show from (2.33) that

$$
\frac{\partial\varphi}{\partial B}\;\approx\; p_{1}(B)\,\varphi_{1}'(B_{c}) + p_{2}(B)\,\varphi_{2}'(B_{c})\,,
$$

the probability-weighted average of the branch slopes. Sketch it at finite $$N$$ and at $$N=\infty$$: a sigmoid of height $$\Delta\varphi'$$ sharpening into a jump. The kink in $$\varphi$$ itself is the defining discontinuity of a first-order transition. Show also, directly from the integral, that $$\partial_{B}\varphi = {\mathbb{E}}\big[\partial_{B} E(\theta,B)\big]$$: the observable that jumps is the one conjugate to the control parameter. When $$B=\beta$$ it is the energy, and the jump is the *latent heat*; for the Ising model with $$B$$ the field, it is the magnetization.

**(c)** *Second derivative.* Using $$\partial_{B} p_{1} = -\partial_{B} p_{2} = -N p_{1}p_{2}\,\Delta\varphi'$$ (verify this), show that

$$
-\frac{\partial^{2}\varphi}{\partial B^{2}}\;=\; N\,p_{1}p_{2}\,(\Delta\varphi')^{2} \;-\; p_{1}\varphi_{1}'' - p_{2}\varphi_{2}''\,.
$$

Sketch this curve. Near $$B_{c}$$, where $$p_{1}p_{2}\approx\frac{1}{4}$$, the first term is a peak of height $$\sim N(\Delta\varphi')^{2}/4$$ and width $$\sim 1/(N\Delta\varphi')$$, which converges to a delta function as $$N\to\infty$$. Show also that when $${{\mathcal O}}(\theta) = \partial_{B}E(\theta,B)$$ does not depend on $$B$$, $$-\partial_{B}^{2}\varphi = N\,\mathrm{Var}({{\mathcal O}})\geq 0$$. (For $$B=\beta$$ this is the heat capacity; for the Ising field it is the susceptibility.)

**(d)** *Plot it.* Take the minimal model $$\varphi_{1}(B) = a\,(B-B_{c})$$, $$\varphi_{2} = 0$$ and plot $$\varphi$$, $$\partial_{B}\varphi$$, and $$-\partial_{B}^{2}\varphi$$ for a few values of $$N$$. (Use a numerically stable $$\log(e^{x}+e^{y})$$.) Watching the peak grow with $$N$$ rather than saturate is the standard diagnostic separating a true transition from a smooth crossover.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$p_{i}$$ is the fraction of $$Z$$ contributed by basin $$i$$. With $$\varphi_{1}-\varphi_{2}\approx\Delta\varphi'\,\Delta B$$ near the crossing, $$p_{2} = (1+e^{-N(\varphi_1-\varphi_2)})^{-1}\approx(1+e^{-N\Delta\varphi'\Delta B})^{-1}$$. The switch happens over the window $$|\Delta B|\lesssim 1/(N\Delta\varphi')$$, which shrinks with system size.

**(b)** Differentiating $$\varphi = -\frac{1}{N}\log(e^{-N\varphi_1}+e^{-N\varphi_2})$$ gives $$\partial_{B}\varphi = p_{1}\varphi_{1}' + p_{2}\varphi_{2}'$$ exactly; near $$B_{c}$$ the slopes are $$\approx\varphi_{i}'(B_{c})$$. Directly from the integral, $$\partial_{B}\varphi = -\frac{1}{N}\partial_{B}\log Z = \frac{1}{Z}\int d\theta\,\partial_{B}E\,e^{-NE}= {\mathbb{E}}[\partial_{B}E]$$: the control parameter is itself a source, coupling to $${{\mathcal O}} = \partial_{B}E$$. *Sketch:* at finite $$N$$, $$\partial_{B}\varphi$$ is a sigmoid interpolating from $$\varphi_{1}'(B_{c})$$ to $$\varphi_{2}'(B_{c})$$ over the window of (a); as $$N\to\infty$$, $$\varphi\to\min(\varphi_{1},\varphi_{2})$$, continuous with a kink at $$B_{c}$$, and $$\partial_{B}\varphi$$ becomes a step of height $$\Delta\varphi'$$.

**(c)** $$\partial_{B}p_{1} = \partial_{B}\frac{e^{-N\varphi_1}}{e^{-N\varphi_1}+e^{-N\varphi_2}}= -Np_{1}p_{2}(\varphi_{1}'-\varphi_{2}')$$ and $$\partial_{B}p_{2} = -\partial_{B}p_{1}$$. Then $$\partial_{B}^{2}\varphi = (\partial_{B}p_{1})\varphi_{1}' + (\partial_{B}p_{2})\varphi_{2}' + p_{1}\varphi_{1}''+p_{2}\varphi_{2}'' = -Np_{1}p_{2}(\Delta\varphi')^{2} + p_{1}\varphi_{1}''+p_{2}\varphi_{2}''$$. *Sketch:* a smooth background from the $$\varphi_{i}''$$ terms plus a peak at $$B_{c}$$ of height $$\approx N(\Delta\varphi')^{2}/4$$ and width $$\sim1/(N\Delta\varphi')$$, the nascent delta function of the $$N=\infty$$ kink. For the variance identity: with $${{\mathcal O}}=\partial_{B}E$$ independent of $$B$$, differentiating $$\partial_{B}\varphi = {\mathbb{E}}({{\mathcal O}})$$ once more gives $$\partial_{B}^{2}\varphi = -N[{\mathbb{E}}({{\mathcal O}}^{2})-{\mathbb{E}}({{\mathcal O}})^{2}]$$, so $$-\partial_{B}^{2}\varphi = N\,\mathrm{Var}({{\mathcal O}})\geq0$$, which is why the curve is a peak and not a dip. The two-branch formula exhibits the leading piece of this variance: $${{\mathcal O}}\approx\varphi_{1}'$$ in one basin and $$\approx\varphi_{2}'$$ in the other, and the variance of that two-point mixture is exactly $$p_{1}p_{2}(\Delta\varphi')^{2}$$.

**(d)** See Figure 14. The peak in the right panel grows in proportion to $$N$$; a crossover's bump would saturate.

![Anatomy of a first-order transition at finite , in the minimal two-branch model , , with the control parameter written as . Left: the branch free energies cross at ; the limiting free-energy density is their minimum, which has a kink. Middle: at finite , is the probability-weighted average of the branch slopes (2.36), a sigmoid of width . Right: the susceptibility (2.37) peaks at with height and width .](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-first-order-smoothing-6b807602.png)

Anatomy of a first-order transition at finite $$N$$, in the minimal two-branch model $$\varphi_{1}(B) = 0.3\,(B-B_{c})$$, $$\varphi_{2}\equiv0$$, with the control parameter written as $$\alpha$$. Left: the branch free energies cross at $$B_{c}$$; the limiting free-energy density is their minimum, which has a kink. Middle: at finite $$N$$, $$\partial_{B}\varphi$$ is the probability-weighted average of the branch slopes (2.36), a sigmoid of width $$\propto1/N$$. Right: the susceptibility (2.37) peaks at $$B_{c}$$ with height $$\propto N$$ and width $$\propto1/N$$.

:::
