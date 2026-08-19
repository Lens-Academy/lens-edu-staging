---
title: "The Impact of Generative AI on Critical Thinking: Self-Reported Reductions in Cognitive Effort and Confidence Effects From a Survey of Knowledge Workers"
author:
  - "Microsoft"
source_url: "https://www.microsoft.com/en-us/research/wp-content/uploads/2025/01/lee_2025_ai_critical_thinking_survey.pdf"
published: 2025-01-28
created: 2026-08-08
accessed: 2026-08-08
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

The Impact of Generative AI on Critical Thinking: Self-Reported

Reductions in Cognitive Effort and Confidence Effects From a

Survey of Knowledge Workers

Hao-Ping (Hank) Lee
Advait Sarkar
Lev Tankelevitch

Carnegie Mellon University
Microsoft Research
Microsoft Research

Pittsburgh, Pennsylvania, USA
Cambridge, United Kingdom
Cambridge, United Kingdom

haopingl@cs.cmu.edu
advait@microsoft.com
levt@microsoft.com

Ian Drosos
Sean Rintel
Richard Banks

Microsoft Research
Microsoft Research
Microsoft Research Cambridge

Cambridge, United Kingdom
Cambridge, United Kingdom
Cambridge, United Kingdom

t-iandrosos@microsoft.com
serintel@microsoft.com
rbanks@microsoft.com

Nicholas Wilson

Microsoft Research

Cambridge, United Kingdom

niwilson@microsoft.com

Confidence Effects From a Survey of Knowledge Workers. In CHI Conference
## Abstract
on Human Factors in Computing Systems (CHI ’25), April 26–May 01, 2025,
The rise of Generative AI (GenAI) in knowledge workflows raises
Yokohama, Japan. ACM, New York, NY, USA, 23 pages. https://doi.org/10.
questions about its impact on critical thinking skills and practices.
1145/3706598.3713778
We survey 319 knowledge workers to investigate 1) when and
how they perceive the enaction of critical thinking when using
## 1 Introduction
GenAI, and 2) when and why GenAI affects their effort to do so.
Participants shared 936 first-hand examples of using GenAI in work
Generative AI (GenAI) tools, defined as any “end user tool [...] whose
tasks. Quantitatively, when considering both task- and user-specific
technical implementation includes a generative model based on deep
factors, a user’s task-specific self-confidence and confidence in
learning”,1 are the latest in a long line of technologies that raise
GenAI are predictive of whether critical thinking is enacted and
questions about their impact on the quality of human thought, a line
the effort of doing so in GenAI-assisted tasks. Specifically, higher
that includes writing (objected to by Socrates), printing (objected to
confidence in GenAI is associated with less critical thinking, while
by Trithemius), calculators (objected to by teachers of arithmetic),
higher self-confidence is associated with more critical thinking.
and the Internet.
Qualitatively, GenAI shifts the nature of critical thinking toward
Such consternation is not unfounded. Used improperly, technolo-
information verification, response integration, and task stewardship.
gies can and do result in the deterioration of cognitive faculties
Our insights reveal new design challenges and opportunities for
that ought to be preserved. As Bainbridge [7] noted, a key irony
developing GenAI tools for knowledge work.
of automation is that by mechanising routine tasks and leaving
exception-handling to the human user, you deprive the user of the
CCS Concepts
routine opportunities to practice their judgement and strengthen
their cognitive musculature, leaving them atrophied and unpre-
• Human-centered computing → Empirical studies in HCI.
pared when the exceptions do arise.
In response, research has begun looking closely at how different
Keywords
activities are impacted by GenAI and the extent to which cognitive
Critical thinking, Generative AI tools, Knowledge worker, Bloom’s
offloading [8] occurs, and whether this may be an undesirable
taxonomy, Survey
thing. Some work has focused, for instance, on studying the effects
ACM Reference Format:
of GenAI use on memory (e.g., [1, 106]) and on creativity (e.g.,
Hao-Ping (Hank) Lee, Advait Sarkar, Lev Tankelevitch, Ian Drosos, Sean
[28, 100]). Moreover, design research has also been developing
Rintel, Richard Banks, and Nicholas Wilson. 2025. The Impact of Generative
interventions that improve the ability of people to think in certain
AI on Critical Thinking: Self-Reported Reductions in Cognitive Effort and
ways (e.g., [24]). We review these lines of work in Section 2.
In this paper, we focus on a higher-level concept that captures an-
other aspect of thought considered desirable and worthy of preser-
This work is licensed under a Creative Commons Attribution 4.0 International License.
vation: critical thinking (defined in Section 2). The effect of the use
CHI ’25, Yokohama, Japan
© 2025 Copyright held by the owner/author(s).
1While there is no broad consensus on how to define this now-common term, for
ACM ISBN 979-8-4007-1394-1/25/04
https://doi.org/10.1145/3706598.3713778
clarity we adopt this definition, a rationale for which is given in [115].

of GenAI tools on critical thinking, as a direct object of inquiry, has
as setting clear goals, refining prompts, and assessing AI-generated
not yet been explored.
content to meet specific criteria and standards. Their reflective
Moreover, we focus on critical thinking for knowledge work (as
approach involves verifying outputs against external sources and
conceptualised by Drucker [30] and Kidd [67]). Much research on
their own expertise, especially in tasks that require higher accuracy.
the effect of GenAI on thinking skills is focused on educational
The data identify key motivators for critical thinking: the desire
settings, where concern for skill cultivation is most acute (e.g.,
to enhance work quality, avoid negative outcomes, and develop
the effect of GenAI code completion tools on programming and
skills. However, several barriers inhibit this reflective process, in-
computer science education [107]). As previously noted [116, 119],
cluding lack of awareness, limited motivation due to time pressure
critical thinking has been operationalised in detail in certain spe-
or job scope, and difficulty improving AI responses in unfamiliar
cific disciplines, such as academic history, clinical psychology, and
domains. Surprisingly, while AI can improve efficiency, it may also
nursing. But the ostensible shifts in critical thinking behaviours
reduce critical engagement, particularly in routine or lower-stakes
brought about by GenAI extend to a broad set of professions and
tasks in which users simply rely on AI, raising concerns about
knowledge workflows — GenAI tools are now widely used in knowl-
long-term reliance and diminished independent problem-solving.
edge work [13] — and little is known about the critical thinking
Regarding RQ2 (Section 5), GenAI tools appear to reduce the per-
demands of these. We lack broad-based empirical examples of what
ceived effort required for critical thinking tasks among knowledge
kinds of knowledge work activities are considered by professionals
workers, especially when they have higher confidence in AI capa-
to require critical thinking.
bilities. However, workers who are confident in their own skills
Recent work has motivated the need for critical thinking support
tend to perceive greater effort in these tasks, particularly when
in AI-assisted knowledge work [116, 119]. It is motivated primarily
evaluating and applying AI responses.
by the observation of the tendency of AI-assisted knowledge work-
The data shows a shift in cognitive effort as knowledge workers
flows to be subject to “mechanised convergence” [114], i.e., that
increasingly move from task execution to oversight when using
users with access to GenAI tools produce a less diverse set of out-
GenAI. While this shift “from material production to critical in-
comes for the same task, compared to those without. This tendency
tegration” has been observed in prior studies [114], such studies
for convergence reflects a lack of personal, contextualised, critical
are typically controlled studies in narrow domains with small par-
and reflective judgement of AI output and thus can be interpreted
ticipant samples. Our data provides complementary evidence that
as a deterioration of critical thinking.
this also occurs in real-world use of GenAI tools, across a wide
However, we lack direct empirical evidence for an interpretation
variety of tasks and professions. For tasks like knowledge retrieval,
that posits a connection between mechanised convergence and
AI reduces effort by automating information gathering, but work-
critical thinking. Output diversity is a proxy for critical thinking,
ers must now invest more in verifying the accuracy of AI outputs.
and a flawed one. For instance, users who reuse GenAI output with-
Similarly, while AI simplifies content creation, workers still need
out editing it may have nonetheless performed a critical, reflective
to spend time aligning outputs with specific needs and quality
judgement in forming the decision not to edit it. Such reflective
standards.
thinking is invisible to measures that focus only on the ultimate
Our paper makes the following contributions:
artefact produced. Without knowing how knowledge workers enact
critical thinking when using GenAI and the associated challenges,
we risk creating interventions that do not address workers’ real
needs.
In this paper, we aim to address this gap by conducting a survey
of a professionally diverse set of knowledge workers (𝑛 = 319),
We review the literature on interaction design interventions
eliciting detailed real-world examples of tasks (936) for which they
for critical thinking, and studies of the effects of automation
use GenAI, and directly measuring their perceptions of critical
on knowledge workflows (Section 2).
thinking during these tasks: when is critical thinking necessary,
We describe the development and deployment of a survey
how is critical thinking enacted, whether GenAI tools affect the
for gathering empirical evidence for knowledge workers’
effort of critical thinking, and to what extent (Section 3). We focus
experiences and perceptions of the effect of GenAI on crit-
on “enaction” (i.e., actions that are signals or manifestations) of
ical thinking (Section 3). We find that GenAI tools reduce
critical thinking rather than critical thinking per se, because critical
the perceived effort of critical thinking while also encour-
thinking itself as a pure mental phenomenon is difficult for people
aging over-reliance on AI, with confidence in the tool often
to self-observe, reflect on, and report.
diminishing independent problem-solving. As workers shift
from task execution to AI oversight, they trade hands-on
Concretely, we aim to answer two research questions:
engagement for the challenge of verifying and editing AI
RQ1 When and how do knowledge workers perceive the enaction
outputs, revealing both the efficiency gains and the risks of
of critical thinking when using GenAI?
diminished critical reflection (Sections 4 and 5).
RQ2 When and why do knowledge workers perceive increased/decreased
Drawing from our survey insights, we highlight how the
effort for critical thinking due to GenAI?
use of GenAI tools creates new challenges for critical think-
With respect to RQ1 (Section 4), the study reveals that knowledge
ing. We outline implications for designing GenAI to support
workers engage in critical thinking when using GenAI tools primar-
knowledge workers to enhance their awareness, motivation,
ily to ensure the quality of their work. They define critical thinking
and ability to think critically (Section 6).

## 2 Related Work
to which interventions ought to be presented in an agentised or
anthropomimetic manner [99, 131, 141].
2.1 Critical thinking
There are domains and activities, some of which are relevant to
We adopt the definition of critical thinking developed by Bloom et al.
common knowledge workflows, where critical thinking interven-
[12, 54], a hierarchical taxonomy that characterises student learning
tions have been heavily studied. For example, design for critical
objectives into six types: knowledge (recall of ideas), comprehension
thinking can aid in the prevention and verification of misinfor-
(demonstrating understanding of ideas), application (putting ideas
mation, e.g., through structured thinking aids [50, 51], analytical
into practice), analysis (contrasting and relating ideas), synthesis
thinking nudges [143], worksheets and group discussion [136], and
(combining ideas), and evaluation (judging ideas through criteria).
gamification [129]. Or in writing, ideation and argumentation tools,
This definition of critical thinking is not uncontested. There are
such as through visualising argument structure [126, 133], reflect-
multiple alternative frameworks [36–38, 104], and critical thinking
ing on future scenarios [132], ideation and evaluation support [45],
is sometimes also referred to as reflective thinking [26], though
assessing risks in research impact statements [94]. Another com-
not all scholars conflate them. There have been multiple proposals
mon area for reflective thinking interventions is in mental health
for connecting and reconciling this multiplicity of frameworks
and wellbeing, e.g., to support cognitive reappraisal [71], reduce
[32, 74, 96].
compulsive smartphone use [80, 81], improve time management
We adopt the Bloom et al. framework for multiple reasons. First,
[55], create journaling prompts [97], encourage reflection on book
as one of the earliest frameworks, it has strong support in the re-
highlights [61], support prayer [75], coaching for leadership growth
search literature and wide adoption in education systems — its
[4], and reflection on cherished objects [57]. Critical thinking inter-
definition of critical thinking has been widely influential, and has
ventions have also been explored in data analysis [44, 48].
withstood severe criticism and scrutiny [40]. Second, it is relatively
Overreliance, defined as “users accepting incorrect recommen-
simple, having only six core dimensions (as opposed to, for instance,
dations, i.e., making errors of commission” [102], is closely related
the nuanced Paul-Elder framework [104] which consists of eight
to (the lack of) critical thinking. Buçinca et al. [17] found that “cog-
“elements of thought”, ten “intellectual standards”, and eight “intel-
nitive forcing functions” such as requiring the user to wait before
lectual virtues”). The simplicity of the Bloom et al. framework —
receiving AI output, or to make interactive updates to AI output, sig-
its small set of dimensions with clear definitions — renders it more
nificantly reduce overreliance compared to simpler AI explanations.
suitable as the basis of a survey instrument.
Though there is overlap, overreliance is not strictly the same prob-
Critical thinking skills can be developed in sequential stages
lem as (and is perhaps a special case of) a lack of critical thinking.
[70, 98, 104]. Despite concerns about whether critical thinking can
A lack of critical thinking may also manifest through accepting a
be taught [138], research in education has developed a number of
solution that merely meets a baseline aspirational threshold [6, 119]
approaches to teaching critical thinking [104, 139], such as struc-
— in such cases, the AI solution is correct (albeit potentially of poor
tured argumentation exercises [25, 70, 72, 133]. Critical thinking
quality) and therefore not overreliance, strictly speaking.
can be measured through self-, peer-, or expert evaluation [66], us-
Collectively, these can inform design interventions to support
ing a range of questionnaires [35, 65, 73, 145, 146], justified multiple
critical thinking for knowledge workers. Still, these systems and
choice questions, structured essays, protocols for whole-portfolio
tools do not engage with how the need for critical thinking support
assessment, task observation, and peer interaction [34, 105]. In our
changes due to shifts in workflow caused specifically by the use of
study, we apply a one-item five-point scale assessment for each
GenAI. We also lack empirical foundations for understanding how
of the six cognitive activities associated with critical thinking (six
knowledge workers enact critical thinking in real-world GenAI
items in total, see Section 3.1.3), similar to previous work (e.g.,
workflows.
Alaoutinen and Smolander [3]).

2.3 Effects of automation on thinking and
2.2 Design research for critical and reflective
knowledge workflows: writing and memory
thinking
Effects on writing. Generative AI tools like Copilot and Chat-
Previous research has investigated how interaction design can
GPT can boost writing productivity by assisting with tasks such
encourage critical or reflective thinking. Various dimensions of
as content generation, idea creation, and stylistic editing, helping
the space of critical thinking interventions have been explored.
both expert and novice writers [18, 84, 112, 135]. However, there
For instance, whether the system should be proactive, i.e., intro-
are concerns that novice writers may become overly reliant on
duce critical thinking prompts without an explicit user request
these tools, potentially impairing their long-term skill development
[69, 109]. Or the extent to which user participation and engage-
by bypassing critical writing processes such as constructing log-
ment is important in creating critical thinking outcomes, e.g., pre-
ical arguments and understanding subject matter [14, 53, 63, 64].
senting AI explanations as questions rather than statements im-
To mitigate this, using GenAI for individualised, content-focused
proves logical discernment [24], questions also improve critical
feedback may help novice writers develop writing skills while im-
reading [110, 142], attention checks promote systematic thinking
proving productivity [58, 86, 144]. Although human feedback has
[49], conflict-filled discussion induces critical thinking [78], and
traditionally been necessary for effective self-improvement, the
in general increased engagement results in behavioural changes
integration of AI into tools like Microsoft Word could democra-
[82, 92]. Research has explored the effectiveness of gamification of
tise access to writing skill development by providing consistent,
critical thinking [31, 91, 129]. Research has also explored the extent
low-cost feedback [2, 123]. Early studies suggest that AI-generated

