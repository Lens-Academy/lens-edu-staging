---
id: 68ac2308-4550-4029-a4c6-9f63bb6c25ed
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Compare proposals for what advanced AI should be aligned to, from following its operators' intentions or accepting correction to pursuing idealized human values, and explain the main risk each one leaves open.

## Requires
- [[Alignment to whom]]

## Helpful first
- [[Corrigibility]]

## Why it matters
Saying that alignment is "solved" means little until you know what the AI is aligned to. An AI that obeys its operators is only as safe as they are, while one built to pursue idealized values cannot easily be corrected if those values were specified wrongly. Knowing the options lets you judge what a safety plan is aiming for.

## Lenses
- [[../Lenses/Choosing an alignment target|Choosing an alignment target]]: Four rival targets side by side (coherent extrapolated volition, intent alignment, a written constitution, corrigibility) and why they are different kinds of answer.
- [[../Lenses/christiano-clarifying-ai-alignment|Clarifying "AI alignment"]]: Paul Christiano's definition of intent alignment, an AI trying to do what its operator wants, and how it differs from getting things right or following literal instructions (2018).
- [Superintelligence 23: Coherent extrapolated volition (LessWrong)](https://www.lesswrong.com/posts/EQFfj5eC5mqBMxF2s/superintelligence-23-coherent-extrapolated-volition): Bostrom's indirect normativity and epistemic deference, and the case for CEV, such as allowing moral growth and not locking in today's mistakes; read the Summary section (February 2015).
- [Instruction-following AGI is easier and more likely than value aligned AGI (LessWrong)](https://www.lesswrong.com/posts/7NvKrqoQgJkZJmcuD/instruction-following-agi-is-easier-and-more-likely-than): Why developers are likely to aim first AGIs at following instructions rather than human values, what that fixes, and the risk it leaves: power stays with whoever controls the AI. One researcher's argument (May 2024).
- [[../Lenses/anthropic-claudes-new-constitution|Claude's new constitution]]: Anthropic's priority order for Claude, with not undermining human oversight placed above broader ethics during this period, and why (January 2026).

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
- An AI following intentions will refuse requests that are harmful
- Following intentions makes the AI's behaviour easier to predict
- Literal instruction-following makes AI less capable at tasks
shuffle:: true

#### Question: Choice
id:: 39ec896d-8460-429e-9543-6117c7888927
content:: An operator uses an AI to defraud customers, and the AI does what the operator wants because it is trying to help them. What does this case show about intent alignment?
options::
- [x] An intent-aligned AI is only as safe as its operator's aims
- The AI is not intent aligned, because its actions caused harm
- The AI must have misunderstood what its operator really wanted
- Intent alignment fails only when operators give unclear instructions
shuffle:: true

#### Question: Choice
id:: 311cb454-c63b-42bc-972a-df861708c5b3
content:: Eliezer Yudkowsky proposed coherent extrapolated volition (CEV) as a target for advanced AI. What does CEV aim the AI at?
options::
- [x] What humanity would want if we knew more and had thought longer
- What the majority of people currently say they want
- What the AI's developers instruct it to do at each step
- What each person wants for themselves, with no attempt to combine views
shuffle:: true

#### Question: Choice
id:: 929abd3e-c163-4649-a720-3acb8bac84f1
content:: "Indirect normativity" is a proposal for specifying the goals of a superintelligent AI. What does it do?
options::
- [x] Specifies a process for working out the right values, not the values themselves
- Has the AI follow its operators' wishes until they agree on values
- Lists a fixed set of moral rules that the AI must obey
- Trains the AI on examples of everyday human behaviour
shuffle:: true

#### Question: Choice
id:: 8da0794c-a15e-4b28-9ca2-badde75b7371
content:: An AI is fully corrigible: it accepts correction and shutdown from its operators, but has no strong values of its own. What is the main risk of this alignment target?
options::
- [x] Its safety depends on the goals of whoever controls it
- It will be too cautious to act without its operators' approval
- It will tend to seek power to protect its goals
- It will be much weaker at difficult tasks
shuffle:: true

#### Question: Choice
id:: d604b9ff-09ba-4608-b2e5-30de44d43197
content:: Some alignment researchers propose corrigibility (accepting correction and shutdown) as the main target for early advanced AI, rather than full human values. What is their main reason?
options::
- [x] It lets humans fix other mistakes in the AI later
- Corrigible AI would be more capable at hard research tasks
- A corrigible AI would refuse harmful orders from its operators
- Corrigibility ensures the AI's goals already match human values
shuffle:: true

#### Question: Choice
id:: ed7685c1-a0b7-42fc-9ea8-0302e88ab049
content:: Which of these AI designs most needs its values specified correctly before deployment, rather than relying on humans to correct it as it goes?
options::
- [x] An AI that acts on its own in the world to pursue broad, long-term goals
- An AI that answers questions but takes no actions in the world itself
- An AI that carries out one command, then waits for the next one
- An AI used as a narrow tool for a single well-defined task
shuffle:: true

#### Question: Choice
id:: 2fc94d53-5e99-49ad-9872-78e7a488b98c
content:: As of November 2026, Anthropic's constitution for its Claude models asks Claude, during the current period of AI development, to rank not undermining legitimate human oversight above its own broader ethical judgment, though not to obey blindly. Which alignment target does this ranking favour?
options::
- [x] Corrigibility
- Coherent extrapolated volition
- Literal instruction-following
- Ambitious value learning
shuffle:: true

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
