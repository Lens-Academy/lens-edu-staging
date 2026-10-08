---
id: 'ebe8cc0e-af2c-4ee5-ab54-eb8e99a6f128'
title: "B.6.12 Feature learning, muP and grokking"
tldr: "Why the NTK moves in the mean-field limit (feature learning), the scaling dial between lazy and mean-field, muP, and a reading exercise on grokking as a lazy-to-rich transition."
summary_for_tutor: "Sections 5.3-5.6 of Iliad worksheet B.6 Physics of Deep Learning. Covers the per-neuron kernel and the NTK of order 1/N, the dial gamma between 1/2 (lazy) and 1 (mean-field) with its table, maximal update parameterization and hyperparameter transfer, and the guided reading of Kumar et al. 2024 with a terminology box. Contains Exercise 5.4 (lazy vs rich along the dial) and Exercise 5.5 (grokking as a lazy-to-rich transition, reading questions a-f), both with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 5.3 The NTK is no longer constant: feature learning

Section 4.3 showed that in the fan-in normalization the NTK freezes as $$N\to\infty$$, and Section 4.2 defined feature learning as change of the NTK during training. Let's redo that computation in mean-field scaling. From (5.7), $$\partial f/\partial c_{i} = \frac{1}{N}\phi(a_{i}\cdot x)$$ and $$\partial f/\partial a_{i} = \frac{1}{N}c_{i}\phi'(a_{i}\cdot x)\,x$$, so the NTK of Section 4.1 is

