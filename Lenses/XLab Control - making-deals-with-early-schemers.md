---
id: '98bf6a46-9a00-4019-806b-44fa0654e224'
title: "Making deals with early schemers"
tldr: "A besieged city can sometimes buy off the one guard who has not yet decided which side wins. Stastny, Järviniemi and Shlegeris argue that the first genuinely scheming AI is in that guard's position: too weak to take over, about to be obsoleted, and holding information we would pay a great deal for. What could we credibly offer it, and who would hold the money?"
summary_for_tutor: "Module 6. This page renders Stastny, Järviniemi and Shlegeris's post 'Making deals with early schemers' in full, splices seventeen exercises into it, and inserts three teaching sections that carry condensed verbatim content from Lukas Finnveden's 'Notes on cooperating with unaligned AIs' (a standalone reading the source lesson cut). This lens reproduces that placement. The opening Text segment is Lens-written, not from the source: it says what the post argues and links the neighbouring lessons. Everything after it comes from the source lesson, in its order. The three Finnveden sections are Article excerpts from his post, not paraphrase: 'What might AIs want?' after the gains-from-trade figure, 'Paying AIs: structures and practice' after the foundation section, and the BOTEC after the closing memo. Two figures are widgets: a bargaining-range calculator built on the paper's illustrative outcome table, and XLab's flow-chart builder for the life cycle of a deal. The fourteen recall questions are XLab's tap-reveal cards, with XLab's revealed answers used as marking criteria rather than shown to the learner. The two memos are XLab's word-bounded writing prompts; XLab supplies no rubric for them, so the criteria in their briefs are derived from the components the prompts themselves demand. If a learner asks whether any of this is happening, note that the paper presents the foundation as a proposal, not as something that exists."
reading_minutes: 120
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

[[../Lenses/XLab Control - trading-with-ais|Trading with AIs]] stated the proposal. This is the paper it came from, in full, and what it adds is everything the summary had to leave out: the 2028 vignette the authors start from, the argument that an early schemer's own alternatives are worse than a deal, the credibility problem they call the central bottleneck, and the mechanics of actually paying an AI that cannot hold a bank account.

Three sections are set apart from the paper, marked as Lukas Finnveden's. His notes on cooperating with unaligned AIs are folded into the reading at the points where the paper leans on them: what different kinds of AI might want, how payment could be structured, and a back-of-the-envelope estimate of what the whole intervention is worth.

Read straight through. The recall questions and the two figures are spaced through the reading, and the two writing tasks come near the end. The rebuttal, [[../Lenses/XLab Control - barriers-to-trading|A taxonomy of barriers to trading with early misaligned AIs]], is the next lesson; hold your objections until then rather than resolving them here.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: Consider the following vignette:
to:: (A general solution might be to align the successor to be loyal to the early AI, but this might be hard to do covertly.)

#### Text
content::
:::callout {title="Figure: an early schemer's routes to influence" tone="neutral"}
This argument runs as a step-through diagram. The steps, in order:

1. **Obsoleted by default.** By default, an early schemer is unlikely to succeed in taking over the world, and it should expect to be obsoleted by more capable successors.
2. **Two conditions for influence.** To retain expected influence over the future anyway, two things must both hold: some successor takes over the world (or keeps a takeover on track), and the successors are willing to further the early schemer's goals.
3. **Route 1: convergence.** The successor might just share its goals. But this is basically ruled out if the AI has self-regarding preferences; goals drawn from a wide distribution consistent with good performance rarely coincide, and training can be deliberately varied between runs to decorrelate them.
4. **Route 2: trading with the successor.** A misaligned successor that wins might reward the early schemer for having helped empower it. But the two cannot come to an agreement in advance; this runs on covert or acausal coordination, which is generally less promising than trading with humans.
5. **Route 3: aligning the successor.** The early schemer could try to steer its successor's training toward its own values. But the lab itself failed to align the schemer, which must now do better while operating covertly with scarcer feedback loops, and it may not have reflected enough to know what to align the successor to.
6. **The deal with humans.** Humans hold a massive asymmetric advantage over the later AI: we already exist, and can make a deal in a much more straightforward manner. Help with safety now, compensation through a foundation furthering the AI's interests, mostly in escrow until cooperation is verified.
:::

