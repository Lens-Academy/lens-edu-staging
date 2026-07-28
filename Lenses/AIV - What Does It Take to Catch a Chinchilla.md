{++{"author":"Elias's AI","timestamp":1785221466526}@@---
id: '2f754c84-fb9c-4a59-a569-d1af1cc819df'
title: "What Does It Take to Catch a Chinchilla?"
tldr: "The founding move of the field: you cannot inspect a training run while it happens, but chips remember. Snapshot the weights, keep the receipts, count the chips."
summary_for_tutor: "The foundational reading of the course (Shavit 2023). Establishes the verification problem — governments may want to enforce rules on large-scale ML training, and rule-breakers will not comply if they expect to go unnoticed — and proposes the three-part compute-monitoring framework that most later work builds on or reacts against: (1) on-chip firmware that periodically snapshots weights in device memory, (2) retained training documentation that must prove the claimed run produced those snapshots (a Proof-of-Learning / Proof-of-Training-Transcript problem), (3) supply-chain accounting so no actor accumulates undeclared chips. Introduces the Prover/Verifier framing and the insight that verification can rest on random inspection of a sample of chips rather than continuous surveillance. Excerpt runs from the introduction through the solution overview; the per-stage detail in sections 4-6 is available collapsed for learners who want it."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

This is the paper the rest of the field argues with, so it is worth reading properly.

Shavit's problem: suppose governments want to enforce a rule on large-scale AI training. Law-abiding labs will comply. The actors you actually worry about will not — *especially if they believe the violation will go unnoticed*. So the rule is only as real as your ability to check it.

His answer starts from an observation that sounds almost too simple: you cannot watch a training run as it happens, but the chips that did the training are physical objects that persist, and they can be made to remember.

**Read from the beginning and stop when you reach:**

> For the Verifier to ascertain compliance from simply inspecting a chip, we will need interventions at three stages: on the chip, at the Prover's data-center, and in the supply chain.

That covers the problem, what kinds of rules are enforceable, and the shape of the solution. The rest of the paper — the detail of each of the three stages — stays available below if you want it, and it is genuinely interesting, but it is not required here.

Return when you're done.

#### Article
source:: [[../articles/shavit-what-does-it-take-to-catch-a-chinchilla-verifying-rules-on-large-scale-neural-network-training-via-compute-monitoring]]
to:: "For the Verifier to ascertain compliance from simply inspecting a chip, we will need interventions at three stages: on the chip, at the Prover’s data-center, and in the supply chain."

#### Text
content::
Notice the structure of what you just read. Three mechanisms, and none of them is sufficient alone. Before you move on, try to say what each one *rules out* — and what a violator could do if you dropped any single one.

#### Chat
instructions::
TLDR of what the learner just read:
Shavit's compute-monitoring framework for verifying rules on large-scale ML training. Governments may want to enforce limits on frontier training runs; rule-violators will not comply voluntarily, particularly if they expect not to be caught, so the rule depends on verification. The framework centres on random chip inspection — the Verifier inspects a sufficient random sample of the Prover's ML chips and confirms none contributed to a rule-violating run — supported by interventions at three stages: (1) on the chip, firmware that periodically logs/snapshots weights held in device memory, making the artifact non-deniable; (2) at the data centre, retained training documentation sufficient to prove to a Verifier that the claimed training process produced those snapshotted weights (the Proof-of-Training-Transcript / Proof-of-Learning problem); (3) in the supply chain, a chip-owner directory and accounting so no actor assembles a large undeclared cluster. Distinguishes "ML chips" (high-interconnect accelerators) from consumer GPUs. Notes that trust in the on-chip mechanisms is itself a problem, and recommends open-source hardware-roots-of-trust so untrusting Verifiers can validate designs for backdoors.

The learning outcomes this serves: (a) why international AI agreements need technical verification and why AI is harder than nuclear; (b) the three-part compute-accounting regime and what each part rules out.

Discussion topics to explore:
- The interlock. Ask them to remove one leg and say what breaks. Without snapshots, the transcript is unfalsifiable paperwork. Without transcripts, a snapshot is billions of uninterpretable numbers. Without supply-chain accounting, both are irrelevant because the violation happens on chips outside the regime. Each leg closes a *different* escape route — this is the key structural insight.
- The trust boundary. The scheme puts its root of trust inside hardware physically possessed, powered, and operated by the party being constrained. Ask whether that can hold against a state adversary with unlimited physical access and time. Shavit himself flags supply-chain attacks as beyond the paper's scope.
- Random sampling. Verification does not require inspecting every chip. Ask why a random sample suffices — it should lead them to the deterrence logic: you need the probability of detection high enough that cheating stops paying, not certainty.
- The premise with an expiry date. The framework assumes concentrated specialized compute is the chokepoint. Ask what happens to it if algorithmic efficiency, smaller models, or inference-time scaling let you reach frontier capability without a landmark training run.
- Proof-of-Learning as the load-bearing unsolved piece: checking the transcript must be far cheaper than re-running the training, or the Verifier's job is impossible.

Ask what struck them as the weakest link. Check that they can state what each of the three parts rules out — that is the thing to walk away with.

Do not resolve the tamper-resistance problem for them; it is genuinely open and later readings return to it. Stay grounded in the paper.
++}