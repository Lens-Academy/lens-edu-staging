---
id: 'b21382c7-d99a-40c8-9462-ba06fa361551'
learning-outcome: "Explain the flexHEG architecture — an auditable guarantee processor paired with a secure physical enclosure — what its flexibility and open-source design buy, and what it must assume about tamper resistance and trust"
domain: "[[../Domains/Governance and Policy]]"
{++{"author":"Elias's AI","timestamp":1785319770888}@@stage: advanced
++}requires:
  - "[[Access substitutes for verification technology]]"
authors:
  - Elias+Claude
---
## Test:
id:: 82973068-5ff2-4928-a793-64039cafe462
#### Question
content:: A flexHEG is meant to let a chip's owner prove things about how that chip was used — to someone who does not trust them — without handing over what is running on it.

**Describe the two components and the division of labour between them. Then explain what the "flexible" and open-source properties are for, and identify the assumption the whole design rests on.**
assessment-instructions::
Score according to the following rubric.

**1** — Describes generic on-chip monitoring with no architecture; treats the mechanism as a remote kill switch or as surveillance of model outputs. *Example: "It's a chip feature that lets governments watch what AI companies are training and shut it down if it's dangerous."*

**2** — Names one component or gestures at "secure hardware", but cannot explain why two parts are needed or what flexibility contributes. *Example: "There's a secure processor on the accelerator that checks what it's being used for, and it's tamper-resistant."*

**3** — Gets the architecture: an **auditable guarantee processor** that observes and attests to how the accelerator is being used and enforces the agreed rules, paired with a **secure enclosure** providing physical tamper resistance so the owner cannot bypass, spoof, or quietly remove the processor. The division of labour is logic versus physics: the processor decides and attests, the enclosure makes the processor's report trustworthy by making interference detectable. Explains the point of the pairing — attestation from a component the owner could freely tamper with carries no information, so the physical layer is what gives the logical layer its meaning. States the goal: privacy-preserving verification and enforcement of claims about AI development, letting parties coordinate without exposing sensitive information or national-security details. *Example: "Two pieces. An auditable guarantee processor sits with the accelerator, watches how it's used, enforces the rules, and produces attestations. A secure enclosure wraps it in physical tamper resistance. The processor is the logic, the enclosure is the physics — and you need both, because an attestation from something the owner can freely open and reprogram tells you nothing. The enclosure is what makes the processor's word worth anything. The payoff is that you can prove a claim about your training run without revealing the run."*

**4** — As above, plus explains flexibility and openness as answers to specific failure modes. **Flexible / updateable:** the rules a regime wants to enforce will change as capabilities, thresholds, and agreements change, so baking one policy into silicon guarantees obsolescence — the mechanism must support a range of governance schemes (compute limits during training, privacy-preserving evaluations, controlled deployment, automated safety protocols) rather than one. **Open-source:** the party being verified must be convinced the device does only what is claimed and is not a backdoor or espionage instrument, and the verifying party must be convinced it cannot be subverted — mutual inspectability of the design is what makes a device that both sides distrust nonetheless acceptable to both. *Example: Adds "Flexibility is about not shipping a dead standard: the thresholds and the rules will move, and hardware you can't update is hardware that's wrong in three years — so it has to support many governance schemes, from training compute caps to privacy-preserving evals to deployment controls. Open-source is about mutual suspicion: the operator needs to believe the box isn't exfiltrating their secrets, and the verifier needs to believe it can't be subverted. Publishing the design is how one device becomes acceptable to two parties who distrust each other."*

**5** — As above, plus names the load-bearing assumption and its uncomfortable position: the design places the trust boundary inside hardware that is physically possessed, powered, and operated by the party it is meant to constrain — a resourced state adversary has indefinite physical access, which is the hardest condition under which to maintain tamper resistance, and the authors acknowledge the approach remains technically challenging with unresolved implementation hurdles. Also notes the systemic dependencies: it needs to be built into accelerators, so it requires manufacturer and supply-chain cooperation and only covers chips produced under the regime, leaving legacy and non-participating hardware outside — meaning flexHEG is a component of a layered regime rather than a solution to verification. *Example: Adds "The whole thing stands on tamper resistance holding against an adversary who owns the box — a state with unlimited physical access, time, and budget, which is the worst case for any tamper-evident design, and the authors are candid that it's unsolved. And it only exists if it's manufactured in, which means chipmaker and supply-chain buy-in, and which means it covers the chips made under the regime and nothing else. Legacy hardware and non-participants sit outside. So it's a layer, not an answer — strong where it applies, and it has to be stacked with methods that don't need the chip's cooperation."*
max-chars:: 1800

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - Flexible Hardware-Enabled Guarantees]]
