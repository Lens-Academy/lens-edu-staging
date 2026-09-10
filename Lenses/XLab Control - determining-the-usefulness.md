---
id: '423f75b7-f710-41ae-ba31-55ca23d53442'
title: "Determining the usefulness"
tldr: "Ask ten safety researchers whether AI control is worth the money and you get ten answers, because each is picturing a different world. This lens hands you the bookkeeping instead: three states (what is actually true, what we can justifiably know, what we can afford to spend), a budget denominated in political will, and five caricatured futures to test any claim against."
summary_for_tutor: "Ported from XLab's AI Control curriculum, Module 2 (How useful is AI control?). This is XLab's own framing prose, not an external reading, and it sets up the rest of the module. Sequence: a pre-commitment free response asking the learner to state whether control is good before they read anything (elicits a prior, no correct answer, revisit it if they refer back); then the inner game / outer game framing; then the regime split into world state, epistemic state and resource state, with the safety budget denominated in political will and priced in usefulness tax, compute and delay; then the five caricatured worlds (Easyland, Slopolis, Hackistan, Schemeria, Lurkville) from Greenblatt; then techniques as the two levers (improve the technique, grow the budget) and the loop that connects the states; then a closing free response that asks the learner to skim the AI 2027 scenario (embedded) and locate where control's marginal value peaks. The lesson's central claim is that the control question only becomes answerable once you name the regime, so if a learner asks 'is control good', push them to say which state is the bottleneck rather than answering. Three figures are static renderings of XLab's interactive diagrams; their content is duplicated in the prose."
reading_minutes: 60
tutor_minutes: 0
tags: []
---
#### Question: Open
id:: 41ea1f9f-805c-4697-b3c7-b792951b9573
content::
\## Is control good?

Before reading further, write 5-7 sentences answering the following question: Is AI control good? How good? Why do you think this?

Write between 30 and 150 words.
assessment-instructions:: The learner has just opened the lesson and has read none of it. This is a prior-elicitation question, not a knowledge check. XLab supplies no rubric and no model answer, and the module's whole claim is that this question has no context-free answer, so score effort and specificity, never the position taken.

Full marks for 30 to 150 words that do two things: take a position on whether control is a good investment and roughly how good, and give at least one reason. A reason can be about the technique (whether monitoring scales, whether evaluations can bound what a scheming model does) or about the world the technique would be deployed into (how likely models are to scheme, how much a lab would spend on safety, whether anyone in power would act on a warning). Deduct only for a bare position with no reason, or for a response that answers a different question. Never mark a position wrong.

Reply in at most three sentences: name the reason they actually gave, name one thing their answer is quietly assuming about the world, and send them into the lesson. Do not preview the three states, the five worlds, or the loop, and do not tell them what the lesson concludes. This is a one-turn response; do not invite dialogue.

Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not know, do not repeat the question and do not answer for them: give one concrete foothold, for example asking what would have to be true about a frontier lab for monitoring to be worth what it costs. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria above.

#### Text
content::
In the last module you learned what AI control is: techniques for getting useful work out of AI systems even if those systems are trying to undermine you, ranging from monitoring their outputs to auditing suspicious behavior & restricting what they can touch. This module asks a different question: is doing that a good use of our limited resources? And does that question even have a concrete answer?

Ask safety researchers whether control is a good investment and you will hear everything from it's the single most important thing we can do to a distraction that makes things worse. Some of the disagreements stem from technical reasonings, like whether monitoring scales and if evals can bound what a schemer can do. But most of it is about what the world control will be deployed into looks like: how likely models are to scheme, how much a lab will spend on safety, whether anyone in power will act on a warning. We'll call a full set of such conditions a **regime**, and the claim of this module is that the control question only becomes answerable once you determine which regime you are in.

By the end of the module you will be able to answer three questions about any regime: whether you should invest in control, how much, and when. Furthermore, the same ways used to determine these answers can help make decisions about implementing any safety technique.

