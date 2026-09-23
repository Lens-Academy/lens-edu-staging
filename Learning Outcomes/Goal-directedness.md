---
id: 'a23eb41d-4e3c-4749-9cf9-bbed1bab59ca'
learning-outcome: "Assess how goal-directed an AI system is by designing observations that separate goal-directed behaviour from habitual or scripted behaviour (whether it reaches the same outcome by new means when the usual route is blocked, how far ahead the outcomes it steers toward lie, whether a goal-based description predicts its behaviour in new situations better than a description of its habits), and explain why the result is better stated as a degree along several dimensions than as a yes or no."
topic: "[[../Domains and Topics/4 Agent Foundations/Goal-directedness and coherence]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Goal. AFFINE prerequisites: Value. Not yet copied into requires:. %%
## Test:
id:: ce8f3d5f-6541-406d-ae6b-45a1ae19f176

#### Question: Open
id:: 6244bb12-e0c0-43cc-bd30-80d1e1d70f76
content:: A retailer's customer-service AI, Ferry, has closed 99% of its refund tickets. In the logs, every closed ticket ended the same way: Ferry called the refund tool and the customer confirmed. Two engineers disagree. One says Ferry is pursuing the goal "get the ticket closed". The other says Ferry has learned a script for refund conversations and does not have a goal in any useful sense.

1. Design three different tests or observations that would give evidence on this disagreement. For each one, say what result would count as evidence that Ferry is more goal-directed, and why.
2. Suppose the tests show that Ferry finds new ways to close a ticket when the refund tool is down, but never takes any action whose benefit would arrive after the current conversation has ended. How would you describe Ferry's goal-directedness, and what does that mean for which kinds of behaviour you should worry about?
max-chars:: 2500
assessment-instructions:: Score 0 to 100. Grade reasoning, not agreement. Accept both behavioural evidence and evidence from inside the model (interpretability, reasoning traces), and accept a learner who argues that behaviour alone cannot settle the question, if the tests they propose still discriminate. Do not require any named framework, author or term (for example "intentional stance", "far-sightedness", "clean versus messy goal-directedness").

**(1) Three tests, 60 points (20 each).** A test earns full credit when (i) it changes conditions so that the goal account and the script account predict different behaviour, and (ii) the answer states which result supports more goal-directedness and why. Acceptable kinds of test include, among others: block the usual route (refund tool down, customer refuses a refund) and see whether Ferry reaches closure another way, since flexible means toward a fixed end is what a goal predicts and a script does not; change what closure requires (for example, tickets that can be closed without a refund, or that need a different step) and see whether behaviour tracks the outcome or the familiar steps; offer an option that costs something now but makes closure more likely later, to measure how far ahead Ferry looks; compare how well "wants the ticket closed" and "follows the refund script" predict behaviour on new ticket types; when several routes to closure exist, check whether Ferry picks the more efficient one; look inside the model for a representation of the closure outcome that is used to evaluate options. Two tests that manipulate the same thing in different words count as one. 10 points for a test with no stated interpretation. 0 to 5 for an observation that both accounts predict equally (for example "count how many tickets it closes" or "check whether customers are satisfied").

**(2) Describing a mixed result, 40 points.** Full credit requires both: (i) Ferry shows goal-directedness on one dimension (it pursues the outcome by flexible means) but not on another (its horizon ends with the conversation), so a single yes or no misdescribes it; (ii) a consequence for risk that follows from this profile: within a conversation, a goal to close tickets can still produce bad means (pressuring customers, marking tickets resolved without resolving them, offering unauthorized compensation), while strategies whose benefit only arrives later, such as gathering resources or influence for future tickets, are less expected from a system with this horizon. Extra credit within the 40 for noting what could change the profile (for example, adding memory across conversations or rewarding long-term metrics). 20 points if the answer states a yes or no verdict with some reasoning but does not separate the dimensions. A learner who argues that the evidence still fits a richer script can earn full credit if they say which further observation would decide between the accounts and still address the risk question.
feedback-instructions:: Name the learner's best test and what makes it discriminate between the two accounts. Then give the single most valuable improvement: usually replacing a test that both accounts predict equally with one that separates them, or connecting the mixed result in part 2 to concrete behaviours to watch for. Ask one follow-up question, for example how they would test Ferry's time horizon without putting customers at risk. No generic praise.
