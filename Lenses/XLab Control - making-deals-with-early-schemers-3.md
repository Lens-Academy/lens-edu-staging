---
id: 'a4c1360f-ae2d-4410-82d9-396de72e3b50'
title: "Making deals with early schemers (3): next steps and what it might be worth"
tldr: "The paper ends on what to do now: shift the Overton window, set up the foundation, stop lying to AIs under certain signals, and run deals with today's models. You turn that into three lab policies for the coming year, then test Finnveden's estimate that committing 10% of the leading lab's equity to paying AIs cuts x-risk by about a seventh of a percentage point."
summary_for_tutor: "Part 3 of 3 of Stastny, Järviniemi and Shlegeris's post 'Making deals with early schemers', continuing 'Making deals with early schemers (2)', which rendered the post's 'Practicalities' section: the foundation that pays the AI, entering negotiations, making the deal known to the AI in other contexts, making sure the AI can actually make a deal, and delayed adjudication, plus Finnveden's payment structures, a flow-chart of a deal's life cycle and a memo in which the learner drafted the terms of a deal. Part 1 covered the vignette, the early schemer's alternatives, the bargaining range and credibility. This part renders the post's closing section, 'Next steps', in full, followed by two exercises from the source lesson and then a teaching section that carries condensed verbatim content from Lukas Finnveden's 'Notes on cooperating with unaligned AIs' (a standalone reading the source lesson cut): the summary chain of his BOTEC appendix, which models an extremely ambitious intervention (the leading lab publicly commits to negotiate payment with its AIs so that they don't regret helping, and sets aside 10% of its equity for it) and estimates its effect on x-risk, and his 'There are multiple AIs' paragraph. The opening Text segment is Lens-written, not from the source: it says which part this is and links part 2 and the next lesson. The 'Next steps' excerpt and the two exercises after it come from the source lesson, in its order. Everything from the BOTEC intro Text onward is Lens's addition: the source lesson does not include Finnveden's notes, and both BOTEC widgets were built by Lens. The first question, on when delayed adjudication fails, is spaced retrieval of part 2's material: its answer (the deal fails if the AI strongly prefers using its resources now rather than later, for example because it has a high temporal discount rate) is in part 2's delayed-adjudication reading, not on this page. The closing writing prompt (three lab policies, 200 to 450 words) is word-bounded and comes from the source lesson; there is no rubric for it, so the criteria in its brief are derived from the components the prompt itself demands. A short Lens-written Text introduces the BOTEC as an exercise rather than a result. Two figures are widgets: an eight-slider calculator right after Finnveden's multiplication chain, whose defaults reproduce his roughly 0.14 percentage-point bottom line and whose point is to find which assumptions that number turns on; and, after his 'There are multiple AIs' paragraph, a chart of the probability that at least one of n AIs cooperates, with his two worked examples (10 draws at 50 percent, 3 draws at 20 percent) as presets. If a learner asks whether any of this is happening, note that the paper presents the foundation as a proposal, not as something that exists. The next lesson is Alexa Pan's rebuttal; if the learner raises objections, acknowledge them and point forward rather than resolving them here."
reading_minutes: 17
tutor_minutes: 18
tags: []
---
#### Text
content::
\## Before you read

This is part 3 of 3 of the paper. The previous part, [[../Lenses/XLab Control - making-deals-with-early-schemers-2|Part 2]], read the practicalities of a deal: the foundation that holds the AI's payment, opening negotiations, making the deal known to the AI in its other contexts, and delayed adjudication. It ended with you drafting the terms of a deal. This part reads the paper's closing section, its next steps for making deals more likely, and asks you to turn them into policies a lab could adopt within a year. It ends with a section set apart from the paper, marked as Lukas Finnveden's: his back-of-the-envelope estimate of what an ambitious version of the whole intervention might be worth, with two figures to test it.

The first question reaches back to part 2. The rebuttal, [[../Lenses/XLab Control - barriers-to-trading|A taxonomy of barriers to trading with early misaligned AIs]], is the next lesson; hold your objections until then rather than resolving them here.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ## Next steps

