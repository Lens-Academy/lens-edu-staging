---
id: '8aaaf25e-bbdd-4092-bef1-1e64dbc4ecf0'
learning-outcome: {--{"author":"Elias's AI","timestamp":1787500741463}@@"Interpret evidence--}{++{"author":"Elias's AI","timestamp":1787500741463}@@"Decompose an effective-compute forecast into its chip-stock, hardware-efficiency and algorithmic-efficiency factors, predict how constraining one factor changes the aggregate growth rate, name the assumption that constraint leans on hardest, and distinguish a claim about when a capability arrives from a claim++} about {--{"author":"Elias's AI","timestamp":1787500741463}@@Forecasting, timelines, AGI, and transformative AI"--}{++{"author":"Elias's AI","timestamp":1787500741463}@@how fast capability grows once it does."++}
domain: "[[../Domains/Strategy]]"
stage: intermediate
tags:
  - {--{"author":"Elias's AI","timestamp":1787500741463}@@skill-tree-placeholder--}{++{"author":"Elias's AI","timestamp":1787500741463}@@learning-outcome++}
---{++{"author":"Elias's AI","timestamp":1787500741463}@@

## Test:
id:: 664aaa83-f121-404b-ab22-038180866302

#### Question
content::
Effective compute is the product of three factors: algorithmic efficiency, hardware efficiency (performance per chip), and the number of AI chips in service. Recent annual growth rates for them are roughly 3x, 1.35x and 2.3x respectively.

Suppose that from 2029 an international agreement caps the worldwide installed base of AI chips, holding the chip count flat. Assume operators may still retire chips and replace them one for one with current-generation hardware, so performance per chip keeps improving at trend. The other two factors carry on at their current rates.

(a) Does effective compute stop growing? Give the aggregate annual growth rate before and after the cap, and show the calculation.
(b) Name the assumption in that calculation you think is doing the most work, and say which way the answer moves if it is wrong.
(c) A commentator says the cap buys us years before takeoff. What has it changed, and what has it left open?

assessment-instructions::
Single pass/fail. Pass requires checks 1 and 4, plus at least one of checks 2 and 3. Each check is yes or no. Silence on a check fails that check.

1. MANDATORY. Treats the aggregate as a product, not a sum, and concludes growth does not stop, because the two unconstrained factors keep compounding.
FAIL an answer that subtracts, that averages the factors, or that implies growth halts.

2. Gives a before and an after figure, and the figures follow from the student's own stated multiplication. On the question's stated assumptions these are 1.35 x 3 = 4.05x per year after the cap, down from 1.35 x 3 x 2.3 = 9.32x per year before it. Accept any rounding in 4 to 4.1 and 9 to 9.4, or "roughly fourfold, down from roughly ninefold", or the equivalent in logs (about 0.61 log10 per year, down from about 0.97, a drop of 0.36, which is exactly the 2.3 factor).
ALSO ACCEPT 3x down from 6.9x, and 3.45x down from 7.94x, when the student states the premise that produces it: reading the 2.3x figure as growth in installed compute capacity, which already contains performance per chip; or rejecting the replacement assumption so that hardware efficiency cannot be realised on a capped fleet; or using a different published hardware figure. All three premises are defensible and one of them is forced by a contradiction in the source material.
FAIL only an answer whose numbers do not follow from its own stated premises.

3. Answers (b) with a named assumption AND a stated direction. Any of these pass: that hardware efficiency is realisable at all on a fleet that cannot grow; that the three factors are independent, when algorithmic progress is itself discovered by running experiments on chips; that 3x per year algorithmic efficiency continues rather than saturating, given that the compute needed for a fixed result is bounded below; that a cap is enforceable against stockpiling, smuggling, or uncapped inference silicon; that a short recent trend extrapolates.
A direction is required, not just a caveat. Do not require any particular assumption to be the one chosen.

4. MANDATORY. Answers (c) with the two axes kept apart. The answer must contain both: that the cap changes when a given level of effective compute is reached, which is a claim about timelines; and that how fast capability rises after transformative AI arrives is a separate question which a later arrival date does not settle.
FAIL an answer that treats "arrives later" as equivalent to "then goes slower", and fail an answer that only restates the arithmetic.

Grader note 1: do not read check 4 as requiring the student to say the cap is irrelevant to takeoff speed. It is not irrelevant, and a student who says so with a mechanism is right and must be credited, in either direction. Slower: the compute-centric account of takeoff runs through an investment feedback loop that converts economic returns into more compute, and the chapter allows "a slow takeoff if the loops are weaker or counterbalanced by other factors". Faster: one input is held while algorithmic efficiency compounds against it, and stockpiled or newly permitted chips at the moment the cap lapses convert accumulated efficiency into a discontinuous jump. Check 4 tests that the student treats these as two questions, not that they declare the two independent.

Grader note 2: do not treat "a freeze makes takeoff faster" as automatically correct. The overhang argument in its standard form is about hardware accumulating while software lags, and a chip cap is the mirror of that, so the student must supply a mechanism for it to land. There is also a live counter-argument in the chapter, that a sustained cap suppresses chip production itself so the counterfactual chips are never built and no overhang accumulates. A student who raises that counter-argument is reasoning well and must not be marked down for contradicting the paragraph above.

Grader note 3: the Atlas separately reports frontier training compute growing 5x per year. That is a different quantity from worldwide effective compute, one lab's largest run rather than the world's stock, and mixing them is a common error. A student who flags the difference, or who notices that 5x per year at the frontier on top of roughly 2.3x to 3.1x per year for world physical compute implies a rising share of world compute going into single runs, is correct. Credit under check 3.

Grader note 4: grade the reasoning, not the verdict on the commentator. A student who concludes the commentator is broadly right, and gets there by separating the two axes and naming a mechanism, passes.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AI Safety Atlas - Capabilities - Forecasting Timelines - PQ]]

## Lens:
source:: [[../Lenses/AI Safety Atlas - Capabilities - Forecasting Timelines]]

## Lens:
source:: [[../Lenses/AI Safety Atlas - Capabilities - Takeoff]]

## Lens:
source:: [[../Lenses/AI Safety Atlas - Capabilities - Exercises]]++}