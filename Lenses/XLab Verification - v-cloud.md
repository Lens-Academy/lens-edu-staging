---
id: 'f78c8de0-f12f-446e-992b-a27c30dc3e84'
title: "2.2.1 Provider records and workload observables"
tldr: "Faithful alpha import of XLab lesson 2.2.1 Provider records and workload observables."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. Interactive elements marked as import gaps must be completed on XLab until Lens has an equivalent."
tags: [wip]
---
#### Text
content::
Cloud providers sit between AI developers and the machines they rent. Because
providers own, operate, meter, and bill for that compute, they can act as record
keepers, verifiers, enforcers, and securers. But cloud evidence is one witness,
not the whole court: self-hosted clusters, non-signatory jurisdictions, and
stolen weights all sit outside a provider's reach. In this module, you will
learn what cloud providers can observe, how those observations become evidence,
and where cloud oversight runs out.

\## Learning objectives

1. Identify the identity, resource-use, and operational records a cloud provider can observe, and explain what each record supports—and what it still does not establish.
2. Distinguish provider-controlled evidence from customer declarations, and assess the reliability of each when determining a workload's type, scale, and operator.
3. Analyze how customer identification, beneficial-ownership checks, reporting thresholds, ongoing monitoring, and access controls turn cloud records into a verification regime—and how an evader could route around them.
4. Assess where cloud oversight loses coverage, and identify which claims require corroboration from hardware, intelligence, or human verification mechanisms.

\## 2.2.1 Provider records and workload observables

The four readings in this submodule do different jobs. The first establishes what a provider can observe. The second adds customer identity and due diligence. The third shows how a threshold can be evaded. The fourth asks whether the resulting control is politically and administratively usable.

As you read, keep two columns:

1. **What record or signal exists?**
2. **What conclusion does it support—and what does it still not establish?**

Start by asking which claims a provider's ordinary records can support—and
which claims remain beyond those records.

\## Governing Through the Cloud: The Intermediary Role of Compute Providers in AI Regulation

