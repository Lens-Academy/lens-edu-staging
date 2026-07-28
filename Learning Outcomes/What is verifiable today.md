{++{"author":"Elias's AI","timestamp":1785221457063}@@---
id: 'b5b5b628-c9fb-409c-a64f-4a3313c24a8f'
learning-outcome: "Assess which international AI agreements are verifiable with existing or near-term technology, and explain why data-center-based development and deployment is the tractable case while mobile AI-enabled systems are the hard case"
domain: "[[../Domains/Governance and Policy]]"
stage: intermediate
requires:
  - "[[Verification methods and their evasions]]"
authors:
  - Elias+Claude
---
## Test:
id:: 'd42dd4a7-6562-42aa-af58-c2a7dc955008'
#### Question
content:: A common assumption is that verifying AI agreements is a problem for the future — that it waits on breakthroughs nobody has made yet. The Oxford AIGI report, written under deliberately conservative assumptions, reaches a different conclusion.

**What is that conclusion, and what distinction does it rest on? Explain why data centers are the tractable case and mobile AI-enabled systems the hard one — and say what this implies for what should be done now.**
assessment-instructions::
Score according to the following rubric.

**1** — Reports that verification is impossible or entirely future-dependent, missing the report's actual finding. Draws no distinction between kinds of agreement. *Example: "The report says we can't verify AI agreements yet and need more research first."*

**2** — Recalls that some verification is feasible now, but cannot say which agreements or why, and treats the data-center / mobile-systems distinction as incidental. *Example: "They found some things are verifiable with current technology. Data centers are easier than weapons systems."*

**3** — States the finding: **many** international AI agreements are verifiable with existing or near-term technology — no revolutionary advance required — and the political feasibility of an agreement hinges on its verifiability, so this matters directly for what can be negotiated. Explains the distinction correctly: data-center-based development and deployment is tractable because the activity is concentrated in a small number of large, fixed, power-hungry, capital-intensive facilities that are hard to hide and where narrow-purpose verification hardware can be installed and mutually inspected. Mobile AI-enabled systems — AI in weapons and other deployed devices — are the hard case: they are numerous, dispersed, physically inaccessible, militarily sensitive, and the relevant property is a behavioral disposition of software rather than a countable object, so neither concealment-resistance nor inspection access is available. *Example: "The headline is that a lot of agreements are already verifiable — this isn't waiting on a breakthrough — and that matters because whether an agreement is verifiable is a big part of whether it's negotiable at all. The split is about where the activity lives. Frontier training and large-scale inference happen in a handful of enormous fixed buildings that draw enormous power and cost a fortune; you can find those, and you can install narrow-purpose verification hardware in them that both sides agree to inspect. AI inside mobile military systems is the opposite: thousands of dispersed units nobody will let you near, where the thing you'd want to check is how the software behaves, not an object you can count."*

**4** — As above, plus draws the strategic implication: because verifiability varies by agreement type, the near-term move is to negotiate the agreements that are verifiable rather than the ones that would be ideal — scope the obligation to where the verification exists. Notes that the report's conservative assumptions strengthen the conclusion: if verification is feasible even granting pessimistic technical and political premises, the finding is robust rather than optimistic. *Example: Adds "The practical upshot is to shape agreements around the verification you can actually get, instead of writing the ideal treaty and hoping the mechanisms show up. And it's worth noting how the conclusion was reached: they assumed things go badly — technically and politically — and still found feasibility. A finding that survives pessimistic assumptions is much more useful than one that needs optimistic ones."*

**5** — As above, plus reasons about the dynamics: today's tractability rests on compute concentration, which is a contingent fact about the current technology and economics, so the window for data-center-based verification could narrow if capability decentralizes (efficiency gains, smaller models, inference-time scaling, distributed training). This makes the recommended near-term investments — in verification research and in state policy that lowers the cost and security risk of participating — time-sensitive rather than merely worthwhile, and argues for building the regime while the chokepoint still exists. *Example: Adds "The uncomfortable part is that the tractable case is tractable because of an accident of the current cost curve: capability is concentrated in giant facilities. That's not a law. If efficiency gains, smaller models, inference-time scaling, or workable distributed training spread capability out, the chokepoint that makes verification cheap today erodes. Which turns 'we should invest in verification research and in policy that makes participating cheaper' from good advice into a deadline — you want the regime standing while the chokepoint is still there to hang it on."*
max-chars:: 1800

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - Verification for International AI Governance]]

## Lens:
source:: [[../Lenses/AIV - Verifying International Agreements on AI]]
notes:: The RAND working paper; pairs with the Oxford report as the state-of-play anchor.
++}