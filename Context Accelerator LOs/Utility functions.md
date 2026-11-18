---
id: 7db21092-f07c-4498-b1cc-21a0e8ad136c
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how a utility function represents an agent's preferences as numbers that rank outcomes, which preferences can be represented this way, and what it means for an agent to maximize one.

## Requires
- [[Agents and goals]]

## Helpful first

## Why it matters
AI safety arguments often model an AI as maximizing a utility function. Knowing what that claim does and doesn't say helps you judge those arguments: for example, why a maximizer gives no weight to anything its function leaves out, and why "it has a utility function" says little unless we know what the function is about.

## Lenses

## Tests

#### Question: Choice
id:: 8a87e1d8-e93f-4605-89dd-43149efe883d
content:: What does a utility function do?
options::
- [x] Assigns numbers to outcomes so that preferred outcomes get higher numbers
- Measures how much pleasure each outcome gives the agent
- Measures how much money each outcome is worth to the agent
- Estimates how likely the agent is to reach each outcome
shuffle:: true

#### Question: Choice
id:: 8587f9c6-806d-4410-a2c4-2131db5e98aa
content:: An agent prefers A to B, B to C, and C to A. Can a utility function represent these preferences?
options::
- [x] No, because u(A) > u(B) > u(C) > u(A) is impossible
- Yes, by giving A, B and C equal utility
- Yes, if the utility function is allowed to be unbounded
- Yes, by using negative numbers for some outcomes
shuffle:: true

#### Question: Choice
id:: 409c63cf-c710-415f-8b7f-98b5359dd60a
content:: An agent can't compare two job offers: it neither prefers one nor sees them as equally good. Which condition for representing preferences with a utility function does this break?
options::
- [x] Completeness
- Transitivity
- Continuity
- Independence
shuffle:: true

#### Question: Choice
id:: c5456a8e-92b4-4bf4-977c-20ab6582344a
content:: A utility function gives outcome A the number 1, B the number 2 and C the number 3. When choosing among sure outcomes, with no uncertainty, which other assignment represents exactly the same preferences?
options::
- [x] A 10, B 20, C 1,000
- A 3, B 2, C 1
- A 1, B 3, C 2
- A 2, B 2, C 3
shuffle:: true

#### Question: Choice
id:: 22bd5af4-e1d4-4109-9498-a68cd07a87ee
content:: An AI's utility function gives higher numbers to world states that contain more paperclips. What do those numbers measure?
options::
- [x] Which states the AI prefers to which others
- How much pleasure each state gives the AI
- How useful each state is to the AI's designers
- How likely the AI is to reach each state
shuffle:: true

#### Question: Choice
id:: c9898506-d7b5-4b9b-a4a9-ae9b521145d2
content:: An AI system's choices are well described as maximizing a particular utility function. Does that mean the function is stored explicitly in its code or weights?
options::
- [x] No, the function can summarize how its choices rank outcomes
- Yes, a system has to store a function to maximize it
- Yes, otherwise its choices would have no consistent pattern
shuffle:: true

#### Question: Choice
id:: 35e6720b-1a29-4064-9ac2-82251837706a
content:: A system flips a coin each second to choose its next action. If a utility function may be defined over a system's whole history of actions, which statement is correct?
options::
- [x] It can be described as maximizing a function that scores its actual history highest
- It can't be described as maximizing a utility function, since it acts randomly
- It needs an internal representation of a goal before it can maximize one
- It needs its coin flips to settle into a pattern before it can maximize one
shuffle:: true

#### Question: FillBlank
id:: 06740f3c-af9e-4ef9-9820-c982976402c4
content:: An agent that takes the first option good enough to meet a threshold, instead of searching for the best one, is called a {{satisficer|satisficing agent}}.

#### Question: Open
id:: 03f5e7df-0850-4ff2-9d0d-4171ccd898aa
content:: What does it mean for an agent to maximize a utility function?
assessment-instructions:: Score out of 100. 100 for: among the options available to it, the agent chooses the one whose outcome has the highest utility (or the highest expected utility when outcomes are uncertain). 50 for a vague answer such as "it pursues its goals" that doesn't say it picks the highest-ranked option.

#### Question: Open
id:: 9d29efed-accc-458d-abbc-8165a2260ee4
content:: A cleaning robot maximizes a utility function that scores only how little dust is left in a room. Knocking over a vase on its route would let it remove slightly more dust. What would a pure maximizer of this function do, and why?
assessment-instructions:: Score out of 100. 100 for: it knocks over the vase, because the vase has no weight in its utility function, so any gain in the dust score wins. 50 for the right action without the reason, or for noting only that the function ignores the vase.
