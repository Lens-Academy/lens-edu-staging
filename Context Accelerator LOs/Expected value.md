---
id: e84dc325-299a-4297-94e3-282739c37c20
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Compare uncertain options by expected value, explain why a bet that will probably fail can still be worth taking, and recognise the main ways expected-value reasoning goes wrong.

## Requires

## Helpful first
- [[Subjective probability]]

## Why it matters
People working on AI risk often compare projects and risks by expected value, for example backing several long shots because one success could outweigh many failures. Understanding this lets you follow and question those choices, and notice when a guessed tiny probability is carrying a huge conclusion.

## Lenses

## Tests
#### Question: Choice
id:: 4c0bcadf-4a9b-4e3c-bb2c-37decb06b029
content:: Which of these best describes the expected value of an uncertain option?
options::
- [x] The probability-weighted average of its possible outcomes
- Its most likely outcome
- Its best outcome, discounted for risk
- The average of its best and worst outcomes
shuffle:: true

#### Question: FillBlank
id:: 39e51e73-bbbb-417a-9a43-e1ef82db9e74
content:: An option with a 5% chance of a payoff of 200, and nothing otherwise, has an expected value of {{10}}.

#### Question: Choice
id:: e778ff31-1951-4879-abae-6ca54b614b09
content:: Project A is certain to prevent a given harm. Project B has a 20% chance of preventing a harm 50 times larger, and otherwise does nothing. Judged by expected value alone, should Project B be preferred?
options::
- [x] Yes
- No

#### Question: Choice
id:: 7acd8690-986c-493b-8967-bfed3beac4fe
content:: Two options have equal expected value. Option A gives a certain result; option B gives either twice that result or nothing, with equal chances. What does expected value alone say about choosing between them?
options::
- [x] Neither is better than the other
- A is better because its result is certain
- B is better because its best case is higher
- Neither can be compared until B is resolved
shuffle:: true

#### Question: Choice
id:: 52866935-6512-4f73-8922-49cc29d99e55
content:: A funder takes a hits-based approach: it backs many projects that each have a small chance of a very large success. If this works as intended, what should the funder expect to see?
options::
- [x] Most projects fail, and a few successes provide most of the value
- Most projects succeed modestly, with few outright failures
- Value spread fairly evenly across the funded projects
- Projects chosen mainly for their low chance of failure
shuffle:: true

#### Question: Choice
id:: 4e15ebeb-52d6-47e3-8005-afb4a67835e7
content:: A grantmaker finds that 80% of the long-shot research projects it funded failed. Does this fact alone show that its funding decisions had poor expected value?
options::
- [x] No
- Yes

#### Question: Choice
id:: fd0687c6-a345-40d8-a506-11994c00bbb3
content:: A person prefers a sure $1,000 to a 50% chance of $2,100, even though the gamble has a higher expected dollar value. Which explanation is consistent with them deciding well?
options::
- [x] Each extra dollar matters less to them once they have $1,000
- They have miscalculated the expected value of the gamble
- A 50% chance is too uncertain for expected value to apply
- They are ignoring the gamble's best possible outcome
shuffle:: true

#### Question: Choice
id:: 0ed27ea2-c16b-406d-affc-268f7a2cfe05
content:: Someone argues for a project by multiplying a guessed one-in-a-billion probability of success by an astronomically large benefit. What is the main weakness of this expected-value argument?
options::
- [x] Its conclusion rests almost entirely on a probability nobody can estimate well
- Expected value can't be used for outcomes that happen only once
- Multiplying probabilities by very large numbers is mathematically invalid
- Expected value only applies to outcomes measured in money
shuffle:: true

#### Question: Choice
id:: 395f32dc-dee2-4614-9297-312705de23f9
content:: In the thought experiment called Pascal's mugging, a stranger demands $10 and threatens to cause vast suffering by magic if refused. You think the threat is almost certainly false. Why does this trouble naive expected-value reasoning?
options::
- [x] The stranger can name a harm big enough to outweigh any tiny probability
- Expected value says threats from strangers should be ignored
- The $10 cost is certain, so expected value can't be calculated
- The threat's probability is zero, so expected value is undefined
shuffle:: true

#### Question: Choice
id:: e492e753-7a6e-420c-ae73-9c310ec3c5dc
content:: A careful analysis puts the chance of a disaster at 1 in 10,000. You think there is a 1 in 100 chance the analysis is badly flawed. What follows for your overall estimate of the disaster's chance?
options::
- [x] It may be well above 1 in 10,000, since a flawed analysis could be far off
- It should stay at 1 in 10,000, since that is the best analysis available
- It should be lower, since doubts about an analysis reduce its estimates
- It should be exactly 1 in 100, the chance the analysis is flawed
shuffle:: true

#### Question: Open
id:: 8a646ce6-b3b3-43d1-8751-952cff32d773
content:: Explain why it can be reasonable to fund a project you think will probably fail.
assessment-instructions:: Score out of 100. 100: if the project succeeds the payoff is large enough that probability times payoff beats safer options (an example is fine, such as a 10% chance of a large impact beating a certain small one). 50: says the reward is high but doesn't link it to the low probability.

#### Question: Open
id:: 151031f7-244b-48d1-9abc-5a1797317c9d
content:: Give one way expected-value reasoning about AI risk can mislead, even when the arithmetic is correct.
assessment-instructions:: Score out of 100. 100 for any one of: the inputs are guesses that drive the result; ignoring the chance that the model or argument itself is wrong; tiny probabilities of enormous stakes dominating the decision (fanaticism, Pascal's mugging); leaving out important outcomes or options. 50: says only that numbers are uncertain, without saying how that misleads.

#### Question: Open
id:: c0579815-0f0a-47ba-a701-f918ec53bef8
content:: In decision theory, what is "fanaticism", and what is one response people propose to it?
assessment-instructions:: Score out of 100. 60: always preferring a tiny chance of an enormous payoff over a sure, more modest good, however tiny the chance. 40 for any one response: ignore probabilities below some threshold; cap how much value an outcome can have; discount speculative estimates; give weight to other decision rules or moral views.
