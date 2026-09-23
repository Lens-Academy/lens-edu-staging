---
title: "Anthropic’s “Hot Mess” paper overstates its case (and the blog post is worse)"
author:
  - "RobertM"
source_url: "https://www.lesswrong.com/posts/ceEgAEXcL7cC2Ddiy/anthropic-s-hot-mess-paper-overstates-its-case-and-the-blog"
published: 2026-02-04
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Author's note: this is somewhat more rushed than ideal, but I think getting this out sooner is pretty important. Ideally, it would be a bit less snar…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Author's note: this is somewhat more rushed than ideal, but I think getting this out sooner is pretty important. Ideally, it would be a bit less snarky. I've made a few edits in response to David Johnston's comment_ [_here_](https://www.lesswrong.com/posts/ceEgAEXcL7cC2Ddiy/anthropic-s-hot-mess-paper-overstates-its-case-and-the-blog?commentId=nAxFiz6DHGggBA7f8)_, mostly about the paper's reporting of its own results._

Anthropic[^note-1] recently published a new piece of research: [The Hot Mess of AI: How Does Misalignment Scale with Model Intelligence and Task Complexity?](https://alignment.anthropic.com/2026/hot-mess-of-ai/) ([arXiv](https://arxiv.org/abs/2601.23045), [Twitter thread](https://x.com/AnthropicAI/status/2018481220741689581)).

I have some complaints about both the paper and the accompanying blog post.

## tl;dr ^tl-dr

-   The paper's technical definition of "incoherence" is uninteresting[^note-2] and the framing of the paper, blog post, and Twitter thread equivocate with the more normal English-language definition of the term, which is extremely misleading.
-   The paper's abstract says that "in several settings, larger, more capable models are more incoherent than smaller models", which is technically true, but the results are mixed at best (leaning against). I think the way this is described in the accompanying blog post and Twitter thread is pretty misleading. I also think the abstract of the paper relies on the equivocation above to drive its conclusion.
-   Section 5 of the paper (and to a larger extent the blog post and Twitter) attempt to draw conclusions about future alignment difficulties that are unjustified by the experiment results, and would be unjustified even if the experiment results pointed in the other direction.
-   The blog post is substantially LLM-written. I think this contributed to many of its overstatements. I have no explanation for the Twitter thread.

# Paper ^paper

The paper's abstract says:

> Incoherence changes with model scale in a way that is experiment-dependent. However, in several settings, larger, more capable models are more incoherent than smaller models. Consequently, scale alone seems unlikely to eliminate incoherence.

This is a selective emphasis of the results, where in most experiments, model coherence remained unchanged or increased with size. There are a few[^note-3] obvious exceptions.

The first is the Synthetic Optimizer setting, where they trained "models to literally mimic the trajectory of a hand-coded optimizer descending a loss function". They say:

> All models show consistently rising incoherence per step; interestingly, smaller models reach a lower plateau after a tipping point where they can no longer follow the correct trajectory and stagnate, reducing variance. This pattern also appears in individual bias and variance curves (Fig. 26). Importantly, larger models reduce bias more than variance. These results suggest that they learn the correct objective faster than the ability to maintain long coherent action sequences.

But bias stemming from a lack of ability is not the same as bias stemming from a lack of propensity. The smaller models here are clearly not misaligned in the propensity sense, which is the conceptual link the paper tries to establish in the description of Figure 1 to motivate its definition of "incoherence":

> AI can fail because it is misaligned, and produces consistent but undesired outcomes, or because it is incoherent, and does not produce consistent outcomes at all. These failures correspond to bias and variance respectively. As we extrapolate risks from AI, it is important to understand whether failures from more capable models performing more complex tasks will be bias or variance dominated. Bias dominated failures will look like model misalignment, while variance dominated failures will resemble industrial accidents.

So I think this result provides approximately no evidence that can be used to extrapolate to superintelligent AIs where misalignment might pose actual risks.

The next two are Gemma3 (1b, 4b, 12b, 27b) on MMLU and GPQA, respectively.

![image.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/v1770101053/lexical_client_uploads/wfdvsvp822a70mwlimva.png)

  

![image.png](https://res.cloudinary.com/lesswrong-2-0/image/upload/v1770101110/lexical_client_uploads/yylpc8ibfknzwzki2ufg.png)

There are some other positive slopes, but frankly they look like noise to me (Qwen3 on both MMLU and GPQA).

Anyways, notice that on four of the five groups of questions, Gemma3's incoherence drops with increasing model size; only on the hardest group of questions does it trend (slightly) upward.

I think that particular headline claim is basically false. But even if it were true, it would be uninteresting, because they define incoherence as "the fraction of model error caused by variance".

Ok, now let's consider a model with variance of 1e-3 and bias of 1e-6. Huge "incoherence"! Am I supposed to be reassured that this model will therefore not coherently pursue goals contrary to my interests? Whence this conclusion? (Similarly, an extremely dumb, broken model which always outputs the same answer regardless of input is extremely "coherent". A rock is also extremely "coherent", by this definition.)

A couple other random complaints:

-   The paper basically assumes away the possibility of deceptive schemers[^cite-4].
-   The paper is a spiritual successor of the 2023 blog post, [The hot mess theory of AI misalignment: More intelligent agents behave less coherently](https://sohl-dickstein.github.io/2023/03/09/coherence.html) ([LW discussion](https://www.lesswrong.com/posts/SQfcNuzPWscEj4X5E/the-hot-mess-theory-of-ai-misalignment-more-intelligent)). I think [gwern's comment](https://www.lesswrong.com/posts/SQfcNuzPWscEj4X5E/the-hot-mess-theory-of-ai-misalignment-more-intelligent?commentId=kqYc3wC4S7nKHQ2br) is a sufficient refutation of the arguments in that blog post. This paper also reports the survey results presented in that blog post alongside the ML experiments, as a separate line of evidence. This is unserious; to the extent that the survey says anything interesting, it says that "coherence" as understood by the survey-takers is unrelated to the ability of various agents to cause harm to other agents.

# Blog ^blog

First of all, the blog post seems to be substantially the output of an LLM. In context, this is not that surprising, but it is annoying to read, and I also think this might have contributed to some of the more significant exaggerations or unjustified inferences.

Let me quibble with a couple sections. First, "Why Should We Expect Incoherence? LLMs as Dynamical Systems":

> A key conceptual point: ****LLMs are dynamical systems, not optimizers.**** When a language model generates text or takes actions, it traces trajectories through a high-dimensional state space. It has to be _trained_ to act as an optimizer, and _trained_ to align with human intent. It's unclear which of these properties will be more robust as we scale.

> Constraining a generic dynamical system to act as a coherent optimizer is extremely difficult. Often the number of constraints required for monotonic progress toward a goal grows exponentially with the dimensionality of the state space. We shouldn't expect AI to act as coherent optimizers without considerable effort, and this difficulty doesn't automatically decrease with scale.

The paper has a similar section, with an even zanier claim:

> The set of dynamical systems that act as optimizers of a fixed loss is measure zero in the space of all dynamical systems.

This seems to me like a vacuous attempt at defining away the possibility of building superintelligence (or perhaps "coherent optimizers"). I will spend no effort on its refutation, Claude 4.5 Opus being capable of doing a credible job:

:::callout {title="Claude Opus 4.5 on the 'measure zero' argument." collapse="closed"}
Yes, optimizers of a fixed loss are measure zero in the space of all dynamical systems. But so is essentially _every_ interesting property. The set of dynamical systems that produce grammatical English is measure zero. The set that can do arithmetic is measure zero. The set that do anything resembling cognition is measure zero. If you took this argument seriously, you'd conclude we shouldn't expect LLMs to produce coherent text at all—which they obviously do.

The implicit reasoning is something like: "We're unlikely to land on an optimizer if we're wandering around the space of dynamical systems." But we're not wandering randomly. We're running a highly directed training process specifically designed to push systems toward useful, goal-directed behavior. The uniform prior over all dynamical systems is the wrong reference class entirely.
:::

The broader (and weaker) argument - that we "shouldn't expect AI to act as coherent optimizers without considerable effort" - might be trivially true. Unfortunately Anthropic (and OpenAI, and Google Deepmind, etc) are putting forth considerable effort to build systems that can reliably solve extremely difficult problems over long time horizons ("coherent optimizers"). The authors also say that we shouldn't "expect this to be easier than training other properties into their dynamics", but there are [reasons to think this is false](https://www.lesswrong.com/posts/RQpNHSiWaXTvDxt6R/coherent-decisions-imply-consistent-utilities), which renders the bare assertion to the contrary kind of strange.

Then there's the "Implications for AI Safety" section:

> Our results are evidence that future AI failures may look more like ****industrial accidents**** than ****coherent pursuit of goals that were not trained for****. (Think: the AI intends to run the nuclear power plant, but gets distracted reading French poetry, and there is a meltdown.) However, coherent pursuit of poorly chosen goals that we trained for remains a problem. Specifically:

> 1\. ****Variance dominates on complex tasks.**** When frontier models fail on difficult problems requiring extended reasoning, there is a tendency for failures to be predominantly incoherent rather than systematic.

> 2\. ****Scale doesn't imply supercoherence.**** Making models larger improves overall accuracy but doesn't reliably reduce incoherence on hard problems.

> 3\. ****This shifts alignment priorities.**** If capable AI is more likely to be a hot mess than a coherent optimizer of the wrong goal, this increases the relative importance of research targeting _reward hacking_ and _goal misspecification_ during training—the bias term—rather than focusing primarily on aligning and constraining a perfect optimizer.

> 4\. ****Unpredictability is still dangerous.**** Incoherent AI isn't safe AI. Industrial accidents can cause serious harm. But the _type_ of risk differs from classic misalignment scenarios, and our mitigations should adapt accordingly.

1 is uninteresting in the context of future superintelligences (unless you're trying to define them out of existence).

2 is actively contradicted by the evidence in the paper, relies on a definition of "incoherence" that could easily classify a fully-human-dominating superintelligence as more "incoherent" than humans, and is attempting to both extrapolate trend lines from experiments on tiny models to superintelligence, and then extrapolate from those trend lines to the underlying cognitive properties of those systems!

3 relies on 2.

4 is slop.

---

I think this paper could have honestly reported a result on incoherence increasing with task length. As it is, I think the surrounding communications misreport the paper's results re: incoherence scaling with model size, the paper itself performs an implicit motte-and-bailey with its definition of "incoherence", and it tries to draw conclusions about the likelihood of future alignment difficulties that would be unjustified by any plausible reading of the experiment results.

[^note-1]: From their Anthropic Fellows program, but published on both their [Alignment blog](https://alignment.anthropic.com/2026/hot-mess-of-ai/) and on their [Twitter](https://x.com/AnthropicAI/status/2018481220741689581).
[^note-2]: Expanded on later in this post.
[^note-3]: One of which is Figure 2a's "MCQ Format: Self-Reported Survival Instinct" with Opus 4 and Sonnet 4, which I'm ignoring because reasoning-length half of the paper isn't the part that I take issue with.
[^cite-4]: Figure 1: "AI can fail because it is misaligned, and produces consistent but undesired outcomes, or because it is incoherent, and does not produce consistent outcomes at all. These failures correspond to bias and variance respectively. As we extrapolate risks from AI, it is important to understand whether failures from more capable models performing more complex tasks will be bias or variance dominated. Bias dominated failures will look like model misalignment, while variance dominated failures will resemble industrial accidents."
