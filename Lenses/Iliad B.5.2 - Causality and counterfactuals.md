---
id: '863a286a-80fc-4f7a-b69d-369dea149e94'
title: "B.5.2 Causality and counterfactuals"
tldr: "Frames data attribution as a causal question, shows how leave-one-out counterfactuals fail through overdetermination and non-transitivity, introduces Shapley values, and fixes the notation used later."
summary_for_tutor: "Section 1 (1.1 to 1.4) of Iliad worksheet B.5 Data Attribution: attribution as causal analysis, Definition 1.1 (counterfactual attribution), Example 1.2 (bakery overdetermination), Example 1.3 (boulder non-transitivity), Definition 1.4 (Shapley value) with a remark that Shapley dilutes credit and is costly, and the notation: training set, per-example loss, data weights beta, weighted loss L(w; beta), observable phi, and influence as the derivative of phi(pi(beta)) in beta_i at beta = 1. Keep this notation. No exercises."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Causality and Counterfactuals

\### 1.1 Data attribution as causal analysis

At the heart of data attribution, we find a causal question: **Which training examples caused a model to behave the way it does?** If mechanistic interpretability aims for the causal analysis of a forward pass, data attribution aims for the causal analysis of a training run.[^1] Our north star is a decomposition of the training data into "causes" of the model's behaviour.

Two asymmetries between the two settings are worth keeping in mind from the start. First, both problems inherit the same conceptual difficulties of causal reasoning in general (explained in the next section) and there is no reason to expect data attribution to escape them. Second, a forward pass is cheap, while a training run is not. Where mechanistic interpretability can validate a claim by running many ablations, data attribution cannot in general afford even one retraining. That being said, there are also advantages: Generally speaking, the training process is more robust and the ablations we run may be more human understandable than high-dimensional modification of activations or weights.

Now, before developing such data attribution methods, we should be aware of the tension between causality and the ways we will validate a hypothesis. Finding a "true" causal relationship in practice can be much more difficult than it may seem at first glance. In the following section we take the question seriously, and find that the naive counterfactual answer fails in ways that matter.

\### 1.2 Counterfactual attribution and its failures

The classical notion of causation is due to Lewis 1973: $$A$$ caused $$B$$ iff, had $$A$$ not occurred, $$B$$ would not have occurred. Applied to data attribution, this says that a training example "causes" a behaviour when removing it would have altered the behaviour, also known as the *leave-one-out (LOO) counterfactual*. We relax this definition from a binary to a gradual one.

:::callout {title="Definition" tone="blue"}

**Definition 1.1 (Counterfactual attribution).** We attribute an action $$A$$ to a behaviour $$B$$ iff

1. had $$A$$ occurred, $$B$$ would have occurred to a higher degree;
2. had $$A$$ not occurred, $$B$$ would have occurred to a lesser degree (or not at all).

:::

Definition 1.1 is the simplest formalisation of cause. But as Mueller 2024 emphasises, it breaks in at least two cases.

**Overdetermination: redundant causes are missed.**  When two training examples are each *sufficient* to produce a behaviour, removing either one leaves the behaviour intact, and LOO attributes credit to neither.

:::callout {title="Tip" tone="green"}

**Example 1.2 (Overdetermination in the bakery).** OpenCroissant, a bakery, sources four ingredients: flour, butter, yeast, and sugar. Each can come from a standard or premium supplier. The bakery has observed that using all premium ingredients produces exceptionally fluffy croissants and wishes to identify which upgrades are responsible.

Unbeknownst to the bakery, exceptional fluffiness depends on two independent leavening mechanisms.

- *Steam leavening.* Premium butter has higher fat content and better water distribution, producing more steam and hence more lift.
- *Biological leavening.* A premium yeast strain ferments more vigorously, producing more gas and hence more lift.

Either mechanism alone causes exceptional fluffiness: puff pastry rises from steam alone, and bread rises from yeast alone. Downgrading premium butter to standard therefore has negligible effect on fluffiness (the threshold is still met), and likewise for yeast. Counterfactual attribution (Definition 1.1) concludes that neither butter nor yeast was a cause albeit both were.

:::

The same pattern may arise in learning, where once a behaviour is learned, i.e. has hit saturation, additional examples will not affect it and appear as causally irrelevant.

**Non-transitivity: counterfactuals do not chain.**  Direct ablation will not capture *how* an action causes a behaviour.

:::callout {title="Tip" tone="green"}

**Example 1.3 (Non-transitivity of counterfactuals).** The following scenario is due to Ned Hall, as reported in Hitchcock 2001.

**(A)** A hiker is wandering through the mountains when a boulder rolls down the hill.

**(B)** The hiker sees the boulder and dodges.

