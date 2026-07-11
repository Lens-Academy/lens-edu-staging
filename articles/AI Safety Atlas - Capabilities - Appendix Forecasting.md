---
title: "Appendix: Forecasting"
author:
  - "Markov Grey"
  - "Charbel-Raphaël Segerie"
source_url: "https://ai-safety-atlas.com/chapters/v1/capabilities/appendix-forecasting/"
published: 2026-06-18
created: 2026-06-18
accessed: 2026-06-18
description:
tags:
  - "article-importer"
---

## Effective Compute

### Hardware Efficiency

The first factor in increasing effective compute is - how efficient is the hardware that we produce at doing computation?

**AI chips are getting about 35% more powerful each year, but we're approaching physical limits.** Since around 2010, the raw computational performance (FLOP/s) of GPUs in FP32 precision has grown by roughly 1.35× per year ([Epoch AI, 2023](https://epoch.ai/trends); [Hobbahn et al., 2023](https://epoch.ai/blog/trends-in-machine-learning-hardware)). The improvement comes from things like denser transistors, specialized AI circuitry, and switching to lower-precision number formats. Performance per dollar has improved rapidly, and hardware at any given precision and fixed performance level becomes 30% cheaper each year. At the same time, manufacturers continue to introduce more powerful and expensive hardware ([Epoch AI, 2025](https://epoch.ai/data/machine-learning-hardware))

