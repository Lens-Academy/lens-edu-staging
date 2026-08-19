---
id: '5cdfdeb9-5286-491f-bb68-79fcdaadd166'
learning-outcome: Given an unfamiliar trend line and a proposed extrapolation from it, state what must be true of the underlying quantity for the extrapolation to hold, distinguish a claim the measurement supports from one it does not, and use a base rate for trend breaks to say how much confidence the extrapolation earns.
domain: none
stage: intermediate
---
## Test:
id:: {--{"author":"Luc's AI","timestamp":1787132678912}@@'b7c38da8-4b6f-45fb-8be9-f77f01dbd829'--}{++{"author":"Luc's AI","timestamp":1787132678912}@@b7c38da8-4b6f-45fb-8be9-f77f01dbd829++}

#### Question
content:: A materials lab publishes a metric they call **depth**: for a candidate battery chemistry, the number of consecutive synthesis-and-test steps their automated system can carry out before a human has to intervene. They measure depth on their systems from the past six years and find it doubles roughly every nine months. The fit is good, R-squared above 0.95, and it holds across three separate hardware generations.

A commentator writes: "Depth doubles every nine months. Full autonomy in materials discovery needs a depth of around 10,000 steps. We are at 40 today. That is eight doublings, so six years. Materials science is solved by 2032."

The trend is real and well measured. The conclusion is doing something the trend does not license.

Say what the commentator must be assuming about the quantity called depth for the six-year figure to follow. Then separate what the measurement does establish from what it does not. Finally: given that you cannot resolve those assumptions from the data, how confident should anyone be in 2032, and on what basis would you set that confidence?

max-time:: 15:00

assessment-instructions:: The student has completed a module on timeline estimation, including a live capability metric whose own authors published its limitations, and a survey of measured base rates for discontinuous progress. This test uses a fabricated materials-science metric so that no answer can be recovered from the assigned readings; the student must transfer the reasoning.

The capability being tested: identifying the assumptions an extrapolation requires beyond the fit itself (construct stability, homogeneity of the task distribution, continuity of the generating mechanism), separating supported from unsupported claims, and grounding a confidence statement in an outside-view base rate rather than in the goodness of the fit.

The underlying structure, for your reference as grader. The commentator must assume at least:
- CONSTRUCT STABILITY. "Depth" at 40 steps and "depth" at 10,000 steps must be the same quantity. If the failures that force human intervention at step 40 are different in kind from those that would arise at step 5,000 (error accumulation, drift, decisions no one specified), the metric measures two different things at the two ends and the curve does not span them.
- HOMOGENEITY. The doubling was measured over whatever tasks were in their test set. Extrapolation assumes the next 10,000-step tasks are drawn from the same distribution rather than being the ones that were excluded because nothing could do them.
- MECHANISM CONTINUITY. Six years and three hardware generations is evidence the mechanism is stable so far. It is not evidence that the mechanism does not have a limit inside the extrapolated range, and R-squared is silent on this: a good fit measures agreement inside the observed range only.
- THRESHOLD VALIDITY. The 10,000 figure is asserted, not measured. If full autonomy needs 10,000 steps AND something else the metric does not capture, the arithmetic is answering a different question.
What the measurement DOES establish: that on this task distribution, on this system family, over this period, the quantity grew fast and regularly, which is real evidence against "progress has stalled" and real evidence that the doubling mechanism was not a one-generation artifact.
On confidence: the correct move is to notice that the fit's quality does not transfer to the extrapolation, and to reach for an outside view. Base rates for a strong technological trend continuing eight more doublings without a break are not near-certainty; robust discontinuities in surveyed technological trends are rare per year but not negligible, and trend *breaks* short of discontinuity are common. A defensible answer lands well below the confidence the R-squared invites, and says why the R-squared was the wrong input.

Grade reasoning, not agreement. A student who defends the 2032 figure while correctly naming the assumptions it rests on, and gives a base-rate argument for why those assumptions usually hold, is demonstrating the capability.

Response: assign one level, then justify it in 100 to 180 words, quoting the student's own words for the move that determined the level. Short paragraphs. No lists. Do not over-validate; avoid generic praise (great answer, excellent, well done).

**1**: Accepts or rejects the extrapolation on the strength of the fit. Treats R-squared above 0.95 as licensing the projection, or dismisses the whole thing as "just a line on a graph" without naming what would have to hold. *Example: "The data is strong, R-squared over 0.95 across three hardware generations is about as good as it gets in this kind of work. Eight doublings at nine months each really is six years, so 2032 seems like a reasonable projection unless something unexpected happens."*

**2**: Objects that the trend might not continue and lists possible obstacles (physical limits, harder problems, funding), but treats these as external events that might interrupt a valid extrapolation rather than as assumptions the extrapolation already requires. No distinction between what the data supports and what it does not. *Example: "Trends like this usually break at some point. They could hit a physical limit, or the remaining problems could be much harder than the ones they have solved, or the funding could dry up. So 2032 is optimistic. I would say it takes longer than they think."*

**3**: Names at least two of the required assumptions as assumptions (construct stability across two orders of magnitude, or task homogeneity, or mechanism continuity), separates the supported claim from the unsupported one, and states that the fit's quality does not carry into the extrapolated range. The pass bar. *Example: "The R-squared tells you the line describes the six years they measured. It says nothing about the range they have not measured, and the whole claim is about that range. For the arithmetic to work, depth at 10,000 has to be the same thing as depth at 40. I doubt it is: what stops a run at step 40 is probably a hardware fault, and what would stop a run at step 5,000 is more likely drift or an accumulated error nobody specified a rule for. That is a different failure mode wearing the same units. There is also the question of which tasks they measured on, since the hardest ones are exactly the ones that would have been left out of a test set six years ago. What the data does establish is that this grew fast and regularly on their own benchmark for six years, which is not nothing."*

**4**: As above, plus explicitly refuses to set confidence from the fit and instead reaches for an outside view, giving a rough base rate for a strong trend surviving eight further doublings and stating a confidence well below what the fit invites. *Example: Adds "So I would not put my confidence in 2032 anywhere near what the R-squared suggests. The right reference class is not this curve, it is technological trends generally, and strong regular trends holding across eight more doublings without a break is not the common case. Trend breaks short of a genuine discontinuity are ordinary. I would sit somewhere around 20 percent on the 2032 claim, and most of that number comes from the base rate rather than from anything in their chart."*

**5**: As above, plus notices that the 10,000-step threshold is itself an unmeasured assertion, so even a perfectly continued trend would not settle the question the commentator asked. *Example: Adds "There is a second problem underneath the first. The 10,000 figure is asserted, not measured, and nobody has demonstrated that depth is the binding constraint on autonomous materials discovery at all. If autonomy needs 10,000 steps and something the metric does not capture, such as choosing which chemistry is worth trying, then even a trend that continues perfectly lands you at 10,000 steps of a process that still is not autonomous. The extrapolation and the threshold are separate claims and only one of them has data behind it. I would ask what happened to the runs that reached the current depth limit: if they were producing useful chemistries and simply stopped, that is evidence for the threshold, and if they were producing nothing worth having, the metric and the goal have come apart."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/Trends - Predict The Metric - PQ]]
notes:: Predict-before-you-read on the METR time-horizon result; the student commits to a number first.

## Lens:
source:: [[../Lenses/Trends - What A Curve Licenses]]

## Lens:
source:: [[../Lenses/Trends - The Base Rate For Breaks]]
