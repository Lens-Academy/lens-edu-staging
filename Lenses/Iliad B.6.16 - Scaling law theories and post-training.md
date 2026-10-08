---
id: '0bdcb59e-978f-4a4d-8fd4-24d703c24c3a'
title: "B.6.16 Scaling law theories and post-training"
tldr: "The quantization model of scaling, emergence from staggered cliffs, exponents from data geometry and kernel spectra, solvable and dynamical theories, and post-training scaling."
summary_for_tutor: "Sections 7.5-7.10 of Iliad worksheet B.6 Physics of Deep Learning. Covers assumptions QH1-QH3 of Michaud et al., the three scaling laws derived from them, emergence as a sum of cliffs with the multitask sparse parity lab, the data-manifold argument alpha_P about 4/d, spectral exponents from kernel eigenvalues, the Maloney-Roberts-Sully field theory, the Bordelon-Atanasov-Pehlevan dynamical theory, and scaling beyond pretraining. Contains Exercises 7.1 (three scaling laws from three assumptions), 7.2 and 7.3, each with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 7.5 The quantization model: exponents from the statistics of skills

The quantization model of Michaud, Liu, Girit, and Tegmark (Michaud et al. 2023) is a minimal model of scaling. It has no architecture, no optimizer, and essentially no mathematics beyond a tail sum, and it produces all three laws of (7.1), plus a sharp point of view on "emergent capabilities." The name is deliberately provocative: the proposal is that what a network learns comes in *discrete units*, dubbed *quanta*.

[^4]

The assumptions, in the form we'll use:

- **QH1 (discreteness).** The computations and knowledge relevant to the prediction task decompose into enumerable *quanta*: basic skills or facts (*e.g.* "carry the one," "Paris follows `the capital of France is'," ...). Each quantum is either fully learned or not learned at all, with no partial credit.
- **QH2 (ordered acquisition).** Networks learn quanta roughly in order of decreasing usefulness, so a given model has learned the first $$m$$ quanta of a fixed sequence.
- **QH3 (Zipfian use).** Quantum $$k$$ is *used* on a fraction

$$
p_{k} = \frac{k^{-(\alpha+1)}}{\zeta(\alpha+1)}
$$

of samples ($$\alpha>0$$ a constant), and on those samples, knowing it reduces the loss by a constant $$\Delta$$ (independent of $$k$$).

Consequently, a model that has learned the first $$m$$ quanta has expected loss

$$
L_{m} = L_{\infty} + \Delta \sum_{k>m}p_{k}\,.
$$

That is the entire model. Everything else is asking how $$m$$ is limited by each resource.

:::callout {title="Exercise" tone="amber"}
**Exercise 7.1 (★) (Three scaling laws from three assumptions).** **(a)** Estimate the tail sum in (7.8) to show $$L_{m} - L_{\infty} \propto m^{-\alpha}$$.

**(b)** *Parameter-limited (data and training unlimited).* Suppose each quantum costs a constant capacity of $$c$$ parameters to learn. Derive $$\alpha_{P}$$ in terms of $$\alpha$$.

**(c)** *Data-limited (capacity and training unlimited).* Suppose a quantum is learnable only if it is used by at least $$\tau$$ training samples, for constant $$\tau$$. Given $$n$$ i.i.d. samples, which quanta are learnable? Derive $$\alpha_{n}$$.

**(d)** *Training-limited, single epoch.* Suppose instead that learning quantum $$k$$ requires $$\tau$$ gradient updates on batches containing it. After $$S$$ steps of online training (fresh batches), derive $$\alpha_{S}$$.

**(e)** *Falsifiability.* Parts (b)–(c) predict a parameter-free relation between $$\alpha_{P}$$ and $$\alpha_{n}$$: write it down, and note which of the two exponents must be larger. Compare with the measured values quoted after (7.1). Something is wrong — what? List the assumptions you used and discuss which are most suspect. (This is a discussion question with no settled answer; see the solution for candidates.)
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$\sum_{k>m}k^{-(\alpha+1)}\approx \int_{m}^{\infty} k^{-(\alpha+1)}dk = m^{-\alpha}/\alpha$$, so $$L_{m} - L_{\infty} \propto m^{-\alpha}$$. (The same replace-sum-by-integral move as the entropy estimates of Section 2.4.)

