---
id: 'e7f82dce-8a68-41bf-a730-3c9d5de07006'
title: "Disagreement, Cruxes, and Action"
tldr: "When serious people remain far apart, averaging their probabilities can hide the real issue. The useful work is to find what drives the disagreement, what evidence could move it, and which actions still make sense before consensus."
summary_for_tutor: "Uses the Existential Risk Persuasion Tournament, Scott Alexander's discussion, and the Forecasting Research Institute's follow-up on roots of disagreement. Covers persistent disagreement, cruxes, value of information, worldview differences, local deference, and robust action."
reading_minutes: 34
tutor_minutes: 24
tags:
  - wip
---

#### Text
content::
\## What if good-faith disagreement survives?

There is a comforting picture of rational disagreement. Two thoughtful people disagree because one has missed a fact, misunderstood an argument, or made a mistake. They share information, identify the error, and move closer together. Sometimes that is exactly what happens.

AI risk gives us harder cases. The Existential Risk Persuasion Tournament brought together domain experts and experienced forecasters to make predictions about severe global risks. Scott Alexander's discussion of the tournament highlighted a striking result: people with serious forecasting or subject-matter credentials could look at much of the same evidence and remain very far apart, especially on risks with little historical precedent.[^alexander] That raised an obvious question. Was the disagreement simply too shallow? Maybe the participants had not spent enough time on the arguments, or maybe the "experts" and "forecasters" did not understand one another.

The Forecasting Research Institute's follow-up study tried to test that possibility more directly.[^fri] It recruited a small group of AI-risk "concerned" participants and "skeptical" participants, including superforecasters and domain experts, and had them spend substantial time reading, forecasting, discussing, and working together on cruxes. The two groups could summarize one another's arguments reasonably well. They still barely converged. In the report's final forecasts, the median concerned participant put 20 percent on AI-caused existential catastrophe by 2100 while the skeptical group put 0.12 percent.[^fri]

Those numbers should not be treated as authoritative estimates for the course. The sample was small and deliberately selected for disagreement. The durable lesson is about the structure of the disagreement. More engagement and better mutual understanding did not remove it.

\## Top-level probabilities can hide agreement underneath

A twenty-percentage-point gap sounds like a disagreement about everything. The FRI results suggest otherwise. The groups agreed much more on some components than their final numbers suggest. Both gave high probability to very powerful AI being developed by 2100 under the study's definition. They disagreed more about what follows from that capability: how fast AI moves beyond humans in strategically relevant domains, how often systems develop dangerous goals, whether an advanced system could actually cause human extinction, and how effectively society would respond.[^fri]

This matters because the policy implication of a disagreement depends on which link carries it. If the main crux is capability timelines, better forecasting of AI research progress is useful. If the crux is dangerous agency, evaluations and interpretability matter more. If the crux is institutional response, governance research may be the bottleneck. If the crux is how much theoretical reasoning deserves weight before empirical confirmation, the disagreement is partly methodological and may not dissolve through another benchmark.

A top-level probability compresses all of this. Two people can both say ten percent while believing completely different stories. Two people can say one percent and twenty percent while agreeing on most of the causal chain and differing sharply on one transition. Treating the number as the disagreement can therefore hide the question we actually need to investigate.

\## Cruxes turn disagreement into research questions

FRI asked participants to propose *cruxes*: near-term questions whose resolution would produce large updates in long-run AI-risk beliefs.[^fri] A good crux connects an observable outcome to a belief we care about. If the outcome goes one way, the belief should move meaningfully. If it goes the other way, it should move in the opposite direction or at least much less.

One of the stronger shared cruxes concerned evaluations of dangerous capabilities, such as whether future systems would show abilities related to autonomous replication or avoiding shutdown.[^fri] The skeptical group generally wanted more real-world evidence that theoretical danger mechanisms were appearing. Concerned participants also cared about those observations, although their highest-value questions were often more focused on alignment and alignment research.

The most interesting result is that even the best near-term cruxes did not explain most of the long-run disagreement. The report estimated that one of the strongest convergent cruxes would close only about five percent of the gap between the median pair.[^fri] This is not a failure of the crux method. It tells us that much of the disagreement lives somewhere else.

#### Question: Open
id:: 9d09f247-2c3a-47d8-9e4f-61589d7db14f
content::
\## Midpoint check