$$
\Theta(x,x') = \frac{1}{N^{2}}\sum_{i=1}^{N} k_{\theta_i}(x,x') = \frac{1}{N}\int k_{\theta}(x,x')\, d\rho_{N}(\theta)\,,
$$

with the per-neuron kernel

$$
k_{\theta}(x,x') := \phi(a\cdot x)\phi(a\cdot x') + c^{2}\,\phi'(a\cdot x)\phi'(a\cdot x')\; x\cdot x'\,.
$$

Thus $$\Theta = O(1/N)$$, recovering the previous observation that gradients are small, which was the reason for the rescaling (5.14). The estimates of Section 4.3 also explain why the kernel is now free to move. The Hessian blocks (4.27) carry $$1/N$$ instead of $$1/\sqrt{N}$$, so $$\|\nabla_{\theta}^{2} f\| = O(1/N)$$; but the learning rate is $$\eta = N\tilde\eta$$, so the bound (4.25) gives for the relative drift $$\|\dot\Theta\|/\|\Theta\| \lesssim \eta\,\|\nabla^{2}_{\theta} f\|\,|\Delta| = O(1)$$. The bound no longer forces the kernel to freeze, and the equations of motion (5.15) will show that it does move. As $$N\to \infty$$, the meaningful object is $$N\Theta = \int k_{\theta}\, d\rho_{N}$$, and the function-space dynamics (4.10) now becomes a kernel gradient flow *with a time-dependent kernel*:

$$
\frac{d}{dt}f^{\mu} = -\tilde\eta \big(N\Theta^{\mu}{}_{\nu}\big)\big|_{\rho_t}\, \Delta^{\nu}\,, \qquad N\Theta\big|_{\rho_t}= \int k_{\theta}\, d\rho_{t}\,.
$$

*At initialization* the LLN makes $$N\Theta \to {\mathbb{E}}_{\rho_0}[k_{\theta}]$$, a deterministic kernel — the *same* limiting kernel (4.24) as in the fan-in normalization. The two limits start from the same place.

*During training*, however, they part ways. In Section 4.3, each parameter moved only $$O(1/\sqrt{N})$$, so $$\rho_{N}$$ stayed within $$O(1/\sqrt{N})$$ of $$\rho_{0}$$ and the kernel was pinned, (4.31). Here, the equations of motion (5.15) move each particle an *order-one* distance. (Each neuron has only $$O(1/N)$$ leverage, so fitting the data *forces* the average neuron to move a distance $$O(1)$$.) Thus $$\rho_{t}$$ transports macroscopically, and by (5.26) the kernel is dragged along at order one as well.

\### 5.4 The scaling dial and Maximal Update Parameterization

It's quite instructive to look at an entire one-parameter family of scalings, which has fan-in/NTK scaling and mean-field scaling as its endpoints. The family can be encoded via a prefactor

$$
f_{\theta}(x) = \frac{1}{N^{\gamma}}\sum_{i=1}^{N} c_{i}\,\phi(a_{i}\cdot x)\,,\qquad \gamma\in[\tfrac{1}{2},1]\,,
$$

where $$c_{i}, a_{ij}\sim {{\mathcal N}}(0,1)$$. For each $$\gamma$$, as $$N\to\infty$$, the learning rate must be simultaneously be scaled as $$\eta = N^{2\gamma-1}\tilde\eta$$ so that the function-space dynamics stays $$O(1)$$ (one can derive that from $$\Theta\sim N^{1-2\gamma}$$). Repeating the estimates above gives (see Exercise 5.4):

|  | $$f_{\theta_0}$$ at init | per-neuron motion | limit |
| --- | --- | --- | --- |
| $$\gamma=\tfrac{1}{2}$$ | $$O(1)$$ (GP, CLT) | $$O(N^{-1/2})$$ | lazy: Sections 3 and 4 |
| $$\tfrac{1}{2}<\gamma<1$$ | $$O(N^{\frac{1}{2}-\gamma})\to 0$$ | $$O(N^{\gamma-1})\to 0$$ | lazy (frozen kernel, zero init) |
| $$\gamma=1$$ | $$O(N^{-1/2})\to 0$$ | $$O(1)$$ | mean-field: this section |

Notably, every intermediate $$\gamma$$ collapses onto the kernel limit: the initialization GP is scaled away, but the neurons still move vanishingly little, so training is again linear in an (appropriately rescaled) frozen kernel (Chizat et al. 2019; Mei et al. 2018). Mean-field, $$\gamma=1$$, is the *unique* scaling in this family with both a well-defined limit and order-one feature movement; it's the "maximal update" that one can take without blowing up. This uniqueness can be generalized from one hidden layer to arbitrary depth (where consistency forces *layer-dependent* learning-rate and initialization scalings), and is known as the Maximal Update Parametrization, $$\mu$$P, in Yang and Hu's line of work on tensor programs (Yang & Hu 2021). In particular, mean-field scaling is $$\mu$$P for $$L=1$$.

:::callout {title="Exercise" tone="amber"}
**Exercise 5.4 (Lazy vs. rich along the dial).** For the family (5.27):

**(a)** show $$\Theta = O(N^{1-2\gamma})$$ and hence that $$\eta = N^{2\gamma-1}\tilde\eta$$ is the right co-scaling;

**(b)** show the initialization output is $$O(N^{1/2-\gamma})$$ and per-neuron velocities are $$O(N^{\gamma-1})$$;

**(c)** conclude that the (normalized) kernel drift over any fixed training horizon is $$O(N^{\gamma-1})$$, vanishing for every $$\gamma<1$$;

**(d)** reconcile $$\gamma=\frac{1}{2}$$ with the bounds of Section 4.3. Optional: relate $$\gamma$$ to the output-scale parameter $$\alpha$$ of (Chizat et al. 2019), where multiplying any model by $$\alpha\to\infty$$ produces lazy training.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$\partial f/\partial c_{i} = N^{-\gamma}\phi(a_{i}\cdot x)$$ and similarly for $$a_{i}$$, so $$\Theta = \sum_{i} N^{-2\gamma}\,k_{\theta_i}= N^{1-2\gamma}\cdot\frac{1}{N}\sum_{i} k_{\theta_i}= O(N^{1-2\gamma})$$; demanding $$\eta\,\Theta = O(1)$$ forces $$\eta = N^{2\gamma-1}\tilde\eta$$.

**(b)** At initialization $$f = N^{-\gamma}\sum_{i} c_{i}\phi(a_{i}\cdot x)$$ is $$N^{-\gamma}$$ times a sum of $$N$$ i.i.d. mean-zero terms $$= O(\sqrt{N})$$, so $$f_{\theta_0}= O(N^{1/2-\gamma})$$. Per-neuron velocities: $$\dot c_{i} = -\eta\,\partial{{\mathcal L}}/\partial c_{i} = O(N^{2\gamma-1}\cdot N^{-\gamma}) = O(N^{\gamma-1})$$, and likewise for $$\dot a_{i}$$.

**(c)** The normalized kernel $$N^{2\gamma-1}\Theta = \frac{1}{N}\sum_{i} k_{\theta_i}$$ is an empirical average over particles, so over any fixed horizon its drift is of the order of the per-particle displacement, $$O(N^{\gamma-1})$$ — vanishing for every $$\gamma<1$$, order one exactly at $$\gamma=1$$.

**(d)** At $$\gamma=\frac{1}{2}$$: per-neuron motion $$O(N^{-1/2})$$, matching (4.30) (an $$O(1)$$ total displacement shared among $$N$$ neurons); initialization output $$O(1)$$, the GP of Section 3. For the optional part: relative to the mean-field parametrization (5.7), $$f_{\gamma} = \alpha\, f_{\rm MF}$$ with $$\alpha = N^{1-\gamma}$$, so in the language of (Chizat et al. 2019) every $$\gamma<1$$ sends the laziness $$\alpha\to\infty$$ with width — lazy — while $$\gamma=1$$ keeps $$\alpha$$ of order one.

:::

\### 5.5 What is this framework good for?

Nobody solves the McKean–Vlasov PDE (5.20) for a real network! There are practical payoffs, though, of three different kinds: *scaling prescriptions*, *mechanism identification*, and *reduced descriptions* that downstream theories build on.

Hyperparameter transfer ($$\mu$$P) is one key application. The mean-field analysis is, fundamentally, a theory of which joint scalings of initialization and learning rate keep the training dynamics nondegenerate and learning features as $$N\to\infty$$. Its deep-network generalization (Yang & Hu 2021) turns this into an engineering recipe, $$\mu$$Transfer (Yang et al. 2022): parametrize the network so that its infinite-width limit is the feature-learning one, and then optimal hyperparameters become approximately width-independent, so one can tune a small proxy model and *transfer* the settings to the large one. In the original demonstration this retuned GPT-3 6.7B at a few percent of pretraining cost and outperformed the published model; variants of this parametrization are now standard in large-scale training.

The dial of Section 5.4 also lets one interpolate between regimes on real architectures, and measure where feature learning actually pays off. Kernel-regime behavior tends to be competitive on small datasets, while on CIFAR-scale image tasks trained networks beat their own frozen NTKs by large margins (Geiger et al. 2020). Diagnostics from this circle of ideas (kernel distance/alignment during training, e.g. the silent-alignment effect (Atanasov et al. 2022)) are now routine tools for asking "is my network actually learning features, or just doing kernel regression?"

The mean-field limit here holds data fixed while sending $$N\to\infty$$, which unfortunately does not yet make it a quantitative theory of generalization at realistic data/width ratios. The dynamical mean-field theory of Section 6 (Bordelon & Pehlevan 2022) will rectify this somewhat; it is a field-theoretic refinement of the current analysis, whose extensions do reproduce compute-optimal neural scaling laws, in particular at large dataset size (Bordelon et al. 2024).

\### 5.6 Grokking as a lazy-to-rich transition: a reading exercise

We finish this section with two guided readings that apply various concepts introduced above to one of the most interesting and fundamental phenomenons in learning: grokking (Power et al. 2022). Grokking refers to the following behavior. One trains a small network on an algorithmic dataset — the canonical example is addition mod $$P$$, presented as pairs $$(n,m)$$ with label $$(n+m)\bmod P$$, with only a fraction of all $$P^{2}$$ facts shown. The network reaches perfect *training* accuracy quickly, while *test* accuracy sits at chance: it has simply memorized. Then, orders of magnitude later in training and long after the train loss has flattened, test accuracy jumps abruptly to near $$100\%$$. Such delayed, abrupt generalization, with emergent capabilities, demands a mechanism.

Theory has produced (at least) two quantitative explanations, and this subsection and the next walk through one each: the *dynamical* lens of Kumar–Bordelon–Gershman–Pehlevan (Kumar et al. 2024) (this subsection) — grokking as a delayed transition from lazy to rich dynamics — and the *equilibrium* lens of Rubin–Seroussi–Ringel (Rubin et al. 2024) (Section 5.7) — grokking as a first-order phase transition with metastable lag. The two walkthroughs are parallel in structure and use largely disjoint toolkits from these notes. The dynamical one presumes comfort with Sections 4 and 5.4; the Bayesian one is a denser read, and combines scaling analysis with a mean-field approximation.

The work of Kumar, Bordelon, Gershman, and Pehlevan (Kumar et al. 2024) invokes no statistical-mechanics ensemble at all. There is only gradient descent, and the lazy/rich dial of Section 5.4, *unfolding in time*. The paper claims that a network groks when 1) it first fits the training data through its cheap, fast channel (kernel regression with the frozen NTK of its initialization), and that lazy fit memorizes without generalizing because the initial kernel is misaligned with the task; then 2) on a slower timescale controlled by the network's laziness, the features finally move (the kernel rotates, as in Section 5.3), a generalizing solution is found, and test loss falls long after train loss did. Two beautiful features of this work are that its clearest examples grok under vanilla gradient descent with zero weight decay, and that the parameter norm increases during grokking. Both are direct counterexamples to earlier accounts of grokking built on weight decay and shrinking norms.

