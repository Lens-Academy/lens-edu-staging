---
title: "A very non-technical explanation of the basics of infra-Bayesianism"
author:
  - "David Matolcsi"
source_url: "https://www.lesswrong.com/posts/NdJsWDS7Aq4xqoumk/a-very-non-technical-explanation-of-the-basics-of-infra"
published: 2023-04-26
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "As a response to John Wentworth's public request, I try to explain the basic structure of infra-Bayesian decision-making in a nutshell.…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

# **Introduction** ^introduction

As a response to John Wentworth's [public request](https://www.lesswrong.com/posts/ig62gqK2xRPv79Wsr/usd500-bounty-contest-explain-infra-bayes-in-the-language-of), I try to explain the basic structure of infra-Bayesian decision-making in a nutshell. Be warned that I significantly simplify some things, but I hope it gives roughly the right picture.

This post is mostly an abridged version of my previous post [Performance guarantees in classical learning and infra-Bayesianism](https://www.lesswrong.com/posts/q6dQpSfNHCYzKb2mf/performance-guarantees-in-classical-learning-theory-and). If you are interested in the more detailed and less sloppy version, you can read it there, it's a little more technical, but still accessible without serious background knowledge. 

I also wrote up my general [thoughts and criticism](https://www.lesswrong.com/posts/StkjjQyKwg7hZjcGB/a-mostly-critical-review-of-infra-bayesianism) on infra-Bayesianism, and a shorter [post](https://www.lesswrong.com/posts/yykNvq257zBLDNmJo/infra-bayesianism-naturally-leads-to-the-monotonicity) explaining how infra-Bayesianism leads to the monotonicity principle.

# **Classical learning theory** ^classical-learning-theory

[Infra-Bayesianism](https://www.lesswrong.com/posts/zB4f7QqKhBHa5b37a/introduction-to-the-infra-bayesianism-sequence) was created to address some weak spots in classical learning theory. Thus, we must start by briefly talking about learning theory in general.

In classical learning theory, the agent has a hypothesis class, each hypothesis giving a full description of the environment. The agent interacts with the environment for a long time, slowly accumulating loss corresponding to certain events. The agent has a time discount rate $\gamma$ , and its overall life-time loss is calculated by weighing the losses it receives through its history by this time discount.

The regret of an agent in environment $e$ is the difference between the loss the agent actually receives through its life, and the loss it would receive if it followed the policy that is optimal for the environment $e$.

We say that a policy successfully learns a hypothesis class $H$, if it has low expected regret with respect to every environment $e$ described in the hypothesis class.

How can a policy achieve this? In the beginning, the agent takes exploratory steps and observes the environment. If the observations are much more likely in environment $e_1$ than in environment $e_2$, then the agent starts acting in ways that make more sense in environment $e_1$, and starts paying less attention to what would be a good choice in $e_2$. This works well, because it doesn't cause much expected regret in $e_2$ if the policy starts making bad choices in situations that are very unlikely to occur in $e_2$: by definition, this only rarely causes problems.

Bayesian updating is a special case of this: originally, there is a prior on every hypothesis, then it's updated by how unlikely the observations are according to the particular hypothesis.

But this is just one possible way of learning. Assume that the hypothesis class $H$ has certain favorable properties (it excludes [traps](https://www.lesswrong.com/posts/StkjjQyKwg7hZjcGB/a-mostly-critical-review-of-infra-bayesianism#Traps_)), and the discount rate $\gamma$ is close to $1$, that is, the agent can be patient and devote a long time to exploration. Then, there are many algorithms that do a reasonably good job at learning: whichever $e\in H$ environment the agent is placed at, it will have low expected regret compared to the best possible policy in $e$.

# **The non-realizability problem** ^the-non-realizability-problem

So we selected a policy that has low expected regret in every environment in the hypothesis class. Unfortunately, we still don't know anything about how this policy does in environments that are not in the hypothesis class (technical term: the environment is [non-realizable](https://www.lesswrong.com/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version#3_1__Realizability)). This is a big problem, because it's certain that in real life, the true environment will not be in the agent's hypothesis class. First, because it's just practically impossible to have a full model of the world, down to the atomic level. Second, the environment includes the agent itself, which makes this theoretically impossible too.

Let's look at a simple example. The agent observes a sequence of $0$s and $1$s, and is tasked with predicting the next token (it gets $0$ loss for guessing correctly, and $1$ loss for incorrectly, and it has a shallow discount rate, which means it has  a long time for learning).

The agent has only a limited hypothesis class, it only contains hypotheses that claim that the observed sequence is produced by a finite-state machine (with an output function and with a potentially probabilistic transition function). It even selected a policy that has low regret in all these environments.

Meanwhile, the actual sequence it observes is $1$ for [square-free](https://en.wikipedia.org/wiki/Square-free_integer) indices and $0$ otherwise. Do we have any guarantee that the agent will do reasonably well in this environment?

Unfortunately, not. For every reasonable policy, one can attach to it this extra condition: "If you observed the square-free sequence so far, then guess  $0$ on square-free indices and   $1$ otherwise". It's the exact opposite of what it should be doing.

This is really dumb. Maybe we shouldn't expect it to do a perfect job in predicting the sequence, but in the observed sequence so far every fourth bit was $0$, and the agent is observing this pattern for millions of bits, surely it should pick up on that and guess at least the fourth bits correctly. Or at least do something equally good as predicting the fourth bits, instead of just completely failing.

On the other hand, this additional failure mode condition wouldn't make the policy significantly worse in any of the environments in its hypothesis class. No finite state machine produces the square-free sequence for too long, so the policy having this failure mode on the square-free sequence doesn't cause significant expected regret for any sequence in the hypothesis class (assuming the time discount $\gamma\to 1$.)

Why would a policy have a failure mode like that? Well, there is no clear reason for that, and if there is a failure in real life, it probably won't look like "the policy almost always behaves reasonably, but goes crazy on one particular sequence, the square-free one". But this example is intended to show that theoretically it can happen, we have no performance guarantee on environments outside the hypothesis class. So this simplistic toy example demonstrates that a policy having low regret on a relatively broad hypothesis class (like sequences produced by finite state automatons) doesn't guarantee that it won't behave in really stupid ways in an environment outside the hypothesis class (like keep guessing always wrong, even though at least learning that the fourth bits are $0$ should be really simple). In my [longer post](https://www.lesswrong.com/posts/q6dQpSfNHCYzKb2mf/performance-guarantees-in-classical-learning-theory-and), I give some more examples and define the terms more precisely.

At this point, we might ask how likely it is for a policy selected to do well on a class of environments to do very stupid things in the environment we actually deploy it in. This depends on the specific way we select the policy, what the hypothesis class and the real environment exactly are, and what we mean by "very stupid things".

But Vanessa's agenda is more ambitious and more theoretical than that, and asks whether we can construct a new learning theory, in which a not-extremely-broad hypothesis class can be enough to really guarantee that the agent doesn't do very stupid things in any environment.

# **Infra-Bayesianism** ^infra-bayesianism

An infra-Bayesian learning agent assumes that the environment is controlled by a malevolent deity, Murphy. Murphy wants the agent to receive the maximum possible life-time loss (calculated with the time discount $\gamma$), and Murphy can read the agent's mind and knows its full policy from the beginning. 

However, Murphy's actions are constrained by some law. The agent originally doesn't know what this law is, that's what it needs to learn over the course of its life. Accordingly, the agent's hypothesis class doesn't range over descriptions of "what the world is like" but over laws "how Murphy is constrained". 

The agent selects a policy that has low regret with respect to every law $\Theta$ in its hypothesis class. Regret is defined as the difference between the actual loss received and the loss that the optimal policy chosen for $\Theta$ would receive against Murphy if Murphy was constrained only by the law $\Theta$. There are theorems showing that for some pretty broad hypothesis classes of laws we can select a policy that has low regret with respect to all of them (as $\gamma\to 1$). 

It's useful to note here that the laws can also be probabilistic in nature. For example: "On the seventh digits, Murphy can choose the probability of $0$ being displayed between $17\%$ and $39\%$. Then the actual bit is randomly generated based on the probability Murphy chose."

Here is where convex sets come in: The law constrains Murphy to choose the probability distribution of outcomes from a certain set in the space of probability distributions. Whatever the loss function is, the worst probability distribution Murphy can choose from the set is the same as he could choose from the convex hull of the set. So we might as well start by saying that the law must be constraining Murphy to a convex set of probability distributions.

Go back to our previous example of an agent doing sequence-prediction of the square-free sequence. The agent has this relatively narrow hypothesis class: "There is a finite-state machine (with a potentially probabilistic transition function) whose states are assigned to $0, 1$ or $X$. If the state is assigned to is $0$ or $1$, then Murphy is constrained to show that as the next bit of the sequence. If the state is assigned to $X$, Murphy can choose the next bit." There is a theorem that shows that there can be policies that have low regret with respect to all these hypotheses (as $\gamma\to 1$). Assume the agent has a policy like that.

Initially, the agent guesses the next bits randomly. It observes that it sometimes succeeds, something that wouldn't happen if Murphy was totally unconstrained. So it can rule out this hypothesis. As time goes on, it observes that every fourth bit is $0$, so it tries guessing $0$ on fourth bits... and it gets it right! Murphy knows the agent's full policy, so the fact that the agent can successfully guess the fourth digits suggests that Murphy is constrained on the fourth bits to output $0$. This way, the agent starts to pay more attention to hypotheses that correctly predict real patterns in the sequence (like every fourth and ninth digit being $0$), and starts to act accordingly (by guessing $0$ on these bits). It's important to remember though that Murphy plans for the long-run and can read the agent's full policy, so the agent needs to keep an eye out for the possibility that Murphy is not actually constrained in this way, just wants to teach the agent the wrong lesson as part of a long-term plot. So the agent might need to revise this hypothesis when things start to go wrong, but until the $0$s keep reliably coming on the fourth digits, it makes sense to guess that.

Can the same problem arise as before? Namely, that the agent just has a failure mode on observing the square-free sequence, which just makes it act stupidly.

Well, it depends on how stupidly. It's still not guaranteed that the agent successfully "learns" the pattern to always guess $0$ on the fourth digits. In fact, we can prove that it's still possible that it guesses $1$ for every digit if it observes the square-free sequence.

But always guessing $1$ would at least mean getting lots of digits right (even if not the fourth digits). That's something we actually have a performance guarantee for: if an infra-Bayesian agent observes a sequence where every fourth digit is $0$, then it is guaranteed to get at least $\frac{1}{4}$ of the digits right.

Otherwise, if observing the square-free sequence produced such a serious failure mode that would make the agent guess less than $\frac{1}{4}$ of the digits right, then if Murphy was only constrained by the law "every fourth digit must be $0$", then Murphy would intentionally produce the square-free sequence to induce the failure mode. That would mean that a policy with a failure mode like that would have a non-negligible regret with respect to the law "every fourth digit must be $0$", as it does significantly worse than the optimal policy of always guessing  $0$ on the fourth digits. However, we assumed that the policy has low regret with respect to every law in its hypothesis class, and this simple law is included in that. Contradiction.

Thus, we proved that an infra-Bayesian learning agent with a relatively narrow hypothesis class will always guess at least $\frac{1}{4}$ of the digits right if it observes a sequence in which every fourth digit is $0$. I'm only moderately satisfied with this result, it would have felt more natural to prove that it will learn to get the actual fourth digits right, but that's not true. Still, even this performance guarantee is better than what we get from classical learning theory.

(Also, Vanessa has a different intuition here and doesn't think that correctly predicting the fourth bits would have been a more natural goal than just getting  $\frac{1}{4}$ of the digits right somewhere. "Rationality is systematized winning: Ultimately, what's important is how overall successful the agent is at achieving its goals, and the particular actions the agent takes are instrumental." That's also  a fair point.)

# **The results of infra-Bayesianism** ^the-results-of-infra-bayesianism

John's request was to explain "the major high-level definitions and results in infra-Bayes to date". I really don't know of many "major high-level results".

To the best of my knowledge, the main motivation behind the development of infra-Bayesianism was that it helps with the non-realizability problem, that is, the above-described example generalizes to other situations, and we can prove interesting performance guarantees in general environments if we just assume that the infra-Bayesian agent has low regret on a relatively narrow hypothesis class. I don't know of strong results about this yet, and I'm relatively skeptical whether we will get further with the research of performance guarantees. You can read more details in my longer, technical [post](https://www.lesswrong.com/posts/q6dQpSfNHCYzKb2mf/performance-guarantees-in-classical-learning-theory-and).

## **Newcomb's problem** ^newcombs-problem

_(lower confidence, this was not my research direction)_

In [Newcomb's problem](https://en.wikipedia.org/wiki/Newcomb%27s_paradox), it's just really convenient that we are already assuming that the environment is controlled by Murphy _who knows the agent's full policy from the beginning, effectively reading its mind._

We can include some laws in the hypothesis class that say that if Murphy doesn't fill box $A$ but the agent still one-boxes in that turn, then all the agent's losses are wiped out forever. I feel that including this is kind of hacky, but it feels less hacky in the more general framework where we are talking about measures instead of probability distributions, and a law like this can be relatively naturally encoded in that framework.

If the agent has some laws like that in its hypothesis class, then it will do some exploratory steps where it just one-boxes to see what happens.

If there is no correlation between one-boxing and finding treasure (as it's usually the case in our world), it soon learns not to leave money-boxes unopened and does exploratory one-boxing just very very occasionally.

On the other hand, if it's actually playing against Omega in Newcomb's game, then it will soon realize that the law in its hypothesis class that best explains the observations is the one according to which every time it decides to one-box, Murphy fills the box with treasure, otherwise all the loss would be wiped out which Murphy really wants to avoid.

I'm unsure how I feel about this solution to Newcomb's problem, but I think I agree with the main point: you are not born knowing how the game works and what the good action is, you learn it from playing the game yourself or watching others play. And infra-Bayesianism gives a relatively natural framework for learning the right lesson that you should one-box.

If you want to learn more about this, I recommend Thomas Larsen's relatively beginner-friendly [explanation](https://www.lesswrong.com/posts/DMoiZDYZzqknfvoHh/infra-bayesianism-distillation-realizability-and-decision#Application_to_Decision_Theory_Problems). Note that his post still relies on the older framework in which agents had utilities and not losses, so "all the loss is wiped out" is equivalent to "the agent receives infinite utility". This made the previous formalism somewhat more contrived than it currently is.

## **Other results** ^other-results

I really don't know about other results building on infra-Bayesianism. Infra-Bayesian logic and Infra-Bayesian Physicalism exist, but they feel like mostly separate fields that only borrow some mathematical formalism from the original infra-Bayes, and they can't be easily explained based on the non-formalized version of infra-Bayes I presented above. Also, as far as I know, they didn't really produce any actual results yet. 

Maybe the other mentees who looked into other parts of infra-Bayesianism can link results in the comments if they find something I missed.
