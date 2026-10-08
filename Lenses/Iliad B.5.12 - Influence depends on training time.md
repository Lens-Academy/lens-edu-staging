---
id: 'cb0b7e8f-f8df-4631-847e-fdcdaa28c0be'
title: "B.5.12 Influence depends on training time"
tldr: "Exercise 4.3 on a two-layer deep linear network: how a training example's influence changes over training time, when it peaks, and when its sign flips. Ends with an unfinished practical considerations section."
summary_for_tutor: "Sections 4.4 and 5 of Iliad worksheet B.5 Data Attribution: the stagewise dynamics of a two-layer linear network, analytic influence of perturbing example z_p, Exercise 4.3 (a)-(c) with collapsed solution (three sources of influence, when influence peaks near each mode's transition time, sign flips with d = 2 and s_1 much larger than s_2), remarks on the general singular basis and the developmental view of Lee et al. 2025. Section 5 Practical Considerations and Open Problems reads only 'Under construction'. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 4.4 Exercise: Influence depends on training time

The previous sections analyzed unrolling's asymptotics in the converged limit. But the whole point of unrolling is that the training *path* matters. The following exercise makes this concrete in a setting where the influence function admits a closed form at every point during training: a two-layer deep linear network (DLN), the same class of models from the SLT lecture day. The setup and analytic formula follow Lee et al. 2025.

:::callout {title="Exercise" tone="amber"}
**Exercise 4.3 (Stagewise influence in a deep linear network).** A two-layer linear network $$f_{W}(x) = W_{2} W_{1} x$$ with $$W_{1}, W_{2} \in {\mathbb{R}}^{d\times d}$$ is trained on $$\{(x_{i},y_{i})\}_{i=1}^{n}$$ with squared loss. Assume whitened inputs ($$\tfrac{1}{n}\sum_{i} x_{i} x_{i}^{\top} = I$$) and, for simplicity, that the input–output cross-covariance $$\Sigma_{xy}= \tfrac{1}{n}\sum_{i} x_{i} y_{i}^{\top}$$ is already diagonal with entries $$s_{1} > s_{2} > \cdots > s_{d} > 0$$.[^5]

**Dynamics.**  Under gradient flow with small balanced initialization, the network's modes evolve independently. The effective weight matrix at time $$t$$ is $$W(t) = \mathrm{diag}(\mathcal{G}_{1}(t),\dots,\mathcal{G}_{d}(t))$$, where each mode strength follows

$$
\mathcal{G}_{k}(t) \;=\; \frac{s_{k}\,e^{2s_k t/\tau}}{e^{2s_k t/\tau}- 1 + s_{k}/\mathcal{G}_{k}(0)},
$$

with $$\mathcal{G}_{k}(0) \ll s_{k}$$ and time constant $$\tau$$. Mode $$k$$ transitions from $$\approx 0$$ to $$\approx s_{k}$$ around time $$t_{k}^{*} \approx \tfrac{\tau}{2s_k}\log(s_{k}/\mathcal{G}_{k}(0))$$. Larger singular values saturate first: the network learns dominant structure before fine structure.

**Analytic influence.**  Now perturb the weight of training example $$z_{p} = (x_{p},y_{p})$$ by $$\varepsilon$$, so the perturbed cross-covariance is $$\Sigma_{xy}(\varepsilon) = \Sigma_{xy}+ \varepsilon\,y_{p} x_{p}^{\top}$$. Since $$\Sigma_{xy}$$ is diagonal, the perturbation shifts its eigenvalues and rotates its eigenvectors. The influence of $$z_{p}$$ on the weight matrix at time $$t$$ decomposes as

$$
\mathcal{I}_{p}(t) \;:=\; \frac{\partial W(t,\varepsilon)}{\partial\varepsilon}\bigg\rvert_{\varepsilon=0}\;=\; A\,\mathcal{G}(t) \;+\; \mathcal{G}'_{\varepsilon}(t) \;+\; \mathcal{G}(t)\,B,
$$

with three terms:

- $$A$$ and $$B$$ are skew-symmetric matrices describing how the perturbation *rotates* the left/right singular bases. Their off-diagonal entries are $$A_{jk}= B_{kj}= (y_{p})_{j}(x_{p})_{k}/(s_{k} - s_{j})$$ for $$j \neq k$$.
- $$\mathcal{G}'_{\varepsilon}(t) = \mathrm{diag}\bigl(g'_{t}(s_{1})\,(y_{p})_{1}(x_{p})_{1},\;\dots,\;g'_{t}(s_{d})\,(y_{p})_{d}(x_{p})_{d}\bigr)$$ encodes the change in mode strengths, where