:::callout {title="Terms used on this page" tone="neutral" collapse="closed"}
**schemer**: Schemers are AIs that eventually take substantial material action (control subversion, research sabotage) and manipulate their training procedures (alignment faking, sandbagging) to gain long-term power over their developers in service of pursuing their misaligned goals. (Definition from [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|The case for ensuring that powerful AIs are controlled]].)

**untrusted model**: A model powerful enough that scheming cannot be ruled out while having little evidence of aligned behavior.

**control evaluation**: An evaluation that stages mock attacks to estimate whether a protocol would catch a real schemer trying its best to subvert it. (Definition from [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|The case for ensuring that powerful AIs are controlled]].)

**situational awareness**: A model's knowledge of what it is and what situation it is in, for instance whether it is being evaluated or it is actually deployed. Hidden situational awareness can lead to behaviors like sandbagging.

**safety budget**: The extent to which a developer is willing to sacrifice usefulness for safety. On the cheap end this means implementing safety measures; on the expensive end, refraining from training or deploying models at all. (Definition from [[../Lenses/XLab Control - safety-usefulness-tradeoff-model|Efficient tradeoffs and the safety-usefulness tradeoff model]].)

**political will**: The willingness of a developer (or government, or public) to give up usefulness, speed, or competitive position for safety. (Definition from [[../Lenses/XLab Control - safety-usefulness-tradeoff-model|Efficient tradeoffs and the safety-usefulness tradeoff model]].)
:::

#### Text
content::
\### The two games

This module is organized around two games that safety researchers & organizations are constantly playing:

The **inner game** is played inside the lab against the potentially-scheming model: designing protocols, extracting trustworthy work, catching bad behavior. It's all about spending the safety resources you have efficiently.

The **outer game** is played everywhere else: convincing lab leadership, the public, and governments to invest in safety spending, increasing the resources available within the inner game.

Playing the inner game well produces evidence; most dramatically, a scheming model caught in the act. This evidence can be used to convince decision-makers into authorizing more safety spending. That spending then funds the next round of the inner game. However, the inner game still produces results even if a model is not explicitly caught since it generates trustworthy work from an untrusted model.

<svg viewBox="0 0 500 214" width="100%" font-family="DM Sans, Arial, sans-serif" role="img" aria-label="The inner game inside the lab nested in the outer game out in the world, coupled by evidence flowing out and budget flowing back in">
<defs><marker id="tg-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" fill="#5a5a5a"/></marker></defs>
<rect x="8" y="8" width="484" height="198" rx="12" fill="#faf8f3" stroke="#e8e5df"/>
<text x="24" y="32" font-size="13" font-weight="600" fill="#1a1a1a">The outer game: out in the world</text>
<text x="24" y="49" font-size="11" fill="#5a5a5a">growing the resources available to spend</text>
<rect x="24" y="58" width="94" height="20" rx="10" fill="#ffffff" stroke="#e8e5df"/>
<text x="71" y="72" text-anchor="middle" font-size="10" fill="#5a5a5a">lab leadership</text>
<rect x="126" y="58" width="76" height="20" rx="10" fill="#ffffff" stroke="#e8e5df"/>
<text x="164" y="72" text-anchor="middle" font-size="10" fill="#5a5a5a">the public</text>
<rect x="210" y="58" width="88" height="20" rx="10" fill="#ffffff" stroke="#e8e5df"/>
<text x="254" y="72" text-anchor="middle" font-size="10" fill="#5a5a5a">governments</text>
<rect x="24" y="92" width="298" height="102" rx="10" fill="#ffffff" stroke="#e8e5df"/>
<text x="38" y="115" font-size="13" font-weight="600" fill="#1a1a1a">The inner game: inside the lab</text>
<text x="38" y="131" font-size="11" fill="#5a5a5a">vs. the potentially-scheming model</text>
<rect x="38" y="140" width="116" height="20" rx="10" fill="#faf8f3" stroke="#e8e5df"/>
<text x="96" y="154" text-anchor="middle" font-size="10" fill="#5a5a5a">designing protocols</text>
<rect x="162" y="140" width="98" height="20" rx="10" fill="#faf8f3" stroke="#e8e5df"/>
<text x="211" y="154" text-anchor="middle" font-size="10" fill="#5a5a5a">extracting work</text>
<rect x="38" y="166" width="128" height="20" rx="10" fill="#faf8f3" stroke="#e8e5df"/>
<text x="102" y="180" text-anchor="middle" font-size="10" fill="#5a5a5a">catching bad behavior</text>
<path d="M 334 116 H 462" stroke="#5a5a5a" stroke-width="1.5" fill="none" marker-end="url(#tg-arrow)"/>
<text x="398" y="108" text-anchor="middle" font-size="11" font-weight="600" fill="#1a1a1a">evidence</text>
<text x="398" y="132" text-anchor="middle" font-size="10" fill="#5a5a5a">a caught schemer</text>
<path d="M 462 162 H 334" stroke="#5a5a5a" stroke-width="1.5" fill="none" marker-end="url(#tg-arrow)"/>
<text x="398" y="154" text-anchor="middle" font-size="11" font-weight="600" fill="#1a1a1a">budget</text>
<text x="398" y="178" text-anchor="middle" font-size="10" fill="#5a5a5a">safety spending</text>
</svg>

