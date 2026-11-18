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
Developers may hand AI systems important work before anyone can confirm those systems are aligned. Control offers safeguards that don't depend on knowing a model's goals, so understanding it helps you judge developers' safety plans and see why control can buy time but isn't expected to replace alignment for far stronger systems.

## Lenses

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
id:: 4f3c2b9c-795f-41c2-81a8-29eeabf14bf5
content:: In the "defer to trusted" AI control protocol, a monitor rates an output from the powerful untrusted model as suspicious. What happens next?
options::
- [x] A weaker trusted model writes the output instead
- The untrusted model is retrained right away
- The output goes to users with a warning attached
- The untrusted model is shut down for good
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
id:: 7985eb49-7205-4fdf-b52b-9f8af26fe308
content:: Is AI control mainly a method for changing what an AI model wants?
options::
- [x] No
- Yes

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
id:: 3aefe0de-b495-4333-b726-9565a82cb387
content:: In AI control research on high-stakes failures, is a protocol judged unsafe if a misaligned model succeeds at a single serious attack during a long deployment?
options::
- [x] Yes
- No

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
