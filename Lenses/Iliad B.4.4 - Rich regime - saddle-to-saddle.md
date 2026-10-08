---
id: '7b24c07c-a40a-401e-924d-3cf218a5f734'
title: "B.4.4 Rich regime: saddle-to-saddle"
tldr: "Solves the rich regime under small initialization: with aligned singular vectors the dynamics split into logistic equations, so large modes are learned first, one after another."
summary_for_tutor: "This is Section 5 'Rich regime: saddle-to-saddle' of worksheet B.4 (training dynamics). It contains Exercises 5.1-5.4: the aligned NTK under the alignment assumption, decoupled scalar ODEs dw/dt = 2w(s - w), the logistic solution and separation of timescales (larger s_alpha learned faster), and incremental learning with the low-rank implicit bias and the link to the saddles P_S M. Collapsed solutions and a hint on 5.1 are included. Keep the notation w_alpha(t), s_alpha, w_0. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Guillaume Corlouer (Stormglass)
source_url: https://iliad-intensive.org/learning/training-dynamics/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. Rich regime: saddle-to-saddle

This is the core problem. We derive the exact solution of the rich regime dynamics directly from the self-consistent equation of Section 4, emphasizing the NTK perspective.

**Alignment assumption.** Start from the balanced gradient flow equation derived in Exercise 4.6:

$$
\dot{W}= (WW^{\top})^{1/2}(M - W) + (M - W)(W^{\top} W)^{1/2}
$$

We work in the **rich regime** (small initialization) with balanced weights. Assume that the student is **aligned** to the teacher: the singular vectors of $W(t)$ coincide with those of $M$ at all times. Concretely, write:

$$
M = U\,\text{diag}(s_{1}, \ldots, s_{d})\,V^{\top}, \qquad W(t) = U\,\text{diag}(w_{1}(t), \ldots, w_{d}(t))\,V^{\top}
$$

where $U, V$ are the left/right singular vectors of $M$, and $w_{\alpha}(t) \geq 0$ are the evolving singular values of $W$.

:::callout {title="Exercise" tone="amber"}
**Exercise 5.1 (Aligned NTK).** Under this alignment assumption, show that the NTK operator is aligned to the task, i.e. $K[F]$ preserves the SVD basis. In particular, show that:

$$
\begin{aligned}(WW^{\top})^{1/2}&= U\,\text{diag}(w_{1}, \ldots, w_{d})\,U^{\top}, \\ (W^{\top} W)^{1/2}&= V\,\text{diag}(w_{1}, \ldots, w_{d})\,V^{\top}\end{aligned}
$$

and that the residual is $M - W = U\,\text{diag}(s_{1} - w_{1}, \ldots, s_{d} - w_{d})\,V^{\top}$.

*Hint*: Recall that for $A = U\,\text{diag}(\sigma_{i})\,V^{\top}$, we have $AA^{\top} = U\,\text{diag}(\sigma_{i}^{2})\,U^{\top}$, and therefore $(AA^{\top})^{1/2}= U\,\text{diag}(|\sigma_{i}|)\,U^{\top}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Under the alignment assumption, $W = U\,\text{diag}(w_{\alpha})\,V^{\top}$. Then:

$$
WW^{\top} = U\,\text{diag}(w_{\alpha}^{2})\,U^{\top}
$$

Since $w_{\alpha} \geq 0$, the positive matrix square root is:

$$
(WW^{\top})^{1/2}= U\,\text{diag}(w_{\alpha})\,U^{\top}
$$

Similarly:

$$
W^{\top} W = V\,\text{diag}(w_{\alpha}^{2})\,V^{\top} \quad \Longrightarrow \quad (W^{\top} W)^{1/2}= V\,\text{diag}(w_{\alpha})\,V^{\top}
$$

The residual is immediate:

$$
M - W = U\,\text{diag}(s_{\alpha} - w_{\alpha})\,V^{\top}
$$

The NTK operator acts on any matrix $F = U\,\text{diag}(f_{\alpha})\,V^{\top}$ as:

