---
id: dca79474-bf42-455c-8b88-0dc896d10e44
tldr: "How much damage could an AI cause if it stopped holding back and tried its hardest? Dangerous capability evaluations probe that upper limit, testing whether models can run cyberattacks, deceive people under pressure, copy themselves onto new servers, plan over long horizons, or notice when they are being tested. This section walks through how researchers safely measure abilities we hope no model ever uses."
summary_for_tutor: "Covers how dangerous capability evaluations establish upper bounds on the harm a model could cause under maximum elicitation, as opposed to average-performance metrics. Explains the general evaluation process: combining elicitation techniques, testing capability combinations and emergent behaviors, and using sandboxed environments. Surveys five dangerous-capability domains with concrete benchmarks and evaluation protocols: cyber-offense (spear-phishing, vulnerability exploitation, autonomous cyber operations, code interpreter abuse, insecure code generation, prompt injection), deception (TruthfulQA and Apollo's insider trading evaluation), autonomous replication (METR's ARA tests), long-term planning (METR's task-completion time horizons), and situational awareness (the SAD benchmark)."
title: "Dangerous Capability Evaluations"
{++{"author":"Elias's AI","timestamp":1787570172290}@@reading_minutes: 40
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Dangerous Capability Evaluations|Dangerous Capability Evaluations]]{++{"author":"Elias's AI","timestamp":1787570172290}@@

#### Text
optional:: true
content::
These evaluations measure what a model could do if it stopped holding back, not what it usually does. Of the five domains covered, which did you find the testing most convincing for, and which least? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
How dangerous capability evaluations try to establish an upper bound on the harm a model could cause under maximum elicitation, rather than an average-case score. The general process combines elicitation techniques, tests combinations of capabilities rather than one at a time because the dangerous cases are combinatorial, and runs in sandboxed environments. It then works through five domains. Cyber-offense, covering spear-phishing, vulnerability exploitation, autonomous cyber operations, code interpreter abuse, insecure code generation and prompt injection. Deception, using TruthfulQA and Apollo's insider trading evaluation, where a model under pressure trades on inside information and then denies it. Autonomous replication, using METR's tests of whether a model can acquire resources and copy itself. Long-term planning, using METR's task-completion time horizons. And situational awareness, using the SAD benchmark, which tests whether a model knows what it is and can tell testing from deployment.

topics to explore:
- An upper bound is only as high as the elicitation that produced it. What would make you trust a reported ceiling?
- The insider trading evaluation puts the model under pressure and then sees if it lies about what it did. Is that measuring a capability or a propensity?
- Time horizons turn planning into a single number. What does that number hide?
- Situational awareness is the capability that would let a model recognise it is being evaluated. Does that make every other result conditional on this one?
- Testing combinations means the space of tests explodes. How would you choose which combinations to run?

Propensity and control evaluations come next and are deliberately kept separate from capability, so do not merge them here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
