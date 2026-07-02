---
id: 977a0418-d91f-457d-87dd-65865e91e3b6
title: "Preventing Collusion Between Monitors"
tldr: Your best monitor for an untrusted model is another copy of the untrusted {--{"author":"Elias's AI","timestamp":1783002593133}@@model —--}{++{"author":"Elias's AI","timestamp":1783002593133}@@model,++} which only works if the two copies can't wink at each other.{--{"author":"Elias's AI","timestamp":1783002593133}@@ The anti-collusion playbook — paraphrasing, honeypots, information limits — against adversaries that share weights and Schelling points.--}
summary_for_tutor: "Covers Shlegeris's analysis of untrusted monitoring {--{"author":"Elias's AI","timestamp":1783002594848}@@— using--}{++{"author":"Elias's AI","timestamp":1783002594848}@@(using++} copies of the capable-but-possibly-scheming model to monitor {--{"author":"Elias's AI","timestamp":1783002594848}@@itself —--}{++{"author":"Elias's AI","timestamp":1783002594848}@@itself)++} and preventing collusion via paraphrasing inputs (destroying steganographic signals), redacting context so monitors can't distinguish real actions from planted honeypot attacks, checking monitor reports against known-bad examples, and limiting shared information that could coordinate a 'let it slide' policy."
---

#### Text
content::
(More in the technical {--{"author":"Elias's AI","timestamp":1783002596975}@@weeds —--}{++{"author":"Elias's AI","timestamp":1783002596975}@@weeds;++} treat as optional if short on time.) Your best monitor for an untrusted model is... another copy of the untrusted model. Which only works if the two copies can't wink at each other. The anti-collusion playbook.

#### Article
source:: [[../articles/shlegeris-how-to-prevent-collusion-when-using-untrusted-models-to-monitor-each-other]]

#### Chat
instructions::
TLDR of what the user just read: Shlegeris analyzes untrusted monitoring: using copies of the capable-but-possibly-scheming model to monitor itself, and preventing collusion via strategies like paraphrasing inputs (destroying steganographic signals), redacting context so the monitor can't tell real actions from honeypot tests, checking monitor reports against known-bad examples, and limiting shared information that could coordinate a "let it slide" policy.

Discussion topics to explore:
- Why use untrusted monitors at all when trusted (weaker) monitors exist?
- Which anti-collusion measure seems most robust: paraphrasing, honeypots, or information limits?
- How would AIs even coordinate collusion without communicating (shared Schelling points from shared weights)?

Check they can explain the honeypot test: if the monitor fails to flag a planted attack, you've incriminated the monitor.
