---
title: "Sufficiently optimized agents appear coherent"
author:
  - "Eliezer Yudkowsky, et al."
source_url: "https://www.lesswrong.com/w/sufficiently-optimized-agents-appear-coherent"
published: 2025-11-05
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Argues that optimization processes strong and general enough to eliminate qualitatively self-destructive behaviors (such as circular preferences or exploitable Allais-paradox-style choices) should produce agents that appear Bayesian-coherent, since humanly-predictable coherence violations are also cheap for the agent itself to eliminate."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Arguments ^arguments

Summary: Violations of coherence constraints in probability theory and decision theory correspond to qualitatively destructive or dominated behaviors. Coherence violations so easily computed as to be humanly predictable should be eliminated by optimization strong enough and general enough to reliably eliminate behaviors that are qualitatively dominated by cheaply computable alternatives. From our perspective, this should produce agents such that, _ceteris paribus_, we do not think we can predict, in advance, any coherence violation in their behavior.

### Coherence violations correspond to qualitatively destructive behaviors ^coherence-violations-correspond-to

There is a correspondence between, on the one hand, thought processes that seem to violate intuitively appealing coherence constraints from the Bayesian family, and on the other hand, sequences of overt behaviors that leave the agent qualitatively worse off than before or that seem intuitively dominated by other behaviors.

For example, suppose you claim that you prefer A to B, B to C, and C to A. This 'circular preference' (A > B > C > A) seems intuitively unappealing; we can also see how to visualize it as an agent with a qualitatively self-destructive behavior as follows:

-   You prefer to be in San Francisco rather than Berkeley, and if you are in Berkeley, you will pay $50 for a taxi ride to San Francisco. (So far, no problem.)
-   You prefer San Jose to San Francisco, and if in San Francisco, you will pay $50 to go to San Jose. (Still no problem so far.)
-   You like Berkeley more than San Jose, and if in San Jose will pay $50 to go to Berkeley.

The corresponding agent will spend $150 on taxi rides and then end up in the same position, perhaps ready to spend even more money on taxi rides. The agent is strictly, qualitatively worse off than before. We can see this, in some sense, even though the agent's preferences are partially incoherent. Assuming the agent has a coherent preference for money or something that can be bought with money, alongside its incoherent preference for location, then the circular trip has left it strictly worse off (since in the end the location was unchanged). The circular trip is still dominated by the option of staying in the same place.

(The above is a variant of an argument first presented by Steve Omohundro.)

