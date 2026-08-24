---
id: bd9196d1-c7fc-421d-8886-f9e0201a85ae
tldr: "If we build AI as smart as us, what actually keeps it safe? This section first debunks the intuitive fixes everyone reaches for (Asimov's laws, raising it like a child, no robot body, just turn it off), then lays out the real strategies: solve alignment, iteratively catch and fix misalignment, keep the AI boxed and controlled, and read its thoughts through the chain of thought."
summary_for_tutor: "Surveys safety strategies for human-level AGI (as distinct from superintelligence). Opens by explaining why four intuitive approaches fail: explicit rules (Asimov's laws), raising AI like a child, withholding physical embodiment, and using an off switch. Then examines four substantive strategies: solving AGI alignment (requirements of robustness, scalability, feasibility, and low alignment tax, plus sub-goals of specification, scalable oversight, generalization, and interpretability); iteratively fixing misalignment through detection-and-correction loops, with counter-arguments about dangerous capabilities, non-generalizing alignment, and broken feedback loops; maintaining control via boxing, monitoring, and control evaluations even without alignment; and transparent thoughts via chain-of-thought monitoring, including its unfaithfulness and the 'most forbidden technique' of training on interpretability. Also discusses the misuse-versus-misalignment distinction and AI-enabled coups."
{++{"author":"Elias's AI","timestamp":1787567927952}@@reading_minutes: 33
tutor_minutes: 7
++}title: "AGI Safety Strategies"
---

#### Article
source:: [[../articles/AI Safety Atlas - Strategies - AGI Safety Strategies|AGI Safety Strategies]]{++{"author":"Elias's AI","timestamp":1787567941261}@@

#### Text
optional:: true
content::
Catching and fixing misalignment as you go only works if you get more than one attempt, and the section calls it a strategic gamble in its own words. Would you take that bet? Talk it through with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Safety strategies for human-level AGI, where the section assumes we can still oversee systems and iterate, unlike the ASI case. It opens by dismissing four intuitive fixes: explicit rules such as Asimov's laws, which cannot cover every situation; raising the system like a child, which assumes it develops human moral intuitions; withholding a physical body, which ignores the harm a purely digital system can do; and just turning it off, which fails if the system is embedded or can replicate. It then covers four real strategies. Solving alignment, where even the requirements are contested and current techniques fall well short. Fixing misalignment iteratively through detection-and-correction loops, which the section presents as a live disagreement and calls a strategic gamble, with three counter-arguments: it means deliberately training dangerous systems, alignment may not generalise while capabilities do, and the feedback loop may break under a fast takeoff. Maintaining control through boxing, monitoring and control evaluations, which it says is probably not scalable but is doable and complementary to alignment, noting that evaluating capability is easier than evaluating propensity. And transparent thoughts, monitoring chain of thought, where it presents evidence that reported reasoning is often unfaithful and that some architectures remove the possibility entirely.

topics to explore:
- The iterative strategy assumes problems stay discoverable and fixable. Which of the three counter-arguments would sink it first?
- Some researchers put more than a 50 percent chance on straightforward approaches working. What are they seeing that critics are not?
- Control is described as unscalable but useful now. Does a strategy with a known expiry date deserve the effort?
- Chain of thought monitoring is unfaithful in the cases studied. Does that make it useless, or useless only where reasoning was shallow anyway?
- Four intuitive fixes get dismissed early. Was any of them dismissed too fast?

The misuse-versus-misalignment comparison, AI-enabled coups, whether control research reduces risk, how to box an AI, and training on interpretability all sit in collapsed optional callouts. Do not assume the learner has read them.

ASI strategies come next and are deliberately kept separate, so do not bring in superintelligence-specific proposals here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
