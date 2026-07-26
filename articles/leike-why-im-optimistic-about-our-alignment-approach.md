---
title: "Why I’m optimistic about our alignment approach"
author:
  - "Jan Leike"
source_url: "https://aligned.substack.com/p/alignment-optimism"
published: 2023-02-15
created: 2026-06-21
accessed: 2026-06-21
description: "Some arguments in favor and responses to common objections"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[OpenAI’s approach to alignment research](https://openai.com/blog/our-approach-to-alignment-research/) involves [perfecting RLHF](https://openai.com/blog/instruction-following/), [AI-assisted human evaluation](https://aligned.substack.com/p/ai-assisted-human-feedback), and [automated alignment research](https://aligned.substack.com/p/alignment-mvp). Why is this a good strategy? What are the reasons to be optimistic about it? My optimism stems from five sources:

1.  **Positive updates about AI.** A lot of developments over the last few years have made AI systems more favorable to alignment than they looked initially, both in terms of how the AI tech tree is shaking out and the empirical evidence on alignment we’ve gathered so far.
    
2.  **A more modest goal.** We’re not trying to solve all alignment problems. We’re just trying to align a system that’s capable enough to make more alignment progress than we can.
    
3.  **Evaluation is easier than generation.** This is a very general principle that holds across many domains. It’s true for alignment research as well.
    
4.  **We’re setting ourselves up for iteration.** We can set ourselves up for iterative, measurable improvements on our alignment path.
    
5.  **Conviction in language models.** Language models will be smart enough to get useful alignment research work out of them.
    

Nevertheless, there is still so much to do and it’s critical to remember that aligning systems that are smarter than us will look very different than aligning today’s models. It’s also important to distinguish between optimism and caution: the burden of proof is always on showing that a new system is sufficiently aligned and we cannot shift the burden of proof to showing that the situation has changed compared to earlier systems.

The last section [responds to some common objections to our approach](https://aligned.substack.com/i/88447351/common-objections).

## My reasons for optimism

## 1\. Positive updates about AI

### 1.1 The AI tech tree is looking favorably

A few years ago it looked like the path to AGI was by training deep RL agents from scratch in a wide range of games and multi-agent environments. These agents would be aligned to maximizing simple score functions such as survival and winning games and wouldn’t know much about human values. Aligning the resulting agents would be a lot of effort: not only do we have to create a human-aligned objective function from scratch, we’d likely also need to instill actually new capabilities into the agents like understanding human society, what humans care about, and how humans think.

Large language models (LLMs) make this a lot easier: they come preloaded with a lot of humanity’s knowledge, including detailed knowledge about human preferences and values. Out of the box they aren’t agents who are trying to pursue their own goals in the world and and their objective functions are quite malleable. For example, they are [surprisingly easy to train to behave more nicely](https://openai.com/blog/instruction-following/).

### 1.2 The empirical evidence is looking favorably

Some of the most exciting alignment work from recent years has been empirical: [researchers](https://arxiv.org/abs/2209.14375) [build](https://arxiv.org/abs/2204.05862) [prototypes](https://arxiv.org/abs/2210.11416) of what they think more aligned systems could look like to see how well it would actually work and what the kinks are. This is not meant to diminish conceptual insights, but those are always on shaky ground if they aren’t backed by mathematical theorems or empirical evidence.

-   [Deep RL from human preferences](https://arxiv.org/abs/1706.03741): When starting to work on it, I thought it was reasonably likely that it wouldn't really work. [GANs didn't really work initially](https://arxiv.org/abs/1406.2661) except on very small datasets and took several years and many researchers to figure out the tricks on how to make training stable. Yet RLHF worked pretty well, even on the visually pretty weird Atari games and when using feedback from actual humans. It wasn’t easy to make it work: Dario’s intuitions on tuning were pretty important to making it work on Atari. Training was pretty janky at the time because deep RL generally was and it took a bunch of iterations to get to work. But [it replicated](https://arxiv.org/abs/1811.06521).
    
-   [Summarization from human feedback](https://openai.com/blog/learning-to-summarize-with-human-feedback/): This was really the first convincing proof-of-concept that RLHF works on language models and that you can optimize goals that are fuzzy and somewhat ambiguous. This is important because human values are fuzzy and before this paper, there hadn’t been clear demonstrations at scale of AI systems learning from fuzzy goals. While in theory learning human values shouldn’t actually be fundamentally different from learning to recognize a cat in an image, it’s not clear that optimizing against these fuzzy goals works well in practice.
    
-   [InstructGPT](https://openai.com/blog/instruction-following/) demonstrated that there is a real “alignment overhang” in language models that wasn’t very hard to access. The main result, an effective >100x model size increase on human preference scores is absolutely wild and I would have been super amazed by a “mere” 5x model size increase. The amount of human feedback needed was pretty moderate and achievable: ~50,000 comparisons, and ~300,000 episodes of training. That number is so small that we could actually have humans hand-label every training episode! For the first time, this showed that even a moderate amount of fine-tuning can shift model behavior a lot towards being more aligned on GPT-3-sized models. This is incredibly good news!
    
-   [Self-critiquing models](https://openai.com/blog/critiques/): Helping humans find 50% more flaws that they would have unassisted with a model that isn't superhuman on a task that isn’t hard for humans is a surprisingly strong result, showing that our model can basically already add a lot of value for feedback assistance. This increased my optimism about [recursive reward modeling](https://deepmindsafetyresearch.medium.com/scalable-agent-alignment-via-reward-modeling-bf4ab06dfd84) a lot: meaningfully assisting human evaluation is actually easier than I previously thought. Maybe this is because our human labelers aren’t actually that careful or because models that aren't very smart are still pretty good at noticing random flaws.
    
-   [Discriminator-critique (DC) gap](https://arxiv.org/pdf/2206.05802.pdf#page=12): The DC gap is probably the closest empirical measure we have right now to how well we can [elicit latent knowledge](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit) from our language models. A large DC gap implies that our models know about a bunch of flaws in their response they aren’t telling us when we ask nicely. The DC gap we measured in the critiques paper was surprisingly small, and since then we have struggled to find a clean way to exhibit the problem in toy tasks or on a code dataset we made specifically for this purpose. If eliciting latent knowledge is actually a large problem, why is it so hard to exhibit in today’s models? It seems like they are actually quite good at telling us what’s wrong with what they are doing. Nevertheless, it is worrying that [the DC gap doesn’t shrink with model size](https://arxiv.org/pdf/2206.05802.pdf#page=14).
    

Let’s not get carried away by this evidence. Just because it has been favorable so far, doesn’t mean it will continue to be. AI systems aren’t yet smarter than us, so we’re not facing the real problems yet. But the evidence so far still counts: if we had a substantially harder time aligning current AI systems, we should be more worried about aligning future AI systems. If we can’t win the game on easy mode, we shouldn’t expect to win the game on hard mode. But if we do win on easy mode, we might still fail on hard mode, and we need to be ready to work hard on it.

## 2\. A more modest goal

When thinking about solving alignment, it’s natural to picture trying to find [a once-and-for-all solution](https://aligned.substack.com/p/alignment-solution) to the whole problem. I used to think this way until the rise of LLMs. Finding this once-and-for-all solution could be very difficult, and we don’t really know how to do this. The task seems very daunting and it’s easy to be pessimistic about it.

But that’s not what we humans need to do. Instead, we only need to build a minimal viable product: an [automated alignment researcher](https://aligned.substack.com/p/alignment-mvp) that helps us make more alignment progress faster. For example, if we automate the generation of most alignment work, we can focus its evaluation, [which I claim is a lot easier](https://aligned.substack.com/i/88447351/evaluation-is-easier-than-generation). In other words, on this path we likely don’t have to confront all the hardest challenges of the alignment problem on our own and instead can get AI to help us with them.

This has a bunch of advantages:

1.  **The model doesn’t have to be fully aligned.** It only needs to be sufficiently aligned to help us do this narrow task. It doesn’t have to point out all flaws in a given alignment proposal it knows about (it can have a DC gap), as long as we have some other way to find them. It doesn’t have to be maximally helpful, as long as it’s quite helpful. We have to mistrust what the model is doing anyway and discard it if we can’t rigorously evaluate it.
    
2.  **The model can be “narrower.”** It doesn’t need to understand biology, physics, or human society that well. In practice we’d probably fine-tune from an LLM that does understand all of those things, but we could apply some targeted brain damage to the model as a safety precaution. More generally, the model only has to exceed human-level in a few domains, while it can be worse than humans in most others.
    
3.  **It’s easy to add more safeguards.** The system doesn’t need to be connected to the internet, it doesn’t have to interact with a large number of people, and it doesn’t need to run arbitrary code. These safeguards won’t protect us against a super smart system that wants to break out, but they will contribute to increasing our safety margin for a while.
    
4.  **The model doesn’t need a lot of agency.** The system doesn’t have to set its own goals or pursue goals that span long horizons. We don’t need to supervise it using long-term outcomes in the real world.
    
5.  **The model doesn’t need persistent memory.** We can fine-tune the model on what it needs to know and use a moderately sized context to hold the task-relevant information. We don’t need the model to decide what it should remember.
    
6.  **Alignment taxes don’t matter as much.** Because this system isn’t directly competing with other potentially less aligned systems in a market place, a larger overhead relative to other training methods might not make a big difference, as long as the overall cost for automated alignment research is manageable.
    

Each of these aspects should make our job noticeably easier than actually trying to align a general-purpose digital agent that acts in the world like a CEO.

However, automated alignment research also requires more intense scrutiny on the research product: since this research would presumably inform how the next generation of AI systems is build, it is a path for AI systems to try to gain power over humans. Moreover, succeeding at this goal does not mean that humanity’s work on alignment is done, even if they don’t have the cognitive capabilities anymore to make meaningful intellectual contributions relative to AI.

## 3\. Evaluation is easier than generation

This principle is important because it allows us to easily get meaningful alignment work out of our systems. If it’s true, it means we can substantially accelerate our research if we focus our time and effort on evaluating what our systems are doing instead of doing this work ourselves (even if their generation ability isn’t quite as good as ours).

This property is underlying [recursive reward modeling](https://deepmindsafetyresearch.medium.com/scalable-agent-alignment-via-reward-modeling-bf4ab06dfd84) (and to some extent [debate](https://openai.com/blog/debate/)): If evaluation is easier than generation, assisted humans have an advantage over similarly smart AI generators. As long as this is true, we can scale to harder and harder tasks by creating evaluation (and thus training) signals for AI systems doing those tasks. While recursive reward modeling won’t scale indefinitely, it also don’t need to. It just needs to scale far enough for us to be able to use it to [supervise a lot of alignment research](https://aligned.substack.com/i/88447351/a-more-modest-goal).

_Evaluation is easier than generation_ is a very general property that holds across many domains:

-   **Formal problems.** [Most computer scientists believe that NP!= P](https://en.wikipedia.org/wiki/P_versus_NP_problem#Reasons_to_believe_P_%E2%89%A0_NP_or_P_=_NP), which implies that there is a large class of problems for which this property is formally true. Most of these problems also have been empirically shown to have this property for algorithms we could think of: SAT solving, graph algorithms, proof search, model checking, and so on.
    
-   **Classical sports and games.** Any sport or game that is worth watching has this property. Not only does the audience need to be able to tell who won the game, but also who is ahead and who is making awesome moves or plays. Thus evaluation needs to be easy enough to be done by the vast majority of the audience members. At the same time, generation (playing the game well) needs to be difficult enough that the best humans can easily set themselves apart from the vast majority; otherwise holding a competition would not be very interesting. For example: you can tell who’s ahead in Starcraft by looking at the players’ units and economy; you can tell who’s ahead in DotA by looking at kill/death statistics and gold earned; you can tell who is ahead in chess by looking at material and position (though evaluating position well can be difficult); you can tell who is winning at soccer or football by looking at the scoreboard and whose court most time is spent; and so on.
    
-   **A lot of consumer products:** It’s so much easier to compare the quality of different smartphones than it is to build a better smartphone. This doesn’t just apply to easily measurable characteristics like amount of RAM or number of pixels, but also fuzzier aspects like how nice it is to hold and how long does the battery last. In fact, this is true for most (tech) products and this is why people pay attention to Amazon and YouTube reviews. On the flip side, for products where evaluation is difficult for individual consumers and there are few governmental regulations, the market is often flooded with low quality products. For example, nutritional supplements frequently don’t have the benefits they claim, don’t contain the amount of active ingredients they claim, or contain unhealthy contamination. In this case, evaluation requires having expensive lab equipment, so most people who make the purchasing decisions don’t have a reliable signal; they can only take the supplements and see how they feel.
    
-   **Most jobs:** whenever a company hires an employee, they need to know whether that employee is actually helping them achieve their mission. It wouldn’t be economical to spend as much time and effort on evaluating the job performance of employees as it takes to do their job, so only a much smaller amount of effort could be spent on evaluating job performance. Does it work? I certainly wouldn’t claim that companies get a perfect signal on how well their employees actually perform, but if they couldn’t evaluate more easily than the employee, then efforts like performance improvements, promotions, and firings would be essentially random and a waste of time. Thus companies who don’t put a lot of time and effort into employee performance evaluation should be outcompeting other companies who do.
    
-   **Academic research:** Evaluating academic research is notoriously difficult and governmental funding agencies have few tools to distinguish good from bad research: the decision typically needs to be made by non-experts, lots of low-quality work gets funded, and proxy metrics like citation counts and number of published papers are known to be over-optimized. The [NeurIPS experiment](https://blog.neurips.cc/2021/12/08/the-neurips-2021-consistency-experiment/) famously found a lot of noise in the academic review process, but what is easy to overlook is that there was also a lot of meaningful signal: writing a NeurIPS paper typically takes at least a few months of full-time work (say >1,000h), while a review is typically completed within a few hours (e.g. 4 reviews taking 3h each totals 12h). Yet reviewer committees agree 77% of the time on the accept/reject decision and agree on accepting oral/spotlight-rated papers 94% of the time. This is an incredibly high agreement rate (much higher than on the OpenAI API tasks where labeler-labeler agreement is around 70-80%) given that two orders of magnitude more effort went into generation than evaluation! There is a lot to be said about broken academic incentives and whether NeurIPS papers actually advance humanity’s scientific knowledge, but it seems that the claim is true at least for the task of writing a paper that gets into NeurIPS.
    

Nevertheless, there are also tasks for which this principle is generally not true: It’s easier to write your signature than it is to evaluate whether a given squiggle is your signature. It’s easy to encrypt or hash an image of a dog, but it’s very difficult to evaluate whether some given binary data is an encrypted or hashed picture of a dog. This makes cryptography possible at all.

The evidence above does not imply that the principle is also true for alignment research. But it sure is gesturing very heavily towards this. In other words, if it was much harder to evaluate NeurIPS papers than to write them and reviewers don’t tend to agree above chance level, shouldn’t we count that as evidence against alignment research being easy to automate?

Even more, if it were true that alignment research isn’t easier to evaluate than it is to generate, this is bad news even for purely human-driven alignment research: In this case a human who finds a solution the alignment problem won’t be able to convince others to use that solution because others won’t know whether it’s any good. Instead every AGI developer would need to come up with a solution for themselves.

While any proxy metric for evaluating alignment research can be over-optimized and will result in alignment research that looks compelling but is fundamentally flawed, that doesn’t mean that there won’t be proxy metrics that are still useful to optimize for a while.

However, there is an important caveat: adversarially constructed inputs may be a lot harder to evaluate than non-adversarial ones (though might still be easier to evaluate than to generate). For example, [superhuman go agents have simple exploits](https://arxiv.org/abs/2211.00241). A hypothetical example for alignment research: [it is possible to plant backdoors into models by only controlling the randomness during training](https://arxiv.org/abs/2204.06974). A human evaluator who does not know this will miss an important flaw in training code written by a malicious AI system who is secretly manipulating the randomness source.

Another important open question is how much easier evaluation is if you can’t rely on feedback signals from the real world. For example, is evaluation of a piece of code easier than writing it, even if you’re not allowed to run it? If we’re worried that our AI systems are writing code that might contain trojans and sandbox-breaking code, then we can’t run it to “see what happens” before we’ve reviewed it carefully. In this case, it could be easier to rewrite the code from scratch yourself instead of discovering a hidden flaw (which [Rice’s theorem](https://en.wikipedia.org/wiki/Rice%27s_theorem) suggests isn’t defense-advantaged).

## 4\. We’re setting ourselves up for iteration

One of the problems that conceptual alignment work has is that it’s unclear when progress is being made and by how much. The best proxy is “do other researchers think progress is being made” and that’s pretty flawed: the alignment research community largely disagrees about whether any conceptual piece constitutes real progress.

A lot of problems get a lot more tractable once you’ve set yourself up for iteration: you have (1) a basic system that’s working (even if just barely at first) and (2) a proxy metric that tells you whether or not changes you’re making are improvements. This allows incremental changes to an existing system and a feedback loop that allows you to gain information from reality. In a machine learning analogy, (1) is a model architecture and (2) allows us to calculate gradients; together they allow us to take gradient steps.

In this sense alignment research is very meta: we’re optimizing a metric (2) that measures how well we’re making progress on making metrics (e.g. aligned reward models) that can be optimized (e.g. via RL) to make progress. I won’t dwell on the obvious [goodharting](https://en.wikipedia.org/wiki/Goodhart%27s_law) disclaimer that we can’t optimize any metric we have indefinitely. However, some metrics are useful and we can optimize them for a while before we need a better metric.

While we haven’t yet set ourselves up for iteration on aligning AGI, we’ve managed to set ourselves up successfully for a lot of the smaller problems that lead up to it. Some examples:

-   Training [InstructGPT](https://openai.com/blog/instruction-following/) to maximize human preferences on the OpenAI API prompts and training [ChatGPT](https://openai.com/blog/chatgpt/) to maximize human preferences as a dialog assistant. This allows us to evaluate a lot of different models: we can tune hyperparameters, change the data mix, change training methods (e.g. SFT vs. PPO) and see how well they work. Needless to say, it’s not a perfect metric because it doesn’t capture a bunch of problems well (for example unsafe responses). At some point our models will learn to fool our human evaluators, but it’s been very valuable for improving InstructGPT and ChatGPT.
    
-   Measuring the adversarial robustness of our safety mitigations through [human](https://arxiv.org/abs/2209.07858) and [automated](https://arxiv.org/abs/2202.03286) red-teaming. If it takes more time and effort for humans to cause safety failures, our safety mitigations have improved.
    
-   Using [targeted perturbations to measure how well AI can assist human evaluation](https://arxiv.org/abs/2206.05802): By introducing targeted perturbations to model responses to make them deliberately better or worse, we can measure how well humans can evaluate the two different versions in different settings. If we hold our labelers and the model capabilities constant, we can [experiment with different forms of assistance](https://arxiv.org/abs/2211.03540) and measure how long it takes humans to evaluate and what kind of accuracy they get.
    
-   Training critique models and measuring the [discriminator-critique (DC) gap](https://arxiv.org/pdf/2206.05802.pdf#page=12): if we reduce the DC gap, we are reducing our model’s latent knowledge that we don’t have access to. Since discriminators are trained with supervised learning and SGD, they should be able to find any simple function of the activations to best predict on the discrimination task; it would be very difficult for the model to hide relevant knowledge in this setting.
    
-   We want to train alignment research assistance models and evaluate them on researcher preferences on those models’ completions. Analogously to our InstructGPT and ChatGPT setup, we can use this to measure how much more useful we’re making the model to alignment researchers.
    

A [once-and-for-all solution to alignment will look very different](https://aligned.substack.com/p/alignment-solution) from what we do today and our current metrics definitely won’t be able to track progress all the way there. But they do allow us to make iterative progress towards it, and that’s hugely valuable. The alignment research community disagrees whether these metrics really point in the right direction, but they can verify that we’re making progress on our [shorter-term goals](https://openai.com/blog/our-approach-to-alignment-research/). Over time, our progress will become more apparent and easier to evaluate.

## 5\. Conviction in language models

Language models have gotten a lot smarter over the past 5 years and I expect that they will continue getting smarter over the next few years. I believe that there is nothing inherently special about our own cognitive abilities and at some point language models will be better at any limited-context text-in text-out tasks related to our own work than we are. A lot of alignment work can be phrased in this format and so they are quite well-suited for it. There is a lot more to be said about this topic, but this is not the place for it.

## Common objections

I’m optimistic that we can produce progress that will end up convincing others of the merit of [our approach](https://openai.com/blog/our-approach-to-alignment-research/). Would it count if our automated alignment researcher writes papers on [embedded agency](https://arxiv.org/abs/1902.09469) that researchers working on this problem consider real progress on that agenda? What if language models produce novel interpretability insights that prove useful when understanding transformers? If we fundamentally distrust any alignment research produced by AI, we are potentially foreclosing ourselves to a big opportunity for progress.

Below I respond to specific objections that have been raised to our strategy.

## Recursive reward modeling doesn’t work

A quick clarification on terminology: Some people consider recursive reward modeling (RRM) an instance of [iterated amplification](https://openai.com/blog/amplifying-ai-training/) (with amplification = using an AI assistant, and distillation = RLHF). However, most people seem to understand iterated amplification in a more narrow sense with imitating learning, which is a different algorithm from recursive reward modeling and suffers from different drawbacks (for example it doesn’t take advantage of the principle that [evaluation is easier than generation](https://aligned.substack.com/i/88447351/evaluation-is-easier-than-generation)). Objections against iterated amplification are often phrased for the imitation learning version (i.e. [factored cognition](https://ought.org/research/factored-cognition)) or [debate](https://openai.com/blog/debate/), but I attempt to re-cast them for RRM here.

### Obfuscated arguments

The first version of this objection comes from interpretations of the [obfuscated arguments problem](https://www.alignmentforum.org/posts/PJLABqQ962hZEqhdB/debate-update-obfuscated-arguments-problem): you can create examples of tasks that allow incorrect completions for which an aligned debate agent would have a very hard time to win against a malicious opponent. Put simply, there exist tasks that are much harder to evaluate than to generate the correct answer for (i.e. counterexamples to [the principle discussed above](https://aligned.substack.com/i/88447351/evaluation-is-easier-than-generation)). The write-up provides an example using primality testing: it’s easy to claim that a given number is prime, while refuting this claim in a debate setting would require actually finding a divisor (which is much more difficult due to the existence of statistical primality tests).

The post claims that the same weakness also applies to iterated amplification, but don’t provide an argument and only mention how that would apply to the factored cognition version of amplification. However, unlike RRM, factored cognition doesn’t rely very much on the principle that evaluation is easier than generation. Supervising tasks for which evaluation isn’t easier than generation won’t work well with RRM, which is why it’s important that this principle [holds for alignment research](https://aligned.substack.com/i/88447351/a-more-modest-goal).

### Eliciting latent knowledge

The [eliciting latent knowledge (ELK) problem](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit) is about getting AI systems to tell us everything they know even if we’re not able to faithfully supervise them to do so because they know more than we do. [The authors discuss how they expect this problem to interact with debate, amplification, and RRM](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit#heading=h.3l614s96sz9t). They sketch a hypothetical scenario of an AI system that excels at predicting biological processes in detail but struggles to explain them to humans. Such a system could be used to make a new drug by predicting how it would impact human biology, without being able to explain how and why it works. This means that even with similarly capable assistance, humans wouldn’t be able to tell whether this drug is safe to use without actually running human trials and those trials wouldn’t be able to detect very slow-acting side-effects. In this scenario, assisted humans aren’t better at evaluating drugs than the model is at generating them, and RRM wouldn’t work well unless we have sufficient safety margins to train based on real-world outcomes.

### Response

The example of the primality test could easily be supervised with RRM because how statistical primality tests works can be explained to humans and accepted as sufficient evidence. But for other tasks this might not be the case. So the “deeper ELK problem” is in analogy of primality testing: a scenario where the model has a reliable “intuition” that it can’t articulate or provide evidence for.

Let’s illustrate this using the primality testing analogy. For example, the main agent could write some code that relies on its “intuition” that a number N is prime without being able to provide evidence of primality. Our evaluation assistant can point out the lack of evidence and we’d have to throw out the code. This holds both in cases where the main agent’s “intuition” is correct and the code would work and in cases where the main agent is deceptive and trying to sneak a bug into the code.

Scenarios like this might incur a (potentially substantial) alignment tax because our model “knows” the right answer. If we can’t trust the model’s code and instead we have to run potentially much less efficient code, we incur a potentially significant additional cost that’s caused only from misalignment. We might struggle to supervise such tasks with RRM even though our models can perform them well. In the absence of another alignment technique (which we currently don’t have), we have to ask humans to do these tasks themselves.

It’s unclear how much this actually matters in practice. If this issue was a wide-spread, we should be able to measure some of this using [our DC gap methodology](https://aligned.substack.com/i/88447351/the-empirical-evidence-is-looking-favorably). Maybe we’ll be able to detect this for larger models or for harder tasks, but right now we don’t have a clean enough exhibition of the problem to study.

[A recent paper](https://openreview.net/pdf?id=ETKGuby0hcs) suggests that we might be able to directly read out which statements a language model believes to be true; if this replicates this might be a path to mitigating this problem if it shows up in practice. Furthermore, better interpretability tools could help a lot with this problem because they could give us more direct access to a model’s latent knowledge.

Even if the problem was easily measurable in our models, and we can’t easily solve it, whether the problem matters a lot would depend on how much alignment tax it incurs. For alignment research automation even a larger tax might not matter much, and we might be able to find mitigations to ELK problems using automated alignment research.

Overall, my read of the evidence so far is that the most difficult obstacles to alignment will be encountered elsewhere.

## Automating alignment research is too similar to automating ML research

Most of the alignment work we do day to day is just normal ML research: we look at data, write code, train models, look at plots, and so on. This means that to automate most of our work, we’d actually need to build an automated general-purpose ML researcher. Once that’s possible, the intelligence explosion will already have started because the automated ML researcher can then work on making AI systems more capable, possibly accelerating progress rapidly. This means we might need to make a lot of progress on alignment very quickly to keep up.

This suggests that the path of automating alignment research will be difficult to navigate so that it differentially accelerates alignment over capabilities.

### Response

#### Automated ML research will happen anyway

It seems incredibly hard to believe that ML researchers won’t think of doing this as soon as it becomes feasible.

#### We’re making alignment and ML research fungible

Right now alignment research is mostly talent-constrained. Once we reach a significant degree of automation, we can much more easily reallocate GPUs between alignment and capability research. In particular, whenever our alignment techniques are inadequate, we can spend more compute on improving them. Additional resources are much easier to request than requesting that other people stop doing something they are excited about but that our alignment techniques are inadequate for.

In general, everyone who is developing AGI has an incentive to make it aligned with them. This means they’d be incentivized to allocate resources towards alignment and thus the easier we can make it to do this, the more likely it is for them to follow this incentives.

#### We can focus on tasks differentially useful to alignment research

Compared to ML research, alignment research is much more pre-paradigmatic and needs to sort out its fundamentals. The kind of tasks that help crystallize what the right paths, concepts, formalisms and cognitive tools are would be more differentially helpful to alignment.

Moreover, there is so much leverage to be gained from working on the right problems. Even if we don’t automate any of the ML research and engineering we’re working on, we could probably still gain a large increase in the effectiveness of our alignment work by just improving prioritization and finding better projects to work on. However, this is probably the part of our work that I would least like to entrust in our models if we’re not confident in their alignment, so this path is to be treated cautiously.

Once we have an automated alignment researcher, the most important and urgent research will be to make its successor more aligned than itself. We need to use it to invest in longer-term research as well, but currently we don’t have a clear picture for how solving current theoretical alignment problems would help us make the next generation of ML models more aligned. Nevertheless, it is possible that automated alignment research helps us make a lot more progress on [what the right long-term theoretical questions to study are](https://aligned.substack.com/i/72909590/a-formal-theory-for-alignment).

#### ML progress is largely driven by compute, not research

This sentiment has been famously cast as “ [The Bitter Lesson](http://www.incompleteideas.net/IncIdeas/BitterLesson.html).” Past trends indicate that [compute usage in AI doubled about every 3.4 months](https://openai.com/blog/ai-and-compute/) while [efficiency gains doubled only every 16 months](https://openai.com/blog/ai-and-efficiency/). Roughly, compute usage is mainly driven by compute while efficiency is driven by research. This means compute increase dominated ML progress historically.

But I don’t weigh this argument very highly because I’m not sure if this trend will continue, and there is always the possibility to discover a “transformer-killer” architecture or something like this.

## Alignment research can only be done by AI systems that are too dangerous to run

### Alignment research requires strong consequentialist reasoning

This objection is commonly given by [MIRI](https://intelligence.org/) and MIRI-adjacent researchers. They have a strong belief that in order to do good alignment research, you need to be good at “consequentialist reasoning,” i.e. model-based planning, that allows creatively figuring out paths to achieve goals. This is a very general cognitive technique and thus we should expect smart AI to use it. Even more, if you don’t use this kind of reasoning, then you’ll miss some important aspect of how they will behave and how they will try to seek power.

### Response

Trying to model the thought processes of systems much smarter than you is pretty hopeless. However, if we understand our systems’ incentives (i.e. reward/loss functions) we can still make meaningful statements about what they’ll try to do. Reasoning about incentives alone wouldn’t avoid inner misalignment problems ([see below](https://aligned.substack.com/i/83984486/inner-alignment-problems)), so need to account for them explicitly.

It seems clear that a much weaker system can help us on our kind of alignment research and if we’re right, we will be able to demonstrate this empirically with relatively mundane AI systems that aren’t suffering from potentially catastrophic misalignment problems.

A hypothetical example of a pretty safe AI system that is clearly useful to alignment research is a theorem-proving engine: given a formal mathematical statement, it produces a proof or counterexample. We can evaluate this proof procedurally with a proof checker, so we can be sure that only correct proofs (relative to a formal system of axioms that [we can’t ever prove to be non-contradictory](https://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems)) are produced. Such a system should meaningfully accelerate any alignment research work that is based on formal math, and it can also help formally verify and find security vulnerabilities in computer programs.

## Inner alignment problems

### Inner alignment

My research focuses mainly on “outer” alignment: getting an aligned training and evaluation objective for our AI systems on the tasks that we give them. While most alignment researchers agree that this is a critical problem that we need to get right, some alignment researchers think that this isn’t the most difficult part. For example, it could be that we actually get stuck at [inner misalignment problems](https://aligned.substack.com/p/inner-alignment): the model learns to internally execute optimization algorithms on an inferred goal, and the inferred goal [misgeneralizes at test time](https://arxiv.org/abs/2210.01790).

### Response

We have yet to see a convincing demonstration of emerging inner misalignment in our language models, though others have exhibited that [learned goals can misgeneralize at test time](https://arxiv.org/abs/2105.14111). We know LLMs exhibit in-context learning, so it’s plausible that at some point they’ll exhibit in-context RL.

It’s plausible that we can address inner alignment problems using simple techniques: As long as we have a reward function we can trust on the test distribution, we can detect inner misalignment as it’s happening and retrain our policy on the new distribution. In other words, we can reduce inner alignment problems to problems we already need to solve to achieve “outer” alignment:

-   We need reliable ways to evaluate what our policy is doing, so we can provide a training signal to our outer policy at test time.
    
-   We need detection for distributional change, so we know whether we can trust our policy and reward function or need to adapt them.
    
-   In high-stakes environments we need safe exploration, so that the outer policy avoids unsafe states in the new (and unknown) distribution of inner RL problems before we’ve updated it.
    

These solutions need to be applied very carefully. For example, when using a reward model trained from human feedback, we need to update it quickly enough on the new distribution. In particular, [auto-induced distributional shift](https://arxiv.org/abs/2009.09153) might change the distribution faster than the reward model is being updated.

## We don’t know how well generalization will work

Some people have raised the concern that we don’t know how well generalization will work in the future. So far it’s been working pretty incredibly: For example, InstructGPT generalizes to following instructions in foreign languages. However, relying on our reward model to generalize to out-of-distribution tasks is risky if we don’t understand it well.

### Response

I agree with this, but I think this doesn’t go far enough. We should try pretty hard to avoid having to rely on generalization at all, unless we have a much better reason than “it seems to work really well.” The problem is that once we mainly rely on generalization instead of evaluating what our systems are doing, we are basically “flying blind:” since we aren’t evaluating we don’t have a way of knowing whether generalization is still working, potentially until it’s far too late.

Using an RRM-like setup, I expect that we’ll get AI systems that can do pretty hard tasks while we can still recursively evaluate everything. Moreover, in the long run we shouldn’t make a train/test time distinction and keep evaluating and supervising our systems after deployment. In other words: I want to ensure that highly capable AI systems always have some probability of being supervised.

This doesn’t mean that generalization won’t help us. Ideally we can leverage generalization to make expensive evaluation a lot cheaper. Arguably reward models already fulfill this role: instead of providing a comparison for each episode during RL training, we only provide comparisons for a subset of them and let our models generalize to the rest of them. But this is i.i.d. in-distribution generalization, because we sample the tasks that we supervise at random from all the tasks that we do.

When using AI-assisted human feedback, we would hope to leverage a lot of generalization in the assistance tasks (for example to each other or from the top-level task). To be sure how well-aligned our model actually is on difficult tasks, we shouldn’t be averse to rely on generalization, but we want to be able to reach the ground-truth using recursive human judgments (e.g. humans evaluate each assistance task separately, then evaluate the higher-level tasks with assistance, and so on).

_Thanks especially to Leo Gao, William Saunders, Ajeya Cotra, Paul Christiano, and Jeff Wu for lots of discussion and feedback on this topic, as well as Daniel Kokotajlo, Holden Karnofsky, Daniel Mossing, and Carroll Wainwright for feedback on this post._