**(C)** The hiker is unharmed.

Counterfactually, (A) caused (B): had the boulder not rolled, the hiker would not have dodged. And (B) caused (C): had the hiker not dodged, she would have been crushed. But (A) did not cause (C): whether or not the boulder rolled, she ends up unharmed.

:::

In the data-attribution setting this corresponds to chains of mediation. A training example may induce an intermediate feature, and that feature may drive a downstream capability, without the datapoint itself passing the counterfactual test against the capability end-to-end. Methods that look only at marginal effects miss the mediation.

\### 1.3 Beyond leave-one-out: Shapley values

A natural response to overdetermination is to stop looking only at the LOO swap and instead ask how a training example contributes across *all* subsets of the training set it could be part of. This is the idea behind *Shapley values* (Shapley 1953).

:::callout {title="Definition" tone="blue"}

**Definition 1.4 (Shapley value).** Let $$v: 2^{[n]}\to \mathbb{R}$$ be a set function (a "game"). The Shapley value of element $$i$$ is

$$
\varphi_{i}(v) \;:=\; \frac{1}{n}\sum_{S \subseteq [n] \setminus \{i\}}\binom{n-1}{|S|}^{-1}\bigl(v(S \cup \{i\}) - v(S)\bigr).
$$

:::
We can think of $$[n]$$ as a set of players and $$v(S)$$ as the value of the coalition. In our previous example, the players are the premium ingredients and the value is the resulting fluffiness. Then $$v(S)$$ will measure the fluffiness of the croissant when the ingredients in $$S$$ are premium and the rest are standard.

Shapley values partially address overdetermination. Returning to the baker example: in coalitions $$S\subset [n]$$ where neither butter nor yeast is premium, upgrading one has a large marginal effect; in coalitions where the other leavener is already premium, the marginal effect is small. Averaging gives each ingredient roughly half the credit.

:::callout {title="Note" tone="blue"}

**Remark (Shapley still dilutes credit).** Shapley values redistribute credit more fairly but do not fully solve overdetermination. Each of butter and yeast receives roughly half the credit for fluffiness, yet each *alone* is sufficient, so one could argue each deserves the full credit. Furthermore, Shapley values over a training set of size $$n$$ require evaluating $$v(S)$$ on $$2^{n}$$ coalitions, each demanding a retraining. This is hopeless for realistic models.

:::

\### 1.4 Notation and goals

We close the section by fixing notation that will be used throughout.

- A training set is $$\mathcal{D}= \{z_{i}\}_{i=1}^{n}$$ with $$z_{i} = (x_{i}, y_{i})$$.
- A model is a function $$f_{w}: X \to Y$$ parameterised by $$w \in W \subset \mathbb{R}^{d_p}$$.
- The per-example loss is $$L_{j}(w)=L(w, z_{i}) = \ell(f_{w}(x_{i}), y_{i})$$ for some pointwise loss $$\ell$$.
- We introduce a vector of *data weights* $$\beta = (\beta_{1}, \ldots, \beta_{n}) \in \mathbb{R}^{n}$$ and define the *weighted training loss*

$$
L(w; \beta) \;:=\; \frac{1}{n}\sum_{i=1}^{n} \beta_{i}\, L(w, z_{i}),
$$

and we write $$L(w) := L(w, 1)$$ for the unweighted loss.
- The behaviour we want to attribute is a differentiable scalar observable $$\phi: W \to \mathbb{R}$$. This could be the loss on a held-out point, an average loss on a task, the logit of a specific completion, or any other scalar function of the trained parameters.

In general we want to know "If I change $$\beta_{i}$$, how will this affect $$\phi$$?" This question is typically split into two parts:

- *Parameter influence*: "If I change $$\beta_{i}$$, how will this affect the final parameters?"
- *Influence on $$\phi$$*: "If I change the final parameters, how will this affect $$\phi$$?"

In practice we may think of the influence then as a measure of the composition of these maps

$$
\begin{aligned}B&\xrightarrow{\pi}"W"\to \mathbb{R}\\ \beta&\mapsto w(\beta) \mapsto \phi(w(\beta)).\end{aligned}
$$

where we are intentionally vague about the first map and where the different approaches, influence functions, Bayesian influence functions, and unrolling, differ in how they interpret it.

That being said, all attribution methods in these lecture notes can be phrased as estimators of partial derivatives or finite differences of this map. The *influence* of an example $$i$$ is then computed as first-order approximation:

$$
\boxed{\;\frac{\partial\,\phi(\pi(\beta))}{\partial \beta_{i}}\bigg|_{\beta = \mathbf{1}}\;}
$$

[^1]: In Section 4 we make this analogy explicit.
