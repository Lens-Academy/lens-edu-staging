---
id: 'ca532e24-9835-4a3d-acb8-681fff1cedf2'
title: "Verification Methods and Their Evasions"
tldr: "Ten methods, and for each one, how a determined state gets around it. The lesson is not that verification fails — it's that the evasions fight each other."
summary_for_tutor: "Wasil, Reed, Miller and Barnett's catalogue of verification methods for international AI agreements, organised by how much cooperation each requires from the state you distrust: national technical means (satellite imagery, energy-consumption and construction signatures, procurement and shipping records, signals intelligence — no cooperation needed), access-dependent methods (declarations, on-site data-centre inspection, interviews, whistleblower channels — require consent), and hardware-dependent methods (supply-chain accounting, export restriction, on-chip mechanisms — bind the guarantee to the chips). The paper's distinctive move is pairing every method with its evasion, and the learner's job is to see why layering classes produces coverage that no single method has: the evasions are not independent, and defeating one method tends to create the signature another looks for. Also introduces the two target violations (unauthorized high-compute training runs, clandestine data centres) and the legacy-hardware problem for hardware-dependent measures."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

Shavit gave you one mechanism. This reading gives you the map — and then, for every method on it, the way around it.

Read it the way the authors intend: adversarially. For each method, hold two questions at once. *What cooperation does this need from the state I don't trust?* And *what would I do to defeat it?*

The organizing axis is that first question, and it produces three families: methods that need nothing from the target, methods that need its consent, and methods that ride on the chips themselves.

**Read from the beginning and stop when you reach:**

> Overall, hardware-dependent methods represent a promising but long-term goal, requiring sustained international cooperation and technological innovation to realize their full potential in AI governance.

That covers the executive summary, what is being verified, and all three families of method. The limitations discussion and appendices are below if you want them.

#### Article
source:: [[../articles/wasil-verification-methods-for-international-ai-agreements]]
to:: "Overall, hardware-dependent methods represent a promising but long-term goal, requiring sustained international cooperation and technological innovation to realize their full potential in AI governance."

#### Text
content::
Read as a list of methods, this paper looks discouraging — everything has a counter. Read as a design brief, it says something else.

Before the discussion: pick any two methods from *different* families and ask whether a violator could evade both at once, cheaply, at the same time.

#### Chat
instructions::
TLDR of what the learner just read:
Wasil, Reed, Miller and Barnett catalogue verification methods for international AI agreements aimed at two violations: unauthorized high-compute training runs and clandestine data centres. Methods are grouped by the cooperation they require. **National technical means** need essentially none — satellite and overhead imagery, energy-consumption and thermal signatures, construction and infrastructure buildout, procurement and shipping records, signals and human intelligence — and are evaded by concealment and dispersal (siting compute underground or inside existing industrial load, splitting runs across facilities, masking power signatures). **Access-dependent methods** require consent — declarations, on-site inspections of data centres, personnel interviews, whistleblower programmes — and are evaded by sanitizing what inspectors see, timing activity around scheduled visits, and maintaining undeclared sites. **Hardware-dependent methods** bind verification to the chips — supply-chain accounting, export controls, on-chip mechanisms — and are evaded by smuggling, shell purchasers, tampering with or spoofing on-chip mechanisms, and using chips outside the regime; they also face the legacy-hardware problem, since advanced chips already in circulation have no built-in mechanisms, requiring retrofit or phase-out.

The learning outcome this serves: classify verification methods by the cooperation they demand, pair each class with its characteristic evasion, and draw the conclusion for how a regime should be assembled.

Discussion topics to explore:
- The central insight to draw out: coverage comes from **layering classes, not from picking the best method**, because each class fails to a different evasion. Push until they can state this in their own words.
- Then push further, because this is where the real understanding sits: **the evasions are not independent, and they interfere with each other.** Concealing your power signature caps how much compute you can actually draw. Dispersing a run across sites multiplies the buildings that must all stay secret and creates an interconnect problem. Keeping a facility undeclared means its chips cannot appear in any legitimate procurement record. The violator is not asked to beat one method — they are asked to satisfy several mutually inconvenient constraints simultaneously. Ask them to construct a cheat that beats two families at once and watch the cost climb.
- The other axis. Methods differ not only in evadability but in intrusiveness, cost, and political acceptability. Ask which methods are cheap technically but expensive politically, and what that implies about where research effort pays off. This should lead to the thought that the binding constraint on a real regime is usually acceptability rather than physics.
- Legacy hardware: chips already in circulation have no on-chip mechanisms. Ask what that does to the timeline for any hardware-dependent scheme.
- If they conclude "so verification is hopeless", treat that as a live position worth testing rather than an error, then ask what standard they are holding it to. Verification does not need to be leak-proof; it needs to make consequential-scale cheating unlikely enough to deter.

Ask which pairing surprised them most. Check that they can name the three families and one specific evasion for each without looking.
