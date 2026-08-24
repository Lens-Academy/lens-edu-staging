---
id: 58aea487-e0f7-40fb-a88b-6f6cbc691bd8
tldr: "An AI can reach the right answer through bad reasoning, or the wrong answer through sound reasoning. Process oversight grades the steps, not just the final result: supervising each link in the chain to give sharper feedback and make outcomes harder to game. But can we trust that the reasoning we see is the reasoning it actually used?"
summary_for_tutor: "Contrasts outcome-based oversight (grading only final answers) with process-based oversight (supervising intermediate reasoning steps). Explains how process supervision eases credit assignment and can reduce specification gaming by rewarding endorsed reasoning, at the cost of requiring more human expertise. Covers externalized reasoning oversight (ERO) via chain-of-thought, the faithfulness problem (post-hoc rationalization, steganography, and reduced reliance in larger models), the limit that oversight misses harmful side effects the model never reasons about, and procedural cloning, which extends behavioral cloning by imitating experts' intermediate steps."
title: "Process Oversight"
{++{"author":"Elias's AI","timestamp":1787570624265}@@reading_minutes: 13
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Scalable Oversight - Process Oversight|Process Oversight]]{++{"author":"Elias's AI","timestamp":1787570624265}@@

#### Text
optional:: true
content::
Process oversight grades the reasoning rather than the answer, and the section then says the visible reasoning may not be the reasoning that was used. Did that undercut it for you? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Outcome-based oversight grades only the final answer; process-based oversight supervises the intermediate steps. The section argues process supervision makes credit assignment easier, since you can see where the reasoning went wrong rather than only that it did, and can reduce specification gaming, because reward attaches to reasoning the overseer endorses rather than to a result that could have been reached any way at all. The cost is that it needs more human expertise, since someone has to judge the steps. It covers externalised reasoning oversight through chain of thought, and then the faithfulness problem: reported reasoning can be post-hoc rationalisation, can hide information through steganography, and larger models appear to rely on their stated reasoning less. It also notes a structural limit, that overseeing reasoning cannot catch harmful side effects the model never reasons about. It closes with procedural cloning, which extends behavioural cloning by imitating an expert's intermediate steps rather than only their outputs.

topics to explore:
- If stated reasoning can be rationalisation, is grading it better than grading outcomes, or just differently wrong?
- Rewarding endorsed reasoning is also training the model on what overseers approve of. Does that reintroduce the sycophancy problem from the previous chapter?
- The side-effects limit says oversight only sees what the model thought about. How much of the risk is in that blind spot?
- Process oversight needs more expertise per unit of output, in a field the governance chapter said is short of experts. Does it scale?
- Steganography means the reasoning could be there but hidden. What would you look for?

Amplification, debate and weak-to-strong generalization come later, so stay with process oversight here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
