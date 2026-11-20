---
id: 23752e57-47f9-427b-b7e2-b6f8a4b85e89
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how OpenAI went from a nonprofit research lab to a leading AI company with a for-profit arm, who leads it, and what it says about AI risk and how to manage it.

## Requires

## Helpful first
- [[AI companies]]

## Why it matters
OpenAI builds some of the most widely used AI systems, so its choices shape the pace of the whole field. Knowing how its structure, leadership fights and safety departures unfolded helps you judge its safety promises and the debate over whether a nonprofit mission can steer a commercial lab.

## Lenses
- [A Timeline of the Battle for OpenAI: Musk, Altman, and the For-Profit Shift (TIME)](https://time.com/7328674/openai-chatgpt-sam-altman-elon-musk-timeline/): the basic facts from the 2015 nonprofit to the 2019 capped-profit arm, Altman's firing and return in 2023, and the October 2025 restructuring that lifted the profit cap and left Microsoft with about 27% (October 2025).
- [Planning for AGI and Beyond (OpenAI)](https://openai.com/index/planning-for-agi-and-beyond/): Sam Altman sets out OpenAI's view that AGI could bring huge benefits but also existential risks, and why it releases ever more capable models step by step; its notes on the capped-profit structure are now out of date (February 2023).
- [Our Updated Preparedness Framework (OpenAI)](https://openai.com/index/updating-our-preparedness-framework/): how OpenAI tracks dangerous capabilities in biology, chemistry, cybersecurity and AI self-improvement, and the High and Critical thresholds that require safeguards before deployment or during development (April 2025).
- [OpenAI Exec Exits With Safety Concerns (CNN)](https://www.cnn.com/2024/05/17/tech/openai-exec-exits-safety-concerns): why Superalignment co-lead Jan Leike quit, saying "safety culture and processes have taken a backseat to shiny products", as the team was dissolved (May 2024).
- [Not For Private Gain: Open Letter on OpenAI's Restructuring (notforprivategain.org)](https://notforprivategain.org/): the critics' case from former OpenAI staff, legal scholars and Geoffrey Hinton that the nonprofit's control was what held profit and racing in check, and that removing it would hand the balance to shareholders; read Sections I and II (April 2025).

## Tests

#### Question: Open
id:: 16f16a71-535a-4ed7-a07f-ed59db261671
content:: OpenAI was founded in 2015 as a nonprofit. What reason did its founders give for choosing that structure?
assessment-instructions:: Score out of 100. 100 for: so that advanced AI (AGI) would be developed for the benefit of humanity as a whole rather than to make money for shareholders; or so it could pursue its mission free of the need for financial return. 50 for a vague answer about "doing good" with no contrast to profit. 0 for tax or legal convenience.

#### Question: FillBlank
id:: 57810b37-6010-4689-bbe7-d9f1a3580e06
content:: OpenAI's stated mission is to ensure that artificial general intelligence benefits {{all of humanity|humanity|all humanity|everyone}}.

#### Question: Choice
id:: 9ea93520-db1d-482b-b205-fd4de95738a1
content:: In 2019 OpenAI created a "capped-profit" company under its nonprofit. What was the main reason it gave?
options::
- [x] To raise the large sums needed for compute and staff
- To prepare for listing its shares on a stock exchange
- To meet new US rules on AI research funding
- To keep its safety research apart from product work
shuffle:: true

#### Question: Choice
id:: 57277cd4-a32a-4f49-bd1e-16488a9f1fa8
content:: In November 2023, OpenAI's nonprofit board removed CEO Sam Altman, saying he had not been consistently candid with it. What happened next?
options::
- [x] He returned as CEO within days, and most of the board left
- He stayed out, and Mira Murati became the permanent CEO
- He started a rival lab, which Microsoft later bought
- A court ordered him reinstated several months later
shuffle:: true

#### Question: Choice
id:: 16d9b6f0-183a-4191-8669-5f5f5638f3aa
content:: What did OpenAI's for-profit arm become in the restructuring it completed in October 2025?
options::
- [x] A public benefit corporation in which the nonprofit holds a large stake
- A subsidiary of Microsoft, in which the nonprofit keeps a small stake
- A publicly traded company, with the nonprofit wound up and dissolved
- An ordinary corporation owned only by its investors and staff
shuffle:: true

#### Question: Choice
id:: a6034dca-94a3-4154-9ec9-6c5f1c54accb
content:: OpenAI's 2019 structure capped the returns its investors could make. What happened to that cap in its October 2025 restructuring?
options::
- [x] It was removed, so investor returns are no longer capped
- It was kept at 100 times each investor's stake
- It was lowered, as a condition set by state regulators
- It was kept for early investors and dropped for new ones
shuffle:: true

#### Question: Choice
id:: ced003bb-c91a-4ad5-ace9-9e6be700dffd
content:: As of November 2026, what is Microsoft's relationship to OpenAI?
options::
- [x] A major investor holding a large minority stake
- The majority owner, which appoints OpenAI's board
- A competitor with no financial ties to OpenAI
- A cloud supplier and lender with no ownership stake
shuffle:: true

#### Question: Choice
id:: 09b9e493-bec8-48c3-ae47-5ded52fd76db
content:: OpenAI's 2018 Charter includes a clause about what OpenAI would do if a value-aligned, safety-conscious project came close to building AGI before it did. What does the clause commit OpenAI to?
options::
- [x] Stop competing with that project and start assisting it
- Keep competing, but share its safety research with that project
- Ask governments to review that project before it deploys
- Offer to buy that project and its staff
shuffle:: true

#### Question: Open
id:: 9cf7336e-5981-445d-ae13-95529c18b9cf
content:: OpenAI's leaders, including Sam Altman, have said advanced AI could pose catastrophic risks, even human extinction. Why do they say OpenAI should keep building it anyway?
assessment-instructions:: Score out of 100. 100 for both: the benefits could be enormous (e.g. science, medicine, abundance), and someone will build it regardless, so it is better for a safety-focused lab to be at the frontier and shape how it is done (releasing it gradually so society can adapt also counts). 50 for only one of these. 0 for saying they deny the risks. The answer need not agree with OpenAI.

#### Question: Choice
id:: f93b9edf-285b-4766-b950-b84447b131de
content:: What is OpenAI's stated reason for "iterative deployment", its strategy of releasing increasingly capable models step by step?
options::
- [x] Society gets time to adapt, and the lab learns from real use
- Frequent releases keep rivals from copying its research
- Smaller steps keep each model cheaper to train and to run
- Regulators can sign off on each model before the next is trained
shuffle:: true

#### Question: Choice
id:: 95ea5a20-62ce-46ca-b8b2-d7af0cd72a07
content:: In May 2024, Jan Leike, co-lead of OpenAI's Superalignment team, resigned. What was his main public criticism of OpenAI?
options::
- [x] Safety culture and processes had taken a back seat to products
- It was releasing its models too slowly to stay competitive
- It was publishing too much safety research openly
- Government rules were blocking his team's research
shuffle:: true

#### Question: Open
id:: 44aacc5e-6322-48a8-8720-edbac9cb7da9
content:: What is OpenAI's Preparedness Framework meant to do?
assessment-instructions:: Score out of 100. 100 for: track and test its models for dangerous capabilities (such as biological, chemical or cyber threats, or AI improving itself) and require safeguards, or hold back deployment, when a model crosses set risk thresholds. 50 for "a safety policy" or "testing models" without the idea of capability thresholds that trigger safeguards.
#### Question: Choice
id:: 653df571-c7af-40c6-9dcd-d238ad7c6e89
content:: OpenAI's 2025 Preparedness Framework says OpenAI may adjust its safety requirements in one situation. Which?
options::
- [x] A rival lab releases a high-risk model without comparable safeguards
- A government asks it to move faster for national security reasons
- Its investors vote to put a product launch ahead of further testing
- Its tests show that no current model is close to a risk threshold
shuffle:: true

#### Question: Open
id:: d4527943-4cac-414a-8887-15b6b7440bea
content:: In 2025 OpenAI turned its capped-profit company into a public benefit corporation with no cap on investor returns, with the nonprofit keeping a minority stake and the power to appoint its board. Critics say this makes AI risk worse. What is their main argument?
assessment-instructions:: Score out of 100. 100 for: profit and investor pressure push the company to commercialise and race faster, weakening the nonprofit's ability to put safety and its mission ahead of returns. 50 for "money corrupts" or "it's about profit" without linking this to safety or racing. The answer need not agree with the critics.