(Phenomena like this, known as 'preference reversals', are a common empirical finding in behavioral psychology. Since a human mind is an ever-changing balance of drives and desires that can be heightened or weakened by changes of environmental context, eliciting inconsistent sets of preferences from humans isn't hard and can consistently be done in the laboratory in economics experiments, especially if the circularity is buried among other questions or distractors.)

As another illustration, consider the Allais paradox. As a simplified example, consider offering subjects a choice between hypothetical Gamble 1A, a certainty of receiving $1 million if a die comes up anywhere from 00-99, and Gamble 1B, a 10% chance of receiving nothing (if the die comes up 00-09) and a 90% chance of receiving $5 million (if the die comes up 10-99). Most subjects choose Gamble 1A. So far, we have a scenario that could be consistent with a coherent utility function in which the interval of desirability from receiving $0 to receiving $1 million is more than nine times the interval from receiving $1 million to receiving $5 million.

However, suppose only half the subjects are randomly assigned to this condition, and the other half are asked to choose between Gamble 2A, a 90% chance of receiving nothing (00-89) and a 10% chance of receiving $1 million (90-99), versus Gamble 2B, a 91% chance of receiving nothing (00-90) and a 9% chance of receiving $5 million (91-99). Most subjects in this case will pick Gamble 2B. This combination of results guarantees that at least some subjects must behave in a way that doesn't correspond to any consistent utility function over outcomes.

The Allais Paradox (in a slightly different formulation) was initially celebrated as showing that humans don't obey the expected utility axioms, and it was thought that maybe the expected utility axioms were 'wrong' in some sense. However, in accordance with the standard families of coherence theorems, we can crank the coherence violation to exhibit a qualitatively dominated behavior:

Suppose you show me a switch, set to "A", that determines whether I will get Gamble 2A or Gamble 2B. You offer me a chance to pay you one penny to throw the switch from A to B, so I do so (I now have a 91% chance of nothing, and a 9% chance of $5 million). Then you roll one of two ten-sided dice to determine the percentile result, and the first die, the tens digit, comes up "9". Before rolling the second die, you offer to throw the switch back from B to A in exchange for another penny. Since the result of the first die transforms the experiment into Gamble 1A vs. 1B, I take your offer. You now have my two cents on the subject. (If the result of the first die is anything but 9, I am indifferent to the setting of the switch since I receive $0 either way.)

Again, we see a manifestation of a powerful family of theorems showing that agents that cannot be seen as corresponding to any coherent probabilities and consistent utility function will exhibit qualitatively destructive behavior, like paying someone a cent to throw a switch and then paying them another cent to throw it back.

There is a large literature on different sets of coherence constraints that all yield expected utility, starting with the Von Neumann-Morgenstern Theorem. No other decision formalism has comparable support from so many families of differently phrased coherence constraints.

There is similarly a large literature on many classes of coherence arguments that yield classical probability theory, such as the Dutch Book theorems. There is no substantively different rival to probability theory and decision theory that is competitive when it comes to (a) plausibly having some bounded analogue which could appear to describe the uncertainty of a powerful cognitive agent, and (b) seeming highly motivated by coherence constraints, that is, being forced by the absence of qualitatively harmful behaviors that correspond to coherence violations.

### Generic optimization pressures, if sufficiently strong and general, should be expected to eliminate behaviors that are dominated by clearly visible alternatives. ^generic-optimization-pressures-if

Even an incoherent collection of shifting drives and desires may well recognize, after having paid their two cents or $150, that they are wasting money, and try to do things differently (self-modify). An AI's programmers may recognize that, from their own perspective, they would rather not have their AI spend money on circular taxi rides. This implies a path from incoherent non-advanced agents to coherent advanced agents as more and more optimization power is applied to them.

A sufficiently advanced agent would presumably catch on to the existence of coherence theorems and see the abstract pattern of the problems (as humans already have). But it is not necessary to suppose that these qualitatively destructive behaviors are being targeted because they are 'irrational'. It suffices for the incoherencies to be targeted as 'problems' because particular cases of them are recognized as having produced clear, qualitative losses.

Without knowing in advance the exact specifics of the optimization pressures being applied, it seems that, in advance and ceteris paribus, we should expect that paying a cent to throw a switch and then paying again to switch it back, or throwing away $150 on circular taxi rides, are qualitatively destructive behaviors that optimization would tend to eliminate. E.g., one expects a consequentialist goal-seeking agent would prefer, or a policy reinforcement learner would be reinforced, or a fitness criterion would evaluate greater fitness, etc., for eliminating the behavior that corresponds to incoherence, ceteris paribus, and given the option of eliminating it at a reasonable computational cost.

If there is a particular kind of optimization pressure that seems sufficient to produce a cognitively highly advanced agent, but which also seems sure to overlook some particular form of incoherence, then this would present a loophole in the overall argument and yield a route by which an advanced agent with that particular incoherence might be produced (although the agent's internal optimization must also be predicted to tolerate the same incoherence, as otherwise the agent will self-modify away from it).

### Eliminating behaviors that are dominated by cheaply computable alternative behaviors will produce cognition that looks Bayesian-coherent from our perspective. ^eliminating-behaviors-that-are

Perfect epistemic and instrumental coherence is too computationally expensive for bounded agents to achieve. Consider, e.g., the conjunction rule of probability that $P(A\wedge B) \le P(A)$. If A is a theorem, and B is a lemma very helpful in proving A, then asking the agent for the probability of A alone may elicit a lower answer than asking the agent about the joint probability of A&B (since thinking of B as a lemma increases the subjective probability of A). This is not a full-blown form of conjunction fallacy since there is no particular time at which the agent explicitly assigns a lower probability to $P(A)=P((A\wedge B) \vee (A\wedge \neg B))$ than to $P(A\wedge B)$. But even for an advanced agent, if a human was watching the series of probability assignments, the human might be able to say some equivalent of, "Aha, even though the agent was exposed to no new outside evidence, it assigned probability $X$ to $P(A)$ at time $t$, and then assigned probability $Y>X$ to $P(A\wedge B)$ at time $t+2$."

Two notions of "sufficiently optimized agents will appear coherent (to humans)" that might be salvaged from the above objection are as follows:

-   There will be some _bounded_ notion of Bayesian rationality that incorporates, e.g., a theory of [logical uncertainty](https://www.lesswrong.com/w/logical-uncertainty), which agents will appear from a human perspective to strictly obey. All departures from this bounded coherence that humans can understand using their own computing power will have been eliminated.
-   It will not be possible for humans to _specifically predict in advance_ any large coherence violation as, e.g., the above intertemporal conjunction fallacy. Anything simple enough and computable cheaply enough for humans to predict in advance will also be computationally possible for the agent to eliminate in advance. Any predictable coherence violation, which is significant enough to be humanly worth noticing, will also be damaging enough to be worth eliminating.

Although the first notion of salvageable coherence above seems to us quite plausible, it has a large gap with respect to what this bounded analogue of rationality might be. Insofar as the thesis that optimized agents appear coherent has practical implications, these implications should probably rest upon the second line of argument.

One possible loophole of the second line of argument might be some predictable class of incoherences, which are not at all damaging to the agent and hence not worth spending even relatively tiny amounts of computing power to eliminate. If so, this would imply some possible humanly predictable incoherences of advanced agents, but these incoherences would not be _exploitable_ to cause any final outcome that is less than maximally preferred by the agent, including scenarios where the agent spends resources it would not otherwise spend, etc.

A final implicit step is the assumption that when all humanly-visible agent-damaging coherence violations have been eliminated, the agent should look to us coherent; or that if we cannot predict specific coherence violations in advance, then we should reason about the agent as if it is coherent. We don't yet see a relevant case where this would fail, but any failure of this step could also produce a loophole in the overall argument.

## Caveats ^caveats

### Some possible mind designs may evade the default expectation ^some-possible-mind-designs

Since [mind design space is large](https://www.lesswrong.com/posts/tnWRXkcDi5Tw9rzXw/the-design-space-of-minds-in-general), we should expect with high probability that there are at least some architectures that evade the above arguments and describe highly optimized cognitive systems, or reflectively stable systems, that appear to humans to systematically depart from bounded Bayesianism.

### There could be some superior alternative to probability theory and decision theory that is Bayesian-incoherent ^there-could-be-some

When it comes to the actual outcome for advanced agents, the relevant fact is not whether there are currently some even more appealing alternatives to probability theory or decision theory, but whether these exist in principle. The human species has not been around long enough for us to be sure that this is not the case.

Remark one: To advance-predict specific incoherence in an advanced agent, (a) we'd need to know what the superior alternative was, and (b) it would need to lead to the equivalent of going around in loops from San Francisco to San Jose to Berkeley.

Remark two: If, on some development methodology, it might prove catastrophic for there to exist some _generic_ unknown superior to probability theory or decision theory, then we should perhaps be worried on this score. Especially since we can be reasonably sure that an advanced agent cannot actually use probability theory and decision theory, and must use some bounded analogue if it uses any analogue at all.

### A cognitively powerful agent might not be sufficiently optimized ^a-cognitively-powerful-agent

Scenarios that negate the thesis that [relevant powerful agents will be highly optimized](https://www.lesswrong.com/w/relevant-powerful-agents-will-be-highly-optimized), such as [brute forcing non-recursive intelligence](https://www.lesswrong.com/w/brute-forcing-non-recursive-intelligence), can potentially evade the 'sufficiently optimized' condition required to yield predicted coherence. E.g., it might be possible to create a cognitively powerful system by overdriving some fixed set of algorithms, and then to prevent this system from optimizing itself or creating offspring agents in the environment. This could allow the creation of a cognitively powerful system that does not appear to us as a bounded Bayesian (if, for some reason, that was a good idea).

## Implications ^implications

If probability high: The predictions we make today about the behaviors of generic advanced agents should not depict them as being visibly, specifically incoherent from a probability-theoretic or decision-theoretic perspective.

If probability not extremely high: If it were somehow necessary or helpful for safety to create an incoherent agent architecture, this might be possible, though difficult. The development methodology would need to contend with both the optimization pressures producing the agent and the optimization pressures that the agent itself might apply to itself or to environmental subagents. Successful [intelligence brute forcing](https://www.lesswrong.com/w/intelligence-brute-forcing) scenarios in which a cognitively powerful agent is produced by using a great deal of computing power on known algorithms, and then the agent is somehow forbidden from self-modifying or creating other environmental agents, might be able to yield predictably incoherent agents.

If probability not extremely high: The assumption that an advanced agent will become Bayesian-coherent should not be a [load bearing premise](https://www.lesswrong.com/w/load-bearing-premise) of a safe development methodology unless there are further safeguards or fallbacks. A safe development methodology should not fail catastrophically if there exists a generic, unknown superior to probability theory or decision theory.
