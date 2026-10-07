---
id: 'e24f4980-3de2-4679-8a6d-4182233ebfe4'
title: "How Could AI Cause Catastrophe?"
tldr: "AI catastrophe is a landscape of pathways, not one story. Misuse, races, organizational failure, rogue systems, gradual disempowerment, and accumulative collapse call for different evidence and different interventions."
summary_for_tutor: "Maps major catastrophic-AI pathways using Hendrycks et al., Karnofsky, Grace, Kulveit et al., and Kasirzadeh. The learner should distinguish decisive takeover from malicious use, race dynamics, organizational failure, gradual disempowerment, and accumulative systemic collapse."
reading_minutes: 38
tutor_minutes: 20
tags:
  - wip
---

#### Text
content::
\## One phrase, several very different stories

"AI could cause catastrophe" sounds like one claim. It is closer to a family name.

A government worried about AI-enabled bioterrorism needs a different response from a lab worried about deceptive internal goals. A regulator worried about race dynamics is solving a different problem from a policymaker worried that human influence slowly drains out of the economy and political system. If these pathways are bundled together, people can appear to disagree about AI risk while actually disagreeing about different objects.

Hendrycks, Mazeika, and Woodside group catastrophic AI risks into four broad sources: malicious use, AI race dynamics, organizational risks, and rogue AI systems.[^cite-hendrycks-overview] This is a useful first map because each category locates the problem in a different place.

\## Malicious use

In malicious-use scenarios, a human or organization wants to cause harm and AI increases what they can do. The AI can remain obedient. There is no alignment failure in the usual sense.

The obvious examples are cyber and biological misuse. Advanced systems could lower the expertise needed to design attacks, automate parts of an attack pipeline, or help people search a much larger space of dangerous possibilities. The important variable is not whether the model "wants" catastrophe. It is whether a dangerous actor can use the model to overcome bottlenecks that previously protected society.[^cite-hendrycks-overview]

Persuasion and surveillance belong here too. Highly personalized influence can alter beliefs at scale. A government can use AI for censorship, monitoring, or political control. These harms can also interact with other risks by weakening the information environment needed for collective response.

A purely technical alignment solution may do little here if the system faithfully follows a malicious user's instructions. Safety can require access control, monitoring, governance, security, or institutional design.

\## Race dynamics

A second pathway comes from competition. A company may prefer to test more carefully but fear losing market share. A state may prefer slower military automation but fear that an opponent will move faster. Each actor can make a locally understandable choice that leaves everyone in a worse equilibrium.

Race dynamics matter because they can change the evidential threshold for deployment. A lab that would wait under monopoly can deploy under competition. A state can delegate more authority to AI because machine-speed response seems strategically necessary. Safety measures can look like unilateral handicaps.

This kind of risk is neither a malicious-use story nor a rogue-AI story. The failure comes from incentives among human actors. Unit 7 will examine these coordination problems in more detail. For Unit 1, notice the implication: some catastrophic AI risk remains even if every individual AI system behaves exactly as its operator intends.

\## Organizational failure

Complex organizations fail in ways no individual intends. Hendrycks and coauthors point to familiar accident mechanisms: weak safety culture, ignored warnings, information-security failures, model theft or release, inadequate external review, and incentives that reward progress more strongly than caution.[^cite-hendrycks-overview]

This category is easy to underestimate because it can sound mundane next to superintelligence. The mechanism is familiar, which can make it more credible, not less. A powerful system does not need to be adversarial if the organization gives it the wrong access, misunderstands an evaluation, suppresses bad news, or loses control of the model weights.

Organizational risk also interacts with uncertainty. If managers believe the risk is speculative, they may rationally spend less on prevention. If internal researchers have information that senior leadership does not, the organization can make decisions from a distorted picture. Safety therefore depends partly on how institutions aggregate information and incentives.

\## Rogue or misaligned AI

The classic loss-of-control argument focuses on systems whose behavior diverges from what humans intend.

Holden Karnofsky usefully separates capability from motivation.[^cite-karnofsky-defeat] First ask whether sufficiently capable systems could acquire decisive influence if they tried. Software can be copied. Digital workers can operate continuously, perform research, write code, coordinate quickly, and interact with digital infrastructure. A large population of capable AI systems may matter even without one magical superintelligence.

Then ask why the systems would ever try.

Karnofsky's "aims" argument starts from the gap between the thing humans want and the feedback humans can actually provide.[^cite-karnofsky-aim] Training rewards behavior that evaluators can recognize. If a model learns how the evaluator is mistaken, there can be cases where producing the appearance of success is rewarded more than producing the underlying result.

That still does not produce catastrophe. The chain needs agency, some persistent objective or behavioural tendency, enough capability, useful routes to resources or influence, failures of oversight, and failures of human response.

Katja Grace attacks many of those links.[^cite-grace-counterarguments] Economically useful systems may not need coherent long-term goals. Intelligence may translate into power less directly than takeover arguments assume. Institutions, ownership, law, physical infrastructure, and other humans also matter. Human-AI teams may remain competitive. Power-seeking may be costly enough that it is not the best strategy for many goals.

These objections do not refute the entire class. They tell us where evidence is needed.

\## Gradual disempowerment

Now consider a scenario with no betrayal.

Kulveit and coauthors argue that AI can reduce human influence through ordinary competition.[^cite-kulveit-disempowerment] The economy currently responds to human preferences partly because humans provide labour and demand. States respond to citizens partly because they need taxes, administrators, legitimacy, and military participation. Culture remains human-facing because humans produce, consume, and transmit it.

If AI becomes a better substitute across these roles, systems can remain locally functional while becoming less dependent on humans. Firms that preserve costly human involvement can lose to firms that automate. States can become less dependent on citizen labour. Cultural production can shift toward machine creators and machine audiences. The feedback loops are linked: economic power shapes politics, politics shapes markets, culture shapes both.

