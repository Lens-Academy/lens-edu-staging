---
id: '01252915-279a-48c6-b34a-97e51ce90203'
title: "4.1 Feasibility Judgments"
tldr: {--{"author":"Elias's AI","timestamp":1788015954283}@@"Faithful alpha import--}{++{"author":"Elias's AI","timestamp":1788015954283}@@"Mechanisms age; the skill++} of {--{"author":"Elias's AI","timestamp":1788015954283}@@XLab lesson 4.1 Feasibility Judgments."--}{++{"author":"Elias's AI","timestamp":1788015954283}@@judging them does not. Check the bets you placed in 2.0 against the reference map, learn the four questions that turn 'is it feasible?' into an answer, survive three drill benches, and write the defended-ranking memo your capstone will build on."++}
summary_for_tutor: "Imported from XLab's {--{"author":"Elias's AI","timestamp":1788015954283}@@canonical --}Verification {--{"author":"Elias's AI","timestamp":1788015954283}@@curriculum. Preserve--}{++{"author":"Elias's AI","timestamp":1788015954283}@@curriculum; preserve++} source framing. {--{"author":"Elias's AI","timestamp":1788015954283}@@XLab currently blocks cross-site embedding, so linked external exercises must be completed--}{++{"author":"Elias's AI","timestamp":1788015954283}@@Sequence: (1) Intuition check: the reference map for the twelve mechanisms rated in 2.0 (a table of rung labels on four metrics plus one closed callout per mechanism with XLab's explanation and sources), then an open reflection++} on {--{"author":"Elias's AI","timestamp":1788015954283}@@XLab."--}{++{"author":"Elias's AI","timestamp":1788015954283}@@one mechanism where Module 2 evidence changed the learner's view. (2) Four metrics of feasibility, each a callout with a source excerpt and what to glean. (3) Drill bench: three benches (evasion, regime, position) as graded choice questions, one numeric estimate and one short open answer, each followed by a closed 'Why' callout; give the why after each answer, do not reveal it before. (4) The defended-ranking memo (about 900 words, peer reviewed) that 4.2 receives. When the learner disagrees with the reference map, ask which metric and what evidence would settle it rather than defending the map."++}
tags: [wip]{++{"author":"Elias's AI","timestamp":1788015954283}@@
duration_minutes: 120++}
---
#### Text
content::
Verification is a rapidly changing field. Technological breakthroughs and geopolitical shifts alike significantly affect the relevance, feasibility, and effectiveness of different verification models. In this module, you will develop the future-proof skill of *discernment:* learning how to discern the relative feasibility of any mechanism using research strategies and critical analysis.

\## Intuition Check

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016020463}@@ **Interactive exercise:** XLab's `mechanism-sort-reveal` widget--}{++{"author":"Elias's AI","timestamp":1788016020463}@@
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
*Every AI accelerator carries a unique cryptographic identity and can prove to a remote verifier what firmware it is running. This would let a treaty body maintain a registry of who holds which chips and confirm the hardware++} has {--{"author":"Elias's AI","timestamp":1788016020463}@@no direct Lens equivalent yet. Complete--}{++{"author":"Elias's AI","timestamp":1788016020463}@@not been tampered with.*

The primitives ship today on frontier accelerators; what is missing is the registry regime around them, so technical feasibility is high but not finished. Politics are middling: low intrusiveness helps, but rivals must still accept a shared registry. Effectiveness is the anchor case — attestation proves specific claims about specific hardware, and the concentrated supply chain means nearly every serious training effort passes through chips it can cover. Because it lives in silicon, it persists across model paradigms for the lifetime of the installed base.

Sources: Aarne, Fist & Withers, Secure, Governable Chips (CNAS, 2024); Kulp et al., Hardware-Enabled Governance Mechanisms (RAND working paper, 2024); NVIDIA H100 confidential-computing and attestation documentation (2023)
:::

:::callout {title="On-chip compute metering" tone="neutral" collapse="closed"}
*Chips measure how much computation they perform and what class of workload it is, then report the totals to a verifier. This could confirm that declared facilities stay under agreed compute thresholds.*

Metering firmware that survives a motivated operator with physical access does not exist yet — this is research, not rollout. Politically, continuous usage reporting cuts deeper than an inventory of chips, and the fight over reporting granularity would be real. If it runs, though, it delivers: aggregate compute totals bear directly on threshold claims across everyone who uses covered chips. Rooted in hardware,++} it {++{"author":"Elias's AI","timestamp":1788016020463}@@ages well, with the caveat that algorithmic efficiency slowly weakens what any compute number means.

Sources: Shavit, What Does It Take to Catch a Chinchilla? (2023); Kulp et al., Hardware-Enabled Governance Mechanisms (RAND working paper, 2024)
:::

:::callout {title="Hardware licensing and remote authorization" tone="neutral" collapse="closed"}
*Chips require a cryptographic license, renewed on a schedule, to keep operating at full capability. An authority could suspend or revoke a violator's compute directly rather than relying on sanctions after the fact.*

Tamper-resistant remote authorization that survives a state-level adversary with physical possession is years out; flexHEG-style designs are still on paper. Politically it is the hardest sell on the list — an external off-switch for domestic compute. Effectiveness lands mid-scale because it is control more than evidence: a valid license says little about what actually ran, even though coverage through the chip base would be broad. Durability tracks the hardware it rides on, minus a permanent arms race over defeat devices.

Sources: Petrie, Heim et al., Interim Report: Mechanisms for Flexible Hardware-Enabled Guarantees (2024); Aarne, Fist & Withers, Secure, Governable Chips (CNAS, 2024); Wasil et al., Verification Methods for International AI Agreements (2024)
:::

:::callout {title="Independent verification of training claims" tone="neutral" collapse="closed"}
*Developers preserve checkpoints and training records, and verifiers recompute randomly chosen segments of the run on their own cluster. A match supports the claim that the declared training run is what actually happened.*

Spoofed ++}in the {--{"author":"Elias's AI","timestamp":1788016020463}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/capstone/capstone-feasibility).--}{++{"author":"Elias's AI","timestamp":1788016020463}@@lab, expensive to recompute, and undemonstrated at frontier scale — early research. Politically it demands the crown jewels: checkpoints, data, and hyperparameters, though only for declared runs.++} Its {--{"author":"Elias's AI","timestamp":1788016020463}@@surrounding lesson text--}{++{"author":"Elias's AI","timestamp":1788016020463}@@effectiveness is capped by coverage, strong claims about runs someone chose to declare and silence about everyone else. It also decays fast: training techniques shift underneath it, and every shift reopens the spoofing question.

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

Export licensing, customs data, and financial trails already track advanced chips; the machinery is real but leaky, with documented smuggling in the tens of thousands of units. The political high anchor lives here: reporting attached to export licenses that already operate. Effectiveness pairs broad coverage of who holds capability with weaker evidence about what they do with it. The decay vector++} is {--{"author":"Elias's AI","timestamp":1788016020463}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788016020463}@@structural — smuggling networks adapt, and chip fabrication outside the control regime grows every year.++}

