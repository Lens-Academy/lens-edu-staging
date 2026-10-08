---
title: "Towards a New Decision Theory"
author:
  - "Wei Dai"
source_url: "https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory"
published: 2009-08-13
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "It commonly acknowledged here that current decision theories have deficiencies that show up in the form of various paradoxes. Since there seems to be…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

It is commonly acknowledged here that current decision theories have deficiencies that show up in the form of various paradoxes. Since there seems to be little hope that Eliezer will publish his [Timeless Decision Theory](https://www.lesswrong.com/lw/135/timeless_decision_theory_problems_i_cant_solve) any time soon, I decided to try to synthesize some of the ideas discussed in this forum, along with a few of my own, into a coherent alternative that is hopefully not so paradox-prone.

I'll start with a way of framing the question. Put yourself in the place of an AI, or more specifically, the decision algorithm of an AI. You have access to your own source code S, plus a bit string X representing all of your memories and sensory data. You have to choose an output string Y. That’s the decision. The question is, how? (The answer isn't “Run S,” because what we want to know is what S should be in the first place.)

Let’s proceed by asking the question, “What are the consequences of S, on input X, returning Y as the output, instead of Z?” To begin with, we'll consider just the consequences of that choice in the realm of abstract computations (i.e. computations considered as mathematical objects rather than as implemented in physical systems). The most immediate consequence is that any program that calls S as a subroutine with X as input, will receive Y as output, instead of Z. What happens next is a bit harder to tell, but supposing that you know something about a program P that call S as a subroutine, you can further deduce the effects of choosing Y versus Z by tracing the difference between the two choices in P’s subsequent execution. We could call these the computational consequences of Y. Suppose you have preferences about the execution of a set of programs, some of which call S as a subroutine, then you can satisfy your preferences directly by choosing the output of S so that those programs will run the way you most prefer.

A more general class of consequences might be called logical consequences. Consider a program P’ that doesn’t call S, but a different subroutine S’ that’s logically equivalent to S. In other words, S’ always produces the same output as S when given the same input. Due to the logical relationship between S and S’, your choice of output for S must also affect the subsequent execution of P’. Another example of a logical relationship is an S' which always returns the first bit of the output of S when given the same input, or one that returns the same output as S on some subset of inputs.

