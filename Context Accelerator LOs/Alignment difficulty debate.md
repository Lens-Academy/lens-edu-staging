---
id: e9fd7b7f-9385-424d-b2f3-b94c2bf10afd
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main positions on how hard aligning advanced AI will be, from fairly easy through hard but solvable to extremely hard, and the arguments and evidence each side uses, including how each reads current models' behavior.

## Requires
- [[Alignment difficulty arguments]]

## Helpful first
- [[Aligned behavior so far]]
- [[Misalignment in current models]]

## Why it matters
Two people can agree that AI will soon be very capable and still give very different risk estimates, mostly because they disagree about how hard alignment is. Knowing the main positions, and what each counts as evidence, lets you find where an argument really disagrees and judge which new results should change your view.

## Lenses
- [[../Lenses/Forecasting risk and choosing an approach|Forecasting risk and choosing an approach]]: the spread of views, from optimistic to pessimistic.
- [[../Lenses/optimism-ai-is-easy-to-control|AI is easy to control]]: Belrose and Pope's case for the easy end.
- [[../Lenses/AFSRA - AGI Ruin, A List of Lethalities|AGI Ruin: A List of Lethalities]]: Yudkowsky's case for the very hard end.
- [Alignment remains a hard, unsolved problem](https://www.lesswrong.com/posts/epjuxGnSPof3GnMSL/alignment-remains-a-hard-unsolved-problem): Evan Hubinger's intermediate view (November 2025).
- [Ten levels of AI alignment difficulty](https://www.lesswrong.com/posts/EjgfreeibTXRx9Ham/ten-levels-of-ai-alignment-difficulty): a scale of what each difficulty level would require.

## Tests

#### Question: Choice
id:: 5572092c-51cf-494f-adfb-0c291165bd1f
content:: In Anthropic's 2023 "Core Views on AI Safety", which describes the intermediate scenario for alignment difficulty?
options::
- [x] Preventing catastrophe is possible but needs major scientific and engineering effort
- Current techniques such as RLHF are roughly sufficient on their own
- Aligning advanced AI is likely beyond reach, so safety is unsolvable
- Misalignment is a minor risk, so the main work is preventing misuse
shuffle:: true

#### Question: Choice
id:: a1a3c111-86b2-41fa-a03c-b48069dfcfb9
content:: Chris Olah's informal scale of alignment difficulty runs from "steam engine" through "Apollo" to "P vs NP". What does the Apollo level stand for?
options::
- [x] A huge but achievable scientific and engineering project
- A problem that existing engineering methods already handle
- A problem needing breakthroughs that may never come
- A problem solved mainly by one lucky insight
shuffle:: true

#### Question: Choice
id:: 512b0239-777a-4a3c-b44a-e5b818b8ef19
content:: Nora Belrose and Quintin Pope argue that AI is easy to control partly because neural networks are "white boxes". What do they mean?
options::
- [x] Developers can read and change every weight and activation
- Models explain their own reasoning in plain language
- Models' training data is open to public inspection
- Models follow decision rules that programmers wrote by hand
shuffle:: true

#### Question: Choice
id:: 98b28195-08f8-4f8f-b1b0-8625b54a6db0
content:: Which of these findings is evidence for the view that alignment is harder than it looks?
options::
- [x] Backdoor behavior trained into a model survived later safety training
- Models trained with RLHF refuse most clearly harmful requests
- Models trained on internet text describe human moral norms accurately
- Models given a written constitution follow its rules in most tests
shuffle:: true

#### Question: Choice
id:: f493f8c0-b104-419b-b937-9097dbc37e06
content:: Why do researchers who think alignment is very hard give little weight to today's models mostly behaving well?
options::
- [x] Weaker systems' good behavior may not carry over to systems able to deceive
- Behavioral tests of current models are mostly run by the labs that built them
- Today's models are trained with methods that labs plan to abandon soon
- Current models are too small to learn human values from their training data
shuffle:: true

#### Question: Choice
id:: f69396de-104d-408c-82f4-91c6d7dd29bc
content:: People at the very hard end of the alignment debate argue that alignment must work on the first critical try. Does this argument depend on current models already being misaligned?
options::
- [x] No
- Yes

#### Question: Choice
id:: 1b88b35c-ede8-4001-bc49-579a4faef7ef
content:: In its 2023 "Core Views on AI Safety", what does Anthropic say its role would be if the pessimistic scenario, where alignment is essentially unsolvable, turned out to be true?
options::
- [x] Gather evidence that safety techniques fail and warn the world's institutions
- Release models early so that safety problems surface sooner
- Focus on misuse, since misalignment would be beyond anyone's control
- Build the most capable model first so it sets the safety standard
shuffle:: true

#### Question: Choice
id:: 91184476-5976-4257-85de-1b286ec2dac8
content:: Among researchers who agree AI will soon surpass humans at most tasks, which question most divides those who expect alignment to be easy from those who expect it to be very hard?
options::
- [x] Whether training on behavior gives superhuman systems the goals we intended
- Whether AI labs should publish their safety research openly
- Whether AI systems will need more compute than exists today
- Whether governments will regulate AI within the next decade
shuffle:: true

#### Question: Choice
id:: 2f20cbd0-d3f2-4cd3-9913-1749b323816a
content:: A researcher thinks aligning advanced AI is technically fairly easy, yet still worries about AI catastrophe. Which reason fits that combination of views?
options::
- [x] Developers racing each other may skip safety work even when it is cheap
- Easy alignment would make AI systems more likely to seek power
- Easy alignment would make models refuse to help with safety research
- Easy alignment would slow AI progress far below current forecasts
shuffle:: true

#### Question: Choice
id:: 1930745f-8b64-4378-bb64-da112540fefd
content:: Researchers with an intermediate view treat the reward hacking and alignment faking seen in current models as warnings, not signs of a hopeless problem. What is their main reason?
options::
- [x] These failures were fairly easy to detect, so they can be studied and fixed
- These failures appeared only in models too small to be dangerous
- These failures were caused by mistakes in human-written training labels
- These failures went away by themselves as models were scaled up
shuffle:: true

#### Question: FillBlank
id:: 3a50d7aa-96cd-4a85-8042-bf77eb650452
content:: The argument that an AI's capabilities may carry over to new domains while its trained-in alignment does not is called the {{sharp left turn}}.

#### Question: Open
id:: 685ce875-5a01-49d7-b506-cf735404f2fd
content:: Name one piece of evidence optimists cite that aligning advanced AI may be fairly easy, and one reason pessimists consider that evidence weak.
assessment-instructions:: Score out of 100. 50 for any one optimist point: current models mostly behave well and follow instructions; RLHF or constitutional training works; models learn human values from training data; full access to weights allows inspection and editing. 50 for a matching pessimist reply: weaker systems can't yet deceive or seize power, so good behavior says little; behavioral training doesn't pin down goals; capabilities may generalize further than alignment.

#### Question: Open
id:: 12202055-44ae-43f6-8020-10906401d06c
content:: Two experts agree that AI will soon be far more capable than humans, but one puts the risk of AI-caused catastrophe near 1% and the other near 90%. What disagreement most likely explains the gap?
assessment-instructions:: Score out of 100. 100 for saying they disagree about how hard alignment is, for example whether current techniques will scale to smarter-than-human systems or whether we can learn from failures before one is fatal. 50 for another real crux without mentioning alignment difficulty, such as whether developers will coordinate or slow down.

#### Question: Open
id:: fd1f6fb5-6181-4adf-aa04-9120d18b5972
content:: What kind of result from future AI systems should move a researcher with an intermediate view of alignment difficulty toward the very hard view?
assessment-instructions:: Score out of 100. 100 for any one of: safety training hiding misaligned behavior rather than removing it; models deceiving evaluators in ways interpretability tools miss; techniques that worked on weaker models failing on stronger ones; scheming appearing in realistic settings. 50 for a vague answer such as "models behaving badly" with no link to detection or scaling.
