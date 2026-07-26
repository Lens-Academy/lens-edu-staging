---
title: "The Longtermist AI Governance Landscape: A Basic Overview"
source_url: https://forum.effectivealtruism.org/posts/ydpo7LcJWhrr2GJrx/the-longtermist-ai-governance-landscape-a-basic-overview
author:
  - Sam Clarke
published: 2022-01-18
created: 2022-01-18
description: "A basic overview of the different kinds of work happening in longtermist AI governance, covering strategy research, tactics research, policy development and advocacy, and field-building."
tags:
  - ea-intro-program
  - effective-altruism
  - artificial-intelligence
  - ai-safety
  - ai-governance
  - longtermism
  - existential-risk
  - work-in-progress
---{++{"author":"Luc's AI","timestamp":1785090636935}@@

%%
Add discussion note here:

...

%%++}

*Aim: to give a basic overview of what is going on in longtermist AI governance.*

*Audience: people who have limited familiarity with longtermist AI governance and want to understand it better. I don't expect this to be helpful for those who already have familiarity with the field. ETA: Some people who were already quite familiar with the field have found this helpful.*

This post outlines the different kinds of work happening in longtermist AI governance. For each kind of work, I'll explain it, give examples, sketch some stories for how it could have a positive impact, and list the actors I'm aware of who are currently working on it.

Firstly, some definitions:

- *AI governance* means bringing about local and global norms, policies, laws, processes, politics, and institutions (not just governments) that will affect social outcomes from the development and deployment of AI systems.
- *Longtermist AI governance*, in particular, is the subset of this work that is motivated by a concern for the very long-term impacts of AI. This overlaps significantly with work aiming to govern transformative AI (TAI).

It's worth noting that the field of longtermist AI governance is very small. I'd guess that there are around 60 people working in AI governance who are motivated by a concern for very long-term impacts.

# Short summary

On a high level, I find it helpful to consider there being a spectrum between foundational and applied work. On the foundational end, there's *strategy research*, which aims to identify good high-level goals for longtermist AI governance; then there's *tactics research* which aims to identify plans that will help achieve those high-level goals. Moving towards the applied end, there's policy development work that takes this research and translates it into concrete policies; work that advocates for those policies to be implemented, and finally the actual implementation of those policies (by e.g. civil servants).

There's also field-building work (which doesn't clearly fit on the spectrum). Rather than contributing directly to the problem, this work aims to build a field of people who are doing valuable work on it.

