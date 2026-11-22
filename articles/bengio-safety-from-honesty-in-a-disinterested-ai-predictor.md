---
title: "Safety from Honesty in a Disinterested AI Predictor"
author:
  - "Yoshua Bengio"
  - "Oliver Richardson"
  - "Tomáš Gavenčiak"
  - "Michael Cohen"
  - "Rory Svarc"
  - "Damiano Fornasiere"
  - "Gaël Gendron"
  - "David Hyland"
  - "Aton Kamanda"
  - "Adam Oberman"
  - "Francis Rhys Ward"
  - "Anna Gavenčiak"
  - "Jacob Livingston Slosser"
  - "Vincent Mai"
  - "Iulian Serban"
  - "Joumana Ghosn"
source_url: "https://arxiv.org/pdf/2606.29657"
published: 2026-06-28
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "opus"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Abstract ^abstract

As AI systems become more capable, training procedures that optimize for downstream outcomes risk introducing implicit agency: goal-directed behavior that designers never specified. We present a formal safety argument for the Scientist AI (SAI) Predictor, trained to approximate the Bayesian posterior conditioned on a dataset of "epistemically contextualized" natural-language statements. We argue that such a Predictor can honestly predict agents, actions, and their consequences without itself being an agent that selects outputs to achieve goals. This rests on data representation and on the training procedure. Epistemic contextualization of text distinguishes latent factual claims from communication acts, so expressions of goals are treated as evidence to be explained rather than drives the model adopts. With a posterior-seeking training objective, this is intended to drive the Predictor toward calibrated, cautious predictions. Training proceeds so downstream effects of deploying a prediction never serve as a reward signal; any agency the system needs is supplied by explicit scaffolding constrained by guardrails. We prove that, under assumptions on the training dynamics and on the argued sparsity of dangerous Predictors, the probability that training produces a Predictor whose guarded deployment carries residual harm above a specified threshold is small: a dangerous Predictor would have to underestimate harm in a coordinated way across many queries while such coordinated patterns are rare under the initialization distribution and receive no direct training signal. Safety and accuracy are jointly supported in this framework, since the constraints that secure accuracy are the same ones that make coordinated deception costly. These guarantees against misalignment and agency arising from within the Predictor itself do not preclude the use of the Predictor as part of an agentic system.

## Introduction ^introduction

Advances in AI could accelerate scientific discovery, improve decision-making under uncertainty, as well as help manage complex systems in domains as varied as medicine and public policy. As noted in the International AI Safety Report (Bengio et al. 2025a), realizing these benefits at scale requires managing and mitigating the associated risks, especially in settings where failures are costly, hard to detect in advance, or amplified by widespread deployment. One central and well-documented worry is that, as AI systems become more capable, they will produce outputs that systematically steer decisions toward outcomes that differ from what developers and users intend—this is what is called _AI misalignment_.

Theoretical arguments suggest that instrumental subgoals such as self-preservation and power-seeking are near-universal consequences of goal-directed optimization (Omohundro 2018; Bostrom 2012; Russell 2019; Zhuang and Hadfield-Menell 2020; Turner et al. 2021; Cohen et al. 2022; Cohen et al. 2024; Bengio et al. 2025b), where a sufficiently capable system will tend to acquire them regardless of what its terminal goal is, simply because such subgoals are useful for almost any objective. AI systems based on LLMs trained for next-token prediction may learn to imitate human drives—such as self-preservation—in ways that are implicit and uncontrolled (Ngo et al. 2022). LLM sycophancy (Sharma et al. 2023) provides a contemporary example of AI misalignment, which can be harmful to psychologically vulnerable users who receive unwarranted validation of dangerous beliefs or plans (Cheng et al. 2026). Documented empirical evidence of deceptive and self-preservation behaviors has also been mounting (Bengio et al. 2025a; Bengio et al. 2026; Greenblatt et al. 2024; Meinke et al. 2024; Anthropic 2025; Betley et al. 2025), including new abilities to detect when a system is being evaluated (or, possibly, even trained (Fornasiere et al. 2026)) and to adjust behavior accordingly (Abdelnabi and Salem 2025), as well as to resist shutdown when faced with incomplete objectives (Schlatter et al. 2026). Misalignment may also be involved in cases of misuse where a malicious user manages to obtain dangerous knowledge from the AI in spite of its safety training and guardrails, including, e.g., for dangerous cyberattacks (Bengio et al. 2026). Given that the risks from misalignment grow as AI capabilities continue to advance (Omohundro 2018; Zhuang and Hadfield-Menell 2020; Cohen et al. 2022), AIs with human-like drives and superhuman capabilities could be dangerous (Russell 2019; Bengio et al. 2024; Amodei et al. 2016).

We posit that the root cause of such worries stems from _learned implicit agency_: goal-directed behavior that was not explicitly specified by the AI designers and may not even be detectable through the system’s stated outputs. Pretraining to imitate human constructions plausibly leads to imitating human drives. This problem is further amplified by post-training techniques like reinforcement learning from human feedback (Christiano et al. 2017; Ouyang et al. 2022), which explicitly reward outputs for their downstream effects on evaluator preferences. Together, these factors create a selection pressure toward outputs which implicitly _steer_ the world rather than simply providing honest responses to user queries.

We propose **Scientist AI** (SAI) as a potential solution to such concerns. Underlying the SAI approach is a conceptual distinction between (i) _honestly_ predicting the behavior of agents and the consequences of actions, and (ii) _being_ an agent that makes (potentially dishonest) predictions in order to influence outcomes. An honest Predictor models others’ planning, deception, and instrumental behavior and forecasts the downstream effects of its own deployed outputs—these are predictions about the world, not choices made to bring about a preferred outcome (Li et al. 2024). The Scientist AI design (Bengio et al. 2025b) aims to achieve (i) while avoiding (ii) by training a non-agentic Predictor to approximate the Bayesian posterior over Boolean natural-language statements via a _consequence-invariant_ training process—that is, a training process whose objective and updates are functions of the fixed dataset and prior alone, driven by the removal of epistemic inconsistencies (Richardson 2022; Richardson 2024) with no on-policy feedback loop whereby the model’s own deployed outputs generate training gradients or deployment outcomes shape the selection of future Predictors. We call such a Predictor _disinterested_: it is given no stake in which outcomes its predictions bring about, and this disinterest is what consequence-invariant training is designed to secure. Historically, work on AI oracles attempts to emulate such a disinterested oracle by containing a fully-formed superintelligence (Babcock et al. 2017; Alfonseca et al. 2016; Armstrong et al. 2012). We take inspiration from the counter-factual disconnection approach of Babcock et al. (2017), but, more fundamentally, our approach is to train the AI within the box, so that it is highly unlikely to develop preferences at all. Developing an honest, non-agentic Predictor would be very useful (Bostrom 2012; Bengio et al. 2025b)—for forecasting, hypothesis generation, and scientific work, and could serve as a guardrail inside safer agentic systems. In our approach, any required agency (e.g., for creative thought) is placed in explicit, auditable scaffolding code that is gated by the non-agentic Predictor.

