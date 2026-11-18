---
id: 75f1f5e0-38ee-4f50-8e21-71a0c9f773a5
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what AI-driven robots can and can't do as of late 2026, why robotics has lagged AI that works with text and code, and how physical capability affects AI's economic impact and risk.

## Requires
- [[Machine learning]]

## Helpful first

## Why it matters
An AI that can only use computers still depends on people for physical work: building chips, running power plants, repairing data centers. Capable robots would remove that dependence, let AI automate much more of the economy, and let AI systems build things, including more robots, quickly. Tracking robotics tells you how near those changes are.

## Lenses

## Tests
#### Question: Choice
id:: 2f46b260-3762-49f3-aace-98c60bfe1967
content:: As of November 2026, which of these tasks remains hardest for AI systems to do reliably?
options::
- [x] Tidying a kitchen in a home the system has never seen
- Solving competition-level math problems
- Beating the world's best players at Go
- Writing working code for a small website
shuffle:: true

#### Question: FillBlank
id:: 2d39f202-07e9-46d5-834f-ef14a3971384
content:: The observation that skills humans find effortless, like seeing and handling objects, are often harder to automate than skills like chess is called {{Moravec's paradox|Moravec paradox}}.

#### Question: Choice
id:: a461a314-694f-4d3c-879c-81b1828abac0
content:: What is a main reason robot learning has progressed more slowly than language models?
options::
- [x] There is no internet-scale record of robot actions to train on
- Neural networks cannot process camera images fast enough
- Robot control needs far larger models than language does
- Robotics companies have attracted little investment since 2015
shuffle:: true

#### Question: Choice
id:: b52a744d-d884-4f60-a890-40e550407708
content:: What does a vision-language-action (VLA) model do in robotics?
options::
- [x] Takes camera images and an instruction and outputs the robot's movements
- Describes in words what a robot's cameras see, for a human operator
- Generates simulated videos of robots for training other models
- Checks a robot's planned movements against hand-written safety rules
shuffle:: true

#### Question: Choice
id:: 14a9f516-313c-4123-9326-195ab1f264e6
content:: Many recent robot control models start from a model pretrained on internet images and text. What does this mainly add?
options::
- [x] General knowledge of objects and language, so less robot data is needed
- Detailed motor commands taken from text that describes robot arms
- Faster reactions while the robot's motors are moving
- The ability to control a robot with no robot training data
shuffle:: true

#### Question: Choice
id:: a7728d25-2ab4-4f7f-a979-92bdad8e8e1b
content:: People remotely controlling today's robot arms can do many household tasks, like loading a dishwasher. For such tasks, what does this suggest is the bigger barrier to useful home robots?
options::
- [x] The AI software that controls the robot
- The robot's mechanical hardware

#### Question: Choice
id:: e71c93c5-a12f-494f-82a7-47d0243079e8
content:: Robot developers often train control policies in physics simulations before using them on real robots. What is the main difficulty with this approach?
options::
- [x] Real-world physics differs from the simulation, so skills often transfer poorly
- Simulated training runs much slower than training on physical robots
- Simulations cannot produce the camera images a robot would see
- A policy trained in simulation cannot be copied onto many robots
shuffle:: true

#### Question: Choice
id:: 6613c592-1c2b-412d-a635-3b990c742fef
content:: A company's warehouse robot learns a new packing task. Compared with training human workers, what is a key difference in how the skill spreads?
options::
- [x] The learned software can be copied to every robot of the same model
- Each robot must be retrained from scratch by a human operator
- Robots need more practice than humans before reaching full speed
- The skill spreads slowly because robots cannot share their data
shuffle:: true

#### Question: Choice
id:: 96f3da95-1b9b-4060-8240-d93c728ad573
content:: As of November 2026, which best describes driverless taxis?
options::
- [x] Paid rides with no safety driver run daily in many US and Chinese cities
- No company yet offers paid rides without a safety driver on board
- They run in a few test zones but carry no paying passengers
- Cars that drive themselves anywhere unsupervised are sold to the public
shuffle:: true

#### Question: Choice
id:: 21d135fd-ba83-4cd4-b62e-650f147e7c08
content:: As of November 2026, which best describes humanoid robots?
options::
- [x] Tens of thousands ship per year, mostly for research, demos and pilots
- Hundreds of thousands do routine factory work, mostly in China
- No company has yet sold one to a customer outside a research lab
- Thousands work in homes, doing chores without any remote help
shuffle:: true

#### Question: Choice
id:: 838f92ec-bd80-42f2-8584-64cc1145f3d5
content:: According to the International Federation of Robotics, one country installed more than half of all new industrial robots worldwide in 2024. Which country?
options::
- [x] China
- United States
- Japan
- Germany
shuffle:: true

#### Question: Open
id:: 9b6c5467-9bc5-4699-ae04-66f234427b74
content:: Why could capable robots make a misaligned AI system more dangerous, even if the AI's intelligence stayed the same?
assessment-instructions:: Score out of 100. 100 for: without robots, the AI depends on humans for physical work (chips, power, data center upkeep, building things), which gives humans leverage; capable robots would remove that dependence and let it act or build in the world directly. 50 for "it could act physically" without the dependence point. 30 for only "robots could attack people".

#### Question: Open
id:: cff12735-06f5-49a7-a40a-3874a2664b33
content:: Suppose AI could do nearly all work done at a computer, but robotics stayed where it was in 2026. Why would AI's effect on the economy still be limited?
assessment-instructions:: Score out of 100. 100 for: much of the economy's work is physical (for example manufacturing, construction, care, transport, farming), so it would still need human workers, and that physical work would limit how far and how fast output could grow. 50 for naming physical jobs without saying they hold back overall growth.

#### Question: Open
id:: 9c725de3-3836-4a67-9922-087080413f68
content:: An AI system has no access to robots. Name one way it could still get physical tasks done in the world.
assessment-instructions:: Score out of 100. 100 for any one of: paying, hiring or persuading humans to do the work (for example through gig platforms or contractors); controlling existing automated equipment, such as automated labs, factories or vehicles; ordering goods and services online. 0 for answers that need it to have robots.
