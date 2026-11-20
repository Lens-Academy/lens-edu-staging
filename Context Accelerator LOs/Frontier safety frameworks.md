---
id: ad77f7eb-84b7-4932-add3-24c9a525af14
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how AI companies' safety frameworks link required safeguards to dangerous-capability thresholds, describe the voluntary commitments governments have brokered since 2023, and assess the main weaknesses of relying on them.

## Requires
- [[AI evaluations]]

## Helpful first

## Why it matters
Safety frameworks and voluntary pledges are how frontier AI companies say they will manage catastrophic risks. Governments mostly rely on them; a few laws, such as California's SB 53, now require large developers to publish and follow one. Knowing how they work and where they fail helps you judge companies' safety claims and what binding rules must add.

## Lenses
- [[../Lenses/AI Safety Atlas - Evaluations - Evaluation Frameworks|Evaluation Frameworks]]: how Anthropic, OpenAI and Google DeepMind use evaluations as gates for scaling.
- [[../Lenses/AI Safety Atlas - Governance - Governance Architectures|Governance Architectures]]: what corporate self-governance can and can't do next to national and international rules.
- https://metr.org/blog/2025-12-09-common-elements-of-frontier-ai-safety-policies/: what twelve companies' safety policies have in common (December 2025).
- https://www.governance.ai/analysis/anthropics-rsp-v3-0-how-it-works-whats-changed-and-some-reflections: what Anthropic's 2026 rewrite of its policy dropped, and the case for and against it.
- https://www.aljazeera.com/news/2026/9/29/trump-top-tech-firms-sign-accord-to-self-police-ai-development: the September 2026 White House accord and its critics.

## Tests
#### Question: Choice
id:: ce5b0c1a-d761-48da-a5b1-c6e1d7fe22d5
content:: What is the basic structure of a frontier safety framework, such as a responsible scaling policy?
options::
- [x] Set safeguards must be in place once tests find a dangerous capability
- A cap on the compute any one model may be trained with
- A government licence needed before training a large model
- A timetable of model releases agreed between competing companies
shuffle:: true

#### Question: Choice
id:: b49188bd-876b-4acb-8bad-32e855f6b8cc
content:: In most companies' frontier safety frameworks, who decides whether a model has crossed one of the framework's capability thresholds?
options::
- [x] The company itself, in some cases with outside review
- A national AI safety institute with legal authority
- An international body set up by treaty
- An industry panel that the companies elect each year
shuffle:: true

#### Question: Open
id:: e442c2ed-2226-426f-8401-ba1f41742dba
content:: A company tests its new model for a dangerous capability using little time, no fine-tuning and simple prompts, and finds it just below the threshold in its safety framework. Why might this result undermine the framework?
assessment-instructions:: Score out of 100. 100 for saying weak elicitation can underestimate the model's real capability, so the model may have crossed the threshold and the required safeguards won't be triggered. 50 for saying only that the test was inadequate without linking it to missing the threshold.

#### Question: Choice
id:: 95d61eb3-0664-4211-b5cc-99004392f256
content:: In February 2026, version 3.0 of Anthropic's Responsible Scaling Policy dropped wording that implied Anthropic would pause if it couldn't keep risks acceptable. What main reason did Anthropic give?
options::
- [x] A pause by one company does little if competitors keep going
- Its models had been shown to be aligned, so pauses were unneeded
- Governments had promised to impose any needed pause themselves
- Outside auditors had judged its safeguards enough to rule out catastrophe
shuffle:: true

#### Question: Choice
id:: 6c96d4bd-2cbb-47de-a9f5-b5001f5bca86
content:: Meta's 2025 frontier AI framework said it would stop developing a model judged to pose critical risk. How did Meta change this rule when it revised the framework in April 2026?
options::
- [x] It allowed development to go on with mitigations in place
- It handed the decision to stop to an outside safety institute
- It extended the stop rule to models posing only high risk
- It replaced the stop rule with a cap on training compute
shuffle:: true

#### Question: Choice
id:: b8440201-7af1-4a6f-a7c9-096f34e347bb
content:: At the AI Seoul Summit in May 2024, frontier AI companies signed the Frontier AI Safety Commitments. What did they commit to?
options::
- [x] Publish safety frameworks and not develop or deploy a model if risks can't be kept below thresholds
- Submit every new model to the UK AI Safety Institute for approval before it is released to the public
- Stop training any model above an agreed compute limit until an international treaty was in place
- Give the summit's host governments access to the weights of their most capable models
shuffle:: true