$$
\begin{aligned}K[F]&= U\,\text{diag}(w_{\alpha})\,U^{\top} U\,\text{diag}(f_{\alpha})\,V^{\top} \\&\quad + U\,\text{diag}(f_{\alpha})\,V^{\top} V\,\text{diag}(w_{\alpha})\,V^{\top} \\&= U\,\text{diag}(2w_{\alpha} f_{\alpha})\,V^{\top}.\end{aligned}
$$

So $K[F]$ stays in the SVD basis of $M$ — the NTK is aligned to the task. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.2 (Decoupled scalar ODEs).** Substitute into the self-consistent equation. Show that the matrix equation decouples into $d$ independent scalar ODEs:

$$
\dot{w}_{\alpha} = 2\,w_{\alpha}\,(s_{\alpha} - w_{\alpha}), \qquad \alpha = 1, \ldots, d
$$

*Hint*: Compute the product $(WW^{\top})^{1/2}(M - W)$ in the SVD basis. It is diagonal with entries $w_{\alpha}(s_{\alpha} - w_{\alpha})$. The second term contributes identically, giving the factor of 2.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Substitute into $\dot{W}= (WW^{\top})^{1/2}(M-W) + (M-W)(W^{\top} W)^{1/2}$:

**First term:**

$$
U\,\text{diag}(w_{\alpha})\,\underbrace{U^\top U}_{I}\,\text{diag}(s_{\alpha} - w_{\alpha})\,V^{\top} = U\,\text{diag}\big(w_{\alpha}(s_{\alpha} - w_{\alpha})\big)\,V^{\top}
$$

**Second term:**

$$
U\,\text{diag}(s_{\alpha} - w_{\alpha})\,\underbrace{V^\top V}_{I}\,\text{diag}(w_{\alpha})\,V^{\top} = U\,\text{diag}\big((s_{\alpha} - w_{\alpha})\,w_{\alpha}\big)\,V^{\top}
$$

Summing:

$$
\dot{W}= U\,\text{diag}\big(2\,w_{\alpha}(s_{\alpha} - w_{\alpha})\big)\,V^{\top}
$$

Since $W = U\,\text{diag}(w_{\alpha})\,V^{\top}$ and the singular vectors are constant by assumption, we read off:

$$
\boxed{\dot{w}_\alpha = 2\,w_\alpha\,(s_\alpha - w_\alpha)}
$$

The NTK perspective makes the structure transparent: the factor $2w_{\alpha}$ is the NTK eigenvalue for mode $\alpha$, which amplifies learning in directions that are already strong, while $(s_{\alpha} - w_{\alpha})$ is the residual. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.3 (Timescale of learning).** The ODE $\dot{w}= 2w(s - w)$ is a logistic equation whose solution is:

$$
w(t) = \frac{s}{1 + \left(\frac{s}{w_0}- 1\right)e^{-2st}}
$$

where $w_{0} = w(0)$. Compute the time $t_{\alpha}$ it takes for mode $\alpha$ to travel from initial strength $w_{0}$ to a final strength $w_{f}$. Show that:

$$
t_{\alpha} = \frac{1}{2 s_{\alpha}}\ln\left(\frac{w_{f}\,(s_{\alpha} - w_{0})}{w_{0}\,(s_{\alpha} - w_{f})}\right)
$$

Deduce that modes with larger singular values $s_{\alpha}$ are learned faster. This is a **separation of timescales**: the network learns features in decreasing order of their singular value strength.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

From the logistic solution $w(t) = \frac{s}{1 + (s/w_{0} - 1)e^{-2st}}$, we invert to find $t$ as a function of $w$. The derivation is equivalent to integrating $\dot{w}= 2w(s-w)$ by separation of variables:

$$
\int_{w_0}^{w_f}\frac{dw}{w(s-w)}= 2\,t_{\alpha}
$$

Using partial fractions $\frac{1}{w(s-w)}= \frac{1}{s}\!\left(\frac{1}{w}+ \frac{1}{s-w}\right)$:

$$
\frac{1}{s_{\alpha}}\Big[\ln w - \ln(s_{\alpha} - w)\Big]_{w_0}^{w_f}= 2\,t_{\alpha}
$$

