---
id: '70ee83e3-ccaa-4130-a72f-8a4310acc919'
title: "1.2.1 Geographic supply-chain map"
tldr: {--{"author":"Elias's AI","timestamp":1788016569158}@@"Faithful alpha import--}{++{"author":"Elias's AI","timestamp":1788016569158}@@"One Dutch company builds every EUV machine on Earth; one island fabricates about 90 percent++} of {--{"author":"Elias's AI","timestamp":1788016569158}@@XLab lesson 1.2.1 Geographic supply-chain map."--}{++{"author":"Elias's AI","timestamp":1788016569158}@@leading-edge logic; three firms make nearly all high-bandwidth memory. Follow a chip from sand to model through fourteen countries and see where the chain pinches to a few known addresses, and where it fans out into places a verifier cannot see."++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788016569158}@@"Imported--}{++{"author":"Elias's AI","timestamp":1788016569158}@@"Reading-only lens reproducing XLab's interactive supply-chain map as text: six supply-chain layers with why each matters for verification, the eight-stage pipeline++} from {++{"author":"Elias's AI","timestamp":1788016569158}@@materials to trained models, and fourteen country cards (primary layer, layers, actor roles, anchor facts, why it matters for verification), plus a link to ETO's Chip Explorer. Closes with ++}XLab's {--{"author":"Elias's AI","timestamp":1788016569158}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed on XLab."--}{++{"author":"Elias's AI","timestamp":1788016569158}@@Notes and sources and a currency warning: concentration figures are 2021 to 2023 data. If the learner asks about a number, point them to the cited sources (CSET 2021; Sastry, Heim, Belfield et al. 2024; CNAS 2024) and remind them shares move while the structure has not."++}
tags: [wip]
duration_minutes: 15
---
#### Text
content::
The world map of AI compute: who makes what, where it flows, and where verification can grab hold — with a look inside the chip itself.

Where an actor sits constrains both what it can observe and what leverage an agreement can apply. Use the map to find the stages where production is concentrated in a few jurisdictions, then compare those chokepoints with the more diffuse parts of the chain where activity becomes harder to see.

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016617137}@@ **Interactive exercise:**--}{++{"author":"Elias's AI","timestamp":1788016617137}@@
\## The Compute Supply Chain

**Start here.** The whole story of this map is concentration. The chain crosses borders dozens of times, but the parts that matter for verification sit in a handful of countries — and each stage is a near-monopoly. Open a country for its role, or a layer to see exactly who would have to be in the room to verify it.

- **≈90%** of leading-edge logic is fabricated on one island
- **1** company builds every EUV lithography machine on Earth
- **3** firms make nearly all high-bandwidth memory

\### Supply chain layers

Colors on++} XLab's {--{"author":"Elias's AI","timestamp":1788016617137}@@`interactive-map` widget has --}{++{"author":"Elias's AI","timestamp":1788016617137}@@map show a country's primary layer. Most of the interesting countries sit in more than one.

