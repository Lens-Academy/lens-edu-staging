---
title: "How AI Chips Are Made"
author:
  - "Yashvardhan Sharma"
source_url: "https://chipsupplychain.org/"
published: 2026-09-28
created: 2026-09-28
accessed: 2026-09-28
llm-review:
  date: 2026-09-28
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-09-28
    kind: "live"
description: "The AI chip supply chain, stage by stage: who makes each part, how concentrated each stage is, and what a substitute would cost. Every stage has a 3D specimen beside the text."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

![](https://chipsupplychain.org/print-title.png)

Every stage of the supply chain, and who controls it.

Yashvardhan Sharma with Claude

The Chain: seventeen chapters.

Printed from chipsupplychain.org · Updated 27 September 2026

## How to read a chapter ^how-to-read-a

Each of the fifteen stage chapters opens with a chokepoint card.

-   **Concentration.** How many firms credibly supply this stage: Extreme, High, Moderate or Low.
-   **Substitutability.** How hard it would be for a well-funded state or firm to build an alternative: Easy, Moderate, Hard or Very hard, rated against four tests.
-   **Price or market size.** What one unit costs, or what the stage earns in a year.

The card also gives where China and the United States stand. The chapters run in process order.

[Download the chain as a PDF](https://chipsupplychain.org/chip-supply-chain-the-chain.pdf)

## Contents ^contents

{--{"author":"James's AI","timestamp":1790593402681}@@17--}{++{"author":"James's AI","timestamp":1790593402681}@@1. [[#^chip-design-eda-and|Chip Design, EDA and IP]]
2. [[#^silicon-and-wafers|Silicon and Wafers]]
3. [[#^chemicals-gases-and-photoresist|Chemicals, Gases and Photoresist]]
4. [[#^lithography|Lithography]]
5. [[#^photomasks-and-pellicles|Photomasks and Pellicles]]
6. [[#^deposition-and-etch|Deposition and Etch]]
7. [[#^metrology-and-inspection|Metrology and Inspection]]
8. [[#^transistors-and-the-front|Transistors and the Front End]]
9. [[#^foundries-and-fabs|Foundries and Fabs]]
10. [[#^memory-and-hbm|Memory and HBM]]
11. [[#^advanced-packaging|Advanced Packaging]]
12. [[#^substrates-and-pcbs|Substrates and PCBs]]
13. [[#^test-and-assembly|Test and Assembly]]
14. [[#^systems-and-networking|Systems and Networking]]
15. [[#^data-centers-and-power|Data Centers and Power]]
16. [[#^the-economics-of-ai|The Economics of AI Chips]]
17.++} [[#^geopolitics|Geopolitics]]

## Chip Design, EDA and IP ^chip-design-eda-and

The cheapest stage in the chain to fund and one of the most concentrated. Three software firms sell the tools used to design every leading-edge AI accelerator.

{--{"author":"James's AI","timestamp":1790593752529}@@1,683--}{++{"author":"James's AI","timestamp":1790593752529}@@_1,683++} words / 7 {--{"author":"James's AI","timestamp":1790593752529}@@minSpecimen:--}{++{"author":"James's AI","timestamp":1790593752529}@@min · Interactive 3D Specimen:++} die floorplan{++{"author":"James's AI","timestamp":1790593752529}@@ (only on the live site: [open this chapter on chipsupplychain.org](https://chipsupplychain.org/#design-and-eda))_++}

In plain terms

Chip design turns an idea for a new chip into a complete blueprint. A chip holds billions of transistors, tiny electrical switches, and the blueprint fixes where each one sits and how it is wired to the others. The chip works in ticks, and a signal has to cross those wires within one tick, less than a billionth of a second. Software from three companies, Synopsys, Cadence and Siemens, lays out a plan like that, checks it and signs it off, and a chip factory accepts only designs that have passed those tools. The factory prints each layer of the design onto silicon through a stencil, and changing the plan after that costs a fresh set of stencils and several months. Withhold the software and no new chip can be designed.

### In short ^in-short

Three vendors sell every complete design flow used at the leading edge [3](https://newsletter.semianalysis.com/p/eda-market-primer). Design is cheap next to what it commits: tens of millions of dollars of engineering and masks decide what tens of billions of dollars of factory capacity will make [1](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor). It is the control a government can impose fastest, and the one China is closest to neutralizing, though CSET still finds no complete domestic flow [17](https://cset.georgetown.edu/article/semiconductors-more-u-s-leverage-more-bad-news-for-beijing-part-3/). The largest buyers now design their own parts, with Broadcom doing the implementation and the buyer's name on the product [11](https://investors.broadcom.com/news-releases/news-release-details/openai-and-broadcom-announce-strategic-collaboration-deploy-10).

Concentration: **Extreme**

Substitutability: **Hard**. Only three complete sets of chip design software exist, and a fourth would have to be written from nothing and approved by a foundry.

Price or market size: **A 3 nm photomask set costs about $40M, and startups have designed and made a 7 nm chip for $50-75M**

Who leads

-   {--{"author":"James's AI","timestamp":1790593756681}@@USSynopsys--}{++{"author":"James's AI","timestamp":1790593756681}@@US · **Synopsys**:++} $7.05B revenue in the fiscal year ended 31 October 2025, Ansys included from July; 90%+ of the timing-signoff market
-   {--{"author":"James's AI","timestamp":1790593757544}@@USCadence--}{++{"author":"James's AI","timestamp":1790593757544}@@US · **Cadence**:++} $5.30B revenue in calendar 2025; 55-60% of the hardware emulator market
-   {--{"author":"James's AI","timestamp":1790593758261}@@DESiemens EDA--}{++{"author":"James's AI","timestamp":1790593758261}@@DE · **Siemens EDA**:++} $2.2-2.5B revenue in 2025; 85%+ of physical verification, the final layout check
-   {--{"author":"James's AI","timestamp":1790593759094}@@GBArm--}{++{"author":"James's AI","timestamp":1790593759094}@@GB · **Arm**:++} About 50% of processor compute at the top cloud firms, fiscal 2026
-   {--{"author":"James's AI","timestamp":1790593760055}@@USBroadcom--}{++{"author":"James's AI","timestamp":1790593760055}@@US · **Broadcom**:++} $16.7B of AI chip revenue in the third quarter of fiscal 2026

Where it is made

-   {--{"author":"James's AI","timestamp":1790593760979}@@USUnited States--}{++{"author":"James's AI","timestamp":1790593760979}@@US · **United States**:++} Synopsys, Cadence, Broadcom, Marvell, Nvidia, AMD; Siemens EDA's main sites
-   {--{"author":"James's AI","timestamp":1790593761630}@@GBUnited Kingdom--}{++{"author":"James's AI","timestamp":1790593761630}@@GB · **United Kingdom**:++} Arm processor and interconnect designs, licensed from Cambridge
-   {--{"author":"James's AI","timestamp":1790593762443}@@TWTaiwan--}{++{"author":"James's AI","timestamp":1790593762443}@@TW · **Taiwan**:++} Alchip, Global Unichip and MediaTek: design services that carry a chip to the factory
-   {--{"author":"James's AI","timestamp":1790593762737}@@ILIsrael--}{++{"author":"James's AI","timestamp":1790593762737}@@IL · **Israel**:++} Annapurna Labs, the AWS design house behind Trainium and Graviton
-   {--{"author":"James's AI","timestamp":1790593763610}@@INIndia--}{++{"author":"James's AI","timestamp":1790593763610}@@IN · **India**:++} Nearly 20% of the world's chip design engineers, on the Indian government's count

Why substitution is slow

Three complete sets of chip design software exist today, and tools from one set cannot be combined with tools from another. The foundry that makes the chip approves exact versions of each tool. It accepts the check that every signal arrives on time only from the tool it has approved for that check. A newcomer would have to write a fourth set from nothing. It would then spend five to ten years finding the rare ways a chip can fail, which the approved tools already catch. CSET at Georgetown University judges that Chinese design tools cannot yet handle designs for the newest chips.

**Where China stands**

China designs its own AI accelerators, but Huawei's best, the Ascend 950, delivers about half the computing performance of Nvidia's H100 from 2022, on Epoch AI's estimate. CSET at Georgetown University judges that Chinese design software cannot yet handle the newest chips. The US government stopped sales of American and German design software to China for five weeks in 2025, then allowed them again.

**Where the US stands**

The United States has the two largest design-software vendors and the leading custom-chip design houses. Siemens EDA is German-owned, but the American technology inside it still needs US export licenses.

Design is the only stage in this chain with no factory, and the one a foreign government can shut off fastest. In 2025 one did. For five weeks, every Chinese chip designer lost the software that turns a design into something a factory can print.

### How it works ^how-it-works

Design runs in five stages, each one's output the next one's input, all of it in software.

-   **Architecture.** Engineers fix the shape of the chip: how wide the block that multiplies numbers is, how much fast on-chip memory sits beside it, how many high-bandwidth memory stacks line the edges. The output is a plan.
-   **RTL.** Engineers write the plan as register-transfer-level code, RTL, in the hardware language SystemVerilog. A register is a small store on the chip that holds one number, and the clock is the tick that moves every register forward together. The code says what every register holds on every tick, and the output is a text description of the whole chip.
-   **Verification.** The biggest team on most projects checks that the code does what the plan says. They run it in simulation, prove parts of it correct with mathematics, and load it into emulators, cabinets of reprogrammable chips that behave like the design, so the chip's own software can boot before any silicon exists.
-   **Physical design.** Software swaps each piece of the code for a logic cell, a small ready-made circuit the foundry has already proved it can make, then places the cells on the chip, wires them together and proves that every signal arrives in time.
-   **Tape-out.** The handover. Software turns the placed layout into pattern files for the mask shop. First it pre-distorts each shape so that it prints as drawn, which is optical proximity correction; then it cuts the layout into the files a mask writer reads, which is mask data preparation.

All that checking exists because a mistake costs a whole new mask set. One set costs more than $1 million at 28 nm, more than $10 million at 7 nm and about $40 million at 3 nm, and a whole leading-edge chip has gone from design to tape-out on TSMC 7 nm for $50 million to $75 million, everything included [1](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor). The nanometer labels name generations of the process, each finer than the last, and no longer measure anything.

**Chart:** What one photomask set costs, by node ($M). The 28 nm and 7 nm figures are minimums ($M)

28 nm 1 $M 7 nm 10 $M 3 nm 40 $M

Source: [SemiAnalysis, The Dark Side of the Semiconductor Design Renaissance, July 2022](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor)

### Variants and trade-offs ^variants-and-trade-offs

#### Merchant GPU versus custom ASIC ^merchant-gpu-versus-custom

Nvidia designs Blackwell once and sells it to everyone, so the buyer gets mature software and a resale market. A custom accelerator, an ASIC built for one company's own workload, is narrower and tuned to that one workload. Google's seventh-generation tensor processing unit, Ironwood, carries 192 GB of memory per chip, six times its predecessor's, and delivers twice the performance per watt [2](https://blog.google/innovation-and-ai/infrastructure-and-cloud/google-cloud/ironwood-tpu-age-of-inference/).

#### The EDA flow ^the-eda-flow

Three complete flows exist, and they do not mix. A team commits to one vendor's set of tools because the foundry certifies its reference recipes against specific tool versions, and timing signed off in one tool is not accepted in another. Synopsys alone holds more than 90 percent of static timing analysis, the check that proves a chip will run at its rated speed [3](https://newsletter.semianalysis.com/p/eda-market-primer), so inside each step of the flow the concentration is higher still.

**Chart:** Each leading vendor's share of its own design-software segment, 2025 (%)

Static timing (Synopsys PrimeTime) 90% Physical verification (Siemens Calibre) 85% Synthesis (Synopsys Design Compiler) 85% Emulation (Cadence Palladium) 58%

Source: [SemiAnalysis, EDA Market Primer, May 2026](https://newsletter.semianalysis.com/p/eda-market-primer)

#### Buy the IP or build it ^buy-the-ip-or

Design houses license the processor cores, the interface controllers and the blocks that drive high-bandwidth memory. Arm supplies most of the processor side: $4.92 billion of revenue, $2.61 billion of it royalties, and roughly 50 percent of processor compute at the top cloud firms in fiscal 2026 [4](https://newsroom.arm.com/news/arm-q4-fye26-results). The hardest block to buy is the memory interface, which has to hold its timing across thousands of microscopic solder bumps into a stacked memory die. RISC-V, the open instruction set that needs no license, handles the small control tasks on the chip, and Nvidia now uses it in every GPU [5](https://riscv.org/blog/shd-forecast-2026/).

#### Chiplets ^chiplets

The reticle limit, the largest area a scanner can print in one exposure, ended the single-die accelerator. Modern parts are chiplets, several smaller dies wired together, and the UCIe standard lets those links come from different vendors: version 3.0 adds 48 and 64 GT/s data rates [6](https://www.uciexpress.org/specifications). Broadcom's 3.5D XDSiP is the largest of these, packing more than 6,000 mm2 of silicon and 12 high-bandwidth memory stacks into one package [7](https://docs.broadcom.com/doc/3-5d-xdsip-platform-technology).

### Who makes it ^who-makes-it

Design software and licensed blocks were an $18 billion market in 2025, and Synopsys, Cadence and Siemens EDA took more than 85 percent of it, with no other vendor above 5 percent in any core category [3](https://newsletter.semianalysis.com/p/eda-market-primer).

Synopsys is the largest. Its own results put revenue at $7.054 billion for the fiscal year to 31 October 2025, with Ansys, bought that July, contributing $756.6 million [8](https://www.sec.gov/Archives/edgar/data/883241/000119312525314200/d29055dex991.htm). Cadence, whose year ends in December, took $5.30 billion in calendar 2025 [9](https://www.sec.gov/Archives/edgar/data/813672/000081367226000016/R115.htm). The two fiscal years do not line up, so any total for this market depends on which twelve months are counted and on how much of Ansys it includes.

**Chart:** Design software and licensed-block revenue share, 2025. Synopsys includes Ansys (%)

Synopsys **44%** Cadence **29%** Siemens EDA **13%** All others **14%**

%% validator-ignore-next-line --code article.block-repeated-nearby --reason source-provides-alternative-citation-formats %%
Source: [SemiAnalysis, EDA Market Primer, May 2026](https://newsletter.semianalysis.com/p/eda-market-primer)

Design services, where one firm turns another's specification into a manufacturable chip, are narrower again, and most of the announced AI deals are Broadcom's. It booked $16.7 billion of AI semiconductor revenue in the third quarter of fiscal 2026, up 221 percent [10](https://www.sec.gov/Archives/edgar/data/0001730168/000173016826000076/avgo-08022026x8kxex99.htm).

In October 2025 OpenAI and Broadcom said they would deploy 10 gigawatts of OpenAI-designed accelerators, with Broadcom turning the design into silicon and supplying the Ethernet networking around it [11](https://investors.broadcom.com/news-releases/news-release-details/openai-and-broadcom-announce-strategic-collaboration-deploy-10). In April 2026 Broadcom extended its Meta partnership to multiple gigawatts of MTIA, Meta's in-house chip, and the first 2 nm AI accelerator [12](https://investors.broadcom.com/news-releases/news-release-details/broadcom-announces-extended-partnership-meta-deploy-technology).

Below Broadcom and Marvell sit the Taiwanese houses that carry a customer's circuit list all the way to a finished mask set on TSMC's newest nodes; Alchip reported $992 million of revenue in 2025 [13](https://www.alchip.com/en/Investors/financials/). The engineers are spread across more countries than the firms, and India alone holds nearly 20 percent of the world's chip designers [14](https://www.pib.gov.in/PressReleasePage.aspx?PRID=2148393).

### The chokepoint ^the-chokepoint

In late May 2025 the US Bureau of Industry and Security, the agency that writes export licenses, told the design-software vendors to stop selling to China. Cadence got its letter on 23 May: exporting design software classified 3D991 and 3E991 to any party in China, or to a Chinese military end user anywhere, now needed a license [15](https://www.sec.gov/Archives/edgar/data/813672/000081367225000093/cdns-20250702.htm). Synopsys got its letter on 29 May and a rescinding letter on 2 July, after trade talks in which Washington eased technology restrictions [16](https://www.sec.gov/Archives/edgar/data/883241/000119312525155294/d80081d8k.htm).

Washington can impose this control alone, and at once. It also speeds up the substitution it was meant to prevent: Synopsys's China revenue fell from 16 percent of the total in fiscal 2024 to 12 percent in fiscal 2025 [3](https://newsletter.semianalysis.com/p/eda-market-primer).

CSET at Georgetown University finds that Chinese designers rely on US tools for all their chip designs, that US firms alone sell the full range of software a leading-edge chip needs, and that Chinese vendors cannot yet support designs at those nodes [17](https://cset.georgetown.edu/article/semiconductors-more-u-s-leverage-more-bad-news-for-beijing-part-3/). No domestic vendor has a certified, complete flow for a 5 nm-class accelerator, and the domestic flows match on features and fall short in the rare failure cases a foundry has already validated.

China can design an accelerator. It cannot finish one at the leading edge without foreign tools, or build what it designs without foreign equipment: SMIC's 7 nm capacity is small enough that Huawei has to choose between its phone chips and its AI chips [18](https://cset.georgetown.edu/publication/pushing-the-limits-huaweis-ai-chip-tests-u-s-export-controls/).

On Epoch AI's estimates, Huawei's flagship chip for 2026, the Ascend 950, delivers about half the computing performance of Nvidia's H100, which began shipping in 2022, and about a seventh of the B300's. Huawei will make about 1.5 million Ascend chips in 2026 against Nvidia's 5.9 million. With fewer and weaker chips, its total computing power will be less than 4 percent of Nvidia's. Epoch puts Huawei's chips three to four years behind Nvidia's until at least 2030, for three reasons. SMIC, which makes Huawei's chips, cannot pack transistors as densely as TSMC, which makes Nvidia's. Chinese memory makers are only starting to produce high-bandwidth memory. And Huawei's software for programming its chips is far less mature than Nvidia's [19](https://epoch.ai/publications/huaweis-roadmap-to-2031).

### Key evaluation criteria ^key-evaluation-criteria

-   **Flow completeness.** How many steps one vendor covers, from the first line of code to final signoff.
-   **Foundry certification.** Whether the foundry has validated that exact tool version against its reference flow and process design kit, the file set describing what the factory can print. Without that, the foundry refuses signoff.
-   **Verification throughput.** Simulation cycles and emulator capacity per day, which set the schedule more than anything else.
-   **IP availability at node.** Whether the licensed blocks, the processor cores, the high-speed serial links, PCIe and the memory interface, have been proven in silicon on that process.
-   **Design services depth.** Whether a partner can carry a customer's circuit list to a finished mask set on the newest node.
-   **Legal exposure.** How much of the flow is US-origin technology, and so subject to export licensing.

{--{"author":"James's AI","timestamp":1790593768774}@@Card--}{++{"author":"James's AI","timestamp":1790593768774}@@**Card++} 1 of {--{"author":"James's AI","timestamp":1790593768774}@@5Question--}{++{"author":"James's AI","timestamp":1790593768774}@@5 · Question**++}

What does chip design produce?

{--{"author":"James's AI","timestamp":1790593769607}@@Card--}{++{"author":"James's AI","timestamp":1790593769607}@@**Card++} 1 of {--{"author":"James's AI","timestamp":1790593769607}@@5Answer--}{++{"author":"James's AI","timestamp":1790593769607}@@5 · Answer**++}

A blueprint of the chip: where each transistor sits and how it is wired.

A chip factory builds only designs that have passed checks in approved design software. [[#^how-it-works|Reread: How it works]]

{--{"author":"James's AI","timestamp":1790593770357}@@Card--}{++{"author":"James's AI","timestamp":1790593770357}@@**Card++} 2 of {--{"author":"James's AI","timestamp":1790593770357}@@5Question--}{++{"author":"James's AI","timestamp":1790593770357}@@5 · Question**++}

Who sells the software used to design leading-edge chips?

{--{"author":"James's AI","timestamp":1790593770868}@@Card--}{++{"author":"James's AI","timestamp":1790593770868}@@**Card++} 2 of {--{"author":"James's AI","timestamp":1790593770868}@@5Answer--}{++{"author":"James's AI","timestamp":1790593770868}@@5 · Answer**++}

Three firms: Synopsys, Cadence and Siemens EDA.

Together they held more than 85 percent of the market in 2025. [[#^who-makes-it|Reread: Who makes it]]

{--{"author":"James's AI","timestamp":1790593771677}@@Card--}{++{"author":"James's AI","timestamp":1790593771677}@@**Card++} 3 of {--{"author":"James's AI","timestamp":1790593771677}@@5Question--}{++{"author":"James's AI","timestamp":1790593771677}@@5 · Question**++}

Why is that software hard to replace?

{--{"author":"James's AI","timestamp":1790593772314}@@Card--}{++{"author":"James's AI","timestamp":1790593772314}@@**Card++} 3 of {--{"author":"James's AI","timestamp":1790593772314}@@5Answer--}{++{"author":"James's AI","timestamp":1790593772314}@@5 · Answer**++}

A new vendor would have to write a complete set of tools from nothing and get a foundry to approve it.

Each foundry certifies its process against specific versions of the existing tools. [[#^the-chokepoint|Reread: The chokepoint]]

{--{"author":"James's AI","timestamp":1790593773326}@@Card--}{++{"author":"James's AI","timestamp":1790593773326}@@**Card++} 4 of {--{"author":"James's AI","timestamp":1790593773326}@@5Question--}{++{"author":"James's AI","timestamp":1790593773326}@@5 · Question**++}

Can China design the newest chips on its own software?

{--{"author":"James's AI","timestamp":1790593774095}@@Card--}{++{"author":"James's AI","timestamp":1790593774095}@@**Card++} 4 of {--{"author":"James's AI","timestamp":1790593774095}@@5Answer--}{++{"author":"James's AI","timestamp":1790593774095}@@5 · Answer**++}

Not yet.

CSET finds that Chinese design software cannot handle the newest chips. In 2025 the United States stopped these sales to China for five weeks. [[#^the-chokepoint|Reread: The chokepoint]]

{--{"author":"James's AI","timestamp":1790593775081}@@Card--}{++{"author":"James's AI","timestamp":1790593775081}@@**Card++} 5 of {--{"author":"James's AI","timestamp":1790593775081}@@5Question--}{++{"author":"James's AI","timestamp":1790593775081}@@5 · Question**++}

How far behind Nvidia is Huawei's best AI chip?

{--{"author":"James's AI","timestamp":1790593775713}@@Card--}{++{"author":"James's AI","timestamp":1790593775713}@@**Card++} 5 of {--{"author":"James's AI","timestamp":1790593775713}@@5Answer--}{++{"author":"James's AI","timestamp":1790593775713}@@5 · Answer**++}

About three to four years, on Epoch AI's estimate.

Huawei's flagship for 2026, the Ascend 950, delivers about half the computing performance of Nvidia's H100, which began shipping in 2022. [[#^the-chokepoint|Reread: The chokepoint]]

#### Five things to remember ^five-things-to-remember

-   Chip design turns an idea into a blueprint, and a factory builds only designs checked in approved software.
-   Synopsys, Cadence and Siemens EDA sell the software used to design every leading-edge chip.
-   A new vendor would have to write a complete set of tools and win a foundry's approval.
-   China designs its own AI chips but cannot yet design the newest ones on its own software.
-   Huawei's best AI chip trails Nvidia's by three to four years, on Epoch AI's estimate.

**Sources (19)**

1.  B [The Dark Side Of The Semiconductor Design Renaissance – Fixed Costs Soaring Due To Photomask Sets, Verification, and Validation](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor) SemiAnalysis · 24 July 2022
2.  A [Ironwood: The first Google TPU for the age of inference](https://blog.google/innovation-and-ai/infrastructure-and-cloud/google-cloud/ironwood-tpu-age-of-inference/) Google · 9 April 2025
3.  B [EDA Market Primer](https://newsletter.semianalysis.com/p/eda-market-primer) SemiAnalysis · 21 May 2026
4.  A [Arm delivers record-breaking quarter and full-year results](https://newsroom.arm.com/news/arm-q4-fye26-results) Arm · 6 May 2026
5.  A [Behind The Scenes of SHD Group's 2026 RISC-V Market Forecast](https://riscv.org/blog/shd-forecast-2026/) RISC-V International · 19 June 2026
6.  A [Specifications | UCIe Consortium](https://www.uciexpress.org/specifications) UCIe Consortium
7.  A [3.5D XDSiP Platform Technology](https://docs.broadcom.com/doc/3-5d-xdsip-platform-technology) Broadcom · 4 December 2024
8.  A [SYNOPSYS INC, Form 8-K current report for the period ended 2025-12-10 (8-K)](https://www.sec.gov/Archives/edgar/data/883241/000119312525314200/d29055dex991.htm) U.S. Securities and Exchange Commission (filing by SYNOPSYS INC) · 10 December 2025
9.  A [CADENCE DESIGN SYSTEMS INC, Form 10-K annual report for the period ended 2025-12-31 (financial statement R115)](https://www.sec.gov/Archives/edgar/data/813672/000081367226000016/R115.htm) U.S. Securities and Exchange Commission (filing by CADENCE DESIGN SYSTEMS INC) · 19 February 2026
10.  A [Broadcom Inc., Form 8-K current report for the period ended 2026-09-02 (8-K)](https://www.sec.gov/Archives/edgar/data/0001730168/000173016826000076/avgo-08022026x8kxex99.htm) U.S. Securities and Exchange Commission (filing by Broadcom Inc.) · 2 September 2026
11.  A [OpenAI and Broadcom announce strategic collaboration to deploy 10 gigawatts of OpenAI-designed AI accelerators](https://investors.broadcom.com/news-releases/news-release-details/openai-and-broadcom-announce-strategic-collaboration-deploy-10) Broadcom
12.  A [Broadcom Announces Extended Partnership with Meta to Deploy Technology to Support Multi-Gigawatts of Meta's Custom Silicon, MTIA](https://investors.broadcom.com/news-releases/news-release-details/broadcom-announces-extended-partnership-meta-deploy-technology) Broadcom · 14 April 2026
13.  A [Financials - Alchip](https://www.alchip.com/en/Investors/financials/) Alchip Technologies
14.  A [India’s Semiconductor Vision Gathers Momentum with 3nm Chip Design and Large-Scale Talent Development Initiatives](https://www.pib.gov.in/PressReleasePage.aspx?PRID=2148393) Press Information Bureau, Government of India
15.  A [CADENCE DESIGN SYSTEMS INC, Form 8-K current report for the period ended 2025-07-02 (8-K)](https://www.sec.gov/Archives/edgar/data/813672/000081367225000093/cdns-20250702.htm) U.S. Securities and Exchange Commission (filing by CADENCE DESIGN SYSTEMS INC) · 3 July 2025
16.  A [SYNOPSYS INC, Form 8-K current report for the period ended 2025-07-02 (8-K)](https://www.sec.gov/Archives/edgar/data/883241/000119312525155294/d80081d8k.htm) U.S. Securities and Exchange Commission (filing by SYNOPSYS INC) · 3 July 2025
17.  A [Semiconductors: More U.S. Leverage, More Bad News For Beijing (Part 3)](https://cset.georgetown.edu/article/semiconductors-more-u-s-leverage-more-bad-news-for-beijing-part-3/) Center for Security and Emerging Technology (CSET) · 25 October 2021
18.  A [Pushing the Limits: Huawei's AI Chip Tests U.S. Export Controls](https://cset.georgetown.edu/publication/pushing-the-limits-huaweis-ai-chip-tests-u-s-export-controls/) Center for Security and Emerging Technology (CSET) · 17 June 2024
19.  A [Will Huawei catch up to Nvidia by 2030?](https://epoch.ai/publications/huaweis-roadmap-to-2031) Epoch AI · 24 September 2026

## Silicon and Wafers ^silicon-and-wafers

China makes almost all of the world's polysilicon and almost none of the 300 mm wafers. Five firms in Japan, Taiwan, Germany and South Korea make the 300 mm wafer every AI accelerator starts on.

{--{"author":"James's AI","timestamp":1790593777407}@@1,424--}{++{"author":"James's AI","timestamp":1790593777407}@@_1,424++} words / 6 {--{"author":"James's AI","timestamp":1790593777407}@@minSpecimen:--}{++{"author":"James's AI","timestamp":1790593777407}@@min · Interactive 3D Specimen:++} boule and wafer{++{"author":"James's AI","timestamp":1790593777407}@@ (only on the live site: [open this chapter on chipsupplychain.org](https://chipsupplychain.org/#silicon-and-wafers))_++}

In plain terms

Every chip is built on a wafer, a thin round slice of silicon about 30 centimeters across that carries hundreds of chips at once. Making one starts with sand, which is silicon bound to oxygen. The sand is refined until, of every hundred billion atoms, fewer than one is anything other than silicon. The silicon is melted, a small seed crystal is lowered to the surface and drawn slowly back up, and the melt freezes onto it as one long cylinder, a single crystal with its atoms in one unbroken orderly pattern from end to end. Saws cut the cylinder into discs, and each disc is polished until its surface is flat to within a few atoms, right out to the edge. Only five companies in the world make these wafers to that standard, and none of them is American or Chinese.

### In short ^in-short-2

The wafer is a cheap input and a concentrated one: five firms and $11.4 billion of revenue sit under every leading-edge chip [5](https://www.siltronic.com/fileadmin/investorrelations/2026/Q1/20260429_Siltronic_InvestorPresentation__.pdf) [1](https://www.prnewswire.com/news-releases/semi-reports-2025-annual-worldwide-silicon-wafer-shipments-and-revenue-results-302683028.html). China's polysilicon dominance is real but in the wrong grade, and its 300 mm position is small [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). The epitaxial mix matters more than the square inches, because that is what AI demand buys and where the incumbents make money. The failed move to 450 mm showed that this stage of the chain changes over decades.

Concentration: **High**

Substitutability: **Moderate**. Five firms already make 300 mm wafers that fabs have approved, but a fab has to test and approve a new supplier separately for every chip it makes.

Price or market size: **The world wafer market was $11.4bn in 2025, on 12,973 million square inches shipped**

Who leads

-   {--{"author":"James's AI","timestamp":1790593780804}@@JPShin-Etsu Handotai--}{++{"author":"James's AI","timestamp":1790593780804}@@JP · **Shin-Etsu Handotai**:++} Largest supplier; the parent's electronics materials arm sold ¥750.3bn from April to December 2025
-   {--{"author":"James's AI","timestamp":1790593781770}@@JPSUMCO--}{++{"author":"James's AI","timestamp":1790593781770}@@JP · **SUMCO**:++} ¥409.7bn of 2025 net sales, but an ¥11.8bn loss
-   {--{"author":"James's AI","timestamp":1790593782565}@@TWGlobalWafers--}{++{"author":"James's AI","timestamp":1790593782565}@@TW · **GlobalWafers**:++} NT$60.6bn revenue in 2025
-   {--{"author":"James's AI","timestamp":1790593783260}@@KRSK Siltron--}{++{"author":"James's AI","timestamp":1790593783260}@@KR · **SK Siltron**:++} One of the five firms that supply the whole wafer market
-   {--{"author":"James's AI","timestamp":1790593784535}@@DESiltronic--}{++{"author":"James's AI","timestamp":1790593784535}@@DE · **Siltronic**:++} €1,346.7m revenue in 2025

Where it is made

-   {--{"author":"James's AI","timestamp":1790593786546}@@JPJapan--}{++{"author":"James's AI","timestamp":1790593786546}@@JP · **Japan**:++} Shin-Etsu and SUMCO crystal growth and polishing
-   {--{"author":"James's AI","timestamp":1790593787837}@@TWTaiwan--}{++{"author":"James's AI","timestamp":1790593787837}@@TW · **Taiwan**:++} GlobalWafers headquarters and plants
-   {--{"author":"James's AI","timestamp":1790593788891}@@DEGermany--}{++{"author":"James's AI","timestamp":1790593788891}@@DE · **Germany**:++} Siltronic Burghausen and Freiberg; Wacker semiconductor-grade polysilicon
-   {--{"author":"James's AI","timestamp":1790593789713}@@KRSouth Korea--}{++{"author":"James's AI","timestamp":1790593789713}@@KR · **South Korea**:++} SK Siltron, being sold to Doosan
-   {--{"author":"James's AI","timestamp":1790593790936}@@USUnited States--}{++{"author":"James's AI","timestamp":1790593790936}@@US · **United States**:++} Hemlock polysilicon in Michigan; GlobalWafers Sherman, Texas and St Peters, Missouri

Why substitution is possible

Five firms make 300 mm wafers good enough for the newest chips, so losing one leaves four. A new wafer plant can still be built: GlobalWafers of Taiwan spent $3.5 billion on a plant in Texas, the first wafer production line of its kind in the United States in over twenty years. The slow part is approval. A fab tests a new wafer supplier separately for each chip it makes, and each test runs for months. Supply contracts are also signed years ahead. Switching wafer suppliers therefore takes two to five years.

**Where China stands**

China made about 93 percent of the world's polysilicon in 2023, but 98 percent of it was solar grade, too impure for chips. It held under 1 percent of the 300 mm wafer market as of 2021, and it supplies only 12 percent of the wafers its own 300 mm fabs use.

**Where the US stands**

No American firm makes wafers in volume. Hemlock makes polysilicon in Michigan, and GlobalWafers of Taiwan took a CHIPS Act award of up to $406 million toward a $3.5 billion Texas plant that opened in May 2025.

The whole world market for silicon wafers came to $11.4 billion of revenue on 12,973 million square inches in 2025 [1](https://www.prnewswire.com/news-releases/semi-reports-2025-annual-worldwide-silicon-wafer-shipments-and-revenue-results-302683028.html). That is a small fraction of Nvidia's data center revenue, and every leading-edge chip behind it was built on one of these discs.

### How it works ^how-it-works-2

![](https://chipsupplychain.org/media/silicon-light-end.jpg)

From sand to wafer

Silicon starts as quartzite, a rock that is silicon bound to oxygen. An arc furnace melts it with carbon, and the carbon takes the oxygen away as gas, leaving rough silicon metal. Refiners turn the metal into a gas, trichlorosilane, and distill it, because the impurities boil at other temperatures and stay behind. The clean gas then flows over silicon filaments heated inside a bell jar. On the hot surface the gas breaks apart, its silicon settles onto the filaments, and over days the filaments thicken into gray rods of polysilicon, the Siemens process. Everything downstream is made from those rods. The same process serves solar cells and chips, but only the ultra-pure semiconductor grade is any use for chips [2](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-silicon.pdf), and the two grades are separate industries with separate suppliers.

A grower melts the polysilicon at about 1,420 degrees Celsius, hotter than lava, and pulls a single crystal out of it by the Czochralski method. The grower lowers a small seed crystal on the end of a rod to the surface of the melt and draws it back up, slowly turning. Silicon freezes onto the seed in the seed's own atomic pattern, and a cylinder grows beneath it, the ingot. The pull starts with a thin neck so that the flaws formed where the seed first touched the melt end in the neck and never reach the ingot. Boron or phosphorus stirred into the melt, a step called doping, sets how readily the wafer conducts and whether the current in it is carried by negative charges or positive ones.

A wire saw, a web of fine wire running through abrasive, slices the ingot into discs. The maker then laps each disc, grinding both faces flat between rotating plates, etches off the damaged surface with acid, and polishes it to a mirror with colloidal silica, a slurry of silica particles far too small to see. Epitaxial wafers get one more layer of near-perfect silicon grown on top at about 1,200 degrees Celsius [3](https://www.sumcosi.com/english/products/process/), still hot enough to glow orange, and almost every step throws material away.

### Variants and trade-offs ^variants-and-trade-offs-2

#### Prime versus epitaxial ^prime-versus-epitaxial

A prime wafer is a uniformly doped, front-polished single crystal: cheapest, and good enough for most memory and mature logic. An epitaxial wafer adds a thin, lightly doped, defect-controlled layer on top. The transistors live in that layer, so its quality sets the lowest leakage the chip can reach and its risk of latch-up, a parasitic short between power and ground. SEMI, the industry association, credits the 2025 rise in shipments to AI demand for advanced epitaxial wafers and high-bandwidth memory [1](https://www.prnewswire.com/news-releases/semi-reports-2025-annual-worldwide-silicon-wafer-shipments-and-revenue-results-302683028.html).

#### Silicon on insulator ^silicon-on-insulator

A buried layer of oxide, which is glass, separates a thin working layer of silicon from the bulk beneath, and Soitec's Smart Cut process makes nearly all of it [4](https://www.soitec.com/home/group). It matters for radio and low-power chips. AI GPUs run on plain epitaxial silicon.

### Who makes it ^who-makes-it-2

Siltronic's own map of the chain puts five major suppliers behind the whole wafer market [5](https://www.siltronic.com/fileadmin/investorrelations/2026/Q1/20260429_Siltronic_InvestorPresentation__.pdf). CSET at Georgetown names them: Shin-Etsu, SUMCO, GlobalWafers, Siltronic and SK Siltron, headquartered in Japan, Taiwan, Germany and South Korea [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf).

**Chart:** Silicon wafer market by supplier headquarters. Five firms, four countries, no US producer (%)

Japan **56%** Taiwan **16%** Europe **14%** South Korea **10%** China **4%** United States **0%**

Source: [CSET, The Semiconductor Supply Chain, January 2021](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf)

Their 2025 results split between an AI boom and a slump in the older, mature nodes.

-   **Shin-Etsu.** Its electronics materials arm sold ¥750.3 billion in the nine months to December 2025, on strong AI-related wafer demand [7](https://www.shinetsu.co.jp/wp-content/uploads/2025/07/20260127_con_E.pdf).
-   **SUMCO.** Sold ¥409.7 billion and still lost ¥11.8 billion, as operating profit fell from ¥36.9 billion to ¥1.3 billion while it added leading-edge 300 mm capacity and reorganized its weak 200 mm lines [8](https://www.sumcosi.com/english/pdf/ir/library/shareholders/27/pdf/nc_e_27.pdf).
-   **Siltronic.** Lost €77.9 million on €1,346.7 million of sales while spending €369.1 million on its Singapore fab [9](https://www.siltronic.com/en/press/press-releases/siltronic-ag-robust-business-performance-in-2025-demonstrates-resilience-despite-challenging-conditions.html).
-   **GlobalWafers.** NT$60.6 billion of revenue, down 3.24 percent in local currency [10](https://www.sas-globalwafers.com/en/gwc_news_en_20260303/).

Area shipped rose 5.8 percent in 2025 while revenue fell 1.2 percent [1](https://www.prnewswire.com/news-releases/semi-reports-2025-annual-worldwide-silicon-wafer-shipments-and-revenue-results-302683028.html). Wafers sell on multi-year agreements that fix price and volume years ahead, so a jump in demand does not change the price in the year it happens.

China made 1.50 million metric tons of polysilicon, the raw material, in 2023, about 93 percent of world output [11](https://pubs.usgs.gov/myb/vol3/2023/myb3-2023-china.pdf). Solar-grade material was 98 percent of that output and electronic-grade 2 percent [11](https://pubs.usgs.gov/myb/vol3/2023/myb3-2023-china.pdf), so almost none of it can go into a chip.

**Chart:** China's polysilicon output by grade, 2023. China made about 93% of the world's 1.5 million metric tons that year (%)

Solar-grade **98%** Electronic-grade **2%**

Source: [USGS Minerals Yearbook, China, 2023](https://pubs.usgs.gov/myb/vol3/2023/myb3-2023-china.pdf)

Siltronic sizes electronic-grade silicon at $1.4 billion, with five major suppliers, none of them Chinese: Wacker, Hemlock, OCI, Tokuyama and Mitsubishi [5](https://www.siltronic.com/fileadmin/investorrelations/2026/Q1/20260429_Siltronic_InvestorPresentation__.pdf).

Crystal growth and polishing sit in Japan, Taiwan, Germany and South Korea, with no major US-headquartered producer as of 2021 [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). GlobalWafers opened a $3.5 billion plant in Sherman, Texas in May 2025, the first production line of its kind built in the United States in over twenty years, and announced another $4 billion for phases three and four the same day [12](https://www.sas-globalwafers.com/en/gwc_news_en_20250516/). Washington had awarded it up to $406 million under the CHIPS incentives program [13](https://www.commerce.gov/news/press-releases/2024/12/biden-harris-administration-announces-chips-incentives-awards).

### The chokepoint ^the-chokepoint-2

China dominates polysilicon and has almost no share in wafers. As of 2021 Chinese firms held under 5 percent of the wafer market and under 1 percent of 300 mm [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). Chinese producers supplied 12 percent of the wafers consumed by China's own 300 mm fabs, against 18 percent at 200 mm and below [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf).

Leading-edge 300 mm wafers depend on know-how that was never written down and that is not built into any machine a rival could buy, and 300 mm carried 99.7 percent of world fab capacity at 45 nm and below as of 2021 [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). A fab has to qualify each new wafer source for every chip it makes, which takes quarters, while the contracts already in place run for years.

The last increase in wafer size, to 300 mm, happened in 2002 [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). Bigger discs make printing a bigger share of the processing cost: photolithography takes half the cost of processing a 300 mm wafer against a quarter of a 150 mm one [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). The attempt to move to 450 mm never reached production, and every leading-edge chip is still made on 300 mm.

One fatal defect ruins far more silicon on a GPU die that fills a whole printed field than on a small chip, and extreme-ultraviolet printing stays in focus over only a very small range of heights (see [[#^lithography|Lithography]]), so flatness has to hold at every point on the disc.

### Key evaluation criteria ^key-evaluation-criteria-2

-   **Grade.** Electronic against solar polysilicon separates a Chinese commodity market from a German, American, Japanese and Korean one; solar was 98 percent of China's 2023 output [11](https://pubs.usgs.gov/myb/vol3/2023/myb3-2023-china.pdf).
-   **Defect density** in the epitaxial layer. A big AI die loses more good silicon per defect than a small chip does, which is why AI demand shows up first in advanced epitaxial wafers [1](https://www.prnewswire.com/news-releases/semi-reports-2025-annual-worldwide-silicon-wafer-shipments-and-revenue-results-302683028.html).
-   **Flatness and nanotopography**, the fine ripple across the surface, because extreme-ultraviolet exposure stays in focus over only a very small range of heights, and that has to hold across a 300 mm wafer.
-   **Diameter**, where 300 mm carries every leading-edge node and 99.7 percent of capacity at 45 nm and below [6](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf).
-   **Contract structure**, since long-term agreements set price and volume years ahead and keep a jump in demand from moving the price.

{--{"author":"James's AI","timestamp":1790593798116}@@Card--}{++{"author":"James's AI","timestamp":1790593798116}@@**Card++} 1 of {--{"author":"James's AI","timestamp":1790593798116}@@4Question--}{++{"author":"James's AI","timestamp":1790593798116}@@4 · Question**++}

What is a wafer?

{--{"author":"James's AI","timestamp":1790593799677}@@Card--}{++{"author":"James's AI","timestamp":1790593799677}@@**Card++} 1 of {--{"author":"James's AI","timestamp":1790593799677}@@4Answer--}{++{"author":"James's AI","timestamp":1790593799677}@@4 · Answer**++}

A thin disc of pure silicon, about 30 centimeters across, that carries hundreds of chips.

It is sliced from a single crystal and polished flat to within a few atoms. [[#^how-it-works-2|Reread: How it works]]

{--{"author":"James's AI","timestamp":1790593801942}@@Card--}{++{"author":"James's AI","timestamp":1790593801942}@@**Card++} 2 of {--{"author":"James's AI","timestamp":1790593801942}@@4Question--}{++{"author":"James's AI","timestamp":1790593801942}@@4 · Question**++}

Who makes the wafers for leading-edge chips?

{--{"author":"James's AI","timestamp":1790593803252}@@Card--}{++{"author":"James's AI","timestamp":1790593803252}@@**Card++} 2 of {--{"author":"James's AI","timestamp":1790593803252}@@4Answer--}{++{"author":"James's AI","timestamp":1790593803252}@@4 · Answer**++}

Five firms, in Japan, Taiwan, Germany and South Korea.

They are Shin-Etsu, SUMCO, GlobalWafers, Siltronic and SK Siltron. None is American or Chinese. [[#^who-makes-it-2|Reread: Who makes it]]

{--{"author":"James's AI","timestamp":1790593804628}@@Card--}{++{"author":"James's AI","timestamp":1790593804628}@@**Card++} 3 of {--{"author":"James's AI","timestamp":1790593804628}@@4Question--}{++{"author":"James's AI","timestamp":1790593804628}@@4 · Question**++}

Why does switching wafer suppliers take years?

{--{"author":"James's AI","timestamp":1790593806036}@@Card--}{++{"author":"James's AI","timestamp":1790593806036}@@**Card++} 3 of {--{"author":"James's AI","timestamp":1790593806036}@@4Answer--}{++{"author":"James's AI","timestamp":1790593806036}@@4 · Answer**++}

A fab must test and approve a new supplier separately for every chip it makes.

The switch takes two to five years. [[#^the-chokepoint-2|Reread: The chokepoint]]

{--{"author":"James's AI","timestamp":1790593807452}@@Card--}{++{"author":"James's AI","timestamp":1790593807452}@@**Card++} 4 of {--{"author":"James's AI","timestamp":1790593807452}@@4Question--}{++{"author":"James's AI","timestamp":1790593807452}@@4 · Question**++}

China makes most of the world's polysilicon. Why does that give it little hold over chip wafers?

{--{"author":"James's AI","timestamp":1790593808622}@@Card--}{++{"author":"James's AI","timestamp":1790593808622}@@**Card++} 4 of {--{"author":"James's AI","timestamp":1790593808622}@@4Answer--}{++{"author":"James's AI","timestamp":1790593808622}@@4 · Answer**++}

Almost all of it is solar grade, too impure for chips.

In 2023, 98 percent of China's output was solar grade. Chinese firms held under 1 percent of the 300 mm wafer market in 2021. [[#^the-chokepoint-2|Reread: The chokepoint]]

#### Four things to remember ^four-things-to-remember

-   Every chip starts on a wafer, a polished disc of pure silicon about 30 centimeters across.
-   Five firms in Japan, Taiwan, Germany and South Korea make the wafers for leading-edge chips.
-   A fab needs two to five years to approve a new wafer supplier.
-   China makes most of the world's polysilicon, but almost all of it is too impure for chips.

**Sources (13)**

1.  A [SEMI Reports 2025 Annual Worldwide Silicon Wafer Shipments and Revenue Results](https://www.prnewswire.com/news-releases/semi-reports-2025-annual-worldwide-silicon-wafer-shipments-and-revenue-results-302683028.html) PR Newswire · 10 February 2026
2.  A [Mineral Commodity Summaries 2026](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-silicon.pdf) U.S. Geological Survey · 5 February 2026
3.  A [SUMCO, production processes page](https://www.sumcosi.com/english/products/process/) SUMCO
4.  A [Soitec | Key figures](https://www.soitec.com/home/group) Soitec
5.  A [FOUNDATION OF DIGITAL LIFE Investor Presentation](https://www.siltronic.com/fileadmin/investorrelations/2026/Q1/20260429_Siltronic_InvestorPresentation__.pdf) Siltronic · 29 April 2026
6.  A [The Semiconductor Supply Chain - Issue Brief](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf) Center for Security and Emerging Technology (CSET) · 21 January 2021
7.  A [Consolidated Financial Results for the First Three Quarters Ended December 31, 2025](https://www.shinetsu.co.jp/wp-content/uploads/2025/07/20260127_con_E.pdf) Shin-Etsu Chemical · 26 January 2026
8.  A [Note: This document has been translated from the Japanese original for reference purposes only. In the event of any](https://www.sumcosi.com/english/pdf/ir/library/shareholders/27/pdf/nc_e_27.pdf) SUMCO · 3 March 2026
9.  A [Siltronic AG: Robust business performance in 2025 demonstrates resilience despite challenging conditions](https://www.siltronic.com/en/press/press-releases/siltronic-ag-robust-business-performance-in-2025-demonstrates-resilience-despite-challenging-conditions.html) Siltronic · 27 August 2026
10.  A [GlobalWafers Reports Full Year 2025 Results - GlobalWafers Co., Ltd. All rights reserved.](https://www.sas-globalwafers.com/en/gwc_news_en_20260303/) GlobalWafers · 3 March 2026
11.  A [The Mineral Industry of China in 2020-2021](https://pubs.usgs.gov/myb/vol3/2023/myb3-2023-china.pdf) U.S. Geological Survey · 17 February 2026
12.  A [GlobalWafers America Officially Opens for Business - GlobalWafers Co., Ltd. All rights reserved.](https://www.sas-globalwafers.com/en/gwc_news_en_20250516/) GlobalWafers · 15 May 2025
13.  A [Biden-Harris Administration Announces CHIPS Incentives Awards with GlobalWafers to Support Domestic Production of Silicon Wafers](https://www.commerce.gov/news/press-releases/2024/12/biden-harris-administration-announces-chips-incentives-awards) U.S. Department of Commerce · 17 December 2024

## Chemicals, Gases and Photoresist ^chemicals-gases-and-photoresist

A few hundred chemicals separate a blank wafer from a working chip. Japan makes about four-fifths of the photoresist. Twice the supply of these materials has been restricted, and no fab stopped, because the countries affected stockpiled and developed substitutes instead.

{--{"author":"James's AI","timestamp":1790593811954}@@1,467--}{++{"author":"James's AI","timestamp":1790593811954}@@_1,467++} words / 6 {--{"author":"James's AI","timestamp":1790593811954}@@minSpecimen:--}{++{"author":"James's AI","timestamp":1790593811954}@@min · Interactive 3D Specimen:++} gas cabinet{++{"author":"James's AI","timestamp":1790593811954}@@ (only on the live site: [open this chapter on chipsupplychain.org](https://chipsupplychain.org/#chemicals-gases-and-photoresist))_++}

In plain terms

Photoresist is a coating that changes wherever light hits it. A machine spins a coat of it, thinner than a soap bubble, across the wafer. Light shines through a stencil onto the coat, and a liquid wash then takes away the parts the light reached. What remains is a pattern, and the next machine cuts that pattern into the wafer beneath, a step called etching. A few hundred other gases and liquids lay down layers, strip them off and clean the wafer between steps. All of them have to be clean to about one stray metal atom in every trillion. Each formula is approved for one factory and one product at a time, and a new supplier has to earn that approval from scratch, so a second source takes years. Nine tenths of the world's photoresist comes from Japan, and no factory can swap it out quickly.

### In short ^in-short-3

Photoresist is the most concentrated input at this stage: about 90 percent Japanese in 2021 and 78 percent in 2023 [3](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf) [4](https://www.meti.go.jp/policy/mono_info_service/joho/conference/semicon_digital/0014/handeji14-4.pdf), with one of the largest suppliers now 84 percent owned by a Japanese state fund [5](https://www.jiccapital.co.jp/en/news/.assets/E_20240417_JIC_JICC_PressRelease.pdf). Individual molecules are far more concentrated than the gas industry that sells them: neon and nitrogen trifluoride come from a handful of plants. China's gallium, germanium and antimony controls affect non-silicon chips and optics but not a silicon GPU, and the gallium suspension runs for one year from November 2025 [14](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-gallium.pdf). The qualification cycle matters more than the spot price, because every disruption so far was absorbed within a year and each one added a second source somewhere.

Concentration: **High**

Substitutability: **Moderate**. Rated on photoresist, the hardest input in this stage: Japan makes about four-fifths of it, and Korea needed five years to develop substitutes.

Price or market size: **Wafer fabrication materials were a $45.8bn market in 2025 and packaging materials $27.4bn, $73.2bn in total**

Who leads

-   {--{"author":"James's AI","timestamp":1790593820349}@@JPJSR--}{++{"author":"James's AI","timestamp":1790593820349}@@JP · **JSR**:++} Owner of Inpria's metal-oxide resist for extreme-ultraviolet printing; 84% held by Japan Investment Corporation, a state-backed fund, since April 2024
-   {--{"author":"James's AI","timestamp":1790593821826}@@JPTokyo--}{++{"author":"James's AI","timestamp":1790593821826}@@JP · **Tokyo++} Ohka {--{"author":"James's AI","timestamp":1790593821826}@@Kogyo--}{++{"author":"James's AI","timestamp":1790593821826}@@Kogyo**:++} Top-five resist maker; ¥139.7bn of sales in the first half of fiscal 2026
-   {--{"author":"James's AI","timestamp":1790593823361}@@FRAir Liquide--}{++{"author":"James's AI","timestamp":1790593823361}@@FR · **Air Liquide**:++} €2,465m of electronics revenue in 2025, 9.1% of group sales
-   {--{"author":"James's AI","timestamp":1790593824790}@@USEntegris--}{++{"author":"James's AI","timestamp":1790593824790}@@US · **Entegris**:++} $3.20bn of 2025 revenue in filters, polishing slurries, gas delivery and wafer carriers
-   {--{"author":"James's AI","timestamp":1790593825863}@@JPJX--}{++{"author":"James's AI","timestamp":1790593825863}@@JP · **JX++} Advanced {--{"author":"James's AI","timestamp":1790593825863}@@Metals--}{++{"author":"James's AI","timestamp":1790593825863}@@Metals**:++} About 65% of sputtering targets, the metal plates that chip wiring is made from

Where it is made

-   {--{"author":"James's AI","timestamp":1790593827968}@@JPJapan--}{++{"author":"James's AI","timestamp":1790593827968}@@JP · **Japan**:++} Photoresist, ultra-pure hydrofluoric acid, sputtering targets, polishing slurries
-   {--{"author":"James's AI","timestamp":1790593829366}@@USUnited States--}{++{"author":"James's AI","timestamp":1790593829366}@@US · **United States**:++} Entegris filters and wafer carriers, DuPont polishing slurries, Air Products gases
-   {--{"author":"James's AI","timestamp":1790593830810}@@FRFrance--}{++{"author":"James's AI","timestamp":1790593830810}@@FR · **France**:++} Air Liquide electronics gases and precursors
-   {--{"author":"James's AI","timestamp":1790593832353}@@KRSouth Korea--}{++{"author":"James's AI","timestamp":1790593832353}@@KR · **South Korea**:++} SK Materials nitrogen trifluoride, Dongjin resist, on-site gas for memory fabs
-   {--{"author":"James's AI","timestamp":1790593833375}@@CNChina--}{++{"author":"James's AI","timestamp":1790593833375}@@CN · **China**:++} Gallium, germanium and antimony refining; growing wet chemicals and polishing slurries

Why substitution is possible

Photoresist is the light-sensitive coating that holds the printed pattern on the wafer. Each formula is approved for one layer of one product at one fab. A new supplier therefore has to develop its version together with the fab, one layer at a time. Korea shows what switching takes. When Japan required an individual export license for each shipment of resist in 2019, Korea kept its fabs running and spent five years funding its own substitutes. Switching takes two to five years, and closer to five for the newest chips.

**Where China stands**

China cannot make photoresist for extreme-ultraviolet printing or for the finest 193 nm printing. It held under 5 percent of the photoresist market as of 2021. It refines 99 percent of the world's primary low-purity gallium. Since August 2023 it has required licenses to export gallium and germanium.

**Where the US stands**

American firms are strong in filters, containers, polishing slurries and gas delivery: Entegris, DuPont and Air Products. They are nearly absent from advanced photoresist since JSR of Japan bought Inpria, an American startup, in 2021.

A modern fab is a chemical plant with lithography attached. Air Liquide alone supplies more than 200 molecules and roughly 50,000 cylinders a year [1](https://www.airliquide.com/group/activities/electronics). None of it costs much by the metric ton, and any one of them missing stops the fab.

### How it works ^how-it-works-3

The resist has to change only where the light lands, and change fast enough that the scanner, the machine that projects the pattern, can expose each patch of the wafer in milliseconds. Since the 1990s the standard resist has been the chemically amplified resist. Each photon that lands frees one acid molecule inside the film, and nothing more happens until the wafer is baked. In the bake, each acid molecule sets off hundreds of reactions around itself that turn the film soluble, so a little light does a lot of chemistry. The wash then takes away the exposed film and leaves the rest. The light comes at 248 nm from a krypton fluoride laser or 193 nm from an argon fluoride laser shining through a layer of water, which sharpens the image.

That chemistry works less well with extreme ultraviolet (see [[#^lithography|Lithography]]). A 13.5 nm photon carries about fourteen times the energy of a 193 nm one, so the same dose of light arrives as far fewer photons. With fewer photons, where each one happens to land matters, and that randomness shows up as ragged line edges and missing contact holes, the small wells that join one layer of wiring to the next. Resist makers answered by absorbing more of the light: metal-oxide resists, built on clusters of tin and oxygen, take up extreme ultraviolet far better than carbon films, which is why JSR bought Inpria in 2021 [2](https://www.jsr.co.jp/jsr_e/news/2021/20210917.html).

Everything else puts material on the wafer, takes it off, or keeps it clean. Bulk gases arrive by the metric ton, specialty gases in grams. Silane carries silicon into the chamber for deposition. A plasma tears nitrogen trifluoride into charged fragments, which scrub the chamber walls clean between wafers. Hydrofluoric acid cleans the wafer itself. Polishing slurries grind each new layer flat before the next goes on. Sputtering targets are slabs of pure metal; a plasma knocks atoms off them, and the atoms settle on the wafer as the metal for the wiring. Filters and carriers keep contamination out.

### Variants and trade-offs ^variants-and-trade-offs-3

| Resist class | Wavelength | Where it is used | Limit |
| --- | --- | --- | --- |
| i-line novolak | 365 nm | Packaging, mature nodes | Resolution |
| KrF chemically amplified | 248 nm | Implant layers, thick films | Resolution |
| ArF immersion chemically amplified | 193 nm | Most critical layers below 28 nm | Needs several exposures per layer |
| EUV chemically amplified | 13.5 nm | Leading-edge single-exposure layers | Shot noise from too few photons |
| EUV metal-oxide | 13.5 nm | High-NA tools, tightest pitches | Cost, defects, outgassing |

Each resist class is tied to one scanner and one layer [3](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf).

### Who makes it ^who-makes-it-3

Japan produced about 90 percent of the world's semiconductor photoresist as of 2021, the rest mostly in the United States and South Korea [3](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). A later survey by Fuji Keizai, relayed in the December 2025 strategy deck of Japan's Ministry of Economy, Trade and Industry, puts Japan at 78 percent in 2023, the United States at 13 and South Korea at 6, with China inside the small remainder [4](https://www.meti.go.jp/policy/mono_info_service/joho/conference/semicon_digital/0014/handeji14-4.pdf).

**Chart:** Semiconductor photoresist production share by country, 2021 (%)

Japan **90%** United States, South Korea and others **10%**

Source: [CSET, The Semiconductor Supply Chain](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf)

A vehicle of Japan Investment Corporation, a state-backed fund, took 84.36 percent of JSR's shares at ¥4,350 each in a tender offer that closed on 16 April 2024, then delisted it [5](https://www.jiccapital.co.jp/en/news/.assets/E_20240417_JIC_JICC_PressRelease.pdf).

Tokyo Ohka Kogyo sold ¥139,668 million in the first half of fiscal 2026, up 25.1 percent on AI server demand [6](https://www.tok.co.jp/application/files/7417/8598/0069/q2_2612_en.pdf). Fujifilm lifted its polishing-slurry capacity at Kumamoto by 30 percent in January 2025 [7](https://www.fujifilm.com/jp/en/news/hq/11942) and opened extreme-ultraviolet resist lines at Shizuoka and Pyeongtaek that October [8](https://www.fujifilm.com/jp/en/news/hq/11842).

Wafer fabrication materials sold $45.8 billion in 2025 and packaging materials $27.4 billion [9](https://www.prnewswire.com/news-releases/global-semiconductor-materials-market-revenue-reaches-record-73-2-billion-in-2025--semi-reports-302768700.html).

Gases are a Western-led oligopoly: Linde, Air Liquide, Air Products, Nippon Sanso and Messer. Air Liquide's electronics arm alone sold €2,465 million in 2025, 9.1 percent of group revenue [1](https://www.airliquide.com/group/activities/electronics). Smaller firms specialize in single molecules: SK Materials in nitrogen trifluoride, Kanto Denka in fluorine chemistry, Stella Chemifa and Morita in ultra-high-purity hydrofluoric acid.

As of 2021 five firms held more than 60 percent of wet chemicals, and DuPont and Cabot Microelectronics about 56 percent of a $790 million market in polishing slurries [3](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). Sputtering targets are more concentrated than any of those, with JX Advanced Metals holding about 65 percent of the world market [10](https://www.jx-nmm.com/english/company/glance/).

### The chokepoint ^the-chokepoint-3

Supply at this stage has been disrupted twice since 2019, once by a government and once by a war.

In July 2019 Japan put photoresist, hydrogen fluoride and fluorinated polyimide under individual export licenses for South Korea. It had supplied more than 90 percent of Korean imports of two of the three, and hydrogen fluoride exports fell 87.9 percent [11](https://www.rieti.go.jp/en/columns/v01_0201.html). Korea kept its fabs running and spent five years funding domestic substitutes, which is what materials controls usually produce.

In 2022 Russia invaded Ukraine, which supplied about 70 percent of the world's neon and 90 percent of the semiconductor-grade neon used by US industry [12](https://www.csis.org/blogs/perspectives-innovation/russias-invasion-ukraine-impacts-gas-markets-critical-chip-production). Buyers had stockpiled since the 2014 annexation of Crimea, and Korean and Japanese chipmakers reported adequate neon from China instead [12](https://www.csis.org/blogs/perspectives-innovation/russias-invasion-ukraine-impacts-gas-markets-critical-chip-production).

China's export controls fall on the metals. Beijing announced export licenses for gallium and germanium in July 2023, in force from August, then banned both, plus antimony and superhard materials, to the United States in December 2024 [13](https://www.stimson.org/2025/chinas-germanium-and-gallium-export-restrictions-consequences-for-the-united-states/). In November 2025 it lifted the gallium ban for one year [14](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-gallium.pdf).

Neither metal goes into a silicon logic chip. Germanium goes into fiber optics, infrared optics, solar cells for satellites and radiation detectors [15](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-germanium.pdf); gallium into the non-silicon wafers behind radio front ends, LEDs and lasers [14](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-gallium.pdf). They move the price instead. Germanium metal averaged $4,100 a kilogram in 2025 against $1,392 in 2023, and US imports of the metal fell 67 percent [15](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-germanium.pdf). The US Geological Survey put the cost to US GDP of a complete ban at about $3.4 billion [13](https://www.stimson.org/2025/chinas-germanium-and-gallium-export-restrictions-consequences-for-the-united-states/).

**Chart:** Germanium metal, annual average price ($/kg). China licensed exports from August 2023 and banned US shipments in December 2024 ($/kg)

2021 1,187 2022 1,294 2023 1,392 2024 1,991 2025 4,100

Source: [USGS Mineral Commodity Summaries, February 2026 (Argus Media prices)](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-germanium.pdf)

The slower risk is the European Union's proposed restriction on PFAS, the long-lived fluorinated chemicals. The five member states behind it published a revised text on 20 August 2025, after working through more than 5,600 comments [16](https://echa.europa.eu/-/echa-supports-pfas-restriction-with-targeted-derogations). The committees of ECHA, the EU chemicals agency, now back an EU-wide restriction with targeted exemptions, and the scientific evaluation is due to finish by the end of 2026 [16](https://echa.europa.eu/-/echa-supports-pfas-restriction-with-targeted-derogations). These chemicals are everywhere in a fab: photoacid generators, etch gases, chamber liners, pump seals and filter membranes are all fluorinated. An exemption is likely, but nothing is law yet.

### Key evaluation criteria ^key-evaluation-criteria-3

-   **Purity, in parts per trillion** of metallic contamination, a million times finer than parts per million, which is the spec that keeps entrants out.
-   **Qualification lock-in**: a resist or slurry is approved for one layer of one product at one fab, so switching costs are counted in tape-outs.
-   **Photon efficiency** for EUV resists: how much light the resist absorbs sets the dose, the dose sets how many wafers an hour the scanner prints, and too few photons per dose set the defect rate, which is the case for metal-oxide chemistry.
-   **Transportability**: bulk gases are made on site at the fab, and only cylinder-shipped specialty gases can be embargoed.
-   **Byproduct exposure**: gallium is recovered mostly from bauxite refining and germanium from zinc concentrates, so supply depends on another industry's economics [14](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-gallium.pdf).

{--{"author":"James's AI","timestamp":1790593839424}@@Card--}{++{"author":"James's AI","timestamp":1790593839424}@@**Card++} 1 of {--{"author":"James's AI","timestamp":1790593839424}@@4Question--}{++{"author":"James's AI","timestamp":1790593839424}@@4 · Question**++}

What does photoresist do?

{--{"author":"James's AI","timestamp":1790593841479}@@Card--}{++{"author":"James's AI","timestamp":1790593841479}@@**Card++} 1 of {--{"author":"James's AI","timestamp":1790593841479}@@4Answer--}{++{"author":"James's AI","timestamp":1790593841479}@@4 · Answer**++}

It holds the pattern printed by light, so the next step can etch that pattern into the wafer.

A wash removes the parts the light reached. The pattern that remains guides the etch. [[#^how-it-works-3|Reread: How it works]]

{--{"author":"James's AI","timestamp":1790593843470}@@Card--}{++{"author":"James's AI","timestamp":1790593843470}@@**Card++} 2 of {--{"author":"James's AI","timestamp":1790593843470}@@4Question--}{++{"author":"James's AI","timestamp":1790593843470}@@4 · Question**++}

Which country makes most of the world's photoresist?

{--{"author":"James's AI","timestamp":1790593844869}@@Card--}{++{"author":"James's AI","timestamp":1790593844869}@@**Card++} 2 of {--{"author":"James's AI","timestamp":1790593844869}@@4Answer--}{++{"author":"James's AI","timestamp":1790593844869}@@4 · Answer**++}

Japan.

Japan made about 90 percent in 2021 and 78 percent in 2023. [[#^who-makes-it-3|Reread: Who makes it]]

{--{"author":"James's AI","timestamp":1790593846389}@@Card--}{++{"author":"James's AI","timestamp":1790593846389}@@**Card++} 3 of {--{"author":"James's AI","timestamp":1790593846389}@@4Question--}{++{"author":"James's AI","timestamp":1790593846389}@@4 · Question**++}

Why does replacing a photoresist supplier take years?

{--{"author":"James's AI","timestamp":1790593847771}@@Card--}{++{"author":"James's AI","timestamp":1790593847771}@@**Card++} 3 of {--{"author":"James's AI","timestamp":1790593847771}@@4Answer--}{++{"author":"James's AI","timestamp":1790593847771}@@4 · Answer**++}

Each formula is approved for one layer of one product at one factory.

After Japan's 2019 export licenses, Korea needed five years to build substitutes. [[#^the-chokepoint-3|Reread: The chokepoint]]

{--{"author":"James's AI","timestamp":1790593849038}@@Card--}{++{"author":"James's AI","timestamp":1790593849038}@@**Card++} 4 of {--{"author":"James's AI","timestamp":1790593849038}@@4Question--}{++{"author":"James's AI","timestamp":1790593849038}@@4 · Question**++}

Do China's controls on gallium and germanium hurt silicon AI chips?

{--{"author":"James's AI","timestamp":1790593850292}@@Card--}{++{"author":"James's AI","timestamp":1790593850292}@@**Card++} 4 of {--{"author":"James's AI","timestamp":1790593850292}@@4Answer--}{++{"author":"James's AI","timestamp":1790593850292}@@4 · Answer**++}

Very little. Neither metal goes into a silicon chip.

Both go into optics and non-silicon chips such as LEDs and lasers. [[#^the-chokepoint-3|Reread: The chokepoint]]

#### Four things to remember ^four-things-to-remember-2

-   Photoresist holds the pattern printed by light so the next step can etch it into the wafer.
-   Japan makes most of the world's photoresist: about 90 percent in 2021 and 78 percent in 2023.
-   Each resist is approved for one layer of one product at one factory, so a new supplier takes years.
-   China's gallium and germanium controls hit optics and non-silicon chips, and barely touch a silicon GPU.

**Sources (16)**

1.  A [Electronics | Air Liquide](https://www.airliquide.com/group/activities/electronics) Air Liquide
2.  A [JSR Agrees to Acquire EUV Pioneer Inpria Corporation | 2021 | News](https://www.jsr.co.jp/jsr_e/news/2021/20210917.html) JSR Corporation · 17 September 2021
3.  A [The Semiconductor Supply Chain - Issue Brief](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf) Center for Security and Emerging Technology (CSET) · 21 January 2021
4.  A [METI, Semiconductor and digital industry strategy: future direction (半導体・デジタル産業戦略の今後の方向性), 23 December 2025](https://www.meti.go.jp/policy/mono_info_service/joho/conference/semicon_digital/0014/handeji14-4.pdf) Ministry of Economy, Trade and Industry (Japan) · 23 December 2025
5.  A [April 17, 2024 Japan Investment Corporation](https://www.jiccapital.co.jp/en/news/.assets/E_20240417_JIC_JICC_PressRelease.pdf) Japan Investment Corporation · 17 April 2024
6.  A [Consolidated Financial Results for the Second Quarter (Interim) of the Fiscal Year Ending December 31, 2026 \[J-GAAP\]](https://www.tok.co.jp/application/files/7417/8598/0069/q2_2612_en.pdf) Tokyo Ohka Kogyo · 5 August 2026
7.  A [Fujifilm to Enhance its Production Capacity of Advanced Semiconductor Material CMP Slurries at the Kumamoto Site](https://www.fujifilm.com/jp/en/news/hq/11942) Fujifilm · 5 December 2024
8.  A [Fujifilm Launches EUV Resist and EUV Developer](https://www.fujifilm.com/jp/en/news/hq/11842) Fujifilm · 29 October 2024
9.  A [Global Semiconductor Materials Market Revenue Reaches Record $73.2 Billion in 2025, SEMI Reports](https://www.prnewswire.com/news-releases/global-semiconductor-materials-market-revenue-reaches-record-73-2-billion-in-2025--semi-reports-302768700.html) PR Newswire · 12 May 2026
10.  A [Quick Guide to JX Advanced Metals | Corporate Overview](https://www.jx-nmm.com/english/company/glance/) JX Advanced Metals
11.  A [The impact of export controls on international trade: evidence from the Japan–Korea trade dispute in the semiconductor industry](https://www.rieti.go.jp/en/columns/v01_0201.html) Research Institute of Economy, Trade and Industry (Japan) · 8 May 2023
12.  A [Russia's Invasion of Ukraine Impacts Gas Markets Critical to Chip Production | Perspectives on Innovation](https://www.csis.org/blogs/perspectives-innovation/russias-invasion-ukraine-impacts-gas-markets-critical-chip-production) Center for Strategic and International Studies
13.  A [China’s Germanium and Gallium Export Restrictions: Consequences for the United States](https://www.stimson.org/2025/chinas-germanium-and-gallium-export-restrictions-consequences-for-the-united-states/) Stimson Center · 19 March 2025
14.  A [Mineral Commodity Summaries 2026](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-gallium.pdf) U.S. Geological Survey · 5 February 2026
15.  A [Mineral Commodity Summaries 2026](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-germanium.pdf) U.S. Geological Survey · 5 February 2026
16.  A [ECHA supports PFAS restriction with targeted derogations](https://echa.europa.eu/-/echa-supports-pfas-restriction-with-targeted-derogations) European Chemicals Agency · 26 March 2026

## Lithography ^lithography

The most concentrated stage in the chain. One firm in the Netherlands builds every extreme ultraviolet scanner in the world, the machine that prints the finest circuit layers. It shipped 48 of them in 2025, at around $200 million each.

{--{"author":"James's AI","timestamp":1790593852291}@@1,564--}{++{"author":"James's AI","timestamp":1790593852291}@@_1,564++} words / 7 {--{"author":"James's AI","timestamp":1790593852291}@@minSpecimen:--}{++{"author":"James's AI","timestamp":1790593852291}@@min · Interactive 3D Specimen:++} EUV scanner{++{"author":"James's AI","timestamp":1790593852291}@@ (only on the live site: [open this chapter on chipsupplychain.org](https://chipsupplychain.org/#lithography))_++}

In plain terms

Lithography prints the pattern of a circuit onto the wafer. A machine holds a stencil of one layer of the circuit up to a lamp and projects the image, four times smaller, onto the silicon. Light cannot draw a line much finer than its own wave, so the finer the lines, the shorter the wavelength of light needed to print them. Air soaks up the shortest light now in use, so the machine has to print in a vacuum. Only one company has ever built a machine that prints with it, and it is Dutch. Export controls are government rules on who a company may sell to. Every advanced chip passes through that firm's machines, so a rule aimed at it reaches all advanced chipmaking.

### In short ^in-short-4

ASML, in Veldhoven, using Zeiss mirrors from Oberkochen, sets the resolution of every leading-edge AI chip. ASML booked 48 EUV systems in 2025, four of them High-NA [1](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf). Export controls cut China's share of ASML system sales from 41 percent in 2024 to 33 percent in 2025 [4](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf), and China's answer is domestic immersion DUV plus an EUV prototype that has not yet made a chip. No announced program changes this bottleneck before 2030.

Concentration: **Extreme**

Substitutability: **Very hard**. ASML is the only maker of EUV scanners, only Zeiss can polish their mirrors, and a state-funded Chinese team has made the light but has not printed a chip.

Price or market size: **About $200M**. for a standard EUV scanner, $350-400M for the newer High-NA version and about $60M for a DUV tool, according to Reuters. ASML does not publish per-system prices

Who leads

-   {--{"author":"James's AI","timestamp":1790593860946}@@NLASML--}{++{"author":"James's AI","timestamp":1790593860946}@@NL · **ASML**:++} 100% of EUV (extreme ultraviolet) and above 80% of DUV (deep ultraviolet); EUV was 48% of its own 2025 system revenue and immersion DUV 42%
-   {--{"author":"James's AI","timestamp":1790593862376}@@JPNikon--}{++{"author":"James's AI","timestamp":1790593862376}@@JP · **Nikon**:++} 22 new chipmaking scanners in the year to March 2026, in a market Nikon estimates at 570 units
-   {--{"author":"James's AI","timestamp":1790593864608}@@JPCanon--}{++{"author":"James's AI","timestamp":1790593864608}@@JP · **Canon**:++} i-line and krypton fluoride steppers for older, coarser layers, plus the only commercial nanoimprint tool

Where it is made

-   {--{"author":"James's AI","timestamp":1790593866551}@@NLNetherlands--}{++{"author":"James's AI","timestamp":1790593866551}@@NL · **Netherlands**:++} ASML design and final assembly, Veldhoven
-   {--{"author":"James's AI","timestamp":1790593867307}@@DEGermany--}{++{"author":"James's AI","timestamp":1790593867307}@@DE · **Germany**:++} Zeiss SMT optics, Oberkochen; Trumpf carbon dioxide lasers that drive the light source, Ditzingen
-   {--{"author":"James's AI","timestamp":1790593868654}@@USUnited States--}{++{"author":"James's AI","timestamp":1790593868654}@@US · **United States**:++} ASML light-source research and manufacturing, San Diego
-   {--{"author":"James's AI","timestamp":1790593869679}@@JPJapan--}{++{"author":"James's AI","timestamp":1790593869679}@@JP · **Japan**:++} Nikon and Canon deep ultraviolet scanners and steppers

Why substitution is slow

Nobody else has ever built an EUV scanner. A newcomer would first have to make mirrors a meter wide, polished smooth to within tens of picometers, a picometer being a trillionth of a meter. It would also need a light source that hits tin droplets with a laser 50,000 times a second. The best-funded attempt so far, in China, has made extreme-ultraviolet light but has printed no chip. CSIS judges that China cannot yet build a working EUV scanner, and no announced program would change that before 2030.

**Where China stands**

No EUV scanner has ever been sold to a customer in China. CSIS judges that China cannot build the technology despite state investment. Shanghai Aishengna Electronic Technology Group, a state-owned firm registered in 2023, is reported to have started producing Chinese immersion DUV scanners in 2026. SMEE, the older Chinese supplier, holds about 4 percent of the world market for i-line scanners, the coarsest kind, and no share of any finer kind.

**Where the US stands**

No American firm makes scanners. The US government still controls who may buy them, through Dutch export licenses, the American-made parts inside each machine, and its entity list of firms that may not be supplied.

Every transistor in an AI accelerator gets its shape from a machine one company builds. ASML sold 327 lithography systems in 2025, 48 of them extreme ultraviolet, and nobody else sells EUV [1](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf).

### How it works ^how-it-works-4

The stencil is a photomask, the film is photoresist and the machine is a scanner (see [[#^photomasks-and-pellicles|Photomasks and pellicles]]).

The wafer is coated with photoresist, a film that changes wherever light touches it. The mask holds one layer of the circuit as a pattern of clear and dark areas, drawn four times larger than life. The machine shines light through the mask, shrinks the image four times with a lens, and lands it on the film. A wash then removes the film where the light hit, and the pattern is left standing on the wafer for the next machine to etch in or fill with metal. Then the film is stripped and the next mask goes in. A chip takes dozens of masks, one per layer.

![](https://chipsupplychain.org/media/litho-light-end.jpg)

How lithography prints a chip

The image from one mask covers a patch about 26 by 33 mm, so the wafer moves under the lens one patch at a time, close to a hundred patches per wafer. ASML's own throughput rating for an EUV scanner assumes 96 of them [2](https://www.asml.com/en/products/euv-lithography-systems/twinscan-nxe3400b). Before each one, the machine finds marks printed in earlier layers and lines the new layer up on them to within a few nanometers.

Finer lines need shorter light. The finest light now in use, at 13.5 nm, is stopped by glass and by air, so an EUV scanner works in a vacuum and uses mirrors instead of lenses, and its masks are mirrors too. The older machines, which use light fourteen times longer, gain extra sharpness by filling the gap between lens and wafer with water [3](https://www.asml.com/en/technology/lithography-principles/lenses-and-mirrors).

When one exposure cannot draw a pattern finely enough, the layer is printed with two, three or four masks instead. Each extra pass costs a mask, machine time and a chance to misalign, so a single EUV exposure usually works out cheaper.

### Variants and trade-offs ^variants-and-trade-offs-4

#### Deep ultraviolet ^deep-ultraviolet

Deep ultraviolet (DUV) light comes from gas lasers: 248 nanometers from krypton fluoride (KrF), 193 from argon fluoride (ArF), shone through air or water. These tools still dominate by volume: of ASML's 327 systems in 2025, 131 were ArF immersion, 78 KrF, 54 the older, coarser i-line and 16 ArF dry [4](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf). A DUV scanner costs roughly $60 million. DUV is the one tier with named competitors, Nikon and Canon, and ASML still holds above 80 percent of it [5](https://www.reuters.com/world/asia-pacific/250-million-asml-printer-behind-nvidias-chips-2026-07-28/).

Immersion is the contested tier, because without EUV a fab needs NXT:2000i-class scanners and several passes per layer to reach leading-edge logic, and that is the tier Dutch export licensing covers.

#### Extreme ultraviolet ^extreme-ultraviolet

The 13.5 nm light comes from dropping molten tin into a vacuum vessel 50,000 times a second and hitting each droplet twice, with a low-intensity pulse to flatten it and then one that vaporizes it into plasma [6](https://www.asml.com/en/technology/lithography-principles/light-and-lasers). Zeiss mirrors carry it to the wafer, and the largest are a meter across, polished flat to within tens of picometers, thousandths of a nanometer [3](https://www.asml.com/en/technology/lithography-principles/lenses-and-mirrors).

Brighter light means more wafers an hour, and ASML ran the first 1,000-watt EUV source in April 2025 [7](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf). Its TWINSCAN NXE:3800E now ships at its full 220 wafers an hour, 37 percent better than the NXE:3600D [7](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf).

#### High-NA EUV ^high-na-euv

High numerical aperture (High-NA) raises the aperture from 0.33 to 0.55 and cuts the smallest printable feature from 13 nm to 8 nm [8](https://www.asml.com/en/company/stories/2024/5-things-high-na-euv). Its optics shrink the mask image four times in one direction and eight in the other, halving the patch of wafer one exposure covers and doubling the exposures per wafer [8](https://www.asml.com/en/company/stories/2024/5-things-high-na-euv). The second-generation TWINSCAN EXE:5200B runs at 175 wafers an hour, 60 percent above the EXE:5000 [7](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf).

Reuters puts a standard EUV tool at around $200 million and a High-NA machine at $350 to $400 million, prices ASML does not publish [5](https://www.reuters.com/world/asia-pacific/250-million-asml-printer-behind-nvidias-chips-2026-07-28/).

**Chart:** What one lithography system costs. The High-NA figure is quoted as a $350-400M range; the bar shows the low end ($M)

DUV scanner 60 EUV, 0.33 NA 200 High-NA EUV 350

Source: [Reuters, The $400 million ASML 'printers', July 2026](https://www.reuters.com/world/asia-pacific/250-million-asml-printer-behind-nvidias-chips-2026-07-28/)

Intel and TSMC have chosen differently on High-NA:

-   **Intel Foundry** ships the first high-volume logic product made with High-NA, on Intel 18A, and installed the first EXE:5200B [9](https://www.asml.com/en/news/press-releases/2026/high-na-euv-reaches-new-readiness-milestone), after more than a million High-NA wafers [10](https://www.intel.com/content/www/us/en/newsroom/news/intel-foundry/intel-foundry-asml-accelerate-industry-readiness-for-high-na-euv.html).
-   **TSMC** waited, and now says it will use High-NA in high-volume manufacturing from 2030 [11](https://pr.tsmc.com/english/news/3338).

ASML booked four EXE systems as revenue in 2025 against two in 2024 [1](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf), and expects the platform to carry high-volume manufacturing from 2027 [7](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf). On 8 September 2026 it announced with TSMC a move to 12-inch photomasks to lift the field-size limit, with a pilot mask line in 2031 and production systems by 2033 [11](https://pr.tsmc.com/english/news/3338).

{++{"author":"James's AI","timestamp":1790593874567}@@**Chart:** ++}EUV systems ASML booked as revenue each {--{"author":"James's AI","timestamp":1790593874567}@@yeartools--}{++{"author":"James's AI","timestamp":1790593874567}@@year (tools)++}

2023 53 2024 44 2025 48

Source: [ASML annual reports 2024 and 2025](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf)

### Who makes it ^who-makes-it-4

ASML took EUR 32.7 billion in net sales in 2025 at a 52.8 percent gross margin [1](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf), and in July 2026 raised its 2026 forecast to EUR 43 to 45 billion at 54 to 56 percent [12](https://ourbrand.asml.com/asset/c8dbf3fc-4c5e-4406-83f6-27694b138245/Press-Release-Financial-Results-Q2-2026.pdf). It assembles more than it makes, listing 5,100 suppliers [13](https://www.sec.gov/Archives/edgar/data/937966/000162828026011377/asml-2025xannualxreportx.htm). Four of them make the main parts of the EUV machine:

-   **Zeiss SMT**, Oberkochen, makes the illumination system and the six-mirror projection optics [14](https://www.zeiss.com/semiconductor-manufacturing-technology/inspiring-technology/euv-lithography.html).
-   **Trumpf**, Ditzingen, makes the carbon dioxide drive laser, which amplifies a few watts to 40 kilowatts [15](https://www.trumpf.com/en_US/products/lasers/euv-drive-laser/).
-   **ASML San Diego**, the former Cymer, designs the source where the laser turns tin into plasma, and builds the droplet generator [16](https://www.asml.com/en/company/about-asml/locations/san-diego).
-   **VDL ETG** builds the frames that suspend and position the mirrors [17](https://www.vdlgroep.com/en/vdl-groep/innovation-projects/vdl-etg-builds-complex-frames-for-zeiss).

Zeiss mirror polishing and coating caps EUV output. Final assembly in Veldhoven waits on the optics.

Nikon and Canon are specialists now. Nikon sold 22 new scanners in the year to March 2026, into a market it sizes at 570 units, and lost money on Precision Equipment [18](https://www.nikon.com/content/dam/web-assets/nikoncom/company/local/global/en/ir/ir_library/result/pdf/2026/26_all_e.pdf). Canon's alternative is nanoimprint, where the FPA-1200NZ2C stamps the pattern instead of projecting it, down to a 14 nm linewidth [19](https://global.canon/en/news/2024/20240926.html). No leading-edge logic customer has taken it up.

**Chart:** ASML net system sales by technology, 2025 (%)

EUV **48%** ArF immersion **42%** KrF **4%** Metrology and inspection **3%** ArF dry **2%** i-line **1%**

Source: [ASML Q4 2025 investor presentation](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf)

### Controls and China's answer ^controls-and-chinas-answer

Export controls bar EUV from Chinese foundries, and CSIS judges that China cannot yet build it despite state spending [20](https://www.csis.org/blogs/strategic-technologies-blog/breakthroughs-or-boasts-assessing-recent-chinese-lithography). Below EUV, the restrictions arrived in this order:

-   **Dutch national licensing** of advanced DUV took effect on 1 September 2023, and The Hague widened it on 6 September 2024 [21](https://www.government.nl/latest/news/2024/09/06/the-netherlands-expands-export-control-measure-advanced-semiconductor-manufacturing-equipment).
-   **A partial license revocation** disclosed on 1 January 2024 stopped NXT:2050i and NXT:2100i shipments to a few Chinese customers [22](https://www.asml.com/en/news/press-releases/2023/statement-regarding-partial-revocation-export-license).
-   **The BIS Affiliates Rule** extended entity-list controls to 50 percent-owned subsidiaries from 29 September 2025 [23](https://www.federalregister.gov/documents/2025/09/30/2025-19001/expansion-of-end-user-controls-to-cover-affiliates-of-certain-listed-entities), then BIS suspended it to 9 November 2026 [24](https://www.federalregister.gov/documents/2025/11/12/2025-19846/one-year-suspension-of-expansion-of-end-user-controls-for-affiliates-of-certain-listed-entities).

China fell from 41 percent of ASML's net system sales in 2024 to 33 percent in 2025 [4](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf).

On DUV, Reuters reported in July 2026, on one unnamed source, that Shanghai Aishengna Electronic Technology Group has started producing home-grown immersion DUV tools. The firm was registered in August 2023 with 7 billion yuan of capital and two state shareholders, Shanghai Electric Holding and a Shanghai International Trust subsidiary. It has no website, and has taken in teams from SMEE and the startup Yuliangsheng [25](https://www.reuters.com/world/china/china-starts-production-home-grown-immersion-duv-chipmaking-tools-source-2026-07-28/). SMEE, the incumbent, is strongest in i-line and even there holds about four percent of the world market [20](https://www.csis.org/blogs/strategic-technologies-blog/breakthroughs-or-boasts-assessing-recent-chinese-lithography).

On EUV there is less evidence, and claims of Huawei mass production in 2026 remain unverified. Reuters reported in December 2025 that a Shenzhen team of former ASML engineers had built a prototype that makes extreme ultraviolet light but no chip [26](https://www.reuters.com/world/china/how-china-built-its-manhattan-project-rival-west-ai-chips-2025-12-17/). Between that light and a printed chip sit the mirrors, and only Zeiss can polish them.

**Chart:** ASML net system sales by the region tools shipped to, 2025 (%)

China **33%** South Korea **25%** Taiwan **22%** United States **12%** Japan **5%** Rest of Asia **2%** EMEA **1%**

%% validator-ignore-next-line --code article.block-repeated-nearby --reason source-provides-alternative-citation-formats %%
Source: [ASML Q4 2025 investor presentation](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf)

### The chokepoint ^the-chokepoint-4

If ASML stops shipping, nothing at the leading edge gets printed, and even ASML could not rebuild itself quickly, since Zeiss makes its optics and Trumpf its drive laser.

For AI accelerators, EUV is the point of control. It prints the finest layers, the ones that set how densely transistors and wires pack, and TSMC expects the number of layers needing High-NA to rise as AI designs grow more complex [11](https://pr.tsmc.com/english/news/3338). Every added layer is more time on a tool nobody else builds.

### Key evaluation criteria ^key-evaluation-criteria-4

-   **Resolution.** Set by wavelength divided by numerical aperture. 13 nm at 0.33 NA, 8 nm at 0.55 NA [8](https://www.asml.com/en/company/stories/2024/5-things-high-na-euv).
-   **Throughput.** Wafers an hour at a stated dose. 220 on the NXE:3800E, 175 on the EXE:5200B [7](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf).
-   **Overlay.** How precisely one layer lands on the one below; ASML credits the EXE:5200B's gain to new Zeiss optics [7](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf).
-   **Field size.** The patch of wafer one exposure covers. High-NA halves it, so big AI dies must be stitched until 12-inch masks arrive [8](https://www.asml.com/en/company/stories/2024/5-things-high-na-euv).
-   **Source power.** Brighter light, more wafers an hour, which is why the 1,000-watt demonstration matters [7](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf).

Card 1 of 4Question

What does lithography do?

Card 1 of 4Answer

It prints each layer of a chip's circuit onto the wafer.

The machine projects the image of a stencil, four times smaller, onto the silicon. [[#^how-it-works-4|Reread: How it works]]

Card 2 of 4Question

Why do the finest layers need extreme-ultraviolet (EUV) light?

Card 2 of 4Answer

Finer lines need light of a shorter wavelength, and EUV has the shortest in use.

Air and glass absorb EUV light, so the machine works in a vacuum and uses mirrors instead of lenses. [[#^how-it-works-4|Reread: How it works]]

Card 3 of 4Question

Who makes EUV machines?

Card 3 of 4Answer

Only ASML, in the Netherlands.

ASML booked 48 EUV systems in 2025. Its mirrors come from one supplier, Zeiss. [[#^who-makes-it-4|Reread: Who makes it]]

Card 4 of 4Question

Can China buy or build an EUV machine?

Card 4 of 4Answer

No. None has been sold to China, and its own prototype has printed no chip.

China's answer so far is domestic immersion DUV machines, which use longer-wavelength light. [[#^controls-and-chinas-answer|Reread: Controls and China's answer]]

#### Four things to remember ^four-things-to-remember-3

-   Lithography prints each layer of a chip's circuit onto the wafer.
-   The finest layers need extreme-ultraviolet light, which works only in a vacuum and with mirrors.
-   ASML of the Netherlands is the only maker of EUV machines, and Zeiss is the only maker of their mirrors.
-   No EUV machine has been sold to China, and its own prototype has printed no chip.

Sources (26)

1.  A [ASML 2025 Annual Report](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf) ASML · 24 February 2026
2.  A [TWINSCAN NXE:3400B: EUV lithography systems](https://www.asml.com/en/products/euv-lithography-systems/twinscan-nxe3400b) ASML
3.  A [Lenses & mirrors - Lithography principles](https://www.asml.com/en/technology/lithography-principles/lenses-and-mirrors) ASML
4.  A [Presentation Investor Relations Q4 2025](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf) ASML · 27 January 2026
5.  B [Explainer: The $400 million ASML 'printers' key for the AI chip boom](https://www.reuters.com/world/asia-pacific/250-million-asml-printer-behind-nvidias-chips-2026-07-28/) Reuters · 28 January 2026
6.  A [All about light and lasers in lithography](https://www.asml.com/en/technology/lithography-principles/light-and-lasers) ASML
7.  A [ASML 2025 Annual Report](https://ourbrand.asml.com/m/8ab959d4926657b/original/asml-2025-annual-report-strategic-report-section.pdf) ASML · 24 February 2026
8.  A [5 things you should know about High NA in EUV](https://www.asml.com/en/company/stories/2024/5-things-high-na-euv) ASML · 25 January 2024
9.  A [High NA EUV reaches new readiness milestone with first high-volume Logic product](https://www.asml.com/en/news/press-releases/2026/high-na-euv-reaches-new-readiness-milestone) ASML · 15 July 2026
10.  A [Intel Foundry and ASML Accelerate Industry Readiness for High-NA EUV](https://www.intel.com/content/www/us/en/newsroom/news/intel-foundry/intel-foundry-asml-accelerate-industry-readiness-for-high-na-euv.html) Intel · 7 September 2026
11.  A [ASML and TSMC Announce Initiative to Pioneer Industry Transition to Large-Format Photomasks for High NA EUV](https://pr.tsmc.com/english/news/3338) TSMC · 8 September 2026
12.  A [Press Release Financial Results Q2 2026](https://ourbrand.asml.com/asset/c8dbf3fc-4c5e-4406-83f6-27694b138245/Press-Release-Financial-Results-Q2-2026.pdf) ASML · 14 July 2026
13.  A [ASML HOLDING NV, Form 6-K report of foreign private issuer for the period ended 2025-12-31 (6-K)](https://www.sec.gov/Archives/edgar/data/937966/000162828026011377/asml-2025xannualxreportx.htm) U.S. Securities and Exchange Commission (filing by ASML HOLDING NV) · 25 February 2026
14.  A [EUV lithography and technology](https://www.zeiss.com/semiconductor-manufacturing-technology/inspiring-technology/euv-lithography.html) Carl Zeiss
15.  A [Good things come in ever-smaller packages](https://www.trumpf.com/en_US/products/lasers/euv-drive-laser/) TRUMPF
16.  A [Explore ASML San Diego](https://www.asml.com/en/company/about-asml/locations/san-diego) ASML
17.  A [VDL Groep, VDL ETG builds complex frames for Zeiss, innovation project page](https://www.vdlgroep.com/en/vdl-groep/innovation-projects/vdl-etg-builds-complex-frames-for-zeiss) VDL Groep
18.  A [FINANCIAL RESULTS The Year Ended March 31,2026](https://www.nikon.com/content/dam/web-assets/nikoncom/company/local/global/en/ir/ir_library/result/pdf/2026/26_all_e.pdf) Nikon · 21 May 2026
19.  A [Canon delivers FPA -1200NZ2C nanoimprint lithography system for semiconductor manufacturing to the Texas Institute for Electronics](https://global.canon/en/news/2024/20240926.html) Canon · 26 September 2024
20.  A [Breakthroughs or Boasts? Assessing Recent Chinese Lithography Advancements | Strategic Technologies Blog](https://www.csis.org/blogs/strategic-technologies-blog/breakthroughs-or-boasts-assessing-recent-chinese-lithography) Center for Strategic and International Studies
21.  A [The Netherlands expands export control measure for advanced semiconductor manufacturing equipment](https://www.government.nl/latest/news/2024/09/06/the-netherlands-expands-export-control-measure-advanced-semiconductor-manufacturing-equipment) Government of the Netherlands · 6 September 2024
22.  A [Statement regarding partial revocation export license](https://www.asml.com/en/news/press-releases/2023/statement-regarding-partial-revocation-export-license) ASML · 1 January 2024
23.  A [Expansion of End-User Controls To Cover Affiliates of Certain Listed Entities](https://www.federalregister.gov/documents/2025/09/30/2025-19001/expansion-of-end-user-controls-to-cover-affiliates-of-certain-listed-entities) Federal Register (Commerce Department; Industry and Security Bureau) · 30 September 2025
24.  A [One Year Suspension of Expansion of End-User Controls for Affiliates of Certain Listed Entities](https://www.federalregister.gov/documents/2025/11/12/2025-19846/one-year-suspension-of-expansion-of-end-user-controls-for-affiliates-of-certain-listed-entities) Federal Register (Commerce Department; Industry and Security Bureau) · 12 November 2025
25.  B [China starts production of home-grown immersion DUV chipmaking tools, source says](https://www.reuters.com/world/china/china-starts-production-home-grown-immersion-duv-chipmaking-tools-source-2026-07-28/) Reuters · 28 July 2026
26.  B [How China built its 'Manhattan Project' to rival the West in AI chips](https://www.reuters.com/world/china/how-china-built-its-manhattan-project-rival-west-ai-chips-2025-12-17/) Reuters · 17 December 2025

## Photomasks and Pellicles ^photomasks-and-pellicles

Every leading-edge chip depends on a business worth tens of billions of yen. Two Japanese firms make almost all the blank plates that EUV masks are built on, one Japanese firm inspects them, and the dust cover meant to protect them is still not in production.

1,421 words / 6 minSpecimen: photomask

In plain terms

A photomask is the stencil that lithography prints from, one for each layer of a chip. The same plate prints its layer on wafer after wafer, so one plate shapes millions of chips. No glass lets the short light now in use pass through, so instead of a window the plate is a mirror, built up from about forty pairs of very thin layers, and the light bounces off it. A dark pattern drawn on top of the mirror soaks up the light wherever no line should print. Any speck of dust on the plate repeats on every wafer it prints. Two Japanese firms make almost all of those mirrors. A business almost nobody has heard of can hold up every advanced chip in the world.

### In short ^in-short-5

Photomasks are the cheapest chokepoint in this chain, which is why nobody has funded an entrant. Three blank suppliers in the world on AGC's count [6](https://www.agc.com/en/hub/pr/the-japanese-glass-behind-next-generation-chips.html), one of them describing its own share as exceptionally high [8](https://www.hoya.com/ir/2025/en/review/it.html), and a single-vendor actinic inspection tool [10](https://www.lasertec.co.jp/en/ir/plan/message.html) are needed for every EUV layer of every leading-edge accelerator. Pellicles remain unproven in production, so fabs trade throughput against defect risk product by product [11](https://www.asml.com/en/news/stories/2022/the-euv-pellicle-indistinguishable-from-magic). And mask-set costs of $10 million to $40 million decide which AI chips get designed [14](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor).

Concentration **Extreme**

Substitutability **Hard** Only three firms make the blank plates for EUV masks, and only Lasertec sells the tool that checks a finished mask in EUV light.

Price or market size **A mask set for the newest chips costs roughly $10M to $40M, depending on the node and on who is estimating**

Who leads

-   JPAGC Ranks itself No.1 worldwide in EUV mask blanks and counts three suppliers in all; targeted over ¥40bn of blank sales by 2025
-   JPHoya Says its share of mask blanks is exceptionally high, and expects to keep its lead as customers add a second supplier
-   JPLasertec The only supplier of EUV mask inspection at the wavelength the scanner itself uses; JPY 230.5bn revenue in the year to June 2026
-   ATIMS Nanofabrication Intel calls it the established industry leader in multi-beam mask writers, the machines that draw the pattern onto the mask
-   USPhotronics Largest mask maker selling to outside customers; $849.3M revenue in fiscal 2025

Where it is made

-   JPJapan Mask blanks (AGC, Hoya), DUV blanks (Shin-Etsu), inspection (Lasertec), writers (NuFlare), pellicles (Mitsui Chemicals)
-   ATAustria IMS Nanofabrication multi-beam mask writers, Vienna
-   DEGermany Zeiss mask repair and metrology
-   USUnited States Photronics merchant mask shops, KLA inspection
-   TWTaiwan TSMC's in-house mask shop, and a 10% stake in IMS

Why substitution is slow

An EUV mask starts as a blank plate coated with forty layers. AGC and Hoya took two decades to learn how to make one. Three firms have now done it and the structure of the plate is published, so a newcomer knows what to build. Reaching a plate that fabs accept would take five to ten years. The harder part is inspection, because Lasertec sells the only tool that checks a mask in the same EUV light the scanner uses. Other tool makers stayed out of EUV mask inspection because the market was too small to be worth the cost, and a large budget removes that barrier.

Where China stands

SMIC runs two mask shops of its own in Shanghai, but only for the older g-line, i-line, KrF and ArF scanners. No Chinese firm makes an EUV mask blank, a tool that checks a mask in EUV light, or a multi-beam writer, the machine that draws the finest patterns onto a mask.

Where the US stands

Photronics is the largest mask maker that sells to outside customers, and KLA makes mask inspection tools, but no American firm makes an EUV mask blank or a tool that checks a mask in EUV light.

Every EUV layer on an AI accelerator needs a flawless mask, built on a blank plate that two Japanese firms supply and passed by an inspection tool that one Japanese firm makes. AGC, one of the two, says it is the only company in the world that takes an EUV blank all the way from the glass to the finished coating [1](https://www.agc.com/en/news/detail/1203819_2814.html).

### How it works ^how-it-works-5

A mask starts as a blank, a polished plate with nothing on it yet. For deep ultraviolet the blank is a window of quartz carrying a light-blocking film such as molybdenum silicide, and Shin-Etsu supplies those blanks [2](https://www.shinetsu.co.jp/en/products/electronics-materials/photomask-blanks/). For EUV the blank is a mirror of about 40 molybdenum and silicon layer pairs, 7 nm to a pair, laid on low-expansion glass, with a dark tantalum film on top, the absorber, that will carry the pattern [3](https://arxiv.org/pdf/1912.09075).

The mask shop coats the blank with resist, and a mask writer draws the design into the coating with a beam of electrons, one shape at a time, over many hours, because no light draws finely enough. A wash removes the drawn resist, an etch removes the blocking film or absorber wherever the resist is gone, and the rest of the resist is stripped. The plate now passes light, or reflects it, in the exact shape of one layer of the chip, four times larger than it will print. An inspection tool compares the plate to the design, and a repair tool fixes the stray defects it finds.

Making the plate a mirror creates its own problems:

-   **Mask 3D effects.** Light strikes the mirror at a slant, and the absorber has height, so its edges throw small shadows that distort the printed shape; software has to correct for it in advance.
-   **Write precision.** Every edge of the absorber has to sit within a few nanometers of where the design says.
-   **Particles.** Anything on the reflector prints on every wafer until someone finds it.

High-NA scanners, the newest EUV machines, print finer lines with larger mirrors, and each exposure then covers half the patch of wafer, doubling the exposures needed, so a large die, one chip's rectangle, has to be stitched from two masks [4](https://www.asml.com/en/company/stories/2024/5-things-high-na-euv). On 8 September 2026 ASML and TSMC announced a move to 12-inch masks, larger than today's, to remove that limit, with a pilot line in 2031 [5](https://www.asml.com/en/news/press-releases/2026/tsmc-and-asml-announce-industry-transition-to-large-format-photomasks-for-high-na-euv).

### Variants and trade-offs ^variants-and-trade-offs-5

#### Blanks ^blanks

Two decades of learning went into the blank: laying down forty layer pairs across a six-inch plate, flat to within less than an angstrom, a tenth of a nanometer, with no particle buried anywhere underneath. Nobody publishes a market share for EUV blanks, but AGC counts the suppliers. It says it is one of three companies worldwide that supply EUV blanks, and the only one that handles every material and process itself [6](https://www.agc.com/en/hub/pr/the-japanese-glass-behind-next-generation-chips.html). Its own data book lists EUV photomask blanks among the products where AGC holds the No.1 position worldwide [7](https://www.agc.com/en/ir/library/outline/pdf/reference.pdf).

Hoya says its share of the mask blank market is exceptionally high, and expects customers to move gradually toward multi-sourcing EUV blanks [8](https://www.hoya.com/ir/2025/en/review/it.html). AGC raised its EUV blank capacity by about 30 percent in 2025, on a line in Fukushima funded under a METI supply-chain program, and was aiming for more than ¥40 billion of sales in the business [1](https://www.agc.com/en/news/detail/1203819_2814.html).

#### Writers ^writers

An electron-beam writer cuts the pattern into a sensitive coating on the blank. Multi-beam writers fire many beams at once, which is what lets a dense EUV mask finish in a usable time, and two firms make them: IMS Nanofabrication of Vienna and Japan's NuFlare. Intel calls IMS the established leader, and sold roughly 10 percent of it to TSMC in September 2023 at a valuation near $4.3 billion [9](https://www.intc.com/news-events/press-releases/detail/1645/intel-to-sell-minority-stake-in-ims-nanofabrication).

#### Inspection and repair ^inspection-and-repair

A mask defect costs yield on every wafer that mask prints, so fabs check masks three times: as blanks, after patterning and again in production. Actinic inspection looks at 13.5 nm, the wavelength the mask itself sees, and Lasertec is the only supplier, on JPY 230.5 billion of net sales in the year to June 2026 [10](https://www.lasertec.co.jp/en/ir/plan/message.html). KLA sells optical reticle inspection; Zeiss sells e-beam repair.

#### Pellicles ^pellicles

A pellicle is a thin membrane on a frame above the mask. Particles land on it, too far out of focus to print, and the pattern below stays clean.

ASML's EUV membrane is 13 nanometers thick, has to hold together at 500 degrees Celsius in vacuum, and every photon it absorbs is light that never reaches the wafer [11](https://www.asml.com/en/news/stories/2022/the-euv-pellicle-indistinguishable-from-magic). The light crosses it twice, on the way in and on the way back off the mirror, so absorption counts double.

Carbon nanotube membranes are the intended fix, still short of production in a leading-edge fab. Imec has mounted them on reticles and exposed them in an NXE:3300 scanner, measuring single-pass transmission up to 97 percent and finding the effect on imaging low and correctable [12](https://www.imec-int.com/en/press/imec-demonstrates-cnt-pellicle-utilization-euv-scanner). Mitsui Chemicals, licensed by ASML, is building capacity at Iwakuni-Ohtake for membranes above 92 percent transmittance that can withstand sources above 1,000 W [13](https://jp.mitsuichemicals.com/en/release/2024/2024_0528_1/index.htm).

### Cost and design economics ^cost-and-design-economics

SemiAnalysis put mask sets beyond $1 million at 28 nm, beyond $10 million at 7 nm and near $40 million at 3 nm, as of 2022 [14](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor).

That cost decides who can use a node at all. A GPU spread over hundreds of thousands of units absorbs a $40 million mask set easily; the same set makes a custom inference chip shipping in the thousands uneconomic [14](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor). That cost limits AI silicon to a handful of designs.

Cost of one mask set by node, 2022 estimates$M

28 nm 1 $M 7 nm 10 $M 3 nm 40 $M

Source: [SemiAnalysis](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor)

### Who makes it ^who-makes-it-5

Mask making splits between fabs that make their own and firms that sell to everyone. TSMC, Samsung and Intel run their own leading-edge mask shops, because they want to control turnaround time. Photronics is the largest outside supplier, on $849.3 million of fiscal 2025 revenue, of which $615.1 million was IC masks [15](https://www.globenewswire.com/news-release/2025/12/10/3203040/0/en/Photronics-Reports-Full-Year-and-Fourth-Quarter-Fiscal-2025-Results.html). Toppan, Dai Nippon Printing and Hoya take most of the rest.

SMIC runs two in-house mask shops in Shanghai, for g-line, i-line, KrF and ArF tools [16](https://www.smics.com/en/site/mask). There is no Chinese EUV blank, no Chinese actinic inspection tool and no Chinese multi-beam writer.

### The chokepoint ^the-chokepoint-5

Mask blanks are as concentrated as lithography, on a fraction of the money. Three firms supply EUV blanks worldwide, AGC says [6](https://www.agc.com/en/hub/pr/the-japanese-glass-behind-next-generation-chips.html), one firm certifies them, and neither business is big enough to attract a funded entrant. Nobody starts from scratch at ¥40 billion of annual sales, to serve a handful of customers, with twenty years of defect learning ahead [1](https://www.agc.com/en/news/detail/1203819_2814.html). A business too small to fund a fourth entrant has kept the count at three.

A decade on, no pellicle membrane is transparent, tough and long-lived at once, so fabs trade throughput against defect risk. A production carbon nanotube pellicle would move EUV cost per wafer more than any scanner improvement.

### Key evaluation criteria ^key-evaluation-criteria-5

-   **Blank defectivity.** Particles buried in the multilayer cannot be repaired, so blank yield sets mask yield.
-   **Write time and placement.** Multi-beam writers make dense, curved EUV patterns affordable, and Intel calls IMS the established industry leader in them [9](https://www.intc.com/news-events/press-releases/detail/1645/intel-to-sell-minority-stake-in-ims-nanofabrication).
-   **Actinic inspectability.** Only a 13.5 nm inspection sees what the scanner sees, and only Lasertec sells one [10](https://www.lasertec.co.jp/en/ir/plan/message.html).
-   **Pellicle transmission and lifetime.** Transmission counts twice, and the best demonstrated carbon nanotube membranes pass 97 percent in a single crossing [12](https://www.imec-int.com/en/press/imec-demonstrates-cnt-pellicle-utilization-euv-scanner).
-   **Mask-set cost per node.** $10M to $40M at the leading edge, which decides which designs can use it [14](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor).

Card 1 of 4Question

What is a photomask?

Card 1 of 4Answer

The stencil that lithography prints from, one for each layer of a chip.

The same plate prints its layer on wafer after wafer, so any flaw on it repeats on every wafer. [[#^how-it-works-5|Reread: How it works]]

Card 2 of 4Question

How many firms make the blank plates for EUV masks?

Card 2 of 4Answer

Three, led by AGC and Hoya of Japan.

Only one firm, Lasertec of Japan, sells the tool that checks a finished EUV mask in EUV light. [[#^who-makes-it-5|Reread: Who makes it]]

Card 3 of 4Question

Why has no new firm entered the business?

Card 3 of 4Answer

The market is too small to pay for the years of work a newcomer would need.

The existing suppliers spent about twenty years learning to make plates without defects. [[#^the-chokepoint-5|Reread: The chokepoint]]

Card 4 of 4Question

What masks can China make?

Card 4 of 4Answer

Masks for older machines only.

No Chinese firm makes an EUV mask blank or a tool that checks an EUV mask. [[#^the-chokepoint-5|Reread: The chokepoint]]

#### Four things to remember ^four-things-to-remember-4

-   A photomask is the stencil for one layer of a chip, and any flaw on it repeats on every wafer.
-   Three firms make EUV mask blanks, and only Lasertec sells the tool that checks them in EUV light.
-   The market is too small to repay a newcomer for twenty years of learning to avoid defects.
-   China makes masks only for older machines.

Sources (16)

1.  A [AGC to Boost Production Capacity of EUVL Photomask Blanks](https://www.agc.com/en/news/detail/1203819_2814.html) AGC · 27 April 2023
2.  A [Photomask blanks - Shin-Etsu Chemical Co., Ltd.](https://www.shinetsu.co.jp/en/products/electronics-materials/photomask-blanks/) Shin-Etsu Chemical · 3 April 2019
3.  A [The refined EUV mask model I.A. MAKHOTKIN1\*, M. WU1, V. SOLTWISCH2, F. SCHOLZE2, V. PHILIPSEN1](https://arxiv.org/pdf/1912.09075) arXiv · 19 December 2019
4.  A [5 things you should know about High NA in EUV](https://www.asml.com/en/company/stories/2024/5-things-high-na-euv) ASML · 25 January 2024
5.  A [TSMC and ASML Announce Initiative to Pioneer Industry Transition to Large-Format Photomasks for High NA EUV](https://www.asml.com/en/news/press-releases/2026/tsmc-and-asml-announce-industry-transition-to-large-format-photomasks-for-high-na-euv) ASML · 8 September 2026
6.  A [The Japanese glass behind next-generation chips](https://www.agc.com/en/hub/pr/the-japanese-glass-behind-next-generation-chips.html) AGC
7.  A [AGC Data Book](https://www.agc.com/en/ir/library/outline/pdf/reference.pdf) AGC Inc. · 29 May 2026
8.  A [Information Technology Business | Review of Operations | HOYA REPORT 2025](https://www.hoya.com/ir/2025/en/review/it.html) HOYA
9.  A [Intel to Sell Minority Stake in IMS Nanofabrication Business to TSMC](https://www.intc.com/news-events/press-releases/detail/1645/intel-to-sell-minority-stake-in-ims-nanofabrication) Intel · 12 September 2023
10.  A [Business Report | Lasertec Corporation](https://www.lasertec.co.jp/en/ir/plan/message.html) Lasertec
11.  A [Indistinguishable from magic: the EUV pellicle](https://www.asml.com/en/news/stories/2022/the-euv-pellicle-indistinguishable-from-magic) ASML · 14 September 2022
12.  A [Imec demonstrates CNT pellicle utilization on EUV scanner](https://www.imec-int.com/en/press/imec-demonstrates-cnt-pellicle-utilization-euv-scanner) imec · 6 October 2020
13.  A [Mitsui Chemicals Sets up Production Facilities for CNT Pellicles to Be Used in Next-Gen EUV Lithography](https://jp.mitsuichemicals.com/en/release/2024/2024_0528_1/index.htm) Mitsui Chemicals
14.  B [The Dark Side Of The Semiconductor Design Renaissance – Fixed Costs Soaring Due To Photomask Sets, Verification, and Validation](https://newsletter.semianalysis.com/p/the-dark-side-of-the-semiconductor) SemiAnalysis · 24 July 2022
15.  A [Photronics Reports Full Year and Fourth Quarter Fiscal 2025 Results](https://www.globenewswire.com/news-release/2025/12/10/3203040/0/en/Photronics-Reports-Full-Year-and-Fourth-Quarter-Fiscal-2025-Results.html) GlobeNewswire (release by Photronics) · 10 December 2025
16.  A [Mask Service](https://www.smics.com/en/site/mask) SMIC

## Deposition and Etch ^deposition-and-etch

Lithography prints the pattern; deposition and etch do the rest, over a thousand steps per wafer, and it is the one kind of chipmaking tool where Chinese makers have gained real share.

1,561 words / 7 minSpecimen: process chamber

In plain terms

Deposition and etch build the chip itself, one layer at a time. Deposition lays down a film a few atoms thick. Lithography prints a pattern on it. Etch then eats away everything the pattern does not protect, and the next film goes down on top. A chip takes more than a thousand of these rounds. Some of the holes the etch cuts are hundreds of times deeper than they are wide, the shape of a finger-wide shaft dropping through several floors, and the film has to coat them right to the bottom. The etch has to eat one material and leave the one beside it untouched. Four firms in America, Japan and the Netherlands make most of these machines, and China has come closer to matching them here than anywhere else.

### In short ^in-short-6

Deposition and etch are the volume business of a fab: over a thousand steps per wafer, four American, Japanese and Dutch firms taking most of the money, and no monopoly like ASML's in lithography. The AI roadmap makes each step harder faster than it adds steps, because gate-all-around, HBM and backside power ask each chamber for better selectivity and deeper holes. China has closed the gap fastest in deposition and etch and slowest in ALD, the tool gate-all-around logic depends on.

Concentration **High**

Substitutability **Moderate** Most deposition and etch steps have three or four approved tool makers; atomic layer deposition is the exception.

Price or market size **Tool makers publish no list prices** World sales of chipmaking equipment were $135.1B in 2025, with wafer processing tools up 12%.

Who leads

-   USApplied Materials $28.4B revenue, fiscal 2025; leader in physical and chemical vapor deposition and in epitaxy
-   USLam Research $23.2B revenue, fiscal 2026; leader in dry etch and in metal atomic layer deposition
-   JPTokyo Electron 23% of dry etch and 38% of chemical vapor deposition, 2025
-   NLASM International €3.2B revenue, 2025; leader in single-wafer atomic layer deposition
-   CNNaura 5th largest equipment vendor worldwide, 2025 estimate

Where it is made

-   USUnited States Applied Materials (Santa Clara), Lam Research (Fremont)
-   JPJapan Tokyo Electron, Kokusai Electric, Hitachi High-Tech
-   NLNetherlands ASM International, Almere; ALD and epitaxy
-   KRSouth Korea Large buyer; Semes and local suppliers in wet processing
-   CNChina Naura, AMEC, Piotech; largest equipment market at $49.3B in 2025

Why substitution is possible

For most of the deposition and etch steps inside a fab, the tool can already be bought from three or four makers: Applied Materials, Lam, Tokyo Electron and ASM International. Switching from one maker to another means testing the new tool on the fab's own line until it matches, which takes two to five years for the newest chips. The exception is atomic layer deposition, which lays down a film one layer of atoms at a time. Chinese tool makers gained real share in etch over five years but stayed under 1 percent in atomic layer deposition, so that is the step where China is weakest.

Where China stands

Of all kinds of chipmaking tool, deposition and etch is where Chinese makers are strongest. Chinese suppliers held about 11 percent of dry etch and 7 percent of deposition in 2024, but under 1 percent of atomic layer deposition.

Where the US stands

Two of the three largest deposition and etch tool makers are American. The US government lists dry etch, atomic layer deposition and deep-hole deposition tools as controlled exports, and one rule also covers tools built outside the United States with American technology.

Applied Materials and Lam Research, the two largest deposition and etch suppliers, booked $28.4 billion and $23.2 billion of revenue in their latest fiscal years [1](https://data.sec.gov/api/xbrl/companyconcept/CIK0000006951/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json) [2](https://www.sec.gov/Archives/edgar/data/707549/000070754926000033/lrcx_exhibitx991xq4x2026.htm).

### How it works ^how-it-works-6

![](https://chipsupplychain.org/media/dep-etch-light-end.jpg)

One round of deposition and etch

Both steps happen in a vacuum chamber that holds one wafer at a time. A pump empties the chamber of air, a measured flow of gas comes in, and an electric field that reverses millions of times a second, a radio-frequency field, strips electrons off the gas molecules. The gas is now a plasma, charged fragments that react far more readily than whole molecules do.

For deposition the gas carries the material wanted. The fragments land on the wafer and stick, and the film builds from the bottom up, a few atoms at a time. To coat the floor of a deep hole as thickly as its rim, the machine can work in cycles: let one gas settle in a single layer on every surface, pump it out, admit a second gas that reacts with that layer and nothing else, pump again. Each cycle adds one layer of atoms wherever the gas reached, so the film gets to the bottom of holes hundreds of times deeper than they are wide.

For etch the gas attacks one material and leaves the one beside it. Wherever the photoresist pattern covers the wafer, nothing happens. Wherever it does not, the fragments react with the surface and turn it into a gas, which the pump carries away. A second field pulls the charged fragments straight down at the wafer, so the etch cuts vertically and a narrow hole keeps its width as it deepens. When the etch reaches the material underneath, which the gas was chosen not to touch, it slows almost to a stop, and the tool ends the step.

Change the gas, the pressure, the power and the temperature, and the same hardware either adds material or takes it away, which is why the export controls on these tools are written as process specifications.

CSET puts a single chip at more than 1,000 process steps, with the part-finished product crossing international borders 70 or more times [3](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf).

### Variants and trade-offs ^variants-and-trade-offs-6

#### Deposition families ^deposition-families

The market sizes and leading shares below are CSET's for 2025, which it builds from TechInsights data, on a $26.2 billion deposition tool market [4](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N36) and a $21.9 billion dry etch market [5](https://chipexplorer.eto.tech/?parentNode=N46&selectedNode=N103).

-   **Physical vapor deposition** knocks atoms off a solid target and lands them on the wafer, the standard method for metal barriers and seed layers, $4.9 billion in 2025 [6](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N42).
-   **Chemical vapor deposition** reacts gases at the wafer surface to grow a film; the plasma-enhanced version runs cooler and is most of the $11.2 billion CVD market, $7.5 billion in 2025 [7](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N47) [8](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N38).
-   **Atomic layer deposition** lays down less than one atomic layer at a time, so it coats vertical walls as evenly as horizontal floors. US regulators call it the basis for 3D scaling in 3D DRAM, 3D NAND and gate-all-around logic [9](https://www.govinfo.gov/content/pkg/FR-2023-10-25/pdf/2023-23049.pdf); ASM International leads it with 54.5 percent of a $4.1 billion market in 2025 [10](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N41).
-   **Epitaxy and electroplating** grow the strained silicon-germanium source and drain, and fill the copper wiring trenches [3](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf).

#### Etch families ^etch-families

-   **Conductor etch** cuts gates, metals and silicon, $12.2 billion in 2025, led by Lam at 51.2 percent [11](https://chipexplorer.eto.tech/?parentNode=N46&selectedNode=N50).
-   **Dielectric etch** cuts the insulating oxides and nitrides between them, $8.7 billion in 2025, led by Tokyo Electron at 55.9 percent [12](https://chipexplorer.eto.tech/?parentNode=N46&selectedNode=N51).
-   **High-aspect-ratio etch** decides whether memory works at all: a 3D NAND channel or DRAM capacitor is a hole far deeper than it is wide that has to come out straight. Lam chills the wafer to sharpen the profile, and says Cryo 3.0 holds critical-dimension deviation under 0.1 percent down channels 10 microns deep [13](https://newsroom.lamresearch.com/2024-07-31-Lam-Research-Introduces-Lam-Cryo-TM-3-0-Cryogenic-Etch-Technology-to-Accelerate-Scaling-of-3D-NAND-for-the-AI-Era).

AI hardware asks for sideways cuts, deeper holes and a second metal stack on the wafer's back.

-   **Gate-all-around** needs isotropic etch, which cuts sideways, to release the silicon nanosheets from the silicon-germanium between them, and BIS ties its dry etch controls to exactly that [9](https://www.govinfo.gov/content/pkg/FR-2023-10-25/pdf/2023-23049.pdf).
-   **HBM** needs holes etched straight through the silicon so chips can be stacked and wired, which BIS controls at 10:1 or deeper above 7 microns a minute [14](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf).
-   **Backside power delivery** adds thinning, backside vias and a second metal stack. Applied Materials expects it to add about $1 billion per 100,000 wafer starts a month to its wiring business [15](https://www.globenewswire.com/news-release/2024/07/08/2909540/0/en/applied-materials-unveils-chip-wiring-innovations-for-more-energy-efficient-computing.html).

Tokyo Electron world market share by tool type, 2025%

Coater/developer 91% CVD 38% Oxidation/diffusion 31% Deposition systems 27% Dry etch 23% Cleaning 20% ALD 15%

Source: [Tokyo Electron FY2026 Q4 results presentation](https://www.tel.com/ir/library/report/pjuomj00000000tf-att/fy26q4transcript-e.pdf)

### Who makes it ^who-makes-it-6

SEMI put global equipment billings at $135.1 billion in 2025, up 15 percent from $117.1 billion, with wafer processing equipment up 12 percent [17](https://www.semi.org/en/SEMI-Reports-Global-Semiconductor-Equipment-Billings-Reached-135-Billion-in-2025).

Within deposition and etch no one firm dominates as ASML does in lithography. The share chart in Tokyo Electron's own results presentation puts it at 23 percent of dry etch, 27 percent of deposition systems and 15 percent of ALD in 2025, against 91 percent of coater/developer [16](https://www.tel.com/ir/library/report/pjuomj00000000tf-att/fy26q4transcript-e.pdf).

ASM International, the atomic layer deposition specialist, reached a record EUR 3.2 billion of revenue in 2025 as customers built 2 nm gate-all-around capacity, with molybdenum ALD entering volume production [18](https://www.asm.com/media/yvxbavwe/20260303-asm-reports-q4-and-full-year-2025-results.pdf).

What the world spent on chipmaking equipment$B

2024 117.1 2025 135.1

Source: [SEMI, Worldwide Semiconductor Equipment Market Statistics](https://www.semi.org/en/SEMI-Reports-Global-Semiconductor-Equipment-Billings-Reached-135-Billion-in-2025)

### China and the controls ^china-and-the-controls

China is the tool vendors' largest customer and their fastest-improving competitor. It bought $49.3 billion of equipment in 2025, still the biggest single market, though its spending fell half a percent while Taiwan's rose 90 percent to $31.5 billion [17](https://www.semi.org/en/SEMI-Reports-Global-Semiconductor-Equipment-Billings-Reached-135-Billion-in-2025). China still takes a large share of every major vendor's sales.

-   **Tokyo Electron**: 34.1 percent of sales in the year to March 2026, down from 41.7 percent [16](https://www.tel.com/ir/library/report/pjuomj00000000tf-att/fy26q4transcript-e.pdf).
-   **Lam Research**: 26 percent in the June 2026 quarter, behind Taiwan at 27 percent [2](https://www.sec.gov/Archives/edgar/data/707549/000070754926000033/lrcx_exhibitx991xq4x2026.htm).
-   **Applied Materials**: 28 percent in the third fiscal quarter of 2026, down from 35 percent [19](https://www.globenewswire.com/news-release/2026/08/13/3344890/0/en/applied-materials-announces-third-quarter-2026-results.html).
-   **ASM International**: more than 30 percent of 2025 revenue [18](https://www.asm.com/media/yvxbavwe/20260303-asm-reports-q4-and-full-year-2025-results.pdf).

Between 2019 and 2024 China-based suppliers went from 2 to 7 percent of deposition and from under 3 to about 9 percent of etch and clean, 11 percent in dry etch alone. In ALD they gained nothing and stayed under 1 percent [20](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/). AMEC, the biggest of them, turned over RMB 12.385 billion in 2025, up 36.6 percent, and spent RMB 3.744 billion on research, 30.2 percent of sales [21](https://www.amec-inc.com/news/708.html).

Washington tightened these rules four times between 2022 and 2025.

-   **October 2022.** The 7 October interim final rule put manufacturing equipment and US person support under license and widened foreign-produced item rules for 28 listed Chinese entities [22](https://www.govinfo.gov/content/pkg/FR-2022-10-13/pdf/2022-21658.pdf).
-   **October 2023.** The rule effective 17 November rewrote the equipment entries, adding isotropic and anisotropic dry etch (ECCN 3B001.c.1), spatial ALD (3B001.d.9), low-fluorine tungsten ALD and CVD (3B001.d.10) and carbon hard mask PECVD (3B001.d.5) [9](https://www.govinfo.gov/content/pkg/FR-2023-10-25/pdf/2023-23049.pdf).
-   **December 2024.** BIS controlled 24 more types of equipment and three types of software, added 140 entities and wrote a foreign direct product rule that reaches tools built outside the United States [23](https://www.bis.gov/press-release/commerce-strengthens-export-controls-restrict-chinas-capability-produce-advanced-semiconductors-military). The new entries take in TSV etch and deposition into features deeper than 200:1 [14](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf).
-   **September 2025.** The Affiliates Rule extended Entity List restrictions to any company at least 50 percent owned by a listed entity [24](https://www.govinfo.gov/content/pkg/FR-2025-09-30/pdf/2025-19001.pdf); BIS then stayed it to 9 November 2026 [25](https://www.govinfo.gov/content/pkg/FR-2025-11-12/pdf/2025-19846.pdf).

Applied Materials took a $253 million charge to settle an export controls matter [19](https://www.globenewswire.com/news-release/2026/08/13/3344890/0/en/applied-materials-announces-third-quarter-2026-results.html), so the rules reach the vendors as well as their customers.

China-based suppliers' share of global tool segments, 2024%

Dry stripping 35% Dry etch 11% CMP 11% PVD 10% Etch and clean 9% Deposition 7% CVD 7% Lithography (i-line) 4%

Source: [CSET, Inside Beijing’s Chipmaking Offensive](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/)

### The chokepoint ^the-chokepoint-6

The chokepoint is real but weaker than lithography's. Three or four credible vendors exist for most of the deposition and etch steps inside a fab. The exceptions are ALD, where China holds under 1 percent [20](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/), and the extremely deep, narrow holes that HBM and 3D memory need. The December 2024 rule targets those [14](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf).

### Key evaluation criteria ^key-evaluation-criteria-6

-   **Selectivity.** How hard the process attacks one material and spares another. BIS controls wet processing at a silicon-germanium-to-silicon ratio of 100:1 [9](https://www.govinfo.gov/content/pkg/FR-2023-10-25/pdf/2023-23049.pdf).
-   **Conformality and aspect ratio.** Whether a film reaches the bottom of a hole, and how deep that hole is against its width. Controls start at 10:1 for TSV etch and 200:1 for 3D DRAM deposition [14](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf).
-   **Uniformity.** Variation across a 300 mm wafer, with under 2 percent treated as an advanced-manufacturing marker [14](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf).
-   **Throughput.** Wafers per hour, which sets cost per layer and decides how many lots a fab can run.
-   **Particles and chamber matching.** How large a share of the defects a fab can tolerate comes from these tools, and whether one chamber behaves like the next, which {++{"author":"James's AI","timestamp":1790593576251}@@metrology and inspection ++}measure (see [[#^metrology-and-inspection|Metrology and inspection]]).

Card 1 of 4Question

What do deposition and etch do?

Card 1 of 4Answer

Deposition lays down a thin film, and etch cuts away the parts the printed pattern leaves exposed.

A chip takes more than a thousand of these rounds, one layer at a time. [[#^how-it-works-6|Reread: How it works]]

Card 2 of 4Question

Who makes most deposition and etch tools?

Card 2 of 4Answer

Four firms: Applied Materials, Lam Research, Tokyo Electron and ASM International.

They are American, Japanese and Dutch. No single firm dominates the way ASML does in lithography. [[#^who-makes-it-6|Reread: Who makes it]]

Card 3 of 4Question

In which kind of chipmaking tool have Chinese makers come closest to the leaders?

Card 3 of 4Answer

Deposition and etch.

Chinese suppliers held about 11 percent of dry etch and 7 percent of deposition in 2024. [[#^china-and-the-controls|Reread: China and the controls]]

Card 4 of 4Question

Which deposition tool is China furthest behind in?

Card 4 of 4Answer

Atomic layer deposition, with under 1 percent of the market.

The newest gate-all-around transistors depend on it. [[#^china-and-the-controls|Reread: China and the controls]]

#### Four things to remember ^four-things-to-remember-5

-   Deposition lays down thin films and etch cuts them into patterns, over more than a thousand rounds per chip.
-   Four American, Japanese and Dutch firms make most of these tools, and none dominates.
-   Chinese makers have come closest to the leaders here, with about 11 percent of dry etch in 2024.
-   China is furthest behind in atomic layer deposition, which the newest transistors depend on.

Sources (25)

1.  A [Revenue from Contract with Customer, Excluding Assessed Tax (us-gaap:RevenueFromContractWithCustomerExcludingAssessedTax) reported by APPLIED MATERIALS INC /DE, XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0000006951/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json) U.S. Securities and Exchange Commission (XBRL data for APPLIED MATERIALS INC /DE)
2.  A [LAM RESEARCH CORP, Form 8-K current report for the period ended 2026-07-29 (8-K)](https://www.sec.gov/Archives/edgar/data/707549/000070754926000033/lrcx_exhibitx991xq4x2026.htm) U.S. Securities and Exchange Commission (filing by LAM RESEARCH CORP) · 29 July 2026
3.  A [The Semiconductor Supply Chain - Issue Brief](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf) Center for Security and Emerging Technology (CSET) · 21 January 2021
4.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N36) Emerging Technology Observatory (ETO)
5.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N46&selectedNode=N103) Emerging Technology Observatory (ETO)
6.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N42) Emerging Technology Observatory (ETO)
7.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N47) Emerging Technology Observatory (ETO)
8.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N38) Emerging Technology Observatory (ETO)
9.  A [Export Controls on Semiconductor Manufacturing Items](https://www.govinfo.gov/content/pkg/FR-2023-10-25/pdf/2023-23049.pdf) U.S. Government Publishing Office (Federal Register) · 25 October 2023
10.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N35&selectedNode=N41) Emerging Technology Observatory (ETO)
11.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N46&selectedNode=N50) Emerging Technology Observatory (ETO)
12.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N46&selectedNode=N51) Emerging Technology Observatory (ETO)
13.  A [Lam Research Introduces Lam Cryo™ 3.0 Cryogenic Etch Technology to Accelerate Scaling of 3D NAND for the AI Era](https://newsroom.lamresearch.com/2024-07-31-Lam-Research-Introduces-Lam-Cryo-TM-3-0-Cryogenic-Etch-Technology-to-Accelerate-Scaling-of-3D-NAND-for-the-AI-Era) Lam Research · 31 July 2024
14.  A [Foreign-Produced Direct Product Rule Additions, and Refinements to Controls for Advanced Computing and Semiconductor Manufacturing Items](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf) U.S. Government Publishing Office (Federal Register) · 5 December 2024
15.  A [Applied Materials Unveils Chip Wiring Innovations for More Energy-Efficient Computing](https://www.globenewswire.com/news-release/2024/07/08/2909540/0/en/applied-materials-unveils-chip-wiring-innovations-for-more-energy-efficient-computing.html) GlobeNewswire (release by Applied Materials) · 8 July 2024
16.  A [Investor Relations / April 30, 2026](https://www.tel.com/ir/library/report/pjuomj00000000tf-att/fy26q4transcript-e.pdf) Tokyo Electron · 30 April 2026
17.  A [SEMI Reports Global Semiconductor Equipment Billings Reached $135 Billion in 2025, Up 15% Year-on-Year](https://www.semi.org/en/SEMI-Reports-Global-Semiconductor-Equipment-Billings-Reached-135-Billion-in-2025) SEMI · 7 April 2026
18.  A [Press Release Q4, 2025 text](https://www.asm.com/media/yvxbavwe/20260303-asm-reports-q4-and-full-year-2025-results.pdf) ASM International · 3 March 2026
19.  A [Applied Materials Announces Third Quarter 2026 Results](https://www.globenewswire.com/news-release/2026/08/13/3344890/0/en/applied-materials-announces-third-quarter-2026-results.html) GlobeNewswire (release by Applied Materials) · 13 August 2026
20.  A [Inside Beijing’s Chipmaking Offensive](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/) Center for Security and Emerging Technology (CSET) · 14 July 2025
21.  A [AMEC holds its 2025 annual results briefing (中微公司成功举办2025年度业绩说明会)](https://www.amec-inc.com/news/708.html) Advanced Micro-Fabrication Equipment (AMEC) · 1 April 2026
22.  A [Implementation of Additional Export Controls: Certain Advanced Computing and Semiconductor Manufacturing Items; Supercomputer and Semiconductor End Use; Entity List Modification](https://www.govinfo.gov/content/pkg/FR-2022-10-13/pdf/2022-21658.pdf) U.S. Government Publishing Office (Federal Register) · 13 October 2022
23.  A [Commerce Strengthens Export Controls to Restrict China's Capability to Produce Advanced Semiconductors for Military Applications](https://www.bis.gov/press-release/commerce-strengthens-export-controls-restrict-chinas-capability-produce-advanced-semiconductors-military) U.S. Bureau of Industry and Security · 2 December 2024
24.  A [Expansion of End-User Controls To Cover Affiliates of Certain Listed Entities](https://www.govinfo.gov/content/pkg/FR-2025-09-30/pdf/2025-19001.pdf) U.S. Government Publishing Office (Federal Register) · 30 September 2025
25.  A [One Year Suspension of Expansion of End-User Controls for Affiliates of Certain Listed Entities](https://www.govinfo.gov/content/pkg/FR-2025-11-12/pdf/2025-19846.pdf) U.S. Government Publishing Office (Federal Register) · 12 November 2025

## Metrology and Inspection ^metrology-and-inspection

No fab is planned around measuring and inspecting wafers, and no fab works without it. One American firm holds about 57% of the market for those tools, roughly seven times its nearest rival, and its share is still growing.

1,541 words / 7 minSpecimen: electron microscope column

In plain terms

Metrology and inspection are the factory's quality control. Between the steps that build a chip, another machine looks the wafer over. It checks whether the lines are the right width, whether this layer landed squarely on the last one, and whether a speck of dirt has killed a circuit. An AI accelerator is the part built to run AI, and its main chip, the one that does the calculating, is one of the largest cut from a wafer. A bigger chip is a bigger target for a speck. On a chip that size, halving the stray specks lifts the share of working chips from about half to about seven in ten. One American firm sells seven times as many of those machines as its nearest rival, so a chip factory, or fab, cut off from it can buy every other tool and still not learn why its chips fail.

### In short ^in-short-7

Yield is set by defect density and die area, and AI accelerators have the largest dies in production. KLA holds about 57 percent of the market, six to seven times its nearest rival, and is still gaining [2](https://d1io3yog0oux5.cloudfront.net/_7791115a123b86b3f10b1a5eb5210224/klatencor/db/1166/10653/file/2026+Investor+Day+Master+Final_IR+copy.pdf), with Applied Materials, Lasertec, Hitachi High-Tech, ASML, Nova, Onto and Camtek splitting the rest [3](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60). KLA's packaging process control revenue is heading toward $1.1 billion in 2026 [1](https://d1io3yog0oux5.cloudfront.net/_b9ee755a5f60dd0fb3f9e27967aed6af/klatencor/db/1117/10668/letter_to_shareholders/KLA+Earnings+Shareholder+Letter+-+Q4+FY26.pdf). No one has recorded a Chinese gain in process control, which is why the controls on it are the ones China can least easily answer with domestic tools.

Concentration **High**

Substitutability **Moderate** KLA is the largest maker of measuring and inspecting tools, but every kind has a second maker, so losing KLA would slow a fab without stopping it.

Price or market size **A $15.7B process control tool market in 2025, about 57% of it KLA's** KLA's fiscal 2026 revenue was $13.58B against a wafer equipment market of roughly $120B in 2025, so process control is around a tenth of what a fab spends on tools.

Who leads

-   USKLA 56.5% of process control in 2024 on its own investor-day count, 6.5 times its nearest rival; $13.58B revenue, fiscal 2026
-   USApplied Materials 11.2% of process control tools in 2025: electron-beam defect review, line-width measurement and film metrology
-   JPLasertec 6.4% of process control tools in 2025, almost all of it mask inspection
-   NLASML 5.9% of process control tools in 2025: YieldStar layer alignment and HMI multibeam electron inspection
-   ILNova 4.3% of process control tools in 2025; $880.6M revenue, 2025
-   USOnto Innovation 2.6% of process control tools in 2025; $1.01B revenue, 2025

Where it is made

-   USUnited States KLA (Milpitas), Onto Innovation (Wilmington, MA), Applied Materials
-   NLNetherlands ASML YieldStar and HMI e-beam, Veldhoven and San Jose
-   JPJapan Hitachi High-Tech CD-SEM; Lasertec mask inspection; Rigaku X-ray
-   ILIsrael Nova (Rehovot) and Camtek (Migdal Haemek)
-   CNChina Domestic entrants only; 0.7% of the process control tool market in 2025

Why substitution is possible

Metrology and inspection tools measure and inspect wafers so a fab can find and fix faults in its process. KLA is the biggest maker, but seven other firms ship approved tools, and three of them are the leader in one kind of tool. A fab that loses KLA and buys from the others keeps running. It finds fewer flaws and fixes them more slowly, and it needs two to five years to return to its old performance. A country that is not allowed to buy from any of them would take far longer: Chinese firms held 0.7 percent of the market for these tools in 2025.

Where China stands

Of all major kinds of chipmaking tool, metrology and inspection is where Chinese makers are weakest. In 2019 Chinese firms held 3.4 percent of line-width measurement, 1.3 percent of defect inspection and none of mask or packaging inspection. In 2025 they still held 0.7 percent of the whole market for these tools. CSET's 2026 survey of Chinese share gains covers deposition, etch, polishing, lithography, packaging and test, and does not cover measurement and inspection.

Where the US stands

KLA is the largest maker of metrology and inspection tools in the world. It puts its own 2024 share at 56.5 percent, or 6.5 times its nearest rival. CSET's Supply Chain Explorer puts it at 56.8 percent of the 2025 market. American firms hold 72 percent of this market and Japanese firms 14 percent. A December 2024 US rule added inspection and measurement tools for patterned 300 mm wafers to the controlled list, for tools that can find defects 21 nm across or smaller.

Process control is about a tenth of what a fab spends on tools, out of a wafer equipment market of roughly $120 billion in 2025 [1](https://d1io3yog0oux5.cloudfront.net/_b9ee755a5f60dd0fb3f9e27967aed6af/klatencor/db/1117/10668/letter_to_shareholders/KLA+Earnings+Shareholder+Letter+-+Q4+FY26.pdf). At its March 2026 investor day KLA put its own 2024 share at 56.5 percent, six and a half times its nearest competitor [2](https://d1io3yog0oux5.cloudfront.net/_7791115a123b86b3f10b1a5eb5210224/klatencor/db/1166/10653/file/2026+Investor+Day+Master+Final_IR+copy.pdf); CSET's own count for 2025 is 56.8 percent [3](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60).

### How it works ^how-it-works-7

An inspection tool sweeps a beam of light across the wafer, photographs it, and compares the image of each chip with the image of its neighbors. The chips on a wafer are meant to be identical, so anything that shows in one and not the others is a defect, and the tool records where it is. For faults too small for light to show, a second tool scans a beam of electrons across a small patch and builds a picture from the electrons that bounce back.

A metrology tool measures known shapes. It shines light on a test pattern printed beside the circuits and works out from the scatter how wide the lines are and how thick the film is, and it reads marks printed in this layer and the last to measure how far the two are out of line, which is overlay.

The fab pays for all this to protect yield, the share of chips on a wafer that work. A wafer loses value two ways: whole regions ruined by mishandling, misalignment or over-etching, and single circuits killed by stray material or an airborne particle [4](https://web.ece.ucsb.edu/~parhami/docs_folder/f33-book-dep-comp-pt2.pdf).

A bigger chip is a bigger target for the second kind, and the loss grows faster than the area. In the standard formula, die yield is (1 + D0A/a) to the power minus a, where D0 is defects per square centimeter, A is die area and a is a clustering constant of 3 to 4, which says how much defects bunch together. At a defect density of 0.8 a 1 square centimeter die yields 49 percent and a 2 by 2 centimeter die 11 percent, so the bigger die costs about twenty times as much [4](https://web.ece.ucsb.edu/~parhami/docs_folder/f33-book-dep-comp-pt2.pdf).

Run that equation with a clustering constant of 3 for an 8 square centimeter die, about as much as one exposure can print, and it yields about 49 percent at a defect density of 0.10 and about 69 percent at 0.05 [4](https://web.ece.ucsb.edu/~parhami/docs_folder/f33-book-dep-comp-pt2.pdf). Getting from one to the other is yield learning: find which of the thousand-odd steps is losing dies, fix it, move on.

![](https://chipsupplychain.org/media/defects-light-end.jpg)

Why big chips lose more to defects

### Variants and trade-offs ^variants-and-trade-offs-7

The tools trade sensitivity against speed. All the market sizes and shares below are CSET's, for 2025 [3](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60).

-   **Defect inspection** scans a whole wafer with light or electrons and compares each die against its neighbors. It is by far the largest family, $6.7 billion, and the one KLA dominates, at 85.9 percent. ASML's HMI eScan 1100 runs 25 electron beams at once, up to 15 times the speed of a single beam, and finds patterning defects down to 7 nm [5](https://www.asml.com/en/products/metrology-and-inspection-systems/hmi-escan-1100).
-   **Film and shape metrology** measures how thick each film is and how flat the wafer sits, without cutting it open: $2.6 billion, with KLA at 45.6 percent, Nova at 24.6 and Onto Innovation at 10.9. Onto paid about $720 million in August 2026 for 27 percent of Japan's X-ray maker Rigaku [6](https://investors.ontoinnovation.com/news/news-details/2026/Onto-Innovation-Completes-Strategic-Investment-in-Rigaku-Holdings-Corporation/default.aspx).
-   **Mask inspection and repair** gets its own tools, because a defect on a mask repeats on every die: $2.2 billion, and the one family where KLA has a close rival, 45.9 percent against Lasertec's 42 and Zeiss's 10.1.
-   **Overlay metrology** measures whether this layer sits on the one below: $991 million, split almost evenly between KLA at 51.5 percent and ASML at 47.9.
-   **Critical dimension metrology** measures how wide a printed feature actually came out: $1.2 billion, and the one family Japan leads, with Hitachi at 71.9 percent and Applied Materials at 27.5.
-   **Electron-beam metrology** resolves detail too fine for light: $1.3 billion, led by Applied Materials at 45.1 percent with ASML at 35.6 and KLA at 18.8.

Process control market by tool family, 2025$M

Defect inspection 6,700 Film and shape metrology 2,600 Mask inspection and repair 2,200 E-beam metrology 1,300 CD metrology 1,200 Overlay metrology 991.4 Defect review 729.1

Source: [ETO Supply Chain Explorer, CSET](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60)

### Who makes it ^who-makes-it-7

KLA is most of the segment: 56.8 percent of a $15.7 billion market in 2025 [3](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60), up two points since 2021 by its own figures [2](https://d1io3yog0oux5.cloudfront.net/_7791115a123b86b3f10b1a5eb5210224/klatencor/db/1166/10653/file/2026+Investor+Day+Master+Final_IR+copy.pdf). Its fiscal 2026 revenue was $13.579 billion, after $12.156 billion in fiscal 2025 [7](https://data.sec.gov/api/xbrl/companyconcept/CIK0000319201/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json), and it says it gained share again in 2025 across mask, optical wafer and e-beam inspection [8](https://d1io3yog0oux5.cloudfront.net/_a357bfc9113388e37f3bfcb2ea2f0b64/klatencor/db/1117/10655/letter_to_shareholders/KLA+Shareholder+Letter+-+Q3+FY26.pdf).

Process control tool revenue share, 2025%

KLA **56.8%** Applied Materials **11.2%** Lasertec **6.4%** Hitachi High-Tech **6.2%** ASML **5.9%** Nova **4.3%** Onto Innovation **2.6%** Camtek **1.6%** Rigaku **1.2%** All others **3.8%**

%% validator-ignore-next-line --code article.block-repeated-nearby --reason source-provides-alternative-citation-formats %%
Source: [ETO Supply Chain Explorer, CSET](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60)

The rest are specialists, and nobody else reaches 11 percent.

-   **Applied Materials** is the largest of them at 10.5 percent, selling e-beam defect review, CD-SEM line-width tools and film metrology next to the deposition and etch tools that create the defects.
-   **Lasertec** holds 7.7 percent, almost all of it mask inspection; **Hitachi High-Tech** 5.6 percent, almost all of it CD-SEM; **ASML** 5.2 percent through YieldStar overlay and HMI e-beam inspection.
-   **Nova** holds 3.7 percent and took $880.6 million in 2025 on optical film and dimensional metrology [9](https://data.sec.gov/api/xbrl/companyconcept/CIK0001109345/us-gaap/Revenues.json).
-   **Onto Innovation** holds 3.0 percent on $1,005.3 million of 2025 revenue [10](https://investors.ontoinnovation.com/news/news-details/2026/Onto-Innovation-Reports-2025-Fourth-Quarter-and-Full-Year-Results/default.aspx) and **Camtek** 1.5 percent on $496.1 million [11](https://www.sec.gov/Archives/edgar/data/1109138/000117891326000549/zk2634405.htm).

Patterning, which covers overlay and mask inspection, grew 61 percent year on year in the June 2026 quarter, when Taiwan took 31 percent of revenue and China 26 percent [1](https://d1io3yog0oux5.cloudfront.net/_b9ee755a5f60dd0fb3f9e27967aed6af/klatencor/db/1117/10668/letter_to_shareholders/KLA+Earnings+Shareholder+Letter+-+Q4+FY26.pdf).

KLA revenue by product line, June 2026 quarter%

Wafer inspection **49%** Services **22%** Patterning **20%** PCB and component inspection **4%** Specialty semiconductor process **4%** Other **1%**

Source: [KLA letter to shareholders, Q4 FY2026](https://d1io3yog0oux5.cloudfront.net/_b9ee755a5f60dd0fb3f9e27967aed6af/klatencor/db/1117/10668/letter_to_shareholders/KLA+Earnings+Shareholder+Letter+-+Q4+FY26.pdf)

Process control's share of fab spending is still rising, and KLA credits tighter specifications, less built-in redundancy and more logic inside memory built for high-performance computing [8](https://d1io3yog0oux5.cloudfront.net/_a357bfc9113388e37f3bfcb2ea2f0b64/klatencor/db/1117/10655/letter_to_shareholders/KLA+Shareholder+Letter+-+Q3+FY26.pdf).

The advantage is analytics as much as optics: inspection produces far more candidate defects than engineers can look at, and KLA has spent five years putting AI classification through its whole line [8](https://d1io3yog0oux5.cloudfront.net/_a357bfc9113388e37f3bfcb2ea2f0b64/klatencor/db/1117/10655/letter_to_shareholders/KLA+Shareholder+Letter+-+Q3+FY26.pdf).

### Packaging, AI and China ^packaging-ai-and-china

The AI packaging build-out is where this segment is growing fastest. KLA took the number one position in advanced wafer-level packaging process control in 2025, adding 14 points [8](https://d1io3yog0oux5.cloudfront.net/_a357bfc9113388e37f3bfcb2ea2f0b64/klatencor/db/1117/10655/letter_to_shareholders/KLA+Shareholder+Letter+-+Q3+FY26.pdf), and expects about $1.1 billion of packaging process control revenue in 2026, more than 70 percent growth [1](https://d1io3yog0oux5.cloudfront.net/_b9ee755a5f60dd0fb3f9e27967aed6af/klatencor/db/1117/10668/letter_to_shareholders/KLA+Earnings+Shareholder+Letter+-+Q4+FY26.pdf). Onto signed a volume purchase agreement worth over $240 million with an HBM maker for 2D inspection and 3D bump metrology through 2027 [10](https://investors.ontoinnovation.com/news/news-details/2026/Onto-Innovation-Reports-2025-Fourth-Quarter-and-Full-Year-Results/default.aspx).

China has made less progress in process control than anywhere else in the tool chain. In 2019 Chinese firms held 3.4 percent of line-width measurement, 1.3 percent of defect inspection and none of photomask or packaging inspection [12](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf). Six years later they were at 0.7 percent of the whole process control tool market [3](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60). CSET's 2026 audit of where China gained runs through deposition, etch, polishing, lithography, packaging and test, and never reaches process control [13](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/).

The December 2024 rule wrote process control into the export lists. It controls defect inspection and measurement of patterned 300 mm wafers where the tool can find defects of 21 nm or smaller using light below 400 nm, or an electron beam resolving 1.65 nm, or a cold field emission source, or two or more beams [14](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf). A foreign direct product rule carries the same reach to tools built outside the United States [15](https://www.bis.gov/press-release/commerce-strengthens-export-controls-restrict-chinas-capability-produce-advanced-semiconductors-military).

### The chokepoint ^the-chokepoint-7

Process control is a chokepoint of concentration. Several firms can build a good film metrology tool, but one firm sets the standard across nearly the whole flow, and its lead is widening. A sanctioned fab can buy scanners and etchers on the gray market and still fail to get production going, because without sensitive inspection it cannot find out why its yield is low.

### Key evaluation criteria ^key-evaluation-criteria-7

-   **Sensitivity.** The smallest killer defect a tool can find. ASML's multibeam system is specified to 7 nm patterning defects [5](https://www.asml.com/en/products/metrology-and-inspection-systems/hmi-escan-1100).
-   **Throughput.** Wafers per hour, which decides how many lots a fab can afford to look at; multibeam buys up to 15x over single-beam [5](https://www.asml.com/en/products/metrology-and-inspection-systems/hmi-escan-1100).
-   **Nuisance rate.** The share of flagged events that turn out not to be real defects, which is what AI classification is meant to reduce.
-   **Sampling plan.** How many wafers and sites per lot, a cost decision as much as a physics one, which sets what process control costs the fab.
-   **Time to result.** How fast a measurement reaches the process engineer, which sets the speed of yield learning.

Card 1 of 4Question

What do metrology and inspection tools do?

Card 1 of 4Answer

They check each wafer between steps for line width, layer alignment and defects.

Their measurements tell a fab why its chips fail. [[#^how-it-works-7|Reread: How it works]]

Card 2 of 4Question

Why do AI chips depend so much on finding defects?

Card 2 of 4Answer

They are among the largest chips made, and a bigger chip is more likely to catch a defect.

On a chip that size, halving the defects raises the share of working chips from about half to about seven in ten. [[#^packaging-ai-and-china|Reread: Packaging, AI and China]]

Card 3 of 4Question

Who leads the market for these tools?

Card 3 of 4Answer

KLA, an American firm, with about 57 percent.

That is six to seven times its nearest rival. Every kind of tool still has a second maker. [[#^who-makes-it-7|Reread: Who makes it]]

Card 4 of 4Question

How strong are Chinese makers of these tools?

Card 4 of 4Answer

Weaker than in any other major kind of chipmaking tool.

They held 0.7 percent of the market in 2025. [[#^packaging-ai-and-china|Reread: Packaging, AI and China]]

#### Four things to remember ^four-things-to-remember-6

-   Metrology and inspection tools check each wafer between steps and tell a fab why its chips fail.
-   AI chips are among the largest made, so finding defects matters most for them.
-   KLA of the United States holds about 57 percent of the market, six to seven times its nearest rival.
-   Chinese makers are weakest here, with 0.7 percent of the market in 2025.

Sources (15)

1.  A [Letter to Shareholders Q4 Fiscal 2026](https://d1io3yog0oux5.cloudfront.net/_b9ee755a5f60dd0fb3f9e27967aed6af/klatencor/db/1117/10668/letter_to_shareholders/KLA+Earnings+Shareholder+Letter+-+Q4+FY26.pdf) KLA Corporation · 27 July 2026
2.  A [Compounding Sustainable Outperformance](https://d1io3yog0oux5.cloudfront.net/_7791115a123b86b3f10b1a5eb5210224/klatencor/db/1166/10653/file/2026+Investor+Day+Master+Final_IR+copy.pdf) KLA Corporation · 13 March 2026
3.  A [Supply Chain Explorer: Advanced Chips](https://chipexplorer.eto.tech/?parentNode=N118&selectedNode=N60) Emerging Technology Observatory (ETO)
4.  A [Behrooz Parhami, Dependable Computing: A Multilevel Approach, part 2](https://web.ece.ucsb.edu/~parhami/docs_folder/f33-book-dep-comp-pt2.pdf) University of California, Santa Barbara · 11 October 2020
5.  A [The HMI eScan 1100](https://www.asml.com/en/products/metrology-and-inspection-systems/hmi-escan-1100) ASML
6.  A [Onto Innovation Completes Strategic Investment in Rigaku Holdings Corporation](https://investors.ontoinnovation.com/news/news-details/2026/Onto-Innovation-Completes-Strategic-Investment-in-Rigaku-Holdings-Corporation/default.aspx) Onto Innovation · 10 August 2026
7.  A [Revenue from Contract with Customer, Excluding Assessed Tax (us-gaap:RevenueFromContractWithCustomerExcludingAssessedTax) reported by KLA CORP, XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0000319201/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json) U.S. Securities and Exchange Commission (XBRL data for KLA CORP)
8.  A [Letter to Shareholders Q3 Fiscal 2026](https://d1io3yog0oux5.cloudfront.net/_a357bfc9113388e37f3bfcb2ea2f0b64/klatencor/db/1117/10655/letter_to_shareholders/KLA+Shareholder+Letter+-+Q3+FY26.pdf) KLA Corporation · 29 April 2026
9.  A [Revenues (us-gaap:Revenues) reported by NOVA LTD., XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0001109345/us-gaap/Revenues.json) U.S. Securities and Exchange Commission (XBRL data for NOVA LTD.)
10.  A [Onto Innovation Reports 2025 Fourth Quarter and Full Year Results](https://investors.ontoinnovation.com/news/news-details/2026/Onto-Innovation-Reports-2025-Fourth-Quarter-and-Full-Year-Results/default.aspx) Onto Innovation · 19 February 2026
11.  A [CAMTEK LTD, Form 6-K report of foreign private issuer for the period ended 2026-02-18 (6-K)](https://www.sec.gov/Archives/edgar/data/1109138/000117891326000549/zk2634405.htm) U.S. Securities and Exchange Commission (filing by CAMTEK LTD) · 18 February 2026
12.  A [The Semiconductor Supply Chain - Issue Brief](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf) Center for Security and Emerging Technology (CSET) · 21 January 2021
13.  A [Inside Beijing’s Chipmaking Offensive](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/) Center for Security and Emerging Technology (CSET) · 14 July 2025
14.  A [Foreign-Produced Direct Product Rule Additions, and Refinements to Controls for Advanced Computing and Semiconductor Manufacturing Items](https://www.govinfo.gov/content/pkg/FR-2024-12-05/pdf/2024-28270.pdf) U.S. Government Publishing Office (Federal Register) · 5 December 2024
15.  A [Commerce Strengthens Export Controls to Restrict China's Capability to Produce Advanced Semiconductors for Military Applications](https://www.bis.gov/press-release/commerce-strengthens-export-controls-restrict-chinas-capability-produce-advanced-semiconductors-military) U.S. Bureau of Industry and Security · 2 December 2024

## Transistors and the Front End ^transistors-and-the-front

Three companies can build a 2 nm-class transistor. Shrinking stopped lowering the cost per transistor about a decade ago, and every gain since has come from extra process steps.

1,553 words / 7 minSpecimen: gate-all-around transistor

In plain terms

The front end of a chip factory is the part that builds the transistors, the billions of tiny switches in every chip. Each switch is a valve. Current runs along a narrow strip of silicon called the channel, and a small voltage on a gate above the strip opens or shuts the flow. Shorter strips switch faster and more of them fit on a chip, but make the strip short enough and the valve stops sealing: current leaks through even when the gate is off, and the chip burns power doing nothing. The fix is to wrap the gate around all four sides of the strip, so it can squeeze the flow shut from every side, and that takes a long sequence of steps that have to run in exact order. Only three companies, TSMC, Intel and Samsung, can do it, a list so short that an export control can name every one of them.

### In short ^in-short-8

Every gain since the FinFET era has come from process steps and new materials, while shrinking the geometry gave less each node. TSMC's own numbers show the density gain per node falling from 1.2 times at N2P to about 1.1 at A16 [4](https://www.tsmc.com/english/dedicatedFoundry/technology/platform_HPC_tech_advancedTech). Three companies can run a 2 nm-class process, and only TSMC runs it at volume for outside customers. SRAM has stopped shrinking, which is why accelerators keep their memory off the logic die. China can reach 5 nm-class geometry without EUV, and CSIS still judges that China cannot build a working EUV system, which is the gap the export controls defend [16](https://www.csis.org/blogs/strategic-technologies-blog/breakthroughs-or-boasts-assessing-recent-chinese-lithography).

Concentration **Extreme**

Substitutability **Hard** Three firms make gate-all-around transistors, the newest kind, and none sells its process recipe.

Price or market size **No foundry publishes prices for its newest wafers** The public measure is how many more transistors TSMC fits on each new process, and that gain falls from 1.2x at N2P to about 1.1x at A16.

Who leads

-   TWTSMC N2 in volume production since 4Q25, the first nanosheet node
-   USIntel 18A in high-volume manufacturing; 18A-P adds 9% performance at the same power
-   KRSamsung Foundry SF2 family; SF2Z adds backside power
-   CNSMIC N+2 and N+3, printed in several passes on older deep-ultraviolet tools, no EUV
-   JPRapidus State-backed 2 nm entrant targeting mass production in 2027

Where it is made

-   TWTaiwan TSMC N2 at Fab 20 Hsinchu and Fab 22 Kaohsiung
-   USUnited States Intel 18A at Fab 52, Arizona; TSMC Arizona on N4 and N3
-   KRSouth Korea Samsung Hwaseong and Pyeongtaek
-   JPJapan Rapidus Chitose, Hokkaido
-   CNChina SMIC Shanghai and Beijing 300 mm lines

Why substitution is slow

The scarce thing is the process recipe: which steps, in which order, on which tools. Three firms have written one, so a newcomer knows it can be done but has to work out its own. Rapidus in Japan, backed by the state, is now finding out what that costs when starting with no line, on 267.6 billion yen and a 2027 target. Anyone who can buy extreme-ultraviolet scanners should expect five to ten years. China cannot buy those scanners. It has reached 5 nm-class features by printing each layer several times, and that keeps it behind the newest chips.

Where China stands

SMIC ships a process it calls N+3, measured at 113.4 million transistors per square millimeter. It prints each layer in two or four passes because it cannot buy an extreme-ultraviolet scanner. Its narrowest wires sit closer together than Intel 18A's, which shows what a decade of state money buys without an EUV scanner.

Where the US stands

Intel runs the only American-owned line that makes the newest transistors. Its 18A process brought gate-all-around transistors and backside power, where power is fed from under the transistors, to market together. Intel is also the first to use High-NA EUV scanners, the newest kind, in volume production.

A Blackwell GPU is 208 billion switches on two dies, each the largest a lithography machine can print in one shot [1](https://www.nvidia.com/en-us/data-center/technologies/blackwell-architecture/). Every switch has to turn on fully, turn off completely, and keep doing it for years. Making the switches is the front end of line; wiring them together is the back end.

### How it works ^how-it-works-8

The front end builds that valve in a fixed order. First it marks where each transistor will sit and fires atoms of boron or phosphorus into the silicon there, a step called ion implantation, so that those patches conduct the way the design needs.

Next it shapes the channel, in a FinFET by etching the silicon into thin fins standing up from the wafer and laying the gate over the top and both sides of each fin, three sides instead of one. In a gate-all-around transistor the fab instead grows alternating layers of silicon and silicon-germanium, cuts the stack into a narrow bar, then dissolves the silicon-germanium away, leaving thin silicon sheets held at their ends like shelves, and fills the gaps above, below and beside each sheet with gate metal, all four sides. Before the metal goes in, a film of insulator a few atoms thick is laid over every sheet, so that the gate controls the channel without touching it. Last come the contacts, small metal plugs down to the two ends of the channel and to the gate, ready for the wiring layers above.

Each of those is a deposition, an etch or an implant of its own, and they have to run in exact order, since a sheet cannot be wrapped once the metal is on, nor the insulator added once it is buried.

The leak the wrapping prevents is called short-channel leakage, and it has three fixes:

-   **Better insulator.** Thicker, so fewer electrons slip straight through it, yet controlling the channel as tightly as before: Intel switched the gate insulator from silicon dioxide to hafnium at 45 nm in 2007 [2](https://www.intel.com/pressroom/archive/releases/2007/20070128comp.htm).
-   **More gate.** Wrap gate metal around more sides of the channel, as fins and nanosheets do.
-   **Thinner channel.** Thin the silicon until no current can flow where the gate cannot reach it.

### Variants and trade-offs ^variants-and-trade-offs-8

#### Planar and FinFET ^planar-and-finfet

A planar transistor lays the gate on one side of a flat channel, and loses control as the channel shortens. A fin stands the channel on edge so the gate covers three sides, but current then comes in whole fins: a designer who needs more adds one, and nobody gets half a fin.

#### Gate-all-around nanosheets ^gate-all-around-nanosheets

A nanosheet lays the channel back down, stacks two to four thin sheets and threads gate metal around each one. The sheets can be drawn any width, so current comes in fine steps again, which TSMC sells as NanoFlex.

N2 entered volume production in the fourth quarter of 2025, TSMC's first nanosheet node [3](https://www.tsmc.com/english/dedicatedFoundry/technology/logic/l_2nm). TSMC rates the follow-on N2P at 18 percent more speed at the same power, 36 percent less power at the same speed, and 1.2 times the logic density of N3E [4](https://www.tsmc.com/english/dedicatedFoundry/technology/platform_HPC_tech_advancedTech). Intel's RibbonFET shipped on 18A, and 18A-P adds another 9 percent performance at the same power [5](https://www.intc.com/news-events/press-releases/detail/1772/intel-foundry-details-process-milestones-and-future).

Those numbers are vendor claims until someone measures the silicon. Each foundry picks its own baseline, and none publishes a density figure that can be set against a rival's.

TSMC's published density gain, node over nodex versus the baseline node

N2P logic vs N3E 1.2 N2P chip vs N3E 1.1 A16 chip vs N2P 1.1

Source: [TSMC advanced technologies, HPC platform](https://www.tsmc.com/english/dedicatedFoundry/technology/platform_HPC_tech_advancedTech)

#### Backside power delivery ^backside-power-delivery

Power and signal share one stack of copper wiring above the transistors, where wide power rails crowd out the signal wires. Backside power delivery grinds the wafer thin and builds a second network underneath it.

Intel shipped it first as PowerVia: on 18A, an 11 percent cut in routed area and a tenfold cut in dynamic voltage droop, the sag in supply voltage when a block of logic switches on at once [5](https://www.intc.com/news-events/press-releases/detail/1772/intel-foundry-details-process-milestones-and-future). TSMC's Super Power Rail lands that network straight on each transistor's source and drain, with no buried rail between, which is harder to build and gives more: against N2P, A16 gives 8 to 10 percent more speed, 15 to 20 percent less power and up to 1.10 times the chip density [4](https://www.tsmc.com/english/dedicatedFoundry/technology/platform_HPC_tech_advancedTech).

TSMC's logic roadmap beyond N2, from its own announcements

1.  2028-01-01N2U, 3-4% faster or 8-10% lower power than N2P
2.  2028-01-01A14, up to 15% faster and more than 20% denser than N2
3.  2029-01-01A13, a direct shrink of A14 for 6% area savings
4.  2029-01-01A12, the A14 platform with Super Power Rail backside power

Source: [TSMC, 2026 North America Technology Symposium](https://pr.tsmc.com/english/news/3302)

#### CFET and what comes after ^cfet-and-what-comes

A logic gate needs two transistors that switch on opposite signals, and today they sit side by side. The research institute imec expects complementary FETs to stack them and roughly halve the pair's area beyond the 1 nm nodes [7](https://www.imec-int.com/en/articles/imec-puts-complementary-fet-cfet-logic-technology-roadmap).

### The back end of line ^the-back-end-of

Wiring is now as hard to make as the transistor. Copper seeps into the insulator around it, so every wire needs a barrier, a liner and a cap, and once the narrowest wires sit less than 20 nm apart those wrappers take a large share of the wire's cross-section [8](https://www.imec-int.com/en/articles/semi-damascene-metallization-inflection-point-back-end-line-processing). Two metals are moving into those narrow levels.

-   **Ruthenium** needs no barrier, so the whole wire conducts; imec has demonstrated ruthenium lines at a 16 nm pitch [9](https://www.imec-int.com/en/press/imec-demonstrates-16nm-pitch-ru-lines-record-low-resistance-obtained-using-semi-damascene).
-   **Molybdenum** conducts worse in bulk, 5.3 against copper's 1.68 microhm-cm, but in a thin film it beats tungsten by up to 30 percent and needs no barrier either, which is moving it into the contacts on each transistor [10](https://blog.entegris.com/molybdenums-role-in-ultra-fast-computing-the-metal-behind-the-speed).

### Who makes it ^who-makes-it-8

TSMC, Intel and Samsung build gate-all-around nodes with extreme ultraviolet lithography. SMIC builds 7 and 5 nm-class nodes without it. State-backed Rapidus targets 2 nm mass production in 2027 on 267.6 billion yen raised in February 2026 [11](https://www.rapidus.inc/en/news_topics/information/rapidus-secures-267-6-billion-yen-in-funding-from-japan-government-and-private-sector-companies/).

Node names describe nothing physical. SMIC's N+3, sold as 5 nm-class, sets its narrowest wires 32.5 nm apart, tighter than Intel 18A's 36 nm, and reaches 113.4 million transistors per square millimeter against 107.7 for TSMC's N6 [12](https://newsletter.semianalysis.com/p/steel-smic-n3-teardown).

AI accelerators sit a node behind the leading edge, because a die that large comes out working only on a process that has run for years. Blackwell uses a custom TSMC 4NP [1](https://www.nvidia.com/en-us/data-center/technologies/blackwell-architecture/).

SRAM, the fast memory on the logic die, is the scaling failure that hurts AI chips most. TSMC claims 22 percent more SRAM density from N3E to N2, but the gain comes from the circuits around the array, and none of it from the cell that holds one bit [13](https://newsletter.semianalysis.com/p/clash-of-the-foundries), which is much of why accelerators push their memory off the die. See [[#^memory-and-hbm]].

### The chokepoint ^the-chokepoint-8

No single machine makes the front end a chokepoint. The recipe does, and a recipe is which steps run in which order on which tools.

China shows what that recipe costs. The third National Integrated Circuit Fund raised 344 billion yuan, about $47 billion, in May 2024 [14](https://asia.nikkei.com/spotlight/supply-chain/china-launches-47bn-chip-fund-to-counter-u.s.-restrictions), so money is not the constraint; tools are. A Shanghai state firm began building domestic immersion scanners in 2026, in single-digit annual volumes [15](https://www.reuters.com/world/china/china-starts-production-home-grown-immersion-duv-chipmaking-tools-source-2026-07-28/). Those are deep-ultraviolet machines, a generation behind EUV, and SMIC gets fine features out of them by printing each layer in several passes. That volume keeps those lines running and comes nowhere near replacing ASML. EUV is further away: China has announced $43 billion for domestic development, and the Center for Strategic and International Studies still judges that China cannot build a working system [16](https://www.csis.org/blogs/strategic-technologies-blog/breakthroughs-or-boasts-assessing-recent-chinese-lithography).

See [[#^lithography|Lithography]] and [[#^geopolitics|Geopolitics]].

### Key evaluation criteria ^key-evaluation-criteria-8

-   **Electrostatic control.** How far the gate wraps the channel. It sets how much the switch leaks when off, and the lowest supply voltage it can run on.
-   **Density.** Transistors per square millimeter, comparable only inside one foundry's own numbering and for one kind of cell.
-   **Interconnect resistance.** Below a 20 nm wire spacing the wire becomes the slower part and sets the delay [8](https://www.imec-int.com/en/articles/semi-damascene-metallization-inflection-point-back-end-line-processing).
-   **Power delivery.** The voltage lost carrying power across the die. Backside power frees area and cuts the droop tenfold [5](https://www.intc.com/news-events/press-releases/detail/1772/intel-foundry-details-process-milestones-and-future).
-   **SRAM scaling.** The cell that holds one bit has stopped shrinking, which caps how much cache an accelerator can afford.
-   **Cost per transistor.** No foundry publishes wafer prices, so the shrinking density gain per node is the proxy. On that proxy, cost per transistor is rising for the first time.

Card 1 of 4Question

Why do the newest transistors wrap the gate around the channel?

Card 1 of 4Answer

To stop current leaking when the switch is off.

Shorter channels switch faster but leak. A gate on all four sides can shut the flow off completely. [Reread: How it works](#transistors-and-front-end--how-it-works)

Card 2 of 4Question

Which companies can make these gate-all-around transistors?

Card 2 of 4Answer

TSMC, Intel and Samsung.

Only TSMC makes them in volume for outside customers. [Reread: Who makes it](#transistors-and-front-end--who-makes-it)

Card 3 of 4Question

Why is the front end hard for a new firm to enter?

Card 3 of 4Answer

No firm sells its process recipe, the exact sequence of steps that builds the transistors.

A newcomer has to develop its own. [Reread: The chokepoint](#transistors-and-front-end--the-chokepoint)

Card 4 of 4Question

How does China's SMIC make advanced chips without an EUV machine?

Card 4 of 4Answer

It prints each layer in two or four passes on older deep-ultraviolet tools.

This reaches 5 nm-class features. CSIS judges that China still cannot build a working EUV system. [Reread: The chokepoint](#transistors-and-front-end--the-chokepoint)

#### Four things to remember ^four-things-to-remember-7

-   The newest transistors wrap the gate around all four sides of the channel to stop current leaking.
-   Only TSMC, Intel and Samsung can make them, and only TSMC does so in volume for outside customers.
-   No firm sells its process recipe, so a newcomer has to develop its own.
-   SMIC reaches 5 nm-class features without EUV by printing each layer in several passes.

Sources (16)

1.  A [NVIDIA Blackwell Architecture](https://www.nvidia.com/en-us/data-center/technologies/blackwell-architecture/) Nvidia · 18 December 2025
2.  A [Intel's Transistor Technology Breakthrough Represents Biggest Change to Computer Chips in 40 Years](https://www.intel.com/pressroom/archive/releases/2007/20070128comp.htm) Intel · 27 January 2007
3.  A [2nm Technology](https://www.tsmc.com/english/dedicatedFoundry/technology/logic/l_2nm) TSMC
4.  A [HPC Platform – Advanced Technologies](https://www.tsmc.com/english/dedicatedFoundry/technology/platform_HPC_tech_advancedTech) TSMC
5.  A [Intel Foundry Details Process Milestones and Future Innovation at VLSI Symposium](https://www.intc.com/news-events/press-releases/detail/1772/intel-foundry-details-process-milestones-and-future) Intel · 16 June 2026
6.  A [TSMC Debuts A13 Technology at 2026 North America Technology Symposium](https://pr.tsmc.com/english/news/3302) TSMC · 23 April 2026
7.  A [CFET (complementary FET)](https://www.imec-int.com/en/articles/imec-puts-complementary-fet-cfet-logic-technology-roadmap) imec
8.  A [Semi-damascene metallization](https://www.imec-int.com/en/articles/semi-damascene-metallization-inflection-point-back-end-line-processing) imec
9.  A [16nm Ru lines using semi-damascene integration approach](https://www.imec-int.com/en/press/imec-demonstrates-16nm-pitch-ru-lines-record-low-resistance-obtained-using-semi-damascene) imec · 3 June 2025
10.  A [Molybdenum’s Role in Ultra-Fast Computing: The Metal Behind the Speed](https://blog.entegris.com/molybdenums-role-in-ultra-fast-computing-the-metal-behind-the-speed) Entegris · 18 May 2026
11.  A [Rapidus Secures 267.6 Billion Yen in Funding from Japan Government and Private Sector Companies This strategic funding plan will enable Rapidus to steadily progress from its current R&D phase to mass production of 2nm logic semiconductors by 2027 - Information - Rapidus Corporation](https://www.rapidus.inc/en/news_topics/information/rapidus-secures-267-6-billion-yen-in-funding-from-japan-government-and-private-sector-companies/) Rapidus
12.  B [Is SMIC N+3’s Metal Pitch Smaller than Intel 18A’s?](https://newsletter.semianalysis.com/p/steel-smic-n3-teardown) SemiAnalysis · 14 June 2026
13.  B [Clash of the Foundries: Gate All Around + Backside Power at 2nm](https://newsletter.semianalysis.com/p/clash-of-the-foundries) SemiAnalysis · 1 October 2024
14.  B [China launches $47bn chip fund to counter U.S. restrictions](https://asia.nikkei.com/spotlight/supply-chain/china-launches-47bn-chip-fund-to-counter-u.s.-restrictions) Nikkei Asia · 27 May 2024
15.  B [China starts production of home-grown immersion DUV chipmaking tools, source says](https://www.reuters.com/world/china/china-starts-production-home-grown-immersion-duv-chipmaking-tools-source-2026-07-28/) Reuters · 28 July 2026
16.  A [Breakthroughs or Boasts? Assessing Recent Chinese Lithography Advancements | Strategic Technologies Blog](https://www.csis.org/blogs/strategic-technologies-blog/breakthroughs-or-boasts-assessing-recent-chinese-lithography) Center for Strategic and International Studies

## Foundries and Fabs ^foundries-and-fabs

TSMC runs six plants that each print more than 100,000 wafers a month. All six are in Taiwan, and they hold 13 of the 17 million wafers a year the company can make.

1,391 words / 6 minSpecimen: wafer carrier (FOUP)

In plain terms

A foundry is a fab that makes chips for other companies. Those companies send in their designs, and the foundry runs them all through the same building on the same tools. The building costs tens of billions of dollars, and the air inside is cleaner than an operating room. Even so, a wafer crosses hundreds of machines over several months inside sealed boxes, never touching that air. No chip company sells enough of one product to fill a factory like that on its own, so the world shares a handful of them. TSMC runs the biggest, and all six of its largest plants sit in Taiwan, which is why one island's politics reaches the whole chip supply.

### In short ^in-short-9

The foundry model won because leading-edge fabs are too expensive for one design house, and it concentrated because only the leader earns enough to build the next node. TSMC's six gigafabs hold 13 of the 17 million wafers a year it can make, and all six are in Taiwan [1](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/gigafab). Intel and Samsung are credible technically and unproven commercially, and Intel is now part-owned by its government [10](https://www.intc.com/news-events/press-releases/detail/1748/intel-and-trump-administration-reach-historic-agreement-to). Diversification costs $165 billion and a decade in the American case alone [9](https://pr.tsmc.com/english/news/3210), which makes the concentration in Taiwan a fact about the 2020s and 2030s.

Concentration **Extreme**

Substitutability **Hard** Intel and Samsung also run lines for the newest chips, but TSMC has not built one of its largest fabs outside Taiwan, and the slow part is training the workforce.

Price or market size **BCG puts the ten-year cost of owning a fab completed in 2026 at $35-43 billion** TSMC intends to spend $165 billion in the United States alone

Who leads

-   TWTSMC 77% of wafer revenue from 7 nm and below, 2Q26; six gigafabs, all in Taiwan
-   USIntel Foundry $5.8bn revenue and a $2.089bn operating loss, 2Q26
-   KRSamsung Foundry Hwaseong and Pyeongtaek; at least $17bn of construction at Taylor, Texas
-   CNSMIC $9.327bn revenue in 2025 at 93.5% utilization
-   JPRapidus State-backed 2 nm entrant, Chitose

Where it is made

-   TWTaiwan TSMC's six gigafabs and UMC; N2 and N3 for every leading AI accelerator
-   KRSouth Korea Samsung Foundry, Hwaseong and Pyeongtaek
-   CNChina SMIC and Hua Hong; the largest installed capacity of any region, almost all of it on older nodes
-   USUnited States Intel Foundry, GlobalFoundries, TSMC Arizona, Samsung Taylor
-   JPJapan TSMC Kumamoto, Rapidus Chitose

Why substitution is slow

Money can buy the building. BCG puts the ten-year cost of a fab finished in 2026 at $35 to $43 billion. Intel and Samsung already run lines for the newest chips, so a newcomer is copying something that has been done. Money cannot quickly buy a workforce that has run one process for years. Even TSMC has yet to build one of its largest fabs anywhere but Taiwan. A working line takes five to ten years, and reaching high volume takes longer.

Where China stands

SMIC and Hua Hong are China's largest foundries. SMIC had revenue of $9.327 billion in 2025 with its lines 93.5 percent full. It cannot buy an EUV scanner, so it cannot make the newest chips. China is forecast to have more fab capacity than any other region, and almost none of it can make the newest chips.

Where the US stands

Intel Foundry is the only American-owned foundry that makes the newest chips. It lost $2.089 billion on $5.8 billion of revenue in the second quarter of 2026. The federal government owns 9.9 percent of Intel and takes no part in running it.

TSMC calls a plant a GIGAFAB once it runs more than 100,000 wafers a month, each a 300 mm disc, twelve inches across. It operates six of them, and every one is in Taiwan [1](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/gigafab).

### How it works ^how-it-works-9

Inside, the work is one loop repeated for every layer. Wafers travel in a lot, a batch of 25 in a sealed pod called a FOUP that only a machine opens. An overhead track carries the pod from tool to tool. At each tool a robot lifts one wafer out, the tool does its one job, depositing a film, printing a pattern, etching it, cleaning it or measuring it, and the robot puts the wafer back. The pod moves on to the next tool, often across the building, and the loop starts again with the next layer. A chip takes hundreds of those visits, so a wafer spends months inside.

The pod keeps the wafer clean for all of that time, because the wafer never meets the room's air, and even that air is filtered until it carries almost no dust. Every design in the building runs on the same tools because each tool is set by recipe, the list of gases, temperatures and times for one step, and a foundry offers each customer the same list of recipes on shared machines. The tools run day and night, since an idle tool earns nothing. The finished wafer is tested (see [[#^test-and-assembly|Test and assembly]]), then cut and packaged.

TSMC, founded in 1987, invented the pure-play model: it builds chips for other companies and promises never to compete with them. BCG puts the ten-year cost of owning a fab completed in 2026 at $35 to $43 billion, a third to two thirds above one finished three years earlier [2](https://www.bcg.com/publications/2023/navigating-the-semiconductor-manufacturing-costs).

Every plant TSMC and its subsidiaries run came to more than 17 million wafers a year in 2025, counted as if each were the standard 12-inch size [3](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/fab_capacity). The six largest plants, all in Taiwan and called gigafabs, hold 13 million of that [1](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/gigafab); Arizona, Kumamoto, Nanjing and Washington hold the rest.

### Variants and trade-offs ^variants-and-trade-offs-9

#### Pure-play foundries ^pure-play-foundries

TSMC and UMC build only for others. Chips at 7 nm and below, meaning the newest processes, were 77 percent of TSMC's wafer revenue in the second quarter of 2026, split 33 percent at 5 nm, 30 at 3 nm, 11 at 7 nm and 3 at 2 nm, on revenue of $40.20 billion at a 67.7 percent gross margin [4](https://www.sec.gov/Archives/edgar/data/0001046179/000104617926000451/a2q26e_withguidancexfinal.htm). No other foundry earns that margin, so none can fund the next node out of cash flow.

TSMC wafer revenue by node, 2Q26% of wafer revenue

2 nm **3** 3 nm **30** 5 nm **33** 7 nm **11** 10 nm and above **23**

Source: [TSMC 2Q26 results, filed with the SEC](https://www.sec.gov/Archives/edgar/data/0001046179/000104617926000451/a2q26e_withguidancexfinal.htm)

#### Integrated device makers turned foundry ^integrated-device-makers-turned

Intel and Samsung design and sell their own chips and rent out capacity too. Renting out capacity is harder for them, because customers dislike handing designs to a competitor and the company's own products take the best capacity. Intel Foundry booked $5.8 billion of revenue in the second quarter of 2026, up 31 percent, against a $2.089 billion operating loss [5](https://www.intc.com/news-events/press-releases/detail/1776/intel-reports-second-quarter-2026-financial-results).

#### National champions ^national-champions

SMIC, Hua Hong and Rapidus exist because a government decided they should. SMIC's revenue rose 16.2 percent to $9.327 billion in 2025 at 93.5 percent utilization, on monthly capacity above a million wafers counted in the smaller 8-inch size, and a 21 percent gross margin [6](https://www.smics.com/en/site/news_read/7951). Rapidus raised 267.6 billion yen in February 2026 to carry it to 2 nm mass production in 2027 [7](https://www.rapidus.inc/en/news_topics/information/rapidus-secures-267-6-billion-yen-in-funding-from-japan-government-and-private-sector-companies/).

#### Mature-node capacity ^mature-node-capacity

Most wafers come off older lines. The industry association SEMI expects foundries alone to reach 12.7 million wafers a month by 2026, with the fastest growth in China [8](https://www.semi.org/en/news-media-press-releases/semi-press-releases/global-semiconductor-fab-capacity-projected-to-expand-6%25-in-2024-and-7%25-in-2025-semi-reports). Those lines make power devices, analog chips and microcontrollers, and compete on price.

### Capacity and cost ^capacity-and-cost

TSMC intends to spend $165 billion in the United States, adding $100 billion in March 2025 to the $65 billion already committed in Phoenix, for three more fabs, two packaging plants and an R&D center [9](https://pr.tsmc.com/english/news/3210). That is the largest foreign direct investment in US history, and it still does not put a gigafab outside Taiwan.

TSMC does not auction capacity; it books it years ahead against prepayments, so the queue for a node is set before the node exists. Through 2024 and 2025 the binding constraint was packaging. See [[#^advanced-packaging|Advanced packaging]].

### Who makes it ^who-makes-it-9

Intel is now partly state-owned. In August 2025 Washington bought 433.3 million newly issued Intel shares at $20.47, or $8.9 billion, for a 9.9 percent stake, paid out of $5.7 billion of unpaid CHIPS Act grants and $3.2 billion from the Secure Enclave program. The stake carries no control, and it came with a five-year warrant for a further 5 percent that Washington can exercise only if Intel drops below 51 percent ownership of the foundry business [10](https://www.intc.com/news-events/press-releases/detail/1748/intel-and-trump-administration-reach-historic-agreement-to). That makes the warrant an option on Intel keeping its fabs.

Intel's technical position improved in 2026. It reached high-volume manufacturing on part of Panther Lake using ASML's High-NA extreme ultraviolet scanners, the first company to do so, and put 18A-P into risk production, the trial runs a process goes through before it is signed off [5](https://www.intc.com/news-events/press-releases/detail/1776/intel-reports-second-quarter-2026-financial-results). The commercial position has not caught up, since 14A depends on winning external customers first.

Samsung's main plant outside Korea is Taylor, Texas: a committed minimum of $17 billion, $6 billion of buildings and $11 billion of equipment, for leading-edge and mature logic [11](https://semiconductor.samsung.com/sas/company/taylor/).

### The chokepoint ^the-chokepoint-9

SEMI forecast China at 10.1 million wafers a month in 2025, the most of any region, against Taiwan's 5.8 million out of a world total of 33.7 million [8](https://www.semi.org/en/news-media-press-releases/semi-press-releases/global-semiconductor-fab-capacity-projected-to-expand-6%25-in-2024-and-7%25-in-2025-semi-reports). Almost none of China's is advanced. The United States had almost no capacity below 10 nm in 2022 and is projected to hold 28 percent of it by 2032, on $2.3 trillion of new fab investment [12](https://www.bcg.com/publications/2024/emerging-resilience-in-semiconductor-supply-chain).

Installed wafer fab capacity by region, 2025 forecast, all nodesmillion 8-inch-equivalent wafers per month

China 10.1 Taiwan 5.8 South Korea 5.4 Japan 4.7 Americas 3.2 Europe and Mideast 2.7 SE Asia 1.8

Source: [SEMI World Fab Forecast](https://www.semi.org/en/news-media-press-releases/semi-press-releases/global-semiconductor-fab-capacity-projected-to-expand-6%25-in-2024-and-7%25-in-2025-semi-reports)

Three risks meet on one island:

-   **Seismic.** Taiwan sits on an active plate boundary, and a tool knocked out of calibration scraps the work in progress across a whole fab.
-   **Power.** A gigafab is a large industrial load on a small island grid. Spare generating capacity sets how fast Taiwan can add fabs.
-   **Political.** A blockade or conflict would remove most sub-5 nm capacity from the world market at once, with no substitute available inside a decade. See [[#^geopolitics|Geopolitics]].

Diversification is slow because the hard part of a fab is a workforce that has run one process for years, and TSMC has yet to build a gigafab anywhere but Taiwan [1](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/gigafab).

### Key evaluation criteria ^key-evaluation-criteria-9

-   **Leading-edge share.** TSMC's 77 percent of wafer revenue from 7 nm and below is why it can self-fund the next node [4](https://www.sec.gov/Archives/edgar/data/0001046179/000104617926000451/a2q26e_withguidancexfinal.htm).
-   **Yield at ramp.** How many good chips a new process gives in its first year, which separates a profitable node from a subsidized one. Intel Foundry's loss comes from yield.
-   **Ten-year cost of ownership.** $35 to $43 billion for a fab finished in 2026, and rising [2](https://www.bcg.com/publications/2023/navigating-the-semiconductor-manufacturing-costs).
-   **Utilization.** How full the lines run. SMIC's 93.5 percent shows what a captive home market does for volume, and not for margins [6](https://www.smics.com/en/site/news_read/7951).
-   **Customer concentration.** A foundry owned by a chipmaker competes with its own customers, which caps who will trust it with a flagship design.
-   **Geographic exposure.** How much of a buyer's supply sits on one island, one grid, one fault system.

Card 1 of 4Question

What is a foundry?

Card 1 of 4Answer

A chip factory that makes chips designed by other companies.

A fab costs tens of billions of dollars, and no chip company sells enough of one product to fill one alone. [[#^how-it-works-9|Reread: How it works]]

Card 2 of 4Question

Where are TSMC's largest plants?

Card 2 of 4Answer

All six are in Taiwan.

They hold 13 of the 17 million wafers TSMC can make in a year. [[#^who-makes-it-9|Reread: Who makes it]]

Card 3 of 4Question

What is the slowest part of building leading-edge chipmaking outside Taiwan?

Card 3 of 4Answer

Training a workforce that has run the process for years.

Money can buy the building. TSMC has committed $165 billion to the United States and has not yet built one of its largest plants there. [[#^the-chokepoint-9|Reread: The chokepoint]]

Card 4 of 4Question

How much of China's fab capacity can make the newest chips?

Card 4 of 4Answer

Almost none.

China has more capacity than any other region, but SMIC cannot buy an EUV machine. [[#^the-chokepoint-9|Reread: The chokepoint]]

#### Four things to remember ^four-things-to-remember-8

-   A foundry makes chips for other companies, because no chip company can fill a fab alone.
-   All six of TSMC's largest plants are in Taiwan.
-   Money can buy a fab building, and training the workforce is the slow part.
-   China has more fab capacity than any other region, and almost none of it can make the newest chips.

Sources (12)

1.  A [GIGAFAB® Facilities](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/gigafab) TSMC
2.  A [Navigating the Costly Economics of Chip Making](https://www.bcg.com/publications/2023/navigating-the-semiconductor-manufacturing-costs) Boston Consulting Group · 28 September 2023
3.  A [Fab Capacity](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/fab_capacity) TSMC
4.  A [TAIWAN SEMICONDUCTOR MANUFACTURING CO LTD, Form 6-K report of foreign private issuer for the period ended 2026-06-30 (6-K)](https://www.sec.gov/Archives/edgar/data/0001046179/000104617926000451/a2q26e_withguidancexfinal.htm) U.S. Securities and Exchange Commission (filing by TAIWAN SEMICONDUCTOR MANUFACTURING CO LTD) · 16 July 2026
5.  A [Intel Reports Second-Quarter 2026 Financial Results](https://www.intc.com/news-events/press-releases/detail/1776/intel-reports-second-quarter-2026-financial-results) Intel · 23 July 2026
6.  A [SMIC Announces 2025 Annual Results](https://www.smics.com/en/site/news_read/7951) SMIC
7.  A [Rapidus Secures 267.6 Billion Yen in Funding from Japan Government and Private Sector Companies This strategic funding plan will enable Rapidus to steadily progress from its current R&D phase to mass production of 2nm logic semiconductors by 2027 - Information - Rapidus Corporation](https://www.rapidus.inc/en/news_topics/information/rapidus-secures-267-6-billion-yen-in-funding-from-japan-government-and-private-sector-companies/) Rapidus
8.  A [Global Semiconductor Fab Capacity Projected to Expand 6% in 2024 and 7% in 2025, SEMI Reports](https://www.semi.org/en/news-media-press-releases/semi-press-releases/global-semiconductor-fab-capacity-projected-to-expand-6%25-in-2024-and-7%25-in-2025-semi-reports) SEMI · 18 June 2024
9.  A [TSMC Intends to Expand Its Investment in the United States to US$165 Billion to Power the Future of AI](https://pr.tsmc.com/english/news/3210) TSMC · 4 March 2025
10.  A [Intel and Trump Administration Reach Historic Agreement to Accelerate American Technology and Manufacturing Leadership](https://www.intc.com/news-events/press-releases/detail/1748/intel-and-trump-administration-reach-historic-agreement-to) Intel · 22 August 2025
11.  A [Taylor | US Fab | Samsung Semiconductor Global](https://semiconductor.samsung.com/sas/company/taylor/) Samsung Electronics · 11 September 2025
12.  A [Emerging Resilience in the Semiconductor Supply Chain](https://www.bcg.com/publications/2024/emerging-resilience-in-semiconductor-supply-chain) Boston Consulting Group · 8 May 2024

## Memory and HBM ^memory-and-hbm

Three firms make every HBM stack in the world. The stack is the largest block of silicon in an AI package, and the cooling plate above it now limits how tall it can be.

1,396 words / 6 minSpecimen: HBM stack

In plain terms

High bandwidth memory, or HBM, is where an AI chip keeps the numbers it is working on, and it is built to hand them over fast. A memory maker stacks up to sixteen memory chips into a cube, drills holes straight down through the stack, and fills the holes with copper so that every layer is wired to the ones below. The cube then sits beside the processor, the chip that does the calculating. Stacking is the hard part, because each chip is ground so thin that the copper in its holes shows through its back, the finished cube has to fit under the plate that cools it, and one bad chip ruins the whole cube. Only SK hynix, Samsung and Micron have made it work, and a single line in an American export control reaches all three.

### In short ^in-short-10

HBM is the most expensive component in an AI accelerator, and three firms supply all of it: the two Korean ones sold 82.5 percent in 2025 [11](https://www.sec.gov/Archives/edgar/data/2120882/000119312526299963/d32785d424b4.htm). The limit now is heat and height inside a 775-micrometer cube [9](https://news.skhynix.com/en/tech-note-series-ep2/), and the fix, hybrid bonding, is two generations away. The export control on HBM works because one bandwidth-density threshold catches every part worth buying [15](https://www.federalregister.gov/documents/2024/12/05/2024-28270/foreign-produced-direct-product-rule-additions-and-refinements-to-controls-for-advanced-computing).

Concentration **Extreme**

Substitutability **Hard** Three firms ship HBM, and no fourth firm has both the newest DRAM and a line that stacks it.

Price or market size **An HBM stack moves data over a path 16 times wider than a DDR5 memory module's** That width costs chip area and lowers the share of stacks that come out working.

Who leads

-   KRSK hynix 63.2% of HBM revenue, 2025; first to complete HBM4, at over 10 Gbps per pin
-   KRSamsung 19.3% of HBM revenue, 2025; Hwaseong and Pyeongtaek
-   USMicron 17.4% of HBM revenue, 2025; HBM4 above 11 Gbps per pin

Where it is made

-   KRSouth Korea SK hynix Cheongju and Icheon; Samsung Pyeongtaek and Hwaseong
-   USUnited States Micron headquarters and R&D; SK hynix packaging plant under construction in Indiana
-   TWTaiwan Micron DRAM and HBM packaging in Taichung; TSMC builds HBM4 logic base dies
-   JPJapan Micron Hiroshima, 1-gamma DRAM
-   SGSingapore Micron HBM advanced packaging

Why substitution is slow

Among the three HBM makers, market share shifts as soon as a customer approves a new part: Micron went from 5.8 percent of HBM revenue in 2024 to 23.1 percent by the first quarter of 2026 without adding capacity. A fourth maker would be harder. It would need the newest DRAM, a line that drills through and thins wafers, and a way to stack the thinned chips without warping them, all inside one company. Its stack would then have to pass Nvidia's speed test. That takes five to ten years, and no Chinese firm ships HBM3E or HBM4 in volume yet.

Where China stands

No Chinese firm ships HBM3E or HBM4 in volume. CXMT is the only Chinese firm that could plausibly get there, and the US export controls are written to prevent that.

Where the US stands

Micron is the only American HBM maker. BIS, the US export control office, requires a license for HBM faster than 2 GB/s per square millimeter of package or stack area, under control number ECCN 3A090.c, and every stack now in production is faster than that.

An AI accelerator is a machine for moving numbers past arithmetic units, and arithmetic got cheap faster than the moving did. High bandwidth memory now decides how fast a GPU runs.

### How it works ^how-it-works-10

Each layer in the cube is a DRAM chip, ground thin and bonded to the one below with microbumps, dots of solder, and the whole stack sits on a base die that manages it. The copper-filled holes are TSVs, through-silicon vias, and they let a signal reach any layer without a wire around the outside.

An HBM3E cube talks to the processor over 1,024 wires at once, a 1,024-bit interface, sixteen times wider than a standard DDR5 memory module, the memory stick in a PC [1](https://www.micron.com/products/memory/hbm). HBM4 doubles that to 2,048 wires [2](https://www.jedec.org/news/pressreleases/jedec%C2%AE-and-industry-leaders-collaborate-release-jesd270-4-hbm4-standard-advancing). Ordinary memory cannot be made that wide, because the pins would not fit on a circuit board. The stack can, since its wires run down through the TSVs and across a few millimeters of silicon to the processor beside it, with no board in the way.

![](https://chipsupplychain.org/media/hbm-stack-light-end.jpg)

Inside a memory stack

Answering a prompt is what the width is for. Training reuses each stored number across a huge multiplication, so a chip can fetch little and compute a lot. To generate one word of an answer, the chip reads the whole model from memory, and the whole record of the conversation so far, does a little arithmetic, and waits for the next read. That record grows with the length of the conversation and the number of users served at once. So memory size and speed usually set how many people one chip can serve.

### Variants and trade-offs ^variants-and-trade-offs-10

| Generation | Interface | Bandwidth per stack | Capacity per stack |
| --- | --- | --- | --- |
| HBM3E | 1,024-bit, 16 channels (32 pseudo-channels) | over 1.2 TB/s | 24 GB (8 chips), 36 GB (12 chips) |
| HBM4 | 2,048-bit, 32 channels | over 2.0 TB/s, up to 3.3 TB/s | up to 64 GB (16 chips, 32 Gb dies) |

#### HBM3E ^hbm3e

Micron ships the high-volume parts, 24 GB with eight chips stacked and 36 GB with twelve [3](https://www.micron.com/products/memory/hbm/hbm3e), and HBM3E should be about two thirds of all HBM shipments in 2026 [4](https://news.skhynix.com/en/2026-market-outlook-focus-on-the-hbm-led-memory-supercycle/).

#### HBM4 ^hbm4

The standards body JEDEC published JESD270-4 in April 2025, setting the 2,048-bit interface and 2 TB/s per stack at 8 Gb/s per pin [2](https://www.jedec.org/news/pressreleases/jedec%C2%AE-and-industry-leaders-collaborate-release-jesd270-4-hbm4-standard-advancing). Nobody ships at that baseline: SK hynix completed HBM4 at over 10 Gb/s per pin in September 2025 [5](https://news.skhynix.com/en/sk-hynix-completes-worlds-first-hbm4-development-and-readies-mass-production/), and Micron's parts run above 11 Gb/s for more than 2.8 TB/s per stack [6](https://www.micron.com/products/memory/hbm/hbm4).

The chip at the bottom of an HBM4 stack is now a logic chip, so it has to be made in a foundry, and SK hynix partnered with TSMC to build it [7](https://news.skhynix.com/sk-hynix-partners-with-tsmc-to-strengthen-hbm-technological-leadership/). That gives TSMC a role inside a product it does not make.

Peak bandwidth per HBM stackGB/s

HBM3E, 1,024-bit 1,200 HBM4, 2,048-bit 2,000 HBM4, advanced configurati 3,300

Source: [Siemens EDA, HBM3E and HBM4 IC design guide, April 2026](https://blogs.sw.siemens.com/semiconductor-packaging/2026/04/24/hbm3e-hbm4-ic-design-guide/)

### How a stack is built ^how-a-stack-is

-   **Drill and thin.** Etch vertical holes, the through-silicon vias, into a memory wafer, fill them with copper, then grind the wafer from behind until the copper comes through.
-   **Stack and join.** SK hynix uses Advanced MR-MUF, which melts the solder bumps between stacked chips and molds a filler around them in one pass, which limits heat and warping [5](https://news.skhynix.com/en/sk-hynix-completes-worlds-first-hbm4-development-and-readies-mass-production/).
-   **Stay under the height limit.** HBM4 raised the height limit on a finished cube from 720 micrometers to 775, still under a millimeter, because a stack taller than the processor beside it would hit the cooling plate [9](https://news.skhynix.com/en/tech-note-series-ep2/).

Hybrid bonding is the next step and it is not ready. Pressing copper pad straight onto copper pad, with no solder and no filler, would cut the spacing between connections from about 20 micrometers to under 1, but SK hynix expects full-scale adoption only at HBM4E or HBM5, where stacks pass twenty layers [9](https://news.skhynix.com/en/tech-note-series-ep2/).

### Who makes it ^who-makes-it-10

Ordinary computer memory, DRAM, is a three-firm oligopoly, and HBM is the same three firms reordered: SK hynix, Samsung and Micron. Nobody else has both leading-edge DRAM and a stacking line inside one company.

SK hynix built its lead by being first to pass Nvidia's qualification tests, and expects roughly 70 percent of Rubin HBM4 in 2026 [4](https://news.skhynix.com/en/2026-market-outlook-focus-on-the-hbm-led-memory-supercycle/). It started building a $4 billion packaging plant in West Lafayette, Indiana in August 2026 [10](https://www.purdue.edu/newsroom/2026/Q3/sk-hynix-breaks-ground-on-4-billion-advanced-packaging-production-facility-in-purdue-research-park/), and Micron packages in Taichung and Singapore.

The split is on the record because SK hynix registered shares in the United States: of 2025 HBM revenue, SK hynix took 63.2 percent, Samsung 19.3 and Micron 17.4, which puts the two Korean suppliers at 82.5 percent of the world's HBM [11](https://www.sec.gov/Archives/edgar/data/2120882/000119312526299963/d32785d424b4.htm). The filing credits the research firm IDC. These shares move fast: in 2024 the same three stood at 56.4, 37.8 and 5.8, so Samsung halved and Micron tripled inside a year on qualification wins alone. By the first quarter of 2026 Micron was at 23.1 percent and Korea down to 76.9 [11](https://www.sec.gov/Archives/edgar/data/2120882/000119312526299963/d32785d424b4.htm).

Global HBM revenue by supplier, 2025%

SK hynix (KR) **63.2%** Samsung (KR) **19.3%** Micron (US) **17.4%**

Source: [SK hynix Form 424B4 prospectus, 10 July 2026, on IDC data](https://www.sec.gov/Archives/edgar/data/2120882/000119312526299963/d32785d424b4.htm)

HBM market revenue, Bank of America estimate$B

2025 34.6 2026 54.6

Source: [Bank of America estimate cited in SK hynix's 2026 market outlook](https://news.skhynix.com/en/2026-market-outlook-focus-on-the-hbm-led-memory-supercycle/)

Bank of America puts the 2026 HBM market at $54.6 billion, up 58 percent on the year [4](https://news.skhynix.com/en/2026-market-outlook-focus-on-the-hbm-led-memory-supercycle/). HBM is sold under contracts signed long before the wafers exist. Every wafer turned over to HBM is a wafer not making ordinary DRAM, which is how AI demand raises the price of a laptop.

### The chokepoint ^the-chokepoint-10

Every leading accelerator depends on Korean or American HBM. Nvidia's GB300 NVL72 carries 20 TB of HBM3E at up to 576 TB/s [12](https://www.nvidia.com/en-us/data-center/gb300-nvl72/), Rubin's VR200 up to 288 GB of HBM4 per GPU at up to 22 TB/s [13](https://developer.nvidia.com/blog/inside-nvidia-rubin-gpu-architecture-powering-the-era-of-agentic-ai/), and AMD's MI355X 288 GB of HBM3E at 8 TB/s [14](https://inferencex.semianalysis.com/chips/mi355x).

The Bureau of Industry and Security rule of 5 December 2024, at 89 FR 96790, added an export classification, ECCN 3A090.c, for "High bandwidth memory (HBM) having a 'memory bandwidth density' greater than 2 gigabytes per second per square millimeter". Its technical note defines that density as the memory bandwidth in gigabytes per second divided by the area of the package or stack in square millimeters. The rule also reaches stacks made outside the United States, through a foreign direct product rule that catches goods made abroad with American technology [15](https://www.federalregister.gov/documents/2024/12/05/2024-28270/foreign-produced-direct-product-rule-additions-and-refinements-to-controls-for-advanced-computing). Against the JEDEC numbers, that threshold captures every stack now in production, so there is no compliant high-end HBM to sell. Under 15 CFR 742.6(b)(10)(ii) BIS reads applications for 3A090.c into China or Macau with a presumption of approval when the buyer is not headquartered there, and a presumption of denial when it is. That split is what lets the Chinese sites of Korean and American firms, and the allied packaging houses on the mainland, go on receiving HBM [15](https://www.federalregister.gov/documents/2024/12/05/2024-28270/foreign-produced-direct-product-rule-additions-and-refinements-to-controls-for-advanced-computing) [16](https://www.ecfr.gov/current/title-15/subtitle-B/chapter-VII/subchapter-C/part-742/section-742.6).

China's HBM maker is CXMT, and it is behind the three. That gap is closing from a base that did not exist five years ago. The barrier for a new entrant is the stacking line and Nvidia's approval.

### Key evaluation criteria ^key-evaluation-criteria-10

-   **Bandwidth per stack** sets how fast a chip can serve answers: over 1.2 TB/s on HBM3E, over 2 TB/s on HBM4 [8](https://blogs.sw.siemens.com/semiconductor-packaging/2026/04/24/hbm3e-hbm4-ic-design-guide/).
-   **Capacity per stack** decides how large a model fits on one accelerator, up to 64 GB with sixteen chips stacked [2](https://www.jedec.org/news/pressreleases/jedec%C2%AE-and-industry-leaders-collaborate-release-jesd270-4-hbm4-standard-advancing).
-   **Stack height**, 775 micrometers for HBM4, caps the number of layers before the cooling plate [9](https://news.skhynix.com/en/tech-note-series-ep2/).
-   **Stack yield** sets the price more than wafer cost does, because one bad die scraps the cube.
-   **Thermal path** gets worse with every layer: the chip at the bottom runs hottest, and each one added above it makes the heat harder to get out.
-   **Qualification** means passing Nvidia's data-rate test, above 10 Gb/s, against JEDEC's 8 [5](https://news.skhynix.com/en/sk-hynix-completes-worlds-first-hbm4-development-and-readies-mass-production/).

Card 1 of 4Question

What is HBM?

Card 1 of 4Answer

Memory chips stacked into a cube beside the processor and wired to pass data fast.

Copper-filled holes run straight down through the stack, which holds up to sixteen chips. [[#^how-it-works-10|Reread: How it works]]

Card 2 of 4Question

Why does an AI chip need such fast memory?

Card 2 of 4Answer

For each word it writes, it reads the whole model from memory.

Memory speed and size usually set how many users one chip can serve. [[#^how-it-works-10|Reread: How it works]]

Card 3 of 4Question

Who makes HBM?

Card 3 of 4Answer

Three firms: SK hynix, Samsung and Micron.

The two Korean firms sold 82.5 percent of it in 2025. A fourth maker would need both the newest DRAM and a line that stacks it. [[#^who-makes-it-10|Reread: Who makes it]]

Card 4 of 4Question

Can China get advanced HBM?

Card 4 of 4Answer

No. US export controls cover every stack in production, and no Chinese firm makes it in volume.

CXMT is the one Chinese firm that could plausibly get there. [[#^the-chokepoint-10|Reread: The chokepoint]]

#### Four things to remember ^four-things-to-remember-9

-   HBM is memory stacked into a cube beside the processor and wired to pass data fast.
-   An AI chip reads its whole model from memory for each word, so memory speed limits it.
-   Only SK hynix, Samsung and Micron make HBM.
-   US export controls cover every HBM stack in production, and no Chinese firm makes it in volume.

Sources (16)

1.  A [High-bandwidth memory (HBM)](https://www.micron.com/products/memory/hbm) Micron Technology
2.  A [JEDEC® and Industry Leaders Collaborate to Release JESD270-4 HBM4 Standard: Advancing Bandwidth, Efficiency, and Capacity for AI and HPC](https://www.jedec.org/news/pressreleases/jedec%C2%AE-and-industry-leaders-collaborate-release-jesd270-4-hbm4-standard-advancing) JEDEC Solid State Technology Association · 16 April 2025
3.  A [Micron, HBM3E product page](https://www.micron.com/products/memory/hbm/hbm3e) Micron Technology
4.  A [2026 Market Outlook – “Focus on the HBM-Led Memory Supercycle”](https://news.skhynix.com/en/2026-market-outlook-focus-on-the-hbm-led-memory-supercycle/) SK hynix
5.  A [SK hynix Completes World’s First HBM4 Development and Readies Mass Production](https://news.skhynix.com/en/sk-hynix-completes-worlds-first-hbm4-development-and-readies-mass-production/) SK hynix
6.  A [Micron, HBM4 product page](https://www.micron.com/products/memory/hbm/hbm4) Micron Technology
7.  A [SK hynix Partners with TSMC to Strengthen HBM Technological Leadership](https://news.skhynix.com/sk-hynix-partners-with-tsmc-to-strengthen-hbm-technological-leadership/) SK hynix
8.  A [HBM3e and HBM4: IC design guide for next-generation high bandwidth memory](https://blogs.sw.siemens.com/semiconductor-packaging/2026/04/24/hbm3e-hbm4-ic-design-guide/) Siemens Digital Industries Software · 24 April 2026
9.  A [\[Tech Note\] Hybrid Bonding: Evolving into a Foundational Technology for Improving Semiconductor Performance](https://news.skhynix.com/en/tech-note-series-ep2/) SK hynix
10.  A [SK hynix breaks ground on $4 billion advanced packaging production facility in Purdue Research Park](https://www.purdue.edu/newsroom/2026/Q3/sk-hynix-breaks-ground-on-4-billion-advanced-packaging-production-facility-in-purdue-research-park/) Purdue University · 27 August 2026
11.  A [SK hynix Inc., Form 424B4 prospectus for the period ended 2026-07-10 (424(B)(4))](https://www.sec.gov/Archives/edgar/data/2120882/000119312526299963/d32785d424b4.htm) U.S. Securities and Exchange Commission (filing by SK hynix Inc.) · 10 July 2026
12.  A [NVIDIA GB300 NVL72](https://www.nvidia.com/en-us/data-center/gb300-nvl72/) Nvidia · 23 July 2026
13.  A [Inside NVIDIA Rubin GPU Architecture: Powering the Era of Agentic AI](https://developer.nvidia.com/blog/inside-nvidia-rubin-gpu-architecture-powering-the-era-of-agentic-ai/) Nvidia · 21 July 2026
14.  B [AMD Instinct MI355X Specs, Pricing & AI Inference Benchmarks](https://inferencex.semianalysis.com/chips/mi355x) SemiAnalysis
15.  A [Foreign-Produced Direct Product Rule Additions, and Refinements to Controls for Advanced Computing and Semiconductor Manufacturing Items](https://www.federalregister.gov/documents/2024/12/05/2024-28270/foreign-produced-direct-product-rule-additions-and-refinements-to-controls-for-advanced-computing) Federal Register (Commerce Department; Industry and Security Bureau) · 5 December 2024
16.  A [15 CFR 742.6, Regional stability](https://www.ecfr.gov/current/title-15/subtitle-B/chapter-VII/subchapter-C/part-742/section-742.6) Electronic Code of Federal Regulations

## Advanced Packaging ^advanced-packaging

Lithography stopped being the limit on chip size in 2022. The limit now is how large an interposer, the silicon base plate under the chips, TSMC can build, and through 2025 how many it could build a month.

1,402 words / 6 minSpecimen: CoWoS package, exploded

In plain terms

Packaging joins finished chips into one component and mounts them on a base, called a substrate, wired almost as finely as the chips themselves. A lithography machine, which prints a chip's circuits, can cover only a rectangle about the size of a postage stamp in one shot, and a modern accelerator needs more circuit than fits in one, so it cannot be one chip. It is made as several pieces, set side by side on a shared slab of silicon and wired together through it, with the stacked memory a few millimeters away. Slab, chips and base all expand at different rates when heated, so the package can warp and its joints crack. Getting that right in large numbers is hard enough that nearly every AI accelerator is packaged by TSMC, in Taiwan.

### In short ^in-short-11

Advanced packaging capped AI chip output through 2024 and 2025: the physics was solved and the lines were not built. On Epoch AI's estimate Nvidia alone took 60.3 percent of the world's CoWoS in 2025, and four American designers took around 90 percent [9](https://epoch.ai/data-insights/ai-chip-supply-chain-constraints). By March 2026 the binding constraint had moved back to front-end wafers [10](https://newsletter.semianalysis.com/p/the-great-ai-silicon-shortage). The concentration is unchanged: China can package chips but not the 2.5D structures AI accelerators need, and the American alternatives do not start until 2028.

Concentration **Extreme**

Substitutability **Moderate** Intel's EMIB can do the same job as TSMC's CoWoS, and the real shortage is in making enough working packages at the volume Nvidia orders.

Price or market size **No public wafer counts** TSMC told investors CoWoS capacity would grow about 60% a year, and keeps adding to that, but will not publish the total. Epoch AI estimates Nvidia alone used 60.3% of the world's CoWoS capacity in 2025

Who leads

-   TWTSMC Almost all CoWoS for leading AI accelerators
-   TWASE Technology NT$645.4B revenue, 2025; the largest outsourced assembly and test firm
-   USAmkor $6.71B net sales, 2025; the largest American assembly and test firm
-   CNJCET RMB 35.96B revenue, 2024; the largest Chinese assembly and test firm
-   SGASMPT $532.1M advanced packaging revenue, 2025; thermocompression bonders

Where it is made

-   TWTaiwan TSMC AP fabs and the OSAT cluster; almost all 2.5D capacity for AI accelerators
-   USUnited States Amkor Peoria, Arizona from 2028; two TSMC advanced packaging plants planned in Arizona
-   CNChina JCET, Tongfu and HT-Tech, strong in conventional assembly and test, weak in 2.5D
-   NLNetherlands Besi hybrid and die bonders
-   JPJapan Disco grinders and dicers; TEL and Shibaura bonding tools

Why substitution is possible

None of the packaging steps is unusual, and Intel's EMIB does the same job when TSMC's CoWoS is sold out. The hard part is volume. A newcomer has to buy enough bonding machines and run enough practice lots to make the interposer, the silicon base plate under the chips, at 5.5 times the area a scanner prints in one shot. It then has to attach the memory stacks, have them work, and do all of that at the volume Nvidia alone orders. Amkor's plant in Peoria, Arizona shows the timing: production starts in early 2028, so the wait is two to five years.

Where China stands

China is far stronger at packaging and testing chips than at making them. JCET alone had revenue of RMB 35.96 billion in 2024. Chinese tool makers gained share in packaging and test tools while gaining none in atomic layer deposition or lithography. Almost none of that Chinese packaging is built on a silicon interposer, the kind AI accelerators need.

Where the US stands

No firm yet does CoWoS-class packaging in volume in the United States. Amkor is building a $7B packaging and test plant in Peoria, Arizona, with up to $407M of CHIPS Act money, and production starts in early 2028.

A lithography scanner prints a rectangle 26 mm by 33 mm, or 858 mm2, in one exposure [1](https://www.asml.com/en/products/euv-lithography-systems/twinscan-nxe3400c). Every AI accelerator worth buying is bigger than that. Packaging is the stage that lets an accelerator be larger than that rectangle, and it decides how much larger.

### How it works ^how-it-works-11

High bandwidth memory gives a second reason to split the package: its 1,024-bit or 2,048-bit connection, that many wires at once, is too wide for a resin base board to carry, so the memory sits beside the logic on a shared silicon carrier, the interposer.

![](https://chipsupplychain.org/media/package-light-end.jpg)

The parts of an AI accelerator

The name CoWoS says the order: chip onto wafer, then wafer onto substrate. TSMC makes a thin silicon wafer carrying wiring and vertical copper vias, metal-filled holes that join one layer of wiring to the next, but no transistors. It bonds the logic dies and memory stacks face down onto that wafer with microbumps, dots of solder 30 to 40 microns apart, about a third of a hair's width, each dot one electrical joint. Then it cuts the interposer out of the wafer, attaches it to the resin substrate, and the substrate goes onto its board.

Each of those packaging steps is ordinary on its own. But one cracked joint scraps a package holding eight qualified HBM stacks and two of the most expensive logic dies ever made.

### Variants and trade-offs ^variants-and-trade-offs-11

| Family | Carrier | Size limit | Used for |
| --- | --- | --- | --- |
| CoWoS-S | Full silicon interposer | 3.3x reticle, about 2,700 mm2 | H100-class parts |
| CoWoS-R | Resin interposer with fine redistribution wiring | Above 3.3x reticle | Cost-sensitive, fewer HBM stacks |
| CoWoS-L | Redistribution wiring with local silicon bridges | 5.5x reticle in production, 9.5x in development | Blackwell, Rubin |

#### 2.5D: silicon, RDL and bridges ^2-5d-silicon-rdl

TSMC has run CoWoS in volume since 2012 [2](https://3dfabric.tsmc.com/english/dedicatedFoundry/technology/cowos.htm). CoWoS-S wires most finely, but its interposer is one unbroken piece of silicon whose yield falls as the area grows, so CoWoS-L replaces the slab with fine wiring and small silicon bridges only where the wiring is dense. Intel's EMIB buries the same bridge idea in the resin substrate, and is a credible second source when CoWoS capacity is short.

Blackwell was the first high-volume design on CoWoS-L, and it went badly. The bridges carrying the 10 TB/s link between the two compute dies have to be placed to a tolerance that warping makes hard to hold [3](https://semianalysis.com/2024/08/04/nvidias-blackwell-reworked-shipment/).

#### 3D: SoIC, Foveros, X-Cube ^3d-soic-foveros-x-cube

TSMC's SoIC and Intel's Foveros bond dies face to face, copper pad to copper pad with no solder, packing the connections far closer than microbumps allow. TSMC put 3 nm SoIC into volume production in 2025 [4](https://investor.tsmc.com/static/annualReports/2025/english/pdf/2025_tsmc_ar_e_ch5.pdf), with an A14-on-A14 version due in 2029 carrying 1.8 times as many connections between the dies as the 2 nm generation [5](https://pr.tsmc.com/english/news/3302). Heat decides the layout: the bottom die overheats and the top is hard to power, so 3D designs often put cache underneath and compute on top.

#### Two ways off the silicon interposer ^two-ways-off-the

Panel-level packaging swaps the round wafer for a rectangular panel and wastes far less area; see [[#^test-and-assembly|Test and assembly]]. JEDEC published SPHBM4 on 13 July 2026. It puts HBM4 memory on a base chip carrying 512 data signals instead of 2,048, which spaces the connections widely enough to mount the stack on a standard resin substrate, off the silicon interposer altogether [6](https://www.jedec.org/news/pressreleases/new-jedec%C2%AE-sphbm4-standard-enables-hbm4-class-bandwidth-organic-substrates).

### Capacity ^capacity

TSMC does not publish a CoWoS wafer number, and will not. At its 2024 symposium it told investors capacity would grow at a 60 percent compound rate, and on the July 2024 earnings call C.C. Wei said he could not reach supply and demand balance [7](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2024-08/5122725a56670882d777a8e8bfe0ed247cc55330/TSMC%202Q24%20Transcript.pdf).

In October 2025 Wei would still say only that TSMC would add capacity again in 2026 and give the real figure the year after, and that front end and back end were both, in his word, tight [8](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2025-10/6860312f04fd291d0f26b46c1234f84e6332717e/TSMC%203Q25%20Transcript.pdf).

Epoch AI weighs each designer's component use against world supply and puts Nvidia at 60.3 percent of all CoWoS in 2025, with a 90 percent confidence interval of 56.5 to 64.3; Google took 13.5, AMD 8.4 and Amazon 7.4 [9](https://epoch.ai/data-insights/ai-chip-supply-chain-constraints). Those four absorbed around 90 percent of all CoWoS and all HBM by value while taking about 12 percent of the world's advanced logic wafers, which is why packaging ran out and logic did not.

Who consumed the world's CoWoS capacity, 2025%

Nvidia **60.3%** Google **13.5%** AMD **8.4%** Amazon **7.4%** Everyone else **10.4%**

Source: [Epoch AI, advanced packaging and HBM were the bottlenecks on AI chip production in 2025](https://epoch.ai/data-insights/ai-chip-supply-chain-constraints)

SemiAnalysis reported in March 2026 that front-end wafers are now the dominant bottleneck and CoWoS supply is easing, partly because TSMC has no reason to build interposer lines its N3 output cannot feed [10](https://newsletter.semianalysis.com/p/the-great-ai-silicon-shortage).

### Who makes it ^who-makes-it-11

CoWoS interposer size on TSMC's roadmapreticles

2024, CoWoS-L 3.5 2026, in production 5.5 In development 9.5 2028 14

Source: [TSMC 2025 annual report and 2026 technology symposium](https://pr.tsmc.com/english/news/3302)

The word packaging covers two industries. TSMC does the 2.5D work, chips side by side on a shared carrier, in its own back-end fabs; everything else goes to outsourced assembly and test firms. ASE Technology Holding, the largest, billed NT$645.4 billion in 2025, with its assembly and test business up 23 percent, and Amkor, the largest American one, billed $6.71 billion [11](https://www.prnewswire.com/news-releases/ase-technology-holding-co-ltd-reports-its-unaudited-consolidated-financial-results-for-the-fourth-quarter-and-the-full-year-of-2025-302679779.html) [12](https://www.sec.gov/Archives/edgar/data/1047127/000104712726000007/amkr123125erex-991.htm).

The tools are a narrower chokepoint than the assembly houses.

-   **Thermocompression bonding.** Pressing dies together under heat and force. ASMPT's advanced packaging revenue reached $532.1 million in 2025, with the bonder line up about 146 percent; it targets 35 to 40 percent of a market it puts at $1.6 billion by 2028 [13](https://www.asmpt.com/en/investor-relations/news-events/asmpt-announces-2025-annual-results/).
-   **Hybrid bonding.** Solder disappears and copper pads meet directly. Applied Materials built its Kinex bonder with Besi, which makes the placement head [14](https://www.appliedmaterials.com/eu/en/product-library/kinex-integrated-die-to-wafer-hybrid-bonding-system.html).
-   **Grinding and dicing.** Disco dominates the steps that thin wafers and cut packages apart; see [[#^test-and-assembly|Test and assembly]] [15](https://newsletter.semianalysis.com/p/disco-corporation-the-world-leader).

TSMC's Arizona commitment reached $265 billion in July 2026 and covers two advanced packaging plants alongside 10 fabs [16](https://www.azcommerce.com/news-events/news/2026/7/tsmc-announcement/). Amkor started building a $7 billion campus in Peoria in October 2025, backed by up to $407 million of CHIPS money, producing from early 2028 [17](https://ir.amkor.com/news-releases/news-release-details/amkor-technology-breaks-ground-new-semiconductor-advanced), and Wei confirms it will open before TSMC's own two do [8](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2025-10/6860312f04fd291d0f26b46c1234f84e6332717e/TSMC%203Q25%20Transcript.pdf).

### The chokepoint ^the-chokepoint-11

China-based suppliers' share of back-end tool segments, 2024%

Test, linear and discrete 69% Burn-in test 9% Advanced packaging tools 7% SoC test 5% Atomic layer deposition 1%

Source: [CSET, Inside Beijing’s Chipmaking Offensive (ALD shown for contrast, under 1%)](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/)

JCET, the largest Chinese assembler, billed RMB 35.96 billion in 2024, up 21 percent [19](https://www.jcetglobal.com/en/site/news-detail?id=1952), and Chinese toolmakers took real share in packaging and test equipment over the same years they took none in atomic layer deposition [18](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/). Packaging tools are less export-controlled than lithography, and Huawei's most credible response to the restrictions is to build big chips from small chiplets cut on SMIC silicon and assembled at home. China still has no silicon-interposer 2.5D at volume with qualified HBM beside it.

Each generation on TSMC's roadmap needs a larger interposer.

-   **2028.** A 14-reticle interposer carrying about ten large compute dies and 20 HBM stacks, roughly 12,000 mm2 of silicon, about the area of a compact disc [5](https://pr.tsmc.com/english/news/3302).
-   **2029.** More than 14 reticles, and a 40-reticle System-on-Wafer beside it [5](https://pr.tsmc.com/english/news/3302).

### Key evaluation criteria ^key-evaluation-criteria-11

-   **Interposer area** is the limit on how much logic and memory fit, now 5.5x reticle on CoWoS-L [5](https://pr.tsmc.com/english/news/3302).
-   **Package yield** decides whether a generation ships on time, and nobody publishes it.
-   **Warpage control** covers the expansion mismatch between die, bridge, interposer and substrate that broke early CoWoS-L and gets harder as packages grow [3](https://semianalysis.com/2024/08/04/nvidias-blackwell-reworked-shipment/).
-   **HBM stacks supported** is about 20 on the 14-reticle package due in 2028 [5](https://pr.tsmc.com/english/news/3302).
-   **Bonder throughput** is slow by nature: thermocompression and hybrid bonding place one die at a time, and three or four firms hold the tools [13](https://www.asmpt.com/en/investor-relations/news-events/asmpt-announces-2025-annual-results/).
-   **Substrate size** limits everything above it. A 14-reticle interposer needs a resin substrate that will not warp under it, which pushes ABF build-up film to its limits; see [[#^substrates-and-pcbs]].

Card 1 of 4Question

Why is an AI accelerator built from several chips in one package?

Card 1 of 4Answer

It needs more circuit than a lithography machine can print in one shot.

Packaging sets the pieces and their memory side by side on a shared slab of silicon and wires them together. [[#^how-it-works-11|Reread: How it works]]

Card 2 of 4Question

Who packages nearly every AI accelerator?

Card 2 of 4Answer

TSMC, in Taiwan.

Its process is called CoWoS. Nvidia alone took an estimated 60.3 percent of it in 2025. [[#^who-makes-it-11|Reread: Who makes it]]

Card 3 of 4Question

Why did packaging limit AI chip output in 2024 and 2025?

Card 3 of 4Answer

Too few packaging lines had been built.

The methods already worked. By March 2026 the limit had moved back to making wafers. [[#^the-chokepoint-11|Reread: The chokepoint]]

Card 4 of 4Question

Can China or the United States package AI accelerators at volume?

Card 4 of 4Answer

Not yet.

China packages chips at scale, but almost none on the silicon slab AI chips need. The first American line, Amkor's in Arizona, starts in early 2028. [[#^the-chokepoint-11|Reread: The chokepoint]]

#### Four things to remember ^four-things-to-remember-10

-   An AI accelerator needs more circuit than one chip can hold, so packaging joins several chips and their memory.
-   TSMC packages nearly every AI accelerator, in Taiwan.
-   Packaging limited AI chip output in 2024 and 2025 because too few lines had been built.
-   Neither China nor the United States packages AI accelerators at volume yet.

Sources (19)

1.  A [TWINSCAN NXE:3400C](https://www.asml.com/en/products/euv-lithography-systems/twinscan-nxe3400c) ASML
2.  A [TSMC, CoWoS technology page](https://3dfabric.tsmc.com/english/dedicatedFoundry/technology/cowos.htm) TSMC
3.  B [Nvidia's Blackwell Reworked - Shipment Delays & GB200A Reworked Platforms](https://semianalysis.com/2024/08/04/nvidias-blackwell-reworked-shipment/) SemiAnalysis · 4 August 2024
4.  A [TSMC 2025 Annual Report, chapter 5](https://investor.tsmc.com/static/annualReports/2025/english/pdf/2025_tsmc_ar_e_ch5.pdf) TSMC
5.  A [TSMC Debuts A13 Technology at 2026 North America Technology Symposium](https://pr.tsmc.com/english/news/3302) TSMC · 23 April 2026
6.  A [New JEDEC® SPHBM4 Standard Enables HBM4-Class Bandwidth on Organic Substrates](https://www.jedec.org/news/pressreleases/new-jedec%C2%AE-sphbm4-standard-enables-hbm4-class-bandwidth-organic-substrates) JEDEC Solid State Technology Association · 13 July 2026
7.  A [Q2 2024 Taiwan Semiconductor Manufacturing Co Ltd Earnings Call (Chinese, English) — edited transcript](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2024-08/5122725a56670882d777a8e8bfe0ed247cc55330/TSMC%202Q24%20Transcript.pdf) Refinitiv StreetEvents (transcript of a TSMC earnings call), via TSMC · 18 July 2024
8.  A [Q3 2025 Taiwan Semiconductor Manufacturing Co Ltd Earnings Call (Chinese, English) — edited transcript](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2025-10/6860312f04fd291d0f26b46c1234f84e6332717e/TSMC%203Q25%20Transcript.pdf) Refinitiv StreetEvents (transcript of a TSMC earnings call), via TSMC · 16 October 2025
9.  A [Advanced packaging and HBM, not logic dies, were the bottlenecks on AI chip production in 2025](https://epoch.ai/data-insights/ai-chip-supply-chain-constraints) Epoch AI · 12 March 2026
10.  B [The Great AI Silicon Shortage](https://newsletter.semianalysis.com/p/the-great-ai-silicon-shortage) SemiAnalysis · 12 March 2026
11.  A [ASE Technology Holding Co., Ltd. Reports Its Unaudited Consolidated Financial Results for the Fourth Quarter and the Full Year of 2025](https://www.prnewswire.com/news-releases/ase-technology-holding-co-ltd-reports-its-unaudited-consolidated-financial-results-for-the-fourth-quarter-and-the-full-year-of-2025-302679779.html) PR Newswire · 5 February 2026
12.  A [AMKOR TECHNOLOGY, INC., Form 8-K current report for the period ended 2026-02-09 (8-K)](https://www.sec.gov/Archives/edgar/data/1047127/000104712726000007/amkr123125erex-991.htm) U.S. Securities and Exchange Commission (filing by AMKOR TECHNOLOGY, INC.) · 9 February 2026
13.  A [ASMPT Announces 2025 Annual Results AI-Driven Structural Growth Underpins Group Performance](https://www.asmpt.com/en/investor-relations/news-events/asmpt-announces-2025-annual-results/) ASMPT · 4 March 2026
14.  A [Applied Materials, Kinex integrated die-to-wafer hybrid bonding system product page](https://www.appliedmaterials.com/eu/en/product-library/kinex-integrated-die-to-wafer-hybrid-bonding-system.html) Applied Materials
15.  B [DISCO Corporation, The World Leader In Semiconductor Capital Equipment For Cutting, Grinding, Polishing](https://newsletter.semianalysis.com/p/disco-corporation-the-world-leader) SemiAnalysis · 19 July 2022
16.  A [TSMC Announces Additional $100 Billion Investment in Arizona](https://www.azcommerce.com/news-events/news/2026/7/tsmc-announcement/) Arizona Commerce Authority · 16 July 2026
17.  A [Amkor Technology Breaks Ground on New Semiconductor Advanced Packaging and Test Campus in Arizona; Expands Investment to $7 Billion](https://ir.amkor.com/news-releases/news-release-details/amkor-technology-breaks-ground-new-semiconductor-advanced) Amkor Technology
18.  A [Inside Beijing’s Chipmaking Offensive](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/) Center for Security and Emerging Technology (CSET) · 14 July 2025
19.  A [JCET Releases 2024 Annual Report, Achieves Record-High Revenue](https://www.jcetglobal.com/en/site/news-detail?id=1952) JCET Group · 20 April 2025

## Substrates and PCBs ^substrates-and-pcbs

A Japanese food company makes 95 percent of the insulating film inside high-end chip packages, and a Japanese textile company weaves the glass cloth beneath it.

1,356 words / 6 minSpecimen: substrate layers

In plain terms

A package substrate is the adapter between a chip and the circuit board under it. The chip's connections come out finer than a human hair; the board is wired in millimeters. The substrate is built up like plywood. A stiff core of glass cloth and resin sits in the middle. Thin sheets of epoxy film are pressed onto both faces, a laser burns holes through each sheet, and copper is plated into the holes to carry signals from one layer to the next. Every added layer is another set of holes that can fail. A handful of firms build these substrates, and the film and the glass cloth each come from a single Japanese supplier, so a shortage here stops accelerators shipping.

### In short ^in-short-12

TSMC says packaging capacity already caps what its customers can ship. The two materials that make a substrate possible come from single Japanese suppliers: Ajinomoto puts its film at 95 percent of that market, and Nitto Boseki claims an overwhelming advantage in the glass cloth beneath it. Substrate plants in Japan, Taiwan and Korea are spending billions, but film and glass cloth add capacity more slowly than GPU output grows. Glass cores fix the physics eventually; on Intel's and Samsung's own dates, they do not fix 2027.

Concentration **Extreme**

Substitutability **Hard** Rated on the insulating film inside the substrate: Ajinomoto supplies about 95 percent of it by its own count, and every substrate maker would have to re-approve a replacement layer by layer.

Price or market size **Ibiden alone is spending about JPY 500 billion on high-performance substrate capacity from fiscal 2026 to 2028, JPY 220 billion of it in the first phase**

Who leads

-   JPAjinomoto 95% of the world market for insulating film in high-end processor packages, on its own account
-   JPNitto Boseki Claims an overwhelming lead in low-expansion glass cloth
-   JPIbiden Says it wins close to 100% of each new generation of interposer substrates at launch
-   TWUnimicron Build-up substrates were 52% of sales in Q2 2026
-   KRSamsung Electro-Mechanics Package solution sales KRW 771.6bn in Q2 2026, up 37%

Where it is made

-   JPJapan Build-up film, low-expansion glass cloth, and Ibiden and Shinko substrate plants in Gifu and Nagano
-   TWTaiwan Unimicron, Nan Ya PCB, Kinsus; the largest cluster of substrate makers selling to all comers
-   KRSouth Korea Samsung Electro-Mechanics, LG Innotek, and a glass-core joint venture with Sumitomo Chemical
-   CNChina Most of the circuit board competition, alongside Taiwan; now pushing into glass cloth and build-up film
-   ATAustria AT&S, the only European advanced substrate maker of scale

Why substitution is slow

A few firms build substrates. Money can expand their plants, and every large one is expanding. The single points of failure are in the materials inside the substrate. Ajinomoto makes the thin insulating film between the substrate's wiring layers, puts its own share at about 95 percent, and has been the standard since 1999. Beneath that film is Nitto Boseki's glass cloth, woven so it barely swells with heat. A newcomer can build a line to make such a film. Every substrate maker and every packaging house then has to test the new film in each layer of each product before using it. That takes years at each of them, so the whole switch takes five to ten years.

Where China stands

Most of the firms competing in circuit boards are Chinese or Taiwanese. Nitto Boseki itself calls them aggressive fast followers in special glass. Chinese firms still make almost none of the high-end insulating film.

Where the US stands

No American firm makes these substrates in volume. TTM Technologies is the main American circuit board maker. Data center computing was 24 percent of its sales in 2025, up from 14 percent in 2023. Intel is developing substrates made of glass for the second half of the decade.

On TSMC's July 2026 earnings call, chief executive C.C. Wei said packaging capacity is now so tight that it limits customers' growth [1](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2026-08/3e494f0c14dd0890f897aa044415e21d93486cc4/TSMC%202Q26%20Transcript.pdf). The silicon interposer that wires chips together inside a package spans a few millimeters. Past its edge the wiring turns to epoxy and glass: a build-up substrate, a printed circuit board of thirty layers, then a rack.

### How it works ^how-it-works-12

The substrate maker drills the core and plates it with copper before the build-up starts. Each cycle then presses on a film of epoxy about 10 micrometers thick, burns holes through it with a laser, plates copper into the holes to link the layers, and etches the wiring on top [2](https://www.ajinomoto.com/stories/the-ajinomoto-groups-unexpected-role-in-semiconductor-manufacturing-the-insulating-film-abf-born-from-aminoscience). A human hair is ten times thicker than one of those films [3](https://www.ajinomoto.co.jp/company/en/ir/event/business_briefing/main/01113/teaserItems1/01/linkList/00/link/3_ICT_E.pdf).

Silicon and epoxy swell at different rates when heated, so the larger the package, the more it warps. AI parts are the largest: Ajinomoto counts 18 layers of its film in a high-performance computing substrate against six in a PC part, on a body three and a half times the area [3](https://www.ajinomoto.co.jp/company/en/ir/event/business_briefing/main/01113/teaserItems1/01/linkList/00/link/3_ICT_E.pdf). The fix is a core that barely expands, which means low-expansion glass cloth and tighter control of the resin.

### Variants and trade-offs ^variants-and-trade-offs-12

#### BT substrates ^bt-substrates

Bismaleimide-triazine laminate, or BT, is the cheaper and older family. It still leads on unit volume and suits memory stacks and mobile parts, but it cannot hold the fine wiring or the flatness a large logic die needs.

#### ABF build-up substrates ^abf-build-up-substrates

Ajinomoto Build-up Film, or ABF, is the insulating sheet between the copper layers, and it sits under every high-end CPU, GPU and AI accelerator. A major chipmaker first used it in 1999, and Ajinomoto calls it the de facto standard in package development ever since [3](https://www.ajinomoto.co.jp/company/en/ir/event/business_briefing/main/01113/teaserItems1/01/linkList/00/link/3_ICT_E.pdf). Asked on the company's own site whether its share was nearer 30 or 50 percent, the electronic materials division answered: "More like 95 percent market share", and said practically all high-performance computers and servers rely on it [2](https://www.ajinomoto.com/stories/the-ajinomoto-groups-unexpected-role-in-semiconductor-manufacturing-the-insulating-film-abf-born-from-aminoscience).

Layers of build-up film in one package substratelayers

PC substrate 6 HPC substrate 18

Source: [Ajinomoto business briefing on ABF, June 2023](https://www.ajinomoto.co.jp/company/en/ir/event/business_briefing/main/01113/teaserItems1/01/linkList/00/link/3_ICT_E.pdf)

#### Glass core substrates ^glass-core-substrates

A glass core in place of resin removes most of the swelling problem, which is why chipmakers and substrate makers are both trying it.

-   **Intel** announced glass substrates in September 2023 for the latter part of this decade [4](https://download.intel.com/newsroom/archive/2025/en-us-2023-09-18-intel-unveils-industryleading-glass-substrates-to-meet-demand-for-more-powerful-compute.pdf).
-   **Samsung Electro-Mechanics** signed a joint venture with Sumitomo Chemical in November 2025 to make glass core, with mass production after 2027 [5](https://samsungsem.com/global/newsroom/news/view.do?id=9850).

Both programs point past 2027, so glass does not help before then.

### The materials underneath ^the-materials-underneath

Ajinomoto's film is a small line in a food company's accounts and a chokepoint for every chipmaker. The Healthcare and Others segment that carries electronic materials lifted business profit 45.1 percent to JPY 66.2 billion in the year to March 2026, and Ajinomoto credits the materials for most of that [6](https://www.ajinomoto.co.jp/company/en/ir/library/result/main/014/teaserItems1/0/linkList/06/link/FY25Q4_Tanshin_E.pdf). Capacity comes slowly: about JPY 25 billion of growth investment from fiscal 2023, sized against demand out to 2030 [3](https://www.ajinomoto.co.jp/company/en/ir/event/business_briefing/main/01113/teaserItems1/01/linkList/00/link/3_ICT_E.pdf).

The core one layer down comes from one supplier too. Nitto Boseki's T-glass is stiff and barely swells when heated, which is what a dense package substrate needs [7](https://www.nittobo.co.jp/eng/business/electronicmaterials/t-glass.htm). The company claims an overwhelming advantage in quality and capacity for low-expansion glass, says demand has risen two to three times since its fiscal 2024 to 2027 plan was set, and is spending JPY 80 billion over those four years to catch up [8](https://www.nittobo.co.jp/eng/ir/pdf/Nittobo_Integrated-Report_2025.pdf). Apple and Qualcomm are among the customers worried about Japanese glass cloth supply [9](https://asia.nikkei.com/business/technology/tech-asia/apple-and-qualcomm-fret-over-strained-supplies-of-japan-s-glass-cloth).

Chinese firms are entering this layer, and Nitto Boseki says so itself: it names Chinese and Taiwanese firms as aggressive fast followers in special glass [8](https://www.nittobo.co.jp/eng/ir/pdf/Nittobo_Integrated-Report_2025.pdf). At stake is a chip materials market Nikkei sizes at $73 billion [10](https://asia.nikkei.com/business/tech/semiconductors/china-chip-material-makers-battle-japan-rivals-for-73bn-market).

### Who makes it ^who-makes-it-12

The plants that build substrates for other firms are an Asian oligopoly, and every large one is expanding. The White House's 2021 hundred-day supply chain review recorded build-up substrate among the materials commenters called vulnerable, and named the makers as Ibiden, Shinko, Nanya, Samsung, Unimicron, Shennan Circuits, Zhuhai Yueya and AKM. None of the eight is American [11](https://bidenwhitehouse.archives.gov/wp-content/uploads/2021/06/100-day-supply-chain-review-report.pdf).

-   **Ibiden** will invest about JPY 500 billion from fiscal 2026 to fiscal 2028, starting with JPY 220 billion at its Gama plant and mass production from fiscal 2027 [12](https://www.ibiden.com/company/2026/02/notice-regarding-capital-investment-plan-for-high-performance-ic-package-substrates.html). In May 2026 management said it typically takes close to 100 percent of a new generation of interposer substrates at launch and loses 20 to 30 points three to six months later. On silicon-bridge substrates, it said, wiring the underside is hard enough that it expects to keep its technical lead through fiscal 2030 [13](https://www.ibiden.com/ir/items/en_QA_FY25Q4.pdf).
-   **Unimicron** took NT$42.9 billion of sales in the second quarter of 2026, 52 percent of it build-up substrates and 61 percent of it AI data center work [14](https://www.unimicron.com/files/money/Earnings/en/2026-Q2-consolidated-en.pdf).
-   **Samsung Electro-Mechanics** grew package solution sales 37 percent year on year to KRW 771.6 billion in the second quarter, on substrates for AI accelerators and server processors [15](https://m.samsungsem.com/global/newsroom/news/view.do?id=10462).

Shinko has a new owner: Fujitsu sold its 50.02 percent stake to a fund run by the state-backed Japan Investment Corporation [16](https://www.jiccapital.co.jp/en/news/.assets/E_20250217_JIC_JICC_PressRelease.pdf).

Unimicron sales by technology, second quarter 2026%

ABF substrate **52%** PCB **27%** BT substrate **9%** HDI **9%** FPC **2%** Other **1%**

Source: [Unimicron 2026 Q2 earnings conference](https://www.unimicron.com/files/money/Earnings/en/2026-Q2-consolidated-en.pdf)

### The boards under the GPU ^the-boards-under-the

TTM Technologies says it regularly builds printed circuit boards of more than 30 layers and can go past 70 [17](https://www.sec.gov/Archives/edgar/data/1116942/000119312526051976/ttmi-20251229.htm). Those layers carry hundreds of amps to the GPUs and route traffic between them fast enough that how much signal the laminate absorbs becomes a main design constraint.

Data center computing was 24 percent of TTM's $2.91 billion of fiscal 2025 revenue, against 14 percent two years earlier [17](https://www.sec.gov/Archives/edgar/data/1116942/000119312526051976/ttmi-20251229.htm) [18](https://data.sec.gov/api/xbrl/companyconcept/CIK0001116942/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json). It names its competition as mostly Chinese and Taiwanese [17](https://www.sec.gov/Archives/edgar/data/1116942/000119312526051976/ttmi-20251229.htm). The alternative is Southeast Asia, where Thailand has built an AI board industry [19](https://asia.nikkei.com/business/technology/tech-asia/thailand-carves-out-a-less-glamorous-ai-niche-printed-circuit-boards).

### The chokepoint ^the-chokepoint-12

Money can expand an oligopoly of substrate plants, and it is being spent. The single points of failure are one layer down: one company's film and one company's glass cloth, both Japanese, both running at full capacity and adding more on building schedules measured in years while AI demand compounds quarterly.

Flatness is the first thing lost as packages grow. TSMC has told investors that its CoWoS packaging roadmap goes beyond 14 times the area a lithography machine can print in one shot [1](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2026-08/3e494f0c14dd0890f897aa044415e21d93486cc4/TSMC%202Q26%20Transcript.pdf). Bigger bodies mean more warping, more layers, more holes that can break the circuit, and lower yield on a part that is already expensive before a die touches it.

### Key evaluation criteria ^key-evaluation-criteria-12

-   **Layer count** sets how much current and how many signals the substrate can carry. Each added layer is another chance to lose the part.
-   **Body size** drives everything else. Once a body is much larger than the dies it carries, warping and handling take over from the wiring in deciding what can be built.
-   **Coefficient of thermal expansion**, how much a material swells when heated, must be close enough to silicon that the package survives repeated heating and cooling, which is what T-glass provides and why its supply matters.
-   **Dielectric properties**, how much signal the core laminate absorbs, set the speeds the substrate and the board underneath can run.
-   **Qualification time** protects the incumbents. Approving a second supplier for a film or a laminate takes years.

Card 1 of 4Question

What does a package substrate do?

Card 1 of 4Answer

It connects a chip's hair-fine connections to a circuit board wired in millimeters.

It is built in layers of epoxy film and copper around a stiff glass-cloth core. [[#^how-it-works-12|Reread: How it works]]

Card 2 of 4Question

Which two substrate materials each come from one Japanese supplier?

Card 2 of 4Answer

The insulating film, from Ajinomoto, and the glass cloth, from Nitto Boseki.

Ajinomoto puts its share of the film at about 95 percent. [[#^the-materials-underneath|Reread: The materials underneath]]

Card 3 of 4Question

Why would replacing Ajinomoto's film take years?

Card 3 of 4Answer

Every substrate maker would have to approve the new film in each layer of each product.

That takes five to ten years. [[#^the-chokepoint-12|Reread: The chokepoint]]

Card 4 of 4Question

Does any American firm make these substrates in volume?

Card 4 of 4Answer

No.

The makers are in Japan, Taiwan, Korea and China. [[#^who-makes-it-12|Reread: Who makes it]]

#### Four things to remember ^four-things-to-remember-11

-   A package substrate connects a chip's fine connections to a circuit board wired in millimeters.
-   The film and the glass cloth inside it each come from one Japanese supplier.
-   Replacing the film would take five to ten years of approvals.
-   No American firm makes these substrates in volume.

Sources (19)

1.  A [Q2 2026 Taiwan Semiconductor Manufacturing Co Ltd Earnings Call (Chinese, English) — edited transcript](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2026-08/3e494f0c14dd0890f897aa044415e21d93486cc4/TSMC%202Q26%20Transcript.pdf) LSEG StreetEvents (transcript of a TSMC earnings call), via TSMC · 16 July 2026
2.  A [The Ajinomoto Group’s Unexpected Role in Semiconductor Manufacturing: The Insulating Film “ABF” Born from “AminoScience” | Stories](https://www.ajinomoto.com/stories/the-ajinomoto-groups-unexpected-role-in-semiconductor-manufacturing-the-insulating-film-abf-born-from-aminoscience) Ajinomoto · 5 March 2026
3.  A [Ajinomoto, Business Briefing: ABF-Based Growth Strategy in ICT, 12 June 2023](https://www.ajinomoto.co.jp/company/en/ir/event/business_briefing/main/01113/teaserItems1/01/linkList/00/link/3_ICT_E.pdf) Ajinomoto · 12 June 2023
4.  A [Intel Unveils Industry-Leading Glass Substrates to Meet Demand for...](https://download.intel.com/newsroom/archive/2025/en-us-2023-09-18-intel-unveils-industryleading-glass-substrates-to-meet-demand-for-more-powerful-compute.pdf) Intel · 31 January 2025
5.  A [Samsung Electro-Mechanics Signs MOU with Sumitomo Chemical Group to Establish a Joint Venture for Glass Core Used in Package Substrates](https://samsungsem.com/global/newsroom/news/view.do?id=9850) Samsung Electro-Mechanics · 5 November 2025
6.  A [Note: This document has been translated from the Japanese original for reference purposes only. In the event of any](https://www.ajinomoto.co.jp/company/en/ir/library/result/main/014/teaserItems1/0/linkList/06/link/FY25Q4_Tanshin_E.pdf) Ajinomoto · 1 May 2026
7.  A [T-glass | Electronic Materials Business | Business and Products](https://www.nittobo.co.jp/eng/business/electronicmaterials/t-glass.htm) Nitto Boseki (Nittobo)
8.  A [2-4-1, Kojimachi, Chiyoda-ku, Tokyo, 102-8489, Japan](https://www.nittobo.co.jp/eng/ir/pdf/Nittobo_Integrated-Report_2025.pdf) Nitto Boseki (Nittobo) · 16 September 2025
9.  B [Apple and Qualcomm fret over strained supplies of Japan's glass cloth](https://asia.nikkei.com/business/technology/tech-asia/apple-and-qualcomm-fret-over-strained-supplies-of-japan-s-glass-cloth) Nikkei Asia · 14 January 2026
10.  B [China chip material makers battle Japan rivals for $73bn market](https://asia.nikkei.com/business/tech/semiconductors/china-chip-material-makers-battle-japan-rivals-for-73bn-market) Nikkei Asia · 1 July 2026
11.  A [BUILDING RESILIENT SUPPLY CHAINS,](https://bidenwhitehouse.archives.gov/wp-content/uploads/2021/06/100-day-supply-chain-review-report.pdf) The White House (Biden administration archive) · 7 June 2021
12.  A [Ibiden, Notice Regarding Capital Investment Plan for High-Performance IC Package Substrates](https://www.ibiden.com/company/2026/02/notice-regarding-capital-investment-plan-for-high-performance-ic-package-substrates.html) Ibiden · 3 February 2026
13.  A [Ibiden, questions and answers from the financial presentation for the year ended 31 March 2026](https://www.ibiden.com/ir/items/en_QA_FY25Q4.pdf) Ibiden · 12 May 2026
14.  A [Unimicron consolidated financial statements, second quarter 2026](https://www.unimicron.com/files/money/Earnings/en/2026-Q2-consolidated-en.pdf) Unimicron Technology
15.  A [Samsung Electro-Mechanics, Q2 2026 business results](https://m.samsungsem.com/global/newsroom/news/view.do?id=10462) Samsung Electro-Mechanics · 30 July 2026
16.  A [February 17, 2025 Japan Investment Corporation](https://www.jiccapital.co.jp/en/news/.assets/E_20250217_JIC_JICC_PressRelease.pdf) Japan Investment Corporation · 17 February 2025
17.  A [TTM TECHNOLOGIES INC, Form 10-K annual report for the period ended 2025-12-29 (10-K)](https://www.sec.gov/Archives/edgar/data/1116942/000119312526051976/ttmi-20251229.htm) U.S. Securities and Exchange Commission (filing by TTM TECHNOLOGIES INC) · 17 February 2026
18.  A [Revenue from Contract with Customer, Excluding Assessed Tax (us-gaap:RevenueFromContractWithCustomerExcludingAssessedTax) reported by TTM TECHNOLOGIES, INC., XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0001116942/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json) U.S. Securities and Exchange Commission (XBRL data for TTM TECHNOLOGIES, INC.)
19.  B [Thailand carves out a less-glamorous AI niche: printed circuit boards](https://asia.nikkei.com/business/technology/tech-asia/thailand-carves-out-a-less-glamorous-ai-niche-printed-circuit-boards) Nikkei Asia · 3 September 2025

## Test and Assembly ^test-and-assembly

Assembly and test decide which dies are allowed into a package that costs more than a car. One Japanese firm now sells two thirds of the world's chip testers.

1,251 words / 5 minSpecimen: probe card

In plain terms

Before a chip can be sold, a machine has to put questions to it and check every answer. While the chips are still on the wafer, thousands of needles press onto small metal pads on each one, send in signals and read what comes back; the tester marks any chip that answers wrong, and that chip goes no further. A modern accelerator glues together a dozen expensive pieces, and one bad piece throws away all of them. So the industry tests sooner, hotter and longer than it used to, to make a weak chip fail on the test bench before it reaches a finished product, and two firms, one Japanese and one American, sell most of the machines that do it.

### In short ^in-short-13

Test used to be the cheap step at the end. With a dozen expensive dies in one package, it now protects everything made before it: the market for logic chip testers grew about 68 percent in 2025 [7](https://www.advantest.com/document/en/investors/ir-library/result/JE_BIZ_260427_note.pdf) and burn-in has started moving back onto the wafer [3](https://www.aehr.com/2026/07/aehr-test-systems-reports-fiscal-2026-fourth-quarter-and-full-year-financial-results-with-record-quarterly-bookings-and-100-million-effective-backlog/). Advantest has turned a duopoly into a two-thirds share of the machines. The assembly business beneath it stays fragmented, and four of the top ten assembly and test firms are Chinese [19](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/), which is why export controls have little effect on assembly and test.

Concentration **High**

Substitutability **Moderate** No test or assembly tool has only one maker, but switching testers means rebuilding every one of the customer's test programs.

Price or market size **ASE and Amkor alone had $27.3 billion of revenue in 2025** ASE spent $4.1 billion on machinery and buildings in the first half of 2026

Who leads

-   JPAdvantest 65% of the tester market in 2025
-   USTeradyne Second in testers; about 80% of the market with Advantest
-   TWASE $20.6bn of 2025 revenue, the largest assembly and test contractor
-   USAmkor $6.71bn of 2025 revenue
-   JPDisco Leading share in dicing saws, grinders and blades

Where it is made

-   TWTaiwan ASE, Powertech, KYEC and ChipMOS; the largest assembly and test cluster
-   JPJapan Advantest testers, Disco dicing and grinding, Micronics Japan probe cards
-   USUnited States Teradyne, FormFactor, Cohu, Aehr; Amkor's Arizona packaging plant
-   CNChina Four of the top ten assembly and test firms by 2024 revenue are China-headquartered
-   MYMalaysia Penang and Kulim; Malaysia ships about 13% of the world's packaged chips

Why substitution is possible

Advantest and Teradyne sell about 80 percent of the testers between them, but both make machines that customers have approved, and the smaller kinds of test and assembly tool have several makers each. Customers rarely switch, because a new tester means rebuilding every test program, from the first prototype through to the production line. Advantest tells its investors the same thing. A newcomer pays that cost once and takes two to five years. The barrier is low enough that four of the top ten assembly and test firms are already Chinese.

Where China stands

Assembly and test is the stage where China is most competitive. CSET at Georgetown counts four of the top ten assembly and test firms by 2024 revenue as Chinese. The tools those firms use are far less tightly controlled than lithography or deposition tools.

Where the US stands

American firms are strong in test machines and probe cards, the beds of pins that touch each chip on the wafer: Teradyne, FormFactor, Cohu and Aehr. They are weak in assembly. Amkor is building a $7 billion packaging and test campus in Arizona and has a long-term deal with TSMC to fill it.

Semiconductor manufacturing runs to 400 to 600 steps, and Advantest counts test as the only one that puts electricity through the [1](https://www.advantest.com/document/en/investors/ir-library/investors-guide/Investors_Guide_2504E.pdf) chip . Every stage so far makes dies; the back end of the industry, assembly and test, decides which of them are allowed into a package.

### How it works ^how-it-works-13

Each round of test catches failures the round before it cannot see.

-   **Wafer sort.** Thousands of needles land on each die while it is still on the wafer, a tester drives patterns in and checks the answers, and the failures go no further.
-   **Burn-in.** Run the part hot and under power for hours, so anything that would fail early fails now, before assembly.
-   **Final test.** The tester runs the packaged part again, because packaging adds failures of its own.
-   **System-level test.** The finished part sits in a socket and runs something close to a real workload, because some failures appear only when everything runs at once.

Proving a die good before it is packaged is now worth far more. Aehr screens for early and hidden failures before dies are cut from the wafer, so a weak processor never reaches high-bandwidth memory and an expensive substrate [2](https://www.aehr.com/2026/08/aehr-receives-22-million-follow-on-order-for-ai-processor-wafer-level-burn-in-systems/). Its lead AI customer is moving burn-in off the finished system and onto the wafer, nine 300 mm wafers at a time [3](https://www.aehr.com/2026/07/aehr-test-systems-reports-fiscal-2026-fourth-quarter-and-full-year-financial-results-with-record-quarterly-bookings-and-100-million-effective-backlog/).

### Variants and trade-offs ^variants-and-trade-offs-13

#### Wafer sort and known-good die ^wafer-sort-and-known-good

The probe card that holds those needles is the hard part. For a high-bandwidth memory stack it must contact eight, twelve or sixteen dies at speed without degrading the signals [4](https://www.sec.gov/Archives/edgar/data/1039399/000103939926000009/form-20251227.htm). For a large logic die every needle must sit in the same plane, survive repeated touchdowns without drifting, and do it hot. Cards are custom to the device, so each new part means a new card and a new qualification.

#### Final test, burn-in and system-level test ^final-test-burn-in-and

The economics get worse as packages grow. TSMC has told investors that its CoWoS packaging roadmap runs beyond 14 times the area a lithography machine can print in one shot [5](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2026-08/3e494f0c14dd0890f897aa044415e21d93486cc4/TSMC%202Q26%20Transcript.pdf). Every added die is another chance to lose the whole assembly, which is why the number of test steps keeps rising. ASE ran 6,797 testers in the second quarter of 2025 and 8,348 a year later [6](https://www.sec.gov/Archives/edgar/data/1122411/000095010326011351/dp250868_6k.htm).

Automated test equipment: share of the ~$9.0bn tester market, 2025%

Advantest **65%** Teradyne and all others **35%**

Source: [Advantest FY2025 results briefing, April 2026](https://www.advantest.com/document/en/investors/ir-library/result/JE_BIZ_260427_note.pdf)

### Who makes it ^who-makes-it-13

Advantest puts its own share at about 65 percent of a $9.0 billion tester market in 2025: 66 percent of test for logic chips, up ten points in a year, and about 60 percent of memory test [7](https://www.advantest.com/document/en/investors/ir-library/result/JE_BIZ_260427_note.pdf). It and Teradyne hold about 80 percent between them [1](https://www.advantest.com/document/en/investors/ir-library/investors-guide/Investors_Guide_2504E.pdf). Teradyne grew 13 percent to $3.19 billion for 2025, with fourth-quarter revenue up 44 percent on AI demand [8](https://investors.teradyne.com/news-events/press-releases/detail/433/teradyne-reports-fourth-quarter-and-full-year-2025-results).

Where the tester money went in calendar 2025$bn

SoC testers **6.9** Memory testers **2.1**

%% validator-ignore-next-line --code article.block-repeated-nearby --reason intentional-repeat-in-distinct-structured-entries %%
Source: [Advantest FY2025 results briefing, April 2026](https://www.advantest.com/document/en/investors/ir-library/result/JE_BIZ_260427_note.pdf)

Below the two tester makers, the rest of the test and assembly equipment splits into niches, each with its own suppliers.

-   **Probe cards.** FormFactor took $785.0 million in fiscal 2025 [9](https://data.sec.gov/api/xbrl/companyconcept/CIK0001039399/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json); Technoprobe grew 15.7 percent to EUR 628.4 million, 38 percent of it from AI, and plans to double capacity by the end of 2027 [10](https://technoprobe.com/wp-content/uploads/2026/03/PR-FY-2025_.pdf).
-   **Handlers and burn-in**, the machines that feed parts into a tester and heat them. Cohu took $453.0 million in fiscal 2025 [11](https://data.sec.gov/api/xbrl/companyconcept/CIK0000021535/us-gaap/RevenueFromContractWithCustomerIncludingAssessedTax.json); Aehr did $50.0 million in fiscal 2026 but booked a record $60.7 million in the fourth quarter alone and guides to $130 million to $150 million in fiscal 2027 [3](https://www.aehr.com/2026/07/aehr-test-systems-reports-fiscal-2026-fourth-quarter-and-full-year-financial-results-with-record-quarterly-bookings-and-100-million-effective-backlog/).
-   **Dicing and grinding.** Disco leads in wafer grinders and the saws that cut wafers into dies [12](https://newsletter.semianalysis.com/p/disco-corporation-the-world-leader), and its newest saw handles pieces up to 400 by 400 mm, for packaging on rectangular panels [13](https://www.disco.co.jp/eg/news/corp/20251215_1.html).
-   **Bonding.** Kulicke and Soffa did $654.1 million in fiscal 2025 [14](https://data.sec.gov/api/xbrl/companyconcept/CIK0000056978/us-gaap/Revenues.json), while Besi's second-quarter 2026 revenue rose 68.7 percent to EUR 249.9 million on and data center demand [15](https://www.besi.com/investor-relations/press-releases/2025/details-1/be-semiconductor-industries-nv-announces-q2-26-and-h1-26-results/).

Thermocompression bonders, which press memory dies into a stack and place chiplets on substrates, are the most concentrated niche. ASMPT took a repeat order for fifteen chip-to-substrate bonders in December 2025 [16](https://www.asmpt.com/en/investor-relations/news-events/asmpt-secures-additional-orders-for-fifteen-chip-to-substrate-thermo-compression-bonding-tools-driven-by-ai-tailwind/) and, in its 2025 results, put that market at $1.6 billion by 2028, of which it means to hold 35 to 40 percent [17](https://www.asmpt.com/en/investor-relations/news-events/asmpt-announces-2025-annual-results/). See [[#^memory-and-hbm]].

### The back end's geography ^the-back-ends-geography

Outsourced assembly and test, the OSAT business, is Taiwanese with a large Chinese challenger. ASE, the biggest, billed $20.6 billion in 2025 [18](https://data.sec.gov/api/xbrl/companyconcept/CIK0001122411/ifrs-full/Revenue.json); Georgetown's CSET counts four of the top ten OSATs by 2024 revenue as China-headquartered [19](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/). Malaysia ships about 13 percent of the world's packaged chips and wants 7 percent of advanced packaging shipments by 2035 [20](https://www.mida.gov.my/advanced-packaging-how-malaysia-is-packaging-the-future-of-ai/).

ASE spent $2.7 billion on machinery and $1.4 billion on buildings in the first half of 2026, and says revenue from leading-edge advanced packaging is running ahead of its $3.5 billion guidance for the year [21](https://www.sec.gov/Archives/edgar/data/1122411/000095010326011353/dp250875_6k.htm). Powertech aims to run the first panel-level packaging line for AI chips in 2027 [22](https://asia.nikkei.com/business/tech/semiconductors/powertech-eyes-world-s-first-panel-level-packaging-for-ai-chips-in-2027).

Amkor took $6.71 billion of revenue in 2025 [23](https://data.sec.gov/api/xbrl/companyconcept/CIK0001047127/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json), and $1.90 billion in the second quarter of 2026 alone, up 26 percent year on year [24](https://www.sec.gov/Archives/edgar/data/1047127/000104712726000043/amkr6302026erex-991.htm). It has expanded its Arizona campus to a $7 billion investment [25](https://ir.amkor.com/news-releases/news-release-details/amkor-technology-breaks-ground-new-semiconductor-advanced). Under a partnership signed in June 2026 [26](https://ir.amkor.com/news-releases/news-release-details/tsmc-and-amkor-technology-announce-long-term-partnership) it will run packaging and test there for TSMC, whose Phoenix fabs sit next door [27](https://pr.tsmc.com/english/news/3174).

Testers installed at ASE, the largest assembly and test contractortesters

Q2 2025 6,797 Q1 2026 7,585 Q2 2026 8,348

Source: [ASE Technology Holding, second quarter 2026 earnings release (SEC Form 6-K)](https://www.sec.gov/Archives/edgar/data/1122411/000095010326011351/dp250868_6k.htm)

### The chokepoint ^the-chokepoint-13

Unlike lithography, no test or assembly tool has a single supplier. Advantest argues that switching tester vendor means rebuilding the whole development, evaluation and production test environment, which is why share moves slowly [1](https://www.advantest.com/document/en/investors/ir-library/investors-guide/Investors_Guide_2504E.pdf).

Assembly and test is also the part of the chain where China is strongest, because assembly, dicing, bonding and test tools are not covered by the export controls on lithography and deposition. ASE and Amkor billed $27.3 billion between them in 2025, against industry sales of $791.7 billion [28](https://www.semiconductors.org/global-annual-semiconductor-sales-increase-25-6-to-791-7-billion-in-2025/), a small share of the money for a step every chip has to pass through.

### Key evaluation criteria ^key-evaluation-criteria-13

-   **Test coverage** is the share of hidden failures caught before they reach a package that cannot be taken apart.
-   **Test time per part** sets throughput and cost, and large dies, memory stacks and chiplets all push it up.
-   **Probe card flatness and life** decide what wafer sort costs. Every needle must stay in the same plane across a full die and hold that over a long life.
-   **Thermal control** matters more every generation. A kilowatt-class accelerator has to be held at temperature in the socket while it is tested at speed.
-   **Capacity and geography** are the practical constraint. Taiwan, China and Malaysia hold most of the floor space, and new capacity takes years.

Card 1 of 3Question

Why do chipmakers now test chips earlier and more often?

Card 1 of 3Answer

One bad chip can ruin a package that holds a dozen expensive ones.

Testing makes a weak chip fail before it is built into a finished product. [[#^how-it-works-13|Reread: How it works]]

Card 2 of 3Question

Who makes most chip testers?

Card 2 of 3Answer

Advantest of Japan and Teradyne of the United States.

Together they hold about 80 percent of the market. Advantest alone holds about 65 percent. [[#^who-makes-it-13|Reread: Who makes it]]

Card 3 of 3Question

Where does China stand in assembly and test?

Card 3 of 3Answer

It is China's strongest stage in the chain.

Four of the top ten assembly and test firms are Chinese, and their tools face far lighter export controls than lithography tools. [[#^the-back-ends-geography|Reread: The back end's geography]]

#### Three things to remember ^three-things-to-remember

-   Chips are tested early and often because one bad chip can ruin a package of expensive ones.
-   Advantest and Teradyne make about 80 percent of chip testers.
-   Assembly and test is China's strongest stage, with four of the top ten firms.

Sources (28)

1.  A [Investors Guide April 25, 2025](https://www.advantest.com/document/en/investors/ir-library/investors-guide/Investors_Guide_2504E.pdf) Advantest · 13 May 2025
2.  A [Aehr Receives $22 Million Follow-On Order for AI Processor Wafer-Level Burn-In Systems](https://www.aehr.com/2026/08/aehr-receives-22-million-follow-on-order-for-ai-processor-wafer-level-burn-in-systems/) Aehr Test Systems · 12 August 2026
3.  A [Aehr Test Systems Reports Fiscal 2026 Fourth Quarter and Full Year Financial Results with Record Quarterly Bookings and $100 Million Effective Backlog](https://www.aehr.com/2026/07/aehr-test-systems-reports-fiscal-2026-fourth-quarter-and-full-year-financial-results-with-record-quarterly-bookings-and-100-million-effective-backlog/) Aehr Test Systems · 14 July 2026
4.  A [FORMFACTOR INC, Form 10-K annual report for the period ended 2025-12-27 (10-K)](https://www.sec.gov/Archives/edgar/data/1039399/000103939926000009/form-20251227.htm) U.S. Securities and Exchange Commission (filing by FORMFACTOR INC) · 20 February 2026
5.  A [Q2 2026 Taiwan Semiconductor Manufacturing Co Ltd Earnings Call (Chinese, English) — edited transcript](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2026-08/3e494f0c14dd0890f897aa044415e21d93486cc4/TSMC%202Q26%20Transcript.pdf) LSEG StreetEvents (transcript of a TSMC earnings call), via TSMC · 16 July 2026
6.  A [ASE Technology Holding Co., Ltd., Form 6-K report of foreign private issuer for the period ended 2026-07-30](https://www.sec.gov/Archives/edgar/data/1122411/000095010326011351/dp250868_6k.htm) U.S. Securities and Exchange Commission (filing by ASE Technology Holding Co., Ltd.) · 30 July 2026
7.  A [Advantest, presentation notes for the FY2025 (year ended 31 March 2026) results briefing, 27 April 2026](https://www.advantest.com/document/en/investors/ir-library/result/JE_BIZ_260427_note.pdf) Advantest · 27 April 2026
8.  A [Teradyne Reports Fourth Quarter and Full Year 2025 Results](https://investors.teradyne.com/news-events/press-releases/detail/433/teradyne-reports-fourth-quarter-and-full-year-2025-results) Teradyne · 2 February 2026
9.  A [Revenue from Contract with Customer, Excluding Assessed Tax (us-gaap:RevenueFromContractWithCustomerExcludingAssessedTax) reported by FormFactor, Inc., XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0001039399/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json) U.S. Securities and Exchange Commission (XBRL data for FormFactor, Inc.)
10.  A [Technoprobe, press release: the Board of Directors approves the draft statutory and consolidated annual report as at 31 December 2025](https://technoprobe.com/wp-content/uploads/2026/03/PR-FY-2025_.pdf) Technoprobe · 18 March 2026
11.  A [Revenue from Contract with Customer, Including Assessed Tax (us-gaap:RevenueFromContractWithCustomerIncludingAssessedTax) reported by COHU, INC., XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0000021535/us-gaap/RevenueFromContractWithCustomerIncludingAssessedTax.json) U.S. Securities and Exchange Commission (XBRL data for COHU, INC.)
12.  B [DISCO Corporation, The World Leader In Semiconductor Capital Equipment For Cutting, Grinding, Polishing](https://newsletter.semianalysis.com/p/disco-corporation-the-world-leader) SemiAnalysis · 19 July 2022
13.  A [DISCO develops the DFD6080 fully automatic dicing saw for work sizes up to 400 mm square (最大400mm角のパッケージ切断に対応したダイシングソー「DFD6080」を開発)](https://www.disco.co.jp/eg/news/corp/20251215_1.html) DISCO Corporation · 15 December 2025
14.  A [Revenues (us-gaap:Revenues) reported by KULICKE AND SOFFA INDUSTRIES, INC., XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0000056978/us-gaap/Revenues.json) U.S. Securities and Exchange Commission (XBRL data for KULICKE AND SOFFA INDUSTRIES, INC.)
15.  A [BE Semiconductor Industries N.V. Announces Q2-26 and H1-26 Results](https://www.besi.com/investor-relations/press-releases/2025/details-1/be-semiconductor-industries-nv-announces-q2-26-and-h1-26-results/) BE Semiconductor Industries (Besi) · 23 July 2026
16.  A [ASMPT Secures Additional Orders for Fifteen Chip-to-Substrate Thermo-Compression Bonding Tools Driven by AI Tailwind](https://www.asmpt.com/en/investor-relations/news-events/asmpt-secures-additional-orders-for-fifteen-chip-to-substrate-thermo-compression-bonding-tools-driven-by-ai-tailwind/) ASMPT · 22 December 2025
17.  A [ASMPT Announces 2025 Annual Results AI-Driven Structural Growth Underpins Group Performance](https://www.asmpt.com/en/investor-relations/news-events/asmpt-announces-2025-annual-results/) ASMPT · 4 March 2026
18.  A [Revenue (ifrs-full:Revenue) reported by ASE Technology Holding Co., Ltd., XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0001122411/ifrs-full/Revenue.json) U.S. Securities and Exchange Commission (XBRL data for ASE Technology Holding Co., Ltd.)
19.  A [Inside Beijing’s Chipmaking Offensive](https://cset.georgetown.edu/article/inside-beijings-chipmaking-offensive/) Center for Security and Emerging Technology (CSET) · 14 July 2025
20.  A [Advanced Packaging: How Malaysia is Packaging the Future of AI](https://www.mida.gov.my/advanced-packaging-how-malaysia-is-packaging-the-future-of-ai/) Malaysian Investment Development Authority · 1 July 2026
21.  A [ASE Technology Holding Co., Ltd., Form 6-K report of foreign private issuer for the period ended 2026-07-30](https://www.sec.gov/Archives/edgar/data/1122411/000095010326011353/dp250875_6k.htm) U.S. Securities and Exchange Commission (filing by ASE Technology Holding Co., Ltd.) · 30 July 2026
22.  B [Powertech eyes world's first panel-level packaging for AI chips in 2027](https://asia.nikkei.com/business/tech/semiconductors/powertech-eyes-world-s-first-panel-level-packaging-for-ai-chips-in-2027) Nikkei Asia · 27 August 2026
23.  A [Revenue from Contract with Customer, Excluding Assessed Tax (us-gaap:RevenueFromContractWithCustomerExcludingAssessedTax) reported by AMKOR TECHNOLOGY, INC., XBRL company concept data](https://data.sec.gov/api/xbrl/companyconcept/CIK0001047127/us-gaap/RevenueFromContractWithCustomerExcludingAssessedTax.json) U.S. Securities and Exchange Commission (XBRL data for AMKOR TECHNOLOGY, INC.)
24.  A [AMKOR TECHNOLOGY, INC., Form 8-K current report for the period ended 2026-07-27 (8-K)](https://www.sec.gov/Archives/edgar/data/1047127/000104712726000043/amkr6302026erex-991.htm) U.S. Securities and Exchange Commission (filing by AMKOR TECHNOLOGY, INC.) · 27 July 2026
25.  A [Amkor Technology Breaks Ground on New Semiconductor Advanced Packaging and Test Campus in Arizona; Expands Investment to $7 Billion](https://ir.amkor.com/news-releases/news-release-details/amkor-technology-breaks-ground-new-semiconductor-advanced) Amkor Technology
26.  A [TSMC and Amkor Technology Announce Long Term Partnership to Accelerate Advanced Packaging in the United States](https://ir.amkor.com/news-releases/news-release-details/tsmc-and-amkor-technology-announce-long-term-partnership) Amkor Technology
27.  A [Amkor and TSMC to Expand Partnership and Collaborate on Advanced Packaging in Arizona](https://pr.tsmc.com/english/news/3174) TSMC · 4 October 2024
28.  A [Global Annual Semiconductor Sales Increase 25.6% to $791.7 Billion in 2025 - Semiconductor Industry Association](https://www.semiconductors.org/global-annual-semiconductor-sales-increase-25-6-to-791-7-billion-in-2025/) Semiconductor Industry Association · 6 February 2026

## Systems and Networking ^systems-and-networking

A finished package is useless until it is bolted to a baseboard, fed a thousand amps and wired to seventy-one other packages. Many firms can do the assembly; few can make the lasers for the optical links.

1,325 words / 6 minSpecimen: GPU baseboard

In plain terms

One AI chip is not enough to train a model. So seventy-two of them are wired together in a rack, a cabinet the size of a wardrobe, and run as one computer. Each chip sits on its own board and draws more than a thousand amps, several times the current a whole house is wired to carry. The chips have to swap results with each other all the time, and a copper wire can carry those signals only a few meters before they fade, so the longer links send them as light down glass fiber. Many companies can build the rack. Only a few can make the lasers that send the light, and that is the narrow point.

### In short ^in-short-14

At the rack, the hard parts are power and light. Assembly is competitive and can move countries in a year. The control points are NVLink-class scale-up switching, which one firm still owns [3](https://www.nvidia.com/en-us/data-center/nvlink/), and indium phosphide lasers, where Nvidia paid $4 billion for capacity it could not order [17](https://nvidianews.nvidia.com/news/nvidia-announces-strategic-partnership-with-lumentum-to-develop-state-of-the-art-optics-technology) and 70 percent of the feedstock is Chinese [16](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-indium.pdf).

Concentration **High**

Substitutability **Moderate** Rated on the two most concentrated parts: Nvidia alone sells NVLink, the link that joins the accelerators in a rack, and few firms make the lasers for the optical links.

Price or market size **Nvidia put $2B each into Coherent and Lumentum in March 2026 to buy indium phosphide laser capacity**

Who leads

-   USNvidia NVLink and NVSwitch for links inside a rack; InfiniBand and Spectrum-X Ethernet between racks
-   USBroadcom Switch chips sold to any buyer (Tomahawk, Jericho) and most custom AI accelerators
-   TWFoxconn Largest AI rack assembler; builds in Taiwan, Mexico, Texas
-   CNInnoLight High-speed optical modules; plants in Suzhou, Taiwan and Thailand
-   USCoherent Indium phosphide lasers and data center transceivers

Where it is made

-   USUnited States Switch and accelerator silicon, indium phosphide lasers, system design
-   TWTaiwan Contract design and rack assembly; high-layer-count circuit boards
-   CNChina Optical module assembly and test; most of the world's indium
-   THThailand Chinese module makers' offshore transceiver plants
-   MXMexico Rack integration for the North American market

Why substitution is possible

Rack assembly is easy to replace: if Foxconn stopped, Quanta and Wistron would take over the volume within a few quarters. The two concentrated parts are inside the rack, and a fix is under way for each. UALink is a published rival to NVLink, running 200 Gb/s per lane and joining up to 1,024 accelerators. For the lasers, Nvidia put $2 billion each into Coherent and Lumentum to secure supply that an ordinary order could not. Any newcomer with money would have to do the same, over two to five years.

Where China stands

China holds two parts of the optical link that the United States does not. Chinese firms assemble the high-speed optical modules in volume, mostly in plants in Thailand and Suzhou. China also produces about 70 percent of the world's indium, the raw material for the lasers inside those modules.

Where the US stands

American firms make the switch chips, the links that join accelerators inside a rack, and the lasers, but do almost none of the rack assembly. Nvidia's partners began building racks in Houston and Dallas in 2025. In July 2026 the Federal Communications Commission barred new approvals for imported equipment containing parts from firms on its Covered List.

A package computes nothing until it is built into a machine, and building the machine is a separate industry from making the package.

### How it works ^how-it-works-14

![](https://chipsupplychain.org/media/racks-light-end.jpg)

How AI chips are wired together

An accelerator ships as a module, the chip on a small board with its power supply and memory stacks. Nvidia calls its version SXM, and the open-standards equivalent is the Open Compute Project's accelerator module. Eight bolt onto a baseboard that carries their power and the switch chips, which pass data between any two modules at full speed.

Rack-scale systems drop the baseboard. An Nvidia GB300 NVL72 holds 18 compute trays plus nine switch trays, 72 GPUs in all, and draws up to 142 kW, more than ten times a conventional enterprise rack [1](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html); Rubin keeps that shape [2](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin). Inside the rack the trays reach each other over copper. Beyond it, every link runs on glass fiber with an optical transceiver at each end, where a laser turns the electrical signal into pulses of light and a detector at the far end turns the pulses back into current.

Every AI cluster runs two networks that are not interchangeable. Scale-up binds a few dozen accelerators tightly enough that they can read each other's memory, at terabytes per second; scale-out joins thousands of those groups at hundreds of gigabits per second. A byte is eight bits, so the inner network is tens of times faster than the outer one. A model too big for one accelerator gets split across the scale-up group, so that group's bandwidth sets the size of model that can be trained.

### Variants and trade-offs ^variants-and-trade-offs-14

#### Scale-up: NVLink, UALink and Google's torus ^scale-up-nvlink-ualink-and

The designs differ in how many accelerators can share one pool of memory.

-   **NVLink and NVSwitch.** Nvidia's per-GPU bandwidth went from 900 GB/s in NVLink 4 to 1,800 in NVLink 5 and 3,600 in NVLink 6; the rack's own network moves 130 TB/s on Blackwell and 260 TB/s on Rubin [3](https://www.nvidia.com/en-us/data-center/nvlink/).
-   **UALink.** The open answer runs 200 Gb/s per lane, four lanes to a station for 800 Gb/s, and can address up to 1,024 endpoints in one group [4](https://ualinkconsortium.org/blog/ualink-200g-1-0-specification-overview-802/).
-   **Google's 3D torus.** Ironwood, the seventh generation of Google's own TPU accelerator, wires 64 chips to a rack and uses optical switches to join cubes into superpods of 9,216 chips, trading latency for the ability to route around a failed rack in software [5](https://cloud.google.com/blog/products/compute/inside-the-ironwood-tpu-codesigned-ai-stack).

NVLink bandwidth per GPU by generationGB/s

NVLink 4 (Hopper) 900 NVLink 5 (Blackwell) 1,800 NVLink 6 (Rubin) 3,600

Source: [NVIDIA NVLink product page, 2026](https://www.nvidia.com/en-us/data-center/nvlink/)

#### Scale-out: InfiniBand versus Ethernet ^scale-out-infiniband-versus-ethernet

InfiniBand, the specialized network built for supercomputers, carried nearly all scale-out traffic when AI clusters were small and alike. Ethernet overtook it on raw capacity first: Broadcom doubled the bandwidth of the switch chips it sells to all comers every generation, from 25.6 Tbps on one chip in Tomahawk 4 [6](https://www.broadcom.com/company/news/product-releases/52756) to 51.2 in Tomahawk 5 [7](https://investors.broadcom.com/news-releases/news-release-details/broadcom-ships-tomahawk-5-industrys-highest-bandwidth-switch) and 102.4 in Tomahawk 6 [8](https://www.broadcom.com/company/news/product-releases/64031). Then the Ultra Ethernet Consortium published its 1.0 specification in June 2025, standardizing the load balancing, congestion control and lossless behavior InfiniBand had from the start [9](https://ultraethernet.org/ultra-ethernet-consortium-uec-launches-specification-1-0-transforming-ethernet-for-ai-and-hpc-at-scale/).

Broadcom Tomahawk switching capacity on one chipTbps

Tomahawk 4 25.6 Tomahawk 5 51.2 Tomahawk 6 102.4

Source: [Broadcom product releases for Tomahawk 4, 5 and 6](https://www.broadcom.com/company/news/product-releases/64031)

Nvidia sells both networks, telling investors that a $75.2 billion data center quarter came from Blackwell 300 plus demand for "InfiniBand, Spectrum-X Ethernet, and NVLink" [10](https://www.sec.gov/Archives/edgar/data/1045810/000104581026000052/nvda-20260426.htm), because large buyers run both networks.

#### Optics: pluggable, then co-packaged ^optics-pluggable-then-co-packaged

Every link longer than a few meters is optical, and a cluster needs several transceivers, the modules that turn electricity into light and back, for each accelerator. Their power cost is why both switch vendors are moving the optics onto the switch package itself: Broadcom's Tomahawk 6 Davisson cuts optical interconnect power by about 70 percent, more than 3.5 times better than [11](https://www.broadcom.com/company/news/product-releases/63626) plug-in modules , and Nvidia's Spectrum-X Photonics reaches 512 ports of 800 gigabits during 2026 using four times fewer lasers [12](https://nvidianews.nvidia.com/news/nvidia-spectrum-x-co-packaged-optics-networking-switches-ai-factories).

### Who makes it ^who-makes-it-14

Optical modules are assembled where labor and land are cheap, and the Chinese makers went offshore early. InnoLight has run a Thai plant since 2019 alongside Suzhou and Taiwan [13](https://www.innolight.com/about), and Eoptolink assembles in Rayong and Chonburi [14](https://www.eoptolink.com/about-us/contacts). The American rules now follow the firm, wherever its plants sit: the Federal Communications Commission's July 2026 order bars new authorizations for devices that contain logic chips from firms on its Covered List, and the record for that rule names optical transceivers as one such component [15](https://docs.fcc.gov/public/attachments/FCC-26-50A1.pdf).

The lasers inside those modules come from far fewer firms. Indium phosphide is the only practical material for the lasers in 800-gigabit and 1.6-terabit optics, and its feedstock is concentrated: China accounts for about 70 percent of world indium production [16](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-indium.pdf). Nvidia put $2 billion into Lumentum and $2 billion into Coherent in March 2026, buying research, future capacity and access rights [17](https://nvidianews.nvidia.com/news/nvidia-announces-strategic-partnership-with-lumentum-to-develop-state-of-the-art-optics-technology) [18](https://nvidianews.nvidia.com/news/nvidia-and-coherent-announce-strategic-partnership-to-develop-optics-technology-to-scale-next-generation-data-center-architecture).

Custom accelerator and switch silicon is a US duopoly. Broadcom sells the Ethernet switch chips other firms build their switches around, and designs most of the custom accelerators, including Google's TPUs and Meta's own; its AI semiconductor revenue reached $16.7 billion in the third quarter of fiscal 2026, up 221 percent [19](https://www.sec.gov/Archives/edgar/data/1730168/000173016826000076/avgo-08022026x8kxex99.htm). The other custom-silicon designer is Marvell, whose five-year agreement with AWS, announced in December 2024, covers custom AI chips alongside the optical and networking parts that go with them [20](https://www.sec.gov/Archives/edgar/data/1835632/000183563224000193/final2024_12x02xmarvell-.htm).

Physical assembly is done by Taiwanese firms. Foxconn booked NT$8.1 trillion of revenue in 2025, up 18 percent, with cloud and networking among the drivers [21](https://www.honhai.com/en-us/press-center/press-releases/latest-news/1978). Assembly is moving closer to the customer: Nvidia's partners commissioned more than a million square feet of US manufacturing space in 2025, Foxconn in Houston and Wistron in Dallas [22](https://blogs.nvidia.com/blog/nvidia-manufacture-american-made-ai-supercomputers-us/).

### The chokepoint ^the-chokepoint-14

Several capable ODMs on three continents screw racks together, and the power {--{"author":"James's AI","timestamp":1790593589395}@@supplies,--}{++{"author":"James's AI","timestamp":1790593589395}@@supplier busbars,++} cables and connectors have many suppliers. If Foxconn stopped tomorrow, Quanta and Wistron would absorb the volume in a couple of quarters.

The parts that cannot be replaced that fast are the components that go into the rack.

-   **Indium phosphide laser capacity.** The shortage is in material and fab space: Nvidia's answer was to buy into two laser makers [18](https://nvidianews.nvidia.com/news/nvidia-and-coherent-announce-strategic-partnership-to-develop-optics-technology-to-scale-next-generation-data-center-architecture), and the indium those lasers need is 70 percent Chinese [16](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-indium.pdf).
-   **NVSwitch.** Nobody else sells a scale-up switch of NVLink's bandwidth to all comers, which is what UALink exists to change [4](https://ualinkconsortium.org/blog/ualink-200g-1-0-specification-overview-802/).
-   **High-layer-count {++{"author":"James's AI","timestamp":1790593591656}@@circuit ++}boards.** The boards, and the {++{"author":"James's AI","timestamp":1790593591656}@@low-loss ++}laminate they are built from, are concentrated in Taiwan and Japan; see [[#^substrates-and-pcbs]].

Optical module assembly is a separate case: concentrated, but not technically hard. Where the modules get built follows cost and policy, and it can change in a year or two.

### Key evaluation criteria ^key-evaluation-criteria-14

-   **Scale-up domain size** is how many accelerators share one pool of memory: up to 1,024 endpoints in the UALink spec [4](https://ualinkconsortium.org/blog/ualink-200g-1-0-specification-overview-802/) and 9,216 for an Ironwood superpod [5](https://cloud.google.com/blog/products/compute/inside-the-ironwood-tpu-codesigned-ai-stack).
-   **Bandwidth per accelerator** limits how far one model can be split across chips. NVLink 6 is 3,600 GB/s [3](https://www.nvidia.com/en-us/data-center/nvlink/).
-   **Picojoules per bit** is the energy cost of moving data. Optics dominate network power at 800 gigabits and above, and co-packaging is more than 3.5 times better than plug-in modules [11](https://www.broadcom.com/company/news/product-releases/63626).
-   **Serviceability** falls with co-packaged optics, which trade field-replaceable modules for a switch that goes back whole when a channel fails.
-   **Supply** concentration is in the components: many firms assemble the modules; far fewer can make the lasers inside them.

Card 1 of 4Question

What is an AI rack?

Card 1 of 4Answer

A cabinet of 72 AI chips wired together to run as one computer.

The chips swap results with each other constantly. [[#^how-it-works-14|Reread: How it works]]

Card 2 of 4Question

Why do the longer links between AI chips carry signals as light?

Card 2 of 4Answer

Copper carries the signals only a few meters before they fade.

A laser turns the signal into pulses of light that travel down glass fiber. [[#^how-it-works-14|Reread: How it works]]

Card 3 of 4Question

Which parts of an AI rack are hardest to replace?

Card 3 of 4Answer

Nvidia's NVLink switching and the lasers for the optical links.

Rack assembly is easy to move. If Foxconn stopped, Quanta and Wistron could take over within a few quarters. [[#^the-chokepoint-14|Reread: The chokepoint]]

Card 4 of 4Question

What does China control in the optical links?

Card 4 of 4Answer

About 70 percent of the world's indium, the raw material for the lasers.

Chinese firms also assemble high-speed optical modules in volume. [[#^the-chokepoint-14|Reread: The chokepoint]]

#### Four things to remember ^four-things-to-remember-12

-   An AI rack wires 72 chips together to run as one computer.
-   Longer links carry signals as light, because copper fades after a few meters.
-   NVLink switching and the lasers are the hard parts, and rack assembly is easy to move.
-   China produces about 70 percent of the world's indium, the raw material for the lasers.

Sources (22)

1.  A [System Hardware & Components](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html) Nvidia
2.  A [NVIDIA, Partners Drive Next-Gen Efficient Gigawatt AI Factories in Buildup for Vera Rubin](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin) Nvidia · 13 October 2025
3.  A [NVLink & NVLink Switch for Advanced Multi-GPU Communication](https://www.nvidia.com/en-us/data-center/nvlink/) Nvidia · 20 April 2026
4.  A [UALink™ 200G 1.0 Specification Overview](https://ualinkconsortium.org/blog/ualink-200g-1-0-specification-overview-802/) UALink Consortium
5.  A [Inside the Ironwood TPU codesigned AI stack](https://cloud.google.com/blog/products/compute/inside-the-ironwood-tpu-codesigned-ai-stack) Google Cloud · 6 November 2025
6.  A [Broadcom Ships Tomahawk 4, Industry’s Highest Bandwidth Ethernet Switch Chip at 25.6 Terabits per Second](https://www.broadcom.com/company/news/product-releases/52756) Broadcom
7.  A [Broadcom Ships Tomahawk 5, Industry's Highest Bandwidth Switch Chip to Accelerate AI/ML Workloads](https://investors.broadcom.com/news-releases/news-release-details/broadcom-ships-tomahawk-5-industrys-highest-bandwidth-switch) Broadcom
8.  A [Broadcom Now Shipping World’s First 102.4 Tbps Switch in Production Volume](https://www.broadcom.com/company/news/product-releases/64031) Broadcom
9.  A [Ultra Ethernet Consortium (UEC) Launches Specification 1.0 Transforming Ethernet for AI and HPC at Scale - Ultra Ethernet Consortium](https://ultraethernet.org/ultra-ethernet-consortium-uec-launches-specification-1-0-transforming-ethernet-for-ai-and-hpc-at-scale/) Ultra Ethernet Consortium · 11 June 2025
10.  A [NVIDIA CORP, Form 10-Q quarterly report for the period ended 2026-04-26 (10-Q)](https://www.sec.gov/Archives/edgar/data/1045810/000104581026000052/nvda-20260426.htm) U.S. Securities and Exchange Commission (filing by NVIDIA CORP) · 20 May 2026
11.  A [Broadcom Announces Tomahawk® 6 – Davisson, the Industry’s First 102.4-Tbps Ethernet Switch with Co-Packaged Optics](https://www.broadcom.com/company/news/product-releases/63626) Broadcom
12.  A [NVIDIA Announces Spectrum-X Photonics, Co-Packaged Optics Networking Switches to Scale AI Factories to Millions of GPUs](https://nvidianews.nvidia.com/news/nvidia-spectrum-x-co-packaged-optics-networking-switches-ai-factories) Nvidia · 18 March 2025
13.  A [InnoLight Technology, company overview page](https://www.innolight.com/about) InnoLight Technology
14.  A [Eoptolink Technology, contacts page](https://www.eoptolink.com/about-us/contacts) Eoptolink Technology
15.  A [Federal Communications Commission FCC-26-50](https://docs.fcc.gov/public/attachments/FCC-26-50A1.pdf) U.S. Federal Communications Commission
16.  A [Mineral Commodity Summaries 2026](https://pubs.usgs.gov/periodicals/mcs2026/mcs2026-indium.pdf) U.S. Geological Survey · 5 February 2026
17.  A [NVIDIA Announces Strategic Partnership With Lumentum to Develop State-of-the-Art Optics Technology](https://nvidianews.nvidia.com/news/nvidia-announces-strategic-partnership-with-lumentum-to-develop-state-of-the-art-optics-technology) Nvidia · 2 March 2026
18.  A [NVIDIA and Coherent Announce Strategic Partnership to Develop Optics Technology to Scale Next-Generation Data Center Architecture](https://nvidianews.nvidia.com/news/nvidia-and-coherent-announce-strategic-partnership-to-develop-optics-technology-to-scale-next-generation-data-center-architecture) Nvidia · 2 March 2026
19.  A [Broadcom Inc., Form 8-K current report for the period ended 2026-09-02 (8-K)](https://www.sec.gov/Archives/edgar/data/1730168/000173016826000076/avgo-08022026x8kxex99.htm) U.S. Securities and Exchange Commission (filing by Broadcom Inc.) · 2 September 2026
20.  A [Marvell Technology, Inc., Form 8-K current report for the period ended 2024-12-02 (8-K)](https://www.sec.gov/Archives/edgar/data/1835632/000183563224000193/final2024_12x02xmarvell-.htm) U.S. Securities and Exchange Commission (filing by Marvell Technology, Inc.) · 2 December 2024
21.  A [Hon Hai Technology Group (Foxconn) Announces FY2025 & 4Q25 Financial Results - Hon Hai Technology Group](https://www.honhai.com/en-us/press-center/press-releases/latest-news/1978) Hon Hai Precision Industry (Foxconn) · 16 March 2026
22.  A [NVIDIA to Manufacture American-Made AI Supercomputers in US for First Time](https://blogs.nvidia.com/blog/nvidia-manufacture-american-made-ai-supercomputers-us/) Nvidia · 14 April 2025

## Data Centers and Power ^data-centers-and-power

The chips are no longer the slowest part of a data center buildout. A large transformer takes three years, turbine output does not reach 30 GW a year until 2030, and Texas has fifty times more large loads, mostly data centers, waiting to connect than it has approved to switch on.

1,334 words / 6 minSpecimen: server rack

In plain terms

A data center's job is to feed electricity to the machines inside it and carry away the heat they give off. One rack of AI chips, a cabinet the size of a wardrobe, draws 142 kilowatts, and every watt of it comes back out as heat, more than air can carry away, so water is piped through the rack instead. A large training site already holds a hundred thousand chips, and the newest sites are planned in gigawatts. One gigawatt is the whole output of a large power station, and OpenAI's planned sites add up to more than nine of them by 2029. Getting that much electricity to the door is harder than putting up the building, because the transformers and heavy switches that connect a site to the grid, and the turbines that make the power, come from a few suppliers and take years to arrive.

### In short ^in-short-15

The rack became the unit of AI compute at 142 kW and is heading for a megawatt by 2027 [4](https://developer.nvidia.com/blog/nvidia-800-v-hvdc-architecture-will-power-the-next-generation-of-ai-factories/), which forces liquid cooling and an 800-volt bus on every large operator [3](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin). Nine vendors sell the cooling equipment, so buying it is a question of price [3](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin). The power equipment comes with queues: transformers take three years [1](https://www.energy.gov/sites/default/files/2024-10/EXEC-2022-001242%20-%20Large%20Power%20Transformer%20Resilience%20Report%20signed%20by%20Secretary%20Granholm%20on%207-10-24.pdf), six years of turbine output is already booked [9](https://www.sec.gov/Archives/edgar/data/1996810/000199681026000147/gevpressrelease2q26.htm), and Texas has fifty times more large load in the queue than it has approved to switch on [13](https://www.ercot.com/files/docs/2026/07/29/ERCOT-Senate-July-29-Panel-1-Assessing-The-Grid.pdf). When an AI buildout slips, the delay is usually in the substation yard.

Concentration **High**

Substitutability **Moderate** Several approved vendors sell every piece of power and cooling equipment, but a transformer takes three years to arrive and GE Vernova's gas turbines have orders for about six years ahead.

Price or market size **Transformer lead times of 36 months, against under a year before 2020** GE Vernova's gas backlog and reserved slots grew from 100 GW to 116 GW in 2026

Who leads

-   USGE Vernova 116 GW of gas equipment backlog and reserved factory slots at mid-2026
-   CHHitachi Energy Large power transformers and high-voltage switchgear
-   DESiemens Energy Grid technologies, transformers, turbines
-   USVertiv Data center power and cooling systems; NVIDIA gigawatt AI factory partner
-   FRSchneider Electric Electrical distribution and cooling; partner in NVIDIA's 800-volt DC designs

Where it is made

-   USUnited States Most new AI capacity; ERCOT and PJM carry the load growth
-   CHSwitzerland Hitachi Energy and ABB transformer and switchgear engineering
-   DEGermany Siemens Energy grid technologies and turbines
-   TWTaiwan Delta Electronics power shelves, busbars and thermal modules
-   JPJapan Hitachi group transformer manufacturing

Why substitution is possible

Nothing in a data center's power and cooling has to be invented. Nine firms sell the power and cooling equipment for Nvidia's gigawatt data center designs, so a buyer can get the equipment and negotiate the price. Money cannot shorten the wait. A large power transformer now takes 36 months to arrive, against under a year before 2020. GE Vernova has close to six years of gas turbine orders waiting. New capacity is therefore two to five years away.

Where China stands

China has spare generating capacity, a large domestic industry making transformers and switchgear, and can connect new sites quickly. Its AI buildout is limited by the supply of accelerators, and it has power to spare.

Where the US stands

The United States has the demand and the money but cannot shorten the wait for equipment. Transformers and turbines both take years to arrive. Most large power transformers are imported, and no restarted nuclear reactor is running yet.

For thirty years the semiconductor industry set the pace and everything downstream followed. A wafer clears a leading-edge fab in months; a large power transformer takes three years, and before 2020 the same order took under one [1](https://www.energy.gov/sites/default/files/2024-10/EXEC-2022-001242%20-%20Large%20Power%20Transformer%20Resilience%20Report%20signed%20by%20Secretary%20Granholm%20on%207-10-24.pdf).

### How it works ^how-it-works-15

A rack is now the unit of AI compute. A GB300 NVL72 draws up to 142 kW through eight 33 kW power shelves, the rack's own power supplies, more than ten times a conventional enterprise rack in the same floor area [2](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html).

Between the grid and the rack, a substation steps the high voltage down with transformers. Switchgear, the building's heavy circuit breakers, can cut any part of the site off in a fault. Battery-backed supplies hold the load for the seconds it takes backup generators to start. Distribution boards split the feed among the rows of racks. At the back of each rack a busbar, a solid copper bar doing a job a cable would melt at, carries the current down to the trays. Every one of those is heavy equipment with its own lead time.

Heat leaves in water. Cold plates on the GPU packages pass it to a building loop that releases it outdoors, and Nvidia's Vera Rubin racks run 45 °C supply water, warm enough that many sites can skip chillers [3](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin).

Nvidia is also moving rack distribution to 800 volts of direct current. Raising the voltage cuts the current for the same power, and heat in copper comes from current, so the same conductor carries over 150 percent more power and the 200 kg busbars feeding a single rack are no longer needed [3](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin).

### Variants and trade-offs ^variants-and-trade-offs-15

#### Cooling ^cooling

-   **Air.** Heat exchangers in the rack door work at moderate densities but cannot carry away the heat of an AI rack.
-   **Direct-to-chip liquid.** The default for anything Blackwell-class or later; every new AI hall is now plumbed for it.
-   **Immersion.** Higher density still, but hard to service and barely used at scale.

Cooling is not the bottleneck. Nvidia names nine firms supplying data center power and cooling systems for its gigawatt reference designs, among them ABB, Eaton, Hitachi Energy, Mitsubishi Electric, Schneider Electric, Siemens and Vertiv [3](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin).

#### Rack power ^rack-power

Nvidia's 800-volt DC architecture is drawn for racks from 100 kW to more than a megawatt, with megawatt racks from 2027, because the 54-volt distribution in today's racks hits physical limits past about 200 kW [4](https://developer.nvidia.com/blog/nvidia-800-v-hvdc-architecture-will-power-the-next-generation-of-ai-factories/).

A megawatt rack changes the busbar, the floor loading, the coolant flow, the leak detection and the stored energy that carries the rack through a dip. Nvidia's Rubin racks hold 20 times more stored energy, to steady the draw as tens of thousands of GPUs enter and leave a training step together [3](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin).

#### Where the electrons come from ^where-the-electrons-come

-   **Grid interconnection.** The slow path, and the one every announced campus is queued in.
-   **Behind-the-meter gas**, generation on the site itself. The fast path, which is why campuses are sited next to gas.
-   **Nuclear.** Almost entirely prospective. Constellation agreed to sell the output of the 835 MW Crane Clean Energy Center to Microsoft before restart work began [5](https://www.constellationenergy.com/news/2025/constellation-ahead-of-schedule-for-launch-of-crane-clean-energy-center.html). The plant shut in 2019 and is restarting on a $1 billion federal loan closed in November 2025, still subject to Nuclear Regulatory Commission approval [6](https://www.energy.gov/articles/energy-department-closes-loan-restart-nuclear-power-plant-pennsylvania). No restarted reactor is serving data centers yet.

### Who makes it ^who-makes-it-15

The largest data center operators pay for the buildout. Alphabet, Amazon, Meta, Microsoft and Oracle spent $448.3 billion of capital in 2025, and on that trend reach $770 billion in 2026 [7](https://epoch.ai/data-insights/hyperscaler-capex-trend).

Capital spending by the five largest US data center operators, 2025$B

Amazon 137.5 Microsoft 88 Alphabet 83.1 Meta 72.5 Oracle 40.6

Source: [Epoch AI, hyperscaler capex trend, February 2026, from company filings](https://epoch.ai/data-insights/hyperscaler-capex-trend)

Campuses are now described in gigawatts: OpenAI's Stargate portfolio targets more than 9 GW across US sites by 2029, with Abilene, Texas going from 0.3 GW to 1.2 GW by late 2026 [8](https://epoch.ai/publications/openai-stargate-where-the-us-sites-stand).

The equipment vendors are the constraint. GE Vernova, Siemens Energy, Hitachi Energy, ABB, Eaton and Schneider Electric supply the turbines, transformers and switchgear. GE Vernova's gas equipment backlog and reserved factory slots went from 100 GW to 116 GW inside 2026, with data center orders past $5 billion by mid-year, more than double the whole of 2025 [9](https://www.sec.gov/Archives/edgar/data/1996810/000199681026000147/gevpressrelease2q26.htm).

GE Vernova annual gas turbine output, actual and plannedGW/yr

2026 20 2028 24 2030 30

Source: [GE Vernova second-quarter 2026 results, July 2026](https://www.sec.gov/Archives/edgar/data/1996810/000199681026000147/gevpressrelease2q26.htm)

### Capacity and demand ^capacity-and-demand

US data centers used 176 TWh in 2023, 4.4 percent of national electricity, and Lawrence Berkeley National Laboratory projects 325 to 580 TWh by 2028, between 6.7 percent and 12 percent of the total [10](https://newscenter.lbl.gov/2025/01/15/berkeley-lab-report-evaluates-increase-in-electricity-demand-from-data-centers/). The Energy Information Administration expects national electricity use to rise 1 percent in 2026 and 3 percent in 2027, the fourth straight annual increase and the strongest four-year run since 2000 [11](https://www.eia.gov/pressroom/releases/press582.php).

US data center electricity use, actual and 2028 projection rangeTWh

2014 58 2023 176 2028 low case 325 2028 high case 580

Source: [Lawrence Berkeley National Laboratory, December 2024](https://newscenter.lbl.gov/2025/01/15/berkeley-lab-report-evaluates-increase-in-electricity-demand-from-data-centers/)

Chip efficiency keeps the low case plausible: Google's Ironwood TPU delivers twice the performance per watt of its predecessor [12](https://cloud.google.com/blog/products/compute/inside-the-ironwood-tpu-codesigned-ai-stack). The energy per token, where a token is the chunk of text a model reads or writes, falls while total energy rises, because the number of tokens rises faster.

### The chokepoint ^the-chokepoint-15

Announced capacity and energized capacity are a long way apart. ERCOT, the grid operator for most of Texas, was tracking about 474 GW of large loads seeking a connection in June 2026, roughly 90 percent of it data centers [13](https://www.ercot.com/files/docs/2026/07/29/ERCOT-Senate-July-29-Panel-1-Assessing-The-Grid.pdf). Only 9,042 MW had been approved to switch on [14](https://www.ercot.com/files/docs/2026/03/12/March-TAC-Report.pdf).

Behind that queue sit the equipment lead times.

-   **Large power transformers.** Thirty-six-month lead times are commonly quoted and the worst reach 60, against under a year before the pandemic; 82 percent of the units put into US service in 2019 were imported [1](https://www.energy.gov/sites/default/files/2024-10/EXEC-2022-001242%20-%20Large%20Power%20Transformer%20Resilience%20Report%20signed%20by%20Secretary%20Granholm%20on%207-10-24.pdf).
-   **Gas turbines.** GE Vernova will build 20 GW of turbines this year and is working toward 30 GW a year in 2030, against a backlog of 116 GW, close to six years of output [9](https://www.sec.gov/Archives/edgar/data/1996810/000199681026000147/gevpressrelease2q26.htm).
-   **Firm new generation**, the kind that runs whatever the weather. The one reactor restart with a data center buyer behind it, the 835 MW Crane plant, shut in 2019 and is still waiting on its license [6](https://www.energy.gov/articles/energy-department-closes-loan-restart-nuclear-power-plant-pennsylvania).

The chip chain moves faster: foundry and memory capacity have repeatedly expanded within a couple of years of the order. Money buys silicon capacity faster than it buys power capacity, and that difference decides how much of the 2026 capital spending turns into working compute.

### Key evaluation criteria ^key-evaluation-criteria-15

-   **Time to power** counts the months from signed lease to energized megawatt, and it is the number developers compete on.
-   **Transformer and turbine lead time** covers the two queues that set the schedule, at three years [1](https://www.energy.gov/sites/default/files/2024-10/EXEC-2022-001242%20-%20Large%20Power%20Transformer%20Resilience%20Report%20signed%20by%20Secretary%20Granholm%20on%207-10-24.pdf) and six years of booked output [9](https://www.sec.gov/Archives/edgar/data/1996810/000199681026000147/gevpressrelease2q26.htm).
-   **Rack density supported** decides what an existing hall can take. An air-cooled one cannot host a 142 kW NVL72 without a full mechanical retrofit [2](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html).
-   **Firmness of supply** separates a signed interconnection agreement from a delivered transformer.
-   **Energy per token** is the only efficiency measure that matters commercially. It keeps falling, but the number of tokens rises faster [12](https://cloud.google.com/blog/products/compute/inside-the-ironwood-tpu-codesigned-ai-stack).

Card 1 of 4Question

Why are AI racks cooled with water?

Card 1 of 4Answer

One rack draws 142 kilowatts, and that much heat is more than air can carry away.

Every watt a rack draws comes back out as heat. [Reread: Cooling](#data-centers-and-power--cooling)

Card 2 of 4Question

How big are the newest AI data centers?

Card 2 of 4Answer

They are planned in gigawatts, each the output of a large power station.

OpenAI's planned sites add up to more than nine gigawatts by 2029. [Reread: Capacity and demand](#data-centers-and-power--capacity-and-demand)

Card 3 of 4Question

What slows down building an AI data center most?

Card 3 of 4Answer

Waiting for power equipment.

A large power transformer takes about 36 months to arrive, and GE Vernova's gas turbines are booked about six years ahead. [Reread: The chokepoint](#data-centers-and-power--the-chokepoint)

Card 4 of 4Question

What limits China's AI data center buildout?

Card 4 of 4Answer

The supply of AI chips. China has power to spare.

China has spare generating capacity and makes its own transformers. The United States imports most of its large transformers. [Reread: The chokepoint](#data-centers-and-power--the-chokepoint)

#### Four things to remember ^four-things-to-remember-13

-   One AI rack draws 142 kilowatts, too much heat for air, so racks are cooled with water.
-   The newest AI sites are planned in gigawatts, each the output of a large power station.
-   Power equipment is the slow part: a large transformer takes about 36 months to arrive.
-   China has power to spare and is limited by the supply of AI chips.

Sources (14)

1.  A [U.S. Department of Energy Large Power Transformer Resilience Report to Congress, July 2024](https://www.energy.gov/sites/default/files/2024-10/EXEC-2022-001242%20-%20Large%20Power%20Transformer%20Resilience%20Report%20signed%20by%20Secretary%20Granholm%20on%207-10-24.pdf) U.S. Department of Energy · 10 July 2024
2.  A [System Hardware & Components](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html) Nvidia
3.  A [NVIDIA, Partners Drive Next-Gen Efficient Gigawatt AI Factories in Buildup for Vera Rubin](https://blogs.nvidia.com/blog/gigawatt-ai-factories-ocp-vera-rubin) Nvidia · 13 October 2025
4.  A [NVIDIA 800 VDC Architecture Will Power the Next Generation of AI Factories](https://developer.nvidia.com/blog/nvidia-800-v-hvdc-architecture-will-power-the-next-generation-of-ai-factories/) Nvidia · 20 May 2025
5.  A [Constellation Ahead of Schedule for Launch of Crane Clean Energy Center](https://www.constellationenergy.com/news/2025/constellation-ahead-of-schedule-for-launch-of-crane-clean-energy-center.html) Constellation Energy · 19 February 2025
6.  A [Energy Department Closes Loan to Restart Nuclear Power Plant in Pennsylvania](https://www.energy.gov/articles/energy-department-closes-loan-restart-nuclear-power-plant-pennsylvania) U.S. Department of Energy · 17 November 2025
7.  A [Hyperscaler capex has quadrupled since GPT-4's release](https://epoch.ai/data-insights/hyperscaler-capex-trend) Epoch AI · 26 February 2026
8.  A [OpenAI Stargate: where the US sites stand](https://epoch.ai/publications/openai-stargate-where-the-us-sites-stand) Epoch AI · 17 April 2026
9.  A [GE Vernova Inc., Form 8-K current report for the period ended 2026-07-22 (8-K)](https://www.sec.gov/Archives/edgar/data/1996810/000199681026000147/gevpressrelease2q26.htm) U.S. Securities and Exchange Commission (filing by GE Vernova Inc.) · 22 July 2026
10.  A [Berkeley Lab Report Evaluates Increase in Electricity Demand from Data Centers](https://newscenter.lbl.gov/2025/01/15/berkeley-lab-report-evaluates-increase-in-electricity-demand-from-data-centers/) Lawrence Berkeley National Laboratory · 15 January 2025
11.  A [EIA Press Release (01/13/2026): EIA forecasts strongest four-year growth in U.S. electricity demand since 2000, fueled by data centers](https://www.eia.gov/pressroom/releases/press582.php) U.S. Energy Information Administration
12.  A [Inside the Ironwood TPU codesigned AI stack](https://cloud.google.com/blog/products/compute/inside-the-ironwood-tpu-codesigned-ai-stack) Google Cloud · 6 November 2025
13.  A [Electric Reliability Council of Texas, ERCOT update to the Senate Committee on Business and Commerce, 29 July 2026](https://www.ercot.com/files/docs/2026/07/29/ERCOT-Senate-July-29-Panel-1-Assessing-The-Grid.pdf) Electric Reliability Council of Texas · 29 July 2026
14.  A [Electric Reliability Council of Texas, Large Load Interconnection Status Update, 13 March 2026](https://www.ercot.com/files/docs/2026/03/12/March-TAC-Report.pdf) Electric Reliability Council of Texas · 13 March 2026

## The Economics of AI Chips ^the-economics-of-ai

Inside an AI accelerator the silicon is the cheap part. Memory and packaging are most of the cost.

1,241 words / 5 minSpecimen: wafer cost

In plain terms

A bill of materials is the list of parts inside a product and what each one costs to build. For an AI accelerator, the processor itself, the chip that does the calculating, is the cheap part, about a seventh of the total. The stacked memory beside it is nearly half, and the packaging that wires the two together costs more than the chip. Three firms in the world make that memory and one Taiwanese firm does that packaging, so the costliest parts are also the scarcest, and that is where a government's rules bite hardest.

### In short ^in-short-16

On a B200 the logic dies are 14 percent of the build, memory 45, and packaging with its scrap another 33 [1](https://epoch.ai/data-insights/b200-cost-breakdown). Nvidia's 75 percent gross margin is the most visible number in the chain [6](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027), and a custom chip can undercut it by buying the same wafers and the same memory. The lines underneath are harder to cut: memory stacking yield, CoWoS interposer yield and the megawatts do not get cheaper as volume rises.

Building a Blackwell B200 costs about $6,400. Nvidia sells it for $30,000 to $40,000 [1](https://epoch.ai/data-insights/b200-cost-breakdown). That $6,400 splits into stages that are expensive because of physics, because capacity is short, or because one firm sets the price.

### How it works ^how-it-works-16

Three numbers set the cost of a die, the finished rectangle of circuitry cut out of a wafer.

-   **Wafer price.** TSMC does not publish it. Epoch AI's model of Blackwell's custom TSMC 4NP process [2](https://www.nvidia.com/en-us/data-center/technologies/blackwell-architecture/) assumes about $17,000 for a 300 mm wafer [1](https://epoch.ai/data-insights/b200-cost-breakdown).
-   **Dies per wafer.** A wafer is a circle and dies are rectangles, so the edge of the disc goes to waste: an 800 mm2 die, near the largest a scanner can print in one shot, fits 68 times.
-   **Yield.** Defects land at random, so a bigger die is likelier to catch one. Epoch AI models the Blackwell die at 40 to 70 percent good, centered on 60 [1](https://epoch.ai/data-insights/b200-cost-breakdown).

Those three numbers put the two dies inside a B200 at about $900, 14 percent of the build [1](https://epoch.ai/data-insights/b200-cost-breakdown). Doubling the wafer price moves the whole bill by a few hundred dollars.

### Variants and trade-offs ^variants-and-trade-offs-16

#### Memory is the largest line ^memory-is-the-largest

The 192 GB of high-bandwidth memory beside those dies, sold as HBM3E, is the single largest line: about $2,900, 45 percent of the build, at $14 to $17 per gigabyte [1](https://epoch.ai/data-insights/b200-cost-breakdown). Nvidia controls that line least of all: three firms make the memory, and they sell every stack they can build.

#### Packaging, substrate and test ^packaging-substrate-and-test

\CoWoS-L, the TSMC process that mounts dies and memory on one carrier and wires them together, adds about $1,100, more than the logic dies it carries [1](https://epoch.ai/data-insights/b200-cost-breakdown). Packaging yield runs 65 to 95 percent, and a package that fails after the memory goes on throws away the dies and the memory with it, adding roughly $1,000 to every B200 that ships [1](https://epoch.ai/data-insights/b200-cost-breakdown). Substrate, board, test and assembly add $480 [1](https://epoch.ai/data-insights/b200-cost-breakdown). See [[#^advanced-packaging|Advanced packaging]] for why packaging capacity runs out first.

#### The B200 bill of materials ^the-b200-bill-of

| Line | Estimate | Range |
| --- | --- | --- |
| HBM3E, 192 GB in eight stacks | $2,900 | $2,800-3,100 |
| CoWoS-L packaging | $1,100 | $1,000-1,200 |
| Packaging yield loss | $1,000 | $430-1,700 |
| Logic die, two on TSMC 4NP | $900 | $720-1,200 |
| Substrate, board, test, other | $480 | $370-600 |
| Manufacturing cost | ~$6,400 | $5,700-7,300 |
| Selling price | $30,000-40,000 |  |

Epoch AI models each line as a range, deriving the packaging line from TSMC's advanced packaging revenue and Nvidia's share of CoWoS capacity [1](https://epoch.ai/data-insights/b200-cost-breakdown). Nothing of that quality exists for the H100 or Rubin.

Where the ~$6,400 of B200 manufacturing cost goes, 2026$

HBM3E, 192 GB **2,900** CoWoS-L packaging **1,100** Packaging yield loss **1,000** Logic die, two on 4NP **900** Substrate, board, test **480**

Source: [Epoch AI B200 cost model, from a $17,000 4NP wafer, 40-70% die yield, $14-17 per GB of memory, and a packaging line derived from TSMC's advanced packaging revenue](https://epoch.ai/data-insights/b200-cost-breakdown)

#### From package to rack to cluster ^from-package-to-rack

At rack scale the number that matters is the cost of a GPU-hour. For an operator that owns the machine, SemiAnalysis puts a Vera Rubin NVL72 at $3.57, against $1.84 for a GB200 and $2.36 for a GB300 [3](https://inferencex.semianalysis.com/blog/vera-rubin-nvl72-vs-gb200-nvl72-inference). Each generation costs its owner more per hour than the last, and buyers pay because throughput rises faster than the rate.

One level up, a 100,000 H100 cluster costs over $4 billion in servers, draws about 150 MW, uses 1.59 TWh a year, pays $123.9 million for power and needs 98,304 [4](https://newsletter.semianalysis.com/p/100000-h100-clusters-power-network) optical transceivers .

### Who captures the value ^who-captures-the-value

| Firm | Stage | Quarter ended | Gross margin |
| --- | --- | --- | --- |
| Micron | HBM and DRAM | May 2026 | 84.6% |
| Nvidia | Accelerator design | July 2026 | 75.0% |
| TSMC | Wafers and CoWoS | June 2026 | 67.7% |
| KLA | Inspection | June 2026 | 61.4% |
| ASML | Lithography | June 2026 | 54.0% |
| Lam Research | Etch | June 2026 | 51.7% |
| Applied Materials | Deposition | August 2026 | 50.3% |
| Ibiden | Substrates | June 2026 | 36.4% |
| ASE Technology | OSAT | June 2026 | 21.0% |
| Amkor | OSAT | June 2026 | 16.8% |

Every figure is the firm's own reported gross margin [5](https://investors.micron.com/news/press-release/2026/Micron-Technology-Inc--Reports-Record-Results-for-the-Third-Quarter-of-Fiscal-2026/default.aspx) [6](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027) [7](https://pr.tsmc.com/english/news/3326) [8](https://ir.kla.com/news-events/press-releases/detail/518/kla-corporation-reports-fiscal-2026-fourth-quarter-and-full) [9](https://www.asml.com/en/news/press-releases/2026/q2-2026-financial-results) [10](https://newsroom.lamresearch.com/2026-07-29-Lam-Research-Corporation-Reports-Financial-Results-for-the-Quarter-Ended-June-28,-2026) [11](https://ir.appliedmaterials.com/news-releases/news-release-details/applied-materials-announces-third-quarter-2026-results) [12](https://www.ibiden.com/ir/items/tannshinn2026Q1.pdf) [13](https://www.prnewswire.com/news-releases/ase-technology-holding-co-ltd-reports-its-unaudited-consolidated-financial-results-for-the-second-quarter-of-2026-302838714.html) [14](https://www.sec.gov/Archives/edgar/data/0001047127/000104712726000043/amkr6302026erex-991.htm).

SK hynix publishes no gross margin. Its operating margin hit 76 percent in the June quarter, on revenue up 257 percent in a year [15](https://news.skhynix.com/en/q2-2026-business-results/).

Gross margin, each firm's most recent reported quarter%

Micron 84.6% Nvidia 75% TSMC 67.7% KLA 61.4% ASML 54% Lam Research 51.7% Applied Materials 50.3% Ibiden 36.4% ASE Technology 21% Amkor 16.8%

Source: [Each firm's own quarterly earnings release; quarters end between May and August 2026 (TSMC shown)](https://pr.tsmc.com/english/news/3326)

Design, inspection and leading-edge wafers earn gross margins of 50 to 75 percent, substrates 36, assembly and test 17 to 21. In 2026 memory passed all of them: Micron earned 39.8 percent for the year to August 2025 [16](https://investors.micron.com/news/press-release/2025/Micron-Technology-Inc--Reports-Results-for-the-Fourth-Quarter-and-Full-Year-of-Fiscal-2025-09-23-2025/default.aspx) and 84.6 percent in the quarter to May 2026 [5](https://investors.micron.com/news/press-release/2026/Micron-Technology-Inc--Reports-Record-Results-for-the-Third-Quarter-of-Fiscal-2026/default.aspx). The margin moved up the chain, to Nvidia's suppliers.

The two bodies that count this industry disagree. World Semiconductor Trade Statistics forecast $772 billion of global chip sales for 2025 [17](https://www.wsts.org/76/103/Global-Semiconductor-Market-Approaches-1T-in-2026); the Semiconductor Industry Association counted $791.7 billion [18](https://www.semiconductors.org/global-annual-semiconductor-sales-increase-25-6-to-791-7-billion-in-2025/). The forecasters put 2026 at $975 billion, with memory and logic each growing more than 30 percent [17](https://www.wsts.org/76/103/Global-Semiconductor-Market-Approaches-1T-in-2026). Below those totals sit $135.1 billion of [19](https://www.semi.org/en/SEMI-Reports-Global-Semiconductor-Equipment-Billings-Reached-135-Billion-in-2025) equipment billings and $448.3 billion of 2025 capital spending at Alphabet, Amazon, Meta, Microsoft and Oracle, on track for $770 billion in 2026 [20](https://epoch.ai/data-insights/hyperscaler-capex-trend).

Size of each layer of the chain, 2025$B

Semiconductor sales 792 Hyperscaler capex 448 Nvidia data center revenue 194 Semiconductor equipment 135

Source: [Semiconductor Industry Association on chip sales; Epoch AI on capital spending at Alphabet, Amazon, Meta, Microsoft and Oracle; Nvidia FY2026 results; SEMI on equipment billings](https://www.semiconductors.org/global-annual-semiconductor-sales-increase-25-6-to-791-7-billion-in-2025/)

### Where the money goes ^where-the-money-goes

Per unit of compute, logic keeps getting cheaper and everything wrapped around it gets more expensive. Packaging and its scrap cost more than twice the logic dies [1](https://epoch.ai/data-insights/b200-cost-breakdown), and a GB300 NVL72 rack already draws 142 kW [21](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html).

| Stage | Class | Why |
| --- | --- | --- |
| EUV lithography | Structurally expensive | One supplier; price set by twenty years of optics development. |
| Masks and pellicles | Structurally expensive | Scales with layer count; every design pays again. |
| Metrology and inspection | Structurally expensive | Inspection time rises faster than throughput. |
| HBM | Structurally expensive | Stacking and through-silicon vias cut good die per wafer. |
| Advanced packaging, CoWoS-L | Structurally expensive | 65 to 95 percent packaging yield; scrap destroys dies and memory. |
| Power and cooling plant | Structurally expensive | Priced by grid queues and turbine lead times. |
| Leading-edge logic wafers | Compressible with scale | Defect density and utilization improve through a ramp. |
| Design and EDA | Compressible with scale | Engineering cost is spread across volume. |
| Deposition and etch tools | Compressible with scale | Credible second sources for most deposition and etch steps. |
|{--{"author":"James's AI","timestamp":1790593699374}@@  --}{++{"author":"James's AI","timestamp":1790593699374}@@ ABF substrates ++}| Compressible with scale | A {++{"author":"James's AI","timestamp":1790593699374}@@laminate ++}line, buildable at scale. |
| Optical transceivers | Compressible with scale | Copper and {++{"author":"James's AI","timestamp":1790593700212}@@co-packaged optics ++}cap the price. |
| Test and assembly (OSAT) | Already commoditized | 17 to 21 percent margins; sold on price. |
| Wafers and bulk gases | Already commoditized | Multi-supplier, long-qualified, thin margins. |
| Rack integration (ODM) | Already commoditized | Low-teens margins on parts the customer specifies. |

### Key evaluation criteria ^key-evaluation-criteria-16

-   **Cost per good die.** A 30 percent wafer price rise at constant yield is survivable. A ten-point yield drop on an 800 mm2 die is not.
-   **Memory dollars per gigabyte, and gigabytes per part.** The largest line on the bill, set by three firms.
-   **Packaging yield.** Every point lost throws away finished dies and the memory attached to them [1](https://epoch.ai/data-insights/b200-cost-breakdown).
-   **Share of the bill the vendor does not control.** Nvidia sets its own margin but buys memory, packaging and substrates at another firm's price.
-   **Rack watts.** Past about 140 kW a rack, power and cooling capex grows faster than accelerator capex [21](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html).
-   **Compressibility class.** Whether the line falls when volume doubles. If it does not, capacity is the constraint.

Card 1 of 3Question

What does an Nvidia B200 cost to build, and what does it sell for?

Card 1 of 3Answer

About $6,400 to build. It sells for $30,000 to $40,000.

The build cost is an estimate by Epoch AI. Nvidia's gross margin is 75 percent. [Reread: The B200 bill of materials](#component-costs--the-b200-bill-of-materials)

Card 2 of 3Question

What is the most expensive part of an AI accelerator?

Card 2 of 3Answer

The stacked memory, about 45 percent of the cost to build.

The logic chips that do the calculating are about 14 percent. [Reread: Memory is the largest line](#component-costs--memory-is-the-largest-line)

Card 3 of 3Question

Why does packaging cost more than the logic chips?

Card 3 of 3Answer

A package that fails after assembly throws away the chips and the memory inside it.

Packaging and its scrap come to about 33 percent of the cost. [Reread: Packaging, substrate and test](#component-costs--packaging-substrate-and-test)

#### Three things to remember ^three-things-to-remember-2

-   A B200 costs about $6,400 to build and sells for $30,000 to $40,000.
-   The stacked memory is the most expensive part, about 45 percent of the cost.
-   Packaging costs more than the logic chips, because a failed package throws away everything inside it.

Sources (21)

1.  A [NVIDIA's B200 costs around $6,400 to produce](https://epoch.ai/data-insights/b200-cost-breakdown) Epoch AI · 10 December 2025
2.  A [NVIDIA Blackwell Architecture](https://www.nvidia.com/en-us/data-center/technologies/blackwell-architecture/) Nvidia · 18 December 2025
3.  B [Vera Rubin NVL72 vs GB200 NVL72? Inference TCO & Architecture Analysis](https://inferencex.semianalysis.com/blog/vera-rubin-nvl72-vs-gb200-nvl72-inference) SemiAnalysis · 23 July 2026
4.  B [100,000 H100 Clusters: Power, Network Topology, Ethernet vs InfiniBand, Reliability, Failures, Checkpointing](https://newsletter.semianalysis.com/p/100000-h100-clusters-power-network) SemiAnalysis · 17 June 2024
5.  A [Micron Technology, Inc. Reports Record Results for the Third Quarter of Fiscal 2026](https://investors.micron.com/news/press-release/2026/Micron-Technology-Inc--Reports-Record-Results-for-the-Third-Quarter-of-Fiscal-2026/default.aspx) Micron Technology · 24 June 2026
6.  A [NVIDIA Announces Financial Results for Second Quarter Fiscal 2027](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027) Nvidia · 26 August 2026
7.  A [TSMC Reports Second Quarter EPS of NT$27.25](https://pr.tsmc.com/english/news/3326) TSMC · 16 July 2026
8.  A [KLA CORPORATION REPORTS FISCAL 2026 FOURTH QUARTER AND FULL YEAR RESULTS](https://ir.kla.com/news-events/press-releases/detail/518/kla-corporation-reports-fiscal-2026-fourth-quarter-and-full) KLA Corporation · 28 July 2026
9.  A [ASML reports €9.3 billion total net sales and €2.9 billion net income in Q2 2026](https://www.asml.com/en/news/press-releases/2026/q2-2026-financial-results) ASML · 15 July 2026
10.  A [Lam Research Corporation Reports Financial Results for the Quarter Ended June 28, 2026](https://newsroom.lamresearch.com/2026-07-29-Lam-Research-Corporation-Reports-Financial-Results-for-the-Quarter-Ended-June-28,-2026) Lam Research · 29 July 2026
11.  A [Applied Materials Announces Third Quarter 2026 Results](https://ir.appliedmaterials.com/news-releases/news-release-details/applied-materials-announces-third-quarter-2026-results) Applied Materials · 13 August 2026
12.  A [Note: This document has been translated from a part of the Japanese original for reference purposes only.](https://www.ibiden.com/ir/items/tannshinn2026Q1.pdf) Ibiden · 3 August 2026
13.  A [ASE Technology Holding Co., Ltd. Reports Its Unaudited Consolidated Financial Results for the Second Quarter of 2026](https://www.prnewswire.com/news-releases/ase-technology-holding-co-ltd-reports-its-unaudited-consolidated-financial-results-for-the-second-quarter-of-2026-302838714.html) PR Newswire · 30 July 2026
14.  A [AMKOR TECHNOLOGY, INC., Form 8-K current report for the period ended 2026-07-27 (8-K)](https://www.sec.gov/Archives/edgar/data/0001047127/000104712726000043/amkr6302026erex-991.htm) U.S. Securities and Exchange Commission (filing by AMKOR TECHNOLOGY, INC.) · 27 July 2026
15.  A [SK hynix Announces 2Q26 Financial Results](https://news.skhynix.com/en/q2-2026-business-results/) SK hynix
16.  A [Micron Technology, Inc. Reports Results for the Fourth Quarter and Full Year of Fiscal 2025](https://investors.micron.com/news/press-release/2025/Micron-Technology-Inc--Reports-Results-for-the-Fourth-Quarter-and-Full-Year-of-Fiscal-2025-09-23-2025/default.aspx) Micron Technology · 23 September 2025
17.  A [Global Semiconductor Market Approaches $1T in 2026](https://www.wsts.org/76/103/Global-Semiconductor-Market-Approaches-1T-in-2026) World Semiconductor Trade Statistics
18.  A [Global Annual Semiconductor Sales Increase 25.6% to $791.7 Billion in 2025 - Semiconductor Industry Association](https://www.semiconductors.org/global-annual-semiconductor-sales-increase-25-6-to-791-7-billion-in-2025/) Semiconductor Industry Association · 6 February 2026
19.  A [SEMI Reports Global Semiconductor Equipment Billings Reached $135 Billion in 2025, Up 15% Year-on-Year](https://www.semi.org/en/SEMI-Reports-Global-Semiconductor-Equipment-Billings-Reached-135-Billion-in-2025) SEMI · 7 April 2026
20.  A [Hyperscaler capex has quadrupled since GPT-4's release](https://epoch.ai/data-insights/hyperscaler-capex-trend) Epoch AI · 26 February 2026
21.  A [System Hardware & Components](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html) Nvidia

## Geopolitics ^geopolitics

Every stage in this chain sits in someone's jurisdiction. Since 2018 the United States has been converting that fact into policy, and China has been building substitutes.

In plain terms

An export control is a rule that makes a sale need the government's permission. The government names an item and a buyer, and from then on its own companies must hold a license before they ship that item to that buyer. The American government stretches the rule to cover goods made abroad with American technology. Few governments can use such a rule to much effect, because it works only when their own firms sell something the buyer cannot get elsewhere. The machines, software and chemicals that make an advanced chip come from a short list of firms in the United States, the Netherlands, Japan and South Korea. China can copy the simpler machines within a few years. It cannot yet copy the machine that prints the finest circuits, the chemistry that machine needs, or high-bandwidth memory, the stacked memory beside an AI chip.

### In short ^in-short-17

One or two countries hold a dozen points in the chain, and export controls are built on that. They have held China below the leading edge, where it still cannot get extreme-ultraviolet machines, their resist or high-bandwidth memory. They have not stopped substitution beneath it, where domestic tools now take a third of China's own market. The Netherlands and Japan paid for that, their toolmakers' China share of sales down from 41 to 33 percent at ASML and from 47 to 27 percent at Tokyo Electron. What began as a small yard is now tariffs, equity stakes and a cut of licensed sales, and none of it has moved leading-edge logic or packaging out of Taiwan.

3,223 words / 14 min

Washington's control regime and Beijing's answer to it are both unfinished.

### The shape of the contest ^the-shape-of-the

In 2022 Washington changed the goal from staying a generation ahead to "as large a lead as possible", sold as a [1](https://www.csis.org/analysis/where-chips-fall-us-export-controls-under-biden-administration-2022-2024) small yard with a high fence . The October rules that followed aimed to push China backwards [2](https://www.csis.org/analysis/choking-chinas-access-future-ai). Licensing once asked who was buying and why; country-wide prohibition asks only where the item is going.

### Chokepoints and who holds them ^chokepoints-and-who-holds

| Segment | Leader | Share | Basis |
| --- | --- | --- | --- |
| EUV lithography | Netherlands | 100% | revenue, 2025 |
| DUV lithography | Netherlands | 95% | revenue, 2025 |
| Metrology and inspection | United States | 72% | revenue, 2025 |
| Deposition | United States | 60% | revenue, 2025 |
| Etch and clean | United States | 53% | revenue, 2025 |
| Photoresist | Japan | 78.4% | revenue, 2023 |
| Silicon wafers | Japan | 53% | revenue, 2023 |
| Leading-edge logic, 5 nm and below | Taiwan | 72% | capacity, 2025, site estimate |
| Foundry, all nodes | Taiwan | 78% | market share, 2025 |
| HBM | South Korea | 82.5% | revenue, 2025: SK hynix 63.2, Samsung 19.3, Micron 17.4 |
| AI accelerator design | United States | 93% | revenue, 2025 |
| Mature logic, 28 nm and above | China | 38% | capacity, 2025, site estimate |

-   **Equipment.** CSET's ETO Supply Chain Explorer, TechInsights 2025 revenue by parent-company headquarters [3](https://raw.githubusercontent.com/georgetown-cset/eto-chip-explorer/main/data/provision.csv).
-   **Materials.** Country shares of photoresist and silicon wafers as Japan's Ministry of Economy, Trade and Industry published them in December 2025, from Fuji Keizai's materials survey, by parent-company headquarters [4](https://www.meti.go.jp/policy/mono_info_service/joho/conference/semicon_digital/0014/handeji14-4.pdf). Japan held 76.7 percent of photoresist in 2021 and 78.4 in 2023, and 52.4 percent of wafers against 53.0, so neither position is moving.
-   **Taiwan.** The 78 percent is the Taiwan Semiconductor Industry Association's 2025 count, as the Stimson Center gives it [5](https://www.stimson.org/2025/why-taiwan-fears-america-first-risks-eroding-its-silicon-shield/). The 72 percent is a Chip Supply Chain estimate for capacity at 5 nm and below, carried forward from the 2022 industry baseline because nobody publishes a current measurement [6](https://www.semiconductors.org/wp-content/uploads/2024/05/Report_Emerging-Resilience-in-the-Semiconductor-Supply-Chain.pdf). The 92 percent quoted more often is a February 2024 US International Trade Commission figure, relayed by that same Stimson piece, on a wider reading of "most advanced" [5](https://www.stimson.org/2025/why-taiwan-fears-america-first-risks-eroding-its-silicon-shield/).
-   **Memory.** SK hynix's US listing prospectus splits 2025 high-bandwidth memory revenue between SK hynix at 63.2 percent, Samsung at 19.3 and Micron at 17.4, so Korea holds 82.5; by the first quarter of 2026 Korea was down to 76.9 [7](https://www.sec.gov/Archives/edgar/data/0002120882/000119312526299963/d32785d424b4.htm). The underlying figures are IDC's, relayed by the prospectus.
-   **Design.** CSIS [8](https://www.csis.org/analysis/chinas-localization-drive-semiconductors-gains-impetus-allied-chip-export-controls).
-   **China's mature nodes.** The 38 percent is a Chip Supply Chain reading of logic capacity at 28 nm and above. It sits between the 2022 industry measurement [6](https://www.semiconductors.org/wp-content/uploads/2024/05/Report_Emerging-Resilience-in-the-Semiconductor-Supply-Chain.pdf) and CSIS's finding that China now holds about half of global mature-node capacity, on a broader definition that includes discrete, analog and power chips [8](https://www.csis.org/analysis/chinas-localization-drive-semiconductors-gains-impetus-allied-chip-export-controls).

Advanced packaging is missing because nobody publishes a capacity split and TSMC will not give one. No country is self-sufficient, so each side's controls can hurt the other.

### The US export-control campaign, 2018 to today ^the-us-export-control-campaign

Commerce built the regime one rule at a time, each closing a gap the last one left.

-   **17 August 2020, the Foreign Direct Product Rule.** The Entity List, Commerce's roster of buyers that need a license, cut Huawei and 68 affiliates off from US technology in May 2019 [9](https://www.federalregister.gov/documents/2019/05/21/2019-10616/addition-of-entities-to-the-entity-list), so Huawei bought foreign chips instead. Commerce then extended the rule to any foreign item made with US technology and bound for Huawei [10](https://www.federalregister.gov/documents/2020/08/20/2020-18213/addition-of-huawei-non-us-affiliates-to-the-entity-list-the-removal-of-temporary-general-license-and). That reach makes American controls extraterritorial.
-   **7 October 2022, the first country-wide rules.** Two new export classifications, 3A090 and 3B090, capped exportable AI chips and set fab thresholds at 16 nm FinFET logic, 18 nm half-pitch DRAM and [2](https://www.csis.org/analysis/choking-chinas-access-future-ai) 128-layer NAND . They also barred US persons from servicing advanced Chinese fabs, emptying them of American engineers within days [11](https://www.federalregister.gov/documents/2022/10/13/2022-21658/implementation-of-additional-export-controls-certain-advanced-computing-and-semiconductor).
-   **17 October 2023, the density fix.** Chip designers had tuned interconnect speed to fall under the 2022 threshold while keeping the compute, so Commerce's {++{"author":"James's AI","timestamp":1790593617180}@@Bureau of Industry and Security ++}(BIS) dropped that parameter for two others: {--{"author":"James's AI","timestamp":1790593617180}@@and.--}{++{"author":"James's AI","timestamp":1790593617180}@@total processing performance and performance density.++} A data-center chip now needs a license at 4,800 points of that performance score, or at 1,600 with a density of 5.92 [12](https://cset.georgetown.edu/article/bis-2023-update-explainer/).
-   **2 December 2024, the widest rule.** 24 equipment types, three software tools, the first controls on high-bandwidth memory and 140 Entity List additions [13](https://www.bis.gov/press-release/commerce-strengthens-export-controls-restrict-chinas-capability-produce-advanced-semiconductors-military).
-   **15 January 2025, AI Diffusion.** A rule requiring a license for the top band of accelerators, 3A090.a and 4A090.a, to any destination worldwide, then reopening it by exception: License Exception AIA to the nineteen destinations named in supplement no. 5 to part 740, License Exception LPP in capped volumes elsewhere, nothing to China [14](https://www.federalregister.gov/documents/2025/01/15/2025-00636/framework-for-artificial-intelligence-diffusion). BIS said on 13 May that it would not enforce the framework, two days before the compliance date [15](https://www.bis.gov/press-release/department-commerce-announces-rescission-biden-era-artificial-intelligence-diffusion-rule-strengthens). It withdrew none of the text. The worldwide license requirement, License Exceptions AIA, ACM and LPP, supplement no. 5 and the 790 million TPP per-country allocation all stand in the Code today, and BIS says it enforces the requirement only against Country Groups D:1, D:4 and D:5 and against firms headquartered in D:5 or [16](https://www.federalregister.gov/documents/2026/07/14/2026-14132/enhanced-favorable-treatment-for-the-united-arab-emirates-under-the-export-administration) [17](https://www.ecfr.gov/current/title-15/subtitle-B/chapter-VII/subchapter-C/part-742/section-742.6) Macau . No tiered replacement has appeared; bilateral deals took the place of the caps.

On 9 April 2025 the government told Nvidia it needed a license to ship the H20 to China, to the D:5 group of arms-embargoed countries, and to any company headquartered or ultimately owned there, so no Chinese buyer could route the order through a foreign subsidiary [18](https://www.sec.gov/Archives/edgar/data/1045810/000104581025000082/nvda-20250409.htm). Nvidia took a $4.5 billion charge on stock it could no longer sell. Licenses came back in August at a price: US officials, the filing says, "have expressed an expectation that the USG will receive 15 percent of the revenue generated from licensed H20 sales", though no regulation codifies it [19](https://www.sec.gov/Archives/edgar/data/1045810/000104581025000209/nvda-20250727.htm).

Early 2026 set the current settlement.

-   **13 January 2026, effective 15 January.** BIS announced on 13 January that it would move the H200 and AMD MI325X to case-by-case review, with third-party testing and a cap at 50 percent of what the exporter ships to US customers [20](https://www.bis.gov/press-release/department-commerce-revises-license-review-policy-semiconductors-exported-china). The rule, at 91 FR 1685, took effect on publication two days later [21](https://www.federalregister.gov/documents/2026/01/15/2026-00789/revision-to-license-review-policy-for-advanced-computing-commodities).
-   **15 January 2026.** A national-security proclamation under Section 232 put a 25 percent tariff on the same class of chips, then exempted almost every American use, from data centers to startups [22](https://www.federalregister.gov/documents/2026/01/20/2026-01052/adjusting-imports-of-semiconductors-semiconductor-manufacturing-equipment-and-their-derivative).
-   **12 February 2026.** Applied Materials paid $252 million, the statutory maximum, over $126 million of ion implanters routed through Korea to an Entity-Listed Chinese customer [23](https://www.bis.gov/press-release/applied-materials-pay-252-million-penalty-bis-illegally-exporting-semiconductor-manufacturing-equipment).

Eight rule changes that shaped the regime

1.  2019-05-16Huawei and 68 affiliates added to the Entity List
2.  2022-10-07First country-wide controls on AI chips and fab tools
3.  2023-10-17Performance density added; A800 and H800 captured
4.  2024-12-0224 tool types, HBM controls, 140 entity listings
5.  2025-01-15AI Diffusion rule published, three country tiers
6.  2025-05-13AI Diffusion rescinded
7.  2025-08-11US officials seek 15% of licensed H20 sales
8.  2026-01-13H200 and MI325X case-by-case review announced, effective 15 January

Source: [BIS press releases and Federal Register rules](https://www.bis.gov/news-updates)

### Cloud and remote access ^cloud-and-remote-access

Renting a chip is not exporting it. An export, at 15 CFR 734.13, is a shipment or transmission out of the United States or a release of technology or source code to a foreign person, so a Singapore data center selling time on an H200 already installed there moves nothing across a border [25](https://www.ecfr.gov/current/title-15/subtitle-B/chapter-VII/subchapter-C/part-734/section-734.13).

The American rules reach that trade through the firms holding the chips. A January 2026 license for China or Macau is conditioned on the applicant getting the consignee's know-your-customer procedures and its list of Infrastructure-as-a-Service customers in Belarus, China, Cuba, Iran, Macau, North Korea, Russia and Venezuela, "necessary to prevent unauthorized remote access from end users described in paragraph (dd)(1)(iv)", and on a promise that no algorithm trained on the chips is served back to those users [26](https://www.govinfo.gov/content/pkg/FR-2026-01-15/html/2026-00789.htm).

The diffusion rule addressed the other end, the output. It classified frontier model weights as ECCN 4E091, warned American cloud providers that training such a model for the US subsidiary of a foreign-headquartered customer raises a red flag that the weights will leave without a license, and barred its validated end users from training one abroad, while saying that API access to a model, and rented capacity for inference, "are not prohibited" [14](https://www.federalregister.gov/documents/2025/01/15/2025-00636/framework-for-artificial-intelligence-diffusion).

So the controls reach the chip, frontier model weights, and the promises a licensed consignee signs. Compute sold by the hour on chips lawfully installed abroad sits outside them.

### Allies: the Netherlands, Japan, Korea and Europe ^allies-the-netherlands-japan

Unilateral tool controls would only transfer the sales, so the campaign depends on The Hague and Tokyo.

-   **The Netherlands.** The Dutch began licensing advanced deep-ultraviolet tools on 1 September 2023, widened that in September 2024 [27](https://www.government.nl/latest/news/2024/09/06/the-netherlands-expands-export-control-measure-advanced-semiconductor-manufacturing-equipment) and reached measurement and inspection tools on 1 April 2025 [28](https://www.government.nl/latest/news/2025/01/15/klever-export-controls-on-advanced-semiconductor-manufacturing-equipment-to-be-tightened).
-   **Japan.** Controls on advanced manufacturing equipment took effect on 23 July 2023 and apply to all destinations and name no country [29](https://www.csis.org/analysis/csis-translation-updated-japanese-export-controls-high-performance-semiconductor).
-   **South Korea.** BIS revoked the Validated End-User status that let Samsung, SK hynix and Intel run their China fabs without individual licenses, effective 31 December 2025. It will license those fabs to keep running, but not to expand or upgrade [30](https://www.federalregister.gov/documents/2025/09/02/2025-16735/revocation-of-validated-end-user-authorizations-in-the-peoples-republic-of-china).

On 30 September 2025 a BIS rule extended Entity List restrictions to any subsidiary half-owned by a listed firm [31](https://www.federalregister.gov/documents/2025/09/30/2025-19001/expansion-of-end-user-controls-to-cover-affiliates-of-certain-listed-entities). The same day the Dutch economy minister invoked the Goods Availability Act against Nexperia, the Nijmegen chipmaker that supplies European car lines, citing governance failures that risked moving technology out of Europe [32](https://www.government.nl/latest/news/2025/10/12/minister-of-economic-affairs-invokes-goods-availability-act). Neither lasted: BIS suspended its rule for a year on 10 November [33](https://www.federalregister.gov/documents/2025/11/12/2025-19846/one-year-suspension-of-expansion-of-end-user-controls-for-affiliates-of-certain-listed-entities) and the minister suspended his order on 19 November [34](https://www.government.nl/documents/2025/11/19/update-on-invoking-goods-availability-act). Europe holds a chokepoint at the leading edge and none at the mature nodes its car industry runs on.

The MATCH Act, introduced on 8 April 2026, would ban sales of immersion deep-ultraviolet scanners to China, name CXMT, Hua Hong, Huawei, SMIC and YMTC in statute, and give allies 150 days to match before the US extends the Foreign Direct Product Rule alone [35](https://www.foreign.senate.gov/press/rep/release/risch-ricketts-kim-introduce-match-act-level-the-global-playing-field-for-us-tech).

### China's response ^chinas-response

Five bodies run Beijing's side. The Ministry of Industry and Information Technology (MIIT) sets substitution targets, and in 2024 reportedly told Chinese telecom operators to strip foreign chips out of their networks by 2027 [8](https://www.csis.org/analysis/chinas-localization-drive-semiconductors-gains-impetus-allied-chip-export-controls). The National Development and Reform Commission (NDRC) plans the compute build-out and co-issued the national computing-power network plan [36](https://english.www.gov.cn/news/202312/27/content_WS658b72afc6d0868f4e8e28ba.html). The Ministry of Commerce (MOFCOM) writes and administers the export controls, including the mineral rules below [37](https://english.mofcom.gov.cn/Policies/AnnouncementsOrders/art/2025/art_0dd87cbee7b045bf93fabe6ab2faceee.html). The State Administration for Market Regulation (SAMR) is the antitrust authority, and opened its Nvidia investigation in December 2024 [38](https://www.cfr.org/articles/cyber-week-review-december-13-2024). The Cyberspace Administration of China (CAC) runs the security reviews, and in September 2025 told firms including ByteDance and Alibaba to cancel Nvidia orders [39](https://cset.georgetown.edu/newsletter/september-18-2025/).

The retaliation itself targets the inputs. Micron was first, failing a CAC review on 21 May 2023 and losing its critical infrastructure buyers [40](https://www.csis.org/analysis/micron-aggression-right-response-beijings-ban-us-chipmaker). Mineral controls followed.

-   **3 December 2024.** Notice 46, from MOFCOM, banned exports of gallium, germanium, antimony and superhard materials to the United States, one day after the American chip rules [41](https://cset.georgetown.edu/publication/china-rare-earth-export-ban/).
-   **4 April 2025.** Announcement 18 put seven medium and heavy rare earths under licensing, from samarium to yttrium, as metal, oxide, compound or finished magnet [37](https://english.mofcom.gov.cn/Policies/AnnouncementsOrders/art/2025/art_0dd87cbee7b045bf93fabe6ab2faceee.html).
-   **9 October 2025.** A further announcement reached foreign-made goods containing Chinese rare earths worth 0.1 percent or more of their value, putting a Chinese export license between a foreign firm and its own product [42](https://cset.georgetown.edu/publication/mofcom-notice-2025-61/).
-   **November 2025.** After Trump and Xi met at the Asia-Pacific summit, the ministry suspended the gallium ban for a year [43](https://www.csis.org/analysis/us-china-trade-truce-has-not-solved-gallium-problem).

Nothing was repealed; the gallium ban is paused and the licensing regimes stand.

The blunter instrument is demand. Chinese regulators discouraged customers from buying, importing or using Nvidia's data-center products, and endorsed performance-per-watt and bandwidth standards for accelerators in Chinese data centers [44](https://www.sec.gov/Archives/edgar/data/1045810/000104581026000075/nvda-20260726.htm). When Washington licensed H200 sales in February 2026, Beijing restricted them, and Nvidia's shipments came to less than 1 percent of data-center revenue [44](https://www.sec.gov/Archives/edgar/data/1045810/000104581026000075/nvda-20260726.htm). That quarter's data-center revenue was $89.0 billion, and the next quarter's guidance assumed no China compute revenue [45](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027).

Chinese tool vendors held 10 to 15 percent of their home market before 2022, took 25 percent in 2024 and 35 percent in 2025, and hold about 40 percent of domestic etch and deposition [8](https://www.csis.org/analysis/chinas-localization-drive-semiconductors-gains-impetus-allied-chip-export-controls).

Substitution stalls at the leading edge. SMIC prints 7 nm-class logic on older deep-ultraviolet scanners, exposing each layer several times because it cannot buy an extreme-ultraviolet scanner, and Huawei shipped about 805,000 Ascend units in 2025 on that silicon. The binding constraint is memory. A stockpile of roughly 13 million memory stacks, most bought before the December 2024 rules took effect, supports about 1.6 million Ascend 910C packages; CXMT, China's own memory maker, should reach about 2 million stacks in 2026, enough for 250,000 to 300,000 more [46](https://newsletter.semianalysis.com/p/huawei-ascend-production-ramp).

China's share of revenue at the four largest chip-tool makers, peak year and latest%

ASML, 2024 41% ASML, 2025 33% Applied Materials, FY2024 37% Applied Materials, FY2025 30% Lam Research, FY2024 42% Lam Research, FY2025 34% Tokyo Electron, Q4 FY2024 47% Tokyo Electron, Q4 FY2026 27%

Source: [ASML Q4 2025 investor presentation, Applied Materials and Lam Research 10-K filings, Tokyo Electron Q4 FY2026 results](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf)

### Industrial policy: CHIPS, Rapidus, Big Fund and the rest ^industrial-policy-chips-rapidus

The CHIPS and Science Act authorized about $52.7 billion [8](https://www.csis.org/analysis/chinas-localization-drive-semiconductors-gains-impetus-allied-chip-export-controls). By July 2025 $30.9 billion of direct funding had reached 19 companies for 40 projects, a median 14.2 percent of each project's capital cost [48](https://files.gao.gov/reports/GAO-26-107882/index.html).

On 22 August 2025 the government converted $5.7 billion of unpaid Intel grants and $3.2 billion of Secure Enclave defense money into a 9.9 percent stake worth $8.9 billion [49](https://www.intc.com/news-events/press-releases/detail/1748/intel-and-trump-administration-reach-historic-agreement-to).

Tariffs became the second instrument. The 2026 US-Taiwan trade agreement cuts the tariff on Taiwanese goods to 15 percent in exchange for at least $250 billion of Taiwanese investment in US chip production [50](https://www.cfr.org/articles/u-s-taiwan-trade-agreement-leaves-major-questions-open). On 16 July 2026 TSMC added $100 billion for four more Arizona fabs at 2 nm and below, taking that campus to $265 billion [51](https://www.phoenix.gov/newsroom/ced-news/tsmc-announces-additional--100-billion-investment-in-arizona.html), more than the whole CHIPS Act authorization.

Europe's first Chips Act produced no leading-edge fab, and the Chips Act 2.0 proposal adopted on 3 June 2026 widens state aid and shifts the emphasis from supply to demand without changing that [52](https://digital-strategy.ec.europa.eu/en/library/proposal-chips-act-20). Japan chose a national champion instead: Rapidus verified 2 nm gate-all-around transistors on its Chitose pilot line in 2025 and raised another 267.6 billion yen, about $1.7 billion, targeting mass production in 2027 [53](https://www.rapidus.inc/en/news_topics/information/rapidus-secures-267-6-billion-yen-in-funding-from-japan-government-and-private-sector-companies/).

China spends more, and differently. The latest round of its National Integrated Circuit Industry Investment Fund, the Big Fund, reached $47 billion [54](https://www.rand.org/pubs/perspectives/PEA4012-1.html). CSIS puts cumulative state funding since 2014 at $150 billion, roughly triple the CHIPS authorization [8](https://www.csis.org/analysis/chinas-localization-drive-semiconductors-gains-impetus-allied-chip-export-controls). The money has produced a domestic tool industry and no leading-edge node.

CHIPS Act direct funding awarded, by firm, as of July 2025$B

Intel 7.9 Micron 6.4 TSMC 6.6 Samsung 4.7 Texas Instruments 1.6 GlobalFoundries 1.6 SK hynix 0.5 Amkor 0.4 GlobalWafers 0.4 Hemlock Semiconductor 0.3

Source: [GAO-26-107882, Semiconductors: Information on Projects Funded to Strengthen U.S. Supply Chain](https://files.gao.gov/reports/GAO-26-107882/index.html)

### Taiwan ^taiwan

Taiwan is the concentration risk that no policy has reduced. Its foundries hold 78 percent of the world's contract chipmaking on the industry association's 2025 count, and 2 nm runs nowhere else [5](https://www.stimson.org/2025/why-taiwan-fears-america-first-risks-eroding-its-silicon-shield/). At 5 nm and below the island holds an estimated 72 percent of capacity in 2025, a Chip Supply Chain estimate [6](https://www.semiconductors.org/wp-content/uploads/2024/05/Report_Emerging-Resilience-in-the-Semiconductor-Supply-Chain.pdf). The packaging is on the island too. Asked in October 2025 how much CoWoS capacity he would add, TSMC's chairman said only that it was "working very hard to narrow the gap between the demand and supply", with wafer and packaging capacity both "very tight" [55](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2025-10/6860312f04fd291d0f26b46c1234f84e6332717e/TSMC%203Q25%20Transcript.pdf).

The silicon shield argument holds that this concentration deters invasion: destroying TSMC would cost an aggressor more than the island is worth. The counterargument is that staying irreplaceable gives Taipei reason to slow the diversification Washington wants. Taiwan bars the overseas production of its most advanced chips, so what TSMC builds in the United States runs a generation behind what it builds at home, and nobody expects Arizona to reach 2 nm before 2028 [5](https://www.stimson.org/2025/why-taiwan-fears-america-first-risks-eroding-its-silicon-shield/).

Arizona narrows the gap in wafers, and TSMC has two advanced packaging fabs planned there [55](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2025-10/6860312f04fd291d0f26b46c1234f84e6332717e/TSMC%203Q25%20Transcript.pdf). But a fab without its Taiwanese mask shops, chemical suppliers and trained crews is not a substitute. The shield is real and weakening, and diversification is not keeping up.

### Where the chips go: the Gulf, Southeast Asia, and smuggling ^where-the-chips-go

The Gulf has been let inside the controls. In November 2025 Commerce authorized G42 of the United Arab Emirates and HUMAIN of Saudi Arabia to buy up to 35,000 Nvidia GB300s each under security and reporting conditions [56](https://www.commerce.gov/news/press-releases/2025/11/statement-uae-and-saudi-chip-exports). On 10 July 2026 it moved the Emirates from Country Groups D:3 and D:4 into A:5, the tier that holds Washington's close allies, and named the Emirati government alongside G42 and the US hyperscalers as consignees who can take controlled AI chips and systems with no quantity cap. Licenses survive for the top-tier items, 3A090.a and 4A090.a, so the favorable treatment is tied to the named buyers [16](https://www.federalregister.gov/documents/2026/07/14/2026-14132/enhanced-favorable-treatment-for-the-united-arab-emirates-under-the-export-administration). Saudi Arabia still works license by license.

Southeast Asia is where chips get past the controls. Since 14 July 2025 Malaysia has required a permit to export, tranship or transit any high-performance US-origin AI chip, plus 30 days' notice under its Strategic Trade Act [57](https://www.miti.gov.my/miti/resources/Media%20Release/%5BFINAL%5D_MITI_Press_Stmt_Malaysia_Regulates_Trade_of_US_AI_Chips_2025-07-14.pdf). On 25 March 2026 the Justice Department charged three people over about $170 million of servers bought through Thai front companies for delivery to China [58](https://www.justice.gov/opa/pr/chinese-national-and-two-us-citizens-charged-conspiring-smuggle-artificial-intelligence).

The House select committee on China puts the median estimate at 140,000 chips smuggled to Chinese entities in 2024 [59](https://chinaselectcommittee.house.gov/media/press-releases/protecting-us-tech-china-committee-and-bipartisan-bicameral-leaders-unite-to-stop-ccp-ai-chip-smuggling). Congress's answer, the Chip Security Act, would require location verification on controlled chips within 180 days of enactment [60](https://www.congress.gov/bill/119th-congress/senate-bill/1705/text). The House Foreign Affairs Committee passed it 42-0 on 26 March 2026 [61](https://huizenga.house.gov/news/documentsingle.aspx?DocumentID=404259); it has not become law.

### Who gains and who pays ^who-gains-and-who

-   **Taiwan and Korea.** Nothing in the policy mix moves leading-edge logic, memory stacking or advanced packaging off an island and a peninsula before 2030; reshoring adds capacity elsewhere without subtracting it there.
-   **The Netherlands and Japan.** Their tool makers build the controlled machines, so they gain a say in who gets what and lose the business that paid for it: Tokyo Electron's China share fell from 47.4 to 26.8 percent of quarterly sales in two years [62](https://www.tel.com/ir/library/report/pjuomj00000000tf-att/fy26q4transcript-e.pdf).
-   **The United States.** It holds 93 percent of accelerator design revenue and will keep it. It has built no wafer, memory or assembly industry, and $30.9 billion of grants will not.
-   **China.** Mature nodes, sub-leading-edge tools, DRAM and NAND are going domestic on a visible timetable. Extreme-ultraviolet machines, their resist and high-bandwidth memory at scale are not, and stockpile arithmetic caps Ascend output near a million units a year.

The Gulf gains without making anything: named Emirati buyers take advanced compute on terms European ones do not get. And Washington's instruments now reach past licensing: a 25 percent tariff on advanced chips [22](https://www.federalregister.gov/documents/2026/01/20/2026-01052/adjusting-imports-of-semiconductors-semiconductor-manufacturing-equipment-and-their-derivative), a 9.9 percent federal stake in Intel [49](https://www.intc.com/news-events/press-releases/detail/1748/intel-and-trump-administration-reach-historic-agreement-to), an expected 15 percent cut of licensed H20 sales [19](https://www.sec.gov/Archives/edgar/data/1045810/000104581025000209/nvda-20250727.htm) and a case-by-case queue for the H200 [21](https://www.federalregister.gov/documents/2026/01/15/2026-00789/revision-to-license-review-policy-for-advanced-computing-commodities).

### What to watch ^what-to-watch

-   **November 2026.** Whether China renews the one-year suspension of its gallium ban or lets it expire [43](https://www.csis.org/analysis/us-china-trade-truce-has-not-solved-gallium-problem).
-   **The MATCH Act's 150-day deadline.** If it passes, allied divergence on deep-ultraviolet tools gets a statutory deadline [35](https://www.foreign.senate.gov/press/rep/release/risch-ricketts-kim-introduce-match-act-level-the-global-playing-field-for-us-tech).
-   **CXMT's memory ramp.** Domestic memory caps Chinese accelerator volume before logic wafers do [46](https://newsletter.semianalysis.com/p/huawei-ascend-production-ramp).
-   **SMIC's advanced-node ramp.** 45,000 {++{"author":"James's AI","timestamp":1790593640316}@@wafers a month ++}at end-2025, an estimated 60,000 in 2026 and 80,000 in 2027, every one of them {++{"author":"James's AI","timestamp":1790593640316}@@multiply exposed ++}because SMIC has no extreme-ultraviolet machine [46](https://newsletter.semianalysis.com/p/huawei-ascend-production-ramp). {++{"author":"James's AI","timestamp":1790593640316}@@Yield ++}is the open question.
-   **Taiwan's overseas-production ban against its $250 billion investment promise.** The two contradict each other, and one will be dropped.

Card 1 of 5Question

When does an export control work?

Card 1 of 5Answer

When a country's own firms sell something the buyer cannot get elsewhere.

The machines, software and chemicals for advanced chips come from a few firms in the United States, the Netherlands, Japan and South Korea. [Reread: Chokepoints and who holds them](#geopolitics--chokepoints-and-who-holds-them)

Card 2 of 5Question

How do US export controls reach goods made in other countries?

Card 2 of 5Answer

They cover foreign goods made with American technology.

In August 2020 the United States used this reach to cut Huawei off from chips made abroad with American technology. [Reread: The US export-control campaign, 2018 to today](#geopolitics--the-us-export-control-campaign-2018-to-today)

Card 3 of 5Question

What have export controls achieved against China?

Card 3 of 5Answer

They have kept China below the leading edge.

China still cannot get EUV machines, their resist or high-bandwidth memory. Its own toolmakers took 35 percent of its home market in 2025. [Reread: China's response](#geopolitics--chinas-response)

Card 4 of 5Question

What have the controls cost allied toolmakers?

Card 4 of 5Answer

A large share of their sales to China.

China's share of ASML's system sales fell from 41 percent in 2024 to 33 percent in 2025. Its share of Tokyo Electron's sales fell from 47 to 27 percent. [Reread: Allies: the Netherlands, Japan, Korea and Europe](#geopolitics--allies-the-netherlands-japan-korea-and-europe)

Card 5 of 5Question

Where are the most advanced chips made today?

Card 5 of 5Answer

Only in Taiwan.

No policy so far has moved leading-edge chipmaking or packaging off the island. [Reread: Taiwan](#geopolitics--taiwan)

#### Five things to remember ^five-things-to-remember-2

-   An export control works only when a country's firms sell something the buyer cannot get elsewhere.
-   US controls also cover foreign goods made with American technology.
-   The controls have kept China below the leading edge, and Chinese toolmakers took 35 percent of their home market in 2025.
-   The controls cut Dutch and Japanese toolmakers' sales to China.
-   The most advanced chips are still made only in Taiwan.

Sources (62)

1.  A [Where the Chips Fall: U.S. Export Controls Under the Biden Administration from 2022 to 2024](https://www.csis.org/analysis/where-chips-fall-us-export-controls-under-biden-administration-2022-2024) Center for Strategic and International Studies · 12 December 2024
2.  A [Choking off China’s Access to the Future of AI](https://www.csis.org/analysis/choking-chinas-access-future-ai) Center for Strategic and International Studies · 11 October 2022
3.  A [ETO Chip Explorer source data: provision.csv](https://raw.githubusercontent.com/georgetown-cset/eto-chip-explorer/main/data/provision.csv) Center for Security and Emerging Technology (CSET) / Emerging Technology Observatory
4.  A [METI, Semiconductor and digital industry strategy: future direction (半導体・デジタル産業戦略の今後の方向性), 23 December 2025](https://www.meti.go.jp/policy/mono_info_service/joho/conference/semicon_digital/0014/handeji14-4.pdf) Ministry of Economy, Trade and Industry (Japan) · 23 December 2025
5.  A [Why Taiwan Fears ‘America First’ Risks Eroding Its ‘Silicon Shield’](https://www.stimson.org/2025/why-taiwan-fears-america-first-risks-eroding-its-silicon-shield/) Stimson Center · 10 October 2025
6.  A [R AJ VA RA DA RA JA N / I ACOB KOCH -W E SE R / CH RI S RI CH A RD / JOSE P H FI TZ GE RA L D /](https://www.semiconductors.org/wp-content/uploads/2024/05/Report_Emerging-Resilience-in-the-Semiconductor-Supply-Chain.pdf) Semiconductor Industry Association · 9 May 2024
7.  A [SK hynix Inc., Form 424B4 prospectus for the period ended 2026-07-10 (424(B)(4))](https://www.sec.gov/Archives/edgar/data/0002120882/000119312526299963/d32785d424b4.htm) U.S. Securities and Exchange Commission (filing by SK hynix Inc.) · 10 July 2026
8.  A [China’s Localization Drive in Semiconductors Gains Impetus from Allied Chip Export Controls](https://www.csis.org/analysis/chinas-localization-drive-semiconductors-gains-impetus-allied-chip-export-controls) Center for Strategic and International Studies · 24 March 2026
9.  A [Addition of Entities to the Entity List](https://www.federalregister.gov/documents/2019/05/21/2019-10616/addition-of-entities-to-the-entity-list) Federal Register (Commerce Department; Industry and Security Bureau) · 21 May 2019
10.  A [Addition of Huawei Non-U.S. Affiliates to the Entity List, the Removal of Temporary General License, and Amendments to General Prohibition Three (Foreign-Produced Direct Product Rule)](https://www.federalregister.gov/documents/2020/08/20/2020-18213/addition-of-huawei-non-us-affiliates-to-the-entity-list-the-removal-of-temporary-general-license-and) Federal Register (Commerce Department; Industry and Security Bureau) · 20 August 2020
11.  A [Implementation of Additional Export Controls: Certain Advanced Computing and Semiconductor Manufacturing Items; Supercomputer and Semiconductor End Use; Entity List Modification](https://www.federalregister.gov/documents/2022/10/13/2022-21658/implementation-of-additional-export-controls-certain-advanced-computing-and-semiconductor) Federal Register (Commerce Department; Industry and Security Bureau) · 13 October 2022
12.  A [Explainer: The Commerce Department's October 2023 Export Control Update](https://cset.georgetown.edu/article/bis-2023-update-explainer/) Center for Security and Emerging Technology (CSET) · 4 December 2023
13.  A [Commerce Strengthens Export Controls to Restrict China's Capability to Produce Advanced Semiconductors for Military Applications](https://www.bis.gov/press-release/commerce-strengthens-export-controls-restrict-chinas-capability-produce-advanced-semiconductors-military) U.S. Bureau of Industry and Security · 2 December 2024
14.  A [Framework for Artificial Intelligence Diffusion](https://www.federalregister.gov/documents/2025/01/15/2025-00636/framework-for-artificial-intelligence-diffusion) Federal Register (Commerce Department; Industry and Security Bureau) · 15 January 2025
15.  A [Department of Commerce Announces Rescission of Biden-Era Artificial Intelligence Diffusion Rule, Strengthens Chip-Related Export Controls](https://www.bis.gov/press-release/department-commerce-announces-rescission-biden-era-artificial-intelligence-diffusion-rule-strengthens) U.S. Bureau of Industry and Security · 13 May 2025
16.  A [Enhanced Favorable Treatment for the United Arab Emirates Under the Export Administration Regulations](https://www.federalregister.gov/documents/2026/07/14/2026-14132/enhanced-favorable-treatment-for-the-united-arab-emirates-under-the-export-administration) Federal Register (Commerce Department; Industry and Security Bureau) · 14 July 2026
17.  A [15 CFR 742.6, Regional stability](https://www.ecfr.gov/current/title-15/subtitle-B/chapter-VII/subchapter-C/part-742/section-742.6) Electronic Code of Federal Regulations
18.  A [NVIDIA CORP, Form 8-K current report for the period ended 2025-04-09 (8-K)](https://www.sec.gov/Archives/edgar/data/1045810/000104581025000082/nvda-20250409.htm) U.S. Securities and Exchange Commission (filing by NVIDIA CORP) · 15 April 2025
19.  A [NVIDIA CORP, Form 10-Q quarterly report for the period ended 2025-07-27 (10-Q)](https://www.sec.gov/Archives/edgar/data/1045810/000104581025000209/nvda-20250727.htm) U.S. Securities and Exchange Commission (filing by NVIDIA CORP) · 27 August 2025
20.  A [Department of Commerce Revises License Review Policy for Semiconductors Exported to China](https://www.bis.gov/press-release/department-commerce-revises-license-review-policy-semiconductors-exported-china) U.S. Bureau of Industry and Security · 13 January 2026
21.  A [Revision to License Review Policy for Advanced Computing Commodities](https://www.federalregister.gov/documents/2026/01/15/2026-00789/revision-to-license-review-policy-for-advanced-computing-commodities) Federal Register (Commerce Department; Industry and Security Bureau) · 15 January 2026
22.  A [Adjusting Imports of Semiconductors, Semiconductor Manufacturing Equipment, and Their Derivative Products Into the United States](https://www.federalregister.gov/documents/2026/01/20/2026-01052/adjusting-imports-of-semiconductors-semiconductor-manufacturing-equipment-and-their-derivative) Federal Register (Executive Office of the President) · 20 January 2026
23.  A [Applied Materials to Pay $252 Million Penalty to BIS for Illegally Exporting Semiconductor Manufacturing Equipment](https://www.bis.gov/press-release/applied-materials-pay-252-million-penalty-bis-illegally-exporting-semiconductor-manufacturing-equipment) U.S. Bureau of Industry and Security · 11 February 2026
24.  A [U.S. Bureau of Industry and Security, news and updates](https://www.bis.gov/news-updates) U.S. Bureau of Industry and Security
25.  A [15 CFR 734.13 -- Export.](https://www.ecfr.gov/current/title-15/subtitle-B/chapter-VII/subchapter-C/part-734/section-734.13) Electronic Code of Federal Regulations
26.  A [Federal Register, Volume 91 Issue 10 (Thursday, January 15, 2026)](https://www.govinfo.gov/content/pkg/FR-2026-01-15/html/2026-00789.htm) U.S. Government Publishing Office
27.  A [The Netherlands expands export control measure for advanced semiconductor manufacturing equipment](https://www.government.nl/latest/news/2024/09/06/the-netherlands-expands-export-control-measure-advanced-semiconductor-manufacturing-equipment) Government of the Netherlands · 6 September 2024
28.  A [Klever: export controls on advanced semiconductor manufacturing equipment to be tightened](https://www.government.nl/latest/news/2025/01/15/klever-export-controls-on-advanced-semiconductor-manufacturing-equipment-to-be-tightened) Government of the Netherlands · 15 January 2025
29.  A [CSIS Translation: Updated Japanese Export Controls on High-Performance Semiconductor Manufacturing Equipment](https://www.csis.org/analysis/csis-translation-updated-japanese-export-controls-high-performance-semiconductor) Center for Strategic and International Studies · 18 July 2023
30.  A [Revocation of Validated End-User Authorizations in the People's Republic of China](https://www.federalregister.gov/documents/2025/09/02/2025-16735/revocation-of-validated-end-user-authorizations-in-the-peoples-republic-of-china) Federal Register (Commerce Department; Industry and Security Bureau) · 2 September 2025
31.  A [Expansion of End-User Controls To Cover Affiliates of Certain Listed Entities](https://www.federalregister.gov/documents/2025/09/30/2025-19001/expansion-of-end-user-controls-to-cover-affiliates-of-certain-listed-entities) Federal Register (Commerce Department; Industry and Security Bureau) · 30 September 2025
32.  A [Minister of Economic Affairs invokes Goods Availability Act](https://www.government.nl/latest/news/2025/10/12/minister-of-economic-affairs-invokes-goods-availability-act) Government of the Netherlands · 12 October 2025
33.  A [One Year Suspension of Expansion of End-User Controls for Affiliates of Certain Listed Entities](https://www.federalregister.gov/documents/2025/11/12/2025-19846/one-year-suspension-of-expansion-of-end-user-controls-for-affiliates-of-certain-listed-entities) Federal Register (Commerce Department; Industry and Security Bureau) · 12 November 2025
34.  A [Update on invoking Goods Availability Act](https://www.government.nl/documents/2025/11/19/update-on-invoking-goods-availability-act) Government of the Netherlands · 19 November 2025
35.  A [Risch, Ricketts, Kim Introduce MATCH Act; Level the Global Playing Field for U.S. Tech](https://www.foreign.senate.gov/press/rep/release/risch-ricketts-kim-introduce-match-act-level-the-global-playing-field-for-us-tech) U.S. Senate Committee on Foreign Relations · 8 April 2026
36.  A [China accelerates building of national computing power network](https://english.www.gov.cn/news/202312/27/content_WS658b72afc6d0868f4e8e28ba.html) The State Council of the People's Republic of China · 27 December 2023
37.  A [Announcement No.18 of 2025 of The Ministry of Commerce and The General Administration of Customs of The People’s Republic of China Announcing the decision to implement export control on some medium and heavy rare earth related items](https://english.mofcom.gov.cn/Policies/AnnouncementsOrders/art/2025/art_0dd87cbee7b045bf93fabe6ab2faceee.html) Ministry of Commerce of the People's Republic of China
38.  A [Cyber Week in Review: December 13, 2024](https://www.cfr.org/articles/cyber-week-review-december-13-2024) Council on Foreign Relations · 13 December 2024
39.  A [Beijing blocks Nvidia sales in vote of confidence for Chinese chipmakers, the White House strikes a deal for 10 percent of Intel, and Commerce voids a $7.4B CHIPS Act grant](https://cset.georgetown.edu/newsletter/september-18-2025/) Center for Security and Emerging Technology (CSET) · 18 September 2025
40.  A [Micron Aggression: The Right Response to Beijing’s Ban on the U.S. Chipmaker](https://www.csis.org/analysis/micron-aggression-right-response-beijings-ban-us-chipmaker) Center for Strategic and International Studies · 22 June 2023
41.  A [Ministry of Commerce Notice 2024 No. 46: Notice Concerning Strengthening Controls on Exports of Relevant Dual-Use Items to the United States](https://cset.georgetown.edu/publication/china-rare-earth-export-ban/) Center for Security and Emerging Technology (CSET) · 3 December 2024
42.  A [Ministry of Commerce Notice 2025 No. 61: Announcement of the Decision to Implement Controls on Exports of Rare Earth-Related Items to Foreign Countries](https://cset.georgetown.edu/publication/mofcom-notice-2025-61/) Center for Security and Emerging Technology (CSET) · 9 October 2025
43.  A [The U.S.-China Trade Truce Has Not Solved the Gallium Problem](https://www.csis.org/analysis/us-china-trade-truce-has-not-solved-gallium-problem) Center for Strategic and International Studies · 11 May 2026
44.  A [NVIDIA CORP, Form 10-Q quarterly report for the period ended 2026-07-26 (10-Q)](https://www.sec.gov/Archives/edgar/data/1045810/000104581026000075/nvda-20260726.htm) U.S. Securities and Exchange Commission (filing by NVIDIA CORP) · 26 August 2026
45.  A [NVIDIA Announces Financial Results for Second Quarter Fiscal 2027](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027) Nvidia · 26 August 2026
46.  B [Huawei Ascend Production Ramp: Die Banks, TSMC Continued Production, HBM is The Bottleneck](https://newsletter.semianalysis.com/p/huawei-ascend-production-ramp) SemiAnalysis · 8 September 2025
47.  A [Presentation Investor Relations Q4 2025](https://ourbrand.asml.com/m/3136300aa4999bc1/original/2026_01_28_Presentation-Investor-Relations-Q4-2025.pdf) ASML · 27 January 2026
48.  A [GAO-26-107882, SEMICONDUCTORS: Information on Projects Funded to Strengthen U.S. Supply Chain](https://files.gao.gov/reports/GAO-26-107882/index.html) U.S. Government Accountability Office
49.  A [Intel and Trump Administration Reach Historic Agreement to Accelerate American Technology and Manufacturing Leadership](https://www.intc.com/news-events/press-releases/detail/1748/intel-and-trump-administration-reach-historic-agreement-to) Intel · 22 August 2025
50.  A [U.S.-Taiwan Trade Agreement Leaves Major Questions Open](https://www.cfr.org/articles/u-s-taiwan-trade-agreement-leaves-major-questions-open) Council on Foreign Relations · 13 February 2026
51.  A [TSMC Announces Additional $100 Billion Investment In Arizona](https://www.phoenix.gov/newsroom/ced-news/tsmc-announces-additional--100-billion-investment-in-arizona.html) City of Phoenix · 16 July 2026
52.  A [Proposal for the Chips Act 2.0](https://digital-strategy.ec.europa.eu/en/library/proposal-chips-act-20) European Commission
53.  A [Rapidus Secures 267.6 Billion Yen in Funding from Japan Government and Private Sector Companies This strategic funding plan will enable Rapidus to steadily progress from its current R&D phase to mass production of 2nm logic semiconductors by 2027 - Information - Rapidus Corporation](https://www.rapidus.inc/en/news_topics/information/rapidus-secures-267-6-billion-yen-in-funding-from-japan-government-and-private-sector-companies/) Rapidus
54.  A [China's Evolving Industrial Policy for AI](https://www.rand.org/pubs/perspectives/PEA4012-1.html) RAND Corporation · 26 June 2025
55.  A [Q3 2025 Taiwan Semiconductor Manufacturing Co Ltd Earnings Call (Chinese, English) — edited transcript](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2025-10/6860312f04fd291d0f26b46c1234f84e6332717e/TSMC%203Q25%20Transcript.pdf) Refinitiv StreetEvents (transcript of a TSMC earnings call), via TSMC · 16 October 2025
56.  A [Statement on UAE and Saudi Chip Exports](https://www.commerce.gov/news/press-releases/2025/11/statement-uae-and-saudi-chip-exports) U.S. Department of Commerce · November 2025
57.  A [EXPORT, TRANSSHIPMENT AND TRANSIT OF HIGH-PERFORMANCE AI CHIPS OF US ORIGIN](https://www.miti.gov.my/miti/resources/Media%20Release/%5BFINAL%5D_MITI_Press_Stmt_Malaysia_Regulates_Trade_of_US_AI_Chips_2025-07-14.pdf) Ministry of Investment, Trade and Industry (Malaysia) · 14 July 2025
58.  A [Chinese National and Two U.S. Citizens Charged with Conspiring to Smuggle Artificial Intelligence Technology to China](https://www.justice.gov/opa/pr/chinese-national-and-two-us-citizens-charged-conspiring-smuggle-artificial-intelligence) U.S. Department of Justice · 25 March 2026
59.  A [Protecting U.S. Tech: China Committee and Bipartisan, Bicameral Leaders Unite to Stop CCP AI Chip Smuggling](https://chinaselectcommittee.house.gov/media/press-releases/protecting-us-tech-china-committee-and-bipartisan-bicameral-leaders-unite-to-stop-ccp-ai-chip-smuggling) U.S. House Select Committee on the Chinese Communist Party · 7 July 2025
60.  A [S.1705 – Chip Security Act, 119th Congress (2025-2026), bill text](https://www.congress.gov/bill/119th-congress/senate-bill/1705/text) U.S. Congress (Congress.gov, Library of Congress)
61.  A [UNANIMOUS: Bipartisan Huizenga Legislation to Curb AI Chip Smuggling Passes Committee](https://huizenga.house.gov/news/documentsingle.aspx?DocumentID=404259) U.S. House of Representatives (Office of Rep. Bill Huizenga) · 26 March 2026
62.  A [Investor Relations / April 30, 2026](https://www.tel.com/ir/library/report/pjuomj00000000tf-att/fy26q4transcript-e.pdf) Tokyo Electron · 30 April 2026

## AI Chips ^ai-chips

The chips that train and run AI models, from the A100 of 2020 to the parts shipping in 2026, with the foundry, process node, memory supplier and packaging plant behind each one.

### Packages at one scale ^packages-at-one-scale

The logic dies do the computing, the memory stacks feed them, the interposer is the silicon slab that wires the two together, and the substrate is the card underneath.

### Specs side by side ^specs-side-by-side

TFLOPS counts trillions of calculations a second. FP16, FP8 and FP4 are number formats: the fewer the bits, the more calculations a chip can do.

## Suppliers ^suppliers

What each of the 220 firms makes, where it sits, and how hard it would be to replace.

The route of one chip

**Taiwan** leads four stages, three of them extreme Makes nearly every leading-edge chip and packages most of them

[[#^chip-design-eda-and|1]] [[#^silicon-and-wafers|2]] [[#^chemicals-gases-and-photoresist|3]] [[#^lithography|4]] [[#^photomasks-and-pellicles|5]] [[#^deposition-and-etch|6]] [[#^metrology-and-inspection|7]] [[#^transistors-and-the-front|8]] [[#^foundries-and-fabs|9]] [[#^memory-and-hbm|10]] [[#^advanced-packaging|11]] [[#^substrates-and-pcbs|12]] [[#^test-and-assembly|13]] [[#^systems-and-networking|14]] [[#^data-centers-and-power|15]]

1.  [[#^chip-design-eda-and|01Chip Design, EDA & IPSan Jose · US]]
2.  [[#^silicon-and-wafers|02Silicon & WafersTokyo · JP]]
3.  [[#^chemicals-gases-and-photoresist|03Chemicals, Gases & PhotoresistKawasaki · JP]]
4.  [[#^lithography|04LithographyVeldhoven · NL]]
5.  [[#^photomasks-and-pellicles|05Photomasks & PelliclesYokohama · JP]]
6.  [[#^deposition-and-etch|06Deposition & EtchSanta Clara · US]]
7.  [[#^metrology-and-inspection|07Metrology & InspectionMilpitas · US]]
8.  [[#^transistors-and-the-front|08Transistors & the Front EndHsinchu · TW]]
9.  [[#^foundries-and-fabs|09Foundries & FabsTainan · TW]]
10.  [[#^memory-and-hbm|10Memory & HBMIcheon · KR]]
11.  [[#^advanced-packaging|11Advanced PackagingKaohsiung · TW]]
12.  [[#^substrates-and-pcbs|12Substrates & PCBsOgaki · JP]]
13.  [[#^test-and-assembly|13Test & AssemblyPenang · MY]]
14.  [[#^systems-and-networking|14Systems & NetworkingTaipei · TW]]
15.  [[#^data-centers-and-power|15Data Centers & PowerAshburn · US]]

The United States holds 93% of AI accelerator design, more than any other country, and is named on fourteen of the seventeen chokepoint cards.

-   [[#^chip-design-eda-and|AI accelerator design _estimate_ 93% 2025]]
-   [[#^chip-design-eda-and|EDA software _estimate_ 74% 2025]]
-   [[#^metrology-and-inspection|Metrology & inspection tools reported by TechInsights 71.7% 2025]]
-   [[#^chip-design-eda-and|Chip Design, EDA and IP **Extreme** Synopsys, Cadence, Broadcom, Marvell, Nvidia, AMD; Siemens EDA's main sites]]
-   [[#^lithography|Lithography **Extreme** ASML light-source research and manufacturing, San Diego]]
-   [[#^photomasks-and-pellicles|Photomasks and Pellicles Extreme Photronics merchant mask shops, KLA inspection]]

[[#^suppliers|66 firms in the supplier list, led by AI accelerator vendor; interconnect and networking; optics and photonics]] · [[#^geopolitics|four chokepoint towns: Hillsboro, Phoenix, Austin, Boise]]

The Netherlands holds 100% of EUV lithography tools, more than any other country, and is named on four of the seventeen chokepoint cards.

-   [[#^lithography|EUV lithography tools _reported by TechInsights_ 100% 2025]]
-   [[#^lithography|DUV lithography tools _computed_ 95% 2025]]
-   [[#^deposition-and-etch|Deposition tools reported by TechInsights 10.9% 2025]]
-   [[#^lithography|Lithography **Extreme** ASML design and final assembly, Veldhoven]]
-   [[#^advanced-packaging|Advanced Packaging Extreme Besi hybrid and die bonders]]
-   [[#^deposition-and-etch|Deposition and Etch High ASM International, Almere; ALD and epitaxy]]

[[#^suppliers|4 firms in the supplier list, led by lithography; equipment subsystems and components; deposition and etch]] · [[#^geopolitics|one chokepoint town: Veldhoven]]

Germany holds 17% of specialty gases, and is named on four of the seventeen chokepoint cards.

-   [[#^chemicals-gases-and-photoresist|Specialty gases estimate 17% 2024]]
-   [[#^chip-design-eda-and|EDA software _estimate_ 13% 2025]]
-   [[#^silicon-and-wafers|Silicon wafers reported by Fuji Keizai 10% 2023]]
-   [[#^lithography|Lithography **Extreme** Zeiss SMT optics, Oberkochen; Trumpf carbon dioxide lasers that drive the light source, Ditzingen]]
-   [[#^photomasks-and-pellicles|Photomasks and Pellicles Extreme Zeiss mask repair and metrology]]
-   [[#^silicon-and-wafers|Silicon and Wafers High Siltronic Burghausen and Freiberg; Wacker semiconductor-grade polysilicon]]

[[#^suppliers|10 firms in the supplier list, led by equipment subsystems and components; silicon and wafers; power and cooling]] · [[#^geopolitics|two chokepoint towns: Oberkochen, Dresden]]

Japan holds 78.4% of photoresist, more than any other country, and is named on thirteen of the seventeen chokepoint cards.

-   [[#^chemicals-gases-and-photoresist|Photoresist reported by Fuji Keizai 78.4% 2023]]
-   [[#^silicon-and-wafers|Silicon wafers reported by Fuji Keizai 53% 2023]]
-   [[#^photomasks-and-pellicles|Photomasks 53% 2019]]
-   [[#^lithography|Lithography **Extreme** Nikon and Canon deep ultraviolet scanners and steppers]]
-   [[#^photomasks-and-pellicles|Photomasks and Pellicles Extreme Mask blanks (AGC, Hoya), DUV blanks (Shin-Etsu), inspection (Lasertec), writers (NuFlare), pellicles (Mitsui Chemicals)]]
-   [[#^transistors-and-the-front|Transistors and the Front End **Extreme** Rapidus Chitose, Hokkaido]]

[[#^suppliers|43 firms in the supplier list, led by photoresist and materials; photomasks; substrates and PCBs]] · [[#^geopolitics|three chokepoint towns: Kumamoto, Yokkaichi, Tokyo]]

Taiwan holds 72% of leading-edge logic manufacturing (≤5 nm), more than any other country, and is named on eleven of the seventeen chokepoint cards.

-   [[#^foundries-and-fabs|Leading-edge logic manufacturing (≤5 nm) estimate 72% 2025]]
-   [[#^test-and-assembly|Assembly, test and packaging (ATP) 28% 2022]]
-   [[#^foundries-and-fabs|Mature logic manufacturing (≥28 nm) estimate 27% 2025]]
-   [[#^chip-design-eda-and|Chip Design, EDA and IP **Extreme** Alchip, Global Unichip and MediaTek: design services that carry a chip to the factory]]
-   [[#^photomasks-and-pellicles|Photomasks and Pellicles Extreme TSMC's in-house mask shop, and a 10% stake in IMS]]
-   [[#^transistors-and-the-front|Transistors and the Front End **Extreme** TSMC N2 at Fab 20 Hsinchu and Fab 22 Kaohsiung]]

[[#^suppliers|25 firms in the supplier list, led by systems and servers; advanced packaging and OSAT; substrates and PCBs]] · [[#^geopolitics|three chokepoint towns: Hsinchu, Tainan, Kaohsiung]]

South Korea holds 82.5% of HBM, more than any other country, and is named on seven of the seventeen chokepoint cards.

-   [[#^memory-and-hbm|HBM reported by IDC 82.5% 2025]]
-   [[#^memory-and-hbm|DRAM manufacturing reported by IDC 69.3% 2025]]
-   [[#^silicon-and-wafers|Silicon wafers reported by Fuji Keizai 13% 2023]]
-   [[#^transistors-and-the-front|Transistors and the Front End **Extreme** Samsung Hwaseong and Pyeongtaek]]
-   [[#^foundries-and-fabs|Foundries and Fabs Extreme Samsung Foundry, Hwaseong and Pyeongtaek]]
-   [[#^memory-and-hbm|Memory and HBM Extreme SK hynix Cheongju and Icheon; Samsung Pyeongtaek and Hwaseong]]

[[#^suppliers|15 firms in the supplier list, led by AI accelerator vendor; silicon and wafers; photoresist and materials]] · [[#^geopolitics|two chokepoint towns: Icheon, Pyeongtaek]]

China holds 38% of mature logic manufacturing (≥28 nm), more than any other country, and is named on nine of the seventeen chokepoint cards.

-   [[#^foundries-and-fabs|Mature logic manufacturing (≥28 nm) estimate 38% 2025]]
-   [[#^test-and-assembly|Assembly, test and packaging (ATP) 30% 2022]]
-   [[#^chemicals-gases-and-photoresist|Specialty gases estimate 15% 2024]]
-   [[#^transistors-and-the-front|Transistors and the Front End **Extreme** SMIC Shanghai and Beijing 300 mm lines]]
-   [[#^foundries-and-fabs|Foundries and Fabs Extreme SMIC and Hua Hong; the largest installed capacity of any region, almost all of it on older nodes]]
-   [[#^advanced-packaging|Advanced Packaging Extreme JCET, Tongfu and HT-Tech, strong in conventional assembly and test, weak in 2.5D]]

Where China stands

[[#^lithography|Lithography]] No EUV scanner has ever been sold to a customer in China.

[[#^transistors-and-the-front|Transistors and the Front End]] SMIC ships a process it calls N+3, measured at 113.4 million transistors per square millimeter.

[[#^suppliers|30 firms in the supplier list, led by AI accelerator vendor; design and EDA; deposition and etch]] · [[#^geopolitics|five chokepoint towns: Shanghai, Beijing, Wuhan, Shenzhen, Hefei]]

Malaysia is named on one of the seventeen chokepoint cards.

-   [[#^test-and-assembly|Test and Assembly High Penang and Kulim; Malaysia ships about 13% of the world's packaged chips]]

No firm in the supplier list · [[#^geopolitics|one chokepoint town: Penang]]

Singapore is named on one of the seventeen chokepoint cards, and three of the 220 firms in the supplier list are based there.

-   [[#^memory-and-hbm|Memory and HBM Extreme Micron HBM advanced packaging]]

[[#^suppliers|3 firms in the supplier list, led by advanced packaging and OSAT]] · [[#^geopolitics|one chokepoint town: Singapore]]

The United Kingdom holds 48% of core IP, more than any other country, and is named on one of the seventeen chokepoint cards.

-   [[#^chip-design-eda-and|Core IP _estimate_ 48% 2025]]
-   [[#^chip-design-eda-and|Chip Design, EDA and IP **Extreme** Arm processor and interconnect designs, licensed from Cambridge]]

[[#^suppliers|5 firms in the supplier list, led by IP and architecture; chemicals and gases; equipment subsystems and components]]

Israel holds 6% of metrology & inspection tools, and is named on two of the seventeen chokepoint cards.

-   [[#^chip-design-eda-and|Chip Design, EDA and IP **Extreme** Annapurna Labs, the AWS design house behind Trainium and Graviton]]
-   [[#^metrology-and-inspection|Metrology and Inspection High Nova (Rehovot) and Camtek (Migdal Haemek)]]

[[#^suppliers|3 firms in the supplier list, led by metrology and inspection; foundry]]

India is named on one of the seventeen chokepoint cards.

-   [[#^chip-design-eda-and|Chip Design, EDA and IP **Extreme** Nearly 20% of the world's chip design engineers, on the Indian government's count]]

No firm in the supplier list · [[#^geopolitics|one chokepoint town: Bengaluru]]

France is named on one of the seventeen chokepoint cards, and three of the 220 firms in the supplier list are based there.

-   [[#^chemicals-gases-and-photoresist|Chemicals, Gases and Photoresist High Air Liquide electronics gases and precursors]]

[[#^suppliers|3 firms in the supplier list, led by silicon and wafers; chemicals and gases; power and cooling]]

Austria is named on two of the seventeen chokepoint cards, and three of the 220 firms in the supplier list are based there.

-   [[#^photomasks-and-pellicles|Photomasks and Pellicles Extreme IMS Nanofabrication multi-beam mask writers, Vienna]]
-   [[#^substrates-and-pcbs|Substrates and PCBs Extreme AT&S, the only European advanced substrate maker of scale]]

[[#^suppliers|3 firms in the supplier list, led by photomasks; advanced packaging and OSAT; substrates and PCBs]]

Switzerland is named on one of the seventeen chokepoint cards, and three of the 220 firms in the supplier list are based there.

-   [[#^data-centers-and-power|Data Centers and Power High Hitachi Energy and ABB transformer and switchgear engineering]]

[[#^suppliers|3 firms in the supplier list, led by equipment subsystems and components; power and cooling]]

Thailand is named on one of the seventeen chokepoint cards, and one of the 220 firms in the supplier list is based there.

-   [[#^systems-and-networking|Systems and Networking High Chinese module makers' offshore transceiver plants]]

[[#^suppliers|1 firm in the supplier list, led by optics and photonics]]

All stages

### Stages, most concentrated first ^stages-most-concentrated-first

### Which countries supply which stages ^which-countries-supply-which

## Export Controls ^export-controls

Every rule since 2018, what can still be sold to China, and each firm's China sales.

-   No licenseNone needed.
-   Case by caseA license is required, and each application is judged on its own.
-   Presumption of denialA license is required and will normally be refused. An Entity List listing sits here.
-   ProhibitedNo license is available, or an outright ban.
-   PolicyMoney and tariffs; nothing stops a shipment.
-   SuspendedThe instrument is stayed until a date. The outcome beside it returns when the stay ends.

### China share of revenue, from company filings ^china-share-of-revenue

#### Lithography ^lithography-2

**ASML** NL · peak 36% in FY2024

15% 14% 26% 36% 29% FY2021 FY2025

#### Deposition & Etch ^deposition-etch

**SCREEN Holdings** JP · peak 42% in FY2025

31% 26% 21% 39% 42% 38% FY2021 FY2026

**Tokyo Electron** JP · peak 44% in FY2024

29% 28% 24% 44% 42% 34% FY2021 FY2026

**Lam Research** US · peak 42% in FY2024

35% 31% 26% 42% 34% 34% FY2021 FY2026

**Applied Materials** US · peak 37% in FY2024

33% 28% 27% 37% 30% FY2021 FY2025

**Veeco Instruments** US · peak 36% in FY2024

18% 19% 33% 36% 27% FY2021 FY2025

#### Metrology & Inspection ^metrology-inspection

**Camtek** IL · peak 55% in FY2021

55% 44% 47% 31% 49% FY2021 FY2025

**Nova** IL · peak 39% in FY2024

21% 28% 36% 39% 33% FY2021 FY2025

**KLA** US · peak 43% in FY2024

27% 29% 27% 43% 33% 30% FY2021 FY2026

**Onto Innovation** US · peak 25% in FY2022

19% 25% 17% 12% 7% FY2021 FY2025

#### Test ^test

**Advantest** JP · peak 32% in FY2023

32% 23% 19% FY2023 FY2025

**Teradyne** US · peak 17% in FY2021

17% 16% 12% 13% 14% FY2021 FY2025

#### Memory ^memory

**SK hynix** KR · peak 37% in FY2021

37% 27% 31% 24% 20% FY2021 FY2025

**Samsung Electronics** KR · peak 16% in FY2021

16% 12% 11% 15% 14% FY2021 FY2025

**Micron** US · peak 14% in FY2023

8.9% 11% 14% 12% 7.1% FY2021 FY2025

#### AI Accelerator Vendor ^ai-accelerator-vendor

**AMD** US · peak 25% in FY2021

25% 22% 15% 24% 22% FY2021 FY2025

**Nvidia** US · peak 26% in FY2022

23% 26% 21% 20% 19% 9.1% FY2021 FY2026

#### Design & EDA ^design-eda

**Cadence** US · peak 17% in FY2023

13% 15% 17% 12% 13% FY2021 FY2025

**Synopsys** US · peak 16% in FY2023

13% 16% 16% 16% 12% FY2021 FY2025

#### Advanced Packaging & OSAT ^advanced-packaging-osat

**BE Semiconductor Industries** NL · peak 38% in FY2021

38% 26% 36% 34% 35% FY2021 FY2025

#### Chemicals & Gases ^chemicals-gases

**Entegris** US · peak 21% in FY2024

16% 15% 16% 21% 21% FY2021 FY2025

The same figures as a table

Shares are computed from the absolute figures each firm filed. Firms count China differently: where the goods ship, where they are billed, or where the customer is based.

## How AI chips are made ^how-ai-chips-are

An introduction to the entire semiconductor supply chain.

17 paragraphs2,240 wordsabout 10 min

1.  01
    
    Chapter 01Stage 1 of 15
    
    ### Chip Design, EDA and IP
    
    Chip design turns an idea for a new chip into a complete blueprint. A chip holds billions of transistors, tiny electrical switches, and the blueprint fixes where each one sits and how it is wired to the others. The chip works in ticks, and a signal has to cross those wires within one tick, less than a billionth of a second. Software from three companies, Synopsys, Cadence and Siemens, lays out a plan like that, checks it and signs it off, and a chip factory accepts only designs that have passed those tools. The factory prints each layer of the design onto silicon through a stencil, and changing the plan after that costs a fresh set of stencils and several months. Withhold the software and no new chip can be designed.
    
    -   The market for chip design software and licensed circuit blocks was about $18B in 2025, with Synopsys, Cadence and Siemens EDA holding over 85% [source](https://newsletter.semianalysis.com/p/eda-market-primer "EDA Market Primer, SemiAnalysis, 2026-05-21")
    -   Synopsys reported $7.054B of revenue for fiscal year 2025, the twelve months to 31 October 2025, of which Ansys contributed $756.6M after the July close [source](https://www.sec.gov/Archives/edgar/data/883241/000119312525314200/d29055dex991.htm "SYNOPSYS INC, Form 8-K current report for the period ended 2025-12-10 (8-K), U.S. Securities and Exchange Commission (filing by SYNOPSYS INC), 2025-12-10")
    
    Who leadsSynopsys US _·_ Cadence US _·_ Siemens EDA DE
    
    **Extreme** [[#^chip-design-eda-and|Read the chapter]]
    
2.  02
    
    Chapter 02Stage 2 of 15
    
    ### Silicon and Wafers
    
    Every chip is built on a wafer, a thin round slice of silicon about 30 centimeters across that carries hundreds of chips at once. Making one starts with sand, which is silicon bound to oxygen. The sand is refined until, of every hundred billion atoms, fewer than one is anything other than silicon. The silicon is melted, a small seed crystal is lowered to the surface and drawn slowly back up, and the melt freezes onto it as one long cylinder, a single crystal with its atoms in one unbroken orderly pattern from end to end. Saws cut the cylinder into discs, and each disc is polished until its surface is flat to within a few atoms, right out to the edge. Only five companies in the world make these wafers to that standard, and none of them is American or Chinese.
    
    -   Worldwide silicon wafer shipments rose 5.8% to 12,973 million square inches in 2025 while revenue fell 1.2% to $11.4 billion [source](https://www.prnewswire.com/news-releases/semi-reports-2025-annual-worldwide-silicon-wafer-shipments-and-revenue-results-302683028.html "SEMI Reports 2025 Annual Worldwide Silicon Wafer Shipments and Revenue Results, PR Newswire, 2026-02-10")
    -   Five major suppliers supply the entire $11.4bn semiconductor silicon wafer market [source](https://www.siltronic.com/fileadmin/investorrelations/2026/Q1/20260429_Siltronic_InvestorPresentation__.pdf "FOUNDATION OF DIGITAL LIFE Investor Presentation, Siltronic, 2026-04-29")
    
    Who leadsShin-Etsu Handotai JP _·_ SUMCO JP _·_ GlobalWafers TW
    
    **High** [[#^silicon-and-wafers|Read the chapter]]
    
3.  03
    
    Chapter 03Stage 3 of 15
    
    ### Chemicals, Gases and Photoresist
    
    Photoresist is a coating that changes wherever light hits it. A machine spins a coat of it, thinner than a soap bubble, across the wafer. Light shines through a stencil onto the coat, and a liquid wash then takes away the parts the light reached. What remains is a pattern, and the next machine cuts that pattern into the wafer beneath, a step called etching. A few hundred other gases and liquids lay down layers, strip them off and clean the wafer between steps. All of them have to be clean to about one stray metal atom in every trillion. Each formula is approved for one factory and one product at a time, and a new supplier has to earn that approval from scratch, so a second source takes years. Nine tenths of the world's photoresist comes from Japan, and no factory can swap it out quickly.
    
    -   Japan holds about 90% of world semiconductor photoresist production, and China could not make EUV resists (as of 2021) [source](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf "The Semiconductor Supply Chain - Issue Brief, Center for Security and Emerging Technology (CSET), 2021-01-21")
    -   Japan Investment Corporation's vehicle took 84.36% of JSR at ¥4,350 a share in a tender offer that closed on 16 April 2024 [source](https://www.jiccapital.co.jp/en/news/.assets/E_20240417_JIC_JICC_PressRelease.pdf "April 17, 2024 Japan Investment Corporation, Japan Investment Corporation, 2024-04-17")
    
    Who leadsJSR JP _·_ Tokyo Ohka Kogyo JP _·_ Air Liquide FR
    
    **High** [[#^chemicals-gases-and-photoresist|Read the chapter]]
    
4.  04
    
    Chapter 04Stage 4 of 15
    
    ### Lithography
    
    Lithography prints the pattern of a circuit onto the wafer. A machine holds a stencil of one layer of the circuit up to a lamp and projects the image, four times smaller, onto the silicon. Light cannot draw a line much finer than its own wave, so the finer the lines, the shorter the wavelength of light needed to print them. Air soaks up the shortest light now in use, so the machine has to print in a vacuum. Only one company has ever built a machine that prints with it, and it is Dutch. Export controls are government rules on who a company may sell to. Every advanced chip passes through that firm's machines, so a rule aimed at it reaches all advanced chipmaking.
    
    -   ASML booked 48 EUV systems as revenue in 2025, versus 44 in 2024 and 53 in 2023 [source](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf "ASML 2025 Annual Report, ASML, 2026-02-24")
    -   ASML total net sales were EUR 32.7 billion in 2025 at a 52.8% gross margin [source](https://ourbrand.asml.com/m/419103cb23dfeaa4/original/asml-2025-annual-report-financial-performance-section.pdf "ASML 2025 Annual Report, ASML, 2026-02-24")
    
    Who leadsASML NL _·_ Nikon JP _·_ Canon JP
    
    **Extreme** [[#^lithography|Read the chapter]]
    
5.  05
    
    Chapter 05Stage 5 of 15
    
    ### Photomasks and Pellicles
    
    A photomask is the stencil that lithography prints from, one for each layer of a chip. The same plate prints its layer on wafer after wafer, so one plate shapes millions of chips. No glass lets the short light now in use pass through, so instead of a window the plate is a mirror, built up from about forty pairs of very thin layers, and the light bounces off it. A dark pattern drawn on top of the mirror soaks up the light wherever no line should print. Any speck of dust on the plate repeats on every wafer it prints. Two Japanese firms make almost all of those mirrors. A business almost nobody has heard of can hold up every advanced chip in the world.
    
    -   AGC calls itself the world's only maker of EUV mask blanks handling every step from glass material to coating, and expanded capacity by about 30% in 2025 under a METI supply-chain program [source](https://www.agc.com/en/news/detail/1203819_2814.html "AGC to Boost Production Capacity of EUVL Photomask Blanks, AGC, 2023-04-27")
    -   Hoya says it holds an exceptionally high share of the mask blank market and expects customers to move gradually to buying EUV blanks from more than one supplier [source](https://www.hoya.com/ir/2025/en/review/it.html "Information Technology Business | Review of Operations | HOYA REPORT 2025, HOYA")
    
    Who leadsAGC JP _·_ Hoya JP _·_ Lasertec JP
    
    **Extreme** [[#^photomasks-and-pellicles|Read the chapter]]
    
6.  06
    
    Chapter 06Stage 6 of 15
    
    ### Deposition and Etch
    
    Deposition and etch build the chip itself, one layer at a time. Deposition lays down a film a few atoms thick. Lithography prints a pattern on it. Etch then eats away everything the pattern does not protect, and the next film goes down on top. A chip takes more than a thousand of these rounds. Some of the holes the etch cuts are hundreds of times deeper than they are wide, the shape of a finger-wide shaft dropping through several floors, and the film has to coat them right to the bottom. The etch has to eat one material and leave the one beside it untouched. Four firms in America, Japan and the Netherlands make most of these machines, and China has come closer to matching them here than anywhere else.
    
    -   Producing one chip takes more than 1,000 process steps and 70 or more border crossings (CSET, 2021) [source](https://cset.georgetown.edu/wp-content/uploads/The-Semiconductor-Supply-Chain-Issue-Brief-1.pdf "The Semiconductor Supply Chain - Issue Brief, Center for Security and Emerging Technology (CSET), 2021-01-21")
    -   Global sales of chipmaking equipment reached $135.1B in 2025, up 15% from $117.1B in 2024, with wafer processing equipment up 12% (SEMI) [source](https://www.semi.org/en/SEMI-Reports-Global-Semiconductor-Equipment-Billings-Reached-135-Billion-in-2025 "SEMI Reports Global Semiconductor Equipment Billings Reached $135 Billion in 2025, Up 15% Year-on-Year, SEMI, 2026-04-07")
    
    Who leadsApplied Materials US _·_ Lam Research US _·_ Tokyo Electron JP
    
    **High** [[#^deposition-and-etch|Read the chapter]]
    
7.  07
    
    Chapter 07Stage 7 of 15
    
    ### Metrology and Inspection
    
    Metrology and inspection are the factory's quality control. Between the steps that build a chip, another machine looks the wafer over. It checks whether the lines are the right width, whether this layer landed squarely on the last one, and whether a speck of dirt has killed a circuit. An AI accelerator is the part built to run AI, and its main chip, the one that does the calculating, is one of the largest cut from a wafer. A bigger chip is a bigger target for a speck. On a chip that size, halving the stray specks lifts the share of working chips from about half to about seven in ten. One American firm sells seven times as many of those machines as its nearest rival, so a chip factory, or fab, cut off from it can buy every other tool and still not learn why its chips fail.
    
    -   Die yield is (1 + D0A/a) to the power minus a, with a of 3 to 4 for modern CMOS, so defect density and die area alone set the ceiling [source](https://web.ece.ucsb.edu/~parhami/docs_folder/f33-book-dep-comp-pt2.pdf "Behrooz Parhami, Dependable Computing: A Multilevel Approach, part 2, University of California, Santa Barbara, 2020-10-11")
    -   KLA became the largest supplier of process control tools for advanced wafer-level packaging in calendar 2025, adding 14 percentage points of share and growing that revenue about 70% [source](https://d1io3yog0oux5.cloudfront.net/_a357bfc9113388e37f3bfcb2ea2f0b64/klatencor/db/1117/10655/letter_to_shareholders/KLA+Shareholder+Letter+-+Q3+FY26.pdf "Letter to Shareholders Q3 Fiscal 2026, KLA Corporation, 2026-04-29")
    
    Who leadsKLA US _·_ Applied Materials US _·_ Lasertec JP
    
    **High** [[#^metrology-and-inspection|Read the chapter]]
    
8.  08
    
    Chapter 08Stage 8 of 15
    
    ### Transistors and the Front End
    
    The front end of a chip factory is the part that builds the transistors, the billions of tiny switches in every chip. Each switch is a valve. Current runs along a narrow strip of silicon called the channel, and a small voltage on a gate above the strip opens or shuts the flow. Shorter strips switch faster and more of them fit on a chip, but make the strip short enough and the valve stops sealing: current leaks through even when the gate is off, and the chip burns power doing nothing. The fix is to wrap the gate around all four sides of the strip, so it can squeeze the flow shut from every side, and that takes a long sequence of steps that have to run in exact order. Only three companies, TSMC, Intel and Samsung, can do it, a list so short that an can name every one of them.
    
    -   TSMC N2 entered volume production in 4Q25, its first nanosheet gate-all-around node [source](https://www.tsmc.com/english/dedicatedFoundry/technology/logic/l_2nm "2nm Technology, TSMC")
    -   TSMC N2P delivers 18% more speed at the same power, 36% less power at the same speed, 1.2x logic density and 1.15x chip density over N3E [source](https://www.tsmc.com/english/dedicatedFoundry/technology/platform_HPC_tech_advancedTech "HPC Platform – Advanced Technologies, TSMC")
    
    Who leadsTSMC TW _·_ Intel US _·_ Samsung Foundry KR
    
    **Extreme** [[#^transistors-and-the-front|Read the chapter]]
    
9.  09
    
    Chapter 09Stage 9 of 15
    
    ### Foundries and Fabs
    
    A foundry is a fab that makes chips for other companies. Those companies send in their designs, and the foundry runs them all through the same building on the same tools. The building costs tens of billions of dollars, and the air inside is cleaner than an operating room. Even so, a wafer crosses hundreds of machines over several months inside sealed boxes, never touching that air. No chip company sells enough of one product to fill a factory like that on its own, so the world shares a handful of them. TSMC runs the biggest, and all six of its largest plants sit in Taiwan, which is why one island's politics reaches the whole chip supply.
    
    -   7 nm and below was 77% of TSMC's wafer revenue in 2Q26, on revenue of $40.20 billion at a 67.7% gross margin [source](https://www.sec.gov/Archives/edgar/data/0001046179/000104617926000451/a2q26e_withguidancexfinal.htm "TAIWAN SEMICONDUCTOR MANUFACTURING CO LTD, Form 6-K report of foreign private issuer for the period ended 2026-06-30 (6-K), U.S. Securities and Exchange Commission (filing by TAIWAN SEMICONDUCTOR MANUFACTURING CO LTD), 2026-07-16")
    -   TSMC defines a GIGAFAB as a 300 mm fab running more than 100,000 wafers a month; it operates six, whose combined capacity exceeded 13 million 12-inch equivalent wafers in 2025 [source](https://www.tsmc.com/english/dedicatedFoundry/manufacturing/gigafab "GIGAFAB® Facilities, TSMC")
    
    Who leadsTSMC TW _·_ Intel Foundry US _·_ Samsung Foundry KR
    
    **Extreme** [[#^foundries-and-fabs|Read the chapter]]
    
10.  10
     
     Chapter 10Stage 10 of 15
     
     ### Memory and HBM
     
     High bandwidth memory, or HBM, is where an AI chip keeps the numbers it is working on, and it is built to hand them over fast. A memory maker stacks up to sixteen memory chips into a cube, drills holes straight down through the stack, and fills the holes with copper so that every layer is wired to the ones below. The cube then sits beside the processor, the chip that does the calculating. Stacking is the hard part, because each chip is ground so thin that the copper in its holes shows through its back, the finished cube has to fit under the plate that cools it, and one bad chip ruins the whole cube. Only SK hynix, Samsung and Micron have made it work, and a single line in an American export control reaches all three.
     
     -   HBM4 sets a 2,048-bit interface with 32 channels, 2 TB/s per stack at 8 Gb/s per pin, and up to 64 GB per stack [source](https://www.jedec.org/news/pressreleases/jedec%C2%AE-and-industry-leaders-collaborate-release-jesd270-4-hbm4-standard-advancing "JEDEC® and Industry Leaders Collaborate to Release JESD270-4 HBM4 Standard: Advancing Bandwidth, Efficiency, and Capacity for AI and HPC, JEDEC Solid State Technology Association, 2025-04-16")
     -   A single HBM stack's data path is 1,024 bits wide, which Micron counts as 32 independent channels (the JEDEC standard calls them 16 channels of two pseudo-channels each), 16 times wider than a standard DDR5 module's [source](https://www.micron.com/products/memory/hbm "High-bandwidth memory (HBM), Micron Technology")
     
     Who leadsSK hynix KR _·_ Samsung KR _·_ Micron US
     
     **Extreme** [[#^memory-and-hbm|Read the chapter]]
     
11.  11
     
     Chapter 11Stage 11 of 15
     
     ### Advanced Packaging
     
     Packaging joins finished chips into one component and mounts them on a base, called a substrate, wired almost as finely as the chips themselves. A lithography machine, which prints a chip's circuits, can cover only a rectangle about the size of a postage stamp in one shot, and a modern accelerator needs more circuit than fits in one, so it cannot be one chip. It is made as several pieces, set side by side on a shared slab of silicon and wired together through it, with the stacked memory a few millimeters away. Slab, chips and base all expand at different rates when heated, so the package can warp and its joints crack. Getting that right in large numbers is hard enough that nearly every AI accelerator is packaged by TSMC, in Taiwan.
     
     -   A scanner's maximum exposure field is 26 mm by 33 mm, or 858 mm2 [source](https://www.asml.com/en/products/euv-lithography-systems/twinscan-nxe3400c "TWINSCAN NXE:3400C, ASML")
     -   TSMC is now producing 5.5-reticle CoWoS, having certified it in 2025 and started volume production in 2026 [source](https://pr.tsmc.com/english/news/3302 "TSMC Debuts A13 Technology at 2026 North America Technology Symposium, TSMC, 2026-04-23")
     
     Who leadsTSMC TW _·_ ASE Technology TW _·_ Amkor US
     
     **Extreme** [[#^advanced-packaging|Read the chapter]]
     
12.  12
     
     Chapter 12Stage 12 of 15
     
     ### Substrates and PCBs
     
     A package substrate is the adapter between a chip and the circuit board under it. The chip's connections come out finer than a human hair; the board is wired in millimeters. The substrate is built up like plywood. A stiff core of glass cloth and resin sits in the middle. Thin sheets of epoxy film are pressed onto both faces, a laser burns holes through each sheet, and copper is plated into the holes to carry signals from one layer to the next. Every added layer is another set of holes that can fail. A handful of firms build these substrates, and the film and the glass cloth each come from a single Japanese supplier, so a shortage here stops shipping.
     
     -   TSMC's chief executive told the July 2026 earnings call that packaging capacity is so tight it now limits customers' growth [source](https://investor.tsmc.com/english/encrypt/files/encrypt_file/reports/2026-08/3e494f0c14dd0890f897aa044415e21d93486cc4/TSMC%202Q26%20Transcript.pdf "Q2 2026 Taiwan Semiconductor Manufacturing Co Ltd Earnings Call (Chinese, English) — edited transcript, LSEG StreetEvents (transcript of a TSMC earnings call), via TSMC, 2026-07-16")
     -   Ajinomoto Build-up Film was first adopted by a major semiconductor manufacturer in 1999, and Ajinomoto calls it the de facto standard insulating material for package development ever since [source](https://www.ajinomoto.co.jp/company/en/ir/event/business_briefing/main/01113/teaserItems1/01/linkList/00/link/3_ICT_E.pdf "Ajinomoto, Business Briefing: ABF-Based Growth Strategy in ICT, 12 June 2023, Ajinomoto, 2023-06-12")
     
     Who leadsAjinomoto JP _·_ Nitto Boseki JP _·_ Ibiden JP
     
     **Extreme** [[#^substrates-and-pcbs|Read the chapter]]
     
13.  13
     
     Chapter 13Stage 13 of 15
     
     ### Test and Assembly
     
     Before a can be sold, a machine has to put questions to it and check every answer. While the chips are still on the, thousands of needles press onto small metal pads on each one, send in signals and read what comes back; the marks any chip that answers wrong, and that chip goes no further. A modern glues together a dozen expensive pieces, and one bad piece throws away all of them. So the industry tests sooner, hotter and longer than it used to, to make a weak chip fail on the test bench before it reaches a finished product, and two firms, one Japanese and one American, sell most of the machines that do it.
     
     -   Advantest estimates its overall tester market share at about 65% in CY2025, with 66% of logic chip test (up about 10 points year on year) and about 60% of memory test [source](https://www.advantest.com/document/en/investors/ir-library/result/JE_BIZ_260427_note.pdf "Advantest, presentation notes for the FY2025 (year ended 31 March 2026) results briefing, 27 April 2026, Advantest, 2026-04-27")
     -   The CY2025 tester market was about $9.0 billion: $6.9 billion of logic chip testers, up about 68% year on year, and $2.1 billion of memory testers [source](https://www.advantest.com/document/en/investors/ir-library/result/JE_BIZ_260427_note.pdf "Advantest, presentation notes for the FY2025 (year ended 31 March 2026) results briefing, 27 April 2026, Advantest, 2026-04-27")
     
     Who leadsAdvantest JP _·_ Teradyne US _·_ ASE TW
     
     **High** [[#^test-and-assembly|Read the chapter]]
     
14.  14
     
     Chapter 14Stage 14 of 15
     
     ### Systems and Networking
     
     One AI chip is not enough to train a model. So seventy-two of them are wired together in a rack, a cabinet the size of a wardrobe, and run as one computer. Each chip sits on its own board and draws more than a thousand amps, several times the current a whole house is wired to carry. The chips have to swap results with each other all the time, and a copper wire can carry those signals only a few meters before they fade, so the longer links send them as light down glass fiber. Many companies can build the rack. Only a few can make the lasers that send the light, and that is the narrow point.
     
     -   NVLink 6 carries 3,600 GB/s per GPU, double NVLink 5's 1,800 GB/s and four times NVLink 4's 900 GB/s [source](https://www.nvidia.com/en-us/data-center/nvlink/ "NVLink & NVLink Switch for Advanced Multi-GPU Communication, Nvidia, 2026-04-20")
     -   A GB300 NVL72 rack holds 18 compute trays and 9 NVLink switch trays with 18 NVSwitch ASICs, drawing up to 142 kW [source](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html "System Hardware & Components, Nvidia")
     
     Who leadsNvidia US _·_ Broadcom US _·_ Foxconn TW
     
     **High** [[#^systems-and-networking|Read the chapter]]
     
15.  15
     
     Chapter 15Stage 15 of 15
     
     ### Data Centers and Power
     
     A data center's job is to feed electricity to the machines inside it and carry away the heat they give off. One rack of AI chips, a cabinet the size of a wardrobe, draws 142 kilowatts, and every watt of it comes back out as heat, more than air can carry away, so water is piped through the rack instead. A large training site already holds a hundred thousand chips, and the newest sites are planned in gigawatts. One gigawatt is the whole output of a large power station, and OpenAI's planned sites add up to more than nine of them by 2029. Getting that much electricity to the door is harder than putting up the building, because the transformers and heavy switches that connect a site to the grid, and the turbines that make the power, come from a few suppliers and take years to arrive.
     
     -   A GB300 NVL72 rack draws up to 142 kW, fed by eight 33 kW power shelves [source](https://docs.nvidia.com/enterprise-reference-architectures/nvl72-ai-factory/latest/components.html "System Hardware & Components, Nvidia")
     -   NVIDIA's 800-volt DC architecture is drawn for racks from 100 kW to over 1 MW, with megawatt racks from 2027, because the 54-volt distribution in today's racks hits physical limits past about 200 kW [source](https://developer.nvidia.com/blog/nvidia-800-v-hvdc-architecture-will-power-the-next-generation-of-ai-factories/ "NVIDIA 800 VDC Architecture Will Power the Next Generation of AI Factories, Nvidia, 2025-05-20")
     
     Who leadsGE Vernova US _·_ Hitachi Energy CH _·_ Siemens Energy DE
     
     **High** [[#^data-centers-and-power|Read the chapter]]
     
16.  16
     
     Chapter 16
     
     ### The Economics of AI Chips
     
     A bill of materials is the list of parts inside a product and what each one costs to build. For an AI accelerator, the processor itself, the chip that does the calculating, is the cheap part, about a seventh of the total. The stacked memory beside it is nearly half, and the packaging that wires the two together costs more than the chip. Three firms in the world make that memory and one Taiwanese firm does that packaging, so the costliest parts are also the scarcest, and that is where a government's rules bite hardest.
     
     -   A B200 costs about $6,400 to build, in a range of $5,700 to $7,300, and sells for $30,000 to $40,000 [source](https://epoch.ai/data-insights/b200-cost-breakdown "NVIDIA's B200 costs around $6,400 to produce, Epoch AI, 2025-12-10")
     -   High-bandwidth memory (HBM3E) is $2,900 of that $6,400, at $14 to $17 per gigabyte; the logic dies are $900 [source](https://epoch.ai/data-insights/b200-cost-breakdown "NVIDIA's B200 costs around $6,400 to produce, Epoch AI, 2025-12-10")
     
     [[#^the-economics-of-ai|Read the chapter]]
     
17.  17
     
     Chapter 17
     
     ### Geopolitics
     
     An export control is a rule that makes a sale need the government's permission. The government names an item and a buyer, and from then on its own companies must hold a license before they ship that item to that buyer. The American government stretches the rule to cover goods made abroad with American technology. Few governments can use such a rule to much effect, because it works only when their own firms sell something the buyer cannot get elsewhere. The machines, software and chemicals that make an advanced chip come from a short list of firms in the United States, the Netherlands, Japan and South Korea. China can copy the simpler machines within a few years. It cannot yet copy the machine that prints the finest circuits, the chemistry that machine needs, or high-bandwidth memory, the stacked memory beside an AI chip.
     
     -   Taiwan's foundries hold 78% of the global foundry market on the Taiwan Semiconductor Industry Association's 2025 count; the 92% often quoted for the most advanced chips is a February 2024 US International Trade Commission figure that the same Stimson explainer relays [source](https://www.stimson.org/2025/why-taiwan-fears-america-first-risks-eroding-its-silicon-shield/ "Why Taiwan Fears ‘America First’ Risks Eroding Its ‘Silicon Shield’, Stimson Center, 2025-10-10")
     -   SK hynix's July 2026 US prospectus puts Korean suppliers at 82.5% of 2025 HBM revenue, SK hynix 63.2 and Samsung 19.3, and at 76.9% in the first quarter of 2026; the filing relays IDC's figures [source](https://www.sec.gov/Archives/edgar/data/0002120882/000119312526299963/d32785d424b4.htm "SK hynix Inc., Form 424B4 prospectus for the period ended 2026-07-10 (424(B)(4)), U.S. Securities and Exchange Commission (filing by SK hynix Inc.), 2026-07-10")
     
     [[#^geopolitics|Read the chapter]]
     

## Glossary ^glossary

Every term, firm, chip and country, with the passages that use them.

Try

15 CFRCFR, Code of Federal Regulations, 15 CFR 742.6, part 742, part 740, part 734, supplement no. 5 to part 740, supplement no. 5

The Code of Federal Regulations is the standing text of US rules, sorted into titles and parts. Title 15 holds the Export Administration Regulations: part 734 says what is subject to them, part 740 lists the license exceptions and, in its supplement no. 5, the nineteen favored destinations, and part 742 sets the licensing policy for each control.

A rule that was announced in the Federal Register lives on in the CFR, which is why the unenforced Diffusion rule still binds.

[[#^geopolitics|Read it in Geopolitics →]]

300 mm300-millimeter, 12-inch, 12-inch equivalent, 200 mm, 8-inch, 8-inch-equivalent, 450 mm, 150 mm

300 mm is the diameter of the standard wafer, about twelve inches. Older fabs run 200 mm, or 8-inch, wafers, which carry less than half as many chips. The industry has stayed at 300 mm since 2002 and abandoned the move to 450 mm.

Every leading-edge chip is made on 300 mm, and 300 mm wafers carry 99.7 percent of capacity at 45 nm and below.

[[#^silicon-and-wafers|Read it in Silicon and Wafers →]]

3A0903A090.a, 3A090.b, 3A090.c, 4A090, 4A090.a, ECCN 3A090, ECCN 4A090

3A090 is the entry in the US export control list that covers advanced AI chips, defined by their total processing performance and performance density; 4A090 covers the computers built from them. Its part c, added in December 2024, covers high bandwidth memory. A chip inside 3A090.a needs a license for China and, since 2025, for most of the world.

Every chip on the AI Chips page is placed by whether it falls inside 3A090.a.

[[#^geopolitics|Read it in Geopolitics →]]

3B0013B090, 3B001.c.1, 3B001.d.9, 3B001.d.10, 3B001.d.5, 3D991, 3E991

3B001 and 3B090 are the entries in the US export control list that cover chipmaking equipment, written as process specifications: an etch tool that cuts sideways, a deposition tool that reaches 200-to-1 holes. The related 3D and 3E entries cover the software and know-how that go with the tools.

The design-software letters of May 2025 cited 3D991 and 3E991, and the tool rules of 2023 and 2024 added entry after entry under 3B001.

[[#^geopolitics|Read it in Geopolitics →]]

ABFAjinomoto Build-up Film, build-up film, ABF build-up film, ABF substrate, ABF substrates

A sheet of epoxy resin about a hundredth of a millimeter thick, laid over the copper wiring of a chip's base board to insulate it before the next layer of wiring goes on. It comes from the Japanese food company Ajinomoto, which developed it out of its amino acid chemistry.

One firm supplies more than 95 percent of it, TSMC names it alongside memory as a limit on AI supply, and Ajinomoto's next new plant will not operate until 2032.

[[#^substrates-and-pcbs|Read it in Substrates and PCBs →]]

acceleratorAI accelerator, XPU, accelerators

A chip built to do the one kind of arithmetic machine learning needs, multiplying large grids of numbers, far faster than a general-purpose processor can. Nvidia's graphics processors, Google's Tensor Processing Units and Amazon's Trainium are all accelerators.

Accelerators are what the whole supply chain is for, and the unit that export licenses are granted or refused for.

advanced packaging2.5D packaging, 3D packaging, 2.5D, 2.5D work, advanced packaging plants

The steps that assemble several finished chips into one component, sitting side by side or stacked, wired together closely enough to behave like a single larger chip. Ordinary packaging only puts one chip into a protective case with contacts on the bottom.

The second tightest bottleneck in the chain after lithography. In 2025 it capped how many AI accelerators could be built; transistor supply did not.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

Affiliates Ruleaffiliates rule, 50 percent rule, affiliates of listed entities

The Affiliates Rule extended the Entity List to any company at least half owned by a listed firm, anywhere in the world, so that a listed company could not buy through a subsidiary. It took effect on 29 September 2025 and was suspended for a year six weeks later.

It is stayed to 9 November 2026, and its return would reach the subsidiaries that toolmakers still sell to.

[[#^geopolitics|Read it in Geopolitics →]]

AI Diffusion ruleAI Diffusion, diffusion rule, Framework for Artificial Intelligence Diffusion, AI Diffusion framework

The AI Diffusion rule, published on 15 January 2025, required a license to ship the most capable AI chips anywhere in the world, then opened exceptions: unlimited to nineteen allies, capped volumes elsewhere, nothing to China. It also controlled the weights of frontier AI models.

Four months later BIS said it would leave the rule unenforced, and it withdrew none of the text, so its license requirement and exceptions still stand.

[[#^geopolitics|Read it in Geopolitics →]]

ALDatomic layer deposition

A way of coating a chip roughly one atomic layer at a time. Each pulse of gas sticks to the surface and then stops once the surface is covered, so the film ends up the same thickness on the floor and on the walls of a hole hundreds of times deeper than it is wide.

Atomic layer deposition is what makes stacked memory and wrap-around transistors possible, and US export rules name it directly. It is the one tool category where Chinese suppliers still hold under 1 percent of the market.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

ArFargon fluoride, argon fluoride laser, 193 nm, 193-nanometer

ArF is argon fluoride, the gas mixture inside the laser that gives deep ultraviolet scanners their 193-nanometer light. An ArF scanner, dry or immersion, prints most of the fine layers on any chip made without extreme ultraviolet.

ArF immersion was 42 percent of ASML's system sales in 2025, and it is the tier that China's domestic scanner effort is copying.

[[#^lithography|Read it in Lithography →]]

ASICapplication-specific integrated circuit, custom silicon, ASICs, custom accelerator, custom accelerators, custom chip, custom AI silicon, custom AI ASICs

A one-customer chip, designed for a single job and never sold on the open market. Google's Tensor Processing Unit and Amazon's Trainium are chips of this kind; an Nvidia part sold to any customer is not.

Custom chips are how the largest cloud buyers try to escape Nvidia's pricing, and roughly 95 percent of the work of designing them alongside the buyer runs through just two firms, Broadcom and Marvell.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

ATEautomated test equipment, tester

The machine that connects to a finished chip, feeds it millions of test patterns and checks whether the answers coming back are right. It is the only stage of chip manufacturing that runs electricity through the product.

Advantest and Teradyne hold about 80 percent of this market, and changing tester vendor means rebuilding a customer's whole production test environment, so share moves slowly.

[[#^test-and-assembly|Read it in Test and Assembly →]]

back endback end of line, BEOL, back-end, back-end fabs, back-end tools

Inside a fab, the back end of line is the second half of making a chip, the dozen or more layers of copper wiring stacked above the transistors. In the industry at large, the back end means everything after the wafer leaves the fab: grinding, dicing, packaging and test.

Wiring is now as hard as the transistor, and the back end is the part of the chain where China is closest to self-sufficiency.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

backside power deliverybackside power, backside vias, PowerVia, Super Power Rail, backside power network

Backside power delivery grinds a finished wafer thin and builds the wires that carry power on its underside, so the wiring above the transistors carries only signals. Power arrives through holes drilled up from below, clear of the crowded top.

Intel ships it on 18A and TSMC on A16; it is one of the few remaining ways to make a chip faster without shrinking the transistor.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

base diebase chip, base logic die, logic base die, HBM base die

The base die is the bottom chip of an HBM stack, the one that talks to the processor on behalf of the memory dies stacked above it. From HBM4 it is a logic chip made in a foundry.

That change gives TSMC a share of a product it does not make, and ties HBM4 supply to foundry capacity.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

baseboardbaseboards, SXM, OAM, accelerator module, HGX, HGX baseboard

A baseboard is the large circuit board that eight accelerator modules bolt onto inside a server, carrying their power and the switch chips that let them reach each other at full speed. Nvidia's module is called SXM and its baseboard HGX; the open-standard equivalents are OAM and UBB.

Rack-scale systems such as the NVL72 have no baseboard and wire 72 GPUs together directly.

[[#^systems-and-networking|Read it in Systems and Networking →]]

BGAball grid array, FC-BGA, flip-chip BGA

A way of joining a packaged chip to a circuit board using a grid of small solder balls across the underside in place of a row of pins around the edge. Heating the assembly melts every ball at once into a permanent joint.

The number and spacing of those balls limit how much current and how many signals can reach a package, which matters when a single AI accelerator draws more than a thousand amps.

[[#^substrates-and-pcbs|Read it in Substrates and PCBs →]]

Big FundNational Integrated Circuit Industry Investment Fund, National Integrated Circuit Fund, third chip fund, China's third chip fund

The Big Fund is the nickname for China's National Integrated Circuit Industry Investment Fund, the state vehicle that puts government money into Chinese chip firms. Its third round, raised in May 2024, came to 344 billion yuan, about $47 billion.

Cumulative state funding since 2014 is about triple the CHIPS authorization, and it has bought a tool industry and no leading-edge node.

[[#^geopolitics|Read it in Geopolitics →]]

bill of materialsBOM

The itemized list of every purchased part in a finished product and what each part cost, the way a builder's invoice prices lumber, wiring and fixtures separately.

On an AI accelerator the memory line alone is roughly half of manufacturing cost, so the bill of materials shows which suppliers capture the money a buyer spends.

[[#^the-economics-of-ai|Read it in The Economics of AI Chips →]]

BISBureau of Industry and Security, part of the US Department of Commerce

The US government office that decides which technologies may be exported, to whom, and on what conditions. It writes the rules, issues the licenses and brings the enforcement cases.

Almost every restriction on selling AI chips or chipmaking tools to China is a bureau rule, and the bureau can change a threshold with a Federal Register notice, with no act of Congress needed.

[[#^geopolitics|Read it in Geopolitics →]]

burn-inburn in, wafer-level burn-in, burn-in test

Burn-in runs a chip hot and under power for hours so that anything that would have failed in its first months fails now, before the part is shipped. It used to happen after packaging; for AI chips it is moving back onto the wafer.

One weak die in a package of a dozen expensive parts scraps all of them, so burn-in now protects everything else in the package.

[[#^test-and-assembly|Read it in Test and Assembly →]]

busbarbusbars, copper busbar, copper busbars

A busbar is a thick bar of solid copper that carries very large currents down the back of a rack to the boards that need them, doing the job a cable would melt trying to do. The bar feeding one AI rack weighs about 200 kilograms.

Nvidia's move to 800-volt distribution exists to push more power through the same copper and retire those bars.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

capexcapital expenditure, capital spending

Money a company spends on long-lived physical assets such as buildings, machines and servers, as distinct from salaries and other running costs.

The five largest cloud companies spent $448 billion of capex in 2025 and have told investors to expect more in 2026, and that is the number every firm in this chain plans against.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

case-by-case reviewcase by case, case-by-case, reviewed case by case

Case-by-case review means a license is required and each application is judged on its own, with no presumption either way. Since January 2026 the H200 and MI325X are reviewed this way for China, with conditions attached to each approval.

It is the middle setting between an open market and a presumption of denial, and it is where the current settlement sits.

[[#^geopolitics|Read it in Geopolitics →]]

chipchips, microchip, microchips, semiconductor chip

A chip is a small rectangle of silicon, usually smaller than a fingernail, that carries a complete electronic circuit made of billions of transistors. It is cut from a wafer after the circuit has been built up on it layer by layer.

Everything on the site is about how these rectangles get made, and who can stop the making.

[[#^silicon-and-wafers|Read it in Silicon and Wafers →]]

chipletchiplets

One of several smaller pieces that a chip has been deliberately split into, each manufactured separately and then wired back together inside a single package. A chip built this way is a house assembled from prefabricated rooms.

Splitting a design raises yield and lets a firm mix manufacturing processes, but it pushes the difficulty into packaging, which is the more constrained stage.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

CHIPS ActCHIPS and Science Act, CHIPS incentives, CHIPS money, CHIPS Act grants, CHIPS authorization, CHIPS Act support, CHIPS award

The CHIPS and Science Act, passed in August 2022, authorized about $52.7 billion of US federal money for chip factories at home, most of it as grants to firms building fabs and plants. By July 2025 $30.9 billion had been awarded to 19 companies, and a condition of each grant bars the recipient from expanding in China.

TSMC's Arizona commitment alone, at $265 billion, is now five times the whole authorization.

[[#^geopolitics|Read it in Geopolitics →]]

chokepointchokepoints

A step in the supply chain where so few firms or countries can do the work that losing one of them stops everybody. The term comes from Georgetown's Center for Security and Emerging Technology, which mapped the chip industry segment by segment to find the ones with only one or two suppliers.

Chokepoints are where a policy has effect, and where one sanction or one factory fire reaches the whole industry.

CMPchemical mechanical polishing, chemical mechanical planarization, polishing slurry, polishing slurries, slurry, slurries, CMP slurry, CMP pads, planarization

After each new layer goes onto a wafer, its surface is rubbed flat again with a pad and a liquid full of fine grit, the slurry. The step is called chemical mechanical polishing, or CMP. Without it the next layer would be printed on a surface too bumpy to focus on.

A chip takes dozens of these polishes, and the slurry for each is qualified for one layer at one fab, which is why a $790 million slurry market has only two leaders.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

co-packaged opticsco-packaged, co-packaging, CPO, plug-in modules, plug-in optics

Co-packaged optics puts the lasers and light-to-electricity converters onto the switch chip's own package instead of into plug-in modules at the front of the box. The electrical path shrinks from centimeters to millimeters, which cuts the power the optics burn by about 70 percent.

Optics dominate network power at 800 gigabits and above, so both switch vendors are moving to it during 2026.

[[#^systems-and-networking|Read it in Systems and Networking →]]

coater/developercoater-developer, coater and developer, coater/developer track, track tool, track tools

A coater/developer, or track, is the machine that spins a thin coat of photoresist onto the wafer before it enters the scanner and washes away the exposed parts after it comes out. It is bolted to the scanner and every layer passes through it twice.

Tokyo Electron holds 91 percent of the market, one of the highest shares in the tool industry.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

coefficient of thermal expansionCTE, thermal expansion, expansion mismatch, low-CTE

The coefficient of thermal expansion is how much a material swells for each degree it warms. Silicon barely moves; epoxy moves several times more. Bolt the two together, heat them, and the package bends.

Matching expansion across die, bridge, interposer and substrate is what warpage control means, and it gets harder as packages grow.

[[#^substrates-and-pcbs|Read it in Substrates and PCBs →]]

compute thresholdtraining compute threshold

A limit set on the amount of arithmetic used to train an AI model. It counts operations, whichever chips run them. The 2023 US executive order on AI set its reporting line at "any model that was trained using a quantity of computing power greater than 10^26 integer or floating-point operations" (Executive Order 14110, section 4.2(b)(i), 88 FR 75191). The same number became an export control in January 2025: ECCN 4E091 covers "'Parameters' for an artificial intelligence model trained utilizing 10^26 or more 'operations'", and 15 CFR 742.6(a)(13) requires a license for them to every destination worldwide. Europe drew its line ten times lower, at a cumulative training run "greater than 10^25" floating point operations, in Article 51(2) of the EU AI Act.

Every other control threshold measures a chip. This one measures the model the chips train, which is the only place the rules reach a capability itself. The two numbers also disagree by a factor of ten, and Article 51(3) lets the European Commission move its figure by delegated act, so the model-level line is the one most likely to shift.

[[#^geopolitics|Read it in Geopolitics →]]

Concentrationconcentration band

A four-band judgment of how many firms could credibly supply a stage today, taken at the narrowest step inside it. Extreme means three or fewer, or one firm holding more than half the stage. High means four to six, with the top two taking most of the revenue. Moderate means seven or more, none of them dominant. Low means many, with the scarce input something another industry sells at volume. Where a figure exists for the top country's share of the segment, it serves as a second check, and the supplier count wins when the two disagree.

The fewer the firms that can do a stage, the more one accident or one license decision moves the whole chain.

consigneeconsignees, named consignee, named consignees, ultimate consignee

The consignee is the party a shipment is sent to, the name on the export license. A named consignee, such as G42 in the United Arab Emirates, can receive controlled chips on the terms attached to its own name.

The 2026 UAE rule attaches its terms to a list of consignees, so the deal follows the buyer across borders.

[[#^geopolitics|Read it in Geopolitics →]]

Country GroupsCountry Group, Country Group D:5, D:5, A:5, D:1, D:3, D:4, arms-embargoed countries

The groups that US export rules sort the world's countries into, published as supplement no. 1 to 15 CFR part 740. A:5 and A:6 are close partners; D:1, D:4 and D:5 are the national security, missile technology and arms-embargoed groups; E:1 and E:2 are the most restricted. A country can sit in several at once, and the license requirement usually turns on which.

The license rule for AI chips is written in country groups: a license is needed for D:1, D:4 and D:5 destinations that are not also A:5 or A:6 (15 CFR 742.6(a)(6)). Moving the UAE into A:5 in July 2026 changed its position without naming it in the rule.

[[#^geopolitics|Read it in Geopolitics →]]

CoWoSchip on wafer on substrate

TSMC's method for mounting logic chips and memory stacks side by side on a shared slab of silicon, then mounting that slab on a rigid base board. Nearly every high-end AI accelerator is built this way.

CoWoS capacity was the practical ceiling on AI accelerator output through 2025, and Nvidia has booked more than half of TSMC's 2026 to 2027 expansion.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

critical dimensioncritical dimensions, CD, CD-SEM, critical-dimension, line width, line-width, line widths

The critical dimension is the width of the finest printed feature on a layer, the number a lithography and etch step is judged by. A CD-SEM is an electron microscope built to measure it across a wafer without cutting anything.

Hitachi holds about 69 percent of CD measurement, one of the few tool families Japan leads.

[[#^metrology-and-inspection|Read it in Metrology and Inspection →]]

CVDchemical vapor deposition, PECVD, plasma-enhanced chemical vapor deposition, MOCVD, CVD precursor, precursor, precursors

Chemical vapor deposition, or CVD, grows a film by flowing gases over a hot wafer so they react on its surface and leave a solid layer behind. The plasma-enhanced version, PECVD, runs cooler. The gases used are called precursors.

Along with etch, CVD is the volume business of a fab and the segment where Chinese toolmakers have gained most.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

de minimis

The share of controlled American content a foreign-made item may contain before US export rules, the EAR, apply to it. Under 15 CFR 734.4 the general threshold is 25 percent of the item's value, and 10 percent for the most restricted destinations. Above the line the item is caught; below it, it is not.

It is the ordinary way an item leaves American jurisdiction, and the reason the foreign direct product rules were written: those rules ignore the percentage altogether. There is no de minimis at all for the advanced-node equipment named in 15 CFR 734.4(a)(3).

[[#^geopolitics|Read it in Geopolitics →]]

defect densityD0, defects per square centimeter

The average number of chip-killing flaws per square centimeter of processed wafer. It is a fab's quality score, inferred from how many chips come out working.

Yield falls steeply with die area multiplied by defect density, so on the reticle-sized dies AI chips use, halving defect density nearly doubles the number of saleable parts.

[[#^metrology-and-inspection|Read it in Metrology and Inspection →]]

denial order

An order from BIS that shuts a named party out of trade in US-controlled items, as a penalty. It is a punishment, and no license policy is involved. Under 15 CFR 764.3 it suspends or revokes the party's outstanding licenses and bars exports, reexports and in-country transfers of any item subject to the EAR to or by that party. There is no application to file. Orders can be issued outright or suspended and later activated.

It is the only instrument that stops trade absolutely. The order activated against ZTE in April 2018 halted most of the company's production within weeks and was terminated 89 days later on settlement (83 FR 17644; 83 FR 34825).

[[#^geopolitics|Read it in Geopolitics →]]

deposition

Adding a layer of material to a wafer, either by knocking atoms off a solid target so they land on the surface, or by reacting gases at the surface so a film grows there. It is how the insulators, the wires and the parts of each transistor are built up.

Deposition and etch are the volume business of a fab, dominated by Applied Materials, Lam Research and Tokyo Electron, and they are where Chinese toolmakers have gained the most share.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

dicingwafer dicing, dicing saw, dicing saws, grinding, wafer grinding, grinders, wafer grinders, thinning, wafer thinning

Dicing cuts a finished wafer into its individual dies with a diamond saw or a laser. Grinding, done first, thins the wafer from the back, sometimes until it is a few hundredths of a millimeter thick so it can be stacked.

Disco of Japan dominates both steps, and the newest saws handle rectangular panels as well as round wafers.

[[#^test-and-assembly|Read it in Test and Assembly →]]

diesingular of dice, dies

One rectangular chip cut out of a wafer. Hundreds are printed side by side on the same disc and then sliced apart, and each separated rectangle is a die.

Cost, yield and export thresholds are all reckoned per die, and AI accelerators use among the largest dies in production, which makes every defect far more expensive.

[[#^silicon-and-wafers|Read it in Silicon and Wafers →]]

dielectricdielectrics, dielectric etch, dielectric properties, insulator, insulating layer

A dielectric is an insulator: a material that does not conduct, such as the glassy oxides and nitrides between a chip's wires or the epoxy in a package substrate. Dielectric etch cuts holes and trenches through those insulating layers so the wires can be laid in.

How much signal a dielectric absorbs sets how fast a substrate or circuit board can run, which is why laminate suppliers matter to AI systems.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

DRAMdynamic random-access memory

A computer's main working memory. Each bit is a charge held in a microscopic capacitor that leaks, so the whole chip has to be refreshed thousands of times a second and forgets everything when the power goes off.

Three firms make nearly all of it, and their decision to convert capacity to AI memory pushed ordinary memory contract prices up more than 90 percent in a single quarter of 2026.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

DUVdeep ultraviolet, deep-ultraviolet, DUV scanner, DUV scanners, DUV tools

Chipmaking light with a wavelength of 248 or 193 nanometers, produced by a gas laser. Flooding the gap above the wafer with ultrapure water bends the light further and sharpens the printed image, which is called immersion.

Immersion deep ultraviolet is the most advanced lithography China can buy or build, which is where Dutch export licensing draws its line.

[[#^lithography|Read it in Lithography →]]

EARExport Administration Regulations

The body of US rules that governs the export of commercial goods, software and technology, including items with both civilian and military uses, written and enforced by the Bureau of Industry and Security. They run from 15 CFR part 730 to part 774: part 734 sets what they cover, part 742 the license requirements, part 744 the end-use and end-user controls, part 740 the exceptions and part 764 the penalties.

Almost every American export rule on chips and chip tools amends these regulations. They are changed by a notice in the Federal Register, with no act of Congress, which is why a threshold can move in a week.

[[#^geopolitics|Read it in Geopolitics →]]

EAR99

The label for an item that falls under US export rules but is not named on the Commerce Control List, the catalog of controlled items, from 15 CFR 734.3(c). It is a residual category with conditions: an EAR99 item still needs a license if it is going to a listed party or a controlled end use.

Most of what a chip plant buys is EAR99. It is the answer to "do I need a license?" for the great majority of shipments, and the reason the end-user controls in part 744 matter more than the classification for many exporters.

[[#^geopolitics|Read it in Geopolitics →]]

ECCNExport Control Classification Number

The catalog number that US export rules assign to a controlled item, rather like a customs tariff code for security-sensitive technology. Number 3A090 covers advanced computing chips and 3B001 covers chipmaking equipment.

An item's classification number decides whether it needs a license, so the technical thresholds written into each number are where the policy takes effect.

[[#^geopolitics|Read it in Geopolitics →]]

EDAelectronic design automation, chip design software

The software that turns a description of what a chip should do into the exact pattern of shapes to be printed on silicon, and proves the result will work before anyone commits money to masks and wafers.

Three vendors sell every complete design flow used at the leading edge, which is why stopping their sale to China in May 2025 took three letters and no lead time.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

electron beamelectron-beam, e-beam, electron beams, multi-beam, multibeam, e-beam inspection, electron-beam metrology

An electron beam is a stream of electrons focused to a spot far smaller than any spot of light. Fabs use it to write the pattern onto a photomask, to inspect wafers for defects light cannot see, and to measure line widths. A multi-beam tool fires thousands of beams at once because a single beam is slow.

Only two firms make the multi-beam writers that cut EUV masks, and the December 2024 rule controls any inspection tool using two or more beams.

[[#^photomasks-and-pellicles|Read it in Photomasks and Pellicles →]]

electronic-gradeelectronic grade, semiconductor-grade, semiconductor grade, solar-grade, solar grade, eleven nines

Electronic-grade silicon is pure enough for chips: fewer than one stray atom in a hundred billion, sometimes written as eleven nines. Solar-grade silicon is a thousand times dirtier, fine for a solar panel and useless for a transistor. The two grades come from different plants and different suppliers.

The line between the grades is the line between a Chinese commodity market and a German, American and Japanese one.

[[#^silicon-and-wafers|Read it in Silicon and Wafers →]]

end-use and end-user controlsend user, end users, end-user, end use, military end user

Export rules that turn on who the buyer is and what they will do with the item, whatever the item is. The same tool can ship freely to one customer and need a license that will be refused for another.

These controls reach past the product to the customer, so a company can lose access because of who owns it or what its site produces, as when US rules were extended to firms majority owned by listed entities.

[[#^geopolitics|Read it in Geopolitics →]]

Entity Listentity-list, Entity-Listed, Entity List additions, listed entity, listed entities, listed firm, listed firms

A published list of foreign companies, institutes and individuals that need a license before anyone anywhere, American or foreign, may send them an item subject to the EAR. Each entry states its own license review policy, so a listing is not one uniform outcome: most carry a presumption of denial, meaning the license will normally be refused; SMIC's is case by case except for items uniquely capable of production at 10 nanometers and below. It is supplement no. 4 to 15 CFR part 744, and the license requirement is in 15 CFR 744.11.

The fastest and simplest instrument Washington has: it names an organization. Since September 2025 a listing has reached companies the listed firm half owns, though that extension is stayed to 9 November 2026 (90 FR 50857).

[[#^geopolitics|Read it in Geopolitics →]]

epitaxyepitaxial, epitaxial wafer, epitaxial wafers, epitaxial layer, epi

Epitaxy grows a fresh layer of crystal on top of a wafer, atom by atom, so the new layer continues the crystal beneath it with almost no flaws. An epitaxial wafer is a plain wafer with that extra layer, and the transistors are built in that layer.

AI chips are built on epitaxial wafers because a big die cannot afford the defects a plain slice carries, which is where the wafer makers earn their money.

[[#^silicon-and-wafers|Read it in Silicon and Wafers →]]

etchetching, etched, etches, etcher, etchers, dry etch

Removing material from a wafer wherever the printed pattern says it should not be, usually by turning a gas into a plasma whose ions and fragments eat one material while leaving the material beside it alone.

Stacked memory and wrap-around transistors need holes far deeper than they are wide, which is why US rules control etch tools by hole shape and selectivity.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

EthernetUltra Ethernet, Spectrum-X, Spectrum-X Ethernet, Tomahawk, Ethernet switch

Ethernet is the ordinary networking standard of offices and the internet, now made fast and reliable enough to link the servers of an AI cluster. The switch chips at its heart, such as Broadcom's Tomahawk, route traffic between thousands of accelerators.

Ethernet took the scale-out layer back from InfiniBand on raw capacity, and Broadcom sells the chips to everyone.

[[#^systems-and-networking|Read it in Systems and Networking →]]

EUVextreme ultraviolet, extreme-ultraviolet, EUV scanner, EUV scanners, extreme ultraviolet lithography

Chipmaking light at a wavelength of 13.5 nanometers, made by dropping molten tin into a vacuum and hitting it with a laser 100,000 times a second to create a plasma hotter than the surface of the sun. Everything absorbs this light, including air and glass, so the machine runs in vacuum and every lens has to be a mirror.

One company, ASML, makes every extreme ultraviolet machine on Earth, none has ever been sold to China, and no leading-edge logic or advanced memory process runs without one.

[[#^lithography|Read it in Lithography →]]

export controlexport controls, export licensing, export license, export licenses, export licence, export licences, export-control

An export control is a rule that makes a sale need the government's permission. The government names an item and a buyer, and from then on its own companies must hold a license before they ship that item to that buyer. The United States stretches the rule to goods made abroad with American technology.

It works only when the seller's firms make something the buyer cannot get elsewhere, which is the condition the rest of this book documents.

[[#^geopolitics|Read it in Geopolitics →]]

fabfabrication plant, wafer fab, fabs, chip factory, chip factories

The factory where wafers are processed into chips. It is a cleanroom with a second building's worth of pumps, gas cabinets and water treatment underneath it, and a leading-edge one costs $15 to $25 billion and takes four to six years to build.

Fab construction is the slowest part of any reshoring plan and the one that needs the most capital, which is why subsidy programs on three continents target it and why the capacity they buy arrives late this decade.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

fabless

A chip company that designs and sells chips but owns no factory, paying a contract manufacturer, a foundry, to make them. Nvidia, AMD, Apple, Qualcomm and Broadcom all work this way.

The fabless model concentrates manufacturing in a handful of foundries, so a designer's supply, cost and geographic exposure are set by a company it does not control.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

FinFETfin field-effect transistor

A transistor whose channel, the strip that current flows through, is stood on edge like a shark fin, so that the gate, the electrode that switches the current, wraps around three of its sides instead of resting on one. More contact means firmer control and less leakage when the switch is meant to be off.

FinFET was the standard transistor shape from roughly 2011 until 2025, and US export rules still use 16 nanometer FinFET production as one threshold for what counts as an advanced fab.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

FLOPSfloating point operations per second, TFLOPS, PFLOPS, FLOP, teraflops

A count of how many arithmetic operations on decimal numbers a chip can perform each second, the way horsepower counts an engine's output.

The standard unit of AI compute and the basis of export thresholds, but only comparable between chips when the number format behind it is stated.

foreign direct product ruleFDPR, FDP rule, foreign-produced direct product rule, direct product rule, foreign-produced item rules, foreign-produced item rule, foreign-produced item

A US rule that puts a foreign-made item under American control when two tests are both met. The first is about the product: the item was made directly from specified US technology or software, or in a plant that was. The second is about the destination: the item is going somewhere, or to someone, the rule names. Both halves are needed. The mechanics are in 15 CFR 734.9.

The rule is what makes US controls extraterritorial. Without it a listed buyer could order the same chip from a supplier outside America; with it, a chip made in Taiwan on American tools for a listed Chinese firm needs a US license.

[[#^geopolitics|Read it in Geopolitics →]]

foundrypure-play foundry, contract chipmaker, foundries, pure-play, pure play, pure-play model, contract chipmaking

A factory business that manufactures chips designed by other companies and promises never to compete with them. TSMC created the model in 1987, and it worked because no single design house sells enough chips to fill a modern fab.

TSMC took about 73 percent of foundry revenue in 2026 and nearly all leading-edge production, so one company's capacity plan sets the world's supply of AI chips.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

FP8 and FP48-bit and 4-bit floating point, FP8, FP4, FP16, BF16, INT8, number formats

Ways of writing a number using only 8 or 4 binary digits, or bits, instead of the 32 a computer traditionally uses. Each number is less precise, but the chip can perform and store far more of them, which suits machine learning better than it would suit accounting.

Halving the precision roughly doubles a chip's headline speed, so a performance figure quoted without its number format is meaningless and an export threshold has to say which format it counts.

front endfront end of line, FEOL, front-end, front-end wafers

The front end of line is the first half of making a chip, the steps that build the transistors in the silicon. In the industry at large, the front end means the whole wafer fab, as against the back end where chips are packaged and tested.

By 2026 front-end wafers had overtaken packaging as the tightest constraint on AI chip output.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

gallium and germaniumgallium, germanium, antimony

Gallium and germanium are metals used in chips other than silicon logic: gallium in the compound wafers behind radio parts, LEDs and lasers, germanium in fiber optics, infrared lenses and satellite solar cells. Both are recovered as byproducts, gallium from aluminum refining and germanium from zinc.

China refines 99 percent of the world's primary gallium and used both metals as its first retaliation against US chip rules.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

gate-all-aroundGAA, nanosheet transistor, RibbonFET at Intel, nanosheet, nanosheets, RibbonFET, GAA transistor, gate-all-around transistors

A transistor in which the gate, the electrode that switches the current, wraps all the way round the channel that current flows through; a fin's gate touches three sides. Surrounding the channel gives the gate full control, so the switch still turns fully off as dimensions shrink.

Only TSMC, Intel and Samsung can build the 2 nanometer generation's transistor in volume, and it is what drives new demand for atomic layer deposition and sideways etching tools.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

GB/sTB/s, Gb/s, Tbps, gigabytes per second, terabytes per second, gigabits per second, terabits per second

GB/s is gigabytes per second, the measure of how much data a link or a memory can move; TB/s is a thousand times more. A lowercase b, as in Gb/s or Tbps, counts bits, each an eighth of a byte. One HBM stack moves over 2 TB/s; NVLink 6 gives each GPU 3,600 GB/s.

The first US chip rule caught any part with a 600 GB/s link, and the 2026 rule sets a 6,500 GB/s memory ceiling.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

glass clothT-glass, low-expansion glass, glass fiber cloth, low-expansion glass cloth

Glass cloth is a woven fabric of fine glass fibers that gives a substrate core or circuit board its stiffness. T-glass is a special grade that barely expands when heated, which keeps a large package flat.

One Japanese company, Nitto Boseki, supplies the low-expansion cloth under every large AI package, and its plants are running at full capacity.

[[#^substrates-and-pcbs|Read it in Substrates and PCBs →]]

GPUgraphics processing unit, GPUs

A processor originally built to draw video game images by doing thousands of simple calculations simultaneously. That same shape of arithmetic turned out to be what neural networks need, so this chip became the default AI processor.

Nvidia holds roughly 70 percent of the AI chip market, and its graphics processors are what most export licenses name.

gross margin

The share of a sale left over after paying what it cost to make the thing, before research, sales and overheads are counted. A 70 percent gross margin means $70 of every $100 of revenue survives manufacturing cost.

Gross margin shows where pricing power sits: chip designers, memory makers and inspection-tool vendors keep well over half of each sale, substrate makers about a third, and assembly and test houses under a fifth.

[[#^the-economics-of-ai|Read it in The Economics of AI Chips →]]

HBMhigh bandwidth memory, high-bandwidth memory, HBM3E, HBM4, HBM4E, HBM stack, HBM stacks, memory stacks, stacked memory

A stack of eight to sixteen memory chips, drilled through with copper columns and mounted a few millimeters from the processor so data reaches the arithmetic units far faster than it could across a motherboard. One such stack moves data roughly thirty times faster than an ordinary memory chip.

The most expensive line on an AI accelerator's bill of materials, made by three firms whose entire 2026 output was sold before the year began.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

High-NA EUVhigh numerical aperture extreme ultraviolet, ASML EXE series, High-NA, High NA, High-NA scanners, High-NA machine, High-NA tools

The next generation of extreme ultraviolet machine, whose larger mirrors collect light over a wider angle and so print smaller features. The wider optics also halve the area the machine can print in one exposure, so a large chip has to be stitched together from two exposures.

Each machine costs $350 to $400 million, only ten were installed anywhere as of September 2026, and Intel's early adoption against TSMC's delay to 2030 is a real disagreement about where the technology goes.

[[#^lithography|Read it in Lithography →]]

high-performance computingHPC, HPC platform, high-performance computers

High-performance computing is the industry's name for the heavy end of the market: supercomputers, AI accelerators and the server processors beside them. A foundry's HPC platform is the version of a node tuned for those chips.

AI has made HPC the largest customer for the newest nodes, the most film layers in a substrate and the most inspection time.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

high-volume manufacturingHVM, volume production, mass production, high volume, in volume, production ramp

High-volume manufacturing is the point where a new process or product stops being a trial and runs at full rate with enough good chips to sell. A process reaches it a year or more after its first working wafers.

Announcements name the year a node enters high-volume manufacturing; until then a process exists only on pilot lines.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

hybrid bondingdirect bond interconnect, SoIC, Foveros, copper pad to copper pad

Joining two chips face to face by pressing their copper pads, and the glass-like insulator around them, into direct contact, with no solder in between. Removing the solder lets connections be packed much more tightly and shortens the path heat has to travel out.

Taller, cooler memory stacks depend on this step, only two suppliers make the tools, and every slip in their schedule moves the memory roadmap with it.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

hydrogen fluoridehydrofluoric acid, HF, ultra-high-purity hydrofluoric acid, high-purity hydrogen fluoride

Hydrogen fluoride is a gas that dissolves glass, and hydrofluoric acid is its solution in water. Fabs use both to strip oxide layers and clean wafers between steps, at purities of a few stray atoms in a trillion.

When Japan put it under license for South Korea in 2019, exports fell 88 percent and Korea spent five years building its own supply.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

hyperscalerhyperscalers

One of the handful of companies that run data centers at global scale and buy computing hardware by the gigawatt: Amazon, Microsoft, Google, Meta and, on most definitions, Oracle.

They commit capital years before the hardware exists.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

i-lineg-line, i-line steppers, i-line scanners

i-line is the coarsest lithography light still in use, 365 nanometers from a mercury lamp, named for one line in the lamp's spectrum. It prints the widest features on a chip and much of a package. The even older g-line sits at 436 nanometers.

i-line is the one tier where a Chinese toolmaker has a measurable share, about 4 percent of the world market, and nothing above it.

[[#^lithography|Read it in Lithography →]]

IDMintegrated device manufacturer, integrated device maker, integrated device makers

A chip company that both designs its products and manufactures them in its own factories. Intel, Samsung and Micron are the main surviving examples.

An integrated maker that also rents out factory capacity is competing with its own customers, which is the commercial reason Intel and Samsung struggle to win other firms' flagship designs.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

immersion lithographyimmersion DUV, ArF immersion, immersion scanner, immersion scanners, immersion tools, immersion DUV scanners, immersion deep-ultraviolet

An immersion scanner prints with a thin layer of ultrapure water between its lens and the wafer. Light bends more sharply through water than through air, so the same lens prints finer lines. It is the best that deep ultraviolet light can do, one step below extreme ultraviolet.

Immersion is the tier China can still buy and is now building itself, and it is where Dutch export licensing draws its line.

[[#^lithography|Read it in Lithography →]]

in-country transfertransfer (in-country)

A change in the end use or the end user of an item inside one foreign country, defined at 15 CFR 734.16. Nothing crosses a border: a server legally imported into a country for one customer is transferred when it is resold, or repurposed, for another.

It is the step that catches hardware diverted after it has landed, and it is why a license granted for a named Chinese customer does not travel with the hardware. Reexports and in-country transfers of advanced chips to Country Group D:5 keep a presumption of denial even where an export would be read case by case (91 FR 1685).

[[#^geopolitics|Read it in Geopolitics →]]

indium phosphideInP, indium

Indium phosphide is a crystal, grown from the metal indium and phosphorus, that gives off light when current passes through it, which silicon cannot do. It is the material of the lasers inside the fastest optical modules. Indium itself is recovered as a byproduct of zinc mining.

China produces about 70 percent of the world's indium, and Nvidia paid $4 billion for laser capacity it could not simply order.

[[#^systems-and-networking|Read it in Systems and Networking →]]

inferenceinference chip, inference chips, inference accelerator, inference accelerators, training and inference

Training is the run that builds an AI model, reading a vast body of text through a cluster of accelerators for weeks. Inference is using the finished model: answering a prompt. Training reuses each stored number across a huge multiplication; inference reads the whole model to produce each word and waits on memory.

Inference is where memory size and speed set how many people one chip can serve, which is why HBM decides how fast a GPU runs.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

InfiniBandQuantum-2, Quantum-X800

InfiniBand is a networking standard built for supercomputers, with low delay and no dropped packets, that AI clusters used to link thousands of servers before Ethernet caught up. Nvidia owns the main supplier and sells both.

The choice between InfiniBand and Ethernet decides who sells the switch chips, and Broadcom's Ethernet parts now double in bandwidth every generation.

[[#^systems-and-networking|Read it in Systems and Networking →]]

interposerinterposers, silicon interposer, silicon carrier

A slab of silicon carrying wiring but no transistors, used as a miniature circuit board underneath several chips so they can be connected at a density no ordinary board could reach.

The interposer's own manufacturing yield, roughly 60 to 70 percent on large ones, is now a real share of an accelerator's cost, and its maximum area caps how much silicon fits in one package.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

ion implantationion implanter, ion implanters, implant, implant layers, implantation

A machine fires charged atoms of boron, phosphorus or arsenic into the silicon at high speed so they lodge just under the surface. Where they land, the silicon conducts differently, which is how the two halves of a transistor are made. The machine is an ion implanter.

Implanters are export-controlled tools, and Applied Materials paid a $252 million penalty in 2026 for shipping them to a listed Chinese customer.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

IPsilicon IP, IP blocks, licensed blocks, licensed circuit blocks, semiconductor IP, IP catalog, intellectual property

In chip design, IP means a ready-made block of circuitry, such as a processor core or a memory interface, that a design house licenses. Arm sells processor IP; others sell the blocks that talk to memory, PCIe or another chiplet.

Arm's royalties reach $2.61 billion a year because nearly every AI accelerator's host processor is built on its cores.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

is-informed letteris informed letter, is-informed letters, by letter

A letter from BIS to one named company imposing a license requirement on a specific export, without any rule being published. The authority is written into the regulations themselves, for example 15 CFR 744.23(b), which lets BIS inform a person individually, with no amendment to the EAR.

It is the fastest way a control is imposed. The A100 and H100 requirement of August 2022 and the H20 requirement of April 2025 both arrived this way, and the public learned of each from the company's own filing.

[[#^geopolitics|Read it in Geopolitics →]]

JEDECJESD270-4, JEDEC standard

JEDEC is the industry body that writes the standards for memory chips, so that a memory stack from any maker fits any processor built to the same specification. Its HBM4 standard, published in April 2025, sets the width and speed of the interface.

Nvidia's qualification bar sits above the JEDEC baseline, which is why passing the standard is not the same as winning the order.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

kilowattkW, kilowatts, megawatt, MW, megawatts, gigawatt, GW, gigawatts

A kilowatt is a thousand watts, about what a hair dryer draws. A megawatt is a thousand kilowatts, a gigawatt a thousand megawatts, roughly the output of one large power station. One AI rack draws 142 kilowatts; a data center campus is now sized in gigawatts.

A gigawatt of accelerators is what OpenAI and Broadcom mean when they announce a deal, and power is what limits it.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

known-good dieKGD, good die, good dies, known good die

A bare chip tested thoroughly enough, before assembly, to be trusted inside something expensive. In an ordinary product a faulty chip wastes one chip; inside a stacked package it can ruin thirty.

As packages grow toward ten logic chips and twenty memory stacks, the cost of catching a bad one late pushes testing and burn-in, running chips hot to force early failures, back onto the wafer.

[[#^test-and-assembly|Read it in Test and Assembly →]]

KrFkrypton fluoride, krypton fluoride laser, 248 nm, 248-nanometer

KrF is krypton fluoride, the gas in an older lithography laser that shines at 248 nanometers. KrF scanners print the coarser layers of a chip, where lines are far apart, and thick films for packaging.

Every chip still needs KrF layers, so the tool is in every fab, including China's, and nobody controls its export.

[[#^lithography|Read it in Lithography →]]

laminatelaminates, copper-clad laminate, copper-clad laminates, low-loss laminate, core laminate

A laminate is a stiff sheet made by pressing glass cloth and resin together, usually with copper foil bonded to its faces. It is the material a circuit board or a substrate core is cut from. A low-loss laminate absorbs little of the signal passing through the wires on it.

How much signal the laminate absorbs has become a main design limit on the boards that link GPUs.

[[#^substrates-and-pcbs|Read it in Substrates and PCBs →]]

large power transformerlarge power transformers, transformer, transformers, switchgear, substation

A large power transformer is the machine, the size of a house, that steps grid electricity down from transmission voltage to a level a data center can use. Switchgear is the heavy switching and protection equipment around it, and together they make up the substation at the gate of the campus.

A transformer ordered today arrives in about three years, against under a year before 2020, and that queue is where AI buildouts slip.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

lead timelead times, delivery time

Lead time is the wait between placing an order and receiving it. A wafer clears a fab in months; a large power transformer ordered today takes about three years, and six years of gas turbine output is already sold.

Money buys silicon capacity faster than it buys power capacity, and lead time is where that difference shows.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

leading edgeleading-edge, at the leading edge, advanced node, advanced nodes, advanced-node

The leading edge is the newest generation of chipmaking process in volume production, today the 3 nm and 2 nm nodes, made only by TSMC, Samsung and Intel. A leading-edge chip is one built on it. Everything older is a mature node.

Export controls draw their line at the leading edge, and only TSMC runs it at volume for outside customers.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

liquid coolingdirect-to-chip cooling, cold plate cooling, cold plate, cold plates, liquid-cooled, direct-to-chip liquid, direct liquid cooling

Taking heat out of a processor by pumping water through a metal plate bolted directly onto it, instead of blowing air across a finned heatsink. Water carries far more heat per unit of volume, which is the only practical way to cool a rack drawing over a hundred kilowatts.

It adds 7 to 10 percent to construction cost but cuts the floor area needed per megawatt by 70 to 85 percent, and an air-cooled data hall cannot host a modern AI rack without a full mechanical rebuild.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

lithographyphotolithography

Printing a circuit pattern onto a wafer by shining light through a patterned plate and projecting a shrunken image of it onto a light-sensitive coating. It is photography at the scale of nanometers, repeated once for every layer of the chip.

The most concentrated stage in the chain, and the resolution a country can reach sets the ceiling on every chip it can make.

[[#^lithography|Read it in Lithography →]]

lotlots, wafer lot, wafer lots, per lot

A lot is the batch of wafers a fab moves through its machines together, usually 25 in one sealed carrier. Recipes, inspections and yield are tracked lot by lot.

How many wafers per lot a fab can afford to inspect is a cost decision that sets what process control costs it.

[[#^metrology-and-inspection|Read it in Metrology and Inspection →]]

MacauMacao, China or Macau, China and Macau

Macau is a Chinese city with its own customs territory, like Hong Kong, so goods can enter it under separate rules. US export controls name China and Macau together to close that route, and treat a firm headquartered in either the same way.

Every chip rule since 2022 is written for China or Macau, which is why the pair appears throughout the AI Chips page.

[[#^geopolitics|Read it in Geopolitics →]]

mask blankmask blanks, EUV blank, EUV blanks, photomask blank, photomask blanks, blank plate, DUV blanks

A mask blank is a photomask before any pattern is on it: a six-inch square of very flat glass carrying the coating the pattern will be cut into. For extreme ultraviolet the coating is a mirror of about forty pairs of ultrathin layers, and a single buried particle ruins the plate.

Three firms in the world make EUV blanks and one Japanese firm certifies them, on a business too small to attract a funded entrant.

[[#^photomasks-and-pellicles|Read it in Photomasks and Pellicles →]]

mask shopmask shops, mask making, mask maker, mask makers

A mask shop is the factory, inside a foundry or run by a specialist such as Photronics, that turns a finished chip design into its set of photomasks. It writes each plate with an electron beam, inspects it and repairs it.

TSMC, Samsung and Intel run their own to control turnaround time, and a fab without its mask shops nearby is not a substitute for one that has them.

[[#^photomasks-and-pellicles|Read it in Photomasks and Pellicles →]]

mask writermask writers, multi-beam writer, multi-beam writers, electron-beam writer, e-beam writer, mask writing

A mask writer is the machine that cuts a chip's pattern into a photomask blank with an electron beam, one shape at a time. A dense EUV mask carries billions of shapes, so modern writers fire many beams at once to finish in hours.

IMS Nanofabrication of Vienna and NuFlare of Japan are the only two suppliers, and no Chinese firm makes one.

[[#^photomasks-and-pellicles|Read it in Photomasks and Pellicles →]]

mature nodemature nodes, mature-node, mature logic, older nodes, older lines, trailing edge

A mature node is an older chipmaking process, 28 nm and above, that has run for years and competes on price. Most of the world's wafers come off these lines, making power chips, analog parts and microcontrollers.

China holds about 38 percent of mature logic capacity and is moving to domestic suppliers there on a visible timetable, while the leading edge stays out of reach.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

memory bandwidth densitybandwidth density, bandwidth-density

Memory bandwidth density is how much data a memory stack can move each second divided by its area: gigabytes per second per square millimeter. The December 2024 rule controls any stack above 2, and every HBM stack in production is far above it.

One threshold catches every part worth buying, which is why the HBM control works where the chip controls let parts through.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

memory wall

The widening gap between how fast a processor can calculate and how fast memory can feed it numbers to work on. Computing speed has been roughly tripling every two years while memory bandwidth has less than doubled over the same period.

This gap is why AI accelerators now spend most of their cost and silicon area on memory, and why memory suppliers have started earning margins comparable to chip designers.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

metal-oxide resistmetal-oxide resists, metal oxide resist, tin-oxide resist, metal-oxide EUV photoresist

A metal-oxide resist is a photoresist built on clusters of tin and oxygen. Tin absorbs extreme ultraviolet light far better than carbon, so the resist needs fewer photons to record a pattern and prints sharper edges at the smallest sizes.

JSR bought its inventor, Inpria, in 2021, and a Japanese state fund then bought JSR, so the chemistry High-NA needs sits under Japanese control.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

METIMinistry of Economy, Trade and Industry, Japan's Ministry of Economy, Trade and Industry

METI is Japan's Ministry of Economy, Trade and Industry, the ministry that writes Japan's export controls and funds its chip industry. It licensed 23 categories of chipmaking equipment in July 2023 and subsidizes Rapidus, mask-blank capacity and materials plants.

Japan's controls apply to every destination and name no country, and METI is the office that decides them.

[[#^geopolitics|Read it in Geopolitics →]]

metrologyprocess control, when grouped with inspection, metrology and inspection, inspection tools

Measuring what a factory actually built: how wide a printed line came out, how thick a film is, whether this layer sits exactly on top of the last one. Inspection is the related job of finding flaws.

One firm, KLA, holds about 64 percent of this market, and a sanctioned fab that obtains other tools on the gray market still cannot work out why its yield is low.

[[#^metrology-and-inspection|Read it in Metrology and Inspection →]]

microbumpmicrobumps, solder bump, solder bumps, bumps, bump, bump metrology

A microbump is a dot of solder, a few hundredths of a millimeter across, that joins a die to the interposer or substrate beneath it. A large chip has tens of thousands, spaced 30 to 40 microns apart, and each one is an electrical connection that has to survive the package heating and cooling.

Hybrid bonding, which replaces bumps with copper pressed straight onto copper, is the next step and is not yet ready for HBM.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

mm2square millimeters, square millimeter, mm²

mm2 means square millimeters, the unit chip areas are given in. A lithography scanner prints at most 858 mm2 in one shot, an AI GPU die is about 800 mm2, and the largest planned interposer is 12,000 mm2, about the area of a compact disc.

Yield falls faster than area rises, so mm2 is the number behind most of what a chip costs.

[[#^the-economics-of-ai|Read it in The Economics of AI Chips →]]

model weightsweights, frontier model weights, trained weights

Model weights are the billions of numbers an AI model consists of once it has been trained, the file that runs on the chips. Copy the weights and the model goes with them.

The AI Diffusion rule classified frontier model weights as a controlled item, ECCN 4E091, so the controls reach the output of the chips as well as the chips.

[[#^geopolitics|Read it in Geopolitics →]]

MOFCOMMinistry of Commerce, China's Ministry of Commerce

MOFCOM is China's Ministry of Commerce, the ministry that writes and administers China's own export controls. Its notices put gallium, germanium, antimony and the rare earths under license and, in December 2024, banned their export to the United States.

Beijing's retaliation targets the raw materials, and MOFCOM is the office that signs each notice.

[[#^geopolitics|Read it in Geopolitics →]]

multipatterningdouble patterning, quadruple patterning, self-aligned quadruple patterning, multiple patterning, multi-patterning, several passes, several exposures, multiply exposed, DUV multipatterning

Printing a single chip layer using two, three or four separate plates and etching steps, because one exposure cannot resolve features that close together. It is what a fab does when it cannot get sharper light.

China reaches advanced processes this way without extreme ultraviolet machines, taking roughly 34 lithography steps where nine would do, which is the direct source of its yield and cost penalty.

[[#^lithography|Read it in Lithography →]]

NAND3D NAND, NAND flash, flash memory, 128-layer NAND

NAND is the memory that keeps data when the power is off: the storage inside a phone, a laptop drive or a data center disk. 3D NAND stacks its cells in hundreds of layers, made by etching holes far deeper than they are wide. It is slow next to DRAM and is not used inside an AI accelerator.

The 2022 rules set a fab threshold at 128-layer NAND, and China's YMTC is the target.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

nanometernm, nanometers, microns, micrometer, micrometers, angstrom, angstroms, picometer, picometers

A nanometer is a billionth of a meter, about the width of ten atoms; a human hair is about 80,000 of them across. A micron, or micrometer, is a thousand nanometers, an angstrom is a tenth of a nanometer, and a picometer is a thousandth. Lithography light is measured in nanometers, package bumps in microns, and mirror flatness in picometers.

Node names such as 2 nm no longer describe any feature that size, but the physical limits of printing and stacking are still set in these units.

[[#^lithography|Read it in Lithography →]]

neonneon gas, semiconductor-grade neon

Neon is the gas inside the lasers that give deep ultraviolet scanners their light, mixed with krypton or argon and fluorine. A fab uses it by the cylinder and cannot print without it.

Ukraine supplied about 70 percent of the world's neon before 2022, and the fabs kept running only because they had stockpiled since 2014.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

nitrogen trifluorideNF3

Nitrogen trifluoride is a gas that, split apart in a plasma, releases fluorine that scours the deposits off the inside of a process chamber between wafers. It is the largest-volume specialty gas in a fab.

SK Materials makes a large share of the world's supply, one of the single-molecule specialists under the big gas companies.

%% validator-ignore-next-line --code article.block-repeated-nearby --reason intentional-repeat-in-distinct-structured-entries %%
[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

nm-class5 nm-class, 7 nm-class, 2 nm-class, nanometer-class, nm class

Nm-class, as in 7 nm-class, means a process roughly as dense as the foundries' 7 nm generation, used when a maker's own name for the node is different or when nothing on it measures 7 nanometers. Node names stopped describing a physical size around 2010.

SMIC's 7 nm-class and 5 nm-class processes, made without EUV, are the ceiling on China's own AI chips.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

nodeprocess node, technology node, for example N2 or 18A, nodes

The name a foundry gives one generation of its manufacturing process. The number in the name stopped measuring anything on the chip decades ago: nothing on TSMC's N2 is 2 nanometers wide, and SMIC's 5 nanometer-class process has a tighter metal spacing than Intel's 18A.

Because node names are marketing labels and measure nothing, rules and comparisons that rely on them are unreliable, which is why US export thresholds specify transistor type and metal spacing.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

NVL72GB200 NVL72, GB300 NVL72, Vera Rubin NVL72

Nvidia's rack-sized product: 72 accelerators and 36 processors wired into one machine that software can treat as a single computer. The GB300 version draws up to 142 kilowatts.

AI capacity is now bought and priced by the rack, at roughly $5.0 million for a Grace Blackwell one and an estimated $7.8 million for its Vera Rubin successor.

[[#^systems-and-networking|Read it in Systems and Networking →]]

NVLinkNVSwitch, NVLink 5, NVLink 6, NV-HBI

Nvidia's private high-speed connection between its own accelerators, carrying up to 3,600 gigabytes per second per chip so that dozens of them can act as one. No other vendor sells a switch with comparable bandwidth.

A genuine single-vendor chokepoint inside an otherwise competitive systems layer, and the reason the rest of the industry created the UALink standard to compete with it.

[[#^systems-and-networking|Read it in Systems and Networking →]]

ODMoriginal design manufacturer, ODMs, contract manufacturer, contract manufacturers, contract manufacturing, EMS, server ODM

An ODM, for original design manufacturer, is a firm such as Foxconn, Quanta or Wistron that designs and builds servers and racks to a customer's specification and puts the customer's name on the box. A contract manufacturer does the assembly only.

Several ODMs on three continents can build an AI rack, which is why rack integration earns low-teens margins and is not a chokepoint.

[[#^systems-and-networking|Read it in Systems and Networking →]]

oligopolyoligopolies, duopoly, three-firm oligopoly

An oligopoly is a market with only a few sellers, so each one's decisions move the price; a duopoly has two. DRAM, industrial gases, substrates and chip testers are all oligopolies.

Most stages of this chain are oligopolies, a few are monopolies, and the difference decides whether losing one supplier stops the line.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

operating marginoperating profit, operating loss, operating income

Operating margin is what is left of revenue after both the cost of making the product and the cost of running the company, research and sales included, as a share of revenue. It sits below gross margin, which counts only the cost of making.

SK hynix publishes no gross margin, so its 76 percent operating margin is the number that shows where HBM profits went.

[[#^the-economics-of-ai|Read it in The Economics of AI Chips →]]

optical transceiveroptical module, pluggable optics, optical transceivers, transceiver, transceivers, optical modules, 800G optical transceivers

A small device that turns electrical signals into laser light for sending down a glass fiber, and turns them back at the far end. Every network link longer than a few meters in a large AI cluster needs one at each end.

Chinese firms supply more than half the world's high-speed modules, and the indium phosphide lasers inside them ran at roughly half of demand in early 2026.

[[#^systems-and-networking|Read it in Systems and Networking →]]

OSAToutsourced semiconductor assembly and test, OSATs, outsourced assembly and test, assembly and test firms, assembly and test contractor, assembly and test houses

A contract firm that takes finished wafers, cuts them into chips, seals the chips into packages and tests them. It is the back end of chipmaking, done for hire.

A low-margin business at 14 to 20 percent, with four of the ten largest firms Chinese and its tools largely outside the export control lines drawn around lithography and advanced deposition.

[[#^test-and-assembly|Read it in Test and Assembly →]]

overlayoverlay error, alignment

How precisely one printed layer of a chip lands on top of the layer beneath it. The best machines hold this to under a nanometer, which is a few atoms of misalignment across a disc 300 millimeters wide.

Overlay is one of the specifications that separates an advanced printing machine from an ordinary one, and it gets worse every time a layer has to be printed in several passes.

[[#^metrology-and-inspection|Read it in Metrology and Inspection →]]

panel-level packagingpanel-level, panel level packaging, rectangular panel, rectangular panels

Panel-level packaging builds packages on a large rectangular sheet instead of a round wafer, so far less area is wasted at the edges and many more packages fit on one carrier. It is the industry's way around the size limits of a 300 mm wafer.

The first panel-level line for AI chips is due in 2027, which would ease the CoWoS bottleneck.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

PCIePCI Express, PCIe 6, PCIe 7

PCIe is the standard connector and link that joins a processor to the cards inside a computer, an accelerator included. Each generation doubles the speed. In an AI server it carries data between the host processor and the GPUs, while faster private links join the GPUs to each other.

The PCIe block is licensed IP that has to be proven on each new node before a chip can use it.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

PDKprocess design kit, process design kits

A process design kit, or PDK, is the file set a foundry gives designers describing exactly what its factory can print: the sizes, spacings and electrical behavior of every feature on one node. Design software is checked against it before a chip is accepted.

A PDK is written against specific tool versions, which is why a design team cannot mix vendors' software.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

pelliclepellicles, EUV pellicle

A thin transparent membrane held a few millimeters above a photomask so that dust settles on it, far enough out of focus that it does not print, and the pattern stays clean. It is a lens cap a photographer can shoot through.

No membrane yet survives extreme ultraviolet light while passing enough of it, so fabs trade printing speed against defect risk product by product, and solving this would cut the cost of that printing more than any machine upgrade.

[[#^photomasks-and-pellicles|Read it in Photomasks and Pellicles →]]

performance density

A chip's TPP, the export rules' measure of computing power, divided by the area of its logic dies in square millimeters, memory stacks excluded. It applies only to a chip that already reaches 1,600 TPP, and it catches parts that spread the same computing power over more silicon. It replaced the 2022 test, which was based on interconnect bandwidth, the speed at which a chip exchanges data with its neighbors.

It closed the gap the A800 and H800 used, and it is the clearest case of a control written as a formula. The threshold is 5.92 in ECCN 3A090.a (88 FR 73458).

[[#^geopolitics|Read it in Geopolitics →]]

photomaskmask, reticle, mask set, photomasks, masks, mask sets, mask blank set

The master template for one layer of a chip: a quartz plate, or for the shortest wavelengths a mirror, carrying the pattern that gets projected onto the wafer. A leading-edge chip needs seventy to a hundred of them, and the full set costs $10 million to $40 million.

Mask cost decides which chips can afford a leading-edge process at all, and the blank plates the masks are made from come from just two Japanese suppliers.

[[#^photomasks-and-pellicles|Read it in Photomasks and Pellicles →]]

photoresistresist, resists, EUV resist, EUV resists, resist makers

A liquid polymer spun onto a wafer in a film a few tens of nanometers thick that changes how easily it dissolves wherever light strikes it. Developing it, much like developing photographic film, washes away the exposed parts and leaves the printed pattern behind.

Japan supplies most of the world's photoresist, between 75 and 90 percent on published estimates, and the largest maker is now owned outright by a Japanese state fund. Each resist is approved per layer per chip per fab, so switching supplier takes years.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

pitchpitches, half-pitch, gate pitch, metal pitch, wire pitch, line pitch

Pitch is the distance from one line on a chip to the next, center to center, so it counts the line and the gap together. Half-pitch is half that. A 16 nm pitch means lines 16 nanometers apart; the 2022 rules set a DRAM threshold at 18 nm half-pitch.

Pitch is the reliable measure of how fine a process prints.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

plasmaplasmas, plasma etch, plasma-enhanced, plasma source

A plasma is a gas that has had electrons knocked off its atoms by an electric field, leaving charged fragments that react with whatever they touch. Most deposition and etch happens in a plasma inside a vacuum chamber, and the extreme ultraviolet light source is a plasma of vaporized tin.

Change the gas, pressure and power in the chamber and the same plasma tool either adds a film or removes one, which is why export rules name process recipes.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

polysiliconpolycrystalline silicon, electronic-grade polysilicon, semiconductor-grade polysilicon, polysilicon feedstock

Polysilicon is silicon refined to purity but not yet grown into one crystal: gray rods made of many small crystals. It is the raw material that is melted down to pull the single crystal a wafer is cut from. The same material, at lower purity, goes into solar panels.

China makes about 93 percent of the world's polysilicon, but almost all of it is solar grade, so the dominance does not reach chips.

[[#^silicon-and-wafers|Read it in Silicon and Wafers →]]

power shelfpower shelves, rack power shelf

A power shelf is a slide-in unit in a rack that converts the incoming supply to the voltage the boards use and feeds it to the busbar. A GB300 NVL72 rack draws its 142 kilowatts through eight of them at 33 kilowatts each.

The shelves and the boards behind them have many suppliers; the transformers upstream do not.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

presumption of approvalapproval is presumed, presumed approval

A presumption of approval means a license is still required but will normally be granted. It is the opposite of a presumption of denial, and the two can sit inside one rule: HBM sales into China are presumed approved for a buyer headquartered elsewhere and presumed denied for a Chinese one.

That split is what keeps the Chinese plants of Korean and American firms inside the trade.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

presumption of denial

A license review policy. An application may be filed and will be considered, but the reviewing agencies start from the position that it should be refused, and the exporter has to overcome that. It is the policy for advanced computing chips going to China and Macau under 15 CFR 742.6(b)(10), and for most Entity List entries.

It is the distinction that decides whether a company files at all: under a presumption of denial an application can still be made, under a prohibition it cannot.

[[#^geopolitics|Read it in Geopolitics →]]

printed circuit boardPCB, PCBs, printed circuit boards, circuit board, circuit boards, high-multilayer PCB

A printed circuit board is the flat green or black card that electronic parts are soldered onto, with its wiring etched from copper sheets and stacked in layers. The board under an AI GPU has more than 30 layers and carries hundreds of amps.

High-layer-count boards and the laminate they are built from are concentrated in Taiwan, Japan and now Thailand.

[[#^substrates-and-pcbs|Read it in Substrates and PCBs →]]

probe cardprobe cards

A circuit board carrying thousands of fine needles that press down onto the contact pads of a chip while it is still part of the wafer, so a tester can drive signals into it. Every card is custom-built for one chip design.

Because cards are bespoke and slow to qualify, probe card supply and lead time set how fast a new accelerator or memory stack can ramp to volume.

[[#^test-and-assembly|Read it in Test and Assembly →]]

PVDphysical vapor deposition, sputtering, sputtering target, sputtering targets, sputter

Physical vapor deposition, or PVD, coats a wafer by knocking atoms off a solid slab of metal, the sputtering target, in a vacuum so they fly across and land on the wafer as a thin film. It lays down the metal barriers and seed layers under a chip's copper wiring.

The targets are a chokepoint of their own: JX Advanced Metals supplies about 65 percent of the world's.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

qualificationqualify, qualifies, qualified, qualifying, requalify, requalification, qualification tests, qualification lock-in

Qualification is the months of testing a fab or a customer runs before it will accept a new material, tool or supplier for one product. A resist, a slurry, a wafer source or a memory stack is approved for one layer of one product at one fab, and switching means running the whole test again.

Qualification, counted in quarters, is what makes a second source slow, and it protects every incumbent in this chain.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

rackcabinet, racks, cabinets, rack-scale

The standard steel frame that computing equipment is bolted into in a data center, roughly the size of a large refrigerator. AI systems have turned the rack from a container into the product, because an entire rack is now sold and wired as one machine.

Rack power went from about 120 kilowatts in 2024 to plans for a megawatt by 2027, and each step forces changes to cooling, busbars, floor loading and the substation outside.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

rampramps, ramp-up, ramping, yield at ramp

A ramp is the months in which a new process or product climbs from a few wafers a week to full output while the share of working chips rises. Yield is lowest at the start of the ramp and improves as engineers find which steps lose dies.

Yield at ramp separates a profitable node from a subsidized one, and Intel Foundry's losses come from the ramp.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

rare earthsrare earth, rare-earth, rare earth elements, medium and heavy rare earths

The rare earths are seventeen metals, from samarium to yttrium, that go into the strong magnets in motors, disk drives and wind turbines, and into some lasers and glass. They are not rare in the ground, but China does nearly all the refining.

Beijing put seven of them under export license in April 2025 and claimed jurisdiction over any foreign product containing 0.1 percent of its rare earths.

[[#^geopolitics|Read it in Geopolitics →]]

redistribution layerRDL, redistribution wiring, redistribution layers

A redistribution layer is a thin sheet of fine copper wiring, laid down in resin, that spreads a die's tightly spaced connections out to a wider pattern the package can handle. CoWoS-R and CoWoS-L use it in place of a full silicon interposer.

Swapping silicon for redistribution wiring is how TSMC pushed packages past 3.3 times the reticle size.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

reexport

Shipping an item that falls under US export rules, the EAR, from one foreign country to another, defined at 15 CFR 734.14. A Korean stack of memory moving from Korea to China is a reexport, and it needs the same US license a shipment from Texas would.

Most of the trade the controls are aimed at never touches the United States. Without a rule on reexports, the controls would bind only American ports.

[[#^geopolitics|Read it in Geopolitics →]]

reticlephotomask

The patterned plate that a lithography machine projects onto the wafer, one chip layer at a time. In practice the word means the same as photomask, with reticle stressing that the machine steps the same image repeatedly across the disc.

The reticle's fixed printable area, 26 by 33 millimeters, is a hard physical limit that shapes how every large AI chip has to be designed.

[[#^photomasks-and-pellicles|Read it in Photomasks and Pellicles →]]

reticle limitreticle size limit, reticle field, field size, reticle-limited, reticle size, reticles, times reticle

The largest chip a lithography machine can print in a single exposure, about 858 square millimeters, or 26 by 33 millimeters. It is set by the machine's optics and is the same for every design.

Every AI accelerator worth buying is bigger than this, so designs must be split into chiplets and rejoined inside a package, which is how advanced packaging became the industry's bottleneck.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

RISC-VRISC-V cores, RISC-V processor

RISC-V is an open instruction set, the list of basic commands a processor understands, that anyone may use without a license. Companies build their own processor cores on it, and Nvidia now uses such cores for housekeeping inside every GPU.

It is the license-free alternative to Arm, and Chinese designers are adopting it to end their dependence on foreign firms for processor cores.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

RTLregister-transfer level, register-transfer-level, register transfer level, RTL description, RTL code

RTL, for register-transfer level, is the code in which a chip is first written: a text description, in a language such as SystemVerilog, of what every storage element holds on every tick of the clock. Software later turns it into transistors and wires.

An RTL description is what a design house hands to its tools and, through them, to the foundry.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

scale-out networkback-end network, cluster fabric, scale-out, scale out

The network that joins thousands of accelerator groups into one cluster, running at hundreds of gigabits per second over Ethernet or InfiniBand. The technology is ordinary data center networking; the scale is not.

Ethernet has taken more than two thirds of this market from InfiniBand, which moved the value to merchant switch chips and to the optical modules that carry the traffic.

[[#^systems-and-networking|Read it in Systems and Networking →]]

scale-up networkscale-up fabric, coherent domain, scale-up, scale up, scale-up domain, scale-up switch

The wiring that joins a few dozen accelerators inside one rack so a model too large for a single chip can be spread across them. It runs at terabytes per second, hundreds of times faster than the network between racks.

Scale-up bandwidth sets how large a model can be trained or served before the network becomes the limit, and Nvidia's NVLink is still the only product at the top of this market.

[[#^systems-and-networking|Read it in Systems and Networking →]]

scannerscanners, stepper, steppers, lithography scanner, lithography scanners, lithography machine, lithography system, lithography systems

A scanner is the lithography machine itself: it holds the photomask up to a light source and projects a shrunken image of one layer onto the wafer, sweeping mask and wafer past each other in a narrow slit of light. An older stepper exposes the whole field at once instead of scanning. One EUV scanner costs about $200 million.

ASML makes every EUV scanner in the world, so the scanner is the tool most of the export-control story is about.

[[#^lithography|Read it in Lithography →]]

second sourcesecond sources, second-source, multi-sourcing, dual source, single source, sole source, single-source

A second source is a second supplier qualified for the same part or material, so that a fab can keep running if the first one stops shipping. A single-source part has none, and adding one means joint development and a fresh qualification.

Every disruption in this chain so far has been absorbed within a year, and each one added a second source somewhere.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

SerDesserializer-deserializer, high-speed serial links, serial links, serial link

A SerDes, for serializer-deserializer, is the circuit at the edge of a chip that turns many slow parallel signals into one very fast stream over a single wire, and back again at the other end. Every link out of an accelerator, to another chip, a switch or an optical module, runs through one.

SerDes speed sets how much data a chip can move, and the blocks are licensed IP that few firms can design at the leading edge.

[[#^systems-and-networking|Read it in Systems and Networking →]]

signoffsign-off, static timing analysis, timing signoff, timing sign-off, physical verification, signed off

Signoff is the final set of automated checks a chip design must pass before a foundry will make it: that every signal arrives in time at the clock speed promised, and that every shape in the layout can be printed. Static timing analysis is the timing half; physical verification is the layout half.

Synopsys holds more than 90 percent of timing signoff and Siemens 85 percent of physical verification, and a foundry accepts no design that has not passed them.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

silicon bridgesilicon bridges, EMIB, silicon-bridge, local silicon bridges, embedded bridge

A silicon bridge is a small sliver of silicon carrying dense wiring, set into the package only where two dies need thousands of connections between them, so the rest of the package can use cheaper wiring. Intel calls its version EMIB; TSMC's CoWoS-L uses the same idea.

Placing the bridges to tolerance is what went wrong on the first Blackwell packages and delayed shipment.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

silicon shield

The argument that Taiwan's dominance of advanced chipmaking deters an attack, because destroying or seizing TSMC would cost an aggressor and the world more than the island is worth.

The central and contested assumption behind Taiwan policy: a shield works only while it stays irreplaceable, which gives Taipei reason to slow the diversification its allies want.

[[#^geopolitics|Read it in Geopolitics →]]

small yard, high fencesmall yard with a high fence, small yard

The stated design of US technology controls: restrict the narrow set of items that genuinely decide national security and leave the rest of the trade alone.

Whether the yard has stayed small is the standard test of whether export controls remain targeted security policy or have become general industrial policy.

[[#^geopolitics|Read it in Geopolitics →]]

specialty gasesspecialty gas, electronic specialty gases, bulk gases, bulk gas, electronic gases, process gas, process gases

A fab runs on two kinds of gas. Bulk gases, such as nitrogen and oxygen, arrive by the metric ton and are usually made on the fab site. Specialty gases, such as silane or nitrogen trifluoride, arrive in cylinders by the gram, each one doing one job, from depositing a film to cleaning a chamber.

Only cylinder-shipped specialty gases can be embargoed, and a single molecule such as neon can come from a handful of plants.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

SRAMstatic random-access memory, cache, on-chip memory, on-die SRAM, on-die memory, L2 cache

SRAM is the fast memory built from transistors on the logic chip itself, used as a cache that holds the numbers a processor is about to need. It is far faster than the memory stacks beside the chip and far smaller, because each bit takes six transistors.

The SRAM cell has stopped shrinking with each node, which caps how much cache an accelerator can carry and pushes memory off the die into HBM.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

subject to the EAR

The test for whether an item falls under US export rules at all. Under 15 CFR 734.3 it covers anything in the United States, anything of US origin wherever it now sits, foreign-made goods that contain more than a permitted share of controlled US content, and foreign-made goods caught by a foreign direct product rule. Nationality of the seller is not the test; the item is.

The phrase decides who the rules apply to. A Dutch or Korean firm shipping between two foreign countries can still need a US license, because the rules follow the item.

[[#^geopolitics|Read it in Geopolitics →]]

Substitutabilitysubstitutability rating

A four-band rating of how hard it would be for a well-funded state or firm, starting today, to build an alternative to the leaders of a stage, judged against four written tests. Easy: a second supplier is qualified, meaning approved by customers, and shipping today at the leading node, the most advanced process. Moderate: a second supplier exists but is not yet qualified at the leading node, about two to five years to close the gap. Hard: no second supplier at the leading node, five to ten years, and the path is known. Very hard: no second supplier, and the path runs through physics, decades of unwritten know-how or protected intellectual property, ten years or more, and nobody has repeated it yet. The clock always times the same actor and stops at qualification, well after a prototype.

It says how long a rival or a government would need to replace a stage, which is the question the export debate turns on.

substratepackage substrate, IC substrate, substrates, build-up substrate, build-up substrates, package substrates, IC substrates, resin substrate

The small, dense circuit board that a chip package sits on, spreading the chip's microscopic connections out to the millimeter-scale solder balls a motherboard can accept. It is built up layer by layer from epoxy film, laser-drilled holes and plated copper.

TSMC names substrates alongside memory as a limit on AI supply, and as packages grow, keeping a large one flat becomes harder than wiring it.

[[#^substrates-and-pcbs|Read it in Substrates and PCBs →]]

tape-outtape out, taped out, tapes out, tape-outs, tapeout

The moment a chip design is declared finished and the pattern files are sent to the factory to be written into masks. The name survives from when the data physically left on a reel of magnetic tape.

After tape-out any change costs a new mask set and a new manufacturing run, so it is the point where hundreds of millions of dollars of downstream commitment becomes irreversible.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

thermocompression bondingthermocompression, thermo-compression bonding, thermocompression bonder, thermocompression bonders, TCB, die bonder, die bonders, bonder, bonders

Thermocompression bonding presses one die onto another, or onto a substrate, under heat and force until the tiny solder bumps between them melt and join. It is how memory dies are stacked into an HBM cube and how chiplets are placed on a package.

The bonders place one die at a time, three or four firms make them, and ASMPT's line grew 146 percent in 2025 on AI demand.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

throughputwafers an hour, wafers per hour, wafers-per-hour

Throughput is how many wafers a machine can process in an hour. An EUV scanner reaches about 220, an inspection tool far fewer, and a bonder places one die at a time.

Throughput sets cost per layer and decides how many wafers a fab can afford to inspect, which is why brighter light sources and multi-beam tools matter.

[[#^lithography|Read it in Lithography →]]

TPPtotal processing performance

The measure US export rules use for a chip's computing power: twice the number of multiply-accumulate operations, a multiply followed by an add, that it does each second, multiplied by the number of bits in each operation, added up across every processing unit on the chip. The definition sits in ECCN 3A090, in supplement no. 1 to 15 CFR part 774.

The dividing line for sales to China. Control starts at 4,800 TPP; since 15 January 2026 applications below 21,000 TPP and 6,500 GB/s of memory bandwidth are read case by case (91 FR 1685). Accelerators are now designed around the formula.

[[#^geopolitics|Read it in Geopolitics →]]

TPUTensor Processing Unit, TPUs

Google's own AI chip, designed in-house and used only inside Google's own data centers and cloud service. The seventh generation is called Ironwood.

The clearest evidence that a large buyer can build a real alternative to chips bought on the open market, with Google claiming a total cost per chip about 44 percent below that of the Nvidia server it replaces.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

transistortransistors

The switch every chip is built from. Current runs through a channel between two terminals, and a voltage on a third terminal, the gate, opens or closes that path much as a tap opens or closes a pipe. One Nvidia Blackwell part contains 208 billion of them.

Everything in this supply chain exists to make transistors smaller, faster and less leaky, and the difficulty of doing that is why the industry consolidated into so few firms.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

transistor densitylogic density, chip density, transistors per square millimeter, density gain

Transistor density is how many transistors fit in a square millimeter of chip, now over 100 million on a leading-edge logic process. Each new node has traditionally raised it by a large step; the step is now about 1.1 to 1.2 times.

No foundry publishes wafer prices, so the shrinking density gain per node is the only public proxy for cost per transistor, and it says cost is rising.

[[#^transistors-and-the-front|Read it in Transistors and the Front End →]]

TSVthrough-silicon via, TSVs, through-silicon vias, through silicon via, through silicon vias

A copper column drilled all the way down through a chip so that power and signals can pass from its top face to its bottom face. It is what makes stacking chips vertically possible, in the way an elevator shaft makes a tall building usable.

These columns are what make high bandwidth memory possible, and US rules control the tools that cut them by hole shape and etching speed.

[[#^memory-and-hbm|Read it in Memory and HBM →]]

TWhterawatt-hour, terawatt-hours, terawatt hours

A terawatt-hour is a billion kilowatt-hours, the unit national electricity use is counted in. US data centers used 176 TWh in 2023, 4.4 percent of the country's electricity.

The projection of 325 to 580 TWh by 2028 is the number the grid debate turns on.

[[#^data-centers-and-power|Read it in Data Centers and Power →]]

UCIeUniversal Chiplet Interconnect Express, UCIe 3.0

UCIe is an open standard for the short, very fast link between two chiplets sitting side by side in one package. It lets chiplets from different vendors be wired together, the way PCIe lets cards from different vendors share a computer.

Version 3.0 reaches 64 billion transfers a second per wire, which is what lets an accelerator be assembled from pieces.

[[#^chip-design-eda-and|Read it in Chip Design, EDA and IP →]]

US personUS persons, U.S. person, U.S. persons

In export law a US person is any American citizen, resident or company, wherever in the world they are. Since October 2022 a US person may not service or support an advanced chip fab in China without a license.

The rule emptied Chinese fabs of American engineers within days, and it reaches people directly.

[[#^geopolitics|Read it in Geopolitics →]]

utilizationutilization rate, fab utilization

Utilization is how full a fab's lines are running, as a share of what they could run. A fab costs the same whether it is full or empty, so utilization decides whether it makes money.

SMIC's 93.5 percent shows what a captive home market does for volume, and its 21 percent gross margin shows what it does not do for price.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

VEUValidated End-User, Validated End User, Validated End-User status, VEU status, VEU cover, validated end users

An authorization BIS grants to a named foreign facility, letting approved items ship to it without an individual license each time. The approved facilities are listed in supplement no. 7 to 15 CFR part 748, and the procedure is 15 CFR 748.15.

It is what let Intel, Samsung and SK hynix run their fabs inside China on general authority after 2022. Revoking it in 2025 did not stop those fabs; it made every shipment a license application, and BIS said it would license operation but not expansion (90 FR 42321).

[[#^geopolitics|Read it in Geopolitics →]]

viascopper vias, vertical vias, vertical copper vias

Vias are the small vertical holes, filled with metal, that connect one layer of wiring to the layer above or below it. A chip has billions; an interposer has them through its whole thickness; a package substrate has them drilled by laser through each sheet of film.

Every added layer is another set of vias that can fail, which is why yield falls as packages and substrates grow.

[[#^advanced-packaging|Read it in Advanced Packaging →]]

wafersilicon wafer, 300 mm wafer, wafers, silicon wafers, 300 mm wafers

The polished disc of ultrapure silicon that chips are built on, 300 millimeters across and less than a millimeter thick. Hundreds of chips are printed on one disc and cut apart at the end.

Five firms hold roughly 85 percent of 300 millimeter capacity, and this $11.4 billion market supports trillions of dollars of downstream value.

[[#^silicon-and-wafers|Read it in Silicon and Wafers →]]

wafer fab equipmentWFE, front-end equipment, equipment billings, wafer processing equipment, semiconductor equipment, chipmaking tools, chipmaking equipment

The collective name for the machines that process wafers inside a fab: printing systems, deposition and etch chambers, cleaning tools and measurement systems. It excludes the packaging and test machines used afterwards.

Spending on this equipment was a record $116.9 billion in 2025 and is the best early indicator of how much new chip capacity is being built, roughly two years before it produces anything.

[[#^deposition-and-etch|Read it in Deposition and Etch →]]

wafer sortwafer test, probe test, wafer probe

Wafer sort is the first test a chip gets, while it is still on the wafer. A probe card lowers thousands of needles onto the pads of one die, a tester drives signals in and reads the answers, and any die that answers wrong is marked and never packaged.

Proving a die good before it is packaged now saves the eight memory stacks and the substrate that a bad die would otherwise waste.

[[#^test-and-assembly|Read it in Test and Assembly →]]

wafers per monthwafers a month, wafer starts, wafer starts per month, WSPM, wafer starts a month, million wafers per month

Wafers per month is how fab capacity is counted: the number of wafers a plant can start through its line each month. A TSMC gigafab runs more than 100,000; SMIC's advanced lines run about 45,000. Figures are often converted to 8-inch or 12-inch equivalents so plants with different wafer sizes can be compared.

China leads the world in wafers per month and almost none of it is advanced, and that gap is what the contest is about.

[[#^foundries-and-fabs|Read it in Foundries and Fabs →]]

wet chemicalswet chemical, wet processing, wet clean, cleaning chemicals, process chemicals

Wet chemicals are the liquids a wafer is dipped in or sprayed with between steps: acids that strip a layer, solvents that remove resist, and ultrapure water rinses. Wet processing is any step done in liquid.

Five firms held more than 60 percent of the market as of 2021, and BIS controls wet tools by how selectively they etch one material over another.

[[#^chemicals-gases-and-photoresist|Read it in Chemicals, Gases and Photoresist →]]

yielddie yield, yields, packaging yield, package yield, stack yield

The percentage of chips on a wafer that work. Flaws land at random, so the larger the chip the more likely it is to catch one, and yield falls steeply as chips get bigger.

Yield sets the cost of a working AI chip: a ten point yield drop on a reticle-sized die hurts far more than a 30 percent rise in the wafer price.

[[#^the-economics-of-ai|Read it in The Economics of AI Chips →]]