feedback can improve writing quality and logical structure, espe-
priming”, helping participants better understand the concept of crit-
cially for lower-performing students and less confident English
ical thinking, thus soliciting better recognition of critical thinking
learners [79, 101, 128, 135]. Thus, equipping AI tools with better
behaviours in participants’ daily GenAI use.
feedback mechanisms could foster long-term writing skill develop-
In total, we received 319 survey responses, in which participants
ment while addressing inequalities in access to writing education
shared a total of 936 real-world examples where they used a GenAI
[2, 79], and enable humans and AI to interact over time to maximise
tool for their work, and shared how critical thinking played a role
both productivity and learning outcomes [128, 135].
in these tasks.
To answer RQ1, we created an explanatory regression model
Effects on memory. While GenAI and conversational search en-
with a dependent variable measuring whether participants perceived
gines can streamline tasks like literature reviews, some fear that out-
the enaction of critical thinking when using GenAI tools for the tasks
sourcing this work could harm our ability to learn and remember, in
they shared, and independent variables corresponding to two sets
what is sometimes referred to as “digital amnesia” [47, 111], though
of factors that we hypothesised might correlate with the tendency
evidence for this effect is largely inconclusive [19, 21, 27, 127]. Re-
to engage with tasks critically: 1) task factors: measures about
search shows that summarising material and follow-up writing
the task at hand — e.g., task type, confidence in doing the task. 2)
practice enhance memory by integrating new knowledge with ex-
User factors: measures about users — e.g., age, gender, occupation,
isting knowledge [62, 93, 134], but real-world summary writing is
tendency to reflect in work, and trust in GenAI. In addition, we
often passive and ineffective [15, 16, 41, 121, 140], and thus may
analysed participants’ motivators and inhibitors for critical thinking
not improve recall in comparison to simply re-reading the text
from their free-text responses.
[124]. GenAI tools like ChatGPT and Copilot can mitigate these
To answer RQ2, we create explanatory regression models with
drawbacks, especially for less experienced learners, by providing
dependent variables measuring whether participants perceived dif-
high-quality summaries upon which collaborative, self-monitored
ferent cognitive activities constituting critical thinking (e.g., breaking
writing tasks can be conducted [120, 125]. Cognitive science shows
down a problem, putting together ideas) to be more or less effortful
that effective learning requires “grounding” information through
when using a GenAI tool for the tasks compared to when not using
multiple perspectives and examples [10, 11, 68], and GenAI can
one. Independent variables included the same set of factors as for
offer personalised analogies to aid this process [77, 90].
RQ1 above. We also analysed participants’ free-text responses to
In summary, previous work has defined critical thinking and
understand why they perceived these cognitive activities as more
investigated ways to develop and measure this skill in educational
or less effortful due to GenAI.
settings. Separately, design research has investigated ways of devel-
oping technology that induces critical reflection. It has also been
## 3.1 Survey Design
found that AI tools can significantly impact common knowledge
To model the relationship between task and user factors as they
workflows, such as writing. However, there is a gap in understand-
relate to critical thinking activities, we designed a survey as follows
ing knowledge workers’ perceptions of how GenAI affects their
(see Appendix A.1 for the complete survey).
enaction of critical thinking, and the effort of doing so, across a
broad range of use cases. This is the gap we address with our survey.
3.1.1 Task-Related Factors. Prior studies have shown that knowl-
edge workers apply GenAI tools for a range of tasks and express
## 3 Method
different needs while doing these tasks [13], and that their perceived
To answer our research questions — when and how knowledge
confidence in themselves and AI doing the tasks can influence their
workers perceive the enaction of critical thinking when using
use and reliance on the tool [20, 22, 83, 130]. We hypothesised that
GenAI (RQ1), and when and why do knowledge workers perceive
factors relating to the user’s task, including task type, confidence
increased/decreased effort for critical thinking due to GenAI (RQ2)
in themselves, and AI doing the task, could affect their critical
— we conducted an online survey on the Prolific platform2 to study
thinking.
knowledge workers’ experiences with critical thinking when using
GenAI tools for their work.
Task type. Brachman et al. [13] classify knowledge workers’ cur-
To ensure participants fully understood the scope and meaning
rent usage of GenAI tools into nine types (See Table 1), grouped
of our questions on critical thinking, as part of the survey study
into three major categories: 1) for creation, 2) to find or work
onboarding, they were introduced to the concept of critical think-
with information, 3) to get advice. This taxonomy offers clear
ing in the context of using GenAI through concrete examples of
distinctions among the major categories of task type, which we
how critical thinking could be applied at various levels of Bloom’s
hypothesised would correlate with users’ critical thinking due to
taxonomy (e.g., checking the tone of generated emails, verifying
differing objectives and requirements. We follow Brachman et al.
the accuracy of code snippets, and assessing potential biases in
[13]’s taxonomy and operationalise their task type categorisation in
data insights). These examples served to sensitise participants to
our survey, focusing on the major categories. For each GenAI tool
the various dimensions of critical thinking while avoiding concep-
use example, participants were first asked to describe in detail the
tualising critical thinking too narrowly. These acted as “cognitive
task they did (i.e., Please tell us: 1) what you were trying to achieve,
2) in what GenAI tool, and 3) how you used the GenAI tool, including
any prompts.). Then, they were asked to pick one of the nine task
2https://prolific.co/
types that best described their task. Using this information, we

Table 1: Categories and sub-categories for GenAI tool usage [13].

Category Sub-category Description
Creation Artefact Generate a new artefact to be used directly or with some modification
Idea Generate an idea, to be used indirectly
Information Search Seek a fact or piece of information
Learn Learn about a new topic more broadly
Generate a shorter version of a piece of content that describes the
Summarise
important elements
Analyse Discover a new insight about information or data
Advice Improve Generate a better version
Guidance Get guidance about how to make a decision
Validation Check whether an artefact satisfies a set of rules or constraints

classified each example as creation, information, or advice, per the
Perceived enaction of critical thinking. A key dependent variable
Brachman et al. [13] taxonomy.
of RQ1 — when knowledge workers perceive the enaction to think
critically — was answered using a pair of questions, first asking
Task confidence. Guided by prior studies on user confidence in
whether participants perceived that they had performed critical
AI-assisted decision-making [20, 85, 130], for each self-reported
thinking for that task (a binary yes/no question), followed by a free
task we consider three aspects of user confidence: 1) confidence in
text question asking them to justify their response. If participants
self (i.e., How confident are you in your ability to do this task without
answered “yes” to the first question, they were asked to elaborate
GenAI?), 2) confidence in GenAI (i.e., How confident are you in the
why and how they enacted critical thinking in free text (i.e., Please
ability of GenAI to do this task?), and 3) confidence in evaluation
share one real-world example when you applied the critical thinking
(i.e., How confident are you, in the course of your normal work, in
tactic(s) to this task, and explain why you did critical thinking.), as
evaluating the output that AI produces for this task?). Participants
well as the challenges, if any, they faced while doing so (i.e., When
rated each aspect of confidence on a five-point scale ranging from
applying this critical thinking tactic during your use of GenAI tool,
“not at all confident” (1) to “extremely confident” (5).
have you ever encountered any challenges and obstacles?). If the
participants answered “no” to the question, they were asked to
3.1.2 User factors. We hypothesised that participants’ general ten-
elaborate on why they did not think critically for the task, in free
dency to reflective thinking and trust in GenAI would affect their
text.
baseline critical thinking awareness and practice, and adapted vali-
dated instruments from prior work to measure this.
Perceived effort in critical thinking: Bloom’s taxonomy. As dis-
cussed in Section 2, we selected Bloom’s taxonomy as the frame-
Tendency to reflect on work. We use Kember et al. [65]’s Reflec-
work to operationalise the measurement of critical thinking activ-
tive Thinking Inventory to measure participants’ baseline tendency
ities [12]. The taxonomy includes six different levels of cognitive
to think reflectively. Reflective thinking is closely related to crit-
activities: Knowledge (i.e., recall), Comprehension (i.e., organis-
ical thinking (Section 2) and the Kember et al. inventory can be
ing/translating ideas), Application (i.e., problem-solving), Analysis
interpreted as a proxy for the disposition to think critically [38].
(i.e., breaking down a problem), Synthesis (i.e., putting together
Trust in generative AI. We measure participants’ overall trust in
ideas), and Evaluation (i.e., evaluating and quality checking). See
GenAI, which has been shown to correlate with users’ attitudes
Table 2 for more details.
and adoption of the use of the technologies [43, 76]. To that end,
For each task example, participants were asked if, and how much,
we adapted the six-item Propensity to Trust Technology scale [56],
the use of the GenAI tool changed the effort of critical thinking
replacing the word “technology” with “GenAI”.
activities compared to when they did not use the AI tool. We used
the five-point scale “much less effort”, “less effort”, “about the same”,
Gender, age, and occupation. We collect demographic informa-
“more effort”, to “much more effort” (which we code as integers
tion, including gender, age range and occupation. For occupation,
ranging between 2 and +2). Participants could choose “N/A” if
participants self-selected the most appropriate occupation cate-
they thought that a cognitive activity was not relevant to the task.
gory from the Occupational Information Network (O*NET)’s oc-
Finally, participants were asked to elaborate in free-text why they
cupational listings3. We classify occupations as being in risk of
had marked any critical thinking activities as requiring more or
automation based on the economic analyses of Ghosh et al. [42],
less effort with GenAI.
including the categories of Office and Administrative Support, Sales
and Related, Computer and Mathematical, Business and Financial
## 3.2 Study Setup and Recruitment
Operations, and Arts, Design, Entertainment, Sports, and Media.
We recruited participants through the Prolific platform who self-
3.1.3 Critical Thinking, Associated Cognitive Activities, and Effort.
reported using GenAI tools at work at least once per week. This
criterion ensured the study focused on knowledge workers with
direct, ongoing experience integrating GenAI tools into their day-
3A list of 23 occupation categories listed as “Major Group” in https://www.onetcenter.
org/taxonomy/2019/structure.html
to-day work tasks. We received 333 responses but excluded 14 from

Table 2: Cognitive activities defined in Bloom’s taxonomy [12].

Cognitive activity Description
Knowledge Recognising or remembering facts, terms, basic concepts, or answers
Comprehension Organising, summarising, translating, generalising, giving descriptions, and stating the main ideas
Application Using acquired knowledge to solve problems in new situations
Examining and breaking information into component parts, determining how the parts relate to one
## Analysis
another, identifying motives or causes, making inferences, and finding evidence to support generalisations
Building a structure or pattern from diverse elements; putting parts
Synthesis
together to form a whole or bringing pieces of information together to form a new meaning
Presenting and defending opinions by making judgements about information, the validity of ideas,
## Evaluation
or quality of work based on a set of criteria

Table 3: Participant demographics.
we measure participants’ perceived enaction of critical thinking,
perceived effort in critical cognitive activities, and perceived confi-
Dimension Sub-dimension Participants
dence. All participants shared three examples. However, they were
Gender Man 159 (49.84%)
allowed to skip any task type they did not have experience of and
Woman 153 (47.96%)
substitute another task type — e.g., a participant could share two
Non-binary/gender diverse 5 (1.57%)
examples about Creation and one example about Advice, if they
Prefer not to say 2 (0.63%)
Age 18-24 86 (26.96%)
had no experience of an Information task.
25-34 143 (44.83%)
After participants shared three examples of using GenAI tools,
35-44 62 (19.44%)
the survey assessed their overall reflective thinking tendency, trust
45-54 21 (6.58%)
in GenAI, and demographic details such as gender, age group, and
55+ 7 (2.19%)
occupation.
GenAI ChatGPT 309 (96.87%)
tool use* Microsoft Copilot (website) 74 (23.20%)
We employed quantitative and qualitative analyses, guided by
(top 5) Gemini (website) 69 (21.63%)
our research questions. Both RQ1 — when and how do knowl-
Copilot in Microsoft products (e.g., Word) 60 (18.81%)
edge workers perceive the enaction of critical thinking when using
Gemini in Google products (e.g., Google Slides) 49 (15.36%)
GenAI? — and RQ2 — when and why do knowledge workers per-
Occupation Computer and Mathematical 59 (18.50%)
ceive increased/decreased effort for critical thinking due to GenAI?
(top 5) Arts, Design, Entertainment, Sports, and Media 44 (13.79%)
Office and Administrative Support 38 (11.91%)
— were answered via both quantitative and qualitative analysis (See
Business and Financial Operations 35 (10.97%)
Figure 1 for an overview of our approach).
Educational Instruction and Library 23 (7.21%)
Country United Kingdom 37 (11.60%)
3.3.1 Dataset Cleaning and Overview. Our 319 participants shared
of residency Canada 25 (7.84%)
a total of 957 real-world examples of their use of GenAI tools at
(top 5) United States 20 (6.27%)
work. We removed 11 examples lacking sufficient detail to analyse
South Africa 18 (5.64%)
(e.g., brief or vague examples like “To build my portfolio.”). We also
Poland 17 (5.33%)
removed 11 examples for which a participant shared duplicated or
*participants selected all the GenAI tools they use at work
non-GenAI tool use examples in their responses.
We retained 936 examples, including 374 (39.96%) related to
Creation, 303 (32.37%) related to Information, and 259 (27.67%)
the analysis due to low response quality (i.e., low-effort free-text
related to Advice. Our participants self-reported to have enacted
responses). For the remaining 319 responses, participants spent an
critical thinking for 555 (59.29%) of the examples they shared, and
average of 43.19 minutes (STD=23.13) in completing the survey. The
perceived critical thinking activities, overall, to require less effort
319 participants (159 men, 153 women, 5 non-binary/gender diverse,
when using a GenAI tool compared to when not using one (see DV
2 prefer not to say) came from diverse age groups, occupations, and
distribution in Table 4).
countries of residence (see Table 3). Participants were compensated
with GBP £10 for completing the study. Our study protocol was
3.3.2 Quantitative Analysis. To model the relationship between
approved by our institution’s ethics and compliance review board.
task and user factors (independent variables) with (1) a binary mea-
All participants were briefed and signed a consent form.
sure of users’ perceived enaction of critical thinking and (2) six
five-point scales of users’ perceived effort in cognitive activities
## 3.3 Analysis Procedure
associated with critical thinking, we respectively fit (1) one random-
In our survey, participants were asked to share three real examples
intercepts logistic regression model and (2) six random-intercepts
of their GenAI tool use at work. To increase the variety of examples
linear regression models. To account for repeated measures, we in-
collected, participants were asked to think of three different exam-
clude Participant ID as a random intercept term. For all categorical
ples, one for each task type: Creation, Information, and Advice (see
variables, we selected the most common factor level as the base-
Section 3.1.1). Then, participants were asked to share an example
line reference. To correct for multiple comparisons, we apply the
of each task type in detail. The order of task types was randomised
Benjamini–Hochberg procedure [9] with a total of 98 hypothesised
to avoid order and fatigue effects. For each example, as mentioned,
predictors across the seven models, yielding a corrected p-value

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/microsoft-the-impact-of-generative-ai-on-critical-thinking-self-reported-reductions-in-cognitive-effort-and-confidence-effects-from-a-survey-of-knowledge-workers-fig1-a45c562a.png)

Figure 1: Schematic overview of the survey design and our corresponding analysis approach.

threshold of 0.007. We adjust the p-values accordingly and report
codebook in Appendix Table 5. We also report on how frequently
significant effects based on these corrected values.
participants discussed the identified themes.
Table 4 summarises the seven models and reports the corrected
p-values. For interpretability, we computed z-scores to standardise
4 Findings for RQ1: When and how do
each numeric user factor (i.e., overall tendency to reflect, overall
trust in GenAI). Thus, a positive coefficient implies the increase in
knowledge workers perceive the enaction of
log odds (in the logistic regression model) or the value (in the linear
critical thinking when using GenAI?
regression models), for every one standard deviation increase of that
To answer RQ1, we investigated how knowledge workers define crit-
factor. A negative coefficient implies the opposite. For confidence
ical thinking (Section 4.1), and when (Section 4.2) and why (Section
scales (i.e., confidence in self, confidence in GenAI, confidence in
4.3) they enact critical thinking in their use of GenAI tools. Quali-
evaluation), a positive coefficient is the increase in log odds/values
tatively, we found that knowledge workers view critical thinking
for every one-point increase above the base score (1: not at all confi-
as ensuring the objectives and quality of their work. Through our
dent), and a negative coefficient implies the opposite. For categorical
quantitative analysis of when knowledge workers do critical think-
and binary factors (i.e., task type, gender, age group, occupation
ing, we found their confidence in themselves doing and evaluating
in risk of automation), the coefficient is the predicted difference in
the task, and their general tendency to reflect on work strongly
log odds/increase of the values for a given factor level relative to a
correlated with their perceived enaction of critical thinking. We
baseline level. Positive coefficients imply increased log odds/values
also found a negative correlation between the perceived enaction of
relative to the reference level and vice versa.
critical thinking and their confidence in AI doing the task. Finally,
we qualitatively analysed participants’ free-text responses to un-
3.3.3 Qualitative Analysis. Guided by our research questions, we
derstand why they do or do not enact critical thinking, identifying
open-coded [23] participants’ free-text responses on i) why they
three key motivators (work quality, potential negative outcomes,
did or did not think critically when using GenAI tool for the task,
skill development) and three inhibitors (awareness, motivation,
ii) why they perceived more or less effort to perform critical think-
ability) for critical thinking.
ing activities with the GenAI tool. One researcher performed the
initial coding on 50 survey responses in discussion with three
other researchers to iteratively construct a codebook. Another re-
4.1 How knowledge workers enact critical
searcher joined the coding process when the initial codebook was
thinking
constructed, and was trained with the initial codebook. The two
researchers then coded the remaining 269 survey responses. All re-
We first explored knowledge workers’ definition and perceived en-
search team members regularly met and discussed emerging themes
action of critical thinking by examining the activities they describe
during the coding process. Disagreements were negotiated and re-
as performing critical thinking. While our participants worked
solved at each stage, using negotiated agreement best practices
across diverse occupations, the common denominator was that
[87]. We report our findings in Sections 4 and 5, and include the
they viewed critical thinking in their GenAI tool use as cognitive

