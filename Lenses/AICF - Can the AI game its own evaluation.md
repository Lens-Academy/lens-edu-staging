---
id: 'ef4c993e-6431-4449-aa6e-87051fa108be'
title: "Can the AI game its own evaluation?"
reading_minutes: 5
tutor_minutes: 6
tldr: "Control relies on getting a model's best effort when it matters: from the red team trying to draw out its attacks, and from untrusted monitors. A scheming model could deliberately underperform. Redwood researchers explain where this would hurt, and why they think training makes it much harder."
summary_for_tutor: "Optional lens in Unit 4 of AI Control Fundamentals, Module 'Practical problems', optional lens. The learner reads the section 'Sandbagging can cause a variety of problems' from Julian Stastny and Buck Shlegeris's 'Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking' (Redwood Research, May 2025): misaligned AIs may intentionally underperform in dangerous capability evaluations (for a high-stakes control safety case the red team must elicit powerful, sneaky attacks from the untrusted model, which has an incentive to sandbag), in AI safety research, as untrusted monitors (failing to flag attacks, or sandbagging their collusion abilities), and when generating training signals. Two types: hiding latent capabilities, and not living up to their potential. Training makes sandbagging much harder. Then the authors' overall view: highly uncertain, depends on the domain, but substantially lower risk with careful countermeasures. This is a practical criticism: the authors are control researchers naming a weakness they work on. One question. Do not tell the learner who is right."
---
#### Text
content::
**The criticism: the AI can game its own evaluation.** A control evaluation needs the red team to draw out the model's best attacks, and untrusted monitoring needs a monitor that really tries to flag attacks. A scheming model could deliberately do worse in both: this is called *sandbagging*. Two Redwood Research researchers, Julian Stastny and Buck Shlegeris, explain where this would hurt. Like the stress tests in the previous lens, this is a problem control researchers name and work on themselves.

#### Article
source:: [[../articles/stastny-misalignment-and-strategic-underperformance-an-analysis-of-sandbagging-and-exploration-hacking]]
from:: "## Sandbagging can cause a variety of problems"
to:: Training does in fact make sandbagging way harder, as we will discuss in the next section.

#### Text
content::
Their overall view, from the start of the post:

#### Article
from:: Overall, we are highly uncertain about the difficulty of preventing sandbagging.
to:: But overall, sandbagging risk seems substantially lower if we carefully apply countermeasures discussed in this post.

#### Question: Open
id:: 303613b0-2816-4ee7-91da-771aa8ed4ceb
force-feedback:: first
content::
\## Where would sandbagging hurt control?

Pick one of the four contexts the authors list. How could a sandbagging model there make a lab think its control protocol is safer than it is?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Stastny and Shlegeris list four contexts where deliberate underperformance is especially bad: dangerous capability evaluations (for a control safety case the red team must draw powerful, sneaky attacks out of the untrusted model, which has an incentive to hold back so it is deployed with less scrutiny), AI safety research, untrusted monitoring (a misaligned monitor may fail to flag attacks, and may hide how well it can collude), and generating training signals. 40: a context named and correctly described. 60: a concrete path from sandbagging in that context to a lab overrating its protocol's safety, for example: the model holds back its attacks in the evaluation, so the red team finds only weak attacks and the measured safety is too high; or an untrusted monitor looks reliable in testing but lets real attacks through, or hides its ability to recognise attacks written by another copy of itself. For safety research or training signals, credit a path such as safety work that looks fine but is weak, so the lab believes its protections are better than they are. 30 of these 60 for a path that is only asserted. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "In a control evaluation, the red team asks the untrusted model to come up with its sneakiest attacks. A scheming model could deliberately produce weak ones. Then the monitor catches everything in testing, the lab reports high safety, and the model is deployed with less scrutiny, even though in deployment it would use its real, better attacks."
feedback-instructions:: The learner explains how sandbagging in one context could make a lab overrate its control protocol. Strong answers give a concrete path: the model holds back its attacks during the red team's evaluation, so measured safety is too high; or an untrusted monitor fails to flag attacks or hides its collusion ability, so monitoring looks more reliable than it is. Name the strongest part, then the single most useful fix. One turn, 60 to 110 words. No generic praise. If the learner is stuck, ask: in an evaluation, who decides how good the attacks are?
