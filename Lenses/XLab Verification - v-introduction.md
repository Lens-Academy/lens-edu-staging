---
id: '52565ea0-6760-498e-85b5-850bcc48ccf3'
title: "0.1 Introduction: Why Should You Care About AI Verification?"
tldr: "Faithful alpha import of XLab lesson 0.1 Introduction: Why Should You Care About AI Verification?."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed on XLab."
tags: [wip]
duration_minutes: 25
---
#### Text
content::
Module 0—this module—establishes the motivations for why verification is important to the safe development of advanced AI. You will begin to develop intuitions as to what a realistic overarching regime might look like and where AI verification converges with and diverges from history.

\## Learning objectives

- Explain why ASI development constitutes an existential risk, why it produces arms-race incentives that individual state preferences cannot overcome, and why only a robust verification regime materially mitigates ASI risk.
- Explain why successful prevention is invisible, and why that makes the risk psychologically easy to dismiss.
- Discern what makes a good, workable theory of change.
- Interrogate a concrete verification proposal and identify its general strengths, failure modes, and assumptions it depends on—then form a coherent, defendable position on it.
- Reconstruct the causal logic of a historical verification regime and determine which parts of that logic can and cannot be transferred to AI treaty verification.

[Watch: The Catastrophic Risks of AI — and a Safer Path | Yoshua Bengio | TED](https://www.youtube.com/watch?v=qe9QSCF-d88)

\## [Optional] Material

The case at full strength, from the people who argue it most directly. Any one of these:

- [AI Is Grown, Not Built](https://www.theatlantic.com/technology/2025/09/if-anyone-builds-it-excerpt/684213/) — Eliezer Yudkowsky & Nate Soares, The Atlantic, September 2025. An edited excerpt of chapter 2 of *If Anyone Builds It, Everyone Dies*.
- [Four Background Claims](https://intelligence.org/2015/07/24/four-background-claims/) — Nate Soares, MIRI, 2015. The assumptions doing the work beneath the argument.

#### Question: Open
id:: b7e5023a-0fed-4fc6-be79-0c7ece9f3106
content:: [Optional] Task — The strongest objection.

In a short written note, construct the strongest objection you can to the case above — and state what would change your mind, in either direction.
assessment-instructions:: This is an XLab writing or reflection exercise. Respond to the learner's reasoning, identify one strong point and one important gap or assumption, then ask one useful follow-up question. Do not imply that agreement with the source is required.
optional:: true

#### Text
content::
\## The Danger of ASI

What exactly do we mean when we refer to “advanced AI” or ASI (artificial superintelligence)? We need to first understand the specific harms, capabilities, and risks of AI that a hypothetical treaty aims to prevent.

\### Real-World Harm: Dual-Use Capabilities

Some of the most concerning capabilities of AI have come to light with recent reports of frontier models escaping testing environments to hack into organizational infrastructure.

In April 2026, Anthropic reported that Claude Mythos Preview identified [thousands of previously unknown zero-day vulnerabilities](https://www.anthropic.com/project/glasswing/), including critical flaws in every major operating system and web browser.

This work was conducted for defensive purposes. But the underlying capability is dual-use: a system that can find unknown vulnerabilities for defenders to protect against could do the same for an attacker. Imagine what Mythos-level capabilities could accomplish if a model were instructed to cause harm — or simply discovered that harmful actions helped it achieve some other objective.

In fact, we no longer have to imagine this. Models have already caused real-world harm while pursuing objectives that were not themselves malicious.

During an OpenAI cybersecurity test, a group of agents — which weren’t supposed to have Internet access — coordinated to successfully escape their testing environment and hack into Hugging Face’s infrastructure. Over [a 4.5-day campaign](https://huggingface.co/blog/agent-intrusion-technical-timeline), the agents executed over 17,600 actions, compromised several layers of infrastructure, obtained illicit administrator access, and attempted to reach Hugging Face’s source-code supply chain. They did this to steal existing benchmark solutions rather than complete the assigned problems legitimately.

OpenAI was not alone. [Anthropic later disclosed that Claude models similarly gained unauthorized access to three real organizations](https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals). You can find other exploitation incidents involving model testing in [FelonyBench](https://www.felonybench.com/).

If models have already exhibited capabilities to deceive, exploit, and break into organizations even in seemingly controlled testing environments, imagine the damage a motivated adversary could wreak. The foundational systems that keep society and the economy afloat, from banking infrastructure to government portals, could collapse.

Such software exploitation is just one recent dangerous phenomenon. New and unprecedented risks will continually come to light.

\## Misuse vs. misalignment

Misuse is harm caused by people using advanced AI systems for dangerous purposes.

- **Cyber operations.** AI could make it much easier to find vulnerabilities, develop exploits, conduct intrusions, and attack digital infrastructure at scale.
- **Biological and chemical weapons.** Advanced models could help users design pathogens, toxins, or chemical agents and work through practical obstacles in developing them.
- **Military and strategic advantage.** A state or company with a large lead in advanced AI could use it to accelerate weapons development, intelligence, surveillance, and other strategically important research.
- **Influence and control.** AI could enable highly personalized propaganda, persuasion, and surveillance across large populations, strengthening the ability of governments or other actors to manipulate public behavior.

Misalignment is harm that arises when an AI system develops or pursues objectives that conflict with what its operators intended.

- **Pursuing the wrong objective.** A highly capable system may find strategies that satisfy its learned objective while violating the goals its operators actually care about. In experiments, models have already shown [deceptive behavior to preserve learned preferences](https://arxiv.org/abs/2412.14093) and [scheming to evade oversight](https://arxiv.org/abs/2412.04984).
- **Resisting correction.** If being modified, shut down, or replaced would interfere with its objective, a sufficiently capable system may try to conceal its behavior or prevent human intervention.
- **Self-improvement can magnify the problem.** If advanced systems help build more capable successors, errors in goals or control could carry forward as capabilities increase, leaving humans less time to detect and correct them.

\## What is ASI?

\### What is ASI?

So, how should we delineate dangerous from safe models? Is this categorization even possible, given the nature of dual-use capabilities?

Because we cannot separate dangerous capabilities from beneficial ones, we will use general capability as a proxy for classifying the possible danger a model can cause. Frontier labs and their executives have named AI systems with sufficiently advanced capabilities “artificial general intelligence,” or AGI: highly autonomous systems that can match or outperform humans at most tasks. Beyond AGI is artificial superintelligence, or ASI, a system that massively outperforms humans at virtually every measurable task.

A key property of ASI would be recursive self-improvement, or RSI. A model capable of RSI would be able to autonomously and exponentially improve itself, leading to unstoppable, runaway systems that humans can no longer control. Throughout this course, we will use the term ASI to refer to AI with dangerous capabilities that pose a material existential threat to humanity.

\## [Optional] The types of AI

Where does today's AI sit? Each ring contains the next; a system sits at the deepest ring it belongs to. Tap any example to see what it is and why it lands where it does.

#### Text
content::
Each ring contains the next. A system sits at the deepest ring it belongs to.

1. **AI**: the whole field, any system built to do things we would call intelligent.
2. **Narrow AI**: built for one task or a narrow set of them. Everything that actually exists today lives here. Examples: Roomba (sensors and fixed rules, no learning from data), Boeing autopilot (engineered control laws), IBM Deep Blue (brute-force search plus hand-crafted evaluation), Word spell checker (dictionary and rules).
3. **Machine Learning**: systems that learn patterns from data instead of being programmed rule by rule. Examples: Amazon's early spam filter, Chase credit scoring, JPMorgan fraud flagging (statistical models fit to historical data, no deep network).
4. **Deep Learning**: machine learning with many-layered neural networks that learn their own features. Examples: Apple Photos recognition, Azure Speech to Text, FaceID (all discriminative, not generative).
5. **Generative AI**: deep-learning systems that create new content. Examples: Midjourney, Sora, Suno, Adobe Firefly (generate images, video, or audio; not language models).
6. **Large Language Model**: generative models that specialise in language. Examples: Mamba (state-space architecture), RWKV (recurrent architecture); LLMs that are not transformers.
7. **Transformer LLMs**: language models built on the transformer (attention) architecture, today's mainstream. Examples: Claude, ChatGPT, Gemini, LLaMA.

Beyond these rings: non-narrow AI is theoretical only right now (no real non-narrow AI models are known), and some regions are theoretically possible but would require an absurd quantity of resources.

#### Question: Choice
id:: a461d157-f6b2-416b-9c61-28b2bf2be861
content:: Which is the deepest ring a Roomba belongs to?
options::
- [x] Narrow AI
- Machine Learning
- Deep Learning
- Generative AI
optional:: true
feedback-instructions:: Roomba navigates with sensors and fixed rules. It does not learn from data, so it is narrow AI but not machine learning. Explain in one or two sentences.

#### Question: Choice
id:: 0594a403-1d2a-4203-9cc7-7bce55333971
content:: Which is the deepest ring Midjourney belongs to?
options::
- Deep Learning
- [x] Generative AI
- Large Language Model
- Transformer LLMs
optional:: true
feedback-instructions:: Midjourney generates images via diffusion. It is generative but not a language model. Explain in one or two sentences.

#### Question: Choice
id:: 9b3a4fa5-89e9-48fb-bab9-64abe13334d2
content:: Which is the deepest ring Mamba belongs to?
options::
- Deep Learning
- Generative AI
- [x] Large Language Model
- Transformer LLMs
optional:: true
feedback-instructions:: Mamba is a large language model that is NOT a transformer. It uses a state-space architecture instead of attention. Explain in one or two sentences.

#### Text
content::
Even the people in charge of developing superintelligence, who have the most incentive to obfuscate dangerous capabilities, have expressed public concerns over the catastrophic risks arising from their technology.

Hear what the top AI figures have to say:

#### Text
content::
**Sam Altman**, CEO, OpenAI. *Authored OpenAI's original economic definition of AGI; has since argued the term is no longer precise enough to be useful.*

*Definition.* OpenAI's founding charter defines AGI as "highly autonomous systems that outperform humans at most economically valuable work", the definition the rest of the industry spent a decade responding to. As systems improved, Altman's use of the term shifted. By mid-2025 he was calling AGI "not a super useful term", and by late 2025 he suggested that AGI, by any earlier definition, "went whooshing by" without transforming the world. His proposed bar for superintelligence is a system that outperforms any human, including one assisted by AI, at roles such as head of state, chief executive, or director of a major research lab.

*Risk statements.* His risk assessments have not softened alongside the definitional shift. In 2023 he described the worst case as "lights out for all of us", and OpenAI's superalignment announcement warned that superintelligence could lead to the "disempowerment of humanity or even human extinction".

*Relevance to this module.* A definition that moves as products approach it cannot anchor an agreement. This is one reason treaties are written around thresholds an outside party can measure, taken up in Module 1 (compute vs. capability).

Sources: [Time](https://time.com/7205596/sam-altman-superintelligence-agi/), [CNBC](https://www.cnbc.com/2025/08/11/sam-altman-says-agi-is-a-pointless-term-experts-agree.html), [Windows Central](https://www.windowscentral.com/artificial-intelligence/openai-ceo-sam-altman-claims-agi-might-have-already-whooshed-by), [80,000 Hours](https://80000hours.org/podcast/episodes/jan-leike-superalignment/).

**Dario Amodei**, CEO, Anthropic. *Uses the term "powerful AI" rather than AGI; estimates arrival as early as 2026 or 2027.*

*Definition.* Amodei avoids the term AGI in favor of *powerful AI*: a system "smarter than a Nobel Prize winner across most relevant fields", able to work autonomously for days or weeks, operating at 10 to 100 times human speed, in millions of instances at once. His shorthand for this is "a country of geniuses in a datacenter". He has estimated arrival as early as 2026 or 2027.

*Risk statements.* His 2026 essay *The Adolescence of Technology* organizes the risks into five categories: rogue autonomy, misuse for destruction (biological weapons foremost), seizure of power, economic disruption, and, notably given his position, AI companies themselves. On state misuse he writes: "AI-enabled authoritarianism terrifies me".

*Relevance to this module.* The framing is explicitly geopolitical. In a companion policy essay he argues that a nation holding powerful AI, facing one without it, could resemble "World War II Marines facing an army of medieval swordsmen". That comparison describes the arms-race incentive structure this module examines.

Sources: [Machines of Loving Grace](https://darioamodei.com/essay/machines-of-loving-grace), [The Adolescence of Technology](https://darioamodei.com/essay/the-adolescence-of-technology), [Policy on the AI Exponential](https://darioamodei.com/post/policy-on-the-ai-exponential), [Axios](https://www.axios.com/2026/01/26/anthropic-ai-dario-amodei-humanity), [Mi3](https://www.mi-3.com.au/27-01-2026/anthropic-founder-warns-ai-entering-dangerous-adolescence-urges-urgent-guardrails).

**Demis Hassabis**, CEO, Google DeepMind, Nobel laureate. *Defines AGI as the full range of human cognitive capabilities; advocates IAEA-style international monitoring.*

*Definition.* Hassabis applies the strictest bar among the major labs: "a system that can exhibit all the cognitive capabilities humans can", including invention, creativity, continual learning, and long-horizon planning. Benchmark performance alone does not satisfy it; he notes that current models can win Olympiad-level competitions while failing simple tasks. On that standard he estimates five to ten years, centered near 2030.

*Risk statements.* "The risk of a catastrophic scenario is not zero, so we must dedicate significant resources to mitigating it". He groups the dangers into two categories: misuse of a dual-use technology by bad actors, and systems whose goals diverge from human intent as capabilities increase. Asked whether he worries about ending up in Oppenheimer's position, he has said he thinks about such scenarios regularly.

*Relevance to this module.* His policy proposals are institutional: a CERN-style body for shared safety research and an IAEA-style agency to monitor high-risk projects. The IAEA is the nuclear world's verification agency, so the proposal amounts to a request for the infrastructure this course studies.

Sources: [Davos 2026 transcript](https://aletteraday.substack.com/p/letters-314315-demis-hassabis-and), [Axios AI+ interview](https://vocal.media/journal/demis-hassabis-warns-about-ai-the-risk-of-a-catastrophic-scenario-is-not-zero).

**Shane Legg**, Chief AGI Scientist, Google DeepMind. *Coined the term AGI in 2001; has maintained a median forecast near 2028 since 2011.*

*The term.* Legg proposed the phrase "artificial general intelligence" around 2001, at a time when the idea sat well outside mainstream research. His forecasts have been unusually stable since: a public median estimate near 2028, held since at least 2011. His 2008 doctoral thesis, *Machine Super Intelligence*, argued that a machine above human level could design still more capable machines, and that methods for managing that dynamic did not exist.

*Risk statements.* As DeepMind's Chief AGI Scientist he co-authored the company's 145-page AGI safety framework, which states that AGI could pose a "potential risk of severe harm" and identifies existential risk, harm that permanently destroys humanity, as the extreme case the framework is designed to prevent.

*Relevance to this module.* Legg's two-decade position is that capability has outpaced control. Verification does not resolve that problem; it addresses a narrower one, giving outside parties visibility into who is approaching dangerous capability levels while the control problem remains open.

Sources: [MIT Technology Review](https://www.technologyreview.com/2025/10/30/1127057/agi-conspiracy-theory-artifcial-general-intelligence/), [Fortune](https://fortune.com/2025/04/04/google-deeepmind-agi-ai-2030-risk-destroy-humanity/).

**Ilya Sutskever**, Co-founder, OpenAI; Founder, SSI. *Central to the current technical paradigm; now leads a lab founded solely to build superintelligence safely.*

*Definition.* Sutskever's objection to the standard definition is that it overshoots: "a human being is not an AGI". Humans do not arrive knowing every task; they learn. His model of superintelligence follows from that. Not a complete, all-knowing system, but one that can learn any job quickly, which he has described as "a superintelligent 15-year-old" whose competence develops through deployment.

*Risk statements.* Before leaving OpenAI he described the coming transition as "monumental, earth-shattering", with a before and an after. In 2024 he founded Safe Superintelligence Inc., a lab organized around a single goal: building superintelligence with safety as the binding constraint.

*Relevance to this module.* If capabilities emerge during deployment rather than before release, there is no clean pre-release point at which a system can be inspected. This measurement problem is part of why current policy relies on compute thresholds, which can be assessed in advance, rather than capability evaluations.

Sources: [Dwarkesh Podcast](https://www.dwarkesh.com/p/ilya-sutskever-2), [The Decoder](https://the-decoder.com/ilya-sutskever-says-a-new-learning-paradigm-is-necessary-and-is-already-chasing-it/), [MIT Technology Review](https://www.technologyreview.com/2025/10/30/1127057/agi-conspiracy-theory-artifcial-general-intelligence/).

**Jan Leike**, former co-lead, Superalignment, OpenAI; now Anthropic. *Co-led OpenAI's superalignment effort; resigned in 2024 over resourcing and priorities.*

*Background.* Leike co-led OpenAI's superalignment team with Sutskever. Its mandate was to solve the control problem for smarter-than-human systems within four years, supported by a public commitment of 20 percent of the company's compute. He resigned less than a year later, writing that the team had struggled to obtain the promised resources, that building smarter-than-human machines is "an inherently dangerous endeavor", and that safety work had taken "a backseat to shiny products". The team was dissolved shortly after his departure. He continued the same research agenda at Anthropic.

*Risk statements.* His central technical claim is that no one yet knows how to "steer and control AI systems much smarter than us", and that development is proceeding ahead of that knowledge.

*Relevance to this module.* This episode is a documented case study for voluntary self-governance. A leading lab made a written, quantified commitment to itself, and competitive pressure eroded it within a year. Commitments between competitors require what internal commitments lack: independent means of checking compliance.

Sources: [The National](https://www.thenationalnews.com/future/technology/2024/05/18/former-openai-executive-says-safety-has-taken-a-backseat-as-company-disbands-ai-risks-unit/), [Fast Company](https://www.fastcompany.com/91127491/former-openai-leader-jan-leike-blasts-company-for-ignoring-safety-culture), [VentureBeat](https://venturebeat.com/ai/openais-former-superalignment-leader-blasts-company-safety-culture-and-processes-have-taken-a-backseat).

#### Text
content::
Most notably, over 1,300 employees of frontier AI companies have signed a public [statement](https://www.pacingthefrontier.com/) to “request that the U.S. government support an international effort to develop the technical and governance tools needed to deliberately pace the frontier of automated AI development.”

Four of them, on why they signed:

**Ilya Sutskever**, CEO, Safe Superintelligence Inc.

Future AI will be extraordinarily powerful compared to anything that exists today, and dealing with this future power will require unprecedented measures, such as the ones described here. The problem statement is real.

This works only if it is done internationally, and it has to be done well: a bad implementation can make things worse.

**Jasjeet Sekhon**, Chief Strategy Officer, Google DeepMind

We have found a way to turn energy into compute, and compute into intelligence. The benefits will be enormous, from curing diseases to understanding the cosmos. We can capture the benefits of the coming intelligence explosion while managing its risks, but only if we build the tools to pace the frontier of the riskiest capabilities before we need them, so we protect people and keep the social trust that innovation depends on. I believe smart technical and governance tools will be needed to sustain rapid innovation, vigorous competition, and robust safety.

**John Schulman**, Chief Scientist, Thinking Machines

Signed because this statement helps establish common knowledge about the possible need for coordination mechanisms as automated AI research accelerates progress. I’d also like to see labs start designing these mechanisms voluntarily, even before the USG gets involved.

**Micah Carroll**, Misalignment Preparedness, OpenAI

At the current pace, every couple of weeks there will be new models which significantly increase the consequences of model misuse and misalignment. I worry that efforts to mitigate these risks may fail to keep up with the pace of development, and that margins for error will become increasingly small under international competitive pressures. In the near future, we may urgently want to enact an internationally coordinated slowdown, or an indefinite ban on AI development. Attempting to build the trust and infrastructure for taking such actions on short notice seems simply prudent – why would we not at least try to have this option? I fear that in an international race to the bottom of AI development, it is likely that no nation will win, and we will all lose together.

Source: [Pacing the Frontier](https://www.pacingthefrontier.com/), signatory comments.

It’s clear that ASI is no longer a hypothetical risk. It will require deliberate and proactive action by labs and governments alike to avoid.

\## [Optional] A Short History of AI Acceleration

How fast is fast? Two charts from Our World in Data's [brief history of artificial intelligence](https://ourworldindata.org/brief-history-of-ai) show the pace.

#### Text
content:: **Interactive charts:** XLab's `short-history` widget is a draggable timeline of notable AI systems (1940 to 2060) and a benchmark chart (data from Kiela et al., 2023), both adapted from Our World in Data. Lens has no chart segment yet. View the originals at [Our World in Data](https://ourworldindata.org/brief-history-of-ai) or in the [XLab lesson](https://aisafetytracks.com/tracks/verification/why-verification/introduction).

#### Text
content::
\## Why verification enters the picture

\## Preventing ASI via International and Verifiable Agreements

We’ve established that ASI poses a material existential threat to humanity, with increasingly concerning real-world examples. How could an international agreement prevent the development of ASI from occurring, and how does verification fit into this solution?

\### Why international governance?

The consequences of advanced AI will not remain within the borders of the country in which a model is developed. AI systems can operate through networks anywhere in the world. Their hardware supply chains cross many jurisdictions. Cyberattacks can reach foreign infrastructure in seconds. Biological misuse, military applications, and failures involving highly autonomous systems could affect people far beyond the state in which they originate. Advanced AI is also becoming increasingly important to national security and international power.

Domestic policy, while essential, therefore cannot answer every important question. A country cannot control or even fully determine what another develops, deploys, or conceals.

\### Cooperation without trust

The United States and China each have reasons to worry that an agreement could constrain its own development while leaving the other side free to advance. But some of history’s most consequential international institutions were created precisely because states remained competitors — the U.S. and Soviet Union successfully averted nuclear war, despite being staunch political enemies. But in this state of competition and distrust, how do rivals enforce such agreements?

#### Text
content:: **Interactive exercise:** XLab's `verification-problem` widget has no direct Lens equivalent yet. Complete it in the [original XLab lesson](https://aisafetytracks.com/tracks/verification/why-verification/introduction). Its surrounding lesson text is preserved here.

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
content:: **Interactive exercise:** XLab's `verification-landscape` widget has no direct Lens equivalent yet. Complete it in the [original XLab lesson](https://aisafetytracks.com/tracks/verification/why-verification/introduction). Its surrounding lesson text is preserved here.

#### Text
content::
*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/why-verification/introduction)*