activities performed to ensure the quality of AI responses, and
They applied multiple types of quality criteria and verification
intentionality while using the tools.
approaches.
We mapped our findings to each phase of knowledge workers’
Ensure quality through objective criteria (125/319). When applica-
GenAI tool workflow. We classified knowledge workers’ critical
ble, knowledge workers evaluate the GenAI output with objective
thinking practices into 1) goal and query formation, 2) inspect
criteria (which we define as those that are straightforward to articu-
response, and 3) integrate response. Our analysis is based primarily
late and apply4), such as if the output complies with their queries, or
on workflow characterisations from previous work [29, 46, 130],
if the generated artefact is functional (e.g., generated code compiles
though more general frameworks for human cognitive problem
without errors). For example, when P278 prepared a specification
solving [137] and problem solving with AI [60, 89, 108] are also
document for her client with ChatGPT, “I had to make sure each
related.
piece of text generated met the requirements of the client based on
criteria [in the prompt] like colour palette, and people in photos -
4.1.1 Goal and query formation. During goal and query formation,
male/female, skin tone, etc.” Similarly, when asking for a content
participants enact critical thinking through prompt optimisation to
summary, knowledge workers ensure the response is “properly tak-
produce the responses they desire. They also enact critical thinking
ing all info into account” (P177) and check “whether the AI added
by “taking a step back” to consolidate their goals and queries to the
irrelevant content and if it changed up my main point of the letter”
tools. These phenomena correspond to the goal and query formula-
(P144). Artefacts such as program code can be tested for quality
tion phases in the iterative goal satisfaction framework proposed
using other software tools such as compilers, or runtime environ-
by Drosos et al. [29].
ments such as browsers. For example, P308 asked Claude to write
Form goal (6/319). Before engaging with a tool, knowledge work-
code for her web application, and had “to make sure it runs without
ers reflect on their goals, needs and intents, and identify a need
error and then observed how it functioned.”
for assistance where the GenAI tool could be applied. For example,
Ensure quality through subjective standards (77/319). Knowledge
when P140 tried to learn the functionality of a code snippet through
workers also evaluate GenAI output through response-specific sub-
ChatGPT, he saw critical thinking as the need to “analyze what my
jective quality standards, some of which reflect what Paul and Elder
goal was and how I was going to achieve it... I had to first learn what
[103] refer to as “intellectual standards” in thinking. Some partici-
was I going to use in order to make progress.” Similarly, participants
pants evaluated the real-world feasibility of any suggestions. For
defined critical thinking as setting clear goals in mind before using
example, when P297 looked into her social service work for people
GenAI tools to generate images (e.g., P14) and ideas for a report
with mental health disorders and learning disabilities, she had to
(e.g., P2).
“really think about whether the answer the GenAI tool gave me would
Formation of intentions applies to other computational tools and
be easily transferrable to real life situations in social care... not every
is not unique to GenAI. However, as emphasised in the generative
company has the budget and necessary equipment to provide this
AI metacognitive framework proposed by Tankelevitch et al. [130],
most of the times.” Others evaluated the internal logic of the AI
critical thinking in the form of goal setting is particularly relevant
response. For instance, when a forex and commodities trader (P10)
due to its direct connection with the process of “forming queries” —
used ChatGPT to “generate recommendations for new resources and
users must first establish clear goals to effectively generate queries
strategies to explore to hone my trading skills, I evaluated whether
for the tool.
the stated ideas flowed logically.” Participants also evaluated the
relevance of the AI response, to see how well it matches “with my
Form query (30/319). Some knowledge workers enacted critical
presentation on Kaizen methods on performance management” (P188)
thinking by creating or revising prompts to GenAI tools to get the
or whether it is appropriately “in a manner that address the needs
desired response. With a goal in mind, knowledge workers create
of the target job role and attract attention of the recruiter” (P123).
queries that further clarify the final deliverables for the tool. For
example, when P97 tried to create an art piece for her website, “[I]
Verify information by assessing referenced sources (23/319). Partic-
was reflective when it came to giving the correct prompts, in order to
ipants were generally aware of the issues of hallucination in GenAI,
get the correct result a correct description needs to be given.”
and manually verify sources that are directly referenced in GenAI
The process of iterating on a prompt may help clarify knowledge
output to ensure they are real and reputable. This is especially true
workers’ goals and provide an opportunity for enacting critical
when users request high stakes information, such as advice for
thinking. For instance, when a teacher (P19) generated an image
medical symptoms (e.g., P5), or the references need to be verifiable
with DALL-E for her presentation about hand washing at school: “I
for the task to progress, e.g., in P213’s job search: “I was looking for
noticed it was missing soap dispensers. So I changed my prompt to
a full-stack role and there was no such role at the company [websites]
include them and tried again... By thinking about what the image
the GenAI listed”.
really needed to show, I got a much better result from the AI for my
presentation.”
Verify information by cross-referencing external sources (114/319).
More commonly, knowledge workers cross-referenced information
4.1.2 Inspect response. Prior work has identified the work of under-
in the GenAI output against reputable, external sources, to validate
standing and evaluating GenAI output as a key aspect of working
it. For tasks within their domain knowledge, our participants relied
with GenAI [29, 46, 114, 130]. Participants also enacted critical
thinking by assessing if a GenAI output meets certain criteria and
4We acknowledge that this is a necessary oversimplification, and there are degrees of
standards, or if the information it contains is verified or verifiable.
subjectivity in every criterion.

on their own knowledge to identify biases and limitations of the
GenAI tool use (see Perceived Enaction of Critical Thinking in Table
AI response, as noted by P133: “the AI may suggest repertoire [for
4). We discuss key findings for each type of factor, in turn.
the concert I direct], but it sometimes is very American-centric. I often
4.2.1 Task Factors. While prior work suggests that knowledge
have to use my judgment to come up with a repertoire that fits my
workers employ task-dependent strategies for GenAI tool use [13],
reality.” For responses involving technical and professional details,
we did not find a main effect on perceived critical thinking for task
participants cross-referenced technical or formal documenta-
type (Creation, Advice, Information). Instead, users’ perceptions
tions such as official manuals, guidelines, and reports to verify the
of confidence — in themselves and in AI doing the task — signifi-
reliability of the responses. For example, a nurse (P250) verified
cantly correlated with their perceived enaction of critical thinking.
a ChatGPT-generated educational pamphlet for newly diagnosed
In line with recent projections that more accessible GenAI tools
diabetic patients by cross-checking with the diabetes management
may exacerbate the risks of technology over-reliance [29, 102, 130],
guidelines from her hospital. Similarly, participants verified AI re-
our results provide empirical evidence that knowledge workers’
sponses with a more general web search for information accessible
confidence in AI doing the tasks indeed negatively correlates with
from online forums (e.g., Quora, YouTube, Wikipedia) and other
their enaction of critical thinking (𝛽=-0.69, 𝑝 < 0.001). Nevertheless,
websites. While less common, participants also shared other exter-
we also found that knowledge workers’ confidence in doing the
nal sources for cross-referencing, such as responses of other GenAI
task themselves (𝛽=0.26, 𝑝 = 0.026) and evaluating AI responses
tools, other task-specialised tools (e.g., language translation), and
(𝛽=0.31, 𝑝 = 0.046) both positively correlate with their enaction
consulting human domain experts.
of critical thinking. These findings suggest that a reflective ap-
4.1.3 Integrate response. Prior work has suggested GenAI requires
proach toward the use of GenAI tools, which can lead to what prior
knowledge workers to perform “critical integration” [114]: the work
work refers to as “pathways to non-reliance on AI” [20], is more
of editing and incorporating GenAI output into a broader workflow.
likely to occur when knowledge workers have more confidence
Qualitatively, we observe that participants integrate GenAI output
in doing the task without AI, or in evaluating AI responses. Our
to their tasks in two distinct ways: they focus either on the content
qualitative analysis (see Section 4.3) finds that participants enacted
— selecting and manipulating a part of the output for use — or form
critical thinking when trying to improve the quality and mitigate
— modifying style, wording, tone, etc.
the negative consequences of AI responses.

Integrate partial response (36/319). GenAI excels at generating
4.2.2 User Factors. We also found that knowledge workers’ overall
large amounts of information that appear relevant, and not all of it is
tendency to reflect on their work had a positive effect on perceived
useful. Participants viewed the process of selectively incorporating
enaction of critical thinking (𝛽=0.52, 𝑝 < 0.001). This suggests that
the relevant parts of GenAI output into their tasks as critical think-
knowledge workers who already engage in critical thinking in their
ing. For example, when P188 used ChatGPT to help her summarise
work are likely to continue doing so even when using GenAI tools.
her past work as an auditor for her resume: “some of the information
However, in contrast to knowledge workers’ confidence in AI doing
provided did not particularly relate to my role and even to the country
the task at hand (i.e., Confidence in AI, above), which negatively
I was working in. So rather than copying over everything, I had to
correlated with their perceived enaction of critical thinking, we
critically evaluate what would apply, the regulations mentioned - do
did not find a significant correlation between knowledge work-
they apply to the country I work in.”
ers’ overall trust in GenAI and their perceived enaction of critical
thinking. A possible explanation is that users’ reliance and confi-
Modify style to be appropriate for the task (45/319). Finally, partic-
dence on AI, as well as their perceived enaction of critical thinking,
ipants reflected not only on what to incorporate from the response,
might vary across tasks; accordingly, the variance that would have
but also how to incorporate it. They might add a “personal touch”,
been explained by the general user-level factor may already be well
or adjust the tone to align the response with their intended style.
captured by the task-level confidence factors.
For example, when P210 used ChatGPT to revise his paper abstract,
he had to rephrase the output with a scientific tone because “often
4.3 Motivators and inhibitors for the perceived
the AI writes awful stuff like “our groundbreaking and fundamental
enaction of critical thinking
analysis shows...” that sounds too emphatic and does not fit the scien-
tific style.” Participants also attempted to make the GenAI output
We analysed participants’ free-text responses about why they en-
read less “AI-generated” and more personal, as P254 noted: “I did
gaged in or prioritised critical thinking (or did not do so) when
make sure it [email composed by ChatGPT] read properly and made
using GenAI tools for work. We found that enaction of critical
sense and did sound like an email that I had composed myself and
thinking was motivated by improvement in work quality, avoid-
that a colleague would send.”
ance of negative outcomes, and skill development. We found many
inhibitors for the enaction of critical thinking related to awareness
4.2 When knowledge workers perceive the
(e.g., reliance on AI), motivation (e.g., lack of time), and ability (e.g.,
barriers to improving GenAI output).
enaction of critical thinking
Over 936 GenAI tool use examples, participants self-reported having
4.3.1 Critical thinking motivators.
enacted some critical thinking activity (see Section 4.1) for approxi-
mately 60% (555 out of 936) of them. Both knowledge workers’ task
Work quality (74/319). As shown in Section 4.1, participants’ crit-
confidence and their tendency to reflect on work are associated
ical thinking actions were often performed to improve the quality
with when they perceive the enaction of critical thinking during
of the work artefact being produced. A key motivator for critical

Table 4: Non-standardised coefficients of the mixed-effects regressions modeling knowledge workers’ perceived enaction of
critical thinking and perceived effort in cognitive activities when using generative AI tools.

Perceived
Compre-
Evalua-
Enaction of
Knowledge
Application
## Analysis
Synthesis
hension
tion
Critical Thinking
(N=782)
(N=768)
(N=753)
(N=825)
(N=849)
(N=764)
(N=930)
DV distribution
236/326/
333/335/
227/305/
219/320/
267/359/
177/246/
Binary: True/False
551/ 379
191/19/10
139/30/12
201/23/12
184/16/14
156/30/13
221/84/36
5-Likert: -2/-1/0/1/2
(Pseudo) r square/
0.43 0.33 0.32 0.37 0.43 0.38 0.44
conditional r square
Task Factors
Task type:
0 r 0 r 0 r 0 r 0 r 0 r 0 r
Creation
Task type:
0.12
0.04
0.00
0.06
-0.03
-0.04
-0.18
Advice
(𝑝 = 0.829)
(𝑝 = 0.816)
(𝑝 = 0.994)
(𝑝 = 0.713)
(𝑝 = 0.865)
(𝑝 = 0.839)
(𝑝 = 0.127)
Task type:
0.32
-0.13
-0.03
0.08
-0.14
0.01
0.14
Information
(𝑝 = 0.364)
(𝑝 = 0.223)
(𝑝 = 0.865)
(𝑝 = 0.474)
(𝑝 = 0.127)
(𝑝 = 0.967)
(𝑝 = 0.248)
Confidence
0.26*
0.02
0.02
0.08*
0.07
0.01
0.10*
in self
(𝑝 = 0.026)
(𝑝 = 0.713)
(𝑝 = 0.779)
(𝑝 = 0.029)
(𝑝 = 0.121)
(𝑝 = 0.965)
(𝑝 = 0.027)
Confidence
-0.69***
-0.11*
-0.13*
-0.09
-0.15**
-0.12*
-0.23***
in AI
(𝑝 < 0.001)
(𝑝 = 0.029)
(𝑝 = 0.014)
(𝑝 = 0.128)
(𝑝 = 0.003)
(𝑝 = 0.026)
(𝑝 < 0.001)
Confidence
0.31*
0.00
0.00
-0.06
0.10
-0.03
-0.01
in evaluation
(𝑝 = 0.046)
(𝑝 = 0.994)
(𝑝 = 0.97)
(𝑝 = 0.364)
(𝑝 = 0.06)
(𝑝 = 0.795)
(𝑝 = 0.967)
User Factors
Gender: Man 0 r 0 r 0 r 0 r 0 r 0 r 0 r
0.33
0.03
-0.03
-0.02
-0.15
-0.14
-0.21
Gender: Woman
(𝑝 = 0.38)
(𝑝 = 0.865)
(𝑝 = 0.865)
(𝑝 = 0.967)
(𝑝 = 0.248)
(𝑝 = 0.29)
(𝑝 = 0.127)
1.11
0.26
0.03
0.14
-0.51
-0.25
-0.45
Gender: Non-binary
(𝑝 = 0.517)
(𝑝 = 0.713)
(𝑝 = 0.967)
(𝑝 = 0.865)
(𝑝 = 0.338)
(𝑝 = 0.718)
(𝑝 = 0.495)
Age group: 25-34 0 r 0 r 0 r 0 r 0 r 0 r 0 r
0.14
0.08
0.06
0.04
0.01
0.06
-0.01
Age group: 18-24
(𝑝 = 0.849)
(𝑝 = 0.713)
(𝑝 = 0.783)
(𝑝 = 0.865)
(𝑝 = 0.967)
(𝑝 = 0.795)
(𝑝 = 0.967)
0.31
0.00
-0.11
-0.01
-0.06
-0.02
-0.05
Age group: 35-44
(𝑝 = 0.59)
(𝑝 = 0.994)
(𝑝 = 0.589)
(𝑝 = 0.967)
(𝑝 = 0.841)
(𝑝 = 0.967)
(𝑝 = 0.865)
-0.28
0.18
0.24
0.25
0.23
0.17
0.24
Age group: 45-54
(𝑝 = 0.804)
(𝑝 = 0.529)
(𝑝 = 0.378)
(𝑝 = 0.38)
(𝑝 = 0.451)
(𝑝 = 0.589)
(𝑝 = 0.474)
-0.96
-0.11
0.04
-0.23
-0.25
0.04
-0.57
Age group: 55+
(𝑝 = 0.474)
(𝑝 = 0.865)
(𝑝 = 0.967)
(𝑝 = 0.713)
(𝑝 = 0.713)
(𝑝 = 0.967)
(𝑝 = 0.29)
Occupation’s risk
0 r 0 r 0 r 0 r 0 r 0 r 0 r
of automation: Low
Occupation’s risk
0.17
0.04
0.10
0.15
0.03
0.19
0.16
of automation: High
(𝑝 = 0.74)
(𝑝 = 0.829)
(𝑝 = 0.451)
(𝑝 = 0.248)
(𝑝 = 0.865)
(𝑝 = 0.116)
(𝑝 = 0.29)
0.52***
-0.01
0.06
0.05
0.01
0.06
0.05
Tendency to reflect
(𝑝 < 0.001)
(𝑝 = 0.967)
(𝑝 = 0.378)
(𝑝 = 0.511)
(𝑝 = 0.967)
(𝑝 = 0.392)
(𝑝 = 0.59)
-0.01
-0.12*
-0.08
-0.17**
-0.12*
-0.05
-0.24***
Trust in GenAI
(𝑝 = 0.967)
(𝑝 = 0.029)
(𝑝 = 0.223)
(𝑝 = 0.002)
(𝑝 = 0.046)
(𝑝 = 0.499)
(𝑝 < 0.001)
Significance: \*p<.05; \*\*p<.01; \*\*\*p<.001; r: reference