![](https://res.cloudinary.com/cea/image/upload/f_auto,q_auto/v1/mirroredImages/ydpo7LcJWhrr2GJrx/zbaoafws9hoqdi7i8cj6)

Of course, this classification is a simplification and not all work will fit neatly into a single category.

You might think that insights mostly flow from the more foundational to the more applied end of the spectrum, but it's also important that research is sensitive to policy concerns, e.g. considering how likely your research is to inform a policy proposal that is politically feasible.

We'll now go through each of these kinds of work in more detail.

# Research

## Strategy research

*Longtermist AI strategy research* ultimately aims to identify high-level goals we could pursue that, if achieved, would clearly increase the odds of eventual good outcomes from advanced AI, from a longtermist perspective (following Muehlhauser, I'll sometimes refer to this aim as 'getting *strategic clarity*').

This research can itself vary on a spectrum between *targeted* and *exploratory* as follows:

- Targeted strategy research answers questions which shed light on some other specific, important, known question
  - e.g. "I want to find out how much compute the human brain uses, because this will help me answer the question of when TAI will be developed (which affects what high-level goals we should pursue)"
- Exploratory strategy research answers questions without a very precise sense of what other important questions they'll help us answer
  - e.g. "I want to find out what China's industrial policy is like, because this will probably help me answer a bunch of important strategic questions, although I don't know precisely which ones"

### Examples

- Work on TAI forecasting, e.g. biological anchors and scaling laws for neural language models.
  - Example of strategic relevance: if TAI is soon, then slowly growing a large field of experts seems less promising; if TAI is very far, then longtermist AI governance should probably be relatively deprioritised.
- Work on clarifying the sources of AI x-risk, e.g. writing by Christiano, Critch, Carlsmith, Ngo and Garfinkel.
  - Example of strategic relevance: if most x-risk from AI comes from advanced misaligned AI agents, then governance should focus on influencing the first actors to build them.
- Work on investigating the speed of AI progress around TAI, e.g. investigation and analysis by AI Impacts.
  - Example of strategic relevance: if AI progress occurs discontinuously, then there are likely to be only a small number of high-stakes actors, and most of the value of governance will come from influencing those actors.

It's easy to confuse strategy research (and especially *exploratory* strategy research) with *broadly scoped* research. As many of the above examples show, strategy research can be *narrowly scoped* - that is, it can answer a fairly narrow question. Examples of broadly vs. narrowly scoped questions:

- On scaling laws:
  - Broad question: in general, how does the performance of deep learning models change as you increase the size of those models?
  - Narrower question: how does the performance of *large language models specifically (e.g. GPT-3)* change as you increase the size of those models? (The question tackled in this paper.)
- On sources of AI x-risk:
  - Broad question: how much x-risk is posed by advanced AI in general?
  - Narrower question: how much x-risk is posed *by influence-seeking AI agents specifically*? (The question tackled in this report.)

Indeed, I think it's often better to pick narrowly scoped questions, especially for junior researchers, because they tend to be more tractable.

Luke Muehlhauser has some recommendations for those who want to try this kind of work: see point 4 in this post. And see this post for some examples of open research questions.

### Stories for impact

- *Direct impact*: there are many possible goals in AI governance, and we need to prioritise the most important ones. This work is often motivated by researchers' impressions that there is very little clarity about topics which affect what goals we should pursue. For example, see the results of these surveys which show wide disagreement about AI x-risk scenarios and the total amount of AI x-risk, respectively.
- *Indirect impact:*
  - Field-building: having a clear understanding of what we're working to achieve and why it matters would help attract more people to the field.
  - Communicating the need for policy change: if you want to convince people to do costly or dramatic things in the future, you'd better have clear things to say about what we're working to achieve and why it matters.

### Who's doing it?

Some people at the following orgs: FHI, GovAI, CSER, DeepMind, OpenAI, GCRI, CLR, Rethink Priorities, OpenPhil, CSET, plus some independent academics.

## Tactics research

*Longtermist AI tactics research* ultimately aims to identify plans that will help achieve high-level goals (that strategy research has identified as a priority). It tends to be more narrowly scoped by nature.

It's worth noting that there can be reasons to do tactics research even if you haven't clearly identified some goal as a priority: for your own learning, career capital, and helping to build an academic field.

### Examples

- The Windfall Clause
  - Plan: develop a tool for distributing the benefits of AI for the common good
  - High-level goals which this plan is pursuing: reducing incentives for actors to race against each other to be the first to develop advanced AI; reducing economic inequality.
- Mechanisms for Supporting Verifiable Claims
  - Plan: develop practices by which AI developers could make their own claims about AI development more verifiable (that is, claims to which developers can be held accountable)
  - High-level goals which this plan is pursuing: developing mechanisms for demonstrating responsible behaviour of AI systems; enabling more effective oversight; reducing pressure to cut corners for the sake of gaining a competitive edge.
- AI & Antitrust
  - Plan: proposing ways to mitigate tensions between competition law and the need for cooperative AI development
  - High-level goal which this plan is pursuing: increasing cooperation between companies developing advanced AI.

### Stories for impact

- *Direct impact*: creating solutions that get used to help make better decisions (in policy and future research).
  - This is what Allan Dafoe calls the 'Product model of research'.
- *Indirect impact*: even if not all solutions get used to help make better decisions, they will help grow the field of people who care about longtermist AI governance issues, and improve insight, expertise, connections and credibility of researchers.
  - This is what Allan Dafoe calls the 'Field-building model of research'.

### Who's doing it?

Some people at the following orgs: FHI, GovAI, CSER, DeepMind, OpenAI, GCRI, CSET, Rethink Priorities, LPP, plus some independent academics.

# Policy development, advocacy and implementation

Strategy research outputs high-level goals. Tactics research takes those goals and outputs plans for achieving them. *Policy development* work takes those plans and translates them into policy recommendations that are ready to be delivered to policymakers. This requires figuring out (e.g.) which precise ask to make, what language to use (both in the formal policy and in the ask), and other context-specific features that will affect the probability of successful implementation.

*Policy advocacy* work advocates for policies to be implemented, e.g. figuring out who is the best person to make the policy ask, to whom, and at what time.

*Policy implementation* is the work of actually implementing policies in practice, by civil servants or corporations.

It's worth distinguishing government policy (i.e. policy intended to be enacted by governments or intergovernmental organisations) from corporate policy (i.e. policy intended to be adopted by corporations). Some people working on longtermist AI governance focus on improving corporate policy (especially the policies of AI developers), while others in the field focus on improving the policies of relevant governments.

A common motivation for all policy work is that implementation details are often thought to be critical for successful policymaking. For example, if a government regulation has a subtle loophole, that can make the regulation useless.

Compared with research, this kind of work tends to involve relatively less individual thinking, and relatively more conversation/information collection (e.g. having meetings to learn who has authority over a policy, what they care about, and what other players want in a policy) as well as coordination (e.g. figuring out how you can get a group of actors to endorse a policy, and then making that happen).

As mentioned earlier, policy insight sometimes flows 'backwards'. For example, policy development might be done iteratively based on how advocacy changes your knowledge (and the policy landscape).

### Examples

- Government policy:
  - Committing to not incorporate AI technology into nuclear command, control and communications (NC3), e.g. as advocated for by CLTR in their Future Proof report.
  - Government monitoring of AI development, e.g. as developed in this whitepaper on AI monitoring.
  - Making nascent regulation or AI strategies/principles sensitive to risks from advanced AI systems (as well as current ones), e.g. feedback by various EA orgs about the EU AI Act.
- Corporate policy:
  - Developing norms for the responsible dissemination of AI research, given its potential for misuse, e.g. these recommendations by PAI.

These ideas vary on a spectrum between more targeted (e.g. not integrating AI into NC3) to more general (in the sense of creating general-purpose capacity to deal with a broad class of problems that will likely arise, e.g. most of the others above). I think our policy development, advocacy and implementation today should mostly focus on more general ideas, given our uncertainties about how AI will play out (whilst also pushing for obviously good specific ideas, when they arise).

### Stories for impact

- *Direct impact:* having good policies in place increases our chances of successfully navigating the transition to a world with advanced AI.
- *Indirect impact:* even if you can't be sure that some policy idea is robustly good, developing/advocating/implementing it will help build insight, expertise, connections and credibility of longtermist AI governance people. We don't want to get to an AI "crunch time", and only then start learning about how to develop policy and decision-making.
  - That said, we should be very careful with implementing policies that could end up being harmful, e.g. by constraining future policy development.

### Who's doing it?

- Development:
  - Of government policy: CLTR, FLI, GovAI, CSET, CSER, FHI, TFS
  - Of corporate policy: OpenAI, DeepMind, GovAI, CSER, FHI, PAI
- Advocacy:
  - For government policy: CLTR, CSET, FLI, TFS
  - For corporate policy: PAI
- Implementation:
  - Of government policy: people in various civil services
  - Of corporate policy: OpenAI, DeepMind

# Field-building

This is work that explicitly aims to grow the field or community of people who are doing valuable work in longtermist AI governance. One could think of this work as involving both (1) bringing in new people, and (2) making the field more effective.

### Examples

1. Bringing in new people by creating:
   - policy fellowships, such as the OpenPhil Technology Policy Fellowship;
   - online programs or courses to help junior people get synced up on what is happening in AI governance;
   - high quality, broadly appealing intro material that reaches many undergraduates;
   - more scalable research fellowships to connect, support and credential interested junior people.
2. Making the field more effective by creating:
   - research agendas;
   - ways for senior researchers to easily hire research assistants.

### Stories for impact

- *Growth model*: building a longtermist AI governance field with lots of aligned people with the capacity and relevant expertise to do important research and policy work (perhaps especially when this work is less bottlenecked by lack of strategic clarity).
- *Metropolis model:* building a longtermist AI governance field with dense connections to broader communities (e.g. policymaking, social science, machine learning), such that the field can draw on diverse expertise from these communities.

### Who's doing it?

GovAI, OpenPhil, SERI, CERI, CHERI and EA Cambridge. From a broader view, all cause-general EA movement building as well. This is the least explored kind of work discussed in this post.

# Other views of the longtermist AI governance landscape

I've presented just one possible view of the longtermist AI governance landscape - there are obviously others, which may be more helpful for other purposes. For example, you could carve up the landscape based on different kinds of interventions, such as:

- Shifting existing discussions in the policy space to make them more sensitive to AI x-risk (e.g. building awareness of the difficulty of assuring cutting-edge AI systems)
- Proposing novel policy tools (e.g. international AI standards)
- Getting governments to fund AI safety research
- Shifting corporate behaviour (e.g. the windfall clause)
- …

Or, you could carve things up by geographic hub (though not all organisations are part of a geographic hub):

- Bay Area: OpenPhil, OpenAI, PAI, various AI alignment orgs. On average more focused on misalignment as the source of AI x-risk; culturally closer to Silicon Valley and rationality cultures.
- DC: US govt, CSET. Focus on US policy development/advocacy/implementation; culturally closer to DC culture.
- UK: FHI/GovAI, DeepMind, UK govt, CSER, CLTR, (others?). On average more concern over a wider range of sources of AI x-risk.
- EU. In 2020, the European Commission drafted the world's first AI regulation, which will likely be passed in the next few years and could lead to a Brussels effect.
- China.
- …

Or, you could carve up the landscape based on different "theories of victory", i.e. complete stories about how humanity successfully navigates the transition to a world with advanced AI. There's a lot more that could be said about all of this; the aim of this post has just been to give a concise overview of the kinds of work that are currently happening.

*Acknowledgements: this is my own synthesis of the landscape, but is inspired and/or draws directly from EA forum posts by Allan Dafoe, Luke Muehlhauser and Convergence Analysis. Thanks also to Jess Whittlestone for helpful conversation, plus Matthijs Maas, Yun Gu, Konstantin Pilz, Caroline Baumöhl and especially a reviewer from SERI for feedback on a draft.*

*This work is licensed under a [Creative Commons Attribution 4.0 International License.](https://creativecommons.org/licenses/by/4.0/)*
