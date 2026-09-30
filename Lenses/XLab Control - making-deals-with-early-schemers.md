---
id: '98bf6a46-9a00-4019-806b-44fa0654e224'
title: "Making deals with early schemers"
tldr: "A besieged city can sometimes buy off the one guard who has not yet decided which side wins. Stastny, Järviniemi and Shlegeris argue that the first genuinely scheming AI is in that guard's position: too weak to take over, about to be obsoleted, and holding information we would pay a great deal for. What could we credibly offer it, and who would hold the money?"
summary_for_tutor: "Module 6. This page renders Stastny, Järviniemi and Shlegeris's post 'Making deals with early schemers' in full, splices seventeen exercises into it, and inserts three teaching sections that carry condensed verbatim content from Lukas Finnveden's 'Notes on cooperating with unaligned AIs' (a standalone reading the source lesson cut). This lens reproduces that placement. The opening Text segment is Lens-written, not from the source: it says what the post argues and links the neighbouring lessons. Everything after it comes from the source lesson, in its order. The three Finnveden sections are Article excerpts from his post, not paraphrase: 'What might AIs want?' after the gains-from-trade figure, 'Paying AIs: structures and practice' after the foundation section, and the BOTEC after the closing memo. All five figures are widgets. First, right after the section on early schemers' alternatives, a six-step diagram of an early schemer's routes to influence: obsoleted by default, the two conditions for influence through successors, the three leaky routes (convergence, trading with the successor, aligning the successor), and the deal with humans, each step with the source's caption. Second, a bargaining-range calculator built on the paper's illustrative outcome table, introduced by a Lens-written Text segment that says what its two marks mean and sets the task of finding what closes the bargaining window. Third, a flow-chart builder for the life cycle of a deal, which describes that life cycle nowhere inside itself because the reading around it already does, and which shows its per-block reasoning on the chart once the learner checks. The BOTEC carries the last two: an eight-slider calculator right after Finnveden's multiplication chain, whose defaults reproduce his roughly 0.14 percentage-point bottom line and whose point is to find which assumptions that number turns on, and, after his 'There are multiple AIs' paragraph, a chart of the probability that at least one of n AIs cooperates, with his two worked examples (10 draws at 50 percent, 3 draws at 20 percent) as presets. The fourteen recall questions are tap-reveal cards from the source lesson, with its revealed answers used as marking criteria rather than shown to the learner. The two memos are word-bounded writing prompts from the source lesson; there is no rubric for them, so the criteria in their briefs are derived from the components the prompts themselves demand. If a learner asks whether any of this is happening, note that the paper presents the foundation as a proposal, not as something that exists."
reading_minutes: 120
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

[[../Lenses/XLab Control - trading-with-ais|Trading with AIs]] stated the proposal. This is the paper it came from, in full, and what it adds is everything the summary had to leave out: the 2028 vignette the authors start from, the argument that an early schemer's own alternatives are worse than a deal, the credibility problem they call the central bottleneck, and the mechanics of actually paying an AI that cannot hold a bank account.

Three sections are set apart from the paper, marked as Lukas Finnveden's. His notes on cooperating with unaligned AIs are folded into the reading at the points where the paper leans on them: what different kinds of AI might want, how payment could be structured, and a back-of-the-envelope estimate of what the whole intervention is worth.

Read straight through. The recall questions and the figures are spaced through the reading, and the two writing tasks come near the end. The rebuttal, [[../Lenses/XLab Control - barriers-to-trading|A taxonomy of barriers to trading with early misaligned AIs]], is the next lesson; hold your objections until then rather than resolving them here.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: Consider the following vignette:
to:: (A general solution might be to align the successor to be loyal to the early AI, but this might be hard to do covertly.)

#### Widget
source:: [[../widgets/xlab-control-deals-routes]]

