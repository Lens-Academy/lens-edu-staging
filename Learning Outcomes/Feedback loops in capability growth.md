---
id: '66af2dd6-ea05-4cf9-9cf6-ad39b7c58ebf'
learning-outcome: Given an unfamiliar system in which an output is fed back into the process that produced it, determine whether the coupling produces a bounded speedup or unbounded acceleration, identify the specific quantity whose behaviour decides which, and state what would have to be measured to tell the two apart in advance.
domain: none
stage: intermediate
---
## Test:
id:: 'dc99e11b-2967-4cde-9b55-f7ee821c107c'

#### Question
content:: Two research directors describe their labs.

**Director A:** "We automated our literature review. Every researcher now covers four times as many papers per week. We also automated experiment scheduling, which saved another 20 percent of their time. Between the two, we are getting through roughly five times the work we did last year."

**Director B:** "Our lab designs lab robots. The robots we shipped last year are now the ones assembling next year's robots. Each generation assembles the next generation about 15 percent faster than the one before it did, and we have no plan to stop."

Both labs are speeding up. They are not speeding up in the same *kind* of way.

Describe the difference in terms of how the speedup accumulates over time. For Director B's lab, identify the single quantity that determines whether the process runs away or settles down, and say what happens on either side of its critical value. Then: what measurement would you demand from Director B, before believing either outcome?

max-time:: 15:00

assessment-instructions:: The student has completed a module on takeoff speeds, compute-centric growth models, and the distinction between linear combination and recursive coupling. This test uses lab robots rather than AI R&D so that an answer reciting the intelligence-explosion literature cannot pass. The student must recognise the same mathematical object in an unfamiliar dress.

The capability being tested: distinguishing an additive or multiplicative combination of one-time improvements (bounded, converges to a ceiling) from a recursive loop in which output re-enters as input (potentially unbounded, governed by a gain parameter), identifying the gain-versus-diminishing-returns quantity as the decider, and naming the measurement that discriminates.

The underlying structure, for your reference as grader:
- Director A has a LINEAR COMBINATION. Two independent speedups compose once. Amdahl's law applies: once literature review takes zero time, you cannot save more than the fraction it occupied. Each improvement is a one-time gain on a fixed denominator; total speedup converges to a ceiling set by the un-automated remainder. Iterating does not help because the output (papers reviewed) is not an input to the reviewing process.
- Director B has a RECURSIVE LOOP. Robot capability is both output and input. The relevant object is the return on each round: if each generation's 15 percent improvement is applied to producing a next generation that is itself improved, the improvements compound rather than add.
- The deciding quantity is HOW THE GAIN ITSELF BEHAVES as capability accumulates: does a generation that is 15 percent better produce a next generation that is 15 percent better again, or less, and if less, how fast does that decay?

  GRADER, THIS MATTERS AND IS EASY TO GET WRONG. There is no critical value at "gain equals one", and a student who says so should be corrected, gently, not credited. Work the model: if each generation builds the next g faster, cycle times are T0, T0/(1+g), T0/(1+g)^2, ... and the total time to arbitrarily many generations is T0/(1 - 1/(1+g)), which is FINITE for ANY constant g > 0. A 0.1 percent gain gives 1001 x T0. So sustained constant gain, however small, is already the runaway case; it is not a knife edge.
  Nor does "diminishing" imply a ceiling. The exact condition: capability is the product of (1 + g_n) over rounds, and that product converges if and only if the SUM of the gains converges. So g_n = 0.15/n is a harmonic series, diverges, and capability grows without bound however slowly; g_n = 0.15/n^2 is summable and settles to a finite ceiling. 1/n^2 is an EXAMPLE of fast-enough, not the threshold: anything summable does it, including 1/n^1.01, which converges to a much larger ceiling. So there are at least three regimes, not two: blowup in finite time, unbounded but decelerating, and a true ceiling.
  In continuous form, with dc/dt = k c^a: a > 1 is a genuine finite-time singularity, a = 1 is pure exponential (unbounded, never infinite at finite time), a < 1 is polynomial and still unbounded. The critical exponent is a = 1, and AT the critical value the answer is exponential growth, not blowup.
  What to require at the pass bar is therefore the SHAPE of the decay, not a comparison to one. Credit a student who says "it depends whether the per-round gain holds up, decays slowly, or decays fast, and those give different answers"; credit highly a student who notices that "diminishing returns" is not by itself enough to get a ceiling. Do NOT mark down a student who constructs a counterexample to the ceiling claim, they are right.
