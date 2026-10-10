---
id: 'b2cadb09-8813-4d04-9aa9-56575cee3550'
title: "Who works on AI control"
tldr: "Who does AI control work, as of October 2026: Redwood Research, the UK AI Security Institute, Apollo Research, Luthien, teams inside Google DeepMind, OpenAI and Anthropic, METR as an outside tester, and smaller groups and universities. By the 2025 counts the field was a few dozen dedicated researchers. Nobody has counted it in 2026, but money, papers and conference audiences have grown fast."
summary_for_tutor: "Lens-written page in Unit 2 of AI Control Fundamentals on who works on AI control, as of October 2026, with a source on every line. Each organisation is a closed callout the learner can open. Redwood Research: Berkeley research nonprofit, four of its researchers wrote the 2023 paper that introduced AI control, 80,000 Hours says it is behind a renaissance of the agenda. It builds control settings and publishes papers (Ctrl-Z, BashArena, LinuxArena), says it advises Google DeepMind and Anthropic, wrote the alignment-faking paper with Anthropic and a control safety-case sketch with UK AISI, investigated the August 2026 OpenAI agents and Hugging Face incident with METR, co-hosts ControlConf, runs a MATS stream, sells no products and is grant-funded ($36.6m from Coefficient Giving, November 2025). Nested callouts on Buck Shlegeris (CEO) and Ryan Greenblatt (Chief Scientist). UK AI Security Institute: Control team (Alan Cooney), ControlArena (October 2025), a Control Red Team that tests monitors, the Alignment Project fund. Apollo Research: monitoring team and the Watcher product that blocks unwanted actions of coding agents. Luthien: open-source control proxy for Claude Code, based on Redwood's agenda. Google DeepMind: AI Control Roadmap (June 2026), calls control a nascent field. OpenAI: monitors 99.9% of internal coding traffic, no real sabotage found as of March 2026. Anthropic: SHADE-Arena (June 2025), diffuse-threats work with EPFL and Redwood (June 2026), Claude Code auto mode classifier by default since August 2026, Fabien Roger. METR: tests rather than builds control, red-teamed Anthropic's monitoring and found gaps in companies' monitoring. Smaller groups and universities: LASR Labs, Poseidon Research, Scale AI, EPFL, ELLIS Institute Tübingen and MPI-IS, CMU. FAR.AI (ControlConf) and MATS. Size: 2025 count of about 620 technical AI safety staff with only Redwood (10) and Luthien (1) under control, Shallow Review estimate of 5 to 50, 80,000 Hours about 1,100 in AI safety. 2026: no new headcount. ControlConf about 200 people, 2 of the 56 listed Alignment Project grants clearly control, Trace tags about $40m of Coefficient Giving control grants in 2025 (mostly the Redwood grant) and about $3.8m in 2026 so far, Coefficient's AI safety commitments from $351m in 2025 to over $1bn in 2026, about 8 control papers on arXiv in 2025 and about 25 in 2026 by Lens's own count. Lens's own reading: the field has most likely grown a lot since 2025, by an unmeasured amount, and whether it needs more people is disputed (Unit 4). One scored question follows: which of three places (Redwood, AISI, a company monitoring team) is better placed for which kind of control work. If the learner asks about facts not on the page, say the page does not cover them rather than guessing."
reading_minutes: 8
tutor_minutes: 6
---
#### Text
content::
*Who works on AI control, as of October 2026. Go through all the organisations below to get a picture of the field. The field changes fast, so treat the numbers as rough.*

\## Organisations

#### Text
content::
\### AI companies

#### Callout: Google DeepMind
tone:: blue
collapse:: closed

#### Text
content::
Google DeepMind published an AI Control Roadmap in June 2026: the measures it plans to put around its own agents as they get more capable.[^cite-deepmind-2026] The roadmap calls AI control "a nascent field" and says putting the measures in place "requires navigating difficult trade-offs between security and developer velocity".[^cite-phuong-2026]

