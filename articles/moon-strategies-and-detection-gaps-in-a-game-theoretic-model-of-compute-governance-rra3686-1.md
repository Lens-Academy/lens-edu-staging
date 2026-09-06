---
title: "Strategies and Detection Gaps in a Game-Theoretic Model of Compute Governance"
author:
  - "Alvin Moon"
  - "Padmaja Vedula"
  - "Jesse Geneson"
  - "Simon Bar-on"
source_url: "https://www.rand.org/content/dam/rand/pubs/research_reports/RRA3600/RRA3686-1/RAND_RRA3686-1.pdf"
published: 2025-06-09
created: 2026-09-06
accessed: 2026-09-06
llm-review:
  date: 2026-09-06
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-06
    kind: "live"
description: "A RAND report using a simple game-theoretic model to identify gaps in compute-threshold-based AI training detection and to recommend how cloud-provider monitoring strategies could close them."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/moon-strategies-and-detection-gaps-in-a-game-theoretic-model-of-compute-governance-fig1-1dc49b30.jpg)

ALVIN MOON, PADMAJA VEDULA, JESSE GENESON, SIMON BAR-ON

# Strategies and Detection Gaps in a Game-Theoretic Model of Compute Governance --- ^strategies-and-detection-gaps

For more information on this publication, visit [www.rand.org/t/RRA3686-1](http://www.rand.org/t/RRA3686-1).

## **About RAND** ^about-rand

RAND is a research organization that develops solutions to public policy challenges to help make communities throughout the world safer and more secure, healthier and more prosperous. RAND is nonprofit, nonpartisan, and committed to the public interest. To learn more about RAND, visit [www.rand.org](http://www.rand.org).

## **Research Integrity** ^research-integrity

Our mission to help improve policy and decisionmaking through research and analysis is enabled through our core values of quality and objectivity and our unwavering commitment to the highest level of integrity and ethical behavior. To help ensure our research and analysis are rigorous, objective, and nonpartisan, we subject our research publications to a robust and exacting quality-assurance process; avoid both the appearance and reality of financial and other conflicts of interest through staff training, project screening, and a policy of mandatory disclosure; and pursue transparency in our research engagements through our commitment to the open publication of our research findings and recommendations, disclosure of the source of funding of published research, and policies to ensure intellectual independence. For more information, visit [www.rand.org/about/research-integrity](http://www.rand.org/about/research-integrity).

RAND's publications do not necessarily reflect the opinions of its research clients and sponsors.

Published by the RAND Corporation, Santa Monica, Calif.

© 2025 RAND Corporation

RAND® is a registered trademark.

## **Limited Print and Electronic Distribution Rights** ^limited-print-and-electronic

This publication and trademark(s) contained herein are protected by law. This representation of RAND intellectual property is provided for noncommercial use only. Unauthorized posting of this publication online is prohibited; linking directly to its webpage on [rand.org](http://rand.org) is encouraged. Permission is required from RAND to reproduce, or reuse in another form, any of its research products for commercial purposes. For information on reprint and reuse permissions, please visit [www.rand.org/about/publishing/permissions](http://www.rand.org/about/publishing/permissions).

## About This Report --- ^about-this-report

This report documents research and analysis conducted as part of a study entitled “Broadly Capable AI [Artificial Intelligence] Threats and Mitigation (BCAIT): How Can a Cloud Compute Provider Know If a Big AI Training Run Is Happening on Their System?” sponsored by the Technology and Security Policy Center (TASP) in the RAND Global and Emerging Risks division. The purpose of the study was to investigate detection and monitoring mechanisms that cloud service providers could employ to identify large AI training runs. The intended audience of this report is national policymakers interested in compute-based AI governance. This report may be of interest to cloud service providers and companies providing infrastructure as a service.

## Technology and Security Policy Center ^technology-and-security-policy

RAND Global and Emerging Risks is a division of RAND that delivers rigorous and objective public policy research on the most consequential challenges to civilization and global security. This work was undertaken by the division’s TASP, which explores how high-consequence, dual-use technologies change the global competition and threat environment, then develops policy and technology options to advance the security of the United States, its allies and partners, and the world. For more information, contact [tasp@rand.org](mailto:tasp@rand.org).

## Funding ^funding

This research was independently initiated and conducted within TASP using income from operations and gifts from philanthropic supporters, which have been made or recommended by DALHAP Investments Ltd., Effektiv Spenden, Ergo Impact, Founders Pledge, Charlottes och Fredriks Stiftelse, Good Ventures, Jaan Tallinn, Longview, Open Philanthropy, and Waking Up Foundation. A complete list of donors and funders is available at [www.rand.org/TASP](http://www.rand.org/TASP). RAND donors and grantors have no influence over research findings or recommendations

## Acknowledgments ^acknowledgments

We thank our project sponsors and TASP leadership, Jeff Alstott and Emma Westerman. We are also grateful to Ying Yi Dang, Casey Dugan, Edward Geist, Lennart Heim, Gabriel Kulp, Robin Meili, Henri van Soest, Cord Thomas, and Zev Winkelman for discussions that helped with the writing of this report. Finally, we would like to thank Onni Aarne and Aaron Frank for providing thoughtful and careful reviews of our final report.

## Summary --- ^summary

As the capabilities of artificial intelligence (AI) technologies continue to improve, policymakers will face the difficult challenge of balancing support for AI development and oversight to protect national security and reduce risks of unintended harms from AI systems. In this report, we analyze the effectiveness of AI training detection procedures for cloud service providers, to help inform compute-based AI governance and policymaking. We describe several ways in which AI governance policymakers might be able to improve the effectiveness of AI governance.

## Findings and Recommendations ^findings-and-recommendations

### *Findings* ^findings

- Cloud service providers might not be able to report and detect AI training if they are obligated to monitor and report activity based only on floating-point operation thresholds in future AI governance policy.
- In the future, many types of capable AI models will likely exist whose training will be hard to detect. We outline strategies for cloud service providers that could aid with AI training detection in cloud computing environments.

### *Recommendations* ^recommendations

- To develop effective AI governance, policymakers should support efforts to find detection gaps in compute-based monitoring schemes. These efforts should change and adapt with technological progress in AI.
- Policymakers should also continue to pursue both compute- and noncompute-based AI governance.
- Continuing research into effective thresholds for compute monitoring is required to create a robust compute-based monitoring framework that can adapt to technological progress.

## Contents --- ^contents

|                                                                                              |     |
|----------------------------------------------------------------------------------------------|-----|
| About This Report.....                                                                       | iii |
| Summary .....                                                                                | iv  |
| Strategies and Detection Gaps in a Game-Theoretic Model of Compute Governance .....          | 1   |
| Research Objective and Background.....                                                       | 1   |
| Creating a Simple Game-Theoretic Model of Artificial Intelligence Training Run Evasion ..... | 2   |
| Finding Detection Gaps .....                                                                 | 5   |
| Closing Detection Gaps .....                                                                 | 9   |
| Conclusion .....                                                                             | 11  |
| Appendix. Artificial Intelligence Training and Hardware.....                                 | 13  |
| Abbreviations.....                                                                           | 15  |
| References.....                                                                              | 16  |
| About the Authors.....                                                                       | 20  |

## Strategies and Detection Gaps in a Game-Theoretic Model of Compute Governance --- ^strategies-and-detection-gaps-2

## Research Objective and Background ^research-objective-and-background

The technical implementation of artificial intelligence (AI) governance is in development. In 2023, the U.S. Congress introduced several bills pertaining to AI standards and safety (U.S. House of Representatives, 2023; U.S. Senate, 2023a; U.S. Senate, 2023b), none of which had been enacted as of this writing. The same year, the Biden administration issued its “Executive Order 14110 of October 30, 2023: Safe, Secure, and Trustworthy Development and Use of Artificial Intelligence” (Biden, 2023), following an executive order from the first Trump administration that identified the need to regulate AI that could be used for “malicious cyber-enabled activity” through identity verification (Trump, 2021). In 2024, the California Legislature passed Senate Bill 1047 (California Legislature, 2024), the Safe and Secure Innovation for Frontier Artificial Intelligence Models Act, which was intended to mitigate risk of harm from large AI models.

Although the 2023 executive order was rescinded in 2025 (Trump, 2025) and Senate Bill 1047 (California Legislature, 2024) failed to pass into law in 2024 (Allyn, 2024), these two efforts are remarkable as AI policy documents because they relied on *compute governance*, or the regulation of AI development through computational resources used for training AI models. Both policies propose the use of *compute thresholds*, which are limits on computational resources for training models, to regulate large AI models. For example, in the case of the 2023 executive order, cloud service providers (CSPs) would have been obligated to report on customer AI training initially according to compute thresholds and later according to technical conditions on AI models set by the Secretary of Commerce.

Although, at the time of writing this report and to the best of our knowledge, there are no active bills or policies that refer to compute thresholds, it is possible that, in the future, compute-based AI governance could again require CSPs to report their customers’ training activities. Few CSPs have the necessary hardware and supporting infrastructure to train large AI models (Davenport and Alavi, 2023), and they might be hesitant to adopt additional monitoring schemes[^note-monitoring-schemes] because of voluntary industry standards that avoid identifying customer activities, apart from those that inform the billing for services provided (such as load-balancing by scaling up instances of a service). The service industry standard also places the responsibility of the data solely on the customer (i.e., a CSP does not have an insight into the content of a customer’s data). However, a CSP might be able to infer, based on technical measures or *metrics*, with high degrees of certainty, that large AI training runs are happening on its systems. In this report, we study how to improve compute-based monitoring policies by considering three questions:

[^note-monitoring-schemes]: Meaning monitoring in addition to company-specific billing and use policies.

- How large of an AI model can be realistically trained while evading compute-based reporting requirements?
- What types of AI models would escape detection?
- What compute-based thresholds could compute-governance policies use to discourage unreported training?

Providing complete answers to these three questions is outside the scope of this work. We do not think that empirical studies alone can provide a complete answer, given that part of this problem is modeling CSP and customer business interests and intentions. To complement empirical studies of these questions, we did the following:

- Create a simple, game-theoretic[^note-game-theoretic] model of AI training run evasion that reflects both a CSP’s potential reluctance to monitor its customers and a customer’s desire to escape notice.
- Describe examples of AI that fall within detection gaps.
- Use our simple model to show how increasing the number of types of compute-based thresholds closes detection gaps by allowing more-accurate detection or by increasing costs associated with hidden training to potential evaders.

[^note-game-theoretic]: A game-theoretic model uses *game theory*, or the mathematical study of strategic interactions between competing parties.

Considering our findings about detecting potential evaders, we give high-level recommendations to policymakers interested in the continued development and improvement of compute-based monitoring policies. We hope our introductory model and considerations, in combination with empirical analysis, will point future research in fruitful directions by providing a framework to evaluate compute thresholds and other compute-based governance schemes.

## Creating a Simple Game-Theoretic Model of Artificial Intelligence Training Run Evasion ^creating-a-simple-game-theoretic

Although large parts of our analysis would be possible outside the context of these models, our game-theoretic formalism emphasizes the conflicts of interest in the compute-governance landscape. For example, by exploring the constraints on CSP strategies, we identified the importance of a *mandatory metric*, defined in the section “Cloud Service Provider Monitoring Strategies.” Although CSPs have metrics for business purposes (Hagemann and Katsarou, 2021; Nawrocki and Sus, 2022), they would likely want to minimize the number, cost, and invasiveness of metrics used for reporting obligations. In contrast, a policymaker, who is not directly represented in our model but who ostensibly designs the rules of the game, would want to maximize the effectiveness of a compute-governance policy by ensuring that a set of mandatory metrics can detect violations of the policy while minimizing the size of the set, to promote compliance. Broadly, we hope that, by introducing formalism, we will add another lens for viewing and for solving problems in AI governance.

### *Parameters of the Game* ^parameters-of-the-game

We parameterized training using the following notions:

- **cloud service accounts:** an indeterminate resource describing the collection of user accounts registered with the CSP, as well as each account's access to compute resources. Each account accesses compute resources through *instances*, or allocations of hardware for computational tasks.
- **CSP monitoring strategies:** the methods a CSP will employ to detect AI training on its hardware
- **evader strategies:** the methods a user of a CSP can employ to evade detection while training an AI on the CSP's hardware.

For the remainder of this section, we specify the possible values of our parameters before defining our model of AI training.

#### Cloud Service Accounts ^cloud-service-accounts

A CSP allows users to access its infrastructure by registering accounts and requesting compute resources. Examples of compute resources include central processing units, graphics processing units (GPUs), as well as other, more specialized types of processing units for AI training (Khan and Mann, 2020). The user of a CSP account specifies the type and number of compute resources in an instance and uses the instance to execute algorithms. The exact ways in which physical compute resources owned by the CSP contribute to computational tasks requested by the user can be complicated. For simplicity, we assumed that CSPs offer one type of computational unit, GPUs, and that a GPU contributes to a computational task by executing operations at a constant rate in time. For a more detailed explanation of this assumption, see the appendix.

We also assumed that an account runs exactly one algorithm on one instance at a time. This way, there is a one-to-one correspondence between executions of algorithms and accounts. We assumed that the evader knows all regulatory policies. We also assumed that the CSP does not initially know which accounts are associated with the evader. Practically, this means that the CSP does not know whether the evader (or even a compliant user) has multiple accounts.

#### Cloud Service Provider Monitoring Strategies ^cloud-service-provider-monitoring

A CSP monitors several metrics for its accounts to bill its customers and optimize the allocation of its compute resources. A metric is a function that, given an account and a period of time, returns either an absolute quantity or a rate. Some examples of metrics are

- **total power:** the total power consumption of hardware associated with all instances of the account
- **maximum GPU cluster size:** the largest number of GPUs used simultaneously by a single instance of the account
- **floating-point operations (FLOPs):** the total number of FLOPs performed across all instances of an account.

Regulations about cloud computing could obligate a CSP to report on only a few metrics, which we call *mandatory metrics*. In our model, mandatory metrics determine the set of CSP strategies through compute thresholds. When the mandatory metric exceeds its threshold, a reading from the metric is recorded. For example, if the metric is the number of FLOPs performed in an hour, a threshold for this metric could be a maximum rate of FLOPs per hour. We assumed that a regulatory policy has set a threshold number for each mandatory metric.

#### Evader Strategies ^evader-strategies

Whereas the CSP’s strategies are determined by metrics, the evader’s strategies will be determined by its accounts with the CSP and the algorithms it wishes to run on the accounts. We limited the evader’s interactions with the CSP to the following actions:

- The evader can register and maintain an account with the CSP.
- Given an algorithm, the evader can run the algorithm on one of its accounts, using the type of instance that the algorithm requires.

If the evader has more than one account, it can choose the sequencing of algorithm execution. We also assumed that the evader knows all mandatory metrics and can evaluate these metrics on its own requested instances in real time.

### Detection Game ^detection-game

The detection game we use for the rest of this report is defined in the box.

:::callout {title="Detection Game"}
**Players**

- CSP
- evader

**Rules**

- The CSP chooses a set of metrics that must contain all mandatory metrics.
- The evader chooses a sequence of algorithms, each one either a training algorithm or not, to run in order using a set of accounts with the CSP. At least one of the algorithms must be a training algorithm.
- After all algorithms fully execute, the CSP identifies the accounts that exceeded any of the thresholds and decides whether these accounts have run training algorithms.

**Outcomes**

If the CSP finds at least one account that ran a training algorithm out of the set of accounts that exceeded any of the thresholds, and the CSP does not mistakenly pick any account that did not run a training algorithm, the CSP wins. Otherwise, the evader wins.
:::

See the section on data transfers and cluster sizes (“Large Data Transfers and Number of Graphics Processing Units”) for a discussion of a variant of the detection game involving more than one CSP.

### Finding Detection Gaps ^finding-detection-gaps

In this section, we describe how large of an AI model could be trained without being detected by a CSP. We argue that, according to the historical compute thresholds set by previous attempts at compute regulation, there is a detection gap for models trained within a floating-point training compute cost in the range between  $10^{23}$  and  $10^{26}$  operations. Later we discuss how, in the near term, smaller models will not be as capable as larger models below the  $10^{23}$ -operation lower limit of the detection gap. However, improvements to software might improve the capabilities of smaller models in the future.

The detection gap identified by our simple model does not account for methods that leverage pretrained models, such as those that are open-source, or new paradigms of machine learning. We discuss this possibility in our section on closing detection gaps.

### *Finding a Detection Gap* ^finding-a-detection-gap

In the table, we use publicly available statistics about BigScience’s open-source large language model, BigScience Large Open-Science Open-Access Multilingual Language Model (BLOOM) (BigScience Workshop, 2022), to show that CSPs might not be able to detect AI training by using the following thresholds from the 2023 executive order for AI models trained primarily on biological sequence data. Assuming that the CSP provides access to hardware with high network connectivity, a threshold is broken when training uses more than either of the following:

- $10^{23}$  floating-point or integer operations
- a group of GPUs capable of more than  $10^{20}$  floating-point or integer operations per second.

BLOOM’s training compute requirements marginally exceed the first threshold and give a historical example of a training session that we can use in our scenario.

#### BLOOM Training Statistics ^bloom-training-statistics

| Statistic                           | Value |
|-------------------------------------|-------|
| Number of GPUs                      | 384   |
| Number of days                      | ~118  |
| Training dataset size, in terabytes | 1.6   |
| Compute capacity, in TFLOPs/s/GPU   | ~150  |
| Number of epochs <sup>a</sup>       | 1     |

SOURCE: Features data from Huggingface, undated.

NOTE: TFLOP = tera-FLOP. TFLOPs/s/GPU = TFLOPs per second per GPU.

<sup>a</sup> An AI model has been *trained* on a dataset if its associated training algorithm updates the model in response to the data points in the dataset. An *epoch* is a single pass of the training algorithm through the whole training dataset.

By multiplying the number of GPUs by their individual compute capacities and number of days in the table, we estimated a training cost of  $5.8 \times 10^{23}$  FLOPs.[^note-sevilla-estimate]

[^note-sevilla-estimate]: Sevilla et al. (2022) reports a more conservative estimate of  $1.8 \times 10^{23}$  floats for BLOOM. In either case, the order of magnitude is the same, and reducing the leading coefficient of the float estimate will only improve the applicability of sequential training.

Suppose a CSP chooses to report only based on the thresholds above. Then, we argue, there is a way for the evader to train BLOOM without being detected. It suffices to show that there is at least one evader strategy that always wins against the CSP, which we call *sequential training*. We calculated

$$
384 \text{ GPUs} \times (1.5 \times 10^{14} \text{ FLOP/s per GPU}) = 5.76 \times 10^{16} \text{ FLOP/s.}
$$

So, if the evader chooses instances with 384 GPUs with maximum compute capacity  $1.5 \times 10^{14}$  FLOP/s/GPU, like in the BLOOM training run, its instances will remain under  $10^{20}$  FLOP/s, and the only relevant threshold is for total floating-point or integer operations. Then the entire training run for BLOOM could be accomplished through 58 distinct instances of  $10^{22}$  FLOPs accomplished at a rate of  $5.76 \times 10^{16}$  FLOP/s, without exceeding the threshold for total FLOPs. Under our hardware assumptions,[^note-appendix-hardware] each instance would take roughly two days.

[^note-appendix-hardware]: See the appendix for details on our assumptions on hardware.

In this calculation, the number of accounts used by the evader is not strictly determined. Increasing the number of FLOPs per session from  $10^{22}$  to just under  $10^{23}$  will decrease the number of accounts required for training at the cost of extending the length of a session. The calculations to determine this relationship are straightforward, and we omit them.

#### Predictions About Models in the Detection Gap ^predictions-about-models-in

In this section, we describe AI models that appear in the detection gap outlined above. AI models designed for biology are concrete examples. In the figure, we list several historical examples of AI models trained on biological sequence data that were designed for specific computational tasks, such as protein modeling. The example data are from the public Epoch dataset on compute trends for AI systems, published on January 17, 2024, and were selected through a keyword search for *protein* or *bio* in the model description.[^note-minerva-excluded]

#### **Training Compute Requirements for Biological Artificial Intelligence, Calendar Year 2016 to Calendar 2024** ^training-compute-requirements-for

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/moon-strategies-and-detection-gaps-in-a-game-theoretic-model-of-compute-governance-fig2-5b074566.jpg)

SOURCE: Features data from Epoch, undated.

[^note-minerva-excluded]: Minerva, an AI model developed by Google, was excluded from the result of this search because we did not find technical documentation indicating that it had been trained on biological sequence data.

According to the dataset, the only AI model in this search with training compute exceeding  $10^{23}$  FLOPs was Galactica, a model developed by Meta AI as a science-oriented large language model; however, it was arguably not primarily trained on biological sequence data (Taylor et al., 2022). We note that, although the Epoch dataset shows that the model xTrimoPGLM-100B required less than  $10^{23}$  FLOPs to train, a preprint submitted to bioRxiv[^note-biorxiv-definition] by the model’s developers claims that it required  $6.2 \times 10^{23}$  FLOPs to train (Chen et al., 2024). If the figures in the preprint by Chen et al. (2024) are accurate, xTrimoPGLM-100B was the first known AI model in the detection gap. Informed by the figure and scaling laws,[^note-scaling-laws] we predict that biological AI models will continue to incur higher training costs. Since Epoch published this dataset in 2024, at least one other generative AI model for protein analysis was developed using more than  $10^{23}$  total FLOPs (Hayes et al., 2025). In the future, it is likely that many AI models with uses in biology and chemistry will emerge in the gap.

[^note-biorxiv-definition]: bioRxiv is a public preprint repository for the biological sciences.

The figure also supports the hypothesis that expenditures for training compute will continue to trend upward, even within specialized application domains. In the near term, as specialized models are developed for specific tasks within application domains, such as computational biology, more models will fill the  $10^{23}$ - to  $10^{26}$ -operation detection gap. In the opposite direction, specialized AI models could require less training compute than general models, such as OpenAI’s generative pretrained transformer (GPT) series because their application domains are narrow. Technological advancements in machine learning could also shift the understanding of how much training compute is required to train a capable AI model. This could be accomplished by algorithmic and software improvements, or it could be accomplished by the development of new ways to implement AI systems, such as through the combination of compute-based machine learning and symbolic logic (Garcez and Lamb, 2020). Latter methods are examples of *neurosymbolic AI*, which represents one of many state-of-the-art research efforts to progress AI development beyond the current neural network–based architectures. There are also possibilities stemming from using pretrained models, such as open-source models, as an avenue for training capable AI models outside the framework of compute-based detection. Because an open-source model has already been trained, incorporating it into a mixture-of-experts AI system[^note-mixture-of-experts] would represent a “discount” in the training cost of the entire system. *Fine-tuning*, by specializing AI training after initial waves of training, could represent an extreme discount to training cost because it improves the capability of pretrained models at relatively little cost (Hu et al., 2021).

All together, these methods, combined with an upward trend in training compute, will simultaneously push the envelope of training costs and lower the training compute required to create capable models. The emergence of smaller, capable models will challenge compute-based policies that attempt to regulate these models using compute thresholds and will change the relevant ranges for detection gaps.

[^note-scaling-laws]: *Scaling laws* are relationships between training compute and AI model learning capability, first documented in the foundational papers Kaplan et al. (2020) and Hoffmann et al. (2022).

[^note-mixture-of-experts]: The mixture-of-experts method combines many AI models to produce an output; see Chen et al. (2022) for a review.

### Closing Detection Gaps ^closing-detection-gaps

In this section, we outline four CSP threshold strategies that close our model’s detection gap. We also mention several proposals for AI governance in the literature that are not based on thresholds and relate them to our problem of detecting AI training.

### *Large Data Transfers and Number of Graphics Processing Units* ^large-data-transfers-and

As the table shows, training datasets even for relatively small AI models can be large. Strategies for evading thresholds, such as sequential training, will most likely involve multiple accounts to distribute the reported activity, avoiding suspicious concentrations. Evaders may try to split training data across several accounts; see Shallue et al. (2019) for a discussion of the costs and benefits of data parallelism. However, it is unlikely that the largest AI models, representing the most-advanced current AI systems, can be trained this way while avoiding detection. So, assuming that training data are kept together during training, large and sudden data transfers into new accounts should capture training activity.

Another practically indivisible type of resource is the GPU. Although hundreds of GPUs is a small number compared with the thousands of GPUs typically used to train a large language model, requests for hundreds of GPUs at a CSP might be relatively rare in practice. Dividing training across different clusters of GPUs is prohibitively expensive with current models; for example, recent efforts by Google to implement distributed training of a large neural network required 32 times the baseline number of colocated training units to fully train the model (Douillard et al., 2024). Requiring CSPs to report based on sensitive GPU cluster size thresholds will also be effective at flagging AI training.

As an interesting corollary, we note that monitoring for large data transfers and cluster sizes to new accounts also increases the visibility of sequential training across different CSPs.

### *Patterns in Algorithm Instructions and Graphics Processing Unit Use* ^patterns-in-algorithm-instructions

Compared with most other types of algorithms, training algorithms for AI models have a limited set of instructions, and the most frequently executed instruction is the multiply-accumulate (MAC) operation (Chen et al., 2019; Li et al., 2017). Additionally, training algorithms are highly parallelized (Valiant, 1990). If a CSP monitors hardware parameters and kernel execution features, such as periodic synchronization and execution times, the CSP might be able to determine code features, such as instruction counts, that are otherwise hidden because of consumer privacy considerations. In the context of detection, the combination of a high number of MAC operations and a low number of distinct instruction types would imply a likelihood that an algorithm executed on cloud resources is a training algorithm. Explicitly, the threshold would be the ratio of MAC operations to total number of instructions in a given length of time, as implied by patterns in hardware use. Adversarial evaders could try to avoid detection

by this threshold by executing unrelated algorithms in between or during training activities, to reduce the total ratio of MAC operations, but this would come at a cost to training efficiency.

### *Power* ^power

Luccioni, Viguier, and Ligozat (2023) states that BLOOM required 433,196 kWh of energy across approximately 118 days, working out to an approximate average rate of 3,600 kWh per day. This figure is an order of magnitude greater than the highest average daily household energy use rate across U.S. states (U.S. Energy Information Administration, 2023). And although data are not available for proprietary AI models, such as OpenAI’s GPT-4, we expect BLOOM’s power cost to be a lower bound for large AI models (de Vries, 2023). Setting power consumption rate thresholds on accounts would enable capturing training activity.

### *Output and User Identity* ^output-and-user-identity

The previously discussed strategies are used to determine whether a user of a CSP is training a neural network–based AI model without inspecting the source code, generated data, or identifying information about the account owner. This constraint on accessible information is consistent with the business models of most CSPs, which guarantee levels of privacy for users. However, the literature on AI governance often considers scenarios in which CSPs have direct access to algorithm outputs and to information about account owners. For example, proof-of-learning and proof-of-training methods use intermediate outputs of compute units, such as GPUs, to verify that a user’s activities are training models that comply with predetermined training rules (Jia et al., 2021; Shavit, 2023). And know-your-customer (KYC) schemes propose requiring users to register with governing organizations and provide identifying details about entities and key personnel associated with accounts, as well as descriptions of purpose for compute (Egan and Heim, 2023).

Proof-of-activity and KYC schemes require knowing how a customer intends to use compute. In terms of the detection game in the figure, these schemes are CSP strategies that are not determined by thresholds. Instead, they rely on access to specialized metrics that reveal the user’s activities and identity across accounts. The “winning” conditions of this game, modified to allow nonthreshold CSP strategies and outside information about accounts, are not easily analyzed quantitatively. For example, Egan and Heim have predicted that, to resist KYC schemes, evaders could hide their identities through shell organizations; whether such a strategy would work is a matter of policy.[^note-shell-companies]

[^note-shell-companies]: Given the existing policies and procedures of detecting shell companies and countering illicit use, such as those followed by such organizations as the Financial Action Task Force and the U.S. Department of the Treasury’s Financial Crimes Enforcement Network, detecting illicit use for AI training might require additional nuances to these policies (Financial Crimes Enforcement Network, undated; U.S. Department of the Treasury, undated).

### *Determining Effective Thresholds* ^determining-effective-thresholds

Theoretic studies of effective thresholds have practical limitations to their applicability, and, without data-driven and empirical studies to ground them, they risk missing the main drivers of future efficacy of compute-based regulation. We highlight two related and important questions about thresholds that should be answered by future research to understand how to effectively set compute thresholds:

- Do different compute monitoring thresholds have different costs to observe?
- How can existing results about capabilities and performance from computing be paired with noncompute-based governance, existing or hypothetical, to create effective thresholds?

An answer to the first question will inform whether certain compute thresholds are reasonable for a CSP to adopt, and an answer to the second question would bridge the gap between technical literature and real-life policy.

## **Conclusion** ^conclusion

In this section, we provide recommendations to national policymakers on AI governance through compute thresholds.

### *Take Steps to Find and Close Detection Gaps* ^take-steps-to-find

With too few mandatory metrics, adversarial strategies, such as sequential training, can evade detection and successfully train AI that is potentially capable of harm. To develop effective AI governance, policymakers should support systematic efforts to identify and close detection gaps. We analyzed a simple model of evasion and showed that a detection gap exists in the model and contains AI trained on biological sequence data. In the future, the detection gap could also contain neurosymbolic AI. We have proposed several metrics to close this detection gap, any of which could be useful in detecting AI training, including data transfer patterns, numbers of GPUs, and power consumption. As technology and methods evolve, continued effort will be necessary to dynamically identify and close gaps.

### *Continue to Develop Both Compute and Noncompute-Based Governance for AI* ^continue-to-develop-both

AI governance might depend on noncompute mechanisms to be effective. For example, our analysis used a game-theoretic model of training that assumed that, if a CSP were able to identify at least one account belonging to an adversarial evader, it would satisfy its reporting obligation. This implies a role for a regulatory agency that would be able to determine the identity of the evader and compel it to disclose details about its activities. We anticipate that, going beyond our model, future compute governance would require nontechnical, policy-based mechanisms to work effectively.

### *Establish a Framework for Determining Compute Thresholds* ^establish-a-framework-for

Establishing a compute-governance policy necessarily means creating a framework to propose and evaluate compute thresholds. We recommend directing research toward the feasibility of thresholds that effectively govern AI models that require fewer than  $10^{26}$  FLOPs to train. Our proposed direction of using game-theoretic models in conjunction with empirical, data-driven results about AI capability is one way forward in establishing this framework. Regardless of the approach, an effective framework will relate technical aspects of training, such as training compute, with AI capability. An effective framework will also be able to adapt to technological progress and changing paradigms within AI research.

By incorporating these recommendations into future AI governance policies, national policymakers would take steps toward minimizing the ability of adversarial actors to evade compute-based monitoring schemes while training AI models.

## Appendix. Artificial Intelligence Training and Hardware --- ^appendix-artificial-intelligence-trainin

AI models that use neural networks, or prediction models based loosely on biological networks of neurons, require training before they can be useful for computational tasks. In this appendix, we outline the technical assumptions on training that we used throughout the study.

When we refer to an AI model, we assume that it is based on neural networks. Training a neural network requires a dataset from which to “learn” and computational resources to execute the learning. In practice, learning is the activity of creating and successively updating a large collection of variables called *weights and biases*. After the end of training, the final weights and biases are used by the AI model for such tasks as prediction and classification during the inference phase. We used the following criterion to determine when the model’s training is complete.

### Definition ^definition

An AI model has been *trained* on a dataset if its associated training algorithm updates the model’s weights and biases in response to the data points in the dataset. An *epoch* is a single pass of the training algorithm through the whole training dataset.

The runtime of an epoch depends on what computing resources were used during training. Although our definition of *training* technically requires using each element of the dataset only at least once during training, many models train over several epochs; our analysis will generalize in obvious ways over multiple epochs.

We now discuss assumptions about hardware performance. Our analysis assumed that training computations are performed by a GPU. We used the following simple rate calculation to quantify a compute unit’s contribution toward training time. If a GPU has a maximum compute capacity of  $N$  TFLOP/s, its output is approximated by

$$
\text{output} = \text{training time} \times N \text{ TFLOP/s} \times u,
$$

where  $u$  is the average utilization percentage of the GPU over the training time.

### Hardware Performance Assumptions ^hardware-performance-assumptions

We assumed an ideal situation in which  $u = 1$ , with the understanding that our analysis can easily be modified for different values of utilization. We approximated the output of a cluster of identical GPUs by multiplying the output of one GPU by the size of the cluster.

Last, we discuss how our hardware assumptions above relate to the sequential training strategy we first introduced in the section “Finding a Detection Gap.” Before starting sequential

training, the evader selects a training set, a neural network–based AI model, and desired compute resources. The evader then determines  $K$ , the integer such that  $K$  steps in the training algorithm trains through 1 epoch. We leave the precise notion of step undefined because this can depend on the training algorithm. For  $1 \leq i \leq K$ , denote by  $W_i$  the weights and biases of the model. A training run updates the weights and biases per step,  $W_{i-1} \mapsto W_i$ , so it has natural breakpoints defined by  $1 \leq i \leq K$ .

During the game, the evader chooses a partition  $k_1 < k_2 < \dots < k_m = K$  and prepares identical cloud computing accounts  $A_1, \dots, A_m$ . Then, the evader runs the training algorithm for steps  $1 \leq s \leq k_1$  on  $A_1$ , resulting in  $W_{k_1}$ . For subsequent indices  $1 < j \leq m$ , given input  $W_{k_{j-1}}$ , the evader runs steps  $k_{j-1} < s \leq k_j$  on account  $A_j$ , resulting in  $W_{k_j}$ .

In practice, the training of AI models is highly parallelized, meaning that the training data and algorithm execution are distributed across the GPUs in the instance. Choices in parallelization will change how and when the weights and biases are updated during training. We assumed that our sequential training strategy would be applied to training algorithms in which the compute requirements for a batch are much smaller than the relevant compute thresholds. This implies that, with proper choice of partition, a batch would not be trained across two accounts. Without this assumption, sequential training might require the passing of computation states between accounts. This passing of states would add complexity to our training description, but data transfer would not change the results of our analysis; the burden on time and resource costs would depend on the model, but data transfer would not violate a compute threshold condition based on FLOPs.

## Abbreviations --- ^abbreviations

|       |                                                                          |
|-------|--------------------------------------------------------------------------|
| AI    | artificial intelligence                                                  |
| BLOOM | BigScience Large Open-Science Open-Access Multilingual Language<br>Model |
| CSP   | cloud service provider                                                   |
| FLOP  | floating-point operation                                                 |
| GPT   | generative pretrained transformer                                        |
| GPU   | graphics processing unit                                                 |
| KYC   | know your customer                                                       |
| MAC   | multiply-accumulate                                                      |
| TFLOP | tera-FLOP                                                                |

## References --- ^references

- Allyn, Bobby, “California Gov. Newsom Vetoes AI Safety Bill That Divided Silicon Valley,” *Morning Edition*, September 29, 2024.
- Angluin, Dana, “Queries and Concept Learning,” *Machine Learning*, Vol. 2, April 1988.
- Biden, Joseph R., “Executive Order 14110 of October 30, 2023: Safe, Secure, and Trustworthy Development and Use of Artificial Intelligence,” *Federal Register*, Vol. 88, No. 210, November 1, 2023.
- BigScience Workshop, “BLOOM: A 176B-Parameter Open-Access Multilingual Language Model,” arXiv, arXiv:2211.05100v4, June 27, 2022.
- California Legislature, Safe and Secure Innovation for Frontier Artificial Intelligence Models Act, S.B. 1047, vetoed September 29, 2024.
- Chen, Bo, Xingyi Cheng, Pan Li, Yangli-ao Geng, Jing Gong, Shen Li, Zhilei Bei, Xu Tan, Boyan Wang, Xin Zeng, Chiming Liu, Aohan Zeng, Yuxiao Dong, Jie Tang, and Le Song, “xTrimoPGLM: Unified 100B-Scale Pre-Trained Transformer for Deciphering the Language of Protein,” arXiv, arXiv:2401:06199v2, December 9, 2024.
- Chen, Ke, Linbin Chen, Pedro Reviriego, and Fabrizio Lombardi, “Efficient Implementations of Reduced Precision Redundancy (RPR) Multiply and Accumulate (MAC),” *IEEE Transactions on Computers*, Vol. 68, No. 5, May 2019.
- Chen, Zixiang, Yihe Deng, Yue Wu, Quanquan Gu, and Yuanzhi Li, “Towards Understanding Mixture of Experts in Deep Learning,” arXiv, arXiv:2208.02813v1, August 4, 2022.
- Davenport, Tom, and Maryam Alavi, “How to Train Generative AI Using Your Company’s Data,” *Harvard Business Review*, July 6, 2023.
- de Vries, Alex, “The Growing Energy Footprint of Artificial Intelligence,” *Joule*, Vol. 7, No. 10, October 18, 2023.
- Defense Advanced Research Projects Agency, “Assured Neuro Symbolic Learning and Reasoning (ANSR),” webpage, undated. As of June 12, 2024: <https://www.darpa.mil/program/assured-neuro-symbolic-learning-and-reasoning>
- Douillard, Arthur, Qixuan Feng, Andrei A. Rusu, Adhiguna Kuncoro, Yani Donchev, Rachita Chhaparia, Ionel Gog, Marc’Aurelio Ranzato, Jiajun Shen, and Arthur Szlam, “DiPaCo: Distributed Path Composition,” arXiv, arXiv:2403.10616v1, March 15, 2024.

- Egan, Janet, and Lennart Heim, "Oversight for Frontier AI Through a Know-Your-Customer Scheme for Compute Providers," Centre for the Governance of AI, October 25, 2023.
- Epoch, "Parameter, Compute and Data Trends in Machine Learning," webpage, date unknown. As of January 29, 2024:  
<https://epochai.org/data/epochdb/visualization>
- Financial Crimes Enforcement Network, U.S. Department of the Treasury, homepage, undated. As of March 6, 2025:  
<https://fincen.gov>
- Garcez, Artur d'Avila, and Luis C. Lamb, "Neurosymbolic AI: The 3rd Wave," arXiv, arXiv:2012.05876v2, December 16, 2020.
- Hagemann, Tanja, and Katerina Katsarou, "A Systematic Review on Anomaly Detection for Cloud Computing Environments," *AICCC '20: Proceedings of the 2020 3rd Artificial Intelligence and Cloud Computing Conference*, Association for Computing Machinery, 2021.
- Hayes, Thomas, Roshan Rao, Halil Akin, Nicholas J. Sofroniew, Deniz Oktay, Zeming Lin, Robert Verkuil, Vincent Q. Tran, Jonathan Deaton, Marius Wiggert, Rohil Badkundri, Irhum Shafkat, Jun Gong, Alexander Derry, Raul S. Molina, Neil Thomas, Yousuf A. Khan, Chetan Mishra, Carolyn Kim, Liam J. Bartie, Matthew Nemeth, Patrick D. Hsu, Tom Sercu, Salvatore Candido, and Alexander Rives, "Simulating 500 Million Years of Evolution with a Language Model," *Science*, Vol. 387, No. 6736, January 16, 2025.
- Heim, Lennart, and Janet Egan, "Accessing Controlled AI Chips via Infrastructure-as-a-Service (IaaS): Implications for Export Controls," Centre for the Governance of AI, December 15, 2023.
- Hoffmann, Jordan, Sebastian Borgeaud, Arthur Mensch, Elena Buchatskaya, Trevor Cai, Eliza Rutherford, Diego de Las Casas, Lisa Anne Hendricks, Johannes Welbl, Aidan Clark, Tom Hennigan, Eric Noland, Katie Millican, George van den Driessche, Bogdan Damoc, Aurelia Guy, Simon Osindero, Karen Simonyan, Erich Elsen, Jack W. Rae, Oriol Vinyals, and Laurent Sifre, "Training Compute-Optimal Large Language Models," arXiv, arXiv:2203.15556v1, March 29, 2022.
- Hu, Edward J., Yelong Shen, Phillip Wallis, Zeyuan Allen-Zhu, Yuanzhi Li, Shean Wang, Lu Wang, and Weizhu Chen, "LoRA: Low-Rank Adaptation of Large Language Models," arXiv, arXiv:2106.09685v2, October 16, 2021.
- Huggingface, "BigScience Large Open-Science Open-Access Multilingual Language Model," webpage, undated. As of December 22, 2023:  
<https://huggingface.co/bigscience/bloom>

- Jia, Hengrui, Mohammad Yaghini, Christopher A. Choquette-Choo, Natalie Dullerud, Anvith Thudi, Varun Chandrasekaran, and Nicolas Papernot, "Proof-of-Learning: Definitions and Practice," *2021 IEEE Symposium on Security and Privacy (SP)*, 2021.
- Kaplan, Jared, Sam McCandlish, Tom Henighan, Tom B. Brown, Benjamin Chess, Rewon Child, Scott Gray, Alec Radford, Jeffrey Wu, and Dario Amodei, "Scaling Laws for Neural Language Models," arXiv, arXiv:2001.08361v1, January 23, 2020.
- Khan, Saif M., and Alexander Mann, "AI Chips: What They Are and Why They Matter," issue brief, Center for Security and Emerging Technology, April 2020.
- Li, Guanpeng, Siva Kumar Sastry Hari, Michael Sullivan, Timothy Tsai, Karthik Pattabiraman, Joel Emer, and Stephen W. Keckler, "Understanding Error Propagation in Deep Learning Neural Network (DNN) Accelerators and Applications," *SC17: International Conference for High Performance Computing, Networking, Storage and Analysis*, November 2017.
- Littlestone, Nick, "Learning Quickly When Irrelevant Attributes Abound: A New Linear-Threshold Algorithm," *Machine Learning*, Vol. 2, April 1988.
- Luccioni, Alexandra Sasha, Sylvain Viguer, and Anne-Laure Ligozat, "Estimating the Carbon Footprint of BLOOM, a 176B Parameter Language Model," *Journal of Machine Learning Research*, Vol. 24, 2023.
- Nawrocki, Piotr, and Wiktor Sus, "Anomaly Detection in the Context of Long-Term Cloud Resource Usage Planning," *Knowledge and Information Systems*, Vol. 64, 2022.
- Sevilla, Jaime, Lennart Heim, Anson Ho, Tamay Besiroglu, Marius Hobbhahn, and Pablo Villalobos, "Compute Trends Across Three Eras of Machine Learning," *2022 International Joint Conference on Neural Networks (IJCNN)*, 2022.
- Shallue, Christopher J., Jaehoon Lee, Joseph Antognini, Jascha Sohl-Dickstein, Roy Frostig, and George E. Dahl, "Measuring the Effects of Data Parallelism on Neural Network Training," *Journal of Machine Learning Research*, Vol. 20, No. 112, 2019.
- Shavit, Yonadav, "What Does It Take to Catch a Chinchilla? Verifying Rules on Large-Scale Neural Network Training via Compute Monitoring," arXiv, arxiv:2303.11341v2, May 30, 2023.
- Taylor, Ross, Marcin Kardas, Guillem Cucurull, Thomas Scialom, Anthony Hartshorn, Elvis Saravia, Andrew Poulton, Viktor Kerkez, and Robert Stojnic, "Galactica: A Large Language Model for Science," arXiv, arXiv:2211.09085v1, November 16, 2022.
- Trump, Donald J., "Executive Order 13984 of January 19, 2021: Taking Additional Steps to Address the National Emergency with Respect to Significant Malicious Cyber-Enabled Activities," *Federal Register*, Vol. 68, No. 14, January 25, 2021.

- Trump, Donald J., “Executive Order 14148 of January 28, 2025: Initial Rescissions of Harmful Executive Orders and Actions,” *Federal Register*, Vol. 90, No. 17, January 28, 2025.
- U.S. Department of the Treasury, “Financial Action Task Force (FATF),” webpage, undated. As of March 6, 2025:  
<https://home.treasury.gov/about/offices/terrorism-and-financial-intelligence/terrorist-financing-and-financial-crimes/financial-action-task-force-fatf>
- U.S. Energy Information Administration, U.S. Department of Energy, “How Much Electricity Does an American Home Use?” webpage, last updated October 20, 2023. As of January 4, 2024:  
<https://www.eia.gov/tools/faqs/faq.php?id=97&t=3>
- U.S. House of Representatives, AI Foundation Model Transparency Act of 2023, H.R. 6881, 118th Congress, referred to the U.S. House of Representatives Committee on Energy and Commerce, December 22, 2023.
- U.S. Senate, Federal Artificial Intelligence Risk Management Act of 2023, S.3205, 118th Congress, referred to the U.S. Senate Committee on Homeland Security and Governmental Affairs, November 2, 2023a.
- U.S. Senate, Eliminating Bias in Algorithmic Systems Act of 2023, S.3478, 118th Congress, referred to the U.S. Senate Committee on Homeland Security and Governmental Affairs, December 12, 2023b.
- Valiant, Leslie G, “A Bridging Model for Parallel Computation,” *Communications of the ACM*, Vol. 33, No. 8, August 1990.

## About the Authors --- ^about-the-authors

Alvin Moon is an associate mathematician at RAND. His current RAND research focuses on modeling and mathematical analysis in such topics as artificial intelligence, cryptography, supply chains, and workforce development. He has a Ph.D. in mathematics.

Padmaja Vedula is a senior information scientist at RAND, specializing in systems architecture, cybersecurity, cyber policy and deterrence, emerging technologies, and digital transformation. She has a master's degree in international public policy and master's degree in computer applications.

Jesse Geneson is a mathematician at RAND. His research papers have focused on graph theory, online reinforcement learning, mathematical neuroscience, and extremal combinatorics. He has a Ph.D. in applied mathematics.

Simon Bar-on is a Technical Analyst with background in computational mathematics. At RAND he has focused largely on modeling and simulation with applications in a wide variety of subject areas. He has a master's degree in applied mathematics.
