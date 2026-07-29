---
id: 'dbcda91b-10ce-4205-8cc2-5339dfc6d2a7'
learning-outcome: "Classify verification methods for AI agreements as national technical means, access-dependent, or hardware-dependent, and pair each class with the evasion route that defeats it and the cooperation it demands"
domain: "[[../Domains/Governance and Policy]]"
{++{"author":"Elias's AI","timestamp":1785319805454}@@stage: advanced
++}requires:
  - "[[The verification problem for AI agreements]]"
authors:
  - Elias+Claude
---
## Test:
id:: 9c2cb793-41af-409d-b02d-9cb344d137fb
#### Question
content:: Wasil and co-authors catalog verification methods and then, for each one, describe how a determined state would get around it.

**Lay out the three classes of method, and for each: what cooperation does it require from the state you distrust, and what is its characteristic evasion? Then say what follows for how a real regime should be assembled.**
assessment-instructions::
Score according to the following rubric.

**1** — Lists methods with no organizing principle, or cannot distinguish methods by the cooperation they need. Treats evasion as a reason verification is hopeless. *Example: "There's satellites, inspections, and chip tracking. But countries can always cheat, so verification doesn't really work."*

**2** — Recovers roughly the three classes but the cooperation axis is muddled, and evasions are named generically ("they'd hide it") rather than matched to the specific method they defeat. *Example: "National technical means is spying, then there's inspections which need permission, and hardware controls. Each one can be evaded by concealment."*

**3** — Gets the classification and its logic: **national technical means** work with essentially no cooperation from the target — satellite imagery, power-consumption and construction signatures, procurement and shipping records, signals intelligence — and are evaded by concealment and dispersal (siting compute underground or inside existing industrial load, splitting a run across facilities, masking the power signature). **Access-dependent methods** require the target's consent — declarations, on-site inspection of data centers, interviews, whistleblower channels — and are evaded by sanitizing what inspectors see, timing around scheduled visits, and maintaining undeclared sites. **Hardware-dependent methods** attach the guarantee to the chips themselves — supply-chain accounting, export restriction, on-chip mechanisms — and are evaded by smuggling and shell purchasers, tampering with or spoofing the on-chip mechanism, and using chips outside the regime's jurisdiction. States the corollary: because each class fails to a different evasion, coverage comes from layering classes, not from picking the best one. *Example: "National technical means need nothing from the other side — imagery, power draw, construction, shipping records — and they lose to concealment: put it underground, hide the load inside an industrial site, split the run across buildings. Access-dependent methods need consent — declarations and on-site inspections — and they lose to a sanitized tour and an undeclared facility next door. Hardware-dependent methods bind the check to the chips — supply-chain accounting, export controls, on-chip mechanisms — and they lose to smuggling, front companies, and tampering. Since each one fails differently, the point isn't to find the strong one, it's to stack them so that a single evasion doesn't buy you anything."*

**4** — As above, plus articulates why layering actually works rather than just sounding prudent: the evasions are not independent, and the measures a violator takes to defeat one method tend to create the signature another method looks for. Concealing power draw constrains how much compute you can run; dispersing a training run raises interconnect requirements and multiplies the sites that must all stay quiet; keeping a facility undeclared means it cannot appear in the procurement records that would legitimize its chips. The regime's strength is the joint difficulty of satisfying all the evasions at once. *Example: Adds "The reason stacking helps is that the evasions fight each other. Hiding your power signature caps how much compute you can actually draw. Splitting the run across sites means more buildings that all have to stay secret and a networking problem you now have to solve. Running an undeclared facility means its chips can't show up in any legitimate procurement record. You're not asking the violator to beat one method, you're asking them to satisfy several mutually inconvenient constraints simultaneously — and that's a much smaller space of workable cheats."*

**5** — As above, plus reasons about the regime as a design problem under constraint: methods differ not only in evadability but in intrusiveness, cost, and political acceptability, so the goal is a portfolio on the efficient frontier — maximum residual confidence per unit of intrusion and per unit of political capital spent. Notes that this reframes research priorities: the highest-value work is on mechanisms that buy confidence cheaply in political terms (privacy-preserving, narrowly scoped, verifiable by the distrusted party's own instruments), because the binding constraint on a real regime is usually acceptability rather than physics. *Example: Adds "Once you see it as a portfolio, the question stops being 'which method is strongest' and becomes 'which combination buys the most residual confidence per unit of intrusion and political cost.' That's why the research frontier sits where it does — on mechanisms that are cheap politically: narrowly scoped, privacy-preserving, checkable with instruments the distrusted party owns. Physics isn't usually what stops a regime. Somebody refusing to sign is."*
max-chars:: 1800

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - Verification Methods and Their Evasions]]
