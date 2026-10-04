---
id: 'a360d64c-a9ce-4b37-a661-adf9bc90267d'
title: "Would a catch change anything?"
tldr: "Suppose a developer catches its AI red-handed trying to escape. Buck Shlegeris argues that even then, competitors and governments could explain it away. Others reply that a real catch would be hard to dismiss. The catch route depends on who believes the evidence and acts on it."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control), right after 'Catching AIs red-handed'. The learner reads Buck Shlegeris's post 'Would catching your AIs trying to escape convince AI developers to slow down or undeploy?' (August 2024) in full: even a red-handed catch might not lead to slowing down, because a competitor can argue that stopping is too costly given the race with China, that AIs do weird stuff, that there is no evidence of power-seeking, that the competitor messed up its own alignment, or that the logs are forged or the model was rigged. Sceptics of the theoretical arguments might not end up above 50% on scheming, undeploying is expensive, and news might not leave the lab. His takeaways: be prepared for other developers not to undeploy, have plans for deploying possibly scheming models (one reason he researches control), plan how to persuade people, and sell the current arguments now. Then comments: Max Nadeau asks whether this is a change from treating a catch as a win condition. Shlegeris replies he is somewhat more pessimistic about catch-then-shut-down (you might need to catch the model about 30 times) but still optimistic about few-shot catastrophe prevention. Tom Davidson replies that a lab that caught a systematic schemer could produce highly credible scientific evidence and that many sceptics would change their minds, though the world would not definitely pause. Oliver Habryka's reply to Davidson says he would take bets against Davidson, because in practice nobody will be able to prove the model was scheming rather than role-playing. If the learner asks what happened later: in a 2025 80,000 Hours interview Shlegeris said his own update after a catch would be only about 3x, and Unit 5 covers how people argued about the real 2026 Hugging Face incident. This is the evidence-and-response part of the catch route and its dependence on political will. Do not say who is right."
reading_minutes: 11
tutor_minutes: 12
tags:
  - reading
---
#### Text
content::
The last reading counted a catch as a win, partly because it would make shutting down more likely. Here Buck Shlegeris, one of its authors, asks whether that is true. After his post come four comments from the discussion, including his own reply. All of these were written before the 2026 Hugging Face incident. Unit 5 looks at how people argued about that real case.

#### Article
source:: [[../articles/buck-would-catching-your-ais-trying-to-escape-convince-ai-developers-to-slow-down-or-undeploy]]

#### Question: Open
id:: 30c77db4-7b3c-4d15-93ed-8ab46964e35e
content::
Shlegeris imagines a competitor arguing against shutting down. Which of the competitor's arguments do you find most convincing, and what would a developer need to have prepared in advance to answer it?
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner just read Shlegeris's post. The competitor's arguments: stopping is extremely costly because China is racing, AIs are known to do weird stuff and one anomaly proves little, there is no evidence of power-seeking, the other company just messed up its own alignment, and the logs may be forged or the model rigged. Any choice is fine. Good answers name what could be prepared in advance, for example many independent catches rather than one, ways to let outsiders verify incidents and logs, agreement beforehand on what evidence would trigger a pause, or an international arrangement so stopping does not mean losing a race. Shlegeris's own takeaways include planning how to persuade people and selling today's arguments now. In at most five sentences, say whether the learner's preparation answers the argument they chose and name one thing that would strengthen it. Do not say whether a catch would work. No generic praise. At most two turns.

#### Article
source:: [[../articles/maxnadeau-comment-on-would-catching-your-ais-trying-to-escape-convince-ai-developers-to-slow-down-or-undeploy]]

#### Article
source:: [[../articles/buck-comment-on-would-catching-your-ais-trying-to-escape-convince-ai-developers-to-slow-down-or-undeploy]]

#### Article
source:: [[../articles/davidson-comment-on-would-catching-your-ais-trying-to-escape-convince-ai-developers-to-slow-down-or-undeploy]]

#### Text
content::
Oliver Habryka replied to Davidson:

#### Article
source:: [[../articles/habryka-comment-on-would-catching-your-ais-trying-to-escape-convince-ai-developers-to-slow-down-or-undeploy]]

#### Question: Open
id:: ceb1ae71-1e63-4130-b39e-e3554a28b22f
content::
Shlegeris now separates two things a catch could do: get a developer to shut down, and help it make later attempts fail. Which of the two depends more on political will, and why? Where does Davidson disagree with him, and what could you observe that would tell you who is closer to right?
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner read Shlegeris's post, his reply to Max Nadeau, Tom Davidson's comment and Oliver Habryka's reply. Shutting down (catch-then-shut-down) depends much more on political will: the developer, its competitors or governments must believe the evidence and accept the cost of stopping. Shlegeris is now more pessimistic about it (he imagines needing to catch the model around 30 times) but still optimistic about few-shot catastrophe prevention, which the developer's own safety team can do even if leadership keeps deploying. In the post he already notes that a competitor could claim the logs were forged or the model rigged. Davidson disagrees about persuasion: he thinks a lab that caught a systematic schemer could produce scientifically credible evidence, that many sceptics would change their minds, and that it would be a massive shift even if the world did not pause. Habryka replies that he would bet against Davidson, because in practice nobody will be able to prove the model was scheming rather than "role-playing", against a background of models that are obviously not aligned. Useful observations: how labs and governments respond to real misbehaviour incidents, whether incidents get published with verifiable evidence, whether ML researchers update after strong demonstrations of scheming. In at most five sentences, check both parts, correct any misreading in one sentence, and say whether their observation could actually be made. Do not say who is right. No generic praise. At most two turns.
