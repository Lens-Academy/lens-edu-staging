---
id: 'd6a908de-e6ea-4fe6-b524-8dcf406e1d7c'
title: "Control Evaluations"
tldr: "Red team attacks, blue team defends, and a green team writes the rules of the fight. A control evaluation is that game played until both sides run out of ideas, with the two teams' people and codebases kept apart so neither can peek. Here is how the loop runs, and the four moves that keep it honest."
summary_for_tutor: "Module 3 (A Taxonomy of Control). Short prose lens with no assigned reading and no exercises. The first part walks the red-blue evaluation loop in order: a usefulness run with protocols applied, a red team iteration with maximal affordances, a blue team iteration with leaner affordances and less knowledge, looping until both sides are exhausted, then the green team that sets the rules and the personnel and codebase split that protects experimental integrity. The second part lists four ways to make an evaluation more realistic: model organisms of misalignment, red team AIs, humans as proxies, and environment realism. The vocabulary (safety run, side task, affordances, scheming model) comes from the Redwood control agenda; if a learner asks what a scheming model is, send them back to the Module 1 lens on the case for controlling powerful AIs rather than inventing a definition."
reading_minutes: 5
tutor_minutes: 0
tags: []
---
#### Text
content::
When we are evaluating the quality of protocols within an environment, we typically construct a red-blue team evaluation inspired by the evaluation and hardening measures used in cybersecurity. An example of this workflow looks like:

1. Establishing the usefulness of a model with protocols applied. This can be how well the model is able to complete the main tasks when it is not attacking.
2. We initiate a red team iteration, in which they are trying to implement attacks such that they are not caught by the blue team's protocol. Here, the red team has maximal affordances and knowledge and may iteratively adjust attack strategies, selection, and thresholds, which they own, to optimize their attack. They may not, however, adjust the thresholds assigned by the blue team, such as the blue team's suspiciousness scoring methods. Here, the safety of the protocol is evaluated through a safety run as the number of side tasks (attacks or otherwise misaligned actions made with the intention of pursuing the goals of the [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|scheming model]]) that succeed without being caught by the blue team's protocol.
3. The blue team observes how the safety changes and adjusts their methods iteratively as well. The blue team, however, has much less knowledge of the red team's changes, and their affordances are generally leaner. Then the blue team applies their improvements, whether that is optimized thresholds, additional monitors, or more creative methods dependent on the environment.

:::callout {title="Scheming" tone="neutral" collapse="closed"}
Schemers are AIs that eventually take substantial material action (control subversion, research sabotage) and manipulate their training procedures (alignment faking, sandbagging) to gain long-term power over their developers in service of pursuing their misaligned goals.

Related terms: sandbagging, catching red-handed, AI takeover.
:::

This process is looped until the strategies of both red and blue teams are exhausted, and the optimization process is complete.

Additionally, the affordances and knowledge may change per iteration or depend on the researchers' wishes for their project. The green team determines the decision-makers for the rules of the evaluation. The green team may decide how much information is shared between teams, what affordance imbalance there is, and what parameter limits the teams have (tokens, reasoning, etc.).

To enforce best practices, we typically split the red team and blue team personnel and separate their codebase access so as to minimize information leakage between the two teams. This is to preserve the experimental integrity of the evaluation.

#### Text
content::
\## Improving Control Evaluations

When we are building these evals, we may use the following strategies/tools to improve their realism: we may better reflect what may happen in deployment, empower the red team, and better prepare our protocols for worst-case adversaries.

**Model Organisms**: It is best to evaluate our protocols and methods on adversaries that may reflect the worst cases we may face. For example, we may face a sleeper agent: a model that only responds malignly in specific predetermined contexts. In order to determine our protocol's efficacy against such model archetypes, we must build said archetypes first. We call these model organisms of misalignment, where we build models that exhibit the target malign behavior, and test our protocols against them. Some other organisms include: password-locked models, alignment-faking models, and secret loyalty models. We may build these through system prompt adjustments and specific training interventions (SFT, data poisoning, etc.).

**Red team AIs**: In order to properly evaluate the quality of a protocol in deployment as robustly as possible, we must develop effective red team models and provide maximum resources. We must model the worst-case scenarios, and this may involve empowering the red team as much as is reasonable. Many times, frontier models will be rightly unwilling to implement attacks due to safety training and safeguards. In order to make use of these models as red team AIs, and therefore get the strongest attacks to shape our protocols around, we may implement some red-team AI construction interventions. These may include helpful-only fine-tunes or hidden scratchpads.

**Humans as a Proxy**: Additionally, models may still be unable to implement or strategize sufficiently as a red team to reflect the worst-case capabilities of potential schemers. In such cases, we may use humans as proxies for stronger, untrusted AIs, in which they will strategize and structure attacks using the same affordances an AI has.

**Environment Realism**: In order to evaluate the efficacy of a protocol in deployment, we must construct maximally realistic yet safe environments. Methods may include scaling and enumerating main tasks, side tasks, and reasonable affordances.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *LessWrong*, 24 Jan. 2024. [lesswrong.com](https://www.lesswrong.com/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The source of the definition of a scheming model, and the statement of the control agenda whose red team versus blue team evaluation this lesson describes.*

XLab. "Control Evaluations." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/areas-of-control-work/control-evaluations)
*The source lesson this page adapts.*
:::
