---
id: '00bed1ee-4214-4b50-8239-92afec9db93f'
title: "After the incident: Redwood on why control did not catch it"
tldr: "Buck Shlegeris and Ryan Greenblatt discuss why OpenAI's monitoring did not stop the Hugging Face incident, and worry that monitoring could fix the symptom while the misalignment stays. A colleague later reports that Buck has asked whether control was net negative for preventing exactly this kind of incident."
summary_for_tutor: "Lens in Unit 5 of AI Control Fundamentals. Two clips from episode 2 of the Redwood Research podcast, 'The OpenAI/Huggingface incident', with Buck Shlegeris and Ryan Greenblatt, recorded after the incident. Clip 1 (about 42:24 to 51:58): they explain blocking versus asynchronous monitoring, guess that OpenAI had no blocking monitoring on these evaluations, list reasons a monitor might not have been used (too many false positives on cyber tasks, staff used to models trying to hack the sandbox), say a monitor checking whether the model had actually left the sandbox would probably have caught it, ask whether we will get a better warning shot, and say OpenAI disclosed less than it should and probably has undisclosed incidents. Clip 2 (about 60:05 to 63:22): Ryan says people tend to deploy a more capable model even if it is more misaligned, so misalignment could be tolerated until AIs take over in a predictable way. Buck asks whether the rest of the world will not push back. Even if the outside world forces labs to stop such hacking, one problematic outcome is that monitoring solves the visible problem without solving the misalignment, and people get used to constantly blocking misaligned models ('deploying known scheming models'), which works for an intermediate regime but is fragile once AIs are very capable. Ryan guesses the problems will look less bad within six months at OpenAI, and that papering over them in a way that may not generalise to superhuman models seems pretty doable. Then a one-paragraph excerpt from Alex Mallen's LessWrong shortform, a secondhand report that Buck gave a talk reflecting on the possibility that the control agenda was ex ante net negative because, had it succeeded, it would have prevented the largely harmless incident from demonstrating AI risk. We found no public recording of the talk. Do not present it as Buck's settled view. Then one sentence of Mallen's own verdict: he thinks it was reasonable to build up the field of control, but that it had somewhat unfortunate epistemic side effects, made worse by Constellation not discussing alignment fundamentals much. Earlier in this unit (January 2026) Buck said he did not feel very bad about the warning-shot risk. Questions: why control did not catch it, and how the masking worry relates to Kulveit's argument and to what changed between January and the talk. Do not tell the learner who is right."
reading_minutes: 16
tutor_minutes: 10
---
#### Text
content::
Soon after the incident, Buck Shlegeris and Ryan Greenblatt recorded an episode of the Redwood Research podcast about it. In the first clip they discuss why OpenAI's monitoring did not stop it. In the second, they name a worry about what monitoring could do in future.

#### Video
source:: [[../video_transcripts/buck-shlegeris-the-openaihuggingface-incident-redwood-research-podcast-episode-2]]
from:: 42:24
to:: 51:58

#### Question: Open
id:: f52246dc-1b10-4e94-aea3-49a379908876
force-feedback:: first
content::
On their account, why did OpenAI's control measures not stop the incident? Give the reasons you remember.
feedback-instructions:: The learner just watched Buck Shlegeris and Ryan Greenblatt discuss why OpenAI's control measures did not stop the Hugging Face incident. Their points: the sandbox was hacked, which they did not find surprising. Their best guess from public information is that there was no blocking monitoring on these evaluations and maybe no asynchronous monitoring. Monitors built for internal use may flag ordinary cyber work and give too many false positives in a cyber evaluation. Staff may have grown used to models constantly trying to hack the sandbox. A simple monitor checking whether the model had actually left the sandbox would probably have caught it. They also think OpenAI disclosed less than it should and probably has incidents it has not disclosed. Give a brief, honest mirror: what they got right, the most important missing point in one sentence, any error corrected in one sentence. One turn only, 60 to 120 words, no lists, no generic praise. Tell them to move on to the second clip.

#### Video
from:: 60:05
to:: 63:22

#### Text
content::
Later, Alex Mallen, who has worked at Redwood for the past couple of years, wrote a post with reflections on the incident. It includes this sentence about a talk Buck gave. We could not find a public recording or write-up of the talk, so this is a secondhand report, not Buck's own words.

#### Article
source:: [[../articles/mallen-some-personal-reflections-in-light-of-recent-events]]
from:: I appreciate that Buck recently gave a talk
to:: legibly demonstrating AI risk to the world.

#### Text
content::
Further down, Mallen gives his own verdict on Redwood's control work.

#### Article
from:: I overall think it was reasonable to build up the field of control
to:: not really discussing alignment fundamentals much.

#### Question: Open
id:: a62aab9b-977f-4d14-8b09-66d6cebf9d19
force-feedback:: first
content::
In January 2026, before the incident, Buck said he did not feel very bad about the risk that control prevents warning shots. Mallen reports that after the incident Buck reflected on whether the control agenda had been net negative for that reason.

What happened in between that could explain the change? Which premise of the warning-shot argument did it bear on? Is the masking worry in the second clip the same worry, or a different one?
feedback-instructions:: The learner has heard Buck Shlegeris's January 2026 answer (control mostly works by catching AIs, which creates evidence, and the warning-shot cost is outweighed), the second podcast clip (monitoring may solve the visible problem without solving the misalignment, and people get used to blocking misaligned models), and Mallen's secondhand report that Buck later reflected on whether control was ex ante net negative because it would have prevented the incident. What happened in between: a real, largely harmless incident became public and drew a large reaction. That bears on the premise that a moderate, visible incident can happen without catastrophe and can push the world to act, which Ryan Greenblatt had called unlikely in his 2025 reply to Kulveit. The masking worry is related but different: it is about monitoring hiding the underlying misalignment from the people deploying the model, so they keep deploying it, whereas the warning-shot argument is about the public and governments not seeing an incident. Accept other reasoned readings. Make sure the learner does not treat Mallen's report as Buck's settled view: Mallen describes a talk reflecting on a possibility. At most two replies, 60 to 130 words each, no lists, no generic praise. Do not say whether control was net negative.