**(b)** $$m = P/c$$ quanta fit, so $$L(P)-L_{\infty} \propto (P/c)^{-\alpha}$$:   $$\boxed{\alpha_P = \alpha}$$.

**(c)** Quantum $$k$$ is seen $$\approx n\, p_{k}$$ times, so it is learnable iff $$n\, p_{k} \gtrsim \tau$$, i.e. $$k \lesssim m(n) \propto (n/\tau)^{1/(\alpha+1)}$$ by (7.7). Then $$L(n) - L_{\infty} \propto m(n)^{-\alpha}$$:   $$\boxed{\alpha_n = \frac{\alpha}{\alpha+1}}$$.

**(d)** Identical threshold logic with $$S$$ in place of $$n$$: $$\boxed{\alpha_S = \frac{\alpha}{\alpha+1}}$$. Note the model predicts $$\alpha_{n}=\alpha_{S}$$ — data and single-epoch training time are interchangeable bottlenecks, a foreshadowing of the joint treatment in Section 7.9.

**(e)** Eliminating $$\alpha$$: $$\frac{1}{\alpha_{n}}= \frac{1}{\alpha_{P}}+ 1$$, hence $$\alpha_{n} < \alpha_{P}$$ always. But the measured LLM values have $$\alpha_{n} \approx 0.095 > \alpha_{P} \approx 0.076$$: the predicted *ordering* is violated, not just the numbers. Candidate culprits, roughly in order of suspicion: (i) the measured $$\alpha_{n}$$ comes from multi-epoch training with early stopping, not the clean "capacity-unlimited, data-limited" protocol assumed in (c); (ii) the threshold $$\tau$$ and per-quantum cost $$c$$ need not be $$k$$-independent (rare quanta may be intrinsically harder or easier); (iii) $$\Delta$$ constant across quanta is crude; (iv) real capabilities may not decompose into independent quanta at all — they share structure, so learning one changes the cost of others (see the lab of Section 7.6, where exactly this happens). The instructive point is not which repair is right but that the model is sharp enough to be *wrong* — compare the falsifiability discussion of Section 1.

:::

\### 7.6 Emergence: smooth laws from staggered cliffs

The quantization model's deepest payoff is conceptual. Under QH1, the learning of any *single* quantum is a step function: a capability is absent, then abruptly present. Yet the aggregate loss (7.8) is a smooth power law. There is no contradiction. *A smooth law is a sum of many staggered cliffs*, each weighted by $$p_{k}$$ and individually invisible in the aggregate, since quantum $$k$$ contributes only the small fraction $$p_{k}$$ of the loss. Michaud et al. sharpen this with a genetics metaphor. A test sample is *monogenic* if its loss is governed by a single quantum, so that its loss curve during training is a plateau followed by a cliff; it is *polygenic* if many quanta contribute, in which case its loss falls smoothly. Both kinds of per-token curves are observed in real LLMs. From this perspective, "emergent capabilities" (Wei et al. 2022) are neither magic nor mirage (Schaeffer et al. 2023): any benchmark dominated by a few quanta *must* show abrupt arrival, while any sufficiently aggregated metric *must* look smooth. Emergence is a property of what you measure, not (necessarily) of a phase transition inside the model.

![Multitask sparse parity (Michaud et al. 2023): smooth scaling from staggered cliffs. Setup: subtasks with Zipfian frequencies , ; inputs are a one-hot task indicator ( bits) concatenated with random bits; the label is the parity of a fixed random -subset of the bits, the subset depending on the task. Model: one-hidden-layer ReLU MLP, width , MSE loss on labels, trained online (fresh batches of ; Adam, learning rate , steps; fixed seed). Left: test loss per subtask vs. training step. Each subtask is learned in an abrupt cliff, frequent tasks first. Right: the frequency-weighted aggregate is smooth; the dashed guide is the idealized quanta-model slope from Exercise 7.1(d). The measured decay is visibly steeper, as discussed in the text.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-sparse-parity-135b1d82.png)

