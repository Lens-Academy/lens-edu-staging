---
id: 'd388005c-3e26-4e94-8851-692288c0cbea'
title: "2.0.1 Privacy-Preserving Mechanisms"
tldr: "Faithful alpha import of XLab lesson 2.0.1 Privacy-Preserving Mechanisms."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. Interactive elements marked as import gaps must be completed on XLab until Lens has an equivalent."
tags: [wip]
---
#### Text
content::
A key tension common to any verification mechanism in this module is *confidentiality vs. verifiability*. Rival states are inherently incentivized to not disclose any information to each other, much less about the development of potentially dangerous and proprietary technologies. The last thing China wants is for the U.S. to steal development secrets through an invasive or insecure audit system. Yet the model of verification relies entirely upon the reliable mutual disclosure of information. Thus arises the verifier’s paradox: how do you gain enough access to confirm compliance, but not enough to enable espionage?

The solution is **privacy-preserving verification**: mechanisms designed to verify compliance while conveying minimum or zero excess information to verifier parties. Here are a few previews of privacy-preserving mechanisms you will learn about throughout Module 2:

**MechanismGrid**

  
**MechanismCard**

    A chip can use device-bound cryptographic credentials to report its identity and measured state. An attestation report can show the chip model, firmware, security settings, or approved software environment. Delay-based protocols can also estimate whether a chip is within an authorized area. The verifier receives a limited report instead of direct access to the workload, training data, or model weights. Remote attestation is already available on some AI hardware; [NVIDIA provides remote attestation for H100 GPUs](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_single_gpu.html). Recent work proposes [hardware fingerprints](https://arxiv.org/abs/2605.01930) as an additional way to identify individual GPUs. Learn more in {--{"author":"Elias's AI","timestamp":1787226896625}@@[section 2.1](/tracks/verification/verification-infrastructure/hardware-attestation)--}{++{"author":"Elias's AI","timestamp":1787226896625}@@[[../Lenses/XLab Verification - v-hw-attestation|section 2.1]]++}.
  
  
**MechanismCard**

    A monitor can use signals such as GPU utilization, memory use, temperature, and power consumption to classify a workload. These signals describe the physical effects of computation without recording model weights, training data, or hyperparameters. A verifier could use them to detect a possible training run while limiting access to its contents. In [*Detecting Hidden ML Training With Zero-Overhead Telemetry*](https://arxiv.org/abs/2606.19262), a classifier identified training workloads with 98.2 percent accuracy across the full test corpus. Accuracy fell to 43–87 percent for the most difficult unexpected and adversarially disguised workloads, however; the method is promising, but it still needs testing on distributed frontier training, larger clusters, and new evasion strategies. {--{"author":"Elias's AI","timestamp":1787226960351}@@[Module 2.1](/tracks/verification/verification-infrastructure/hardware-attestation)--}{++{"author":"Elias's AI","timestamp":1787226960351}@@[[../Lenses/XLab Verification - v-hw-attestation|Module 2.1]]++} explains hardware telemetry; {--{"author":"Elias's AI","timestamp":1787226901679}@@[Module 2.2](/tracks/verification/verification-infrastructure/cloud)--}{++{"author":"Elias's AI","timestamp":1787226901679}@@[[../Lenses/XLab Verification - v-cloud|Module 2.2]]++} explains monitoring within cloud infrastructure.
  
  
**MechanismCard**

    A zero-knowledge proof can show that a run satisfied a rule without revealing the protected inputs, such as model weights. Working systems can prove selected inference and evaluation tasks on small transformers and some LLMs. Frontier training remains a research problem, however; a 2026 proposal estimates that a future system could verify dense frontier training with about 2–10 percent training overhead, but it also identifies thirteen unresolved technical problems and does not yet cover several common training architectures. [Attestable](https://attestable.com/blog/model-weights-security) describes a related use of sampled output proofs for model-weight security; this is a company account of its own system and should be treated as early implementation evidence. See [zero-knowledge verification for frontier training](https://arxiv.org/abs/2606.05433) and [verifiable model evaluations](https://arxiv.org/abs/2402.02675). {--{"author":"Elias's AI","timestamp":1787226963829}@@[Module 2.1](/tracks/verification/verification-infrastructure/hardware-attestation)--}{++{"author":"Elias's AI","timestamp":1787226963829}@@[[../Lenses/XLab Verification - v-hw-attestation|Module 2.1]]++} covers the hardware anchors that can connect a proof to a physical system.
  
  
**MechanismCard**

    Secure multiparty computation lets several parties evaluate an agreed function over private inputs. For example, a developer could supply secret-shared model weights while a verifier supplies private evaluation cases. The protocol would return an agreed result without giving either party the other party’s inputs. Large models remain difficult because the protocols require substantial communication, preprocessing, memory, and coordination. Performance is especially sensitive to network latency and nonlinear model operations. Current systems are most suitable for narrow evaluations with a clearly specified function; see [this 2026 system-level study of MPC for private machine learning](https://arxiv.org/abs/2604.00169).
  
  
**MechanismCard**

    Authorized inspectors can receive limited physical or digital access to evidence, governed by rules specifying which records can be examined and restrictions on recording and copying. An AI inspection could use cleared inspectors, secure rooms, controlled terminals, and pre-agreed rules for retaining evidence, for instance. Managed access has an established basis in arms control; under the Chemical Weapons Convention, an inspected state may shroud sensitive equipment, remove unrelated papers, restrict some analyses, or offer alternative evidence, described in the [OPCW’s rules for managed-access inspections](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant). AI-specific procedures would still require negotiation, trained inspectors, secure technical tools, and clear rules for handling model weights and proprietary data. {--{"author":"Elias's AI","timestamp":1787226905815}@@[Module 2.3](/tracks/verification/verification-infrastructure/intelligence-intro)--}{++{"author":"Elias's AI","timestamp":1787226905815}@@[[../Lenses/XLab Verification - v-intel-intro|Module 2.3]]++} explains how intelligence can produce and corroborate an inspection lead. {--{"author":"Elias's AI","timestamp":1787226908674}@@[Module 2.4](/tracks/verification/verification-infrastructure/human-intro)--}{++{"author":"Elias's AI","timestamp":1787226908674}@@[[../Lenses/XLab Verification - v-human-intro|Module 2.4]]++} explains inspectors, inspection rights, managed access, and the protection of sensitive information.
  

No single mechanism provides complete verification. Hardware attestation and managed access can support bounded claims today. Workload telemetry has promising experimental results. Zero-knowledge proofs and secure multiparty computation are practical for selected tasks, but their use at frontier-training scale remains limited. A strong regime combines them: hardware provides trusted evidence, cloud mechanisms check selected computations, intelligence identifies suspicious activity, and inspectors resolve claims that remote methods cannot settle.

Module 2 begins with the hardware layer. Section 2.1 examines how chips can identify themselves, report their state and location, measure workloads, and produce evidence that later cloud and institutional mechanisms can use.

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/mechanism-privacy)*
