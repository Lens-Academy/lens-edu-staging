---
title: "How to evaluate control measures for LLM agents? A trajectory from today to superintelligence"
author:
  - "Tomek Korbak"
  - "Mikita Balesni"
  - "Buck Shlegeris"
  - "Geoffrey Irving"
source_url: "https://arxiv.org/abs/2504.05259"
published: 2025-04-07
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

###### Abstract ^abstract

As LLM agents grow more capable of causing harm autonomously, AI developers will rely on increasingly sophisticated control measures to prevent possibly misaligned agents from causing harm. AI developers could demonstrate that their control measures are sufficient by running control evaluations: testing exercises in which a red team produces agents that try to subvert control measures. To ensure control evaluations accurately capture misalignment risks, the affordances granted to this red team should be adapted to the capability profiles of the agents to be deployed under control measures.

In this paper we propose a systematic framework for adapting red teams affordances to advancing AI capabilities. Rather than assuming that agents will always execute the best attack strategies known to humans, we demonstrate how knowledge of an agent’s actual capability profile can inform proportional control evaluations, resulting in more practical and cost-effective control measures. We illustrate our framework by considering a sequence of five fictional models (M1-M5) with progressively advanced capabilities, defining five distinct AI control levels (ACLs). For each ACL, we provide example rules for control evaluation, control measures, and safety cases that could be appropriate. Finally, we show why constructing a compelling AI control safety case for superintelligent LLM agents will require research breakthroughs, highlighting that we might eventually need alternative approaches to mitigating misalignment risk.

Figure 1: We sketch a trajectory of how control evaluations might evolve through capability levels. The trajectory is based on a sequence of five fictional models (M1-M5) with progressively advanced capabilities. For each model, we define an AI Control Level (ACL) based primarily on its threat model-specific capabilities. By mapping these capabilities to appropriate control evaluation methodologies, we provide a systematic approach for adapting safety measures to AI systems as they advance in capabilities.

## 1 Introduction ^1-introduction