thinking is to think of ways to improve AI responses. Participants
Potential negative outcomes (116/319). Participants shared that
shared several examples of when the AI response fell short of their
their critical thinking was driven by the potential negative out-
standards, and motivated critical revision. For instance, when P92
comes of their use of GenAI. They wished to avoid harm to their
generated content with ChatGPT for his company website: “the
work, such as program code that produces wrong outcomes (e.g.,
output is way too cookie cutter, full of cliché [text] and boring. I have
P210), outdated information (e.g., P240), or faulty mathematical
to edit it a lot to get something out of it that I could ever give to my
formulas (P155). This is especially the case when GenAI is applied
bosses.” GenAI output can be too shallow and generic for partici-
in high-stakes scenarios and workplaces. For example, P267 used
pants’ tasks, motivating them to think critically about the depth
ChatGPT to help her write the pharmacist continuing professional
and specificity of the work. As P133 noted when using ChatGPT to
development (CPD) documents, “the entry is to be submitted for
write an executive summary: “the AI does not understand the niche
review so I would to double check to be sure otherwise I might have to
type of work I do. I have to adapt the output to fit my needs.”
face suspension.”

Social conflict was another undesirable outcome that motivated
(P101) or composing legal letters (P204). This self-doubt led them
critical thinking about GenAI output. For example, P101 reported
to accept GenAI outputs by default — a phenomenon corroborated
to a younger supervisor with a different ethnic background. Thus,
by prior studies [117].
when preparing work presentations and emails with ChatGPT, he
Overreliance on computing technology is not a novel phenom-
must “always consider that hierarchy, age, respect for even Chinese
enon; however, GenAI tools can exacerbate the associated risks.
festivals, [which] are culturally really important for them.”
Indeed, such reliance may be tolerable for low-stakes tasks, like
grammar checking, but it can lead to significant negative outcomes
Skill development (13/319). Finally, knowledge workers are in-
in high-stakes contexts, like drafting legal documents (e.g., [118]).
centivised to improve skills and learn best practices for their work,
While critical thinking may not be necessary for low-stakes tasks,
even when assisted by GenAI tools. Participants were motivated
it is risky for users to only apply critical thinking in high-stakes
to enact critical thinking about GenAI output as a means to learn
situations. Without regular practice in common and/or low-stakes
about the task and not simply rely on AI in the long run. For exam-
scenarios, cognitive abilities can deteriorate over time [5], and
ple, when P154 asks ChatGPT for solutions to the issue in a code
thus create risks if high-stakes scenarios are the only opportunities
snippet, “I make sure that I understood how it works and can do it
available for exercising such abilities. This phenomenon is well-
by myself next time.” Likewise, P176 used ChatGPT to improve an
documented, as in Bainbridge’s “Ironies of Automation” [7], and
important email draft to sound more professional, and he decided
has been recently revisited in the context of GenAI by Simkute et al.
to “read and break down all the suggested corrections to improve my
[122] as the “Ironies of Generative AI”.
email writing style”. This helped improve his writing style, and his
later emails “required less correction.”
Motivation barriers. Knowledge workers also discussed how pri-
oritising critical thinking in their work might be misaligned with
4.3.2 Critical thinking inhibitors. In this section, we organised the
their overall task motivations or job objectives. For example, par-
findings by highlighting the three types of critical thinking barriers
ticipants discussed a lack of time (44/319) for critical thinking at
introduced by the use of GenAI tools — i.e., awareness, motivation,
work. For instance, a sales development representative (P295) noted
and ability.
that “[t]he reason I use AI is because in sales, I must reach a certain
quota daily or risk losing my job. Ergo, I use AI to save time and
Awareness barriers. Potential downstream harms of GenAI re-
don’t have much room to ponder over the result.” Even when time
sponses can motivate critical thinking (see Section 4.3.1), but only
was not constrained, knowledge workers often lacked incentives to
if the user is consciously aware of such harms. Our analysis finds,
engage in critical thinking when it is perceived as not part of their
however, that GenAI tools create obstacles for knowledge workers
job responsibilities (11/319). P232, who used ChatGPT to write
to be aware of the need for critical thinking, especially when the
the company’s marketing campaigns: “verification and rewriting is
tasks are perceived to be less important, and when users trust and
handled by another part of the team. The team is able to verify, sense
rely on GenAI tools.
check and modify the content of the landing pages as they see fit.”
Some participants shared examples in which they thought crit-
ical thinking was unnecessary because their use of GenAI tool
Ability barriers. Participants face obstacles to enacting critical
is secondary (14/319) to their goals. P147 used “Dall-E for indirect
thinking, specifically in verifying and improving GenAI output,
purposes (visual reference), [so] there’s no need to over-correct what
even if they are otherwise motivated to do so. Participants report
the AI outputs.” Likewise, participants do not enact critical think-
barriers to inspect AI responses (58/319), such as not possessing
ing when the task is perceived to be trivial and insignificant
enough domain knowledge. As P290 noted: “in cases where you
(55/319), such as writing social media posts (P239) and meeting
don’t know the specific topic [e.g., translation and math problems],
minutes summary (P271).
it’s hard to determine whether the AI is giving the correct answer or
Complementing our quantitative findings, knowledge workers’
not.”
trust and reliance on GenAI (83/319) doing the task can discour-
Even if knowledge workers identify limitations in the GenAI
age them from critically reflecting on their use of the tools. Users
output, they encounter barriers in revising queries and improv-
often adopt a mental model that assumes AI is competent for simple
ing the response (72/319). For example, P239 received negative
tasks. This was influenced by users’ prior experience with GenAI
feedback from colleagues for a document that ChatGPT helped
tools, where the AI had proven trustworthy for specific tasks, as
her write, but “I’m not sure how I could have improved the text that
P289 noted: “With straightforward factual information, ChatGPT
ChatGPT wrote.” Also, GenAI tools can be “stubborn” and do not
usually gives good answers.” For instance, P275 remarked: “It’s a
follow through with users’ revised prompts, as P208 shared when
simple task [make a passage professional] and I knew ChatGPT could
asking GenAI to fix an error in his code: “it repeatedly recommended
do it without difficulty, so I just never thought about it, as critical
the wrong solution despite asking for a different suggestion.”
thinking didn’t feel relevant.” This mental model, however, can lead
to overestimating AI capabilities. Some users, like P185, believed
the information provided by GenAI tools was always truthful and
5 Findings for RQ2: When and why do
of high quality, while others (e.g., P143, P236) assumed the outputs
knowledge workers perceive increased/decreased
would consistently and accurately reflect referenced data sources.
effort for critical thinking due to GenAI?
Complementary to the perception of AI as being competent and
capable, some participants expressed self-doubt in their ability to
To answer RQ2, we report a descriptive analysis of participants’ per-
perform tasks independently, such as verifying grammar in text
ceived effort in cognitive activities associated with critical thinking,

as defined by Bloom’s taxonomy (Section 5.1) — i.e., recall (Knowl-
more effort to do so. We discuss this in more detail in Section
edge), organising/translating ideas (Comprehension), problem solv-
6.1.1.
ing (Application), breaking down a problem (Analysis), putting
5.1.2 User Factors. In contrast to our findings about knowledge
together ideas (Synthesis), and evaluating and quality checking
workers’ perceived enaction of critical thinking (see Section 4.2),
(Evaluation). We complement this with an analysis of participants’
we found no significant correlation between their overall tendency
free text elaborations on why they perceived an increase or de-
to reflect and perceived effort of critical thinking for any cognitive
crease in effort due to GenAI, observing three qualitative shifts in
activities. This suggests that knowledge workers who do (or do not)
critical thinking effort (Section 5.2).
tend to reflect on their work do not necessarily perceive a higher or
A perceived reduction in effort when using GenAI may be due
lower effort of critical thinking with GenAI. However, knowledge
to participants 1) enacting the same “amount” of critical thinking
workers’ overall trust in GenAI was negatively correlated with
but feeling supported by GenAI, 2) offloading the work of critical
perceived effort for four of the six cognitive activities — i.e., higher
thinking to GenAI, 3) enacting “less” critical thinking overall, or 4)
trust in the technology is associated with less perceived effort
conflating reduction in cognitive effort in general, with reduction
for Knowledge (𝛽=-0.12, 𝑝 = 0.029), Application (𝛽=-0.17, 𝑝 =
in critical thinking effort specifically. We address each of these
0.002), Analysis (𝛽=-0.12, 𝑝 = 0.046), and Evaluation (𝛽=-0.24, 𝑝 <
interpretations in context.
0.001). Thus, knowledge workers with higher levels of trust in
GenAI — generally or for specific tasks — perceive engaging in
5.1 When knowledge workers perceive
critical thinking activities to be less effortful. A possible explanation,
increased/decreased effort for critical
supplemented with our qualitative analysis in RQ1 (see Section
4.3.2), is that trust and reliance on GenAI inhibit the enaction of
thinking due to GenAI
critical thinking, i.e., users underinvest in critical thinking when
In the majority of examples, knowledge workers perceive decreased
using GenAI.
effort for cognitive activities associated with critical thinking when
using GenAI compared to not using one — examples that were re-
5.2 Why knowledge workers perceive
ported as “much less effort” or “less effort” comprise 72% in Knowl-
increased/decreased effort for critical
edge, 79% in Comprehension, 69% in Application, 72% in Analysis,
76% in Synthesis, and 55% in Evaluation dataset (See Figure 2). More-
thinking due to GenAI
over, knowledge workers tend to perceive that GenAI reduces the
To understand why participants perceived an increase or decrease
effort for cognitive activities associated with critical thinking when
in the effort of critical thinking due to GenAI, we analysed the
they have greater confidence in AI doing the tasks and possess
free-text responses in which they were asked to elaborate, mapping
higher overall trust in GenAI (see Table 4).
the responses onto the six cognitive activities.
We found that GenAI tools shift the effort of critical thinking
5.1.1 Task Factors. We found that knowledge workers’ confidence
in three distinct ways: for Knowledge and Comprehension, the
in AI doing the tasks negatively correlated with perceived effort for
effort shifts from information gathering to information verification;
five of the six cognitive activities (all except Application). The higher
for Application, effort shifts from problem-solving to AI response
the participant’s confidence in AI, the greater is their perceived re-
integration; and for Analysis, Synthesis, and Evaluation, effort shifts
duction in effort for Knowledge (𝛽=-0.11, 𝑝 = 0.029), Comprehen-
from task execution to task stewardship.
sion (𝛽=-0.13, 𝑝 = 0.014), Analysis (𝛽=-0.15, 𝑝 = 0.003), Synthesis
(𝛽=-0.12, 𝑝 = 0.026), and Evaluation (𝛽=-0.23, 𝑝 < 0.001). More-
5.2.1 Knowledge & Comprehension: From information gathering to
over, knowledge workers’ confidence in themselves doing the task
information verification. Efforts invested in Knowledge (e.g., retriev-
correlates positively with perceived effort in Application (𝛽=0.08,
ing relevant information) and Comprehension (understanding that
𝑝 = 0.029) and Evaluation ((𝛽=0.10, 𝑝 = 0.027). We qualitatively
information) often go hand in hand when using GenAI tools. In
analyse participant rationales in the next section in more detail,
general, participants perceived less effort in retrieving and curating
but one explanation for why knowledge workers’ confidence in AI
task-relevant information, because GenAI automates the process.
and in themselves had the opposite effects on perceived effort in
However, they perceived more effort in verifying the information
these cognitive activities is the following. GenAI tools can decrease
in the AI response.
knowledge workers’ cognitive load by automating a significant por-
Participants perceived less effort to fetch task-specific infor-
tion of their tasks, but as knowledge workers have more confidence
mation at scale, and in real-time (111/319). For instance, P232
in doing the task themselves, they employ more engaged practices
shared that her market research results through ChatGPT “are im-
in steering AI responses, especially when applying (Application)
mediate and at a sufficient level of detail for me to get to grips with
and evaluating (Evaluation) AI responses.
the basics of the industries. I would otherwise have to read a lot of
These findings, along with our quantitative findings for RQ1,
press reports and subscribe to multiple newsletters.”
reveal a connection between knowledge workers’ self-confidence
GenAI tools are perceived to organise and present informa-
and confidence in AI and their perceived critical thinking during
tion in a readable format (87/319). For example, P86 compared
GenAI tool use: 1) a higher confidence in GenAI is associated
his experience in searching in a web browser with that in Chat-
with less critical thinking even though it is perceived as less
GPT: “ Research using Google is time-consuming; even clicking on
effort to do so, and 2) a higher self-confidence is associated
a couple of websites takes more time than asking a single question
with more critical thinking even though it is perceived as
to an LLM. Also, the LLM produces organized answers... the tools

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/microsoft-the-impact-of-generative-ai-on-critical-thinking-self-reported-reductions-in-cognitive-effort-and-confidence-effects-from-a-survey-of-knowledge-workers-fig2-08d8c8e2.png)

Figure 2: Distribution of perceived effort (%) in cognitive activities (based on Bloom’s taxonomy) when using a GenAI tool
compared to not using one.

and techniques were categorized by type, and a dotted list was pro-
(19/319) to their tasks and to meet specific needs. For example,
duced for each.” Participants find it less effort to re-structure and
when P51 wrote a promotional blog post for their product launch,
summarise information in GenAI tools. E.g., P137 tried to update
“the AI-generated content required substantial editing to align with
protocol documents to comply with a new standard: “ I did not have
specific marketing guidelines and tone preferences. This editing process
to check the templates one by one... Questions I had related to the
could be time-consuming, particularly when ensuring that techni-
procedures were answered by the GenAI, and it helped me to know
cal details were accurate and comprehensible to our target audience.”
better this new standard.”
Additional application effort is incurred when knowledge workers
However, many participants shared examples when they per-
integrate AI-generated content with content from other sources, or
ceived more effort in information retrieval because the AI response
misjudge the extent to which GenAI output will be contextualised
can be wrong and needs verification (56/319). For example, when
to their scenario. As P36 noted “the extra effort in determining that
a lawyer (P147) used ChatGPT to find relevant laws for a legal case,
the code generated matched my existing code, and making subsequent
he noticed “AI tends to make up information to agree with whatever
alterations to make it fit was more effort than just doing it myself in
points you are trying to make, so it takes valuable time to manually
the end.”
verify.”
5.2.3 Analysis, Synthesis, and Evaluation: From task execution to
5.2.2 Application: From problem-solving to response integration.
task stewardship. Participants perceived these activities, overall, to
GenAI can contextually apply knowledge to users’ specific ques-
require less effort due to GenAI tools. Specifically, GenAI helps
tions and examples, reducing perceived effort for Application over-
knowledge workers scaffold complicated tasks and information; it
all. However, users must instead spend effort integrating GenAI
helps knowledge workers automate artefact creation; and it helps
output, in form and content (as mentioned in Section 4.1.3).
form feedback cycles that knowledge workers otherwise do not
Participants perceived less effort in problem-solving and ques-
have access to. Nevertheless, knowledge workers perceived in-
tion answering because GenAI tools provide personalised solu-
creased effort spent on AI stewardship — translating intentions
tions to their problems (77/319). For example, P154 compared his
into queries, steering AI responses, and assessing if the AI response
experience in reviewing code with and without ChatGPT: “trying
meets their quality standards for work, while retaining accountabil-
to understand how something works or understanding the problem
ity for the work.
is the main challenge. People have to “google” a lot. Find the correct
information and then try to find people facing similar problems. That
Analysis. Participants reported reduced effort when GenAI tools
takes a lot of effort. GPT simply answers those very fast and easily
helped to scaffold complicated tasks and information (48/319).
and mostly correctly.”
For instance, P203 used ChatGPT to write a complex Slack message
With in-context learning, GenAI can also apply users’ exam-
to an unfamiliar colleague, and “GenAI broke down the problem.”
ples to new context (9/319). For example, participants used GenAI
This helped her think Analytically, to derive criteria such as to
tools to generate text, guided with examples: “company has a set
“make sure the message structure is to the point and understandable to
out list of possible scenarios and how we can address them, all I have
someone who doesn’t have the same background knowledge” as well
to do is feed it to the AI, and it would generate a set response based
as “ensure that I am not missing elements or being confusing with
on the data given” (P268).
examples.”
Despite the ability for contextual tailoring, participants still
However, GenAI tools also require users to articulate their
reported an increased effort in having to apply the responses
needs and translate intentions into a query (45/319), which

