---
title: "The paper that killed deep learning theory"
author:
  - "LawrenceC"
source_url: "https://www.lesswrong.com/posts/ZvQfcLbcNHYqmvWyo/the-paper-that-killed-deep-learning-theory"
published: 2026-04-26
created: 2026-09-22
accessed: 2026-09-22
llm-review:
  date: 2026-09-22
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-22
    kind: "live"
description: "Around 10 years ago, a paper came out that arguably killed classical deep learning theory: Zhang et al.'s aptly titled Understanding deep learning re…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Around 10 years ago, a paper came out that arguably killed classical deep learning theory: Zhang et al.'s aptly titled _Understanding deep learning requires rethinking generalization_.

Of course, this is a bit of an exaggeration. No single paper ever kills a field of research on its own, and deep learning theory was not exactly the most productive and healthy field at the time this was published. And the paper didn't come close to addressing _all_ theoretical approaches to understanding aspects of deep learning. But if I had to point to a single paper that shattered the feeling of optimism at the time, it would be Zhang et al. 2016.[^note-best-paper] 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/bd260105325c4383584f07f70859bf2a3c792083c7c89de198978772800a9c29/rokdkfphnilzofzxmz7m)

_Believe it or not, this unassuming table rocked the field of deep learning theory back in 2016, despite probably involving fewer computational resources than what Claude 4.7 Opus consumed when I clicked the “Claude” button embedded into the LessWrong editor._

---

Let’s start by answering a question: what, exactly, do I mean by deep learning theory?

At least in 2016, the answer was: “extending _statistical learning theory_ to deep neural networks trained with SGD, in order to derive _generalization bounds_ that would explain their behavior in practice”.

---

Since [the seminal work of Valiant](https://www.cs.princeton.edu/courses/archive/spring08/cos511/handouts/valiant.pdf) in the mid 1980s, [statistical learning theory](https://en.wikipedia.org/wiki/Statistical_learning_theory) had been the dominant approach for understanding machine learning algorithms. The framework imagined a data distribution _D_ over inputs X and outputs Y where the goal was to fit a hypothesis _h_ : X → Y that minimized the expected test loss for a loss function L : X × Y → R over _D_. A learning algorithm would receive _n_ samples from the data distribution, and would minimize the training loss averaged across the sample L(h(x), y).

The core results of this approach took the form of _generalization bounds:_ given some metric of complexity of the hypothesis class _H_, bound the difference between the average training loss and the test loss in terms of this metric of hypothesis complexity. To put it in less technical terms, a generalization bound basically says:

> _If your hypothesis class is not too complicated relative to the amount of training data you have, and it explains the training data well, then it will generalize and do well on the full data distribution._

The field of statistical learning had settled on a few preferred ways to measure complexity: [_VC dimension_](https://en.wikipedia.org/wiki/Vapnik%E2%80%93Chervonenkis_dimension) and [_Rademacher complexity_](https://en.wikipedia.org/wiki/Rademacher_complexity) being the two main metrics, though some researchers considered alternatives such as the [margin between positive/negative example from the classification boundary](https://en.wikipedia.org/wiki/Margin_classifier).

The success of modern deep learning, starting from the early 2010s, posed something of an existential crisis for this field. By all the metrics – including both VC Dimension and Rademacher complexity – even a simple MLP with sigmoidal or ReLU activations represents far too complicated a hypothesis class to not immediately overfit on the training data. If the VC dimension results for a neural network are assumed to be asymptotically tight up to constraints, then no neural network with even 100,000 parameters should be able to do anything useful on data points not included in the training data. Yet, not only were neural networks performing better than other machine learning algorithms, by the mid 2010s there was a growing list of examples where neural networks with tens of millions of parameters solved problems (such as the ImageNet challenge) that no other machine learning algorithm could make much progress on.  

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/089579c755f591822bd4e6d179b1e0eff3a44cd4bba5e089efc6578acbed23fc/afoeu62j0avnk1rrrl7k)

_This classic XKCD was published in September 2014, right about the time where neural networks started to make image classification viable without years of dedicated research effort._

  

---

Clearly, neural networks did generalize. If traditional metrics of complexity, based on the representation capacity of the class of neural networks with arbitrarily specified, infinite precision floating points, failed at capturing the simplicity of neural networks in practice, then the field simply needed to construct new simplicity measures to argue that neural networks learned simple functions in practice.

This was the approach taken in several papers around the time. For example, [Neyshabur, Tomioka, Srebro’s](https://arxiv.org/abs/1503.00036) [_Norm-Based Capacity Control in Neural Networks_](https://arxiv.org/abs/1503.00036) [(2015)](https://arxiv.org/abs/1503.00036) constructed a complexity measure based on the [Frobenius norm](https://en.wikipedia.org/wiki/Matrix_norm) of the weight matrices in a deep neural network. [Hardt, Recht, and Singer’s](https://arxiv.org/abs/1509.01240) [_Train faster, generalize better: Stability of stochastic gradient descent_](https://arxiv.org/abs/1509.01240) [(2015)](https://arxiv.org/abs/1509.01240)[^note-hardt-recht] showed that neural networks trained with a small number of SGD steps with sufficiently small step size were [_uniformly stable_](https://en.wikipedia.org/wiki/Stability_\(learning_theory\)) in that removing a single training example would not change the model’s loss on any particular test example by very much.

At least when I first entered the field of deep learning as an undergrad in early 2016, there was a sense of cautious optimism: we would find the way in which neural networks in realistic regimes were simple, and thereby derive generalization bounds that would be applicable in practice.

---

So, what did Zhang et al. 2016 actually show? Why did understanding deep learning require rethinking generalization?

To quote the paper, the “central finding can be summarized as: _Deep neural networks easily fit random labels_”. Specifically, the authors trained neural networks on the standard-at-the-time CIFAR10 and ImageNet benchmarks to memorize random labels, while following standard procedures and training for the same order of magnitude of steps. They also show that with similar techniques, neural networks could be trained to memorize random noise inputs.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/9b3cf38a27b50366bb58bdb55bddf322f5bbabb2172b40f712a22990f29164e5/ov0f9aweaes1uevycijk)

_From the introduction of Zhang et al. 2016. You know that a paper is going to be impactful when its central finding is exactly 7 words long._

Why is this an effective death knell for the simplicity-and-generalization-bound approach? The authors' results show that the _same_ class of neural networks, trained with the _same_ learning algorithm, can generalize when given true labels and memorize random ones. This shows that the hypothesis class of neural networks that are learnable with standard techniques _cannot be simple_ in any useful sense, at least for complexity measures that depend only on properties of the hypothesis class and (data-independent) properties of the learning algorithm.

---

The paper has 5 important parts. Let's go through each of them.

1.  **The core empirical finding** **that neural networks can fit random labels.** The authors train a 1- and a 3-layer MLP, an AlexNet variant, and an Inception variant on CIFAR10. They train the models normally (with the true labels), as well as four ways of corrupting the dataset: random labels (replacing each label with a random class with some probability), shuffled pixels (the same permutation on pixels is applied to each image), random pixels (a different random permutation is applied to each image), and pure Gaussian noise (replacing every single pixel with an independent draw from a Gaussian). In each of these five cases, the network gets to near 0 training loss. Notably, while training with random labels is _harder_, convergence to zero training loss takes only a factor of 1.5-3.5x longer than with the true labels. And by varying the degree of label corruption, the authors can produce models that either generalize to the test set to varying degrees or perform no better than chance.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/61c40c609577bc7500f4053034ea5f2ff4a39b03f87fee3285a5a4f3006e88d5/kcuhooqm3k7pheyuwm1z)

