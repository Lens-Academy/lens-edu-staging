{++{"author":"Elias's AI","timestamp":1785221632660}@@---
id: 'ffff89f9-3e9c-4718-b960-722daac7ed23'
slug: aiv-m4-building-it
title: "Building the Lie Detector, and the Treaty It Serves"
readings:
  - "Cankaya 2026, A system overview for near-term, low-trust AI compute verification"
  - "Cankaya 2026, All hands on deck to build the datacenter lie detector"
  - "Scher et al. 2025, An International Agreement to Prevent the Premature Creation of Artificial Superintelligence"
authors:
  - Elias+Claude
---

# Learning Outcome:
source:: ![[../Learning Outcomes/A low-trust compute verification architecture]]

# Learning Outcome:
source:: ![[../Learning Outcomes/From mechanism to agreement]]

# Lens: Welcome
id:: e38af20b-d323-415e-8343-f549c2df7922
tldr:: Put it together: an architecture that needs nobody to trust anybody's silicon, a call to build it, and the treaty it would serve. Then decide whether the thing standing in the way is technical or political.
summary_for_tutor:: Closing framing lens for Module 4. Frames the module as assembly plus judgement. First the capstone architecture (Cankaya's low-trust system overview): capture/evaluate split, non-programmable taps recording cryptographic commitments, untrusted prover manifest checked against independently captured evidence, air-gapped evaluation with redundant mutually distrusting TCBs from separate supply chains, analog data-movement control, instructor-executor blinding, covert-adversary threat model, near-term feasibility with no new silicon at under ~10% overhead, and honestly stated open problems. Then the call to action framing verification as an orphaned problem and arguing verification infrastructure could defuse the security dilemma driving the race. Then Scher et al.'s concrete proposed agreement (US-China-led coalition, FLOP threshold, ban on dangerous and verifiability-undermining research) as the mapping exercise: which obligations the course's machinery serves well and which it barely touches. Ends by requiring the learner to take a defended position on whether the binding constraint is technical or political, and to see that the two are coupled because verification research lowers the political cost of agreeing. Framing text only.
#### Text
content::
Time to put it together, and then to make a judgement.

**The architecture.** Every mechanism so far has needed someone to trust some silicon — Shavit's logging firmware, flexHEG's guarantee processor. Cankaya's system overview tries to remove that requirement entirely, and to do it with no newly designed chips. Two moves carry it. *Split capture from evaluation*: what runs continuously is deliberately stupid, passive taps recording hashes, because the always-on component must have almost no attack surface; the complicated, expensive work happens later, elsewhere, and rarely. *Buy trust with redundancy rather than authority*: nobody trusts a shared device, each side trusts only its own hardware, several independently-sourced machines do the same computation and cross-check — so a subverted box yields a **disagreement**, not a false clean result.

**The call to build it.** A short, concrete piece arguing this is an *orphaned problem* — noticed by many powerful actors, beneficial to all of them, owned by none. Its larger claim is worth taking seriously: that much of the pressure to race comes from not knowing what a rival is doing, so verification infrastructure is not only an enforcement tool but a way to build your way out of a security dilemma.

**The treaty.** Finally, an actual proposed agreement: a US–China-led coalition, a FLOP threshold capping training scale, and a ban on research advancing toward superintelligence — including research that would undermine the agreement's own verifiability. Read it as a specification and run the mapping. The compute ceiling is almost exactly what this course's machinery was built for. The research ban is almost exactly what it cannot touch.

Then the question this course has been building toward. The Oxford and RAND reports say much of the verification is already feasible. Scher and co-authors say the political will does not exist. So:

> **Is the binding constraint technical or political — and what does your answer imply about what someone should actually work on?**

Get the second half right, because the easy answer is wrong. "It's political, so the engineering doesn't matter" does not follow. Verification research *reduces the political cost of agreeing* — less intrusion, less IP exposed, less espionage surface. The constraints are coupled, not rival. And there is a clock: the mechanisms depend on compute staying concentrated, so a decentralising technology base narrows the window in which any of this is verifiable at all.

# Lens:
source:: ![[../Lenses/AIV - A System Overview for Low-Trust Compute Verification]]

# Lens:
source:: ![[../Lenses/AIV - Build the Datacenter Lie Detector]]

# Lens:
source:: ![[../Lenses/AIV - An International Agreement to Prevent Premature ASI]]
++}