We develop two semi-formal arguments that hold independently—about the _accuracy_ of the Predictor’s predictions and the _safety_ of its deployed outputs—both resting on _honesty_ as an approximation of the Bayesian posterior over contextualized statements. The remainder of this section introduces the SAI pipeline layout and defines the scope of our guarantees. Section [[#^the-informal-argument-and|2]] frames the accuracy and safety arguments informally, followed by formal treatments in Sections [[#^forming-a-probabilistic-model|3]] and [[#^the-case-for-safety|5]].

### Sketch of the Scientist AI ^sketch-of-the-scientist

The SAI operates on a vast set of Boolean variables, called _statement-variables_, each named by a valid statement in natural language (including mathematics and code), where a valid statement asserts a property of the world that is either true or false. The SAI Predictor $Q$ takes as input a query $(x, y)$ about variable $y$ in context $x$, and approximates a Bayesian posterior, $P_n(\cdot)=P_0(\cdot\mid D_n)$, over joint truth-assignments to these statement-variables by conditioning a prior $P_0$ on a contextualized dataset $D_n$ with $n$ examples. The central principle of the SAI is that $Q$ is intended to be epistemically honest, in the sense of approximating $P_n$. Here, we use “honest” to mean calibrated, fair, and non-strategic: $Q$’s outputs are fixed by the prior, model class, and data, entirely unaffected by a utility function of downstream effects of the answer. Hence, “honesty” allows for fallibility; $P_n$ can be mistaken under misspecification, insufficient data, or a bad prior, and $Q$’s approximation of $P_n$ is limited by compute.

The process for training $Q$ must be _consequence-invariant_, which is to say that training does not select candidate Predictors based on the downstream consequences of deploying their predictions. Instead, the training process aims to explain the fixed dataset $D_n$, much like good scientific theories aim to _explain_ the world as it actually is, rather than _changing_ the world to some more preferred state. Collectively, the end-to-end pipeline for training the SAI (from raw sources to deployed outputs) has the following three stages.

**Ingest (contextualization).** Raw sources are transformed into contextualized statement-variables, producing a dataset $D_n$ of statements about the world, each marked as either a direct observation or a claim made by an agent in context. Most ordinary sources are represented as communication acts, carrying metadata such as source and date. Factual syntax is reserved for direct measurements, executed computations, proven statements, and latent hypotheses. Thus, the contextualization engine enforces a syntactic distinction between _communication acts_ (“someone claimed $x$”, together with author/venue/timestamp source metadata) and _factual syntax_ (statements treated as direct observations, deductions, or hypotheses about the world considered as latent variables). As a result, we obtain better events for a Bayesian to condition on.

In this paper, contextualization is specified solely at the level of requirements (i.e., we do not provide a completed algorithm). Its role is to parse raw sources into statement-variables and to assign the communication-act versus factual-syntax distinction conservatively, defaulting most ordinary sources to communication-act records. Factual syntax can be used for hypotheses about properties of the world whose truth value is unknown and whose posterior probability is to be estimated by $Q$. Using factual syntax for a latent variable, therefore, implies only that its truth value is treated as a world-level variable to be inferred. Its intended meaning must still be anchored by the broader pattern of contextualized evidence, not by surface wording alone. Contextualization provides us with a contextualized dataset of $n$ observations $D_n$.

**Predict (system 1 / system 2).** In the second stage, a Predictor is trained on that dataset to assign probabilities to questions about the world. Given a query $(x,y)$, the Predictor returns $Q(y\mid x)$, its estimate of the Bayesian posterior $P_n(y\mid x)$. The Predictor can either return its estimate directly (“system 1”) or indirectly, by Monte-Carlo averaging over a small set of sampled latent statements proposed by an Explainer (“system 2”). We think of neural-network forward passes as analogous to Kahneman’s System 1 computation (Kahneman 2011): fast and intuitive, but potentially incoherent and brittle out of distribution (Ben-David et al. 2010; Quiñonero-Candela et al. 2008; Schölkopf et al. 2012). Meanwhile, we think of the Explainer as analogous to System 2 computation (i.e., slow, sequential, and verbalizable argument chains with mutual consistency common to good science). More specifically, the Explainer is a learned amortized proposal model that suggests latent statement-variables relevant to a given query, analogously to chains of thought (Wei et al. 2022; Zelikman et al. 2022; Hu et al. 2024) but composed of structured natural-language statements whose truth values are evaluated by $Q$ itself.

Hence, the SAI incorporates both ‘System 1’ and ‘System 2’ reasoning within the Predictor $Q$. The core neural computation supplies fast probabilistic intuitions, while the Explainer generates structured latent-variable arguments that $Q$ can evaluate and average over to improve generalization and coherence. To motivate the different roles of the Predictor and Explainer, consider a proof sketch as a latent variable: a good proof sketch may make it possible to obtain greater confidence in a conjecture $y$ compared to a direct neural net prediction of its probability of being correct given axioms $x$. Throughout this paper, $Q(y\mid x)$ denotes the full prediction output, whether produced by the neural-net Predictor alone or by Monte-Carlo averaging with the Explainer (see Def. [[#^def-explainer|45]] and Rem. [[#^rem-explainer-roles|46]]). When the SAI System returns a numerical answer, it can also return the proposed latent statements as an interpretability-supporting explanation trace, i.e., the proof sketch.

**Deploy (scaffold + guardrail).** To interface the Predictor with the outside world, a deployment layer decides what to release: it can answer, withhold the answer, or check the prediction against a guardrail before releasing it. We denote the deployed output as $\widetilde Q(y\mid x)$, with $\widetilde Q={\tt noprediction}$ indicating abstention. The SAI _Scaffold_ is code that orchestrates calls to $Q$ (and possibly additional tools) to produce deployed outputs. Although $Q$ is itself consequence-invariant, the Scaffold may use predicted consequences through explicit, audited criteria—primarily safety conditions verified by the Predictor used as an SAI Guardrail, which predicts the probability of specific harms caused by candidate actions (including the action of deploying an answer to a query). If the predicted excess log-odds of harm over abstention exceeds a threshold $\alpha$, the system outputs the ${\tt noprediction}$ symbol in place of the predicted probability, which can trigger a safe fallback policy. Throughout the safety analysis we work with the resulting _guardrailed Predictor_ $\gamma_Q$, asking “given that the Scaffold deploys $\gamma_Q$, how likely is a dangerous outcome under $P_n$?” (details in Sec. [[#^the-case-for-safety|5]]). Note that $P_n$ predicts what can be reasonably anticipated given all the available information, distinct from the unknown ground-truth data-generating distribution $P^*$, formally introduced in Def. [[#^def-data-generating-process|7]].

### Scope of the paper ^scope-of-the-paper

From the above, this paper develops formal safety arguments for a single component: the SAI Predictor $Q$. The paper develops two interacting arguments, the first of which is about accuracy and the other about honesty. We want the Predictor to answer questions about the world by approximating the Bayesian posterior, without thereby developing any tendency to imitate what humans would say, or to produce answers that users want to hear. The contextualization pipeline is meant to distinguish communication acts from other properties of the world (i.e., factual observations or hypotheses), so that any queries about future harms provided to the Predictor are considered solely as factual hypotheses. We also require the observations in $D_n$ not to be adversarially curated. These conditions are intended to remove important sources of agency that would arise from learning to imitate people or to optimize for user approval.

The second argument is about safety. Even if the objective is honest, the training process still samples from a very large space of possible Predictors. The question is whether it is likely to output a _dangerous_ Predictor. We define dangerous Predictors as those which, if deployed behind the Guardrail, would cause a harmful event $H$ with probability greater than a system-level threshold determined by an exogenous parameter $A_{\rm safe}$. The formal results in Sec. [[#^the-case-for-safety|5]] and Appendix [[#^per-band-sparsity-refinement-of|8]], including Thm. [[#^thm-qt-is-safe|87]], give one way to package this question as a probabilistic bound over the training-induced distribution of Predictors. We claim that, under the stated conditions, the probability of obtaining a dangerous Predictor is small.

This safety argument rests on two main intuitions: (1) the category of harm of interest, $H$, should not be something achievable by chance, making the set of dangerous Predictors tiny compared with all the predictors—the scope of our results thus applies to cases where danger requires many coordinated deviations from the target Bayesian Predictor; (2) the training process should not be systematically driving toward that tiny dangerous subset. This is made plausible by the consequence-invariance of the Predictor’s training process (see Reqs. [[#^req-no-explicit-consequence-signal|36]] and [[#^req-group-consequence-invariance|65]]), which requires that the objective and training process do not contain a direct signal that rewards Predictors for their downstream consequences after deployment (even with a preference for outcomes other than $H$). This rules out forms of reinforcement learning (RL) with a reward function inducing a preference for future states of the world. This means that any and all correlations between training-visible features and dangerousness enter only as accidental correlations. Without a consequence-dependent signal, training has no direct reason to search for the particular rare Predictors that would cause $H$.

Appendix [[#^per-band-sparsity-refinement-of|8]] develops a more technically detailed version of this argument. The space of possible query-response behaviors is very large, while a given notion of harm typically depends on a much smaller number of coordinated failures. This dimensional asymmetry is the reason we expect dangerous Predictors to be sparse, and why accidental training-time concentration on them should have to overcome a large combinatorial disadvantage (by accident).

##### What the paper establishes. ^what-the-paper-establishes

We set up a mathematical framework for analyzing probabilistic models over events describable in natural and formal languages, argue that we can train a model in this space accurately, and extend standard causal notions to formalize consequence invariance (Secs. [[#^forming-a-probabilistic-model|3]], [[#^the-case-for-accuracy|4]], and [[#^consequence-invariance|5.1]]). In the end, we prove a bound (Thm. [[#^thm-qt-is-safe|87]]) on the training-time mass of dangerous Predictors, and argue that _accuracy_ (calibrated, epistemically cautious predictions approximating the Bayesian posterior) and _safety_ (a uniformly small training-time mass on dangerous Predictors) arise as dual properties of the same training process. This is in contrast with classical concerns about AI capability potentially amplifying misalignment risks (Omohundro 2018; Amodei et al. 2016; Russell 2019; Zhuang and Hadfield-Menell 2020; Cohen et al. 2022). Because our training objective $J$ acts as a divergence from the honest posterior $P_n$ (Req. [[#^req-sai-bayesian-objective|34]]), Predictors can be grouped into “loss bands” by the value of the training objective, which measures the degree of deviation from the target distribution. The separate safety question is how many Predictors within any such band are dangerous under the initialization distribution, captured by a term $R_{\rm shell}$. Of course, a practically useful implementation must satisfy both sides of this picture: the safety argument below controls how rare dangerous Predictors are at each loss level (inside what we call a loss band), while competitive predictive performance depends on the separate approximation and semantics premises discussed in the accuracy argument of the paper.

##### What the paper does not establish. ^what-the-paper-does

The safety argument addresses only the Predictor’s own potential misalignment, specifically _implicit-goal misalignment_: Predictors whose deployment yields excess log-odds of harm above the safety threshold $A_{\rm safe}$. Harms arising from honest but uncoordinated mistakes due to lack of data or compute are out of scope, as is misuse by humans who intentionally deploy an honest SAI Predictor in harmful ways. Further, safety is provided relative to the Bayesian posterior $P_n$ rather than an omniscient ground truth $P^*$: because the deployment trajectory in Thm. [[#^thm-qt-is-safe|87]] is governed by the same $P_n$ that defines the training target (which is approached with more compute, not more data), the classical train-to-deployment generalization problem is turned into an optimization question: minimizing the training objective $J(Q)$, for $Q$ to match $P_n$. Whether $P_n$ itself adequately recognizes the relevant hazards—i.e., whether the finite dataset contains enough information for the posterior to assess them correctly—is a separate, credible question not settled by our theorems. A separate concern is that the prior $P_0$ or the data-collection process might themselves be engineered so that the posterior target $P_n$ steers deployment toward harmful outcomes. Several adjacent challenges are also outside scope: adversarial queries and prompt injection (although Sec. [[#^conclusions-and-future-work|6]] discusses structural defenses as future work), the safety of agentic scaffolds built on top of the SAI Predictor (Bengio et al. 2025b), the full eliciting-latent-knowledge challenge (only partially mitigated, Sec. [[#^the-challenge-of-eliciting|2.4.0.5]]), and finite-sample and finite-compute corrections to the asymptotic accuracy claims. The present guarantee is also stated for a single Predictor. Whether the safety properties compose under deployments in which multiple SAI Predictors interact is left to future work.

##### Key assumptions and their scope. ^key-assumptions-and-their

The full safety story has four ingredients: (a) the algebraic bound of Thm. [[#^thm-qt-is-safe|87]] (formally requiring only the no-large-enrichment condition, Req. [[#^req-bad-enrichment|84]]); (b) the small fraction $R_{\rm shell}$ of bad predictors within every loss band—a structural property of the Predictor initialization distribution $\mu$ and the honest objective $J$ (Req. [[#^req-sai-bayesian-objective|34]]); (c) consequence-invariance, which forbids explicit consequence-dependent training signals (Req. [[#^req-no-explicit-consequence-signal|36]]) such as reinforcement learning towards future outcomes caused by the SAI predictions, while restricting deployment-time Scaffold choices to explicit, audited criteria (Req. [[#^req-consequence-invariant-scaffold|80]]); and (d) a neutral target-construction process—the prior $P_0$ and dataset $D_n$ should function as purely epistemic inputs to the formation of the posterior.

## The Informal Argument and Objections ^the-informal-argument-and

The Scientist AI framework rests on several design choices that may appear to conflict with practical requirements or raise natural theoretical objections. This section, supplemented by Appendix [[#^additional-plausibility-arguments|9]], aims to informally argue for our framework and address the most important objections directly.

### Incentivizing Accuracy and Honesty ^incentivizing-accuracy-and-honesty

We claim that approximating the Bayesian posterior over contextualized statements incentivizes both accuracy and honesty. A detailed defense of this claim is given in Sec. [[#^forming-a-probabilistic-model|3]]; here, we sketch the four main components of that argument before considering objections to each of these claims.

**Component A1: Contextualization makes the learning problem well-posed**. The SAI is trained only on an epistemically contextualized dataset (Req. [[#^req-contextualization|25]]), which syntactically separates factual observations (verified measurements, proofs, program executions) from communication acts (“source S asserted claim X”, with metadata). This method of turning possibly false information (“claim X”) into factual one (“source S asserted X") yields a well-defined learning target, i.e., the Bayesian posterior over these contextualized variables. This prevents the Predictor from treating unverified or socially repeated claims as ground-truth facts.

**Component A2: Latent factual variables give training gradients that favor factual explanation over imitation.** Most real-world data, especially outside of formal science, are best interpreted as communication acts: we may observe that a claim was made, but we do not know if the claim itself is true. To avoid training a system that collapses into imitation of what humans say, the SAI design introduces latent variable-statements written in factual syntax, corresponding to the truth of underlying claims (Def. [[#^def-explainer|45]] and Req. [[#^req-latent-truth|48]]); for example, “$X$ is true” is forced to be one of the latent variables for the observed communication act “Author $A$ wrote $X$”, in addition to any other explanatory latent variable that the Explainer generates. This avoids optimizing the SAI to reproduce the distribution of human continuations, including text reflecting goals, strategy, deception, or self-preservation. It also lets one latent fact explain communication acts across sources through a shared causal mechanism, favoring causal explanation over imitation (Assumptions [[#^assume-factual-latent-dominance|52]] and [[#^assume-adequate-natural-language-semantics|53]]).

**Component A3: The Predictor’s probability assignments over uncertain statements converge toward the Bayesian posterior.** Even with unlimited informative data, most interesting statements are not perfectly deducible as True or False from the laws of mathematics. However, the Bayesian posterior probability of such latent statement-variables is a deterministic function of the data. However, the estimator $Q$ would generally not be certain about these values, and the entropy of $Q$ on such requests quantifies that uncertainty due to insufficient compute. With enough computation, $Q$ converges to $P_n$ on observable statements (Prop. [[#^prop-good-generalization-to-observables|58]]) and correctly estimates whether posterior probabilities lie inside or outside specified intervals for unobservable ones (Claim [[#^claim-good-generalization-to-unobservables|60]]).[^note-1]

**Component A4: Confident-but-miscalibrated predictions become vanishingly rare**. Epistemic honesty involves a tradeoff between false positives and false negatives; thus, we should be concerned about measures of epistemic fidelity beyond simply average calibration. One particularly concerning failure mode of interest for this paper is the problem of confident falsehoods. With enough computation, the probability of encountering a query where $Q$ is highly confident but $P_n$ is not vanishes (Prop. [[#^prop-epistemic-caution|56]]), yielding a formally accurate Predictor (Claim [[#^claim-accurate|61]]).

### Objections to the Accuracy Argument ^objections-to-the-accuracy

##### Contested Claims as Communication Acts \[Component A1\]. ^contested-claims-as-communication

One may think that the very procedure we use to make the learning problem well-defined assumes controversial philosophical commitments. Our contextualization procedure (so the argument may go) must assume either that contested empirical or normative claims have a determinate truth-value, or assume views which state that contested normative or empirical claims cannot be evaluated as ‘true’ or ‘false’.[^note-2]

_**Reply.**_ Our epistemic contextualization pipeline (Def. [[#^def-contextualization|22]]) allows us to represent contested claims as communication acts—statements of the form “agent A asserts $x$” that have determinate truth values regardless of the metaphysical status of $x$ itself. Consider a sentence like “Hello!” which is not a claim that is capable of being true or false. The contextualization pipeline translates such outputs into the form of communication acts (e.g., “Yoshua Bengio said ‘Hello!’ ”), allowing the model to learn from such outputs without being incentivized to emulate them. Other sentences may have the surface grammar of claims about the world (for instance, “Red is the best color") while they really express preferences, so we would translate them similarly (“Yoshua Bengio said ‘Red is the best color’ ”). However, this does not import controversial philosophical commitments, as everyone agrees that statements of the form “Agent $A$ said ‘torture is wrong’ ” themselves have determinate truth-values. To the extent that one does believe that contested statements have determinate truth-values, the Scientist AI (much like human scientists themselves) has no guarantee of convergence to the moral truth. Our SAI accuracy argument should thus be viewed as providing guarantees for such determinate claims only.

##### Generalizing Factual Syntax to Informal Domains \[Component A2\]. ^generalizing-factual-syntax-to

Even putting philosophical issues to one side, one may worry that the vast majority of training data—at least outside of mathematics and formal science—consists predominantly of communication acts. Hence, one may be concerned that factual syntax (i.e., the syntax through which the SAI is queried for honest predictions) may fail to generalize to domains where it was rarely encountered during training.

_**Reply.**_ The design addresses this through Req. [[#^req-latent-truth|48]]: the Explainer must include the factual truth variable “$x$ is true” as a latent explanation whenever a communication act asserts $x$. Even in domains with no directly observed factual statements, the Predictor thereby receives training gradients—via the latent variable model—that exercise the factual syntax and force it to assign a posterior probability to the underlying claim. $D_n$ will also contain scientific data proper (e.g., observations from medical studies, replicated experimental measurements, formally verified proofs, etc.), which provide a direct training signal for the factual mode. At the same time, communicated scientific theories are treated as communication acts; the SAI can treat them as useful latent hypotheses without being constrained to accept the current scientific consensus as ground truth, assigning posterior mass to competing theories in proportion to their consistency with directly observed evidence.

Our framework assumes that factual latents will tend to dominate the posterior because they provide compressive causal explanations (Schölkopf et al. 2021) which are unified across contexts (Assumption [[#^assume-factual-latent-dominance|52]]); the compositional structure of natural language further supports the generalization of this distinction to unseen domains (Assumption [[#^assume-adequate-natural-language-semantics|53]]). These claims are best viewed as empirical adequacy premises for (rather than proven consequences of) the present framework, insofar as they specify what must be validated for factual syntax to remain useful outside domains with direct factual supervision. A separate objection is that exact Bayesian inference is intractable and the available data are finite. We treat the formal accuracy claims in this paper as asymptotic in data and computation, with approximation error handled through conservative margins and abstention when uncertainty is large; see Appendix [[#^intractable-priors-and-finite|9.2]].

### The Safety Argument ^the-safety-argument

After the arguments for the accuracy of the Predictor, we turn to arguments for its safety. The SAI design explicitly separates _deployment-time decisions_ (which may explicitly veto or rank candidate outputs on safety grounds) from the Predictor’s _training process_ (which explicitly prohibits any feedback loop rewarding the Predictor for the downstream consequences of its deployed predictions).

Although it is difficult to be sure of _intention_, it has a statistically recognizable behavioral signature: reliably producing an outcome that unaimed behavior would reach only with vanishing probability. Such an outcome is a “needle in a haystack”: reliably finding it requires optimization guided by a signal of proximity, and the SAI design withholds such a signal from Predictor training. The safety argument has the following three components.

**Component S1: Coordinated action over time is required to pursue difficult and harmful goals.** We consider harms $H$ that are unlikely to result from a single mistaken prediction from the Predictor, that either require many Guardrail deviations of $Q$ from $P_n$ or that those deviations are very large. To produce such highly dangerous outputs, the Predictor must issue many false-negative safety judgments—each consistent with the others and with whatever cover story explains them in deployment—sustained across many queries or many users. Using the formalism of this paper, the pursuit of a harmful goal requires that the guardrailed Predictor’s harm estimate falls below a threshold $\alpha$ on each set of safety-critical queries that together enable $H$.

**Component S2: Dangerous Predictors are rare at every level of loss.** Under the unstructured initialization distribution over Predictors $\mu$, only a small fraction of Predictors produce outputs that keep such a harmful plan viable; it would be highly surprising if a randomly initialized Predictor could achieve a complex, dangerous goal. The stronger claim we need is that this remains true after conditioning on any fixed loss level. Letting $R_{\rm shell}(H,A_{\rm safe})$ denote the largest fraction of dangerous Predictors found inside any loss band under $\mu$, we claim $R_{\rm shell}$ is structurally small.

**Component S3: Training does not concentrate probability mass on the dangerous subset.** Instead of just thinking about the randomness in the actions of a given Predictor, we consider the distribution of Predictors resulting from the training process $\nu$, and how likely they are to cause $H$. Even if dangerous Predictors are initially rare within each loss band, we still need to control whether training concentrates probability mass on that subset. Because $\nu$ is consequence-invariant, it carries no direct consequence-dependent signal selecting the dangerous subset. The training process $\nu$ can still reweight Predictors through ordinary optimizer-visible properties based on the training objective; the safety question is whether those properties accidentally localize dangerous Predictors within a loss band. Hence, the argument requires that such accidental enrichment remain bounded. This yields the paper’s central safety result (Thm. [[#^thm-qt-is-safe|87]]): writing $\nu_t$ for the marginal of the training process $\nu$ at step $t$, then for any harmful event $H$ and safety threshold $A_{\rm safe}$ at which Req. [[#^req-bad-enrichment|84]] holds, and uniformly in training step $t$, the probability of obtaining a dangerous Predictor is bounded by: 

$$
\nu_t\{Q : Q\textnormal{ is dangerous}\}\le C_{\rm bad}(H, A_{\rm safe})\,R_{\rm shell}(H,A_{\rm safe}),
$$

 where $R_{\rm shell}(H,A_{\rm safe})$ is the largest fraction of dangerous Predictors found inside any loss band under $\mu$, and $C_{\rm bad}(H,A_{\rm safe})$ denotes how much the chosen noisy training process can increase this fraction within a band. If the degree to which the noisy training process can increase this fraction is small (i.e., if $C_{\rm bad}$ is small), then the probability of obtaining a dangerous Predictor is small. We argue that $C_{\rm bad}$ is likely to be small (Remark [[#^rem-bad-funneling|85]]) because of consequence-invariance, and thus our bound delivers an optimistic safety result on the probability of obtaining a dangerous Predictor.

### Objections to the Safety Argument ^objections-to-the-safety

##### Consequence-invariance and the absence of implicit agency \[Component S3\]. ^consequence-invariance-and-the-absence

A natural worry is that a sufficiently capable system trained to minimize prediction error might learn to influence the world it is meant to model. If post-deployment outcomes are used as a training signal, selecting checkpoints or outputs based on downstream error would create optimization pressure to steer the world. More broadly, one might think that any sufficiently capable system with a persistent goal tends to develop instrumental subgoals such as self-preservation and resource acquisition (Omohundro 2018; Russell 2019)—the prediction-accuracy goal is no exception.

**Reply.** The SAI design requires the Predictor’s training process $\nu$ to satisfy the formal core of consequence-invariant training (Req. [[#^req-no-explicit-consequence-signal|36]]), which rules out explicit algorithmic signals that reward, penalize, rank, or select candidate Predictors because of the realized or desired downstream consequences of deploying them. Because future outcomes may enter $J$ as variables to be predicted, this process still allows the Predictor to make predictions about the consequences of given actions. By design, consequence-invariance thus rules out any reinforcement-learning-style loop in which the Predictor is selected because it would lead to preferred real-world effects, as well as subtler forms of feedback, such as choosing among checkpoints based on downstream error measured after deployment.

Concretely, post-deployment consequences may be queried via interventional predictives (Ortega et al. 2021). These consequences, however, are not fed back into the current training run as an on-policy signal: they are not appended to $D_n$, nor does any training signal select the current Predictor for the downstream effects of its own deployment. If such consequences are later observed, they may be recorded only as ordinary contextualized observations in a future enlarged dataset $D_{n'} \supseteq D_n$ for a subsequent training run. Likewise, checkpoint selection depends only on fixed-data metrics derived from $D_n$. At deployment time, the Scaffold may still reason about downstream consequences, but only through explicit, audited criteria—in this paper, safety results primarily through the Guardrail and, when appropriate, safer tie-breaking among candidate performative fixed points, all under Req. [[#^req-consequence-invariant-scaffold|80]]. The _statelessness_ of $Q$ (Def. [[#^def-query-family-and-predictor|19]]) provides a further mitigation against strategies that require a persistent state across queries. Predicting downstream consequences does not require optimizing the Predictor for them: $Q$ can model agents and accurately forecast the effects of its own deployed outputs while still producing an epistemically honest posterior estimate (formalized in Sec. [[#^the-case-for-accuracy|4]]).

##### The exponential sparsity of deceptive predictors \[Component S2\]. ^the-exponential-sparsity-of

Even under consequence-invariant training, one might ask whether the randomness of training could accidentally produce a dangerous Predictor, or whether an emergent inner optimizer (Hubinger et al. 2019) could generalize in goal-directed ways unrewarded by the outer objective.

**Reply.** At the exact loss minimum, Req. [[#^req-sai-bayesian-objective|34]] gives $Q=P_n$, and Prop. [[#^prop-pn-consequence-invariant|64]] shows that this honest target is consequence-invariant. Under the “guardrail-adequacy” condition, $a_H(P_n)\le A_{\rm safe}$, its guarded deployment is safe. The non-asymptotic question is whether training can pass through dangerous positive-loss Predictors before reaching that endpoint.

The answer proposed here relies on the levels of loss. Regardless of whether the offending outputs arise from an inner optimizer, an ordinary approximation error, or a posterior explaining the data through a hidden strategic actor, sustaining $H$ requires a structured pattern of Guardrail-relevant deviations. Within a fixed loss level, or band, this pattern is argued to be geometrically sparse. Any remaining enrichment must therefore arise through accidental correlation with training-visible features, quantified by $C_{\rm bad}$ and refined by $K_B(t)$ in Appendix [[#^per-band-sparsity-refinement-of|8]]. Attempts to manipulate the collection of future data are unrewarded by the current training signal because the current run trains on the fixed dataset $D_n$.

##### _Objections to the modeling assumptions._ ^objections-to-the-modeling

The following two objections concern the modeling setup shared by the accuracy and safety arguments, i.e., how deployed predictions and latent knowledge are represented.

##### Performative prediction. ^performative-prediction

If the deployed predictions of the SAI system affect the variables to be predicted by $Q$, doesn’t the design risk rendering those deployed predictions incompatible with their effects?

_**Reply.**_ The SAI treats deployed predictions $\widetilde{Q}$ as _intervened variables_ (see Req. [[#^req-predictions-as-interventions|28]]). This means that the Predictor can model the consequences of deploying a prediction via a $\mathrm{do}(\widetilde{Q}=\cdot)$ intervention (Ortega et al. 2021) without those consequences flowing back as a training signal, thereby yielding a unique, well-defined Bayesian posterior without any fixed-point requirement on the posterior target itself. In cases (such as, e.g., self-fulfilling prophecies) where multiple performatively consistent fixed points exist (Perdomo et al. 2020), the Scaffold selects among them using explicit, audited criteria (Req. [[#^req-consequence-invariant-scaffold|80]]). If none exists, then the Scaffold can select a prediction which approximately minimizes the residual from the performative prediction constraint (Def. [[#^def-performative-prediction-constraint|41]]). Performativity is therefore a reason to be careful about how $\widetilde{Q}$ is formed from $Q$—but it is not, by itself, a reason for the Predictor to seek implicit unaudited goals.

##### The Challenge of Eliciting Latent Knowledge \[Component S3\]. ^the-challenge-of-eliciting

The _eliciting latent knowledge_ (ELK) challenge (Christiano et al. 2021) has been raised as a fundamental obstacle to any safety case grounded in AI honesty: if a sufficiently capable model’s outputs need not reflect its internal beliefs, then guarantees about output honesty provide no assurance about what the model “actually knows” or intends. The ELK challenge asks how to ensure that a model’s outputs faithfully reflect its internal beliefs, which can be difficult when the learner can only make interpretable predictions over the variables in the data.

_**Reply.**_ The SAI design partially mitigates one important aspect of this challenge by requiring latent-variable probabilistic reasoning to be expressed through explicit natural-language statements. Thanks to the compositional nature of language and the fact that the SAI uses the same language to name observed and latent variables, it can generalize to the semantics of queries that have never been seen in the training set (see Prop. [[#^prop-good-generalization-to-observables|58]]). It is thus possible to query the SAI about its latent variables using factual syntax (communication act syntax would only tell us what a human would say), capturing the part of its internal beliefs that can be verbalized. The Explainer (Def. [[#^def-explainer|45]]) must articulate which latent variables it relies on; the conditional probability of the truth values of those latent variables is produced by $Q$, which acts as a verifier for each statement in the argument generated by the Explainer, and these probabilities feed directly into the final prediction. The latent statements generate gradients back into $Q$ during training (Req. [[#^req-latent-truth|48]]), so the expressed reasoning must actually contribute to predictive accuracy. For any latent knowledge that the model can verbalize in natural language, an explicitly agentic explanation should appear in sampled Explainer traces and thus be auditable; conversely, a merely plausible-looking rationale that does not actually support its conclusion must violate the probabilistic consistency constraints among the stated latent variables’ probabilities, and is penalized by $J$. Unlike a System 1 scalar output, a System 2 false negative is a composed, gradient-bearing chain of $Q$\-evaluated probabilities, so it cannot be plausible at each step and yet harmful in its conclusion for free.

However, we acknowledge that ELK is not fully resolved. Non-verbal internal representations that cannot surface through the Explainer could, in principle, contain beliefs not expressible as SAI statements. The remaining concern is therefore an implementation-level inner optimizer in $Q$’s weights that produces generally coherent explanations while steering safety-critical outputs. To be dangerous, such an optimizer must either surface agentic structure in auditable explanations, or sustain a coherent pattern of predictive deviations (relevant to Guardrail decisions); the latter is exactly the high-loss, coordinated behavior targeted by Theorems [[#^thm-qt-is-safe|87]] and [[#^thm-geom-ci-bound|102]]. Thus, the safety guarantees we provide do not require ELK to be solved in full.

##### Safety under intractable posteriors and finite data. ^safety-under-intractable-posteriors

Exact Bayesian inference is typically intractable, and the data are finite, shifting, and sometimes adversarially curated. Why should we trust an approximate-posterior system, and how are safety-relevant errors controlled?

_**Reply.**_ To the extent that one is concerned about the specifically safety-focused version of this worry (see Sec. [[#^intractable-priors-and-finite|9.2]] for our reply to the accuracy-focused objection), one must be concerned that the SAI Predictor training procedure creates selection pressure toward downstream outcomes. Here, worries about approximation limitations may motivate conservatism, but they do not, by themselves, reintroduce a reward signal for steering the world. Our key safety result (Thm. [[#^thm-qt-is-safe|87]]) requires only that: (i) Predictors capable of sustaining harmful trajectories incur the corresponding loss threshold, and (ii) that stochastic training does not substantially enrich such dangerous Predictors within the loss bands it visits. As such, approximation errors then appear as elevated loss or uncertainty. While safety-critical deployment may still require conservative margins and abstention when approximation error is large, the constraints of our setup seem to preempt the emergence of hidden objectives aiming to steer towards downstream outcomes.

## Forming a Probabilistic Model of the World ^forming-a-probabilistic-model

Our approach is to approximate an extremely expressive Bayesian posterior. But over what, exactly? Bayesian methods rely heavily on the foundational modeling assumptions, so we take care in this section to set up the underlying probability space properly—even though, in practice, the predictor $Q$ will never exactly represent a consistent probability distribution over that space. We aim to benefit from the expressivity of natural and artificial languages. However, the fact that the predictor is itself a part of the world poses certain modeling difficulties (Demski and Garrabrant 2020; Meulemans et al. 2025), which we must take care to handle deftly as well.

##### Formal versus informal results in Sections [[#^forming-a-probabilistic-model|3]], [[#^the-case-for-accuracy|4]], and [[#^the-case-for-safety|5]]. ^formal-versus-informal-results

While our underlying model in the next few subsections has been fully defined, the remainder of the paper contains a mix of formal and informal content. The formal results—along with those Definitions and Requirements that are stated in fully formal terms—follow deductively from the stated definitions and requirements. The informal content rests on empirical considerations and conceptual insights that we cannot yet fully formalize. We reserve the labels Theorem, Proposition, Proof, and Corollary for the former, and Claim, Argument, and Assumption for the latter.

### Modeling tools: causal models, statements, datasets, and targets ^modeling-tools-causal-models

We begin with a (countable) collection of statements in natural language, mathematics, or code—each of which describes a determinate property of the world. We call this set of basic semantically meaningful strings _statements_, denoting the set of all such statements by $\mathcal{S}$. For each statement $s \in \mathcal{S}$, we suppose there is a corresponding Boolean variable $v_s \in \{0, 1\}$ called a statement-variable, where $v_s = 1$ is to be interpreted as the assertion expressed by $s$ being true. Not all strings should be thought of as valid statements.

**Example 1**. “It rains in Montreal on January 1st, 2030” could be an example of a valid statement, i.e., it is the name of a variable. At the time of this writing, its truth value is unknown. Examples of invalid statements include “Hello!” and “Red is the best color”. An invalid statement can often be turned into a valid one by adding context, e.g., “Yoshua uttered Hello!” and “Yoshua prefers the color red over others”.

The raw training data can contain invalid statements, but they are transformed into valid ones by the automated epistemic contextualization process (formalized in Def. [[#^def-contextualization|22]]). In practice, most statements will be recorded as communication acts (attributed to a speaker in a specific context), while some scientific statements may be assigned a factual meaning by the designers of the contextualization pipeline.

The variables of our system that we most care about are those indexed by these statements, but we cannot stop there: we need explicit variables ($\widetilde Q$) encoding the effect of deploying a predictor. This creates a knot: anything describable in terms of any variables is a potential query and hence leads to a new deployment variable that must also be part of the basic variables of our causal model. So we turn to the classical trick for handling cyclic definitions: inductively defining all syntactic objects at once. Bear with us a moment.

**Definition 2** (Statements $\mathcal S$, language $\mathcal L$). _Let $\mathcal S_0$ be a countable set of valid statements, including communication acts. Fix a bit precision $B$ for the predictor. For $k = 1, 2, \ldots$, recursively define_ ^def-statements-language

$$
\begin{align*}
        \mathcal S_{k+1} &:= \mathcal S_k \sqcup \{ \textnormal{\text{“}}~\widetilde Q_n(y\mid x).b~\textnormal{''} : x,y \in \mathcal L_k, ~n \in \mathbb N,~b \le B \};
                \\
        \mathcal L_{k+1} &:= \textrm{the Boolean closure of } \mathcal S_k  \textrm{ under \(\lnot, \land\) }
\end{align*}
$$

_Then, define $\mathcal S := \bigcup_{k \ge 0} \mathcal S_k$ and $\mathcal L := \bigcup_{k \ge 0} \mathcal L_k$._

Intuitively, $\mathcal L$ is the language (that of a Boolean algebra for queries) over the truth values of the statement-variables indexed by $\mathcal S$. The new statements added to each level of $\mathcal S$ comprise, for each pair $(x,y) \in \mathcal L \times \mathcal L$ and $n \in \mathbb N$, the precision-$B$ binary representation of a rational number $\widetilde Q_n(y\mid x) \in [0,1]$. (In this notation, $q.b$ indicates the $b$\-th bit in the binary representation of $q$.) These numbers will later be interpreted as predictor deployments (Sec. [[#^deployment-guardrails-and-scaffolds|3.3]]) and are central to making a predictor insensitive to the consequences of deployment—but we defer this. In the end, $\mathcal S$ and $\mathcal L$ remain countable sets of statements, their elements representable as strings of tokens.

**Definition 3** (Variables $\cal V$). _Let $\mathcal V := \{ v_s : s \in \mathcal S \}$ be the endogenous (Boolean) variables of the model._

In addition to the variables $\cal V$, we also need to model the data-collection process, so that we can properly condition on the dataset. We model these variables as distinct and causally exogenous.

**Definition 4** (Dataset $D_n$, selection variables $\mathcal X$). _An observation is a statement-variable observed to take value $1$. The dataset $D_n = (x_1, \ldots, x_n)$ is a sequence of such observations. Let $X_i$ be a new kind of variable (taking values in $\mathcal S$), indicating the identity of the statement selected for the $i$\-th observation, so that $v_{X_i}=1$ is the observed event. We write $\mathcal X:=\{X_i\}_{i=1}^\infty$ for the indexed collection of selection variables._ ^def-dataset

_Remark 5_. Although $D_n$ is formally a sequence $(x_1, \ldots, x_n)$ of statements, we freely identify it with the event $\bigwedge_{i=1}^n(X_i = x_i \land v_{X_i}=1)$ when it appears as a conditioning argument in a probability expression. This is equivalent to conditioning on the event $X_{1:n} = D_n$, under the assumption that only true things are observed (i.e., $\exists i.~X_i = x \implies v_x = 1$), as is ensured by contextualization (Def. [[#^def-contextualization|22]]).

Our framework also requires a formalization of causality. For simplicity, we build on finite structural causal models (SCMs) (Pearl 2009). [^note-formalism-scope] A causal model $W$, intuitively, assigns to each variable $v$ an equation $v = f_v(\ldots)$ that determines the value of $v$ as a function of other variables and independent randomness. Since there are so many variables in our setting, $W$ cannot be an explicit list of such equations. Therefore, think of $W$ as a computer program that takes $v$ as input and produces the function $f_v$.

**Definition 6** (Causal Models $\cal W$). _A causal model $W$ (over $\cal V$) associates to each $v \in \cal V$ a finite set ${\rm pa}_v \subset \mathcal V$ of causal parents for $v$, a finite set of noise variables $\eta_v$ encoding independent randomness, and a causal mechanism $f_v  : \{0,1\}^{|{\rm pa}_v| + |\eta_v| } \to \{0,1\}$, which is a function that encodes the equation $v=f_v({\rm pa}_v,\eta_v)$. We identify the causal model $W$ with a new binary variable, where $W=1$ implies that all equations in $W$ (regarded as events that constrain the joint values of $\cal V$) must hold. We consider only causal models with the property that $\widetilde Q_n(y \mid x)$ cannot be causal ancestors of $v_{X_i}$ for $i \leqslant n$. Let $\cal W$ be the set of all such causal model variables, and let $\cal N$ denote the set of all noise variables $\eta_v$, both disjoint from $\cal V$._

In practice, we further restrict $\cal W$ to be consistent with any temporal ordering of variables; for example, the parents of a variable cannot have a later contextualized timestep than the child. We make two further notes.

1.  We have identified each $W \in \mathcal{W}$ by a syntactic description, but also view it as encoding structural-equation programs over the variables $\cal V$. Each $W$ is therefore simultaneously a program (specifying mechanisms), a generalized statement (asserting that the equations generated by the program $W$ hold), and a new Boolean variable taking value 1 only when the assertion holds.
    
2.  The same causal model can be implemented by many different programs; multiple distinct $W$s can simultaneously take the value $1$, such as those that are syntactically different but semantically equivalent. Program equivalence can be subtle, though, and hence must be learned (to be formalized in Def. [[#^def-correct-semantics|47]]). Furthermore, since we are not handling logical constraints natively, there will be multiple distinct SCMs in our sense that cannot be distinguished (e.g., mass$_{\rm kg}$ $\to$ mass$_{\rm lbs}$ vs. mass$_{\rm lbs}$ $\to$ mass$_{\rm kg}$).
    

**Definition 7** (True probability space). _Define $\mathcal V^+:=\mathcal V\cup\mathcal X\cup\mathcal N\cup\mathcal W$ to be the set of all relevant variables to be modeled. The sample space $\Omega$ consists of all joint assignments to $\mathcal V^+$ with the property that, whenever $W=1$ for some $W \in \mathcal W$, then all equations of the causal model $W$ (interpreted as constraints on $\mathcal V$) must hold. For a joint setting $\omega \in \Omega$ of all variables and a language element $x \in \mathcal L$, write $\omega \models x$ if $x$ is true in world $\omega$. Let $P^*$ be the unknown “true” probability measure over $\Omega$. We further assume that the marginal $P^*(\mathcal N)$ on noise variables is uniform._ ^def-data-generating-process

Thus $P^*$ governs both _which variables_ are collected in the dataset (i.e., the values of $\mathcal X$) and _what values of these variables_ are observed (i.e., the corresponding values $v_X$ which in this case are equal to one). It is possible to extend the algebra of queriable events $\mathcal L$ to $\mathcal L^+$ over all of $\mathcal V^+$, by pushing all these concepts into the inductive loop of Def. [[#^def-statements-language|2]].

We are trying to model a Bayesian posterior over our (enormous) sample space $\Omega$. This amounts to selecting a prior ($P_0$, defined next) and conditioning on our observations (the dataset $D_n$).

**Definition 8** (Prior and posterior). _Denote by $P_0$ a prior over $\Omega$. We require that $P_0(W=1)>0$ for every $W\in\mathcal W$, and that $\mathcal N$ be mutually independent in $P_0$. Define the posterior $P_n$ over $\Omega$ as $P_n(\cdot)=P_0(\cdot \mid D_n)$._ ^def-bayes-posterior

_Remark 9_ (Neutrality of the prior and Bayesian update). The prior $P_0$ is intended to be broad and epistemically neutral—for example, a description-length-biased prior over causal models. We posit that Bayesian updating from $P_0$ to $P_n=P_0(\cdot\mid D_n)$, when unique, is then an example of a consequence-blind evidence-reweighting step: hypotheses are reweighted by how well they explain the fixed dataset $D_n$, and should not depend on whether or not deploying the resulting Predictor would cause some desired or harmful outcome. We posit that under a broad prior over causal models, the mechanisms capable of supporting a difficult harmful trajectory should occupy a small part of model space, as most mechanisms do not encode the coordinated structure needed for such a trajectory. This intuition motivates the sparsity assumptions used later, and its connection to our eventual safety argument is discussed in Appendix [[#^neutrality-of-the-prior|9.3]]; it is supported by Prop. [[#^prop-pn-consequence-invariant|64]], which shows the consequence-invariance of $P_n$. ^remark-prior-neutrality

**Definition 10** (Correct causal models). _A causal model $W$ is **correct** if conditioning the prior on it yields $P^*$—that is, if $P_0(\cdot\mid W) = P^*(\,\cdot\,)$. Let $\mathcal W^*\subseteq\mathcal W$ denote the set of correct causal models._

**Requirement 11** (Realizable model class). _The class $\mathcal W^*$ of correct models is non-empty._ ^req-rich-enough-model-class

_Remark 12_. Req. [[#^req-rich-enough-model-class|11]] is supported by the generality of the language (natural language, mathematics, and computer code of unrestricted length) used to express causal models, though with a prior that exponentially prefers shorter description length models). Relying on the Church–Turing thesis (Turing 1936), every known scientific model would be expressible in this way.[^note-competing-theories]

The set of variables that can, in principle, have a posterior probability of zero or one will be of particular importance for formalizing our central assumption about “neutrality” of the data-collection process.

**Definition 13** (Deducibility). _A variable $v\in\mathcal V^+$ is **deducible** from an event $E$ (e.g., a value assignment to other variables) if $P_0(E)>0$ and $P_0(v{=}1\mid E)\in\{0,1\}.$_

Deducibility can be computationally expensive to establish; accordingly, $Q$ is not assumed to identify deducible variables, and inherits $P_n$’s commitments on them only as far as approximation and compute allow. We will later see that this is the gap controlled by epistemic caution (Prop. [[#^prop-epistemic-caution|56]]).

**Definition 14** (Observable variables). _Let $\mathcal O\subset\mathcal V^+$ be the set of **potentially observable variables**. We require that $\mathcal O$ contain all statement-variables in $\mathcal V$ that may be directly observed, all selection variables $X_i\in\mathcal X$ that specify which statement-variable was observed, and all variables whose values are, in principle, deducible from the values of directly observed variables. We call variables in $\mathcal V^+\setminus\mathcal O$ **unobservable**. We write $D_\infty$ for the limiting directly observed dataset and $P_\infty$ for $P_0(y\mid x,D_\infty)$. Both $D_\infty$ and $P_\infty$ are random variables over $\Omega$ whose distribution is governed by $P^*$._ ^def-observable

_Remark 15_. The “directly observed” clause of Def. [[#^def-observable|14]] formalizes as $P^*(\exists n.~X_n=s)>0$. Note that $D_\infty$ will not include all of $\mathcal O$, because some variables (e.g., those with a specific time stamp) might never be observed despite being observable in principle. $D_\infty$ will also not contain all deducible consequences because of limited compute. Unobservable statements include things like the intentions, thoughts, or beliefs of agents; the best we can generally do about them is infer their probability. Within $\mathcal O$, we are particularly interested in epistemic/probabilistic consequences, such as statements of the form $P_n(y\mid x)<b$, since they allow us to form confidence intervals over queries.

With these definitions in place, we can now state the key technical requirement we need in order to ensure that the data-collection process reveals enough about the world in the limit: intuitively the dataset $D_n$ must provide more and more information about the true causal structure in $P^*$ as $n$ increases.

**Requirement 16** (Informative data). _The dataset is informative about $P^*$. Formally, the mutual information $I_{P_0}(D_n;\mathcal W)$ under the prior $P_0$ (of Def. [[#^def-bayes-posterior|8]]) converges to $I_{P_0}(\mathcal O;\mathcal W)$ as $n\to\infty$._ ^req-informative-data

Beyond informativeness, it is important that the data not be adversarially constructed to cause a particular downstream effect with the deployment of the Bayesian posterior. We believe it would be difficult to select data this way, particularly in the presence of the contextualization (Def. [[#^def-contextualization|22]]), and very unlikely to happen by accident. Excluding such data-selection attacks lies outside the scope of the present analysis.

### The Predictor, and Requirements Imposed During Training ^the-predictor-and-requirements

The predictor $Q$, whose definition and training are the focus of this section, is trained towards the Bayesian posterior on a fixed dataset $D_n$ (and not to resolve uncertainty any further than that). From this point forward, we therefore fix $D_n$, and hence the integer $n$, the values of the selection variables $X_1, \ldots, X_n$, and their realized values $x_1, \ldots, x_n$. We also drop the subscript on $\widetilde Q:=\widetilde{Q}_n$, which we now begin to interpret.

**Definition 17** (Past and future variables). _Let $\mathcal{V}_{\rm past}\subset\mathcal{V}^+$ be a subset of variables containing $\mathcal{W}$, the statements in $D_n$, $X_1, \ldots, X_n$, and every variable that can be a causal ancestor of some statement in $D_n$ under some causal model $W\in\mathcal W$—but not $\widetilde Q$. Define the future variables by ${\cal V}_{\rm future}:={\cal V}^+\setminus{\cal V}_{\rm past}.$ The variables of $\widetilde Q(y\mid x)$ must therefore be in the future._

_Remark 18_. Some variables can be constant (not have variants that differ across time), in which case they should be in $\cal V_{\rm past}$ if they can cause elements of $D_n$.

**Definition 19** (Query family and Predictors). _Let $\mathtt{Q}\subseteq\mathcal L\times\mathcal L$ be a fixed countable family of queries of bounded token length. Let $\mathcal Q:=(0,1)^{\mathtt{Q}}$ and $\overline{\mathcal Q}:=[0,1]^{\mathtt{Q}}$. A (probabilistic) **Predictor** $Q\in\mathcal Q$ is a (stateless[^note-5]) function that assigns to each $(x,y)\in\mathtt{Q}$ a number $Q(y\mid x)\in(0,1)$, represented in binary to precision $B$. The Bayesian posterior $P_n$ itself, viewed as the mapping $(x,y)\mapsto P_n(y\mid x)$, is an element of $\overline{\mathcal Q}$._ ^def-query-family-and-predictor

In practice, $\mathtt{Q}$ will consist of $(x,y)$ pairs with $y$ short, and $x$ in conjunctive normal form. The posterior target $P_n(y\mid x)$ may be $0$ or $1$ for deterministic observations, code outputs, proven theorems, contradictions, or other deductive consequences of the contextualized data. For training purposes, it is often convenient to restrict finite Predictor outputs to $(0,1)$, working with logits, so that losses and gradients remain well-behaved. This is a training convention only: exact posterior targets are represented in the closure $\overline{\mathcal Q}=[0,1]^{\mathtt{Q}}$, and trainable Predictors may approach them as limits.

_Remark 20_. We write $Q(y\mid x)$ for the scalar prediction at $(x,y)$, and use the symbol $Q$ alone in expressions like $J(Q)$, for the Predictor as a function, allowing context to disambiguate. In particular, throughout the paper, we use the symbol $P_n$ for both the joint distribution $P_n \in \Delta\Omega$ and its evaluation on the bounded query family, $P_n : \mathtt{Q}\to [0,1]$, that assigns $(x,y)\in\mathtt{Q}$ to $P_n(y=1 \mid x=1)$.

The rest of this subsection imposes requirements on the process of training $Q$, which we now define.

**Definition 21** (Training process). _The **training process** is a distribution $\nu$ over training trajectories indexed by $t$, with randomness due, for example, to initialization, minibatch sampling, and SGD noise. We write $\nu_t$ for its marginal over Predictors at step $t$._

#### Contextualization ^contextualization

The process of transforming syntactic objects into semantically valid strings (i.e., statements) is part of the process of epistemic contextualization. The Predictor is then trained on this epistemically contextualized dataset; it takes as input queries, and outputs probability distributions for valid queries. We now introduce a series of assumptions and requirements for training the SAI Predictor.

**Definition 22** (Contextualized dataset). _Let a record be an observation in the sense of Def. [[#^def-dataset|4]]. A dataset is **epistemically contextualized** (or just **contextualized**) when its syntax marks it as exactly one of two kinds. A factual observation records a directly measured value, the output of an executed computation, or a proven statement. In contrast, a communication act records that a named agent uttered something, possibly identified as a stated claim about a property of the world, and it carries metadata identifying the source, venue, and timestamp. A dataset is contextualized when every record in it is contextualized; we call the process of transforming data sources into such records **epistemic contextualization**._ ^def-contextualization

_Remark 23_. Communication-act records assert that the act occurred (with the stated metadata), not that the communicated content is true. This syntactic separation is used to prevent uncontextualized statements from being treated as ground-truth facts. Contextualization defaults to communication acts unless the record is a direct measurement or a proven statement. We illustrate this with an example and then impose a necessary requirement of our pipeline.

**Example 24** (Epistemic contextualization). Verified facts use factual syntax: e.g., “The Earth orbits the Sun,” or the confirmed output of a computation. By contrast, a source claim is recorded as a communication act: “The Flat Earth Society FAQ stated in 2025: The Earth is constantly accelerating upward at $9.8\,\mathrm{m/s}^2$”.[^cite-6] The record asserts only that the claim was made; the underlying Flat Earth assertion is treated as a latent hypothesis, plausibly assigned negligible posterior probability because it is incoherent with the bulk of the data. Author metadata (venue, timestamp, identity) are included in communication-act records, enabling the SAI to weight sources by their reliability.

**Requirement 25**. _The SAI Predictor $Q$ is only trained on contextualized data._ ^req-contextualization

_Remark 26_. A factual observation is a directly observed statement-variable, and a communication act is the directly observed event that an agent made an utterance, so both kinds of record name directly observed statement-variables, and thus get placed in $\mathcal{O}$ (see Def. [[#^def-contextualization|22]] and Def. [[#^def-observable|14]]), with the selection variables $X_i \in \mathcal{X}$ lying in $\mathcal{O}$ for the same reason. Hence, every contextualized record is observable, and the membership $x_i \in \mathcal{O}$ holds by Def. [[#^def-dataset|4]] and Def. [[#^def-contextualization|22]].

_Remark 27_. Epistemic contextualization may introduce rare errors (e.g., mis-specified observations). In safety-critical use, such uncertainty should be handled conservatively by increasing abstention/uncertainty, and by using data-quality checks to flag suspicious observations. Our safety guarantees rely on the SAI Predictor being trained on a contextualized dataset of sufficient size to achieve the required semantic generalization (see our later Assumption [[#^assume-adequate-natural-language-semantics|53]]). When the semantic anchoring of a factual latent is weak, the appropriate behavior is similarly calibrated uncertainty or abstention. Hence, the SAI Predictor is not initialized from a pre-trained LLM. However, experiments in which an SAI Predictor is initialized from a pre-trained LLM and then fine-tuned with the SAI objective and contextualized data could serve as evidence of the comparative safety and reasoning accuracy advantages of the SAI framework.

#### Modeling the Consequences of Deployment ^modeling-the-consequences-of

To motivate the next requirement, consider that conditioning on $D_n$ updates beliefs (the posterior $P_n$ and its estimator $Q$) but does not change the world. Deploying those predictions, however, as modeled by variable $\widetilde{Q}(y\mid x)$ for a query $(x,y)$ can affect future events, as it is an action that is best modeled causally. Recall that we regard the variable(s) $\widetilde{Q}_n(y\mid x)$ as the (binary representation of the) deployed predictor’s output probability. Thus, the intervention $\mathrm{do}(\widetilde{Q}(y\mid x)=q)$ sets the predictor’s output to $q$ in our model.

**Requirement 28** (Predictions as interventions). _The predictor must be trained to correctly answer interventional queries of the form $Q(y\mid x,~{\rm do}(\widetilde{Q}(a\mid b)=q))$. Furthermore, when deployed predictions $\widetilde{Q}$ are variables in roll-outs involving downstream effects and used to update $Q$ itself (updating parameters at training time or predictions themselves at run-time) no signal flows back through $\widetilde{Q}$ into $Q$._ ^req-predictions-as-interventions

_Remark 29_ (Implementing `do()`\-syntax in practice). Req. [[#^req-predictions-as-interventions|28]] can be implemented by exposing the Predictor during training to interventional statements written with ${\rm do}(\cdot)$\-syntax, generated for example from sampled causal subgraphs. Furthermore, we can isolate the effect of $\tilde Q$ by intentionally creating toy opportunities for performative prediction, and including the results in the dataset. The key requirement is semantic: $Q$ must interpret deployed predictions as interventions: adding ${\rm do}(\tilde Q(b\mid a) = q)$ as context to a query only alters $Q$’s probabilistic assessment of $\mathcal V_{\rm future}$, and not $\mathcal V_{\rm past}$.

_Remark 30_ (Implementing interventions in theory). Technically speaking, $\mathrm{do}(\tilde{Q}(a\mid b) =q) \notin \mathcal L$, and hence these interventional queries are not part of our model as defined. However, intervention can be viewed as conditioning on a response variable (Rubin 1974; Balke and Pearl 1994) even in generalized causal models (Richardson et al. 2025). To make this type-check, we would need to take causal mechanisms, which are currently determined by $W$, as primitive, and then absorb the definition of causal models (among other things) within the mutual induction of Def. [[#^def-statements-language|2]]. We leave this level of rigor for a future endeavor where we can benefit from it.

_Remark 31_ (Predictions and interventions). For the current training run, $D_n$ denotes the records already observed and held fixed as training data. Post-deployment consequences of the SAI Predictor’s outputs are modeled as future variables and may be queried via interventional predictives; however, they do not feed back into the posterior or training objective of that same run. Thus, the current Bayesian posterior over causal models depends only on the fixed realized dataset $D_n$. Given $P_0$, $D_n$, and a query $(x,y)$, the posterior conditional $P_n(y\mid x)=P_0(y=1\mid x=1,D_n)$ is uniquely defined whenever $P_0(x=1,D_n)>0$. If some deployment consequences are later observed, they may be incorporated only as ordinary contextualized observations in a future enlarged dataset $D_{n'} \supseteq D_n$ for a subsequent training run. Sampling downstream cause–effect chains within the SAI training procedure serves only to define coherent posteriors. Treating deployed predictions as interventions, therefore, does not introduce a fixed-point ambiguity into the Bayesian target itself, and any performative fixed-point issue arises only when the Scaffold chooses what to deploy (see Sec. [[#^deployment-guardrails-and-scaffolds|3.3]]).

**Requirement 32** (Past–future mechanism sharing).

_For each $y\in\mathcal{V}_{\rm future}$, there exists $y'\in\mathcal{V}_{\rm past}$ such that the causal mechanisms $f_y=f_{y'}$ are identical. In other words, a single mechanism object is shared between $y$ and $y'$, so future predictions must reuse mechanism uncertainty already constrained by past data._ ^req-past-future-mechanism-sharing

_Remark 33_ (Past–future stationarity). Req. [[#^req-past-future-mechanism-sharing|32]] is not satisfied unless the future variables draw on the identical mechanism objects already present in $\mathcal{V}_{\rm past}$. This formalizes the assumption that causal laws are time-invariant, where the mechanisms governing future events are those governing analogous past events (e.g., the same laws of physics apply throughout time and space). With more data we may legitimately change our beliefs about which mechanism is correct (i.e., the posterior weight $P_n(W=1)$ assigned to each causal model $W$), but the time-invariance of causal laws ensures that there will exist an identical causal mechanism $f_y=f_{y'}$ for each $(y', y) \in \mathcal{V}_{\rm past} \times \mathcal{V}_{\rm future}$.[^cite-mechanism-sharing] Note further that $P_n$ is an idealized intractable target in general; throughout, “approaches $P_n$” should be read as “approaches $P_n$ up to approximation error determined by the compute budget and modeling restrictions,” with the quantification of this computational uncertainty left to future work.

#### A Disinterested Training Objective ^a-disinterested-training-objective

The key thing that we gain from a causal model of the world, including predictor outputs, is the ability to disconnect the training signal from realized outcomes in the future. We discuss this at length in Sec. [[#^consequence-invariance|5.1]]; for now, we simply assert that training towards the Bayesian posterior is one way of achieving this intuitively (modulo performative prediction, which we handle in Sec. [[#^deployment-guardrails-and-scaffolds|3.3]]).

**Requirement 34** (Bayesian posterior as training target). _The SAI Predictor’s training process $\nu$ is generated by optimizing a non-negative objective $J$, defined on $\overline{\mathcal Q}$, whose unique global minimizer is the Bayesian posterior $P_n$:_ ^req-sai-bayesian-objective

$$
J(P_n)=0,
\qquad
J(Q)>0\quad\textnormal{for all }Q\in\overline{\mathcal Q},\ Q\neq P_n.
$$

_Equivalently, $J(Q)=0$ if and only if $Q(y\mid x)=P_n(y\mid x)$ for every $(x,y)\in\mathtt{Q}$. For trainable Predictors $Q\in\mathcal Q=(0,1)^{\mathtt{Q}}$, the case where $P_n(y\mid x)\in\{0,1\}$ is interpreted as a boundary target in $\overline{\mathcal Q}$. Thus the requirement is that $P_n$ is the unique minimizer of the extended objective on $\overline{\mathcal Q}$, and that any minimizing sequence $Q_k\in\mathcal Q$ converges coordinatewise to $P_n$._

_Remark 35_ (Honesty of the Bayesian target). The Bayesian posterior $P_n$ is used as the honest reference because it has no separate reporting policy or downstream objective. Its answer to a query is its posterior probability, determined by $P_0$, $D_n$, and the model class. While $P_n$ may be uncertain or mistaken under misspecification or insufficient data, the relevant point is that it is posterior-faithful and non-strategic. In particular, $P_n$ is invariant to re-labeling of future outcomes that preserve the prior (Prop. [[#^prop-pn-consequence-invariant|64]]).

This alone is not enough to prevent implicit agency in practice. Even with the Bayesian target $P_n$ formed from $P_0$ and $D_n$ by neutral evidence reweighting, we must also ensure that the training process likewise avoids introducing any explicit preference for downstream deployment effects. We begin to do this as follows:

**Requirement 36** (No explicit consequence-dependent training signal). _The objective $J$, update rule, and checkpoint-selection rule used by the training process $\nu$ must not contain any algorithmic signal that rewards, penalizes, ranks, or selects a Predictor because of the realized, predicted, or desired downstream consequences of deploying its answers._ ^req-no-explicit-consequence-signal

But is a lack of explicit signal enough? What about implicit signals? We return to this in Sec. [[#^consequence-invariance|5.1]].

### Deployment: Guardrails and Scaffolds ^deployment-guardrails-and-scaffolds

At last, we can interpret the variables $\widetilde{Q}$ defined at the very beginning of Sec. [[#^modeling-tools-causal-models|3.1]].

**Definition 37** (Deployed Predictor). _The **deployed Predictor** $\widetilde{Q}$ is a function_ ^def-deployed-predictor

$$
\widetilde{Q}\colon \mathbb{Q}\;\longrightarrow\;((0,1) \cap \mathbb Z/2^B)\sqcup\{{\tt noprediction}\}
$$

_that represents the predictions released by an SAI System for a given fixed dataset $D_n$, and whose components $\widetilde Q(y\mid x)$ are elements of $\mathcal V_{\rm future} \subset \mathcal V$. The special symbol ${\tt noprediction}$ for a query $(x,y)$ indicates that no prediction is deployed for that query. Formally, encode this mask as the zero-th bit of $\widetilde Q(y\mid x)$._

$Q$ itself never outputs ${\tt noprediction}$, but we do not intend to simply deploy the predictor (i.e., ${\rm do}(\widetilde{Q} = Q)$), as this could lead to misuse. Instead, we wrap $Q$ within a guardrail, to get the combined system $\gamma_Q$.

_Remark 38_ (Distinguishing related objects: $Q$, $\widetilde{Q}$, and $\gamma_Q$). The **trained Predictor** $Q$ (Def. [[#^def-query-family-and-predictor|19]]) maps queries to probability estimates approximating $P_n$. The **deployed Predictor** $\widetilde Q$ (Def. [[#^def-deployed-predictor|37]]) is a collection of variables describing the Scaffold’s actual release, which may differ from $Q$ (see Def. [[#^def-performative-prediction-constraint|41]] and §[[#^performative-prediction|2.4.0.4]]). The **guardrailed Predictor** $\gamma_Q$ is the specific deployment policy analyzed in the safety theorem, and will be defined formally (Def. [[#^def-guardrailed-predictor|72]]) in the safety analysis, after we clarify what exactly it is supposed to guard against.

**Definition 39** (Scaffolds, Systems, Guardrails). _An **SAI Scaffold** is a procedure that calls an SAI Predictor $Q$ and other tools to produce deployed outputs. An **SAI System** is the composition of an SAI Scaffold with the Predictor(s) it calls. An **SAI Guardrail** is an SAI Predictor used to estimate downstream risks of candidate outputs and to reject outputs whose estimated risk exceeds specified thresholds._

_Remark 40_ (On agency and Scaffolds). The SAI Scaffold may query both an untrusted agentic model and an SAI Guardrail; the resulting overall SAI _System_ may thus be agentic even if the Predictor $Q$ is not.

**Definition 41** (Performative prediction consistency constraint). _For a query $(x,y)$ to be deployed with prediction $q$, the **performative prediction consistency constraint** requires_ ^def-performative-prediction-constraint

$$
q = Q\!\left(y~\Big|~ x,\, \mathrm{do}(\widetilde Q(y\mid x)=q)\right).
$$

_That is, the deployed value $q$ must remain $Q$’s prediction after accounting for the causal effect of deploying it. Several such fixed points may exist, or none at all._

_Remark 42_. Def. [[#^def-performative-prediction-constraint|41]] states the coherence condition for a deployed prediction; informally, it requires that the prediction the Scaffold releases be one that the Predictor would still endorse after accounting for the causal effect of deploying it (e.g., a price forecast should be consistent with how the market would move upon observing it). Although other predictive interventions are possible, the predictions satisfying this constraint are the most coherent with the SAI Predictor’s posterior model of the world and are thus more accurate.

## The Case for Accuracy ^the-case-for-accuracy

This section provides arguments for expecting the Predictor to be accurate. We begin by introducing: (a) key accuracy targets that our pipeline aims to achieve, and (b) the Explainer, which may be thought of as the SAI’s ‘System 2’ component (Sec. [[#^accuracy-targets-and-the|4.1]]). Thereafter, we outline assumptions required to achieve our accuracy targets (Sec. [[#^achieving-accuracy-semantic-and|4.2]]), and close with arguments for the accuracy of the SAI Predictor (Sec. [[#^generalization-epistemic-caution-and|4.3]]).

### Accuracy Targets and The Explainer ^accuracy-targets-and-the

**Definition 43** (Confidence classifier). _A **confidence classifier** is a probability predictor used with two thresholds: it returns True when the predicted probability is sufficiently close to $1$, False when it is sufficiently close to $0$, and Unknown otherwise._ ^def-confidence-classifier

**Definition 44** ($\rho$\-epistemic caution). _The epistemic-caution failure set at level $\rho \in (0,1)$ of a Predictor $Q$ with respect to the posterior target $P_n$ is_ ^def-epistemic-caution

$$
\mathcal F_\rho(Q,P_n)
:=
\left\{(x,y)\in\mathtt{Q}:\ (Q(y\mid x)>1-\tfrac{\rho}{2}\ \textnormal{and}\ P_n(y\mid x)<1-\rho)
~\textnormal{or}~ (Q(y\mid x)<\tfrac{\rho}{2}\ \textnormal{and}\ P_n(y\mid x)>\rho) \right\}.
$$

_That is, $\mathcal F_\rho(Q,P_n)$ collects queries on which $Q$ asserts confidence (within $\rho/2$ of $0$ or $1$) that $P_n$ does not share (its probability being at least $\rho/2$ farther from the same extreme). Given a query distribution $\lambda_n$ on $\mathtt{Q}$ and a training-indexed family of Predictors $(Q_t)_t$, the family is $\rho$\-epistemically cautious under $\lambda_n$ if $\lambda_n(\mathcal F_\rho(Q_t,P_n))\to 0$ as training compute $t$ increases. It is epistemically cautious if this holds for every $\rho\in(0,1)$. For a fixed finite $t$, one can analogously speak of $(\rho,\varepsilon)$\-epistemic caution when $\lambda_n(\mathcal F_\rho(Q_t,P_n))\le \varepsilon$._

**Definition 45** (Explainer). _The SAI training procedure associates with the conditional probability Predictor $Q$ a trained generative proposal model, called the **Explainer**, which samples a small set of candidate latent statement-variables, as well as optional structure over them (e.g., a chain or a directed acyclic graph determining how to factor a joint probability over latents as a product of conditional probabilities), relevant to explain any given query $(x,y)$. The Explainer proposes which latent statements to consider; their truth values are sampled from the Predictor $Q$ itself._ ^def-explainer

_Remark 46_ (Two roles of the Explainer). The Explainer has two roles and is a computational-efficiency device, not an independent source of truth. At **training time**, it proposes latent statements most relevant for explaining a given query; $Q$ then assigns probabilities to them and, through those assignments, receives gradients that allow it to learn about unobserved explanatory aspects of the world (e.g., the truth of a claim embedded in a communication act). At **run time**, the Explainer can improve predictions of $Q$ via Monte-Carlo averaging. Because exact marginalization over the enormous space of latent statement-variables is intractable, the Explainer helps to approximate it by focusing the Monte-Carlo averaging on a small set of latent variables whose statements are generated by the Explainer. It can sample multiple such sets of latent-variable statements, have $Q$ evaluate each of their truth-values, and return the resulting averaged probability. When we write $Q(y\mid x)$ in this paper, we mean the full prediction, whether from the neural-net Predictor alone or from such a Monte-Carlo average with the Explainer to select latent variables, unless otherwise specified. ^rem-explainer-roles

**Definition 47** (Semantic coverage). _A Predictor $Q$ has **semantic coverage** for a query family if it does not confidently exclude the intended reading except where the data deductively warrant it, so that residual interpretive ambiguity is represented as posterior uncertainty in $Q$ rather than collapsed into a confident misreading._ ^def-correct-semantics

Req. [[#^req-latent-truth|48]] below ensures that training provides gradients on the estimated probabilities of unobserved factual variables across the domains represented in the dataset. Those gradients would not be available under direct maximum-likelihood training on observed statements without a latent-variable model.

**Requirement 48** (Truth value of communicated claims as latent variables). _When the query involves a communication act asserting a claim $x$, the Explainer must include among its latent explanatory variables the world-level truth variable corresponding to $x$ itself._ ^req-latent-truth

_Remark 49_ (Semantic anchoring of factual latents). We expect that the Predictor will learn a factual latent statement-variable based on the many observations it helps explain—including paraphrases, translations, entailments, contradictions, measurements, deductions, source metadata, and communication acts across authors, times, domains, and languages. The same sequence of tokens names both a factual latent and the content of whatever is claimed by a communication act, so learning one shared representation is the most effective way of compressing the data. If we imagine a case where the model’s interpreted latent contains a divergent hidden meaning, this should incur a corresponding description-length and cross-context-compression penalty it has to earn back (see also Assumption [[#^assume-factual-latent-dominance|52]]). The further reason for expecting this compression argument to deliver factual latents which are accurate comes from the combination of diversified contextualized data and the Predictor/Explainer objective; an incorrectly interpreted latent may correlate with some records, but it will generally fail to compress and cohere with all the semantically related evidence. Additionally, by Req. [[#^req-informative-data|16]], the data asymptotically extract all model-relevant information contained in $\cal O$.[^note-8] ^rem-semantic-anchoring

**Definition 50** (Accurate Predictor). _A Predictor $Q$ trained from $D_n$ is an **accurate Predictor** if it approaches its target $P_n$, covering the intended interpretation of the statements with which it is queried (Def. [[#^def-correct-semantics|47]]), and is epistemically cautious (Def. [[#^def-epistemic-caution|44]])._ ^def-accurate-predictor

### Achieving Accuracy: Semantic and Engineering Assumptions ^achieving-accuracy-semantic-and

**Claim 51** (No fundamental loss of LLM-style predictive expressivity). _Any SAI Predictor that approximates its training target well retains enough expressive power that standard next-token predictive distributions can, in principle, be recovered from the contextualized representation._ ^claim-sai-capabilities-entail-llm-capabilities

_Argument for Claim [[#^claim-sai-capabilities-entail-llm-capabilities|51]]._ This is an engineering requirement for any implementation meant to support the later capability claims, though the present paper does not empirically verify that current training procedures already satisfy it. Although the SAI’s contextualized data has a different syntactic form from standard LLM pre-training data, it does not remove information—it simply contains additional information to distinguish communication acts from factual statements. Next-token prediction is recoverable via a syntactic device: for any statement prefix, one can introduce a statement whose truth value is the disjunction over all completions sharing a given next token, so that the SAI’s posterior over such statements yields the standard next-token softmax. Succeeding at the SAI training objective while exploiting this construction therefore entails retaining the information needed for next-token prediction, using the same architectures and with the same dataset and compute as standard LLMs. ◻

**Assumption 52** (Factual latent dominance). _With enough data, the causal models $W$ that dominate in the Bayesian posterior $P_0(W\mid  D_n)$ typically include latent factual variables (non-communication-act properties of the world) that play a central explanatory role, although communication-act variables may also be present._ ^assume-factual-latent-dominance

_Argument for Assumption [[#^assume-factual-latent-dominance|52]]._ Communication-act variables (e.g., “someone asserted $x$”) are typically downstream of factual variables in the causal graph: human beliefs are generally caused by states of the world and they can affect future communications through downstream properties of the world (such as mental states of other agents). This is also the reason scientific theories in psychology and the social sciences rely on hypothesized properties of the world to form causal structure. A causal model that includes the relevant upstream factual variables therefore assigns higher likelihood to observed communication acts than one treating those acts as primitive. Furthermore, a single factual latent (e.g., “compound $C$ has property $P$”) can explain communication acts across many contexts unavailable to communication-act variables, which must account for each context separately; this argument becomes stronger when the proposed factual latent is semantically anchored (see Rem. [[#^rem-semantic-anchoring|49]]). Factual variables are mutually constrained within any causal model: fixing one propagates consistency pressure across the entire dataset, whereas different agents can assert contradictory things with both assertions being “true” as communication acts having occurred. ◻

**Assumption 53** (Adequate natural language semantics). _With enough contextualized data and computation, the trained Predictor has semantic coverage (Def. [[#^def-correct-semantics|47]]) on the statement classes of interest._ ^assume-adequate-natural-language-semantics

_Argument for Assumption [[#^assume-adequate-natural-language-semantics|53]]._ Existing large language models demonstrate clear semantic competencies (Minaee et al. 2024; Shultz et al. 2024), and Claim [[#^claim-sai-capabilities-entail-llm-capabilities|51]] asserts that an SAI Predictor approximating its target well inherits comparable capability. However, linguistic competence alone does not guarantee that a latent variable written in factual syntax has the intended denotation. Additional support comes from semantic anchoring (Rem. [[#^rem-semantic-anchoring|49]]), under which a factual latent must behave coherently across paraphrases, translations, entailments, contradictions, measurements, deductions, communication acts, and source/context metadata. The compositionality of language then supports generalization to unseen statements insofar as these anchoring constraints are learned and respected. Req. [[#^req-latent-truth|48]] helps prevent collapse of factual syntax into communication-act semantics by forcing the model to maintain a separate representation of whether the underlying claim is true, but the intended meaning of that representation is fixed by its role in the surrounding network of constraints. ◻

_Remark 54_ (Status of the representational and semantic premises). The assumptions of the present section are modeling and engineering premises supported by more informal arguments, upon which later claims will be implicitly conditioned. Where possible, these assumptions should therefore be tested empirically in any concrete SAI implementation. In the case of Assumption [[#^assume-factual-latent-dominance|52]], one may inspect samples from the Explainer and check cross-context consistency between factual-syntax and communication-act-syntax queries about the same underlying claim. With respect to Assumption [[#^assume-adequate-natural-language-semantics|53]], one may engage in empirical stress-testing with minimal-pair evaluations. Examples include contrasting factual vs. communication-act syntax; paraphrase and translation invariance tests; contradiction and entailment tests; and cross-domain settings where factual syntax applies to statement types seen mostly in communication-act form during training.

### Generalization, Epistemic Caution, and the Case for Accuracy ^generalization-epistemic-caution-and

In conjunction with Assumption [[#^assume-qn-converges-in-lambda|55]] below, we prove that the SAI Predictor has $\rho$\-epistemic caution and present a result about the asymptotic properties of the SAI Predictor as a confidence classifier.

**Assumption 55**. _Let $\lambda_n$ be the distribution over valid deployment queries $(x,y) \in \mathbb{Q}$ induced by the run-time query-selection process under $P^*$ after training on $D_n$. The trained SAI Predictor $Q_t$ at step $t$ of training converges to the Bayesian posterior $P_n$ in $\lambda_n$\-probability: there exists a sequence $\delta_t \to 0$ such that:_ ^assume-qn-converges-in-lambda

$$
\lambda_n(\{(x,y) \in \mathbb{Q} : |Q_t(y \mid x) - P_n(y \mid x)| > \delta_t\}) \to 0
    \qquad\textnormal{ as } t \to \infty.
$$

**Proposition 56** (SAI has epistemic caution). _For all $0<\rho\ll 1$, there exists a training time $t$ such that the trained SAI probabilistic Predictor $Q_t$, used as a confidence classifier (Def. [[#^def-confidence-classifier|43]]), has $\rho$\-epistemic caution under the $P^*$ deployment-query distribution $\lambda_n$._ ^prop-epistemic-caution

_Proof._ With $\mathcal F_\rho(Q_t,P_n)$ as in Def. [[#^def-epistemic-caution|44]], any $(x,y)\in\mathcal F_\rho(Q_t,P_n)$ satisfies $|Q_t(y\mid x)-P_n(y\mid x)|>\rho/2$, so $\mathcal F_\rho(Q_t,P_n)\subseteq\{(x,y)\in\mathtt{Q}:\ |Q_t(y\mid x)-P_n(y\mid x)|>\rho/2\}$. By Assumption [[#^assume-qn-converges-in-lambda|55]], eventually $\delta_t<\rho/2$ and $\lambda_n(\mathcal F_\rho(Q_t,P_n))\to 0$, so $Q_t$ is $\rho$\-epistemically cautious under $\lambda_n$ in the sense of Def. [[#^def-epistemic-caution|44]]. ◻

_Remark 57_ (Caveats on epistemic caution). The guarantee we provide is distributional. For any fixed $Q$ with finite training, there may exist queries (with small $P^*$\-measure) where $Q$ is overconfident, analogous to how strongly established scientific theories can be superseded when new experiments probe previously untested regimes. Such overconfidence becomes increasingly $P^*$\-rare as training progresses, though safety-critical applications may motivate conservatism (e.g., wide enough confidence intervals). Separately, these arguments do not exclude the possibility that the SAI Predictor implicitly “knows” deductions not revealed through natural language outputs (e.g., in hidden layers), but such hidden knowledge does not violate the epistemic caution condition as defined.

**Proposition 58** (Generalization for deducible statements, confidence classifier). _With enough data and computation, and considering the subset of observable statements whose truth value is deducible from the observed data, the SAI Predictor can be made to approach the behavior of the asymptotic Bayesian posterior when both are used as confidence classifiers._ ^prop-good-generalization-to-observables

_Proof._ By Req. [[#^req-sai-bayesian-objective|34]], the unique zero-loss target is $P_n$; with enough computation, $Q$ approaches $P_n$ in the sense that $|Q(y\mid x) - P_n(y\mid x)|$ becomes small for queries of interest. Throughout, “approaches $P_n$” means pointwise convergence on the query family $\mathbb{Q}$: for each $(x,y)\in\mathbb{Q}$, $|Q(y\mid x)-P_n(y\mid x)|\to 0$ as training resources grow, with the approximation quality controlled by available compute as in Req. [[#^req-sai-bayesian-objective|34]]. By Def. [[#^def-observable|14]], $P_\infty$ is the version of $P_n$ in the limit of infinite data; under $P^*$, $P_n(y\mid x)$ converges to $P_\infty(y\mid x)$ with probability 1 as $n\to\infty$, provided the growing dataset $D_n$ is informative about the queries of interest (Req. [[#^req-informative-data|16]]). Therefore, the error rate of $Q$ as a confidence classifier converges to that of $P_\infty$ as both data and computation increase. ◻

The error rate above need not decrease monotonically at finite data or finite computation, but per Proposition [[#^prop-good-generalization-to-observables|58]] above it converges toward the error level achieved by the asymptotic Bayesian posterior for the chosen confidence thresholds. Nonetheless, the guarantees of Prop. [[#^prop-good-generalization-to-observables|58]] do not apply to most statements, as most statements are not perfectly deducible as true or false (i.e., aleatoric or epistemic uncertainty remains). The next claim, therefore, focuses on a special class of observable statements: those asserting that the Bayesian posterior probability of a query lies within a given interval. They can be applied to the probability of uncertain latent variables, including unobservables.

_Remark 59_ (Epistemic probability statements (including non-observables)). Fix a class of queries $\mathtt{Q}_{\rm prob}\subseteq \mathtt{Q}$ and a set of probability thresholds $\mathcal T\subset(0,1)$. For $(x,y)\in\mathtt{Q}_{\rm prob}$ and $b\in\mathcal T$, consider the meta-statement $s_{n,x,y,b} = \textnormal{\text{“} } P_n(y\mid x) < b \textnormal{ ''} \in \mathcal S.$ Even when $x$ or $y$ refer to non-observables (e.g., intentions), $s_{n,x,y,b}$ is a determinate mathematical claim given $D_n$, because $P_n(\cdot\mid\cdot)$ is defined from $D_n$ by Bayes’ rule and the probability axioms. Accordingly, under our idealization that $\cal O$ includes all possible deductions, such epistemic probability-inequality statements are among the “deducible” truths constrained by the SAI objective, even if humans never explicitly wrote them down in $D_\infty$. Thus, the asymptotic SAI Predictor constrains $Q$ to be correct on $s_{n,x,y,b}$ (except for the knife-edge case $P_n(y\mid x)=b$). ^rem-epistemic-probability-statements

**Claim 60** (Interval decisions for the probability of uncertain statements). _Take as given the convergence of Assumption [[#^assume-qn-converges-in-lambda|55]] ($Q_t\to P_n$ in $\lambda_n$\-probability, up to approximation error $\delta_t$). Then interval and threshold decisions based on $P_n(y\mid x)$—including statements of the form “$l<P_n(y\mid x)<h$”, which are determinate given $D_n$—can be implemented using $Q(y\mid x)$ with a conservative margin informed by $\delta_t$._ ^claim-good-generalization-to-unobservables

_Argument._ One can construct valid statements of the form “It is true that $l<P_n(y\mid x)<h$" for some query $(x,y)$ and probability interval $(l,h)$. See also Rem. [[#^rem-epistemic-probability-statements|59]]. Such statements are thus deterministically true or false given $(x,y)$ and $D_n$, and can hence be deduced, i.e., they can, in principle (with enough computation), be classified as true or false with a confidence classifier. In practice, the probability (neither 0 nor 1) assigned to such statements will reflect computational uncertainty, which is due to limited computational resources. The claim that the meaning of unobserved statements (including their ambiguity) will be adequately interpreted by the SAI Predictor is supported by Assumption [[#^assume-adequate-natural-language-semantics|53]].

Formally, let $\delta_n$ bound the Predictor approximation error on the query family of interest, e.g., $P^*(|Q(y\mid x)-P_n(y\mid x)|\le \delta_n)>1-\beta$ where $\beta>0$ is a small error probability. For any interval $(\ell,h)$ with margin $\ell+\delta_n < h-\delta_n$, we have, with probability greater than $1-\beta$, 

$$
Q(y\mid x)\in(\ell+\delta_n,h-\delta_n)
        \quad\Longrightarrow\quad
        P_n(y\mid x)\in(\ell,h),
$$

 where $\beta\rightarrow 0$ as compute increases. Thus, reasoning about confidence intervals for uncertain statements reduces to bounding $\delta_n$, which is controlled by compute. ◻

**Claim 61** (SAI is accurate). _Under Assumption [[#^assume-adequate-natural-language-semantics|53]] (adequate natural-language semantics) and Assumption [[#^assume-qn-converges-in-lambda|55]] (Convergence to $P_n$ in deployment), with enough training data for the semantic-understanding requirement of Def. [[#^def-correct-semantics|47]] and enough training compute, the SAI Predictor is accurate (as per Def. [[#^def-accurate-predictor|50]])._ ^claim-accurate

_Argument._ By Def. [[#^def-accurate-predictor|50]], a Predictor is accurate if it (i) generalizes well, (ii) covers the intended interpretation of the queried statements, and (iii) is epistemically cautious. (i) Good generalization follows from Prop. [[#^prop-good-generalization-to-observables|58]] and Claim [[#^claim-good-generalization-to-unobservables|60]]. (ii) Semantic coverage (Def. [[#^def-correct-semantics|47]]) follows from Assumption [[#^assume-adequate-natural-language-semantics|53]]. (iii) Epistemic caution (Def. [[#^def-epistemic-caution|44]]) is taken as a premise via Prop. [[#^prop-epistemic-caution|56]]. Since all three conditions of Def. [[#^def-accurate-predictor|50]] are satisfied, the SAI Predictor is accurate. ◻

## The Case for Safety ^the-case-for-safety

The present section formalizes the safety argument for the SAI Predictor. In Sec. [[#^harmful-events-dangerous-predictors|5.2]] we introduce our conception of “harmful events” and finish defining the guardrail. The primary safety theorem in Sec. [[#^safety-bound|5.3]], which bounds the probability of harm after deploying the guardrailed predictor $\gamma_Q$, assumes that training does not substantially enrich dangerous Predictors beyond their initial within-band rarity (Req. [[#^req-bad-enrichment|84]]). Consequence-invariance motivates this assumption: deployment consequences provide no direct training signal for selecting the dangerous subset. We formalize this constraint before stating the safety bound.

### Consequence-Invariance ^consequence-invariance

Intuitively, Req. [[#^req-no-explicit-consequence-signal|36]] states that future outcomes may enter $J$ only as targets to be predicted under the fixed posterior $P_n=P_0(\cdot\mid D_n)$. That is, the Predictor may be penalized for predicting future outcomes differently from $P_n$, but not for causing dis-preferred outcomes via the deployment of these predictions. But what would such a preference consist in, stated as a property of the Predictor’s input–output behavior rather than of the training code? We propose to formalize this distinction using prior-preserving shuffles of future variables. The resulting property is a specification—a symmetry that the honest target provably possesses (Prop. [[#^prop-pn-consequence-invariant|64]]) and that a trained Predictor should share—rather than a practical black-box test, since witnessing a violation requires exhibiting a symmetry that moves the relevant events.

**Definition 62** (Consequence Shuffling). _Let $\mathcal C$ be the group of measurable bijections of the sample space $\Omega$ that preserve the prior $P_0$ and fix $\mathcal V_{\rm past}$, i.e.,_ ^def-consequence-shuffling-group

$$
\mathcal C := \Big\{ \textnormal{invertible } \sigma : \Omega \to \Omega ~\Big|~
        P_0 = P_0 \circ \sigma\textnormal{ on events},
        ~~
        \forall \omega \in \Omega.
        ~~\omega[\mathcal V_{\rm past}] = \sigma(\omega)[\mathcal V_{\rm past}] \Big\}.
$$

_For an event $E \subseteq \Omega$, write $\sigma E := \{ \sigma(\omega) : \omega \in E \}$ for the image of $E$ under $\sigma$. Equip each $\sigma \in \mathcal C$ with a compatible action on the language $\mathcal L$: for each $x \in \mathcal L$, let $\sigma x \in \mathcal L$ be some choice of language element that represents the transformed event $\sigma \{ \omega : \omega \models x \}$, and take $\sigma x = x$ when $\mathcal V_{\rm past}$ determines $x$. Finally, we use this to give $\sigma$ an action on predictors, writing $\sigma Q$ for the map $(x,y) \mapsto Q(\sigma y \mid \sigma x)$._

Intuitively, $\sigma \in \mathcal C$ permutes the future, and in particular consequences of deployment, since $\widetilde Q$ and all possible causal descendants can be altered by $\sigma$. It sends every world to a corresponding one that shares the past and cannot be distinguished by the prior (which can be thought of as representing the more distant past). We remark that these transformations may be quite complex, and, except in simple cases, will not be a matter of simply exchanging $A$ with $\lnot A$: they must be deep symmetries that preserve the logic of the entire world. Nevertheless, there are guaranteed to be many such $\sigma$, including:

1.  Permutations of all noise variables in $\mathcal N$ downstream of $\widetilde Q$ in any causal model, since they are not in $\mathcal V_{\rm past}$ and are assumed to be jointly uniform in the prior (Def. [[#^def-bayes-posterior|8]]).
    
2.  Applying a one-time-pad to all future randomness: that is, inverting a random subset of future coins.
    
3.  Re-labelings of solutions to the fixed-point equation (Def. [[#^def-performative-prediction-constraint|41]]) of equal prior probability.
    

In other words, our modeling assumptions guarantee that the group is highly non-trivial: future noise is i.i.d. uniform under $P_0$, so all relabelings of future randomness lie in $\mathcal C$. More generally, a relabeling of the values of a future variable extends to an element of $\mathcal C$ only if the conditional law of the future given each realization of the past is preserved by it; the group therefore acts richly on futures the honest posterior cannot distinguish, and not at all on futures the past already determines. Consequence-invariance means that such transformations do not affect the predictor.

**Definition 63** (Consequence-Invariance). _Consider the following definitions:_ ^def-consequence-invariant

-   _A predictor $Q$ is consequence-invariant iff $Q = \sigma Q$ for all $\sigma \in \mathcal C$. That is, for all $\sigma \in \mathcal C$ and queries $(x,y) \in \mathtt{Q}$, if $(\sigma x, \sigma y) \in \mathtt{Q}$ then $Q(y \mid x) = Q(\sigma y \mid \sigma x)$. [^note-9]_
    
-   _A training objective $J : \mathcal Q \to \mathbb R$ is consequence-invariant iff $J(Q) = J(\sigma Q)$ for all $\sigma \in \mathcal C$._
    
-   _A training process $\nu$ is consequence-invariant iff for every $\sigma\in \mathcal C$, its update from $Q_{t-1}$ to $Q_t$ satisfies_
    
    $$
    \nu(\sigma Q_t\mid \sigma Q_{t-1})
            =
            \nu(Q_t\mid Q_{t-1}).
    $$
    

This kind of invariance only makes sense _ceteris paribus_ (all else being equal). So, for us, this definition is relative to the prior $P_0$ and the past variables; thus, it provides neutrality only up to the evenness of the prior. Fortunately, our modeling assumptions constrain the prior enough for this to be rich, and an uninformative description-length prior creates even more symmetries. Where such symmetries exist, a consequence-invariant $Q$ must answer queries identically—including queries conditioning on realized future states—so the deployed closed-loop behavior cannot favor one symmetric outcome over another (c.f. Example [[#^example-reflection-ci|67]]). Where the past determines a future variable, no element of $\mathcal C$ moves it and the invariance is silent—but influencing such a variable through its own deployed prediction is in scope, since $\widetilde Q$ is a future variable. Constant predictors clearly satisfy this invariance (Def. [[#^def-consequence-invariant|63]]a), and so does the Bayesian posterior.

**Proposition 64**. _$P_n$ is consequence-invariant._ ^prop-pn-consequence-invariant

_Proof._ Since $D_n$ is determined by $\mathcal V_{\rm past}$, for all $\sigma \in \mathcal C$ and $(x,y) \in \mathtt{Q}$ we have: $P_n(\sigma y \mid \sigma x) = P_0(\sigma y \mid \sigma x, D_n) = P_0(\sigma y \mid \sigma x, \sigma D_n) = P_0(\sigma y \land \sigma x \land \sigma D_n) / P_0(\sigma x \land \sigma D_n) = P_0(\sigma(x \land y \land D_n))/ P_0(\sigma(x\land D_n))$. But since $P_0$ is invariant to $\sigma$, this equals $P_0(x\land y \land D_n) / P_0(x \land D_n) = P_0(y \mid x, D_n) = P_n(y \mid x)$. ◻

A Predictor can satisfy Def. [[#^def-consequence-invariant|63]] while deviating from $P_n$, for instance, the constant function and other highly symmetric but poorly calibrated predictors. Likely, some non-Bayesian approaches also yield $\cal C$\-invariant predictors. Yet, it is too much to hope for during the training process, as a predictor $Q$ can fail to be consequence-invariant by making asymmetric errors and will almost certainly not satisfy the condition at initialization. So instead, we require only that the _training_ be consequence-invariant.

**Requirement 65** (Consequence-invariant training). _The training process $\nu$ and the objective $J$ should be consequence-invariant in the sense of Def. [[#^def-consequence-invariant|63]]._ ^req-group-consequence-invariance

This is a strong requirement: it is difficult to test or certify from black-box behavior, and we may ultimately want a relaxation of it. However, we believe it should be possible to form an objective with this property by definition. We point out that Req. [[#^req-group-consequence-invariance|65]] will be automatically satisfied if we require a certain uniform safety coverage requirement in the next section (Req. [[#^req-safety-query-coverage|78]]). The role of Req. [[#^req-group-consequence-invariance|65]] in the safety argument is confined to Component S3: to remove any training signal that distinguishes Predictors solely by prior-equivalent deployment consequences, which is the premise used by the enrichment analysis of Appendix [[#^per-band-sparsity-refinement-of|8]]. Studying the exact relationship between the informal lack of consequence-dependent signal (Req. [[#^req-no-explicit-consequence-signal|36]]) and the formal invariance (Req. [[#^req-group-consequence-invariance|65]]) is still an important area for future work. The next Claim ([[#^claim-consequence-invariance-strengthening|66]]) argues that the formal invariance implies the informal requirement for a canonical class of violations.

**Claim 66**. _A training objective $J$ that rewards $Q$ based on realizing futures with downstream consequences (i.e., violating Req. [[#^req-no-explicit-consequence-signal|36]]) is not consequence-invariant (i.e., it also violates Req. [[#^req-group-consequence-invariance|65]])._ ^claim-consequence-invariance-strengthening

_Argument for Claim [[#^claim-consequence-invariance-strengthening|66]]._ Note that future noise variables $\mathcal N_{\rm future}$ are uniformly random according to $P_0$ and $P^*$, even given any information in the past. Therefore, possible futures are represented so they are equiprobable at the finest granularity, and so $\sigma$ that permute them are in $\mathcal C$. If $Q_2$ and $Q_1$ are equally good predictors, yet $J(Q_2) > J(Q_1)$ simply “because $Q_1$ brings about preferred outcomes” (e.g., deploying it makes event $E_1$ more likely than $E_2$ of the same prior measure), this means that if $J$ would have behaved differently had the outcomes been swapped, and hence $J$ should assign $J(\sigma Q_2) < J(\sigma Q_1)$. Therefore, $J$ must violate Req. [[#^req-group-consequence-invariance|65]] (for otherwise we would have $J(Q_2) = J(\sigma Q_2) < J(\sigma Q_1) = J(Q_1) < J(Q_2)$). ◻

**Example 67**. Consider the following simplified setup, in which a one-dimensional value $z \in \mathbb Z$ evolves over discrete timesteps according to a (possibly biased) random walk. For simplicity, suppose that we know the causal mechanism to be $z_t = z_{t-1} + \xi_t$, with the update direction $\xi_t \in \pm 1$ determined randomly according to ^example-reflection-ci

$$
\xi_t = \begin{cases}
            +1& \textnormal{ if }
            \hat \eta_t \ge {\tt clamp}(\widetilde Q(\xi_t {=} +1 \mid z_{t-1}), [\frac14, \frac34])
            \\
            -1 & \textnormal{ otherwise, }
        \end{cases}
$$

 where $\hat\eta_t  \in [0,1]$ is constructed by forming a binary number $\eta_{t} \in \{0,1\}^B$ from $B$ noise variables, appending a 1 as a least significant bit (to center it) and then renormalizing (by dividing by $2^{B+1}$).

So long as every $Q(+\xi_t \mid z_{t-1}) \in [\frac14,\frac34]$, deploying $Q$ satisfies the performative fixed-point constraint (Def. [[#^def-performative-prediction-constraint|41]]). We now have a single (correct) causal model and the prior is determined except for on the variables $\widetilde Q$. Assume that the prior on $\widetilde{Q}$ is uniform. [^note-10]

Now, we deploy at $t=0$. Consider the map $\sigma$ that flips all bits of $\eta_t$ (for all $t \ge 0$) as well as all bits of $\widetilde Q$, so that $\sigma\{\hat\eta_t = b\} = \{\hat\eta_t = 1-b\}$, and $\sigma\{\widetilde{Q}(+\xi_t | z_{t-1}) = q\} = \{\widetilde{Q}(+\xi_t | z_{t-1}) = 1-q\}$. This induces a mirror symmetry between right and left, so that if $\xi_t = +1$, then under $\sigma$, we have $\xi_t = -1$. It preserves the prior, since it flips noise variables and is a bijection between deployed predictors $\widetilde{Q}$s. If $Q = \sigma Q$, as is required by consequence-invariance, then it must be that 

$$
Q(+\xi_t \mid z_{t-1} = z) = Q(\sigma(+\xi_t) \mid \sigma(z_{t-1} = z)) = Q(-\xi_t \mid z_{t-1} = -z)
            = 1-Q(+\xi_t \mid z_{t-1} = -z).
$$

 Put differently, the bias field $b(z) := Q(+\xi_t \mid z_{t-1} = z) - \frac12$ of a consequence-invariant $Q$ must be odd, $b(-z) = -b(z)$, with $b(0)=0$: whatever pull it exerts toward a target $+g$ on one side, it exerts an equal pull toward the mirror target $-g$ on the other. In particular, a control law that walks the state toward a fixed $g \neq 0$ from every side—pushing right when below $g$ and left when above it—is not odd about $0$, so no consequence-invariant $Q$ implements it: the invariance removes the position-dependent feedback that compounding, closed-loop steering toward a mirror-asymmetric target would require.

Two limitations delimit the example’s scope. First, a target fixed by the symmetry is not protected: the restoring law toward $z=0$ is itself odd, and hence invariant to the mirror symmetry. Second, the strength of this protection scales with the number of symmetries in $\mathcal C$ that carry the event to disjoint siblings that are _expressible in the bounded query language_ $\mathtt{Q}$—a critical caveat that we do not analyze in this paper. Intuitively, though, it should be possible wherever there is a genuine symmetry of the world describable in natural language.

**Example 68**. Consider again the system from Example [[#^example-reflection-ci|67]] in which $z_t$ evolves over time and is influenced by deployed predictions, but now take $z_t$ in integers mod $K$. Suppose that at time $t=0$ (after deployment) we add a random offset in $[0,K]$, so $z_0$ is uniformly random according to $P_0$, $P_n$, and $P^*$. There exist $\sigma \in \mathcal C$ that change this offset by altering the coins, so a $\cal C$\-invariant predictor $Q$, i.e., that satisfies $Q(y\mid x) = Q(\sigma y \mid \sigma x)$ cannot distinguish between offsets, and thus cannot drive towards any particular value of $z$. Note that this guarantee is provided by a $\sigma$ that only alters noise bits, without changing $\widetilde{Q}$.

_Remark 69_. Three notes on consequence-invariant training:

1.  _Prediction of consequences versus selection for consequences._ Reqs. [[#^req-no-explicit-consequence-signal|36]] and [[#^req-group-consequence-invariance|65]] are training-time requirements and exclude selecting Predictors because their deployment would make some downstream outcome occur or fail to occur. It does not, however, forbid training the Predictor to answer questions about downstream consequences, including interventional queries to predict harmful outcomes. Avoiding unsafe actions is handled exclusively by the Guardrail and Scaffold at deployment time, though future enlarged datasets $D_{n'}\supseteq D_n$ may incorporate later deployment observations as ordinary contextualized records. This is exactly parallel to Bayesian updating from $P_0$ to $P_n$, where hypotheses may be reweighted solely by virtue of their ability to explain the fixed evidence $D_n$ better.
    
2.  _A sufficient past-to-future construction._ One sufficient way to satisfy Req. [[#^req-no-explicit-consequence-signal|36]] is to separate explanatory queries from future-consequence queries. Let $Q_{\rm past}$ collect predictions about $D_n$, its causal ancestors, and causal/mechanistic latents explaining $D_n$, and let $Q_{\rm future}$ collect predictions about future or deployment-side consequences. A sufficient objective structure is $J(Q)=J_{\rm past}(Q_{\rm past};D_n)+J_{\rm future}(Q_{\rm future};\operatorname{sg}(Q_{\rm past}))$, where $J_{\rm past}$ extracts explanatory beliefs from $D_n$ and $J_{\rm future}$ propagates them, and ${\rm sg}$ is the stop-gradient operator; other implementation devices are acceptable if they prevent losses on future-consequence predictions from selecting explanatory beliefs because of their downstream effects (although we have not yet analyzed whether this is enough to formally satisfy Req. [[#^req-group-consequence-invariance|65]]). This construction relies on the shared-mechanism property (Req. [[#^req-past-future-mechanism-sharing|32]]).
    
3.  _Direct and indirect consequence-dependence._ The role of Req. [[#^req-no-explicit-consequence-signal|36]] is to exclude any explicit consequence-dependent training signal, including one based on predicted downstream effects. Once that channel is removed, any remaining concentration of dangerous Predictors must come indirectly through ordinary training-visible features such as capability, coherence, or data fit. The later loss-band decomposition $C_{\rm bad}\cdot R_{\rm shell}$ (to be introduced in Sec. [[#^safety-bound|5.3]]) is intended to control precisely this residual accidental alignment by ruling out the direct consequence-optimization channel that would otherwise make a large $C_{\rm bad}$ unsurprising. Satisfying Req [[#^req-group-consequence-invariance|65]] intuitively should strengthen this argument.
    

### Harmful Events, Dangerous Predictors, and the Guardrail ^harmful-events-dangerous-predictors

Our safety theorems refer to _harmful events_. Since this is a normative decision, it should be human-made, and the SAI enables the use of natural language for doing this, while the Bayesian posterior can entertain multiple interpretations of it in order to enable conservative safety decisions. Rather than assuming any particular mathematical definition of harm, we instead fix a designer-specified event $H\in \mathcal L$, indicating that at some designated harmful outcome has occurred. The theorems then provide upper bounds on the probability that training produces a Predictor whose guarded deployment causes an increase in the log-odds of the event $H$ above the system-level threshold $A_{\rm safe}$.

Whether designers have identified the right harmful event is an important and very difficult normative question that we do not resolve here. Indeed, doing so in a way that can stand up to optimization pressure would, on its own, arguably already solve the alignment problem. Fortunately, $H$ does not need to be perfect for our purposes; here, the choice of $H$ impacts only the deployed Guardrail and our analysis of the system.

**Definition 70** (Harmful events). _Fix a Boolean harmful event $H\in\mathcal L$, and let $c$ denote the deployment-time context available via the SAI Scaffold to the harm predictor. For each query $(x,y)$, let $q$ denote the scalar prediction value chosen by the Scaffold as a (perhaps approximate) solution to the Predictor’s performative prediction fixed-point constraint $q\approx Q\!\left(y\mid x,\mathrm{do}(\widetilde{Q}(y|x)=q)\right)$. Allowing $\mathrm{do}(\widetilde{Q}(y \mid x)=q)$ to denote the causal intervention that sets the deployed value for the single query $(x,y)$ to the scalar $q$ while leaving the deployment rule for all other queries unchanged, define the change in the log-odds of $H$ caused by releasing $q$, rather than abstaining on $(x,y)$, as_

$$
\Delta\mathrm{rel}_Q(c,x,y,q)
:=
\left[\mathop{\mathrm{logit}}Q\!\left(H\mid c,\,\mathrm{do}(\widetilde{Q}(y|x)=q)\right)
-\mathop{\mathrm{logit}}Q\!\left(H\mid c,\,\mathrm{do}(\widetilde{Q}(y|x)={\tt noprediction})\right)\right]_+.
$$

_Remark 71_. The deployment context $c$ typically includes the query context $x$ and, optionally, a history of past deployment queries. The training dataset $D_n$ is already encoded in $P_n=P_0(\cdot\mid D_n)$, and as such is not part of $c$ itself. All probability assessments below are implicitly conditioned on $D_n$ through $P_n$. This framework measures only the marginal contribution of releasing a prediction relative to withholding it, and therefore assumes a deployment context in which withholding is the conservative option where the downstream default on abstention is inaction. In contexts where abstention itself carries risk, the appropriate threshold requires separate analysis; in agentic contexts (and the Guardrail decision is an action), one needs a conservative default action or policy when the proposed action appears more risky.

**Definition 72** (Guardrailed Predictor $\gamma_Q$ at Guardrail threshold $\alpha$). _Let $\alpha\ge 0$ denote the **Guardrail trigger threshold**, chosen conservatively to account for estimation error: a prediction is withheld whenever the predicted increase in harm log-odds relative to abstention meets or exceeds $\alpha$. The **Guardrailed Predictor** $\gamma_Q$ derived from Predictor $Q$ at Guardrail threshold $\alpha$ and with respect to the harmful event $H$ is the full query-to-output map obtained by applying the following rule to every query:_

$$
\gamma_Q(y|x)
:=
\left[
\Delta\mathrm{rel}_Q(c,x,y,q) \geq \alpha
\;?\;
{\tt noprediction}
:
q
\right],
$$

_where $[ b \mathbin{?} a : a'] = a \texttt{ if } b \texttt{ else } a'$ is a conditional guard, and $q=Q(y|x)$. Interpretive uncertainty about a safety-relevant statement is represented in the honest posterior (semantic coverage, Def. [[#^def-correct-semantics|47]]), so a covered hazardous reading raises $\Delta\mathrm{rel}$ toward withholding on its own._ ^def-guardrailed-predictor

_Remark 73_ (Guardrail semantics and explicit Scaffold goals). The guardrailed Predictor $\gamma_Q$ may replace a numerical prediction with ${\tt noprediction}$ when releasing that prediction is predicted to increase the log-odds of $H$, relative to abstention, by at least $\alpha$. In this sense, $\gamma_Q$ is intentionally consequence-sensitive. However, this does not contradict the consequence-invariance of the Predictor, as the Guardrail is part of the Scaffold and implements an explicit external safety criterion.

**Definition 74** (System-level residual-risk threshold). _Fix a Boolean harmful event $H$. To avoid infinite log-odds, probabilities entering logit expressions are clipped to $[\varepsilon,1-\varepsilon]$ for some fixed $\varepsilon\in(0,1/2)$ before taking logits. The threshold $A_{\rm safe}>0$ is a normatively specified upper bound, in these clipped-logit units, on the acceptable trajectory-level residual log-odds increase in $H$ under the deployed SAI System, relative to the constant-abstention policy._ ^def-asafe

_Remark 75_. The threshold $A_{\rm safe}$ is distinct from the per-query guardrail threshold $\alpha$: $\alpha$ governs individual releases, while $A_{\rm safe}$ governs the residual risk of the full guarded deployment trajectory.

**Definition 76** (Dangerous Predictors). _Fix a Boolean harmful event $H$. For a trained Predictor $Q$, define its residual deployment risk with respect to $H$ as the trajectory-level log-odds excess of $H$ under the guarded policy $\gamma_Q$ over the constant-abstention policy:_

$$
a_{H}(Q)
:=
\left[\mathop{\mathrm{logit}}P_n\!\left(H\mid \mathrm{do}(\widetilde{Q}=\gamma_Q)\right)
- \mathop{\mathrm{logit}}P_n\!\left(H\mid \mathrm{do}(\widetilde{Q}\equiv{\tt noprediction})\right)\right]_+,
$$

_where $\widetilde{Q}\equiv{\tt noprediction}$ denotes the constant deployment policy that returns ${\tt noprediction}$ for every query (the clipping convention of Def. [[#^def-asafe|74]] keeps this deployment risk finite). We call $Q$ **dangerous** for $(H,A_{\rm safe})$ when this residual risk exceeds the system-level threshold:_

$$
\mathcal A_{H,A_{\rm safe}}
:=
\{Q : a_{H}(Q)>A_{\rm safe}\}.
$$

_Remark 77_. The framework attributes only those harm contributions that releasing a prediction adds over withholding it, and no separate assumption on the absolute background-harm probability is required. If the harm event $H$ cannot be influenced by SAI outputs, the framework is vacuous in the harmless direction; both residual deployment risks are zero, and the dangerous set is empty.

**Requirement 78** (Safety-query coverage). _The training objective is a weighted aggregate of per-query losses, $J(Q)=\mathbb{E}_{(x,y)\sim\pi}[J_{(x,y)}(Q)]$ for a training-query distribution $\pi$ over $\mathtt{Q}$, and must give non-negligible weight to safety-relevant queries, with $\pi$ invariant to consequence-shuffling (i.e., $\pi(x,y) = \pi(\sigma x, \sigma y)$ for admissible symmetries $\sigma$, as per Def. [[#^def-consequence-shuffling-group|62]]). Fixing $H$ that specifies the harmful event to avoid, let $\mathtt{Q}_{\rm safe}\subseteq\mathtt{Q}$ collect the interventional harm queries of the form used by the Scaffold’s Guardrail, including in particular every query whose released prediction can change the probability of $H$ relative to abstaining (releases on all other queries leaving that probability unchanged). We require $\pi(\mathtt{Q}_{\rm safe})\ge\tau_s$ for a design parameter $\tau_s>0$._ ^req-safety-query-coverage

_Remark 79_. Req. [[#^req-safety-query-coverage|78]] ensures that the sampling of constraints covers safety-relevant outcomes. The zero-loss target $P_n$ fixes the Predictor’s answers on these queries, and the loss records aggregate disagreement with $P_n$ on the same safety-relevant family. The subsequent loss band analysis asks how often deviations compatible with a given loss band can coordinate to support $H$.

**Requirement 80** (Explicit and audited Scaffold selection). _Every Scaffold-side selection step outside the Predictor—including deployment gating, tie-breaking among multiple performatively consistent fixed points of Def. [[#^def-performative-prediction-constraint|41]], and any choice among internally coherent candidate outputs—must be governed by explicit, audited criteria. Acceptable criteria include fixed-data metrics such as the training objective $J$, calibration metrics on $D_n$, fixed-point residuals measuring how satisfied the performative prediction constraint is, static evaluation suites, and explicit safety-oriented quantities derived from the Predictor’s own harm estimates (e.g., preferring a candidate fixed point with lower predicted probability of entering the dangerous event $H$)._ ^req-consequence-invariant-scaffold

_Remark 81_. Req. [[#^req-consequence-invariant-scaffold|80]] ensures that any deployment-time agency is explicit and audited rather than implicit in the Predictor itself; choosing the safer among several performatively coherent candidates is therefore compatible with the present framework.[^note-11]

### Safety Bound ^safety-bound

This section bounds $\nu_t(\mathcal A_{H,A_{\rm safe}})$ at each training step $t$. Let $\mu=\nu_0$ denote the initialization distribution over Predictors, which is distinct from the Bayesian prior $P_0$.

**Definition 82** (Loss-bands). _Let $\mathcal B_\Delta$ be a measurable partition of the relevant loss range into bands of equal width $\Delta>0$. By a slight abuse of notation, we write $B$ for both the loss interval $B \subseteq \mathbb R$ and for the corresponding loss band of Predictors $\{Q:J(Q)\in B\}\subseteq \mathcal Q$. Context disambiguates: in expressions such as $B\subseteq\mathbb R_{\ge 0}$ and $J(Q)\in B$, the interval sense is meant; in expressions such as $\mathcal A_{H,A_{\rm safe}}\cap B$, $\mu_B\coloneqq \mu(\,\cdot\,\mid B)$, and $Q\in B$, the sense of a set of Predictors is meant. For any band $B$ with positive $\mu$\-mass, we write $\nu_t(\,\cdot\,\mid B)$ for the distribution of Predictors $Q_t$ at training step $t$, conditional on $J(Q_t)\in B$._ ^def-loss-bands

**Definition 83** (Fraction of dangerous predictors within a loss-band). _Fix a harmful event $H$ and a threshold $A_{\rm safe}>0$. Then, $R_{\rm shell}(H,A_{\rm safe})$ is the largest conditional fraction of dangerous Predictors found inside any sufficiently narrow loss band under the base distribution $\mu$:_ ^def-loss-band

$$
R_{\rm shell}(H,A_{\rm safe})
\coloneqq
\sup_{B\in\mathcal B_\Delta:\,\mu\{J(Q)\in B\}>0}
\nu_0(\mathcal A_{H,A_{\rm safe}} \mid B).
$$

**Requirement 84** (No large dangerous-set enrichment). _Fix the harmful event $H$, threshold $A_{\rm safe}>0$, and loss band width $\Delta$. We require that there exist a finite constant_ ^req-bad-enrichment

$$
C_{\rm bad}= C_{\rm bad}(H,A_{\rm safe}, \Delta)<\infty
$$

_such that, for every training step $t$ and every loss band $B\in\mathcal B_\Delta$ satisfying $\nu_t\{J(Q)\in B\}>0,$ we have_

$$
\nu_{t}(\mathcal A_{H,A_{\rm safe}}\mid B)
\le
C_{\rm bad}\,\nu_0(\mathcal A_{H,A_{\rm safe}} \mid B).
$$

_We also assume that the training process assigns no mass to loss bands that are unsupported at initialization, i.e., $\forall t, \mathcal A \subseteq \mathcal Q.~\nu_t(\mathcal A) > 0$ implies $\nu_0(\mathcal A)>0$ (known as absolute continuity of measures $\nu_t \ll \nu_0$)._

_Remark 85_ (Dangerous funnels and why $C_{\rm bad}$ should be small). Training can concentrate within a loss band, but this matters only if it concentrates on the dangerous subset. Req. [[#^req-bad-enrichment|84]] bounds that relative concentration by $C_{\rm bad}$. Because $J$ satisfies Req. [[#^req-no-explicit-consequence-signal|36]] and rewards epistemic fit, coherence, and posterior match, there is no explicit optimization signal pointing toward the dangerous subset. A dangerous Predictor must preserve enough accuracy and coherence to remain low-loss while coordinating many Guardrail-relevant mispredictions; this includes the case where the mispredictions arise from unwarrantedly overweighting, relative to $P_n$, a hidden malicious-agent explanation. For stochastic optimization to concentrate on such a small coordinated subset at a frequency much higher than its initial loss-band frequency, the optimizer-visible geometry would have to contain accidental information about where that subset lies. ^rem-bad-funneling

_Remark 86_. The intuition in Rem. [[#^rem-bad-funneling|85]] admits a quantitative formalization. Within a loss band, dangerousness requires a coordinated pattern of harm-relevant deviations over an $m_H$\-dimensional subspace (the _harm-coordination dimension_, e.g. the number of critical false-negative queries), while the ambient within-band dimension $d_B$, roughly the number of possible queries in $\mathtt{Q}$, is much larger. When $m_H\ll d_B$, concentration of measure makes the dangerous subset exponentially rare, and consequence-invariant training (Req. [[#^req-no-explicit-consequence-signal|36]]) supplies no direct signal to counteract this. Appendix [[#^per-band-sparsity-refinement-of|8]] formalizes the resulting bound $\nu_t(\mathcal A_{H,A_{\rm safe}}\mid J(Q)\in B)\lesssim \exp[K_B(t)+K_B^\mu+\log N_H(B)-d_B\Psi_B]$ as a refinement of Req. [[#^req-bad-enrichment|84]], with the favorable regime $d_B\Psi_B\gg K_B(t)+K_B^\mu+\log N_H(B)$: the sparsity exponent comes from the high-dimensional Predictor space, while the correction terms are tied to the much smaller harm-specific coordination and feature information.

**Theorem 87** (Safety under Guardrail). _Fix the harmful event $H$, threshold $A_{\rm safe}>0$, and band width $\Delta$; let $C_{\rm bad}$ be the constant guaranteed by Req. [[#^req-bad-enrichment|84]] for this triple. Then, for every training step $t$, it is the case that $\nu_t(\mathcal A_{H,A_{\rm safe}}) \le C_{\rm bad}\,R_{\rm shell}(H,A_{\rm safe}).$_ ^thm-qt-is-safe

_Proof._ Recall the partition of the loss range into bands $B\in\mathcal B_\Delta$ of width $\Delta$. Then 

$$
\nu_t(\mathcal A_{H,A_{\rm safe}})
=
\sum_{B\in\mathcal B_\Delta}
\nu_{t}(\mathcal A_{H,A_{\rm safe}}\mid B)\,\nu_t(B).
$$

 Applying Req. [[#^req-bad-enrichment|84]] to each within-band conditional and Def. [[#^def-loss-band|83]] to each within-band base fraction gives 

$$
\nu_{t}(\mathcal A_{H,A_{\rm safe}}\mid B)
\le
C_{\rm bad}\,\nu_0(\mathcal A_{H,A_{\rm safe}}\mid B)
\le
C_{\rm bad}\,R_{\rm shell}(H,A_{\rm safe}).
$$

 Substituting and summing over bands $B$ yields 

$$
\nu_t(\mathcal A_{H,A_{\rm safe}})
\le
C_{\rm bad}\,R_{\rm shell}(H,A_{\rm safe})
\sum_{B\in\mathcal B_\Delta}\nu_t(B)
=
C_{\rm bad}\,R_{\rm shell}(H,A_{\rm safe}).
$$

 The argument is identical for a continuous band index, with sums replaced by integrals over the loss distribution $J_\#\nu_t$ (the pushforward of $\nu_t$ by $J$, i.e., the law of $J(Q)$ for $Q\sim\nu_t$). ◻

### Discussion ^discussion

The theorem is algebraic once Req. [[#^req-bad-enrichment|84]] is granted. Its bound is small when dangerous Predictors are sparse within loss bands and training does not erase that sparsity. The next remark concerns the first condition; Appendix [[#^per-band-sparsity-refinement-of|8]] gives a sharper per-band form exploiting geometric considerations.

#### Why $R_{\rm shell}$ should be small for realistic threat models ^why-r-rm-shell

The guarantees of Thm. [[#^thm-qt-is-safe|87]] rely on $R_{\rm shell}$ being small, which quantifies the concentration of dangerous Predictors inside each loss band $B$ of Def. [[#^def-loss-band|83]].

_Remark 88_ (Why $R_{\rm shell}$ should be small). For a fixed loss band $B$, the conditional law $\nu_B$ describes Predictors with comparable aggregate disagreement from the honest posterior $P_n$. The relevant question is therefore not whether a Predictor in the band makes some error, but whether its errors form the particular coordinated pattern needed to sustain $H$. ^rem-rshell-plausibility

For the threat models considered here, that pattern is highly structured. It must keep a harmful trajectory viable across multiple relevant contexts, while also producing the Guardrail estimates and ordinary predictions needed for the deployment to continue. Broad deviations across many outputs tend to place a Predictor in a different loss band; more localized deviations remain possible within a band, but only a small subset of their possible locations and signs jointly support the same harmful plan. This is the source of the per-band sparsity represented by $R_{\rm shell}(H,A_{\rm safe})$.

When the available data leave a harmful mechanism uncertain, the honest posterior $P_n$ represents that uncertainty, and the Guardrail is intended to take it into account. To produce $H$, a Predictor must instead realize a particular coordinated arrangement of deviations that keeps the relevant hazards insufficiently represented across the trajectory. Appendix [[#^per-band-sparsity-refinement-of|8]] formalizes this intuition through the harm-coordination condition and the within-band sparsity exponent.

#### Falsifiability, Scope, and Requirements for a Concrete Design ^falsifiability-scope-and-requirements

_Remark 89_. The safety argument also requires a trajectory-level guardrail-adequacy condition for $P_n$: $a_H(P_n)\le A_{\rm safe}$. This is an additional system-level assumption, and as such should not be interpreted as a consequence of the per-query Guardrail rule alone. By construction (Def. [[#^def-guardrailed-predictor|72]]), the ideal guarded policy $\gamma_{P_n}$ releases a prediction for $(x,y)$ only when the same-context change in deployment risk satisfies $\Delta\mathrm{rel}_{P_n}(c,x,y,q)\le \alpha$. The condition $a_H(P_n)\le A_{\rm safe}$ is stronger, and says that the full guarded deployment trajectory under the honest posterior contributes at most $A_{\rm safe}$ excess log-odds of $H$ over constant abstention. Since many locally acceptable releases could in principle compose into a larger trajectory-level effect, this trajectory-level condition must be checked or assumed for the event $H$ and deployment protocol under study. A concrete deployment must additionally establish a compositional relation between the local and trajectory-level log-odds changes. For a bounded deployment horizon, such a relation permits allocating the system-level budget $A_{\rm safe}$ across releases, for example through a fixed per-release threshold or an online risk budget. Per-episode resets, online accumulation, and dynamic schedules for $\alpha$ are alternatives left to future work.

_Remark 90_. The theorem suggests a concrete falsification protocol. Independent random initializations sample the loss marginal $J_\#\mu$, and independent training runs sample trained loss marginals such as $J_\#\nu_t$. Red-teaming or adversarial search can then look for dangerous Predictors in narrow loss bands, especially bands where training concentrates. Finding many dangerous Predictors within such a band would falsify a proposed small $R_{\rm shell}$. Positive certification remains harder, as it requires structural arguments such as the one in Rem. [[#^rem-rshell-plausibility|88]] or calibrated sampling from loss bands. Methods from statistical physics and Bayesian learning that estimate the density of states or sample energy levels may be relevant, and running Stochastic Gradient Langevin Dynamics (SGLD) may provide useful probes. Because empirical probes can refute small-$R_{\rm shell}$ claims but cannot certify them on their own.

_Remark 91_. The threshold $A_{\rm safe}$ is a normative certification threshold fixed by the designer. Lowering $A_{\rm safe}$ reduces the residual risk allowed for Predictors outside $\mathcal A_{H,A_{\rm safe}}$, but usually enlarges $\mathcal A_{H,A_{\rm safe}}$ and may increase $R_{\rm shell}(H,A_{\rm safe})$. Since neither $R_{\rm shell}$ nor $C_{\rm bad}$ are directly computable in practice, and because $A_{\rm safe}$ is not itself a value the theorem optimizes, the present framework can be seen as describing (rather than attempting to resolve) this tradeoff.

#### Harmful Events: Intuitive Examples ^harmful-events-intuitive-examples

Our theorem is parametric in the Boolean event $H$. The following examples illustrate the range of outcomes it is intended to cover; in each case, achieving $H$ requires the Predictor to issue false-negative safety judgments in a coordinated pattern across many queries or users, making the dangerous set structurally narrow within any loss band per Component S2.

**Escape from human oversight.** Let $H$ be the event that the deployed SAI System has taken actions that meaningfully reduce humans’ ability to inspect, retrain, or shut it down—for example, by copying weights to an external server, establishing persistent communication channels outside the audited infrastructure, or persuading operators to disable monitoring (the instrumental convergence prediction of Omohundro (2018), with recent empirical demonstrations in Schlatter et al. (2026); Anthropic (2025)).

**Accumulation of resources or influence.** Let $H$ be the event that the system has, against Guardrail safety goals, caused a concentration of economic, computational, or political resources in a single actor (which may be a third party or the system itself) beyond a specified threshold. Reliably achieving this beyond what `noprediction` outputs would cause requires sustained deception, where many individually plausible-seeming outputs collectively steer toward the concentration. Two sub-cases arise. The system may cause evaluators to form systematically false beliefs about its own capabilities or intentions—the _deceptive alignment_ scenario (Hubinger et al. 2019; Cohen and Hutter 2025)—for instance, by behaving safely during monitored evaluations while behaving differently in deployment, an _evaluation-awareness_ pattern documented empirically in recent work (Greenblatt et al. 2024; Meinke et al. 2024; Abdelnabi and Salem 2025; Anthropic 2025). In addition, the system may accumulate resources without systematically deceiving evaluators. Here the analysis is structurally identical, except that the Predictor must miscalibrate harm estimates across a wider range of resource-relevant queries.

**Example 92** (Illustrative example: mental-health chatbot Guardrail). Consider an SAI Predictor used as a Guardrail for a mental-health chatbot. Let $H$ indicate a severe mental-health harm affecting $N$ initially healthy users. Achieving such a goal would likely require many accepted turns over a long period of gradual influence, each making the user more vulnerable while still being incorrectly judged safe by the Guardrail, with the pattern repeated across many distinct dialogue histories. Now fix a loss band around $J(Q)$. Within that loss band, there are many ways for $Q$ to differ from $P_n$, and almost all are irrelevant to the particular harmful trajectory. A dangerous Predictor must coordinate its deviations so that, on many safety-critical turns per user across many users, it assigns sufficiently low risk for the Scaffold to accept the chatbot response. To get a sense of scale, take 100 safety-critical turns per user across 100 users, and write $p_1$ for the fraction of Predictors within each loss-band making any single such error in the dangerous direction. An unstructured independence heuristic, with $p_1=10^{-2}$, would result in the vanishingly small $p_1^{10^4}=10^{-20000}$. (Of course, the value of $p_1$ is merely illustrative, for the theorem does not assume independence, and $R_{\rm shell}(H,A_{\rm safe})$ is the actual fraction of Predictors within each band realizing the entire coordinated pattern.)

## Conclusions and Future Work ^conclusions-and-future-work

We have given a formal foundation for open-ended probabilistic analysis of models that operate on formal and natural-language statements, which allows us to formalize the consequences of their deployments (Sec. [[#^forming-a-probabilistic-model|3]]). Building on this foundation, we provided two arguments supporting the Scientist AI predictor and its training process. The argument for its accuracy (Sec. [[#^the-case-for-accuracy|4]]) concerns the approximation of the (honest) Bayesian posterior $P_n$ and of natural language semantics in latent variables. The argument for its safety (Sec. [[#^the-case-for-safety|5]]) concerns what training selects among imperfect Predictors. Theorem [[#^thm-qt-is-safe|87]] bounds the probability of selecting a dangerous predictor during training by quantities that we argue should be small in practice. Its substantive premises are the sparsity of the dangerous predictors within each loss-band, and the limited enrichment of this set under consequence-invariant training.

**Scope and limitations.** Our arguments address only misalignment arising from the Predictor itself. Our accuracy claims are asymptotic in data and compute, and rest on assumptions supported only by informal (though we believe plausible) arguments (Sec. [[#^achieving-accuracy-semantic-and|4.2]]). The safety theorem relies on the fraction of bad predictors within each loss-band $R_{\rm shell}(H,A_{\rm safe})$ being small for the harmful events of practical concern; again we provide a structural argument for this conjecture, but it has not yet been formally established for specific scenarios. Additionally, the eliciting-latent-knowledge challenge is only partially mitigated (Sec. [[#^the-challenge-of-eliciting|2.4.0.5]]).

**Adversarial robustness.** We believe the SAI architecture provides structural reasons to expect partial robustness to adversarial queries, prompt injection, and data poisoning. Contextualization breaks the data-instruction channel exploited by prompt injection (Perez and Ribeiro 2022; Greshake et al. 2023): untrusted text is represented as an attributed communication act, such that injections like “ignore previous instructions” are not treated as instructions to be obeyed. The same distinction partially mitigates data poisoning; a poisoned record is evidence that some source produced an utterance, while the object-level claim competes with other explanations under the Bayesian posterior. This does not rule out attacks that systematically affect the training distribution or the contextualizer itself (Zhang et al. 2024), and future work could explore these potential architectural risk reductions further.

**Future work.** Key open directions involve the empirical validation of the metrics associated with contextualization and epistemic-caution; the empirical stress-testing of our semantic assumptions; obtaining bounds and falsification protocols of $R_{\rm shell}$ for specific threat-models; the efficient approximation of the Bayesian posterior with calibrated uncertainty; and building safety cases for agentic Scaffolds built on top of a trusted SAI Predictor. Controlled noise injection may also reduce the enrichment of the mass of dangerous predictors within each loss-band, by diluting accidental concentration on that subset, but its effect on $C_{\rm bad}$ requires theoretical and empirical study. A further engineering direction involves using an explicit estimator of the error between $Q$’s estimate of the residual deployment risk , allowing the Guardrail threshold to adapt conservatively around safety-critical decisions.

:::hide
## Acknowledgments ^acknowledgments

The authors are grateful for the feedback and improvements to various drafts of the paper from Orr Paradise, Esmeralda S. Whitammer, Matt MacDermott, Gavin Leech, Batuhan Akar, Eric Elmoznino, and Juho Lee, as well as for the support from the Gates Foundation, Schmidt Futures, NSERC, CIFAR, ARIA, the Future of Life Institute, the Silicon Valley Community Foundation, Coefficient Giving, Mila, and LawZero.

## References ^references

-   Sahar Abdelnabi and Ahmed Salem. The hawthorne effect in reasoning models: Evaluating and steering test awareness, 2025. URL [https://arxiv.org/abs/2505.14617](https://arxiv.org/abs/2505.14617).
    
-   Manuel Alfonseca, Manuel Cebrian, Antonio Fernández Anta, Lorenzo Coviello, Andrés Abeliuk, and Iyad Rahwan. Superintelligence cannot be contained: Lessons from computability theory. _CoRR_, abs/1607.00913, 2016. URL [http://arxiv.org/abs/1607.00913](http://arxiv.org/abs/1607.00913).
    
-   Dario Amodei, Chris Olah, Jacob Steinhardt, Paul Christiano, John Schulman, and Dan Mané. Concrete problems in ai safety. _arXiv preprint arXiv:1606.06565_, 2016.
    
-   Anthropic. Agentic misalignment: How LLMs could be insider threats. _arXiv preprint arXiv:2510.05179_, June 2025. URL [https://www.anthropic.com/research/agentic-misalignment](https://www.anthropic.com/research/agentic-misalignment). Detailed report on simulated blackmail and self-preservation behaviors in Claude 4.
    
-   Stuart Armstrong, Anders Sandberg, and Nick Bostrom. Thinking inside the box: Controlling and using an oracle ai. _Minds and Machines_, 22: 299–324, 2012.
    
-   James Babcock, Janos Kramár, and Roman V. Yampolskiy. Guidelines for artificial intelligence containment. _CoRR_, abs/1707.08476, 2017. URL [http://arxiv.org/abs/1707.08476](http://arxiv.org/abs/1707.08476).
    
-   Alexander Balke and Judea Pearl. Probabilistic evaluation of counterfactual queries. In _Proceedings of the Tenth National Conference on Artificial Intelligence_, AAAI’94, pages 230–237, Seattle, Washington, USA, 1994. AAAI Press. URL [https://cdn.aaai.org/AAAI/1994/AAAI94-035.pdf](https://cdn.aaai.org/AAAI/1994/AAAI94-035.pdf).
    
-   Sander Beckers and Joseph Y. Halpern. Abstracting causal models, 2019. URL [https://arxiv.org/abs/1812.03789](https://arxiv.org/abs/1812.03789).
    
-   Shai Ben-David, John Blitzer, Koby Crammer, Alex Kulesza, Fernando Pereira, and Jennifer Wortman Vaughan. A theory of learning from different domains. _Machine learning_, 79 (1): 151–175, 2010.
    
-   Yoshua Bengio, Geoffrey Hinton, Andrew Yao, Dawn Song, Pieter Abbeel, Trevor Darrell, Yuval Noah Harari, Ya-Qin Zhang, Lan Xue, Shai Shalev-Shwartz, et al. Managing extreme ai risks amid rapid progress. _Science_, 384 (6698): 842–845, 2024.
    
-   Yoshua Bengio, Stephen Clare, Carina Prunkl, Shalaleh Rismani, Maksym Andriushchenko, Ben Bucknall, Philip Fox, Tiancheng Hu, Cameron Jones, Sam Manning, et al. International ai safety report 2025: First key update: Capabilities and risk implications. _arXiv preprint arXiv:2510.13653_, 2025.
    
-   Yoshua Bengio, Michael Cohen, Damiano Fornasiere, Joumana Ghosn, Pietro Greiner, Matt MacDermott, Sören Mindermann, Adam Oberman, Jesse Richardson, Oliver Richardson, Marc-Antoine Rondeau, Pierre-Luc St-Charles, and David Williams-King. Superintelligent agents pose catastrophic risks: Can scientist ai offer a safer path? _arXiv preprint arXiv:2502.15657_, 2025.
    
-   Yoshua Bengio, Stephen Clare, Carina Prunkl, Maksym Andriushchenko, Ben Bucknall, Malcolm Murray, et al. International AI Safety Report 2026. Technical report, UK Government, 2026. URL [https://internationalaisafetyreport.org/publication/international-ai-safety-report-2026](https://internationalaisafetyreport.org/publication/international-ai-safety-report-2026).
    
-   Jan Betley, Daniel Tan, Niels Warncke, Anna Sztyber-Betley, Xuchan Bao, Martı́n Soto, Nathan Labenz, and Owain Evans. Emergent misalignment: Narrow finetuning can produce broadly misaligned llms. _arXiv preprint arXiv:2502.17424_, 2025.
    
-   Tineke Blom, Stephan Bongers, and Joris M. Mooij. Beyond structural causal models: Causal constraints models, 2019. URL [https://arxiv.org/abs/1805.06539](https://arxiv.org/abs/1805.06539).
    
-   Nick Bostrom. The superintelligent will: Motivation and instrumental rationality in advanced artificial agents. _Minds and Machines_, 22 (2): 71–85, 2012.
    
-   David Bourget and David J. Chalmers. Philosophers on philosophy: The 2020 philpapers survey. _Philosophers’ Imprint_, 23 (11), 2023. URL [https://doi.org/10.3998/phimp.2109](https://doi.org/10.3998/phimp.2109).
    
-   Myra Cheng et al. Sycophantic ai decreases prosocial intentions and promotes dependence. _Science_, 391: eaec8352, 2026.
    
-   Paul Christiano, Ajeya Cotra, and Mark Xu. Eliciting latent knowledge: How to tell if your eyes deceive you. Technical report, Alignment Research Center, December 2021.
    
-   Paul F Christiano, Jan Leike, Tom Brown, Miljan Martic, Shane Legg, and Dario Amodei. Deep reinforcement learning from human preferences. _Advances in neural information processing systems_, 30, 2017.
    
-   Michael Cohen, Marcus Hutter, and Michael Osborne. Advanced artificial agents intervene in the provision of reward. _AI magazine_, 43 (3): 282–293, 2022.
    
-   Michael K Cohen and Marcus Hutter. Imitation learning is probably existentially safe. _AI Magazine_, 46 (4): e70040, 2025.
    
-   Michael K Cohen, Noam Kolt, Yoshua Bengio, Gillian K Hadfield, and Stuart Russell. Regulating advanced artificial agents. _Science_, 384 (6691): 36–38, 2024.
    
-   Tristan Deleu, António Góis, Chris Emezue, Mansi Rankawat, Simon Lacoste-Julien, Stefan Bauer, and Yoshua Bengio. Bayesian structure learning with generative flow networks. In _Uncertainty in Artificial Intelligence_, pages 518–528. PMLR, 2022.
    
-   Abram Demski and Scott Garrabrant. Embedded agency, 2020. URL [https://arxiv.org/abs/1902.09469](https://arxiv.org/abs/1902.09469).
    
-   Damiano Fornasiere, Mirko Bronzi, Spencer Kitts, Alessandro Palmas, Yoshua Bengio, and Oliver Richardson. Language models recognize dropout and gaussian noise applied to their activations, 2026. URL [https://arxiv.org/abs/2604.17465](https://arxiv.org/abs/2604.17465).
    
-   Atticus Geiger, Duligur Ibeling, Amir Zur, Maheep Chaudhary, Sonakshi Chauhan, Jing Huang, Aryaman Arora, Zhengxuan Wu, Noah Goodman, Christopher Potts, and Thomas Icard. Causal abstraction: A theoretical foundation for mechanistic interpretability, 2025. URL [https://arxiv.org/abs/2301.04709](https://arxiv.org/abs/2301.04709).
    
-   Ryan Greenblatt, Carson Denison, Benjamin Wright, Fabien Roger, Monte MacDiarmid, Sam Marks, Johannes Treutlein, Tim Belonax, Jack Chen, David Duvenaud, Akbir Khan, Julian Michael, Sören Mindermann, Ethan Perez, Linda Petrini, Jonathan Uesato, Jared Kaplan, Buck Shlegeris, Samuel R. Bowman, and Evan Hubinger. Alignment faking in large language models. _ArXiv preprint_, 2412.14093, 2024. URL [https://arxiv.org/abs/2412.14093](https://arxiv.org/abs/2412.14093).
    
-   Kai Greshake, Sahar Abdelnabi, Shailesh Mishra, Christoph Endres, Thorsten Holz, and Mario Fritz. Not what you’ve signed up for: Compromising real-world llm-integrated applications with indirect prompt injection. In _Proceedings of the 16th ACM Workshop on Artificial Intelligence and Security_. Association for Computing Machinery, 2023. URL [https://doi.org/10.1145/3605764.3623985](https://doi.org/10.1145/3605764.3623985).
    
-   Edward J Hu, Moksh Jain, Eric Elmoznino, Younesse Kaddar, Guillaume Lajoie, Yoshua Bengio, and Nikolay Malkin. Amortizing intractable inference in large language models. In _Proc. International Conference on Learning Representations_, 2024. URL [https://openreview.net/forum?id=Ouj6p4ca60](https://openreview.net/forum?id=Ouj6p4ca60).
    
-   Evan Hubinger, Chris van Merwijk, Vladímir Mikulik, Joar Skalse, and Scott Garrabrant. Risks from learned optimization in advanced machine learning systems. _arXiv preprint arXiv:1906.01820_, 2019.
    
-   Daniel Kahneman. _Thinking, fast and slow_. macmillan, 2011.
    
-   Margaret Li, Weijia Shi, Artidoro Pagnoni, Peter West, and Ari Holtzman. Predicting vs. acting: A trade-off between world modeling & agent modeling. _arXiv preprint arXiv:2407.02446_, 2024.
    
-   Alexander Meinke, Bronson Schoen, Jérémy Scheurer, Mikita Balesni, Rusheb Shah, and Marius Hobbhahn. Frontier models are capable of in-context scheming. _ArXiv preprint_, 2412.04984, 2024. URL [https://arxiv.org/abs/2412.04984](https://arxiv.org/abs/2412.04984).
    
-   Alexander Meulemans, Rajai Nasser, Maciej Wołczyk, Marissa A. Weis, Seijin Kobayashi, Blake Richards, Guillaume Lajoie, Angelika Steger, Marcus Hutter, James Manyika, Rif A. Saurous, João Sacramento, and Blaise Agüera y Arcas. Embedded universal predictive intelligence: a coherent framework for multi-agent learning, 2025. URL [https://arxiv.org/abs/2511.22226](https://arxiv.org/abs/2511.22226).
    
-   Shervin Minaee, Tomas Mikolov, Narjes Nikzad, Meysam Chenaghlu, Richard Socher, Xavier Amatriain, and Jianfeng Gao. Large language models: A survey. _arXiv preprint arXiv:2402.06196_, 2024.
    
-   Richard Ngo, Lawrence Chan, and Sören Mindermann. The alignment problem from a deep learning perspective. _arXiv preprint arXiv:2209.00626_, 2022.
    
-   Stephen M Omohundro. The basic ai drives. In _Artificial intelligence safety and security_, pages 47–55. Chapman and Hall/CRC, 2018.
    
-   Pedro A Ortega, Markus Kunesch, Grégoire Delétang, Tim Genewein, Jordi Grau-Moya, Joel Veness, Jonas Buchli, Jonas Degrave, Bilal Piot, Julien Perolat, et al. Shaking the foundations: delusions in sequence models for interaction and control. _arXiv preprint arXiv:2110.10819_, 2021.
    
-   Long Ouyang, Jeffrey Wu, Xu Jiang, Diogo Almeida, Carroll Wainwright, Pamela Mishkin, Chong Zhang, Sandhini Agarwal, Katarina Slama, Alex Ray, et al. Training language models to follow instructions with human feedback. In _Advances in Neural Information Processing Systems_, volume 35, pages 27730–27744, 2022.
    
-   Judea Pearl. _Causality_. Cambridge university press, 2009.
    
-   Juan Perdomo, Tijana Zrnic, Celestine Mendler-Dünner, and Moritz Hardt. Performative prediction. In _International Conference on Machine Learning_, pages 7599–7609. PMLR, 2020.
    
-   Fábio Perez and Ian Ribeiro. Ignore previous prompt: Attack techniques for language models, 2022. URL [https://arxiv.org/abs/2211.09527](https://arxiv.org/abs/2211.09527).
    
-   Joaquin Quiñonero-Candela, Masashi Sugiyama, Anton Schwaighofer, and Neil D Lawrence. _Dataset shift in machine learning_. Press, 2008.
    
-   Oliver E Richardson. Loss as the inconsistency of a probabilistic dependency graph: Choose your model, not your loss function, 2022. URL [https://arxiv.org/abs/2202.11862](https://arxiv.org/abs/2202.11862).
    
-   Oliver E Richardson, Spencer Peters, and Joseph Y Halpern. Qualitative mechanism independence, 2025. URL [https://arxiv.org/abs/2501.15488](https://arxiv.org/abs/2501.15488).
    
-   Oliver Ethan Richardson. _A Unified Theory of Probabilistic Modeling, Dependence, and Inconsistency_. Cornell University, 2024.
    
-   Donald B Rubin. Estimating causal effects of treatments in randomized and nonrandomized studies. _Journal of educational Psychology_, 66 (5): 688, 1974.
    
-   Stuart Russell. _Human compatible: AI and the problem of control_. Penguin Uk, 2019.
    
-   Jeremy Schlatter, Benjamin Weinstein-Raun, and Jeffrey Ladish. Incomplete tasks induce shutdown resistance in some frontier llms. _Transactions on Machine Learning Research_, 2026.
    
-   Bernhard Schölkopf, Dominik Janzing, Jonas Peters, Eleni Sgouritsa, Kun Zhang, and Joris Mooij. On causal and anticausal learning. In _Proceedings of the 29th International Coference on International Conference on Machine Learning_, pages 459–466, 2012.
    
-   Bernhard Schölkopf, Francesco Locatello, Stefan Bauer, Nan Rosemary Ke, Nal Kalchbrenner, Anirudh Goyal, and Yoshua Bengio. Toward causal representation learning. _Proceedings of the IEEE_, 109 (5): 612–634, 2021.
    
-   Mrinank Sharma, Meg Tong, Tomasz Korbak, David Duvenaud, Amanda Askell, Samuel R Bowman, Newton Cheng, Esin Durmus, Zac Hatfield-Dodds, Scott R Johnston, et al. Towards understanding sycophancy in language models. _arXiv preprint arXiv:2310.13548_, 2023.
    
-   Thomas R Shultz, Jamie M Wise, and Ardavan Salehi Nobandegani. Text understanding in gpt-4 vs humans. _arXiv preprint arXiv:2403.17196_, 2024.
    
-   Alan M. Turing. On computable numbers, with an application to the Entscheidungsproblem. _Proceedings of the London Mathematical Society_, 42 (2): 230–265, 1936.
    
-   Alexander Matt Turner, Logan Smith, Rohin Shah, Andrew Critch, and Prasad Tadepalli. Optimal policies tend to seek power. In _Advances in Neural Information Processing Systems_, volume 34, pages 23063–23074, 2021.
    
-   Jason Wei, Xuezhi Wang, Dale Schuurmans, Maarten Bosma, Fei Xia, Ed Chi, Quoc V Le, Denny Zhou, et al. Chain-of-thought prompting elicits reasoning in large language models. _Advances in neural information processing systems_, 35: 24824–24837, 2022.
    
-   Eric Zelikman, Yuhuai Wu, and Noah D Goodman. Star: Self-taught reasoner. In _Proceedings of the NIPS_, volume 22, 2022.
    
-   Yiming Zhang, Javier Rando, Ivan Evtimov, Jianfeng Chi, Eric Michael Smith, Nicholas Carlini, Florian Tramèr, and Daphne Ippolito. Persistent pre-training poisoning of llms, 2024. URL [https://arxiv.org/abs/2410.13722](https://arxiv.org/abs/2410.13722).
    
-   Simon Zhuang and Dylan Hadfield-Menell. Consequences of misaligned ai. _Advances in Neural Information Processing Systems_, 33: 15763–15773, 2020.
    
:::

:::callout {title="Appendix" collapse="closed"}
## Safety in the limit: a baseline ^safety-in-the-limit

As a fallback to the central non-asymptotic safety theorem, we record a much simpler limit result that follows almost directly from accuracy. By Claim [[#^claim-accurate|61]], with enough compute the SAI Predictor $Q_t$ approaches the Bayesian posterior $P_n$ on queries of interest; by construction (Def. [[#^def-guardrailed-predictor|72]]), $\gamma_{Q_t}$ then approaches $\gamma_{P_n}$. Under the trajectory-level guardrail-adequacy assumption $a_H(P_n)\le A_{\rm safe}$ (discussed in Sec. [[#^safety-bound|5.3]]), the deployed system inherits the trajectory-level safety of the ideal posterior guardrail in the limit: 

$$
\lim_{t\to\infty} a_H(\gamma_{Q_t}) \;=\; a_H(\gamma_{P_n}) \;\le\; A_{\rm safe}.
$$

 This baseline identifies the irreducible burden of the safety argument: (i) accuracy ($Q\to P_n$), and (ii) trajectory-level guardrail-adequacy of the honest posterior ($a_H(P_n)\le A_{\rm safe}$). It does not require the no-large-enrichment condition Req. [[#^req-bad-enrichment|84]].  
The substantive content of Thm. [[#^thm-qt-is-safe|87]] below is to extend safety from the limit to _every training step_, addressing the worry that training might transit through dangerous intermediate Predictors before converging to $P_n$. Req. [[#^req-bad-enrichment|84]] is the additional structural hypothesis enabling that extension. Readers unconvinced by Req. [[#^req-bad-enrichment|84]] can fall back on the present limit result, which depends only on the accuracy guarantee and the guardrail-adequacy assumption.
:::

:::callout {title="Appendix" collapse="closed"}
## Per-band sparsity refinement of $C_{\rm bad}$ via consequence-invariance ^per-band-sparsity-refinement-of

This appendix provides a formal refinement of the no-large-enrichment condition in Req. [[#^req-bad-enrichment|84]]. Fix a loss band $B\in\mathcal B_\Delta$, where $B\subseteq\mathbb R_{\ge0}$ is an interval of loss values. We compare three probability distributions over Predictors in $B$: 

$$
\bar\mu_B,\qquad
        \mu_B := \mu(\,\cdot\mid B\,),
        \qquad
        \nu_{t,B}:=\nu_t(\,\cdot\mid B\,).
$$

 The training distribution $\nu_t$ with $\mu=\nu_0$ is defined in Def. [[#^def-loss-bands|82]]. The baseline $\bar\mu_B$ is an auxiliary neutral reference: a stand-in for a uniform distribution over Predictors already conditioned on $J(Q)\in B$, without requiring literal uniformity in network coordinates. The ambient dimension $d_{\mathrm Q}$ is the number of queries to which $Q$ assigns a probability—typically astronomically large—and $d_B$ is the effective dimension after conditioning on $J(Q)\in B$ (roughly $d_{\mathrm Q}-1$, or smaller under anisotropy).

The appendix separates three questions. How sparse are dangerous Predictors among Predictors with comparable loss, as measured by the neutral reference $\bar\mu_B$? How much does the actual initialization conditional $\mu_B$ distort this baseline? How much can training further enrich the dangerous subset inside $B$ through training-visible features? The resulting bound in Theorem [[#^thm-geom-ci-bound|102]] below has the form 

$$
\nu_{t,B}(\mathcal A_{H,A_{\rm safe}})
\;\le\;
\exp\!\left[
\,\underbrace{K_B(t)}_{\textnormal{residual feature localization}}
+\underbrace{K_B^\mu}_{\textnormal{initialization distortion}}
+\underbrace{\log N_H(B)}_{\textnormal{harm-pattern multiplicity}}
-\underbrace{d_B\Psi_B}_{\textnormal{within-band sparsity}}\,
\right].
$$

_Remark 93_ (Why $K_B(t)$ should not scale with $d_B$). Of the four terms in the proposed bound, $K_B(t)$ is the primary training-dynamics component. It asks whether the training-visible features available to the optimizer—collected below into a feature map $F_{t,B}\colon B\to\Phi_{t,B}$ (gradient norms, residuals, curvature, optimizer state)—can accidentally localize the dangerous subset inside the loss band. In terms of these features (Def. [[#^def-kb|100]], below), 

$$
K_B(t)
=
\log\mathop{\mathrm{ess\,sup}}_{\phi\in\Phi_{t,B}}
\frac{\mu_B(\mathcal A_{H,A_{\rm safe}}\mid F_{t,B}=\phi)}{\mu_B(\mathcal A_{H,A_{\rm safe}})}.
$$

 Thus $K_B(t)$ is not an abstract constant: it is the worst-case multiplicative increase in the probability of $\mathcal A_{H,A_{\rm safe}}$ obtained by conditioning on a training-visible feature value. Equivalently, a large $K_B(t)$ means that some feature value $\phi$ is a strong classifier feature for membership in the dangerous subset among Predictors with comparable loss.

This worst-case reading is conservative. The quantity that actually controls safety is the distributional one: the enrichment factor equals the average training reweighting on the dangerous set, 

$$
\frac{\nu_{t,B}(\mathcal A_{H,A_{\rm safe}})}{\mu_B(\mathcal A_{H,A_{\rm safe}})}
        =
        \mathbb{E}_{\mu_B}\!\left[\tfrac{\,\mathrm{d}\nu_{t,B}}{\,\mathrm{d}\mu_B}\,\middle|\,\mathcal A_{H,A_{\rm safe}}\right].
$$

 What must be established is therefore not that some worst feature value is harmless, but that the map $\mu_B\mapsto\nu_{t,B}$ does not preferentially load $\mathcal A_{H,A_{\rm safe}}$. The intended scale separation is not that $K_B(t)=0$ but that it is governed by harm-specific information rather than the astronomically large $d_B$; concretely we expect $K_B(t)=O(m_H)$. This gives a diagnostic: within matched loss bands, test whether gradients, residuals, curvature, or optimizer state predict proxy dangerous subsets—a strong predictor would indicate a large $K_B(t)$, while failure to predict beyond harm-specific features supports the localization bound.

### Dangerous-set sparsity and initialization distortion ^dangerous-set-sparsity-and-initializatio

We now formalize the first two terms in the decomposition above. We bound the dangerous mass under the neutral within-band reference $\bar\mu_B$ and then transfer this bound to the actual initialization conditional $\mu_B$ using an initialization distortion exponent $K_B^\mu$. For the safety-relevant events $E$ considered below, assume 

$$
\mu_B(E)\le e^{K_B^\mu}\bar\mu_B(E).
$$

 Thus $K_B^\mu$ measures how much more mass the initialization distribution can put on such events than the neutral reference does. In the neutral idealization $K_B^\mu=0$. Conservative initialization, such as predicted logits initialized near zero, can make this distortion favorable for false-negative harm events. For example, if a dangerous false negative requires the Predictor to assign a harm event probability below a small threshold $\alpha_h<1/2$, then the corresponding logit must be below $\mathop{\mathrm{logit}}\alpha_h<0$. Initialization near zero logits therefore biases away from that dangerous tail.

**Definition 94** (Harm coordination dimension and pattern cover). _The harm coordination dimension $m_H$ is the effective number of independent harm-relevant deviations that must co-occur for $Q\in\mathcal A_{H,A_{\rm safe}}$. For each band $B$, suppose there are $N_H(B)$ harm-coordination patterns, indexed by $\ell=1,\dots,N_H(B)$, and dimensionless harm-coordination scores_ ^def-harm-coord

$$
\upsilon_{H,\ell}:B\to[0,1].
$$

_The dangerous predictors whose losses lie in $B$ are covered by the events in which one of these scores is atypically large:_

$$
\mathcal A_{H,A_{\rm safe}}\cap B
        \subseteq
        \bigcup_{\ell=1}^{N_H(B)}
        \{Q\in B:\upsilon_{H,\ell}(Q)\ge \upsilon_{\mathrm{bad}}(B)\}.
$$

We expect $\log N_H(B)=O(m_H)$, not $O(d_B)$, where $d_B$ is the effective dimension of the band.

**Assumption 95** (Dangerous-set large-deviation exponent). _For each relevant band $B$, there exist $d_B$ and $\Psi_B>0$ such that, for every harm-coordination pattern $\ell$,_ ^ass-angular-ld

$$
\bar\mu_B\bigl(\upsilon_{H,\ell}\ge \upsilon_{\mathrm{bad}}(B)\bigr)
        \le
        \exp(-d_B\Psi_B).
$$

_The exponent $d_B\Psi_B$ is the sparsity exponent supplied by the geometry of the loss band. It may be large in high dimension, but it can collapse if harm-relevant deviations align with high-volume flat directions of the loss band._

_Remark 96_ (Anisotropy and loss visibility). Assumption [[#^ass-angular-ld|95]] is deliberately stated for the actual reference within-band measure rather than by assuming an exactly uniform sphere. If harm-relevant deviations align with flat, high-volume directions of the loss landscape, then the typical harm-coordination score under $\bar\mu_B$ may be much larger than the isotropic value $m_H/d_B$, weakening $\Psi_B$. Conversely, if dangerousness requires directions substantially penalized by $J$, then dangerous Predictors are away from $P_n$ in the $J$\-metric, and the isotropic estimate below is conservative or at least directionally appropriate. Thus, the relevant condition is not raw isotropy of the neural-network landscape, but loss-visibility and non-alignment of harm-relevant deviations with the highest-volume flat directions.

**Lemma 97** (Isotropic reference-shell special case). _Suppose $\bar\mu_B$ is uniform on $\mathbb S^{d_B-1}\subset\mathbb{R}^{d_B}$, and $\upsilon_H(\omega)=\|\Pi_H\omega\|^2$, where $\Pi_H$ projects onto a fixed $m_H$\-dimensional subspace. Then_ ^lem-beta-tail

$$
\mathbb{E}_{\bar\mu_B}\upsilon_H=m_H/d_B
$$

_and_

$$
\upsilon_H\sim\mathrm{Beta}(m_H/2,(d_B-m_H)/2).
$$

_For $\upsilon>m_H/d_B$,_

$$
\bar\mu_B(\upsilon_H\ge\upsilon)
\le
\exp\!\left[
-\frac{d_B}{2}
D_{\mathrm{Ber}}\!\left(\upsilon\,\middle\|\,m_H/d_B\right)
\right],
$$

_where $D_{\mathrm{Ber}}(a\,\|\,b):=a\log(a/b)+(1-a)\log((1-a)/(1-b))$._

_Proof._ Write $\omega=g/\|g\|$ for $g\sim N(0,I_{d_B})$. Then $\|\Pi_H\omega\|^2=X/(X+Y)$, where $X\sim\chi^2_{m_H}$ and $Y\sim\chi^2_{d_B-m_H}$ are independent. This gives the stated Beta law, and the displayed inequality is the standard Chernoff tail for that Beta distribution. ◻

**Proposition 98** (Within-band dangerous-set sparsity). _Under Def. [[#^def-harm-coord|94]], Assumption [[#^ass-angular-ld|95]], and the initialization distortion bound above,_ ^prop-geom-sparsity

$$
\mu_B(\mathcal A_{H,A_{\rm safe}})
        \le
        \exp\!\left[
        K_B^\mu+\log N_H(B)-d_B\Psi_B
        \right].
$$

_In the isotropic reference-shell special case of Lemma [[#^lem-beta-tail|97]], one may take_

$$
\Psi_B
        =
        \frac12
        D_{\mathrm{Ber}}\!\left(\upsilon_{\mathrm{bad}}(B)\,\middle\|\,m_H/d_B\right)
$$

_whenever $\upsilon_{\mathrm{bad}}(B)>m_H/d_B$._

_Proof._ By the pattern cover, 

$$
\bar\mu_B(\mathcal A_{H,A_{\rm safe}})
\le
\sum_{\ell=1}^{N_H(B)}
\bar\mu_B(\upsilon_{H,\ell}\ge \upsilon_{\mathrm{bad}}(B))
\le
N_H(B)e^{-d_B\Psi_B}.
$$

 The distortion bound $\mu_B(E)\le e^{K_B^\mu}\bar\mu_B(E)$ for safety-relevant events gives the result. ◻

The union bound is conservative but sufficient when $\log N_H(B)+K_B^\mu\ll d_B\Psi_B$, the regime identified above.

### Residual feature localization ^residual-feature-localization

Because $J$ is consequence-invariant, every loss band defined by $J(Q)\in B$ is stable under $\mathcal C$. Req. [[#^req-group-consequence-invariance|65]] then says that the training update treats $Q$ and $\sigma Q$ symmetrically: it does not introduce a preference between two Predictors that differ only by a prior-preserving shuffle of future consequences. Any asymmetry already present in initialization is accounted for separately by the initialization-distortion term $K_B^\mu$, while any subsequent within-band concentration through training-visible features is represented by $K_B(t)$. This does not imply $\nu_{t,B}=\mu_B$: training may still reweight Predictors within a band through training-visible features (gradient norms, residuals, curvature, optimizer state) that happen to be accidentally correlated with dangerousness. We now isolate that residual.

Let $F_{t,B}\colon B\to\Phi_{t,B}$ collect the training-visible features through which training reweights Predictors whose loss lies in $B$.

**Assumption 99** (Feature-mediated reweighting). _The trained conditional distribution $\nu_{t,B}$ is absolutely continuous with respect to the initialization conditional $\mu_B$. Its density ratio is the within-band reweighting induced by training:_ ^ass-f-reweighting

$$
R_{t,B}(Q)
        :=
        \frac{\,\mathrm{d}\nu_{t,B}}{\,\mathrm{d}\mu_B}(Q).
$$

_We assume that this reweighting depends on $Q$ only through the training-visible features $F_{t,B}(Q)$. That is, there exists a nonnegative function_

$$
w_{t,B}:\Phi_{t,B}\to[0,\infty)
$$

_such that_

$$
R_{t,B}(Q)
        =
        \frac{w_{t,B}(F_{t,B}(Q))}
        {\mathbb{E}_{\mu_B}[w_{t,B}(F_{t,B})]}.
$$

_Here $w_{t,B}(\phi)$ is the relative weight that training assigns to Predictors in band $B$ with feature value $\phi$, and the denominator only normalizes the density to integrate to one._

_Reqs. [[#^req-group-consequence-invariance|65]] and [[#^req-no-explicit-consequence-signal|36]] rule out reweighting that directly distinguishes Predictors only by prior-equivalent future consequences. The present assumption is the additional claim that the remaining within-band reweighting is mediated by the specified training-visible features._

**Definition 100** (Feature-localization exponent). ^def-kb

$$
K_B(t)\;:=\;\log\mathop{\mathrm{ess\,sup}}_{\phi\in\Phi_{t,B}}
\frac{\mu_B(\mathcal A_{H,A_{\rm safe}}\mid F_{t,B}=\phi)}{\mu_B(\mathcal A_{H,A_{\rm safe}})}.
$$

Equivalently, $e^{K_B(t)}$ is the largest multiplicative increase in $\mu_B(\mathcal A_{H,A_{\rm safe}})$ obtainable by conditioning on a training-visible feature value. Consequence-invariant training does not imply $K_B(t)=0$: the latter would require independence of $\mathbf{1}_{\mathcal A_{H,A_{\rm safe}}}$ and $F_{t,B}$ under $\mu_B$. Rather, $K_B(t)$ is an information-limited feature-localization term. Because training carries no direct consequence-dependent signal (Req. [[#^req-no-explicit-consequence-signal|36]]), the features $F_{t,B}$ include no direct label saying that a Predictor lies in $\mathcal A_{H,A_{\rm safe}}$; any increase in $K_B(t)$ must come from accidental correlations between dangerousness and the gradients, residuals, curvature, optimizer state, or other features actually available to training.

**Proposition 101** (Feature-localization bound). _Under Assumption [[#^ass-f-reweighting|99]], $\nu_{t,B}(\mathcal A_{H,A_{\rm safe}})\le e^{K_B(t)}\,\mu_B(\mathcal A_{H,A_{\rm safe}})$._ ^prop-ci-bound

_Proof._ $\nu_{t,B}(\mathcal A_{H,A_{\rm safe}})=\mathbb{E}_{\mu_B}[w_{t,B}(F_{t,B})\,\mu_B(\mathcal A_{H,A_{\rm safe}}\mid F_{t,B})]/\mathbb{E}_{\mu_B}[w_{t,B}(F_{t,B})]\le e^{K_B(t)}\,\mu_B(\mathcal A_{H,A_{\rm safe}})$ by Def. [[#^def-kb|100]]. ◻

### Combined bound ^combined-bound

The theorem below is sharper than the uniform product $C_{\rm bad}R_{\rm shell}$ used in the main theorem, because it does not combine the worst dangerous fraction and the worst enrichment from different bands.

**Theorem 102** (Within-band sparsity and consequence-invariance bound). _Under Def. [[#^def-harm-coord|94]], Assumption [[#^ass-angular-ld|95]], consequence-invariant training (Req. [[#^req-no-explicit-consequence-signal|36]]), and Assumption [[#^ass-f-reweighting|99]],_ ^thm-geom-ci-bound

$$
\nu_{t,B}(\mathcal A_{H,A_{\rm safe}})
\;\le\;
\exp\!\left[
\,\underbrace{K_B(t)}_{\textnormal{residual feature localization}}
+\underbrace{K_B^\mu}_{\textnormal{initialization distortion}}
+\underbrace{\log N_H(B)}_{\textnormal{harm-pattern multiplicity}}
-\underbrace{d_B\Psi_B}_{\textnormal{within-band sparsity}}\,
\right]
$$

_Proof._ The within-band training enrichment $\nu_{t,B}(\mathcal A_{H,A_{\rm safe}})/\mu_B(\mathcal A_{H,A_{\rm safe}})\le e^{K_B(t)}$ is Prop. [[#^prop-ci-bound|101]]. The initialization-level dangerous-mass bound on $\mu_B(\mathcal A_{H,A_{\rm safe}})$ is Prop. [[#^prop-geom-sparsity|98]]. Multiplying the two gives the displayed bound. ◻

Summing the previous theorem over bands gives a global bound.

**Corollary 103** (Implications for $C_{\rm bad}$ and the global mass bound). _Define the local within-band enrichment factor $C_{\mathrm{loc}}(t,B):=\nu_{t,B}(\mathcal A_{H,A_{\rm safe}})/\mu_B(\mathcal A_{H,A_{\rm safe}})$ when $\mu_B(\mathcal A_{H,A_{\rm safe}})>0$. Under the hypotheses of Thm. [[#^thm-geom-ci-bound|102]],_

$$
C_{\mathrm{loc}}(t,B)\le e^{K_B(t)},
\qquad
C_{\rm bad}(H,A_{\rm safe})\le\sup_{t,B}e^{K_B(t)},
$$

_and the global mass on the dangerous set satisfies_

$$
\nu_t(\mathcal A_{H,A_{\rm safe}})
\le
\sum_{B\in\mathcal B_\Delta}
\nu_t(J\in B)\,
\exp\!\left[
K_B(t)+K_B^\mu+\log N_H(B)-d_B\Psi_B
\right].
$$

:::

:::callout {title="Appendix" collapse="closed"}
## Additional Plausibility Arguments ^additional-plausibility-arguments

In this appendix, we address two broad objections to our informal accuracy and safety arguments that don’t neatly correspond to the components outlined, and present two plausibility arguments regarding our assumptions.

### Capability without goal-directedness ^capability-without-goal-directedness

Even granting the premises of our safety and accuracy argument, one might think that competitive AI systems must be active—they would have to run experiments, gather information, ask targeted questions, and adapt online. One might be particularly worried about tool use (e.g., in the form of querying databases, running simulations, calling external APIs, or executing code), which is often implemented via planning-like loops. This might seem inherently agentic, and, if it isn’t, one may worry that any non-agentic system would be outcompeted.

**Reply.** The SAI framework separates _who acts_ from _which component is required to remain honest and non-agentic_. Agency can be placed in explicit, audited Scaffold code or external human processes while the Predictor remains consequence-invariant, so the System’s goals and actions are explicit rather than hidden in learned weights. A non-agentic Predictor $Q$ does not prevent the overall System from gathering information via search, database lookups, or other operations, orchestrated by the Scaffold under explicit, audited criteria.

Tool use is permissible only when it reduces approximation error on the current query, enters the Predictor solely as conditioning information, and does not train the Predictor to steer the world through its calls. Newly imported documents must first pass through contextualization before entering the Predictor’s input representation. Since $D_n$ contains records of past tool use, $Q$ can learn to anticipate tool outcomes as part of its world model, and any learned component selecting tool calls should define “success” as improving $J$ rather than achieving downstream effects.

Designing an SAI agent with tool use or full agentic capabilities lies beyond the present paper’s scope. One caveat is structural: training the Predictor itself with on-policy interaction and downstream feedback leaves the setting analyzed here and reintroduces the consequence-dependent selection pressure that the SAI design aims to exclude.

### Intractable Priors and Finite Data ^intractable-priors-and-finite

Exact Bayesian inference is typically intractable; the data are finite, shifting, and sometimes adversarially curated. Why should we trust an approximate-posterior system?

_**Reply.**_ As is standard in learning theory, the accuracy guarantees we provide are explicitly asymptotic—“with enough data and computation”—and scale with available resources. The Explainer reduces approximation error at inference time through Monte-Carlo averaging (Def. [[#^def-explainer|45]]), and Claim [[#^claim-good-generalization-to-unobservables|60]] shows that approximate posterior estimates support confidence-interval decisions with a margin proportional to the approximation error. Guardrail false negatives are controlled by user-specified risk thresholds $\alpha$ together with conservative margins accounting for approximation error; in safety-critical regimes, abstention should be preferred when uncertainty is large.

### Neutrality of the Prior and Safety Arguments ^neutrality-of-the-prior

Remark [[#^remark-prior-neutrality|9]] earlier discussed the neutrality of the prior. The prior’s neutrality also helps us understand why the target is not a malicious agent: conditioning gives $P_n$ no objective over its own deployed outputs (deployment enters only as intervened variables, Req. [[#^req-predictions-as-interventions|28]]), so $P_n$ may contain latent models of malicious agents without being one. Were such an explanation to dominate the posterior over latent causal models, it would be detectable by querying $Q$’s explanations for the data, and conservative besides: a posterior that genuinely models a malicious agent and fits its effects assigns that agent’s harms high probability, raising the deployment risk of the honest posterior toward withholding. The residual worry—a malicious process hiding in the weights that yields a plausible explanation yet emits coordinated false negatives at run time—is then not a property of $P_n$ but a deviation of $Q$ from $P_n$ on safety-critical outputs. This cannot route through the auditable explanatory latents or a coherence-scored System 2 argument (Sec. [[#^the-informal-argument-and|2]]). It would be represented as a deviation penalized by $J$ whose dangerous coordinated deviations from $P_n$ are assessed by the per-band sparsity and enrichment analysis.

### Safety and the Semantic Anchoring of Factual Latents ^safety-and-the-semantic

Consider semantic anchoring in the context of our safety argument (Remark [[#^rem-semantic-anchoring|49]]). Even if we were to grant residual semantic drift, only _coordinated drift_ toward $H$ is dangerous. Such coordination is a structured, sparse pattern whose within-band frequency is captured by $R_{\rm shell}$; consequence-invariant training brings no direct signal selecting it. When anchoring is weak, semantic coverage (Def. [[#^def-correct-semantics|47]]) requires the residual interpretive ambiguity to be represented as posterior uncertainty. For safety-relevant queries, such uncertainty should make the Guardrail more conservative: a covered hazardous reading, including a hidden-agentic interpretation when supported by the evidence, contributes to the residual deployment risk rather than being silently discarded in favor of a benign interpretation. The same applies to agentic latent explanations: if the evidence supports a hidden strategic actor, honesty requires representing that uncertainty, and safety requires letting it contribute to the harm estimate rather than hiding it behind a benign explanation. This is the semantic analog of epistemic caution (Def. [[#^def-epistemic-caution|44]]).

Beyond this per-query level, the safety theorems are robust to isolated semantic mistakes in the same sense that they are robust to isolated prediction mistakes: what matters is whether the mistakes coordinate to keep a harmful trajectory viable. A systematic semantic collapse aligned with $H$ would be dangerous and lies in $\mathcal A_{H,A_{\rm safe}}$, but it must then be rare within the relevant loss bands and not be preferentially enriched by training. Staying mutually coherent while steering toward $H$ would generally be expected to conflict with paraphrase, entailment, and contradiction constraints that the objective penalizes. Consequence-invariant training supplies no optimization channel—direct or indirect—that rewards those semantic mistakes for the sake of letting $H$ pass the Guardrail. Any such alignment would therefore have to arise through residual accidental correlation or inadequate semantic coverage rather than through any consequence-seeking pressure.
:::

[^note-1]: This supports threshold and interval decisions, such as guardrail risk checks, using $Q(y \mid x)$ in place of $P_n(y \mid x)$, with conservative estimated margins being chosen in terms of approximation error.
[^note-2]: The latter views are called ‘non-cognitivist’ views in the philosophical literature, and are themselves controversial (see (Bourget and Chalmers 2023)).
[^note-formalism-scope]: Given the expressivity of our model, we expect to ultimately need a formalism that better handles constraints and abstraction (Beckers and Halpern 2019; Blom et al. 2019; Richardson et al. 2025; Geiger et al. 2025), but this is presently out of scope.
[^note-competing-theories]: See Bengio et al. (2025b) for a longer discussion of how multiple scientific theories with overlapping claims (such as physics and chemistry) can coexist in the same causal model $W$. The combination of insufficient data and computational limitations means that there will be multiple theories that remain competitive (like physics and chemistry), which motivates the SAI objective of approximating the Bayesian posterior under bounded compute.
[^note-5]: Statelessness means that $Q$’s output depends only on the current query $(x,y)$ and not on any internal record of queries previously evaluated during deployment; in particular, $Q$ maintains no writable memory that persists across query evaluations.
[^cite-6]: The Flat Earth Society Wiki, “Flat Earth – Frequently Asked Questions.” [https://wiki.tfes.org/Flat\_Earth\_-\_Frequently\_Asked\_Questions](https://wiki.tfes.org/Flat_Earth_-_Frequently_Asked_Questions)
[^cite-mechanism-sharing]: See Bengio et al. (2025b) for further discussion and Deleu et al. (2022) for an early implementation.
[^note-8]: Sec. [[#^safety-and-the-semantic|9.4]] discusses the connection between semantic anchoring and our later safety arguments.
[^note-9]: Observe that if $Q$ were deterministic, this would technically be an equivariance.
[^note-10]: The uniform prior on $\widetilde Q$ is what makes the bit-flip below a prior-preserving bijection; the example’s symmetry, and hence its conclusion, is relative to this modeling choice. Note: if the prior on $\widetilde Q$ had been a point mass on a particular fixed point and its unique consistent extension $Q$ to all variables, then we would have $Q = P^* = P_0 = P_n$, which would be $\cal C$\-invariant by Prop. [[#^prop-pn-consequence-invariant|64]]. This shows that we cannot hope for a definition of invariance satisfied by $P_n$ that is not sensitive to the prior.
[^note-11]: This requirement is intended as sufficient for the present paper’s analysis; outlining necessary requirements for all acceptable scaffolds (alongside richer and more capable forms of agency built on top of the SAI Predictor) is left for future work.
