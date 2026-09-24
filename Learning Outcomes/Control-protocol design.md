---
id: '6877082d-d757-4df3-ba75-5ca13dd27779'
learning-outcome: "For a specified way a possibly scheming model could cause harm in a given deployment, propose a layered set of control measures that covers prevention (limiting what the model can reach or do), detection and response; decide for each response whether it must act before the model's action takes effect or can act afterwards, based on whether the harm is concentrated in a few actions and whether it can be undone; and for each measure name what it costs and how a model that knows about it could get around it."
topic: "[[../Domains and Topics/7 AI Control/Control protocols]]"
stage: intermediate
requires:
  - "[[Control threat modeling]]"
authors:
  - Elias+Claude
---
## Test:
id:: d579733e-0b1c-40b5-96e3-84af5a57f4df

#### Question: Open
id:: c046f23c-700b-4d89-80a2-cbbbe45a77d0
content::
An AI company runs an internal research agent built on its newest model, which it cannot rule out is scheming. The agent runs machine-learning experiments for the company's researchers. To do that it:

- reads the researchers' experiment configurations and writes its results to a shared experiment tracker;
- submits training and evaluation jobs to the company's compute cluster through the cluster's job scheduler, using credentials issued to the agent;
- can point jobs at any dataset stored on the cluster, including a restricted dataset of a few gigabytes that holds hazardous biology protocols used in the company's dangerous-capability evaluations;
- its jobs can download software packages from the internet through the company's proxy.

The company worries about one specific harm: the agent launching a job that sends the restricted dataset, or part of it, to a server outside the company.

Propose a layered set of control measures against this harm that includes at least one measure that prevents it, one that detects it and one that responds to it. For each measure:

1. say whether it prevents the harm, detects it, or responds to it;
2. for each response, say whether it has to act before the relevant action takes effect or can act afterwards, and why;
3. name its main cost to the company, and one way a model that knows about the measure could get around it.
placeholder:: Aim for three to six measures. About 250 to 450 words.
assessment-instructions:: Score 0 to 100. The capability tested is designing layered control measures for a specific threat, choosing the timing of responses from the shape of the harm, and knowing the price and the weak point of each measure. Load-bearing elements:

(1) Prevention, about 20 points: at least one measure that removes or narrows the agent's ability to reach the harm, with the prevention role stated and tied to this attack path. Examples: least-privilege permissions so the agent's jobs cannot read the restricted dataset, or can only use it through an interface that returns evaluation scores and never the raw data; network isolation so jobs that can read restricted data have no route to the internet; limits on outbound bandwidth; an approval step before the agent gets new permissions; audited, locked-down scheduler and job code so the agent cannot modify them. Explaining that the measure forces an attack across a boundary that can be watched is welcome but not required.

(2) Detection, about 15 points: at least one measure that notices an attempt, with the detection role stated. Examples: a monitor that reviews each job specification before it runs; monitoring of outbound traffic volume and destinations; alerts when a job reads restricted data it has no evident need for; comparison of the agent's behaviour against its normal baseline.

(3) Response timing, about 30 points. Sending the data out can happen in one job and cannot be undone: every part that leaves is permanently out, and splitting it into pieces only spreads the same permanent harm over more steps. So the response that matters for the sending step has to act before the transfer happens: blocking, pausing for human review, or replacing the action before it runs. About 20 for stating this with the reason: about 12 for either reason alone (that the harm cannot be undone, or that a single action does it and cannot be reverted in time), the full 20 for both. About 10 for correctly placing at least one other response, for example log review, incident investigation or reverting changes, as acceptable afterwards because it deals with something that can still be fixed or informs later decisions, or for saying explicitly that after-the-fact review cannot recover data once it has left. Judge timing by what the learner says the response does, not by its label: some sources file "blocking" under responses that act afterwards, but a response described as stopping the action before it runs counts as acting before.

(4) Costs and ways around, about 35 points. About 15 for a concrete, plausible cost for most measures (for example slower experiments from review before execution, engineering effort to build isolation or a scores-only interface, blocked legitimate package downloads, reviewer time for false alarms, researchers losing flexibility). About 20 for a concrete way around for most measures, specific to that measure (for example hiding the data inside traffic that looks legitimate such as a package request, encoding it in results written to the experiment tracker if that tracker is reachable from outside, writing a job specification that looks routine to a weaker monitor, requesting extra permissions with a plausible justification, getting a job that can read the data to hand it to a job that has network access, sending it in small pieces below volume alarms, or modifying the scheduler or job code itself). Generic evasions ("the model could be sneaky") earn nothing.

Gating caps (each below the pass bar):
- An answer with no prevention measure, no detection measure, or no response measure cannot score above 55.
- An answer that does not place a response for the sending step before the transfer takes effect, whether it omits the timing or puts it afterwards, cannot score above 55, unless it argues soundly that its prevention measures leave the agent no route for the transfer and says what would happen if they failed.
- An answer that places the response for the sending step before the transfer but gives no reason tied to the harm being impossible to undo or doable in a single action cannot score above 55.
- An answer that names a concrete cost for fewer than half of its measures cannot score above 55.
- An answer that names a specific way around for fewer than half of its measures cannot score above 55.

Accept any equivalent terminology; do not require the words "synchronous", "asynchronous", "least privilege" or any named technique. Additional sound measures, such as honeypots offering a fake easy path to external storage, earn credit within the element they belong to. Grade reasoning, not agreement: a learner who argues that one measure makes another unnecessary can score well if the argument holds for this deployment. A pass is roughly 60.
feedback-instructions:: Name the strongest measure in the answer in one sentence, then the single change that would most improve the answer. If the learner let the sending step be handled only after the fact, point out that data cannot be recalled once it has left. Do not reveal or discuss the numerical score. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - detection-mitigations]]
notes:: The detection half of the toolkit: monitoring on every action, auditing hierarchies, environment-level monitoring (rate detection, anomaly detection), and how models evade detection (evaluation awareness, collusion).

## Lens:
source:: [[../Lenses/XLab Control - prevention-response-mitigations]]
notes:: Prevention (permissions, isolation, supply chain) and response, including why averting an attack is harder than reverting one and why concentrated, irreversible threats need responses that act before the action. The practice question at the end uses a diffuse, reversible case (slowly weakened safety evaluations); the test uses a concentrated, irreversible one (restricted data leaving the company).
