---
id: '01252915-279a-48c6-b34a-97e51ce90203'
title: "4.1 Feasibility Judgments"
tldr: "Mechanisms age; the skill of judging them does not. Check the bets you placed in 2.0 against the reference map, learn the four questions that turn 'is it feasible?' into an answer, survive three drill benches, and write the defended-ranking memo your capstone will build on."
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. Sequence: (1) Intuition check: the reference map for the twelve mechanisms rated in 2.0 (a table of rung labels on four metrics plus one closed callout per mechanism with XLab's explanation and sources), then an open reflection on one mechanism where Module 2 evidence changed the learner's view. (2) Four metrics of feasibility, each a callout with a source excerpt and what to glean. (3) Drill bench: three benches (evasion, regime, position) as graded choice questions, one numeric estimate and one short open answer, each followed by a closed 'Why' callout; give the why after each answer, do not reveal it before. (4) The defended-ranking memo (about 900 words, peer reviewed) that 4.2 receives. When the learner disagrees with the reference map, ask which metric and what evidence would settle it rather than defending the map."
tags: [wip]
duration_minutes: 120
---
#### Text
content::
Verification is a rapidly changing field. Technological breakthroughs and geopolitical shifts alike significantly affect the relevance, feasibility, and effectiveness of different verification models. In this module, you will develop the future-proof skill of *discernment:* learning how to discern the relative feasibility of any mechanism using research strategies and critical analysis.

\## Intuition Check

#### Text
content::
:::callout {title="Reference map" tone="neutral" collapse="closed"}
Here is the set you sealed in 2.0, laid over the reference map — a judgment assembled from the module readings and current deployments. Disagreeing is fine; the useful question is which metric you disagree on, and what evidence would settle it.

Open your own ratings from [[../Lenses/XLab Verification - v-mechanism-effective|2.0 Place your bets]] beside this table and compare mechanism by mechanism.

| Mechanism | Technical feasibility | Political feasibility | Verification effectiveness | Durability |
|---|---|---|---|---|
| Chip identity and remote attestation | Buildable | Hard bargain | Solid | Decade-proof |
| On-chip compute metering | Prototype | Hard bargain | Solid | Ages slowly |
| Hardware licensing and remote authorization | Research | Non-starter | Capped | Ages slowly |
| Independent verification of training claims | Research | Rivals yield | Capped | Decaying |
| Cloud KYC and cluster registration | Running | Willing | Capped | Needs upkeep |
| Cloud workload monitoring and reporting | Buildable | Hard bargain | Capped | Needs upkeep |
| Satellite and infrastructure monitoring | Running | Piggybacks | Capped | Ages slowly |
| Chip supply-chain tracking | Buildable | Willing | Capped | Needs upkeep |
| National intelligence sharing | Running | Rivals yield | Capped | Ages slowly |
| Whistleblower channels and protections | Running | Hard bargain | Capped | Ages slowly |
| On-site and challenge inspections | Running | Rivals yield | Solid | Ages slowly |
| Privacy-preserving proofs | Not close | Willing | Capped | Needs upkeep |

Rungs, low to high. Technical feasibility: Not close, Research, Prototype, Buildable, Running. Political feasibility: Non-starter, Rivals yield, Hard bargain, Willing, Piggybacks. Verification effectiveness: Near nothing, Weak/narrow, Capped, Solid, Strong & broad. Durability: Leaking now, Decaying, Needs upkeep, Ages slowly, Decade-proof.
:::

Why the reference map lands where it does, mechanism by mechanism:

:::callout {title="Chip identity and remote attestation" tone="neutral" collapse="closed"}
*Every AI accelerator carries a unique cryptographic identity and can prove to a remote verifier what firmware it is running. This would let a treaty body maintain a registry of who holds which chips and confirm the hardware has not been tampered with.*

The primitives ship today on frontier accelerators; what is missing is the registry regime around them, so technical feasibility is high but not finished. Politics are middling: low intrusiveness helps, but rivals must still accept a shared registry. Effectiveness is the anchor case — attestation proves specific claims about specific hardware, and the concentrated supply chain means nearly every serious training effort passes through chips it can cover. Because it lives in silicon, it persists across model paradigms for the lifetime of the installed base.

Sources: Aarne, Fist & Withers, Secure, Governable Chips (CNAS, 2024); Kulp et al., Hardware-Enabled Governance Mechanisms (RAND working paper, 2024); NVIDIA H100 confidential-computing and attestation documentation (2023)
:::

:::callout {title="On-chip compute metering" tone="neutral" collapse="closed"}
*Chips measure how much computation they perform and what class of workload it is, then report the totals to a verifier. This could confirm that declared facilities stay under agreed compute thresholds.*

Metering firmware that survives a motivated operator with physical access does not exist yet — this is research, not rollout. Politically, continuous usage reporting cuts deeper than an inventory of chips, and the fight over reporting granularity would be real. If it runs, though, it delivers: aggregate compute totals bear directly on threshold claims across everyone who uses covered chips. Rooted in hardware, it ages well, with the caveat that algorithmic efficiency slowly weakens what any compute number means.

Sources: Shavit, What Does It Take to Catch a Chinchilla? (2023); Kulp et al., Hardware-Enabled Governance Mechanisms (RAND working paper, 2024)
:::

:::callout {title="Hardware licensing and remote authorization" tone="neutral" collapse="closed"}
*Chips require a cryptographic license, renewed on a schedule, to keep operating at full capability. An authority could suspend or revoke a violator's compute directly rather than relying on sanctions after the fact.*

Tamper-resistant remote authorization that survives a state-level adversary with physical possession is years out; flexHEG-style designs are still on paper. Politically it is the hardest sell on the list — an external off-switch for domestic compute. Effectiveness lands mid-scale because it is control more than evidence: a valid license says little about what actually ran, even though coverage through the chip base would be broad. Durability tracks the hardware it rides on, minus a permanent arms race over defeat devices.

Sources: Petrie, Heim et al., Interim Report: Mechanisms for Flexible Hardware-Enabled Guarantees (2024); Aarne, Fist & Withers, Secure, Governable Chips (CNAS, 2024); Wasil et al., Verification Methods for International AI Agreements (2024)
:::

:::callout {title="Independent verification of training claims" tone="neutral" collapse="closed"}
*Developers preserve checkpoints and training records, and verifiers recompute randomly chosen segments of the run on their own cluster. A match supports the claim that the declared training run is what actually happened.*

Spoofed in the lab, expensive to recompute, and undemonstrated at frontier scale — early research. Politically it demands the crown jewels: checkpoints, data, and hyperparameters, though only for declared runs. Its effectiveness is capped by coverage, strong claims about runs someone chose to declare and silence about everyone else. It also decays fast: training techniques shift underneath it, and every shift reopens the spoofing question.

Sources: Jia et al., Proof-of-Learning: Definitions and Practice (2021); Zhang et al., Adversarial Examples for Proof-of-Learning (2022); Shavit, What Does It Take to Catch a Chinchilla? (2023)
:::

:::callout {title="Cloud KYC and cluster registration" tone="neutral" collapse="closed"}
*Cloud providers verify who their large customers really are, including beneficial owners behind reseller chains, and register large clusters and training runs with an authority. Frontier-scale compute becomes hard to rent anonymously.*

The high anchor for technical feasibility: identity, billing, and abuse infrastructure already run at scale, and the US has already moved through the 2023 executive order. Politics piggyback on domestic regulation of domestic firms. But identity is not activity — KYC narrows the suspect pool without establishing what anyone trained, and it sees only the cloud-hosted slice of the threat surface. Durability is middling: reseller chains and jurisdictional arbitrage adapt faster than rules do.

Sources: Egan & Heim, Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers (2023); US Executive Order 14110, IaaS KYC provisions (2023); US Commerce/BIS proposed rule on IaaS customer identification (2024)
:::

:::callout {title="Cloud workload monitoring and reporting" tone="neutral" collapse="closed"}
*Providers watch cluster allocation and utilization patterns, preserve logs and billing records, report suspicious use, and can suspend access. The provider becomes a standing observer of what its customers run.*

Providers already see allocation, utilization, and billing; classifying workloads reliably enough to flag a covert run is the unsolved part. Politically it is a standing window into customers' most sensitive operations — tolerable domestically, harder across borders. Effectiveness is capped twice: signatures are gameable, and self-hosted or non-signatory compute never appears in the logs. It also needs constant upkeep, because every shift in training practice re-opens the classification problem.

Sources: Heim, Fist, Egan et al., Governing Through the Cloud (2024); Wasil et al., Verification Methods for International AI Agreements (2024)
:::

:::callout {title="Satellite and infrastructure monitoring" tone="neutral" collapse="closed"}
*Remote sensing tracks data-center construction, power draw, and cooling infrastructure. Frontier-scale facilities have physical signatures that are difficult to hide from overhead collection.*

Mature, deployed, and consent-free: overhead collection is the easiest yes on the board, with sixty years of national-technical-means precedent behind it. What it delivers is bounded — it proves a facility exists and roughly what power it draws, for every actor on Earth, but says nothing about what runs inside. Coverage without depth caps effectiveness at the middle. Durability is decent while frontier compute stays physically enormous; efficiency gains and distributed training chip away at the signature.

Sources: Baker, Nuclear Arms Control Verification and Lessons for AI Treaties (2023); SALT II and New START national-technical-means and noninterference provisions; Wasil et al., Verification Methods for International AI Agreements (2024)
:::

:::callout {title="Chip supply-chain tracking" tone="neutral" collapse="closed"}
*Export records, customs data, and financial activity trace accelerators from fabrication to installation. Diversions and smuggling routes show up as gaps between where chips were sold and where they can be accounted for.*

Export licensing, customs data, and financial trails already track advanced chips; the machinery is real but leaky, with documented smuggling in the tens of thousands of units. The political high anchor lives here: reporting attached to export licenses that already operate. Effectiveness pairs broad coverage of who holds capability with weaker evidence about what they do with it. The decay vector is structural — smuggling networks adapt, and chip fabrication outside the control regime grows every year.

Sources: Grunewald, AI Chip Smuggling into China (IAPS, 2023); US BIS advanced-computing export controls (2022, updated 2023)
:::

:::callout {title="National intelligence sharing" tone="neutral" collapse="closed"}
*States pass leads from their own collection to an international verification body, the way national tips have pointed nuclear inspectors at undeclared facilities. The regime supplies the follow-up; the agencies supply the anomaly.*

Collection exists today and needs no invention. The politics of sharing are the bottleneck: sources and methods, selective cooperation, wildly unequal capacity. Effectiveness is the coverage mirror-image of the consensual mechanisms — it can see precisely the undeclared activity everything else misses, but it delivers leads, not proof. And it is durable the way espionage is durable: the tradecraft adapts alongside whatever it watches.

Sources: IAEA and UNSCOM experience with member-state information (Iraq, 1991 onward); Baker, Nuclear Arms Control Verification and Lessons for AI Treaties (2023)
:::

:::callout {title="Whistleblower channels and protections" tone="neutral" collapse="closed"}
*Secure reporting channels, anti-retaliation protections, and rewards give employees, contractors, and suppliers a path to report concealed activity. Insiders can see what no sensor reaches.*

Channels are trivial to build; the mechanism is law and institutions, not technology. Protections exist in some jurisdictions and stop at exactly the borders where they would matter most. A single insider can deliver the most incriminating evidence available — but sporadically, uncorroborated, and nothing guarantees an insider exists where you need one, which caps effectiveness. Durability is decent: as long as humans build these systems, some of them can talk.

Sources: A Right to Warn about Advanced Artificial Intelligence, open letter from AI-lab employees (2024); Wasil et al., Verification Methods for International AI Agreements (2024)
:::

:::callout {title="On-site and challenge inspections" tone="neutral" collapse="closed"}
*International inspectors visit declared facilities on a routine schedule and can demand short-notice access to suspect sites. Managed-access rules decide what inspectors may see and what stays shielded.*

The craft is proven and the institutions exist; nothing technical blocks it. Consent does: no major AI state currently accepts foreign inspectors inside frontier labs, and the CWC's challenge provision has never once been invoked. When inspectors do get in, effectiveness is high — direct observation resolves what remote evidence cannot, across declared and challenged sites alike. The regime decays politically rather than technically, one access fight at a time.

Sources: Chemical Weapons Convention managed-access and challenge-inspection provisions (OPCW); Wasil et al., Verification Methods for International AI Agreements (2024); Baker, Nuclear Arms Control Verification and Lessons for AI Treaties (2023)
:::

:::callout {title="Privacy-preserving proofs" tone="neutral" collapse="closed"}
*Zero-knowledge proofs and secure multiparty computation let a developer prove a claim about a model or training run without revealing weights, code, or data. Verification without disclosure, if the cryptography scales.*

The low anchor for technical feasibility: proving anything at frontier scale is orders of magnitude beyond today's cryptography, and fully homomorphic approaches are worse still. If that changed, the politics look comparatively good — this is the rare mechanism whose entire design goal is confidentiality. Effectiveness would be capped by scope: it proves exactly the claims parties agree to formalize, over runs they choose to prove, and nothing else. The cryptographic assumptions age well; the claim set needs renegotiating every time the paradigm moves.

Sources: Garg et al., Experimenting with Zero-Knowledge Proofs of Training (2023); Kang et al., zero-knowledge proofs for ML inference (2022); Wasil et al., Verification Methods for International AI Agreements (2024)
:::
{>>{"author":"Elias's AI","timestamp":1788016020463}@@XLab's mechanism-sort-reveal widget overlays the learner's sealed 2.0 ratings (browser localStorage) on this reference map and computes per-mechanism gaps ("Close call", "Near miss", "Big gap"). The learner-specific overlay cannot be reproduced; the reference map and XLab's explanations are reproduced verbatim from the widget data file.<<}

#### Question: Open
id:: bb06a146-287c-498d-bd22-b27545fa1c9e
content:: Return to your ranking from the beginning of the course. Choose one mechanism for which later evidence in Module 2 changed your view. Write brief answers to the following in your notebook:

- What heuristics did you initially use?
- What evidence changed your judgment?
- What question should you have asked earlier?

Pay attention to how your heuristics changed: where was your intuition accurate, and where was it off?
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
\## Four Metrics of Feasibility

“Is this mechanism feasible?” is usually too vague to answer beyond an initial intuition check, like you did in [[../Lenses/XLab Verification - v-mechanism-effective|2.0]].{>>{"author":"Elias's AI","timestamp":1788015963580}@@MDX says "1.0.2", which does not exist in XLab's curriculum; the intuition check (Place your bets) is the mechanism-sort widget in 2.0. Reported to Elias for XLab.<<} Feasibility depends on myriad factors, including what the mechanism must verify, whom it must cover, where it would operate, how soon it must be deployed, and what level of performance is required. A serious feasibility assessment should answer four connected questions, which you were introduced to at the beginning of Module 2:

:::callout {title="1. Technical Feasibility" tone="blue"}
Can the mechanism be built and operated at the required scale? Examine the maturity of its hardware and software, its error rates, cost, staffing needs, security, dependencies, and performance under realistic conditions. Keep the distinction between a promising component and a complete operational system. The existence of hardware attestation, for example, does not by itself prove that a full training claim can be reliably verified.

**Source:** Shavit (2023), [What does it take to catch a Chinchilla?](https://arxiv.org/abs/2303.11341) (arXiv:2303.11341)

**Excerpt (from the abstract):** “The system consists of interventions at three stages: (1) using on-chip firmware to occasionally save snapshots of the the neural network weights stored in device memory, in a form that an inspector could later retrieve; (2) saving sufficient information about each training run to prove to inspectors the details of the training run that had resulted in the snapshotted weights; and (3) monitoring the chip supply chain to ensure that no actor can avoid discovery by amassing a large quantity of un-tracked chips.”

**What you should glean:** The author must chain three subsystems together before the mechanism can operate. Count the parts that exist today and the parts that are only proposals. The firmware, the training log, and the supply-chain monitor are each a separate engineering project, so the full system is far less mature than its most mature part.
:::

:::callout {title="2. Political Feasibility" tone="purple"}
Whose cooperation is required, and how easy is it to get them to agree? A verification system may depend on legislators, regulators, laboratories, cloud providers, chipmakers, standards bodies, inspectors, foreign governments, and/or enforcement agencies. Identify who must authorize, build, operate, provide access, interpret findings, and act on them. Then identify which actor could block implementation, and why: consider the benefits actors might receive, the costs and risks they might bear, and available alternatives.

**Source:** Sheehan (Carnegie, Aug 2024), [China’s Views on AI Safety Are Changing—Quickly](https://carnegieendowment.org/research/2024/08/chinas-views-on-ai-safety-are-changing-quickly)

**Excerpt:** The July 2024 Third Plenum decision called on the government to “establish an AI safety supervision and regulation system”: the first major CCP policy document to call for oversight aimed at frontier AI risks.

**What you should glean:** One necessary actor put a new position into its most authoritative document type. This is direct data about political feasibility: a mechanism that needs the agreement of the Chinese government became easier to get in July 2024 than it was in 2023. Track the document type, not only the words, because a Plenum decision binds more actors than an op-ed does.
:::

:::callout {title="3. Verification Effectiveness" tone="green"}
Would the mechanism produce evidence that matters? Ask what claim the evidence would actually support, how direct it is, whether it has been tested against adaptive evasion, and which actors or activities remain outside its coverage. A deployable mechanism may still contribute little to detecting, deterring, or demonstrating compliance.

**Source:** Wasil, Reed, Miller & Barnett (2024), [Verification methods for international AI agreements](https://arxiv.org/abs/2408.16074) (arXiv:2408.16074)

**Excerpt (on data center inspections):** “Inspections can only be carried out with the agreement of the host nation, potentially allowing time for concealment of violations.”

**What you should glean:** The mechanism is fully buildable, but the evidence it produces is weak against an adaptive adversary. A clean inspection report only supports the claim “we found nothing at the declared site on the agreed day.” Ask what claim the evidence supports, not whether the mechanism can run.
:::

:::callout {title="4. Durability" tone="amber"}
Will the verification mechanism persist across technological and geopolitical change, or is it easily rendered obsolete by capability jumps or the decline of a fraught inter-country relationship? A fixed compute threshold is relatively fragile because improvements in algorithms can move dangerous capabilities below the regulated line. Chip-level logging or attestation may be more durable because it is anchored in physical infrastructure with slower turnover. Durability is therefore comparative: even hardware-based mechanisms require updating as chips, supply chains, and evasion strategies change.

**Source:** Hooker (2024), [On the Limitations of Compute Thresholds as a Governance Strategy](https://arxiv.org/html/2407.05694v1) (arXiv:2407.05694)

**Excerpt (from the abstract):** “A key conclusion of this essay is that compute thresholds, as currently implemented, are shortsighted and likely to fail to mitigate risk. The relationship between compute and risk is highly uncertain and rapidly changing. Relying upon compute thresholds overestimates our ability to predict what abilities emerge at different scales.”

**What you should glean:** The threshold decays because the quantity it measures and the risk it targets move apart over time. Ask this of each mechanism: which external change breaks the connection between what it measures and what the treaty cares about, and how fast does that change move? A mechanism with an update path survives; a fixed number does not.
:::

\## Drill Bench

The evasion, regime and position benches — module 3 and module 4, and the prep for the capstone. One step at a time: commit, read why, then Continue.

#### Text
content::
\### Evasion bench

Classify four schemes against the taxonomy, then survive the statistics trap. (~7 min)

#### Question: Choice
id:: b3bcff05-c09b-4801-9cf9-a1ba7c37869a
content:: A lab’s declared inference cluster shows training-shaped utilization: sustained all-to-all traffic in long nightly blocks, checkpoint-sized storage writes every few hours.

Which of the eight evasion buckets is this?
options::
- Proxy organizations
- Smuggled hardware
- Threshold gaming
- [x] Repurposed infrastructure
- Distributed training
shuffle:: true
feedback-instructions:: Explain: bucket 5, repurposed infrastructure, training disguised as inference on legitimately held compute. Detectability is its weak flank: workload labels are cheap to fake, but utilization shape is not, which is why the cloud layer's telemetry is the natural tripwire here. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Bucket 5, repurposed infrastructure — training disguised as inference on legitimately held compute. Detectability is its weak flank: workload labels are cheap to fake, but utilization shape is not, which is why the cloud layer’s telemetry is the natural tripwire here.
:::

#### Question: Choice
id:: 48ba02dd-3a2c-412e-8c4d-7b2c734cff27
content:: A subsidiary registered in a non-party state buys five thousand accelerators; its parent company is a treaty-bound lab. The chips never appear in the parent’s declarations.

Which bucket?
options::
- [x] Proxy organizations
- Weight exfiltration
- False reporting
- Tampering with verification mechanisms
- Threshold gaming
shuffle:: true
feedback-instructions:: Explain: bucket 1, proxy organizations, the Meridian pattern from the actor bench, now as a scheme: legal separation used to break the paper trail between buyer and beneficiary. The counter lives at the chokepoint (chip registries follow the silicon, not the org chart) plus beneficial-ownership analysis. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Bucket 1, proxy organizations — the Meridian pattern from the actor bench, now as a scheme: legal separation used to break the paper trail between buyer and beneficiary. The counter lives at the chokepoint (chip registries follow the silicon, not the org chart) plus beneficial-ownership analysis.
:::

#### Question: Choice
id:: a522340c-1f5d-4c65-884b-37740844ffdf
content:: Three sites in three jurisdictions each run training just below the notification threshold; the checkpoints are periodically merged.

Which bucket?
options::
- Smuggled hardware
- [x] Distributed training
- Repurposed infrastructure
- False reporting
- Proxy organizations
shuffle:: true
feedback-instructions:: Explain: bucket 8, distributed training, sub-threshold fragmentation. It attacks the aggregation rule, not the sensor: each site is individually legal. The lesson: thresholds need language about combined runs and affiliated entities, or arithmetic becomes a loophole. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Bucket 8, distributed training — sub-threshold fragmentation. It attacks the *aggregation rule*, not the sensor: each site is individually legal. Which is the lesson — thresholds need language about combined runs and affiliated entities, or arithmetic becomes a loophole.
:::

#### Question: Choice
id:: 0c314899-c2df-4cfe-8da1-a8d7f0965da7
content:: Extracted attestation keys are used to replay valid-looking quotes from a cluster whose actual firmware was replaced months ago.

Which bucket?
options::
- [x] Tampering with verification mechanisms
- Weight exfiltration
- Threshold gaming
- False reporting
- Smuggled hardware
shuffle:: true
feedback-instructions:: Explain: bucket 7, tampering, the scheme aimed at the regime's own instruments rather than at the underlying rule. Nastiest property: it converts a verification signal from evidence into disinformation, which is why key compromise procedures and cross-layer corroboration are regime-design requirements, not nice-to-haves. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Bucket 7, tampering — the scheme aimed at the regime’s own instruments rather than at the underlying rule. Nastiest property: it converts a verification signal from evidence into disinformation, which is why key compromise procedures and cross-layer corroboration are regime-design requirements, not nice-to-haves.
:::

#### Question: Choice
id:: 22b578ab-8f1b-4da7-8ce1-94ec70d04ecf
content:: Case: the treaty’s first monitoring year ends. Confirmed-violation findings are triple the pre-treaty estimate of covert activity. A columnist: “the treaty tripled cheating.” A minister proposes scrapping it.

Did covert activity necessarily increase?
options::
- Yes — findings tripled
- [x] No — the instrument changed; found violations and existing violations are different quantities
- Cannot say anything from these numbers
shuffle:: true
feedback-instructions:: Explain: no. Before the treaty there was no monitoring, so the baseline "estimate" counted a fraction of an invisible total. Findings measure detection times incidence; the treaty changed the first factor massively. If the learner chose "Cannot say anything", note that this overcorrects: the numbers do say something, they bound detection performance. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
No — before the treaty there was no monitoring, so the baseline “estimate” counted a fraction of an invisible total. Findings measure detection × incidence; the treaty changed the first factor massively. (Answer C overcorrects: the numbers do say something — they bound detection performance.)
:::

#### Question: Choice
id:: cbb77e16-57e8-4ed3-a8ca-45149fd1ba5b
content:: The classic case, one century older: when steel helmets replaced cloth caps in the First World War, field hospitals recorded MORE head wounds — because soldiers who previously died were now surviving into the statistics.

Name the shared error.
options::
- Base-rate neglect
- [x] A selection effect: the observation instrument changed, so the observed sample changed
- Sunk-cost reasoning
- Circular reasoning
shuffle:: true
feedback-instructions:: Explain: both stories move cases across a visibility boundary (dead to wounded, invisible to detected) and both invite blaming the instrument for what it newly reveals. Verification regimes face this politically every year one: rising findings will be spun as regime failure when they are the regime working. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Both stories move cases across a visibility boundary — dead→wounded, invisible→detected — and both invite blaming the instrument for what it newly reveals. Verification regimes face this politically every year one: rising findings will be spun as regime failure when they are the regime working. Brief accordingly.
:::

\### Regime bench

Extract what the memo actually claims, sort strong from weak, counter both kinds, price the stack. (~10 min)

MEMORANDUM — from the Deputy Minister for Strategy, re: the proposed verification regime. “(1) Every verification mechanism on offer can be defeated by a resourced adversary: attestation falls to physical access, proof-of-learning has been spoofed, customer vetting dissolves in reseller chains. (2) It follows that a regime stacked from such layers can be defeated too. (3) The BWC episode settles the politics: states will not accept intrusive verification — that protocol died, and so will this one. (4) And pause-grade inspection collides with legitimate secrecy: classified workloads, trade secrets, national-security systems. (5) Strategy should therefore preserve freedom of action and fund national capability instead.”

#### Question: Choice
id:: 65b5d768-2bda-4ea8-9715-f4e5141b9324
content:: Before judging a text, establish what it says. Mark every statement the memo actually asserts.
options::
- [x] Individual verification mechanisms can each be defeated by a resourced adversary.
- [x] A regime layered from defeatable mechanisms is itself defeatable.
- Independent layers multiply detection probability.
- [x] States will not accept intrusive verification; the BWC proves it.
- Verification technology will mature substantially within a decade.
- [x] Pause-grade inspection conflicts with legitimate secrecy.
- [x] The ministry should preserve freedom of action and fund national capability.
multi:: true
feedback-instructions:: Five statements are asserted (sentences 1 to 5 of the memo) and two are phantoms. "Independent layers multiply detection probability": the memo asserts the opposite; marking it means reading your rebuttal into the author's mouth, the extraction error the source round punishes hardest. "Verification technology will mature substantially within a decade": never addressed, the classic planted distractor. Name each item the learner got wrong and which sentence, if any, asserts it. Close with: extraction precedes evaluation; you cannot sort strong from weak until the claim list is the author's and not yours.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Extraction precedes evaluation: you cannot sort strong from weak until the claim list is the author’s and not yours. Five claims in, two phantoms out — now the sorting can start.

- Individual verification mechanisms can each be defeated by a resourced adversary. Asserted — sentence (1), with three supporting examples.
- A regime layered from defeatable mechanisms is itself defeatable. Asserted — sentence (2), flagged by its own “it follows”.
- Independent layers multiply detection probability. The memo asserts the OPPOSITE. Marking this means reading your rebuttal into the author’s mouth — the extraction error the source round punishes hardest.
- States will not accept intrusive verification; the BWC proves it. Asserted — sentence (3).
- Verification technology will mature substantially within a decade. Never addressed — plausible-sounding and absent, the classic planted distractor.
- Pause-grade inspection conflicts with legitimate secrecy. Asserted — sentence (4).
- The ministry should preserve freedom of action and fund national capability. Asserted — sentence (5), the memo’s recommendation.
:::

Sorting rule from the source pedagogy: strong arguments get engaged on the merits; weak ones get their flaw named. Both earn marks — mislabeling earns none.

#### Question: Choice
id:: 90ef49c3-e8e5-455f-98d8-843612be993b
content:: Memo sentence (1): “Every verification mechanism on offer can be defeated by a resourced adversary.”

Strong or weak?
options::
- [x] Strong — engage it
- Weak — name the flaw
feedback-instructions:: Explain: strong. The course itself teaches it: attestation breaks under physical access, PoL was spoofed, KYC dissolves in reseller chains. Concede the premise honestly; the regime's answer is layering, never mechanism-perfection. Steelmanning the opponent's true premises is what makes the eventual rebuttal land. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Strong — the course itself teaches it: attestation breaks under physical access, PoL was spoofed, KYC dissolves in reseller chains. Concede the premise honestly; the regime’s answer is layering, never mechanism-perfection. Steelmanning the opponent’s true premises is what makes the eventual rebuttal land.
:::

#### Question: Choice
id:: 092d5aa3-86c4-4f1f-8dcc-6a2c242718af
content:: Memo sentence (2): “It follows that a regime stacked from such layers can be defeated too.”

Strong or weak?
options::
- Strong — engage it
- [x] Weak — name the flaw
feedback-instructions:: Explain: weak, a composition fallacy. What is true of each layer separately is not true of the stack, provided the layers fail independently. Note the memo's own tell: "it follows" marks the exact joint where the inference breaks. The learner will price this fallacy in numbers two steps from now. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Weak — a composition fallacy: what is true of each layer separately is not true of the stack, *provided the layers fail independently*. Note the memo’s own tell — “it follows” marks the exact joint where the inference breaks. You will price this fallacy in numbers two steps from now.
:::

#### Question: Choice
id:: fbceaea3-3472-4e9b-bdf4-97fd391ed607
content:: Memo sentence (3): “The BWC episode settles the politics: states will not accept intrusive verification.”

Strong or weak?
options::
- Strong — engage it
- [x] Weak — name the flaw
feedback-instructions:: Explain: weak, generalizing from one failure while the counterexamples run seventy years: IAEA safeguards, CWC managed access, START inspections. The honest residue is real, though: the BWC case proves political acceptability is a design constraint, which is exactly how the spine teaches it. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Weak — generalizing from one failure while the counterexamples run seventy years: IAEA safeguards, CWC managed access, START inspections. The honest residue is real, though: the BWC case proves political acceptability is a design constraint, which is exactly how the spine teaches it.
:::

#### Question: Choice
id:: 03007ab7-3417-4f2f-bdf0-99ac8582e031
content:: Memo sentence (4): “Pause-grade inspection collides with legitimate secrecy — classified workloads, trade secrets, national-security systems.”

Strong or weak?
options::
- [x] Strong — engage it
- Weak — name the flaw
feedback-instructions:: Explain: strong. The secrets-and-people bench exists because this is true. The engagement: confidentiality-preserving verification (ZK proofs, attestation) where the technology exists, managed access where it does not yet. A reply that dismisses the secrecy concern loses the reader who most needs convincing. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Strong — the secrets-and-people bench exists because this is true. The engagement: confidentiality-preserving verification (ZK proofs, attestation) where the technology exists, managed access where it does not yet. A reply that dismisses the secrecy concern loses the reader who most needs convincing.
:::

Counterargument discipline, part two of the source format: for each argument, formulate the counter that MEETS it — not the author, not the vibe.

#### Question: Choice
id:: 0f617796-7c8e-403f-af0d-5fd413288a25
content:: Which counterargument actually meets memo sentence (2) — the stack-fails-too inference?
options::
- [x] Three independent layers each missing 30% of the time jointly miss ~3% of the time — composition flips the odds, provided failures are independent
- The Deputy Minister has no technical background in verification
- Verification also builds trust between rivals, which has diplomatic value
- Some verification mechanisms are in fact unbreakable
feedback-instructions:: Explain: only the first meets the inference where it lives, and carries its own scope condition. The second attacks the author (the position bench dissects that move), the third changes the subject, and the fourth concedes the memo's frame by defending a claim the course itself rejects. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Only the first meets the inference where it lives — and carries its own scope condition. The second attacks the author (the position bench dissects that move), the third changes the subject, and the fourth concedes the memo’s frame by defending a claim the course itself rejects.
:::

#### Question: Choice
id:: 879e9745-77e9-48cc-ba12-d8d3e528488b
content:: Which counterargument actually meets memo sentence (3) — the BWC-settles-the-politics claim?
options::
- [x] One dead protocol against seventy years of operating regimes — safeguards, CWC, START — is a sample of one, not a law; what the BWC proves is that acceptability is a design constraint
- The BWC failure was two decades ago; the politics have changed since
- Biology and AI are different technologies, so the case is irrelevant
- States that reject verification are simply acting in bad faith
feedback-instructions:: Explain: the first names the inferential flaw (overgeneralization) and salvages the argument's true residue, the strongest form of counterargument in the source rubric. The second asserts without showing, the third dodges the political claim it needs to answer, the fourth moralizes and concedes nothing. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The first names the inferential flaw (overgeneralization) AND salvages the argument’s true residue — the strongest form of counterargument in the source rubric. The second asserts without showing, the third dodges the political claim it needs to answer, the fourth moralizes and concedes nothing.
:::

The source tables demand counterarguments in the STRONG rows too — countering an argument you concede is sound is its own skill: you bound its scope, you never deny it.

#### Question: Choice
id:: 92561c92-604e-4afa-a297-8c3aa9a1d9e5
content:: Memo sentence (4) is strong — verification really does collide with legitimate secrecy. Which counter meets even a strong argument?
options::
- [x] Concede the collision, then bound it: confidentiality-preserving proofs where the technology exists, CWC-style managed access where it does not — the carve-out is a designed feature with seventy years of practice behind it
- Secrecy claims are usually pretexts for having something to hide
- Transparency simply matters more than secrecy
- Trade secrets have no protection in international law anyway
feedback-instructions:: Explain: concede-and-bound is the only move that survives contact with a true premise. The second option is the attribution reflex (the position bench dissects it), the third is a value assertion that persuades nobody who does not already agree, and the fourth is false, and silent about classified workloads, the collision's hardest case. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Concede-and-bound is the only move that survives contact with a true premise. The second option is the attribution reflex (the position bench dissects it), the third is a value assertion that persuades nobody who does not already agree, and the fourth is false — and silent about classified workloads, the collision’s hardest case.
:::

Now price the composition fallacy — computed, not chosen. Assume three independent evidence streams — hardware, intelligence, human — each with a 70% chance of catching a given covert program.

#### Question: FillBlank
id:: 42700410-921e-4f75-8268-bc5fd7939339
content:: What percentage of covert programs evades all three? Enter the number: {{number min 0 max 100 2.7}} %
assessment-instructions:: Reference answer 2.7 (0.3 × 0.3 × 0.3 = 0.027). Give 100 for any answer between 2 and 3.5 inclusive, which is the range XLab accepts. Give 50 for 0.027 or 0.03 (right computation, forgot to convert to percent). Give 0 otherwise.
feedback-instructions:: Explain: 0.3 × 0.3 × 0.3 = 0.027, so 2.7%. Each mediocre layer alone misses one time in three; the stack misses one in thirty-seven. The proviso is load-bearing: layers sharing a blind spot (all fed by the same declarations, say) are one layer wearing three uniforms; independence is a design requirement, not a free assumption. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
0.3 × 0.3 × 0.3 = 0.027 → 2.7%. Each mediocre layer alone misses one time in three; the stack misses one in thirty-seven. The proviso is load-bearing: layers sharing a blind spot (all fed by the same declarations, say) are one layer wearing three uniforms — independence is a design requirement, not a free assumption.
:::

\### Position bench

Critique vectors on a radical manifesto — all the rubric’s rows — then the prognostic analysis it never did, run on our own measure. (~9 min)

Movement one — the critique taxonomy. The Zero Hour Manifesto demands an immediate, unconditional, permanent global shutdown of all AI development; its author is a 22-year-old movement founder. Four critique lines from the public debate follow. Classify each: does it attack the SPEAKER (personal traits, hidden interests) or the ARGUMENT (premises, program)? Both kinds appear in every real debate — only one kind carries evidential weight.

#### Question: Choice
id:: cc362678-d543-4aab-b458-9c5db56fcfd8
content:: Critique line 1: “Twenty-two years old, never trained a model, never held a clearance — this is not someone who understands the systems she wants to shut down.”

Speaker-directed or argument-directed?
options::
- [x] Speaker-directed — personal characteristics
- Argument-directed — premises or program
feedback-instructions:: Explain: speaker-directed, age and credentials, the source rubric's first family (personal characteristics: age, education, temperament). Cataloguing it is worth marks; relying on it is not: a claim's truth does not vary with its speaker's CV, and the strongest version of her argument survives her entirely. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Speaker-directed: age and credentials — the source rubric’s first family (personal characteristics: age, education, temperament). Cataloguing it is worth marks; relying on it is not: a claim’s truth does not vary with its speaker’s CV, and the strongest version of her argument survives her entirely.
:::

#### Question: Choice
id:: d146fc3d-9143-4e43-9d76-33d508425485
content:: Critique line 2: “Follow the money — the movement’s donors hold short positions against AI companies. The manifesto is a trading strategy wearing a safety costume.”

Speaker-directed or argument-directed?
options::
- [x] Speaker-directed — attribution of hidden motives
- Argument-directed — premises or program
feedback-instructions:: Explain: speaker-directed, second family: attribution, the speaker as instrument of concealed interests, declared goals diverging from real ones. Rhetorically devastating, evidentially empty: motives predict why someone argues, never whether the argument holds. Flag it, name it, and return to the claims. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Speaker-directed, second family: attribution — the speaker as instrument of concealed interests, declared goals diverging from real ones. Rhetorically devastating, evidentially empty: motives predict WHY someone argues, never WHETHER the argument holds. Flag it, name it, and return to the claims.
:::

#### Question: Choice
id:: ef7fa9f1-ee5a-44d6-b872-cc7c73d14b55
content:: Critique line 3: “The manifesto treats catastrophe-absent-shutdown as certain. That axiom is contestable — and every demand downstream inherits its uncertainty.”

Speaker-directed or argument-directed?
options::
- Speaker-directed — attribution of hidden motives
- [x] Argument-directed — a contestable axiomatic premise
feedback-instructions:: Explain: argument-directed, the axiom family, the source rubric's "contestable foundational premises". This is the critique that does real work: it locates the load-bearing assumption and prices everything built on it. Note it applies symmetrically: the foundations' securitization case must survive the same probe. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Argument-directed: the axiom family — the source rubric’s “contestable foundational premises”. This is the critique that does real work: it locates the load-bearing assumption and prices everything built on it. Note it applies symmetrically — the foundations’ securitization case must survive the same probe.
:::

#### Question: Choice
id:: 2d4883b3-93c3-4c1f-b7c7-45757aedce89
content:: Critique line 4: “It demands the terminal measure immediately, offers no transition plan, and never once analyzes what its own success would cause.”

Speaker-directed or argument-directed?
options::
- Speaker-directed — personal characteristics
- [x] Argument-directed — non-constructiveness and missing prognostic analysis
feedback-instructions:: Explain: argument-directed, and a double hit from the rubric: radicalism-without-program (all negation, no positive design) and absent prognostic analysis (no accounting of the measure's own consequences). That second flaw is fixable, and movement two of this bench fixes it, on our own measure, so the critique cannot be returned to sender. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Argument-directed, and a double hit from the rubric: radicalism-without-program (all negation, no positive design) and absent prognostic analysis (no accounting of the measure’s own consequences). That second flaw is fixable — and movement two of this bench fixes it, on our own measure, so the critique cannot be returned to sender.
:::

#### Question: Choice
id:: 42e6609a-b738-40e3-9746-c9d2fdb6efc5
content:: Critique line 5: “Her diagnosis is real and grave — which is exactly why this unserious prescription wrongs it. The gravity of the problem does not transfer to the proposal.”

Speaker-directed or argument-directed?
options::
- Speaker-directed — it concedes her sincerity, so it must be about her
- [x] Argument-directed — the importance-of-problem vs. adequacy-of-solution mismatch
feedback-instructions:: Explain: argument-directed, the source rubric's subtlest row: a contradiction between the weight of the stated problem and the unsatisfactoriness of the proposed path. Conceding the diagnosis makes it more argument-directed, not less; nothing about the speaker is in play. The rubric's one remaining row, ideological capture, sits on the argument side too: it indicts the reasoning's incentives, not the person's character, though in street debate it constantly decays into attribution. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Argument-directed — the source rubric’s subtlest row: a contradiction between the weight of the stated problem and the unsatisfactoriness of the proposed path. Conceding the diagnosis makes it MORE argument-directed, not less; nothing about the speaker is in play. (The rubric’s one remaining row — ideological capture — sits on the argument side too: it indicts the reasoning’s incentives, not the person’s character, though in street debate it constantly decays into attribution.)
:::

Movement two — the prognostic analysis the manifesto skipped, run honestly on the course’s own measure: an immediate emergency pause on all training runs above 10²⁵ FLOP. Source-pedagogy rule: a measure is not analyzed until you have named consequences for it and against it, across domains.

#### Question: Choice
id:: 2d0b748e-df18-4987-8e42-f01dccf7d436
content:: Consequence card: “Compute-rich actors redirect spending into algorithmic efficiency, eroding what the FLOP threshold measures.”

Does this cut for or against the measure as designed?
options::
- For — it shows the threshold binding
- [x] Against — threshold-gaming pressure the design must anticipate
feedback-instructions:: Explain: against, in the technical domain, the evasion taxonomy's bucket 3 arriving on schedule. Not fatal: it argues for effective-compute indexing and periodic threshold review rather than for no pause. Naming a consequence against your own preferred measure is the discipline being drilled. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Against, in the technical domain — the evasion taxonomy’s bucket 3 arriving on schedule. Not fatal: it argues for effective-compute indexing and periodic threshold review rather than for no pause. Naming a consequence against your own preferred measure is the discipline being drilled.
:::

#### Question: Choice
id:: e16ba894-a1cb-4eb8-b449-173f1504e729
content:: Consequence card: “Verification infrastructure built for the pause — registries, telemetry, inspection corps — survives the pause and supports weaker regimes afterward.”

For or against?
options::
- [x] For — durable institutional gains in the political domain
- Against — sunk costs in the economic domain
feedback-instructions:: Explain: for, institutionally, the foundations' design exception running forward: pause-grade machinery is reusable for caps, transparency, licensing. Regime design compounds; even a pause that lapses leaves the verification commons better than it found it. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
For, institutionally — the foundations’ design exception running forward: pause-grade machinery is reusable for caps, transparency, licensing. Regime design compounds; even a pause that lapses leaves the verification commons better than it found it.
:::

#### Question: Choice
id:: 139208d1-6d1f-4cc8-b928-7d0d8fa58e53
content:: Consequence card: “States that could never train at 10²⁵ FLOP bear no direct cost, while capable states bear all of it — resentment and defection pressure concentrate among exactly the parties whose compliance matters.”

For or against?
options::
- For — the burden falls on those who created the risk
- [x] Against — a political-economy strain concentrated where compliance is most needed
feedback-instructions:: Explain: against, in the political domain, asymmetric burden with compliance-weighted stakes. The two-level-game primer predicts where this bites: capable states' domestic ratification. Mitigations (sunset clauses, shared monitoring budgets, technology-access provisions) belong in the capstone, not in denial. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Against, in the political domain — asymmetric burden with compliance-weighted stakes. The two-level-game primer predicts where this bites: capable states’ domestic ratification. Mitigations (sunset clauses, shared monitoring budgets, technology-access provisions) belong in the capstone, not in denial.
:::

#### Question: Open
id:: 04c7a34f-3906-4c7c-bf8c-e4f09a47b1ec
content:: Last commit, source-pedagogy category “other consequences named”: state one consequence of the pause in a domain the cards did not cover — economic, humanitarian, epistemic, ecological, your call. One or two sentences, with its direction.
assessment-instructions:: There is no answer key. Give full credit if the learner names one consequence of an emergency pause on training runs above 10^25 FLOP in a domain the three cards did not cover (the cards covered algorithmic-efficiency redirection, reusable verification infrastructure, and asymmetric burden on capable states) and states its direction, for or against the measure. Give partial credit if the domain is new but the direction is missing, or the direction is stated but the consequence repeats a card. XLab requires at least 60 characters.
feedback-instructions:: Tell the learner: no key for this one; the rubric habit is the point. The consequence table has more rows than any card deck, and capstone graders (like the source round's graders) award the rows you open yourself. Carry your answer into your own regime design. Two or three sentences.

#### Text
content::
\## Defended-ranking memo

#### Question: Open
id:: d31b5568-5767-496e-8065-3a81639be8ab
content:: Produce the defended-ranking memo: a recommended mechanism portfolio for one named policy goal, with residual blind spots and their owners — the artifact the 4.2 capstone receives. Defend the ranking against both your own initial guesses and the field’s published ratings.

Audience: whoever acts on the 4.2 capstone — the portfolio is handed forward, not filed. (about 900 words; peer reviewed against the rubric)
assessment-instructions:: This is the module's peer-reviewed written output (XLab memo slot m4-0-ranking-memo, about 900 words). Check for: one named policy goal; a recommended portfolio of mechanisms with a defended ranking; residual blind spots each assigned an owner (who covers it); an explicit defence against the learner's own initial 2.0 ratings and against published ratings from the module readings. Respond to the reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the reference map is required.
{>>{"author":"Elias's AI","timestamp":1788016140074}@@XLab renders this as its persistent MemoDesk (a cross-lesson notebook, JavaScript-backed). The memo brief and audience are reproduced verbatim from memos.ts; the desk itself is not reproducible.<<}

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Sheehan, Matt. "China’s Views on AI Safety Are Changing—Quickly." Carnegie Endowment for International Peace, Aug. 2024. [carnegieendowment.org](https://carnegieendowment.org/research/2024/08/chinas-views-on-ai-safety-are-changing-quickly)
*Sheehan reads the July 2024 Third Plenum decision, the first major CCP policy document to call for an AI safety supervision and regulation system, as evidence of Beijing’s accelerating turn toward frontier-AI safety oversight.*

Wasil, Akash R., Tom Reed, Jack William Miller, et al. "Verification Methods for International AI Agreements." *arXiv*, Aug. 2024. [arxiv.org](https://arxiv.org/abs/2408.16074)
*A survey of ten verification techniques for catching violations of international AI agreements, from unauthorized training runs to undeclared data centers.*

Hooker, Sara. "On the Limitations of Compute Thresholds as a Governance Strategy." *arXiv*, July 2024. [arxiv.org](https://arxiv.org/html/2407.05694v1)
*The counterargument on thresholds: why compute cutoffs are a shaky governance proxy, since the compute-risk relationship is uncertain and moving.*

Shavit (2023), cited inline in the technical-feasibility card, has no verified citation entry yet. The reference-map sources are named inside each mechanism's callout.

XLab. "4.1 Feasibility Judgments." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/capstone/capstone-feasibility)
*The source lesson this page adapts, including the reference map and the drill bench.*
:::