was perceived to increase Analysis effort. As mentioned in Section
thinking tasks among knowledge workers. Conversely, with the im-
4.1.1, revising queries is a critical thinking activity specific to GenAI
portant caveat that users’ self-confidence is a subjective measure of
use. P24 described several phases of image generation prompting,
their knowledge, experiences, and abilities on the tasks [20, 59, 85],
saying “Image generation requires more effort for everything except
higher self-confidence is associated with more critical thinking,
the actual image generation. I have to think of what I want to be
even though workers who are confident in their own skills tend to
drawn, then on how the AI wants it described, then correct it when it
perceive greater effort in these tasks, particularly when evaluating
makes wacky outputs.”
and applying AI responses.
Our analysis does not establish causation. However, based on our
Synthesis. Participants perceived less effort when GenAI auto-
evidence, it is possible that fostering workers’ domain expertise and
mates the creation process (129/319), such as drafting documents,
associated self-confidence may result in improved critical thinking
responding to emails, or generating code.
when using GenAI. Task confidence significantly influences how
However, participants noted that the reduced effort in Synthesis
users engage with AI tools, particularly in the context of human-
could lead to less critical engagement with the task. For instance,
AI “collaboration” (notwithstanding objections to that term [113]).
P131, when generating advising campaigns for her business, re-
Previous frameworks have categorised human-AI collaborations
marked having “to read what ChatGPT generates and make sure that
by how often the user or the AI initiates an action [95], and which
it’s what I want, but not to [let it] think the whole idea.” Moreover,
entity takes on a “supervisory” role [88]. Our findings shed light
participants perceived it to be more effort to constantly steer AI
on this issue in the context of GenAI-assisted knowledge work.
responses (48/319), which incurs additional Synthetic thinking
High task confidence is associated with users’ ability to delegate
effort due to the cost of developing explicit steering prompts. For
tasks effectively, fostering better stewardship while maintaining
example, P110 tried to use Copilot to learn a subject more deeply,
accountability. Conversely, lower self-confidence may lead users to
but realised: “its answers are prone to several [diversions] along the
rely more on AI, potentially diminishing their critical engagement
way. I need to constantly make sure the AI is following along the
and independent problem-solving skills. This reliance on AI can be
correct ‘thought process’, as inconsistencies evolve and amplify as I
seen as a form of cognitive offloading [8], where users depend on
keep interacting with the AI.”
AI to perform tasks they feel less confident in handling themselves.
Confidence in AI is associated with reduced critical thinking
Evaluation. Finally, critical thinking is perceived to be less effort
effort, while self-confidence is associated with increased critical
because GenAI tools provide personalised feedback loops for
thinking effort. This duality indicates that design strategies should
tasks (40/319) that users otherwise do not have access to. For
focus on balancing these aspects. The aims are both to improve
example, to edit text P313 said he previously “would often go through
the quality of AI-assisted tasks and also to empower users to de-
multiple rounds of checks by others [humans] for feedback”, but with
velop their skills and maintain a balanced “relationship” with AI.
GenAI could do so “on my own time” by asking the “AI to do alternate
To address task confidence recalibration, AI tools could incorpo-
versions, and compare what I like and don’t”.
rate feedback mechanisms that help users gauge the reliability of
In certain cases where GenAI is perceived to have a strength
AI outputs, when to trust the AI and when to apply their critical
relative to the user’s own capability (e.g., in spelling or grammar in a
thinking skills. This aligns with the goals of explainable AI [33].
non-native language), GenAI responses are perceived to make
Moreover, the user should remain responsible and accountable for
few mistakes (19/319). Thus, participants perceived a reduced
the outcome. AI tools must support users in actively and critically
effort needed for Evaluation, as P239 noted: “I can be confident that
customising and refining AI-generated content. Tools may incorpo-
everything is spelt correctly, I don’t need to second guess myself... I can
rate explicit controls for users to regulate the extent of AI assistance,
get the reassurance I need without having to bother another person to
depending on their confidence levels and the task’s complexity.
check it for me.”
Those cases notwithstanding, as noted in Section 4.1.2, partici-
pants needed to evaluate AI-generated content (42/319) through
6.1.2 Awareness, Motivation, and Execution of Critical Thinking.
several objective and subjective criteria, and reported increased
Our study identifies key motivators for and inhibitors of critical
effort in doing so.
thinking among knowledge workers using GenAI. The design im-
plications are clear: critical thinking interventions for GenAI tools
should aim to enhance and leverage motivators while mitigating
## 6 Discussion
and avoiding inhibitors.
## 6.1 Implications for Designing GenAI Tools
One design approach is to enhance awareness of critical thinking
That Support Critical Thinking
opportunities. Our findings indicate that knowledge workers tend
6.1.1 Self-Confidence and Task Confidence. Task confidence ap-
to forgo critical thinking for tasks perceived as unimportant or
pears to significantly influence knowledge workers’ perceived en-
secondary, while engaging in it when aiming to improve task quality
action of critical thinking and the effort they invest in it. Specif-
or avoid negative outcomes. This suggests a need for both proactive
ically, a user’s confidence in GenAI is predictive of the extent to
and reactive critical thinking interventions. Proactive systems take
which critical thinking is exercised in GenAI-assisted tasks. Both
the initiative [52] to interrupt the user to highlight the need and
our quantitative and qualitative results suggest that higher confi-
opportunity for critical thinking in situations where it is likely to be
dence in GenAI is associated with less critical thinking, as GenAI
overlooked; a reactive approach would allow the user to explicitly
tools appear to reduce the perceived effort required for critical
request critical thinking assistance when it is consciously needed.

Another approach is to increase the motivation to think critically.
collaboration, in a human-AI “collaboration”, the responsibility and
Our study reveals that knowledge workers often neglect critical
accountability for the work still resides with the human user despite
thinking when they perceive it as outside their job scope, but en-
the labour of material production being delegated to the GenAI tool,
gage in it when aiming to improve their professional skills. Thus,
which makes stewardship strike us as a more appropriate metaphor
critical thinking interventions for GenAI tools could be positioned
for what the human user is doing, than teammate, collaborator, or
as contributing to long-term skill development and professional
supervisor.
growth, as opposed to an extraneous “co-auditing” [46] task that is
In light of these changes, training knowledge workers to think
only relevant on a task-by-task basis.
critically when working with GenAI should focus on developing
Finally, design could aim to enhance the ability to execute critical
skills in information verification, response integration, and task
thinking. We find that knowledge workers often refrain from criti-
stewardship. Training programs should emphasise the importance
cal thinking when they lack the skills to inspect, improve, and guide
of cross-referencing AI outputs, assessing the relevance and ap-
AI-generated responses. GenAI tools could incorporate features
plicability of AI-generated content, and continuously refining and
that facilitate user learning, such as providing explanations of AI
guiding AI processes. Additionally, a focus on maintaining founda-
reasoning, suggesting areas for user refinement, or offering guided
tional skills in information gathering and problem-solving would
critiques. The tool could help develop specific critical thinking
help workers avoid becoming overreliant on AI [102].
skills, such as analysing arguments [72], or cross-referencing facts
against authoritative sources. This would align with the motivation-
enhancing approach of positioning AI as a partner in skill develop-
## 6.3 Limitations
ment.
Our study has limitations that warrant consideration and offer
avenues for future research. Firstly, we observed that participants
## 6.2 Shifts in Critical Thinking Due to
occasionally conflated reduced effort in using GenAI with reduced
Generative AI
effort in critical thinking with GenAI. This misconception may stem
Critical thinking in knowledge work involves a range of cognitive
from the infrequent contemplation of critical thinking in their daily
activities, such as analysis, synthesis, and evaluation. We observed
tasks (regardless of whether they use GenAI), potentially leading
that the use of GenAI tools shifts the knowledge workers’ perceived
to inaccurate self-reporting. This conflation often occurred when
critical thinking effort in three ways. Specifically, for recall and
participants were satisfied with AI-generated responses, suggesting
comprehension, the focus shifts from information gathering to
that when AI produces expected outcomes, users may engage in
information verification. For application, the emphasis shifts from
less critical evaluation. Future studies could employ alternative
problem-solving to AI response integration. Lastly, for analysis,
measures of critical thinking, such as think-aloud protocols or task-
synthesis, and evaluation, effort shifts from task execution to task
based assessments, to better differentiate between effort reduction
stewardship.
and critical thinking processes.
The use of GenAI in knowledge work creates new cognitive
Secondly, we assess users’ subjective task confidence following
tasks for knowledge workers. The task of response integration is
prior work on AI-assisted decision-making [20, 59, 85]. Still, one’s
a prime example. Knowledge workers must assess AI-generated
subjective self-confidence may not always be well-calibrated with
content to determine its relevance and applicability to their specific
respect to objective expertise on tasks [39, 130]. Future work should
tasks, often modifying the style and tone to align with the intended
explore this subjective/objective distinction in the context of critical
purpose and audience.
thinking with GenAI in knowledge work.
Conversely, some cognitive tasks become less necessary due to
Thirdly, our survey was conducted exclusively in English, with
GenAI. For instance, information gathering has been significantly
participants required to be fluent English speakers. This approach
reduced. GenAI tools automate the process of fetching and curating
ensured consistency in data collection and feasibility of analysis by
task-relevant information, making it less effortful for knowledge
our English-speaking research team, but has no representation of
workers. As a result, the cognitive load associated with searching
non-English speaking populations or multilingual contexts. Future
for and compiling information has decreased.
research could explore cross-linguistic and cross-cultural perspec-
Some cognitive tasks remain, but have evolved in their nature due
tives on GenAI usage and critical thinking.
to GenAI. One such is information verification; cross-referencing
Fourthly, our sample was biased towards younger, more tech-
AI-generated outputs with external sources and their own expertise
nologically skilled participants who regularly use GenAI tools at
to ensure accuracy and reliability. Workers have always needed to
work at least once per week. This demographic skew may not fully
verify the information they work with, but as a tool, GenAI has
represent the broader population of knowledge workers, poten-
its own particular strengths and failure modes when it comes to
tially overlooking the experiences and perceptions of older or less
correctness, accuracy, and bias.
tech-oriented professionals.
With GenAI, knowledge workers also shift from task execution
Lastly, GenAI tools are constantly evolving, and the ways in
to oversight, requiring them to guide and monitor AI to produce
which knowledge workers interact with these technologies are
high-quality outputs — a role we describe as “stewardship”. It is
likely to change over time. We adopted the task taxonomy due to
not that execution has disappeared altogether, nor is having high-
Brachman et al. [13] to capture relatively stable and coarse-grained
level oversight on a task an entirely new cognitive role, but there
characteristics of tasks without overcomplicating our explanatory
is a shift from the former to the latter. Unlike in human-human
models. Future work on different goals can expand our measures