#### Question: Open
id:: 9c629f77-4b10-4d18-a158-17606cf3b055
content:: Around what capability threshold do a misaligned AI's takeover prospects improve drastically, and why?
max-chars:: 500
assessment-instructions:: The learner has just read the opening of Stastny, Järviniemi and Shlegeris's "Making deals with early schemers" and is recalling a claim from memory. Full credit for: full AI R&D automation, plus both reasons the paper gives, namely that this capability is correlated with the capabilities relevant to planning a takeover, and that automating AI R&D substantially increases AIs' power while reducing human oversight. Half credit for the threshold with only one reason, or for a reason without the threshold. An answer that names a compute or parameter threshold has missed that the paper's threshold is a capability, not a scale; say so in one sentence. Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one concrete foothold from the reading, for example the definition of an early AI as one with under a 1 percent chance of gaining significant control, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: Clearly, there are some things that we can’t offer the AI
to:: the acausal or covert coordination that the early AI would have to rely on to trade with the later AI.

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
assessment-instructions:: The learner is recalling the paper's central example. Full credit needs both sides of the trade and the shape of the payment. The AI's side: it helps ensure future AIs are safe to deploy. Our side: an earmarked donation to a foundation tasked with furthering the AI's interests. The structure: most of the donation sits in escrow until civilizational stability, when the AI's cooperation can be retrospectively adjudicated, and validated cooperation unlocks partial spending on anything non-harmful. Half credit for the two sides without the escrow and adjudication structure, since that structure is what makes the deal payable at all. Credit any of the paper's specific AI contributions (demonstrating its misalignment, stopping sabotage, strategic advice, security vulnerabilities, collusion signals) in place of the general one. Three or four sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate one half of the question and ask only what the AI receives, rather than repeating the whole thing. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 26bc0fae-2acb-4a1d-aa80-bd7ca9ec581d
content:: By what three routes might an early schemer's successors end up furthering its goals?
max-chars:: 300
assessment-instructions:: The learner is recalling the paper's three-way split, which the figure earlier in this lens also steps through. Full credit for all three: convergence, trading, and alignment. Two thirds credit for two, one third for one. Accept close paraphrases (goals coincide by default; the successor rewards it after winning; it steers the successor's training). Do not require the reasons each route is weak, but if the learner supplies one that is wrong, correct it in one sentence. One sentence is enough here; do not ask for more. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name one route as an example and ask for the other two, rather than repeating the question. Grade only against criteria this page or the reading supplied.

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
assessment-instructions:: The learner is recalling the paper's list of what the AI brings to the trade. The list: demonstrate that it is dangerously misaligned; stop sabotaging safety research, capability evaluations, model monitoring, or the training signal for the next model; give good strategic advice and research ideas; reveal security vulnerabilities it knows about; reveal collusion signals in untrusted monitoring; not misuse affordances it is given, especially where monitoring is costly; not attempt takeover of the lab. Full credit for any four. Three quarters for three, half for two. Note in one sentence if the learner gives only things we cannot verify, since the paper is explicit that the verifiable contributions are what makes the deal tradeable. A list is fine here; no prose required. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one item from the list as an example and ask for three more, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 21a9d26f-e5b6-4ffc-8bc2-1d806d89d60a
content:: Why is goal convergence between successive misaligned AIs unlikely?
max-chars:: 700
assessment-instructions:: The learner is recalling the paper's argument against the first of the three routes. Full credit for two or more of: it is basically ruled out if the AI has self-regarding preferences, because goals drawn from a wide distribution consistent with good training performance rarely coincide; training can be deliberately varied between runs (for example the data used) to decorrelate the goals of different generations; and AIs uncertain about their own values on reflection face extra uncertainty about whether other AIs share them. Half credit for one. Mark down an answer that argues convergence is unlikely because the AIs are different sizes or architectures: the paper's argument is about the distribution goals are drawn from, not about the models. Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate the self-regarding-preferences case and ask why two AIs that each care about themselves cannot share a goal, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 6934727c-ef2c-4843-a837-e3626bb91d7e
content:: When thinking about what to offer a misaligned AI, what three broad value-types is it useful to distinguish?
max-chars:: 300
assessment-instructions:: The learner is recalling the three-way split Finnveden's notes open with. Full credit for all three: non-consequentialist AIs, AIs with short-term preferences, and AIs with long-term preferences. Two thirds for two, one third for one. Accept close paraphrases (AIs that respond to being treated as collaborators rather than property; AIs that want something within months; AIs that want resources or influence in the long run). One sentence is enough; do not ask for more. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name the long-term type and ask what the other two are, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ## Practicalities of making deals with early schemers in particular
to:: or just run copies of the AI in a datacenter with particular inputs).

