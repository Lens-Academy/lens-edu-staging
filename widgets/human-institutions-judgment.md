---
id: '9d441097-a5d4-4251-95f2-c7890b443a97'
title: Audit the verifier
summary_for_tutor: "XLab's Audit the verifier lab (case file: the International AI Verification Office examining Project Lattice, where two engineers report a concealed run approved after a safety warning, authenticated messages and power records corroborate parts of it, the developer withholds scheduler logs and chip inventory, and only a council can sanction). The learner works through fourteen decisions in four phases (Institution: independence, competence, accountability, authority, access; Capture: financial, informational, cultural, political; Evidence boundary: human record, operational fact; Response: investigation, compliance finding, enforcement). Each decision offers four lines in a seeded order; the learner selects one and commits it. A wrong line shows Not supported by this record with a retry hint and the learner chooses again; the supported line shows an explanation and a source link (Brundage et al., Wasil et al., Baker et al., OPCW) and unlocks the next decision. After the fourteenth decision the learner assembles the completed file: the Institutional assessment and response record, listing the fourteen finding lines by phase. The widget is complete when the file is assembled; the first commit on each decision is scored. The saved summary reports the current decision, the committed line, and which decisions needed unsupported commits."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Audit the verifier</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-institutions-judgment". -->
<!-- Shared engine: XLab's human-policy-decision-lab (src/components/verification/widgets/human-policy-decision-lab.tsx) with the INSTITUTIONS_JUDGMENT_LAB data from src/lib/verification/data/human-policy-labs.ts inlined below. -->
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
  // Data: verbatim from XLab's human-policy-labs.ts (INSTITUTIONS_JUDGMENT_LAB), em dashes replaced.
  var LAB = {
    "id": "institutions-judgment",
    "eyebrow": "Institutions and policy judgment · 2.4.4",
    "title": "Audit the verifier",
    "instruction": "Inspect the institution before relying on its finding. Then separate what the human record establishes from what still requires technical or physical evidence, and match each decision to its legal and evidentiary threshold.",
    "caseTitle": "The International AI Verification Office",
    "caseBody": "The Office is examining Project Lattice. Two engineers independently report that management approved a concealed run after receiving a safety warning. Authenticated messages show the warning reached the relevant executives. Power and procurement records corroborate the project code and dates. The developer refuses raw scheduler logs and chip inventory, although the treaty mandate expressly requires both. A council (not the Office) has authority to impose sanctions.",
    "artifactTitle": "Institutional assessment and response record",
    "artifactIntro": "The record identifies institutional weaknesses, names the mechanism of capture, preserves the boundary between organizational and operational facts, and assigns separate decisions to investigation, compliance, and enforcement.",
    "phases": [
      {
        "id": "institution",
        "label": "Institution",
        "steps": [
          {
            "id": "independence",
            "label": "Independence",
            "prompt": "What makes this audit arrangement insufficiently independent?",
            "context": "The developer selects the audit provider from an unrestricted list, negotiates the scope, pays a renewable annual fee, and may block publication by ending the engagement.",
            "choices": [
              {
                "id": "commercial-dependence",
                "text": "The provider's future income, scope, and ability to publish depend on the auditee whose claims it must test."
              },
              {
                "id": "formal-third-party",
                "text": "Independence is adequate because the provider is legally incorporated separately from the developer."
              },
              {
                "id": "expertise-cures",
                "text": "Technical expertise cures the financial and publication conflict because a capable auditor will recognize manipulation."
              },
              {
                "id": "disclose-after",
                "text": "The conflict is immaterial if the provider discloses the payment relationship after publishing a favorable report."
              }
            ],
            "answerId": "commercial-dependence",
            "retry": "Ask what happens to fees, access, scope, and publication when the auditor reaches an unwelcome conclusion.",
            "explanation": "Brundage et al. call for disclosed financial relationships, standardized terms that prevent auditor shopping, cooling-off periods, and payment models that reduce dependence on auditees.",
            "sourceLabel": "Brundage et al., Independent experts",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Independence: deficient when the auditee controls selection, renewal, scope, or publication and an unfavorable finding threatens future income."
          },
          {
            "id": "competence",
            "label": "Competence",
            "prompt": "What competence does the Project Lattice inquiry require?",
            "context": "The assigned team consists entirely of model evaluators. It has no compute-accounting, data-center, forensic interviewing, evidence-handling, or treaty-law expertise.",
            "choices": [
              {
                "id": "multidisciplinary-gap",
                "text": "The team cannot credibly resolve the inquiry without adding the disciplines needed to interpret infrastructure, records, interviews, evidence integrity, and the governing obligation."
              },
              {
                "id": "model-eval-enough",
                "text": "Model-evaluation expertise is sufficient because every frontier-AI compliance question ultimately concerns model behavior."
              },
              {
                "id": "lawyers-only",
                "text": "Treaty lawyers can resolve the factual dispute from the text of the access obligation without technical or investigative specialists."
              },
              {
                "id": "hire-after",
                "text": "Specialist competence matters only after the Office has already issued its factual finding and needs to defend it on appeal."
              }
            ],
            "answerId": "multidisciplinary-gap",
            "retry": "List the factual and legal questions in the case, then ask whether one discipline can answer all of them.",
            "explanation": "Brundage et al. recommend multidisciplinary teams, subcontracting, or consortia when one audit organization lacks the required breadth.",
            "sourceLabel": "Brundage et al., Independent experts",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Competence: must match the claim across AI evaluation, compute and facility operations, investigation, evidence handling, security, and law."
          },
          {
            "id": "accountability",
            "label": "Accountability",
            "prompt": "Which arrangement makes the Office accountable without giving the auditee a veto?",
            "choices": [
              {
                "id": "review-without-veto",
                "text": "Disclose methods and conflicts where possible, keep a traceable case file, use independent quality review, and allow correction of factual errors without permitting suppression of conclusions."
              },
              {
                "id": "secret-no-review",
                "text": "Keep methods, conflicts, and quality controls secret because any external review would compromise sensitive information."
              },
              {
                "id": "auditee-approval",
                "text": "Require the developer to approve the final wording so procedural fairness prevents reputational harm."
              },
              {
                "id": "public-raw",
                "text": "Publish every raw record and source identity so the public can reproduce the investigation without relying on institutional review."
              }
            ],
            "answerId": "review-without-veto",
            "retry": "Accountability needs traceability, quality control, and correction of error; it does not require either total secrecy or auditee control.",
            "explanation": "Brundage et al. pair rigorous, traceable methods with procedural fairness: companies may correct factual errors but should not exert undue influence over conclusions.",
            "sourceLabel": "Brundage et al., Rigor and Clarity",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Accountability: requires traceable methods, conflict disclosure, independent quality review, and a factual-correction process that does not become a publication veto."
          },
          {
            "id": "authority",
            "label": "Authority",
            "prompt": "What does the Office's authority permit it to do?",
            "context": "The treaty authorizes the Office to compel records, conduct inspections, and issue compliance findings. Only the council may impose sanctions.",
            "choices": [
              {
                "id": "split-authority",
                "text": "The Office may investigate and make the authorized compliance finding; enforcement requires a separate council decision under the treaty."
              },
              {
                "id": "office-sanctions",
                "text": "Any institution able to obtain evidence has inherent authority to impose proportionate sanctions without a council decision."
              },
              {
                "id": "no-finding",
                "text": "Because it cannot sanction, the Office may collect evidence but cannot issue a compliance finding."
              },
              {
                "id": "council-investigates",
                "text": "The council's enforcement authority makes the Office's investigative mandate unnecessary; the council should determine the facts itself."
              }
            ],
            "answerId": "split-authority",
            "retry": "Separate collection and assessment, the compliance judgment, and the institution authorized to order a response.",
            "explanation": "Wasil et al. identify institutional powers and handling noncompliance as separate design questions. Evidence access does not create enforcement authority by implication.",
            "sourceLabel": "Wasil et al., Future directions",
            "sourceHref": "https://arxiv.org/html/2408.16074v2#S1.SS2",
            "findingLine": "Authority: the Office may compel, investigate, and find compliance only as the treaty provides; sanctions remain with the council."
          },
          {
            "id": "access",
            "label": "Access",
            "prompt": "What does the current access condition do to the Office's finding?",
            "context": "Management supplies summaries and selected interviewees but withholds raw scheduler logs, chip inventory, and private staff contact.",
            "choices": [
              {
                "id": "access-caps-finding",
                "text": "It caps the substantive finding because the auditee controls the evidentiary frame and the operational facts cannot be checked directly."
              },
              {
                "id": "summaries-sufficient",
                "text": "It provides deep access because the summaries cover every category named in the mandate."
              },
              {
                "id": "cooperation-signal",
                "text": "It supports a favorable finding because supplying any non-public information demonstrates good-faith cooperation."
              },
              {
                "id": "human-replaces-logs",
                "text": "It has no effect because interviews can substitute for scheduler logs and inventory in proving the workload and compute threshold."
              }
            ],
            "answerId": "access-caps-finding",
            "retry": "Formal authority is not actual access. Ask who selected the evidence and whether the disputed operational fact can be checked from it.",
            "explanation": "Brundage et al. distinguish independent status from access adequate to support the claim. Company-selected summaries and interviewees leave an informational dependency intact.",
            "sourceLabel": "Brundage et al., §§2 and 5.3",
            "sourceHref": "https://arxiv.org/html/2601.11699v4#S5.SS3",
            "findingLine": "Access: management-selected summaries and interviewees do not support a deep finding when raw operational evidence and private contact are withheld."
          }
        ]
      },
      {
        "id": "capture",
        "label": "Capture",
        "steps": [
          {
            "id": "financial-capture",
            "label": "Financial",
            "prompt": "Which fact is financial capture?",
            "choices": [
              {
                "id": "renewal-fee",
                "text": "A favorable result protects a renewable auditee-paid fee and future engagements."
              },
              {
                "id": "curated-records",
                "text": "Management chooses the records and interviewees that define the inquiry."
              },
              {
                "id": "normal-assumptions",
                "text": "Staff adopt the developer's view of which safety problems are normal and not worth escalating."
              },
              {
                "id": "minister-delay",
                "text": "A minister delays publication to protect a diplomatic agreement."
              }
            ],
            "answerId": "renewal-fee",
            "retry": "Identify the pressure operating through money and future work.",
            "explanation": "Financial capture changes the verifier's incentives through fees, renewal, funding, appointment, or future employment.",
            "sourceLabel": "Brundage et al., Independent experts",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Financial capture: revenue or future work depends on avoiding a finding that displeases the auditee or funder."
          },
          {
            "id": "informational-capture",
            "label": "Informational",
            "prompt": "Which fact is informational capture?",
            "choices": [
              {
                "id": "curated-records",
                "text": "Management chooses the records, systems, interviewees, and initial questions that define what the verifier can see."
              },
              {
                "id": "renewal-fee",
                "text": "The provider relies on a renewable fee from the audited company."
              },
              {
                "id": "shared-culture",
                "text": "Inspectors come to regard the developer's risk tolerance as the natural professional baseline."
              },
              {
                "id": "foreign-policy",
                "text": "The government suppresses a finding that could damage its strategic relationship with another state."
              }
            ],
            "answerId": "curated-records",
            "retry": "Look for control over the facts, questions, and people entering the evidentiary frame.",
            "explanation": "Informational capture persists even when the verifier is formally outside the company: the regulated party can still determine what becomes knowable.",
            "sourceLabel": "Brundage et al., Access and Independence",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Informational capture: the auditee controls the evidentiary frame by selecting records, systems, interviewees, and questions."
          },
          {
            "id": "cultural-capture",
            "label": "Cultural",
            "prompt": "Which fact is cultural capture?",
            "choices": [
              {
                "id": "adopted-baseline",
                "text": "Through repeated staffing exchanges and socialization, the verifier adopts the developer's assumptions about what counts as normal, serious, or worth investigating."
              },
              {
                "id": "record-selection",
                "text": "The developer withholds raw logs and offers a summary instead."
              },
              {
                "id": "budget-cut",
                "text": "The auditee threatens to move its paid engagement to another provider."
              },
              {
                "id": "cabinet-order",
                "text": "The cabinet orders the Office to avoid a finding during treaty negotiations."
              }
            ],
            "answerId": "adopted-baseline",
            "retry": "Cultural capture changes the verifier's professional frame, not only its access, funding, or formal instructions.",
            "explanation": "A verifier can remain formally independent while internalizing the regulated organization's categories, urgency, and tolerance for weak evidence.",
            "sourceLabel": "Brundage et al., §§4.1 and 5",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Cultural capture: the institution internalizes the auditee's assumptions about normal practice and the seriousness of possible failure."
          },
          {
            "id": "political-capture",
            "label": "Political",
            "prompt": "Which fact is political capture?",
            "choices": [
              {
                "id": "minister-suppression",
                "text": "A minister narrows or delays the finding to protect a government, company, or diplomatic relationship."
              },
              {
                "id": "staff-norms",
                "text": "Inspectors absorb the developer's professional norms through repeated collaboration."
              },
              {
                "id": "fee-pressure",
                "text": "A provider fears losing an annual audit fee after an adverse conclusion."
              },
              {
                "id": "evidence-menu",
                "text": "Management chooses which documents the investigators may inspect."
              }
            ],
            "answerId": "minister-suppression",
            "retry": "Identify direct pressure serving governmental or diplomatic interests.",
            "explanation": "Political capture operates through appointment, direction, delay, scope restriction, or suppression for political rather than evidentiary reasons.",
            "sourceLabel": "Brundage et al., Independent experts",
            "sourceHref": "https://arxiv.org/html/2601.11699v4",
            "findingLine": "Political capture: officials alter scope, timing, or conclusions to protect governmental, corporate, or diplomatic interests."
          }
        ]
      },
      {
        "id": "evidence",
        "label": "Evidence boundary",
        "steps": [
          {
            "id": "human-establishes",
            "label": "Human record",
            "prompt": "What can the human and documentary record establish here?",
            "context": "The engineers had access to the decision process, gave independent accounts, and produced authenticated contemporaneous messages showing the warning reached the executives.",
            "choices": [
              {
                "id": "knowledge-authorization",
                "text": "That the warning reached the named executives and that management discussed or authorized the project as the messages record, subject to the defined people and period."
              },
              {
                "id": "exact-compute",
                "text": "The exact compute used by the workload, because the engineers participated in the decision process."
              },
              {
                "id": "all-implementation",
                "text": "That every operational instruction was carried out exactly as authorized, because the approval record is authenticated."
              },
              {
                "id": "no-hidden-activity",
                "text": "That no other concealed project existed, because two sources independently described Project Lattice."
              }
            ],
            "answerId": "knowledge-authorization",
            "retry": "Human evidence is strongest on organizational knowledge, decision, warning, staging, and intent, not automatic proof of machine activity.",
            "explanation": "Baker et al. map personnel to the violations they can observe while emphasizing compartmentalization and collusion. Authentication and independent accounts support the organizational fact, not facts outside those sources' access.",
            "sourceLabel": "Baker et al., §4.3",
            "sourceHref": "https://arxiv.org/html/2507.15916#S4.SS3",
            "findingLine": "Human-mechanism finding: authenticated messages and independent sources can establish who received the warning and what management decided within the observed process."
          },
          {
            "id": "technical-required",
            "label": "Operational fact",
            "prompt": "What still requires technical or physical evidence?",
            "choices": [
              {
                "id": "workload-threshold",
                "text": "Whether the run occurred as described, which workload executed, which chips participated, and whether total compute crossed the treaty threshold."
              },
              {
                "id": "executive-received",
                "text": "Whether the executives received the warning shown in their authenticated message thread."
              },
              {
                "id": "source-role",
                "text": "Whether the engineers held the roles confirmed by personnel and access records."
              },
              {
                "id": "retaliation-threat",
                "text": "Whether a manager threatened a reporter in a recorded meeting corroborated by an independent witness."
              }
            ],
            "answerId": "workload-threshold",
            "retry": "Separate the organizational decision from execution, hardware participation, workload identity, and measured compute.",
            "explanation": "Wasil et al. require facility access, chip identifiers, activity logs, training records, and related technical measures to test operational AI-development claims. Human evidence can direct that inquiry but not replace it.",
            "sourceLabel": "Wasil et al., Access-dependent methods",
            "sourceHref": "https://arxiv.org/html/2408.16074v2#S6.SS2",
            "findingLine": "Technical/physical requirement: scheduler and activity logs, chip inventory, and facility evidence must establish execution, workload identity, participating hardware, and compute."
          }
        ]
      },
      {
        "id": "response",
        "label": "Response",
        "steps": [
          {
            "id": "investigation-threshold",
            "label": "Investigation",
            "prompt": "What decision is supported before the withheld logs are obtained?",
            "choices": [
              {
                "id": "open-investigation",
                "text": "Open or continue a focused investigation and preserve evidence: the concern is specific, plausible, partly corroborated, and points to records capable of resolving it."
              },
              {
                "id": "substantive-compliance",
                "text": "Find the training prohibition violated because the sources and power record together prove the workload and compute threshold."
              },
              {
                "id": "enforce-now",
                "text": "Impose sanctions immediately because delay would reward concealment, even though the council has not acted and the operational fact is unresolved."
              },
              {
                "id": "close-case",
                "text": "Close the matter because evidence insufficient for enforcement is necessarily insufficient for investigation."
              }
            ],
            "answerId": "open-investigation",
            "retry": "The investigation threshold is intentionally lower than the compliance and enforcement thresholds.",
            "explanation": "A specific corroborated allegation with an identifiable evidence path justifies preservation and investigation before the evidence supports a final substantive judgment.",
            "sourceLabel": "Baker et al., personnel layer; Wasil et al.",
            "sourceHref": "https://arxiv.org/html/2507.15916#S4.SS3",
            "findingLine": "Investigation: justified by a specific, plausible, partly corroborated concern and a realistic path to resolving evidence."
          },
          {
            "id": "compliance-threshold",
            "label": "Compliance finding",
            "prompt": "What compliance finding does the documented refusal support?",
            "context": "The treaty expressly requires scheduler logs and chip inventory. The Office issued a valid demand, offered managed access, and the deadline expired without production.",
            "choices": [
              {
                "id": "access-breach",
                "text": "Find breach of the access and cooperation obligation, while recording that the underlying training-run allegation remains a separate unresolved question."
              },
              {
                "id": "run-proved",
                "text": "Find both the access breach and the prohibited run proved because refusal necessarily means the logs are incriminating."
              },
              {
                "id": "no-finding-until-run",
                "text": "Issue no compliance finding until the Office proves the underlying run; access duties cannot be breached independently."
              },
              {
                "id": "office-sanction",
                "text": "Treat the access finding as the Office's authority to impose whatever enforcement measure it considers proportionate."
              }
            ],
            "answerId": "access-breach",
            "retry": "Identify the obligation whose facts are already established, and keep it separate from the concealed conduct the records were meant to test.",
            "explanation": "A valid demand, an express duty, managed alternatives, and documented refusal can establish noncompliance with access. Whether refusal proves the underlying activity depends on a separate inference rule in the agreement.",
            "sourceLabel": "OPCW managed-access precedent; Wasil et al.",
            "sourceHref": "https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant",
            "findingLine": "Compliance finding: the documented refusal establishes breach of the express access duty; it does not by itself establish the prohibited run."
          },
          {
            "id": "enforcement-threshold",
            "label": "Enforcement",
            "prompt": "When is enforcement justified?",
            "choices": [
              {
                "id": "authority-process",
                "text": "When an authorized trigger or valid compliance finding exists and the council applies the treaty's authority, required process, proportionality, and urgency rules."
              },
              {
                "id": "strong-suspicion",
                "text": "Whenever investigators hold a strong suspicion, even if the treaty assigns sanctions elsewhere and no compliance process has concluded."
              },
              {
                "id": "auditor-recommends",
                "text": "Whenever an independent auditor recommends sanctions, because independence supplies enforcement authority."
              },
              {
                "id": "automatic-maximum",
                "text": "Automatically at the maximum level after any access delay so that enforcement remains deterrent."
              }
            ],
            "answerId": "authority-process",
            "retry": "Evidence strength, legal authority, decision process, and proportionality are separate conditions for enforcement.",
            "explanation": "Wasil et al. identify institutional powers, handling noncompliance, and proportionate enforcement as distinct design questions. A verifier's finding can trigger but does not itself create the authorized response.",
            "sourceLabel": "Wasil et al., Future directions",
            "sourceHref": "https://arxiv.org/html/2408.16074v2#S1.SS2",
            "findingLine": "Enforcement: requires an authorized trigger or valid finding, the designated decision-maker, required process, and a proportionate response, not suspicion alone."
          }
        ]
      }
    ]
  };

  var STORAGE_KEY = "xlab-human-institutions-judgment:v1";
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