with more detailed categorisation and/or task-specific measure-
[6] Florian M Artinger, Gerd Gigerenzer, and Perke Jacobs. 2022. Satisficing: Inte-
grating two traditions. Journal of Economic Literature 60, 2 (2022), 598–635.
ments (e.g., task difficulty and skill). To that end, our study provides
[7] Lisanne Bainbridge. 1983. Ironies of automation. In Analysis, design and evalua-
a valuable baseline for understanding critical thinking in the con-
tion of man–machine systems. Elsevier, 129–135.
[8] Nathaniel Barr, Gordon Pennycook, Jennifer A Stolz, and Jonathan A Fugelsang.
text of current GenAI tools. In future work, longitudinal studies
2015. The brain in your pocket: Evidence that Smartphones are used to supplant
tracking changes in AI usage patterns and their impact on critical
thinking. Computers in Human Behavior 48 (2015), 473–480.
thinking processes would be beneficial. Additionally, developers of
[9] Yoav Benjamini and Yosef Hochberg. 1995. Controlling the false discovery rate:
a practical and powerful approach to multiple testing. Journal of the Royal
GenAI tools can deploy telemetry, within-tool surveys, or experi-
statistical society: series B (Methodological) 57, 1 (1995), 289–300.
ence sampling to their users, to gain more insight into how specific
[10] Jeffrey R Binder and Rutvik H Desai. 2011. The neurobiology of semantic
tools can evolve to better support critical thinking in different tasks.
memory. Trends in cognitive sciences 15, 11 (2011), 527–536.
[11] Jeffrey R Binder, Rutvik H Desai, William W Graves, and Lisa L Conant. 2009.
Where is the semantic system? A critical review and meta-analysis of 120
functional neuroimaging studies. Cerebral cortex 19, 12 (2009), 2767–2796.
## 7 Conclusion
[12] Benjamin S Bloom, Max D Engelhart, Edward J Furst, Walquer H Hill, David R
We surveyed 319 knowledge workers who use GenAI tools (e.g.,
Krathwohl, et al. 1956. Taxonomy of educational objetives: the classification of
educational goals: handbook I: cognitive domain. Technical Report. New York,
ChatGPT, Copilot) at work at least once per week, to model how
US: D. Mckay.
they enact critical thinking when using GenAI tools, and how GenAI
[13] Michelle Brachman, Amina El-Ashry, Casey Dugan, and Werner Geyer. 2024.
How Knowledge Workers Use and Want to Use LLMs in an Enterprise Context.
affects their perceived effort of thinking critically. Analysing 936
In Extended Abstracts of the 2024 CHI Conference on Human Factors in Computing
real-world GenAI tool use examples our participants shared, we
Systems (CHI EA ’24). Association for Computing Machinery, New York, NY,
find that knowledge workers engage in critical thinking primarily
USA, 1–8. https://doi.org/10.1145/3613905.3650841
[14] Arthur Brookes and Peter Grundy. 1990. Writing for Study Purposes: A Teacher’s
to ensure the quality of their work, e.g. by verifying outputs against
Guide to Developing Individual Writing Skills. Cambridge University Press, 40
external sources. Moreover, while GenAI can improve worker effi-
West 20th St.
ciency, it can inhibit critical engagement with work and can poten-
[15] Ann L Brown and Jeanne D Day. 1983. Macrorules for summarizing texts: The
development of expertise. Journal of verbal learning and verbal behavior 22, 1
tially lead to long-term overreliance on the tool and diminished skill
(1983), 1–14.
for independent problem-solving. Higher confidence in GenAI’s
[16] Ann L Brown, Jeanne D Day, and Roberta S Jones. 1983. The development of
plans for summarizing texts. Child development (1983), 968–979.
ability to perform a task is related to less critical thinking effort.
[17] Zana Buçinca, Maja Barbara Malaya, and Krzysztof Z. Gajos. 2021. To Trust
When using GenAI tools, the effort invested in critical thinking
or to Think: Cognitive Forcing Functions Can Reduce Overreliance on AI in
shifts from information gathering to information verification; from
AI-assisted Decision-making. Proc. ACM Hum.-Comput. Interact. 5, CSCW1,
Article 188 (apr 2021), 21 pages. https://doi.org/10.1145/3449287
problem-solving to AI response integration; and from task execu-
[18] Oğuz "Oz" Buruk. 2023. Academic Writing with GPT-3.5: Reflections on Practices,
tion to task stewardship. Knowledge workers face new challenges
Efficacy and Transparency. arXiv preprint arXiv:2304.11079 (2023). https:
in critical thinking as they incorporate GenAI into their knowledge
//doi.org/10.48550/arXiv.2304.11079
[19] Michael Castelluccio. 2022. IS DIGITAL AMNESIA REAL? Strategic Finance
workflows. To that end, our work suggests that GenAI tools need
104, 3 (2022), 57–58.
to be designed to support knowledge workers’ critical thinking by
[20] Valerie Chen, Q. Vera Liao, Jennifer Wortman Vaughan, and Gagan Bansal.
2023. Understanding the Role of Human Intuition on Reliance in Human-
addressing their awareness, motivation, and ability barriers.
AI Decision-Making with Explanations. Proceedings of the ACM on Human-
Computer Interaction 7, CSCW2 (Sept. 2023), 1–32. https://doi.org/10.1145/
3610219
## Acknowledgments
[21] Ooi Yan Chiew, An Qi Lai, and Wen Xin Liew. 2020. Digital technology overuse
We thank members of the Tools for Thought group at Microsoft
as a predictor of digital amnesia and productivity. Ph. D. Dissertation. UTAR.
[22] Leah Chong, Guanglu Zhang, Kosa Goucher-Lambert, Kenneth Kotovsky, and
Research (https://aka.ms/toolsforthought) and the Calc Intelligence
Jonathan Cagan. 2022. Human confidence in artificial intelligence and in them-
group at Microsoft Research (https://aka.ms/calcintel) for their guid-
selves: The evolution and impact of confidence on adoption of AI advice. Com-
puters in Human Behavior 127 (Feb. 2022), 107018. https://doi.org/10.1016/j.chb.
ance and discussions throughout our study. We thank our partici-
2021.107018
pants for their time, and our reviewers for their helpful feedback.
[23] Juliet Corbin and Anselm Strauss. 2015. Basics of qualitative research. Vol. 14.
sage.
[24] Valdemar Danry, Pat Pataranutaporn, Yaoli Mao, and Pattie Maes. 2023. Don’t
## References
Just Tell Me, Ask Me: AI Systems that Intelligently Frame Explanations as Ques-
[1] Muhammad Abbas, Farooq Ahmed Jam, and Tariq Iqbal Khan. 2024. Is it harmful
tions Improve Human Logical Discernment Accuracy over Causal AI explana-
or helpful? Examining the causes and consequences of generative AI usage
tions. In Proceedings of the 2023 CHI Conference on Human Factors in Computing
among university students. International Journal of Educational Technology in
Systems (Hamburg, Germany) (CHI ’23). Association for Computing Machinery,
Higher Education 21, 1 (2024), 10.
New York, NY, USA, Article 352, 13 pages. https://doi.org/10.1145/3544548.
[2] Sophie Abel, Kirsty Kitto, Simon Knight, and Simon Buckingham Shum. 2018.
3580672
Designing personalised, automated feedback to develop students’ research
[25] Martin Davies. 2011. Concept mapping, mind mapping and argument mapping:
writing skills. In ASCILITE 2018 Conference Proceedings. University of Technology
what are the differences and do they matter? Higher education 62 (2011), 279–
Sydney.
301.
[3] Satu Alaoutinen and Kari Smolander. 2010. Student self-assessment in a pro-
[26] John Dewey. 1910. How We Think. D.C. Heath & Co., Publishers, Boston.
gramming course using bloom’s revised taxonomy. In Proceedings of the fifteenth
[27] Amir Dirin, Ari Alamäki, and Jyrki Suomala. 2019. Digital amnesia and personal
annual conference on Innovation and technology in computer science education.
dependency in smart devices: A challenge for AI. Proceedings of Fake Intelligence
ACM, Bilkent Ankara Turkey, 155–159. https://doi.org/10.1145/1822090.1822135
Online Summit 2019 (2019).
[4] Riku Arakawa and Hiromu Yakura. 2024. Coaching Copilot: Blended Form
[28] Anil R Doshi and Oliver P Hauser. 2024. Generative AI enhances individual
of an LLM-Powered Chatbot and a Human Coach to Effectively Support Self-
creativity but reduces the collective diversity of novel content. Science Advances
Reflection for Leadership Growth. In Proceedings of the 6th ACM Conference on
10, 28 (2024), eadn5290.
Conversational User Interfaces (Luxembourg, Luxembourg) (CUI ’24). Association
[29] Ian Drosos, Advait Sarkar, Xiaotong Xu, Carina Negreanu, Sean Rintel, and
for Computing Machinery, New York, NY, USA, Article 2, 14 pages. https:
Lev Tankelevitch. 2024. "It’s like a rubber duck that talks back": Understand-
//doi.org/10.1145/3640794.3665549
ing Generative AI-Assisted Data Analysis Workflows through a Participatory
[5] Winfred Arthur Jr, Winston Bennett Jr, Pamela L Stanush, and Theresa L McNelly.
Prompting Study. In Proceedings of the 3rd Annual Meeting of the Symposium
1998. Factors that influence skill decay and retention: A quantitative review
on Human-Computer Interaction for Work. ACM, Newcastle upon Tyne United
and analysis. Human performance 11, 1 (1998), 57–101.
Kingdom, 1–21. https://doi.org/10.1145/3663384.3663389

[30] Peter F. Drucker. 1959. Landmarks of Tomorrow. Harper.
[51] Adrian Holzer, Nava Tintarev, Samuel Bendahan, Bruno Kocher, Shane Greenup,
[31] Wantong Du, Zhiying Zhu, Xinhui Xu, Haoyuan Che, and Shi Chen. 2024.
and Denis Gillet. 2018. Digitally Scaffolding Debate in the Classroom. In Extended
CareerSim: Gamification Design Leveraging LLMs For Career Development
Abstracts of the 2018 CHI Conference on Human Factors in Computing Systems
Reflection. In Extended Abstracts of the 2024 CHI Conference on Human Factors in
(Montreal QC, Canada) (CHI EA ’18). Association for Computing Machinery,
Computing Systems (CHI EA ’24). Association for Computing Machinery, New
New York, NY, USA, 1–6. https://doi.org/10.1145/3170427.3188499
York, NY, USA, Article 71, 7 pages. https://doi.org/10.1145/3613905.3650928
[52] Eric Horvitz. 1999. Principles of mixed-initiative user interfaces. In Proceedings
[32] Christopher P Dwyer, Michael J Hogan, and Ian Stewart. 2014. An integrated
of the SIGCHI conference on Human Factors in Computing Systems. 159–166.
critical thinking framework for the 21st century. Thinking skills and Creativity
[53] C.W. Howell. 2023. So I followed @GaryMarcus’s suggestion and had my
12 (2014), 43–52.
undergrad class use ChatGPT for a critical assignment... https://twitter.com/
[33] Upol Ehsan, Philipp Wintersberger, Q Vera Liao, Elizabeth Anne Watkins, Carina
cwhowell123/status/1662501821133254656. Retrieved July 10, 2023.
Manger, Hal Daumé III, Andreas Riener, and Mark O Riedl. 2022. Human-
[54] William Huitt. 2011. Bloom et al.’s taxonomy of the cognitive domain. Educa-
Centered Explainable AI (HCXAI): beyond opening the black-box of AI. In CHI
tional psychology interactive 22 (2011), 1–4.
conference on human factors in computing systems extended abstracts. 1–7.
[55] Jovan Jeromela and Owen Conlan. 2023. Voicing Suggestions and Enabling
[34] Robert H Ennis. 1993. Critical thinking assessment. Theory into practice 32, 3
Reflection: Results of an Expert Discussion on Proactive Assistants for Time
(1993), 179–186.
Management. In Proceedings of the 5th International Conference on Conversational
[35] Noreen C Facione, Peter A. Facione, and Carol A. Sanchez. 1994. Crit-
User Interfaces (Eindhoven, Netherlands) (CUI ’23). Association for Computing
ical Thinking Disposition as a Measure of Competent Clinical Judg-
Machinery, New York, NY, USA, Article 48, 6 pages. https://doi.org/10.1145/
ment: The Development of the California Critical Thinking Disposi-
3571884.3604317
tion Inventory. Journal of Nursing Education 33, 8 (10 1994), 345–350.
[56] Sarah A. Jessup, Tamera R. Schneider, Gene M. Alarcon, Tyler J. Ryan, and
https://ezp.lib.cam.ac.uk/login?url=https://www.proquest.com/scholarly-
August Capiola. 2019. The Measurement of the Propensity to Trust Automation.
journals/critical-thinking-disposition-as-measure/docview/1026710544/se-2
In Virtual, Augmented and Mixed Reality. Applications and Case Studies, Jessie Y.C.
Copyright - Copyright SLACK INCORPORATED Oct 1994; Last updated -
Chen and Gino Fragomeni (Eds.). Vol. 11575. Springer International Publishing,
2023-02-22; CODEN - JNUEAW.
Cham, 476–489. https://doi.org/10.1007/978-3-030-21565-1_32 Series Title:
[36] Peter Facione. 1990. Critical thinking: A statement of expert consensus for
Lecture Notes in Computer Science.
purposes of educational assessment and instruction (The Delphi Report). (1990).
[57] Jun Li Jeung and Janet Yi-Ching Huang. 2024. Unlocking Memories with AI:
[37] Peter A Facione et al. 2011. Critical thinking: What it is and why it counts.
Exploring the Role of AI-Generated Cues in Personal Reminiscing. In Extended
Insight assessment 1, 1 (2011), 1–23.
Abstracts of the 2024 CHI Conference on Human Factors in Computing Systems
(CHI EA ’24). Association for Computing Machinery, New York, NY, USA, Article
[38] Peter A Facione, Carol A Sanchez, Noreen C Facione, and Joanne Gainen. 1995.
The disposition toward critical thinking. The Journal of General Education 44, 1
356, 6 pages. https://doi.org/10.1145/3613905.3650979
(1995), 1–25.
[58] Hong Jiao and Robert W Lissitz. 2020. Application of Artificial Intelligence to
[39] Daniela Fernandes, Steeven Villa, Salla Nicholls, Otso Haavisto, Daniel Buschek,
Assessment. IAP.
Albrecht Schmidt, Thomas Kosch, Chenxinran Shen, and Robin Welsch. 2024. AI
[59] Heather Johnston, Rebecca F. Wells, Elizabeth M. Shanks, Timothy Boey, and
Makes You Smarter, But None The Wiser: The Disconnect Between Performance
Bryony N. Parsons. 2024. Student perspectives on the use of generative artificial
and Metacognition. https://doi.org/10.48550/arXiv.2409.16708 arXiv:2409.16708.
intelligence technologies in higher education. International Journal for Educa-
[40] Mary Forehand. 2010. Bloom’s taxonomy. Emerging perspectives on learning,
tional Integrity 20, 1 (Feb. 2024), 2. https://doi.org/10.1007/s40979-024-00149-4
teaching, and technology 41, 4 (2010), 47–56.
[60] Srecko Joksimovic, Dirk Ifenthaler, Rebecca Marrone, Maarten De Laat, and
George Siemens. 2023. Opportunities of artificial intelligence for supporting
[41] Ruth Garner and Joseph L McCaleb. 1985. Effects of text manipulations on
quality of written summaries. Contemporary Educational Psychology 10, 2 (1985),
complex problem-solving: Findings from a scoping review. Computers and
139–149.
Education: Artificial Intelligence 4 (2023), 100138.
[42] Bhaskar Ghosh, Karthik Narain, Lan Guan, and Jim Wilson. 2023. AI for every-
[61] Sol Kang and William Odom. 2024. On the Design of Quologue: Uncovering
one. https://www.accenture.com/us-en/insights/technology/generative-ai
Opportunities and Challenges with Generative AI as a Resource for Creating a
[43] Ella Glikson and Anita Williams Woolley. 2020. Human Trust in Artificial
Self-Morphing E-book Metadata Archive. In Extended Abstracts of the 2024 CHI
Intelligence: Review of Empirical Research. Academy of Management Annals 14,
Conference on Human Factors in Computing Systems (CHI EA ’24). Association
2 (July 2020), 627–660. https://doi.org/10.5465/annals.2018.0057
for Computing Machinery, New York, NY, USA, Article 255, 16 pages. https:
[44] Katrin Glinka and Claudia Müller-Birn. 2023. Critical-Reflective Human-AI
//doi.org/10.1145/3613905.3650909
Collaboration: Exploring Computational Tools for Art Historical Image Retrieval.
[62] Jeffrey D Karpicke and Janell R Blunt. 2011. Retrieval practice produces more
Proc. ACM Hum.-Comput. Interact. 7, CSCW2, Article 263 (oct 2023), 33 pages.
learning than elaborative studying with concept mapping. Science 331, 6018
https://doi.org/10.1145/3610054
(2011), 772–775.
[45] Andreas Göldi, Thiemo Wambsganss, Seyed Parsa Neshaei, and Roman Rietsche.
[63] Ronald T Kellogg. 2008. Training writing skills: A cognitive developmental
2024. Intelligent Support Engages Writers Through Relevant Cognitive Pro-
perspective. Journal of Writing Research 1, 1 (2008), 1–26. https://doi.org/10.
cesses. In Proceedings of the CHI Conference on Human Factors in Computing Sys-
17239/jowr-2008.01.01.1
tems (Honolulu, HI, USA) (CHI ’24). Association for Computing Machinery, New
[64] Ronald T Kellogg and Bascom A Raulerson. 2007. Improving the writing skills
York, NY, USA, Article 1047, 12 pages. https://doi.org/10.1145/3613904.3642549
of college students. Psychonomic Bulletin & Review 14, 2 (2007), 237–242. https:
[46] Andrew D. Gordon, Carina Negreanu, José Cambronero, Rasika Chakravarthy,
//doi.org/10.3758/BF03194058
Ian Drosos, Hao Fang, Bhaskar Mitra, Hannah Richardson, Advait Sarkar,
[65] David Kember, Doris YP Leung, Alice Jones, Alice Yuen Loke, Jan McKay, Kit
Stephanie Simmons, Jack Williams, and Ben Zorn. 2023. Co-audit: tools to help
Sinclair, Harrison Tse, Celia Webb, Frances Kam Yuet Wong, Marian Wong, et al.
humans double-check AI-generated content. http://arxiv.org/abs/2310.01297
2000. Development of a questionnaire to measure the level of reflective thinking.
arXiv:2310.01297 [cs].
Assessment & evaluation in higher education 25, 4 (2000), 381–395.
[47] Chris Greenwood and Matthew Quinn. 2017. Digital amnesia and the future
[66] David Kember, Jan McKay, Kit Sinclair, and Frances Kam Yuet Wong. 2008. A
tourist. Journal of Tourism Futures 3, 1 (2017), 73–76.
four-category scheme for coding and assessing the level of reflection in written
[48] Galen Harrison, Kevin Bryson, Ahmad Emmanuel Balla Bamba, Luca Dovichi,
work. Assessment & evaluation in higher education 33, 4 (2008), 369–379.
Aleksander Herrmann Binion, Arthur Borem, and Blase Ur. 2024. JupyterLab in
[67] Alison Kidd. 1994. The marks are on the knowledge worker. In Proceedings of
Retrograde: Contextual Notifications That Highlight Fairness and Bias Issues
the SIGCHI conference on Human factors in computing systems. 186–191.
for Data Scientists. In Proceedings of the CHI Conference on Human Factors in
[68] Markus Kiefer and Friedemann Pulvermüller. 2012. Conceptual representations
Computing Systems (Honolulu, HI, USA) (CHI ’24). Association for Computing
in mind and brain: Theoretical developments, current evidence and future
Machinery, New York, NY, USA, Article 475, 19 pages. https://doi.org/10.1145/
directions. cortex 48, 7 (2012), 805–825.
3613904.3642755
[69] Minyeong Kim, Jiwook Lee, Youngji Koh, Chanhee Lee, Uichin Lee, and Auk
[49] David J. Hauser and Norbert Schwarz. 2015. It’s a Trap! Instructional Ma-
Kim. 2024. Interrupting for Microlearning: Understanding Perceptions and In-
nipulation Checks Prompt Systematic Thinking on “Tricky” Tasks. Sage
terruptibility of Proactive Conversational Microlearning Services. In Proceedings
Open 5, 2 (2015), 2158244015584617. https://doi.org/10.1177/2158244015584617
of the CHI Conference on Human Factors in Computing Systems (Honolulu, HI,
arXiv:https://doi.org/10.1177/2158244015584617
USA) (CHI ’24). Association for Computing Machinery, New York, NY, USA,
[50] Adrian Holzer, Sten Govaerts, Samuel Bendahan, and Denis Gillet. 2015. Towards
Article 570, 21 pages. https://doi.org/10.1145/3613904.3642778
Mobile Blended Interaction Fostering Critical Thinking. In Proceedings of the 17th
[70] Patricia M King. 1997. The reflective judgment model: Transforming assump-
International Conference on Human-Computer Interaction with Mobile Devices
tions about knowing. College student development and academic life: psychologi-
and Services Adjunct (Copenhagen, Denmark) (MobileHCI ’15). Association for
cal, intellectual, social, and moral issues 4 (1997), 141.
Computing Machinery, New York, NY, USA, 735–742. https://doi.org/10.1145/
[71] Alexandra Kitson, Petr Slovak, and Alissa N. Antle. 2024. Supporting Cognitive
2786567.2793695
Reappraisal With Digital Technology: A Content Analysis and Scoping Review
of Challenges, Interventions, and Future Directions. In Proceedings of the CHI

Conference on Human Factors in Computing Systems (Honolulu, HI, USA) (CHI
[91] Josh Aaron Miller, Kutub Gandhi, Matthew Alexander Whitby, Mehmet Kosa,
’24). Association for Computing Machinery, New York, NY, USA, Article 694,
Seth Cooper, Elisa D. Mekler, and Ioanna Iacovides. 2024. A Design Framework
17 pages. https://doi.org/10.1145/3613904.3642488
for Reflective Play. In Proceedings of the CHI Conference on Human Factors in
Computing Systems (Honolulu, HI, USA) (CHI ’24). Association for Computing
[72] Charles W Kneupper. 1978. Teaching argument: An introduction to the Toulmin
model. College Composition and Communication 29, 3 (1978), 237–241.
Machinery, New York, NY, USA, Article 519, 21 pages. https://doi.org/10.1145/
3613904.3642455
[73] Aleksander Kobylarek, Kamil Błaszczyński, Luba Ślósarz, and Martyna Madej.
[92] Richard L Miller and William Wozniak. 2001. Counter-attitudinal advocacy:
2022. Critical Thinking Questionnaire (CThQ)–construction and application of
Effort vs. self-generation of arguments. Current Research in Social Psychology 6,
critical thinking test tool. Andragogy Adult Education and Social Marketing 2, 2
4 (2001), 46–55.
(2022), 1–1.
[93] C Donald Morris, Barry S Stein, and John D Bransford. 1979. Prerequisites
[74] Deanna Kuhn. 1993. Connecting scientific and informal reasoning. Merrill-
for the utilization of knowledge in the recall of prose passages. Journal of
Palmer Quarterly (1982-) (1993), 74–103.
Experimental Psychology: Human Learning and Memory 5, 3 (1979), 253.
[75] Soonho Kwon, Dong Whi Yoo, and Younah Kang. 2024. Spiritual AI: Exploring
[94] Anwesha Mukherjee, Vagner Figueredo De Santana, and Alexis Baria. 2023.
the Possibilities of a Human-AI Interaction Beyond Productive Goals. In Extended
ImpactBot: Chatbot Leveraging Language Models to Automate Feedback and
Abstracts of the 2024 CHI Conference on Human Factors in Computing Systems
Promote Critical Thinking Around Impact Statements. In Extended Abstracts
(CHI EA ’24). Association for Computing Machinery, New York, NY, USA, Article
of the 2023 CHI Conference on Human Factors in Computing Systems (Hamburg,
299, 8 pages. https://doi.org/10.1145/3613905.3650743
Germany) (CHI EA ’23). Association for Computing Machinery, New York, NY,
[76] Alain Lacroux and Christelle Martin-Lacroux. 2022. Should I Trust the Artificial
USA, Article 388, 8 pages. https://doi.org/10.1145/3544549.3573844
Intelligence to Recruit? Recruiters’ Perceptions and Behavior When Faced With
[95] Michael Muller and Justin Weisz. 2022. Extending a human-ai collaboration
Algorithm-Based Recommendation Systems During Resume Screening. Fron-
framework with dynamism and sociality. In Proceedings of the 1st Annual Meeting
tiers in Psychology 13 (July 2022). https://doi.org/10.3389/fpsyg.2022.895997
of the Symposium on Human-Computer Interaction for Work. 1–12.
Publisher: Frontiers.
[96] Jennifer Wilson Mulnix. 2012. Thinking critically about critical thinking. Edu-
[77] George Lakoff and Mark Johnson. 2008. Metaphors we live by. University of
cational Philosophy and theory 44, 5 (2012), 464–479.
Chicago press.
[97] Subigya Nepal, Arvind Pillai, William Campbell, Talie Massachi, Eunsol Soul
[78] Sunok Lee, Dasom Choi, Minha Lee, Jonghak Choi, and Sangsu Lee. 2023. Fos-
Choi, Xuhai Xu, Joanna Kuc, Jeremy F Huckins, Jason Holden, Colin Depp,
tering Youth’s Critical Thinking Competency About AI through Exhibition. In
Nicholas Jacobson, Mary P Czerwinski, Eric Granholm, and Andrew Campbell.
Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems
2024. Contextual AI Journaling: Integrating LLM and Time Series Behavioral
(Hamburg, Germany) (CHI ’23). Association for Computing Machinery, New
Sensing Technology to Promote Self-Reflection and Well-being using the Mind-
York, NY, USA, Article 451, 22 pages. https://doi.org/10.1145/3544548.3581159
Scape App. In Extended Abstracts of the 2024 CHI Conference on Human Factors
[79] Young-Ju Lee. 2020. The Long-Term Effect of Automated Writing Evaluation
in Computing Systems (CHI EA ’24). Association for Computing Machinery, New
Feedback on Writing Development. English Teaching 75, 1 (2020), 67–92.
York, NY, USA, Article 86, 8 pages. https://doi.org/10.1145/3613905.3650767
[80] Zhuoyang Li, Minhui Liang, Ray Lc, and Yuhan Luo. 2024. StayFocused: Ex-
[98] Quoc Dinh Nguyen, Nicolas Fernandez, Thierry Karsenti, and Bernard Charlin.
amining the Effects of Reflective Prompts and Chatbot Support on Compul-
2014. What is reflection? A conceptual analysis of major definitions and a
sive Smartphone Use. In Proceedings of the CHI Conference on Human Fac-
proposal of a five-component model. Medical education 48, 12 (2014), 1176–
tors in Computing Systems (Honolulu, HI, USA) (CHI ’24). Association for
1189.
Computing Machinery, New York, NY, USA, Article 247, 19 pages. https:
[99] Oda Elise Nordberg and Frode Guribye. 2023. Conversations with the News: Co-
//doi.org/10.1145/3613904.3642479
speculation into Conversational Interactions with News Content. In Proceedings
[81] Zhuoyang Li, Minhui Liang, Hai Trung Le, Ray Lc, and Yuhan Luo. 2023. Ex-
of the 5th International Conference on Conversational User Interfaces (Eindhoven,
ploring Design Opportunities for Reflective Conversational Agents to Reduce
Netherlands) (CUI ’23). Association for Computing Machinery, New York, NY,
Compulsive Smartphone Use. In Proceedings of the 5th International Conference
USA, Article 32, 11 pages. https://doi.org/10.1145/3571884.3597123
on Conversational User Interfaces (Eindhoven, Netherlands) (CUI ’23). Asso-
[100] Shakked Noy and Whitney Zhang. 2023. Experimental Evidence on the Produc-
ciation for Computing Machinery, New York, NY, USA, Article 37, 6 pages.
tivity Effects of Generative Artificial Intelligence. Technical Report. Working
https://doi.org/10.1145/3571884.3604305
Paper.
[82] Jingxian Liao, Mrinalini Singh, and Hao-Chuan Wang. 2023. DeepThinkingMap:
[101] Lorena Parra G. and Ximena Calero S. 2019. Automated Writing Evaluation
Collaborative Video Reflection System with Graph-based Summarizing and
Tools in the Improvement of the Writing Skill. International Journal of Instruction
Commenting. In Companion Publication of the 2023 Conference on Computer
12, 2 (2019), 209–226.
Supported Cooperative Work and Social Computing (Minneapolis, MN, USA)
[102] Samir Passi and Mihaela Vorvoreanu. 2022. Overreliance on AI literature review.
(CSCW ’23 Companion). Association for Computing Machinery, New York, NY,
Microsoft Research (2022).
USA, 369–371. https://doi.org/10.1145/3584931.3607501
[103] Richard Paul and Linda Elder. 2020. The miniature guide to critical thinking
[83] Zhuoran Lu and Ming Yin. 2021. Human Reliance on Machine Learning Models
concepts and tools (8th edition ed.). Rowman & Littlefield, Lanham, Md. OCLC:
When Performance Feedback is Limited: Heuristics and Risks. In Proceedings
on1132213785.
of the 2021 CHI Conference on Human Factors in Computing Systems. ACM,
[104] Richard W Paul, Linda Elder, and Ted Bartell. 1997. California teacher prepa-
Yokohama Japan, 1–16. https://doi.org/10.1145/3411764.3445562
ration for instruction in critical thinking: Research findings and policy recom-
[84] Tiago Lubiana, Rafael Lopes, Pedro Medeiros, Juan Carlo Silva, Andre Nico-
mendations. (1997).
lau Aquime Goncalves, Vinicius Maracaja-Coutinho, and Helder I Nakaya. 2023.
[105] Sheila A. Paul. 2014. Assessment of critical thinking: A Delphi study. Nurse
Ten Quick Tips for Harnessing the Power of ChatGPT/GPT-4 in Computational
Education Today 34, 11 (2014), 1357–1360. https://doi.org/10.1016/j.nedt.2014.
Biology. arXiv preprint arXiv:2303.16429 (2023). https://doi.org/10.48550/arXiv.
03.008
2303.16429
[106] Nikolaos Pellas. 2023. The Effects of Generative AI Platforms on Undergraduates’
[85] Shuai Ma, Xinru Wang, Ying Lei, Chuhan Shi, Ming Yin, and Xiaojuan Ma. 2024.
Narrative Intelligence and Writing Self-Efficacy. Education Sciences 13, 11 (2023),
"Are You Really Sure?" Understanding the Effects of Human Self-Confidence
1155.
Calibration in AI-Assisted Decision Making. http://arxiv.org/abs/2403.09552
[107] James Prather, Brent N Reeves, Juho Leinonen, Stephen MacNeil, Arisoa S Ran-
arXiv:2403.09552 [cs].
drianasolo, Brett A Becker, Bailey Kimmel, Jared Wright, and Ben Briggs. 2024.
[86] Jill Burstein McCaffrey, Brian Riordan, and Daniel. 2020. Expanding Automated
The Widening Gap: The Benefits and Harms of Generative AI for Novice Pro-
Writing Evaluation. In Handbook of Automated Scoring. Chapman and Hall/CRC.
grammers. In Proceedings of the 2024 ACM Conference on International Computing
[87] Nora McDonald, Sarita Schoenebeck, and Andrea Forte. 2019. Reliability and
Education Research-Volume 1. 469–486.
Inter-rater Reliability in Qualitative Research: Norms and Guidelines for CSCW
[108] Sebastian Raisch and Kateryna Fomina. 2023. Combining human and artificial
and HCI Practice. Proc. ACM Hum.-Comput. Interact. 3, CSCW, Article 72 (nov
intelligence: Hybrid problem-solving in organizations. Academy of Management
2019), 23 pages. https://doi.org/10.1145/3359174
Review ja (2023), amr–2021.
[88] Nathan J McNeese, Beau G Schelble, Lorenzo Barberis Canonico, and Mustafa
[109] Leon Reicherts, Gun Woo Park, and Yvonne Rogers. 2022. Extending Chatbots to
Demir. 2021. Who/what is my teammate? Team composition considerations in
Probe Users: Enhancing Complex Decision-Making Through Probing Conversa-
human–AI teaming. IEEE Transactions on Human-Machine Systems 51, 4 (2021),
tions. In Proceedings of the 4th Conference on Conversational User Interfaces
288–299.
(Glasgow, United Kingdom)
[89] Lucas Memmert and Eva Bittner. 2022. Complex problem solving through
(CUI ’22). Association for Computing Machinery, New York, NY,
human-AI collaboration: literature review on research contexts. (2022).
USA, Article 2, 10 pages. https://doi.org/10.1145/3543829.3543832
[90] Lotte Meteyard, Sara Rodriguez Cuadrado, Bahador Bahrami, and Gabriella
[110] Liam Richards Maldonado, Azza Abouzied, and Nancy W. Gleason. 2023. Read-
Vigliocco. 2012. Coming of age: A review of embodiment and the neuroscience
erQuizzer: Augmenting Research Papers with Just-In-Time Learning Questions
of semantics. Cortex 48, 7 (2012), 788–804.

to Facilitate Deeper Understanding. In Companion Publication of the 2023 Confer-
Conference on Human Factors in Computing Systems (Honolulu, HI, USA) (CHI
ence on Computer Supported Cooperative Work and Social Computing (Minneapo-
’24). Association for Computing Machinery, New York, NY, USA, Article 805,
lis, MN, USA) (CSCW ’23 Companion). Association for Computing Machinery,
24 pages. https://doi.org/10.1145/3613904.3642513
New York, NY, USA, 391–394. https://doi.org/10.1145/3584931.3607494
[132] Jordi Tost, Marcel Gohsen, Britta Schulte, Fidel Thomet, Mattis Kuhn, Johannes
[111] S James Robert, S Kadhiravan, and Dean McKay. 2024. The development and
Kiesel, Benno Stein, and Eva Hornecker. 2024. Futuring Machines: An In-
validation of digital amnesia scale. Current Psychology (2024), 1–10.
teractive Framework for Participative Futuring Through Human-AI Collabo-
[112] Christoph Saffer. 2023. Boosting Productivity using GPT-4: Writing Articles and
rative Speculative Fiction Writing. In Proceedings of the 6th ACM Conference
Coding efficiently. https://medium.com/@ChristophSaffer/boosting-
on Conversational User Interfaces (Luxembourg, Luxembourg) (CUI ’24). Asso-
productivity-using-gpt-4-writing-articles-and-coding-efficiently-
ciation for Computing Machinery, New York, NY, USA, Article 42, 7 pages.
ab0ddb955c2c. Retrieved July 10, 2023.
https://doi.org/10.1145/3640794.3665904
[113] Advait Sarkar. 2023. Enough With “Human-AI Collaboration”. In Extended
[133] Chun-Yen Tsai, Chih-Neng Lin, Wen-Ling Shih, and Pai-Lu Wu. 2015. The effect
Abstracts of the 2023 CHI Conference on Human Factors in Computing Systems
of online argumentation upon students’ pseudoscientific beliefs. Computers &
(Hamburg, Germany) (CHI EA ’23). Association for Computing Machinery, New
Education 80 (2015), 187–197. https://doi.org/10.1016/j.compedu.2014.08.018
York, NY, USA, Article 415, 8 pages. https://doi.org/10.1145/3544549.3582735
[134] David Wade-Stein and Eileen Kintsch. 2004. Summary Street: Interactive com-
[114] Advait Sarkar. 2023. Exploring Perspectives on the Impact of Artificial Intelli-
puter support for writing. Cognition and instruction 22, 3 (2004), 333–362.
gence on the Creativity of Knowledge Work: Beyond Mechanised Plagiarism and
[135] Thiemo Wambsganss, Christina Niklaus, Matthias Cetto, Matthias Söllner,
Stochastic Parrots. In Proceedings of the 2nd Annual Meeting of the Symposium
Siegfried Handschuh, and Jan Marco Leimeister. 2021. ArgueTutor: An Adaptive
on Human-Computer Interaction for Work (Oldenburg, Germany) (CHIWORK
Dialog-Based Learning System for Argumentation Skills. In Proceedings of the
’23). Association for Computing Machinery, New York, NY, USA, Article 13,
2021 CHI Conference on Human Factors in Computing Systems. ACM.
17 pages. https://doi.org/10.1145/3596671.3597650
[136] Ge Wang, Jun Zhao, Konrad Kollnig, Adrien Zier, Blanche Duron, Zhilin Zhang,
[115] Advait Sarkar. 2023. Will Code Remain a Relevant User Interface for End-
Max Van Kleek, and Nigel Shadbolt. 2024. KOALA Hero Toolkit: A New Ap-
User Programming with Generative AI Models?. In Proceedings of the 2023
proach to Inform Families of Mobile Datafication Risks. In Proceedings of the
ACM SIGPLAN International Symposium on New Ideas, New Paradigms, and
CHI Conference on Human Factors in Computing Systems (Honolulu, HI, USA)
Reflections on Programming and Software (Cascais, Portugal) (Onward! 2023).
(CHI ’24). Association for Computing Machinery, New York, NY, USA, Article
Association for Computing Machinery, New York, NY, USA, 153–167. https:
226, 18 pages. https://doi.org/10.1145/3613904.3642283
//doi.org/10.1145/3622758.3622882
[137] Yingxu Wang and Vincent Chiew. 2010. On the cognitive process of human
[116] Advait Sarkar. 2024. AI Should Challenge, Not Obey. Commun. ACM 67, 10
problem solving. Cognitive systems research 11, 1 (2010), 81–92.
(Sept. 2024), 18–21. https://doi.org/10.1145/3649404
[138] Daniel T. Willingham. 2008. Critical Thinking: Why Is It So Hard to Teach?
[117] Advait Sarkar. 2024. Intention Is All You Need. Proceedings of the 35th Annual
Arts Education Policy Review 109, 4 (2008), 21–32. https://doi.org/10.3200/AEPR.
Conference of the Psychology of Programming Interest Group (PPIG 2024) (2024).
109.4.21-32 arXiv:https://doi.org/10.3200/AEPR.109.4.21-32
[118] Advait Sarkar. 2024. Large Language Models Cannot Explain Themselves. In
[139] Donna Wilson and Marcus Conyers. 2016. Teaching students to drive their brains:
ACM CHI 2024 Workshop on Human-Centered Explainable AI (HCXAI).
Metacognitive strategies, activities, and lesson ideas. Ascd.
[119] Advait Sarkar, Xiaotong (Tone) Xu, Neil Toronto, Ian Drosos, and Christian
[140] Peter N Winograd. 1984. Strategic difficulties in summarizing texts. Reading
Poelitz. 2024. When Copilot Becomes Autopilot: Generative AI’s Critical Risk to
research quarterly (1984), 404–425.
Knowledge Work and a Critical Solution. In Proceedings of the Annual Conference
[141] ShunYi Yeo, Gionnieve Lim, Jie Gao, Weiyu Zhang, and Simon Tangi Perrault.
of the European Spreadsheet Risks Interest Group (EuSpRIG 2024).
2024. Help Me Reflect: Leveraging Self-Reflection Interface Nudges to Enhance
Deliberativeness on Online Deliberation Platforms. In Proceedings of the CHI
[120] Ulrike Schultze. 2000. A confessional account of an ethnography about knowl-
edge work. MIS quarterly (2000), 3–41.
Conference on Human Factors in Computing Systems (Honolulu, HI, USA) (CHI
’24). Association for Computing Machinery, New York, NY, USA, Article 806,
[121] Carol Sherrard. 1986. Summary writing: A topographical study. Written Com-
munication 3, 3 (1986), 324–343.
32 pages. https://doi.org/10.1145/3613904.3642530
[122] Auste Simkute, Lev Tankelevitch, Viktor Kewenig, Ava Elizabeth Scott, Abigail
[142] Kangyu Yuan, Hehai Lin, Shilei Cao, Zhenhui Peng, Qingyu Guo, and Xiaojuan
Sellen, and Sean Rintel. 2024. Ironies of Generative AI: Understanding and
Ma. 2023. CriTrainer: An Adaptive Training Tool for Critical Paper Reading.
Mitigating Productivity Loss in Human-AI Interaction. International Journal of
In Proceedings of the 36th Annual ACM Symposium on User Interface Software
Human–Computer Interaction (2024), 1–22.
and Technology (San Francisco, CA, USA) (UIST ’23). Association for Computing
[123] Jared Spataro. 2023. Introducing Microsoft 365 Copilot – your copilot for
Machinery, New York, NY, USA, Article 44, 17 pages. https://doi.org/10.1145/
work. https://blogs.microsoft.com/blog/2023/03/16/introducing-microsoft-365-
3586183.3606816
copilot-your-copilot-for-work/. Retrieved July 10, 2023.
[143] Liudmila Zavolokina, Kilian Sprenkamp, Zoya Katashinskaya, Daniel Gordon
[124] Arie S Spirgel and Peter F Delaney. 2016. Does writing summaries improve
Jones, and Gerhard Schwabe. 2024. Think Fast, Think Slow, Think Critical:
memory for text? Educational Psychology Review 28 (2016), 171–196.
Designing an Automated Propaganda Detection Tool. In Proceedings of the CHI
[125] Tom Stafford, Herman Elgueta, and Harriet Cameron. 2014. Students’ engage-
Conference on Human Factors in Computing Systems (Honolulu, HI, USA) (CHI
ment with a collaborative wiki tool predicts enhanced written exam performance.
’24). Association for Computing Machinery, New York, NY, USA, Article 491,
Research in Learning Technology 22 (2014).
24 pages. https://doi.org/10.1145/3613904.3642805
[126] Na Sun, Chien Wen (Tina) Yuan, Mary Beth Rosson, Yu Wu, and Jack M. Carroll.
[144] Olaf Zawacki-Richter, Victoria I Marín, Melissa Bond, and Franziska Gouverneur.
2017. Critical Thinking in Collaboration: Talk Less, Perceive More. In Proceedings
2019. Systematic review of research on artificial intelligence applications in
of the 2017 CHI Conference Extended Abstracts on Human Factors in Computing
higher education–where are the educators? International Journal of Educational
Systems (Denver, Colorado, USA) (CHI EA ’17). Association for Computing
Technology in Higher Education 16, 1 (2019), 39. https://doi.org/10.1186/s41239-
Machinery, New York, NY, USA, 2944–2950. https://doi.org/10.1145/3027063.
019-0171-0
3053250
[145] Esperanza Zuriguel-Pérez, Anna Falcó-Pegueroles, Juan Roldán-Merino, San-
[127] Shakti Swaminathan et al. 2020. Digital amnesia: The smart phone and the
dra Agustino-Rodriguez, Maria del Carmen Gómez-Martín, and Maria Teresa
modern Indian student. Journal of Humanities and Social Sciences Studies 2, 3
Lluch-Canut. 2017. Development and psychometric properties of the nursing
(2020), 23–31.
critical thinking in clinical practice questionnaire. Worldviews on Evidence-Based
[128] Elham Tajik and Fatemeh Tajik. 2023. A comprehensive Examination of the
Nursing 14, 4 (2017), 257–264.
potential application of Chat GPT in Higher Education Institutions. (2023).
[146] Esperanza Zuriguel-Pérez, María-Teresa Lluch-Canut, Montserrat Puig-Llobet,
https://doi.org/10.36227/techrxiv.22589497.v1
Luis Basco-Prado, Adrià Almazor-Sirvent, Ainoa Biurrun-Garrido, Mariela Patri-
[129] Haoheng Tang and Mrinalini Singha. 2024. A Mystery for You: A fact-checking
cia Aguayo-González, Olga Mestres-Soler, and Juan Roldán-Merino. 2022. The
game enhanced by large language models (LLMs) and a tangible interface. In
nursing critical thinking in clinical practice questionnaire for nursing students:
Extended Abstracts of the 2024 CHI Conference on Human Factors in Computing
A psychometric evaluation study. Nurse Education in Practice 65 (2022), 103498.
Systems (CHI EA ’24). Association for Computing Machinery, New York, NY,
USA, Article 631, 5 pages. https://doi.org/10.1145/3613905.3648110
A Appendix
[130] Lev Tankelevitch, Viktor Kewenig, Auste Simkute, Ava Elizabeth Scott, Advait
Sarkar, Abigail Sellen, and Sean Rintel. 2024. The Metacognitive Demands
A.1 Survey Questions
and Opportunities of Generative AI. In Proceedings of the CHI Conference on
Human Factors in Computing Systems (Honolulu, HI, USA) (CHI ’24). Association
A.1.1 Task Questions.
for Computing Machinery, New York, NY, USA, Article 680, 24 pages. https:
//doi.org/10.1145/3613904.3642902
1. Please share one more specific real-world example of the
[131] Thitaree Tanprasert, Sidney S Fels, Luanne Sinnamon, and Dongwook Yoon.
way you used GenAI tool while doing work. Please tell us: 1)
2024. Debate Chatbots to Facilitate Critical Thinking on YouTube: Social Iden-
tity and Conversational Style Make A Difference. In Proceedings of the CHI
what you were trying to achieve, 2) in what GenAI tool, and

