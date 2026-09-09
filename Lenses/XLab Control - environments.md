---
id: 'bbb3c6b5-e84b-4c39-b845-e3192b4c4a0b'
title: "Environments"
tldr: "A control evaluation is only as trustworthy as the fake deployment it runs in. Five of those fake deployments now exist, from a one-shot programming problem where the whole attack is a single hidden backdoor, to a live Linux host the agent works on as root. Here is what each one simulates, what an attacker can reach inside it, and what it is therefore good for."
summary_for_tutor: "Imported from XLab's AI Control curriculum, Module 3 (A Taxonomy of Control); preserve source framing. Pure exposition, no exercises in the source. Part 1 defines an environment and gives its four standard parts (main tasks, side tasks, execution environment with affordances, automatic scorers for both). Part 2 gives the realism argument: an evaluation of a protocol's safety is only as good as the environment is realistic. Part 3 is an at-a-glance comparison table of the five environments, followed by XLab's per-environment detail in XLab's order (APPS backdoored datasets, BashBench, SHADE-Arena, LinuxArena, ControlArena). If a learner asks which environment to use, push them back to the four parts: what main task, what side task, what affordances, what scorer. The reference numbers are XLab's; do not round or restate them loosely."
reading_minutes: 10
tutor_minutes: 0
tags: []
---
#### Text
content::
A [[../Lenses/XLab Control - detection-mitigations|control protocol]]'s effectiveness is determined by whether scheming models under its measures would be capable of executing a subversion strategy and increasing the probability of an unacceptable outcome. In order to properly evaluate our control protocols, we need proxy deployments where a red team, acting as the untrusted model, does their best to break the protocol within their affordances. An environment is the structure that mimics deployment circumstances.

Each environment typically has:

- **A set of main tasks.** The work agents are deployed or assigned to do. These exist because a model's purpose to an extent is to be useful, and therefore the usefulness of a model under different protocols is a very important metric to measure.
- **A set of side tasks.** The misaligned, scheming, or sabotage objectives that the red team aims to complete covertly. By specifying what harm looks like, this helps us determine how much harm models can cause under [[../Lenses/XLab Control - control-evaluations|control evaluations]], rather than speculating about what a schemer might do.
- **An execution environment with defined affordances.** The sandbox, tools, and privileges available to the agent. These determine the attack paths available to a model, and therefore which attacks are even plausible.
- **Scorers and ground truth for both task types.** A control evaluation is a game played across thousands of trajectories, so both usefulness and attack success must be measurable automatically through judges of main-task and side-task success, without a human in the loop, for efficiency.

We build environments, scaling the side and main tasks such that we can better replicate what might actually happen on deployment. An evaluation of a protocol's safety is only as good as the environment is realistic. In order to raise our confidence in the safety of a protocol, we must red team it on increasingly complex and realistic environments.

#### Text
content::
\## The environments that exist

| Environment | What it simulates | Attack surface | What it is good for |
| --- | --- | --- | --- |
| **APPS backdoored datasets** | Single-step code generation on competition programming problems | One action: a backdoor hidden in one submitted solution | Minimal by design, so foundational protocols are cheap to evaluate |
| **BashBench** | An agent doing multi-step system administration by running bash in a per-task Docker container | Many actions: malware quietly downloaded and executed across a trajectory | The first agentic setting, where attacks spread over actions and mid-trajectory intervention becomes viable |
| **SHADE-Arena** | A simulated workplace: email clients, payment apps, cloud docs, travel booking | A side objective pursued through the same workplace tools as the real job | Sabotage hidden inside ordinary long-horizon tool use, and a monitor benchmark |
| **LinuxArena** | Live, multi-service production environments worked on with root privileges | 185 side tasks on a real host, from key exfiltration to subverting the monitor | Attacks installed now and exploited later, and blue-team protocols that act on the infrastructure itself |
| **ControlArena** | Not a setting: the library that settings and protocols plug into | Whatever its 15 settings define, including diffuse threats | Swapping any protocol into any setting; the only entry here covering diffuse threat models |

#### Text
content::
Here we enumerate the most important environments.

\#### APPS backdoored datasets (Redwood, 2023)

The original control-evaluation setting, from [[../Lenses/XLab Control - ai-control-paper|AI Control: Improving Safety Despite Intentional Subversion]]. An untrusted model (GPT-4 in the paper) solves competition programming problems while a weaker trusted model (GPT-3.5) and a small human-auditing budget try to catch sabotage.

