---
title: "Leveraging Scale"
author:
  - "Markov Grey"
  - "Charbel-Raphaël Segerie"
source_url: "https://ai-safety-atlas.com/chapters/v1/capabilities/leveraging-scale/"
published: 2026-06-18
created: 2026-06-18
accessed: 2026-06-18
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Recent AI progress is primarily driven by massive scale in computation, data, and model size. Empirically observed scaling trends can help provide guidelines for predicting future capabilities.

---

In the previous section, we looked at different notions of how to define AGI and measure the relevant capabilities. Now we'll examine one of the most important drivers behind improvements in these capabilities: scale.

## Bitter Lesson

**Human-engineered domain knowledge consistently loses to general methods that leverage massive computation.** We assume that most of you probably went to university in an era where machine learning and AI roughly mean the same thing, or even that deep learning and AI mean the same thing. This hasn't always been true. Early in AI's history, researchers believed the key to artificial intelligence was carefully encoding human knowledge and expertise into computer programs. This led to expert systems filled with hand-crafted rules and chess engines programmed with sophisticated strategic principles. Time and again, these approaches hit walls while simple learning algorithms combined with massive computation kept improving. However, time and time again, researchers learned what we now call the bitter lesson.

> The biggest lesson that can be read from 70 years of AI research is that general methods that leverage computation are ultimately the most effective, and by a large margin. [...] The bitter lesson is based on the historical observations that 1) AI researchers have often tried to build knowledge into their agents, 2) this always helps in the short term, and is personally satisfying to the researcher, but 3) in the long run it plateaus and even inhibits further progress, and 4) breakthrough progress eventually arrives by an opposing approach based on scaling computation by search and learning.
> — Richard Sutton

