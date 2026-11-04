---
id: '3b276b1d-0466-41b8-9848-0bc07706018a'
title: "Worst-case thinking in AI alignment"
tldr: >-
  "Assume the worst" can rest on several different reasons, such as being optimized against or wanting a solution that holds in any case. Which reason applies decides how you should answer someone who calls your scenario far-fetched.
summary_for_tutor: >-
  Buck Shlegeris argues that people in AI alignment often conflate distinct reasons for assuming things will go as badly as possible. He lists six: being optimized against (a misaligned AI searching for gaps in human oversight, where he agrees with Yudkowsky that "only a small part of the space is bad" is no comfort), selecting from a space that mostly contains bad options (Hubinger et al.'s claim that there are more paths to deceptive than to robust alignment, where SGD is not adversarial and so how common bad models are matters), making pessimistic assumptions so the solution generalizes, as cryptographers do (for example assuming no interpretability tools in order to develop an alternative to relying on them), aiming effort at the worlds where it has the most marginal impact, Murphyjitsu (stamping out many individually unlikely failures) and the planning fallacy. Each reason calls for a different reply when a scenario is called far-fetched. The question asks the student to identify the reason and the right reply in two cases: an AI whose proposed actions are reviewed by humans, and an oversight method that assumes no interpretability tools.
reading_minutes: 8
tutor_minutes: 6
---
#### Article
source:: [[../articles/buck-worst-case-thinking-in-ai-alignment]]

#### Question: Open
id:: 8d3cb590-fc2e-4523-9519-6e08c53ba977
content::
Two arguments come up in an AI safety team's meeting.

**Case 1:** The team is training an AI that may be misaligned. Humans review each action it proposes before the action runs. A teammate says: "Only a tiny share of possible actions would slip a harmful step past our reviewers, so we will probably be fine."

**Case 2:** A researcher is designing an oversight method that assumes no interpretability tools will be available. She expects some such tools to exist, but she wants a method that does not depend on them. A colleague objects: "That is unrealistically pessimistic. We will probably have some interpretability tools."

1. In Case 1, which of Shlegeris's reasons for worst-case thinking applies?
2. In your own words, and applied to this case, what reply to the teammate does that reason call for, according to Shlegeris?
3. In Case 2, which of his reasons applies?
4. In your own words, and applied to this case, what reply to the colleague does that reason call for, according to Shlegeris?
force-feedback:: first
assessment-instructions:: Score out of 100. The scenario: in Case 1, a possibly misaligned AI proposes actions that humans review, and a teammate argues that only a tiny share of actions would get a harmful step past the reviewers. In Case 2, a researcher's oversight method assumes no interpretability tools, and a colleague calls this unrealistically pessimistic. The reading's ideas: when you are being optimized against (a misaligned AI searching for something bad that humans miss), it does not matter that bad actions are a small part of the space, because the optimizer selects for them. To change your mind, someone would have to show there is no adversarial selection, or that such actions do not exist or cannot be found. When you make pessimistic assumptions to solve a problem in as much generality as possible, as cryptographers do, you agree the assumption may be unrealistic, but a solution that works under it also works in easier situations. Shlegeris's own example is assuming no interpretability tools in order to build an alternative to relying on them.
20: Step 1. Names the reason for Case 1, in any words: being optimized against (the AI is searching against the reviewers).
30: Step 2. Gives the reply for Case 1: a misaligned AI would search for exactly the actions the reviewers miss, so the small share of such actions does not make the team safe.
20: Step 3. Names the reason for Case 2, in any words: making a pessimistic assumption to get a solution that holds in general, as cryptographers do.
30: Step 4. Gives the reply for Case 2: the researcher can agree the assumption is pessimistic, and say that a method that works without interpretability tools will also work if such tools exist (or that the point is to have an alternative to relying on them). An answer that defends Case 2 by claiming interpretability tools will in fact be unavailable scores at most 10 on this step.
Give half the points of step 2 or step 4 if that step only reproduces the post's general wording without applying it to the reviewers or to the interpretability tools.
Model answer, for the feedback, not a grading checklist: "Case 1 is being optimized against. A misaligned AI is looking for exactly the harmful actions the reviewers would miss, so it doesn't matter that they are rare. The teammate would have to show the AI isn't searching, or that no such action exists. Case 2 is a pessimistic assumption made for generality, like a cryptographer assuming someone reads every message. The researcher can agree it is pessimistic, but a method that works without interpretability tools will also work if we have them."
feedback-instructions:: The student has just read Buck Shlegeris's "Worst-case thinking in AI alignment" and answered a four-part question about two cases: a possibly misaligned AI whose actions are reviewed by humans, and an oversight method that assumes no interpretability tools. Key ideas from the post: (1) being optimized against: a few remaining bad strategies are enough, so "bad actions are rare" is no comfort, (2) selecting over a space that is mostly bad: SGD is not adversarial, so what matters is how common bad models are, (3) pessimistic assumptions for generality, as cryptographers make, because solutions for harder settings work in easier ones, (4) aiming at the worlds where effort has the most marginal impact, (5) Murphyjitsu and the planning fallacy, (6) each reason calls for a different reply to "that's far-fetched".

Reply in 80 to 150 words, in short paragraphs, with no lists. Do not over-validate and avoid generic praise (great job, excellent, well done). Name the strongest specific part of the answer. If the score is below 100, name the most important thing the answer missed or got wrong, then ask one question that helps them fix it. At 100, confirm briefly and tell them to move on. Allow at most 2 follow-up turns, then close with one sentence on how well they have the post's ideas.

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold from the post: for Case 1, the team of ten smart humans looking for hidden gotchas in an unaligned AI's actions, or for Case 2, the example of relaxed adversarial training that assumes no access to interpretability tools. If their next message still does not attempt the question, rephrase the whole question in different terms. Judge only against what the post says, and treat as a gap only what the question asks.
