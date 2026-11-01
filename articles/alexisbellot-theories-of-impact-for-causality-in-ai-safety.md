---
title: "Theories of Impact for Causality in AI Safety"
author:
  - "alexisbellot"
source_url: "https://www.lesswrong.com/posts/eyzQra2HiisHuqawP/theories-of-impact-for-causality-in-ai-safety"
published: 2025-04-11
created: 2026-11-01
accessed: 2026-11-01
llm-review:
  date: 2026-11-01
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-01
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Thanks to Jonathan Richens and Tom Everitt for discussions about this post._

The case for causality research[^note-1] is under-stated in the broader AI Safety community. There are few convincing arguments floating around for why and how research in causality can help us understand and mitigate risks from AI.

Cause and effect relationships play a central role in how we (and AIs) understand the world and act upon it. Causal associations intend to be more than descriptions, or summaries of the observed data, and instead relate to the underlying data-generating processes. The overall pitch is that such a mechanistic understanding, when recognised and mastered, allows one to infer what would happen under interventions and hypothetical (counter-to-fact) scenarios, that can give us a richer understanding on AI behaviour and risks.

Here I compile a list of different arguments I have collected from [people](https://causalincentives.com/) currently pushing this [agenda](https://www.lesswrong.com/s/pcdHisDEGLbxrbSHD) as well as my own research for why causality matters.

# Theories of impact ^theories-of-impact

**1\. Understand the limits of AI capabilities**. There are limits to the things we can observe and experiment on. It is unlikely that recorded data will ever capture the outcomes of all possible experiments (including counterfactual thought experiments) under all circumstances. The implication is that answers to these questions must be _deduced_ from other data and assumptions about the world. For example, we might want to know whether an AI agent could eventually, with enough training, predict the effect of any experiment in some domain, even those that haven’t yet been conducted. The answer will sometimes be yes and sometimes no. How to reach these conclusions can be interpreted as a problem of causal identification (e.g. Def. 17 in [Bareinboim et al. 2022](https://causalai.net/r60.pdf)).

**2\. Provide a foundation for AI world modelling**. Causal models are immensely expressive, encoding the likelihood of events and the behaviour of the system under (possibly incompatible) interventions. Inferring the AI’s world (or causal) model from the data and assumptions available is a problem of causal discovery ([Glymour et al., 2019](https://www.frontiersin.org/journals/genetics/articles/10.3389/fgene.2019.00524/full)). Many different methods have been developed under different assumptions and could be leveraged to study the models underlying AI behaviour.

There is already lots of convincing theoretical evidence that AI systems that behave approximately rationally ([Halpern and Piermont, 2024](https://arxiv.org/pdf/2401.10937)) or that are able to complete tasks in many different environments ([Richens and Everitt, 2024](https://openreview.net/pdf?id=pOoKI3ouv1)) can be described as operating on a causal world model.

**3\. Uncover the beliefs and intentions of AI agents**. AI systems are currently trained across many different tasks and display a remarkable ability to transfer knowledge and capabilities across tasks. It can become difficult to explain this behavior without referring to the underlying cognition going on inside the models. AIs might summarize the underlying structure relating different tasks in some form of (internal) world model.  

This view then suggests the possibility of defining beliefs as features of that internal world model. For example, the subjective belief  “_I believe that age should not play a role in employment success_” corresponds to the counterfactual query (roughly) “_Had I changed the individual’s age, my assessment of their future employment success would remain unchanged._” whose truth value can be directly extracted from the AI’s world model ([Chapter 7, Pearl, 2009](https://books.google.es/books?hl=en&lr=&id=f4nuexsNVZIC&oi=fnd&pg=PR15&dq=Causality&ots=y4EW0qwBmk&sig=0HQvT6Ne0M1i06ke15totYEJ1ME&redir_esc=y#v=onepage&q=Causality&f=false)). Similarly, the subjective belief “_I believe that starting a recurrent fitness routine leads to better health outcomes_” corresponds to an interventional query (roughly) “_Assigning an individual to a gym session, irrespective of their prior preferences, causes better health outcomes._” that can also be derived from the AI’s world model.

This opens the door to making use of the full set of identification techniques from causality to infer the beliefs of AI systems from data and other assumptions.

**4\. Provide a mechanistic account of robustness.** Changes in distribution of data might compromise performance and exacerbate Safety risks. Performing robustly in environments different from those an algorithm was trained or tested in is a necessary ingredient for solving the alignment problem. But what do we mean by different environments? And what makes them different?

If we take the view that changes in distributions emerge as a consequence of changes in the underlying causal mechanisms of the environment, then this becomes a transportability problem. Recent work has shown that we can evaluate and learn predictors with a worst-case performance guarantee out-of-distribution ([Jalaldoust et al., 2024](https://causalai.net/r88.pdf)). Similar algorithms could be designed for evaluating the worst case performance of policies which can help us monitor AI systems.

**5\. Predict an AI’s actions out-of-distribution.** To guarantee the safety of AI systems out-of-distribution we might want to infer the agent’s preferences over actions. If the agent can be approximated by an expected utility maximizer, the problem can be defined as searching over the space of actions that maximize expected utility in the agent’s model of the new shifted environment, i.e. out-of-distribution.  Under what conditions is this possible? Can we say anything from observing the AI’s behaviour in related environments?

We can make use of tools in the transportability literature to make progress on this question ([Bareinboim et al, 2016](https://www.pnas.org/doi/pdf/10.1073/pnas.1510507113?trk=public_post_comment-text)). For some set of discrepancies between source and target domain, we might very well be able to bound the AI’s choice of action, possibly ruling out provably sub-optimal actions. This can be an important safety for understanding when an agent should be more closely monitored.

**6\. Provide a standard for good AI explanations**. Convincing explanations often point to “reasons” or “causes” underlying a particular outcome or decision. The extent to which we can explain an AI’s behaviour depends on the extent to which we will be able to infer the underlying causal mechanisms governing its decision-making process. If we can ground explanations in causal mechanisms we might be able to make use of causal discovery and causal abstraction techniques to recover them ([Geiger et al., 2021](https://arxiv.org/pdf/2106.02997)). Finding good explanations could then be defined as a search problem. That doesn’t mean the problem is easy, but it does open up many new angles of attack.

**7\. Provide a standard for alignment notions**. At a higher level, nearly all the features we'd like these systems to have, like being corrigible, robust, intelligible, not being deceptive or harmful, having values aligned with ours, etc., are properties that are difficult to state formally. There is a case to be made for using causal language to give mathematical definitions. For example, fairness ([Plecko et al, 2022](https://arxiv.org/pdf/2207.11385)), harm ([Richens et al., 2022](https://openreview.net/pdf?id=zkQho-Jxky9)), and incentives ([Everitt et al., 2021](https://scholar.google.se/citations?view_op=view_citation&hl=en&user=BdulyjIAAAAJ&citation_for_view=BdulyjIAAAAJ:mVmsd5A6BfQC)) can be made more transparent and estimable from data once we define them in terms of counterfactuals using causal language.

It is unclear whether causal and counterfactual notions will fit all safety-relevant features of AI systems, but it seems like a fruitful line of research.

**8\. Provide tools for evaluating human agency**. Agency is a defining feature of human life that is challenged as AI systems increasingly take up economically productive activities and displace workers. In the context of AI-safety, loss of human agency as a consequence of interacting with AI systems is an important concern ([Mitelut et al., 2024](https://arxiv.org/pdf/2305.19223)).  Several researchers define agency in causal terms. On one account, agency is the “feeling” of causality: the feeling that we are in control of our actions and that we can cause events to occur in the external world. On another account, agency is the (more complex) notion of actual causality ([Halpern, 2016](https://books.google.co.uk/books?hl=en&lr=&id=9cvxDAAAQBAJ&oi=fnd&pg=PR7&dq=actual+causality&ots=Nc6HfeWhWL&sig=MIhxMg430IX3iKnWX1z_DuTFkBU&redir_esc=y#v=onepage&q=actual%20causality&f=false)).

To understand and evaluate the potential loss of  human agency we might want to infer the actual causes, or loci of causality, behind our actions? Pearl opened the door to formally defining actual causation using causal models ([Pearl, 2009](https://books.google.co.uk/books?hl=en&lr=&id=f4nuexsNVZIC&oi=fnd&pg=PR15&dq=Pearl+J+\(2009\)+Causality:+Models,+Reasoning,+and+Inference%3B+2nd+edition.+Cambridge+University+Press+&ots=y4FOUrzuoi&sig=wNma1IYURp6cJ_ODaw_YjBLbNpw&redir_esc=y#v=onepage&q=Pearl%20J%20\(2009\)%20Causality%3A%20Models%2C%20Reasoning%2C%20and%20Inference%3B%202nd%20edition.%20Cambridge%20University%20Press&f=false)). The intuition being that, e.g., a (human) decision, causes an outcome if and only if the decision is a necessary element of a sufficient set for the outcome. This definition has been shown to give intuitive answers on a wide set of problem cases. Evaluating actual causality given data (and possibly some  knowledge of an AI agent’s internal model) is a problem that can be tackled with counterfactual inference tools.

**9\. Provide new explanations for** [**approximate inner alignment**](https://www.alignmentforum.org/s/r9tYkB2a8Fp4DN8yB). Encoding what we actually want in a loss function is, in fact, too hard and will not be solved, so we will ultimately end up training the AI on a proxy. Proxies for what we value are generally correlated with what we actually value, at least on the evaluations we are able to perform. Out-of-distribution that correlation might break down. If we have some structural understanding of the invariances between in- and out- of-distribution domains we might be able to predict how the correlation between true and proxy values might change. This is a problem of transportability that involves partial observability, and it is conceivable that causal tools can formalize some versions of this problem.

**10\. Monitor AI plans**. The AI system proposes a course of action that it predicts leads to successful outcomes. Can we get a second opinion? While searching for optimal policies might be a difficult problem, evaluating the likely effects of a given policy is a much more tractable and classical causal inference problem ([Correa et al., 2020](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=DpdawQQAAAAJ&citation_for_view=DpdawQQAAAAJ:Y0pCki6q_DkC)). If we can develop or extend these techniques in the context of evaluating AI decision-making we could provide an additional check to assert that the AI's plans are consistent with the real-world data and our own knowledge of the task.

**11\. Improve evaluations with more rigorous experimental design.** The strongest evidence for true relationships in nature are often given by rigorous experimental designs that isolate the effect of interest, for example with a randomized control trial ([Shadish et al., 2002](https://iaes.cgiar.org/sites/default/files/pdf/147.pdf)). These techniques could be adapted and extended to improve the evaluation of AI systems, and better interpret the results of our experiments. This is a very large literature that touches on most data-driven scientific disciplines but all appeal to the design of experiments for the inference of causal effects.

Some of this literature is bound to be relevant for AI Safety and will likely allow us to accelerate the design of good evaluations and give us more confidence in our results.

**12\. Provide the right abstractions for interpretability research**. Causal abstraction provides a theoretical foundation for mechanistic interpretability. One purpose of interpretability research is to translate model behavior to a representation that is readily understood by humans. We would expect those representations to drive the behaviour of AI systems, e.g. that a change in the representation leads to a corresponding change in the model’s output ([Geiger et al., 2021](https://arxiv.org/pdf/2106.02997)). That is, _cause_ the observed behaviour of an AI system.

# Conclusion ^conclusion

In the study of physics or medicine, we rely on formal theories to help us predict the behaviour of advanced technologies in situations that are difficult to test in simulations. As AI agency increases, we would benefit from a similarly principled understanding of what decisions AIs are likely to make, their beliefs, world models, etc. The language of causality is one promising candidate to formalize all of these questions and has an impressive [track-record](https://www.nobelprize.org/prizes/economic-sciences/2021/summary/) in many other data-driven sciences.

[^note-1]: Popular science book-length [introduction](https://bayes.cs.ucla.edu/WHY/), technical [introduction](https://ftp.cs.ucla.edu/pub/stat_ser/r350-reprint.pdf) for statisticians, more recent and modern (technical) [introduction](https://causalai.net/r60.pdf) to causality (among many other excellent references to the topic).
