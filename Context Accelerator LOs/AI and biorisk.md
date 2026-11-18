---
id: 758d4e06-8fb2-4f55-8b26-9c57a0e597e5
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why biological misuse is among the most-discussed catastrophic AI risks, how evaluations and lab safeguards try to manage it, what the main wider defences are, and the main arguments for and against prioritising it.

## Requires

## Helpful first
- [[Current AI capabilities]]
- [[Sources of AI catastrophe]]

## Why it matters
Biological misuse shapes much of today's AI policy: company safety frameworks, government testing and model safeguards are often built around it. Knowing what the concern is, how it is measured and where people disagree helps you judge these policies and decide how much of your own effort the risk deserves.

## Lenses

## Tests
#### Question: Choice
id:: 26328695-3727-4b54-830a-64820a071c37
content:: Is the risk of people using AI to help cause a biological catastrophe usually classed as a misuse risk or a misalignment risk?
options::
- [x] Misuse risk
- Misalignment risk

#### Question: Choice
id:: d94ff3d1-f68d-4407-a772-beb8f36b3e06
content:: Why is a deliberately caused pandemic seen as a possible global catastrophe, unlike most attacks?
options::
- [x] Disease can spread far beyond the people first affected
- Hospitals keep few records of unusual illnesses
- Biological attacks tend to leave no evidence behind
- Most countries have no public health agency
shuffle:: true

#### Question: Open
id:: f59d3107-ed66-499d-849e-ab5a130f1d68
content:: In evaluations of AI and biological misuse, what does "uplift" mean?
assessment-instructions:: Score out of 100. 100: how much the AI increases a person's ability to carry out a harmful task compared with what they could do without it, for example with only internet search. 40 if the answer says only that the AI is "helpful" for the task, with no comparison to a baseline.

#### Question: Open
id:: 35174f62-7846-4f20-8b87-1b342011e547
content:: Why does much of the concern about AI and biological weapons focus on people without expertise, rather than on experts?
assessment-instructions:: Score out of 100. 100: experts could already do much of the harm without AI; the worry is that AI acting like an expert adviser (advice, troubleshooting) lowers the expertise needed, so many more people could attempt an attack. 50 for saying AI makes it easier without saying it widens the set of capable people.

#### Question: Choice
id:: 122f3d5e-ba5d-477c-ab4b-cc06608e1c4c
content:: In a frontier AI company's safety framework, what typically follows if evaluations suggest a model has reached a biological-weapons capability threshold?
options::
- [x] Stronger safeguards must be in place before deployment
- The model's weights are published for outside review
- The company pauses its biology research for a year
- The model is handed over to a government agency
shuffle:: true

#### Question: Choice
id:: c8e53a61-2da3-4176-b34b-cd90fb98143d
content:: In 2025, did at least one frontier AI company release a model with stronger safeguards because it could not rule out that the model had reached its biological-risk threshold?
options::
- [x] Yes
- No

#### Question: Choice
id:: e8d60871-bb8a-4e02-8593-05610b795d2d
content:: What is the main aim of biosecurity red-teaming of an AI model before release?
options::
- [x] To find out whether people can get harmful help past its safeguards
- To measure how quickly the model answers biology questions
- To check that the model's biology answers cite their sources
- To train the model on new biology textbooks
shuffle:: true

#### Question: Choice
id:: 282db5b3-9d63-4429-ba5d-e4e73a3834b0
content:: Why do open-weight models make safeguards against biological misuse harder to rely on?
options::
- [x] Anyone with the weights can fine-tune away refusal training
- Their developers are not allowed to test them before release
- They are trained on more biology papers than closed models
- They can only run on government computers
shuffle:: true

#### Question: Choice
id:: 6227a856-8ae4-4a3f-980b-856d86bc5902
content:: Which of these defences against AI-assisted bioweapons would still work if the attacker used an AI model with no safeguards?
options::
- [x] Screening orders placed with DNA synthesis companies
- Training models to refuse dangerous requests
- Classifiers that filter a model's answers
- Red-teaming models before release
shuffle:: true

#### Question: FillBlank
id:: 20d4d1bb-15b8-49d6-ab24-1c8cd0d8b281
content:: Monitoring populations for new disease outbreaks so they can be caught early is called {{biosurveillance|disease surveillance}}.

#### Question: Choice
id:: 04974626-9def-4712-a593-bf644460acf6
content:: Why do many scientists object to AI safeguards that block biology questions broadly?
options::
- [x] Much of the same knowledge is needed for medicine and research
- Blocking questions makes models more likely to be stolen
- Safeguards make models much slower at writing code
- People rarely ask AI models about biology
shuffle:: true

#### Question: Open
id:: 614797f1-6939-49d7-b4ce-1105e1fdde46
content:: Give one argument people make for treating AI-assisted biological misuse as a priority.
assessment-instructions:: Score out of 100. 100 for any one clearly stated argument, for example: a pandemic could kill very large numbers of people; AI could widen the set of people able to attempt an attack; the risk may arrive sooner than risks from superintelligence; it already drives policy and company thresholds, so getting it right matters; defences like synthesis screening are tractable. 30 for a vague answer such as "it is dangerous".

#### Question: Open
id:: fad37c4c-6771-4987-889e-83f17da6cb01
content:: Give one argument people make against AI safety efforts putting a lot of weight on biological misuse.
assessment-instructions:: Score out of 100. 100 for any one clearly stated argument, for example: hands-on lab work, not information, is the main bottleneck; evaluations may overstate real-world uplift; the existing biosecurity field already covers much of it; misaligned superintelligence deserves the effort more; broad safeguards hurt legitimate science. 30 for saying the risk isn't real, with no reason.