*Source: XLab source material, [original](https://arxiv.org/abs/2403.08501)*

The executive-summary selections and complete sections below are reproduced under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Citations and cross-references link to the pinned arXiv version.

\### [Governing Through the Cloud](https://arxiv.org/abs/2403.08501)
*selected paragraphs from the Executive Summary*
Heim et al. (2024) | CC BY 4.0

**Governance Capacities —** We propose that compute providers can leverage their crucial role in the AI supply chain to secure infrastructure and serve as the intermediate node in support of regulatory objectives while maintaining customers’ privacy and rights. They can facilitate effective AI regulation via four key capacities: as securers, record keepers, verifiers, and, in some cases, even enforcers. Reporting represents a related yet distinct dimension, wherein compute providers provide information to authorities as mandated by law or regulations. (section 2)

**Technical Feasibility —** Our analysis indicates these governance capabilities are likely to be technically feasible and possible to implement in a confidentiality- and privacy-preserving way using techniques available to compute providers today. Compute providers often collect a wide range of data on their customers and workloads, for the purposes of billing, marketing, service analysis, optimization, and fulfilling legal obligations. Much of this data could also be used to support identity verification, as well as verifying technical properties of workloads. At a minimum, providers have access to billing information and can access basic technical data on how their hardware is used. This likely makes it possible for compute providers to develop techniques to detect and classify certain relevant workloads (e.g., whether a workload involves training a frontier model) and to quantify the amount of compute consumed by a workload. Verification of more detailed properties of a workload, such as the type of training data used, or whether a particular model evaluation was run, could be useful for governance purposes but is not currently possible without direct access to customer code and data. With further research and development efforts, compute providers may be able to offer “confidential computing” services to allow customers to prove these more detailed properties without otherwise revealing sensitive data. (section 3)

**Technical and Governance Challenges —** To realize a robust governance model, several technical and governance challenges remain. These include identifying additional measurable properties of AI development that correspond to potential threats, making workload classification methods robust to potential evasion, and formulating privacy-preserving verification protocols. (section 5.1)

The success of our proposed oversight scheme hinges on its multilateral adoption to prevent the migration of AI activities to jurisdictions with less stringent oversight. For an international framework to be durable and effective, it must address concerns from non-US governments. Cooperation will need to account for complex privacy and oversight issues associated with globally spread data centers. Compute provider oversight may affect competition in the AI ecosystem and raise concerns about issues of national competitiveness, and, consequently, this may influence the ability of US providers to offer products globally, including to foreign public-sector customers. Industry-led privacy-preserving standards could help ensure trust, but further research is needed to incentivize broad international buy-in to a global framework. (section 1.4 and section 5.2)

Read the following sections in full. In Appendix B, use Table 4 as a map from each observable to its current availability and the verification task it might support.

  
\### 3.2 Record Keeping
Record keeping is highly feasible using tools and metrics currently available to compute providers, who already collect a wide range of data on customers and service usage for:

- Accurately billing customers

- Marketing new services to customers

- Maintaining and optimizing service provision

- Detecting and responding to fraud, abuse, security risks, and technical issues

- Complying with legal obligations, such as financial record keeping

Compute providers also share these records with third parties for activities such as:

- Exchanging information with other companies for fraud prevention, detection, and credit risk reduction

- Providing third-party vendors with information for promotional and marketing purposes

- Complying with legal obligations, such as an enforceable government request

Compute providers typically have well-defined privacy policies around these records, including specific retention and security policies based on the sensitivity and business- or legal use cases for different kinds of records. Some of this data will likely be useful for verification activities relevant to frontier AI governance. The specific data attributes generally collected by compute providers can be found in [table 4](https://arxiv.org/abs/#ax-tab-4) below, mapped onto specific use cases for governance purposes. This information is based on conversations, public data collection, and privacy policies available from a representative sample of large and small compute providers [[26](https://arxiv.org/abs/#ax-ref-awsprivacynotice2024), [45](https://arxiv.org/abs/#ax-ref-coreweaveprivacypolicy2022), [73](https://arxiv.org/abs/#ax-ref-fluidstackfluidstackprivacynotice2022), [81](https://arxiv.org/abs/#ax-ref-googlecloudgooglecloudprivacy2024), [97](https://arxiv.org/abs/#ax-ref-lambdalambdaprivacypolicy2022), [104](https://arxiv.org/abs/#ax-ref-microsoftmicrosoftprivacystatement2024)].

  
\#### 3.3.2 Workload Classification
“Workload classification” describes a scenario where an infrastructure provider is attempting to classify a workload into a particular category. We will consider, from a frontier AI governance perspective, what these categories might be, and how they might be differentiated.
First, it is useful to know whether a workload relates broadly to AI. Frontier AI workloads will generally all use AI accelerators, but not all workloads that use AI accelerators will necessarily be AI workloads. For example, graphics and scientific computing workloads sometimes use AI accelerators. However, these workload categories can likely be differentiated using observable properties of the workload. Examples of such properties are outlined in [appendix B](https://arxiv.org/abs/#ax-sec-observable-data-attributes) in the Appendix. Within the broad category of AI workloads, there are several sub-categories of workload, corresponding to stages in the AI model’s life cycle, that are useful to differentiate from a governance perspective:

- Design, in which researchers and engineers experiment with different model designs, algorithms, and datasets.

- Training, in which a model learns from a large dataset. Typically known as “pre-training” to distinguish from enhancement.

- Enhancement, in which a trained model is further refined using a smaller data set (e.g., fine-tuning), sometimes using techniques such as reinforcement learning.

- Deployment in which a trained model is used in an operational setting, e.g., to make new predictions (“inference”).

   Figure 10: Simplified AI Lifecycle including training, enhancement (e.g., fine-tuning), and deployment (i.e., inference). (Figure from [[138](https://arxiv.org/abs/#ax-ref-sastrycomputingpowergovernance2024)].)

Each of these categories can be distinguished based on scale, among other attributes. Given the large scale of the frontier AI workloads we are interested in detecting and classifying, we can place a strong initial filter on which specific workloads warrant attention, ignoring the vast majority of workloads run on a compute provider’s infrastructure. As discussed by [[138](https://arxiv.org/abs/#ax-ref-sastrycomputingpowergovernance2024)], the training stage, where compute demands are especially high, is an especially practical stage to monitor.[18](https://arxiv.org/abs/#ax-fn-18)
The simplest method of workload classification might be based purely on the hardware configuration (in terms of types and numbers of devices) available to a customer. For example, in 2024, if a customer has requested a hardware configuration involving tens of thousands of AI accelerators, connected together using a high-bandwidth network fabric, it becomes much more likely they intend to engage in large-scale training, relative to other customers. Combining this information with the amount of time the hardware is being used can tell us whether it was possible for a customer to run a particular workload (e.g., pre-training above a particular scale), which could provide grounds for a more detailed investigation. These coarse methods are possible using data already available to compute providers for billing purposes. See [section 3.3.3](https://arxiv.org/abs/#ax-sec-compute-accounting) below for more information on these kinds of approaches.
More precise methods for frontier workload classification might involve manually defining some technical characteristics of relevant workloads, or training a machine learning classifier using cluster- and node-level technical information to predict whether a workload falls into a relevant category. Compute providers could also collect declarations from customers about the workloads they are running, and use that information as a reference point for classification. These approaches are based on the assumption that different kinds of workloads will have characteristic and learnable features. As an example, we expect frontier-scale training in 2024 will likely have several distinguishing features relative to other possible workloads. These could include the number of accelerators used (tens of thousands), the peak operation throughput utilization of accelerators over time (fairly constant), the patterns of communication between and within nodes (following specific patterns corresponding to different forms of parallelization), and limited outbound/inbound communication to external networks, such as the Internet, during the training run. According to six interviews with commercial compute providers, including both large and smaller providers, these kinds of cluster- and node-level characteristics are often already collected and used to understand customer workloads to optimize their services.[19](https://arxiv.org/abs/#ax-fn-19) Research released by Google, Microsoft, and Alibaba demonstrates some of the ways this technical information is collected and analyzed for business purposes [[90](https://arxiv.org/abs/#ax-ref-jeonanalysislargescalemultitenant2019), [155](https://arxiv.org/abs/#ax-ref-tirmaziborgnextgeneration2020), [168](https://arxiv.org/abs/#ax-ref-wengmlaaswildworkload2022)]. Some of this data has been released as public data sets that can be used to develop workload classification techniques [[7](https://arxiv.org/abs/#ax-ref-alibabaclustertrace2024), [76](https://arxiv.org/abs/#ax-ref-googleclusterdata2024)].
Workload classification techniques using these kinds of data have been studied in different contexts. [[148](https://arxiv.org/abs/#ax-ref-tangmitsupercloudworkload2022)] introduced the “MIT Supercloud Dataset,” containing node-level technical information for over 3,000 AI accelerator-based workloads. Workload classifiers trained on this data have reached 95%accuracy at distinguishing AI workloads across ten different model architectures [[167](https://arxiv.org/abs/#ax-ref-weissevaluationlowoverhead2022)]. Other research on workload classification for different kinds of high-performance computing workloads has reached similar levels of accuracy [[28](https://arxiv.org/abs/#ax-ref-banjongkanmultilabelclassificationhigh20), [149](https://arxiv.org/abs/#ax-ref-teraiworkloadclassificationperformance20)], including classifiers trained only to use data on power draw [[44](https://arxiv.org/abs/#ax-ref-coposcatchmeif2020), [96](https://arxiv.org/abs/#ax-ref-kohlerrecognizinghpcworkloads2021)].
However, there are several ways these findings may not be representative for frontier AI workload classification in a production environment. First, the authors mostly generated labeled data by running workloads themselves, which likely involved a level of standardization in software and datasets that would be unrealistic for real-world conditions. Second, this research typically involved a small number of different hardware configurations and scales, whereas these parameters will likely vary further in production contexts. Lastly, even a 5%error rate may be prohibitively high in production, given the potential consequences of reporting a false positive to a regulator.
Compute providers offering large-scale AI clusters are likely to have the expertise to address these technical challenges. In doing so, we recommend that compute providers—in collaborative efforts where possible—consider a range of technical approaches for classification, ranging from simple manually defined thresholds through to machine-learning based classifiers. These methods could also be combined with other useful data and processes, such as by soliciting customer declarations on the intended use/purpose of a hardware configuration or workload, and by conducting follow-up investigations in cases where classification confidence is low. box1Box 1 demonstrates what a workload classification process combining these elements might look like.
[breakable,boxrule=1pt,enhanced jigsaw, sharp corners,pad at break*=1mm,colbacktitle=lightgray,colback=lightgray,colframe=black,coltitle=black,toptitle=1mm,bottomtitle=1mm,width=,fonttitle=,parbox=false,title=Box 1: An example process for frontier AI workload classification. ,phantom=box1]
- The compute provider lists the specific set of hardware configurations and scales they offer that are sufficient for efficient training of frontier AI workloads (i.e., within defined cost/time boundaries). Given that compute providers tend to specialize in particular hardware configurations (e.g., AI accelerator types and node configurations), this number could be quite small.

- The compute provider collects labeled cluster- and node-level data on workloads simulated or run on each of these configurations. Compute providers offering similar hardware configurations may benefit from coordinating to produce larger datasets.

- The compute provider creates technical thresholds to define relevant workload categories based on their identifying characteristics, and tests them on the collected data. This could include training ML-based workload classifiers. It may be the case that a single classification approach works well for a range of different hardware configurations and/or scales, or that more specific classifiers are required for different configurations.

- In operation, for any customer seeking access to or already using a relevant hardware configuration, the compute provider could then:

- Ensure they have performed adequate identity verification.

- Collect declarations from the customer on the intended use of the hardware configuration, and/or declarations on the nature of any sufficiently large workload run on that configuration.

- Validate these declarations by running automated classification on workloads that use that configuration, and conduct follow-up analyses where useful, especially in cases where classification confidence is low.

The difficulty of classifying workloads increases if a compute customer is actively trying to disguise the nature of their workload. This kind of obfuscation may become likely in cases where a customer has a strong financial, criminal, or political incentive to avoid regulatory oversight. Such incentives are likely to grow when frontier AI models become both more attractive for criminal activities and more economically lucrative. Analogous practices can be observed in the finance sector, where illicit actors have engaged in “structuring” (breaking up a single transaction into several smaller transactions) to avoid automated transaction reporting from their bank to the regulator [[99](https://arxiv.org/abs/#ax-ref-linnredefiningbanksecrecy2010)]. We discuss and list these challenges in [section 5.1](https://arxiv.org/abs/#ax-sec-technical-challenges).

  
\#### 3.3.3 Compute Accounting
We introduce “compute accounting”: measurements and techniques to produce an estimation of the amount of compute consumed by a customer running one or more workloads on a specific compute cluster. These techniques are comparatively similar to the previous section on workload classification ([section 3.3.2](https://arxiv.org/abs/#ax-sec-workload-classification)). However, rather than establishing the class of a workload, compute accounting aims to determine its magnitude. Moreover, compute accounting is useful even when the workload is not classified at all, as an estimate of the total amount of compute used by a given customer is an upper bound for a single (unknown) workload. From a practical governance perspective, compute accounting could be used as an input to workload classification, and/or as a standalone metric to determine whether a particular workload has exceeded a compute-based reporting threshold.
The amount of compute used by a given workload is a useful metric from a governance perspective. In the context of AI training, novel capabilities (and related risks) are likely to first emerge in models that require large amounts of compute [[132](https://arxiv.org/abs/#ax-ref-pilzincreasedcomputeefficiency2024), [141](https://arxiv.org/abs/#ax-ref-sevillacomputetrendsthree2022)]. In the context of AI inference, compute is correlated with the scale and processing speed of the deployment: how many copies of the model are being run, and how fast the model is operating (the throughput, e.g., tokens per second for LLMs). Insofar as the model is capable enough to potentially cause harm, these factors could then be correlated with risk and the need for enhanced oversight (Appendix I of [[122](https://arxiv.org/abs/#ax-ref-obriendeploymentcorrectionsincident2023)]).
More formally, the total computing power of a rented cluster and how long a customer has access to it results in a quantity of available compute—a “compute budget.” The customer is then choosing how to allocate that budget across different workloads. For example, a given set of AI accelerators could be used for a single training run, multiple small training runs, or model deployment ([figure 11](https://arxiv.org/abs/#ax-fig-11)). In cases where compute is being consumed by a customer (as opposed to hardware sitting idle), the amount of compute consumed can be attributed to at least one workload. The addition of workload classification allows fractions of that usage to be ascribed to workloads of particular types.
   Figure 11: Three example scenarios of a set of AI accelerator nodes running different workloads over time. Compute accounting establishes the amount of compute used over time, while workload classification can differentiate between these three scenarios by mapping compute usage to specific workloads.

We can estimate the compute budget via two different approaches:

- Theoretical compute budget estimation: calculated using the assumed throughput (measured in OP/s) of the hardware potentially involved in the workload, and multiplying it by the time the hardware is being used.

- Empirical compute budget estimation: calculated using actual measurements from the hardware that can serve as more direct proxies for compute consumption. For example, aggregating AI accelerator core utilization and time-in-use data across all AI accelerators involved in a workload, and multiplying by the peak capacity of each core.

Theoretical compute is a derivative of empirical compute, useful for establishing an estimate in circumstances where empirical measurements are not available. As exact circumstances and configurations differ between compute providers, not all attributes of both theoretical and empirical compute are likely to be observable. However, in practice, both kinds could be used to inform an overall estimate of compute usage for a particular instance of running a workload ([figure 12](https://arxiv.org/abs/#ax-fig-12)).
   Figure 12: A spectrum of possible compute usage metrics for AI workload analysis, from low-level measurements, such as on-chip calculations, to more high-level measurements, such as the hardware available to a customer. Each of these metrics can be synergistically combined to enhance the accuracy and sensitivity of workload classification and compute accounting.

Regardless of whether the approach is theoretical or empirical, it will be important for compute providers to estimate both throughput (OP/s) and total quantity of operations (OP). This provides crucial information to detect cases where a customer is evading a reportable compute threshold by utilizing multiple compute providers or accounts to sequentially perform partial training of a model. In this case, the throughput available to the customer is necessary to identify that a rate of compute usage corresponding to a reportable threshold has been reached, even if the reportable threshold itself has not. We discuss this in [5.1](https://arxiv.org/abs/#ax-sec-technical-challenges).
Measuring Theoretical Compute Budget — Theoretical approaches measure the potential for a certain amount of compute to be used for one or more workloads within a given time frame. This is easier to measure than empirical compute, and in the simplest form is equivalent to hardware resources a customer has been allocated to access within the cluster. For any given compute provider, the number of customers with access to sufficient theoretical compute to train a frontier model will be small.[20](https://arxiv.org/abs/#ax-fn-20) This makes theoretical compute a useful measure for determining which specific customers are relevant for a frontier AI regulatory regime. This can be calculated using data already available to compute providers for billing purposes ([table 4](https://arxiv.org/abs/#ax-tab-4)). Relevant data for measurement of compute are:

- Node assignment: Compute providers can bill customers for on-demand nodes (a full or partial node) at a granularity ranging from seconds to hours [[24](https://arxiv.org/abs/#ax-ref-awsamazonec2ondemand)], or reserved nodes ranging from days to months [[25](https://arxiv.org/abs/#ax-ref-awsamazonec2reserved)]. Theoretically, the used compute budget can be calculated using this information by summing the theoretical peak performance of the AI accelerators in each node, multiplying it by the time the node is available to the customer, and the assumed average utilization of the AI accelerators.[21](https://arxiv.org/abs/#ax-fn-21)

- Data ingress/egress: Data into and out of the cluster is metered and sometimes billed [[79](https://arxiv.org/abs/#ax-ref-googlecloud), [107](https://arxiv.org/abs/#ax-ref-microsoftazure), [129](https://arxiv.org/abs/#ax-ref-pal2021)]. The communication of nodes within the cluster to endpoints outside the cluster, as well as the amount of data transferred and time when communication occurs, can inform whether nodes outside the cluster participated in a training run or deployment.

The exact procedures to allocate, measure, and invoice customer usage for billing purposes are not publicly available for any major provider. However, every provider must have internal control systems and diagnostics to record this information accurately, as well as status reporting and other telemetry to maintain the health of their clusters (such as the state of individual machines and network switches). While billing information provides a widely-measured baseline for customer compute usage, intra-cluster network information such as the network topology can provide greater detail. Specifically, knowledge of whether two nodes are capable of communicating within a cluster informs whether they may participate in running the same parallel workload.
Theoretical compute, while relatively simple to calculate in most cases, is useful primarily to establish an upper limit on the total compute budget of a customer. To map compute usage onto a particular workload requires additional information at the cluster or node level, as previously covered in [section 3.3.2](https://arxiv.org/abs/#ax-sec-workload-classification).
Measuring empirical compute budget — Measurements of empirical compute usage involve observations of a cluster’s hardware-level characteristics, often measurements of the node itself (perhaps from a hypervisor or other privileged software) or inter-node communication fabric. Empirical compute, in contrast to theoretical, can provide a highly precise and accurate accounting of the amount of compute, though some limitations exist. We consider that two categories of measuring empirical compute exist: operations and data transfer. Operations refers to the mathematical calculations performed as part of a workload (most frequently multiplication and addition for contemporary AI workloads). Data transfer refers to the movement of the data necessary to perform those calculations: network links from node-to-node, or chip-to-chip within a node or loaded from an AI accelerator’s memory.
While these properties are essentially metadata, compute providers would need to detail collection and observation of this within their terms of service with very clear guidelines about how the data will be collected, stored, and used. While strict internal policies are necessary to ensure the integrity of such metadata, this kind of usage policy would likely not require any significant deviation from existing policies for sensitive customer data handling, or deviation from the kinds of data that are already often collected [[26](https://arxiv.org/abs/#ax-ref-awsprivacynotice2024), [45](https://arxiv.org/abs/#ax-ref-coreweaveprivacypolicy2022), [73](https://arxiv.org/abs/#ax-ref-fluidstackfluidstackprivacynotice2022), [81](https://arxiv.org/abs/#ax-ref-googlecloudgooglecloudprivacy2024), [97](https://arxiv.org/abs/#ax-ref-lambdalambdaprivacypolicy2022), [104](https://arxiv.org/abs/#ax-ref-microsoftmicrosoftprivacystatement2024)].
Within a given node, opportunities to measure empirical compute include:

- Operations performed on AI accelerators: Individual chips contain performance counters to measure information such as the number of instructions executed [[171](https://arxiv.org/abs/#ax-ref-enwiki-1169157291)]. A vendor tool may be required to access this information [[120](https://arxiv.org/abs/#ax-ref-nvidianvidiansightperf)].

- Data flow to/from AI accelerator’s memory: The rate at which data is written to or read from the AI accelerator’s memory can be observed over time, allowing measurement of throughput and quantity, and can inform an estimation of the total number of operations performed [[115](https://arxiv.org/abs/#ax-ref-nationalenergyresearchscientificcomputin), [172](https://arxiv.org/abs/#ax-ref-williams2008)].

- Data traffic between accelerators and other nodes: Node-to-node and chip-to-chip communication is an indicator of participating in the same workload, even if the workload itself cannot be classified [[101](https://arxiv.org/abs/#ax-ref-merritt2023), [119](https://arxiv.org/abs/#ax-ref-nvidia), [144](https://arxiv.org/abs/#ax-ref-shoeybi2020)].

Even without privileged software access to the node, other measurements of cluster operations are useful to inform an estimate of empirical compute:

- Power consumption: In cases where precise chip utilization is not observable, measurements of power consumption (of a node or individual AI accelerators within a node) can help inform an estimate. The amount of power consumed by each node is considerably higher when a node (or even an individual AI accelerator [[121](https://arxiv.org/abs/#ax-ref-zotero-3386)]) executes a workload compared to idle. However, power consumption does not simply scale linearly with performance [[130](https://arxiv.org/abs/#ax-ref-patelpolcapoweroversubscription2023)], though specific calibration for a device may enable improved estimation. Power consumption will typically be a way of measuring both operations and data transfer, as both these activities consume energy within a node.

- Data traffic between nodes: Granular information such as the number of data sent to and from the node, the source and destination of this data, and the timing with which they are sent can inform how multiple nodes are cooperatively executing the same workload.

While many of these measurements alone provide limited insight, combining measurements can provide more insight into the compute usage of a particular workload ([figure 12](https://arxiv.org/abs/#ax-fig-12)). Empirical measurements form an upper bound for compute usage, as not every operation can be known to have contributed to a workload.

  
\#### 3.3.4 Detailed Workload Verification
To verify compliance with regulations on the development or deployment of frontier AI systems, it may be useful for a compute provider to validate more fine-grained features of a workload, such as whether a particular training dataset was used, the model architecture, or whether a particular model evaluation was run. We call such activities “detailed workload verification.” This form of verification differs from workload classification in that it will almost always require knowing certain properties of the code and/or data used by the customer.
One undesirable form of workload verification would simply require compute providers to have direct access to customer code and data. However, this level of access is not acceptable, as compute providers will not access customer data without permission unless required to maintain the health of their cluster or legally compelled (see [[21](https://arxiv.org/abs/#ax-ref-awsawscustomeragreement2024)], and other terms of services from compute providers). Internal risk management processes, such as auditing access to customer data by employees, typically govern details such as when access occurred, by whom, and whether it was authorized.
However, using privacy-preserving technologies built into data center hardware, it may become possible for a compute provider, in collaboration with a customer, to verify particular properties of a workload without observing any other information—only the required verification result needs to be shared [[1](https://arxiv.org/abs/#ax-ref-aarnesecuregovernablechips2024)]. As one example, many modern CPUs and AI accelerators, such as NVIDIA’s H100, and data center CPUs from AMD and Intel, come equipped with a “trusted execution environment” (TEE), allowing the AI accelerator/CPU’s customer to assert the confidentiality and integrity of code/data, while exposing only the code/data they choose to, and having full control over who they expose it to ([figure 13](https://arxiv.org/abs/#ax-fig-13)). Techniques that leverage a TEE in this way are often known as “confidential computing.” Compute providers are increasingly making these features available to customers [[23](https://arxiv.org/abs/#ax-ref-awsawsnitroenclaves), [105](https://arxiv.org/abs/#ax-ref-microsoftlearnconfidentialcomputingazure), [103](https://arxiv.org/abs/#ax-ref-microsoftlearnwhatconfidentialcomputing2)].
   Figure 13: Using confidential computing techniques allows an “attester” (customer) to share high-level information about a workload with a “verifier” (e.g., a compute provider or a regulator) such that the verifier can trust the information, without the attester sharing any additional code or data. (Adapted from [[1](https://arxiv.org/abs/#ax-ref-aarnesecuregovernablechips2024)].)

Using confidential computing techniques, customers may be able to provably verify particular governance-relevant properties of their workloads to their compute provider or directly to a regulator. For example, a customer may wish to demonstrate that they ran a particular model evaluation, obtained a particular result on a model evaluation, or did (not) use a particular dataset during training. However, these techniques have yet to be fully validated and implemented in production contexts. Several organizations are actively researching and developing software for using confidential computing to allow privacy-preserving auditing of models [[111](https://arxiv.org/abs/#ax-ref-mithrilsecurityblindai2024), [126](https://arxiv.org/abs/#ax-ref-howauditai2023), [127](https://arxiv.org/abs/#ax-ref-openminedpysyft2024)]. There has also been some work on expanding these techniques to allow privacy-preserving auditing of training workloads (e.g., the dataset used, or quantity of compute consumed), though this area is less well-explored [[38](https://arxiv.org/abs/#ax-ref-choitoolsverifyingneural2023), [110](https://arxiv.org/abs/#ax-ref-mithrilsecurityaicert2024)].[22](https://arxiv.org/abs/#ax-fn-22) If regulatory requirements on compute providers end up requiring them to validate more fine-grained properties of workloads, these kinds of methods could be used to achieve this in a way that preserves customer confidentiality and privacy. In the meanwhile, we encourage compute providers and developers to explore and develop these techniques to ensure they can be implemented without meaningful performance penalties, and while preserving other aspects of customer experience and confidentiality.

  
\## B Observable Data Attributes
1whitelightgray
 |
 |     | Visible attribute
  |   | Uses
  |   | Involves collection of data not already widely collected?
  |   | Ease of implementation
 |   | Ease of circumvention

 |     5c  – Continued from previous page.
 |    | Visible attribute
  |   | Uses
  |   | Involves collection of data not already widely collected?
  |   | Ease of implementation
 |   | Ease of circumvention

 |
 5r{Continued on next page.}
 |

Hardware configuration requested by the customer  |   | Workload classification.
 |  The quantity of AI accelerators requested and networking setup are strongly suggestive of the workloads a customer intends to run.
  |  No, already collected.  |  Already collected by compute providers to set up and provision infrastructure.  |  Highly difficult or impossible.
 |   | Number of hours that resources (e.g., AI accelerators) are in use
  |   | Workload classification, compute accounting.
 |  Allows high-level boundary setting on workload type/size.
  |  No, already collected.  |  Already collected by compute providers for billing purposes.  |  Highly difficult or impossible.
 |  Power draw  |   | Workload classification, compute accounting.
 |  Allows high-level boundary setting on workload type/size, as increased power draw corresponds to increased throughput for a particular device. Power consumption over time may allow differentiation of inference from training [[130](https://arxiv.org/abs/#ax-ref-patelpolcapoweroversubscription2023)].
  |  No, already collected.  |  Possible to collect using existing tooling. Already collected by some compute providers.  |  Possible, but would involve substantial cost efficiency penalties.
 |  Network bandwidth between AI accelerator servers  |   | Workload classification, compute accounting.
 |  Large AI training workloads require high bandwidth between servers. Different communication patterns correspond to different kinds of workloads, and bandwidth utilization is related to the quantity of computation performed on each server.
  |  No, already collected.  |  Possible to collect using existing tooling. Already collected by some compute providers.  |  Possible, but could involve substantial cost efficiency penalties.
 |  Network bandwidth within AI accelerator servers  |   | Workload classification, compute accounting.
 |  Different bandwidth patterns correspond to different kinds of workloads, and bandwidth utilization is related to the quantity of computation performed within each server.
  |  No, already collected.  |  Possible to collect using existing tooling. Already collected by some compute providers.  |  Possible, but could involve substantial cost efficiency penalties.
 |  AI accelerator core &memory bandwidth utilization  |   | Workload classification, compute accounting.
 |  Large AI workloads typically have high memory bandwidth utilization, and core utilization will tend to be constant for training, while inference is typically variable.
  |  No, already collected.  |  Possible to collect using existing tooling. Difficult to collect for bare-metal services.  |  Possible, but could involve substantial cost efficiency penalties.
 |  Performance counters by numerical precision  |   | Workload classification, compute accounting.
 |  Lower precision is common in AI workloads and allows differentiation from most scientific computing workloads and possibly gaming. Counters also provide a direct measurement of operations consumed by a workload.
  |  Potentially. This degree of telemetry on an individual customer is unusual. Policies for collection and analysis would need to be clearly outlined in provider’s terms of service.  |  Possible to collect using existing tooling. Difficult to collect for bare metal services.  |  Possible, but could involve moderate cost efficiency penalties.
 |  Modification of weights in memory  |   | Workload classification, compute accounting.
 |  Model training requires changing the weights in memory using a backward pass. Typically the only large data structures in memory are the weights and activations, so it should be possible to observe whether stores are made to that region of memory. The magnitude and frequency of memory updates are related to the quantity of compute consumed.
  |  Potentially  |  Not currently possible.  |  Difficult: training requires modifying weights in memory to be highly performant.
 |  Workload hyperparameters  |  Workload classification, compute accounting, detailed workload verification.  |  Yes. Can potentially be made privacy-preserving using confidential computing techniques.  |  Possible to collect with customer consent.  |  Unclear (highly dependent on implementation).
 |  Training dataset  |  Workload classification, compute accounting, detailed workload verification.  |  Yes. Can potentially be made privacy-preserving using confidential computing techniques.  |  Possible to collect with customer consent.  |  Unclear (highly dependent on implementation).
Table: An overview of observable data attributes.

UTF8gbsn

\## References

-  Aarne, O., Fist, T., and Withers, C.  Secure, Governable Chips.  Technical report, Center for a New American Security, January 2024.  URL [https://www.cnas.org/publications/reports/secure-governable-chips](https://arxiv.orghttps://www.cnas.org/publications/reports/secure-governable-chips).
 [↩](https://arxiv.org/abs/#ax-cite-aarnesecuregovernablechips2024)

-  Abbott, K. W., Levi-Faur, D., and Snidal, D. (eds.).  Regulatory intermediaries in the age of governance, volume 670 of The Annals of the American Academy of Political and Social Science.  SAGE, March 2017a.  ISBN 978-1-5063-9011-6.  URL [https://www.jstor.org/stable/i26361533](https://arxiv.orghttps://www.jstor.org/stable/i26361533).
 [↩](https://arxiv.org/abs/#ax-cite-abbottregulatoryintermediariesage2017)

-  Abbott, K. W., Levi-faur, D., and Snidal, D.  Theorizing Regulatory Intermediaries: The RIT Model.  The ANNALS of the American Academy of Political and Social Science, 6700 (1):0 14–35, March 2017b.  ISSN 0002-7162, 1552-3349.  [10.1177/0002716216688272](https://arxiv.orghttps://doi.org/10.1177/0002716216688272).  URL [http://journals.sagepub.com/doi/10.1177/0002716216688272](https://arxiv.orghttp://journals.sagepub.com/doi/10.1177/0002716216688272).

-  Advani, A., Elming, W., and Shaw, J.  The Dynamic Effects of Tax Audits.  The Review of Economics and Statistics, 1050 (3):0 545–561, May 2023.  ISSN 0034-6535.  [10.1162/rest_a_01101](https://arxiv.orghttps://doi.org/10.1162/rest_a_01101).  URL [https://doi.org/10.1162/rest_a_01101](https://arxiv.orghttps://doi.org/10.1162/rest_a_01101).
 [↩](https://arxiv.org/abs/#ax-cite-advani2023)

-  Ahmed, N. and Wahed, M.  The De-democratization of AI: Deep Learning and the Compute Divide in Artificial Intelligence Research, October 2020.  URL [http://arxiv.org/abs/2010.15581](https://arxiv.orghttp://arxiv.org/abs/2010.15581).  arXiv:2010.15581 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-ahmeddedemocratizationaideep2020)

-  Alderman, L.  Ireland’s Days as a Tax Haven May Be Ending, but Not Without a Fight.  The New York Times, July 2021.  ISSN 0362-4331.  URL [https://www.nytimes.com/2021/07/08/business/ireland-minimum-corporate-tax.html](https://arxiv.orghttps://www.nytimes.com/2021/07/08/business/ireland-minimum-corporate-tax.html).
 [↩](https://arxiv.org/abs/#ax-cite-aldermanirelanddaystax2021)

-  Alibaba.  Alibaba Cluster Trace Program, March 2024.  URL [https://github.com/alibaba/clusterdata](https://arxiv.orghttps://github.com/alibaba/clusterdata).  original-date: 2017-09-05T03:16:34Z.
 [↩](https://arxiv.org/abs/#ax-cite-alibabaclustertrace2024)

-  Allen, G. C.  Choking off China’s Access to the Future of AI.  Technical report, Center for Strategic and International Studies, October 2022.  URL [https://www.csis.org/analysis/choking-chinas-access-future-ai](https://arxiv.orghttps://www.csis.org/analysis/choking-chinas-access-future-ai).
 [↩](https://arxiv.org/abs/#ax-cite-allen2022)

-  Allen, G. C., Benson, E., and Putnam, M.  Japan and the Netherlands Announce Plans for New Export Controls on Semiconductor Equipment.  Commentary, Center for Strategic and International Studies, April 2023.  URL [https://www.csis.org/analysis/japan-and-netherlands-announce-plans-new-export-controls-semiconductor-equipment](https://arxiv.orghttps://www.csis.org/analysis/japan-and-netherlands-announce-plans-new-export-controls-semiconductor-equipment).
 [↩](https://arxiv.org/abs/#ax-cite-allenjapannetherlandsannounce2023)

-  Amazon.com, Inc.  An update on Amazon’s efforts to combat child sexual abuse material, April 2023a.  URL [https://www.aboutamazon.com/news/policy-news-views/amazon-csam-transparency-report-2022](https://arxiv.orghttps://www.aboutamazon.com/news/policy-news-views/amazon-csam-transparency-report-2022).  Section: Policy news &views.
 [↩](https://arxiv.org/abs/#ax-cite-amazon-cominc-2023)

-  Amazon.com, Inc.  Amazon and Anthropic Announce Strategic Collaboration to Advance Generative AI, September 2023b.  URL [https://press.aboutamazon.com/2023/9/amazon-and-anthropic-announce-strategic-collaboration-to-advance-generative-ai](https://arxiv.orghttps://press.aboutamazon.com/2023/9/amazon-and-anthropic-announce-strategic-collaboration-to-advance-generative-ai).
 [↩](https://arxiv.org/abs/#ax-cite-amazon-cominc-amazonanthropicannounce202)

-  Amazon.com, Inc.  Sustainability Amazon, 2024.  URL [https://sustainability.aboutamazon.com/products-services/the-cloud](https://arxiv.orghttps://sustainability.aboutamazon.com/products-services/the-cloud).
 [↩](https://arxiv.org/abs/#ax-cite-amazon-cominc-cloud)

-  AMD.  AMD Regulatory Trade Compliance, 2024.  URL [https://www.amd.com/en/legal/compliance/trade-compliance.html](https://arxiv.orghttps://www.amd.com/en/legal/compliance/trade-compliance.html).
 [↩](https://arxiv.org/abs/#ax-cite-amd)

-  Anderljung, M., Barnhart, J., Korinek, A., Leung, J., O’Keefe, C., Whittlestone, J., Avin, S., Brundage, M., Bullock, J., Cass-Beggs, D., Chang, B., Collins, T., Fist, T., Hadfield, G., Hayes, A., Ho, L., Hooker, S., Horvitz, E., Kolt, N., Schuett, J., Shavit, Y., Siddarth, D., Trager, R., and Wolf, K.  Frontier AI Regulation: Managing Emerging Risks to Public Safety, November 2023a.  URL [http://arxiv.org/abs/2307.03718](https://arxiv.orghttp://arxiv.org/abs/2307.03718).  arXiv:2307.03718 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-anderljungfrontierairegulation2023)

-  Anderljung, M., Smith, E. T., O’Brien, J., Soder, L., Bucknall, B., Bluemke, E., Schuett, J., Trager, R., Strahm, L., and Chowdhury, R.  Towards Publicly Accountable Frontier LLMs: Building an External Scrutiny Ecosystem under the ASPIRE Framework.  Technical report, Centre for the Governance of AI, November 2023b.  URL [https://www.governance.ai/research-paper/towards-publicly-accountable-frontier-llms](https://arxiv.orghttps://www.governance.ai/research-paper/towards-publicly-accountable-frontier-llms).  arXiv:2311.14711 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-anderljung2023)

-  Anthropic.  Anthropic Partners with Google Cloud, February 2023.  URL [https://www.anthropic.com/news/anthropic-partners-with-google-cloud](https://arxiv.orghttps://www.anthropic.com/news/anthropic-partners-with-google-cloud).

-  Australian Attorney-General’s Department.  Data Retention: Guideline for Service Providers.  Technical report, Australian Government, July 2015.  URL [https://www.homeaffairs.gov.au/nat-security/files/data-retention-guidelines-service-providers.pdf](https://arxiv.orghttps://www.homeaffairs.gov.au/nat-security/files/data-retention-guidelines-service-providers.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-australianattorney-generalsdepartmentdat)

-  Australian DITRDCA.  International Air Services Information Memorandum, January 2024.  URL [https://www.infrastructure.gov.au/infrastructure-transport-vehicles/aviation/international-aviation/air-services-agreements-arrangements/international-air-services-information-memorandum](https://arxiv.orghttps://www.infrastructure.gov.au/infrastructure-transport-vehicles/aviation/international-aviation/air-services-agreements-arrangements/international-air-services-information-memorandum).  Last Modified: 2024-01-18 Publisher: Department of Infrastructure, Transport, Regional Development, Communications and the Arts.
 [↩](https://arxiv.org/abs/#ax-cite-transportdepartmentofinfrastructure2024)

-  Aviation Transport Security Act.  Aviation Transport Security Regulations, 2005.  URL [https://www8.austlii.edu.au/cgi-bin/viewdb/au/legis/cth/consol_reg/atsr2005457/](https://arxiv.orghttps://www8.austlii.edu.au/cgi-bin/viewdb/au/legis/cth/consol_reg/atsr2005457/).

-  AWS.  General Data Protection Regulation (GDPR) Center, 2024a.  URL [https://aws.amazon.com/compliance/gdpr-center/](https://arxiv.orghttps://aws.amazon.com/compliance/gdpr-center/).
 [↩](https://arxiv.org/abs/#ax-cite-aws)

-  AWS.  AWS Customer Agreement, 2024b.  URL [{](https://arxiv.org{)https://aws.amazon.com/agreement/#: :text=You
 [↩](https://arxiv.org/abs/#ax-cite-awsawscustomeragreement2024)

-  AWS.  AWS Global Infrastructure, 2024c.  URL [https://aws.amazon.com/about-aws/global-infrastructure/](https://arxiv.orghttps://aws.amazon.com/about-aws/global-infrastructure/).
 [↩](https://arxiv.org/abs/#ax-cite-awsawsglobalinfrastructure)

-  AWS.  AWS Nitro Enclaves, 2024d.  URL [https://aws.amazon.com/ec2/nitro/nitro-enclaves/](https://arxiv.orghttps://aws.amazon.com/ec2/nitro/nitro-enclaves/).
 [↩](https://arxiv.org/abs/#ax-cite-awsawsnitroenclaves)

-  AWS.  Amazon EC2 On-Demand Pricing, 2024e.  URL [https://aws.amazon.com/ec2/pricing/on-demand/](https://arxiv.orghttps://aws.amazon.com/ec2/pricing/on-demand/).
 [↩](https://arxiv.org/abs/#ax-cite-awsamazonec2ondemand)

-  AWS.  Amazon EC2 Reserved Instances, 2024f.  URL [https://aws.amazon.com/ec2/pricing/reserved-instances/](https://arxiv.orghttps://aws.amazon.com/ec2/pricing/reserved-instances/).
 [↩](https://arxiv.org/abs/#ax-cite-awsamazonec2reserved)

-  AWS.  AWS Privacy Notice, 2024g.  URL [https://aws.amazon.com/privacy/](https://arxiv.orghttps://aws.amazon.com/privacy/).
 [↩](https://arxiv.org/abs/#ax-cite-awsprivacynotice2024)

-  AWS.  Security of the AWS Infrastructure, 2024h.  URL [https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/security-of-the-aws-infrastructure.html](https://arxiv.orghttps://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/security-of-the-aws-infrastructure.html).

-  Banjongkan, A., Pongsena, W., Chanklan, R., Kerdprasop, N., and Kerdprasop, K.  Multi-label classification of high performance computing workload with variable transformation.  International Journal of Machine Learning and Computing, 8:0 536–541, December 2018.  [10.18178/ijmlc.2018.8.6.742](https://arxiv.orghttps://doi.org/10.18178/ijmlc.2018.8.6.742).  URL [https://www.ijmlc.org/vol8/742-ML0023.pdf](https://arxiv.orghttps://www.ijmlc.org/vol8/742-ML0023.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-banjongkanmultilabelclassificationhigh20)

-  BBC.  EU-US Privacy Shield for data struck down by court.  BBC News, July 2020.  URL [https://www.bbc.com/news/technology-53418898](https://arxiv.orghttps://www.bbc.com/news/technology-53418898).
 [↩](https://arxiv.org/abs/#ax-cite-euusprivacyshield2020)

-  Belfield, H. and Hua, S.-S.  Compute and Antitrust: Regulatory implications of the AI hardware supply chain, from chip design to cloud APIs.  Verfassungsblog, August 2022.  URL [https://verfassungsblog.de/compute-and-antitrust/](https://arxiv.orghttps://verfassungsblog.de/compute-and-antitrust/).
 [↩](https://arxiv.org/abs/#ax-cite-belfield2022)

-  Besiroglu, T., Bergerson, S. A., Michael, A., Heim, L., Luo, X., and Thompson, N.  The Compute Divide in Machine Learning: A Threat to Academic Contribution and Scrutiny?, January 2024.  URL [http://arxiv.org/abs/2401.02452](https://arxiv.orghttp://arxiv.org/abs/2401.02452).  arXiv:2401.02452 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-besiroglu2024)

-  Biden, J. R.  S.1738 - 110th Congress (2007-2008): PROTECT Our Children Act of 2008, October 2008.  URL [https://www.congress.gov/bill/110th-congress/senate-bill/1738](https://arxiv.orghttps://www.congress.gov/bill/110th-congress/senate-bill/1738).  Archive Location: 2007-06-28.

-  Boyle, A. and Lau, T.  The President’s Extraordinary Sanctions Powers, July 2021.  URL [https://www.brennancenter.org/our-work/research-reports/presidents-extraordinary-sanctions-powers](https://arxiv.orghttps://www.brennancenter.org/our-work/research-reports/presidents-extraordinary-sanctions-powers).
 [↩](https://arxiv.org/abs/#ax-cite-boylepresidentextraordinarysanctions2021)

-  Buttarelli, G.  The EU-U.S. Privacy Shield two years on, March 2018.  URL [https://www.edps.europa.eu/press-publications/press-news/blog/eu-us-privacy-shield-two-years](https://arxiv.orghttps://www.edps.europa.eu/press-publications/press-news/blog/eu-us-privacy-shield-two-years).
 [↩](https://arxiv.org/abs/#ax-cite-buttarelli2018)

-  California Energy Commission.  Power Plant Licensing, 2024.  URL [https://www.energy.ca.gov/programs-and-topics/topics/power-plants/power-plant-licensing](https://arxiv.orghttps://www.energy.ca.gov/programs-and-topics/topics/power-plants/power-plant-licensing).  Publisher: California Energy Commission.

-  Center for Open Science.  BrainsCAN Computational Core Neuroimaging Wiki, March 2019.  URL [https://osf.io/k89fh/](https://arxiv.orghttps://osf.io/k89fh/).  Publisher: OSF.
 [↩](https://arxiv.org/abs/#ax-cite-centerforopenscience2019)

-  China Law Translate.  中华人民共和国国家情报法 (2018修正), June 2017.  URL [https://www.chinalawtranslate.com/national-intelligence-law-of-the-p-r-c-2017/](https://arxiv.orghttps://www.chinalawtranslate.com/national-intelligence-law-of-the-p-r-c-2017/).
 [↩](https://arxiv.org/abs/#ax-cite-translatezhonghuarenmingongheguoguojiaqi)

-  Choi, D., Shavit, Y., and Duvenaud, D.  Tools for Verifying Neural Models’ Training Data, July 2023.  URL [http://arxiv.org/abs/2307.00682](https://arxiv.orghttp://arxiv.org/abs/2307.00682).  arXiv:2307.00682 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-choitoolsverifyingneural2023)

-  Code of Federal Regulations.  22 CFR Part 120 - Purpose and Definitions, 2024.  URL [https://www.ecfr.gov/current/title-22/part-120](https://arxiv.orghttps://www.ecfr.gov/current/title-22/part-120).
 [↩](https://arxiv.org/abs/#ax-cite-codeoffederalregulations22cfrpart)

-  Confidential Computing Consortium.  Confidential Computing: Hardware-Based Trusted Execution for Applications and Data.  Technical report, Confidential Computing Consortium, November 2022.  URL [https://confidentialcomputing.io/wp-content/uploads/sites/10/2023/03/CCC_outreach_whitepaper_updated_November_2022.pdf](https://arxiv.orghttps://confidentialcomputing.io/wp-content/uploads/sites/10/2023/03/CCC_outreach_whitepaper_updated_November_2022.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-confidentialcomputingconsortium2022)

-  Congressional Research Service.  Who Regulates Whom? An Overview of the U.S. Financial Regulatory Framework.  CRS Report R44918, Congressional Research Service, October 2023.  URL [https://sgp.fas.org/crs/misc/R44918.pdf](https://arxiv.orghttps://sgp.fas.org/crs/misc/R44918.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-congressionalresearchservice2023)

-  Congressional Research Service.  The International Emergency Economic Powers Act: Origins, Evolution, and Use.  CRS Report R45618, Congressional Research Service, January 2024.  URL [https://sgp.fas.org/crs/natsec/R45618.pdf](https://arxiv.orghttps://sgp.fas.org/crs/natsec/R45618.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-internationalemergencyeconomic2024)

-  Consumer Financial Protection Bureau.  CFPB Proposes New Federal Oversight of Big Tech Companies and Other Providers of Digital Wallets and Payment Apps, November 2023.  URL [https://www.consumerfinance.gov/about-us/newsroom/cfpb-proposes-new-federal-oversight-of-big-tech-companies-and-other-providers-of-digital-wallets-and-payment-apps/](https://arxiv.orghttps://www.consumerfinance.gov/about-us/newsroom/cfpb-proposes-new-federal-oversight-of-big-tech-companies-and-other-providers-of-digital-wallets-and-payment-apps/).
 [↩](https://arxiv.org/abs/#ax-cite-consumerfinancialprotectionbureaucfpbpro)

-  Copos, B. and Peisert, S.  Catch Me If You Can: Using Power Analysis to Identify HPC Activity, May 2020.  URL [http://arxiv.org/abs/2005.03135](https://arxiv.orghttp://arxiv.org/abs/2005.03135).  arXiv:2005.03135 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-coposcatchmeif2020)

-  CoreWeave.  Privacy Policy, October 2022.  URL [https://docs.coreweave.com/policies/terms-of-service/privacy-policy](https://arxiv.orghttps://docs.coreweave.com/policies/terms-of-service/privacy-policy).

-  CoreWeave.  Security &Compliance, 2023.  URL [https://docs.coreweave.com/policies/terms-of-service/security-and-compliance](https://arxiv.orghttps://docs.coreweave.com/policies/terms-of-service/security-and-compliance).

-  Cottier, B.  Trends in the Dollar Training Cost of Machine Learning Systems, January 2023.  URL [https://epochai.org/blog/trends-in-the-dollar-training-cost-of-machine-learning-systems](https://arxiv.orghttps://epochai.org/blog/trends-in-the-dollar-training-cost-of-machine-learning-systems).
 [↩](https://arxiv.org/abs/#ax-cite-epoch2023trendsinthedollartrainingcostof)

-  Council of the European Union.  Proposal for a Regulation of the European Parliament and of the Council laying down harmonised rules on artificial intelligence (Artificial Intelligence Act) and amending certain Union legislative acts, January 2024.  URL [https://data.consilium.europa.eu/doc/document/ST-5662-2024-INIT/en/pdf](https://arxiv.orghttps://data.consilium.europa.eu/doc/document/ST-5662-2024-INIT/en/pdf).
 [↩](https://arxiv.org/abs/#ax-cite-council-of-the-european-union-proposal-2)

-  Country Legal Frameworks Resource.  Provision of Real-time Lawful Interception Assistance, 2023.  URL [https://clfr.globalnetworkinitiative.org/country/france/](https://arxiv.orghttps://clfr.globalnetworkinitiative.org/country/france/).

-  Cox, J.  Inside the Underground Site Where ‘Neural Networks’ Churn Out Fake IDs, February 2024.  URL [https://www.404media.co/inside-the-underground-site-where-ai-neural-networks-churns-out-fake-ids-onlyfake/](https://arxiv.orghttps://www.404media.co/inside-the-underground-site-where-ai-neural-networks-churns-out-fake-ids-onlyfake/).
 [↩](https://arxiv.org/abs/#ax-cite-cox2024)

-  Dettmers, T., Lewis, M., Belkada, Y., and Zettlemoyer, L.  LLM.int8(): 8-bit Matrix Multiplication for Transformers at Scale, November 2022.  URL [http://arxiv.org/abs/2208.07339](https://arxiv.orghttp://arxiv.org/abs/2208.07339).  arXiv:2208.07339 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-dettmersllmint88bit2022)

-  ECFR.  Acceptance and screening of individuals and accessible property., 2024.  URL [https://www.ecfr.gov/current/title-49/part-1544/section-1544.201](https://arxiv.orghttps://www.ecfr.gov/current/title-49/part-1544/section-1544.201).
 [↩](https://arxiv.org/abs/#ax-cite-acceptancescreeningindividuals2024)

-  Egan, J. and Heim, L.  Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers.  Technical report, Centre for the Governance of AI, October 2023.  URL [https://www.governance.ai/research-paper/oversight-for-frontier-ai-through-kyc-scheme-for-compute-providers](https://arxiv.orghttps://www.governance.ai/research-paper/oversight-for-frontier-ai-through-kyc-scheme-for-compute-providers).
 [↩](https://arxiv.org/abs/#ax-cite-lennartoversightfrontierai2023)

-  EU Agency for Cybersecurity.  Safe Harbor Privacy Principles, July 2000.  URL [https://www.enisa.europa.eu/topics/risk-management/current-risk/laws-regulation/data-protection-privacy/safe-harbor-privacy-principles](https://arxiv.orghttps://www.enisa.europa.eu/topics/risk-management/current-risk/laws-regulation/data-protection-privacy/safe-harbor-privacy-principles).
 [↩](https://arxiv.org/abs/#ax-cite-europeanunionagencyforcybersecuritysafeh)

-  European Commission.  EU-U.S. Privacy Shield: Frequently Asked Questions, July 2016.  URL [https://ec.europa.eu/commission/presscorner/detail/hr/MEMO_16_2462](https://arxiv.orghttps://ec.europa.eu/commission/presscorner/detail/hr/MEMO_16_2462).
 [↩](https://arxiv.org/abs/#ax-cite-europeancommissioneuuprivacyshield2016)

-  European Commission.  Commission welcomes G7 leaders’ agreement on Guiding Principles and a Code of Conduct on Artificial Intelligence, October 2023a.  URL [https://ec.europa.eu/commission/presscorner/detail/en/ip_23_5379](https://arxiv.orghttps://ec.europa.eu/commission/presscorner/detail/en/ip_23_5379).
 [↩](https://arxiv.org/abs/#ax-cite-europeancomission2023)

-  European Commission.  Shaping Europe’s digital future: Hiroshima Process International Code of Conduct for Advanced AI Systems, October 2023b.  URL [https://digital-strategy.ec.europa.eu/en/library/hiroshima-process-international-code-conduct-advanced-ai-systems](https://arxiv.orghttps://digital-strategy.ec.europa.eu/en/library/hiroshima-process-international-code-conduct-advanced-ai-systems).

-  European Union.  Directive 2011/93/EU of the European Parliament and of the Council of 13 December 2011 on combating the sexual abuse and sexual exploitation of children and child pornography, and replacing Council Framework Decision 2004/68/JHA, July 2011.  URL [https://eur-lex.europa.eu/eli/dir/2011/93/oj](https://arxiv.orghttps://eur-lex.europa.eu/eli/dir/2011/93/oj).

-  European Union.  Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data, and repealing Directive 95/46/EC (General Data Protection Regulation), May 2016.  URL [http://data.europa.eu/eli/reg/2016/679/oj](https://arxiv.orghttp://data.europa.eu/eli/reg/2016/679/oj).  119.

-  European Union.  Regulation (EU) 2021/784 of the European Parliament and of the Council of 29 April 2021 on addressing the dissemination of terrorist content online.  Official Journal of the European Union L 172/79, pp. 79–109, May 2021.  URL [https://eur-lex.europa.eu/eli/reg/2021/784/oj](https://arxiv.orghttps://eur-lex.europa.eu/eli/reg/2021/784/oj).
 [↩](https://arxiv.org/abs/#ax-cite-europeanunion2021)

-  Farrell, H. and Newman, A.  Underground Empire: How America Weaponized the World Economy.  Henry Holt and Co., September 2023.  ISBN 978-1-250-84055-4.  URL [https://us.macmillan.com/books/9781250840554/undergroundempire](https://arxiv.orghttps://us.macmillan.com/books/9781250840554/undergroundempire).
 [↩](https://arxiv.org/abs/#ax-cite-farrellundergroundempirehow2023)

-  Federal Register.  Taking Additional Steps To Address the National Emergency With Respect to Significant Malicious Cyber-Enabled Activities: A Proposed Rule by the Commerce Department, January 2024.  URL [https://www.federalregister.gov/documents/2024/01/29/2024-01580/taking-additional-steps-to-address-the-national-emergency-with-respect-to-significant-malicious](https://arxiv.orghttps://www.federalregister.gov/documents/2024/01/29/2024-01580/taking-additional-steps-to-address-the-national-emergency-with-respect-to-significant-malicious).
 [↩](https://arxiv.org/abs/#ax-cite-federalregister2024)

-  Federal Trade Commission.  FTC Launches Inquiry into Generative AI Investments and Partnerships, January 2024.  URL [https://www.ftc.gov/news-events/news/press-releases/2024/01/ftc-launches-inquiry-generative-ai-investments-partnerships](https://arxiv.orghttps://www.ftc.gov/news-events/news/press-releases/2024/01/ftc-launches-inquiry-generative-ai-investments-partnerships).
 [↩](https://arxiv.org/abs/#ax-cite-federaltradecommissionftclaunchesinquiry)

-  FedRAMP.  Understanding Baselines and Impact Levels for FedRAMP Authorization, 2024.  URL [https://www.fedramp.gov/baselines/](https://arxiv.orghttps://www.fedramp.gov/baselines/).
 [↩](https://arxiv.org/abs/#ax-cite-baselines)

-  Financial Action Task Force.  FATF 40 Recommendations October 2003 (incorporating all subsequent amendments until October 2004).  Technical report, FATF, October 2003.  URL [{](https://arxiv.org{)https://www.fatf-gafi.org/content/dam/fatf-gafi/recommendations/FATF
 [↩](https://arxiv.org/abs/#ax-cite-financialactiontaskforcefatf40recommenda)

-  Financial Action Task Force.  International Standards on Combating Money Laundering and the Financing of Terrorism and Proliferation.  Technical report, FATF, Paris, France, November 2023.  URL [{](https://arxiv.org{)https://www.fatf-gafi.org/content/dam/fatf-gafi/recommendations/FATF
 [↩](https://arxiv.org/abs/#ax-cite-financialactiontaskforceinternationalsta)

-  Financial Action Task Force.  High-risk and other monitored jurisdictions, 2024a.  URL [https://www.fatf-gafi.org/en/topics/high-risk-and-other-monitored-jurisdictions.html](https://arxiv.orghttps://www.fatf-gafi.org/en/topics/high-risk-and-other-monitored-jurisdictions.html).

-  Financial Action Task Force.  Financial Action Task Force Home, 2024b.  URL [https://www.fatf-gafi.org/en/home.html](https://arxiv.orghttps://www.fatf-gafi.org/en/home.html).
 [↩](https://arxiv.org/abs/#ax-cite-financialactiontaskforcehome)

-  Financial Crimes Enforcement Network.  FACT SHEET for Section 312 of the USA PATRIOT Act Final Regulation and Notice of Proposed Rulemaking.  Technical report, U.S. Treasury, December 2005.  URL [https://www.fincen.gov/fact-sheet-section-312-usa-patriot-act-final-regulation-and-notice-proposed-rulemaking](https://arxiv.orghttps://www.fincen.gov/fact-sheet-section-312-usa-patriot-act-final-regulation-and-notice-proposed-rulemaking).
 [↩](https://arxiv.org/abs/#ax-cite-financialcrimesenforcementnetwork)

-  Financial Crimes Enforcement Network.  Financial Crimes Enforcement Network - Mission, 2024.  URL [https://www.fincen.gov/about/mission](https://arxiv.orghttps://www.fincen.gov/about/mission).

-  Fist, T. and Grunewald, E.  Preventing AI Chip Smuggling to China.  Working Paper, Center for a New American Security, October 2023.  URL [https://www.cnas.org/publications/reports/preventing-ai-chip-smuggling-to-china](https://arxiv.orghttps://www.cnas.org/publications/reports/preventing-ai-chip-smuggling-to-china).

-  Fist, T., Heim, L., and Schneider, J.  Chinese Firms Are Evading Chip Controls, June 2023.  URL [https://foreignpolicy.com/2023/06/21/china-united-states-semiconductor-chips-sanctions-evasion/](https://arxiv.orghttps://foreignpolicy.com/2023/06/21/china-united-states-semiconductor-chips-sanctions-evasion/).
 [↩](https://arxiv.org/abs/#ax-cite-fistchinesefirmsare2024)

-  FluidStack.  FluidStack Privacy Notice, February 2022.  URL [{](https://arxiv.org{)https://uploads-ssl.webflow.com/64e49a6c77bc12449a05e6a2/6502008478387e54d7816888_Privacy

-  Future of Life Institute.  EU Artificial Intelligence Act: The Act Texts, 2024.  URL [https://artificialintelligenceact.eu/the-act/](https://arxiv.orghttps://artificialintelligenceact.eu/the-act/).
 [↩](https://arxiv.org/abs/#ax-cite-futureoflifeinstituteeuartificialintelli)

-  Gatlan, S.  Microsoft breach led to theft of 60,000 US State Dept emails, September 2023.  URL [https://www.bleepingcomputer.com/news/security/microsoft-breach-led-to-theft-of-60-000-us-state-dept-emails/](https://arxiv.orghttps://www.bleepingcomputer.com/news/security/microsoft-breach-led-to-theft-of-60-000-us-state-dept-emails/).
 [↩](https://arxiv.org/abs/#ax-cite-gatlan2023)

-  Google.  google/cluster-data, March 2024.  URL [https://github.com/google/cluster-data](https://arxiv.orghttps://github.com/google/cluster-data).  original-date: 2015-07-29T17:52:23Z.
 [↩](https://arxiv.org/abs/#ax-cite-googleclusterdata2024)

-  Google Cloud.  Google Cloud &the General Data Protection Regulation (GDPR), 2021.  URL [https://cloud.google.com/privacy/gdpr](https://arxiv.orghttps://cloud.google.com/privacy/gdpr).

-  Google Cloud.  Cloud Data Processing Addendum, November 2023.  URL [https://cloud.google.com/terms/data-processing-addendum](https://arxiv.orghttps://cloud.google.com/terms/data-processing-addendum).
 [↩](https://arxiv.org/abs/#ax-cite-googlecloudclouddataprocessing)

-  Google Cloud.  All networking pricing, 2024a.  URL [https://cloud.google.com/vpc/network-pricing](https://arxiv.orghttps://cloud.google.com/vpc/network-pricing).
 [↩](https://arxiv.org/abs/#ax-cite-googlecloud)

-  Google Cloud.  Climate Sustainability, 2024b.  URL [https://cloud.google.com/gov/sustainability](https://arxiv.orghttps://cloud.google.com/gov/sustainability).

-  Google Cloud.  Google Cloud Privacy Notice, 2024c.  URL [https://cloud.google.com/terms/cloud-privacy-notice](https://arxiv.orghttps://cloud.google.com/terms/cloud-privacy-notice).

-  Government of India.  Govt considering proposal to set up 25K GPUs, October 2023.  URL [https://indbiz.gov.in/govt-considering-proposal-to-set-up-25k-gpus/](https://arxiv.orghttps://indbiz.gov.in/govt-considering-proposal-to-set-up-25k-gpus/).
 [↩](https://arxiv.org/abs/#ax-cite-govtconsideringproposal2023)

-  Hacker, P.  The European AI liability directives – Critique of a half-hearted approach and lessons for the future.  Computer Law &Security Review, 51:0 105871, November 2023.  ISSN 0267-3649.  [10.1016/j.clsr.2023.105871](https://arxiv.orghttps://doi.org/10.1016/j.clsr.2023.105871).  URL [https://www.sciencedirect.com/science/article/pii/S026736492300081X](https://arxiv.orghttps://www.sciencedirect.com/science/article/pii/S026736492300081X).
 [↩](https://arxiv.org/abs/#ax-cite-hacker2023)

-  Hay, J. R. and Shleifer, A.  Private enforcement of public laws: a theory of legal reform.  American Economic Review Papers and Proceedings, 880 (2):0 398–403, 1998.  URL [https://www.jstor.org/stable/116955](https://arxiv.orghttps://www.jstor.org/stable/116955).

-  Heim, L.  Crucial Considerations for Compute Governance, February 2024.  URL [https://blog.heim.xyz/crucial-considerations-for-compute-governance/](https://arxiv.orghttps://blog.heim.xyz/crucial-considerations-for-compute-governance/).
 [↩](https://arxiv.org/abs/#ax-cite-heimcrucialconsiderationscompute2024)

-  Heim, L. and Egan, J.  Accessing Controlled AI Chips via Infrastructure-as-a-Service (IaaS): Implications for Export Controls: Comment on BIS–2022–0025 (RIN 0694–AI94) — Question 1.  Technical report, Centre for the Governance of AI, December 2023.  URL [https://cdn.governance.ai/Accessing_Controlled_AI_Chips_via_Infrastructure-as-a-Service.pdf](https://arxiv.orghttps://cdn.governance.ai/Accessing_Controlled_AI_Chips_via_Infrastructure-as-a-Service.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-heimaccessingcontrolledai2023)

-  IBM.  What is Confidential Computing?, 2024.  URL [https://www.ibm.com/topics/confidential-computing](https://arxiv.orghttps://www.ibm.com/topics/confidential-computing).
 [↩](https://arxiv.org/abs/#ax-cite-ibm)

-  India’s Ministry of Electronics and Information Technology.  Proposed Digital India Act, 2023, March 2023.  URL [{](https://arxiv.org{)https://www.meity.gov.in/writereaddata/files/DIA_Presentation
 [↩](https://arxiv.org/abs/#ax-cite-indiasministryofelectronicsandinformatio)

-  Janardhan, S.  Reimagining Our Infrastructure for the AI Age, May 2023.  URL [https://about.fb.com/news/2023/05/metas-infrastructure-for-ai/](https://arxiv.orghttps://about.fb.com/news/2023/05/metas-infrastructure-for-ai/).
 [↩](https://arxiv.org/abs/#ax-cite-janardhanreimaginingourinfrastructure202)

-  Jeon, M., Venkataraman, S., Phanishayee, A., Qian, J., Xiao, W., and Yang, F.  Analysis of Large-Scale Multi-Tenant GPU Clusters for DNN Training Workloads, August 2019.  URL [http://arxiv.org/abs/1901.05758](https://arxiv.orghttp://arxiv.org/abs/1901.05758).  arXiv:1901.05758 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-jeonanalysislargescalemultitenant2019)

-  Jiang, B. and Cao, A.  China to create and implement national standard for large language models in move to regulate AI, while using its power to transform industries.  South China Morning Post, July 2023.  URL [https://www.scmp.com/tech/policy/article/3226942/china-create-and-implement-national-standard-large-language-models-move-regulate-ai-while-using-its](https://arxiv.orghttps://www.scmp.com/tech/policy/article/3226942/china-create-and-implement-national-standard-large-language-models-move-regulate-ai-while-using-its).

-  Jones, G., Egan, J., and Rosenbach, E.  Advancing in Adversity: Ukraine’s Battlefield Technologies and Lessons for the U.S.  Policy Brief, Belfer Center for Science and International Affairs, July 2023.  URL [https://www.belfercenter.org/publication/advancing-adversity-ukraines-battlefield-technologies-and-lessons-us](https://arxiv.orghttps://www.belfercenter.org/publication/advancing-adversity-ukraines-battlefield-technologies-and-lessons-us).
 [↩](https://arxiv.org/abs/#ax-cite-jonesadvancingadversityukraine2023)

-  Kim, C.  Privacy activists slam EU-US pact on data sharing.  BBC News, July 2023.  URL [https://www.bbc.com/news/world-us-canada-66161135](https://arxiv.orghttps://www.bbc.com/news/world-us-canada-66161135).
 [↩](https://arxiv.org/abs/#ax-cite-kimprivacyactivistsslam2023)

-  Korolov, M.  Data centers unprepared for new European energy efficiency regulations, December 2023.  URL [https://www.networkworld.com/article/1251883/data-centers-unprepared-for-new-european-energy-efficiency-regulations.html](https://arxiv.orghttps://www.networkworld.com/article/1251883/data-centers-unprepared-for-new-european-energy-efficiency-regulations.html).
 [↩](https://arxiv.org/abs/#ax-cite-korolov2023)

-  Kulp, G., Gonzales, D., Smith, E., Heim, L., Puri, P., Vermeer, M. J. D., and Winkelman, Z.  Hardware-Enabled Governance Mechanisms: Developing Technical Solutions to Exempt Items Otherwise Classified Under Export Control Classification Numbers 3A090 and 4A090.  Technical report, RAND Corporation, January 2024.  URL [https://www.rand.org/pubs/working_papers/WRA3056-1.html](https://arxiv.orghttps://www.rand.org/pubs/working_papers/WRA3056-1.html).
 [↩](https://arxiv.org/abs/#ax-cite-kulphardwareenabledgovernancemechanisms2)

-  Köhler, S., Wenzel, L., Plauth, M., Böning, P., Gampe, P., Geier, L., and Polze, A.  Recognizing HPC Workloads Based on Power Draw Signatures.  In 2021 Ninth International Symposium on Computing and Networking Workshops (CANDARW), pp. 278–284, December 2021.  [10.1109/CANDARW53999.2021.00053](https://arxiv.orghttps://doi.org/10.1109/CANDARW53999.2021.00053).  URL [https://ieeexplore.ieee.org/document/9644213](https://arxiv.orghttps://ieeexplore.ieee.org/document/9644213).

-  Lambda Labs.  Lambda Privacy Policy, August 2022.  URL [https://lambdalabs.com/legal/privacy-policy](https://arxiv.orghttps://lambdalabs.com/legal/privacy-policy).

-  legislation.gov.uk.  Data Retention and Investigatory Powers Act 2014, 2014.  URL [https://www.legislation.gov.uk/ukpga/2014/27/crossheading/retention-of-relevant-communications-data/enacted](https://arxiv.orghttps://www.legislation.gov.uk/ukpga/2014/27/crossheading/retention-of-relevant-communications-data/enacted).  Publisher: King’s Printer of Acts of Parliament.
 [↩](https://arxiv.org/abs/#ax-cite-legislation-gov-ukdataretentioninvestiga)

-  Linn, C. J.  Redefining the Bank Secrecy Act: Currency Reporting and the Crime of Structuring.  Santa Clara Law Review, 500 (2):0 407–513, January 2010.  URL [https://digitalcommons.law.scu.edu/lawreview/vol50/iss2/4/](https://arxiv.orghttps://digitalcommons.law.scu.edu/lawreview/vol50/iss2/4/).
 [↩](https://arxiv.org/abs/#ax-cite-linnredefiningbanksecrecy2010)

-  Lohr, A.  Intelligence community and Defense Department to share classified cloud services, July 2023.  URL [https://federalnewsnetwork.com/defense-main/2023/07/intelligence-community-and-defense-department-to-share-classified-cloud-services/](https://arxiv.orghttps://federalnewsnetwork.com/defense-main/2023/07/intelligence-community-and-defense-department-to-share-classified-cloud-services/).
 [↩](https://arxiv.org/abs/#ax-cite-lohr2023)

-  Merritt, R.  What Is NVLink?, March 2023.  URL [https://blogs.nvidia.com/blog/what-is-nvidia-nvlink/](https://arxiv.orghttps://blogs.nvidia.com/blog/what-is-nvidia-nvlink/).
 [↩](https://arxiv.org/abs/#ax-cite-merritt2023)

-  Microsoft.  US National Security Orders Reports | Microsoft CSR, 2022.  URL [https://www.microsoft.com/en-us/corporate-responsibility/fisa](https://arxiv.orghttps://www.microsoft.com/en-us/corporate-responsibility/fisa).
 [↩](https://arxiv.org/abs/#ax-cite-microsoftusnationalsecurity)

-  Microsoft.  What is confidential computing?, October 2023.  URL [https://learn.microsoft.com/en-us/azure/confidential-computing/overview](https://arxiv.orghttps://learn.microsoft.com/en-us/azure/confidential-computing/overview).

-  Microsoft.  Microsoft Privacy Statement – Microsoft privacy, February 2024a.  URL [https://privacy.microsoft.com/en-us/privacystatement](https://arxiv.orghttps://privacy.microsoft.com/en-us/privacystatement).

-  Microsoft.  Confidential Computing on Azure, February 2024b.  URL [https://learn.microsoft.com/en-us/azure/confidential-computing/overview-azure-products](https://arxiv.orghttps://learn.microsoft.com/en-us/azure/confidential-computing/overview-azure-products).

-  Microsoft Azure.  Azure Sustainability, 2024a.  URL [https://azure.microsoft.com/en-us/explore/global-infrastructure/sustainability](https://arxiv.orghttps://azure.microsoft.com/en-us/explore/global-infrastructure/sustainability).

-  Microsoft Azure.  Bandwidth pricing, 2024b.  URL [https://azure.microsoft.com/en-us/pricing/details/bandwidth/](https://arxiv.orghttps://azure.microsoft.com/en-us/pricing/details/bandwidth/).

-  Microsoft Corporate Blogs.  Microsoft and OpenAI extend partnership, January 2023.  URL [https://blogs.microsoft.com/blog/2023/01/23/microsoftandopenaiextendpartnership/](https://arxiv.orghttps://blogs.microsoft.com/blog/2023/01/23/microsoftandopenaiextendpartnership/).
 [↩](https://arxiv.org/abs/#ax-cite-microsoftcorporateblogsmicrosoftopenaiex)

-  Milmo, D.  CMA to investigate UK cloud computing market amid Microsoft and Amazon concerns.  The Guardian, October 2023.  ISSN 0261-3077.  URL [https://www.theguardian.com/business/2023/oct/05/amazon-and-microsofts-uk-cloud-computing-dominance-faces-investigation](https://arxiv.orghttps://www.theguardian.com/business/2023/oct/05/amazon-and-microsofts-uk-cloud-computing-dominance-faces-investigation).
 [↩](https://arxiv.org/abs/#ax-cite-milmocmainvestigateuk2023)

-  Mithril Security.  mithril-security/aicert, January 2024a.  URL [https://github.com/mithril-security/aicert](https://arxiv.orghttps://github.com/mithril-security/aicert).  original-date: 2023-07-04T07:24:29Z.

-  Mithril Security.  mithril-security/blindai, February 2024b.  URL [https://github.com/mithril-security/blindai](https://arxiv.orghttps://github.com/mithril-security/blindai).  original-date: 2022-02-06T14:07:35Z.
 [↩](https://arxiv.org/abs/#ax-cite-mithrilsecurityblindai2024)

-  Mulani, N. and Whittlestone, J.  Proposing a Foundation Model Information-Sharing Regime for the UK, June 2023.  URL [https://www.governance.ai/post/proposing-a-foundation-model-information-sharing-regime-for-the-uk](https://arxiv.orghttps://www.governance.ai/post/proposing-a-foundation-model-information-sharing-regime-for-the-uk).

-  Murgia, M.  White House science chief signals US-China co-operation on AI safety.  Financial Times, January 2024.  URL [https://www.ft.com/content/94b9878b-9412-4dbc-83ba-aac2baadafd9](https://arxiv.orghttps://www.ft.com/content/94b9878b-9412-4dbc-83ba-aac2baadafd9).
 [↩](https://arxiv.org/abs/#ax-cite-murgiawhitehousescience2024)

-  Nagao, R.  Japan to pay for half of $100m generative AI supercomputer - Nikkei Asia.  Nikkei Asia, June 2023.  URL [https://asia.nikkei.com/Business/Technology/Japan-to-pay-for-half-of-100m-generative-AI-supercomputer](https://arxiv.orghttps://asia.nikkei.com/Business/Technology/Japan-to-pay-for-half-of-100m-generative-AI-supercomputer).

-  National Energy Research Scientific Computing.  NERSC Documentation: Roofline Performance Model, 2024.  URL [https://docs.nersc.gov/tools/performance/roofline/](https://arxiv.orghttps://docs.nersc.gov/tools/performance/roofline/).
 [↩](https://arxiv.org/abs/#ax-cite-nationalenergyresearchscientificcomputin)

-  National Security Telecommunications Advisory Committee.  NSTAC Report to the President: Addressing the Abuse of Domestic Infrastructure by Foreign Malicious Actors.  Technical report, National Security Telecommunications Advisory Committee, 2023.  URL [https://www.cisa.gov/sites/default/files/2024-01/NSTAC_Report_to_the_President_on_Addressing_the_Abuse_of_Domestic_Infrastructure_by_Foreign_Malicious_Actors_508c.pdf](https://arxiv.orghttps://www.cisa.gov/sites/default/files/2024-01/NSTAC_Report_to_the_President_on_Addressing_the_Abuse_of_Domestic_Infrastructure_by_Foreign_Malicious_Actors_508c.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-nationalsecuritytelecommunicationsadviso)

-  Nevo, S., Lahav, D., Karpur, A., Alstott, J., and Matheny, J.  Securing Artificial Intelligence Model Weights: Interim Report.  Technical report, RAND Corporation, October 2023.  URL [https://www.rand.org/pubs/working_papers/WRA2849-1.html](https://arxiv.orghttps://www.rand.org/pubs/working_papers/WRA2849-1.html).
 [↩](https://arxiv.org/abs/#ax-cite-nevo2023)

-  NVIDIA.  Confidential Compute on NVIDIA Hopper H100, July 2023.  URL [https://images.nvidia.com/aem-dam/en-zz/Solutions/data-center/HCC-Whitepaper-v1.0.pdf](https://arxiv.orghttps://images.nvidia.com/aem-dam/en-zz/Solutions/data-center/HCC-Whitepaper-v1.0.pdf).

-  NVIDIA.  NVIDIA BlueField Networking Platform, 2024a.  URL [https://resources.nvidia.com/en-us-accelerated-networking-resource-library-ms/](https://arxiv.orghttps://resources.nvidia.com/en-us-accelerated-networking-resource-library-ms/).

-  NVIDIA.  NVIDIA Nsight Perf SDK, 2024b.  URL [https://developer.nvidia.com/nsight-perf-sdk](https://arxiv.orghttps://developer.nvidia.com/nsight-perf-sdk).
 [↩](https://arxiv.org/abs/#ax-cite-nvidianvidiansightperf)

-  NVIDIA.  Redfish APIs Support, 2024c.  URL [https://docs.nvidia.com/dgx/dgxh100-user-guide/redfish-api-supp.html](https://arxiv.orghttps://docs.nvidia.com/dgx/dgxh100-user-guide/redfish-api-supp.html).
 [↩](https://arxiv.org/abs/#ax-cite-zotero-3386)

-  O’Brien, J., Ee, S., and Williams, Z.  Deployment corrections: An incident response framework for frontier AI models.  Technical report, Institute for AI Policy and Strategy, September 2023.  URL [https://arxiv.org/abs/2310.00328](https://arxiv.orghttps://arxiv.org/abs/2310.00328).
 [↩](https://arxiv.org/abs/#ax-cite-obriendeploymentcorrectionsincident2023)

-  OECD.  Measuring the environmental impacts of artificial intelligence compute and applications: The AI footprint.  OECD Digital Economy Papers 341, OECD, November 2022.  URL [https://www.oecd-ilibrary.org/science-and-technology/measuring-the-environmental-impacts-of-artificial-intelligence-compute-and-applications_7babf571-en](https://arxiv.orghttps://www.oecd-ilibrary.org/science-and-technology/measuring-the-environmental-impacts-of-artificial-intelligence-compute-and-applications_7babf571-en).  Series: OECD Digital Economy Papers Volume: 341.
 [↩](https://arxiv.org/abs/#ax-cite-oecdmeasuringenvironmentalimpacts2022)

-  Office for Civil Rights.  Guidance on HIPAA &Cloud Computing, October 2016.  URL [https://www.hhs.gov/hipaa/for-professionals/special-topics/health-information-technology/cloud-computing/index.html](https://arxiv.orghttps://www.hhs.gov/hipaa/for-professionals/special-topics/health-information-technology/cloud-computing/index.html).  Last Modified: 2023-02-02T10:24:50-0500.
 [↩](https://arxiv.org/abs/#ax-cite-officeforcivilrights2016)

-  OFWAT.  The Water Services Regulation Authority, 2024.  URL [https://www.ofwat.gov.uk/regulated-companies/ofwat-industry-overview/licences/](https://arxiv.orghttps://www.ofwat.gov.uk/regulated-companies/ofwat-industry-overview/licences/).

-  OpenMined.  How to Audit an AI Model Owned by Someone Else (Part 1): An introduction to state-of-the-art AI auditing infrastructure, June 2023.  URL [https://blog.openmined.org/ai-audit-part-1/](https://arxiv.orghttps://blog.openmined.org/ai-audit-part-1/).

-  OpenMined.  OpenMined/PySyft, March 2024.  URL [https://github.com/OpenMined/PySyft](https://arxiv.orghttps://github.com/OpenMined/PySyft).  original-date: 2017-07-18T20:41:16Z.

-  Owen, D.  How predictable is language model benchmark performance?, January 2024.  URL [http://arxiv.org/abs/2401.04757](https://arxiv.orghttp://arxiv.org/abs/2401.04757).  arXiv:2401.04757 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-owenhowpredictablelanguage2024)

-  Pal, B., Gorczynski, S., and Schmidt, D.  Overview of Data Transfer Costs for Common Architectures | AWS Architecture Blog, June 2021.  URL [https://aws.amazon.com/blogs/architecture/overview-of-data-transfer-costs-for-common-architectures/](https://arxiv.orghttps://aws.amazon.com/blogs/architecture/overview-of-data-transfer-costs-for-common-architectures/).  Section: Amazon EC2.

-  Patel, P., Choukse, E., Zhang, C., Goiri, I., Warrier, B., Mahalingam, N., and Bianchini, R.  POLCA: Power Oversubscription in LLM Cloud Providers, August 2023.  URL [http://arxiv.org/abs/2308.12908](https://arxiv.orghttp://arxiv.org/abs/2308.12908).  arXiv:2308.12908 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-patelpolcapoweroversubscription2023)

-  Pilz, K. and Heim, L.  Compute at Scale: A Broad Investigation into the Data Center Industry, November 2023.  URL [https://arxiv.org/abs/2311.02651v4](https://arxiv.orghttps://arxiv.org/abs/2311.02651v4).
 [↩](https://arxiv.org/abs/#ax-cite-pilz2023)

-  Pilz, K., Heim, L., and Brown, N.  Increased Compute Efficiency and the Diffusion of AI Capabilities, February 2024.  URL [http://arxiv.org/abs/2311.15377](https://arxiv.orghttp://arxiv.org/abs/2311.15377).  arXiv:2311.15377 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-pilzincreasedcomputeefficiency2024)

-  Prime Minister’s Office, FCDO UK, and DSIT UK.  The Bletchley Declaration by Countries Attending the AI Safety Summit, 1-2 November 2023, November 2023.  URL [https://www.gov.uk/government/publications/ai-safety-summit-2023-the-bletchley-declaration/the-bletchley-declaration-by-countries-attending-the-ai-safety-summit-1-2-november-2023](https://arxiv.orghttps://www.gov.uk/government/publications/ai-safety-summit-2023-the-bletchley-declaration/the-bletchley-declaration-by-countries-attending-the-ai-safety-summit-1-2-november-2023).
 [↩](https://arxiv.org/abs/#ax-cite-primeministersoffice10downingstreetbletc)

-  Rabinovitsj, D.  Opening AI Infrastructure: Ushering In The Age Of GenAI, December 2023.  URL [https://drive.google.com/file/d/1ud1JZqco2868AvmkNkrA-Axp-74PvwWx/view?usp=embed_facebook](https://arxiv.orghttps://drive.google.com/file/d/1ud1JZqco2868AvmkNkrA-Axp-74PvwWx/view?usp=embed_facebook).
 [↩](https://arxiv.org/abs/#ax-cite-rabinovitsjopeningaiinfrastructure)

-  Rep. Collins, D. R.-G.-.  Text - H.R.4943 - 115th Congress (2017-2018): CLOUD Act, February 2018.  URL [https://www.congress.gov/bill/115th-congress/house-bill/4943/text](https://arxiv.orghttps://www.congress.gov/bill/115th-congress/house-bill/4943/text).  Archive Location: 2018-02-06.
 [↩](https://arxiv.org/abs/#ax-cite-rep-collinstext4943115th2018)

-  Richter, F.  Amazon Maintains Cloud Lead as Microsoft Edges Closer, February 2024.  URL [https://www.statista.com/chart/18819/worldwide-market-share-of-leading-cloud-infrastructure-service-providers](https://arxiv.orghttps://www.statista.com/chart/18819/worldwide-market-share-of-leading-cloud-infrastructure-service-providers).
 [↩](https://arxiv.org/abs/#ax-cite-infographicamazonmaintains2024)

-  Sanction Scanner.  What is the Difference Between Smurfing and Structuring?, 2024.  URL [https://sanctionscanner.com/blog/what-is-the-difference-between-smurfing-and-structuring-594](https://arxiv.orghttps://sanctionscanner.com/blog/what-is-the-difference-between-smurfing-and-structuring-594).
 [↩](https://arxiv.org/abs/#ax-cite-sanctionscannerwhatdifferencesmurfing)

-  Sastry, G., Heim, L., Belfield, H., Anderljung, M., Brundage, M., Hazell, J., O’Keefe, C., Hadfield, G. K., Ngo, R., Pilz, K., Gor, G., Bluemke, E., Shoker, S., Egan, J., Trager, R. F., Avin, S., Weller, A., Bengio, Y., and Coyle, D.  Computing Power and the Governance of Artificial Intelligence, February 2024.  URL [http://arxiv.org/abs/2402.08797](https://arxiv.orghttp://arxiv.org/abs/2402.08797).  arXiv:2402.08797 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-sastrycomputingpowergovernance2024)

-  Secretary of State for Science, Innovation and Technology.  A pro-innovation approach to AI regulation.  Policy paper Command Paper Number: 815, GOV.UK., August 2023.  URL [https://www.gov.uk/government/publications/ai-regulation-a-pro-innovation-approach/white-paper](https://arxiv.orghttps://www.gov.uk/government/publications/ai-regulation-a-pro-innovation-approach/white-paper).  ISBN: 978-1-5286-4009-1.

-  Senator Scott Wiener.  Senator Wiener Introduces Legislation to Ensure Safe Development of Large-Scale Artificial Intelligence Systems and Support AI Innovation in California, February 2024.  URL [https://sd11.senate.ca.gov/news/20240208-senator-wiener-introduces-legislation-ensure-safe-development-large-scale-artificial](https://arxiv.orghttps://sd11.senate.ca.gov/news/20240208-senator-wiener-introduces-legislation-ensure-safe-development-large-scale-artificial).

-  Sevilla, J., Heim, L., Ho, A., Besiroglu, T., Hobbhahn, M., and Villalobos, P.  Compute Trends Across Three Eras of Machine Learning.  In 2022 International Joint Conference on Neural Networks (IJCNN), pp. 1–8, July 2022.  [10.1109/IJCNN55064.2022.9891914](https://arxiv.orghttps://doi.org/10.1109/IJCNN55064.2022.9891914).  URL [http://arxiv.org/abs/2202.05924](https://arxiv.orghttp://arxiv.org/abs/2202.05924).  arXiv:2202.05924 [cs].

-  Shavit, Y., Agarwal, S., Brundage, M., and Adler, S.  Practices for Governing Agentic AI Systems.  Research Paper, OpenAI, December 2023.  URL [https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf](https://arxiv.orghttps://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-shavitpracticesgoverningagentic2023)

-  Sheehan, M.  Tracing the Roots of China’s AI Regulations.  Technical report, Carnegie Endowment for International Peace, February 2024.  URL [https://carnegieendowment.org/2024/02/27/tracing-roots-of-china-s-ai-regulations-pub-91815](https://arxiv.orghttps://carnegieendowment.org/2024/02/27/tracing-roots-of-china-s-ai-regulations-pub-91815).

-  Shoeybi, M., Patwary, M., Puri, R., LeGresley, P., Casper, J., and Catanzaro, B.  Megatron-LM: Training Multi-Billion Parameter Language Models Using Model Parallelism, March 2020.  URL [http://arxiv.org/abs/1909.08053](https://arxiv.orghttp://arxiv.org/abs/1909.08053).  arXiv:1909.08053 [cs].

-  Sliwko, L. and Getov, V.  AGOCS — Accurate Google Cloud Simulator Framework.  In 2016 Intl IEEE Conferences on Ubiquitous Intelligence &Computing, Advanced and Trusted Computing, Scalable Computing and Communications, Cloud and Big Data Computing, Internet of People, and Smart World Congress (UIC/ATC/ScalCom/CBDCom/IoP/SmartWorld), pp. 550–558, January 2016.  [10.1109/UIC-ATC-ScalCom-CBDCom-IoP-SmartWorld.2016.0095](https://arxiv.orghttps://doi.org/10.1109/UIC-ATC-ScalCom-CBDCom-IoP-SmartWorld.2016.0095).  URL [https://ieeexplore.ieee.org/document/7816891](https://arxiv.orghttps://ieeexplore.ieee.org/document/7816891).
 [↩](https://arxiv.org/abs/#ax-cite-sliwkoagocsaccurategoogle2016)

-  Smith, B.  The need for a Digital Geneva Convention, February 2017.  URL [https://blogs.microsoft.com/on-the-issues/2017/02/14/need-digital-geneva-convention/](https://arxiv.orghttps://blogs.microsoft.com/on-the-issues/2017/02/14/need-digital-geneva-convention/).
 [↩](https://arxiv.org/abs/#ax-cite-smithneeddigitalgeneva2017)

-  Smith, B.  How do we best govern AI?, May 2023.  URL [https://blogs.microsoft.com/on-the-issues/2023/05/25/how-do-we-best-govern-ai/](https://arxiv.orghttps://blogs.microsoft.com/on-the-issues/2023/05/25/how-do-we-best-govern-ai/).
 [↩](https://arxiv.org/abs/#ax-cite-smith2023)

-  Tang, B. J., Chen, Q., Weiss, M. L., Frey, N., McDonald, J., Bestor, D., Yee, C., Arcand, W., Byun, C., Edelman, D., Hubbell, M., Jones, M., Kepner, J., Klein, A., Michaleas, A., Michaleas, P., Milechin, L., Mullen, J., Prout, A., Reuther, A., Rosa, A., Bowne, A., McEvoy, L., Li, B., Tiwari, D., Gadepally, V., and Samsi, S.  The MIT Supercloud Workload Classification Challenge.  In 2022 IEEE International Parallel and Distributed Processing Symposium Workshops (IPDPSW), pp. 708–714, May 2022.  [10.1109/IPDPSW55747.2022.00122](https://arxiv.orghttps://doi.org/10.1109/IPDPSW55747.2022.00122).  URL [http://arxiv.org/abs/2204.05839](https://arxiv.orghttp://arxiv.org/abs/2204.05839).  arXiv:2204.05839 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-tangmitsupercloudworkload2022)

-  Terai, M., Kashiwaki, R., and Shoji, F.  Workload Classification and Performance Analysis using Job Metrics in the K computer.  IPSJ SIG Technical Report 13, Information Processing Society of Japan, December 2017.  URL [https://ipsj.ixsq.nii.ac.jp/ej/?action=repository_uri&item_id=184893&file_id=1&file_no=1](https://arxiv.orghttps://ipsj.ixsq.nii.ac.jp/ej/?action=repository_uri&item_id=184893&file_id=1&file_no=1).  Vol. 2017-HPC-162.

-  The European High Performance Computing Joint Undertaking.  Open Call to Support HPC-powered Artificial Intelligence (AI) Applications - European Commission, November 2023.  URL [https://eurohpc-ju.europa.eu/open-call-support-hpc-powered-artificial-intelligence-ai-applications-2023-11-28_en](https://arxiv.orghttps://eurohpc-ju.europa.eu/open-call-support-hpc-powered-artificial-intelligence-ai-applications-2023-11-28_en).

-  The White House.  Voluntary AI Commitments, September 2023a.  URL [https://www.whitehouse.gov/wp-content/uploads/2023/09/Voluntary-AI-Commitments-September-2023.pdf](https://arxiv.orghttps://www.whitehouse.gov/wp-content/uploads/2023/09/Voluntary-AI-Commitments-September-2023.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-thewhitehouse2023)

-  The White House.  Executive Order on the Safe, Secure, and Trustworthy Development and Use of Artificial Intelligence.  Technical report, The White House, October 2023b.  URL [https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/](https://arxiv.orghttps://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/).
 [↩](https://arxiv.org/abs/#ax-cite-thewhitehouseexecutiveordersafe2023)

-  The White House.  FACT SHEET: Biden-Harris Administration Secures Voluntary Commitments from Leading Artificial Intelligence Companies to Manage the Risks Posed by AI, July 2023c.  URL [https://www.whitehouse.gov/briefing-room/statements-releases/2023/07/21/fact-sheet-biden-harris-administration-secures-voluntary-commitments-from-leading-artificial-intelligence-companies-to-manage-the-risks-posed-by-ai/](https://arxiv.orghttps://www.whitehouse.gov/briefing-room/statements-releases/2023/07/21/fact-sheet-biden-harris-administration-secures-voluntary-commitments-from-leading-artificial-intelligence-companies-to-manage-the-risks-posed-by-ai/).
 [↩](https://arxiv.org/abs/#ax-cite-thewhitehousefactsheetbidenharris2023)

-  The White House.  G7 Hiroshima Leaders’ Communiqué, May 2023d.  URL [https://www.whitehouse.gov/briefing-room/statements-releases/2023/05/20/g7-hiroshima-leaders-communique/](https://arxiv.orghttps://www.whitehouse.gov/briefing-room/statements-releases/2023/05/20/g7-hiroshima-leaders-communique/).
 [↩](https://arxiv.org/abs/#ax-cite-thewhitehouseg7hiroshimaleaders2023)

-  Tirmazi, M., Barker, A., Deng, N., Haque, M. E., Qin, Z. G., Hand, S., Harchol-Balter, M., and Wilkes, J.  Borg: the next generation.  In Proceedings of the Fifteenth European Conference on Computer Systems, pp. 1–14, Heraklion Greece, April 2020. ACM.  ISBN 978-1-4503-6882-7.  [10.1145/3342195.3387517](https://arxiv.orghttps://doi.org/10.1145/3342195.3387517).  URL [https://dl.acm.org/doi/10.1145/3342195.3387517](https://arxiv.orghttps://dl.acm.org/doi/10.1145/3342195.3387517).

-  Trager, R., Harack, B., Reuel, A., Carnegie, A., Heim, L., Ho, L., Kreps, S., Lall, R., Larter, O., Ó hÉigeartaigh, S., Staffell, S., and Villalobos, J. J.  International Governance of Civilian AI: A Jurisdictional Certification Approach.  Whitepaper, Oxford Martin AI Governance initiative and Centre for the Governance of AI, August 2023.  URL [https://cdn.governance.ai/International_Governance_of_Civilian_AI_OMS.pdf](https://arxiv.orghttps://cdn.governance.ai/International_Governance_of_Civilian_AI_OMS.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-tragerinternationalgovernancecivilian202)

-  UK DSIT.  Capabilities and risks from frontier AI: A discussion paper on the need for further research into AI risk.  Technical report, DSIT UK, October 2023.  URL [https://assets.publishing.service.gov.uk/media/65395abae6c968000daa9b25/frontier-ai-capabilities-risks-report.pdf](https://arxiv.orghttps://assets.publishing.service.gov.uk/media/65395abae6c968000daa9b25/frontier-ai-capabilities-risks-report.pdf).
 [↩](https://arxiv.org/abs/#ax-cite-departmentforscienceinnovationandtechnol)

-  UK DSIT and Donelan, M.  Technology Secretary announces investment boost making British AI supercomputing 30 times more powerful, November 2023.  URL [https://www.gov.uk/government/news/technology-secretary-announces-investment-boost-making-british-ai-supercomputing-30-times-more-powerful](https://arxiv.orghttps://www.gov.uk/government/news/technology-secretary-announces-investment-boost-making-british-ai-supercomputing-30-times-more-powerful).

-  UK Government.  AI Safety Summit 2023 - GOV.UK, February 2024.  URL [https://www.gov.uk/government/topical-events/ai-safety-summit-2023](https://arxiv.orghttps://www.gov.uk/government/topical-events/ai-safety-summit-2023).
 [↩](https://arxiv.org/abs/#ax-cite-gov-uk2024)

-  UK Research and Innovation.  £300 million to launch first phase of new AI Research Resource, November 2023.  URL [https://www.ukri.org/news/300-million-to-launch-first-phase-of-new-ai-research-resource/](https://arxiv.orghttps://www.ukri.org/news/300-million-to-launch-first-phase-of-new-ai-research-resource/).

-  US BIS and US DOC.  Implementation of Additional Export Controls: Certain Advanced Computing Items; Supercomputer and Semiconductor End Use; Updates and Corrections, October 2023.  URL [https://www.federalregister.gov/documents/2023/10/25/2023-23055/implementation-of-additional-export-controls-certain-advanced-computing-items-supercomputer-and](https://arxiv.orghttps://www.federalregister.gov/documents/2023/10/25/2023-23055/implementation-of-additional-export-controls-certain-advanced-computing-items-supercomputer-and).
 [↩](https://arxiv.org/abs/#ax-cite-bureauofindustryandsecurity2023)

-  U.S. National Science Foundation.  Democratizing the future of AI R&D: NSF to launch National AI Research Resource pilot | NSF - National Science Foundation, January 2024.  URL [https://new.nsf.gov/news/democratizing-future-ai-rd-nsf-launch-national-ai](https://arxiv.orghttps://new.nsf.gov/news/democratizing-future-ai-rd-nsf-launch-national-ai).

-  U.S. Securities and Exchange Commission.  Retention of Records Relevant to Audits and Reviews, March 2003.  URL [https://www.sec.gov/rules/2003/01/retention-records-relevant-audits-and-reviews](https://arxiv.orghttps://www.sec.gov/rules/2003/01/retention-records-relevant-audits-and-reviews).

-  Vailshery, L. S.  Worldwide infrastructure as a service (IaaS) and platform as a service (PaaS) hyperscaler market share from 2020 to 2023, by vendor, February 2024.  URL [https://www.statista.com/statistics/1202770/hyperscaler-iaas-paas-market-share/](https://arxiv.orghttps://www.statista.com/statistics/1202770/hyperscaler-iaas-paas-market-share/).
 [↩](https://arxiv.org/abs/#ax-cite-vailsheryworldwideinfrastructureservice2)

-  Vanian, J.  HPE hacked by same Russian intelligence group that hit Microsoft, January 2024.  URL [https://www.cnbc.com/2024/01/24/hpe-hit-by-russian-intelligence-group-that-hacked-microsoft.html](https://arxiv.orghttps://www.cnbc.com/2024/01/24/hpe-hit-by-russian-intelligence-group-that-hacked-microsoft.html).

-  Ward, J. and Hu, K.  US antitrust inquiry targets OpenAI and Anthropic’s deals with Big Tech.  Reuters, January 2024.  URL [https://www.reuters.com/technology/ftc-launches-inquiry-into-generative-ai-investments-partnerships-2024-01-25/](https://arxiv.orghttps://www.reuters.com/technology/ftc-launches-inquiry-into-generative-ai-investments-partnerships-2024-01-25/).
 [↩](https://arxiv.org/abs/#ax-cite-wardusantitrustinquiry2024)

-  Weiss, M. L., McDonald, J., Bestor, D., Yee, C., Edelman, D., Jones, M., Prout, A., Bowne, A., McEvoy, L., Gadepally, V., and Samsi, S.  An Evaluation of Low Overhead Time Series Preprocessing Techniques for Downstream Machine Learning, September 2022.  URL [http://arxiv.org/abs/2209.05300](https://arxiv.orghttp://arxiv.org/abs/2209.05300).  arXiv:2209.05300 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-weissevaluationlowoverhead2022)

-  Weng, Q., Xiao, W., Yu, Y., Wang, W., Wang, C., He, J., Li, Y., Zhang, L., Lin, W., and Ding, Y.  MLaaS in the wild: Workload analysis and scheduling in Large-Scale heterogeneous GPU clusters.  In 19th USENIX symposium on networked systems design and implementation (NSDI 22), pp. 945–960, Renton, WA, April 2022. USENIX Association.  ISBN 978-1-939133-27-4.  URL [https://www.usenix.org/conference/nsdi22/presentation/weng](https://arxiv.orghttps://www.usenix.org/conference/nsdi22/presentation/weng).
 [↩](https://arxiv.org/abs/#ax-cite-wengmlaaswildworkload2022)

-  Whittlestone, J. and Clark, J.  Why and How Governments Should Monitor AI Development, August 2021.  URL [http://arxiv.org/abs/2108.12427](https://arxiv.orghttp://arxiv.org/abs/2108.12427).  arXiv:2108.12427 [cs].
 [↩](https://arxiv.org/abs/#ax-cite-whittlestonewhyhowgovernments2021)

-  Whittlestone, J., Avin, S., Heim, L., Anderljung, M., and Sastry, G.  Response to the UK’s Future of Compute Review.  Technical report, Centre for the Governance of AI, March 2023.  URL [https://www.governance.ai/research-paper/response-to-the-uks-future-of-compute-review](https://arxiv.orghttps://www.governance.ai/research-paper/response-to-the-uks-future-of-compute-review).

-  Wikipedia contributors.  Hardware performance counter, August 2023.  URL [https://en.wikipedia.org/w/index.php?title=Hardware_performance_counter&oldid=1169157291](https://arxiv.orghttps://en.wikipedia.org/w/index.php?title=Hardware_performance_counter&oldid=1169157291).
 [↩](https://arxiv.org/abs/#ax-cite-enwiki-1169157291)

-  Williams, S., Waterman, A., and Patterson, D.  Roofline: An Insightful Visual Performance Model for Floating-Point Programs and Multicore Architectures, October 2008.  URL [https://people.eecs.berkeley.edu/~kubitron/cs252/handouts/papers/RooflineVyNoYellow.pdf](https://arxiv.orghttps://people.eecs.berkeley.edu/~kubitron/cs252/handouts/papers/RooflineVyNoYellow.pdf).

\## Footnotes

- For a discussion of compute as a governance node, see [[138](https://arxiv.org/abs/#ax-ref-sastrycomputingpowergovernance2024)]. [↩](https://arxiv.org/abs/#ax-fnref-1)

- Our focus is on the entities that own and operate data centers, prioritizing the “legal entity” level of abstraction over the physical locations or “data centers” themselves. [↩](https://arxiv.org/abs/#ax-fnref-2)

- This discussion extends to services that offer hardware access with sufficient flexibility for customer-defined usage, which may occasionally encompass certain Platform-as-a-Service (PaaS) offerings. However, our emphasis is on scenarios in which usage surpasses certain AI compute thresholds that are of relevance for frontier AI. In contrast, services providing access to pre-configured AI models (Software-as-a-Service, or SaaS) fall outside our defined scope of compute providers. (The suggested governance capacities could still help if the regulation of these services is desired.) [↩](https://arxiv.org/abs/#ax-fnref-3)

- The term “cloud” is more associated with a specific business model rather than the underlying activity of providing compute resources. For this context, we prefer the term “compute providers” to accurately reflect the focus on the provision of computing power. This choice also allows us to include entities that predominantly provide their computational resources internally (e.g., Meta [[89](https://arxiv.org/abs/#ax-ref-janardhanreimaginingourinfrastructure202)]) within the scope of our discussion. [↩](https://arxiv.org/abs/#ax-fnref-4)

- The most notable hyperscalers include Microsoft Azure, Amazon Web Services (AWS), Apple, Bytedance, Meta, Oracle, Alibaba, Tencent, and Google Cloud [[164](https://arxiv.org/abs/#ax-ref-vailsheryworldwideinfrastructureservice2)]. [↩](https://arxiv.org/abs/#ax-fnref-5)

- Many prominent AI companies either operate as hyperscalers themselves or maintain strategic partnerships with them. For example, OpenAI’s collaboration with Microsoft [[108](https://arxiv.org/abs/#ax-ref-microsoftcorporateblogsmicrosoftopenaiex)], and Anthropic’s associations with AWS and Google Cloud [[11](https://arxiv.org/abs/#ax-ref-amazon-cominc-amazonanthropicannounce202), [16](https://arxiv.org/abs/#ax-ref-anthropicanthropicpartnersgoogle2023)] , exemplify such relationships. [↩](https://arxiv.org/abs/#ax-fnref-6)

- These relationships and the concentrated market for large-scale compute have given rise to antitrust and competition concerns, drawing scrutiny from regulators, including an ongoing inquiry by the US Federal Trade Commission [[63](https://arxiv.org/abs/#ax-ref-federaltradecommissionftclaunchesinquiry)] and an investigation by the UK Competition and Markets Authority [[109](https://arxiv.org/abs/#ax-ref-milmocmainvestigateuk2023)]. While we acknowledge the need to carefully analyze how enhanced regulatory measures may impact competition issues in the sector, we expect the impact to be limited and not broadly significant. This is due to the focused scope of the measures, targeting only those compute providers capable of supporting large-scale AI infrastructure and customers who are running large-scale workloads costing tens to hundreds of millions of dollars or more. A detailed discussion of these antitrust concerns requires broader analysis and is beyond the scope of this paper. [↩](https://arxiv.org/abs/#ax-fnref-7)

- Also see Section 2.1 of [[14](https://arxiv.org/abs/#ax-ref-anderljungfrontierairegulation2023)]. [↩](https://arxiv.org/abs/#ax-fnref-8)

- In [section 5.2](https://arxiv.org/abs/#ax-sec-governance-challenges), we elaborate on privacy and confidentiality considerations, emphasizing that our proposed regulatory measures are specifically aimed at key actors in frontier AI development, rather than being broadly applied to the entire customer base of compute providers, such as individuals. [[86](https://arxiv.org/abs/#ax-ref-heimaccessingcontrolledai2023)] and [[53](https://arxiv.org/abs/#ax-ref-lennartoversightfrontierai2023)] also discuss the idea of “above-threshold compute usage.” [↩](https://arxiv.org/abs/#ax-fnref-9)

- Especially, as some of the currently proposed measures may be overly broad, potentially violating confidentiality principles. [↩](https://arxiv.org/abs/#ax-fnref-10)

- The size of the customer base of compute providers varies significantly. Typically, compute providers offer their services to a wide range of entities, with most usage falling outside the scope of our primary concern in this paper (see [section 1](https://arxiv.org/abs/#ax-sec-introduction)). Nonetheless, our analysis also includes large compute owners who exclusively use their resources internally. For example, a major technology company cannot circumvent the guidelines proposed in this discussion by merely categorizing its usage as “internal provisions” or not identifying itself as a “customer.” This approach ensures comprehensive coverage of all relevant forms of compute provision for frontier AI. [↩](https://arxiv.org/abs/#ax-fnref-11)

- ITAR compliance requires arms-related data to be secured from foreign persons. There is no formal certification process for cloud providers, although many choose to be audited by a third-party organization certified under the Federal Risk Authorization Management Program (FedRAMP) [[39](https://arxiv.org/abs/#ax-ref-codeoffederalregulations22cfrpart)]. [↩](https://arxiv.org/abs/#ax-fnref-12)

- Such regulations could be enforced by chartering or registration (for example, firms cannot accept federally insured deposits unless chartered as a bank, credit union, or thrift) [[41](https://arxiv.org/abs/#ax-ref-congressionalresearchservice2023)], or tied to a license to acquire specialized AI compute hardware, as is already in place for the export of certain equipment from US companies [[13](https://arxiv.org/abs/#ax-ref-amd)]. [↩](https://arxiv.org/abs/#ax-fnref-13)

- An example of this could be in the event of an AI system malfunctioning and causing financial loss or physical harm, record keeping allows for the traceability of the AI’s development and deployment process, helping to identify the origin of the fault (forensics) and parties responsible (attribution). [↩](https://arxiv.org/abs/#ax-fnref-14)

- “Under the directive, owners and operators of data centers with 500 kilowatts or more of installed IT capacity will need to report their 2023 energy performance by May 15, 2024. That includes statistics about installed power, incoming and outgoing data traffic, total data stored and processed, energy consumption, power usage, temperature set points, waste heat utilization, and use of renewable energy.” [[94](https://arxiv.org/abs/#ax-ref-korolov2023)] [↩](https://arxiv.org/abs/#ax-fnref-15)

- Hardware-enabled mechanisms for verification and enforcement of governance regimes are discussed in [[1](https://arxiv.org/abs/#ax-ref-aarnesecuregovernablechips2024)] and [[95](https://arxiv.org/abs/#ax-ref-kulphardwareenabledgovernancemechanisms2)]. [↩](https://arxiv.org/abs/#ax-fnref-16)

- For an example of what such standards might look like, see security requirements in the Federal Risk Authorization Management Program (FedRAMP). FedRAMP assigns different levels of requirements depending on the sensitivity of the use case [[64](https://arxiv.org/abs/#ax-ref-baselines)]. [↩](https://arxiv.org/abs/#ax-fnref-17)

- See Section 3.C of [[138](https://arxiv.org/abs/#ax-ref-sastrycomputingpowergovernance2024)]. [↩](https://arxiv.org/abs/#ax-fnref-18)

- Interviews conducted between October 2023 and February 2024 [↩](https://arxiv.org/abs/#ax-fnref-19)

- For example, to meet the AI Executive Order’s reporting requirement of 1026 operations for a training run, a customer will need access to around 60,000 cutting-edge AI accelerators (Nvidia H100) for 90 days, assuming a utilization of 34%. [↩](https://arxiv.org/abs/#ax-fnref-20)

- “Utilization” in this context refers to the usage as a proportion of the node’s theoretical peak computational performance. [↩](https://arxiv.org/abs/#ax-fnref-21)

- [[38](https://arxiv.org/abs/#ax-ref-choitoolsverifyingneural2023)] propose a method for verifying training data, but it requires sharing of sensitive data with the verifier. Making the scheme fully privacy-preserving is discussed but left for future work by the authors. [↩](https://arxiv.org/abs/#ax-fnref-22)

- Threshold as stipulated by the AI Executive Order. Note it is subject to updates. [↩](https://arxiv.org/abs/#ax-fnref-23)

- In this case, models trained on with more than 1026 operations and occurring on frontier infrastructure. [↩](https://arxiv.org/abs/#ax-fnref-24)

- The proposed rules also require US IaaS providers and their foreign resellers to verify the identities of all foreign customers. This broader measure has come under criticism for being ineffective in addressing cyber threats, giving rise to privacy issues, and impacting the competitiveness of US compute provision [[116](https://arxiv.org/abs/#ax-ref-nationalsecuritytelecommunicationsadviso)]. This paper does not engage in analysis of this broader measure, and instead focuses on the subsection of compute for frontier AI. As outlined in the introduction, this narrower focus only captures a small number of AI firms and compute providers, which mitigates much of the concern around regulatory burden (see discussion in [section 1.4](https://arxiv.org/abs/#ax-sec-limitations-and-future-research-directio). [↩](https://arxiv.org/abs/#ax-fnref-25)

- Note, however, that strong cyber security at the infrastructure level alone is insufficient. AI firms will still need to implement and maintain strong cyber security practices on their own systems ([section 3.1](https://arxiv.org/abs/#ax-sec-security)). [↩](https://arxiv.org/abs/#ax-fnref-26)

- For example, techniques to reduce the memory footprint of training are an active area of research (e.g., [[51](https://arxiv.org/abs/#ax-ref-dettmersllmint88bit2022)]). [↩](https://arxiv.org/abs/#ax-fnref-27)

- A customer might attempt to hide the fact that they are engaging in AI training by using non-standard number representations, affecting traffic to/from outside networks, or deliberately using less efficient algorithms with different workload characteristics, such as under-utilizing memory or computation. However, the more a customer attempts to disguise workloads in this fashion, the greater the cost in terms of lost efficiency. In the context of frontier model training, where a single workload can cost tens of millions of dollars, perhaps these losses could be significant enough to make many forms of obfuscation too costly. [↩](https://arxiv.org/abs/#ax-fnref-28)

- In the event of adversarial actors attempting to obscure their activities, it should be noted that such gaming of the system typically comes at a cost, potentially affecting the efficiency or performance of the AI system being trained. Compute providers and regulators will need to consider whether the penalties for non-compliance are substantial enough to deter such behavior, weighing if the cost of circumventing outweighs the cost of compliance. [↩](https://arxiv.org/abs/#ax-fnref-29)

- Scaling laws suggest that achieving substantial enhancements in performance on downstream tasks necessitates exponential increases in training compute. This principle underscores that compute investments grow exponentially for comparatively linear improvements in task performance [[128](https://arxiv.org/abs/#ax-ref-owenhowpredictablelanguage2024)]. [↩](https://arxiv.org/abs/#ax-fnref-30)

- The complexity of verification processes is further increased by the diversity of national ID and business registration regulations when considered in an international context (e.g., India has more advanced ID verification systems than other countries [[88](https://arxiv.org/abs/#ax-ref-indiasministryofelectronicsandinformatio)]). [↩](https://arxiv.org/abs/#ax-fnref-31)

- E.g., zero-knowledge proofs that regulators can trust to verify compute usage without having direct access to data centers or sensitive data. [↩](https://arxiv.org/abs/#ax-fnref-32)

- Typically a node and a server are equivalent, but “server” refers to the physical hardware, while a “node” is a unit of computational resources within the cluster’s infrastructure. [↩](https://arxiv.org/abs/#ax-fnref-33)

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud)*
