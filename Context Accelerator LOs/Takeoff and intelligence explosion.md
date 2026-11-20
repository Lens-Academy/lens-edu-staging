---
id: b33e7f55-ea22-4cfd-b2df-613ef59a408f
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Define takeoff, intelligence explosion, recursive self-improvement and the technological singularity, and explain the basic argument that AI able to do AI research could drive a rapid, self-reinforcing rise in capability, along with its main weak points.

## Requires
- [[AGI and superintelligence]]

## Helpful first

## Why it matters
How fast AI could go from human level to far beyond it decides how much time people have to respond. The question is live: AI already speeds up AI research at some labs. These terms and arguments help you follow forecasts and safety plans that depend on takeoff speed, and judge what makes a fast takeoff more or less likely.

## Lenses
- [[../Lenses/AI Safety Atlas - Capabilities - Takeoff|Takeoff]]: what takeoff speed is and how it differs from timelines, slow versus fast takeoff, the automating-research and intelligence-explosion arguments, machine advantages such as copying, and why a fast takeoff leaves only one chance to get safety right (2026).
- [[../Lenses/What are the differences between a singularity, an intelligence explosion, and a hard takeoff|Singularity, Intelligence Explosion, Hard Takeoff]]: short definitions that keep the singularity, intelligence explosion, hard takeoff and FOOM apart, and why an intelligence explosion need not be sudden.
- [[../Lenses/ahead-ii-from-agi-to-superintelligence-the-intelligence-explosion|From AGI to Superintelligence: the Intelligence Explosion]]: the case for a fast intelligence explosion, from a leading proponent: millions of copies of automated AI researchers, and the main bottlenecks (compute for experiments, the last steps of automation, ideas getting harder to find). Read from the opening to the end of the bulleted list under "Possible bottlenecks" (May 2024).
- [Inside the Race to Make AI Build Itself (TIME)](https://time.com/article/2026/08/07/ai-recursive-self-improvement-anthropic-openai/): how Anthropic and OpenAI are using AI to speed up their own research, what the risks are, and why critics such as Arvind Narayanan and Gary Marcus doubt a runaway loop (August 2026).
- [[../Lenses/forethought-will-ai-rd-automation-cause-a-software-intelligence-explosion|Will AI R&D Automation Cause a Software Intelligence Explosion?]]: Forethought's analysis of whether AI improving AI software could outrun diminishing returns; read the sections from "A toy model to demonstrate the dynamics of a software intelligence explosion" to "In the real world, are returns to software R&D greater or less than one?" (2025) (more advanced).

## Tests

#### Question: Choice
id:: d3ec9d1a-2c8a-4eaf-9212-e7f8abaa1c45
content:: Which of these is an example of recursive self-improvement in AI?
options::
- [x] An AI system invents a training method used to build its stronger successor
- Human raters score a model's answers so engineers can fine-tune it
- A model gets more accurate when it is trained on more data
- Engineers give the next version of a model a larger dataset
shuffle:: true

#### Question: Choice
id:: a752d35b-2742-44bf-97b2-ca82ddb25059
content:: People use "technological singularity" in several different senses. Which of these is NOT one of the common senses?
options::
- [x] The moment AI systems first become conscious
- A point past which the future is very hard to predict
- A loop of smarter minds building still smarter minds
- Technological change that keeps speeding up over time
shuffle:: true

#### Question: Choice
id:: 916d0d8f-17b1-4116-9e54-be5defdbec8e
content:: Which finding would most weaken the argument for an intelligence explosion?
options::
- [x] Each capability gain takes much more research effort than the one before
- AI systems turn out to be better at coding than at other tasks
- AI companies keep increasing what they spend on computing power
- Human AI researchers often move from one company to another
shuffle:: true

#### Question: Choice
id:: 6ce6f21f-1111-4d57-bb8d-e08296462041
content:: Suppose an AI system can do AI research as well as a skilled human researcher. Which property could let it speed up research far more than hiring one more researcher would?
options::
- [x] It can be copied and run as many instances at once
- It has read more research papers than any human has
- It can explain its reasoning in plain language
- It can search the internet for related work
shuffle:: true

#### Question: Choice
id:: c671e3d3-a383-4e3d-8054-3c0945a7bd1e
content:: Two forecasters agree that AGI will probably arrive around 2035. One expects superintelligence within a year after that; the other expects it to take decades. What do they mainly disagree about?
options::
- [x] Takeoff speed
- When AGI will arrive
- The definition of AGI
- Whether AI will be aligned
shuffle:: true

#### Question: Choice
id:: 5180570e-815a-4304-8030-dffa4a42b720
content:: Does the basic argument for an intelligence explosion require AI systems to want to make themselves smarter?
options::
- [x] No, humans could direct AI systems to do AI research
- Yes, the AI must itself be trying to become smarter

#### Question: Open
id:: 6e437810-b0af-464c-91a0-f28392a6404a
content:: The intelligence explosion argument says that once AI can do AI research as well as top human researchers, progress could keep speeding up, not just get a one-off boost. Explain why it could keep speeding up.
assessment-instructions:: Score out of 100. 100 for a feedback loop: better AI makes better AI researchers, who make the next improvement faster, and this repeats. 50 for only saying AI adds many more or faster researchers (e.g. running many copies), without the loop. 0 for answers that only mention more money or bigger computers.

#### Question: Open
id:: 08774b78-4c0b-41b8-9810-ecd1f919c824
content:: Suppose AI systems can do AI research as well as human researchers. Name one physical bottleneck that could still slow an intelligence explosion, and say why it would.
assessment-instructions:: Score out of 100. 100 for any one of: computing power for experiments and training runs; chip manufacturing capacity; energy supply; time to build data centres; gathering real-world data. It needs a short reason, e.g. research needs experiments, which need compute. 50 for a bottleneck named with no reason. 25 for a non-physical bottleneck such as regulation.

#### Question: Open
id:: aa69453d-a095-4c76-8cce-f40df707798e
content:: Give one reason why a rapid intelligence explosion would make the risks from advanced AI harder to manage.
assessment-instructions:: Score out of 100. 100 for any one of: little time to notice and fix problems such as misalignment; safety methods tested on weaker systems may fail on much stronger ones; laws and institutions could not keep up; one developer could gain a decisive lead over everyone else. 50 for a vague answer such as "it would be dangerous" with no clear reason.
