---
id: 977a0418-d91f-457d-87dd-65865e91e3b6
title: "Preventing Collusion Between Monitors"
tldr: Your best monitor for an untrusted model is another copy of the untrusted model, which only works if the two copies can't wink at each other.
summary_for_tutor: "Covers Shlegeris's analysis of untrusted monitoring (using copies of the capable-but-possibly-scheming model to monitor itself) and preventing collusion via paraphrasing inputs (destroying steganographic signals), redacting context so monitors can't distinguish real actions from planted honeypot attacks, checking monitor reports against known-bad examples, and limiting shared information that could coordinate a 'let it slide' policy."
---

#### Text
content::
(More in the technical weeds; treat as optional if short on time.) Your best monitor for an untrusted model is... another copy of the untrusted model. Which only works if the two copies can't wink at each other. The anti-collusion playbook.

#### Article
source:: [[../articles/shlegeris-how-to-prevent-collusion-when-using-untrusted-models-to-monitor-each-other]]

#### Text
content::
Which single anti-collusion measure — paraphrasing, honeypots, or information limits — would you actually stake the whole protocol on? Commit to one, then stress-test it with the tutor against two copies that share weights and Schelling points.

#### Chat
instructions::
TLDR of what the user just read: Shlegeris analyzes untrusted monitoring: using copies of the capable-but-possibly-scheming model to monitor itself, and preventing collusion via strategies like paraphrasing inputs (destroying steganographic signals), redacting context so the monitor can't tell real actions from honeypot tests, checking monitor reports against known-bad examples, and limiting shared information that could coordinate a "let it slide" policy.

Discussion topics to explore:
- Why use untrusted monitors at all when trusted (weaker) monitors exist?
- Which anti-collusion measure seems most robust: paraphrasing, honeypots, or information limits?
- How would AIs even coordinate collusion without communicating (shared Schelling points from shared weights)?

Check they can explain the honeypot test: if the monitor fails to flag a planted attack, you've incriminated the monitor.