The paper is written almost entirely in the language these notes have already built (Sections 4 and 5), so the dialect box below is short. Read the introduction, the two-layer polynomial-regression model, and the experiments (modular arithmetic, MNIST, a one-layer transformer); skip the dynamical mean-field asymptotics on a first pass — that machinery belongs to Section 6. Then work through Exercise 5.5.

:::callout {title="Note" tone="blue"}

A few translations of terminology from (Kumar et al. 2024):

- *Lazy / linearized dynamics*: the regime of Section 4.3 — the network moves only in the affine subspace (4.1) spanned by its initial gradients, so training is kernel regression with the frozen initial NTK (Sections 4.1 and 4.6).
- *Laziness parameter $$\alpha$$*: an overall multiplier on the network output, $$f \mapsto \alpha f$$ (with loss and learning rate co-scaled). This is the continuous version of the $$\gamma$$-dial of Section 5.4, in the form introduced by (Chizat et al. 2019): $$\alpha\to\infty$$ is fully lazy, small $$\alpha$$ is rich.
- *Kernel–task (mis)alignment*: the language of Section 4.2 — how much of the target lies in the top eigenmodes of the initial NTK. Misaligned $$=$$ the target's weight sits in small-eigenvalue modes, which the mode-filtering formula of Section 4.6 says are not learnable from the available data.
- *Sufficient statistics*: a handful of scalar functions of the weights whose closed dynamics determine the test loss — the dynamical analogue of the order parameters of Section 2.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.5 (Grokking as a lazy-to-rich transition).** Read (Kumar et al. 2024) as assigned above, and answer the following, citing where in the paper each answer lives. (Parts (a)–(e) have exact counterparts in Exercise 5.6, the other walkthrough; part (f) is the shared comparison question.)

