---
title: "'Obvious' Insights Take Time"
source_url: https://ifanyonebuildsit.com/2/obvious-insights-take-time
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---
It's hard to come across insights in AI, even when they look simple and obvious in retrospect.

This is important to understand because doing AI *right* will probably require a lot of insights. No matter how simple they might sound in retrospect, such insights can sometimes take decades of toil to find.

Toward that end, we'll spotlight a few of the insights that power modern AIs.

If you happen to have some skill at programming, for instance, you might read Chapter 2 of the book and think that this "gradient descent" business sounds so simple that you could just run out and try it. But if you did, you'd probably quickly run into some sort of error. Perhaps your program would crash with a floating-point error because the numbers in one of the weights had gotten too large.

Back in the twentieth century, nobody knew how to make gradient descent work on a neural network with several layers of intermediate numbers between the input and the output. To avoid issues, programmers had to learn all sorts of tricks, like initializing all the weights in slightly clever ways that prevent them from getting too large. For example, instead of initializing all weights to a random number between 0 and 1 (or a random number with mean 0 and standard deviation 1), you've got to initialize the weights like that and then divide them all by a constant designed to ensure that the *next* layer's numbers *also* won't get too large during operation.

Gradient descent runs into problems when run on complicated formulas with lots of steps or "layers," and dividing the initial random numbers by a constant is one of the primary ideas that enables "deep learning." That trick wasn't invented until six decades after neural networks were originally proposed in 1943.

The idea of using calculus to tweak the parameters was first discussed in 1962 and first applied to the idea of neural networks with more than one layer in 1967. It wasn't really popularized until a paper in 1986 (which Geoffrey Hinton co-authored — this is one reason he's called a "godfather of AI"). Note, however, that the more general idea of using calculus on differentiable questions to move in the direction of a correct answer — for example, in order to calculate a square root — was invented by Isaac Newton.

Another key trick is as follows. In the book, we give an example of gradient descent operations:

> I'll multiply each input-number with the weight in the first parameter, and then add it to the weight in the second parameter, and then I'll replace it with zero if it's negative, and then…

This list of operations is no mistake. Multiplication, addition, and "replace it with zero if it's negative" are, more or less, the three critical operations in a neural network. The first two are the operators that make up a "matrix multiplication," and the last one introduces a "nonlinearity" and thereby allows the network to learn nonlinear functions.

The formula for "replace it with zero if it's negative" is  and is called a rectified linear unit (ReLU).[\*](#ftnt67) The formula that people originally tried to use was the "sigmoid" formula:

There were good reasons for guessing that the more complicated "sigmoid" formula would work! From a shallow perspective, it makes the outputs range sensibly from 0 to 1 in a smooth way; and from a deeper perspective, it has some useful connections to probability theory. Even some modern deep neural networks use something like a sigmoid on some steps. But if you are just going to use one nonlinearity, a ReLU works much better.

The problem with the sigmoid formula is that it tends to make a lot of the outputs have very tiny gradients. And if most of the gradients are very small, gradient descent stops working…at least, unless you know the modern trick of taking larger gradient steps when tiny gradients always point in the same direction. (To our knowledge, this trick first appeared in the literature in 2012, when it was proposed by Geoffrey Hinton.)

"Make your initial random numbers smaller so their multiplied sums don't get huge" and "use max(x, 0) instead of a complicated formula" and "take larger steps when tiny gradients keep pointing in the same direction" might sound like weirdly simple ideas to not invent for decades — especially with the way they sound like they'd be obvious in retrospect to a computer programmer who understands all this stuff. This is an important lesson for the way that science and engineering work in real life.

*Even when there is a simple and practical solution to some engineering challenge, often researchers don't find it until they have tried and failed for decades.* You cannot rely on researchers seeing it as soon as a solution becomes important. You cannot rely on them seeing it within the next two years. Even if a solution seems obvious in retrospect, sometimes the field stumbles along for decades without it.

Later on, this will be a useful lesson to keep in mind in Part III of the book, when we discuss how ill-prepared humanity is for the challenge presented by superintelligence.

If the price of some mad inventors stumbling ahead is that everyone on Earth dies during this awkward baby stage, then we can't let them stumble on ahead. The inventors will protest that there's no way for them to figure out the simple, robust solution without being allowed to stumble around for a few decades; they'll say it's not realistic to expect them to figure it out in advance.

It is hopefully obvious to everyone who is not a mad inventor that, if these claims are true, we ought to shut down their efforts.

But that's a topic we'll take up again in Part III of the book, after we complete the argument that artificial superintelligence would have the means, motive, and opportunity to extinguish humanity. For now, we turn to the topic of how "obvious" ideas like the ones we've been discussing — and a few ideas that are quite a bit less obvious — come together to make an actual working AI model.

[\*](#ftnt67_ref) Newer architectures will use more sophisticated functions. For instance, the Llama 3.1 architecture [described below](/2/a-full-description-of-an-llm) uses the ["SwiGLU" function](https://arxiv.org/pdf/2002.05202), which has a complicated formula that we won't reproduce here.