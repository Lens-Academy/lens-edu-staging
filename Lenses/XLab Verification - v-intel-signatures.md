---
id: '3e9c7610-3661-4ac9-b4ee-160932e9d3c9'
title: "2.3.1 Observable signatures of undeclared AI development"
tldr: {--{"author":"Elias's AI","timestamp":1788015683911}@@"Faithful alpha--}{++{"author":"Elias's AI","timestamp":1788015683911}@@"A covert training site leaks like a hidden factory: a footprint from orbit, a rooftop where snow never settles, a power line you cannot bury quietly, a GPU++} import {--{"author":"Elias's AI","timestamp":1788015683911}@@of XLab lesson 2.3.1 Observable signatures --}{++{"author":"Elias's AI","timestamp":1788015683911}@@spike, a hiring wave. Learn what each signature can honestly establish, its main caveat, and which ++}of {--{"author":"Elias's AI","timestamp":1788015683911}@@undeclared AI development."--}{++{"author":"Elias's AI","timestamp":1788015683911}@@seven collection disciplines picks it up."++}
summary_for_tutor: "Imported from XLab's {--{"author":"Elias's AI","timestamp":1788015683911}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed on XLab."--}{++{"author":"Elias's AI","timestamp":1788015683911}@@Verification curriculum; a ten-minute reading with no questions. It catalogues the observable signatures of undeclared frontier-AI development (overhead imagery, thermal, energy and the power grid, procurement and financial intelligence, open sources), each with what it establishes and its caveat, sorts them into four families (facility, resource-flow, organizational, operational), and ends with the collection map: seven intelligence disciplines (OSINT, HUMINT, SIGINT, CYBER, IMINT, GEOINT, MASINT) rendered as collapsed callouts with what each picks up and its characteristic limit. Keep the identify/resolve distinction in view: intelligence identifies, the regime resolves. If the learner asks about a signature, press the standing red-team question: would it survive an adversary who knows it is being watched? The Unfinished writing callout is XLab's own note about parts not yet built; do not invent that content."++}
tags: [wip]
duration_minutes: 10
---
#### Text
content::
Every mechanism so far has needed the monitored side to play along. Hardware
roots of trust (2.1) and provider reporting (2.2) share one failure mode: they
assume cooperation. This section covers the one evidence stream that works
uninvited — what undeclared frontier-AI development shows to a rival who is
simply watching, and what a watcher can honestly conclude from it.

The guiding question: **how can states identify possible undeclared frontier-AI
development without the monitored actor's cooperation?**

Two properties frame the layer. It works without permission, and it works
today — no new hardware, no new treaty machinery. Three literatures name the
same thing differently: Wasil et al. call it the national technical means (NTM)
category, *Six Layers* calls it Layer 6, and Scher and Thiergart call it the
national-intelligence building blocks.

Hold on to one distinction for the rest of the module. Intelligence
**identifies**; the regime **resolves**. A tip is not a finding.

\## The signature catalog

Each signature below carries the same three-part anatomy: what it tells a
verifier, what access it requires, and its main caveat. A standing red-team
question applies to every one — **would this signature survive an adversary who
knows it is being watched?**

\### Overhead imagery

Building footprint, electrical substations, cooling equipment, security
perimeter. Facilities above roughly 10,000 H100-equivalents typically occupy
substantial footprints with characteristic features (MIRI, Appendix D.3.5; a
2025 snapshot).

The historical hook: the IAEA only began using satellite imagery in the 1990s,
after failures to detect undeclared facilities under declared-facility
safeguards.

Caveats: imagery is unlikely to distinguish AI from non-AI datacenters —
cooling is the key differentiator — it struggles with industrial look-alikes,
and it can be defeated by underground or camouflaged construction.

\### Thermal

Waste heat, and the narrow temperature band of constant chip operation. Infrared
imaging, or heat inferred from rooftops where snow never accumulates in winter
(Baker, footnote 127). Sensing capability is actively improving — HotSat-class
commercial thermal satellites are the current example.

\### Energy and the power grid

The module's most quantitative tool and its most perishable. Measured energy
delivery can be converted into an approximate FLOP count, which makes large
unauthorized runs detectable from power draw — coarse violations only (Wasil et
al.). City-scale draw needs transmission lines visible even in public satellite
imagery, and burying them is itself a slow, satellite-visible construction
project (MIRI).

