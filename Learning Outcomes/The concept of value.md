---
id: '2e686f03-11a7-4203-bafb-6f75bc87ad4c'
learning-outcome: "Given a proposal to align an AI system with a person's or humanity's 'values', identify what the proposal takes values to be (for example, revealed choices, stated preferences, reward signals, or what the person would endorse on reflection), and construct a concrete case in which that conception and another plausible one come apart, so that the system would act against the person's values in the other sense."
topic: "[[../Domains and Topics/4 Agent Foundations/Values]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Value. AFFINE prerequisites: none. Not yet copied into requires:. %%
## Test:
id:: daa3de37-3545-463a-91af-abd6fa738fb9

#### Question: Open
id:: 53314bc0-8e96-417c-8caa-f6a212802271
content:: A startup describes its personal assistant AI like this: "Our assistant is aligned with each user's values. For every user, we show pairs of possible responses thousands of times, record which one the user picks, and train the assistant to produce the kind of response that user picks."

1. In this method, what is a user's "values" taken to be? State it precisely enough that someone could tell what the method would count as evidence about a user's values.
2. Describe one other thing that "a person's values" could reasonably mean that this method does not measure.
3. Construct a concrete situation involving one user in which the two meanings come apart, so that the assistant, working as designed, acts against that user's values in your second sense. Say what the assistant does and why the method produces it.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement with any view about which conception of value is correct. A learner may argue that the startup's conception is the right one, or that no single conception is adequate, and still earn full credit if parts 1 to 3 are done well.

**(1) The method's conception, 25 points.** Full credit: identifies that the method treats values as whatever produces the user's in-the-moment choices between presented options (revealed preference on the responses shown), so evidence about values is only which option was picked, under the conditions of picking. Extra precision within the 25 for noting that it measures choices among the options offered, not preferences about things the user is never shown. 12 points for a vague answer such as "what the user likes".

**(2) A second conception, 25 points.** Full credit for any clearly stated conception the method does not measure, for example: what the user would endorse after reflection or with fuller information; the user's stated long-term goals or commitments; the user's actual wellbeing or interests; values about states of the world the user never observes; values the user holds about what kind of person to be. 12 points if the second conception is named but is not clearly different from in-the-moment choice.

**(3) A divergence case, 50 points.** Full credit: a concrete situation with one user, where the two conceptions recommend different assistant behaviour, and a mechanism explaining why the method produces the behaviour that goes against the second conception. Examples of the kind of case that qualifies, not required ones: a user who picks flattering feedback on their writing but wants to become a better writer; a user who picks the reassuring answer about a health symptom but would, on reflection, want to be told to see a doctor; a user who picks responses that confirm their political views but values being well informed. 25 points if the case is generic ("people sometimes choose things that are bad for them") or if it does not explain why this training method produces the behaviour. 10 points if the case does not actually separate the two conceptions (both would recommend the same thing).

A fluent essay about the difficulty of defining values that does not complete part 3 with a specific case cannot score above 45.
feedback-instructions:: Name the strongest part, quoting a phrase. Then name the single most valuable improvement: usually either stating the method's conception precisely (choices among the options shown) or sharpening the divergence case so that the two conceptions clearly recommend different behaviour. If the answer is strong, ask whether the second conception the learner chose could itself be measured, and what would go wrong if it were. No generic praise.
