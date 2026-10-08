---
id: '7494195c-ecc4-4597-a8b3-f837817fe18a'
slug: ai-control-fundamentals-u4
title: "Is control enough?"
---
%% Part 1 of Unit 4 of AI Control Fundamentals; the unit continues in 'What control does to the world' (split into modules by topic, Elias 2026-10-08). The note below describes the whole unit as it was before the split. %%

%% Unit 4 of AI Control Fundamentals. Time (reading+tutor): welcome 4+3, slop 16+11, better schemers 14+13, protocols hold up 4+6, superintelligence 6+8, profit-only 16+17, warning shots 15+14, safety-washing 11+12, adversarial and AI welfare 18+14, practice 5+19 (lenses 226), plus about 18 for test 1 (classifying criticisms) and 8 for test 2 (backfire). About 252 minutes. %%

# Lens: Welcome to Unit 4
id:: db5cd027-63d2-431d-9ee8-fde62339bcb3
reading_minutes:: 4
tutor_minutes:: 3
tldr:: Criticisms of control dispute different things. Some say it will not work, some say it is not worth the effort, and some say it makes things worse. Telling them apart is the first step to judging them.
summary_for_tutor:: Opening lens of Unit 4 of AI Control Fundamentals, written by Lens. It introduces the unit's way of sorting criticisms of control into three kinds (control does not work, works but is not worth the effort, works and makes things worse), maps them onto two questions to ask of any safety plan ("if it worked, would it be good?" for the last two kinds, "would it work?" for the first, with a link to Yonatan Cale's similar split for safety cases), says that each criticism in the unit comes with replies from people who work on control, and lists what the unit covers. The question asks the learner to sort Jan Kulveit's criticism from Unit 1. Reference answer: it is the "works and makes things worse" kind, since it accepts that control can stop an AI but says this mostly turns useful warning shots into quiet catches or a larger failure. Do not tell the learner whether Kulveit is right.
#### Text
content::
Unit 3 set out why people work on control. This unit sets out the main criticisms, in the critics' own words, each with replies from people who work on control. It is not meant to settle who is right. It is meant to help you see what each criticism actually disputes, so you can weigh it.

We find it useful to sort criticisms of control into three kinds:

- **Control does not work.** It will not stop a capable scheming model, or it stops working as models get more capable.
- **Control works but is not worth the effort.** For example, scheming is unlikely, other failures matter more, or the work would happen anyway.
- **Control works and makes things worse.** It reduces one risk but raises the overall risk.

Another way to see the three kinds is to ask two questions of any safety plan, in this order: if it worked, would it be good? And then: would it work? (Yonatan Cale [separates two similar questions for safety cases](https://www.lesswrong.com/posts/HmdprC38DbjDnNmgt/improving-our-safety-cases-using-upper-and-lower-bounds): would a measure be sufficient if we had it, and can it be built?) "Does not work" criticisms answer the second question. "Not worth it" and "makes things worse" criticisms answer the first: even if control works, would it be good? This unit covers criticisms of both kinds.

Some criticisms have more than one side. The sorting helps you see what a criticism disputes. It does not decide whether the criticism is right.

When you answer a criticism, we suggest comparing the world with control against what would realistically happen without it, not against a perfect solution. Any safety measure falls short of perfect, so that comparison cannot tell you whether control helps. When you weigh a reply to a criticism, check that the reply makes the same realistic comparison.

\## In this unit you will

- Read John Wentworth's case against control research, with replies from Buck Shlegeris and Lucius Bushnaq.
- Read Oliver Habryka, Jozdien and MIRI on why control may not work, and what control's authors say back.
- Look at two recent experiments in which researchers stress-tested control protocols with smarter attacks.
- Read Oliver Habryka's worry that control pushes AI capabilities forward, and Yonatan Cale's question whether a company that only cares about profit would build a safety tool anyway, with three answers.
- Come back to Jan Kulveit's warning-shot argument, with the replies it got and two comments written after a real incident in 2026.
- Read about safety-washing and power concentration, about whether control could make AIs more adversarial, and about what controlling AIs could cost them if they matter morally.
- Practise sorting criticisms and tracing how a control measure could backfire.

#### Question: Open
id:: 31dcd176-d8e1-4df6-9bcc-63426148f058
force-feedback:: first
content::
In Unit 1 you read Jan Kulveit's argument that control may increase existential risk. Which of the three kinds of criticism is it, and why? One or two sentences.
feedback-instructions:: The learner sorts Jan Kulveit's Unit 1 criticism. It is mainly the "works and makes things worse" kind: Kulveit accepts that control can stop a misaligned AI, but argues it mostly turns moderate, visible warning shots into quiet catches inside a company, or into a larger failure later. If the learner says "not worth the effort", acknowledge that Kulveit also mentions control moving resources away from alignment, and that he calls this not the dominant effect. Two or three sentences. Do not say whether Kulveit is right. No generic praise. Send them to the first reading.

# Lens:
source:: [[../Lenses/AICF - Slop, not scheming]]

# Lens:
source:: [[../Lenses/AICF - Does control breed better schemers]]

# Lens:
source:: [[../Lenses/AICF - Do control protocols hold up]]

# Lens:
source:: [[../Lenses/AICF - What about superintelligence]]
