---
title: "Common Ground between AI 2027 & AI as Normal Technology"
author:
  - "Sayash Kapoor"
source_url: "https://asteriskmag.substack.com/p/common-ground-between-ai-2027-and"
published: 2025-11-12
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "AI 2027 and AI as Normal Technology were both published in April of this year."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_[AI 2027](https://ai-2027.com/)_ and _[AI as Normal Technology](https://knightcolumbia.org/content/ai-as-normal-technology)_ were both published in April of this year. Both were read much more widely than we, their authors, expected.

Some of us (Eli, Thomas, Daniel, the authors of AI 2027) expect AI to radically transform the world within the next decade, up to and including such sci-fi-sounding possibilities as superintelligence, nanofactories, and Dyson swarms. Progress will be continuous, but it will accelerate rapidly around the time that AIs automate AI research.

Others (Sayash and Arvind, the authors of AI as Normal Technology) think that the effects of AI will be much more, well, normal. Yes, we can expect economic growth, but it will be the gradual, year-on-year improvement that accompanied technological innovations like electricity or the internet, not a radical break in the arc of human history.

These are substantial disagreements, which have been partially hashed out [here](https://blog.ai-futures.org/p/ai-as-profoundly-abnormal-technology) and [here](https://www.normaltech.ai/p/a-guide-to-understanding-ai-as-normal).

Nevertheless, we’ve found that all of us have more in common than you might expect.

In this essay, we’ve come together to discuss the ways in which we agree with each other on how AI progress is likely to proceed (or fail to proceed) over the next few years.[^note-1]

## 1\. Before strong AGI, AI will be a normal technology. ^1-before-strong-agi

Broadly speaking, even the authors of _AI 2027_ agree that AI is a normal technology prior to strong AGI.

(Different people mean different things by “strong AGI,” which has caused substantial confusion. For purposes of this post, we mean something like “humans in the cloud” — that is, AI systems which can learn, adapt, generalize to new situations, operate autonomously, and coordinate with each other at least as well as top humans. In general, they can do virtually everything humans can do just as well but faster and cheaper.) [^note-2]

Before we have strong AGI, when AI systems become good enough to automate any given task, the humans who performed that task will probably be able to switch to another. For example, when some part of the AI research process is automated, the overall process will be bottlenecked by something else. As a result, total research progress will accelerate, but not dramatically so. AI will mostly function as a tool; it won’t be capable of operating autonomously for long periods. The diffusion of AI throughout the economy will continue to be fairly gradual, with industries slowly handing over tasks to AIs as they become convinced that the AIs are reliable enough and as they build the necessary infrastructure, interfaces, and new workflows.

## 2\. Strong AGI developed and deployed in the near future would not be a normal technology. ^2-strong-agi-developed

Even the _AI as Normal Technology_ authors agree that if strong AGI is developed and deployed in the next decade, things would not be normal at all. Since strong AGI will by definition match or exceed top humans at reliability, learning, adapting, and generalizing, it would necessarily be better than humans at shifting to new tasks as old ones are automated.

In Arvind and Sayash’s view, the notion of “Strong AGI”, or [any other notion of AGI](https://www.normaltech.ai/p/agi-is-not-a-milestone), is a joint property of the system and its environment. They think strong AGI won’t be developed in the lab (say, by scaling LLMs). Rather, building strong AGI will require a feedback loop with the real world that would set limits to the pace of progress. Thus, if strong AGI is developed and deployed in the next decade, it is a world in which the normal technology view has failed and/or is no longer useful. On the other hand, a more gradual route to “strong AGI” could be one in which the framework remains helpful, though the endpoint of this route is something they consider outside the horizon that can be reasonably foreseen and planned for.  
  
By contrast, AI 2027 authors see current developments as harbingers of strong AGI. They expect progress to be continuous, but rapid, and to accelerate dramatically when AIs fully automate AI research. Major AI companies claim that they will automate AI research and achieve superintelligence by 2027 or 2028. The AI 2027 authors are uncertain but think that more likely than not, it’ll happen within the next decade.

## 3\. Most existing benchmarks will likely saturate soon. ^3-most-existing-benchmarks

Progress in AI is frequently measured by evaluating their ability to solve problems from various “benchmarks”.[^note-3]

We all believe that, in the next few years, most of the existing benchmarks, and standard extensions of them, will “saturate” — that is, AI systems will match or exceed performance of expert humans across all of the tasks they evaluate.

To make this concrete, we believe it is possible that by 2027 or 2028, AI systems will saturate all capability benchmarks referenced in the GPT-5, Claude 4, or Gemini 2.5 technical reports. This includes question-answering benchmarks like MMLU or Humanity’s Last Exam and agentic benchmarks like SWE-Bench, RE-Bench, MLE-Bench, or Terminal Bench. If we gave an expert human in the relevant problem domain any specific question from one of these benchmarks, and graded them according to the benchmark rules, we believe it’s possible that AI systems will out-score the best humans. We believe this could be true even for “AGI”-branded benchmarks, like ARC-AGI (v1, v2, or even v3). Furthermore, we believe this could be true for a single AI system and that it will not be the case that individual models will need to be tuned on a task-by-task basis.

Arvind and Sayash believe that these benchmarks have poor construct validity, and as a result, that saturation does not mean that the underlying task will be easy to automate. Just because an AI system can resolve SWE-Bench issues with super-human performance, this does not imply that it will be able to start replacing humans at the job of software engineering. At least for the next 50 years, they expect that there will be many jobs where humans out-perform the best AIs.

Thomas, Eli, and Daniel agree that there is an important gap between benchmark scores and real-world utility; their disagreement centers on the magnitude of this gap. They feel that some of these benchmarks (for example, RE-Bench and HCAST) are an important source of evidence for how close we are to the automation of AI R&D.

## 4\. AIs may still regularly fail at mundane human tasks; Strong AGI may not arrive this decade. ^4-ais-may-still

On the other extreme, we also all believe that it will probably still be the case that AI systems regularly fail at automating tasks humans find relatively simple. For example, by the end of 2029, none of us would be _that_ surprised if AI systems couldn’t reliably handle simple tasks like “book me a flight to Paris” using a standard human website.[^note-4]

We think this about most tasks that people regularly tackle throughout their lives: purchasing products online, filing their taxes, scheduling meetings, etc. We expect that an AI system will be able to achieve high scores on benchmark versions of these tasks, but when placed in the real world, we do not strongly predict that they will consistently surpass human performance.

We believe this is true for several reasons, but mainly because robustly handling the long tail of errors is challenging. It is simultaneously possible that AI systems can solve tasks well _on average_, and yet behave far worse than any human would in the worst case scenario. We think that in domains where a human can reasonably verify the work, AI systems will be reliable enough to be useful in practice. But we all agree that it is possible that even by 2029 AI systems will not be able to be used in high-assurance settings.[^note-5] While “reasoning” models are able to help mitigate these types of simple confusions, we do not expect them to completely resolve this problem.

We all expect that strong AGI will _probably_ not arrive before 2029, and in early 2029 the world will _probably_ still look basically like it does today. There will be AI systems that succeed at increasingly many tasks, but humans are still basically employed to do most things, and AIs will not be able to independently discover new science.

Arvind and Sayash agree with this because they do not expect “strong AGI” to arrive anytime soon.

But the authors of AI 2027 also agree, though only barely; they think that their “strong AGI in 2027” scenario is plausible, but faster than their median expectations. The median timelines of Daniel, Eli, and Thomas for when we will develop strong AGI are 2030, 2035, and 2033, respectively.[^note-6]

## 5\. AI will be (at least) as big a deal as the internet. ^5-ai-will-be

While we disagree on the upper bound of capabilities, we all agree that AI will be a “big deal”. (Formalizing this is somewhat challenging, but we will try now.) The world will change as a result of this technology, and things that seemed like science fiction will soon be possible — just like the world of today is different to the world thirty years ago. Indeed, in many ways, the technology we have today exceeds the capabilities of the science fiction of the time.

The internet fundamentally altered the way the world works. Want to book a flight? You don’t call a travel agent, you go to the airline’s website. Want to access your bank? Go to the bank’s website. Video calls to someone halfway around the world? Stream your favorite TV show on demand? Social media? Newspapers? Encyclopedias? Shopping? All built on the internet. We all believe that AI could be at least as transformative. Saying more than this is as hard as asking someone in 1990 to predict how the Internet will transform society. We would be right on some counts, very wrong on others, and miss entire categories of change.

Arvind and Sayash agree that AI is a general-purpose technology that will have similarly transformative effects. In the long run, they expect AI could automate most cognitive tasks, just as the industrial revolution led to the automation of most physical tasks, in the sense that machines are now responsible for vastly more physical work than the human population. That said, they expect AI impacts to largely follow the path of previous general-purpose technologies, which are bottlenecked by barriers to diffusion and adoption rather than capabilities. And they expect that there would still be a lot left for humans to do — like controlling AI systems, and deciding how they should be used.

The authors of _AI 2027_ clearly believe that AI will be at least as big of a deal as the internet. But they believe this will very rapidly be followed by AI that is more important than any other technology ever developed (in this article, referred to loosely as Strong AGI. Elsewhere it is sometimes called ASI or Superintelligence, or just AGI).

---

The above agreements are focused primarily around specific predictions about events that we expect will (or will not) occur in this decade. But we also have many agreements about actionable policy proposals. Despite our differing world views, we see many actions as sensible in any possible future world, and encourage more research on ways to mitigate potential harms from advanced AI.

We hope to be able to encourage policy makers to enact sensible legislation that can be broadly agreed upon regardless of the particular AI timeline that we may be in.

## 6\. AI alignment is unsolved. ^6-ai-alignment-is

We all agree that “AI Alignment”— that is, the problem of training AIs to behave in a way that aligns with our values and expectations — has not been solved when it comes to current AI systems.

We all agree that it is important to invest in research aimed at aligning current and future AI systems — for example, chain of thought monitorability, mechanistic interpretability, scalable oversight, and the science of generalization.

We all agree that on the current trajectory, AIs will continue to be misaligned, often in ways that aren’t detected by evaluations. Therefore, we all agree that we should not rely on AI alignment as our last (or only) line of defense against misaligned advanced AI. We should develop mechanisms for controlling AI systems that will work even without solving the alignment problem. People should treat every AI system as possibly misaligned, and act accordingly — in particular, we should be cautious about how much trust is placed in AI systems, and not give them enough _power_ to pose a catastrophic risk if misaligned.

Sayash and Arvind think that while alignment is [helpful](https://www.normaltech.ai/p/model-alignment-protects-against), other mechanisms for controlling AI systems will help manage the impacts of AI deployment. Daniel, Eli, and Thomas agree that this is true for weaker AI systems but think that solving alignment is extremely important for strong AGI, because they expect other control mechanisms to fail as AIs become increasingly superhuman.

## 7\. AIs must not make important decisions or control critical systems. ^7-ais-must-not

We all believe that current AIs should not be allowed to have autonomous control over critical systems.[^note-7] This includes extreme cases like giving AIs control over data centers, nuclear weapons, tech companies, or government decision making processes.

## 8\. Transparency, auditing, and reporting are beneficial. ^8-transparency-auditing-and

We all believe that improving transparency, auditing, and reporting are important to ensure the safe development of AI. Developers of frontier AIs should be required to be transparent about the safety measures put in place. Independent auditors should regularly evaluate the safety of the AI systems as they are trained and at the end of training. Whistleblower protections should be strengthened. Safe harbors for independent researchers should be established to encourage safety research. AI developers should release detailed reports about how and why they believe their systems are safe for use.

## 9\. Governments must build capacity to track and understand developments in the AI industry. ^9-governments-must-build

We all agree that building technical expertise within the government to track the progress and diffusion of AI capabilities is helpful for understanding the technology and figuring out its potential societal implications. Governments can play a role in evaluating AI models (especially for domains that have national security implications), solving coordination problems, such as when the defenses need to be implemented by actors other than AI companies, and understanding and reacting appropriately to new developments.

## 10\. Diffusion of AI into the economy is generally good. ^10-diffusion-of-ai

The productive impacts of AI will be realized as it diffuses across society. Governments and other actors can play many roles in enabling diffusion. Deploying AI may also help build resilience, as defenders can figure out how to use these systems to enable better responses to risks like cyber-attacks and other AI-enabled threats.

To be clear, we aren’t recommending ramming AI into everything as fast as possible. We simply mean that it’s generally good for AI products and services to diffuse through the economy; they will have many immediate benefits and also help us learn more about AI, its strengths and weaknesses, its opportunities and risks.

## 11\. A secret intelligence explosion — or anything remotely similar — would be bad, and governments should be on the lookout for it. ^11-a-secret-intelligence

Tech companies like OpenAI and Anthropic are explicitly planning to automate their own jobs as fast as possible; that is, they are aiming to train AIs that can fully automate the AI R&D process itself. The resulting “recursive self-improvement” could result in an “intelligence explosion” of rapid capability gains (at least, that’s what the authors of AI 2027 expect) or it could be bottlenecked by other factors such as the lack of real-world data (at least, that’s what the authors of AI as Normal Technology expect).[^note-8]

We all agree, though, that if rapid AI capability improvements were to occur in secret, this would be dangerous — and potentially catastrophic. Secrecy would stand in the way of the oversight, and coordination that may be necessary regardless of how transformative the technology becomes. Instead, information about the latest AI capability trends, the guidelines and constraints that AI companies attempt to instill in their models, the alignment and control techniques they use, and safety incidents and evaluation results relevant to the above needs to flow quickly out of the companies and to the public. Transparency about AI development is broadly beneficial in a variety of worldviews, even if there is no RSI or strong AGI.

## Conclusion ^conclusion

The future remains uncertain. But, at least in the next few years, we all agree more than we disagree on how progress in AI is likely to proceed. We hope that by being explicit about our agreements here it will help others better understand our differing positions, and the confidence with which we hold them.

Distinguishing between these two possible futures (futures similar to _AI 2027_ vs. futures described in _AI as Normal Technology_) is important, and the sooner we can construct methods that would help us predict what future we’re headed towards the better. An important research contribution could therefore be to develop metrics that would help distinguish between these two possible futures _before we get there_. We are, in fact, continuing to collaborate on the creation of such metrics. Stay tuned.

_Attribution: Nicholas Carlini brought the group together and wrote the first draft, on the basis of conversations he had with the others at the Curve, CSET, and elsewhere. The other authors then worked through it a few times, rewriting and editing it until they were satisfied it represented their views. Thanks also to Clara Collier for edits and publishing it on this blog._

[^note-1]: This discussion originates from a workshop hosted by CSET in July of 2025, which Thomas, Sayash, and Nicholas attended. Over the course of two days, we tried to find near-term strongly-held points of disagreement. We were all quite surprised when the effort failed. While we all (wildly!) disagree about what the long-term future will look like, our predictions for the next few years overlap quite substantially.
[^note-2]: For the purposes of this agreement in particular the _AI 2027_ authors’ more nuanced view is that AI will transition to not being a normal technology as it gets closer to strong AGI. Especially in a world with longer transitions from top-human-level at many/most jobs to top-human-level at ~all jobs, they expect that AI might cease being a normal technology in the relevant sense somewhat before the first strong AGI.
[^note-3]: Think exams, but for AI systems instead of students.
[^note-4]: More specifically, we mean this when comparing the LLM to, e.g., a travel agent. Today, if we ask a travel agent to get us to Paris, they’ll get us to Paris. Maybe it won’t be exactly to our liking (we prefer flights that leave later in the day—but they couldn’t know that). But they won’t, e.g., book us to London by accident. Our belief is that even in 2029 AIs may still not be reliable in this way, and if you ask one to do something simple like this, it will sometimes fail spectacularly, e.g., by getting distracted while trying to navigate the UI for some unknown and seemingly arbitrary reason, failing to book the flight, and then lying that it had completed the task.
[^note-5]: The AI 2027 team believe that at some point these flaws will be fixed —plausibly within five years, probably within 10 years—while Arvind and Sayash believe it will likely take much longer.
[^note-6]: At the time AI 2027 was published, their medians were 2028, 2031, and 2031 respectively. Events since then, and improvements to their timelines model, have shifted their distributions outwards somewhat.
[^note-7]: The AI 2027 authors think that perhaps it’ll make sense to hand off important responsibilities and decisions to AIs in the future, once they have been rigorously shown to be aligned and/or controlled adequately. However we are not close to being able to achieve that level of assurance.
[^note-8]: “In short, we don’t think RSI will lead to superintelligence because the external bottlenecks to building and deploying powerful AI systems cannot be overcome by improving their technical design. That is why we don’t discuss it much. … That said, we acknowledge that our whole thesis might be wrong, and it is more likely that we’re wrong if RSI is achieved.” (From [this post](https://www.normaltech.ai/p/a-guide-to-understanding-ai-as-normal#footnote-anchor-3-173147197).)
