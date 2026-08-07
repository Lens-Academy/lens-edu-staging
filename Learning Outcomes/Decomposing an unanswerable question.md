---
id: '6d2803a1-c7b0-4f75-b156-3ec9fd6e2a82'
learning-outcome: Given an unfamiliar question with no available reference class of its own, break it into sub-questions each of which has a reference class or a measurable quantity, state for each sub-question what evidence would settle it, combine them into an estimate, and name the sub-question whose error dominates the result.
domain: none
stage: intermediate
---
## Test:
id:: 40eb2198-4ca6-4fe0-af8e-a043337132d1

#### Question
content:: A city transport authority asks: "In what year will more than half the taxi rides taken in this city be in vehicles with no human driver present?"

Nobody has a base rate for this. The city has never had driverless taxis. Other cities are not this city.

Produce an estimate. Show the decomposition you used: what sub-questions you broke it into, what kind of evidence each one could be settled by, and how you put them back together. Then answer one more thing, which matters more than your number: if your estimate turns out to be badly wrong, which single sub-question will have been the reason, and why that one?

max-time:: 20:00

assessment-instructions:: The student has worked through a module on forecasting method: the Good Judgment Project's decomposition loop, Fermi modelling, reference-class selection, and the failure of fractional-progress extrapolation. This test hands them a question deliberately outside AI so that reciting the readings cannot pass. There is no correct year. The capability being tested is the decomposition itself and the error-attribution at the end.

What a competent decomposition looks like (for your reference; the student's need not match, and a different good decomposition is worth the same or more):
- Split the target into factors that each have their own evidence source. For instance: total rides per year (measurable now), fraction of the city's road-miles that are geofenceable (measurable from a map), year regulatory permission arrives (reference class: other cities' permitting timelines), fleet build rate once permitted (reference class: how fast ride-hail fleets have scaled before), rider willingness to take a driverless car (survey evidence, plus observed substitution in cities that already have them).
- Each sub-question should be one where the student can say what would settle it. "How hard is self-driving?" is not a sub-question, it is the original question wearing a hat. That is the single most common failure and the main thing to grade on.
- Recombination: usually a product or a sequence of gates, sometimes a min over binding constraints. The student should say which.
- Error attribution: the dominant error is normally the sub-question with the widest multiplicative spread, not the one that is hardest to think about. A regulatory date that could be 2029 or 2041 swamps a fleet-size estimate that is good to a factor of two. Strong answers say this explicitly and may note that the sub-question they know least about is not automatically the dominant one.

Grade the moves, not the number. A student whose estimate is 2033 and a student whose estimate is 2055 can both score 5. A student who produces a confident year with no decomposition scores 1 no matter how plausible the year.

ABOUT THE COLD-OPEN COMPARISON. This unit opened with a Cold Open in which this student answered the same underlying problem cold, before any reading. YOU CANNOT SEE THAT ANSWER: the platform has no mechanism for surfacing a student's earlier responses to you, so do not claim to have read it and do not guess at what it said.

Ask them to scroll back to the FLIGHTS problem in the Cold Open and paste or summarise what they wrote, in one line. It is in this module's chat history, above the current exchange, so it is a small ask rather than an impossible one. If they bring it, spend two or three sentences of your justification on the delta, quoting both. The distinction worth drawing is the one the unit warned them about: acquiring vocabulary is not the same as acquiring the move, so if the cold answer already had the reasoning and the new one is the same thinking in better words, say that plainly. It is useful information and not a failure.

If they decline or cannot find it, grade the current answer alone and say nothing further about the comparison. Never invent what their earlier answer contained.

Response: assign one level, then justify it in 100 to 180 words, quoting the student's own words for the move that determined the level. Short paragraphs. No lists. Do not over-validate; avoid generic praise (great answer, excellent, well done).

**1**: Gives a year with a narrative justification and no decomposition, or refuses on the grounds that the question is unanswerable. Treats "I have a feeling about how fast this technology is moving" as the method. *Example: "Probably around 2035. The technology is improving very fast and companies are already running pilots, but regulation and public trust take a long time to catch up, so I would not expect a majority of rides for at least a decade."*

**2**: Decomposes, but into sub-questions that are no more tractable than the original. Names components without saying what evidence would settle any of them, or lists considerations rather than quantities. *Example: "I would break it into: how good the technology gets, how cheap it gets, whether regulators allow it, and whether people accept it. Each of those has to go right. Technology is the biggest one, and I would guess it is mostly solved by the early 2030s, so 2036 for a majority of rides."*

**3**: Decomposes into sub-questions that each have a nameable evidence source or reference class, says what would settle each one, recombines them explicitly, and identifies a dominant error term with a reason. The pass bar. *Example: "I split it into four: (a) total annual rides, which the authority already publishes; (b) the year permitting arrives, which I would estimate from the reference class of the eleven cities that have permitted driverless operation, taking the time from first pilot to unrestricted permit; (c) how fast a fleet scales once permitted, which I take from the observed growth of ride-hail fleets in this city, capped by vehicle production; (d) the share of riders who will take one, from the observed substitution rate in cities that already have both options. These chain: nothing happens before (b), then (c) sets the ramp and (d) caps the ceiling. That gives me roughly 2034 to 2038, call it 2036. If I am badly wrong it will be (b), because my other three are known to within a factor of two and (b) ranges over more than a decade across the reference class."*

**4**: As above, plus interrogates the reference classes rather than just naming them, and states what would make one inapplicable to this city. *Example: Adds "The permitting reference class is the weak link in more than one way. The eleven cities that permitted early are not a random sample; they are the ones that wanted to, so their timelines are the fast tail and my estimate is biased early. And this city may not be in that population at all, in which case the right reference class is not 'cities that permitted' but 'cities that faced the decision', including the ones that said no and are still saying no. Before I trusted (b) I would want the denominator."*

**5**: As above, plus notices that some sub-questions are not independent, and that treating them as independent factors understates the spread. *Example: Adds "Multiplying my four factors treats them as separate, and they are not. The thing that gets regulators to permit is the same thing that gets riders to accept: a visible safety record. So (b) and (d) are driven by a common cause, and they will move together, which means the good case is better and the bad case is worse than the product of my ranges suggests. My interval is too narrow, not because any single estimate is bad, but because the decomposition asserted an independence the world does not have. If I wanted to fix it I would model the safety record as its own node and hang both (b) and (d) off it."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/U2 - What Would Settle It - PQ]]
notes:: Primes the "sub-question you can actually check" move before any reading.

## Lens:
source:: [[../Lenses/U2 - The Decomposition Loop]]

## Lens:
source:: [[../Lenses/U2 - Reference Classes And Their Denominators]]