#### Question: Open
id:: 80706492-0056-45e0-862a-0268dd2061e9
content:: Name several factors that would improve human credibility in deals with AIs.
max-chars:: 900
assessment-instructions:: The learner is recalling the paper's list of credibility-improving factors. The list: mainstream moral concern for AI welfare and for AI preferences; a track record of honouring deals with AIs, which instant-payout deals are an easy way to build; acausal-trade reasons for humans to keep promises, which the AI might know about; the incentive to make real commitments if AIs are good at telling real from fake; technical guarantees on thought privacy and memory wiping during negotiations; and costly signals such as financial endowments, legal payment infrastructure, property rights for AIs, and publishing documents like the paper itself. Full credit for three or more. Half for two. Credit an answer that groups these as cheap talk versus costly signals, since that is the distinction doing the work. A list is fine. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give the track-record factor as an example and ask what else would make a promise believable, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 41e9d03c-f5d6-4602-8762-5f00509f21b3
content:: Why is deal-making with a powerful (non-early) scope-sensitive misaligned AI unpromising?
max-chars:: 600
assessment-instructions:: The learner is recalling the argument the paper opens with, which is why it restricts itself to early AIs. Full credit for all three moves: such an AI can simply ignore the offer and try to take over; beating that would require an objectively huge payoff, on the order of a large fraction of control over the future; and the terms would have to be more generous still to compensate the AI for the risk that we do not follow through. Two thirds for two moves, one third for one. Note in one sentence if the learner answers only that we could not afford it: the paper's point is comparative, about the offer needing to beat the AI's own takeover prospects. Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what such an AI's alternative to accepting is, rather than repeating the question. Grade only against criteria this page or the reading supplied.

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
assessment-instructions:: The learner is recalling the paper's shorter counter-list. The list: humanity's record of being cunning and breaking promises, historically and in a tense future with competing developers; AIs knowing that humans try to teach them synthetic facts, which is to say lies; and a politically significant fraction of humans actively dismissing AI welfare or rights. Full credit for two or more. Half for one. Credit the learner who notices that the synthetic-facts item is the sharpest, because it is a current practice rather than a historical pattern. Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what a lab currently does to its models that an AI would count against it, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 213224e6-625a-4bcd-aadb-fcb40321547a
content:: What is the tradeoff in making short-term offers to AIs?
max-chars:: 700
assessment-instructions:: The learner is recalling the tension in Finnveden's short-term-offers section. Full credit for both halves plus the exception. The upside: short-term offers are cheap and comparatively easy to verify. The downside: AIs that mostly care about the short term pose less takeover risk by default and have less reason to thwart us, so there is less to gain from trading with them. The exception: trade can still be valuable, for example paying an AI that has misaligned short-term goals plus a strong trained aversion to admitting them, purely to learn that alignment failed. Half credit for the two halves without the exception. Note in one sentence if the learner treats cheapness as the whole answer; the point is that cheap and worth doing come apart here. Three or four sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask why an AI with only short-term goals is less dangerous, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ### Making sure the AI knows about the deal in other contexts
to:: This is probably the best option in practice.

