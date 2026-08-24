---
id: 2f961736-2a29-4cc1-85d3-947286dd7728
tldr: "Can a weak teacher train a smarter student to exceed the teacher? Weak-to-strong generalization bets that powerful models already hold latent skills, and that imperfect human-level supervision can draw them out, a stand-in for aligning superhuman AI we can no longer fully check. Does the student surpass its supervisor, or just copy its mistakes?"
summary_for_tutor: "Presents weak-to-strong generalization (W2SG) as an empirical approach to superhuman alignment. Motivates using narrowly superhuman models as case studies, where weak models (e.g. GPT-2) stand in for human supervisors of stronger models (e.g. GPT-4). Explains the assumption that strong models hold latent capabilities weak supervision can elicit, defines the setup (weak supervisor, strong student, strong ceiling) and the Performance Gap Recovered (PGR) metric. Covers limitations (overfitting to weak errors, task-representation assumptions, slow-takeoff reliance), how W2SG complements scalable oversight, and sandwiching evaluations with their non-expert, model, and expert layers."
title: "Weak-to-Strong (W2S)"
reading_minutes: 14
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Scalable Oversight - Weak-to-Strong (W2S)|Weak-to-Strong (W2S)]]

#### Text
optional:: true
content::
The whole approach rests on strong models already holding skills that weak supervision can draw out rather than teach. Did you find that assumption convincing? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Weak-to-strong generalization treats superhuman alignment as something you can study now, by using a weak model as a stand-in for a human supervising a stronger one, for instance GPT-2 supervising GPT-4. The bet is that the strong model already has the relevant capability latent in it, so weak and error-prone supervision only has to elicit it rather than teach it. The setup has three reference points: the weak supervisor, the strong student trained on its labels, and the strong ceiling, what the student reaches with correct supervision. Performance Gap Recovered measures how much of the distance between weak supervisor and ceiling the student covers. The section gives the limitations: students can overfit to the weak supervisor's errors and inherit them, the approach assumes the task is already represented in the strong model, and it leans on a slow takeoff where there is time to iterate. It positions this as complementary to the rest of the chapter, and covers sandwiching evaluations, which put non-experts, a model, and experts at different layers to see where the model lands.

topics to explore:
- Eliciting a latent capability and teaching a new one are very different claims. Which does the evidence here actually support?
- If the student inherits the supervisor's mistakes, is that a failure of the method or exactly what supervision does?
- GPT-2 supervising GPT-4 stands in for a human supervising a superhuman system. Where does the analogy strain?
- The approach assumes a slow takeoff. The capabilities chapter treated that as contested. How much rests on it?
- Sandwiching places the model between non-experts and experts. What would it mean if it beat the non-experts but the gap to experts never closed?

This is the last reading in the chapter. A separate reflection comes next and asks the learner to recall the chapter from memory, so do not run a chapter-wide review here and do not quiz them on earlier sections.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.
