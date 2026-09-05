---
title: The verification problem
summary_for_tutor: "An introduction to the verification problem. Two adversarial states have signed an agreement limiting a dangerous technology. The learner tests four answers to the question of how each side can know the other complies: trust (collapses), punish violations (arrives too late), mutual transparency (backfires), and neutral privacy-preserving verification (holds). Each card opens a short explanation of why that option fails or holds. Content ported from XLab's Verification track."
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The verification problem</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "verification-problem". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --border: #e8e5df;
    --muted: #faf8f3;
    --muted-fg: #5a5a5a;
    --fg: #1a1a1a;
    --card: #ffffff;
    --ring: #1a1a1a;
    --comply: #7a4a0d;
    --defect: #8a5a2b;
    --brand: #b87018;
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
  .eyebrow {
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted-fg);
    margin: 0;
  }
  header { padding: 20px; border-bottom: 1px solid var(--border); }
  .head-grid { display: grid; gap: 16px; margin-top: 12px; }
  @media (min-width: 720px) {
    .head-grid { grid-template-columns: 1fr 14rem; align-items: end; }
  }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 30px; line-height: 1.15; margin: 0; max-width: 42rem; }
  .lede { color: var(--muted-fg); margin: 12px 0 0; max-width: 42rem; }
  .prompt-box {
    border: 1px solid var(--border);
    background: var(--muted);
    border-radius: 8px;
    padding: 12px;
    font-size: 12px;
    font-weight: 500;
    margin: 0;
  }
  .options { display: grid; gap: 12px; padding: 16px; }
  @media (min-width: 640px) { .options { grid-template-columns: 1fr 1fr; padding: 20px; } }
  .option {
    font: inherit;
    text-align: left;
    color: inherit;
    border: 1px solid var(--border);
    background: #fff;
    border-radius: 8px;
    padding: 16px;
    cursor: pointer;
    transition: background-color 120ms;
  }
  .option:hover { background: var(--muted); }
  .option:focus-visible { outline: 2px solid var(--ring); outline-offset: 2px; }
  .option.is-open { border-color: var(--brand); box-shadow: 0 0 0 1px var(--brand); }
  .option-top { display: flex; justify-content: space-between; align-items: center; gap: 12px; }
  .option-label { font-size: 10px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--muted-fg); }
  .inspected { display: none; align-items: center; gap: 4px; font-size: 11px; font-weight: 500; color: var(--comply); }
  .option.is-seen .inspected { display: inline-flex; }
  .option-question { display: block; margin-top: 20px; font-family: var(--font-heading); font-size: 20px; font-weight: 600; }
  .option-summary { display: block; margin-top: 6px; color: var(--muted-fg); }
  .option-cta { display: block; margin-top: 16px; font-size: 12px; font-weight: 500; color: var(--brand); }
  .detail { display: none; border-top: 1px solid var(--border); background: var(--muted); padding: 16px; }
  .detail.is-open { display: block; }
  .detail-card { border: 1px solid var(--border); background: var(--card); border-radius: 8px; padding: 16px 20px; }
  .detail-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 16px; }
  .verdict { margin: 0; }
  .verdict.holds { color: var(--comply); }
  .verdict.fails { color: var(--defect); }
  .outcome { margin: 6px 0 0; font-family: var(--font-heading); font-size: 22px; font-weight: 600; display: flex; align-items: center; gap: 8px; }
  .close {
    font: inherit; border: 0; background: transparent; color: var(--muted-fg);
    width: 32px; height: 32px; border-radius: 6px; cursor: pointer; font-size: 18px; line-height: 1;
  }
  .close:hover { background: var(--muted); color: var(--fg); }
  .detail-body { color: var(--muted-fg); margin-top: 16px; max-width: 48rem; }
  .detail-body p { margin: 0 0 8px; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
</style>
</head>
<body>
<section aria-labelledby="vp-title">
  <header>
    <p class="eyebrow">An introduction to the verification problem</p>
    <div class="head-grid">
      <div>
        <h1 id="vp-title">Two rivals. One treaty. Zero trust.</h1>
        <p class="lede">Two adversarial states have signed a mutual agreement limiting a dangerous technology. Neither believes the other for a second.</p>
      </div>
      <p class="prompt-box">How do you know the other party will uphold its obligations, and how does it know you will follow yours?</p>
    </div>
  </header>

  <div class="options" id="options" role="list"></div>

  <div class="detail" id="detail" role="region" aria-live="polite">
    <div class="detail-card">
      <div class="detail-top">
        <div>
          <p class="eyebrow verdict" id="verdict"></p>
          <h2 class="outcome" id="outcome"></h2>
        </div>
        <button type="button" class="close" id="close" aria-label="Close">&times;</button>
      </div>
      <div class="detail-body" id="detail-body"></div>
    </div>
  </div>
</section>

<script>
  var OPTIONS = [
    {
      id: "trust",
      label: "Option 01",
      question: "Trust?",
      summary: "A handshake, a signature and a promise kept on honor alone.",
      outcome: "It collapses",
      holds: false,
      detail: [
        "You could trust each other, and trust each other’s trust. Works with friends, but not with nation-state adversaries incentivized to self-protect by gaining the secret upper hand, and especially not when dealing with the development of high-risk technologies."
      ]
    },
    {
      id: "punish",
      label: "Option 02",
      question: "Punish violations?",
      summary: "Sanctions, retaliation and consequences severe enough to deter misconduct.",
      outcome: "It arrives too late",
      holds: false,
      detail: [
        "In the absence of trust, they could penalize violations of the agreement and preempt misconduct. But deterrence depends upon the reliability of tracking each party’s actions. Moreover, an ex-post regime fails when consequences are immediate, far-reaching, and irreversible: no fine can bring back the dead."
      ]
    },
    {
      id: "open",
      label: "Option 03",
      question: "Mutual transparency?",
      summary: "Open the books, show the facilities and publish the research.",
      outcome: "It backfires",
      holds: false,
      detail: [
        "They could mutually disclose actions, but increased transparency risks theft of proprietary information or prototypes by adversaries. Each party is still incentivized to develop a secret advantage and fabricate compliance."
      ]
    },
    {
      id: "verify",
      label: "Option 04",
      question: "Neutral, privacy-preserving verification mechanisms?",
      summary: "Prove compliance without surrendering the secrets around it.",
      outcome: "It holds",
      holds: true,
      detail: [
        "What if you could mutually verify compliance without risking undue loss of privacy? If each party could verify the other’s compliance without learning their secrets, knowing they can do the same, they have fewer material incentives to dodge compliance. Verification displaces the impossible promise of trust in a volatile adversary toward trust in a shared, robust verification regime."
      ]
    }
  ];

  var openId = null;
  var visited = {};
  var optionsEl = document.getElementById("options");
  var detailEl = document.getElementById("detail");

  function el(tag, className, text) {
    var node = document.createElement(tag);
    if (className) node.className = className;
    if (text !== undefined) node.textContent = text;
    return node;
  }

  OPTIONS.forEach(function (option) {
    var button = el("button", "option");
    button.type = "button";
    button.setAttribute("role", "listitem");
    button.dataset.id = option.id;

    var top = el("span", "option-top");
    top.appendChild(el("span", "option-label", option.label));
    top.appendChild(el("span", "inspected", "✓ Inspected"));
    button.appendChild(top);
    button.appendChild(el("span", "option-question", option.question));
    button.appendChild(el("span", "option-summary", option.summary));
    button.appendChild(el("span", "option-cta", "Test this answer →"));

    button.addEventListener("click", function () { inspect(option); });
    optionsEl.appendChild(button);
  });

  function render() {
    var buttons = optionsEl.querySelectorAll(".option");
    for (var i = 0; i < buttons.length; i++) {
      var id = buttons[i].dataset.id;
      buttons[i].classList.toggle("is-open", id === openId);
      buttons[i].classList.toggle("is-seen", !!visited[id]);
      buttons[i].setAttribute("aria-expanded", id === openId ? "true" : "false");
    }
    detailEl.classList.toggle("is-open", openId !== null);
  }

  function inspect(option) {
    visited[option.id] = true;
    openId = option.id;
    var verdict = document.getElementById("verdict");
    verdict.textContent = option.holds ? "The answer that holds" : "Failure mode";
    verdict.className = "eyebrow verdict " + (option.holds ? "holds" : "fails");
    document.getElementById("outcome").textContent = (option.holds ? "✔ " : "") + option.outcome + ".";
    var body = document.getElementById("detail-body");
    body.textContent = "";
    option.detail.forEach(function (paragraph) { body.appendChild(el("p", null, paragraph)); });
    render();
    detailEl.scrollIntoView({ behavior: "smooth", block: "nearest" });
  }

  document.getElementById("close").addEventListener("click", function () {
    openId = null;
    render();
  });
</script>
</body>
</html>
