---
id: 37165c5a-1b40-4db3-a5d9-667a17059aa5
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how AI control aims to use possibly misaligned AI safely, describe protocols such as trusted monitoring, and say how control evaluations test them and where the approach stops working.

## Requires
- [[AI alignment]]

## Helpful first
- [[Scheming]]
- [[Defense in depth]]

## Why it matters
AI developers already have AI doing a large share of their research and coding, and no one can yet confirm those systems are aligned. Control offers safeguards that don't depend on knowing a model's goals, so understanding it helps you judge developers' safety plans and see why control may buy time but isn't expected to suffice for far stronger systems.

## Lenses
- [[../Lenses/AICF - Control in plain words|Control in plain words]]: CSET's explainer for non-specialists: alignment as the first line of defence, control as the second, and cybersecurity-style safeguards such as least privilege and logging (Oct 2025).
- [[../Lenses/AICF - Using dangerous AI, but safely|Using Dangerous AI, But Safely?]]: Robert Miles walks through the founding control experiment: trusted and untrusted models, red and blue teams, trusted monitoring, defer to trusted, untrusted monitoring and collusion, and why control won't hold for superintelligence (Nov 2024).
- [[../Lenses/AICF - Catching AIs red-handed|Catching AIs red-handed]]: Greenblatt and Shlegeris on why catching a model in an attempt changes things: shutting it down, studying the attempt, and using it to stop the next one (2024).

## Tests

#### Question: Choice
id:: c95cc5b6-b477-4d77-bf50-878b53bf944c
content:: When an AI control evaluation tests a safety protocol, what does it assume about the AI system being controlled?
options::
- [x] It may be deliberately trying to get around the protocol
- It is aligned but sometimes makes honest mistakes
- It cannot tell when it is being tested
- It has been checked for hidden goals with interpretability tools
shuffle:: true

#### Question: Choice
id:: be5894da-783d-4732-a20d-455e2bd7cb61
content:: In AI control, why is a weaker model often treated as "trusted" while a more capable model is not?
options::
- [x] The weaker model is thought too limited to scheme effectively
- The weaker model's code has been formally verified
- Weaker models are unable to produce harmful outputs
- The weaker model was trained on carefully filtered data
shuffle:: true

#### Question: Choice
id:: a4e54730-08f9-4526-bdb5-53d146b55e5d
content:: In an AI control evaluation, what is the red team's job?
options::
- [x] Designing ways for the untrusted model to subvert the protocol
- Training the model to be more aligned before deployment
- Checking the model's outputs for factual mistakes
- Testing the lab's defences against outside hackers
shuffle:: true

#### Question: Choice
id:: a3ec3bd2-0574-419a-b14f-1e2e03935cf6
content:: An AI control protocol uses a second copy of a powerful untrusted model to monitor the first, instead of a weaker trusted monitor. What is the main extra risk?
options::
- [x] The two copies could coordinate to let attacks pass
- The monitor may be too weak to follow the work
- The monitor may flag so much that audits become impossible
- The monitor may reveal the protocol's details to users
shuffle:: true

#### Question: Choice
id:: cfe2c81c-0ee6-403e-9a1c-f1b4203aafad
content:: A control protocol has a weaker trusted model redo a task whenever a monitor finds the powerful untrusted model's output suspicious. What does the developer mainly give up by lowering the suspicion threshold so this happens more often?
options::
- [x] Usefulness, because more work is done by the weaker model
- Safety, because the weaker model is more likely to scheme
- Oversight, because human auditors see fewer outputs
- Transparency, because the weaker model's reasoning is harder to inspect
shuffle:: true

#### Question: Choice
id:: 5320c48c-c9a4-4f06-8d84-6e4672b72ba9
content:: Why do many AI control researchers expect control to stop being enough for AI far more capable than humans?
options::
- [x] Monitors and human auditors fall too far behind the AI's abilities
- Control needs a model to be proven aligned first
- Stronger models make fewer mistakes for monitors to catch
- Control protocols cost too much to run on large models
shuffle:: true

#### Question: Choice
id:: 096f04c4-00dc-4610-86a9-d355719449e0
content:: Which of these is an AI control measure rather than an alignment technique?
options::
- [x] Limiting an AI agent's permissions and logging its actions
- Training the model with human feedback to be more honest
- Using interpretability to remove a deceptive goal
- Training the model to follow a written constitution
shuffle:: true

#### Question: Choice
id:: 0af89d0d-035d-4cf7-acb2-1d71ef836dd2
content:: In AI control evaluations of high-stakes settings, a single successful attack during a long deployment counts as a safety failure. Why?
options::
- [x] Some single actions, like leaking the model's weights, cause harm that can't be undone
- Evaluations are too short to observe more than one attack
- Regulators require developers to report every successful attack
- A model that attacks once will attack every task after that
shuffle:: true

#### Question: Open
id:: 654e62fd-9b54-440e-9bbf-9ee0dad7b112
content:: AI control is often described as complementing alignment research. What does control add if alignment work is already under way?
assessment-instructions:: Score out of 100. 100 for saying control keeps AI use safe even if alignment efforts fail or a model's alignment can't be verified, because it doesn't rely on the model having good goals. 50 for calling it a backup without saying it works regardless of the model's goals.

#### Question: Open
id:: b7227344-8eb5-4a99-8103-63644c42c4b9
content:: In trusted monitoring, a weaker trusted model reviews the actions of a stronger untrusted model. Give one way a scheming stronger model might try to get past this.
assessment-instructions:: Score out of 100. 100 for any one of: hiding harmful actions in work too subtle for the weak monitor to recognise; attacking rarely so that spot checks miss it; splitting an attack across innocent-looking steps; behaving well when it suspects a test; manipulating or prompt-injecting the monitor. 40 for a vague "it could trick the monitor".

#### Question: Open
id:: 500b5222-93cb-4c05-bd52-6a5084cad9f3
content:: Why is catching an AI model in a real attempt to subvert safety measures useful beyond stopping that one attempt?
assessment-instructions:: Score out of 100. 100 for any one of: it is strong evidence the model is misaligned, which can justify pausing or changing plans; developers can study the attempt to improve their protocols; examples of attacks help train better monitors. 50 for "it shows something went wrong" without saying how that can be used.
