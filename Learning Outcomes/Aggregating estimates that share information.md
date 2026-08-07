---
id: 'bb7a45a3-3a37-4741-b102-9c654bed4164'
learning-outcome: Given several estimates of the same quantity, determine how much the estimators' information overlaps, state whether the correct aggregate lies inside or outside the range of the individual estimates, and explain why averaging is the right move under one overlap structure and the wrong move under another.
domain: none
stage: intermediate
---
## Test:
id:: b39c1796-cc71-4996-9deb-a896cc1baa53

#### Question
content:: A regulator must decide whether a chemical plant will exceed its emissions limit next quarter. Base rate across all comparable plants: 20% do.

Three engineers assess this plant. Independently, without conferring, each returns a probability:

- Engineer A: 45%
- Engineer B: 40%
- Engineer C: 50%

The regulator averages them and reports 45%.

Part 1. Suppose each engineer inspected a different subsystem, and none saw the others' subsystem. Is 45% the right aggregate? If not, is the right number above 50% or below 40%, and what fact about the three assessments forces it there?

Part 2. Now suppose instead that all three attended the same briefing, saw the same maintenance log, and formed their views from it, differing only in temperament. Same three numbers. Does your answer to Part 1 change, and why?

Part 3. The regulator has the three numbers but does not know which of the two worlds she is in. What could she ask the engineers, without asking them to re-forecast, that would tell her?

max-time:: 20:00

assessment-instructions:: The student has completed a module on forecasting method, including aggregation and the extremization result. The chemical-plant setting is unfamiliar so a student who memorised the coin example from the reading cannot simply restate it; they must recognise the same structure in new clothes.

The mathematical object being tested is how the correct aggregate depends on the CORRELATION STRUCTURE of the estimators' evidence, not on the estimates themselves. The three numbers are identical in both worlds; the right answer differs. That is the whole point, and a student who thinks the answer can be computed from the three numbers alone has missed it.

Part 1 (independent evidence). All three moved the same direction from the 20% prior, on non-overlapping evidence. Each engineer's update is evidence, and the regulator holds all three. She therefore knows more than any individual and should extremize: the correct aggregate is ABOVE 50%, outside the range of the inputs. The fact that forces it is the agreement in direction combined with the independence of the evidence: three separate subsystems each independently look bad. Averaging discards the information carried by the concurrence and systematically under-updates.

Part 2 (shared evidence). The three are near-duplicates of one assessment. There is effectively one piece of evidence reported three times. The aggregate should be roughly a single engineer's number, around 45%, and certainly not extremized. The spread reflects temperament, not information. A student who says "average is now correct, or nearly so" is right; the deeper statement is that with fully shared evidence the sample size is one, so the correct move is closer to taking one of them than to combining them.

Part 3 (diagnosing the structure). The good answers ask about the EVIDENCE, not the conclusion: what did you look at, what would have changed your mind, what is the single fact most responsible for your number. If the three name different facts, the evidence is disjoint. If they name the same maintenance log, it is shared. Asking them to re-forecast after hearing each other is explicitly excluded because it destroys the independence being measured, and strong students may notice that this is exactly why a group discussion before eliciting is costly. Also creditable: check whether the three cite common sources, or ask each what they would have said absent the briefing.

Grade reasoning, not agreement. A student who argues for a smaller extremization on the grounds that "different subsystems" still share a plant-wide common cause is reasoning correctly and can score at or above the pass bar.

ABOUT THE COLD-OPEN COMPARISON. This unit opened with a Cold Open in which this student answered the same underlying problem cold, before any reading. YOU CANNOT SEE THAT ANSWER: the platform has no mechanism for surfacing a student's earlier responses to you, so do not claim to have read it and do not guess at what it said.

Ask them to scroll back to the THREE TECHNICIANS problem in the Cold Open and paste the number they gave. It is in this module's chat history, above the current exchange, so it is a small ask rather than an impossible one. If they bring it, spend two or three sentences of your justification on the delta, quoting both. The distinction worth drawing is the one the unit warned them about: acquiring vocabulary is not the same as acquiring the move, so if the cold answer already had the reasoning and the new one is the same thinking in better words, say that plainly. It is useful information and not a failure.

If they decline or cannot find it, grade the current answer alone and say nothing further about the comparison. Never invent what their earlier answer contained.

Response: assign one level, then justify it in 100 to 180 words, quoting the student's own words for the move that determined the level. Short paragraphs. No lists. Do not over-validate; avoid generic praise (great answer, excellent, well done).

**1**: Treats aggregation as an arithmetic question about the three numbers. Answers 45% in both worlds, or objects that three is too small a sample, without engaging with evidence structure at all. *Example: "45% is the mean, so it is the best estimate available. Three data points is not many, and I would want more engineers before making a regulatory decision, but there is no reason to prefer any number outside the range they gave."*

**2**: Recognises that the two worlds differ and that shared information is somehow a problem, but does not get the direction right, or treats the shared-evidence case as the one needing adjustment while leaving the independent case at the average. Frequently says the correct aggregate must lie inside the range because "you cannot know more than the experts." *Example: "In the second case the engineers are not really independent, so averaging overstates the evidence and I would trust the number less. In the first case the average is fine. Either way the answer has to be somewhere between 40 and 50, because the regulator has no information of her own."*

**3**: Gets both directions right with the mechanism: independent concurring evidence licenses an aggregate outside the range, shared evidence does not, and the reason is that the regulator holds the union of the evidence. Proposes at least one diagnostic that asks about evidence rather than conclusions. The pass bar. *Example: "In the first world the right number is above 50%. Each engineer started from the 20% base rate and moved up on evidence nobody else saw, so the regulator is holding three separate pieces of bad news, and she knows more than any one of them. The concurrence is itself the information, and averaging throws it away. In the second world that argument disappears: they all read the same log, so there is one piece of evidence with three readings, and around 45% is right. To tell the worlds apart I would ask each engineer what single observation drove their number. Three different answers means three pieces of evidence; the same answer three times means one."*

**4**: As above, plus recognises that the two worlds are endpoints of a continuum and that the correct extremization scales with the degree of non-overlap. *Example: Adds "These are the extremes and real cases sit between them. Even the three subsystem inspections are not fully independent: they are inspections of one plant with one maintenance culture and one budget, so some of what each engineer saw has a common cause, and I should extremize less than full independence would justify. The right way to think about it is that extremization is a dial set by how much of the evidence is disjoint, not a switch. Assuming independence when it is partial is how a committee talks itself into confidence it has not earned."*

**5**: As above, plus notes that the elicitation procedure determines which world you are in, so the structure is a design choice rather than a fact to be discovered. *Example: Adds "The deeper point is that the regulator partly chooses which world she is in, and she chose before she asked. If she had briefed all three together, she would have manufactured world two and destroyed the information that makes world one worth having, while the numbers on the page would look the same and might even look better, because they would agree more tightly. Tighter agreement among people who share a source is not more evidence, it is less, and it is the failure mode that makes an expert consensus a weaker signal than it appears. So the aggregation question cannot be separated from the elicitation design: what you can correctly do at the end is fixed by how you gathered at the start."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/U2 - Three People Agreeing - PQ]]
notes:: Pumps the wrong intuition (the answer must lie between the inputs) so the reading can break it.

## Lens:
source:: [[../Lenses/U2 - Average Then Extremize]]
