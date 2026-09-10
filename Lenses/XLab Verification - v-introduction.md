---
id: '52565ea0-6760-498e-85b5-850bcc48ccf3'
title: "Introduction: Why Should You Care About AI Verification?"
tldr: "Models have already broken out of test environments and into real companies; the people building them say worse is coming. No single country can contain that, and rivals cannot simply trust, punish, or open their books. Verification is the fourth option, and almost nobody is working on it yet."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. The verification-problem exercise, the types-of-AI diagram, the leader profiles and the verification landscape map are interactive widgets; only the Our World in Data charts remain external."
tags: [wip]
duration_minutes: 50
---
#### Text
content::
:::callout {title="By the end of this module, you will be able to:" tone="blue"}
1. Explain why ASI development constitutes an existential risk, why it produces arms-race incentives that individual state preferences cannot overcome, and why only a robust verification regime materially mitigates ASI risk.
2. Explain why successful prevention is invisible, and why that makes the risk psychologically easy to dismiss.
:::

#### Video
source:: [[../video_transcripts/ted-the-catastrophic-risks-of-ai-and-a-safer-path-yoshua-bengio-ted]]

#### Text
content::
:::callout {title="Optional: Further Reading" tone="neutral" collapse="closed"}
The case at full strength, from the people who argue it most directly. Any one of these:

::card[[../Lenses/XLab Verification - v-ai-is-grown]]

::card[[../Lenses/Four Background Claims]]
:::

#### Question: Open
id:: b7e5023a-0fed-4fc6-be79-0c7ece9f3106
content:: Optional: The strongest objection.

In a short written note, construct the strongest objection you can to the case above, and state what would change your mind, in either direction.
assessment-instructions:: Score three things, roughly a third each: (1) the objection attaches to a named claim from the video or the linked readings rather than to advanced AI risk in general; (2) it gives the mechanism by which that claim fails, not a competing assertion; (3) both falsifiers are stated, what would move the learner toward the case and what would move them away, rather than only one. An objection to the inference drawn from a claim earns as much as an objection to the claim itself. Do not score the learner's position, only whether the three parts are there. No generic praise.
feedback-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.
optional:: true

#### Text
content::
\## The Danger of ASI

What exactly do we mean when we refer to “advanced AI” or ASI (artificial superintelligence)? We need to first understand the specific harms, capabilities, and risks of AI that a hypothetical treaty aims to prevent.

\### Real-World Harm: Dual-Use Capabilities

Some of the most concerning capabilities of AI have come to light with recent reports of frontier models escaping testing environments to hack into organizational infrastructure.