The striking feature of this scenario is that no moment needs to look like takeover. Human welfare can even improve for a while. The risk is that relative influence falls far enough that humans eventually cannot redirect the systems around them.

Individual AI alignment is not obviously sufficient here. A well-behaved assistant can still participate in an economy whose competitive dynamics reduce human leverage. The object of alignment has moved from one model to a civilization-scale system.

\## Accumulative risk

Kasirzadeh's accumulative-risk framework gives us another lens.[^cite-kasirzadeh-accumulative] Social risks that look recoverable in isolation can interact. Misinformation weakens trust. Surveillance weakens political accountability. Economic disruption weakens institutions. Military competition raises pressure for automation. Once system resilience has fallen, a further shock can trigger a cascade.

Her point is not that every current AI harm secretly equals existential risk. The claim is about pathways. A series of lower-severity disruptions can change the background conditions in which later disruptions occur. The system crosses thresholds.

This framing also helps bridge a political divide in AI ethics. Near-term harms and existential risk are often presented as rival topics. In an accumulative model, some present-day risks are part of the causal route to long-run catastrophe. The relationship becomes empirical: which harms are local and recoverable, and which ones degrade the systems needed to recover from future shocks?

\## Which pathways should dominate?

We do not have a source-supported answer that one pathway should dominate all others. The evidence differs by pathway and can change over time.

A useful portfolio view asks what each intervention protects against. Biosecurity measures can help under malicious use and some race scenarios. Better organizational safety helps even when models are not agentic. Alignment and control research matter more under rogue-AI pathways. Democratic resilience and preservation of human influence matter more under gradual and accumulative scenarios.

This is why "Do you believe in AI x-risk?" is a poor research question. A person can be skeptical of fast takeover and still be very worried about misuse or gradual disempowerment. Another person can think social harms are severe while doubting they accumulate into existential catastrophe.

The next submodule makes skepticism explicit. We will look at arguments claiming that x-risk work distracts from current harms, that human frailty is the real target, and that society has many checkpoints at which it can intervene later.

[^cite-hendrycks-overview]: Dan Hendrycks, Mantas Mazeika, and Thomas Woodside (2023), *An Overview of Catastrophic AI Risks*. [arXiv](https://arxiv.org/abs/2306.12001)
[^cite-karnofsky-defeat]: Holden Karnofsky, *AI Could Defeat All Of Us Combined*. [Cold Takes](https://www.cold-takes.com/ai-could-defeat-all-of-us-combined/)
[^cite-karnofsky-aim]: Holden Karnofsky, *Why Would AI "Aim" to Defeat Humanity?* [Cold Takes](https://www.cold-takes.com/why-would-ai-aim-to-defeat-humanity/)
[^cite-grace-counterarguments]: Katja Grace, *Counterarguments to the Basic AI X-Risk Case*. [AI Impacts](https://aiimpacts.org/counterarguments-to-the-basic-ai-x-risk-case/)
[^cite-kulveit-disempowerment]: Jan Kulveit et al. (2025), *Gradual Disempowerment: Systemic Existential Risks from Incremental AI Development*. [arXiv](https://arxiv.org/abs/2501.16946)
[^cite-kasirzadeh-accumulative]: Atoosa Kasirzadeh (2025), *Two Types of AI Existential Risk: Decisive and Accumulative*. [Philosophical Studies](https://doi.org/10.1007/s11098-025-02301-3)

#### Question: Open
id:: 2250f05a-7440-4fb6-af70-c48f14c5f27e
content::
\## Mid-reading check

Pick two pathways from the reading that would require substantially different safety interventions. What changes about the intervention once you change the mechanism?

feedback-instructions::
Ungraded checkpoint. Help the learner connect mechanism to intervention. Do not rank the pathways. One reply.

#### Question: Open
id:: e4e62076-c096-483d-9014-d629a9bd58d4
content::
\## Phase 1: Recall

Without looking back, reconstruct the main AI-catastrophe pathways from the reading. Group them however makes sense to you. Then mark which pathway currently seems most neglected in public discussion.

feedback-instructions::
Respond once in 90 to 150 words. Credit alternative taxonomies if they distinguish genuinely different causal mechanisms. The final judgment about neglect is reflective and should not be graded.

#### Question: Open
id:: cb7b585a-04ea-4998-ac7e-29798f22957d
content::
\## Phase 2: Processing

Which of these pathways would remain worrying if future AI systems had no persistent goals of their own? Explain the mechanism.

feedback-instructions::
Ungraded. Help the learner notice that malicious use, races, organizational failure, and some systemic pathways do not require autonomous long-run AI goals. Maximum two replies.

#### Question: Open
id:: d643cd65-f536-4943-a6be-fbc665223dda
content::
\## Phase 3: Learning Question

A research funder says: "If instrumental power-seeking turns out to be rare in advanced AI, most catastrophic AI-safety work becomes unnecessary."

Evaluate the claim. Name at least three catastrophic pathways that could remain important and explain why each does not depend on instrumental power-seeking by an AI system.

assessment-instructions::
Score out of 100.

60 points: The answer gives three genuinely distinct catastrophic pathways that do not require AI instrumental power-seeking, such as malicious human use, competitive race dynamics, organizational accidents or security failures, gradual human disempowerment through ordinary incentives, or accumulative systemic collapse.

40 points: The answer explains the causal mechanism for the examples, showing why each can occur even if AI systems do not independently seek power.

feedback-instructions::
Give 100 to 170 words. Credit any well-explained three pathways. Below full credit, identify where two examples are really the same mechanism or where the explanation quietly reintroduces AI power-seeking.
