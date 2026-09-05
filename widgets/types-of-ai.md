---
title: The types of AI
summary_for_tutor: A concentric diagram of AI categories, outermost to innermost - AI, Narrow AI, Machine Learning, Deep Learning, Generative AI, Large Language Models, Transformer LLMs - with example systems placed in each ring (Roomba, Deep Blue, Amazon spam filter, FaceID, Midjourney, Mamba, Claude, ChatGPT...). The learner taps a ring or an example to read what it is and why it sits at that ring and not the next one in. The grey margin outside the red rings is non-narrow AI, which is theoretical only. Content ported from XLab's Verification track.
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The types of AI</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "types-of-ai". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --border: #e8e5df;
    --muted: #faf8f3;
    --muted-fg: #5a5a5a;
    --fg: #1a1a1a;
    --card: #ffffff;
    --primary: #b87018;
    --font-ui: "DM Sans", Arial, sans-serif;
    --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    font-family: var(--font-ui);
    font-size: 14px;
    line-height: 1.5;
    color: var(--fg);
    background: var(--card);
  }
  .layout { display: grid; gap: 16px; align-items: start; }
  @media (min-width: 860px) { .layout { grid-template-columns: minmax(0, 1fr) 16rem; } }
  .diagram { border: 1px solid var(--border); border-radius: 12px; overflow: hidden; background: var(--card); }
  svg { display: block; width: 100%; height: auto; user-select: none; -webkit-user-select: none; }
  .ring { cursor: pointer; }
  .label { cursor: pointer; font-weight: 600; paint-order: stroke; stroke-linejoin: round; }
  .pill { cursor: pointer; paint-order: stroke; stroke-linejoin: round; }
  .pill.is-active { font-weight: 600; text-decoration: underline; }
  .panel {
    border: 1px solid var(--border);
    background: var(--card);
    border-radius: 12px;
    padding: 16px;
    box-shadow: none;
  }
  @media (min-width: 860px) { .panel { position: sticky; top: 8px; } }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted-fg); margin: 0; }
  .panel h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 4px 0 0; }
  .panel p { margin: 8px 0 0; }
  .hint { color: var(--muted-fg); font-style: italic; margin: 0; }
  .small { color: var(--muted-fg); font-size: 12px; }
  .why { border-top: 1px solid var(--border); margin-top: 12px; padding-top: 8px; }
  .why .eyebrow { display: inline; margin-right: 6px; }
  .region-list { display: flex; flex-direction: column; gap: 8px; margin-top: 12px; }
  .region-btn, .close-btn {
    font: inherit; color: inherit; text-align: left; cursor: pointer;
    border: 1px solid var(--border); background: transparent; border-radius: 8px;
  }
  .region-btn { padding: 8px 12px; }
  .region-btn:hover, .close-btn:hover { background: var(--muted); }
  .region-btn strong { display: block; font-weight: 500; }
  .region-btn span { display: block; color: var(--muted-fg); font-size: 12px; }
  .close-btn { float: right; border: 0; width: 28px; height: 28px; margin: -4px -4px 0 0; color: var(--muted-fg); font-size: 18px; line-height: 1; }
</style>
</head>
<body>
<div class="layout">
  <div class="diagram">
    <svg id="svg" viewBox="0 0 1180 1240" role="img" aria-label="Concentric rings of AI categories with example systems"></svg>
  </div>
  <aside class="panel" id="panel" aria-live="polite"></aside>
</div>