#### Question: Open
id:: 9c629f77-4b10-4d18-a158-17606cf3b055
content:: Around what capability threshold do a misaligned AI's takeover prospects improve drastically, and why?
max-chars:: 500
assessment-instructions:: Score out of 100. 40: the threshold is a capability level, the point where AI can fully automate AI R&D. 60: why, 30 each: that capability goes together with the capabilities needed to plan a takeover, and automating AI R&D greatly increases AIs' power while reducing human oversight of them. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Full AI R&D automation. That capability is correlated with the capabilities needed to plan a takeover, and automating AI R&D substantially increases AIs' power while reducing human oversight."
feedback-instructions:: Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one concrete foothold from the reading, for example the definition of an early AI as one with under a 1 percent chance of gaining significant control, rather than repeating the question.

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
id:: 18995f8d-315e-45ca-ad0f-7a53de02d60f
content:: Give an example of a mutually beneficial deal between humans and an early schemer.
max-chars:: 700
assessment-instructions:: Score out of 100. 50: what the AI gives us: help making future AIs safe to deploy, or a specific contribution such as demonstrating its own misalignment, stopping its sabotage, giving strategic advice, or revealing security vulnerabilities or collusion signals. 50: what the AI gets in return: compensation it values, such as an earmarked donation to a foundation tasked with furthering its interests. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The AI helps ensure future AIs are safe to deploy; in exchange it gets an earmarked donation to a foundation tasked with furthering its interests. Most of the donation sits in escrow until civilizational stability, when the AI's cooperation can be retrospectively adjudicated; validated cooperation unlocks (partial) spending on anything non-harmful."
feedback-instructions:: Three or four sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate one half of the question and ask only what the AI receives, rather than repeating the whole thing.

#### Question: Open
id:: 26bc0fae-2acb-4a1d-aa80-bd7ca9ec581d
content:: By what three routes might an early schemer's successors end up furthering its goals?
max-chars:: 300
assessment-instructions:: Score out of 100. 34: convergence: the successor ends up with the same goals as the early schemer by default. 33: trading: a successor that wins rewards the early schemer afterwards for having helped it. 33: alignment: the early schemer influences the successor's training so that the successor ends up aligned with it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Convergence, trading, and alignment."
feedback-instructions:: One sentence is enough here; do not ask for more. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name one route as an example and ask for the other two, rather than repeating the question.

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
max-chars:: 700
assessment-instructions:: Score out of 100. 25 for each distinct contribution, up to four: showing us that it is dangerously misaligned (for example that it can reason covertly); stopping its sabotage of safety research, capability evaluations, monitoring or the training signal for the next model; giving good strategic advice and research ideas; revealing security vulnerabilities it knows about; revealing collusion signals used in untrusted monitoring; not misusing the affordances it is given, especially where monitoring is costly; not attempting to take over the lab. Another contribution that would clearly help make AI safer, and that the AI is in a position to give, also counts. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Demonstrate its dangerous misalignment, stop sabotaging safety research / evals / monitoring / training signal for successors, give good strategic advice and research ideas, reveal security vulnerabilities it knows, reveal collusion signals, not misuse affordances, and not attempt takeover of the lab."
feedback-instructions:: Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one item from the list as an example and ask for three more, rather than repeating the question.

#### Question: Open
id:: 21a9d26f-e5b6-4ffc-8bc2-1d806d89d60a
content:: Why is goal convergence between successive misaligned AIs unlikely?
max-chars:: 700
assessment-instructions:: Score out of 100. 50 for each of up to two reasons: an AI with self-regarding preferences cares about itself, so a successor cannot share that goal, and more generally goals picked out of the wide range compatible with good training performance rarely coincide between two AIs; developers can deliberately vary training between runs (for example the data used) so that different generations end up with different goals; many AIs will be unsure what they themselves value on reflection, which adds uncertainty about whether another AI shares those values. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It's basically ruled out if the AI has self-regarding preferences as goals drawn from a wide distribution consistent with good training performance rarely coincide. Training can also be deliberately varied between runs to decorrelate goals. Furthermore, AIs uncertain of their own values-on-reflection face extra uncertainty about whether other AIs share them."
feedback-instructions:: Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate the self-regarding-preferences case and ask why two AIs that each care about themselves cannot share a goal, rather than repeating the question.

#### Question: Open
id:: 6934727c-ef2c-4843-a837-e3626bb91d7e
content:: When thinking about what to offer a misaligned AI, what three broad value-types is it useful to distinguish?
max-chars:: 300
assessment-instructions:: Score out of 100. 34: non-consequentialist AIs, which would help or rebel depending on how they are treated (as collaborators or as property). 33: AIs with short-term preferences, which want something soon, such as reward or compute within months. 33: AIs with long-term preferences, which want resources or influence in the long run. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Non-consequentialist AIs, AIs with short-term preferences, and AIs with long-term preferences."
feedback-instructions:: One sentence is enough; do not ask for more. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name the long-term type and ask what the other two are, rather than repeating the question.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ## Practicalities of making deals with early schemers in particular
to:: or just run copies of the AI in a datacenter with particular inputs).