**(a)** *What regime is the analysis set in, and what dial controls it?* There is no thermodynamic limit and no equilibrium ensemble here, so what plays the role that a "scaling limit" plays elsewhere in this section? How is the laziness parameter $$\alpha$$ implemented, and how does it relate to the $$\gamma$$-dial of Section 5.4? Section 5.2's scaling prescription had two halves, an output scale and a learning-rate scale. Which half is doing the work here? (The other walkthrough meets the opposite half: see Exercise 5.6(a).)

**(b)** *What plays the role of the order parameter?* What quantity distinguishes the memorized state from the generalizing one, and how would you measure it in a real training run? Compare with the Fourier overlap $$\Phi(w)$$ that plays this role in the other walkthrough (Exercise 5.6(b)): what information do the two quantities share?

**(c)** *Necessary conditions.* The paper states three conditions for grokking to occur. Find them, and translate each into the language of these notes (Sections 4.6, 4.3 and 5.4).

**(d)** *What parameter is tuned?* What makes grokking more dramatic, and what makes it vanish entirely? What does the theory predict in the two extremes $$\alpha\to\infty$$ and $$\alpha$$ small? Contrast with the control parameters of Exercise 5.6(d).

**(e)** *Where does the delay come from?* Both theories must explain the gap between the train-loss drop and the test-loss jump. Here there is no metastability and no noise — so what produces two well-separated timescales in a single deterministic flow? What does each theory *require* to produce a delay (noise? weight decay? neither?), and how do the paper's zero-weight-decay, growing-norm experiments bear on earlier explanations of grokking?

