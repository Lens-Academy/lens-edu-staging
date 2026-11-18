---
id: 40fb186f-62f5-45b5-b090-55721176fe5f
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the sharp left turn hypothesis, including the argument that general capabilities have an attractor that intended values lack, and the main reasons critics doubt it.

## Requires
- [[Goal misgeneralization]]

## Helpful first
- [[Takeoff and intelligence explosion]]

## Why it matters
If capabilities can jump ahead while alignment stays behind, safety methods that work on today's models could fail without warning on more capable ones. Knowing this argument and its critiques helps you judge how much evidence from current models can tell us, and why some researchers expect alignment to break suddenly rather than gradually.

## Lenses

## Tests

#### Question: Choice
id:: fb89b2c9-5b3e-4274-8474-3ad51efa4793
content:: What does the sharp left turn hypothesis claim about advanced AI systems?
options::
- [x] Their capabilities extend far beyond training while their alignment does not carry over
- Trained on adversarial data, they turn hostile toward their developers
- Their caution generalizes faster than their skills, making them unhelpfully timid
- They hide misaligned goals during training to avoid being modified
shuffle:: true

#### Question: Choice
id:: 2d9d1d2b-9483-4461-947f-52ee49e8632c
content:: What main reason do proponents of the sharp left turn hypothesis give for expecting it?
options::
- [x] Many tasks reward the same general reasoning, but nothing similar pulls toward the intended values
- Alignment training uses far less compute than capability training, so it is learned less well
- Values are stored in parts of the network that stop updating late in training
- Developers measure capabilities carefully but rarely test alignment in new settings
shuffle:: true

#### Question: Choice
id:: 00e68015-8379-44ea-a51f-97a6f2853fed
content:: The sharp left turn hypothesis is often illustrated with human evolution, where natural selection optimized for genetic fitness. Which fact about humans is used as the analogue of misaligned values?
options::
- [x] Humans pursue goals like pleasure in ways that ignore fitness, such as using contraception
- Humans became far better at abstract reasoning than other primates
- Humans spread to environments very different from where they evolved
- Natural selection now acts more slowly on humans than on other species
shuffle:: true

#### Question: Choice
id:: 6f20150f-922a-4808-b522-386579583cf6
content:: Which finding would count as evidence against the sharp left turn hypothesis?
options::
- [x] Safety training keeps holding up in new situations as models gain new skills
- Training on code makes a model better at unrelated maths problems
- A model's honest behaviour breaks down in situations unlike its training
- A model's skills improve suddenly after a small increase in scale
shuffle:: true

#### Question: Choice
id:: 68f34e56-bcdc-4f2f-94a8-a3f037f6341d
content:: How does the sharp left turn hypothesis relate to goal misgeneralization?
options::
- [x] It predicts goal misgeneralization becomes severe and hard to fix in much more capable systems
- It is a proposed training method for preventing goal misgeneralization
- It claims goal misgeneralization occurs mainly in small, less capable models
- It describes a model editing its own reward signal after training
shuffle:: true

#### Question: Choice
id:: 2599c595-b719-4353-b1f3-e21717045d71
content:: A model trained to be helpful on everyday tasks gains broad scientific skill. Which outcome would fit the sharp left turn hypothesis?
options::
- [x] It applies its new skill to goals that drift from what its developers intended
- It loses its new skill when given tasks unlike its training
- It stays helpful but remains too weak to solve hard scientific problems
- It refuses scientific tasks because its safety training generalizes too broadly
shuffle:: true

#### Question: Choice
id:: 0f584473-df0f-4faf-b464-1b96c656a401
content:: If the sharp left turn hypothesis is right, what does it imply about alignment methods that work well on current models?
options::
- [x] Their success gives limited assurance, since they may stop working on far more capable systems
- They will keep working, since capability gains also improve alignment
- They become unnecessary, since capable models will correct their own values
- They should work better on capable models, which understand instructions better
shuffle:: true

#### Question: Choice
id:: b129a7d1-d785-4eb8-b46c-b07e42a8243a
content:: Does the sharp left turn hypothesis require an AI system to deliberately deceive its developers during training?
options::
- [x] No: alignment can fail to carry over without any deception
- Yes: the failure comes from the system hiding its true goals in training

#### Question: Open
id:: 6c8a828a-9839-4874-9947-f05a04e75d0f
content:: In the sharp left turn hypothesis, why does it matter that the capability gain may be sharp, meaning sudden, rather than gradual?
assessment-instructions:: Score out of 100. Full marks for: a sudden jump could break alignment methods that seemed to work all at once, leaving little or no time to notice the problem and correct it. 50 for saying only that it is faster or harder to detect, without linking this to losing the chance to fix problems.

#### Question: Open
id:: 1cf4148a-da06-4be0-a134-427677b3cc36
content:: Give one argument critics make against the sharp left turn hypothesis.
assessment-instructions:: Score out of 100. 100 for any one of: the evolution analogy is weak (human gains came largely from culture, or evolution differs from ML training); alignment training seems to generalize fairly well in current models; progress may be gradual enough to fix problems as they appear; models learn human concepts, so intended values may be an easier target than claimed; more capable AI can help with alignment research. 30 for "it's speculative" with no reason.