Against that, Scher and Thiergart rate power-grid analysis only **Medium**
feasibility — their sole non-High intelligence mechanism. Three reasons:

- Covert generation at the roughly 130 MW scale of a 100k-H100 cluster is
  plausible, comparable to military naval reactors.
- Around 500 datacenters worldwide exceed 10 MW — a large haystack (2024–25
  figures).
- Chip performance-per-watt improves about 1.6× a year, steadily shrinking the
  energy signature of any fixed quantity of compute.

Real-world colour: the xAI Memphis behind-the-meter gas turbines were surfaced
by aerial thermal imaging — the signature and the workaround in one case.

:::callout {title="Architecture changes the picture" tone="blue"}
Power consumption is architecture-dependent, so the same facility can change
signature without changing size. Scaling an existing architecture by adding
layers and shifting to a new architecture with a different compute profile
produce different curves, and inference and training draw differently again.
See Scher et al., *An International Agreement to Prevent the Premature Creation
of Artificial Superintelligence*, Appendix D — and connect it back to the
development picture from Module 1.
:::

\### Procurement, customs, and financial intelligence

The best real-case material in the module. The canonical indicator is a
GPU-import surge to a region far exceeding declared facilities' needs (Wasil et
al.), with the State Department's Blue Lantern end-use monitoring and FinCEN
suspicious-activity reporting as named institutional precedents.

Financial intelligence is rated **High** feasibility, under one year: covert AI
projects are very expensive and might leave a substantial money trail across raw
materials, chips, and datacenter components (Scher and Thiergart). Covert fabs
are detectable by monitoring the lithography-equipment supply chain — a
chokepoint of a few dozen capable facilities worldwide (Shavit §6). The Huawei
shadow-fab network surfaced in 2023 through exactly this channel.

Caveats: domestic chip manufacturing erodes customs tracking, and dual-use
purchases blur financial signals.

\### Open sources

Permits, filings, hiring, supplier disclosures, published interconnect and
power-purchase records. *Six Layers* classes open-source intelligence with the
supplemental mechanisms.

\## The four signature families

The cards above sort into four families, and it is worth being able to name
which one a given observation belongs to:

- **Facility signatures** — what the building is and looks like.
- **Resource-flow signatures** — power, water, chips, money moving in.
- **Organizational signatures** — who is hired, who contracts with whom.
- **Operational signatures** — what the site does, and when.

\## How we see traces

Those are the signatures. The disciplines below are the ways a watcher picks
them up — the collection side of the same picture.

