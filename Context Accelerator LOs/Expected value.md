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
- [[../Lenses/probablygood-expected-value-why-probabilities-can-help-us-make-better-career-decisions|Expected Value]]: what expected value is and how to calculate it, with a lottery ticket and a comparison of two career paths (2023).
- [Hits-based giving (Effective Altruism Forum)](https://forum.effectivealtruism.org/posts/badD656AemGYnraMt/hits-based-giving): Holden Karnofsky on why a funder should back projects that will probably fail, when a few big successes carry the whole portfolio; read "The basic case for hits-based giving" (April 2016).
- [[../video_transcripts/robert-miles-ai-safety-is-ai-safety-a-pascals-mugging|Is AI Safety a Pascal's Mugging?]]: Robert Miles on Pascal's wager and mugging, why huge stakes can't stand in for evidence, and why a real 1-in-100 risk is different from a mugger's threat.
- [Why We Can't Take Expected Value Estimates Literally (GiveWell)](https://blog.givewell.org/2011/08/18/why-we-cant-take-expected-value-estimates-literally-even-when-theyre-unbiased/): Holden Karnofsky on why a rough estimate built from guesses shouldn't decide a choice on its own, and how this defuses Pascal's mugging; read from the start through the section "Pascal's Mugging" (August 2011).
- [Tiny Probabilities of Great Value (Utilitarianism.net)](https://www.utilitarianism.net/guest-essays/expected-value-fanaticism): Petra Kosonen on "fanaticism", where expected value always favours a tiny chance of a vast payoff, and proposed fixes such as capping value or ignoring very small probabilities; read the first section and "Alternatives to fanaticism" (2025).

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

#### Question: Choice
id:: b94256b6-feb4-4267-826f-35845ae7a713
content:: Two options have equal expected value. Option A gives a certain result; option B gives either twice that result or nothing, with equal chances. Which difference between them does expected value alone ignore?
options::
- [x] How risky each option is
- How likely each outcome is
- How large each outcome is
- Which has the higher average result
shuffle:: true

#### Question: Choice
id:: 52866935-6512-4f73-8922-49cc29d99e55
content:: A funder takes a hits-based approach: it backs many projects that each have a small chance of a very large success. If this works as intended, what should the funder expect to see?
options::
- [x] Most projects fail, and a few successes provide most of the value
- Most projects succeed modestly, with few outright failures
- Value spread fairly evenly across the funded projects
- About half the projects succeed, each adding similar value
shuffle:: true

#### Question: Choice
id:: 4e15ebeb-52d6-47e3-8005-afb4a67835e7
content:: A grantmaker finds that 80% of the long-shot research projects it funded failed. Does this fact alone show that its funding decisions had poor expected value?
options::
- [x] No
- Yes

#### Question: Choice
id:: 0ed27ea2-c16b-406d-affc-268f7a2cfe05
content:: Someone argues for a project by multiplying a guessed one-in-a-billion probability of success by an astronomically large benefit. What is the main weakness of this expected-value argument?
options::
- [x] Its result hinges on a probability nobody can estimate well
- Expected value can't be used for outcomes that happen only once
- Expected value ignores what happens if the project fails
- Expected value only applies to risks with a long track record
shuffle:: true

#### Question: Choice
id:: 395f32dc-dee2-4614-9297-312705de23f9
content:: In the thought experiment called Pascal's mugging, a stranger demands $10 and threatens to cause vast suffering by magic if refused. You think the threat is almost certainly false. Why does this trouble naive expected-value reasoning?
options::
- [x] The stranger can name a harm big enough to outweigh any tiny probability
- Expected value gives no weight to outcomes you believe are false
- Expected value needs the threat's probability to be known exactly
- A $10 stake is too small for expected value to apply
shuffle:: true

#### Question: Choice
id:: e492e753-7a6e-420c-ae73-9c310ec3c5dc
content:: A careful analysis puts the chance of a disaster at 1 in 10,000. You think there is a 1 in 100 chance the analysis is badly flawed. What follows for your overall estimate of the disaster's chance?
options::
- [x] It may be well above 1 in 10,000, since a flawed analysis could be far off
- It should stay at 1 in 10,000, since that is the best analysis available
- It should be lower, since doubts about an analysis reduce its estimates
- It should be about 1 in 1,000,000, combining the two probabilities
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
id:: 202865d6-94c2-43ff-963a-4e4e9bfdd237
content:: Followed strictly, expected-value reasoning can prefer a tiny chance of an enormous payoff to a sure, more modest good, however tiny the chance. Give one response people propose to this problem, and one drawback of that response.
assessment-instructions:: Score out of 100. 50 for one response: ignore probabilities below a threshold; cap how much value an outcome can have; discount speculative estimates; give weight to other decision rules or moral views. 50 for a fitting drawback, e.g. any threshold is arbitrary and many small risks may each fall below it; a cap can make huge real harms count too little; how much to discount is unclear.
