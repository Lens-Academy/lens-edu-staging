---
id: '93903a76-28f1-4737-83ab-868346a4c838'
title: "B.6.15 Empirical neural scaling laws"
tldr: "The empirical neural scaling laws in parameters, data and compute, joint laws and the Chinchilla revision, and a survey of theoretical proposals for where exponents come from."
summary_for_tutor: "Sections 7, 7.1-7.4 of Iliad worksheet B.6 Physics of Deep Learning. Covers the three power laws of Kaplan et al., why C is about 6Pn, the compute-optimal frontier, exponents across modalities (Henighan et al.), joint fits (Kaplan vs Chinchilla), Zipf's law, and a table of proposals (quantization, data manifold, percolation, eigenlearning, solvable field theory, DMFT). Notation: P and n here, N and D in the literature; alpha without subscript is the Zipf exponent. No exercises in this lens."
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
\## 7. Scaling laws

In this final section we return to the theme of Section 1 and discuss the *neural scaling laws*. Over many orders of magnitude, the test loss of large models falls as a clean power law in each resource spent on it: parameters, data, and compute. These laws were found by fitting curves to measurements, and they have proved to be a remarkably simple, robust, and consequential empirical observation, one that any successful model of deep learning should be able to capture. Many models do capture their form, and several go further and make quantitative predictions for the exponents, based on features of the data distribution.

The organizing question of the section is: *where do the exponents come from?* We first assemble the empirical picture (Sections 7.1–7.2): the three laws, what each one holds fixed, and the joint laws that govern compute-optimal training, where the Kaplan–Chinchilla discrepancy lived and was resolved. We then turn to theory. Section 7.3 states the mechanism common to every proposal — power laws in the data produce power laws in the loss — and Section 7.4 surveys the main proposals in one table. The rest of the section works out four rows of that table, in order of increasing machinery: the frequency statistics of skills (Section 7.5, run as a derive-it-yourself exercise, with its payoff for "emergent capabilities" in Section 7.6); the geometry of data and the spectra of kernels (Section 7.7); and solvable large-$$N$$ field theories, static and then dynamical (Sections 7.8–7.9). We close with the newest measurements, for which there is no theory yet: post-training and test-time scaling (Section 7.10).

**Notation.** We keep the conventions of these notes: $$P$$ is the parameter count and $$n$$ the dataset size. Be warned that the scaling-law literature writes $$N$$ for our $$P$$ and $$D$$ for our $$n$$ (their $$N$$ is *not* our width!), so the famous exponents $$\alpha_{N},\alpha_{D}$$ are our $$\alpha_{P},\alpha_{n}$$. For reading the sources:

| these notes | scaling-law literature (Kaplan et al. 2020; Hoffmann et al. 2022; Michaud et al. 2023; Maloney et al. 2022) |
| --- | --- |
| $$P$$ (parameters) | $$N$$ |
| $$n$$ (dataset size) | $$D$$ |
| $$\alpha_{P}$$, $$\alpha_{n}$$ (exponents) | $$\alpha_{N}$$, $$\alpha_{D}$$ |
| $$m$$ (quanta learned, Section 7.5) | $$n$$ |

Note also that in this section $$\alpha$$ (no subscript) denotes the Zipf exponent of the quantization model, not the load of Section 2.

\### 7.1 The empirical laws

Kaplan et al. (Kaplan et al. 2020) established, for autoregressive language models, that when a model is not bottlenecked by the other resources its test loss obeys

$$
L(P) \propto P^{-\alpha_P}\,,\qquad L(n) \propto n^{-\alpha_n}\,,\qquad L(C) \propto C^{-\alpha_C}\,,
$$

where $$P$$ is the number of (non-embedding) parameters, $$n$$ the dataset size in tokens, and $$C$$ the training compute in FLOPs. The measured exponents were $$\alpha_{P} \approx 0.076$$, $$\alpha_{n}\approx 0.095$$, and $$\alpha_{C}\approx 0.050$$, with the trends holding over up to seven orders of magnitude. Three points of bookkeeping are usually left implicit. They are worth making explicit before asking where the laws come from.