Multitask sparse parity (Michaud et al. 2023): smooth scaling from staggered cliffs. Setup: $$T=48$$ subtasks with Zipfian frequencies $$p_{i}\propto i^{-(\alpha+1)}$$, $$\alpha=0.4$$; inputs are a one-hot task indicator ($$T$$ bits) concatenated with $$24$$ random $$\pm1$$ bits; the label is the parity of a fixed random $$3$$-subset of the bits, the subset depending on the task. Model: one-hidden-layer ReLU MLP, width $$512$$, MSE loss on $$\pm1$$ labels, trained online (fresh batches of $$256$$; Adam, learning rate $$2\times10^{-3}$$, $$1.2\times10^{5}$$ steps; fixed seed). *Left:* test loss per subtask vs. training step. Each subtask is learned in an abrupt cliff, frequent tasks first. *Right:* the frequency-weighted aggregate $$L(S)=\sum_{i}p_{i}L_{i}(S)$$ is smooth; the dashed guide is the *idealized* quanta-model slope $$-\alpha/(\alpha+1)$$ from Exercise 7.1(d). The measured decay is visibly steeper, as discussed in the text.

**Lab: multitask sparse parity.** The entire mechanism fits in a laptop-scale experiment, shown in Figure 8; students are encouraged to reproduce and modify it (all details are in the caption). A network is trained online on $$T$$ separate parity subtasks with Zipfian frequencies. The input is a one-hot task indicator concatenated with random bits, and the label is the parity of a small task-specific subset of the bits. Parity is a needle-in-a-haystack skill with no partial credit, *i.e.* an honest hand-built quantum. The result: each subtask's test loss is a staggered cliff (frequent tasks fall first), while the frequency-weighted aggregate loss decays smoothly. Note also the honest failure visible in the right panel. The measured aggregate decays *more steeply* than the idealized quanta slope $$-\alpha/(\alpha+1)$$ of Exercise 7.1(d), because the cliffs bunch up rather than spreading Zipf-like; the rare tasks are learned sooner than the threshold rule $$S\,p_{k}\gtrsim\tau$$ predicts. The subtasks share a hidden layer and an adaptive optimizer, so they are not learned independently, and assumption (iv) in the solution to Exercise 7.1(e) fails.

\### 7.7 Exponents from geometry and from spectra

The quantization model takes the Zipf exponent $$\alpha$$ as *input*. The next two arguments produce exponents as *output*, from properties of the data.

\#### 7.7.1 Geometry: the data-manifold argument

Sharma and Kaplan (Sharma & Kaplan 2020) propose the simplest continuous mechanism. A network with ReLU activations computes a piecewise-linear function, so regression on a data manifold of intrinsic dimension $$d$$ is a problem of *piecewise-linear interpolation*. A network with $$P$$ parameters can afford $$\sim P$$ linear pieces; tiling a $$d$$-dimensional manifold with $$P$$ pieces gives spacing $$s \sim P^{-1/d}$$; a linear patch approximates a smooth target to accuracy $$\sim s^{2}$$ (Taylor); and MSE is the *square* of the error. Hence

$$
L(P) \sim (s^{2})^{2} \sim P^{-4/d}\,,\qquad \alpha_{P} \approx \frac{4}{d}\,.
$$

Exponents are small because data manifolds are high-dimensional. The formula is testable, since $$d$$ can be measured with intrinsic-dimension estimators, which is exactly what (Sharma & Kaplan 2020) do.

:::callout {title="Exercise" tone="amber"}
**Exercise 7.2 (Exponents from the data manifold).** **(a)** Fill in the derivation of (7.9), stating precisely where smoothness of the target is used.

**(b)** How does the answer change for mean-absolute-error loss?

**(c)** Taking the measured $$\alpha_{P}\approx0.076$$ for language models at face value, estimate the effective dimension of the "manifold of text." Discuss whether the input dimension, the embedding dimension, or something else is being measured.

**(d)** What does this mechanism predict for the *data* exponent $$\alpha_{n}$$, if $$n$$ samples are what limits the resolution of the tiling?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** As in the text; smoothness (bounded second derivatives) enters in the per-patch error $$\sim s^{2}$$.

**(b)** Mean-absolute error is the error itself, not its square: $$L\sim s^{2} \sim P^{-2/d}$$.

**(c)** $$d \approx 4/0.076 \approx 50$$: an effective, intrinsic dimension of the distribution of text as seen by the model — vastly smaller than the nominal input dimension (vocabulary $$\times$$ context), which is the whole point.

