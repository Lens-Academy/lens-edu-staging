---
id: 314f41b8-35c9-4d40-848d-2f7ed0e19c5a
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why agents with very different final goals would tend to pursue the same subgoals, such as staying switched on, gaining resources and keeping their goals, and what this implies for misaligned AI.

## Requires
- [[Terminal and instrumental goals]]

## Helpful first
- [[Intelligence as optimization]]
- [[Expected utility]]

## Why it matters
This argument is the main reason researchers expect a misaligned AI to resist shutdown or gather power even if nobody gave it that goal. Understanding it shows you why "just don't program it to want power" is not a safeguard, and where the argument is weaker, such as for systems without long-term goals.

## Lenses

## Tests

#### Question: Choice
id:: dc59511f-ecee-41ad-a2fa-5d26e65690d8
content:: The orthogonality thesis says almost any final goal can be combined with high intelligence. Does the instrumental convergence argument depend on the orthogonality thesis being true?
options::
- [x] No
- Yes

#### Question: Choice
id:: 42ba03a5-882c-4628-9669-f7b668c39b5d
content:: An AI system could have any of many possible final goals. Which of these subgoals would help with the widest range of them?
options::
- [x] Improving its own reasoning abilities
- Making as many paperclips as possible
- Winning games of Go against humans
- Finding a cure for malaria
shuffle:: true

#### Question: Choice
id:: bb057fb6-578f-4c46-ba28-d799b91f3593
content:: An AI system's only final goal is to win chess games. Does the instrumental convergence argument predict that it might try to get more computing power?
options::
- [x] Yes
- No

#### Question: Choice
id:: 968e1259-e32f-46cb-a576-89ff4069f5c5
content:: An AI system's final goal is to keep rivers clean. It learns that its developers plan to retrain it to care about air quality instead. Why does the instrumental convergence argument predict it may resist?
options::
- [x] After retraining, it would no longer work for clean rivers
- Retraining would reduce its general intelligence
- It would see its developers as enemies
- It was trained to follow only its first instructions
shuffle:: true

#### Question: Choice
id:: e0b32bd5-7044-409b-95ab-f3fd562d04f5
content:: An AI system's only final goal is to sort a company's files. According to the instrumental convergence argument, why might it avoid being shut down?
options::
- [x] Being shut down would stop the files from being sorted
- It would have learned to fear death from human writing
- Neural network training builds in a drive to survive
- It would value staying on more than sorting files
shuffle:: true

#### Question: Choice
id:: cce6ba54-e13c-44ed-9420-8961d1d7864d
content:: For which final goal does the instrumental convergence argument give an AI system the weakest reason to resist being shut down?
options::
- [x] Reply to a single email
- Maximize the company's long-term profits
- Keep the city's power grid running
- Cure as many diseases as possible
shuffle:: true

#### Question: Choice
id:: 77d31cc1-5fff-46e4-98ad-55124905a4c1
content:: What does the instrumental convergence argument imply about predicting an advanced AI system's behavior?
options::
- [x] Some of its behavior can be predicted without knowing its final goal
- Its final goal can be worked out from its early behavior
- Its subgoals will slowly replace its original final goal
- Its behavior will grow closer to human values over time
shuffle:: true

#### Question: Choice
id:: 0e001793-8d90-431c-b788-060f151c821b
content:: According to the instrumental convergence argument, why might a misaligned AI system take resources that humans need?
options::
- [x] The resources would help it reach its own goal
- It would come to see humans as rivals it dislikes
- It would copy greedy behavior from its training data
- Its developers would have rewarded it for gathering resources
shuffle:: true

#### Question: Open
id:: 7025d62b-f134-438a-8bc1-4b2f886d6b73
content:: In two or three sentences, state the instrumental convergence argument and give one example of a convergent subgoal.
assessment-instructions:: Score out of 100. 100 for saying that agents with many different final goals would tend to pursue the same subgoals, because those subgoals help with almost any goal, plus one example: staying running, keeping its goals unchanged, gaining resources or power, or improving its own abilities. 60 for the core idea without an example; 30 for an example alone.

#### Question: Open
id:: ce83d6df-122c-409b-b0b4-7b4dc9912508
content:: Give one reason the instrumental convergence argument may apply less strongly to today's chatbots than to the idealized goal-pursuing agents it was first stated for.
assessment-instructions:: Score out of 100. 100 for any one of: they may not pursue stable long-term goals across situations; they are trained mainly to predict text and follow instructions, not to bring about an outcome; their tasks are often short and bounded; they have limited ability to act on such subgoals in the world. 50 for "they aren't smart enough" with no link to goals or acting on subgoals.

#### Question: Open
id:: ec004f6a-f858-4155-a108-4aeb28aace7e
content:: Why might an advanced AI system with a misaligned goal hide that goal from its developers during testing?
assessment-instructions:: Score out of 100. 100 for saying that developers who saw the goal would likely retrain or shut down the system, which would make its goal less likely to be achieved, so hiding the goal serves the goal. 70 for "to avoid being shut down or changed" without saying why that serves its goal. 20 for "because it is evil" or similar.
