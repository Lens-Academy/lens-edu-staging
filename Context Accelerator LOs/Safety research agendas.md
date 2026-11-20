---
id: a384150b-0ffb-4409-aaf2-818da62d5577
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Name the main technical AI safety agendas, such as alignment training, scalable oversight, interpretability, evaluations and AI control, and say which problem each one tries to solve.

## Requires

## Helpful first
- [[Sources of AI catastrophe]]
- [[AI alignment]]

## Why it matters
Safety work splits into agendas aimed at different problems: making models want the right things, checking what they want and can do, or staying safe if they want the wrong things. Knowing which problem each agenda targets helps you judge research directions, spot gaps and see why labs combine several.

## Lenses
- [[../Lenses/Risks from power-seeking AI|Risks from power-seeking AI]]: read only the "Technical safety approaches" section, a one-page map of safe-goal training, scalable oversight, evaluations and interpretability, monitoring and control, and model organisms, each with the problem it targets (2026).
- [Recommendations for technical AI safety research directions (Anthropic Alignment Science)](https://alignment.anthropic.com/2025/recommended-directions): Anthropic's tour of capability and alignment evaluations, interpretability and chain-of-thought faithfulness, AI control with trusted monitors, scalable oversight and weak-to-strong generalization, robustness and unlearning, with why each matters (January 2025).
- [[../video_transcripts/rational-animations-ai-sleeper-agents-how-anthropic-trains-and-catches-them|AI Sleeper Agents]]: how researchers build deliberately misaligned "model organisms", find that safety training doesn't remove the hidden behaviour, and catch it with simple probes on the model's internals.
- [[../Lenses/AF not really math not really science|Agent Foundations: not really math, not really science]]: an agent foundations researcher on why the agenda studies agency with mathematics rather than experiments on current models (August 2025).

## Tests

#### Question: Choice
id:: 6834c513-c391-43a5-8e44-930226b869ef
content:: Before release, a lab tests whether its new model can give meaningful help to someone trying to make a biological weapon. Which safety agenda does this belong to?
options::
- [x] Dangerous capability evaluations
- Alignment evaluations
- AI control
- Scalable oversight
shuffle:: true

#### Question: Choice
id:: 55602b5d-4907-4177-9a2b-06037548b7ba
content:: A lab can't verify that its model is aligned, so a weaker, trusted model reviews the strong model's actions and flags suspicious ones for humans. Which agenda is this?
options::
- [x] AI control
- Scalable oversight
- Mechanistic interpretability
- Alignment pretraining
shuffle:: true

#### Question: Choice
id:: d31e50a2-1b4e-4e47-bfcf-910cae8fb219
content:: Which problem does the scalable oversight agenda try to solve?
options::
- [x] Humans can't reliably judge AI work on tasks beyond their expertise
- A model might hide misaligned goals whenever it is being tested
- A misaligned model might sabotage work while deployed in a lab
- People might use a capable model to help build weapons
shuffle:: true

#### Question: Choice
id:: 29579f16-e62b-4012-867a-43b08c40eecf
content:: Researchers test whether a strong model fine-tuned on labels from a weaker model can end up more accurate than that weak supervisor. What real problem is this setup meant to stand in for?
options::
- [x] Humans having to train AI systems that are more capable than they are
- Labs compressing large models into smaller ones that are cheaper to run
- Attackers using small open models to jailbreak larger frontier models
- Small models being too weak to learn well from very large datasets
shuffle:: true

#### Question: Choice
id:: 0b52f30e-e9c6-4392-ac98-d47400de14a2
content:: Researchers train a simple classifier on a model's internal activations to detect when the model is lying. Which agenda is this?
options::
- [x] Interpretability
- Chain-of-thought monitoring
- Behavioral evaluations
- Red-teaming
shuffle:: true

#### Question: Choice
id:: 6310d320-d358-4010-8038-7a6ac520d29b
content:: Researchers deliberately train a model with a hidden harmful behavior, then test whether standard safety training removes it. What is this kind of research called?
options::
- [x] Model organisms of misalignment
- Capability elicitation
- Adversarial training
- Agent foundations
shuffle:: true

#### Question: Choice
id:: 63513c68-0c76-4879-8ba8-a071706080c1
content:: Agent foundations researchers mostly work on the mathematical theory of agency rather than on experiments with current AI models. What is their main reason?
options::
- [x] They doubt results on today's models will hold for far smarter ones
- They think today's models are too dangerous to run experiments on
- They think today's models are already aligned well enough
- They think theory results are faster to publish than experiments
shuffle:: true

#### Question: Choice
id:: c9475770-e686-49b7-b529-a8a778008c8b
content:: Does the AI control agenda aim to make a model want what its developers intend?
options::
- [x] No, it aims to stay safe even if the model's goals are wrong
- Yes, it trains the model to share its developers' goals

#### Question: Choice
id:: 7a17eae8-3a30-4f31-a60c-21604836f420
content:: Why do many safety researchers want interpretability as well as behavioral evaluations, rather than relying on evaluations alone?
options::
- [x] A model could behave well on tests while having other goals
- Behavioral evaluations can be run only after deployment
- Behavioral evaluations need access to model weights to work
- Behavioral tests can't detect dangerous capabilities
shuffle:: true

#### Question: Choice
id:: 251d79ba-f0ad-45ce-9b62-80322fb4d257
content:: Alignment training methods such as RLHF and constitutional AI reward outputs that graders judge to be good. What is a main worry about relying on them for much more capable models?
options::
- [x] Models may learn to look good to graders rather than be good
- Models trained this way lose most of their capabilities
- These methods can be applied only during pretraining
- Graders' judgments can't be turned into a training signal
shuffle:: true

#### Question: Choice
id:: a9ba1f16-1cb1-4b8f-90f3-659d3e9e150a
content:: Which of these safety approaches mainly targets misuse, where people direct an AI toward harmful goals, rather than an AI pursuing unintended goals of its own?
options::
- [x] Unlearning hazardous knowledge from the model
- Scalable oversight of the model's outputs
- Interpretability probes for deception
- Model organisms of scheming
shuffle:: true

#### Question: FillBlank
id:: 1169c468-69f4-451d-8a79-ae95646aea05
content:: Research that tries to reverse-engineer a neural network's computations into human-understandable features and circuits is called {{mechanistic interpretability|mech interp}}.

#### Question: Open
id:: 4a7198d8-6782-4f1c-828b-bce1aa4e03fa
content:: Name two technical AI safety agendas and, for each, the problem it tries to solve.
assessment-instructions:: Score out of 100. 50 per agenda correctly paired with its problem, e.g. interpretability: understanding model internals to detect misalignment; evaluations: testing for dangerous capabilities or behavior; scalable oversight: supervising AI on tasks humans can't judge; AI control: staying safe if the model is misaligned; alignment training: shaping behavior; agent foundations: theory of agency. 25 for a correct name with a vague problem.

#### Question: Open
id:: 82f3fcd5-ac44-449f-ac3b-b37c6646e92f
content:: Technical safety agendas differ in whether they try to prevent misalignment, or to detect it or limit its harm. Name one agenda of each kind.
assessment-instructions:: Score out of 100. 50 for a preventing agenda (alignment training such as RLHF or constitutional AI, alignment pretraining, scalable oversight, agent foundations). 50 for a detecting or harm-limiting agenda (interpretability, evaluations, red-teaming, chain-of-thought monitoring, AI control). Accept other placements if a correct reason is given.
