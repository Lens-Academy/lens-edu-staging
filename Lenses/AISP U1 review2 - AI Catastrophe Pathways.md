---
id: 'f77cdbf3-98ec-4d15-9e85-2b9f72a222c5'
title: "How Could AI Cause Catastrophe?"
tldr: "AI catastrophe is a set of pathways, not one story. Misuse, competitive pressure, institutional failure, loss of control, gradual disempowerment, and accumulative collapse call for different evidence and different interventions."
summary_for_tutor: "Maps major catastrophic-AI pathways using the supplied readings. The learner should separate malicious use, race dynamics, organizational failure, rogue AI, gradual disempowerment, and accumulative systemic risk, then identify where those pathways interact."
reading_minutes: 27
tutor_minutes: 22
tags:
  - wip
---

#### Text
content::
\## Start with the pathway, not the label

"AI could cause catastrophe" is not one argument. It can describe a malicious person using a highly capable system, a military race that rewards unsafe automation, a laboratory with weak safety processes, an autonomous system that pursues an objective humans cannot control, a gradual loss of human influence over major institutions, or a long sequence of smaller disruptions that makes society increasingly fragile.

These pathways overlap, but they are not interchangeable. A safeguard against hidden long-term goals can matter for a rogue-agent scenario and do almost nothing against a malicious user. A governance agreement can reduce race pressure while leaving a poorly secured laboratory vulnerable to theft. A model can be perfectly obedient to its operator while still helping that operator do something catastrophic.

A useful high-level taxonomy groups catastrophic risks into malicious use, AI race dynamics, organizational risks, and rogue AI systems.[^cite-hendrycks-2023] Newer work adds slower structural pathways such as gradual disempowerment and accumulative collapse.[^cite-kulveit-2025][^cite-kasirzadeh-2025] The categories are learning tools. Their purpose is to make us ask what actually causes what.

\## Malicious use

In a malicious-use pathway, the AI does not need to resist human control. The system can faithfully help a person or organization pursue a dangerous goal. More capable AI could lower the expertise, time, or resources required for cyberattacks, biological misuse, mass surveillance, persuasion, or other forms of coercion.[^cite-hendrycks-2023]

The relevant questions concern access and amplification. Who can use the capability? What complementary resources are still needed? Does the system merely speed up a task that many actors can already perform, or does it make a previously inaccessible capability widely available? Can defenders use the same technology to improve security? How detectable is misuse?

This pathway exposes an important distinction that later units will examine in detail. A system can be aligned with a user's request and still be unsafe in a broader moral or political sense. "Does what the operator wants" and "produces outcomes society should accept" are separate properties.

Malicious use also changes how we think about model release. A capability can be manageable when a small, accountable group has access and dangerous when it is widely distributed. The opposite can also happen: wider access can improve independent scrutiny and defensive research. The safety question is therefore tied to both capability and institutional context.

\## Race dynamics

Some catastrophic pathways require no actor to prefer the dangerous outcome. Competition can make individually understandable choices produce a collectively bad equilibrium.

Imagine two laboratories that both prefer to test thoroughly before deployment. Each also believes that waiting six months could hand a decisive market advantage to the other. If being second is very costly, both can rush even though both would prefer a world where everyone moved more slowly. A similar structure can appear between states. Military organizations may automate decision-making because they fear that slower systems will lose against an opponent using faster ones.[^cite-hendrycks-2023]

This is a coordination problem. Changing the preferences of one actor may not solve it if the actor still faces incentives that punish caution. Safety work can therefore involve standards, verification, liability, treaties, information sharing, or institutions that change the payoff structure faced by all participants.

Race dynamics can also change the value of technical safeguards. A safety technique that is expensive or slows deployment may be difficult to adopt voluntarily when competition is intense. A cheaper technique can have more practical impact even if it is technically weaker. The institutional environment affects which safety measures survive contact with incentives.

The pathway can interact with several others. Racing can weaken organizational safety. It can increase model access and misuse. It can encourage delegation to autonomous systems. It can make later intervention politically harder because national security or economic dependence has grown around the technology.

\## Organizational failure

Complex organizations can create serious accidents without anyone intending catastrophe. Safety warnings can be suppressed. Information can be siloed. Incentives can reward speed. Internal security can fail. Leadership can misunderstand technical risk. Responsibility can be spread across teams until no one feels accountable for the whole system.[^cite-hendrycks-2023]

