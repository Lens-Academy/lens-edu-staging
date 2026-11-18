---
id: 68ac2308-4550-4029-a4c6-9f63bb6c25ed
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Compare research proposals for what advanced AI should ultimately aim at, from following its operators' intentions or accepting correction to pursuing idealized human values, and explain the main risk each one leaves open.

## Requires
- [[Alignment to whom]]

## Helpful first
- [[Corrigibility]]

## Why it matters
Saying that alignment is "solved" means little until you know what the AI is aligned to. An AI that obeys its operators is only as safe as they are, while one built to pursue idealized values cannot easily be corrected if those values were specified wrongly. Knowing the options lets you judge what a safety plan is aiming for.

## Lenses

## Tests

#### Question: Choice
id:: d4267487-dfa3-461a-9c7f-37bbee4f73a4
content:: In AI alignment research, what does it mean for an AI to be "intent aligned" with its operator?
options::
- [x] It is trying to do what its operator wants it to do
- It produces outcomes that are good for humanity
- It follows the exact wording of its operator's instructions
- It pursues the values its operator would hold after long reflection
shuffle:: true

#### Question: Choice
id:: 64e68f30-ab07-4593-90f4-5f6f0d29f6ff
content:: Why do many alignment researchers prefer aligning AI to a user's intentions rather than to the literal wording of their instructions?
options::
- [x] Literal instructions often leave out things the user cares about
- Intentions are easier for an AI to observe than words
- Following intentions removes the need for human oversight
- Literal instruction-following makes AI less capable at tasks
shuffle:: true

#### Question: Choice
id:: 4442c4b6-a638-41fc-a693-f59b1fc58311
content:: An operator wants to defraud customers, and their AI helps exactly as the operator wants. By the usual definition of intent alignment, is this AI intent aligned?
options::
- [x] Yes
- No

#### Question: Choice
id:: 311cb454-c63b-42bc-972a-df861708c5b3
content:: Eliezer Yudkowsky proposed coherent extrapolated volition (CEV) as a target for advanced AI. What does CEV aim the AI at?
options::
- [x] What humanity would want if we knew more and had thought longer
- What the majority of people currently say they want
- What the AI's developers instruct it to do at each step
- What a panel of moral philosophers votes for
shuffle:: true

#### Question: Choice
id:: 929abd3e-c163-4649-a720-3acb8bac84f1
content:: "Indirect normativity" is a proposal for specifying the goals of a superintelligent AI. What does it do?
options::
- [x] Specifies a process for working out the right values, not the values themselves
- Lets the AI choose any goal, provided it accepts being shut down
- Lists a fixed set of moral rules that the AI must obey
- Trains the AI on examples of everyday human behaviour
shuffle:: true

#### Question: Choice
id:: 0ce0eaca-7f3a-4858-92c0-61b97943038b
content:: Does the indirect normativity approach to AI goals require its designers to know the correct moral theory in advance?
options::
- Yes
- [x] No

#### Question: Choice
id:: 8da0794c-a15e-4b28-9ca2-badde75b7371
content:: An AI is fully corrigible: it accepts correction and shutdown from its operators, but has no strong values of its own. What is the main risk of this alignment target?
options::
- [x] Its safety depends on the goals of whoever controls it
- It will tend to resist being retrained by its operators
- It will tend to seek power to protect its goals
- It will be much weaker at difficult tasks
shuffle:: true

#### Question: Choice
id:: d604b9ff-09ba-4608-b2e5-30de44d43197
content:: Some alignment researchers propose corrigibility (accepting correction and shutdown) as the main target for early advanced AI, rather than full human values. What is their main reason?
options::
- [x] It lets humans fix other mistakes in the AI later
- Corrigible AI would be more capable at hard research tasks
- Corrigibility would make human oversight of the AI unnecessary
- Human values are simple enough to need no learned target
shuffle:: true

#### Question: Choice
id:: bac3f1f0-b6f1-4ea7-a569-0925066b9b79
content:: Nick Bostrom sorts possible superintelligent AI designs into oracles, genies and sovereigns. What is a sovereign?
options::
- [x] An AI that acts on its own in the world to pursue broad goals
- An AI that answers questions but takes no actions itself
- An AI that carries out one command, then waits for the next
- An AI that is owned and run by a national government
shuffle:: true

#### Question: Choice
id:: 2fc94d53-5e99-49ad-9872-78e7a488b98c
content:: As of November 2026, Anthropic's constitution for its Claude models asks Claude, during the current period of AI development, to rank not undermining legitimate human oversight above its own broader ethical judgment. Which alignment target does this ranking favour?
options::
- [x] Corrigibility
- Coherent extrapolated volition
- Literal instruction-following
- Ambitious value learning
shuffle:: true

#### Question: FillBlank
id:: 787f4378-9b29-4dc1-87b4-f0898e3b12fa
content:: Eliezer Yudkowsky's proposal that AI should pursue what humanity would want "if we knew more, thought faster, were more the people we wished we were" is called coherent extrapolated {{volition}}.

#### Question: Open
id:: f2ace7a6-0372-49d4-a349-2a09faff07f3
content:: Explain the difference between aligning an AI to a person's instructions and aligning it to their intentions, and give an example where the two differ.
assessment-instructions:: Score out of 100. 50 for saying instructions are the literal request while intentions are what the person actually wants, including unstated preferences. 50 for a fitting example (e.g. "get me to the airport fast" taken literally means breaking traffic laws; "fix the failing tests" done by deleting the tests).

#### Question: Open
id:: ac81350a-670c-41f8-9aee-1464aec90b4c
content:: Give one advantage and one disadvantage of aiming advanced AI at corrigibility rather than at idealized human values.
assessment-instructions:: Score out of 100. 50 for an advantage, any one of: humans can correct mistakes, it may be simpler to specify, it doesn't require solving ethics first. 50 for a disadvantage, any one of: safety depends on the controllers' goals, it enables misuse or power concentration, the AI won't refuse harmful orders, humans may make poor corrections.

#### Question: Open
id:: af854ecf-1581-447c-9971-8335623eb031
content:: What is indirect normativity, and why might someone prefer it to writing an AI's values down directly?
assessment-instructions:: Score out of 100. 50 for describing it as giving the AI a process or criterion for working out the right values (such as what we would want after more reflection) instead of a fixed list. 50 for a reason, any one of: we may be wrong about our values, values are too complex to write down, it lets the AI find values better than our current ones.
