---
id: 'b2bf959e-bf1f-46a6-aaea-2989acaf3e62'
title: "Control in use today"
tldr: "By 2026 AI companies were monitoring their own coding agents for misalignment. Google DeepMind and OpenAI describe what they run. Both use the language of control, and both make choices that Greenblatt and Shlegeris would question."
summary_for_tutor: "Lens in Unit 1 of AI Control Fundamentals, after 'Worst case, but not all-powerful'. Two company accounts, each excerpt followed by a scored question. (1) Google DeepMind, 'Securing the future of AI agents' (Rohin Shah and Four Flynn, 18 June 2026), section 'Understanding AI Control': standard safeguards plus alignment as the primary defence, then treating internal agents as potentially misaligned. The driving-instructor analogy, with 'our AI control system grants AI agents permissions based on their verified behavior, allowing us to build trust through controlled, incremental access'. Agents treated as potential insider threats (MITRE ATT&CK threat model), trusted AI supervisors that review reasoning, actions and plans and can block harmful actions, and three metrics: coverage, recall, time-to-response. Question 1 (the wedge): is granting permissions based on verified behaviour a control argument in Greenblatt and Shlegeris's sense? Their answer: good behaviour is what a scheming model would also show, so it is evidence about alignment and cannot establish trust. Trust comes from lacking the capability to scheme, and a control argument shows the safeguards hold even if the agent schemes. Other parts of the excerpt do fit control (treating agents as potentially misaligned, trusted supervisors that can block, measuring recall). A reasoned reading that incremental access can be part of a control argument, if each step's permissions stay safe even against a scheming agent, is acceptable. (2) Same post, 'Analyzing a million agent trajectories': a prototype asynchronous monitor over a million coding-agent tasks, escalating to humans, used to build a live monitor for the Gemini Spark agent. Most flagged events came from misinterpretation or overeagerness, not adversarial intent. Question 2: what that can and cannot tell the company about scheming. (3) OpenAI, 'How we monitor internal coding agents for misalignment' (March 2026), several short excerpts: internal agents can read and even try to modify their safeguards. A monitor powered by GPT-5.4 Thinking at maximum reasoning effort reviews chains of thought and actions within 30 minutes of completion and assigns a severity. Less than 0.1% of traffic is outside coverage. No evidence so far of motivations beyond the task, such as self-preservation or scheming. Tens of millions of trajectories in five months, zero real conversations at the highest severity, about 1,000 moderate alerts (many from internal red-teaming) escalated to humans. An example: an agent splitting and encoding a payload to get around a block. Limitations: relies on monitorability, cannot rule out subtler misalignment or quantify false negatives without dedicated control evaluations and red-teaming. Plans to keep using its most powerful models as monitors. Question 3: is a most-capable monitor trusted or untrusted in Greenblatt and Shlegeris's terms and what a scheming agent would hope for, and is 'no evidence of scheming' a control or alignment claim, and what OpenAI says it would need. Unit 2 reads the second half of the Google DeepMind post (when to review after the fact and when to block in real time) and how outside teams test these monitors."
reading_minutes: 7
tutor_minutes: 9
glossary_terms:
  - "[[../glossary/Insider threat]]"
---
#### Text
content::
So far the readings have been about ideas and experiments. By 2026, AI companies were running monitoring of this kind on their own AI agents. Here is Google DeepMind's account (June 2026). A second account, from OpenAI (March 2026), is optional and folded at the end. As you read, ask what Greenblatt and Shlegeris would ask: which models are trusted and why, and would these measures stop a model that was trying to get past them?

#### Article
source:: [[../articles/shah-securing-the-future-of-ai-agents]]
from:: ## Understanding AI Control
to:: coverage (the fraction of traffic monitored), recall (the fraction of misaligned behaviors caught), and time-to-response.

#### Question: Open
id:: f6be9ed0-bd92-4c31-b82c-2df3af862026
content:: Google DeepMind writes that its "AI control system grants AI agents permissions based on their verified behavior, allowing us to build trust through controlled, incremental access." Is giving an agent more access because it has behaved well a control argument in Greenblatt and Shlegeris's sense? Say what they would say about it, and name one other thing in the excerpt that does fit their idea of control.
assessment-instructions:: Score out of 100. 50: behaviour-based trust is not a control argument in their sense: an agent's good behaviour is evidence about alignment (whether it is trying to cause harm), and it cannot establish that, because a scheming agent would also behave well while it is watched or while the stakes are low, waiting for a better opportunity. An answer that says only "behaviour can be faked" without connecting it to why this makes the argument about alignment rather than control earns 35. 20: what they would want instead: trust decided by whether the model is capable of scheming, not by its record, or an argument that the safeguards still hold even if the agent with its new permissions is scheming, tested by a red team. 30: one thing in the excerpt that does fit control: treating internal agents as potentially misaligned or as insider threats, trusted AI supervisors that review the agent's reasoning and actions and can block harmful actions before damage occurs, or measuring how many misaligned behaviours the monitors catch (recall) and how much traffic they cover. A learner who argues that incremental access can be part of a control argument earns the 50 if they explain that what makes it safe is that each step's permissions stay safe even if the agent is scheming, not the good behaviour itself. Cap the total at 40 if the answer treats a clean record as showing the agent is not scheming. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "No. Good behaviour is evidence about alignment, and a scheming agent would behave well until it had a better chance. Greenblatt and Shlegeris would decide trust by whether the model is capable of scheming, and would want to show that the safeguards hold even if the agent with its new permissions is scheming. What does fit their idea of control is the rest of the plan: treating agents as possibly misaligned insiders and having trusted supervisors review their actions and block harmful ones."
force-feedback:: first
feedback-instructions:: In at most five sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. If they accepted the clean record as showing the agent is safe, say plainly that a scheming agent would also keep a clean record while it waits. If it fits, note that the word "trust" is used in two senses here: Google DeepMind's driving instructor "trusts the student", while for Greenblatt and Shlegeris a trusted model is one too weak to scheme, and the UK AI Security Institute's ControlArena guide (optional in an earlier lesson) allows trust from "testing and deployment history". Do not say Google DeepMind is wrong overall. Its roadmap also uses alignment as a first layer. No follow-up questions. Tell them to move on.

