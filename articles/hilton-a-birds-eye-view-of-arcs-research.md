---
title: "A bird's eye view of ARC's research"
author:
  - "Jacob Hilton"
source_url: "https://www.lesswrong.com/posts/ztokaf9harKTmRcn4/a-bird-s-eye-view-of-arc-s-research"
published: 2024-10-23
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "This post includes a \"flattened version\" of an interactive diagram that cannot be displayed on this site. I recommend reading the original version of…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_This post includes a "flattened version" of an interactive diagram that cannot be displayed on this site. I recommend reading the original version of the post with the interactive diagram, which can be found [here](https://www.alignment.org/blog/a-birds-eye-view-of-arcs-research)._

Over the last few months, ARC has released a number of pieces of research. While some of these can be independently motivated, there is also a more unified research vision behind them. The purpose of this post is to try to convey some of that vision and how our individual pieces of research fit into it.

_Thanks to Ryan Greenblatt, Victor Lecomte, Eric Neyman, Jeff Wu and Mark Xu for helpful comments._

## A bird's eye view ^a-birds-eye-view

To begin, we will take a "bird's eye" view of ARC's research.[^note-diagram-arrows] As we "zoom in", more nodes will become visible and we will explain the new nodes.

_An interactive version of the diagrams below can be found [here](https://www.alignment.org/blog/a-birds-eye-view-of-arcs-research)._

### Zoom level 1 ^zoom-level-1

![birds\_eye\_lvl1.svg](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hilton-a-birds-eye-view-of-arcs-research-img1-2039d90b.png)

At the most zoomed-out level, ARC is working on the problem of "[intent alignment](https://ai-alignment.com/clarifying-ai-alignment-cec47cd69dd6)": how to design AI systems that are trying to do what their operators want. While many practitioners are taking an iterative approach to this problem, there are [foreseeable ways](https://arxiv.org/abs/2307.15217) in which today's leading approaches could fail to scale to more intelligent AI systems, which could have [undesirable consequences](https://www.cold-takes.com/without-specific-countermeasures-the-easiest-path-to-transformative-ai-likely-leads-to-ai-takeover/). ARC is attempting to develop algorithms that have a better chance of scaling gracefully to future AI systems, hence the term "**scalable alignment**".

ARC's particular approach to scalable alignment is a "builder-breaker" methodology (described in more detail [here](https://ai-alignment.com/my-research-methodology-b94f2751cb2c), and exemplified in the [ELK report](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit)). Roughly speaking, if the scalability of an algorithm depends on unknown empirical contingencies (such as how advanced AI systems generalize), then we try to make worst-case assumptions instead of attempting to extrapolate from today's systems. This is intended to create a feasible iteration loop for theoretical research. We are also conducting empirical research, but mostly to help generate and probe theoretical ideas rather than to test different empirical assumptions.

### Zoom level 2 ^zoom-level-2

![birds\_eye\_lvl2.svg](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hilton-a-birds-eye-view-of-arcs-research-img2-21915dc0.png)

Most of ARC's research attempts to solve one of two central subproblems in alignment: alignment robustness and eliciting latent knowledge (ELK).

**Alignment robustness** refers to AI systems remaining intent aligned even when faced with out-of-distribution inputs.[^note-alignment-robustness-term] There are a few reasons to focus on failures of alignment robustness, as discussed [here](https://ai-alignment.com/techniques-for-optimizing-worst-case-performance-39eafec74b99) (where they are called "malign" failures). A quintessential example of an alignment robustness failure is [_deceptive alignment_](https://arxiv.org/abs/1906.01820), also known as "[scheming](https://arxiv.org/abs/2311.08379)": the possibility that an AI system will internally reason about the objective that it is being trained on, and stop being intent aligned when it detects clues that it has been taken out of its training environment.

**Eliciting latent knowledge (ELK)** is defined in [this report](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit), and asks: how can we train an AI system to honestly report its internal beliefs, rather than what it predicts a human would think? If we could do this, then we could potentially avoid misalignment by checking whether the model's beliefs are consistent with its actions being helpful. ELK could help with scalable alignment via alignment robustness, but it could also help via [outer alignment](https://www.lesswrong.com/posts/SzecSPYxqRa5GCaSF/clarifying-inner-alignment-terminology), by giving the reward function access to relevant information known by the model.

### Zoom level 3 ^zoom-level-3

![birds\_eye\_lvl3.svg](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hilton-a-birds-eye-view-of-arcs-research-img3-34e464cf.png)

ARC hopes to make progress on both alignment robustness and ELK using **heuristic explanations** for neural network behaviors. A heuristic explanation is similar to the kind of explanation found in [mechanistic interpretability](https://www.transformer-circuits.pub/2022/mech-interp-essay), except that ARC is attempting to find a mathematical notion of an "explanation", so that they can be found and used automatically. This is similar to how formal verification for ordinary programs can be performed automatically, except that we believe proof is too strict of a standard to be feasible. These similarities are discussed in more detail in the post [Formal verification, heuristic explanations and surprise accounting](https://www.alignment.org/blog/formal-verification-heuristic-explanations-and-surprise-accounting/) (especially the first couple of sections, up until "Surprise accounting").

A heuristic explanation for a rare but high-stakes kind of failure could help with alignment robustness, while a heuristic explanation for a specific behavior of interest could help with ELK. These two applications of heuristic explanations are fleshed out in more detail at the next zoom level.

### Zoom level 4 ^zoom-level-4

![birds\_eye\_lvl4.svg](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hilton-a-birds-eye-view-of-arcs-research-img4-b298cd9b.png)

ARC has identified two broad ways in heuristic explanations could help with alignment robustness and/or ELK.

**Low probability estimation (LPE)** is the task of estimating the probability of a rare kind of model output. The most obvious approach to LPE is to try to find model inputs that give rise to such an output, but this can be infeasible (e.g. if the model were to implement something like a cryptographic hash function). Instead, we can "[relax](https://www.lesswrong.com/posts/9Dy5YRaoCxH9zuJqa/relaxed-adversarial-training-for-inner-alignment)" this goal and search for a heuristic explanation of why the model could hypothetically produce such an output (e.g. by treating the output of the cryptographic hash function as random). LPE would help with alignment robustness by allowing us to select models for which we cannot explain why they would ever behave catastrophically, even hypothetically. This motivation for LPE is discussed in much greater depth in the post [Estimating Tail Risk in Neural Networks](https://www.alignment.org/blog/estimating-tail-risk-in-neural-networks/).

**Mechanism distinction** describes our broad hope for how heuristic explanations could help with ELK. A central challenge for ELK is "sensor tampering": detecting when the model reports what it predicts a human would think, but the human has been fooled in some way. Our hope is to detect this by noticing that the model's report has been produced by an "abnormal mechanism". There are a few potential ways in which heuristic explanations could be used to perform mechanism distinction, but the one we currently consider the most promising is **mechanistic anomaly detection (MAD)**, as explained in the post [Mechanistic anomaly detection and ELK](https://www.alignment.org/blog/mechanistic-anomaly-detection-and-elk/) (for a gentler introduction to MAD, see [this post](https://www.lesswrong.com/s/GiZ6puwmHozLuBrph/p/n7DFwtJvCzkuKmtbG)). A variant of MAD is **safe distillation**, which is an alternative way to perform mechanism distinction if we also have access to a formal specification of what we are trying to elicit latent knowledge of.

A semi-formal account of how heuristic explanations could enable all of LPE, MAD and safe distillation is given in [Towards a Law of Iterated Expectations for Heuristic Estimators](https://www.alignment.org/blog/research-update-towards-a-law-of-iterated-expectations-for-heuristic-estimators/). An explanation of how MAD could also be used to help with alignment robustness is given in [Mechanistic anomaly detection and ELK](https://www.alignment.org/blog/mechanistic-anomaly-detection-and-elk/) (in the section "Deceptive alignment").

## How ARC's research fits into this picture ^how-arcs-research-fits

We will now explain how some of ARC's research fits into the above diagram at the most zoomed in level. For completeness, we will cover all of ARC's most significant pieces of published research to date, in chronological order. Each piece of work has been labeled with the most closely related node from the diagram, but often also covers nearby nodes and the relationships between them.

| [**Eliciting latent knowledge: How to tell if your eyes deceive you**](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit) defines ELK, explains its importance for scalable alignment, and covers a large number of possible approaches to ELK. Some of these approaches are somewhat related to heuristic explanations, but most are alternatives that we are no longer pursuing. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/gexim4y9pnprmswlgx91) |
| --- | --- |
| [**Formalizing the presumption of independence**](https://arxiv.org/abs/2211.06738) lays out the problem of devising a formal notion of heuristic explanations, and makes some early inroads into this problem. It also includes a brief discussion of the motivation for heuristic explanations and the application to alignment robustness and ELK. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/c88bwyukwyrwoqbfagdc) |
| [**Mechanistic anomaly detection and ELK**](https://www.alignment.org/blog/mechanistic-anomaly-detection-and-elk/) and our other late 2022 blog posts ([**1**](https://www.alignment.org/blog/finding-gliders-in-the-game-of-life/), [**2**](https://www.alignment.org/blog/can-we-efficiently-explain-model-behaviors/), [**3**](https://www.alignment.org/blog/can-we-efficiently-distinguish-different-mechanisms/)) explain the approach to mechanism distinction that we currently find the most promising, mechanistic anomaly detection (MAD). They also cover how mechanism distinction could be used to address alignment robustness and ELK, how heuristic explanations could be used for mechanism distinction, and the feasibility of finding heuristic explanations. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/uhdvvkujmgyqy3npt2u1) |
| [**Formal verification, heuristic explanations and surprise accounting**](https://www.alignment.org/blog/formal-verification-heuristic-explanations-and-surprise-accounting/) discusses the high-level motivation for heuristic explanations by comparing and contrasting them to formal verification for neural networks (as explored in [this paper](https://arxiv.org/abs/2406.11779)) and mechanistic interpretability. It also introduces _surprise accounting_, a framework for quantifying the quality of a heuristic explanation, and presents a [draft](https://www.alignment.org/content/files/2024/06/max_of_k_writeup.pdf) of empirical work on heuristic explanations. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/c88bwyukwyrwoqbfagdc) |
| [**Backdoors as an analogy for deceptive alignment**](https://www.alignment.org/blog/backdoors-as-an-analogy-for-deceptive-alignment/) and the associated paper [**Backdoor defense, learnability and obfuscation**](https://arxiv.org/abs/2409.03077) discuss a formal notion of backdoors in ML models and some theoretical results about it. This serves as an analogy for the subdiagram _Heuristic explanations → Mechanism distinction → Alignment robustness_. In this analogy, alignment robustness corresponds to a model being backdoor-free, mechanism distinction corresponds to the backdoor defense, and heuristic explanations correspond to so-called "mechanistic" defenses. The blog post covers this analogy in more depth. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/oitnkbfpxwjjgckcs73c) |
| [**Estimating Tail Risk in Neural Networks**](https://www.alignment.org/blog/estimating-tail-risk-in-neural-networks/) lays out the problem of low probability estimation, how it would help with alignment robustness, and possible approaches to LPE based on heuristic explanations. It also presents a [draft](https://www.alignment.org/content/files/2024/09/Analytically_Learning_VAEs.pdf) describing an approach to heuristic explanations based on analytically learning variational autoencoders. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/kktrwydz4asgchl1vpby) |
| [**Towards a Law of Iterated Expectations for Heuristic Estimators**](https://www.alignment.org/blog/research-update-towards-a-law-of-iterated-expectations-for-heuristic-estimators/) and the associated [**paper**](https://arxiv.org/abs/2410.01290) discuss a possible coherence property for heuristic explanations as part of the search for a formal notion of heuristic explanations. It also provides a semi-formal account of how heuristic explanations could be applied to low probability estimation and mechanism distinction. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/c88bwyukwyrwoqbfagdc) |
| [**Low Probability Estimation in Language Models**](https://www.alignment.org/blog/low-probability-estimation-in-language-models/) and the associated paper [**Estimating the Probabilities of Rare Outputs in Language Models**](https://arxiv.org/abs/2410.13211) describe an empirical study of LPE in the context of small transformer language models. The method inspired by heuristic explanations outperforms naive sampling in this setting, but does not outperform methods based on red-teaming (searching for inputs giving rise to the rare behavior), although there remain theoretical cases where red-teaming fails. | ![Related diagram node](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ztokaf9harKTmRcn4/kktrwydz4asgchl1vpby) |

## Further subproblems ^further-subproblems

ARC's research can be subdivided further, and we have been putting significant effort into a number of subproblems not explicitly mentioned above. For instance, our work on heuristic explanations includes both work on **formalizing heuristic explanations** (devising a formal framework for heuristic explanations) and work on **finding heuristic explanations** (designing efficient search algorithms for them). Some subproblems of these include:

-   **Measuring quality**: "[surprise accounting](https://www.alignment.org/blog/formal-verification-heuristic-explanations-and-surprise-accounting/#surprise-accounting)" offers a potential way to measure the quality of a heuristic explanation, which is important for being able to search for high-quality explanations. However, it is currently an informal framework with many missing details.
-   **Capacity allocation**: it will probably be too challenging to find high-quality explanations for every aspect of a model's behavior. Instead, we can try to tailor explanations towards behaviors with potentially catastrophic consequences. A good loss function for heuristic explanations should push for quality only where it is relevant to the behavior at hand.
-   **Cherry-picking**: if we use a heuristic explanation to estimate something (as in low probability estimation), we need to make sure that the way in which we find the explanation doesn't systematically bias the estimate.
-   **Form of representation**: one form that a heuristic explanation could take is of an "[activation model](https://www.alignment.org/blog/estimating-tail-risk-in-neural-networks/#layer-by-layer-activation-modeling)", i.e. a probability distribution over a model's internal activations. However, we may also need to represent explanations that do not correspond to any particular probability distribution.
-   **Formal desiderata**: we can attempt to formalize heuristic explanations by considering [properties](https://www.alignment.org/blog/research-update-towards-a-law-of-iterated-expectations-for-heuristic-estimators/) that we think they should satisfy, and seeing if those properties can be satisfied.
-   **No-coincidence principle**: in order for heuristic explanations to work in the worst case, we need every possible behavior to be amenable to explanation. We sometimes refer to this desideratum as the "no-coincidence principle" (a term taken from [this paper](https://mxphi.com/wp-content/uploads/2023/04/MxPhi-Gowers2023.pdf)). Counterexamples to this principle could present obstacles to our approach.
-   **Empirical regularities**: some model weights may have no explanation beyond being tuned to match some empirical average, either because the input distribution is defined empirically, or because of an emergent regularity in a formally-defined system (such as the relative value of a queen and a pawn in chess). A good notion of heuristic explanations should be able to deal with these.

## Conclusion ^conclusion

We have painted a high-level picture of ARC's research, explained how our published research fits into it, and briefly discussed some additional subproblems that we are working on. We hope this provides people with a clearer sense of what we are up to.

[^note-diagram-arrows]: An arrow in the diagram expresses that solving one problem should help solve another, but it varies from case to case whether subproblems combine "conjunctively" (all subproblems need to be solved to solve the main problem) or "disjunctively" (a solution to any subproblem can be used to solve the main problem).
[^note-alignment-robustness-term]: The term "alignment robustness" comes from [this summary](https://www.lesswrong.com/posts/Epm6CkXrdRyAihMRe/an-66-decomposing-robustness-into-capability-robustness-and) of [this post](https://www.lesswrong.com/posts/2mhFMgtAjFJesaSYR/2-d-robustness), and is synonymous with "objective robustness" in the terminology of [this post](https://www.lesswrong.com/posts/SzecSPYxqRa5GCaSF/clarifying-inner-alignment-terminology). A slightly more formal variant is "high-stakes alignment", as defined in [this post](https://ai-alignment.com/low-stakes-alignment-f3c36606937f).
