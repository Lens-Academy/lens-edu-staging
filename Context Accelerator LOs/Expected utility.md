---
id: ce0a030b-ff20-4d50-af4d-8819dddbe94c
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Calculate an option's expected utility, explain how an expected utility maximizer chooses between gambles, and describe what the von Neumann–Morgenstern theorem and coherence arguments do and don't show about AI systems.

## Requires
- [[Utility functions]]

## Helpful first
- [[Subjective probability]]

## Why it matters
Many arguments about AI risk, including instrumental convergence, model an advanced AI as an expected utility maximizer. If you understand the model, you can follow those arguments and also spot where they rely on assumptions the model doesn't supply, such as what the utility function is about.

## Lenses
- [Decision Theory FAQ (LessWrong)](https://www.lesswrong.com/posts/zEWJBFFMvQ835nq6h/decision-theory-faq): what expected utility is and how to calculate it, why utility need not track money, and the von Neumann–Morgenstern axioms and theorem; read sections 4.1, 8.2–8.4 and 8.6.3 (the Allais paradox) (February 2013).
- [[../Lenses/yudkowsky-coherent-decisions-imply-consistent-utilities|Coherent Decisions Imply Consistent Utilities]]: why agents that don't shoot themselves in the foot behave as if maximizing expected utility, from money pumps to the Allais paradox; read "Why not circular preferences?", "Probabilities and expected utility" (up to "Probabilities summing to 1") and "The Allais Paradox" (2017).
- [[../Lenses/shah-coherence-arguments-do-not-entail-goal-directed-behavior|Coherence Arguments Do Not Entail Goal-Directed Behavior]]: any behaviour can be described as maximizing some utility function, so the label alone doesn't imply goals, power-seeking or danger; an influential critique (2018).
- [[../Lenses/katjagrace-coherence-arguments-imply-a-force-for-goal-directed-behavior|Coherence Arguments Imply a Force for Goal-Directed Behavior]]: a reply to Shah arguing that pressure toward coherence still pushes real agents toward goal-directedness; the other side of the debate (2021).

## Tests

#### Question: Choice
id:: 58525627-99ac-4a5e-8682-d154ee875156
content:: An expected utility maximizer chooses between a sure outcome with utility 6 and a gamble with a 50% chance of utility 10 and a 50% chance of utility 0. Which does it choose?
options::
- [x] The sure outcome, since 6 is more than the gamble's 5
- The gamble, since its best outcome is worth 10
- Either one, since both are worth about the same
- It depends on how risk-averse the agent is
shuffle:: true

#### Question: Open
id:: 404dc164-495d-4fa2-b180-8cb36429f0a6
content:: A person prefers a sure $50 to a 50% chance of $100 (and otherwise nothing). How can this choice fit expected utility maximization, even though both options have the same expected amount of money?
assessment-instructions:: Score out of 100. 100 for saying that utility need not be proportional to money: if each extra dollar adds less utility (diminishing marginal utility, a concave utility function), the sure $50 has higher expected utility than the gamble. 50 for just naming "risk aversion" without linking it to how utility depends on money.

#### Question: Choice
id:: 9e5eff97-b7c1-4456-96b3-2688c8ecf6c2
content:: An expected utility maximizer gives outcomes A, B and C the utilities 0, 1 and 3. Which new set of utilities for A, B and C would keep all its choices between gambles over these outcomes the same?
options::
- [x] 10, 12, 16
- 0, 1, 2
- 0, 1, 9
- 1, 2, 3
shuffle:: true

#### Question: Choice
id:: 9e037f7c-f38a-42e6-b59a-328d2033cf50
content:: What does the von Neumann–Morgenstern utility theorem show?
options::
- [x] Preferences over gambles that meet certain axioms can be represented by expected utility
- Rational agents should value each extra dollar equally
- Any system's behaviour can be described as maximizing some utility
- Smarter agents tend to converge on the same utility function
shuffle:: true

#### Question: Choice
id:: c1a26587-6080-4bd5-9f56-23a1aea9e3a8
content:: Many people prefer a sure $1 million to a gamble giving 89% $1 million, 10% $5 million and 1% nothing. Many of the same people prefer 10% $5 million (else nothing) to 11% $1 million (else nothing). What does this pair of choices show?
options::
- [x] No utilities for the money amounts make both choices maximize expected utility
- Diminishing marginal utility of money explains both choices
- These people always pick the option with the most expected money
- These people always pick the option with the best possible outcome
shuffle:: true

#### Question: Choice
id:: 199e6076-232d-44b7-860e-de69f45bb589
content:: Why do some AI safety arguments expect advanced AI systems to behave like expected utility maximizers?
options::
- [x] Agents that break its axioms can be exploited, giving capable agents a reason to stop
- The vNM theorem proves that any intelligent system satisfies its axioms
- Developers usually write an explicit utility function into AI systems
- A theorem proves that trained AI systems end up with stable goals
shuffle:: true

#### Question: Choice
id:: ba47a483-5cfb-4f80-9e95-fdb8f2b4871a
content:: In expected utility theory as used to model an AI agent, where do the probabilities in the agent's calculation come from?
options::
- [x] The agent's own beliefs
- Frequencies measured in past trials
- The true physical chances
- Numbers set by its designers
shuffle:: true

#### Question: Open
id:: 7c9e42fb-161c-4b8a-9685-1c1daf65b5cd
content:: To compute the expected utility of an action, an agent needs two kinds of input. What are they?
assessment-instructions:: Score out of 100. 100 for both: the probability of each possible outcome given the action (the agent's beliefs) and the utility of each outcome (its preferences or values). 50 for only one of the two.

#### Question: Open
id:: f49d6e2e-913c-4d83-9f21-f384e4ffc97c
content:: An AI system is known to maximize expected utility. Why is that fact alone not enough to predict that it will seek power or resist being shut down?
assessment-instructions:: Score out of 100. 100 for any one of: it depends on what the utility function is about (e.g. a function over short-term or narrow outcomes may gain little from power); almost any behaviour can be described as maximizing some utility function, so the label alone constrains little. 40 for answers about capability alone (e.g. "it may not be smart enough") without mentioning the goal.
