---
id: '55e77b5f-adc2-4342-aef5-fd07e3853f35'
title: Who knows what? (Insider Report)
summary_for_tutor: "A three-phase source-assessment drill from XLab's Verification track. Phase 1, Assess sources: six insider cards (Evaluator, Training engineer, Infrastructure operator, Procurement or finance staff, Supplier or data-center contractor, Executive or board member). For each, the learner reads the source's prompt, reported claim, incentives and consistency test, then picks one card in each of three columns (Could observe, Could not establish, Check against) from three options each and presses Check assessment; wrong picks show the source's own mismatch line, and a fully correct pick reveals the one-paragraph assessment for that source. Phase 2, Review report (unlocked after all six sources are assessed): the Project Lattice case report (a cooling contractor reporting a capacity expansion for 1,024 accelerators, work-order code PX-814, an independently obtained utility record, a pending financial reward) and four commit-then-reveal credibility questions on Access, Incentives, Consistency and Independent corroboration; a wrong answer shows a retry hint and the learner must answer correctly to continue. Phase 3, Record finding: the disposition (Further investigation warranted, no compliance finding), the finding text, the four basis lines, and four failure modes (Selective truth, Coordinated cover story, Management staging, Suppression). Done means the learner reached the finding. The saved-state summary tells you which sources are assessed, which credibility questions are answered, and where the learner is. When the learner over-reaches, use the widget's own line: a job title alone proves nothing; limit the claim to what the person could observe, state what remains unknown, and choose evidence the source did not control."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Who knows what?</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-insiders". -->
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
  h1, h2, h3, h4 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 26px; line-height: 1.2; }
  h2 { font-size: 20px; }
  h3 { font-size: 17px; }
  h4 { font-size: 15px; }
  p { margin: 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .small { font-size: 12px; }
  .muted { color: var(--muted); }
  .wrap { border: 1px solid var(--border); border-radius: 8px; background: var(--bg); overflow: hidden; }
  header.top { padding: 20px; border-bottom: 1px solid var(--border); }
  header.top h1 { margin-top: 8px; }
  .lede { color: var(--muted); margin-top: 8px; max-width: 46rem; }
  .rail { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin: 16px 0 0; padding: 0; list-style: none; }
  .rail li { border: 1px solid var(--border); border-radius: 6px; padding: 8px 6px; text-align: center; font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
  .rail li.is-active { border-color: var(--accent); color: var(--accent); background: var(--surface); font-weight: 600; }
  .rail li.is-done { color: var(--text); background: var(--surface); }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button:disabled { cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; font-weight: 500; }
  button.primary:hover { background: var(--accent-hover); border-color: var(--accent-hover); }
  button.primary:disabled { opacity: 0.5; }
  button.ghost { border-color: transparent; color: var(--muted); padding: 6px 8px; }
  button.ghost:hover { color: var(--text); }
  .actions { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 16px; }

  /* Map phase */
  .map-top { padding: 16px 20px; border-bottom: 1px solid var(--border); background: var(--surface); }
  .progress-row { display: flex; align-items: center; justify-content: space-between; gap: 12px; margin-bottom: 12px; }
  .bar { width: 120px; height: 6px; border-radius: 3px; background: var(--border); overflow: hidden; }
  .bar span { display: block; height: 100%; background: var(--accent); }
  .actor-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 8px; }
  @media (min-width: 640px) { .actor-grid { grid-template-columns: repeat(3, 1fr); } }
  @media (min-width: 1100px) { .actor-grid { grid-template-columns: repeat(6, 1fr); } }
  .actor { min-height: 72px; padding: 10px; display: flex; flex-direction: column; gap: 4px; }
  .actor.is-active { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .actor .role { font-size: 12px; font-weight: 600; line-height: 1.3; }
  .actor .station { font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
  .actor .done { font-size: 11px; color: var(--accent); font-weight: 600; }
  .map-body { display: grid; }
  @media (min-width: 1000px) { .map-body { grid-template-columns: 17rem minmax(0, 1fr); } }
  aside.side { padding: 20px; border-bottom: 1px solid var(--border); background: var(--surface); }
  @media (min-width: 1000px) { aside.side { border-bottom: 0; border-right: 1px solid var(--border); } }
  aside.side h2 { margin-top: 6px; }
  .claim { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 12px; margin-top: 14px; }
  .claim p + p { margin-top: 6px; }
  .clue { border-top: 1px solid var(--border); margin-top: 14px; padding-top: 10px; }
  .clue p + p { margin-top: 4px; font-size: 12px; }
  .main { padding: 20px; }
  .columns { display: grid; gap: 16px; }
  @media (min-width: 820px) { .columns { grid-template-columns: repeat(3, minmax(0, 1fr)); } }
  .col h4 { font-family: var(--font-ui); font-size: 12px; font-weight: 600; margin-top: 4px; line-height: 1.35; }
  .col .head { min-height: 48px; margin-bottom: 8px; }
  .cards { display: grid; gap: 8px; }
  .cardbtn { width: 100%; padding: 10px 12px; }
  .cardbtn .lbl { display: flex; justify-content: space-between; gap: 8px; font-size: 12px; font-weight: 600; line-height: 1.35; }
  .cardbtn .mark { flex: none; font-weight: 600; }
  .cardbtn .det { display: block; margin-top: 4px; font-size: 11px; color: var(--muted); line-height: 1.4; }
  .cardbtn.is-selected { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .cardbtn.is-correct { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); background: var(--surface); }
  .cardbtn.is-wrong { border-style: dashed; border-color: var(--muted); box-shadow: none; }
  .cardbtn:disabled { opacity: 0.85; }
  .cardbtn:disabled:hover { background: #fff; }
  .cardbtn.is-correct:disabled:hover { background: var(--surface); }
  .colmsg { margin-top: 8px; font-size: 11px; font-weight: 500; color: var(--accent-hover); }
  .verdict { border-top: 1px solid var(--border); margin-top: 20px; padding-top: 16px; }
  .box { border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; background: var(--surface); }
  .box.ok { border-color: var(--text); }
  .box .t { font-size: 12px; font-weight: 600; }
  .box .t.ok { color: var(--accent-hover); }
  .box p + p { margin-top: 8px; }
  .box .basis { border-top: 1px solid var(--border); margin-top: 10px; padding-top: 10px; font-size: 12px; }

  /* Examination phase */
  .exam { display: grid; }
  @media (min-width: 1000px) { .exam { grid-template-columns: 19rem minmax(0, 1fr); } }
  .report { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 14px; margin-top: 10px; }
  .qhead { display: flex; justify-content: space-between; gap: 12px; align-items: flex-start; }
  .qhead h2 { margin-top: 6px; }
  .prompt { margin-top: 10px; max-width: 42rem; }
  .choices { display: grid; gap: 10px; margin-top: 16px; }
  .choice { width: 100%; padding: 12px 14px; line-height: 1.5; }
  .choice.is-selected { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .choice.is-correct { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); background: var(--surface); }
  .choice.is-wrong { border-style: dashed; border-color: var(--muted); box-shadow: none; }
  .choice .mark { font-weight: 600; margin-right: 6px; }

  /* Finding phase */
  .finding { border: 1px solid var(--accent); border-radius: 8px; padding: 20px; background: var(--surface); }
  .finding .eyebrow { color: var(--accent-hover); }
  .finding h2 { margin-top: 8px; font-size: 24px; }
  .finding .text { margin-top: 12px; }
  .basis-list { margin: 8px 0 0; padding: 0; list-style: none; display: grid; gap: 6px; font-size: 12px; }
  .basis-list li { display: flex; gap: 8px; }
  .basis-list li .mark { flex: none; color: var(--accent-hover); font-weight: 600; }
  .modes { display: grid; gap: 10px; margin-top: 12px; }
  @media (min-width: 640px) { .modes { grid-template-columns: 1fr 1fr; } }
  .mode { border: 1px solid var(--border); border-radius: 8px; padding: 12px 14px; }
  .mode h4 { font-family: var(--font-ui); font-size: 13px; font-weight: 600; }
  .mode p { margin-top: 4px; font-size: 12px; color: var(--muted); }
  .foot { border-top: 1px solid var(--border); margin-top: 20px; padding-top: 16px; display: flex; flex-wrap: wrap; gap: 12px; align-items: center; justify-content: space-between; }
  .foot p { max-width: 36rem; font-size: 12px; color: var(--muted); }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
</style>
</head>
<body>
<div class="wrap" id="app">
  <header class="top">
    <p class="eyebrow">Source assessment · 2.4.1</p>
    <h1>Who knows what?</h1>
    <p class="lede">For each source, identify what they could observe, what they could not know, and which independent record could verify the claim. You will produce a short assessment for each source.</p>
    <ol class="rail" id="rail" aria-label="Exercise progress"></ol>
  </header>
  <div id="stage" aria-live="polite"></div>
</div>

<script>
(function () {
  "use strict";

  var CONNECTION_KINDS = ["observation", "boundary", "corroboration"];

  var CONNECTION_KIND_COPY = {
    observation: { eyebrow: "Could observe", question: "What could this person observe directly?" },
    boundary: { eyebrow: "Could not establish", question: "What part of the suspected violation would remain outside their view?" },
    corroboration: { eyebrow: "Check against", question: "Which independent record could verify the claim?" }
  };

  var CONNECTION_CARDS = {
    observation: [
      { id: "evaluation-record", label: "Result under the tested setup", detail: "Scores, prompts, methodology, exclusions, and anomalies in the evaluation they ran." },
      { id: "model-lineage", label: "Training records and model lineage", detail: "Training code, datasets, checkpoints, run configuration, and which model descended from which run." },
      { id: "cluster-activity", label: "Cluster activity", detail: "Allocated accelerators, job timing, utilization, access events, power draw, and unusual log gaps." },
      { id: "purchase-flow", label: "Purchases and payments", detail: "Orders, invoices, project codes, counterparties, payment timing, and off-ledger anomalies." },
      { id: "facility-build", label: "Facility capacity", detail: "Racks, chips, cooling, power, interconnects, and installation dates." },
      { id: "decision-record", label: "Decisions and risk warnings", detail: "What leadership approved, what the board was told, which risks were accepted, and what was withheld." }
    ],
    boundary: [
      { id: "evaluation-no-deployment", label: "What happened after the test", detail: "A test result does not show how the model was later deployed, modified, or monitored in production." },
      { id: "engineer-no-intent", label: "Why leadership approved the work", detail: "Technical participation does not show why leaders authorized the work or whether they intended to conceal it." },
      { id: "infra-no-authorization", label: "Why the job ran or who approved it", detail: "Infrastructure records show that compute ran. They do not show its purpose or who authorized it." },
      { id: "commercial-no-workload", label: "Which workload used the capacity", detail: "A purchase or payment can expose undeclared capacity without identifying the model or code that used it." },
      { id: "contractor-no-purpose", label: "What the facility ran", detail: "A contractor can see what was installed without knowing which workload or model used it." },
      { id: "leadership-no-execution", label: "Whether the decision was carried out", detail: "A formal decision does not prove that staff carried it out or that the record is complete." }
    ],
    corroboration: [
      { id: "evaluation-artifacts", label: "Evaluation records created at the time", detail: "Signed result files, prompt and harness versions, run identifiers, and deployment records from another system." },
      { id: "lineage-logs", label: "Model registry and scheduler records", detail: "Checkpoint hashes, storage and access logs, run manifests, scheduler records, and independent code review." },
      { id: "infra-telemetry", label: "Provider telemetry and hardware inventory", detail: "Scheduler data held by the provider, power and network telemetry, hardware attestations, and a physical count." },
      { id: "transaction-records", label: "Records held by counterparties", detail: "Vendor invoices, bank or ledger entries, shipping and customs records, serials, and receiving logs." },
      { id: "facility-records", label: "Utility, delivery, and inspection records", detail: "Power allocations, permits, delivery manifests, work orders, maintenance logs, and site inspection." },
      { id: "governance-records", label: "Decision records created at the time", detail: "Board minutes, risk memos, approval tickets, messages, and technical evidence that tests implementation." }
    ]
  };

  var SOURCE_ACTORS = [
    {
      id: "evaluator", role: "Evaluator", station: "Evaluation",
      prompt: "Ran the capability evaluation and kept the test harness and results.",
      report: "The model crossed the agreed capability threshold in our evaluation run.",
      incentives: "May want to defend the test method, avoid blame for a missed risk, or meet a professional duty to report.",
      consistencyTest: "Compare the test setup and exclusions with notes, code changes, earlier accounts, and the saved results.",
      choices: {
        observation: ["decision-record", "evaluation-record", "model-lineage"],
        boundary: ["engineer-no-intent", "evaluation-no-deployment", "leadership-no-execution"],
        corroboration: ["lineage-logs", "governance-records", "evaluation-artifacts"]
      },
      correct: { observation: "evaluation-record", boundary: "evaluation-no-deployment", corroboration: "evaluation-artifacts" },
      mismatch: {
        observation: "Limit the claim to the evaluation this person ran.",
        boundary: "The evaluator did not observe what happened after the test.",
        corroboration: "Check records created during the evaluation, then examine deployment separately."
      },
      sentence: "The evaluator can describe the test method and results. They cannot establish how the model was later deployed. Check signed test records and independent deployment records."
    },
    {
      id: "training-engineer", role: "Training engineer", station: "Model development",
      prompt: "Configured the training run, handled checkpoints, and can trace the model's lineage.",
      report: "This checkpoint came from an undeclared run using the restricted training configuration.",
      incentives: "May face consequences for taking part, feel loyalty to the team, or want to prevent misuse of their work.",
      consistencyTest: "Compare the dates, configuration, checkpoint lineage, and access claims with records maintained by other teams.",
      choices: {
        observation: ["cluster-activity", "model-lineage", "decision-record"],
        boundary: ["infra-no-authorization", "leadership-no-execution", "engineer-no-intent"],
        corroboration: ["infra-telemetry", "lineage-logs", "governance-records"]
      },
      correct: { observation: "model-lineage", boundary: "engineer-no-intent", corroboration: "lineage-logs" },
      mismatch: {
        observation: "Focus on the run configuration, workload, and model lineage.",
        boundary: "The engineer may not know why leadership approved the work.",
        corroboration: "Check model and run records from storage, scheduling, and review systems."
      },
      sentence: "The training engineer can describe the workload and model lineage, but may not know why leadership approved the work. Check checkpoint hashes, model-registry entries, scheduler records, and access logs."
    },
    {
      id: "infrastructure", role: "Infrastructure operator", station: "Compute operations",
      prompt: "Administers the cluster and can see allocations, failures, access events, and telemetry.",
      report: "A large eight-week job ran on the cluster under a project code omitted from the declaration.",
      incentives: "May want to protect the operations team, avoid discipline for missing logs, or report misuse of systems they maintain.",
      consistencyTest: "Compare job timing, accelerator count, access events, and log gaps with provider records, power data, and physical inventory.",
      choices: {
        observation: ["facility-build", "cluster-activity", "model-lineage"],
        boundary: ["contractor-no-purpose", "engineer-no-intent", "infra-no-authorization"],
        corroboration: ["lineage-logs", "facility-records", "infra-telemetry"]
      },
      correct: { observation: "cluster-activity", boundary: "infra-no-authorization", corroboration: "infra-telemetry" },
      mismatch: {
        observation: "Focus on the cluster records this operator can access.",
        boundary: "The records do not explain the job's purpose or who approved it.",
        corroboration: "Check telemetry and inventory records outside this operator's control."
      },
      sentence: "The infrastructure operator can establish that a large job ran, when it ran, and which cluster it used. They may not know its purpose or who approved it. Check provider telemetry, power records, and hardware inventory."
    },
    {
      id: "procurement-finance", role: "Procurement or finance staff", station: "Commercial records",
      prompt: "Processed purchases and payments charged to an unfamiliar project code.",
      report: "The organization acquired far more accelerator capacity than it declared.",
      incentives: "May fear blame for approving the purchase, want to protect the budget owner, or have fewer ties to the technical team.",
      consistencyTest: "Reconcile quantities, dates, project codes, counterparties, and payment flows across internal and external ledgers.",
      choices: {
        observation: ["facility-build", "purchase-flow", "cluster-activity"],
        boundary: ["contractor-no-purpose", "commercial-no-workload", "infra-no-authorization"],
        corroboration: ["facility-records", "transaction-records", "infra-telemetry"]
      },
      correct: { observation: "purchase-flow", boundary: "commercial-no-workload", corroboration: "transaction-records" },
      mismatch: {
        observation: "This source sees purchase and payment records, not the machines in operation.",
        boundary: "A ledger can expose capacity without identifying the workload that consumed it.",
        corroboration: "Check records held by vendors, banks, shippers, customs agencies, and receiving staff."
      },
      sentence: "Procurement or finance staff can document what was bought and how it was paid for. They may not know which workload used it. Check vendor invoices, payment records, shipping documents, serial numbers, and receiving logs."
    },
    {
      id: "supplier-contractor", role: "Supplier or data-center contractor", station: "Facility operations",
      prompt: "Installed power, cooling, racks, or chips during a capacity expansion.",
      report: "The site added capacity under a project code that does not appear in the declared facility plan.",
      incentives: "May seek a reward, protect future contracts, pursue a commercial dispute, or avoid being linked to concealed work.",
      consistencyTest: "Compare the project code, quantities, site, and installation dates across work orders and later accounts.",
      choices: {
        observation: ["purchase-flow", "cluster-activity", "facility-build"],
        boundary: ["commercial-no-workload", "infra-no-authorization", "contractor-no-purpose"],
        corroboration: ["transaction-records", "infra-telemetry", "facility-records"]
      },
      correct: { observation: "facility-build", boundary: "contractor-no-purpose", corroboration: "facility-records" },
      mismatch: {
        observation: "Focus on the equipment and infrastructure this contractor installed or serviced.",
        boundary: "The contractor did not see which model or workload used the capacity.",
        corroboration: "Check utility, delivery, installation, maintenance, and inspection records."
      },
      sentence: "The supplier or contractor can describe what was installed, where, and when. They may not know how the capacity was used. Check utility allocations, delivery manifests, work orders, maintenance logs, and the site itself."
    },
    {
      id: "executive-board", role: "Executive or board member", station: "Governance",
      prompt: "Received risk warnings and took part in the decision to proceed.",
      report: "Leadership understood the restriction and deliberately approved work outside the declaration.",
      incentives: "May want to defend the official account, limit personal liability, oppose management, or correct an earlier decision.",
      consistencyTest: "Compare the decision, dates, attendees, stated reasons, and warnings with records created at the time and accounts from other participants.",
      choices: {
        observation: ["evaluation-record", "decision-record", "model-lineage"],
        boundary: ["evaluation-no-deployment", "engineer-no-intent", "leadership-no-execution"],
        corroboration: ["evaluation-artifacts", "lineage-logs", "governance-records"]
      },
      correct: { observation: "decision-record", boundary: "leadership-no-execution", corroboration: "governance-records" },
      mismatch: {
        observation: "Focus on the decisions and warnings this person received or discussed.",
        boundary: "Approving a plan does not show exactly how staff carried it out.",
        corroboration: "Check records made at the time and technical evidence of what staff actually did."
      },
      sentence: "The executive or board member can describe decisions, warnings, and intent. They may not know every technical action taken. Check minutes, approvals, messages, and independent technical records."
    }
  ];

  var SOURCE_REPORT = {
    label: "Case report · Project Lattice",
    body: "A cooling contractor reports that Project Lattice added power and chilled-water capacity for 1,024 accelerators over six weeks. The contractor has applied for a financial reward and provides work-order code PX-814. A utility record obtained separately contains the same code and dates. The contractor did not have access to cluster workloads."
  };

  var CREDIBILITY_QUESTIONS = [
    {
      id: "access", label: "Access", prompt: "What can this source actually know?",
      choices: [
        { id: "access-bounded", text: "The installed capacity, site, dates, and project code, not the workload or its authorization." },
        { id: "access-violation", text: "That an unauthorized frontier-model training run occurred." },
        { id: "access-none", text: "Nothing useful, because contractors are outside the AI developer." }
      ],
      answerId: "access-bounded",
      retry: "Separate the physical work they witnessed from the workload they could not see.",
      explanation: "The contractor can describe infrastructure work they performed or saw. That access does not show which model ran, who authorized it, or whether a rule was breached.",
      findingLine: "Access: The contractor can describe the capacity expansion and project code, but not the workload or its authorization."
    },
    {
      id: "incentives", label: "Incentives", prompt: "How should the financial reward affect the assessment?",
      choices: [
        { id: "incentive-context", text: "Record the possible reward and the costs of reporting. Treat motive as a reason to check the claim carefully, not as proof that it is true or false." },
        { id: "incentive-dismiss", text: "Assume the report is unreliable because the source may receive a reward." },
        { id: "incentive-credit", text: "Treat the personal risk of reporting as proof that the allegation is true." }
      ],
      answerId: "incentive-context",
      retry: "The reward may encourage a false report. Fear of retaliation or lost work may discourage a true one. Neither decides whether this report is accurate.",
      explanation: "Incentives matter because they may shape whether and how someone reports. They do not replace evidence.",
      findingLine: "Incentives: The possible reward and the risk of losing work both matter, but neither confirms nor disproves the report."
    },
    {
      id: "consistency", label: "Consistency", prompt: "Which consistency check matters here?",
      choices: [
        { id: "consistency-material", text: "Check whether the site, dates, quantity, and project code remain stable across interviews and fit the known timeline." },
        { id: "consistency-verbatim", text: "Require every retelling to use exactly the same words and peripheral details." },
        { id: "consistency-group", text: "Accept matching accounts from coworkers selected and briefed together as independent confirmation." }
      ],
      answerId: "consistency-material",
      retry: "Focus on the facts that matter. Identical wording may reflect rehearsal, and coordinated accounts are not independent evidence.",
      explanation: "Minor details may change as people recall an event. The central facts should remain consistent with the timeline and other evidence.",
      findingLine: "Consistency: The site, dates, quantity, and project code should remain stable and fit the known timeline. Scripted agreement is not independent evidence."
    },
    {
      id: "corroboration", label: "Independent corroboration", prompt: "Which evidence adds the most weight to this report?",
      choices: [
        { id: "corroboration-independent", text: "The independently obtained utility log, followed by serial, receiving, scheduler, and authorization records from separate systems." },
        { id: "corroboration-reputation", text: "The contractor's reputation for honesty in the local industry." },
        { id: "corroboration-copy", text: "A spreadsheet the contractor created after deciding to report." }
      ],
      answerId: "corroboration-independent",
      retry: "Use evidence created independently of the source and outside the source's control.",
      explanation: "The matching project code and dates link the report to an external record. They support the claim that the site expanded, but not a claim about the workload.",
      findingLine: "Corroboration: The utility record supports the infrastructure claim. Workload and approval records are still needed."
    }
  ];

  var FINAL_FINDING = {
    disposition: "Further investigation warranted · no compliance finding",
    text: "The report supports a finding that Project Lattice expanded infrastructure at the stated site and time. It does not show which workload ran or whether any rule was breached. Investigators should preserve the work orders and utility record, then obtain receiving records, serial numbers, scheduler telemetry, model-lineage records, and approval documents."
  };

  var FAILURE_MODES = [
    { name: "Selective truth", check: "The expansion may be real even if the claimed prohibited workload is not. Do not treat proof of infrastructure as proof of how it was used." },
    { name: "Coordinated cover story", check: "Matching accounts are not independent if managers selected, briefed, or monitored the speakers." },
    { name: "Management staging", check: "A clean tour and selected records show what management chose to present. They do not rule out undeclared activity elsewhere." },
    { name: "Suppression", check: "A lack of reports means little if staff have no safe reporting channel, cannot see the relevant declarations, or reasonably fear retaliation." }
  ];

  var PHASES = [
    { id: "map", label: "1 · Assess sources" },
    { id: "examine", label: "2 · Review report" },
    { id: "finding", label: "3 · Record finding" }
  ];

  /* Seeded shuffle (port of XLab src/lib/shuffle.ts): order is a function of the item id, never of the visit. */
  function hashSeed(seed) {
    var h = 0x811c9dc5;
    for (var i = 0; i < seed.length; i++) {
      h ^= seed.charCodeAt(i);
      h = Math.imul(h, 0x01000193);
    }
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
  function seededShuffle(seed, items) {
    var order = items.slice();
    var rand = prng(hashSeed(seed));
    for (var i = order.length - 1; i > 0; i--) {
      var j = Math.floor(rand() * (i + 1));
      var tmp = order[i]; order[i] = order[j]; order[j] = tmp;
    }
    return order;
  }

  function sourceActor(id) {
    for (var i = 0; i < SOURCE_ACTORS.length; i++) if (SOURCE_ACTORS[i].id === id) return SOURCE_ACTORS[i];
    return SOURCE_ACTORS[0];
  }
  function connectionCard(kind, id) {
    var list = CONNECTION_CARDS[kind];
    for (var i = 0; i < list.length; i++) if (list[i].id === id) return list[i];
    return null;
  }
  function checkConnection(actorId, selection) {
    var actor = sourceActor(actorId);
    var correct = {}, messages = {}, complete = true;
    CONNECTION_KINDS.forEach(function (kind) {
      correct[kind] = selection[kind] === actor.correct[kind];
      if (!selection[kind]) messages[kind] = "Choose a card for this link.";
      else if (!correct[kind]) messages[kind] = actor.mismatch[kind];
      if (!correct[kind]) complete = false;
    });
    return { complete: complete, correct: correct, messages: messages };
  }
  function checkCredibilityAnswer(questionId, answerId) {
    for (var i = 0; i < CREDIBILITY_QUESTIONS.length; i++) {
      if (CREDIBILITY_QUESTIONS[i].id === questionId) return CREDIBILITY_QUESTIONS[i].answerId === answerId;
    }
    return false;
  }

  /* State */
  var STORAGE_KEY = "lens-widget-human-insiders";
  var state = freshState();
  var completedOnce = false;

  function freshState() {
    return {
      phase: "map",
      activeActorId: "evaluator",
      selections: {},      /* actorId -> { kind: cardId } */
      checked: {},         /* actorId -> true once "Check assessment" was pressed for the current selection */
      resolved: [],        /* actor ids in the order they were resolved */
      questionIndex: 0,
      answerId: "",
      examState: null      /* null | "correct" | "wrong" */
    };
  }

  function isResolved(actorId) { return state.resolved.indexOf(actorId) !== -1; }
  function currentSelection(actorId) { return state.selections[actorId] || {}; }
  function currentResult(actorId) {
    if (isResolved(actorId)) return checkConnection(actorId, sourceActor(actorId).correct);
    if (state.checked[actorId]) return checkConnection(actorId, currentSelection(actorId));
    return null;
  }

  /* Actions */
  function selectActor(actorId) {
    state.activeActorId = actorId;
    render(); persist();
  }
  function chooseConnection(kind, id) {
    var actorId = state.activeActorId;
    if (isResolved(actorId)) return;
    var sel = currentSelection(actorId);
    sel[kind] = id;
    state.selections[actorId] = sel;
    delete state.checked[actorId];
    render(); persist();
  }
  function testConnections() {
    var actorId = state.activeActorId;
    if (isResolved(actorId)) return;
    state.checked[actorId] = true;
    var result = checkConnection(actorId, currentSelection(actorId));
    if (result.complete) state.resolved.push(actorId);
    render(); persist();
  }
  function nextSource() {
    for (var i = 0; i < SOURCE_ACTORS.length; i++) {
      if (!isResolved(SOURCE_ACTORS[i].id)) { selectActor(SOURCE_ACTORS[i].id); return; }
    }
  }
  function beginExamination() {
    if (state.resolved.length !== SOURCE_ACTORS.length) return;
    state.questionIndex = 0;
    state.answerId = "";
    state.examState = null;
    state.phase = "examine";
    render(); persist();
  }
  function backToMap() {
    state.phase = "map";
    render(); persist();
  }
  function chooseAnswer(id) {
    if (state.examState === "correct") return;
    state.answerId = id;
    state.examState = null;
    render(); persist();
  }
  function testAnswer() {
    if (!state.answerId) return;
    var q = CREDIBILITY_QUESTIONS[state.questionIndex];
    state.examState = checkCredibilityAnswer(q.id, state.answerId) ? "correct" : "wrong";
    render(); persist();
  }
  function nextQuestion() {
    if (state.examState !== "correct") return;
    if (state.questionIndex === CREDIBILITY_QUESTIONS.length - 1) {
      state.phase = "finding";
      render(); persist();
      if (!completedOnce) {
        completedOnce = true;
        if (window.Lens) window.Lens.complete();
      }
      return;
    }
    state.questionIndex += 1;
    state.answerId = "";
    state.examState = null;
    render(); persist();
  }
  function restart() {
    state = freshState();
    render(); persist();
  }

  /* Persistence */
  function summaryText() {
    var parts = [];
    var names = state.resolved.map(function (id) { return sourceActor(id).role; });
    parts.push("Who knows what? drill. Phase: " + phaseLabel(state.phase) + ".");
    parts.push(state.resolved.length + " of " + SOURCE_ACTORS.length + " sources assessed" + (names.length ? " (" + names.join(", ") + ")" : "") + ".");
    if (state.phase === "map") {
      var actor = sourceActor(state.activeActorId);
      var sel = currentSelection(actor.id);
      var picks = CONNECTION_KINDS.map(function (kind) {
        var card = sel[kind] ? connectionCard(kind, sel[kind]) : null;
        return CONNECTION_KIND_COPY[kind].eyebrow + ": " + (card ? card.label : "nothing chosen");
      });
      parts.push("Looking at " + actor.role + (isResolved(actor.id) ? " (assessed)" : "") + ". Current picks: " + picks.join("; ") + ".");
      var res = currentResult(actor.id);
      if (res && !res.complete) {
        var wrong = CONNECTION_KINDS.filter(function (k) { return !res.correct[k]; }).map(function (k) { return CONNECTION_KIND_COPY[k].eyebrow; });
        parts.push("Last check failed on: " + wrong.join(", ") + ".");
      }
    } else if (state.phase === "examine") {
      var q = CREDIBILITY_QUESTIONS[state.questionIndex];
      var chosen = null;
      for (var i = 0; i < q.choices.length; i++) if (q.choices[i].id === state.answerId) chosen = q.choices[i];
      parts.push("Reviewing the Project Lattice case report, question " + (state.questionIndex + 1) + " of " + CREDIBILITY_QUESTIONS.length + " (" + q.label + ").");
      if (chosen) parts.push("Selected: \"" + chosen.text + "\"" + (state.examState ? " (" + (state.examState === "correct" ? "correct" : "wrong, retrying") + ")" : " (not yet checked)") + ".");
      if (state.questionIndex > 0) parts.push("Earlier credibility questions answered correctly: " + CREDIBILITY_QUESTIONS.slice(0, state.questionIndex).map(function (x) { return x.label; }).join(", ") + ".");
    } else {
      parts.push("All four credibility questions answered. The finding is issued: " + FINAL_FINDING.disposition + ".");
    }
    return parts.join(" ");
  }
  function phaseLabel(id) {
    for (var i = 0; i < PHASES.length; i++) if (PHASES[i].id === id) return PHASES[i].label;
    return id;
  }
  function persist() {
    var snapshot = JSON.parse(JSON.stringify(state));
    if (window.Lens) {
      window.Lens.saveState(snapshot, summaryText());
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snapshot)); } catch (e) { /* storage unavailable */ }
    }
  }
  function hydrate(saved, meta) {
    if (saved && typeof saved === "object" && saved.phase) {
      var next = freshState();
      next.phase = ["map", "examine", "finding"].indexOf(saved.phase) !== -1 ? saved.phase : "map";
      next.activeActorId = sourceActor(saved.activeActorId).id;
      next.selections = (saved.selections && typeof saved.selections === "object") ? saved.selections : {};
      next.checked = (saved.checked && typeof saved.checked === "object") ? saved.checked : {};
      next.resolved = Array.isArray(saved.resolved) ? saved.resolved.filter(function (id) { return SOURCE_ACTORS.some(function (a) { return a.id === id; }); }) : [];
      next.questionIndex = Math.min(Math.max(parseInt(saved.questionIndex, 10) || 0, 0), CREDIBILITY_QUESTIONS.length - 1);
      next.answerId = typeof saved.answerId === "string" ? saved.answerId : "";
      next.examState = (saved.examState === "correct" || saved.examState === "wrong") ? saved.examState : null;
      if (next.phase !== "map" && next.resolved.length !== SOURCE_ACTORS.length) next.phase = "map";
      state = next;
    }
    if (meta && meta.completed) completedOnce = true;
    if (state.phase === "finding") completedOnce = true;
    render();
  }

  /* Rendering */
  function el(tag, className, text) {
    var node = document.createElement(tag);
    if (className) node.className = className;
    if (text !== undefined && text !== null) node.textContent = text;
    return node;
  }
  function btn(label, className, onClick) {
    var b = el("button", className, label);
    b.type = "button";
    b.addEventListener("click", onClick);
    return b;
  }

  var railEl = document.getElementById("rail");
  var stageEl = document.getElementById("stage");

  function render() {
    renderRail();
    stageEl.textContent = "";
    if (state.phase === "map") stageEl.appendChild(renderMap());
    else if (state.phase === "examine") stageEl.appendChild(renderExam());
    else stageEl.appendChild(renderFinding());
  }

  function renderRail() {
    railEl.textContent = "";
    var active = 0;
    for (var i = 0; i < PHASES.length; i++) if (PHASES[i].id === state.phase) active = i;
    PHASES.forEach(function (p, index) {
      var li = el("li", index === active ? "is-active" : (index < active ? "is-done" : ""), (index < active ? "✓ " : "") + p.label);
      if (index === active) li.setAttribute("aria-current", "step");
      railEl.appendChild(li);
    });
  }

  function renderMap() {
    var root = el("div");
    var actor = sourceActor(state.activeActorId);
    var resolved = isResolved(actor.id);
    var allResolved = state.resolved.length === SOURCE_ACTORS.length;
    var result = currentResult(actor.id);
    var selection = currentSelection(actor.id);

    /* Actor grid */
    var top = el("div", "map-top");
    var prog = el("div", "progress-row");
    prog.appendChild(el("p", "small muted", state.resolved.length + " of " + SOURCE_ACTORS.length + " sources assessed"));
    var bar = el("div", "bar");
    bar.setAttribute("aria-hidden", "true");
    var fill = el("span");
    fill.style.width = Math.round((state.resolved.length / SOURCE_ACTORS.length) * 100) + "%";
    bar.appendChild(fill);
    prog.appendChild(bar);
    top.appendChild(prog);
    var grid = el("div", "actor-grid");
    SOURCE_ACTORS.forEach(function (candidate) {
      var done = isResolved(candidate.id);
      var b = btn("", "actor" + (candidate.id === actor.id ? " is-active" : ""), function () { selectActor(candidate.id); });
      b.setAttribute("aria-pressed", candidate.id === actor.id ? "true" : "false");
      b.appendChild(el("span", "role", candidate.role));
      b.appendChild(el("span", "station", candidate.station));
      if (done) b.appendChild(el("span", "done", "✓ Assessed"));
      grid.appendChild(b);
    });
    top.appendChild(grid);
    root.appendChild(top);

    /* Body */
    var body = el("div", "map-body");
    var aside = el("aside", "side");
    aside.appendChild(el("p", "eyebrow", "Source"));
    aside.appendChild(el("h2", null, actor.role));
    aside.appendChild(el("p", "small muted", actor.station));
    var pr = el("p", null, actor.prompt); pr.style.marginTop = "12px";
    aside.appendChild(pr);
    var claim = el("div", "claim");
    claim.appendChild(el("p", "eyebrow", "Reported claim"));
    claim.appendChild(el("p", null, "“" + actor.report + "”"));
    aside.appendChild(claim);
    [["Incentives", actor.incentives], ["Consistency test", actor.consistencyTest]].forEach(function (pair) {
      var c = el("div", "clue");
      c.appendChild(el("p", "eyebrow", pair[0]));
      c.appendChild(el("p", null, pair[1]));
      aside.appendChild(c);
    });
    body.appendChild(aside);

    var main = el("div", "main");
    var cols = el("div", "columns");
    CONNECTION_KINDS.forEach(function (kind) {
      var copy = CONNECTION_KIND_COPY[kind];
      var col = el("section", "col");
      var head = el("div", "head");
      head.appendChild(el("p", "eyebrow", copy.eyebrow));
      head.appendChild(el("h4", null, copy.question));
      col.appendChild(head);
      var cards = el("div", "cards");
      var order = seededShuffle(actor.id + ":" + kind, actor.choices[kind]);
      order.forEach(function (id) {
        var card = connectionCard(kind, id);
        var selected = selection[kind] === id;
        var cls = "cardbtn";
        var mark = "";
        if (selected) {
          cls += " is-selected";
          if (result) {
            if (result.correct[kind]) { cls += " is-correct"; mark = "✓"; }
            else { cls += " is-wrong"; mark = "✗"; }
          }
        }
        var b = btn("", cls, function () { chooseConnection(kind, id); });
        b.disabled = resolved;
        b.setAttribute("aria-pressed", selected ? "true" : "false");
        var lbl = el("span", "lbl");
        lbl.appendChild(el("span", null, card.label));
        if (mark) lbl.appendChild(el("span", "mark", mark));
        b.appendChild(lbl);
        b.appendChild(el("span", "det", card.detail));
        cards.appendChild(b);
      });
      col.appendChild(cards);
      if (result && result.messages[kind]) {
        var m = el("p", "colmsg", result.messages[kind]);
        m.setAttribute("role", "alert");
        col.appendChild(m);
      }
      cols.appendChild(col);
    });
    main.appendChild(cols);

    var verdict = el("div", "verdict");
    if (result && result.complete) {
      var box = el("div", "box ok");
      box.appendChild(el("p", "t ok", "✓ Assessment complete"));
      box.appendChild(el("p", null, actor.sentence));
      verdict.appendChild(box);
    } else {
      verdict.appendChild(el("p", "small muted", "A job title alone proves nothing. Limit the claim to what this person could observe, state what remains unknown, and choose evidence the source did not control."));
    }
    var actions = el("div", "actions");
    if (!resolved) {
      actions.appendChild(btn("Check assessment", "primary", testConnections));
    } else if (allResolved) {
      actions.appendChild(btn("Review a source report →", "primary", beginExamination));
    } else {
      actions.appendChild(btn("Next source →", "primary", nextSource));
    }
    verdict.appendChild(actions);
    main.appendChild(verdict);
    body.appendChild(main);
    root.appendChild(body);
    return root;
  }

  function renderExam() {
    var root = el("div", "exam");
    var q = CREDIBILITY_QUESTIONS[state.questionIndex];
    var aside = el("aside", "side");
    aside.appendChild(el("p", "eyebrow", SOURCE_REPORT.label));
    var rep = el("div", "report");
    rep.appendChild(el("p", null, SOURCE_REPORT.body));
    aside.appendChild(rep);
    var note = el("p", "small muted", "Assess the report through access, incentives, consistency, and independent corroboration. Do not rely on the reporter's reputation.");
    note.style.marginTop = "12px";
    aside.appendChild(note);
    var back = btn("← Back to source map", "ghost", backToMap);
    back.style.marginTop = "8px";
    aside.appendChild(back);
    root.appendChild(aside);

    var main = el("div", "main");
    var head = el("div", "qhead");
    var hl = el("div");
    hl.appendChild(el("p", "eyebrow", "Question " + (state.questionIndex + 1) + " of " + CREDIBILITY_QUESTIONS.length));
    hl.appendChild(el("h2", null, q.label));
    head.appendChild(hl);
    main.appendChild(head);
    main.appendChild(el("p", "prompt", q.prompt));

    var choices = el("div", "choices");
    var order = seededShuffle("lattice:" + q.id, q.choices);
    order.forEach(function (choice) {
      var selected = state.answerId === choice.id;
      var cls = "choice";
      var mark = "";
      if (selected) {
        cls += " is-selected";
        if (state.examState === "correct") { cls += " is-correct"; mark = "✓"; }
        else if (state.examState === "wrong") { cls += " is-wrong"; mark = "✗"; }
      }
      var b = btn("", cls, function () { chooseAnswer(choice.id); });
      b.setAttribute("aria-pressed", selected ? "true" : "false");
      b.disabled = state.examState === "correct";
      if (mark) b.appendChild(el("span", "mark", mark));
      b.appendChild(el("span", null, choice.text));
      choices.appendChild(b);
    });
    main.appendChild(choices);

    if (state.examState) {
      var ok = state.examState === "correct";
      var box = el("div", "box" + (ok ? " ok" : ""));
      box.style.marginTop = "16px";
      box.setAttribute("role", ok ? "status" : "alert");
      box.appendChild(el("p", "t" + (ok ? " ok" : ""), ok ? "✓ Assessment recorded" : "This conclusion goes too far"));
      box.appendChild(el("p", null, ok ? q.explanation : q.retry));
      if (ok) box.appendChild(el("p", "basis", q.findingLine));
      main.appendChild(box);
    }

    var actions = el("div", "actions");
    if (state.examState === "correct") {
      actions.appendChild(btn((state.questionIndex === CREDIBILITY_QUESTIONS.length - 1 ? "Issue finding" : "Continue") + " →", "primary", nextQuestion));
    } else {
      var check = btn("Check answer", "primary", testAnswer);
      check.disabled = !state.answerId;
      actions.appendChild(check);
    }
    main.appendChild(actions);
    root.appendChild(main);
    return root;
  }

  function renderFinding() {
    var root = el("div", "main");
    var card = el("div", "finding");
    card.appendChild(el("p", "eyebrow", FINAL_FINDING.disposition));
    card.appendChild(el("h2", null, "Assessment"));
    card.appendChild(el("p", "text", FINAL_FINDING.text));
    var basis = el("div", "clue");
    basis.appendChild(el("p", "eyebrow", "Basis for the finding"));
    var ol = el("ol", "basis-list");
    CREDIBILITY_QUESTIONS.forEach(function (q) {
      var li = el("li");
      li.appendChild(el("span", "mark", "✓"));
      li.appendChild(el("span", null, q.findingLine));
      ol.appendChild(li);
    });
    basis.appendChild(ol);
    card.appendChild(basis);
    root.appendChild(card);

    var sec = el("section");
    sec.style.marginTop = "24px";
    sec.appendChild(el("p", "eyebrow", "Common failure modes"));
    var h = el("h3", null, "Why a consistent account may still be wrong");
    h.style.marginTop = "6px";
    sec.appendChild(h);
    var modes = el("div", "modes");
    FAILURE_MODES.forEach(function (mode) {
      var a = el("article", "mode");
      a.appendChild(el("h4", null, mode.name));
      a.appendChild(el("p", null, mode.check));
      modes.appendChild(a);
    });
    sec.appendChild(modes);
    root.appendChild(sec);

    var foot = el("div", "foot");
    foot.appendChild(el("p", null, "A human source can tell an investigator where to look and which records to preserve. Technical or physical evidence is still needed for facts the source did not observe."));
    foot.appendChild(btn("↺ Start over", "", restart));
    root.appendChild(foot);
    return root;
  }

  /* Boot */
  if (window.Lens) {
    window.Lens.onState(hydrate);
  } else {
    var saved = null;
    try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) { saved = null; }
    hydrate(saved, { completed: false });
  }
})();
</script>
</body>
</html>
