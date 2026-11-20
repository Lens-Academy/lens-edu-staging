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
- [[../articles/darioamodei-dario-amodei-the-adolescence-of-technology|The Adolescence of Technology]]: Anthropic's CEO makes the case for concern. AI could walk people without expertise through making a bioweapon, so Anthropic released its 2025 models under stronger safeguards; he then covers his answers to skeptics and three defences: model guardrails and classifiers, government rules including DNA synthesis screening, and defences such as early detection and vaccines. Read section 2, "A surprising and terrible empowerment" (January 2026).
- [[../articles/ai-security-institute-frontier-ai-trends-report|Frontier AI Trends Report]]: the UK AI Security Institute's test results on how much models now help with biology, how expert red-teamers still find ways past safeguards, and why open-weight models are hard to protect. Read "Chemistry & biology" in section 3, section 4 "Safeguards" and section 7 "Open-source models" (December 2025).
- [Rethinking the De-skilling Narrative in AI and Biological Weapons Policy (Georgetown Journal of International Affairs)](https://gjia.georgetown.edu/science-technology/rethinking-the-de-skilling-narrative-in-ai-and-biological-weapons-policy/): the sceptic's case from a biodefence scholar: hands-on know-how, not information, is the bottleneck, and overstated threat assessments risk curbing useful science (August 2026).
- [Do the biorisk evaluations of AI labs actually measure the risk of developing bioweapons? (Epoch AI)](https://epochai.substack.com/p/do-the-biorisk-evaluations-of-ai): a close look at the evals labs cite, what "uplift" over an internet baseline means, and where tests may overstate or understate real risk; concludes that labs' caution was largely justified (June 2025) (more advanced)

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
- It is often hard to tell who carried out the attack
- It can cost far less than building a nuclear weapon
- It can be planned in secret by a small group
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
- The model is retrained with all biology data removed
- Release goes ahead once the result is reported to government
- The model is offered only to vetted biology researchers
shuffle:: true

#### Question: Choice
id:: c94fac64-c060-490d-81f1-ef2d9b8e168b
content:: In 2025, Anthropic (for Claude Opus 4) and OpenAI (for ChatGPT Agent) released models with stronger safeguards against biological misuse. What was their stated reason?
options::
- [x] They could not rule out that the model had reached their biological-risk threshold
- Tests had shown the model gave real help to someone attempting an attack
- A government regulator had ordered the safeguards before release
- Users had been caught using earlier models to plan attacks
shuffle:: true

#### Question: Choice
id:: e8d60871-bb8a-4e02-8593-05610b795d2d
content:: What is the main aim of biosecurity red-teaming of an AI model before release?
options::
- [x] To find out whether people can get harmful help past its safeguards
- To check that the model's answers to biology questions are accurate
- To estimate how many users will ask the model about biology
- To decide which biology courses the model should recommend
shuffle:: true

#### Question: Choice
id:: 282db5b3-9d63-4429-ba5d-e4e73a3834b0
content:: Why do open-weight models make safeguards against biological misuse harder to rely on?
options::
- [x] Anyone with the weights can fine-tune away refusal training
- They are always more capable at biology than closed models
- Their developers cannot run evaluations on them before release
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

#### Question: Choice
id:: 05da1752-b174-49ca-89ae-8cc27f4c2a05
content:: Why is early detection of disease outbreaks valued even by people who doubt that AI gives attackers much help?
options::
- [x] It helps against outbreaks of any origin
- It stops attackers from getting AI help
- It makes model safeguards unnecessary
- It is only needed once AI help is proven
shuffle:: true

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
