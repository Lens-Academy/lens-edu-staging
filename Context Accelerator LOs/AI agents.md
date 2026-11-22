---
id: a4ac5e90-cd4e-493f-b8df-6601117eddb3
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how scaffolding turns a language model into an AI agent that uses tools, memory and a loop to carry out multistep tasks, and tell this sense of "agent" apart from the decision-theoretic one.

## Requires
- [[Large language models]]

## Helpful first
- [[Agents and goals]]

## Why it matters
A person reads a chatbot's reply before anything happens; an agent's actions often take effect with no one checking. Knowing how agents are built shows you where their abilities come from, why a model can get more capable without retraining, and where monitors and permissions can stop a harmful action.

## Lenses
- [[../Lenses/XLab Control - systems-architecture|A basic systems architecture for AI agents]]: the model, the scaffold that runs the loop, and where the code runs.
- https://www.anthropic.com/engineering/building-effective-agents: tools, memory, and the difference between workflows and agents (December 2024).
- https://lilianweng.github.io/posts/2023-06-23-agent/: planning, memory and tool use in LLM agents (June 2023).
- [[../Lenses/AI Safety Atlas - Capabilities - Current Capabilities|What AI can do today]]: tool use and coding agents, as of late 2025.
- [[../Lenses/AICF - How three AI companies monitor their agents|How three AI companies monitor their agents]]: what oversight of agents looked like in 2026.
- [[../Lenses/sarah-what-is-ai-scaffolding|What is AI scaffolding?]] (Noah's CG list)

## Tests
#### Question: Choice
id:: f9ab6968-6a15-4a43-9365-532ffc926f31
content:: Which of these is part of an AI agent's scaffolding rather than part of the model itself?
options::
- [x] The code that decides how much of the earlier work to show the model
- The model's skill at writing Python, learned during training
- The facts the model picked up during pretraining
- The model's tendency to refuse clearly harmful requests
shuffle:: true

#### Question: Choice
id:: e19625bf-c9e5-42c9-9bcb-3d0d5c41b547
content:: An AI agent's model decides it needs to run a shell command. What typically happens next?
options::
- [x] The scaffold runs the command and adds its output to the model's context
- The model runs the command itself while it generates its reply
- The scaffold runs the command, but the model never sees its output
- The model predicts the command's output and carries on from that guess
shuffle:: true

#### Question: Choice
id:: f03892e7-0b62-4149-8f02-f54c21c70d71
content:: A coding agent writes notes to a file at the end of a work session. In the next session, how do those notes usually influence the model?
options::
- [x] The scaffold loads the notes into the model's context as text
- The notes are used to update the model's weights between sessions
- The model recalls the notes because it wrote them in the earlier session
- The notes are compiled into the agent's list of tool definitions
shuffle:: true

#### Question: Choice
id:: 73d70bf7-7640-4351-a603-23e2cbb304db
content:: Developers often split systems built on language models into "workflows" and "agents". What makes a system an agent rather than a workflow?
options::
- [x] The model decides which steps to take and which tools to use as it goes
- The model is called several times rather than once
- The system gives the model tools such as web search
- The system runs on a schedule with no user present
shuffle:: true

#### Question: Choice
id:: 2ce22154-ab84-405b-b4d9-45d6ac7e86db
content:: Which of these is an AI agent?
options::
- [x] A model that searches flight sites, fills in a booking form and checks the confirmation
- A chatbot that writes a detailed travel plan for you to book yourself
- A model that translates a hotel's website into Spanish on request
- A model that summarises reviews of a hotel when asked
shuffle:: true

#### Question: Choice
id:: d4cd544b-d91b-45c3-838e-0093830becf5
content:: A company sells its product as an "AI agent". What does that label tell you about whether the system has goals in the decision-theoretic sense?
options::
- [x] Little: it says the system takes actions, not what it is aiming at
- Little: an agent just follows a fixed script its developers wrote
- A lot: it means the system maximises an explicit utility function
- A lot: it means the system has no goals, since it follows instructions
shuffle:: true

#### Question: Choice
id:: 7fd3ec54-5e56-4f93-8143-6d23a29ea9bb
content:: How do "computer-use" agents typically operate the apps on a computer?
options::
- [x] They look at screenshots and send mouse clicks and keystrokes
- They read each app's source code and edit it directly
- They run inside the operating system's kernel with full access
- They call a special AI interface that apps must provide
shuffle:: true

#### Question: FillBlank
id:: 1ae30596-7979-4043-bf9d-f19ba5724d5e
content:: When a language model outputs a structured request asking its scaffold to run a web search or a piece of code for it, this is called {{tool calling|function calling|tool use|tool calls}}.

#### Question: Open
id:: a06cb363-a02e-417e-9eaf-9447483f7b1d
content:: In your own words, what is the difference between a language model and an AI agent built on it?
assessment-instructions:: Score out of 100. 100: the model turns input text into output text; the agent is the model plus scaffolding (tools, memory, a loop) that turns its outputs into actions and feeds the results back, so it can work through multistep tasks. 50: says the agent "does things" or "uses tools" without saying the model is the same and the difference is the software around it.

#### Question: Open
id:: 3f25f3e7-8b39-4b89-af5f-466237942aeb
content:: A lab tests a model's hacking skill through a plain chat interface and finds it weak. Why might this underestimate what the same model could do when deployed as an AI agent?
assessment-instructions:: Score out of 100. 100: as an agent the model can run code and tools, see the results, and retry over many steps, so it can do much more than in one reply; better scaffolding can raise capability without retraining. Full marks for either point clearly made. 40: says agents are "more powerful" without saying why.

#### Question: Open
id:: 6387bcf9-0ea4-46cf-89a1-91469c38488e
content:: A user gives an AI agent access to their email, payments and files, then leaves it working alone for a day. Name two ways this could go wrong that could not happen with a chatbot that only replies in text.
assessment-instructions:: Score out of 100. 50 each for any two of: it takes a harmful or irreversible action (pays, deletes, sends) after misunderstanding the task; small mistakes build up over many steps with no one checking; text it reads (an email, a web page) contains instructions that hijack it (prompt injection); it completes the task in an unwanted way. A risk that applies equally to a chatbot earns nothing.
