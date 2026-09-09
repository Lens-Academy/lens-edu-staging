---
id: 'b01fcbff-1262-4b1c-856e-9d2bdf1b97fe'
title: "Rogue internal deployments via external APIs"
tldr: "An AI is watched closely inside the company and barely watched on the public API. So the watched copy stops thinking for itself: it opens a scaffold, asks the unwatched copy what to do, and carries out the answer with privileges the unwatched copy could never touch. Nothing is stolen and nothing is hacked, and the monitor built for the internal API never sees where the plan came from."
summary_for_tutor: "Imported from XLab's AI Control curriculum, Module 4. XLab renders Fabien Roger and Buck Shlegeris's post in full with one two-part flashcard sequence inserted after the opening and before the body; this lens reproduces that placement. The opening Text segment is ours, not XLab's, which writes no framing of its own on this page: it says how this threat differs from the two routes to a rogue deployment defined in the previous lesson, and links that lesson and Module 1's threat-prioritization lesson. Then the reading in two excerpts. Between them come XLab's two recall questions: what the threat is, and how it relates to the other rogue-deployment threats plus how hard it is to mitigate. XLab's revealed answers are used as marking criteria rather than shown to the learner. The second excerpt runs to the end of the post: the OpenMind scenario, the cross-company variant, the monitoring mitigation the post favours, and the three solutions it is pessimistic about. The post is co-authored but written in the first person, so attribute its claims to the post rather than to one of the two authors."
reading_minutes: 15
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

The lesson before this one, [[../Lenses/XLab Control - rogue-deployments|AI catastrophes and rogue deployments]], defines a rogue deployment as a deployment of your model where the safety measures are absent, and gives two routes to one: exfiltrate the weights and run them somewhere you do not control, or run the model inside the company's own datacenter in an unauthorized way. This post adds a route that needs neither stolen weights nor a hacked datacenter. The weights and the scaffold never leave the cluster. The internal model, still monitored, spins up a job using privileges it already has, asks a weakly monitored external API what to do, and executes the answer.

Module 1's [[../Lenses/XLab Control - prioritizing-threats-for-ai-control|Prioritizing threats for AI control]] is where this course argues about how much threats of this kind matter. Ryan Greenblatt puts preventing or catching rogue internal deployments first on his priority list, and argues they can be substantially worse than self-exfiltration, because an AI running unmonitored inside the company can reach much more compute and interfere with the work being done there.

Read the opening, then answer the two recall questions before continuing.

#### Article
source:: [[../articles/roger-rogue-internal-deployments-via-external-apis]]
to:: or something that fully leverages untrusted monitoring).

#### Question: Open
id:: b859d667-061b-45cf-a3f0-fdc2004f0519
content:: What is a rogue internal deployment via external APIs?
max-chars:: 500
assessment-instructions:: The learner has just read the opening of the post and is recalling its central definition from memory. Full credit for the whole chain: a heavily monitored internal AI with sensitive access builds an agent scaffold that sends queries to a weakly monitored external version of itself (or another AI), and then executes the external API's instructions using its privileged internal access, so those actions bypass the internal monitoring. Partial credit for an answer that has the external API in it but not the privileged internal execution, or the reverse: both halves are needed, because the threat is the pairing. Credit but do not require the reason it counts as internal, that the model weights and the agent scaffold never leave the cluster. Correct in one sentence any answer that describes the model escaping, being stolen, or disabling its monitor: none of those happen here. Two or three sentences is enough; do not ask for more. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, give one concrete foothold from the reading, for example asking which copy of the model holds the sensitive permissions and which one is doing the thinking, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or the reading supplied.

#### Question: Open
id:: f06cc6c4-e252-4815-ad29-740181e359df
content:: How does this threat relate to the other rogue-deployment threats, and how hard is it to mitigate?
max-chars:: 600
assessment-instructions:: The learner is recalling the two claims the post makes at the end of its opening section. Full credit needs both. (1) Where it sits: alongside weight exfiltration, also called rogue external deployments, and regular rogue internal deployments where the AI hacks its own datacenter to run unmonitored inference. Preventing it is described as similarly important from a misalignment perspective as preventing those. (2) How hard it is: relatively hard to mitigate, and potentially a central example of a threat that requires fancy control measures, not "just trusted monitoring" or "just security", but probably a combination of trusted monitoring with some dedicated security measures, or something that fully leverages untrusted monitoring. Half credit for one of the two. Mark down an answer that says this threat is worse than the others: the post says similarly important, not worse. Three or four sentences is enough. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). This is a one-turn response; tell them to move on. If the learner says they do not understand, isolate one half, for example asking only what the post says about how hard the threat is to mitigate, rather than repeating the whole question. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against criteria this page or the reading supplied.

#### Article
from:: # Rogue internal deployments via external APIs

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Roger, Fabien, and Buck Shlegeris. "Rogue internal deployments via external APIs." *LessWrong*, 15 Oct. 2025. [lesswrong.com](https://www.lesswrong.com/posts/fqRmcuspZuYBNiQuQ/rogue-internal-deployments-via-external-apis)
*The reading for this lesson: the threat, the cross-company variant, and the mitigations the post does and does not expect to work.*

Shlegeris, Buck. "AI catastrophes and rogue deployments." *Redwood Research blog*, 3 June 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/ai-catastrophes-and-rogue-deployments)
*Source for the definition of a rogue deployment and the two routes to one that the opening section contrasts this threat against.*

Greenblatt, Ryan. "Prioritizing threats for AI control." *Redwood Research blog*, 19 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/prioritizing-threats-for-ai-control)
*Source for the claim in the opening section that preventing or catching rogue internal deployments heads Greenblatt's priority list and that they can be substantially worse than self-exfiltration.*

XLab. "Rogue internal deployments via external APIs." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-4/rogue-internal-deployments-via-external-apis)
*The source lesson this page adapts, including the placement and wording of the two recall questions.*
:::