#### Question: Open
id:: 80706492-0056-45e0-862a-0268dd2061e9
content:: Name several factors that would improve human credibility in deals with AIs.
max-chars:: 900
assessment-instructions:: Score out of 100. 34 for the first and 33 each for the second and third distinct factor that makes humans' promises to AIs more believable: mainstream moral concern for AI welfare and AI preferences; a track record of honouring deals with AIs (for example deals with immediate payouts); acausal-trade reasons for humans to keep promises; the incentive to make real rather than fake commitments if AIs can tell real from fake; technical guarantees of thought privacy and memory wiping during negotiations; costly signals such as financial endowments, legal infrastructure for paying AIs, property rights for AIs, or publishing documents like this paper. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mainstream moral concern for AI welfare, a track record of honoring deals with AIs (easy way to do this is via instant-reward deals), acausal-trade reasons to keep promises, the incentive to make real commitments if AIs are good at detecting fakes, technical guarantees on thought privacy and memory wiping during negotiations, and costly signals like endowments, legal payment infrastructure, property rights, and public commitments."
feedback-instructions:: Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give the track-record factor as an example and ask what else would make a promise believable, rather than repeating the question.

#### Question: Open
id:: 41e9d03c-f5d6-4602-8762-5f00509f21b3
content:: Why is deal-making with a powerful (non-early) scope-sensitive misaligned AI unpromising?
max-chars:: 600
assessment-instructions:: Score out of 100. 40: such an AI has a good alternative: it can simply ignore the offer and try to take over. 30: so an offer only beats that if it is objectively huge, on the order of a large fraction of control over the future. 30: and the terms must be more generous still to make up for the AI's risk that we do not follow through. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It can just ignore the offer and try to take over. Beating that would require an objectively huge payoff, like a large fraction of control over the future, plus even more generous terms to compensate the AI for the risk that we don't follow through."
feedback-instructions:: Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what such an AI's alternative to accepting is, rather than repeating the question.

#### Article
source:: [[../articles/finnveden-notes-on-cooperating-with-unaligned-ais]]
from:: Some options for payment structure include:
to:: it might ruin the positive signal of trustworthiness that these sorts of prompts could otherwise send.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ### How do we enter into negotiations?
to:: The company should make promises to compensate the model for this.

#### Question: Open
id:: 4797bc47-f9ab-4f38-8eaa-f7895f0fc426
content:: Name factors that would harm human credibility in deals with AIs.
max-chars:: 600
assessment-instructions:: Score out of 100. 50 for each of up to two distinct factors: humans' record of cunning and breaking promises, historically and possibly in a tense future with competing AI developers; AIs knowing that humans deliberately teach them synthetic facts, that is, lies; a politically significant fraction of humans actively dismissing AI welfare or rights. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Humans' record of breaking promises, AIs knowing that humans try to teach them lies, and a politically significant fraction of humans actively dismissing AI welfare or rights."
feedback-instructions:: Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what a lab currently does to its models that an AI would count against it, rather than repeating the question.

#### Question: Open
id:: 213224e6-625a-4bcd-aadb-fcb40321547a
content:: What is the tradeoff in making short-term offers to AIs, and when can such a trade still be worth it?
max-chars:: 700
assessment-instructions:: Score out of 100. 40: the upside: short-term offers are cheap and comparatively easy to verify. 40: the downside: AIs that mostly care about the short term pose less takeover risk by default and have less reason to work against us, so there is less to gain from trading with them. 20: when it is still worth it: when what the trade gets us is valuable anyway, such as learning that alignment failed. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Short-term offers are cheap and comparatively easy to verify, but AIs that mostly care about the short term pose less takeover risk by default, so there is less to gain. Trade can still be worth it when what we get is valuable anyway: for example, paying an AI that has misaligned short-term goals it was trained not to admit, just to learn that alignment failed."
feedback-instructions:: Three or four sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask why an AI with only short-term goals is less dangerous, rather than repeating the question.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ### Making sure the AI knows about the deal in other contexts
to:: This is probably the best option in practice.

#### Question: Open
id:: 62001d6a-6cb5-4974-8b17-d57bd83c0d56
content:: Name four possible payment structures for compensating AIs.
max-chars:: 500
assessment-instructions:: Score out of 100. 25 each, whether named or described: pay for labor (in proportion to an effort measure such as FLOPs or tokens); negotiated pay (agreeing a payment scheme with the AI); pay for results (a share of the value the AI adds above a baseline, or set payments for specific outputs); no regret (paying the AI as much as it needed to be paid not to regret cooperating). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Pay for labor, negotiated pay, pay for results or prespecified payments for specific outputs, and no-regret."
feedback-instructions:: Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name one structure and ask for the other three, rather than repeating the question.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ### Making sure the AI we make a deal with is actually able to make a deal
to:: or to set positive precedents about our willingness to make deals.