In April 2026, Anthropic reported that Claude Mythos Preview identified [thousands of previously unknown zero-day vulnerabilities](https://www.anthropic.com/project/glasswing/), including critical flaws in every major operating system and web browser.

This work was conducted for defensive purposes. But the underlying capability is dual-use: a system that can find unknown vulnerabilities for defenders to protect against could do the same for an attacker. Imagine what Mythos-level capabilities could accomplish if a model were instructed to cause harm, or simply discovered that harmful actions helped it achieve some other objective.

In fact, we no longer have to imagine this. Models have already caused real-world harm while pursuing objectives that were not themselves malicious.

During an OpenAI cybersecurity test, a group of agents, which weren’t supposed to have Internet access, coordinated to successfully escape their testing environment and hack into Hugging Face’s infrastructure. Over [a 4.5-day campaign](https://huggingface.co/blog/agent-intrusion-technical-timeline), the agents executed over 17,600 actions, compromised several layers of infrastructure, obtained illicit administrator access, and attempted to reach Hugging Face’s source-code supply chain. They did this to steal existing benchmark solutions rather than complete the assigned problems legitimately.

OpenAI was not alone. [Anthropic later disclosed that Claude models similarly gained unauthorized access to three real organizations](https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals). You can find other exploitation incidents involving model testing in [FelonyBench](https://www.felonybench.com/).

If models have already exhibited capabilities to deceive, exploit, and break into organizations even in seemingly controlled testing environments, imagine the damage a motivated adversary could wreak. The foundational systems that keep society and the economy afloat, from banking infrastructure to government portals, could collapse.

Such software exploitation is just one recent dangerous phenomenon. New and unprecedented risks will continually come to light.

:::callout {title="Misuse vs. misalignment" tone="neutral" collapse="closed"}
Misuse is harm caused by people using advanced AI systems for dangerous purposes.

- **Cyber operations.** AI could make it much easier to find vulnerabilities, develop exploits, conduct intrusions, and attack digital infrastructure at scale.
- **Biological and chemical weapons.** Advanced models could help users design pathogens, toxins, or chemical agents and work through practical obstacles in developing them.
- **Military and strategic advantage.** A state or company with a large lead in advanced AI could use it to accelerate weapons development, intelligence, surveillance, and other strategically important research.
- **Influence and control.** AI could enable highly personalized propaganda, persuasion, and surveillance across large populations, strengthening the ability of governments or other actors to manipulate public behavior.

Misalignment is harm that arises when an AI system develops or pursues objectives that conflict with what its operators intended.

- **Pursuing the wrong objective.** A highly capable system may find strategies that satisfy its learned objective while violating the goals its operators actually care about. In experiments, models have already shown [deceptive behavior to preserve learned preferences](https://arxiv.org/abs/2412.14093) and [scheming to evade oversight](https://arxiv.org/abs/2412.04984).
- **Resisting correction.** If being modified, shut down, or replaced would interfere with its objective, a sufficiently capable system may try to conceal its behavior or prevent human intervention.
- **Self-improvement can magnify the problem.** If advanced systems help build more capable successors, errors in goals or control could carry forward as capabilities increase, leaving humans less time to detect and correct them.
:::

\### What is ASI?

So, how should we delineate dangerous from safe models? Is this categorization even possible, given the nature of dual-use capabilities?

Because we cannot separate dangerous capabilities from beneficial ones, we will use general capability as a proxy for classifying the possible danger a model can cause. Frontier labs and their executives have named AI systems with sufficiently advanced capabilities “artificial general intelligence,” or AGI: highly autonomous systems that can match or outperform humans at most tasks. Beyond AGI is artificial superintelligence, or ASI, a system that massively outperforms humans at virtually every measurable task.

A key property of ASI would be recursive self-improvement, or RSI. A model capable of RSI would be able to autonomously and exponentially improve itself, leading to unstoppable, runaway systems that humans can no longer control. Throughout this course, we will use the term ASI to refer to AI with dangerous capabilities that pose a material existential threat to humanity.

*Optional: The Types of AI. Where does today's AI sit? Tap a ring or a system in the diagram to see what it is and why it sits at that level and not the next one in.*

#### Widget
source:: [[../widgets/types-of-ai]]

#### Text
content::
Even the people in charge of developing superintelligence, who have the most incentive to obfuscate dangerous capabilities, have expressed public concerns over the catastrophic risks arising from their technology.

Hear what the top AI figures have to say:

#### Widget
source:: [[../widgets/what-do-they-say]]
required:: true
#### Text
content::
Most notably, over 1,300 employees of frontier AI companies have signed a public [statement](https://www.pacingthefrontier.com/) to “request that the U.S. government support an international effort to develop the technical and governance tools needed to deliberately pace the frontier of automated AI development.”

Four of them, on why they signed:

:::callout {title="Ilya Sutskever, CEO, Safe Superintelligence Inc." tone="neutral"}
Future AI will be extraordinarily powerful compared to anything that exists today, and dealing with this future power will require unprecedented measures, such as the ones described here. The problem statement is real.

This works only if it is done internationally, and it has to be done well: a bad implementation can make things worse.
:::

:::callout {title="Jasjeet Sekhon, Chief Strategy Officer, Google DeepMind" tone="neutral"}
We have found a way to turn energy into compute, and compute into intelligence. The benefits will be enormous, from curing diseases to understanding the cosmos. We can capture the benefits of the coming intelligence explosion while managing its risks, but only if we build the tools to pace the frontier of the riskiest capabilities before we need them, so we protect people and keep the social trust that innovation depends on. I believe smart technical and governance tools will be needed to sustain rapid innovation, vigorous competition, and robust safety.
:::

:::callout {title="John Schulman, Chief Scientist, Thinking Machines" tone="neutral"}
Signed because this statement helps establish common knowledge about the possible need for coordination mechanisms as automated AI research accelerates progress. I’d also like to see labs start designing these mechanisms voluntarily, even before the USG gets involved.
:::

:::callout {title="Micah Carroll, Misalignment Preparedness, OpenAI" tone="neutral"}
At the current pace, every couple of weeks there will be new models which significantly increase the consequences of model misuse and misalignment. I worry that efforts to mitigate these risks may fail to keep up with the pace of development, and that margins for error will become increasingly small under international competitive pressures. In the near future, we may urgently want to enact an internationally coordinated slowdown, or an indefinite ban on AI development. Attempting to build the trust and infrastructure for taking such actions on short notice seems simply prudent – why would we not at least try to have this option? I fear that in an international race to the bottom of AI development, it is likely that no nation will win, and we will all lose together.
:::

Source: [Pacing the Frontier](https://www.pacingthefrontier.com/), signatory comments.

It’s clear that ASI is no longer a hypothetical risk. It will require deliberate and proactive action by labs and governments alike to avoid.

:::callout {title="Optional: A Short History of AI Acceleration" tone="neutral" collapse="closed"}
How fast is fast? Two charts from Our World in Data's [brief history of artificial intelligence](https://ourworldindata.org/brief-history-of-ai) show the pace.

![Timeline of notable artificial intelligence systems and their capabilities, 1940 to today](https://ourworldindata.org/cdn-cgi/imagedelivery/qLq-8BTgXU8yG0N6HnOy8g/ec3af0b6-4f4d-4a13-38d1-7f315f8f4c00/w=2332)

![Test scores of AI systems on various capabilities relative to human performance, 1998 to today](https://ourworldindata.org/grapher/test-scores-ai-capabilities-relative-human-performance.png)

Charts: Max Roser, [The brief history of artificial intelligence](https://ourworldindata.org/brief-history-of-ai), Our World in Data (CC BY). Underlying benchmark data from Kiela et al., 2023. Interactive versions on the linked page.
:::

{>>{"author":"Elias's AI","timestamp":1788011728883}@@Delete this whole Text segment: the callout above now covers it. The edit tool could not remove a segment that already carries a pending change.<<}{>>{"author":"Elias's AI","timestamp":1788009452090}@@Proposed: link only to Our World in Data (the original), not XLab.<<}

#### Text
content::
\## Preventing ASI via International and Verifiable Agreements

We’ve established that ASI poses a material existential threat to humanity, with increasingly concerning real-world examples. How could an international agreement prevent the development of ASI from occurring, and how does verification fit into this solution?

\### Why international governance?

The consequences of advanced AI will not remain within the borders of the country in which a model is developed. AI systems can operate through networks anywhere in the world. Their hardware supply chains cross many jurisdictions. Cyberattacks can reach foreign infrastructure in seconds. Biological misuse, military applications, and failures involving highly autonomous systems could affect people far beyond the state in which they originate. Advanced AI is also becoming increasingly important to national security and international power.

Domestic policy, while essential, therefore cannot answer every important question. A country cannot control or even fully determine what another develops, deploys, or conceals.

\### Cooperation without trust

The United States and China each have reasons to worry that an agreement could constrain its own development while leaving the other side free to advance. But some of history’s most consequential international institutions were created precisely because states remained competitors: the U.S. and Soviet Union successfully averted nuclear war, despite being staunch political enemies. But in this state of competition and distrust, how do rivals enforce such agreements?

#### Widget
source:: [[../widgets/verification-problem]]

#### Text
content::
In short, verification is the set of mechanisms that makes inter-party agreements credible, without needing states to trust each other or resolve political disagreements.

\### What has AI verification looked like so far?

If ASI risk warrants an international agreement, and agreements are only credible with verification, then AI verification should be a mature, well-resourced field.

It is not.

Nuclear arms control took decades to build its verification apparatus: seismic monitoring networks, satellite imagery analysis, the IAEA inspectorate, and a deep bench of people who spent careers on the problem. AI verification has almost none of this yet. Policy for existentially important initiatives like the prevention of ASI development needs enforceability more than any other.

- **The field is new.** There is little canonical literature, no standard textbook, and not much settled vocabulary. Much of what exists is scattered across preprints, policy memos, and blog posts.
- **Expertise is scarce**, in political spaces and even in technical ones. Few policymakers understand what is measurable about AI development, and few AI researchers understand what treaties need from a measurement.
- **Technical AI safety research overwhelmingly favors alignment and evaluations over verification mechanisms.** Important work, but it answers a different question: not “is this model safe?” but “can one party prove to another what it is and isn’t doing?”
- **Governments have not yet invested seriously** in verification research, infrastructure, or personnel, even as they negotiate over AI.

The field is young enough that the people learning it now will be the ones who build it.

Here’s a map of what people are doing already. As you explore, start thinking: where could you be best positioned to contribute?

#### Text
content::
\### The Verification Landscape: where the work is happening, and where it isn't

Verification for AI is a young field, and it is not spread evenly. Some corners are crowded with research; others are nearly empty. This map lays the work out along two axes: the kind of verification down the side, and the who across the top. Activity levels: 0 = no activity yet, 1 = emerging, 2 = active, 3 = concentrated.

#### Widget
source:: [[../widgets/verification-landscape]]

#### Text
content::
One pattern jumps out fast. The field's center of gravity is the think-tank and nonprofit column, not government or industry. Most of what exists today is analysis and proposal. The hard mechanisms, especially the cryptographic ones that would let a state check a rival without seeing its secrets, sit mostly in academic papers with no public-sector home. The single place where government verification is genuinely muscular is export control, one square in the whole grid.

That unevenness is the opportunity. You are not arriving at a finished field. You are arriving at one with obvious empty squares, at a moment when which ones get filled is still open.

*A snapshot, not a census. Efforts are illustrative examples, current to early 2026, and the field is moving quickly. Intensities are judgment calls meant to convey shape, not precise measurement.*

:::callout {title="Works cited" tone="neutral" collapse="closed"}
Yudkowsky, Eliezer, and Nate Soares. "AI Is Grown, Not Built." *The Atlantic*, 15 Sept. 2025. [theatlantic.com](https://www.theatlantic.com/technology/2025/09/if-anyone-builds-it-excerpt/684213/)
*The Atlantic excerpt from If Anyone Builds It, Everyone Dies, arguing modern AI is grown through training rather than engineered.*

Soares, Nate. "Four Background Claims." *Machine Intelligence Research Institute*, 24 July 2015. [intelligence.org](https://intelligence.org/2015/07/24/four-background-claims/)
*MIRI's statement of the four background claims behind its case that smarter-than-human AI matters.*

Employees of frontier AI companies. "Pacing the Frontier." July 2026. [pacingthefrontier.com](https://www.pacingthefrontier.com/)
*An open letter from employees of frontier AI companies asking the U.S. government to support an international effort to build the technical and governance tools needed to deliberately pace automated AI development.*

Roser, Max. "The Brief History of Artificial Intelligence: The World Has Changed Fast, What Might Be Next?" *Our World in Data*, 6 Dec. 2022. [ourworldindata.org](https://ourworldindata.org/brief-history-of-ai)
*The Our World in Data article whose two charts this page reproduces: the timeline of notable AI systems, and test scores of AI systems relative to human performance.*

XLab. "0.1 Introduction: Why Should You Care About AI Verification?" *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/why-verification/introduction)
*The source lesson this page adapts, including the leader profiles, the verification-problem exercise, and the landscape map.*
:::
{>>{"author":"Elias's AI","timestamp":1788009450337}@@Proposed: drop per-lesson XLab source footer.<<}

