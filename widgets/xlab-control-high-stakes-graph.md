---
id: 'a0e30f44-c25e-4d26-95a6-a841800fb993'
title: The control graph
summary_for_tutor: "A five-step build-up of the control graph. The axes are how incriminating each of the model's actions is (vertical) against how many actions the model needs to cause a catastrophe (horizontal). Step 1 shows the bare axes. Step 2 lights the high-stakes band on the left (few actions needed). Step 3 lights the low-stakes band on the right (many actions needed, no single action decides the outcome). Step 4 lights the two off-band corners: top right, many actions each highly incriminating, trivially solved with random auditing; bottom left, a catastrophe in a few barely-incriminating actions, probably hopeless. Step 5 draws the diagonal and argues incrimination and action count are inversely correlated. The learner steps through with Back and Next or by clicking a step dot; nothing is graded and there is no right answer, so if a learner asks about it, ask them where a given deployment scenario would sit on the two axes."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 0; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.card { border: 1px solid var(--border); border-radius: 8px; overflow: hidden; background: var(--bg); }
.head { display: flex; align-items: flex-start; justify-content: space-between; gap: 12px;
  flex-wrap: wrap; padding: 12px 16px; border-bottom: 1px solid var(--border); background: var(--page); }
.head h2 { font-family: var(--font-heading); font-weight: 600; font-size: 16px; margin: 0; }
.head p { margin: 4px 0 0; color: var(--muted); font-size: 12px; max-width: 46em; }
.body { padding: 16px; }
svg.graph { width: 100%; height: auto; display: block; }
.caption { min-height: 84px; margin-top: 12px; }
.caption .step-label { margin: 0; font-weight: 600; font-variant-numeric: tabular-nums; }
.caption .step-text { margin: 4px 0 0; color: var(--muted); }
.controls { display: flex; align-items: center; justify-content: space-between; gap: 12px;
  flex-wrap: wrap; margin-top: 12px; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px;
  background: #fff; padding: 6px 12px; cursor: pointer; }
button:hover:not(:disabled) { background: var(--page); border-color: var(--muted); }
button:disabled { opacity: 0.45; cursor: default; }
button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
.dots { display: flex; gap: 8px; }
.dots button { width: 22px; height: 22px; padding: 0; border-radius: 50%; border: 1px solid var(--border);
  background: #fff; position: relative; }
.dots button::after { content: ""; position: absolute; inset: 5px; border-radius: 50%; background: var(--border); }
.dots button[aria-current="step"] { border-color: var(--accent); }
.dots button[aria-current="step"]::after { background: var(--accent); }
.dots button.seen::after { background: var(--muted); }
.reset { font-size: 12px; padding: 4px 10px; color: var(--muted); }
@media (max-width: 420px) {
  .controls { justify-content: center; }
  .caption { min-height: 120px; }
}
</style>
</head>
<body>
<!-- Ported from XLab's AI Control curriculum, lesson "What is High Stakes?" (Module 4). -->
<div class="card">
  <div class="head">
    <div>
      <h2>The control graph</h2>
      <p>Build the high-stakes control graph region by region: high-stakes, low-stakes, the trivially-solved and probably-hopeless corners, then see why incrimination and the number of actions are inversely correlated.</p>
    </div>
    <button type="button" class="reset" id="reset">Reset</button>
  </div>
  <div class="body">
    <svg viewBox="0 0 560 400" class="graph" role="img" aria-label="The control graph: how incriminating each action is against how many actions are needed to cause a catastrophe, built up region by region (high-stakes, low-stakes, trivially solved, probably hopeless), then the inverse correlation between the axes">
      <defs>
        <marker id="axis-arrow" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
          <path d="M0,0 L8,4 L0,8 z" fill="#5a5a5a"></path>
        </marker>
        <marker id="diag-arrow" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
          <path d="M0,0 L8,4 L0,8 z" fill="#b87018"></path>
        </marker>
      </defs>
      <g id="r-high" opacity="0.15" style="transition: opacity 0.4s">
        <polygon points="84,22 196,22 420,122 196,222 84,172" fill="#e9c893" stroke="#ffffff" stroke-width="2"></polygon>
      </g>
      <g id="r-low" opacity="0.35" style="transition: opacity 0.4s">
        <polygon points="420,122 532,172 532,322 420,322 196,222" fill="#ddd8cf" stroke="#ffffff" stroke-width="2"></polygon>
      </g>
      <g id="r-corners" opacity="0.35" style="transition: opacity 0.4s">
        <polygon points="196,22 532,22 532,172" fill="#eeebe5" stroke="#ffffff" stroke-width="2"></polygon>
        <polygon points="84,172 84,322 420,322" fill="#eeebe5" stroke="#ffffff" stroke-width="2"></polygon>
      </g>
      <text id="l-high" x="225.87" y="115.33" opacity="0" style="transition: opacity 0.4s" fill="#1a1a1a" font-size="15" font-weight="700">High-stakes</text>
      <text id="l-low" x="405.07" y="248.67" opacity="0" style="transition: opacity 0.4s" fill="#5a5a5a" font-size="13" font-weight="600">Low-stakes</text>
      <g id="l-corners" opacity="0" style="transition: opacity 0.4s">
        <text x="461.07" y="66.44" text-anchor="middle" fill="#5a5a5a" font-size="10">
          <tspan x="461.07" dy="0">Trivially solved</tspan><tspan x="461.07" dy="13">with random auditing</tspan>
        </text>
        <text x="158.67" y="287.56" text-anchor="middle" fill="#5a5a5a" font-size="10">
          <tspan x="158.67" dy="0">Probably</tspan><tspan x="158.67" dy="13">hopeless?</tspan>
        </text>
      </g>
      <g id="l-diag" opacity="0" style="transition: opacity 0.4s">
        <line x1="457.33" y1="244.22" x2="151.2" y2="91.44" stroke="#b87018" stroke-width="2" stroke-dasharray="6 5" marker-end="url(#diag-arrow)"></line>
        <text x="330.4" y="138.67" text-anchor="middle" fill="#9a5c10" font-size="10" font-weight="600">
          <tspan x="330.4" dy="0">fewer actions &#8594;</tspan><tspan x="330.4" dy="13">bigger, more incriminating actions</tspan>
        </text>
      </g>
      <line x1="72" y1="322" x2="72" y2="18" stroke="#5a5a5a" stroke-width="1.75" marker-end="url(#axis-arrow)"></line>
      <line x1="72" y1="334" x2="542" y2="334" stroke="#5a5a5a" stroke-width="1.75" marker-end="url(#axis-arrow)"></line>
      <text x="62" y="172" transform="rotate(-90 62 172)" text-anchor="middle" fill="#1a1a1a" font-size="12" font-weight="500">How incriminating is each action?</text>
      <text x="308" y="356" text-anchor="middle" fill="#1a1a1a" font-size="12" font-weight="500">Number of actions to cause catastrophe</text>
    </svg>

    <div class="caption" aria-live="polite">
      <p class="step-label" id="step-label"></p>
      <p class="step-text" id="step-text"></p>
    </div>

    <div class="controls">
      <button type="button" id="back">Back</button>
      <div class="dots" id="dots" role="group" aria-label="Steps"></div>
      <button type="button" id="next">Next</button>
    </div>
  </div>
</div>

<script>
(function () {
  var STEPS = [
    {
      label: "The axes",
      text: "The control graph places a deployment scenario on two axes: how incriminating each of the model's actions is, and how many actions the model needs to cause a catastrophe."
    },
    {
      label: "High-stakes",
      text: "“High stakes” is what takes the least amount of actions to produce a catastrophically threatening occurrence: the left half of the band, where only a few actions are needed."
    },
    {
      label: "Low-stakes",
      text: "The right half of the band is the low-stakes region: lots of actions are needed to cause a catastrophe, so no single action decides the outcome."
    },
    {
      label: "The corners",
      text: "The corners fall off the interesting band. Top right: many actions needed and each one highly incriminating, so it is trivially solved with random auditing. Bottom left: a catastrophe in a few barely-incriminating actions. Probably hopeless?"
    },
    {
      label: "Why the diagonal?",
      text: "Incrimination and number of actions are inversely correlated: as the number of actions decreases while the catastrophe stays the same, each action's size and impact must grow, breaking more safeguards and costing more reasoning, so each action becomes more incriminable."
    }
  ];

  var step = 0;
  var maxStep = 0;

  var el = {
    high: document.getElementById("r-high"),
    low: document.getElementById("r-low"),
    corners: document.getElementById("r-corners"),
    labelHigh: document.getElementById("l-high"),
    labelLow: document.getElementById("l-low"),
    labelCorners: document.getElementById("l-corners"),
    diag: document.getElementById("l-diag"),
    stepLabel: document.getElementById("step-label"),
    stepText: document.getElementById("step-text"),
    back: document.getElementById("back"),
    next: document.getElementById("next"),
    dots: document.getElementById("dots"),
    reset: document.getElementById("reset")
  };

  var dotButtons = [];
  STEPS.forEach(function (s, i) {
    var b = document.createElement("button");
    b.type = "button";
    b.setAttribute("aria-label", "Step " + (i + 1) + ": " + s.label);
    b.addEventListener("click", function () { go(i); });
    el.dots.appendChild(b);
    dotButtons.push(b);
  });

  function render() {
    el.high.setAttribute("opacity", step >= 1 ? "0.95" : "0.15");
    el.low.setAttribute("opacity", step >= 2 ? "1" : "0.35");
    el.corners.setAttribute("opacity", step >= 3 ? "1" : "0.35");
    el.labelHigh.setAttribute("opacity", step >= 1 ? "1" : "0");
    el.labelLow.setAttribute("opacity", step >= 2 ? "1" : "0");
    el.labelCorners.setAttribute("opacity", step >= 3 ? "1" : "0");
    el.diag.setAttribute("opacity", step === 4 ? "1" : "0");

    el.stepLabel.textContent = (step + 1) + ". " + STEPS[step].label;
    el.stepText.textContent = STEPS[step].text;

    el.back.disabled = step === 0;
    el.next.disabled = step === STEPS.length - 1;

    dotButtons.forEach(function (b, i) {
      if (i === step) { b.setAttribute("aria-current", "step"); }
      else { b.removeAttribute("aria-current"); }
      if (i <= maxStep && i !== step) { b.classList.add("seen"); }
      else { b.classList.remove("seen"); }
    });
  }

  function save() {
    if (!window.Lens) { return; }
    var summary = "Control graph: currently on step " + (step + 1) + " of " + STEPS.length +
      " (" + STEPS[step].label + "). Furthest step reached: " + (maxStep + 1) + " of " + STEPS.length +
      " (" + STEPS[maxStep].label + ").";
    Lens.saveState({ step: step, maxStep: maxStep }, summary);
    if (maxStep === STEPS.length - 1) { Lens.complete(); }
  }

  function go(i) {
    step = Math.max(0, Math.min(STEPS.length - 1, i));
    if (step > maxStep) { maxStep = step; }
    render();
    save();
  }

  el.back.addEventListener("click", function () { go(step - 1); });
  el.next.addEventListener("click", function () { go(step + 1); });
  el.reset.addEventListener("click", function () { go(0); });

  if (window.Lens && Lens.onState) {
    Lens.onState(function (state) {
      if (state && typeof state.step === "number") {
        maxStep = typeof state.maxStep === "number" ? state.maxStep : state.step;
        step = state.step;
      }
      render();
    });
  }

  render();
})();
</script>
</body>
</html>
