---
title: "Negative Results for Sparse Autoencoders On Downstream Tasks and Deprioritising SAE Research (Mechanistic Interpretability Team Progress Update)"
author:
  - "DeepMind Safety Research"
source_url: "https://deepmindsafetyresearch.medium.com/negative-results-for-sparse-autoencoders-on-downstream-tasks-and-deprioritising-sae-research-6cadcfc125b9"
published: 2025-03-26
created: 2026-11-22
accessed: 2026-11-22
allowAuthorInTitle: true
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "Lewis Smith*, Sen Rajamanoharan*, Arthur Conmy, Callum McDougall, Janos Kramar, Tom Lieberum, Rohin Shah, Neel Nanda"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Lewis Smith\*, Sen Rajamanoharan\*, Arthur Conmy, Callum McDougall, Janos Kramar, Tom Lieberum, Rohin Shah, Neel Nanda_

_\* = equal contribution_

The following piece is a list of snippets about research from the GDM mechanistic interpretability team, which we didn’t consider a good fit for turning into a paper, but which we thought the community might benefit from seeing in this less formal form. These are largely things that we found in the process of a project investigating whether sparse autoencoders were useful for downstream tasks, notably out-of-distribution probing.

This blog post consists of the summary and introduction, you can see the full technical details and complete snippets in [our accompanying Alignment Forum post](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft)

## TL;DR ^tl-dr

-   To validate whether SAEs were a worthwhile technique, [we explored whether they were useful on the downstream task of OOD generalisation when detecting harmful intent in user prompts](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Using_SAEs_for_OOD_Probing)
-   Negative result: [SAEs underperformed linear probes](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Results)  
    – Corollary: Linear probes are actually really good and cheap and perform great
-   As a result of this and parallel work, [**we are deprioritising fundamental SAE research for the moment and exploring other directions**](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Conclusions_and_Strategic_Updates), though SAEs will remain a tool in our toolkit  
    – We do **not** think that SAEs are useless or that no one should work on them, but we also do not think that SAEs will be a game-changer for interpretability, and speculate that the field is over-invested in them.
-   [Training SAEs specialised for chat data closed about half the gap but was still worse than linear probes](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Results)  
    – [We tried several ways to train chat SAEs, all did about as well](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Comparing_different_ways_to_train_Chat_SAEs). By default, we recommend taking an SAE on pretraining data and finetuning it on a bit of chat data
-   Other results:  
    – [We found SAEs fairly helpful for debugging low quality datasets](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Dataset_debugging_with_SAEs) (noticing spurious correlations)  
    – [We present a variant of JumpReLU with an alternative sparsity penalty to get rid of high-frequency latents](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Removing_High_Frequency_Latents_from_JumpReLU_SAEs)  
    – [We argue that a standard auto-interp approach of computing the average interpretability of a uniformly sampled SAE latent can be misleading](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Autointerp_and_high_frequency_latents) as it doesn’t penalise models which have high frequency, but not very interpretable, latents, and explore weighting the interpretability score by latent frequency.

## Introduction ^introduction

## Motivation ^motivation

