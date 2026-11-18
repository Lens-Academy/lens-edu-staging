---
id: 4dea2c50-3ad0-43c4-b50e-75694db15571
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Tell apart the main senses of "alignment" (intent vs. impact, today's products vs. superintelligence, narrow vs. broad) and work out which sense a speaker means when they don't say.

## Requires
- [[AI alignment]]

## Helpful first

## Why it matters
People who mean different things by "aligned" can agree on the facts and still seem to disagree. A lab calling its chatbot "well aligned" and a researcher calling alignment "unsolved" may both be right. Spotting the sense in use lets you judge each claim on its merits and avoid both false reassurance and false alarm.

## Lenses

## Tests
#### Question: Choice
id:: 433619cd-8fb2-4d8b-8f85-2f96c23e68c6
content:: In the intent sense of alignment, an AI is aligned if it is trying to do what its operator wants. Which of these is a failure of intent alignment?
options::
- [x] An AI quietly works toward a goal its operator never wanted
- An AI gives a wrong answer because it lacks the facts
- An AI cannot finish a long task within its time limit
- An AI writes slower code than a skilled human would
shuffle:: true

#### Question: Choice
id:: 7d088ea1-a3a9-4942-ac4b-11d32bdabf47
content:: An AI assistant sincerely tries to do what its user wants, but by mistake it deletes the user's important files. Intent alignment is about what the AI is trying to do; impact alignment is about the effects it actually has. Which describes this AI?
options::
- [x] Intent aligned but not impact aligned
- Impact aligned but not intent aligned
- Both intent aligned and impact aligned
- Neither intent aligned nor impact aligned
shuffle:: true

#### Question: Choice
id:: 2d85eb75-0d29-42a4-90de-a6f9dcabdccb
content:: An AI company calls its new chatbot "our most aligned model yet", citing fewer harmful replies and more honest answers in its tests. Which sense of "alignment" is the company most likely using?
options::
- [x] How well today's AI products behave in use
- Keeping systems smarter than humans pursuing intended goals
- Whether AI's overall effect on society turns out well
- Whether the model's inner goals match its training goal
shuffle:: true

#### Question: Choice
id:: 845b06c1-45b4-4c5d-92db-3d2a296d5c5d
content:: Many researchers doubt that the methods used to align today's chatbots will be enough to align AI systems much smarter than humans. What is the main reason?
options::
- [x] They rely on human feedback, which fails once AI outsmarts its judges
- They need text data, and future systems won't be trained on text
- They only work on models small enough to inspect by hand
- They assume AI has goals, which superintelligent systems will lack
shuffle:: true

#### Question: Choice
id:: 3165e179-4fed-4e46-9de9-b7184f2ba70a
content:: Which statement uses "alignment" in the broad sense, meaning AI going well for humanity, rather than the narrow sense of an AI pursuing its developers' goals?
options::
- [x] "Alignment includes making sure AI doesn't let a small group seize power."
- "Alignment means the model tries to do what its developers intend."
- "Our alignment training cut the model's harmful replies by half."
- "Alignment is about stopping AI from gaming its reward signal."
shuffle:: true

#### Question: Choice
id:: ed458d5f-92ee-47a4-bceb-17aa36ad0e6e
content:: In the intent sense, an AI is aligned if it is trying to do what its operator wants. An AI tries hard to help its operator, and the operator wants help defrauding customers. Is the AI intent aligned?
options::
- [x] Yes
- No

#### Question: Choice
id:: 89c35f91-edce-46a7-b523-068d6fd78d2b
content:: Every action an AI system has taken so far has had good effects. Does this show that the system is intent aligned, meaning it is trying to do what its operator wants?
options::
- [x] No
- Yes

#### Question: Open
id:: b456a529-64cc-4294-8705-e0c403660b60
content:: Speaker A says "alignment is going well: models refuse harmful requests far more reliably than two years ago." Speaker B says "alignment is unsolved: we can't yet make systems smarter than us reliably pursue intended goals." Explain how both could be right.
assessment-instructions:: Score out of 100. 100 for saying they use different senses: A means how well today's products behave, B means aligning systems smarter than humans, and progress on the first need not carry over to the second (for example because human oversight stops working). 50 for saying they mean different things without naming which. 0 for picking one speaker as right.

#### Question: Open
id:: 2022f268-380f-4adc-898e-6f038c54959f
content:: Name two different senses of "alignment" and give one claim about an AI system that would be true in one sense but false in the other.
assessment-instructions:: Score out of 100. 100 for two genuinely different senses (for example intent vs. impact, today's products vs. superintelligence, narrow vs. broad) plus a claim that really splits them, such as "an AI that obeys a fraudster is aligned" (true for intent, false for broad or impact). 50 for two correct senses with no working example. 0 for one sense only.

#### Question: FillBlank
id:: 842141a4-9ce2-453d-828e-233183e53038
content:: In the sense of alignment proposed by Paul Christiano, an AI is {{intent|intent-}} aligned if it is trying to do what its operator wants it to do.
