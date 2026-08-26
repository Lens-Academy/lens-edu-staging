---
id: 9899891d-b7c6-436b-b48a-f691e0994dcf
slug: ai-risk-fundamentals
slug-aliases: superintelligence-101
title: AI Risk Fundamentals
description: "This is an introductory AI safety course that assumes no prior knowledge of AI safety, or even computer science. We hope this course can serve as deep foundation for expanding knowledge into the student's areas of interest: technical AI safety, governance, or direct advocacy. In particular, it provides the base-level intuitions that motivate our main AI safety course, which is more ambitious in technical terms (for example, by asking the students to assess the various existing AI safety techniques)."
discussion: https://discord.com/channels/1440725236843806762/1481259751374327929
---

%%
Some overarching non-learning outcomes we want to achieve:
[[../Outcomes/Dummy - Agency to contribute]]
[[../Outcomes/Dummy - Personal contribution plan]]
[[../Outcomes/Dummy - Discuss AI risk with one person]]
%%

%%
Structural improvement (comment from student)

Just to second on this where participants have found the workload to be quite intensive. My impression on it is that there was miscalculation, misunderstanding, or underestimation from some participants in this regard. The pace also allows few opportunities for recalibration.
Also to talk briefly about the module construction, I concur that the contracted pacing has led to difficulties as the first 6 chapters of the book are the most dense, but leaving Chapter 6 for M3 also gives you a weird overhang where the discussion ends up fixating on Part II.
M3 in general was quite weird since the prior format offered better interrogation of the underlying issues. The video scenario ends shy of the cosmic stakes framing of Chapter 9. I believe there was also no explicit naming of instrumental convergence in this version, which I take to be a critical blunder as I would say most of my participants did not infer this themselves.
%%
# Module: [[../modules/IABIED M1 Intro and Nonhuman Minds, Part 1]]

# Meeting: Introduction
meeting-doc-template:: https://docs.google.com/document/d/1VbHf5ENp0fOjqATTMLbKYhhbUvPqvi7Ugs32THIum1g/edit
facilitator-survey:: [[../surveys/Navigator Session 1 Debrief]] {>>{"author":"Turner's AI","timestamp":1786809891204}@@SAMPLE FOR HAMZA - the intake half of the pair. Meeting 1 gets the fuller debrief (background, baseline scales, growth interest, referral prompt); meetings 2-5 get the short recurring one. Exactly the pattern the learner surveys already use on this course - AIRF Session 1 Survey here, AIRF Weekly Survey below.

Ported from the Cohort 4 "Navigator Week 1 Debrief" Google Form, keeping its framing verbatim because it is doing real work: "Be blunt: this is about fixing the system, not evaluating you."

The three baseline scales (risk_seriousness / agency_belief / motivation) deliberately reuse the SAME keys as the learner survey so navigator and learner trajectories are comparable in one export. community_connection is navigator-only - the learner instrument has next_step_clarity in that slot instead.

LIVE as of 2026-08-18. The platform side shipped in #531/#532: course.ts reads facilitator-survey::, and core/surveys/native.py serves it as a kind='facilitator' survey that unlocks on meeting end alone, with no check-in requirement (the navigator DM is routed by group roster, not attendance).<<}
survey:: [[../surveys/AIRF Session 1 Survey]] {>>{"author":"Turner's AI","timestamp":1786479585670}@@Native port of the AI Risk Fundamentals Week 1 Google Form (baseline scales + buddy handle + BlueDot history), matching the AIF Unit 1 pattern. Meeting 1 gets this intake survey; meetings 2-5 get the generic AIRF Weekly Survey. The Discord-handle question is deliberately dropped: the platform already knows who is answering, which is the whole reason the native surveys avoid the identity-matching problem the Google forms had.<<}

# Module: [[../modules/IABIED M2 Nonhuman Minds, Part 2]]

# Module: [[../modules/IABIED M3 Nonhuman Minds, Part 3]]

# Meeting: Nonhuman Minds
meeting-doc-template:: https://docs.google.com/document/d/1hNj0npIxflO6C5AJcNPHms7HOiH_hlAgomBPQVhfp2A/edit?tab=t.0#heading=h.by5wcelvjnsd
survey:: [[../surveys/AIRF Weekly Survey]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]
{>>{"author":"Elias's AI","timestamp":1786520689365}@@Correction: the 2026-08-09 note here claimed this link had been repointed to a rebuilt Ch3-5 doc, but the ID it named as "retired" was the same ID the link already used, so the link was never actually moved. The linked doc still ran the old Ch3-4 session (no Chapter 5, no glossary tab, next-unit pointer naming no reading) until 2026-08-12, which is why a navigator ran meeting 2 off outdated material. Fixed by updating the linked doc itself in place, so this link stays correct: Room 3 is now the Chapter 5 "weakest link" prompt, the next-unit pointers name Ch 6 + film + Coda + Your Leverage, and the missing Glossary tab (Modules 2 and 3) has been restored. The parallel Ch3-5 rebuild that lived in a personal Drive was never shared and is now renamed "OLD - ...(merged into live doc)".<<}


# Module: [[../modules/IABIED M4 One Extinction Scenario]]

# Meeting: One Extinction Scenario
meeting-doc-template:: https://docs.google.com/document/d/1Gg6RHLoWzjegjqeAL_AioitZdJE3tVL_t632h0COyMI/edit
survey:: [[../surveys/AIRF {++{"author":"Turner's AI","timestamp":1787704219034}@@Session 3 Survey]] {>>{"author":"Turner's AI","timestamp":1787704219034}@@Repointed 2026-08-26 from AIRF Weekly Survey to a new meeting-3-only file. Reason: the 1:1 booking block (user interview + career guidance) is for meeting 3 only, and AIRF Weekly Survey is shared by meetings 2, 3 and 4, so editing it in place would have put the booking offer on three meetings. AIRF Session 3 Survey is a byte-for-byte copy of AIRF ++}Weekly Survey with the booking block appended at the end, so every existing question keeps its key, wording and order and the pre/post rating comparison is untouched. Same pattern the course already uses for Session 1 and Session 5. Meetings 2 and 4 still point at AIRF Weekly Survey and were not touched. The block is three Text segments and adds NO answer keys: two Yes/No questions (user_interview_interest, career_chat_interest) were drafted and then removed on 2026-08-26 before promotion, because an answerable segment sitting between the two link sections could be answered and then wiped when the learner clicked through to book (survey answers live only in React state until Submit, and survey links have no target=_blank). The rule the file now satisfies: no answerable segment may precede an outbound link. Interest is measured by actual bookings on the four calendars, not by a survey answer.<<}
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]] {>>{"author":"Turner's AI","timestamp":1786809781581}@@The recurring half of the pair: meetings 2-5 all use this one, mirroring how the learner surveys use AIRF Weekly Survey in the same slots.

HISTORY (resolved). This line was authored 2026-08-16 as a target for a parser change that had not been built, and carried a long note saying it was silently ignored. That note is obsolete: the parser change shipped in #531, reached production in #532, and every meeting on this course now carries a facilitator-survey.

The typo guard at course.ts now contains-matches instead of prefix-matching /^surve/i, so facilitatorsurvey:: and facilitator_survey:: warn rather than vanish silently.<<}

