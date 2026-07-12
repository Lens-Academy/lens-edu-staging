---
title: "Why China isn’t about to leap ahead of the West on compute"
author:
  - "Veronika Blablová"
  - "Robi Rahman"
source_url: "https://epoch.ai/gradient-updates/why-china-isnt-about-to-leap-ahead-of-the-west-on-compute"
published: 2025-07-26 {>>{"author":"Elias's AI","timestamp":1783843119446}@@date and second author verified from the live epoch.ai byline on 2026-07-12<<}
created: 2026-07-02
accessed: 2026-07-02
description: "Chinese hardware is closing the gap, but major bottlenecks remain"
tags:
  - "article-importer"
---

Gradient Updates shares more opinionated or informal takes on big questions in AI progress. These posts solely represent the views of the authors, and do not necessarily reflect the views of Epoch AI as a whole.

We keep hearing that China is catching up with the West in AI compute. A great example of this comes from NVIDIA’s CEO Jensen Huang, who recently [claimed](https://www.youtube.com/watch?v=EV7qSW3HFxI) that China has made “enormous progress” in the last few years, and that “China is right behind us. We’re very, very close.”

And China has indeed been making a ton of progress. As we’ll see, Chinese hardware has been closing the gap across a range of metrics relating to computational power and data transfer, both of which are crucial aspects of AI workloads.

But despite this progress, we don’t think China is about to leap ahead of the West on AI compute. China’s top developers—including Alibaba, ByteDance, Baidu, and DeepSeek—still rely primarily on NVIDIA chips. And major roadblocks still remain before China can leap ahead.

The first bottleneck lies in chip manufacturing. U.S. export controls of chipmaking equipment make it more costly for China to produce chips at the massive scale needed for frontier model training and inference.

The second bottleneck lies in China’s weaker software ecosystem. Unlike NVIDIA’s CUDA stack, Chinese chips operate in ecosystems that are bug-prone, poorly-documented, and unstable.

As a result, we think that Chinese developers will continue to prefer to train their models on Western chips when available, for at least the next few years. However, this does not preclude them training on less-performant Chinese chips with a cost penalty, when Western chips are hard to acquire.

![newsletter-icon](https://epoch.ai/assets/icons/paper-plane.svg)

Get the latest from Epoch AI [Subscribe](https://epochai.substack.com/subscribe)

## On paper, China’s hardware is closing the gap

AI developers want to train and run better AI systems, and a huge part of this is using better AI hardware. This means using more powerful chips and better infrastructure to process large amounts of data.

What we’ve seen over the last few years is that while Western hardware remains better along these dimensions, Chinese hardware is closing the gap.

Take computational power as an example. Since 2017, the floating-point operations per second (FLOP/s) of both Chinese and non-Chinese chips have grown exponentially.[^1] Whereas there was an order of magnitude gulf between Chinese and Western silicon in 2018, this difference has shrunk to 3x today, the gap between China’s leading GPU, Huawei’s Ascend 910C, and NVIDIA’s B200, the leading Western GPU.[^2] Chinese chips even briefly held the lead with the release of the BR100 datacenter GPU, which was allegedly the fastest chip on the market at the time of release.[^3]

![](https://epoch.ai/assets/images/gradient-updates/2025/why-china-isnt-about-to-leap-ahead-of-the-west-on-compute/gu-diffusion-1-v1.png)

When we account for the costs of computation, we see a similar pattern. Chinese hardware has historically been cost-competitive with Western hardware, albeit available only in lower quantities. For example, although Huawei’s Ascend 910B was 3x weaker than NVIDIA’s H100 in computational performance, it was also 3x cheaper. Since these two GPUs were released in 2022, they had equal price-performance in the same year.[^4]

But focusing on computational operations is only half the story. For a fair comparison of Western and Chinese hardware, we also need to consider how well this hardware transfers data. This is crucial because AI workloads generally involve a huge amount of data processing across various hardware components.

One step in this process is moving data between a chip’s memory and its compute units. The maximum rate that this data transfer can occur is called the memory bandwidth, and it’s especially important for running AI systems [on long-context inputs or outputs](https://epoch.ai/gradient-updates/us-export-controls-china-ai).

On this metric, we also see Chinese hardware closing the gap. Western chips currently have the lead, with NVIDIA’s B200 currently having almost double the memory bandwidth of Huawei’s Ascend 910C.[^5] But Chinese chip memory bandwidth has improved at a rate of about 24% per year from 2017 to 2025, outpacing the roughly 13% annual gains seen by non-Chinese peers over the same period. If this rapid improvement is sustained, we could see parity in memory bandwidth as soon as the next generation of devices,[^6] though recent [export controls](https://www.federalregister.gov/documents/2024/12/05/2024-28270/foreign-produced-direct-product-rule-additions-and-refinements-to-controls-for-advanced-computing) on high-bandwidth memory present roadblocks against catching up.

The other crucial dimension of data transfer happens between chips. The maximum rate of this transfer, the interconnect bandwidth, needs to be high so that chips don’t spend too much time waiting for data during training.

As with the other metrics, Western hardware is currently in the lead. NVIDIA’s custom NVLink technology is over ten times faster than the PCIe 4.0 standard used with the Ascend 910C.[^7] To address this, Huawei has recently developed its own custom technology called the Unified Bus, used to link a network of chips in its CloudMatrix 384 system. Although this custom network reaches less than half the bandwidth of NVLink, and is not as well-supported by mainstream machine learning frameworks as NVIDIA’s interconnect stacks, the trend remains the same: Chinese hardware is catching up.

## China still has to overcome major bottlenecks in domestic AI compute

### In practice, reliance on Western chips persists

Despite all these improvements, and even with NVIDIA imports substantially restricted, domestic chips have never been predominant among leading Chinese AI developers.

One way to see this is by looking at our data on notable Chinese machine learning models. Filtering down to the 130 language models released between 2017 and 2024, we see that over 90% of these models were trained on Western hardware.[^8]

![](https://epoch.ai/assets/images/gradient-updates/2025/why-china-isnt-about-to-leap-ahead-of-the-west-on-compute/gu-china-2-v1.png)

Even if we exclude joint ventures with U.S., Australian, or U.K. institutions (where the developers can access foreign silicon), the clear majority of homegrown models relied on NVIDIA GPUs. In fact, the first model [reportedly](https://www.caixinglobal.com/2024-01-31/daily-tech-roundup-iflytek-releases-first-upgraded-ai-model-trained-entirely-on-chinese-chips-102162335.html) trained entirely on Chinese hardware was not released until January 2024, after several years of training models on Western hardware.[^9]

### Manufacturing Limitations and Export Controls

Probably the most important reason for the dominance of Western hardware is that China has been unable to manufacture these AI chips in adequate volumes. Whereas Huawei [reportedly](https://www.ft.com/content/f46b7f6d-62ed-4b64-8ad7-2417e5ab34f6) manufactured 200,000 Ascend 910B chips in 2024, [estimates](https://www.reuters.com/technology/artificial-intelligence/nvidias-h20-chip-orders-jump-chinese-firms-adopt-deepseeks-ai-models-sources-say-2025-02-25/) suggest that roughly one million NVIDIA GPUs were legally delivered to China in the same year. Most of these NVIDIA chips are [H800](https://www.reuters.com/technology/nvidia-tweaks-flagship-h100-chip-export-china-h800-2023-03-21/) and [H20](https://www.tomshardware.com/tech-industry/artificial-intelligence/nvidias-defeatured-h20-gpus-in-china-sell-surprisingly-well-50-percent-increase-every-quarter-in-sanctions-compliant-gpus-for-chinese-ai-customers) GPUs, which are made less performant than the best Western chips in order to slide under the export control thresholds. Furthermore, tens of thousands of high-performance NVIDIA GPUs were likely [smuggled](https://www.cnas.org/publications/reports/countering-ai-chip-smuggling-has-become-a-national-security-priority) via third-country or illicit channels. But they’re still clearly an attractive option for Chinese developers, as evidenced by the high number of [orders](https://ifp.org/the-h20-problem/) from major Chinese AI [companies](https://ai-frontiers.org/articles/us-chip-export-controls-china-ai), including ByteDance, Alibaba, and Tencent.[^10]

Of course, Huawei is looking to expand its compute production to get around these bottlenecks. They are [reportedly](https://www.ft.com/content/f46b7f6d-62ed-4b64-8ad7-2417e5ab34f6) targeting 400,000 Ascend 910 (B and C) units in 2025, as well as potential new chips like the Ascend 920, [slated](https://www.datacenterdynamics.com/en/news/huawei-unveils-ascend-920-ai-chip-will-start-shipping-910c-to-chinese-customers-from-may-report/) to launch in the second half of 2025.[^11] However, this domestic supply is insufficient to train models on the frontier of scaling, since it is fragmented across various AI developers,[^12] and tends to be high in defects. These make large-scale training much more difficult, though not impossible, to achieve.

What makes China’s compute availability situation [more challenging](https://ai-frontiers.org/articles/us-chip-export-controls-china-ai) is the introduction of export controls over the last few years. Before these export controls, NVIDIA already dominated China’s AI compute with a [90% market share](https://www.reuters.com/technology/chinas-military-government-acquire-nvidia-chips-despite-us-ban-2024-01-14/).[^13] Now China has to deal with restrictions on key inputs to chip production as well.

One such input to chip production is semiconductor manufacturing equipment (SME). One prominent example of such equipment is the advanced lithography machines used to etch circuit designs on semiconductor chips, which are almost exclusively made by the Dutch firm ASML. Without access to foreign SME, domestic Chinese manufacturers like SMIC are left playing catch-up.[^14] Consider that these chip manufacturing devices aren’t perfect, and only a fraction of produced chips actually work. This fraction, known as the “yield”, decreases when using worse equipment. So it’s no surprise that SMIC’s reported yields are [below 50%](https://asiatimes.com/2024/02/smic-to-sell-huawei-costly-inefficient-5nm-chips/), compared to TSMC’s [90%](https://fuse.wikichip.org/news/2879/tsmc-5-nanometer-update).[^15] Such low yields make these Chinese chips substantially less economically viable, requiring state support to alleviate this financial burden.[^16]

These financial challenges are compounded by the other aspects of [American](https://www.reuters.com/technology/tsmc-could-face-1-billion-or-more-fine-us-probe-sources-say-2025-04-08/) and [Taiwanese](https://www.cnbc.com/2025/06/16/taiwan-blacklists-china-huawei-smic-further-aligning-with-us-trade-policy-.html) export controls, which restrict TSMC from manufacturing advanced chips on behalf of mainland Chinese companies.[^17] U.S. export controls also [effectively blacklist](https://www.bis.gov/media/documents/general-prohibition-10-guidance-may-13-2025.pdf) Chinese AI hardware use anywhere in the world. This makes it [risky](https://www.bis.gov/media/documents/general-prohibition-10-guidance-may-13-2025.pdf) for Chinese companies to adopt Huawei chips, since they could face American sanctions as a result.

### Software Ecosystem Gaps

In addition to hardware challenges, Chinese AI chips exist within a much less mature software [ecosystem](https://www.chinatalk.media/p/can-huawei-compete-with-cuda) than their Western counterparts.

On the one hand, we have NVIDIA’s CUDA, a software ecosystem for training across GPUs. This has benefited from over fifteen years of documentation and refinement, a large user base, and robust integration with popular machine learning frameworks like PyTorch and TensorFlow.

On the other hand, we have Huawei’s CANN framework. This was only introduced in 2019, twelve years after CUDA. And it’s often said by developers to be bug-prone, [unstable](https://www.ft.com/content/3dab07d3-3d97-4f3b-941b-cc8a21a901d6), and [poorly documented](https://www.chinatalk.media/p/can-huawei-compete-with-cuda), with frequent runtime crashes and limited third-party integration.[^18]

These issues don’t make it impossible for Chinese developers to perform large-scale training runs on Chinese hardware, but they certainly make it more costly. In fact, they have led many Chinese ML teams to adopt a hybrid approach, leveraging Huawei’s Ascend chips for inference workloads, while reserving their limited supplies of NVIDIA GPUs for large-scale training pipelines.[^19]

## Will China overcome these bottlenecks?

So far, we’ve argued that Chinese hardware has been catching up, but has only been used to a limited extent due to bottlenecks in chip manufacturing and the AI software ecosystem. This, however, leaves us with a big question: Will China overcome these bottlenecks in the near future?

Without access to advanced lithography equipment and the memory needed to create chips, Chinese manufacturers will be playing catch-up against the West. Even if export restrictions are alleviated, the immaturity of Chinese accelerator software ecosystems poses another serious bottleneck. China is trying to achieve parity in software and indigenize its supply chain, but even with massive subsidies, each roadblock will require years of work to overcome.

Put bluntly, we don’t see China leaping ahead on compute within the next few years. Not only would China need to overcome major obstacles in chip manufacturing and software ecosystems, they would also need to surpass foreign companies making massive investments into their own chip fabrication infrastructure and hardware R&D. Unless export controls erode or Beijing solves multiple technological challenges in record time, we think that China will remain at least one generation behind in hardware. This doesn’t prevent Chinese developers from training and running frontier AI models, but it does make it much more costly. Overall, we think these costs are large enough to put China at a substantial disadvantage in AI scaling for at least the rest of the decade.

_Thanks to Tharin Pillay, Lynette Bye, and Anson Ho for editorial suggestions, and Erich Grunewald, Mary Clare McMahon, and Yafah Edelman for helping to refine our research and takeaways._

## Appendix

| Year | Western Chips | Chinese Chips |
| --- | --- | --- |
| 2017 | NVIDIA V100 | — |
| 2018 | NVIDIA V100 | — |
| 2019 | NVIDIA V100 | Huawei Ascend 910A |
| 2020 | NVIDIA A100 | Huawei Ascend 910A |
| 2021 | AMD MI250X | Huawei Ascend 910A |
| 2022 | NVIDIA H100 | Huawei Ascend 910B  
Biren BR100\* |
| 2023 | AMD MI300X | Huawei Ascend 910B  
Biren BR100\* |
| 2024 | NVIDIA B200 | Huawei Ascend 910C |
| 2025 | NVIDIA B300 | Huawei Ascend 920\*\* |

Table 1: timeline of leading Western and Chinese chips in each year.

\*Not available for purchase due to export restrictions on TSMC wafers.

\*\*Exact specifications not yet published.

| Name | Release year | FP16 Performance (TFLOP/s) | Price-performance (GFLOP/s/$) | Thermal design power (W) | Energy efficiency (FP16 GFLOP/J) | Memory (GB) | Memory bandwidth (GB/s) | Interconnect bandwidth (GB/s) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| NVIDIA V100 | 2017 | 125 | 6.7 | 300 | 416 | 16/32 | 900 | 300 |
| NVIDIA A100 | 2020 | 312 | 13 | 400 | 780 | 40/80 | 1500 | 600 |
| NVIDIA H100 | 2022 | 989 | 22 | 700 | 1413 | 80/96 | 3300 | 900 |
| NVIDIA B200 | 2024 | 2250 | 64 | 1000 | 2250 | 192 | 8000 | 1800 |
| NVIDIA B300 | 2025 | 2500 | \* | 1200 | 2083 | 288 | 8000 | 1800 |
| AMD MI250X | 2021 | 383 | 26 | 500 | 766 | 128 | 3200 | 800 |
| AMD MI300X | 2023 | 1307 | 87 | 750 | 1743 | 192 | 5300 | 892 |
| Huawei Ascend 910A | 2019 | 256 | \* | 310 | 826 | 32 | 1280 | 270 |
| Huawei Ascend 910B | 2022 | 376 | 22 | 400 | 940 | 32 | 1600 | 392 |
| Huawei Ascend 910C | 2024 | 752 | 29 | 700 | 1142 | 128 | 3200 | 540 |
| Biren BR100 | 2022 | 1024 | \* | 550 | 1861 | 64 | 1640 | 412 |

Table 2: specifications of selected ML hardware.[^20]

\*Hardware prices not available.

## About the authors

Veronika Blablová

Veronika Blablová is a PhD student at Masaryk University, a research fellow at the Central European Institute of Asian Studies, and an Associate Data Analyst at Epoch AI, where she conducts research on Chinese AI models and hardware.

Robi Rahman

Robi Rahman managed Epoch's database of AI models, machine learning hardware, and GPU clusters. His research covers inputs and algorithms for AI development. Before joining Epoch AI, Robi was a contributor to the Stanford AI Index Report and received a master's degree in data science from Harvard University. He now works on AI governance at MIRI.

[^1]: See more regarding the trends in computational performance of machine learning hardware in [this data insight](https://epoch.ai/data-insights/peak-performance-hardware-on-different-precisions).
[^2]: Note that this refers to 16-bit performance. In particular, Huawei’s Ascend 910C [delivers](https://semianalysis.com/2025/04/16/huawei-ai-cloudmatrix-384-chinas-answer-to-nvidia-gb200-nvl72/) approximately 754 TFLOP/s, while NVIDIA’s B200 [delivers](https://resources.nvidia.com/en-us-dgx-systems/dgx-b200-datasheet) 2250 TFLOP/s. The DGX B200 server provides 18 PFLOPS of dense FP16/BF16 performance across 8 GPUs; each GPU has a performance of 18/8 = 2.25 PFLOP/s.
[^3]: The BR100 was never manufactured in large quantities, and China soon trailed in performance compared to NVIDIA’s H100 GPU. Benchmark trials by SemiAnalysis [found](https://i0.wp.com/semianalysis.com/wp-content/uploads/2024/12/71-bf16-gemm-perf-for-real-world-shapes-w-amd-images.png?resize=1489%2C1084&ssl=1) that H100s achieve 700-750 TFLOPS on dense matrix multiplications in BF16 arithmetic format, about 70-75% of its theoretical maximum BF16 performance. Based on DeepSeek’s [testing](https://www.tomshardware.com/tech-industry/artificial-intelligence/deepseek-research-suggests-huaweis-ascend-910c-delivers-60-percent-nvidia-h100-inference-performance), Huawei’s Ascend 910C processor—currently the most advanced chip manufactured in China—reached about 60% of Nvidia’s H100 performance, which would equal approximately 593 TFLOP/s, representing about 80% of the Chinese chip’s theoretical ceiling of 752 TFLOP/s.
[^4]: Compared with the H100, which was released around the same time, the Ascend 910B has lower total performance (376 vs 989 TFLOP/s) and memory bandwidth (1.6 vs 3.3 TB/s), but priced at ¥120,000 (around $16,000) versus the H100’s original retail price of $44,000, the chips had equal price-performance at 2.2×1010 FLOP/s per dollar. However, note that the lower memory and interconnect bandwidth of the Ascend 910B mean that it is less usable for scaled-up modern workloads than the H100, and therefore less useful after 2022.
[^5]: Specifically, NVIDIA’s B200 chip offers a memory bandwidth of 8 terabytes per second (TB/s), while Huawei’s Ascend 910C has a memory bandwidth of about 3.2 TB/s.
[^6]: We should also note that raw memory bandwidth only tells half the story. The ratio of bandwidth to memory is important because many ML kernels—optimizer updates, sparse embeddings, attention layers—are [memory-bound](https://en.wikipedia.org/wiki/Roofline_model), so their sustained FLOP/s is capped by their relative bandwidth per GB of memory. Chinese and western chips had historically similar ratios, but the latest domestic chips are inferior to Blackwell on this metric, and will need to improve if they are to be used at a scale matching the largest NVIDIA clusters.
[^7]: NVLink lets NVIDIA GPUs share data at up to 900 GB/s per chip. In comparison, the common PCIe 4.0 standard only moves data between chips at 64 GB/s.
[^8]: So far, DeepSeek—probably the most often referenced Chinese LLM—has also [used NVIDIA GPUs](https://arxiv.org/abs/2412.19437) to train its LLMs. Some social media posts [rumored](https://www.scmp.com/tech/tech-trends/article/3308227/deepseek-speculation-swirls-online-over-chinese-ai-start-ups-much-anticipated-r2-model) that R2 was trained on Ascend 910B but such claims have not been confirmed.
[^9]: In January 2024, iFLYTEK’s Spark 3.5 LLM was [reported](https://www.caixinglobal.com/2024-01-31/daily-tech-roundup-iflytek-releases-first-upgraded-ai-model-trained-entirely-on-chinese-chips-102162335.html) to be the first LLM trained entirely on domestic computing hardware, followed a year later by the only such reasoning model, [Spark X1](https://global.chinadaily.com.cn/a/202504/21/WS68060e40a3104d9fd3820aa6.html).
[^10]: These H20 orders were frozen as the U.S. Department of Commerce [imposed](https://techcrunch.com/2025/04/15/nvidia-h20-chip-exports-hit-with-license-requirement-by-us-government/) a [licence](https://www.wsj.com/livecoverage/stock-market-trump-tariffs-trade-war-04-16-25/card/u-s-confirms-new-export-curbs-on-nvidia-and-amd-chips-fBcQ4j5ueZDe5fdxpKoQ) requirement for the exports in April 2025. In July 2025, Nvidia [announced](https://apnews.com/article/nvidia-china-ai-chips-h20-trump-91588c36559bc881b8e010a9ed95cf0a) that it will be granted licenses to resume sales of H20 to China. This was preceded by CEO Jensen Huang personally [lobb](https://www.theguardian.com/us-news/2025/jul/15/trump-nvidia-jensen-huang-chips-china) ying President Trump, warning that Nvidia would lose US $5.5 billion and that continued chips exports are needed for the U.S. to [maintain](https://www.washingtonpost.com/world/2025/07/15/nvidia-ai-chip-sales-china/) AI leadership.
[^11]: Actual production may be even lower than targeted, as industry sources [believe](https://www.csis.org/analysis/deepseek-huawei-export-controls-and-future-us-china-ai-race#:~:text=Industry%20sources%20told%20CSIS%20that%20the%20Financial%20Times%20report%20is%20not%20correct%20and%20that%20Huawei/SMIC%E2%80%99s%20true%20yield%20remains%20at%2020%20percent.) that SMIC’s yield rate is worse than estimated by the FT.
[^12]: In theory, these chips can collectively perform 1028 floating-point operations per year, but with the Chinese AI industry heavily fragmented between dozens of developers, a substantial portion of compute dedicated to inference, and historically poor model FLOP utilization in large clusters of Huawei chips, Ascend processors are likely not sufficient to create leading models. Chinese state media often describe the situation as a “ [Hundred Model War](https://chinamediaproject.org/the_ccp_dictionary/hundred-model-war/) ”, which refers to the high number of companies involved in LLMs development. Baidu’s CEO already [warned](https://finance.yahoo.com/news/too-many-ai-models-china-093000688.html) that China has too many LLMs and the companies should focus more on their applications.
[^13]: NVIDIA CEO Huang Jensen [mentioned](https://economictimes.indiatimes.com/tech/artificial-intelligence/nvidia-says-us-export-controls-on-ai-to-china-were-a-failure/articleshow/121303942.cms) in May 2025 that NVIDIA’s share in the Chinese market dropped to 50%.
[^14]: Although Huawei and Semiconductor Manufacturing International Corporation (SMIC) are independent companies, the pressure of the U.S. export controls have made them mutually indispensable, forming a key pillar for China’s semiconductor ambitions. Huawei, cut off from its previous cooperation with TSMC, is one of SMIC’s most important clients. SMIC now manufactures most of Huawei’s chips (including datacenter [Ascen](https://www.tomshardware.com/tech-industry/artificial-intelligence/huaweis-homegrown-ai-chip-examined-chinese-fab-smic-produced-ascend-910b-is-massively-different-from-the-tsmc-produced-ascend-910) d, mobile [Kirin](https://www.reuters.com/technology/chinas-huawei-poised-overcome-us-ban-with-return-5g-phones-research-firms-2023-07-12/), and joint [plans](https://www.mobileworldlive.com/huawei/huawei-targets-3nm-chip-in-2026/) to manufacture 3 nm chips), and they also [cooperate](https://www.digitimes.com/news/a20250225PD224/huawei-ascend-ai-chip-yield-rate.html) in R&D.
[^15]: Here we are comparing yields specifically at the 7nm process, and in general the yield will depend on the specific design and specifications of the chip.
[^16]: In 2017, China’s “New Generation Artificial Intelligence Development Plan” [identified](https://digichina.stanford.edu/work/full-translation-chinas-new-generation-artificial-intelligence-development-plan-2017/) hardware as one of China’s weak points for becoming a dominant player in the AI field by 2030. Since then, the Chinese government has put a lot of investment into building domestic semiconductor capabilities and reducing reliance on foreign hardware. This includes a mix of gigantic [investment funds](https://www.reuters.com/technology/china-sets-up-475-bln-state-fund-boost-semiconductor-industry-2024-05-27/) and [subsidies](https://merics.org/en/report/huawei-quietly-dominating-chinas-semiconductor-supply-chain), with SMIC receiving a significant amount of state support, while Beijing [urges](https://www.bloomberg.com/news/articles/2024-09-27/china-urges-local-companies-to-stay-away-from-nvidia-s-ai-chips) Chinese companies to adopt domestic chips.
[^17]: In spite of the export controls, TSMC-manufactured chips likely ended up in Huawei’s AI processors. TSMC is currently under investigation for potentially violating the controls, which could lead to over $1 billion in [fines](https://www.reuters.com/technology/tsmc-could-face-1-billion-or-more-fine-us-probe-sources-say-2025-04-08/). These chips were officially made for Chinese firm Sophgo, but reverse-engineering [revealed](https://www.wsj.com/tech/mystery-surrounds-discovery-of-tsmc-tech-inside-huawei-ai-chips-7d922a01) they matched those used in Huawei’s Ascend 910B, suggesting a covert supply chain route. TSMC has halted shipments to Sophgo, reported the issue to authorities, and maintains it has complied with all regulations. It is estimated that TSMC manufactured and shipped over 2 million Ascend 910B logic dies to various [Huawei shell companies](https://www.csis.org/analysis/deepseek-huawei-export-controls-and-future-us-china-ai-race) after the imposition of the export controls.
[^18]: To overcome CANN’s performance and stability hurdles, Huawei has been [dispatching](https://www.ft.com/content/3dab07d3-3d97-4f3b-941b-cc8a21a901d6) teams of engineers to major customers—including Baidu, Tencent and iFlytek—to help port their CUDA-based training code to the CANN stack and keep deployments running.
[^19]: For example, [ByteDance](https://wccftech.com/bytedance-reportedly-acquires-100000-of-huaweis-ascend-910b-ai-chips/) and [Tencent](https://www.reuters.com/technology/chinas-tencent-seek-domestic-source-ai-training-chips-following-us-chip-curb-2023-11-15/) mentioned that they plan to use Huawei chips for inference and allocate their NVIDIA chips for training purposes. Huawei itself has [underlined](https://www.huaweicentral.com/huawei-eyes-nvidias-share-in-chinese-ai-chip-market-report/) its strategy to focus on dominating China’s inference rather than new LLM training. Although Huawei has [trained](https://arxiv.org/abs/2504.07866) some language models using Ascend chips, all of their publicly disclosed runs have involved a much smaller number of chips compared to frontier training—only several thousand, compared to hundreds of thousands.
[^20]: Price-performance calculations use release prices of the hardware, if available, which includes all NVIDIA chips except the B200. For chips whose prices are not published, we use estimates from public sources.