#### Question: Choice
id:: 1227517c-332e-4e30-a97e-23db9c56dce6
content:: What is the legal status of the 2023 White House AI commitments and the 2024 Seoul Frontier AI Safety Commitments?
options::
- [x] Voluntary, with no penalties for a company that breaks them
- Binding once each signatory's home government ratifies them
- Binding in the United States but voluntary elsewhere
- Enforced through fines set by national AI safety institutes
shuffle:: true

#### Question: Choice
id:: 021930bb-82ec-47ab-8797-1a14d3749435
content:: In September 2026, six AI companies signed the "Joint Commitment on Frontier Responsibilities" at the White House. Which of these does it include?
options::
- [x] Using independent external auditors to check the companies' safeguards
- A pause on training models above a set compute threshold
- Licensing of frontier models by a new federal agency
- Publishing the full results of every dangerous-capability test
shuffle:: true

#### Question: Open
id:: d592fc94-cb9b-4f89-95e2-08757856a134
content:: Give one reason critics doubt that the White House "Joint Commitment on Frontier Responsibilities", signed by six AI companies in September 2026, will constrain the companies much.
assessment-instructions:: Score out of 100. 100 for any one of: it is voluntary with no penalties; the companies drafted it; the companies choose and pay their own auditors; it sets no capability thresholds or clear standards; it is vague about what counts as compliance. 50 for a general complaint about self-regulation with no specific reason.

#### Question: Open
id:: 09fd1212-7689-4420-8324-7c564a1fe140
content:: Name two weaknesses of relying on companies' frontier safety frameworks to manage catastrophic AI risk.
assessment-instructions:: Score out of 100. 50 each for any two of: voluntary and self-enforced; the company can revise or weaken it at will; the company sets and judges its own thresholds; evaluations can miss capabilities; competitive pressure can override it; little outside verification; safeguards for higher capability levels are vague or undefined; some risks such as misalignment are covered poorly.

#### Question: Choice
id:: 93fff12d-ac56-4ca4-95b2-7438a3104e53
content:: Why might an AI company choose its required safeguards before a model reaches a dangerous-capability threshold, rather than deciding once it gets there?
options::
- [x] Decisions made early are less swayed by pressure to ship
- Advance choices let the company skip evaluations of later models
- Most countries' regulators require safeguards to be chosen in advance
- Advance choices bind competitors to adopt the same safeguards
shuffle:: true

#### Question: FillBlank
id:: 4fa83c63-d696-4809-8936-827720d781f3
content:: Anthropic's Responsible Scaling Policy groups the safeguards required at each level of model capability into {{AI Safety Levels|AI Safety Level|ASLs|ASL}}.

#### Question: Choice
id:: dc34c72a-df8e-454d-8f78-e795bbc76dc2
content:: Besides safeguards on how a model is deployed, what else do most frontier safety frameworks require once a model crosses a dangerous-capability threshold?
options::
- [x] Stronger security to stop the model's weights being stolen
- Releasing the model's weights so outsiders can audit it
- Reporting the model's full training data to a regulator
- Limiting the model's use to the company's home country
shuffle:: true

#### Question: Choice
id:: bd65cec6-b65c-476f-97d9-b03e4907ecda
content:: Did the voluntary AI commitments that seven companies made to the White House in July 2023 tie specific safeguards to capability thresholds?
options::
- [x] No
- Yes

#### Question: Choice
id:: 8938081c-bc56-4577-9653-f2c0ba712338
content:: After the 2024 AI Seoul Summit, did companies such as Meta, Microsoft and Amazon publish their own frontier safety frameworks?
options::
- [x] Yes
- No

#### Question: Choice
id:: 75330521-c0c3-4214-8b6a-e2ad4c4b163c
content:: In July 2023, seven leading AI companies made voluntary commitments to the White House. Which of these was among them?
options::
- [x] Test models internally and externally for security risks before release
- Pause training of any model more capable than GPT-4
- Submit new models to a federal licensing agency
- Publish their models' weights for outside researchers
shuffle:: true
