---
id: '393ab747-32d9-419d-8089-4f739096eb21'
title: "The Case Against Prioritising AI X-Risk"
tldr: "Skepticism can target the probability of catastrophe, the mechanisms behind it, or the claim that x-risk work deserves priority. A strong case for intervention has to survive all three."
summary_for_tutor: "Presents and evaluates technical objections from Grace and the Distraction, Human Frailty, and Checkpoints for Intervention arguments reconstructed by Swoboda et al. The aim is to distinguish critiques of probability from critiques of priority, then identify what evidence would resolve each."
reading_minutes: 38
tutor_minutes: 22
tags:
  - wip
---

#### Text
content::
\## There is more than one way to reject the x-risk agenda

When people say they are skeptical of AI existential risk, they can mean very different things. One person may think the probability of advanced AI causing catastrophe is low because the technical threat model has weak links. Another may grant a nontrivial risk but think the proposed interventions are ineffective. A third may accept both the risk and some interventions while arguing that x-risk has become too politically dominant and diverts attention from harms that are already occurring.

Those positions should not be collapsed. They point to different evidence and different practical conclusions. If the problem is an implausible takeover mechanism, technical results matter. If the problem is poor intervention quality, we need evidence about tractability and side effects. If the problem is political distraction, we need evidence about budgets, agendas, representation, and institutional power.

Some objections attack the mechanism itself: whether useful systems need persistent goals, whether misalignment becomes catastrophic, whether cognitive advantage converts into power, and whether human institutions can respond.[^cite-grace] Other objections grant more of the technical case and challenge the priority claim. Three especially useful versions ask whether x-risk work distracts from current harms, whether ordinary human and institutional frailty explains most of the danger, and whether society can wait for later intervention checkpoints.[^cite-swoboda-2025] These objections need different evidence, so they should be kept separate.

\## Technical skepticism: the chain may be weaker than it looks

Several transitions in the standard loss-of-control story are contestable. Economically useful systems may not need to become coherent, long-horizon agents. Systems may be somewhat misaligned without that misalignment becoming catastrophic. Individual cognitive ability may convert into power less easily than takeover stories assume because power also depends on institutions, infrastructure, rights, social cooperation, and access to physical resources. Humans using AI may remain competitive. Capability growth may also be gradual enough that society has multiple opportunities to respond.[^cite-grace]

These are serious objections because the catastrophic conclusion is conjunctive. If several uncertain links all have to hold, weakening one can matter a lot. At the same time, not every objection has to defeat the whole threat model. A system need not literally become a perfect expected-utility maximizer for strategic behaviour to matter. Intelligence need not translate automatically into power for highly capable systems to create new security problems. Slow takeoff can lower one danger while increasing diffuse race and disempowerment risks.

The useful way to engage technical skepticism is therefore to ask which claim the objection actually changes. Does it reduce the probability of dangerous agency? Does it change how much power a system could acquire? Does it increase the time available for intervention? Does it only challenge one abrupt-takeover story while leaving misuse or gradual pathways intact? This is much more informative than asking whether Grace is "pro-risk" or "anti-risk".

\## The Distraction Argument

Swoboda and coauthors first reconstruct what they call the **Distraction Argument**.[^swoboda] In its strongest form, the argument is not merely "current harms matter too". That claim is easy to accept. The stronger claim is that public and policy attention to speculative existential risk *causes* current harms to receive less attention or weaker regulation.

There are plausible mechanisms. Dramatic future-risk narratives can give frontier companies a large role in defining the regulatory conversation. They can crowd out perspectives from people affected by discrimination, labour harms, privacy violations, or misinformation. Policymakers have limited attention. Philanthropic and research budgets are finite. If one framing becomes dominant, other work can lose resources and legitimacy.

Swoboda and coauthors argue that the empirical case for a broad displacement effect is not yet strong. They examine claims that x-risk discourse increases AI hype and investment, allows corporate leaders to dominate policy, pushes companies to frame regulation around future risks, and shifts political attention away from current harms. Their conclusion is cautious: some local tradeoffs can exist, but the claim that x-risk discourse generally causes current harms to be ignored is not well established.[^swoboda]

That does not make the concern irrelevant. It makes it empirical. We should ask whether budgets are substitutes, whether specific policies crowd one another out, whose expertise is represented, and whether catastrophic-risk framing changes which problems regulators notice. There can also be synergies. Better incident reporting, model evaluations, biosecurity, security culture, and accountability can help with both present and future risks.

