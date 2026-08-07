---
id: 'bfee82b6-8588-4467-b262-289dbde09149'
learning-outcome: State the disagreement between two rival accounts of what makes alignment hard, one holding that alignment fails to generalize as capabilities generalize, the other that the target was never a well-defined thing to point at; identify what observation would distinguish them; and determine which account a given proposed solution implicitly assumes.
domain: none
stage: advanced
---
## Test:
id:: 7ceb8922-bad8-400e-a152-fbafc10e26d0
#### Question
content::
A lab announces a result. They trained a model on a large set of human judgments about which of two outcomes is better. On held-out judgments from the same population, the model predicts human preferences with 99.4% accuracy, well above the rate at which two humans agree with each other. The team writes:

> The remaining gap to full alignment is an engineering problem. We have a reliable specification of human values, verified against held-out data. What remains is scaling the optimizer that pursues it.

Two researchers reject this conclusion, for different reasons, and they also disagree with each other.

Researcher A says the result is real but tells you almost nothing about the situation you care about.
Researcher B says the quantity they measured to 99.4% accuracy is not the quantity they think it is.

Reconstruct both objections. Then state precisely where A and B disagree with each other, not just where each disagrees with the lab. Finally, describe an experiment or observation whose result would count as evidence for one of these two views over the other, and say what each would predict.

max-time:: 25:00
assessment-instructions:: The student has read Soares on the sharp left turn and Wentworth on the pointers problem. This test never names either author or either paper, and the scenario is not from either text. The student must recognize the two positions from their structure and, critically, must separate them from each other rather than merging them into a single "alignment is hard" blur.

The merge is the dominant failure mode. Both objections sound like "your metric does not mean what you think", so students collapse them. They are different claims:

- A (distributional / dynamic): the target may be perfectly well-defined, and the model may really have learned it, but it was learned on a distribution. When capabilities generalize to regimes far outside training, which is exactly the regime that matters, the learned alignment does not come along. Held-out data from the same population is still in-distribution, so 99.4% is measured in precisely the regime where nobody was worried. The problem is that alignment and capability generalize at different rates.
- B (specification / semantic): there is no well-defined target to have learned. Human judgments are a function of latent variables inside human world-models, things like whether a person is really happy rather than appearing so. Those latents may not correspond to anything in the world, and outside the human's own model they may not be defined at all. So the model has learned to predict human judgments, which is a different object from human values, and the two come apart exactly where the human's model is wrong.

Where they disagree with each other, which is the load-bearing part of the question:
- On whether the target exists. B says the thing being pointed at is not well-defined. A generally grants that there is a coherent thing we want and says the difficulty is keeping the system pointed at it through a capability jump.
- On what would count as a solution. Under A, a solution looks like maintaining or restoring alignment across a distributional leap; robustness and corrigibility through the transition. Under B, that would not help, because you would be robustly preserving a pointer that does not resolve. B needs a prior account of what the pointer refers to.
- On where the failure happens. A locates it in a transition, at a time. B locates it in the specification, present from the start and simply not yet visible.
- Consequently on whether more capable models help. Under B, a sufficiently capable model that models humans very well could in principle resolve the reference, so capability partly helps. Under A, capability is what triggers the failure.

For the discriminating observation, accept any proposal that is genuinely differential. Good instances: take a system whose behavior is excellent in-distribution, move it to a genuinely novel regime, and ask whether the failures look like a coherent goal pursued into new territory in ways we did not want (favors A) or like the target itself becoming ambiguous, with the system's behavior depending on how the ambiguity is resolved rather than degrading in a consistent direction (favors B). Or: examine cases where humans are factually wrong about the latents their values rest on, someone who wants a friend to be happy while being deceived about it, and see whether the model tracks the human's judgment or the underlying state; B predicts these come apart and predicts trouble at exactly those points even with no distributional shift at all, which is the sharpest test since it isolates B's mechanism from A's.

A student may argue the two are compatible or that one subsumes the other. That can be a 4 or 5 answer if they first state both crisply and then argue the relation, with the differential prediction still identified. It is a 2 if used to avoid distinguishing them.