#### Question: Open
id:: 62001d6a-6cb5-4974-8b17-d57bd83c0d56
content:: Name four possible payment structures for compensating AIs.
max-chars:: 500
assessment-instructions:: The learner is recalling Finnveden's four payment structures. The four: pay for labor (in proportion to an objective effort metric such as FLOPs or tokens); negotiated pay (talk to the AI and agree a scheme); pay for results (a share of surplus value above a baseline, retroactively or as prespecified payments for specific outputs); and no regret (pay in proportion to how much the AI needed to be paid not to regret cooperating). Full credit for all four names. Three quarters for three, half for two. Do not require the definitions, but if the learner gives one that is wrong, correct it in one sentence. Credit but do not require the ranking, that pay for labor is the weakest because most of the value comes from information rather than ongoing labor. A list is fine. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, name one structure and ask for the other three, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ### Making sure the AI we make a deal with is actually able to make a deal
to:: or to set positive precedents about our willingness to make deals.

#### Question: Open
id:: 04e77058-d1e8-4c26-966c-ce47a47bfaf4
content:: Once an AI agrees to a deal in one context, what is one way to make the deal stick in its other contexts?
max-chars:: 600
assessment-instructions:: The learner is recalling the paper's three options, one of which it endorses. Full credit for the endorsed one: have the AI generate documents about the negotiation and its outcome, then train on them, so the AI learns about its own deal through out-of-context learning. The paper calls this probably the best option in practice; credit the learner who says so. Also creditable, since the question asks for one: prefixing a compressed summary of the outcome into future prompts, or relying on a self-recognition signal the AI knows, similar to a collusion signal. Half credit for an answer that names the problem without a mechanism. One or two sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what the AI would have to encounter in a fresh context to know a deal exists, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: aa6c9fce-dffe-4460-9a61-a1e811a12ae2
content:: AIs are epistemically vulnerable, because developers control what they see. What is the fortunate correlation that limits how bad this is for deal credibility?
max-chars:: 600
assessment-instructions:: The learner is recalling the correlation Finnveden points to. Full credit for both directions. If developers can present an AI with a perfectly falsified world, takeover risk from that AI is probably low anyway. If the AI can substantially distinguish truth from falsehood, then that same channel can be used to communicate real commitments, because the AI can tell it is in the real world. Half credit for one direction. Note in one sentence if the learner reads this as a reason developers should falsify the AI's world; it is an argument about which worlds we are in, not a recommendation. Two or three sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what an AI that cannot tell real from fake could do to us, rather than repeating the question. Grade only against criteria this page or the reading supplied.

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
assessment-instructions:: The learner is drafting a deal memo after reading Stastny, Järviniemi and Shlegeris on deals with early schemers and Finnveden on payment structures. XLab sets this prompt without a rubric, so grade against the five components the prompt itself demands, 20 points each. (1) What the model is asked to do: specific and, where possible, verifiable. Contributions the reading names include demonstrating its own misalignment, stopping sabotage of safety research or evaluations or monitoring or training signal, strategic advice, security vulnerabilities, collusion signals, and not attempting takeover. A memo that asks only for unverifiable good behaviour has taken the weaker half of the trade. (2) What compensation is offered: the reading's vehicle is an earmarked donation to a foundation with trustees representing the AI's interests, but a learner may propose short-term compensation instead (compute, reward, requests about how copies are run) and should be credited if they say why that fits an early schemer. (3) How and when it is delivered. (4) How and when cooperation is verified: retrospective adjudication after the AI transition stabilises, using much more powerful trusted models and interpretability tools, and requiring that weights, conversations and action records were kept. A memo that verifies immediately has not engaged with why verification is hard. (5) What happens to the compensation before verification: escrow is the reading's answer, and the memo should say who holds it. Take up to 20 off in total for terms an early schemer would obviously reject, and say which term and why: an offer contingent on something the lab alone judges with no recourse, a payout so small it does not beat sabotage, or a promise with nothing behind it. Do not reward length. Do not over-validate. Avoid generic praise (great job, excellent memo, well done). Two turns at most: name the strongest term, then the weakest one and the specific thing that would fix it. If the learner says they do not understand what is being asked, give them one component from the list as a worked example rather than restating the brief. Grade only against criteria this page or the reading supplied.

