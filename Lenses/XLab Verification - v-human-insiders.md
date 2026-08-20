---
id: 'dae72ebf-335a-4bd5-b970-b2b3e72230ed'
title: "2.4.1 Insiders and human sources"
tldr: "Faithful alpha import of XLab lesson 2.4.1 Insiders and human sources."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. Interactive elements marked as import gaps must be completed on XLab until Lens has an equivalent."
tags: [wip]
---
#### Text
content::
In this section, you will learn about the three main categories of human- or
personnel-based verification: whistleblower programs, personnel interviews,
and national intelligence activities. First, read the below excerpt of Baker's
_Verifying International Agreements on AI_ paper, paying attention to each
mechanism's unique strengths, failure modes, and applicable circumstances.{--{"author":"Elias's AI","timestamp":1787219624529}@@

\## Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment

*Source: XLab source material, [original](https://arxiv.org/abs/2507.15916v2)*

This page reproduces [§4.3 “Personnel-Based Verification Layers”](https://arxiv.org/html/2507.15916#S4.SS3) and [Appendix A.8 “Whistleblower Programs”](https://arxiv.org/html/2507.15916#A1.SS8) in full, including Tables 8, 9, and 14.

The source text and tables are reproduced under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

\### 5.3--}{++{"author":"Elias's AI","timestamp":1787219624529}@@


#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
from:: ###++} 4.3 Personnel-Based Verification Layers{--{"author":"Elias's AI","timestamp":1787219624529}@@
 |    Potential verification layer
  |   Summary of layer
  |   Keyadvantages
  |   Key disadvantages

 |
 Whistleblower programs

  |   Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals.
  |   Relatively simple, precedented, and implementation---}
{--{"author":"Elias's AI","timestamp":1787219624529}@@ready.
  |   Unclear effectiveness: depends on the number and loyalty of accomplices.

 |
  Interviews of personnel

  |   Interviews may reveal violations at any verification subgoal, e.g., via inconsistencies or perhaps improved lie detection tech, but such tech is abusable.
  |   Relatively simple and precedented.
  |   Unclear effectiveness: depends on accomplices’ ability to lie undetected.

 |   National intelligence activities

  |   Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.
  |   Precedented and may be feasible unilaterally.
  |   More adversarial, harder for third parties to verify, and unclear effectiveness.

 |

Table: Summary of personnel-based verification layers and their tradeoffs.

   Figure 7: Summary of how personnel-based verification layers would complete each subgoal. Each of these layers simply consists of a single mechanism applied to all subgoals.

--}{++{"author":"Elias's AI","timestamp":1787219624529}@@to:: ++}In contrast to other, more technical verification mechanisms, {--{"author":"Elias's AI","timestamp":1787219624529}@@personnel-based verification--}{++{"author":"Elias's AI","timestamp":1787219624529}@@_personnel-based verification_++} relies on the difficulty of having large groups of people collude without disclosures or leaks. Verifiers could systematically seek disclosures or leaks through whistleblower programs, interviews of personnel, and national intelligence activities. Intelligence activities, though, might involve cyber or signals intelligence, not only direct communication with personnel.

{--{"author":"Elias's AI","timestamp":1787219624529}@@\#### 5.3.1 4.3.1 Mechanisms
We outline three distinct mechanisms for personnel-based verification. All are well-established mechanisms for verifying compliance with regulations or international agreements.
Whistleblower programs: Formal, cooperative whistleblower programs could enable and encourage employees to narrowly blow the whistle on violations ([Appendix A.8](https://arxiv.org/abs/#a.8-whistleblower-programs)):[63](https://arxiv.org/abs/#ax-fn-63)

- To enable whistleblowing, employees could be allowed to confidentially view some of their employer’s claims. They could also be given regular in-person contact with Verifiers, to counter whistleblower suppression, with measures to minimize inappropriate leaks.

- To encourage whistleblowing, formal programs could, e.g., enable anonymous reports, offer financial rewards, or build pro-whistleblower norms.

Interviews of personnel: Employees could reveal violations unintentionally in interviews with Verifiers. This is in contrast with whistleblowers, who intentionally reveal violations. Interviewees could collude to lie, but they may struggle to do so convincingly. Another concern with interviews could be that they might reveal sensitive information; this could be mitigated by limiting interviews to questions within a narrow, agreed-on scope, similar to the questions asked to whistleblowers ([Appendix A.8](https://arxiv.org/abs/#a.8-whistleblower-programs)).
Hypothetically, one way interviews could be relatively robust is if they involved more reliable lie-detection technology than currently exists. However, we are not recommending the development of such technology, due to its potential for abuse.
National intelligence activities: States[64](https://arxiv.org/abs/#ax-fn-64) could seek evidence of violations through disciplines including human intelligence, signals intelligence, and cyber intelligence. Unlike the above mechanisms, intelligence activities may be effective without the Prover’s cooperation.[65](https://arxiv.org/abs/#ax-fn-65) Intelligence-based verification may not be equally feasible for all states in multilateral contexts, but states with relatively weak intelligence capabilities could rely on stronger states’ intelligence-based verification. For example, in a hypothetical agreement with the United States and China as parties, if a third party lacked confidence in their own intelligence capabilities, they might trust that the United States would verify (and enforce) China’s compliance, because doing so would be in U.S. interests, and vice versa.

\#### 5.3.2 4.3.2 Analysis--}{++{"author":"Elias's AI","timestamp":1787219624529}@@#### Article++}
{--{"author":"Elias's AI","timestamp":1787219624529}@@Personnel-based verification offers simplicity, but its reliability is unclear. Personnel-based verification mechanisms tend to offer relatively cheap, simple verification methods, without necessarily depending on complex, new technical protocols or hardware (which may be slow to develop, stress-test, and physically set up). Consequently, personnel-based mechanisms may be unusually feasible to use on short notice. These mechanisms leverage the large number of individuals involved in large-scale AI development—typically hundreds ([Table 9](https://arxiv.org/abs/#tab:the_number_of_contributors)). Human-based verification would also tend to strengthen other verification mechanisms, catching efforts to circumvent other mechanisms via significant collusion. However, human-based verification mechanisms may be hindered by counterintelligence, such as a violator involving only a small group of well-vetted and surveilled individuals in any violation (possibly for security reasons), though there are potential countermeasures.--}{++{"author":"Elias's AI","timestamp":1787219624529}@@source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]++}
{--{"author":"Elias's AI","timestamp":1787219624529}@@Personnel-based mechanisms would not only provide their own assurances but also strengthen technical assurances. In addition to providing independent ways to detect violations, personnel-based mechanisms could detect efforts to circumvent on- and off-chip layers. For example, if a state tried to circumvent on-chip mechanisms, it might use personnel to: identify or design hardware vulnerabilities, physically tamper with chips, or swap a compromised chip design into a chipmaking machine.[66](https://arxiv.org/abs/#ax-fn-66) Thus, a significant number of personnel may be able to disclose or leak evidence of the violation, not even counting the personnel involved in the AI aspects of the violation. In this sense, verification layers do not only provide backup in case other layers fail; they also make it less likely that other layers will fail.
The number of human personnel needed for AI development and deployment could fall due to AI automation, reducing the effectiveness of personnel-based verification. AI models are increasingly capable of software engineering and AI R&D [[16](https://arxiv.org/abs/#ax-ref-bengio2025internationalaisafetyreport), [123](https://arxiv.org/abs/#ax-ref-kwa2025measuringaiabilitycomplete)]. Still, even if AI engineers become fully automatable, some human involvement could persist. For example, human personnel may remain as organizational leaders, as staff who construct or maintain data centers, and as overseers of AI deployments—especially if significant human oversight is required.[67](https://arxiv.org/abs/#ax-fn-67) Separately, capable AI agents could benefit on- and off-chip verification layers ([Section 4.1](https://arxiv.org/abs/#on-chip-verification-layer); [Section 4.2](https://arxiv.org/abs/#off-chip-verification-layers)).
 |   AI model (or model family)
  |   Number of “core contributors”[68](https://arxiv.org/abs/#ax-fn-68)
  |   Number of “contributors” (including core contributors)

 |      GPT-4 (OpenAI)
  |   85 (excl. Microsoft)
  |   287 (excl. Microsoft)

 |   Llama 3 (Meta)
  |   222
  |   529

 |    Gemini (Google DeepMind)
  |   712
  |   1254

 |

Table: The number of contributors and core contributors publicly listed for several prominent AI models. Note these are not defined consistently, and they likely exclude various employees who could blow the whistle on certain violations, e.g., data center construction/maintenance staff, supplier company staff, or other AI developer staff such as product staff.

We'll pay special attention to whistleblower programs, which have the most
historical precedence, existing infrastructure, and potential verifiability
effectiveness.

\#### A.1.8 --}{++{"author":"Elias's AI","timestamp":1787219624529}@@from:: #### ++}A.8 Whistleblower Programs
{--{"author":"Elias's AI","timestamp":1787219624529}@@Background: Programs and laws that encourage employees to blow the whistle on violations are commonplace [[142](https://arxiv.org/abs/#ax-ref-nwc-whistlelaws)], contributing to approximately $2 billion or more in SEC fines in 2023.[135](https://arxiv.org/abs/#ax-fn-135) In the AI industry, large-scale AI projects tend to involve hundreds of employees ([Table 9](https://arxiv.org/abs/#tab:the_number_of_contributors))—hundreds of individuals who might be able to report any large-scale violations to a Verifier. In addition to AI developers’ own employees, other organizations throughout the AI supply chain have employees who can blow the whistle on some violations, especially undeclared AI data centers. Employees could blow the whistle on a Prover’s (i) non-compliant AI activities, (ii) falsified declarations, or (iii) attempts to circumvent another verification mechanism ([Table 14](https://arxiv.org/abs/#tab:types_of_employees_who_would_have_information)). Formal whistleblower programs could promote appropriate forms of whistleblowing by providing (would-be) whistleblowers with information they can check, disclosure protocols, and incentives (including intrinsic motivation, social norms, protection, and financial rewards). Provers may view formal whistleblower programs as legitimate, so Provers may be willing to take verifiable actions that facilitate whistleblowing (in contrast to espionage), such as allowing employees to privately talk with a Verifier.
Challenges and mitigations:

- Secure and confidential communication with potential whistleblowers. A Prover might try to not only retaliate against whistleblowers, but also entirely block or alter their messages. Standard approaches to secure internet communication (e.g., TLS, VPNs, and Tor) are not designed to secure the communications of parties who may be under video surveillance, or whose computers may be backdoored. Instead, a more secure option is for such employees to make in-person visits to a building physically secured by a Verifier. To prevent the Prover from detecting or blocking whistleblowers’ visits to these locations, the verification protocol could require the Prover to periodically send various relevant employees to visit the Verifier-secured building (e.g., as brief visits to an office near the Prover’s offices).[136](https://arxiv.org/abs/#ax-fn-136) [137](https://arxiv.org/abs/#ax-fn-137) [138](https://arxiv.org/abs/#ax-fn-138)

- Ensuring whistleblowers have enough information to report signs of violations. Even if an employee is not aware of a violation, they may have knowledge inconsistent with a Prover’s declarations ([Table 14](https://arxiv.org/abs/#tab:types_of_employees_who_would_have_information)). To learn if this is the case, the Verifier could, within employee interviews, ask the employee to check the Prover’s relevant declarations, or to share information that should match the relevant declarations, preferably via a confidentiality-preserving technology. A “low-tech” option for confidentiality preservation could involve a carefully overseen personal computer.[139](https://arxiv.org/abs/#ax-fn-139) However, perhaps a Prover can have sufficient compartmentalization and employee loyalty for all accomplices to lie.

- Further incentivizing whistleblowers: Beyond the anonymity protections discussed above, a whistleblower system could likely be strengthened by (potentially mandated) measures that make employees more morally, socially, or financially motivated to blow the whistle on violations. These could include trainings, certifications, knowledge tests, hiring practices, safety culture,[140](https://arxiv.org/abs/#ax-fn-140) financial rewards [[215](https://arxiv.org/abs/#ax-ref-secwhistleblower), [103](https://arxiv.org/abs/#ax-ref-irs2025whistleblower), [40](https://arxiv.org/abs/#ax-ref-cftc2025whistleblower)],[141](https://arxiv.org/abs/#ax-fn-141) and asylum or refugee status. Still, as above, it is unclear if these incentives would overcome a major Prover initiative for compartmentalization and employee loyalty.

- Avoiding excess disclosure: Employees could be allowed to disclose only a very small amount of information to the Verifier, as discussed in above footnotes. Further, the Prover and Verifier could jointly state agreed-on, reasonable bounds of protected whistleblowing (including high-level descriptions of potential violations and information to investigate further, but excluding digital transfers of Prover models, data, or code outside of a confidentiality-preserving technology). Parties could also agree on what questions or information a Verifier may share with an employee, so that the Prover could learn from their employees if the Verifier is inappropriately pressuring them to disclose IP.

 |   Type of violation
  |   Some employees who would have information about the violation

 |      Non-compliant declarations of large-scale AI development or deployment (intended to be detected by Subgoals 1.A or 1.B)
  |   • AI researchers and engineers who contribute to the declared activity and thus could notice if model origins, output origins, or evaluations/properties are falsely declared, or if workloads are designed to spoof verification
• Officials who deliberate on, order, or coordinate the violation (e.g., senior executives, top advisory bodies, and lower-level managers, in government and colluding companies)
• Spoofers: researchers and engineers who circumvent on- and off-chip verification mechanisms, if these are present[142](https://arxiv.org/abs/#ax-fn-142)

 |   Undeclared, large-scale uses of known AI compute clusters (intended to be detected by Subgoal 2.A)
  |   • AI researchers and engineers who contribute to the undeclared activity, or to another compliant activity that is altered to hide the non-compliant activity
• Officials who deliberate on, order, or coordinate the violation
• Spoofers: Researchers and engineers who circumvent on- and off-chip verification mechanisms, if these are present
• Compute cluster oversight or management staff

 |    Undeclared, large-scale AI compute (intended to be detected by Subgoal 2.B)
  |   • AI researchers and engineers who contribute to the undeclared activity, or to another compliant activity that is altered to hide the non-compliant activity
• Officials who deliberate on, order, or coordinate the violation
• Spoofers: Staff who circumvent other verification mechanisms, if present (e.g., by diverting chips and breaking compliance locks)
• Data center construction and operations staff (e.g., maintenance and security staff)
• Supplier staff who supply e.g., AI chips, energy, and other data center equipment
• Compute cluster design and setup staff
• Administrative (e.g., relevant finance, procurement, legal) staff

 |

Table:--}{++{"author":"Elias's AI","timestamp":1787219624529}@@to:: Table 14:++} Types of employees who would have information about different types of violations. Personnel-based verification could leverage these employees for verification.

\## Insider Report

Even when the human source is truthful and legally allowed to report, however,
reporting channels can still fail in various ways, which the next section will
cover.

\## [Optional] Exercise: Insider Report (8–10 minutes)

#### Text
content:: **Interactive exercise:** XLab's `human-insiders` widget has no direct Lens equivalent yet. Complete it in the [original XLab lesson](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-insiders). Its surrounding lesson text is preserved here.

#### Text
content::
*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-insiders)*