In general, you can’t be certain about the consequences of a choice, because you’re not logically omniscient. How to handle logical/mathematical uncertainty is an [open problem](https://www.lesswrong.com/lw/f9/a_request_for_open_problems/bun), so for now we'll just assume that you have access to a "mathematical intuition subroutine" that somehow allows you to form beliefs about the likely consequences of your choices.

At this point, you might ask, “That’s well and good, but what if my preferences extend beyond abstract computations? What about consequences on the physical universe?” The answer is, we can view the physical universe as a program that runs S as a subroutine, or more generally, view it as a mathematical object which has S embedded within it. (From now on I’ll just refer to programs for simplicity, with the understanding that the subsequent discussion can be generalized to non-computable universes.) Your preferences about the physical universe can be translated into preferences about such a program P and programmed into the AI. The AI, upon receiving an input X, will look into P, determine all the instances where it calls S with input X, and choose the output that optimizes its preferences about the execution of P. If the preferences were translated faithfully, the the AI's decision should also optimize your preferences regarding the physical universe. This faithful translation is a second major open problem.

What if you have some uncertainty about which program our universe corresponds to? In that case, we have to specify preferences for the entire set of programs that our universe may correspond to. If your preferences for what happens in one such program is independent of what happens in another, then we can represent them by a probability distribution on the set of programs plus a utility function on the execution of each individual program. More generally, we can always represent your preferences as a utility function on vectors of the form \<E1, E2, E3, …> where E1 is an execution history of P1, E2 is an execution history of P2, and so on.

These considerations lead to the following design for the decision algorithm S. S is coded with a vector \<P1, P2, P3, ...> of programs that it cares about, and a utility function on vectors of the form \<E1, E2, E3, …> that defines its preferences on how those programs should run. When it receives an input X, it looks inside the programs P1, P2, P3, ..., and uses its "mathematical intuition" to form a probability distribution P\_Y over the set of vectors \<E1, E2, E3, …> for each choice of output string Y. Finally, it outputs a string Y\* that maximizes the expected utility Sum P\_Y(\<E1, E2, E3, …>) U(\<E1, E2, E3, …>). (This specifically assumes that expected utility maximization is the right way to deal with mathematical uncertainty. Consider it a temporary placeholder until that problem is solved. Also, I'm describing the algorithm as a brute force search for simplicity. In reality, you'd probably want it to do something cleverer to find the optimal Y\* more quickly.)

#### Example 1: Counterfactual Mugging ^example-1-counterfactual-mugging

Note that Bayesian updating is not done explicitly in this decision theory. When the decision algorithm receives input X, it may determine that a subset of programs it has preferences about never calls it with X and are also logically independent of its output, and therefore it can safely ignore them when computing the consequences of a choice. There is no need to set the probabilities of those programs to 0 and renormalize.

So, with that in mind, we can model [Counterfactual Mugging](http://wiki.lesswrong.com/wiki/Counterfactual_mugging) by the following Python program:

```python
def P(coin):
    AI_balance = 100
    if coin == "heads":
        if S("heads") == "give $100":
            AI_balance -= 100
    if coin == "tails":
        if Omega_Predict(S, "heads") == "give $100":
            AI_balance += 10000
```

The AI’s goal is to maximize expected utility = .5 \* U(AI\_balance after P("heads")) + .5 \* U(AI\_balance after P("tails")). Assuming U(AI\_balance)=AI\_balance, it’s easy to determine U(AI\_balance after P("heads")) as a function of S’s output. It equals 0 if S(“heads”) == “give $100”, and 100 otherwise. To compute U(AI\_balance after P("tails")), the AI needs to look inside the Omega\_Predict function (not shown here), and try to figure out how accurate it is. Assuming the mathematical intuition module says that choosing “give $100” as the output for S(“heads”) makes it more likely (by a sufficiently large margin) for Omega\_Predict(S, "heads") to output “give $100”, then that choice maximizes expected utility.

#### Example 2: Return of Bayes ^example-2-return-of

This example is based on case 1 in Eliezer's post [Priors as Mathematical Objects](https://www.lesswrong.com/lw/hk/priors_as_mathematical_objects). An urn contains 5 red balls and 5 white balls. The AI is asked to predict the probability of each ball being red as it as drawn from the urn, its goal being to maximize the expected logarithmic score of its predictions. The main point of this example is that this decision theory can reproduce the effect of Bayesian reasoning when the situation calls for it. We can model the scenario using preferences on the following Python program:

```python
def P(n):
    urn = ['red', 'red', 'red', 'red', 'red', 'white', 'white', 'white', 'white', 'white']
    history = []
    score = 0
    while urn:
        i = n%len(urn)
        n = n/len(urn)
        ball = urn[i]
        urn[i:i+1] = []
        prediction = S(history)
        if ball == 'red':
            score += math.log(prediction, 2)
        else:
            score += math.log(1-prediction, 2)
        print (score, ball, prediction)
        history.append(ball)
```

Here is a printout from a sample run, using n=1222222:

```
-1.0 red 0.5
-2.16992500144 red 0.444444444444
-2.84799690655 white 0.375
-3.65535182861 white 0.428571428571
-4.65535182861 red 0.5
-5.9772799235 red 0.4
-7.9772799235 red 0.25
-7.9772799235 white 0.0
-7.9772799235 white 0.0
-7.9772799235 white 0.0
```

S should use deductive reasoning to conclude that returning (number of red balls remaining / total balls remaining) maximizes the average score across the range of possible inputs to P, from n=1 to 10! (representing the possible orders in which the balls are drawn), and do that. Alternatively, S can approximate the correct predictions using brute force: generate a random function from histories to predictions, and compute what the average score would be if it were to implement that function. Repeat this a large number of times and it is likely to find a function that returns values close to the optimum predictions.

#### Example 3: Level IV Multiverse ^example-3-level-iv

In Tegmark's Level 4 [Multiverse](http://space.mit.edu/home/tegmark/multiverse.html), all structures that exist mathematically also exist physically. In this case, we'd need to program the AI with preferences over all mathematical structures, perhaps represented by an ordering or utility function over conjunctions of well-formed sentences in a formal set theory. The AI will then proceed to "optimize" all of mathematics, or at least the parts of math that (A) are logically dependent on its decisions and (B) it can reason or form intuitions about.

I suggest that the Level 4 Multiverse should be considered the default setting for a general decision theory, since we cannot rule out the possibility that all mathematical structures do indeed exist physically, or that we have direct preferences on mathematical structures (in which case there is no need for them to exist "physically"). Clearly, application of decision theory to the Level 4 Multiverse requires that the previously mentioned open problems be solved in their most general forms: how to handle logical uncertainty in any mathematical domain, and how to map fuzzy human preferences to well-defined preferences over the structures of mathematical objects.

**Added:** For further information and additional posts on this decision theory idea, which came to be called "Updateless Decision Theory", please see [its entry](https://wiki.lesswrong.com/wiki/Updateless_decision_theory) in the LessWrong Wiki.
