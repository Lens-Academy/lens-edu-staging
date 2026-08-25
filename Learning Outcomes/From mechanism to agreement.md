---
id: 'a8b96d09-37b6-4c3b-8902-d9609aec1fea'
learning-outcome: "Evaluate how a verification scheme maps onto the obligations of a concrete proposed AI treaty, and judge where the binding constraint on such an agreement is technical versus political"
domain: "[[../Domains/Governance and Policy]]"
stage: advanced
requires:
  - "[[A low-trust compute verification architecture]]"
authors:
  - Elias+Claude
eval-results:
  content-sha: 962e28db
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question depends on course scaffolding it never restates: it points at 'the verification machinery from this module' rather than supplying the mechanisms itself, so it cannot be posed at a random moment."}
  evidence: {B1: "Take the verification machinery from this module and map it onto those obligations"}
---
## Test:
id:: 51520b70-c2a7-43e0-a83a-444e9fb387fc
#### Question
content:: Consider a proposed international agreement with these obligations: a coalition led by the US and China; a cap on training scale, expressed as a threshold on the total compute (FLOP) used to train any single model, which the parties intend to enforce mainly by tracking advanced AI chips and where they are deployed; and a ban on research that advances toward superintelligence or that would undermine the agreement's own verifiability.

Now take the verification mechanisms that exist today or are close to it: accounting for AI chips along the supply chain, on-chip mechanisms that attest to or report how a chip is used, physical inspection of data centres, and capture of workload-level evidence about what was trained where — alongside non-technical fallbacks such as declarations, personnel vetting, and whistleblower protections.

**Map that machinery onto the agreement's obligations: which are well served by it, and which are not? Then make a judgement — is the binding constraint on this agreement technical or political, and what does your answer imply about what to work on?**
assessment-instructions::
Score according to the following rubric.

**1** — Summarizes the proposal without connecting it to verification, or asserts that verification simply solves it. *Example: "They propose a treaty between the US and China with a compute limit, and the verification methods we studied would be used to enforce it."*

**2** — Attempts a mapping but only in general terms, with no distinction between well-served and poorly served obligations, and the technical-versus-political judgement is unargued. *Example: "Chip tracking and inspections would cover the compute threshold. The research ban is harder. It's mostly a political problem."*

**3** — Maps the obligations with discrimination. **Well served:** a FLOP threshold on training is close to the ideal target for this machinery — it is a quantitative bound on an activity concentrated in large fixed facilities, reachable by chip supply-chain accounting, on-chip mechanisms, data-center inspection, and workload-level evidence capture; the proposal's own reliance on tracking chips and their deployment matches what the mechanisms actually deliver. **Poorly served:** a ban on *dangerous research* is a restriction on intellectual activity, not on a measurable physical quantity — it has no compute signature, can proceed at small scale on legitimate hardware, and would fall back on declarations, personnel measures, and whistleblowers rather than technical verification. Notes the reflexive provision — banning research that undermines verifiability — as an acknowledgement that the regime's own technical foundations are erodible. *Example: "The compute threshold is almost exactly what this machinery was built for: a number bounding an activity that lives in a few enormous buildings, reachable through chip accounting, on-chip mechanisms, data-center inspection, and workload evidence — and the proposal leans on chip tracking, which is what the mechanisms actually provide. The research ban is the opposite: it restricts thinking, not a measurable quantity. It has no compute footprint, it can happen at small scale on ordinary hardware, and you'd be relying on declarations, vetting, and whistleblowers. Notably they also ban research that would undermine verifiability, which is a tacit admission that the technical floor can be eroded from underneath."*

**4** — As above, plus reaches a defended judgement. Recognises that the scheme's effectiveness could diminish as capabilities advance and, critically, that the political will to put such an agreement in place does not currently exist — which, combined with the observation that many such obligations are already verifiable with existing or near-term technology, locates the binding constraint on the political side. Draws the implication carefully: this does *not* make technical work low-value, because verification research reduces the political cost of agreeing (less intrusion, less IP exposure, less espionage surface) and so relaxes the binding constraint rather than addressing a different one. *Example: Adds "Two things point the same way: the scheme could degrade as capabilities advance, and the political will doesn't exist today. Put that next to the fact that a lot of these obligations are *already* verifiable with existing or near-term tech, and the binding constraint is clearly political. But that's not an argument for abandoning the technical work — the mechanisms are what make agreement cheap enough to be politically possible. Less intrusion, less IP exposed, less espionage surface. Technical progress loosens the political constraint; it isn't a rival to it."*

**5** — As above, plus reasons about sequencing and fragility as a strategist. Verifiability and political will are coupled rather than independent: an agreement is easier to sign when it is verifiable, and mechanisms get built when an agreement looks plausible, so the work is to have credible verification ready before a political window opens — which is the argument behind treating the "datacenter lie detector" as an orphaned problem worth crash-building now rather than after a crisis. Notes the time dependence: the mechanisms rest on compute concentration and on the chip chokepoint, so a decentralizing technology base narrows the window in which this class of agreement is verifiable at all — making the ordering (build capability, then negotiate) urgent rather than merely tidy. May also note the reflexive risk that a coalition-led regime's verification demands are themselves a bargaining object, so scoping obligations to what is verifiable is both a technical and a diplomatic act. *Example: Adds "The two constraints aren't independent — an agreement is easier to sign when it's verifiable, and mechanisms get funded when an agreement looks plausible. Which means the real task is to have credible verification sitting on the shelf *before* a political window opens, because you can't build it during the crisis that creates the window. That's the force of calling the lie detector an orphaned problem: it's the thing nobody owns and everybody would need. And there's a clock on it, because the mechanisms depend on compute staying concentrated and the chip chokepoint holding. If capability decentralizes first, this class of agreement stops being verifiable at all — so the ordering isn't tidiness, it's a deadline."*
max-chars:: 2000

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - An International Agreement to Prevent Premature ASI]]

## Lens:
source:: [[../Lenses/AIV - Build the Datacenter Lie Detector]]
