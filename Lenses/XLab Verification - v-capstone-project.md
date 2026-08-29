---
id: '604bd0b7-483a-4f65-b8ae-49bda77adb57'
title: "4.2 Capstone project"
tldr: "One piece of work that shows what you learned, on a problem you chose. Thirty briefs from the capstone bank are laid out below with the numbers that decide whether you can take one on (team, hours, weeks, mentor); or propose your own. Then put your name on the sheet."
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. The capstone page: short framing (choose from the bank or propose your own), then the sign-up sheet as one open question (brief chosen or own proposal, in the learner's words), then the capstone bank reproduced as one closed callout per brief (30 course-fit briefs, grouped by track, each with summary, team, effort, duration, difficulty, deliverable, audience, skills, prerequisites and sources). Help the learner compare briefs against their background and hours; do not pick for them. If they propose their own idea, check it is relevant to technical AI governance and aimed at an AI-safety-related theme, and push them to state deliverable, audience and the realistic version."
tags: [wip]
duration_minutes: 360
---
#### Text
content::
You are almost done. The only thing left is the capstone project — one piece of work that shows what you have learned, applied to a problem you chose.

**There is no assigned task.** Two ways to pick one:

- **Choose from the capstone bank.** The full bank is below — every brief with the numbers that decide whether you can take it on.{>>{"author":"Elias's AI","timestamp":1788015819424}@@Dropped the trailing clause "and the [bank page](/verification/capstone-bank) has the same briefs with search and filters": a relative XLab link, dead on Lens, and we add no XLab links. XLab's bank page holds 80 briefs across the whole program; this lens carries the 30 that XLab's CapstoneBank component prints on this unit (courseFit).<<}
- **Suggest your own capstone idea.** It has to be relevant to technical AI governance and aimed at an AI-safety-related theme.

Either way, put your name on the sign-up sheet, so your facilitator knows what you are working on and can read your proposal.

#### Question: Open
id:: 8b5f4955-5f96-4d52-86d7-6eac74af9754
content:: \## Sign-up sheet

Your facilitator reads this sheet — the brief you committed to, or the idea you proposed.

Name the brief from the bank below you are taking (its title), or describe your own capstone idea: what you would build or write, and what it would show.
assessment-instructions:: This is the capstone sign-up, not a graded exercise. If the learner named a brief from the bank, confirm it back in one sentence and ask one question about fit: their team size, the hours per week they have, or a listed prerequisite they have not covered. If the learner proposed their own idea, check that it is relevant to technical AI governance and aimed at an AI-safety-related theme, then ask them to name the deliverable and the audience if they have not. Do not grade or rank the choice.
{>>{"author":"Elias's AI","timestamp":1788015830841}@@XLab's CapstoneSignup is a logged-in form writing to XLab's database (a brief picker over the bank plus a proposal textarea with placeholder "What you would build or write, and what it would show.", and the facilitator reads the resulting sheet). The database sheet itself cannot be reproduced; this open question captures the same two inputs so the facilitator can read them on Lens.<<}

#### Text
content::
\## Capstone bank

Each brief below is what XLab's bank card shows on this unit, plus the full-brief fields (audience, skills, prerequisites, sources). Open a brief to read it.

\## Technical Governance (1 brief)
:::callout {title="Redraw the AI-vs-Human Capability Chart" tone="neutral" collapse="closed"}
*The best-known chart of AI against human performance stops in 2023. Rebuild it at today's date and say what a threshold can honestly attach to.*

Fits this course: Lands on 1.1 — a pause agreement has to name a covered capability, and this is the measurement that claim would rest on.

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · notebook · mentor optional · ready to run

**Deliverable:** Reproducible chart and dataset, a methods note, and a two-page brief on what a capability threshold can be written against

**Audience:** Anyone about to cite a capability curve in a threshold argument.

**Skills:** benchmark literacy, data provenance, normalisation choices, trend presentation, threshold design

**Sources:** [Test scores of AI systems on various capabilities relative to human performance — Our World in Data](https://ourworldindata.org/grapher/test-scores-ai-capabilities-relative-human-performance); [Dynabench: Rethinking Benchmarking in NLP — Kiela et al. (2021)](https://arxiv.org/abs/2104.14337); [AI Benchmarking Dashboard — Epoch AI](https://epoch.ai/data/ai-benchmarking-dashboard); [AI Index — Stanford HAI](https://hai.stanford.edu/ai-index)
:::

\## Verification (29 briefs)
:::callout {title="A Cloud KYC Regime That Is Not Just Paperwork" tone="neutral" collapse="closed"}
*Module 2.2 warns that self-reporting alone is a paperwork regime. Design the cloud reporting rules for one provider so that at least one claim in them is actually checkable.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Reporting-rule spec with a per-claim checkability rating and the evasion routes it leaves open

**Audience:** The national regulator drafting the reporting obligation, and the provider who has to implement it.

**Skills:** regime design, telemetry analysis, evasion modelling, cost-of-compliance analysis

**Prerequisites:** Verification 1 — actors; Verification 2.2 — the cloud layer; Verification 3 — covert development

**Sources:** [Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers — Egan & Heim (2023)](https://arxiv.org/abs/2310.13625)
:::

:::callout {title="A Minimum Viable Compute-Accounting Audit" tone="neutral" collapse="closed"}
*What should a commercial AI audit prove about how each GPU was used? Claims, logs, retention, auditor access — and what happens when logs are missing.*

1–2 people · 12–18 hrs · 3 weeks · ≈5 hrs/wk · core · spec · mentor optional · draft

**Deliverable:** Draft auditing standard, 2–3 pages

**Audience:** The audit firm that has to say what its stamp proves.

**Skills:** audit design, evidence standards, logging requirements

**Prerequisites:** Verification 1 — actors; Verification 2.2 — the cloud layer
:::

:::callout {title="A Reporting Channel an Insider Would Actually Use" tone="neutral" collapse="closed"}
*Module 2.4 says the human layer reveals what hardware and intelligence cannot — if evidence reaches a verifier. Design the channel, against the NDAs and equity that stop it.*

1–2 people · 12–18 hrs · 3 weeks · ≈5 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Channel design — who receives, what protects the reporter, and the evidence standard on arrival

**Audience:** The regulator or oversight body that wants insider evidence and currently receives none.

**Skills:** institutional design, incentive analysis, evidence standards, protective-regime drafting

**Prerequisites:** Verification 1 — actors; Verification 2.4 — the human layer

**Sources:** [A Collection of AI Governance Research Ideas — von Knebel & Anderljung (2024), idea 20: AI and whistleblowing](https://www.markusanderljung.com/blog/a-collection-of-ai-governance-research-ideas-2024)
:::

:::callout {title="A Security Case for One Sensor" tone="neutral" collapse="closed"}
*Power, temperature and timing telemetry cannot classify workloads reliably. Build the security case for using one sensor feed anyway.*

1–2 people · 12–18 hrs · 3 weeks · ≈5 hrs/wk · core · analysis · mentor optional · draft

**Deliverable:** A verification security case for one telemetry mechanism

**Audience:** The verifier deciding whether a sensor feed is worth installing.

**Skills:** security cases, telemetry analysis, adversarial reasoning

**Prerequisites:** Verification 2.0 — confidentiality vs verifiability; Verification 2.1 — the hardware layer
:::

:::callout {title="A Verification Package You Could Ship in a Year" tone="neutral" collapse="closed"}
*Twelve months, no new chips. Assemble the verification package that could actually be deployed, and state plainly what it still cannot see.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Prioritized implementation roadmap with residual gaps stated

**Audience:** The task force told to stand up verification this year, not next.

**Skills:** regime design, feasibility triage, gap analysis

**Prerequisites:** Verification 2.x — the four layers; Verification 4.1 — feasibility and layering
:::

:::callout {title="Build the US–China AI Incident Hotline" tone="neutral" collapse="closed"}
*The hotline has been proposed for years and never specified. Design it — what counts as an incident, who picks up, what is said, and why either side would believe it.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Hotline design — incident taxonomy, escalation ladder, and the credibility problem addressed

**Audience:** The desk officers on both ends who would have to use it at 3am.

**Skills:** crisis mechanism design, institutional analysis, signalling under mistrust, precedent critique

**Prerequisites:** Verification 0 — treaty anatomy; Verification 1 — actors; Verification 4.1 — feasibility and layering

**Sources:** [Orphaned Policies (post 5 of 7 on AI governance) — Mass_Driver, orphan 7](https://www.lesswrong.com/posts/wFKZmvfRfNn24HNHp/orphaned-policies-post-5-of-7-on-ai-governance)
:::

:::callout {title="Can You Prove This Model Came From That Run?" tone="neutral" collapse="closed"}
*Proof-of-learning is in Module 2.1 as fragile and spoofed; model-heritage inference is an open problem next door. Assess what either can support and what a regime could rest on them.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · dossier · mentor recommended · draft

**Deliverable:** Feasibility assessment of training-provenance claims, with the claims each method can and cannot carry

**Audience:** The regulator asked to accept "this is the model we evaluated" as established fact.

**Skills:** feasibility assessment, provenance reasoning, adversarial analysis, evidence standards

**Prerequisites:** Verification 2.0 — confidentiality vs verifiability; Verification 2.1 — the hardware layer

**Sources:** [Open Technical Problems in Open-Weight AI Model Risk Management (2025), §4.5 model provenance and forensics: model heritage inference, and how practical and scalable proof-of-training methods are](https://openreview.net/forum?id=8QyGLnFkzc)
:::

:::callout {title="Cut the Interconnect, Keep the Inference" tone="neutral" collapse="closed"}
*Disconnect part of the optical links between racks and training stops while inference survives — allegedly. Work out what remains possible and who checks the cables.*

1–2 people · 10–14 hrs · 2 weeks · ≈6 hrs/wk · core · design · mentor optional · draft

**Deliverable:** Short protocol design plus a red-team pass on it

**Audience:** The negotiator who needs an emergency measure that does not kill civilian service.

**Skills:** protocol design, network reasoning, red-teaming

**Prerequisites:** Verification 2.1 — the hardware layer; Verification 3 — covert development
:::

:::callout {title="Does Switching Off the Cooling Switch Off the Training?" tone="neutral" collapse="closed"}
*An inspector confirms the cooling is off. Under what conditions does that actually rule out a large training run — and how would an operator get around it?*

1–2 people · 12–18 hrs · 3 weeks · ≈5 hrs/wk · core · analysis · mentor optional · draft

**Deliverable:** Threat model with a claim → observable → evasion → countermeasure table

**Audience:** The inspectorate asked to certify that a halt is actually a halt.

**Skills:** threat modelling, physical-layer reasoning, evasion analysis

**Prerequisites:** Verification 2.1 — the hardware layer; Verification 3 — covert development
:::

:::callout {title="Hardware Chokepoint Dossier" tone="neutral" collapse="closed"}
*Trace one node of the compute supply chain end to end and rank it as a verification chokepoint — who sees what, and who would have to agree.*

1 person · 10–14 hrs · 2 weeks · ≈6 hrs/wk · core · dossier · mentor optional · ready to run

**Deliverable:** Six-to-eight page dossier with a chokepoint ranking table

**Audience:** An analyst deciding where to spend a verification budget.

**Skills:** supply chain analysis, actor mapping, chokepoint ranking, source triangulation

**Prerequisites:** Verification 1 — actors; Verification 2.1 — the hardware layer
:::

:::callout {title="How Much Hidden Compute Breaks the Deal?" tone="neutral" collapse="closed"}
*How much concealed compute must a state retain before a pause agreement stops being worth signing? Three scenarios, priced for capability and strategic effect.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · analysis · mentor recommended · draft

**Deliverable:** Scenario analysis with a sensitivity table

**Audience:** The delegation deciding how much verification is enough to sign.

**Skills:** scenario analysis, capability estimation, strategic reasoning

**Prerequisites:** Verification 2.3 — the intelligence layer; Verification 3 — covert development; Verification 4.1 — feasibility and layering
:::

:::callout {title="Is the Model in Production the Model That Passed?" tone="neutral" collapse="closed"}
*Evals passed on one model. Millions of requests run against another — would anyone notice? Design the chain that lets an auditor say deployed equals evaluated.*

1–2 people · 12–18 hrs · 3 weeks · ≈5 hrs/wk · core · design · mentor optional · draft

**Deliverable:** Protocol diagram from evaluation to deployment, plus an attack tree

**Audience:** The auditor who signed off on the eval and now has to stand behind the deployment.

**Skills:** protocol design, attestation reasoning, attack trees

**Prerequisites:** Verification 2.0 — confidentiality vs verifiability; Verification 3 — covert development
:::

:::callout {title="Make an Eval Result Believable to a Stranger" tone="neutral" collapse="closed"}
*A lab says its model scored below the danger threshold. Specify what a third party would have to observe to believe that — and what it costs to provide.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Attestation spec — the observation chain, the residual trust, and the cost to the lab

**Audience:** The regulator who has to accept or reject a self-reported eval result.

**Skills:** evidence standards, attestation design, adversarial reasoning, cost-of-compliance analysis

**Prerequisites:** Verification 2.x — the four layers; Verification 4.1 — feasibility and layering; TG week 3 — running evals

**Sources:** [Request for Proposals: Improving Capability Evaluations — Coefficient Giving, formerly Open Philanthropy (2025, closed)](https://coefficientgiving.org/funds/navigating-transformative-ai/request-for-proposals-improving-capability-evaluations/)
:::

:::callout {title="Minimal Verification Regime for an Emergency Pause" tone="neutral" collapse="closed"}
*Design the smallest verification regime that could make a three-month emergency pause credible to a party that expects to be cheated.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · core · spec · mentor recommended · ready to run

**Deliverable:** Two-page regime spec plus a one-page evasion annex

**Audience:** The negotiating team that would have to sign it, and the technical staff who would have to run it.

**Skills:** regime design, threat modelling, evidence standards, institutional analysis

**Prerequisites:** Verification 2.x — the four layers; Verification 3 — covert development; Verification 4.1 — feasibility and layering
:::

:::callout {title="Permit Inference, Prohibit Training" tone="neutral" collapse="closed"}
*An agreement permits inference and prohibits training. Define permitted inference so the boundary survives fine-tuning, distillation and synthetic-data generation.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Draft rule, five edge cases, and the revisions they force

**Audience:** The drafter of a pause clause that has to leave deployed services running.

**Skills:** definition drafting, workload analysis, adversarial testing

**Prerequisites:** Verification 2.2 — the cloud layer; Verification 3 — covert development
:::

:::callout {title="Prove Compliance Without Handing Over the Model" tone="neutral" collapse="closed"}
*Module 2.0's whole problem in one artifact — pick one claim a developer must prove, and specify how to prove it without disclosing weights, data, or a trusted enclave.*

1–2 people · 16–22 hrs · 3 weeks · ≈6 hrs/wk · advanced · spec · mentor required · draft

**Deliverable:** Protocol sketch for one claim, with the trust assumptions and the residual disclosure named

**Audience:** The regulator who needs the assurance and the developer who cannot hand over the asset.

**Skills:** protocol reasoning, trust-assumption analysis, cryptographic literacy, feasibility assessment

**Prerequisites:** Verification 2.0 — confidentiality vs verifiability; Verification 2.1 — the hardware layer; Verification 4.1 — feasibility and layering

**Sources:** [Open Problems in Technical AI Governance — Reuel et al. (2025), verification questions: what methods can verify compute usage without TEEs; can ZKPs demonstrate compliance without disclosing architectural details; how can TEEs be designed to limit misuse](https://arxiv.org/abs/2407.14981)
:::

:::callout {title="Red-Team a Verification Stack" tone="neutral" collapse="closed"}
*Take a published verification proposal and break it — a structured evasion report with detection probabilities and the patch each route demands.*

2–3 people · 16–22 hrs · 3 weeks · ≈6 hrs/wk · stretch · analysis · mentor recommended · ready to run

**Deliverable:** Evasion report with an attack tree and a patch list

**Audience:** The team that published the proposal you are attacking.

**Skills:** red-teaming, attack trees, detection reasoning, adversarial cost modelling

**Prerequisites:** Verification 2.x — the four layers; Verification 3 — covert development
:::

:::callout {title="Spot a Training Run Without Looking Inside It" tone="neutral" collapse="closed"}
*Could a verifier tell a large training run from utilisation signatures alone — no workload access, no code? Work out what the signature is and how cheaply it is faked.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · analysis · mentor recommended · draft

**Deliverable:** Signature analysis with a detection-rule sketch and the spoofing cost for each signal

**Audience:** The verifier who will never be allowed to see the workload.

**Skills:** signature analysis, privacy-preserving verification, detection reasoning, adversarial cost modelling

**Prerequisites:** Verification 2.1 — the hardware layer; Verification 2.2 — the cloud layer; Verification 3 — covert development

**Sources:** [Open Problems in Technical AI Governance — Reuel et al. (2025), compute questions: can large training runs be detected while retaining developer privacy, e.g. through signatures in processor utilisation?](https://arxiv.org/abs/2407.14981)
:::

:::callout {title="Steal a Chain of Custody From Another Industry" tone="neutral" collapse="closed"}
*Other industries already track dangerous things through many hands. Take one working custody regime apart and report what transfers to compute — and what does not.*

1–2 people · 14–18 hrs · 3 weeks · ≈5 hrs/wk · core · dossier · mentor optional · draft

**Deliverable:** Case study of one custody regime plus a transfer analysis for the compute supply chain

**Audience:** Whoever is designing chip tracking and does not want to reinvent forty years of practice.

**Skills:** analogical reasoning, regime analysis, precedent critique

**Prerequisites:** Verification 1 — actors; Verification 2.1 — the hardware layer

**Sources:** [A Collection of AI Governance Research Ideas — von Knebel & Anderljung (2024), idea 66: learning from chain of custody applications in other industries](https://www.markusanderljung.com/blog/a-collection-of-ai-governance-research-ideas-2024)
:::

:::callout {title="Stock and Flow Accounting Case Studies" tone="neutral" collapse="closed"}
*Case studies of regimes that track dual-use physical objects — registration, transfer penalties, measured loss rates — as building blocks for compute stock-and-flow accounting.*

1–2 people · 10–14 hrs · 2 weeks · ≈6 hrs/wk · core · dossier · mentor optional · draft

**Deliverable:** Two case studies on the source's own template — methods, penalties, and the measured loss rate

**Skills:** case studies, regime analysis, quantitative loss rates

**Prerequisites:** Verification 1 — actors; Verification 2.1 — the hardware layer

**Sources:** [A Collection of AI Governance Research Ideas — von Knebel & Anderljung (2024), idea 65: stock and flow accounting case studies](https://www.markusanderljung.com/blog/a-collection-of-ai-governance-research-ideas-2024)
:::

:::callout {title="The Security Baseline That Would Have Stopped It" tone="neutral" collapse="closed"}
*Weight exfiltration is the evasion route that voids the compute regime. Write the infrastructure-security baseline a regime would require in advance, and price it.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Security baseline by threat tier, with the audit evidence for each control and its cost

**Audience:** The regulator writing a security condition, and the lab that has to pass an audit against it.

**Skills:** security requirement design, threat tiering, auditability analysis, cost-of-compliance analysis

**Prerequisites:** Verification 2.4 — the human layer; Verification 3 — covert development; Verification 4.1 — feasibility and layering

**Sources:** [Open Problems in Technical AI Governance — Reuel et al. (2025), security questions: what infrastructure-level cybersecurity measures protect model weights from theft; how can models be protected from inference attacks reproducing weights](https://arxiv.org/abs/2407.14981)
:::

:::callout {title="Train It in Pieces, Under Every Threshold" tone="neutral" collapse="closed"}
*Evasion scenario 8 says a run can be fragmented below the line. Work out how far that actually goes today, what it costs, and which threshold designs survive it.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · analysis · mentor recommended · draft

**Deliverable:** Feasibility assessment of fragmented training plus a threshold-design recommendation that survives it

**Audience:** Whoever writes the threshold, and the verifier who has to enforce it.

**Skills:** technical feasibility assessment, evasion modelling, threshold design, cost estimation

**Prerequisites:** Verification 2.1 — the hardware layer; Verification 3 — covert development; TG week 2 — compute governance

**Sources:** [Open Problems in Technical AI Governance — Reuel et al. (2025), compute questions: can AI models be trained using a large number of small compute clusters?](https://arxiv.org/abs/2407.14981)
:::

:::callout {title="Treaty Clause Redraft" tone="neutral" collapse="closed"}
*Take the verification articles of a real arms-control treaty and redraft them for frontier AI — clause by clause, with the disanalogies marked.*

1–2 people · 12–16 hrs · 2 weeks · ≈7 hrs/wk · stretch · analysis · mentor recommended · draft

**Deliverable:** Redrafted clause set with a facing-page commentary

**Audience:** A treaty lawyer who knows arms control and not AI.

**Skills:** legal drafting, clause analysis, analogical reasoning, precedent critique

**Prerequisites:** Verification 0 — treaty anatomy; Verification 2.3 — the intelligence layer
:::

:::callout {title="What Assurance Costs in Secrets" tone="neutral" collapse="closed"}
*Every verification mechanism buys confidence by spending the operator's secrets. Price the exchange rate across inspections, taps, telemetry, trusted hardware and recomputation.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · analysis · mentor recommended · draft

**Deliverable:** Assurance × disclosure × intrusiveness matrix

**Audience:** The operator and verifier negotiating what must be shown for what assurance.

**Skills:** mechanism comparison, privacy analysis, trade-off mapping

**Prerequisites:** Verification 2.0 — confidentiality vs verifiability; Verification 2.x — the four layers
:::

:::callout {title="What Would Compute Monitoring Actually Cost?" tone="neutral" collapse="closed"}
*The compute-monitoring literature has the mechanisms, the timing, even a first-pass inspector headcount. It has no penalties and no price. Produce the costing a budget office would need.*

1–2 people · 16–22 hrs · 3 weeks · ≈6 hrs/wk · stretch · analysis · mentor recommended · draft

**Deliverable:** Costed monitoring plan — headcount, inspection cadence, penalty schedule, hardware dependencies

**Audience:** The agency that would be asked to stand this up, and the committee funding it.

**Skills:** cost estimation, institutional design, inspection regime design, dependency analysis

**Prerequisites:** Verification 1 — actors; Verification 2.1 — the hardware layer; Verification 4.1 — feasibility and layering

**Sources:** [Orphaned Policies (post 5 of 7 on AI governance) — Mass_Driver, orphan 8](https://www.lesswrong.com/posts/wFKZmvfRfNn24HNHp/orphaned-policies-post-5-of-7-on-ai-governance)
:::

:::callout {title="When Does a Secret Datacenter Earn an Inspection?" tone="neutral" collapse="closed"}
*Power draw, cooling, procurement, satellite imagery — when does a stack of maybes justify an inspection? Build the rubric that turns signals into a decision.*

1–2 people · 12–18 hrs · 3 weeks · ≈5 hrs/wk · core · memo · mentor optional · draft

**Deliverable:** Evidentiary rubric plus a decision memo

**Audience:** The agency that has to decide when suspicion becomes an inspection.

**Skills:** evidence standards, intelligence analysis, escalation design

**Prerequisites:** Verification 2.3 — the intelligence layer; Verification 3 — covert development
:::

:::callout {title="When Is Tamper-Evidence Enough?" tone="neutral" collapse="closed"}
*Tamper-proof hardware is expensive and unsolved; tamper-evident is neither. In which institutional settings is finding out afterwards actually sufficient?*

1–2 people · 10–14 hrs · 2 weeks · ≈6 hrs/wk · core · analysis · mentor optional · draft

**Deliverable:** Decision framework

**Audience:** The regime designer deciding where prevention is worth its cost.

**Skills:** institutional design, inspection economics, risk analysis

**Prerequisites:** Verification 2.1 — the hardware layer; Verification 4.1 — feasibility and layering
:::

:::callout {title="When the Weights Are Already Out" tone="neutral" collapse="closed"}
*Module 3 rates weight exfiltration as the evasion route that bypasses the compute regime entirely. Specify what a verification regime does the day after it happens.*

1–2 people · 14–20 hrs · 3 weeks · ≈6 hrs/wk · stretch · spec · mentor recommended · draft

**Deliverable:** Post-exfiltration regime annex — what is still verifiable, what is not, and what the agreement should have said

**Audience:** The parties to an agreement whose central mechanism has just been routed around.

**Skills:** regime design, ecosystem monitoring, threat modelling, evidence standards

**Prerequisites:** Verification 2.x — the four layers; Verification 3 — covert development; Verification 4.1 — feasibility and layering

**Sources:** [Open Technical Problems in Open-Weight AI Model Risk Management (2025)](https://openreview.net/forum?id=8QyGLnFkzc)
:::

:::callout {title="Where Should the Supply Chain Keep Logs?" tone="neutral" collapse="closed"}
*Manufacturing logs are cheap to demand and easy to drown in. Find the point in the semiconductor chain where credible logs buy the most information for the least trust.*

1–2 people · 12–18 hrs · 3 weeks · ≈5 hrs/wk · core · analysis · mentor optional · draft

**Deliverable:** Ranked chokepoint matrix

**Audience:** The regulator choosing where in the supply chain to demand records.

**Skills:** supply-chain analysis, comparative ranking, measurement design

**Prerequisites:** Verification 1 — actors; Verification 2.1 — the hardware layer
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
The sources listed inside each brief are the bank's own pointers and have no separate citation entries.

XLab. "4.2 Capstone project." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/capstone/capstone-project)
*The source lesson this page adapts.*
:::
