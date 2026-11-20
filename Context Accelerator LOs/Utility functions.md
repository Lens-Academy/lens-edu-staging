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
AI safety arguments often model an AI as maximizing a utility function. Knowing what that claim does and doesn't say helps you judge them: for example, what a maximizer does to things we value that its function only partly captures, and why "it has a utility function" says little unless we know what the function is about.

## Lenses
- [[../video_transcripts/machineintelligenceresearchinstitute-eliezer-yudkowsky-ai-alignment-why-its-hard-and-where-to-start|AI Alignment: Why It's Hard, and Where to Start]]: Yudkowsky on what a utility function is, why circular preferences can't have one, what an expected-utility maximizer does, and how a "fill the cauldron" utility function floods the workshop; watch or read the opening, about 0:00–14:00, up to where he turns to measuring impact (2016).
- [[../video_transcripts/robertmiles-ai-that-doesnt-try-too-hard-maximizers-and-satisficers|Maximizers and Satisficers]]: Rob Miles's stamp collector shows why maximizing almost any simple utility function leads to extreme actions, why capping it doesn't help, and why a satisficer may turn itself into a maximizer (2019).
- [[../Lenses/shah-coherence-arguments-do-not-entail-goal-directed-behavior|Coherence Arguments Do Not Entail Goal-Directed Behavior]]: Rohin Shah shows that any behaviour, even random twitching, can be described as maximizing some utility function over histories, so "it maximizes a utility function" tells you little until you know what the function is about; one side of a live debate, read the first two sections (2018).
- [[../Lenses/Iliad/D.1 Decision Theory and Reinforcement Learning/Iliad D.1.1.2 - Completeness, transitivity and ordinal utility|Completeness, Transitivity and Ordinal Utility]]: the two conditions under which preferences can be represented by a utility function, why only the ranking matters, and what goes wrong with incomparable options or cycles (the money pump); formal notation throughout (more advanced).

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
- No, because the agent can't compare A with C
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
- No, but it must be the objective the system was trained on
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
id:: d7f6142a-673c-48b5-8577-84733ba82444
content:: A cleaning robot maximizes a utility function that scores only how little dust is left in a room. Knocking over a vase on its route would let it remove slightly more dust. What would a pure maximizer of this function do, and why? If the designers then add a penalty for broken vases to the function, what problems remain?
assessment-instructions:: Score out of 100. 100 for: it knocks over the vase, since the vase has no weight in its function, so any dust gain wins; and after the fix, other things the function still leaves out can be sacrificed, and the vase can still be broken if the dust gain outweighs the penalty. 70 for the first part plus one remaining problem. 40 for the first part alone, or the action without the reason.
