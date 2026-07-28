{++{"author":"Elias's AI","timestamp":1785221627874}@@---
id: '6467b750-b68f-4283-b39b-ebece4690044'
learning-outcome: "Explain why binding international agreements on AI require technical verification to be politically viable, and identify what makes AI agreements harder to verify than nuclear arms-control agreements"
domain: "[[../Domains/Governance and Policy]]"
authors:
  - Elias+Claude
---
## Test:
id:: 5875aea2-b4a3-4510-ab23-3a6adf54f8e1
#### Question
content:: Nuclear arms control had things to look at: radiation signatures, seismic monitoring, missile silos visible from orbit, warheads you can count. An AI agreement has none of that.

**Why does an international AI agreement need verification at all — rather than just signatures on a document — and what specifically makes verifying it harder than verifying a nuclear treaty?**
assessment-instructions::
Score according to the following rubric.

**1** — Treats verification as a nice-to-have, an add-on for building trust, or conflates it with enforcement. Cannot name a concrete disanalogy with nuclear. *Example: "Countries need to trust each other, so it helps to check that they're following the rules. AI is harder because it's newer and more complicated."*

**2** — Sees that unverified agreements are weak, but the reason stays vague — "cheating" without a mechanism — and the AI-vs-nuclear contrast is asserted rather than explained. *Example: "If nobody checks, countries will just cheat. AI is harder to verify because it's all software and you can't see it."*

**3** — Gets the strategic core: an unverifiable agreement is one no party can afford to keep, because a defector gains and a complier loses, so verifiability is a precondition for anyone signing — the political feasibility of an agreement hinges on its verifiability. Names at least two real disanalogies: AI compute is dual-use and commercially ubiquitous rather than a purpose-built weapons complex; the object of interest is a training run or a set of weights, which emits no physical signature; and inspection touches commercially and militarily sensitive IP (weights, data, architecture) in a way counting warheads does not. *Example: "An agreement nobody can verify is one nobody can rationally comply with — if you can't tell whether the other side stopped, stopping yourself is unilateral disarmament. So verifiability isn't a bonus feature, it's what makes signing rational in the first place. Nuclear had physics on its side: fissile material is rare, enrichment plants are huge and distinctive, tests shake the ground. A training run is just chips drawing power in a building that looks like every other data center, and the thing you'd want to inspect — the weights — is the most commercially sensitive object the company owns."*

**4** — As above, plus articulates the structural asymmetry: verification does not need to be perfect, it needs to make covert violation at consequential scale unlikely enough that the expected cost of cheating exceeds the gain. The bar is deterrence of scaled defection, not detection of every violation — which is why "you could always hide one GPU" is not a refutation. *Example: Adds "The standard isn't leak-proof. It's that a violation big enough to matter has to be likely enough to get caught that cheating stops being worth it. Hiding a handful of chips doesn't buy you a frontier model; hiding a hundred-thousand-chip cluster is a much harder thing to keep quiet. Verification wins by pushing the cheapest cheat above the threshold of usefulness."*

**5** — As above, plus connects verifiability to the security dilemma it dissolves: much of the pressure to race comes from not knowing what a rival is doing, so a working verification regime is not merely an enforcement tool but a way to remove the uncertainty that drives acceleration. Also notes the corresponding hazard — verification regimes are themselves intrusive instruments, so the design problem is to buy confidence at the minimum cost in exposed secrets, which is why privacy-preserving mechanisms are load-bearing rather than decorative. *Example: Adds "The deepest argument is that the race is partly an artifact of blindness. If each side has to assume the worst about the other's secret program, both accelerate, and both end up somewhere neither wanted. Verification attacks the uncertainty, not just the cheating — which is why it's worth the intrusion. But it cuts both ways: a regime that demands your weights to prove you're compliant is one no lab and no state will accept. That's the whole reason the field is obsessed with proving things without revealing them."*
max-chars:: 1400

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - Why Verification - PQ]]
notes:: Pre-reading question; primes the nuclear-analogy intuition the readings complicate.

## Lens:
source:: [[../Lenses/AIV - What Does It Take to Catch a Chinchilla]]
++}