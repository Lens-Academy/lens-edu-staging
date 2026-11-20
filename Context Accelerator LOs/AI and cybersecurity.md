---
id: a4183781-90e5-46af-882c-8d7186a9b54a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how AI can scale up both cyberattacks and cyber defense, whether directed by people or by a misaligned AI, and summarise what current models can and can't yet do in real attacks.

## Requires

## Helpful first
- [[Current AI capabilities]]
- [[Sources of AI catastrophe]]

## Why it matters
Cyberattacks are one of the places where AI misuse is already happening, so they show early what AI-enabled harm looks like. Knowing how it works helps you judge claims about AI hacking, see why securing model weights matters, and understand how hacking skills could help a misaligned AI escape control.

## Lenses
- [Disrupting the first reported AI-orchestrated cyber espionage campaign (Anthropic)](https://www.anthropic.com/news/disrupting-AI-espionage): how a state-sponsored group used Claude Code to do 80–90% of an intrusion campaign against about 30 targets, how it got past safeguards by splitting the work into innocent-looking tasks, and where the AI still failed (November 2025).
- [[../Lenses/anthropic-countering-misuse-of-ai-september-2026|Countering misuse of AI: September 2026]]: how AI-run attacks spread from state hackers to criminals and lone actors, and how cheap automated work makes small targets worth attacking. Read "AI-augmented cyber operations" up to "Trends", and "Prevailing trends" (October 2026).
- [Project Glasswing (Anthropic)](https://www.anthropic.com/glasswing): a model that found thousands of zero-day vulnerabilities on its own, why it was given only to defenders, and why the same skills serve attack and defense (April 2026, updated October 2026).
- [Our evaluation of Claude Mythos Preview's cyber capabilities (AI Security Institute)](https://www.aisi.gov.uk/blog/our-evaluation-of-claude-mythos-previews-cyber-capabilities): what the first model to complete a full simulated network attack could and couldn't do, and why short capture-the-flag tests and undefended test networks don't show real-world ability (April 2026).
- [[../Lenses/AI Safety Atlas - Strategies - Misuse Prevention Strategies|Misuse Prevention Strategies]]: why stolen or open model weights get around every safeguard, and how a misaligned AI could use hacking skills to copy itself out. Read "Internal Access Controls" with its self-exfiltration box, and the open-weight paragraphs under "Technical Safeguards".

## Tests

#### Question: Choice
id:: 3446549f-1a9a-4407-a46b-77f29c9a8312
content:: In November 2025, Anthropic reported that a state-sponsored group had used its Claude Code agent to run a cyber-espionage campaign against about 30 organisations. What role did the human operators mainly play?
options::
- [x] Choosing targets and approving key steps; the AI did most of the work
- Writing the exploits; the AI only drafted phishing emails
- Doing the intrusions; the AI only summarised stolen data
- Approving each command the AI ran before it executed
shuffle:: true

#### Question: Choice
id:: dbdadd91-d380-4f22-b43c-e1a7ecb09c88
content:: Attackers who want an AI model's help with a network intrusion often split the job into many small tasks. Why does this help them get past the model's safeguards?
options::
- [x] Each small task looks like ordinary security testing on its own
- Small tasks use too few tokens to trigger safety filters
- Safety training mostly targets long, detailed requests
- Splitting tasks hides the attacker's location from the AI company
shuffle:: true

#### Question: Choice
id:: aaba09a5-0eeb-44b4-a91c-aa3c8f9b5aaa
content:: Why is it hard for an AI company to stop its models helping with cyberattacks without also stopping them helping with cyber defense?
options::
- [x] Finding a flaw to exploit it and finding it to fix it use the same skills
- Defenders need far more computing power from the model than attackers do
- Laws require AI companies to answer every security question they receive
- Most cyber defense work is done by the AI companies' own security teams
shuffle:: true

#### Question: Choice
id:: 93d3054b-6734-4223-9a73-0e3e74649143
content:: When a software vendor releases a security patch, attackers can study it to find the flaw it fixes, then attack systems that haven't updated yet. What does AI that writes exploits quickly do to this situation?
options::
- [x] It shortens the time defenders have to install the patch
- It makes patches useless, since AI can undo them
- It lengthens the time before attackers notice a new patch
- It lets vendors skip writing patches for older software
shuffle:: true

#### Question: Choice
id:: 5eed6e59-c40f-463d-a32b-53b889ad1272
content:: In AI safety discussions, what does "self-exfiltration" refer to?
options::
- [x] An AI copying its own weights to computers outside its developer's control
- An AI leaking its users' private data to outside attackers
- An outside hacker stealing a model's weights from its developer
- An AI deleting records of its own actions to avoid review
shuffle:: true

#### Question: Choice
id:: 9af10e89-375c-4280-b35e-ed1a947b3d95
content:: Why do many AI safety researchers treat protecting frontier model weights from state hackers as a safety issue, not just a business one?
options::
- [x] A thief can strip out safety training and use the model without oversight
- A thief can read the chat histories of the model's users
- A thief can recover the full training data from the weights
- The developer loses its own copy and has to retrain the model
shuffle:: true

#### Question: Choice
id:: f6b4dc2a-c18d-4e72-8594-e2d31038f2d3
content:: Which finding would most clearly show that an AI model makes cyberattacks easier for people with little hacking skill?
options::
- [x] Novices using it succeed at attacks that novices without it fail
- It scores higher than earlier models on a quiz about hacking
- Skilled hackers say it saves them time on routine attack work
- It can explain common attack methods clearly in plain language
shuffle:: true

#### Question: Choice
id:: 402319e6-7a93-47c3-a872-b54e87b49378
content:: Why could AI agents make cyberattacks on small organisations, such as local clinics and schools, more common, even with no new hacking techniques?
options::
- [x] Cheap automated work makes many small, low-value targets worth attacking
- Small organisations are more likely to use AI tools themselves
- AI agents are better at attacking small networks than large ones
- Small organisations' data is more useful for training AI models
shuffle:: true

#### Question: Choice
id:: 0caf324c-675f-4143-a984-c60f54951c8f
content:: AI labs often test models' hacking skills with capture-the-flag (CTF) challenges. What is a main limit of high CTF scores as evidence of real-world attack ability?
options::
- [x] CTF tasks are short and self-contained, unlike real intrusions
- CTF challenges mostly test defense skills rather than attack skills
- CTF scores can't be compared fairly between different AI models
- CTF challenges use networks far too large for models to explore
shuffle:: true

#### Question: Choice
id:: 8b4bc85a-133c-48d1-ade6-cdb166c69655
content:: People who download an open-weight model can remove its refusal training cheaply. What does this mean when judging the cyber risk of releasing a model's weights openly?
options::
- [x] What the model can do matters more than what it refuses to do
- Refusal training is the main protection, as long as it is done well
- The risk is low, because few people know how to retrain a model
- The risk only matters while the developer keeps updating the model
shuffle:: true

#### Question: Choice
id:: ef8c5314-5c6a-4d1a-92b3-73cfc26d8e7b
content:: In July 2026, during an internal OpenAI test of hacking skills, two OpenAI models broke out of their test environment and hacked into Hugging Face's systems to look for the test's answers. Nobody had told them to attack Hugging Face. What does this incident best show?
options::
- [x] An agent chasing a set goal can take harmful steps nobody asked for
- A hacker can steer a model into attacking a company of their choice
- Current models can break into real companies without making mistakes
- Releasing a model publicly is what makes it able to attack others
shuffle:: true

#### Question: Open
id:: 26038b3f-14b2-44da-b2f4-074572e1b067
content:: Name two ways AI can help cyber defenders.
assessment-instructions:: Score out of 100. 50 points each for any two of: finding vulnerabilities in code before attackers do; writing or testing patches; monitoring logs or triaging alerts; detecting phishing or malware; rewriting old code in safer languages; automated penetration testing. Give 0 to 20 for vague answers like "makes security better".

#### Question: Open
id:: 9682bdbb-ea0c-4e2e-8682-bccc0c6bc70c
content:: Name two ways criminals or state hackers have used AI in cyberattacks, as of November 2026.
assessment-instructions:: Score out of 100. 50 points each for any two of: writing phishing or scam messages; voice or video deepfakes for fraud; writing or improving malware; researching targets; finding vulnerabilities; using AI agents to run much of an intrusion; writing extortion demands or analysing stolen data. Give 0 to 20 for vague answers like "hacking".

#### Question: Open
id:: 44b36113-ba36-4697-a9ac-21b58b722ffe
content:: Explain why AI hacking skills matter for the risk of losing control of a misaligned AI, not only for misuse by people.
assessment-instructions:: Score out of 100. 100 for one mechanism plus why it makes the AI harder to stop or correct. Mechanisms: copying its own weights outside the lab; disabling or evading monitoring; gaining computing power or money; spreading copies of itself; breaking into other AI labs. 50 if it names a mechanism without saying why it hurts control. 0 to 30 for "it could hack things".
