---
id: '04534f4d-b4a3-4484-8e5a-556d7bcb3ac0'
title: Everything comes with a cost
summary_for_tutor: "A two-sided flip card for auditing one of the learner's own policy beliefs. Side A asks for a policy they strongly believe in (typed, or borrowed from four chips: universal healthcare, school vouchers, a carbon tax, banning phones in schools). Flipping the card reveals Side B, which asks for one real cost or downside of enforcing that policy, with an optional lens hint (who pays, who is constrained, what enforcing it requires, what happens to those who refuse). Facing the tradeoff shows both sides as a ledger and asks how easy naming the price was (almost instant, took some thought, genuinely hard); each rating reveals a one-line reflection, the full policy composed as one sentence (I support X at the cost of Y), and the closing line that the question is what we are willing to compromise. The learner's goal, price and rating are saved and shown to you in the widget-state block. Done means the learner has picked a rating; they can then try another policy. Ungraded and personal: acknowledge in one sentence, check only that the price is a cost of enforcing the same policy rather than a cost of the problem it addresses, no praise, no lecture."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Everything comes with a cost</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "policy-cost". -->
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
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 24px; line-height: 1.2; margin: 0; }
  .lede { color: var(--muted); margin: 6px 0 0; max-width: 52ch; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .stage { margin-top: 16px; perspective: 1400px; }
  .flip { display: grid; transition: transform 500ms; transform-style: preserve-3d; }
  .flip.is-flipped { transform: rotateY(180deg); }
  @media (prefers-reduced-motion: reduce) { .flip { transition: none; } }
  .face {
    grid-column: 1; grid-row: 1; min-width: 0;
    display: flex; flex-direction: column; gap: 12px;
    border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 20px;
    backface-visibility: hidden; -webkit-backface-visibility: hidden;
  }
  .face-b { transform: rotateY(180deg); }
  .face[inert] { pointer-events: none; }
  [hidden] { display: none !important; }
  label { font-weight: 600; }
  input[type="text"] {
    width: 100%; font: inherit; color: inherit; background: #fff;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  input[type="text"]:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  .chips { display: flex; flex-wrap: wrap; align-items: center; gap: 6px; font-size: 12px; color: var(--muted); }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button:disabled { opacity: 0.5; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.pill { border-radius: 999px; padding: 3px 10px; font-size: 12px; font-weight: 600; color: var(--muted); }
  button.pill:hover { color: var(--text); }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button.link { border: 0; border-bottom: 1px dotted var(--muted); border-radius: 0; background: transparent; padding: 0 0 1px; font-size: 12px; color: var(--muted); align-self: flex-start; }
  button.link:hover { color: var(--text); background: transparent; }
  .echo { font-size: 12px; color: var(--muted); overflow-wrap: anywhere; margin: 0; }
  .echo b { color: var(--text); font-weight: 600; }
  .lenses { font-size: 12px; line-height: 1.8; color: var(--muted); margin: 0; }
  .foot { display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 8px; }
  .faced { margin-top: 16px; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 20px; display: flex; flex-direction: column; gap: 16px; }
  .ledger { display: flex; flex-direction: column; gap: 8px; }
  .row { display: flex; align-items: baseline; gap: 12px; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 12px; }
  .row .eyebrow { flex: none; width: 6rem; }
  .row .val { min-width: 0; font-size: 16px; line-height: 1.3; overflow-wrap: anywhere; }
  .ask { font-weight: 600; margin: 0; }
  .ease { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; }
  .ease button.pill[aria-pressed="true"] { border-color: var(--text); color: var(--text); background: var(--surface); box-shadow: 0 0 0 1px var(--text); }
  .ease button.pill[aria-pressed="true"]::before { content: "\2713 "; }
  .ease.has-choice button.pill[aria-pressed="false"] { opacity: 0.5; }
  .reveal { display: flex; flex-direction: column; gap: 16px; }
  .branch { border-top: 1px solid var(--border); padding-top: 12px; color: var(--muted); margin: 0; }
  .full { border: 1px solid var(--text); border-radius: 8px; padding: 16px; }
  .full p { margin: 8px 0 0; font-size: 16px; line-height: 1.3; color: var(--muted); overflow-wrap: anywhere; }
  .full b { color: var(--text); font-weight: 600; }
  .closer { font-size: 16px; margin: 0; }
  @media (max-width: 480px) {
    .row { flex-direction: column; gap: 4px; }
    .row .eyebrow { width: auto; }
  }
</style>
</head>
<body>
<section aria-labelledby="pc-title">
  <h1 id="pc-title">Everything comes with a cost.</h1>
  <p class="lede">A sixty-second exercise: before you scope policy for anyone else, audit one of your own.</p>

  <div class="stage" id="stage">
    <div class="flip" id="flip">
      <form class="face face-a" id="form-a">
        <p class="eyebrow">Side A · The goal</p>
        <label for="pc-policy">A policy you strongly believe in:</label>
        <input type="text" id="pc-policy" maxlength="90" autocomplete="off" placeholder="type it here…">
        <div class="chips" id="chips"><span>or borrow one:</span></div>
        <div class="foot">
          <span></span>
          <button type="submit" class="primary" id="flip-btn" disabled>Flip the card</button>
        </div>
      </form>

      <form class="face face-b" id="form-b" inert>
        <p class="eyebrow">Side B · The price</p>
        <p class="echo">Side A: <b id="echo"></b></p>
        <label for="pc-price">One real cost or downside of enforcing it:</label>
        <input type="text" id="pc-price" maxlength="160" autocomplete="off" placeholder="be honest, one is enough">
        <button type="button" class="link" id="stuck" aria-expanded="false" aria-controls="lenses">Stuck? Try a lens</button>
        <p class="lenses" id="lenses" hidden>Who pays? · Who is constrained? · What does enforcing it require? · What happens to those who refuse?</p>
        <div class="foot">
          <button type="button" id="back-btn">← Back</button>
          <button type="submit" class="primary" id="face-btn" disabled>Face the tradeoff</button>
        </div>
      </form>
    </div>
  </div>

  <div class="faced" id="faced" hidden>
    <p class="eyebrow">Both sides of the card</p>
    <div class="ledger">
      <div class="row"><span class="eyebrow">The goal</span><span class="val" id="led-goal"></span></div>
      <div class="row"><span class="eyebrow">The price</span><span class="val" id="led-price"></span></div>
    </div>
    <div>
      <p class="ask" id="ask">Naming the price: how easy was it?</p>
      <div class="ease" id="ease" role="group" aria-labelledby="ask"></div>
    </div>
    <div class="reveal" id="reveal" hidden>
      <p class="branch" id="branch" aria-live="polite"></p>
      <div class="full">
        <p class="eyebrow">The full policy</p>
        <p id="full"></p>
      </div>
      <p class="closer">The question is never just <em>what do we want to accomplish?</em> It is <em>what are we willing to compromise to get it?</em></p>
      <button type="button" class="link" id="again">Try another policy</button>
    </div>
  </div>
</section>

<script>
  var CHIPS = ["Universal healthcare", "School vouchers", "A carbon tax", "Banning phones in schools"];
  var EASE = [
    { key: "instant", label: "Almost instant", line: "The cost was there all along; it just isn’t the half we practice saying out loud." },
    { key: "thought", label: "Took some thought", line: "Conviction keeps the goal in sharp focus and the price in the blur." },
    { key: "hard", label: "Genuinely hard", line: "When a policy feels cost-free, its costs usually land on someone outside our view, or no one has looked yet." }
  ];
  var STORE_KEY = "lens-widget-policy-cost";

  var state = { policy: "", price: "", flipped: false, lenses: false, faced: false, ease: null, history: [] };
  var completed = false;

  var flip = document.getElementById("flip");
  var stage = document.getElementById("stage");
  var formA = document.getElementById("form-a");
  var formB = document.getElementById("form-b");
  var policyInput = document.getElementById("pc-policy");
  var priceInput = document.getElementById("pc-price");
  var flipBtn = document.getElementById("flip-btn");
  var faceBtn = document.getElementById("face-btn");
  var backBtn = document.getElementById("back-btn");
  var stuckBtn = document.getElementById("stuck");
  var lensesEl = document.getElementById("lenses");
  var echoEl = document.getElementById("echo");
  var faced = document.getElementById("faced");
  var easeEl = document.getElementById("ease");
  var reveal = document.getElementById("reveal");
  var branchEl = document.getElementById("branch");
  var fullEl = document.getElementById("full");
  var easeButtons = {};

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function easeByKey(key) { for (var i = 0; i < EASE.length; i++) if (EASE[i].key === key) return EASE[i]; return null; }
  function setInert(node, on) {
    if (on) { node.setAttribute("inert", ""); node.setAttribute("aria-hidden", "true"); }
    else { node.removeAttribute("inert"); node.removeAttribute("aria-hidden"); }
  }

  var chipsEl = document.getElementById("chips");
  CHIPS.forEach(function (chip) {
    var b = el("button", "pill", chip);
    b.type = "button";
    b.addEventListener("click", function () {
      state.policy = chip;
      render();
      persist();
      policyInput.focus();
    });
    chipsEl.appendChild(b);
  });

  EASE.forEach(function (e) {
    var b = el("button", "pill", e.label);
    b.type = "button";
    b.setAttribute("aria-pressed", "false");
    b.addEventListener("click", function () {
      state.ease = e.key;
      render();
      persist();
    });
    easeButtons[e.key] = b;
    easeEl.appendChild(b);
  });

  function summary() {
    var goal = state.policy.trim() || "(not written yet)";
    var lines = ["Side A (the goal): " + goal + "."];
    if (state.flipped || state.faced) lines.push("Side B (the price): " + (state.price.trim() || "(not written yet)") + ".");
    if (!state.faced) {
      lines.push(state.flipped ? "The card is flipped to Side B; the learner has not faced the tradeoff yet." : "The card shows Side A; not flipped yet.");
    } else if (!state.ease) {
      lines.push("The learner has faced the tradeoff but not yet rated how easy naming the price was.");
    } else {
      var e = easeByKey(state.ease);
      lines.push("Rated naming the price as: " + e.label + ". Reflection shown: " + e.line);
      lines.push("Full policy: I support " + state.policy.trim() + " at the cost of " + state.price.trim() + ".");
    }
    if (state.history.length) {
      var prev = state.history.map(function (h) {
        var he = easeByKey(h.ease);
        return "I support " + h.policy + " at the cost of " + h.price + " (" + (he ? he.label.toLowerCase() : "unrated") + ")";
      });
      lines.push("Earlier cards: " + prev.join("; ") + ".");
    }
    return lines.join(" ");
  }

  function persist() {
    var snapshot = {
      policy: state.policy, price: state.price, flipped: state.flipped, lenses: state.lenses,
      faced: state.faced, ease: state.ease, history: state.history
    };
    if (window.Lens) {
      Lens.saveState(snapshot, summary());
      if (!completed && state.faced && state.ease) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORE_KEY, JSON.stringify(snapshot)); } catch (err) { /* storage unavailable */ }
    }
  }

  function render() {
    var hasPolicy = !!state.policy.trim();
    var hasPrice = !!state.price.trim();
    if (policyInput.value !== state.policy) policyInput.value = state.policy;
    if (priceInput.value !== state.price) priceInput.value = state.price;
    flipBtn.disabled = !hasPolicy;
    faceBtn.disabled = !(hasPolicy && hasPrice);
    echoEl.textContent = state.policy;
    flip.classList.toggle("is-flipped", state.flipped);
    setInert(formA, state.flipped);
    setInert(formB, !state.flipped);
    stuckBtn.setAttribute("aria-expanded", state.lenses ? "true" : "false");
    lensesEl.hidden = !state.lenses;

    stage.hidden = state.faced;
    faced.hidden = !state.faced;
    document.getElementById("led-goal").textContent = state.policy;
    document.getElementById("led-price").textContent = state.price;
    EASE.forEach(function (e) { easeButtons[e.key].setAttribute("aria-pressed", state.ease === e.key ? "true" : "false"); });
    easeEl.classList.toggle("has-choice", !!state.ease);
    var chosen = easeByKey(state.ease);
    reveal.hidden = !chosen;
    if (chosen) {
      branchEl.textContent = chosen.line;
      fullEl.textContent = "";
      fullEl.appendChild(document.createTextNode("I support "));
      fullEl.appendChild(el("b", null, state.policy));
      fullEl.appendChild(document.createTextNode(" at the cost of "));
      fullEl.appendChild(el("b", null, state.price));
      fullEl.appendChild(document.createTextNode("."));
    }
  }

  policyInput.addEventListener("input", function () { state.policy = policyInput.value; render(); persist(); });
  priceInput.addEventListener("input", function () { state.price = priceInput.value; render(); persist(); });

  formA.addEventListener("submit", function (event) {
    event.preventDefault();
    if (!state.policy.trim()) return;
    state.flipped = true;
    render();
    persist();
    window.setTimeout(function () { priceInput.focus({ preventScroll: true }); }, 560);
  });
  backBtn.addEventListener("click", function () {
    state.flipped = false;
    render();
    persist();
    window.setTimeout(function () { policyInput.focus({ preventScroll: true }); }, 560);
  });
  stuckBtn.addEventListener("click", function () { state.lenses = !state.lenses; render(); persist(); });
  formB.addEventListener("submit", function (event) {
    event.preventDefault();
    if (!state.policy.trim() || !state.price.trim()) return;
    state.faced = true;
    render();
    persist();
  });
  document.getElementById("again").addEventListener("click", function () {
    if (state.policy.trim() && state.price.trim()) {
      state.history.push({ policy: state.policy.trim(), price: state.price.trim(), ease: state.ease });
      if (state.history.length > 10) state.history = state.history.slice(-10);
    }
    state.policy = ""; state.price = ""; state.flipped = false; state.lenses = false; state.faced = false; state.ease = null;
    render();
    persist();
    policyInput.focus({ preventScroll: true });
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.policy === "string") state.policy = saved.policy.slice(0, 90);
      if (typeof saved.price === "string") state.price = saved.price.slice(0, 160);
      state.flipped = !!saved.flipped;
      state.lenses = !!saved.lenses;
      state.faced = !!saved.faced && !!state.policy.trim() && !!state.price.trim();
      state.ease = easeByKey(saved.ease) ? saved.ease : null;
      if (Array.isArray(saved.history)) {
        state.history = saved.history.filter(function (h) {
          return h && typeof h.policy === "string" && typeof h.price === "string";
        }).slice(-10);
      }
    }
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = localStorage.getItem(STORE_KEY); } catch (err) { raw = null; }
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (err) { /* ignore bad data */ } }
  }
</script>
</body>
</html>