_The key figure from the Zhang et al. paper: subfigures (a) and (b) show that neural networks are able to perfectly memorize random labels without many additional training steps, and (c) confirms that models in their regime interpolate between chance performance and good performance on the test set._

The authors also train an InceptionV3 model on ImageNet with random labels, and find that it can get 95.2% top-1 accuracy on the train set.  

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/ZvQfcLbcNHYqmvWyo/fca5ffd560d7695c9bf60c3e1cea8c7f5f5cf31abc573647a5f5aa622f200c45/rygxwayniopy1ikebdyf)

_The ImageNet results from the paper are similar in that neural networks can memorize random labels to a large extent. Unlike with the CIFAR10 results, the authors also report the extent regularization impedes the memorization ability of the network (not very much)._

  

2.  **The implications for statistical learning theory approaches to generalization bounds.** These experiments show that in realistic regimes, Rademacher complexity and VC dimension bounds are basically vacuous, since neural networks have enough representational capacity to memorize entire training sets. Hardt and Recht's (both authors on this paper) prior results on uniform stability also are necessarily vacuous in this setting, since it’s a property that only depends on the algorithm and hypothesis class (it’s data-independent!), but the algorithm and hypothesis class stays the same in each experimental setting.
3.  **Further experiments demonstrating that explicit regularization cannot rescue generalization bounds.** The authors show that on both ImageNet and CIFAR-10, explicit regularization methods such as data augmentation or weight decay do not seem to affect the test accuracy of the algorithms very much. That is, the neural networks generalize to the test distribution even without any regularization. The authors also show that on ImageNet, applying dropout or weight decay _still_ allows the resulting model to memorize the training set to a large extent. So any generalization bound that depends on regularization (e.g. weight norm-based explanations) cannot explain why neural networks generalize.
4.  **A simple toy construction that showed a two-layer ReLU network can memorize a number of examples** _**linear in parameter count**_**.** The authors include a simple theoretical result, where a depth-2 ReLU network with 2n+d weights can fit _any_ labeling of a sample of _n_ data points in _d_ dimensions. This feels pretty extraneous to me given the strength of the empirical results, but the construction is simple and it confirms the intuition that neural networks with millions of parameters “should” be able to fit tens of thousands of data points in the CIFAR10 setting.  
5.  **Some notes on how statistical learning theory fails** _**even in a simple overparameterized linear regime**_**.** The authors consider a basic overparameterized linear regression setting, and show both empirically and theoretically that SGD can learn a minimum norm solution that generalizes. The authors point out that statistical learning theory at the time had no explanation for generalization in this simple regime.  
    They also demonstrate empirically that smaller norm doesn’t imply better generalization – by applying preprocessing to an MNIST dataset to increase its effective dimensionality for a linear classifier, the resulting larger linear classifier has higher norm but less generalization error (this result also undercuts the weight-norm based approach to explaining generalization in neural networks).  
    Amusingly, the quick thoughts put forth by the authors in this setting would go on to become quite influential, both in that people would study the behavior of SGD in overparameterized linear regimes, and that it hints toward future puzzles such as double descent.

---

So, how did the field of deep learning theory react to this paper? What were the attempts to get around this result using data-dependent generalization bounds? And what was the paper that arguably sealed the deal on the whole edifice, and nailed the proverbial coffin shut?

I'll answer these questions in tomorrow's post.

[^note-best-paper]: Notably, Zhang et al. 2016 got _best paper_ at ICLR 2017, so it was widely recognized as important even at the time.
[^note-hardt-recht]: Note that both Hardt and Recht were also authors on the Zhang et al. paper.