The accumulative-risk perspective adds another complication. Some present harms may be part of a long-run catastrophic pathway if they erode trust, institutional resilience, democratic control, or human leverage. Kasirzadeh explicitly argues that the boundary between social risk and existential risk can be causal rather than simply temporal.[^kasirzadeh] This does not mean every bias or misinformation problem is existential. It means "near-term" and "long-term" are not always separate buckets.

#### Question: Open
id:: e9fc204c-224d-4d3f-8f60-bcc72ec728a1
content::
\## Midpoint check

Suppose funding for AI x-risk research doubles next year.

What evidence would convince you that this *did* crowd out work on current AI harms? What evidence would convince you that the two areas were mostly complementary?

feedback-instructions::
This is ungraded. Push the learner toward observable indicators such as budgets, hiring, legislative agendas, research grants, or policy substitution. Do not assume that attention is either zero-sum or automatically complementary. Maximum two replies.

#### Text
content::
\## The Human Frailty Argument

The second reconstructed argument says that catastrophic AI risk is ultimately a problem of ordinary human and institutional failure.[^swoboda] People are reckless, overconfident, selfish, biased, bad at coordination, and sometimes malicious. Organizations suppress warnings, mismanage technology, and pursue incentives that conflict with public safety. If those familiar weaknesses are the real source of danger, perhaps we should focus on fixing governance and institutional competence instead of devoting special resources to speculative superintelligence scenarios.

There is a real insight here. Many AI risks do depend on human frailty. Misuse requires a person or organization choosing a harmful use. Race dynamics depend on strategic behaviour. Organizational accidents are, by definition, partly organizational. Even a technically misaligned system has to be built, deployed, given access, and inadequately supervised by humans.

The stronger conclusion is harder to establish. If "human frailty" is defined broadly enough to include every failure to anticipate or manage any AI danger, the claim becomes almost trivially true. Saying "the disaster happened because humans failed to prevent it" tells us very little about what prevention requires. A useful version of the argument has to identify specific frailties and show that generic interventions against them would address the AI-specific risk at lower cost than specialized safety work.

Swoboda and coauthors therefore treat the argument as an important reminder, not a successful reason to ignore x-risk research.[^swoboda] Improving institutions, incentives, regulation, and organizational culture may reduce many catastrophic pathways. Understanding AI-specific mechanisms can still be necessary to know which institutional failures matter and what safeguards to build.

This creates a healthy research question: **which parts of AI safety are genuinely AI-specific, and which are cases of broader problems such as security, governance, coordination, and institutional design?** If a generic intervention works, that is a reason to prefer it in some cases. If the mechanism is genuinely new, generic good governance may not be enough.

\## The Checkpoints for Intervention Argument

The third skeptical argument has a very intuitive form: dangerous AI cannot appear from nowhere. People have to build more capable systems, connect them to infrastructure, automate more tasks, grant access to resources, and continue deploying despite warning signs. At each stage, humanity gets another chance to stop. If the danger becomes real, we can intervene then.[^swoboda]

This argument is strongest when three conditions hold. First, the warning signs are observable before the worst damage occurs. Second, society retains the technical and political ability to intervene after those signs appear. Third, waiting produces valuable information without irreversibly worsening the situation.

Those conditions may hold for some pathways. A capability evaluation can reveal a dangerous ability early. A deployment can be paused. A regulation can be introduced once the evidence becomes clearer. In such cases, waiting can avoid expensive premature action.

The argument weakens when checkpoints are hard to observe, widely distributed, or themselves eroded by the transition. A capability can diffuse across many actors before regulation arrives. Competitive pressure can make unilateral restraint costly. Economic dependence can make shutdown politically expensive. A gradual-disempowerment process can reduce the leverage available to intervene later. If strategic deception is possible, behavioural warning signs can become less trustworthy. The fact that there are logical checkpoints does not guarantee that they remain effective intervention points.

Swoboda and coauthors conclude that the argument identifies a real source of reassurance but does not establish that waiting is generally safe.[^swoboda] The key empirical question is how much option value remains at each checkpoint.

\## Priority arguments need a second layer

At this point, it is useful to separate **risk assessment** from **priority assessment**. Even if you think a catastrophic pathway is plausible, that does not tell you which intervention deserves resources. Priority depends on tractability, cost, side effects, neglectedness, and the quality of alternatives.

Suppose you assign ten percent to a serious AI catastrophe but think none of the available interventions change that probability. Your concern may be high while your willingness to fund a particular programme remains low. Conversely, you could assign one percent to catastrophe and still support a cheap evaluation programme if it provides valuable information and has few downsides.

