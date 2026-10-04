---
title: "Should safety researchers quit frontier labs re. warning shots?"
author:
  - "Ryan Kidd"
source_url: "https://www.lesswrong.com/posts/TfqMs3AarsHnHiwai/should-safety-researchers-quit-frontier-labs-re-warning"
published: 2026-09-05
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "I've recently heard a surge of support for an old argument: AI safety researchers should not work at frontier AI companies because this reduces the likelihood of non-lethal warning shots, and we need warning shots to build support for an AI pause/slow-down."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

I've recently heard a surge of support for an old argument: AI safety researchers should not work at frontier AI companies because this reduces the likelihood of non-lethal warning shots, and we need warning shots to build support for an AI pause/slow-down. This argument has several components:

-   **Technical AI safety work is futile, absent an AI pause:** Current "prosaic AGI" safety research agendas pursued at frontier AI companies, like AI control, scalable oversight, interpretability, etc., might not scale to AI systems that matter. Even when such techniques appear to benefit AI alignment, they might merely mask a deeper alignment failure that will manifest, disastrously, as AI capabilities grow. At worst, current alignment/control techniques might incentivize more sophisticated AI model deception. Even if the techniques do scale, they might be too expensive or annoying for AI company leadership to reliably mandate for all deployments, and the military or government might care even less!
-   **Technical AI safety work might block warning shots:** The warning shots that state-of-the-art (SotA) alignment, control, and monitoring techniques can prevent might be "non-lethal" to humanity, whereas future "lethal" incidents might not be prevented by SotA alignment/control techniques. By deploying SotA alignment and control techniques within frontier AI companies, we reduce the risk of warning shots like the OpenAI x Hugging Face incident (which OpenAI monitors supposedly would have caught, had they been turned on for the particular internal deployment), but we might fail to prevent lethal loss-of-control incidents.
-   **Warning shots are instrumental to an AI pause:** If we assume that SotA AI safety research is insufficient to "make AI go well" on the current trajectory, then we might need an AI pause or slowdown (e.g., [Plan A/S](https://ai-2040.com/)). Warning shots might help build political appetite for a pause or slowdown by convincing policymakers and the public that catastrophic AI risks are real. Therefore, people working on alignment or control at a frontier AI company should consider quitting their jobs to increase the chance that non-lethal warning shots occur and spur an AI pause.

I think this argument has some merit. I expect that RLHF++ will probably be insufficient to align TED-AI circa-2028 and such systems will be terrifically difficult to monitor or control. However, I think there are also significant weaknesses to this argument. Here are some countervailing points to consider:

-   **Alignment MVPs are probably still useful:** In spite of the OpenAI x Hugging Face incident, I expect that most AI safety researchers will use frontier models to help with research, including [agent](https://www.lesswrong.com/posts/qTNm8qzqhhpno58fZ/resolution-has-a-new-agent-foundations-team) [foundations](https://www.lesswrong.com/posts/7QvKqpGJwqXrQcMgx/llms-are-starting-to-noticeably-accelerate-our-work) researchers. [Alignment MVPs](https://aligned.substack.com/p/alignment-mvp), AIs that are sufficiently aligned/controlled to aid research, may remain a crucial part of AI safety research during an AI pause or slowdown. Currently, the best AIs would arguably be unusable for safety research without the hard work of frontier AI company post-training and safety teams. If AI safety researchers quit frontier AI companies en masse, we might be stuck using current generation AIs for the duration of an AI pause; maybe this is unideal?
-   **"Safety-stragglers" will cause warning shots anyways:** Most US-based frontier AI companies, like Google DeepMind, Meta, and xAI, scored failing grades on [Guidelight's Control standard](https://guidelight.ai/blog/control-assessment-august-2026#scoring-chart). Apparently, xAI has only two staff working on frontier AI safety and Meta is not much better off. Chinese AI companies like DeepSeek, Moonshot, Zhipu, etc. might have ~0 frontier safety staff. If leading AI companies are [only a few months ahead](https://epoch.ai/eci?subset-view=graph&subset-tab=Software+engineering&view=graph&tab=release-date&showFrontierTrend=true) of "safety-stragglers", we might see politically expedient warning shots from the least safety-conscious AI companies, regardless of what the leading companies do.
-   **Responses to historical warning shots are high-variance:** The Chernobyl disaster slowed nuclear power adoption worldwide; maybe an AI warning shot would likewise slow AI progress? As a counterexample, consider the atomic bombings of Hiroshima and Nagasaki, which arguably spurred the Cold War nuclear arms race. AI warning shots could actually spur military investment and weaponization of AI! Also, the COVID-19 pandemic, which caused massive loss of life, does not seem to have caused Western society to take pandemic risk seriously.
-   **The purpose of an AI pause is do more safety and resilience work:** Let's say that we pause or slow down frontier AI progress; what then? Arguably, the next step is to solve AGI alignment as fast as possible and improve civilizational resilience with the aid of AI. Absent an staggeringly effective compute monitoring regime (or "burning all the GPUs"), we might eventually have to build aligned AGI to help detect and sabotage blacksite projects. If we curtail the development of new AI safety researchers by discouraging them from working with research mentors at frontier AI companies now, we might have a smaller talent pool to capitalize on an AI pause.
-   **The next warning shot might be lethal:** It's possible that the next OAIxHF-style incident causes loss of life, via bioweapons or cyber attacks on critical systems. If safety researchers quit frontier AI companies now, absent an AI pause, this might enable a catastrophe.
-   **Allowing warning shots "for the greater good" seems morally fraught:** This point speaks for itself. I think that arguments to "allow short-term harm for the greater good" should have to overcome a strong prior against this kind of thinking. Letting people get hurt seems bad, particularly if there is significant uncertainty about whether it is necessary.

Overall, I am cautiously optimistic about working on certain types of safety research at frontier AI companies, particularly if a coordinated AI slowdown (e.g., Plan A) occurs. I nevertheless feel highly uncertain about the "Alignment MVP" strategy in light of recent containment failures and alignment results. I think this merits serious consideration.

---

Addendum: I won't rehash the extensive debate over whether AI "safety" researchers working at frontier AI companies are causing harm via other channels, such as:

-   Making AI systems more deployable by reducing hate speech, jailbreaks, or trivial misalignment, thus increasing AI company revenue and driving AI investment and capabilities progress. (E.g., this argument is most commonly leveled against RLHF, but has also more recently been applied to AI control and scalable oversight research as these have become relevant to commercial deployments.)
-   Contributing to "safetywashing" by creating the appearance that AI companies are doing a lot of safety work, when this work will not usefully contribute to AGI alignment (much debate here, especially post-emergent misalignment).
-   Creating Alignment MVPs that are good at all kinds of frontier AI research, which then differentially accelerate AI capabilities more than the intended safety properties due to AI company leadership decisions. (Note that there is reasonable debate over whether near-term corrigible AGI would be net-good for civilizational resilience or concentration of power.)
-   Otherwise "legitimizing" AI companies pushing the capabilities frontier.

These are legitimate concerns, but largely irrelevant to the topic of this post.

---

Disclosure: I'm the CEO of [MATS](https://www.matsprogram.org/), which trains AI safety researchers, including with mentors at frontier AI companies, and a [meaningful fraction](https://www.lesswrong.com/posts/tPjAgWpsQrveFECWP/ryan-kidd-s-shortform?commentId=6dwq7qkszz5dyZ6sj) of our alumni end up working at those companies. If the argument I'm responding to is right, a good chunk of what MATS has done might be counterproductive, so I have an obvious incentive to find it wrong. I've tried to steelman it anyway and I'd appreciate feedback.