$$
\frac{1}{s_{\alpha}}\ln\frac{w_{f}\,(s_{\alpha} - w_{0})}{w_{0}\,(s_{\alpha} - w_{f})}= 2\,t_{\alpha}
$$

Therefore:

$$
\boxed{t_\alpha = \frac{1}{2s_{\alpha}}\ln\left(\frac{w_{f}\,(s_{\alpha} - w_{0})}{w_{0}\,(s_{\alpha} - w_{f})}\right)}
$$

For a fixed ratio $w_{f}/s_{\alpha}$ and fixed $w_{0}$, the learning time scales as $t_{\alpha} \propto 1/s_{\alpha}$: **modes with larger singular values are learned faster**. The network learns features in decreasing order of their strength — a strong separation of timescales.

**Contrast with the lazy regime** (anticipating Section 6): in the lazy regime the NTK is frozen at $K_{0} = 2w_{0} \gg 1$, so $\dot{w}_{\alpha} \approx 2w_{0}(s_{\alpha} - w_{\alpha})$. All modes converge at the same exponential rate $2w_{0}$, independent of $s_{\alpha}$. The rich regime has state-dependent NTK ($2w_{\alpha}$), creating a positive feedback loop — modes that are already large learn even faster — which amplifies the differences between $s_{\alpha}$ into a hierarchy of timescales $t_{1} \ll t_{2} \ll \cdots \ll t_{r}$. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.4 (Incremental learning).** Consider a teacher with $r$ nonzero singular values and a small uniform initialization $w_{\alpha}(0) = w_{0} \ll s_{r}$ for all $\alpha$. Qualitatively, discuss:

- What is the approximate distribution of singular values of $W(t)$ at early times?
- How do the singular values of $W(t)$ evolve throughout training?
- What happens in the limit $t \to \infty$?

What does this analysis tell us about the sequence of critical points visited by the gradient flow?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

With uniform initialization $w_{\alpha}(0) = w_{0}$ for all $\alpha$, the sigmoid solution shows that mode $\alpha$ remains near $w_{0}$ until time $t \approx \frac{1}{2s_{\alpha}}\ln(s_{\alpha}/w_{0})$, then transitions rapidly to $w_{\alpha} \approx s_{\alpha}$.

**Early times** ($t \sim \frac{1}{2s_{1}}\ln(s_{1}/w_{0})$): Only mode 1 has grown significantly, so the spectrum is **one singular value near $s_{1}$, with all the others still near $w_{0} \ll s_{r}$**. The student is approximately $W(t) \approx w_{1}(t)\,u_{1} v_{1}^{\top}$, effectively **rank 1**.

**Intermediate times**: As $t$ increases, $w_{2}$ switches on, then $w_{3}$, etc. The singular values **switch on one at a time**, in decreasing order of $s_{\alpha}$, each staying near $w_{0}$ and then rising to $s_{\alpha}$ over a narrow window. The student is approximately $W(t) \approx \sum_{\alpha=1}^{k(t)}w_{\alpha}(t)\,u_{\alpha} v_{\alpha}^{\top}$ where $k(t)$ increases stepwise, so the effective **rank increases incrementally**.

**Long times** ($t \to \infty$): All modes converge, $w_{\alpha} \to s_{\alpha}$, and $W \to M$.

This is an **implicit bias toward low-rank (simple) solutions**: at any finite time, the network represents the best rank-$k$ approximation to the teacher. The gradient flow effectively performs a greedy SVD.

**Connection to the saddle structure (Exercise 3.3):** The saddle points $P_{S} M$ with $|S| = k$ are exactly the best rank-$k$ approximations to $M$, with loss $\frac{1}{2}\sum_{\alpha > k}s_{\alpha}^{2}$. The gradient flow trajectory passes **near** these saddles as it incrementally recruits modes. The **plateaus** in the loss curve correspond to time spent near saddle points (only $k$ modes active), and the **sharp transitions** correspond to escaping along the unstable direction that activates the next mode. $\square$

:::
