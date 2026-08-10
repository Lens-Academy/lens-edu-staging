---
id: '100c2fee-ecc0-4270-8023-efaac2efa4ce'
learning-outcome: Given a trend extrapolated forward to a conclusion, identify the functional form the extrapolation assumes, name the interaction between parts of the system that would break that form, state which direction the resulting error runs, and construct the alternative curve that the same data also supports.
domain: none
stage: intermediate
---
## Test:
id:: 348a053f-c379-4f8a-9d2b-0d5efd34a2a4

#### Question
content:: A hospital network is estimating when a new diagnostic system will handle the majority of its imaging caseload. They survey their radiologists annually with one question: "What fraction of your diagnostic work could this system do today, unsupervised?"

The answers were 4% in 2022 and 16% in 2026. The analysts fit a line through the two points: 3 percentage points a year, so 100% around 2054. They publish "roughly thirty years out" and the network plans hiring accordingly.

Assume the survey answers are honest and accurate. The 2054 figure is still not a forecast of anything.

Three things:

1. Write down the equation the analysts are implicitly using, and say what it assumes about how the remaining work relates to the work already done.

2. Describe a concrete way the parts of this system could interact that makes that equation wrong, and say whether it makes 2054 too early or too late. Note that both answers are defensible; the reasoning is what counts.

3. Draw a second curve through the same two data points that implies a materially different date. State what would have to be true about radiology for your curve to be the right one, and what observation between now and 2030 would distinguish it from the analysts' line.

max-time:: 25:00

assessment-instructions:: The student has completed a module on forecasting method, including the fractional-progress survey method and its 372-year result, {--{"author":"Lauren's AI","timestamp":1786379726308}@@scaling-law extrapolation, --}and the general problem of inferring a functional form from a trend. This test is set in radiology, not AI, so an answer that reconstructs the assigned readings cannot pass. The underlying object is a functional-form question: two points constrain a curve only if you have already assumed its shape, and the shape assumption is doing all the work.

The mathematics the student is being asked to make visible:

- Part 1. The analysts assume progress is LINEAR IN THE FRACTION REMAINING BEING UNIFORM: d(fraction)/dt is constant, so every remaining percentage point costs the same as every point already done. Equivalently, the work is a homogeneous pile and they have measured the rate of eating it. The student does not need this vocabulary, but must state the uniformity assumption in some form. Simply writing "f(t) = 0.03t + c" without saying what it assumes about the remaining work is a partial answer.

- Part 2. Interactions that break uniformity, in either direction. Good answers name a mechanism, not just a possibility.
  - Making it LATE (2054 too early): the remaining cases are the hard ones. Every year the system takes the easiest remaining slice, so the residual is adversely selected and the marginal cost per point rises. This is the standard shape and produces the asymptote that never reaches 100%. It is also the mechanism behind the 372-year result the students saw: linear extrapolation of a self-selecting residual.
  - Making it EARLY (2054 too late): a threshold or a coupling. If the system reaching some capability level changes the regulatory status, or changes which cases get routed to it, or if one architectural advance solves a class of failures at once, the fraction jumps rather than creeping. Also: the radiologists are estimating unsupervised handling, but the deployed system may work supervised at first, and the supervision requirement can be removed by a single institutional decision rather than by incremental capability.
  - Best answers note the survey itself is an interaction: radiologists' answers are not independent measurements, they are shaped by what their colleagues and the vendor say, so the two data points may be correlated in a way that flattens or steepens the apparent trend without anything in the world changing.

- Part 3. Any curve through (2022, 0.04) and (2026, 0.16) with a stated mechanism. The obvious ones:
  - Exponential / doubling: 4 to 16 is two doublings in four years, so 100% arrives around 2031. Requires that capability compounds, e.g. each solved case class generates training data that helps the next.
  - Logistic: same early behaviour as the exponential, saturating short of 100%, so "majority" arrives in the early 2030s but 100% never does. Requires a hard residual.
  - Asymptotic / power law approaching a ceiling below 1: never reaches a majority. Requires that some fraction of cases is irreducibly a judgment call.
  The distinguishing observation is the load-bearing part. A student who names a curve but cannot say what measurement in 2028 would tell the two apart has not finished the move. The general answer: measure the SHAPE, not the level, by taking annual rather than four-year readings, and by disaggregating the caseload so you can see whether the system is advancing across case types or saturating within easy ones.

Grade reasoning, not the date. A student who argues 2054 is too late and one who argues it is too early can both score 5. A student who says only "extrapolation is unreliable" scores 1 regardless of how sophisticated the surrounding prose is.

