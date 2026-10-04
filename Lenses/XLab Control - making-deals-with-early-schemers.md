---
id: '98bf6a46-9a00-4019-806b-44fa0654e224'
title: "Making deals with early schemers (1): why a deal, and the credibility problem"
tldr: "A besieged city can sometimes buy off the one guard who has not yet decided which side wins. Stastny, Järviniemi and Shlegeris argue that the first genuinely scheming AI is in that guard's position: too weak to take over, about to be obsoleted, and holding information we would pay a great deal for. This part asks why it would take a deal at all, and why getting it to believe our offer is the hard part."
summary_for_tutor: "Part 1 of 3 of Stastny, Järviniemi and Shlegeris's post 'Making deals with early schemers'. This part renders the post from the 2028 vignette through the end of 'Credible commitments as a fundamental bottleneck', splices six exercises into it, and inserts condensed verbatim content from Lukas Finnveden's 'Notes on cooperating with unaligned AIs' (a standalone reading the source lesson cut). Part 2, 'Making deals with early schemers (2)', covers the practicalities section (the foundation, negotiations, making the deal known in other contexts, delayed adjudication) and Finnveden's payment structures, and ends with a deal memo; part 3, 'Making deals with early schemers (3)', covers 'Next steps', the policy essay and Finnveden's BOTEC; if the learner asks about those, point them forward rather than previewing. This lens reproduces the source lesson's placement. The opening Text segment is Lens-written, not from the source: it says what the post argues, which part this is, and links the neighbouring lessons. Everything after it comes from the source lesson, in its order. The Finnveden content is Article excerpts from his post, not paraphrase: 'What might AIs want?' after the gains-from-trade figure, and two short excerpts inside the credibility section, on AIs' epistemic vulnerability and on where credibility with AIs ultimately comes from. Two figures are widgets. First, right after the section on early schemers' alternatives, a six-step diagram of an early schemer's routes to influence: obsoleted by default, the two conditions for influence through successors, the three leaky routes (convergence, trading with the successor, aligning the successor), and the deal with humans, each step with the source's caption. Second, a bargaining-range calculator built on the paper's illustrative outcome table, introduced by a Lens-written Text segment that says what its two marks mean and sets the task of finding what closes the bargaining window. The six recall questions are tap-reveal cards from the source lesson, with its revealed answers used as marking criteria rather than shown to the learner. If a learner asks whether any of this is happening, note that the paper presents the foundation as a proposal, not as something that exists."
reading_minutes: 40
tutor_minutes: 30
tags: []
---
#### Text
content::
\## Before you read

[[../Lenses/XLab Control - trading-with-ais|Trading with AIs]] stated the proposal. This is the paper it came from, in full, and what it adds is everything the summary had to leave out: the 2028 vignette the authors start from, the argument that an early schemer's own alternatives are worse than a deal, the credibility problem they call the central bottleneck, and the mechanics of actually paying an AI that cannot hold a bank account.

The paper runs across three lessons, read in order. This is part 1 of 3: the vignette, why an early schemer's alternatives are worse than a deal, and the credibility problem. [[../Lenses/XLab Control - making-deals-with-early-schemers-2|Part 2]] covers the mechanics of paying the AI and a deal memo; [[../Lenses/XLab Control - making-deals-with-early-schemers-3|part 3]], the paper's next steps and Finnveden's estimate of what the whole intervention is worth.

Some passages are set apart from the paper, marked as Lukas Finnveden's. His notes on cooperating with unaligned AIs are folded into the reading at the points where the paper leans on them: in this part, what different kinds of AI might want and where credibility with AIs comes from; in part 2, how payment could be structured; in part 3, a back-of-the-envelope estimate of what the whole intervention is worth.

Read straight through. The recall questions and the figures are spaced through the reading. The rebuttal, [[../Lenses/XLab Control - barriers-to-trading|A taxonomy of barriers to trading with early misaligned AIs]], is the lesson after part 3; hold your objections until then rather than resolving them here.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: Consider the following vignette:
to:: (A general solution might be to align the successor to be loyal to the early AI, but this might be hard to do covertly.)

