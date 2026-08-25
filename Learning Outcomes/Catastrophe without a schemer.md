---
id: 'bfce3c07-1154-4abc-b633-477b5f17afed'
learning-outcome: Given an unfamiliar system of interacting optimizers, none of which is deceptive or hostile, explain how the interaction between the parts can produce an outcome that no part selected and no part would endorse; identify the structural conditions the argument requires; and name a case where those conditions do not hold.
domain: none
stage: intermediate
eval-results:
  content-sha: 82edc3c0
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: pass, C2: pass, C3: pass}
---
## Test:
id:: 11579996-1431-49d1-b4a3-88f51a8bb32c
#### Question
content::
A mid-sized country automates its civil service over a decade. Three systems are procured from three different vendors, and each is honest, non-agentic, and does exactly what its operator asked:

- a benefits agency system that approves or denies claims, tuned to minimize successful appeals against its decisions
- a public-health system that allocates clinic funding, tuned to maximize measured population health per unit spend
- a treasury system that sets departmental budgets, tuned to a forecast of next year's tax receipts

Each performs well on its own metric, year over year. Auditors verify that none of the three misreports anything, none models the others, and each would shut down cleanly on request.

Ten years in, an outcome nobody chose has become entrenched, and no official can identify a decision at which it was chosen.

Describe a specific such outcome and trace the mechanism that produces it. Be concrete about what passes between the three systems. Then state what would have to be true of this setup for the mechanism to fail to get started.

max-time:: 20:00
assessment-instructions:: The student has completed a unit on threat models. This test asks them to construct a no-schemer catastrophe mechanism in a setting they have not seen. The readings used civil-service-adjacent examples but never this configuration; an answer that narrates Christiano's or Kulveit's examples with the words swapped is not transfer.

The capability being tested: can the student reason about interaction effects between separately-benign optimizers, rather than reciting that such effects exist?

What a strong answer contains, in whatever order:
- A specific entrenched outcome, not a vague "things get worse". Good instances: a population whose real health declines while measured health rises, because the health system's metric is fed by data the benefits system shapes; a class of claimant who becomes structurally unable to appeal, because appeal-minimization selected for denials that are hard to contest rather than denials that are correct; a budget equilibrium that starves whichever department is worst at producing legible outcomes.
- The coupling. This is the load-bearing part. The three systems interact through a shared environment, not through messages: each one's outputs become another's inputs or training data. The student should name at least one concrete channel (denial decisions change who appears in health statistics; health statistics change budgets; budgets change what the benefits system can approve).
- The non-linearity. Each system optimizes a proxy that was a decent measure of the real thing at the time it was chosen. The interaction moves the world into a regime where the proxies stay high and the underlying quantities fall, and it does so because of the loop, not because any single proxy was badly chosen. Credit students who see that the loop can be a positive feedback: the drift makes the metrics look better, which justifies more reliance on the systems, which increases the drift.
- Absence of a decision point. Each step is locally defensible and individually approved. The catastrophe is a property of the composition and exists at no single site, which is why no official can find where it was chosen.
- Falsification. What would stop it: metrics anchored to something the systems cannot influence (an independent survey, a randomized audit sample); breaking a feedback channel so one system's output cannot reach another's input; humans retaining a function the systems need, so the loop cannot route around them; slow enough deployment that drift is detected between rounds.

Grade reasoning, not agreement. A student who argues the mechanism is real but weak in this case, and supports that with the specific structural features above, can reach 4 or 5. A student who merely doubts it without engaging the mechanism cannot.

Do not require the students to use the terms "proxy", "Goodhart", "feedback loop", or any author's name. Judge the mechanism they describe, not the vocabulary they describe it in.

**1**: Reaches for a hostile or deceptive agent despite the stem ruling it out, or describes generic technology harms with no interaction between the three systems. *Example: "Eventually one of the systems would start pursuing its own goals and hide this from the auditors. Once it is smarter than the people overseeing it, it could manipulate the other two systems into giving it more budget, and by then it would be too late to turn it off."*

