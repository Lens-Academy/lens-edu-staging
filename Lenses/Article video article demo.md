---
id: 68f8a820-80eb-45e4-b95d-77eef358f817
{++{"author":"Elias's AI","timestamp":1783848769189}@@tldr: "Demo lens showing how one lens can interleave content from different sources: an article excerpt, then a video excerpt, then a second article excerpt. It illustrates that article and video source inheritance are tracked separately, so the later article segment still inherits the earlier article's source even though a video block sits between them."
summary_for_tutor: "A demonstration lens that stitches together three excerpts: a passage from the Wikipedia article on existential risk from AI, a 0:00-0:30 clip from a Kurzgesagt video, and a second passage from the same Wikipedia article. Its purpose is to show source-inheritance behavior — article and video sources are inherited independently, so the trailing article segment reuses the earlier article source despite the intervening video. No learning assessment."
++}title: Article video article demo
---

#### Text
content::
This lens mixes an article excerpt, a video excerpt, and then another article excerpt.

#### Article
source:: [[../articles/wikipedia-existential-risk-from-ai]]
from:: "**Existential risk from artificial intelligence**"
to:: "irreversible [global catastrophe]"

#### Video
source:: [[../video_transcripts/kurzgesagt-ai-humanitys-final-invention]]
from:: 0:00
to:: 0:30

%% Article and video source inheritance are separate. The next article segment still remembers the previous article source, even though we put a video in between. %%
#### Article
from:: "> The upshot is simply a question of time"
to:: "moment question."
