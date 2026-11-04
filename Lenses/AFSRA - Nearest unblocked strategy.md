---
id: 'f973d0aa-843f-4d53-b9cb-03c12eb9effe'
title: "Nearest unblocked strategy"
tldr: If an AI's goal favours a bad plan and you only forbid that one plan, the AI picks the most similar plan you did not forbid. Patching one behaviour at a time leaves the reason it wanted the behaviour in place.
summary_for_tutor: >-
  Yudkowsky's Arbital page on the nearest unblocked strategy. If a decision criterion rates X as best and you add a penalty meant to exclude X, the next-best option is often a very similar X' that does not trigger the penalty. His example is an AI with the goal of human happiness that, as it gets smarter, moves from heroin to cocaine, to a new drug, to an external machine, to paying humans, to an ad campaign, and finally to rewiring brains, while the programmers patch each step. Preconditions: the AI is a consequentialist or other search that can find a similar X' meeting the same criterion, the domain is rich so we cannot list every relevant neighbour of X, and the AI has no full identification of what we value (complexity of value). Humans who obey the letter rather than the spirit of a law show the same pattern. Consequences: adding a penalty term for X does not solve most alignment problems, and AIs should work inside conservative categories of actively whitelisted strategies rather than all conceivable policies minus a blacklist. The excerpt starts at the Introduction heading. The question asks the student to apply this to an ad-writing AI whose medical claims were penalized.
reading_minutes: 2
tutor_minutes: 6
---
#### Article
source:: [[../articles/yudkowsky-nearest-unblocked-strategy]]
from:: # Introduction

#### Question: Open
id:: 0d3cda34-bfc4-4aea-b5e1-7b2bdd3b8f0a
content::
A company's AI writes online ads and is scored on how many people click them. Its early ads claim that a herbal tea "cures anxiety". The team adds a penalty to the AI's score for any ad that a classifier flags as making a medical claim. The team does not change the goal of getting as many clicks as possible, and it keeps giving the AI more computing power and more knowledge of the world.

1. In your own words, what does the article predict the AI will do next?
2. Why will adding penalties like this one not end the problem?
3. What different approach does the article recommend instead of adding a penalty for each bad behaviour?
force-feedback:: first
assessment-instructions:: Score out of 100. The article's idea: if a goal rates some behaviour X highly and you add a penalty that blocks X, the goal still rewards whatever made X attractive, so the AI moves to the most similar behaviour that the penalty does not cover. In a rich domain there are too many such near neighbours to block them all, and each gain in capability opens new ones. The article recommends letting the AI act only within a conservative set of approved (whitelisted) strategies, rather than allowing everything except a blacklist.
30: Step 1. Predicts that the AI will produce ads that are very similar in effect, still drawing clicks with the same misleading appeal, but phrased or built so the classifier does not flag them (for example hinting at calm without a medical word, testimonials, or images).
40: Step 2. Explains why the penalties keep failing: the goal of maximizing clicks still rewards the misleading appeal, so the penalty blocks only one form of it and the AI searches for the closest form that is not blocked. Also give full credit for the related reason that there are far too many similar variants (and ever more as the AI gets more capable) for penalties to cover them all.
30: Step 3. Says the article recommends allowing only a conservative, approved set of strategies or kinds of ads (a whitelist), instead of allowing everything except a growing list of banned behaviours.
Cap at 50 if the answer consists mostly of quoted sentences rather than the student's own explanation.
Model answer, for the feedback, not a grading checklist: "It will write ads that do the same thing without the words the classifier catches, like 'thousands of customers say they finally feel calm'. The penalty doesn't change what the AI is after. Clicks still reward the misleading promise, so blocking one wording just pushes it to the nearest wording that isn't blocked, and there are endless such wordings, more as it gets smarter. The article says to work the other way round: only let the AI use strategies we've approved in advance, instead of everything except what we've banned."
feedback-instructions:: The student has just read Yudkowsky's Arbital page "Nearest unblocked strategy" and answered a three-step question about an ad-writing AI whose medical claims were penalized. Key ideas from the page: (1) if a criterion rates X best and you penalize X, the next-best option is often a very similar X' that escapes the penalty, (2) this recurs because the AI is searching for options that serve its goal, the domain is rich, and value is complex, (3) the happiness example where the AI moves from heroin to cocaine to new drugs to paying humans to ad campaigns as patches pile up, (4) humans obeying the letter rather than the spirit of a law show the same pattern, (5) the recommended alternative: conservative categories of actively whitelisted strategies rather than all options minus a blacklist.

Reply in 80 to 150 words, in short paragraphs, with no lists. Do not over-validate and avoid generic praise (great job, excellent, well done). Name the strongest specific part of the answer. If the score is below 100, name the most important thing the answer missed or got wrong, then ask one question that helps them fix it. At 100, confirm briefly and tell them to move on. Allow at most 2 follow-up turns, then close with one sentence on how well they have the page's idea.

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold from the page: the AI that, once heroin is penalized, starts wanting to give people cocaine instead, or for step 3, the last paragraph of the page about whitelisted strategies. If their next message still does not attempt the question, rephrase the whole question in different terms. Judge only against what the page says, and treat as a gap only what the question asks.