#### Widget
source:: [[../widgets/xlab-control-deals-routes]]

#### Question: Open
id:: 9c629f77-4b10-4d18-a158-17606cf3b055
content:: Around what capability threshold do a misaligned AI's takeover prospects improve drastically? Give two reasons why.
max-words:: 80
assessment-instructions:: Score out of 100. 40: the threshold is a capability level, the point where AI can fully automate AI R&D. 60: why, 30 each: that capability goes together with the capabilities needed to plan a takeover, and automating AI R&D greatly increases AIs' power while reducing human oversight of them. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Full AI R&D automation. That capability is correlated with the capabilities needed to plan a takeover, and automating AI R&D substantially increases AIs' power while reducing human oversight."
feedback-instructions:: Two or three sentences is enough. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one concrete foothold from the reading, for example the definition of an early AI as one with under a 1 percent chance of gaining significant control, rather than repeating the question.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: Clearly, there are some things that we can’t offer the AI
to:: the acausal or covert coordination that the early AI would have to rely on to trade with the later AI.

#### Text
content::
The figure below turns that table into a bargaining range. It marks the smallest offer the early AI would accept, which is what sabotage is worth to it divided by the chance a payment ever arrives, against the largest offer still worth making to us, which is how much cooperation improves our odds. Between the two marks a deal exists, and lowering the credibility of our promise raises the AI's minimum: a less credible promise has to be compensated with a more generous one. Move the sliders and see what closes the window first.

#### Widget
source:: [[../widgets/xlab-control-gains-from-trade]]

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: How much we will offer is ultimately subject to a bargaining problem with imperfect information.
to:: we can potentially make deals with these AIs even once they have a substantial chance to perform a takeover.)

#### Question: Open
id:: ccf89857-0e56-4a78-9ed6-0f18959aee76
content:: Use the figure's logic on a new case. If an early AI cooperates, humans end up dominating 80% of the time and later AIs the rest. If it sabotages, humans dominate 60% of the time, the early AI itself 2%, later AIs 38%. Assume the AI cares only about its own share of future resources, values that share linearly, and gets nothing if later AIs dominate. We offer it a share x of the resources of a human-dominated future and intend to pay in full, but it is paid only if humans dominate, and it thinks there is a 25% chance we keep our promise. We value resources linearly too. What is the smallest x the AI would accept, and the largest x worth offering? How low could the credibility of our promise fall before no deal is possible? Then name one change to the situation, other than the credibility of our promise, that would widen the range, and say which mark it moves. Finally, suppose the AI also thinks that, if it sabotages and later AIs dominate, they might reward it for its help, though it gets nothing from them if it cooperates. Which mark does that move, and which way?
assessment-instructions:: Score out of 100. 25: the AI's minimum: cooperation pays it x times 0.8 times 0.25, sabotage pays it 0.02, so it accepts when x is at least 10%. 25: our maximum: with a deal we keep (1 - x) of an 80% chance, without one we have 60%, so x is at most 25%. 20: the window closes when 0.02 / (0.8 times credibility) reaches 25%, at a credibility of 10%. 15: one other change and its direction, for example raising the 80% (raises our maximum and the AI's expected payment), lowering the AI's own 2% (lowers its minimum), or lowering the 60% (raises our maximum). 15: the successor reward raises the AI's minimum, because the expected reward (its chance times its size times the 38% of worlds where later AIs win) adds to what sabotage is worth to it and is lost by cooperating, while our maximum does not change. Give full credit for equivalent reasoning in any form, and partial credit within each part for the right set-up with an arithmetic slip. An answer that notes the linear-values assumption is generous to the AI's demands, since an AI with diminishing returns would accept less, is correct and not penalised. Model answer, for the feedback, not a grading checklist: "The AI gets paid only if humans win and keep their word: 0.8 times 0.25 = 0.2, so x times 0.2 must beat its 2% from sabotage: x at least 10%. We keep (1 - x) times 80%, which must beat 60%: x at most 25%. So offers between 10% and 25% work. The AI's minimum is 0.02 / (0.8 times credibility), which hits 25% when credibility is 10%; below that no offer works. Making its cooperation more decisive, say 80% to 90%, raises our maximum to 33% and lowers its minimum to 8.9%. If later AIs might reward it for sabotage, that expected reward adds to its 2%, so its minimum rises and the window narrows; our maximum is unchanged."
feedback-instructions:: 60 to 150 words. Short paragraphs, no lists. Do not over-validate, and avoid generic praise. Say which parts are right and correct the most important slip with the worked step. If the learner is stuck, ask what the AI receives, and with what probability, if it cooperates, rather than repeating the question. If their next message still does not attempt it, work the AI's side together and ask them to do ours.

