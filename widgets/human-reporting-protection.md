---
id: 'f20e4063-78a2-49cd-9066-97458c1d93cf'
title: Follow the report
summary_for_tutor: "Follow the report: an assembly exercise in two cases. Case 1 (Protection route) is Nadia, a frontier-developer safety engineer who reports a biological-risk deployment directly to the California Attorney General under SB 53 despite a broad NDA; the six links are Person, Subject, Recipient, Identity protection, NDA and remedy, Competent investigator. Case 2 (Evidence path) is a cooling contractor who emails a verifier a work order (Project Lattice, code PX-814, 1,024 accelerators over six weeks) matched by a utility allocation record; the six links are Preserve, Authenticate, Investigate, Corroborate, Package, Pass on. For each case the learner sees a bank of twelve statements (one correct and one decoy per link), picks a statement, places it on a link, then presses Check the route. Wrong links show a retry hint and can be taken back; correct links show the explanation and its source (California Labor Code 1107 to 1107.2, the AIWI/CARMA guide and SB 53 commentary, CIGIE Quality Standards for Investigations, Wasil et al., Baker et al. Table 14). When all six hold, the assembled finding appears: Case 1 ends with the legal route existing but identity protection and the office's competence unresolved; Case 2 ends with usable evidence for a bounded claim only (the expansion, not the workload). Done means both findings are recorded and the closing view shows the two thresholds: a statute can protect person, subject and recipient while leaving identity, competence or authority unresolved, and corroborated records can support one fact without proving the larger allegation. Content ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Follow the report</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-reporting-protection". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .frame { border: 1px solid var(--border); border-radius: 8px; background: #fff; overflow: hidden; }
  .head { border-bottom: 1px solid var(--border); padding: 16px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .eyebrow.accent { color: var(--accent); }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 26px; margin: 6px 0 0; }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 6px 0 0; }
  h3 { font-family: var(--font-heading); font-weight: 600; font-size: 17px; margin: 0; }
  h4 { font-weight: 600; font-size: 14px; margin: 10px 0 0; }
  p { margin: 0; }
  .lede, .muted { color: var(--muted); }
  .lede { margin-top: 8px; max-width: 46rem; }
  .rail { list-style: none; margin: 16px 0 0; padding: 0; display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 8px; }
  .rail li { border: 1px solid var(--border); border-radius: 6px; padding: 6px 4px; text-align: center; font-size: 10px; letter-spacing: 0.06em; text-transform: uppercase; color: var(--muted); }
  .rail li.is-active { border-color: var(--accent); color: var(--text); background: var(--surface); font-weight: 600; }
  .rail li.is-past { background: var(--surface); color: var(--text); }
  .section { padding: 16px; }
  .section + .section { border-top: 1px solid var(--border); }
  .between { display: flex; flex-wrap: wrap; gap: 4px 16px; align-items: baseline; justify-content: space-between; }
  .small { font-size: 12px; }
  ol.route { list-style: none; margin: 12px 0 0; padding: 0; display: grid; gap: 8px; }
  .link { border: 1px solid var(--border); border-radius: 8px; background: #fff; }
  .link.is-right { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .link.is-wrong { border-color: var(--text); border-style: dashed; }
  .link-main { display: flex; gap: 12px; padding: 12px; align-items: flex-start; }
  .num { flex: none; width: 28px; height: 28px; border: 1px solid var(--border); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 12px; color: var(--muted); }
  .link-body { flex: 1; min-width: 0; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.55; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button.placed { display: block; width: 100%; margin-top: 4px; border-color: transparent; padding: 4px 0; }
  button.placed:hover { background: var(--surface); }
  button.placed .hint { display: block; font-size: 11px; color: var(--muted); margin-top: 2px; }
  button.slot { display: block; width: 100%; margin-top: 4px; border-style: dashed; color: var(--muted); font-size: 13px; }
  button.slot.is-ready { border-color: var(--accent); color: var(--accent); font-weight: 600; }
  .verdict { border-top: 1px solid var(--border); padding: 8px 12px; font-size: 12px; color: var(--muted); }
  .verdict .tag { font-weight: 600; color: var(--text); margin-right: 6px; }
  .verdict.is-right .tag { color: var(--accent); }
  .verdict a { display: inline-block; margin-top: 4px; color: var(--accent); font-weight: 600; text-decoration: underline; text-underline-offset: 3px; }
  .bank { display: grid; gap: 8px; margin-top: 12px; }
  button.statement { width: 100%; padding: 10px 14px; }
  button.statement.is-held { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: var(--surface); }
  button.statement.is-held::before { content: "\2713\00a0"; color: var(--accent); font-weight: 600; }
  .notice { margin-top: 16px; border: 1px dashed var(--text); border-radius: 8px; padding: 12px 14px; }
  .notice p:first-child { font-weight: 600; }
  .foot { display: flex; justify-content: flex-end; margin-top: 20px; }
  .finding { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--surface); }
  .pill { display: inline-block; margin-top: 12px; border: 1px solid var(--border); border-radius: 999px; padding: 4px 12px; font-size: 12px; font-weight: 600; background: #fff; }
  .lines { display: grid; gap: 8px; margin-top: 16px; }
  .line { border: 1px solid var(--border); border-radius: 8px; padding: 10px 14px; }
  .line .tag { color: var(--accent); font-weight: 600; margin-right: 6px; }
  .line b { font-weight: 600; }
  .two { display: grid; gap: 12px; grid-template-columns: repeat(2, minmax(0, 1fr)); margin-top: 16px; }
  .two .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; }
  .two .card h3 { margin-top: 0; }
  .two .card p { margin-top: 8px; color: var(--muted); }
  .big { font-size: 24px; color: var(--accent); }
  @media (max-width: 600px) {
    .two { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="frame">
  <header class="head">
    <p class="eyebrow">Reporting and protection · 2.4.2</p>
    <h1>Follow the report</h1>
    <p class="lede">Reconstruct one route out of the organization and one route from allegation to usable evidence. Every statement in the bank belongs to at most one link, and half of them belong to none.</p>
    <ol class="rail" id="rail" aria-label="Exercise progress"></ol>
  </header>
  <div id="main"></div>
</div>

<script>
  // Data copied verbatim from XLab's src/lib/verification/data/human-reporting-protection.ts
  // (the bank uses, as in XLab, the correct statement and the first decoy of each step).
  var CALIFORNIA_LABOR_CODE = "https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=";
  var AIWI_GUIDE = "https://aiwi.org/ai-whistleblowing-law-best-practice/";
  var AIWI_SB53 = "https://aiwi.org/publication-commentary-whistleblower-protections-in-sb-53/";
  var CIGIE_QSI = "https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf#page=13";
  var WASIL = "https://arxiv.org/html/2408.16074";

  var CASES = [
    {
      id: "protected-route",
      eyebrow: "Case 1 · Protection route",
      title: "A safety engineer reports to the Attorney General",
      body: "Nadia is employed by a frontier developer. Her assigned work includes assessing and managing risks of critical safety incidents. She has reasonable cause to believe a planned deployment could materially contribute to more than 50 deaths by providing expert assistance for the release of a biological agent. She reports directly to the California Attorney General. Nadia signed a broad NDA. The external intake route states no anonymity or confidentiality guarantee, and no technical AI specialist has yet been assigned.",
      steps: [
        {
          id: "person",
          label: "Person",
          choices: [
            { id: "assigned-safety-role", text: "Her assigned responsibility for critical-safety-incident risk places her within the chapter's definition of a covered employee." },
            { id: "all-frontier-staff", text: "Every employee of a frontier developer is a covered employee for every report about model safety." }
          ],
          answerId: "assigned-safety-role",
          retry: "Use the job responsibility in §1107(b), not the person's seniority, employer alone, or the recipient's later decision.",
          explanation: "Section 1107(b) ties covered-employee status to responsibility for assessing, managing, or addressing risk of critical safety incidents. Nadia's assigned work meets that definition on the facts given.",
          sourceLabel: "California Labor Code §1107(b)",
          sourceHref: CALIFORNIA_LABOR_CODE,
          findingLine: "Person: Nadia is a covered employee because critical-safety-incident risk is part of her assigned work."
        },
        {
          id: "subject",
          label: "Subject",
          choices: [
            { id: "defined-catastrophic-risk", text: "Her reasonable-cause report describes a specific and substantial public danger arising from a catastrophic risk defined by the chapter." },
            { id: "incident-only", text: "The chapter protects only reports made after deaths, injuries, or property losses have already occurred." }
          ],
          answerId: "defined-catastrophic-risk",
          retry: "Apply both parts of the rule: reasonable cause and a subject within §1107.1(a). The scenario supplies the chapter's scale and biological-risk pathway.",
          explanation: "Section 1107.1(a)(1) covers a reasonable-cause disclosure of a specific and substantial public danger resulting from catastrophic risk. Section 1107(a) supplies the scale and listed pathways.",
          sourceLabel: "California Labor Code §§1107(a), 1107.1(a)(1)",
          sourceHref: CALIFORNIA_LABOR_CODE,
          findingLine: "Subject: The reported biological-risk pathway and scale fall within the chapter's catastrophic-risk route."
        },
        {
          id: "recipient",
          label: "Recipient",
          choices: [
            { id: "direct-ag-route", text: "No. The Attorney General is an expressly named recipient, and §1107.1 does not make internal reporting a prerequisite." },
            { id: "internal-first", text: "Yes. Protection begins only after the developer has received the report and missed a response deadline." }
          ],
          answerId: "direct-ag-route",
          retry: "Read the recipient list in §1107.1(a). The internal process is an additional route, not a gate in front of the Attorney General.",
          explanation: "The Attorney General is named in §1107.1(a). The chapter also names specified internal recipients and a federal authority, but it does not require Nadia to use an internal channel first.",
          sourceLabel: "California Labor Code §1107.1(a), (c), and (e)",
          sourceHref: CALIFORNIA_LABOR_CODE,
          findingLine: "Recipient: Nadia may report directly to the Attorney General without first reporting to the developer."
        },
        {
          id: "identity",
          label: "Identity protection",
          choices: [
            { id: "external-gap", text: "SB 53 requires an anonymous internal process for large developers, but the chapter does not itself require the external Attorney General route to be anonymous or confidential." },
            { id: "all-routes-anonymous", text: "Every recipient named in §1107.1(a) must accept the report anonymously and may never learn the reporter's identity." }
          ],
          answerId: "external-gap",
          retry: "Separate the anonymous internal process in §1107.1(e) from the external recipients in §1107.1(a). The AIWI/CARMA guide asks for both anonymity and confidentiality externally because the chapter does not specify them.",
          explanation: "The chapter requires an anonymous internal process at a large frontier developer. It does not impose an express anonymity or confidentiality rule on the external Attorney General route. AIWI/CARMA recommend both for receiving authorities.",
          sourceLabel: "California Labor Code §1107.1(e); AIWI/CARMA, Disclosure Channels and Agency Requirements",
          sourceHref: AIWI_GUIDE,
          findingLine: "Identity protection: The external route is legally available, but SB 53 does not itself supply the anonymity and confidentiality guarantees recommended by AIWI/CARMA."
        },
        {
          id: "remedy",
          label: "NDA and remedy",
          choices: [
            { id: "scoped-contract-protection", text: "The developer may not use the contract to prevent this protected disclosure or retaliate for it; the chapter supplies fees, burden shifting, and possible injunctive relief." },
            { id: "nda-void-everywhere", text: "The NDA is void in full, including provisions unrelated to protected reporting and disclosures to recipients outside the statute." }
          ],
          answerId: "scoped-contract-protection",
          retry: "Keep the contract rule within the protected disclosure defined by the chapter, then read the remedies in §1107.1(f)–(i).",
          explanation: "Sections 1107.1(a) and (b) prevent specified contracts from blocking protected disclosures. The chapter also provides attorney's fees, shifts the burden after a contributing-factor showing, and authorizes temporary or preliminary injunctive relief.",
          sourceLabel: "California Labor Code §1107.1(a), (b), and (f)–(i)",
          sourceHref: CALIFORNIA_LABOR_CODE,
          findingLine: "NDA and remedy: The contract cannot block this protected report; retaliation can trigger fees, burden shifting, and injunctive relief."
        },
        {
          id: "investigator",
          label: "Competent investigator",
          choices: [
            { id: "recipient-not-capacity", text: "It establishes a protected destination, not that the office already has the technical expertise or a clear mandate to resolve a catastrophic-risk report without a legal violation." },
            { id: "recipient-proves-capacity", text: "It establishes that the office has sufficient AI expertise, investigative access, and authority for every report within the chapter." }
          ],
          answerId: "recipient-not-capacity",
          retry: "A legally permitted recipient, a protected identity, and an institution able to investigate are separate design questions.",
          explanation: "AIWI/CARMA recommend that receiving agencies have or can obtain technical AI expertise. Their SB 53 analysis separately identifies uncertainty about the Attorney General's mandate where the report alleges catastrophic risk but no legal violation.",
          sourceLabel: "AIWI/CARMA, Agency Requirements; Whistleblower Protections in SB 53, Executive Summary",
          sourceHref: AIWI_SB53,
          findingLine: "Competent investigator: The Attorney General is a protected recipient, but expertise and authority to act still require institutional design."
        }
      ],
      resultTitle: "The legal route exists, but the protection chain is incomplete",
      result: "Nadia fits the covered-person definition, the subject falls within the catastrophic-risk route, the Attorney General is an authorized recipient, and the NDA cannot block this protected disclosure. The first unresolved condition is identity protection on the external route. The office's technical competence and authority to act are a second unresolved condition.",
      breakLabel: "First unresolved condition · identity protection"
    },
    {
      id: "evidence-path",
      eyebrow: "Case 2 · Evidence path",
      title: "A contractor supplies a work order",
      body: "An independent cooling contractor emails a verifier an original work order showing that Project Lattice added capacity for 1,024 accelerators over six weeks. The attachment bears project code PX-814. A utility allocation record obtained separately contains the same code and dates. The contractor installed cooling equipment but had no access to cluster workloads or model records.",
      steps: [
        {
          id: "preserve",
          label: "Preserve",
          choices: [
            { id: "retain-original", text: "Retain the original message, attachment, and available metadata; open a case record; restrict and record access; and seek timely preservation of relevant records." },
            { id: "summary-only", text: "Copy the allegation into an intake summary and discard the original message so the reporter cannot later be identified from metadata." }
          ],
          answerId: "retain-original",
          retry: "Preservation comes before a merits decision. Keep the original submission and its context while limiting unnecessary exposure of the source.",
          explanation: "CIGIE requires accurate and complete case-file documentation and preservation of chain of custody. Early preservation protects records before routine deletion or deliberate alteration can remove them.",
          sourceLabel: "CIGIE Quality Standards for Investigations, Accurate and Complete Documentation; Collecting Evidence",
          sourceHref: CIGIE_QSI,
          findingLine: "Preserve: Keep the original submission and metadata, create the case record, log handling, and protect relevant records from loss."
        },
        {
          id: "authenticate",
          label: "Authenticate",
          choices: [
            { id: "provenance-not-truth", text: "It would test the contractor's claimed access and the work order's origin and integrity; it would not establish that an unauthorized workload ran." },
            { id: "reputation-authenticates", text: "A strong professional reputation would authenticate both the document and every inference the contractor draws from it." }
          ],
          answerId: "provenance-not-truth",
          retry: "Separate provenance and integrity from the truth of the allegation. A genuine work order can still be misunderstood or selectively presented.",
          explanation: "CIGIE requires investigators to verify the validity of information and evidence. Here that means testing role, access, origin, and integrity. Authentication does not prove what workload used the installed capacity.",
          sourceLabel: "CIGIE Quality Standards for Investigations, Collecting Evidence",
          sourceHref: CIGIE_QSI,
          findingLine: "Authenticate: Test the contractor's access and the document's provenance and integrity without treating authenticity as proof of the allegation."
        },
        {
          id: "investigate",
          label: "Investigate",
          choices: [
            { id: "test-both-directions", text: "Define the allegation and applicable rule, then lawfully pursue records and accounts that could support, qualify, or contradict it." },
            { id: "support-only", text: "Collect only material that supports the contractor because exculpatory evidence belongs in a later adversarial response." }
          ],
          answerId: "test-both-directions",
          retry: "The investigation tests an allegation. It is not a search for support for a conclusion already recorded.",
          explanation: "CIGIE requires objective collection and analysis of both exculpatory and incriminating evidence. Complaint evaluation also asks whether to investigate, refer, or take no further action under the office's authority and priorities.",
          sourceLabel: "CIGIE Quality Standards for Investigations, Complaint Evaluation; Executing Investigations",
          sourceHref: CIGIE_QSI,
          findingLine: "Investigate: Define the allegation and rule, then seek both supporting and contradictory evidence through lawful, independent methods."
        },
        {
          id: "corroborate",
          label: "Corroborate",
          choices: [
            { id: "expansion-only", text: "It independently supports the project code, dates, and capacity expansion; scheduler, lineage, access, and authorization records are still needed to identify the workload and its status." },
            { id: "workload-proved", text: "It proves that an unauthorized frontier-model training run consumed the added capacity during those dates." }
          ],
          answerId: "expansion-only",
          retry: "Match the independent record to the fact it can test. A power allocation can support an expansion without identifying the code or model that later used it.",
          explanation: "Wasil et al. describe financial records and inspections as ways to test whistleblower claims. Their corroborative value remains claim-specific. Baker's Table 14 likewise separates personnel who know about infrastructure from personnel who know about AI activity and authorization.",
          sourceLabel: "Wasil et al., comparison table; Baker et al., Appendix A.8, Table 14",
          sourceHref: WASIL,
          findingLine: "Corroborate: The utility record supports the expansion. Workload, model lineage, access, and authorization remain unestablished."
        },
        {
          id: "package",
          label: "Package",
          choices: [
            { id: "scoped-record", text: "The allegation, source-access limits, authenticated items, handling record, independent support, contradictions, unresolved questions, applicable rule, and identity restrictions." },
            { id: "conclusion-only", text: "Only the strongest bottom-line conclusion, because underlying contradictions and limits may confuse the decision-maker." }
          ],
          answerId: "scoped-record",
          retry: "A receiving verifier needs the evidence and its limits. CIGIE requires reports to be supported by the case file and to include relevant exculpatory and mitigating information.",
          explanation: "CIGIE requires accurate, complete, impartial reporting supported by case-file evidence. The package should preserve the distinction between what the source observed, what investigators established, and what remains unresolved.",
          sourceLabel: "CIGIE Quality Standards for Investigations, Reporting",
          sourceHref: CIGIE_QSI,
          findingLine: "Package: Send a supported, scoped record that includes provenance, handling, corroboration, contradictions, limits, and identity restrictions."
        },
        {
          id: "pass",
          label: "Pass on",
          choices: [
            { id: "documented-referral", text: "Refer the matter promptly to an appropriate authority, preserve the record and handling restrictions, document the transfer, and retain the scoped case history required by policy." },
            { id: "investigate-anyway", text: "Keep the matter and investigate it fully; receiving a protected report supplies any jurisdiction or access power the office lacks." }
          ],
          answerId: "documented-referral",
          retry: "Authority does not arise from intake. Referral must preserve the record, the source restrictions, and accountability for the transfer.",
          explanation: "CIGIE's complaint-evaluation standard expressly includes referral to another appropriate authority. Its documentation and information-management requirements continue to govern how the sending office records and protects the transfer.",
          sourceLabel: "CIGIE Quality Standards for Investigations, Complaint Evaluation; Managing Investigative Information",
          sourceHref: CIGIE_QSI,
          findingLine: "Pass on: Make a documented referral to a competent, authorized body without losing the record, its restrictions, or the history of handling."
        }
      ],
      resultTitle: "The report has become usable evidence, but only for a bounded claim",
      result: "The preserved and authenticated work order, independently matched to the utility record, supports the claim that Project Lattice expanded infrastructure at the stated time. It does not establish which workload ran or whether a rule was breached. The transmitted package must state that limit and identify the technical and governance records still required.",
      breakLabel: null
    }
  ];

  var FINAL = {
    eyebrow: "Two different thresholds",
    title: "The report can travel without proving the case",
    protection: {
      title: "Protection finding",
      text: "A statute can protect a person, subject, and recipient while leaving identity safeguards, technical competence, or authority unresolved."
    },
    evidence: {
      title: "Evidence finding",
      text: "Preserved and corroborated records may support one fact without supporting the larger allegation. The transmitted package must say exactly where that boundary lies."
    }
  };

  var PHASES = ["1 · Protection route", "2 · Evidence path", "3 · Findings"];
  var STORAGE_KEY = "v-human-reporting-protection:v1";

  // State. `held` is transient (a statement picked up but not yet placed) and is not saved.
  var caseIndex = 0;
  var placed = {};
  var checked = false;
  var showCaseResult = false;
  var finished = false;
  var held = null;
  var completedOnce = false;

  function currentCase() { return CASES[caseIndex]; }
  function isRight(caseFile, stepId, choiceId) {
    for (var i = 0; i < caseFile.steps.length; i++) {
      if (caseFile.steps[i].id === stepId) return caseFile.steps[i].answerId === choiceId;
    }
    return false;
  }
  function findStatement(caseFile, choiceId) {
    if (!choiceId) return null;
    for (var i = 0; i < caseFile.steps.length; i++) {
      var cs = caseFile.steps[i].choices;
      for (var j = 0; j < cs.length; j++) if (cs[j].id === choiceId) return cs[j];
    }
    return null;
  }
  // The bank: the correct statement and the first decoy of every step, in id order (as in XLab).
  function statementBank(caseFile) {
    var entries = [];
    caseFile.steps.forEach(function (step) {
      var right = null, decoy = null;
      step.choices.forEach(function (c) {
        if (c.id === step.answerId) { if (!right) right = c; }
        else if (!decoy) decoy = c;
      });
      entries.push(right, decoy);
    });
    return entries.sort(function (a, b) { return a.id < b.id ? -1 : a.id > b.id ? 1 : 0; });
  }
  function isFilled(caseFile) {
    return caseFile.steps.every(function (s) { return !!placed[s.id]; });
  }
  function isAllRight(caseFile) {
    return isFilled(caseFile) && caseFile.steps.every(function (s) { return isRight(caseFile, s.id, placed[s.id]); });
  }
  function wrongSteps(caseFile) {
    if (!checked) return [];
    return caseFile.steps.filter(function (s) { return placed[s.id] && !isRight(caseFile, s.id, placed[s.id]); });
  }

  function fill(stepId) {
    if (!held) return;
    var next = {};
    Object.keys(placed).forEach(function (slot) {
      var choice = placed[slot];
      if (slot !== stepId && choice !== held) next[slot] = choice;
    });
    next[stepId] = held;
    placed = next;
    held = null;
    checked = false;
    render();
    persist();
  }
  function clearSlot(stepId) {
    var next = {};
    Object.keys(placed).forEach(function (k) { if (k !== stepId) next[k] = placed[k]; });
    placed = next;
    checked = false;
    render();
    persist();
  }
  function continueFromResult() {
    if (caseIndex < CASES.length - 1) {
      caseIndex += 1;
      placed = {};
      held = null;
      checked = false;
      showCaseResult = false;
      render();
      persist();
      return;
    }
    finished = true;
    render();
    persist();
  }
  function restart() {
    caseIndex = 0;
    placed = {};
    held = null;
    checked = false;
    showCaseResult = false;
    finished = false;
    render();
    persist();
  }

  function summary() {
    if (finished) {
      return "The learner has completed both cases of Follow the report and recorded both findings: the protection finding (a statute can protect a person, subject, and recipient while leaving identity safeguards, technical competence, or authority unresolved) and the evidence finding (preserved and corroborated records may support one fact without supporting the larger allegation).";
    }
    var caseFile = currentCase();
    var parts = ["Follow the report, " + caseFile.eyebrow + " (" + caseFile.title + ")."];
    if (showCaseResult) {
      parts.push("All six links hold and the assembled finding is on screen: " + caseFile.resultTitle + ".");
      if (caseIndex > 0) parts.push("Case 1 was completed earlier.");
      return parts.join(" ");
    }
    var n = Object.keys(placed).length;
    parts.push(n + " of " + caseFile.steps.length + " links placed" + (checked ? ", route checked." : ", not yet checked."));
    caseFile.steps.forEach(function (step) {
      var st = findStatement(caseFile, placed[step.id]);
      var line = step.label + ": " + (st ? "\"" + st.text + "\"" : "empty");
      if (checked && st) line += isRight(caseFile, step.id, st.id) ? " (holds)" : " (does not hold; hint: " + step.retry + ")";
      parts.push(line);
    });
    if (caseIndex > 0) parts.push("Case 1 was completed earlier.");
    return parts.join(" ");
  }

  function persist() {
    var state = { caseIndex: caseIndex, placed: placed, checked: checked, showCaseResult: showCaseResult, finished: finished };
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (finished && !completedOnce) {
        completedOnce = true;
        Lens.complete();
      }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }

  var railEl = document.getElementById("rail");
  var mainEl = document.getElementById("main");

  function el(tag, cls, text) {
    var node = document.createElement(tag);
    if (cls) node.className = cls;
    if (text != null) node.textContent = text;
    return node;
  }
  function btn(text, cls, id, onClick) {
    var b = el("button", cls, text);
    b.type = "button";
    if (id) b.id = id;
    b.addEventListener("click", onClick);
    return b;
  }
  function clearNode(node) { while (node.firstChild) node.removeChild(node.firstChild); }

  function renderRail() {
    clearNode(railEl);
    var active = finished ? 2 : caseIndex;
    PHASES.forEach(function (label, index) {
      var li = el("li", null, (index < active ? "✓ " : "") + label);
      if (index === active) { li.classList.add("is-active"); li.setAttribute("aria-current", "step"); }
      if (index < active) li.classList.add("is-past");
      railEl.appendChild(li);
    });
  }

  function renderCaseWork(caseFile) {
    var wrap = el("div");
    var intro = el("section", "section");
    intro.appendChild(el("p", "eyebrow accent", caseFile.eyebrow));
    intro.appendChild(el("h2", null, caseFile.title));
    var body = el("p", "muted", caseFile.body);
    body.style.marginTop = "10px";
    intro.appendChild(body);
    wrap.appendChild(intro);

    var work = el("section", "section");
    var head = el("div", "between");
    head.appendChild(el("h3", null, "The route"));
    head.appendChild(el("p", "muted small", Object.keys(placed).length + " of " + caseFile.steps.length + " links placed"));
    work.appendChild(head);

    var wrong = wrongSteps(caseFile);
    var route = el("ol", "route");
    caseFile.steps.forEach(function (step, index) {
      var choiceId = placed[step.id];
      var statement = findStatement(caseFile, choiceId);
      var isWrong = wrong.some(function (s) { return s.id === step.id; });
      var right = checked && !!choiceId && isRight(caseFile, step.id, choiceId);
      var li = el("li");
      var box = el("div", "link" + (right ? " is-right" : "") + (isWrong ? " is-wrong" : ""));
      var main = el("div", "link-main");
      main.appendChild(el("span", "num", String(index + 1)));
      var lb = el("div", "link-body");
      lb.appendChild(el("p", "eyebrow", step.label));
      if (statement) {
        var placedBtn = btn(statement.text, "placed", "slot-" + step.id, function () { clearSlot(step.id); });
        placedBtn.setAttribute("aria-label", "Remove the statement placed on " + step.label);
        placedBtn.appendChild(el("span", "hint", "Press to take it back"));
        lb.appendChild(placedBtn);
      } else {
        var slot = btn(held ? "Place it here" : "Empty", "slot" + (held ? " is-ready" : ""), "slot-" + step.id, function () { fill(step.id); });
        slot.disabled = !held;
        lb.appendChild(slot);
      }
      main.appendChild(lb);
      box.appendChild(main);
      if (isWrong) {
        var v = el("div", "verdict");
        v.appendChild(el("span", "tag", "Does not hold."));
        v.appendChild(document.createTextNode(step.retry));
        box.appendChild(v);
      }
      if (right) {
        var v2 = el("div", "verdict is-right");
        v2.appendChild(el("span", "tag", "Holds."));
        v2.appendChild(document.createTextNode(step.explanation));
        v2.appendChild(el("br"));
        var a = el("a", null, step.sourceLabel + " ↗");
        a.href = step.sourceHref;
        a.target = "_blank";
        a.rel = "noopener";
        v2.appendChild(a);
        box.appendChild(v2);
      }
      li.appendChild(box);
      route.appendChild(li);
    });
    work.appendChild(route);

    var bankHead = el("div", "between");
    bankHead.style.marginTop = "24px";
    bankHead.appendChild(el("h3", null, "Statements"));
    bankHead.appendChild(el("p", "muted small", "Each belongs to at most one link. Half belong to none."));
    work.appendChild(bankHead);
    var used = {};
    Object.keys(placed).forEach(function (k) { used[placed[k]] = true; });
    var bank = el("div", "bank");
    statementBank(caseFile).forEach(function (entry) {
      if (used[entry.id]) return;
      var holding = held === entry.id;
      var b = btn(entry.text, "statement" + (holding ? " is-held" : ""), "statement-" + entry.id, function () {
        held = holding ? null : entry.id;
        render();
      });
      b.setAttribute("aria-pressed", holding ? "true" : "false");
      bank.appendChild(b);
    });
    work.appendChild(bank);

    var filled = isFilled(caseFile);
    var allRight = isAllRight(caseFile);
    if (checked && !allRight) {
      var notice = el("div", "notice");
      notice.setAttribute("role", "status");
      notice.appendChild(el("p", null, wrong.length === 1 ? "One link does not hold." : wrong.length + " links do not hold."));
      notice.appendChild(el("p", "muted", "Each is marked with what it got wrong. Press a placed statement to take it back."));
      work.appendChild(notice);
    }

    var foot = el("div", "foot");
    if (checked && allRight) {
      foot.appendChild(btn("Assemble finding →", "primary", "assemble", function () {
        showCaseResult = true;
        held = null;
        render();
        persist();
      }));
    } else {
      var check = btn("Check the route", "primary", "check", function () {
        if (!isFilled(currentCase())) return;
        checked = true;
        render();
        persist();
      });
      check.disabled = !filled;
      foot.appendChild(check);
    }
    work.appendChild(foot);
    wrap.appendChild(work);
    return wrap;
  }

  function renderCaseResult(caseFile) {
    var sec = el("section", "section");
    var box = el("div", "finding");
    box.appendChild(el("p", "big", caseFile.id === "protected-route" ? "🛡" : "📄"));
    box.appendChild(el("p", "eyebrow", "Assembled finding"));
    box.appendChild(el("h2", null, caseFile.resultTitle));
    var r = el("p", "muted", caseFile.result);
    r.style.marginTop = "10px";
    box.appendChild(r);
    if (caseFile.breakLabel) box.appendChild(el("p", "pill", caseFile.breakLabel));
    sec.appendChild(box);

    var lines = el("div", "lines");
    caseFile.steps.forEach(function (step) {
      var line = el("p", "line");
      line.appendChild(el("span", "tag", "✓"));
      line.appendChild(el("b", null, step.label + ": "));
      var prefix = step.label + ": ";
      var text = step.findingLine.indexOf(prefix) === 0 ? step.findingLine.slice(prefix.length) : step.findingLine;
      line.appendChild(el("span", "muted", text));
      lines.appendChild(line);
    });
    sec.appendChild(lines);

    var finalCase = caseIndex === CASES.length - 1;
    var foot = el("div", "foot");
    foot.appendChild(btn((finalCase ? "Record both findings" : "Continue to evidence") + " →", "primary", "continue", continueFromResult));
    sec.appendChild(foot);
    return sec;
  }

  function renderFinal() {
    var sec = el("section", "section");
    sec.appendChild(el("p", "big", "✓"));
    sec.appendChild(el("p", "eyebrow", FINAL.eyebrow));
    sec.appendChild(el("h2", null, FINAL.title));
    var two = el("div", "two");
    [FINAL.protection, FINAL.evidence].forEach(function (f) {
      var card = el("div", "card");
      card.appendChild(el("h3", null, f.title));
      card.appendChild(el("p", null, f.text));
      two.appendChild(card);
    });
    sec.appendChild(two);
    var reset = btn("↺ Review both routes", null, "restart", restart);
    reset.style.marginTop = "20px";
    sec.appendChild(reset);
    return sec;
  }

  function render() {
    renderRail();
    clearNode(mainEl);
    var caseFile = currentCase();
    if (finished) mainEl.appendChild(renderFinal());
    else if (showCaseResult) mainEl.appendChild(renderCaseResult(caseFile));
    else mainEl.appendChild(renderCaseWork(caseFile));
  }

  function pruneState(saved) {
    if (!saved || typeof saved !== "object") return;
    var ci = saved.caseIndex;
    if (typeof ci === "number" && ci >= 0 && ci < CASES.length) caseIndex = Math.floor(ci);
    var caseFile = currentCase();
    var next = {};
    if (saved.placed && typeof saved.placed === "object") {
      caseFile.steps.forEach(function (step) {
        var v = saved.placed[step.id];
        if (typeof v === "string" && findStatement(caseFile, v)) next[step.id] = v;
      });
    }
    // One statement can sit on only one link.
    var seen = {};
    Object.keys(next).forEach(function (k) { if (seen[next[k]]) delete next[k]; else seen[next[k]] = true; });
    placed = next;
    checked = saved.checked === true && isFilled(caseFile);
    showCaseResult = saved.showCaseResult === true && isAllRight(caseFile);
    finished = saved.finished === true;
  }

  function hydrate(saved, meta) {
    pruneState(saved);
    if (meta && meta.completed) completedOnce = true;
    held = null;
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) {}
    hydrate(raw, null);
  }
</script>
</body>
</html>
