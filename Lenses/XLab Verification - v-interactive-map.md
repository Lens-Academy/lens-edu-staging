---
id: '70ee83e3-ccaa-4130-a72f-8a4310acc919'
title: "Geographic supply-chain map"
tldr: "One Dutch company builds every EUV machine on Earth; one island fabricates about 90 percent of leading-edge logic; three firms make nearly all high-bandwidth memory. Follow a chip from sand to model through fourteen countries and see where the chain pinches to a few known addresses, and where it fans out into places a verifier cannot see."
summary_for_tutor: "XLab's interactive supply-chain map as a widget, with the reading around it on the page. The page opens with the geographic framing, then three headline stats (about 90 percent of leading-edge logic fabricated on one island, one company builds every EUV lithography machine, three firms make nearly all high-bandwidth memory), then the widget: a clickable world map of fourteen countries coloured by their primary supply-chain layer, a key of the six layers (chip design and EDA, equipment and materials, fabrication, memory HBM, packaging assembly and test, compute and models), a detail card, and the eight-stage pipeline from materials and wafers to trained models. Selecting a country opens its layers, two or three anchor facts, its actor roles and a 'Why it matters for verification' paragraph; selecting a layer in the key or a stage in the pipeline dims the map to that layer's countries and lists who would have to be in the room to verify it. Below the widget the page glosses the six actor roles (capability holder, chokepoint controller, information holder, enforcement authority, evasion pathway, victim/free-rider/beneficiary) and links ETO's Chip Explorer as optional further reading (Anatomy of a Chip), then closes with XLab's Notes and sources and a currency warning: concentration figures are 2021 to 2023 data. The widget has no finish condition; its saved state records which card is open and which countries, layers and stages the learner has opened. If the learner asks about a number, point them to the cited sources (CSET 2021; Sastry, Heim, Belfield et al. 2024; CNAS 2024) and remind them shares move while the structure has not."
tags: [wip]
duration_minutes: 15
---
#### Text
content::
The world map of AI compute: who makes what, where it flows, and where verification can grab hold, with a look inside the chip itself.

Where an actor sits constrains both what it can observe and what leverage an agreement can apply. Use the map to find the stages where production is concentrated in a few jurisdictions, then compare those chokepoints with the more diffuse parts of the chain where activity becomes harder to see.

#### Text
content::
\## The Compute Supply Chain

The whole story of this map is concentration. The chain crosses borders dozens of times, but the parts that matter for verification sit in a handful of countries, and each stage is a near-monopoly.

- **≈90%** of leading-edge logic is fabricated on one island
- **1** company builds every EUV lithography machine on Earth
- **3** firms make nearly all high-bandwidth memory

#### Widget
source:: [[../widgets/interactive-map]]

#### Text
content::
:::callout {title="Optional: Anatomy of a Chip" tone="neutral"}
[Anatomy of a Chip](https://chipexplorer.eto.tech/)

Explore the components inside an AI accelerator and connect them to the supply-chain stages shown above.
:::

#### Text
content::
:::callout {title="Start here" tone="neutral"}
The whole story of this map is concentration. The chain crosses borders dozens of times, but the parts that matter for verification sit in a handful of countries — and each stage is a near-monopoly.

Tap a country for its role, or isolate a layer to see exactly who would have to be in the room to verify it.
:::

#### Text
content::
\### Actor roles in this module

Every country card on the map is tagged with the actor roles that country plays in this module: capability holder, chokepoint controller, information holder, enforcement authority, evasion pathway, or victim, free-rider, beneficiary. The same state can hold a chokepoint, enforce the rules, and be a pathway around them.

#### Text
content::
A geographic chokepoint is potential leverage, not verification by itself. It matters only when some authority can require a declaration, obtain a record, inspect a facility, or impose a technical control there. Carry that distinction into [[../Lenses/XLab Verification - v-actor-edges|1.2.2]], which turns positions on the supply chain into evidence relationships: who can show a verifier something about whom.

\### Notes and sources

The stage-by-stage structure comes from CSET’s [“The Semiconductor Supply Chain”](https://cset.georgetown.edu/publication/the-semiconductor-supply-chain/) (2021), including its account of assembly and test as the part of the chain with the lowest barriers to entry. The concentration figures come from Sastry, Heim, Belfield et al., [“Computing Power and the Governance of Artificial Intelligence”](https://arxiv.org/abs/2402.08797) (2024): ASML at 100% of EUV lithography, TSMC at roughly 90% of sub-7 nm logic in the cited 2022 data, and several critical steps with fewer than three suppliers. High-bandwidth memory entered the US export-control perimeter in 2024; Fist, Burga and Chilukuri describe that expansion in [“Technology to Secure the AI Chip Supply Chain”](https://www.cnas.org/publications/reports/technology-to-secure-the-ai-chip-supply-chain-a-primer) (CNAS, 2024).

**Currency.** The concentration figures above use 2021–2023 data reported in 2021 and 2024 sources. Shares move; the structure (one EUV maker, one dominant leading-edge fab and a handful of clouds) has not. Re-verify a number before quoting it. The policy layer moves faster still: re-check dates, thresholds and bill status before citing. Later modules go deeper on the mechanisms named here.{>>{"author":"Elias's AI","timestamp":1788016632624}@@The italic "Content current as of July 2026 ... Congress.gov (H.R. 3447 / S. 1705) ..." paragraph is no longer in XLab's MDX; it was replaced by this Notes and sources section and Currency paragraph, copied from interactive-map.mdx.<<}

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Khan, Saif M., Alexander Mann, and Dahlia Peterson. *The Semiconductor Supply Chain: Assessing National Competitiveness*. Center for Security and Emerging Technology, Jan. 2021. [cset.georgetown.edu](https://cset.georgetown.edu/publication/the-semiconductor-supply-chain/)
*CSET's mapping of the semiconductor supply chain and where national chokepoints sit.*

Sastry, Girish, Lennart Heim, Haydn Belfield, et al. "Computing Power and the Governance of Artificial Intelligence." *arXiv*, Feb. 2024. [arxiv.org](https://arxiv.org/abs/2402.08797)
*The foundational survey of compute as a governance lever: why computing power is detectable, excludable, and quantifiable in ways algorithms and data are not.*

Fist, Tim, Tao Burga, and Vivek Chilukuri. *Technology to Secure the AI Chip Supply Chain: A Working Paper*. Center for a New American Security, 2024. [cnas.org](https://www.cnas.org/publications/reports/technology-to-secure-the-ai-chip-supply-chain-a-primer)
*Argues that export controls on AI chips are hard to enforce and easy to evade through shell companies, and proposes hardware-enabled mechanisms instead. Cited here for the fact that US controls now reach all chips using advanced high-bandwidth memory.*

XLab. "1.2.1 Geographic supply-chain map." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/policy-scoping/interactive-map)
*The source lesson this page adapts, including the map data reproduced above.*

ETO's Chip Explorer is linked inline above and has no entry in XLab's citation registry.
:::