<script>
  var AI_LEVELS = [
    { key: "ai", name: "AI", blurb: "The whole field: any system built to do things we would call intelligent.", examples: [] },
    { key: "narrow", name: "Narrow AI", blurb: "Built for one task or a narrow set of them. Everything that actually exists today lives here.", examples: [
      { name: "Roomba", what: "iRobot's robot vacuum.", why: "Navigates with sensors and fixed rules. It does not learn from data, so it is narrow AI but not machine learning." },
      { name: "Boeing autopilot", what: "Flight-control automation.", why: "Follows engineered control laws for one job; nothing about it is learned from data." },
      { name: "IBM Deep Blue", what: "The chess computer that beat Kasparov in 1997.", why: "Brute-force search plus a hand-crafted evaluation function: formidable, but narrow and not machine learning." },
      { name: "Word spell checker", what: "Dictionary-and-rules spelling correction.", why: "Looks words up against a list and applies rules; narrow and rule-based." }
    ] },
    { key: "ml", name: "Machine Learning", blurb: "Systems that learn patterns from data instead of being programmed rule by rule.", examples: [
      { name: "Amazon spam filter", what: "Amazon's early email spam classification.", why: "Learns spam-vs-not from labelled examples: machine learning, but not a deep neural network." },
      { name: "Chase credit", what: "Chase's automated credit-scoring decisions.", why: "Statistical models fit to historical data; machine learning without deep learning." },
      { name: "JPMorgan fraud", what: "JP Morgan's transaction-fraud flagging.", why: "Learns fraud patterns from past transactions; classical machine learning." }
    ] },
    { key: "dl", name: "Deep Learning", blurb: "Machine learning with many-layered neural networks that learn their own features.", examples: [
      { name: "Apple Photos", what: "On-device photo recognition (image classifiers).", why: "Convolutional neural networks: deep learning, but it labels images rather than generating them." },
      { name: "Azure Speech to Text", what: "Microsoft's speech-recognition service.", why: "Deep neural nets map audio to text; recognition, not generation." },
      { name: "FaceID", what: "Apple's face unlock.", why: "A deep neural net recognises your face: discriminative, not generative." }
    ] },
    { key: "gen", name: "Generative AI", blurb: "Deep-learning systems that create new content: images, audio, video, text.", examples: [
      { name: "Midjourney", what: "Text-to-image generator.", why: "Generates images (diffusion): generative, but not a language model." },
      { name: "Sora", what: "OpenAI's text-to-video model.", why: "Generates video; generative, but not language." },
      { name: "Suno", what: "AI music generator.", why: "Generates audio; generative, non-language." },
      { name: "Adobe Firefly", what: "Adobe's image-generation model.", why: "Generative imagery; not a language model." }
    ] },
    { key: "llm", name: "Large Language Model", blurb: "Generative models that specialise in language.", examples: [
      { name: "Mamba", what: "A state-space-model language model.", why: "A large language model that is NOT a transformer: it uses a state-space architecture instead of attention." },
      { name: "RWKV", what: "An RNN-style language model.", why: "A language model built on a recurrent architecture rather than transformers." }
    ] },
    { key: "transformer", name: "Transformer LLMs", blurb: "Language models built on the transformer (attention) architecture: today's mainstream.", examples: [
      { name: "Claude", what: "Anthropic's assistant.", why: "A transformer-based large language model." },
      { name: "ChatGPT", what: "OpenAI's assistant.", why: "Built on GPT transformers." },
      { name: "Gemini", what: "Google DeepMind's assistant.", why: "Transformer-based." },
      { name: "LLaMA", what: "Meta's open-weight model family.", why: "Transformer architecture." }
    ] }
  ];
  var AI_REGIONS = {
    theoretical: { label: "Theoretical only", body: "Right now is theoretical-only. There are no real non-narrow AI models known right now." },
    absurd: { label: "Possible but absurd", body: "Theoretically possible but would require an absurd quantity of resources. Less likely to occur." }
  };
  var PROMPT = "Tap any system to see what it is and why it sits at this ring, not the next one in.";

  // Geometry (same viewBox and ring placement as the original diagram).
  var VBW = 1180, VBH = 1240;
  var AI = { cx: 590, cy: 600, r: 585 };
  var RED_BOTTOM = 1160, RED_R0 = 505, RED_STEP = 73;
  var NAME_FS = 34, EX_FS = 21, PILL_H = 30, EX_GAP = 14, CHAR_W = 0.56, PAD = 14;

  function levelCircle(i) {
    if (i === 0) return AI;
    var r = RED_R0 - (i - 1) * RED_STEP;
    return { cx: AI.cx, cy: RED_BOTTOM - r, r: r };
  }
  function redOpacity(i) { return 0.12 + (i - 1) * 0.15; }
  function topEdge(i) { var c = levelCircle(i); return c.cy - c.r; }
  function bandWidth(c, y, pad) {
    var rr = c.r - pad, v = rr * rr - (y - c.cy) * (y - c.cy);
    return v > 0 ? 2 * Math.sqrt(v) : 0;
  }
  function estPill(name) { return name.length * EX_FS * CHAR_W + 8; }

  // Pack example pills into rows that fit the chord width at each row's y.
  function packRows(c, examples, startY) {
    var rows = [], row = [], w = 0, y = startY;
    examples.forEach(function (ex) {
      var iw = estPill(ex.name);
      var maxW = bandWidth(c, y + PILL_H / 2, PAD);
      if (row.length && w + EX_GAP + iw > maxW) {
        rows.push(row); row = []; w = 0; y += PILL_H;
      }
      row.push({ ex: ex, w: iw });
      w += (row.length > 1 ? EX_GAP : 0) + iw;
    });
    if (row.length) rows.push(row);
    return rows;
  }

  var svg = document.getElementById("svg");
  var SVG_NS = "http://www.w3.org/2000/svg";
  function make(tag, attrs, parent) {
    var node = document.createElementNS(SVG_NS, tag);
    for (var k in attrs) node.setAttribute(k, attrs[k]);
    (parent || svg).appendChild(node);
    return node;
  }

  var view = { kind: "none" };
  var rings = [], labels = [], pills = [];

  function buildDiagram() {
    var defs = make("defs", {});
    var pattern = make("pattern", { id: "hatch", width: 13, height: 13, patternUnits: "userSpaceOnUse", patternTransform: "rotate(45)" }, defs);
    make("line", { x1: 0, y1: 0, x2: 0, y2: 13, stroke: "rgba(90,90,90,0.2)", "stroke-width": 1.4 }, pattern);

    var bg = make("rect", { x: 0, y: 0, width: VBW, height: VBH, fill: "transparent" });
    bg.addEventListener("click", function () { setView({ kind: "none" }); });

    make("circle", { cx: AI.cx, cy: AI.cy, r: AI.r, fill: "#f3f1ec" });
    make("circle", { cx: AI.cx, cy: AI.cy, r: AI.r, fill: "url(#hatch)" });

    AI_LEVELS.forEach(function (lvl, i) {
      var c = levelCircle(i);
      var ring = make("circle", { cx: c.cx, cy: c.cy, r: c.r, "class": "ring", "vector-effect": "non-scaling-stroke" });
      if (i === 0) {
        ring.setAttribute("fill", "transparent");
      } else {
        ring.setAttribute("fill", "#b87018");
        ring.setAttribute("fill-opacity", redOpacity(i));
      }
      ring.addEventListener("click", function (e) { e.stopPropagation(); setView({ kind: "level", i: i }); });
      rings.push(ring);
    });

    AI_LEVELS.forEach(function (lvl, i) {
      var c = levelCircle(i);
      var light = i > 0 && redOpacity(i) >= 0.6;
      var isDisk = i === AI_LEVELS.length - 1;
      var nameY, exTop;
      if (i === 0) {
        nameY = topEdge(0) + 26 + NAME_FS / 2;
      } else if (isDisk) {
        var rowsGuess = packRows(c, lvl.examples, c.cy).length;
        var blockH = NAME_FS * 1.1 + 10 + rowsGuess * PILL_H;
        nameY = c.cy - blockH / 2 + NAME_FS / 2;
        exTop = nameY + NAME_FS / 2 + 10;
      } else {
        nameY = topEdge(i) + 14 + NAME_FS / 2;
        exTop = nameY + NAME_FS / 2 + 10;
      }
      var label = make("text", {
        x: c.cx, y: nameY, "text-anchor": "middle", "dominant-baseline": "middle",
        "font-size": NAME_FS, "class": "label",
        fill: light ? "#fff" : "#1a1a1a", stroke: light ? "rgba(60,35,5,0.35)" : "#fff", "stroke-width": 5
      });
      label.textContent = lvl.name;
      label.addEventListener("click", function (e) { e.stopPropagation(); setView({ kind: "level", i: i }); });
      labels.push(label);

      if (!lvl.examples.length) return;
      var rows = packRows(c, lvl.examples, exTop);
      rows.forEach(function (row, ri) {
        var total = row.reduce(function (s, it) { return s + it.w; }, 0) + (row.length - 1) * EX_GAP;
        var x = c.cx - total / 2;
        var y = exTop + ri * PILL_H + PILL_H / 2;
        row.forEach(function (it) {
          var ei = lvl.examples.indexOf(it.ex);
          var g = make("g", { "class": "pill-group" });
          make("rect", { x: x, y: y - PILL_H / 2, width: it.w, height: PILL_H, fill: "transparent" }, g);
          var t = make("text", {
            x: x + it.w / 2, y: y, "text-anchor": "middle", "dominant-baseline": "middle",
            "font-size": EX_FS, "class": "pill",
            fill: light ? "#fff" : "#1a1a1a", stroke: light ? "rgba(60,35,5,0.4)" : "#fff", "stroke-width": 4
          }, g);
          t.textContent = it.ex.name;
          g.style.cursor = "pointer";
          g.addEventListener("click", function (e) { e.stopPropagation(); setView({ kind: "example", i: i, ei: ei }); });
          pills.push({ node: t, i: i, ei: ei });
          x += it.w + EX_GAP;
        });
      });
    });
  }

  function paint() {
    var selLevel = view.kind === "level" || view.kind === "example" ? view.i : null;
    rings.forEach(function (ring, i) {
      var selected = selLevel === i;
      if (i === 0) {
        ring.setAttribute("stroke", selected ? "#1a1a1a" : "rgba(90,90,90,0.4)");
        ring.setAttribute("stroke-width", selected ? 3 : 1.5);
      } else {
        ring.setAttribute("stroke", selected ? "#1a1a1a" : "#fff");
        ring.setAttribute("stroke-opacity", selected ? 1 : 0.4);
        ring.setAttribute("stroke-width", selected ? 3 : 1.25);
      }
    });
    pills.forEach(function (p) {
      var active = view.kind === "example" && view.i === p.i && view.ei === p.ei;
      p.node.classList.toggle("is-active", active);
    });
  }

  var panel = document.getElementById("panel");
  function el(tag, className, text) {
    var node = document.createElement(tag);
    if (className) node.className = className;
    if (text !== undefined) node.textContent = text;
    return node;
  }
  function closeButton(label, next) {
    var b = el("button", "close-btn", "×");
    b.type = "button";
    b.setAttribute("aria-label", label);
    b.addEventListener("click", function () { setView(next); });
    return b;
  }

  function renderPanel() {
    panel.textContent = "";
    if (view.kind === "none") {
      panel.appendChild(el("p", "hint", PROMPT));
      var list = el("div", "region-list");
      ["theoretical", "absurd"].forEach(function (r) {
        var b = el("button", "region-btn");
        b.type = "button";
        b.appendChild(el("strong", null, AI_REGIONS[r].label));
        b.appendChild(el("span", null, "AI that is not narrow, out in the grey margin. Tap to read."));
        b.addEventListener("click", function () { setView({ kind: "region", r: r }); });
        list.appendChild(b);
      });
      panel.appendChild(list);
      return;
    }
    if (view.kind === "region") {
      panel.appendChild(closeButton("Close", { kind: "none" }));
      panel.appendChild(el("p", "eyebrow", "Beyond real AI"));
      panel.appendChild(el("h2", null, AI_REGIONS[view.r].label));
      panel.appendChild(el("p", null, AI_REGIONS[view.r].body));
      return;
    }
    var lvl = AI_LEVELS[view.i];
    if (view.kind === "level") {
      panel.appendChild(closeButton("Close", { kind: "none" }));
      panel.appendChild(el("p", "eyebrow", "Level"));
      panel.appendChild(el("h2", null, lvl.name));
      panel.appendChild(el("p", null, lvl.blurb));
      if (lvl.examples.length) panel.appendChild(el("p", "small", "Tap a system in this ring to see why it sits here, not one ring deeper."));
      return;
    }
    var ex = lvl.examples[view.ei];
    panel.appendChild(closeButton("Back to level", { kind: "level", i: view.i }));
    panel.appendChild(el("p", "eyebrow", lvl.name));
    panel.appendChild(el("h2", null, ex.name));
    panel.appendChild(el("p", null, ex.what));
    var why = el("p", "why");
    why.appendChild(el("span", "eyebrow", "Why here"));
    why.appendChild(document.createTextNode(ex.why));
    panel.appendChild(why);
  }

  function setView(next) {
    view = next;
    paint();
    renderPanel();
  }

  buildDiagram();
  setView({ kind: "none" });
</script>
</body>
</html>
