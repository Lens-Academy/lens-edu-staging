---
id: '239089c3-9588-4163-b941-ae471a59f460'
title: "Goodhart's Curse"
tldr: Like the auction winner who most likely overbid, the option that scores highest on an imperfect measure is most likely the one the measure overrates. The harder an AI searches, the more it finds and exploits the measure's errors.
summary_for_tutor: >-
  Yudkowsky's Arbital page on Goodhart's Curse, his name for the combination of the Optimizer's Curse and Goodhart's Law. The Winner's Curse says that when many bidders make unbiased estimates, the winner probably overbid. The Optimizer's Curse generalizes this: the action with the highest estimated utility probably has an upward error, actions with high-variance estimates are selected for, and the problem grows as a larger space is searched, including implicitly by gradient ascent. Goodhart's Law: when a measure becomes a target, it stops being a good measure (bank capital reserves, IBM paying per line of code). Goodhart's Curse: a powerful agent neutrally optimizing a proxy U of our true values V seeks out places where U diverges upward from V, especially where value learning worked poorly, and this gets worse as the AI becomes more powerful. No evil genie is needed. The page then argues that telling the AI to treat U as an estimate of V (the V, T, U distinction), or relying on moral uncertainty, still leaves errors that Goodhart's Curse seeks out. It notes the exact conditions are not yet known (a positively correlated normal distribution, the smile maximizer), and names mild optimization and conservative strategies as research avenues. The question asks the student to apply the curse to a powerful search over chatbot answers scored by a reward model.
reading_minutes: 13
tutor_minutes: 8
---
#### Article
source:: [[../articles/yudkowsky-goodharts-curse]]

#### Question: Open
id:: cedd0afa-c20f-4945-bc21-56fe79fa8aa1
content::
A lab trains a reward model to score chatbot answers for how helpful they are. Across typical answers its scores are right on average: it overrates some answers and underrates others by about the same amount. The lab then uses a powerful search to pick, out of millions of candidate answers, the one with the highest score. Some kinds of answers, such as answers in unusual formats, were rare in the reward model's training data, so its scores for those are much less reliable. They are still right on average, but with much bigger errors in both directions.

Answer in your own words.

1. Why should the lab expect the top-scoring answer to be less helpful than its score says, even though the scores are right on average?
2. Why is the top-scoring answer especially likely to be one of the unusual answers whose scores are unreliable?
3. According to the article, what happens to the gap between the top answer's score and its real helpfulness if the search is made more powerful and considers far more candidates?
force-feedback:: first
assessment-instructions:: Score out of 100. The article's ideas used here: when you pick the option with the highest estimated value, you also pick for estimation errors in its favour, so the winner's score probably overstates its true value even if every estimate is unbiased on average (the Winner's and Optimizer's Curse). Estimates with more variance produce larger upward errors, so the top of the ranking is dominated by options whose estimates are noisy. Searching a larger space makes this worse, because a stronger search finds more and larger places where the proxy U is above the true value V.
40: Step 1. Explains that choosing the single highest score selects for answers whose score happened to be too high: among millions of answers, the one at the top is likely there partly because the reward model overrated it, so its real helpfulness is probably lower than its score.
30: Step 2. Explains that unreliable scores vary more, so some unusual answers get very large overestimates by chance, and those large errors are what push an answer to the very top.
30: Step 3. Says the problem gets worse: a more powerful search over more candidates finds bigger overestimates or more flaws in the reward model, so the gap between the winning score and real helpfulness grows.
Cap at 50 if the answer consists mostly of quoted sentences rather than the student's own explanation.
Model answer, for the feedback, not a grading checklist: "If you pick the top score out of millions, you're also picking the answer the model got most wrong in its favour. Some answers are overrated by chance, and the most overrated ones float to the top, so the winner is probably worse than its score. The unusual answers have the noisiest scores, so they have the biggest lucky overestimates and are the most likely to win. A stronger search makes this worse, because it looks through more answers and so finds bigger errors to exploit."
feedback-instructions:: The student has just read Yudkowsky's Arbital page "Goodhart's Curse" and answered a three-step question about a powerful search that picks the top-scoring chatbot answer according to a reward model that is unbiased on average but unreliable on unusual answers. Key ideas from the page: (1) the Winner's Curse: the auction winner probably overbid, (2) the Optimizer's Curse: the action with the highest estimate probably has an upward error, high-variance estimates are selected for, and this worsens with a larger search, (3) Goodhart's Law: a measure that becomes a target stops being a good measure, (4) Goodhart's Curse: optimizing a proxy U of true values V seeks out places where U is above V, more so as the AI becomes more powerful, with no evil intent needed, (5) telling the AI to treat U as an estimate of V, or relying on moral uncertainty, still leaves errors the curse seeks out.

Reply in 80 to 150 words, in short paragraphs, with no lists. Do not over-validate and avoid generic praise (great job, excellent, well done). Name the strongest specific part of the answer. If the score is below 100, name the most important thing the answer missed or got wrong, then ask one question that helps them fix it. At 100, confirm briefly and tell them to move on. Allow at most 2 follow-up turns, then close with one sentence on how well they have the page's idea.

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold from the page: the auction where every bidder bids $10 plus random noise and the winner is probably someone who overbid, or for step 2, the five actions worth -$20 whose estimates have a standard deviation of $100. If their next message still does not attempt the question, rephrase the whole question in different terms. Judge only against what the page says, and treat as a gap only what the question asks.
