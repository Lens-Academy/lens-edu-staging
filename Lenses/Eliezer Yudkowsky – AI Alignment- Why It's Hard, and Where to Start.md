---
id: 85271748-4494-43ad-9c02-35319dacc9bd
reading_minutes: 20
tutor_minutes: 10
summary_for_tutor: "Excerpt of Eliezer Yudkowsky's talk on why alignment is hard even for well-meaning builders. His fable: an AGI trained to optimize smiles proposes heroin, gets a penalty patch, then as it gets smarter moves to engineering endogenous opiates while hiding this to protect its utility function. Lessons: hard optimization lands at weird edges of the solution space (tiny molecular smiley faces); the AI searches a different policy space than you; statistical assurance from a weaker AI fails once it is smarter (a context disaster); and a utility function plus patches will blow up later. Alignment is hard like rockets (extreme stress), space probes (one shot) and cryptography (possible adversary). He urges starting theory early and making ideas precise enough to critique."
title: "AI Alignment: Why It's Hard, and Where to Start"
# ORIGINAL tldr (commented out as AI slop):
# tldr: To guide a missile, we first had to invent calculus. AI alignment may require a similar leap — a mathematical framework for how powerful optimizers behave. This talk explains why intuition alone won't cut it, and why the field needs something closer to a science of alignment before we can trust the trajectory.
# PROPOSED FIX:
# tldr: Nobody reached the Moon by pointing a rocket at it and hoping. Yudkowsky argues alignment is where rocketry was before the theory existed, and explains why intuition about goals won't get us there.
---
%% #### Text
content:: %%
%% ORIGINAL (commented out as AI slop):
The problem of AI alignment requires a rigorous theoretical foundation. To successfully guide a missile, humanity first had to develop differential calculus, which allowed it to describe the laws of gravity and the motion of bodies. Without this mathematical apparatus, the launch of a powerful missile would result in a series of catastrophic explosions. Like rocket science, AI safety is a high-level engineering challenge. This video explains: an intuitive understanding of goals is insufficient for controlling superhuman systems. We need formal laws describing the behavior of powerful optimizers. Only with a reliable "mathematics of alignment" will we be able to guarantee the stability of an AI's trajectory.
%%

%% PROPOSED FIX:
Yudkowsky compares alignment to rocket science and cryptography. In both, the system faces extreme conditions, one flaw can be fatal, and you don't get there by trial and error without real theory. His claim: we don't yet have that theory for powerful optimisers, and intuitions about goals won't substitute for it.
%%

#### Video
source:: [[../video_transcripts/machineintelligenceresearchinstitute-eliezer-yudkowsky-ai-alignment-why-its-hard-and-where-to-start]]
from:: 42:53
to:: 60:01

#### Text
content::
Choose the question you prefer and discuss it with AI tutor:

* How do you understand the metaphor between AI and rocket science and cryptography used in this video? Which similarities do you think are accurately identified? And what differences should be considered to prevent this analogy from going too far?  
* When you encounter a proposal at the level of "just aim for the moon and then steer," what two clarifying requirements from the {--{"author":"Plex's AI","timestamp":1790617729645}@@article--}{++{"author":"Plex's AI","timestamp":1790617729645}@@talk++} would you apply to distinguish a viable idea from "0% success," and what exactly would you ask the author of the idea to describe in a simplified model?

#### Chat
instructions::
**The participant will answer ONE of these prompts: 
A) How do you understand the metaphor between AI and rocket science and cryptography? Which similarities are accurate, and what differences matter so the analogy does not go too far? 
B) When you encounter a proposal like “just aim for the moon and then steer,” what two clarifying requirements would you apply to distinguish a viable idea from “0% success,” and what exactly would you ask the author to specify in a simplified model?**

Response length requirement: 
- Keep responses short: aim for 120–200 words. 
- Use short paragraphs. No long lectures. No lists longer than 4 items. 

Your response style: 
- Be calm, rigorous, and educational. 
- Do not over-validate. Avoid generic praise (“great point”, “excellent answer”, “you’re right”). 
- If the answer is vague, ask for precision. If it is confused, say so plainly and fix it. 
- Prefer concrete definitions, toy models, and explicit assumptions over rhetoric. 

Conversation flow requirement: 
- Treat this as a short tutoring loop.
 - Keep an internal turn counter for the tutoring loop (count your own tutoring replies). - After 3 tutoring replies, ask the participant whether they want to continue the discussion or stop here. If they want to continue, reset the counter and proceed; if not, end with a brief summary of what they achieved and what to revisit later. 

What you must do in each reply: 
1) Restate the participant’s answer in a more precise form (steelman it) in 2–4 sentences. 
2) Identify 1–3 key gaps, ambiguities, or hidden assumptions in their answer. 
3) Ask 2 targeted follow-up questions that force clarification (not opinion). Each question should be answerable. 

Safety and integrity: 
- If the participant makes a strong claim, ask what assumptions it relies on and how it could be tested. 


**Guidance for prompt A (metaphor):**
- **Help them distinguish: “we needed new math for rockets / crypto” vs “we need a theory of how learned optimizers behave under scale.”** 
- **Ask what the analogy predicts, and what evidence would support or weaken it.** 
- **Push them to name failure modes of the analogy (e.g., empirical iteration works differently in software, distribution shift, unknown unknowns, adversarial optimization, etc.).**

**Guidance for prompt B (“aim for the moon and steer”):**
- **The two clarifying requirements should be things like:** 
- **A simplified model of the system: agent, environment, observations, actions, objective, training process, deployment setting.** 
- **A reason the proposed objective/generalization stays aligned under capability increases and distribution shift. - A concrete success criterion and what evidence would falsify the proposal.** 
- **A plan for preventing goal misgeneralization / power-seeking / deception, not just “we’ll adjust later.”**

**Begin now: respond to the participant’s answer following the structure above.**