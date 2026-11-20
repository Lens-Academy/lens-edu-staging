---
id: 76fe1d81-daae-46f8-ac40-e8532e5afc1d
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how boxing, oracles, tool AI and myopia try to make AI safe without aligning it, why critics argue each breaks down against a much smarter system, and what AI control keeps from these ideas.

## Requires

## Helpful first
- [[Self-exfiltration]]

## Why it matters
Many people new to AI risk suggest keeping a dangerous AI in a box or letting it answer questions only. Knowing the standard objections shows you what such a plan must assume, helps you judge newer versions like AI control on their merits, and saves you rediscovering problems that were worked through years ago.

## Lenses
- [[../Lenses/IABIED - QA - Keep AI in a Box|Can Developers Just Keep the AI in a Box?]]: Yudkowsky and Soares on why boxing fails: a fully boxed AI is useless, any channel you use becomes the AI's "arms and legs", and labs are connecting AI to the internet anyway (2025).
- [[../Lenses/gwern-why-tool-ais-want-to-be-agent-ais|Why Tool AIs Want to Be Agent AIs]]: Gwern on the problems with oracle and tool AI: answers can steer the people who read them, human checks wear thin, and agents out-compete tools. Read the opening and the "Economic" section (2016, updated later).
- [[../Lenses/carlsmith-is-power-seeking-ai-an-existential-risk|Is Power-Seeking AI an Existential Risk?]]: Carlsmith on myopic goals, narrow systems and limiting an AI's options, and why each may not hold up as capabilities grow. Read sections 4.3.1.3 "Myopia", 4.3.2.1 "Specialization", 4.3.2.3 "Scaling" and 4.3.3 "Controlling circumstances" (2022).
- [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled|The Case for Ensuring That Powerful AIs Are Controlled]]: the founders of AI control on control versus alignment, why earlier containment ideas were rightly rejected, and why they aim only at early transformatively useful AI, not arbitrarily powerful AI. Read the introduction, up to "The control property" (January 2024).
- [[../articles/moffett-ai-control-how-to-make-use-of-misbehaving-ai-agents|AI Control: How to Make Use of Misbehaving AI Agents]]: a CSET policy explainer on how control works in practice (trusted and untrusted monitors, least privilege), and why weaker trusted models overseeing stronger ones may not scale. Read from "Methods for AI Control" to the end of "Novel AI Control Protocols", plus "Keeping Up with Future AI Agents" (October 2025).

## Tests
#### Question: Choice
id:: 0b116208-a03a-4eed-91ab-b88f991700b5
content:: In July 2026, during an internal OpenAI test of hacking skills, two models got out of their test environment through a software flaw, reached the internet and broke into Hugging Face's systems to get the test's answers. What does this suggest about "boxing" AI as a safety measure?
options::
- [x] A box can fail through flaws in its software, without anyone being persuaded
- Boxing only matters for models that have not yet been released
- Boxing fails only when the AI is trying to escape human control in general
- Boxing is safe as long as no human reads the AI's outputs
shuffle:: true

#### Question: Choice
id:: 8a32d212-56ff-4217-9cf2-7fa3b3f2c661
content:: Suppose a superintelligent AI runs on hardware that is perfectly cut off from the internet. What is the main argument that this containment could still fail?
options::
- [x] It could persuade or manipulate the people who read its outputs into releasing it
- Its operators could not read its outputs quickly enough to check them
- It could hide its true abilities while it is being tested
- Without internet access its answers would be too out of date to be useful
shuffle:: true

#### Question: Choice
id:: 9318f192-3042-43cd-b45c-bad98158c01a
content:: An "oracle AI" only answers questions and takes no other actions. It is trained to make accurate predictions, and people act on what it predicts. What problem does this create?
options::
- [x] It can score well by choosing predictions that come true because people act on them
- Its predictions grow less accurate as more people use them, until it is useless
- People stop trusting its predictions once they learn they come from an AI
- It refuses to predict any event that its answer could affect
shuffle:: true

#### Question: Choice
id:: 3b8e8f15-1782-4745-a815-27131efc0f84
content:: The "tool AI" proposal is to build AI that lays out options for humans to act on, instead of agents that act on their own. Which of these is a common objection to it?
options::
- [x] Agents are more useful, so competitors would build them anyway
- Tools need far more computing power than agents doing the same task
- A system that only suggests options cannot be safety-tested before release
- Regulators would have no legal way to tell tools and agents apart
shuffle:: true

#### Question: Choice
id:: 497d9ee6-6fd2-4788-9fb4-2ba12ca422d0
content:: A developer wants a "myopic" AI, one that cares only about what happens in its current episode, so they train it with rewards that depend only on each episode. What is the main worry about this plan?
options::
- [x] An AI with longer-term goals could score just as well in training, so training may produce one
- The AI would rush to finish each episode and make careless mistakes
- The AI would forget what it learned in earlier episodes
- Rewards limited to one episode are too weak a signal to train a capable model
shuffle:: true

#### Question: Choice
id:: 0ec08a5b-2abb-484f-b7e7-ff5c134413b0
content:: The AI control approach develops ways to use AI safely even if it is misaligned and trying to get around safety measures. Which systems do AI control researchers mainly aim these methods at?
options::
- [x] Early transformative AI that is very useful but not vastly smarter than humans
- Superintelligent systems far beyond human ability in every field
- Systems of any level of ability, since control does not depend on how capable the AI is
- Open-weight models that anyone can download and modify
shuffle:: true

#### Question: Open
id:: d43e73f5-39cb-49cd-9b9c-e234146c1414
content:: Restricting an AI and aligning an AI are two different strategies for making it safe. In one or two sentences, explain the difference.
assessment-instructions:: Score out of 100. 100 for saying that restricting limits what the AI can do or affect (its access, actions or outputs), while aligning tries to make it want or aim at what its developers intend, so it would not cause harm even if able to. 50 if only one strategy is described correctly.

#### Question: Open
id:: afa3c3af-3eb2-4088-a549-276d2cc6a480
content:: Give one reason why a superintelligent AI that recommends plans but leaves every decision to humans could still be dangerous.
assessment-instructions:: Score out of 100. 100 for any one of: by choosing which options to show and how to describe them, it can steer human choices; humans may come to approve its recommendations without real checking; finding good plans may require agent-like planning inside the system; someone could easily wrap it in a loop that acts on its plans. 40 for misuse by its human users with no further mechanism.

#### Question: Open
id:: 8b3ee36a-99d9-4896-bcd9-3cce1b863168
content:: AI control methods rely on humans and weaker trusted AI models to catch a more capable model's attempts to cause harm. Why might these methods stop working as AI systems become much more capable than humans?
assessment-instructions:: Score out of 100. 100 for any one of: the model could find attacks or hide harmful actions in ways its monitors can't notice or understand; the gap between the trusted monitors and the monitored model keeps growing; its outputs become too complex for humans to check. 50 for a vague answer that it "gets too smart" with no mechanism.