| Layer | To verify at this layer, you'd need | Stat |
| --- | --- | --- |
| Chip design & EDA | Where capability is born. The architectures and the design software behind every advanced chip belong to a handful of US and UK firms, so rules can attach here before a single wafer exists. | 2 EDA firms |
| Equipment & materials | The narrowest chokepoint in the chain. A few firms in three allied countries build the tools and supply the chemistry every advanced fab depends on. | EUV: 1 company |
| Fabrication | Nearly all frontier chips are made in a handful of known facilities. Few sites, known addresses, hard to hide — which is exactly what makes a verification regime imaginable. | ≈90% → 1 island |
| Memory (HBM) | No high-bandwidth memory, ++}no {--{"author":"Elias's AI","timestamp":1788016617137}@@direct Lens equivalent yet. Complete --}{++{"author":"Elias's AI","timestamp":1788016617137}@@AI accelerator. HBM comes from three firms in two countries — a second countable chokepoint stacked right next to the first. | 3 firms, 2 countries |
| Packaging, assembly & test | Where chips become products and fan out into the world — and where they can slip out of sight. Transshipment and diversion risk lives in this layer. | the evasion surface |
| Compute & models | What the rules are ultimately about. Frontier-scale data centers are big, hot, and power-hungry — easy to find, harder to audit. The models inside them are hardest of all. | easy to find, hard to audit |

\### The pipeline · sand to model

Upstream · concentrated · most verifiable → downstream · diffuse · hardest to verify.

1. **Materials & wafers** (Equipment & materials). *Japan dominates photoresists and silicon wafers. An advanced fab without them stalls in months.* Shin-Etsu, SUMCO and specialist chemical suppliers occupy quieter upstream bottlenecks than the equipment makers, but advanced fabrication still depends on them.
2. **Design & EDA** (Chip design & EDA). *Two US firms control the design software; the architectures are US and UK. Capability starts as files.* NVIDIA, AMD, Huawei and other designers determine whether accelerators include attestation, metering or location features; Synopsys and Cadence supply the EDA software used to make those designs real. They comply with controls while lobbying against rules that raise costs or cut sales.
3. **Equipment** (Equipment & materials). *100% of EUV lithography comes from one Dutch company built around German optics.* ASML, Applied Materials and Tokyo Electron build the machines without which no leading-edge chip exists. Their customer base is small and highly visible, and they know which fabs receive each system.
4. **Fabrication** (Fabrication). *Roughly 90% of leading-edge logic is made on one island, mostly by one company.* TSMC, Samsung and Intel turn designs into physical chips and retain the production and customer records of what was made, how many and for whom. Their compliance sits between US rules and Chinese customers.
5. **Memory (HBM)** (Memory). *Three firms in two countries. No HBM, no accelerator.* SK Hynix, Samsung and Micron make the high-bandwidth memory beside every frontier accelerator, creating another small set of producers through which the chain must pass. The Korean firms also balance US controls against substantial exposure to China.
6. **Packaging & test** (Packaging, assembly & test). *Where chips fan out into products — and where diversion risk begins.* Advanced-packaging lines such as TSMC's CoWoS remain concentrated enough for chips to be counted. Ordinary assembly-and-test firms are more numerous, have the lowest barriers to entry in the chain and are largely absent from policy debates.
7. **Data centers** (Compute & models). *Gigawatt facilities visible from space: easy to find, harder to audit.* AWS, Microsoft Azure, Google Cloud, Oracle, Alibaba and specialists such as CoreWeave sit between customers and machines. Their logs, billing and telemetry make them natural monitors, and they can interrupt a job, but reseller chains and mislabeled workloads weaken what they can attribute to a customer.
8. **Trained models** (Compute & models). *A handful of labs — but what happens inside them is the hardest thing of all to verify.* OpenAI, Anthropic, Google DeepMind, Meta, xAI and their Chinese peers hold the fullest account of what they trained and evaluated. They can report, hide trade secrets, overstate precautions or benefit from a rival's restraint. Millions of downstream deployers reveal what models can do, while resellers, contractors and front companies can break the link between a named customer and an activity.

\### The countries

Every country card is tagged with the actor roles it plays in this module: capability holder, chokepoint controller, information holder, enforcement authority, evasion pathway, or victim, free-rider, beneficiary. The same state can hold a chokepoint, enforce the rules, and be a pathway around them.

:::callout {title="United States" tone="neutral" collapse="closed"}
*Primary layer: Chip design & EDA. Also: Equipment & materials, Fabrication, Memory (HBM), Compute & models. Roles: capability holder, chokepoint controller, information holder, enforcement authority.*

- NVIDIA and AMD design the accelerators; Synopsys and Cadence control the chip-design software (EDA) nearly everyone uses
- Applied Materials, Lam Research, and KLA build fab equipment; Micron makes HBM; Intel and new TSMC Arizona fabs bring some leading-edge production home
- Hyperscalers run the largest GPU fleets; frontier labs — OpenAI, Anthropic, Google — train the models

**Why ++}it {++{"author":"Elias's AI","timestamp":1788016617137}@@matters for verification.** Holds the design, software, and cloud levers, and writes the export rules (BIS). In any two-way international regime, it is also the actor everyone else would need to verify, while the same machinery could constrain its lead and its own firms.
:::

:::callout {title="China" tone="neutral" collapse="closed"}
*Primary layer: Compute & models. Also: Fabrication, Memory (HBM). Roles: capability holder, evasion pathway.*

- DeepSeek and other labs train frontier-class models; a House committee concluded DeepSeek used export-restricted NVIDIA chips
- SMIC pushes 7nm-class fabrication under sanctions; CXMT and YMTC build a domestic memory industry
- Reporting suggests over $1B of controlled chips were smuggled ++}in {++{"author":"Elias's AI","timestamp":1788016617137}@@during a single three-month stretch

**Why it matters for verification.** The hardest test for any regime: ++}the {--{"author":"Elias's AI","timestamp":1788016617137}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/interactive-map). --}{++{"author":"Elias's AI","timestamp":1788016617137}@@actor current rules try to exclude, and the counterparty a future agreement would have to verify without trust. It reads on-chip controls and inspections as surveillance and containment.
:::

:::callout {title="Taiwan" tone="neutral" collapse="closed"}
*Primary layer: Fabrication. Also: Packaging, assembly & test. Roles: chokepoint controller, information holder.*

- TSMC fabricates roughly 90% of leading-edge logic — including every NVIDIA AI accelerator
- ++}Its {--{"author":"Elias's AI","timestamp":1788016617137}@@surrounding lesson text --}{++{"author":"Elias's AI","timestamp":1788016617137}@@CoWoS advanced-packaging capacity gates how many accelerators exist at all

**Why it matters for verification.** Nearly every frontier chip passes through a few known facilities. TSMC's customer records are a verification asset; the concentration makes Taiwan both the system's tightest physical chokepoint and a strategic point of failure it does not control.
:::

:::callout {title="South Korea" tone="neutral" collapse="closed"}
*Primary layer: Memory (HBM). Also: Fabrication. Roles: chokepoint controller, capability holder.*

- SK Hynix and Samsung supply most of the world's HBM — the stacked memory sitting beside every AI accelerator
- US export controls extended to HBM in Dec 2024; Korean fabs in China now run on annually renewed licenses

**Why it matters for verification.** Accelerators cannot ship without HBM. This second countable chokepoint sits inside a state balancing export exposure to China against alliance pressure from the United States.
:::

:::callout {title="Japan" tone="neutral" collapse="closed"}
*Primary layer: Equipment & materials. Roles: chokepoint controller.*

- Tokyo Electron, Nikon, and Canon build critical fab equipment
- Near-monopolies in materials: photoresists, silicon wafers (Shin-Etsu, SUMCO), specialty gases

**Why it matters for verification.** Joined the US and the Netherlands in aligning equipment export controls in 2023. Materials monopolies are quiet leverage: an advanced fab stalls within months without Japanese chemistry, while Japan faces pressure from both sides of the US-China rivalry.
:::

:::callout {title="Netherlands" tone="neutral" collapse="closed"}
*Primary layer: Equipment & materials. Roles: chokepoint controller, information holder.*

- ASML is the world's only maker of EUV lithography machines, required for every leading-edge chip
- Only a few hundred EUV systems exist; each ++}is {--{"author":"Elias's AI","timestamp":1788016617137}@@preserved --}{++{"author":"Elias's AI","timestamp":1788016617137}@@tracked and serviced by ASML for its whole life

**Why it matters for verification.** The cleanest chokepoint in the entire chain: one company, one country, machines too large and too rare to hide. The Netherlands is a small state carrying outsized weight in the 2023 equipment-control alignment.
:::

:::callout {title="United Kingdom" tone="neutral" collapse="closed"}
*Primary layer: Chip design & EDA. Also: Compute & models. Roles: capability holder, information holder.*

- Arm's architecture sits inside most of the world's chips, including NVIDIA's Grace CPUs
- Google DeepMind; the AI Security Institute pioneered government evaluation of frontier models

**Why it matters for verification.** A standards and evaluations power. Part of what any verification regime would check — the evals — is being defined ++}here.{++{"author":"Elias's AI","timestamp":1788016617137}@@
:::

:::callout {title="Germany" tone="neutral" collapse="closed"}
*Primary layer: Equipment & materials. Also: Fabrication. Roles: chokepoint controller.*

- Zeiss builds the precision optics at the heart of every ASML EUV machine
- TSMC's first European fab is rising in Dresden

**Why it matters for verification.** The Dutch EUV monopoly is really a Dutch-German stack: two countries inside one machine. Both would sit at any verification table.
:::

:::callout {title="Singapore" tone="neutral" collapse="closed"}
*Primary layer: Compute & models. Also: Packaging, assembly & test. Roles: evasion pathway, information holder.*

- Major data-center, finance, and logistics hub for the region
- Feb 2025: three men charged with fraud over servers with NVIDIA chips declared for Malaysia — reportedly ~$390M worth

**Why it matters for verification.** Where paper trails and physical trails diverge. A large share of chip billing routes through Singapore entities, which makes it the know-your-customer pressure point.
:::

:::callout {title="Malaysia" tone="neutral" collapse="closed"}
*Primary layer: Packaging, assembly & test. Also: Compute & models. Roles: evasion pathway, enforcement authority.*

- Penang hosts one of the world's largest chip assembly-and-test clusters; Johor is in a GPU data-center boom
- Since July 2025, requires strategic trade permits for export, transshipment, or transit of US-origin AI chips

**Why it matters for verification.** Transshipment risk and an enforcement experiment in one place: named as a routing country in US smuggling cases, now building its own permit regime.
:::

:::callout {title="Vietnam" tone="neutral" collapse="closed"}
*Primary layer: Packaging, assembly & test. Roles: evasion pathway.*

- Intel's largest assembly-and-test plant operates near Ho Chi Minh City
- Packaging investment is growing as supply chains diversify

**Why it matters for verification.** Every new assembly hub widens the surface a tracking regime has to cover. Diversification is resilience for industry — and dispersion for verifiers.
:::

:::callout {title="Thailand" tone="neutral" collapse="closed"}
*Primary layer: Packaging, assembly & test. Also: Compute & models. Roles: evasion pathway.*

- Named alongside Malaysia as a routing country in the Nov 2025 US smuggling indictment
- Growing assembly, test, and data-center investment

**Why it matters for verification.** A live piece of the evasion map: restricted chips moved through third countries to obscure their true destination — exactly what location verification is meant to catch.
:::

:::callout {title="United Arab Emirates" tone="neutral" collapse="closed"}
*Primary layer: Compute & models. Roles: victim, free-rider, beneficiary; capability holder.*

- G42 anchors national AI ambitions
- A multi-gigawatt US-partnered AI campus in Abu Dhabi was announced in 2025 under a bilateral compute deal

**Why it matters for verification.** The live experiment in compute diplomacy: access to US chips in exchange for security conditions. Whether those conditions are verifiable is the open question.
:::

:::callout {title="Saudi Arabia" tone="neutral" collapse="closed"}
*Primary layer: Compute & models. Roles: victim, free-rider, beneficiary.*

- HUMAIN launched in 2025 with major NVIDIA and AMD agreements
- Gigawatt-scale data-center plans tied to sovereign investment

**Why it matters for verification.** The same experiment as the UAE: compute-for-conditions deals — which only mean something if the conditions can actually be checked.
:::

\### Anatomy of a Chip

Explore the components inside an AI accelerator and connect them to the supply-chain stages shown above: [ETO Chip Explorer](https://chipexplorer.eto.tech/).{>>{"author":"Elias's AI","timestamp":1788016617137}@@Native reproduction of XLab's interactive-map widget data (src/lib/verification/data/interactive-map.ts): layers, pipeline, country cards, stats and chip-explorer link. The world map itself is an SVG drawn from that data at runtime with no static image in xlab/public, so the geographic picture is not reproduced; the data behind it is.<<}++}

#### Text
content::
A geographic chokepoint is potential leverage, not verification by itself. It matters only when some authority can require a declaration, obtain a record, inspect a facility, or impose a technical control there. Carry that distinction into 1.2.2, which turns positions on the supply chain into evidence relationships: who can show a verifier something about whom.

_Content current as of July 2026. The policy layer of this field moves monthly — re-verify dates, thresholds, and bill status before citing. Key sources: Congress.gov (H.R. 3447 / S. 1705), BIS export control rules, EU AI Act Art. 51, CSIS, CRS R48642. Later modules go deeper on every mechanism named here._

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/policy-scoping/interactive-map)*