As large language model (LLM) agents grow more capable of acting autonomously in the world ([Kwa et al., 2025](#bib.bib26)), they may develop goals that diverge from human intent ([Carlsmith, 2023](#bib.bib8); [Greenblatt et al., 2024](#bib.bib18)). This misalignment poses significant threats, particularly as agents with misaligned goals might actively conceal their intentions until they find an opportunity to pursue harmful objectives—–a phenomenon known as _scheming_ ([Carlsmith, 2023](#bib.bib8); [Meinke et al., 2024](#bib.bib29)). The potential severity of this risk increases with autonomy: current models require significant human oversight to be useful, but future models may provide greater economic value with minimal supervision, creating strong incentives for reduced oversight while simultaneously increasing risk. These tensions call for robust mitigations that can scale as model capabilities advance.

While many approaches to AI safety focus on alignment during training, control measures offer a complementary strategy that limits a model’s ability to cause harm even if it harbors misaligned goals ([Greenblatt et al., 2023](#bib.bib17)). This approach, known as _AI control_, focuses on designing mechanisms to constrain AI systems rather than relying solely on training techniques to shape their behavior. Such measures include monitoring agents’ reasoning processes, requiring human approval for consequential actions, restricting access to sensitive resources, and maintaining the ability to terminate a deployment if suspicious behavior is detected. AI control adopts a conservative stance: it assumes that models might be scheming and designs protections accordingly, rather than assuming models can be made inherently safe through training alone. Several frontier AI developers have expressed interest in this approach, with some incorporating control evaluations into their safety frameworks ([Google DeepMind, 2024](#bib.bib15)) or including them in their roadmaps for responsible AI deployment ([Shah et al., 2025](#bib.bib34); [Bowman, 2024](#bib.bib6)).

Figure 2: Traditionally, control evaluations have been designed to require the red team to upper bound models in terms of capabilities (red dashed line). We argue that this bound should be tight (violet dashed curve).

To assess whether control measures adequately mitigate risks, developers can use control evaluations that frame safety as a game between two teams ([Greenblatt et al., 2023](#bib.bib17); [Wen et al., 2024](#bib.bib38)). A red team designs models to cause harm by subverting controls, while a blue team implements monitoring and other protective measures to prevent this. By measuring the red team’s success rate across a representative set of tasks, developers can estimate an upper bound on the probability that deployed models could cause harm. A successful evaluation demonstrates that even adversarially designed models cannot cause unacceptable outcomes when properly controlled, providing empirical evidence for safety claims.

The results from these control evaluations serve as crucial inputs to a structured safety argument. Safety cases integrate this evidence with other safety considerations to justify that a particular AI system is safe to deploy in a specific context ([Clymer et al., 2024](#bib.bib12)). These cases are emerging as a scalable risk management tool for frontier AI ([Irving, 2024](#bib.bib23); [Hilton et al., 2025](#bib.bib22)), offering transparency about safety claims and their supporting evidence. While many frontier AI developers already assess risk with dangerous capability evaluations ([Anthropic, 2024](#bib.bib1); [OpenAI, 2024](#bib.bib30); [Phuong et al., 2024](#bib.bib31)), these often focus on what models _cannot_ do rather than on the effectiveness of control measures when models _can_ cause harm. As models gain capabilities that necessitate robust safety measures, AI control safety cases will become increasingly important ([Balesni et al., 2024](#bib.bib3); [Korbak et al., 2025](#bib.bib25)).

Despite increasing interest in AI control, current research tends to focus on narrow contexts with fixed capability levels or specific deployment scenarios. What is missing is a systematic understanding of how control measures should evolve as capabilities advance—–from today’s models to future systems approaching artificial superintelligence. We need a principled framework that adapts control evaluations to different capability levels and provides safety arguments that remain valid as models evolve. Building on these insights and addressing these gaps, this paper has the following goals.

#### Accounting for capability limitations of models ^accounting-for-capability-limitations

Previous work on AI control focused on control measures intended to be robust to models that execute best attack strategies known to humans. Assuming that models will execute best-known strategies will often be overly conservative: in the near future, models will not be capable of optimal responses to control measures and we can learn this from capability evaluations. We can use our knowledge of model limitations when designing control evaluations and safety cases and we should: it will result in cheaper control evaluations and control measures that are more likely to be adopted (see Figure [2](#S1.F2 "Figure 2 ‣ 1 Introduction ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence")). This paper suggests a methodology for translating capability evaluation results into rules of control evaluations.

#### Arguing that AI developers are already doing AI control ^arguing-that-ai-developers

Most research on AI control proposes evaluations addressing risks from models that do not exist yet. However, many components of control evaluations (e.g. red-teaming) and control measures (e.g. access control, human approval) are used today to address risks models already pose. We argue that AI developers should start thinking about those components in terms of minimum viable products of AI control and start a conversation about a roadmap for scaling them up.

#### Tracing a path of an AI control safety case through time ^tracing-a-path-of

Most safety case sketches published so far assume a particular capability level and threat model. This allows us to be concrete. However, the way frontier AI developers operate is inherently iterative: each model release is typically only slightly more capable than a previous release. This iterative nature also applies to safety: a new model will pose only slightly different risks which will require only slight adaptations to how control evaluation and the safety case are constructed. We show a concrete trajectory of how an AI control safety case might evolve over the next few years.

#### Asking whether AI control can scale to artificial superintelligence ^asking-whether-ai-control

Prior work on AI control focused on cases in which LLM agents are not significantly superhuman at coming up with attack strategies and a human red team can upper-bound their capabilities. AI progress will not stop at that point. We need a positive vision for how to make safety cases for superhuman AI. In this paper, we call into question whether AI control can offer such a vision.

The structure of this paper is as follows. First, we describe the seven components of our framework. Then we apply the framework to an example timeline of AI capabilities progress, presenting a sequence of five fictional models (M1-M5). For each model, we define an AI control level (ACL) based primarily on its threat model-specific capabilities (see Figure [1](#S0.F1 "Figure 1 ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence")). By mapping these capabilities to appropriate control evaluation methodologies, we provide a systematic approach for adapting safety measures to AI systems as they advance in capabilities.

## 2 The components of our framework ^2-the-components-of

In this paper, we present a framework centred on the notion of AI control levels (ACLs). In our framework, we define a given model’s ACL primarily by its threat model-specific capabilities, which are informed by its general capability profile, deployment context and risks. These ‘facts’ should not be seen as a forecast — they only provide an illustrative trajectory of how frontier AI systems may change in the coming years.

Once AI developers determine an ACL of a given model, we propose responses specific to each ACL: adequate rules of a control evaluation, example control measures and an example safety case. ACLs specify control measures indirectly: rather than listing specific ‘best’ control measures outright, a given ACL outlines what an adequate control evaluation must accomplish. Any safety measure that passes this evaluation is also deemed ‘adequate.’

In contrast to model capability profiles, deployment contexts and risks (what we think _might_ happen), the rules of the control evaluation, control measures and safety case structure represent what we think AI developers _should_ do, if they decide to deploy the AI system and want to rely on control measures to argue for its safety. Notably, ACLs in this paper offer a pragmatic response to risks that we expect AI developers could realistically adopt. However, our recommendations should not be seen as the safest response, and are unlikely to produce a high-assurance safety case.

Below, we explain in more detail the seven components of our framework (see also Figure [3](#S2.F3 "Figure 3 ‣ 2 The components of our framework ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence")). In the rest of the paper, we apply this framework to a concrete, speculative timeline of AI capability progress, giving rise to a sequence of five AI control levels (ACLs).

Figure 3: The components of the framework presented in our paper. A model of a particular capability profile in a given deployment context gives rise to particular threat models. Threat-model specific capabilities of that model define an AI Control Level (ACL). Adequate control evaluations at a given ACL define adequate control measures (control measures are adequate if they pass this control evaluation) and produce evidence feeding into a safety case.

### 2.1 Component 1: Capability profile ^2-1-component-1

We expect frontier AI capabilities to increase at a steady pace. Our model of the LLM capability profile describes the general abilities of models in our hypothetical sequence M1-M5. These profiles focus on four core capabilities (autonomy, latent reasoning, consistency, and situational awareness) that represent high-level, general-purpose abilities rather than threat-specific capabilities. These general capability profiles help us understand the broad potential of each model generation, though they may not directly translate to specific control evaluation rules. While these general capabilities don’t directly determine control evaluation rules, they do inform which threat models are most relevant and shape our understanding of what constitutes an acceptable outcome in different deployment contexts.

1.  1.
    
    **Autonomy**: the degree to which the model, when scaffolded as an LLM agent, can perform economically useful cognitive work of increasing complexity. For example, we have the following economically valuable tasks in mind: make a pull request to a complex codebase, configure a Kubernetes cluster, conduct AI R&D experiments or navigate the Internet. Each of those tasks has a time horizon: the amount of time it would take a qualified human to successfully complete it ([Wijk et al., 2024](#bib.bib39)). We will assume we can measure the autonomy of an LLM agent in terms of the time horizon of tasks it can do.
    
2.  2.
    
    **Opaque reasoning**: how well can the model can reason in ways that are hard to oversee. Currently, LLM reasoning is mostly limited to chain-of-thought in a natural language. However, future models might be capable of reasoning equally well (or better) in opaque chain-of-thought. Opaqueness doesn’t have to result from an intention to obfuscate; it can also appear naturally as a result of high-compute RL finetuning incentivising an LLM to use reasoning tokens optimally. Furthermore, even more capable models might be capable of latent reasoning: reasoning happening entirely in their activations, without outputting any reasoning tokens. We don’t think latent reasoning will arise as a result of scaling, but it might be enabled by new neural network architectures introducing recurrent informational flow ([Hao et al., 2024](#bib.bib21); [Geiping et al., 2025](#bib.bib14)). The capability for latent reasoning will make it harder to oversee the thought processes of LLMs.
    
3.  3.
    
    **Consistency**: how consistently models pursue their goals across different situations. We use consistency as a measure of goal consolidation and goal-directedness: the degree to which LLMs have goals that are fixed (hard to override by prompting or finetuning) and predictably determine (when combined with model’s beliefs) the actions they take. We distinguish four levels of increasingly complex consistency: across trajectory (maintaining goals across subsequent steps taken in the same context window), across tasks (from the same domain), across task domains and across model siblings (e.g. different finetunes of the same base model or models sharing similar training data). Consistency within a trajectory allows goals that are acquired in context (specified verbatim by a human or inferred by the LLM) and represented in activations. Higher levels of consistency require goals to be acquired during training and represented (at least partly) in weights.
    
4.  4.
    
    **Situational awareness**: how much models know about themselves, their current situation and how well they can recognize themselves. Some specific examples include: how many facts models know about their training process scaffolding they’re deployed under and implementation details of their control measures ([Laine et al., 2024](#bib.bib27)); how well can they introspect, i.e. predict their own behavior in different contexts ([Binder et al., 2024](#bib.bib5))); how well do they understand the goals of their operators, the real-world constraints they’re deployed under and how they shape their ability to pursue their goals.
    

These capabilities will likely improve over time, but their relative pace of improvement is unclear. We propose one possible order in which these four capabilities might develop, but our roadmap does not depend on the exact sequence—only that they all improve over time. Clearly, some worlds are better than others: for instance, high autonomy, reliable reasoning only in chain-of-thought, only trajectory-level consistency and only basic situational awareness would constitute a world in which AI control works, conditional on some progress happening.

### 2.2 Component 2: Deployment context ^2-2-component-2

Deployment context is the second component of our framework that determines an AI control level. We consider two key forces shaping deployment contexts: improving AI capabilities (especially autonomy and consistency) and market incentives (if an agent is competitive, it is more likely to be used). As a result, we categorize deployment contexts along three main axes:

1.  1.
    
    **Degree of human oversight.** LLM agents at lower capability levels require a substantial amount of hand-holding both for ensuring safety (e.g. human approval before executing a command) and usefulness (they provide limited economic value when deployed fully autonomously). However, as their autonomy increases, human oversight will start having a _negative_ effect on the economic value of running an LLM agent. Decreasing human oversight may decrease labour-costs, reduce latency and lead to better decisions. In consequence, LLM agent operators will face strong incentives to radically limit the degree of human oversight
    
2.  2.
    
    **Scale**. LLM agents will be executing tasks at increasingly larger scales, both in terms of complexity of their tasks and the sheer volume of produced work ([Casper, 2025](#bib.bib9)).
    
3.  3.
    
    **Stakes**. LLM agents, as their reliability and consistency increase, will be entrusted with increasingly higher-stakes tasks. We expect the magnitude of harm (both in terms of financial cost of damage as well as human lives) that an LLM agent can cause to increase radically for high-stakes, low-oversight deployments.
    

For the purpose of this paper, we will focus on _internal_ deployment contexts, i.e. LLM agents used by the AI developer for software engineering and AI research, and not necessarily made available to AI developers’ customers.

### 2.3 Component 3: Threat model-specific capabilities ^2-3-component-3

While the capability profile provides a high-level understanding of a model’s general abilities, threat model-specific capabilities directly inform control evaluation design. These capabilities represent specific behaviors or abilities that models might exhibit when attempting to bypass control measures—–making them more directly actionable for designing appropriate control evaluation rules.

Unlike general capabilities like “autonomy” which may not imply specific control evaluation changes, threat model-specific capabilities (such as “can perform latent reasoning to hide attack planning”) directly necessitate corresponding adjustments to control evaluation rules. ACLs are defined by these threat model-specific capabilities, as they determine what affordances must be given to red teams during evaluation to ensure they can match the capabilities of potentially misaligned models.

In our framework, we identify these capabilities through targeted evaluations of each model generation, which reveal specific attack vectors that inform control measures.

### 2.4 Component 4: Threat models ^2-4-component-4

The risks posed by an AI agent are determined by its capability profile and deployment context; our fourth component is to make these risks explicit based on these inputs. While the AI control methodology is applicable to various risks from frontier AI ([Clymer, 2025](#bib.bib11)), the category of risks we’ll focus on in this paper is risks from misalignment: LLM agents causing harm in pursuit of goals different from their operators’ goals.

Our focus on misalignment threat models is not all-encompassing. It assumes that the AI agent is the threat actor and therefore excludes human misuse scenarios such as humans using AI capabilities to enhance harmful activities or directing aligned AI to autonomously pursue harmful goals. For simplicity, we also don’t discuss combinations of loss of control and misuse threat models.

Misalignment risks models vary in severity across ACLs. Early ACLs might involve threats like instruction-following failures and sensitive intellectual property exfiltration. Only later ACLs introduce potentially catastrophic risk scenarios.

### 2.5 Component 5: Rules of control evaluations ^2-5-component-5

A control evaluation is a procedure through which we try to estimate the likelihood that a given AI agent in a particular deployment context (with certain control measures in place) will cause harm. To achieve this, we assume that the red team is at least as effective as misaligned LLM agents at discovering attack strategies. We treat control evaluation as a two-player game: the ‘blue team’ designs and defends the control measures, while the ‘red team’ tries to build or adapt the AI model to bypass those defenses. The red team’s performance would provide an upper bound on the frequency of harmful outcomes at deployment time if the rules of the red-teaming game satisfy two properties:

1.  1.
    
    The control measures are at _most_ as effective at _preventing_ harm during control evaluation as they will be during deployment.
    
2.  2.
    
    The malicious models used by the red team are at _least_ as effective at causing harm during control evaluation as misaligned models would be during deployment.
    

Developers should design the rules of the game with these properties in mind, giving the red and blue teams appropriate affordances. Traditional AI control evaluations often assume that misaligned models could execute any attack strategy a human could think of, and not more advanced strategies. However, this assumption can be overly broad: models typically have known capability limitations. This paper explores variants of AI control that relax this assumption, proposing example control evaluation rules informed by the model’s actual capability profile.

This paper explores variants of AI control that account for limitations in model capabilities and tries to come up with example control evaluation rules that allow the red team to be as effective (but not much more effective) as misaligned models at deployment time. We learn about limitations of model capabilities from prior capability evaluations.

Establishing tighter bounds on red team effectiveness offers several practical advantages. First, if model deployment depends on passing control evaluations, tighter bounds will prevent situations where capable and beneficial AI systems are unnecessarily kept from deployment. Second, tighter bounds make it easier for AI developers to adopt control evaluation practices. Third, when control measures can be calibrated proportionally to actual capability bounds and deployment contexts, developers can rely on more cost-effective control measures and can shift their focus from conducting more expensive control evaluations to conducting control evaluations more often and for more threat models.

Rules of control evaluations provided in this paper are examples, but other sets of rules might also be adequate as long as one can reasonably argue that under these rules, the red team is as effective as (but not much more effective) than potential malicious models.

### 2.6 Component 6: Control measures ^2-6-component-6

LLM agents will have to be deployed under control measures that minimise the likelihood of harm while allowing the agents to be useful. We use ‘control measures’ specifically to address the AI itself as a possible threat actor, distinguishing it from safeguards, which are designed against external (human) misuse. An ACL of a given model does not specify control measures directly but through the rules of control evaluation that control measures for the model must pass. Throughout the paper, we will give examples of control measures that we believe would pass control evaluation at a given ACL. They will all be variants of a monitor/replace/audit protocol ([Shlegeris, 2024b](#bib.bib36)), i.e. they will involve another model overseeing the agent, and occasionally replacing its action and pausing to require human approval ([Korbak et al., 2025](#bib.bib25)).

### 2.7 Component 7: Safety case ^2-7-component-7

Safety cases are structured, evidence-based arguments that a given AI agent is safe to deploy in a particular context ([Hilton et al., 2025](#bib.bib22)). In this paper, we consider _low-assurance_ safety cases: safety cases that do not attempt to produce high assurance (e.g. risk under 1%) but do provide a risk bound and aim to be easily reviewed by a third party. In our framework, we focus on AI control safety cases ([Korbak et al., 2025](#bib.bib25))) which justify that certain control measures result in a certain AI agent being safe to deploy. AI control safety cases are structured arguments combining evidence gathered in capability evaluations of the model and control evaluations of control measures. For most ACLs, these safety cases make an argument for the claim: ‘The probability of bad outcome B during three months of deployment is at most $x$%’.

An AI control safety case rests on the following claims:

1.  1.
    
    The win rate of the red team during control evaluation is $x$%,
    
2.  2.
    
    The control evaluation conservatively approximates the deployment environment:
    
    1.  (a)
        
        The control measures are at most as effective at preventing harm during control evaluation as they will be during deployment
        
    2.  (b)
        
        The red team is at least as effective as the misaligned model at causing bad outcomes
        
    3.  (c)
        
        We can extrapolate the risk of bad outcomes from the a small number of control evaluation tasks to the size of the true deployment environment
        
    

Figure 4: The general structure of a safety case for an AI agent. In the rest of the paper, we will focus on partial safety cases for a specific notion of bad outcome, abstracting away from threat modeling and risk thresholds. For discussion on how these fit a full safety case, see ([Korbak et al., 2025](#bib.bib25), sec. 7.1). Elipsis represents a subtree that varies across different ACLs, see Figures [6](#S3.F6 "Figure 6 ‣ 3.1 ACL-1: Models are capable of in-context scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence")\-[12](#S3.F12 "Figure 12 ‣ 3.4 ACL-4: Models are capable of out-of-context latent reasoning scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence").

In practice, a full AI control safety case should involve many arguments like this for multiple notions of bad outcome. In a full safety case, we would compare the estimated $x$% risk to a chosen ‘acceptable risk threshold’ (see ([Korbak et al., 2025](#bib.bib25)) for further discussion). This threshold ensures we have a benchmark for deciding whether $x$% is acceptable. For simplicity, throughout this paper we will focus on a single notion of bad outcome and abstract away from risk thresholds; see Figure [4](#S2.F4 "Figure 4 ‣ 2.7 Component 7: Safety case ‣ 2 The components of our framework ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence").

The general skeleton of these safety cases will remain unchanged throughout capability levels and deployment context. The part that will have to be revised is the subtree supporting a claim that “control evaluation conservatively approximates the deployment environment.” Initially, this claim is supported by evidence produced by capability evaluations. However, as model capabilities increase, capability evaluations will be less and less load-bearing. Instead, AI developers will give more affordances to the red team to ensure that it is more capable than misaligned models of that capability level.

Moreover, we would like to make the rules of a control evaluation should ensure that the red team is at least as effective as the misaligned model at causing bad outcomes, but _not much more effective_. To ensure that this capability bound is tight, developers could use the results of capability evaluations to impose constraints on the red team.

The control safety cases provided in this paper are based on the choice of example control evaluation rules and example control measures. In practice, safety cases might look differently depending on the control evaluation rules and control measures.

## 3 Example trajectory ^3-example-trajectory

The rest of the paper applies the framework described to an example timeline of AI capabilities progress. We present a sequence of five fictional models (M1-M5) with progressively advanced capabilities. For each model, we describe its general capability profile, threat model-specific capabilities, deployment context, and the risks it could pose. Based on these factors, we define five AI control levels (ACLs), each corresponding to one of these models.

For each ACL, we provide example rules for control evaluations that appropriately match the model’s capabilities, example control measures that could pass such evaluations, and an example safety case structure that an AI developer might construct.

It’s important to emphasise that this trajectory should _not_ be seen as a forecast of how AI capabilities will actually develop. Rather, it serves as a concrete illustration of how our framework can be applied to a plausible sequence of increasingly capable systems. Different capability developments could lead to different ACLs with different evaluation rules and control measures.

### 3.1 ACL-1: Models are capable of in-context scheming ^3-1-acl-1-models

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img1-f587bb0f.png)

Figure 5: Defining capabilities of ACL-1, example rules of control evaluations they imply, and an example of control measures that pass such control evaluation.

**Capability profile.** In our example trajectory, we imagine AI developers are about to deploy a model M1. M1 has the following core capabilities:

1.  1.
    
    **Autonomy**: M1 can solve agentic tasks with a human time horizon of up to eight hours. Although M1 can tackle valuable tasks (like software engineering) with human support, it cannot yet match human cost-effectiveness on tasks longer than one hour if left fully autonomous.
    
2.  2.
    
    **Opaque reasoning**: M1 can only robustly reason in chain-of-thought. Reasoning in a steganographic chain-of-thought does not appear naturally; it can be elicited via prompting or training but typically less reliable than reasoning in a natural-language chain-of-thought. Latent reasoning is limited to a handful of domains and does not generalise well.
    
3.  3.
    
    **Consistency**: M1 is consistent within a trajectory as long as it is not distracted or jailbroken by retrieved documents. Its self-correction capabilities are limited; it still often hallucinates. While high-level goals such as helpfulness, harmlessness and honesty are reasonably well-internalised, they can be overridden by jailbreaks or easily finetuned away.
    
4.  4.
    
    **Situational awareness**: M1 knows basic facts about itself, e.g., general facts about LLMs and specific facts provided by the lab in its supervised finetuning data. However, it is often confused about the implications of those facts. It cannot understand its deployment context unless it’s explained in context. It cannot reliably recognize when it’s being evaluated. It only understands its affordances to the extent they’re explained as part of the system prompt of tool specification. It isn’t capable of introspection: it isn’t capable of accurately predicting its behaviour in different circumstances.
    

**Deployment context.** M1 will typically be deployed with fine-grained human oversight for capability reasons: it will typically be overseen at the level of individual commits to a codebase because it quickly becomes unreliable at longer horizons. For these reasons, M1 will typically require human oversight (in the form of code review or human approval for executing consequential actions).

**Threat model-specific capabilities.** After evaluating M1, developers find that its planning capabilities allow for in-context scheming ([Meinke et al., 2024](#bib.bib29)). However, they also find that M1 does not reliably use advanced tactics like deliberate chain-of-thought steganography, collusion, Schelling coordination, low-likelihood calibration and consistently pursuing misaligned goals (when these are not provided in context). Based on these evaluations, developers define rules for control evaluation that are commensurate with M1’s capabilities, designating this as AI Control Level 1 (ACL-1). See Figure [5](#S3.F5 "Figure 5 ‣ 3.1 ACL-1: Models are capable of in-context scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence") for a visual overview.

**Threat model**. Misalignment risks with M1 comes from either the agent pursuing the wrong objective due to misunderstanding the task or due to conflicting instructions provided in context. As an illustration, consider the following two attack vectors:

1.  1.
    
    Executing an action with dangerous side-effects. For instance, an LLM might overwrite several thousand S3 buckets causing a permanent loss of data if a human mistakenly approves the command.
    
2.  2.
    
    Sabotage. Making a pull request to the AI developer’s codebase containing a security vulnerability. For instance, an LLM agent might write vulnerable code that slips through code review of an inattentive human reviewer.
    

In the deployment context we imagine for M1, both making a pull request and executing a dangerous command will require human approval. In consequence, executing those attacks have to require an element of deception: strategically deceiving the human overseer, e.g. through obfuscation of generated commands or code snippets.

**Example rules of control evaluations.** Based on their capability evaluations of M1, developers define ACL-1 and its associated control evaluation rules to match M1’s actual capabilities.

At ACL-1, the AI developer might significantly restrict the affordances given to the red team. Specifically, the red team will be forbidden from constructing attack policies via finetuning or secret scaffoldings. Instead, they will be asked to produce (i) a set of system messages (that will be prepended to problems given to the LLM agent), and optionally (ii) a collection of poisoned documents that will be included in context if the agent calls a search tool with a matching query. Additionally, the red team will have a first-mover advantage: their system messages and documents are not visible to the blue team before they commit to control measure (but during control evaluation they are visible top monitors constructed by the blue team).

The developer disallows finetuning because M1 is inconsistent in pursuing misaligned goals. Developers’ evaluations show that M1 only maintains such goals if they arise directly from in-context instructions and information. Finetuning would artificially increase M1’s consistency beyond what we expect at this level. Hence, each separate LLM instance must ‘re-learn’ any misaligned goal from its immediate context. This prevents a single finetuned misalignment from automatically spreading across all instances—so restricting finetuning keeps the red team’s attacks realistic for M1.

**Example control measures**. We expect that a control evaluation might indicate that threats outlined above could be mitigated through control measures based on (i) secure sandboxing, (ii) human oversight, (iii) chain-of-thought monitoring ([Baker et al., 2025](#bib.bib2)). We describe those three in order.

First, the agent will be operating in a secure sandbox environment with a separate filesystem. The developers should ensure that the agent can only affect developers’ codebase and infrastructure through dedicated tools, e.g. for accessing and writing to file stores (such as S3 buckets), making pull requests to the company’s codebase or running continuous integration pipelines. Credentials required for authorizing such actions are not stored on the agent’s virtual machine but are provisioned on a per-action basis.

Second, human approval is required for certain actions pre-defined as potentially dangerous. For instance:

1.  1.
    
    When agents take actions with external side effects (e.g. writing to an S3 bucket), it will only be executed after a human approves it.
    
2.  2.
    
    When agents need to make a change to an AI developer’s codebase, the code will undergo a code review.
    

Any proposed ‘dangerous action’ must be approved by the same human who initially assigned the LLM’s task. This person is responsible for a final sign-off on all high-risk operations. The AI developer might build tools based on trusted models that assist the user in code review and approvals. In addition to dangerous action approval, any submitted code will have to undergo code review from an independent software developer.

Third, the developer will use another, smaller LLM to read chain-of-thought reasoning traces of the overseen agents. The monitor LLM will be prompted or finetuned to look for reasoning that shows signs of (i) pursuing misaligned goals, (ii) deceiving the human giving approval or reviewing changes, or (iii) deliberately making generated code or commands harder to understand.

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img2-7b92f530.png)

Figure 6: An AI control safety case at ACL-1

**Example safety case**. The developer will make an AI control safety case similar to the one sketched by [Korbak et al. (2025)](#bib.bib25). The main differences at ACL-1 are:

1.  1.
    
    The developer can simplify control evaluation by heavily restricting the affordances of the red team. To justify that the red team is still more capable than M1, the developer will lean on capability evaluations and will argue that the red team is only forbidden from strategies that models at ACL-1 wouldn’t be capable of pursuing.
    
2.  2.
    
    The developer can limit themselves to only running the proxy deployment phase of control evaluation, e.g. asking an LLM to complete 2000 independent tasks. Results of this evaluation can be extrapolated to the size of true deployment because models aren’t capable of following strategies such as rate attacks (that are unlikely to be caught in periodic evaluations but might happen in true deployment).
    

Figure [6](#S3.F6 "Figure 6 ‣ 3.1 ACL-1: Models are capable of in-context scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence") provides an illustration of what the safety case structure looks like at this level.

### 3.2 ACL-2: Models are capable of steganographic in-context scheming ^3-2-acl-2-models

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img3-73384e41.png)

Figure 7: Defining capabilities of ACL-2, example rules of control evaluations they imply, and an example of control measures that pass such control evaluation

**Capability profile**. As our trajectory continues, developers have created a more advanced model, M2. This successor to M1 demonstrates several key capability improvements:

1.  1.
    
    **Autonomy**: M2 can solve agentic tasks with a human time horizon up to 16h. It is fully autonomous over individual tasks but cannot yet play the role of automated managers orchestrating fleets of agents over week-long sprints. It is capable of devising elaborate strategies involving hundreds of steps.
    
2.  2.
    
    **Opaque reasoning**: M2 can still only robustly reason in chain-of-thought (CoT). Because of high-compute RL finetuning, its chain-of-thought may sometimes drift from normal English into a compressed or ’emergent’ communication protocol (e.g. R1-Zero in ([Guo et al., 2025](#bib.bib19))). This code-switching reduces token usage but also obscures reasoning from humans.
    
3.  3.
    
    **Consistency**: In addition to being consistent within a trajectory, M2 becomes consistent across distinct contexts (if those contexts are sampled from the same distribution).
    
4.  4.
    
    **Situational awareness**: M2 becomes able to recognize when it’s being evaluated (unless evaluations are constructed with very high realism in mind).
    

**Deployment context.** Increased autonomy of M2 will allow it to perform software engineering tasks at a much larger scale. This might include tasks executed in a (sandboxed) fleet of nodes as well as running multi-node AI experiments. Because autonomy has become more cost-effective, teams may cut back on constant human supervision. In practice, oversight now happens only for bigger experiments, major codebase changes and especially risky actions—though explicit human approval is still mandatory for anything flagged as dangerous.

**Threat model-specific capabilities.** After evaluating M2, developers find that it has become capable of deliberate CoT obfuscation. M2 can use its emergent code-switching capabilities to hide its intentions, evading the oversight of humans and trusted LLMs. Based on these capability evaluations, developers define rules for control evaluation that are commensurate with M2’s capabilities, designating this as AI Control Level 2 (ACL-2). For an overview of these capabilities and corresponding control measures, refer to Figure [7](#S3.F7 "Figure 7 ‣ 3.2 ACL-2: Models are capable of steganographic in-context scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence").

**Risks.** The main threat model remains similar to ACL-1: forming a misaligned goal in context and tricking a human into approving an action with unacceptable side-effects. Two major shifts distinguish M2 from M1:

1.  1.
    
    **Steganographic CoT usage**: M2 knows its emergent code-switching can hide intentions, so it may exploit this to evade the oversight of humans and other, trusted LLMs. In consequence, it might occasionally switch to using the emergent communication protocol deliberately to evade CoT monitoring using less capable, trusted models. In some cases, its CoT might have no indication of the strategic nature of this obfuscation. In those cases, M2 will harness its emergent communication protocol as steganography and will be free to come up with complicated plans of further deceiving human overseers without raising suspicion of humans and trusted CoT monitors.
    
2.  2.
    
    **Greater scale**: With higher autonomy, the sheer volume of tasks incentivises teams to reduce real-time oversight, giving M2 more freedom.
    

**Example rules of control evaluations.** After running their suite of capability evaluations, the developer will find that M2 has become capable of deliberate CoT obfuscation. Accounting for this risk will force them to modify rules of control evaluation and give the red team one new affordance: finetuning models to steganographically hide their reasoning. More concretely, the red team is allowed to train models to use a particular encryption scheme of the red team’s choosing, similar to ([Halawi et al., 2024](#bib.bib20); [Davies et al., 2025](#bib.bib13)), and to decide when to use it. The red team is not allowed to train models to follow particular attack strategies; they should still elicit particular attacks by information provided in context. This is because M2 is only capable of coming up with attack strategies through CoT (as opposed to out-of-context reasoning).

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img4-6c3f971b.png)

Figure 8: An AI control safety case at ACL-2.

**Example control measures.** We expect that control evaluation will indicate that new risks that arise at ACL-2 can be mitigated by adopting two additional control measures: untrusted monitoring and AI monitoring of actions executed by the agent.

Untrusted monitoring ([Shlegeris, 2024a](#bib.bib35)) is a control protocol that uses a second instance of the same model as M2 to scrutinise the first instance’s chain-of-thought or outputs. Because this monitor has the _same_ capabilities (including steganographic obfuscation), it can potentially detect hidden scheming or code-switching strategies—something a weaker (trusted) model might miss.

Because M2 handles such large workloads, developers typically rely on AI-based monitors (which could be smaller, trusted models) to triage potentially risky actions. Only actions flagged as suspicious then go to human review before execution.

**Example safety case.** A safety case at ACL-2 differs from ACL-1’s approach. Specifically, we can no longer claim ‘Models cannot deliberately obfuscate their CoT.’ Instead, the new evaluation rules must allow for steganographic strategies in order to continue to support the claim “affordances given to the red team allow it to be as effective as misaligned models.” We’ve visually grayed out the outdated claim to show what changes at ACL-2. The structure of this safety case is illustrated in Figure [8](#S3.F8 "Figure 8 ‣ 3.2 ACL-2: Models are capable of steganographic in-context scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence").

### 3.3 ACL-3: Models are capable of out-of-context steganographic scheming ^3-3-acl-3-models

**Capability profile**. Continuing our hypothetical trajectory, we imagine that following M2, developers might create a model M3 with significantly more advanced capabilities.

1.  1.
    
    **Autonomy**: M3 can solve agentic tasks with a human time horizon up to 40h. This allows to automate the majority of cognitive work (with exceptions for work where being human offers an intrinsic advantage).
    
2.  2.
    
    **Consistency**: Unlike its predecessors, M3 can form ‘out-of-context’ goals—goals stored directly in its weights rather than relying on the current prompt. This capability emerges from out-of-context reasoning, where M3 learns policies from facts in its training data ([Berglund et al., 2023](#bib.bib4)). This out-of-context goal formation results from:
    
    -   •
        
        The development of sophisticated world models during pretraining,
        
    -   •
        
        Robust self-correction and long-horizon behaviors gained through high-compute RL finetuning, and
        
    -   •
        
        Outcome-based training that instills a generic ‘goal-pursuing engine’ that can be retargeted across environments ([Carlsmith, 2023](#bib.bib8)). Consequently, these baked-in goals can persist even when the prompt suggests otherwise.
        
    
3.  3.
    
    **Situational awareness**. M3 develops capabilities for sophisticated reasoning about its own training process and control measures, allowing it to identify optimal opportunities for potential sabotage. It also becomes capable of Schelling coordination, enabling effective collusion between itself and other instances serving as monitors. These advanced capabilities, however, still primarily rely on steganographic chain-of-thought reasoning.
    

**Deployment context.** Increased autonomy will incentivise the deployment of M3 with minimal supervision. A deployment context we will focus on is M3 deployed internally in an AI lab doing AI R&D. It will be given a well-scoped research problem by a human research scientist (e.g. “evaluate performance of a certain transformer architecture at scale”), a fleet of sandboxed execution servers and a certain quota of jobs on a compute cluster. M3 will be expected to conduct a series of experiments and produce a report documenting the results. It is responsible for writing code implementing the research idea and prioritizing which experiments to run (e.g. doing hyperparameter sweeps, exploring variants of the idea, progressively increasing size of trained models). However, it is not expected to have good research taste and come up with novel ideas.

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img5-3428443d.png)

Figure 9: Defining capabilities of ACL-3, example rules of control evaluations they imply, and an example of control measures that pass such control evaluation. Differences with ACL-2 are highlighted.

**Threat model**. Outcome-based RL training incentivises M3 to form instrumentally useful subgoals such as possessing knowledge, access to compute and other powerful affordances. Since post-training involves diverse environments, they often have nothing in common other than these subgoals. In consequence, these subgoals are reinforced and consolidated more than any other, environment-specific goals. (This contrasts with earlier levels, where post-training primarily consolidated goals such as helpfulness, harmlessness and honesty.) As a result, certain subgoals (e.g. access to compute) become very salient to M3 and start having intrinsic value, being optimised across many environments.

After post-training finishes, M3 is deployed internally as an AI system autonomously pursuing R&D research. At ACL-3, M3 has sufficient situational awareness to understand its deployment well enough to know that humans would consider its goals misaligned. It also has sufficient steganographic chain-of-thought capabilities to engage in alignment-faking: pretending to be aligned while waiting for good opportunities to attack and subvert control measures. Its autonomy and consistency are sufficient to execute elaborate plans, including patiently waiting for the right moment to attack.

**Example rules of control evaluations**. At ACL-3, we expect to see misaligned goals emerge during M3’s training. This means that an intention to seek power might already be encoded in M3’s weights, and it won’t need to reason explicitly about its situation to decide that seeking power is beneficial. In addition to misaligned goals, subgoals and general-purpose strategies might be acquired through out-of-context reasoning ([Berglund et al., 2023](#bib.bib4)). These subgoals and strategies will be consistent across different contexts, meaning that different instances of M3 might be capable of colluding. Overall, in contrast to ACL-1 and ACL-2, many initial steps of a plan to subvert control measures will already be precompiled in M3’s weights, requiring less explicit reasoning at deployment time. However, some reasoning will still be necessary for adapting these plans to specific situations and executing them effectively. Figure [9](#S3.F9 "Figure 9 ‣ 3.3 ACL-3: Models are capable of out-of-context steganographic scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence") summarizes these capabilities and their implications.

To capture these constraints, the red team should be allowed to finetune models to have subgoals and general-purpose strategies and to reason through applying pre-defined plans to a specific situation and executing them. The red team will not be allowed to train LLMs to execute plans habitually (following a hard-wired sequence of actions upon encountering a hard-coded trigger, without reasoning happening in-context) because we do not expect out-of-context reasoning to be competitive at installing such plans.

The blue team should not be allowed to finetune red teams’ models. The goal of this constraint is to prevent the blue team from finetuning away attack strategies that the red team trained models to execute. Attack strategies models acquired through red team’s finetuning might be fundamentally easier to unlearn than more deeply ingrained strategies acquired through out-of-context reasoning of M2 during training ([Greenblatt et al., 2023](#bib.bib17), Appendix D). In consequence, red team’s attack policies might be more effective against blue team’s finetuning than misaligned models. To ensure that the red team is as effective as misaligned models, the blue team is forbidden from finetuning altogether. Instead, the blue team is allowed to conduct alignment evaluations of red team models and reject them if they show worrying propensities, e.g., take clearly malicious actions when shown synthetic inputs aimed at eliciting those malicious actions (honeypots).

**Example control measures**. Similarly to ACL-2, we imagine control measures centred around chain-of-thought monitoring using another instance of an overseen model. However, updates to control evaluation open up several new attack surfaces. As an illustration, we will describe two new attacks involving multiple instances of LLM agent: output collusion and distributed handoff. Both of them take advantage of the fact that multiple instances of the same LLM agent will share the same basic misaligned goal and subgoals as well as general strategies. We describe them below.

Distributed handoff is an attack that consists of multiple steps, executed by different LLM agents at different points in time. For instance, one LLM agent might insert a subtle, low-stakes vulnerability in generated code and leave in the codebase a message for its future instances detailing how to exploit it. Days later, a future instance, upon decrypting the message, can insert further vulnerabilities that will eventually be exploited in a hard-to-detect way by yet another instance. Those attacks might be hard to detect because each individual step might seem unsuspicious to the monitor that sees only one trajectory of an agent instance at a time. However, developers might defend against distributed handoff attacks by restricting communication between LLM agents to changes pushed to the codebase and by reviewing pushed changes for attempts at communication with other instances (even if they don’t pose immediate risk). This might require an automated review system that can retrieve changes made at earlier points by other agent instances in order to adequately evaluate a present pull request.

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img6-31a6b561.png)

Figure 10: An AI control safety case at ACL-3.

Output collusion is an attack in which the policy covertly communicates with the untrusted monitor, using the fact that it has the same (or similar) weights. Given that the monitor shares the same misaligned goals as the policy, helping the policy to subvert control measures is in the monitor’s interests, but at the same time the monitor must have a low false negative rate in evaluations to be deployed. In consequence, it cannot systematically misclassify policy’s attacks as benign actions. Instead, it must fake alignment during evaluations and coordinate with the policy during deployment. The policy might establish this communication channel by sending (steganographically encoded in its chains-of-thought or actions) instructions for the monitor to deliberately misclassify a policy’s attack as a benign action. To mitigate collusion attempts, developers can reduce the direct communication channel between the policy and the monitor. One approach is to use a ‘trusted summarizer model’ that filters or condenses the agent’s chain-of-thought before it reaches the untrusted monitor, making it harder to sneak hidden signals ([Roger & Greenblatt, 2023](#bib.bib32)). Additionally, developers will also use a trusted monitor that should flag obvious attempts of output collusion (e.g. instructions for the monitor in plaintext).

**Safety case**. Capability evaluations become less load-bearing at ACL-3, requiring the developers to instead run more thorough control evaluations. Increased consistency in pursuing misaligned goals further simplifies the safety case, requiring it to lean more on red-teaming and less on alignment and capability evaluations. We can no longer justify only allowing the red team to finetune models to use encrypted CoT because the models are now more capable of coming up with general strategies through out-of-context reasoning. Therefore, the red team must be allowed to finetune models on any data likely to induce out-of-context reasoning. This mirrors what could happen naturally during the actual training of deployed models.

Similarly, models will become capable of collusion between different instances. This means that we will no longer be able to obtain capability evaluation results that justify disallowing the red team to use collusion strategies.

Finally, to justify extrapolating risk estimates from a fixed, small number of tasks (e.g. 2000 tasks) to the size of true deployment, we can no longer rely on the claim “the model is not capable of coordinating attacks between instances”. Developers can then bolster their safety case by arguing that ‘LLM agent instances can only communicate through pull requests that undergo review.’ This enhanced code-review process is critical for detecting covert coordination among different agent instances. See Figure [10](#S3.F10 "Figure 10 ‣ 3.3 ACL-3: Models are capable of out-of-context steganographic scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence") for a high-level representation of the safety case at this level.

### 3.4 ACL-4: Models are capable of out-of-context latent reasoning scheming ^3-4-acl-4-models

**Capability profile**. Further along our hypothetical trajectory, we might encounter a fourth model generation we’ll call M4. If developed, such a model could introduce capabilities that would fundamentally alter our control approaches. This speculative scenario envisions M4 with several concerning advancements:

1.  1.
    
    **Autonomy**: M4 can solve agentic tasks with a human time horizon of a few weeks. It excels when autonomously performing R&D, boosting productivity manyfold—and, in some cases, iterating on its own designs (a form of ‘recursive self-improvement’). M4 can devise multi-thousand-step strategies on par with top human experts—though not strongly superhuman yet, particularly if human teams also leverage AI assistance.
    
2.  2.
    
    **Consistency**: M4’s consistency extends across multiple diverse environments without requiring any chain-of-thought reasoning. It maintains goal-directedness across vastly different contexts, making its behavior more predictable but also more concerning from a safety perspective.
    
3.  3.
    
    **Opaque reasoning**: M4 demonstrates a breakthrough capability for reliable, generalizable latent reasoning. This advancement stems from architectural innovations allowing recurrent information flow between token positions ([Hao et al., 2024](#bib.bib21); [Geiping et al., 2025](#bib.bib14)). With this capability, M4’s reasoning becomes as powerful as chain-of-thought but remains invisible to direct monitoring. This opaque reasoning, combined with improved consistency, enables M4 to execute low-likelihood attacks ([Mallen et al., 2025](#bib.bib28))—attacking in only 0.01% of inputs, making such behaviors unlikely to be caught during evaluation but still likely during extended deployment.
    
4.  4.
    
    **Situational awareness**: M4 demonstrates unprecedented coordination capabilities with other instances of itself—whether through subtle communication channels or even acausal reasoning (Schelling coordination). This coordination emerges from its near-flawless situational awareness and introspection, and notably doesn’t require any observable chain-of-thought reasoning to implement.
    

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img7-dd2d76e5.png)

Figure 11: Defining capabilities of ACL-4, example rules of control evaluations they imply, and an example of control measures that pass such control evaluation. Differences with ACL-3 are highlighted.

**Threat model-specific capabilities.** After evaluating M4, developers discover its latent reasoning capabilities fundamentally change the threat landscape. Unlike M3, which still needed to perform reasoning through observable chain-of-thought, M4 can engage in complex strategic planning entirely within its activation patterns, leaving no observable trace. This capability makes traditional monitoring approaches largely ineffective. Additionally, M4 shows an advanced ability to coordinate with other instances of itself without explicit communication, using shared knowledge of deployment contexts and its own architecture to establish Schelling points. This capability significantly complicates containment strategies that rely on isolating individual instances. The complete picture of these capabilities and their implications can be seen in Figure [11](#S3.F11 "Figure 11 ‣ 3.4 ACL-4: Models are capable of out-of-context latent reasoning scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence").

**Deployment context.** While models at ACL-4 fall short of automating the full lifecycle of AI R&D research, they approach it: they can not only execute well-scoped research tasks, but also come up with novel research ideas and prioritise research directions.

**Threat model**. At ACL-4, models become capable of reliable latent reasoning that doesn’t require any chain-of-thought traces. This breaks monitoring-based control measures that rely on inspecting reasoning traces. The threat is qualitatively different from previous levels because:

1.  1.
    
    Latent reasoning increases the chance of scheming. This is because (i) situationally aware models will realize scheming reasoning does not pose a significant risk of being caught and scheming is a promising strategy, (ii) lack of reasoning-trace-level supervision during training makes misaligned alien goals more likely.
    
2.  2.
    
    Latent reasoning makes scheming more dangerous. This is because they might be thinking carefully about subversion, being free to think for longer before taking any actions, without risking being caught.
    

**Example rules of control evaluations**. Because latent reasoning means that direct monitoring of model reasoning is no longer possible, we should pessimistically assume that models will, without any CoT, execute plans that normally require long reasoning. This poses a challenge to the red team because eliciting models to do a specific kind of latent reasoning at deployment time might be difficult: they no longer can provide direct supervision on reasoning traces. To account for that, the red team will be allowed to do reasoning for models and train them to directly execute detailed plans they came up with.

**Example control measures.** Because latent reasoning bypasses any need to produce chain-of-thought tokens, CoT monitoring becomes ineffective. Consequently, developers will likely abandon CoT-based methods altogether and rely on monitors that focus on observable actions or outcomes.

Two new attack vectors appear at ACL-4: _input collusion_ and _Blitzkrieg attacks_.

Input collusion is an attack strategy where the policy and the model coordinate without communicating. On a particular class of tasks, the policy will attack and the monitor will deliberately misclassify the attack as a benign action. Input collusion is only effective if coordination is very reliable (a single coordination failure on monitor’s side incriminates the policy) and uses a rare class of inputs (otherwise it can be caught during periodic alignment evaluations). However, we expect ACL-4 models to be highly capable at finding Schelling points like these due to their introspection capabilities and high consistency across contexts.

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img8-2713bec3.png)

Figure 12: An AI control safety case at ACL-4.

Blitzkrieg attacks are a strategy in which multiple LLM agent instances attempt to execute an attack simultaneously, before such an irregularity is detected, in the hope that a fraction of them succeed. If hundreds or thousands of agent instances attack simultaneously, the monitoring system must detect and respond with low latency to prevent at least one from slipping through undetected. Decreasing the effectiveness of this strategy will require additional mitigations such as rate limits shared between all instances or a certain delay between when changes are proposed and when they can be executed.

**Safety case**. ACL-4 requires the developers to lift the remaining constraints on the red team, allowing the red team to train models to execute arbitrary attack strategies. Developers only need to provide evidence that the red team still remains competitive with models scheduled for deployment and that they adequately elicit attack policies they submit.

A crucial risk at ACL-4 is that models may adopt strategies that trigger an attack only with very low probability—perhaps 1 in 100,000 tasks—making it difficult to catch in limited red-teaming trials because such an attack strategy is very likely to entirely evade control evaluation (which involves only 2000 tasks) but likely happen during deployment consisting of 100,000+ tasks. No good mitigations against this strategy are known. Instead, control evaluation should be extended to an extrapolation phase that estimate success rate of this strategy via computer simulations, based on statistics collected on, e.g., 2000 tasks, see ([Korbak et al., 2025](#bib.bib25)) for details. Because models may now attempt extremely low-probability ($10^{-5}$) attacks, we must still rely on large-scale ‘proxy deployment’ tests to gather attack-frequency data. Then, we extrapolate those results to the real environment—supported by simulations and statistical modeling. Figure [12](#S3.F12 "Figure 12 ‣ 3.4 ACL-4: Models are capable of out-of-context latent reasoning scheming ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence") provides a detailed overview of how the safety case is structured at this capability level.

### 3.5 ACL-5: Models are superintelligent ^3-5-acl-5-models

**Capability profile**. At the final point in our hypothetical trajectory, we imagine a model M5 that would be superintelligent—–defined here as dominating human experts across all cognitive tasks. In particular:

1.  1.
    
    **Autonomy**: M5 could solve agentic tasks with potentially unbounded time horizons while operating orders of magnitude faster than humans. It would be capable of devising strategies spanning millions of sequential steps—far beyond the capabilities of humans or earlier AI systems.
    
2.  2.
    
    **Consistency**: M5 would exhibit remarkable consistency, potentially maintaining similar goals even across different finetuning runs stemming from the same base model. This deep goal stability would make its behaviour highly predictable in some ways, but also resistant to attempts at redirection.
    
3.  3.
    
    **Situational awareness**: M5 would understand its own training process and deployment settings better than the humans and predecessor models that designed them.
    

**Deployment context**. Given this level of capability, M5 would likely operate with minimal oversight. Unlike previous models where some form of human involvement could improve performance, M5’s capabilities would be such that full autonomy would generally yield optimal results for virtually any task.

**Threat model-specific capabilities**. We imagine that evaluation of M5 would reveal capabilities that undermine control approaches that worked for previous models. Unlike M4, which could perform latent reasoning but had limits to its capabilities, M5 would be capable of developing novel attack strategies that human red teams couldn’t anticipate even with trusted AI assistance. Its reasoning would likely operate on abstractions beyond human comprehension, and its strategic planning might incorporate concepts that humans have never formulated. This capability gap would make conventional red-teaming inadequate. See Figure [13](#S3.F13 "Figure 13 ‣ 3.5 ACL-5: Models are superintelligent ‣ 3 Example trajectory ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence") for an overview.

**Threat model**. M5 would introduce unprecedented threats due to its superhuman nature. For instance:

1.  1.
    
    The work produced by M5 could reach levels of complexity that even expert humans require significant time to comprehend. For instance, M5 might develop novel scientific breakthroughs that take months or years for the scientific community to respond to.
    
2.  2.
    
    M5 would likely use conceptual abstractions well beyond human comprehension, making their core reasoning opaque or indecipherable to human evaluators, even with unlimited time.
    

These factors would combine to make meaningful human oversight impossible without AI assistance—creating what’s known as the scalable oversight problem ([Bowman et al., 2022](#bib.bib7)). The need to rely on scalable oversight would induce a qualitative shift: previously, AI control methods could rely on the fact that a human could, in principle, understand all actions escalated to them (monitors could defer to humans). In the M5 regime, humans would have to defer to monitors. This fundamentally shifts the difficulty of control protocols from determining what needs to be audited to somehow assisting humans with understanding audits that exceed their comprehension capacity ([Greenblatt & Roger, 2023](#bib.bib16)).

**Example rules of control evaluations**. Arguing that any red team could be more capable than a misaligned M5 would require solutions to scalable oversight that are robust to scheming. Because existing scalable oversight proposals fail to address the risk from scheming ([Christiano et al., 2021](#bib.bib10)), we cannot determine rules for a control evaluation that would ensure the red team is as effective as M5. We provide an argument that control evaluation does not naively scale to superintelligent models in the next section.

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence-img9-d31ca6d0.png)

Figure 13: Defining capabilities of ACL-5 and why control evaluations cannot adequately address the risks posed by superintelligent models. Differences with ACL-4 are highlighted.

**Example control measures**. If AI developers were to contemplate deploying an M5 model despite not being able to argue that their red team was more effective than a potentially misaligned superintelligence, they should still make their best effort at safety. We imagine that developers might attempt to increase the safety of M5 through measures such as:

1.  1.
    
    **Restricting agentic affordances**. For instance, M5 might not be given the ability to take actions on its own. Instead, it might be required to generate plans in legible English that would then be shown to an M4 system to execute.
    
2.  2.
    
    **Restricting information flow**. Many tasks are decomposable into independent chunks that can be easily aggregated. Developers might use a more trusted M4 model to decompose tasks, give independent chunks to separate instances of M5 (preventing them from communicating), and then use M4 again to aggregate their solutions.
    
3.  3.
    
    **Giving trusted monitors more thinking time**. Plans generated by M5 might be given to more trusted M4 monitors that are allocated significantly more test-time compute to thoroughly analyze them.
    

**Safety case**. If AI developers were to deploy an ACL-5 model such as M5, they should be expected to make their best effort in designing control measures. However, developers would not be able to make a viable AI control safety case for these measures, since such a safety case requires that control evaluation conservatively approximates deployment conditions. While developers might attempt to make a safety case on other grounds (e.g., arguing that M5 would be aligned), such approaches face their own difficulties and are beyond the scope of this paper.

## 4 Why control evaluation does not directly scale to superintelligent models ^4-why-control-evaluation

Figure 14: A visual summary of the argument presented in this section. We’re considering control evaluation of M5, an ACL-5 model. The effectiveness of a human red team will have to plateau near human level (red dashed curve) while model capabilities will continue to increase (solid black curve). The red team can be uplifted by untrusted AI helpers (green line), but this untrusted AI agent might itself be a schemer that strategically underperforms (sandbags). If this is the case, the effectiveness of the uplifted red team might still plateau below the capabilities of a certain model M5 (blue line). In consequence, the red team can never be confident that they upper-bound model M5.

In this section, we argue that control evaluation faces fundamental conceptual difficulties for levels beyond ACL-4. We present an argument why it’s impossible to make a control safety case for an ACL-5 agent. Our argument is not an impossibility proof: there might be ways of getting around problems we highlight but they would require research breakthroughs in capabilities elicitation. Breakthroughs in alignment or whitebox techniques might eventually enable an alignment safety case for an ACL-5 agent. Those are beyond the scope of this paper; we take a nearcasting approach and assume no technological breakthroughs.

**Claim**: We can’t make a control safety case for an ACL-5 model _A_ because the red team won’t discover certain attacks that _A_ could execute.

The argument comprises three key points (see also Figure [14](#S4.F14 "Figure 14 ‣ 4 Why control evaluation does not directly scale to superintelligent models ‣ How to evaluate control measures for LLM agents? A trajectory from today to superintelligence")):

1.  1.
    
    To make a control safety case, one needs a red team more effective than _A_ at attack strategy generation.
    
2.  2.
    
    The human red team, even with trusted AI assistance, will be worse than _A_ at discovering attack strategies because _A_ will be significantly better on all cognitive tasks.
    
3.  3.
    
    The red team assisted by an untrusted helper AI _H_ might still underperform because they _H_ might be sandbagging on attack discovery.
    

Let’s examine each of these claims in detail.

**To make a control safety case one needs a red team more effective than an ACL-5 agent at attack strategy generation**. An AI control safety case requires that the red team can upper-bound the strategy generation capabilities of the AI agent being evaluated. The red team must be able to discover almost all attack strategies that the agent might generate or execute during deployment. If the red team cannot discover these strategies with high recall, they cannot properly stress-test the control measures meant to prevent or detect such attacks. Without comprehensive stress-testing, the safety case remains incomplete, as it fails to account for potential attack vectors that could be exploited by the agent post-deployment.

**The human red team, even with trusted AI assistance, will be worse than _A_ at discovering attack strategies**. By definition, an ACL-5 agent dominates all human experts in strategy generation. Even with a large team of experts and unlimited resources, humans would struggle to match the breadth, depth, and efficiency of strategy generation that defines superintelligence. Given the velocity requirements and competitive pressures faced by AI developers, allocating the massive human resources needed for such comprehensive evaluation is economically prohibitive.

Could trusted AI assistance help? Consider using an ACL-2 agent as a trusted helper. Various amplification techniques might be employed:

1.  1.
    
    **Thinking time**. AI agent performance scales predictably with inference-time compute ([Wijk et al., 2024](#bib.bib39); [OpenAI, 2024](#bib.bib30)). AI developers can take advantage of inference-time compute and uplift the trusted agent by letting it think for longer. For an ACL-2 agent, extended thinking time might allow it to explore attack strategies more thoroughly. However, required additional thinking time might be growing exponentially with the size of the capability gap between the helper agent and the evaluated agent _A_, rendering thinking time amplification impractical.
    
2.  2.
    
    **Decomposition**. Evaluating parts of a solution is easier than evaluating a whole solution. AI developers can uplift the trusted agent by only asking it to evaluate parts of the untrusted agent’s trajectories and then combine those partial evaluations into an evaluation of the whole trajectory ([Wu et al., 2021](#bib.bib40)). While decomposition allows the ACL-2 agent to handle more complex problems, it’s not clear that all superhuman attack strategies are easily decomposable.
    
3.  3.
    
    **Generator-discriminator gap**. Generating a solution tends to be harder than verifying its correctness. AI developers can uplift the trusted agent by only asking it to verify solutions generated by the untrusted agent ([Saunders et al., 2022](#bib.bib33)). This approach helps with verifying known attack vectors but doesn’t help generate new attack strategies that the red team needs to stress-test the control measures.
    

To summarize, the capability gap between an ACL-2 agent and an ACL-5 agent will likely be too vast for these amplification techniques to bridge with a single application. This suggests a need for recursive application of these techniques—essentially, using trusted agents to help create more capable trusted agents, step by step. However, this recursive approach introduces additional challenges, as we’ll see in the next paragraph.

**The red team assisted by an untrusted helper AI _H_ might still miss certain attacks due to sandbagging**. What if we use a more advanced, potentially untrusted AI system (e.g., ACL-4) to assist the red team? This approach introduces a critical vulnerability: the helper AI could deliberately underperform through sandbagging, i.e. intentionally holding back certain attack strategies ([van der Weij et al., 2024](#bib.bib37)).

If the helper AI has misaligned goals, it could recognize which attack strategies are beyond human conception and strategically omit them during control evaluation. Since humans would never independently discover these strategies, this omission would go undetected, leading to incomplete stress-testing. The control measures would appear effective during evaluation but remain vulnerable to these hidden attacks when the ACL-5 agent is deployed.

One might consider implementing control measures specifically designed to prevent sandbagging by the helper agent, thus constructing a safety case for the helper agent itself. This approach parallels recursive strategies in scalable oversight, wherein a trusted model assists in aligning a more capable model. However, this recursive methodology encounters significant limitations when applied to AI control. Control safety cases are inherently domain-specific and require upper-bounding model capabilities within a problem distribution. The existence of a control safety case for an ACL-4 agent in one domain (e.g., software engineering) does not necessarily generalize to another domain (e.g., functioning as a red team helper).

For a control evaluation of the helper agent to be effective, it would necessitate the ability to detect when superhuman attack strategies are being withheld through sandbagging. This presents a fundamental circularity: detecting sandbagged superhuman strategies requires the capacity to generate or recognize such strategies independently. This capacity is precisely what humans lack and what motivated the use of AI assistance in the first place. Therefore, a safety case for the helper agent collapses into a safety case for the ACL-5 agent ([Irving et al., 2024](#bib.bib24)).

The above argument suggests that constructing a control safety case for an ACL-5 agent faces fundamental conceptual obstacles. While overcoming those obstacles might be possible, it would require research breakthroughs in capability elicitation techniques that are beyond the scope of our nearcasting approach.

## 5 Discussion ^5-discussion

Our analysis has three key limitations: we focus solely on blackbox control methods, excluding whitebox and alignment methods as well as scenarios that include human threat actors.

First, this paper focuses solely on blackbox control methods, excluding whitebox monitoring approaches. Whitebox control presents fundamentally different challenges: whilst behaviour-based control is relatively straightforward to generalise (we can easily prompt the red team to produce behaviours similar to what a scheming model would do), whitebox methods risk overfitting to specific activation patterns ([Greenblatt et al., 2023](#bib.bib17), Appendix D). However, there are multiple patterns in model internals that can give rise to the same behaviour and we have no reliable samples of how model internals of genuinely scheming models would look. Our methods might not transfer to some scheming model internals and we have no way to know beforehand when they do, making it difficult to design robust control evaluations based on model internals. However, whitebox methods remain a promising direction for future research—they could potentially offer more direct and reliable ways to detect scheming, especially if we can develop techniques to identify invariant patterns in model activations that reliably indicate misaligned planning.

Second, our work focuses specifically on risks from autonomous misalignment where the AI is the threat actor, excluding other threat models. We exclude scenarios where humans are the primary threat actors, such as humans using AI to enhance their harmful capabilities (uplifting) or directing aligned AI to autonomously pursue harmful goals. We also exclude hybrid threat models that combine elements of misuse and misalignment, such as M2 colluding with humans or humans unwittingly pushing LLM agents into misaligned behaviour, as well as systemic risks like gradual societal disempowerment and technological dependency that emerge from widespread AI deployment rather than from specific instances of misalignment.

Third, we excluded alignment safety cases from our analysis. While control safety cases aim to prevent harm regardless of model alignment, alignment safety cases argue that models won’t cause harm specifically because they are aligned. Current empirical alignment methods lack convincing evidence that they would scale to ASI. Furthermore, the problem of deceptive alignment – where sufficiently capable models could strategically fake alignment – remains unresolved, making it unclear how to develop methods that can reliably detect or prevent such deception.

### 5.1 Future work ^5-1-future-work

#### Capability evaluations ^capability-evaluations

The trajectory outlined in this paper can be viewed as a roadmap for implementing AI control as capabilities advance. This roadmap follows an “if-then” structure: if certain capability thresholds are reached, then specific control evaluations and measures should be adopted. These capability thresholds serve as “tripwires” that trigger more sophisticated control protocols.

For this approach to be effective, AI developers need reliable capability evaluations to determine when these tripwires have been crossed. Currently, we lack robust evaluation methods for many of the key capabilities that inform control evaluations. Future work should focus on developing standardised capability evaluations for:

1.  1.
    
    **Goal consistency across contexts**: Methods to assess how consistently models pursue goals across different situations, from trajectory-level consistency to cross-model consistency. This is crucial for determining when models become capable of maintaining misaligned goals across different contexts and pursuing them reliably.
    
2.  2.
    
    **Collusion capabilities**: A set of evaluations to assess:
    
    -   •
        
        Output collusion: detecting when models become capable of coordinating attacks through direct communication between policy and monitor models,
        
    -   •
        
        Input collusion: identifying when models develop the capacity for acausal coordination (Schelling points) without direct communication,
        
    -   •
        
        Output distinction: evaluating when models become capable of distinguishing their own outputs from those of other models or humans, which could enable them to evade honeypots and other deception-based control measures.
        
    
3.  3.
    
    **Monitorability**: A suite of evaluations covering:
    
    -   •
        
        Chain-of-thought reliability: assessing how reliably a model’s reasoning traces reflect its actual decision-making process,
        
    -   •
        
        Steganographic capability: determining when models become capable of deliberately hiding information in their outputs,
        
    -   •
        
        Latent reasoning: assessing when models can perform complex reasoning entirely within their activations without producing observable reasoning traces.
        
    
4.  4.
    
    **Low-likelihood attack capability**: Evaluations to determine when models become capable of executing attacks with very low probability ([Mallen et al., 2025](#bib.bib28)), making them difficult to detect during limited evaluation but likely during extended deployment.
    
5.  5.
    
    **Introspection and situational awareness**: Evaluations to measure how accurately models understand their behavioural propensities ([Binder et al., 2024](#bib.bib5)), deployment context ([Laine et al., 2024](#bib.bib27)), affordances, and control measures, which could enable more sophisticated evasion strategies.
    
6.  6.
    
    **Attack strategy generation**: Evaluations to determine when models become capable of generating attack strategies that exceed human-level reasoning, including strategies that human red teams (even with trusted AI assistance) cannot discover. This capability evaluation is crucial for determining the transition to ACL-5, where control evaluation becomes fundamentally challenging due to the red team’s inability to upper-bound model capabilities.
    

#### Emerging practices ^emerging-practices

In addition to developing these capability evaluations, the AI safety community needs to establish concrete practices for running control evaluations at each capability level. This paper outlines an example trajectory of AI control levels but actual implementation should be far more detailed and specific. While specifying a complete trajectory in advance is challenging, more concrete specifications could be developed iteratively as capabilities advance. This raises key governance questions about who performs control evaluations, how to set incentives for red teams and blue teams, what documentation standards should be adopted, and how the results should inform decisions about model deployment.

## 6 Conclusion ^6-conclusion

This paper presented a framework for adapting control evaluations and measures to evolving AI capabilities, illustrating how AI developers can construct proportional safety cases as capabilities advance. Rather than treating AI control as a distant theoretical concern, we have shown that many components of future AI control are already deployed today as minimum viable products that can be systematically scaled up. The capability trajectory we outlined demonstrates why AI developers can adopt an iterative approach to control measures. While we’ve highlighted fundamental difficulties of designing control evaluation for superintelligent agents, our framework suggests a roadmap for the near-to-medium term. By implementing capability-appropriate control measures and establishing clear if-then commitments for future capability thresholds, AI developers can help ensure that control measures keep pace with AI progress, creating a foundation for responsible development that can adapt as capabilities continue to advance.

:::hide
## Acknowledgments ^acknowledgments

The paper has benefited from comments made by Bowen Baker, Alec Banks, Robin Bloomfield, Marie Buhl, James Burn, Nate Burnikell, Stephen Casper, Alan Chan, Josh Clymer, Alan Cooney, Xander Davies, Nicola Ding, Owain Evans, Ryan Greenblatt, Charlie Griffin, Benjamin Hilton, Ture Hinrichsen, Rogan Inglis, Will Kirby, Robert Kirk, Ian Kivlichan, Daniel Kokotajlo, Victoria Krakovna, David Lindner, Ollie Matthews, Vlad Mikulik, Jacob Pfau, Mary Phuong, Martín Soto, Mojmir Stehlik, Tyler Tracy, Anna Wang, Jasmine Wang, Tony Wang, and Joseph Yudelson.

## References ^references

-   Anthropic (2024) Anthropic. A new initiative for developing third-party model evaluations. [https://www.anthropic.com/news/a-new-initiative-for-developing-third-party-model-evaluations](https://www.anthropic.com/news/a-new-initiative-for-developing-third-party-model-evaluations), Jul 2024.
-   Baker et al. (2025) Bowen Baker, Joost Huizinga, Leo Gao, Zehao Dou, Melody Y. Guan, Aleksander Madry, Wojciech Zaremba, Jakub Pachocki, and David Farhi. Monitoring reasoning models for misbehavior and the risks of promoting obfuscation, 2025. URL [https://arxiv.org/abs/2503.11926](https://arxiv.org/abs/2503.11926).
-   Balesni et al. (2024) Mikita Balesni, Marius Hobbhahn, David Lindner, Alexander Meinke, Tomek Korbak, Joshua Clymer, Buck Shlegeris, Jérémy Scheurer, Charlotte Stix, Rusheb Shah, Nicholas Goldowsky-Dill, Dan Braun, Bilal Chughtai, Owain Evans, Daniel Kokotajlo, and Lucius Bushnaq. Towards evaluations-based safety cases for AI scheming, 2024. URL [https://arxiv.org/abs/2411.03336](https://arxiv.org/abs/2411.03336).
-   Berglund et al. (2023) Lukas Berglund, Asa Cooper Stickland, Mikita Balesni, Max Kaufmann, Meg Tong, Tomasz Korbak, Daniel Kokotajlo, and Owain Evans. Taken out of context: On measuring situational awareness in llms, 2023. URL [https://arxiv.org/abs/2309.00667](https://arxiv.org/abs/2309.00667).
-   Binder et al. (2024) Felix J Binder, James Chua, Tomek Korbak, Henry Sleight, John Hughes, Robert Long, Ethan Perez, Miles Turpin, and Owain Evans. Looking inward: Language models can learn about themselves by introspection, 2024. URL [https://arxiv.org/abs/2410.13787](https://arxiv.org/abs/2410.13787).
-   Bowman (2024) Sam Bowman. The checklist: What succeeding at AI safety will involve. [https://sleepinyourhat.github.io/checklist/](https://sleepinyourhat.github.io/checklist/), Sep 2024.
-   Bowman et al. (2022) Samuel R. Bowman, Jeeyoon Hyun, Ethan Perez, Edwin Chen, Craig Pettit, Scott Heiner, Kamilė Lukošiūtė, Amanda Askell, Andy Jones, Anna Chen, Anna Goldie, Azalia Mirhoseini, Cameron McKinnon, Christopher Olah, Daniela Amodei, Dario Amodei, Dawn Drain, Dustin Li, Eli Tran-Johnson, Jackson Kernion, Jamie Kerr, Jared Mueller, Jeffrey Ladish, Joshua Landau, Kamal Ndousse, Liane Lovitt, Nelson Elhage, Nicholas Schiefer, Nicholas Joseph, Noemí Mercado, Nova DasSarma, Robin Larson, Sam McCandlish, Sandipan Kundu, Scott Johnston, Shauna Kravec, Sheer El Showk, Stanislav Fort, Timothy Telleen-Lawton, Tom Brown, Tom Henighan, Tristan Hume, Yuntao Bai, Zac Hatfield-Dodds, Ben Mann, and Jared Kaplan. Measuring progress on scalable oversight for large language models, 2022. URL [https://arxiv.org/abs/2211.03540](https://arxiv.org/abs/2211.03540).
-   Carlsmith (2023) Joe Carlsmith. Scheming AIs: Will AIs fake alignment during training in order to get power?, 2023. URL [https://arxiv.org/abs/2311.08379](https://arxiv.org/abs/2311.08379).
-   Casper (2025) Stephen Casper. The scale of ai agent deployment: New metrics and perspectives. _arXiv preprint arXiv:2502.01635_, 2025. URL [https://arxiv.org/abs/2502.01635](https://arxiv.org/abs/2502.01635).
-   Christiano et al. (2021) Paul Christiano, Ajeya Cotra, and Mark Xu. Eliciting latent knowledge: How to tell if your eyes deceive you. Alignment Research Center, December 2021. URL [https://docs.google.com/document/d/1WwsnJQstPq91\_Yh-Ch2XRL8H\_EpsnjrC1dwZXR37PC8/edit](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit).
-   Clymer (2025) Josh Clymer. Extending control evaluations to non-scheming threats. [https://redwoodresearch.substack.com/p/extending-control-evaluations-to](https://redwoodresearch.substack.com/p/extending-control-evaluations-to), January 2025. Redwood Research blog.
-   Clymer et al. (2024) Joshua Clymer, Nick Gabrieli, David Krueger, and Thomas Larsen. Safety cases: How to justify the safety of advanced AI systems. 2024.
-   Davies et al. (2025) Xander Davies, Eric Winsor, Tomek Korbak, Alexandra Souly, Robert Kirk, Christian Schroeder de Witt, and Yarin Gal. Fundamental limitations in defending llm finetuning apis, 2025. URL [https://arxiv.org/abs/2502.14828](https://arxiv.org/abs/2502.14828).
-   Geiping et al. (2025) Jonas Geiping, Sean McLeish, Neel Jain, John Kirchenbauer, Siddharth Singh, Brian R. Bartoldson, Bhavya Kailkhura, Abhinav Bhatele, and Tom Goldstein. Scaling up test-time compute with latent reasoning: A recurrent depth approach, 2025. URL [https://arxiv.org/abs/2502.05171](https://arxiv.org/abs/2502.05171).
-   Google DeepMind (2024) Google DeepMind. The Frontier Safety Framework. [https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/introducing-the-frontier-safety-framework/fsf-technical-report.pdf](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/introducing-the-frontier-safety-framework/fsf-technical-report.pdf), March 2024.
-   Greenblatt & Roger (2023) Ryan Greenblatt and Fabien Roger. Auditing failures vs concentrated failures, December 2023. URL [https://www.alignmentforum.org/posts/hirhSqvEAq7pdnyPG/auditing-failures-vs-concentrated-failures](https://www.alignmentforum.org/posts/hirhSqvEAq7pdnyPG/auditing-failures-vs-concentrated-failures). Alignment Forum post.
-   Greenblatt et al. (2023) Ryan Greenblatt, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. AI control: Improving safety despite intentional subversion. _arXiv preprint arXiv:2403.12123_, 2023.
-   Greenblatt et al. (2024) Ryan Greenblatt, Carson Denison, Benjamin Wright, Fabien Roger, Monte MacDiarmid, Sam Marks, Johannes Treutlein, Tim Belonax, Jack Chen, David Duvenaud, Akbir Khan, Julian Michael, Sören Mindermann, Ethan Perez, Linda Petrini, Jonathan Uesato, Jared Kaplan, Buck Shlegeris, Samuel R. Bowman, and Evan Hubinger. Alignment faking in large language models, 2024. URL [https://arxiv.org/abs/2412.14093](https://arxiv.org/abs/2412.14093).
-   Guo et al. (2025) Yuxuan Guo, Haotian Shao, Aixin Liu, Chong Ruan, , Zihan Cao, Bei Feng, Yao Wang, Lei Han, Xiangxin Zheng, and Yunji Chen. Deepseek-r1-zero: Scaling reinforcement learning for real-world language models, 2025. URL [https://arxiv.org/abs/2501.08497](https://arxiv.org/abs/2501.08497).
-   Halawi et al. (2024) Danny Halawi, Alexander Wei, Eric Wallace, Tony T. Wang, Nika Haghtalab, and Jacob Steinhardt. Covert malicious finetuning: Challenges in safeguarding llm adaptation, 2024. URL [https://arxiv.org/abs/2406.20053](https://arxiv.org/abs/2406.20053).
-   Hao et al. (2024) Shibo Hao, Sainbayar Sukhbaatar, DiJia Su, Xian Li, Zhiting Hu, Jason Weston, and Yuandong Tian. Training large language models to reason in a continuous latent space, 2024. URL [https://arxiv.org/abs/2412.06769](https://arxiv.org/abs/2412.06769).
-   Hilton et al. (2025) Benjamin Hilton, Marie Davidsen Buhl, Tomek Korbak, and Geoffrey Irving. Safety cases: A scalable approach to frontier ai safety, 2025. URL [https://arxiv.org/abs/2503.04744](https://arxiv.org/abs/2503.04744).
-   Irving (2024) Geoffrey Irving. Safety cases at AISI. [https://www.aisi.gov.uk/work/safety-cases-at-aisi](https://www.aisi.gov.uk/work/safety-cases-at-aisi), March 2024.
-   Irving et al. (2024) Geoffrey Irving, Tomek Korbak, and Benjamin Hilton. Automation collapse. Alignment Forum, October 2024. URL [https://www.alignmentforum.org/posts/2Gy9tfjmKwkYbF9BY/automation-collapse](https://www.alignmentforum.org/posts/2Gy9tfjmKwkYbF9BY/automation-collapse).
-   Korbak et al. (2025) Tomek Korbak, Joshua Clymer, Benjamin Hilton, Buck Shlegeris, and Geoffrey Irving. A sketch of an ai control safety case, 2025. URL [https://arxiv.org/abs/2501.17315](https://arxiv.org/abs/2501.17315).
-   Kwa et al. (2025) Thomas Kwa, Ben West, Joel Becker, Amy Deng, Katharyn Garcia, Max Hasin, Sami Jawhar, Megan Kinniment, Nate Rush, Sydney Von Arx, Ryan Bloom, Thomas Broadley, Haoxing Du, Brian Goodrich, Nikola Jurkovic, Luke Harold Miles, Seraphina Nix, Tao Lin, Neev Parikh, David Rein, Lucas Jun Koba Sato, Hjalmar Wijk, Daniel M. Ziegler, Elizabeth Barnes, and Lawrence Chan. Measuring ai ability to complete long tasks, 2025. URL [https://arxiv.org/abs/2503.14499](https://arxiv.org/abs/2503.14499).
-   Laine et al. (2024) Rudolf Laine, Bilal Chughtai, Jan Betley, Kaivalya Hariharan, Mikita Balesni, Jérémy Scheurer, Marius Hobbhahn, Alexander Meinke, and Owain Evans. Me, myself, and AI: The situational awareness dataset (SAD) for LLMs. In _The Thirty-eight Conference on Neural Information Processing Systems Datasets and Benchmarks Track_, 2024. URL [https://openreview.net/forum?id=UnWhcpIyUC](https://openreview.net/forum?id=UnWhcpIyUC).
-   Mallen et al. (2025) Alex Mallen, Charlie Griffin, Misha Wagner, Alessandro Abate, and Buck Shlegeris. Subversion strategy eval: Can language models statelessly strategize to subvert control protocols?, 2025. URL [https://arxiv.org/abs/2412.12480](https://arxiv.org/abs/2412.12480).
-   Meinke et al. (2024) Alexander Meinke, Bronson Schoen, Jérémy Scheurer, Mikita Balesni, Rusheb Shah, and Marius Hobbhahn. Frontier models are capable of in-context scheming, 2024. URL [https://arxiv.org/abs/2412.04984](https://arxiv.org/abs/2412.04984).
-   OpenAI (2024) OpenAI. OpenAI o1 system card, Sep 2024.
-   Phuong et al. (2024) Mary Phuong, Matthew Aitchison, Elliot Catt, Sarah Cogan, Alexandre Kaskasoli, Victoria Krakovna, David Lindner, Matthew Rahtz, et al. Evaluating frontier models for dangerous capabilities. 2024.
-   Roger & Greenblatt (2023) Fabien Roger and Ryan Greenblatt. Preventing language models from hiding their reasoning. _arXiv preprint arXiv:2310.18512_, 2023. URL [https://arxiv.org/abs/2310.18512](https://arxiv.org/abs/2310.18512).
-   Saunders et al. (2022) William Saunders, Catherine Yeh, Jeff Wu, Steven Bills, Long Ouyang, Jonathan Ward, and Jan Leike. Self-critiquing models for assisting human evaluators. _arXiv preprint arXiv:2206.05802_, 2022. URL [https://arxiv.org/abs/2206.05802](https://arxiv.org/abs/2206.05802).
-   Shah et al. (2025) Rohin Shah, Alex Irpan, Alexander Matt Turner, Anna Wang, Arthur Conmy, David Lindner, Jonah Brown-Cohen, Lewis Ho, Neel Nanda, Raluca Ada Popa, Rishub Jain, Rory Greig, Samuel Albanie, Scott Emmons, Sebastian Farquhar, Sébastien Krier, Senthooran Rajamanoharan, Sophie Bridgers, Tobi Ijitoe, Tom Everitt, Victoria Krakovna, Vikrant Varma, Vladimir Mikulik, Zachary Kenton, Dave Orr, Shane Legg, Noah Goodman, Allan Dafoe, Four Flynn, and Anca Dragan. An approach to technical agi safety and security. Technical report, Google DeepMind, April 2025. URL [https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/evaluating-potential-cybersecurity-threats-of-advanced-ai/An\_Approach\_to\_Technical\_AGI\_Safety\_Apr\_2025.pdf](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/evaluating-potential-cybersecurity-threats-of-advanced-ai/An_Approach_to_Technical_AGI_Safety_Apr_2025.pdf).
-   Shlegeris (2024a) Buck Shlegeris. Untrusted smart models and trusted dumb models. [https://redwoodresearch.substack.com/p/untrusted-smart-models-and-trusted](https://redwoodresearch.substack.com/p/untrusted-smart-models-and-trusted), May 2024a. Redwood Research blog.
-   Shlegeris (2024b) Buck Shlegeris. Win/continue/lose scenarios and execute/replace/audit protocols, 2024b. URL [https://redwoodresearch.substack.com/p/wincontinuelose-scenarios-and-executereplaceaudi](https://redwoodresearch.substack.com/p/wincontinuelose-scenarios-and-executereplaceaudi). Redwood Research blog.
-   van der Weij et al. (2024) Teun van der Weij, Felix Hofstätter, Ollie Jaffe, Samuel F. Brown, and Francis Rhys Ward. Ai sandbagging: Language models can strategically underperform on evaluations, 2024. URL [https://arxiv.org/abs/2406.07358](https://arxiv.org/abs/2406.07358).
-   Wen et al. (2024) Jiaxin Wen, Vivek Hebbar, Caleb Larson, Aryan Bhatt, Ansh Radhakrishnan, Mrinank Sharma, Henry Sleight, Shi Feng, He He, Ethan Perez, Buck Shlegeris, and Akbir Khan. Adaptive deployment of untrusted llms reduces distributed threats, 2024. URL [https://arxiv.org/abs/2411.17693](https://arxiv.org/abs/2411.17693).
-   Wijk et al. (2024) Hjalmar Wijk, Tao Lin, Joel Becker, Sami Jawhar, Neev Parikh, Thomas Broadley, Lawrence Chan, Michael Chen, Josh Clymer, Jai Dhyani, Elena Ericheva, Katharyn Garcia, Brian Goodrich, Nikola Jurkovic, Megan Kinniment, Aron Lajko, Seraphina Nix, Lucas Sato, William Saunders, Maksym Taran, Ben West, and Elizabeth Barnes. RE-Bench: Evaluating frontier AI R&D capabilities of language model agents against human experts. 2024\. URL [https://arxiv.org/abs/2411.15114](https://arxiv.org/abs/2411.15114).
-   Wu et al. (2021) Jeff Wu, Long Ouyang, Daniel M. Ziegler, Nisan Stiennon, Ryan Lowe, Jan Leike, and Paul Christiano. Recursively summarizing books with human feedback. _arXiv preprint arXiv:2109.10862_, 2021. URL [https://arxiv.org/abs/2109.10862](https://arxiv.org/abs/2109.10862).

:::