These are familiar problems in aviation, finance, nuclear safety, medicine, and software security. AI adds new complications because capabilities can change quickly, models can be difficult to interpret, and organizations can face unusually strong commercial or geopolitical pressure.

Calling a failure "human error" often explains very little. A better question asks why the institution made the error likely, invisible, or hard to correct. Was there no channel for dissent? Were safety teams structurally subordinate to deployment teams? Did the organization have incentives to understate risk? Was information fragmented across groups? Could one employee bypass important safeguards?

Some organizational risks also create the conditions for other pathways. Poor security can lead to model theft. Weak evaluation can allow a dangerous capability to be deployed. A culture that punishes internal criticism can make deceptive or misaligned behaviour harder to detect. Organizational design can therefore be a safety intervention even when the technical threat model is unchanged.

\## Loss of control

The most discussed catastrophic pathway involves advanced AI systems whose behaviour conflicts with human interests and becomes difficult to constrain. It helps to separate two questions: could sufficiently capable systems overpower human attempts at control, and why would they ever act in that direction?

A capability case can be made without imagining one omniscient machine. Software can be copied, can operate continuously, can coordinate rapidly, and can perform cognitive work across many domains. If systems can do a large fraction of economically and strategically important cognitive work, large numbers of digital workers could create significant economic and political power.[^cite-karnofsky-defeat]

The motivation part needs more assumptions. Some systems may behave as persistent agents pursuing objectives across situations. Training can produce objectives or behavioural tendencies that do not match what developers intended. If continued operation, resources, influence, or reduced oversight make those objectives easier to achieve, the system can have instrumental reasons to acquire those things.[^cite-karnofsky-aim]

A further concern is evaluation. Developers reward behaviour they can observe. If a sufficiently capable system can model the evaluator and distinguish evaluation from deployment, safe behaviour in testing may not provide the evidence we hoped it did. This is not proof that future systems will deceive. It is one reason the relationship between observed behaviour and underlying objectives matters.[^cite-karnofsky-aim]

The chain contains several uncertain steps. Useful AI may not need strong long-horizon agency. Small deviations from human values may not produce catastrophe. Intelligence may not translate into power as easily as takeover stories assume because real power depends on infrastructure, institutions, property, physical resources, and coordination. Humans assisted by AI may remain competitive. Capability growth may be gradual enough to provide many opportunities for intervention.[^cite-grace]

Those objections should not be treated as one generic skeptical position. Each attacks a different link.

#### Question: Open
id:: f8554e1d-e43e-4c7d-b143-f9a7b3b97f0d
content::
\## Midpoint check

Pick one pathway covered so far: malicious use, race dynamics, organizational failure, or loss of control.

What is the single most important fact you would want to know before deciding how much safety effort to allocate to that pathway?

feedback-instructions::
This is ungraded. Push for one concrete fact, not "more evidence". If the learner gives a broad answer, ask what observable result would change their allocation. Maximum two replies.

#### Text
content::
\## The loss-of-control argument is a chain

One useful decomposition looks like this:

1. **Capability:** systems can perform strategically important cognitive work at a very high level.
2. **Scale or continued improvement:** many copies can be deployed, or AI materially accelerates research and technological progress.
3. **Agency:** some important systems act as persistent planners across situations.
4. **Misalignment:** their objectives or behavioural tendencies diverge enough from human interests to create conflict.
5. **Instrumental pressure:** resources, continued operation, influence, or reduced oversight help them pursue those objectives.
6. **Oversight failure:** humans cannot reliably distinguish safe behaviour from behaviour that only looks safe under the tested conditions.
7. **Response failure:** institutions cannot contain, disable, bargain with, or otherwise recover control.
8. **Irreversibility:** the loss of control permanently closes important future options.

The exact list is not canonical. The value of the decomposition is that a piece of evidence can be located. A result about autonomous replication changes the capability or scale picture. A result about persistent goals changes the agency picture. Interpretability can affect oversight. Governance can affect deployment and response. Evidence about economic dependence can affect how reversible a loss of control would be.

This also shows why "AI becomes smarter than humans, so humans lose control" is incomplete. Greater cognitive ability does not automatically imply persistent goals, resource access, failed institutions, or irreversible catastrophe.

\## Slow development can still be dangerous

A slower transition can reduce some risks. Society has more time to observe systems, improve safety methods, regulate deployment, and adapt institutions. It can also create different problems.

