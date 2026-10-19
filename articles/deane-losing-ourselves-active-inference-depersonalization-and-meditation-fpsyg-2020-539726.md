---
title: "Losing Ourselves: Active Inference, Depersonalization, and Meditation"
author:
  - "George Deane"
  - "Mark Miller"
  - "Sam Wilkinson"
source_url: "https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2020.539726/full"
published: 2020-10-29
created: 2026-10-19
accessed: 2026-10-19
llm-review:
  date: 2026-10-19
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-19
    kind: "live"
description: "Disruptions in the ordinary sense of selfhood underpin both pathological and"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## HYPOTHESIS AND THEORY article ^hypothesis-and-theory-article

Sec. Theoretical and Philosophical Psychology

Volume 11 - 2020 | [https://doi.org/10.3389/fpsyg.2020.539726](https://doi.org/10.3389/fpsyg.2020.539726)

## Losing Ourselves: Active Inference, Depersonalization, and Meditation ^losing-ourselves-active-inference

-   1\. Department of Philosophy, University of Edinburgh, Edinburgh, United Kingdom
    
-   2\. Department of Informatics, University of Sussex, Brighton, United Kingdom
    
-   3\. Department of Sociology, Philosophy and Anthropology, University of Exeter, Exeter, United Kingdom
    

## Abstract ^abstract

Disruptions in the ordinary sense of selfhood underpin both pathological and “enlightened” states of consciousness. People suffering from depersonalization can experience the loss of a sense of self as devastating, often accompanied by intense feelings of alienation, fear, and hopelessness. However, for meditative contemplatives from various traditions, “selfless” experiences are highly sought after, being associated with enduring peace and joy. Little is understood about how these contrasting dysphoric and euphoric experiences should be conceptualized. In this paper, we propose a unified account of these selfless experiences within the active inference framework. Building on our recent active inference research, we propose an account of the experiences of selfhood as emerging from a temporally deep generative model. We go on to develop a view of the self as playing a central role in structuring ordinary experience by “tuning” agents to the counterfactually rich possibilities for action. Finally, we explore how depersonalization may result from an inferred loss of allostatic control and contrast this phenomenology with selfless experiences reported by meditation practitioners. We will show how, by beginning with a conception of self-modeling within an active inference framework, we have available to us a new way of conceptualizing the striking experiential similarities and important differences between these selfless experiences within a unifying theoretical framework. We will explore the implications for understanding and treating dissociative disorders, as well as elucidate both the therapeutic potential, and possible dangers, of meditation.

## Introduction ^introduction

In daily life, we take for granted the existence of a self: we feel that we are possessors of certain qualities, the experiencers of certain sensations, that we are different and distinct from one another, and that we endure from day to day. And yet, these assumptions have long been the focus of skepticism within both Western and Eastern philosophical traditions. Thinkers from various disciplines (e.g., from philosophy of mind, cognitive science, phenomenology, and Buddhist philosophy) are beginning to collaborate on various topics revolving around self and subjectivity. One lens through which philosophers and cognitive scientists have been recently exploring the self is through cases where subjects report a loss, or diminishment, of their sense of self. These reports occur most prominently in the context of psychiatric disorders such as depersonalization (e.g.,;; ), meditation (e.g.,; ), and psychedelic drugs (e.g.,; ). The active inference framework—a popular approach to modeling action and perception that uses principles of variational Bayesian inference ()—is particularly promising for understanding these phenomena.

Our aim in this paper is to provide an updated account of selfless experience within the active inference framework [^note-1]. By selfless experience, here, we mean the diminished sense of self that is reported in a wide variety of cases including depersonalization and meditative insight. Active inference and predictive processing have already been used to provide accounts of depersonalization in psychiatric contexts (; ), and although we find these accounts promising, we seek to build on them in important ways. In particular, we differ from existing accounts in taking affective valence and control to be central to the sense of self. Building on existing accounts of self-modeling within an active inference framework (;; ), our account casts the self-model in terms of an allostatic control model (ACM; ), which we unpack in terms of “agentive control” and “motivational” components. The central thesis of this view is that the self is understood as an inference about endogenous causes of self-evidencing outcomes. In simple terms, this could be understood as the system modeling what it _wants_ (motivations) and what it _can do_ (abilities). However, we do not simply adopt the ACM for its own sake—there are concrete explanatory payoffs. In particular, we are better able to account for the wide range of selfless experiences under a single unifying framework. Selfless experiences come in a variety of flavors, ranging from the dysphoric and dysfunctional experiences associated with depersonalization to the euphoric and potentially superfunctional states sought after by meditators. Our explanation of this difference is, as we will see, an intrinsic part of our account of the emergence of these phenomena themselves.

An important addition to this literature that we will make is a reinterpretation of the role that affect plays in these processes. We will argue that the sense of self arises from the system’s evaluation of its own performance, or predictive control, of its own adaptive behaviors. As we will see, the tracking of our performance, and the allocation of resources (i.e., setting of precision), is being done in part by affective systems. That is, we quite literally feel how well adapted we are to a situation, and those feelings move us in ways that are intended to improve that fit. This has the consequence that our sense of being a self and affect are mechanistically intertwined. This updated theoretical account of selfhood then allows us to propose a more unified framework for understanding various alterations in selfhood and affectivity.

We proceed as follows: In _From the Free Energy Principle to Hierarchical Predictive Processing_, we give an overview of the free energy principle and hierarchical predictive processing. In _A Control-Theoretic Perspective_, we position these frameworks within a control theoretic perspective and show how allostasis can be formalized in terms of active inference. In _Affect in Deep Self-Models_, we build on these ideas to present an account of self-modeling in terms of allostatic control. In _Active Inference Accounts of Depersonalization_ and _ACM Account of Meditative Selflessness_, we apply this model of the self to address depersonalization and selfless experiences attained through meditation, respectively. We wrap up and conclude by comparing and contrasting these two dysphoric and euphoric selfless experiences.

## From the Free Energy Principle to Hierarchical Predictive Processing ^from-the-free-energy

The free energy principle (FEP; ) is an ambitious unifying and overarching theory of life, according to which biological systems naturally strive to minimize free energy.

The FEP starts from the observation of existence (; ) and seeks to understand how organisms maintain their existence by “tuning” to their environmental niche, where the quantity of free energy is understood as a measure of the disattunement (which is equivalent to model “uncertainty”) between the agent and environment (). Crucially, in order to exist and reproduce, agents must stay within conditions that are conducive to continued existence—such as avoiding an unacceptably high body temperature. Of course, this is _phenotype specific_ —the conditions that make continued existence viable vary across species. Organisms must minimize free energy, which is equivalent to maximizing the evidence of their model and so their own existence (, ). Maximizing model evidence in this way is called “self-evidencing” ().

In animals like us (and many others), it has been proposed that free energy is minimized, at least in large part, by hierarchical predictive processing in the brain and central nervous system (;, ). What the brain has to do, on such a view, is minimize prediction error (free energy) as efficiently as possible. This requires it to come up with an overall hypothesis or model about what is going on in the world. This hierarchical model generates predictions, and if it is inaccurate, it generates _prediction error_ and updates predictions accordingly.

A major challenge in model selection arises because the world is a noisy and ambiguous place. Thus, there exists, at any given time, more than one model that fits the incoming sensory signal. This is where the notion of _prior probability_, often shortened simply to _prior_, comes in (and with it, the Bayesian element of the framework). This is the background probability of the model independently of the evidence. For example, (adapting an example from ) before I hear my downstairs front window creak open, there is a background probability concerning the likelihood that I might be burgled. Whether I live in a high- or low-crime neighborhood will influence the prior probability of the “that’s a burglar!” model in response to the sound of the creaking window (“the evidence”). Models are selected based on both fit with current evidence and their prior probability. This means that you can get trade-offs, for example, where a model with a relatively low fit has a sufficiently high prior probability to be selected. For example, in the case of the hollow mask illusion, the model with the best fit would be the (perceptually accurate) “hollow concave face” model, but the slightly lower fit “normal convex face” model has such a high prior probability that it is selected instead, giving rise to the illusion.

This captures what the brain has to do, namely, resolve ambiguity using priors (viz., in a Bayesian manner); however, it does not tell us how this is implemented physically in the brain. Put simply, the brain maximizes efficiency (minimizes free energy) by being proactive and anticipatory. In other words, the nervous system does not passively wait for inputs to come in. Rather, even at the earliest stages of sensory processing, inputs are greeted by a barrage of top–down prediction. This does not just save time; it also saves energy and bandwidth, since the parts of the incoming sensory signals that have already been accurately predicted do not need to be passed up the processing hierarchy. All that gets passed up is what is “newsworthy” (), namely, prediction error. Putting this all together, the nervous system tries to minimize prediction error by coming up with successful hierarchical predictive models that are chosen in a Bayesian manner (namely, based on fit and prior).

There are two more important tweaks to this picture. The first is to do with second-order prediction dynamics, namely, how the brain deals with statistical volatility. This requires introducing the notion of _precision_. In short, the world that we live in does not just have variability but also predictable levels of variability. As a result, our nervous systems learn over time that there are contexts where environmental information is high quality (trustworthy) and other contexts where it is not. For example, in good lighting, visual information is relatively high quality, whereas in poor lighting, it is relatively low. What an optimal system will do in response to this is have a way of setting second-order precision, namely, of appropriately varying the extent to which prediction error should be taken seriously (adjusted as a function of the likelihood of prediction error being accurate or simply noise). In high-quality informational contexts, it is expected that predictions will be good, and so prediction errors will be given relatively high weight (or gain). In low-quality contexts, prediction errors will be taken less seriously. This turning up and down of the gain on prediction error signaling is most commonly called _precision weighting_, and it plays a role far beyond the second-order dynamics that we used to introduce it. It is central to attention (), and to the bringing about of bodily movement, an issue to which we now turn.

The second tweak comes when we note that, for embodied creatures like ourselves, action is an ever-present part of our existence. The Bayesian picture just described makes it look like we are primarily in the business of updating our models to best fit inputs from the world. However, of course, there are two ways of responding to prediction error. You can, certainly, update the model to better fit the world, but you can also update the world to better fit the model. The former is known as _perceptual inferenc_ e, and the latter is known as _active inference_. It is with the latter that you get a PP account of action and basic motivation more generally. Active inference, on our view, is central to allostasis, a notion we introduce shortly.

## A Control-Theoretic Perspective ^a-control-theoretic-perspective

The foundations of active inference can be traced to control theory. The idea that a system maintains existence by resisting environmental disorder by acting to remain within a limited repertoire of _phenotype-congruent_ states is closely related to the notion of maintaining “essential variables” (), where an internal reference point (also known as a setpoint or goal signal) is compared to the current state and the system acts so as to restore conditions to the setpoint.

The principles of _control-oriented predictive regulation_ () are very similar.

Here, the brain applies the same inferential machinery of hierarchical predictive processing to infer and track key homeostatic variables, using prior expectations and afferent sensory information about the body coming “from within” (). In order to stay alive, organisms have to execute the right actions to bring about state transitions that bring bodily states into reasonable bounds (). The phylogenetically endowed high precision on expectations for staying within homeostatically viable states means that the organism acts to realize prior beliefs corresponding to the maintenance of essential variables (“goal priors”), for example, eating to restore a blood sugar concentration to expected levels. While goal priors originate in the maintenance of essential variables (e.g., steady temperature, blood sugar levels, etc.), over the course of ontogeny, an organism can acquire new goal priors that are predictive on longer timescales of being relevant for maintaining homeostasis—such as staying within a particular social milieu ().

Active inference, then, formalizes homeostasis through a control theoretic lens. Homeostasis from this perspective is maintained not only through autonomic reflexes (i.e., sweating to cool down) but also by _prospective control_. Such systems anticipate future dyshomeostatic conditions before they arise and proactively act to avoid them. This prospective control relates to both inferences about current and future bodily states contingent on certain actions (;; ). This process of anticipatory action, by which the brain regulates the needs of the body, is known as _allostasis_ (). Active inference formally articulates allostasis, such that agents _anticipate_ surprising outcomes before they arise and act in order to minimize uncertainty about potential future outcomes (;, [^cite-11]).

On the active inference formulation, the action selection process itself is cast as a problem of inference, where agents must infer the active sampling of the world that realizes prior preferences and minimizes uncertainty (). Action selection, then, depends on the use of a deep temporal model, where policies (sequences of actions) are selected based on prior expectations of the quantity of free energy that the agent expects itself to average over time (“expected free energy”) _given_ a particular policy or course of action (; ). Intuitively, some courses of action (such as riding in the train carriage) have lower expected free energy than others (such as riding on the roof). Crucially, this involves anticipating unfavorable or dyshomeostatic conditions before they arise and acting to minimize uncertainty about potential future outcomes (, ). On this account, higher levels of the cortical hierarchy, tracking regularities unfolding on longer timescales (), contextualize lower levels by anticipating the downstream consequences of action and selecting policies that minimize expected free energy according to these expectations (; ). For example, my longer-term goal of successfully catching the train includes expectations about what I need to do to get to the station on time, which in turn unpacks into subgoals such as getting in my car and lower-level action–prediction loops as I use the pedal, gearstick, and so on.

In order to minimize free energy over longer timescales, active inference requires balancing the _pragmatic_ and _epistemic_ value of different actions. The pragmatic (or instrumental) value of an action or action policy (a sequence of actions) refers to the probability of it resulting in sensory states that fulfill some prior preference or goal state, such as maintaining a viable body temperature. Epistemic value refers to the reduction in uncertainty or information gain expected under a given action or action policy (). Epistemic action allows organisms to increase an agent’s ability to reduce free energy by increasing their understanding of the predictable aspects of the environment. Information-seeking behavior such as novelty seeking and curiosity can be accounted for within this formulation in terms of epistemic action (;;;; ). Intrinsic motivation (and epistemic foraging) can be understood here in terms of uncertainty reduction (). Simulations of economic decision making and epistemic foraging behavior have been built based on this view that the probability of a policy is proportional to expected free energy (,, ). Active inference formulations of planning and navigation have been used to dissolve the “explore–exploit” dilemma, as the agent simply needs to act so as to minimize uncertainty (i.e., free energy; ). Agents engaging active inference do not just keep themselves in the states that are expected; rather, they anticipate in order to minimize uncertainty about potential future outcomes (;,, ).

Now that we have introduced the control-theoretic notion of allostasis, and how it is achieved via active inference, we next go on to develop our view of the sense of self.

## The Sense of Self as a Model of Allostatic Control ^the-sense-of-self

This section will argue that the self is best understood in terms of an _allostatic control model_ (ACM). Recently, a number of computational models of the minimal sense of self (namely, the self as implicitly present in everyday world-directed experience, rather than something more overt and explicit like the self-conception or narrative self) have been advanced in the active inference literature (;;; ). Common to these proposals is that the sense of self arises inferentially within a hierarchical generative model. Our central claim is that the inferential self-model arises from the system tracking its own self-evidencing capabilities (). The purpose of tracking these capacities is to infer confidence (precision) in potential action policies according to their expected free energy and thereby arbitrate between potential actions accordingly. Self-modeling of this kind, then, is fundamentally related to selecting allostatic or anticipatory actions, where the system preemptively infers and avoids unfavorable conditions before they arise. By casting the self-model in terms of allostatic control, we will connect our view in new ways to the prevalent theme in neuroscience about the rich relationship between affectivity and the self (;; ). This view can be understood formally in terms of a higher-level inference about “subjective fitness”—that is, a higher level of the generative model that scores the “fit” between the action model and the world (see for a formal treatment and computational model of this idea). Conceptually, our view of the sense of self can be decomposed into “agentive control” and “motivational” components. We will present these in turn.

### Agentive Control ^agentive-control

Recall that while perception involves updating the model to better predict the incoming sensory input, action changes the incoming sensory input to better fit the model. In selecting an action, then, the system implicitly infers itself as able to bring about the consequences of that action. A sense of agency, the sense of being the one in control of an action, naturally emerges here as part of model sampling ()—in selecting an action, the system implicitly infers itself as able to bring about the sensory consequences of the action. On this view, the sense of control—the expectation of being able to bring about certain consequences given certain actions—is _learned_ through past experiences of the system inferring its own agentive capacities.

This connects closely with preexisting accounts of the sense of agency, where the system infers its own agency based on the ability to predict the outcome of a given action (). Here, attribution to endogenous causes (self), as opposed to exogenous causes (world/other), occurs as the result of a “comparator model,” where the sensory consequences of an action are compared with the expected sensory consequences (). This allows the system to sculpt and improve motor control, as the discrepancy between the sensory consequences of an action are compared with the predicted (intended) outcomes. The system can then act to iteratively reduce this discrepancy and refine motor commands (; ).

Crucially for the current account, _control_ is _temporally deep_ (), such that the agent not only has predictions about the immediate consequences of actions but also of consequences extending into the future. The sensory consequences of a given action may be sensorially proximal (e.g., the immediate sensory consequences of hitting send on an email), or sensorially distal and abstract (e.g., the expectation that when you see that person they will know the information in the email). The system, then, must be able to track the outcomes of actions on multiple timescales. Within the generative model, lower and higher levels of the hierarchy track regularities unfolding at faster and slower timescales, respectively (). For an organism with a temporally deep generative model, this includes tracking its expected control of actions on short timescales (e.g., the expected sensory consequences of taking a step) and using these inferences to inform inferences about the state of control on temporally deep timescales (e.g., being able to walk a distance). On this view, the system models itself as an agent according to this hierarchically deep inference about its own endogenous control of sensation via its actions. In other words, I have a sense of what I can do based on past experience of acting in the world and come to expect myself as a controller over my future actions.

### Motivation ^motivation

The _motivational_ component of our view of the self-model is understood in terms of _goal priors_ and, as such, connects closely to views of selfhood grounded in interoception (;; ). This is because the system will be generally more concerned about controlling the “essential variables” (i.e., homeostatic set points like blood sugar levels) tracked by interoception than variables inferred through exteroception and proprioception, which are less likely to pertain directly to homeostasis (; ).

Creatures tracking longer timescales can augment this with _deep goal hierarchies_ (see ), where fulfillment of longer-term goals can be traded off with fulfillment of shorter-term goals. On this view, low-level maintenance of “essential variables” are phylogenetically endowed expectations that, due to an “ _a priori_ hyperprecision of visceral channels” (, p. 7), the system must act to fulfill, rather than simply updating via perceptual inference. One example would be moving to the shade under a tree to maintain viable body temperature. Divergence from these fundamental, phenotype-congruent low-level prior expectations tunes attention and amplification of sensory signals. This manifests itself to the system as, for example, the feeling of hunger (interoceptive prediction error) or a violation of the “healthy body condition” prior in the case of pain (). These interoceptive changes tune the organism to the appropriate action opportunities in the given context, such as finding food to resolve interoceptive prediction errors or removing the source of pain. Crucially, pain is tuned relative to expectations given the context (). In the case of an approaching bear, the prospective inference about imminent catastrophic prediction error of being eaten trumps the proximal pain of a twisted ankle, and the selected policy is running away. Put another way, hierarchically deep contextualization of interoceptive signals tunes an organism to appropriate actions and engagements with the environment () and assigns appropriate precision to priors and ascending prediction errors. For low-level drives and motivations, this is intuitive—the hungry organism is tuned to capitalize on eating opportunities present in the environment. Precision on goals tracking different timescales are continually being traded off between levels—such as refraining from eating chocolate cake in the present for the sake of a longer-term goal of sticking to a diet ().

The sense of self, then, emerges as the result of a hierarchically deep inference about the system’s control of its own self-evidencing outcomes. In the generative model, this means that the sense of self can be understood in terms of a higher-level inference about the “fit” between the current action model and the world. By fit here we mean how well or poorly one is doing at reducing error over time relative to expectations. As we will see in the next section, a key implication of this picture is that self-modeling is fundamentally affective, where affective changes in the body tracks how well the organism is doing at fulfilling its own goal priors (“subjective fitness;”;; ). An upshot of this picture is that self-modeling, and indeed the feeling of being a self, is connected to affect in ways previously underappreciated in the literature, as we will explore next.

### Affect in Deep Self-Models ^affect-in-deep-self-models

The previous section argued for a view of self-modeling as a higher-level inference about the system’s allostatic control. In our view, as we will now see, minimal self-modeling and affect are coconstitutive, such that affect can be understood as an inference about the performance of the action model in bringing about self-evidencing outcomes. This section unpacks how inference about allostatic control, manifesting affectively, is central to the allocation of precision.

In tracking the performance or “fitness” of the model over time, the system becomes sensitive to _the rate of error reduction._ In selecting a policy, the system has prior expectations of the rate at which error is likely to be reduced over time. The system can then evaluate whether its performance at reducing error is better or worse relative to its prior expectations. We can think of each agent’s performance in reducing error then in terms of a slope that plots the various speeds that prediction errors are being accommodated relative to their expectations. Changes in the rate at which error is reduced (referred to as “error dynamics”) turns out to be an important source of information for a predictive organism, as it reflects the efficiency, and so the quality, of its action model performance over time. As such, error dynamics play an important role in tuning precision estimations—increasing or decreasing our beliefs in the reliability of the model generating the policy (; ). If precision is set based on estimations of how likely some action is to lead to the expected result, then the efficiency—the rate at which error is reduced—of those actions to reduce error should be taken into consideration. Greater than expected error for a given policy is evidence that the system should downregulate precision on the action model. Sensitivity to error dynamics increases our capacity to reduce prediction error over longer timescales, as it affords a means to toggle confidence levels on the action model according to the volatility of the environment.

The phenomenological manifestation of this (subpersonal) sensitivity to error reduction rates over time is affect. There is a growing literature that supports the view that affective changes not only track changes in immediate divergences from the homeostatic ideal, as was the focus of earlier predictive accounts of interoception (see ), but also tracks the rate of change in error management over time (;; ). Valenced bodily feelings (i.e., positive and negative hedonic tone) are, in part, a reflection of how well or poorly we are reducing error over time relative to expectations. When error is being reduced slower than expected, and the organism is becoming increasingly disattuned to its environment, this change is marked by feelings of frustration and disappointment. The negatively valenced bodily feelings provide the organism with feedback about the reliability of the selected action policies, indicating a need to downregulate precision on those policies. In contrast, when error is being managed at a better than expected rate, the organism is gripping the scene well, the bodily feedback are positive feelings of hope and satisfaction, and precision is upregulated. It is intuitive that persistently worse than expected rates of error reduction on a given goal prior act as a disincentive to pursue that goal and motivate the system to select a more achievable goal, and doing well is motivating to continue to realize a certain goal. Precision does not just concern the organism here and now and its momentary state of uncertainty but is instead helping it to continuously improve working toward managing uncertainty over time. Importantly, positive and negative feelings alter precision relative to the rate at which we have come to expect errors to be resolved.

Affective valence here is being reimagined within the active inference framework as a domain general controller that tracks and assigns precision relative to changes in our expected rates of error reduction (that is, expected reductions in free energy;; ). Inference about how well the system is self-evidencing as a whole is tracking a long-term dimension of the self, which is necessarily more invariant and abstract in virtue of tracking a longer timescale, showing less variability than “lower” aspects of the self-model that are more amenable to changing across contexts. Negative and positive feelings then track lesser than expected and greater than expected allostatic control, respectively. This higher-order inference about the system’s confidence in its own action model, used to modulate precision on expected free energy (), is a candidate computational correlate for the sense of self—the feeling of being an agent.

This account of self-modeling as mechanistically intertwined with affectivity is, at present, a theoretical proposal. However, recent work (most notably ) provides proof of principle of how this theoretical framework can be modeled computationally. This is a very promising groundwork for future work in computational modeling that is able to tie both phenomenology and behavior to underlying computational mechanisms. An important consequence of highlighting this underappreciated link between affect and self-modeling in active inference is that it provides a bridge between these computational frameworks and the phenomenology of being a self (for another account of this, see ). Bodily feelings here represent a prereflective source of information about how well an agent is doing in their predictive engagements. These feelings give them a sense of what they can do, of what is possible, and what is not possible (the sense of “I can”). We have a feel for what is possible in the world based on what we can do in the particular situation we find ourselves within. Above, we characterized bodily feelings as driving policy selection. The result is that one quite literally feels drawn to relevant action possibilities. These bodily feelings track which possibilities are relevant to an agent and move us to improve [^note-2]. The result is an ongoing dynamic dialectic between agent and environment all circling around affectivity.

While the importance of this ongoing tension between bodily feeling and environmental affordances is easily overlooked when it is functioning well, alterations in this quality can have devastating effects on how one experiences oneself and one’s world. With the addition of these more recent computational models of valence as setting precision relative to changes in control, we have now for the first time at our disposal the means to provide the fullest expression of an active inference account of the sense of self. In the rest of this paper, we will use this more fully realized view of the self to propose a new unified account of the alterations in self-experience native to depersonalization and meditative insight.

## Active Inference Accounts of Depersonalization ^active-inference-accounts-of

Depersonalization disorder (DPD) is still a relatively neglected dissociative disorder. Dissociative disorders are a class of mental illness characterized by disruptions in perception, consciousness, and/or identity. These disruptions can cause various symptoms that are problematic for a person’s life including social relationships and work life. Recently, however, research into the phenomenon of depersonalization more generally is increasing in part due to the piqued interest of philosophers and cognitive scientists interested in the nature and function of the self. Depersonalization experiences potentially provide researchers with important glimpses into the neuropsychological mechanisms and functional profiles of our ordinary experiences of being a self (see Metzinger on philosophy and dissociative disorders). A hallmark of depersonalization is a disturbance in subjective experience. This commonly includes a sense of detachment or alienation toward themselves, their bodies, and their environments. While specific disturbances in self-related experiences (depersonalization) and their experience of the environment (derealization) can come apart, they commonly co-occur; we will have more to say about his co-occurrence shortly ().

London-based writer Gracie Lofthouse writes on her own experience of depersonalization in a recent article:

> _“The first time I can remember feeling like I didn’t exist, I was 15. I was sitting on a train and all of a sudden I felt like I’d been dropped into someone else’s body. My memories, experiences, and feelings—the things that make up my intrinsic sense of “me-ness”—projected across my mind like phantasmagoria, but I felt like they belonged to someone else. Like I was experiencing life in the third person” ()._

Most people have some experience of this sort of state. If you have not, it can be difficult to understand, and indeed, sufferers of depersonalization commonly report difficulties in expressing their experiences (, p. 80). Depersonalization symptoms can last for moments, or several years, and commonly accompany major depression, anxiety disorders, substance addiction, brain injury and disease, and emotional trauma. An increasingly popular view of depersonalization is that it may act like an “airbag” in traumatic situations: when fight or flight are unable to remove an overwhelming, emotionally painful, experience, then the affective system may have its volume turned down as a direct means of reducing the suffering. The result of this reduction is what Medford calls it “desomaticion” or “deaffectation” (;;; ) and is potentially the cause of the characteristically strange phenomenon of losing something important about the self and the world (see, e.g.,;;;;; ).

In our view, predictive processing has offered some of the most promising avenues for understanding depersonalization. Our main aim here is to build on these and to improve on them based on more recent developments in the literature on active inference and the view of the self-model outlined in the previous section. The main explanatory payoffs that we can see are not only that we can better explain depersonalization and related symptoms but that we are also well-placed to explain why some instances of loss of self can have a positive valence, while others do not. Ultimately, superficial similarities in what are described as experiences of “loss of self” mask deep underlying differences.

### Existing Predictive Processing Accounts of Depersonalization ^existing-predictive-processing-accounts

were perhaps the first to apply predictive processing to depersonalization, and since then, has also provided an account. build their account on the central notion of “conscious presence.” Since “presence” involves both a sense of oneself as present in the world, and the world as present to us, it casts depersonalization and derealization as two sides of the same coin. To briefly summarize their account, they build on work in schizophrenia research on the loss of the sense of agency (e.g.,; ) according to which this arises from imprecise predictions about the sensory consequences of actions (see also _Agentive Control_, above). This account gets adapted to account for presence. According to,

> _“presence is the result of successful suppression by top-down predictions of informative interoceptive signals evoked (directly) by autonomic control signals and (indirectly) by bodily responses to afferent sensory signals. According to the model, disorders of presence (as in DPD) follow from pathologically imprecise interoceptive predictive signals.” (p. 2)_

Our account builds on this in a number of respects. First, this account is based on a view of emotion as interoceptive inference. So is ours, in a sense, but what Seth and colleagues mean is emotion as interoceptive _perceptual_ inference. In other words, as they explicitly state (p. 1), they are fleshing out the James–Lange theory of emotion () according to which emotion is perception of bodily (specifically visceral) change. Given a PP gloss, whereas perception is the result of model selection for minimizing prediction error from sense perception, emotion is simply model selection for minimizing prediction error from interoception. This is perceptual inference since the model has to accommodate the input. Building on our recent work (; ), we, in contrast, view emotion, and affect more generally, as involving _active_ inference, too. In terms of ACM, it is a central part of allostasis. This brings us to another crucial difference with our view. The view of emotion as interoceptive model building tells us nothing about _valence_. And yet, emotion has valence: it tends to be either positive or negative (and to greater or lesser degrees). In contrast, we tie positive valence to allostatic control (and negative valence to lack of such control). This means, crucially, given what we say later, that valence falls naturally out of our account, both of affect in general but also of self-loss, both negative and positive, in particular.

Unlike Seth and colleagues’ account, Gerrans’ account does not take presence as a basic notion out of which both self and self-loss emerge for free. Instead, Gerrans appeals to the notion of a “self-model” or, perhaps more accurately, the idea that the self-features as part of an overall predictive model that determines conscious experience. Gerrans’ main point is that our ordinary experience of the world, and ourselves, is generated by a constant integration of cognitive, perceptual, and affective signals. Building on his earlier work with Chris Letheby (), the self here is part of a predictive model, one that works to explain away the affective changes that occur as the organism engages with its environment. When affective signals go missing, the predictive system needs to explain the absence.

Gerrans’ approach to explaining depersonalization focuses on the role of affect in the generation of our felt sense of presence (). Like, Gerrans concludes that when predictions about ordinary affective reactions are not fulfilled, the system generates the sense of the agent being no longer present in the experience. In short, Gerrans builds on Seth et al. but adds the self-more explicitly into the model. To the extent that Gerrans’ account is similar to Seth and colleagues’ account, it shares many of the same differences with our own. Nevertheless, we like the embellishment of adding the self as a feature of the predictive model. In a sense, we would agree with Gerrans that presence emerges from a basic notion of self rather than the other way around.

What both of these existing accounts have in common, with respect to depersonalization, is the focus on affective numbing based on alterations (viz., inaccuracies) to interoceptive predictive processing. We do not disagree. However, what we add to the picture is the idea that affect carries inbuilt valence, involves active inference (allostasis), and, crucially, plays a role in setting precision weighting. This has the welcome side effect of allowing us to neatly explain other features of depersonalization beyond simply affective numbing. It also generates an account of depersonalization according to which it is inherently a negative experience (rather than something that needs to be appraised as such after the fact). These two other accounts tell us why there might be a loss of sense of self but not why that is negative. Given the existence of extremely positive experiences of self-loss (“enlightened” states), the negativity of the experience is not something that should be taken for granted. Our explanation of this large difference in valence is that superficial similarities are masking quite radical differences in what is going on in the two cases.

In the next section, we will propose that ACM can do a better job at accounting for depersonalization experiences than previous PP accounts. In particular, we will develop a view of depersonalization as a loss of allostatic control.

### ACM Account of Depersonalization ^acm-account-of-depersonalization

Recall that the ACM casts the sense of self as underpinned by an inference about the system’s endogenous control of self-evidencing outcomes. The highest levels of the self-model are also the most enduring, due to their being the most invariant across contexts. These higher levels that track how well we are able to control our interactions with the environment (i.e., allostatic control), more generally, act as hyper-priors informing more domain general precision estimations. The result of the sense of self being hierarchically deep in this way is that a temporary loss of control within a particular context may not necessarily reduce a more general sense of control or a sense of control across contexts. In other words, someone can fail to play the violin well without losing confidence in their ability to live a good life.

This inference about allostatic control—manifesting as affective valence—plays a role in setting precision relative to changes in how well or poorly we are doing at reducing error given the context. Sensitivity to unexpected increases in prediction error rates—manifesting here phenomenologically as negative valence—acts as a disincentive to continue operating in a particular context (; ). For example, when learning an instrument, if a certain song is too complex given our skill level, the feelings of frustration that arise could motivate task switching perhaps to a simpler song or to developing some of the skills necessary to eventually play the more complex tune. Task switching here offers a way for the system to get back to reducing error at a better rate.

However, what happens when the system cannot resolve the negative affect through task switching? In other words, how would such a system behave if unexpected error continued to rise regardless of perceptual updates and behavioral interventions? For example, in active inference terms, trauma could be understood as a massive influx of prediction error causing the system to drastically lower confidence (precision) in its action models (see ). In the case of physical trauma, the body’s integrity, which is highly expected, is seriously disrupted or damaged. The system in this situation is unable to reduce errors either by updating their models (perceptual inference) or acting in a way that will bring their expectations back in line with the current situation (active inference). This disparity between expected control of prediction error and the error-riddled reality produces huge amounts of negative affect, which, as we have discussed above, reduces certainty on the currently selected policy as a means of tuning the agent to better predictive opportunities.

If an external situation continues to create error (i.e., severe pain) over an extended period of time, and the agent cannot control the situation through switching domain or context (that would otherwise be controllable), the resulting drop in precision on expected free energy is going to be such that consequent transitions between higher level affective states will be forced into the same fearful state continuously. The ascending message from the negative “affective charge” () will override the descending message from higher level policies (i.e., our ability to control error by task switching also fails to resolve the issue, and so we lose confidence domain general control). That means that you have exactly the same effect at the next level, whereby the desired state (positive affect) is never reached despite trying to control it, leading to a drop in the precision on expected free energy at that level, and so on upwards. Crucially though, for this to happen, the person would have to never give up the resistance to the fear/pain, i.e., maintain a high precision on that goal state (i.e., the phylogenetically expectation to have a healthy, well-functioning body). In time, the “hopeless” situation might eventually create a learned belief that, no matter what they do, they will always be in a negative valence state (i.e., valence state transitions are not conditioned by policies and are stable in “negative”). It would basically be a perfect storm for a gridlock situation where you have a strong preference against the negative state but then you also know that you cannot escape it no matter what you do. The only option is to dissolve the process that is creating the negative affect in the first place since nothing else can work. The consequence would be an unraveling of the process by which we form affective states (i.e., inferring confidence in expected free energy) and with it the sense of self  [^note-3].

The dampening of affect and the feeling of self-loss are intimately related here. In losing a sense of allostatic control, the system ceases to posit itself as a causally efficacious controller of sensations. Accordingly, in losing a sense that the system has allostatic control across contexts, the affective system ceases to tune to opportunities to reduce error. Nothing is motivationally salient because the system infers that it is not causally efficacious in bringing about self-evidencing outcomes, and as such, it infers a global loss of confidence in precision on action policies (see ). The result would be that the world would lose some of its _phenomenal depth—_ it would cease to solicit one’s engagements and so be perceived (just as DPD sufferers suggest) as two-dimensional, or flat (, p. 93). The result is, as Colombetti and Ratcliffe write, that “The world ceases to matter, people and events are not salient anymore. With this, the world ceases to move and affect one through one’s body” (2012, p. 148; see also work by; ).

This proposal casts new light on various circumstances of occurrence surrounding experiences of depersonalization. For example, consider a traumatic stressor such as torture, which is perhaps the most reliable instigator of depersonalization (). On the current account, sustained inefficiency of the motivational system (in this case, severe pain over an extended period of time) in a scenario where the person has no control to act to resolve the prediction error results in a global loss of confidence in “tuning” affective responses. Another example is major depression. Depression can be understood as a domain general inference of loss of allostatic control, where, in extreme cases, the system ceases to posit itself as a causally efficacious agent (; ). The chronic stress of an uncertain or volatile environment means eventually that the system ceases to posit endogenous control on the outcomes as the occurrence of positive/negative outcomes is inferred to be independent of the agent’s actions. Through the current framework, the comorbidity of major depression with depersonalization can be understood to be a sustained loss of allostatic self-efficacy. Stephan and colleagues proposed that “the performance of interoceptive-allostatic circuitry is monitored by a metacognitive layer that updates beliefs about the brain’s capacity to successfully regulate bodily states” (, p. 1), which they dub “allostatic self-efficacy.” Other accounts have proposed that depression functions as a means of reducing prediction error associated with adverse social contexts (). If this is along the right lines, depression itself would function as a means of motivating withdrawal from potentially aversive contexts. The link between major depression and depersonalization can be understood here in terms of the system ceasing to posit itself as an endogenous controller of self-evidencing outcomes—when there are no possible context to move to (no high level, temporally deep goal priors to realize), the total loss of allostatic control is experienced as depersonalization [^note-4].

In the next section, we turn our attention to an example of a potentially euphoric selfless experience, namely, the sorts of selfless experiences that can arise from meditation. A view of the self-model in terms of allostatic control gives a fitting account of this and shows how this kind of selfless experience is radically different (indeed, relative to control, they are diametrically opposed) to selfless experience in depersonalization.

## ACM Account of Meditative Selflessness ^acm-account-of-meditative

While meditation is something of an umbrella term, the disciplined control of attention is central to almost all styles of meditation (;;; ). For brevity, we will focus here specifically on _focused attention meditation_. Meditation here takes the form of consciously attending to a particular object (i.e., bodily sensation or breathing), and when the mind wanders from the chosen target and the practitioner realizes the shift, they actively “let go” of the distractor and reorient their attention back to the initial meditative target.

Active inference has recently begun to be applied to thinking about meditation (; ). have provided the first account of _focused attention_ meditation in terms of active inference. Focused attention meditation is described as having two interrelated aims: the pragmatic activity of regulating attention on a particular object (i.e., the breath sensations, an object) and the epistemological activity of increasing one’s understanding of the nature of the meditative object and the various distractors, in particular recognizing their dynamic and impersonal nature (Lutz, 28).

In active inference terms, the pragmatic aspect of focused attention meditation requires that top–down directed precision enhance the behavioral policies associated with stable attention on an object. The challenge for the meditator then is to maintain this policy, although multiple other policies may be simultaneously active and acting as competitors for selection (). In meditation, this ongoing competition becomes simplified to include only the policy of maintaining attention on the meditation object and all other competing policies attempting to divert attentional resources elsewhere (e.g., spontaneous memories, future planning, homeostatic concerns, mind wandering, etc.). Inaction during this process is considered crucial, as it is the process of setting top–down precision on the sensory signals associated with the meditative object that allows this dialectic between focused attention and distraction to unfold and to be consciously attended to. Lutz and colleagues suggest that this quality of “inaction” corresponds to the subjective experience of “letting go” of the various distractions (p. 28).

Over time, the meditator can learn to allow the various distracting thoughts and sensations to arise and pass without disturbing their concentration, that is, without disrupting the meditation policy of focused attention. In part, this occurs through learning to actively reduce precision on the distracting (negative) goal prior. Inaction itself does this to some degree. An itch motivates, via negative valence, a scratching policy because of the preference for the non-itching state (i.e., goal prior) and the high precision on the itching state (i.e., resistance to the sensations), as well as the learned connection between the itch and the action policy scratching. By not acting, and calmly observing the itch, the negative preference loses precision (i.e., resistance to the sensations is dropped). The result is that the probability of the sensation driving the selection of a new (distracted) policy is also lessened. In other words, meditators can actively reduce certainty on goal states and mitigate involuntary policy selection through inaction. The result is that over time, such goal priors cease to draw processing (i.e., attention) in the same way.

In line with our view that the system infers its own control in terms of correspondence of action–outcome contingencies, here, the system learns endogenous control on the precision of goal priors through repeated reduction via opting for the focused attention policy. Over time, the decrease in distractibility can be understood as an increased ability to endogenously control precision on goal priors. The system here refines attentional selection through mental action in a way analogous to refining motor commands through iterative inference of control of action–outcome contingencies (; ). Note that learning to actively adjust precision on goal priors in this way is to learn to exert exactly the kind of control that is missing or weakened in cases of depersonalization as characterized above. In those cases, an inability to reduce precision on a goal prior that was unattainable leads to tremendous suffering and a loss of confidence in our ability to control the world more generally. In learning that it can endogenously set precision, it now begins to infer a domain general sense of being able to realize its goal states. This increase in domain general control may correspond to the pervasive feelings of joy and peace that characterize long-term meditation (; ).

During the course of becoming an adept meditator, one develops the ability to remain poised between the object of attention and the ongoing flow of spontaneous mental activities. This capacity to remain subtly focused on the meditative object, while at the same time observing clearly the spontaneous mental activity, provides an optimal opportunity to learn about the process of policy selection taking place within its own system (). This is the epistemological element of focused meditation. The result of this introspective investigation is a gradual “opacification” of these mental processes (). A mental process is considered transparent insofar as its contents are available to consciousness, while its non-intentional structure or construction process are not (). Without having access to the earlier stages of processing, transparent processes are presented subjectively as fundamentally real and personally essential. Metzinger writes,

> _“Transparent phenomenal states make their representational content appear as irrevocably _real_, as something the existence of which you cannot doubt. Put more precisely, you may certainly be able cognitively to have doubts about its existence, but according to subjective experience this phenomenal content—the _awfulness_ of pain, the fact that it is _your own_ pain—is not something you can distance yourself from. The phenomenol-ogy of transparency is the phenomenology of direct realism and in the domain of self-representation it creates the phenomenology of identifi-cation.” (2017, p. 248)._

By continually letting go, the distracting policy selections are observed as non-essential—they arise, they persist for some time, and they eventually dissolve without the need for overt actions. The system becomes aware of the constructed nature of these precision assignments (e.g., itching directly leading to scratching). Through repeated observation of this process, the system ceases to identify with the precision selections, exactly because it observes them to occur without attributing them to a “self” as an endogenous cause. Recall that the system infers itself as a self—as an endogenous cause of sensations—through agentive actions, where the correspondence between action–outcome contingency feels agentive. Through repeated reorientation of attention back to the meditation target (by reengaging the meditation policy), the automatic precision assignments (e.g., itch→scratch) cease to be identified as essential and so begin to lose the quality of immediateness and irrefutability that come with being transparent. Crucially, as the system observes these precision allocations occurring independently of agentive engagement (due to the non-action policy currently being engaged), the usual means of inferring itself as a self-due to the correspondence of action–outcome contingencies is disrupted, and processes occurring in the system increasingly appear as non-essential to the self. This point about opacification is an important one for our discussion about selfless experiences.

This ties in closely with the “non-self” themes in Buddhism. Common to all Buddhist schools is a critique of our ordinary self-experiences. The Buddhist doctrine of _no-self_ (anattā) teaches that our ordinary self-experience is both mistaken and an important source of human suffering. The mistake is the common assumption that behind the various psychophysical processes that make up our conscious experiences, there is a single, essential subject, who is responsible for constructing and owning those processes. However, when we turn our attention inwards in an attempt to catch a glimpse of this assumed subject, all we ever experience is the dynamic and impersonal processes. This is the point—while we commonly assume there to be an essential and _unconstructed_ subject, that sense of being a subject is in fact _constructed_ from the interaction of our cognitive–behavioral processes. The Buddhist move here is not to deny that the sense of self is real, that quality of experience that delineates my sensations from yours. Rather, the selfless insight Buddhist meditators seek out is the transformative recognition that, while the self unreflectively appears to us as essential, persisting, and unified, it is in fact constructed, impermanent, and dynamic (see ).

According to the Buddhist tradition, our mistaken assumptions about the self are generated and maintained by craving (_tanha_ in Pali). Craving is a technical term here; it describes the felt urgency or motivational drive to make the world conform to our desires—our anxiety to perpetuate positive feelings and reduce negative ones. This ongoing emotional investment is what unifies the various impersonal psychophysical processes under a single idea: a persistent and essential self. In turn, the more we identify with our specific concerns or roles, the more intense the motivation to bring about those states in the world [^note-5]. In humans, these desires expand beyond basic homeostatic concerns (i.e., being fed and watered) to include the wider constellation of ideas and roles we appropriate into our identity (i.e., being a student). In Buddhism, this craving is thought to be responsible for significant human suffering. Consider the difference in magnitude between the relatively short-lived pain of breaking an arm, and the potentially life long suffering of losing an opportunity to play a beloved sport professionally. At the heart of Buddhism is the teaching that, while pain is unavoidable (i.e., the broken bone), our reaction to it (i.e., the craving to be a professional player) is optional. It is the craving, and not the pain, that is thought to be transformed through meditation and with it the mistaken sense of self that craving engenders.

Meditation is presented as a vehicle for reducing craving and disrupting the mistaken view of self. In the satipatthana sutta, the foremost early Buddhist text on meditation, the student is directed to divide their experience into five categories (or “aggregates”) of phenomena: bodily form, valence, perception, volitional activities, and consciousness. These aggregates together are thought to create the experience of being a subject (; ). The aim of meditation here is to reduce one’s identification with these psychophysical processes by closely examining each individually and their interactions and systematically noting their impersonal nature. In Anattalakkhaṇa Suttam, the Buddha suggests that meditators observe each aggregate, saying to themselves “not-I” or “not-my-self.” As the various psychophysical processes that make up the self-come to be experienced as “not-I,” the constructed nature of the self becomes apparent.

In addition to non-meditation policies (i.e., distractions) being driven by changes in goal states, they are also driven by our affective reactions to those goal states. As we have seen, valence sets precision relative to our ability to reduce error given a certain goal. Ordinarily, once a goal state is selected (predicted), any hesitancy in responding in the ways that the system has learned to expect produces negative valence, which has the effect of increasing the drive on policy selection as an attempt to catch up to the predicted slope. As long as valence is experienced transparently, it has this powerful motivating effect on actions. The meditator then must also be able to reduce the certainty on the valenced reactions that occur from their commitment to non-action. By attending to the valenced sensations themselves (i.e., the discomfort of not reacting), the system learns that these signals too are changing and non-essential. As soon as one has made the observation that non-action makes them uncomfortable, these systems are already being rendered opaque. Focused attention meditation then simultaneously makes opaque precision on goal priors (i.e., the confidence in the degree of wanting or not wanting certain states) and precision on expected free energy reduction that is given affectively.

In Buddhism, reflecting on valence (_vedana_ in pali) is considered especially important in the process of relinquishing craving and disrupting the mistaken view of the self. Valence is considered the “weak link” in the process that gives rise to both craving and the mistaken view of self (). In non-meditators, valence conditions craving: pleasant feelings give rise to attachment; painful feelings give rise to resistance. In contrast, long-term meditators are thought to be able to experience valence without further craving-driven responses. The Buddha taught,

> _“Touched by that pleasant feeling he does not lust after pleasure or continue to lust after pleasure. That pleasant feeling of his ceases. With the cessation of the pleasant feeling, painful feeling arises. Touched by that painful feeling, he does not sorrow, grieve, and lament, he does not weep beating his breast and becomes distraught” (, p. 334)._

Notice that even for the “well-taught noble disciple” (that is, meditators who no longer operate under craving and illusory notions of the self), valenced states still arise. These states are in and of themselves neutral in terms of well-being (). It is the strong motivational impulse to act (i.e., fleeing our pain; grasping at joys) in response to those signals that the Buddhist meditative project aims to transform. A close meditative investigation of valence is taught to have the effect of separating valence from craving, the result being that one begins to react with less preference relative to pleasure and pain. As Buddhist scholar Albahari writes, “As mental suffering is finally eliminated through insight \[into the non-self-nature of these processes\], unpleasant _vedanā_ will be confined to only physical (not mental) suffering” (, p. 11). As our urgency to react in self-serving ways diminishes, so too does the illusion of being an enduring and essential subject. The culmination of this process of extinguishing craving is _nibbāna_ \[enlightenment\]: “the final flash of insight that burns out _taṇhā_ and the sense of self for good” (, p. 11).

The gradual opacification of valence results in various positive effects discussed in the Buddhist paradigm. As described above, inaction would allow for the opacification and dereification of the valence system. As valence is increasingly modeled (made opaque), it ceases to invoke that powerful sense of urgency (associated with the Buddhist notion of craving or taṇhaā;), which, as we saw above, results from valence being experienced transparently and so presented phenomenologically as both immediately real and essential to the self (). This change is an important one, as it results in the loss of the driving force that perpetuates the sense that there is an essential subject within and behind the various processes (). As valence is made opaque, and control over goal prior precisions is achieved, craving ceases due to its disentanglement from the conditioning influence of pleasure or pain. Thus, the illusion of self is disrupted. In gaining endogenous control on the precision of goal priors, meditation therefore enables the system to pull these apart so that (dis)liking does not need to condition (not) wanting, allowing the suffering associated with craving (and aversion) to be avoided. Gaining insight into the process by which valence is driven by our goal priors would have the consequence of allowing one to actively separate the two darts discussed by the Buddha. One comes to understand how pain (deviation from a goal prior) leads to suffering (transparent negative valence signaling the deviation from the goal prior and its expected resolution); that suffering occurs only insofar as we desire to avoid the pain (high precision on the goal prior drives error dynamics); and finally, although we often cannot do anything about the pain itself, we can, by watching the whole process closely, render the valenced reactions opaque and so reduce the degree to which valence drives policy selection. That is, we can reduce the craving and suffering that arises from transparent valenced reactions simply by observing closely the link between pain and discomfort, thereby rendering the valence opaque.

The opacification of this part of the precision machinery opens new opportunities for control. Observing our valenced reactions allows us to develop new higher order policies about how precision (via valence) is being set on policies [^note-6]. In other words, instead of valenced signals adjusting precision on policies directly, and so automatically conditioning us to behave in certain ways, one can now learn to activate alternative policies depending on the usefulness of the valenced signals. For example, mindfulness has been shown to be highly effective in helping people to quit smoking cigarettes (). The practice here is to disrupt the pattern leading from craving to using by selecting a policy to closely attend to the feelings of craving—the negative valence driving processing toward the expected rate of error reduction relative to nicotine levels—every time they arise. The new goal now activated every time there is a craving (instead of smoking a cigarette) is to watch, as closely as possible the arising, the progression and the inevitable depletion of the craving-related feelings. Overtime, these sorts of mindfulness practices have the effect of teaching the system that cravings are in fact just feelings in the body, which can be allowed to direct processing and behavior or not [^note-7]. This discovery can represent a major return of control for people struggling with substance addiction. Notice that valence here does not go missing through this process of opacification (as it does in depersonalization). Rather, valence begins to be interpreted by the system as what it is: information that can be useful, but is not essential, in selecting policies.

## Conclusion ^conclusion

In this paper, we seek to better understand the nature of the self from the perspective of the increasingly popular active inference framework. Within this framework, we present a novel account of the self, in terms of an allostatic control model (ACM; ). Central to the ACM account is a view of affect as a second-order process that guides the predictive system (via precision weighting) toward opportunities to improve. This is a novel take on affect that we have been developing over a number of recent publications (, [^cite-10]; ).

We then put this account to work in trying to understand two starkly contrasting forms of self-loss, namely, depersonalization and the selfless experiences attained through meditation (viz., Buddhist no-self insights). Given our proposed framework, these two varieties of selfless experience are characterized by stark differences in the systems degree of control: whereas depersonalization is expressly characterized as resulting from a critical loss of inferred control, selflessness in the context of meditative practices is marked by a significant gain in control.

There is today, however, an increasingly popular idea that depersonalization and the selfless experiences attained through meditation are somehow closely related. Meditation teacher and neuroscience enthusiast Shinzen Young has called depersonalization the “evil twin” of the Buddhist notion of _enlightenment_ (). Part of what motivates this association, so it seems, are similarities in first personal accounts of both kinds of selfless states. Sufferers of depersonalization and long-term meditators make surprisingly similar reports about reductions in their experience of being agents of their actions and as owners of their thoughts and behaviors. While these first personal accounts can sound very similar, given our framework, this is where the family resemblance ends.

As we have shown throughout this paper, there are important computational differences between these two selfless experiences. Of particular importance is the difference in how affective valence contributes to either state. Depersonalization is characterized as a loss of control, leading to the dampening of these affective valence systems. In meditation, there occurs a gradual opacification of the affective valence system. This opacification produces an important change in the meditator’s relationship with the positive and negative affect—specifically, by no longer being automatically appropriated into their self-model. This has the result that changes in valence no longer create the existential urgency for change they would otherwise. It is important to note here that valence remains perfectly intact, continuing to tune the agent toward opportunities to improve in their predictive success. The purpose of the practice is not to disrupt valence itself (as happens in depersonalization) but rather to become conscious of the precision estimators in a way that allows them to select more skillful and beneficial policies. What is permanently altered in the meditation process is the system’s reaction to those signals. While there is still the experience of frustration and joy, there is no longer the sense of being an essential subject to appropriate these states as “me” and “mine.” This insight leads to an eventual dissolving of our misguided idea that we are a single and enduring thing, to be replaced by an acknowledgment that we are a dynamic, self-organizing process. Far from reducing control, and in direct contrast to depersonalization, this development of one’s metacognitive abilities here allows one to contextualize and control precision estimations in new and powerful ways.

Notice then that for someone to transition from experiences of depersonalization to the selfless states attained through meditation, they would first need to regain their phenomenal access to those affective responses. Without affect playing its role in tuning the system (relative to its predictive success), the opacification and subsequent insight into the nature of those precision processes could not occur. To be clear, we are not suggesting that the endeavor of bringing affect back online for people suffering depersonalization should be carried out through meditation specifically [^note-8]. Rather, our point is that those affective signals would have to first become available for introspective access in order to be modeled in the way facilitated by focused meditation. This follows from the fact that, on our account, it is not the loss of affectivity that results in the selfless experiences sought after by Buddhist meditators but the process of modeling those affective changes that opens the way for a new perspective of the self and a new layer of control to emerge.

In terms of control, depersonalization and selfless experiences sought after by mediators are, computationally speaking, polar opposites. And yet, there is something important to be said here about the potential focused attention meditation has to provoke depersonalization experiences. Britton’s _Dark Night Project_ has documented and investigated a large number of personal reports on various difficulties that can accompany meditative practices [^note-9]. suggests that adopting a persistent attitude of turning toward difficult stimuli and focusing on negative emotions can lead to negative outcomes. This aspect of mindfulness training has positive effects for some people, primarily by helping them to facilitate a gradual sensitization to negative affect. Such exposure approaches to therapy are thought to work by reducing avoidance, which has been shown to play a leading role in the generation and maintenance of various psychological disorders (). However, exposure therapies are most effective for people who tend toward high levels of avoidance (). In other, low-avoidance personality types, anxiety and dissociative disorders can be produced and exacerbated by facilitating an attentional bias toward threat (; ). The fact is that the most effective treatment for an individual will depend on their baseline attitude toward threat. Given our account above, it makes sense why inappropriately meditating on traumatic events (that is beyond a certain healthy window of tolerance) could create depersonalization effects. If depersonalization is an airbag deployed when fight or flight would not work for getting one out of a traumatic emotional experience, then persistently meditating on an overwhelmingly traumatic experience while practicing inaction produces just those conditions. In effect, it could act like a kind of psychological self-torture. Meditation, in this case, would begin to lead to a perceived loss of allostatic self-efficacy, rather than toward the liberating states of self-understanding it is meant to.

## Statements ^statements

### Author contributions ^author-contributions

All authors provided equal contributions to all sections, and so names appear in alphabetical order.

### Funding ^funding

MM and GD carried out this work with the support of Horizon 2020 European Union ERC Advanced Grant XSPECT - DLV-692739.

### Acknowledgments ^acknowledgments

We would like to thank Lars Sandved-Smith and Maxwell Ramstead for the ongoing discussions about meditation, metacognition, and awareness from an active inference perspective.

### Conflict of interest ^conflict-of-interest

The authors declare that the research was conducted in the absence of any commercial or financial relationships that could be construed as a potential conflict of interest.

## References ^references

:::hide

-   1
    
    AlbahariM. (2009). Witness-consciousness: its definition, appearance and reality. _J. Conscious. Stud._ 1662–84.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BAlbahari&publication_year=2009&title=Witness-consciousness%3A%2Bits%2Bdefinition%2C%2Bappearance%2Band%2Breality.&journal=J.+Conscious.+Stud.&volume=16&pages=62-84)
    -   [View reference in article](#B1a)
    
-   2
    
    AlbahariM. (2014). Insight knowledge of no self in Buddhism: an epistemic analysis.__Philos. Imprint__ 141–30.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BAlbahari&publication_year=2014&title=Insight%2Bknowledge%2Bof%2Bno%2Bself%2Bin%2BBuddhism%3A%2Ban%2Bepistemic%2Banalysis.&journal=Philos.+Imprint&volume=14&pages=1-30)
    -   [View reference in article](#B2a)
    
-   3
    
    AllenM.FristonK. J. (2016). From cognitivism to autopoiesis: towards a computational framework for the embodied mind.__Synthese__ 1952459–2482. 10.1007/s11229-016-1288-5
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/29887647)
    -   [CrossRef](https://doi.org/10.1007/s11229-016-1288-5)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BAllen&author=K.%2BJ..%2BFriston&publication_year=2016&title=From%2Bcognitivism%2Bto%2Bautopoiesis%3A%2Btowards%2Ba%2Bcomputational%2Bframework%2Bfor%2Bthe%2Bembodied%2Bmind.&journal=Synthese&volume=195&pages=2459-2482)
    -   [View reference in article](#B3a)
    
-   4
    
    AllenM.TsakirisM. (2018). “The body as first prior: interoceptive predictive processing and the primacy,” in __The Interoceptive Mind: From Homeostasis to Awareness__ (Oxford: Oxford University Press), 2–7.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BAllen&author=M..%2BTsakiris&publication_year=2018&title=The%2Bbody%2Bas%2Bfirst%2Bprior%3A%2Binteroceptive%2Bpredictive%2Bprocessing%2Band%2Bthe%2Bprimacy&journal=The+Interoceptive+Mind%3A+From+Homeostasis+to+Awareness&pages=2-7)
    -   [View reference in article](#B4a)
    
-   5
    
    Anālayo (2009). __From Craving to Liberation-Excursions Into the Thought-word of the Pâli Discourses (1).__ New York, NY: Buddhist Association of the United States.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?publication_year=2009&journal=From+Craving+to+Liberation-Excursions+Into+the+Thought-word+of+the+P%C3%A2li+Discourses+%281%29.)
    -   [View reference in article](#B5a)
    
-   6
    
    AppsM. A.TsakirisM. (2014). The free-energy self: a predictive coding account of self-recognition. _Neurosci. Biobehav. Rev._ 4185–97. 10.1016/j.neubiorev.2013.01.029
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/23416066)
    -   [CrossRef](https://doi.org/10.1016/j.neubiorev.2013.01.029)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M.%2BA..%2BApps&author=M..%2BTsakiris&publication_year=2014&title=The%2Bfree-energy%2Bself%3A%2Ba%2Bpredictive%2Bcoding%2Baccount%2Bof%2Bself-recognition.&journal=Neurosci.+Biobehav.+Rev.&volume=41&pages=85-97)
    -   [View reference in article](#B6a)
    
-   7
    
    AshbyW. (2013). __Design for a Brain: The Origin of Adaptive Behaviour.__ Berlin: Springer.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=W..%2BAshby&publication_year=2013&journal=Design+for+a+Brain%3A+The+Origin+of+Adaptive+Behaviour.)
    -   [View reference in article](#B7a)
    
-   8
    
    AustinJ. H. (2013). Zen and the brain: mutually illuminating topics. _Front. Psychol._ 4:784. 10.3389/fpsyg.2015.00784
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26113831)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00784)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J.%2BH..%2BAustin&publication_year=2013&title=Zen%2Band%2Bthe%2Bbrain%3A%2Bmutually%2Billuminating%2Btopics.&journal=Front.+Psychol.&volume=4)
    -   [View reference in article](#B8a)
    
-   9
    
    BadcockP. B.DaveyC. G.WhittleS.AllenN. B.FristonK. J. (2017). The depressed brain: an evolutionary systems theory. _Trends Cogn. Sci._ 21182–194. 10.1016/j.tics.2017.01.005
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/28161288)
    -   [CrossRef](https://doi.org/10.1016/j.tics.2017.01.005)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=P.%2BB..%2BBadcock&author=C.%2BG..%2BDavey&author=S..%2BWhittle&author=N.%2BB..%2BAllen&author=K.%2BJ..%2BFriston&publication_year=2017&title=The%2Bdepressed%2Bbrain%3A%2Ban%2Bevolutionary%2Bsystems%2Btheory.&journal=Trends+Cogn.+Sci.&volume=21&pages=182-194)
    -   [View reference in article](#B9a)
    
-   10
    
    BakerD.EarleM.MedfordN.SierraM.TowellA.DavidA. (2007). Illness perceptions in depersonalization disorder: testing an illness attribution model. _Clin. Psychol. Psychothera. Int. J. Theory Pract._ 14105–116. 10.1002/cpp.518
    
    -   [CrossRef](https://doi.org/10.1002/cpp.518)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=D..%2BBaker&author=M..%2BEarle&author=N..%2BMedford&author=M..%2BSierra&author=A..%2BTowell&author=A..%2BDavid&publication_year=2007&title=Illness%2Bperceptions%2Bin%2Bdepersonalization%2Bdisorder%3A%2Btesting%2Ban%2Billness%2Battribution%2Bmodel.&journal=Clin.+Psychol.+Psychothera.+Int.+J.+Theory+Pract.&volume=14&pages=105-116)
    -   [View reference in article](#B10a)
    
-   11
    
    BarrettL. F. (2017). The theory of constructed emotion: an active inference account of interoception and categorization. _Soc. Cogn. Affect. Neurosci._ 121–23.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=L.%2BF..%2BBarrett&publication_year=2017&title=The%2Btheory%2Bof%2Bconstructed%2Bemotion%3A%2Ban%2Bactive%2Binference%2Baccount%2Bof%2Binteroception%2Band%2Bcategorization.&journal=Soc.+Cogn.+Affect.+Neurosci.&volume=12&pages=1-23)
    -   [View reference in article](#B11a)
    
-   12
    
    BarryT. J.VervlietB.HermansD. (2015). An integrative review of attention biases and their contribution to treatment for anxiety disorders. _Front. Psychol._ 6:968. 10.3389/fpsyg.2015.00968
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26217284)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00968)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=T.%2BJ..%2BBarry&author=B..%2BVervliet&author=D..%2BHermans&publication_year=2015&title=An%2Bintegrative%2Breview%2Bof%2Battention%2Bbiases%2Band%2Btheir%2Bcontribution%2Bto%2Btreatment%2Bfor%2Banxiety%2Bdisorders.&journal=Front.+Psychol.&volume=6)
    -   [View reference in article](#B12a)
    
-   13
    
    BartoA. G. (2013). “Intrinsic motivation and reinforcement learning,” in __Intrinsically Motivated Learning in Natural and Artificial Systems__, edsBaldassarreG.MirolliM. (Berlin: Springer), 17–47. 10.1007/978-3-642-32375-1\_2
    
    -   [CrossRef](https://doi.org/10.1007/978-3-642-32375-1_2)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BG..%2BBarto&publication_year=2013&title=Intrinsic%2Bmotivation%2Band%2Breinforcement%2Blearning&journal=Intrinsically+Motivated+Learning+in+Natural+and+Artificial+Systems&pages=17-47)
    
-   14
    
    BlakemoreS. J.SmithJ.SteelR.JohnstoneE. C.FrithC. D. (2000). The perception of self-produced sensory stimuli in patients with auditory hallucinations and passivity experiences: evidence for a breakdown in self-monitoring. _Psychol. Med._ 301131–1139. 10.1017/s0033291799002676
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/12027049)
    -   [CrossRef](https://doi.org/10.1017/s0033291799002676)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S.%2BJ..%2BBlakemore&author=J..%2BSmith&author=R..%2BSteel&author=E.%2BC..%2BJohnstone&author=C.%2BD..%2BFrith&publication_year=2000&title=The%2Bperception%2Bof%2Bself-produced%2Bsensory%2Bstimuli%2Bin%2Bpatients%2Bwith%2Bauditory%2Bhallucinations%2Band%2Bpassivity%2Bexperiences%3A%2Bevidence%2Bfor%2Ba%2Bbreakdown%2Bin%2Bself-monitoring.&journal=Psychol.+Med.&volume=30&pages=1131-1139)
    -   [View reference in article](#B14a)
    
-   15
    
    BowenS.MarlattA. (2009). Surfing the urge: brief mindfulness-based intervention for college student smokers. _Psychol. Addict. Behav._ 23:666. 10.1037/a0017127
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/20025372)
    -   [CrossRef](https://doi.org/10.1037/a0017127)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S..%2BBowen&author=A..%2BMarlatt&publication_year=2009&title=Surfing%2Bthe%2Burge%3A%2Bbrief%2Bmindfulness-based%2Bintervention%2Bfor%2Bcollege%2Bstudent%2Bsmokers.&journal=Psychol.+Addict.+Behav.&volume=23)
    -   [View reference in article](#B15a)
    
-   16
    
    BrittonW. B. (2019). Can mindfulness be too much of a good thing? The value of a middle way. _Curr. Opin. Psychol._ 28159–165. 10.1016/j.copsyc.2018.12.011
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/30708288)
    -   [CrossRef](https://doi.org/10.1016/j.copsyc.2018.12.011)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=W.%2BB..%2BBritton&publication_year=2019&title=Can%2Bmindfulness%2Bbe%2Btoo%2Bmuch%2Bof%2Ba%2Bgood%2Bthing%3F%2BThe%2Bvalue%2Bof%2Ba%2Bmiddle%2Bway.&journal=Curr.+Opin.+Psychol.&volume=28&pages=159-165)
    -   [View reference in article](#B16a)
    
-   17
    
    BruinebergJ.RietveldE. (2014). Self-organization, free energy minimization, and optimal grip on a field of affordances. _Front. Hum. Neurosci._ 8:599. 10.3389/fnhum.2014.00599
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/25161615)
    -   [CrossRef](https://doi.org/10.3389/fnhum.2014.00599)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BBruineberg&author=E..%2BRietveld&publication_year=2014&title=Self-organization%2C%2Bfree%2Benergy%2Bminimization%2C%2Band%2Boptimal%2Bgrip%2Bon%2Ba%2Bfield%2Bof%2Baffordances.&journal=Front.+Hum.+Neurosci.&volume=8)
    -   [View reference in article](#B17a)
    
-   18
    
    CarterO. L.PrestiD. E.CallistemonC.UngererY.LiuG. B.PettigrewJ. D. (2005). Meditation alters perceptual rivalry in tibetan buddhist monks. _Curr. Biol._ 15R412–R413.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=O.%2BL..%2BCarter&author=D.%2BE..%2BPresti&author=C..%2BCallistemon&author=Y..%2BUngerer&author=G.%2BB..%2BLiu&author=J.%2BD..%2BPettigrew&publication_year=2005&title=Meditation%2Balters%2Bperceptual%2Brivalry%2Bin%2Btibetan%2Bbuddhist%2Bmonks.&journal=Curr.+Biol.&volume=15&pages=R412-R413)
    -   [View reference in article](#B18a)
    
-   19
    
    CiaunicaA.CharltonJ.FarmerH. (2020). When the window cracks: transparency and the fractured self in depersonalisation. _Phenomenol. Cogn. Sci._ 621–19.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A..%2BCiaunica&author=J..%2BCharlton&author=H..%2BFarmer&publication_year=2020&title=When%2Bthe%2Bwindow%2Bcracks%3A%2Btransparency%2Band%2Bthe%2Bfractured%2Bself%2Bin%2Bdepersonalisation.&journal=Phenomenol.+Cogn.+Sci.&volume=62&pages=1-19)
    -   [View reference in article](#B19a)
    
-   20
    
    ClarkA. (2013). Whatever next? Predictive brains, situated agents, and the future of cognitive science. _Behav. Brain Sci._ 36181–204. 10.1017/s0140525x12000477
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/23663408)
    -   [CrossRef](https://doi.org/10.1017/s0140525x12000477)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A..%2BClark&publication_year=2013&title=Whatever%2Bnext%3F%2BPredictive%2Bbrains%2C%2Bsituated%2Bagents%2C%2Band%2Bthe%2Bfuture%2Bof%2Bcognitive%2Bscience.&journal=Behav.+Brain+Sci.&volume=36&pages=181-204)
    -   [View reference in article](#B20a)
    
-   21
    
    ClarkA. (2015). __Surfing Uncertainty: Prediction Action and the Embodied Mind.__ Oxford: Oxford University Press.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A..%2BClark&publication_year=2015&journal=Surfing+Uncertainty%3A+Prediction+Action+and+the+Embodied+Mind.)
    -   [View reference in article](#B21a)
    
-   22
    
    ColombettiG.RatcliffeM. (2012). Bodily feeling in depersonalization: a phenomenological account. _Emot. Rev._ 4145–150. 10.1177/1754073911430131
    
    -   [CrossRef](https://doi.org/10.1177/1754073911430131)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BColombetti&author=M..%2BRatcliffe&publication_year=2012&title=Bodily%2Bfeeling%2Bin%2Bdepersonalization%3A%2Ba%2Bphenomenological%2Baccount.&journal=Emot.+Rev.&volume=4&pages=145-150)
    -   [View reference in article](#B22a)
    
-   23
    
    CorcoranA. W.PezzuloG.HohwyJ. (2019). From allostatic agents to counterfactual cognisers: active inference. _Biol. Philos._ 35:32.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BW..%2BCorcoran&author=G..%2BPezzulo&author=J..%2BHohwy&publication_year=2019&title=From%2Ballostatic%2Bagents%2Bto%2Bcounterfactual%2Bcognisers%3A%2Bactive%2Binference.&journal=Biol.+Philos.&volume=35)
    -   [View reference in article](#B23a)
    
-   24
    
    CraigA. D. (2003). Interoception: the sense of the physiological condition of the body. _Curr. Opin. Neurobiol._ 13500–505. 10.1016/s0959-4388(03)00090-4
    
    -   [CrossRef](https://doi.org/10.1016/s0959-4388\(03\)00090-4)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BD..%2BCraig&publication_year=2003&title=Interoception%3A%2Bthe%2Bsense%2Bof%2Bthe%2Bphysiological%2Bcondition%2Bof%2Bthe%2Bbody.&journal=Curr.+Opin.+Neurobiol.&volume=13&pages=500-505)
    -   [View reference in article](#B24a)
    
-   25
    
    DamasioA. (2003). Feelings of emotion and the self. _Ann. N. Y. Acad. Sci._ 1001253–261.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A..%2BDamasio&publication_year=2003&title=Feelings%2Bof%2Bemotion%2Band%2Bthe%2Bself.&journal=Ann.+N.+Y.+Acad.+Sci.&volume=1001&pages=253-261)
    -   [View reference in article](#B25a)
    
-   26
    
    DambrunM. (2016). When the dissolution of perceived body boundaries elicits happiness: the effect of selflessness induced by a body scan meditation. _Conscious. Cogn._ 4689–98. 10.1016/j.concog.2016.09.013
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/27684609)
    -   [CrossRef](https://doi.org/10.1016/j.concog.2016.09.013)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BDambrun&publication_year=2016&title=When%2Bthe%2Bdissolution%2Bof%2Bperceived%2Bbody%2Bboundaries%2Belicits%2Bhappiness%3A%2Bthe%2Beffect%2Bof%2Bselflessness%2Binduced%2Bby%2Ba%2Bbody%2Bscan%2Bmeditation.&journal=Conscious.+Cogn.&volume=46&pages=89-98)
    -   [View reference in article](#B26a)
    
-   27
    
    DambrunM.RicardM. (2011). Self-centeredness and selflessness: a theory of self-based psychological functioning and its consequences for happiness. _Rev. Gen. Psychol._ 15138–157. 10.1037/a0023059
    
    -   [CrossRef](https://doi.org/10.1037/a0023059)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BDambrun&author=M..%2BRicard&publication_year=2011&title=Self-centeredness%2Band%2Bselflessness%3A%2Ba%2Btheory%2Bof%2Bself-based%2Bpsychological%2Bfunctioning%2Band%2Bits%2Bconsequences%2Bfor%2Bhappiness.&journal=Rev.+Gen.+Psychol.&volume=15&pages=138-157)
    -   [View reference in article](#B27a)
    
-   28
    
    DavisJ.ThompsonE. (2017). From the five aggregates to phenomenal consciousness: toward a cross-cultural cognitive science.__mindRxiv__ \[Preprint\], Available online at: [https://mindrxiv.org/bs8af/](https://mindrxiv.org/bs8af/)
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BDavis&author=E..%2BThompson&publication_year=2017&title=From%2Bthe%2Bfive%2Baggregates%2Bto%2Bphenomenal%2Bconsciousness%3A%2Btoward%2Ba%2Bcross-cultural%2Bcognitive%2Bscience.&journal=mindRxiv)
    -   [View reference in article](#B28a)
    
-   29
    
    DeaneG. (2020). Dissolving the self: active inference, psychedelics, and ego-dissolution. _Philos. Mind Sci._ 11–21. 10.33735/phimisci.2020.i.39
    
    -   [CrossRef](https://doi.org/10.33735/phimisci.2020.i.39)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BDeane&publication_year=2020&title=Dissolving%2Bthe%2Bself%3A%2Bactive%2Binference%2C%2Bpsychedelics%2C%2Band%2Bego-dissolution.&journal=Philos.+Mind+Sci.&volume=1&pages=1-21)
    -   [View reference in article](#B29a)
    
-   30
    
    EldarS.RiconT.Bar-HaimY. (2008). Plasticity in attention: implications for stress response in children. _Behav. Res. Ther._ 46450–461. 10.1016/j.brat.2008.01.012
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/18313034)
    -   [CrossRef](https://doi.org/10.1016/j.brat.2008.01.012)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S..%2BEldar&author=T..%2BRicon&author=Y..%2BBar-Haim&publication_year=2008&title=Plasticity%2Bin%2Battention%3A%2Bimplications%2Bfor%2Bstress%2Bresponse%2Bin%2Bchildren.&journal=Behav.+Res.+Ther.&volume=46&pages=450-461)
    -   [View reference in article](#B30a)
    
-   31
    
    FabryR. E. (2019). Into the dark room: a predictive processing account of major depressive disorder. _Phenomenol. Cogn. Sci._ 19685–704. 10.1007/s11097-019-09635-4
    
    -   [CrossRef](https://doi.org/10.1007/s11097-019-09635-4)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=R.%2BE..%2BFabry&publication_year=2019&title=Into%2Bthe%2Bdark%2Broom%3A%2Ba%2Bpredictive%2Bprocessing%2Baccount%2Bof%2Bmajor%2Bdepressive%2Bdisorder.&journal=Phenomenol.+Cogn.+Sci.&volume=19&pages=685-704)
    
-   32
    
    FarbN.DaubenmierJ.PriceC. J.GardT.KerrC.DunnB. D.et al (2015). Interoception, contemplative practice, and health. _Front. Psychol._ 6:763. 10.3389/fpsyg.2015.00763
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26106345)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00763)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=N..%2BFarb&author=J..%2BDaubenmier&author=C.%2BJ..%2BPrice&author=T..%2BGard&author=C..%2BKerr&author=B.%2BD..%2BDunn&publication_year=2015&title=Interoception%2C%2Bcontemplative%2Bpractice%2C%2Band%2Bhealth.&journal=Front.+Psychol.&volume=6)
    -   [View reference in article](#B32a)
    
-   33
    
    FristonK. (2005). A theory of cortical responses. _Philos. Trans. R. Soc. Lond. B Biol. Sci._ 360815–836. 10.1098/rstb.2005.1622
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/15937014)
    -   [CrossRef](https://doi.org/10.1098/rstb.2005.1622)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K..%2BFriston&publication_year=2005&title=A%2Btheory%2Bof%2Bcortical%2Bresponses.&journal=Philos.+Trans.+R.+Soc.+Lond.+B+Biol.+Sci.&volume=360&pages=815-836)
    -   [View reference in article](#B33a)
    
-   34
    
    FristonK. (2010). The free-energy principle: a unified brain theory? _Nat. Rev. Neurosci._ 11127–138. 10.1038/nrn2787
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/20068583)
    -   [CrossRef](https://doi.org/10.1038/nrn2787)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K..%2BFriston&publication_year=2010&title=The%2Bfree-energy%2Bprinciple%3A%2Ba%2Bunified%2Bbrain%2Btheory%3F&journal=Nat.+Rev.+Neurosci.&volume=11&pages=127-138)
    -   [View reference in article](#B34a)
    
-   35
    
    FristonK. (2018). Am I self-conscious?(or does self-organization entail self-consciousness?). _Front. Psychol._ 9:579. 10.3389/fpsyg.2015.00579
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26029135)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00579)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K..%2BFriston&publication_year=2018&title=Am%2BI%2Bself-conscious%3F%28or%2Bdoes%2Bself-organization%2Bentail%2Bself-consciousness%3F%29.&journal=Front.+Psychol.&volume=9)
    -   [View reference in article](#B35a)
    
-   36
    
    FristonK.FitzGeraldT.RigoliF.SchwartenbeckP.PezzuloG. (2017). Active inference: a process theory. _Neural Comput._ 291–49. 10.1162/neco\_a\_00912
    
    -   [CrossRef](https://doi.org/10.1162/neco_a_00912)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K..%2BFriston&author=T..%2BFitzGerald&author=F..%2BRigoli&author=P..%2BSchwartenbeck&author=G..%2BPezzulo&publication_year=2017&title=Active%2Binference%3A%2Ba%2Bprocess%2Btheory.&journal=Neural+Comput.&volume=29&pages=1-49)
    -   [View reference in article](#B36a)
    
-   37
    
    FristonK.RigoliF.OgnibeneD.MathysC.FitzgeraldT.PezzuloG. (2015). Active inference and epistemic value. _Cogn. Neurosci._ 6187–214. 10.1080/17588928.2015.1020053
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/25689102)
    -   [CrossRef](https://doi.org/10.1080/17588928.2015.1020053)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K..%2BFriston&author=F..%2BRigoli&author=D..%2BOgnibene&author=C..%2BMathys&author=T..%2BFitzgerald&author=G..%2BPezzulo&publication_year=2015&title=Active%2Binference%2Band%2Bepistemic%2Bvalue.&journal=Cogn.+Neurosci.&volume=6&pages=187-214)
    -   [View reference in article](#B37a)
    
-   38
    
    FristonK.SchwartenbeckP.FitzGeraldT.MoutoussisM.BehrensT.DolanR. J. (2013). The anatomy of choice: active inference and agency. _Front. Hum. Neurosci._ 7:598. 10.3389/fpsyg.2015.00598
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26029138)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00598)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K..%2BFriston&author=P..%2BSchwartenbeck&author=T..%2BFitzGerald&author=M..%2BMoutoussis&author=T..%2BBehrens&author=R.%2BJ..%2BDolan&publication_year=2013&title=The%2Banatomy%2Bof%2Bchoice%3A%2Bactive%2Binference%2Band%2Bagency.&journal=Front.+Hum.+Neurosci.&volume=7)
    -   [View reference in article](#B38a)
    
-   39
    
    FristonK. J.StephanK. E. (2007). Free-energy and the brain.__Synthese__ 159417–458. 10.1007/s11229-007-9237-y
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/19325932)
    -   [CrossRef](https://doi.org/10.1007/s11229-007-9237-y)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K.%2BJ..%2BFriston&author=K.%2BE..%2BStephan&publication_year=2007&title=Free-energy%2Band%2Bthe%2Bbrain.&journal=Synthese&volume=159&pages=417-458)
    -   [View reference in article](#B39a)
    
-   40
    
    FristonK. J.DaunizeauJ.KilnerJ.KiebelS. J. (2010). Action and behavior: a free-energy formulation. _Biol. Cybern._ 102227–260. 10.1007/s00422-010-0364-z
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/20148260)
    -   [CrossRef](https://doi.org/10.1007/s00422-010-0364-z)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K.%2BJ..%2BFriston&author=J..%2BDaunizeau&author=J..%2BKilner&author=S.%2BJ..%2BKiebel&publication_year=2010&title=Action%2Band%2Bbehavior%3A%2Ba%2Bfree-energy%2Bformulation.&journal=Biol.+Cybern.&volume=102&pages=227-260)
    -   [View reference in article](#B40a)
    
-   41
    
    FristonK. J.StephanK. E.MontagueR.DolanR. J. (2014). Computational psychiatry: the brain as a phantastic organ. _Lancet Psychiatr._ 148–158. 10.1016/s2215-0366(14)70275-5
    
    -   [CrossRef](https://doi.org/10.1016/s2215-0366\(14\)70275-5)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K.%2BJ..%2BFriston&author=K.%2BE..%2BStephan&author=R..%2BMontague&author=R.%2BJ..%2BDolan&publication_year=2014&title=Computational%2Bpsychiatry%3A%2Bthe%2Bbrain%2Bas%2Ba%2Bphantastic%2Borgan.&journal=Lancet+Psychiatr.&pages=148-158)
    -   [View reference in article](#B41a)
    
-   42
    
    FrithC. D. (1987). The positive and negative symptoms of schizophrenia reflect impairments in the perception and initiation of action. _Psychol. Med._ 17631–648. 10.1017/s0033291700025873
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/3628624)
    -   [CrossRef](https://doi.org/10.1017/s0033291700025873)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=C.%2BD..%2BFrith&publication_year=1987&title=The%2Bpositive%2Band%2Bnegative%2Bsymptoms%2Bof%2Bschizophrenia%2Breflect%2Bimpairments%2Bin%2Bthe%2Bperception%2Band%2Binitiation%2Bof%2Baction.&journal=Psychol.+Med.&volume=17&pages=631-648)
    -   [View reference in article](#B42a)
    
-   43
    
    FrithC. D. (2014). __The Cognitive Neuropsychology of Schizophrenia.__ London: Psychology press.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=C.%2BD..%2BFrith&publication_year=2014&journal=The+Cognitive+Neuropsychology+of+Schizophrenia.)
    
-   44
    
    GarfieldJ. L. (2015). “Buddhism and modernity,” in __The Buddhist World__, ed.PowersJ. (London: Routledge), 94–104.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J.%2BL..%2BGarfield&publication_year=2015&title=Buddhism%2Band%2Bmodernity&journal=The+Buddhist+World&pages=94-104)
    
-   45
    
    FuchsT. (2005). Corporealized and disembodied minds: a phenomenological view of the body in melancholia and schizophrenia. _Philos. Psychiatr. Psychol._ 1295–107.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=T..%2BFuchs&publication_year=2005&title=Corporealized%2Band%2Bdisembodied%2Bminds%3A%2Ba%2Bphenomenological%2Bview%2Bof%2Bthe%2Bbody%2Bin%2Bmelancholia%2Band%2Bschizophrenia.&journal=Philos.+Psychiatr.+Psychol.&volume=12&pages=95-107)
    
-   46
    
    GerransP. (2019). Depersonalization disorder, affective processing and predictive coding. _Rev. Philos. Psychol._ 10401–418. 10.1007/s13164-018-0415-2
    
    -   [CrossRef](https://doi.org/10.1007/s13164-018-0415-2)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=P..%2BGerrans&publication_year=2019&title=Depersonalization%2Bdisorder%2C%2Baffective%2Bprocessing%2Band%2Bpredictive%2Bcoding.&journal=Rev.+Philos.+Psychol.&volume=10&pages=401-418)
    
-   47
    
    HaggardP. (2017). Sense of agency in the human brain. _Nat. Rev. Neurosci._ 18:196. 10.1038/nrn.2017.14
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/28251993)
    -   [CrossRef](https://doi.org/10.1038/nrn.2017.14)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=P..%2BHaggard&publication_year=2017&title=Sense%2Bof%2Bagency%2Bin%2Bthe%2Bhuman%2Bbrain.&journal=Nat.+Rev.+Neurosci.&volume=18)
    
-   48
    
    HamiltonS. (2000). __Early Buddhism: A New Approach: The I of the Beholder.__ Richmond: Curzon Press.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S..%2BHamilton&publication_year=2000&journal=Early+Buddhism%3A+A+New+Approach%3A+The+I+of+the+Beholder.)
    
-   49
    
    HarrisS. E. (2018). A nirvana that is burning in Hell: pain and flourishing in mahayana buddhist moral thought.__Sophia__ 57337–347. 10.1007/s11841-017-0619-4
    
    -   [CrossRef](https://doi.org/10.1007/s11841-017-0619-4)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S.%2BE..%2BHarris&publication_year=2018&title=A%2Bnirvana%2Bthat%2Bis%2Bburning%2Bin%2BHell%3A%2Bpain%2Band%2Bflourishing%2Bin%2Bmahayana%2Bbuddhist%2Bmoral%2Bthought.&journal=Sophia&volume=57&pages=337-347)
    
-   50
    
    HespC.SmithR.AllenM.FristonK.RamsteadM. (2019). Deeply felt affect: the emergence of valence in deep active inference.__PsyArXiv__ \[Preprint\], Available online at: [https://psyarxiv.com/62pfd/](https://psyarxiv.com/62pfd/) (accessed December 3, 2019).
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=C..%2BHesp&author=R..%2BSmith&author=M..%2BAllen&author=K..%2BFriston&author=M..%2BRamstead&publication_year=2019&title=Deeply%2Bfelt%2Baffect%3A%2Bthe%2Bemergence%2Bof%2Bvalence%2Bin%2Bdeep%2Bactive%2Binference.&journal=PsyArXiv)
    
-   51
    
    HohwyJ. (2012). Attention and conscious perception in the hypothesis testing brain. _Front. Psychol._ 3:96. 10.3389/fpsyg.2015.00096
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/25741298)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00096)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BHohwy&publication_year=2012&title=Attention%2Band%2Bconscious%2Bperception%2Bin%2Bthe%2Bhypothesis%2Btesting%2Bbrain.&journal=Front.+Psychol.&volume=3)
    
-   52
    
    HohwyJ. (2016). The self-evidencing brain. _Noûs._ 50259–285.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BHohwy&publication_year=2016&title=The%2Bself-evidencing%2Bbrain.&journal=No%C3%BBs.&volume=50&pages=259-285)
    
-   53
    
    HohwyJ.MichaelJ. (2017). “Why should any body have a self?,” in __The Subject’s Matter: Self-Consciousness and the Body__, edsAmsmithA.de vignemontF. (Montréal: MIP Press), 363.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BHohwy&author=J..%2BMichael&publication_year=2017&title=Why%2Bshould%2Bany%2Bbody%2Bhave%2Ba%2Bself%3F&journal=The+Subject%E2%80%99s+Matter%3A+Self-Consciousness+and+the+Body)
    
-   54
    
    HosoyaT.BaccusS. A.MeisterM. (2005). Dynamic predictive coding by the retina.__Nature__ 43671–77. 10.1038/nature03689
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/16001064)
    -   [CrossRef](https://doi.org/10.1038/nature03689)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=T..%2BHosoya&author=S.%2BA..%2BBaccus&author=M..%2BMeister&publication_year=2005&title=Dynamic%2Bpredictive%2Bcoding%2Bby%2Bthe%2Bretina.&journal=Nature&volume=436&pages=71-77)
    
-   55
    
    JamesW. (1890). The perception of reality. _Principles Psychol._ 2283–324.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=W..%2BJames&publication_year=1890&title=The%2Bperception%2Bof%2Breality.&journal=Principles+Psychol.&volume=2&pages=283-324)
    
-   56
    
    JoffilyM.CoricelliG. (2013). Emotional valence and the free-energy principle. _PLoS Comput. Biol._ 9:e03094. 10.1371/journal.pcbi.1003094
    
    -   [CrossRef](https://doi.org/10.1371/journal.pcbi.1003094)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BJoffily&author=G..%2BCoricelli&publication_year=2013&title=Emotional%2Bvalence%2Band%2Bthe%2Bfree-energy%2Bprinciple.&journal=PLoS+Comput.+Biol.&volume=9)
    
-   57
    
    KaplanR.FristonK. J. (2018). Planning and navigation as active inference. _Biol. Cybernet._ 112323–343. 10.1007/s00422-018-0753-2
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/29572721)
    -   [CrossRef](https://doi.org/10.1007/s00422-018-0753-2)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=R..%2BKaplan&author=K.%2BJ..%2BFriston&publication_year=2018&title=Planning%2Band%2Bnavigation%2Bas%2Bactive%2Binference.&journal=Biol.+Cybernet.&volume=112&pages=323-343)
    
-   58
    
    KiebelS. J.DaunizeauJ.FristonK. J. (2008). A hierarchy of time-scales and the brain. _PLoS Comput. Biol._ 4:e1000209. 10.1371/journal.pcbi.1000209
    
    -   [CrossRef](https://doi.org/10.1371/journal.pcbi.1000209)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S.%2BJ..%2BKiebel&author=J..%2BDaunizeau&author=K.%2BJ..%2BFriston&publication_year=2008&title=A%2Bhierarchy%2Bof%2Btime-scales%2Band%2Bthe%2Bbrain.&journal=PLoS+Comput.+Biol.&volume=4)
    
-   59
    
    KiraI. A.AshbyJ. S.OdenatL.LewandowskyL. (2013). The mental health effects of torture trauma and its severity: a replication and extension.__Psychology__ 4472–482. 10.4236/psych.2013.45067
    
    -   [CrossRef](https://doi.org/10.4236/psych.2013.45067)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=I.%2BA..%2BKira&author=J.%2BS..%2BAshby&author=L..%2BOdenat&author=L..%2BLewandowsky&publication_year=2013&title=The%2Bmental%2Bhealth%2Beffects%2Bof%2Btorture%2Btrauma%2Band%2Bits%2Bseverity%3A%2Ba%2Breplication%2Band%2Bextension.&journal=Psychology&volume=4&pages=472-482)
    
-   60
    
    KiversteinJ.MillerM.RietveldE. (2017). The feeling of grip: novelty, error dynamics, and the predictive brain.__Synthese__ 1962847–2869. 10.1007/s11229-017-1583-9
    
    -   [CrossRef](https://doi.org/10.1007/s11229-017-1583-9)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BKiverstein&author=M..%2BMiller&author=E..%2BRietveld&publication_year=2017&title=The%2Bfeeling%2Bof%2Bgrip%3A%2Bnovelty%2C%2Berror%2Bdynamics%2C%2Band%2Bthe%2Bpredictive%2Bbrain.&journal=Synthese&volume=196&pages=2847-2869)
    
-   61
    
    KiversteinJ.MillerM.RietveldE. (2020). How mood tunes prediction: a neurophenomenological account of mood and its disturbance in major depression. _Neurosci. Conscious._ 2020:niaa003. 10.1093/nc/niaa003
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/32818063)
    -   [CrossRef](https://doi.org/10.1093/nc/niaa003)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BKiverstein&author=M..%2BMiller&author=E..%2BRietveld&publication_year=2020&title=How%2Bmood%2Btunes%2Bprediction%3A%2Ba%2Bneurophenomenological%2Baccount%2Bof%2Bmood%2Band%2Bits%2Bdisturbance%2Bin%2Bmajor%2Bdepression.&journal=Neurosci.+Conscious.&volume=2020)
    
-   62
    
    LethebyC.GerransP. (2017). Self unbound: ego dissolution in psychedelic experience. _Neurosci. Conscious._ 3:nix016. 10.1093/nc/nix016
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/30042848)
    -   [CrossRef](https://doi.org/10.1093/nc/nix016)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=C..%2BLetheby&author=P..%2BGerrans&publication_year=2017&title=Self%2Bunbound%3A%2Bego%2Bdissolution%2Bin%2Bpsychedelic%2Bexperience.&journal=Neurosci.+Conscious.&volume=3)
    
-   63
    
    LimanowskiJ.BlankenburgF. (2013). Minimal self-models and the free energy principle. _Front. Hum. Neurosci._ 7:547. 10.3389/fpsyg.2015.00547
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/25972834)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00547)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J..%2BLimanowski&author=F..%2BBlankenburg&publication_year=2013&title=Minimal%2Bself-models%2Band%2Bthe%2Bfree%2Benergy%2Bprinciple.&journal=Front.+Hum.+Neurosci.&volume=7)
    
-   64
    
    LindahlJ. R.BrittonW. B. (2019). ‘I have this feeling of not really being here’: buddhist meditation and changes in sense of self. _J. Conscious. Stud._ 26157–183.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=J.%2BR..%2BLindahl&author=W.%2BB..%2BBritton&publication_year=2019&title=%E2%80%98I%2Bhave%2Bthis%2Bfeeling%2Bof%2Bnot%2Breally%2Bbeing%2Bhere%E2%80%99%3A%2Bbuddhist%2Bmeditation%2Band%2Bchanges%2Bin%2Bsense%2Bof%2Bself.&journal=J.+Conscious.+Stud.&volume=26&pages=157-183)
    
-   65
    
    LinsonA.ParrT.FristonK. J. (2020). Active inference, stressors, and psychological trauma: a neuroethological model of (mal) adaptive explore-exploit dynamics in ecological context. _Behav. Brain Res._ 380:112421. 10.1016/j.bbr.2019.112421
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/31830495)
    -   [CrossRef](https://doi.org/10.1016/j.bbr.2019.112421)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A..%2BLinson&author=T..%2BParr&author=K.%2BJ..%2BFriston&publication_year=2020&title=Active%2Binference%2C%2Bstressors%2C%2Band%2Bpsychological%2Btrauma%3A%2Ba%2Bneuroethological%2Bmodel%2Bof%2B%28mal%29%2Badaptive%2Bexplore-exploit%2Bdynamics%2Bin%2Becological%2Bcontext.&journal=Behav.+Brain+Res.&volume=380)
    
-   66
    
    LofthouseG. (2014). __Enlightenment’s Evil Twin.__ Available online at: [http://www.theatlantic.com/health/archive/2014/12/enlightenments-eviltwin/383726/](http://www.theatlantic.com/health/archive/2014/12/enlightenments-eviltwin/383726/) (accessed February, 25 2020).
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BLofthouse&publication_year=2014&journal=Enlightenment%E2%80%99s+Evil+Twin.)
    
-   67
    
    LutzA.MattoutJ.PagnoniG. (2019). The epistemic and pragmatic value of non-action: a predictive coding perspective on meditation. _Curr. Opin. Psychol._ 28166–171. 10.1016/j.copsyc.2018.12.019
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/30711914)
    -   [CrossRef](https://doi.org/10.1016/j.copsyc.2018.12.019)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A..%2BLutz&author=J..%2BMattout&author=G..%2BPagnoni&publication_year=2019&title=The%2Bepistemic%2Band%2Bpragmatic%2Bvalue%2Bof%2Bnon-action%3A%2Ba%2Bpredictive%2Bcoding%2Bperspective%2Bon%2Bmeditation.&journal=Curr.+Opin.+Psychol.&volume=28&pages=166-171)
    
-   68
    
    MacLeodC.RutherfordE.CampbellL.EbsworthyG.HolkerL. (2002). Selective attention and emotional vulnerability: assessing the causal basis of their association through the experimental manipulation of attentional bias. _J. Abnorm. Psychol._ 111:107. 10.1037/0021-843x.111.1.107
    
    -   [CrossRef](https://doi.org/10.1037/0021-843x.111.1.107)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=C..%2BMacLeod&author=E..%2BRutherford&author=L..%2BCampbell&author=G..%2BEbsworthy&author=L..%2BHolker&publication_year=2002&title=Selective%2Battention%2Band%2Bemotional%2Bvulnerability%3A%2Bassessing%2Bthe%2Bcausal%2Bbasis%2Bof%2Btheir%2Bassociation%2Bthrough%2Bthe%2Bexperimental%2Bmanipulation%2Bof%2Battentional%2Bbias.&journal=J.+Abnorm.+Psychol.&volume=111)
    
-   69
    
    MatthewsG. A.TyeK. M. (2019). Neural mechanisms of social homeostasis. _Ann. N. Y. Acad. Sci._ 14575–25. 10.1111/nyas.14016
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/30875095)
    -   [CrossRef](https://doi.org/10.1111/nyas.14016)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G.%2BA..%2BMatthews&author=K.%2BM..%2BTye&publication_year=2019&title=Neural%2Bmechanisms%2Bof%2Bsocial%2Bhomeostasis.&journal=Ann.+N.+Y.+Acad.+Sci.&volume=1457&pages=5-25)
    
-   70
    
    McNallyR. J. (2018). Attentional bias for threat: crisis or opportunity? _Clin. Psychol. Rev._ 694–13. 10.1016/j.cpr.2018.05.005
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/29853421)
    -   [CrossRef](https://doi.org/10.1016/j.cpr.2018.05.005)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=R.%2BJ..%2BMcNally&publication_year=2018&title=Attentional%2Bbias%2Bfor%2Bthreat%3A%2Bcrisis%2Bor%2Bopportunity%3F&journal=Clin.+Psychol.+Rev.&volume=69&pages=4-13)
    
-   71
    
    MedfordN. (2012). Emotion and the unreal self: depersonalization disorder and de-affectualization. _Emot. Rev._ 4139–144. 10.1177/1754073911430135
    
    -   [CrossRef](https://doi.org/10.1177/1754073911430135)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=N..%2BMedford&publication_year=2012&title=Emotion%2Band%2Bthe%2Bunreal%2Bself%3A%2Bdepersonalization%2Bdisorder%2Band%2Bde-affectualization.&journal=Emot.+Rev.&volume=4&pages=139-144)
    
-   72
    
    MedfordN.BrierleyB.BrammerM.BullmoreE. T.DavidA. S.PhillipsM. L. (2006). Emotional memory in depersonalization disorder: a functional MRI study. _Psychiatry Res. Neuroimag._ 14893–102. 10.1016/j.pscychresns.2006.05.007
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/17085021)
    -   [CrossRef](https://doi.org/10.1016/j.pscychresns.2006.05.007)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=N..%2BMedford&author=B..%2BBrierley&author=M..%2BBrammer&author=E.%2BT..%2BBullmore&author=A.%2BS..%2BDavid&author=M.%2BL..%2BPhillips&publication_year=2006&title=Emotional%2Bmemory%2Bin%2Bdepersonalization%2Bdisorder%3A%2Ba%2Bfunctional%2BMRI%2Bstudy.&journal=Psychiatry+Res.+Neuroimag.&volume=148&pages=93-102)
    
-   73
    
    MedfordN.SierraM.BakerD.DavidA. S. (2005). Understanding and treating depersonalisation disorder.__Adv. Psychiatr. Treat__ 1192–100. 10.1192/apt.11.2.92
    
    -   [CrossRef](https://doi.org/10.1192/apt.11.2.92)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=N..%2BMedford&author=M..%2BSierra&author=D..%2BBaker&author=A.%2BS..%2BDavid&publication_year=2005&title=Understanding%2Band%2Btreating%2Bdepersonalisation%2Bdisorder.&journal=Adv.+Psychiatr.+Treat&volume=11&pages=92-100)
    
-   74
    
    MedfordN.SierraM.StringarisA.GiampietroV.BrammerM. J.DavidA. S. (2016). Emotional experience and awareness of self: functional MRI studies of depersonalization disorder. _Front. Psychol._ 7:432. 10.3389/fpsyg.2015.00432
    
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00432)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=N..%2BMedford&author=M..%2BSierra&author=A..%2BStringaris&author=V..%2BGiampietro&author=M.%2BJ..%2BBrammer&author=A.%2BS..%2BDavid&publication_year=2016&title=Emotional%2Bexperience%2Band%2Bawareness%2Bof%2Bself%3A%2Bfunctional%2BMRI%2Bstudies%2Bof%2Bdepersonalization%2Bdisorder.&journal=Front.+Psychol.&volume=7)
    
-   75
    
    MetzingerT. (2003). Phenomenal transparency and cognitive self-reference. _Phenomenol. Cogn. Sci._ 2353–393. 10.1023/b:phen.0000007366.42918.eb
    
    -   [CrossRef](https://doi.org/10.1023/b:phen.0000007366.42918.eb)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=T..%2BMetzinger&publication_year=2003&title=Phenomenal%2Btransparency%2Band%2Bcognitive%2Bself-reference.&journal=Phenomenol.+Cogn.+Sci.&volume=2&pages=353-393)
    
-   76
    
    MiallR. C.WolpertD. M. (1996). Forward models for physiological motor control. _Neural Netw._ 91265–1279. 10.1016/s0893-6080(96)00035-4
    
    -   [CrossRef](https://doi.org/10.1016/s0893-6080\(96\)00035-4)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=R.%2BC..%2BMiall&author=D.%2BM..%2BWolpert&publication_year=1996&title=Forward%2Bmodels%2Bfor%2Bphysiological%2Bmotor%2Bcontrol.&journal=Neural+Netw.&volume=9&pages=1265-1279)
    
-   77
    
    MillerM.ClarkA. (2017). Happily entangled: prediction, emotion, and the embodied mind.__Synthese__ 1952559–2575. 10.1007/s11229-017-1399-7
    
    -   [CrossRef](https://doi.org/10.1007/s11229-017-1399-7)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BMiller&author=A..%2BClark&publication_year=2017&title=Happily%2Bentangled%3A%2Bprediction%2C%2Bemotion%2C%2Band%2Bthe%2Bembodied%2Bmind.&journal=Synthese&volume=195&pages=2559-2575)
    
-   78
    
    MillerM.KiversteinJ.RietveldE. K. (2020). Embodying addiction: a predictive processing framework. _Brain Cogn._ 138:105495. 10.1016/j.bandc.2019.105495
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/31877434)
    -   [CrossRef](https://doi.org/10.1016/j.bandc.2019.105495)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BMiller&author=J..%2BKiverstein&author=E.%2BK..%2BRietveld&publication_year=2020&title=Embodying%2Baddiction%3A%2Ba%2Bpredictive%2Bprocessing%2Bframework.&journal=Brain+Cogn.&volume=138)
    
-   79
    
    MillièreR. (2017). Looking for the self: phenomenology, neurophysiology and philosophical significance of drug-induced ego dissolution. _Front. Hum. Neurosci._ 11:245. 10.3389/fnhum.2016.00245
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/27252642)
    -   [CrossRef](https://doi.org/10.3389/fnhum.2016.00245)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=R..%2BMilli%C3%A8re&publication_year=2017&title=Looking%2Bfor%2Bthe%2Bself%3A%2Bphenomenology%2C%2Bneurophysiology%2Band%2Bphilosophical%2Bsignificance%2Bof%2Bdrug-induced%2Bego%2Bdissolution.&journal=Front.+Hum.+Neurosci.&volume=11)
    
-   80
    
    MillièreR.Carhart-HarrisR. L.RosemanL.TrautweinF. M.Berkovich-OhanaA. (2018). Psychedelics, meditation, and self-consciousness. _Front. Psychol._ 9:1475. 10.3389/fnhum.2016.001475
    
    -   [CrossRef](https://doi.org/10.3389/fnhum.2016.001475)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=R..%2BMilli%C3%A8re&author=R.%2BL..%2BCarhart-Harris&author=L..%2BRoseman&author=F.%2BM..%2BTrautwein&author=A..%2BBerkovich-Ohana&publication_year=2018&title=Psychedelics%2C%2Bmeditation%2C%2Band%2Bself-consciousness.&journal=Front.+Psychol.&volume=9)
    
-   81
    
    MirzaM. B.AdamsR. A.MathysC. D.FristonK. J. (2016). Scene construction, visual foraging, and active inference. _Front. Comput. Neurosci._ 10:56. 10.3389/fnhum.2016.00056
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26941633)
    -   [CrossRef](https://doi.org/10.3389/fnhum.2016.00056)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M.%2BB..%2BMirza&author=R.%2BA..%2BAdams&author=C.%2BD..%2BMathys&author=K.%2BJ..%2BFriston&publication_year=2016&title=Scene%2Bconstruction%2C%2Bvisual%2Bforaging%2C%2Band%2Bactive%2Binference.&journal=Front.+Comput.+Neurosci.&volume=10)
    
-   82
    
    MoutoussisM.FearonP.El-DeredyW.DolanR. J.FristonK. J. (2014). Bayesian inferences about the self (and others): a review. _Conscious. Cogn._ 2567–76. 10.1016/j.concog.2014.01.009
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/24583455)
    -   [CrossRef](https://doi.org/10.1016/j.concog.2014.01.009)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BMoutoussis&author=P..%2BFearon&author=W..%2BEl-Deredy&author=R.%2BJ..%2BDolan&author=K.%2BJ..%2BFriston&publication_year=2014&title=Bayesian%2Binferences%2Babout%2Bthe%2Bself%2B%28and%2Bothers%29%3A%2Ba%2Breview.&journal=Conscious.+Cogn.&volume=25&pages=67-76)
    
-   83
    
    ÑānamoliB.BodhiB. (1995). __The Middle Length Discourses of the Buddha.__ Boston, MA: Wisdom.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=B..%2B%C3%91%C4%81namoli&author=B..%2BBodhi&publication_year=1995&journal=The+Middle+Length+Discourses+of+the+Buddha.)
    
-   84
    
    OngaroG.KaptchukT. J. (2019). Symptom perception, placebo effects, and the Bayesian brain.__Pain__ 1601–4. 10.1097/00006396-900000000-98882
    
    -   [CrossRef](https://doi.org/10.1097/00006396-900000000-98882)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BOngaro&author=T.%2BJ..%2BKaptchuk&publication_year=2019&title=Symptom%2Bperception%2C%2Bplacebo%2Beffects%2C%2Band%2Bthe%2BBayesian%2Bbrain.&journal=Pain&volume=160&pages=1-4)
    
-   85
    
    PagnoniG.GuareschiF. T. (2015). Remembrance of things to come: a conversation between Zen and neuroscience on the predictive nature of the mind.__Mindfulness__ 827–37. 10.1007/s12671-015-0438-z
    
    -   [CrossRef](https://doi.org/10.1007/s12671-015-0438-z)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BPagnoni&author=F.%2BT..%2BGuareschi&publication_year=2015&title=Remembrance%2Bof%2Bthings%2Bto%2Bcome%3A%2Ba%2Bconversation%2Bbetween%2BZen%2Band%2Bneuroscience%2Bon%2Bthe%2Bpredictive%2Bnature%2Bof%2Bthe%2Bmind.&journal=Mindfulness&volume=8&pages=27-37)
    
-   86
    
    PezzuloG. (2014). Why do you fear the bogeyman? An embodied predictive coding model of perceptual inference. _Cogn. Affect. Behav. Neurosci._ 14902–911. 10.3758/s13415-013-0227-x
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/24307092)
    -   [CrossRef](https://doi.org/10.3758/s13415-013-0227-x)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BPezzulo&publication_year=2014&title=Why%2Bdo%2Byou%2Bfear%2Bthe%2Bbogeyman%3F%2BAn%2Bembodied%2Bpredictive%2Bcoding%2Bmodel%2Bof%2Bperceptual%2Binference.&journal=Cogn.+Affect.+Behav.+Neurosci.&volume=14&pages=902-911)
    
-   87
    
    PezzuloG. (2018). Commentary: the problem of mental action: predictive control without sensory sheets. _Front. Psychol._ 9:1291. 10.3389/fnhum.2016.001291
    
    -   [CrossRef](https://doi.org/10.3389/fnhum.2016.001291)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BPezzulo&publication_year=2018&title=Commentary%3A%2Bthe%2Bproblem%2Bof%2Bmental%2Baction%3A%2Bpredictive%2Bcontrol%2Bwithout%2Bsensory%2Bsheets.&journal=Front.+Psychol.&volume=9)
    
-   88
    
    PezzuloG.CisekP. (2016). Navigating the affordance landscape: feedback control as a process model of behavior and cognition. _Trends Cogn. Sci._ 20414–424. 10.1016/j.tics.2016.03.013
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/27118642)
    -   [CrossRef](https://doi.org/10.1016/j.tics.2016.03.013)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BPezzulo&author=P..%2BCisek&publication_year=2016&title=Navigating%2Bthe%2Baffordance%2Blandscape%3A%2Bfeedback%2Bcontrol%2Bas%2Ba%2Bprocess%2Bmodel%2Bof%2Bbehavior%2Band%2Bcognition.&journal=Trends+Cogn.+Sci.&volume=20&pages=414-424)
    
-   89
    
    PezzuloG.NolfiS. (2019). Making the environment an informative place: a conceptual analysis of epistemic policies and sensorimotor coordination.__Entropy__ 21:350. 10.3390/e21040350
    
    -   [CrossRef](https://doi.org/10.3390/e21040350)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BPezzulo&author=S..%2BNolfi&publication_year=2019&title=Making%2Bthe%2Benvironment%2Ban%2Binformative%2Bplace%3A%2Ba%2Bconceptual%2Banalysis%2Bof%2Bepistemic%2Bpolicies%2Band%2Bsensorimotor%2Bcoordination.&journal=Entropy&volume=21)
    
-   90
    
    PezzuloG.RigoliF.FristonK. (2015). Active Inference, homeostatic regulation and adaptive behavioural control. _Prog. Neurobiol._ 13417–35. 10.1016/j.pneurobio.2015.09.001
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26365173)
    -   [CrossRef](https://doi.org/10.1016/j.pneurobio.2015.09.001)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BPezzulo&author=F..%2BRigoli&author=K..%2BFriston&publication_year=2015&title=Active%2BInference%2C%2Bhomeostatic%2Bregulation%2Band%2Badaptive%2Bbehavioural%2Bcontrol.&journal=Prog.+Neurobiol.&volume=134&pages=17-35)
    
-   91
    
    PezzuloG.RigoliF.FristonK. J. (2018). Hierarchical active inference: a theory of motivated control. _Trends Cogn. Sci._ 22294–306. 10.1016/j.tics.2018.01.009
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/29475638)
    -   [CrossRef](https://doi.org/10.1016/j.tics.2018.01.009)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=G..%2BPezzulo&author=F..%2BRigoli&author=K.%2BJ..%2BFriston&publication_year=2018&title=Hierarchical%2Bactive%2Binference%3A%2Ba%2Btheory%2Bof%2Bmotivated%2Bcontrol.&journal=Trends+Cogn.+Sci.&volume=22&pages=294-306)
    
-   92
    
    RadovicF.RadovicS. (2002). Feelings of unreality: a conceptual and phenomenological analysis of the language of depersonalization. _Philos. Psychiatr. Psychol._ 9271–279. 10.1353/ppp.2003.0048
    
    -   [CrossRef](https://doi.org/10.1353/ppp.2003.0048)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=F..%2BRadovic&author=S..%2BRadovic&publication_year=2002&title=Feelings%2Bof%2Bunreality%3A%2Ba%2Bconceptual%2Band%2Bphenomenological%2Banalysis%2Bof%2Bthe%2Blanguage%2Bof%2Bdepersonalization.&journal=Philos.+Psychiatr.+Psychol.&volume=9&pages=271-279)
    
-   93
    
    RidderinkhofK. R.Van Den WildenbergW. P.SegalowitzS. J.CarterC. S. (2004). Neurocognitive mechanisms of cognitive control: the role of prefrontal cortex in action selection, response inhibition, performance monitoring, and reward-based learning. _Brain Cogn._ 56129–140. 10.1016/j.bandc.2004.09.016
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/15518930)
    -   [CrossRef](https://doi.org/10.1016/j.bandc.2004.09.016)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K.%2BR..%2BRidderinkhof&author=W.%2BP..%2BVan%2BDen%2BWildenberg&author=S.%2BJ..%2BSegalowitz&author=C.%2BS..%2BCarter&publication_year=2004&title=Neurocognitive%2Bmechanisms%2Bof%2Bcognitive%2Bcontrol%3A%2Bthe%2Brole%2Bof%2Bprefrontal%2Bcortex%2Bin%2Baction%2Bselection%2C%2Bresponse%2Binhibition%2C%2Bperformance%2Bmonitoring%2C%2Band%2Breward-based%2Blearning.&journal=Brain+Cogn.&volume=56&pages=129-140)
    
-   94
    
    SassL. A.ParnasJ. (2003). Schizophrenia, consciousness, and the self. _Schizophr. Bull._ 29427–444. 10.1093/oxfordjournals.schbul.a007017
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/14609238)
    -   [CrossRef](https://doi.org/10.1093/oxfordjournals.schbul.a007017)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=L.%2BA..%2BSass&author=J..%2BParnas&publication_year=2003&title=Schizophrenia%2C%2Bconsciousness%2C%2Band%2Bthe%2Bself.&journal=Schizophr.+Bull.&volume=29&pages=427-444)
    
-   95
    
    SchwartenbeckP.FitzGeraldT.DolanR.FristonK. (2013). Exploration, novelty, surprise, and free energy minimization. _Front. Psychol._ 4:710. 10.3389/fpsyg.2015.00710
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/26074854)
    -   [CrossRef](https://doi.org/10.3389/fpsyg.2015.00710)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=P..%2BSchwartenbeck&author=T..%2BFitzGerald&author=R..%2BDolan&author=K..%2BFriston&publication_year=2013&title=Exploration%2C%2Bnovelty%2C%2Bsurprise%2C%2Band%2Bfree%2Benergy%2Bminimization.&journal=Front.+Psychol.&volume=4)
    
-   96
    
    SegalS. (2002). __Collision with the Infinite: A Life Beyond the Personal Self.__ London: New Age Books.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S..%2BSegal&publication_year=2002&journal=Collision+with+the+Infinite%3A+A+Life+Beyond+the+Personal+Self.)
    
-   97
    
    SethA. K. (2013). Interoceptive inference, emotion, and the embodied self. _Trends Cogn. Sci._ 17565–573. 10.1016/j.tics.2013.09.007
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/24126130)
    -   [CrossRef](https://doi.org/10.1016/j.tics.2013.09.007)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BK..%2BSeth&publication_year=2013&title=Interoceptive%2Binference%2C%2Bemotion%2C%2Band%2Bthe%2Bembodied%2Bself.&journal=Trends+Cogn.+Sci.&volume=17&pages=565-573)
    
-   98
    
    SethA. K. (2014). __The Cybernetic Bayesian Brain.__ Frankfurt: MIND Group.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BK..%2BSeth&publication_year=2014&journal=The+Cybernetic+Bayesian+Brain.)
    
-   99
    
    SethA. K.FristonK. J. (2016). Active interoceptive inference and the emotional brain. _Philos. Trans. R. Soc. B Biol. Sci._ 371:20160007. 10.1098/rstb.2016.0007
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/28080966)
    -   [CrossRef](https://doi.org/10.1098/rstb.2016.0007)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BK..%2BSeth&author=K.%2BJ..%2BFriston&publication_year=2016&title=Active%2Binteroceptive%2Binference%2Band%2Bthe%2Bemotional%2Bbrain.&journal=Philos.+Trans.+R.+Soc.+B+Biol.+Sci.&volume=371)
    
-   100
    
    SethA. K.SuzukiK.CritchleyH. D. (2012). An interoceptive predictive coding model of conscious presence. _Front. Psychol._ 2:395. 10.3389/fnhum.2016.00395
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/27540360)
    -   [CrossRef](https://doi.org/10.3389/fnhum.2016.00395)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BK..%2BSeth&author=K..%2BSuzuki&author=H.%2BD..%2BCritchley&publication_year=2012&title=An%2Binteroceptive%2Bpredictive%2Bcoding%2Bmodel%2Bof%2Bconscious%2Bpresence.&journal=Front.+Psychol.&volume=2)
    
-   101
    
    SethA. K.TsakirisM. (2018). Being a beast machine: the somatic basis of selfhood. _Trends Cogn. Sci._ 22969–981. 10.1016/j.tics.2018.08.008
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/30224233)
    -   [CrossRef](https://doi.org/10.1016/j.tics.2018.08.008)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=A.%2BK..%2BSeth&author=M..%2BTsakiris&publication_year=2018&title=Being%2Ba%2Bbeast%2Bmachine%3A%2Bthe%2Bsomatic%2Bbasis%2Bof%2Bselfhood.&journal=Trends+Cogn.+Sci.&volume=22&pages=969-981)
    
-   102
    
    ShulmanE. (2014). __Rethinking the Buddha: Early Buddhist Philosophy as Meditative Perception.__ Cambridge: Cambridge University Press.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=E..%2BShulman&publication_year=2014&journal=Rethinking+the+Buddha%3A+Early+Buddhist+Philosophy+as+Meditative+Perception.)
    
-   103
    
    SierraM.BerriosG. E. (1998). Depersonalization: neurobiological perspectives.__Biol. Psychiatry__ 44898–908. 10.1016/s0006-3223(98)00015-8
    
    -   [CrossRef](https://doi.org/10.1016/s0006-3223\(98\)00015-8)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BSierra&author=G.%2BE..%2BBerrios&publication_year=1998&title=Depersonalization%3A%2Bneurobiological%2Bperspectives.&journal=Biol.+Psychiatry&volume=44&pages=898-908)
    
-   104
    
    SierraM.DavidA. S. (2011). Depersonalization: a selective impairment of self-awareness. _Conscious. Cogn._ 2099–108. 10.1016/j.concog.2010.10.018
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/21087873)
    -   [CrossRef](https://doi.org/10.1016/j.concog.2010.10.018)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BSierra&author=A.%2BS..%2BDavid&publication_year=2011&title=Depersonalization%3A%2Ba%2Bselective%2Bimpairment%2Bof%2Bself-awareness.&journal=Conscious.+Cogn.&volume=20&pages=99-108)
    
-   105
    
    SierraM.BakerD.MedfordN.DavidA. S. (2005). Unpacking the depersonalization syndrome: an exploratory factor analysis on the Cambridge Depersonalization Scale. _Psychol. Med._ 351523–1532. 10.1017/S0033291705005325
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/16164776)
    -   [CrossRef](https://doi.org/10.1017/S0033291705005325)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=M..%2BSierra&author=D..%2BBaker&author=N..%2BMedford&author=A.%2BS..%2BDavid&publication_year=2005&title=Unpacking%2Bthe%2Bdepersonalization%2Bsyndrome%3A%2Ban%2Bexploratory%2Bfactor%2Banalysis%2Bon%2Bthe%2BCambridge%2BDepersonalization%2BScale.&journal=Psychol.+Med.&volume=35&pages=1523-1532)
    
-   106
    
    SimeonD.AbugelJ. (2006). __Feeling Unreal: Depersonalization Disorder and the Loss of the Self.__ Oxford: Oxford University Press.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=D..%2BSimeon&author=J..%2BAbugel&publication_year=2006&journal=Feeling+Unreal%3A+Depersonalization+Disorder+and+the+Loss+of+the+Self.)
    
-   107
    
    SimeonD.KozinD. S.SegalK.LerchB.DujourR.GiesbrechtT. (2008). De-constructing depersonalization: further evidence for symptom clusters. _Psychiatry Res._ 157303–306. 10.1016/j.psychres.2007.07.007
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/17959254)
    -   [CrossRef](https://doi.org/10.1016/j.psychres.2007.07.007)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=D..%2BSimeon&author=D.%2BS..%2BKozin&author=K..%2BSegal&author=B..%2BLerch&author=R..%2BDujour&author=T..%2BGiesbrecht&publication_year=2008&title=De-constructing%2Bdepersonalization%3A%2Bfurther%2Bevidence%2Bfor%2Bsymptom%2Bclusters.&journal=Psychiatry+Res.&volume=157&pages=303-306)
    
-   108
    
    SmithL. S.HespC.LutzA.MattoutJ.FristonK.RamsteadM. (2020). Towards a formal neurophenomenology of metacognition: modelling meta-awareness, mental action, and attentional control with deep active inference.__PsyArXiv.__\[Preprint\]. Available online at: [https://psyarxiv.com/5jh3c/](https://psyarxiv.com/5jh3c/)
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=L.%2BS..%2BSmith&author=C..%2BHesp&author=A..%2BLutz&author=J..%2BMattout&author=K..%2BFriston&author=M..%2BRamstead&publication_year=2020&title=Towards%2Ba%2Bformal%2Bneurophenomenology%2Bof%2Bmetacognition%3A%2Bmodelling%2Bmeta-awareness%2C%2Bmental%2Baction%2C%2Band%2Battentional%2Bcontrol%2Bwith%2Bdeep%2Bactive%2Binference.&journal=PsyArXiv.)
    
-   109
    
    StephanK. E.ManjalyZ. M.MathysC. D.WeberL. A.PaliwalS.GardT.et al (2016). Allostatic self-efficacy: a metacognitive theory of dyshomeostasis-induced fatigue and depression. _Front. Hum. Neurosci._ 10:550. 10.3389/fnhum.2016.00550
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/27895566)
    -   [CrossRef](https://doi.org/10.3389/fnhum.2016.00550)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=K.%2BE..%2BStephan&author=Z.%2BM..%2BManjaly&author=C.%2BD..%2BMathys&author=L.%2BA..%2BWeber&author=S..%2BPaliwal&author=T..%2BGard&publication_year=2016&title=Allostatic%2Bself-efficacy%3A%2Ba%2Bmetacognitive%2Btheory%2Bof%2Bdyshomeostasis-induced%2Bfatigue%2Band%2Bdepression.&journal=Front.+Hum.+Neurosci.&volume=10)
    
-   110
    
    SterlingP. (2012). Allostasis: a model of predictive regulation. _Physiol. Behav._ 1065–15. 10.1016/j.physbeh.2011.06.004
    
    -   [Pubmed Abstract](https://pubmed.ncbi.nlm.nih.gov/21684297)
    -   [CrossRef](https://doi.org/10.1016/j.physbeh.2011.06.004)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=P..%2BSterling&publication_year=2012&title=Allostasis%3A%2Ba%2Bmodel%2Bof%2Bpredictive%2Bregulation.&journal=Physiol.+Behav.&volume=106&pages=5-15)
    
-   111
    
    Van de CruysS. (2017). __Affective Value in the Predictive Mind.__ Frankfurt: MIND Group.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S..%2BVan%2Bde%2BCruys&publication_year=2017&journal=Affective+Value+in+the+Predictive+Mind.)
    
-   112
    
    WilkinsonS.DeaneG.NaveK.ClarkA. (2019). “Getting warmer: predictive processing and the nature of emotion,” in __The Value of Emotions for Knowledge__ (Cham: Palgrave Macmillan), 101–119. 10.1007/978-3-030-15667-1\_5
    
    -   [CrossRef](https://doi.org/10.1007/978-3-030-15667-1_5)
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=S..%2BWilkinson&author=G..%2BDeane&author=K..%2BNave&author=A..%2BClark&publication_year=2019&title=Getting%2Bwarmer%3A%2Bpredictive%2Bprocessing%2Band%2Bthe%2Bnature%2Bof%2Bemotion&journal=The+Value+of+Emotions+for+Knowledge&pages=101-119)
    
-   113
    
    WolpertD. M.FlanaganJ. R. (2001). Motor prediction. _Curr. Biol._ 11R729–R732.
    
    -   [Google Scholar](http://scholar.google.com/scholar_lookup?author=D.%2BM..%2BWolpert&author=J.%2BR..%2BFlanagan&publication_year=2001&title=Motor%2Bprediction.&journal=Curr.+Biol.&volume=11&pages=R729-R732)

:::

[^note-1]: See for a recent phenomenological account of depersonalization and meditative insight.
[^note-2]: For an excellent account of the neuroscience supporting the role of affect (including valence and arousal) in simultaneously tracking the relationship between the organism and the environment, and preparing the organism to make improvements to that relationship, see Lisa Feldman-Barrett’s work (2017).
[^note-3]: Thanks to Lars Sandved-Smith for discussions about the computational nature of depersonalization.
[^note-4]: Interestingly, this account is suggestive that the hyperreflective tendency to check one’s body and one’s current state common in people suffering from depersonalization () could be understood as compensatory behavior aimed at reducing the uncertainty relating to the perceived loss of control over interoceptive states.
[^note-5]: For a neuroscientific account of this relationship between identification and motivation, see.
[^note-6]: See for a computational model of this process.
[^note-7]: Notice here that the common phenomenology of long-term meditators being able to simply “let go” of mental and emotional distractions is closely related to the _increase_ in control that we are proposing this meditative process engenders.
[^note-8]: See for reasons why that might be challenging.
[^note-9]: See also and for clear accounts of the relationship between meditation and depersonalization.
[^cite-10]: Kiverstein J., Miller M., Rietveld E. (2020). How mood tunes prediction: a neurophenomenological account of mood and its disturbance in major depression. _Neurosci. Conscious._ 2020:niaa003. [10.1093/nc/niaa003](https://doi.org/10.1093/nc/niaa003)
[^cite-11]: Pezzulo G., Rigoli F., Friston K. J. (2018). Hierarchical active inference: a theory of motivated control. _Trends Cogn. Sci._ 22, 294–306. [10.1016/j.tics.2018.01.009](https://doi.org/10.1016/j.tics.2018.01.009)