**The bitterness comes from discovering that decades of human expertise mattered less than computation.** Researchers who spent years encoding grandmaster chess knowledge watched brute-force search defeat world champion Garry Kasparov. Hand-crafted feature detectors in computer vision got outperformed by neural networks that learned their own features from data. Phonetics-based speech recognition lost to statistical approaches. The pattern repeated: domain expertise helped initially, then hit a wall. Simple learning algorithms plus massive compute kept improving ([Sutton, 2019](http://www.incompleteideas.net/IncIdeas/BitterLesson.html)).

**The bitter lesson doesn't reject human ingenuity or algorithmic innovation.** There's a difference between building better general learning systems and encoding task-specific human knowledge. This isn’t a difference just between good old fashion AI (GoFAI), and modern deep learning. Even within deep learning, the bitter lesson still applies—the winning algorithms are those that leverage scale most effectively. Transformers didn't beat LSTMs by encoding linguistic knowledge. They outperformed because attention mechanisms parallelize better and can actually use massive compute productively. Algorithmic innovation still matters - finding architectures and training methods that extract more from the same data and hardware. The algorithms that succeed are the ones that unlock scale's potential.

**The bitter lesson shapes expectations about AI progress.** If the bitter lesson continues to be true,  improvements should come from either finding algorithms that better leverage scale, or simply scaling existing algorithms with more compute, data, and parameters. In the last few years, the majority of gains seen in AI capabilities have emerged from scaling up the same transformer based language models.

## Scaling Laws

**Training frontier AI models costs hundreds of millions of dollars, making it critical to predict returns on investment.** AI labs face resource allocation decisions with massive stakes: should they spend more on GPUs or training data? Train a larger model briefly or a smaller model longer? With a fixed compute budget, they might choose between a 20-billion parameter model trained on 40% of their data or a 200-billion parameter model trained on 4% of it. Getting this wrong wastes hundreds of millions. Scaling laws help turn these gambles into engineering decisions by establishing empirically observed relationships between inputs and model accuracy.

**Scaling laws describe how model accuracy changes as you vary four key variables:**

- **Compute**: Total floating-point operations (FLOPs) during training - accounts for GPU power, number of chips, and training duration (how many steps you train for).
- **Parameters**: The numbers the model adjusts during training - roughly analogous to "model size".
- **Data**: Training examples seen, measured in tokens for LLMs.
- **Accuracy**: How well the model performs on benchmarks - the inverse of "loss" (lower loss = higher accuracy).

![Figure 1.33](https://ai-safety-atlas.com/_astro/eadd470c5ecbd5bcadcdb62844f5f7ba84b91e8708aca70f8ae5d018e2e368ee.CABzpIwt_Z1k8LSM.webp)

*Figure 1.33: Example of capabilities increasing with an increase with one of variables in the scaling laws - parameter count. The same model architecture (Parti) was used to generate an image using an identical prompt, with the only difference between the models being the parameter size. There are noticeable leaps in quality, and somewhere between 3 billion and 20 billion parameters, the model acquires the ability to spell words correctly ([Yu et al., 2022](https://arxiv.org/abs/2206.10789)).*

**Scaling laws are empirically observed relationships, not laws of nature.** OpenAI first documented these relationships in 2020 by running hundreds of experiments, varying inputs while measuring accuracy ([Kaplan et al., 2020](https://arxiv.org/abs/2001.08361)). They found that when you increase compute by 10×, accuracy improves predictably. Double the parameters, accuracy jumps predictably. These patterns proved surprisingly consistent across model architectures and tasks, suggesting they capture something fundamental about how neural networks learn. Later research revealed optimal training requires roughly 20 tokens of data per parameter - about 10× more data than early laws suggested[^5] ([Hoffmann et al., 2022](https://arxiv.org/abs/2203.15556)). This meant previous large models were undertrained relative to their size. The relationships continue evolving as researchers gather more evidence, but the core insight remains: scale drives predictable capability gains. The following graphs clearly show massive increases in scale for data, compute, and parameter count by all major AI labs.

*Interactive figure 1.4: Exponential growth of parameters in notable AI systems. Parameters are variables in an AI system whose values are adjusted during training to establish how input data gets transformed into the desired output; for example, the connection weights in an artificial neural network ([Giattino et al., 2023](https://ourworldindata.org/artificial-intelligence)).*

*Interactive figure 1.5: Exponential growth of datapoints used to train notable AI systems. Each domain has a specific data point unit; for example, for vision it is images, for language it is words, and forgames it is timesteps. This means systems can only be compared directly within the same domain ([Giattino et al., 2023](https://ourworldindata.org/artificial-intelligence)).*

*Interactive figure 1.6: Exponential growth of computation in the training of notable AI systems. Computation is measured in total peta FLOP, which is 10e15 floating-point operations ([Giattino et al., 2023](https://ourworldindata.org/artificial-intelligence)).*

**The Broken Neural Scaling Laws (BNSL) update in 2023**

Research showed that performance doesn't always improve smoothly - there can be sharp transitions, temporary plateaus, or even periods where performance gets worse before getting better. Examples of this include things like "Grokking", where models suddenly achieve strong generalization after many training steps, or deep double descent, where increasing model size initially hurts then helps performance. Rather than simple power laws, BNSL uses a more flexible functional form that can capture these complex behaviors. This allows for more accurate predictions of scaling behavior, particularly around discontinuities and transitions. Scaling laws are a good baseline, but discontinuous jumps in capabilities and abrupt step changes are still possible ([Caballero et al., 2023](https://arxiv.org/abs/2210.14891)).

![Figure 1.34](https://ai-safety-atlas.com/_astro/8e2e605a0c66f707ea6ce2a5974db7826aa4a37bd8766c2b80668636d60460da.Bhx54fu0_25OOF4.webp)

*Figure 1.34: A Broken Neural Scaling Law example (dark black solid line) (with 3 breaks where purple dotted lines intersect with dark black solid line) contains 4 individual power law segments (where the dashed lines that are yellow, blue, red, and green overlap with the dark black solid line). The 1st and 2nd break are very smooth; the 3rd break is very sharp ([Caballero et al., 2023](https://arxiv.org/abs/2210.14891)).*

## Scaling Hypothesis

**Scaling might continue driving capability gains.** Look back at the examples from previous sections - the programming abilities, emergent reasoning, scientific research assistance, the jump from GPT-3.5 to GPT-4 across professional exams. These capabilities appeared as models got bigger and trained on more data, without requiring new architectural breakthroughs or encoded domain knowledge. If current approaches scaled up could produce systems capable of automating AI research within years, safety work becomes far more urgent. The existing evidence supports multiple interpretations because we're watching a technology develop in real-time whose limits we don't fully understand. So different people hold different hypotheses about how the future could unfold.

**The strong scaling hypothesis.** This proposes that simply scaling up existing architectures with more compute and data will be sufficient to reach transformative AI capabilities ([Gwern, 2020](https://gwern.net/scaling-hypothesis)). According to this view, we already have all the fundamental components needed - it's just a matter of making them bigger, following established scaling laws.

![Figure 1.35](https://ai-safety-atlas.com/_astro/59b06d94e55937d526c17327f255eddadf445e39b248930e0ce6adb8162d0f2c.8ArHDsTp_ZcVvmc.webp)

*Figure 1.35: Augmentation/Scaffolding stays constant, but if the scaling hypothesis, weak or strong, is true, then capabilities will keep improving just by scaling.*

**The weak scaling hypothesis.** This view states that even though scale will continue to be the primary driver of progress, we will also need targeted architectural and algorithmic improvements to overcome specific bottlenecks. These improvements wouldn't require fundamental breakthroughs, but rather incremental enhancements to better leverage scale ([Gwern, 2020](https://gwern.net/scaling-hypothesis)).

**Researchers have been developing algorithms that leverage scale and compute for more than a decade.** We have seen many gains come from improvement in compute efficiency from innovations like better attention mechanisms, mixture-of-experts routing, and efficient training methods. But even when researchers have developed sophisticated algorithms following the bitter lesson's principles, data suggests that between 60-95% of performance gains came from scaling compute and data. While algorithmic improvements contributed 5-40%, though there is substantial methodological uncertainty in disentangling these contributions ([Ho et al., 2024](https://epoch.ai/blog/algorithmic-progress-in-language-models)).

**The emergence of unexpected capabilities might provide another argument for strong scaling.** We've seen previous generations of foundation models demonstrate remarkable abilities that weren't explicitly trained for, like programming. This emergent behavior hints that it is not impossible for higher-order cognitive abilities to similarly emerge simply as a function of further scale.

![Figure 1.36](https://ai-safety-atlas.com/_astro/bf0a21178ac5eed6de6d35f41948b121b7dde10b52ce978f5b9f72955814c759.DSIRe1Hz_ZE2jXc.webp)

*Figure 1.36: Even if we see no improvements in model scale, other elicitation techniques and scaffolding can keep improving. So overall capabilities keep growing. Realistically, the future is probably going to see both improvement due to scaffolding and scale. So for now, there does not seem to be an upper limit on improving capabilities as long as either one of the two holds.*

**Scale combined with techniques and tools hypothesis.** Essentially, both the scaling laws (which only predict foundation model capabilities) and most debates around "scale is all you need" often miss other aspects of AI development that happen outside the scope of what scaling laws can predict. They don't account for improvements in AI "scaffolding" (like chain-of-thought prompting, tool use, or retrieval), or combinations of multiple models working together in novel ways. Any LLM with internet access, code execution, and the ability to call upon the help of other specialized sub-models has substantially more capability than the same LLM alone. We gave several examples of this being the dominant trend in our first section - tool use, thinking for longer (inference time scaling), MCP servers and so on.

**Debates around the scaling laws only tell us about the capabilities of a single **foundation model** trained in a standard way.** For example, by the strong scaling hypothesis we can reach TAI by simply scaling up the same foundation model until it completely automates ML RnD. But even if scaling stops, halting capabilities progress on the core foundation model (in either a weak or a strong way), the external techniques that leverage the existing model can still continue advancing. Many researchers think that this is a core element where future capabilities will come from. It is also referred to as "unhobbling" ([Aschenbrenner, 2024](https://situational-awareness.ai/from-gpt-4-to-agi/#Unhobbling)), "schlep" ([Cotra, 2023](https://www.planned-obsolescence.org/scale-schlep-and-systems/)) and various other terms, but all of them point to the same underlying principle - raw scaling of single model performance is only one part of overall AI capability advancement.

![Figure 1.37](https://ai-safety-atlas.com/_astro/f5ef5f01a4c869d9a77a0c71f25718abf017d9b5218e4074ff78505777a758ed.C8R01McJ_1vMyH6.webp)

*Figure 1.37: An example of how much the performance on a benchmark can change just by using post training techniques like doing reasoning specific training and allowing the model to think for longer. The base model scores ~ 4.5% on the humanities last exam benchmark (HLE), whereas with each subsequent “unhobbling” step we see jumps in performance leading up to a 25% score on the benchmark ([Somala et al., 2024](https://epoch.ai/gradient-updates/three-issues-undermining-compute-based-ai-policies)).*

**Even the tool based scaling hypothesis is debated.** Some argue that tools or scale poured into LLMs is unlikely to lead to AGI as they define it. They advocate for completely different architectures from transformer based LLMs, focusing instead on things like neuro-symbolic approaches, ensemble methods, or a completely new undiscovered architecture ([Goertzel et. al., 2023](https://arxiv.org/abs/2310.18318); [Marcus, 2025](https://garymarcus.substack.com/p/the-last-few-months-have-been-devastating); [LeCun, 2025](https://www.youtube.com/watch?v=ETZfkkv6V7Y); [Chollet, 2025](https://www.youtube.com/watch?v=s7_NlkBwdj8)).

**Despite disagreements about whether scale will lead to “true AGI”, major AI labs are betting heavily on scaling.** Sam Altman from OpenAI has stated his belief that scaling is going to be a big component leading to capability gains ([Altman, 2023](https://openai.com/blog/planning-for-agi-and-beyond)), Anthropic CEO Dario Amodei has expressed similar views ([Amodei, 2023](https://www.dwarkeshpatel.com/p/dario-amodei)) and DeepMind's safety team similarly wrote that "*not many more fundamental innovations are needed for AGI*" ([DeepMind, 2022](https://www.lesswrong.com/posts/GctJD5oCDRxCspEaZ/clarifying-ai-x-risk)). This consensus suggests that regardless of whether strong, weak, or tools-based scaling dominates, scale itself will likely remain central to near-term progress.

[^5]:  This is also commonly called ‘chinchilla optimality’ or the chinchilla optimal frontier based on the original model that these laws were tested on.
