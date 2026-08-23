{++{"author":"Elias's AI","timestamp":1787493268253}@@---
id: '24af6011-7df7-4d76-a99c-05a507c58f18'
title: Reading with a tutor
tldr: The source arrives on the page, not on a reading list. You answer in your own words, a grader scores it against a rubric you never see, and the page stays incomplete until you have actually talked to the tutor.
summary_for_tutor: "Tour page demonstrating the reading workflow. Two Article excerpts from the Wikipedia overview of existential risk from AI (the opening definition, then the paragraph on expert disagreement, the second inheriting the first's source), a graded open question built as a wedge against argument from authority, and an open tutor chat gated by min_chat_messages 2. The learning outcome in play is what expert concern does and does not establish."
reading_minutes: 6
tutor_minutes: 6
min_chat_messages: 2
---

#### Text
content::
:::callout {title="What this page demonstrates" tone="blue"}
An **Article segment**: the assigned reading rendered inside the lens, with its author, publication date and a link to the original, and with the parts you were not assigned collapsed rather than deleted. The second excerpt below inherits the first one's source, so a multi-part reading is authored as a set of start and stop anchors rather than as copied text.

Then a **graded question**: you write an answer, a grader scores it against a rubric the author wrote and you never see, and a tutor responds to what you actually said.

Then a **gated chat**. This page will not let you mark it complete until you have sent two messages to the tutor. That gate is one line in the source file, and it is the difference between a course you can click through and a course you have to do.
:::

#### Article
source:: [[../articles/wikipedia-existential-risk-from-ai]]
from:: "**Existential risk from artificial intelligence**"
to:: "the actions of a future machine superintelligence."

#### Text
content::
That is the claim, and the gorilla comparison is the argument for it. The next question is who believes it and on what basis. Note that the material between the excerpts is still there, collapsed, one click away: a learner who wants the whole article is never blocked from it, and a learner who wants only the assigned part is never buried in it.

#### Article
from:: "Experts disagree on whether artificial general intelligence"
to:: "increased focus on global [AI regulation]"

#### Text
content::
One more excerpt, from further down the same article. The worry is considerably older than the technology that provoked it, which is worth knowing before deciding how much the recent wave of statements adds.

#### Article
from:: "One of the earliest authors to express serious concern"
to:: "signed by numerous experts in AI safety and the AI existential risk which stated:"

#### Question
content::
\## Where does this argument break?

A friend reads the passage above and concludes: "Hinton and Bengio are worried, hundreds of experts signed the statement, and the survey found a majority putting the risk at 10 percent or more. LeCun disagrees, but he is outnumbered. So the case is settled."

Every fact in that summary is in the text. The conclusion still does not follow. In a few sentences: what is wrong with the inference, and what would a stronger version of the argument have to do instead?

assessment-instructions::
The learner has just read the opening of the Wikipedia overview of existential risk from AI, including the paragraph on expert disagreement, and has been handed a deliberately flawed inference: that a headcount of concerned experts settles the question.

This is practice, not the test. Your job is to find out whether the learner can separate a claim about people from a claim about the world.

What a strong answer contains, in any wording:
- Counting signatories measures the distribution of opinion in a population, not the truth of the proposition. It is evidence about experts, not about AI.
- The signatories are not a random sample, the statement is short enough that signing it commits a person to very little, and the survey cited had a 17 percent response rate, so the population it describes is not the population of AI researchers.
- A stronger argument has to state the mechanism: what capability, acquired how, would produce what kind of loss of control. Expert concern can motivate looking at the mechanism, it cannot substitute for it.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct. Do not over-validate. Avoid generic praise (great answer, exactly right, well spotted).
- If the learner names the mechanism gap, say so plainly and push one step further: ask what evidence about the mechanism would actually move them.
- If the learner only says "appeal to authority" without saying what the argument is missing, name that gap in one sentence and ask them to supply it.
- If the learner defends the inference, do not concede and do not lecture. Ask what they would say if the same headcount had gone the other way.

Close by pointing them at the chat below, where they can take the disagreement further.

#### Chat
instructions::
The learner has just read the opening of the Wikipedia overview of existential risk from AI (the definition of AI x-risk, the gorilla comparison, the intelligence explosion sketch, and the paragraph on expert disagreement) and has answered a question about why counting worried experts does not establish the claim.

This is an open conversation. Follow the learner, do not run a curriculum.

Useful directions if they are unsure where to start:
- What would have to be true about an AI system for "we lose control" to be more than a story? Push toward capability, goal formation and oversight, not vibes.
- Yann LeCun's position that machines will have no desire for self-preservation: what is the strongest version of it, and what would falsify it?
- The gorilla comparison in the text does work for the conclusion. Where does the analogy hold, and where does it break?
- The intelligence explosion claim and the AlphaZero example: the article itself notes that AlphaZero did not recursively improve its own architecture. What does the example actually support?

Keep replies short, two or three short paragraphs. Ask one question at a time. Treat disagreement with the article as a legitimate stance and make the learner state what would change their mind. Do not resolve the question for them.

#### Text
content::
:::callout {title="Why the gate" tone="amber" collapse="closed"}
Reading time is a bad proxy for learning, and completion clicks are a worse one. A lens can require a minimum number of tutor messages, a completed answer, or both, and the page shows a live checklist of what is still outstanding. Everything a learner writes here is the raw material for the test at the end of this module, and for the cohort report a facilitator sees before the group meets.
:::
++}