**In the near future this trend seems likely to continue, but thermodynamic limits will eventually stop this trend.** Chips can only get so energy-efficient before physics says “no”. Every computation generates heat as a fundamental law of physics, not an engineering problem. Current analysis suggests there is room for a 50 to 1,000× improvement in energy efficiency before we hit fundamental CMOS limits, with a 50% chance that improvements cease before a roughly 200× improvement on existing technology. These estimates suggest that CMOS processors are likely sufficiently efficient to power substantially larger AI training runs than today.[^7] This implies we have significant headroom to scale using current silicon paradigms through 2030 and beyond, although hardware R&D returns may eventually diminish as we approach physical limits. Beyond these limits, training runs would likely require radical changes to computing paradigms, like a shift to adiabatic computing ([Ho et al., 2023](https://epoch.ai/blog/limits-to-the-energy-efficiency-of-cmos-microprocessors); [Sevilla et al., 2024](https://epoch.ai/blog/can-ai-scaling-continue-through-2030)).

![Figure 1.49](https://ai-safety-atlas.com/_astro/bdb134a95993fb4816fbb2e070440888792c5400c6146ba14308ce1b04b25327.rtTkIm2P_Z4EhJy.webp)

*Figure 1.49: Currently observed trends in the efficiency of hardware used for ML over the last decades. We can see a clear year by year increase in peak computational performance ([Hobbahn et al., 2023](https://epoch.ai/blog/trends-in-machine-learning-hardware)).*

![Figure 1.50](https://ai-safety-atlas.com/_astro/a3f2cc4543e98eccdfae46d3b4d6d37dcd1ae74150ef2d9f996d9fb8a9f23b22.C7PGqa6m_1iKt6I.webp)

*Figure 1.50: A forecast of the future using the Growth and AI Transition Endogenous (GATE) playground. This graph shows investments in hardware R&D improving the efficiency of AI chips (measured in units of FLOP/year per $). Eventually, hardware efficiency is capped by physical limits. The red line showcases aggressive parameter settings, green is conservative parameter settings. The red zone highlights the difference in timelines to full automation between aggressive and conservative models ([Epoch AI, 2025](https://epoch.ai/gate)).*

### Software and Algorithmic Efficiency

The second factor in increasing effective compute is - how well we can utilize all the existing hardware that we have. This is separate from just making the physical hardware itself more efficient.

**Better algorithms have cut the compute needed for a given result by ~3× per year.** The level of compute needed to achieve a given level of performance has halved roughly every 8 months[^8]. This rapid improvement means that the compute required to achieve specific levels of capability on benchmarks can drop by orders of magnitude over just a few years of algorithmic progress. The improvements to compute efficiency explain roughly 35% of performance improvements in language modeling since 2014, with the other 65% coming from just building more chips and running them longer. Overall, this means we're getting smarter about using available hardware, and not just throwing more compute at problems ([Epoch AI, 2023](https://epoch.ai/trends); [Ho et al., 2024](https://epoch.ai/blog/algorithmic-progress-in-language-models)).

![Figure 1.51](https://ai-safety-atlas.com/_astro/eb988e1bd46f91bd8a3352483694e332564153ad2ca3ff6d618f7c60ba6f7b92.Bz_2uoRR_Z2rUai8.webp)

*Figure 1.51: Estimates of the contributions of scaling and algorithmic innovation in terms of the raw compute that would be naively needed to achieve a state-of-the-art level of performance. The contribution of algorithmic progress is roughly half as much as that of compute scaling ([Ho et al., 2024](https://epoch.ai/blog/algorithmic-progress-in-language-models))*

![Figure 1.52](https://ai-safety-atlas.com/_astro/dcc6ba3945fe1ec4e062f6a686d913ea6e7ab4f1bb26838f47bf35c190c648e5.D1B_mtUY_YW8zW.webp)

*Figure 1.52: A forecast of the future using the Growth and AI Transition Endogenous (GATE) playground. This graph shows algorithmic improvements over time. By developing better algorithms and using higher-quality data, it becomes possible to do more with the same hardware (measured in units of "effective FLOP per FLOP"). The red line showcases aggressive parameter settings, green is conservative parameter settings. The red zone highlights the difference in timelines to full automation between aggressive and conservative models ([Epoch AI, 2025](https://epoch.ai/gate)).*

### Semiconductor Production

The third factor in increasing effective compute is - how many chips can you actually build?

**Total available computing power from NVIDIA chips has grown by approximately 2.3x per year since 2019, enabling the training of ever-larger {--{"author":"Luc's AI","timestamp":1783790193745}@@models. **NVIDIA--}{++{"author":"Luc's AI","timestamp":1783790193745}@@models.** NVIDIA++} designs a dominant share of AI training chips, and Taiwan's TSMC serves as the primary chip fab for these manufacturers. The AI chip supply chain is highly concentrated. In 2024 TSMC dedicated roughly 5% of their advanced chip production to AI accelerators—the rest goes to phones, computers, and other electronics ([Sevilla et al., 2024](https://epoch.ai/blog/can-ai-scaling-continue-through-2030)). If AI labs want dramatically more chips, TSMC would need to shift priorities, expand capacity, and compete with other customers who also want cutting-edge semiconductors ([Epoch AI, 2025](https://epoch.ai/data-insights/nvidia-chip-production)).

![Figure 1.53](https://ai-safety-atlas.com/_astro/c50e93e29d48ea44d7b4c1168a76e45ec55a4d5777f5fbdd2374ab45a19b9db4.BRIBDf5H_1UzYmU.webp)

*Figure 1.53: An estimate the world’s installed NVIDIA GPU compute capacity, broken down by GPU model ([Epoch AI, 2025](https://epoch.ai/data-insights/nvidia-chip-production)).*

![Figure 1.54](https://ai-safety-atlas.com/_astro/fafb3fa17ebfdb40c333e59acb398411662a9e81c2e67e9bcf707975fe0f69fb.CgpxvwKI_e4WKe.webp)

*Figure 1.54: Table showcasing estimates costs and times to overcome various  constraints in scaling up compute production ([Edelman & Ho, 2025](https://epoch.ai/gradient-updates/compute-scaling-will-slow-down-due-to-increasing-lead-times)).*

*Interactive figure 1.7: Quarterly revenue of NVIDIA Corporation across its main market segments, reported in US dollars. NVIDIA manufactures graphics processing units (GPUs), which were originally used for gaming and are now used to train AI models. This data is not adjusted for inflation ([Our World in Data, 2023](https://ourworldindata.org/artificial-intelligence)).*

**Investment doesn't immediately make chip production go faster.** If some country wants to build their own TSMC equivalent, then it can take 4-5 years to build a new cutting-edge fab (accounting for construction and permitting), though upgrading an existing fab takes less time, around 2 years in addition to billions in investment ([Edelman & Ho, 2025](https://epoch.ai/gradient-updates/compute-scaling-will-slow-down-due-to-increasing-lead-times); [Epoch AI, 2025](https://arxiv.org/abs/2503.04941)). Besides the existing competition for chips from TSMC, another factor is that the machines TSMC needs to manufacture the chips. These are almost exclusively made by a single company: ASML in the Netherlands ([Blablová, 2025](https://epoch.ai/gradient-updates/why-china-isnt-about-to-leap-ahead-of-the-west-on-compute)). These extreme ultraviolet (EUV) lithography machines cost between $150 million to $380 million each. If/When someone (e.g. TSMC) wants to expand production, they can't just order fifty more next month. They join an already long waitlist ([Edelman & Ho, 2025](https://epoch.ai/gradient-updates/compute-scaling-will-slow-down-due-to-increasing-lead-times); [Sevilla, AXRP Podcast, 2024](https://axrp.net/episode/2024/10/04/episode-37-jaime-sevilla-forecasting-ai.html)).

![Figure 1.55](https://ai-safety-atlas.com/_astro/4379d79917d0fad0adf1f7afd9c561ce5440c4e95b5373929e365f94e04a7b64.fMk2I0Ny_10wiQB.webp)

*Figure 1.55: A forecast using the Growth and AI Transition Endogenous (GATE) playground. This graph shows potential scale up of AI chip fabrication to meet demand for AI workloads. Due to the exponential cost of rapid expansions, growth is reduced by an “adjustment costs” parameter. The red line showcases aggressive parameter settings, green is conservative parameter settings. The red zone highlights the difference in timelines to full automation between aggressive and conservative models ([Epoch AI, 2025](https://epoch.ai/gate)).*

## Investment and Training Costs

**The cost in USD of training frontier models has grown by 3.5x per year per year since 2020.** If trends continue, we'll see the training cost for a single model approach billion-dollar training runs by 2027. The cost breaks down roughly as: 50-65% for hardware (spread across its useful life), 30-45% for the researchers and engineers, and 2-6% for electricity. This is venture capital and Big Tech money so far, but these numbers are approaching scales where only nations or the largest corporations can compete ([Cottier et al., 2025](https://epoch.ai/blog/how-much-does-it-cost-to-train-frontier-ai-models)).

![Figure 1.56](https://ai-safety-atlas.com/_astro/f06a1e183fe969589fa929fb1d9dff951a83b6e6a6df2caf3aceb704e885d37d._td_T3Sm_Ziy6Jq.webp)

*Figure 1.56: Breakdown of model development costs for selected models. Hardware costs are amortized to the total number of chip-hours spent on experiments and training. R&D staff costs cover the duration of development, from initial experiments to publication ([Cottier et al., 2025](https://epoch.ai/blog/how-much-does-it-cost-to-train-frontier-ai-models)).*

*Interactive figure 1.8: Hardware and energy cost to train notable AI systems. This data is expressed in US dollars, adjusted for inflation ([Our World in Data, 2023](https://ourworldindata.org/artificial-intelligence)).*

![Figure 1.57](https://ai-safety-atlas.com/_astro/caa98a2ded9650e9f63377f25ab123f847060f358bca6814166ad4ca387c587a.CeDOP_zi_1yAh1x.webp)

*Figure 1.57: Amortized hardware cost plus energy cost for the final training run of frontier models. The selected models are among the top 10 most compute-intensive for their time. Amortized hardware costs are the product of training chip-hours and a depreciated hardware cost, with 23% overhead added for cluster-level networking. Open circles indicate costs which used an estimated production cost of Google TPU hardware. These costs are generally more uncertain than the others, which used actual price data rather than estimates ([Cottier et al., 2025](https://epoch.ai/blog/how-much-does-it-cost-to-train-frontier-ai-models)).*

**The acquisition cost in USD of the hardware used to train frontier AI models has grown by 2.5x per year since 2016.** To give you a sense of how much training a frontier model costs, the total amortized cost of developing Grok-4 (released in July 2025), including hardware and electricity, is estimated at $480 million USD. The acquisition cost of the hardware to train Grok-3, including GPUs, other server components, and networking, is estimated at $3 billion USD. The hardware used to train Grok 4 may have been even more expensive ([Epoch AI, 2025](https://epoch.ai/trends)).

*Interactive figure 1.9: Money put into privately held AI companies by private investors. This excludes publicly traded companies (e.g., Big Tech companies) and companies’ internal spending, such as R&D or infrastructure. Expressed in US dollars, adjusted for inflation ([Our World in Data, 2023](https://ourworldindata.org/artificial-intelligence)).*

**An unknown question is whether the returns to productivity gains will justify continued investment.** 2025 saw a lot of news headlines about circular investment and an “AI bubble”. If AI can automate significant portions of cognitive work, capturing even a fraction of the global labor market makes trillion-dollar investments rational. However, massive investments face increasing hurdles due to structural constraints. As compute scales up, the lead time between project initiation and deployment lengthens significantly—roughly one year for every ten-fold increase in scale—creating a feedback loop that naturally slows the pace of scaling ([Edelman & Ho, 2025](https://epoch.ai/gradient-updates/compute-scaling-will-slow-down-due-to-increasing-lead-times)). This uncertainty regarding long-term returns over extended periods may drive investors to prefer incremental scaling, breaking up projects into smaller chunks to gauge returns before committing further, rather than making massive upfront investments ([Edelman & Ho, 2025](https://epoch.ai/gradient-updates/compute-scaling-will-slow-down-due-to-increasing-lead-times)). Several things could break the pattern entirely: models hitting a capability ceiling where more compute doesn't help, regulations capping training runs or data center sizes, energy costs making large runs uneconomical, or economic recession drying up capital. Each represents a distinct way scaling could stop independent of technical feasibility.

![Figure 1.58](https://ai-safety-atlas.com/_astro/fedf8fa8bc073d10df89d911a0e41ba559e0c33fad24a14aabb18db80cdf10e5.BsCjVJpR_246vhG.webp)

*Figure 1.58: A forecast using the Growth and AI Transition Endogenous (GATE) playground. GATE predicts high levels of investment in AI-related capital and R&D to support massive expansions of the effective compute stock. This involves major reallocations away from conventional capital investments and consumption, and occurs before AI generates significant economic value, motivated by the large payoffs from AI automation. The red line showcases aggressive parameter settings, green is conservative parameter settings. The red zone highlights the difference in timelines to full automation between aggressive and conservative models ([Epoch AI, 2025](https://epoch.ai/gate)).*

![Figure 1.59](https://ai-safety-atlas.com/_astro/b14c4e692da0b2b03657cff6d8eae07677920f65fd7f8ac8faeb0a6a46aa8923.BY3OFUkL_Zu2K9B.webp)

*Figure 1.59: Large investments in AI precede the economic benefits of automation, driven by expectations of large future payoffs. At the start of simulations, there is a brief period with substantial AI investment but with little generated economic value. However, as automation proceeds the value generated by AI grows rapidly, comprising the majority of output within a few years. The GATE model thus captures the dynamic where it is worth making major upfront investments to enjoy the value generated by AI. The investment is measured as the fraction of yearly economic output that is reinvested in AI, while the benefit is measured as the fraction of yearly output that can be attributed to the deployment of digital workers. The red line showcases aggressive parameter settings, green is conservative parameter settings. The red zone highlights the difference in timelines to full automation between aggressive and conservative models ([Epoch AI, 2025](https://epoch.ai/gate)).*

## Power Consumption

**Training frontier models requires enough electrical power to run a small city.** GPT-4's training run likely consumed around 50 megawatts, equivalent to powering roughly 40,000 US homes. If compute scaling continues at 4-5× per year, frontier training runs will require 4-16 gigawatts by 2030—matching the Grand Coulee Dam, America's largest power plant ([You et al., 2025](https://epoch.ai/blog/power-demands-of-frontier-ai-training)).

**Energy costs remain small relative to hardware costs but this could change.** Currently, electricity costs represent only 2-6% of total training costs, with hardware and labor dominating the budget ([Cottier et al., 2024](https://epoch.ai/blog/how-much-does-it-cost-to-train-frontier-ai-models)). But if training runs scale to 10+ gigawatts while hardware efficiency improvements slow down, energy could become a much larger fraction of costs. At $0.05 per kilowatt-hour, a 10 GW training run running for 100 days costs roughly $120 million just for electricity. That's still less than the hardware, but it's no longer negligible. And in practice, securing multi-gigawatt power supplies might cost significantly more than wholesale electricity rates suggest.

![Figure 1.60](https://ai-safety-atlas.com/_astro/487591961ef339d5cf030b1222adb956d309714c87b08469b99bb08fc9428db7.BsohuGYB_ZXOfNq.webp)

*Figure 1.60: Historic trend and forecast for the electricity demand of the largest individual frontier training runs ([You et al., 2025](https://epoch.ai/blog/power-demands-of-frontier-ai-training)).*

![Figure 1.61](https://ai-safety-atlas.com/_astro/10b45a2130b1b013ff68caa43e3dda39f356bdcca7355ce8bfa17e2bb74b99ad.BqNUWOtj_6chaO.webp)

*Figure 1.61: The projected power consumption for planned frontier datacenters for selected AI companies ([Epoch AI, 2025](https://epoch.ai/data/data-centers)).*

**Scaling AI systems to the forecasted levels of 2030 will require substantial power infrastructure.** A training run of $2 times 10^29$ FLOP would require approximately 6 GW of power, assuming improvements in hardware efficiency. This scale necessitates data center campuses ranging from 1 to 5 GW by the end of the decade ([Sevilla et al., 2024](https://epoch.ai/blog/can-ai-scaling-continue-through-2030)). Lead times increase with scale: every additional 10× increase in compute stock adds roughly one year to project timelines. Constructing the necessary large-scale power plants typically takes 2-3 years ([Edelman & Ho, 2025](https://epoch.ai/gradient-updates/compute-scaling-will-slow-down-due-to-increasing-lead-times)). Despite these hurdles, the cost of power remains a small fraction of data center expenses—roughly one-tenth the cost of the chips - making the capital investment rational given the potential returns ([Ho et al., 2025](https://epoch.ai/gradient-updates/is-almost-everyone-wrong-about-americas-ai-power-problem)).

*Interactive figure 1.10: Total electricity generated in each country or region, measured in terawatt-hours ([Our World in Data, 2024](https://ourworldindata.org/energy-production-consumption)).*

*Interactive figure 1.11: The levelized cost of energy (LCOE) accounts for everything, the cost of building the power plant, plus the ongoing costs in keeping it operational over the lifetime of the plant. The cost of energy generation per watt has been falling for decades, and even more dramatically for renewable sources ([Our World in Data, 2026](https://ourworldindata.org/grapher/levelized-cost-of-energy)).*

---

[^7]:  CMOS (Complementary Metal-Oxide-Semiconductor) is the primary paradigm in processor production. The majority of all digital integrated circuits (CPUs, GPUs, RAM, mobile SoCs) produced today are CMOS.

[^8]:  95% confidence interval of 5 to 14 months
