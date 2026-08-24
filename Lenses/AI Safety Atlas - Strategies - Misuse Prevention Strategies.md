---
id: d53e1458-a4a7-450b-b4ce-8bc7c60211f6
tldr: "If a powerful AI model can be downloaded by anyone, how do you stop it being weaponized? This section walks the gradient from fully closed to fully open release, showing how API gateways, filtering, rate limits, and monitoring try to keep dangerous capabilities in check, and where laws and norms have to take over."
summary_for_tutor: "Covers strategies for preventing AI misuse by controlling access to dangerous capabilities. Explains the access gradient from fully closed to fully open-source, positions API-based deployment as a common middle ground, and details its safety mechanisms - input/output filtering, rate limiting, usage monitoring, usage restrictions, and on-the-fly updates. Also frames misuse prevention as requiring legal and social measures to manage harms from already widely available models."
{++{"author":"Elias's AI","timestamp":1787567846556}@@reading_minutes: 35
tutor_minutes: 7
++}title: "Misuse Prevention Strategies"
---

#### Article
source:: [[../articles/AI Safety Atlas - Strategies - Misuse Prevention Strategies|Misuse Prevention Strategies]]{++{"author":"Elias's AI","timestamp":1787567859481}@@

#### Text
optional:: true
content::
The section's preferred middle ground, API access, also hands a few companies the power to decide who may use what. It says so itself, and keeps the strategy anyway. Do you accept that trade? Put it to the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Preventing misuse by controlling access to dangerous capabilities. The industry has moved past release or do-not-release to a continuous gradient from fully closed to fully open weights, with API deployment as the common middle ground: code, weights and data stay closed while capabilities are reachable through a gateway. That gateway allows input and output filtering, rate limiting, usage monitoring including identity checks, usage restrictions backed by terms of service, and on-the-fly safety updates that open weights cannot receive. The section then concedes the cost: when developers hold exclusive control they unilaterally decide acceptable uses and who gets access, so restricting access concentrates power and needs other strategies to counterbalance. It quotes Ajeya Cotra arguing that systems too dangerous to open source are probably too dangerous to train at all. Deciding which models are dangerous comes first, via evaluations and red teaming. Internal access controls protect the weights themselves, since exfiltration makes every external control irrelevant. Technical safeguards include circuit breakers and machine unlearning. It closes on models already widely available, where it says there is no purely technical fix and the answer is laws, content moderation, watermarking, education and research.

topics to explore:
- Restricting access concentrates power, and the section says so plainly. What would have to be true for that to be the wrong trade?
- Cotra's claim is stronger than the section's own position. If it is right, what happens to the whole access-gradient framing?
- Evaluations decide which models are dangerous, so the access strategy inherits whatever the evaluations miss. How much weight can they carry?
- The section says there is no technical solution for models already released. Does that make the legal and normative measures a fallback, or the main event?
- Internal controls protect weights, external controls protect use. Which failure would be worse, and which is the field better at?

Several parts sit in collapsed optional callouts, including the open-versus-closed arguments, the security levels, self-exfiltration, AI-enabled human takeover, and tamper-resistant safeguards. Do not assume the learner has read them.

The evaluations and red teaming material gets a full chapter later, so point at it rather than teaching it here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}
