---
id: 'd388005c-3e26-4e94-8851-692288c0cbea'
title: "2.0.1 Privacy-Preserving Mechanisms"
tldr: {--{"author":"Elias's AI","timestamp":1788015691725}@@"Faithful alpha import --}{++{"author":"Elias's AI","timestamp":1788015691725}@@"Rivals must prove compliance to each other without handing over the secrets an audit would expose. Meet the five ways out of that paradox, from a chip signing a report about itself to an inspector working under shrouds, and learn which ++}of {--{"author":"Elias's AI","timestamp":1788015691725}@@XLab lesson 2.0.1 Privacy-Preserving Mechanisms."--}{++{"author":"Elias's AI","timestamp":1788015691725}@@them work today and which are still papers."++}
summary_for_tutor: "Imported from XLab's{--{"author":"Elias's AI","timestamp":1788015691725}@@ canonical--} Verification {--{"author":"Elias's AI","timestamp":1788015691725}@@curriculum. Preserve--}{++{"author":"Elias's AI","timestamp":1788015691725}@@curriculum; preserve++} source framing. {--{"author":"Elias's AI","timestamp":1788015691725}@@XLab currently blocks cross-site embedding, so linked external exercises must be completed on XLab."--}{++{"author":"Elias's AI","timestamp":1788015691725}@@A reading lens with no questions: the confidentiality vs. verifiability tension, then five mechanism cards (hardware identity and remote attestation, privacy-preserving workload telemetry, zero-knowledge proofs, secure multiparty computation, managed access) rendered as closed callouts with XLab's text and links to the Module 2 lenses that develop each. If asked, help the learner separate deployed primitives (attestation, managed access) from experimental results (telemetry) and research proposals (ZK, MPC at frontier scale)."++}
tags: [wip]
duration_minutes: 10
---
#### Text
content::
A key tension common to any verification mechanism in this module is *confidentiality vs. verifiability*. Rival states are inherently incentivized to not disclose any information to each other, much less about the development of potentially dangerous and proprietary technologies. The last thing China wants is for the U.S. to steal development secrets through an invasive or insecure audit system. Yet the model of verification relies entirely upon the reliable mutual disclosure of information. Thus arises the verifier’s paradox: how do you gain enough access to confirm compliance, but not enough to enable espionage?

The solution is **privacy-preserving verification**: mechanisms designed to verify compliance while conveying minimum or zero excess information to verifier parties. Here are a few previews of privacy-preserving mechanisms you will learn about throughout Module 2:

:::callout {title="Hardware {--{"author":"Elias's AI","timestamp":1788015857403}@@attestation--}{++{"author":"Elias's AI","timestamp":1788015857403}@@identity++} and {--{"author":"Elias's AI","timestamp":1788015857403}@@location verification" tone="blue"}--}{++{"author":"Elias's AI","timestamp":1788015857403}@@remote attestation" tone="neutral" collapse="closed"}++}
{++{"author":"Elias's AI","timestamp":1788015857403}@@*Diagram: a chip inside a facility sends a signed attestation report to the verifier; the verifier gets no direct access to the workload or weights.*

++}A chip can use device-bound cryptographic credentials to report its identity and measured state. An attestation report can show the chip model, firmware, security settings, or approved software environment. Delay-based protocols can also estimate whether a chip is within an authorized area. The verifier receives a limited report instead of direct access to the workload, training data, or model weights. Remote attestation is already available on some AI hardware; [NVIDIA provides remote attestation for H100 GPUs](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_single_gpu.html). Recent work proposes [hardware fingerprints](https://arxiv.org/abs/2605.01930) as an additional way to identify individual GPUs. Learn more in [[../Lenses/XLab Verification - v-hw-attestation|section 2.1]].
:::

:::callout {--{"author":"Elias's AI","timestamp":1788015859285}@@{title="Workload--}{++{"author":"Elias's AI","timestamp":1788015859285}@@{title="Privacy-preserving workload++} telemetry" {--{"author":"Elias's AI","timestamp":1788015859285}@@tone="green"}--}{++{"author":"Elias's AI","timestamp":1788015859285}@@tone="neutral" collapse="closed"}++}
{++{"author":"Elias's AI","timestamp":1788015859285}@@*Diagram: physical signals such as power and temperature leave the facility for classification; the workload's contents stay sealed inside.*

++}A monitor can use signals such as GPU utilization, memory use, temperature, and power consumption to classify a workload. These signals describe the physical effects of computation without recording model weights, training data, or hyperparameters. A verifier could use them to detect a possible training run while limiting access to its contents. In [*Detecting Hidden ML Training With Zero-Overhead Telemetry*](https://arxiv.org/abs/2606.19262), a classifier identified training workloads with 98.2 percent accuracy across the full test corpus. Accuracy fell to 43–87 percent for the most difficult unexpected and adversarially disguised workloads, however; the method is promising, but it still needs testing on distributed frontier training, larger clusters, and new evasion strategies. [[../Lenses/XLab Verification - v-hw-attestation|Module 2.1]] explains hardware telemetry; [[../Lenses/XLab Verification - v-cloud|Module 2.2]] explains monitoring within cloud infrastructure.
:::

:::callout {title="Zero-knowledge proofs" {--{"author":"Elias's AI","timestamp":1788015861603}@@tone="purple"}--}{++{"author":"Elias's AI","timestamp":1788015861603}@@tone="neutral" collapse="closed"}++}
{++{"author":"Elias's AI","timestamp":1788015861603}@@*Diagram: a proof that the run satisfied the rule crosses to the verifier; the protected inputs themselves reveal nothing else.*

++}A zero-knowledge proof can show that a run satisfied a rule without revealing the protected inputs, such as model weights. Working systems can prove selected inference and evaluation tasks on small transformers and some LLMs. Frontier training remains a research problem, however; a 2026 proposal estimates that a future system could verify dense frontier training with about 2–10 percent training overhead, but it also identifies thirteen unresolved technical problems and does not yet cover several common training architectures. [Attestable](https://attestable.com/blog/model-weights-security) describes a related use of sampled output proofs for model-weight security; this is a company account of its own system and should be treated as early implementation evidence. See [zero-knowledge verification for frontier training](https://arxiv.org/abs/2606.05433) and [verifiable model evaluations](https://arxiv.org/abs/2402.02675). [[../Lenses/XLab Verification - v-hw-attestation|Module 2.1]] covers the hardware anchors that can connect a proof to a physical system.
:::

:::callout {title="Secure multiparty computation" {--{"author":"Elias's AI","timestamp":1788015864312}@@tone="amber"}--}{++{"author":"Elias's AI","timestamp":1788015864312}@@tone="neutral" collapse="closed"}++}
{++{"author":"Elias's AI","timestamp":1788015864312}@@*Diagram: developer and verifier each hold private inputs; a joint computation returns only the agreed result to both.*

++}Secure multiparty computation lets several parties evaluate an agreed function over private inputs. For example, a developer could supply secret-shared model weights while a verifier supplies private evaluation cases. The protocol would return an agreed result without giving either party the other party’s inputs. Large models remain difficult because the protocols require substantial communication, preprocessing, memory, and coordination. Performance is especially sensitive to network latency and nonlinear model operations. Current systems are most suitable for narrow evaluations with a clearly specified function; see [this 2026 system-level study of MPC for private machine learning](https://arxiv.org/abs/2604.00169).
:::

:::callout {--{"author":"Elias's AI","timestamp":1788015866428}@@{title="Managed-access inspections" tone="neutral"}--}{++{"author":"Elias's AI","timestamp":1788015866428}@@{title="Managed access" tone="neutral" collapse="closed"}++}
{++{"author":"Elias's AI","timestamp":1788015866428}@@*Diagram: a cleared inspector enters the facility under agreed rules; sensitive equipment stays shrouded.*

++}Authorized inspectors can receive limited physical or digital access to evidence, governed by rules specifying which records can be examined and restrictions on recording and copying. An AI inspection could use cleared inspectors, secure rooms, controlled terminals, and pre-agreed rules for retaining evidence, for instance. Managed access has an established basis in arms control; under the Chemical Weapons Convention, an inspected state may shroud sensitive equipment, remove unrelated papers, restrict some analyses, or offer alternative evidence, described in the [OPCW’s rules for managed-access inspections](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant). AI-specific procedures would still require negotiation, trained inspectors, secure technical tools, and clear rules for handling model weights and proprietary data. [[../Lenses/XLab Verification - v-intel-intro|Module 2.3]] explains how intelligence can produce and corroborate an inspection lead. [[../Lenses/XLab Verification - v-human-intro|Module 2.4]] explains inspectors, inspection rights, managed access, and the protection of sensitive information.
:::

No single mechanism provides complete verification. Hardware attestation and managed access can support bounded claims today. Workload telemetry has promising experimental results. Zero-knowledge proofs and secure multiparty computation are practical for selected tasks, but their use at frontier-training scale remains limited. A strong regime combines them: hardware provides trusted evidence, cloud mechanisms check selected computations, intelligence identifies suspicious activity, and inspectors resolve claims that remote methods cannot settle.

Module 2 begins with the hardware layer. {--{"author":"Elias's AI","timestamp":1788015881183}@@Section 2.1--}{++{"author":"Elias's AI","timestamp":1788015881183}@@[[../Lenses/XLab Verification - v-hw-attestation|Section 2.1]]++} examines how chips can identify themselves, report their state and location, measure workloads, and produce evidence that later cloud and institutional mechanisms can use.

{--{"author":"Elias's AI","timestamp":1788015881183}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/mechanism-privacy)*--}{++{"author":"Elias's AI","timestamp":1788015881183}@@#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
NVIDIA. "Hopper Single GPU Attestation Example." *NVIDIA Attestation Tools documentation*, NVIDIA. [docs.nvidia.com](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_single_gpu.html)
*NVIDIA's own quick-start walkthrough of remotely attesting an H100 GPU in Confidential Computing mode: the working evidence that remote attestation already ships on AI hardware.*

Tee, Wayne, and Jonathan Happel. "GPU Fingerprinting for Location Verification." *arXiv*, May 2026. [arxiv.org](https://arxiv.org/abs/2605.01930)
*Proposes physical hardware fingerprints, rather than stored cryptographic keys an adversary with physical access could extract, as a way to re-identify individual GPUs, with up to 100 percent re-identification accuracy in small-scale tests.*

Rahman, Robi, and Sabiha Tajdari. "Detecting Hidden ML Training With Zero-Overhead Telemetry." *arXiv*, June 2026. [arxiv.org](https://arxiv.org/abs/2606.19262)
*A study classifying GPU workloads from privacy-preserving telemetry, reporting 98.2 percent accuracy at spotting concealed training runs.*

Attestable. "From Verifiability to Model-Weight Security." Attestable. [attestable.com](https://attestable.com/blog/model-weights-security)
*The company's own account of using sampled zero-knowledge output proofs to shrink a datacenter's security dependencies: early implementation evidence, as the lesson flags.*

Peigné, Pierre, Ky Nguyen, and Paul Wang. "Zero knowledge verification for frontier AI training is possible." *arXiv*, June 2026. [arxiv.org](https://arxiv.org/abs/2606.05433)
*The 2026 proposal estimating a future ZK system could verify dense frontier training at roughly 2–10 percent overhead, while naming thirteen unresolved technical problems and the training architectures it does not yet cover.*

South, Tobin, Alexander Camuto, Shrey Jain, et al. "Verifiable evaluations of machine learning models using zkSNARKs." *arXiv*, Feb. 2024. [arxiv.org](https://arxiv.org/abs/2402.02675)
*Shows a model's claimed evaluation results can be proved with zkSNARKs without revealing the weights behind them.*

Huang, Pengzhi, Kiwan Maeng, and G. Edward Suh. "Beyond Latency: A System-Level Characterization of MPC and FHE for PPML." *arXiv*, Mar. 2026. [arxiv.org](https://arxiv.org/abs/2604.00169)
*The system-level study of MPC (and FHE) for private machine learning behind the lesson's caveats: communication, preprocessing, memory, and latency are what keep large models hard.*

Organisation for the Prohibition of Chemical Weapons. "Verification Annex, Part X: Challenge Inspections Pursuant to Article IX." *Chemical Weapons Convention*, OPCW. [opcw.org](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)
*The CWC's managed-access rules: how an inspected state may shroud sensitive equipment and restrict analyses while challenge inspectors still resolve compliance questions.*

XLab. "2.0.1 Privacy-Preserving Mechanisms." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/mechanism-privacy)
*The source lesson this page adapts, including the five mechanism cards.*
:::++}
