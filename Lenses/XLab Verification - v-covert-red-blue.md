---
id: '8d4ad089-70ef-4367-96e6-b9f1ce8e4b93'
title: "Red team, blue team: from treaty requirements to a verification system"
tldr: "A treaty says what is forbidden. An engineer proposes a machine that might show whether it happened. Your job is to sit on the panel that decides whether the machine is good enough, and to say precisely which obligations it can carry and which it cannot touch."
summary_for_tutor: "XLab's unit 3.2, restored from git history and retargeted at the primary sources. The learner reads the operative paragraphs of Articles IV to VII of the MIRI draft agreement (Scher, Abecassis, Barnett and Abeyta) and Sections 1 to 3 of Cankaya's low-trust compute verification architecture, then writes a 2 to 6 page expert review answering ten questions. The spine of the whole exercise is a coverage judgment: Article VII paragraph 1(e) and 1(f), workload declarations and rerunning declared workloads, are the two toolkit items Cankaya's system actually implements, and Articles V and VI, chip consolidation and production and transfer monitoring, are almost entirely outside it. Push the learner to cite by article and paragraph and by section, to separate what the sources state from what they infer, and to notice that the two texts are not independent, since Aaron Scher is thanked in Cankaya's acknowledgements. Section B at the end returns to the ten-route taxonomy and scores seven of the routes; three routes are missing from XLab's scored table and that gap is flagged in the lens."
tags: [wip]
duration_minutes: 180
authors:
  - Elias+Claude