Think of one claim from your own AI-risk model.

Write one near-term observation that would make you substantially *more* confident in the claim and one that would make you substantially *less* confident.

Would someone who disagrees with you also see those observations as relevant evidence?

feedback-instructions::
This is ungraded. Help the learner make the observations genuinely discriminating. If their evidence would be expected under both the claim and its alternative, point that out. If the opposing side would reject the evidence as irrelevant, ask what deeper methodological disagreement explains that. Maximum two replies.

#### Text
content::
\## Sometimes the disagreement is about what counts as evidence

The FRI report identifies a broader worldview difference.[^fri] Skeptical participants tended to put more weight on a world that usually changes gradually and to be more cautious about long chains of theoretical reasoning without direct empirical validation. Concerned participants were more willing to give substantial weight to theoretical arguments about capability gaps, misalignment, and power even before those mechanisms had strong real-world demonstrations.

This is a familiar tension in emerging-risk analysis. If we insist on direct historical evidence for every important claim, genuinely novel dangers will always look weak until the world has already produced a close precedent. If we rely too heavily on theoretical chains, we can construct internally coherent stories that are badly calibrated.

There is no general rule saying that theory gets thirty percent and outside-view evidence gets seventy. What we can do is make the evidential standard explicit. When a person says "I would update only after seeing dangerous autonomous behaviour in deployed systems", that is a different epistemic position from "the mechanism is strong enough that waiting for a demonstration would be irresponsible." Once the difference is visible, we can ask whether there are intermediate tests that both sides should care about.

This is also where Unit 1 connects back to deep uncertainty. A disagreement can persist because people assign different probabilities to the same model, but it can also persist because they trust different models or different kinds of evidence. In the latter case, simply collecting more of one side's preferred evidence may do little.

\## Value of information is about decisions, not curiosity

A crux is useful partly because it can have *value of information*. Information is decision-relevant when possible findings change what we should do enough to justify the cost of obtaining them.

Imagine two studies. The first gives a very precise measurement of a capability everyone already expects and would not change anyone's policy. The second has wider error bars but could decide whether a lab introduces a costly containment measure. The second study may have more practical value.

FRI developed metrics for comparing forecasting questions by how much they are expected to change beliefs and reduce disagreement.[^fri] We do not need the formal details here. The important habit is to ask: **what result could actually change the decision?** This protects research agendas from becoming collections of interesting questions disconnected from action.

It also gives uncertainty a positive role. Sometimes the correct response to uncertainty is neither "act as if the worst case is true" nor "wait passively". It is to spend resources on the uncertainty that is most likely to change a consequential choice.

\## When should you defer?

Most participants in this course will not be experts on every part of the AI-risk chain. Nobody is. The question is how to use other people's expertise without replacing your own reasoning with a credential check.

Deference is most straightforward when the target domain is well defined, experts have a strong track record on similar questions, and the methods have received repeated feedback from reality. A virologist has relevant expertise about viral replication. A security engineer has relevant expertise about software vulnerabilities. A machine-learning researcher may know far more about current training methods than a philosopher.

The final question "what is the probability that AI causes existential catastrophe?" cuts across many domains and reaches far beyond direct feedback. It includes machine learning, economics, security, organizational behaviour, geopolitics, forecasting, philosophy, and assumptions about systems that do not yet exist. Expertise becomes local. A forecaster can have a strong record on shorter-horizon questions and still face a very unusual century-scale target. An AI researcher can understand current systems deeply and have no special expertise in population ethics or international bargaining.

A sensible response is **decomposed deference**. Ask which part of the model a person's expertise bears on, how good the feedback in that domain is, and how the local judgment is being combined with other judgments. This lets us learn from experts without pretending there is one profession called "expert on the entire future".

\## Why averaging can be useful, and why it can be misleading

Suppose one group says two percent and another says twenty percent. Averaging them to eleven percent can be reasonable in some settings. If the estimates are comparably informed, reasonably independent, and aimed at the same well-defined quantity, aggregation can reduce individual error.

Those assumptions often fail in AI risk. Both groups may use the same published evidence. One group may have better information about one part of the problem. The numbers may encode different threat models. One side may be making a moral judgment while the other is making an empirical one. Or the estimates may be correlated because everyone is responding to the same small community of arguments.

