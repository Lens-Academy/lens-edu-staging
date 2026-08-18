---
id: '48e9b3a0-92a5-40c6-ba1a-a23e67cae04b'
title: Navigator Post-Meeting Survey
{--{"author":"Turner's AI","timestamp":1787059063393}@@tags:
  - wip
--}---

#### Text
content:: You just ran a session, thank you. This is how we improve the run sheet, session structure and guidance week to week. Takes about two minutes.\n\nBe blunt: this is about fixing the system, not evaluating you. If something was broken, dense or confusing, that is the most useful thing you can tell us.

#### Text
content:: {--{"author":"Turner's AI","timestamp":1786810378917}@@\###--}{++{"author":"Turner's AI","timestamp":1786810378917}@@—++} The run sheet{++{"author":"Turner's AI","timestamp":1786810378917}@@ —++}

#### Rating
key:: run_sheet_worked
content:: How well did the run sheet work as your guide?
scale:: 5
low-label:: Got in my way
high-label:: Made it easy
required:: true

#### Choice
key:: content_amount_right
content:: Was the amount of content right for your session length?
options::
- Too little
- About right
- Too much
required:: true

#### Choice
key:: segments_over_or_cut
content:: Which segments ran long or got cut for time?
options::
- Lobby / welcome
- R1 Icebreaker
- R2 discussion
- Break
- R3 discussion
- R4 Feedback / next unit
- Close
- Nothing, we were on time
multi:: true

#### Question
key:: run_sheet_friction
content:: Anything in the run sheet that was confusing, wrong, or missing? Be blunt.

#### Text
content:: {--{"author":"Turner's AI","timestamp":1786810389025}@@\###--}{++{"author":"Turner's AI","timestamp":1786810389025}@@—++} Did the session land{++{"author":"Turner's AI","timestamp":1786810389025}@@ —++}

#### Rating
key:: group_engagement
content:: How engaged was your group overall?
scale:: 5
low-label:: Flat
high-label:: Buzzing
required:: true

#### Rating
key:: peer_connection
content:: Did participants connect with each other, not just with you?
scale:: 5
low-label:: Not really
high-label:: A lot
required:: true

#### Rating
key:: ended_energised
content:: Did people leave energised?
scale:: 5
low-label:: Fizzled
high-label:: Ended on a high
required:: true

#### Text
content:: {--{"author":"Turner's AI","timestamp":1786810396744}@@\###--}{++{"author":"Turner's AI","timestamp":1786810396744}@@—++} Ops and tech{++{"author":"Turner's AI","timestamp":1786810396744}@@ —++}

#### Choice
key:: friction_areas
content:: Any tech or logistics friction?
options::
- Zoom or the join link
- Breakout rooms
- Discord
- Calendar invite
- Session doc access
- Recording or notetaker
- Attendance not recorded
- No friction
multi:: true

#### Question
key:: friction_detail
content:: If you hit friction, tell us what broke.

#### Choice
key:: needed_intervention
content:: Did anything come up that needed you to step in?
options::
- No, it ran itself
- Minor facilitation nudges
- Yes, a substantive intervention
- Yes, and I would like someone to follow up

#### Question
key:: intervention_detail
content:: If you stepped in, what happened? Skip if nothing did.
placeholder:: A sentence is plenty.

#### Text
content:: {--{"author":"Turner's AI","timestamp":1786810404099}@@\###--}{++{"author":"Turner's AI","timestamp":1786810404099}@@—++} Anything else{++{"author":"Turner's AI","timestamp":1786810404099}@@ —++}

#### Question
key:: worked_well
content:: What is one thing that worked well that another navigator should copy?

#### Question
key:: dashboard_improvement
content:: What would make the navigator dashboard more useful?

#### Question
key:: {--{"author":"Turner's AI","timestamp":1786810411690}@@open_response--}{++{"author":"Turner's AI","timestamp":1786810411690}@@anything_else++}
content:: Anything else we should change before next week?
