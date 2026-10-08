---
id: '3a723759-d611-4456-9802-7212d72d392c'
title: "E.2.4 Computational steganography"
tldr: "Computational steganography with a short reusable key, pseudorandom functions, how PRF-driven token sampling hides a message, the brute-force attack cost, and the assumptions behind it."
summary_for_tutor: "Sections 9 to 14 of Iliad worksheet E.2: Definition 9.1 (computational steganography, no efficient adversary distinguishes P from Q), Definition 10.1 (pseudorandom function family F_k with negligible distinguishing advantage), Example 11.1 (PRF-driven token sampling with cat, dog, fox at 0.5, 0.3, 0.2), attack cost O(2^lambda), the assumption of one-way functions rather than P not equal NP, and a final summary of the perfect versus computational trade-off."
authors:
  - Stephan Wäldchen (Independent)
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/steganography/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 9. Computational steganography

:::callout {title="Definition" tone="blue"}

**Definition 9.1 (Computational steganography).** In computational steganography, the requirement is weakened.

Instead of demanding

$$
P=Q
$$

against all adversaries, we demand that no efficient adversary can distinguish $$P$$ from $$Q$$.

:::

So the guarantee is not:

> no one can distinguish the two distributions.

It is:

> no polynomial-time adversary can distinguish them with non-negligible advantage.

:::callout {title="Warning" tone="amber"}

An unbounded adversary may still break the scheme.

:::

\## 10. Pseudorandom functions

:::callout {title="Definition" tone="blue"}

**Definition 10.1 (Pseudorandom function).** A **pseudorandom function** (PRF) is a family of keyed functions

$$
F=\{F_{k}:\{0,1\}^{\ell_1(\lambda)}\to \{0,1\}^{\ell_2(\lambda)}\mid k\in\{0,1\}^{\lambda}\}.
$$

It is a PRF if:

1. $$F_{k}$$ is efficiently computable given $$k$$.
2. For every probabilistic polynomial-time distinguisher $$D$$,

$$
\left| \Pr_{k\leftarrow\{0,1\}^{\lambda}}\left[D^{F_k(\cdot)}(1^{\lambda})=1\right] - \Pr_{f} \left[D^{f(\cdot)}(1^{\lambda})=1\right] \right| \le \mathrm{negl}(\lambda),
$$

where $$f$$ is a truly random function with the same domain and range.

:::

:::callout {title="Note" tone="blue"}

**Remark.** Intuitively:

- a truly random function requires an enormous amount of randomness,
- a PRF uses only a short key,
- but to efficient algorithms, it looks like a truly random function.

:::

\## 11. How the paper uses this idea

:::callout {title="Tip" tone="green"}

**Example 11.1 (PRF-driven token sampling).** The LLM normally samples from a next-token distribution. For example, if the model predicts

$$
\Pr(\text{cat})=0.5,\quad \Pr(\text{dog})=0.3,\quad \Pr(\text{fox})=0.2,
$$

then ordinary sampling draws a uniform random number $$u\in[0,1]$$ and chooses:

- cat if $$u<0.5$$,
- dog if $$0.5\le u<0.8$$,
- fox if $$0.8\le u<1$$.

The steganographic scheme does the same thing, except $$u$$ is generated from a secret-keyed PRF.

:::

Because the PRF output behaves like a uniform random number to efficient observers, the marginal token distribution is unchanged. The model still outputs cat, dog, and fox with probabilities $$0.5,0.3,0.2$$.

The hidden message is encoded by making the PRF input depend on the hidden symbol currently being transmitted. The decoder, knowing the key, tests which candidate hidden symbol best explains the observed sequence of sampled tokens.

\## 12. Attack cost

If the secret key has length $$\lambda$$, the generic brute-force attack is to try all possible keys:

$$
2^{\lambda}.
$$

For each candidate key, the attacker checks whether the observed text has the statistical structure expected under that key. If the correct key is found, the attacker can run the retrieval algorithm and decode the payload.

So the brute-force attack cost is roughly

$$
O(2^{\lambda}).
$$

More carefully:

- the attack cost is *at most* $$2^{\lambda}$$ by exhaustive search;
- a weak PRF or flawed construction could allow faster attacks;
- a well-designed scheme aims to make exhaustive search the best available strategy.

\## 13. Relation to assumptions

:::callout {title="Warning" tone="amber"}

The relevant assumption is not simply

$$
P\ne NP.
$$

That is too weak for modern cryptography.

:::

A more standard assumption is the existence of **one-way functions**, which implies the existence of PRFs.

So the computational-security story is:

1. Assume secure PRFs exist.
2. Replace true randomness by PRF-generated randomness.
3. Efficient adversaries cannot distinguish the PRF from true randomness.
4. Therefore efficient adversaries cannot distinguish stego output from innocent output, except with negligible advantage.

But an unbounded adversary can still brute-force the key or distinguish the PRF family from a truly random function.

\## 14. Final summary

Perfect information-theoretic steganography requires

$$
P_{\text{stego}}=P_{\text{innocent}}
$$

exactly, and with perfect decoding it requires secret randomness satisfying

$$
H(K)\ge H(M).
$$

So unlimited perfect hidden communication requires an unlimited or refreshed secret resource.

Computational steganography instead uses a short reusable key and a PRF. The output distribution is computationally indistinguishable from innocent model output, assuming the PRF is secure. This gives practical steganography, but only against efficient adversaries.

The tradeoff is:

$$
\text{perfect security}\Rightarrow \text{large fresh secret randomness}
$$

whereas

$$
\text{short reusable key}\Rightarrow \text{computational security only}.
$$