*Why FLOPs, and why $$C \approx 6Pn$$.* Compute is measured in floating-point operations because FLOPs are the only measure of training effort that does not depend on how the job is run. Wall-clock time depends on the hardware and the parallelism. The number of training *steps* depends on the batch size: the same $$n$$ tokens can be one giant batch or a million small ones, and below the "critical batch size" (which (Kaplan et al. 2020) measure separately) the loss depends only on the number of tokens processed. FLOPs count the arithmetic itself, which is also what energy and money are proportional to. The standard estimate is

$$
C \;\approx\; 6\,P\,n\,.
$$

Per token, the forward pass costs about $$2P$$ FLOPs: essentially every parameter sits in some matrix multiplication and is used once, for one multiply and one add. The backward pass costs about twice the forward pass, since each layer needs the gradient with respect to its activations and the gradient with respect to its weights, two matrix multiplications of the same size as the forward one. That gives $$6P$$ FLOPs per token, times $$n$$ tokens. The $$\approx$$ absorbs attention (whose per-token cost grows with context length rather than parameter count), embeddings, and optimizer overhead.

*The single-epoch assumption.* The estimate (7.2) assumes that every token processed is a fresh token, so that "tokens processed" and "dataset size" are the same number. This was true of the runs on which the laws were measured, which used well under one epoch of the corpus. Conceptually the two are different resources. The *statistical* resource is the number of distinct tokens $$n$$; the *computational* resource is the number of tokens processed, $$T = E\,n$$ over $$E$$ epochs, so that in general $$C\approx 6PT$$. Fixing $$n$$ and growing $$C$$ by repetition buys optimization, not statistics: the loss converges to the $$n$$-limited floor and then overfits. In the language of Section 2.1, more epochs means larger $$\beta$$ at a fixed quenched sample, while fresh data changes the quenched free energy itself. Empirically the one-epoch idealization is forgiving: for up to about four epochs, repeated tokens are nearly as valuable as fresh ones, after which their value decays quickly (Muennighoff et al. 2023). This matters increasingly, now that frontier training is data-constrained.

*The compute law is not independent.* Since $$C\approx 6Pn$$ depends only on the other two resources, how can compute ever be the unbottlenecked one? The answer is that $$L(C)$$ is measured by a different protocol. It is the lower envelope

$$
L(C) \;=\; \min_{P,\,n\;:\;6Pn\,=\,C}\; L(P, n)\,,
$$

traced out by training many model sizes and keeping the best loss at each value of compute. On this curve compute is the binding constraint by construction, and "not bottlenecked" means "optimally allocated." This makes $$\alpha_{C}$$ a derived exponent. Minimizing an additive joint law $$L = A\,P^{-\alpha_P}+ B\,n^{-\alpha_n}$$ at fixed $$Pn$$ balances the two terms, and gives

$$
\frac{1}{\alpha_{C}}\;=\; \frac{1}{\alpha_{P}}+ \frac{1}{\alpha_{n}}\,, \qquad P \propto C^{\,\alpha_n/(\alpha_P + \alpha_n)}\,,\quad n \propto C^{\,\alpha_P/(\alpha_P + \alpha_n)}\,.
$$

The harmonic sum makes $$\alpha_{C}$$ smaller than either single-resource exponent, since a factor of $$C$$ must be split between growing $$P$$ and growing $$n$$. Kaplan's values give $$\alpha_{C}\approx 0.042$$, against the measured $$0.050$$: roughly consistent, with the gap traceable to the form of the fit and to early-stopping details.

*Universal form; data-dependent exponents.* The same power-law form holds far beyond language. Henighan et al. (Henighan et al. 2020) trained autoregressive transformers on many kinds of data and found power laws everywhere, but with exponents that depend on the data:

| modality | $$\alpha_{P}$$ | $$\alpha_{C}$$ |
| --- | --- | --- |
| language | $$0.070$$ | $$0.048$$ |
| images $$32{\times}32$$ | $$0.13$$ | $$0.10$$ |
| images $$8{\times}8$$ | $$0.24$$ | $$0.19$$ |
| video | $$0.24$$ | $$0.14$$ |
| math (procedural) | $$0.16$$ | $$0.17$$ |

