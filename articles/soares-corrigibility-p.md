---
title: "Corrigibility"
author:
  - "Nate Soares"
source_url: "https://www.lesswrong.com/p/corrigibility"
published: 2015-04-05
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "\"I can't let you do that, Dave.\""
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

A ‘corrigible’ agent is one that [doesn’t interfere](https://arbital.greaterwrong.com/p/nonadversarial?l=7g0) with what [we](https://arbital.greaterwrong.com/p/value_alignment_programmer?l=9r) would intuitively see as attempts to ‘correct’ the agent, or ‘correct’ our mistakes in building it; and permits these ‘corrections’ despite the apparent [instrumentally convergent reasoning](https://arbital.greaterwrong.com/p/instrumental_convergence?l=10g) saying otherwise.

-   If we try to suspend the AI to disk, or shut it down entirely, a corrigible AI will let us do so. (Even though, if suspended, [the AI will then be unable to fulfill what would usually be its goals](https://arbital.greaterwrong.com/p/no_coffee_if_dead?l=7g2).)
    
-   If we try to reprogram the AI’s utility function or meta-utility function, a corrigible AI will allow this modification to go through. (Rather than, e.g., fooling us into believing the utility function was modified successfully, while the AI actually keeps its original utility function as [obscured](https://arbital.greaterwrong.com/p/cognitive_steganography?l=3cq) functionality; as we would expect by default to be [a preferred outcome according to the AI’s current preferences](https://arbital.greaterwrong.com/p/preference_stability?l=3r6).)
    

More abstractly:

-   A corrigible agent experiences no preference or [instrumental pressure](https://arbital.greaterwrong.com/p/instrumental_pressure?l=10k) to interfere with attempts by the programmers or operators to modify the agent, impede its operation, or halt its execution.
    
-   A corrigible agent does not attempt to manipulate or deceive its operators, especially with respect to properties of the agent that might otherwise cause its operators to modify it.
    
-   A corrigible agent does not try to [obscure its thought processes](https://arbital.greaterwrong.com/p/cognitive_steganography?l=3cq) from its programmers or operators.
    
-   A corrigible agent is motivated to preserve the corrigibility of the larger system if that agent self-modifies, constructs sub-agents in the environment, or offloads part of its cognitive processing to external systems; or alternatively, the agent has no preference to execute any of those general activities.
    

A stronger form of corrigibility would require the AI to positively cooperate or assist, such that the AI would rebuild the shutdown button if it were destroyed, or experience a positive preference _not_ to self-modify if self-modification could lead to incorrigibility. But this is not part of the primary specification since it’s possible that we would _not_ want the AI trying to actively be helpful in assisting our attempts to shut it down, and would in fact prefer the AI to be passive about this.

Good proposals for achieving corrigibility in specific regards are [open problems in AI alignment](https://arbital.greaterwrong.com/p/value_alignment_open_problem?l=4m). Some areas of active current research are [Utility indifference](https://arbital.greaterwrong.com/p/utility_indifference?l=1b7) and interruptibility.

Achieving total corrigibility everywhere via some single, general mental state in which the AI “knows that it is still under construction” or “believes that the programmers know more than it does about its own goals” is termed ‘[the hard problem of corrigibility](https://arbital.greaterwrong.com/p/hard_corrigibility?l=3ps)’.

## Difficulties ^difficulties

### Deception and manipulation by default ^deception-and-manipulation-by

By default, most sets of preferences are such that an agent acting according to those preferences will prefer to retain its current preferences. For example, imagine an agent which is attempting to collect stamps. Altering the agent so that it prefers to collect bottle caps would lead to futures where the agent has fewer stamps, and so allowing this event to occur is dispreferred (under the current, stamp-collecting preferences).

More generally, as noted by [instrumentally convergent strategies](https://arbital.greaterwrong.com/p/instrumental_convergence?l=10g), most utility functions give an agent strong incentives to retain its current utility function: imagine an agent constructed so that it acts according to the utility function U, and imagine further that its operators think they built the agent to act according to a different utility function U’. If the agent learns this fact, then it has incentives to either deceive its programmers (prevent them from noticing that the agent is acting according to U instead of U’) or manipulate its programmers (into believing that they actually prefer U to U’, or by coercing them into leaving its utility function intact).

A corrigible agent must avoid these default incentives to manipulate and deceive, but specifying some set of preferences that avoids deception/manipulation incentives remains an open problem.

### Trouble with utility function uncertainty ^trouble-with-utility-function

A first attempt at describing a corrigible agent might involve specifying a utility maximizing agent that is uncertain about its utility function. However, while this could allow the agent to make some changes to its preferences as a result of observations, the agent would still be incorrigible when it came time for the programmers to attempt to correct what they see as mistakes in their attempts to formulate how the “correct” utility function should be determined from interaction with the environment.

As an overly simplistic example, imagine an agent attempting to maximize the internal happiness of all humans, but which has uncertainty about what that means. The operators might believe that if the agent does not act as intended, they can simply express their dissatisfaction and cause it to update. However, if the agent is reasoning according to an impoverished hypothesis space of utility functions, then it may behave quite incorrigibly: say it has narrowed down its consideration to two different hypotheses, one being that a certain type of opiate causes humans to experience maximal pleasure, and the other is that a certain type of stimulant causes humans to experience maximal pleasure. If the agent begins administering opiates to humans, and the humans resist, then the agent may “update” and start administering stimulants instead. But the agent would still be incorrigible — it would resist attempts by the programmers to turn it off so that it stops drugging people.

It does not seem that corrigibility can be trivially solved by specifying agents with uncertainty about their utility function. A corrigible agent must somehow also be able to reason about the fact that the humans themselves might have been confused or incorrect when specifying the process by which the utility function is identified, and so on.

### Trouble with penalty terms ^trouble-with-penalty-terms

A second attempt at describing a corrigible agent might attempt to specify a utility function with “penalty terms” for bad behavior. This is unlikely to work for a number of reasons. First, there is the [Nearest unblocked strategy](https://arbital.greaterwrong.com/p/nearest_unblocked?l=42) problem: if a utility function gives an agent strong incentives to manipulate its operators, then adding a penalty for “manipulation” to the utility function will tend to give the agent strong incentives to cause its operators to do what it would have manipulated them to do, without taking any action that technically triggers the “manipulation” cause. It is likely extremely difficult to specify conditions for “deception” and “manipulation” that actually rule out all undesirable behavior, especially if the agent is [smarter than us](https://arbital.greaterwrong.com/p/unforeseen_maximum?l=47) or [growing in capability](https://arbital.greaterwrong.com/p/context_disaster?l=6q).

More generally, it does not seem like a good policy to construct an agent that searches for positive-utility ways to deceive and manipulate the programmers, [even if those searches are expected to fail](https://arbital.greaterwrong.com/p/nonadversarial?l=7g0). The goal of corrigibility is _not_ to design agents that want to deceive but can’t. Rather, the goal is to construct agents that have no incentives to deceive or manipulate in the first place: a corrigible agent is one that reasons as if it is incomplete and potentially flawed in dangerous ways.

## Open problems ^open-problems

Some open problems in corrigibility are:

### Hard problem of corrigibility ^hard-problem-of-corrigibility

On a human, intuitive level, it seems like there’s a central idea behind corrigibility that seems simple to us: understand that you’re flawed, that your meta-processes might also be flawed, and that there’s another cognitive system over there (the programmer) that’s less flawed, so you should let that cognitive system correct you even if that doesn’t seem like the first-order right thing to do. You shouldn’t disassemble that other cognitive system to update your model in a Bayesian fashion on all possible information that other cognitive system contains; you shouldn’t model how that other cognitive system might optimally correct you and then carry out the correction yourself; you should just let that other cognitive system modify you, without attempting to manipulate how it modifies you to be a better form of ‘correction’.

Formalizing the hard problem of corrigibility seems like it might be a problem that is hard (hence the name). Preliminary research might talk about some obvious ways that we could model A as believing that B has some form of information that A’s preference framework designates as important, and showing what these algorithms actually do and how they fail to solve the hard problem of corrigibility.

### [Utility indifference](https://arbital.greaterwrong.com/p/utility_indifference?l=1b7) ^utility-indifference

explain utility indifference

The current state of technology on this is that the AI behaves as if there’s an absolutely fixed probability of the shutdown button being pressed, and therefore doesn’t try to modify this probability. But then the AI will try to use the shutdown button as an outcome pump. Is there any way to avert this?

### Percentalization ^percentalization

Doing something in the top 0.1% of all actions. This is actually a Limited AI paradigm and ought to go there, not under Corrigibility.

### Conservative strategies ^conservative-strategies

Do something that’s as similar as possible to other outcomes and strategies that have been whitelisted. Also actually a Limited AI paradigm.

This seems like something that could be investigate in practice on e.g. a chess program.

### Low impact measure ^low-impact-measure

(Also really a Limited AI paradigm.)

Figure out a measure of ‘impact’ or ‘side effects’ such that if you tell the AI to paint all cars pink, it just paints all cars pink, and doesn’t transform Jupiter into a computer to figure out how to paint all cars pink, and doesn’t dump toxic runoff from the paint into groundwater; and _also_ doesn’t create utility fog to make it look to people like the cars _haven’t_ been painted pink (in order to minimize this ‘side effect’ of painting the cars pink), and doesn’t let the car-painting machines run wild afterward in order to minimize its own actions on the car-painting machines. Roughly, try to actually formalize the notion of “Just paint the cars pink with a minimum of side effects, dammit.”

It seems likely that this problem could turn out to be FAI-complete, if for example “Cure cancer, but then it’s okay if that causes human research investment into curing cancer to decrease” is only distinguishable by us as an okay side effect because it doesn’t result in expected utility decrease under our own desires.

It still seems like it might be good to, e.g., try to define “low side effect” or “low impact” inside the context of a generic Dynamic Bayes Net, and see if maybe we can find something after all that yields our intuitively desired behavior or helps to get closer to it.

### Ambiguity identification ^ambiguity-identification

When there’s more than one thing the user could have meant, ask the user rather than optimizing the mixture. Even if A is in some sense a ‘simpler’ concept to classify the data than B, notice if B is also a ‘very plausible’ way to classify the data, and ask the user if they meant A or B. The goal here is to, in the classic ‘tank classifier’ problem where the tanks were photographed in lower-level illumination than the non-tanks, have something that asks the user, “Did you mean to detect tanks or low light or ‘tanks and low light’ or what?”

### Safe outcome prediction and description ^safe-outcome-prediction-and

Communicate the AI’s predicted result of some action to the user, without putting the user inside an unshielded argmax of maximally effective communication.

### Competence aversion ^competence-aversion

To build e.g. a [behaviorist genie](https://arbital.greaterwrong.com/p/behaviorist?l=102), we need to have the AI e.g. not experience an instrumental incentive to get better at modeling minds, or refer mind-modeling problems to subagents, etcetera. The general subproblem might be ‘averting the instrumental pressure to become good at modeling a particular aspect of reality’. A toy problem might be an AI that in general wants to get the gold in a Wumpus problem, but doesn’t experience an instrumental pressure to know the state of the upper-right-hand-corner cell in particular.