**(f)** *Synthesis.* Are the equilibrium mechanism of Section 5.7 and the dynamical mechanism of this section incompatible, or two corners of one phenomenon? Design at least one experiment whose outcome would favor one over the other — consider, e.g., how the grokking delay should depend on training noise at fixed hyperparameters, or how the delay should fluctuate from seed to seed, under each mechanism.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Finite network, deterministic gradient descent/flow, no limit required: the analysis is organized around the *linearization* of Section 4.3 and departures from it. The dial is an output multiplier $$\alpha$$ (with appropriate co-scaling of the loss/learning rate), exactly the scale parameter of lazy training (Chizat et al. 2019): at large $$\alpha$$ an $$O(1)$$ change of $$f$$ requires only an $$O(1/\alpha)$$ change of weights, so features barely move — a continuous, finite-$$N$$ version of the $$\gamma$$-dial, where $$N^{\gamma - 1}$$ played the role of $$1/\alpha$$ (Exercise 5.4). And this paper is precisely about the half of the scaling story that the Bayesian treatment of Exercise 5.6(a) could not see: there, only the induced function prior survived and the learning-rate/dynamics half dropped out; here there is no prior at all, and *everything* is the dynamics half — the two walkthroughs literally partition Section 5.2's prescription between them.

**(b)** The alignment between the (current) NTK and the task — equivalently the kernel's distance from its initialization, or the paper's low-dimensional sufficient statistics: in the memorized state the kernel is still (close to) its initialization and the fit lives in misaligned modes; in the generalizing state the kernel's top eigenspaces have rotated onto the target. Measurable in any run by tracking the empirical NTK (Section 4.2). The Fourier overlap $$\Phi(w)$$ of Exercise 5.6(b) carries the same information — features aligned with the task's structure — read off the weights and their posterior rather than off the kernel; for modular addition, a rotated kernel and condensed Fourier modes are two descriptions of the same event.

**(c)** (i) *The top eigenvectors of the initial NTK are misaligned with the labels*: in the language of Section 4.6, the target's weight sits in modes with small eigenvalues, so the lazy (kernel-regression) solution fits the training points without generalizing — memorization, in the precise mode-filtering sense. (ii) *The dataset is in a Goldilocks window*: large enough that a generalizing solution exists (cf. the critical sample size of Exercise 5.6(d)), small enough that train and test loss do not simply track each other. (iii) *Training starts lazy* (large $$\alpha$$, or large initialization scale): feature learning is initially suppressed, as in Section 4.3, so the kernel fit happens *first*.

**(d)** The laziness $$\alpha$$ (and the initialization scale, which acts similarly): increasing it stretches the delay between the lazy fit and feature learning, making grokking more dramatic; decreasing it makes the network rich from the start, so train and test fall together and grokking *vanishes*. In the extreme $$\alpha\to\infty$$ the network is a pure kernel machine forever: by condition (i) it never generalizes, and the grokking time diverges. Contrast Exercise 5.6(d): there the knobs were sample size and temperature moving the system across a phase boundary; here the knob does not change *where* the system ends up so much as *how long* the misaligned detour lasts.

**(e)** From a separation of timescales built into the flow: fitting the train set within the frozen-kernel subspace is fast (the exponential convergence of Section 4, eq. (4.34)), while rotating the kernel is slow — suppressed by the laziness, since feature motion is $$O(1/\alpha)$$-small per unit of function change. Train loss bottoms out on the fast clock; test loss must wait for the slow one. Nothing stochastic is needed: no noise, no weight decay, no barrier crossing — and that is the force of the paper's counterexamples, since grokking with zero weight decay and *growing* weight norm rules out explanations in which regularization-driven norm shrinkage causes the transition. The equilibrium mechanism of Section 5.7, by contrast, needs temperature: its delay is the escape from a metastable free-energy basin, which pure gradient flow would never make.

**(f)** They live in different corners and need not compete: Rubin et al. describe noisy (Langevin/Bayesian) training near equilibrium, Kumar et al. deterministic training far from it; both say *the cheap channel is used first — kernel fit or metastable memorizing phase — and features arrive late*. Distinguishing experiments:
1. *noise dependence* — an activated (metastable-escape) delay should shorten rapidly with increasing training noise, roughly Arrhenius-like, while a timescale-separation delay survives at zero noise and depends on it only weakly; measure grokking time vs. Langevin temperature at fixed $$\alpha$$, $$n$$.
2. *Seed-to-seed statistics* — nucleation out of a metastable state is a rare-event process with broad (roughly exponential) waiting-time distributions across seeds; a deterministic mechanism predicts narrow, initialization-scale-set delays.
3. *The $$\alpha$$-dial itself* — the lazy-to-rich account makes a sharp prediction that the delay is monotonically stretched by $$\alpha$$ with grokking eliminated at small $$\alpha$$; the equilibrium account ties the delay to the free-energy landscape at fixed ensemble, not to $$\alpha$$. Running these on modular addition is a very feasible project.

:::