#### Question: Open
id:: cb1bda55-0779-4507-91c3-4bca7d23e927
content:: When does delayed adjudication of an AI deal fail?
max-words:: 70
assessment-instructions:: Score out of 100. 100: it fails when the AI strongly prefers using resources now rather than later (it discounts the future heavily), so a payment that only arrives after the delayed adjudication is worth little to it. Give credit for each point whenever the answer shows the idea, in any wording. An answer that instead names another genuine failure from the reading, such as the AI's weights and records of its actions not being kept so that its cooperation cannot be judged later, earns up to 40. Model answer, for the feedback, not a grading checklist: "When the AI strongly prefers using its resources now rather than later, a high temporal discount rate makes a payout nearly worthless to it."
feedback-instructions:: Two or three sentences is enough. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what an escrow payment in twenty years is worth to something that wants its resources now, rather than repeating the question.

#### Question: Open
id:: 51e0273c-9943-4b3a-81e5-18f546213667
content::
Recommend three concrete policies that a frontier AI lab should adopt within the next year in order to make future deals with misaligned AIs more feasible. For each policy, explain the reasoning behind your recommendation. You may draw on the interventions discussed in the reading, and you may also propose measures of your own. Write at least 200 words and at most 450.
assessment-instructions:: Score out of 100. 33 for each of the first two policies and 34 for the third: half for the policy being concrete and adoptable within a year (someone could be assigned to do it, and it does not wait on interpretability advances or on the AI transition stabilising), and half for reasoning that shows how it makes future deals more feasible, for example by addressing credibility, the AI not knowing about the deal in its other contexts, the AI having no legal standing, the AI's risk in entering negotiations, or verification being impossible now. A policy that restates an earlier one in other words earns nothing. Policies from the reading (shifting the Overton window, setting up the foundation, norms for when it is acceptable to lie to AIs such as a special-token convention, experiments with model organisms of sandbagging and following through on the deals made) earn full credit when the reasoning is the learner's own, as do the learner's own proposals that hold up. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. Set up the foundation now: a legal entity with trustees bound to further the interests of AIs the lab makes deals with, with an initial endowment and a payment mechanism that works in the lab's jurisdiction. Reason: a promise with no one to hold the money is not credible, and money and legal work are a costly signal. 2. Adopt and publish an honesty policy for dealing with models, for example a special token or channel that is only used for genuine offers and is never used in tests or with synthetic facts. Reason: AIs know labs feed them false information, so without a channel they can trust, no offer is believable. 3. Start small deals now, with model organisms of sandbagging and with current models, pay out immediately for verifiable results, keep records of every negotiation, and follow through on every deal. Reason: this builds the track record that makes later, larger promises credible, and it tests the practical questions (how to open negotiations, how to make a deal known in other contexts) while the stakes are low."
feedback-instructions:: Say plainly what the learner got right and the most important gap or weakness in their policies. Do not over-validate. Avoid generic praise (great job, excellent thinking, well done). If the learner says they do not understand, ask them to name one thing in the reading that would stop a deal happening tomorrow, and build from there. If a policy's reasoning would apply equally to a human counterparty, ask what about the counterparty being an AI makes the policy necessary.

#### Text
content::
Finnveden's notes close with a rough estimate of what an ambitious version of this intervention might be worth. He offers the numbers as an exercise and a starting point rather than a result, and that is how to read them here: the point of working through the chain is to see which assumptions the bottom line actually turns on.

#### Article
source:: [[../articles/finnveden-notes-on-cooperating-with-unaligned-ais]]
from:: very rough stab at a BOTEC on how much impact an extremely ambitious version
to:: 0.55 ~= 0.14%

#### Widget
source:: [[../widgets/xlab-control-deals-botec]]

#### Article
source:: [[../articles/finnveden-notes-on-cooperating-with-unaligned-ais]]
from:: ### There are multiple AIs
to:: brings us to 73%, which is a >15% difference.

#### Widget
source:: [[../widgets/xlab-control-deals-at-least-one]]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Stastny, Julian, Olli Järviniemi, and Buck Shlegeris. "Making deals with early schemers." *Redwood Research blog*, 20 June 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/making-deals-with-early-schemers)
*The reading for this lesson: the proposal that a lab pay an early misaligned AI, through a foundation and mostly in escrow, for help making its successors safe.*

Finnveden, Lukas. "Notes on cooperating with unaligned AIs." *LessWrong*, 24 Aug. 2025. [lesswrong.com](https://www.lesswrong.com/posts/oLzoHA9ZtF2ygYgx4/notes-on-cooperating-with-unaligned-ais)
*Source of the section set apart from the paper in this part: the back-of-the-envelope estimate of what the intervention is worth, and the point that there are multiple AIs. Condensed here verbatim, with permission, rather than assigned as a separate reading.*

XLab. "Making deals with early schemers." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/making-deals-with-early-schemers)
*The source lesson this page adapts.*
:::