#### Text
content::{--{"author":"Elias's AI","timestamp":1788015695399}@@ **Interactive exercise:** XLab's `collection-map` widget has--}{++{"author":"Elias's AI","timestamp":1788015695399}@@
\### The collection map

Seven ways a watcher sees. The disciplines split into two families: those that collect language, and those that collect physics. Open each one.

**Collects language**

:::callout {title="OSINT, Open-source intelligence" tone="neutral" collapse="closed"}
Anything published or otherwise available without concealment: permits, corporate filings, hiring, supplier disclosures, interconnect queues and power-purchase records.

**Picks up.** Organizational and facility signatures, before anything is built.

**Characteristic limit.** Six Layers classes it with the supplemental mechanisms — it rarely settles a question on its own.
:::

:::callout {title="HUMINT, Human intelligence" tone="neutral" collapse="closed"}
Collection from people — sources inside an organization, defectors, contractors, and anyone with placement and access.

**Picks up.** Intent and internal knowledge, which++} no {--{"author":"Elias's AI","timestamp":1788015695399}@@direct Lens equivalent yet. Complete--}{++{"author":"Elias's AI","timestamp":1788015695399}@@sensor reads.

**Characteristic limit.** Slow, unschedulable, and dependent on a person choosing to talk; it cannot be tasked the way a satellite can.
:::

:::callout {title="SIGINT, Signals intelligence" tone="neutral" collapse="closed"}
Interception of communications and electronic emissions — who is talking to whom, and sometimes what they said.

**Picks up.** Organizational and operational signatures.

**Characteristic limit.** The most sources-and-methods-sensitive stream, which is exactly why it is the hardest to share with a treaty verifier.
:::

:::callout {title="CYBER, Cyber intelligence" tone="neutral" collapse="closed"}
Collection from networks and systems themselves. MIRI's Definition 17 names it inside national technical means.

**Picks up.** Operational signatures — what a facility is actually running.

**Characteristic limit.** Its inclusion in a treaty definition is contested: read as legalized collection by one party and as a license to hack by the other.
:::

**Collects physics**

:::callout {title="IMINT, Imagery intelligence" tone="neutral" collapse="closed"}
Overhead and aerial imagery: building footprint, electrical substations, cooling plant, security perimeter.

**Picks up.** Facility signatures, and construction while++} it {++{"author":"Elias's AI","timestamp":1788015695399}@@is happening.

**Characteristic limit.** Unlikely to separate an AI datacenter from any other datacenter — cooling is the differentiator — and defeated by underground siting.
:::

:::callout {title="GEOINT, Geospatial intelligence" tone="neutral" collapse="closed"}
Imagery placed ++}in {++{"author":"Elias's AI","timestamp":1788015695399}@@geographic and temporal context — terrain, infrastructure, transmission lines, and change over time.

**Picks up.** Resource-flow signatures: the grid connection a large site needs.

**Characteristic limit.** Reads the surroundings well and ++}the {--{"author":"Elias's AI","timestamp":1788015695399}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/verification-infrastructure/intelligence-signatures). Its surrounding lesson text --}{++{"author":"Elias's AI","timestamp":1788015695399}@@activity inside poorly.
:::

:::callout {title="MASINT, Measurement and signature intelligence" tone="neutral" collapse="closed"}
The physics a facility emits — thermal, effluent, radar and geophysical signatures. Clark's technical-collection reference ++}is {--{"author":"Elias's AI","timestamp":1788015695399}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788015695399}@@the one on this.

**Picks up.** Waste heat and the narrow temperature band of constant chip operation; geophysical methods are already used against underground construction.

**Characteristic limit.** The signature it reads is shrinking: performance-per-watt improves about 1.6x a year, so a fixed quantity of compute emits less each year.
:::++}

#### Text
content::
\## Readings

- [Scher et al., *An International Agreement to Prevent the Premature Creation
  of Artificial Superintelligence*](https://arxiv.org/abs/2511.10783) —
  Appendix D, on architecture-dependent power consumption.
- [Wasil et al., *Verification methods for international AI
  agreements*](https://arxiv.org/abs/2408.16074) — selected pages.

{--{"author":"Elias's AI","timestamp":1788015704469}@@**Unfinished writing**

--}{++{"author":"Elias's AI","timestamp":1788015704469}@@:::callout {title="Unfinished writing" tone="amber"}
++}Two pieces this section is specified to carry are not built yet: the
interactive on AI data-centre power consumption built from
[Epoch's data-centre dataset](https://epoch.ai/data/ai-data-centers), with the
inference-versus-training comparison; and the predict-before-the-reveal beat on
each signature card ("what does this signature actually establish, and what is
its main caveat?"). The open-source card is also held short deliberately — a
dedicated treatment exists and should be distilled before it is finalised.{++{"author":"Elias's AI","timestamp":1788015704469}@@
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Scher, Aaron, David Abecassis, Peter Barnett, et al. "An International Agreement to Prevent the Premature Creation of Artificial Superintelligence." *arXiv*, Nov. 2025. [arxiv.org](https://arxiv.org/abs/2511.10783)
*MIRI's draft international agreement to prevent the premature creation of artificial superintelligence, the treaty text several lessons read against.*

Wasil, Akash R., Tom Reed, Jack William Miller, et al. "Verification Methods for International AI Agreements." *arXiv*, Aug. 2024. [arxiv.org](https://arxiv.org/abs/2408.16074)
*A survey of ten verification techniques for catching violations of international AI agreements, from unauthorized training runs to undeclared data centers.*++}

{--{"author":"Elias's AI","timestamp":1788015704469}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/intelligence-signatures)*--}{++{"author":"Elias's AI","timestamp":1788015704469}@@Epoch AI. "AI Data Centers." *Epoch AI*, continuously updated. [epoch.ai](https://epoch.ai/data/ai-data-centers)
*Epoch's continuously updated database of the world's largest AI data centers, built from satellite imagery and permitting records.*

XLab. "2.3.1 Observable signatures of undeclared AI development." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/intelligence-signatures)
*The source lesson this page adapts, including the collection map.*
:::++}
