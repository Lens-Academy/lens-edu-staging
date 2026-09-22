---
id: 'c81c1118-d19b-438f-a51f-68638ebc149b'
title: Weighted factor model
summary_for_tutor: "Effective Thesis Accelerator, Week 3, worksheet Steps 2 to 4, as a native version of Effective Thesis's Example Thesis WFM spreadsheet. Its four parts match the sheet's tabs, and one is open at a time. Brainstorm (the Brainstorm of research question tab): the learner lists 10 to 20 candidate research questions with a quick score from 1 to 10, why it matters and a source or inspiration, then shortlists their top 5 to 10 (by hand or with a top-N-by-quick-score helper). A shortlisted question can get a Description, a simplified or cleaned version for the WFM, which then labels it everywhere after. Factors (the Info tab): twelve factors in four categories (Impact on the Problem Area, Impact on my career path, Impact on my community, General Thesis Interest), each with the sheet's description, a weight in percent, an inversion (higher is better or higher is worse) and a rationale for the weight; the learner can rename, add and remove factors, and the weights must total 100. Score (WFM(Values)): each shortlisted question scored 1 to 10 on every factor. Results (WFM (Scores)): a ranking on the weighted score, score times weight as a fraction summed, out of 10, which is what the Week 3 reading teaches (an inverted factor counts as 11 minus the score); one click away is the standardised score, the sheet's Sum column (each factor z-scored across the fully scored shortlist, times weight, times -1 if inverted, summed), which is relative to that shortlist. It shows which factors separate first from second, then asks for a gut favourite and shows the worksheet's tension line. Complete means two shortlisted questions fully scored, weights totalling 100 and a gut pick. Their work arrives as a one-paragraph summary: weights and what moved from the sheet's defaults, the ranking, the gap drivers and whether the gut pick disagrees with the model. There is no answer key. If they ask for review, ask whether they really believe the weight doing the most work between first and second, and if gut and model disagree, ask what the model is not capturing rather than telling them which to trust."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Weighted factor model</title>
<!-- A Lens port of Effective Thesis's "[Shared] Example Thesis WFM" spreadsheet (Accelerator, Week 3). Factor names, descriptions, weights, category prompts and the worked example are Effective Thesis's; three formula slips in the sheet are corrected here. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  [hidden] { display: none !important; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  /* Safety net: the host frame stops growing at 6000px and hides overflow, so the widget scrolls inside itself past this. */
  #root { max-height: 5900px; overflow-y: auto; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; line-height: 1.25; margin: 0 0 4px; }
  h3 { font-family: var(--font-heading); font-weight: 600; font-size: 16px; margin: 0; }
  h4 { font-size: 13px; font-weight: 600; margin: 16px 0 6px; }
  p { margin: 0 0 10px; }
  .lede { color: var(--muted); margin-bottom: 14px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 6px; }
  .hint { font-size: 13px; color: var(--muted); }
  .sr { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
  .step { border: 1px solid var(--border); border-radius: 8px; background: #fff; margin-bottom: 12px; }
  .step-head { display: flex; flex-wrap: wrap; align-items: baseline; gap: 2px 10px; width: 100%; border: 0; border-radius: 8px; background: #fff; padding: 12px 16px; text-align: left; cursor: pointer; }
  .step-head:hover { background: var(--surface); }
  .step-num { font-size: 12px; font-weight: 600; color: var(--accent); width: 100%; }
  .step-title { font-family: var(--font-heading); font-weight: 600; font-size: 17px; }
  .step-status { margin-left: auto; font-size: 12px; color: var(--muted); }
  .step-status.is-done { color: var(--text); font-weight: 600; }
  .step-body { padding: 10px 16px 16px; border-top: 1px solid var(--border); }
  label.f { display: block; font-size: 12px; font-weight: 600; color: var(--muted); margin: 6px 0 2px; }
  input[type=text], input[type=number], textarea, select {
    font: inherit; color: inherit; background: #fff; border: 1px solid var(--border);
    border-radius: 6px; padding: 5px 7px; max-width: 100%;
  }
  input[type=text], textarea { width: 100%; }
  textarea { resize: vertical; }
  input.num { width: 3.6rem; text-align: right; font-variant-numeric: tabular-nums; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 6px 11px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button:disabled { color: var(--muted); cursor: default; background: #fff; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.link { border: 0; padding: 2px 4px; color: var(--muted); text-decoration: underline; background: transparent; }
  button.small { padding: 4px 9px; font-size: 13px; }
  button.toggle[aria-pressed=true] { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  input:focus-visible, textarea:focus-visible, button:focus-visible, select:focus-visible { outline: 2px solid var(--accent); outline-offset: 1px; }
  .actions { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; margin-top: 12px; }
  .confirm { border-left: 3px solid var(--accent); background: var(--surface); border-radius: 0 6px 6px 0; padding: 10px 12px; margin-top: 10px; }
  .note { font-size: 13px; color: var(--muted); margin-top: 8px; }
  .warn { border-left: 3px solid var(--accent); background: var(--surface); border-radius: 0 6px 6px 0; padding: 8px 12px; margin: 0 0 12px; font-size: 13px; }
  /* Brainstorm rows: stacked on phones, one row per question (the sheet's columns) from 620px. */
  .qhdr { display: none; }
  .qrow { display: grid; grid-template-columns: 2rem minmax(0, 1fr); gap: 4px 8px; border-top: 1px solid var(--border); padding: 8px 0; }
  .qrow.is-short { box-shadow: inset 3px 0 0 var(--accent); }
  .qrow .n { font-weight: 600; font-variant-numeric: tabular-nums; padding-top: 6px; padding-left: 6px; }
  .qrow > div { grid-column: 2; }
  .qrow .qquick { display: flex; align-items: center; gap: 8px; }
  .qrow .qquick label.f { margin: 0; }
  .qmore { display: none; }
  .qmore.is-open { display: block; }
  .qact { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; }
  .cat { margin-top: 16px; }
  .cat-head { display: flex; align-items: baseline; gap: 10px; border-bottom: 2px solid var(--accent); padding-bottom: 4px; }
  .cat-head .tot { margin-left: auto; font-weight: 600; font-variant-numeric: tabular-nums; white-space: nowrap; }
  .cat-prompt { font-family: var(--font-heading); font-style: italic; color: var(--muted); margin: 6px 0 0; }
  .factor { border-bottom: 1px solid var(--border); padding: 8px 0; }
  .frow { display: grid; grid-template-columns: minmax(0, 1fr); gap: 6px; }
  .fctl { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; }
  .wbox { display: flex; align-items: center; gap: 4px; }
  .fmore { margin-top: 6px; }
  .desc { font-size: 13px; margin: 4px 0 0; }
  .meter { display: flex; flex-wrap: wrap; gap: 6px 12px; align-items: baseline; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 8px 12px; margin: 10px 0; }
  .meter .big { font-weight: 600; font-variant-numeric: tabular-nums; }
  .meter .off { color: var(--accent); font-weight: 600; }
  .scroll { overflow-x: auto; border: 1px solid var(--border); border-radius: 8px; margin-top: 10px; }
  table { border-collapse: separate; border-spacing: 0; font-size: 13px; }
  th, td { border-bottom: 1px solid var(--border); padding: 5px 6px; vertical-align: middle; background: #fff; }
  table.grid th.qcol { position: sticky; left: 0; z-index: 1; text-align: left; font-weight: 500; min-width: 8.5rem; max-width: 11rem; border-right: 1px solid var(--border); }
  table.grid thead th { font-size: 11px; color: var(--muted); font-weight: 600; text-align: center; }
  table.grid thead th.catcol { border-bottom: 2px solid var(--accent); text-transform: uppercase; letter-spacing: 0.05em; font-size: 10px; }
  table.grid thead th.catcol .w { display: block; text-transform: none; letter-spacing: 0; color: var(--text); }
  table.grid td { text-align: center; }
  table.grid td.tot { font-weight: 600; font-variant-numeric: tabular-nums; min-width: 4rem; }
  button.rowhead { border: 0; padding: 0; background: transparent; text-align: left; font-weight: 500; text-decoration: underline dotted; }
  .qtext { display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden; }
  button.colhead { border: 0; padding: 2px 2px; font-size: 11px; font-weight: 600; color: var(--text); text-decoration: underline dotted; text-align: center; background: transparent; min-width: 4.2rem; max-width: 6.5rem; line-height: 1.25; }
  button.colhead.is-inv::after { content: " (inv.)"; font-weight: 400; color: var(--muted); }
  input.cell { width: 2.6rem; text-align: center; font-variant-numeric: tabular-nums; padding: 5px 2px; }
  .detail { border-left: 3px solid var(--accent); background: var(--surface); border-radius: 0 6px 6px 0; padding: 8px 12px; margin-top: 10px; font-size: 13px; }
  .detail p:last-child { margin-bottom: 0; }
  table.rank { width: 100%; }
  table.rank th { font-size: 11px; color: var(--muted); font-weight: 600; text-align: left; }
  table.rank td.n, table.rank td.t { font-variant-numeric: tabular-nums; text-align: right; white-space: nowrap; }
  table.rank td.t { font-weight: 600; }
  table.rank tr.is-top td { font-weight: 600; }
  table.rank .orig { display: block; font-weight: 400; font-size: 12px; color: var(--muted); }
  table.rank th button { font-size: 11px; font-weight: 600; padding: 2px 4px; border: 0; background: transparent; color: var(--muted); text-decoration: underline; }
  .check { list-style: none; padding: 0; margin: 8px 0 0; }
  .check li { margin: 2px 0; }
  .check .mark { display: inline-block; min-width: 3.4rem; font-weight: 600; font-size: 12px; }
  .tension { border-left: 3px solid var(--accent); background: var(--surface); border-radius: 0 6px 6px 0; padding: 10px 12px; margin-top: 12px; }
  .tension p:last-child { margin-bottom: 0; }
  ul.drivers { margin: 4px 0 0; padding-left: 18px; }
  @media (min-width: 620px) {
    .qhdr { display: grid; grid-template-columns: 2rem minmax(0, 2fr) 4.4rem minmax(0, 1.5fr) minmax(0, 1fr) 8.5rem; gap: 8px; font-size: 11px; font-weight: 600; color: var(--muted); margin-top: 12px; }
    .qrow { grid-template-columns: 2rem minmax(0, 2fr) 4.4rem minmax(0, 1.5fr) minmax(0, 1fr) 8.5rem; gap: 4px 8px; align-items: start; }
    .qrow > div { grid-column: auto; }
    .qrow .qquick label.f, .qrow .qmore label.f, .qrow .qq label.f { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
    .qmore, .qmore.is-open { display: contents; }
    .qmore .qdesc { grid-column: 2 / 6; }
    .qmore .qdesc label.f { position: static; width: auto; height: auto; clip: auto; }
    .qrow .qact { flex-direction: column; align-items: stretch; grid-column: 6; grid-row: 1; }
    .qmore .qdesc { grid-row: 2; }
    .only-m { display: none !important; }
    .frow { grid-template-columns: minmax(0, 1fr) auto; align-items: end; }
  }
  @media (max-width: 420px) {
    body { padding: 10px; }
    .step-head { padding: 10px 12px; }
    .step-body { padding: 8px 12px 14px; }
    .step-status { margin-left: 0; width: 100%; }
  }
</style>
</head>
<body>
<div id="root">
<p class="eyebrow">Effective Thesis Accelerator, Week 3</p>
<h1>Weighted Factor Model for A High-Impact Thesis</h1>
<p class="lede">The four parts below are the tabs of Effective Thesis's spreadsheet: Brainstorm of research question, Info, WFM(Values) and WFM (Scores). Open one at a time; everything saves as you go.</p>
<div id="warn" class="warn" role="status" hidden></div>
<div id="app"></div>
</div>

<script>
/* WFM:BEGIN  pure calculation and state functions. The tests extract this block from the built file. */
var WFM = {
  CATS: [
    { id: "problem", name: "Impact on the Problem Area",
      prompt: "To what extent does this thesis focus on an important, neglected and tractable problem?" },
    { id: "career", name: "Impact on my career path",
      prompt: "To what extent does this thesis allow me to build career capital for a high-impact path?" },
    { id: "community", name: "Impact on my community",
      prompt: "To what extent does this thesis increase the likelihood of positive impact in my community (i.e. peers, university department, social circles)?" },
    { id: "interest", name: "General Thesis Interest",
      prompt: "To what extent am I interested and intrinsically motivated to work on this thesis?" }
  ],
  // WFM(Values) row 7 has a second rationale that sits over Certainty of Pathway to Impact only (G7).
  FACTOR_PROMPTS: { pathway: "To what extent will this thesis result in real-world impact?" },
  // The sheet's twelve criteria, in its order, with its descriptions and weights. Typos fixed only.
  FACTORS: [
    { id: "importance", cat: "problem", name: "The problem: Importance", short: "Importance", w: 5,
      desc: "Does this thesis address a problem with a high scale?", why: "" },
    { id: "neglected", cat: "problem", name: "The problem: Neglectedness", short: "Neglectedness", w: 5,
      desc: "Does this thesis address a problem with a high degree of neglectedness?", why: "" },
    { id: "tractable", cat: "problem", name: "The problem: Tractability", short: "Tractability", w: 5,
      desc: "Does this thesis address a problem with high tractability?", why: "" },
    { id: "pathway", cat: "problem", name: "Certainty of Pathway to Impact", short: "Certainty of pathway", w: 20,
      desc: "To what extent will this thesis result in real-world impact? How clearly can I trace a path from your thesis to real-world change (via influencing actors, decisions, or systems)? To what extent does this thesis directly result in doing good (i.e. improving lives)? Is it clear who/ which stakeholders will use these findings and that the application of these findings will result in real-world impact?",
      why: "Even if a thesis focuses on a problem that is really important, neglected and tractable, it may not result in any real-world impact if there is no clarity on who will use these findings and how." },
    { id: "skills", cat: "career", name: "Skill Building", short: "Skill building", w: 12,
      desc: "To what extent does this thesis allow me to build skill that will increase my ability to do good and succeed in a high-impact career path?", why: "" },
    { id: "relationship", cat: "career", name: "Relationship Building", short: "Relationships", w: 12,
      desc: "To what extent does this thesis allow me to build relationships that will increase my ability to do good and succeed in a high-impact career path?", why: "" },
    { id: "fit-test", cat: "career", name: "Testing Fit", short: "Testing fit", w: 12,
      desc: "To what extent does this thesis allow me to test my fit for a high-impact career path?", why: "" },
    { id: "community", cat: "community", name: "Community Impact", short: "Community impact", w: 15,
      desc: "Could this thesis inspire peers, supervisors, or institutions toward more impactful work?", why: "" },
    { id: "current-fit", cat: "interest", name: "Current Fit", short: "Current fit", w: 5,
      desc: "To what extent am I likely to succeed and be good in working on this thesis, based on my current skillset?", why: "" },
    { id: "motivation", cat: "interest", name: "Motivation", short: "Motivation", w: 3,
      desc: "Am I intrinsically motivated to work on this thesis?", why: "" },
    { id: "novelty", cat: "interest", name: "Novelty", short: "Novelty", w: 3,
      desc: "To what extent will this project expose me to new ideas, people, skills, or opportunities that I have not yet been exposed to?", why: "" },
    { id: "draw", cat: "interest", name: "Intuitive Draw", short: "Intuitive draw", w: 3,
      desc: "What does my intuition rank this option?", why: "" }
  ],
  // The worked example: WFM(Values) rows 10 to 13 (Options #1 to #4), in FACTORS order.
  EXAMPLE: [
    [8, 9, 7, 10, 7, 10, 10, 6, 10, 10, 10, 10],
    [7, 8, 3, 4, 4, 5, 7, 4, 4, 5, 5, 4],
    [9, 7, 1, 2, 4, 8, 7, 5, 4, 3, 6, 4],
    [8, 9, 7, 8, 5, 9, 9, 6, 9, 2, 9, 6]
  ],
  LIMITS: { questions: 25, factors: 20, text: 300, why: 300, src: 200, desc: 600, qdesc: 200, name: 80, rationale: 500, summary: 2000, seed: 10 },
  // The server stores at most 64 KB, counted as json.dumps(ensure_ascii=True) bytes.
  SAVE: { soft: 62000, hard: 65536 },
  TIE: 0.005,

  isNum: function (v) { return typeof v === "number" && isFinite(v); },
  isArr: function (v) { return Object.prototype.toString.call(v) === "[object Array]"; },
  // Slice without splitting a surrogate pair (a lone surrogate makes the server reject the save).
  cut: function (s, n) {
    if (s.length <= n) return s;
    if (n > 0) {
      var c = s.charCodeAt(n - 1);
      if (c >= 0xD800 && c <= 0xDBFF) n--;
    }
    return s.slice(0, n);
  },
  str: function (v, max) { return typeof v === "string" ? WFM.cut(v, max) : ""; },
  fmt: function (n, dp) {
    var p = Math.pow(10, dp), r = Math.round(n * p) / p;
    if (r === 0) r = 0;
    return r.toFixed(dp);
  },
  fmtPct: function (n) {
    var r = Math.round(n * 10) / 10;
    if (r === 0) r = 0;
    return r % 1 === 0 ? String(r) : r.toFixed(1);
  },
  trunc: function (s, n) {
    s = String(s == null ? "" : s).replace(/\s+/g, " ").replace(/^\s+|\s+$/g, "");
    return s.length > n ? WFM.cut(s, Math.max(1, n - 3)).replace(/\s+$/, "") + "..." : s;
  },
  // What the WFM calls a question: its Description if it has one, else the question as written.
  label: function (q) {
    return q && typeof q.desc === "string" && /\S/.test(q.desc) ? q.desc : (q && q.text) || "";
  },
  serverBytes: function (state) {
    var j = JSON.stringify(state);
    var extra = 0;
    for (var i = 0; i < j.length; i++) if (j.charCodeAt(i) > 127) extra += 5;
    return j.length + extra;
  },
  canGrow: function (state) { return WFM.serverBytes(state) < WFM.SAVE.soft; },
  catName: function (catId) {
    for (var i = 0; i < WFM.CATS.length; i++) if (WFM.CATS[i].id === catId) return WFM.CATS[i].name;
    return "";
  },
  catPrompt: function (f) {
    if (WFM.FACTOR_PROMPTS[f.id]) return WFM.FACTOR_PROMPTS[f.id];
    for (var i = 0; i < WFM.CATS.length; i++) if (WFM.CATS[i].id === f.cat) return WFM.CATS[i].prompt;
    return "";
  },
  weightTotal: function (factors) {
    var t = 0;
    for (var i = 0; i < factors.length; i++) t += WFM.isNum(factors[i].w) ? factors[i].w : 0;
    return Math.round(t * 10) / 10;
  },
  catTotal: function (factors, catId) {
    var t = 0;
    for (var i = 0; i < factors.length; i++) if (factors[i].cat === catId && WFM.isNum(factors[i].w)) t += factors[i].w;
    return Math.round(t * 10) / 10;
  },
  weightReadout: function (factors) {
    var t = WFM.weightTotal(factors), off = Math.round((t - 100) * 10) / 10;
    var text = off === 0 ? "Adds up to 100" : (off < 0 ? WFM.fmtPct(-off) + " short of 100" : WFM.fmtPct(off) + " over 100");
    return { total: t, off: off, ok: off === 0, text: text };
  },
  score: function (q, fid) {
    var s = q && q.scores ? q.scores[fid] : null;
    return WFM.isNum(s) && s >= 1 && s <= 10 ? s : null;
  },
  hasText: function (q) { return !!(q && typeof q.text === "string" && /\S/.test(q.text)); },
  scoredCount: function (q, factors) {
    var n = 0;
    for (var i = 0; i < factors.length; i++) if (WFM.score(q, factors[i].id) != null) n++;
    return n;
  },
  isScored: function (q, factors) { return factors.length > 0 && WFM.scoredCount(q, factors) === factors.length; },
  shortlist: function (state) {
    var out = [];
    for (var i = 0; i < state.questions.length; i++) {
      var q = state.questions[i];
      if (q.short && WFM.hasText(q)) out.push(q);
    }
    return out;
  },
  scoredShortlist: function (state) {
    var s = WFM.shortlist(state), out = [];
    for (var i = 0; i < s.length; i++) if (WFM.isScored(s[i], state.factors)) out.push(s[i]);
    return out;
  },
  // The reading's method: score x weight, summed. An inverted factor counts as 11 - score.
  adjusted: function (s, inv) { return inv ? 11 - s : s; },
  weightedParts: function (q, factors) {
    var p = {};
    for (var i = 0; i < factors.length; i++) {
      var f = factors[i], s = WFM.score(q, f.id);
      p[f.id] = s == null ? 0 : WFM.adjusted(s, f.inv) * (WFM.isNum(f.w) ? f.w : 0) / 100;
    }
    return p;
  },
  sumParts: function (parts) {
    var t = 0;
    for (var k in parts) if (Object.prototype.hasOwnProperty.call(parts, k)) t += parts[k];
    return t;
  },
  weighted: function (q, factors) { return WFM.sumParts(WFM.weightedParts(q, factors)); },
  // The sheet's method, corrected: per factor, weight x inversion(+1/-1) x (score - mean) / sample SD
  // across the questions given, summed. A factor where everyone ties adds 0 (the sheet divides by zero).
  standardised: function (qs, factors) {
    var res = { ok: false, reason: "", totals: {}, parts: {}, tied: [] };
    if (qs.length < 2) {
      res.reason = "The standardised score compares your questions with each other, so it needs at least two fully scored questions.";
      return res;
    }
    var i, j, n = qs.length;
    for (i = 0; i < n; i++) { res.parts[qs[i].id] = {}; res.totals[qs[i].id] = 0; }
    for (j = 0; j < factors.length; j++) {
      var f = factors[j], vals = [], mean = 0, ss = 0;
      for (i = 0; i < n; i++) { vals.push(WFM.score(qs[i], f.id)); mean += vals[i]; }
      mean /= n;
      for (i = 0; i < n; i++) ss += (vals[i] - mean) * (vals[i] - mean);
      var sd = Math.sqrt(ss / (n - 1));
      var tied = !(sd > 1e-9);
      if (tied) res.tied.push(f.id);
      var k = (WFM.isNum(f.w) ? f.w : 0) / 100 * (f.inv ? -1 : 1);
      for (i = 0; i < n; i++) {
        var c = tied ? 0 : k * (vals[i] - mean) / sd;
        res.parts[qs[i].id][f.id] = c;
        res.totals[qs[i].id] += c;
      }
    }
    res.ok = true;
    return res;
  },
  rank: function (qs, totals, dir) {
    var idx = [];
    for (var i = 0; i < qs.length; i++) idx.push({ q: qs[i], i: i });
    var sign = dir === "asc" ? -1 : 1;
    idx.sort(function (a, b) {
      var d = totals[b.q.id] - totals[a.q.id];
      if (Math.abs(d) > 1e-12) return sign * d;
      return a.i - b.i;
    });
    var out = [];
    for (var k = 0; k < idx.length; k++) out.push(idx[k].q);
    return out;
  },
  results: function (state) {
    var qs = WFM.scoredShortlist(state), wt = {}, wp = {};
    for (var i = 0; i < qs.length; i++) {
      wp[qs[i].id] = WFM.weightedParts(qs[i], state.factors);
      wt[qs[i].id] = WFM.sumParts(wp[qs[i].id]);
    }
    return { qs: qs, weighted: wt, wParts: wp, std: WFM.standardised(qs, state.factors), order: WFM.rank(qs, wt, "desc") };
  },
  tied: function (a, b) { return Math.abs(a - b) < WFM.TIE; },
  // Per-factor contribution difference a minus b, largest first.
  gap: function (factors, partsA, partsB) {
    var out = [];
    for (var i = 0; i < factors.length; i++) {
      var f = factors[i];
      out.push({ id: f.id, name: f.name, w: f.w, diff: (partsA[f.id] || 0) - (partsB[f.id] || 0) });
    }
    out.sort(function (a, b) { return b.diff - a.diff; });
    return out;
  },
  gutQuestion: function (state) {
    if (!state.gut) return null;
    for (var i = 0; i < state.questions.length; i++) {
      var q = state.questions[i];
      if (q.id === state.gut && q.short && WFM.hasText(q)) return q;
    }
    return null;
  },
  completion: function (state) {
    var missing = [], n = WFM.scoredShortlist(state).length, rd = WFM.weightReadout(state.factors);
    var items = [
      { ok: n >= 2, text: "Score at least two shortlisted questions on every factor (" + n + " so far)" },
      { ok: rd.ok, text: "Make the weights total 100 (" + (rd.ok ? "they do" : rd.text) + ")" },
      { ok: !!WFM.gutQuestion(state), text: "Choose your gut favourite" }
    ];
    for (var i = 0; i < items.length; i++) if (!items[i].ok) missing.push(items[i].text.charAt(0).toLowerCase() + items[i].text.slice(1));
    return { ok: missing.length === 0, missing: missing, items: items, scored: n, readout: rd };
  },
  defaultFactor: function (id) {
    for (var i = 0; i < WFM.FACTORS.length; i++) if (WFM.FACTORS[i].id === id) return WFM.FACTORS[i];
    return null;
  },
  // True when an "ex" row still holds exactly the worked example, so replacing it loses nothing.
  isPristineExample: function (q) {
    var m = /^ex(\d)$/.exec(q.id || "");
    if (!m) return false;
    var r = Number(m[1]) - 1, row = WFM.EXAMPLE[r];
    if (!row || q.text !== "Example question " + (r + 1)) return false;
    if (q.quick != null || /\S/.test((q.why || "") + (q.src || "") + (q.desc || ""))) return false;
    var n = 0;
    for (var k in q.scores) if (Object.prototype.hasOwnProperty.call(q.scores, k)) n++;
    if (n !== WFM.FACTORS.length) return false;
    for (var c = 0; c < WFM.FACTORS.length; c++) if (q.scores[WFM.FACTORS[c].id] !== row[c]) return false;
    return true;
  },
  // True when any worked-example row ("ex" id) is present, edited or not.
  hasExample: function (state) {
    for (var i = 0; i < state.questions.length; i++) if (/^ex\d$/.test(state.questions[i].id || "")) return true;
    return false;
  },
  hasOwnData: function (state) {
    for (var i = 0; i < state.questions.length; i++) {
      var q = state.questions[i];
      if (WFM.isPristineExample(q)) continue;
      if (WFM.hasText(q) || q.quick != null || /\S/.test((q.why || "") + (q.src || "") + (q.desc || ""))) return true;
      for (var k in q.scores) if (Object.prototype.hasOwnProperty.call(q.scores, k)) return true;
    }
    return false;
  },
  defaultsDiff: function (factors) {
    var d = { weights: [], renamed: [], added: [], removed: [], inverted: [] }, seen = {};
    for (var i = 0; i < factors.length; i++) {
      var f = factors[i], base = WFM.defaultFactor(f.id);
      seen[f.id] = true;
      if (f.inv) d.inverted.push(f.name);
      if (!base) { d.added.push(f); continue; }
      if (f.w !== base.w) d.weights.push({ name: f.name, from: base.w, to: f.w });
      if (f.name !== base.name) d.renamed.push({ from: base.name, to: f.name });
    }
    for (var j = 0; j < WFM.FACTORS.length; j++) if (!seen[WFM.FACTORS[j].id]) d.removed.push(WFM.FACTORS[j].name);
    d.none = !d.weights.length && !d.renamed.length && !d.added.length && !d.removed.length;
    return d;
  },
  capList: function (bits, max) {
    if (bits.length <= max) return bits.join(", ");
    return bits.slice(0, max).join(", ") + " and " + (bits.length - max) + " more";
  },
  listQs: function (order, totals, qLen, max, dp) {
    var parts = [];
    for (var i = 0; i < order.length && i < max; i++) {
      parts.push((i + 1) + ". " + WFM.trunc(WFM.label(order[i]), qLen) + " " + WFM.fmt(totals[order[i].id], dp));
    }
    var s = parts.join("; ");
    if (order.length > max) s += "; and " + (order.length - max) + " more";
    return s;
  },
  summaryAt: function (state, qLen, listN, ratN, fLen, fN) {
    var F = state.factors, out = [], i;
    var named = 0;
    for (i = 0; i < state.questions.length; i++) if (WFM.hasText(state.questions[i])) named++;
    var sl = WFM.shortlist(state);
    out.push("Effective Thesis Week 3 weighted factor model. Brainstorm: " + named + " candidate question" + (named === 1 ? "" : "s") + ", " + sl.length + " shortlisted.");
    var rd = WFM.weightReadout(F), cats = [];
    for (i = 0; i < WFM.CATS.length; i++) cats.push(WFM.CATS[i].name + " " + WFM.fmtPct(WFM.catTotal(F, WFM.CATS[i].id)) + "%");
    out.push("Weights by category: " + cats.join(", ") + "; total " + WFM.fmtPct(rd.total) + "% (" + rd.text.toLowerCase() + ").");
    var d = WFM.defaultsDiff(F), bits = [];
    if (d.none) out.push("The " + F.length + " factors and their weights are the sheet's defaults, unchanged.");
    else {
      if (d.weights.length) {
        bits = [];
        for (i = 0; i < d.weights.length; i++) bits.push(WFM.trunc(d.weights[i].name, fLen) + " " + WFM.fmtPct(d.weights[i].from) + "% to " + WFM.fmtPct(d.weights[i].to) + "%");
        out.push("Weights moved from the sheet's defaults: " + WFM.capList(bits, fN) + ".");
      }
      if (d.renamed.length) {
        bits = [];
        for (i = 0; i < d.renamed.length; i++) bits.push(WFM.trunc(d.renamed[i].from, fLen) + " to " + WFM.trunc(d.renamed[i].to, fLen));
        out.push("Renamed: " + WFM.capList(bits, fN) + ".");
      }
      if (d.added.length) {
        bits = [];
        for (i = 0; i < d.added.length; i++) bits.push(WFM.trunc(d.added[i].name, fLen) + " (" + WFM.catName(d.added[i].cat) + ", " + WFM.fmtPct(d.added[i].w) + "%)");
        out.push("Added factors: " + WFM.capList(bits, fN) + ".");
      }
      if (d.removed.length) out.push("Removed factors from the sheet: " + WFM.capList(d.removed, fN) + ".");
    }
    if (d.inverted.length) {
      bits = [];
      for (i = 0; i < d.inverted.length; i++) bits.push(WFM.trunc(d.inverted[i], fLen));
      out.push("Inverted, so higher is worse: " + WFM.capList(bits, fN) + ".");
    }
    var rats = 0;
    for (i = 0; i < F.length && rats < ratN; i++) {
      var base = WFM.defaultFactor(F[i].id);
      if (/\S/.test(F[i].why || "") && !(base && base.why === F[i].why)) {
        out.push("Rationale for " + WFM.trunc(F[i].name, fLen) + ": \"" + WFM.trunc(F[i].why, 120) + "\".");
        rats++;
      }
    }
    var res = WFM.results(state), order = res.order;
    if (order.length < 2) {
      out.push(order.length === 1
        ? "Only one shortlisted question is fully scored (" + WFM.trunc(WFM.label(order[0]), qLen) + ", " + WFM.fmt(res.weighted[order[0].id], 2) + " out of 10), so there is no ranking yet."
        : "No shortlisted question is fully scored yet, so there is no ranking.");
    } else {
      out.push("Ranking on the weighted score, out of 10: " + WFM.listQs(order, res.weighted, qLen, listN, 2) + ".");
      if (res.std.ok) {
        var so = WFM.rank(res.qs, res.std.totals, "desc"), same = true;
        for (i = 0; i < so.length; i++) if (so[i].id !== order[i].id) same = false;
        out.push(same
          ? "The standardised score (the sheet's Sum column, relative to this shortlist) gives the same order."
          : "The standardised score (the sheet's Sum column, relative to this shortlist) orders them differently: " + WFM.listQs(so, res.std.totals, qLen, listN, 2) + ".");
      }
      var g = WFM.gap(F, res.wParts[order[0].id], res.wParts[order[1].id]), pos = [];
      for (i = 0; i < g.length && pos.length < 3; i++) if (g[i].diff > 0.0005) pos.push(WFM.trunc(g[i].name, fLen) + " (+" + WFM.fmt(g[i].diff, 2) + ")");
      var lead = res.weighted[order[0].id] - res.weighted[order[1].id];
      var gs = WFM.tied(res.weighted[order[0].id], res.weighted[order[1].id])
        ? "#1 and #2 tie on the weighted score" + (pos.length ? "; #1 is stronger on " + pos.join(", ") : "")
        : "#1 leads #2 by " + WFM.fmt(lead, 2) + (pos.length ? ", mostly on " + pos.join(", ") : "");
      var last = g[g.length - 1];
      if (last && last.diff < -0.0005) gs += "; #2 is stronger on " + WFM.trunc(last.name, fLen) + " (" + WFM.fmt(last.diff, 2) + ")";
      out.push(gs + ".");
    }
    var partial = sl.length - res.qs.length;
    if (partial > 0) out.push(partial + " shortlisted question" + (partial === 1 ? " is" : "s are") + " not fully scored yet.");
    var gq = WFM.gutQuestion(state);
    if (!gq) out.push("No gut favourite chosen yet.");
    else {
      var at = -1;
      for (i = 0; i < order.length; i++) if (order[i].id === gq.id) at = i;
      var gl = WFM.trunc(WFM.label(gq), qLen);
      if (at === 0) out.push("Gut favourite: " + gl + ", which agrees with the model's #1.");
      else if (at > 0 && WFM.tied(res.weighted[gq.id], res.weighted[order[0].id])) out.push("Gut favourite: " + gl + ", which ties with the model's #1 on the weighted score.");
      else if (at > 0) out.push("Gut favourite: " + gl + ", which the model ranks #" + (at + 1) + " of " + order.length + ", so it DISAGREES with the model's #1 (" + WFM.trunc(WFM.label(order[0]), qLen) + "). That tension is the thing to talk about.");
      else out.push("Gut favourite: " + gl + ", not fully scored yet.");
    }
    var comp = WFM.completion(state);
    out.push(comp.ok ? "The exercise is complete." : "Still to do: " + comp.missing.join("; ") + ".");
    return out.join(" ");
  },
  summary: function (state) {
    // Shrink in steps until it fits; the last resort cuts at a sentence boundary.
    var tries = [[90, 8, 3, 40, 12], [60, 6, 2, 32, 8], [45, 5, 1, 26, 6], [32, 4, 0, 22, 4], [20, 3, 0, 18, 3]], s = "", t;
    for (var i = 0; i < tries.length; i++) {
      t = tries[i];
      s = WFM.summaryAt(state, t[0], t[1], t[2], t[3], t[4]);
      if (s.length <= WFM.LIMITS.summary) return s;
    }
    s = WFM.cut(s, WFM.LIMITS.summary - 3);
    var stop = s.lastIndexOf(". ");
    return (stop > 0 ? s.slice(0, stop + 1) : s) + "..";
  },
  newId: function (prefix) { return prefix + Math.random().toString(36).slice(2, 9); },
  freshFactors: function () {
    var out = [];
    for (var i = 0; i < WFM.FACTORS.length; i++) {
      var f = WFM.FACTORS[i];
      out.push({ id: f.id, cat: f.cat, name: f.name, short: f.short, desc: f.desc, w: f.w, inv: false, why: f.why });
    }
    return out;
  },
  blankQuestion: function (id) { return { id: id, text: "", quick: null, why: "", src: "", desc: "", short: false, scores: {} }; },
  fresh: function () {
    var qs = [];
    for (var i = 1; i <= WFM.LIMITS.seed; i++) qs.push(WFM.blankQuestion("q" + i));
    return { v: 2, factors: WFM.freshFactors(), questions: qs, gut: "", showStd: false, sortBy: "weighted", sortDir: "desc" };
  },
  exampleQuestions: function () {
    var out = [];
    for (var r = 0; r < WFM.EXAMPLE.length; r++) {
      var q = WFM.blankQuestion("ex" + (r + 1));
      q.text = "Example question " + (r + 1);
      q.short = true;
      for (var c = 0; c < WFM.FACTORS.length; c++) q.scores[WFM.FACTORS[c].id] = WFM.EXAMPLE[r][c];
      out.push(q);
    }
    return out;
  },
  cleanScores: function (raw) {
    var out = {};
    if (!raw || typeof raw !== "object") return out;
    for (var k in raw) {
      if (!Object.prototype.hasOwnProperty.call(raw, k)) continue;
      var v = raw[k];
      if (WFM.isNum(v) && v >= 1 && v <= 10) out[k] = Math.round(v);
    }
    return out;
  },
  // Accepts null, a v1 state ({rows, weights, gut}) or a v2 state; never throws.
  migrate: function (saved) {
    try {
      if (!saved || typeof saved !== "object") return WFM.fresh();
      if (saved.v === 2) return WFM.fromV2(saved);
      if (WFM.isArr(saved.rows)) return WFM.fromV1(saved);
    } catch (e) {}
    return WFM.fresh();
  },
  fromV1: function (saved) {
    var st = WFM.fresh(), i, L = WFM.LIMITS;
    if (saved.weights && typeof saved.weights === "object") {
      for (i = 0; i < st.factors.length; i++) {
        var v = saved.weights[st.factors[i].id];
        if (WFM.isNum(v) && v >= 0 && v <= 100) st.factors[i].w = v;
      }
    }
    var kept = [], ids = {};
    for (i = 0; i < saved.rows.length && kept.length < L.questions; i++) {
      var r = saved.rows[i];
      if (!r || typeof r !== "object") continue;
      var q = WFM.blankQuestion(typeof r.id === "string" && r.id && !ids[r.id] ? r.id.slice(0, 40) : WFM.newId("q"));
      ids[q.id] = true;
      q.text = WFM.str(r.question, L.text);
      q.scores = WFM.cleanScores(r.scores);
      var any = false;
      for (var k in q.scores) if (Object.prototype.hasOwnProperty.call(q.scores, k)) any = true;
      if (!WFM.hasText(q) && !any) continue;
      q.short = true;
      kept.push(q);
    }
    if (kept.length) {
      var n = kept.length;
      while (kept.length < L.seed) kept.push(WFM.blankQuestion(WFM.newId("q") + (n++)));
      st.questions = kept;
    }
    if (typeof saved.gut === "string" && ids[saved.gut]) st.gut = saved.gut;
    return st;
  },
  fromV2: function (saved) {
    var st = WFM.fresh(), i, L = WFM.LIMITS, cats = {};
    for (i = 0; i < WFM.CATS.length; i++) cats[WFM.CATS[i].id] = true;
    if (WFM.isArr(saved.factors)) {
      var fs = [], fids = {};
      for (i = 0; i < saved.factors.length && fs.length < L.factors; i++) {
        var f = saved.factors[i];
        if (!f || typeof f !== "object" || typeof f.id !== "string" || !f.id || fids[f.id]) continue;
        fids[f.id] = true;
        fs.push({
          id: f.id.slice(0, 40), cat: cats[f.cat] ? f.cat : "interest",
          name: WFM.str(f.name, L.name), short: WFM.str(f.short, 40), desc: WFM.str(f.desc, L.desc),
          w: WFM.isNum(f.w) && f.w >= 0 && f.w <= 100 ? Math.round(f.w * 10) / 10 : 0,
          inv: f.inv === true, why: WFM.str(f.why, L.rationale)
        });
      }
      st.factors = fs;
    }
    if (WFM.isArr(saved.questions)) {
      var qs = [], qids = {};
      for (i = 0; i < saved.questions.length && qs.length < L.questions; i++) {
        var s = saved.questions[i];
        if (!s || typeof s !== "object" || typeof s.id !== "string" || !s.id || qids[s.id]) continue;
        qids[s.id] = true;
        qs.push({
          id: s.id.slice(0, 40), text: WFM.str(s.text, L.text),
          quick: WFM.isNum(s.quick) && s.quick >= 1 && s.quick <= 10 ? Math.round(s.quick) : null,
          why: WFM.str(s.why, L.why), src: WFM.str(s.src, L.src), desc: WFM.str(s.desc, L.qdesc),
          short: s.short === true, scores: WFM.cleanScores(s.scores)
        });
      }
      st.questions = qs;
    }
    if (typeof saved.gut === "string") st.gut = saved.gut.slice(0, 40);
    st.showStd = saved.showStd === true;
    st.sortBy = saved.sortBy === "std" ? "std" : "weighted";
    st.sortDir = saved.sortDir === "asc" ? "asc" : "desc";
    return st;
  }
};
/* WFM:END */

(function () {
  var STORE_KEY = "et-wfm-v2-preview";
  var state = WFM.fresh();
  var completed = false;
  // Nothing is saved until the saved state has arrived, so early typing cannot overwrite it.
  var hydrated = !window.Lens;
  var open = { brainstorm: true, factors: false, score: false, results: false };
  var ui = { confirm: null, detail: null, editingDesc: {}, openF: {}, openQ: {}, shortN: 5, shortMsg: "" };
  var live = { cats: [], readouts: [], totals: {}, statuses: {} };

  // ---------- tiny DOM helper ----------
  function h(tag, props, kids) {
    var el = document.createElement(tag);
    if (props) {
      for (var k in props) {
        if (!Object.prototype.hasOwnProperty.call(props, k)) continue;
        var v = props[k];
        if (v == null || v === false) continue;
        if (k === "text") el.textContent = v;
        else if (k === "className") el.className = v;
        else if (k.slice(0, 2) === "on") el.addEventListener(k.slice(2), v);
        else if (k === "value") el.value = v;
        else el.setAttribute(k, v === true ? "" : v);
      }
    }
    if (kids) {
      for (var i = 0; i < kids.length; i++) {
        var c = kids[i];
        if (c == null || c === false) continue;
        el.appendChild(typeof c === "string" ? document.createTextNode(c) : c);
      }
    }
    return el;
  }
  function clear(el) { while (el.firstChild) el.removeChild(el.firstChild); }
  function parseScore(raw) {
    var t = String(raw).replace(/\s+/g, "");
    if (t === "") return null;
    var v = Math.round(Number(t));
    if (!isFinite(v)) return null;
    return Math.min(10, Math.max(1, v));
  }

  // ---------- persistence ----------
  function persist() {
    if (!hydrated) return;
    if (window.Lens) {
      if (WFM.serverBytes(state) >= WFM.SAVE.hard) return;
      Lens.saveState(state, WFM.summary(state));
      if (!completed && WFM.completion(state).ok) {
        completed = true;
        Lens.complete();
      }
    } else {
      try { localStorage.setItem(STORE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }
  function changed() { refresh(); persist(); }

  // ---------- step shell ----------
  var STEPS = [
    { id: "brainstorm", num: "Worksheet Steps 2 and 3", title: "Brainstorm and narrow" },
    { id: "factors", num: "Step 4: factors", title: "Choose and weight your factors" },
    { id: "score", num: "Step 4: score", title: "Score your shortlist" },
    { id: "results", num: "Step 4: results", title: "See what rises to the top" }
  ];
  var app = document.getElementById("app");
  var warnEl = document.getElementById("warn");
  var bodies = {};

  function stepStatus(id) {
    var sl = WFM.shortlist(state), named = 0, i;
    for (i = 0; i < state.questions.length; i++) if (WFM.hasText(state.questions[i])) named++;
    if (id === "brainstorm") return { done: sl.length >= 2, text: named + " question" + (named === 1 ? "" : "s") + ", " + sl.length + " shortlisted" };
    if (id === "factors") {
      var rd = WFM.weightReadout(state.factors);
      return { done: rd.ok, text: state.factors.length + " factors, " + (rd.ok ? "weights add up to 100" : rd.text) };
    }
    if (id === "score") {
      var n = WFM.scoredShortlist(state).length;
      return { done: n >= 2 && n === sl.length, text: n + " of " + sl.length + " shortlisted fully scored" };
    }
    var c = WFM.completion(state);
    return { done: c.ok, text: c.ok ? "Complete" : c.missing.length + " thing" + (c.missing.length === 1 ? "" : "s") + " left to finish" };
  }
  function openOnly(id) {
    open = { brainstorm: false, factors: false, score: false, results: false };
    if (id) open[id] = true;
  }
  function chooseOpen() {
    for (var i = 0; i < STEPS.length; i++) {
      if (!stepStatus(STEPS[i].id).done) { openOnly(STEPS[i].id); return; }
    }
    openOnly("results");
  }

  function renderAll() {
    var keepFocus = document.activeElement && document.activeElement.id ? document.activeElement.id : null;
    clear(app);
    bodies = {};
    live = { cats: [], readouts: [], totals: {}, statuses: {} };
    for (var i = 0; i < STEPS.length; i++) {
      (function (s) {
        var st = h("span", { className: "step-status" });
        live.statuses[s.id] = st;
        var head = h("button", {
          type: "button", className: "step-head", "aria-expanded": open[s.id] ? "true" : "false", id: "head-" + s.id,
          onclick: function () { openOnly(open[s.id] ? null : s.id); ui.confirm = null; renderAll(); focusById("head-" + s.id); }
        }, [
          h("span", { className: "step-num", text: s.num }),
          h("span", { className: "step-title", text: s.title }),
          st
        ]);
        var section = h("section", { className: "step", "aria-labelledby": "head-" + s.id }, [head]);
        if (open[s.id]) {
          var body = h("div", { className: "step-body", id: "body-" + s.id });
          bodies[s.id] = body;
          section.appendChild(body);
          RENDER[s.id](body);
        }
        app.appendChild(section);
      })(STEPS[i]);
    }
    refresh();
    if (keepFocus) focusById(keepFocus);
  }
  function focusById(id) {
    var el = document.getElementById(id);
    if (el && el.focus) { try { el.focus(); } catch (e) {} }
  }
  function goTo(id) { openOnly(id); ui.confirm = null; renderAll(); focusById("head-" + id); }
  function nextButton(to, label) {
    return h("div", { className: "actions" }, [
      h("button", { type: "button", className: "primary", id: "next-" + to, text: label, onclick: function () { goTo(to); } })
    ]);
  }
  function confirmBox(key, message, yesLabel, onYes) {
    if (ui.confirm !== key) return null;
    return h("div", { className: "confirm", role: "alertdialog", "aria-label": yesLabel }, [
      h("p", { text: message }),
      h("div", { className: "actions" }, [
        h("button", { type: "button", className: "primary", id: "yes-" + key, text: yesLabel, onclick: function () { ui.confirm = null; onYes(); } }),
        h("button", { type: "button", id: "no-" + key, text: "Cancel", onclick: function () { ui.confirm = null; renderAll(); } })
      ])
    ]);
  }
  function growNote() {
    return WFM.canGrow(state) ? null : h("p", { className: "note", role: "status", text: "You have reached the size limit for saved work, so you cannot add more. Shorten some text if you need room." });
  }

  // ---------- Steps 2 and 3: brainstorm ----------
  function loadExample() {
    state.questions = WFM.exampleQuestions();
    state.gut = "";
    ui.shortMsg = "";
    ui.openQ = {};
    openOnly("results");
    renderAll();
    persist();
  }
  // Back to exactly what a first-time learner gets: the init path's own constructor (migrate(null) is fresh()).
  // Factors and weights are left alone. A completion already sent stays sent; the checklist just shows it as not done.
  function clearExample() {
    var first = WFM.fresh();
    state.questions = first.questions;
    state.gut = first.gut;
    ui.shortMsg = "";
    ui.openQ = {};
    if (ui.detail && ui.detail.slice(0, 2) === "q:") ui.detail = null;
    openOnly("brainstorm");
    renderAll();
    focusById("load-example");
    persist();
  }
  var CLEAR_MSG = "This removes the example questions and their scores, including any changes you made to them. Any questions you added yourself are removed too, so you start again from a blank list. Your factors and weights stay as they are. Clear all questions?";
  function clearExampleButton(id) {
    if (!WFM.hasExample(state)) return null;
    return h("button", { type: "button", id: id, text: "Clear the worked example", onclick: function () {
      if (WFM.hasOwnData(state)) { ui.confirm = "clear-example"; renderAll(); focusById("yes-clear-example"); }
      else clearExample();
    } });
  }
  function clearExampleConfirm() { return confirmBox("clear-example", CLEAR_MSG, "Yes, clear all questions", clearExample); }
  function shortlistTopN() {
    var n = Math.max(1, Math.min(WFM.LIMITS.questions, Math.round(Number(ui.shortN)) || 5));
    var cands = [], i;
    for (i = 0; i < state.questions.length; i++) {
      var q = state.questions[i];
      if (WFM.hasText(q) && q.quick != null) cands.push({ q: q, i: i });
    }
    if (!cands.length) { ui.shortMsg = "Give your questions a quick score first, then this can pick the top ones."; renderAll(); return; }
    cands.sort(function (a, b) { return (b.q.quick - a.q.quick) || (a.i - b.i); });
    for (i = 0; i < state.questions.length; i++) state.questions[i].short = false;
    var take = Math.min(n, cands.length);
    for (i = 0; i < take; i++) cands[i].q.short = true;
    var tie = take < cands.length && cands[take].q.quick === cands[take - 1].q.quick;
    ui.shortMsg = "Shortlisted your top " + take + " by quick score." +
      (tie ? " Some questions tie at the cut-off score of " + cands[take - 1].q.quick + "; the ones higher in your list went in first." : "") +
      (take < n ? " Only " + cands.length + " question" + (cands.length === 1 ? " has" : "s have") + " a quick score." : "") +
      " Change any of them by hand.";
    renderAll();
    persist();
  }
  function renderBrainstorm(body) {
    body.appendChild(h("p", { text: "Use this to first list out your large list of research questions, before simplifying/cleaning them for the WFM! Don't self-censor, and don't over-develop any single idea yet. Capture everything as you go. Aim for 10-20 questions." }));
    body.appendChild(h("p", { className: "hint", text: "Then the quick pass: without doing new research, score each question from 1 to 10 based on what you already know, and narrow your list down to your top 5-10 by shortlisting them." }));
    body.appendChild(h("div", { className: "actions" }, [
      h("button", { type: "button", id: "load-example", text: "Load ET's worked example", onclick: function () {
        if (WFM.hasOwnData(state)) { ui.confirm = "example"; renderAll(); focusById("yes-example"); }
        else loadExample();
      } }),
      clearExampleButton("clear-example"),
      h("span", { className: "hint", text: "Four example questions with the worked example's scores, to see how it works." })
    ]));
    var cb = confirmBox("example", "This replaces your questions, quick scores and scores with the four worked example questions. Your factors and weights stay as they are. Replace them?", "Yes, replace my questions", loadExample);
    if (cb) body.appendChild(cb);
    var cc = clearExampleConfirm();
    if (cc) body.appendChild(cc);

    body.appendChild(h("div", { className: "qhdr", "aria-hidden": "true" }, [
      h("span", { text: "#" }), h("span", { text: "Candidate question" }), h("span", { text: "Quick score (1-10)" }),
      h("span", { text: "Why it matters" }), h("span", { text: "Source / Inspiration" }), h("span", { text: "" })
    ]));
    for (var i = 0; i < state.questions.length; i++) body.appendChild(questionRow(state.questions[i], i));

    var full = state.questions.length >= WFM.LIMITS.questions || !WFM.canGrow(state);
    var nIn = h("input", { type: "number", className: "num", id: "short-n", min: "1", max: String(WFM.LIMITS.questions), value: String(ui.shortN),
      oninput: function () { ui.shortN = nIn.value; } });
    body.appendChild(h("div", { className: "actions" }, [
      h("button", { type: "button", id: "add-q", disabled: full,
        text: state.questions.length >= WFM.LIMITS.questions ? "That is the maximum of " + WFM.LIMITS.questions : "Add a question",
        onclick: function () {
          if (!WFM.canGrow(state)) return;
          state.questions.push(WFM.blankQuestion(WFM.newId("q")));
          renderAll(); focusById("q-" + (state.questions.length - 1) + "-text"); persist();
        } })
    ]));
    var gn = growNote();
    if (gn) body.appendChild(gn);
    body.appendChild(h("div", { className: "actions" }, [
      h("label", { "for": "short-n", text: "Shortlist my top" }), nIn,
      h("button", { type: "button", id: "short-top", text: "by quick score", onclick: shortlistTopN })
    ]));
    if (ui.shortMsg) body.appendChild(h("p", { className: "note", role: "status", text: ui.shortMsg }));
    body.appendChild(nextButton("factors", "Next: your factors and weights"));
  }
  function questionRow(q, i) {
    var pid = "q-" + i;
    var textIn = h("textarea", { id: pid + "-text", rows: "2", maxlength: String(WFM.LIMITS.text), placeholder: "A candidate research question", value: q.text,
      oninput: function () { q.text = textIn.value; changed(); } });
    var quickIn = h("input", { type: "text", inputmode: "numeric", className: "num", id: pid + "-quick", maxlength: "2", value: q.quick == null ? "" : String(q.quick),
      oninput: function () {
        var v = parseScore(quickIn.value);
        q.quick = v;
        if (v != null && String(v) !== quickIn.value.replace(/\s+/g, "")) quickIn.value = String(v);
        changed();
      } });
    var whyIn = h("textarea", { id: pid + "-why", rows: "2", maxlength: String(WFM.LIMITS.why), value: q.why, oninput: function () { q.why = whyIn.value; changed(); } });
    var srcIn = h("textarea", { id: pid + "-src", rows: "2", maxlength: String(WFM.LIMITS.src), value: q.src, oninput: function () { q.src = srcIn.value; changed(); } });
    var isOpen = !!ui.openQ[q.id];
    var more = h("div", { className: "qmore" + (isOpen ? " is-open" : ""), id: pid + "-more" }, [
      h("div", null, [h("label", { className: "f", "for": pid + "-why", text: "Why it matters" }), whyIn]),
      h("div", null, [h("label", { className: "f", "for": pid + "-src", text: "Source / Inspiration" }), srcIn])
    ]);
    if (q.short) {
      var descIn = h("textarea", { id: pid + "-desc", rows: "2", maxlength: String(WFM.LIMITS.qdesc), value: q.desc,
        placeholder: "Optional: your simplified/cleaned version for the WFM",
        oninput: function () { q.desc = descIn.value; changed(); } });
      more.appendChild(h("div", { className: "qdesc" }, [
        h("label", { className: "f", "for": pid + "-desc", text: "Description" }), descIn,
        h("p", { className: "note", text: "If you write one, the score grid, the ranking and your gut pick use it instead of the question as written." })
      ]));
    }
    var shortBtn = h("button", { type: "button", className: "toggle small", id: pid + "-short", "aria-pressed": q.short ? "true" : "false",
      text: q.short ? "Shortlisted" : "Shortlist",
      onclick: function () { q.short = !q.short; if (!q.short && state.gut === q.id) state.gut = ""; renderAll(); persist(); } });
    var moreBtn = h("button", { type: "button", className: "small only-m", id: pid + "-details", "aria-expanded": isOpen ? "true" : "false", "aria-controls": pid + "-more",
      text: isOpen ? "Hide details" : "Details",
      onclick: function () { if (ui.openQ[q.id]) delete ui.openQ[q.id]; else ui.openQ[q.id] = true; renderAll(); } });
    var rm = h("button", { type: "button", className: "link", id: pid + "-rm", text: "Remove", "aria-label": "Remove question " + (i + 1),
      onclick: function () {
        state.questions.splice(i, 1);
        if (state.gut === q.id) state.gut = "";
        renderAll(); persist();
      } });
    return h("div", { className: "qrow" + (q.short ? " is-short" : "") }, [
      h("span", { className: "n", text: String(i + 1) }),
      h("div", { className: "qq" }, [h("label", { className: "f", "for": pid + "-text", text: "Candidate question" }), textIn]),
      h("div", { className: "qquick" }, [h("label", { className: "f", "for": pid + "-quick", text: "Quick score (1-10)" }), quickIn]),
      more,
      h("div", { className: "qact" }, [shortBtn, moreBtn, rm])
    ]);
  }

  // ---------- Step 4: factors ----------
  function meter() {
    var big = h("span", { className: "big" }), note = h("span");
    live.readouts.push({ big: big, note: note });
    return h("div", { className: "meter", role: "status" }, [h("span", null, ["Weights total ", big]), note]);
  }
  function renderFactors(body) {
    body.appendChild(h("p", { text: "Choose your factors, the criteria you'll judge each question against. We highly recommend you consider what factors are truly important to you when deciding on your thesis topic! Then weight each factor based on what matters most to you, for example, splitting 100 points across your chosen factors." }));
    body.appendChild(h("p", { className: "hint", text: "These start as the example factors and weights from Effective Thesis's spreadsheet. The weighting of each will be highly personal and subjective to you. Open a factor's details to read its description and write your rationale for its weight." }));
    body.appendChild(meter());
    for (var c = 0; c < WFM.CATS.length; c++) {
      (function (cat) {
        var tot = h("span", { className: "tot" });
        live.cats.push({ id: cat.id, el: tot, suffix: "% overall weight" });
        var wrap = h("div", { className: "cat" }, [
          h("div", { className: "cat-head" }, [h("h3", { text: cat.name }), tot]),
          h("p", { className: "cat-prompt", text: cat.prompt })
        ]);
        for (var i = 0; i < state.factors.length; i++) {
          var f = state.factors[i];
          if (f.cat !== cat.id) continue;
          if (WFM.FACTOR_PROMPTS[f.id]) wrap.appendChild(h("p", { className: "cat-prompt", text: WFM.FACTOR_PROMPTS[f.id] }));
          wrap.appendChild(factorBlock(f, i));
        }
        var tooMany = state.factors.length >= WFM.LIMITS.factors || !WFM.canGrow(state);
        wrap.appendChild(h("div", { className: "actions" }, [
          h("button", { type: "button", className: "small", id: "add-f-" + cat.id, disabled: tooMany, text: "Add a factor to " + cat.name,
            onclick: function () {
              if (!WFM.canGrow(state)) return;
              var nf = { id: WFM.newId("f"), cat: cat.id, name: "", short: "", desc: "", w: 0, inv: false, why: "" };
              var at = 0;
              for (var k = 0; k < state.factors.length; k++) if (state.factors[k].cat === cat.id) at = k + 1;
              if (!at) { for (var cc = 0; cc < WFM.CATS.length && WFM.CATS[cc].id !== cat.id; cc++) { for (var k2 = 0; k2 < state.factors.length; k2++) if (state.factors[k2].cat === WFM.CATS[cc].id) at = k2 + 1; } }
              state.factors.splice(at, 0, nf);
              ui.editingDesc[nf.id] = true;
              ui.openF[nf.id] = true;
              renderAll(); focusById("f-" + nf.id + "-name"); persist();
            } })
        ]));
        body.appendChild(wrap);
      })(WFM.CATS[c]);
    }
    var gn = growNote();
    if (gn) body.appendChild(gn);
    body.appendChild(meter());
    body.appendChild(h("div", { className: "actions" }, [
      h("button", { type: "button", id: "reset-f", text: "Reset to the example factors and weights", onclick: function () { ui.confirm = "reset"; renderAll(); focusById("yes-reset"); } })
    ]));
    var cb = confirmBox("reset", "This puts back the spreadsheet's twelve factors, descriptions and weights and clears your inversions and rationales. Your questions and their scores stay. Reset?", "Yes, reset my factors", function () {
      state.factors = WFM.freshFactors(); ui.editingDesc = {}; ui.openF = {}; renderAll(); persist();
    });
    if (cb) body.appendChild(cb);
    body.appendChild(nextButton("score", "Next: score your shortlist"));
  }
  function factorBlock(f, idx) {
    var pid = "f-" + f.id;
    var nameIn = h("input", { type: "text", id: pid + "-name", maxlength: String(WFM.LIMITS.name), value: f.name, placeholder: "Name this factor",
      oninput: function () { f.name = nameIn.value; if (!WFM.defaultFactor(f.id)) f.short = ""; changed(); } });
    var wIn = h("input", { type: "number", className: "num", id: pid + "-w", min: "0", max: "100", step: "1", value: String(f.w), "aria-label": "Weight for " + (f.name || "this factor") + ", percent",
      oninput: function () {
        var v = wIn.value === "" ? 0 : Number(wIn.value);
        if (!isFinite(v) || v < 0) v = 0;
        if (v > 100) v = 100;
        f.w = Math.round(v * 10) / 10;
        changed();
      } });
    var invBtn = h("button", { type: "button", className: "toggle small", id: pid + "-inv", "aria-pressed": f.inv ? "true" : "false",
      title: "Inversion: " + (f.inv ? "a high score counts against the question" : "a high score counts for the question"),
      text: f.inv ? "Higher is worse" : "Higher is better",
      onclick: function () { f.inv = !f.inv; renderAll(); persist(); } });
    var isOpen = !!ui.openF[f.id];
    var hasWhy = /\S/.test(f.why || "");
    var moreBtn = h("button", { type: "button", className: "small", id: pid + "-details", "aria-expanded": isOpen ? "true" : "false", "aria-controls": pid + "-more",
      text: isOpen ? "Hide details" : (hasWhy ? "Details (rationale written)" : "Details"),
      onclick: function () { if (ui.openF[f.id]) delete ui.openF[f.id]; else ui.openF[f.id] = true; renderAll(); } });
    var kids = [
      h("div", { className: "frow" }, [
        h("div", null, [h("label", { className: "f", "for": pid + "-name", text: "Factor" }), nameIn]),
        h("div", { className: "fctl" }, [h("span", { className: "wbox" }, [wIn, h("span", { text: "%" })]), invBtn, moreBtn])
      ])
    ];
    if (isOpen) {
      var more = h("div", { className: "fmore", id: pid + "-more" });
      if (ui.editingDesc[f.id]) {
        var dIn = h("textarea", { id: pid + "-desc", rows: "3", maxlength: String(WFM.LIMITS.desc), value: f.desc, placeholder: "What question does this factor ask of each thesis?",
          oninput: function () { f.desc = dIn.value; changed(); } });
        more.appendChild(h("label", { className: "f", "for": pid + "-desc", text: "Description" }));
        more.appendChild(dIn);
        more.appendChild(h("button", { type: "button", className: "link", id: pid + "-done", text: "Done editing", onclick: function () { delete ui.editingDesc[f.id]; renderAll(); focusById(pid + "-edit"); } }));
      } else {
        more.appendChild(h("p", { className: "desc", text: f.desc || "No description yet." }));
        more.appendChild(h("button", { type: "button", className: "link", id: pid + "-edit", text: "Edit description", onclick: function () { ui.editingDesc[f.id] = true; renderAll(); focusById(pid + "-desc"); } }));
      }
      var whyIn = h("textarea", { id: pid + "-why", rows: "2", maxlength: String(WFM.LIMITS.rationale), value: f.why,
        placeholder: "Why does this factor get this weight for you?", oninput: function () { f.why = whyIn.value; changed(); } });
      more.appendChild(h("label", { className: "f", "for": pid + "-why", text: "Rationale for weight" }));
      more.appendChild(whyIn);
      more.appendChild(h("div", { className: "actions" }, [h("button", { type: "button", className: "link", id: pid + "-rm", text: "Remove this factor", "aria-label": "Remove factor " + (f.name || (idx + 1)),
        onclick: function () {
          state.factors.splice(idx, 1);
          for (var i = 0; i < state.questions.length; i++) delete state.questions[i].scores[f.id];
          if (ui.detail === "f:" + f.id) ui.detail = null;
          renderAll(); persist();
        } })]));
      kids.push(more);
    }
    return h("div", { className: "factor" }, kids);
  }

  // ---------- Step 4: score ----------
  function shortName(f) {
    if (f.short) return f.short;
    return WFM.trunc(f.name || "Unnamed factor", 18);
  }
  function detailBox() {
    var box = h("div", { className: "detail", id: "detail", "aria-live": "polite" });
    var kind = ui.detail ? ui.detail.slice(0, 2) : "", id = ui.detail ? ui.detail.slice(2) : "", i;
    if (kind === "f:") {
      for (i = 0; i < state.factors.length; i++) if (state.factors[i].id === id) {
        var f = state.factors[i];
        box.appendChild(h("p", null, [h("strong", { text: (f.name || "Unnamed factor") + " " }), h("span", { className: "hint", text: WFM.catName(f.cat) + ", " + WFM.fmtPct(f.w) + "%" + (f.inv ? ", higher is worse" : "") })]));
        box.appendChild(h("p", { className: "cat-prompt", text: WFM.catPrompt(f) }));
        box.appendChild(h("p", { text: f.desc || "No description yet." }));
        return box;
      }
    }
    if (kind === "q:") {
      for (i = 0; i < state.questions.length; i++) if (state.questions[i].id === id) {
        var q = state.questions[i];
        box.appendChild(h("p", null, [h("strong", { text: WFM.label(q) })]));
        if (WFM.label(q) !== q.text) box.appendChild(h("p", { text: "Original question: " + q.text }));
        if (/\S/.test(q.why)) box.appendChild(h("p", { text: "Why it matters: " + q.why }));
        return box;
      }
    }
    box.appendChild(h("p", { className: "hint", text: "Tap a factor or a question in the grid to see it in full here." }));
    return box;
  }
  function renderScore(body) {
    body.appendChild(h("p", { text: "Score each question against each factor, on a 1-10 scale. Tap a factor's name to see what it asks." }));
    var sl = WFM.shortlist(state);
    if (sl.length < 1 || !state.factors.length) {
      var to = !state.factors.length ? "factors" : "brainstorm";
      body.appendChild(h("p", { className: "note", text: !state.factors.length ? "Add at least one factor first." : "Shortlist the questions you want to compare in the brainstorm first, or load the worked example there." }));
      body.appendChild(h("div", { className: "actions" }, [h("button", { type: "button", id: "goto-" + to, text: !state.factors.length ? "Go to your factors" : "Go to the brainstorm", onclick: function () { goTo(to); } })]));
      return;
    }
    body.appendChild(detailBox());
    var catRow = h("tr", null, [h("th", { className: "qcol", rowspan: "2", scope: "col", text: "Question" })]);
    var fRow = h("tr");
    var c, i;
    for (c = 0; c < WFM.CATS.length; c++) {
      var n = 0;
      for (i = 0; i < state.factors.length; i++) if (state.factors[i].cat === WFM.CATS[c].id) n++;
      if (!n) continue;
      var w = h("span", { className: "w" });
      live.cats.push({ id: WFM.CATS[c].id, el: w, suffix: "%" });
      catRow.appendChild(h("th", { className: "catcol", colspan: String(n), scope: "colgroup", title: WFM.CATS[c].prompt }, [WFM.CATS[c].name, w]));
      for (i = 0; i < state.factors.length; i++) {
        (function (f) {
          if (f.cat !== WFM.CATS[c].id) return;
          fRow.appendChild(h("th", { scope: "col" }, [h("button", { type: "button", className: "colhead" + (f.inv ? " is-inv" : ""), id: "col-" + f.id, title: f.name,
            "aria-label": (f.name || "Unnamed factor") + ": show description", "aria-controls": "detail",
            text: shortName(f), onclick: function () { ui.detail = "f:" + f.id; renderAll(); focusById("col-" + f.id); } })]));
        })(state.factors[i]);
      }
    }
    catRow.appendChild(h("th", { rowspan: "2", scope: "col", text: "Weighted score" }));
    var tbody = h("tbody");
    for (var r = 0; r < sl.length; r++) {
      (function (q) {
        var lbl = WFM.label(q);
        var tr = h("tr", null, [h("th", { className: "qcol", scope: "row" }, [h("button", { type: "button", className: "rowhead", id: "row-" + q.id,
          title: lbl !== q.text ? "Original question: " + q.text : q.text, "aria-controls": "detail",
          onclick: function () { ui.detail = "q:" + q.id; renderAll(); focusById("row-" + q.id); } }, [h("span", { className: "qtext", text: lbl })])])]);
        for (var c2 = 0; c2 < WFM.CATS.length; c2++) {
          for (var j = 0; j < state.factors.length; j++) {
            (function (f) {
              if (f.cat !== WFM.CATS[c2].id) return;
              var s = WFM.score(q, f.id);
              var inp = h("input", { type: "text", inputmode: "numeric", maxlength: "2", className: "cell", id: "s-" + q.id + "-" + f.id,
                "aria-label": WFM.trunc(lbl, 60) + ", " + (f.name || "Unnamed factor") + ", score 1 to 10", value: s == null ? "" : String(s),
                oninput: function () {
                  var v = parseScore(inp.value);
                  if (v == null) delete q.scores[f.id]; else q.scores[f.id] = v;
                  if (v != null && String(v) !== inp.value.replace(/\s+/g, "")) inp.value = String(v);
                  changed();
                } });
              tr.appendChild(h("td", null, [inp]));
            })(state.factors[j]);
          }
        }
        var tot = h("td", { className: "tot" });
        live.totals[q.id] = tot;
        tr.appendChild(tot);
        tbody.appendChild(tr);
      })(sl[r]);
    }
    body.appendChild(h("div", { className: "scroll", role: "region", "aria-label": "Score grid", tabindex: "0" }, [
      h("table", { className: "grid" }, [h("thead", null, [catRow, fRow]), tbody])
    ]));
    body.appendChild(h("p", { className: "note", text: "The weighted score is each score times its weight, with the weight as a fraction (5% = 0.05), summed across factors: out of 10 when your weights total 100. For a factor marked higher is worse, it counts 11 minus the score." }));
    body.appendChild(nextButton("results", "Next: see the results"));
  }

  // ---------- Step 4: results ----------
  var STAR = "⭐ If your top-scoring question isn't your gut favourite, sit with that tension for a moment before deciding, don't just override the model, and don't just override your gut.";
  function renderResults(body) {
    var clr = clearExampleButton("clear-example-results");
    if (clr) {
      body.appendChild(h("div", { className: "actions" }, [clr, h("span", { className: "hint", text: "Done exploring? This puts back a blank list for your own questions." })]));
      var cc = clearExampleConfirm();
      if (cc) body.appendChild(cc);
    }
    var comp = WFM.completion(state);
    var ul = h("ul", { className: "check" });
    for (var i = 0; i < comp.items.length; i++) {
      ul.appendChild(h("li", null, [h("span", { className: "mark", text: comp.items[i].ok ? "Done" : "To do" }), comp.items[i].text]));
    }
    body.appendChild(h("p", { className: "hint", text: "To finish this exercise:" }));
    body.appendChild(ul);

    var res = WFM.results(state);
    if (res.order.length < 2) {
      body.appendChild(h("p", { className: "note", text: res.order.length === 1
        ? "One question is fully scored. Score at least one more shortlisted question on every factor to see a ranking."
        : "Score at least two shortlisted questions on every factor to see a ranking." }));
      body.appendChild(stdNotes(res));
    } else {
      body.appendChild(rankTable(res));
      body.appendChild(stdNotes(res));
      body.appendChild(gapBlock(res));
    }
    body.appendChild(gutBlock(res));
    if (window.Lens && Lens.promptTutor && res.order.length >= 2) {
      body.appendChild(h("div", { className: "actions" }, [h("button", { type: "button", id: "ask", text: "Ask the tutor to challenge my top choice", onclick: function () {
        Lens.promptTutor(
          "I have scored my research questions in the weighted factor model. Can you challenge my top choice?",
          "The learner has filled in Effective Thesis's Week 3 weighted factor model. Their model: " + WFM.summary(state) +
          " There is no answer key. Pick the single factor doing the most work in separating first from second and ask whether they really believe its weight. If their gut favourite differs from the model's top pick, ask what the model is not capturing rather than telling them which to trust."
        );
      } })]));
    }
  }
  function rankTable(res) {
    var showStd = state.showStd && res.std.ok;
    var key = showStd && state.sortBy === "std" ? "std" : "weighted";
    var totals = key === "std" ? res.std.totals : res.weighted;
    var order = WFM.rank(res.qs, totals, state.sortDir);
    var primaryRank = {};
    for (var i = 0; i < res.order.length; i++) primaryRank[res.order[i].id] = i + 1;
    var min = Infinity, max = -Infinity;
    for (i = 0; i < res.qs.length; i++) { var t = totals[res.qs[i].id]; if (t < min) min = t; if (t > max) max = t; }
    function sortBtn(k, label) {
      var on = key === k;
      return h("button", { type: "button", id: "sort-" + k, "aria-label": label + ": sort " + (on && state.sortDir === "desc" ? "lowest first" : "highest first"),
        text: label + (on ? (state.sortDir === "desc" ? " (high to low)" : " (low to high)") : ""),
        onclick: function () {
          if (state.sortBy === k) state.sortDir = state.sortDir === "desc" ? "asc" : "desc";
          else { state.sortBy = k; state.sortDir = "desc"; }
          renderAll(); focusById("sort-" + k); persist();
        } });
    }
    var head = h("tr", null, [h("th", { scope: "col", text: "#" }), h("th", { scope: "col", text: "Question" }),
      h("th", { scope: "col" }, [sortBtn("weighted", "Weighted score, out of 10")])]);
    if (showStd) head.appendChild(h("th", { scope: "col" }, [sortBtn("std", "Standardised score (the sheet's Sum)")]));
    var tb = h("tbody");
    for (i = 0; i < order.length; i++) {
      var q = order[i];
      var v = totals[q.id];
      var alpha = max - min > 1e-9 ? 0.08 + 0.42 * (v - min) / (max - min) : 0.25;
      var shade = "rgba(184,112,24," + alpha.toFixed(3) + ")";
      var lbl = WFM.label(q);
      var qCell = h("td", { className: "ql", title: lbl !== q.text ? "Original question: " + q.text : null }, [lbl]);
      if (lbl !== q.text) qCell.appendChild(h("span", { className: "orig", text: "Question: " + WFM.trunc(q.text, 140) }));
      var wCell = h("td", { className: "t", text: WFM.fmt(res.weighted[q.id], 2) });
      var row = h("tr", { className: primaryRank[q.id] === 1 ? "is-top" : null }, [
        h("td", { className: "n", text: String(primaryRank[q.id]) }),
        qCell,
        wCell
      ]);
      if (showStd) {
        var sCell = h("td", { className: "t", text: WFM.fmt(res.std.totals[q.id], 4) });
        row.appendChild(sCell);
        (key === "std" ? sCell : wCell).style.background = shade;
      } else wCell.style.background = shade;
      tb.appendChild(row);
    }
    return h("div", null, [
      h("h4", { text: "Your ranking" }),
      h("div", { className: "scroll" }, [h("table", { className: "rank" }, [h("thead", null, [head]), tb])]),
      h("p", { className: "note", text: "# is the rank on the weighted score: each score times its weight, with the weight as a fraction (5% = 0.05), summed across factors (out of 10 when the weights total 100). The shading follows the column you sort by: darker is higher." })
    ]);
  }
  function stdNotes(res) {
    var wrap = h("div");
    var btn = h("button", { type: "button", className: "toggle", id: "toggle-std", "aria-pressed": state.showStd ? "true" : "false",
      text: state.showStd ? "Hide the standardised score" : "Show the standardised score (the spreadsheet's method)",
      onclick: function () { state.showStd = !state.showStd; if (!state.showStd) state.sortBy = "weighted"; renderAll(); focusById("toggle-std"); persist(); } });
    wrap.appendChild(h("div", { className: "actions" }, [btn]));
    if (state.showStd) {
      if (!res.std.ok) wrap.appendChild(h("p", { className: "note", id: "std-hidden", text: res.std.reason + " It is hidden until then." }));
      else {
        wrap.appendChild(h("p", { className: "note", text: "The standardised score is how Effective Thesis's spreadsheet ranks options (its Sum column). For each factor, it takes how far a question's score sits from the average, divided by how spread out the scores are (the sample standard deviation), times the weight, times -1 if higher is worse, and adds these up. 0 means average. It is relative to the fully scored questions on your shortlist: adding, removing or rescoring any of them changes every number." }));
        if (res.std.tied.length) {
          var names = [];
          for (var i = 0; i < state.factors.length; i++) if (res.std.tied.indexOf(state.factors[i].id) !== -1) names.push(state.factors[i].name || "Unnamed factor");
          wrap.appendChild(h("p", { className: "note", text: "Every shortlisted question has the same score on " + names.join(", ") + ", so " + (names.length === 1 ? "it cannot separate them and adds" : "these cannot separate them and add") + " 0 to the standardised score." }));
        }
      }
    }
    return wrap;
  }
  function gapBlock(res) {
    var a = res.order[0], b = res.order[1];
    var g = WFM.gap(state.factors, res.wParts[a.id], res.wParts[b.id]);
    var tie = WFM.tied(res.weighted[a.id], res.weighted[b.id]);
    var wrap = h("div", null, [h("h4", { text: "What separates #1 from #2" })]);
    wrap.appendChild(h("p", { text: tie
      ? WFM.trunc(WFM.label(a), 120) + " ties with " + WFM.trunc(WFM.label(b), 120) + " on the weighted score (" + WFM.fmt(res.weighted[a.id], 2) + " each), for different reasons:"
      : WFM.trunc(WFM.label(a), 120) + " leads " + WFM.trunc(WFM.label(b), 120) + " by " + WFM.fmt(res.weighted[a.id] - res.weighted[b.id], 2) + " points out of 10." }));
    var ul = h("ul", { className: "drivers" }), n = 0;
    for (var i = 0; i < g.length && n < 3; i++) {
      if (g[i].diff <= 0.0005) break;
      ul.appendChild(h("li", { text: (g[i].name || "Unnamed factor") + ": +" + WFM.fmt(g[i].diff, 2) + " for #1 (weight " + WFM.fmtPct(g[i].w) + "%)" }));
      n++;
    }
    var last = g[g.length - 1];
    if (last && last.diff < -0.0005) ul.appendChild(h("li", { text: (last.name || "Unnamed factor") + ": " + WFM.fmt(last.diff, 2) + ", where #2 is stronger (weight " + WFM.fmtPct(last.w) + "%)" }));
    if (!n && !(last && last.diff < -0.0005)) ul.appendChild(h("li", { text: "They score the same on every factor." }));
    wrap.appendChild(ul);
    return wrap;
  }
  function gutBlock(res) {
    var sl = WFM.shortlist(state);
    var wrap = h("div");
    if (sl.length < 2) return wrap;
    var sel = h("select", { id: "gut", onchange: function () { state.gut = sel.value; renderAll(); focusById("gut"); persist(); } });
    sel.appendChild(h("option", { value: "", text: "Choose one" }));
    for (var i = 0; i < sl.length; i++) {
      var lbl = WFM.label(sl[i]);
      sel.appendChild(h("option", { value: sl[i].id, text: WFM.trunc(lbl, 90), title: lbl !== sl[i].text ? "Original question: " + sl[i].text : null }));
    }
    sel.value = WFM.gutQuestion(state) ? state.gut : "";
    wrap.appendChild(h("h4", { text: "Your gut favourite" }));
    wrap.appendChild(h("label", { className: "hint", "for": "gut", text: "Setting the numbers aside: which question do you most want to work on?" }));
    wrap.appendChild(h("div", null, [sel]));
    var box = h("div", { className: "tension", role: "status" });
    var gq = WFM.gutQuestion(state);
    if (gq && res.order.length >= 2) {
      var top = res.order[0];
      var at = -1;
      for (i = 0; i < res.order.length; i++) if (res.order[i].id === gq.id) at = i;
      if (at === 0) box.appendChild(h("p", { text: "Your model and your gut agree: " + WFM.trunc(WFM.label(top), 120) + " comes out on top." }));
      else if (at > 0 && WFM.tied(res.weighted[gq.id], res.weighted[top.id])) box.appendChild(h("p", { text: "Your gut favourite, " + WFM.trunc(WFM.label(gq), 120) + ", ties with the model's top pick on the weighted score (" + WFM.fmt(res.weighted[gq.id], 2) + ")." }));
      else if (at > 0) {
        box.appendChild(h("p", { text: "Your model puts " + WFM.trunc(WFM.label(top), 120) + " on top (" + WFM.fmt(res.weighted[top.id], 2) + "), but your gut picked " + WFM.trunc(WFM.label(gq), 120) + " (#" + (at + 1) + ", " + WFM.fmt(res.weighted[gq.id], 2) + ")." }));
        var g = WFM.gap(state.factors, res.wParts[top.id], res.wParts[gq.id]);
        if (g.length && g[0].diff > 0.0005) box.appendChild(h("p", { text: "Your gut favourite loses most ground on " + (g[0].name || "an unnamed factor") + ", a factor you gave " + WFM.fmtPct(g[0].w) + "%. Is that weight what you really believe, or is a factor you care about missing?" }));
      } else box.appendChild(h("p", { text: "Your gut favourite is not fully scored yet, so the model cannot place it." }));
    }
    box.appendChild(h("p", { text: STAR }));
    wrap.appendChild(box);
    return wrap;
  }

  var RENDER = { brainstorm: renderBrainstorm, factors: renderFactors, score: renderScore, results: renderResults };

  // ---------- live refresh (no rebuild of what the learner is typing in) ----------
  function setTotals() {
    for (var id in live.totals) {
      if (!Object.prototype.hasOwnProperty.call(live.totals, id)) continue;
      for (var i = 0; i < state.questions.length; i++) if (state.questions[i].id === id) {
        var q = state.questions[i];
        live.totals[id].textContent = WFM.isScored(q, state.factors) ? WFM.fmt(WFM.weighted(q, state.factors), 2) : WFM.scoredCount(q, state.factors) + "/" + state.factors.length;
      }
    }
  }
  function refresh() {
    var i, rd = WFM.weightReadout(state.factors);
    var bytes = WFM.serverBytes(state);
    warnEl.hidden = bytes < WFM.SAVE.soft;
    warnEl.textContent = bytes >= WFM.SAVE.hard
      ? "Too much text to save: your latest changes are not being saved. Shorten some of your text to keep saving."
      : "You are close to the size limit for saved work, so adding questions and factors is paused.";
    // Results and the score grid are derived views: rebuild them unless the learner is typing inside them.
    var act = document.activeElement;
    if (bodies.results && !(act && bodies.results.contains(act))) { clear(bodies.results); renderResults(bodies.results); }
    if (bodies.score && !(act && bodies.score.contains(act))) {
      var cats = [];
      for (i = 0; i < live.cats.length; i++) if (!bodies.score.contains(live.cats[i].el)) cats.push(live.cats[i]);
      live.cats = cats; live.totals = {};
      clear(bodies.score); renderScore(bodies.score);
    }
    for (i = 0; i < live.readouts.length; i++) {
      live.readouts[i].big.textContent = WFM.fmtPct(rd.total) + "%";
      live.readouts[i].note.textContent = rd.ok ? "Adds up to 100" : rd.text;
      live.readouts[i].note.className = rd.ok ? "" : "off";
    }
    for (i = 0; i < live.cats.length; i++) live.cats[i].el.textContent = WFM.fmtPct(WFM.catTotal(state.factors, live.cats[i].id)) + live.cats[i].suffix;
    setTotals();
    for (i = 0; i < STEPS.length; i++) {
      var s = stepStatus(STEPS[i].id), el = live.statuses[STEPS[i].id];
      if (!el) continue;
      el.textContent = (s.done ? "Done: " : "") + s.text;
      el.className = "step-status" + (s.done ? " is-done" : "");
    }
  }

  // ---------- boot ----------
  function hydrate(saved, meta) {
    state = WFM.migrate(saved);
    completed = !!(meta && meta.completed);
    hydrated = true;
    ui.confirm = null;
    chooseOpen();
    renderAll();
  }

  chooseOpen();
  renderAll();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = localStorage.getItem(STORE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
})();
</script>
</body>
</html>