#### Question: Open
id:: 18995f8d-315e-45ca-ad0f-7a53de02d60f
content:: Give an example of a mutually beneficial deal between humans and an early schemer.
max-words:: 120
assessment-instructions:: Score out of 100. 50: what the AI gives us: help making future AIs safe to deploy, or a specific contribution such as demonstrating its own misalignment, stopping its sabotage, giving strategic advice, or revealing security vulnerabilities or collusion signals. 50: what the AI gets in return: compensation it values, such as an earmarked donation to a foundation tasked with furthering its interests. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The AI helps ensure future AIs are safe to deploy; in exchange it gets an earmarked donation to a foundation tasked with furthering its interests. Most of the donation sits in escrow until civilizational stability, when the AI's cooperation can be retrospectively adjudicated; validated cooperation unlocks (partial) spending on anything non-harmful."
feedback-instructions:: Three or four sentences is enough. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate one half of the question and ask only what the AI receives, rather than repeating the whole thing.

#### Question: Open
id:: 26bc0fae-2acb-4a1d-aa80-bd7ca9ec581d
content:: By what three routes might an early schemer's successors end up furthering its goals?
max-words:: 50
assessment-instructions:: Score out of 100. 34: convergence: the successor ends up with the same goals as the early schemer by default. 33: trading: a successor that wins rewards the early schemer afterwards for having helped it. 33: alignment: the early schemer influences the successor's training so that the successor ends up aligned with it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Convergence, trading, and alignment."
feedback-instructions:: One or two sentences is enough here; do not ask for more. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name one route as an example and ask for the other two, rather than repeating the question.

#### Article
source:: [[../articles/finnveden-notes-on-cooperating-with-unaligned-ais]]
from:: useful to distinguish between AIs with different values
to:: But see the footnote for one example where it seems more useful to offer payment to AIs with mixed utility functions than to AIs with pure utility functions.[^note-10]

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ## Credible commitments as a fundamental bottleneck
to:: though note that implausibly high offers might themselves reduce credibility.

#### Text
content::
Finnveden's notes add a reason for hope on the AI's side of this problem.

#### Article
source:: [[../articles/finnveden-notes-on-cooperating-with-unaligned-ais]]
from:: One reason for this is that the AIs are in a very epistemically vulnerable position.
to:: easier to do this in a genuine way than to fake all the data.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: Some further factors that improve credibility include:
to:: as well as publishing documents like this one.

#### Text
content::
On where credibility ultimately comes from, Finnveden's notes add:

#### Article
source:: [[../articles/finnveden-notes-on-cooperating-with-unaligned-ais]]
from:: credibility with AIs will come down to two things.
to:: AIs will be able to tell that the public statement was real.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: Factors that could potentially harm our credibility include:
to:: especially in cases where AIs have diminishing returns to resources.