$$
g'_{t}(s_{k}) \;:=\; \frac{\partial\,\mathcal{G}_{k}(t)}{\partial s_{k}}
$$

is the sensitivity of the $$k$$-th mode strength to a change in the corresponding singular value at time $$t$$.

The influence on the loss of a test example $$z_{q} = (x_{q}, y_{q})$$, with residual $$r_{q}(t) = y_{q} - W(t)x_{q}$$, is

$$
\mathcal{I}(z_{p},\,\ell_{q})(t) \;=\; -\,r_{q}(t)^{\top}\bigl(A\,\mathcal{G}(t) + \mathcal{G}'_{\varepsilon}(t) + \mathcal{G}(t)\,B\bigr)\,x_{q}.
$$

**(a)** **(Three sources of influence.)** Interpret the three terms in (38):
- $$A\,\mathcal{G}(t)$$ and $$\mathcal{G}(t)\,B$$: the perturbation *rotates* the singular bases, mixing already-learned modes into each other. Why are these terms proportional to the current mode strengths $$\mathcal{G}(t)$$ rather than to their derivatives?
- $$\mathcal{G}'_{\varepsilon}(t)$$: the perturbation *shifts* the singular values, changing how fast each mode is learned. Why does this term involve $$g'_{t}(s_{k})$$, sensitivity of the dynamics to the singular value, rather than $$\mathcal{G}_{k}(t)$$ itself?

**(b)** **(When does influence peak?)** Using the dynamics (37), argue that $$g'_{t}(s_{k})$$ is peaked around $$t \approx t_{k}^{*}$$ (the transition time of mode $$k$$). Conclude that the $$\mathcal{G}'_{\varepsilon}$$ term, the part of influence that acts through the learning speed of each mode, is concentrated in time around the moment the mode is being learned. Before and after, this contribution is negligible.

*Hint:* Consider the limits $$t \ll t_{k}^{*}$$ (mode not yet learning, $$\mathcal{G}_{k} \approx \mathcal{G}_{k}(0)$$) and $$t \gg t_{k}^{*}$$ (mode saturated, $$\mathcal{G}_{k} \approx s_{k}$$). In both cases, how sensitive is $$\mathcal{G}_{k}$$ to a small change in $$s_{k}$$?

**(c)** **(Sign flips.)** Consider $$d = 2$$ with $$s_{1} \gg s_{2}$$: mode 1 captures a coarse distinction ("animal vs. plant") and mode 2 a fine distinction ("dog vs. cat" within animals). A dog example $$z_{\mathrm{dog}}$$ and a cat example $$z_{\mathrm{cat}}$$ share the same mode-1 coordinate but have opposite mode-2 coordinates: $$(x_{\mathrm{dog}})_{2} = +(x_{\mathrm{cat}})_{2}$$. Using (40), argue that the influence of $$z_{\mathrm{dog}}$$ on a cat test loss can change sign during training: positive while mode 1 is being learned (shared structure), negative after mode 2 is learned (competing structure). At what time is the sign flip sharpest?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* The $$A\mathcal{G}(t)$$ and $$\mathcal{G}(t)B$$ terms describe how the perturbation rotates the singular basis. A rotation mixes already-learned modes into each other, so its effect on the weight matrix is proportional to the current mode strengths: if mode $$k$$ has not yet been learned ($$\mathcal{G}_{k} \approx 0$$), rotating its basis direction contributes nothing to $$W(t)$$. The $$\mathcal{G}'_{\varepsilon}(t)$$ term, by contrast, acts through the learning *dynamics*: perturbing $$s_{k}$$ changes the speed at which mode $$k$$ is learned, and this matters precisely when the dynamics are sensitive to $$s_{k}$$ — not when $$\mathcal{G}_{k}(t)$$ is large or small per se, but when $$\mathcal{G}_{k}(t)$$ is *changing rapidly* as a function of $$s_{k}$$. This is why the derivative $$g'_{t}(s_{k}) = \partial\mathcal{G}_{k}(t)/\partial s_{k}$$ appears rather than $$\mathcal{G}_{k}(t)$$ itself.

*(b)* From (37), $$\mathcal{G}_{k}(t) = s_{k} e^{2s_k t/\tau}/(e^{2s_k t/\tau}- 1 + s_{k}/\mathcal{G}_{k}(0))$$. For $$t \ll t_{k}^{*}$$: $$e^{2s_k t/\tau}\approx 1$$, so $$\mathcal{G}_{k} \approx \mathcal{G}_{k}(0)$$ regardless of $$s_{k}$$ — the mode hasn't started learning yet, and a small change in $$s_{k}$$ makes no difference, so $$g'_{t}(s_{k}) \approx 0$$. For $$t \gg t_{k}^{*}$$: $$e^{2s_k t/\tau}\gg s_{k}/\mathcal{G}_{k}(0)$$, so $$\mathcal{G}_{k} \approx s_{k}$$ and $$g'_{t}(s_{k}) \approx 1$$ — but the *residual* in mode $$k$$ is also $$\approx 0$$, so this term's contribution to the loss influence (40) is negligible. The product $$g'_{t}(s_{k}) \times (\text{residual in mode }k)$$ is peaked around $$t \approx t_{k}^{*}$$, when the mode is in transition: the dynamics are maximally sensitive to $$s_{k}$$ *and* the residual is still nonzero.

*(c)* Write $$x_{\mathrm{dog}}= (\alpha, +\delta)$$ and $$x_{\mathrm{cat}}= (\alpha, -\delta)$$, where $$\alpha$$ is the shared mode-1 component and $$\pm\delta$$ are opposite mode-2 components (since $$\Sigma_{xy}$$ is diagonal, the standard basis is the singular basis). During mode-1 learning ($$t \approx t_{1}^{*}$$, mode 2 not yet active): the residual of the cat test example has a large mode-1 component, and $$z_{\mathrm{dog}}$$'s perturbation increases $$s_{1}$$ (via $$(y_{\mathrm{dog}})_{1} (x_{\mathrm{dog}})_{1} > 0$$), accelerating mode-1 learning. This reduces the cat test loss — positive influence. After mode-2 learning ($$t \approx t_{2}^{*}$$): the cat's residual is now dominated by mode 2, and $$z_{\mathrm{dog}}$$'s mode-2 perturbation has the wrong sign for the cat (because $$(x_{\mathrm{dog}})_{2}$$ and $$(x_{\mathrm{cat}})_{2}$$ have opposite signs). This increases the cat test loss — negative influence. The sign flip is sharpest around $$t_{2}^{*}$$, when $$g'_{t}(s_{2})$$ peaks and the mode-2 residual transitions from large to small.

:::

:::callout {title="Note" tone="blue"}

**Remark (General singular basis).** When $$\Sigma_{xy}= USV^{\top}$$ is not diagonal, the formulas above hold with all vectors expressed in the singular basis: replace $$x_{p}$$ by $$V^{\top} x_{p}$$, $$y_{p}$$ by $$U^{\top} y_{p}$$, $$r_{q}$$ by $$U^{\top} r_{q}$$, and $$W(t)$$ by $$U^{\top} W(t) V$$. The influence on $$W$$ itself becomes $$\mathcal{I}_{p}(t) = U(A\mathcal{G}(t) + \mathcal{G}'_{\varepsilon}(t) + \mathcal{G}(t)B)V^{\top}$$, with $$A_{jk}= (U^{\top} y_{p})_{j}(V^{\top} x_{p})_{k}/(s_{k} - s_{j})$$. See Lee et al. 2025 for the full derivation, including the degenerate case $$s_{j} = s_{k}$$.

:::

:::callout {title="Note" tone="blue"}

**Remark (The developmental view of attribution).** Lee et al. 2025 show that the same phenomenology (influence sign flips, non-monotonic trajectories) appears in language models, where e.g. the influence of delimiter tokens spikes when the model learns pairing structure and then decays. The practical consequence is that data attribution is not a one-shot computation but a time-varying signal, and methods like unrolling that track the training trajectory are better suited to capture this than methods that look only at the final checkpoint.

:::

\## 5. Practical Considerations and Open Problems

Under construction.

[^5]: The general case replaces the standard basis with the left/right singular vectors $$U, V$$ of $$\Sigma_{xy}$$ throughout; see Remark 4.4.