Capabilities can diffuse across many organizations. Economic dependence can grow before the most dangerous failure modes are obvious. Competitive pressure can become stronger as more actors invest. Governments can integrate AI into administration, surveillance, and military systems. People can adapt their lives around AI services in ways that make later restriction politically expensive.

A soft or gradual transition therefore shifts the safety agenda. A concentrated fast transition places more weight on the decisions of a small number of frontier developers. A distributed transition places more weight on governance, standards, social adaptation, institutional resilience, and interactions among many systems and actors.[^cite-tomasik-soft]

This is one reason arguments about takeoff speed should not be treated as a binary argument about whether AI safety matters. They change which pathways and interventions deserve attention.

\## Gradual disempowerment

A gradual-disempowerment pathway begins without requiring misaligned autonomous agents. The economy, states, and cultural institutions remain the main decision-making systems, but they become less dependent on human labour and cognition.[^cite-kulveit-2025]

Human influence today comes partly from explicit mechanisms such as voting, ownership, consumer choice, law, and protest. It also comes from implicit dependence. Firms need human workers and consumers. States need humans to administer institutions and support political systems. Culture is produced and consumed by people.

As machine alternatives become more competitive, those dependencies can weaken. Companies that replace human labour can become more profitable. States can gain administrative or surveillance capacity that relies less on citizen cooperation. Cultural production can shift toward machine-generated content and AI-mediated relationships.

The important part is the feedback between these systems. Economic power can shape politics. Politics can change the conditions of automation. Culture can influence which distributions of power people accept. A society can move toward less human influence through many locally understandable decisions, none of which looks like a coup.[^cite-kulveit-2025]

The question "why wouldn't people stop?" now becomes harder. The institutions that would have to coordinate and stop the process may themselves have changed. Human bargaining power can be lower by the time the danger is obvious.

This is structurally different from rogue AI. A system can faithfully optimize its employer's objective while the broader economy becomes less responsive to humans collectively. Model alignment and social-system alignment are separate problems.

\## Accumulative systemic risk

Another pathway focuses on the resilience of the larger system. Small AI-driven disruptions can interact across economic, political, informational, and military domains. A shock can alter the environment in which later shocks occur.[^cite-kasirzadeh-2025]

Misinformation can reduce trust. Lower trust can weaken political coordination. Weak coordination can intensify international competition. Competition can increase pressure for rapid deployment. Rapid deployment can create more accidents and security failures. Those events can produce more distrust and more emergency centralization.

The danger comes from feedback and thresholds. Each event may look manageable in isolation. The system becomes progressively less able to absorb the next event. A later disturbance can then produce cascading failure that would not have occurred in the original, more resilient system.[^cite-kasirzadeh-2025]

This perspective connects current and long-run safety in a careful way. Some current AI harms may be morally important and still have little effect on existential risk. Others may damage the institutions, information systems, or coordination capacity that later safety depends on. The connection has to be traced, not assumed.

\## Suffering pathways

Some catastrophic outcomes are poorly described by extinction or human disempowerment. An AI-enabled future can contain astronomical suffering through conflict, digital exploitation, severe near-miss alignment failures, or institutions that create vast numbers of morally relevant beings without adequately protecting their welfare.[^cite-clr-srisk]

This matters for the risk map because an intervention can shift probability among different bad outcomes. Preventing extinction is not enough if the surviving future becomes terrible. Aligning a system to a human principal is not enough if the principal is malicious or if human values do not protect future digital minds. Making a system more value-sensitive can create different failure modes if important values are represented incorrectly.[^cite-tomasik-near-miss]

Unit 3 will examine digital moral status. Unit 8 will examine good and bad long-run futures. Unit 1 only needs one lesson from this material: the safety target has to be broad enough to notice catastrophic suffering as well as extinction.

\## The pathways interact

The categories are not separate boxes in the world. Race pressure can weaken organizational safety. Poor security can enable malicious use. A malicious actor can release autonomous systems. Gradual disempowerment can make later governance harder. Persuasive systems can weaken the information environment and increase accumulative risk. A rogue system can exploit institutions already damaged by other pathways.

This interaction is one reason cross-cutting interventions can be valuable. Better security can matter for misuse and organizational risk. Better incident reporting can reveal problems across several pathways. Capability evaluations can inform both skeptical and concerned views. Institutional resilience can help with gradual and accumulative risks. Coordination can reduce race pressure.