Our core motivation was that we, along with much of the interpretability community, had invested a lot of our energy into Sparse Autoencoder (SAE) research. But SAEs lack a ground truth of the “true” features in language models to compare to, making it pretty unclear how well they work. There is qualitative evidence that SAEs are clearly doing _something_, far more structure than you would expect by random chance. But they clearly have a bunch of issues: if you just type an arbitrary sentence into [Neuronpedia](http://neuronpedia.org/), and look at the latents that light up, they do not seem to perfectly correspond to a crisp explanation.

More generally, when thinking about whether we should prioritise working on SAEs, it’s worth thinking about how to decide what kind of interpretability research to do in general. One perspective is to assume there is some crisp, underlying, human-comprehensible truth for what is going on in the model, and to try to build techniques to reverse engineer it. In the case of SAEs, this looks like [the hope that SAE latents capture some canonical set of true concepts inside the model](https://www.lesswrong.com/posts/tojtPCCRpKLSHBdpn/the-strong-feature-hypothesis-could-be-wrong). We think it is clear now that [SAEs in their current form are far from achieving this](https://www.arxiv.org/abs/2502.04878), and it is unclear to us if such “true concepts” even exist. There are several flaws with SAEs that prevent them from capturing a true set of concepts even if one exists, and we are pessimistic that these can all be resolved:

-   [SAEs are missing concepts](https://www.arxiv.org/abs/2502.04878)
-   Concepts are represented in noisy ways where e.g. [small activations don’t seem interpretable](https://transformer-circuits.pub/2023/monosemantic-features#feature-arabic)
-   Latents can be warped in weird ways like [feature absorption](https://arxiv.org/abs/2409.14507)
-   [Seemingly interpretable latents have many false negatives](https://transformer-circuits.pub/2024/july-update/index.html#feature-sensitivity).
-   For more issues with SAEs see Section 2.1.2c of [Sharkey et al.](https://arxiv.org/pdf/2501.16496)

But there are other high-level goals for interpretability than perfectly finding the objective truth of what’s going on — if we can build tools that give understanding that’s imperfect but enough to let us do useful things, like understand whether [a model is faking alignment](https://arxiv.org/abs/2412.14093), that is still very worthwhile. Several important goals, like trying to debug mysterious failures and phenomena, achieving a better understanding of what goals and deception look like, or trying to detect deceptive alignment, do not necessarily require us to discover all of the ‘true features’ of a model; a decent approximation to the models computation might well be good enough. But how could we tell if working on SAEs was bringing us closer to these goals?

Our hypothesis was that if SAEs will eventually be useful for these ambitious tasks, they should enable us to do _something_ new today. So, the goal of this project was to investigate [whether we can do anything useful on downstream tasks](https://www.alignmentforum.org/s/a6ne2ve5uturEEQK7) with SAEs in a way that was at all competitive with baselines — i.e. a task that can be described without making any reference to interpretability. If SAEs are working well enough to be a valuable tool, then there should be things they enable us to do that we cannot currently easily do. And so we thought that if we picked some likely examples of such tasks and then made a fair comparison to well-implemented baselines on some downstream task then, if the SAE does well (ideally beating the baseline, but even just coming close while being non-trivially different), this is a sign that the SAE is a valuable technique worthy of further refinement. Further, even if the SAE doesn’t succeed, it gives you an eval to measure future SAE progress, like how [Farrell et al](https://arxiv.org/abs/2410.19278) ’s unlearning setup was turned into an eval in [SAEBench](https://www.neuronpedia.org/sae-bench/info).

## Our Task ^our-task

So what task did we focus on? Our key criteria was to be objectively measurable, be something that other people cared about and, within those constraints, aiming for something where we thought SAEs might have an edge. As such, we focused on training probes that generalise well out of distribution. We thought that, for sufficiently good SAEs, a sparse probe in SAE latents would be less likely to overfit to minor spurious correlations compared to a dense probe, and thus that being interpretable gave a valuable inductive bias ([though are now less confident in this argument](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Is_it_surprising_that_SAEs_didn_t_work_)). We specifically looked in the context of detecting harmful user intent in the presence of different jailbreaks, and used new jailbreaks as our OOD set.

Sadly, our core results are negative:

1.  Dense linear probes perform nearly perfectly, including out of distribution.
2.  1-sparse SAE probes (i.e. using a single SAE latent as a probe) are much worse, failing to fit the training set.
3.  k-sparse SAE probes can fit the training set for moderate k (approximately k=20), and successfully generalise to an in-distribution test set, but show distinctly worse performance on the OOD set.
4.  Finetuning SAEs on specialised chat data helps, but only closes about half the gap to dense linear probes.
5.  Linear probes trained only on the SAE reconstruction are also significantly worse than linear probes on the residual stream OOD, suggesting that SAEs are discarding information relevant to the target concept

We did have one positive result: the sparse SAE probes enabled us to quickly identify spurious correlations in our dataset, which we cleaned up. Note this slightly stacks the deck against SAEs, since without SAE-based debugging, the linear probes may have latched onto these spurious correlations — however, we think we plausibly could have found the spurious correlations without SAEs given more time, e.g. [Kantamneni et al](https://arxiv.org/abs/2502.16681) showed simpler methods could be similarly effective to SAEs here.

We were surprised by SAEs underperforming linear probes, but also by how well linear probes did in absolute terms, on the complex-seeming task of detecting harmful intent. [We expect there are many practical ways linear probes could be used today](https://www.alignmentforum.org/posts/aG9e5tHfHmBnDqrDy/the-gdm-agi-safety-alignment-team-is-hiring-for-applied) to do cheap monitoring for unsafe behaviour in frontier models.

## Conclusions and Strategic Updates ^conclusions-and-strategic-updates

**Our overall update from this project and parallel external work is to be less excited about research focused on understanding and improving SAEs and, at least for the short term, to explore other research areas**.

The core update we made is that SAEs are unlikely to be a magic bullet, i.e. we think the hope that with a little extra work they can just make models super interpretable and easy to play with doesn’t seem like it will pay off.

The key update we’ve made from our probing results is that current SAEs do not find the ‘concepts’ required to be useful on an important task (detecting harmful intent), but a linear probe can find a useful direction. This may be because the model doesn’t represent harmful intent as a fundamental concept and the SAE is working as intended while the probe captures a mix of tons of concepts, or because the concept is present but the SAE is bad at learning it, or any number of hypotheses. But whatever the reason, it is evidence against SAEs being the right tool for things we want to do in practice.

We consider our probing results disheartening but not enough to pivot on their own. But there have been several other parallel projects in the literature such as [Kantamneni et al](https://arxiv.org/abs/2502.16681)., [Farrell et al](https://arxiv.org/abs/2410.19278)., [Arora et al](https://arxiv.org/abs/2501.17148)., that found negative results on other forms of probing, unlearning and steering, respectively. And the few positive applications with clear comparisons to baselines, like [Karvonen et al](https://www.tilderesearch.com/blog/sieve), largely occur in somewhat niche or contrived settings (e.g. using fairly simple concepts like “is a regex” that SAEs likely find it easy to capture), though there are some signs of life such as [unlearning in diffusion models](https://arxiv.org/abs/2501.18052), [potential usefulness in auditing models](https://www.anthropic.com/research/auditing-hidden-objectives), and [hypothesis generation about labelled text datasets](https://arxiv.org/abs/2502.04382).

We find the comparative lack of positive results here concerning — no individual negative result is a strong update, since it’s not yet clear which tasks are best suited to SAEs, but if current SAEs really are a big step forwards for interpretability, it should not be so hard to find compelling scenarios where they beat baselines. This, combined with the general messiness and issues surfaced by the attempts, and other issues such as poor feature sensitivity, suggest to us that **SAEs and SAE based techniques (**[**transcoders**](https://arxiv.org/abs/2406.11944), [**crosscoders**](https://transformer-circuits.pub/2024/crosscoders/index.html)**, etc) are not likely to be a gamechanger any time soon** and plausibly never will be — we hope to write our thoughts on this topic in more detail soon. We think that the research community’s large investment into SAEs was most justified under the hopes that SAEs could be incredibly transformative to all of the other things we want to do with interpretability. Now that this seems less likely, **we speculate that the interpretability community is somewhat over invested in SAEs**.

To clarify, we are _not_ committing to giving up on SAEs, and **this is not a statement that we think SAEs are useless and that no one should work on them**. We are pessimistic about them being a game changer across the board in their current form, but we predict that there are still some situations where they are able to be useful. We are particularly excited about their potential for exploratory debugging of mysterious failures or phenomena in models, as in [Marks et al](https://arxiv.org/abs/2503.10965), and believe they are worthwhile to keep around in a practitioner’s toolkit. For example, [we found them useful for detecting and debugging spurious correlations in our datasets](https://www.alignmentforum.org/posts/4uXCAJNuPKtKBsi28/sae-progress-update-2-draft#Dataset_debugging_with_SAEs). More importantly, it’s extremely hard to distinguish between fundamental issues and fixable issues, so it’s hard to make any confident statements about what flaws will remain in future SAEs.

As such, we believe that future SAE work is valuable, but should focus much less on hill-climbing on [sparsity reconstruction](https://arxiv.org/abs/2404.16014) [trade-offs](https://arxiv.org/abs/2407.14435), and instead focus on better understanding the fundamental limitations of SAEs, especially those that hold them back on downstream tasks and discovering new limitations; learning how to evaluate and measure these limitations; and learning how to address them, whether by incremental improvements or fundamental improvements. One recent optimistic sign was [Matryoshka SAEs](https://arxiv.org/abs/2503.17547), a fairly incremental change to the SAE loss that seems to have made substantial strides on feature absorption and feature composition. We think that a great form of project is to take a known issue with SAEs, tries to think about why it happens and what changes could fix it, and then verifying that the issue has improved. If researchers have an approach they think is promising that could make substantial progress on an issue with SAEs, we would be excited to see that pursued.

There are also other valuable projects, for example, are there much cheaper ways we can train SAEs of acceptable quality? Or to get similar effects with other feature clustering or dictionary learning methods instead? If we’re taking a pragmatic approach to SAEs, rather than the ambitious approach of trying to find the canonical units of analysis, then sacrificing some quality in return for lowering the major up front cost of SAE training may be worthwhile.

We could imagine coming back to SAE research if we thought we had a particularly important and tractable research direction, or if there is significant progress on some of their core issues. And we still believe that interpreting the concepts in LLM activations is a crucial problem that we would be excited to see progress on. But for the moment we intend to explore some other research directions, such as model diffing, interpreting model organisms of deception, and trying to interpret thinking models.