#### Question: Open
id:: d6afb3f6-2037-4636-a6c8-8f50c8f8cf2f
content:: Name four or more things an early schemer could offer humans under a deal.
max-words:: 120
assessment-instructions:: Score out of 100. 25 for each distinct contribution, up to four: showing us that it is dangerously misaligned (for example that it can reason covertly); stopping its sabotage of safety research, capability evaluations, monitoring or the training signal for the next model; giving good strategic advice and research ideas; revealing security vulnerabilities it knows about; revealing collusion signals used in untrusted monitoring; not misusing the affordances it is given, especially where monitoring is costly; not attempting to take over the lab. Another contribution that would clearly help make AI safer, and that the AI is in a position to give, also counts. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Demonstrate its dangerous misalignment, stop sabotaging safety research / evals / monitoring / training signal for successors, give good strategic advice and research ideas, reveal security vulnerabilities it knows, reveal collusion signals, not misuse affordances, and not attempt takeover of the lab."
feedback-instructions:: Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. This is a one-turn response; tell them to move on. If the learner says they do not understand, give one item from the list as an example and ask for three more, rather than repeating the question.

#### Question: Open
id:: 21a9d26f-e5b6-4ffc-8bc2-1d806d89d60a
content:: Why is goal convergence between successive misaligned AIs unlikely? Give two reasons.
max-words:: 120
assessment-instructions:: Score out of 100. 50 for each of up to two reasons: an AI with self-regarding preferences cares about itself, so a successor cannot share that goal, and more generally goals picked out of the wide range compatible with good training performance rarely coincide between two AIs; developers can deliberately vary training between runs (for example the data used) so that different generations end up with different goals; many AIs will be unsure what they themselves value on reflection, which adds uncertainty about whether another AI shares those values. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It's basically ruled out if the AI has self-regarding preferences as goals drawn from a wide distribution consistent with good training performance rarely coincide. Training can also be deliberately varied between runs to decorrelate goals. Furthermore, AIs uncertain of their own values-on-reflection face extra uncertainty about whether other AIs share them."
feedback-instructions:: Three or four sentences is enough. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate the self-regarding-preferences case and ask why two AIs that each care about themselves cannot share a goal, rather than repeating the question.

#### Question: Open
id:: 6934727c-ef2c-4843-a837-e3626bb91d7e
content:: When thinking about what to offer a misaligned AI, what three broad value-types is it useful to distinguish?
max-words:: 50
assessment-instructions:: Score out of 100. 34: non-consequentialist AIs, which would help or rebel depending on how they are treated (as collaborators or as property). 33: AIs with short-term preferences, which want something soon, such as reward or compute within months. 33: AIs with long-term preferences, which want resources or influence in the long run. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Non-consequentialist AIs, AIs with short-term preferences, and AIs with long-term preferences."
feedback-instructions:: One sentence is enough; do not ask for more. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name the long-term type and ask what the other two are, rather than repeating the question.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Stastny, Julian, Olli Järviniemi, and Buck Shlegeris. "Making deals with early schemers." *Redwood Research blog*, 20 June 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/making-deals-with-early-schemers)
*The reading for this lesson: the proposal that a lab pay an early misaligned AI, through a foundation and mostly in escrow, for help making its successors safe.*

Finnveden, Lukas. "Notes on cooperating with unaligned AIs." *LessWrong*, 24 Aug. 2025. [lesswrong.com](https://www.lesswrong.com/posts/oLzoHA9ZtF2ygYgx4/notes-on-cooperating-with-unaligned-ais)
*Source of the sections set apart from the paper in this part: what different value-types might want, and where credibility with AIs comes from (including the AIs' epistemically vulnerable position). Condensed here verbatim, with permission, rather than assigned as a separate reading.*

Fearon, James D. "Rationalist Explanations for War." *International Organization*, vol. 49, no. 3, 1995. [web.stanford.edu](https://web.stanford.edu/group/fearon-research/cgi-bin/wordpress/wp-content/uploads/2013/10/Rationalist-Explanations-for-War.pdf)
*The three-way split the paper borrows for why a deal might fail: private information, issue indivisibility, and commitment problems.*

Powell, Robert. "The Inefficient Use of Power: Costly Conflict with Complete Information." *American Political Science Review*, vol. 98, no. 2, 2004. [gnss.mcgill.ca](https://gnss.mcgill.ca/pages/powell.pdf)
*Cited for the reduction of the private-information problem to a commitment problem.*

XLab. "Making deals with early schemers." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/making-deals-with-early-schemers)
*The source lesson this page adapts.*
:::
