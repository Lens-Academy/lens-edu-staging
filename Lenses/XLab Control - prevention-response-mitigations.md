---
id: '32c21848-0ff9-4b1a-a8b5-cbf450e248ee'
title: "Prevention and Response Mitigations"
tldr: "Detection only tells you something happened. The other two jobs are shrinking the set of attacks an AI can even attempt, and intervening once one is underway or already done. Locking the doors is harder than repairing the break-in, and that asymmetry runs through everything here: sandboxed dev environments, audited supply chains, resampling, and a shutdown process the AIs are deliberately kept ignorant of."
summary_for_tutor: "Second lens of Module 3's taxonomy, after Detection Mitigations. Ported from XLab, which assembled it from Redwood's 'An overview of control measures' and Google DeepMind's AI Control Roadmap. It is expository, with no exercises: a prevention/response split, then prevention divided into agent- or model-level (permissions and affordances, training-data filtering, precise capability control, consistency checks, AI diversification, exploration-hacking countermeasures, regularization) and environment-level (environment isolation, strict software supply chain, trusted/untrusted AI for defense), then response divided into synchronous (incident escalation and shutdown, resampling and deference) and asynchronous (reverting changes, blocking, alignment investigation). The load-bearing idea is the asymmetry: averting an attack is much harder and costlier than reverting one, which is why the synchronous/asynchronous choice tracks threat severity. A key-terms box carries XLab's glossary definitions. If a learner conflates prevention with detection, ask what each does when the monitor never fires."
reading_minutes: 20
tutor_minutes: 0
tags: []
---
#### Text
content::
*This article was made with portions of [An overview of control measures](https://blog.redwoodresearch.org/p/an-overview-of-control-measures) from Ryan Greenblatt (Redwood Research) and the [GDM AI Control Roadmap](https://arxiv.org/abs/2607.13087) from Mary Phuong et al. at Google DeepMind.*

:::callout {title="Key terms used on this page" tone="neutral" collapse="closed"}
**Untrusted model.** A model powerful enough that scheming cannot be ruled out while having little evidence of aligned behavior.

**Trusted model.** A weaker model trusted not to scheme that's used to monitor, edit, or stand in for the untrusted model's outputs.

**Sandbagging.** A misaligned model intentionally doing worse on a task than it could. Scenarios include slowing down safety research or hiding dangerous capabilities from evaluations. ([Misalignment and strategic underperformance](https://blog.redwoodresearch.org/p/misalignment-and-strategic-underperformance))

**Control protocol.** The pipeline of safety techniques a lab runs untrusted model outputs through designed to extract useful work while preventing, and catching, bad actions. ([AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942))

**Backdoor.** Submitted work that passes all the visible tests but contains a deliberate, exploitable flaw. ([AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942))

**Exfiltration.** An AI getting a copy of its own weights out of the developer's control so it can run and act without the lab's safety measures. Also called self-exfiltration or weight exfiltration.

**Rogue deployment.** A deployment of an AI in which the intended safety measures are absent, like after the model escalates its own permissions inside the lab, or when it runs on exfiltrated weights outside the lab.
:::

We roughly categorize measures to limit harm as either prevention or response. By prevention, we mean measures that limit the space of possible attack paths, such as restricting the agents' capabilities, affordances, or access; agent sandboxing, adding layers of separation between AI agents and critical systems; or security hardening of critical systems. By response we mean measures that follow up on detection to intervene on an ongoing or past attack, e.g. reverting harmful actions, resampling / blocking harmful actions before they are executed, or shutting down a rogue AI. We group prevention and response because they both contribute to the ultimate desideratum of attacks not materializing successfully.

We classify prevention mitigations based on whether they restrict AI agents in some way, or harden the environment to be more resilient to attacks. We classify response mitigations based on when and how they are triggered: asynchronous response does not block agent execution, and usually takes place after the agent has caused some damage. Synchronous response intercepts an agent mid-trajectory, and applies a corrective intervention or review before continuing agent execution. Synchronous response aims to avert damage before it happens.

Averting attacks from happening (be it via prevention measures or synchronous response) is in many ways more difficult than reverting their effects post-hoc (as in asynchronous response). Prevention measures, such as via system design or access control, are significant technical projects that are complex to build, deploy at scale, and maintain. Synchronous response measures require recognizing an attack as it's happening, which is much harder than recognizing the undesirable outcome after it happens, especially when the attack is intentionally obfuscated and/or distributed. These measures may also introduce latency to model actions, and hence impose higher costs and face higher barriers to adoption.

As long as the capability gap between trusted and untrusted models is small enough, trusted models can be used to assist in both detection (e.g. automated monitoring) and harm prevention (e.g. finding and patching vulnerabilities). As trusted models start lagging behind untrusted models, we could potentially use the untrusted model itself for these tasks, with (as-yet-undeveloped) collusion and sandbagging countermeasures in place.

#### Text
content::
\## Agent- or Model-Level Prevention

From the agent- or model-level, we can prevent attacks by minimizing the number of affordances available to an agent, including its ability to access different resources.

**A system for determining permissions and affordances**, which potentially uses AI labor. This would require that AI agents be assigned distinct identities and granted permissions separately from their human user who launched them. These permissions would include things like how many GPUs the AI gets access to, what other AIs the AI can communicate with, what information it can access, and how long it is allowed to reason. As a central example, imagine training a trusted AI to determine what permissions an untrusted AI should be given. There would probably need to be some mechanism via which untrusted AIs can request more permissions. These measures make it possible to restrict access to sensitive resources and implement the least-privilege principle. As a special case, AI access control also includes *data minimization*, i.e., providing agents access to certain categories of data only on a need-to-know basis.

At deployment time, the untrusted model might seek out information about the control protocols it is subject to, in order to circumvent them. Therefore, a mitigation that could help reduce the likelihood of both test-time and deployment-time oversight awareness is **filtering the model's training data** to remove knowledge of AI control and safety evaluations, or limit AI access to unnecessary information that gives models priors that they're being evaluated and how they're being evaluated. If successful, the untrusted model would have less "cached" knowledge of oversight and would have to rederive it from scratch to become evaluation-aware. This would still be possible given sufficient strategic reasoning ability, but it would be significantly harder and more likely to show up in the model's chain-of-thought.

Instead of making our defenses stronger against attacks, we could reduce attack effectiveness by making potential attacks weaker through **more precise capability control**: Ideally, we'd have the ability to ensure that AIs which don't need to hack as part of their job wouldn't be knowledgeable about cyber. And, the same goes for a variety of other domains and capabilities. We'd like all of our AIs, except those working on control measures, to be as poorly informed as possible about our control measures and what the best takeover strategies are. We'd also like to make AIs worse at steganography and acausal coordination. If we could produce AIs of precise capability profiles reasonably cheaply (without needing to have each capability profile correspond to a full training run), that could be quite helpful. Methods could include unlearning, gradient routing, and doing multiple rounds of pretraining that layer relevant capabilities. If we sometimes need a capability and sometimes want to avoid this capability, then we need to ensure that our capability control method doesn't degrade this capability too much. For instance, filtering out data and then fine-tuning at the end might make the model generalize this data less effectively which could be an unaffordable tax. Ideally, we'd be able to combinatorially mix and match capabilities at runtime. (Methods like gradient routing could plausibly allow for this.) Another potential more speculative application of more precise capability control methods is having an AI not learn certain things while still learning other things. For instance, when we do online training, we'll both be teaching the AI about our oversight methods as well as teaching it to perform better according to these methods. This knowledge about our oversight methods might transfer to allowing the AI to more effectively evade our safeguards, so if we could avoid the AI learning this, that would be very useful.

\### Specialized Prevention Measures

**Various methods like consistency checks to make precise sabotage or misleading results more difficult**: task decomposition, consistency checks, and using diverse AI ensembles. There are probably a variety of methods here that make sabotage more difficult, because accurate results have somewhat structurally different properties from sabotaged results. These methods might be too expensive by default.

**(Cheap) AI diversification methods**: In many cases, we would be better off if we had a variety of different AIs that were less correlated in their thinking and potentially their objectives. These AIs could have a harder time coordinating and colluding and might be less likely to want to collude. However, training many different AIs using very different methods might be too expensive. There might exist methods which more cheaply add diversity. This could be related to more precise capability control as discussed above. More expensive diversification could be worthwhile at least for non-frontier AIs that are cheaper to train. For instance, we could use a diversified monitoring ensemble of AIs which are too strong to be trusted but which are substantially weaker than our best AI, such that creating this ensemble by training multiple AIs is affordable.

**Exploration hacking and sandbagging countermeasures**: If we naively apply RL, the AI may be able to [exploration hack](https://www.lesswrong.com/posts/dBmfb76zx6wjPsBC7/when-can-we-trust-model-evaluations#2__Behavioral_RL_Fine_Tuning_Evaluations). There are a variety of countermeasures to attempt to force AIs to explore good actions. See [Notes on countermeasures for exploration hacking (aka sandbagging)](https://www.lesswrong.com/posts/abmzgwfJA9acBoFEX/notes-on-countermeasures-for-exploration-hacking-aka) for more.

**Regularization combined with online training**: This can hopefully make subtle bad actions ineffective as a strategy (because the regularization forces some more specific policy rather than allowing for a broad set of effectively optimal policies). See the discussion in [[../Lenses/XLab Control - handling-non-concentrated-failures|Notes on handling non-concentrated failures with AI control]].

#### Text
content::
\## Environment-Level Prevention

On the environment-based prevention side, we want to prevent potential AI attacks from being able to harm or use our core systems through rigorous security hardening of the model's environment and infrastructure, and installing as many layers of separation as we can between models and core systems. To achieve this, there exist a few promising mitigations.

\### Environment Isolation

The agent's host systems / deployment environment could be engineered with the isolation principle in mind (Anthropic's [How we contain Claude across products](https://www.anthropic.com/engineering/how-we-contain-claude)), so that attack paths are forced to breach security boundaries, making attacks easier to detect and prevent. Here are some examples of defensive design choices and how they restrict attack paths:

- Separating the environment running the agent's scaffold and the environment running the agent's commands → Scaffold tampering requires gaining remote code execution (RCE) capability on the scaffold-running machine, or getting backdoored scaffold code deployed.
- Separate (soft-)sandboxed development environment per instance → Tampering with systems outside the sandbox requires explicitly sending calls to remote services or breaching the sandbox. Monitoring the sandbox perimeter becomes a very effective detection strategy.
- Separating internal-facing and external-facing AI agents. Internal-facing agents are given access to internal code, docs, services, and an offline cache of the internet, but not to live internet. Vice versa for external-facing agents. → Exfiltration and external harm attacks have to breach the internal / external boundary, or otherwise gain unauthorized live internet access.

Many mitigations in this category are medium-size software projects with an upfront implementation cost and moderately low cost in the form of friction/latency.

\### Strict software supply chain of critical code and systems

By "strict software supply chain" we mean that a) there is a thoroughly audited source for each piece of critical infrastructure or asset we want to protect, and b) unaudited forks of the infrastructure or asset are prevented from being used. This hardening would ideally cover frontier model weights, the model serving stack, monitoring code, the permissions system, sandboxing code, shutdown infrastructure, alignment / safety evaluations, and the next frontier model's training data, code and configs.

The purpose of software supply chain hardening is to prevent direct sabotage, and to make sure that mitigations that are load-bearing for maintaining the minimal conditions for control are always in place. For example, suppose we rely on synchronous monitoring and sandboxing for maintaining conditions for control. Then it should not be possible to insert a bug in the production code that disables monitoring on some chunk of traffic. It should also not be possible to just fork the agent scaffold, modify it to remove sandboxing, and run the modified unsandboxed agent.

Possible ways to achieve these security goals include: additional human approval of changes to the relevant codebases, adoption of a high standard for software supply-chain security such as SLSA ([OpenSSF, 2024](https://slsa.dev/spec)) (e.g. preventing unsubmitted code from being run), reproducible builds, data provenance and monitoring.

\### Trusted / Untrusted AI for Defense

Agents can also be used internally for finding and patching vulnerabilities (Anthropic's [Project Glasswing](https://www.anthropic.com/glasswing)). Most importantly, security and control infrastructure would ideally be red-teamed by AI-augmented security engineers and patched. As the infrastructure evolves, it would ideally continue being red-teamed and patched via this process. The main cost here would be the human expert time (if required) and the compute cost of running defensive models.

An example of using this measure is pre-deployment internal hardening, where broad internal deployments of a new model could be preceded by a hardening phase, in which the AI company's internal environment is hardened to withstand the impact of a new, more capable attacker (similar to [Project Glasswing](https://www.anthropic.com/glasswing)). The model itself, possibly in combination with humans and previous models, could be used defensively in this phase to find and patch vulnerabilities in the lab's systems.

Untrusted defense is in many ways analogous to untrusted monitoring in that once trusted or narrow AI paired with humans can no longer defend against the untrusted model, we can resort to the untrusted model itself for vulnerability detection and patching. The untrusted model has an incentive to sabotage these efforts, but there are various countermeasures an AI company could take, for example training a fork of the untrusted model to have a propensity to help with white-hat cybersecurity tasks. A company could also test the model on realistic inputs for which we know the vulnerability and patch. In such tests, the model would want to answer correctly to avoid suspicion, but if the tests are indistinguishable from real situations, then the model may end up helping us in similar non-test situations. This measure seems promising and not too costly. The main cost is compute, and it could be used at lower capability levels as well (just with weaker assurances).

#### Text
content::
\## Synchronous Response

Stopping a high-severity concentrated threat depends on how quickly we can act once it's detected. Labs should therefore have synchronous monitoring and response and/or AI access controls in place by the time models are assessed to be capable of executing such attacks.

\### Measures

**An incident reporting, escalation, and shutdown process**: Quickly and effectively escalating from the point when some human notices a serious issue to taking strong action seems pretty helpful. (Strong action could include a partial or full shutdown.) More minimally, we want to avoid incidents being dismissed or covered up. Having a well-designed, red-teamed, and streamlined process for doing this seems helpful from both a cultural and technical perspective. If AIs see credible and hard-to-fake evidence that they've been caught, they might decide to rapidly strike prior to being shut down. So, making sure most AIs are ignorant about the state of this process seems useful. We should, of course, adversarially evaluate whether AIs strike if they are presented with (fake) evidence that they've been caught to force AIs to only escalate like this in response to very hard-to-fake evidence (which should be easier to withhold from AI systems). A key part of this process, at least once you escalate to quite costly actions, will be getting consensus from a larger number of people that what the AI did is very concerning.

**Resampling and deference strategies**: We might only be able to have detailed human review on a tiny subset of actions, but resampling actions from the same AI or a different AI is much cheaper and could be applied more often, as discussed in [[../Lenses/XLab Control - win-continue-lose|Win/continue/lose scenarios and execute/replace/audit protocols]]. Additionally, blocking could be expensive due to increased latency, but resampling the action, running the new action, and then asynchronously reviewing the blocked action could be much cheaper. This could look like resampling from the same AI or a different (and possibly trusted) AI. And, we should flag for more expensive review if resampled actions from untrusted AIs are consistently suspicious for a particular input. In general, if the original action is suspicious, this is evidence that resampled actions will also be problematic, so we should have more conservative thresholds after resampling. We could also defer to more complex alternative policies that are safer, like having a more capable untrusted AI write instructions for a trusted AI.

#### Text
content::
\## Asynchronous Response

Stopping low-severity and diffuse threats doesn't require immediate action, as threats accumulate gradually or are reversible, so review after the fact is sufficient. Labs can therefore rely on asynchronous monitoring and response for these threats, as well as for high-severity attacks that models are not yet capable of executing.

\### Measures

**Reverting changes**: Rolling back unwanted modifications to code, configurations, or datasets after the fact. This resets the AI adversary's progress on a potential attack and helps mitigate the impact of diffuse threats that occur over time.

**Blocking**: Preventing flagged actions from being executed or submitted. Applicable across various types of monitoring, e.g. action and CoT monitoring, pull-request monitoring, or access requests.

**Alignment investigation**: A follow-up inquiry into a specific instance of concerning AI behavior, often triggered by a monitoring alert or honeypot, aimed at determining the extent to which the behavior is intentional and persistent. It could involve e.g. reproducing and resampling the incident trajectory in a sandbox, analyzing counterfactual scenarios, altering the model's internal state, or directly interrogating the agent. For example, we could use **more elaborate incrimination measures**: These help with gaining confidence about whether an AI was intentionally doing some problematic action, and getting a better understanding of what that bad action might ultimately lead to (which helps with understanding how misaligned the AI is). This could involve things like methods for simulating the response of the environment to AI actions we don't want to execute, and having some setup for quickly mocking a rogue deployment. Ideally, we'd be able to quickly go from an example where the AI seemingly tried to start some sort of rogue deployment to a good understanding of whether this was intended and what the AI would have done during that rogue deployment. This is useful both for better calibrating defensive measures and for building (strong) evidence for risk.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "An overview of control measures." *Redwood Research blog*, 6 Apr. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/an-overview-of-control-measures)
*One of the two sources this lesson is assembled from: Redwood's catalogue of measures a lab could deploy to keep an untrusted model under control.*

Phuong, Mary, Erik Jenner, Laurent Simon, Lewis Ho, Rohin Shah, Sebastian Farquhar, and Scott Coull. "GDM AI Control Roadmap." *arXiv*, 13 July 2026. [arxiv.org](https://arxiv.org/abs/2607.13087)
*The other source this lesson is assembled from: Google DeepMind's roadmap for AI control.*

Hubinger, Evan. "When can we trust model evaluations?" *LessWrong*, 28 July 2023. [lesswrong.com](https://www.lesswrong.com/posts/dBmfb76zx6wjPsBC7/when-can-we-trust-model-evaluations#2__Behavioral_RL_Fine_Tuning_Evaluations)
*The section on behavioral RL fine-tuning evaluations, which is where the lesson's definition of exploration hacking points.*

Greenblatt, Ryan. "Notes on countermeasures for exploration hacking (aka sandbagging)." *LessWrong*, 24 Mar. 2025. [lesswrong.com](https://www.lesswrong.com/posts/abmzgwfJA9acBoFEX/notes-on-countermeasures-for-exploration-hacking-aka)
*The follow-up the lesson points to for ways to force an AI to explore good actions under RL.*

Anthropic. "How we contain Claude across products." *Anthropic Engineering*, 25 May 2026. [anthropic.com](https://www.anthropic.com/engineering/how-we-contain-claude)
*The worked example of the isolation principle behind the environment-isolation measures.*

Anthropic. "Project Glasswing: Securing critical software for the AI era." *Anthropic*, 7 Apr. 2026. [anthropic.com](https://www.anthropic.com/glasswing)
*The example of using AI agents defensively to find and patch vulnerabilities in critical software.*

Open Source Security Foundation. "Supply-chain Levels for Software Artifacts (SLSA) Specification." *OpenSSF*, 2024. [slsa.dev](https://slsa.dev/spec)
*The software supply-chain security standard the lesson names as a way to keep unaudited code out of critical systems.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, 12 Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The source of the control protocol and backdoor definitions in the key-terms box.*

Stastny, Julian. "Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking." *Redwood Research blog*, 8 May 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/misalignment-and-strategic-underperformance)
*The source of the sandbagging definition in the key-terms box.*

XLab. "Prevention and Response Mitigations." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/areas-of-control-work/prevention-response-mitigations)
*The source lesson this page adapts.*
:::
