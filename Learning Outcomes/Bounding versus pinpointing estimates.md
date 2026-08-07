---
id: 'b64206ee-e2e8-4687-ab9d-a2308e86cfde'
learning-outcome: Given an unfamiliar quantitative estimate of a future event, determine whether the estimate's method can locate the answer or only bound it from one side, state which side the bound is on and what assumption puts it there, and name a case where the bound is uninformative.
domain: none
stage: intermediate
---
## Test:
id:: 4ee54bf7-d40a-4ac5-a63b-685628637d5e

#### Question
content:: A public-health team wants to know when a laboratory will first synthesise a self-replicating artificial cell. They reason: the smallest known free-living bacterium has a genome of about 580,000 base pairs, so a synthetic cell needs at least that much designed DNA. Synthesis cost per base pair has fallen steadily for two decades. They divide the required genome size by the projected synthesis throughput and announce: "first synthetic cell by 2041."

Their number is not useless, but it is not what they think it is.

What can this method actually establish, and what can it not? Name the direction the estimate is wrong in, state the assumption that fixes that direction, and describe a situation in which their 2041 figure would tell a decision-maker nothing at all.

max-time:: 12:00

assessment-instructions:: The student has completed a module on timeline estimation methods, including biological anchors and compute-centric extrapolation, and the distinction between bounding and pinpointing an estimate. This test presents an unfamiliar domain (synthetic biology, not AI) so that an answer reconstructing the assigned readings cannot pass.

The capability being tested: recognising that a method built from a *requirement* plus a *trend in the resource that satisfies the requirement* produces a one-sided bound, not a location; identifying which side; naming the assumption that fixes the side; and recognising when the bound is slack enough to be decision-irrelevant.

The underlying structure, for your reference as grader:
- The genome-size figure is a lower bound on required synthesis. It says: you cannot do this with less. It is silent on everything else the task needs (assembly, booting the cell, error correction, regulatory sequence design, the unknown-unknowns of making the thing actually live).
- Therefore the method yields an estimate that is too EARLY, i.e. the true date is 2041 or later. The bound is from below on difficulty, hence from below on date.
- The assumption fixing the direction: that DNA synthesis throughput is the binding constraint. If any other step is harder, the estimate slips later and never earlier.
- The bound is uninformative when the slack is large relative to the decision horizon: if the true limiting step is a scientific problem nobody knows how to attack, "2041 or later" is compatible with 2041 and with 2300, so a decision-maker choosing between funding this year and funding in ten years learns nothing.
- Strong answers may note the symmetric point: a method that enumerated every known difficulty and summed them would bound from the other side (too LATE), because it cannot include shortcuts nobody has thought of. The two bounds together are more informative than either.

Grade reasoning, not agreement. A student who argues the estimate is closer to a location than I have described, and argues it well from the structure of the method, can score at the pass bar or above.

Response: assign one level, then justify it in 100 to 180 words, quoting the student's own words for the move that determined the level. Short paragraphs. No lists. Do not over-validate; avoid generic praise (great answer, excellent, well done).

**1**: Treats the estimate as a prediction and evaluates only whether 2041 seems plausible, or rejects the method wholesale as "just a guess" without identifying any structure. No notion of directionality. *Example: "This is way too speculative. You cannot predict science like this, there are too many unknowns, and picking a specific year like 2041 gives false confidence. They should present a range instead."*

**2**: Notices that the method leaves things out and that the estimate is therefore unreliable, but does not commit to a direction, or commits to a direction without an assumption supporting it. Often lists omitted factors as a grievance rather than as a signed correction. *Example: "They are only counting DNA synthesis. But building a cell also needs assembly, testing, and getting it to actually replicate, none of which are in the model. So the estimate could be off in either direction and 2041 should not be trusted."*

**3**: Identifies the estimate as a one-sided bound, states the correct direction (too early, true date is 2041 or later), and names the assumption that fixes it (synthesis throughput is the binding constraint; every omitted step can only add time). The pass bar. *Example: "The genome size gives a floor on how much synthesis is needed, so what they have computed is the earliest the synthesis part could be done. Every other step they left out (assembly, booting it, debugging a cell that does not divide) can only push the date later, never earlier, because none of them make synthesis faster. So 2041 is a lower bound on the date, not an estimate of it. The assumption doing the work is that synthesis is the bottleneck; if it is not, the bound is loose."*

**4**: As above, plus articulates when the bound is decision-irrelevant by relating the slack to a decision horizon, rather than just saying "it could be much later." *Example: Adds "The bound is only useful if you have some independent reason to think the slack is small. If the real obstacle is that nobody knows how to make a designed genome boot, then '2041 or later' is equally consistent with 2045 and with never, and a funder deciding between acting now and acting in a decade gets nothing from it. A bound is informative in proportion to how tight you can argue it is, and they have not argued tightness at all."*

**5**: As above, plus recognises the symmetric construction: a method built from enumerated difficulties bounds from the opposite side, and the two together are more informative than either, because the answer is bracketed. *Example: Adds "The fix is not a better single number. If you separately estimated by listing every known hard step and costing each one, you would get a bound from the other side, and it would be too late rather than too early, because no enumeration can include the shortcut nobody has thought of yet. Running both gives you a bracket, and the width of the bracket is the honest output. A method that returns one number is hiding which side of the answer it lives on."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/Timelines - What A Model Is For - PQ]]
notes:: Primes the "an estimate is a location" intuition before the readings break it.

## Lens:
source:: [[../Lenses/Timelines - Bounding Not Pinpointing]]
