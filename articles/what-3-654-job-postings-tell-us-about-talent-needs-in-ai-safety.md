---
title: "What 3,654 Job Postings Tell Us About Talent Needs in AI Safety"
author:
  - "Weronika Żurek"
source_url: "https://www.lesswrong.com/posts/tScvv7rQAi4spkTf5/what-3-654-job-postings-tell-us-about-talent-needs-in-ai"
published: 2026-04-15
created: 2026-11-28
accessed: 2026-11-28
llm-review:
  date: 2026-11-28
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-28
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[Crossposted from EA Forum](https://forum.effectivealtruism.org/posts/AAGD34wyWHXm5d2gp/what-3-654-job-postings-tell-us-about-talent-needs-in-ai)

## Summary ^summary

Based on the last 3 years of AI safety job board postings from 80,000 Hours, I checked what skillsets are the most sought after in the field, including positions at different types of organisations, and separately, leadership roles. Here are three of the most important findings:

1.  In leadership positions, a management skillset paired with an operations, strategy, or policy skillset is the most needed combination. Research and technical skills are not very important in this group. 
2.  Information security seems to be a very important skillset to have in AI labs
3.  Research skills are often needed in connection with other skillsets, such as management, information security, software engineering, or policy. 

You can find more conclusions at the end of the post.

I believe this analysis may help draw some important conclusions for two main groups: job-seekers and fieldbuilders, in particular those working on improving talent flows and attracting new talent to high-impact positions in AI safety.

## Introduction ^introduction

When I joined the Astra Fellowship as a Fieldbuilding Fellow in January, it seemed obvious to me that there must be a lot of knowledge in the field about what we need from AI safety talent pipelines. After all, there are a bunch of organisations working on attracting and training the most talented people to work in the field. There must be a whole lot of posts about the topic online, right? Right?

It quickly became clear that things are not actually that easy: the knowledge _exists,_ but it’s typically quite scattered and difficult to find. Important insights tend to be either not written down at all or hidden in unpublished documents, passed between fieldbuilders when they bump into each other at EAGs. Therefore, I decided to dig into the topic myself and check what knowledge I can bring to light. I decided to start from the most obvious source and look into postings from the 80,000 Hours job board. This post is based on an analysis of 3,654 postings in the AI safety and security field that were placed on the job board between 13th of March, 2023 and 9th of March, 2026. I focused on skillsets and combinations of skillsets needed in various types of organisations. Separately, I also checked what the needs are specifically for leadership positions.

_Special thanks to Conor Barnes from the 80,000 Hours team for sharing the data with me._ 

_I conducted most of the analysis myself. I used Claude’s help in designing the spreadsheet and matrices, finding some patterns in the data, and double-checking for mistakes. The content of the post was written entirely by me. Any mistakes made are my own._

## Skillsets ^skillsets

For each posting in the 80,000 Hours job board, one or a few skillset tags are assigned. I used them as a base for my estimations. Below is a full list of all tags from the board and how commonly they occurred in the postings:

| Skillset | n | share of all postings |
| --- | --- | --- |
| Research | 1571 | 43% |
| Policy | 890 | 24.4% |
| Software engineering | 758 | 20.7% |
| Operations¹ | 702 (or ∿ 554)¹ | 19.2% (or ∿15.2%) |
| Information security | 683 | 18.7% |
| Management | 512 | 14% |
| Strategy | 298 (after June 1, 2024)² | 12.2% (after June 1, 2024)² |
| Outreach | 253 | 6.9% |
| Data | 83 | 2.3% |
| Legal | 44 | 1.2% |
| Finance | 43 | 1.2% |
| Other | 176 | 4.8% |

_fig.1. Frequency of skillsets assigned to positions in the whole dataset_

_¹ Before mid-2024, the strategy skillset was included in the operations skillset. Therefore, the number of operations positions in the database is higher than it actually should be. Using the ratio of strategy to operations positions after mid-2024, Claude estimates that the true number of operations positions could be ∿ 554 (∿ 15.2%). However, this is a rough estimation that is not very reliable, e.g. because the actual ratio of these skillsets might have been very different in the past. In all the other tables in this post where the operations skillset comes up, I used the total number of positions to which this skillset was assigned._

² _Since the label for strategy skillset was only introduced in mid-2024, both the number 298 and the 12.2% refer to all positions posted after the 1st of June 2024. For the sake of transparency, there were also two positions with a strategy skillset assigned before that date._ 

_Note: the skillsets add up to way more than 100% because some positions had two or three skillsets assigned._

I also made a co-occurrence matrix to check which skillsets tend to be needed together in the same roles. The most common combinations include:

| Skillset combination | n | share of all postings |
| --- | --- | --- |
| Research + policy | 414 | 11.3% |
| Research + software engineering | 362 | 9.9% |
| Software engineering + information security | 231 | 6.3% |
| Research + information security | 192 | 5.3% |
| Operations + management | 153 | 4.2% |
| Research + management | 148 | 4% |
| Policy + management | 108 | 3% |
| Strategy + management | 104 | 2.9% |

_fig 2. The most common combinations of skillsets assigned to postings in the whole dataset_

Notably, in some cases, **skillset x tends to be required with skillset y, even if the total number of postings to which both are assigned is not very high** (e.g. both skillsets are quite rare). For example, among roles requiring a finance skillset, 62.8% (27 positions) also required an operations skillset. Among roles requiring a legal skillset, 61.4% (27 positions) also required a policy skillset, 56.8% (25 positions) required a research skillset, and 43.2% (19 positions) needed both. For positions that required a policy, software engineering, or data skillset, research skills were needed in almost 50% of the cases. 

## Skillset needs by type of organisation ^skillset-needs-by-type

The roles in my database were posted by 540 organisations, most of which I have never heard of. Since Claude turned out to be quite bad at classifying organisations by type (e.g. classified many private companies as NGOs), I decided not to rely on its judgement, and instead used simplified rules to decide which organisations to include in each category that I looked into. Many organisations, in particular small companies, were not included in any of the categories. 

### Academia ^academia

I classified all organisations with such words as “university”, “college”, and similar in their names as academia. 

This category included a total of 229 positions. 

| Skillset or combination | n | share of postings in academia |
| --- | --- | --- |
| Research | 196 | 85.6% |
| Policy | 51 | 22.3% |
| Information security | 45 | 19.7% |
| Research + policy | 46 | 20% |
| Research + information security | 32 | 14% |
| Research + software engineering | 23 | 10% |

_fig 3. The most common skillsets and combinations of skillsets in postings from academia_

### Public Institutions ^public-institutions

This category included all roles posted at governments or institutions with governments in their name (e.g., the UK Government’s Competition and Markets Authority), as well as other institutions that I am confident belong in the public sector (e.g. the European Commission). Most of these roles were based in the US and UK, but there were also a few in Singapore and Australia, as well as the EU and its member countries. 

A total of 386 positions were included in this category. Notably, 215 of these positions were at the UK AI Security Institute. 

| Skillset or combination | n | share of postings in public institutions |
| --- | --- | --- |
| Policy | 212 | 54.9% |
| Research | 186 | 48.2% |
| Software engineering | 91 | 23.6% |
| Research + policy | 66 | 17% |
| Research + software engineering | 60 | 15.5% |
| Policy + management | 46 | 11.9% |

 _fig 4. The most common skillsets and combinations of skillsets in postings from public institutions_

Due to a majority of the positions coming from one organisation, I decided to check the needs for the same skillsets in UK AISI separately, and they were slightly different to the whole category.

| Skillset or combination | n | share of postings in UK AISI |
| --- | --- | --- |
| Policy | 84 | 39.1% |
| Research | 117 | 54.4% |
| Software engineering | 71 | 33% |
| Research + software engineering | 45 | 20.9% |
| Research + policy | 27 | 12.6% |
| Research + management | 24 | 11.2% |

 _fig 5. The most common skillsets and combinations of skillsets  in UK AISI postings_

The bias seems to be particularly important in the case of software engineering. Only 11.7% of non-UK AISI positions in the category of public institutions (20 postings) required this skillset. For the software engineering and research combination, 45 out of 60 positions in the public institutions were at UK AISI.

### AI labs ^ai-labs

In this category, I included all positions at: Anthropic, OpenAI, Meta, Google (including but not limited to Google DeepMind\*), xAI, and DeepSeek. 

A total of 645 positions were included in this category, out of which 253 were at Anthropic.

| Skillset or combination | n | share of postings in labs |
| --- | --- | --- |
| Information security | 314 | 48.7% |
| Software engineering | 253 | 39.2% |
| Research | 239 | 37.1% |
| Information security + software engineering | 129 | 20% |
| Research + software engineering | 111 | 17.2% |
| Research + information security | 52 | 8% |

 _fig 6. The most common skillsets and combinations of skillsets in postings from AI labs_

Despite the huge share of Anthropic’s positions in this category, its needs do not significantly skew the numbers. Information security skillset was needed in 45.5% of Anthropic posts, software engineering in 41.5%, and research in 39.1%, so the numbers are quite similar to those in the whole category. 

As a side note here: such skillsets as **policy** (90 positions), **strategy** (54 positions), or **operations** (42 positions) were also needed in some high-impact positions at labs, although in lower numbers. 

_\*I decided to include positions at Google outside of Google DeepMind, since they all seemed to be directly relevant for AI safety or security. Some examples of these positions include AI Safety Data Scientist; Group Product Manager, AI Security; Senior Policy Specialist, AI Transparency._

### Non-governmental organisations ^non-governmental-organisations

I included 53 organisations and 440 positions in this category. Since the list of organisations was created by my and Claude’s judgment, there is a non-zero chance that some of the less-known NGOs were missed.

| Skillset or combination | n | share of postings in NGOs |
| --- | --- | --- |
| Research | 205 | 46.6% |
| Policy | 131 | 30% |
| Outreach | 92 | 21% |
| Research + policy | 76 | 17.3% |
| Research + software engineering | 43 | 9.8% |
| Management + operations | 30 | 6.8% |

_fig 7. The most common skillsets and combinations of skillsets in postings from NGOs_

## Leadership roles ^leadership-roles

I decided to do some additional analysis on leadership roles, since I believe they deserve special attention. In this category, I placed all positions that included words like “Chief”, “President”, “Vice-President”, “Head”, “Director”, “Founder”, “Co-Founder”, or “Board”, excluding assistant positions (e.g. Executive Assistant). 

The category included 349 roles in 142 organisations of all types.

| Skillset or combination | n | share of postings of leadership positions |
| --- | --- | --- |
| Management | 183 | 52.4% |
| Operations | 124 | 35.5% |
| Policy | 118 | 33.8% |
| Strategy | 95 | 27.2% |
| Management + operations | 73 | 20.9% |
| Management + strategy | 57 | 16% |
| Management + policy | 54 | 15.5% |

 _fig 8. The most common skillsets and combinations of skillsets in postings of leadership positions_

_Note: as mentioned in the footnote to fig. 1, older positions with the operations skillset might have actually required strategy skills. Therefore, the figures for operations and strategy in this table should be interpreted with caution. In particular, the actual need for operations skillset (and management + operations combination) might be lower than noted in the table, while the actual need for strategy skillset (and management + strategy combination) might be higher. Simply adding the operations and strategy numbers should not be used for estimations, since some positions posted after mid-2024 had both skillsets assigned simultaneously._ 

I expected that many leadership roles would require technical and/or research background, but these skills do not seem to be needed very commonly. Research skillset was only needed in 8.6% of the positions, information security in 6%, software engineering in 2.9%, and data in <1% of postings of leadership roles. However, I would not interpret that very strongly due to the methodology of the study: some knowledge of technical side of AI safety might be needed in many leadership positions. 

## Limitations ^limitations

There are several reasons to be careful in interpreting the numbers from this post. 

Starting from the most obvious problem, many positions are not posted on the 80,000 Hours job board. Some are filled in closed hiring rounds, without any public postings at all; others might be posted online but not in this specific job board. In particular, I expect that leadership and senior positions might be heavily underrepresented in the dataset.

The skillsets assigned to positions are only the most important ones. I expect that in many positions some skills from a given category are needed, even if the skillset is not assigned (e.g. for a leadership role in an NGO, some understanding of strategy is probably needed even if strategy is not the main skillset for this position).

I did not remove such postings as “expression of interest” from the database. I also acknowledge that some positions might be volunteering opportunities. However, I believe very few postings of both of these types were included in the database, and likely they did not have a significant impact on the results of my analysis. 

I rely on 80,000 Hours’ judgment about all posted positions having a high potential for impact. 

Finally, some roles might have been posted more than once despite hiring for one headcount, and others might have been posted one time for a few headcounts. While I am unable to check how common each of these cases is, I find it unlikely that they would have a significant impact on the numbers. 

## Conclusions and implications ^conclusions-and-implications

**For job seekers:**

1.  There is a clear demand for information security, operations and outreach skills in specific categories. These skills are not typically emphasised by AI safety career advisory and upskilling programs, and therefore developing them is likely a good investment of your time and effort
2.  Research is the most commonly needed skillset, and it is particularly important if you come from a legal, policy, data, or software engineering background.
3.  However, research skills are not required (or at least not mentioned among the most important skillsets) in a majority of positions at AI labs, where information security is needed more often. 
4.  Policy, legal, and research skills are deeply connected with each other. If you have two of them, learning the third is likely worth the effort. 
5.  If you want to work in finance, you will probably need an operations background as well. 
6.  The combination of management + operations, policy, or strategy background is particularly promising in leadership roles. On the other side, these roles rarely require a technical or research skillset

**For fieldbuilders:**

1.  The leadership roles need various, probably quite generalist backgrounds, and that’s what we should be aiming for when we try to attract new talent for them. Getting researchers to become leaders is likely not the way to go.
2.  Overall, there is a strong demand for people who combine two or more different skillsets, often from very different domains.
3.  Talents with strong outreach backgrounds will likely find employment in NGOs, but not in labs or public institutions. 
4.  Legal, finance and data skillsets are not in very high demand; we probably don’t need to attract people from these domains into the field
5.  Talents with management, information security, software engineering or policy backgrounds might be particularly promising candidates for research-oriented programs
6.  Given that current AI safety talent pipelines seem to be [overoptimised for researchers](https://forum.effectivealtruism.org/posts/m5dDrMfHjLtMu293G/ai-safety-s-talent-pipeline-is-over-optimised-for), we should probably engage more in training and/or attracting talents of other types, since there is a clear need for that. This also includes pointing to such skillsets as information security in career-related communications. 

If you want to learn more about the skillsets needed in a specific type of position, or what roles your skillset might be useful for, I am happy to look into that for you. Please do not hesitate to contact me at [weronikamzurek@gmail.com](mailto:weronikamzurek@gmail.com) or via private messages in EA Forum. Have a very low bar for reaching out.