This is where many public debates become misleading. People argue over a single "p(doom)" as if every policy recommendation were a monotonic function of that number. It is not. Two people can agree on the probability and disagree completely about the best intervention. Two people can disagree on the probability and still support the same low-cost, robust safety measure.

\## Current harms, catastrophic risks, and one shared system

There is a useful way to interpret the debate that avoids forcing current harms and future catastrophic risks into competition. Some harms are morally important now and have little connection to catastrophe. They deserve attention for ordinary ethical reasons. Some current harms are also early manifestations of mechanisms that matter for long-run safety. Manipulation can affect political resilience. Surveillance can enable durable concentration of power. Economic dependence can alter who has bargaining power. Weak security can create both current incidents and future catastrophic vulnerabilities.

Kasirzadeh's accumulative account makes this overlap explicit.[^kasirzadeh] The right question is not "is this a current harm or an x-risk?" It is "what role does this harm play in the causal system, and what reason do we have to address it?" A present-day injustice does not need an existential-risk justification to matter. A present-day institutional weakness can also become relevant to existential safety if it changes later resilience.

\## The best skeptical arguments improve the safety agenda

A good skeptical argument does not merely lower a probability. It tells us what evidence to seek and what work would become less valuable if the objection succeeds.

If the Distraction Argument is right in a particular institution, we should change funding and representation. If the Human Frailty Argument is right, more resources should go toward organizational safety, incentives, and governance that work across technologies. If the Checkpoints Argument is right, information-gathering and flexible intervention may dominate expensive early restrictions. If Grace's objections are right about agency or power acquisition, some technical agendas lose urgency while misuse or structural pathways can remain.

This is why Unit 1 should include serious skepticism. The point of "why intervene at all?" is not to build the strongest possible case and stop. It is to identify what survives after the strongest objections have been given their full force.

[^grace]: Katja Grace, *Counterarguments to the Basic AI X-Risk Case*. [AI Impacts](https://aiimpacts.org/counterarguments-to-the-basic-ai-x-risk-case/)
[^swoboda]: Torben Swoboda et al. (2025), *Examining Popular Arguments Against AI Existential Risk: A Philosophical Analysis*. [arXiv](https://arxiv.org/abs/2501.04064)
[^kasirzadeh]: Atoosa Kasirzadeh (2025), *Two Types of AI Existential Risk: Decisive and Accumulative*. [Philosophical Studies](https://doi.org/10.1007/s11098-025-02301-3)

#### Question: Open
id:: 3af07680-7353-4c87-8e71-872456f936bf
content::
\## Phase 1: Recall

Without looking back, reconstruct the Distraction, Human Frailty, and Checkpoints arguments. For each one, write the conclusion it is trying to support and the key premise that would have to be true for the argument to work.

feedback-instructions::
Respond once in 100 to 170 words. Focus on whether the learner has kept the three arguments distinct. Point out at most two places where they have confused a critique of the risk probability with a critique of the priority of x-risk work.

#### Question: Open
id:: 7147cbc3-8afd-43d2-8cb9-f457bf1f9906
content::
\## Phase 2: Processing

Which skeptical argument currently seems strongest to you? What observation or evidence would most weaken it?

feedback-instructions::
This is reflective and ungraded. Help the learner turn the objection into a discriminating claim. If the evidence they propose would be compatible with both the objection and its denial, point that out and ask for a better discriminator. Maximum two replies.

#### Question: Open
id:: 524798cf-6256-4735-b3e8-c22136d7e256
content::
\## Phase 3: Learning Question

A policymaker says: "We should postpone serious work on catastrophic AI risk. If the danger becomes real, we will see warning signs and intervene then."

Evaluate this argument. Give one condition that would make waiting reasonable and two *distinct* conditions that would make waiting dangerous. Explain why each condition changes the decision.

assessment-instructions::
Score out of 100.

30 points: The answer gives a coherent condition under which delay is reasonable, such as later evidence arriving before irreversible deployment while intervention remains feasible and not much more costly.

30 points: The answer gives one coherent way checkpoint logic can fail, such as warning signs arriving too late, capabilities diffusing quickly, competitive pressure weakening restraint, growing dependence making intervention harder, or strategic concealment reducing observability.

30 points: The answer gives a second failure condition that is causally distinct from the first.

10 points: The answer explains how the conditions change the value of waiting, for example by changing information value, reversibility, or future intervention capacity.

feedback-instructions::
Give 110 to 180 words. State whether the learner treated waiting as a conditional strategy and whether the two failure conditions are genuinely distinct. Do not grade on whether they favour immediate intervention overall.