The first question should therefore be "why are these numbers different?" before "what is their average?" Aggregation is most useful once we understand what is being aggregated.

\## Disagreement does not require paralysis

A decision-maker eventually has to stop updating and choose. One response is to look for actions that make sense across several plausible views.

Good dangerous-capability evaluations can be useful to someone who assigns a low probability to catastrophe because they test whether feared mechanisms are actually appearing. They can be useful to someone who assigns a high probability because they create warning signals and inform deployment decisions. Better biosecurity matters under malicious-use models even if one doubts strong agentic takeover. Strong information security matters under organizational-risk and misuse scenarios. Preserving institutional capacity can matter under gradual-disempowerment and accumulative-risk models.

Robustness is not enough on its own. A robust action can have tiny impact. Some high-impact decisions genuinely require taking a stand on disputed assumptions. The point is narrower: disagreement does not always block useful action, and finding overlap can be more productive than forcing consensus on one top-level number.

The other response is adaptive action. Take a reversible step, define the evidence that would trigger a stronger response, and update as the evidence arrives. This works only when the later checkpoint remains available. The previous submodule showed why that condition has to be checked rather than assumed.

\## What this unit should leave you with

By now, the course has deliberately avoided giving you a probability to copy. You have seen arguments for taking irreversible risk seriously, reasons not to take huge expected-value estimates literally, a case for precaution that still allows tradeoffs, several distinct AI-catastrophe pathways, and serious objections to prioritising x-risk. You have also seen that thoughtful disagreement can survive unusually intense attempts at resolution.

The point is not that "everyone is uncertain, so anything goes". Some arguments are stronger than others. Some evidence is more discriminating. Some interventions are better supported. The point is that a good decision should expose which claims carry the conclusion and what could change them.

Your final exercise does exactly that. You will build a provisional map of your own view: what worries you, what carries the weight, what the strongest objection is, which information would be most valuable, and what action still makes sense if part of your model is wrong. Later units will attack different pieces of that map.

[^fri]: Josh Rosenberg et al. (2024), *Roots of Disagreement on AI Risk: Exploring the Potential and Pitfalls of Adversarial Collaboration*. [Forecasting Research Institute](https://forecastingresearch.org/research/roots-of-disagreement-on-ai-risk)
[^alexander]: Scott Alexander (2023), *The Extinction Tournament*. [Astral Codex Ten](https://www.astralcodexten.com/p/the-extinction-tournament)

#### Question: Open
id:: 74b01c14-8e88-4f6f-8608-bfcfc03a7c8e
content::
\## Phase 1: Recall

Without looking back, write down three structurally different reasons informed people can remain far apart after serious discussion. Then define a useful crux in your own words.

feedback-instructions::
Respond once in 90 to 160 words. Credit distinct sources of disagreement such as different causal models, evidential standards, long-run expectations, priors, values, or patterns of deference. A useful crux should connect an observable outcome to a meaningful update.

#### Question: Open
id:: 5350c063-5798-4c30-ab20-3ef031685334
content::
\## Phase 2: Processing

Which part of your current view depends most on trusting someone else's expertise? What exactly are you deferring to them about, and how would you notice if that deference were misplaced?

feedback-instructions::
This is reflective and ungraded. Help the learner make the domain of deference local and explicit. Do not encourage blanket trust or blanket skepticism. Maximum two replies.

#### Question: Open
id:: 7017711e-c4fe-4a08-b2f6-a4be96314615
content::
\## Phase 3: Learning Question

Two groups disagree about a long-run technological catastrophe. They understand each other's arguments, share most current evidence, and still differ by an order of magnitude. A policymaker proposes averaging their probabilities and moving on.

Explain why averaging can lose important information. Then describe one better way to use the disagreement for a decision.

assessment-instructions::
Score out of 100.

50 points: The answer explains that top-level probabilities can compress different causal models, evidential standards, priors, values, or correlated evidence, so a midpoint can hide the source of disagreement.

50 points: The answer gives a defensible alternative use of the disagreement, such as decomposing the model, identifying a crux, gathering discriminating information, deferring locally to relevant expertise, or choosing an action that remains useful across the live views.

feedback-instructions::
Give 100 to 170 words. State whether the learner preserved the information inside the disagreement. Below full credit, identify the missing reason or weakness in the proposed alternative. Do not tell them which probability to adopt.
