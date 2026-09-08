---
id: 'b709e4a5-86f1-4bd0-b166-0fe083697862'
title: Why Are We Concerned About Superintelligence?
summary_for_tutor: "Six profile cards of AI-lab leaders (Sam Altman, Dario Amodei, Demis Hassabis, Shane Legg, Ilya Sutskever, Jan Leike), each with a one-line teaser. The learner opens a card to read that person's definition of AGI or superintelligence, their public risk statements, a highlighted paragraph on why it matters for this module, and source links; opened cards are marked as read and a counter shows how many of the six have been read. The widget reports which profiles the learner has read; it is complete when all six have been opened. Content ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Why Are We Concerned About Superintelligence?</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "what-do-they-say". -->
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
  h1, h2 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 24px; line-height: 1.2; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .top { display: flex; flex-wrap: wrap; align-items: baseline; justify-content: space-between; gap: 8px 16px; margin-bottom: 14px; }
  .progress { font-size: 12px; color: var(--muted); }
  .grid { display: grid; gap: 12px; }
  @media (min-width: 640px) { .grid { grid-template-columns: 1fr 1fr; } }
  .card {
    font: inherit; color: inherit; text-align: left; cursor: pointer;
    display: flex; flex-direction: column; gap: 10px;
    border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 14px;
  }
  .card:hover { background: var(--surface); }
  .card:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .card.is-open { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .who { display: flex; align-items: center; gap: 10px; min-width: 0; }
  .avatar {
    flex: 0 0 auto; width: 44px; height: 44px; border-radius: 50%;
    border: 1px solid var(--border); background: var(--surface); color: var(--muted);
    display: inline-flex; align-items: center; justify-content: center; font-weight: 600; font-size: 14px;
  }
  .avatar.lg { width: 60px; height: 60px; font-size: 18px; }
  .name { font-weight: 600; display: block; }
  .role { font-size: 12px; color: var(--muted); display: block; }
  .teaser { color: var(--muted); font-size: 13px; margin: 0; }
  .cta { display: flex; justify-content: space-between; align-items: center; gap: 8px; font-size: 12px; font-weight: 500; color: var(--accent); }
  .read { display: none; color: var(--text); font-weight: 500; }
  .card.is-read .read { display: inline; }
  .detail { display: none; margin-top: 16px; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 16px; }
  .detail.is-open { display: block; }
  .detail-head { display: flex; align-items: center; gap: 14px; }
  .detail-head .who { flex: 1 1 auto; }
  .close { font: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; color: var(--muted); padding: 6px 10px; cursor: pointer; }
  .close:hover { background: var(--surface); color: var(--text); }
  .section { margin-top: 14px; }
  .section p { margin: 4px 0 0; max-width: 46rem; }
  .section.matters { border: 1px solid var(--accent); border-radius: 8px; background: #fff; padding: 12px 14px; }
  .section.matters .eyebrow { color: var(--accent-hover); }
  q { font-style: italic; }
  em { font-style: normal; font-weight: 500; }
  .sources { border-top: 1px solid var(--border); margin-top: 16px; padding-top: 10px; }
  .sources-list { display: flex; flex-wrap: wrap; gap: 4px 16px; margin-top: 4px; }
  .sources a { color: var(--accent-hover); font-size: 12px; text-decoration: underline; text-underline-offset: 2px; }
  .sources a:hover { text-decoration: none; }
  .done { margin-top: 12px; font-size: 12px; color: var(--muted); display: none; }
  .done.is-visible { display: block; }
</style>
</head>
<body>
<div class="top">
  <div>
    <p class="eyebrow">Six leaders, in their own words</p>
    <h1>Why Are We Concerned About Superintelligence?</h1>
  </div>
  <span class="progress" id="progress"></span>
</div>

<div class="grid" id="grid" role="list"></div>

<div class="detail" id="detail" role="region" aria-live="polite"></div>
<p class="done" id="done">All six profiles read.</p>

<script>
  var VIEW_PROFILE = "View profile →";
  var FIGURES = [
    {
      key: "altman", name: "Sam Altman", role: "CEO, OpenAI", initials: "SA",
      teaser: "Authored OpenAI's original economic definition of AGI; has since argued the term is no longer precise enough to be useful.",
      sections: [
        { label: "Definition", paragraphs: [
          "OpenAI's founding charter defines AGI as <q>highly autonomous systems that outperform humans at most economically valuable work</q>, the definition the rest of the industry spent a decade responding to. As systems improved, Altman's use of the term shifted. By mid-2025 he was calling AGI <q>not a super useful term</q>, and by late 2025 he suggested that AGI, by any earlier definition, <q>went whooshing by</q> without transforming the world. His proposed bar for superintelligence is a system that outperforms any human, including one assisted by AI, at roles such as head of state, chief executive, or director of a major research lab."
        ] },
        { label: "Risk statements", paragraphs: [
          "His risk assessments have not softened alongside the definitional shift. In 2023 he described the worst case as <q>lights out for all of us</q>, and OpenAI's superalignment announcement warned that superintelligence could lead to the <q>disempowerment of humanity or even human extinction</q>."
        ] },
        { label: "Relevance to this module", matters: true, paragraphs: [
          "A definition that moves as products approach it cannot anchor an agreement. This is one reason treaties are written around thresholds an outside party can measure, taken up in 1.0.1 Drawing the Line: Compute vs. Capability."
        ] }
      ],
      sources: [
        { label: "Time", href: "https://time.com/7205596/sam-altman-superintelligence-agi/" },
        { label: "CNBC", href: "https://www.cnbc.com/2025/08/11/sam-altman-says-agi-is-a-pointless-term-experts-agree.html" },
        { label: "Windows Central", href: "https://www.windowscentral.com/artificial-intelligence/openai-ceo-sam-altman-claims-agi-might-have-already-whooshed-by" },
        { label: "80,000 Hours", href: "https://80000hours.org/podcast/episodes/jan-leike-superalignment/" }
      ]
    },
    {
      key: "amodei", name: "Dario Amodei", role: "CEO, Anthropic", initials: "DA",
      teaser: "Uses the term \"powerful AI\" rather than AGI; estimates arrival as early as 2026 or 2027.",
      sections: [
        { label: "Definition", paragraphs: [
          "Amodei avoids the term AGI in favor of <em>powerful AI</em>: a system <q>smarter than a Nobel Prize winner across most relevant fields</q>, able to work autonomously for days or weeks, operating at 10 to 100 times human speed, in millions of instances at once. His shorthand for this is <q>a country of geniuses in a datacenter</q>. He has estimated arrival as early as 2026 or 2027."
        ] },
        { label: "Risk statements", paragraphs: [
          "His 2026 essay <em>The Adolescence of Technology</em> organizes the risks into five categories: rogue autonomy, misuse for destruction (biological weapons foremost), seizure of power, economic disruption, and, notably given his position, AI companies themselves. On state misuse he writes: <q>AI-enabled authoritarianism terrifies me</q>."
        ] },
        { label: "Relevance to this module", matters: true, paragraphs: [
          "The framing is explicitly geopolitical. In a companion policy essay he argues that a nation holding powerful AI, facing one without it, could resemble <q>World War II Marines facing an army of medieval swordsmen</q>. That comparison describes the arms-race incentive structure this module examines."
        ] }
      ],
      sources: [
        { label: "Machines of Loving Grace", href: "https://darioamodei.com/essay/machines-of-loving-grace" },
        { label: "The Adolescence of Technology", href: "https://darioamodei.com/essay/the-adolescence-of-technology" },
        { label: "Policy on the AI Exponential", href: "https://darioamodei.com/post/policy-on-the-ai-exponential" },
        { label: "Axios", href: "https://www.axios.com/2026/01/26/anthropic-ai-dario-amodei-humanity" },
        { label: "Mi3", href: "https://www.mi-3.com.au/27-01-2026/anthropic-founder-warns-ai-entering-dangerous-adolescence-urges-urgent-guardrails" }
      ]
    },
    {
      key: "hassabis", name: "Demis Hassabis", role: "CEO, Google DeepMind · Nobel laureate", initials: "DH",
      teaser: "Defines AGI as the full range of human cognitive capabilities; advocates IAEA-style international monitoring.",
      sections: [
        { label: "Definition", paragraphs: [
          "Hassabis applies the strictest bar among the major labs: <q>a system that can exhibit all the cognitive capabilities humans can</q>, including invention, creativity, continual learning, and long-horizon planning. Benchmark performance alone does not satisfy it; he notes that current models can win Olympiad-level competitions while failing simple tasks. On that standard he estimates five to ten years, centered near 2030."
        ] },
        { label: "Risk statements", paragraphs: [
          "<q>The risk of a catastrophic scenario is not zero, so we must dedicate significant resources to mitigating it</q>. He groups the dangers into two categories: misuse of a dual-use technology by bad actors, and systems whose goals diverge from human intent as capabilities increase. Asked whether he worries about ending up in Oppenheimer's position, he has said he thinks about such scenarios regularly."
        ] },
        { label: "Relevance to this module", matters: true, paragraphs: [
          "His policy proposals are institutional: a CERN-style body for shared safety research and an IAEA-style agency to monitor high-risk projects. The IAEA is the nuclear world's verification agency, so the proposal amounts to a request for the infrastructure this course studies."
        ] }
      ],
      sources: [
        { label: "Davos 2026 transcript", href: "https://aletteraday.substack.com/p/letters-314315-demis-hassabis-and" },
        { label: "Axios AI+ interview", href: "https://vocal.media/journal/demis-hassabis-warns-about-ai-the-risk-of-a-catastrophic-scenario-is-not-zero" }
      ]
    },
    {
      key: "legg", name: "Shane Legg", role: "Chief AGI Scientist, Google DeepMind", initials: "SL",
      teaser: "Coined the term AGI in 2001; has maintained a median forecast near 2028 since 2011.",
      sections: [
        { label: "The term", paragraphs: [
          "Legg proposed the phrase \"artificial general intelligence\" around 2001, at a time when the idea sat well outside mainstream research. His forecasts have been unusually stable since: a public median estimate near 2028, held since at least 2011. His 2008 doctoral thesis, <em>Machine Super Intelligence</em>, argued that a machine above human level could design still more capable machines, and that methods for managing that dynamic did not exist."
        ] },
        { label: "Risk statements", paragraphs: [
          "As DeepMind's Chief AGI Scientist he co-authored the company's 145-page AGI safety framework, which states that AGI could pose a <q>potential risk of severe harm</q> and identifies existential risk, harm that permanently destroys humanity, as the extreme case the framework is designed to prevent."
        ] },
        { label: "Relevance to this module", matters: true, paragraphs: [
          "Legg's two-decade position is that capability has outpaced control. Verification does not resolve that problem; it addresses a narrower one, giving outside parties visibility into who is approaching dangerous capability levels while the control problem remains open."
        ] }
      ],
      sources: [
        { label: "MIT Technology Review", href: "https://www.technologyreview.com/2025/10/30/1127057/agi-conspiracy-theory-artifcial-general-intelligence/" },
        { label: "Fortune", href: "https://fortune.com/2025/04/04/google-deeepmind-agi-ai-2030-risk-destroy-humanity/" }
      ]
    },
    {
      key: "sutskever", name: "Ilya Sutskever", role: "Co-founder, OpenAI · Founder, SSI", initials: "IS",
      teaser: "Central to the current technical paradigm; now leads a lab founded solely to build superintelligence safely.",
      sections: [
        { label: "Definition", paragraphs: [
          "Sutskever's objection to the standard definition is that it overshoots: <q>a human being is not an AGI</q>. Humans do not arrive knowing every task; they learn. His model of superintelligence follows from that. Not a complete, all-knowing system, but one that can learn any job quickly, which he has described as <q>a superintelligent 15-year-old</q> whose competence develops through deployment."
        ] },
        { label: "Risk statements", paragraphs: [
          "Before leaving OpenAI he described the coming transition as <q>monumental, earth-shattering</q>, with a before and an after. In 2024 he founded Safe Superintelligence Inc., a lab organized around a single goal: building superintelligence with safety as the binding constraint."
        ] },
        { label: "Relevance to this module", matters: true, paragraphs: [
          "If capabilities emerge during deployment rather than before release, there is no clean pre-release point at which a system can be inspected. This measurement problem is part of why current policy relies on compute thresholds, which can be assessed in advance, rather than capability evaluations (see 1.0.1 Drawing the Line: Compute vs. Capability)."
        ] }
      ],
      sources: [
        { label: "Dwarkesh Podcast", href: "https://www.dwarkesh.com/p/ilya-sutskever-2" },
        { label: "The Decoder", href: "https://the-decoder.com/ilya-sutskever-says-a-new-learning-paradigm-is-necessary-and-is-already-chasing-it/" },
        { label: "MIT Technology Review", href: "https://www.technologyreview.com/2025/10/30/1127057/agi-conspiracy-theory-artifcial-general-intelligence/" }
      ]
    },
    {
      key: "leike", name: "Jan Leike", role: "Former co-lead, Superalignment, OpenAI · now Anthropic", initials: "JL",
      teaser: "Co-led OpenAI's superalignment effort; resigned in 2024 over resourcing and priorities.",
      sections: [
        { label: "Background", paragraphs: [
          "Leike co-led OpenAI's superalignment team with Sutskever. Its mandate was to solve the control problem for smarter-than-human systems within four years, supported by a public commitment of 20 percent of the company's compute. He resigned less than a year later, writing that the team had struggled to obtain the promised resources, that building smarter-than-human machines is <q>an inherently dangerous endeavor</q>, and that safety work had taken <q>a backseat to shiny products</q>. The team was dissolved shortly after his departure. He continued the same research agenda at Anthropic."
        ] },
        { label: "Risk statements", paragraphs: [
          "His central technical claim is that no one yet knows how to <q>steer and control AI systems much smarter than us</q>, and that development is proceeding ahead of that knowledge."
        ] },
        { label: "Relevance to this module", matters: true, paragraphs: [
          "This episode is a documented case study for voluntary self-governance. A leading lab made a written, quantified commitment to itself, and competitive pressure eroded it within a year. Commitments between competitors require what internal commitments lack: independent means of checking compliance."
        ] }
      ],
      sources: [
        { label: "The National", href: "https://www.thenationalnews.com/future/technology/2024/05/18/former-openai-executive-says-safety-has-taken-a-backseat-as-company-disbands-ai-risks-unit/" },
        { label: "Fast Company", href: "https://www.fastcompany.com/91127491/former-openai-leader-jan-leike-blasts-company-for-ignoring-safety-culture" },
        { label: "VentureBeat", href: "https://venturebeat.com/ai/openais-former-superalignment-leader-blasts-company-safety-culture-and-processes-have-taken-a-backseat" }
      ]
    }
  ];

  var STORAGE_KEY = "lens-widget-what-do-they-say";
  var state = { read: [], open: null };
  var completed = false;
  var grid = document.getElementById("grid");
  var detail = document.getElementById("detail");
  var progress = document.getElementById("progress");
  var doneEl = document.getElementById("done");
  var cards = {};

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function figureByKey(key) { for (var i = 0; i < FIGURES.length; i++) if (FIGURES[i].key === key) return FIGURES[i]; return null; }
  function isRead(key) { return state.read.indexOf(key) !== -1; }

  // The profile paragraphs carry only <q> and <em> markup. Build them as
  // elements instead of routing the text through innerHTML.
  function richParagraph(text) {
    var p = el("p");
    var re = /<(\/?)(q|em)>/g;
    var stack = [p];
    var last = 0, m;
    while ((m = re.exec(text)) !== null) {
      if (m.index > last) stack[stack.length - 1].appendChild(document.createTextNode(text.slice(last, m.index)));
      if (m[1] === "/") { if (stack.length > 1) stack.pop(); }
      else { var node = el(m[2]); stack[stack.length - 1].appendChild(node); stack.push(node); }
      last = re.lastIndex;
    }
    if (last < text.length) stack[stack.length - 1].appendChild(document.createTextNode(text.slice(last)));
    return p;
  }
  function avatar(f, large) {
    var a = el("span", "avatar" + (large ? " lg" : ""), f.initials);
    a.setAttribute("aria-hidden", "true");
    return a;
  }
  function who(f) {
    var w = el("span", "who");
    var t = el("span");
    t.appendChild(el("span", "name", f.name));
    t.appendChild(el("span", "role", f.role));
    w.appendChild(t);
    return w;
  }

  FIGURES.forEach(function (f) {
    var b = el("button", "card"); b.type = "button";
    b.setAttribute("role", "listitem");
    b.setAttribute("aria-label", "View profile: " + f.name + ", " + f.role);
    var w = who(f); w.insertBefore(avatar(f, false), w.firstChild);
    b.appendChild(w);
    b.appendChild(el("p", "teaser", f.teaser));
    var cta = el("span", "cta");
    cta.appendChild(el("span", null, VIEW_PROFILE));
    cta.appendChild(el("span", "read", "✓ Read"));
    b.appendChild(cta);
    b.addEventListener("click", function () { openProfile(f.key); });
    cards[f.key] = b;
    grid.appendChild(b);
  });

  function summary() {
    var readNames = [], unreadNames = [];
    FIGURES.forEach(function (f) { (isRead(f.key) ? readNames : unreadNames).push(f.name); });
    var s = "Leader profiles on AGI/superintelligence definitions and risk. Read so far (" + readNames.length + " of " + FIGURES.length + "): " + (readNames.length ? readNames.join(", ") : "none") + ".";
    if (unreadNames.length) s += " Not yet read: " + unreadNames.join(", ") + ".";
    var open = state.open ? figureByKey(state.open) : null;
    s += open ? " Currently open: " + open.name + " (" + open.role + ")." : " No profile open.";
    return s;
  }

  function persist() {
    if (window.Lens) {
      Lens.saveState({ read: state.read, open: state.open }, summary());
      if (!completed && state.read.length === FIGURES.length) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }

  function renderDetail() {
    detail.textContent = "";
    var f = state.open ? figureByKey(state.open) : null;
    detail.classList.toggle("is-open", !!f);
    if (!f) return;
    var head = el("div", "detail-head");
    head.appendChild(avatar(f, true));
    head.appendChild(who(f));
    var close = el("button", "close", "Close"); close.type = "button";
    close.setAttribute("aria-label", "Close profile");
    close.addEventListener("click", function () { state.open = null; render(); persist(); });
    head.appendChild(close);
    detail.appendChild(head);
    f.sections.forEach(function (s) {
      var sec = el("div", "section" + (s.matters ? " matters" : ""));
      sec.appendChild(el("p", "eyebrow", s.label));
      s.paragraphs.forEach(function (t) { sec.appendChild(richParagraph(t)); });
      detail.appendChild(sec);
    });
    var src = el("div", "sources");
    src.appendChild(el("p", "eyebrow", "Sources"));
    var list = el("div", "sources-list");
    f.sources.forEach(function (s) {
      var a = el("a", null, s.label);
      a.href = s.href; a.target = "_blank"; a.rel = "noopener";
      list.appendChild(a);
    });
    src.appendChild(list);
    detail.appendChild(src);
  }

  function render() {
    FIGURES.forEach(function (f) {
      var b = cards[f.key];
      b.classList.toggle("is-open", state.open === f.key);
      b.classList.toggle("is-read", isRead(f.key));
      b.setAttribute("aria-expanded", state.open === f.key ? "true" : "false");
    });
    progress.textContent = state.read.length + " of " + FIGURES.length + " profiles read";
    doneEl.classList.toggle("is-visible", state.read.length === FIGURES.length);
    renderDetail();
  }

  function openProfile(key) {
    if (!isRead(key)) state.read.push(key);
    state.open = key;
    render();
    persist();
    detail.scrollIntoView({ behavior: "smooth", block: "nearest" });
  }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (Array.isArray(saved.read)) state.read = saved.read.filter(function (k) { return !!figureByKey(k); });
      if (typeof saved.open === "string" && figureByKey(saved.open)) state.open = saved.open;
    }
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = localStorage.getItem(STORAGE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
</script>
</body>
</html>