- The measurement to demand: not the per-generation speedup figure, which is compatible with both outcomes, but the TREND in that figure across generations already completed, together with how much of the assembly process is actually inside the loop. If generation-over-generation improvement was 15, then 14, then 12 percent, it is decaying and the process settles. If it was 15, 15, 16, the loop has gain. Strong answers may also ask what fraction of robot production is automated at all, since an un-automated remainder caps the loop the same way Amdahl caps Director A.

Grade reasoning, not agreement. A student who argues Director B's lab will in fact settle down, and locates that argument in the decay of the gain parameter or in an un-automated bottleneck, is demonstrating the capability, not failing to.

Response: assign one level, then justify it in 100 to 180 words, quoting the student's own words for the move that determined the level. Short paragraphs. No lists. Do not over-validate; avoid generic praise (great answer, excellent, well done).

**1**: Treats both as "exponential growth" or both as "just getting faster," with no structural distinction. May rank them by size of the numbers rather than by the shape of the process. *Example: "Both labs are growing exponentially, but A is growing faster right now since five times beats 15 percent. B will catch up eventually because 15 percent compounds. Exponential growth always wins in the long run, so B is the one to watch."*

**2**: Notices that B's improvement feeds back on itself and A's does not, but describes the consequence only qualitatively (B "keeps going," "compounds") without identifying any quantity that decides the outcome, and does not distinguish compounding-to-a-ceiling from unbounded acceleration. *Example: "A got two separate improvements that add up to a fixed amount. B is different because the robots build the robots, so it is a feedback loop and the gains compound each cycle instead of happening once. That means B could accelerate a lot more than A over time."*

**3**: Correctly separates one-time composition (bounded by the un-improved remainder) from recursive coupling, and identifies the deciding quantity as how the per-cycle gain behaves over successive rounds, stating more than one possible outcome. The pass bar. *Example: "A's two savings each apply once to a fixed workload, so they multiply out to a single number and then stop. Even if literature review dropped to zero, the speedup is capped by whatever is left. B is different in kind: the improved robots are the thing doing the improving, so each round's gain applies to a process that is itself already improved. Whether that runs away depends on what happens to the 15 percent as generations get better. If it holds up, cycle times shrink geometrically and the generations arrive faster and faster. If it decays, the answer depends on how fast: a slow decay still grows without bound, and only a fast enough decay settles to a ceiling. To tell which, I would want the generation-over-generation numbers so far, not a single 15 percent."*
Do not require the phrase "gain parameter" or any other vocabulary. A student who says "it depends how fast the improvement per round shrinks, and shrinking is not enough on its own to stop it" has the mechanism and passes.

**4**: As above, plus specifies the measurement as the *trend* in the gain rather than its level, and explains why a single-generation figure cannot discriminate. *Example: Adds "The 15 percent on its own is worthless for this, because both futures are consistent with it. I want the series: what was it for generation one, two, three. A sequence like 15, 14, 12 is a decaying gain and the thing settles. A flat or rising sequence is the runaway case. The number to watch is the ratio between consecutive improvements, not any improvement."*

**5**: As above, plus reasons correctly about what the un-automated remainder does and does not bound. *Example: Adds "The part of building a robot that better robots cannot speed up puts a floor under the cycle time: if 30 percent of assembly is fixed, no amount of gain gets a generation out faster than about a third of the original cycle. But notice what that does and does not do. It caps the RATE at which generations arrive; it does not cap capability. Generations keep arriving, just at a steady clip instead of an accelerating one, so capability still grows without bound, now linearly in time rather than exploding. The un-automated remainder converts a runaway into steady progress, not into a plateau. So my second question to B is what fraction of the pipeline is inside the loop, and my reason is not that it stops the process, it is that it decides whether I am looking at something that finishes before I can react or something I can watch and intervene on."*
GRADER: the previous version of this rubric claimed the remainder "caps B exactly the way un-automated work caps A" and that a high gain on a small fraction "stops". That is wrong and was corrected: Amdahl bounds a speedup RATIO on a fixed workload, while the gain governs a RECURRENCE on a growing quantity. They are not the same mathematics. A student who says the remainder produces a ceiling on capability has made the error this level is designed to catch, and belongs at 3 or 4, not 5. A student who spots the distinction unprompted is doing exactly the intended move.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/Takeoff - Two Kinds Of Faster - PQ]]
notes:: Predict-before-you-read on the linear versus recursive distinction, before any reading names it.

## Lens:
source:: [[../Lenses/Takeoff - Linear Sums And Recursive Loops]]

## Lens:
source:: [[../Lenses/Takeoff - Smoothness Is Not Slowness]]