("Math" here means procedurally generated problems, in the style of the DeepMind mathematics dataset. They are emitted by a known program, so the supply is effectively unlimited. Remember this case: it is the one modality whose data distribution is known in closed form.) The exponents vary by a factor of $$3$$–$$5$$ across modalities. Architecture, by contrast, barely matters: within reasonable architectures, changing the shape (depth vs. width at fixed size) or even the family moves the constants and the plateaus, not the slopes (Kaplan et al. 2020). This asymmetry is the central clue of the section: *whatever sets the exponent lives in the data*. Section 7.7 makes it quantitative.

\### 7.2 Joint laws, bottlenecks, and the Chinchilla revision

Each single-resource law assumes the other resources are unlimited. Joint fits describe the crossover to being bottlenecked, with the loss governed by whichever resource is scarcest. Two parametric forms dominate the literature. Kaplan et al. used

$$
L(P,n) = \Big[\Big(\frac{P_{c}}{P}\Big)^{\alpha_P/\alpha_n}+ \frac{n_{c}}{n}\Big]^{\alpha_n}\,,
$$

while the Chinchilla analysis of Hoffmann et al. (Hoffmann et al. 2022) refit with the additive ansatz

$$
L(P,n) \;\approx\; E + A\, P^{-0.34}+ B\, n^{-0.28}\,.
$$

The additive form is easy to read. $$E\approx 1.69$$ is the irreducible entropy of text, the noise floor that no amount of scale removes; the two deficits decay independently; and the bottleneck is simply the larger deficit. Both forms reduce to the single-resource laws (7.1) in the appropriate corners.

The difference between the fits mattered a great deal in practice, because of what they say about the compute-optimal allocation in (7.3). Kaplan et al.'s analysis gave $$P\propto C^{0.73}$$ and $$n\propto C^{0.27}$$: with more compute, grow the model. For two years the field trained ever-larger models on comparatively little data. Chinchilla's fit gives $$P\propto C^{0.5}$$ and $$n\propto C^{0.5}$$: grow both equally, or as a rule of thumb about $$20$$ tokens per parameter. The prediction was tested directly. At the compute budget of DeepMind's 280B-parameter Gopher, the new rule said to train a model four times smaller on four times more data, and the resulting 70B-parameter Chinchilla beat Gopher across the board. (Both models, and the law, are named in DeepMind's animal series.) Chinchilla's allocation is now the accepted baseline. The discrepancy was later dissected by Porian et al. (Porian et al. 2024): Kaplan's fit was skewed by three small-scale artifacts — how last-layer and embedding compute were counted, over-long warmup, and optimizer settings that were not retuned with scale — and with these corrected, the two experiments agree. One coda: frontier models now deliberately *over*-train relative to Chinchilla, on many more than $$20$$ tokens per parameter, because a smaller model at equal loss is cheaper at inference time, a cost the training-compute-optimal analysis does not see.

With the empirical picture assembled, here is what a theory of (7.1) owes us: (i) why power laws at all, over so many decades; (ii) the values of the exponents (why so small? why do they depend on the modality but not on the architecture?); (iii) relations between exponents (is $$\alpha_{n}$$ determined by $$\alpha_{P}$$?); and (iv) when the laws break. The models surveyed below each answer a subset.

\### 7.3 Where do the laws come from?

The basic answer, common to every proposal surveyed below, is that the loss curve reads off the coarse distribution of structure in the data. Power laws go in with the data and come out in the loss.

The prototype of "power laws in" is *Zipf's law*: rank the words of a large corpus by frequency, and the frequency of the word of rank $$k$$ falls off as $$f_{k}\propto 1/k$$, over about four decades of rank (Figure 7). It is a scale-free tail of ever rarer structure, and it is not special to words. Sequences of $$n$$ consecutive words ($$n$$-grams, the unit of pre-neural language modeling) are Zipf-like at every $$n$$, with slopes that flatten as $$n$$ grows. Facts, meaning discrete pieces of world knowledge attested in text, inherit the heavy-tailed popularity of the entities they mention, and a model's ability to answer a factual question tracks the number of training documents that support it (Kandpal et al. 2023). The covariance and kernel spectra of text and image data are measured power laws (Sections 7.7–7.8). A learner working through such data never runs out of structure to absorb. It moves ever further down the tail, at ever slower returns. That is, qualitatively, why the loss is a power law rather than an exponential (there is structure at all scales) and why it does not simply plateau (the tail does not end).

