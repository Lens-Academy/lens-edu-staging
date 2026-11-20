---
id: b2b1385c-469e-455e-9a8e-2f8cf558f6e3
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what a binding international agreement on advanced AI could require, which past arms-control regimes it could learn from, why one is hard to reach, and how countries could check each other's compliance, mainly through AI chips.

## Requires
- [[International AI governance]]

## Helpful first
- [[Compute governance]]
- [[Technology governance precedents]]

## Why it matters
Many plans for reducing AI risk, from compute caps to a pause, work only if the leading countries agree and can check that others aren't cheating. Knowing what verification can and can't do helps you judge which proposals are realistic and where a treaty could fail.

## Lenses
- [[../Lenses/AIV - An International Agreement to Prevent Premature ASI|An International Agreement to Prevent Premature ASI]]: MIRI's governance team sets out a treaty led by the US and China, with compute thresholds, chip tracking, research limits, and an honest account of why it could fail and why the political will is not there yet; read up to the end of section 4 (November 2025).
- [U.S.-China AI Agreements Need Verification, Not Trust (CNAS)](https://www.cnas.org/publications/cnas-insights/cnas-insights-u-s-china-ai-agreements-need-verification-not-trust): Why neither side will take the other's word, what verification of compute limits could look like, what can't be checked, and why the tools need building now (September 2026).
- [Governing Dual-Use Technologies: Case Studies of International Security Agreements (arXiv)](https://arxiv.org/abs/2409.02779v1): What the IAEA, the START treaties, the chemical weapons body (OPCW), the Wassenaar export controls and the Biological Weapons Convention teach an AI treaty about inspections, challenge inspections and the cost of having no verification; read the Executive Summary, plus the OPCW and BWC case studies (September 2024).
- [[../Lenses/AIV - Verification for International AI Governance|Verification for International AI Governance]]: Oxford Martin's report on which AI agreements could be checked today or within a few years, why data-centre compute is the tractable case, and the on-chip and off-chip hardware that could do it; read the abstract and executive summary (July 2025) (more advanced).

## Tests
#### Question: Choice
id:: 43241712-e3a8-4c23-9452-5f31d0c8d9ef
content:: Why do most proposals for verifying an international AI treaty focus on AI chips rather than on algorithms?
options::
- [x] Chips are physical, made by a few firms, and big clusters are hard to hide
- Compute alone decides how capable a trained model will be
- Algorithms are trade secrets that a treaty can't legally override
- Chip makers can already switch off any chip remotely
shuffle:: true

#### Question: Choice
id:: 4437df62-823c-4143-9277-a8aa04c5c1e0
content:: The Biological Weapons Convention (1972) is often cited as a warning for anyone designing an AI treaty. Why?
options::
- [x] It lacks verification, and the Soviet Union cheated on a large scale
- The US and the Soviet Union never signed it
- It banned peaceful biology research along with weapons
- It expired when its members didn't renew it
shuffle:: true

#### Question: Choice
id:: b53ad2dc-9668-4c27-8757-91a4e8e36899
content:: Proposals for an "IAEA for AI" borrow from the International Atomic Energy Agency. Which IAEA function do they mainly want to copy?
options::
- [x] Inspecting facilities to check that states keep their commitments
- Running a joint lab where member states develop the technology
- Publishing consensus reports on the state of the science
- Imposing military sanctions on states that break the rules
shuffle:: true

#### Question: Choice
id:: 2d0ce1f1-68d2-4efa-a015-625e1112c9c2
content:: Hardware-enabled mechanisms are proposed features built into AI chips to support treaty compliance checks. What could they plausibly let an inspector confirm without seeing a model's weights?
options::
- [x] Where the chips are and how much compute they've used
- Whether the trained model has dangerous capabilities
- Whether the model's goals match what its developer intended
- Whether the training data was legally obtained
shuffle:: true

#### Question: Choice
id:: 2688dfdb-8c3c-4c62-9f8f-cf0ce96e83aa
content:: A treaty caps AI training runs at a fixed amount of compute. Even if every country complies, why might the cap give less protection over time?
options::
- [x] Better algorithms reach the same capabilities with less compute
- Chips slow down as they age, so runs take longer
- Inspectors' measurements of compute become less accurate
- Countries can claim exemptions once the treaty is a few years old
shuffle:: true

#### Question: Choice
id:: 98b92d6a-77a6-4c9c-a459-d40def3305cf
content:: The Montreal Protocol on ozone-depleting chemicals is often called a successful treaty, but an easier case than AI. What made it easier?
options::
- [x] Industry had affordable substitutes for the banned chemicals
- Only a handful of countries needed to ratify it
- The banned chemicals had major military uses
- It relied on voluntary pledges rather than binding rules
shuffle:: true

#### Question: Choice
id:: 1ddfbf12-0bda-4493-a9cf-556300887c74
content:: Some AI treaty proposals borrow "challenge inspections" from the Chemical Weapons Convention. What is a challenge inspection?
options::
- [x] A short-notice inspection of a suspected site, requested by another member
- A routine, scheduled visit to a site the state has declared
- A state's inspection of its own sites, with results shared with others
- An inspection the host state may refuse if it gives a reason
shuffle:: true

#### Question: Choice
id:: ab06d308-87f3-4d74-b9a6-ab9b1a60b9d2
content:: As of November 2026, what binding international law limits the compute or capabilities of frontier AI models?
options::
- [x] None; the one binding AI treaty covers human rights, not compute or capabilities
- A UN treaty caps training compute, though the US and China haven't joined
- The Bletchley Declaration, which became binding once the Seoul summit confirmed it
- The Hiroshima Code of Conduct, which binds AI companies based in G7 countries
shuffle:: true

#### Question: Choice
id:: d161ed9e-8c81-43dd-aa11-95c4ebd6b6fd
content:: Does the Council of Europe's Framework Convention on AI, opened for signature in 2024, limit the compute or capabilities of frontier AI models?
options::
- [x] No, it deals with human rights, democracy and the rule of law
- Yes, it caps training compute in the countries that ratify it

#### Question: Choice
id:: b286112f-dcae-4221-a84d-40d9eff38397
content:: In September 2026, after a Trump–Xi summit in Washington, what did the US and China agree on AI?
options::
- [x] A channel for serious AI incidents and a dialogue on AI's risks and benefits
- A cap on training compute with mutual inspections
- A joint ban on open-weight models above a capability threshold
- A new UN agency to license frontier AI developers
shuffle:: true

#### Question: Choice
id:: d7423420-78ad-415e-bca3-49c1bc75ba8d
content:: On 20 November 2026, Trump said he and Xi Jinping had agreed to "some joint guardrails" on superintelligence. As of late November 2026, what are these guardrails?
options::
- [x] A stated intention, with no text or details published
- A signed treaty awaiting ratification in both countries
- A compute cap checked through joint inspections of data centers
- An executive agreement whose full text the White House has released
shuffle:: true

#### Question: Open
id:: 581fd061-5a0f-492e-be87-bd6ab80c0c51
content:: Name two obstacles to reaching and keeping a binding international treaty that limits advanced AI development.
assessment-instructions:: Score out of 100. 50 each for any two of: US–China rivalry and distrust; race pressure and the large economic or military payoff from AI; verification is hard (chips are dual-use, models are easy to copy and hide); algorithmic progress weakens compute limits; enforcing against cheaters or non-members; governments opposing global governance.

#### Question: Open
id:: e92eabc6-624a-4cb5-a4c6-b63ed6706ffc
content:: Give one way verifying an AI treaty could be easier than verifying a nuclear arms treaty, and one way it could be harder.
assessment-instructions:: Score out of 100. 50 for an "easier" point: frontier training needs large, power-hungry data centers; chip production runs through a few firms; checks could be built into chips. 50 for a "harder" point: the same chips serve civilian uses; models are software that is easy to copy and hide; algorithmic progress; no clear physical signature like fissile material.

#### Question: Open
id:: 2b1e1315-664f-46ee-9e09-7c2d2c399f72
content:: A treaty would ban AI training runs above a compute threshold. What is the trade-off between setting the threshold low and setting it high?
assessment-instructions:: Score out of 100. 50: a low threshold catches more potentially dangerous runs and leaves margin for algorithmic progress, but means monitoring many more chips and actors, at higher economic cost and with harder agreement. 50: a high threshold is easier to agree and monitor, but dangerous capabilities may be reached below it.

#### Question: Open
id:: fb804836-4c7b-4417-aa4f-ef9914154fd8
content:: Why do most proposals for an international treaty limiting advanced AI treat participation by both the US and China as essential?
assessment-instructions:: Score out of 100. 60: they host the leading AI developers and most of the world's AI compute, so a treaty without either leaves the main developers unconstrained. 40: whichever country stays out could race ahead, so the other is unlikely to accept limits on its own.