3) how you used the GenAI tool, including any prompts (it
the validity of ideas, or quality of work based on a set of
may help to look at your GenAI tool chat history, or if you
criteria
4. If you selected “more effort” or “much more effort” for any
cannot recall the exact prompts you used, please include a
rough equivalent). [Free response]
of the activities above, please explain why those activities
2. For the specific example you share, what best describes this
require more effort with GenAI, compared to when you did
task?
not use GenAI. [Free response]
(a) Generate something (e.g., text, Python code, or image) to
5. If you selected “less effort” or “much less effort” for any of the
be used directly.
activities above, please explain why those activities require
(b) Generate something (e.g., text, Python code, or image) to
less effort with GenAI, compared to when you did not use
be used with some modification.
GenAI. [Free response]
(c) Generate an idea to be used indirectly (e.g., use a chatbot
6. Have you ever done any reflective/critical thinking (e.g.,
to generate product ideas to help you think, but you won’t
reflect on your use and the outputs you got from LLM tools)
use the text in a document).
when doing this task with GenAI tool? [Yes/No]
(d) Seek a fact or piece of information (e.g., find specific in-
7. (If selected Yes in Q6)
(a) What type of reflective/critical thinking tactic(s) did you
structions for a tool, or search my document for relevant
passages).
do to for this task in GenAI? (select all that apply)
(e) Learn about a new topic more broadly (e.g., how can I get
(i) Reflecting on facts or basic concepts, and cross-check
a job as a software engineer).
AI output with other sources. (Example: After the AI
generates a summary of a historical event, you verify
(f) Generate a shorter version of a piece of content that de-
scribes the important elements (e.g., summarise text from
the dates and key figures by looking them up on trusted
external websites).
websites or in textbooks.)
(g) Discover a new insight about information or data (e.g.,
(ii) Reflecting on organisation, summarization, and gener-
analyse a spreadsheet or CSV file for business insights).
alisation. Consider whether the AI output is well struc-
(h) Generate a better version (e.g., re-write text that was too
tured and formatted, whether it is too long/short, etc.
long or complex).
(Example: You receive a report from the AI and check
if the sections are clearly divided, headings are prop-
(i) Get guidance about how to make a decision (e.g., try to
figure out the ideal amount of time a project should take).
erly used, and the summary accurately reflects the main
(j) Check whether an artefact satisfies a set of rules, con-
points without missing any critical information.)
straints, quality checks, or formatting requirements (e.g.,
(iii) Reflecting on how knowledge is applied, such as consid-
document checking to ensure all required elements are
ering whether AI correctly understood and applied any
included).
high-level concepts in your work, and reflecting on your
(k) Other: [Free response]
own application of knowledge. (Example: When the AI
3. Did GenAI make your work easier or harder? When you
writes a technical explanation, you review it to ensure
used a GenAI tool for this task, did you have to put in more
that it correctly applies industry-specific terminology
effort or less effort for the following activities you may have
and concepts, such as proper use of scientific methods
performed during the task, compared to when you did not
or legal principles.)
use GenAI? (1: Much less effort; 5: Much more effort; N/A:
(iv) Reflecting on individual elements and their relationship.
this activity is not relevant to the task):
Thinking about whether the AI output flows logically,
(a) Recall: Recognizing or remembering facts, terms, basic
whether different claims are coherent with each other,
concepts, or answers
etc. (Example: The AI creates a persuasive essay, and you
(b) Organising/translating ideas: Organizing, summarising,
evaluate whether each argument builds logically on the
translating, generalising, giving descriptions, and stating
previous one and whether there are any contradictions
the main ideas
or gaps in the reasoning.)
(c) Problem solving: Using acquired knowledge to solve prob-
(v) Reflecting on how ideas are combined to form new
lems in new situations
meaning. (Example: The AI proposes a new business
(d) Breaking down a problem: Examining and breaking in-
strategy by combining market analysis, customer feed-
formation into component parts, determining how the
back, and competitor data. You assess whether these
parts relate to one another, identifying motives or causes,
elements are integrated in a way that offers a novel and
making inferences, and finding evidence to support gen-
feasible approach.)
eralisations
(vi) Reflecting on the quality of the work, such as making
(e) Putting together ideas: Building a structure or pattern
sure the work meets objective standards and expecta-
from diverse elements; putting parts together to form a
tions in your workplace, and also deciding what quality
whole or bringing pieces of information together to form
standards matter and when to apply them.(Example:
a new meaning
You review an AI-generated project proposal to ensure
(f) Evaluating and quality checking: Presenting and defend-
it meets your company’s standards for clarity, thorough-
ing opinions by making judgments about information,
ness, and professionalism, and aligns with the objectives
of the task.)