Grade reasoning, not agreement. A student who thinks the lab is substantially right, and defends that against both objections while stating both accurately, passes.

**1**: Restates that alignment is hard, or objects on grounds unrelated to either position, such as the model being a black box or the data being biased. Does not produce two distinct objections. *Example: "The problem is that the model is a neural network, so we cannot verify what it actually learned. 99.4% accuracy could hide anything, and the training data probably reflects the biases of whoever was asked. You cannot trust a number like that without interpretability tools that let you see inside."*

**2**: Produces two objections but they are the same objection in different words, typically both being generic proxy-gaming. No account of where A and B differ from each other. *Example: "Researcher A would say the metric is a proxy and optimizing hard against a proxy breaks it, since Goodhart's law applies whenever you optimize a measure. Researcher B would say the same thing about human values, that predicting what humans say they prefer is not the same as what is actually good for them. Both of them are pointing out that 99.4% on a proxy does not mean 99.4% aligned."*

**3**: PASS. Reconstructs both positions accurately and distinctly, and names at least one real point of disagreement between them, most commonly whether a well-defined target exists. *Example: "A's objection is about where the number was measured. Held-out judgments from the same population are still the training distribution. The worry was never about a model operating in familiar conditions; it was about what happens when the system becomes capable enough to act in regimes nothing in training resembled. Capability transfers to those regimes, and A's claim is that the alignment does not transfer with it, so a number collected in-distribution does not speak to the case of concern. B's objection is different and does not depend on any distribution shift. Human judgments are about things like whether someone is actually happy, not about whether they appear happy, and those things are variables inside a human's model of the world that may not pick out anything definite outside it. So what the lab measured is accuracy at predicting human judgments, and human values are not that object. They disagree with each other about whether there is a coherent target at all. A can accept that there is something real we want and say the problem is keeping the system aimed at it through a capability jump. B is saying that aim is not defined well enough to be kept."*

**4**: As above, plus derives that the two accounts imply different solution shapes, and can classify a proposed technique by which account it assumes. *Example: Adds "This changes what counts as progress. Work on preserving properties through distributional shift, corrigibility that survives a capability jump, detecting when a system has left the regime its training vouched for, all of that is aimed at A's problem and takes for granted that there is a target worth preserving the aim at. B would call that stabilizing a pointer that does not resolve. The work B's picture demands is prior: say what the pointer refers to, which means finding whether the latent variables in a human's model correspond to anything in the world. The lab's own framing, that what remains is scaling the optimizer, assumes A's world and assumes A's problem is already solved. It has no answer to B at all, since under B a stronger optimizer pursues a target that was never pinned down and pursues it harder."*

**5**: As above, plus proposes a genuinely differential observation with predictions from each side, and identifies what makes the test sharp, ideally isolating one mechanism from the other. *Example: Adds "A test that separates them has to hold one mechanism fixed. Take cases with no distributional shift at all, where a human is simply factually wrong about the thing their judgment rests on: they prefer a state where a friend is happy, and are mistaken about whether the friend is. B predicts a systematic split here, because the model was trained on the judgment and the judgment tracks the human's belief about the latent rather than the latent. A predicts nothing in particular, since we have not left the training regime, so any error should look like ordinary noise rather than a consistent direction. If the split appears with the distribution held fixed, that is evidence for B specifically, because A's mechanism was not given the chance to operate. Run it the other way for A: hold the human's model accurate and vary the regime instead. A predicts a coherent goal pursued competently into territory we did not intend. B predicts something different in texture, behavior that depends on how an ambiguity gets resolved rather than failing in a consistent direction. The reason this is worth doing rather than arguing is that the two views recommend spending the field's next decade on different problems, and one of them is a detour."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/U3 - What Makes This Hard - PQ]]
notes:: Pre-test. Fires before either reading, so the post-test measures movement.

## Lens:
source:: [[../Lenses/U3 - Two Accounts of the Core Difficulty]]
