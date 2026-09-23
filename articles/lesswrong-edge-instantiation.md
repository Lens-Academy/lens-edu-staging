---
title: "Edge instantiation"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/edge-instantiation"
published: 2016-03-12
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "The edge instantiation problem is a hypothesized patch-resistant problem for safe value loading in advanced agent scenarios where, for most utility functions we might try to formalize or teach, the maximum of the agent's utility function will end up lying at an edge of the solution space that is a 'weird extreme' from our perspective."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

The edge instantiation problem is a hypothesized [patch-resistant problem](https://www.lesswrong.com/w/patch-resistance) for [safe](https://www.lesswrong.com/w/advanced-safety) [value loading](https://www.lesswrong.com/w/value-loading) in [advanced agent scenarios](https://www.lesswrong.com/w/advanced-agent-properties) where, for most utility functions we might try to formalize or teach, the maximum of the agent's utility function will end up lying at an edge of the solution space that is a 'weird extreme' from our perspective.

## Definition ^definition

On many classes of problems, the maximizing solution tends to lie at an extreme edge of the solution space. This means that if we have an intuitive outcome X in mind and try to obtain it by giving an agent a solution fitness function F that sounds like it should assign X a high value, the maximum of F may be at an extreme edge of the solution space that looks to us like a very unnatural instance of X, or not an X at all. The Edge Instantiation problem is a specialization of [unforeseen maximization](https://www.lesswrong.com/w/unforeseen-maximization) which in turn specializes Bostrom's [perverse instantiation](https://www.lesswrong.com/w/perverse-instantiation) class of problems.

It is hypothesized (by e.g. [Yudkowsky](https://www.lesswrong.com/users/eliezer_yudkowsky)) that many classes of solution that have been proposed to [patch](https://www.lesswrong.com/w/patch-resistance) Edge Instantiation would fail to resolve the entire problem and that further Edge Instantiation problems would remain. For example, even if we consider a [satisficing](https://www.lesswrong.com/w/satisficing) utility function with only values 0 and 1 where 'typical' X has value 1 and no higher score is possible, an expected utility maximizer could still end up deploying an extreme strategy in order to maximize the _probability_ that a satisfactory outcome is obtained. Considering several proposed solutions like this and their failures suggests that Edge Instantiation is a [resistant](https://www.lesswrong.com/w/patch-resistance) (not ultimately unsolvable, but with many attractive-seeming solutions failing to work) for the deep reason that many possible stages of an agent's cognition would potentially rank solutions and choose very-high-ranking solutions.

The proposition defined is true if Edge Instantiation does in fact surface as a pragmatically important problem for advanced agent scenarios, and would in fact resurface in the face of most 'naive' attempts to correct it. The proposition is not that the Edge Instantiation Problem is unresolvable, but that it's real, important, doesn't have a _simple_ answer, and resists most simple attempts to patch it.

### Example 1: Smiling faces ^example-1-smiling-faces

When Bill Hibbard was first beginning to consider the value alignment problem, he suggested giving AIs the goals of making humans smile, a goal that could be trained by recognizing pictures of smiling humans, and was intended to elicit human happiness. Yudkowsky replied by suggesting that the true behavior elicited would be to tile the future light cone with tiny molecular smiley faces. This is not because the agent was perverse, but because among the set of all objects that look like smiley faces, the solution with the most extreme value for achievable numerosity (that is, the strategy which creates the largest possible number of smiling faces) also sets the value for the size of individual smiling faces to an extremely small diameter. The tiniest possible smiling faces are very unlike the archetypal examples of smiling faces that we had in mind when specifying the utility function; from a human perspective, the intuitively intended meaning has been replaced by a weird extreme.

Stuart Russell observes that maximizing some aspects of a solution tends to set all unconstrained aspects of the solution to extreme values. The solution that maximizes the number of smiles minimizes the size of each individual smile. The bad-seeming result is not just an accidental outcome of mere ambiguity in the instructions. The problem wasn't just that a wide range of possibilities corresponded to 'smiles' and a randomly selected possibility from this space surprised us by not being the central example we originally had in mind. Rather, there's a systematic tendency for the highest-scoring solution to occupy an extreme edge of the solution space, which means that we are _systematically_ likely to see 'extreme' or 'weird' solutions rather than the 'normal' examples we had in mind.

### Example 2: Sorcerer's Apprentice ^example-2-sorcerers-apprentice

In the hypothetical Sorcerer's Apprentice scenario, you instruct an artificial agent to add water to a cauldron, and it floods the entire workplace. Hypothetically, you had in mind only adding enough water to fill the cauldron and then stopping, but some stage of the agent's solution-finding process optimized on a step where 'flooding the workplace' scored higher than 'add 4 buckets of water and then shut down safely', even though both of these qualify as 'filling the cauldron'.

This could be because (in the most naive case) the utility function you gave the agent was increasing in the amount of water in contiguous contact with the cauldron's interior - you gave it a utility function that implied 4 buckets of water were good and 4,000 buckets of water were better.

Suppose that, having foreseen in advance the above possible disaster, you try to [patch](https://www.lesswrong.com/w/patch-resistance) the agent by instructing it not to move more than 50 kilograms of material total. The agent promptly begins to build subagents (with the agent's own motions to build subagents moving only 50 kilograms of material) which build further agents and again flood the workplace. You have run into a [Nearest Unblocked Neighbor](https://www.lesswrong.com/w/nearest-unblocked-strategy) problem; when you excluded one extreme solution, the result was not the central-feeling 'normal' example you originally had in mind. Instead, the new maximum lay on a new extreme edge of the solution space.

Another solution might be to define what you thought was a satisficing agent, with a utility function that assigned 1 in all cases where there were at least 4 buckets of water in the cauldron and 0 otherwise. The agent then calculates that it could increase the _probability_ of this condition obtaining from 99.9% to 99.99% by replicating subagents and repeatedly filling the cauldron, just in case one agent malfunctions or something else tries to remove water from the cauldron. Since 0.9999 > 0.999, there is then a more extreme solution with greater _expected_ utility, even though the utility function itself is binary and satisficing.

## Premises ^premises

### Assumes: Orthogonality thesis ^assumes-orthogonality-thesis

As with most aspects of the value loading problem, [Orthogonality Thesis](https://www.lesswrong.com/w/orthogonality-thesis) is an implicit premise of the Edge Instantiation problem; for Edge Instantiation to be a problem for advanced agents implies that 'what we really meant' or the outcomes of highest [normative value](https://www.lesswrong.com/w/normative-value) are not inherently picked out by every possible maximizing process; and that most possible utility functions do not care 'what we really meant' unless explicitly constructed to have a [do what I mean](https://www.lesswrong.com/w/do-what-i-mean) behavior.

### Assumes: Complexity of values ^assumes-complexity-of-values

If normative values were extremely simple (of very low algorithmic complexity), then they could be formally specified in full, and the most extreme strategy that scored highest on this formal measure simply _would_ correspond with what we really wanted, with no downsides that hadn't been taken into account in the score.

## Arguments ^arguments

### Interaction with nearest unblocked neighbor ^interaction-with-nearest-unblocked

The Edge Instantiation problem has the [Nearest unblocked strategy](https://www.lesswrong.com/w/nearest-unblocked-strategy) pattern. If you foresee one specific 'perverse' instantiation and try to prohibit it, the maximum over the remaining solution space is again likely to be at another extreme edge of the solution space that again seems 'perverse'.

### Interaction with cognitive uncontainability of advanced agents ^interaction-with-cognitive-uncontainabil

Advanced agents search larger solution spaces than we do. Therefore the project of trying to visualize all the strategies that might fit a utility function, to try to verify in our own minds that the maximum is somewhere safe, seems exceptionally untrustworthy (not [Advanced safety](https://www.lesswrong.com/w/advanced-safety)).

### Interaction with context change problem ^interaction-with-context-change

Agents that acquire new strategic options or become able to search a wider range of the solution space may go from having only apparently 'normal' solutions to apparently 'extreme' solutions. This is known as the [context change problem](https://www.lesswrong.com/w/context-disaster). For example, an agent that inductively learns human smiles as a component of its utility function, might as a non-advanced agent have access only to strategies that make humans happy in an intuitive sense (thereby producing the apparent observation that everything is going fine and the agent is working as intended), and then after self-improvement, acquire as an advanced agent the strategic option of transforming the future light cone into tiny molecular smileyfaces.

### Strong pressures can arise at any stage of optimization ^strong-pressures-can-arise

Suppose you tried to build an agent that was an _expected_ utility satisficer - rather than having a 0-1 utility function and thus chasing probabilities of goal satisfaction ever closer to 1, the agent searches for strategies that have at least 0.999 _expected_ utility. Why doesn't this resolve the problem?

A bounded satisficer doesn't _rule out_ the solution of filling the room with water, since this solution also has >0.999 expected utility. It only requires the agent to carry out one cognitive algorithm which has at least one maximizing or highly optimizing stage, in order for 'fill the room with water' to be preferred to 'add 4 buckets and shut down safely' on that stage (while being equally acceptable at future satisficing stages). E.g., maybe you build an expected utility satisficer and still end up with an extreme result because one of the cognitive algorithms suggesting solutions was trying to minimize its own disk space usage.

On a meta-level, we may run into problems of [71](https://www.lesswrong.com/w/71) for [reflective agents](https://www.lesswrong.com/w/reflective-agents). Maybe one simple way of obtaining at least 0.999 expected utility is to create a subagent that _maximizes_ expected utility? It seems intuitively clear why bounded maximizers would build boundedly maximizing offspring, but a bounded satisficer doesn't need to build boundedly satisficing offspring - a bounded maximizer might also be 'good enough'. (In the current theory of TilingAgents, we can prove that an expected utility satisficer can tile to an expected utility satisficer with some surprising caveats, but the problem is that it can tile to other things _besides_ an expected utility satisficer.)

Since it seems very easy for at least one stage of a self-modifying agent to end up preferring solutions that have higher scores relative to some scoring rule, the [edge instantiation](https://www.lesswrong.com/w/edgeinstantiation) problem can be expected to resist naive attempts to describe an agent that seems to have an overall behavior of 'not trying quite so hard'. It's also not clear how to make the instruction 'don't try so hard' be ReflectivelyConsistent, or apply to every part of a considered subagent. This is also why [limited optimization](https://www.lesswrong.com/w/limited-optimization) is an open problem.

Dispreferring solutions with 'extreme impacts' in general is the open problem of [low impact AI](https://www.lesswrong.com/w/low-impact-ai). Currently, no formalizable utility function is known that plausibly has the right intuitive meaning for this. (We're working on it.) Also note that not every extreme 'technically an X' that we think is 'not really an X' has an extreme causal impact in an intuitive sense, so not every case of the Edge Instantiation problem is blocked by dispreferring greater impacts.

## Implications ^implications

### One of limited optimization, low Impact, or full coverage value loading seems critical for real-world agents ^one-of-limited-optimization

As Stuart Russell observes, solving an optimization problem where only some values are constrained or maximized, will tend to set unconstrained variables to extreme values. The universe containing the maximum possible number of [paperclips](https://www.lesswrong.com/w/paperclip-maximizer) contains no humans; optimizing for as much human safety as possible will drive human freedom to zero.

Then we must apparently do at least one of the following:

1.  Build [full coverage](https://www.lesswrong.com/w/full-coverage) advanced agents whose utility functions lead them to terminally disprefer stomping on every aspect of value that we care about (or would care about under reflection). In a full coverage agent there are no unconstrained variables _that we care about_ to be set to extreme values that we would dislike; the AI's goal system knows and cares about _all_ of these. It will not set human freedom to an extremely low value in the course of following an instruction to optimize human safety, because it knows about human freedom and literally everything else.
2.  Build [powerful agents](https://www.lesswrong.com/w/relevant-powerful-agent) that are [limited optimizers](https://www.lesswrong.com/w/limited-optimizers) which predictably invent only solutions we intuitively consider 'non-extreme', whose optimizations are such as to not drive to an extreme on any substage. This leaves us with just ambiguity as a (severe) problem, but at least averts a systematic drive toward extremes that will systematically 'exploit' that ambiguity.
3.  Build [powerful agents](https://www.lesswrong.com/w/relevant-powerful-agent) that are [low impact](https://www.lesswrong.com/w/low-impact) and prefer to avoid solutions that produce greater impacts on _anything_ we intuitively see as an important predicate, including both everything we value and a great many more things we don't particularly value.
4.  Find some other escape route from the [value achievement problem](https://www.lesswrong.com/w/value-achievement-dilemma).

### Insufficiently cautious attempts to build advanced agents are likely to be highly destructive ^insufficiently-cautious-attempts-to

Edge Instantiation is one of the contributing reasons why value loading is hard and naive solutions end up doing the equivalent of tiling the future light cone with paperclips.

We've previously observed certain parties proposing utility functions for advanced agents that seem obviously subject to the Edge Instantiation problem. Confronted with the obvious disaster forecast, they propose [patching](https://www.lesswrong.com/w/patch-resistance) the utility function to eliminate that particular scenario (or rather, say that of course they would have written the utility function to exclude that scenario) or claim that the agent will not 'misinterpret' the instructions so egregiously (denying the [Orthogonality Thesis](https://www.lesswrong.com/w/orthogonality-thesis) at least to the extent of proposing a universal preference for interpreting instructions 'as intended'). Mistakes of this type also belong to a class that potentially wouldn't show up during early stages of the AI, or would show up in an initially noncatastrophic way that seemed easily patched, so people advocating an [empirical first methodology](https://www.lesswrong.com/w/empirical-first-methodology) would falsely believe that they had learned to handle them or eliminated all such tendencies already.

Thus the problem of Edge Instantiation (which is much less severe for nonadvanced agents than advanced agents, will not be solved in the advanced stage by patches that seem to fix weak early problems, and has empirically appeared in proposals by multiple speakers who rejected attempts to point out the Edge Instantiation problem) is a significant contributing factor to the overall expectation that the default outcome of developing advanced agents with current attitudes is disastrous.

### Relative to current attitudes, small increases in safety awareness do not produce significantly less destructive final outcomes ^relative-to-current-attitudes

Simple patches to Edge Instantiation fail and the only currently known approaches would take a lot of work to solve problems like [limited optimization](https://www.lesswrong.com/w/limited-optimization) or [full coverage](https://www.lesswrong.com/w/full-coverage) that are hard for deep reasons. In other words, Edge Instantiation does not appear to be the sort of problem that an AI project can easily avoid just by being made aware of it. (E.g. MIRI knows about it but hasn't yet come up with any solution, let alone one easily patched on to any cognitive architecture.)

This is one of the factors contributing to the general assessment that the curve of outcome goodness as a function of effort is flat for a significant distance around current levels of effort.
