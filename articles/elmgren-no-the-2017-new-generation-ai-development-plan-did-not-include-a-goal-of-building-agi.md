---
title: "No, the 2017 New Generation AI Development Plan did not include a goal of building AGI"
author:
  - "Karson Elmgren"
source_url: "https://substack.com/home/post/p-186039653"
published: 2026-03-10
created: 2026-07-02
accessed: 2026-07-02
description: "Clarifying an important historical detail"
tags:
  - "article-importer"
---{++{"author":"Luc's AI","timestamp":1785090645731}@@

%%
Add discussion note here:

...

%%++}

A foundational document in Chinese AI policy is the 2017 New Generation AI Development Plan (NGAIDP). Although almost ten years old now, it still rightly gets attention as essentially the starting point of CCP thinking on AI in the deep learning era. It came after a dual Sputnik moment for China in 2016, the year that AlphaGo handily beat South Korean Go champion Lee Sedol, and the Obama administration (remember them?) published a national [AI plan](https://obamawhitehouse.archives.gov/sites/default/files/whitehouse_files/microsites/ostp/NSTC/preparing_for_the_future_of_ai.pdf) for the US.

Unfortunately, one of the key ways the NGAIDP continues to be [referenced](https://jamestown.org/agi-has-quietly-become-central-to-beijings-ai-strategy/) is as support for the idea that the Chinese leadership has had a long-standing goal of developing AGI, which the document does not clearly provide evidence for. In this post, I will explain why **this interpretation of the original Chinese is problematic at best, and most likely mistaken**. (One section involves getting quite into the weeds of Chinese grammar/stylistics — I’ve marked this one “optional,” as if you are actually required to read the other sections, which of course you are not.)

## Why do people think this at all?

First, the positive case. If you Google Translate “artificial general intelligence” into Chinese, it will give you the characters 通用人工智能 (in pinyin, _tōngyòng réngōngzhìnéng_).[^1] If you ctrl+f for those characters in the NGAIDP, you will get one hit.

It’s a very simple logic:

1.  The NGAIDP lists China’s scientific and technological goals in AI.
    
2.  The characters 通用人工智能 (_tōngyòng réngōngzhìnéng_) appear in the NGAIDP.
    
3.  Therefore, “AGI” is one of China’s scientific and technological goals in AI.
    

QED.

## Why might this be mistaken?

There are several problems with this argument. The context does not support the idea that the phrase represents an ambition to build AGI. The characters _tōngyòng réngōngzhìnéng_ are inherently ambiguous, but usually do not refer to AGI specifically. It’s even possible that _tōngyòng_ and _réngōngzhìnéng_ appeared next to each other here almost coincidentally, rather than as the intentional use of a distinct term of art. Finally, follow-up documents on the implementation of the NGAIDP don’t mention this phrase at all, so to the extent this was a goal, the ball seems to have immediately been dropped.

## The context

The phrase in which these characters appear in the NGAIDP is “data-driven general-purpose AI mathematical models and theory” (数据驱动的通用人工智能数学模型与理论). English and Chinese grammar differ less than you might expect, and fortunately this is a case where the two line up perfectly, such that the English translation is a direct gloss of the Chinese, with every single word in the same order.[^2]

[

![](https://substackcdn.com/image/fetch/$s_!dUjZ!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F9a4ee572-5e5c-4216-9511-5c6c09710e0d_1024x447.png)

](https://substackcdn.com/image/fetch/$s_!dUjZ!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F9a4ee572-5e5c-4216-9511-5c6c09710e0d_1024x447.png)

Where in the document is this phrase found? It’s not exactly buried, but it is far from prominent.

Section I is preamble; Section II discusses general principles and “Strategic Objectives.” The phrase in question comes in Section III, “Focus Tasks,” which lays out 6 broad ambitions of building an innovation ecosystem, integrating AI in the economy, military and government, building infrastructure for AI, and planning major projects, under the first item “Build open and coordinated AI science and technology innovation systems.”

The first listed task for building these innovation systems is to “Establish basic theory systems for a new generation of AI.” Some of the “Focus Tasks” include boxes that presumably are meant to illustrate specific projects or topics that the task will deal in. Under the “basic theory systems” task, there is a box titled “Basic theory,” the first item in which is “Big data intelligence theory.”

We are now quite deep into a tributary of the document — but we’ve not arrived just yet! “Big data intelligence theory” includes a list of about 5 broad areas of research (followed by an “etc.” for good measure). The _very last one_, finally, is our subject today: “data-driven general-purpose AI mathematical models and theory.”

![](https://substackcdn.com/image/fetch/$s_!Omrc!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5ca06010-aa9a-43ea-8c29-87b976a09ea3_1024x495.png)

Simplified, partial diagram — the document continues on to describes 6 Focus Tasks in total and includes three more top-level sections.

## The phrase refers to scientific theory, not an engineered system

The first problem is that the context and wording of the phrase clearly refer to scientific theory, not an implemented, functioning technical system, i.e. papers rather than an app ready to be deployed. The most natural interpretation is that it refers to things like, for instance, the transformer architecture or scaling laws.

The phrase, again, is “data-driven general-purpose AI mathematical models and theory.” What we are talking about here is some particular kind of “mathematical models” and “theory.”

“Theory” is clear enough. “Mathematical models” is more confusing in that “model” can in principle refer to anything from a scientific framework of a relatively high level of abstraction, to a specific, trained machine learning model that serves as a component in an applied technological product. However, “mathematical model” is not a phrase that is typically used to refer to machine learning models. In fact, the modifier “mathematical” is some evidence that the authors intend to refer to frameworks or architectures rather than to trained machine learning models. It simply doesn’t make much sense to specify that a machine learning model be “mathematical” — any software running on a computer is inherently “mathematical.” On the other hand, the specification does make sense to distinguish quantified frameworks or theories implementable in code, that can be run on real-world data, from conceptual models that could be as simple as a box-and-arrows diagram accompanied by some paragraphs of verbal description. To illustrate, I might say that I have a “model” of human cognition which encompasses a perception module, a motor control module, a memory module, a planning module and so on, and which includes qualitative description of how I imagine the parts operate and interact, for example that the planning module combines information from the perception and memory modules and sends signals to the motor control module. This conceptual model would be a theoretical improvement over viewing human cognition as one big undifferentiated mess, and could help to generate testable hypotheses, but without further work it could not be implemented in code and would not generate quantitative predictions about cognitive activity.

What are some concrete examples of things this phrase might be referring to? What exactly might a Party bureaucrat bring to their boss to show that they had made great contributions to this specific sub-component of one of the NGAIDP “Focus Tasks?” One obvious candidate would be something like the transformer architecture. Published by Google researchers \[the same year as the NGAIDP\], the transformer has proved to be a shockingly effective, general-purpose architecture for almost any machine learning task with enough data to throw at it, and underlies the LLM systems currently driving the AI industry. Another might be scaling laws, a theoretical development that helps to compute how to most efficiently train machine learning models with massive amounts of data and compute. Again, a natural fit.

Whenever AGI is created (assuming that is a possible goal at all), it may very well use transformers as part of its architecture, and its training may be planned with reference to scaling laws. But the transformers and the scaling laws themselves do not constitute AGI. When people claim that the NGAIDP includes a goal of developing AGI, they are imagining it means _actually building a functional system that qualifies as AGI_, not just producing some theoretical or basic science results. Even if you believe that this phrase is referring specifically to AGI, at most it describes a goal of producing science that would help enable the creation of AGI, not aiming directly at the finished product. And there are good reasons to doubt it refers to AGI anyways.

## “Tōngyòng réngōngzhìnéng” ≠ AGI

The even more glaring issue is that _tōngyòng réngōngzhìnéng_ does not have a clean 1-to-1 correspondence with “AGI.” The direct translation of the term, as noted above, is “general-purpose artificial intelligence.”

In English, these two concepts are quite clearly different — it’s not very controversial that existing LLM-based systems are more or less general-purpose, but much more controversial that any might be AGI. The EU AI Act’s regulation of general-purpose AI, too, is clearly not regulation of AGI. In more informal writing and speech in Chinese, people will often simply use the English acronym “AGI” to refer to that concept specifically.

In Chinese, it is more muddled. It’s true that the term _tōngyòng réngōngzhìnéng_ is often used to translate “AGI.” In formal contexts, and especially Party or government documents, using an English-language acronym would be a clear violation of the exigencies of “ [cultural self-confidence](https://en.wikipedia.org/wiki/Four_Confidences),” so if AGI were mentioned in a document like the NGAIDP, it would indeed probably appear as _tōngyòng réngōngzhìnéng_.

However, the term is much more frequently used in contexts where it clearly does not refer to AGI — for example, a national [competition](https://web.archive.org/web/20251218015356/https://www.stdaily.com/web/gdxw/2025-12/17/content_448711.html) just a few weeks ago explored applications of “general-purpose AI” (_tōngyòng réngōngzhìnéng_) in the biomedical, cultural/tourism, energy security, robotics, industrial/manufacturing and metaverse fields. Presumably, no one thinks the LLMs and other systems contestants were meant to integrate into, [for example](https://web.archive.org/web/20251018141207/http://bisai.172xiaoyuan.com/chuangyedasai/10842.html), tourist site management and energy equipment diagnostics are AGI. In general, it has been somewhat conflated with LLMs, likely as a result of the fact that the ChatGPT wave brought into the global public consciousness a frenzied mess of discussion of LLMs, AGI, and whether then-current LLMs were already AGI, or imminently about to be, or something, all at the same time. A [2024 document](https://web.archive.org/web/20260127231505/https://www.gdppnet.com/details/31144.html) from the Guangdong province government characteristically refers to “large models and generative AI” as representative of the category of _tōngyòng réngōngzhìnéng_ that had become prominent since the launch of ChatGPT.

Gao Wen, the director of Shenzhen-based Peng Cheng Laboratory and a prominent figure in the Chinese AI ecosystem, [noted](https://web.archive.org/web/20240224073611/https://www.pcl.ac.cn/html/943/2023-12-30/content-4361.html) the inconvenience of this ambiguity in 2023, and suggested modifying the Chinese terminology in a way that would mirror English by distinguishing “general(-purpose) AI” (_tōngyòngxìng de réngōngzhìnéng,_ 通用性的人工智能) and “artificial general(-purpose) intelligence” (_réngōng tōngyòng zhìnéng,_ 人工通用智能).

Alas, Gao’s proposal has not caught on, and certainly not retroactively. DigiChina’s [translation](https://digichina.stanford.edu/work/full-translation-chinas-new-generation-artificial-intelligence-development-plan-2017/) of the 2017 document made the somewhat strained choice to translate _tōngyòng_ as “common” (in the sense of “in common use”), perhaps specifically to avoid possibly implying there was some connection to AGI here. That, in my opinion, shades a bit too far into adaptation rather than translation. But I do think the DigiChina translators would have been directionally correct in downplaying the possibility of reading “AGI” into the document.

## (Optional) It’s not clearly using tōngyòng réngōngzhìnéng as a term of art

In fact, it’s not even entirely clear that the appearance of these exact characters together isn’t somewhat coincidental. For reasons I explain below, the presence of the modifier “data-driven” would have made it grammatically and stylistically awkward to write the phrase in a way that would clearly indicate that “general-purpose” was meant to apply to “mathematical models and theories” rather than to “AI.” It probably did not occur to the drafters that this distinction might contribute to technological paranoia years down the line.

When trying to understand any bureaucratic language, it’s useful to imagine how a particular phrase might have come about. Generally, anything you see on the page is the result of a process of suggestions and revisions that represents the stable equilibrium of a thicket of intersecting institutional interests. Often, a relatively simple or straightforward phrase gets a narrower specification, or modified diction, in response to pushback from influential stakeholders. Considering hypothetical simpler versions of a bit of language can thus help elucidate what the text is getting at in spirit, without getting bogged down in the details of the letter.[^3]

The noun phrase in which they appear is long, with a relative clause and several adjectives stacked together. Usually in Chinese, a sequence of multiple modifiers will use a particular particle (_de_ 的, which marks possession or a modifier) after one of them to break up the otherwise-monotonous rhythm. In general, however, it’s only used once in a phrase. In the case at hand, it is used after the term “data-driven,” where it is (more or less) required because this functions as a relative clause. This means it could not be used after “general-purpose,” where it otherwise would have fit quite naturally, and which would have excluded the possibility of interpreting the phrase as “AGI.” [^4]

So, it is entirely possible that an original, simpler version of the phrase unambiguously did not refer to AGI, but then someone decided to clarify that they meant data-driven AI (leave the expert systems in the 80s!), which then coincidentally ended up putting “general purpose” directly next to “AI,” and creating an ambiguity that would take on unexpected significance in the future.

[

![](https://substackcdn.com/image/fetch/$s_!l2T_!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Feff2a246-0bdd-49e2-90e4-4278668396e3_1024x478.png)

](https://substackcdn.com/image/fetch/$s_!l2T_!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Feff2a246-0bdd-49e2-90e4-4278668396e3_1024x478.png)

An analogy in English can perhaps help elucidate. If I say “general-purpose AI hardware,” you’re probably imagining a chip that can be generally used for all kinds of AI purposes, rather than a chip that is specifically designed for running GPAI (whatever that might imply). That is, you read it as “general-purpose \[AI hardware\]” rather than “\[general-purpose AI\] hardware.” What I mean here is that it’s possible that this phrase in the NGAIDP could be analogous to as if the drafters had originally written “general-purpose hardware for AI workloads,” but then ended up rewriting it as “general-purpose AI hardware” because it flowed better — and now a bunch of silly foreigners think they were talking about hardware _specifically_ for GPAI (or, in fact, specifically for AGI).

## No signs of follow-up

If this phrase did represent a significant goal, we would expect to see signs of various actors trying to execute on it. But we don’t. Either it was not a very significant goal, or the party-state did a very poor job of pushing it forward.

For context, Chinese planning generally follows a call-and-response pattern. The central government shines out a bat signal, and every provincial official from the jungles of Yunnan to the wheat fields of the Northeast paints their BYD sedan to look like the Batmobile. National-level plans are followed up by provincial follow-up plans which match particular local affordances to the national goals. For provincial level officials, showing that they are aligned with and effectively executing on national-level directives helps raise their chances of promotion. To a significant extent, the on-the-ground action that implements national-level plans stems directly from these provincial-level plans. But as far I could ascertain, none of the provincial and municipal plans following from the 2017 New Generation AI Development Plan even include the term _tōngyòng réngōngzhìnéng_.[^5] Nor is it found in the central government’s 3-year action plan, which detailed the intended implementation of the NGAIDP over 2018-2020.

I will concede that the mere fact that it is _possible_ to read “AGI” into the NGAIDP could in principle matter in and of itself. If influential readers seeking to align their work with the goals of the document also interpreted it that way, then the NGAIDP could have instantiated a goal of developing AGI in effect if not in intention. But there is little evidence of this. The earliest major development related to the term _tōngyòng réngōngzhìnéng_ is the establishment of the Beijing Institute for General AI (BIGAI) in 2020, whose Chinese name uses the term _tōngyòng réngōngzhìnéng_. But that’s already 3 years after the NGAIDP, and there’s no sign that its establishment directly resulted from the NGAIDP.[^6] Otherwise, in general this term was rarely used until the emergence of ChatGPT in late 2022, when it in practice often came to denote LLMs, as discussed above.[^7]

## This would be a very weird way to signal a goal of developing AGI

Taking a step back, we can turn the logic around as a sniff test. Assume the drafters of the NGAIDP intended to signal a goal to develop AGI. What would we expect that signal to look like? This is clearly an ambitious, moonshot goal. It would probably be a standalone item, likely in a category of “critical applications” or “key goals” or something, maybe accompanied by some brief elaboration of how the goal is defined.

As mentioned above, Section II of the document does in fact specify “Strategic Objectives.” This would have been an obvious place to say: “By 2040, develop AGI.” But the document does not say that. Those pesky characters _tōngyòng réngōngzhìnéng_ do not show up in this section at all. To the extent AGI (or more precisely, AGI-relevant machine learning theory) is a goal in the NGAIDP, it is definitively not a “Strategic Objective,” but rather one of dozens of minor goals at the same level of priority as “basic statistical learning theories” and “cognitive quantum models and intrinsic mechanisms” (both from the same “Basic Theory” box).

## Conclusion

So, the NGAIDP seems to use a term that has since taken on the sense of “AGI” as one of its meanings. There remains some irreducible uncertainty that, yes, perhaps at least one person involved with the drafting of this document did intend that meaning at the time — we’ll have to wait for the memoirs, I guess, if they are ever forthcoming. But based on the context of the document, the usage of the time, and clues from grammar, this should be viewed as what it is: a hot take, just barely worth taking seriously.

So how _should_ we interpret this little detail? We can confidently say that, among many other goals, one of the aims of the 2017 NGAIDP was to promote broadly-applicable basic science in data-driven machine learning. Perhaps new architectures, or theoretical discoveries.[^8] It would be much more surprising if it didn’t — this simply reflects one of the obvious research trends in the field as of 5 years after AlexNet inaugurated the triumphant, ever-expanding reign of deep learning.

Now, if you want to say that China in the mid-2020s has an ambition to develop AGI, that’s a different [debate](https://www.chinatalk.media/p/is-china-agi-pilled).[^9] Much has changed since 2017, especially in the years since the launch of ChatGPT. But in my view, it’s clear enough that the starting date for that alleged ambition is not 2017.

[^1]: Henceforth, I will use the pinyin transliteration for ease of reading for those who don’t know Chinese.
[^2]: The single difference is a particle, _de_ 的, between “data-driven” and “general-purpose.” This particle specifies that what comes before it modifies what comes after it. More on this particle later… Note also that Chinese has no grammatical plural, so it could be either “theory” or “theories,” but this distinction does not seem important.
[^3]: And considering the direction in which the final text differs from a naive, simple version can give you a sense for the concerns of the stakeholders involved in the drafting.
[^4]: I should note that this is properly more a matter of style than grammar per se. There are various versions that are technically grammatically possible, but might sound and/or look awkward in one way or another. For example, a comma could potentially have been used between “data-driven” and “general-purpose,” and the particle 的 after that, but this would have been somewhat awkward in breaking up just one of the phrases in a list where otherwise items are separated by commas.
[^5]: Not all of the plans published around the time of the NGAIDP are currently available online. However, of those that are, including those from Beijing, Shanghai, Zhejiang, Jiangsu, and Guangdong, none mentions “ _tōngyòng réngōngzhìnéng_.”
[^6]: This is beside the fact that its research agenda is not widely considered a leading contender to develop AGI.
[^7]: Historical data from Baidu and WeChat were unfortunately not available. [Google Books](https://books.google.com/ngrams/graph?content=%22%E9%80%9A%E7%94%A8%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD%22&year_start=2010&year_end=2022&corpus=zh&smoothing=3) shows small usage starting in 2014, but only growing very slowly in the period of 2016-2019. [Google Trends](https://trends.google.com/explore?q=%2522%25E9%2580%259A%25E7%2594%25A8%25E4%25BA%25BA%25E5%25B7%25A5%25E6%2599%25BA%25E8%2583%25BD%2522&date=2019-01-01%202026-01-01&geo=Worldwide) shows negligible usage prior to 2023.
[^8]: It’s worth noting, incidentally, that China does not obviously seem to have succeeded at this goal — notable Chinese contributions since 2017 have clustered much more in the realm of fast-following US developments, and engineering optimizations such as DeepSeek’s Multi-head Latent Attention.
[^9]: Which hinges critically on, among other things, what you mean by “China.”