---
#### Text
content::
{>>{"author":"Elias's AI","timestamp":1788521011728}@@Restored from XLab commit a10955c^, src/content/lessons/verification/covert-red-blue.mdx (XLab's unit 3.2), together with the ten writing prompts v-task-covert-red-blue-1 to -10 from src/content/verification/exercises.ts at the same commit. Upstream deleted all of it in a10955c.

The largest deviation is deliberate and is the reason the lesson could be restored at all. XLab built this exercise around their own five-page instructional adaptation of the two sources, and their own packet notice said it was an adaptation and not a verbatim reproduction, with the originals remaining authoritative. That packet is not reproduced here. The learner reads the real Articles IV to VII and the real Sections 1 to 3, inlined as article excerpts, and every question has been retargeted at real article, paragraph and section numbers, checked against the texts. XLab's assignment note that "students must not be assessed on details that appear only in omitted passages" no longer applies, because nothing is omitted from the assigned range.

Note on the count: the brief I worked from said nine writing tasks, and XLab's own commit message says nine. There are ten in exercises.ts at a10955c^, numbered 1 to 10. All ten are here. The tenth, overall judgment and redesign, is the one the other nine build to, so dropping it would have been the wrong nine.

Smaller deviations: em dashes removed under the Lens house rule; XLab's unit number dropped from the title, because renumbering this module is Elias's decision; bracket citation markers replaced by a Works cited callout; and XLab's MemoDesk card is not carried over, since its slot is unspecified in memos.ts and there is nothing to import.<<}
You have seen how a covert operation is built and how it is taken apart. Now the harder job: deciding whether a proposed machine would actually make a rule enforceable.

Two documents sit on the table. One is a draft treaty written like a treaty, with articles, paragraphs, thresholds and remedies. The other is a working draft of a verification architecture, published by its author to be argued with. Neither was written with the other in view, and that is the interesting part. The treaty says what must be verified; the architecture says what can be evidenced. Your review is about the gap between those two sentences.

\## Assigned reading

Read the operative paragraphs of **Articles IV to VII** of the draft agreement, and **Sections 1 to 3** of the system overview. Both are inlined below. The material around each excerpt is collapsed rather than removed, so you can open the drafters' own Precedent and Notes sections whenever you want to know why a paragraph reads the way it does.

If you read the whole of the system overview in the first lens of this module, you are re-reading Sections 1 to 3 here with a different question in mind: not what does this system do, but which treaty obligations could it carry.

\### How to cite

- The treaty by **article and paragraph**, for example Article VII.1(f) or Article V.3.
- The system overview by **section**, for example Section 2b or Section 3.2.2.
- Anything you bring from outside either text needs a link.

#### Article
source:: [[../articles/scher-an-international-agreement-to-prevent-the-premature-creation-of-artificial-superintelligence]]
from:: "Each Party agrees to ban and prohibit AI training above the following thresholds: Any training run exceeding the Strict Threshold or any post-training run exceeding the Strict Post-training Threshold."
to:: "The CTB creates and maintains an AI Technique Whitelist specifying allowed AI methods and techniques. The CTB may modify this Whitelist in accordance with Article III. Training runs above the Monitored Threshold may only employ techniques on this Whitelist."

#### Article
from:: "Each Party ensures that within their jurisdiction, all covered chip clusters (CCCs), as defined in Article II"
to:: "Salvage or resale of components from such hardware is prohibited unless expressly authorized by the CTB."

#### Article
from:: "The CTB will coordinate monitoring of AI chip production facilities and key inputs to chip production."
to:: "Such limits aim to allow replacement of aging chips and modest expansion for approved applications while preventing stockpiling that would reduce the time required for a Party to develop ASI after withdrawal."

#### Article
from:: "Parties accept continuous on‑site verification of total chip usage at declared CCCs."
to:: "The CTB will lead research and engineering to develop better technologies for chip use monitoring and verification. Parties will support these efforts"

#### Article
source:: [[../articles/cankaya-a-system-overview-for-near-term-low-trust-ai-compute-verification]]
from:: "In order to plan and execute under tight timelines, one needs to make some strategic bets, instead of hedging too much and keeping all options open."
to:: "Faults, if triggered on purpose, can leak one bit of information to the verifier, per event. The prover and verifier need a pre-agreed budgeted rate for such faults, beyond which suspicion is raised."

#### Text
content::
\## Your role and assignment

You are advising an independent expert panel that must determine whether the proposed low-trust compute-verification system could make the obligations in Articles IV to VII credible and enforceable.

Prepare a 2 to 6 page expert review, excluding references. Answer Questions 1 to 10 in order. You may use course materials and external sources.

Throughout your review:

- Distinguish what each source states from what you infer and from what remains unspecified;
- Cite the treaty by article and paragraph, and the system overview by section;
- Provide reliable links for external factual or technical claims;
- Quote only the language needed to establish an ambiguity, gap, disputed claim, or possible error;
- Treat the verification system as one possible component of the treaty regime, not automatically as a complete implementation of Articles IV to VII.

#### Question: Open
id:: 38a92abc-9dd5-476e-b9a9-264c13c02994
content:: **Question 1. Objective and verification chain**

State the principal objective of Articles IV to VII and the principal objective of the low-trust verification system. Then reconstruct how the two are meant to connect:

regulated activity, captured evidence, protected commitment or record, challenge or evaluation, compliance finding, response.

What observable result would count as successful verification?
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Score in three parts: objectives 30, chain 50, observable result 20.

Objectives. The treaty side is stated, not inferred: Article VII.2, "The aim of this verification is to ensure chips are not being used for prohibited activities, such as large-scale AI training described in Article IV." A good answer reads Articles IV to VII as one instrument serving that aim, with IV.1 setting the prohibition, V.1 and V.3 putting covered chip clusters inside declared and inspectable facilities so that they can be monitored at all, VI.1 keeping newly produced chips tracked from fabrication until installation so that unmonitored supply chains are not established, and VII providing the continuous use verification. The system side is in Section 1, where the author states three aims: make technical objectives for verification more specific and actionable, contribute a first high-level reference architecture, and gather an overview of relevant work. Section 2a carries the load-bearing assertion: verification of high-level aggregate properties such as total training FLOP or the training-versus-inference split is expected to be insufficient against covert development or deployment, so evidence must be collision-resistant and tied to individual ML workloads.

Chain. Award for each link that names a section: capture at line rate by non-programmable taps that hash payloads over packet groups without knowing object boundaries (Section 3.2.1); hashes leaving over a split, sanitized fiber so prover and verifier hold identical commitments while the prover retains the plaintext and writes a manifest (3.2.1); the verifier issuing a challenge on a random or risk-based sample after commitment (3.2.2); reassembly, re-execution and compliance screening inside the prover's auditing environment (3.2.2); cross-checking TCBs and a minimal pre-agreed disclosure through sanitized egress (3.2.2). Credit the learner for noticing that the last link, response, is not in the system overview: Section 3.2.2 says what investigation means is a partly political question and treats it as out of scope, while the treaty supplies the response in Article VII.3, hardware powered off and its non-operation continually verified where the CTB cannot obtain sufficient assurance.

Observable result. Successful verification at sample level is negative: challenged preimages that hash to their commitments and a re-execution that reproduces the declared workload under the declared metadata. Full marks require the learner to connect that to Section 2b, where deterrence comes from detection likelihood multiplied by the cost of being caught exceeding expected gain, so the system's success is a probability of catching a covert adversary rather than proof that nothing happened.

Penalise: giving the treaty objective as preventing superintelligence without pointing at Articles IV to VII; a chain with no section references; claiming the system specifies the response step.
feedback-instructions:: Name the weakest link in the learner's chain and give its section. If they claimed the system specifies what happens after a finding, correct that with Section 3.2.2 and Article VII.3. Then ask one question: at which link does the evidence stop being about a workload and start being about a party? No generic praise.

#### Question: Open
id:: e2907daf-68d9-43c7-9cf2-73c30ee38023
content:: **Question 2. Necessary assumptions**

Identify at least three assumptions that must be true for this combined approach to work. For each assumption:

- State it precisely;
- Explain why the design depends on it;
- Assess how plausible it is;
- Explain what happens if it is false.

Conclude by identifying the most decisive assumption and any dependencies among your assumptions.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Require at least three assumptions, each with all four parts, and a defended choice of the most decisive one. Roughly 25 points per well-developed assumption, 25 for the decisiveness argument and dependency map.

Assumptions actually available in the texts, any of which earns full credit when developed: (1) The perimeter assumption, Section 3.2, that the prover cannot communicate with a monitored pod except across a tapped and warden-sanitized frontend network link. The author's own footnote concedes that backend compute and storage fabrics are far higher-bandwidth, latency-sensitive and therefore harder and more expensive to tap, so incomplete coverage is the live risk. If false, the system is auditing a channel the violation does not use. (2) Commitment precedes challenge, Section 3.2.2, so the prover cannot know which evidence will be opened. If false, sampling stops being adversarially meaningful. (3) The covert-adversary model, Section 2b: cheating is deterred when detection likelihood times cost of being caught exceeds expected gain. The author states the failure mode himself in the attribution problem: if anomalies can be plausibly waved off as malfunction, deterrence weakens, and if every technical bug is treated as a violation the agreement collapses under false positives. (4) Physical security is a prerequisite, Section 1 property 3 and Section 2c requirement 6, since full anti-tamper assurance against a capable adversary is not expected to be solved. (5) Re-execution is reproducible, Section 3.2.2 step 4, which defers the determinism problem to Section 5.2.2; the neighbouring reproducibility claim in Section 3.1, that the captured bitstream can be reproduced rather than stored, is footnoted to soon-to-be-published research on bitwise-reproducible Ethernet frames, and the learner should notice that this is an unpublished citation. (6) On the treaty side, that consolidation actually succeeds: Article V.3 requires each Party to locate, inventory and consolidate all covered chip clusters within 120 days, and Article V.2 permits sub-threshold holdings outside declared facilities provided they are not aggregated, networked or rotated among sites. Everything the verification system does is conditional on the cluster being inside a declared facility in the first place.

Most decisive: assumption 1 or assumption 3 are both defensible as the load-bearing one, and either earns full credit when argued. Give credit for a genuine dependency claim, for example that assumption 3 presupposes 5, since a covert adversary is only deterred if a mismatch can be attributed rather than dismissed.

Penalise: assumptions stated without a section reference; assumptions that are really restatements of the system's goals; an answer that names three assumptions but assesses plausibility for none.
feedback-instructions:: Name the assumption whose failure case is least developed and say concretely what would happen if it were false, using the section. If the learner did not reach either the perimeter assumption or the covert-adversary assumption, introduce whichever they missed and say why it is a candidate for most decisive. Then ask one question: which of their assumptions is the treaty, rather than the architecture, responsible for making true? No generic praise.

#### Question: Open
id:: fa9d3436-5b4b-4d3f-a586-6461691b780c
content:: **Question 3. Coverage of Articles IV to VII**

For each article, classify the verification system's coverage as substantial, partial, or not provided, and justify your classification:

- Article IV, restrictions on AI training;
- Article V, consolidation and monitoring of AI chips;
- Article VI, monitoring production, sale, and transfer of AI chips;
- Article VII, verification of chip use.

Identify which obligations could generate usable evidence through this system, and which would still require inventories, inspections, supply-chain controls, legal authority, intelligence, or other institutions.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: This is the spine of the review. Score 25 per article, and grade the justification rather than the label.

Each article below lists the labels that can earn full marks. Grade against those sets and nothing else: a label inside its set is never penalised for being the less expected of the two, and a label outside it is wrong however well written.

Article VII. Acceptable: substantial, or partial when the answer defendsit,  for example substantial for the chip use verification of VII.1 but partial for Article VII taken whole, because VII.3's remedy and VII.5's differentiated protocols are institutional rather than evidential. Not provided is wrong.

Which paragraph of VII.1 the architecture implements is a judgement neither source makes. Cankaya's paper does not cite the draft agreement, and the agreement was published months before the architecture. What follows is this course's reading, not a finding of either text, so a learner who argues a different mapping from the same paragraphs is doing the exercise correctly rather than getting it wrong.

Our reading is that VII.1(e) and VII.1(f) are the closest fit. VII.1(e), declaration of the workloads and operations of chips by the CCC operator, is what the manifest does: Section 3.1 describes it as the prover's claims about what the ML servers were used for and how captured traffic maps to those claims. VII.1(f), rerunning of declared workloads coordinated by the CTB to confirm fidelity of declarations, is the re-execution step in Section 3.2.2, arrived at independently. Full credit for an answer that reaches that pairing and argues it.

Equal credit for VII.1(c), measurements of power, thermal, and networking characteristics, which the paragraph itself glosses as off-chip monitoring mechanisms. The whole capture layer is off-chip network taps on the frontend link, fixed-function logic parsing only L2 to L4 structure and never interpreting payloads (Sections 3.1 and 3.2.1), so on the face of the paragraph this is an off-chip networking monitoring mechanism. The strongest form of the answer also meets the objection to itself: the drafters' own Precedent for Article VII reads off-chip monitoring as perimeter measurement giving some clues about operations from power draw, thermal emissions, and network bandwidth, while Section 2a asserts that aggregate properties of exactly that kind are insufficient and demands collision-resistant evidence of individual workloads. The taps are inside the letter of (c) and beyond what (c)'s drafting anticipated. Do not require the learner to choose one paragraph; the fullest answer uses all three, mapping capture onto (c) and the declare-then-rerun cycle onto (e) and (f).

Credit an answer that also notices VII.4's operating restrictions on interconnect bandwidth, FLOP rate, memory bandwidth and numerical precision as a different technique aimed at the same distinction between permitted inference and prohibited training, and VII.3 as the remedy the architecture does not supply.

Article IV. Acceptable: partial. Both substantial and not provided are wrong. The system can bear on whether a declared run was what it was declared to be, and IV.2(a) requires training code, data and a FLOP estimate that a workload record could be checked against. It does not itself establish cumulative FLOP against the Strict Threshold in IV.1, and IV.2(b)'s requirement of written approval from US and PRC inspectors physically present at the facility, and IV.5's technique whitelist, are procedural and definitional rather than evidential.

Article V. Acceptable: not provided, or partial when the answer confines the partial to a narrow reading and says which reading. Substantial is wrong. The system presupposes a monitored facility. It cannot locate or inventory clusters (V.3), produce or check a register of locations, quantities, chip types, serial identifiers and interconnects (V.5), observe transfers under advance notice (V.6), or certify destruction (V.7). Reward explicitly the point that a mechanism installed only in declared facilities cannot by itself show that no undeclared cluster exists.

Article VI. Acceptable: not provided, or partial when the answer names a specific paragraph of VI that evidence from this system bears on. Substantial is wrong. Fabrication, HBM and logic production, testing, packaging, assembly, sale, transfer and installation (VI.1(b)), the production halt for unmonitorable facilities (VI.2), the transfer authorization presumptions (VI.4(a) to (c)) and the production caps (VI.7) are supply-chain and legal instruments. No evidence from network traffic inside a data centre speaks to them.

Penalise heavily: classifying V or VI as substantially covered; classifying IV or VII as not provided; any classification with no paragraph citation. Do not penalise a partial for IV or VII that is argued from the paragraphs. Reward an answer that says explicitly which institution has to carry each uncovered obligation.
feedback-instructions:: State which of the four classifications is least defensible and why, citing the paragraph. If the learner cited no paragraph of VII.1 at all, name (c), (e) and (f) as the three candidates and ask which they would defend. If they did map the architecture onto one of those paragraphs and argued it, accept the mapping and say what the strongest objection to it would be, rather than steering them to a different paragraph. Then ask one question: if you had to make the system cover one more article, which paragraph would you attack first, and with what mechanism? No generic praise.

#### Question: Open
id:: 35aca165-0ea2-4d42-9903-184aaff4c6a7
content:: **Question 4. Technical and operational feasibility**

Could the proposed system operate at the scale and level of assurance the treaty requires: yes, only under stated conditions, or no?

Consider network taps, commitments, sampling, challenge procedures, workload reconstruction or re-execution, physical security, redundancy, retrofitting, confidentiality, false positives and false negatives, attribution, cost, and scale. State the conditions required for your conclusion, or the changes needed to make the design feasible.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Award for a defended verdict, 20, and for the specific constraints handled, 80. The texts supply the numbers and the constraints; an answer that argues feasibility in the abstract should not score well.

Constraints available: Section 2c requirement 2 sets the cost target below 10 percent and ideally below 1 percent of the monitored hardware, and requires that the verification system not lower the facility's existing security standard, and that deployment time be measured in weeks or months rather than years. Requirement 3 states that millions of workloads will be screened daily even with sparse random sampling, which is the scale claim the automation argument rests on. Section 3.1 fixes the taps as fixed-function logic parsing only L2 to L4 structure and never interpreting L7 payloads, with reassembly deferred to the evaluation environment, and requires the bitstream to be either fully reproducible or stored. The reproducibility claim is footnoted to soon-to-be-published research. Section 3.2's footnote concedes the backend fabric is harder and more expensive to tap. Section 2c requirement 5 asks for redundant minimal monitors from different supply chains; requirement 6 concedes that physical monitoring remains necessary because anti-tamper assurance against a capable adversary is unresolved. Section 2b supplies the false-positive problem directly: a failed hash does not come with a label saying whether it was evasion, a cosmic-ray bit flip or an evaluation edge case, so the parties need testing, known error rates and a pre-agreed escalation procedure that terminates in attribution.

The treaty side of the scale question is Article V.1, which places every cluster above 16 H100-equivalents inside a declared facility, and V.1(b), which asks that a verification team be able to reach any covered cluster from an international airport within twelve hours. A strong answer notices that this is a large and mostly unremarkable population of facilities, not a handful of frontier sites. Article VII.3 gives the consequence of infeasibility: the hardware is powered off and its non-operation verified.

Verdicts of "only under stated conditions" and "no" are both defensible. An unqualified yes needs an argument against the author's own hedges. Penalise answers that ignore cost, or that treat re-execution as solved.
feedback-instructions:: Name the constraint the learner handled least well and give its section. If they treated re-execution or the tap perimeter as settled, say so and point at the footnotes. Then ask one question: what would you need to see measured in a pilot before you would move your verdict one step toward yes? No generic praise.

#### Question: Open
id:: f371a329-0b0f-4b31-bfe0-e380f7474363
content:: **Question 5. Implementation problems, loopholes, and responsibility**

Identify the major implementation problems and select the most serious one. Then develop at least two important loopholes or evasion pathways. For each pathway, explain:

- The actor and incentive;
- The sequence of actions;
- The weakness that enables it;
- Its likely impact and detectability;
- Who is responsible for prevention, detection, investigation, and remedy;
- Whether those defenders have the authority, information, incentive, and capacity to respond.

Prioritize the pathways. Propose one mitigation for the most serious pathway, and identify the new cost, risk, objection, or residual loophole the mitigation creates.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Require at least two pathways with all six elements, a priority ordering, and a mitigation whose second-order cost is named. Roughly 35 per pathway and 30 for the mitigation and its cost.

Pathways the texts support: the untapped backend fabric, Section 3.2 footnote, where a violation runs on links that produce no commitments; a misleading manifest, Section 3.1, which cannot corrupt the evidence but does shape which challenges are meaningful, so it degrades the value of sampling rather than defeating a check; sub-threshold holdings under Article V.2, where the treaty forbids aggregating, networking or rotating them among sites but relies on Parties making reasonable efforts to monitor sale and aggregation; carveouts under Article IV.4, which may permit runs above the Strict Threshold with CTB oversight; the AI Technique Whitelist under IV.5 as a definitional boundary that a research programme can be steered around; transfers to non-Parties under VI.4(c), which carry only a presumption of denial; and attacking the verification system itself, Section 2b, where the author notes that a malicious prover must both disable the monitors and make them forge plausible outputs, since the verifier would otherwise notice missing commitments.

Responsibility. Credit specificity: the CTB determines and updates verification methods under VII.1 and Article III; inspectors from the US and PRC must be physically present and give written approval for monitored runs under IV.2(b); the Executive Council can cap production under VI.7; Parties themselves must monitor sale and aggregation under V.2. The honest finding for several pathways is that the defender with the information is not the defender with the authority.

Penalise: pathways with no named actor or no sequence; a mitigation with no second-order cost, which is the part of the question most often skipped; treating the manifest as a hole in the evidence rather than as a hole in the sampling.
feedback-instructions:: Name the pathway that is least developed and say which of the six elements it is missing. If the learner's mitigation has no stated cost, supply the obvious one and say why naming it matters. Then ask one question: which of your pathways would survive a doubling of the sampling rate? No generic praise.

#### Question: Open
id:: 2ff754cc-cb85-4db1-91be-f26a8beb04bd
content:: **Question 6. Low trust, confidentiality, incentives, and fairness**

Explain how the design responds to both a potentially dishonest facility operator or state and a potentially intrusive or dishonest verifier. Does it protect sensitive model, training, commercial, and national-security information while still producing credible evidence?

Identify who receives assurance, who bears monitoring or disclosure burdens, and who controls the evidence. Assess whether this distribution is justified and whether the affected actors have incentives to participate and comply.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Score two-sidedness 40, the confidentiality machinery 30, and the distribution and incentives judgment 30.

Two-sidedness is explicit in Section 2b: the malicious prover aims to covertly break the rules, and the malicious verifier is assumed to be a colluding pact of a government and its domestic companies aiming to exfiltrate the prover's weights, code and training data. An answer that treats only the dishonest prover has missed the paper's central symmetry claim, that verification succeeds only if it constrains both parties. Credit the specific verifier-side analysis: exfiltration would have to run through the split fiber link, through side channels crossing the facility boundary, or through compromised inspectors and guards, and the paper's countermeasure for the last is inspection teams of diverse backgrounds keeping watch on each other.

Confidentiality machinery: Section 1 property 1, confidential data does not leave the monitored facility, not even in encrypted form; only commitments go to the verifier, and challenged plaintext enters an auditing environment inside the prover's own facility (Section 3.2.2); disclosure is minimal and pre-agreed by default, and points at suspicious hashes only when there is an issue.

The treaty half of the same question is where most answers are thin, so reward it: Article IV.2(a) gives CTB staff supervised access to all training code and data, with access logging appropriate to sensitivity and protections against duplication or unauthorized disclosure, and makes insufficient access grounds for denying the run; IV.2(c) forbids inspectors from removing storage devices or data from the facility; VII.5 and VII.5(a) allow differentiated verification by likelihood of AI use and by national-security sensitivity, with more automated methods and less physical foreign access at sensitive sites. The drafters name the fairness cost of that themselves in their notes: differentiated protocols might hurt the viability of the agreement if they are seen as unfair.

Distribution: the prover bears the monitoring burden and holds the plaintext; the verifier receives assurance and holds commitments; under the treaty both parties are provers and verifiers to each other, which is the argument that the distribution is symmetric. Credit an answer that questions whether it is symmetric in practice, given asymmetric fleets and asymmetric sensitivity.
feedback-instructions:: If the learner analysed only the dishonest prover, say so first, because the two-sided threat model is the claim the paper rests on. Name one treaty paragraph on confidentiality they did not use. Then ask one question: which actor in this arrangement has the weakest incentive to participate, and what would you offer them? No generic praise.

#### Question: Open
id:: ad3bda06-d407-4557-900d-90ad8ac603af
content:: **Question 7. Coherence and logic**

Is the combined design coherent, partly coherent, or incoherent? Reconstruct its strongest causal inference and identify its most important logical or evidentiary gaps.

In particular, test whether evidence about workloads inside a monitored facility is sufficient to establish treaty compliance concerning total compute, prohibited purpose, chip location, chip production and transfer, attribution, and enforcement.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Award 30 for the reconstructed inference and 70 for the six-way test, roughly 12 each.

The strongest causal inference is the commitment-before-challenge structure plus re-execution: because the prover commits to evidence before knowing what will be opened, and because a challenged sample is re-executed rather than merely inspected, a false declaration turns into a mismatch rather than into a plausible story. Credit an answer that states it in that form and locates it in Sections 3.2.1 and 3.2.2.

The six-way test, with the answers the texts support: total compute, partial, since the evidence is per workload and inside the tapped perimeter, and the paper does not specify FLOP accounting against Article IV.1's thresholds; prohibited purpose, partial, since Section 3.2.2 step 5 screens for inference versus training, model whitelist and blacklisted use, but semantic purpose is the thing Section 3.1 concedes is hard to define programmatically; chip location, no, that is Article V; production and transfer, no, that is Article VI; attribution, no, and the paper says so, since Section 2b's attribution problem notes that a failed hash does not identify its cause and Section 3.2.2 treats investigation as out of scope; enforcement, no, that is Article VII.3 and the institutional machinery around it.

The most important gap a strong answer names: the system is coherent within its own scope and the incoherence, if any, is in treating it as an implementation of Articles IV to VII rather than of parts of VII and IV. Give credit for the observation that four of the six items above are outside the system by construction rather than by weakness.

Penalise: a verdict with no reconstruction; a six-way test that gives the same answer six times; claiming the system establishes attribution.
feedback-instructions:: Name the item in the six-way test the learner got least right and give the section or paragraph that settles it. Then ask one question: if only one of the four uncovered items were fixed by a different mechanism, which would raise the credibility of the whole regime most? No generic praise.

#### Question: Open
id:: 961cdff0-9f68-4c2d-a808-c3a4be48d224
content:: **Question 8. Authors, affiliation, and standpoint**

Identify the authors and institutional affiliation of both texts. Explain how the authors' technical-governance and catastrophic-risk standpoint may have shaped one specific design choice, assumption, priority, or omission.

Identify one materially relevant perspective missing from the assigned reading and explain how including it might change the analysis. Affiliation alone is not evidence that a claim is false.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Score identification 25, the standpoint-to-design-choice link 45, the missing perspective 30.

Identification, checkable in the texts: the agreement is by Aaron Scher, David Abecassis, Peter Barnett and Brian Abeyta of the Machine Intelligence Research Institute Technical Governance Team; the system overview is by Naci Cankaya of the same team. Award a bonus mention in feedback, not in the score, if the learner notices that the two texts are not independent: Cankaya's opening thanks Aaron Scher, Mauricio Baker and Jonathan Ng for feedback on version 0.1, so the architecture was reviewed by one of the treaty's own authors.

The standpoint link must be to one specific choice, not to a general orientation. Strong candidates: the Strict Threshold in Article IV.1 is set at a level the drafters' own notes say is slightly below that used to train models near the state of the art as of August 2025, which only makes sense if the premise is catastrophic risk rather than proportionate regulation; Cankaya's insistence in Section 2a on evidence that can uniquely identify every forward pass, which he defends on the grounds that it lets you screen for any governance objective and which he himself flags as possibly trying too much; the choice in Section 4's opening to de-prioritize mutually trusted silicon entirely; and the drafters' own list of tradeoffs in their introduction, which concedes that the agreement forgoes beneficial capabilities, creates some pathways for authoritarian risk, cedes the US technological lead and risks leaking sensitive information through verification. That an author names his own worst case is evidence about standpoint too.

Missing perspectives that earn credit when developed: commercial cloud operators and their customers, who bear the retrofit and the disclosure burden but are not parties; states other than the US and China, which appear mainly as jurisdictions to be brought in; privacy and data-protection regulators; hardware vendors, who under Article VI.2 face production halts; and the security researchers whose objections Cankaya is explicitly soliciting rather than answering.

Penalise: treating MIRI affiliation as itself an argument against the proposals, which the question rules out; a missing perspective named but not connected to a change in the analysis.
feedback-instructions:: Say whether the standpoint claim was tied to a specific design choice or left general, and if general, give one of the specific candidates. Mention the acknowledgements point if the learner missed it, since two texts by the same team, one reviewed by the other's author, are weaker corroboration of each other than they first appear. Then ask one question: which missing perspective would be most likely to change a paragraph rather than a tone? No generic praise.

#### Question: Open
id:: d3bbd3f3-0331-4edf-a9fe-bc512ab930f9
content:: **Question 9. Factual, theoretical, or technical accuracy**

Identify one important claim or assumption in the assigned reading that may be false, overstated, contested, or insufficiently supported. Provide its exact location, classify the issue accurately, and test it using a reliable external source or a complete technical argument.

If you find no demonstrable error, identify the strongest candidate claim, explain what evidence would be needed to verify it, and state the implication of continued uncertainty.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: Four parts, 25 each: exact location, accurate classification, a real test, and a statement of what evidence would settle it.

Candidate claims that are genuinely testable and are in the assigned range: the cost target in Section 2c requirement 2, that retrofit overhead should be below 10 percent and ideally below 1 percent of the monitored hardware; the scale claim in requirement 3, that millions of workloads will be screened daily even with sparse sampling; the reproducibility footnote in Section 3.1, which supports bitwise-reproducible Ethernet frames by citing research described only as soon to be published, which is an unresolvable citation and a strong answer; the transitivity claim in Section 2b, that a system able to detect whitelisted models run for blacklisted uses can also detect inference of non-whitelisted models and covert training, which the author himself footnotes as conditional on re-execution; on the treaty side, the notes to Article V that a 10^22 FLOP training run on 16 H100s would take around one week (the drafters say 7.3 days at FP8 and 50 percent utilization), the parenthetical in Article V.1 that 16 H100s cost around 500,000 dollars in 2025, the estimate that between 50 and 100 models were trained above 10^24 FLOP as of mid-2025, and the twelve-hour airport accessibility criterion in V.1(b).

A real test means an arithmetic check the learner performs, or a linked external source, not an assertion that the claim seems high. The FLOP and cost claims are arithmetic and should be checked as arithmetic. Give full credit for a well-argued conclusion that the claim survives the test, provided the test was actually run and the confirming or disconfirming evidence is named.

Penalise: a claim with no location; classification that does not match the claim, for example calling an arithmetic estimate contested; a test that only restates the source; picking a claim from outside the assigned articles and sections without saying so.
feedback-instructions:: Say whether the test was performed or merely described. If the learner chose a claim and then argued about it without an external source or a calculation, name what the missing check would have been. Then ask one question: if this claim were wrong by a factor of ten, which of the design's other commitments would have to change? No generic praise.

#### Question: Open
id:: 69482580-7cb1-4162-a754-90b33e7aa74c
content:: **Question 10. Overall judgment and redesign**

Does the low-trust verification system make Articles IV to VII meaningfully more verifiable? Recommend adopt, pilot, redesign, or reject as the next step.

Support your judgment with the system's strongest feature and its most consequential unresolved weakness. Propose one concrete revision informed by a course concept, and explain the revision's second-order cost, risk, political objection, or residual loophole.
placeholder:: Cite the treaty by article and paragraph, the system overview by section.
assessment-instructions:: This is the question the other nine build to, but you are grading this response on its own: you do not have the learner's answers to Questions 1 to 9, so judge only what is written here and never assume what they said earlier. Score the recommendation and its support 40, the revision 35, and the second-order cost 25.

A recommendation about Articles IV to VII rests on a coverage judgment, so this answer has to carry its own. Require it to state, here, which of Articles IV to VII it treats as covered and which as not, and then to recommend something that judgment supports. An answer that states a coverage position and follows it, for example that the architecture reaches chip use verification but not Articles V and VI, therefore pilot rather than adopt, has done what is asked. Take up to half of the first 40 from an answer that recommends with no coverage position stated anywhere in it, because the recommendation then has no stated basis. Take most of the first 40 from an answer that contradicts itself: one that calls the system a complete implementation of Articles IV to VII while elsewhere in the same answer conceding that chip location or the supply chain is untouched, or one that states a coverage position and then recommends something that position does not support.

Pilot and redesign sit most naturally with the source, since Section 1 describes the document as a working draft published to elicit red-teaming before laboratory deployment; adopt is defensible only for the narrow claim about whichever paragraphs of Article VII.1 the answer argues the architecture reaches; reject needs an argument that the strongest feature is not worth its cost.

Strongest feature, credited when specific: commitment before challenge; the separation of capture from evaluation, which allows historical records to be re-examined with better analysis later so that an evader must anticipate future detectors; the elimination of mutually trusted silicon in favour of redundant unilaterally trusted devices; keeping plaintext inside the facility.

Most consequential weakness, credited when specific: the untapped backend fabric; the attribution problem, since a mismatch does not identify its cause and the escalation procedure is left to the parties; scope, since the system does not touch Articles V and VI.

The revision must use a concept from this course, not a generic engineering suggestion. Good examples: applying the Swiss-cheese principle from the second lens of this module by pairing workload evidence with a layer that fails differently, such as power or procurement records, so the holes do not line up; using the ten-route taxonomy to name which routes the revision closes and which it leaves; using the actor map from Module 1 to say who would have to hold the new evidence. The second-order cost must be named concretely, for example that adding a second evidence layer raises the disclosure surface the paper's confidentiality property was built to minimise.

Penalise: a recommendation with no strongest feature or no weakness; a revision with no named cost; a recommendation that states no coverage position; a recommendation that contradicts a coverage position stated elsewhere in the same answer.
feedback-instructions:: You have this answer only, not the learner's earlier ones, so speak only about what is in front of you. First, say whether the answer states the coverage position its recommendation rests on. If it does not, name that gap first, because a recommendation with no stated coverage basis is not reviewable by a panel. If it states one and then recommends something that position does not support, quote the two halves back and say plainly that they do not agree. Name the weaker of the strongest-feature and weakness pair. If the second-order cost is missing, supply the obvious one for their revision and explain why the question asks for it. Then close: state whether this review would be usable by the panel as written, and what one change would make it usable. No generic praise.

#### Text
content::
\## Submission standard

A strong review will fairly reconstruct both texts, distinguish a verification subsystem from the complete treaty regime, trace incentives and responsibilities, develop concrete failure pathways, and make a conditional recommendation supported by evidence.

\## Section B: the taxonomy revisited

You have now tried to construct and detect an evasion scheme. Return to the taxonomy from the previous lens and add judgment. The scores below are relative, conditional assessments, not measured probabilities. They depend on the agreement, actor, hardware fleet, jurisdiction, access rights, and verification architecture.

Scoring: 1 = very low or weak; 2 = low; 3 = moderate; 4 = high; 5 = very high. For verification effectiveness, a higher score is better for the verifier.

Two things to hold while you read the routes below. The scores synthesize the sources cited at the end of this lens together with the course's own judgment; they are not direct findings of any single paper, and several of those sources are preprints that have not necessarily completed peer review. And where a route cites a criminal case, charging documents are allegations: defendants are presumed innocent unless and until guilt is established in court.

\### Repurpose declared infrastructure

| Technical feasibility for evader | Political and organizational feasibility | Verification effectiveness | Durability and harm |
| --- | --- | --- | --- |
| **4/5 High.** The hardware, staff, and site already exist. | **4/5 High.** A small number of authorized insiders may be enough. | **3/5 Moderate.** Logs and telemetry help, but purpose and intent are difficult to infer. | **5/5 Very high.** Standing capacity can support repeated activity. |

Often the most realistic route for an actor that already controls major compute. Legitimate activity provides cover: training can be labeled as inference, or prohibited capability work as safety or maintenance. Broad workload telemetry can produce useful signals, but proving the exact research purpose requires clear rules plus access to raw scheduler records, code, data, checkpoints, and personnel evidence.

*Who can change the balance:* developers; cloud providers; national regulators; inspectors; hardware and standards bodies.

\### Steal or copy model weights

| Technical feasibility for evader | Political and organizational feasibility | Verification effectiveness | Durability and harm |
| --- | --- | --- | --- |
| **3/5 Moderate.** Requires insider access or a serious cyber compromise. | **3/5 Moderate.** Can be done by a small team, but access and confidentiality are demanding. | **2/5 Low.** There may be no new large training signal. | **5/5 Very high.** One successful copy can be duplicated and reused. |

Weight theft changes the verification problem: the actor may acquire a powerful model without recreating its original training run. Access logs, segmentation, data-loss controls, and human reporting can help, but attribution and proof of what was copied are difficult. Compression research may reduce exfiltration time, but exfiltration remains a multistep attack. A compute-only agreement does not close this route.

*Who can change the balance:* frontier developers; cloud providers; security teams; national regulators; law enforcement.

\### Split training across sites

| Technical feasibility for evader | Political and organizational feasibility | Verification effectiveness | Durability and harm |
| --- | --- | --- | --- |
| **2/5 Low today.** Low-communication methods are improving, but frontier-scale cases remain extrapolative. | **2/5 Low.** Many sites, operators, and coordination points increase exposure. | **2/5 Low.** Single-site thresholds and local power signals may miss the whole operation. | **3/5 Moderate.** Repeatable in principle, but inefficient and operationally fragile. |

Recent work makes it unsafe to assume that all frontier training must occur inside one tightly connected facility. However, the largest governance-relevant scenarios are modeled rather than directly demonstrated. Distribution reduces the value of site-level thresholds while increasing procurement, accounting, staffing, networking, and whistleblower surfaces. Treat this as an emerging and uncertain route, not a solved capability.

*Who can change the balance:* treaty designers; chip and cloud regulators; intelligence agencies; inspectors; hardware owners.

\### Falsify declarations or provenance

| Technical feasibility for evader | Political and organizational feasibility | Verification effectiveness | Durability and harm |
| --- | --- | --- | --- |
| **5/5 Very high.** Documents and curated logs are easy to alter when the actor controls them. | **4/5 High.** Requires control of records and cooperation or silence from relevant staff. | **3/5 Moderate.** Independent records and cross-checks can expose contradictions. | **3/5 Moderate.** One false record may cover one run; a captured system can conceal repeated activity. |

False reporting is usually a supporting tactic rather than a complete development strategy. It becomes less effective when records are generated automatically, preserved outside the actor's control, and compared with procurement, power, cloud, chip, code, checkpoint, and human evidence. Verification must test both whether declared activity occurred as claimed and whether important activity was omitted.

*Who can change the balance:* cloud and hardware providers; developers; auditors; inspectors; regulators.

\### Distill or extract capability

| Technical feasibility for evader | Political and organizational feasibility | Verification effectiveness | Durability and harm |
| --- | --- | --- | --- |
| **3/5 Moderate.** Depends on model access, query budget, data, student compute, and output richness. | **4/5 High.** May require no insider and can use proxy accounts or intermediaries. | **3/5 Moderate.** Providers can monitor access, but defenses are emerging and threat-model dependent. | **3/5 Moderate.** A student model can spread, but may not reproduce all teacher capabilities. |

Distillation is not the same as weight theft. It trains a new model to imitate behaviors exposed through an interface; it does not recover the teacher's exact parameters. Providers can use identity checks, rate limits, anomaly detection, output design, fingerprinting, or watermarking, but recent research finds that defense performance depends heavily on attacker assumptions and can trade off against service quality.

*Who can change the balance:* API providers; model developers; regulators; identity and payment providers.

\### Conceal the real actor

| Technical feasibility for evader | Political and organizational feasibility | Verification effectiveness | Durability and harm |
| --- | --- | --- | --- |
| **5/5 Very high.** Shell companies, nominees, and borrowed accounts are cheap to create. | **4/5 High.** Cross-border finance and ownership chains require coordination but are well established. | **3/5 Moderate.** Ownership, payment, address, communications, and logistics links can expose networks. | **4/5 High.** A proxy network can support repeated purchases and replace exposed entities. |

Proxy organizations are a high-feasibility enabling tactic, not a substitute for chips, power, engineering, or a viable workload. The A. Q. Khan network demonstrates how distributed intermediaries and front companies can route around supplier controls and exploit jurisdictional seams. Beneficial-ownership and reseller-chain analysis should therefore examine linked entities, not each nominal customer in isolation.

*Who can change the balance:* cloud and compute providers; exporters; financial institutions; corporate registries; regulators.

\### Divert controlled hardware

| Technical feasibility for evader | Political and organizational feasibility | Verification effectiveness | Durability and harm |
| --- | --- | --- | --- |
| **3/5 Moderate.** False documents and transshipment are feasible; covert frontier-scale accumulation is harder. | **3/5 Moderate.** Requires brokers, logistics, financing, and cross-border concealment. | **3/5 Moderate.** Customs, finance, supplier records, serials, and inspections create leads. | **4/5 High.** Individual shipments are episodic, but acquired hardware and networks can persist. |

Recent U.S. cases allege front companies, false paperwork, dummy servers, and transshipment through third countries to divert controlled AI hardware. These cases show realistic tactics, not proven prevalence; charging documents are allegations unless and until established in court. Acquiring chips is only one step: the actor must still power, cool, network, maintain, and use them.

*Who can change the balance:* vendors; distributors; customs; export-control agencies; freight and financial institutions.

{>>{"author":"Elias's AI","timestamp":1788521011728}@@Seven routes are scored here, and the taxonomy has ten. Missing: hide an undeclared cluster, attack or capture the verification system, and exploit a boundary in the rule. This gap is XLab's, not mine: their module-3 log lists it as an open item and records that the source outline has all ten with full scores and annotations, so the three are transcription owed rather than a content decision. I have not invented scores for them. Note that the last two of the three are the routes this lesson's own reading bears on most directly, since Article IV.5's technique whitelist and Section 2b's malicious prover are exactly those two arguments.<<}

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Scher, Aaron, David Abecassis, Peter Barnett, and Brian Abeyta. "An International Agreement to Prevent the Premature Creation of Artificial Superintelligence." *arXiv*, Nov. 2025. [arxiv.org](https://arxiv.org/abs/2511.10783)
*The draft agreement. Appendix A carries the treaty text; Articles IV to VII are the assigned range. Also published by the MIRI Technical Governance Team at [techgov.intelligence.org](https://techgov.intelligence.org/research/an-international-agreement-to-prevent-the-premature-creation-of-artificial-superintelligence).*

Cankaya, Naci. "A System Overview for Near-Term, Low-Trust AI Compute Verification." *Machine Intelligence Research Institute, Technical Governance Team*, June 2026. [techgov.intelligence.org](https://techgov.intelligence.org/research/a-system-overview-for-near-term-low-trust-ai-compute-verification)
*The architecture. Sections 1 to 3 are the assigned range. [PDF](https://intelligence.org/wp-content/uploads/A-system-overview-for-near-term-low-trust-AI-compute-verification.pdf).*

Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*The six-layer framework behind the repurposing and falsification rows in Section B.*

Rahman, Robi. "Does Distributed Training Undermine Compute Governance?" *arXiv*, May 2026. [arxiv.org](https://arxiv.org/abs/2605.29359)
*The source for the split-training row.*

Rahman, Robi, and Sabiha Tajdari. "Detecting Hidden ML Training With Zero-Overhead Telemetry." *arXiv*, June 2026. [arxiv.org](https://arxiv.org/abs/2606.19262)
*Cited with the repurposing row.*

Nevo, Sella, et al. *Securing AI Model Weights: Preventing Theft and Misuse of Frontier Models.* RAND Corporation, 2024. [rand.org](https://www.rand.org/pubs/research_reports/RRA2849-1.html)
*Cited with the weight-theft row.*

Brown, Davis, Juan-Pablo Rivera, Dan Hendrycks, et al. "Aggressive Compression Enables LLM Weight Theft." *arXiv*, Jan. 2026. [arxiv.org](https://arxiv.org/abs/2601.01296)
*The compression claim in the weight-theft row.*

Jiang, Bo. "DistillGuard: Evaluating Defenses Against LLM Knowledge Distillation." *arXiv*, Mar. 2026. [arxiv.org](https://arxiv.org/abs/2603.07835)
Libon, Lena, Pura Peetathawatchai, Michael Aerni, et al. "What Does It Mean to Break a Distillation Defense?" *arXiv*, June 2026. [arxiv.org](https://arxiv.org/abs/2606.25059)
*The two preprints behind the distillation row.*

Laufer, Michael. "A. Q. Khan Nuclear Chronology." *Carnegie Endowment for International Peace*, 7 Sept. 2005. [carnegieendowment.org](https://carnegieendowment.org/research/2005/09/a-q-khan-nuclear-chronology?lang=en)
International Institute for Strategic Studies. *Nuclear Black Markets: Pakistan, A. Q. Khan and the Rise of Proliferation Networks.* 2007.
Financial Action Task Force. *Guidance on Beneficial Ownership of Legal Persons.* 2023. [fatf-gafi.org](https://www.fatf-gafi.org/en/publications/Fatfrecommendations/Guidance-Beneficial-Ownership-Legal-Persons.html)
*The three sources behind the conceal-the-actor row.*

United States, Department of Justice. 2025 and 2026 charging announcements concerning alleged diversion of controlled AI chips through front companies, false documentation, and transshipment.
*Cited with the hardware-diversion row. XLab's registry carries no specific case URL for this entry.*

XLab. "3.2 Red-team / blue-team exercises." *Verification*, XLab, University of Chicago, 2026.
*The source lesson this page restores. Deleted upstream in commit a10955c and not currently live on aisafetytracks.com.*
:::{>>{"author":"Elias's AI","timestamp":1788521011728}@@Sources marked as preprints in XLab's own text have not necessarily completed peer review, and US charging documents are allegations. Every entry except the two primary sources is XLab's citation-registry record recovered from citations.json at a10955c^; I have not opened the arXiv preprints or the RAND report, so the descriptions of what each supports are XLab's claims about them and not mine. The DOJ entry names no case, which is how XLab left it.<<}
