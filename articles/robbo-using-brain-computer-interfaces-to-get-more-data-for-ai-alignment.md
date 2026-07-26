---
title: "Using Brain-Computer Interfaces to get more data for AI alignment"
author:
  - "Robbo"
source_url: "https://www.lesswrong.com/posts/iWv6Pu2fWPKqevzFE/using-brain-computer-interfaces-to-get-more-data-for-ai"
published: 2021-11-07
created: 2026-07-09
accessed: 2026-07-09
description: "The purpose of this post is to sketch some ways that Brain Computer Interface (BCI) technology might help with various AI alignment techniques. Rough…"
tags:
  - "article-importer"
---{++{"author":"Luc's AI","timestamp":1785090684598}@@

%%
Add discussion note here:

...

%%++}

The purpose of this post is to sketch some ways that [Brain Computer Interface](https://www.lesswrong.com/w/brain-computer-interfaces) (BCI) technology might help with [various AI alignment techniques](https://www.lesswrong.com/posts/fRsjBseRuvRhMPPE5/an-overview-of-11-proposals-for-building-safe-advanced-ai). Roughly, we can divide the strategic relevance of BCI technology into three broad categories.[^1]

1.  _Enhancement._ BCI technology could enhance human intelligence - for example by providing new sensory modalities, or augmenting cognition. [^2]
    
2.  _Merge._ BCI technology could enable a “merge” between AIs and humans. This is advocated by among others, Sam Altman and Elon Musk, and is the stated raison d'etre of Neuralink:
    

> “I think if we can effectively merge with AI by improving the neural link between your cortex and your digital extension of yourself, which already...exists, just has a bandwidth issue. And then effectively you become an AI-human symbiote. And if that then is widespread, with anyone who wants it can have it, then we solve the control problem as well, we don't have to worry about some evil dictator AI because we are the AI collectively. That seems like the best outcome I can think of.” -Elon Musk, interview with Y Combinator ([2016](https://www.ycombinator.com/library/6W-elon-musk-on-how-to-build-the-future)) [^3]

-   On these proposals, humans are not merely enhanced - in some radical sense, humans merge with AI. It’s not entirely clear what these “merge” proposals mean, what merging would look like ([Niplav](https://www.lesswrong.com/posts/rpRsksjrBXEDJuHHy/brain-computer-interfaces-and-ai-alignment): “It seems worrying that a complete company has been built on a vision that has no clearly articulated path to success.”), and "merge" as a alignment strategy seems to be [quite](https://twitter.com/robbensinger/status/1405878940149944332) [unpopular](https://forum.effectivealtruism.org/posts/qfDeCGxBTFhJANAWm/a-new-x-risk-factor-brain-computer-interfaces-1?commentId=EQfXPeTxgHDeMnhEe) in the AI safety community. In future work, I’d like to clarify merge proposals more.

3.  _Alignment aid._ BCI allows us to get data from the brain that could improve the effectiveness of various AI alignment techniques. Whereas _enhancement_ would indirectly help alignment by making alignment researchers smarter, _alignment aid_ proposals are about directly improving the techniques themselves.

This post is about category 3. In conversation, several AI safety researchers have mentioned that BCI could help with AI alignment by giving us more data or better data. The purpose of this post is to sketch a few ways that this could go, and prompt further scrutiny of these ideas.

**1\. Types of Brain Computer Interfaces**

Various technologies fall under the term “brain computer interface”. The commonality is that they record neural activity and transmit information to a computer for further use -- e.g., controlling an electronic device, moving a prosthetic arm, or playing pong. In April 2021 a prominent the Neuralink [demo](https://neuralink.com/blog/monkey-mindpong/), showed a macaque monkey playing 'mind pong' using “a 1,024 electrode fully-implanted neural recording and \[Bluetooth!\] data transmission device”.

Some BCIs only “read” neural signals and use them, as in the ‘mind pong’ demo, while other BCIs also involve “writing” to the brain. While both reading and writing would be necessary for enhancement and merge, I will assume in this post that “reading” capabilities alone would be needed for the alignment aid proposals.

In assessing the state of BCI technology, we can look at three main criteria:

-   Invasiveness: do we have to (e.g.) drill a hole in someone’s skull, or not?
-   Resolution: how fine-grained is the data, both temporally and spatially?
-   Scale: how much of the brain can we record from?

Different kinds of BCI, each with different ways of being relevant to AI, score differently on these measures. Non-invasive techniques techniques are, as you would imagine, more common, and it is non-invasive techniques that are used in current commercial applications. From “Progress in Brain Computer Interface: Challenges and Opportunities” ([2021](https://www.frontiersin.org/articles/10.3389/fnsys.2021.578875/full)):

> Non-invasive BCI exploiting EEG are most common, although more recently, functional near infrared spectroscopy (fNIRS) ([Matthews et al., 2007](https://www.frontiersin.org/articles/10.3389/fnsys.2021.578875/full#B145)), magnetoencephalography (MEG) ([Fukuma et al., 2016](https://www.frontiersin.org/articles/10.3389/fnsys.2021.578875/full#B66)), functional magnetic resonance imaging (fMRI) ([Kaas et al., 2019](https://www.frontiersin.org/articles/10.3389/fnsys.2021.578875/full#B107)) and functional transcranial Doppler ultrasonography ([Faress and Chau, 2013](https://www.frontiersin.org/articles/10.3389/fnsys.2021.578875/full#B60); [Lu et al., 2015](https://www.frontiersin.org/articles/10.3389/fnsys.2021.578875/full#B133); [Khalaf et al., 2019](https://www.frontiersin.org/articles/10.3389/fnsys.2021.578875/full#B115)) have been exploited.

Kernel, one of the most prominent BCI companies, has two products using non-invasive techniques: [Kernel Flow](https://www.kernel.com/flow) which uses functional near infrared spectroscopy fNIRS (see [here](https://www.youtube.com/watch?v=Zs_g4YkTYYM) for a demo), and [Kernel Flux](https://www.kernel.com/flux) which uses MEG. The resolution of non-invasive techniques is limited by hard physical constraints in, given the fundamental difficulty of listening in on individual neurons when there is scalp, fat, and skull in the way. With current technology, invasive techniques are necessary for recording from individual neurons:

> In contrast, invasive intracortical electrodes (Pandarinath et al., 2017) and electrocorticography (ECoG) (Kaiju et al., 2017) have been used, providing a superior signal-to-noise ratio and better localization of brain activity.

But of course invasiveness comes with a variety of problems of its own: greater cost and risk, and the body's eventual rejection of implanted devices.

It seems that for significant human augmentation or for “merge”-like scenarios, we would not just improvements of current methods, but breakthroughs in implantation techniques and materials.[^4] Alignment aid proposals, in contrast, might be possible with currently available non-invasive BCI. That said, I’m not at all clear on what levels of scale and resolution are necessary for these alignment proposals to be feasible, or how their usefulness would scale with resolution.

**2\. BCI for alignment**

_Most of these alignment aid ideas come from conversation with Evan Hubinger. Errors or unclarity are from my transmission._

**High-level picture**

A key component of various AI alignment proposals is teaching AIs something about humans: how humans think, or why we do the things we do, or what we value. AIs have a limited amount of data from which to learn these things. BCI technology might improve the _quantity_ and _quality_ of data available for learning.

Quantity: AI models will need a ton of data to effectively learn. And the amount of information that one can extract from, e.g., reading sentences that a human is generating, is a lot lower than the amount of information one could extract if one also had information about what's happening inside that human’s brain.

Quality: if training data includes detailed information about how humans think, then we can train models not just to output the same sentences that a human would, but to _think_ about those sentences like a human would. (A perennial worry is that we will train models that don't _think_ in the ways that humans do, but instead latch onto inhuman concepts.) But having data which comes directly from human brains could help us train models to think in a more human-like way.

So at a very high level: BCI might give us more training data and better training data for working with humans. A person sitting in a room for 30 minutes answering questions on a computer, would generate far more data with a BCI.

(Question from Evan Hubinger: “You can probably estimate empirically, or with careful Fermi estimation: in 30 minutes of a person with some BCI attached to them, how much meaningful data (excluding noise) do they produce compared to a person who's just typing at a keyboard? What is the actual informational entropy of this data?”)

**Intersection with AI alignment techniques:**

**a. Imitative amplification**

Instead of training models to [imitate](https://www.lesswrong.com/posts/fRsjBseRuvRhMPPE5/an-overview-of-11-proposals-for-building-safe-advanced-ai#2__Imitative_amplification___intermittent_oversight) human language, one could train them to imitate language _plus_ (some subset of) the outputs of the BCI. (Imitating _all_ of the outputs of a BCI might be too difficult, and unnecessary.) Alternatively, one could give BCI outputs to the model, while having the task be to imitate only the sentences. (Hubinger: “This second alternative is a little bit tricky because this is not how machine learning is usually set up, so you'd have to think a little bit about how to get the BCI output information to the model”).

**b. Approval signals for debate or approval-based amplification**

In either [debate](https://arxiv.org/abs/1805.00899) or [approval-based amplification](https://www.lesswrong.com/posts/fRsjBseRuvRhMPPE5/an-overview-of-11-proposals-for-building-safe-advanced-ai#4__Approval_based_amplification___relaxed_adversarial_training), one could use BCI to get a richer approval signal, a signal that contains more information about how the human thinks and feels. This richer signal could produce a much richer loss function than a binary yes-or-no approval signal could.

At a high level, BCI would give us access to internal data about how the human is reacting to things.

Presumably, one would need to “ground” BCI signals in actual sentiments; one would need to train a model to decode sentiment from BCI signals. And given the complexity and range of human reactions, this might be difficult to implement. It’s an open question whether adding BCI sentiment is significantly better than just having people rate things on a more fine-grained scale from (say) 1 - 10, or than other ways of eliciting fine-grained feedback (see below).

**c. Value learning**

In conversation, the BCI-alignment connection people usually make is to propose using BCI for [value learning](https://www.lesswrong.com/s/4dHMdK5TLN6xcqtyc). The general idea is that information about the brain could help us learn (approximations of) human value functions more effectively than language and behavior alone. The hope is that additional neural information could help constrain the set of possible value functions that could be learned. There might be gains from this additional information, whether [or not](https://nivlab.princeton.edu/publications/case-against-economic-values-brain) it makes sense to think we could “read” the value representations in the brain.

While “value learning” is in some sense the most obvious connection to AI alignment, it's hard to say more about what this proposal would look like, in the absence of detailed ideas about the neuroscience of value representation and the state of art in value learning is. This is one of the key further questions in the final section.

**Other sources of more data besides BCI**

Of course, neural recording is not the only source of additional information about humans. Other examples include: video (and in particular, information about body language and facial expression), pupil dilation, heart rate monitoring, electrodermal activity. AI safety researchers I have spoken are not aware of any work that utilizes these sources - one reason being that there is just that there is so much more to explore using language alone, and this research is both cheaper and prima facie more promising than work incorporating these additional measures.

**3\. Future directions and open questions**

As noted, all of these proposals are very sketchy. To evaluate their plausibility, we need: a clearer picture of the proposal, and a more fine-grained analysis of what level of BCI technology would be needed. Greater knowledge of neuroscience than I have would be helpful here (paging [Steve Byrnes](https://www.lesswrong.com/users/steve2152)).

While there is a lot to be gained from more conceptual clarity, I do suspect that many key questions would only resolve in light of actually trying some experiments. Even with today’s limited BCI technologies, I surmise that we could learn a lot even with toy experiments using non-invasive techniques like fNIRs or EEG. That said, even a toy experiment would be rather expensive given the hardware required.

More generally, I hope this prompts more work on BCI. As Niplav [has recently noted](https://www.lesswrong.com/posts/rpRsksjrBXEDJuHHy/brain-computer-interfaces-and-ai-alignment), writing about BCI in the AI strategy community is mostly cursory and scattered around the Internet.[^5] Even if the AI safety community concludes that BCI technology is not likely to be strategically relevant at all, it would be good to have more clearly articulated reasons for why.[^6]

_Thanks to Evan Hubinger, Anders Sandberg, Steve Byrnes, and Oliver Habryka for discussion. Thanks to Miranda Dixon-Luinenburg and the LessWrong feedback service!_

[^1]: I take this distinction from Borg and Sandberg (unpublished draft), who break down BCI relevance into “enhancement”, “merge”, and “improving our ability to accurately learn human values”. For my third category, I look at using BCI a few different alignment proposal, not just “learning human values”.
[^2]: For intriguing examples of sensory augmentation, see [Thomson et al. (2013](https://www.nature.com/articles/ncomms2497)) on using a neuroprosthesis to allow rats to see otherwise invisible infrared light, and [Schumann and O'Reagan (2017)](https://www.nature.com/articles/srep42197) on a non-invasive method for training a ‘sense’ of magnetic North.
[^3]: More quotes from Musk and Altman: this [tweet](https://twitter.com/elonmusk/status/1281121339584114691?lang=en) by Musk. The essay ["The merge"](https://blog.samaltman.com/the-merge) by Altman: "\[U\]nless we destroy ourselves first, superhuman AI is going to happen, genetic enhancement is going to happen, and brain-machine interfaces are going to happen....The merge can take a lot of forms: We could plug electrodes into our brains, or we could all just become really close friends with a chatbot. But I think a merge is probably our best-case scenario. If two different species both want the same thing and only one can have it—in this case, to be the dominant species on the planet and beyond—they are going to have conflict. We should all want one team where all members care about the well-being of everyone else."
[^4]: Tim Urban’s [Wait But Why article](https://waitbutwhy.com/2017/04/neuralink.html) on Neuralink covers some of the proposed new methods and materials; “Physical principles for scalable neural recording” ([2014](https://www.frontiersin.org/articles/10.3389/fncom.2013.00137/full)) maps out the fundamental physical constraints facing neural recording technology.
[^5]: The most extensive treatment of BCI in the AI safety literature is when Bostrom is pessimistic that BCI-enhanced humans would be competitive with “pure” AI in _Superintelligence_, ch. 2. These arguments do not directly apply to using BCI as an alignment aid.
[^6]: Some further BCI research projects that could be useful: further evaluating the ‘enhancement’ and ‘merge’ proposals; a picture of the BCI landscape: the state of the art, current actors, amount of funding; forecasting future BCI capabilities; other ways BCI could be strategically relevant for AI: ‘mind-reading’, advancing neuroscience research (including consciousness research), political impacts.