ABOUT THE COLD-OPEN COMPARISON. This unit opened with a Cold Open in which this student answered the same underlying problem cold, before any reading. YOU CANNOT SEE THAT ANSWER: the platform has no mechanism for surfacing a student's earlier responses to you, so do not claim to have read it and do not guess at what it said.

Ask them to scroll back to the HOSPITAL ON-TIME-STARTS problem in the Cold Open and paste or summarise what they wrote, in one line. It is in this module's chat history, above the current exchange, so it is a small ask rather than an impossible one. If they bring it, spend two or three sentences of your justification on the delta, quoting both. The distinction worth drawing is the one the unit warned them about: acquiring vocabulary is not the same as acquiring the move, so if the cold answer already had the reasoning and the new one is the same thinking in better words, say that plainly. It is useful information and not a failure.

If they decline or cannot find it, grade the current answer alone and say nothing further about the comparison. Never invent what their earlier answer contained.

Response: assign one level, then justify it in 120 to 200 words, quoting the student's own words for the move that determined the level. Short paragraphs. No lists. Do not over-validate; avoid generic praise (great answer, excellent, well done).

**1**: Rejects the extrapolation on general grounds without producing a functional form, an interaction, or an alternative curve. Treats "the future is uncertain" as the analysis. *Example: "You cannot draw a straight line through two data points and get a prediction thirty years out. Technology does not work like that, there are too many variables, and the survey is subjective anyway. They should have used a range instead of a single year."*

**2**: Identifies that the linear assumption is questionable and gestures at the hard-cases-remain idea, but does not write the assumption down as a claim about the remaining work, or gives an interaction without a direction, or offers an alternative curve without a mechanism or a distinguishing observation. *Example: "The line assumes constant progress, which is probably wrong because the last cases are usually the hardest. So it will take longer than 2054. You could also fit an exponential through those points, which would be much faster, so really the two points do not tell you much."*

**3**: States the uniformity assumption explicitly as a claim about the remaining work, names a concrete interaction with a mechanism and a signed direction, and produces a second curve with a stated condition for it being right. The curve must actually pass through both given points, and any date the student reads off it must be consistent with that curve: a logistic saturating below 1 cannot reach 100% at all, so "logistic, hitting 100% in 2029" is a level-2 answer no matter how well argued, and you should say which of the two is wrong. The pass bar. *Example: "Their equation is f(t) = 0.04 + 0.03(t - 2022), and the hidden claim is that the last 84 percentage points are made of the same stuff as the first 16. Here is why that is wrong: the system is not sampling cases at random, it is taking the ones it can already do. Each year the leftover pile is more adversely selected than the year before, so the per-point cost climbs and the curve flattens. That makes 2054 too early, and in the limit the honest answer may be that it never reaches 100%. An alternative through the same points: two doublings in four years, so an exponential hitting 100% around 2031. That would be right if each solved case class fed the next one, for instance by generating labelled data or by revealing a shared failure mode. To tell them apart before 2030 I would stop taking one reading every four years and start taking one a year, because the two curves diverge in the second derivative and I currently have no measurement of it at all."*

**4**: As above, plus recognises that the measurement instrument is part of the system rather than a window onto it, and reasons about how that changes the inference. *Example: Adds "The bigger problem is that the survey is not an observation of the system, it is an observation of radiologists. They are answering a question about their own replaceability, in an institution that has just published a hiring plan based on the previous answer. Whatever the true curve is, this instrument will be smoothest exactly when the underlying change is most disruptive, because that is when people have the strongest reason to answer conservatively. So the flatness of the trend is weak evidence that the world is flat, and I would want an outcome measure, such as the fraction of scans actually read without a second pair of eyes, before I trusted any curve at all."*

**5**: As above, plus articulates the general point that the two data points constrain the curve only after a family has been assumed, and identifies what kind of knowledge does the constraining. *Example: Adds "Underneath all of this is that two points do not select a curve. They select a curve within a family, and the family came from the analyst, not from the data. Infinitely many functions pass through (2022, 0.04) and (2026, 0.16), and choosing among them is a claim about the mechanism, not a claim the data can adjudicate. This is why the direction of my error is not something I can read off the numbers: the linear fit implies a uniform pile, the exponential implies a compounding process, the logistic implies a hard residual, and those are three different theories of radiology which happen to agree on two afternoons in 2022 and 2026. The right output is not a date, it is: here are the three mechanisms, here is the date each implies, and here is the measurement that separates them. Anyone who publishes only the date has hidden the assumption that produced it."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/U2 - The Shape Of The Remaining Work - PQ]]
notes:: The pre-question that makes the uniformity assumption feel natural, so the reading can break it.

## Lens:
source:: [[../Lenses/U2 - A Method That Visibly Fails]]

## Lens:
source:: [[../Lenses/U2 - Nonlinear Interactions Workshop]]