# Module: [[../modules/IABIED M5 Facing The Challenge, Part 1]]

# Meeting: Facing the Challenge, part 1
meeting-doc-template:: https://docs.google.com/document/d/1dW_VlZoAn6eLR0_ZY8XvQvRoVvr51a23XAXMAnH_bSI/edit
survey:: [[../surveys/AIRF Weekly Survey]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]
{>>{"author":"AI","timestamp":1786279506695}@@Course reduced from 6 meetings to 5. Units: M1 | M2+M3 | M4 | M5 | M6+M7, one meeting after each unit. All five meeting docs were updated for these boundaries on 2026-08-09; the old unit-4 doc (19-KJb0ZEVlVYJoVMOnY5xbAm6UJdynAFM0nm7NSg9dg) is retired.<<}

# Module: [[../modules/IABIED M6 Facing The Challenge, Part 2]]

# Module: [[../modules/IABIED M7 What Happens Next]]

# Meeting: Facing the Challenge, part 2
meeting-doc-template:: https://docs.google.com/document/d/1rewnfH3QqcK_WhwD2i1ylfVyldH3sXb6eA45dDeQJ6M/edit?tab=t.0#heading=h.by5wcelvjnsd
survey:: [[../surveys/AIRF Session 5 Survey]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]

{>>{"author":"Turner's AI","timestamp":1786705668364}@@Meeting 5 was serving the generic AIRF Weekly Survey, same as meetings 2-4. That made the Session 1 intake a baseline with no endline: its four impact scales (risk_seriousness, agency_belief, motivation, next_step_clarity) were never asked again, even though the intake tells the learner in writing "We ask the same things again at the end, so the value is in the change, not the score." Repointed to the new AIRF Session 5 Survey, which re-asks all four under the SAME keys so a per-user pre/post delta is a straight join on user_id across meeting 1 and meeting 5. Also carries navigator feedback (quantitative + free text), the recommend score, and the next-cohort MORE/LESS questions ported from the old Week 6 Google Form. Dropped from that form: the Discord-handle question (the native survey already knows who is answering, which is the whole reason we moved off Forms) and the BlueDot question (already captured at intake as bluedot_history). NOTE the recommend score is 1-10, not the 0-10 of a textbook NPS: the platform's rating segments validate 1 <= value <= scale with MAX_RATING_SCALE = 10, so 0 is not expressible. Adjust any NPS formula accordingly, or read it as a 10-point recommend score.<<}

%% Post-meeting surveys (2026-08-11): the survey:: lines above attach the native
in-platform surveys, ported from the two AI Risk Fundamentals Google Forms.
Meeting 1 uses the intake survey (baseline scales); meetings 2-5 use the weekly
one. Keys match the AIF surveys wherever the question is the same
(buddy_texted, content_value, group_connection, meeting_value, worked_well,
could_improve) so the Ops CSV can be compared across courses; AIRF-only
questions get their own keys.

NOTE the course has 5 meeting markers by design (see the 2026-08-09 note above:
reduced from 6 to 5). Every meeting now has both a marker and a survey. %%

{>>{"author":"Turner's AI","timestamp":1786589345987}@@CORRECTED 2026-08-13. This note used to end: "but cohort 5 still carries number_of_group_meetings = 6 and 6 real meetings per group. The 6th meeting therefore has no marker, and so no survey. That is the outstanding 6-to-5 reconciliation, not something these lines can fix." That reconciliation LANDED on 2026-08-11 and the note was never updated, so it described a resolved problem as outstanding. Measured against prod 2026-08-13 02:45Z: c5, c6, c7 and c8 all carry number_of_group_meetings = 5; every c5 and c6 group has exactly 5 meetings with max meeting_number = 5; and there are ZERO live meetings numbered 6 or higher anywhere in c5-c8. The five meeting-doc-template links above were also checked one by one against the templates actually used to build the c6 session-4 and session-5 docs today, and all five match.<<}