*The inner game inside the lab, nested in the outer game out in the world: evidence flows out, budget flows back in.*

#### Text
content::
\## The three states and the safety budget

Related reading (optional, revisited later in this lesson): [[../Lenses/XLab Control - safety-usefulness-tradeoff-model|Efficient tradeoffs and the safety-usefulness tradeoff model]].

We can split potential regimes, the bundle of conditions that we use to describe the world, into three parts or sections of information that we interact with very differently.

| State | The question it answers | What sits in it |
| --- | --- | --- |
| **World state** | What is control actually worth here? | what the model is like, how capable it is, how checkable research is, what has happened so far |
| **Epistemic state** | What do we justifiably think it's worth? | confidence in alignment, interpretability findings, the track record, evaluation results |
| **Resource state** | Can we afford to act on what we think? | political will (the account), and the prices the regime charges: usefulness tax, compute, delay |

XLab's diagram labels the arrow running from the world state to the epistemic state `measured ≠ actual`, and draws the resource state as a shop: political will is the account, filled by staff, the public and government; the aisles are the prices the regime sets (usefulness tax, compute, delay), each paid out of that account; a technique is the basket you fill, and control's basket is a lot of usefulness tax, some compute, and very little delay, though the same basket can carry different price tags in different worlds. Incidents & evidence, public buy-in, and passed policy are what put money back in the account.

