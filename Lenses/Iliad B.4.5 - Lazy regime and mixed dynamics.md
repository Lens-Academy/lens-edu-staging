---
id: '7c70510b-52be-4f83-a39f-4deae8af4ea4'
title: "B.4.5 Lazy regime and mixed dynamics"
tldr: "Shows that large initialization freezes the NTK and gives exponential learning with no timescale separation, then an interpolating ODE that unifies the lazy and rich regimes."
summary_for_tutor: "This covers Sections 6 'Lazy regime' and 7 'Mixed dynamics' of worksheet B.4 (training dynamics). It contains Exercises 6.1-6.3 (linearized NTK for w_0 much larger than s, frozen-NTK exponential solution with rate 2 w_0, no timescale separation) and Exercises 7.1-7.3 (interpolating ODE dw/dt = 2 sqrt(w^2 + tau^2)(s - w) after Tu, Aranguri and Jacot 2024, two-phase dynamics, mode-by-mode transition), plus a remark on grokking. Collapsed solutions are included. Keep the notation w_0, tau, sigma, n. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Guillaume Corlouer (Stormglass)
source_url: https://iliad-intensive.org/learning/training-dynamics/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 6. Lazy regime

We now show that large initialization freezes the NTK and eliminates the timescale separation found in Section 5. For clarity, we work with the **diagonal scalar** model from Exercise 3.1, so each mode $\alpha$ is independent. This avoids matrix algebra and isolates the essential mechanism.

**Setup.** Consider a single mode: a depth-2 diagonal DLN with scalar weights $a, b$ learning a target $s > 0$. From Sections 4 and 5, the balanced gradient flow for $w = ab$ is:

$$
\dot{w}= 2w(s - w)
$$

The factor $2w$ is the (scalar) NTK — it is **state-dependent**: the effective learning rate depends on the current value of $w$.

:::callout {title="Exercise" tone="amber"}
**Exercise 6.1 (Linearizing the NTK).** Now initialize at a **large** value $w_{0} \gg s > 0$. Assume that in the early phase of training, while $w$ has not changed much from $w_{0}$, the ODE becomes approximately:

$$
\dot{w}\approx 2w_{0}(s - w)
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Starting from the same ODE $\dot{w}= 2w(s - w)$, with $w_{0} \gg s > 0$, the weight $w$ needs to decrease from $w_{0}$ to $s$. As long as $w$ has not changed much from $w_{0}$, we can write $w = w_{0} + \delta w$ with $|\delta w| \ll w_{0}$, so:

$$
2w = 2(w_{0} + \delta w) \approx 2w_{0}
$$

The ODE becomes:

$$
\dot{w}\approx 2w_{0}(s - w) \qquad \square
$$

This is a **linear** ODE — the NTK factor $2w$ has been frozen at its initial value $2w_{0}$. Note that only the NTK prefactor is linearized; the residual $(s - w)$ is kept exact since it drives learning.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 6.2 (Frozen-NTK solution).** Solve the linearized ODE from Exercise 6.1. Show that:

$$
w(t) = s + (w_{0} - s)\,e^{-2w_0 t}
$$

What is the learning timescale?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The linearized ODE $\dot{w}= 2w_{0}(s - w)$ is first-order linear. Set $\tilde{w}:= w - s$, then $\dot{\tilde{w}}= -2w_{0}\,\tilde{w}$, with solution $\tilde{w}(t) = (w_{0} - s)\,e^{-2w_0 t}$. Therefore:

$$
\boxed{w(t) = s + (w_0 - s)\,e^{-2w_0 t}}
$$

This is **exponential** convergence to $s$ (contrast with the sigmoid of Section 5). The learning timescale is:

$$
t_{\text{lazy}}\sim \frac{1}{2w_{0}}
$$

It depends on the **initialization scale** $w_{0}$ but **not on the target** $s$. This is the defining feature of the lazy regime: the learning speed is set by the NTK at initialization, not by the structure of the task.

**Self-consistency:** During the learning phase ($t \lesssim 1/(2w_{0})$), the displacement is $|w(t) - w_{0}| \leq |s - w_{0}| \approx w_{0}$ (since $w_{0} \gg s$). The relative change in the NTK is $\Delta(2w)/(2w_{0}) = (w_{0} - s)/w_{0} = 1 - s/w_{0} \approx 1$, so the NTK does change significantly in absolute terms. However, the key point is that the dynamics remain well approximated by the linear ODE because the convergence rate is dominated by $2w_{0}$, which is large and approximately constant throughout training. In the rich regime, by contrast, the NTK changes from $2w_{0} \approx 0$ to $2s$ — a change of order $s/w_{0} \to \infty$ relative to the initial value — making the linearization completely invalid. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 6.3 (No timescale separation).** Now restore the mode index $\alpha$. In the lazy regime, each mode satisfies $\dot{w}_{\alpha} \approx 2w_{0}(s_{\alpha} - w_{\alpha})$ with the **same** rate $2w_{0}$ for all $\alpha$. Compare the lazy learning time $t_{\alpha}^{\text{lazy}}$ with the rich-regime timescale from Exercise 5.3: $t_{\alpha}^{\text{rich}}\propto 1/s_{\alpha}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Restoring the mode index, each mode satisfies $\dot{w}_{\alpha} \approx 2w_{0}(s_{\alpha} - w_{\alpha})$ with solution:

$$
w_{\alpha}(t) = s_{\alpha} + (w_{0} - s_{\alpha})\,e^{-2w_0 t}
$$

All modes converge at the **same exponential rate** $2w_{0}$, regardless of $s_{\alpha}$. The time for mode $\alpha$ to go from $w_{0}$ to within $(1-\epsilon)$ of $s_{\alpha}$ is:

$$
t_{\alpha}^{\text{lazy}}= \frac{1}{2w_{0}}\ln\!\left(\frac{w_{0} - s_{\alpha}}{\epsilon\,(w_{0} - s_{\alpha})}\right) = \frac{1}{2w_{0}}\ln\frac{1}{\epsilon}
$$

which is **independent of $s_{\alpha}$**. All modes reach their targets simultaneously.

**Contrast with the rich regime:**

|  | Rich regime | Lazy regime |
| --- | --- | --- |
| NTK | State-dependent: $2w_{\alpha}$ | Frozen: $2w_{0}$ |
| Learning time for mode $\alpha$ | $t_{\alpha}\propto 1/s_{\alpha}$ | $t_{\alpha}\approx \text{const}$ |
| Timescale separation | Strong: $t_{1}\ll t_{2}\ll \cdots$ | None |
| Intermediate solutions | Low-rank (incremental) | Full-rank from the start |
| Implicit rank bias | Yes (low-rank → high-rank) | No |

In the lazy regime, all components of $M$ are learned simultaneously: signal and noise alike. The network converges directly to the full OLS solution without passing through low-rank intermediates. There is no mechanism to separate signal from noise based on singular value structure. With early stopping, the rich regime recovers a low-rank signal while ignoring noise; the lazy regime cannot. $\square$

:::

\## 7. Mixed dynamics: unifying lazy and rich

In practice, networks are neither purely lazy nor purely rich. Tu, Aranguri & Jacot (2024) provide a unified description. We develop the key ideas using the diagonal scalar model.

:::callout {title="Exercise" tone="amber"}
**Exercise 7.1 (The interpolating ODE).** In Sections 5 and 6, we studied the same ODE $\dot{w}_{\alpha} = 2w_{\alpha}(s_{\alpha} - w_{\alpha})$ in two limits: small $w_{0}$ (rich) and large $w_{0}$ (lazy). A more general model for a depth-2 DLN with balanced initialization at scale $\sigma$ and width $n$ replaces the scalar NTK $2w_{\alpha}$ by:

$$
\dot{w}_{\alpha} = 2\sqrt{w_{\alpha}^{2} + \tau^{2}}\;(s_{\alpha} - w_{\alpha})
$$

where $\tau := \sigma^{2} \sqrt{n}$ is a **threshold** parameter that depends on the initialization scale and width.

Verify that this ODE reproduces the two known regimes:

- **Rich limit** ($\tau \to 0$): recover $\dot{w}_{\alpha} = 2|w_{\alpha}|(s_{\alpha} - w_{\alpha})$.
- **Lazy limit** ($\tau \to \infty$ with $w_{\alpha}$ bounded): recover $\dot{w}_{\alpha} \approx 2\tau(s_{\alpha} - w_{\alpha})$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The interpolating ODE is $\dot{w}_{\alpha} = 2\sqrt{w_{\alpha}^{2} + \tau^{2}}\,(s_{\alpha} - w_{\alpha})$.

**Rich limit ($\tau \to 0$):** The square root reduces to $\sqrt{w_{\alpha}^{2}}= |w_{\alpha}|$, giving:

$$
\dot{w}_{\alpha} = 2|w_{\alpha}|(s_{\alpha} - w_{\alpha})
$$

For $w_{\alpha} > 0$ this is $2w_{\alpha}(s_{\alpha} - w_{\alpha})$, exactly the logistic ODE from Exercise 5.2. $\square$

**Lazy limit ($\tau \to \infty$, $w_{\alpha}$ bounded):** The square root is dominated by $\tau$: $\sqrt{w_{\alpha}^{2} + \tau^{2}}\approx \tau$, giving:

$$
\dot{w}_{\alpha} \approx 2\tau(s_{\alpha} - w_{\alpha})
$$

This is a linear ODE with rate $2\tau$, independent of $s_{\alpha}$ — the frozen-NTK regime of Section 6 (with $\tau$ playing the role of $w_{0}$). $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 7.2 (Two-phase dynamics).** At initialization, all modes start at $w_{\alpha}(0) \sim \sigma^{2} \ll \tau$ (since $\sqrt{n}\gg 1$). Observe that:

- When $|w_{\alpha}| \ll \tau$, the effective learning rate is $\approx 2\tau$, the same for all modes (lazy behavior).
- When $|w_{\alpha}| \gg \tau$, the effective learning rate is $\approx 2|w_{\alpha}|$, which is mode-dependent (rich behavior).

Describe the resulting two-phase dynamics in words: what happens first, and what happens later?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

At initialization, $w_{\alpha}(0) \sim \sigma^{2} \ll \tau = \sigma^{2}\sqrt{n}$ (since $\sqrt{n}\gg 1$). So initially all modes satisfy $|w_{\alpha}| \ll \tau$.

**Early phase (lazy):** $\sqrt{w_{\alpha}^{2} + \tau^{2}}\approx \tau$ for all $\alpha$. Every mode evolves at the same linear rate $2\tau$:

$$
\dot{w}_{\alpha} \approx 2\tau(s_{\alpha} - w_{\alpha}) \qquad \Longrightarrow \qquad w_{\alpha}(t) \approx s_{\alpha}(1 - e^{-2\tau t})
$$

(assuming $w_{\alpha}(0) \approx 0$). The dynamics are approximately linear and the NTK is approximately constant. During this phase, the network **aligns** with the task: each $w_{\alpha}$ grows toward $s_{\alpha}$ at the same rate. There is no timescale separation.

**Late phase (rich):** Once some $w_{\alpha}$ grow past $\tau$, the square root transitions to $\sqrt{w_{\alpha}^{2} + \tau^{2}}\approx |w_{\alpha}|$, and those modes enter the rich regime with the sigmoidal, self-accelerating dynamics $\dot{w}_{\alpha} \approx 2w_{\alpha}(s_{\alpha} - w_{\alpha})$. The state-dependent NTK creates timescale separation, and the modes that have crossed the threshold converge rapidly to their targets.

In summary: the network starts in a lazy phase where all modes grow uniformly (alignment), then transitions to a rich phase where modes accelerate individually (incremental learning). $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 7.3 (Mode-by-mode transition).** Not all modes cross the threshold $\tau$ at the same time: which modes cross it first? Explain why this means that a single network can simultaneously have some modes in the rich regime and others still in the lazy regime.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

In the lazy phase, each mode grows as $w_{\alpha}(t) \approx s_{\alpha}(1 - e^{-2\tau t})$. At any given time, $w_{\alpha}(t) \propto s_{\alpha}$: **modes with larger $s_{\alpha}$ are larger**. Since the lazy-to-rich transition occurs when $|w_{\alpha}| \sim \tau$, the time for mode $\alpha$ to cross the threshold satisfies:

$$
s_{\alpha}(1 - e^{-2\tau t_\alpha^*}) = \tau \qquad \Longrightarrow \qquad t_{\alpha}^{*} = \frac{1}{2\tau}\ln\frac{s_{\alpha}}{s_{\alpha} - \tau}
$$

For $s_{\alpha} > \tau$, this crossing time exists and is smaller for larger $s_{\alpha}$. For $s_{\alpha} < \tau$, the mode never reaches the threshold and remains permanently lazy.

This means that **different modes can be in different regimes simultaneously**: large-$s_{\alpha}$ modes have crossed into the rich regime and are converging rapidly, while small-$s_{\alpha}$ modes are still in the lazy phase (or may never leave it). The network interpolates between the two regimes mode by mode.

**Connection to grokking:** This lazy-to-rich transition provides a mechanism for grokking. During the lazy phase, the network fits the training data via kernel regression with the initial (misaligned) NTK — it **memorizes**. The test loss plateaus because the frozen kernel cannot capture the task structure. Later, as modes cross the threshold into the rich regime, feature learning kicks in: the NTK rotates to align with the task, and the test loss drops — **generalization** is achieved. The grokking delay is controlled by the time it takes the relevant modes to cross $\tau$. Increasing the initialization scale $\sigma$ or the width $n$ increases $\tau$, which extends the lazy phase and widens the grokking gap. This is the same mechanism identified by Kumar et al., *Grokking as the Transition from Lazy to Rich Training Dynamics* (arXiv:2310.06110). $\square$

:::