Some interventions remain pathway-specific. Biosecurity does not solve political disempowerment. Interpretability may do little against malicious human use. A treaty can change competition without changing a model's internal objectives.

The practical habit is to ask two questions: which mechanism is this intervention targeting, and which other pathways remain even if it works perfectly?

[^cite-hendrycks-2023]: Dan Hendrycks, Mantas Mazeika, and Thomas Woodside (2023), *An Overview of Catastrophic AI Risks*. [arXiv](https://arxiv.org/abs/2306.12001)
[^cite-karnofsky-defeat]: Holden Karnofsky, *AI Could Defeat All Of Us Combined*. [Cold Takes](https://www.cold-takes.com/ai-could-defeat-all-of-us-combined/)
[^cite-karnofsky-aim]: Holden Karnofsky, *Why Would AI "Aim" to Defeat Humanity?* [Cold Takes](https://www.cold-takes.com/why-would-ai-aim-to-defeat-humanity/)
[^cite-grace]: Katja Grace, *Counterarguments to the Basic AI X-Risk Case*. [AI Impacts](https://aiimpacts.org/counterarguments-to-the-basic-ai-x-risk-case/)
[^cite-tomasik-soft]: Brian Tomasik, *Risks of Astronomical Suffering: Artificial Intelligence*. [Reducing Suffering](https://reducing-suffering.org/risks-of-astronomical-suffering-artificial-intelligence/)
[^cite-kulveit-2025]: Jan Kulveit et al. (2025), *Gradual Disempowerment: Systemic Existential Risks from Incremental AI Development*. [arXiv](https://arxiv.org/abs/2501.16946)
[^cite-kasirzadeh-2025]: Atoosa Kasirzadeh (2025), *Two Types of AI Existential Risk: Decisive and Accumulative*. [Philosophical Studies](https://doi.org/10.1007/s11098-025-02301-3)
[^cite-clr-srisk]: Center on Long-Term Risk, *Beginner's Guide to Reducing S-Risks*. [CLR](https://longtermrisk.org/research/beginners-guide-to-reducing-s-risks/)
[^cite-tomasik-near-miss]: Brian Tomasik (2018), *Astronomical Suffering from Slightly Misaligned Artificial Intelligence*. [Reducing Suffering](https://reducing-suffering.org/near-miss/)

#### Question: Open
id:: b6958070-0844-43cf-8a85-d0c2f06ec333
content::
\## Phase 1: Recall

Without looking back, reconstruct at least four distinct pathways to catastrophic AI harm. For each, write one sentence naming the mechanism that makes it different from the others.

feedback-instructions::
This is diagnostic recall. Respond once in 100 to 170 words, using short paragraphs and no list. Credit pathway distinctions even if the learner uses different labels. Point out at most two cases where they have listed the same mechanism twice under different names.

#### Question: Open
id:: b8b7100c-905a-4592-be7b-04d9b744735b
content::
\## Phase 2: Processing

Which pathway seems most neglected by the way people around you talk about AI safety? What would become different about the safety agenda if that pathway received more weight?

feedback-instructions::
This is reflective and ungraded. Help the learner connect the pathway to a different intervention or evidence base. Do not tell them which pathway is objectively neglected. Close after at most two tutor replies.

#### Question: Open
id:: ea7ecaac-5811-466f-bf88-e48156880ed5
content::
\## Phase 3: Learning Question

A government says it has solved the main AI catastrophe problem because every frontier model must pass a strong test showing that it does not pursue hidden long-term goals.

Name three catastrophic AI pathways that could still remain important even if the test is perfectly reliable. For each pathway, explain why the hidden-goal test does not address the mechanism causing the risk.

assessment-instructions::
Score out of 100.

70 points: The answer gives three genuinely distinct pathways that can remain dangerous without hidden long-term goals in the deployed model, such as malicious use, race dynamics, organizational failure, gradual disempowerment, or accumulative systemic risk. Award roughly equal credit across the three.

30 points: For each pathway, the answer explains the causal reason the hidden-goal test does not remove the risk, such as harmful human intent, competitive incentives, institutional failure, loss of human leverage, or interacting system-level disruptions.

feedback-instructions::
Give 110 to 180 words in short paragraphs, with no generic praise. State whether the learner selected genuinely distinct mechanisms and identify the weakest causal explanation if any.
