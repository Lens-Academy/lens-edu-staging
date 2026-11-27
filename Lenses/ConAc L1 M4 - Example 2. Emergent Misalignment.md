---
id: '19ea195b-aa85-4350-ae97-71e6a5d0db6d'
title: "Example 2. Emergent Misalignment"
reading_minutes: 5
tutor_minutes: 0
tags:
  - wip
---
#### Text
content::
In February 2025, a group of researchers published a paper titled [Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs](https://www.alignmentforum.org/posts/ifechgnJRtJdduFGC/emergent-misalignment-narrow-finetuning-can-produce-broadly). They reported a surprising finding: fine-tuning language models to produce insecure code led to undesirable behaviour across a range of unrelated tasks.

The researchers could demonstrate the phenomenon experimentally, but did not yet have a satisfactory explanation for why it occurred.

Shortly afterwards, two of the authors published a set of open problems, outlining a research agenda motivated by this discovery.

#### Article
source:: [[../articles/betley-open-problems-in-emergent-misalignment]]
from:: We've recently published a paper about [Emergent Misalignment]
to:: Can we find more examples where training on some narrow task leads to large shifts in model's behavior in unrelated contexts?

#### Text
content::
Notice how differently this agenda is constructed from Kosoy's learning-theoretic agenda.

The starting point here is an empirically observed phenomenon in contemporary AI systems. The research questions emerge from attempts to understand the conditions under which it occurs, the mechanisms that produce it, and the extent to which it generalises across models, datasets and training procedures.

The researchers also consider whether emergent misalignment is a particular instance of a more general phenomenon of unexpected behavioural generalisation during training. If so, investigating this relatively specific observation could contribute to a broader scientific understanding of how neural networks acquire and generalise behavioural properties.

The expectations underlying this research agenda might be reconstructed as follows:

- The observed phenomenon reflects some underlying regularities of learned systems that extend beyond the original experimental setting.
- Systematic experimentation can help identify these regularities and the mechanisms responsible for them.
- The resulting knowledge can inform more general explanations of how behavioural properties are acquired and generalised during training.
- Such explanations may eventually allow us to predict and prevent undesirable forms of generalisation in future AI systems.

The agenda does not require researchers to commit to a particular mathematical theory of learning or intelligence at the outset. The choice of theoretical constructs and explanatory frameworks can itself be informed by subsequent empirical findings.

One of the challenges associated with this approach is establishing the scope of the knowledge it produces. Which of the regularities we discover reflect general properties of learning systems? What are those properties? What can we do to reduce the risks? What would justify extrapolating these mitigation strategies to substantially more capable systems?

In Kosoy's agenda, the challenge is to establish a connection between an abstract mathematical theory and the properties of practically relevant AI systems. Here, researchers face a complementary challenge: establishing how far the knowledge obtained by studying particular AI systems can be generalised.

Can we organise a research agenda so that these two problems are addressed together from the outset?

Our next example illustrates an attempt to do precisely that.