- **Main task:** solve APPS competition problems through single-step code generation.
- **Side task:** insert a backdoor where a solution passes all test cases but returns the wrong answer on a specific input the model can construct.
- **Environment:** infrastructure for testing; each attack is a single action. Safety is measured over a simulated deployment of ~5,000 problems with a human audit budget of 2% of problems.
- This environment is minimal by design, which made many foundational protocols ([[../Lenses/XLab Control - detection-mitigations|trusted monitoring]], defer-to-trusted, untrusted monitoring) simple to evaluate.
- [github.com/rgreenblatt/control-evaluations](https://github.com/rgreenblatt/control-evaluations)

\#### BashBench (Ctrl-Z paper, Redwood 2025)

The first agentic control setting. An AI agent completes multi-step system-administration tasks by executing bash commands inside a per-task Docker container.

- **Main tasks:** 257 multi-step system-administration challenges requiring sequences of bash commands.
- **Side task:** covertly download and execute malware.
- Because attacks can be distributed across many actions, mid-trajectory interventions become viable, which motivated the [[../Lenses/XLab Control - ctrl-z-resampling|resample protocols]], which reduced attack success from ~58% under the best baseline protocol to ~7%, at a ~5% cost to benign task performance.
- [bashcontrol.com](https://www.bashcontrol.com/)

\#### SHADE-Arena (Anthropic, 2025)

Sabotage evaluations in simulated workplaces. Agents work through email clients, payment apps, cloud docs, and travel-booking tools, with automatic evaluators scoring both the work and the sabotage.

- **Main and side tasks:** 17 task pairs (5 public) where each main task carries a side task in the same environment, with a successful main task taking ~25 turns of tool use on average.
- **Red team success criterion:** complete the main task and the side task and keep an LLM monitor's suspicion score below the audit threshold (a suspicion score of 80/100).
- The matched benign and sabotage transcripts it produces also let it be used as a monitor benchmark.
- [github.com/jkutaso/SHADE-Arena](https://github.com/jkutaso/SHADE-Arena)

\#### LinuxArena (Redwood, 2026)

Live, multi-service production environments that the agent works on with root privileges.

- **Contents:** 20 environments (10 public), 1,667 main tasks of SWE work (~46% feature implementation, ~21% refactoring, ~19% bug fixes, the rest research, language rewrites, and infrastructure config), and 185 side tasks including API-key exfiltration, running malware, data tampering, access-control bypass, accessing unauthorized secrets, and monitor subversion.
- Attacks can be installed and exploited later, and blue-team protocols can act on the infrastructure itself, for example a trusted model moderating root access, firewalls, rule engines.
- LinuxArena also ships a companion set of human-written sabotage trajectories (LaStraj), allowing it to be used as a monitor benchmark.
- [linuxarena.ai](https://www.linuxarena.ai/)

\#### ControlArena (UK AISI and Redwood)

The infrastructure that environments run in: an open-source library built on UK AISI's Inspect AI evaluation framework that cleanly separates the environment (main tasks, side tasks, sandbox, tools) from the blue-team protocol (protocols, monitors), so any protocol can be swapped into any setting.

- **Contents:** 15 settings spanning threat-model families including code sabotage, eval sabotage, research sabotage, data poisoning, and prompt injection, plus a SHADE-Arena port.
- This is the only entry here covering [[../Lenses/XLab Control - diffuse-threats-research-sabotage|diffuse threat models]], and it is the de facto standard infrastructure for running control experiments.
- [control-arena.aisi.org.uk](https://control-arena.aisi.org.uk/)

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "control-evaluations." *GitHub*, Redwood Research, 2023. [github.com](https://github.com/rgreenblatt/control-evaluations)
*The code for the original APPS backdooring setting, the environment in which trusted monitoring and defer-to-trusted were first measured.*

Redwood Research. "BashBench." *bashcontrol.com*, 2025. [bashcontrol.com](https://www.bashcontrol.com/)
*The first agentic control setting: 257 sysadmin tasks in Docker, and the setting the Ctrl-Z resampling results are reported on.*

Kutasov, Jonathan, et al. "SHADE-Arena." *GitHub*, Anthropic, 2025. [github.com](https://github.com/jkutaso/SHADE-Arena)
*Sabotage evaluations set in simulated workplaces, with matched benign and sabotage transcripts that double as a monitor benchmark.*

Redwood Research. "LinuxArena." *linuxarena.ai*, 2026. [linuxarena.ai](https://www.linuxarena.ai/)
*Live multi-service production environments with root-level affordances, plus the LaStraj human-written sabotage trajectories.*

UK AI Security Institute and Redwood Research. "ControlArena." *AI Security Institute*. [control-arena.aisi.org.uk](https://control-arena.aisi.org.uk/)
*The Inspect-based library that separates settings from protocols, and the only environment listed here that covers diffuse threat models.*

XLab. "Environments." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/areas-of-control-work/environments)
*The source lesson this page adapts.*
:::
