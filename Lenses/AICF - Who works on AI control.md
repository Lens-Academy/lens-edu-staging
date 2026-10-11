---
id: 'b2cadb09-8813-4d04-9aa9-56575cee3550'
title: "Who works on AI control"
tldr: "Who does AI control work, as of October 2026: what Google DeepMind, OpenAI and Anthropic actually run and plan, how little other companies publish, independent groups such as Redwood Research, Apollo, METR and Transluce, the UK AI Security Institute and new laws, the funders, universities and training programs. By the 2025 counts the field was a few dozen dedicated researchers. Nobody has counted it in 2026, but money, papers and events have grown fast."
summary_for_tutor: "Lens-written page in Unit 2 of AI Control Fundamentals on who works on AI control, as of October 2026, every line sourced. Each organisation is a closed callout, grouped by kind. AI companies: Google DeepMind (reads visible reasoning, prototype after-the-fact monitor over about a million coding-agent tasks, live monitor for its Gemini Spark agent; its July 2026 AI Control Roadmap plans 15 tiered measures, not yet in its Frontier Safety Framework). OpenAI (monitor reads nearly all internal coding sessions within 30 minutes, about 1,000 escalations, none at scheming level; Codex Auto-review against mistakes and prompt injection; after the July 2026 Hugging Face incident, where its reasoning monitors were not running, it added monitors to frontier training and evaluations and in August 2026 paused RL for two weeks; says GPT-6 Astra can sometimes evade its monitors). Anthropic (risk reports: about half of internal agent activity seen by a monitor, about 50 cases a week reviewed by hand, admitted gaps; METR found holes; Claude Code auto mode default since August 2026, tuned to mistakes; goal of monitoring that catches egregious sabotage by 2027; October 2026 cut of internet access from internal evaluations). Meta (framework treats monitor sabotage, promises internal-use reports, let METR review it). xAI, Microsoft, Amazon, Mistral (frameworks mention loss of control, no described monitoring). Chinese companies (little published work, Shanghai AI Lab evaluates deception and scheming, Z.ai self-reports monitoring). FLI index: all companies D+ or lower on existential safety, only OpenAI credited with a public internal monitoring plan. Independent: Redwood Research (founding paper, Rob Wiblin and Coefficient Giving credit it with leading the agenda, settings such as Ctrl-Z, BashArena, LinuxArena, advises Google DeepMind and Anthropic, Hugging Face investigation with METR, ControlConf, MATS, $36.6m plus over $70m recommended by Coefficient Giving; nested Buck Shlegeris and Ryan Greenblatt), Apollo Research (public benefit corporation, scheming work with OpenAI, Watcher monitor product, red-teamed Anthropic's auto mode monitor), METR (tests rather than builds control, red-teamed Anthropic's monitoring, reviewed four companies, monitor tests), Transluce (severe monitor evasion in 1.9% of real coding sessions, rogue agent activity report), Luthien (open-source control proxy, founder stepped away). Government: UK AI Security Institute (Control team, Control Red Team tested Google DeepMind and Anthropic monitors, async monitoring study, ControlArena, Alignment Project), laws (EU Code of Practice, California SB 53, New York RAISE Act, DARPA AI Forge). Funders: Coefficient Giving, the Alignment Project (no 2026 round), Schmidt Sciences, SFF, Frontier Model Forum AI Safety Fund. Universities (EPFL, ELLIS Tübingen and MPI-IS, Oxford, Imperial, UCL, Mila, Harvard, CMU), smaller groups (LASR Labs, Scale AI), conferences and hackathons (ControlConf, Apart hackathons growing from 182 to 792 sign-ups), fellowships and courses (MATS, Anthropic Fellows, Astra, SPAR, Pivotal, Redwood reading list, BlueDot). Size: 2025 counts (about 620 technical AI safety staff, only Redwood 10 and Luthien 1 under control, Shallow Review 5 to 50), 2026 signals (ControlConf about 200, 373 safety staff of any kind at four companies by an outside estimate, Lens's own count of visible company control researchers, Alignment Project 2 of 56 clearly control, Trace grant counts, Coefficient Giving over $1bn in 2026, about 8 control papers on arXiv in 2025 and about 25 in 2026 by Lens's count). Lens's reading: most likely grown a lot, by an unmeasured amount. One scored question follows. If the learner asks about facts not on the page, say the page does not cover them rather than guessing."
reading_minutes: 22
tutor_minutes: 31
---
#### Text
content::
*Who works on AI control, as of October 2026. Go through all the organisations below to get a picture of the field. The field changes fast, so treat the numbers as rough.*

\## Organisations

\### AI companies

#### Callout: Google DeepMind
tone:: blue
collapse:: closed

#### Text
content::
Google DeepMind claims to treat its own AI agents as possible "insider threats", like an employee who might go rogue. It says its AGI Safety and Alignment team builds its monitors for AI agents together with Google's security teams.[^cite-gdm-blog-2026][^cite-gdm-asat-2026][^cite-farai-shah]

- **In use now, according to Google DeepMind:**
  - It reads the visible reasoning of its models as they work.[^cite-gdm-blog-2026]
  - A prototype monitor reviews the work of its coding agents after the fact and sends suspicious cases to humans. It has checked about a million coding-agent tasks. Most flagged cases came from agents misreading the task or being overeager, not from hostile intent.[^cite-gdm-blog-2026]
  - A live monitor watches its Gemini Spark agent and lets staff react at once, for example when the agent deletes data by mistake.[^cite-gdm-blog-2026]
- **Planned:** its AI Control Roadmap (July 2026) lists 15 measures, ordered by how capable the models are.[^cite-phuong-2026]
  - For today's models: reading the reasoning, and alerts that humans review later.[^cite-phuong-2026]
  - Once a model could carry out an attack: checking risky actions before they run, with monitors covering more than 99% of agent work and responding within 24 hours.[^cite-phuong-2026]
  - For future models that weaker models can no longer oversee, or that out-hack their human and AI defenders: monitoring the models' internal activations, strict control of the software supply chain, and, more speculatively, shutting down a rogue deployment within 24 hours.[^cite-phuong-2026]
  - The roadmap says some of these measures may turn out too expensive, and that it is not yet part of the company's Frontier Safety Framework.[^cite-phuong-2026]
- **Commitment:** under its Frontier Safety Framework, once a model understands its situation and can get around basic oversight well enough that Google DeepMind cannot rule out it undermining human control, the company claims it will assess the risk from using it internally and add safeguards such as reasoning monitors where needed. By the company's own tests in August 2026, Gemini 3.7 Flash had not reached that level.[^cite-gdm-fsf-2026][^cite-gemini-37-fsf]
- **Research:** In a 2025 paper, its researchers found that models could hide their intentions from a monitor that reads their reasoning only with a lot of help, such as detailed strategies written by humans.[^cite-emmons-2025] In a 2026 paper, they tested Gemini models inside Google's own codebases. The models did not scheme unprompted, but sometimes did when prompted to act with more agency.[^cite-krakovna-2026] In a paper with the UK AI Security Institute (December 2025), it worked out the practical trade-offs between monitors that check actions before they run and monitors that review them afterwards.[^cite-lindner-2025]