![Zipf's law, illustrated on a synthetic corpus: tokens drawn from a distribution over a vocabulary of words, with the empirical rank–frequency curve against the guide. The curve is a consistency check rather than data, since the words were sampled from a Zipf distribution to begin with. Real corpora look the same over roughly four decades, with deviations at both ends: the Zipf–Mandelbrot correction at low rank, and a steeper tail beyond about words.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-zipf-9dea6d0f.png)

Zipf's law, illustrated on a synthetic corpus: $$2\times10^{6}$$ tokens drawn from a $$1/k$$ distribution over a vocabulary of $$5\times10^{4}$$ words, with the empirical rank–frequency curve against the $$f\propto 1/\mathrm{rank}$$ guide. The curve is a consistency check rather than data, since the words were sampled from a Zipf distribution to begin with. Real corpora look the same over roughly four decades, with deviations at both ends: the Zipf–Mandelbrot correction at low rank, and a steeper tail beyond about $$10^{4}$$ words.

The exponents of these tails differ, and the differences matter, because in every model below the loss exponent is inherited from the data exponent. Pure Zipf is in fact a marginal case. Write the tail of skill frequencies as $$p_{k}\propto k^{-(\alpha+1)}$$. The quantization model of Section 7.5 gives a loss exponent equal to $$\alpha$$, and exact Zipf ($$f_{k}\propto 1/k$$, that is, $$\alpha = 0$$) is the boundary at which the tail sum decays only logarithmically and power-law scaling degenerates. Read this way, the measured $$\alpha_{P}\approx 0.076$$ for language says that its effective skill distribution is $$p_{k}\sim k^{-1.08}$$, barely steeper than pure Zipf. Language scaling is slow because its structure sits just above the marginal $$1/k$$ tail. Image data has steeper tails and scales faster; compare the modality table of Section 7.1.

Where does the theory stand? The single-resource laws have been derived from this mechanism by many models of quite different flavor, and a few models derive multi-resource laws; the survey below keeps score. Three things are missing. First, no theory computes the data's exponents from first principles. Every model converts measured data statistics into loss curves, and the statistics themselves are an empirical input. This is true even for procedurally generated math, where the generating program is known exactly but the computation has not been carried out. Second, there are no joint laws with genuine feature learning. The best dynamical derivations live in lazy, random-feature settings (Section 7.9), while in solvable cases feature learning is known to improve exponents for structured targets, so the corrections need not be small. Third, the bridge from the smooth loss to capabilities is missing. Benchmark performance can jump within a decade of scale while the loss glides smoothly (Wei et al. 2022); this has been contested as an artifact of the metric (Schaeffer et al. 2023), and the quantization model of Section 7.6 gives it a sharper reading. A fourth gap is newer: the post-training and test-time scaling laws of Section 7.10 have no theory at all.

\### 7.4 A survey of theoretical proposals

The table below organizes the most prominent derivations of neural scaling laws by four questions: what models the *data* (equivalently, what a "feature" is and how features are distributed); what models the *network*, if anything; whether actual *exponents* are predicted, and in terms of what; and whether *multi-resource* laws are obtained.

| **proposal** | **data model / "features"** | **NN framework** | **exponents?** | **multi-resource?** |
| --- | --- | --- | --- | --- |
| quantization; Michaud et al. (Michaud et al. 2023) | discrete skill "quanta," Zipf-used, learned in order | none (a counting argument) | in terms of the Zipf exponent $$\alpha$$; plus the relation $$\tfrac{1}{\alpha_n}= \tfrac{1}{\alpha_P}+ 1$$ | separate $$P$$, $$n$$, $$S$$ laws |
| data manifold; Sharma–Kaplan (Sharma & Kaplan 2020) | smooth target on a $$d$$-dimensional manifold | piecewise-linear interpolation (function class only; no training) | yes: $$\alpha_{P}\approx 4/d$$ | no ($$P$$ only) |
| percolation; Brill (Brill 2024) | latent subtask clusters at criticality, with power-law cluster sizes | none: a generic nonparametric learner $$+$$ regression estimates | from percolation critical exponents | two regimes; not joint |
| kernel eigenlearning; Bahri et al. (Bahri et al. 2024), Bordelon–Canatar–Pehlevan (Bordelon et al. 2020; Canatar et al. 2021; Simon et al. 2023) | power-law kernel spectra $$+$$ target coefficients | **frozen kernel**: infinite-width NTK, or GP/Bayesian | in terms of the spectral exponents | partially: resolution- vs. variance-limited regimes |
| solvable field theory; Maloney–Roberts–Sully (Maloney et al. 2022) | latent power-law covariance, extended by random features | linear model on **fixed random features** (frozen kernel); large-$$N$$ RMT, statics | in terms of the data's spectral exponent | yes: joint $$L(P,n)$$, with duality $$P \leftrightarrow n$$ |
| DMFT; Bordelon–Atanasov–Pehlevan (Bordelon et al. 2024) | power-law (source/capacity) spectra | DMFT of gradient-flow training on **fixed random features** (frozen kernel; dynamics) | yes, including the time exponent | fully joint $$L(t,P,n)$$ $$+$$ compute frontier |

Five remarks for reading the table. First, everyone agrees on the origin. In every row the loss exponent is inherited from a power-law tail in the data, whether of skill frequencies, cluster sizes, manifold volume, or covariance spectra. The rows differ in what the tail is a tail *of*, and in how much network machinery is retained. Second, and this deserves emphasis: *every row that models the network at all does so with a frozen kernel*. The eigenlearning row works with the infinite-width NTK or GP kernel of Sections 4.3 and 4.6; the two field-theory rows train only the readout of a fixed set of random features, which is a frozen kernel by construction (Exercise B.6(b)). The manifold row models only the network's function class, as a count of linear pieces, and never trains it; the quantization and percolation rows contain no network. So none of the current derivations involves feature learning, the very mechanism that Sections 5–6 argued is what makes finite networks differ from kernels. Third, equilibrium routes (Bayesian GP learning curves and their finite-width refinements) and dynamical routes (gradient flow, DMFT) give matching exponents wherever they overlap. This is the "two limits of one system" correspondence of Sections 2.1 and 6 at work again. Fourth, only the two field-theory rows currently predict joint laws, and only the dynamical one prices training time, deriving a Chinchilla-like compute-optimal frontier rather than assuming it. Fifth, no row computes the data's own exponent. The closest attempt is the percolation proposal, which derives power-law cluster-size statistics from a critical model of the data distribution; its two criticality regimes (power-law-distributed discrete subtasks, and a dominant data manifold) map onto the quantization and manifold rows respectively. We will not develop the percolation model further. The remaining subsections work through the other rows, in order of machinery.

*Do the predicted exponents agree with experiment?* Where the comparison has been made, the answer is encouraging but not yet sharp. The quantization model's authors extracted "quanta" from a small language model by clustering gradients, measured how often each is used in the training distribution, and found a power law whose exponent roughly matches the model's scaling exponent, as the model requires (Michaud et al. 2023); on the other hand, the model's parameter-free relation between $$\alpha_{P}$$ and $$\alpha_{n}$$ is violated by the measured ordering of Kaplan's exponents (Exercise 7.1(e)). The manifold prediction $$\alpha_{P}\approx 4/d$$ was confirmed in teacher–student experiments, where $$d$$ and $$\alpha_{P}$$ can be measured independently, and tested more loosely on image classifiers and GPT-type language models (Sharma & Kaplan 2020); for language, taking $$\alpha_{P}\approx0.076$$ at face value gives $$d\approx 50$$ (Exercise 7.2). The kernel predictions have been tested on standard architectures and datasets, with exponents computed from measured kernel spectra, and the predicted duality between the $$P$$- and $$n$$-exponents holds up (Bahri et al. 2024). The two field-theory rows take the data's spectral exponent as input. Their qualitative predictions — exponents independent of architecture, $$\alpha_{P}\approx\alpha_{n}$$, and equiparameterization as the compute-optimal rule — match the Chinchilla-era measurements, but a quantitative test needs the covariance spectrum of the training data, which is rarely reported for the large runs.

The honest summary is that these theories convert an exponent measured in the *data* into an exponent measured in the *loss*, and the conversion has held up wherever both have been measured.
