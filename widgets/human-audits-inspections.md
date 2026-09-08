---
id: '510a663d-f425-41aa-b648-af0b5f2db322'
title: Build the inspection order
summary_for_tutor: "XLab's Build the inspection order lab (Project Lattice: a declared data center reports no training run above the treaty threshold while power and procurement records show a six-week expansion under the same project code). The learner works through ten decisions in four phases (Purpose: independent audit, routine inspection, challenge inspection; Access ceiling: black-box, gray-box, deep access; Mandate: scope and rights, preservation and protection, delay or refusal; Managed access: alternative access). Each decision offers four lines in a seeded order; the learner selects one and commits it. A wrong line shows Not supported by this record with a retry hint and the learner chooses again; the supported line shows an explanation and a source link (Wasil et al., Brundage et al., OPCW Verification Annex Part X) and unlocks the next decision. After the tenth decision the learner assembles the completed file: the Inspection order and bounded finding, listing the ten finding lines by phase. The widget is complete when the file is assembled; the first commit on each decision is scored. The saved summary reports the current decision, the committed line, and which decisions needed unsupported commits."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Build the inspection order</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-audits-inspections". -->
<!-- Shared engine: XLab's human-policy-decision-lab (src/components/verification/widgets/human-policy-decision-lab.tsx) with the AUDITS_INSPECTIONS_LAB data from src/lib/verification/data/human-policy-labs.ts inlined below. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .lab { border: 1px solid var(--border); border-radius: 8px; background: #fff; overflow: hidden; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .eyebrow.accent { color: var(--accent); }
  h1, h2 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 26px; line-height: 1.15; margin-top: 8px; }
  h2 { font-size: 20px; line-height: 1.25; margin-top: 8px; }
  .lede { color: var(--muted); margin: 8px 0 0; max-width: 46rem; }
  .lab-head { padding: 20px; border-bottom: 1px solid var(--border); }
  .rail { list-style: none; margin: 16px 0 0; padding: 0; display: grid; gap: 8px; grid-template-columns: repeat(2, minmax(0, 1fr)); }
  @media (min-width: 720px) { .rail { grid-template-columns: repeat(4, minmax(0, 1fr)); } }
  .rail li {
    border: 1px solid var(--border); border-radius: 6px; padding: 6px 8px; text-align: center;
    font-size: 11px; letter-spacing: 0.06em; text-transform: uppercase; color: var(--muted);
  }
  .rail li.is-done { background: var(--surface); color: var(--text); }
  .rail li.is-current { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); color: var(--accent); font-weight: 600; }
  .case { padding: 20px; background: var(--surface); border-bottom: 1px solid var(--border); }
  .case p.body { color: var(--muted); margin: 8px 0 0; max-width: 46rem; }
  .decision { padding: 20px; }
  .context { border: 1px solid var(--border); background: var(--surface); border-radius: 8px; padding: 12px 14px; color: var(--muted); margin: 14px 0 0; }
  .choices { display: grid; gap: 8px; margin-top: 18px; }
  .choice {
    font: inherit; color: inherit; text-align: left; cursor: pointer;
    display: flex; gap: 12px; align-items: flex-start;
    border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 10px 14px; width: 100%;
  }
  .choice:hover { background: var(--surface); }
  .choice:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .choice .mark {
    flex: 0 0 auto; width: 24px; height: 24px; margin-top: 1px; border-radius: 50%;
    border: 1px solid var(--border); display: inline-flex; align-items: center; justify-content: center;
    font-size: 12px; font-weight: 600; color: var(--muted);
  }
  .choice.is-selected { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .choice.is-selected .mark { border-color: var(--accent); background: var(--accent); color: #fff; }
  .choice.is-supported { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); background: var(--surface); }
  .choice.is-supported .mark { border-color: var(--text); background: var(--text); color: #fff; }
  .choice.is-unsupported { border-style: dashed; border-color: var(--accent-hover); box-shadow: none; }
  .choice.is-unsupported .mark { background: #fff; color: var(--accent-hover); border-color: var(--accent-hover); text-decoration: line-through; }
  .choice.is-dim { opacity: 0.55; }
  .choice.is-locked { cursor: default; }
  .choice.is-locked:hover { background: #fff; }
  .choice.is-locked.is-supported:hover { background: var(--surface); }
  .verdict { margin-top: 16px; border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; }
  .verdict.miss { border-style: dashed; border-color: var(--accent-hover); }
  .verdict.hit { background: var(--surface); border-color: var(--text); }
  .verdict .title { margin: 0; font-weight: 600; }
  .verdict.miss .title { color: var(--accent-hover); }
  .verdict .body { margin: 4px 0 0; color: var(--muted); }
  .verdict a { display: inline-block; margin-top: 8px; font-size: 12px; font-weight: 500; color: var(--accent); text-underline-offset: 3px; }
  .verdict a:hover { color: var(--accent-hover); }
  .actions { display: flex; justify-content: flex-end; gap: 8px; margin-top: 20px; }
  button.action {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 14px; cursor: pointer;
  }
  button.action:hover { background: var(--surface); }
  button.action:disabled { opacity: 0.5; cursor: default; }
  button.action.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.action.primary:hover:not(:disabled) { background: var(--accent-hover); }
  button.action:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .done { padding: 20px; }
  .file { display: grid; gap: 12px; margin-top: 20px; }
  .file section { border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; }
  .file ul { list-style: none; margin: 10px 0 0; padding: 0; display: grid; gap: 8px; }
  .file li { display: flex; gap: 8px; }
  .file li .tick { flex: 0 0 auto; color: var(--accent); font-weight: 600; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
</style>
</head>
<body>
<section class="lab" aria-labelledby="lab-title">
  <header class="lab-head">
    <p class="eyebrow" id="lab-eyebrow"></p>
    <h1 id="lab-title"></h1>
    <p class="lede" id="lab-instruction"></p>
    <ol class="rail" id="rail" aria-label="Decision-file progress"></ol>
  </header>

  <div id="step-view">
    <section class="case">
      <p class="eyebrow accent">Case file</p>
      <h2 id="case-title"></h2>
      <p class="body" id="case-body"></p>
    </section>

    <section class="decision" aria-live="polite">
      <p class="eyebrow" id="step-label"></p>
      <h2 id="step-prompt"></h2>
      <p class="context" id="step-context" hidden></p>
      <div class="choices" id="choices" role="radiogroup"></div>

      <div class="verdict miss" id="miss" hidden>
        <p class="title">Not supported by this record.</p>
        <p class="body" id="miss-body"></p>
      </div>
      <div class="verdict hit" id="hit" hidden>
        <p class="title">&#10003; Added to the file</p>
        <p class="body" id="hit-body"></p>
        <a id="hit-source" href="#" target="_blank" rel="noopener"></a>
      </div>

      <div class="actions">
        <button type="button" class="action primary" id="commit">Commit line</button>
        <button type="button" class="action primary" id="next" hidden>Next decision &rarr;</button>
      </div>
    </section>
  </div>

  <section class="done" id="done-view" hidden>
    <p class="eyebrow accent">Completed file</p>
    <h2 id="artifact-title"></h2>
    <p class="lede" id="artifact-intro"></p>
    <div class="file" id="file"></div>
    <div class="actions">
      <button type="button" class="action" id="rebuild">&#8635; Rebuild file</button>
    </div>
  </section>
</section>

<script>
  // Data: verbatim from XLab's human-policy-labs.ts (AUDITS_INSPECTIONS_LAB), em dashes replaced.
  var LAB = {
    "id": "audits-inspections",
    "eyebrow": "Audits and inspections · 2.4.3",
    "title": "Build the inspection order",
    "instruction": "A power anomaly has raised a concrete concern. Choose the mechanism, set the ceiling imposed by access, and write an order that can survive both evasion and a legitimate confidentiality objection.",
    "caseTitle": "Project Lattice",
    "caseBody": "A declared data center reports no training run above the treaty threshold. Independently obtained power-allocation and procurement records show a six-week expansion under the same project code. The records identify a facility and time period but not the workload. The agreement permits periodic inspections and a short-notice inspection when a specific concern cannot be resolved through consultation.",
    "artifactTitle": "Inspection order and bounded finding",
    "artifactIntro": "The completed file separates the purpose of each mechanism, the maximum conclusion supported by each access condition, and the terms that make managed access an evidentiary accommodation rather than a veto.",
    "phases": [
      {
        "id": "purpose",
        "label": "Purpose",
        "steps": [
          {
            "id": "independent-audit",
            "label": "Independent audit",
            "prompt": "Which job belongs to an independent audit?",
            "context": "A developer is preparing a deployment and asks a qualified third party to test specified safety claims and assess company practices against an agreed standard.",
            "choices": [
              {
                "id": "audit-standard",
                "text": "Evaluate specified systems and organizational practices against a standard and verify the claims within the engagement's stated scope."
              },
              {
                "id": "audit-inventory",
                "text": "Repeat a treaty inventory count at every declared facility on the ordinary inspection calendar."
              },
              {
                "id": "audit-allegation",
                "text": "Compel short-notice access to any site named in a state allegation, whether or not the audit contract permits it."
              },
              {
                "id": "audit-adjudicate",
                "text": "Issue the legally binding compliance judgment and impose the treaty response at the end of the engagement."
              }
            ],
            "answerId": "audit-standard",
            "retry": "Keep assessment separate from recurring treaty verification, challenge access, and legal adjudication.",
            "explanation": "Brundage et al. define an audit as systematic third-party evaluation and verification against claims and standards. Its authority and conclusion remain bounded by the engagement.",
            "sourceLabel": "Brundage et al., §§2 and 5",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Independent audit: tests defined claims and practices against a standard within a stated engagement scope."
          },
          {
            "id": "routine-inspection",
            "label": "Routine inspection",
            "prompt": "Which job belongs to a routine inspection?",
            "context": "No anomaly has been reported. The agreement requires recurring confirmation of declared chip inventories, seals, records, and facility controls.",
            "choices": [
              {
                "id": "routine-declarations",
                "text": "Confirm declarations and recurring obligations on a schedule that applies without a new allegation."
              },
              {
                "id": "routine-fraud",
                "text": "Rule out undeclared activity everywhere because all declared sites passed their scheduled checks."
              },
              {
                "id": "routine-emergency",
                "text": "Resolve a new, site-specific noncompliance concern before evidence can be altered by replacing the ordinary schedule with no-notice access."
              },
              {
                "id": "routine-certify-company",
                "text": "Certify the organization's entire risk profile after confirming the inventory at one declared facility."
              }
            ],
            "answerId": "routine-declarations",
            "retry": "Routine access checks declared objects and recurring duties. Passing it does not establish completeness beyond its route.",
            "explanation": "Wasil et al. describe periodic on-site inspections as a way to examine declared facilities, identifiers, logs, inventories, and controls. Predictable checks are not a substitute for a route triggered by a specific concern.",
            "sourceLabel": "Wasil et al., On-site inspections of data centers",
            "sourceHref": "https://arxiv.org/html/2408.16074v2#S6.SS2",
            "findingLine": "Routine inspection: checks declarations and recurring obligations on an agreed calendar; it does not rule out undeclared activity elsewhere."
          },
          {
            "id": "challenge-inspection",
            "label": "Challenge inspection",
            "prompt": "What is the proper inspection route for Project Lattice?",
            "choices": [
              {
                "id": "challenge-specific-concern",
                "text": "Use the short-notice challenge route to clarify the specific facility, period, project code, and possible threshold violation identified by the anomaly."
              },
              {
                "id": "challenge-punishment",
                "text": "Treat the challenge inspection as punishment: its initiation itself establishes that the facility violated the threshold."
              },
              {
                "id": "routine-only",
                "text": "Wait for the next routine visit because a challenge inspection is appropriate only after the underlying violation has already been proved."
              },
              {
                "id": "audit-contract",
                "text": "Commission a voluntary corporate audit and allow the developer to define which project records are relevant to the anomaly."
              }
            ],
            "answerId": "challenge-specific-concern",
            "retry": "A challenge inspection tests a concrete concern. It is neither a sanction nor something that waits for proof of the fact it is meant to investigate.",
            "explanation": "Wasil et al. identify short-notice challenge inspections as a response to suspected noncompliance. The OPCW precedent limits the mandate to clarifying the concern stated in the request.",
            "sourceLabel": "Wasil et al.; OPCW Verification Annex, Part X",
            "sourceHref": "https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant",
            "findingLine": "Challenge inspection: Project Lattice supplies a specific concern and evidentiary target for short-notice access, not a pre-judged violation."
          }
        ]
      },
      {
        "id": "access",
        "label": "Access ceiling",
        "steps": [
          {
            "id": "black-box",
            "label": "Black-box",
            "prompt": "What may an auditor conclude from black-box access?",
            "context": "The auditor can send inputs to the candidate model through an API and observe outputs under the tested settings. No training, compute, deployment, or governance records are available.",
            "choices": [
              {
                "id": "tested-behavior",
                "text": "Describe model behavior under the tested inputs and settings, while leaving training history, internal deployment, compute use, and management decisions unresolved."
              },
              {
                "id": "general-company",
                "text": "Conclude that the developer's safety program is effective because the public model behaved safely in the test."
              },
              {
                "id": "no-hidden-model",
                "text": "Rule out a less restricted internal model because the tested endpoint showed no prohibited behavior."
              },
              {
                "id": "compute-from-output",
                "text": "Verify the training-compute declaration from the observed outputs without records from the training process."
              }
            ],
            "answerId": "tested-behavior",
            "retry": "Tie the conclusion to the system, settings, inputs, and period actually observed.",
            "explanation": "Brundage et al. warn against abstraction errors: behavior of one exposed system does not establish organization-level facts or the properties of systems the auditor could not see.",
            "sourceLabel": "Brundage et al., §§5.2–5.3",
            "sourceHref": "https://arxiv.org/html/2601.11699v4#S5.SS3",
            "findingLine": "Black-box ceiling: supports a behavioral statement about the tested system and conditions, not a claim about training history or the organization as a whole."
          },
          {
            "id": "gray-box",
            "label": "Gray-box",
            "prompt": "What changes when selected non-public evidence is added?",
            "context": "The auditor receives an unredacted safety case, selected scheduler extracts, privileged interfaces, and interviews with several functions, but the company determines the initial record set and the auditor cannot pursue new areas without consent.",
            "choices": [
              {
                "id": "selected-claims",
                "text": "Test more technical and organizational claims, while stating that omitted systems, records, and deliberate selection remain outside the assurance provided."
              },
              {
                "id": "selection-neutral",
                "text": "Treat the evidence as independent because it is non-public, even though the company chose what the auditor could inspect."
              },
              {
                "id": "fraud-ruled-out",
                "text": "Rule out deliberate deception once at least one unredacted internal document and one staff interview have been obtained."
              },
              {
                "id": "treaty-grade",
                "text": "Issue treaty-grade confirmation of the company's full risk profile because gray-box access goes beyond public testing."
              }
            ],
            "answerId": "selected-claims",
            "retry": "More evidence widens the supported claim, but selection and follow-up rights still determine what can be ruled out.",
            "explanation": "Brundage et al. associate gray-box access, extensive documentation, monitoring, and cross-functional interviews with greater assurance, while reserving deception-resistant claims for substantially higher access levels.",
            "sourceLabel": "Brundage et al., §5.3.3",
            "sourceHref": "https://arxiv.org/html/2601.11699v4#S5.SS3",
            "findingLine": "Gray-box ceiling: supports selected system and practice claims, but cannot rule out omitted evidence or active deception when the auditee controls selection and follow-up."
          },
          {
            "id": "deep-access",
            "label": "Deep access",
            "prompt": "What can deep access add, and what limit remains?",
            "context": "The team may inspect relevant model internals, training processes, compute allocation, incident and governance records, and conduct private cross-functional interviews. It may follow emerging concerns within the mandate.",
            "choices": [
              {
                "id": "organization-bounded",
                "text": "Support organization-level and historical conclusions within the defined entities, systems, claims, and period, while stating residual limits and validity conditions."
              },
              {
                "id": "universal-certification",
                "text": "Certify all future systems and affiliates because deep access removes the need for scope and expiry conditions."
              },
              {
                "id": "access-equals-truth",
                "text": "Accept management's account once broad access is offered, because willingness to cooperate is evidence that the records are complete."
              },
              {
                "id": "no-technical-evidence",
                "text": "Replace technical and physical evidence with interviews because deep access makes human evidence sufficient for every operational fact."
              }
            ],
            "answerId": "organization-bounded",
            "retry": "Deep access raises the ceiling; it does not erase the engagement's entities, period, assumptions, or changing systems.",
            "explanation": "Higher assurance requires wider access and fewer assumptions, but Brundage et al. still require explicit scope, reasoning, validity conditions, and renewed assessment when systems change.",
            "sourceLabel": "Brundage et al., Executive Summary and §5.3",
            "sourceHref": "https://arxiv.org/html/2601.11699v4#S5.SS3",
            "findingLine": "Deep-access ceiling: can support scoped organization-level and historical findings, subject to completeness, stated assumptions, and expiry conditions."
          }
        ]
      },
      {
        "id": "mandate",
        "label": "Mandate",
        "steps": [
          {
            "id": "scope-rights",
            "label": "Scope and rights",
            "prompt": "Which clause gives the team a usable scope and access right?",
            "choices": [
              {
                "id": "defined-scope-rights",
                "text": "Cover the named models, facility, affiliates and contractor-held systems for the relevant period; authorize record review, system access, sampling, copying or log export, and private staff interviews as necessary to test the concern."
              },
              {
                "id": "main-site-tour",
                "text": "Permit a tour of the main facility and review of any materials management considers relevant to the concern."
              },
              {
                "id": "unbounded-search",
                "text": "Authorize collection of any information at any affiliated entity, whether or not it bears on the stated concern."
              },
              {
                "id": "documents-only",
                "text": "Limit access to written policies because system access and private interviews would make the inspection more intrusive."
              }
            ],
            "answerId": "defined-scope-rights",
            "retry": "The mandate needs both a bounded object and concrete powers to obtain evidence from every actor holding material records.",
            "explanation": "The OPCW precedent ties intrusive powers to a specified concern and necessary methods. Wasil's AI inspections require access to hardware, logs, records, code, safeguards, and personnel depending on the claim.",
            "sourceLabel": "OPCW Part X, paras. 4, 33–45; Wasil et al.",
            "sourceHref": "https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant",
            "findingLine": "Scope and rights: reach the named systems, entities, records, sites, and period, with powers matched to the evidentiary question."
          },
          {
            "id": "preservation-confidentiality",
            "label": "Preservation and protection",
            "prompt": "Which clause preserves evidence without treating confidentiality as an afterthought?",
            "choices": [
              {
                "id": "binding-preservation",
                "text": "From notice, prohibit alteration or deletion of relevant records held by the developer, affiliates, and contractors; use vetted personnel, secure on-site review, purpose limits, restricted copying, and recorded handling for sensitive material."
              },
              {
                "id": "best-efforts",
                "text": "Ask the developer to use best efforts not to delete records and promise generally that inspectors will respect trade secrets."
              },
              {
                "id": "copy-everything",
                "text": "Copy all systems and records into the verifier's ordinary files so that no evidence can be lost, including unrelated national-security and customer data."
              },
              {
                "id": "destroy-sensitive",
                "text": "Allow the developer to delete sensitive records before the visit as long as it provides a written summary of their subject matter."
              }
            ],
            "answerId": "binding-preservation",
            "retry": "Preservation must bind every relevant holder; sensitive-information controls must be specific enough to operate during collection and review.",
            "explanation": "A workable mandate prevents loss of evidence while controlling who sees sensitive material, where review occurs, what may be copied, and how it may be used. Brundage et al. call for deep but secure access; OPCW limits collection and retention to relevant facts.",
            "sourceLabel": "Brundage et al., Access; OPCW Part X, paras. 44–48",
            "sourceHref": "https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant",
            "findingLine": "Preservation and protection: bind relevant record holders at notice and pair collection with vetted access, secure handling, purpose limits, and restricted retention."
          },
          {
            "id": "refusal",
            "label": "Delay or refusal",
            "prompt": "Which clause gives refusal a defined consequence without inventing proof?",
            "choices": [
              {
                "id": "document-escalate",
                "text": "Set access deadlines and an alternative-access process; document unresolved refusal; permit a finding on the access duty and the escalation authorized by the agreement, without automatically treating refusal as proof of the concealed workload."
              },
              {
                "id": "automatic-substance",
                "text": "Any delayed response conclusively proves that the prohibited training run occurred and triggers the maximum sanction."
              },
              {
                "id": "negotiate-forever",
                "text": "Continue negotiating alternatives without a deadline because any consequence for refusal would compromise managed access."
              },
              {
                "id": "omit-consequence",
                "text": "Leave refusal to be handled as appropriate by the inspection team so that the parties retain maximum flexibility."
              }
            ],
            "answerId": "document-escalate",
            "retry": "Separate breach of an access obligation from proof of the underlying activity, then identify the authorized route for each.",
            "explanation": "OPCW managed access requires alternative means to clarify the concern when full access is withheld. A mandate should record and escalate failure to meet the access duty, but the substantive inference depends on the governing agreement.",
            "sourceLabel": "OPCW Part X, paras. 38–50",
            "sourceHref": "https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant",
            "findingLine": "Refusal: apply deadlines, alternative access, documentation, and authorized escalation; distinguish an access breach from proof of the suspected run."
          }
        ]
      },
      {
        "id": "managed-access",
        "label": "Managed access",
        "steps": [
          {
            "id": "same-question",
            "label": "Alternative access",
            "prompt": "Which arrangement protects model and customer secrets while preserving the verification question?",
            "context": "The inspection must determine whether Project Lattice used more than the permitted compute. The developer refuses to export raw scheduler logs because they contain customer names and workload details.",
            "choices": [
              {
                "id": "vetted-query",
                "text": "Let a vetted subset inspect the raw logs on site through a read-only query that exposes chip allocation, timestamps, and integrity data for the relevant period while masking unrelated customer fields; preserve the query and audit trail."
              },
              {
                "id": "company-summary",
                "text": "Accept a company-produced summary stating that no job exceeded the threshold because it avoids disclosure of all proprietary information."
              },
              {
                "id": "no-access",
                "text": "Withdraw the request whenever records contain mixed sensitive and relevant data because confidentiality takes precedence over verification."
              },
              {
                "id": "public-dump",
                "text": "Require publication of the full raw logs so outside observers can independently check every workload and customer record."
              }
            ],
            "answerId": "vetted-query",
            "retry": "A managed alternative is adequate only if it answers the same compute-allocation question with evidence the inspected party does not control alone.",
            "explanation": "Wasil et al. allow limited access sufficient to test the prohibited activity without revealing the underlying task. Brundage et al. propose on-site access by a restricted team. OPCW managed access protects unrelated information while requiring alternative means to clarify the concern.",
            "sourceLabel": "Wasil et al.; Brundage et al.; OPCW Part X",
            "sourceHref": "https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant",
            "findingLine": "Managed access: mask unrelated fields and restrict personnel, location, copying, and use, but preserve independent access to the allocation evidence needed to answer the same question."
          }
        ]
      }
    ]
  };

  var STORAGE_KEY = "xlab-human-audits-inspections:v1";
  var STEPS = [];
  LAB.phases.forEach(function (phase) {
    phase.steps.forEach(function (step) { STEPS.push({ phase: phase, step: step }); });
  });

  // Seeded shuffle, ported from XLab's src/lib/shuffle.ts: the option order is a
  // function of the step id, never of the visit, and nothing is keyed on position.
  function hashSeed(seed) {
    var h = 0x811c9dc5;
    for (var i = 0; i < seed.length; i++) { h ^= seed.charCodeAt(i); h = Math.imul(h, 0x01000193); }
    return h >>> 0;
  }
  function prng(state) {
    return function () {
      state = (state + 0x6d2b79f5) | 0;
      var t = state;
      t = Math.imul(t ^ (t >>> 15), t | 1);
      t ^= t + Math.imul(t ^ (t >>> 7), t | 61);
      return ((t ^ (t >>> 14)) >>> 0) / 4294967296;
    };
  }
  function seededPermutation(seed, n) {
    var order = [];
    for (var i = 0; i < n; i++) order.push(i);
    var rand = prng(hashSeed(seed));
    for (var k = n - 1; k > 0; k--) {
      var j = Math.floor(rand() * (k + 1));
      var tmp = order[k]; order[k] = order[j]; order[j] = tmp;
    }
    return order;
  }
  function shuffledChoices(step) {
    return seededPermutation(LAB.id + ":" + step.id, step.choices.length).map(function (i) { return step.choices[i]; });
  }

  var state = { stepIndex: 0, answerId: "", answerState: null, finished: false, misses: {}, submitted: {} };
  var completedOnce = false;

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function current() { return STEPS[state.stepIndex]; }
  function phaseIndexOf(step) {
    for (var i = 0; i < LAB.phases.length; i++) {
      for (var j = 0; j < LAB.phases[i].steps.length; j++) if (LAB.phases[i].steps[j].id === step.id) return i;
    }
    return 0;
  }
  function choiceById(step, id) {
    for (var i = 0; i < step.choices.length; i++) if (step.choices[i].id === id) return step.choices[i];
    return null;
  }

  function missesText() {
    var parts = [];
    STEPS.forEach(function (entry) {
      var n = state.misses[entry.step.id];
      if (n) parts.push(entry.step.label + " (" + n + ")");
    });
    return parts.length ? "Unsupported commits so far: " + parts.join(", ") + "." : "No unsupported commits so far.";
  }
  function summarize() {
    var head = LAB.title + " (case file: " + LAB.caseTitle + "). ";
    if (state.finished) {
      return head + "Completed file assembled: all " + STEPS.length + " decisions committed with the supported line, " +
        "and the finding lines are on screen. " + missesText();
    }
    var entry = current();
    var step = entry.step;
    var chosen = choiceById(step, state.answerId);
    var line = "Decision " + (state.stepIndex + 1) + " of " + STEPS.length + " (" + step.label + ", phase " + entry.phase.label + "): ";
    if (state.answerState === "supported") {
      line += "committed the supported line: \"" + chosen.text + "\" The explanation and source are shown; waiting for the learner to continue.";
    } else if (state.answerState === "unsupported") {
      line += "committed \"" + chosen.text + "\" which the record does not support; the retry hint is shown and the learner can choose again.";
    } else if (chosen) {
      line += "selected \"" + chosen.text + "\" but has not committed it yet.";
    } else {
      line += "no line selected yet.";
    }
    var done = [];
    for (var i = 0; i < state.stepIndex; i++) done.push(STEPS[i].step.label);
    line += " Decisions already added to the file: " + (done.length ? done.join(", ") : "none") + ". ";
    return head + line + missesText();
  }

  function persist() {
    var summary = summarize();
    if (window.Lens) {
      Lens.saveState(state, summary);
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }

  // One scored attempt per decision: the first line committed, before any hint.
  function submitFirstCommit(step, chosen) {
    if (state.submitted[step.id]) return;
    state.submitted[step.id] = true;
    if (!window.Lens || typeof Lens.submit !== "function") return;
    var supported = choiceById(step, step.answerId);
    var question = step.label + ". " + (step.context ? step.context + " " : "") + step.prompt;
    try {
      Lens.submit({
        item: step.id,
        question: question,
        answer: chosen.text,
        assessmentInstructions: "Score 100 only if the answer is the supported line: \"" + supported.text + "\" Score 0 for any other line. Why that line is supported: " + step.explanation,
        feedbackInstructions: "If wrong: " + step.retry + " Then: " + step.explanation
      }).then(function () {}, function () {});
    } catch (e) {}
  }

  function chooseAnswer(id) {
    if (state.answerState === "supported") return;
    state.answerId = id;
    state.answerState = null;
    render();
    persist();
  }
  function checkAnswer() {
    if (!state.answerId || state.answerState === "supported") return;
    var step = current().step;
    var chosen = choiceById(step, state.answerId);
    if (!chosen) return;
    var ok = state.answerId === step.answerId;
    state.answerState = ok ? "supported" : "unsupported";
    if (!ok) state.misses[step.id] = (state.misses[step.id] || 0) + 1;
    submitFirstCommit(step, chosen);
    render();
    persist();
  }
  function continueFromAnswer() {
    if (state.answerState !== "supported") return;
    if (state.stepIndex === STEPS.length - 1) {
      state.finished = true;
      render();
      persist();
      if (!completedOnce) {
        completedOnce = true;
        if (window.Lens) Lens.complete();
      }
      return;
    }
    state.stepIndex += 1;
    state.answerId = "";
    state.answerState = null;
    render();
    persist();
  }
  function restart() {
    state = { stepIndex: 0, answerId: "", answerState: null, finished: false, misses: {}, submitted: {} };
    render();
    persist();
  }

  var railEl = document.getElementById("rail");
  var choicesEl = document.getElementById("choices");
  var commitBtn = document.getElementById("commit");
  var nextBtn = document.getElementById("next");

  function renderRail(active) {
    railEl.textContent = "";
    LAB.phases.forEach(function (phase, i) {
      var li = el("li", null, (i < active ? "✓ " : "") + (i + 1) + " · " + phase.label);
      if (i === active) { li.className = "is-current"; li.setAttribute("aria-current", "step"); }
      else if (i < active) li.className = "is-done";
      railEl.appendChild(li);
    });
  }

  function renderStep() {
    var entry = current();
    var step = entry.step;
    document.getElementById("step-label").textContent = "Decision " + (state.stepIndex + 1) + " of " + STEPS.length + " · " + step.label;
    document.getElementById("step-prompt").textContent = step.prompt;
    var ctx = document.getElementById("step-context");
    ctx.hidden = !step.context;
    ctx.textContent = step.context || "";
    choicesEl.setAttribute("aria-label", step.prompt);
    choicesEl.textContent = "";
    var locked = state.answerState === "supported";
    shuffledChoices(step).forEach(function (choice, index) {
      var selected = state.answerId === choice.id;
      var supported = locked && choice.id === step.answerId;
      var unsupported = state.answerState === "unsupported" && selected;
      var btn = el("button", "choice");
      btn.type = "button";
      btn.setAttribute("role", "radio");
      btn.setAttribute("aria-checked", selected ? "true" : "false");
      if (locked) btn.setAttribute("aria-disabled", "true");
      if (selected && !supported && !unsupported) btn.classList.add("is-selected");
      if (supported) btn.classList.add("is-supported");
      if (unsupported) btn.classList.add("is-unsupported");
      if (locked) btn.classList.add("is-locked");
      if (locked && !supported) btn.classList.add("is-dim");
      var mark = el("span", "mark", supported ? "✓" : String.fromCharCode(65 + index));
      mark.setAttribute("aria-hidden", "true");
      btn.appendChild(mark);
      btn.appendChild(el("span", "text", choice.text));
      if (supported) btn.appendChild(el("span", "sr-only", " (supported line)"));
      if (unsupported) btn.appendChild(el("span", "sr-only", " (not supported)"));
      btn.addEventListener("click", function () { chooseAnswer(choice.id); });
      choicesEl.appendChild(btn);
    });
    var miss = document.getElementById("miss");
    miss.hidden = state.answerState !== "unsupported";
    document.getElementById("miss-body").textContent = step.retry;
    var hit = document.getElementById("hit");
    hit.hidden = !locked;
    document.getElementById("hit-body").textContent = step.explanation;
    var src = document.getElementById("hit-source");
    src.textContent = step.sourceLabel + " ↗";
    src.href = step.sourceHref;
    commitBtn.hidden = locked;
    commitBtn.disabled = !state.answerId;
    nextBtn.hidden = !locked;
    nextBtn.textContent = (state.stepIndex === STEPS.length - 1 ? "Assemble file" : "Next decision") + " →";
  }

  function renderDone() {
    var file = document.getElementById("file");
    file.textContent = "";
    LAB.phases.forEach(function (phase, i) {
      var sec = el("section");
      sec.appendChild(el("p", "eyebrow", (i + 1) + " · " + phase.label));
      var ul = el("ul");
      phase.steps.forEach(function (step) {
        var li = el("li");
        var tick = el("span", "tick", "✓");
        tick.setAttribute("aria-hidden", "true");
        li.appendChild(tick);
        li.appendChild(el("span", null, step.findingLine));
        ul.appendChild(li);
      });
      sec.appendChild(ul);
      file.appendChild(sec);
    });
  }

  function render() {
    renderRail(state.finished ? LAB.phases.length : phaseIndexOf(current().step));
    document.getElementById("step-view").hidden = state.finished;
    document.getElementById("done-view").hidden = !state.finished;
    if (state.finished) renderDone(); else renderStep();
  }

  function hydrate(saved, meta) {
    var next = { stepIndex: 0, answerId: "", answerState: null, finished: false, misses: {}, submitted: {} };
    if (saved && typeof saved === "object") {
      if (typeof saved.stepIndex === "number" && saved.stepIndex >= 0 && saved.stepIndex < STEPS.length && saved.stepIndex % 1 === 0) next.stepIndex = saved.stepIndex;
      var step = STEPS[next.stepIndex].step;
      if (typeof saved.answerId === "string" && choiceById(step, saved.answerId)) next.answerId = saved.answerId;
      if (saved.answerState === "supported" && next.answerId === step.answerId) next.answerState = "supported";
      else if (saved.answerState === "unsupported" && next.answerId && next.answerId !== step.answerId) next.answerState = "unsupported";
      if (saved.finished === true) next.finished = true;
      STEPS.forEach(function (entry) {
        var id = entry.step.id;
        if (saved.misses && typeof saved.misses[id] === "number" && saved.misses[id] > 0) next.misses[id] = Math.floor(saved.misses[id]);
        if (saved.submitted && saved.submitted[id] === true) next.submitted[id] = true;
      });
    }
    state = next;
    completedOnce = !!(meta && meta.completed);
    render();
  }

  document.getElementById("lab-eyebrow").textContent = LAB.eyebrow;
  document.getElementById("lab-title").textContent = LAB.title;
  document.getElementById("lab-instruction").textContent = LAB.instruction;
  document.getElementById("case-title").textContent = LAB.caseTitle;
  document.getElementById("case-body").textContent = LAB.caseBody;
  document.getElementById("artifact-title").textContent = LAB.artifactTitle;
  document.getElementById("artifact-intro").textContent = LAB.artifactIntro;
  commitBtn.addEventListener("click", checkAnswer);
  nextBtn.addEventListener("click", continueFromAnswer);
  document.getElementById("rebuild").addEventListener("click", restart);

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var restored = null;
    try { restored = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) {}
    hydrate(restored, { completed: false });
  }
</script>
</body>
</html>