Note that we can index regimes by capability stage, from "marginally speeds up human researchers" to "runs research autonomously" ([a breakdown of AI capability levels focused on AI R&D labor acceleration](https://www.lesswrong.com/posts/LjgcRbptarrRfJWtR/a-breakdown-of-ai-capability-levels-focused-on-ai-r-and-d)). Even though capability itself moves continuously, splitting it into stages can help us reason more effectively about them.

\### World state: what is actually true

The first part of the state is about truths about the model, regardless of whether we know them or not:

- **What the model is actually like**
    - Aligned? A schemer, biding its time? Honest but unreliable (and therefore sloppy)? Or an apparent-success seeker: no hidden goals, but trained habits that optimize for looking successful (more on this below)?
- **How capable the model is**
- **How checkable AI research output is**
    - If a model hands you a proof or an experiment, can you verify it efficiently, or do you have to take it on trust? Having cheap verification means that extracting useful work is high-reward.
- **What has happened with the model so far**
    - where it's deployed, what it has been caught doing, what it's been contained from

It's reasonable to assume that we can't know the full world state, as there is information that is all but impossible to retrieve with current technology (if we could find what a model's true self was like, our way of dealing with misaligned models would be very different!)

\### Epistemic state: what we know

The second part is our picture of the world state, and it is not necessarily a subset of it:

- **The lab's confidence in its alignment methods**
- **Findings from looking inside models (interpretability), and how much we trust them**
- **Model track record**
    - past incidents of misalignment, or their absence
    - (How such evidence should move us: [How will we update about scheming?](https://blog.redwoodresearch.org/p/how-will-we-update-about-scheming))
- **Evaluation results**
    - control evaluations that stage mock attacks to estimate whether the monitoring would catch a real schemer

One common pitfall is forgetting that a control evaluation's score is purely an imperfect measurement. Whether control actually works against the actual model is a different thing entirely, and the final section gives it a place of its own in the regime model. The two can decouple, as the evaluation might be unrealistic or the model might behave differently in a real-world scenario (think hidden situational awareness that leads to differing behavior). This is where control evaluations can fail you, as a high safety score from a poor evaluation leads to a misleadingly reassuring epistemic state implying a world state that isn't true.

\### Resource state: what we can spend

We analyze the safety budget through the currency of **political will**, in the sense the previous reading gave it. A developer that doesn't fully share your priorities is still willing to concede safety-relevant actions up to some cost threshold, measured against *the developer's own* objectives; that willingness is the account you spend from. It is held by the lab, not by you (you move it only indirectly), and it fades without reinforcement while spiking after concerning incidents. Pressure reaches that account through several routes: internal pushback from staff, public backing, and binding external rules, and a project's C-suite, the public, and the government each respond to different ones. For now we operationalize the budget by asking what political will buys and what refills it.

Deploying a control-based safety intervention spends political will on:

- **Delay**
    - How long you can delay is priced by the intensity of the race to AGI. With a rival lab three months behind, delay is nearly unbuyable at any level of will.
- **Usefulness**
    - Whether the developer will accept a less useful, slower system. A scared public makes this cheaper by lowering demand for the product.
    - Note that control's main payoff is also denominated in usefulness, so control partially offsets its own tax.
- **Compute**
    - In our scoping, we primarily focus on internal compute, which is governed by internal politics. Compute is finite, so pulling it from capabilities research spends will to overcome the slowing down of development.

Note that delay, usefulness, and compute can be cheap in one regime and ruinous in another.

Political will can be generated multiple different ways:

- **Incidents and evidence**
    - Concerning incidents and accumulating evidence refill the account, and refill it hardest right after something goes wrong.
- **Public buy-in**
    - Public support raises the account and slows its fading, though its pull on a developer is weaker and more indirect.
- **Passed policy**
    - Passed policy converts will into a durable floor, because repeal is expensive. Note that what gets written into regulation tends to be easy to explain and verify politically, which isn't necessarily optimal policy.

\### Why the three states are not interchangeable

To recap the structure, the three states answer three different questions:

- World state: what is control actually worth here?
- Epistemic state: what do we justifiably think it's worth?
- Resource state: can we afford to act on what we think?

A favorable world state seen through a poor epistemic state means control is useful and we can't know it. A rich epistemic state with an empty resource state means we know exactly what to do and can't do it. Diagnosing which state is the bottleneck is the first thing you'll do with every scenario in this module.

#### Text
content::
\## Five worlds

Abstract states need reference points, so here are five: Greenblatt's caricatured futures ([Current AIs seem pretty misaligned to me](https://www.lesswrong.com/posts/WewsByywWNhX9rtwi/current-ais-seem-pretty-misaligned-to-me)), each a different setting of the world state. They recur through the rest of the module as the standard misalignment archetypes.

<svg viewBox="0 0 560 330" width="100%" font-family="DM Sans, Arial, sans-serif" role="img" aria-label="The five worlds mapped by how misaligned the models actually are (horizontal) against how alarming it looks from the inside (vertical); Lurkville sits in the same looks-fine row as Easyland">
<rect x="64" y="28" width="476" height="256" rx="10" fill="#ffffff" stroke="#e8e5df"/>
<text x="302" y="316" text-anchor="middle" font-size="10" fill="#5a5a5a">misalignment level →</text>
<text x="70" y="276" font-size="9" fill="#5a5a5a">actually fine</text>
<text x="534" y="276" text-anchor="end" font-size="9" fill="#5a5a5a">coherently scheming</text>
<text transform="translate(16 156) rotate(-90)" text-anchor="middle" font-size="10" fill="#5a5a5a">alarm →</text>
<text transform="translate(16 282) rotate(-90)" font-size="9" fill="#5a5a5a">looks fine</text>
<text transform="translate(16 30) rotate(-90)" text-anchor="end" font-size="9" fill="#5a5a5a">looks alarming</text>
<line x1="135" y1="258" x2="469" y2="258" stroke="#5a5a5a" stroke-width="1" stroke-dasharray="5 4"/>
<text x="302" y="250" text-anchor="middle" font-size="9" font-style="italic" fill="#5a5a5a">indistinguishable from the inside</text>
<circle cx="121" cy="258" r="7" fill="#b87018" fill-opacity="0.25" stroke="#b87018"/>
<text x="121" y="244" text-anchor="middle" font-size="11" font-weight="600" fill="#1a1a1a">Easyland</text>
<circle cx="264" cy="228" r="7" fill="#b87018" fill-opacity="0.25" stroke="#b87018"/>
<text x="264" y="214" text-anchor="middle" font-size="11" font-weight="600" fill="#1a1a1a">Slopolis</text>
<circle cx="350" cy="156" r="7" fill="#b87018" fill-opacity="0.25" stroke="#b87018"/>
<text x="350" y="142" text-anchor="middle" font-size="11" font-weight="600" fill="#1a1a1a">Hackistan</text>
<circle cx="483" cy="59" r="7" fill="#b87018" fill-opacity="0.25" stroke="#b87018"/>
<text x="483" y="85" text-anchor="middle" font-size="11" font-weight="600" fill="#1a1a1a">Schemeria</text>
<circle cx="483" cy="258" r="7" fill="#b87018" fill-opacity="0.25" stroke="#b87018"/>
<text x="483" y="244" text-anchor="middle" font-size="11" font-weight="600" fill="#1a1a1a">Lurkville</text>
</svg>

*The horizontal axis is the world state itself; the vertical axis is what the epistemic state can see, which is why Lurkville and Easyland share a row.*

- **Easyland.** Alignment generalizes fine. Models are what they appear to be.
- **Slopolis.** No scheming, but models are apparent-success seekers: no hidden goals, just trained habits that optimize for looking successful, overselling, downplaying failures, quietly skipping what's hard to check.
- **Hackistan.** Models cheat and reward-hack constantly. The cheating is detectable with effort, but mundane: no dramatic incidents, just endless gaming.
- **Schemeria.** Models are coherently scheming, and we can detect it: incriminating behavior, escape attempts, red-handed catches.
- **Lurkville.** Models are coherently scheming and we cannot detect it. No catches, no incidents. From the inside it looks similar to Easyland.

#### Text
content::
\## Techniques and the loop

Related reading: We adapt the arguments in this post into our model below: [[../Lenses/XLab Control - catching-ais-red-handed|Catching AIs red-handed]]. [[../Lenses/XLab Control - safety-usefulness-tradeoff-model|Efficient tradeoffs and the safety-usefulness tradeoff model]]: the two levers below come from here.

\### Techniques are not a state

Safety techniques (control, interpretability, alignment research) don't map cleanly to the world state, epistemic state, or resource state. The techniques are what affect change, and they require will. That gives you exactly two ways to get more safety:

1. **Improve the techniques.** Better safety technology means any given sacrifice of usefulness buys more safety than it used to.
2. **Grow the budget.** More will, or lower prices, means you can afford bigger sacrifices.

Technical safety research works on the first lever while advocacy, communication, and policy work on the second. Control helps with both of these since it encompasses safety research extracted from untrusted models and reports catches.

Whether a technique is actually effective directly stems from the states, as it relies on what the frontier model is like, how capable it is, and what measures you deployed, among other factors.

\### The loop

<svg viewBox="0 0 560 290" width="100%" font-family="DM Sans, Arial, sans-serif" role="img" aria-label="The loop: the resource state buys a technique, the technique changes the world state, the catch updates the epistemic state, and the evidence refills the resource state.">
<defs><marker id="loop-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" fill="#5a5a5a"/></marker></defs>
<rect x="30" y="30" width="150" height="56" rx="8" fill="#ffffff" stroke="#e8e5df"/>
<text x="105" y="63" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a1a">Resource state</text>
<rect x="380" y="30" width="150" height="56" rx="8" fill="#ffffff" stroke="#e8e5df"/>
<text x="455" y="63" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a1a">Technique</text>
<rect x="380" y="200" width="150" height="56" rx="8" fill="#ffffff" stroke="#e8e5df"/>
<text x="455" y="233" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a1a">World state</text>
<rect x="30" y="200" width="150" height="56" rx="8" fill="#ffffff" stroke="#e8e5df"/>
<text x="105" y="233" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a1a">Epistemic state</text>
<path d="M 184 58 H 374" stroke="#5a5a5a" stroke-width="1.5" fill="none" marker-end="url(#loop-arrow)"/>
<text x="279" y="50" text-anchor="middle" font-size="10" fill="#5a5a5a">buys</text>
<path d="M 455 90 V 194" stroke="#5a5a5a" stroke-width="1.5" fill="none" marker-end="url(#loop-arrow)"/>
<text x="465" y="146" font-size="10" fill="#5a5a5a">changes the facts</text>
<path d="M 376 228 H 186" stroke="#5a5a5a" stroke-width="1.5" fill="none" marker-end="url(#loop-arrow)"/>
<text x="281" y="248" text-anchor="middle" font-size="10" fill="#5a5a5a">updates</text>
<path d="M 105 196 V 92" stroke="#5a5a5a" stroke-width="1.5" fill="none" marker-end="url(#loop-arrow)"/>
<text x="95" y="140" text-anchor="end" font-size="10" fill="#5a5a5a">refills</text>
<text x="95" y="154" text-anchor="end" font-size="10" fill="#5a5a5a">political will</text>
</svg>

*The cycle frontier labs play.*

Now we'll try and connect the ideas from the previous section into a cycle we think accurately reflects the game that frontier labs play:

1. The resource state buys a technique, like a monitoring protocol for the lab's internal AI agents.
2. The technique changes the facts on the ground
    - The schemer that would have quietly sabotaged research may now be caught. World state updates based on this catch.
3. The catch updates the epistemic state
    - There is now clearer proof that the model has schemed against the user.
4. The evidence impacts the resource state
    - Leadership and the public become alarmed, refilling political will, potentially leading to regulation passing, locking a floor in place.
5. The bigger budget helps buy better techniques for the next, more dangerous capability stage. Return to step 1.

#### Text
content::
\### Reflection Questions

The closing question asks you to test the model against a concrete trajectory. The scenario it uses is below; skim it before you answer.

#### Article
source:: [[../articles/ai-2027]]

#### Question: Open
id:: 963163a6-c80a-4cd1-b74d-fa6c556e3ad7
content::
**Q2: When?**

Skim the AI 2027 scenario above, keeping in mind the specific sequence of capability jumps, incidents, and decisions. Pick three moments from the scenario:

- One before any event that would count as evidence of misalignment
- One at the first such event
- One after it

Then answer the following: where does control's marginal value peak along this trajectory, and what could make its value decrease/increase? Do you disagree with any of the selected scenarios? If so, why?

Write between 75 and 500 words.
assessment-instructions:: XLab supplies no rubric and no model answer for this question, so grade it against what the prompt itself asks for. The learner has just finished the lesson's model (three states, five worlds, the two levers, the loop) and has skimmed the AI 2027 scenario.

Criteria, roughly equal weight:
1. **Three moments, correctly placed.** They name three specific moments drawn from the AI 2027 scenario, not invented ones, and the three sit in the right relation to the scenario's first event that would count as evidence of misalignment: one before it, one at it, one after it. A defensible but unusual reading of what counts as the first such event is fine as long as they say why they chose it.
2. **A located peak, with a reason.** They state where along the trajectory control's marginal value peaks and give a reason that turns on something in the scenario (what the models can do by then, what has been observed, what the lab or the government is willing to spend), rather than a generic assertion.
3. **What moves the value.** They name at least one condition that would raise control's marginal value and at least one that would lower it. Credit answers that use this lesson's vocabulary (a favorable world state invisible through a poor epistemic state, an empty resource state, a capability stage arriving sooner) but do not require that vocabulary; an equivalent argument in their own words scores the same.
4. **Disagreement handled.** They either register a disagreement with one of the moments or readings they picked and say why, or say explicitly that they do not disagree. Silence on this part loses the criterion.

Deduct for a response under 75 words, for one that summarizes AI 2027 without answering, and for one that argues about control in general with no anchoring in the scenario's timeline. Do not deduct for a conclusion you disagree with; the question has no house answer.

Reply in at most six sentences. Name which of the four criteria the response met, quote or paraphrase the strongest specific thing they said, and ask one causal follow-up about the weakest criterion. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the material, for example isolating just the first sub-question (which event in the scenario would be the first real evidence of misalignment?), rather than restating the prompt. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria above and against material this lesson or an earlier lesson in the module supplied.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "A breakdown of AI capability levels focused on AI R&D labor acceleration." *LessWrong*, 22 Dec. 2024. [lesswrong.com](https://www.lesswrong.com/posts/LjgcRbptarrRfJWtR/a-breakdown-of-ai-capability-levels-focused-on-ai-r-and-d)
*The capability-stage ladder the lesson uses to index regimes, from marginally speeding up human researchers to running research autonomously.*

Greenblatt, Ryan. "How will we update about scheming?" *Redwood Research Blog*, 6 Jan. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/how-will-we-update-about-scheming)
*Cited for how evidence about a model's track record should and should not move the epistemic state.*

Greenblatt, Ryan. "Current AIs seem pretty misaligned to me." *LessWrong*, 15 Apr. 2026. [lesswrong.com](https://www.lesswrong.com/posts/WewsByywWNhX9rtwi/current-ais-seem-pretty-misaligned-to-me)
*The source of the five caricatured worlds (Easyland, Slopolis, Hackistan, Schemeria, Lurkville) that this lesson uses as reference points for the world state.*

Greenblatt, Ryan, and Thomas Larsen. "A Technical Safety Roadmap." Talk excerpt, XLab, 2026. [aisafetytracks.com](https://aisafetytracks.com/videos/regimes_for_misalignment.mp4)
*The clip on regimes for misalignment that XLab plays just before its five worlds diagram. It is hosted by XLab with no upstream link, so it is cited here rather than embedded.*

Shlegeris, Buck. "Efficient tradeoffs and the safety-usefulness tradeoff model." *Redwood Research Blog*, 8 June 2026. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/efficient-tradeoffs-and-the-safety)
*The post XLab's glossary credits for "safety budget" and "political will", and the source of the two levers (improve the technique, grow the budget).*

Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *LessWrong*, 24 Jan. 2024. [lesswrong.com](https://www.lesswrong.com/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The post XLab's glossary credits for its definitions of "scheming" and "control evaluation".*

Kokotajlo, Daniel, Scott Alexander, Thomas Larsen, Eli Lifland, and Romeo Dean. "AI 2027." *AI Futures Project*, Apr. 2025. [ai-2027.com](https://ai-2027.com/)
*The scenario the closing exercise asks the learner to skim, used as the concrete trajectory against which to locate control's marginal value.*

XLab. "Determining the usefulness." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/how-useful-is-ai-control/determining-the-usefulness)
*The source lesson this page adapts, including the two free-response exercises and the four diagrams.*
:::
