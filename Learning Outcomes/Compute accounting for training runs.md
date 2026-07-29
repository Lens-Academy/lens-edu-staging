---
id: 'e1a40873-ce21-4457-af20-6ff34eb60103'
learning-outcome: "Explain Shavit's three-part compute-accounting regime for verifying training-run compliance — on-chip weight snapshots, retained training transcripts checked by Proof-of-Learning, and chip supply-chain accounting — and explain what each part rules out and why none of them works alone"
domain: "[[../Domains/Governance and Policy]]"
{++{"author":"Elias's AI","timestamp":1785319824322}@@stage: advanced
++}requires:
  - "[[The verification problem for AI agreements]]"
authors:
  - Elias+Claude
---
## Test:
id:: bb9f6daf-a217-4860-b569-3d053a7486f3
#### Question
content:: Shavit's scheme is designed so that an inspector can walk up to a set of chips and establish what they were used to train — without the inspector reading anyone's weights on demand or watching the training as it happens.

**Describe the three components of the regime and what each one rules out. Then explain why removing any one of them breaks the whole thing.**
assessment-instructions::
Score according to the following rubric.

**1** — Cannot reconstruct the components; describes generic "monitoring chips" or confuses the scheme with export controls. *Example: "You track the chips and watch what people train, and if they train something too big you catch them."*

**2** — Names one or two components correctly but treats them as independent good ideas rather than a chain, and cannot say what any of them rules out. *Example: "Chips save snapshots of the weights, and there's supply chain tracking so you know who has the chips."*

**3** — Reconstructs all three: (a) chip firmware periodically snapshots the weights in device memory, so an inspector who later shows up has a record of what the chip was actually working on; (b) the trainer retains documentation of the training run — a transcript — sufficient to demonstrate that the claimed training process produced those snapshotted weights, which is the Proof-of-Learning problem; (c) supply-chain accounting tracks where specialized ML chips went, so nobody assembles a large undeclared cluster. Explains the corresponding role: snapshots make the artifact non-deniable, transcripts explain the artifact, supply-chain accounting bounds the population of chips that could be doing anything at all. *Example: "The chips themselves take periodic snapshots of the weights sitting in memory, so there's a physical record on the device. Then the operator has to keep enough documentation of the training run to show an inspector that the process they claim to have run really is what produced those snapshots — that's the proof-of-learning part. And separately, you account for where the advanced chips physically went, so nobody quietly builds a cluster you've never heard of. Snapshot says 'this is what was on the chip', transcript says 'and here's the legitimate run that made it', supply chain says 'and these are all the chips there are.'"*

**4** — As above, plus explains the interlock precisely: without snapshots the transcript is unfalsifiable paperwork (any story fits, since there is no artifact to tie it to); without transcripts a snapshot is an uninterpretable pile of numbers (you have the weights but no account of how they came to be, so you cannot tell a permitted run from a forbidden one); without supply-chain accounting both are irrelevant because the violation simply happens on chips outside the regime. The chain is only as strong as its weakest link because each component answers a different evasion. *Example: Adds "Drop the snapshots and the documentation is just a story — nothing anchors it to reality, so a compliant-looking transcript costs nothing to fabricate. Drop the documentation and you're holding billions of numbers with no way to say which run produced them. Drop the supply-chain piece and you've built a beautiful audit trail for the chips you know about, while the violation happens on the ones you don't. Each leg closes a different escape route, so removing one doesn't weaken the scheme by a third — it opens a door."*

**5** — As above, plus locates the design's real load-bearing assumptions and their fragility: it needs hardware-level instrumentation that the chip owner cannot disable or spoof (so the trust boundary sits inside silicon the operator physically possesses); it needs Proof-of-Learning to be verifiable at far less cost than re-running the training; and it needs the specialized-chip bottleneck to persist, so algorithmic efficiency gains or a shift toward inference-time scaling erode the premise that "large training run" and "lots of accountable chips" are the same event. Notes that Shavit presents this as one mechanism, not a complete regime. *Example: Adds "The scheme rests on three bets. First, that you can put instrumentation in a chip that its physical owner can't turn off or lie to — the trust boundary is inside hardware the potential violator holds in their hands, which is an unusual and uncomfortable place to put it. Second, that checking a proof-of-learning is far cheaper than redoing the training, or the inspector's job is impossible. Third, that concentrated specialized compute stays the chokepoint. That last one is the one that ages: if efficiency gains or inference-time scaling let you get frontier capability without a landmark training run, the whole framing of 'catch the big run' stops matching what you're trying to catch."*
max-chars:: 1600

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - What Does It Take to Catch a Chinchilla]]
