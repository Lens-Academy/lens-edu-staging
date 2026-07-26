---
title: "Distillation of Neurotech and Alignment Workshop January 2023"
author:
  - "lisathiergart"
  - "Sumner L Norman"
source_url: "https://www.lesswrong.com/posts/KQSpRoQBz7f6FcXt3/distillation-of-neurotech-and-alignment-workshop-january-1"
published: 2023-05-22
created: 2026-07-09
accessed: 2026-07-09
description: "Disclaimer: This post is preliminary and doesn't yet fully align with the rigorous standards we typically aim for in LessWrong publications. It recap…"
tags:
  - "article-importer"
---{++{"author":"Luc's AI","timestamp":1785090674217}@@

%%
Add discussion note here:

...

%%++}

**Disclaimer:** This post is preliminary and doesn't yet fully align with the rigorous standards we typically aim for in LessWrong publications. It recaps the dynamic discussions from the neurotech for AI alignment workshop and therefore does not necessarily represent any single participant’s or author’s viewpoint. Shared ahead of the Foresight WBE workshop, our intent is to foster enriching discussion among participants. We welcome your input as we continue refining these insights. 

# Introduction

This document reviews key insights from a January workshop exploring the potential of Neurotech to contribute to the [AI alignment problem.](https://drive.google.com/file/d/1uK7NhdSKprQKZnRjU58X7NLA1auXlWHt/view)  Neurotech, or neurotechnology, refers to the set of tools and methods designed to enhance understanding of the brain, manipulate its function, or interface directly with neural circuits, often for therapeutic or augmentation purposes. The AI alignment problem is the challenge of ensuring that the behavior of an artificial (general) intelligence system is in line with human values and intentions.

The workshop, attended by 16 technical researchers and domain specialists, aimed to jointly map out whether and how neurotech can be useful towards alignment. Our core goal was to cast the net wide for all possible solutions, with an emphasis on those relevant to shortened alignment timelines. This initiative was a follow-up to the Paris Foresight Vision Weekend in November 2022, where it became evident that Neurotech-based approaches to alignment warranted further investigation. The two-hour interactive workshop aimed to compile a comprehensive list of potential approaches and prioritize them based on technical feasibility and timeline relevance.  

The workshop kicked off with a keynote presentation from David Dalrymple that laid the groundwork for participant discussion and defined key working definitions. This was followed by a brainstorming session, break-out room discussions, cluster identification and idea sorting, preliminary cluster prioritization (based on alignment impact, feasibility, timeline, and cost), and analysis of the prioritization results. David's keynote included a figure illustrating a potential breakdown of research intersecting Brain-Computer-Interface and Alignment.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/KQSpRoQBz7f6FcXt3/xokfosgerm0e28ctyrfi)

Several **key insights** from the workshop include 

1.  Workshop participants brainstormed together, identifying six clusters of neuro-based alignment approaches: 
    1.  BCIs to extract human knowledge
    2.  neurotech to enhance humans
    3.  understanding human value formation
    4.  cyborgism
    5.  whole brain emulation
    6.  BCIs creating a reward signal. 
2.  Each cluster aims to align AI with human values but with highly separable/unique approaches. 
3.  These categories likely don’t cover all potential approaches. In this post, we map these approaches with the hope that future workshops can explore and extrapolate to other less-common approaches that could hold potential.
4.  The workshop identified trends that agreed with commonly held assumptions. For example, participants found that complex technologies take longer to develop but have a greater potential impact on AI alignment. The relationship between cost and the other variables remains unclear. Future workshops should address cost and expected value to better guide investment in the space.
5.  Neurotech hardware development faces potentially long timelines that may fall behind the advent of AGI, which presents a major risk for all neurotech-based tradeoffs. 
6.  Neurotech for AI safety is in an early phase with high uncertainty. During this phase, exploring various potential solutions, even unlikely ones, is valuable. This can lead to crucial insights and guide more focused investments, increasing the chances of finding effective AI alignment strategies.
7.  The balance between increasing AI capabilities and alignment impact through neurotechnologies is uncertain. If advances in capability outpace advances in alignment, they may be counterproductive. Technology confidentiality can mitigate this risk but adds to development complexity.

# Outline of Top 6 Clusters

After the ideation & brainstorming phase, participants were tasked with identifying “clusters” of approaches. This task hoped to distill many ideas into broad categories that spanned most of the proposed solution set with fewer ideas to interrogate over the second half of the workshop. The participants defined the following six categories. 

1.  _BCIs to extract human knowledge_ 
    1.  **Summary:** We already create AI systems in our image. We regularly train AI systems to imitate human outputs, e.g. text, images, etc. These outputs, however, are only artifacts of human cognition and represent a tiny fraction of our intentions, thought processes, and values. This cluster intends to use BCI to expand the utility of information artifacts of human cognition beyond conventional forms. 
    2.  **Example approach 1:** BCI is used to build an ontology of human values and bridge that ontology to AIs
        1.  **Example approach 1a (unsupervised):** BCI data is used to better interpret and define key human values in an abstract and global manner that is interpretable by AI. These might be inserted into models by methods including [activation engineering](https://www.lesswrong.com/posts/5spBue2z2tw4JuDCx/steering-gpt-2-xl-by-adding-an-activation-vector#6__The_Eiffel_Tower_is_in_Rome) which can steer models. This could be achieved using machine learning to infer latent “value spaces” from an extremely large corpus of human neurodata. Unsupervised methods may be more successful because they are less likely to break with future models (or change in human moral values).
        2.  **Example approach 1b (supervised):** A training dataset (a large neurodata corpus) would be curated and labeled corresponding to the traits and values related to the time-varying brain states. This enables the model to learn to recognize and incorporate these values into its output. 
        3.  **Example approach 1c:** BCI is used to better understand the neural basis for social behavior and/or moral emotions.
2.  [_Neurotech to enhance humans generally_](https://www.lesswrong.com/posts/vEtdjWuFrRwffWBiP/we-have-to-upgrade)
    1.  **Summary:** We use neurotechnology to enhance human capabilities to stay ahead of the AI curve and/or to bootstrap our ability to generate solutions to the alignment problem. 
    2.  **Example approach 1:** Enhance human AI researchers using brain-to-brain communication, e.g. increase cooperation by sharing semantic and contextual information with concepts. 
    3.  **Example approach 2:** Generic neurotech cognitive enhancement accelerates AI safety research
3.  _Understanding how humans form values_
    1.  **Summary:** This cluster looks at studying how humans form values to better train agents to form their values similarly.
    2.  **Example approach 1:** Investigate Eliezer Yudkowsky's claim that the human brain contains some innate cognitive structures or mechanisms that contribute to the development of moral reasoning. If correct, build this structure or mechanism into AGI and train it similarly to how humans learn. 
4.  _Cyborgism_[^1]
    1.  **Summary:** Cyborgism is the idea of using technology such as AI to enhance human abilities and potential, for example by interleaving human and AI-generated cognition. Cyborgism could enable more effective communication of human values and preferences to the AI, and also enable the development of more transparent and explainable AI systems, which may help ensure that AI systems are used in ways that are beneficial to humanity. [^2]
    2.  **Example approach 1:** Train a 'brain embeddings to \<behavior>' model, then use recordings of humans thinking about positive stuff to condition the model's behavior.
        1.  Analogy: we currently use 'text to \<behavior>' models, then use text to condition the model's behavior. Presumably, brain embeddings will provide a more precise transfer of complex values than will text.
5.  _Whole brain emulation_
    1.  **Summary:** Whole brain emulation (WBE) aspires to capture the functionality of biological/human brains by emulating its structure and function on a computational substrate. Despite advancements, the feasibility of WBE remains debatable, and it carries risks like sampling bias and the exacerbation of inequalities if access is restricted to a few individuals.
    2.  **Example approach 1:** The computational substrate model inherits all of human cognition including its values. Together with access to data and processing unlimited by biology, WBE agents are competitive with the AGI.
    3.  **Example approach 2:** group-aggregated whole-brain emulation, where a team of uploaded humans could work together to solve the problem of AGI alignment. This could potentially end the acute risk period and provide a collective intelligence that is better equipped to solve the alignment problem.
6.  _BCIs to create a “reward signal”_
    1.  **Summary:** Brain-computer interfaces (BCIs) can potentially be used to create a "reward signal" that can be used to align the behavior of artificial general intelligence (AGI) systems with human values.
    2.  **Example approach 1:** Solve "value loading" by measuring "well-being" through humanity-scale deployment of accessible BCI. In other words, the BCI translates human values into a form that can be incorporated into the design and training of AI systems. This can happen asynchronously.
    3.  **Example approach 2:** Human cognition becomes the (live/closed loop) reward signal to a reinforcement learning based AGI agent: Wide-scale adoption of neurotechnology allows for AI to test humans' responses/thoughts in response to hypothetical actions.

**What clusters were not represented during the workshop?**

Due to the workshop’s restricted time of 2 hours, it’s likely that this is not yet an exhaustive list of possible clusters. To help identify technology clusters that may have been missed, we categorized approaches in a hierarchy by (1) information flow, i.e. from humans to AIs or from AIs to humans; (2) Ability; (3) Benefit to AI alignment (Fig. 1). 

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/KQSpRoQBz7f6FcXt3/rbddqt9oabeyuffp9rhr)

**Fig. 1 Cluster Map.** Technologies can be broken down into a hierarchy of categories. This structure may help to identify clusters that were not discussed during the workshop.

# Quantitative Assessment of Trade-offs

To assess the key trade-offs between competing strategies to neuro-based alignment, we identified four critical variables: (1) timeline, (2) cost, (3) feasibility, and (4) impact. The working definitions of these four variables (exactly as they were provided to workshop participants) were:

**Timeline:** Assuming the neuroscience progresses very well, how long will it take to develop the interfaces (including: hardware, software, and methods) that make this possible? note: AI timelines are a controversial, but separable, topic. The goal here is to rank order each cluster from fastest to slowest (fastest = 1, slowest = n).

**Cost:** Rank each cluster from least expensive to most expensive (least = 1, most = n).

**Feasibility:** Assuming that sufficiently high performance neurotechnologies and AI methods are available, what’s the likelihood that each cluster's approach is feasible (including: technical, neuroscience, understanding of alignment; least feasible = 1, most feasible = 5)?

**Impact on AI alignment:** Assuming each approach was guaranteed to be successful, rank order the magnitude of positive impact on AI alignment (ignoring alignment timelines; worst = 1, best=5).

To establish a consensus on these variables, the workshop was divided into self-selected working groups. Each group had the task of rank-ordering technology clusters for each of these four key variables. The aim was to discern trends and identify outlier clusters/strategies.  

## **An analysis of key variable trends**

  
The relationships between feasibility, timeline, and impact on AI (See Fig. 2) align with commonly held assumptions. For instance, technologies that are more complex to develop were anticipated to take longer, suggesting an inverse correlation between feasibility and timeline (Fig. 2A). Similarly, technologies expected to yield a greater impact on AI alignment were predicted to require more development time (Fig. 2b) and were negatively correlated with feasibility. In other words, participants found that the technologies that were most likely to positively impact AI alignment were also the ones that were least feasible and would take the longest to develop.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/KQSpRoQBz7f6FcXt3/bcpeslpn1a2xvrojd5y6)

**Fig. 2| Comparison on key variables.** **A.** Feasibility vs. timeline. Technology clusters that were deemed less feasible were also presumed to take longer to develop. **B.** Impact on AI vs. timeline. Technology clusters that were seen as having a larger potential impact on AI alignment were also presumed to take longer to develop. **C.** Impact on AI vs. feasibility. Technology clusters that were deemed more feasible were seen to be less likely to have an impact on AI alignment. Green trend lines represent high correlations (R2 ≥ 0.4318) and red represent low correlations.

### **Cyborgism: an exception?** 

Interestingly, Cyborgism appeared to diverge from the trends of the other approaches. Despite being consistent with the notion that less feasible technologies take longer to develop, it was not perceived to have a proportionate impact on AI alignment. Essentially, even though cyborgism might require substantial development time and be low in feasibility, its success wouldn’t necessarily yield a significant impact on AI alignment.

### **Cost**

The relationship between cost and the other three factors remained ambiguous. (Fig. 3). No discernible trends were observed between cost and timeline or impact on AI. There was a negative correlation between cost and feasibility, e.g. highly feasible solutions cost less and less feasible solutions cost more to develop. However, these results should be interpreted with caution. During this portion of the workshop, participants were self-selected into breakout rooms, where each room was tasked with ranking technology clusters for a single variable. No one chose to join the “Cost” breakout room. Instead, we (the organizers) quickly ranked the technology clusters with respect to cost. _We include the results for completeness but encourage the reader to interpret these results with caution_ and suggest that future workshops revisit this topic.

![](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/KQSpRoQBz7f6FcXt3/bwpsuhdi5jvxzbgqkvpo)

**Fig. 3| Comparison of cost and other variables.** **A.** timeline vs. cost had no clear trend. **B.** Cost vs. feasibility. Technology clusters that were seen as being less feasible were also seen as higher cost. **C.** Cost vs. impact on AI had no clear trend. Green trend lines represent high correlations (R2 ≥ 0.4318) and red represents low correlations.

In summary, the exercise underscored the complexity of the trade-offs involved in pursuing different strategies. It is hoped that these insights will contribute to a more informed and nuanced discussion on the path forward in the neurotech-based alignment space.

# Discussion of Key Technical and Strategic Trade-offs 

## **Aligning Neurotech and AGI Timelines**

Participants noted that the most impactful neurotechnologies for AGI alignment are likely the most complex and thus would require longer development times. This poses a risk that some of these technologies may not be ready before the anticipated emergence of AGI. Timelines and associated risks leading to AGI are still disputed. However, there was agreement that the longer the R&D cycle relative to AGI's progression, the less likely the technology will make a significant contribution.

Several strategies emerged from the discussion to address this issue:

1. **Better Estimation:** Improve estimates of AGI's arrival and prioritize acceleration of those neurotechnologies that could realistically be developed beforehand. This task is inherently challenging due to the difficulty in making precise estimates, and errors could negatively impact neurotechnology development.

2. **Slow AGI Progress:** Intentionally delaying AGI timelines could provide neurotechnology researchers with additional development time. However, this strategy necessitates community-wide cooperation that contradicts existing financial and personal incentives, making it a difficult proposition.

3. **Scale Resources according to expected value:** Allocate resources to each neurotechnology's development proportionally to its expected value, considering factors like impact on alignment, development timeline, cost, etc.

4. **More efficient use of resources:** Resource allocation should ideally include careful evaluation of the trade-offs between timeline, cost, feasibility, and impact. It will be critical to reduce redundancy and the risk of investing heavily in less feasible or longer-term projects. A strategic, trade-off-informed allocation of resources could maximize the effectiveness of our efforts toward AGI alignment. However, the attendees stressed that it is important to continue investigating all of the proposed neurotechnology clusters because of the unknown potential to significantly mitigate the risks posed by AGI.

5. **Expand resources:** The benefits of these complex neurotechnologies extend beyond AGI alignment. For example, many neurotechnologies have wide-ranging applications in healthcare, which could attract investments outside of the AGI alignment funding structures and community. However, caution is required to avoid potential distractions if the researchers' goals diverge from those of the investors.

## **Feasibility & technical progress for top clusters** 

The feasibility of neurotechnology faces significant scientific and technological risks, especially when considering the concurrent advances and projected timelines in AI. In the breakout session, participants rank-ordered the feasibility (including: technical, neuroscience, understanding of alignment) of the different approaches. In addition, there was discussion about technical feasibility in the breakout session and asynchronous communication after the workshop. Here, we’ll share some of those thoughts.

There are two primary neurotechnology strategies. **The bottom-up approach** targets the structure and function of the central nervous system at its lowest functional level (e.g. a synapse), and scales it to an entire brain. Connectomics are tackling this issue, with large scale [efforts](https://e11.bio/) scoped to accelerate large scale connectomic research. Nevertheless, these approaches might not scale to the entire human brain before AGI arrives. **The top-down approach** measures brain function, often _in vivo_ and in human participants at the scale of the entire brain, but with limited resolution. For example, functional MRI captures brain function with spatial resolutions of ~1 mm and temporal resolutions of ~1 sec. Although orders of magnitude away from single neuron activity, they still produce impressive results (e.g. reconstructing [vision](https://www.youtube.com/watch?v=nsjDnYxJ0bo) or [language](https://www.nature.com/articles/s41593-023-01304-9.epdf?sharing_token=eRF26q0CEKjXJe_xiwrYptRgN0jAjWel9jnR3ZoTv0NG3whxCLvPExlNSoYRnDSfIOgKVxuQpIpQTlvwbh56sqMXN0lZ9RZmdNtl6FGOIAG4FCtIHW1KJlM6y8opjMflLwC5y8nr_2Pf8epQHcEJyXmLOJ5iSW1y1NYLOhz2IXPFyCPrrwPR_3C2ZS70Bg7hvFhEqMbYO3BgDGvsg3V_0w%3D%3D&tracking_referrer=www.npr.org)). This demonstrates the power and promise of top-down neurotechnologies: they create useful results throughout their development that could contribute to alignment.

Top-down neurotech shows promise for AI alignment, but methods such as [electrophysiology](https://neuralink.com/), which invade brain tissue, are problematic. Techniques need to record cellular activity without causing damage, and current "[butcher numbers](https://www.youtube.com/watch?v=AwXnRTNLAhw)" (ratio of damaged to recorded cells) are unacceptably high for whole-brain scaling. Techniques based on optics and/or ultrasound offer promising, less-invasive alternatives. Optical techniques offer high spatial and temporal resolution. Unfortunately, photons scatter in tissue, limiting recording depth. Ultrasound penetrates soft tissue efficiently and is [highly sensitive](https://www.sciencedirect.com/science/article/pii/S0896627321001513) to neuronal function. It's diffraction-limited to ~100 micron resolution, but [super-resolution](https://www.nature.com/articles/s41592-022-01549-5) and [genetic engineering](https://patents.google.com/patent/US20230109152A1/en) techniques are improving spatial resolution and enabling more specific functional measurements. Other approaches based on different biophysical sources of contrast (e.g., [magnetics](https://quspin.com/)), delivery of these approaches to the brain through novel means (e.g., [intravascular](https://synchron.com/)), or the combination of multiple techniques, may also contribute to progress in neurotech for AI alignment.

Most of the clusters that the workshop participants identified include approaches that require neural measurements in behaving humans (1. BCIs to extract human knowledge, 2. Neurotech to enhance humans generally, 4. Cyborgism, 5. Whole brain emulation, and 6. BCIs to create a reward signal), which is most readily achieved using top-down techniques. Thus, advances in top-down neurotechnologies in one category would also likely benefit approaches in many others.

## **Tradeoff: Investment for R&D in Neurotech approaches vs non-neurotech alignment approaches**

Given current funding limits for alignment research, what is the impact of investing in neurotech-based approaches with alignment resources? As a comprehensive cost overview doesn’t exist, we’ll offer a qualitative examination, focusing on WBE as an example.

WBE may attract substantial commercial investment thanks to its potential for applications in health care, entertainment, lifestyle, well-being and longevity. WBE could develop independently of alignment investment or in parallel by commercial interest groups. 

A potential drawback of non-alignment investment in WBE is the possible disregard for alignment-specific issues. For instance, should WBE development be confidential or exclusive? While commercial interest groups might independently pursue WBE, investments from the alignment community could notably accelerate its development. The credibility of this assertion depends on a more detailed understanding of the key technical obstacles for WBE.

A distinguishing factor for neurotech approaches is their reliance on hardware innovation. The quality of brain data is tied to the sophistication of recording equipment. Invasive devices, due to concerns about biocompatibility, device lifespan, and safety, require lengthy and expensive development. Unlike software innovation's rapid progress, hardware innovation is historically slower.

Another significant contributor to overall development cost and time is compliance with regulatory guidelines, such as ethical review and potential new medical legislation, before legally using WBE technology. This difference between neurotech and non-neurotech approaches is noteworthy, as the latter less frequently require ethical evaluation in the current legal landscape.

##   
**Tradeoff on Investment: Maximally Accelerating a Single Technology vs. Diversifying Investment**

When contemplating resource allocation in AI alignment, a key strategic question arises: Should investment be concentrated in a single expensive technology, like WBE, to maximize its R&D speed, or should resources be spread across multiple approaches, each with a sub-maximum R&D pace? (This tradeoff is mostly only valid under the assumption of finite investment resources relative to cost, which does seem likely soon.)

Maximizing resources toward one approach could potentially reduce timelines, accelerate breakthroughs, and increase the probability of this technology being ready for deployment when AGI becomes a reality. In the case of WBE, it could also foster advancements in related fields, such as neuroscience and medicine, due to its wide-reaching application, which could foster further investment, which would (ideally) create a virtuous cycle of investment, progress, investment, and so on. On the other hand, this approach carries significant risks. Each of the approaches discussed here is fraught with uncertainties, both technical and scientific, and participants agreed that WBE was among the most uncertain. Concentrating resources in a single avenue risks total failure if the technology proves infeasible, and other approaches’ development is significantly behind.

Investing in a diverse portfolio of alignment approaches can mitigate this risk. This strategy hedges against the failure of any single approach. Given the high uncertainty surrounding each approach and the many inherent scientific and technological risks of each, exploration of many paths is likely advisable above exploiting a single approach with more resources and increasing the overall chance of success in the field of AI alignment. In summary, the choice between maximizing the acceleration of a single technology and diversifying investment across multiple approaches hinges on a complex interplay of factors. These include the perceived AGI timeline, the potential of each technology for alignment, the associated development risks, and the counterfactual impact of investment. As such, careful and considered strategic decision-making is vital.

## **Balancing Alignment Impact and Capabilities Acceleration**

It’s unclear how each of these technologies will contribute to AI safety vs. general AI capabilities. If the capability increase is larger than the alignment increase, it should possibly not be considered an alignment approach. For neurotechnologies, the outcomes and potential uses toward either end seem particularly uncertain. Additionally, the necessity of maintaining technology confidentiality for alignment impact is a crucial factor. In some instances, confidentiality might be unachievable due to potential parallel development by other industry stakeholders or the need for substantial investment that necessitates involving funders interested in accessing the technology.

# Prioritization Summary 

Given the current scarcity of highly effective alignment strategies, the exploration of neurotech-based approaches is undeniably valuable. However, the substantial R&D uncertainty and high costs associated with neurotechnologies, compounded by the undefined nature of their potential impact, necessitate a deeper investigation into trade-offs and technical obstacles before substantially shifting resources away from any given set of approaches to accelerate another. This consideration is crucial, especially when weighing investment decisions between neurotech and potentially more cost-impact-efficient non-neurotech approaches.

Assuming resources are finite and sufficiently limited such that not all approaches can be maximally developed in parallel (which they currently are), we can draw on decision theory principles to frame these strategies as an exploration-exploitation trade-off. Exploration is optimal in the early stages of a problem, when uncertainty is high and information is scarce. Given the nascent state of neurotech-based AI alignment, we're in precisely such an exploration phase.It is therefore likely valuable to investigate a range of potential solutions, even those that seem unlikely or are less understood. Clusters like neuro & interpretability are affordable and might yield crucial insights. This knowledge can then inform more targeted investments (exploitation), streamlining resource spend and improving the probability of discovering effective and timely AI alignment strategies.

On the other hand, it may be possible that the total pot of resources is substantially increased as the general public gains awareness of the risks of AI. In particular, if public sentiment supports the idea that AGI timelines are sufficiently short, this further increases the probability of increased resources. For example, if legislators (reflecting public sentiment) are convinced of AGI timelines that are within typical voting cycles, political structures will be motivated to fund alignment research. This kind of increase in resources adds an interesting dimension to the strategic discussion. For example, we could explore many alignment strategies in parallel. However, there may be diminishing returns with increased funding, and there might be a talent scarcity problem wherein increased funding doesn’t necessarily equate to an increase in skilled researchers, again emphasizing the need for strategic distribution of resources. Additionally, navigating socio-political implications could become increasingly difficult with increased public and government involvement. 

# Summary & Next Steps 

Neurotech-based AI alignment strategies and their potential impact are in early stages but hold promise as exploratory solutions. If you feel that you have insights to contribute to further discussions or would like to participate in future workshops, we encourage you to get involved. Given the complexity, multi-disciplinary, and nascent nature of these approaches, additional perspectives are particularly valuable at this stage. We also host a slack space for online discussions which we welcome new members to. To reach out, feel free to respond through LessWrong or contact us directly at [sumner@convergentresearch.org](mailto:sumner@convergentresearch.org) or [lisa.thiergart@gmail.com](mailto:lisa.thiergart@gmail.com).

# Acknowledgements

We like to express our gratitude to all the participants of the Neurotech and AI alignment workshop. Thank you for devoting your time and contributing to an insightful and productive discussion that has significantly deepened our understanding of this critical area. We also thank Milan Cvitkovic, David Dalrymple and Bogdan Cirstea for providing feedback on an earlier version of this post. Finally, we’d like to offer special thanks to David Dalrymple for delivering a compelling keynote presentation that set the stage for our discussions. 

[^1]: Cyborgism (especially in a recent alignment agenda) is sometimes used more narrowly to mean “ using AI (primarily pretrained GPT models) to augment human cognition". However in this workshop we intentionally do not restrict the term to language model cooperation and also include uses associated with the term “cyborg”.
[^2]: There are some concerns with this approach. For example, if the AI is able to directly influence an individual's decision-making processes, there is a risk that the individual's autonomy could be compromised. There are also ethical concerns associated with cyborgism. For example, if the integration of AI is only available to a select group of individuals, it could exacerbate existing inequalities and create new ones.