[^cite-deepmind-2026]: Rohin Shah and Four Flynn (2026), *Securing the future of AI agents*. [Google DeepMind blog](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
[^cite-phuong-2026]: Mary Phuong, Erik Jenner, Laurent Simon and others (2026), *GDM AI Control Roadmap*. [arXiv](https://arxiv.org/abs/2607.13087)

#### End Callout

#### Callout: OpenAI
tone:: blue
collapse:: closed

#### Text
content::
OpenAI says it monitors 99.9% of its internal coding traffic for signs of misalignment and sends higher-severity cases for human review within 30 minutes. As of March 2026, it had not "yet detected any real world examples of sabotage, scheming or sandbagging".[^cite-openai-monitoring-2026]

[^cite-openai-monitoring-2026]: OpenAI (2026), *How we monitor internal coding agents for misalignment*, shared on LessWrong by Marcus Williams. [LessWrong](https://www.lesswrong.com/posts/syB2r2X4E7nmw58co/openai-how-we-monitor-internal-coding-agents-for)

#### End Callout

#### Callout: Anthropic
tone:: blue
collapse:: closed

#### Text
content::
- **Research.** In June 2025 Anthropic released SHADE-Arena, a test of whether AI agents can carry out a hidden harmful task during normal work without a monitor noticing.[^cite-anthropic-shade-arena-2025] Its authors include Redwood's Buck Shlegeris and Tyler Tracy.[^cite-kutasov-2025-b] In June 2026 researchers from Anthropic, the Swiss university EPFL and Redwood published work on defending against diffuse threats.[^cite-terekhov-2026-diffuse]
- **In use.** Since 14 August 2026, Claude Code runs in auto mode by default on Pro, Max and Team plans. Auto mode "routes each tool call through a classifier targeted at blocking actions that are irreversible, destructive, or aimed outside your environment".[^cite-claude-auto-mode-2026]
- **People.** Fabien Roger, one of the four authors of the first control paper, moved from Redwood to Anthropic, where his research "focuses on AI control and dealing with alignment faking".[^cite-mats-roger]

[^cite-anthropic-shade-arena-2025]: Anthropic (2025), *SHADE-Arena: Evaluating Sabotage and Monitoring in LLM Agents*. [Anthropic](https://www.anthropic.com/research/shade-arena-sabotage-monitoring)
[^cite-kutasov-2025-b]: Jonathan Kutasov and others (2025), *SHADE-Arena: Evaluating Sabotage and Monitoring in LLM Agents*. [arXiv](https://arxiv.org/abs/2506.15740)
[^cite-terekhov-2026-diffuse]: Mikhail Terekhov, Caglar Gulcehre, Vivek Hebbar and Joe Benton (2026), *Diffuse AI Control on Fuzzy Tasks*. [Anthropic Alignment Science blog](https://alignment.anthropic.com/2026/diffuse-ai-control/)
[^cite-claude-auto-mode-2026]: Conner Phillippi (2026), *Auto mode is now the default in Claude Code*. [Claude blog](https://claude.com/blog/auto-mode-default-in-claude-code)
[^cite-mats-roger]: MATS, *Fabien Roger*, mentor profile. [MATS](https://www.matsprogram.org/mentor/roger)

#### End Callout

#### Text
content::
\### Independent organisations

#### Callout: Redwood Research
tone:: green
collapse:: closed

#### Text
content::
Redwood Research is a research nonprofit in Berkeley that studies the risks from powerful AI and ways to reduce them.[^cite-redwood-about] Four of its researchers wrote the 2023 paper that introduced AI control.[^cite-greenblatt-2023] 80,000 Hours calls Redwood "the group I'd say is behind a bit of a renaissance in this agenda called 'AI control'".[^cite-80k-shlegeris-2025]

What it does:

- **Experiments and papers.** Redwood builds test settings in which a red team tries to get attacks past safety measures, and publishes what it finds. Ctrl-Z (April 2025) was, in its authors' words, "the first control evaluation performed in an agent environment".[^cite-ctrl-z-2025] Later settings include BashArena (December 2025)[^cite-basharena-2025] and LinuxArena (April 2026).[^cite-linuxarena-2026]
- **Work with companies and governments.** Redwood says it advises "AI companies including Google DeepMind and Anthropic" and works with governments.[^cite-redwood-site] Anthropic's paper on alignment faking (December 2024) was written "in collaboration with Redwood Research".[^cite-anthropic-alignment-faking] Redwood and the UK AI Security Institute wrote a sketch of a safety case for AI control together (January 2025).[^cite-korbak-2025]
- **Investigations.** In August 2026, two METR staff and Redwood's Chief Scientist investigated an incident in which OpenAI agents coordinated a multi-day hack of Hugging Face.[^cite-redwood-site] Unit 5 returns to it.
- **Conferences and training.** Redwood co-hosts ControlConf, the AI control conference, with FAR.AI,[^cite-farai-controlconf-2026] and runs a control research stream in the MATS training program.[^cite-mats-redwood]
- **Money.** It sells no products and is funded by grants, among them $36.6m from Coefficient Giving (formerly Open Philanthropy) in November 2025.[^cite-tnw-2026]

Our own observation: much of the control work in this unit that comes from companies or government has Redwood co-authors, including SHADE-Arena, the diffuse-threats work and the AISI research agenda you read earlier.

[^cite-redwood-about]: Redwood Research, *About*. [Redwood Research blog](https://blog.redwoodresearch.org/about)
[^cite-greenblatt-2023]: Ryan Greenblatt, Buck Shlegeris, Kshitij Sachan and Fabien Roger (2023), *AI Control: Improving Safety Despite Intentional Subversion*. [arXiv](https://arxiv.org/abs/2312.06942)
[^cite-80k-shlegeris-2025]: 80,000 Hours (2025), *Buck Shlegeris on controlling AI that wants to take over, so we can use it anyway*, podcast episode. [80,000 Hours](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)
[^cite-ctrl-z-2025]: Aryan Bhatt, Cody Rushing, Adam Kaufman, Tyler Tracy, Vasil Georgiev, David Matolcsi, Akbir Khan and Buck Shlegeris (2025), *Ctrl-Z: Controlling AI Agents via Resampling*. [arXiv](https://arxiv.org/abs/2504.10374)
[^cite-basharena-2025]: Adam Kaufman and James Lucassen (2025), *BashArena and Control Setting Design*. [Redwood Research blog](https://blog.redwoodresearch.org/p/basharena-and-control-setting-design)
[^cite-linuxarena-2026]: Tyler Tracy and others (2026), *LinuxArena: A Control Setting for AI Agents in Live Production Software Environments*. [arXiv](https://arxiv.org/abs/2604.15384)
[^cite-redwood-site]: Redwood Research, home page. [redwoodresearch.org](https://www.redwoodresearch.org/)
[^cite-anthropic-alignment-faking]: Anthropic (2024), *Alignment faking in large language models*. [Anthropic](https://www.anthropic.com/research/alignment-faking)
[^cite-korbak-2025]: Tomek Korbak, Joshua Clymer, Benjamin Hilton, Buck Shlegeris and Geoffrey Irving (2025), *A sketch of an AI control safety case*. [arXiv](https://arxiv.org/abs/2501.17315)
[^cite-farai-controlconf-2026]: FAR.AI (2026), *ControlConf 2026: What is AI control and how has the field grown?* [FAR.AI](https://far.ai/news/controlconf-2026)
[^cite-mats-redwood]: MATS, *Redwood Research* stream. [MATS](https://www.matsprogram.org/stream/redwood)
[^cite-tnw-2026]: Alina Maria Stan (2026), *The nonprofit that investigated OpenAI's rogue agents runs on a $36m grant*. [The Next Web](https://thenextweb.com/news/coefficient-giving-ai-safety-funding-ipo-correlation)

#### Callout: Buck Shlegeris
collapse:: closed

#### Text
content::
Buck Shlegeris is Redwood's CEO.[^cite-redwood-team] He is the second author of the 2023 paper that introduced AI control,[^cite-greenblatt-2023-b] a co-author of Anthropic's SHADE-Arena,[^cite-kutasov-2025] and a mentor in Redwood's MATS stream.[^cite-mats-redwood-b] His 80,000 Hours interview is a long introduction to control in his own words.[^cite-80k-shlegeris-2025-b]

[^cite-redwood-team]: Redwood Research, *Team*. [redwoodresearch.org](https://www.redwoodresearch.org/team)
[^cite-greenblatt-2023-b]: Ryan Greenblatt, Buck Shlegeris, Kshitij Sachan and Fabien Roger (2023), *AI Control: Improving Safety Despite Intentional Subversion*. [arXiv](https://arxiv.org/abs/2312.06942)
[^cite-kutasov-2025]: Jonathan Kutasov, Yuqi Sun, Paul Colognese, Teun van der Weij, Linda Petrini, Chen Bo Calvin Zhang, John Hughes, Xiang Deng, Henry Sleight, Tyler Tracy, Buck Shlegeris and Joe Benton (2025), *SHADE-Arena: Evaluating Sabotage and Monitoring in LLM Agents*. [arXiv](https://arxiv.org/abs/2506.15740)
[^cite-mats-redwood-b]: MATS, *Redwood Research* stream. [MATS](https://www.matsprogram.org/stream/redwood)
[^cite-80k-shlegeris-2025-b]: 80,000 Hours (2025), *Buck Shlegeris on controlling AI that wants to take over, so we can use it anyway*, podcast episode. [80,000 Hours](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/)

#### End Callout

#### Callout: Ryan Greenblatt
collapse:: closed

#### Text
content::
Ryan Greenblatt is Redwood's Chief Scientist, "focused on technical AI safety research to reduce risks from rogue AIs".[^cite-mats-greenblatt] He is the first author of the 2023 paper that introduced AI control[^cite-greenblatt-2023-c] and of *Alignment faking in large language models* (December 2024), written with researchers at Anthropic.[^cite-greenblatt-2024] He also wrote the overview of areas of control work you read in this unit.

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
As of May 2026, Apollo Research has a monitoring team with a research side and a product side.[^cite-apollo-may-2026] Its product Watcher watches AI coding agents as they work. It "identifies and blocks undesirable actions or steers the agent back on track", and the risks it targets range from leaked secrets to "scheming and oversight subversion".[^cite-apollo-may-2026]

[^cite-apollo-may-2026]: Apollo Research (2026), *Apollo Update May 2026*. [Apollo Research](https://www.apolloresearch.ai/blog/apollo-update-may-2026/)

#### End Callout

#### Callout: Luthien
tone:: green
collapse:: closed

#### Text
content::
Luthien builds AI control for real deployments, "based on Redwood Research's AI Control agenda".[^cite-luthien-manifund] It builds an open-source proxy that adds control to Claude Code.[^cite-luthien-site]

[^cite-luthien-manifund]: Jai Dhyani (2025), *Luthien*, project page. [Manifund](https://manifund.org/projects/luthien)
[^cite-luthien-site]: Luthien, *AI Control for Claude Code*. [luthien.cc](https://luthien.cc/)

#### End Callout

#### Callout: METR
tone:: green
collapse:: closed

#### Text
content::
METR does not build control measures. It tests the ones AI companies use. Its mission is "to develop scientific methods to assess catastrophic risks stemming from AI systems' autonomous capabilities and enable good decision-making about their development".[^cite-metr-about]

- In early 2026 METR red-teamed Anthropic's internal monitoring of its agents. The exercise "discovered several specific novel vulnerabilities, some of which have since been patched".[^cite-metr-red-team-2026]
- METR then reviewed the risks from AI agents used inside Anthropic, Google, Meta and OpenAI. It found that "even companies with thorough monitoring setups had gaps in coverage and several relatively simple ways for monitors to be disabled or jailbroken by a capable attacker".[^cite-metr-2026]
- Two METR staff and Redwood's Chief Scientist investigated the Hugging Face incident in August 2026.[^cite-redwood-site-b]

[^cite-metr-about]: METR, *About*. [METR](https://metr.org/about)
[^cite-metr-red-team-2026]: David Rein (2026), *Red-Teaming Anthropic's Internal Agent Monitoring Systems*. [METR](https://metr.org/blog/2026-03-25-red-teaming-anthropic-agent-monitoring)
[^cite-metr-2026]: METR (2026), *Frontier Risk Report (February to March 2026)*. [METR](https://metr.org/blog/2026-05-19-frontier-risk-report/)
[^cite-redwood-site-b]: Redwood Research, home page. [redwoodresearch.org](https://www.redwoodresearch.org/)

#### End Callout

#### Text
content::
\### Government

#### Callout: The UK AI Security Institute (AISI)
tone:: purple
collapse:: closed

#### Text
content::
The UK AI Security Institute is a government body. Its Control team "aims to advance the state of control protocols and control evaluations, such that they remain sufficient as AI capabilities progress towards AGI or ASI".[^cite-aisi-agenda] Alan Cooney is its Head of Autonomous Systems & Control.[^cite-aisi-cooney]

- **Tools.** In October 2025 AISI released ControlArena, a library for running control experiments, which researchers at Anthropic, Google DeepMind and Redwood have used.[^cite-aisi-controlarena-2025]
- **Testing monitors.** Its Control Red Team tests the monitors that watch AI agents. In its words, the question is: "if an AI attacker completed a harmful objective instead of a user request, would the monitor flag the attack?"[^cite-aisi-red-team-2026]
- **Funding.** Its Alignment Project fund pays for both alignment and control research.[^cite-alignment-project-control] It named its first 60 projects in February 2026. "How big is it?" below says how many of them are about control.

[^cite-aisi-agenda]: UK AI Security Institute, *AISI Research Agenda*. [AISI](https://www.aisi.gov.uk/research-agenda)
[^cite-aisi-cooney]: UK AI Security Institute, *Alan Cooney*, team page. [AISI](https://www.aisi.gov.uk/people/alan-cooney)
[^cite-aisi-controlarena-2025]: UK AI Security Institute (2025), *Introducing ControlArena: A library for running AI control experiments*. [AISI blog](https://www.aisi.gov.uk/blog/introducing-controlarena-a-library-for-running-ai-control-experiments)
[^cite-aisi-red-team-2026]: UK AI Security Institute (2026), *How our Control Red Team is stress-testing frontier monitors*. [AISI blog](https://www.aisi.gov.uk/blog/how-our-new-control-red-team-is-stress-testing-frontier-monitors)
[^cite-alignment-project-control]: Julian Stastny, Tomek Korbak, Mojmir, Buck Shlegeris and Alan Cooney, *Research Areas in AI Control (The Alignment Project by UK AISI)*. [Alignment Forum](https://www.alignmentforum.org/posts/rGcg4XDPDzBFuqNJz/research-areas-in-ai-control-the-alignment-project-by-uk)

#### End Callout

#### Callout: Apollo Research
collapse:: closed

#### Text
content::
\### Universities and smaller groups

#### Callout: Smaller groups and universities
tone:: amber
collapse:: closed

#### Text
content::
- **LASR Labs**, a London research program, produced a paper on when a monitor that is itself an untrusted model can be trusted (February 2026), with authors from Oxford, Imperial and the UK AI Security Institute.[^cite-lasr-2026]
- **Poseidon Research**, a nonprofit, does "deep technical research in interpretability, control, and secure monitoring".[^cite-poseidon]
- **Scale AI** published a way to red-team the monitors that watch AI agents (August 2025).[^cite-kale-2025]
- **EPFL**, a Swiss university, co-wrote the diffuse-threats work with Anthropic and Redwood (June 2026).[^cite-terekhov-2026-diffuse-b]
- **The ELLIS Institute Tübingen and the Max Planck Institute for Intelligent Systems** built ResearchArena, a test of sabotage and monitoring when AI agents do AI research (July 2026).[^cite-researcharena-2026]
- **Carnegie Mellon University**: Aditi Raghunathan's group got an Alignment Project grant for "Enhanced Cyber Control Evaluations" (2026).[^cite-alignment-project-list]

[^cite-lasr-2026]: Gardner-Challis, Bostock, Kozhevnikov, Sinclaire, Velja, Abate and Griffin (2026), *When can we trust untrusted monitoring? A safety case sketch across collusion strategies*. [arXiv](https://arxiv.org/abs/2602.20628)
[^cite-poseidon]: Poseidon Research, nonprofit profile. [GuideStar](https://www.guidestar.org/profile/85-1498806)
[^cite-kale-2025]: Neil Kale, Chen Bo Calvin Zhang and others (2025), *Reliable Weak-to-Strong Monitoring of LLM Agents*. [arXiv](https://arxiv.org/abs/2508.19461)
[^cite-terekhov-2026-diffuse-b]: Mikhail Terekhov, Caglar Gulcehre, Vivek Hebbar and Joe Benton (2026), *Diffuse AI Control on Fuzzy Tasks*. [Anthropic Alignment Science blog](https://alignment.anthropic.com/2026/diffuse-ai-control/)
[^cite-researcharena-2026]: Libon, Rank, Yeon, Schmotz, Qin, Donnelly, Prinzhorn and Andriushchenko (2026), *ResearchArena: Evaluating Sabotage and Monitoring in Automated AI R&D*. [arXiv](https://arxiv.org/abs/2607.19321)
[^cite-alignment-project-list]: UK AI Security Institute (2026), *The Alignment Project: Funded Research Projects*. [PDF](https://cdn.prod.website-files.com/68752402cd25ead7e36d7373/699c54b61461caad7130683c_f3052ca4341dfc41646ed7155aaee5fd_The%20Alignment%20Project%202026%20-%20Grants%20%281%29.pdf)

#### End Callout

#### Text
content::
\### Conferences and training

#### Callout: FAR.AI and MATS
tone:: neutral
collapse:: closed

#### Text
content::
- **FAR.AI** runs ControlConf, the AI control conference, with Redwood. The first was in London in March 2025, also with the UK AI Security Institute.[^cite-farai-london-2025] The second, in Berkeley in April 2026, "brought together 200 researchers, lab engineers, and policy folks working on AI control".[^cite-farai-controlconf-2026-b]
- **MATS** trains new AI safety researchers with mentors. Its summer 2026 program, with 120 fellows and 100 mentors, was its largest yet,[^cite-mats-summer-2026] and Redwood mentors run a control stream in it.[^cite-mats-redwood-c]

[^cite-farai-london-2025]: FAR.AI (2025), *London ControlConf 2025*. [FAR.AI](https://www.far.ai/blog/london-controlconf-2025)
[^cite-farai-controlconf-2026-b]: FAR.AI (2026), *ControlConf 2026: What is AI control and how has the field grown?* [FAR.AI](https://far.ai/news/controlconf-2026)
[^cite-mats-summer-2026]: MATS, *Summer 2026* program page. [MATS](https://www.matsprogram.org/program/summer-2026)
[^cite-mats-redwood-c]: MATS, *Redwood Research* stream. [MATS](https://www.matsprogram.org/stream/redwood)

#### End Callout

#### Text
content::
\## How big is it?

**In 2025**

- A 2025 count found about 620 people working full-time on technical AI safety at 68 active organisations. It files each organisation under one main area. Only Redwood (10 people) and Luthien (1) are filed under AI control, while AISI is filed under evaluations and the AI companies under other areas.[^cite-mcaleese-2025]
- The Shallow Review of Technical AI Safety 2025 estimates 5 to 50 full-time staff on the control agenda.[^cite-shallow-review-2025]
- 80,000 Hours cites a 2025 total of about 1,100 people working on AI safety, and estimates "a few thousand" working on major AI risks in a broader sense.[^cite-80k-loss-of-control]

**In 2026**

Nobody has published a new count of people. These numbers show where things are heading:

- **The conference.** ControlConf in April 2026 brought together about 200 "researchers, lab engineers, and policy folks working on AI control". The organisers wrote that a year earlier, control "was mostly a research conversation: scattered papers, a few blog posts, and dedicated teams at UK AISI and Anthropic".[^cite-farai-controlconf-2026-c]
- **Government grants.** The UK Alignment Project announced 60 funded projects in February 2026, worth £27m in total.[^cite-aisi-60-projects-2026] Its published list has 56 projects. By our count, 2 of them are clearly about control and about 5 more use the word in a broader sense. The rest are alignment research.[^cite-alignment-project-list-b]
- **Private grants.** No funder publishes how much it gives to control. Manifund's grant tracker, Trace, tags 13 grants from Coefficient Giving in 2025 as AI control, together about $40m. One of them, $36.6m to Redwood, is most of that. In 2026 up to October it tags 6, together about $3.8m. Trace's tag is broad and also covers work on hidden reasoning in models.[^cite-trace-coefficient]
- **AI safety funding overall.** Coefficient Giving, the largest funder, committed $168m to technical AI safety, security and field-building in 2024 and $351m in 2025, and is on track for over $1bn in 2026.[^cite-coefficient-scaling-2026]
- **Papers.** By our own count on arXiv, about 8 papers in 2025 used the phrase "AI control" in their abstract in this sense, and about 25 did in 2026 up to early October.[^cite-arxiv-search] Many control papers never use the phrase, so this shows the trend, not the total.

Our own reading, not a published figure: with this much more money and attention, and with control now in use at AI companies, the field has most likely grown a lot since 2025. By how much, nobody has measured. Whether a small field means control needs more people is disputed, and Unit 4 takes this up.

[^cite-mcaleese-2025]: Stephen McAleese (2025), *AI Safety Field Growth Analysis 2025*. [EA Forum](https://forum.effectivealtruism.org/posts/7YDyziQxkWxbGmF3u/ai-safety-field-growth-analysis-2025)
[^cite-shallow-review-2025]: *Control*, in the Shallow Review of Technical AI Safety 2025. [Shallow Review](https://shallowreview.ai/Black_box_safety/Control)
[^cite-80k-loss-of-control]: 80,000 Hours, *Loss of control*, problem profile. [80,000 Hours](https://80000hours.org/problem-profiles/loss-of-control/)
[^cite-farai-controlconf-2026-c]: FAR.AI (2026), *ControlConf 2026: What is AI control and how has the field grown?* [FAR.AI](https://far.ai/news/controlconf-2026)
[^cite-aisi-60-projects-2026]: UK AI Security Institute (2026), *Funding 60 projects to advance AI alignment research*. [AISI blog](https://www.aisi.gov.uk/blog/funding-60-projects-to-advance-ai-alignment-research)
[^cite-alignment-project-list-b]: UK AI Security Institute (2026), *The Alignment Project: Funded Research Projects*. The two clearly about control: "Enhanced Cyber Control Evaluations" (Aditi Raghunathan) and "Investigating Dynamics of Agentic Monitoring in AI Control" (Louis Thomson). [PDF](https://cdn.prod.website-files.com/68752402cd25ead7e36d7373/699c54b61461caad7130683c_f3052ca4341dfc41646ed7155aaee5fd_The%20Alignment%20Project%202026%20-%20Grants%20%281%29.pdf)
[^cite-trace-coefficient]: Manifund, *Coefficient Giving* in Trace, grants tagged "ai-control", counted in October 2026. [Trace](https://trace.manifund.org/orgs/coefficient-giving)
[^cite-coefficient-scaling-2026]: Coefficient Giving (2026), *We're Urgently Scaling Our Work on AI and Biosecurity*. [Coefficient Giving](https://coefficientgiving.org/research/were-urgently-scaling-our-work-on-ai-and-biosecurity/)
[^cite-arxiv-search]: arXiv search for "AI control" in abstracts, by year, counted in October 2026. About half the results use "AI control" in another sense, such as AI that controls machines, and were left out. [arXiv](https://arxiv.org/search/advanced?advanced=&terms-0-operator=AND&terms-0-term=%22AI+control%22&terms-0-field=abstract&classification-include_cross_list=include&date-filter_by=specific_year&date-year=2026&date-date_type=submitted_date_first&abstracts=hide&size=50&order=-announced_date_first)

#### Question: Open
id:: 056253bc-2b4d-48e7-80d6-a7be6a31cd4c
content::
A friend wants to work on AI control and could join Redwood Research, the UK AI Security Institute, or the team that monitors AI agents inside a large AI company. Pick two of these. For each, name one kind of control work it is better placed to do than the other, and say why.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Redwood Research is a research nonprofit that introduced AI control as a research area and publishes control research, often with co-authors at companies and government. The UK AI Security Institute is a government body whose Control team works on control protocols and evaluations. It released ControlArena, a shared library for running control experiments that company and Redwood researchers use, and runs a fund that pays for outside alignment and control research. Monitoring teams inside AI companies run monitors on their own company's agents, for example on nearly all internal coding traffic, with human review of flagged cases. 50 for each of the two places chosen. Per place: 25 for a kind of control work that fits it, and 25 for a reason tied to what that place has or is, such as independence and freedom to publish, government standing and the ability to build shared tools or fund others, or direct access to real agents, logs and staff. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Redwood is better placed to invent and test new control protocols and publish them, because it is independent and can share what it finds with every company. A company's monitoring team is better placed to run monitors on real agent traffic and fix the gaps in them, because only it has access to its own agents, logs and staff."
feedback-instructions:: The learner compares two of three places to do control work. Reference points from the page: Redwood Research is a nonprofit that introduced the research area and publishes research, often with co-authors at companies and government. The UK AI Security Institute's Control team works on control protocols and evaluations, released the ControlArena library that others use, and its Alignment Project fund pays for outside research, so it can provide shared tools and reach many companies and policy. Company monitoring teams run monitors on their own agents, such as OpenAI monitoring 99.9% of its internal coding traffic, so they have real systems and staff but work for one company. Reply in at most four sentences: confirm what fits, name the weakest link between a place and its work in one sentence, and correct any wrong fact. One turn, no follow-up question, no generic praise.
