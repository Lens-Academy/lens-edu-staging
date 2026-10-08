---
id: '062bc7a1-e1ac-4e09-945b-7a2b3ad52e7a'
title: "E.2.3 Perfect information-theoretic steganography"
tldr: "Steganography as a hypothesis test, perfect (information-theoretic) indistinguishability measured by total variation distance, and a proof that the key must carry at least as much entropy as the message."
summary_for_tutor: "Sections 5 to 8 of Iliad worksheet E.2: Definition 5.1 (steganography, covertext, P = Model(p) versus Q = Steg_k(p, m), hypothesis test H_0 versus H_1), Definition 6.1 (perfect indistinguishability, P = Q, total variation distance), Fact 6.2 (optimal distinguishing probability), Theorem 7.1 H(M) <= H(K) with a collapsed proof via mutual information and the chain rule, the one-time-pad analogy, and why this is impractical. Keep the notation M, K, X, P, Q."
authors:
  - Stephan Wäldchen (Independent)
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/steganography/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. What is steganography?

:::callout {title="Definition" tone="blue"}

**Definition 5.1 (Steganography (informal)).** **Steganography** is the problem of hiding a secret message inside an ordinary-looking object, called the *covertext*, so that an observer cannot tell whether hidden communication is taking place.

:::

In the LLM asetting:

- the innocent channel is the normal language model,
- the covertext is the model's response,
- the hidden message is a payload embedded in that response,
- the adversary sees the response and tries to decide whether it is ordinary model output or steganographic output.

Formally, for a prompt $$p$$, let

$$
P = \mathrm{Model}(p)
$$

be the innocent distribution over responses, and let

$$
Q = \mathrm{Steg}_{k}(p,m)
$$

be the steganographic distribution when hiding message $$m$$ using key $$k$$.

The adversary performs hypothesis testing:

$$
H_{0}: x \sim P
$$

versus

$$
H_{1}: x \sim Q.
$$

The goal is that the adversary cannot reliably distinguish these two cases.

\## 6. Perfect information-theoretic steganography

:::callout {title="Definition" tone="blue"}

**Definition 6.1 (Perfect information-theoretic indistinguishability).** The strongest possible notion is **perfect information-theoretic indistinguishability**.

This means that the stego output distribution is exactly the same as the innocent output distribution:

$$
P = Q.
$$

Equivalently,

$$
d_{\mathrm{TV}}(P,Q)=0,
$$

where total variation distance is

$$
d_{\mathrm{TV}}(P,Q) = \frac{1}{2}\sum_{x} |P(x)-Q(x)|.
$$

:::

:::callout {title="Note" tone="blue"}

**Fact 6.2 (Optimal distinguishing probability).** Total variation distance is the operational distance for hypothesis testing. If the adversary gets one sample and the two hypotheses have equal prior probability, then the optimal success probability is

$$
\Pr[\text{correct}] = \frac{1}{2}\left(1+d_{\mathrm{TV}}(P,Q)\right).
$$

:::

So if $$d_{\mathrm{TV}}(P,Q)=0$$, no adversary, even an unbounded one, can distinguish stego output from innocent output.

\## 7. Why perfect steganography needs large secret randomness

Suppose:

- $$M$$ is the hidden message,
- $$K$$ is the shared secret key or randomness,
- $$X$$ is the transmitted stegotext.

:::callout {title="Theorem" tone="green"}

**Theorem 7.1 (Perfect steganography needs key entropy).** For perfect information-theoretic steganography with perfect recovery, the shared secret must contain at least as much entropy as the hidden message:

$$
\boxed{H(M)\le H(K).}
$$

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

Assume perfect hiddenness:

$$
I(M;X)=0.
$$

That means the observed stegotext $$X$$ reveals no information about the hidden message.

Also assume perfect decoding:

$$
H(M \mid X,K)=0.
$$

That means the receiver can recover $$M$$ exactly from the stegotext and the secret key.

Then:

$$
H(M)=I(M;X,K).
$$

By the chain rule,

$$
I(M;X,K) = I(M;X)+I(M;K\mid X).
$$

Since $$I(M;X)=0$$,

$$
H(M)=I(M;K\mid X).
$$

And since mutual information is bounded by entropy,

$$
I(M;K\mid X)\le H(K\mid X)\le H(K).
$$

Therefore,

$$
H(M)\le H(K).
$$

:::

For arbitrarily many hidden messages, a finite fixed key is not enough. One needs an unbounded supply of shared secret randomness, or some mechanism for refreshing it.

:::callout {title="Note" tone="blue"}

**Remark.** This is analogous to the one-time pad: perfect secrecy consumes secret key material.

:::

\## 8. Why this is often impractical

If sender and receiver already have a secret channel capable of exchanging large amounts of fresh randomness, then they could often use that channel directly for communication or key refreshment.

:::callout {title="Note" tone="blue"}

**Remark.** That does not make steganography useless, because steganography hides *the existence of communication*, whereas encryption only hides *the content*. But it does mean that perfect information-theoretic steganography is usually expensive in secret randomness.

:::

Therefore, practical schemes often use a short reusable secret key and settle for **computational security**.
