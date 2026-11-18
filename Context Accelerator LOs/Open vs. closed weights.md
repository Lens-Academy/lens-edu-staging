---
id: f965e9d5-b5e6-4412-883d-919a55bc652a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what releasing a model's weights openly means, including running models on your own computer, and describe the main arguments for open release (innovation, research access, spreading power) and against it (misuse, irreversibility, removable safeguards).

## Requires
- [[Models and weights]]

## Helpful first
- [[Sources of AI catastrophe]]

## Why it matters
Decisions to release weights can't be undone, and they shape who can use, study and misuse powerful AI. Knowing the arguments on each side helps you follow and contribute to one of the most contested AI policy questions, instead of treating "open" as simply good or simply dangerous.

## Lenses

## Tests

#### Question: Choice
id:: 5c95202b-b22d-4d26-bbc5-8b815fe5f368
content:: What does it mean for an AI model to be "open-weights"?
options::
- [x] Its trained weights are published, so anyone can download and run it.
- Its training code is published, but the weights stay with the developer.
- Anyone can use it for free through a website or app.
- Its training data and code are released under a free licence.
shuffle:: true

#### Question: Choice
id:: 99a09509-2de7-44bd-93f7-c28cb2152827
content:: Someone downloads an open-weights model and runs it on their own laptop with the internet switched off. Which of these is true?
options::
- [x] The developer can't see or block what they ask it.
- The developer can still filter its answers remotely.
- The model stops working until it passes an online licence check.
- The model stores a log of each conversation for the developer.
shuffle:: true

#### Question: Choice
id:: 094acb21-d7de-4ce1-8c37-918408e00191
content:: A dangerous capability is discovered in a model after it has been released. What can the developer of a closed model, used through the developer's servers, do that the developer of an open-weights model can't?
options::
- [x] Withdraw or patch the model for every user.
- Publish a warning about the capability.
- Stop training future versions of the model.
- Report the problem to regulators.
shuffle:: true

#### Question: Choice
id:: c076d570-5ebd-4aae-847d-a5fce956c05b
content:: Developers often train their open-weights models to refuse harmful requests. What is a main reason critics say this gives limited protection?
options::
- [x] People with the weights can cheaply train the refusals away.
- Safety training makes open models too weak to be useful.
- Safety training works poorly on smaller models.
- Open-weights models are released before safety training is done.
shuffle:: true

#### Question: Choice
id:: 9d102261-7145-4079-8560-c52f3cce3432
content:: Which of these is an argument usually made in favour of releasing model weights openly?
options::
- [x] Outside researchers can study the model's internals for safety research.
- Developers can monitor how the model is being misused.
- The release can be undone if problems appear.
- Fewer groups gain access to the most capable AI.
shuffle:: true

#### Question: Choice
id:: d9b86c85-c945-4103-8136-46bae5f6bdb8
content:: In the debate over open-weights AI models, what does "marginal risk" refer to?
options::
- [x] The extra risk compared with tools people already have.
- The risk from the smallest model in a release.
- The risk left over after safety training.
- The risk to people outside the developer's country.
shuffle:: true

#### Question: Choice
id:: 50ba04ed-32c4-4c3b-8e9a-bec9917ab43c
content:: Does releasing a model's weights openly mean its training data is also made public?
options::
- [x] No
- Yes

#### Question: Choice
id:: 7094ba59-4cb6-426f-aa3e-adf97d19730e
content:: Person A worries most about terrorists using AI to help design bioweapons. Person B worries most about a few companies controlling the most powerful AI. In the open vs. closed weights debate, which position is each more likely to favour?
options::
- [x] A favours closed weights; B favours open weights.
- A favours open weights; B favours closed weights.
- Both favour closed weights.
- Both favour open weights.
shuffle:: true

#### Question: FillBlank
id:: c43cba71-7069-4b3d-8171-d675fa310c21
content:: A model whose weights are kept private, so people can only use it through the developer's app or API, is called a {{closed|closed-weights|closed-weight|proprietary}} model.

#### Question: Open
id:: bfded5e2-de2d-482c-8d73-607b47c391d3
content:: Why is releasing an AI model's weights openly often described as irreversible?
assessment-instructions:: Score out of 100. 100 for saying that once the weights are downloaded, people can keep and share copies, so the developer can't recall or delete them. 50 for only saying that anyone can download them, without explaining why that can't be taken back.

#### Question: Open
id:: 00c015e5-02c5-4b06-9979-3f4f7dc34083
content:: Give one argument that releasing AI model weights openly could reduce the risk of power becoming concentrated.
assessment-instructions:: Score out of 100. 100 for any one of: it spreads powerful AI across many people and groups instead of a few companies or governments; others can build on, check or audit the model, so no single developer controls access; users don't depend on one provider. 50 for "more people get access" without linking it to power.

#### Question: Open
id:: c820cf6d-4fb3-4523-9a5d-d2500a617b57
content:: Give one reason a person or organisation might choose to run an open-weights model on their own computers instead of using a closed model through an app.
assessment-instructions:: Score out of 100. 100 for any one of: privacy (data stays on their own machines); works without internet; lower or predictable cost; can fine-tune or customise it; no provider usage restrictions or filters; not dependent on a provider staying available or unchanged. 50 for a vague answer such as "more control" with no example.
