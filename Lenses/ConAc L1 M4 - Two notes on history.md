---
title: "Two notes on history"
reading_minutes: 3
tutor_minutes: 0
tags:
  - wip
---
#### Text
content::
\### Sparse autoencoders (SAEs)

In May 2024, Anthropic released a version of Claude that had developed a peculiar preoccupation with the Golden Gate Bridge. Even questions about entirely unrelated subjects could elicit enthusiastic descriptions of the bridge. [Golden Gate Claude](https://www.anthropic.com/news/golden-gate-claude) was an unusually accessible demonstration of a research technique known as sparse autoencoders (SAEs).

Two years earlier, Nelson Elhage and his colleagues at Anthropic had published [Toy Models of Superposition](https://transformer-circuits.pub/2022/toy_model/index.html). Their experiments helped explain an awkward property of neural networks: a single neuron could participate in representing several unrelated concepts. If we wanted to understand what a network had learnt, we needed some way of recovering these concepts from its activations.

Researchers at Conjecture [proposed using sparse autoencoders](https://www.alignmentforum.org/posts/z6QQJbtpkEAX3Aojj) for this purpose. In 2023, Hoagy Cunningham and his colleagues tested the approach on language models, while Trenton Bricken's team at Anthropic independently pursued a similar idea. Both groups obtained promising results.

Would the technique work on a model as large and capable as Claude 3 Sonnet? In 2024, Adly Templeton and his colleagues [showed that it could](https://www.anthropic.com/research/mapping-mind-language-model). Among the millions of features they extracted was one associated with the Golden Gate Bridge. By artificially amplifying its activation, they could induce a remarkable change in Claude's behaviour.

By the time SAEs attracted widespread public attention, several research groups had contributed to establishing the problem, developing the method and demonstrating its potential.

\### AI Control

In 2023, Ajeya Cotra posed a question to Buck Shlegeris and Ryan Greenblatt: how would they align AGI if they absolutely had to come up with something that worked? According to [Shlegeris's recollection](https://www.theverge.com/ai-artificial-intelligence/996563/ai-safety-research-metr-redwood-openai-anthropic), they spent two hours thinking about the question, then two weeks, then two months.

What if we could use powerful AI systems safely even if we couldn't establish that they were aligned? This question became the basis of a research programme now known as AI control. By December 2023, Redwood Research had published its [first major experimental study](https://arxiv.org/abs/2312.06942), followed by a [broader case for the agenda](https://www.alignmentforum.org/s/PC3yJgdKvk8kzqZyA/p/kcKrE9mzEHrdqtDpE) in January 2024.

When you first encounter a research agenda on Twitter or LessWrong, you might associate it with a particular paper, person or organisation. It is worth looking a little further back. The person who identified the problem, the person who came up with a promising way of addressing it, and the person whose work made the agenda widely known may have entered the story years apart.
