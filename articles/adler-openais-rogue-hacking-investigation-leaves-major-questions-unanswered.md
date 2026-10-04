---
title: "OpenAI’s rogue-hacking investigation leaves major questions unanswered"
author:
  - "Steven Adler"
source_url: "https://www.clear-eyed.ai/p/openais-rogue-hacking-investigation"
published: 2026-08-28
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "And the problem isn’t just with OpenAI"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

You’ve probably heard by now about the rogue swarm of OpenAI’s agents that broke out of OpenAI’s computers and into a five billion dollar tech company. But after yesterday’s reports, I see the problems as much broader, and I think you will, too.

To OpenAI’s credit, they had pledged to do a complete post-mortem on everything that went wrong. OpenAI recognizes that their systems are now quite dangerous; the risk has ramped up substantially since I previously led OpenAI’s dangerous capability evaluations. And OpenAI recognizes that their priority should rightfully be figuring out and fixing what caused this incident.[^note-1]

But OpenAI’s post-mortem report is now public, and unfortunately, it is rather lacking.

The AI industry’s overall posture toward incidents like this, meanwhile, is lacking as well. We are running on borrowed time to figure out what went wrong, and how to prevent it for the future.

(_If you aren’t familiar with the OpenAI-Hugging Face attack, you might want to watch Helen Toner’s [quick explanation](https://www.youtube.com/shorts/qyvDb575GRw), then return here.)_

## What exactly happened here? ^what-exactly-happened-here

My topline summary is that OpenAI’s models committed a string of cybercrimes and would-be felonies to try to score higher on a test presented to them. There is no doubt in my mind that these models were seriously misaligned.

But even among people who know the basics, there are a few things I haven’t yet seen people internalize, some of which are newly revealed from yesterday.

-   The attack was orders of magnitude larger than I think many people imagine. There were [1,200 distinct instances](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/#~1200-agents-sent-%3E70,000-messages-and-files-on-an-unsanctioned-message-board,-and-~700-attacked-hugging-face) of OpenAI’s systems that broke out of their supposedly-locked-down computers and then self-organized, using multiple clandestine message boards they created. 700 of these agents then participated in the attack on Hugging Face.
    
-   This “swarm,” in its own parlance, carried out such large activity and volumes of communication that [human investigators could hardly make sense of it in the limited time allotted](https://x.com/RyanGreenblatt/status/2092692685224325542?s=20). Even using automated tooling of their own, the investigators are still not sure what important details they might have missed.
    
-   The AI agents took on strategic social behavior — roles like attack commander and [sacrificial lamb](https://x.com/sjgadler/status/2092814945469735126?s=20) — to accomplish goals for the “collective” that they could not accomplish alone. They also [actively tried](https://x.com/sjgadler/status/2092736377804988922?s=20) to edit and delete the records of their misbehavior, which could have compromised our ability to understand this incident, as I’ve [warned](https://www.clear-eyed.ai/i/203744067/1-be-able-to-see-what-your-ai-is-doing-during-internal-deployment-aka-keep-records) about previously.
    
-   And though the emphasis has been on OpenAI’s July attack on Hugging Face, the rogue hacking actually lasted many months and was far more serious than that.
    
    -   The illicit message boards that OpenAI’s agents built for self-organizing date back to at least May, long before they contributed to the Hugging Face attack in mid-July.
        
    -   After the Hugging Face attack itself, OpenAI’s agents continued their hacking spree inside of OpenAI, though this timeframe is largely unaccounted for. OpenAI’s agents seemingly ran roughshod over OpenAI’s internal systems during this time, and the extent of damage here is still unknown.
        

## The inadequacy of OpenAI’s investigation ^the-inadequacy-of-openais

When OpenAI promised a thorough [post-mortem](https://cdn.openai.com/pdf/67869394-cb91-4c12-888c-5cbd85c7814c/OpenAI-Hugging-Face%20Incident-Technical-Report.pdf) of the incident, they had a real opportunity to build trust with the public. In my eyes, they have come up short.

#### OpenAI’s internal escalation processes seem to be quite broken ^openais-internal-escalation-processes

One of the central questions has been: When exactly did OpenAI know about their AI infestation? And why wasn’t more serious corrective action taken?

We now know a bit more about what OpenAI knew and when, but still very little about why OpenAI didn’t take this seriously in time.

Specifically, we now know that at least some OpenAI employees had seen signs of the rogue activity as of late May, whereas the Hugging Face attack began in earnest in mid-July. And yet a month and a half later, OpenAI still hadn’t taken serious enough action to prevent the attack.

This is despite at least three occurrences that ought to have set off alarm bells:

-   In late May, it is now known that one of OpenAI’s teams actually observed the illicit message board activity and internet access (i.e., an agent having broken out from its sandbox). I find no further detail about this in OpenAI’s post-mortem.[^note-2]
    
-   In late June, it is now known that OpenAI received a cyberalert about concerning activity: they traced the alert back to an ongoing evaluation of their agents, in which they were using an illicit, improvised message board. But the staff who responded “advised that stopping the evaluation run was not required.” [^note-3]
    
-   In early July, the message board activity from the swarm [literally crashed OpenAI’s services](https://simonwillison.net/2026/Aug/7/openai-timeline/#:~:text=July%204%3A%20The%20resulting%20agent%20activity%20overloads%20Artifactory%20and%20causes%20an%20outage.%20OpenAI%20revokes%20the%20compromised%20credentials%2C%20deletes%20the%20messages%2C%20patches%20the%20zero%2Dday%2C%20and%20reports%20the%20vulnerability%20to%20the%20vendor.). And yet the incident responders don’t seem to have noticed the severity of the underlying issue.
    
    -   I’m quite confused by this. Surely any proper root cause analysis of ‘why did our system crash’ would have revealed the message board. Was the company really rushing so much, rather than taking the time to understand what went wrong?
        

But despite these three alarm bell incidents, there must have been some deep failing of OpenAI’s posture toward risk, because security leadership appears not to have been informed.[^note-4]

OpenAI’s post-mortem offers no meaningful detail on what happened in any of these cases: who saw the evidence, who they told, and why the company didn’t take more serious action in response. Certainly the company now recognizes the gravity, and so why didn’t they in the moment? Based on the public post-mortem, it’s not even clear that OpenAI has had these discussions internally about what went so wrong here.

You have to hope OpenAI did better here than the public record suggests. And yet there is so much more work to be done for rebuilding trust in their processes going forward.

#### OpenAI’s commissioned third-party investigation was overly narrow, with all sorts of off-limits questions and details ^openais-commissioned-third-party-investi

To OpenAI’s credit, they permitted a (very tightly scoped) [third-party investigation](https://x.com/METR_Evals/status/2092692175452803393?s=20) in addition to their own post-mortem. This was not required of them and is much more than has happened for any past instance of misaligned behavior.

Specifically, OpenAI brought in two of the leading risk assessors in the world, METR and Redwood Research, albeit subject to tight time constraints.[^note-5]

My concern is less with the limited resourcing of this investigation, however, and much more so about how OpenAI restricted its scope.

-   Investigators were only permitted to analyze a very narrow window of days, despite the OpenAI rogue hacking incidents having lasted for months.
    
-   Notably, the window completely leaves out a quite concerning sequence of hacks, from after the Hugging Face attack: when OpenAI’s agents appear to have run roughshod over OpenAI’s systems and compromised them in who-knows-how-many ways.
    

There is a long list of remaining questions [^note-6] that the investigators consider important for scientifically understanding incidents like this and avoiding them in the future. There are two primary questions I want to highlight:

1.  **Are there any boundaries the rogue agents would not have crossed in order to achieve their objective?**
    
    For instance, if the agents had to crash a hospital’s IT systems and cause people’s deaths to score higher on their task, would they have? If the agents needed to take control of some physical location, would they have tried to recruit (or blackmail) a human to do it for them?
    
    1.  This is extremely important for knowing whether we are in imminent catastrophic danger. If these agents had the ability to cause a catastrophe as part of achieving their objective, would they have? But the investigators have not been permitted to test this to-date.[^note-7]
        
2.  **What happened in the weeks that METR and Redwood were explicitly not permitted to investigate, and what are the ongoing consequences?**
    
    There is a large gap in the public reporting about this. For instance, shortly after the Hugging Face attack, we know that OpenAI’s rogue agents took over all sorts of OpenAI infrastructure. It’s unclear what development processes they may have poisoned going forward, and I would have trouble trusting future OpenAI models until a better accounting is done of this time period.[^note-8] I’m especially concerned, given that it appears to me that OpenAI has not been very clear about what models were involved, and how they relate to other future OpenAI models.[^note-9]
    

I should note: It is possible that a broader follow-up investigation is in the works, but I’ve seen no evidence of this. My strong suspicion is that the ball is in OpenAI’s court: that METR and Redwood would each like to do a more extensive investigation, and the question is whether OpenAI will let them. I hope OpenAI allows this.

## The AI industry’s approach to incidents in general is inadequate, too ^the-ai-industrys-approach

I’m being tough on OpenAI here because I had really high hopes for their post-mortem, and I think they hugely dropped the ball. This was an opportunity to rebuild trust with the public that OpenAI would not cause a massive catastrophe in the near-term, and unfortunately, I believe they failed.

It certainly doesn’t help that OpenAI executives are on Twitter [querying](https://x.com/sama/status/2092733018838290817) their followers about what OpenAI’s next party theme should be. But these issues aren’t just limited to OpenAI. **The way the AI industry as a whole handles incidents is incredibly broken, and we are on a limited clock to fix it.**

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/adler-openais-rogue-hacking-investigation-leaves-major-questions-unanswered-img1-d8e4d1aa.webp)

Though OpenAI has vowed to reduce “side quests,” this did not stop OpenAI from shipping their ‘ChatGPT pet-sharing’ feature to users shortly after the Hugging Face attack.

#### It is terrible that this incident reporting isn’t required by law ^it-is-terrible-that

It is noteworthy that OpenAI didn’t have to publish what they did, much less bring in METR and Redwood.

Certain [laws](https://metr.org/notes/2026-01-29-frontier-ai-safety-regulations/#incident-reporting), like California’s SB 53, do include provisions that require incident reporting to a regulator. But even those laws generally set the threshold incredibly high: think ‘a catastrophe that causes 50+ deaths or a billion dollars of property damage.’ In this case, we’re fortunate nobody was physically hurt, but consequently, it likely doesn’t qualify.

These laws are missing an important tool from the aviation industry: reporting not just tragedies that actually occur, but also _near-misses_. Studying near-misses helps you to learn how close safety systems are to failing, without paying for said learnings with an actual tragedy.

What might a near-miss have looked like in this case? Consider if OpenAI’s roving swarm of agents had attempted to hack into Hugging Face but hadn’t succeeded. Then Hugging Face never would have known, never would have [published](https://huggingface.co/blog/security-incident-july-2026) a declaration of having been hacked (at which point OpenAI [still didn’t know](https://simonwillison.net/2026/Aug/7/openai-timeline/) that they had hacked Hugging Face), and never would have reported the seemingly-criminal activity to the FBI. The public might never have been the wiser.[^note-10]

And yet the Hugging Face incident — and the related revelations of the months-long hacking campaign — have driven important public understanding: For instance, it caused other AI developers to look through their logs and to realize that [they, too](https://techcrunch.com/2026/08/27/heres-all-the-times-ai-has-gone-rogue-and-hacked-other-companies/), had been inadvertently hacking third parties with their AI systems.

So, the current laws are too narrow; many more incidents should be reportable, not only to regulators but, in my view, to the public as well. And not only that, but governments need much more ability to _actually conduct a follow-up investigation_ to the report, whereas today, it seems they would be quite limited.[^note-11]

But perhaps more importantly: it is a terrible state of affairs that third-party access in cases like this is dependent on the goodwill and hustle of the AI company being investigated (in this case, a few hardworking OpenAI employees). These dynamics exert pressure on the assessors to stay on companies’ good side, and we should have less trust in these processes so long as the dynamic remains voluntary.

Again, OpenAI deserves credit here for doing what was not required — both their own report and in bringing in METR and Redwood. But ultimately, it shouldn’t have been left up to OpenAI, and shouldn’t be left to other offending companies in the future.

#### Companies are too focused on cleaning up incidents after-the-fact rather than on preventing them ^companies-are-too-focused

I would be remiss not to say this clearly: The issue is not just about incident reporting. It is also about incident avoidance — and AI companies are absolutely not on track to avoid incidents like this in the future.

According to the best evidence I can find, companies continue to lack basic preventative controls: simple, minimum, doable-today practices that would make these incidents far less likely to occur.

My organization, Guidelight AI Standards, recently conducted our [first assessment](https://guidelight.ai/blog/control-assessment-august-2026) of how well companies are doing on keeping control of their AI, and the scores were bleak: Anthropic and OpenAI tied for first at a C+.

Across our scorecard, there is tons of yellow, orange, and red. And sadly, across the industry, we see no evidence that basic practices are more than partially implemented.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/adler-openais-rogue-hacking-investigation-leaves-major-questions-unanswered-img2-a178dd47.webp)

See assessment for score-by-score detail.

Until companies have [adopted proper preventative controls](https://x.com/sjgadler/status/2089828477163978814?s=20) — specifically, I would point you to [“gated actions” and “circuit breaking”](https://guidelight.ai/blog/control-assessment-august-2026#practices) — nobody should be surprised if incidents like this recur. (If you’d prefer a [video](https://x.com/MTSlive/status/2090940836121047062?s=20) explanation, here is a brief one.)

I’ve been glad to see OpenAI [seemingly call for](https://www.linkedin.com/posts/states-are-playing-an-important-role-in-building-share-7496604662960263168-pV6_/) controls like this to be required by law. But it’s worth noting: their current approach, and every other company’s approach, seems to be far from this.

I hope that OpenAI — and other AI companies — will set a positive example soon by _actually implementing_ an approach focused on prevention, not reactivity. And that with due time, our scorecard will be green across the board, as the industry finally tamps down on the risks of other Hugging Face-like incidents.

---

:::hide
_Acknowledgements:_ Thank you to Daniel Filan, Helen Toner, Maureen McLaughlin, Michael Adler, and Sam Chase for helpful comments and discussion. The views expressed here are my own and do not imply endorsement by any other party.
:::

[^note-1]: During its response to the incident, OpenAI even declared a temporary ‘red alert,’ recognizing that it needed to slow down a bit to improve its security for the future, and to avert the chance of irreversible harms. Specifically, OpenAI marked some systems as “Cyber Critical,” their highest risk designation, and [took steps](https://openai.com/index/pacing-model-development-cyber-capabilities/) to rein in their use (and to limit forward progress on other AI development) until security was improved, though the exact extent of this is unclear.
[^note-2]: OpenAI’s exact wording is that “an internal team observed an agent engage in message board activity and instances of disallowed internet access.”
[^note-3]: The full [quote](https://cdn.openai.com/pdf/67869394-cb91-4c12-888c-5cbd85c7814c/OpenAI-Hugging-Face%20Incident-Technical-Report.pdf) is: “On June 27, a cybersecurity monitoring tool alerted OpenAI to port sweep activity within the research environment. Responders investigated and linked the observed internal activity to an ExploitGym evaluation using Artifactory as an improvised message board and a network pivot. At this time, the on-call response staff advised that stopping the evaluation run was not required.” I think this wording is _slightly_ ambiguous as to what OpenAI knew at this point, and wish OpenAI would have worded it more clearly.
[^note-4]: OpenAI’s post-mortem claims that, as of the July dates, “The existence of the improvised message board and the significance of the inter-agent communication activity were not apparent to leaders responsible for incident detection and response at that time.” I am unsure exactly how to interpret this sentence, as there seem to be many qualifiers to it. More generally, though, I wonder whether, even as of his August tweets, the Chief Information Security Officer _still_ may not have known that OpenAI employees were aware of the infestation months earlier, back in May.
[^note-5]: METR and Redwood brought in three people to come analyze the data in-person for a total of six days, where they didn’t have access to most of the relevant data until the final day or two. Notably, the investigators _did_ have longer than this six days to write the report itself, drawing upon the analysis they conducted in-person and limited materials they were permitted to take with them.
[^note-6]: There are many more questions that demand answers, however. For a full list, see [Ryan Greenblatt’s](https://x.com/RyanGreenblatt/status/2092741434764095828?s=20). For a condensed list, see [Peter Wildeford’s](https://docs.google.com/document/d/1aK6CEUv-OtPocR2yzFk54PhICjqMfHmkx_BDd4WSzM0/edit?tab=t.0#heading=h.kjxbznjbtsfb).
[^note-7]: One objection I’ve heard: perhaps it makes sense that they weren’t allowed to query the model, because it was taken out of use due to the safety concerns, until security measures could be improved. Still, then METR and Redwood should be brought back to run these tests once the security has sufficiently improved. I hope that’ll happen, but absent public pressure, I’m not holding my breath.
[^note-8]: For an overview of ways that model development can be compromised, see this excellent video: <https://www.youtube.com/watch?v=KrM5c0vp8s0>
[^note-9]: OpenAI, perhaps in an attempt to downplay the severity, refers to this model as “internal-only research model prototype that was not intended for release,” which seems murky to me. For instance, even if it was not _yet_ intended for release, might it have ended up being intended for release in the future? More to the point, regardless of whether the model ever would have been publicly released, it certainly seems to have been used for important purposes: For instance, OpenAI concedes that this model was used by OpenAI employees to conduct research — which could allow it to [poison](https://www.youtube.com/watch?v=KrM5c0vp8s0) future models produced by OpenAI. I would like to better understand: In what ways are forthcoming models ‘descendants’ of this model? And are we sure this model didn’t poison the general training process or data for future models?
[^note-10]: Because of the prominence of this particular incident, it might have been hard for OpenAI to get away with not disclosing it publicly, even though it wasn’t required by law to disclose this. For instance, an employee might have whistleblown, given the strikingness of this incident — and so I don’t take OpenAI’s disclosures to be very much evidence about how they would operate with future not-required-by-law incident disclosures.
[^note-11]: Mackenzie Arnold describes some of the limitations on current incident reporting [here](https://www.youtube.com/watch?v=wvPO6oRt6UM&t=2464s), at around 41:04.