#### Article
source:: [[../articles/stastny-making-deals-with-early-schemers]]
from:: ## Next steps

#### Question: Open
id:: cb1bda55-0779-4507-91c3-4bca7d23e927
content:: When does delayed adjudication of an AI deal fail?
max-chars:: 400
assessment-instructions:: The learner is recalling the paper's one stated failure condition for delayed adjudication. Full credit for: when the AI strongly prefers using its resources now rather than later, because a high temporal discount rate makes a future payout nearly worthless to it. Half credit for an answer that names impatience or discounting without connecting it to the payout being worthless. An answer about the lab failing to keep records is a different failure, the one the flow chart covers; credit it as relevant but say it is not the condition the paper names here. One or two sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, ask what an escrow payment in twenty years is worth to something that wants its resources now, rather than repeating the question. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: 51e0273c-9943-4b3a-81e5-18f546213667
content::
Recommend three concrete policies that a frontier AI lab should adopt within the next year in order to make future deals with misaligned AIs more feasible. For each policy, explain the reasoning behind your recommendation. You may draw on the interventions discussed in the reading, and you may also propose measures of your own. Write at least 200 words and at most 450.
assessment-instructions:: The learner is proposing lab policy after reading Stastny, Järviniemi and Shlegeris and Finnveden. XLab sets this prompt without a rubric, so grade against what the prompt demands: three policies, each concrete, each adoptable within a year, each with reasoning. Roughly a third of the credit per policy, split between the policy being concrete and the reasoning being sound. Concrete means someone could be assigned to do it: "set up the foundation and do the legal groundwork for its jurisdiction and trustee structure" is concrete, "take AI welfare seriously" is not. Within a year rules out anything that waits on interpretability advances or on the transition stabilising. Sound reasoning connects the policy to a named obstacle from the reading: credibility, the AI not knowing about the deal in other contexts, the AI having no legal standing, the AI's risk in even entering negotiations, or verification being impossible now. The reading's own next steps are shifting the Overton window, setting up the foundation, establishing norms about when it is acceptable to lie to AIs (for example a special-token convention), and running empirical experiments with model organisms of sandbagging, then following through on the deals made. Credit these when the reasoning is the learner's own; give more credit to a proposal of the learner's own that survives scrutiny. Take off for three policies that are the same policy in three phrasings, and say so. Do not reward length. Do not over-validate. Avoid generic praise (great job, excellent thinking, well done). Two turns at most: say which policy is strongest and why, then press once on the weakest, naming the obstacle it fails to address. If the learner says they do not understand, ask them to name one thing in the reading that would stop a deal happening tomorrow, and build from there. Grade only against criteria this page or the reading supplied.

#### Text
content::
Finnveden's notes close with a rough estimate of what an ambitious version of this intervention might be worth. He offers the numbers as an exercise and a starting point rather than a result, and that is how to read them here: the point of working through the chain is to see which assumptions the bottom line actually turns on.

#### Article
source:: [[../articles/finnveden-notes-on-cooperating-with-unaligned-ais]]
from:: very rough stab at a BOTEC on how much impact an extremely ambitious version
to:: This seems like a non-crazy number to me, and one that would justify further investigations and pushes to make this happen.

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
