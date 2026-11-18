---
id: c535b9f8-6e13-437e-b9de-df37235b713a
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what it means to treat a probability as a degree of belief, and read estimates like "a 10% risk of AI catastrophe" correctly: what they claim and what they don't.

## Requires

## Helpful first
- [[Bayesian updating]]

## Why it matters
Most numbers you'll meet about AI risk and timelines are personal estimates, not measurements. Reading them as measured frequencies, or dismissing them as made up, leads you to misjudge what experts are claiming, how much they disagree, and what their numbers mean for decisions.

## Lenses

## Tests

#### Question: Choice
id:: e3d21336-616e-421a-926c-8fd5bfac8fc3
content:: A forecaster says there's a 10% chance AI causes human extinction this century. On the degree-of-belief view of probability, what is she reporting?
options::
- [x] How strongly her evidence leads her to expect it
- The share of humanity expected to die from AI
- The share of AI systems she judges to be dangerous
- The error margin on a measured risk figure
shuffle:: true

#### Question: Choice
id:: 6e4462fc-1011-4943-ad2c-49258f1ac6ee
content:: On the frequency view, a probability is how often something happens over many repeated trials. What is the main difficulty in using this view for the probability that AI causes human extinction?
options::
- [x] The event can't be repeated to see how often it happens
- The event is too unlikely for any frequency to exist
- Experts disagree too much to agree on a frequency
- The outcome depends on human choices, not on chance
shuffle:: true

#### Question: Choice
id:: d9bc25b8-c4ee-4085-adc6-3f450b16f371
content:: A coin has been flipped and covered. Alice saw it land heads; Bob didn't see it. Bob says there's a 50% chance it's heads. On the degree-of-belief view, is Bob's estimate reasonable?
options::
- [x] Yes, it fits his information, as Alice's certainty fits hers
- No, the true probability is now 100% heads
- No, probabilities only apply before the coin is flipped
- Yes, since any number he chose would be fine
shuffle:: true

#### Question: Choice
id:: f703a762-0b7c-4d6c-bc1d-efa55f8f6fc7
content:: A forecaster gave a 20% chance to an event, and the event happened. What does this single outcome tell you about her estimate?
options::
- [x] Little; judging her needs many of her forecasts
- It was wrong, since she said it wouldn't happen
- It was too low, and should have been 100%
- It was a lucky guess, since 20% means unlikely
shuffle:: true

#### Question: Choice
id:: 728655eb-c04f-46f7-81d9-d4a315033a32
content:: Someone says AI has a 30% chance of causing a catastrophe this century and an 80% chance of not causing one this century. Are these two degrees of belief coherent?
options::
- Yes
- [x] No

#### Question: Choice
id:: 7520c091-5ed6-4822-950c-7188371e15b8
content:: A researcher says: "If superhuman AI is built by 2040, I put 40% on catastrophe." A headline reports: "Researcher says 40% chance of AI catastrophe." What's wrong with the headline?
options::
- [x] It drops the condition about superhuman AI by 2040
- Nothing, as conditional and overall chances are equal
- It should report 60%, the chance things go well
- Degrees of belief can't be reported as numbers
shuffle:: true

#### Question: Choice
id:: 914a2516-3509-4834-b510-19685727cbb4
content:: Someone says: "Nobody can know the probability of AI catastrophe, so giving a number is meaningless." What is the main reply from the degree-of-belief view?
options::
- [x] A number states how uncertain you are, not that you know
- The true probability can be worked out from past technologies
- Numbers become meaningful once enough experts agree on them
- A risk without a known number should be treated as zero
shuffle:: true

#### Question: Choice
id:: 3821a88c-b7cd-47a0-a7ee-8de29e412cde
content:: When different people hear that an event is "likely", how do the probabilities they take it to mean usually compare?
options::
- [x] They spread across a wide range
- They cluster tightly around 50%
- They cluster tightly around 95%
- They match closely once context is given
shuffle:: true

#### Question: FillBlank
id:: 958f1b28-cb4d-41cc-93e8-df143938ef43
content:: If your degree of belief that an event will happen is 10%, a bet that risks $1 to win ${{9|9.00}} if it happens should look roughly fair to you.

#### Question: Open
id:: 38ff1ae6-d5a8-462a-8e27-e18f3a424c51
content:: Two careful researchers give 5% and 30% for the same AI catastrophe. Give two reasons, consistent with the degree-of-belief view, why their numbers might differ.
assessment-instructions:: Score out of 100. 50 points for each of two different reasons among: they have different evidence or information; they weigh the same arguments differently; they start from different models or priors; they define the event or time frame differently. Give 25 for a reason that is only "they're biased" with no detail.

#### Question: Open
id:: ef7e0b94-9546-4ce1-813a-f326e0960ac8
content:: On the degree-of-belief view, what can make one person's probability for AI catastrophe better than another's, when neither can be checked against a measured frequency?
assessment-instructions:: Score out of 100. 100 for any one of: it fits the available evidence and arguments better; it comes from someone with a good track record of well-calibrated forecasts; it obeys the rules of probability and is updated properly on new evidence. 50 for "more expertise" without saying why expertise helps.

#### Question: Open
id:: 9408d91b-9307-45e8-84aa-558352ce52fb
content:: Suppose a survey of AI researchers reports a median 5% chance that AI leads to human extinction. Give one reason not to read this as a measured fact about how dangerous AI is.
assessment-instructions:: Score out of 100. 100 for any one of: it combines personal degrees of belief, not observed frequencies; results depend on who answered and how the question was worded; respondents may not have thought hard about it; a median hides wide disagreement. 50 for saying only that surveys can be wrong, with no reason.
