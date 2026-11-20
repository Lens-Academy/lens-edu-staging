---
id: f47f2593-e534-47de-92aa-a2e7e59608cb
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain when sharing true information can cause harm, tell hazards to the knower apart from exfohazards that cause harm by spreading, and weigh these risks against the benefits of openness when deciding what to publish about AI.

## Requires

## Helpful first

## Why it matters
Researchers often have to decide whether to publish a capabilities finding, a new way around a safety measure, or a promising research direction. If you can spot an information hazard, you can hold back or limit what is risky to share, without slipping into secrecy that slows safety work and hides problems from people who need to know.

## Lenses
- [What Are Information Hazards? (EA Forum)](https://forum.effectivealtruism.org/posts/Nc5EjccDTfmcrG93j/what-are-information-hazards): Bostrom's definition of risks from true information, data, idea and attention hazards, and hazards that harm only the knower (February 2020).
- [Don't Use "Infohazard" for Collectively Destructive Info (LessWrong)](https://www.lesswrong.com/posts/yET7wbjjJZtpz6NF3/don-t-use-infohazard-for-collectively-destructive-info): Eliezer Yudkowsky's short case for separating hazards to the knower, like spoilers, from "exfohazards" that do harm by spreading (July 2022).
- [[../Lenses/aaron-scher-the-unilateralists-curse-an-explanation|The Unilateralist's Curse, An Explanation]]: why a risky step, such as publishing a dangerous finding, gets more likely as more people can take it alone, and what to do about it (June 2022).
- [Conjecture: Internal Infohazard Policy (Conjecture)](https://www.conjecture.dev/research/conjecture-internal-infohazard-policy): how one AI safety company sorted work into secret, private and public, and why even saying it was interested in a technique counted as a hazard. Read "Overview and Motivation", "Considerations" and "Example Scenarios" (July 2022).
- [Strong Infohazard Norms Lead to Predictable Failure Modes (Beren Millidge)](https://beren.io/2023-08-09-Strong-Infohazard-Norms-Lead-To-Predictable-Failure-Modes): a former Conjecture researcher's case that heavy secrecy cuts off feedback, makes people overrate their ideas and leaves alignment behind capabilities, with his test for when withholding is justified (August 2023).

## Tests
#### Question: Choice
id:: 2a0a4835-fbbc-4680-b673-8552cc443e66
content:: In Nick Bostrom's sense, what makes something an information hazard?
options::
- [x] A risk of harm from true information being known or spread
- Harm caused by false or misleading information spreading
- Information that a government has classified as secret
- Personal data that is leaked without the owner's consent
shuffle:: true

#### Question: Choice
id:: ce3a897e-1353-4ed9-9daf-11e0ddb9f342
content:: Which of these is an exfohazard, rather than a hazard only to the person who learns it?
options::
- [x] A post showing anyone how to get around an AI model's safety safeguards
- A film spoiler that ruins the ending for the person who reads it
- A grim forecast that makes the reader too anxious to work
- A fact about a friend that the reader would rather not know
shuffle:: true

#### Question: Choice
id:: 3b7500e8-665d-4b46-8295-bd664ec6fa97
content:: Bostrom's "attention hazard" is one kind of information hazard. Which of these is an example?
options::
- [x] Pointing out loudly that a little-known, already published technique is very powerful
- Publishing a new technique that nobody had thought of before
- Overloading a research team with so many tasks that it loses focus
- A news story that leaves readers anxious about AI
shuffle:: true

#### Question: Choice
id:: c8e0a646-fc3a-441e-9fca-3d75c01fe75d
content:: Why can it backfire to announce publicly that you have found a dangerous AI technique, while refusing to say what it is?
options::
- [x] It tells others the technique exists and is worth searching for
- It makes other researchers less willing to share their own findings
- It breaks the publication rules of most AI conferences
- It makes people doubt that the technique is real
shuffle:: true

#### Question: Choice
id:: 1b785800-85b9-415f-b6f1-e86fbfb6b936
content:: You find a reliable way to make a widely used AI model ignore its safety rules. Following the coordinated ("responsible") disclosure norm from computer security, what would you do?
options::
- [x] Tell the model's developer privately, then publish once they have had time to fix it
- Publish at once, so that users and other companies can protect themselves sooner
- Tell no one, ever, including the model's developer
- Post full details to a researcher forum, so the developer hears of it from there
shuffle:: true

#### Question: Choice
id:: fb345869-dff0-46be-a1aa-fc14fcebc089
content:: Why might publishing exactly how an AI company's monitor flags suspicious actions by its AI agents make the monitor weaker?
options::
- [x] Attackers, or models trained on the text, could learn to avoid it
- Competitors could copy the monitor without paying for it
- The company could no longer change the monitor once it was public
- The published method could reveal private data the monitor has seen
shuffle:: true

#### Question: Choice
id:: 4e75cac7-2275-47bd-bad5-8a6928735e29
content:: Which of these is a common argument against keeping AI safety research findings secret?
options::
- [x] Other researchers can't check, correct or build on work they can't see
- Competitors could use the findings to catch up with the lab
- Bad actors could learn from them how safety measures work
- Some safety findings also show how to make models more capable
shuffle:: true

#### Question: Open
id:: 309eba14-8d29-4a1d-bee0-eafadd1eab68
content:: What is the difference between an exfohazard and a hazard to the knower? Give an example of each.
assessment-instructions:: Score out of 100. 60 for the distinction: an exfohazard causes harm through being spread to others (who may misuse it); a hazard to the knower harms the person who learns it (for example distress, bias or lost motivation). 20 for each fitting example. Partial credit for a correct distinction with weak examples.

#### Question: Open
id:: da009f42-1162-4aad-a0aa-38f2d1f8fcdc
content:: While doing safety research, you find a simple trick that makes AI models noticeably more capable. Name two options between publishing everything and telling no one.
assessment-instructions:: Score out of 100. 50 for each of any two reasonable options, such as: share privately with trusted safety researchers or the affected companies; publish the safety results without the method details; delay publication; ask experienced colleagues or a review process before deciding. No credit for full publication or total silence.

#### Question: Open
id:: 32a324a1-5253-4395-a4e4-f62cc7ce0140
content:: Give one way that worrying too much about information hazards can harm AI safety work.
assessment-instructions:: Score out of 100. 100 for any one of: slows research because others can't build on it; blocks peer review and error correction; keeps newcomers and outsiders from contributing; hides warning signs from policymakers or the public; serves as cover for avoiding accountability; withholds information that is already widely known anyway. 50 for a vague answer such as "secrecy is bad".
