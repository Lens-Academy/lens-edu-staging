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
- [[../Lenses/AI Safety Atlas - Strategies - Misuse Prevention Strategies|Misuse Prevention Strategies]]: the spectrum from closed to fully open release, what an API lets a developer do (filter, monitor, patch, revoke), and why openness both spreads and concentrates power; read "External Access Controls" and open the callouts "Ensuring a positive offense-defense balance" (the main arguments for and against openness) and "The impossible challenge of creating tamper-resistant safeguards" (2026).
- [Open Source AI is the Path Forward (Meta)](https://about.fb.com/news/2024/07/open-source-ai-is-the-path-forward/): Mark Zuckerberg's case for open weights, from innovation, cost and running models on your own servers to spreading power and safety through scrutiny; the open side in its leading proponent's words, though Meta has since said it will be more careful about what it opens (July 2024).
- [On the Societal Impact of Open Foundation Models (AI Snake Oil)](https://www.normaltech.ai/p/on-the-societal-impact-of-open-foundation): Kapoor and Narayanan on what open weights make possible and why the question to ask is "marginal risk", the extra risk over closed models and tools people already have; written before newer models raised biorisk concerns (February 2024).
- [Managing risks from increasingly capable open-weight AI systems (UK AI Security Institute)](https://www.aisi.gov.uk/work/managing-risks-from-increasingly-capable-open-weight-ai-systems): why open releases can't be rolled back and safeguards can be cheaply removed, and which mitigations, such as filtering training data and full-access audits, still help (August 2025).
- [[../Lenses/seger-open-sourcing-highly-capable-foundation-models-an-evaluation-of-risks-benefits-and-alternative-methods-for-pursuing-open-source-objectives|Open-Sourcing Highly Capable Foundation Models]] (Noah's CG list)

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
content:: Someone downloads an open-weights model and runs it on their own laptop. Which of these is true?
options::
- [x] The developer can't see or block what they ask it.
- The developer can still filter its answers remotely.
- The developer can switch the model off if it is misused.
- Their conversations are logged on the developer's servers.
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
id:: f27e5afa-bad2-444a-97e5-5fe48b508fbb
content:: In 2026, the most capable open-weights models trailed the most capable closed models by about four months on average. What does this mean for the open vs. closed debate?
options::
- [x] Capabilities first seen in closed models may soon be in models anyone can run and modify.
- Closed developers can count on staying years ahead of anything released openly.
- Open-weights models are too far behind the frontier to matter for misuse.
- Only closed models now need safety testing before they are released.
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
- [x] Outside researchers can study the model's internals.
- Developers can monitor how the model is being misused.
- Safety fixes can be pushed to every user at once.
- Fewer groups gain access to the most capable AI.
shuffle:: true

#### Question: Choice
id:: d62d9b1a-a00c-4842-888e-69eb73972198
content:: A critic warns that an open-weights model can help people carry out cyberattacks. A supporter of open release replies that the same help is already easy to find online. Which finding would most weaken the supporter's reply?
options::
- [x] Tests show the model gives real help beyond what online searches give.
- Closed models can give the same help when asked in the right way.
- The model learned most of what it knows from public web pages.
- The model sometimes gives wrong answers about cyberattacks.
shuffle:: true

#### Question: Choice
id:: 7094ba59-4cb6-426f-aa3e-adf97d19730e
content:: Person A worries most about terrorists using AI to help design bioweapons. Person B worries most about a few companies controlling the most powerful AI. In the open vs. closed weights debate, which position is each more likely to favour?
options::
- [x] A favours closed weights; B favours open weights.
- A favours open weights; B favours closed weights.
- Both favour closed weights.
- Both favour open weights.
shuffle:: true

#### Question: Choice
id:: 200d12fa-670f-42a9-834e-59156613ffb4
content:: Which view is shared by many people on both sides of the open vs. closed weights debate, including some leading open-weights developers?
options::
- [x] Whether to release a model openly should depend on how dangerous its capabilities are.
- Any model can be released openly once its developer has finished safety training.
- A model is safe to release openly once it is a few months behind the frontier.
- Open release makes little difference, because closed models' weights usually leak.
shuffle:: true

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