**(d)** If data limits the tiling, $$n$$ samples resolve spacing $$s\sim n^{-1/d}$$ and $$\alpha_{n} \approx 4/d \approx \alpha_{P}$$: this mechanism predicts *equal* exponents — closer to what is observed than the quanta prediction, and the same conclusion the field theory of Section 7.8 reaches from spectra.

:::

\#### 7.7.2 Spectra: scaling laws from kernel eigenvalues

The second mechanism uses machinery we already own: the Bayesian kernel regression of Section 4.6, whose mode-filtering formula said that with $$n$$ samples (and inverse temperature $$\beta$$), the modes of the GP kernel that get learned are those with $$\lambda_{k} \gtrsim (n\beta)^{-1}$$. Suppose the kernel spectrum and the target's decomposition are power laws,

$$
\lambda_{k} \sim k^{-a}\quad (a>1)\,,\qquad y_{k}^{2} \sim k^{-b}\quad (b>1)\,,
$$

in a shared eigenbasis $$\{\varphi_{k}\}$$. The unlearned modes dominate the test error:

$$
L(n) \;\sim\; \sum_{k \,:\, \lambda_k \lesssim (n\beta)^{-1}}y_{k}^{2} \;\sim\; \sum_{k > k_*}k^{-b}\;\sim\; k_{*}^{\,1-b}\,,\qquad k_{*} \sim (n\beta)^{1/a}\,,
$$

giving $$L(n) \sim n^{-(b-1)/a}$$: *the scaling exponent is a ratio of spectral decay rates*. Everything about the data and the architecture enters through two measurable power laws. This is the starting point of the "eigenlearning" analyses (Bordelon et al. 2020; Canatar et al. 2021; Simon et al. 2023), which sharpen (7.11) into precise learning curves (including the overfitting factor whose divergence produces the double-descent peak of Section 6). Bahri et al. (Bahri et al. 2024) organize the possibilities into a clean $$2\times2$$ taxonomy: *resolution-limited* regimes (exponents from spectra or geometry, as here and in (7.9)) versus *variance-limited* regimes (universal exponent $$1$$), in each of $$P$$ and $$n$$.

:::callout {title="Exercise" tone="amber"}
**Exercise 7.3 (Spectral scaling laws, and quanta as eigenmodes).** **(a)** Derive (7.11) from the mode-filtering formula of Section 4.6, and check that the crossover modes $$k\sim k_{*}$$ do not change the exponent.

**(b)** Show that the quantization model's data-scaling law is the special case $$b=a$$ of (7.11) under the dictionary: quanta $$=$$ eigenmodes, Zipf law $$=$$ spectrum, $$a = \alpha+1$$. (Hint: in the quanta model, $$p_{k}$$ plays *both* roles, setting the learning threshold *and* the contribution $$\Delta\,p_{k}$$ to the loss, so the two power laws coincide.)

**(c)** In the quanta model, what would it mean for $$b \neq a$$? Invent a modification of QH3 that realizes it.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The learned modes contribute $$\big((n\beta)^{-1}/(\lambda_{k} + (n\beta)^{-1})\big)^{2} y_{k}^{2} \approx 0$$ for $$k\ll k_{*}$$; the unlearned ones contribute $$y_{k}^{2}$$; the crossover window contributes $$O(k_{*}^{1-b})$$ as well, so the exponent is unchanged. Hence $$L \sim n^{-(b-1)/a}$$.

**(b)** With $$b=a=\alpha+1$$: $$L\sim n^{-\alpha/(\alpha+1)}$$, i.e. the exponent $$\alpha_{n}$$ of Exercise 7.1(c). The threshold $$\lambda_{k} \gtrsim (n\beta)^{-1}$$ is the threshold $$n\, p_{k} \gtrsim \tau$$; the tail sum of $$y_{k}^{2}$$ is the tail sum of $$\Delta p_{k}$$. Kernel regression *is* a quantization model whose quanta are eigenmodes.

**(c)** $$b\neq a$$ decouples how often a skill is *tested* (its loss weight) from how easy it is to *learn* (its threshold) — e.g. let quantum $$k$$ require $$\tau_{k} \propto k^{\theta}$$ occurrences. Any monotone relation between frequency and difficulty generates a two-exponent family, and (7.11) is its universal form.

