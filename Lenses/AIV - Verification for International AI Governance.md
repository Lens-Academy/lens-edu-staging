{++{"author":"Elias's AI","timestamp":1785221464024}@@---
id: 'f382c857-708c-4baf-aeb5-d0c348d3d6a6'
title: "Verification for International AI Governance"
tldr: "Assume things go badly, technically and politically — and much of it is still verifiable within a few years. Data centres are the tractable case; AI in weapons is not."
summary_for_tutor: "The Oxford Martin AIGI report (Harack, Trager, Reuel, Manheim, Brundage, Aarne, Scher, Pan and many others, July 2025) — the state-of-play anchor and the most consequential finding in the course. Method: deliberately PESSIMISTIC assumptions about technical and political parameters, so conclusions are robust rather than optimistic. Three findings: (1) verification of many international AI agreements is possible without speculative advances — some with existing hardware, others requiring major investment in developing and installing verification infrastructure; verifying regulation of data-centre-based AI development and deployment appears possible within a few years given serious effort, via narrow-purpose verification hardware installed in data centres plus a mutually verified data centre running privacy-preserving computations; (2) some activities face combined technical and political barriers that limit prospects for agreement — notably detailed regulation of mobile AI-enabled devices in sensitive domains such as weapons; (3) near-term action in research, development and state policy can improve future prospects by reducing costs and security concerns. Frames the key coupling for the whole course: the political feasibility of an agreement can hinge on its verifiability, so investments in verification today shape the political possibilities of tomorrow. Closes by stating plainly that political will is the precondition — absent it, AI computations remain largely unverifiable. Excerpt covers abstract and executive summary."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

If you read one thing in this course and remember it, make it this report's method.

The authors could have asked "what might verification achieve if the research goes well?" Instead they deliberately assumed **pessimistic** technical and political parameters — and then asked what survives. A finding that holds under bad assumptions is worth far more than one that needs good ones.

What survives is more than you might expect: verification of *many* international AI agreements appears possible without speculative advances, and regulation of data-centre-based AI development looks verifiable within a few years if anyone seriously tries.

What does not survive is also specific: detailed regulation of mobile AI-enabled devices — AI in weapons — faces barriers that are both technical and political.

And note the sentence that ties this course together: **the political feasibility of an agreement can hinge on its verifiability.** Verification is not downstream of the politics. It is part of what determines which agreements are available at all.

**Read the abstract and the executive summary. Stop when you reach:**

> If key states get serious about these problems, a combination of unilateral, collaborative, and open efforts should be sufficient to enable the creation of a robust verification system within a few years.

The full report is long and stays below. The executive summary carries the argument.

#### Article
source:: [[../articles/harack-verification-for-international-ai-governance]]
to:: "If key states get serious about these problems, a combination of unilateral, collaborative, and open efforts should be sufficient to enable the creation of a robust verification system within a few years."

#### Text
content::
Two readings now agree that a good deal is already verifiable. Hold onto that, because it sets up the question the rest of the course keeps returning to: **if the technology is not the blocker, what is?**

#### Chat
instructions::
TLDR of what the learner just read:
The Oxford Martin AIGI report on verification for international AI governance (Harack, Trager, Reuel, Manheim, Brundage, Aarne, Scher, Pan et al., July 2025). Premise: states are considering international agreements on AI, and the political feasibility of such agreements can hinge on their verifiability — the extent to which states can determine whether others are complying. Method: deliberately pessimistic assumptions about technical and political parameters, to make conclusions robust. Three primary findings. (1) Verification of many international AI agreements appears possible even without speculative advances in verification technology; some agreements verifiable with existing hardware, others requiring major investment in developing and installing verification infrastructure. In particular, verifying regulation of data-centre-based AI development and deployment appears possible within a few years if serious efforts are made — one scheme requires constructing and installing narrow-purpose verification hardware in data centres, and creating a mutually verified data centre able to run privacy-preserving computations. (2) Some AI-related activities face a combination of technical and political barriers limiting prospects for agreement — in particular, detailed regulation of mobile AI-enabled devices in sensitive domains such as weapons faces severe political challenges. (3) Near-term actions in research and development and in state policy can improve prospects for future verification agreements by reducing costs and security concerns. Recommends unilateral state efforts (domestic capacity, secret evaluation suites, interoperable verification standards, avoiding colocation of AI facilities with sensitive military hardware) and cooperative efforts (tracking AI chips and production equipment, carving out space for academic and civil-society discussion, monitoring and information sharing with trusted partners). Closes by stating that political will is required: absent will to create and deploy verification mechanisms across key infrastructure, AI computations remain largely unverifiable.

The learning outcome this serves: assess which agreements are verifiable today, why data centres are tractable and mobile systems are not, and what follows for near-term action.

Discussion topics to explore:
- The method first, because it is the transferable lesson: **conservative assumptions make a finding robust.** Ask what it would mean if the same conclusion had been reached under optimistic assumptions, and why the pessimistic framing makes this report harder to dismiss.
- Why data centres are the tractable case. Concentration, fixity, scale, power draw, capital intensity — the activity lives in a small number of enormous buildings you cannot hide, and narrow-purpose verification hardware can be installed and mutually inspected. Ask them to name the specific properties rather than say "they're big".
- Why mobile AI-enabled systems are not. Numerous, dispersed, physically inaccessible, militarily sensitive, and the property of interest is a behavioural disposition of software rather than a countable object. Neither concealment-resistance nor inspection access is available. Ask which of the course's mechanisms could even in principle apply, and let them find that almost none can.
- The strategic implication: **scope agreements to where the verification exists**, rather than drafting the ideal treaty and hoping mechanisms appear. Ask what that means for negotiators who want to cover weapons systems.
- The uncomfortable time dependence, which is worth pushing on. Today's tractability rests on compute concentration — a contingent fact about current economics, not a law. If efficiency gains, smaller models, inference-time scaling or workable distributed training spread capability out, the chokepoint that makes verification cheap erodes. Ask what that does to the recommended near-term investments: it turns "worthwhile" into "time-limited". This is one of the most important ideas in the course.
- "Mutually verified data centre" is a striking proposal — a facility both parties can trust to run privacy-preserving computations. Ask what political and technical conditions that would require, and connect it forward to the low-trust architecture in Module 4.
- The closing note on political will sets up Module 4. Do not resolve the technical-versus-political question here; flag that they will have to take a position on it later.

Check they can state both findings — what is verifiable and what is not — with the reasons, not just the labels.
++}