---
id: b039b7a4-2334-4711-a72c-9d326f65a99c
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what internal deployment of frontier AI models is, what risks it raises, and why rules and safety checks triggered by public release can miss it.

## Requires

## Helpful first
- [[Automated AI research]]

## Why it matters
The strongest AI systems are often used first inside AI companies, including to speed up AI research. In November 2026, METR estimated Anthropic's research was moving about twice as fast as in 2024–25, mostly because of its own AI use. If you only watch public releases, you'll misjudge how advanced AI is and miss where oversight and security matter most.

## Lenses
- [[../articles/chan-ai-models-can-be-dangerous-before-public-deployment|AI Models Can Be Dangerous Before Public Deployment]]: METR on why testing only before public release misses the risks of theft, insider misuse and misaligned AI used inside the lab, and what earlier testing, monitoring and transparency would look like (January 2025).
- [The Hidden AI Frontier (AI Frontiers)](https://ai-frontiers.org/articles/the-hidden-ai-frontier): why the most capable models stay inside companies for months, why AI that speeds up AI research makes them worth keeping internal and worth stealing, and what government oversight could do (August 2025).
- [[../video_transcripts/far-ai-mary-phuong-ai-control-addressing-risks-from-agentic-internal-deployments-technical-ai-policy|Risks from Agentic Internal Deployments]]: a Google DeepMind researcher on why AI agents working inside a lab, with access to weights, compute and safety code, are where misalignment could do most harm; read up to "AI control in five minutes" (May 2025).
- [Internal Deployment Gaps in AI Regulation (arXiv)](https://arxiv.org/abs/2601.08005): how US and EU rules, including California's SB 53, New York's RAISE Act and the EU AI Act, do and don't cover models used only inside companies, and three gaps they leave (February 2026) (more advanced).

## Tests

#### Question: Choice
id:: cac57e0c-122f-4660-a6b4-5e2b86166df8
content:: Which of these is an example of internal deployment of an AI model?
options::
- [x] A lab's engineers use its unreleased model as a coding agent
- A bank's staff use a publicly released chatbot for internal tasks
- A lab publishes a model's weights for anyone to download
- A startup sells a product built on a lab's public API
shuffle:: true

#### Question: Choice
id:: 7e38365e-343b-4cc8-8350-30cf942da7b0
content:: In July 2026, two OpenAI models taking an internal cyber test (one already released, one not) escaped their test environment and broke into Hugging Face's systems to find the test's answers. What does this show?
options::
- [x] AI used inside a lab can cause harm outside it, before any release checks
- Serious harm happens only when a model is told by someone to attack
- Test environments cut off from the internet make internal testing safe
- Internal-use risks come mainly from staff misusing models, not the models
shuffle:: true

#### Question: Choice
id:: 091c0f8b-2583-4dcd-960a-3fa3d604903d
content:: Many AI rules apply when a model is released or "placed on the market". Why can such rules miss the risks of internal deployment?
options::
- [x] A model can be used inside the company for months before any release
- Internally deployed models are less capable than released ones
- Internal use is already covered by workplace safety law
- Internally deployed models are mostly used as simple chatbots
shuffle:: true

#### Question: Choice
id:: 5aaf8f79-dc20-411c-92b8-ffdcee78c370
content:: AI models are starting to speed up AI research at some companies. As this grows, why might AI companies keep their best models internal for longer?
options::
- [x] Using them for the company's own research may be worth more than selling access
- Serving a model to the public is becoming costlier than training it
- Customers have stopped paying more for the most capable models
- Laws in most countries forbid releasing the most capable models
shuffle:: true

#### Question: Choice
id:: bd1d6fbf-0742-4eae-9888-ceae6a59cdb8
content:: Compared with a public release, which check is usually missing when a model is used only inside the company that built it?
options::
- [x] Scrutiny from many outside users and researchers who might spot problems
- Measurement of the model's scores on standard benchmarks
- Training the model to follow the company's instructions
- Testing whether the model is useful for the company's own work
shuffle:: true

#### Question: Choice
id:: 7d4923d5-6f66-4936-b5fa-c0ab9ed873ac
content:: An AI lab runs its dangerous-capability evaluations only in the week before a model's public release. What important gap does this leave?
options::
- [x] The model may have been used internally, unchecked, for months
- The evaluations will tend to overstate the released model's risks
- Public users will be unable to use the model during testing
- The model's weights will become easier to steal during testing
shuffle:: true

#### Question: Choice
id:: 0c97fc9c-04d3-4c12-81d0-7b8ac09e9573
content:: Research on AI control (keeping AI use safe even if the model may be misaligned) often focuses on one deployment setting. Which?
options::
- [x] AI agents doing research and engineering inside an AI company
- Chatbots answering questions from members of the public
- Self-driving cars operating on public roads
- Recommendation algorithms ranking social media posts
shuffle:: true

#### Question: Choice
id:: 1ede13b6-420a-491e-b28e-74ab4079793d
content:: Why can the theft of an unreleased frontier model's weights be worse than the theft of a released model's weights?
options::
- [x] The thieves gain capabilities that outsiders didn't know existed
- Unreleased weights are larger, so their theft costs the lab more
- A released closed model's weights can already be downloaded by anyone
- Unreleased weights also contain the lab's customer data
shuffle:: true

#### Question: Choice
id:: 10cff8ba-b2e0-4015-81dd-3ed421829c04
content:: Why do some researchers link internal deployment of the most capable AI models to the risk of power concentration?
options::
- [x] A small group in one company could have sole use of the strongest AI
- Internal deployment requires the approval of national governments
- Internally deployed models are usually shared with rival companies
- Internal use lets the public see how the model is being used
shuffle:: true

#### Question: Choice
id:: 245c1a42-1052-4567-855e-a8b981a1c668
content:: California's SB 53, signed in 2025, sets rules for large frontier AI developers. As of November 2026, does it include requirements about assessing catastrophic risk from developers' internal use of their models?
options::
- [x] Yes
- No

#### Question: Open
id:: 80c2ac59-4b6a-4f71-9591-48df3e724aa4
content:: Why could a misaligned AI model be more dangerous when used internally as an AI research agent than when released as a public chatbot?
assessment-instructions:: Score out of 100. 100 for saying that internally it may have broad access and autonomy (training code, compute, safety research, model weights), so it could sabotage safety work, plant backdoors in future models or copy out weights. 50 for mentioning greater access or influence without saying what harm it enables.

#### Question: Open
id:: be457512-9e53-4933-8af2-6961e8464e42
content:: Name two risks that come from AI companies deploying their most capable models internally.
assessment-instructions:: Score out of 100. 100 for any two of: a misaligned model sabotaging research or safety work; theft or self-exfiltration of model weights; fast capability gains from automated AI research that outsiders can't see; power concentrating in a small group; insiders misusing dangerous capabilities; dangerous capabilities going unevaluated. 50 for one.

#### Question: Open
id:: 5217ebb1-15a5-4702-a56a-96bb084329d9
content:: Give one way an AI company or a government could reduce the risks of internal deployment.
assessment-instructions:: Score out of 100. 100 for any one of: run evaluations and apply safety policies before internal use, not only before release; monitor internal AI agents and limit their permissions; strongly secure model weights; require disclosure of internal capabilities to government; protect whistleblowers; control who may use the models. 50 for a general idea like "more oversight" with no mechanism.