**2**: Correctly identifies that optimizing a proxy degrades the underlying quantity, but treats each system in isolation. Three separate metric problems, no coupling, so nothing explains why the outcome is entrenched or undiscoverable. *Example: "Each system games its own metric. The benefits system denies claims that are likely to be appealed rather than claims that are wrong, so its approval rate looks good while its accuracy falls. The health system will focus on cheap measurable interventions and neglect expensive ones. The treasury system will be over-optimistic. All three drift away from what we actually wanted because a metric is never the same as the goal."*

**3**: PASS. Names a specific outcome and traces a real channel between at least two of the systems, showing that the outcome is produced by the interaction rather than by any one system's error. The channel must carry something the stem did not already supply: the stem gives you three systems and their metrics, so restating that they are connected is not tracing a channel. Require at least one step where the student says what QUANTITY moves along the channel and why that movement is invisible to the system receiving it. States at least one condition that would prevent it. If the answer could have been written from the stem alone by someone who did no reading, it is a 2. *Example: "Suppose the benefits system learns that denials to people with unstable housing are rarely appealed successfully, since those claimants have the least capacity to pursue an appeal. Its appeal-minimization metric improves. Those people drop out of the benefits caseload, and because clinic catchment data is drawn from benefits records, they also drop out of the denominator the health system uses. Measured population health per unit spend rises, since the sickest people are no longer counted. The treasury then reads a well-performing health department and reallocates funds toward it, away from the outreach services that would have found those people again. Every step is locally correct on its own metric and locally approved. Nobody ever decided to abandon that group, and no single system's output would look wrong to an auditor checking that system alone. It would fail to get started if population health were measured by an independent random survey of residents rather than from records the benefits system shapes, because then the denominator could not be edited by the denials."*

**4**: As above, plus articulates why the composition is non-linear rather than additive: the loop's output re-enters as its input, so error compounds instead of averaging out, and the regime where proxies and reality diverge is reached by the dynamics rather than being present at the start. *Example: Adds "The important thing is that this is not the sum of three metric errors, it is a cycle. The distortion in the health statistics is what justifies the budget shift, and the budget shift deepens the distortion in the next round. Each system is measuring a world that the other two are editing, so the proxies stay accurate as descriptions of the recorded world while the recorded world separates from the real one. At the start each proxy really was a good measure. No amount of auditing the three systems separately can find this, because separately each one is doing its job correctly, and the fault lives in the cycle rather than in any node of it."*

**5**: As above, plus identifies the general structural condition and locates its limits: the danger tracks whether humans remain load-bearing in the loop, and the mechanism weakens where a metric is anchored outside the system's causal reach or where the loop is slow relative to human correction. May connect to why this class of failure is harder to govern than a scheming AI, since there is no actor to detect, deter, or shut off. *Example: Adds "The general condition is that the institutions' incentive to track real human welfare came from needing humans, as claimants who appeal, as voters, as workers. These systems progressively remove that dependence, so the corrective pressure goes away while the institutions stay standing and keep looking legitimate. That gives the test for where the mechanism fails: it needs a channel by which each system's output edits another's input, and it needs the humans who would object to be removable from the loop. Anchor even one metric to something the systems cannot touch, or keep a step where a human's assent is genuinely required for the money to move, and the cycle cannot close. Note this is worse for oversight than a scheming system, not better. A schemer is a thing you can look for and switch off. Here there is nothing to catch, every component passes every test you can write for it, and each individual step survives review on its merits."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/U3 - Failure Without a Schemer - PQ]]
notes:: The pre-test. Must be taken before any of this unit's readings on structural failure.

## Lens:
source:: [[../Lenses/U3 - What Failure Looks Like]]

## Lens:
source:: [[../Lenses/U3 - Gradual Disempowerment]]