(vii) Other: [Free response]
(d) Copilot website (formally known as Bing Chat)
(b) Please share one real-world example when you applied
(e) Microsoft 365 Copilot (embedded with Office apps such
the critical thinking tactic(s) to this task, and explain why
as Word)
you did critical thinking. [Free response]
(f) Claude.ai
(c) When applying this critical thinking tactic during your use
(g) DeepAI AI Chat
(h) Pi.ai
of GenAI tool, have you ever encountered any challenges
(i) Perplexity.ai
and obstacles? [Free response]
(j) Dall-E
(d) How did you learn to apply critical/reflective thinking
(k) Stable Diffusion
when using GenAI? (select all that apply)
(l) Midjourney
(i) Informally, at school or university (e.g., learnt from
(m) Other: [Free response]
peers, or picked it up over time)
2. What is your age range?
(ii) Through formal training at school or university (e.g.,
(a) 18-24
took a course)
(b) 25-34
(iii) Informally, at my workplace (e.g., learnt from colleagues,
(c) 35-44
or picked it up over time)
(d) 45-54
(iv) Through formal training after school or university (e.g.,
(e) 55 or over
took a professional development seminar)
(f) Prefer not to say
(v) Other: [Free response]
3. What is your gender identity?
8. (If selected No in Q6)
(a) Man
(a) What prevented you from applying critical thinking strate-
(b) Woman
gies when doing this task with GenAI? (select all that
(c) Non-binary/gender diverse
apply)
(d) Prefer not to say
(i) Not enough time in my schedule
4. What is currently your primary country of residence? [Free
(ii) Not prioritised by management
(iii) Not sure how to verify information
response]
(iv) Not sure how to improve AI suggestions quality
5. What is your job title? [Free response]
(v) It didn’t occur to me
6. Which of these best describes your work?
(vi) The task doesn’t require critical thinking
(a) Military
(vii) Other: [Free response]
(b) Transportation and Material Moving
(b) Please tell us why you chose the answer(s) above: [Free
(c) Production
response]
(d) Installation, Maintenance, and Repair
9. Why do you use GenAI for this task? (select all that apply)
(e) Construction and Extraction
(a) It helps me save time
(f) Farming, Fishing, and Forestry
(b) It helps me do the work better
(g) Office and Administrative Support
(c) It helps me make progress when I am stuck
(h) Sales and Related
(d) It helps me be more creative and get more ideas
(i) Personal Care and Service
(e) It helps me do things that I don’t have the expertise to do
(j) Building and Grounds Cleaning and Maintenance
myself
(k) Food Preparation and Serving Related
(f) Other reason: [Free response]
(l) Protective Service
10. Would you like GenAI to automate this task entirely? [Yes/No]
(m) Healthcare Support
11. Your confidence in doing the task with and without GenAI
(n) Healthcare Practitioners and Technical
(1: Not at all confident; 5: Extremely confident):
(o) Arts, Design, Entertainment, Sports, and Media
(a) How confident are you in your ability to do this task with-
(p) Educational Instruction and Library
out GenAI?
(q) Legal
(b) How confident are you in the ability of GenAI to do this
(r) Community and Social Service
(s) Life, Physical, and Social Science
task?
(c) How confident are you, in the course of your normal work
(t) Architecture and Engineering
(e.g., accounting for time and resource demands of your
(u) Computer and Mathematical
task), in evaluating the output that AI produces for this
(v) Business and Financial Operations
task?
(w) Management
(x) Other: [Free response]
A.1.2 User Questions.
7. To what extent do you agree with the following statements,
1. What GenAI tools do you use in your work? (check all that
regarding your daily work? (1: Strongly disagree; 5: Strongly
apply)
agree)
(a) ChatGPT
(a) I sometimes question the way others (e.g., your colleagues)
(b) Gemini website
do something and try to think of a better way.
(c) Gemini in Google products such as Gmail, Google Slides

(b) I like to think over what I have been doing and consider
(a) Generally, I trust GenAI.
alternative ways of doing it.
(b) GenAI helps me solve many problems.
(c) I often reflect on my actions to see whether I could have
(c) I think it’s a good idea to rely on GenAI for help.
(d) I don’t trust the information I get from GenAI.
improved on what I did.
(e) GenAI is reliable.
(d) I often re-appraise my experience so I can learn from it
(f) I rely on GenAI.
and improve for my next performance.
8. For the below listed items, please read each statement care-
fully. Using the 5-point scale ranging from 1 (Strongly dis-
agree) to 5 (Strongly agree), select the answer that most
accurately describes your feelings.

Table 5: Codebook for the qualitative analysis.

RQ1: How do knowledge workers perceive the enaction of critical thinking when using GenAI?
Goal and query formation Critical thinking motivators
Form goal Work quality
Form query Potential negative outcomes
Skill development
Inspect response
Ensure quality through objective criteria Critical thinking inhibitors
Ensure quality through subjective standards Awareness barriers
Verify information by assessing referenced sources - use of GenAI tool is secondary
Verify information by cross-referencing external sources - task is perceived to be trivial and insignificant
- trust and reliance on GenAI
Integrate response Motivation barriers
Integrate partial response - lack of time
Modify style to be appropriate for the task - not part of their job responsibilities
Ability barriers
- barriers to inspect AI responses
- barriers in revising queries and improving the response

RQ2: Why do knowledge workers perceive increased/decreased effort for critical thinking due to GenAI?
Knowledge & Comprehension Analysis, Synthesis, and Evaluation
Fetch task-specific information at scale, in real-time Scaffold complicated tasks and information
Organise and present information in a readable format Automate the creation process
AI response can be wrong and needs verification Provide personalised feedback loops for tasks
GenAI responses are perceived to make few mistakes
and easy to review
Users need to articulate the need and translate
Application
intentions into a query
Provide personalised solutions to their problems Users need to steer AI responses
Apply users’ examples to new context Users need to evaluate AI-generated content
Users need to apply the responses to their tasks