{--{"author":"Elias's AI","timestamp":1788016020463}@@#### Text--}{++{"author":"Elias's AI","timestamp":1788016020463}@@Sources: Grunewald, AI Chip Smuggling into China (IAPS, 2023); US BIS advanced-computing export controls (2022, updated 2023)++}
{--{"author":"Elias's AI","timestamp":1788016020463}@@content::--}{++{"author":"Elias's AI","timestamp":1788016020463}@@:::

:::callout {title="National intelligence sharing" tone="neutral" collapse="closed"}
*States pass leads from their own collection to an international verification body, the way national tips have pointed nuclear inspectors at undeclared facilities. The regime supplies the follow-up; the agencies supply the anomaly.*

Collection exists today and needs no invention. The politics of sharing are the bottleneck: sources and methods, selective cooperation, wildly unequal capacity. Effectiveness is the coverage mirror-image of the consensual mechanisms — it can see precisely the undeclared activity everything else misses, but it delivers leads, not proof. And it is durable the way espionage is durable: the tradecraft adapts alongside whatever it watches.

Sources: IAEA and UNSCOM experience with member-state information (Iraq, 1991 onward); Baker, Nuclear Arms Control Verification and Lessons for AI Treaties (2023)
:::

:::callout {title="Whistleblower channels and protections" tone="neutral" collapse="closed"}++}
{--{"author":"Elias's AI","timestamp":1788016020463}@@Return --}{++{"author":"Elias's AI","timestamp":1788016020463}@@*Secure reporting channels, anti-retaliation protections, and rewards give employees, contractors, and suppliers a path to report concealed activity. Insiders can see what no sensor reaches.*

Channels are trivial to build; the mechanism is law and institutions, not technology. Protections exist in some jurisdictions and stop at exactly the borders where they would matter most. A single insider can deliver the most incriminating evidence available — but sporadically, uncorroborated, and nothing guarantees an insider exists where you need one, which caps effectiveness. Durability is decent: as long as humans build these systems, some of them can talk.

Sources: A Right ++}to {--{"author":"Elias's AI","timestamp":1788016020463}@@your ranking--}{++{"author":"Elias's AI","timestamp":1788016020463}@@Warn about Advanced Artificial Intelligence, open letter++} from {++{"author":"Elias's AI","timestamp":1788016020463}@@AI-lab employees (2024); Wasil et al., Verification Methods for International AI Agreements (2024)
:::

:::callout {title="On-site and challenge inspections" tone="neutral" collapse="closed"}
*International inspectors visit declared facilities on a routine schedule and can demand short-notice access to suspect sites. Managed-access rules decide what inspectors may see and what stays shielded.*

The craft is proven and the institutions exist; nothing technical blocks it. Consent does: no major AI state currently accepts foreign inspectors inside frontier labs, and the CWC's challenge provision has never once been invoked. When inspectors do get in, effectiveness is high — direct observation resolves what remote evidence cannot, across declared and challenged sites alike. The regime decays politically rather than technically, one access fight at a time.

Sources: Chemical Weapons Convention managed-access and challenge-inspection provisions (OPCW); Wasil et al., Verification Methods for International AI Agreements (2024); Baker, Nuclear Arms Control Verification and Lessons for AI Treaties (2023)
:::

:::callout {title="Privacy-preserving proofs" tone="neutral" collapse="closed"}
*Zero-knowledge proofs and secure multiparty computation let a developer prove a claim about a model or training run without revealing weights, code, or data. Verification without disclosure, if ++}the {--{"author":"Elias's AI","timestamp":1788016020463}@@beginning--}{++{"author":"Elias's AI","timestamp":1788016020463}@@cryptography scales.*

The low anchor for technical feasibility: proving anything at frontier scale is orders++} of {++{"author":"Elias's AI","timestamp":1788016020463}@@magnitude beyond today's cryptography, and fully homomorphic approaches are worse still. If that changed, the politics look comparatively good — this is the rare mechanism whose entire design goal is confidentiality. Effectiveness would be capped by scope: it proves exactly the claims parties agree to formalize, over runs they choose to prove, and nothing else. The cryptographic assumptions age well; ++}the {--{"author":"Elias's AI","timestamp":1788016020463}@@course.--}{++{"author":"Elias's AI","timestamp":1788016020463}@@claim set needs renegotiating every time the paradigm moves.++}

{++{"author":"Elias's AI","timestamp":1788016020463}@@Sources: Garg et al., Experimenting with Zero-Knowledge Proofs of Training (2023); Kang et al., zero-knowledge proofs for ML inference (2022); Wasil et al., Verification Methods for International AI Agreements (2024)
:::
{>>{"author":"Elias's AI","timestamp":1788016020463}@@XLab's mechanism-sort-reveal widget overlays the learner's sealed 2.0 ratings (browser localStorage) on this reference map and computes per-mechanism gaps ("Close call", "Near miss", "Big gap"). The learner-specific overlay cannot be reproduced; the reference map and XLab's explanations are reproduced verbatim from the widget data file.<<}

++}#### Question: Open
id:: bb06a146-287c-498d-bd22-b27545fa1c9e
content:: {++{"author":"Elias's AI","timestamp":1788016020463}@@Return to your ranking from the beginning of the course. ++}Choose one mechanism for which later evidence in Module 2 changed your view. {++{"author":"Elias's AI","timestamp":1788016020463}@@Write brief answers to the following in your notebook:

- ++}What heuristics did you initially use?{++{"author":"Elias's AI","timestamp":1788016020463}@@
-++} What evidence changed your judgment?{++{"author":"Elias's AI","timestamp":1788016020463}@@
-++} What question should you have asked earlier?{--{"author":"Elias's AI","timestamp":1788016020463}@@ Where --}{++{"author":"Elias's AI","timestamp":1788016020463}@@

Pay attention to how your heuristics changed: where ++}was your intuition accurate, and where was it off?
{--{"author":"Elias's AI","timestamp":1788016020463}@@feedback:: false--}{++{"author":"Elias's AI","timestamp":1788016020463}@@assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.++}

#### Text
content::
\## Four Metrics of Feasibility

“Is this mechanism feasible?” is usually too vague to answer beyond an initial intuition check, like you did in {--{"author":"Elias's AI","timestamp":1788015963580}@@1.0.2.--}{++{"author":"Elias's AI","timestamp":1788015963580}@@[[../Lenses/XLab Verification - v-mechanism-effective|2.0]].{>>{"author":"Elias's AI","timestamp":1788015963580}@@MDX says "1.0.2", which does not exist in XLab's curriculum; the intuition check (Place your bets) is the mechanism-sort widget in 2.0. Reported to Elias for XLab.<<}++} Feasibility depends on myriad factors, including what the mechanism must verify, whom it must cover, where it would operate, how soon it must be deployed, and what level of performance is required. A serious feasibility assessment should answer four connected questions, which you were introduced to at the beginning of Module 2:

:::callout {--{"author":"Elias's AI","timestamp":1788015955997}@@{title="Technical feasibility"--}{++{"author":"Elias's AI","timestamp":1788015955997}@@{title="1. Technical Feasibility"++} tone="blue"}
Can the mechanism be built and operated at the required scale? Examine the maturity of its hardware and software, its error rates, cost, staffing needs, security, dependencies, and performance under realistic conditions. Keep the distinction between a promising component and a complete operational system. The existence of hardware attestation, for example, does not by itself prove that a full training claim can be reliably verified.

**Source:** Shavit (2023), [What does it take to catch a Chinchilla?](https://arxiv.org/abs/2303.11341) (arXiv:2303.11341)

**Excerpt (from the abstract):** “The system consists of interventions at three stages: (1) using on-chip firmware to occasionally save snapshots of the the neural network weights stored in device memory, in a form that an inspector could later retrieve; (2) saving sufficient information about each training run to prove to inspectors the details of the training run that had resulted in the snapshotted weights; and (3) monitoring the chip supply chain to ensure that no actor can avoid discovery by amassing a large quantity of un-tracked chips.”

**What you should glean:** The author must chain three subsystems together before the mechanism can operate. Count the parts that exist today and the parts that are only proposals. The firmware, the training log, and the supply-chain monitor are each a separate engineering project, so the full system is far less mature than its most mature part.
:::

:::callout {--{"author":"Elias's AI","timestamp":1788015957858}@@{title="Political feasibility"--}{++{"author":"Elias's AI","timestamp":1788015957858}@@{title="2. Political Feasibility"++} tone="purple"}
Whose cooperation is required, and how easy is it to get them to agree? A verification system may depend on legislators, regulators, laboratories, cloud providers, chipmakers, standards bodies, inspectors, foreign governments, and/or enforcement agencies. Identify who must authorize, build, operate, provide access, interpret findings, and act on them. Then identify which actor could block implementation, and why: consider the benefits actors might receive, the costs and risks they might bear, and available alternatives.

**Source:** Sheehan (Carnegie, Aug 2024), [China’s Views on AI Safety Are Changing—Quickly](https://carnegieendowment.org/research/2024/08/chinas-views-on-ai-safety-are-changing-quickly)

**Excerpt:** The July 2024 Third Plenum decision called on the government to “establish an AI safety supervision and regulation system”: the first major CCP policy document to call for oversight aimed at frontier AI risks.

**What you should glean:** One necessary actor put a new position into its most authoritative document type. This is direct data about political feasibility: a mechanism that needs the agreement of the Chinese government became easier to get in July 2024 than it was in 2023. Track the document type, not only the words, because a Plenum decision binds more actors than an op-ed does.
:::

:::callout {--{"author":"Elias's AI","timestamp":1788015959506}@@{title="Verification effectiveness"--}{++{"author":"Elias's AI","timestamp":1788015959506}@@{title="3. Verification Effectiveness"++} tone="green"}
Would the mechanism produce evidence that matters? Ask what claim the evidence would actually support, how direct it is, whether it has been tested against adaptive evasion, and which actors or activities remain outside its coverage. A deployable mechanism may still contribute little to detecting, deterring, or demonstrating compliance.

**Source:** Wasil, Reed, Miller & Barnett (2024), [Verification methods for international AI agreements](https://arxiv.org/abs/2408.16074) (arXiv:2408.16074)

**Excerpt (on data center inspections):** “Inspections can only be carried out with the agreement of the host nation, potentially allowing time for concealment of violations.”

**What you should glean:** The mechanism is fully buildable, but the evidence it produces is weak against an adaptive adversary. A clean inspection report only supports the claim “we found nothing at the declared site on the agreed day.” Ask what claim the evidence supports, not whether the mechanism can run.
:::

:::callout {--{"author":"Elias's AI","timestamp":1788015961330}@@{title="Durability"--}{++{"author":"Elias's AI","timestamp":1788015961330}@@{title="4. Durability"++} tone="amber"}
Will the verification mechanism persist across technological and geopolitical change, or is it easily rendered obsolete by capability jumps or the decline of a fraught inter-country relationship? A fixed compute threshold is relatively fragile because improvements in algorithms can move dangerous capabilities below the regulated line. Chip-level logging or attestation may be more durable because it is anchored in physical infrastructure with slower turnover. Durability is therefore comparative: even hardware-based mechanisms require updating as chips, supply chains, and evasion strategies change.

**Source:** Hooker (2024), [On the Limitations of Compute Thresholds as a Governance Strategy](https://arxiv.org/html/2407.05694v1) (arXiv:2407.05694)

**Excerpt (from the abstract):** “A key conclusion of this essay is that compute thresholds, as currently implemented, are shortsighted and likely to fail to mitigate risk. The relationship between compute and risk is highly uncertain and rapidly changing. Relying upon compute thresholds overestimates our ability to predict what abilities emerge at different scales.”

**What you should glean:** The threshold decays because the quantity it measures and the risk it targets move apart over time. Ask this of each mechanism: which external change breaks the connection between what it measures and what the treaty cares about, and how fast does that change move? A mechanism with an update path survives; a fixed number does not.
:::

\## Drill Bench

The evasion, regime and position benches — module 3 and module 4, and the prep for the capstone. One step at a time: commit, read why, then Continue.

#### Text
content:: **Interactive exercise:** XLab's `drills-games` widget has no direct Lens equivalent yet. Complete it in the [original XLab lesson](https://aisafetytracks.com/tracks/verification/capstone/capstone-feasibility). Its surrounding lesson text is preserved here.

#### Text
content:: **Import gap:** XLab persistent memo desk has no clean Lens equivalent. Use the [original XLab lesson](https://aisafetytracks.com/tracks/verification/capstone/capstone-feasibility) for this element.

#### Text
content::
*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/capstone/capstone-feasibility)*
