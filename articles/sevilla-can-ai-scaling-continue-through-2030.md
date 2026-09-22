---
title: "Can AI scaling continue through 2030?"
author:
  - "Jaime Sevilla"
  - "Tamay Besiroglu"
  - "Ben Cottier"
  - "Josh You"
  - "Edu Roldán"
  - "Pablo Villalobos"
  - "Ege Erdil"
source_url: "https://epoch.ai/publications/can-ai-scaling-continue-through-2030"
published: 2024-08-20
created: 2026-09-22
accessed: 2026-09-22
llm-review:
  date: 2026-09-22
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-22
    kind: "live"
description: "We investigate four constraints to scaling AI training: power, chip manufacturing, data, and latency. We predict 2e29 FLOP runs will be feasible by 2030."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

We investigate the scalability of AI training runs. We identify electric power, chip manufacturing, data and latency as constraints. We conclude that 2e29 FLOP training runs will likely be feasible by 2030.

## Introduction ^introduction

In recent years, the capabilities of AI models have significantly improved. Our research suggests that this growth in computational resources accounts for [a significant portion of AI performance improvements](https://epoch.ai/blog/algorithmic-progress-in-language-models).[^note-1] The consistent and predictable improvements from scaling have led AI labs to [aggressively expand the scale of training](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year), with training compute expanding at a rate of approximately 4x per year.

To put this 4x annual growth in AI training compute into perspective, it outpaces even some of the fastest technological expansions in recent history. It surpasses the [peak growth rates of mobile phone adoption](https://ourworldindata.org/grapher/ict-adoption?time=1980..2011) (2x/year, 1980-1987), [solar energy capacity installation](https://ourworldindata.org/grapher/installed-solar-pv-capacity?time=2002..2010) (1.5x/year, 2001-2010), and [human genome sequencing](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4494865/pdf/pbio.1002195.pdf) (3.3x/year, 2008-2015).

Here, we examine whether it is technically feasible for the current rapid pace of AI training scaling—approximately 4x per year—to continue through 2030. We investigate four key factors that might constrain scaling: power availability, chip manufacturing capacity, data scarcity, and the “latency wall”, a fundamental speed limit imposed by unavoidable delays in AI training computations.

Our analysis incorporates the expansion of production capabilities, investment, and technological advancements. This includes, among other factors, examining planned growth in advanced chip packaging facilities, construction of additional power plants, and the geographic spread of data centers to leverage multiple power networks. To account for these changes, we incorporate projections from various public sources: semiconductor foundries’ planned expansions, electricity providers’ capacity growth forecasts, other relevant industry data, and our own research.

We find that training runs of 2e29 FLOP will likely be feasible by the end of this decade. **In other words, by 2030 it will be very likely _possible_ to train models that exceed GPT-4 in scale to the same degree that GPT-4 exceeds GPT-2 in scale.[^note-2]** If pursued, we might see by the end of the decade advances in AI as drastic as the difference between the rudimentary text generation of GPT-2 in 2019 and the sophisticated problem-solving abilities of GPT-4 in 2023.

Whether AI developers will actually pursue this level of scaling depends on their willingness to invest hundreds of billions of dollars in AI expansion over the coming years. While we briefly discuss the economics of AI investment later, a thorough analysis of investment decisions is beyond the scope of this report.

Figure 1: Estimates of the scale constraints imposed by the most important bottlenecks to scale. Each estimate is based on historical projections. The dark shaded box corresponds to an interquartile range and light shaded region to an 80% confidence interval.

For each bottleneck we offer a conservative estimate of the relevant supply and the largest training run they would allow.[^note-3] Throughout our analysis, we assume that training runs could last between two to nine months, reflecting [the trend towards longer durations](https://epoch.ai/data-insights/training-length-trend). We also assume that when distributing AI data center power for distributed training and chips companies will only be able to muster about [[#^appendix-b-fraction-of|10% to 40% of the existing supply]].[^note-4]

**Power constraints.** Plans for data center campuses of 1 to 5 GW by 2030 have already [been](https://www.ans.org/news/article-5842/amazon-buys-nuclearpowered-data-center-from-talen/) [discussed](https://www.theinformation.com/articles/microsoft-and-openai-plot-100-billion-stargate-ai-supercomputer?rc=9mzoog), which would support training runs ranging from 1e28 to 3e29 FLOP (for reference, GPT-4 was likely around 2e25 FLOP). Geographically distributed training could tap into multiple regions’ energy infrastructure to scale further. Given current projections of US data center expansion, a US distributed network could likely accommodate 2 to 45 GW, which assuming sufficient inter-data center bandwidth would support training runs from 2e28 to 2e30 FLOP. Beyond this, an actor willing to pay the costs of new power stations could access significantly more power, if planning 3 to 5 years in advance.

**Chip manufacturing capacity.** [AI chips](https://epoch.ai/blog/chips-topic-overview) provide the compute necessary for training large AI models. Currently, expansion is constrained by advanced packaging and high-bandwidth memory production capacity. However, given the scale-ups planned by manufacturers, as well as hardware efficiency improvements, there is likely to be enough capacity for 100M H100-equivalent GPUs to be dedicated to training to power a 9e29 FLOP training run, even after accounting for the fact that GPUs will be split between multiple AI labs, and in part dedicated to serving models. However, this projection carries significant uncertainty, with our estimates ranging from 20 million to 400 million H100 equivalents, corresponding to 1e29 to 5e30 FLOP (5,000 to 300,000 times larger than GPT-4).

**Data scarcity.** Training large AI models requires correspondingly large datasets. The indexed web contains about 500T words of unique text, and is projected to increase by 50% by 2030. Multimodal learning from image, video and audio data will likely moderately contribute to scaling, plausibly tripling the data available for training. After accounting for uncertainties on data quality, availability, multiple epochs, and multimodal tokenizer efficiency, we estimate the equivalent of 400 trillion to 20 quadrillion tokens available for training by 2030, allowing for 6e28 to 2e32 FLOP training runs. We speculate that synthetic data generation from AI models could increase this substantially.

**Latency wall.** The latency wall represents a sort of “speed limit” stemming from the minimum time required for forward and backward passes. As models scale, they require more sequential operations to train. Increasing the number of training tokens processed in parallel (the ‘batch size’) can amortize these latencies, but this approach has a limit. Beyond a ‘critical batch size’, further increases in batch size yield diminishing returns in training efficiency, and training larger models requires processing more batches sequentially. This sets an upper bound on training FLOP within a specific timeframe. We estimate that cumulative latency on modern GPU setups would cap training runs at 3e30 to 1e32 FLOP. Surpassing this scale would require alternative network topologies, reduced communication latencies, or more aggressive batch size scaling than currently feasible.

**Bottom line.** While there is substantial uncertainty about the precise scales of training that are technically feasible, our analysis suggests that training runs of around 2e29 FLOP are likely possible by 2030. This represents a significant increase in scale over current models, similar to the size difference between GPT-2 and GPT-4. The constraint likely to bind first is power, followed by the capacity to manufacture enough chips. Scaling beyond would require vastly expanded energy infrastructure and the construction of new power plants, high-bandwidth networking to connect geographically distributed data centers, and a significant expansion in chip production capacity.

Below, we analyze the potential bottlenecks that may constrain AI scaling this decade in greater detail. We then consider which constraints may be most binding, and whether scaling up AI training to this degree would be economically and financially feasible.

## Power constraints ^power-constraints

In this analysis, we project the power requirements necessary to sustain the current trajectory of scaling AI training. We then explore potential strategies to meet these power demands, including on-site power generation, local grid supply, and geographically distributed training networks. Our focus is on AI training runs conducted within the United States, examining the feasibility and constraints of each approach.[^note-5]

**Data center campuses** between **1 to 5 gigawatt (GW)** are likely possible by 2030. This range spans from Amazon’s [960 MW nuclear power contract](https://www.ans.org/news/article-5842/amazon-buys-nuclearpowered-data-center-from-talen/) in Pennsylvania to the 5 GW campuses that [OpenAI/Microsoft](https://www.datacenterdynamics.com/en/news/microsoft-openai-consider-100bn-5gw-stargate-ai-data-center-report/) and [Sam Altman](https://www.datacenterdynamics.com/en/news/openai-pitched-white-house-on-multiple-5gw-data-centers/) have been reported to be pursuing. Such campuses would support AI training runs ranging from **1e28 to 3e29 FLOP**, given expected advancements in the energy efficiency of ML GPUs.

Scaling beyond single-campus data centers would involve **geographically distributed training**, which could utilize energy infrastructure across multiple regions. Given current projections, a distributed training network could accommodate a demand of **2 to 45 GW**, allowing for training runs of **2e28 to 2e30 FLOP**. Bandwidth could also constrain the largest training run that could be done in such a network. Concretely, inter-data center bandwidths of **4 to 20 Petabits per second (Pbps),** which are on trend for existing data centers, would support training runs of **3e29 to 2e31 FLOP**. This is likely high enough that bandwidth would not be a major obstacle compared to securing the power supply.[^note-6]

Larger training runs are plausible: we expect the cost of the infrastructure needed to power GPUs during a training run to be around 40% of the cost of the GPUs themselves by 2030, and rapid expansion of the power supply via natural gas or solar power could be arranged within three to five years of a decision to expand—though this could be constrained by infrastructure-level bottlenecks.

#### The current trend of AI power demand ^the-current-trend-of

AI model training currently consumes a small but rapidly growing portion of total data center power usage. Here, we survey existing estimates of current demand, extrapolates future trends, and compares these projections to overall data center and national power capacity.

Large-scale AI training relies primarily on hardware accelerators, specifically GPUs. The current state-of-the-art GPU is Nvidia’s H100,[^note-7] which has a thermal design power (TDP) of 700W. After accounting for supporting hardware such as cluster interconnect and CPUs, and data center-level overhead such as cooling and power distribution, its peak power demand goes up to 1,700W per GPU.[^cite-8] 

Using the power demand per GPU, we can estimate the installed power demand for frontier models.  The recent [Llama 3.1 405B model](https://ai.meta.com/blog/meta-llama-3-1/), with its 4e25 FLOP training run, used a cluster of 16,000 H100 GPUs. This configuration required 27MW of total installed capacity (16,000 GPUs × 1,700W per GPU). While substantial—equivalent to the average yearly consumption of 23,000 US households[^note-9]—this demand is still small compared to large data centers, which can require hundreds of megawatts. How much will this increase by the end of the decade? Frontier training runs by 2030 are projected to be 5,000x larger than Llama 3.1 405B, reaching 2e29 FLOP.[^note-10] However, we don’t expect power demand to scale by as much. This is for several reasons.

First, we expect hardware to become more power-efficient over time. The peak FLOP/s per W achieved by GPUs used for ML training have increased by around 1.28x/year between 2010 and 2024.[^note-11] If continued, we would see 4x more efficient training runs by the end of the decade.

Second, we anticipate more efficient hardware usage in future AI training. While Llama 3.1 405B used FP16 format (16-bit precision), there’s growing adoption of FP8 training, as seen with [Inflection-2](https://inflection.ai/inflection-2#:~:text=Inflection%2D2%20was%20trained%20on%205%2C000%20NVIDIA%20H100%20GPUs%20in%20fp8%20mixed%20precision%20for%20~10%C2%B2%E2%81%B5%20FLOPs.). An Anthropic co-founder [has suggested](https://x.com/jackclarkSF/status/1773380854812987679) FP8 will become standard practice in frontier labs. We expect that training runs will switch over to 8-bit by 2030, which will be ~2x as power-efficient (e.g. The H100 performs around 2e15 FLOP/s at 8-bit precision, compared to 1e15 FLOP/s at 16-bit precision).[^note-12]

Third, we expect training runs to be longer. Since 2010, the length of training runs [has increased by 20% per year](https://epoch.ai/data/ai-models#training-time-growth) among notable models, which would be on trend to 3x larger training runs by 2030. Larger training run durations would spread out energy needs over time. For context, Llama 3.1 405B was trained over [72 days](https://x.com/EpochAIResearch/status/1815778832265232483), while other contemporary models such as GPT-4 are [speculated](https://www.semianalysis.com/p/gpt-4-architecture-infrastructure) to have been trained over ~100 days. However, we think it’s unlikely that [training runs will exceed a year](https://epoch.ai/blog/the-longest-training-run), as labs will wish to adopt better algorithms and training techniques on the order of the timescale at which these provide substantial performance gains.

Given all of the above, we expect training runs in 2030 will be 4x (hardware efficiency) \* 2x (FP8) \* 3x (increased duration) = 24x more power-efficient than the Llama 3.1 405B training run. Therefore, on-trend 2e29 FLOP training runs in 2030 will require 5,000x (increased scale) / 24x ≈ 200x more power than was used for training of Llama 3.1 405B, for a power demand of 6 GW.

These figures are still relatively small compared to the total installed power capacity of the US, which is around 1,200 GW, or the 477 GW of power that the US produced on average in 2023.[^note-13] However, they are substantial compared to the power consumption of all US data centers today, which is around 20 GW,[^note-14] most of which is [currently not AI related](https://www.goldmansachs.com/intelligence/pages/AI-poised-to-drive-160-increase-in-power-demand.html). Furthermore, facilities that consume multiple gigawatts of power are unprecedentedly massive—energy-intensive facilities today such as aluminum smelters demand up to around the order of a gigawatt of power, but not much more.[^note-15],[^note-16] In the following sections, we investigate whether such energy-intensive facilities will be possible

#### Power constraints for geographically localized training runs ^power-constraints-for-geographically

For geographically localized training, whether done by a single data center or multiple data centers in a single campus, there are two options for supplying power: on-site generation, or drawing from (possibly multiple) power stations through the local electricity grid.

Companies today are already pursuing on-site generation. Meta bought the rights to the power output of a [350MW solar farm in M](https://www.prnewswire.com/news-releases/arevon-and-meta-announce-long-term-contracts-for-349-megawatts-of-new-solar-energy-302079224.html)[issouri](https://www.prnewswire.com/news-releases/arevon-and-meta-announce-long-term-contracts-for-349-megawatts-of-new-solar-energy-302079224.html) and a [300MW solar farm in Arizona](https://www.datacenterdynamics.com/en/news/meta-signs-renewable-energy-deal-in-arizona-with-orsted/).[^note-17] Amazon owns a data center campus in Pennsylvania with a contract for up to [960 megawatts](https://www.utilitydive.com/news/aep-exelon-pjm-interconnection-amazon-data-center-talen-ferc-isa/719869/) from the adjoining 2.5 GW nuclear plant. The primary motivation behind these deals is to save on grid connection costs and guarantee a reliable energy supply. In the coming years such data centers might allow unprecedentedly large training runs to take place—960 MW would be over 35x more power than the 27 MW required for today’s frontier training runs.

Could one acquire even more power through on-site generation? Currently, there are at least [27 power plants](https://database.earth/energy/power-plants/united-states-of-america) with capacity greater than 2.5 GW in the US,[^note-18] ranging in size up to the [Grand Coulee](https://en.wikipedia.org/wiki/Grand_Coulee_Dam) [6.8GW hydroelectric plant](https://en.wikipedia.org/wiki/Grand_Coulee_Dam) [in Washington](https://en.wikipedia.org/wiki/Grand_Coulee_Dam). However, a significant portion of the power capacity from existing plants is likely already committed through long-term contracts.[^note-19] This limited availability of spare capacity suggests that existing US power plants may face challenges in accommodating large-scale on-site generation deals. The scarcity of spare energy capacity also breeds disputes. For example, Amazon’s bid for 960 MW of on-site nuclear power [is challenged by two utilities](https://spectrum.ieee.org/amazon-data-center-nuclear-power) seeking to cap Amazon at its current 300 MW purchase. They argue this arrangement evades shared grid costs; such disputes may also inhibit other on-site power deals.

More large-scale plants might be constructed in the coming years, but few have been built recently, and the most recent >3 GW power stations took around five years to build.[^note-20] It seems unlikely that any already-planned US power stations will be able to accommodate an on-site data center in the >3 GW range by 2030.[^note-21] Instead, moving to larger scales will likely require drawing electricity from the grid. 

As a proxy, we can look at data center consumption trends in geographically localized areas. For instance, Northern Virginia is the largest data center hub in the US, housing nearly [300 data centers](https://www.governing.com/infrastructure/the-data-center-capital-of-the-world-is-in-virginia) that are connected to 5 GW of power in peak capacity.[^note-22] The largest Northern Virginia electricity provider, Dominion, [expects](https://virginiamercury.com/2023/11/21/a-5-point-plan-for-data-centers/#:~:text=Grid%20operator%20PJM%E2%80%99s%20grid%20forecast%20projects%20Dominion%E2%80%99s%20data%20center%20load%20will%20quadruple%20over%20the%20next%2015%20years%2C%20while%20NOVEC%E2%80%99s%20will%20rise%20to%20ten%20times%20what%20it%20is%20today.) their data center load to increase 4x in the next fifteen years, for an implied 10% yearly growth rate. If Dominion and other regional providers stick to similar expansion plans, by 2030 we might expect data center power capacity in Northern Virginia to grow to around 10 GW.[^note-23]

Some companies are investigating options for gigawatt-scale data centers, a scale that seems feasible by 2030. This assessment is supported by industry leaders and corroborated by recent media reports. The CEO of NextEra, the largest utility company in the United States, [recently stated](https://www.bloomberg.com/news/articles/2024-06-12/tech-firms-are-asking-energy-giant-nextera-for-enough-electricity-to-power-miami) that while finding a site for a 5-gigawatt AI data center would be challenging, locations capable of supporting 1-gigawatt facilities do exist within the country. It is also consistent with a [media report](https://www.theinformation.com/articles/microsoft-and-openai-plot-100-billion-stargate-ai-supercomputer?rc=9mzoog) indicating that Microsoft and OpenAI are tentatively planning an AI data center campus for 2028 dubbed _Stargate_ that will require “several gigawatts of power”, with an expansion of up to 5 GW by 2030.[^cite-24] 

In sum, current trajectories suggest that AI training facilities capable of accommodating 2 to 5 GW of power demand are feasible by 2030. This assessment is based on three key factors: the projected growth of data center power capacity, exemplified by Northern Virginia’s expected increase from 5 GW to 10 GW; ambitious industry plans for gigawatt-scale data centers, such as the rumored Stargate campus; and utility company assessments indicating that 1 to 5-gigawatt facilities are viable in select US locations. For context, a 5 GW power supply such as the rumored Stargate campus would allow for training runs of 2e29 FLOP by 2030, accounting for expected advances in energy efficiency, and an increase in training duration to over 300 days.[^note-25] Training networks powered by co-located power plants or local electricity networks are unlikely to exceed 10 GW—as this would come close to the total projected power demand across all data centers in Northern Virginia. 

#### Power constraints for geographically distributed training ^power-constraints-for-geographically-2

Distributing AI training beyond a single data center can help circumvent local power constraints. Inter-data center distributed training involves spreading workloads across multiple data centers, which may or may not be in close proximity. This method has likely been used for large models like Gemini Ultra, allowing access to more hardware resources.[^cite-26] Geographically distributed training extends this concept across wider areas, potentially tapping into separate electricity grids. Major tech companies are well-positioned for this approach, with data centers already spread across multiple regions. For example, Google operates data centers in 15 different U.S. states.[^note-27] This approach could enable larger-scale training operations by accessing a broader pool of power resources.

How much power could distributed data center networks access? As with local data center networks, we ground our discussion in historical trends, supplier forecasts and third-party projections of data center power growth. In a later section we discuss factors that would affect the feasibility of a major expansion in the US’s overall power supply, which could unlock even more power for data centers.

The potential for US data centers to access electricity is substantial and growing. To accurately assess this capacity, it’s crucial to distinguish between two key metrics: the average rate of actual energy consumption, which accounts for downtime and fluctuations, and the total peak capacity for which data centers are rated. We estimate that average power consumption across US data centers is over 20 GW today.[^note-28] Dominion [has said](https://www.princewilliamtimes.com/news/region-s-sluggish-solar-can-t-match-surging-data-center-demand/article_be0be72f-922b-5b5e-94c0-0ac719be236c.html) that the data centers they serve demand 60% of their capacity on average, and estimates from experts we spoke to suggest that data centers consume around 40-50% of their rated capacity, on average. This suggests an overall capacity of 33 to 50 GW, or ~40 GW as a central estimate.[^note-29] In addition, according to [SemiAnalysis’](https://www.semianalysis.com/) data center industry model, total data center IT capacity in North America (the vast majority of which is in the US) was ~36 GW at the end of 2023 and will be ~48 GW at the end of 2024, which is consistent with this estimate.[^note-30]

![](https://epoch.ai/assets/images/posts/2024/can-ai-scaling-continue-through-2030/datacenter-it-capacity.png)

Figure 2: Reported and planned total installed IT capacity of North America data centers via [SemiAnalysis’ data center industry model](https://www.semianalysis.com/p/datacenter-model). **Important note:** to find total capacity, we must multiply these figures by [PUE](https://en.wikipedia.org/wiki/Power_usage_effectiveness), which ranges from 1.2x for AI data centers to 1.5x for other data centers.

The potential for rapid expansion in data center power capacity is significant, as evidenced by multiple sources and projections.  Historical data from SemiAnalysis indicates tracked data center capacity grew at an annual rate of ~20% between 2019 and 2023, per (see figure 2). Planned expansions in 2024 and 2025 aim to accelerate this, achieving 32% yearly growth if completed on time.

We can also look at growth projections from utilities companies to estimate a feasible growth rate for the overall data center industry. In Northern Virginia, Dominion is planning for a 10-15% annual growth rate[^note-31] in data center power in the coming years, following [24% annual demand growth](https://www.goldmansachs.com/pdfs/insights/pages/generational-growth-ai-data-centers-and-the-coming-us-power-surge/report.pdf) from 2017 to 2023. NOVEC, another Virginia utility, [expects 17% yearly growth](https://virginiamercury.com/2023/11/21/a-5-point-plan-for-data-centers/#:~:text=Grid%20operator%20PJM%E2%80%99s%20grid%20forecast%20projects%20Dominion%E2%80%99s%20data%20center%20load%20will%20quadruple%20over%20the%20next%2015%20years%2C%20while%20NOVEC%E2%80%99s%20will%20rise%20to%20ten%20times%20what%20it%20is%20today.) in the coming years.

Finally, other independent estimates are consistent with a ~15% annual growth rate, such as from [Goldman Sachs](https://www.goldmansachs.com/intelligence/pages/gs-research/generational-growth-ai-data-centers-and-the-coming-us-power-surge/report.pdf), which projects that data center power consumption will grow at an annual rate of 15% to 400 TWh in 2030 (for an average demand of ~46 GW), and from [the Electric Power Research Institute (EPRI)](https://www.epri.com/research/products/3002028905), which considers a 15% growth rate if there is a rapid expansion of AI applications.

Overall, an annual growth rate of 10-30% seems achievable. A central estimate of 15% growth would imply that US data center capacity could grow from 40 GW to up to **90 GW** by 2030, or an increase of **50 GW**. Note again that we are using a range of projections of actual growth to ground estimates of _feasible_ growth, so this figure is arguably conservative.

Given power capacity for all data centers, how much power would be available for AI? Currently, the majority of US data centers are dedicated to non-AI uses such as internet services and cloud computing. For instance, SemiAnalysis tracks 3 GW of installed capacity across AI data centers in North America by the end of 2023. This corresponds to ~8% of total data center capacity.[^note-32] However, the share of power demand from AI data centers is on the rise, and we expect the AI power capacity share to become even larger in the coming years.

Existing forecasts of the annual growth in power demand for non-AI data centers center around 8% to 11%.[^note-33] At a 8% growth rate, demand for non-AI applications would increase from around 37 GW today to around 60 GW by 2030, leaving 90 GW - 60 GW ≈ 30 GW capacity for AI data centers. This would result in roughly a 30 GW / 3 GW ≈ 10x expansion in AI installed capacity, or roughly 47% annual growth on AI installed power capacity.[^note-34] This projection assumes a fixed allocation of growth to non-AI applications. However, if AI applications prove more profitable or strategically important, cloud providers could potentially reallocate resources, leading to even higher growth in AI installed power capacity at the expense of non-AI expansion.

Finally, we estimate how much of this capacity can be dedicated to a single training run. We must account for the fact that this added power capacity will likely be shared between different actors, such as Microsoft, Google, Amazon and so on. Our best guess is that the company with the largest share might get around 33% of the power capacity for AI data centers. Companies can front-load their capacity for training, leading to most of their capacity at the time of starting a large training run to be dedicated to training, perhaps by as much as 80%. In total, this means that 33% x 80% = 26% of the AI data center capacity might be used in a single training run.[^note-35]

Given our estimates, the most well-resourced AI company in the US will likely be able to orchestrate a 30 GW x 26% ≈ 8 GW distributed training run by 2030. After accounting for uncertainties on the relevant growth rates and current capacities, we end up with a conservative estimate of **2 to 45 GW** for the largest supply that a developer will be able to muster for distributed training, which would allow for training runs between **2e28 to 2e30 FLOP** (see figure 3 in a later section). For context, our earlier analysis suggested that single-campus facilities might achieve 2 to 5 GW capacity by 2030. The upper end of our distributed training estimate (45 GW) significantly exceeds this single-campus projection, indicating the potential for distributed training to overcome power bottlenecks.

#### Feasibility of geographically distributed training ^feasibility-of-geographically-distribute

Geographically distributed training runs, which spread workloads across multiple data centers to alleviate power constraints, are likely to be technically feasible at the scale projected in our analysis. This approach builds upon existing practices in AI model training, where computations are already massively parallelized across numerous GPUs. The fundamental structure of AI training facilitates geographical distribution: datasets are divided into batches, with model weight updates occurring only once per batch. In a distributed setup, these batches can be split across various locations, requiring data centers to synchronize and share gradient updates only at the conclusion of each batch.

Evidence for the viability of this approach exists in current practices. For instance, Google’s Gemini Ultra model was reportedly trained across multiple data centers, demonstrating the practicality of geographically dispersed training.[^cite-36] While the exact geographic spread of the data centers used for Gemini Ultra is unclear, its training provides a concrete example of large-scale distributed operations.

The feasibility of widely dispersed data centers in distributed training is constrained by latency. In a scenario where major U.S. data centers are connected by an 11,000 km fiber optic loop (a high-end estimate), the communication latency would be approximately 55ms.[^note-37] Synchronization would require two round trips down the network, taking 110ms. This is using a travel speed that is two-thirds the speed of light, so this latency cannot be reduced as long as we are doing fiber optic communication. So if a training run is completed within 300 days, it could involve at most 300 days / 110ms = 240 million gradient updates.

We are uncertain how large batches can be without compromising training effectiveness. We will assume it to be 60 million tokens—which is [speculated](https://www.semianalysis.com/p/gpt-4-architecture-infrastructure?utm_source=post-email-title&publication_id=329241&post_id=134355860&isFreemail=false&triedRedirect=true) to match the largest batch size achieved by GPT-4 during training. This would allow for ~1e16 tokens (240M batches x 60M tokens/batch) to be seen during training, which under [Chinchilla-optimal scaling](https://epoch.ai/blog/chinchilla-scaling-a-replication-attempt) would allow for a ~6e31 FLOP training run.[^note-38] In other words, latency is not likely to be the binding constraint, even when pessimistically assuming a data center network involving very distant data centers.

Beyond latency, bandwidth also influences the feasibility of large-scale distributed training. Current data center switch technology, exemplified by the [Marvell Teralynx 10](https://www.marvell.com/content/dam/marvell/en/public-collateral/switching/marvell-teralynx-10-data-center-ethernet-switch-product-brief.pdf), provides insight into achievable bandwidth. This data center switch supports 128 ports of 400 Gps each, for a total bandwidth of 51.2 Tbps.[^note-39] Transmitting the gradient updates for a 16T parameter model at 8-bit precision using a standard two-stage ring all-reduce operation would then take 2 x 16T x 8 bit / 51.2 Tbps = 4.9 seconds per trip. Adding 110ms of latency per all-reduce as before, the total time per all-reduce would be 5 seconds in total. Given Chinchilla scaling, this model size would maximize the scale of training that can be accomplished in under 300 days of training, leading to a 3e28 FLOP training run.[^note-40]

However, achievable bandwidths are likely to be much higher than what can be managed by a single Teralynx 10 ethernet switch. First, links between data centers pairs can be managed by multiple switches and corresponding fibers, achieving much larger bandwidths. For instance, each node in [Google’s Stargate network](https://dl.acm.org/doi/10.1145/3230543.3230545) featured 32 switches managing external traffic. In a ring all-reduce setup, a 32-switch data center could dedicate 16 switches to manage the connection with each of its two neighbors. Given the precedent of Google’s B4 network, we think that switch arrangements of 8 to 32 switches per data center pair should be achievable.[^note-41]

Second, better switches and transceivers will likely exist in the future, increasing the achievable bandwidth. The [broader](https://people.ucsc.edu/~warner/Bufs/buf-hist.html) [trend](https://www.wheelersnetwork.com/2023/03/marvell-teralynx-leapfrogs-to-512t.html) of ASIC switches suggests a 1.4 to 1.6x/year increase in bandwidth,[^note-42] which would result in 380 to 850 Tbps ethernet switches by the end of the decade.[^cite-43]

Our final estimate of the achievable inter data center bandwidth by 2030 is **4 to 20 Pbps**, which would allow for training runs of **3e29 to 2e31 FLOP**. In light of this, bandwidth is unlikely to be a major constraint for a distributed training run compared to achieving the necessary power supply in the first place.

Expanding bandwidth capacity for distributed training networks presents a relatively straightforward engineering challenge, achievable through the deployment of additional fiber pairs between data centers. In the context of AI training runs potentially costing hundreds of billions of dollars, the financial investment required for such bandwidth expansion appears comparatively modest.[^note-44]

#### Modeling energy bottlenecks ^modeling-energy-bottlenecks

We conclude that training runs in 2030 supported by a local power supply could likely involve **1 to 5 GW** and reach **1e28 to 3e29** **FLOP** by 2030. Meanwhile, geographically distributed training runs could amass a supply of **2 to 45 GW** and achieve **4 to 20 Pbps** connections between data center pairs, allowing for training runs of **2e28 to 2e30 FLOP**.[^note-45] All in all, it seems likely that training runs between **2e28 to 2e30 FLOP** will be possible by 2030.[^note-46] The assumptions behind these estimates can be found in Figure 3 below.

Figure 3: Projected power consumption of local and distributed data center network setups, alongside the scale of the largest training run they would support, accounting for energy efficiency improvements and bandwidth and latency constraints.

Learn more about our assumptions.

Training run duration

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 5.18e6 | 1.56e7 | 2.33e7 |

Training run duration in seconds (1 million seconds = ~11.6 days). Informed by training times of recent record-setters in training compute that trained for 2-3 months, but allowing for up to 9 months in the future. Bottlenecks such as power capacity may drive longer training runs to eke out more compute. See [Sevilla et al (2022)](https://epoch.ai/blog/the-longest-training-run).

Fraction of resources for the largest training run

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 16% | 26% | 40% |

Percent of total AI resources that will be allocated to the single largest training run. This accounts for resources being divided between competitors, and between inference and training. This applies to the power and chip supplies. Based on a [model](https://www.squiggle-language.com/playground?v=0.9.5#code=eNrVVduO3DYM%2FRVin5JN5NvYk%2BwCfWiCom2AoEFuQIABDI1N28LakiLJMxgU%2FfdSsjFj724WeWzfbIo85Dkiqb%2Bvamz42Lu3qsar2yunx0Ohy6ZX2sIvkBc3mGY7Gcx4Nqc3r87m%2FGzNXhXB2qVJUjY63S79PQ7EkAHEMTS8csqAaui%2FoQ%2BrubHCnXaSh9g5bJPmUxrDhRSyLXnfq4o7oSSdJtHrndxJgnvDLdZAxoGICN0jWDWaCu1LwKiNoHNO29s4Ph6PkVOD7bipj9xgVKkhdlh1TMh6tM6cYnkQteCMC8ZlzTpdsVaPzPIeLTOolXFY9yfGtTaKVx2SD%2B8bxtkg%2Bp7qYqMUzhIe%2B75hruPyzjKn2ICOM2KNe6XudlKOQ%2BlVIhZFkuAGnIIMtzOdVbkdGmyFdWhCtVmS5XFSxFkat0q1PZZSHUvXCVP33LRoXSlkWXNHuSQFxQHxK5oTjLJC40hJ4Hs1OujUEQYuT%2F4akLjA5w9fDgW4k8YQ9EnBQE3RA9UAdhyAFJm%2BST%2BcSIS%2B8BeMW89hExWeRXCYznS4qNQfJtHNJSj3%2FULehT9Jp7Bzm4UGwu%2FkcslxDc9SYLCEfk7GVWOSdOvWmxH1DxBXdc5Y%2Bmms%2FBGofI7NnwxdBN6j%2BQLuVfkCVqm8Mj5XmI2BOp30LvDGT5PvHT9QBg8oR4RaUP%2BSx%2F4E2ogKL4FzvWcMP4ok%2Fcp2Ddk8gWuSIf4aFrP5CEXlW7VsV0RXWAGdpFCO9%2FcShFkIrBcaPACcxyMtkju6OqH1RPS3v76RENnm9r8351TtNqFqL1XmlypRtkIiGlpsUbNfTPcmTrPYjzCbZpgtPOP9KPqaPkIqy1qUxEHIxnDiNVZuNEgz7w8XGpNk05LZ%2Bm3zv9Txs6HFTryhMWqYVP31T6iofDutkNfvH5eZG3I6YCRsfPxYbd8FtN9HtNaJgTuklcbdtNecqu78NgzoHbfgaw1HGg29U7QtK%2FQOf%2Fh%2BpfeGH9DwFiMSXFRGWdW4J1WfV%2FbqGXvscbtejUIMq5lZJvsJpIeVPcTz3fIzUMuueoBy9c%2B%2FKFDRNQ%3D%3D) of the current share of total AI chip stock for Google, Microsoft, and Meta. Note that this is the 80% CI rather than 90%.

Peak GPU efficiency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e15 | 2.00e15 | 4.00e15 |

Theoretical peak FLOP/s per GPU used in the largest training run, before accounting for utilization. We assume FP8 FLOP through the model. FP8 FLOP/s for [NVIDIA H100,](https://www.nvidia.com/en-us/data-center/h100/) without sparsity. We allow for a x2 factor of uncertainty to acknowledge that a different number format might be preferred.

Training GPU utilization

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 20.00% | 37.50% | 60.00% |

GPU throughput actually achieved in the training run, as a percentage of the theoretical peak output of the GPU. Median: the median of known values in the notable models database. Low: utilization as low as 20% occurs in our database (e.g. GPT-3), and might result from a trade-off between optimizing efficiency and increasing cluster size. High: highest known value is 56.5% for LaMDA; we have seen approximately 60% in experiments on models with ~10B parameters, e.g. in [MosaicGPT Training Benchmarks](https://github.com/mosaicml/examples/tree/70f07314ca8f27f121d511af2d73bfbb0d019523/examples/llm/throughput).

Installed power capacity per GPU

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1527.9 | 1704 | 1846 |

Installed power capacity per GPU in Watts, including all system components, such as CPU, memory, networking, etc. We also include power for power for cooling, to cover power distribution losses, lighting and other non-IT facility equipment, ie the data center power usage effectiveness (PUE). The average power consumption for a 1016 H100 DGX SuperPOD is 1.4MW, or 1389W per GPU. The peak consumption is 1420W per GPU (see [table 4 here](https://docs.nvidia.com/nvidia-dgx-superpod-data-center-design-dgx-h100.pdf)). We assume a PUE of 1.1 to 1.3 based on estimates from [Patterson et al (2021)](https://arxiv.org/abs/2104.10350) and [Semianalysis](https://www.semianalysis.com/p/ai-datacenter-energy-dilemma-race#:~:text=On%20top%20of,datacenter%20power%20consumption.).

GPU power efficiency growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.16 | 1.28 | 1.42 |

Factor by which power demand per FLOP/s declines per year due to improved efficiency. Estimated from a [regression](https://drive.google.com/file/d/1i9uGDEgHR01k7EQzvODlxTkM007emVjI/view?usp=sharing) that expands the [Hobbhahn et al (2023)](https://epoch.ai/blog/trends-in-machine-learning-hardware) dataset.

US AI data centers power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 3.04e9 |  |

Installed power capacity of US AI data centers, in Watts. Includes installed hardware and PUA. [Semianalysis](https://www.semianalysis.com/p/datacenter-model) reports 2537 MW of critical IT capacity for AI data centers in US and Canada bvy the end of 2023. We assume 1.2x PUE in line with Semianalysis.

US total data center power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 3.30e10 | 4.00e10 | 5.00e10 |

Installed power capacity of all US data centers, in Watts. Includes installed hardware and PUA. Average power consumption across US data centers is over 20 GW today. Dominion’s data centers [demand 60%](https://www.princewilliamtimes.com/news/region-s-sluggish-solar-can-t-match-surging-data-center-demand/article_be0be72f-922b-5b5e-94c0-0ac719be236c.html) of their capacity on average, and estimates from experts we spoke to suggest that data centers consume around 40-50% of their rated capacity, on average. This suggests overall capacity of 33 to 50 GW, or ~40 GW as a central estimate. [Semianalysis data](https://www.semianalysis.com/p/datacenter-model) is also consistent with ~40 GW.

Largest data center campus power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 9.60e8 | 2.50e9 | 5.00e9 |

US total power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 1.16e12 |  |

US data center power capacity growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.1 | 1.15 | 1.32 |

US non-AI data center power capacity growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.07 | 1.08 | 1.1 |

Expected growth of US non-AI data center power demand. Note that the non-AI data center demand growth will be capped by the overall growth rate. [Goldman Sachs](https://www.goldmansachs.com/insights/articles/AI-poised-to-drive-160-increase-in-power-demand) project 10% growth of non-AI data center demand through 2030. In 2022-2024, [Semianalysis](https://www.semianalysis.com/p/datacenter-model) forecasts 8% growth through 2022-2028. [EIA](https://iea.blob.core.windows.net/assets/6b2fd954-2017-408e-bf08-952fdd62118a/Electricity2024-Analysisandforecastto2026.pdf) forecasted a conservative 7% growth rate through 2026.

Data center network distance

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 350 | 2945.1 | 10618.45 |

Fiber optic speed

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 2.00e5 |  |

Achievable batch size

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.60e7 | 6.00e7 | 3.60e8 |

Maximum feasible number of tokens per batch in a distributed training run in 2024. The median corresponds to the supposed [max batch size of GPT-4](https://www.semianalysis.com/p/gpt-4-architecture-infrastructure?utm_source=post-email-title) during training. The lower bound corresponds to the largest batch size achieved by [Llama 3.1 405B](https://arxiv.org/abs/2407.21783).

Inter-data-center bandwidth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 4.10e14 | 8.19e14 | 1.64e15 |

Achievable inter data center connections bandwidth in bits per second (bps). Each node in [Google’s Stargate ethernet network](https://dl.acm.org/doi/10.1145/3230543.3230545) in 2014 featured 32 switches managing external traffic, which would correspond to 32/2 = 16 switches per data center pair on a ring all-reduce setup. The JPOP sites (ibidem) featured 16 outward switches. Using modern Teralynx 10 Ethernet Switch on each data center would result in 51.2 Tbps per link.

Inter-data-center bandwidth growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.4 | 1.5 | 1.6 |

Factor by which achievable bandwidth is expected to grow yearly. Corresponding to a [bootstrap](https://colab.research.google.com/drive/14ixx63lTw8sPfkWh_VXlqwhwq-LKkb78#scrollTo=BYeVEPOgVvcn) of the growth trend on a sample of ASIC Ethernet Switches sourced from [here](https://people.ucsc.edu/~warner/Bufs/buf-hist.html) and [here](https://www.wheelersnetwork.com/2023/03/marvell-teralynx-leapfrogs-to-512t.html).

:::callout {title="How much further could power supply be scaled?" collapse="closed"}
At this point, it is unclear to us how far power provision for data centers could scale if pursued aggressively. So far, we have grounded our discussion in the existing power supply for data centers as well as growth projections from utilities, and the results of our model reflect these estimates. How could these numbers change if there is an unprecedented investment in growing the power supply?[^note-47]

Building new power plants seems reasonably affordable and scalable, but there are also important constraints at the grid level (more below). Natural gas and solar plants can be built [relatively](https://blog.parker.com/site/usa/details-home-page/natural-gas-combined-cycle-power-plants-history-trends-and-outlook-us#:~:text=a%20large%20NGCC%20plant%20can%20be%20built%20in%20less%20than%2024%20months.%C2%A0) [quickly](https://uslightenergy.com/how-long-does-it-take-to-build-a-solar-farm/#:~:text=Solar%20farms%20generally%20take%20eight,equipment%2C%20and%20power%20grid%20capacity.), in under two years,[^note-48] while other types of power, such as nuclear and hydroelectricity, require longer timeframes,[^note-49] and there are no full-scale nuclear plants currently in progress in the US.[^note-50]

How much would it cost to grow the power supply? As a baseline for the cost of expanding power, we can look at the construction and operation costs of a gas power plant.[^note-51]

A gas power plant is [estimated](https://www.eia.gov/analysis/studies/powerplants/capitalcost/pdf/Capital_Cost_Study_Discussion_Slides.pdf) to have an overnight capital cost on the order of $2,500 per kilowatt with 95% carbon capture, or ~$900 without carbon capture, while the operation cost is [roughly 4.5 cents per KWh](https://www.eia.gov/electricity/annual/html/epa_08_04.html) (and around 4 cents more if carbon capture is included[^note-52]). However, we should note that the estimates with carbon capture are theoretical, as gas with carbon capture has not been deployed at scale. Gas without carbon capture is cheaper but could be more constrained by politics and corporate commitments (more on this below). Meanwhile, data centers pay around [$8.7 cents per KWh](https://www.semianalysis.com/p/gpu-cloud-economics-explained-the) for electricity. If we assume a 100% premium on top of the operation cost, data centers would pay ~17 cents/KWh for electricity generated by natural gas with carbon capture.

Meanwhile, an H100 GPU requires 1,700W of power and costs ~$30,000, or ~$17,000 per kilowatt. This means that powering a training run that uses H100s with natural gas would require ~$1500-$4000 in capital costs per H100, and ~$2000 in variable costs.[^note-53] So if AI developers had to fund the construction of all the power plants required, this would only increase their hardware costs by around ($4000 + $2000) / $30,000 = 20%. However, this becomes worse after accounting for hardware trends, despite improving efficiency. GPUs are becoming more energy efficient in Watt per FLOP/s at a rate of 2x per three years, but they are also becoming more _price-performant_ in FLOP/dollar at a rate of [2x per two years](https://epoch.ai/blog/trends-in-machine-learning-hardware#executive-summary). So in 2030 each dollar spent on GPUs buys 8x more FLOP, requiring 4x less power, for twice as much power per dollar, and the cost of power would be 40% of the cost of GPUs.

Given these figures, the construction of arbitrarily large power supply networks for data centers is affordable, relative to the cost of the required chips, _if power can be scaled up at the current marginal price_. But at very large scales beyond ~100 GW, it would require unprecedented effort.

Despite AI developers’ potential willingness to invest heavily in solving power bottlenecks, several obstacles may limit the amount of power available for AI training. Transmission lines, essential for connecting power plants to data centers, typically take [about 10 years to complete](https://ifp.org/how-to-save-americas-transmission-system/#barriers-to-building-infrastructure) and often face political challenges. The process of connecting new power generation to the grid, known as interconnection, has become increasingly time-consuming, with average queue durations in the US recently reaching [five years](https://emp.lbl.gov/queues#:~:text=Interconnection%20wait%20times%20are%20also%20on%20the%20rise%3A%20The%20typical%20duration%20from%20connection%20request%20to%20commercial%20operation%20increased%20from%20%3C2%20years%20for%20projects%20built%20in%202000%2D2007%20to%20over%204%20years%20for%20those%20built%20in%202018%2D2023%20%28with%20a%20median%20of%205%20years%20for%20projects%20built%20in%202023%29.).[^note-54] Additionally, new electrical transformers, crucial for power distribution, can take [up to two years to be delivered](https://www.tdworld.com/utility-business/article/21243198/transformative-times-update-on-the-us-transformer-supply-chain#:~:text=New%20transformers%20can%20take%20as%20long%20as%20two%20years%20to%20be%20delivered). These grid-level bottlenecks create uncertainty about the ability to scale up power supply significantly faster than historical growth rates or the most aggressive utility projections, even with substantial financial investments. The long lead times and complex infrastructure requirements make rapid expansion of power capacity challenging, potentially constraining the growth of large-scale AI training operations.

Another potential constraint is [political and regulatory constraints](https://forbes.com/sites/arielcohen/2022/09/14/nimbyism-is-a-bipartisan-energy-problem/) blocking or delaying the construction of power plants, as well as supporting infrastructure such as transmission lines and natural gas pipelines. This could limit or slow down a large scale-up of power. This political constraint may be malleable,[^note-55] especially if there is much government support for facilitating the power infrastructure to support development of advanced AI systems.

Scaling up AI training power through natural gas presents its own set of challenges. Large yearly expansions of capacity amounting several dozens of gigawatts have precedent in the US. For example, the US installed a net 250 GW of natural gas from [2000 to 2010](https://www.iea.org/data-and-statistics/charts/installed-capacity-in-the-united-states-2000-2020-and-projections-up-to-2040-in-the-sustainable-development-scenario), averaging 25 GW per year. But this approach would necessitate increased gas drilling and the construction of additional pipelines to transport the gas to power plants. While at least [one analysis](https://situational-awareness.ai/racing-to-the-trillion-dollar-cluster/#Power) suggests the US could drill enough gas to power an extra 100 GW for AI training, there are differing opinions on the viability of this approach. For instance, NextEra’s CEO has [identified pipeline construction](https://www.bloomberg.com/news/articles/2024-06-12/tech-firms-are-asking-energy-giant-nextera-for-enough-electricity-to-power-miami) as a potential obstacle, arguing that renewable energy might be a more feasible option for powering AI data centers.

Finally, there is a tension between massive power growth and the US government’s goal of switching to [100% carbon pollution-free energy by 2035](https://web.archive.org/web/20230427003146/https://www.whitehouse.gov/climate/#:~:text=Reaching%20100%25%20carbon%20pollution%2Dfree%20electricity%20by%202035), as well as pledges from the three largest cloud compute providers—[Google](https://sustainability.google/operating-sustainably/net-zero-carbon/), [Microsoft](https://blogs.microsoft.com/blog/2020/01/16/microsoft-will-be-carbon-negative-by-2030/), and [Amazon](https://sustainability.aboutamazon.com/climate-solutions/carbon-free-energy?energyType=true)—to become carbon neutral by 2030. This could limit what types of energy sources could be considered[^note-56] (though these commitments may not prove to be binding if there is sufficient economic pressure to scale up AI). For instance, fossil fuel plants may need to be equipped with carbon capture to hold to these commitments, and carbon capture has not yet been tested at scale and may not be ready for widespread deployment by 2030. This tension is especially acute for coal. Coal power may be a source of slack in the power supply, since coal plants are running at [~50% capacity](https://www.eia.gov/electricity/annual/html/epa_04_08_a.html), down from [~70% in 2008](https://www.spglobal.com/marketintelligence/en/news-insights/trending/XoNzLzWA63RKYX9Xn7pG5w2), despite many being designed to provide reliable [“baseload”](https://en.wikipedia.org/wiki/Base_load) power.[^note-57] However, coal is [much more carbon-intensive than gas](https://www.eia.gov/tools/faqs/faq.php?id=74&t=11).

Given these potential bottlenecks, **it is unclear to what degree US power supply can be scaled up arbitrarily by 2030 at a cost resembling the current margin**. For this reason, we conservatively assume that power supply will not be scaled beyond the levels forecasted by utilities and independent analysts.
:::

## Chip manufacturing capacity ^chip-manufacturing-capacity

AI chips, such as GPUs, provide the compute required to train AI models and are a key input in AI scaling. Growth in GPU clusters has been the main driver of compute growth in the past few years, and higher performance, lower latency, higher memory bandwidth GPUs make it feasible to do ever larger training runs. AI scaling could therefore be constrained by the number of state-of-the-art GPUs that chipmakers can produce.

We model future GPU production and its constraints by analyzing semiconductor industry data, including projected packaging capacity growth, wafer production growth, and capital expenditure on fabrication plants (fabs). Our projections indicate that GPU production through 2030 is expected to expand between 30% to 100% per year, aligning with CoWoS packaging and HBM production growth rates.

In our median projection, we expect enough manufacturing capacity to produce 100 million H100-equivalent GPUs for AI training, sufficient to power a 9e29 FLOP training run. This estimate accounts for GPUs being distributed among multiple AI labs and partially used for model serving. However, this projection has significant uncertainty, primarily due to unknowns in advanced packaging and high-bandwidth memory capacity expansions. Our estimates range from 20 million to 400 million H100 equivalents, potentially enabling training runs between 1e29 and 5e30 FLOP (5,000 to 250,000 times larger than GPT-4).

#### Current production and projections ^current-production-and-projections

Recent years have seen rapid growth in data center GPU sales. Nvidia, which has a [dominant market share](https://www.cnbc.com/2024/06/02/nvidia-dominates-the-ai-chip-market-but-theres-rising-competition-.html) in AI GPUs, [reportedly](https://www.hpcwire.com/2024/06/10/nvidia-shipped-3-76-million-data-center-gpus-in-2023-according-to-study/) shipped 3.76 million data center GPUs in 2023, up from 2.64 million units in 2022.[^note-58] By the end of 2023, [650,000](https://www.tomshardware.com/tech-industry/nvidia-ai-and-hpc-gpu-sales-reportedly-approached-half-a-million-units-in-q3-thanks-to-meta-facebook) Nvidia H100 GPUs were shipped to major tech companies. Projections for 2024 suggest a potential threefold increase in shipments, with expectations of [1.5 to 2 million](https://www.tomshardware.com/news/nvidia-to-reportedly-triple-output-of-compute-gpus-in-2024-up-to-2-million-h100s) H100 units shipped. This volume would be sufficient to power a 6e27 FLOP training run.[^note-59]

However, if we extrapolate the ongoing 4x/year trend in training compute to 2030, we anticipate training runs of around 2e29 FLOP. A training run of this size would require almost 20M H100-equivalent GPUs.[^note-60] If we suppose that at most around 20% of total production can be netted by a single AI lab, global manufacturing capacity would need to reach closer to 100M H100-equivalent GPUs by 2030. This far exceeds current production levels and would require a vast expansion of GPU production.[^note-61]

TSMC, the company that serves as Nvidia’s primary chip fab, faces several challenges in increasing production. One key near-term bottleneck is [chip packaging](https://www.semianalysis.com/p/ai-capacity-constraints-cowos-and) capacity—particularly for TSMC’s Chip-on-wafer-on-Substrate (CoWoS) process, which is Nvidia’s main packaging method for their latest GPUs. This packaging process combines logic units with high-bandwidth memory (HBM) stacks into ready-to-use AI chips. Packaging is difficult to scale up rapidly, as new facilities require complex [equipment](https://www.semianalysis.com/p/ai-expansion-supply-chain-analysis) from many vendors. Constructing these facilities also requires [specialized training](https://www.eetimes.com/urgency-felt-around-finding-chip-fab-construction-talent/) for personnel. These constraints have limited TSMC’s AI chip output, despite strong demand from customers like Nvidia.

TSMC is directing significant efforts to address this constraint. The company is [rapidly increasing](https://www.cna.com.tw/news/afe/202402180022.aspx) its CoWoS packaging capacity from 14,000-15,000 wafers per month in December 2023 to a projected 33,000-35,000 wafers per month by the end of 2024.[^note-62] To further expand this capacity, TSMC opened a new fab in 2023, Advanced Backend Fab 6. At full capacity, this fab could process [up to 83,000 wafers per month](https://pr.tsmc.com/english/news/3033), which would more than double TSMC’s advanced packaging volume.[^note-63] TSMC has also [announced plans](https://www.anandtech.com/show/21405/tsmc-to-expand-cowos-capacity-by-60-every-year-through-2026) to increase its packaging capacity by 60% annually through 2026. Recent scale-ups of CoWoS capacity have ranged from [30%](https://finance.yahoo.com/news/tsmc-boosts-cowos-packaging-machine-010259983.html) to [100%](https://www.cna.com.tw/news/afe/202402180022.aspx) annually. If this trend continues, the number of dies of a fixed size that can be produced will likely increase at a similar rate.[^note-64],[^note-65]

The production of HBM chips themselves is another significant constraint on GPU manufacturing. HBM chips are [nearly sold out](https://www.reuters.com/technology/nvidia-supplier-sk-hynix-says-hbm-chips-almost-sold-out-2025-2024-05-02/) until 2026. While HBM volume is expected to increase [2-3x](https://www.eenewseurope.com/en/hbm-to-be-20-of-dram-market-in-2024/) from 2023 to 2024, much of this growth comes from reallocating capacity from DRAM, which is another class of lower-end memory chips. SK Hynix, the current HBM leader and Nvidia’s main supplier, projects a [60% annual growth](https://www.reuters.com/technology/nvidia-supplier-sk-hynix-says-hbm-chips-almost-sold-out-2025-2024-05-02/) in HBM demand in the medium to long-term (likely referring to revenue), while one analyst firm estimates [45% annual growth](https://www.yolegroup.com/industry-news/hbm-chip-prices-skyrocket-as-ai-boom-fuels-demand/) in production volume from 2023 to 2028.

HBM production and TSMC’s CoWoS packaging capacity, two key constraints in GPU manufacturing, are projected to expand at similar rates in the coming years. Based on TSMC’s announced plans and recent growth trends in CoWoS capacity, which have ranged from 30% to 100% annually, we estimate GPU production will grow at a similar rate in the near term.

Despite the substantial growth in GPU production, wafer production itself is not likely to be the primary limiting factor. Currently, data center GPUs represent only a small portion of TSMC’s total wafer production. Our central estimate of TSMC’s current production capacity for 5nm and 3nm process nodes is 2.2M wafers per year as of early 2024.[^note-66] The projected 2 million H100 GPUs for 2024 would only consume about 5% of the 5nm node’s capacity.[^note-67] Even with the projected growth rates, it’s unlikely that GPU manufacturing will dominate TSMC’s leading-edge capacity in the immediate future. Instead, the main constraints on expanding GPU production appear to be chip packaging and HBM production.

However, it is plausible that GPU manufacturing could eventually come to dominate TSMC’s leading-edge nodes. There is precedent for such a scenario; in 2023, [Apple absorbed around 90%](https://www.digitimes.com/news/a20230515PD201/tsmc-n3b-3nm-apple-chips+components.html) of TSMC’s 3nm production. Given the high profit margins on AI chips, Nvidia could potentially outbid competitors like Apple and Qualcomm for TSMC’s advanced wafer capacity. While we think this is plausible, this scenario is not featured in our mainline analysis.

#### Modeling GPU production and compute availability ^modeling-gpu-production-and

TSMC forecasted AI server demand to grow at [50% annually](https://investor.tsmc.com/chinese/encrypt/files/encrypt_file/reports/2024-04/34ff75e23e53246302ce3a8d90d0423c57c6b120/TSMC%201Q24%20Transcript.pdf) over the next five years. Given TSMC’s historical [5 percentage point yearly increase](https://www.macrotrends.net/stocks/charts/TSM/taiwan-semiconductor-manufacturing/operating-margin) in operating margins, which investors expect to continue due to [price hikes](https://seekingalpha.com/news/4113751-tsmc-ponders-boosting-ai-chip-production-services-for-nvidia-morgan-stanley), we estimate actual GPU volume growth at around 35% per year.[^note-68] This is conservative compared to other projections: [AMD expects 70% annual growth](https://www.futuriom.com/articles/news/how-big-is-the-datacenter-ai-chip-market/2024/01#:~:text=The%20question%20is%2C%20how%20high,%29%20of%20more%20than%2070%25.) for data center chips through 2027, implying about 60% annual GPU volume growth assuming similar price increases.[^note-69] These more aggressive estimates align closely with near-term CoWoS packaging and HBM production scale-up projections discussed above, lending them credibility. We take this range of estimates into account, and project production of GPU dies to expand somewhere between 30% and 100% per year.

We expect that there will be enough wafer capacity to sustain this expansion. TSMC’s historical trends show capex growth of [15% annually](https://finbox.com/NYSE:TSM/explorer/capex/#:~:text=Looking%20back%20at%20the%20last,Similar%20Metrics) and wafer capacity expansion of 8% yearly from 2014 to 2023.[^note-70] TSMC might increase its capex dedicated to expanding GPU production and substantially expand the production of GPU-earmarked-wafers, packaging and other parts of the production. If TSMC accelerates its capex growth to match their expected growth in the AI server market of [50% annual growth](https://investor.tsmc.com/chinese/encrypt/files/encrypt_file/reports/2024-04/34ff75e23e53246302ce3a8d90d0423c57c6b120/TSMC%201Q24%20Transcript.pdf), the historical relationship between input and output growth suggests that total wafer capacity could expand by 27% per year.[^note-71] Overall, this points to a growth rate of leading-edge wafer production of between 5% and 20% per year.

We have appreciable uncertainty about current leading-edge wafer production, and assume that this is somewhere between 100k to 330k/month. At 5 to 20% yearly growth, we project the total stock of leading-edge wafers produced by 2030 to be between 10M and 37M. Based on TSMC’s and others’ projections, we expect around 20% of these wafers to be dedicated to producing data center GPUs.  

These projections indicate that 2e30 to 4e31 FLOP/year worth of global stocks of H100 equivalents will be produced in aggregate. Of course, only some fraction of this will be dedicated to a single training run, since individual labs will only receive some small fraction of shipments, labs will earmark their GPUs to inference and other experiments, and training runs will likely last less than a year. At current rates of improvements in hardware and algorithms and growing budgets for AI, training runs [will likely not exceed six months](https://epoch.ai/blog/the-longest-training-run) if hardware or software progress does not slow. We assume that training runs will last around 2 to 9 months; on the higher end if progress in hardware and software stalls, and the lower end if progress accelerates relative to today.

It is likely that AI chips will be distributed across many competing labs, with some lab owning some non-trivial fraction of global compute stocks. For instance, Meta reportedly bought [one fourth of H100 shipments to major companies in 2023](https://www.statista.com/statistics/1446564/nvidia-h100-gpu-shipments-by-customer/). [[#^appendix-b-fraction-of|We estimate]] that recently, the share of data center GPUs owned by a single lab at any point in time might be somewhere between 10% and 40%.

Of this allocation, some fraction will likely be tied up with serving models and unavailable for training. It is difficult to know what fraction this might be. However, we can use a simple heuristic argument. [A simple analysis](https://epoch.ai/blog/optimally-allocating-compute-between-inference-and-training) suggests AI labs should allocate comparable resources to both tasks. If this holds, and compute for training [continues to grow 4x per year](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year), then we should expect about 80% of the total available compute to be used to train new models.[^note-72]

Putting all this together leads us to the following picture. On the median trajectory, about 100M H100-equivalents could, in principle, be dedicated to training to power an 9e29 FLOP training run. However, this projection carries significant uncertainty, with our estimates ranging from 20 million to 400 million H100-equivalents, corresponding to 1e29 to 5e30 FLOP. To establish an upper bound, we considered a hypothetical scenario where TSMC’s entire capacity for 5nm and below is devoted to GPU production, from now until 2030. In this case, the potential compute could increase by an order of magnitude, reaching 1e30 to 2e31 FLOP. This upper limit, based on current wafer production projections, illustrates the maximum possible impact on AI training capabilities if existing constraints in packaging, HBM production, and wafer allocation were fully resolved. Figure 4 below illustrates these estimates, and lists the assumptions behind them.

Figure 4: Distribution of H100-equivalent GPUs and FLOP available for the largest AI training run in 2030 under different scenarios. “Projected TSMC capacity” estimates TSMC’s capacity for GPU production based on historical trends and projections, while “Full TSMC capacity” is a hypothetical where 100% of TSMC’s leading-edge wafer capacity goes to GPU production.

Learn more about our assumptions.

Training run duration

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 5.18e6 | 1.56e7 | 2.33e7 |

Training run duration in seconds (1 million seconds = ~11.6 days). Informed by training times of recent record-setters in training compute that trained for 2-3 months, but allowing for up to 9 months in the future. Bottlenecks such as power capacity may drive longer training runs to eke out more compute. See [Sevilla et al (2022)](https://epoch.ai/blog/the-longest-training-run).

Fraction of resources for the largest training run

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 16% | 26% | 40% |

Percent of total AI resources that will be allocated to the single largest training run. This accounts for resources being divided between competitors, and between inference and training. This applies to the power and chip supplies. Based on a [model](https://www.squiggle-language.com/playground?v=0.9.5#code=eNrVVduO3DYM%2FRVin5JN5NvYk%2BwCfWiCom2AoEFuQIABDI1N28LakiLJMxgU%2FfdSsjFj724WeWzfbIo85Dkiqb%2Bvamz42Lu3qsar2yunx0Ohy6ZX2sIvkBc3mGY7Gcx4Nqc3r87m%2FGzNXhXB2qVJUjY63S79PQ7EkAHEMTS8csqAaui%2FoQ%2BrubHCnXaSh9g5bJPmUxrDhRSyLXnfq4o7oSSdJtHrndxJgnvDLdZAxoGICN0jWDWaCu1LwKiNoHNO29s4Ph6PkVOD7bipj9xgVKkhdlh1TMh6tM6cYnkQteCMC8ZlzTpdsVaPzPIeLTOolXFY9yfGtTaKVx2SD%2B8bxtkg%2Bp7qYqMUzhIe%2B75hruPyzjKn2ICOM2KNe6XudlKOQ%2BlVIhZFkuAGnIIMtzOdVbkdGmyFdWhCtVmS5XFSxFkat0q1PZZSHUvXCVP33LRoXSlkWXNHuSQFxQHxK5oTjLJC40hJ4Hs1OujUEQYuT%2F4akLjA5w9fDgW4k8YQ9EnBQE3RA9UAdhyAFJm%2BST%2BcSIS%2B8BeMW89hExWeRXCYznS4qNQfJtHNJSj3%2FULehT9Jp7Bzm4UGwu%2FkcslxDc9SYLCEfk7GVWOSdOvWmxH1DxBXdc5Y%2Bmms%2FBGofI7NnwxdBN6j%2BQLuVfkCVqm8Mj5XmI2BOp30LvDGT5PvHT9QBg8oR4RaUP%2BSx%2F4E2ogKL4FzvWcMP4ok%2Fcp2Ddk8gWuSIf4aFrP5CEXlW7VsV0RXWAGdpFCO9%2FcShFkIrBcaPACcxyMtkju6OqH1RPS3v76RENnm9r8351TtNqFqL1XmlypRtkIiGlpsUbNfTPcmTrPYjzCbZpgtPOP9KPqaPkIqy1qUxEHIxnDiNVZuNEgz7w8XGpNk05LZ%2Bm3zv9Txs6HFTryhMWqYVP31T6iofDutkNfvH5eZG3I6YCRsfPxYbd8FtN9HtNaJgTuklcbdtNecqu78NgzoHbfgaw1HGg29U7QtK%2FQOf%2Fh%2BpfeGH9DwFiMSXFRGWdW4J1WfV%2FbqGXvscbtejUIMq5lZJvsJpIeVPcTz3fIzUMuueoBy9c%2B%2FKFDRNQ%3D%3D) of the current share of total AI chip stock for Google, Microsoft, and Meta. Note that this is the 80% CI rather than 90%.

Peak GPU efficiency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e15 | 2.00e15 | 4.00e15 |

Theoretical peak FLOP/s per GPU used in the largest training run, before accounting for utilization. We assume FP8 FLOP through the model. FP8 FLOP/s for [NVIDIA H100,](https://www.nvidia.com/en-us/data-center/h100/) without sparsity. We allow for a x2 factor of uncertainty to acknowledge that a different number format might be preferred.

Training GPU utilization

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 20.00% | 37.50% | 60.00% |

GPU throughput actually achieved in the training run, as a percentage of the theoretical peak output of the GPU. Median: the median of known values in the notable models database. Low: utilization as low as 20% occurs in our database (e.g. GPT-3), and might result from a trade-off between optimizing efficiency and increasing cluster size. High: highest known value is 56.5% for LaMDA; we have seen approximately 60% in experiments on models with ~10B parameters, e.g. in [MosaicGPT Training Benchmarks](https://github.com/mosaicml/examples/tree/70f07314ca8f27f121d511af2d73bfbb0d019523/examples/llm/throughput).

GPU efficiency growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.31 | 1.44 | 1.59 |

Factor by which GPU performance in FLOP/s at a fixed precision improves each year. According to our [latest estimates](https://drive.google.com/file/d/1i9uGDEgHR01k7EQzvODlxTkM007emVjI/view?usp=sharing) of the trend in tensor FP16 performance for AI chips. We assume that the growth rate is similar in different number formats.

Current GPU stock

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.40e6 | 2.20e6 | 3.50e6 |

Number of H100-equivalent AI chips available at EOY 2023. This estimate takes into account reports of H100 shipments ([example](https://www.tomshardware.com/tech-industry/nvidia-ai-and-hpc-gpu-sales-reportedly-approached-half-a-million-units-in-q3-thanks-to-meta-facebook)), estimates of H100 and older GPU shipments based on annual [revenues](https://investor.nvidia.com/news/press-release-details/2024/NVIDIA-Announces-Financial-Results-for-Fourth-Quarter-and-Fiscal-2024/#:~:text=Full%2Dyear%20revenue%20rose%20217%25%20to%20a%20record%20%2447.5%20billion), and an analyst’s [estimate](https://www.theregister.com/2024/05/21/google_now_thirdlargest_in_datacenter/) of Google TPU production.

Current annualized GPU production

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e6 | 1.85e6 | 4.63e6 |

Annualized state-of-the-art GPU production (in number of H100-equivalents) at EOY 2023. [650k](https://www.tomshardware.com/tech-industry/nvidia-ai-and-hpc-gpu-sales-reportedly-approached-half-a-million-units-in-q3-thanks-to-meta-facebook) H100s shipped in 2023, [1.5M-2M](https://www.tomshardware.com/news/nvidia-to-reportedly-triple-output-of-compute-gpus-in-2024-up-to-2-million-h100s) expected in 2024. The start of 2024 would see (0.65\*1.75)^0.5 ~= 1.1M/yr production. We expect about 750k more from Google TPUs and A100s.

Growth of GPU production

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.3 | 1.7 | 2 |

Factor by which the total number of new GPU chips manufactured grows each year, measured in raw chip count rather than H100-equivalent units. This parameter ignores any year-over-year improvements in performance per die (i.e., it just scales the quantity of chips produced). The value of this parameter is informed by recent and planned growth in CoWoS and HBM capacity (30%, 45%, 100% annual growth), which reportedly is a current bottleneck to SotA GPU production.

Current monthly TSMC wafer production

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e5 | 1.80e5 | 3.33e5 |

Current TSMC production of 300mm-equivalent wafers per month for <7nm nodes. Point estimates put the combined monthly production of 5nm and 3nm wafers between 160,000 and 220,000 wpm at the start of 2024. The wider bounds are a guesstimate.

Growth of TSMC CapEx

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.16 | 1.23 | 1.33 |

Factor by which TSMC’s capital expenditures grow each year. Average capex growth in the last decade was [15%/yr](https://finbox.com/NYSE:TSM/explorer/capex/#:~:text=Looking%20back%20at%20the%20last,Similar%20Metrics). However, TSMC expects [50% CAGR](https://investor.tsmc.com/chinese/encrypt/files/encrypt_file/reports/2024-04/34ff75e23e53246302ce3a8d90d0423c57c6b120/TSMC%201Q24%20Transcript.pdf) in revenue from the AI server market over the next 5 years, which could drive up their capex. Overall estimate is a weighted geometric mean with 75% weight on the historical growth. Bounds: guesstimate.

TSMC volume-capex ratio

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.25 | 0.53 | 0.75 |

Ratio of TSMC wafer production output growth rate to capex input growth rate. Median: Average annual capex growth from 2014 to 2023 was about 15% (see other parameter). Based on [TSMC annual reports](https://www.tsmc.com/english/aboutTSMC/dc_annual_report), total wafer output grew from 8 million 12-inch equivalent wafers in 2014 to 15 million in 2022, suggesting an average annual growth rate of 8%. Bounds: guesstimate.

Dies per wafer

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 20 | 28 | 40 |

Number of good dies for a state-of-the-art GPU, per 300mm wafer. Using this [calculator](https://web.archive.org/web/20220327163600/https://caly-technologies.com/die-yield-calculator/). Wafer diameter of 300mm and H100-sized die of 814mm^2, assuming a square die. Defect density of 0.15, 0.1 and 0.05 for 10th, 50th, 90th percentiles, based on this [data](https://www.anandtech.com/show/16028/better-yield-on-5nm-than-7nm-tsmc-update-on-defect-rates-for-n5$.). Future GPUs like Blackwell may use multiple dies, but we account for that as a GPU efficiency improvement.

## Data scarcity ^data-scarcity

Scaling up AI training runs requires access to increasingly large datasets. So far, AI labs have relied on web text data to fuel training runs. Since the amount of web data generated year to year grows more slowly than the data used in training, this will not be enough to support indefinite growth. In this section, we summarize our previous work on [data scarcity](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data), and expand it by estimating further possible gains in scale enabled by multimodal and synthetic data.

The largest training datasets known to have been used in training are on the order of 15 [trillion tokens](https://epoch.ai/trends) of publicly available text and code data.[^note-73] We estimate that the indexed web contains around [500 trillion](https://epoch.ai/trends) tokens after deduplication, 30 times more data than the largest known training datasets. This could be as low as 100T if only looking at already compiled corpora like CommonCrawl, or as high as 3000T if also accounting for private data.[^note-74] 

Since the [Chinchilla scaling laws](https://epoch.ai/blog/chinchilla-scaling-a-replication-attempt) suggest that one ought to scale up dataset size and model size proportionally, scaling up training data by a factor of 30x by using the entirety of the indexed web would enable AI labs to train models with 30x more data and 30x more parameters, resulting in 900x as much compute, i.e. up to 8e28 FLOP if models are trained to be Chinchilla-optimal.[^note-75],[^note-76],[^note-77]

If the recent trend of [4x/year compute scaling](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year) continues, we would run into this “data wall” for text data in about five years. However, data from other modalities and synthetic data generation might help mitigate this constraint. We will argue that multimodal data will result in effective data stocks of 450 trillion to 23 quadrillion tokens, allowing for training runs of 6e28 to 2e32 FLOP. Furthermore, synthetic data might enable scaling much beyond this if AI labs spend a significant fraction of their compute budgets on data generation.[^note-78]

#### Multimodality ^multimodality

AI labs could leverage other data modalities such as image or video.[^note-79] Current multimodal foundation models are trained on datasets where 10-40% is image data.[^cite-80] This data is used to allow models to understand and generate images. Given the usefulness of multimodal understanding, we expect future datasets to include a significant portion of non-text data purely for this purpose. That said, to significantly expand the stock of data, the portion of multimodal data would have to become far greater than that of text data.

Audio, image or video modeling will be valuable enough on its own that AI labs will scale pure audiovisual training. Strong visual abilities could enable models to act as assistants embedded within workflows to [organize information](https://www.theverge.com/2024/6/13/24178144/microsoft-windows-ai-recall-feature-delay) or [operate a web browser](https://github.com/ddupont808/GPT-4V-Act). Models that have fluent, fast, multilingual speech abilities are likely to enable much improved personal voice assistant technology, realtime translation, customer service and more fluid interactions compared to text-only. While current vision models use much less compute than language models,[^note-81] in a scenario where text data is a bottleneck but image data is plentiful, AI labs might start dedicating more resources to image models.

Additional modalities like [protein sequences](https://epoch.ai/blog/biological-sequence-models-in-the-context-of-the-ai-directives#biological-sequence-data) or medical data are also valuable. However, the stock of such data is unlikely to be large enough to significantly expand the stock of available training data.[^note-82]

Multimodal data can further aid language understanding in various ways. Textual data can be transcribed from audio, image and video data, which could further expand the stock of text-related data.[^note-83] More speculatively, non-text data may improve language capabilities through transfer learning or synergy between modalities. For example, it [has been shown](https://arxiv.org/abs/2301.03728) that combining speech and text data can lead to improved performance compared to single-modality models, and it is suggested that such synergies improve with scale. However, research on transfer learning between modalities is scarce, so we can’t conclude with certainty that transfer learning from multimodal data will be useful.

How much visual data would be available for training if one of these scenarios came to pass? The internet has around 10 trillion seconds of video, while the number of images may also be close to 10T.[^note-84] It’s challenging to establish a rate of equivalence between these modalities and text data. Current multimodal models such as [Chameleon-34B](https://arxiv.org/abs/2405.09818) encode images as 1024 tokens, but we expect that as multimodal tokenizers and models become more efficient this will decrease over time. There are examples of efficient encoding of images with as few as [32](https://arxiv.org/abs/2406.07550) [tokens](https://arxiv.org/abs/2406.07550), which after being adjusted by typical text dictionary size would result in 22 tokens per image.[^note-85] We take 22 tokens per image and second of video as a central guess, which means that image and video multimodality would increase the effective stock of data available for training by roughly 400T tokens.[^note-86] This suggests that image and video content might each contribute as much as text to enable scaling. This would allow for training runs ten times larger than if trained purely on text data.

Moreover, there are probably on the order of 500B-1T seconds of publicly available audio on the internet.[^note-87] Neural encoders can store audio at [<1.5 kbps](https://arxiv.org/html/2405.00233v1) while being competitive with standard codecs at much higher bitrate. This corresponds to <100 language-equivalent tokens per second of audio. So it seems likely that total stored audio is on the order of 50-100 trillion tokens, not far from text and image estimates.[^note-88] Hence, this would probably not extend the stock of data by a large factor.

After adding the estimates from all modalities and accounting for uncertainties in the total stock of data, data quality, number of epochs, and tokenizer efficiency, we end up with an estimate of 400 trillion to 20 quadrillion effective tokens available for training, which would allow for training runs of 6e28 to 2e32 FLOP by 2030 (see Figure 5).

Given how wide this interval is, it may be useful to walk through how the high end of the range could be possible. Note that these numbers are merely illustrative, as our actual confidence interval comes from a Monte Carlo simulation based on ranges of values over these parameters.

A high-end estimate of the amount of text data on the indexed web is two quadrillion tokens [(Villalobos et al, 2024)](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data). Meanwhile, a high-end estimate of the number of images and seconds of video on the internet is 40 trillion. If we also use a higher-end estimate of 100 tokens per image or video-second, this would mean four quadrillion visual tokens, or six quadrillion text and visual tokens. If we also assume that this stock of data doubles by 2030, 80% is removed due to quality-filtering ([FineWeb](https://huggingface.co/spaces/HuggingFaceFW/blogpost-fineweb-v1) discarded ~85% of tokens), and models are trained on this data for 10 epochs, this would lead to an effective dataset size of ~20 quadrillion tokens. See Figure 5 for a full list of these parameters and our reasoning for the value ranges we chose.

Figure 5: Projections for the amount of data of each modality and the largest efficient training run they would allow.

Learn more about our assumptions.

Stock of internet text data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.30e14 | 5.10e14 | 2.10e15 |

Number of text tokens available for training. Low:size of Common Crawl. Med: size of the indexed web. High: upper estimate on the size of the indexed web. Estimates taken from [(Villalobos et al, 2024)](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data).

Stock of internet image data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 5.00e12 | 1.00e13 | 2.00e13 |

Stock of internet video data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 4.31e12 | 8.63e12 | 1.73e13 |

Stock of internet audio data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 4.00e11 | 8.00e11 | 1.60e12 |

Seconds of audio available for training. The lower estimate comes from the known quantity of ~150M podcast episodes at an average length of 40 minutes, plus tens of billions of seconds from music. Since this probably undercounts the total number of podcasts and songs and does not include other sources of audio, take 2x that as the central estimate

Growth of data stock

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.03 | 1.07 | 1.1 |

Factor by which the data stock grows per year. [Villalobos et al (2024)](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data) . “Given these considerations, we settle on a confidence interval between 0% and 10% a year. \[95% confidence\]”.

Data epochs

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 3 | 5.00 | 15 |

Multiplier of data stock to account for multiple epochs (multiple passes through training data). [Muennighoff et al. (2023)](https://arxiv.org/abs/2305.16264) find that up to ~4 epochs repeated data is about as valuable as “fresh” data. However, beyond that point there are steep diminishing returns to a marginal epoch, and by 40 epochs there is no marginal gain.

Data quality adjustment

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.1 | 0.2 | 0.4 |

Multiplier of data stock to account for much internet data being duplicated or too low-quality to be used for training. [Villalobos et al (2024)](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data) use a data quality factor between 30% and 50%.

Tokens per image or second of video

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 2 | 22 | 290 |

Tokens per image or second of video in an optimized multimodal model. The 10% percentile corresponds to the additional information contrained in images in sentence image pairs in [Henighan et al (2020)](https://arxiv.org/abs/2010.14701). The central guess corresponds to [Yu et al (2024)](https://arxiv.org/abs/2406.07550), which encodes 256x256 images using 32 tokens, adjusted for a smaller dictionary size than usual text tokenizer. The upper bound corresponds to [Yu et al (2023)](https://arxiv.org/abs/2310.05737), which encodes images as 256 tokens, adjusted for a larger dictionary. See also [[#^appendix-d-equivalence-between|Appendix D]].

Tokens per second of audio

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 2 | 23 | 280 |

Tokens per image or second of video in an optimized multimodal model. The 10% percentile corresponds tokenizing transcribed speech at ~120 words per minute, the central estimate is from SemantiCodec ([Liu et al., 2024](https://arxiv.org/html/2405.00233)) at 350 bps, assuming 15 bits per token. The upper estimate comes from entropy-coded Encodec ([Déffosez et al., 2022](https://arxiv.org/abs/2210.13438)) at 4.2kbps, which is competitive with standard MP3 encodings in terms of quality.

#### Synthetic data ^synthetic-data

In our projections we have only considered human-generated data. Could synthetic data generation be used to greatly expand the data supply? Several important milestones in machine learning have been achieved without relying on human data. [AlphaZero](https://deepmind.google/discover/blog/alphazero-shedding-new-light-on-chess-shogi-and-go/) and [AlphaProof](https://deepmind.google/discover/blog/ai-solves-imo-problems-at-silver-medal-level/) learned to play games and solve geometry problems respectively, matching or surpassing human experts by training purely on self-generated data. Language models fine-tuned on synthetic data can improve their ability to [code](https://arxiv.org/abs/2207.14502) and [answer reasoning questions](https://arxiv.org/abs/2210.11610v2). Small LLMs trained on carefully curated synthetic data [can achieve comparable or superior performance](https://arxiv.org/abs/2309.05463) with significantly fewer parameters and less training data compared to larger models trained on web-scrape text. Large-scale frontier language models like [Llama 3.1](https://arxiv.org/abs/2407.21783) use synthetic data to augment capabilities in areas where collecting high-quality human-annotated data might be challenging or costly, such as long-context capabilities, multilingual performance, and tool use capabilities.

One key reason to expect it should be possible to spend compute to generate high-quality synthetic data is that it’s often easier to verify the quality of an output than it is to generate it. This principle most clearly applies in domains where we can create explicit correctness or quality signals. For example, in coding tasks, we can check if generated code [passes unit tests](https://arxiv.org/abs/2207.14502) or [produces correct outputs for sample inputs](https://arxiv.org/abs/2304.05128). In mathematics, we can [detect logical or arithmetic mistakes](https://arxiv.org/abs/2310.20689) and correct them.

This process enables developers to use compute to generate numerous candidate solutions. They can then systematically verify the correctness or quality of each generated solution, keeping only the high-quality examples while discarding the subpar ones. This approach can computationally create datasets filled with high-quality, synthetic examples. For these tasks, one can expend [more inference compute to generate outputs of higher quality](https://epoch.ai/blog/trading-off-compute-in-training-and-inference).

The verification-easier-than-generation principle may extend beyond coding to various other domains. For instance, it’s often easier to review a research paper for quality and novelty than to write an original paper. Similarly, evaluating the coherence and plausibility of a story is typically less challenging than writing an engaging story from scratch. In these cases, while traditional symbolic systems might struggle with verification, modern AI systems, particularly large language models, have [demonstrated](https://arxiv.org/pdf/2305.01937) evaluation capabilities comparable with human verifiers. This suggests that AI-driven verification could enable creating high-quality synthetic data in these complex domains.

There are additional mechanisms which can be used to generate high-quality synthetic data. For example, it is often the case that a model cannot produce high-quality outputs directly, but it can produce them by combining several smaller steps. This is the key idea behind [chain-of-thought prompting](https://arxiv.org/abs/2201.11903), which can be used to [teach models increasingly complex arithmetic](https://arxiv.org/abs/2309.08589) by bootstrapping from simpler examples.

:::callout {title="Generating endless data" collapse="closed"}
Even if it is technically possible to generate useful synthetic data for a wide range of tasks, the computational overhead of generation might preclude its usage in practice. We can try to estimate how much additional compute would be needed to scale models using synthetic data, compared to a baseline of scaling natural datasets.

Suppose that we have access to a frontier model which we will use as a data generator, and want to train a target model with 10x more compute than the generator. We want the new model to achieve a similar quality than would be obtained by training it on natural data. In previous work, we quantified the extent to which [spending more compute at inference time](https://epoch.ai/blog/trading-off-compute-in-training-and-inference) improves the quality of outputs that models can achieve. Concretely, [chain-of-thought](https://epoch.ai/blog/ai-capabilities-can-be-significantly-improved-without-expensive-retraining) was found to lead to a compute-equivalent-gain of 10x while increasing inference costs by 10x.

This means that increasing the compute usage of the generator during inference by 10x (by generating outputs step by step) raises the quality of the outputs to the level of a model trained on 10x more compute. We can then train our new model on these high-quality outputs to reach the desired level of performance.

Assuming the new model is trained in a compute-optimal fashion, the computational cost of generating the new training dataset would be similar to the cost of training the new model.[^note-89] So using synthetic data would double the compute requirements to train a model, compared to using natural data.

Spending so much compute on synthetic data generation for training would not be unprecedented: DeepMind spent roughly 100x more compute on game simulations to generate data for [AlphaGo Zero](https://deepmind.google/discover/blog/alphago-zero-starting-from-scratch/) than in training the underlying model. However, this is very speculative; for example we haven’t yet seen such a technique applied successfully at scale to frontier model pretraining.
:::

There are several obstacles for using synthetic data. The first is the possibility of [model collapse](https://en.wikipedia.org/wiki/Model_collapse): over-reliance on synthetic data might cause a [degeneration](https://arxiv.org/abs/2305.17493) or [stagnation](https://arxiv.org/abs/2402.07043) of capabilities. It’s unclear if the self-correction mechanisms we have introduced are enough to avoid this outcome, although there are [promising signs](https://arxiv.org/abs/2406.07515).

Increasing compute allocation for data generation can enhance synthetic training data quality through two types of approaches: generating many candidates then filtering for quality, and employing compute-intensive methods like chain-of-thought reasoning to produce superior outputs directly. However, this strategy may face diminishing returns as compute investment grows. When verification or quality estimation processes are imperfect, improvements in data quality may plateau despite additional compute allocation.[^note-90]

Synthetic data is already useful for domains where verification is straightforward such as math and coding or in a small set of domains where collecting high-quality human-annotated data might be challenging or costly, such [as tool use, long-context data](https://arxiv.org/abs/2407.21783) or [preference data](https://arxiv.org/abs/2401.12086). Based on this success, and the intuitions we’ve discussed, we find it plausible that high-quality synthetic data generation is possible in a wide range of fields, beyond what has been demonstrated until now, but this is still uncertain. In this case, data availability might not pose a constraint on scaling, as more could be generated on demand by spending enough compute.

We expect synthetic data to likely be useful for overcoming data bottlenecks. However, the research on the topic is nascent and the state of existing evidence is mixed, and so in this article we conservatively rely on estimates from multimodal data, excluding all types of synthetic data.

## Latency wall ^latency-wall

Another potential constraint to AI scaling is _latency_. There is a minimum time required for a model to process a single datapoint, and this latency grows with the size of the model. Training data is divided into batches, where the data in a batch can be processed in parallel, but there are limits to how large these batches can be. So a training run must last at least as long as the time to process one batch, multiplied by the number of training batches (training dataset size divided by the batch size). Given a finite training run duration, this dynamic limits the size of a model and how much data it can be trained on, and thus the total size of the training run.[^note-91]

This constraint does not pose much of an issue for today’s training runs because typical latencies are very small. However, it could become substantially more important in larger training runs as the minimum latency increases with model size due to the sequential nature of operations across layers.

Training runs can partially manage this latency issue by increasing the batch size, allowing more data to be processed in parallel. In particular, increasing the batch size improves the convergence of stochastic gradient descent, at the cost of more computational resources. This enables one to speed up training at the cost of more compute per batch size, though without substantially increasing the overall compute needed for training. However, beyond a “[critical batch size](https://arxiv.org/pdf/1812.06162)”, further batch increases yield drastically diminished returns per batch. It is therefore not efficient to scale batches indefinitely, and training a model on ever-larger datasets requires increasing the number of batches that need to be processed in sequence.

To get a quantitative sense of the size of this bottleneck, we investigate the relevant sources of latency in the context of training large transformer models. Given batch sizes of 60 million tokens ([speculated](https://www.semianalysis.com/p/gpt-4-architecture-infrastructure?utm_source=post-email-title&publication_id=329241&post_id=134355860&isFreemail=false&triedRedirect=true) to be the batch size of GPT-4), we arrive at training runs between **2e30 to 2e32 FLOP**, which would incur at least 270 to 400 microseconds (µs) of NVLINK and Infiniband communication latency per layer.

However, this may be an underestimate because we expect that the critical batch size likely scales with model size. Under a speculative assumption that batch size can be scaled as roughly the cube root of model size, we estimate the feasibility of training runs around **3e30 to 1e32 FLOP**, which would incur at least 290 to 440 µs of latency with modern hardware.[^note-92]

#### Latency wall given intranode latencies ^latency-wall-given-intranode

We first focus our analysis on intranode latencies, meaning latencies associated with a single node (i.e. a server) hosting multiple GPUs. In this case there are two types of latency that are most pertinent: the _kernel latency_ captures how long a single matrix multiplication or “matmul” takes, and the _communication latency_ measures how long it takes to propagate results between the GPUs.

We anchor our estimates of these two latencies to commonly used machine learning hardware. Experiments by [Erdil and Schneider-Joseph (2024)](https://epoch.ai/blog/data-movement-bottlenecks-scaling-past-1e28-flop) indicate a kernel latency on the order of 4.5 µs for an A100 GPU. Meanwhile, the communication latency in an 8-GPU NVLINK pod for an all-reduce is on the order of 9.2 µs.[^note-93] The total base latency per matmul in an NVLINK pod is then in the order of 13.7 µs.

The latency of each transformer layer follows straightforwardly from this. In particular, each layer of a standard decoder-only transformer model involves four consecutive matrix multiplications,[^note-94] and we must pass each layer twice (for the forward and backward passes). Therefore, the minimal latency per layer and batch is eight times that of a single matrix multiplication, i.e. $8 \times 13.7\,\mu\text{s} = 110\,\mu\text{s}$ .

To finish estimating the largest training run allowed by the latency wall, we need to make some assumption on scaling the number of layers and the amount of training data. As a heuristic, let’s assume that the number of layers in a model is roughly the cube root of the number of parameters,[^cite-95] and that the training dataset size will scale proportionally with the number of parameters, following the Chinchilla rule. In particular, assuming a 120 µs minimum latency per layer and a batch size of 60M tokens, we would find that the largest model that can be trained in nine months is 700T parameters, which allows for Chinchilla-optimal models of up to 6e31 FLOP. Note that this estimate might prove to be too optimistic if the latencies per all-reduce from the NVIDIA Collective Communications Library (NCCL) prove to be slower than reported for intermediate size messages.[^note-96],[^note-97],[^note-98] 

#### Latency wall given latencies between nodes ^latency-wall-given-latencies

So far we have only accounted for intranode (within-node) latencies. This makes sense to some extent; tensor parallelism is often entirely conducted within 8-GPU NVLINK pods precisely to avoid communicating between nodes for each sequential matrix multiplication. However, continued scaling would require _internode_ communication, increasing the latency.

In particular, using a standard InfiniBand tree topology, the latency between nodes scales logarithmically with the number of nodes communicating. Using the [NVIDIA Collective Communications Library (NCCL)](https://developer.nvidia.com/nccl), an all-reduce operation will take at least $t = 7.4\,\mu\text{s} + 2 \times \left(N \times 0.6\,\mu\text{s} + \log_2(M) \times 5\,\mu\text{s}\right)$, where $N$ is the number of GPUs within a pod participating, and $M$ is the number of pods participating (this includes both the communication and kernel latencies).[^note-99] 

For a training run using 2D tensor parallelism, the number of pods corresponds to the number of GPUs coordinating for a 2D tensor parallel calculation. In particular, a cluster performing TP-way 2D tensor parallel training requires a synchronization of TP GPUs, for which we will have 2.75 GPUs on average communicating within each 8-GPU pod, and $\sqrt{\text{TP}} / 2.75$ pods total.

For instance, a 300M H100 cluster using 2,000-way 2D tensor parallelism would involve then $\sqrt {2000} / 2.75 = 16$ pods per all-reduce, incurring a 7.4 µs + 2 x (2.75 x 0.6 µs + log2(16) x 5 µs) = 50 µs latency, which corresponds as before to a 8 x  50 µs = 400 µs latency per layer and batch. This is the cluster size that would allow training the largest possible model in under nine months and with 60M batch size, reaching 7e30 FLOP given projections of hardware efficiency.[^note-100]

#### How can these latencies be reduced? ^how-can-these-latencies

Communication latency might be significantly reduced with improvements to the cluster topology. For instance, a mesh topology could bypass the logarithmic scaling of the internode latency, at the cost of a more complex networking setup within data centers (since you would need to have direct connections between all nodes). 

Another solution might involve larger servers with more GPUs per pod, to reduce the internode latency, or more efficient communication protocols—for instance, for training [Llama 3.1](https://arxiv.org/abs/2407.21783) Meta created a fork of the NVIDIA Collective Communications Library (NCCL) called NCCLX that is optimized for high latency setups, which they claim can shave off tens of microseconds during communications.

Alternatively, we might look into ways to increase the batch size or reduce the number of layers. [Previous research by OpenAI](https://arxiv.org/pdf/1812.06162) relates the critical batch size – after which you see large diminishing returns to training – to how dispersed are gradients with respect to one’s training data. Based on this, [Erdil and Schneider-Joseph (2024)](https://epoch.ai/blog/data-movement-bottlenecks-scaling-past-1e28-flop) conjecture that the batch size might be scaled with the inverse of the reducible model loss, which [per Chinchilla](https://epoch.ai/blog/chinchilla-scaling-a-replication-attempt) scales as roughly the cube root of the number of model parameters.[^note-101] If this holds, it would push back the latency wall by an order of magnitude of scaling, see figure 7 below.

Little work has been done on how the number of layers ought to be scaled and whether it could be reduced. Some experimental work indicates that it is possible to [prune up to half of the intermediate layers](https://arxiv.org/abs/2403.17887) of already trained transformers with a small degradation of performance. This indicates that removing some layers before training might be possible, though it is far from clear. For the time being, we ignore this possibility.

After accounting for uncertainties, we conclude that scaling past 1e32 FLOP will require changes to the network topology, or alternative solutions to scale batch sizes faster or layers slower than theoretical arguments would suggest.

Figure 6: Largest training runs permitted by latency, and corresponding latencies per layer.

Learn more about our assumptions.

Training run duration

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 5.18e6 | 1.56e7 | 2.33e7 |

Training run duration in seconds (1 million seconds = ~11.6 days). Informed by training times of recent record-setters in training compute that trained for 2-3 months, but allowing for up to 9 months in the future. Bottlenecks such as power capacity may drive longer training runs to eke out more compute. See [Sevilla et al (2022)](https://epoch.ai/blog/the-longest-training-run).

Peak GPU efficiency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e15 | 2.00e15 | 4.00e15 |

Theoretical peak FLOP/s per GPU used in the largest training run, before accounting for utilization. We assume FP8 FLOP through the model. FP8 FLOP/s for [NVIDIA H100,](https://www.nvidia.com/en-us/data-center/h100/) without sparsity. We allow for a x2 factor of uncertainty to acknowledge that a different number format might be preferred.

Training GPU utilization

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 20.00% | 37.50% | 60.00% |

GPU throughput actually achieved in the training run, as a percentage of the theoretical peak output of the GPU. Median: the median of known values in the notable models database. Low: utilization as low as 20% occurs in our database (e.g. GPT-3), and might result from a trade-off between optimizing efficiency and increasing cluster size. High: highest known value is 56.5% for LaMDA; we have seen approximately 60% in experiments on models with ~10B parameters, e.g. in [MosaicGPT Training Benchmarks](https://github.com/mosaicml/examples/tree/70f07314ca8f27f121d511af2d73bfbb0d019523/examples/llm/throughput).

GPU efficiency growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.31 | 1.44 | 1.59 |

Factor by which GPU performance in FLOP/s at a fixed precision improves each year. According to our [latest estimates](https://drive.google.com/file/d/1i9uGDEgHR01k7EQzvODlxTkM007emVjI/view?usp=sharing) of the trend in tensor FP16 performance for AI chips. We assume that the growth rate is similar in different number formats.

Achievable batch size

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.60e7 | 6.00e7 | 3.60e8 |

Maximum feasible number of tokens per batch in a distributed training run in 2024. The median corresponds to the supposed [max batch size of GPT-4](https://www.semianalysis.com/p/gpt-4-architecture-infrastructure?utm_source=post-email-title) during training. The lower bound corresponds to the largest batch size achieved by [Llama 3.1 405B](https://arxiv.org/abs/2407.21783).

GPU kernel latency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 4.50e-06 |  |

Minimum time to complete a single matrix multiplication in a modern GPU, in seconds, assuming no kernel fusion. We take this from Erdil and Schneder-Joseph (forthcoming).

Base communication latency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 6.80e-06 |  |

Irreducible communication latency in seconds. We take the LL tree setting from the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc).

Variable intrapod latency (NVlink)

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 6.00e-07 |  |

Relationship between number of ranks and NVLINK communication latency in seconds. We take the LL tree setting from the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc).

Variable interpod latency (InfiniBand)

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 5.00e-06 |  |

Relationship between logarithm of the number of nodes and interpod InfiniBand communication latency in seconds. We take the LL tree setting from the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc).

Minimum TP mini-batch size

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 330 |  |

Minimum size of mini-batch size per GPU when doing 2D tensor parallelism while keeping utilization high. This corresponds to 2e15 FLOP/s x 1 byte/param / (2 FLOP/multadd x 3e12 byte/s), corresponding to the estimated values for the minimum mini-batch size that a single H100 can process efficiently in FP8 format while balancing computation time and memory accesses. See appendix E for more.

Layer scaling

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.21 | 0.27 | 0.33 |

Doublings in the number of layers per doubling of model parameters. Hoffman et al scale the number of layers as 0.27 of model parameters. A naive argument would scale layer size as a third of model size.

Batch size scaling

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.31 | 0.36 | 0.41 |

Doublings in batch size per doubling of model parameters. Erdil and Schneder-Joseph (forthcoming) conjecture that batchsize migth scale with the loss with respect to model size. We take estimates of the relation between model size and loss from the [Chinchilla scaling law](https://epoch.ai/blog/chinchilla-scaling-a-replication-attempt).

## What constraint is the most limiting? ^what-constraint-is-the

So far we have examined four main bottlenecks to AI scaling in isolation. When considered together, they imply that training runs of up to 2e29 FLOP would be feasible by the end of the decade. This would represent a roughly 10,000-fold scale-up relative to current models, and it would mean that the historical trend of scaling could continue uninterrupted until 2030 (see figure 7).[^note-102]

Figure 7: Conservative estimate of the largest possible training run allowed by each of the four constraints we consider. Also plotted: point estimate of the largest frontier run expected by 2030, assuming a 4x/year growth rate since GPT-4’s release.

Learn more about our assumptions.

Training run duration

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 5.18e6 | 1.56e7 | 2.33e7 |

Training run duration in seconds (1 million seconds = ~11.6 days). Informed by training times of recent record-setters in training compute that trained for 2-3 months, but allowing for up to 9 months in the future. Bottlenecks such as power capacity may drive longer training runs to eke out more compute. See [Sevilla et al (2022)](https://epoch.ai/blog/the-longest-training-run).

Fraction of resources for the largest training run

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 16% | 26% | 40% |

Percent of total AI resources that will be allocated to the single largest training run. This accounts for resources being divided between competitors, and between inference and training. This applies to the power and chip supplies. Based on a [model](https://www.squiggle-language.com/playground?v=0.9.5#code=eNrVVduO3DYM%2FRVin5JN5NvYk%2BwCfWiCom2AoEFuQIABDI1N28LakiLJMxgU%2FfdSsjFj724WeWzfbIo85Dkiqb%2Bvamz42Lu3qsar2yunx0Ohy6ZX2sIvkBc3mGY7Gcx4Nqc3r87m%2FGzNXhXB2qVJUjY63S79PQ7EkAHEMTS8csqAaui%2FoQ%2BrubHCnXaSh9g5bJPmUxrDhRSyLXnfq4o7oSSdJtHrndxJgnvDLdZAxoGICN0jWDWaCu1LwKiNoHNO29s4Ph6PkVOD7bipj9xgVKkhdlh1TMh6tM6cYnkQteCMC8ZlzTpdsVaPzPIeLTOolXFY9yfGtTaKVx2SD%2B8bxtkg%2Bp7qYqMUzhIe%2B75hruPyzjKn2ICOM2KNe6XudlKOQ%2BlVIhZFkuAGnIIMtzOdVbkdGmyFdWhCtVmS5XFSxFkat0q1PZZSHUvXCVP33LRoXSlkWXNHuSQFxQHxK5oTjLJC40hJ4Hs1OujUEQYuT%2F4akLjA5w9fDgW4k8YQ9EnBQE3RA9UAdhyAFJm%2BST%2BcSIS%2B8BeMW89hExWeRXCYznS4qNQfJtHNJSj3%2FULehT9Jp7Bzm4UGwu%2FkcslxDc9SYLCEfk7GVWOSdOvWmxH1DxBXdc5Y%2Bmms%2FBGofI7NnwxdBN6j%2BQLuVfkCVqm8Mj5XmI2BOp30LvDGT5PvHT9QBg8oR4RaUP%2BSx%2F4E2ogKL4FzvWcMP4ok%2Fcp2Ddk8gWuSIf4aFrP5CEXlW7VsV0RXWAGdpFCO9%2FcShFkIrBcaPACcxyMtkju6OqH1RPS3v76RENnm9r8351TtNqFqL1XmlypRtkIiGlpsUbNfTPcmTrPYjzCbZpgtPOP9KPqaPkIqy1qUxEHIxnDiNVZuNEgz7w8XGpNk05LZ%2Bm3zv9Txs6HFTryhMWqYVP31T6iofDutkNfvH5eZG3I6YCRsfPxYbd8FtN9HtNaJgTuklcbdtNecqu78NgzoHbfgaw1HGg29U7QtK%2FQOf%2Fh%2BpfeGH9DwFiMSXFRGWdW4J1WfV%2FbqGXvscbtejUIMq5lZJvsJpIeVPcTz3fIzUMuueoBy9c%2B%2FKFDRNQ%3D%3D) of the current share of total AI chip stock for Google, Microsoft, and Meta. Note that this is the 80% CI rather than 90%.

Peak GPU efficiency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e15 | 2.00e15 | 4.00e15 |

Theoretical peak FLOP/s per GPU used in the largest training run, before accounting for utilization. We assume FP8 FLOP through the model. FP8 FLOP/s for [NVIDIA H100,](https://www.nvidia.com/en-us/data-center/h100/) without sparsity. We allow for a x2 factor of uncertainty to acknowledge that a different number format might be preferred.

Training GPU utilization

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 20.00% | 37.50% | 60.00% |

GPU throughput actually achieved in the training run, as a percentage of the theoretical peak output of the GPU. Median: the median of known values in the notable models database. Low: utilization as low as 20% occurs in our database (e.g. GPT-3), and might result from a trade-off between optimizing efficiency and increasing cluster size. High: highest known value is 56.5% for LaMDA; we have seen approximately 60% in experiments on models with ~10B parameters, e.g. in [MosaicGPT Training Benchmarks](https://github.com/mosaicml/examples/tree/70f07314ca8f27f121d511af2d73bfbb0d019523/examples/llm/throughput).

GPU efficiency growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.31 | 1.44 | 1.59 |

Factor by which GPU performance in FLOP/s at a fixed precision improves each year. According to our [latest estimates](https://drive.google.com/file/d/1i9uGDEgHR01k7EQzvODlxTkM007emVjI/view?usp=sharing) of the trend in tensor FP16 performance for AI chips. We assume that the growth rate is similar in different number formats.

Stock of internet text data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.30e14 | 5.10e14 | 2.10e15 |

Number of text tokens available for training. Low:size of Common Crawl. Med: size of the indexed web. High: upper estimate on the size of the indexed web. Estimates taken from [(Villalobos et al, 2024)](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data).

Stock of internet image data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 5.00e12 | 1.00e13 | 2.00e13 |

Stock of internet video data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 4.31e12 | 8.63e12 | 1.73e13 |

Stock of internet audio data

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 4.00e11 | 8.00e11 | 1.60e12 |

Seconds of audio available for training. The lower estimate comes from the known quantity of ~150M podcast episodes at an average length of 40 minutes, plus tens of billions of seconds from music. Since this probably undercounts the total number of podcasts and songs and does not include other sources of audio, take 2x that as the central estimate

Growth of data stock

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.03 | 1.07 | 1.1 |

Factor by which the data stock grows per year. [Villalobos et al (2024)](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data) . “Given these considerations, we settle on a confidence interval between 0% and 10% a year. \[95% confidence\]”.

Data epochs

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 3 | 5.00 | 15 |

Multiplier of data stock to account for multiple epochs (multiple passes through training data). [Muennighoff et al. (2023)](https://arxiv.org/abs/2305.16264) find that up to ~4 epochs repeated data is about as valuable as “fresh” data. However, beyond that point there are steep diminishing returns to a marginal epoch, and by 40 epochs there is no marginal gain.

Data quality adjustment

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.1 | 0.2 | 0.4 |

Multiplier of data stock to account for much internet data being duplicated or too low-quality to be used for training. [Villalobos et al (2024)](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data) use a data quality factor between 30% and 50%.

Tokens per image or second of video

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 2 | 22 | 290 |

Tokens per image or second of video in an optimized multimodal model. The 10% percentile corresponds to the additional information contrained in images in sentence image pairs in [Henighan et al (2020)](https://arxiv.org/abs/2010.14701). The central guess corresponds to [Yu et al (2024)](https://arxiv.org/abs/2406.07550), which encodes 256x256 images using 32 tokens, adjusted for a smaller dictionary size than usual text tokenizer. The upper bound corresponds to [Yu et al (2023)](https://arxiv.org/abs/2310.05737), which encodes images as 256 tokens, adjusted for a larger dictionary. See also [[#^appendix-d-equivalence-between|Appendix D]].

Tokens per second of audio

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 2 | 23 | 280 |

Tokens per image or second of video in an optimized multimodal model. The 10% percentile corresponds tokenizing transcribed speech at ~120 words per minute, the central estimate is from SemantiCodec ([Liu et al., 2024](https://arxiv.org/html/2405.00233)) at 350 bps, assuming 15 bits per token. The upper estimate comes from entropy-coded Encodec ([Déffosez et al., 2022](https://arxiv.org/abs/2210.13438)) at 4.2kbps, which is competitive with standard MP3 encodings in terms of quality.

Current GPU stock

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.40e6 | 2.20e6 | 3.50e6 |

Number of H100-equivalent AI chips available at EOY 2023. This estimate takes into account reports of H100 shipments ([example](https://www.tomshardware.com/tech-industry/nvidia-ai-and-hpc-gpu-sales-reportedly-approached-half-a-million-units-in-q3-thanks-to-meta-facebook)), estimates of H100 and older GPU shipments based on annual [revenues](https://investor.nvidia.com/news/press-release-details/2024/NVIDIA-Announces-Financial-Results-for-Fourth-Quarter-and-Fiscal-2024/#:~:text=Full%2Dyear%20revenue%20rose%20217%25%20to%20a%20record%20%2447.5%20billion), and an analyst’s [estimate](https://www.theregister.com/2024/05/21/google_now_thirdlargest_in_datacenter/) of Google TPU production.

Current annualized GPU production

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e6 | 1.85e6 | 4.63e6 |

Annualized state-of-the-art GPU production (in number of H100-equivalents) at EOY 2023. [650k](https://www.tomshardware.com/tech-industry/nvidia-ai-and-hpc-gpu-sales-reportedly-approached-half-a-million-units-in-q3-thanks-to-meta-facebook) H100s shipped in 2023, [1.5M-2M](https://www.tomshardware.com/news/nvidia-to-reportedly-triple-output-of-compute-gpus-in-2024-up-to-2-million-h100s) expected in 2024. The start of 2024 would see (0.65\*1.75)^0.5 ~= 1.1M/yr production. We expect about 750k more from Google TPUs and A100s.

Growth of GPU production

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.3 | 1.7 | 2 |

Factor by which the total number of new GPU chips manufactured grows each year, measured in raw chip count rather than H100-equivalent units. This parameter ignores any year-over-year improvements in performance per die (i.e., it just scales the quantity of chips produced). The value of this parameter is informed by recent and planned growth in CoWoS and HBM capacity (30%, 45%, 100% annual growth), which reportedly is a current bottleneck to SotA GPU production.

Current monthly TSMC wafer production

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.00e5 | 1.80e5 | 3.33e5 |

Current TSMC production of 300mm-equivalent wafers per month for <7nm nodes. Point estimates put the combined monthly production of 5nm and 3nm wafers between 160,000 and 220,000 wpm at the start of 2024. The wider bounds are a guesstimate.

Growth of TSMC CapEx

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.16 | 1.23 | 1.33 |

Factor by which TSMC’s capital expenditures grow each year. Average capex growth in the last decade was [15%/yr](https://finbox.com/NYSE:TSM/explorer/capex/#:~:text=Looking%20back%20at%20the%20last,Similar%20Metrics). However, TSMC expects [50% CAGR](https://investor.tsmc.com/chinese/encrypt/files/encrypt_file/reports/2024-04/34ff75e23e53246302ce3a8d90d0423c57c6b120/TSMC%201Q24%20Transcript.pdf) in revenue from the AI server market over the next 5 years, which could drive up their capex. Overall estimate is a weighted geometric mean with 75% weight on the historical growth. Bounds: guesstimate.

TSMC volume-capex ratio

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.25 | 0.53 | 0.75 |

Ratio of TSMC wafer production output growth rate to capex input growth rate. Median: Average annual capex growth from 2014 to 2023 was about 15% (see other parameter). Based on [TSMC annual reports](https://www.tsmc.com/english/aboutTSMC/dc_annual_report), total wafer output grew from 8 million 12-inch equivalent wafers in 2014 to 15 million in 2022, suggesting an average annual growth rate of 8%. Bounds: guesstimate.

Dies per wafer

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 20 | 28 | 40 |

Number of good dies for a state-of-the-art GPU, per 300mm wafer. Using this [calculator](https://web.archive.org/web/20220327163600/https://caly-technologies.com/die-yield-calculator/). Wafer diameter of 300mm and H100-sized die of 814mm^2, assuming a square die. Defect density of 0.15, 0.1 and 0.05 for 10th, 50th, 90th percentiles, based on this [data](https://www.anandtech.com/show/16028/better-yield-on-5nm-than-7nm-tsmc-update-on-defect-rates-for-n5$.). Future GPUs like Blackwell may use multiple dies, but we account for that as a GPU efficiency improvement.

Installed power capacity per GPU

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1527.9 | 1704 | 1846 |

Installed power capacity per GPU in Watts, including all system components, such as CPU, memory, networking, etc. We also include power for power for cooling, to cover power distribution losses, lighting and other non-IT facility equipment, ie the data center power usage effectiveness (PUE). The average power consumption for a 1016 H100 DGX SuperPOD is 1.4MW, or 1389W per GPU. The peak consumption is 1420W per GPU (see [table 4 here](https://docs.nvidia.com/nvidia-dgx-superpod-data-center-design-dgx-h100.pdf)). We assume a PUE of 1.1 to 1.3 based on estimates from [Patterson et al (2021)](https://arxiv.org/abs/2104.10350) and [Semianalysis](https://www.semianalysis.com/p/ai-datacenter-energy-dilemma-race#:~:text=On%20top%20of,datacenter%20power%20consumption.).

GPU power efficiency growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.16 | 1.28 | 1.42 |

Factor by which power demand per FLOP/s declines per year due to improved efficiency. Estimated from a [regression](https://drive.google.com/file/d/1i9uGDEgHR01k7EQzvODlxTkM007emVjI/view?usp=sharing) that expands the [Hobbhahn et al (2023)](https://epoch.ai/blog/trends-in-machine-learning-hardware) dataset.

Localized data center power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 5.00e9 | 5.92e9 | 7.00e9 |

Total installed power capacity of data centers in Northern Virginia (Watts). The largest utility company in Northern Virginia (Dominion) has [5.8 GW of contracts](https://www.datacenterfrontier.com/energy/article/33013010/dominion-virginias-data-center-cluster-could-double-in-size) with data centers. Their main competitor Novec does not seem to supply as many data centers.

US AI data centers power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 3.04e9 |  |

Installed power capacity of US AI data centers, in Watts. Includes installed hardware and PUA. [Semianalysis](https://www.semianalysis.com/p/datacenter-model) reports 2537 MW of critical IT capacity for AI data centers in US and Canada bvy the end of 2023. We assume 1.2x PUE in line with Semianalysis.

US total data center power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 3.30e10 | 4.00e10 | 5.00e10 |

Installed power capacity of all US data centers, in Watts. Includes installed hardware and PUA. Average power consumption across US data centers is over 20 GW today. Dominion’s data centers [demand 60%](https://www.princewilliamtimes.com/news/region-s-sluggish-solar-can-t-match-surging-data-center-demand/article_be0be72f-922b-5b5e-94c0-0ac719be236c.html) of their capacity on average, and estimates from experts we spoke to suggest that data centers consume around 40-50% of their rated capacity, on average. This suggests overall capacity of 33 to 50 GW, or ~40 GW as a central estimate. [Semianalysis data](https://www.semianalysis.com/p/datacenter-model) is also consistent with ~40 GW.

Largest data center campus power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 9.60e8 | 2.50e9 | 5.00e9 |

US total power capacity

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 1.16e12 |  |

US data center power capacity growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.1 | 1.15 | 1.32 |

US non-AI data center power capacity growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.07 | 1.08 | 1.1 |

Expected growth of US non-AI data center power demand. Note that the non-AI data center demand growth will be capped by the overall growth rate. [Goldman Sachs](https://www.goldmansachs.com/insights/articles/AI-poised-to-drive-160-increase-in-power-demand) project 10% growth of non-AI data center demand through 2030. In 2022-2024, [Semianalysis](https://www.semianalysis.com/p/datacenter-model) forecasts 8% growth through 2022-2028. [EIA](https://iea.blob.core.windows.net/assets/6b2fd954-2017-408e-bf08-952fdd62118a/Electricity2024-Analysisandforecastto2026.pdf) forecasted a conservative 7% growth rate through 2026.

Data center network distance

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 350 | 2945.1 | 10618.45 |

Fiber optic speed

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 2.00e5 |  |

Achievable batch size

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.60e7 | 6.00e7 | 3.60e8 |

Maximum feasible number of tokens per batch in a distributed training run in 2024. The median corresponds to the supposed [max batch size of GPT-4](https://www.semianalysis.com/p/gpt-4-architecture-infrastructure?utm_source=post-email-title) during training. The lower bound corresponds to the largest batch size achieved by [Llama 3.1 405B](https://arxiv.org/abs/2407.21783).

Inter-data-center bandwidth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 4.10e14 | 8.19e14 | 1.64e15 |

Achievable inter data center connections bandwidth in bits per second (bps). Each node in [Google’s Stargate ethernet network](https://dl.acm.org/doi/10.1145/3230543.3230545) in 2014 featured 32 switches managing external traffic, which would correspond to 32/2 = 16 switches per data center pair on a ring all-reduce setup. The JPOP sites (ibidem) featured 16 outward switches. Using modern Teralynx 10 Ethernet Switch on each data center would result in 51.2 Tbps per link.

Inter-data-center bandwidth growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.4 | 1.5 | 1.6 |

Factor by which achievable bandwidth is expected to grow yearly. Corresponding to a [bootstrap](https://colab.research.google.com/drive/14ixx63lTw8sPfkWh_VXlqwhwq-LKkb78#scrollTo=BYeVEPOgVvcn) of the growth trend on a sample of ASIC Ethernet Switches sourced from [here](https://people.ucsc.edu/~warner/Bufs/buf-hist.html) and [here](https://www.wheelersnetwork.com/2023/03/marvell-teralynx-leapfrogs-to-512t.html).

GPU kernel latency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 4.50e-06 |  |

Minimum time to complete a single matrix multiplication in a modern GPU, in seconds, assuming no kernel fusion. We take this from Erdil and Schneder-Joseph (forthcoming).

Base communication latency

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 6.80e-06 |  |

Irreducible communication latency in seconds. We take the LL tree setting from the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc).

Variable intrapod latency (NVlink)

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 6.00e-07 |  |

Relationship between number of ranks and NVLINK communication latency in seconds. We take the LL tree setting from the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc).

Variable interpod latency (InfiniBand)

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 5.00e-06 |  |

Relationship between logarithm of the number of nodes and interpod InfiniBand communication latency in seconds. We take the LL tree setting from the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc).

Minimum TP mini-batch size

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 330 |  |

Minimum size of mini-batch size per GPU when doing 2D tensor parallelism while keeping utilization high. This corresponds to 2e15 FLOP/s x 1 byte/param / (2 FLOP/multadd x 3e12 byte/s), corresponding to the estimated values for the minimum mini-batch size that a single H100 can process efficiently in FP8 format while balancing computation time and memory accesses. See appendix E for more.

Layer scaling

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.21 | 0.27 | 0.33 |

Doublings in the number of layers per doubling of model parameters. Hoffman et al scale the number of layers as 0.27 of model parameters. A naive argument would scale layer size as a third of model size.

Batch size scaling

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 0.31 | 0.36 | 0.41 |

Doublings in batch size per doubling of model parameters. Erdil and Schneder-Joseph (forthcoming) conjecture that batchsize migth scale with the loss with respect to model size. We take estimates of the relation between model size and loss from the [Chinchilla scaling law](https://epoch.ai/blog/chinchilla-scaling-a-replication-attempt).

GPU memory bandwidth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
|  | 3.30e12 |  |

DRAM bandwidth in Byte/s. Memory bandwidth of the H100 SXM.

GPU memory bandwidth growth

| 10th percentile | Median | 90th percentile |
| --- | --- | --- |
| 1.15 | 1.17 | 1.23 |

The dark shaded box corresponds to an interquartile range and light shaded region to an 80% confidence interval.

The most binding constraints are **power and chip availability**—see figure 7. Of these two, power may be more malleable—the energy industry is less concentrated and there is precedent for 100 GW expansion of the power supply, which suppliers ought to be able to execute if planning three to five years in advance. Expanding chip manufacturing faces multiple challenges: key processes like advanced packaging are mostly allocated to data center GPUs already, and building new fabs requires large capital investments and highly specialized labor.

Data stands out as the most uncertain bottleneck, with its uncertainty range spanning four orders of magnitude. The utility of multimodal data for advancing reasoning capabilities may be limited, and our estimates of both the available stock of such data, its quality, and the efficiency of current tokenization methods are less certain than those for text-based data. Ultimately, synthetic data might enable scaling indefinitely, but at a large compute cost.

Lastly, while the latency wall is a distant constraint, it looms on the horizon as an obstacle to be navigated. It might be pushed back by adopting more complex network topologies, involving larger pods or more connections between pods.

## Will labs attempt to scale to these new heights? ^will-labs-attempt-to

We find that, based on extrapolating current trends around the key AI bottlenecks, training runs of up to 2e29 FLOP will be possible by the end of this decade. Achieving this scale would be on-trend: The largest training runs to date have been of the order of 5e25 FLOP, and six more years of the historical trend of 4x/year would result in models trained using roughly 2e29 FLOP. The price tag of the cluster needed for such a training run will be on the order of hundreds of billions of dollars.[^note-103] Will the AI industry actually seek to train models of this scale?

To date, increasing the scale of AI models has consistently led to improved capabilities. This has instilled a scaling-focused view of AI development that has resulted in the amount of spending on training runs growing [by around 2.5x/year](https://epoch.ai/blog/how-much-does-it-cost-to-train-frontier-ai-models). Early indications suggest that this is likely to continue. Notably, it [has been reported](https://www.theinformation.com/articles/microsoft-and-openai-plot-100-billion-stargate-ai-supercomputer) that Microsoft and OpenAI are working on plans for a data center project known as “Stargate” that could cost as much as $100 billion, set to launch in 2028. This suggests that major tech companies are indeed preparing to achieve the immense scales we’re considering.

Further evidence of AI systems’ potential for sufficiently large economic returns could emerge from scaling beyond GPT-4 to a GPT-6 equivalent model, coupled with [substantial algorithmic improvements](https://epoch.ai/blog/algorithmic-progress-in-language-models) and [post-training improvements](https://epoch.ai/blog/ai-capabilities-can-be-significantly-improved-without-expensive-retraining). This evidence might manifest as newer models like GPT-5 generating over $20 billion in revenue within their first year of release; significant advancements in AI functionality, allowing models to seamlessly integrate into existing workflows, manipulate browser windows or virtual machines, and operate independently in the background. We expect that such developments could convince AI labs and their backers of these systems’ immense potential value.

The potential payoff for AI that can automate a substantial portion of economic tasks is enormous. It’s plausible that an economy would invest trillions of dollars in building up its stock of compute-related capital, including data centers, semiconductor fabrication plants, and lithography machines. To understand the scale of this potential investment, consider that global labor compensation is approximately [$60T per year](https://www.adb.org/sites/default/files/publication/484346/adbi-wp920.pdf). Even without factoring in accelerated economic growth from AI automation, if it becomes feasible to develop AI capable of effectively substituting for human labor, investing trillions of dollars to capture even a fraction of this $60T flow would be economically justified.

Standard [economic models predict](https://epoch.ai/blog/explosive-growth-from-ai-a-review-of-the-arguments) that if AI automation reaches a point where it replaces most or all human labor, economic growth could accelerate [by tenfold or more](https://www.openphilanthropy.org/research/report-on-whether-ai-could-drive-explosive-economic-growth/). Over just a few decades, this accelerated growth could increase economic output by several orders of magnitude. Given this potential, achieving complete or near-complete automation earlier could be worth a substantial portion of global output. Recognizing this immense value, investors may redirect significant portions of their capital from traditional sectors into AI development and its essential infrastructure (energy production and distribution, semiconductor fabrication plants, data centers). This potential for unprecedented economic growth could drive trillions of dollars in investment in AI development.[^note-104]

Settling the question of whether companies or governments will be ready to invest upwards of tens of billions of dollars in large scale training runs is ultimately outside the scope of this article. But we think it is at least plausible, which is why we’ve undertaken this analysis.

## Conclusion ^conclusion

In this article, we estimated the maximum feasible scale of AI training runs by 2030 by analyzing the availability and potential constraints key factors required for scaling up training runs. We examined four categories of bottlenecks (power constraints, chip manufacturing capacity, data scarcity, and the latency wall) to determine at what point they might render larger training runs infeasible. Our main result: Based on current trends, training runs of up to 2e29 FLOP will be feasible by the end of this decade. In other words, **it is likely feasible, by the end of the decade, for an AI lab to train a model that would exceed GPT-4 in scale to the same degree that GPT-4 eclipses GPT-2 in training compute**.

One of the most likely reasons that training runs above these scales might be infeasible is the amount of power that can be supplied by the grid. Substantially expanding the data center power supply by 2030 may be challenging due to grid-level constraints, carbon commitments, and political factors. 

The second key constraint is the limited capacity to manufacture tens of millions of H100-equivalent chips per year. Capacity might be limited if capital expenditure is not substantially accelerated through the next decade, even if the relevant manufacturing capacity is mostly dedicated to producing GPUs or other AI accelerators. 

Overall, these constraints still permit AI labs to scale at 4x/year through this decade, but these present major challenges that will need to be addressed to continue progress.

If AI training runs of this scale actually occur, it would be of tremendous significance. AI might attract investment over hundreds of billions of dollars, becoming the largest technological project in the history of humankind. Sheer scale translates into more performance and generality, suggesting that we might see advances in AI by the end of the decade as major as what we have experienced since the beginning of the decade.

Finally, through our work we have grappled with the uncertainty we face in predicting the trajectory of AI technologies. Despite their importance, power restrictions and chip manufacturing stand out as uncertain. We will be investigating these in more depth in future work.

_We thank Anson Ho, David Owen, Konstantin Pilz, Benjamin Todd, Romeo Dean, Michael Dickens, Max Negele, David Schneider-Joseph, Andy Lubershane, Natalia Martemianova, Ying Yi, Luke Emberson, Peter Wildeford, Jean-Stanislas Denain, Trevor Gaunt, David Mathers, Dylan Patel, Carl Shulman, Ajeya Cotra, Alexander Erben, Ryan Greenblatt, Tim Fist._

## Appendices ^appendices

### Appendix A: Summary of the extrapolative model ^appendix-a-summary-of

Our simple extrapolative model of bottlenecks has four components, modeling each of the main bottlenecks we discuss in the article. The code for the model can be found [here](https://epoch.ai/code/can-ai-scaling-continue-through-2030), and the default model parameters with sources can be found in the parameter tables throughout this article.

First, for modeling power restrictions we consider the installed power capacity of data centers across the US. This is scaled according to projections of data center demand by local utility providers, and restricted by projections of growth of total US power capacity growth. We also separately model the trend of growth of non-AI data centers, which we constrain to grow only at most as fast as the overall data center capacity growth. The projected capacity for AI data centers is modeled as the difference between the projected total data center capacity and the projected non-AI data center capacity. A fraction of this (modeled following [[#^appendix-b-fraction-of|Appendix B]]) is our final estimate of the available capacity for a single training run. We combine this estimate with an exponentially improving trend of energy efficiency (in FLOP/s/W) and estimates of training run length to compute a largest possible training run. We take the minimum between this and the distribution of training runs sizes allowed by plausible achievable bandwidths, as described in the [[#^feasibility-of-geographically-distribute|feasibility of distributed training runs section]]. We also take the maximum between this result and the largest local training run defined by a distribution over plausible local power supplies by 2030.

Second, for modeling limited chip manufacturing capacity, we consider the current bottlenecks of CoWoS packaging and high-bandwidth memory (HBM) production. We project GPU production to grow between 30% and 100% per year, which aligns with recent scale-ups and expected growth in CoWoS and HBM. The model limits this GPU production trend by a projection of TSMC’s total wafer production for <7nm nodes. However, this limit does not have a significant effect by 2030, based on our chosen parameters. We assume that the compute stock accumulates over time, with new chips improving in FLOP/s by 44% per year. As with the power model, this is combined with estimates of the fraction of the stock available, the training run length, and utilization to estimate a largest possible training run.

Third, the model based on data considers the existing stocks of text, video and image. They are combined according to some estimates of transfer efficiency. Finally, we model them as growing exponentially at a rate congruent to the historical rate of growth of internet content. To convert the effective data stock into a maximum training run size we use Chinchilla scaling of 20 tokens per parameter, and total training compute equal to six times the parameter count times the training dataset size.

Fourth and last, to compute the latency wall limit we solve a system of equations as detailed in [[#^appendix-e-computing-the|Appendix E]]. This considers how the communication latency scales with the number of GPUs that need to synchronize to perform tensor parallelism, while accounting for batch size scaling, layer depth scaling and improvements in hardware performance.

All model parameter choices are informed by evidence we could find and our own guesses and intuitions. Model inputs are assumed to follow a [metalog distribution](https://pubsonline.informs.org/doi/abs/10.1287/deca.2016.0338) that fits our guesses of the 10%, 50% and 90% distribution percentiles. We further constrain percentage parameters to be within 0% and 100%, and growth rates to be above 1. We also induce a correlation between the parameter via a Gaussian copula. The correlations induced are explained in table 1 below.

Table 1: Induced correlations between model parameters.

| Parameter | Parameter | Spearman’s rho | Reasoning |
| --- | --- | --- | --- |
| US data center power capacity growth | Growth of GPU production | 0.5 | If large investments are made in GPUs, also will be made in power supply. |
| US data center power capacity growth | Largest data center campus power capacity | 0.5 | If large data centers are being opened, probably the total power demand is growing faster. |
| Inter-data-center bandwidth | US data center power capacity growth | 0.3 | If large efforts are being made to scale power, likely also for bandwidth. |
| Training run duration | US data center power capacity growth | 0.5 | If power is a large constraint, people will want to train for longer to circumvent it. |
| Training run duration | Growth of GPU production | 0.5 | If GPU manufacturing is a large constraint, people will want to train for longer to circumvent it. |
| Training run duration | GPU efficiency growth | -0.7 | If GPU performance improvements are slow, training run lengths could increase (See [The Longest Training Run](https://epoch.ai/blog/the-longest-training-run)) |
| Stock of internet text data | Stock of internet image data | 0.7 | If a large stock of data exists in a modality, it also likely is available in other modalities. |
| Stock of internet image data | Stock of internet video data | 0.7 | See above. |
| Stock of internet video data | Stock of internet text data | 0.7 | See above. |

### Appendix B: Fraction of total resources allocated to the largest training run ^appendix-b-fraction-of

When modeling electrical power and chip manufacturing capacity, we must consider how competition between AI labs affects the fraction of these resources that a lab can secure to perform the largest training run. To estimate this fraction, we consider the stock of AI chips available to each of the most well-resourced firms at the beginning of 2024. We then divide each firm's stock by the total stock of AI chips available. Finally, we adjust this fraction down to account for some chips being allocated to inference. For convenience, we measure the stock of AI chips in terms of H100-equivalents: the number of Nvidia H100 GPUs that would match the total FLOP/s of the stock, at 16-bit precision. Full calculations are available [here](https://www.squiggle-language.com/playground?v=0.9.5).

**Meta:** According to analyst firm Omdia, Meta acquired [150,000](https://www.tomshardware.com/tech-industry/nvidia-ai-and-hpc-gpu-sales-reportedly-approached-half-a-million-units-in-q3-thanks-to-meta-facebook) H100 GPUs by the end of 2023. Meta [plans](https://engineering.fb.com/2024/03/12/data-center-engineering/building-metas-genai-infrastructure/) to have a total of 600,000 H100-equivalent GPUs by the end of 2024. So it is likely that Meta's stock of H100-equivalents at the beginning of 2024 was between 150,000 and 600,000.

**Microsoft:** Omdia estimates that Microsoft also acquired 150,000 H100 GPUs by the end of 2023. Microsoft reportedly [plans](https://www.businessinsider.com/microsoft-gpu-targets-1-8-million-ai-chips-this-year-2024-4) to triple their stock of AI chips to 1.8 million by December. It is unclear what kind of chips these will be, but the plan implies that the initial stock was 600,000 chips, and the timing suggests that many of the new chips will be H100s. Based on the rate of hardware efficiency improvements, the initial stock of 600,000 chips would equate to around 300,000 H100 equivalents.[^note-105] However, it is unclear exactly when Microsoft's expansion plans started. Microsoft may have already acquired more H100 GPUs by the start of 2024; we estimate up to 140,000.[^note-106] Accounting for all of this, we believe that Microsoft's stock of H100-equivalents at the beginning of 2024 was likely between 150,000 and 600,000.

**Google:** Little is known publicly about the production of Google's custom AI chips, known as TPUs. However, one [report](https://www.theregister.com/2024/05/21/google_now_thirdlargest_in_datacenter/) by analyst firm TechInsights estimates the total number of TPU shipments each year.[^note-107] Based on the release dates of each generation of TPU, it is likely that most of the estimated 2 million units in 2023 and 1.5 million units in 2022 were TPUv5. However, there are two versions of TPUv5: the more efficient TPUv5e, and the higher-performance TPUv5p. The share of each TPU type is unclear, so we estimate the total number of TPUv5 units shipped to be between 1 and 3.5 million, and the share of that total made up by TPUv5p to be between 10% and 90%.

As for TPUv4, which was released in 2021, we believe that peak production likely occurred between 2020 and 2022, and estimate that a total of 250,000 to 1.5 million units were produced based on the yearly production reported by TechInsights. We neglect older generations of TPU, given the much lower estimates of production prior to 2021 and the lower performance of those older generations. Google also owns Nvidia GPUs, but given the track record of Google labs exclusively using TPUs to train their flagship models, we think it is unlikely they will allocate these GPUs to their largest training run. So putting the TPUv4 and TPUv5 numbers together, we estimate that the total number of H100-equivalents available to Google is between 400,000 and 1.4 million.

**Amazon:** According to the Omdia report, Amazon acquired 50,000 H100 GPUs by the end of 2023, which is three times less than Microsoft and Meta. Amazon also has custom Trainium chips, with one report that Amazon Web Services (AWS) will soon offer clusters of up to [100,000 Trainium2 chips](https://techcrunch.com/2023/11/28/amazon-unveils-new-chips-for-training-and-running-ai-models/) with a peak of 65e18 FLOP/s of compute. This corresponds to about 66,000 H100-equivalents assuming FP16 precision, or 33,000 assuming FP8 precision. If Amazon already has several of these clusters, they may have hundreds of thousands of H100-equivalents in total. Given that these clusters are only just coming online, however, it seems unlikely that Amazon's stock of AI chips would exceed Google's estimated stock of 400,000 to 1.4 million H100-equivalents.

**Total stock:** To estimate the total stock of AI chips available for training by the beginning of 2024, we add up actual H100s shipped, other GPUs, and Google TPUs. The actual H100s shipped was likely between 500,000 and 1.6 million. Omdia estimated a total of 650,000 shipped to major companies. Given Nvidia's annualized data center revenue of [$47.5 billion](https://investor.nvidia.com/news/press-release-details/2024/NVIDIA-Announces-Financial-Results-for-Fourth-Quarter-and-Fiscal-2024/), and a price of [$30,000](https://www.hpcwire.com/2023/08/17/nvidia-h100-are-550000-gpus-enough-for-this-year/), they could only have sold about 1.6 million H100s at most.

Other GPUs likely make up between 200,000 and 1 million H100 equivalents. The peak years for the previous generation A100 were 2021 and 2022, in which Nvidia earned a combined [$25 billion](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-fourth-quarter-and-fiscal-2022) in data center revenue. At $15,000 per unit, this implies at most 1.7 million units sold, corresponding to about 500,000 H100 equivalents. A more conservative estimate would be $15B / $20,000 ~= 750,000 A100s—roughly 250,000 H100 equivalents. Besides the A100, other GPUs would have a smaller contribution, as they either have lower performance or a much smaller share of the market. Above, we estimated that Microsoft's 150,000 H100 GPUs imply roughly double that number in total H100 equivalents; a similar argument here implies at most 500,000 * 2 = 1 million H100 equivalents from non-H100 GPUs.

**Training allocation:** Available computing resources are split between training new models and running inference on existing ones. [A simple analysis](https://epoch.ai/blog/optimally-allocating-compute-between-inference-and-training) suggests AI labs should allocate comparable resources to both tasks. Assuming this balance, we can estimate future resource allocation. If in 2029 training and inference compute are equal, and training compute continues to grow [at 4x per year](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year), one-quarter of total compute (equal to 2029's training) will run inference on 2029 models, while three-quarters will train 2030 models. This suggests that 80% of 2030's compute would be used for training new models, while 20% would be used for inference on previous models.

**Result:** Adding the stock of actual H100s, other GPUs, and TPUs together results in an estimate of 1.5 to 3.5 million H100-equivalents in total by the beginning of 2024. Since Google has the highest stock estimate of 400,000 to 1.4 million H100-equivalents, we use this stock to estimate the allocation of total resources. After adjusting for 80% of a company's compute being spent on training, our final result is that the largest training run can be allocated 26% (somewhere between 16% to 40%) of the total available chip stock.

### Appendix C: Bandwidth constraints ^appendix-c-bandwidth-constraints

Suppose we have a ring all-reduce setup involving $M$ data centers, with fiber optic bandwidth $F$ bps between every data pair and $t_L$ seconds of latency for a round trip across the network.

The standard all-ring reduce includes $M-1$ stages of parallel reduce followed by $M-1$ stages of broadcast. In each stage, peers communicate to their next neighbor a tensor of size $N/M$, where $N$ is the size of the model, which can be communicated in $N/M \times 8 / F$ seconds, assuming 8 bits per parameter. In total, this takes $2(M-1) \times N/M \times 8 / F \approx 2 \times N \times 8 / F$ seconds.

To this we need to add the latency, corresponding to two round trips down the network, for a total time per all reduce of:

$$
t_{\text{AR}} = \frac{2 \times N \times 8}{F} + 2 \times t_L
$$

Following a logic similar to what is explained in the section [[#^feasibility-of-geographically-distribute|Feasibility of distributed training runs]] when talking about latencies, this would lead to a maximum of $U = \frac{T}{t_{\text{AR}}}$ gradient updates, allowing for a dataset size of $D = U \times B$, where $B$ is the maximum achievable batch size.

We assume the usual Chinchilla relation between model size and number of parameters ($D = 20 \times N$), and numerically solve for the largest model that can be trained using the [fsolve](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.fsolve.html) facility in scipy.

### Appendix D: Equivalence between multimodal and text data ^appendix-d-equivalence-between

Here we set out to estimate how many tokens an image or second of video would be encoded as, in relation to one token of text.

Establishing an equivalence rate between data of different modalities is complex. In the limit, we expect multimodal tokenizers to encode media with an amount of tokens roughly proportional to the amount of information therein contained. So we try to estimate how much information image and video data have in relation to text.

[Henighan et al (2020)](https://arxiv.org/abs/2010.14701) estimate that one 32x32 image provides an information gain over a description as the equivalent of 2-3 words (eg 2-4 tokens of text), which we take as a lower bound on the information content of an image. [Chameleon-34B](https://arxiv.org/abs/2405.09818) encode 512x512 images using 1024 text-equivalent tokens, i.e. 770 words. As of June 2024, OpenAI [charges](https://openai.com/api/pricing/) 255 text tokens to process 512x512 images with GPT-4o. [Yu et al (2023)](https://arxiv.org/abs/2310.05737) encode images with good performance using 256 tokens with a dictionary of 2^18 tokens, four times bigger than typical text tokenizers; we take that as equivalent to $256 \times 18/16 \approx 290$ text tokens (typical text tokenizers use a codebook with 2^16 entries, hence the adjustment). [Yu et al (2024)](https://arxiv.org/abs/2406.07550) encodes 256x256 images using 32 tokens from a codebook with 2^11 entries, equivalent to $32 \times \frac{11}{16} = 22$ text tokens. While the Chameleon paper is the most straightforward application, given the rest of the evidence pointing towards lower dimensions we consider a range of 2 to 290 tokens per image.

For video, we speculate that one second of video content would be the equivalent of 2-10 words of content based on typical speech speeds, i.e. 2-13 text tokens. The information in a video is highly redundant compared to images—for instance, typical high res images take up 2MB of space, while 720p/1080p videos take up [1GB of space per hour of video](https://www.goanywhere.com/blog/how-big-are-movie-files), ie 0.2MB per second of video, which would suggest there is less information per second of video than in ten images. So we take as lower bound the 2 tokens per second of speech and as an upper bound the same 290 tokens per second that we assigned to an image, as a generous upper bound of the image content in the video.

Thus we arrive at a rate of 2 to 290 tokens per image or second of video. We consider this an extremely rough guess, and acknowledge there is significant room for disagreement.

### Appendix E: Computing the largest possible training run given variable communication latency restrictions ^appendix-e-computing-the

In this appendix we explain how we estimate the largest model that can be trained using a tree topology setup without running into latency constraints.

The latency per layer and batch $t_L$ corresponds to combining the base comms latency $t_{\text{base}}$ and the variable comms latencies within a node $t_{\text{INTRA}}$ and across nodes $t_{\text{INTER}}$. Here we are assuming 8-GPU NVLINK nodes (of which at most $\lceil \sqrt 8 \rceil = 3$ coordinate after each layer), and a tree structure, using the formula for an all-reduce latency found in the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc). We multiply this by 4 since each layer has an attention and MLP block, which need to be traversed forward and backward for each batch during training.

$$
t_L = 4 \times \left[t_{\text{base}} + 2 \times \left(t_{\text{INTRA}} \times 3 + t_{\text{INTER}} \times \max\left(0, \log_2\left(\frac{\text{TP}_\text{RANK-2D}}{8}\right)\right)\right)\right]
$$

The number of ranks involved in 2D tensor parallelism synchronization after each layer ($\text{TP}_\text{RANK-2D}$) is the square root of the number of ranks involved in tensor parallelism overall. We bound this as inversely proportional to the maximum slicing across GPUs that can be achieved with data and pipeline parallelism, considering the minimum number of samples in a batch $B_{\text{MIN}}$ that can be processed with TP efficiently ($DP_\text{RANK} \times PP_\text{RANK} = \frac{B}{B_{\text{MIN}}}$).

$$
\text{TP}_\text{RANK-2D} = \max\left(1, \sqrt{\frac{n_{\text{gpu}} \cdot B_{\text{MIN}}}{B}}\right)
$$

To estimate $B_{\text{MIN}}$ we look into the utilization that GPUs can achieve given their bandwidth. This utilization is optimized when the amount of time spent on memory accesses is roughly equal to the time spent on computation. Assuming a peak hardware performance of H FLOP/s, a bandwidth of W bytes/s and a parameter precision of p bytes, the equilibrium between memory access and computation gives:

$$
B_{\text{MIN}} = \frac{H \times p}{2 \times W}
$$

For the H100 at FP8 precision, the minimum batch size per GPU would then correspond to $B_{\text{MIN}} = \frac{2e15 \text{ FLOP/s} \times 1 \text{ byte/param}}{2 \text{ FLOP/multiply-add} \times 3e12 \text{ bytes/s}} \approx 330$. Theoretically, this minimum batch size would increase over time, as the bandwidth and hardware performance improve unequally fast. For simplicity of the analysis, we assume that it will stay roughly fixed.

The number of GPUs is approximated by the model compute $C$ divided by the training duration $T$ and the utilization-adjusted hardware performance $H$ (this is an underestimate, as utilization worsens with scale): $N_{\text{GPU}} = C(T \times H)$. The model compute $C$, dataset size $D$ and model size $N$ obey [the usual relation](https://epoch.ai/blog/estimating-training-compute), $C = 6DN$. Dataset size $D$ is assumed to scale in relation to model size $N$ following the [Chinchilla rule](https://epoch.ai/blog/chinchilla-scaling-a-replication-attempt), $D = 20 \times N$. The batch size $B$ and the layer depth $L$ are assumed to grow exponentially with respect to model size: $B = B_0 \times N^{\alpha_B}$, $L = L_0 \times N^{\alpha_L}$.

The minimum training time $T$ is then bounded by time per layer and batch size $t_L$ times the number of layers $L$ times the number of gradient updates ($U = D/B$): $T = t_L \times L \times D/B$. In the point where scale is maximized, this limit will be taut. We solve this system of equations numerically using the [fsolve](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.fsolve.html) facility in scipy.

### Appendix F: Unprecedented economic growth could drive massive AI investment ^appendix-f-unprecedented-economic

In the section “[[#^will-labs-attempt-to|Will labs attempt to scale to these new heights?]]”, we argued that the unprecedented economic growth from AI automation could drive massive AI investments. While this is far from guaranteed, in this appendix we outline a rough calculation to illustrate this dynamic.

The starting point is to consider a lifetime value function $V$, with isoelastic flow utility over consumption $c$. To capture the economic impact of massive AI automation, we assume that consumption is constant at $\bar{c}$ until some year $T$, after which consumption goes to infinity. We then have $V(c,T) = -\sum_{t=0}^T \beta^t \bar{c}^{-\gamma} = -\bar{c}^{-\gamma} \frac{1-\beta^{T+1}}{1-\beta}$, where we sum over years $t$ with discount $\beta$ and elasticity of intertemporal substitution $\gamma$.

The next step is to relate this to AI investment: we consider how much flow consumption a representative agent would be willing to bring forward the arrival date of these economic impacts. Suppose the representative agent is indifferent between a consumption of $c_1$ in year $T_1$ and a consumption of $c_2$ in year $T_2$, i.e. $V(c_1, T_1) = V(c_2, T_2)$. Then it follows that $\frac{c_1}{c_2} = \left(\frac{1-\beta^{T_1+1}}{1-\beta^{T_2+1}}\right)^{\frac{1}{\gamma}}$.

With this expression, we can plug in some plausible numbers for illustration. Suppose we want to move the point of massive automation from $T_2 = 30$ years to $T_1 = 20$ years, with a discount rate of 2% (i.e. $\beta = 0.98$) and $\gamma = 1$ ([Havránek et al. 2015](https://www.sciencedirect.com/science/article/abs/pii/S002219961500032X)). Then we have $\frac{c_1}{c_2} \approx 0.74$, implying that it is worth giving up 26% of flow consumption each year!

In the US, around 70-80% of GDP is dedicated to consumption ([World Bank, 2022](https://data.worldbank.org/indicator/NY.GDS.TOTL.ZS?locations=US)), amounting to around $18.75T each year. If we believe the above calculation, this suggests forfeiting around $4.7T worth of consumption annually to hasten the arrival of massive automation. Of course, this calculation is based on aggressive assumptions, but at the very least it illustrates why massive upfront investments in AI infrastructure might make sense.

Notes

[^note-1]: For LLMs, compute scaling likely accounts for [the majority of pre-training performance gains](https://epoch.ai/blog/algorithmic-progress-in-language-models). Post-training techniques can add [substantial but highly variable improvements](https://epoch.ai/blog/ai-capabilities-can-be-significantly-improved-without-expensive-retraining), depending on the specific method and domain. When considering both, the relative importance of compute scaling becomes less clear.
[^note-2]: GPT-2 was trained on around 2e21 FLOP, and GPT-4 was trained on around 2e25 FLOP, a 10,000x increase.
[^note-3]: Note that the estimate for the largest training run given latency constraints might be _too optimistic_, since we suspect the communication latencies for the multiplication of intermediate size matrices might be less efficient than we estimate.
[^note-4]: In this summary and throughout this article, whenever a range is given it is to be understood as an 80% CI.
[^note-5]: However, note that other countries might end up being preferred by developers. For example, Chinese providers installed [over a terawatt of power](https://www.statista.com/statistics/302269/china-installed-power-generation-capacity/) in the last decade, and the UAE has a [friendly regulatory process for securing power](https://archive.doingbusiness.org/en/rankings).
[^note-6]: We are assuming training runs between 2 and 9 months of duration, and that for distributed training a single company will only be able to leverage between 16% and 40% of the available supply of power for AI data centers.
[^note-7]: That is, the state-of-the-art among GPUs that are currently widely used. Nvidia has already announced its next generation of [Blackwell](https://www.semianalysis.com/p/nvidia-blackwell-perf-tco-analysis) chips. We account for future GPU generations by projecting efficiency improvements through 2030. Note that Google DeepMind mostly uses [Google TPUs](https://cloud.google.com/tpu?hl=en) for training, but we use Nvidia as our baseline because there is more available information on NVIDIA products than TPUs, and because they are [overwhelmingly](https://www.cnbc.com/2024/06/02/nvidia-dominates-the-ai-chip-market-but-theres-rising-competition-.html) popular among the AI industry overall.
[^cite-8]: Based on the average ratio between the H100 DGX SuperPOD server expected average power (EAP) to the TDP of individual GPUs, we find an overhead factor of 1.4MW / 1016 GPUs / 700W per GPU =  1.96x (see [Table 4 here](https://docs.nvidia.com/nvidia-dgx-superpod-data-center-design-dgx-h100.pdf)). Additionally, the power usage effectiveness (PUE), which accounts for data center-level overhead like cooling and power distribution, in e.g. [Patterson et al (2021)](https://arxiv.org/abs/2104.10350) is reported as a 1.2x additional factor. This results in 700 \* 1.96 \* 1.2 = ~1700W per GPU. Here we follow [our previous work](https://epoch.ai/blog/how-much-does-it-cost-to-train-frontier-ai-models) (see Appendix A.4 from the paper).
[^note-9]: The average [US household](https://www.eia.gov/energyexplained/use-of-energy/electricity-use-in-homes.php) consumes 10,000 kWh of electricity a year, for an average rate of ~1,200 W after dividing by 8,760 hours in a year.
[^note-10]: Training compute for frontier models is growing as [4.1x/year](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year), which would result in training runs of $3.8e25 \text{ FLOP} \times 4.1\text{ x/year}^{6\text{ years}} = 2e29\text{ FLOP}$ by end of the decade.
[^note-11]: We derive this from [an expansion](https://colab.research.google.com/drive/1i9uGDEgHR01k7EQzvODlxTkM007emVjI) of our previous research on the [ML hardware power-efficiency trend](https://epoch.ai/blog/trends-in-machine-learning-hardware).
[^note-12]: 4-bit training has been discussed and demonstrated in [particular research contexts](https://papers.nips.cc/paper/2020/file/13b919438259814cd5be8cb45877d577-Paper.pdf), but it isn’t clear whether it will be useful in practice. We conservatively assume it won’t be.
[^note-13]: It’s not possible to use the full capacity of 1200 GW capacity in practice, because sources like solar, wind, and hydroelectricity generate power intermittently. In addition, power demand naturally fluctuates over time. The US generated over [4,178 terawatt-hours](https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_1_1) in 2023; 4178 TWh / 8760 hours in a year = 477 GW of power generation on average.
[^note-14]: See the section “Power constraints for geographically distributed training” for more discussion on this figure.
[^note-15]: One large smelter in Australia consumes [850 MW](https://www.aemc.gov.au/sites/default/files/content/64a4b588-7e7c-4fa5-b99d-25baa0664618/Tomago-Aluminium-Company.pdf).
[^note-16]: One interesting case study is pump storage facilities. Bath County in Virginia houses the [largest pumped storage station in the US](https://en.wikipedia.org/wiki/Bath_County_Pumped_Storage_Station), with an potential output capacity of 3GW. The input capacity is likely similar—“When generating power, the water flow can be as much as 13.5 million US gallons (51,000 m³) per minute (850 m³/s). When storing power, the flow can be as much as 12.7 million US gallons (48,000 m³) per minute (800 m³/s).” Another point of comparison is CERN’s Large Hadron Collider, which peaks at [200 MW consumption](https://www.lhc-closer.es/taking_a_closer_look_at_lhc/0.energy_consumption#:~:text=the%20whole%20CERN%20site%20will%20peak%20at%20about%20200%20MW).
[^note-17]: Note that since solar farms output varies with the time of the day, the average capacity is roughly 4x less than nominal capacity.
[^note-18]: Notably, all of them are either hydroelectric, nuclear or based on fossil fuels.
[^note-19]: Major electricity consumers secure power through long-term contracts, so power from large plants will be at least partly locked by contracts. In addition, one expert we consulted stated that the US has little spare power capacity given existing supply, since many parts of the US are at “elevated risk” of power shortfalls.
[^note-20]: We could find just two US plants with capacity over 3GW constructed after the year 2000: the [Manatee oil plant](https://floridadep.gov/water/siting-coordination-office/content/manatee-power-plant) and the [West County Energy Center](https://en.wikipedia.org/wiki/West_County_Energy_Center) in Florida. Most other power plants over 3GW were constructed in the 1970s. The [West County Energy Center](https://www.power-technology.com/projects/west-county-energy/#:~:text=Plant%20Owner%20/%20Operator,to%2050%20full%2Dtime%20jobs) construction permit was conceded in March 2006 and finished construction of its third reactor by July 2011, suggesting that it is feasible to build >3GW power plants in five years.
[^note-21]: We emphasize that this applies to power stations already existing or planned. A determined actor might be able to build their own large scale power stations over 3 GW.
[^note-22]: The largest utility company in Northern Virginia (Dominion) has [connected over 4 GW](https://www.datacenterdynamics.com/en/news/dominion-connected-15-data-centers-totaling-933mw-in-virginia-in-2023-15-more-expected-in-2024/) of data centers since 2019, and has 5.8 GW of [contracts](https://www.datacenterfrontier.com/energy/article/33013010/dominion-virginias-data-center-cluster-could-double-in-size) with data centers. NOVEC, another Northern Virginia utility, [also serves many data centers](https://virginiamercury.com/2023/11/21/a-5-point-plan-for-data-centers/), but is a much smaller utility overall at [175k](https://www.novec.com/About_NOVEC/) customers versus Dominion’s [2.7 million](https://www.dominionenergy.com/economic-development/virginia#:~:text=We%20provide%20more%20than%202.7,on%20safety%20and%20the%20environment.).
[^note-23]: Dominion projects an annual growth rate of 10%, which would be an ~1.8x increase over six years. See the next section for more details on growth projections. Note that providers are likely to update their plans for expansion as the demand for such large data centers becomes clearer—and there is precedent for aggressive expansion when facing unexpected demand. For instance, in 2022 Georgia Power [said](https://www.canarymedia.com/articles/electrification/data-centers-bitcoin-and-evs-send-utilities-scrambling-for-more-power) “it will need 17 times more electricity—the equivalent of four new nuclear units—than it had forecast just 18 months earlier because of new data centers and manufacturing in the state.”
[^cite-24]: “The executives \[at Microsoft and OpenAI\] have discussed launching Stargate as soon as 2028 and expanding it through 2030, possibly needing as much as 5 gigawatts of power by the end”, Stargate being the codename for the proposed project.
[^note-25]: We assume a 4x increase in FLOP/s per W over the H100s, and FP8 performance. 100 days, which is similar to today’s training runs, would result in ~7e28 FLOP.
[^cite-26]: [Gemini technical report](https://arxiv.org/abs/2312.11805): “Training Gemini Ultra used a large fleet of TPUv4 accelerators owned by Google across multiple data centers”. It is not clear how many data centers were split across, or if they were close by.
[^note-27]: See their [ISO 27001 compliance report](https://cloud.google.com/security/compliance/compliance-reports-manager#/ReportType=Certificate&ProductArea=Google_Cloud) for the locations.
[^note-28]: Currently, data centers in the US likely consume over 20 GW of power, on average: The [IEA](https://iea.blob.core.windows.net/assets/6b2fd954-2017-408e-bf08-952fdd62118a/Electricity2024-Analysisandforecastto2026.pdf) estimates that US data centers consumed “around 200 TWh in 2022 (~4% of US electricity demand)”, which would be an average rate of [~23 GW](https://www.wolframalpha.com/input?i=200+TWh+divided+by+one+year) over the year. Meanwhile, [McKinsey](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/investing-in-the-rising-data-center-economy) estimates US data centers consumed 17 GW on average in 2022, and [Goldman Sachs](https://www.goldmansachs.com/insights/articles/gs-research/generational-growth-ai-data-centers-and-the-coming-us-power-surge/report.pdf) estimates 146 TWh in 2023, or ~17 GW on average. Given this range of estimates, and rapid growth in recent years, the current rate is likely above 20 GW.
[^note-29]: 20 / 0.6 = 33.3, and 20 / 0.4 = 50.
[^note-30]: SemiAnalyis reports the critical IT capacity (see Figure 2) without accounting for power usage effectiveness (PUE), which is total data center power divided by power used directly for compute rather than overhead functions such as cooling. Our estimate of power consumption per GPU also includes this overhead, so we need to use the total capacity, not the IT capacity. We arrive at our estimates of 36 GW and 48 GW by assuming a PUE of 1.5x for non-AI data centers, and a PUE of 1.2x for AI data centers, based on [SemiAnalysis](https://www.semianalysis.com/p/ai-datacenter-energy-dilemma-race) estimates.
[^note-31]: This is based on backing out growth rates from two different projections. First, Dominion [projects](https://www.datacenterfrontier.com/energy/article/33013010/dominion-virginias-data-center-cluster-could-double-in-size) that data center capacity will double from 2023 to 2028. 2x growth over 5 years is ~15% annual growth. Another [projection](https://virginiamercury.com/2023/11/21/a-5-point-plan-for-data-centers/#:~:text=Grid%20operator%20PJM%E2%80%99s%20grid%20forecast%20projects%20Dominion%E2%80%99s%20data%20center%20load%20will%20quadruple%20over%20the%20next%2015%20years%2C%20while%20NOVEC%E2%80%99s%20will%20rise%20to%20ten%20times%20what%20it%20is%20today.) from a grid operator is that Dominion’s data center load will grow by 4x over 15 years, and 4^(1/15) = ~1.1, or 10% growth. The shorter-term projection is likely more relevant since we are discussing growth until 2030.
[^note-32]: From the figure above we can read 22,109 MW and 2,537 MW of installed IT capacity for non-AI and AI data centers, respectively. Assuming a PUE of 1.5x for the former and 1.2x for the latter, AI data centers correspond to $2{,}537\,\text{MW} \times 1.2\,\text{PUE} \approx 3\,\text{GW}$ installed capacity, which is equal to $\frac{3\,\text{GW}}{22{,}109\,\text{MW} \times 1.5\,\text{PUE} + 3\,\text{GW}} \approx 8\%$ of total installed capacity.
[^note-33]: Goldman Sachs [projects](https://www.goldmansachs.com/insights/articles/AI-poised-to-drive-160-increase-in-power-demand) an increase in non-AI data center energy use from 165 TWh in 2024 to 304 TWh in 2030, which would be a 10.7% growth rate. [SemiAnalysis](https://www.semianalysis.com/p/ai-datacenter-energy-dilemma-race) estimates a 8% growth rate in non-AI critical IT capacity between end of 2023 and end of 2028. Recent annual growth in non-AI IT capacity in North America according to SemiAnalysis data was between 11% to 13%.
[^note-34]: For comparison, both [Goldman Sachs](https://www.goldmansachs.com/insights/articles/AI-poised-to-drive-160-increase-in-power-demand) and [SemiAnalysis](https://www.semianalysis.com/p/datacenter-model) expect a planned expansion of AI power demand of more than 2x throughout 2024. This is from a small base, so it’s unclear how long it can be kept up.
[^note-35]: This is based on each company’s current share of the total stock of AI chips available, measured in units equivalent to the Nvidia H100 GPU. We based the share of power capacity on the share of chips because there was more relevant data available, and there is a strong correlation between power capacity and the number of chips. Our best guess is that Google currently has the largest share, at 33% (20% to 50%). See [[#^appendix-b-fraction-of|Appendix B]] for further details. It’s possible that some companies might choose to reserve a substantial fraction of their resources for inference; here we implicitly assume they will dedicate a majority of their resources to a training cluster, which later might be reused for inference.
[^cite-36]: Gemini technical report: “Training Gemini Ultra used a large fleet of TPUv4 accelerators owned by Google across multiple data centers”.
[^note-37]: This corresponds to a [11,000km ring network](http://www.gcmap.com/mapui?P=SFO-PDX-SLC-DEN-MCI-DSM-MSP-ORD-IND-CMH-IAD-CLT-ATL-BNA-DFW-AUS-PHX-SFO&PM=b:disc5&DU=mi) connecting all major data center hubs in the US. We assume that the signal propagates at [200,000 km/s](https://en.wikipedia.org/wiki/Optical_fiber#Index_of_refraction:~:text=From%20this%20information%2C%20a%20simple%20rule%20of%20thumb%20is%20that%20a%20signal%20using%20optical%20fiber%20for%20communication%20will%20travel%20at%20around%20200%2C000%20kilometers%20per%20second.). This is a pessimistic assumption—distributed data centers need not be spread this far apart. We also consider the latency of switches for sending packets. Modern ethernet switches like Marvell’s Teralynx 10 have latencies in the order of [500 ns per packet forward](https://www.youtube.com/watch?v=wNi9DXaoqoE), which can be ignored in comparison to the much larger flight latencies.
[^note-38]: Under chinchilla-optimal scaling, a model should be trained on 20 tokens per parameter. And training a model requires 6 FLOP per token and per parameter. So the FLOP would be 6 x 1.4e16 x 1.4e16 / 20 = 5.88e31.
[^note-39]: Other fiber optic solutions such as [Infinera’s GX series](https://www.infinera.com/products/gx-series-compact-modular-platform/) might achieve better performance, boasting 1.2 Tbps per fiber and wavelength.
[^note-40]: The math is slightly complex, as more bandwidth results in us being able to train larger models, but larger models take longer to perform gradient updates. We explain the calculation in [[#^appendix-c-bandwidth-constraints|Appendix C]].
[^note-41]: Note that the switch-router paradigm might not be how data centers coordinate. For instance, multiple nearby data center can be connected via protocols like [RDMA over Converged Ethernet (RoCE)](https://docs.nvidia.com/networking/display/mlnxofedv23070512/rdma+over+converged+ethernet+%28roce%29) to coordinate large training runs without routers mediating the connection. Still, we consider the B4 network an illustrative example of the bandwidth that hypercalers can achieve between larger data centers.
[^note-42]: We derive this interval from a [bootstrapped exponential regression](https://colab.research.google.com/drive/14ixx63lTw8sPfkWh_VXlqwhwq-LKkb78#scrollTo=BYeVEPOgVvcn) involving 33 ASIC switch controllers announced between 2001 and 2023.
[^cite-43]: Increasing fiber capacity would require increasing the number of ports or the bandwidth per fiber. While long range connections up to 700Tbps per fiber [have been demonstrated](https://iopscience.iop.org/article/10.1088/2040-8986/ad261f#joptad261ff1), experts we consulted believe that in commercial settings we should expect bandwidths per fiber up to 3 Tbps, as techniques applied in research setting to go beyond these connections rely on technologies like Spatial Domain Multiplexing that are believed to be commercially inferior to increasing the number of fibers. The historical trend would suggest 600 Tbps / 128 ports = 5 Tbps by the end of the decade, which is roughly congruent with the expert assessment, suggesting that the trend can in fact be continued up to this point.
[^note-44]: Two relevant cost examples for bandwidth expansion: the 200 Tbps, 6,000km [MAREA trans-atlantic cable](https://www.submarinenetworks.com/en/systems/trans-atlantic/marea) cost $165 million, while commercial 200G last-mile underground fiber deployment ranges from [$11.30 to $24.13 per foot](https://fiberbroadband.org/wp-content/uploads/2024/01/Fiber-Deployment-Annual-Report-2023_FBA-and-Cartesian.pdf). These costs might not be very representative of land inter-data-center connections.
[^note-45]: This estimate corresponds to the distributional minimum of the training runs allowed by distributed power and bandwidth.
[^note-46]: This last estimate corresponds to the distribution maximum of the previous estimate and the training runs feasible in a single data center campus.
[^note-47]: One natural question is whether AI developers could simply outbid existing users to acquire more power, independent of supply growth. In the US, utilities are heavily regulated and are [overseen by commissions](https://en.wikipedia.org/wiki/Utility_ratemaking) that scrutinize their pricing decisions. This could limit how much data centers can outbid others for power.
[^note-48]: Full development time, including planning, permitting, and construction, would take longer. Solar plants require <2 years including planning time but not including permitting.
[^note-49]: Globally, nuclear plants average [6-8 years](https://www.sustainabilitybynumbers.com/p/nuclear-construction-time), but the most recent nuclear plant in the US, Vogtle, took [~14 years](https://en.wikipedia.org/wiki/Vogtle_Electric_Generating_Plant). Major hydro plants such as [Bath County](https://en.wikipedia.org/wiki/Bath_County_Pumped_Storage_Station) and [Grand Coulee](https://en.wikipedia.org/wiki/Grand_Coulee_Dam) appear to have required roughly 10 years. Wind power timelines seem quite variable and it is unclear what the distribution is.
[^note-50]: Though a few recently-closed nuclear plants [may be reopened](https://www.washingtonpost.com/business/2024/07/10/three-mile-island-nuclear-artificial-intelligence/) within a shorter time frame. There are also companies working on various types of next-generation nuclear plants, including [two](https://www.bloomberg.com/news/articles/2024-07-18/sam-altman-s-helion-energy-promises-fusion-power-by-2028) [companies](https://www.nbcnews.com/tech/tech-news/nuclear-power-oklo-sam-altman-ai-energy-rcna139094) backed by Sam Altman, but these seem unlikely to be deployed at scale by 2030.
[^note-51]: Solar power is arguably cheaper than gas overall, but requires higher upfront capital costs in exchange for very low operation costs: the [EIA](https://www.eia.gov/analysis/studies/powerplants/capitalcost/pdf/Capital_Cost_Study_Discussion_Slides.pdf) estimates that solar power with batteries has a capital cost of over $2k/kW; adjusting for solar’s intermittency, this would be greater than $8k/kW. Companies seeking to scale up power very aggressively may have high discount rates and prefer gas for that reason.
[^note-52]: A [2020 paper](https://ohiorivervalleyinstitute.org/wp-content/uploads/2021/10/CCUS-Report-FINAL-3.pdf) estimates that carbon capture would add 3.87 cents per kWh to the cost of gas. Another estimate is that carbon capture for gas costs [$79 to $88](https://www.spglobal.com/marketintelligence/en/news-insights/latest-news-headlines/natural-gas-plants-with-carbon-capture-could-save-industry-billions-8211-think-tank-71866689) per tonne of CO2 emissions. Given that natural gas produces [~1 pound, or ~1/2000 tonnes](https://www.eia.gov/tools/faqs/faq.php?id=74&t=11) of CO2 per kWh, this also implies ~4 cents per kWh.
[^note-53]: 1700 W over 270 days is [~11,000 kWh](https://www.wolframalpha.com/input?i=1700+watts+*+270+days+in+kilowatt-hours), or ~$1800 at 17 cents per kWh.
[^note-54]: However, the total capacity of projects in the interconnection queue is enormous at 1480 GW, so it is not clear how binding this constraint is. Most projects that apply for interconnection are ultimately withdrawn, so this does not imply that 1480 GW of capacity will come online in the coming years.
[^note-55]: There is [bipartisan interest](https://www.utilitydive.com/news/manchin-barrasso-permitting-reform-bill-demand-hearing-aep/716809/) in making it easier to approve new power plants and energy infrastructure.
[^note-56]: There isn’t a consensus on whether clean energy or fossil fuels are most apt for powering AI growth. NextEra’s CEO [said](https://www.bloomberg.com/news/articles/2024-06-12/tech-firms-are-asking-energy-giant-nextera-for-enough-electricity-to-power-miami) that wind and solar are more promising than gas, while [Ernest Moniz](https://www.wsj.com/business/energy-oil/big-techs-latest-obsession-is-finding-enough-energy-f00055b2), former US secretary of energy, believes that data centers will have to rely heavily on fossil fuels. In any case, constraining the set of possible energy sources presumably would make a scale-up more difficult.
[^note-57]: Some coal plant retirements have already been [delayed](https://www.bloomberg.com/news/articles/2024-01-25/ai-needs-so-much-power-that-old-coal-plants-are-sticking-around) due to data center demand.
[^note-58]: Throughout this section, we focus on Nvidia due to its dominant market share. However, we expect that AI chips from other firms, including Google TPUs, will face similar constraints to scaling production. The AI chip supply chain is highly concentrated in foundries like TSMC, SK Hynix, and Samsung, so different chipmakers will face similar constraints.
[^note-59]: Assuming that one lab amasses ~1/4th of the 2 million H100s for training (see [[#^appendix-b-fraction-of|Appendix B]]), with 2e15 FLOP/s at FP8 precision, 40% FLOP/s utilization, and 6 months of training.
[^note-60]: 16 million GPUs performing [2e15 FLOP/s each at 40% utilization over 6 months](https://www.wolframalpha.com/input?i=16+million+*+2e15+FLOP%2Fsecond+*+0.4+*+6+months) can perform 2e29 FLOP.
[^note-61]: This is even after assuming that performance improvements continue improving at historical rates of around [40% per year](https://colab.research.google.com/drive/1i9uGDEgHR01k7EQzvODlxTkM007emVjI), which would be sufficient for an 8-fold increase in performance, not enough for a 20x increase in total FLOP.
[^note-62]: A wafer is a large piece of silicon that is used to produce many dies, which are packaged into chips. One wafer can produce enough dies for [28 H100](https://www.trendforce.com/news/2024/03/18/news-tsmc-boosts-investment-in-advanced-packaging-with-ntd-500-billion-plan-to-build-six-plants-in-chiayi-science-park/) chips.
[^note-63]: It is unclear when full capacity will be reached.
[^note-64]: This does not mean that the number of chips itself will grow at this rate, especially if, as with the Nvidia B200, [multiple dies will be packaged into a single chip](https://spectrum.ieee.org/nvidia-blackwell).
[^note-65]: Sustaining the trends in AI chip performance may require a new packaging paradigm other than CoWoS in the future, which may require transitioning to new production lines. While this adds some uncertainty, our model assumes that future growth will be similar to the recent and planned levels of growth in CoWoS.
[^note-66]: We estimated an average of about 50,000 3nm wafers and 130,000 5nm wafers per month for Q4 2023, [based on corresponding revenue reports and estimated wafer prices](https://docs.google.com/spreadsheets/d/1XkZutYRk8E6StMD2B1dkfIJpfL5zGDhFXkT5xg_oxW4/edit?usp=sharing). Similarly, China Times reported that [60k to 70k](https://www.ctee.com.tw/news/20231121700061-430501) 3nm wpm was expected by the end of 2023. Combining the 5nm and 3nm figures, the total monthly production for 5nm and 3nm process nodes at the start of 2024 was likely to be around 180,000. This translates to an annualized production volume of 2.2M wafers using these advanced process technologies. Note that NVIDIA H100 GPUs are manufactured on a specialized TSMC [4N node](https://www.nvidia.com/en-us/data-center/technologies/hopper-architecture/), but this node is [included](https://www.tomshardware.com/news/tsmc-to-boost-4nm-and-5nm-output-by-25-percent) under 5nm in [TSMC’s revenue reports](https://investor.tsmc.com/chinese/encrypt/files/encrypt_file/reports/2024-01/894c1f6b900634fd7f369ef213bdfbf11c617297/4Q23ManagementReport.pdf).
[^note-67]: Assuming [28 H100 dies per wafer](https://www.trendforce.com/news/2024/03/18/news-tsmc-boosts-investment-in-advanced-packaging-with-ntd-500-billion-plan-to-build-six-plants-in-chiayi-science-park/) after accounting for defects, 2 million H100 GPUs would require about 71,429 wafers. Using the estimate of 130,000 5nm wafers per month for early 2024, this represents roughly 5% of TSMC’s annualized 5nm wafer capacity (71,429 / (130,000 \* 12) ≈ 4.6%).
[^note-68]: This can be approximated as $revenue_{growth} - \frac{margin_{growth}}{100}$, where $margin_{growth}$ is an additive number of percentage points.
[^note-69]: Even this is conservative relative to Nvidia’s [data center revenue](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-first-quarter-fiscal-2025) growth over the past five years.
[^note-70]: From [8.18M 12-inch equivalent wafers per year in 2014](https://investor.tsmc.com/static/annualReports/2014/english/pdf/e_11_1.pdf) to roughly [16.5M in 2023](https://investor.tsmc.com/static/annualReports/2023/english/index.html). TSMC’s [planned capex for 2025 growth](https://money.udn.com/money/story/12926/8064819) is in line with these historical rates.
[^note-71]: If we model production as proportional to capex raised to some power, scaling up capex growth proportionally should increase production growth proportionally. So 8% / 15% \* (30% to 70%) ~= 16% to 37%.
[^note-72]: If in 2029 training and inference compute are equal, and training compute continues to grow [at 4x per year](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year), one-quarter of total compute (equal to 2029’s training) will run inference on 2029 models, while three-quarters will train 2030 models. This suggests that 80% of 2030’s compute would be used for training new models, while 20% would be used for inference on last year’s models.
[^note-73]: Large proprietary models such as GPT-4o and Claude Opus 3.5 might have been trained on larger data stocks.
[^note-74]: Following a reasoning similar to [our previous work on data bottlenecks](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data), we also adjust the dataset size by 5x epochs and a 5x quality penalty factor. These factors cancel out in our median estimate.
[^note-75]: To estimate this, we consider that the compute used to train a model is roughly [six times the amount of training tokens times model size](https://epoch.ai/blog/estimating-training-compute). The Chinchilla prescription of 20 tokens per parameter would recommend 25 trillion parameters, and 6 \* 25T \* 500T = 7.5e28.
[^note-76]: What if we are training sparse models, such as mixture-of-expert architectures? Sparsity allows to greatly reduce the number of parameters involved in each forward pass. If the number of tokens used for training roughly follows Chinchilla scaling we would then expect data stocks to become fully utilized at lower compute scales, by at least as much as 10x given typical sparsity levels. However, scaling laws for sparse models are poorly understood—efficiently trained models might be trained on less data. For the time being we ignore this consideration.
[^note-77]: Once AI labs run into a training data bottleneck, they can still train larger models without increasing the dataset size to increase performance, at a reduced efficiency – this is known as _undertraining_. For example, if the loss follows the Chinchilla parametric fit one might be able to undertrain models by a factor of up to 3000x with the loss gradient only reducing by a factor of 10x with respect to Chinchilla scaling. Similarly, AI labs might choose to _overtrain_ models to increase the efficiency at inference time (as this allows to reach similar performance with smaller models). Overtraining might cause AI labs to run into data bottlenecks sooner. For simplicity, we set aside undertraining and overtraining considerations.
[^note-78]: Another consideration is that the stock of human-generated text data grows over time, as population increases and as a larger share of internet penetration is achieved. We previously estimated that this will contribute to [grow the stock of publicly available text data](https://epoch.ai/blog/will-we-run-out-of-ml-data-evidence-from-projecting-dataset) by about 7%/year, increasing the data stock by 50% by the end of the decade. We account for this in our final estimates, but given its small significance we elide it in the discussion.
[^note-79]: We ignore here more exotic sources of data, including personal correspondence, recordings of user device activity and scientific and astronomical data. These might enable even further gains.
[^cite-80]: [Chameleon](https://arxiv.org/abs/2405.09818v1) used a mix of 37% image data, [Qwen-VL](https://arxiv.org/abs/2308.12966) used 17%, and GPT-4 [allegedly](https://www.semianalysis.com/p/gpt-4-architecture-infrastructure) used 15%.
[^note-81]: The most expensive pure vision model in our database is ViT-22B, at 4e23 FLOP, 2 orders of magnitude less than frontier language and multimodal models.
[^note-82]: Biological sequence databases contain [billions of protein sequences](https://epoch.ai/blog/biological-sequence-models-in-the-context-of-the-ai-directives#biological-sequence-data), and [petabytes of genetic data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7778961/), but most genetic sequences are highly redundant – only up to 0.4% of the human genome is variable across individuals. The total deduplicated size is therefore likely in the tens of trillions of tokens, significantly less than image or text data.
[^note-83]: For instance, one could use a speech-to-text model like [Whisper](https://openai.com/index/whisper/) to transcribe the [30 million podcasts recorded last year](https://www.demandsage.com/podcast-statistics/) and generate on the order of 30M podcasts x 10 minute/podcast x 3 token/second = 2.7B tokens of text.
[^note-84]: [McGrady et al (2024)](https://journalqd.org/article/view/4066) report an estimate of around 14 billion videos uploaded to YouTube (updated [here](https://www.theatlantic.com/technology/archive/2024/01/how-many-videos-youtube-research/677250/)), with a mean duration of 615.14 seconds. The total amount of video content on the internet is likely not much greater, as Youtube already makes up [7% of all internet traffic](https://www.similarweb.com/top-websites/). (While traffic and content are not the same thing, they are likely well correlated.) [Lee (2021)](https://riseaboveresearch.com/rar-reports/2021-worldwide-image-capture-forecast-2020-2025/) reports that worldwide image capture is in the order of ~1T/year, so the stock will likely be close to ~10T images total.
[^note-85]: The paper linked uses 32 tokens for the encoding, but the used token dictionary is 70% smaller than a typical text token dictionary.
[^note-86]: [[#^appendix-d-equivalence-between|Appendix D]] describes a more careful estimate of the equivalence between modalities. In short, we make an educated guess based on existing work on image and video tokenizers, as well as image and video compression rates. We arrive at an estimate of 2 to 290 tokens per image or second of video.
[^note-87]: As we mentioned, the internet contains on the order of ten trillion seconds of video, most of it with matching audio. However, there is likely significant redundancy between a video and its corresponding audio. Many recordings of speech are also transcribed, as is the case with audiobooks. A large source of mostly untranscribed audio are podcasts: the [Podcast Index](https://podcastindex.org/) has indexed [143 million podcast episodes](https://stats.podcastindex.org/daily_counts.json?utm_source=podnews.net&utm_medium=web&utm_campaign=podnews.net%3A2022-03-10) or about 350B seconds of audio at an average duration of [~40 minutes per episode](https://pacific-content.com/how-long-is-the-average-podcast-episode-81cd5f8dff47/). Music is likely the least redundant type of audio data, and Spotify contains [100 million songs](https://en.wikipedia.org/wiki/Spotify), corresponding to about 24B seconds of music. Overall, it seems likely that there are on the order of hundreds of billions of seconds of publicly available, non-redundant audio.
[^note-88]: As with text, private datasets probably contain more data than public sources. Whatsapp alone receives [7 billion voice notes](https://blog.whatsapp.com/making-voice-messages-better) per year, corresponding to 100B-1T seconds of speech, for a total of 1-10T seconds over 10 years.
[^note-89]: A target model trained with tenfold as much compute would have $\sqrt{10}$ times as many parameters, and so would take $6 \times \sqrt{10} \times N$ FLOP to process a datapoint during training. Generating that data point would require $10 \times 2N$ FLOP using the initial model with $N$ parameters and exploiting the inference-training tradeoff over a $\text{10x}$ training gap. Therefore, the ratio between the compute used for generation and training on each datapoint is $\frac{10 \times 2N \text{ FLOP}}{6 \times  \sqrt{10} \times N \text{ FLOP}} = \frac{\sqrt{10}}{3} \approx 1$.
[^note-90]: In most cases, there is a [limit to how much expanding inference compute can benefit output quality](https://epoch.ai/blog/trading-off-compute-in-training-and-inference). This plateau typically occurs after increasing inference compute by 1-2 orders of magnitude, though for some specific tasks like code generation with unlimited trials, the benefits may extend further.
[^note-91]: Through this section we follow the results of [Erdil and Schneider-Joseph (2024)](https://epoch.ai/blog/data-movement-bottlenecks-scaling-past-1e28-flop).
[^note-92]: A related bottleneck we aren’t discussing are reductions in utilization through an imbalance of computation and memory access, also known as the _memory wall_. This occurs with small matrices, and we in fact expect this to be more binding on current hardware than the latency bottleneck. It is unclear how the balance between memory bandwidth and hardware performance will evolve in the future.
[^note-93]: The [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc) indicates a base latency of 6.8 µs, and a variable NVLINK ring latency of 0.6 µs per rank and round of communication. In a typical NVLINK configuration one would have 8 GPUs, of which 2-3 talk per matmul for 2D tensor parallelism purposes. So the latency per communication per all-reduce is $6.8\,\mu\text{s} + 2 \times (3-1) \times 0.6\,\mu\text{s} = 9.2\,\mu\text{s}$, since an all-reduce requires two rounds of communication.
[^note-94]: The QKV projection, attention computation, and two consecutive linear layers.
[^cite-95]: One natural way to scale models is to scale the model width, the feedforward dimension and the number layers each roughly proportionally. This is backed up in practice by some developers. For instance, [Erdil and Schneider-Joseph (2024)](https://epoch.ai/blog/data-movement-bottlenecks-scaling-past-1e28-flop) calculate that [Hoffmann et al (2022)](https://arxiv.org/abs/2203.15556) scale their models as $L = 8.8e{-2}\, N^{0.27}$ , where $L$ is the number of layers and $N$ is the number of parameters. Note that there is little existing work on “shape” scaling laws, so we are significantly uncertain about whether this relation will hold in the future.
[^note-96]: To step through the calculation: The training time $T$ must be less than nine months, and is at least as high as the induced latency $t_L \times L \times D/B$, where $t_L$ is the minimal latency per layer and batch, L is the number of layers and $D/B$ is the number of batches processed (dataset size $D$ divided by batch size $B$). Solving $T > t_L$ × L × D/B with the scaling assumptions $L = 8.8e{-2}\, N^{0.27}$ and $D = 20N$ results in $N < \left[\frac{T\times B}{20 \cdot t_L \cdot 8.8e{-2}}\right]^{1/1.27}$ ($N$ is the number of model parameters). This results in a maximum model size of 700T parameters, which following Chinchilla scaling would allow a training run of $C = 6DN = 6 \cdot 20 N^2 = 6e31$ FLOP.
[^note-97]: We considered further optimizing the loss under a latency constraint by undertraining. This resulted in small loss reductions compared to Chinchilla scaling, so we ignore this possibility.
[^note-98]: If the models use sparsity, the compute spent per parameter of the model might be significantly less even if the number of layers – and thus the latency – stays constant. However, it might also change the optimal relation between the amount of data and the number of layers of the model. Scaling laws for sparse models are poorly understood, so we ignore this possibility for the time being.
[^note-99]: We can model the all-reduce latency involving $M$ pods and $N$ GPUs per pod as $t = t_{\text{KERNEL}} + t_{\text{BASE}} + 2 \times \left(3 \times t_{\text{INTRA}} + \log_2(N) \times t_{\text{INTER}}\right)$. We have values $t_{\text{BASE}} = 6.8\,\mu\text{s}, \quad t_{\text{INTRA}} = 0.6\,\mu\text{s}, \quad t_{\text{INTER}} = 5\,\mu\text{s}$ for values of the base, intranode (NVLINK) and internode (InfiniBand) latencies in the low latency (LL) tree setup described in the [NCCL repository](https://github.com/NVIDIA/nccl/blob/ab2b89c4c339bd7f816fbc114a4b05d386b66290/src/graph/tuning.cc), plus a $t_{\text{KERNEL}} = 4.5\,\mu\text{s}$ kernel latency as in [Erdil and Schneider-Joseph (2024)](https://epoch.ai/blog/data-movement-bottlenecks-scaling-past-1e28-flop).
[^note-100]: [[#^appendix-e-computing-the|Appendix E]] explains how we calculate this number. In essence, we set up a nonlinear system of equations where the latency is related to cluster size, and vice versa.
[^note-101]: For [Chinchilla scaling](https://epoch.ai/blog/chinchilla-scaling-a-replication-attempt), the loss is reduced as the ~0.35th power of model size.
[^note-102]: So far the discussion has focused on 2030 as a date of interest, but the underlying extrapolative model we have constructed can be applied to the years up to then and afterwards. See [[#^appendix-a-summary-of|Appendix A]] for a description of the model.
[^note-103]: A training run of 2e29 FLOP would require 30M H100-equivalents running at 40% utilization for three months. At a 44% performance improvement per year and a 10% increase in prices for leading ML GPUs, hardware acquisition costs would cost around $200B (or roughly half that if the training run duration were doubled).
[^note-104]: We provide a rough calculation to illustrate this in [[#^appendix-f-unprecedented-economic|Appendix F]].
[^note-105]: Given that generations of Nvidia data center GPUs are roughly two years apart, each previous generation is a factor of $1.44^2$ lower performance than the next, i.e. approximately 0.48x the performance. Supposing that Microsoft bought 150,000 of the past four generations of GPU, the total would be roughly $150,000 \times (1 + 0.48 + 0.23 + 0.11) = 273,000$.
[^note-106]: Microsoft made up 19% of Nvidia’s revenue in the first quarter of 2024 according to [estimates](https://finance.yahoo.com/news/big-tech-ai-investment-is-going-right-to-nvidia-chart-of-the-week-100002139.html?guccounter=1) from Bloomberg (via Yahoo Finance). Given Nvidia earned [$22.6B](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-first-quarter-fiscal-2025) in data center revenue in Q1 of this year, and assuming that Microsoft made up 19% of that, and with a price of [$30,000](https://www.hpcwire.com/2023/08/17/nvidia-h100-are-550000-gpus-enough-for-this-year/) per H100, we land on up to 140,000 H100s for Microsoft as of Q1 2024.
[^note-107]: CRN [reports](https://www.crn.com/news/components-peripherals/2024/google-was-third-biggest-data-center-processor-supplier-last-year-research) that TechInsights estimated revenue attributable to TPUs “by looking at custom chip design revenue reported by Broadcom—which helps Google design TPUs—and how Google deploys TPUs internally and for cloud customers. The firm then applied a fair market price to Google’s TPUs.”