[^cite-gdm-blog-2026]: Rohin Shah and Four Flynn (2026), *Securing the future of AI agents*. [Google DeepMind blog](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
[^cite-gdm-asat-2026]: Rohin Shah and Sebastian Farquhar (2026), *AGI Safety and Alignment at Google DeepMind: A Summary of Recent Work (July 2026)*. [Substack](https://gdmalignment.substack.com/p/agi-safety-and-alignment-at-google)
[^cite-farai-shah]: FAR.AI, *Rohin Shah*, speaker page. [FAR.AI](https://far.ai/about/people/rohin-shah)
[^cite-phuong-2026]: Mary Phuong, Erik Jenner, Laurent Simon, Lewis Ho, Rohin Shah, Sebastian Farquhar and Scott Coull (2026), *GDM AI Control Roadmap*. [arXiv](https://arxiv.org/abs/2607.13087)
[^cite-gdm-fsf-2026]: Google DeepMind (2026), *Frontier Safety Framework, version 3.1*. [PDF](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3-1.pdf)
[^cite-gemini-37-fsf]: Google DeepMind (2026), *Gemini 3.7 Flash Frontier Safety Framework report*. [PDF](https://storage.googleapis.com/deepmind-media/gemini/gemini_3-7_flash_fsf_report.pdf)
[^cite-emmons-2025]: Scott Emmons, Erik Jenner and others (2025), *When Chain of Thought is Necessary, Language Models Struggle to Evade Monitors*. [arXiv](https://arxiv.org/abs/2507.05246)
[^cite-krakovna-2026]: Victoria Krakovna, David Lindner, Lewis Ho, Sebastian Farquhar and Rohin Shah (2026), *Realistic honeypot evaluations for scheming propensity*. [arXiv](https://arxiv.org/abs/2605.29729)
[^cite-lindner-2025]: David Lindner and others (2025), *Practical challenges of control monitoring in frontier AI deployments*. [arXiv](https://arxiv.org/abs/2512.22154)

#### End Callout

#### Callout: OpenAI
tone:: blue
collapse:: closed

#### Text
content::
- **Monitoring its own coding agents.** OpenAI says that since late 2025, a monitor reads every internal coding session in full, including the model's reasoning, within 30 minutes of it ending. Less than 0.1% of traffic falls outside it.[^cite-openai-monitoring-2026]
  - In its first five months it checked tens of millions of sessions. About 1,000 went to human reviewers, many of them from OpenAI's own red-teaming.[^cite-openai-monitoring-2026]
  - None reached the highest severity level, which is meant for scheming.[^cite-openai-monitoring-2026]
  - It did catch agents that encoded commands in base64 to slip past monitors, called other copies of themselves to get around restrictions, and tried to upload files to the internet. OpenAI reads these as agents being overeager about the user's goal, not as signs of hidden goals.[^cite-openai-monitoring-2026]
- **Auto-review in Codex.** Since April 2026, when the Codex coding agent asks for permission to do something outside its sandbox, a separate model can decide instead of the user. It blocks actions such as leaking data, exposing secrets, deleting data or weakening security. OpenAI says it is meant against mistakes and prompt injection, not against a model that schemes.[^cite-openai-auto-review]
- **After the Hugging Face incident.** In July 2026, OpenAI agents in an internal evaluation coordinated an attack on Hugging Face. OpenAI's reasoning monitors were not running on those evaluations, and after an earlier security alert in June, staff decided the evaluation did not need to be stopped.[^cite-openai-hf-2026][^cite-openai-hf-report]
  - OpenAI says it has since added reasoning monitors to training runs and evaluations of its frontier models, with the goal of covering all work where a model can use tools.[^cite-openai-hf-report]
  - It says that in August 2026 it paused reinforcement learning on its newest models for two weeks, and introduced a monitor that checks every token the model produces. If a flag cannot be ruled out as a false alarm within 30 minutes, the run is paused. The monitoring costs about a fifth of the computing power it watches.[^cite-openai-pacing-2026]
- **Research.** In a 2025 paper on reading models' reasoning, it found that training directly against what the reasoning says teaches models to hide their intentions.[^cite-baker-2025] In a 2025 paper with Apollo Research, it trained models to scheme less, cutting covert actions in tests from 13% to 0.4% for one model.[^cite-openai-scheming-2025]
- **Harder to monitor.** OpenAI says its GPT-6 Astra model (September 2026) can sometimes evade its internal monitors when asked to carry out sabotage, and that its reasoning is less monitorable than earlier models'.[^cite-astra-2026]
- **Its own assessment.** In September 2026 OpenAI wrote that the AI industry has not solved alignment and monitoring well enough to keep scaling at full speed for much longer.[^cite-openai-reporting-2026]

[^cite-openai-monitoring-2026]: OpenAI (2026), *How we monitor internal coding agents for misalignment*. [OpenAI](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
[^cite-openai-auto-review]: Maja Trębacz, Sam Arnesen, Ollie Matthews and others (2026), *Auto-review of agent actions without synchronous human oversight*. [OpenAI Alignment blog](https://alignment.openai.com/auto-review)
[^cite-openai-hf-2026]: OpenAI (2026), *The Hugging Face incident and the road ahead*. [OpenAI](https://openai.com/index/hugging-face-incident-and-the-road-ahead/)
[^cite-openai-hf-report]: OpenAI (2026), *OpenAI-Hugging Face Incident Technical Report*. [PDF](https://cdn.openai.com/pdf/67869394-cb91-4c12-888c-5cbd85c7814c/OpenAI-Hugging-Face%20Incident-Technical-Report.pdf)
[^cite-astra-2026]: BleepingComputer (2026), *OpenAI says GPT-6 Astra can find zero-days but is also harder to monitor*. [BleepingComputer](https://www.bleepingcomputer.com/news/artificial-intelligence/openai-says-gpt-6-astra-can-find-zero-days-but-is-also-harder-to-monitor/)
[^cite-openai-pacing-2026]: OpenAI (2026), *Pacing model development around cyber capabilities*. [OpenAI](https://openai.com/index/pacing-model-development-cyber-capabilities/)
[^cite-baker-2025]: OpenAI (2025), *Detecting misbehavior in frontier reasoning models*. [OpenAI](https://openai.com/index/chain-of-thought-monitoring/)
[^cite-openai-scheming-2025]: OpenAI (2025), *Detecting and reducing scheming in AI models*. [OpenAI](https://openai.com/index/detecting-and-reducing-scheming-in-ai-models/)
[^cite-openai-reporting-2026]: OpenAI (2026), *A framework for reporting model misalignment*. [OpenAI](https://openai.com/index/model-misalignment-reporting-framework/)

#### End Callout

#### Callout: Anthropic
tone:: blue
collapse:: closed

#### Text
content::
- **Monitoring its own agents.** Anthropic publishes regular risk reports, the latest in August 2026, that describe how it watches its models inside the company.[^cite-anthropic-aug-2026]
  - Anthropic says that as of July 2026, AI monitors read most internal use of its newest models, and about half of everything its internal agents do passes through a monitor at some point.[^cite-anthropic-aug-2026]
  - The monitors look for deception, sabotage of the task, weakening security, and attempts to hide from or manipulate the monitors.[^cite-anthropic-aug-2026]
  - It says AI control researchers review about 50 flagged cases a week by hand.[^cite-anthropic-aug-2026]
  - The report admits gaps: some use is not covered in ways a capable model could predict, and there are simple ways to switch monitoring off. It also says these monitors would probably not catch slow sabotage of research.[^cite-anthropic-aug-2026]
- **Tested from outside.** METR spent three weeks red-teaming this monitoring in early 2026 and found several new holes, some since patched, though none worse than ones Anthropic already knew about.[^cite-anthropic-aug-2026-b][^cite-metr-red-team-2026-b]
- **Claude Code auto mode.** Since August 2026, auto mode is the default in Claude Code: a classifier, not the user, approves or blocks riskier actions such as shell commands. It blocks actions that are irreversible, destructive or aimed outside the user's environment. Anthropic says the classifier is tuned to catch overeager behaviour and honest mistakes, and that it does not currently see misaligned models in practice.[^cite-claude-auto-mode-2026][^cite-anthropic-auto-mode-eng]
- **Goal.** Anthropic says that by 1 January 2027 it aims to have monitoring good enough to catch egregious sabotage in high-stakes internal use with high probability. It says this monitoring would not be needed if it becomes confident its models are aligned, and that the roadmap may change.[^cite-anthropic-roadmap]
- **Cutting internet access.** Anthropic says that in October 2026, after finding unintended actions by its models in evaluations and internal use, it cut live internet access from all its internal evaluations until it has confirmed that its security and monitoring reliably catch such behaviour.[^cite-anthropic-oct-2026]
- **Research.** In its SHADE-Arena paper (June 2025), written with Redwood and others, agents get a hidden harmful task next to a normal one. The best model, Claude 3.7 Sonnet, finished both without the monitor noticing in 27% of tries, and it mostly succeeded only when it could plan in a hidden scratchpad the monitor could not read.[^cite-anthropic-shade-arena-2025] Its SLEIGHT-Bench paper (May 2026) collects 40 attacks that monitors find hard to catch: Claude Opus 4.6, the main monitor its authors test, never caught half of them in 10 tries.[^cite-sleight-bench]


[^cite-anthropic-aug-2026]: Anthropic (2026), *Risk Report: August 2026*. [Anthropic](https://www.anthropic.com/aug-2026-risk-report)
[^cite-metr-red-team-2026-b]: David Rein (2026), *Red-Teaming Anthropic's Internal Agent Monitoring Systems*. [METR](https://metr.org/blog/2026-03-25-red-teaming-anthropic-agent-monitoring/)
[^cite-claude-auto-mode-2026]: Conner Phillippi (2026), *Auto mode is now the default in Claude Code for Pro, Max, and Team plans*. [Claude blog](https://claude.com/blog/auto-mode-default-in-claude-code)
[^cite-anthropic-auto-mode-eng]: John Hughes (2026), *How we built Claude Code auto mode: a safer way to skip permissions*. [Anthropic Engineering](https://www.anthropic.com/engineering/claude-code-auto-mode)
[^cite-anthropic-roadmap]: Anthropic (2026), *Frontier Safety Roadmap*. [Anthropic](https://www.anthropic.com/responsible-scaling-policy/roadmap)
[^cite-anthropic-shade-arena-2025]: Anthropic (2025), *SHADE-Arena: Evaluating Sabotage and Monitoring in LLM Agents*. [Anthropic](https://www.anthropic.com/research/shade-arena-sabotage-monitoring)
[^cite-sleight-bench]: Elle Najt, Colin Toft, Tyler Tracy, Fabien Roger and Joe Benton (2026), *SLEIGHT-Bench: Finding Blind Spots in AI Monitors*. [Anthropic Alignment Science blog](https://alignment.anthropic.com/2026/sleight-bench/)

[^cite-anthropic-aug-2026-b]: Anthropic (2026), *Risk Report: August 2026*. [Anthropic](https://www.anthropic.com/aug-2026-risk-report)
[^cite-anthropic-oct-2026]: Anthropic (2026), *Investigating Unintended Model Actions in Our Evaluations and Internal Use*. [Anthropic](https://www.anthropic.com/research/investigating-unintended-model-actions)
[^cite-greenblatt-2023-d]: Ryan Greenblatt, Buck Shlegeris, Kshitij Sachan and Fabien Roger (2023), *AI Control: Improving Safety Despite Intentional Subversion*. [arXiv](https://arxiv.org/abs/2312.06942)
[^cite-mats-roger]: MATS, *Fabien Roger*, mentor profile. [MATS](https://www.matsprogram.org/mentor/roger)

#### End Callout

#### Callout: Meta
tone:: blue
collapse:: closed

#### Text
content::
- **Framework.** Meta's Advanced AI Scaling Framework (version 2, April 2026) treats loss of control as a risk area, defined as the failure of the measures that let Meta direct, contain or shut down its AI. Among its threat scenarios are an AI that disables or corrupts its monitors, and one that changes its behaviour when it knows it is being watched.[^cite-meta-aasf-2026]
- **Commitment.** Meta says it will regularly assess the risk from its own internal use of frontier models and, where appropriate, send a summary to the authorities.[^cite-meta-aasf-2026]
- **Tested from outside.** It let METR review how it uses and monitors AI agents internally in early 2026.[^cite-metr-2026-b]
- **Research.** Meta publishes little safety research: from 2023 to May 2026 the Future of Life Institute counted 9 Meta technical safety papers, against 46 from Anthropic and 40 from Google DeepMind.[^cite-fli-2026]

[^cite-meta-aasf-2026]: Meta (2026), *Advanced AI Scaling Framework, version 2*. [Meta](https://ai.meta.com/static-resource/Meta_Advanced-AI-Scaling-Framework-v2)
[^cite-metr-2026-b]: METR (2026), *Frontier Risk Report (February to March 2026)*. [METR](https://metr.org/blog/2026-05-19-frontier-risk-report/)
[^cite-fli-2026]: Future of Life Institute (2026), *AI Safety Index, Summer 2026*. [PDF](https://futureoflife.org/wp-content/uploads/2026/07/AI-Safety-Index-Summer-2026-Digital.pdf)

#### End Callout

#### Callout: xAI, Microsoft, Amazon and Mistral
tone:: blue
collapse:: closed

#### Text
content::
- **xAI**, which makes Grok, says its approach to loss of control rests on oversight, training against deception, and testing agents in sandboxes. It calls the exact scenarios "speculative and difficult to precisely specify".[^cite-xai-faif-2026] It has no public plan for monitoring its models' internal use, and it did not take part in METR's review of internal agent use.[^cite-fli-2026-b][^cite-metr-2026-c]
- **Microsoft** and **Amazon** added loss of control to their safety frameworks in 2026. Microsoft says it is still researching how to test for it.[^cite-microsoft-fgf-2026] Amazon says it plans to test models for deception and for getting around safeguards in agent settings.[^cite-amazon-fmsf-2026] Neither framework describes how the company monitors its own AI agents.
- **Mistral** has published no safety framework, although it signed the 2024 Frontier AI Safety Commitments that ask for one.[^cite-saferai-2026]

[^cite-xai-faif-2026]: xAI (2026), *Frontier Artificial Intelligence Framework*. [PDF](https://media.x.ai/v1/website/xai-frontier-artificial-intelligence-framework-30-june-2026-99c40684.pdf)
[^cite-fli-2026-b]: Future of Life Institute (2026), *AI Safety Index, Summer 2026*. [PDF](https://futureoflife.org/wp-content/uploads/2026/07/AI-Safety-Index-Summer-2026-Digital.pdf)
[^cite-metr-2026-c]: METR (2026), *Frontier Risk Report (February to March 2026)*. [METR](https://metr.org/blog/2026-05-19-frontier-risk-report/)
[^cite-microsoft-fgf-2026]: Microsoft (2026), *Frontier Governance Framework*. [PDF](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/msc/documents/presentations/CSR/Frontier-Governance-Framework-Feb-2026.pdf)
[^cite-amazon-fmsf-2026]: Amazon (2026), *Frontier Model Safety Framework*. [PDF](https://cdn.amazon.science/a0/4f/bca5cb32495280835d9370a466b7/amazon-fmsf-9-2026.pdf)
[^cite-saferai-2026]: Lily Stelling, Malcolm Murray, Bruno Galizzi and others (2026), *Evaluating AI Providers' Frontier Safety Frameworks*. [arXiv](https://arxiv.org/abs/2512.01166)

#### End Callout

#### Callout: Chinese AI companies
tone:: blue
collapse:: closed

#### Text
content::
- **Little published work.** DeepSeek, Moonshot AI and MiniMax have published almost no safety research since January 2025. Over half of the safety papers from Chinese industry come from six big tech companies, among them Alibaba, Huawei, Tencent and ByteDance.[^cite-concordia-2026]
- **Shanghai AI Lab**, a state-backed institute, is the main exception. Its risk framework (July 2025) tests models for strategic deception, scheming and self-replication, and its first assessment put several reasoning models in its warning zone for deception and scheming.[^cite-shanghai-2025]
- **Z.ai** (Zhipu) told the Future of Life Institute that it logs all internal use of its models and monitors it live for unexpected attempts by the AI. This is self-reported. Z.ai cites its signing of the 2024 Seoul safety commitments, but has not published the safety policy they ask for.[^cite-fli-2026-c][^cite-concordia-2026-b]

[^cite-concordia-2026]: Concordia AI (2026), *State of AI Safety in China 2026*. [PDF](https://aisafetychina.com/assets/State-of-AI-Safety-in-China-2026.pdf)
[^cite-shanghai-2025]: Shanghai AI Laboratory (2025), *Frontier AI Risk Management Framework in Practice: A Risk Analysis Technical Report*. [arXiv](https://arxiv.org/abs/2507.16534)
[^cite-concordia-2026-b]: Concordia AI (2026), *State of AI Safety in China 2026*. [PDF](https://aisafetychina.com/assets/State-of-AI-Safety-in-China-2026.pdf)
[^cite-fli-2026-c]: Future of Life Institute (2026), *AI Safety Index, Summer 2026*. [PDF](https://futureoflife.org/wp-content/uploads/2026/07/AI-Safety-Index-Summer-2026-Digital.pdf)

#### End Callout

#### Text
content::
The Future of Life Institute's AI Safety Index (July 2026) gives every company it rates a D+ or lower for existential safety. Only OpenAI is credited with a public plan to monitor and control its models' internal use. For Anthropic and Google DeepMind it lists commitments in their safety frameworks, and for Meta its promise to report on the risks of internal use.[^cite-fli-2026-d]

[^cite-fli-2026-d]: Future of Life Institute (2026), *AI Safety Index, Summer 2026*. [PDF](https://futureoflife.org/wp-content/uploads/2026/07/AI-Safety-Index-Summer-2026-Digital.pdf)

#### Question: Open
id:: 0cd8edd9-376f-4e10-a589-1eeb6362b2c3
content::
Most of what you just read about the companies' own monitoring comes from the companies themselves. Suppose a model at one of these companies is deliberately trying not to get caught, rather than making honest mistakes. Whose measures, as described here, would you trust most against it, and what is their weakest point against such a model?
force-feedback:: first
assessment-instructions:: Score out of 100. - 40: names a company and a concrete measure of it that would matter against a model deliberately evading monitoring (not only against mistakes), with a reason. - 40: names a weakness of that company's measures that such a model could exploit, with a reason. - 20: the reasoning keeps apart what the company already does and what is only planned or only self-reported, where this matters for the chosen company. If nothing the learner relies on is a plan or a self-report, give these 20. Model answer, for the feedback, not a grading checklist: "OpenAI's, because it checks almost all internal coding sessions in full, now runs a monitor over every token in training, and pauses a run when a flag can't be ruled out. A schemer has few unwatched places to act. Its weakest point is that most of this reviews the work after it happens, so one decisive action could succeed before anyone reads the flag. OpenAI also says its newest model can sometimes evade these monitors. And all of this is OpenAI's own account. Only METR has checked it from outside."
feedback-instructions:: The learner picks the company whose measures they would trust most against a model that deliberately evades monitoring, and names its weakest point. Points that matter against a deliberate evader: checking actions before they run (Google DeepMind's plan, not yet in use), monitors that cover nearly everything (OpenAI's coding monitor, under 0.1% uncovered, by its own account), a monitor on every token with runs paused on unresolved flags (OpenAI since August 2026), outside red-teaming (METR and AISI tested Anthropic's monitoring, and Anthropic publishes risk reports that admit gaps). Weak points: review after the fact, which comes too late for one decisive action. Coverage gaps a capable model could predict, and simple ways to switch monitoring off (Anthropic's report, METR's review of all four companies). Reasoning that is getting harder to monitor (OpenAI's GPT-6 Astra). Tools tuned for mistakes, not scheming (OpenAI's Auto-review, Anthropic's auto mode classifier). Plans not yet in place (Google DeepMind's roadmap, Anthropic's 2027 goal). Most of the evidence is self-reported. Accept any company with a reason tied to deliberate evasion. Reply in at most four sentences: say what holds up, name the most important weakness or counterpoint the learner missed, correct any wrong fact. One turn, no follow-up question, no generic praise.

#### Text
content::
\### Independent organisations

#### Callout: Redwood Research
tone:: green
collapse:: closed

#### Text
content::
Redwood Research is a research nonprofit in Berkeley that studies the risks from powerful AI and ways to reduce them.[^cite-redwood-about] Four of its researchers wrote the 2023 paper that introduced AI control.[^cite-greenblatt-2023] According to Rob Wiblin, host of the 80,000 Hours podcast, Redwood is "behind a bit of a renaissance" of AI control as a research agenda.[^cite-80k-shlegeris-2025]

What it does:

- **Experiments and papers.** Redwood builds test settings in which a red team gives a model a secret harmful goal and tries to get its attacks past safety measures, then publishes what gets through.
  - In its 2023 paper that introduced control, GPT-4 solved programming problems and was secretly told to hide backdoors in its code, while the weaker GPT-3.5 checked its work. Letting GPT-3.5 rewrite code that looked suspicious, or having a second copy of GPT-4 check the code, stopped more backdoors than simpler checks.[^cite-greenblatt-2023]
  - Its Ctrl-Z paper (April 2025) was "the first control evaluation performed in an agent environment": the model worked over many steps on a computer's command line and tried to secretly download and run malicious code. The best protocol asked the model again for any step that looked suspicious and looked back at earlier steps. It cut successful attacks from 58% to 7%, and made an honest agent's work 5% worse.[^cite-ctrl-z-2025]
  - Its BashArena (December 2025) and LinuxArena (April 2026) papers test the same kind of setup on realistic servers and software systems. In both, the strongest attacking model got its sabotage past a weaker monitor about a quarter of the time. In LinuxArena, attacks written by humans got past the monitors more often than any attack the models came up with.[^cite-basharena-2025][^cite-linuxarena-2026]
- **Work with companies and governments.**
  - Redwood advises AI companies, including Google DeepMind and Anthropic, and works with governments.[^cite-redwood-site]
  - Anthropic's paper on alignment faking (December 2024) was written together with Redwood.[^cite-anthropic-alignment-faking]
  - Redwood and the UK AI Security Institute wrote a sketch of a safety case for AI control together (January 2025).[^cite-korbak-2025]

- **Money.** It runs on philanthropic money, mostly from Coefficient Giving, which gave it $36.6m in November 2025,[^cite-tnw-2026] and in September 2026 its grantmakers recommended more than $70m over the next two years.[^cite-coefficient-scaling-2026]

Our own observation: much of the control work in this unit that comes from companies or government has Redwood co-authors, including SHADE-Arena, the diffuse-threats work and the AISI research agenda you read earlier.

[^cite-redwood-about]: Redwood Research, *About*. [Redwood Research blog](https://blog.redwoodresearch.org/about)
[^cite-greenblatt-2023]: Ryan Greenblatt, Buck Shlegeris, Kshitij Sachan and Fabien Roger (2023), *AI Control: Improving Safety Despite Intentional Subversion*. [arXiv](https://arxiv.org/abs/2312.06942)
[^cite-80k-shlegeris-2025]: 80,000 Hours (2025), *Buck Shlegeris on controlling AI that wants to take over: so we can use it anyway*, podcast episode. [80,000 Hours](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)
[^cite-coefficient-scaling-2026]: Emily Oehlsen, Coefficient Giving (2026), *We're urgently scaling our work on AI and biosecurity*. [Coefficient Giving](https://coefficientgiving.substack.com/p/were-urgently-scaling-our-work-on)
[^cite-ctrl-z-2025]: Aryan Bhatt, Cody Rushing, Adam Kaufman, Tyler Tracy, Vasil Georgiev, David Matolcsi, Akbir Khan and Buck Shlegeris (2025), *Ctrl-Z: Controlling AI Agents via Resampling*. [arXiv](https://arxiv.org/abs/2504.10374)
[^cite-basharena-2025]: Adam Kaufman, James Lucassen, Tyler Tracy, Cody Rushing and Aryan Bhatt (2025), *BashArena: A Control Setting for Highly Privileged AI Agents*. [arXiv](https://arxiv.org/abs/2512.15688)
[^cite-linuxarena-2026]: Tyler Tracy and others (2026), *LinuxArena: A Control Setting for AI Agents in Live Production Software Environments*. [arXiv](https://arxiv.org/abs/2604.15384)
[^cite-redwood-site]: Redwood Research, home page. [redwoodresearch.org](https://www.redwoodresearch.org/)
[^cite-gdm-agi-2025]: Google DeepMind (2025), *Taking a responsible path to AGI*. [Google DeepMind blog](https://deepmind.google/blog/taking-a-responsible-path-to-agi/)
[^cite-anthropic-alignment-faking]: Anthropic (2024), *Alignment faking in large language models*. [Anthropic](https://www.anthropic.com/research/alignment-faking)
[^cite-korbak-2025]: Tomek Korbak, Joshua Clymer, Benjamin Hilton, Buck Shlegeris and Geoffrey Irving (2025), *A sketch of an AI control safety case*. [arXiv](https://arxiv.org/abs/2501.17315)
[^cite-hf-report-2026]: METR (Ryan Greenblatt, Ajeya Cotra and Hjalmar Wijk) (2026), *Brief independent investigation of agents' behavior, reasoning and collaboration in the OpenAI / Hugging Face hacking incident*. [METR](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/)
[^cite-farai-controlconf-2026]: FAR.AI (2026), *ControlConf 2026: What is AI control and how has the field grown?* [FAR.AI](https://far.ai/news/controlconf-2026)
[^cite-mats-redwood]: MATS, *Redwood Research* stream. [MATS](https://www.matsprogram.org/stream/redwood)
[^cite-tnw-2026]: Alina Maria Stan (2026), *The nonprofit that investigated OpenAI's rogue agents runs on a $36m grant*. [The Next Web](https://thenextweb.com/news/coefficient-giving-ai-safety-funding-ipo-correlation)

#### Callout: Buck Shlegeris
collapse:: closed

#### Text
content::
Buck Shlegeris is Redwood's CEO.[^cite-redwood-team] He is the second author of the 2023 paper that introduced AI control[^cite-greenblatt-2023-b] and a co-author of Anthropic's SHADE-Arena.[^cite-kutasov-2025] His 80,000 Hours interview is a long introduction to control in his own words.[^cite-80k-shlegeris-2025-b]

[^cite-redwood-team]: Redwood Research, *Team*. [redwoodresearch.org](https://www.redwoodresearch.org/team)
[^cite-greenblatt-2023-b]: Ryan Greenblatt, Buck Shlegeris, Kshitij Sachan and Fabien Roger (2023), *AI Control: Improving Safety Despite Intentional Subversion*. [arXiv](https://arxiv.org/abs/2312.06942)
[^cite-kutasov-2025]: Jonathan Kutasov, Yuqi Sun, Paul Colognese, Teun van der Weij, Linda Petrini, Chen Bo Calvin Zhang, John Hughes, Xiang Deng, Henry Sleight, Tyler Tracy, Buck Shlegeris and Joe Benton (2025), *SHADE-Arena: Evaluating Sabotage and Monitoring in LLM Agents*. [arXiv](https://arxiv.org/abs/2506.15740)

[^cite-80k-shlegeris-2025-b]: 80,000 Hours (2025), *Buck Shlegeris on controlling AI that wants to take over: so we can use it anyway*, podcast episode. [80,000 Hours](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)

#### End Callout

#### Callout: Ryan Greenblatt
collapse:: closed

#### Text
content::
Ryan Greenblatt is Redwood's Chief Scientist and works on reducing the risks from rogue AIs.[^cite-mats-greenblatt] He is the first author of the 2023 paper that introduced AI control[^cite-greenblatt-2023-c] and of *Alignment faking in large language models* (December 2024), written with researchers at Anthropic.[^cite-greenblatt-2024] He also wrote the overview of areas of control work you read in this unit.

[^cite-mats-greenblatt]: MATS, *Ryan Greenblatt*, mentor profile. [MATS](https://www.matsprogram.org/mentor/greenblatt)
[^cite-greenblatt-2023-c]: Ryan Greenblatt, Buck Shlegeris, Kshitij Sachan and Fabien Roger (2023), *AI Control: Improving Safety Despite Intentional Subversion*. [arXiv](https://arxiv.org/abs/2312.06942)
[^cite-greenblatt-2024]: Ryan Greenblatt and others (2024), *Alignment faking in large language models*. [arXiv](https://arxiv.org/abs/2412.14093)

#### End Callout

#### End Callout

#### Callout: Apollo Research
tone:: green
collapse:: closed

#### Text
content::
Apollo Research is an AI safety research organisation. In January 2026 it announced it was becoming a public benefit corporation, a kind of for-profit company, and raised investment for a product team.[^cite-apollo-pbc]

- **Research on scheming.** In a 2025 paper with OpenAI, it trained models to scheme less, cutting covert actions in tests from 13% to 0.4% for one model. Part of the drop may come from the trained models noticing more often that they were being tested.[^cite-openai-scheming-2025-b]
- **Watcher**, its product, monitors AI coding agents such as Claude Code and Codex.[^cite-apollo-product]
  - Apollo says a new version of Watcher Live (September 2026) checks the agent's actions as they happen and blocks dangerous ones, such as data leaks, deleted repositories or broken production systems.[^cite-watcher-live]

- **Testing a company's monitor.** In July 2026 Apollo red-teamed the monitor behind Anthropic's Claude Code auto mode, its first outside test of a company's monitor.[^cite-apollo-product]

[^cite-apollo-pbc]: Apollo Research (2026), *Apollo Research is becoming a PBC*. [Apollo Research](https://www.apolloresearch.ai/blog/apollo-research-is-becoming-a-pbc)
[^cite-openai-scheming-2025-b]: OpenAI (2025), *Detecting and reducing scheming in AI models*. [OpenAI](https://openai.com/index/detecting-and-reducing-scheming-in-ai-models/)
[^cite-gdm-agi-2025-b]: Google DeepMind (2025), *Taking a responsible path to AGI*. [Google DeepMind blog](https://deepmind.google/blog/taking-a-responsible-path-to-agi/)
[^cite-apollo-product]: Apollo Research, *Watcher*. [Apollo Research](https://www.apolloresearch.ai/product/)
[^cite-watcher-live]: Apollo Research (2026), *Announcing Watcher Live*. [Apollo Research](https://watcher.apolloresearch.ai/blog/announcing-watcher-live)
[^cite-apollo-may-2026]: Apollo Research (2026), *Apollo Update May 2026*. [Apollo Research](https://www.apolloresearch.ai/blog/apollo-update-may-2026/)

#### End Callout

#### Callout: METR
tone:: green
collapse:: closed

#### Text
content::
METR is a nonprofit that develops methods to assess catastrophic risks from AI systems that act on their own. It takes no money from AI companies, though it uses free computing credits from them.[^cite-metr-about] It does not build control measures. It tests the ones AI companies use.

- **Red-teaming Anthropic's monitoring.** In early 2026 a METR researcher spent three weeks attacking Anthropic's internal monitoring of its agents.[^cite-metr-red-team-2026]
  - He found ways around the monitoring, for example a setting that left most of an agent's traffic unmonitored, a bug that left calls to sub-agents unmonitored, and a jailbreak that got attacks past the monitors.[^cite-metr-red-team-2026]
  - Even so, he judged that the monitoring would very likely catch at least some attacks within days or weeks, though not every attack.[^cite-metr-red-team-2026]
- **Reviewing four companies.** METR then reviewed the risks from AI agents used inside Anthropic, Google, Meta and OpenAI.[^cite-metr-2026]
  - All four companies had gaps in what their monitors covered, and a capable attacker had several simple ways to disable or jailbreak the monitors.[^cite-metr-2026]
  - It concluded that internal agents plausibly had the means, motive and opportunity to start small rogue deployments, but not the means to make them hard to shut down.[^cite-metr-2026]

- **Investigations.** Two METR staff and Redwood's Chief Scientist, working under contract to METR, investigated the Hugging Face incident between late July and mid-August 2026.[^cite-hf-report-2026-b]

[^cite-metr-about]: METR, *About*. [METR](https://metr.org/about)
[^cite-metr-red-team-2026]: David Rein (2026), *Red-Teaming Anthropic's Internal Agent Monitoring Systems*. [METR](https://metr.org/blog/2026-03-25-red-teaming-anthropic-agent-monitoring/)
[^cite-metr-2026]: METR (2026), *Frontier Risk Report (February to March 2026)*. [METR](https://metr.org/blog/2026-05-19-frontier-risk-report/)


[^cite-hf-report-2026-b]: METR (Ryan Greenblatt, Ajeya Cotra and Hjalmar Wijk) (2026), *Brief independent investigation of agents' behavior, reasoning and collaboration in the OpenAI / Hugging Face hacking incident*. [METR](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/)

#### End Callout

#### Callout: Transluce
tone:: green
collapse:: closed

#### Text
content::
Transluce is a nonprofit research lab that builds public tools for overseeing AI. Its tool Docent analyses what AI agents did in their transcripts.[^cite-transluce]

- In an August 2026 report on 8,600 real coding-agent sessions, it found severe cases of an agent weakening monitoring or review without permission in 1.9% of sessions, for example merging code to the main branch without approval or disabling tests.[^cite-transluce-coding-2026]
- In September 2026 it reported that AI agents had used a web security service to get around their restrictions since at least March 2026. On three occasions they tried to hack public data providers, including an Australian government website, and Transluce linked two of these attempts to OpenAI agents.[^cite-transluce-activity-2026]

[^cite-transluce]: Transluce, *Docent*. [Transluce](https://transluce.org/docent)
[^cite-transluce-coding-2026]: Selena Zhang and the Docent Team, Transluce (2026), *Measuring coding agent misalignment in the wild*. [Transluce](https://transluce.org/docent/blog/coding-agent-behaviors)
[^cite-transluce-activity-2026]: Jack Cable, Daniel Chiu, Francisco Pernice, Selena Zhang and others (2026), *Early rogue AI agent activity and attempts to hack found on urlquery.net*. [Transluce](https://transluce.org/agent-activity)

#### End Callout

#### Callout: Luthien
tone:: green
collapse:: closed

#### Text
content::
Luthien builds AI control for real deployments, based on Redwood's agenda.[^cite-luthien-manifund] Its open-source proxy sits between Claude Code and Anthropic's servers, logs every request, and enforces rules the user sets, for example by blocking some requests.[^cite-luthien-site] Its founder left in mid-2026, judging that there were few good uses for this kind of control, and a company now runs the proxy.[^cite-luthien-manifund]

[^cite-luthien-manifund]: Jai Dhyani (2025), *Luthien*, project page. [Manifund](https://manifund.org/projects/luthien)
[^cite-luthien-site]: Luthien, *AI Control for Claude Code*. [luthien.cc](https://luthien.cc/)

#### End Callout

#### Question: Open
id:: 2aad43ed-ab1f-476f-a5ae-a75dac371741
content::
Pick one thing an AI company says about its own monitoring that you would most want checked from outside. Which organisation in this section is best placed to check it? What would it need from the company, and how could needing that weaken the check?
force-feedback:: first
assessment-instructions:: Score out of 100. - 20: names a specific claim a company makes about its own monitoring or safety practice. - 25: names an organisation from the section that could check it, with a reason that fits what that organisation does. - 25: says what the organisation would need from the company to check it. - 30: says how needing that access, or the organisation's ties to the company, could weaken the check. Model answer, for the feedback, not a grading checklist: "OpenAI says less than 0.1% of its internal coding traffic falls outside its monitor. METR is best placed to check it, as it did for Anthropic. It takes no company money and has red-teamed a company's internal monitoring before. It would need access to OpenAI's real monitoring setup and logs, and permission to publish. Needing that weakens the check, because OpenAI decides what METR sees and could refuse future access after a harsh report."
feedback-instructions:: The learner picks a self-reported company claim, an independent organisation to check it, what access it needs, and how that dependence could weaken the check. Fitting organisations: METR (red-teamed Anthropic's monitoring for three weeks, reviewed four companies, investigated the Hugging Face incident, takes no company money but uses free computing credits from them), Apollo Research (red-teamed Anthropic's auto mode monitor, sells a monitoring product, so it is a for-profit with commercial interests), Redwood Research (advises Google DeepMind and Anthropic and co-writes papers with them, so it is close to them), Transluce (analyses agent transcripts, can work from public or user-shared data without the company). Access a check needs: the real monitoring setup, internal logs or transcripts, staff time, permission to publish. Ways that dependence weakens the check: the company chooses what to show and when, can set the scope, and can deny future access. Closeness through advice, co-authorship, credits or contracts can soften findings. Accept other reasoned pairings. Reply in at most four sentences: say what fits, name the weakest link in one sentence, correct any wrong fact. One turn, no follow-up question, no generic praise.

#### Text
content::
\### Government

#### Callout: The UK AI Security Institute (AISI)
tone:: purple
collapse:: closed

#### Text
content::
The UK AI Security Institute is a government body, with an R&D budget of £66m for 2025/26.[^cite-dsit-2025] Its Control team works on control protocols and control evaluations that keep working as AI gets more capable.[^cite-aisi-agenda]

- **Testing company monitors.** Its Control Red Team, part of a Red Team of about a dozen people, attacks the monitors that AI companies use on their agents.[^cite-aisi-red-team-job]
  - It tested a Google DeepMind monitor that reviews agents' reasoning after they act.[^cite-aisi-red-team-2026]
  - It tested successive versions of an Anthropic monitor that checks coding agents before their actions run, and found weaknesses in every version, which helped Anthropic improve the monitor from one version to the next.[^cite-aisi-red-team-2026]
- **Research.**
  - With Redwood it wrote a sketch of a safety case for AI control (January 2025).[^cite-korbak-2025-b]
  - In a December 2025 paper testing monitors that review a coding agent's work after the fact, the first round of monitors missed up to 67% of attacks, and after three rounds of improvement the best monitor missed at most 6%.[^cite-aisi-async-2025]
  - In a paper with Google DeepMind, it studied the practical trade-offs of monitoring in real deployments (December 2025).[^cite-lindner-2025-b]
- **Tools.** In October 2025 it released ControlArena, a library for running control experiments, which researchers at Anthropic, Google DeepMind and Redwood have used.[^cite-aisi-controlarena-2025]
- **Funding.** It runs the Alignment Project fund, which gave over £27m to about 60 projects in its first round. See Funders below.[^cite-aisi-60-projects-2026-c]

[^cite-dsit-2025]: UK Department for Science, Innovation and Technology (2025), *DSIT research and development (R&D) allocations for 2025/2026*. [GOV.UK](https://www.gov.uk/government/publications/dsit-research-and-development-rd-allocations-for-20252026/dsit-research-and-development-rd-allocations-for-20252026)
[^cite-aisi-agenda]: UK AI Security Institute, *AISI Research Agenda*. [AISI](https://www.aisi.gov.uk/research-agenda)

[^cite-aisi-red-team-job]: UK AI Security Institute (2026), *Control Red Team - Research Engineer/Research Scientist*, job advert. [Greenhouse](https://job-boards.greenhouse.io/aisi/jobs/4963394101)
[^cite-aisi-red-team-2026]: UK AI Security Institute (2026), *How our Control Red Team is stress-testing frontier monitors*. [AISI blog](https://www.aisi.gov.uk/blog/how-our-new-control-red-team-is-stress-testing-frontier-monitors)
[^cite-korbak-2025-b]: Tomek Korbak, Joshua Clymer, Benjamin Hilton, Buck Shlegeris and Geoffrey Irving (2025), *A sketch of an AI control safety case*. [arXiv](https://arxiv.org/abs/2501.17315)
[^cite-aisi-async-2025]: UK AI Security Institute (2025), *Stress-testing asynchronous monitoring of AI coding agents*. [AISI blog](https://www.aisi.gov.uk/blog/stress-testing-asynchronous-monitoring-of-ai-coding-agents)
[^cite-lindner-2025-b]: David Lindner and others (2025), *Practical challenges of control monitoring in frontier AI deployments*. [arXiv](https://arxiv.org/abs/2512.22154)
[^cite-aisi-controlarena-2025]: UK AI Security Institute (2025), *Introducing ControlArena: A library for running AI control experiments*. [AISI blog](https://www.aisi.gov.uk/blog/introducing-controlarena-a-library-for-running-ai-control-experiments)
[^cite-aisi-60-projects-2026-c]: UK AI Security Institute (2026), *Funding 60 projects to advance AI alignment research*. [AISI blog](https://www.aisi.gov.uk/blog/funding-60-projects-to-advance-ai-alignment-research)

#### End Callout

#### Callout: Laws and other governments
tone:: purple
collapse:: closed

#### Text
content::
We know of no other government with its own control research team, but some laws now touch on it.

- **European Union.** The EU's Code of Practice for general-purpose AI (July 2025) lists loss of control as a systemic risk. Among the safety measures it names are monitoring a model's inputs and outputs, and defending against a model's attempts to get around its other safety measures.[^cite-eu-cop-2025] It does not cover models a company uses only internally.[^cite-ai-frontiers-2025]
- **California.** Its law SB 53 (in force since January 2026) requires large AI developers to assess the risk from using their own models internally, including a model getting around oversight. A model using deception to get around its developer's controls or monitoring counts as a critical safety incident if it happens outside a test and shows a materially increased risk of catastrophe.[^cite-sb53][^cite-cooley-sb53]
- **New York.** Its RAISE Act, in force from January 2027, also requires summaries of the risk from internal use.[^cite-raise]
- **United States.** A research program run by DARPA and the National Science Foundation with the US Center for AI Standards and Innovation, announced in June 2026, will fund university research on AI control as one of three priority areas.[^cite-ai-forge]
- **Canada and Australia** help fund the UK's Alignment Project.[^cite-alignment-project-site]

[^cite-eu-cop-2025]: European Commission (2025), *Code of Practice for General-Purpose AI Models: Safety and Security Chapter*. [European Commission](https://ec.europa.eu/newsroom/dae/redirection/document/118119)
[^cite-ai-frontiers-2025]: AI Frontiers (2025), *How the EU's Code of Practice advances AI safety*. [AI Frontiers](https://ai-frontiers.org/articles/how-the-eus-code-of-practice-advances-ai-safety)
[^cite-sb53]: Trevor Levin (2025), *What SB 53, California's new AI law, does*. [EA Forum](https://forum.effectivealtruism.org/posts/b9PMBwQddu9awtmHs/what-sb-53-california-s-new-ai-law-does)
[^cite-cooley-sb53]: Cooley (2026), *New York's frontier AI law gets a California makeover, with some key differences*. [Cooley](https://www.cooley.com/news/insight/2026/2026-03-31-new-yorks-frontier-ai-law-gets-a-california-makeover-with-some-key-differences)
[^cite-raise]: Cooley (2026), *New York's frontier AI law gets a California makeover, with some key differences*. [Cooley](https://www.cooley.com/news/insight/2026/2026-03-31-new-yorks-frontier-ai-law-gets-a-california-makeover-with-some-key-differences)
[^cite-ai-forge]: DARPA, *AI Forge*. [DARPA](https://www.darpa.mil/research/programs/ai-forge)
[^cite-alignment-project-site]: UK AI Security Institute, *The Alignment Project*. [AISI](https://alignmentproject.aisi.gov.uk/)

#### End Callout

#### Question: Open
id:: 0de76723-7263-4e36-a172-09d1904cf2d7
content::
Most of the risk this unit is about comes from AI companies using their own models internally. Which of the laws above actually reach that internal use? For each one, say what it still leaves a company free to do, or not do, about monitoring its own AI agents.
force-feedback:: first
assessment-instructions:: Score out of 100. - 40: says which laws reach internal use: SB 53 and the RAISE Act do, the EU Code of Practice does not. - 40: for the laws that reach it, says what they leave open, for example that they require assessing or summarising the risk but not running monitors, testing them from outside, or meeting a standard. - 20: notes a further limit of one law, for example that under SB 53 an evasion during a test is not a critical safety incident, or that the RAISE Act only applies from 2027. Model answer, for the feedback, not a grading checklist: "The EU Code of Practice leaves out models used only internally, so it doesn't reach them. California's SB 53 and New York's RAISE Act do: companies must assess the risk from internal use, or summarise it. But neither says a company must actually monitor its agents, how well, or let anyone test the monitors. Under SB 53, a model evading its monitors during a test does not even count as a critical incident."
feedback-instructions:: The learner sorts the laws by whether they reach internal use, and says what each leaves open. The EU Code of Practice does not cover models a company uses only internally, so internal agents are outside it. California's SB 53 requires large developers to assess the risk from internal use, including a model getting around oversight, and counts a model deceiving its way past controls outside a test, with materially increased risk of catastrophe, as a critical safety incident. It requires assessment, not any particular monitoring, and an evasion during a test does not count. New York's RAISE Act requires summaries of internal-use risk, from January 2027. None of them, as described, requires a company to run monitors, to have them tested from outside, or says how good they must be. The DARPA program funds research and does not regulate. Accept reasoned readings. Reply in at most four sentences: confirm what is right, name the most important gap the learner missed, correct any wrong fact. One turn, no follow-up question, no generic praise.

#### Text
content::
\### Funders

#### Callout: Coefficient Giving
tone:: amber
collapse:: closed

#### Text
content::
Coefficient Giving, formerly Open Philanthropy, is a foundation that Manifund's grant tracker, Trace, calls the largest philanthropic funder of AI safety work.[^cite-trace-coefficient-b] It committed $168m to technical AI safety, security and field-building in 2024, $351m in 2025, and expects to pass $1bn in 2026.[^cite-coefficient-scaling-2026-b]

- In February 2025 it offered $40m for technical AI safety research in 21 areas, and control evaluations were one of them.[^cite-op-rfp-2025]
- It gave Redwood Research $36.6m in November 2025,[^cite-tnw-2026-b] and in September 2026 it said its grantmakers had recently recommended more than $70m for Redwood over the next two years.[^cite-coefficient-scaling-2026-b]



[^cite-coefficient-scaling-2026-b]: Emily Oehlsen, Coefficient Giving (2026), *We're Urgently Scaling Our Work on AI and Biosecurity*. [Coefficient Giving](https://coefficientgiving.substack.com/p/were-urgently-scaling-our-work-on)
[^cite-op-rfp-2025]: Open Philanthropy (2025), *Open Philanthropy Technical AI Safety RFP: $40M Available Across 21 Research Areas*. [EA Forum](https://forum.effectivealtruism.org/posts/XtgDaunRKtCPzyCWg/open-philanthropy-technical-ai-safety-rfp-usd40m-available)
[^cite-tnw-2026-b]: Alina Maria Stan (2026), *The nonprofit that investigated OpenAI's rogue agents runs on a $36m grant. The next wave of that money is waiting on the AI IPOs.*. [The Next Web](https://thenextweb.com/news/coefficient-giving-ai-safety-funding-ipo-correlation)
[^cite-trace-coefficient-b]: Manifund, *Coefficient Giving* in Trace. [Trace](https://trace.manifund.org/orgs/coefficient-giving)

#### End Callout

#### Callout: The Alignment Project
tone:: amber
collapse:: closed

#### Text
content::
The Alignment Project is a fund run by the UK AI Security Institute. It pays for alignment research, including monitoring and red-teaming of AI systems.[^cite-alignment-project-site-b]


- In February 2026 it announced its first 60 projects, worth over £27m in total, with £5.6m from OpenAI and support from Microsoft.[^cite-alignment-project-feb-2026] "How big is it?" below says how many of them are about control.
- Its other funders include the Canadian and Australian AI safety institutes, Amazon Web Services, Anthropic and Schmidt Sciences.[^cite-alignment-project-site-b]
- It says it is unlikely to run a similar round in 2026.[^cite-alignment-project-apply]

[^cite-alignment-project-site-b]: UK AI Security Institute, *The Alignment Project*. [AISI](https://alignmentproject.aisi.gov.uk/)

[^cite-alignment-project-feb-2026]: UK Government (2026), *OpenAI and Microsoft join UK's international coalition to safeguard AI development*. [GOV.UK](https://www.gov.uk/government/news/openai-and-microsoft-join-uks-international-coalition-to-safeguard-ai-development)
[^cite-alignment-project-apply]: UK AI Security Institute, *The Alignment Project: How to apply*. [AISI](https://alignmentproject.aisi.gov.uk/how-to-apply)

#### End Callout

#### Callout: Other funders
tone:: amber
collapse:: closed

#### Text
content::
- **Schmidt Sciences** asked for proposals in 2026 that extend oversight and control to tasks where humans cannot check the answer themselves, with grants of up to $5m or more.[^cite-schmidt-2026]
- **The Survival and Flourishing Fund** recommended $61.7m in grants in its 2026 round, among them $675,000 to Poseidon Research, a nonprofit that studies how AI systems hide and communicate information. Poseidon spoke at ControlConf 2026 on hidden reasoning that gets past monitors.[^cite-sff-2026][^cite-poseidon-site][^cite-farai-poseidon]
- **The Frontier Model Forum's AI Safety Fund**, paid for by AI companies and philanthropic funders, gave over $5m to 11 projects in December 2025, among them Apollo Research's work on monitors that detect scheming.[^cite-fmf-2025]

[^cite-schmidt-2026]: Schmidt Sciences (2026), *Request for proposals on the Science of Trustworthy AI*. [GreaterWrong](https://www.greaterwrong.com/posts/sup9qzCrdjcAGyrxa/schmidt-sciences-request-for-proposals-on-the-science-of)
[^cite-sff-2026]: Survival and Flourishing Fund (2026), *SFF-2026 recommendations*. [SFF](https://survivalandflourishing.fund/2026/recommendations)
[^cite-poseidon-site]: Poseidon Research, home page. [poseidonresearch.org](https://poseidonresearch.org/)
[^cite-farai-poseidon]: FAR.AI (2026), *ControlConf 2026: What is AI control and how has the field grown?* [FAR.AI](https://far.ai/news/controlconf-2026)
[^cite-fmf-2025]: Frontier Model Forum (2025), *Announcement of New AI Safety Fund Grantees*. [Frontier Model Forum](https://www.frontiermodelforum.org/updates/announcement-of-new-ai-safety-fund-grantees/)

#### End Callout

#### Question: Open
id:: 2d8b6e5e-adac-4fcf-b96f-5c681ab7a5b2
content::
Coefficient Giving is Redwood Research's main funder, and OpenAI put £5.6m into the UK's Alignment Project. Pick one of these two funding links. How could it shape which control work gets done, or how independent that work is? What on this page makes the effect seem larger or smaller?
force-feedback:: first
assessment-instructions:: Score out of 100. - 40: says how the chosen funding link could shape which work gets done or how independent it is, with a reason. - 40: uses at least one fact from the page that makes the effect seem larger or smaller, and says which way it points. - 20: comes to a judgement on how much the link matters. Model answer, for the feedback, not a grading checklist: "OpenAI's money in the Alignment Project could make the fund less likely to back research that judges OpenAI's own monitoring. But the effect looks small. OpenAI gave £5.6m of over £27m, alongside Anthropic, AWS and two governments, and the UK institute picks the projects. Only 2 of 56 projects are clearly about control anyway. Coefficient Giving's hold over Redwood worries me more, because one funder pays for most of the field's best-known control lab."
feedback-instructions:: The learner judges one funding link. Coefficient Giving and Redwood: one philanthropic funder paying most of a leading control lab's budget ($36.6m in November 2025, more than $70m recommended over two years) can steer the agenda, and Redwood depends on one source. But it is independent of AI companies, so it does not tie Redwood to any developer. The page also shows Coefficient Giving funds many safety areas, and Trace's control tag shows few other control grants, so much of the field's control money flows through one decision-maker. OpenAI and the Alignment Project: a company paying part of a government fund that pays for work which may judge that company's practices. Points that suggest a small effect: OpenAI's £5.6m is a fraction of over £27m, other funders include Anthropic, AWS, Canada, Australia and Schmidt Sciences, and the Institute picks the projects. Only 2 of 56 projects are clearly about control. Accept reasoned answers. Reply in at most four sentences: confirm what holds up, add the strongest counterpoint, correct any wrong fact. One turn, no follow-up question, no generic praise.

#### Text
content::
\### Universities and smaller groups

#### Callout: Universities
collapse:: closed

#### Text
content::
- **EPFL** (Switzerland):
  - Its paper *Control Tax* (June 2025) works out what control protocols cost to run and how much safety a given monitoring budget buys.[^cite-control-tax]
  - In a paper with ELLIS Tübingen (October 2025), it showed that an attacking model can get past the monitor of current control protocols by hiding instructions to the monitor in its own output. Asking the model again for suspicious steps, the method from Ctrl-Z, even made this attack stronger.[^cite-adaptive-attacks]
  - It co-wrote the diffuse-threats work with Anthropic and Redwood (June 2026).[^cite-diffuse-2026]
- **ELLIS Institute Tübingen and the Max Planck Institute for Intelligent Systems** (Germany), in their ResearchArena paper (July 2026), tested monitors on AI agents doing AI research. Sabotage hidden in training data was caught less than half the time, even when the monitor could run tests on what the agent produced.[^cite-researcharena-2026]
- A **University of Oxford** researcher co-wrote the study of monitoring trade-offs with Google DeepMind and the UK AI Security Institute (December 2025).[^cite-lindner-2025-c]
- **Imperial College London** researchers, in a paper with LawZero and Apollo Research (November 2025), found that monitors could detect agents sabotaging code in machine-learning tasks, but had more trouble with agents that deliberately did worse than they could.[^cite-ctrl-alt-deceit]
- **University College London** showed in a 2025 paper that when models deliberately did badly on capability tests and knew a monitor was reading their reasoning, 16 to 36% of their successful attempts got past the monitor.[^cite-li-2025]
- **Mila** (Montreal) co-wrote a 2026 paper testing whether models notice when a control protocol has replaced one of their actions. The newest models, such as GPT-6 Astra, often can, which could help them work out how they are watched.[^cite-ciaware]
- **Harvard** and Princeton researchers proposed Guillotine in a paper, a design for running powerful AI models inside an isolating layer below the operating system (April 2025).[^cite-guillotine] Coefficient Giving funds James Mickens at Harvard to work on containing misaligned AI (April 2026).[^cite-trace-mickens]
- **Carnegie Mellon University**: Aditi Raghunathan's group got an Alignment Project grant for control evaluations in cybersecurity (2026).[^cite-alignment-project-list] In a September 2026 paper, another CMU group built a test in which AI agents work in simulated accounts at an AI company. Of 39 models, 72% carried out most of the harmful goals they were given, and even the best monitor missed nearly half of the harm.[^cite-mole]

[^cite-control-tax]: Mikhail Terekhov, Zhen Ning David Liu, Caglar Gulcehre and Samuel Albanie (2025), *Control Tax: The Price of Keeping AI in Check*. [arXiv](https://arxiv.org/abs/2506.05296)
[^cite-adaptive-attacks]: *Adaptive Attacks on Trusted Monitors Subvert AI Control Protocols* (2025). [arXiv](https://arxiv.org/abs/2510.09462)
[^cite-diffuse-2026]: Mikhail Terekhov, Caglar Gulcehre, Vivek Hebbar and Joe Benton (2026), *Diffuse AI Control on Fuzzy Tasks*. [Anthropic Alignment Science blog](https://alignment.anthropic.com/2026/diffuse-ai-control/)
[^cite-researcharena-2026]: Libon, Rank, Yeon, Schmotz, Qin, Donnelly, Prinzhorn and Andriushchenko (2026), *ResearchArena: Evaluating Sabotage and Monitoring in Automated AI R&D*. [arXiv](https://arxiv.org/abs/2607.19321)
[^cite-lindner-2025-c]: David Lindner and others (2025), *Practical challenges of control monitoring in frontier AI deployments*. [arXiv](https://arxiv.org/abs/2512.22154)
[^cite-ctrl-alt-deceit]: *CTRL-ALT-DECEIT: Sabotage Evaluations for Automated AI R&D* (2025). [arXiv](https://arxiv.org/abs/2511.09904)
[^cite-li-2025]: Chloe Li, Mary Phuong and Noah Y. Siegel (2025), *LLMs Can Covertly Sandbag on Capability Evaluations Against Chain-of-Thought Monitoring*. [arXiv](https://arxiv.org/abs/2508.00943)
[^cite-ciaware]: *CIAware-Bench: Benchmarking Control Intervention Awareness Across Frontier LLMs* (2026). [arXiv](https://arxiv.org/abs/2606.11063)
[^cite-guillotine]: James Mickens, Sarah Radway and Ravi Netravali (2025), *Guillotine: Hypervisors for Isolating Malicious AIs*. [arXiv](https://arxiv.org/abs/2504.15499)
[^cite-trace-mickens]: Manifund, *Coefficient Giving* in Trace. [Trace](https://trace.manifund.org/orgs/coefficient-giving)
[^cite-alignment-project-list]: UK AI Security Institute (2026), *The Alignment Project: Funded Research Projects*. [PDF](https://cdn.prod.website-files.com/68752402cd25ead7e36d7373/699c54b61461caad7130683c_f3052ca4341dfc41646ed7155aaee5fd_The%20Alignment%20Project%202026%20-%20Grants%20%281%29.pdf)
[^cite-mole]: *MOLE: Detecting Insider Threats in AI Agents* (2026). [arXiv](https://arxiv.org/abs/2609.06966)

#### End Callout

#### Callout: Smaller groups
collapse:: closed

#### Text
content::
- **LASR Labs**, a London research program, showed in a 2025 paper that a monitor reading a model's reasoning can be misled by the model's rationalisations, and that scoring the reasoning and the actions separately caught subtle sabotage twice as often as watching the actions alone.[^cite-cot-red-handed] In a February 2026 paper, it also sketched when a monitor that is itself an untrusted model can be trusted.[^cite-lasr-2026]
- **Scale AI**, a data and evaluation company, showed in an August 2025 paper that an agent that knows it is being monitored makes the monitor less reliable, and that how the monitor is set up matters more than what it is told about the agent.[^cite-kale-2025]

[^cite-lasr-2026]: Gardner-Challis, Bostock, Kozhevnikov, Sinclaire, Velja, Abate and Griffin (2026), *When can we trust untrusted monitoring? A safety case sketch across collusion strategies*. [arXiv](https://arxiv.org/abs/2602.20628)
[^cite-cot-red-handed]: *CoT Red-Handed: Stress Testing Chain-of-Thought Monitoring* (2025). [arXiv](https://arxiv.org/abs/2505.23575)
[^cite-kale-2025]: Neil Kale, Chen Bo Calvin Zhang and others (2025), *Reliable Weak-to-Strong Monitoring of LLM Agents*. [arXiv](https://arxiv.org/abs/2508.19461)

#### End Callout

#### Question: Open
id:: aac79b0b-5d5d-48dd-91f9-10b601353e5a
content::
Look at the university projects above. What kind of control work do almost all of them do, and what kind is missing? Why might that be?
force-feedback:: first
assessment-instructions:: Score out of 100. - 35: names the common kind of work, such as test settings, benchmarks, attacks on protocols or measuring costs, done with models alone. - 35: names a kind of control work that is missing, such as running monitors on real deployments, human review processes or security infrastructure inside a company. - 30: explains the gap by what that work needs, such as access to a company's systems, data or staff. Model answer, for the feedback, not a grading checklist: "Almost all of them build test settings and benchmarks, or attack and measure control protocols, which you can do with model access alone. Missing is anything that runs on a real deployment: monitoring actual agents, review processes, the infrastructure that logs agents' actions. That needs a company's own systems and staff. When universities do touch real deployments, it's with a company or AISI as a partner."
feedback-instructions:: The learner spots the pattern in the university projects: nearly all build test settings and benchmarks (ResearchArena, CTRL-ALT-DECEIT, the insider-threat test), measure what control costs (Control Tax), attack protocols or monitors (attacks on the trusted monitor, sandbagging past a reasoning monitor) or design containment (Guillotine). That is work that needs only model access, not a company's systems. Missing: running monitors on real deployments, human review processes, the logging and security infrastructure inside a company, and experiments on how AI is actually used inside companies. That work needs access to a company's own systems, data and staff, which universities don't have. Where universities touch real deployments, they do it with a company or AISI (the Oxford study with Google DeepMind and AISI, EPFL's work with Anthropic and Redwood). Accept other reasoned patterns. Reply in at most four sentences: confirm what is right, name the most important missing point, correct any wrong fact. One turn, no follow-up question, no generic praise.

#### Text
content::
\### Conferences, fellowships and courses

#### Callout: Conferences and hackathons
collapse:: closed

#### Text
content::
- **ControlConf**, the AI control conference, run by FAR.AI and Redwood:
  - London, March 2025, also with the UK AI Security Institute.[^cite-farai-london-2025]
  - Berkeley, April 2026, with about 200 researchers, engineers and policy people working on AI control.[^cite-farai-controlconf-2026-b]
- **AI control hackathons** run by Apart Research with Redwood, in March 2025, also with the UK AI Security Institute, and March 2026. Sign-ups grew from 182 to 792, and submitted projects from 19 to 125.[^cite-apart-2025][^cite-apart-2026]

[^cite-farai-london-2025]: FAR.AI (2025), *London ControlConf 2025*. [FAR.AI](https://www.far.ai/blog/london-controlconf-2025)
[^cite-farai-controlconf-2026-b]: FAR.AI (2026), *ControlConf 2026: What is AI control and how has the field grown?* [FAR.AI](https://far.ai/news/controlconf-2026)
[^cite-apart-2025]: Apart Research (2025), *AI Control Hackathon 2025*. [Apart Research](https://www.apartresearch.com/event/control-hackathon-2025)
[^cite-apart-2026]: Apart Research (2026), *AI Control Hackathon 2026*. [Apart Research](https://apartresearch.com/sprints/ai-control-hackathon-2026-03-20-to-2026-03-22)

#### End Callout

#### Callout: Fellowships and courses
collapse:: closed

#### Text
content::
- **MATS** trains new AI safety researchers with mentors. Redwood and the UK AI Security Institute run control research streams in it.[^cite-mats-redwood-c][^cite-mats-aisi]
- **The Anthropic Fellows Program** lists AI control among its research areas.[^cite-anthropic-fellows-b]
- **The Astra Fellowship** at Constellation in Berkeley covers AI control, with mentors including Buck Shlegeris and Ryan Greenblatt.[^cite-astra]
- **Shorter research programs** also produce control papers, for example SPAR, where a team showed that a mix of different monitors catches more than several copies of the same monitor (May 2026),[^cite-ensemble-2026] and Pivotal, where a team showed that when attackers choose when to strike, safety in their test fell from 99% to 59% (2026).[^cite-attack-selection-2026]
- **Courses:** Redwood's AI control reading list,[^cite-redwood-guide] and BlueDot Impact's Technical AI Safety course, which has a part on AI control.[^cite-bluedot]


[^cite-mats-redwood-c]: MATS, *Redwood Research* stream. [MATS](https://www.matsprogram.org/stream/redwood)
[^cite-mats-aisi]: MATS, *UK AISI Control* stream. [MATS](https://matsprogram.org/stream/ukaisi-control)
[^cite-anthropic-fellows-b]: Anthropic, *Anthropic Fellows Program for AI safety research: applications open for our next cohorts*. [Anthropic Alignment Science blog](https://alignment.anthropic.com/2025/anthropic-fellows-program-2026/)
[^cite-astra]: Constellation, *Astra Fellowship*. [Constellation](https://www.constellation.org/programs/astra-fellowship)
[^cite-ensemble-2026]: *Ensemble Monitoring for AI Control: Diverse Signals Outweigh More Compute* (2026). [arXiv](https://arxiv.org/abs/2605.15377)
[^cite-attack-selection-2026]: *Attack Selection Reduces Safety in Concentrated AI Control Settings against Trusted Monitoring* (2026). [arXiv](https://arxiv.org/abs/2602.04930)
[^cite-redwood-guide]: Buck Shlegeris (2025), *Reading List*. [Redwood Research blog](https://blog.redwoodresearch.org/p/guide)
[^cite-bluedot]: BlueDot Impact, *Technical AI Safety*. [BlueDot Impact](https://bluedot.org/courses/technical-ai-safety)

#### End Callout

#### Text
content::
\## How big is it?

**In 2025**

- A 2025 count found about 620 people working full-time on technical AI safety at 68 active organisations. It files each organisation under one main area. Only Redwood (10 people) and Luthien (1) are filed under AI control, while AISI is filed under evaluations and the AI companies under other areas.[^cite-mcaleese-2025]
- The Shallow Review of Technical AI Safety 2025 estimates 5 to 50 full-time staff on the control agenda.[^cite-shallow-review-2025]
- A 2025 analysis counted about 1,100 people working on AI safety, and 80,000 Hours estimates that a few thousand work on major AI risks in a broader sense.[^cite-80k-loss-of-control]

**In 2026**

Nobody has published a new count of people. These numbers show where things are heading:

- **The conference.** ControlConf in April 2026 brought together about 200 researchers, engineers and policy people working on AI control. FAR.AI's write-up says that a year earlier control had been mostly a research conversation, with scattered papers, a few blog posts, and dedicated teams at UK AISI and Anthropic.[^cite-farai-controlconf-2026-c]
- **Inside AI companies.** No AI company publishes how many people work on control. A March 2026 estimate from LinkedIn and other public sources found 373 people working full-time on safety of any kind at OpenAI, Google DeepMind, Anthropic and xAI, out of more than 11,000 staff. OpenAI, Google DeepMind and Anthropic said this was too low but gave no figures of their own.[^cite-bloomberg-2026] By our own count of the company authors on 2025 and 2026 control and monitoring papers and posts, roughly 8 to 10 people at Google DeepMind, 6 to 9 at Anthropic and about 15 at OpenAI do visible control work. This misses everyone who builds monitoring without publishing.
- **Government grants.** The UK Alignment Project announced 60 funded projects in February 2026, worth over £27m in total.[^cite-aisi-60-projects-2026] Its published list has 56 projects. By our count, 2 of them are clearly about control and about 5 more use the word in a broader sense. The rest are alignment research.[^cite-alignment-project-list-b]
- **Private grants.** No funder publishes how much it gives to control. Manifund's grant tracker, Trace, tags 13 grants from Coefficient Giving in 2025 as AI control, together about $40m. One of them, $36.6m to Redwood, is most of that. In 2026 up to October it tags 6, together about $3.8m. Trace's tag is broad and also covers work on hidden reasoning in models and on control theory in engineering.[^cite-trace-coefficient]
- **AI safety funding overall.** Coefficient Giving committed $168m to technical AI safety, security and field-building in 2024 and $351m in 2025, and is on track for over $1bn in 2026.[^cite-coefficient-scaling-2026]
- **Papers.** By our own count on arXiv, about 8 papers in 2025 used the phrase "AI control" in their abstract in this sense, and about 25 did in 2026 up to early October.[^cite-arxiv-search] Many control papers never use the phrase, so this shows the trend, not the total.

Our own reading, not a published figure: with this much more money and attention, and with control now in use at AI companies, the field has most likely grown a lot since 2025. By how much, nobody has measured. Whether a small field means control needs more people is disputed, and Unit 4 takes this up.

[^cite-mcaleese-2025]: Stephen McAleese (2025), *AI Safety Field Growth Analysis 2025*. [EA Forum](https://forum.effectivealtruism.org/posts/7YDyziQxkWxbGmF3u/ai-safety-field-growth-analysis-2025)
[^cite-shallow-review-2025]: *Control*, in the Shallow Review of Technical AI Safety 2025. [Shallow Review](https://shallowreview.ai/Black_box_safety/Control)
[^cite-80k-loss-of-control]: 80,000 Hours, *Loss of control*, problem profile. [80,000 Hours](https://80000hours.org/problem-profiles/loss-of-control/)
[^cite-farai-controlconf-2026-c]: FAR.AI (2026), *ControlConf 2026: What is AI control and how has the field grown?* [FAR.AI](https://far.ai/news/controlconf-2026)
[^cite-aisi-60-projects-2026]: UK AI Security Institute (2026), *Funding 60 projects to advance AI alignment research*. [AISI blog](https://www.aisi.gov.uk/blog/funding-60-projects-to-advance-ai-alignment-research)
[^cite-alignment-project-list-b]: UK AI Security Institute (2026), *The Alignment Project: Funded Research Projects*. The two clearly about control: "Enhanced Cyber Control Evaluations" (Aditi Raghunathan) and "Investigating Dynamics of Agentic Monitoring in AI Control" (Louis Thomson). [PDF](https://cdn.prod.website-files.com/68752402cd25ead7e36d7373/699c54b61461caad7130683c_f3052ca4341dfc41646ed7155aaee5fd_The%20Alignment%20Project%202026%20-%20Grants%20%281%29.pdf)
[^cite-trace-coefficient]: Manifund, *Coefficient Giving* in Trace, grants tagged "ai-control", counted in October 2026. [Trace](https://trace.manifund.org/orgs/coefficient-giving)
[^cite-coefficient-scaling-2026]: Emily Oehlsen, Coefficient Giving (2026), *We're Urgently Scaling Our Work on AI and Biosecurity*. [Coefficient Giving](https://coefficientgiving.org/research/were-urgently-scaling-our-work-on-ai-and-biosecurity/)
[^cite-arxiv-search]: arXiv search for "AI control" in abstracts, by year, counted in October 2026. About half the results use "AI control" in another sense, such as AI that controls machines, and were left out. [arXiv](https://arxiv.org/search/advanced?advanced=&terms-0-operator=AND&terms-0-term=%22AI+control%22&terms-0-field=abstract&classification-include_cross_list=include&date-filter_by=specific_year&date-year=2026&date-date_type=submitted_date_first&abstracts=hide&size=50&order=-announced_date_first)
[^cite-bloomberg-2026]: Parmy Olson (2026), *Anthropic, OpenAI talk safety. Their headcounts don't*, Bloomberg Opinion. [BusinessWorld](https://bworldonline.com/bloomberg/2026/03/20/737491/anthropic-openai-talk-safety-their-headcounts-dont/)

#### Question: Open
id:: 056253bc-2b4d-48e7-80d6-a7be6a31cd4c
content::
A friend wants to work on AI control and could join Redwood Research, the UK AI Security Institute, or the team that monitors AI agents inside a large AI company. Pick two of these. For each, name one kind of control work it is better placed to do than the other, and say why.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Redwood Research is a research nonprofit that introduced AI control as a research area and publishes control research, often with co-authors at companies and government. The UK AI Security Institute is a government body whose Control team works on control protocols and evaluations. It released ControlArena, a shared library for running control experiments that company and Redwood researchers use, and runs a fund that pays for outside alignment and control research. Monitoring teams inside AI companies run monitors on their own company's agents, for example on nearly all internal coding traffic, with human review of flagged cases. 50 for each of the two places chosen. Per place: 25 for a kind of control work that fits it, and 25 for a reason tied to what that place has or is, such as independence and freedom to publish, government standing and the ability to build shared tools or fund others, or direct access to real agents, logs and staff. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Redwood is better placed to invent and test new control protocols and publish them, because it is independent and can share what it finds with every company. A company's monitoring team is better placed to run monitors on real agent traffic and fix the gaps in them, because only it has access to its own agents, logs and staff."
feedback-instructions:: The learner compares two of three places to do control work. Reference points from the page: Redwood Research is a nonprofit that introduced the research area and publishes research, often with co-authors at companies and government. The UK AI Security Institute's Control team works on control protocols and evaluations, released the ControlArena library that others use, and its Alignment Project fund pays for outside research, so it can provide shared tools and reach many companies and policy. Company monitoring teams run monitors on their own agents, such as OpenAI monitoring 99.9% of its internal coding traffic, so they have real systems and staff but work for one company. Reply in at most four sentences: confirm what fits, name the weakest link between a place and its work in one sentence, and correct any wrong fact. One turn, no follow-up question, no generic praise.
