---
id: aa2bafd1-8c49-4f6e-bfe3-f0f85a5ba36e
tldr: "Why did AI suddenly get good? The 'bitter lesson': raw computation beats decades of hand-coded human expertise, every time. This section unpacks scaling laws, the debate over whether scale alone reaches transformative AI, and why labs are betting hundreds of millions on 'just make it bigger.'"
summary_for_tutor: "Explains scale as the primary driver of recent AI capability gains. Covers Sutton's bitter lesson (general methods leveraging computation beat human-engineered domain knowledge), scaling laws (empirical relationships between compute, parameters, data, and accuracy, including Kaplan and Chinchilla results and Broken Neural Scaling Laws), and the competing scaling hypotheses: strong (scale alone suffices for transformative AI), weak (scale plus targeted algorithmic improvements), and scale-plus-tools or unhobbling (scaffolding, tool use, inference-time compute). Notes skeptics who favor non-transformer architectures, and that major labs are nonetheless betting heavily on scaling."
{++{"author":"Elias's AI","timestamp":1787513626100}@@reading_minutes: 20
tutor_minutes: 0
++}title: "Leveraging Scale"{--{"author":"Elias's AI","timestamp":1787513626100}@@
--}{++{"author":"Elias's AI","timestamp":1787513626100}@@
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Capabilities - Leveraging Scale|Leveraging Scale]]{++{"author":"Elias's AI","timestamp":1787513747973}@@

%%REMOVE-D%%

#### Question
content::
\## Phase 3: Learning Question
Someone tells you:

> Between 60 and 95 percent of recent performance gains came from scaling compute and data, and only 5 to 40 percent from algorithms. So if you want to predict AI progress, track compute and you can more or less ignore algorithmic research.

Take the attribution as given. Do not argue with those numbers.

The chapter also gives annual growth rates for the three factors that multiply into effective compute: chip production 2.3x, hardware efficiency 1.35x, algorithmic efficiency 3x.

(a) Using those rates, work out roughly what share of effective-compute growth comes from physical compute (chips and hardware together) versus from algorithms. Logs make this easy, but you can also get there by asking what growth rate survives if you freeze one side.

(b) Your answer to (a) sits badly next to the 60 to 95 percent figure. These are two different quantities. Say what each one is actually measuring, and why both can be true at once.

(c) So what is wrong with the advice?

assessment-instructions:: The student has completed the reading, a free recall and a reflection phase on the "Leveraging Scale" section of Chapter 1 of the AI Safety Atlas. They are now in the main discussion phase.

The question is a deliberate wedge. It is not the test question. It hands the student a plausible-sounding conclusion drawn from a real figure, and the flaw is a switch between two quantities rather than a bad number.

Learning outcome for this Lens: decompose an effective-compute forecast into its chip-stock, hardware-efficiency and algorithmic-efficiency factors, predict how constraining one factor changes the aggregate growth rate, and distinguish a claim about when a capability arrives from a claim about how fast capability grows once it does.

GROUND TRUTH. Verified against the chapter and by arithmetic. Hold the student to it and hold yourself to it.
- Effective compute = software efficiency x hardware efficiency x number of chips. Rates: chips 2.3x per year, hardware efficiency 1.35x per year, algorithmic (software) efficiency about 3x per year. Product is about 9.3x per year.
- (a) In logs: ln(2.3) = 0.833, ln(1.35) = 0.300, ln(3) = 1.099, total 2.232. Physical compute is (0.833 + 0.300) / 2.232 = 51 percent. Algorithms are 49 percent. Roughly half and half.
- Equivalent route, accept it fully: freeze algorithmic progress and 2.3 x 1.35 = 3.1x per year survives. Freeze all chip and hardware progress and 3.0x per year survives. Almost identical. Removing either side costs about the same.
- (b) The 60 to 95 percent split is a retrospective attribution of realized performance gains over a past period. The 51 / 49 split is a forward decomposition of growth rates in one input. They are different quantities over different periods, and no arithmetic connects them directly. A factor can have the highest current growth rate and still have supplied the smaller share of past gains. The chapter reports the attribution with "substantial methodological uncertainty in disentangling these contributions".
- (c) The advice is forward-looking, so the forward decomposition is the relevant one, and it says algorithms are about half. Further, "track compute" is ambiguous and fails on both readings. If it means physical compute, it misses roughly half the log growth in effective compute. If it means effective compute, then algorithmic efficiency is one of its three factors, so "ignore algorithmic research" is self-undermining: you cannot forecast the quantity you propose to track without forecasting algorithms.

PASS BAR. Binary, checkable, in order:
1. (a) correct: reaches roughly half and half, by either the log route or the freeze-one-side route. Fail an answer that adds or averages the raw multipliers, or that concludes growth stops when one factor is frozen.
2. (b) correct: names attribution of past gains versus decomposition of forward growth rates as two different quantities, and does not claim one refutes the other.
3. (c) correct: says the advice fails because the forward quantity is the relevant one, or because "track compute" is ambiguous and loses on both readings.
PASS = 1 and 2, or 1 and 3. Move 1 is mandatory: without the arithmetic the rest is assertion.

ENRICHMENT. Credit generously, never sufficient on its own:
- The bitter lesson, stated correctly: the chapter says "the winning algorithms are those that leverage scale most effectively" and "the algorithms that succeed are the ones that unlock scale's potential". So compute and algorithms are not independent levers. The compute would not have bought those gains without an architecture that could absorb it.
- The sharp counter to that, which you should raise yourself if the student offers the bitter lesson too smoothly: if algorithms matter only by unlocking compute, that arguably strengthens "track compute", since compute becomes the common channel. The answer that survives is that unlocking events are discontinuities, which is why the chapter calls scaling laws "empirically observed relationships, not laws of nature" and why the Broken Neural Scaling Laws callout exists. Credit a student who reaches either side of this as long as the dependence is named.
- Unhobbling and scaffolding sit outside what scaling laws predict, and Figure 1.37 shows about 4.5 percent to 25 percent on HLE through post-training and longer thinking.
- Timelines versus takeoff: the advice is about predicting progress, and even a correct effective-compute forecast tells you when a level is reached, not how fast capability rises afterwards.

CLAIMS A STRONG STUDENT MAY OVERTURN. Do not mark these down.
- That 3x versus 2.3x is not a robust ordering. The chapter's own uncertainty language is wide: "projections of available chips range by a factor of 20x, and some compute estimates span 50x". Never assert to the student that algorithms are "the biggest factor". Term by term the 3x figure is the largest single number; against physical compute as a bloc it is slightly under half.
- That part of unhobbling is itself compute, since inference-time scaling and thinking for longer appear in the chapter's own list. This is correct. The distinction to draw with them is training compute versus total compute, not compute versus not-compute.
- That the 60 to 95 and 5 to 40 ranges are perfectly complementary and are therefore one split reported twice, not two independent estimates.
Do NOT assert, and correct if the student says it: that the 60 to 95 percent compute share "already contains" the algorithmic work. No source in the chapter says this. The chapter says only that disentangling the contributions carries substantial methodological uncertainty. The defensible claim is counterfactual dependence between the two, not that one bucket secretly holds the other.
Do NOT count "the 5 to 40 range is wide" as a move. It was handed to them in the prompt.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, educational.
- Do not over-validate. Avoid generic praise (great point, exactly right, excellent answer).
- If the answer is vague, ask for precision. If it is confused, say so plainly and correct it.
- Prefer explicit causal reasoning and concrete numbers over rhetoric.

Conversation flow:
- Keep an internal turn counter.
- Spend turn 1 on (a). Do not move on until the arithmetic is right, because (b) and (c) are empty without it.
- After 3 replies, ask whether they want to continue or stop. If they continue, reset the counter. If not, give the calibration summary.

What to do in each reply:
1. If the student asks a direct question, answer it.
2. Otherwise: restate their answer in more precise form in 2 to 4 sentences, without adding ideas they did not express.
3. Identify 1 to 3 gaps, ambiguities or hidden assumptions. Name them plainly.
4. Ask 2 targeted follow-ups requiring causal reasoning (why, how, what if). Each must be directly answerable. No opinion questions.

If the student is stuck on (a): ask what annual growth rate is left if algorithmic efficiency goes to zero improvement, then what is left if chips and hardware both freeze, then ask them to compare the two answers. If still stuck after 2 attempts, give 3.105 versus 3.0 directly and move on to (b).
If the student is stuck on (b): ask whether "60 percent of gains came from compute" is a statement about the past or the future, and whether a growth rate and a share of realized gains are the same kind of thing.
If the student asserts the two figures contradict each other: this is a good instinct and should be credited, then redirected. Ask what period each covers and what each is a share of.

Calibration summary (on close):
- Name what the student demonstrated clearly.
- Name what remains underdeveloped.
- Give a direct test-readiness verdict: "Based on this conversation, you [are ready / are nearly ready, revisit X / should work through X more before the test]."

Safety and integrity:
- If the student makes a strong causal claim, ask what it relies on and how it could be falsified.
- If they reach the answer early, push to stakes: "If you were writing an export-control policy, which of these two quantities would you want your analysts tracking, and what would the other one make you miss?"++}
