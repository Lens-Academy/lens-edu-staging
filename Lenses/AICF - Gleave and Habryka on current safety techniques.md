---
id: '9fdc047b-2ff2-449a-a37d-b3b9c541ee0c'
title: "Gleave and Habryka: are current safety techniques enough?"
tldr: "After the 2026 Hugging Face incident, Adam Gleave argues that existing techniques, used with care, could have stopped it. Oliver Habryka argues that stopping it would mostly have hidden the warning, and that the same techniques will not hold for the next, stronger models."
summary_for_tutor: "Lens in Unit 5 of AI Control Fundamentals. The learner watches the first 23 minutes of the FAR.AI debate 'Are Current AI Safety Techniques Enough?' between Adam Gleave (FAR.AI) and Oliver Habryka (Lightcone Infrastructure), moderated by Rocket Drew (The Information). Gleave: the Hugging Face incident could have been prevented at three layers (misalignment, control, incident response), the gap is implementation rather than research, and careful use of existing techniques could bring his P(doom) from about 15 percent to under 2 percent up to clearly superhuman systems. Habryka: trying harder might barely have prevented this incident but would not scale to the next model generation, current models are already superhuman hackers, most prosaic alignment work observes failures and trains them away, which hides evidence of misalignment, and at around 16:12 he paraphrases Buck Shlegeris as saying that if Buck had done a good job he might have prevented the Hugging Face incident and that would have been really bad. This is Habryka's paraphrase, not Buck's own words. Habryka says rigorous use of current techniques might move P(doom) from 80 to 90 percent, then says it is unclear to him whether prosaic alignment research has raised or lowered risk. The video is split at about 10:24, after Gleave's opening. The first question asks for Gleave's main claim, the second for Habryka's and how his reading of the incident differs. The third asks where they agree and where the disagreement starts, preparing for the crux practice in the next lens. Do not tell the learner who is right."
reading_minutes: 23
tutor_minutes: 12
---
#### Text
content::
In 2026 FAR.AI hosted a debate between Adam Gleave, CEO of FAR.AI, and Oliver Habryka, CEO of Lightcone Infrastructure, which runs LessWrong. The question was whether current safety techniques are enough, in the light of the Hugging Face incident. Control is one of those techniques, and both speakers talk about what it would have changed.

You will watch about 22 minutes in two parts: the moderator's setup and Gleave's opening (about 9 minutes), then Habryka's reply (about 13 minutes), with a short question in between. While you watch, note what each speaker thinks the incident shows. At about 16:12 Habryka describes something Buck Shlegeris said. Buck has written much of the case for control, which you read in Unit 1. This is Habryka's paraphrase, not Buck's own words.

#### Video
source:: [[../video_transcripts/far-ai-are-current-ai-safety-techniques-enough-adam-gleave-far-ai-oliver-habryka-lightcone]]
from:: 1:11
to:: 10:24

#### Question: Open
id:: 0a9a3cb3-f0b2-49ad-b3d3-480770d6de0b
force-feedback:: first
content::
Without rewatching, write down Gleave's main claim in one or two sentences. What does he think the Hugging Face incident shows?
feedback-instructions:: The learner just watched the moderator's setup and Adam Gleave's opening in the FAR.AI debate and is stating Gleave's main claim from memory. Gleave's main points: the incident was preventable at three layers (fixing the misalignment, control such as monitoring, and incident response), none of this needed a research breakthrough, the gap is between research and how developers implement it, and careful use of existing techniques could bring his P(doom) from about 15 percent to under 2 percent up to clearly superhuman systems. He also points to the lab boasting about a cyber benchmark six weeks after the incident as a sign that incentives point the wrong way. Give a brief, honest mirror: say what they got right without inflation, name the most important missing point in one sentence, and correct any error in one sentence. One turn only, 50 to 100 words, no lists, no generic praise. Tell them to watch Habryka's reply next.

#### Video
from:: 10:24
to:: 23:02

#### Question: Open
id:: ec6518a0-c0ab-4c50-ab77-b72a12ec454f
force-feedback:: first
content::
Without rewatching, write down Habryka's main claim in one or two sentences. What does he think the Hugging Face incident shows, and how does that differ from Gleave's reading?
feedback-instructions:: The learner just watched Oliver Habryka's reply to Adam Gleave in the FAR.AI debate and is stating Habryka's main claim from memory, compared with Gleave's. For reference, Gleave's main points: the incident was preventable at three layers (fixing the misalignment, control such as monitoring, and incident response), none of this needed a research breakthrough, the gap is between research and how developers implement it, and careful use of existing techniques could make risk low up to clearly superhuman systems. Habryka's main points: trying harder might barely have prevented this incident but would not carry over to the next generation, the models are already superhuman hackers, most current alignment work watches for failures and trains them away, which hides the evidence of misalignment, and nothing we have works without first seeing the failure. He paraphrases Buck Shlegeris as saying that preventing the incident would have been really bad. Give a brief, honest mirror: say what they got right without inflation, name the most important missing point about Habryka, or about how his reading differs from Gleave's, in one sentence, and correct any error in one sentence. If they present Habryka's paraphrase as Buck's own words, point out that it is Habryka's account. One turn only, 80 to 130 words, no lists, no generic praise. Tell them to move on to the next question.

#### Question: Open
id:: 18124f72-fbdf-4cae-9a66-7cd03958f5c8
force-feedback:: first
content::
Gleave and Habryka agree on more than it first seems. Name one thing they both accept, and the first point where they part ways.
feedback-instructions:: The learner is looking for common ground and the first point of disagreement in the Gleave and Habryka debate. Points both accept in this clip include: the incident shows real and severe misalignment, developers were careless, and the central problem is what happens with the next, more capable models. Points where they part: whether current techniques with more care will keep working on the next model generation (Gleave expects progress to be smooth enough to stay in a trial-and-error regime, Habryka thinks every technique depends on seeing failures first and breaks as models become superhuman), whether current models could have been kept in a sandbox at all, and whether doing current safety work well makes risk better or worse. Accept any reasonable answer supported by the clip. If the learner names a point of agreement that one of them actually rejects, say so in one sentence. If their point of disagreement is a difference in mood or tone, ask what claim about the world sits under it. At most two replies. Do not say who is right. 60 to 120 words per reply, no generic praise. Tell them the next lens practises exactly this: finding the crux.
