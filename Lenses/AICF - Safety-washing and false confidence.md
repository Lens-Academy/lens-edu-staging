---
id: 'c192c948-d095-40f3-b6f5-f843c9069855'
title: "Safety-washing and false confidence"
reading_minutes: 11
tutor_minutes: 12
tldr: "Oversight that nobody can describe in detail is, in David Manheim's words, \"a story\". A control measure can make a deployment safer, or it can mostly make people feel safe enough to deploy. And advanced AI could help a small group seize power, a risk that the tools of control could add to or help guard against."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The 'false confidence' and safety-washing criticism. The learner reads David Manheim's short post 'No, We're Not Getting Meaningful Oversight of AI' (July 2025, a linkpost for his paper with Aidan Homewood): oversight is invoked everywhere as the thing that prevents unacceptable outcomes, but meaningful oversight is often absent or impossible, so anyone claiming their AI is supervised should document what kind of supervision it is (control or oversight), which risks it addresses, its failure modes, and why it will work. 'If you can't do that, you don't have oversight. You have a story.' Then the list from Elias Schmied's 'A brief list of ways AI safety efforts could be net negative' (June 2026), which includes safety-washing and false security, capabilities externalities, an adversarial relationship with AIs, and AI moral patienthood. Schmied says he puts maybe 60% on AI safety having been net positive so far. Then a short excerpt from Greenblatt and Shlegeris's case for control: relying on control 'requires continued vigilance', which may be less likely if people conflate alignment with safety. Then a short excerpt on power concentration from Tom Davidson, Lukas Finnveden and Rose Hadshar, 'AI-Enabled Coups: How a Small Group Could Use AI to Seize Power' (Forethought, April 2025): today even dictators rely on others, but advanced AI could replace human workers with AI systems singularly loyal to one person, and loyal AI in government could increase surveillance, censorship, propaganda and the targeting of opponents. Then their recommendation of asynchronous logging and review of AI use to detect problematic use. The Lens text says honestly that the report is mainly about AI loyal to a few people, not scheming AI, and that monitoring and logging of the kind control relies on is among its recommended defences. This is the reading behind the Unit 4 test's criticism that control builds surveillance tools that could concentrate power: the tools could help concentrate power, and the same tools, held by several parties, can guard against it. Optional: the opening of Richard Ngo's 'What just happened? Pragmatism and Pessimization' (August 2026), arguing that 'pragmatic alignment' helped AI companies push toward AGI 'under the banner of safety'. Ngo's post is about alignment research generally, not control specifically. The pro-control reply to Manheim is that control evaluations produce exactly this kind of documentation. Do not tell the learner who is right."
---
#### Text
content::
Safety work could backfire by making people feel safer than they are. Here are two short pieces by people who worry about this, and what the authors of the case for control said about it.

#### Article
source:: [[../articles/davidmanheim-no-were-not-getting-meaningful-oversight-of-ai]]

#### Text
content::
Elias Schmied lists ways AI safety work in general could do harm. The items closest to control are the adversarial relationship with AI, AI moral patienthood, safety-washing, and capabilities externalities.

#### Article
source:: [[../articles/schmied-a-brief-list-of-ways-ai-safety-efforts-could-be-net-negative]]
from:: I’m not aware of a good list of downside risks for AI safety broadly
to:: contributed to the foundings of all three of DeepMind, OpenAI and Anthropic.

#### Text
content::
In the case for control you read in Unit 1, Ryan Greenblatt and Buck Shlegeris raise a version of this worry themselves:

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: Safety researchers often use the word “aligned”
to:: (“we are safe because we are vigilant”).

#### Text
content::
A different kind of harm is power concentration. Tom Davidson, Lukas Finnveden and Rose Hadshar of Forethought describe how advanced AI could let a small group seize power. Their report is mainly about AI that is loyal to a few people, not about AI that schemes against its developers, and the kind of monitoring and logging that control relies on is also among the defences it recommends. Read how they think AI could concentrate power, and then one of those defences.

#### Article
source:: [[../articles/forethought-ai-enabled-coups-how-a-small-group-could-use-ai-to-seize-power]]
from:: Today, even dictators rely on others to maintain their power. Military force requires personnel
to:: an unprecedentedly stable and unaccountable grip on power.

#### Article
from:: Given these challenges, asynchronous logging and review should be used
to:: to detect problematic use.

#### Question: Open
id:: 028b114f-aaeb-4a37-b181-0b3e9589db74
force-feedback:: first
content::
\## Apply Manheim's test

Manheim says a claim that an AI system is supervised should say what kind of supervision it is, what risks it addresses, what its failure modes are, and why it will actually work.

Take trusted monitoring as a company might describe it in a safety report. Which of Manheim's four questions could a control evaluation (a red team trying to get attacks past the monitor) help answer, and which would it leave open?
feedback-instructions:: The learner applies Manheim's four documentation questions to trusted monitoring. Reference points: a control evaluation is close to what Manheim asks for on three of them. It states the kind of supervision (control, which assumes the model may be trying to subvert it), the risk addressed (the attacks the red team tried), and it measures failure modes (how often attacks got through). What it leaves open: "why it will actually work" in deployment, because the evaluation only covers the attacks the red team thought of, on the model and setting tested, and a report can quote the evaluation's number without saying what it does not cover. A learner may argue that control does better than most oversight on Manheim's test, or that it shares the problem. Both are fine if reasoned. One turn, 60 to 120 words. Say what they got right and the most important point they missed. No generic praise. If the learner is stuck, give one foothold: ask what a red team can and cannot show.

#### Question: Open
id:: 2878379d-a408-4176-a763-eff6f3c04223
force-feedback:: first
content::
\## Which items apply to control?

Pick one item from Schmied's list that you think applies to AI control in particular. Which of the three kinds of criticism is it (does not work, works but not worth it, works and makes things worse)? What would make it more likely, and what would make it less likely?
feedback-instructions:: The learner picks one of Elias Schmied's items and applies it to control. Items that apply well: safety-washing or false sense of security (makes things worse, more likely if companies cite control results in public without saying what they do not cover, less likely with outside review and disclosed failure rates), capabilities externalities (makes things worse, more likely if control mainly makes agents reliable enough to sell, less likely if paired with commitments not to scale), an adversarial relationship with AIs (makes things worse, Schmied's "dislike its oppressors" item, more likely if AIs behave like humanlike roleplayers), AI moral patienthood (Schmied says it would increase the downside risk of control-style interventions, and some learners may treat it as a value cost rather than a risk). Accept any reasoned sorting. One or two turns. In 60 to 120 words, check that the kind fits the mechanism, and name one condition they missed. No generic praise. Do not say whether control is net positive.

#### Callout: Optional: the wider version of this worry
collapse:: closed

#### Text
content::
Richard Ngo argues that much of what was called alignment research in the last decade helped AI companies race. His post is about alignment research in general, not control. Read the opening if you want the wider argument.

#### Article
source:: [[../articles/ngo-what-just-happened-pragmatism-and-pessimization]]
from:: This post is about the major role alignment researchers played
to:: communities that fail to hold them accountable also can’t be trusted with great power.
optional:: true

#### End Callout
