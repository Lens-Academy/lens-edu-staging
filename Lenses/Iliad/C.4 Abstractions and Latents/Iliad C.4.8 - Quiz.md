---
id: '70ece8d4-918c-45b2-8940-0fca9d2be044'
title: "C.4.8 Quiz"
tldr: "Eight quiz questions on mutual information, latent models, perfect condensation and correspondence, reproduced from the form."
summary_for_tutor: "This is Section 5 (Quiz) of Iliad worksheet C.4 Condensation: eight multiple-choice questions reproduced from the quiz form. Questions 1-3 use the overlapping-bits model (mutual information, H(Y_{1,2}|X_1), which condition fails with singleton latents), question 4 completes the two-witness bound, question 5 applies the correspondence theorem with |A|=k, question 6 asks what H(U|V)=H(V|U)=0 does not establish, question 7 asks whether the noisy pair admits a perfect condensation and question 8 which latents must determine one another. Let the student answer each question before confirming or explaining the correct option."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. Quiz

Take the quiz at [this link](https://docs.google.com/forms/d/e/1FAIpQLSdTAs3Dq6dOeoju0TsyfaVcEcRdZaNgpAe_FMC7rCR3fohOSw/viewform). The questions are reproduced here because the form cannot typeset mathematics.

\### 5.1 Questions

Use base-two logarithms. In questions 1–3, $$S,P,Q$$ are independent fair bits and $$X_{1}=(S,P)$$, $$X_{2}=(S,Q)$$, $$X_{3}=(P,Q)$$, with latents $$Y_{\{1,2\}}=S$$, $$Y_{\{1,3\}}=P$$ and $$Y_{\{2,3\}}=Q$$.

1. What is $$I(X_{1};X_{2})$$?
   - $$0$$
   - $$1$$
   - $$2$$
   - $$3$$
2. Same model. What is $$H(Y_{\{1,2\}}\mid X_{1})$$?
   - $$0$$
   - $$1/2$$
   - $$1$$
   - $$2$$
3. Now put $$Y_{\{i\}}=X_{i}$$ at each singleton address, with every other latent constant. Which condition fails?
   - the latent variable model condition (LVM)
   - the reconstruction condition
   - the Markov condition
   - none of them fails
4. Complete the two-witness bound $$H(U\mid M)\le H(U\mid M,P)+H(U\mid M,Q)+{}$$ ?
   - $$I(P;Q)$$
   - $$I(P;Q\mid M)$$
   - $$H(P\mid Q)$$
   - $$0$$
5. In the correspondence theorem with $$|A|=k$$, suppose every reconstruction error and every Markov defect is at most $$\varepsilon$$. What is the bound on $$H(Y_{{\mathord{\supseteq}} A}\mid Z_{{\mathord{\supseteq}} A})$$?
   - $$k\varepsilon$$
   - $$(k-1)\varepsilon$$
   - $$(2k-1)\varepsilon$$
   - $$2k\varepsilon$$
6. Two corresponding families of latents satisfy $$H(U\mid V)=H(V\mid U)=0$$. Which of these does that *not* establish?
   - each family is a function of the other almost surely
   - neither family retains uncertainty about the other
   - an efficient procedure for translating between them
   - the two families carry the same information
7. Let $$X_{1}$$ be a fair bit and $$X_{2}=X_{1}\mathbin{\oplus}N$$ with $$N\sim\operatorname{Bernoulli}(q)$$, $$0<q<1/2$$. Does this pair admit a perfect condensation?
   - yes: put $$(X_{1},X_{2})$$ in the top latent
   - yes: put each $$X_{i}$$ in its singleton latent
   - no: the top latent must be constant, so the Markov condition would force $$X_{1},X_{2}$$ to be independent
   - only for small enough $$q$$
8. $$Y$$ and $$Z$$ are perfect condensations of the same observables. Which must determine one another?
   - $$Y_{\{1\}}$$ and $$Z_{\{1\}}$$
   - the towers $$Y_{{\mathord{\supseteq}}\{1\}}$$ and $$Z_{{\mathord{\supseteq}}\{1\}}$$
   - $$Y_{\{1,2\}}$$ and $$Z_{\{1\}}$$
   - nothing, in general