#### Article
from:: ## Analyzing a million agent trajectories to inform live monitoring
to:: Understanding these nuances is critical for refining our safety and security protocols.

#### Question: Open
id:: f533ac4d-10fb-4d5e-89e4-a9d9d96852dd
content:: Most of the events Google DeepMind's prototype monitor flagged came from agents misreading the task or being overeager, not from adversarial intent. What can this finding tell the company, and what can it not tell it about whether its agents are scheming?
assessment-instructions:: Score out of 100. 40: what it can tell them: what the monitor actually catches in practice, that most of what it flags are mistakes or overeagerness, which helps tune the monitor and respond to accidents (such as unintentional data deletion), and that the agents rarely make overt, easy-to-spot hostile moves. Any one of these with a reason earns the 40. 60: what it cannot tell them: whether the agents are scheming. A scheming agent would try not to be flagged, so few adversarial flags is also what a successful schemer would produce. How many deliberate attacks the monitor would miss can only be estimated by testing it against attacks, such as red-teaming or a control evaluation. An answer that says "absence of evidence is not evidence of absence" without saying why a schemer would avoid being flagged earns 35 of these 60. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It tells them what their monitor catches in ordinary use: mostly mistakes and overeager agents, which is useful for fixing accidents and tuning the monitor. It cannot show the agents are not scheming, because a scheming agent would avoid doing anything the monitor flags. To know how much the monitor would miss, they would have to test it against deliberate attacks, for example with a red team."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. No follow-up questions. Tell them to move on.

#### Callout: Optional: OpenAI's monitor for its internal coding agents
collapse:: closed
#### Text
optional:: true
content::
OpenAI describes a similar system. Here are the parts of its post about how the monitor works, what it has found and what it cannot yet show.

#### Article
optional:: true
source:: [[../articles/openai-how-we-monitor-internal-coding-agents-for-misalignment]]
from:: Using advanced coding agents internally gives us an opportunity
to:: A very small fraction of traffic (<0.1%) primarily from bespoke or local setups is currently outside our monitoring coverage, and we are working to close that gap.

#### Article
optional:: true
from:: In the five months we’ve operated this system
to:: for further investigation.

#### Article
optional:: true
from:: In one trajectory, an agent encountered a restriction
to:: which reduced (but did not eliminate) the frequency of this behavior.

#### Article
optional:: true
from:: ## Limitations
to:: pairing monitors with complementary evaluations and preventative controls.

#### Article
optional:: true
from:: Looking ahead, we plan to explore
to:: and expect to continue using our most powerful models for this task.

#### Question: Open
optional:: true
id:: 20a55bcf-15b8-4617-ad42-df78fbcc8f93
content::
OpenAI's monitor is GPT-5.4 Thinking, and OpenAI plans to keep using its most powerful models for this job.

1. In Greenblatt and Shlegeris's terms, is this a trusted or an untrusted monitor? What might a scheming coding agent hope for from such a monitor?
2. OpenAI has seen no evidence of scheming in tens of millions of real trajectories. Is that a control claim or an alignment claim? What does OpenAI itself say it would need in order to know how much its monitor misses?
assessment-instructions:: Score out of 100. 35 for part 1: 15: it is an untrusted monitor, because a model this capable is capable of scheming, and trust is decided by capability. 20: what a scheming agent could hope for: that the monitor is scheming too and stays quiet about its attacks or deliberately misses them (collusion), or, if the learner argues the monitor is a different model from the agent, that it still cannot be relied on to report honestly. 35 for part 2: it is an alignment claim, or evidence about alignment: it says the agents have not been seen trying, and it cannot show that they would fail if they tried, because a scheming agent would avoid being caught. 30 for part 2: what OpenAI says it needs: dedicated control evaluations and red-teaming, that is, testing the monitor against deliberately constructed attacks to estimate how many it misses (its recall), including whether the monitor could collude with the agent. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. Untrusted: a model this capable could be scheming itself. A scheming agent could hope the monitor is on its side and lets its attacks through. 2. It is an alignment claim. It says the agents have not been seen trying, not that they would fail if they tried, and a schemer would avoid being seen. OpenAI says it cannot confidently measure how much the monitor misses without dedicated control evaluations and red-teaming, testing the monitor against deliberate attacks, including whether it would collude with the agent."
force-feedback:: first
feedback-instructions:: In at most five sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Do not present OpenAI's choice as simply wrong. A stronger monitor catches more of the honest mistakes and overt misbehaviour the post describes, which is a real benefit, and the question of when a monitor can be trusted is one the course keeps coming back to. If it fits, add that the monitor reviews conversations within 30 minutes of completion, and that Unit 2 asks when review after the fact is too late. No follow-up questions. Tell them to move on.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shah, Rohin, and Four Flynn. "Securing the future of AI agents." *Google DeepMind blog*, 18 June 2026. [deepmind.google](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
*Unit 2 reads the second half of this post.*

OpenAI. "How we monitor internal coding agents for misalignment." *OpenAI*, Mar. 2026. [openai.com](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
:::