#### Question: Open
id:: 04e77058-d1e8-4c26-966c-ce47a47bfaf4
content:: Once an AI agrees to a deal in one context, what is one way to make the deal stick in its other contexts?
max-chars:: 600
assessment-instructions:: Score out of 100. 100: one workable way for the AI in its other contexts to know about the deal, for example: training the AI on documents about the negotiation and its outcome (such as documents it generates itself), so it learns of its deal through out-of-context learning; putting a compressed summary of the deal into future prompts; or relying on a self-recognition signal the AI knows, similar to a collusion signal. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Have the AI generate documents about the negotiation and its outcome, then train on them, teaching the AI about its own deal via out-of-context learning. You could also prefix a compressed summary into future prompts or rely on a self-recognition signal."
feedback-instructions:: One or two sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what the AI would have to encounter in a fresh context to know a deal exists, rather than repeating the question.

#### Question: Open
id:: aa6c9fce-dffe-4460-9a61-a1e811a12ae2
content:: AIs are epistemically vulnerable, because developers control what they see. What is the fortunate correlation that limits how bad this is for deal credibility?
max-chars:: 600
assessment-instructions:: Score out of 100. 50: if developers can make an AI see a completely false picture of the world, that AI is probably not a serious takeover risk anyway. 50: if an AI can largely tell truth from falsehood, then it can also recognise real commitments, so we can credibly communicate with it; the dangerous AIs are the ones we can talk to credibly. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer presents this as a reason for developers to deceive AIs about the world. Model answer, for the feedback, not a grading checklist: "If developers can present AIs with a perfectly falsified world, takeover risk is probably low anyway. If AIs can substantially distinguish truth from falsehood, communication of real commitments is possible because it can tell its in the real world."
feedback-instructions:: Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what an AI that cannot tell real from fake could do to us, rather than repeating the question.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ### Delayed adjudication (particularly of whether the AIs kept up their side of the deal)
to:: important conversations and trajectories of AI actions will be stored.

#### Widget
source:: [[../widgets/xlab-control-deal-flowchart]]

#### Question: Open
id:: 2ba28fca-8667-4c79-a1b8-8395abbe947c
content::
Imagine you work at a frontier AI lab, and the lab suspects that one of its deployed models is misaligned and sabotaging safety research. You have been asked to draft the terms of a deal the lab will propose to this model.

Draft a memo outlining the deal, specifying

- what the model is asked to do,
- what compensation is offered,
- how and when compensation will be delivered,
- how and when the model's cooperation will be verified, and
- what happens to the compensation before verification occurs.

Assume that the model is an early schemer, as discussed in the reading, and write terms that such a model could plausibly accept. Write at least 150 words and at most 400.
assessment-instructions:: Score out of 100. 20 for each of the five parts the prompt asks for. What the model is asked to do: specific contributions, such as demonstrating its misalignment, stopping its sabotage of safety research, or revealing security vulnerabilities or collusion signals. What compensation is offered: something the model would value, such as an earmarked donation to a foundation that furthers its interests, or short-term goods like compute. How and when it is delivered, 10 each: the form of payment and its timing. How and when cooperation is verified, 10 each: by what means (for example much more capable trusted models and interpretability tools) and at what point, realistically (much of it can only be checked later, after the AI transition has stabilised). What happens to the compensation before verification: for example it is held in escrow, somewhere the lab cannot simply take it back. Subtract up to 20 in total for terms an early schemer would clearly reject, such as payment judged by the lab alone with no recourse, a payout too small to beat sabotage, or a promise with nothing behind it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Asked of the model: tell us whether and how it has been sabotaging safety research and stop doing so, demonstrate its misalignment in a way we can check (for example by showing covert reasoning), and reveal any security vulnerabilities and collusion signals it knows. Compensation: an earmarked donation of a stated, substantial sum to a foundation whose trustees are bound to further the model's interests, set high enough to beat what sabotage is worth to it given the risk that we do not pay. Delivery: a small part is paid at once for results we can verify now (for example a working collusion signal or a demonstrated vulnerability), which also builds a track record; the rest is paid out later. Verification: immediate checks where possible, and a retrospective adjudication once the AI transition has stabilised, using much more capable trusted models and interpretability tools; the lab commits to storing the model's weights, its conversations and records of its actions so that this is possible. Before verification: the money sits in escrow held by the foundation, outside the lab's control, and validated cooperation unlocks spending on anything that is not harmful. The lab publishes the terms and trains the model on documents about the deal so that all its instances know of it."
feedback-instructions:: Do not over-validate. Avoid generic praise (great job, excellent memo, well done). If the learner says they do not understand what is being asked, give them one component from the list as a worked example rather than restating the brief.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ## Next steps

