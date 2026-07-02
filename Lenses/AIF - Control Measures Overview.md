{++{"author":"AI","timestamp":1782975219008}@@---
id: 572dba59-26f9-4993-b2e7-4df0bea70624
title: "AIF - Control Measures Overview"
---

#### Text
content::
(More in the technical weeds — treat as optional if short on time.) The catalog of actual control measures: what you can concretely do to an untrusted model, from monitoring to resampling to permission architecture.

#### Article
source:: [[../articles/greenblatt-an-overview-of-control-measures]]

#### Chat
instructions::
TLDR of what the user just read: Greenblatt's overview of control measures: trusted monitoring (weaker trusted models scoring untrusted outputs), untrusted monitoring (with anti-collusion measures), human auditing of the most suspicious actions, resampling/deferring, sandboxing and least-privilege affordances, paraphrasing/information control, and security measures against exfiltration — and how measures compose into protocols.

Discussion topics to explore:
- Which measures give the most safety per unit of usefulness lost?
- How do monitoring, auditing, and resampling compose into a full protocol (connect to execute/replace/audit)?
- Which measures could today's labs deploy this year with modest effort?

Check they can name 4+ distinct control measures and the failure mode each targets.
++}