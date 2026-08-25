---
id: 3ec603de-965b-429f-9dbc-b54bc2d86002
learning-outcome: "Given an argument that concludes nobody should be allowed to attempt some technology, distinguish a position-statement (a conclusion drawn from the accumulated weight of evidence about the difficulty, which calls for preventing the attempt) from a counsel of despair (nothing can be done, so why bother), and explain why the first implies a specific kind of action while the second implies inaction."
reading-from: "Space probes. Nuclear reactors. Computer security. What do all these lessons add up to, and what can we learn from them about the difficulty of aligning an artificial superintelligence?"
reading-to: "end of chapter"
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Taking Action]]"
stage: beginner
eval-results:
  content-sha: 4afa9641
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is bound to reconstructing what Chapter 10 says (its closing position, its five curses), matching the 'State Chapter 11's central diagnosis' fail pattern.", B1: "Question is scaffolded on the specific chapter — it asks what Chapter 10's closing position is and how 'the chapter' wants it read, so it cannot be posed at a random moment."}
  evidence: {A2: "State Chapter 10's closing position ('NOBODY SHOULD BE ALLOWED TO TRY')", B1: "In your own words, what is Chapter 10's closing position, and how does the chapter want you to read it?"}
---

## Test:

id:: 3d3ca945-33d2-4a1b-a098-bc3571529754
#### Question
content:: Suppose someone argues as follows. Look at humanity's hardest engineering domains: space probes that failed on their first and only flight because of errors no ground test caught; nuclear reactors whose worst accidents came from interactions nobody had modelled; computer security, where systems that pass every test still fall to adversaries who find paths the designers never imagined. Building an artificial superintelligence, they say, carries all of these difficulties at once and several more besides — and unlike the others, you cannot inspect the system you are building, iterate on failures, or get a second try. They end with a blunt conclusion, in capital letters: "NOBODY SHOULD BE ALLOWED TO TRY."

Many readers hear that conclusion as despair — a counsel that nothing can be done. Someone making this argument usually means something different.

**In your own words, what position is that conclusion stating, and how is it meant to be read? Specifically, distinguish between despair (nothing can be done, so why bother) and a position-statement (a logical conclusion from evidence that calls for a specific kind of response).**

assessment-instructions::
Score according to the following rubric.

**1**: Reads the closing as despair or fatalism; concludes that the authors think humanity is doomed and there is nothing to do. *Example: "They're saying we're all going to die and there's no point trying."*

**2**: Senses that the position is more than despair but cannot articulate the distinction. *Example: "They're saying it's really really bad but I think they want us to do something about it."*

**3**: Correctly identifies that "NOBODY SHOULD BE ALLOWED TO TRY" is a *position-statement* (a logical conclusion from the cumulative weight of the difficulties named) rather than a counsel of despair. Articulates that the conclusion calls for action (preventing the attempt), not inaction. *Example: "The position is: given those difficulties combined, attempting to build ASI under current conditions is reckless. That's not despair. Despair would say 'we'll fail no matter what.' The claim is 'this specific attempt with this specific level of understanding will fail, so don't do it.' That implies action: prevent the attempt."*

**4**: As above, plus identifies that despair produces *inaction* while a position-statement produces *a different kind of action* (governance, restriction, treaty), and notes that this is what sets up a policy argument rather than an engineering one. *Example: Adds "Despair would tell people to give up; the position-statement tells them to organize. The claim is that the rational response to overwhelming engineering difficulty is to stop trying *until* the conditions change. That is a different kind of action than 'engineer harder.' That's also why it leads naturally into arguments about treaties and governance."*

**5**: As above, plus connects the despair / position-statement distinction to the fact that modern AI systems are grown rather than crafted (or an equivalent observation about the builders' lack of insight into their own system), and explains why a *crafted* engineering challenge of this difficulty might still be tackled by working harder, while a *grown* one of this difficulty cannot — making the position-statement the only available form of progress. *Example: Adds "If ASI were crafted, the response to compounding difficulties might be 'work harder, build better tools, get more eyes on it.' Because it's grown, the engineers don't even know what the failure modes of their own system are, so there's no 'work harder' move available. The position-statement is the only conclusion the evidence supports: under these conditions, the attempt itself is the failure mode."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Position Not Despair - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Position Not Despair]]