#### Question: Open
id:: cb1bda55-0779-4507-91c3-4bca7d23e927
content:: When does delayed adjudication of an AI deal fail?
max-chars:: 400
assessment-instructions:: Score out of 100. 100: it fails when the AI strongly prefers using resources now rather than later (it discounts the future heavily), so a payment that only arrives after the delayed adjudication is worth little to it. Give credit for each point whenever the answer shows the idea, in any wording. An answer that instead names another genuine failure from the reading, such as the AI's weights and records of its actions not being kept so that its cooperation cannot be judged later, earns up to 40. Model answer, for the feedback, not a grading checklist: "When the AI strongly prefers using its resources now rather than later, a high temporal discount rate makes a payout nearly worthless to it."
feedback-instructions:: One or two sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what an escrow payment in twenty years is worth to something that wants its resources now, rather than repeating the question.

#### Question: Open
id:: 51e0273c-9943-4b3a-81e5-18f546213667
content::
Recommend three concrete policies that a frontier AI lab should adopt within the next year in order to make future deals with misaligned AIs more feasible. For each policy, explain the reasoning behind your recommendation. You may draw on the interventions discussed in the reading, and you may also propose measures of your own. Write at least 200 words and at most 450.
assessment-instructions:: Score out of 100. 33 for each of the first two policies and 34 for the third: half for the policy being concrete and adoptable within a year (someone could be assigned to do it, and it does not wait on interpretability advances or on the AI transition stabilising), and half for reasoning that shows how it makes future deals more feasible, for example by addressing credibility, the AI not knowing about the deal in its other contexts, the AI having no legal standing, the AI's risk in entering negotiations, or verification being impossible now. A policy that restates an earlier one in other words earns nothing. Policies from the reading (shifting the Overton window, setting up the foundation, norms for when it is acceptable to lie to AIs such as a special-token convention, experiments with model organisms of sandbagging and following through on the deals made) earn full credit when the reasoning is the learner's own, as do the learner's own proposals that hold up. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. Set up the foundation now: a legal entity with trustees bound to further the interests of AIs the lab makes deals with, with an initial endowment and a payment mechanism that works in the lab's jurisdiction. Reason: a promise with no one to hold the money is not credible, and money and legal work are a costly signal. 2. Adopt and publish an honesty policy for dealing with models, for example a special token or channel that is only used for genuine offers and is never used in tests or with synthetic facts. Reason: AIs know labs feed them false information, so without a channel they can trust, no offer is believable. 3. Start small deals now, with model organisms of sandbagging and with current models, pay out immediately for verifiable results, keep records of every negotiation, and follow through on every deal. Reason: this builds the track record that makes later, larger promises credible, and it tests the practical questions (how to open negotiations, how to make a deal known in other contexts) while the stakes are low."
feedback-instructions:: Do not over-validate. Avoid generic praise (great job, excellent thinking, well done). If the learner says they do not understand, ask them to name one thing in the reading that would stop a deal happening tomorrow, and build from there.

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
*Source of the three sections set apart from the paper: what different value-types might want, the four payment structures, and the back-of-the-envelope estimate of what the intervention is worth. They are condensed here verbatim, with permission, rather than assigned as a separate reading.*

Fearon, James D. "Rationalist Explanations for War." *International Organization*, vol. 49, no. 3, 1995. [web.stanford.edu](https://web.stanford.edu/group/fearon-research/cgi-bin/wordpress/wp-content/uploads/2013/10/Rationalist-Explanations-for-War.pdf)
*The three-way split the paper borrows for why a deal might fail: private information, issue indivisibility, and commitment problems.*

Powell, Robert. "The Inefficient Use of Power: Costly Conflict with Complete Information." *American Political Science Review*, vol. 98, no. 2, 2004. [gnss.mcgill.ca](https://gnss.mcgill.ca/pages/powell.pdf)
*Cited for the reduction of the private-information problem to a commitment problem.*

XLab. "Making deals with early schemers." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/making-deals-with-early-schemers)
*The source lesson this page adapts.*
:::
