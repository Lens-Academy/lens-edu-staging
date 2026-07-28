{++{"author":"Elias's AI","timestamp":1785221468237}@@---
id: '821d4e91-fbec-44d5-9140-5847d66e8e02'
slug: aiv-m1-why-verification
title: "Why Verification, and the Compute Chain"
readings:
  - "Shavit 2023, What does it take to catch a Chinchilla?"
  - "Wasil et al. 2024, Verification Methods for International AI Agreements"
authors:
  - Elias+Claude
---

# Learning Outcome:
source:: ![[../Learning Outcomes/The verification problem for AI agreements]]

# Learning Outcome:
source:: ![[../Learning Outcomes/Compute accounting for training runs]]

# Learning Outcome:
source:: ![[../Learning Outcomes/Verification methods and their evasions]]

# Lens: Welcome
id:: 'f4032140-2e7b-4c07-8abd-a4c84cfe9d3d'
tldr:: Nuclear arms control had radiation, seismographs, and warheads you could count. An AI agreement has a building full of chips that looks like every other building full of chips. This module asks what you would actually go and look at.
summary_for_tutor:: Opening framing lens for Module 1 of the AI verification course. Establishes why verification is a precondition for international AI agreements rather than an add-on — an agreement nobody can check is one nobody can rationally comply with, so verifiability partly determines which agreements are politically available. Then previews the two foundational readings: Shavit's compute-monitoring framework (on-chip weight snapshots, training transcripts / Proof-of-Learning, chip supply-chain accounting) and Wasil et al.'s catalogue of methods paired with their evasions, organised by how much cooperation each demands from the distrusted party. Framing text only; teaching happens in the following lenses.

#### Text
content::
Suppose two rival states agree to stop building AI systems above some capability threshold. The agreement is signed. Now what?

If neither side can tell whether the other complied, the agreement is not merely weak — it is *irrational to keep*. A defector gains, a complier loses, and both know it. Which means verifiability is not a feature you add to an agreement after the diplomacy. **It partly determines which agreements are available at all.**

The trouble is that we have one good historical model for this, and it does not transfer. Nuclear arms control could lean on physics: fissile material is rare, enrichment plants are enormous and distinctive, tests shake the ground, warheads are objects you can count. AI offers none of that. A training run is chips drawing power in a building that looks like every other data centre — and the thing you would most want to inspect, the weights, is the most commercially sensitive object the lab owns.

So this module works the foundations:

- **Why verification at all**, and exactly which properties of AI make it harder than the nuclear case.
- **The compute chain.** Shavit's founding proposal: you cannot watch a training run happen, but chips are physical objects that persist and can be made to remember. Snapshot the weights, keep the receipts, count the chips — and none of the three works without the other two.
- **The map, and the ways around it.** Wasil and co-authors catalogue verification methods and then, for each one, how a determined state would evade it. Read as a list this looks discouraging. Read as a design brief it says something more useful: the evasions interfere with each other.

One idea to carry through the whole course, because most confusion about verification comes from missing it: **verification does not have to be leak-proof.** It has to make cheating at a scale that matters unlikely enough to be a bad bet. "You could always hide one GPU" is not an objection.

# Lens:
source:: ![[../Lenses/AIV - Why Verification - PQ]]

# Lens:
source:: ![[../Lenses/AIV - What Does It Take to Catch a Chinchilla]]

# Lens:
source:: ![[../Lenses/AIV - Verification Methods and Their Evasions]]
++}