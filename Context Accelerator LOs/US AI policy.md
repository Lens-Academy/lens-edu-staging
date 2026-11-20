---
id: 0e7ac152-2499-4f9a-bf5e-a46efec3807b
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main federal US approaches to AI since 2025, including recent executive orders and the White House frontier accord, and explain the main arguments for and against federal preemption of state AI laws.

## Requires

## Helpful first
- [[AI industry lobbying]]

## Why it matters
Most frontier AI labs are based in the US, so US rules shape how the most capable systems are built and tested. Knowing which rules are binding, which are voluntary, and who can override whom helps you judge new proposals and see where advocacy can change outcomes.

## Lenses
- [Regulation of artificial intelligence in the United States (Wikipedia)](https://en.wikipedia.org/wiki/Regulation_of_artificial_intelligence_in_the_United_States): the plain facts in order: Biden's order revoked, the failed 10-year moratorium on state laws, CAISI, the December 2025 order, the March 2026 framework for Congress; read from "In January 2025, President Donald Trump revoked..." to the end of the federal material (November 2026).
- [The Most Likely Outcomes of Trump's Order Targeting State AI Laws (Carnegie Endowment)](https://carnegieendowment.org/emissary/2025/12/ai-trump-order-state-law-what-to-know?lang=en): what the December 2025 order tells the Justice Department and other agencies to do, why it can't override state law by itself, and the case for and against preemption (December 2025).
- [[../Lenses/phillips-robins-with-the-raise-act-new-york-aligns-with-california-on-frontier-ai-laws|RAISE Act and SB 53]]: what California's and New York's frontier AI laws require, and why Congress, not the president, is the likely route to preempting them (February 2026).
- [How does Trump's White House AI accord work? (Al Jazeera)](https://www.aljazeera.com/news/2026/9/30/how-does-trumps-white-house-ai-accord-work): who signed the voluntary September 2026 accord, what it commits them to, why it has no penalties, and the new order on the term "super intelligence" (September 2026).

## Tests

#### Question: Choice
id:: 3bf09503-c348-4b8c-b97d-9af2c18f2ade
content:: President Biden's 2023 executive order on AI (EO 14110) asked developers of the most powerful models to share safety test results with the government. What happened to it in January 2025?
options::
- [x] President Trump revoked it in his first days in office
- Congress turned it into permanent federal law
- A federal court struck it down as unconstitutional
- It stayed in force with minor amendments
shuffle:: true

#### Question: Choice
id:: 02f38910-436a-40f5-a514-274b43aee37f
content:: Which describes what happened to the US AI Safety Institute at NIST in 2025?
options::
- [x] It was renamed the Center for AI Standards and Innovation
- It became a regulator able to license frontier models
- It was merged into the Department of Defense
- It was closed and its staff moved to the states
shuffle:: true

#### Question: Choice
id:: c20be4df-4027-403d-b456-ac5f174b2364
content:: What was the main emphasis of the AI Action Plan the White House released in July 2025?
options::
- [x] Speeding up AI development, infrastructure and exports by cutting regulation
- Setting up a licensing regime for frontier AI developers
- Pausing frontier AI development until safety standards exist
- Handing AI oversight to a new international agency
shuffle:: true

#### Question: Choice
id:: 2a063cca-7d14-47d1-8975-31c698ef7366
content:: In mid-2025, a 10-year moratorium on enforcing state AI laws was proposed as part of a federal budget bill. What happened to it?
options::
- [x] The Senate voted to remove it, so it did not become law
- It passed, but federal courts blocked it
- It passed and froze most state AI laws until 2035
- It was cut to five years and then became law
shuffle:: true

#### Question: Choice
id:: dbae18eb-dae8-4f0e-acd5-ee06a0b59762
content:: In December 2025, President Trump signed an executive order seeking a single national AI policy framework instead of separate state rules. What did it do about existing state AI laws?
options::
- [x] Directed the Justice Department to challenge them in court
- Declared them void from the date of signing
- Created a federal agency to replace state AI regulators
- Ordered states to pause enforcing them for ten years
shuffle:: true

#### Question: FillBlank
id:: 4e975c40-0cd2-4f05-8dd5-9f52114b929c
content:: When a valid federal law overrides state laws on the same subject, this is called federal {{preemption}}.

#### Question: Open
id:: b1960b82-cbba-4499-9978-3cb19df10743
content:: Why can't a US president's executive order, on its own, override a state's AI law? What would be needed instead?
assessment-instructions:: Score out of 100. 50 for explaining that an executive order directs the federal executive branch and has no power of its own to cancel state law; preemption comes from the Constitution or from statutes passed by Congress. 50 for naming what is needed: Congress passing a preempting law, a federal agency rule made under powers Congress granted, or a court ruling the state law invalid (for example as unconstitutional or preempted by an existing federal law).

#### Question: Choice
id:: a85ba7ed-f6ee-40b2-8d1b-94af3d4bbc47
content:: As of November 2026, which best describes the federal effort to override state AI laws?
options::
- [x] It relies on an executive order and lawsuits; Congress has passed no preemption law
- It relies on a 2026 act of Congress that overrides state laws on model development
- It relies on a 2026 Supreme Court ruling that states cannot regulate frontier AI
- It relies on a deal in which states agreed to pause their AI laws until 2030
shuffle:: true

#### Question: Choice
id:: 9fcea2ce-63ff-43f6-9830-02718a8239eb
content:: California's SB 53, the Transparency in Frontier AI Act signed in 2025, is one of the state laws at stake in preemption fights. What does it mainly require of large frontier AI developers?
options::
- [x] Publish a safety framework and report critical safety incidents to the state
- Get a state license before training a model above a size threshold
- Build a shutdown switch into every model they deploy in California
- Pay into a state fund that compensates people harmed by AI
shuffle:: true

#### Question: Choice
id:: 5602eacb-b87b-4071-9a69-90abeeefb0e8
content:: Executive Order 14434 (September 2026) tells federal agencies to say "super intelligence" instead of "artificial intelligence" in official communications. What does "super intelligence" cover in the order?
options::
- [x] The same technologies already defined as AI in federal law
- AI systems that exceed human ability at most tasks
- Frontier models trained above a set compute threshold
- AI systems built by US companies rather than foreign ones
shuffle:: true

#### Question: Choice
id:: e6de04d7-e527-453f-8828-84ff17ef9437
content:: In September 2026, leaders of several frontier AI companies signed the White House Accord on Super Intelligence. How are its commitments enforced?
options::
- [x] They are voluntary, with no legal penalties for breaking them
- A new federal agency can fine companies that break them
- The Center for AI Standards and Innovation must approve each release
- State attorneys general enforce them under consumer protection law
shuffle:: true

#### Question: Choice
id:: 8c78890d-ca73-42f9-b627-4eb63111078d
content:: Which of these is a commitment in the White House Accord on Super Intelligence, signed by frontier AI companies in September 2026?
options::
- [x] Working with independent external auditors on their safety controls
- Pausing training of models above a set compute level
- Giving the federal government copies of their model weights
- Publishing audit results before each model release
shuffle:: true

#### Question: Open
id:: 8f00393f-4413-48b6-a168-9ec167c759e2
content:: Give one argument for a federal law that preempts state AI laws, and one argument against it.
assessment-instructions:: Score out of 100. 50 for any one argument for: avoids a patchwork of conflicting state rules and compliance costs; AI products cross state lines; keeps US firms competitive; one expert national standard. 50 for any one argument against: with no federal frontier safety law, preemption could leave no binding rules; states can act faster and test approaches; respects states' powers; mainly serves industry interests.

#### Question: Open
id:: 2bcc61c9-6cb9-47e8-a597-cb659c30ffad
content:: Some AI company leaders who signed the voluntary White House Accord on Super Intelligence in September 2026 have also called for binding AI regulation. Why might a company want both?
assessment-instructions:: Score out of 100. 100 for any one of: binding rules apply to all competitors, so a careful company isn't undercut by less careful ones; voluntary commitments are easy to drop under competitive pressure; binding rules make commitments credible to the public. 50 for a vague answer about wanting to look responsible.
