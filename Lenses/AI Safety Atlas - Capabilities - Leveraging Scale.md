---
id: aa2bafd1-8c49-4f6e-bfe3-f0f85a5ba36e
tldr: "Why did AI suddenly get good? The 'bitter lesson': raw computation beats decades of hand-coded human expertise, every time. This section unpacks scaling laws, the debate over whether scale alone reaches transformative AI, and why labs are betting hundreds of millions on 'just make it bigger.'"
summary_for_tutor: "Explains scale as the primary driver of recent AI capability gains. Covers Sutton's bitter lesson (general methods leveraging computation beat human-engineered domain knowledge), scaling laws (empirical relationships between compute, parameters, data, and accuracy, including Kaplan and Chinchilla results and Broken Neural Scaling Laws), and the competing scaling hypotheses: strong (scale alone suffices for transformative AI), weak (scale plus targeted algorithmic improvements), and scale-plus-tools or unhobbling (scaffolding, tool use, inference-time compute). Notes skeptics who favor non-transformer architectures, and that major labs are nonetheless betting heavily on scaling."
reading_minutes: 20
tutor_minutes: {--{"author":"Elias's AI","timestamp":1787562836595}@@0--}{++{"author":"Elias's AI","timestamp":1787562836595}@@7++}
title: "Leveraging Scale"
---

#### Article
source:: [[../articles/AI Safety Atlas - Capabilities - Leveraging Scale|Leveraging Scale]]{++{"author":"Elias's AI","timestamp":1787563996748}@@

#### Question: Open
id:: 7d2c8384-b9cc-4928-813e-208456e40a83
optional:: true
content::
The section puts 60 to 95 percent of gains on compute and data and 5 to 40 percent on algorithms, then says the split is hard to make at all, because the algorithms that win are the ones that use scale well.

If the two are that entangled, what is the number still good for?
feedback-instructions::
The learner has just read the AI Safety Atlas section "Leveraging Scale" and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right.

TLDR of what they read:
Scale is presented as the main driver of recent progress. Sutton's bitter lesson: general methods that leverage computation beat hand-encoded human domain knowledge, repeatedly, though the section is careful that this does not mean algorithmic innovation stopped mattering, since the algorithms that win are the ones that use scale well. Scaling laws are empirically observed relationships between compute, parameters, data and accuracy, not laws of nature, and Hoffmann et al. found that optimal training needs roughly 20 tokens of data per parameter, about ten times more than the earlier laws implied, meaning previous large models were undertrained for their size (the body does not use the word Chinchilla; it appears only in a footnote). Three positions are laid out: strong scaling, weak scaling, and scale plus tools, where scaffolding, tool use and inference-time compute sit outside what scaling laws predict. Reported attribution puts 60 to 95 percent of recent gains on compute and data and 5 to 40 percent on algorithms, with acknowledged uncertainty in separating the two.

Take what they wrote seriously and push on it once. Useful directions: what a wide attribution range is still useful for, and what it cannot support; what would have to be true for the 5 to 40 percent figure to be badly wrong; what scaling laws necessarily miss, given they describe a single model trained in a standard way; whether the entanglement is a measurement problem or a real feature of how progress happens.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

Do not preview the later sections in detail. The forecasting section has its own pre-question and this chapter returns to it. Do not give timelines or an arrival date of your own, even if asked, and if the learner volunteers a date or a horizon, do not evaluate it, extend it, or ask them to justify it.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.++}

