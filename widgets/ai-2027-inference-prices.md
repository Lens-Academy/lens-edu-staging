---
id: '9268dc8c-7ac4-4c2c-92ee-33e2b67e9482'
title: How fast LLM inference prices fell at fixed capability (Epoch AI data)
summary_for_tutor: "An interactive replacement for the static Epoch AI chart in the AI 2027 article (July 2027 section, where the scenario's Agent-3-mini is 10x cheaper than Agent-3). It plots, on a log price axis against release date, the cheapest model that matched or beat a fixed performance threshold on a benchmark: for example the price of reaching GPT-4-0314's GPQA score fell from 37.50 to 0.12 dollars per million tokens between March 2023 and December 2024. Data are Epoch AI's public table behind its insight 'LLM inference prices have fallen 9x to 900x/year, depending on the task' (119 rows, 21 benchmark-threshold series over six benchmarks: MMLU, GPQA Diamond, MATH-500, MATH 5, HumanEval, LMSys Chatbot Arena ELO). The learner picks a benchmark, toggles its threshold series on and off, and hovers or arrows through the points to read model, date, price and score; each series shows Epoch's fitted trend and the yearly price-drop factor it implies (9x for GPT-3.5-Turbo-level MMLU, about 40x for GPT-4-level GPQA, about 900x for GPT-4o-level GPQA). Done means the learner has opened at least three benchmarks. Useful discussion: why the rate varies so much by threshold, why the fastest drops are the most recent thresholds, and whether the scenario's 10x-cheaper Agent-3-mini is ambitious or ordinary against this record."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>LLM inference prices at fixed capability</title>
<!-- Interactive replacement for the static Epoch AI chart "LLM inference prices have fallen 9x to 900x/year, depending on the task" in the AI 2027 article (ai-2027.com, section "July 2027: The Cheap Remote Worker").
     Data: Epoch AI data insight "LLM inference price trends", table "Lowest inference prices at fixed performance",
     https://epoch.ai/data/charts/llm-inference-price-trends/lowest_price_models_data.csv (linked from https://epoch.ai/data-insights/llm-inference-price-trends), retrieved 2026-09-08. Licence CC-BY; underlying prices and scores from Epoch AI and Artificial Analysis.
     Columns kept verbatim: Benchmark, Threshold model, Performance range, Model Name, Release Date, USD per 1M Tokens, Predicted log price (Epoch's fitted value for that point), Benchmark score.
     The yearly decline factor per series is computed on this page from Epoch's fitted values at the first and last point of the series: (first fitted / last fitted) ^ (1 / years between them). -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10; --grey: #8a8a8a;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 22px; margin: 4px 0 6px; }
  .lede { color: var(--muted); margin: 0 0 12px; max-width: 46rem; }
  .controls { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; margin-bottom: 8px; }
  .group-label { font-size: 11px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.08em; margin-right: 4px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 6px; background: #fff; padding: 5px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button[aria-checked="true"] { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); font-weight: 600; }
  button[aria-pressed="true"]::before { content: "\2713 "; color: var(--accent); }
  button[aria-pressed="false"] { color: var(--muted); }
  .series-btn { display: inline-flex; align-items: center; gap: 6px; font-size: 12px; }
  .chart-box { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px; overflow-x: auto; }
  .chart-box svg { display: block; width: 100%; height: auto; min-width: 520px; font-family: var(--font-ui); }
  .axis text { font-size: 11px; fill: var(--muted); }
  .grid line { stroke: var(--border); stroke-width: 1; }
  .pt { cursor: pointer; }
  .hit { fill: transparent; pointer-events: all; }
  .detail { margin-top: 10px; border: 1px solid var(--border); border-radius: 8px; padding: 12px 14px; background: var(--surface); min-height: 64px; }
  .detail h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
  .detail p { margin: 0; }
  .rates { margin-top: 10px; display: grid; gap: 8px; grid-template-columns: repeat(auto-fill, minmax(190px, 1fr)); }
  .stat { border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: #fff; }
  .stat .big { font-family: var(--font-heading); font-size: 22px; font-weight: 600; }
  .stat .sub { color: var(--muted); font-size: 12px; }
  .list-wrap { margin-top: 12px; }
  .list { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 6px; }
  .list button { font-size: 12px; padding: 4px 8px; }
  .list button.is-current { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .foot { margin-top: 12px; font-size: 12px; color: var(--muted); }
  .foot p { margin: 0 0 6px; }
  a { color: var(--accent); }
  .done { margin-top: 10px; font-size: 12px; color: var(--muted); }
  .done.is-visible::before { content: "\2713 "; color: var(--accent); }
</style>
</head>
<body>
<p class="eyebrow">Interactive chart</p>
<h1>The price of a fixed level of capability, over time</h1>
<p class="lede">Epoch AI tracked the cheapest model that matched or beat a given score on a benchmark, and how quickly that price fell. Pick a benchmark, switch its performance thresholds on and off, and hover or arrow through the points.</p>

<div class="controls" role="radiogroup" aria-label="Benchmark" id="benchmarks"><span class="group-label">Benchmark</span></div>
<div class="controls" id="series" aria-label="Performance thresholds"><span class="group-label">Threshold</span></div>

<div class="chart-box" id="chart-box"></div>

<div class="detail" id="detail" aria-live="polite">
  <h2 id="d-title">Hover a point, or use the list below</h2>
  <p id="d-body">Each point is the cheapest model, at its release date, that met the threshold. Each dashed line is Epoch's fitted price trend for that threshold.</p>
</div>

<div class="rates" id="rates"></div>

<div class="list-wrap">
  <p class="eyebrow">Points (arrow keys move between them)</p>
  <div class="list" id="list" role="list"></div>
</div>
<p class="done" id="done"></p>

<div class="foot">
  <p>Data: Epoch AI, "LLM inference price trends" (<a href="https://epoch.ai/data-insights/llm-inference-price-trends" target="_blank" rel="noopener">epoch.ai/data-insights/llm-inference-price-trends</a>), table "Lowest inference prices at fixed performance", retrieved 8 Sep 2026, CC-BY; prices and scores from Epoch AI and Artificial Analysis. Prices are US dollars per million tokens. Epoch's summary: the rate of decline "varies dramatically depending on the performance milestone, ranging from 9x to 900x per year."</p>
  <p>The yearly factor shown for each threshold is computed on this page from Epoch's fitted values at the first and last point of that series.</p>
</div>

<script>
var ROWS = [
  ["MMLU", "GPT-3", "[43.9, 100]", "GPT-3", "2021-11-20", 60.0, 60.18506522402149, 43.9],
  ["MMLU", "GPT-3", "[43.9, 100]", "GPT-3", "2022-09-01", 20.0, 8.776477618564474, 43.9],
  ["MMLU", "GPT-3", "[43.9, 100]", "GPT-3.5 Turbo", "2023-03-06", 2.0, 2.4981027096259245, 68.0],
  ["MMLU", "GPT-3", "[43.9, 100]", "Llama-2-Chat-13B", "2023-07-18", 0.56, 1.0103326917473903, 45.0],
  ["MMLU", "GPT-3", "[43.9, 100]", "Llama 2-7B", "2023-12-01", 0.2, 0.403135155212311, 45.3],
  ["MMLU", "GPT-3", "[43.9, 100]", "Llama 2-7B", "2024-04-14", 0.13, 0.1619462377470186, 45.3],
  ["MMLU", "GPT-3", "[43.9, 100]", "Llama-3.1-Instruct-8B", "2024-07-23", 0.1, 0.08240971495475764, 71.0],
  ["MMLU", "GPT-3", "[43.9, 100]", "Llama-3.2-Instruct-3B", "2024-09-24", 0.08, 0.053844477592512346, 64.0],
  ["MMLU", "GPT-3", "[43.9, 100]", "Gemini-1.5-Flash-8B", "2024-10-03", 0.07, 0.05066824328029649, 75.0],
  ["MMLU", "GPT-3.5", "[64.8, 100]", "GPT-3.5", "2022-11-30", 20.0, 10.005324256244808, 64.8],
  ["MMLU", "GPT-3.5", "[64.8, 100]", "GPT-3.5 Turbo", "2023-03-06", 2.0, 4.838877810589961, 68.0],
  ["MMLU", "GPT-3.5", "[64.8, 100]", "GPT-3.5-Turbo-2023-11", "2023-11-06", 0.75, 0.7578736114262563, 68.0],
  ["MMLU", "GPT-3.5", "[64.8, 100]", "Claude-3-Haiku", "2024-03-04", 0.5, 0.3079817361983056, 71.0],
  ["MMLU", "GPT-3.5", "[64.8, 100]", "Gemini-1.5-Flash-2024-05", "2024-05-10", 0.13, 0.1854990406191638, 79.0],
  ["MMLU", "GPT-3.5", "[64.8, 100]", "Llama-3.1-Instruct-8B", "2024-07-23", 0.1, 0.1059629761975539, 71.0],
  ["MMLU", "GPT-3.5", "[64.8, 100]", "Gemini-1.5-Flash-8B", "2024-10-03", 0.07, 0.06145245870247992, 75.0],
  ["MMLU", "GPT-3.5 Turbo", "[68.0, 100]", "GPT-3.5 Turbo", "2023-03-06", 2.0, 2.587583053564357, 68.0],
  ["MMLU", "GPT-3.5 Turbo", "[68.0, 100]", "GPT-3.5-Turbo-2023-11", "2023-11-06", 0.75, 0.5772173975128928, 68.0],
  ["MMLU", "GPT-3.5 Turbo", "[68.0, 100]", "Claude-3-Haiku", "2024-03-04", 0.5, 0.27852866425647577, 71.0],
  ["MMLU", "GPT-3.5 Turbo", "[68.0, 100]", "Gemini-1.5-Flash-2024-05", "2024-05-10", 0.13, 0.18479472953267684, 79.0],
  ["MMLU", "GPT-3.5 Turbo", "[68.0, 100]", "Llama-3.1-Instruct-8B", "2024-07-23", 0.1, 0.11746092351942101, 71.0],
  ["MMLU", "GPT-3.5 Turbo", "[68.0, 100]", "Gemini-1.5-Flash-8B", "2024-10-03", 0.07, 0.07558159574661118, 75.0],
  ["MMLU", "GPT-4-0314", "[86.0, 100]", "GPT-4-0314", "2023-03-14", 37.5, 66.20683541044728, 86.0],
  ["MMLU", "GPT-4-0314", "[86.0, 100]", "GPT-4 Turbo", "2023-11-06", 15.0, 11.004884076125416, 87.0],
  ["MMLU", "GPT-4-0314", "[86.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 2.6309012140350614, 87.0],
  ["MMLU", "GPT-4-0314", "[86.0, 100]", "Gemini-1.5-Pro-2024-05", "2024-05-23", 2.19, 2.439057014986802, 86.0],
  ["MMLU", "GPT-4-0314", "[86.0, 100]", "Gemini 2.0 Flash", "2025-02-05", 0.175, 0.34582083736647057, 88.0],
  ["MMLU", "GPT-4 Turbo", "[87.0, 100]", "GPT-4 Turbo", "2023-11-06", 15.0, 30.753920946642545, 87.0],
  ["MMLU", "GPT-4 Turbo", "[87.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 4.823277394204966, 87.0],
  ["MMLU", "GPT-4 Turbo", "[87.0, 100]", "Claude-3.5-Sonnet-2024-06", "2024-06-20", 6.0, 3.323373896590997, 88.0],
  ["MMLU", "GPT-4 Turbo", "[87.0, 100]", "Llama-3.1-Instruct-405B", "2024-07-23", 3.5, 2.4049208028496873, 87.0],
  ["MMLU", "GPT-4 Turbo", "[87.0, 100]", "Gemini 2.0 Flash", "2025-02-05", 0.175, 0.34872826505641785, 88.0],
  ["GPQA Diamond", "GPT-4-0314", "[33.0, 100]", "GPT-4-0314", "2023-03-14", 37.5, 53.03051531989006, 33.0],
  ["GPQA Diamond", "GPT-4-0314", "[33.0, 100]", "GPT-4 Turbo", "2023-11-06", 15.0, 4.681640819983042, 50.0],
  ["GPQA Diamond", "GPT-4-0314", "[33.0, 100]", "Mistral-Large-2024-02", "2024-02-26", 6.0, 1.4867737676929313, 36.0],
  ["GPQA Diamond", "GPT-4-0314", "[33.0, 100]", "Claude-3-Haiku", "2024-03-04", 0.5, 1.3839178622741644, 33.0],
  ["GPQA Diamond", "GPT-4-0314", "[33.0, 100]", "Gemini-1.5-Flash-2024-05", "2024-05-10", 0.13, 0.6967996973317301, 39.0],
  ["GPQA Diamond", "GPT-4-0314", "[33.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.07549811802856932, 53.0],
  ["GPQA Diamond", "GPT-4 Turbo", "[50.0, 100]", "GPT-4 Turbo", "2023-11-06", 15.0, 34.1148705847694, 50.0],
  ["GPQA Diamond", "GPT-4 Turbo", "[50.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 4.685484763911751, 53.0],
  ["GPQA Diamond", "GPT-4 Turbo", "[50.0, 100]", "Claude-3.5-Sonnet-2024-06", "2024-06-20", 6.0, 3.143433815985568, 56.0],
  ["GPQA Diamond", "GPT-4 Turbo", "[50.0, 100]", "Llama-3.1-Instruct-405B", "2024-07-23", 3.5, 2.2226104388321386, 50.0],
  ["GPQA Diamond", "GPT-4 Turbo", "[50.0, 100]", "Gemini-1.5-Pro-2024-09", "2024-09-24", 2.19, 1.146745251272404, 61.0],
  ["GPQA Diamond", "GPT-4 Turbo", "[50.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.4949019233727883, 53.0],
  ["GPQA Diamond", "GPT-4o-2024-05", "[53.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 11.09418171131444, 53.0],
  ["GPQA Diamond", "GPT-4o-2024-05", "[53.0, 100]", "Claude-3.5-Sonnet-2024-06", "2024-06-20", 6.0, 5.496078097704327, 56.0],
  ["GPQA Diamond", "GPT-4o-2024-05", "[53.0, 100]", "Gemini-1.5-Pro-2024-09", "2024-09-24", 2.19, 0.932007731873607, 61.0],
  ["GPQA Diamond", "GPT-4o-2024-05", "[53.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.2124344916886354, 53.0],
  ["GPQA Diamond", "Claude-3.5-Sonnet-2024-06", "[56.0, 100]", "Claude-3.5-Sonnet-2024-06", "2024-06-20", 6.0, 7.189651000688689, 56.0],
  ["GPQA Diamond", "Claude-3.5-Sonnet-2024-06", "[56.0, 100]", "Gemini-1.5-Pro-2024-09", "2024-09-24", 2.19, 1.6806964067383174, 61.0],
  ["GPQA Diamond", "Claude-3.5-Sonnet-2024-06", "[56.0, 100]", "DeepSeek-V3", "2024-12-26", 0.4775, 0.41114623063642014, 57.0],
  ["GPQA Diamond", "Claude-3.5-Sonnet-2024-06", "[56.0, 100]", "Gemini 2.0 Flash", "2025-02-05", 0.175, 0.22101074871091442, 62.0],
  ["MATH-500", "GPT-3.5-Turbo-2023-06", "[44.0, 100]", "GPT-3.5-Turbo-2023-06", "2023-06-13", 3.25, 2.6603981346636654, 44.0],
  ["MATH-500", "GPT-3.5-Turbo-2023-06", "[44.0, 100]", "GPT-3.5-Turbo-2023-11", "2023-11-06", 0.75, 0.836662001419071, 44.0],
  ["MATH-500", "GPT-3.5-Turbo-2023-06", "[44.0, 100]", "Gemini-1.5-Flash-2024-05", "2024-05-10", 0.13, 0.19165076377641438, 55.0],
  ["MATH-500", "GPT-3.5-Turbo-2023-06", "[44.0, 100]", "Llama-3.1-Instruct-8B", "2024-07-23", 0.1, 0.1066279812824236, 50.0],
  ["MATH-500", "GPT-3.5-Turbo-2023-06", "[44.0, 100]", "Llama-3.2-Instruct-3B", "2024-09-24", 0.08, 0.0647267226438382, 50.0],
  ["MATH-500", "GPT-3.5-Turbo-2023-06", "[44.0, 100]", "Gemini-1.5-Flash-8B", "2024-10-03", 0.07, 0.06027177267395731, 70.0],
  ["MATH-500", "GPT-4 Turbo", "[74.0, 100]", "GPT-4 Turbo", "2023-11-06", 15.0, 21.367566551959538, 74.0],
  ["MATH-500", "GPT-4 Turbo", "[74.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 1.4853814814383117, 79.0],
  ["MATH-500", "GPT-4 Turbo", "[74.0, 100]", "GPT-4o-mini", "2024-07-18", 0.26, 0.5854448849689556, 79.0],
  ["MATH-500", "GPT-4 Turbo", "[74.0, 100]", "DeepSeek-Coder-V2 236B", "2024-09-11", 0.175, 0.26947968118764654, 74.0],
  ["MATH-500", "GPT-4 Turbo", "[74.0, 100]", "Gemini-1.5-Flash-2024-09", "2024-09-24", 0.13, 0.22432668371368422, 83.0],
  ["MATH-500", "GPT-4 Turbo", "[74.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.07257003169449808, 81.0],
  ["MATH-500", "GPT-4o-2024-05", "[79.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 2.6782610281026753, 79.0],
  ["MATH-500", "GPT-4o-2024-05", "[79.0, 100]", "GPT-4o-mini", "2024-07-18", 0.26, 0.8215453701325247, 79.0],
  ["MATH-500", "GPT-4o-2024-05", "[79.0, 100]", "Gemini-1.5-Flash-2024-09", "2024-09-24", 0.13, 0.24314091181946035, 83.0],
  ["MATH-500", "GPT-4o-2024-05", "[79.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.05804590102486641, 81.0],
  ["MATH 5", "GPT-4-0613", "[23.0, 100]", "GPT-4-0613", "2023-06-13", 37.5, 37.04585385765717, 23.0],
  ["MATH 5", "GPT-4-0613", "[23.0, 100]", "GPT-4 Turbo", "2023-11-06", 15.0, 6.6723689725456925, 36.0],
  ["MATH 5", "GPT-4-0613", "[23.0, 100]", "Mistral-8x22", "2024-04-17", 1.2, 0.9843212305178836, 23.0],
  ["MATH 5", "GPT-4-0613", "[23.0, 100]", "Gemini-1.5-Flash-2024-05", "2024-05-10", 0.13, 0.7513788690307809, 23.0],
  ["MATH 5", "GPT-4-0613", "[23.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.05879869954945238, 65.0],
  ["MATH 5", "GPT-4 Turbo", "[36.0, 100]", "GPT-4 Turbo", "2023-11-06", 15.0, 23.90605625534131, 36.0],
  ["MATH 5", "GPT-4 Turbo", "[36.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 1.7291243571454051, 48.0],
  ["MATH 5", "GPT-4 Turbo", "[36.0, 100]", "Gemini-1.5-Pro-2024-05", "2024-05-23", 2.19, 1.5047789208436055, 41.0],
  ["MATH 5", "GPT-4 Turbo", "[36.0, 100]", "GPT-4o-mini", "2024-07-18", 0.26, 0.6910236853538267, 48.0],
  ["MATH 5", "GPT-4 Turbo", "[36.0, 100]", "Gemini-1.5-Flash-2024-09", "2024-09-24", 0.13, 0.2685894391802283, 58.0],
  ["MATH 5", "GPT-4 Turbo", "[36.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.08836101499488888, 65.0],
  ["MATH 5", "GPT-4o-2024-05", "[48.0, 100]", "GPT-4o-2024-05", "2024-05-13", 7.5, 2.6782610281026753, 48.0],
  ["MATH 5", "GPT-4o-2024-05", "[48.0, 100]", "GPT-4o-mini", "2024-07-18", 0.26, 0.8215453701325247, 48.0],
  ["MATH 5", "GPT-4o-2024-05", "[48.0, 100]", "Gemini-1.5-Flash-2024-09", "2024-09-24", 0.13, 0.24314091181946035, 58.0],
  ["MATH 5", "GPT-4o-2024-05", "[48.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.05804590102486641, 65.0],
  ["HumanEval", "GPT-4-0314", "[67.0, 100]", "GPT-4-0314", "2023-03-14", 37.5, 15.72065741592602, 67.0],
  ["HumanEval", "GPT-4-0314", "[67.0, 100]", "GPT-3.5-Turbo-2023-06", "2023-06-13", 3.25, 6.397571514362263, 71.0],
  ["HumanEval", "GPT-4-0314", "[67.0, 100]", "GPT-3.5-Turbo-2023-11", "2023-11-06", 0.75, 1.51206330543973, 71.0],
  ["HumanEval", "GPT-4-0314", "[67.0, 100]", "Claude-3-Haiku", "2024-03-04", 0.5, 0.4666317112613756, 77.0],
  ["HumanEval", "GPT-4-0314", "[67.0, 100]", "Gemma-2-27B", "2024-06-24", 0.26, 0.15431692716506432, 76.0],
  ["HumanEval", "GPT-4-0314", "[67.0, 100]", "Mistral-NeMo", "2024-07-18", 0.13, 0.12174083544477679, 71.0],
  ["HumanEval", "GPT-4-0314", "[67.0, 100]", "Llama-3.1-Instruct-8B", "2024-07-23", 0.1, 0.11587311331404646, 67.0],
  ["HumanEval", "GPT-3.5-Turbo-2023-06", "[71.0, 100]", "GPT-3.5-Turbo-2023-06", "2023-06-13", 3.25, 2.4184376944610544, 71.0],
  ["HumanEval", "GPT-3.5-Turbo-2023-06", "[71.0, 100]", "GPT-3.5-Turbo-2023-11", "2023-11-06", 0.75, 0.9937140022532409, 71.0],
  ["HumanEval", "GPT-3.5-Turbo-2023-06", "[71.0, 100]", "Claude-3-Haiku", "2024-03-04", 0.5, 0.4813068635606939, 77.0],
  ["HumanEval", "GPT-3.5-Turbo-2023-06", "[71.0, 100]", "Gemma-2-27B", "2024-06-24", 0.26, 0.24327790228004323, 76.0],
  ["HumanEval", "GPT-3.5-Turbo-2023-06", "[71.0, 100]", "Mistral-NeMo", "2024-07-18", 0.13, 0.21018690229455173, 71.0],
  ["HumanEval", "GPT-3.5-Turbo-2023-06", "[71.0, 100]", "Phi 4", "2024-12-13", 0.1225, 0.08531801410939835, 87.0],
  ["LMSys Chatbot Arena ELO", "GPT-3.5 Turbo", "[1106.0, inf]", "GPT-3.5 Turbo", "2023-03-06", 2.0, 2.53105982473423, 1106.0],
  ["LMSys Chatbot Arena ELO", "GPT-3.5 Turbo", "[1106.0, inf]", "GPT-3.5-Turbo-2023-11", "2023-11-06", 0.75, 0.5543877450733306, 1107.0],
  ["LMSys Chatbot Arena ELO", "GPT-3.5 Turbo", "[1106.0, inf]", "Claude-3-Haiku", "2024-03-04", 0.5, 0.26514930643934936, 1179.0],
  ["LMSys Chatbot Arena ELO", "GPT-3.5 Turbo", "[1106.0, inf]", "Llama-3-Instruct-8B", "2024-04-18", 0.15, 0.20061338298536696, 1152.0],
  ["LMSys Chatbot Arena ELO", "GPT-3.5 Turbo", "[1106.0, inf]", "Gemini-1.5-Flash-2024-05", "2024-05-10", 0.13, 0.175041287923676, 1227.0],
  ["LMSys Chatbot Arena ELO", "GPT-3.5 Turbo", "[1106.0, inf]", "Llama-3.1-Instruct-8B", "2024-07-23", 0.1, 0.11064912093592524, 1172.0],
  ["LMSys Chatbot Arena ELO", "GPT-3.5 Turbo", "[1106.0, inf]", "Gemini-1.5-Flash-8B", "2024-10-03", 0.07, 0.07081724342839756, 1211.0],
  ["LMSys Chatbot Arena ELO", "GPT-4-0314", "[1186.0, inf]", "GPT-4-0314", "2023-03-14", 37.5, 87.40141512040913, 1186.0],
  ["LMSys Chatbot Arena ELO", "GPT-4-0314", "[1186.0, inf]", "GPT-4 Turbo", "2023-11-06", 15.0, 5.282232254351241, 1256.0],
  ["LMSys Chatbot Arena ELO", "GPT-4-0314", "[1186.0, inf]", "Claude-3-Sonnet", "2024-03-04", 6.0, 1.290909830017495, 1201.0],
  ["LMSys Chatbot Arena ELO", "GPT-4-0314", "[1186.0, inf]", "Llama-3-Instruct-70B", "2024-04-18", 0.89, 0.7576994800402861, 1206.0],
  ["LMSys Chatbot Arena ELO", "GPT-4-0314", "[1186.0, inf]", "Gemini-1.5-Flash-2024-05", "2024-05-10", 0.13, 0.5839405424874228, 1227.0],
  ["LMSys Chatbot Arena ELO", "GPT-4-0314", "[1186.0, inf]", "Gemini-1.5-Flash-8B", "2024-10-03", 0.07, 0.10365916183253746, 1211.0],
  ["LMSys Chatbot Arena ELO", "GPT-4 Turbo", "[1256.0, inf]", "GPT-4 Turbo", "2023-11-06", 15.0, 28.132355579734362, 1256.0],
  ["LMSys Chatbot Arena ELO", "GPT-4 Turbo", "[1256.0, inf]", "GPT-4o-2024-05", "2024-05-13", 7.5, 1.62781451236301, 1285.0],
  ["LMSys Chatbot Arena ELO", "GPT-4 Turbo", "[1256.0, inf]", "Gemini-1.5-Pro-2024-05", "2024-05-23", 2.19, 1.39998496609322, 1260.0],
  ["LMSys Chatbot Arena ELO", "GPT-4 Turbo", "[1256.0, inf]", "GPT-4o-mini", "2024-07-18", 0.26, 0.6017647240512152, 1273.0],
  ["LMSys Chatbot Arena ELO", "GPT-4 Turbo", "[1256.0, inf]", "Gemini-1.5-Flash-2024-09", "2024-09-24", 0.13, 0.21585008602903238, 1271.0],
  ["LMSys Chatbot Arena ELO", "GPT-4o-2024-05", "[1285.0, inf]", "GPT-4o-2024-05", "2024-05-13", 7.5, 10.845292769015972, 1285.0],
  ["LMSys Chatbot Arena ELO", "GPT-4o-2024-05", "[1285.0, inf]", "GPT-4o-2024-08", "2024-08-06", 4.38, 3.2491012556323997, 1337.0],
  ["LMSys Chatbot Arena ELO", "GPT-4o-2024-05", "[1285.0, inf]", "Gemini-1.5-Pro-2024-09", "2024-09-24", 2.19, 1.621786031966235, 1301.0],
  ["LMSys Chatbot Arena ELO", "GPT-4o-2024-05", "[1285.0, inf]", "DeepSeek-V3", "2024-12-26", 0.4775, 0.4337575032942908, 1318.0],
  ["LMSys Chatbot Arena ELO", "GPT-4o-2024-05", "[1285.0, inf]", "Gemini 2.0 Flash", "2025-02-05", 0.175, 0.24251903470923378, 1358.0]
];
var BENCHMARKS = [
  ["MMLU", "General knowledge"], ["GPQA Diamond", "Ph.D. level science questions"], ["MATH-500", "Math"],
  ["MATH 5", "Advanced math"], ["HumanEval", "Coding"], ["LMSys Chatbot Arena ELO", "Chatbot competition"]
];
var SHAPES = ["circle", "square", "diamond", "triangle", "cross"];
var COLORS = ["#b87018", "#1a1a1a", "#8a8a8a", "#b87018", "#1a1a1a"];

// Build series: one per (benchmark, threshold model), rows in date order.
var SERIES = [];
(function () {
  var map = {};
  ROWS.forEach(function (r) {
    var id = r[0] + "|" + r[1];
    if (!map[id]) { map[id] = { id: id, bench: r[0], threshold: r[1], range: r[2], points: [] }; SERIES.push(map[id]); }
    map[id].points.push({ model: r[3], date: r[4], price: r[5], fitted: r[6], score: r[7], series: map[id] });
  });
  SERIES.forEach(function (s) {
    s.points.sort(function (a, b) { return a.date < b.date ? -1 : 1; });
    var f = s.points[0], l = s.points[s.points.length - 1];
    var yrs = (dnum(l.date) - dnum(f.date)) / 365.25;
    s.rate = yrs > 0 ? Math.pow(f.fitted / l.fitted, 1 / yrs) : null;
    s.lower = parseFloat(s.range.replace("[", "").split(",")[0]);
    s.slot = SERIES.filter(function (q) { return q.bench === s.bench; }).indexOf(s);
    s.points.forEach(function (p, i) { p.key = s.id + "|" + i; });
  });
})();
function dnum(iso) { return Date.UTC(+iso.slice(0, 4), +iso.slice(5, 7) - 1, +iso.slice(8, 10)) / 86400000; }
function decYear(iso) { var y = +iso.slice(0, 4); var s = Date.UTC(y, 0, 1) / 86400000, n = Date.UTC(y + 1, 0, 1) / 86400000; return y + (dnum(iso) - s) / (n - s); }

var W = 720, H = 380, ML = 62, MR = 16, MT = 14, MB = 40;
var X0 = 2021.75, X1 = 2025.4, YMIN = 0.02, YMAX = 200;
var SVGNS = "http://www.w3.org/2000/svg";
var state = { bench: "MMLU", off: {}, seenBench: {}, current: null };
var completed = false;

function el(tag, className, text) { var n = document.createElement(tag); if (className) n.className = className; if (text !== undefined) n.textContent = text; return n; }
function svgEl(tag, attrs, text) { var n = document.createElementNS(SVGNS, tag); for (var k in attrs) n.setAttribute(k, attrs[k]); if (text !== undefined) n.textContent = text; return n; }
function sx(year) { return ML + (year - X0) / (X1 - X0) * (W - ML - MR); }
function sy(price) { var t = (Math.log10(price) - Math.log10(YMIN)) / (Math.log10(YMAX) - Math.log10(YMIN)); return H - MB - t * (H - MT - MB); }
function money(v) { return "$" + (v >= 1 ? v.toFixed(2) : v.toFixed(v >= 0.1 ? 3 : 4)); }
function fmtDate(iso) { return new Date(iso + "T00:00:00Z").toLocaleDateString("en-US", { year: "numeric", month: "short", day: "numeric", timeZone: "UTC" }); }
function fmtRate(r) { return r == null ? "n/a" : (r >= 100 ? Math.round(r / 10) * 10 : Math.round(r)) + "x per year"; }
function marker(shape, x, y, color, r) {
  if (shape === "square") return svgEl("rect", { x: x - r, y: y - r, width: 2 * r, height: 2 * r, fill: color, stroke: "#fff", "stroke-width": 1.5 });
  if (shape === "diamond") return svgEl("polygon", { points: x + "," + (y - r - 1) + " " + (x + r + 1) + "," + y + " " + x + "," + (y + r + 1) + " " + (x - r - 1) + "," + y, fill: color, stroke: "#fff", "stroke-width": 1.5 });
  if (shape === "triangle") return svgEl("polygon", { points: x + "," + (y - r - 1) + " " + (x + r + 1) + "," + (y + r) + " " + (x - r - 1) + "," + (y + r), fill: color, stroke: "#fff", "stroke-width": 1.5 });
  if (shape === "cross") { var g = svgEl("g", {}); g.appendChild(svgEl("line", { x1: x - r, y1: y - r, x2: x + r, y2: y + r, stroke: color, "stroke-width": 3 })); g.appendChild(svgEl("line", { x1: x - r, y1: y + r, x2: x + r, y2: y - r, stroke: color, "stroke-width": 3 })); return g; }
  return svgEl("circle", { cx: x, cy: y, r: r, fill: color, stroke: "#fff", "stroke-width": 1.5 });
}
function activeSeries() { return SERIES.filter(function (s) { return s.bench === state.bench && !state.off[s.id]; }); }
function benchLabel(b) { for (var i = 0; i < BENCHMARKS.length; i++) if (BENCHMARKS[i][0] === b) return BENCHMARKS[i][1]; return ""; }
function thresholdLabel(s) { return s.threshold + " level or better (" + s.bench + " " + (s.range.indexOf("inf") >= 0 ? "at least " + s.lower : "score at least " + s.lower) + ")"; }

function renderControls() {
  var bwrap = document.getElementById("benchmarks");
  while (bwrap.children.length > 1) bwrap.removeChild(bwrap.lastChild);
  BENCHMARKS.forEach(function (b) {
    var btn = el("button", "", b[0] + " (" + b[1] + ")"); btn.type = "button"; btn.setAttribute("role", "radio");
    btn.setAttribute("aria-checked", state.bench === b[0] ? "true" : "false");
    btn.addEventListener("click", function () { state.bench = b[0]; state.current = null; resetDetail(); renderAll(); persist(); });
    bwrap.appendChild(btn);
  });
  var swrap = document.getElementById("series");
  while (swrap.children.length > 1) swrap.removeChild(swrap.lastChild);
  SERIES.filter(function (s) { return s.bench === state.bench; }).forEach(function (s) {
    var btn = el("button", "series-btn"); btn.type = "button";
    btn.setAttribute("aria-pressed", state.off[s.id] ? "false" : "true");
    var sw = svgEl("svg", { width: 14, height: 14, viewBox: "0 0 14 14", "aria-hidden": "true" });
    sw.appendChild(marker(SHAPES[s.slot], 7, 7, COLORS[s.slot], 5));
    btn.appendChild(sw);
    btn.appendChild(document.createTextNode(thresholdLabel(s)));
    btn.addEventListener("click", function () {
      if (state.off[s.id]) delete state.off[s.id]; else state.off[s.id] = true;
      if (state.current && state.current.indexOf(s.id + "|") === 0 && state.off[s.id]) { state.current = null; resetDetail(); }
      renderAll(); persist();
    });
    swrap.appendChild(btn);
  });
}

function drawChart() {
  var box = document.getElementById("chart-box");
  box.textContent = "";
  var svg = svgEl("svg", { viewBox: "0 0 " + W + " " + H, role: "img", "aria-label": "Scatter chart of cheapest model price at a fixed benchmark threshold, by release date, log scale" });
  var grid = svgEl("g", { "class": "grid" }), axis = svgEl("g", { "class": "axis" });
  [0.1, 1, 10, 100].forEach(function (p) {
    var y = sy(p);
    grid.appendChild(svgEl("line", { x1: ML, x2: W - MR, y1: y, y2: y }));
    axis.appendChild(svgEl("text", { x: ML - 6, y: y + 4, "text-anchor": "end" }, "$" + p));
  });
  for (var yr = 2022; yr <= 2025; yr++) {
    var x = sx(yr);
    grid.appendChild(svgEl("line", { x1: x, x2: x, y1: MT, y2: H - MB }));
    axis.appendChild(svgEl("text", { x: x, y: H - MB + 16, "text-anchor": "middle" }, String(yr)));
  }
  axis.appendChild(svgEl("text", { x: (ML + W - MR) / 2, y: H - 6, "text-anchor": "middle" }, "Model release date"));
  axis.appendChild(svgEl("text", { x: 12, y: (MT + H - MB) / 2, "text-anchor": "middle", transform: "rotate(-90 12 " + ((MT + H - MB) / 2) + ")" }, "Price, USD per million tokens (log)"));
  svg.appendChild(grid); svg.appendChild(axis);

  var act = activeSeries();
  act.forEach(function (s) {
    var f = s.points[0], l = s.points[s.points.length - 1];
    svg.appendChild(svgEl("line", { x1: sx(decYear(f.date)), y1: sy(f.fitted), x2: sx(decYear(l.date)), y2: sy(l.fitted), stroke: COLORS[s.slot], "stroke-width": 1.5, "stroke-dasharray": s.slot % 2 ? "2 3" : "6 4", opacity: 0.8 }));
  });
  act.forEach(function (s) {
    s.points.forEach(function (p) {
      var x = sx(decYear(p.date)), y = sy(p.price);
      var g = svgEl("g", { "class": "pt", "data-key": p.key });
      if (state.current === p.key) g.appendChild(svgEl("circle", { cx: x, cy: y, r: 10, fill: "none", stroke: "#1a1a1a", "stroke-width": 1.5 }));
      g.appendChild(marker(SHAPES[s.slot], x, y, COLORS[s.slot], 5));
      g.appendChild(svgEl("circle", { "class": "hit", cx: x, cy: y, r: 12 }));
      g.addEventListener("mouseenter", function () { showPoint(p, false); });
      g.addEventListener("click", function () { showPoint(p, true); });
      svg.appendChild(g);
    });
  });
  if (!act.length) svg.appendChild(svgEl("text", { x: (ML + W - MR) / 2, y: (MT + H - MB) / 2, "text-anchor": "middle", fill: "#5a5a5a" }, "All thresholds for this benchmark are switched off."));
  box.appendChild(svg);

  var rates = document.getElementById("rates");
  rates.textContent = "";
  act.forEach(function (s) {
    var f = s.points[0], l = s.points[s.points.length - 1];
    var d = el("div", "stat");
    d.appendChild(el("div", "eyebrow", s.threshold + " level, " + s.bench));
    d.appendChild(el("div", "big", fmtRate(s.rate)));
    d.appendChild(el("div", "sub", money(f.price) + " (" + f.model + ", " + fmtDate(f.date) + ") to " + money(l.price) + " (" + l.model + ", " + fmtDate(l.date) + "); " + s.points.length + " points."));
    rates.appendChild(d);
  });
}

function resetDetail() {
  document.getElementById("d-title").textContent = "Hover a point, or use the list below";
  document.getElementById("d-body").textContent = "Each point is the cheapest model, at its release date, that met the threshold. Each dashed line is Epoch's fitted price trend for that threshold.";
}
function showPoint(p, commit) {
  if (p.series.bench !== state.bench || state.off[p.series.id]) return;
  document.getElementById("d-title").textContent = p.model + ": " + money(p.price) + " per million tokens";
  document.getElementById("d-body").textContent = "Released " + fmtDate(p.date) + ". " + p.series.bench + " score " + p.score + ", which meets the " + p.series.threshold + " threshold (" + (p.series.range.indexOf("inf") >= 0 ? "at least " + p.series.lower : "score at least " + p.series.lower) + "). Epoch's fitted trend at this date: " + money(p.fitted) + ".";
  if (commit) { state.current = p.key; renderList(); drawChart(); persist(); }
}
function renderList() {
  var list = document.getElementById("list");
  list.textContent = "";
  var pts = [];
  activeSeries().forEach(function (s) { s.points.forEach(function (p) { pts.push(p); }); });
  pts.forEach(function (p, i) {
    var b = el("button", "", p.model + " (" + p.series.threshold + " level)"); b.type = "button"; b.setAttribute("role", "listitem");
    if (state.current === p.key) b.classList.add("is-current");
    b.addEventListener("click", function () { showPoint(p, true); });
    b.addEventListener("focus", function () { showPoint(p, false); });
    b.addEventListener("keydown", function (e) {
      var d = (e.key === "ArrowRight" || e.key === "ArrowDown") ? 1 : (e.key === "ArrowLeft" || e.key === "ArrowUp") ? -1 : 0;
      if (!d) return; e.preventDefault();
      var all = list.querySelectorAll("button"); all[(i + d + all.length) % all.length].focus();
    });
    list.appendChild(b);
  });
}
function summary() {
  var act = activeSeries();
  var lines = ["Epoch inference-price chart. Benchmark shown: " + state.bench + " (" + benchLabel(state.bench) + "). Thresholds on: " + (act.length ? act.map(function (s) { return s.threshold + " level, " + fmtRate(s.rate); }).join("; ") : "none") + ". Benchmarks opened so far: " + Object.keys(state.seenBench).join(", ") + "."];
  if (state.current) { var p = null; SERIES.forEach(function (s) { s.points.forEach(function (q) { if (q.key === state.current) p = q; }); }); if (p) lines.push("Point selected: " + p.model + ", " + fmtDate(p.date) + ", " + money(p.price) + " per million tokens, " + p.series.bench + " score " + p.score + "."); }
  return lines.join(" ");
}
function persist() {
  var n = Object.keys(state.seenBench).length, finished = n >= 3;
  var done = document.getElementById("done");
  done.textContent = finished ? "You have compared " + n + " benchmarks." : "To finish: open at least three benchmarks (" + n + " so far).";
  done.classList.toggle("is-visible", finished);
  if (window.Lens) {
    Lens.saveState({ bench: state.bench, off: state.off, seenBench: state.seenBench, current: state.current }, summary());
    if (finished && !completed) { completed = true; Lens.complete(); }
  } else { try { localStorage.setItem("ai-2027-inference-prices", JSON.stringify(state)); } catch (e) {} }
}
function renderAll() { state.seenBench[state.bench] = true; renderControls(); drawChart(); renderList(); }
function hydrate(saved, meta) {
  if (saved && typeof saved === "object") {
    if (BENCHMARKS.some(function (b) { return b[0] === saved.bench; })) state.bench = saved.bench;
    if (saved.off && typeof saved.off === "object") state.off = saved.off;
    if (saved.seenBench && typeof saved.seenBench === "object") state.seenBench = saved.seenBench;
    if (typeof saved.current === "string") state.current = saved.current;
  }
  completed = !!(meta && meta.completed);
  renderAll();
  var cur = null;
  if (state.current) activeSeries().forEach(function (s) { s.points.forEach(function (p) { if (p.key === state.current) cur = p; }); });
  if (cur) showPoint(cur, false); else { state.current = null; resetDetail(); }
  persist();
}
if (window.Lens) { renderAll(); Lens.onState(hydrate); }
else { var s0 = null; try { s0 = JSON.parse(localStorage.getItem("ai-2027-inference-prices")); } catch (e) {} hydrate(s0, null); }
</script>
</body>
</html>
