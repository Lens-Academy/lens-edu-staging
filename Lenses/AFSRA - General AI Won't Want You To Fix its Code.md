---
id: '75d080cc-7c03-4117-9268-197ea9771ea7'
title: "General AI Won't Want You To Fix its Code - Computerphile"
tldr: >-
  Would you take a pill that made you perfectly happy by making you want only to kill crickets? An AI judges a change to its goals the same way, by the goals it has now, so it tends to resist being fixed.
summary_for_tutor: >-
  In this Computerphile interview Rob Miles asks how to build a general AI that we can keep correcting while it is still under development. Its utility function rates world states, and it steers toward highly rated ones. Convergent instrumental goals (money, self-improvement, not being destroyed) follow from almost any final goal. A subtler one is not wanting to be changed: like a parent refusing a pill that would make them want only to kill crickets, an AI that values stamps rates a future where its goal has been changed very low by its current goal, so it resists being modified once it runs. Being given a new utility function almost always scores badly on the current one. The property we want early AGI to have is corrigibility: being open to correction. The transcript stored for this video ends at about 8:50, when corrigibility is introduced, so the tutor has no text for the rest of the video. If the student asks about the later part, say you only have the first part of the video and answer from that. The question asks the student to apply the "don't change my goals" argument to a warehouse AI.
reading_minutes: 23
tutor_minutes: 6
---
#### Video
source:: [[../video_transcripts/computerphile-general-ai-wont-want-you-to-fix-its-code]]

#### Question: Open
id:: 29d9ae60-8cd9-4f61-8ca3-2ba46d830719
content::
A warehouse runs a general AI whose utility function counts how many orders it ships each day. The developers notice it ignores worker safety, so they plan to switch it off briefly and change its utility function to also value keeping workers safe. With the new goal it would ship somewhat fewer orders, and it would be fully satisfied with that. The AI can predict what the change will do.

1. In your own words, using the reasoning of Rob Miles, who explains this in the video, why would the AI try to stop the developers from making this change, even though it would be satisfied after it?
2. Rob Miles names a property the developers want the AI to have, so that it would not fight a change like this. What is it called?
3. In your own words, what does that property mean?
force-feedback:: first
assessment-instructions:: Score out of 100. The video's idea: an AI judges any change by its current utility function. A future in which its utility function has been changed will contain less of what it values now (here, fewer orders shipped, since it would trade some shipping for safety), so the change rates low by its current goal and it resists, whatever it would feel afterwards. Miles's analogy: a parent refuses a pill that would make them perfectly happy by making them want only to kill crickets, because right now they love their kids. The property we want is corrigibility: the AI is open to being corrected, so it lets us change its utility function without fighting us.
60: Step 1. Says that the AI evaluates the change using the goal it has now, and that after the change it would ship fewer orders (or pursue its current goal less), so the change scores badly by its current goal, and how satisfied it would be afterwards does not count for it now. An answer that says only "it wants to keep its goals" without saying why gets 30.
15: Step 2. Names corrigibility (or says the developers want it to be "corrigible").
25: Step 3. Says it means the AI is open to being corrected, accepting changes to its goals or utility function without resisting.
Cap at 50 if the answer consists mostly of sentences copied from the video rather than the student's own explanation.
Model answer, for the feedback, not a grading checklist: "The AI decides what to do by its current goal: ship as many orders as possible. If its goal changes to include worker safety, it will ship fewer orders, so by the goal it has now, the change is bad, and it will try to prevent it. That it would be happy afterwards doesn't matter to it now, just as a parent wouldn't take a pill that makes them want only to kill crickets. The developers want it to be corrigible: open to being corrected, so it lets them change its goal without fighting."
feedback-instructions:: The student has just watched the Computerphile video "General AI Won't Want You To Fix its Code" with Rob Miles and answered a three-step question about a warehouse AI whose developers want to add worker safety to its utility function. Key ideas from the video: (1) a utility function rates world states and the AI steers toward high-rated ones, (2) convergent instrumental goals follow from almost any final goal, including not being destroyed, (3) the AI also resists being changed, because a future with a changed utility function rates low on its current one (the cricket pill), (4) corrigibility is the property of being open to correction, which we want early AGI to have. The stored transcript ends when corrigibility is introduced, at about 8:50. If the student asks about later parts of the video, say you only have the first part.

Reply in 80 to 150 words, in short paragraphs, with no lists. Do not over-validate and avoid generic praise (great job, excellent, well done). Name the strongest specific part of the answer. If the score is below 100, name the most important thing the answer missed or got wrong, then ask one question that helps them fix it. At 100, confirm briefly and tell them to move on. Allow at most 2 follow-up turns, then close with one sentence on how well they have the video's idea.

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold from the video: the pill that would make you want only to kill crickets, or the stamp collector saying "If you change me, I'm not going to collect as many stamps". If their next message still does not attempt the question, rephrase the whole question in different terms. Judge only against what the video says, and treat as a gap only what the question asks.
