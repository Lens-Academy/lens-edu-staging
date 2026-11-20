---
id: 'b4afae57-53fe-42ab-bb86-b06209fa3b5f'
title: "Scaling laws"
{++{"author":"opus-5.5 (Alex R)'s AI","timestamp":1795205125763}@@reading_minutes: 10
tutor_minutes: 0
++}tags:
  - wip
---
#### {++{"author":"opus-5.5 (Alex R)'s AI","timestamp":1795205125763}@@Callout: In this module
collapse:: closed

#### Text
content::
We've looked at what different experts expect to happen. Now let's look at the observations and ideas behind those expectations. To do that, we'll need a few more concepts:

- Scaling laws
- Superintelligence
- Intelligence explosion
- Recursive self-improvement

As you explore these concepts, here are a couple of questions worth keeping in mind:

- What conclusions might the different doctrines draw from the facts presented?
- Could these facts and ideas be interpreted as evidence for or against any of the doctrines?

#### End Callout

#### Article
source:: [[../articles/intelligence-deep-dive-two-the-scaling-era]]
from:: The last decade of artificial intelligence developments
to:: and training data size.

#### Article
from:: In the words of
to:: This observation characterizes the scaling era in AI.

#### Callout: What Are Scaling Laws, Anyway?
collapse:: closed

#### Text
content::
The term “scaling laws” in deep learning refers to relations between functional properties of interest (usually the test loss or some performance metric for fine-tuning tasks) and properties of the architecture or optimization process (like model size, width, or training compute).

When you're training an AI model, you give it some data, let it learn, and then test how well it does on something it hasn't seen before. Naturally, you wonder: what would happen if you made the model twice as large? Or gave it ten times more data? Would it become twice as good? A little better? Would it make any difference at all?

You could run the experiments and find out. And when researchers did, they discovered the models' prediction errors often decreased in remarkably regular ways. Regular enough that you could fit a simple mathematical equation to the results. And once you had that equation, you could make predictions about models you hadn't even built yet.

That's what scaling laws are: empirical mathematical relationships that tell us how a model's property such as loss changes as we change the resources used to build or run it. They don't tell us everything a future model will be capable of (they just can’t by the very nature of these laws), and they don't guarantee that the same patterns will continue forever. But they give us something quite handy: a way to make quantitative predictions about the effects of scaling up AI.

If you're not familiar with the concept, this [short article](https://aisafety.info/questions/7750/What-are-scaling-laws) is a good place to start. For a more detailed explanation, see the [chapter on scaling laws](https://www.aisafetybook.com/textbook/scaling-laws) from Dan Hendrycks' textbook *Introduction to AI Safety, Ethics, and Society* or this [video from the Welch Lab](https://www.youtube.com/watch?v=5eqRuVp65eY).

Scaling laws are used to decide on trade-offs like: investing in more training data, buying more GPUs or training for longer.

**But what exactly are we predicting?**

Suppose I tell you that doubling the size of a model will make it better at predicting the next word. Fine. Now suppose you ask me whether that larger model will be able to solve a maths problem it couldn't solve before. Can I tell you that from the same equation?

Not necessarily. We've measured one thing: how well the model predicts text. What we really want to know is something else: what it can do. And we shouldn't confuse the two.

#### End Callout

#### Text
content::
The research by Kaplan and Hoffmann (which started it all) has established scaling laws as an almost must-use tool in modern AI development. They have enabled the planning of costly experiments, the prediction of loss in large models based on experiments with smaller ones, and the optimization of the balance between parameters, data, and compute.

Interestingly, scaling laws turn out to be both more pervasive and less universal than we might expect. We propose you to reflect on 4 claims:

- First, different architectures scale in different ways. Standard Transformers often exhibit consistent power-law relationships, other architectures (e.g. mixture-of-experts or multimodal models) tend to require additional variables and more complex modeling. Thus the high expectations placed on scaling laws as a universal recipe were, well... perhaps too high. (That said, within their specific domains of applicability, these observed patterns remain useful and are actively utilized).
- Second, the quantity of data is not synonymous with its utility. Factors such as dataset composition, the quality of individual examples, the frequency of data reuse, and the relevance of the data to the target task are *all* critical. In some cases, careful data curation yields better results than a volume of data increasement. That pattern does not generalize well from small models to large ones (which was, in fact, one of the primary early arguments for the utility of scaling laws).
- Third, inference-time compute has emerged as an independent driver of performance improvements. Techniques such as multiple attempts at solving a problem, search, iterative refinement of answers, or querying external knowledge bases can enhance results without requiring an increase in the number of parameters in the core model.
- Fourth, scaling laws do not predict all metrics with equal accuracy. While the reduction in training loss tends to follow a fairly predictable trajectory, performance on specific, practical tasks can exhibit saturation, abrupt transitions, or instability. In some instances, researchers observe patterns that simply do not conform to the expected scaling behavior, with no discernible, consistent deviations from that pattern.

#### Callout: Scaling laws literature reviews
collapse:: closed

#### Text
content::
Scaling laws are useful because they let us predict how models might behave at scales we haven't tested yet. For those interested in how much of this picture of predicting AI progress by extrapolating scaling curves is supported by evidence, we've collected two optional readings:

- The narrative review ["Transformer architectures scaling laws and in-context learning in foundation models"](https://link.springer.com/article/10.1007/s44163-026-02726-7) walks you through a review of empirical scaling laws and existing discussion of ICL mechanisms and the nature of emergent abilities.
- [(Mis)Fitting: A Survey of Scaling Laws](https://arxiv.org/abs/2502.18969) - A review of 51 studies on scaling laws, supplemented by the authors’ own experiments, examines how sure are we that we've found the right laws in the first place? The authors find that seemingly minor methodological choices can lead to substantially different results.

#### End Callout

#### Text
content::
But there is a more fundamental question: why do scaling laws work at all? And what do they actually tell us about intelligence? It turns out that you can get the same power-law improvements in prediction loss even with relatively simple models that don't learn anything we would recognise as intelligent behaviour. Some of these patterns can be explained just by the statistical properties of the training data, without assuming that the model is learning useful concepts or reasoning about the world. So predicting how a model's loss will decrease is not the same as understanding how capabilities emerges.

#### Callout: Does scaling laws reflect the covariance and the covariance alone?
collapse:: closed

#### Text
content::
If you want to explore this distinction further, [Power Laws Are Not Enough](https://www.lesswrong.com/posts/5x54xhX3K2TNY2L3T/power-laws-are-not-enough) brings together several theoretical and empirical results to explain where power-law scaling comes from.

#### End Callout

#### ++}Text
{--{"author":"opus-5.5 (Alex R)'s AI","timestamp":1795205143352}@@TBD--}{++{"author":"opus-5.5 (Alex R)'s AI","timestamp":1795205143352}@@But whatever the limitations of scaling laws, AI companies are investing billions of dollars in larger models, more powerful computing infrastructure, and new ways to use computation during training and inference.

We don't know how long these improvements will continue, but for now, the world's leading AI labs are betting enormous resources that the next increase in scale will be worth it.

What’s important for us is that the race to scale has had a number of important consequences.

#### Article
from:: First, the extreme compute resources required
to:: capable of developing frontier AI models.

#### Article
from:: This concentration reflects a broader structural dynamic
to:: the data on which they depend.

#### Article
from:: this demand led to an extraordinary increase
to:: in data centers will be required.

#### Article
from:: The economic justification for these investments
to:: assumption of sustained returns to scale.

#### Article
from:: Finally, the extraordinary scale of current investment
to:: retained earnings of technology firms.++}