:::

\### 7.8 A solvable large-N field theory

Maloney, Roberts, and Sully (Maloney et al. 2022) supply what the arguments above lack: a *microscopic, exactly solvable* model in which the joint law $$L(P,n)$$ is computed, not modeled. The ingredients are: a generative data model in which observed inputs are (nonlinear functions of) random projections of a latent space, engineered so that the data covariance has a power-law spectrum $$\lambda_{k} \sim k^{-(1+\zeta)}$$, as measured in real image and text data (the spectral exponent is the paper's $$\gamma$$; we reserve $$\gamma$$ for the scaling dial of Section 5.4); a random-feature *linear* student, so we are in the lazy limit of Section 4, whose $$P$$ random features are its trainable parameters, trained on $$n$$ samples; and the joint thermodynamic limit $$P,n\to\infty$$ at fixed ratio. The computation proceeds at large $$P$$ and $$n$$, where expectations over data and features become Gaussian integrals, the test loss becomes a product of resolvents (Green's functions), and the $$1/P$$ expansion organizes into planar ('t Hooft) diagrams that can be resummed exactly.

[^5]

*Frozen, but random.* A natural first reaction is that this model should be trivial. The student is a linear model on fixed random features. Its kernel never moves, so we are squarely in the lazy regime of Section 4, and in the strict infinite-width lazy limit the loss would not depend on $$P$$ at all. The $$P$$-scaling law is a *finite-size effect on the lazy limit*. At finite $$P$$ the feature Gram matrix is a *random* matrix, correlated with the random sample, and its rank caps how many modes of the data spectrum the student can resolve. All of the physics lives in the disorder average over this randomness, which is what the resolvents and the planar diagrams compute. Frozen does not mean deterministic.

Three notable results:

- *Where exponents come from:* the loss inherits the *data's* spectral exponent, $$L \sim \min(P,n)^{-\zeta}$$ up to logarithms. Remarkably, generic nonlinear feature maps *extend* the data's power-law spectrum rather than reshaping it. This explains why exponents are roughly architecture-independent and can only be improved by changing the data (or the task).
- *Duality and Chinchilla:* the loss is (to leading order) *symmetric* under $$P\leftrightarrow n$$. This predicts $$\alpha_{P} \approx \alpha_{n}$$, consistent with observation, and opposite in spirit to the quanta model's asymmetric prediction (Exercise 7.1(e)). It makes *equiparameterization* $$P\propto n$$ compute-optimal, a first-principles Chinchilla rule.
- *Where laws break:* scaling stops when $$\min(P,n)$$ exceeds the latent dimensionality of the data model, and the loss plateaus. Power laws are a statement about the resolvable structure in the data, and they end when the structure is exhausted.

\### 7.9 All the knobs at once: a dynamical theory

Everything so far is statics, or one knob at a time. The current frontier is the *dynamical* mean-field theory of Section 6 applied to scaling. Bordelon, Atanasov, and Pehlevan (Bordelon et al. 2024) solve a random-feature model trained by gradient flow, with power-law data spectra, in the joint limit of large width, large data, and long time. They obtain a single self-consistent prediction for $$L(t, P, n)$$, with the correlation and response functions of Section 6 as the order parameters. Each resource, when it is the binding constraint, contributes its own power law, recovering the resolution-limited exponents of Section 7.7 in the appropriate corners. Moreover, the theory predicts the full *compute-optimal frontier*: minimizing $$L$$ at fixed compute $$C \propto P t$$ yields Chinchilla-like allocation rules and the frontier exponent, rather than assuming them.

A fair question: the features here are again frozen and random, exactly the setting of Section 7.8, so is dynamical mean-field theory overkill? No, for two reasons. First, time is a genuine third resource. Predicting $$L(t,P,n)$$ and the compute frontier requires the whole training trajectory, and the statics only sees the $$t\to\infty$$ corner. Second, the naive mode-by-mode solution of the lazy regime, in which each kernel eigenmode of the residual decays as $$e^{-\eta\lambda_k t}$$ as in (4.34), applies to a *deterministic* kernel. Here the kernel's eigenvalues and eigenvectors are random and correlated with the sampled data, so the disorder average couples the modes. The DMFT correlation and response functions are the dynamical generalization of the static resolvents of Section 7.8, and at $$t\to\infty$$ the equations collapse back onto the static answer, as they must. What the theory is *not* yet doing is feature learning. The adaptive-kernel version of the formalism exists (Bordelon & Pehlevan 2022), but it has not been pushed through power-law data to closed-form scaling laws; these are the "joint laws with genuine feature learning" missing from Section 7.3. Since feature learning is known to improve exponents for structured targets in solvable cases, the correction need not be small.

\### 7.10 Beyond pretraining: post-training and test-time scaling

Frontier models are no longer just pretrained. They are fine-tuned on curated demonstrations (SFT), optimized against reward models or verifiable rewards (RLHF, RLVR), and allowed to spend variable compute at inference time. Do scaling laws extend to these stages? Increasingly, yes. But the functional forms change, and the changes are instructive.

*Transfer and fine-tuning* still look Kaplan-like. The value of pretraining for a downstream task can be quantified as the *effective data transferred*, meaning the amount of fine-tuning data that the pretrained initialization is worth, and it scales as a power law in both the fine-tuning dataset size and the model size (Hernandez et al. 2021).

*Reward-model optimization* introduces a new scaling axis: not data or parameters, but the distance moved from the base policy, $$d = \sqrt{\mathrm{KL}(\pi \,\|\, \pi_{0})}$$. Gao, Schulman, and Hilton (Gao et al. 2023) found that the true ("gold") reward follows simple laws in $$d$$, namely $$d\,(a - b\log d)$$ for best-of-$$n$$ sampling and $$d\,(a - b\,d)$$ for RL, with coefficients that scale smoothly with the size of the reward model. Note the shape: not a power law but a rise and a *fall*. Optimizing a learned proxy eventually degrades the true objective. This is a Goodhart peak, quantified.

*RL on verifiable rewards*, the training recipe of the reasoning models, scales by *saturating sigmoids* rather than power laws. In the largest systematic study to date, performance as a function of RL compute is predictable, but by a fit with an asymptote, an efficiency, and a midpoint, and most recipe choices move the efficiency without changing the asymptote (Khatri et al. 2025). A physics gloss suggests why the form differs, though it is a hypothesis rather than a result. Pretraining mines an effectively unbounded Zipf tail of new structure, hence power laws. RL post-training mostly elicits and reweights capabilities the base model already contains, on a bounded task distribution. In quanta language, pretraining acquires quanta, while RL sharpens the policy over quanta it already has, and one runs out. *Test-time compute* is the other new axis: the coverage achieved by repeated sampling grows roughly as a power law in the number of samples (Brown et al. 2024), and train-time and test-time compute can be traded against each other along a compute-optimal frontier (Snell et al. 2024).

What does not yet exist is a joint law over all four budgets (pretraining, SFT, RL, inference), and any *theory* at all, even at the level of the quantization model, that derives the sigmoid or the Goodhart peak from a model of the data and skill distribution. The empirical forms are waiting for a statistical-mechanics treatment.

That every ingredient of the pretraining synthesis — Gibbs measures, kernels, mean-field limits, MSRJD actions — appeared earlier in these notes as a physics import is, we hope, a fair summary of the state of the field. A theory of the scaling laws is not finished, but it is recognizably being built, and it is being built out of statistical physics. The post-training laws are younger still: their regularities are only now being settled, and there is no theory of them yet. For a student entering the field, that is a map of where the open territory begins.

[^4]: Michaud's blog post [ericjmichaud.com/quanta](https://ericjmichaud.com/quanta/) is an excellent companion to the paper and can substitute for it in this exercise. But attempt Exercise 7.1 *before* reading either; the derivations are short, and they are more instructive to find than to follow.
[^5]: This is also a working example for Section 6's toolkit: the same model can be solved dynamically, and its double-descent peak, at the interpolation threshold $$P\sim n$$, is regularized by ridge or early stopping, connecting back to the divergence of the overfitting factor mentioned in Section 7.7.

::card[[../Lenses/ericjmichaud-on-neural-scaling-and-the-quanta-hypothesis|The Quantization Model of Neural Scaling (Michaud blog post)]]
