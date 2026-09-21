## 🎯 The Headline Numbers (Slide-Ready)

```card-row
[
  { "type": "metric", "title": "Open vs closed intelligence gap", "value": "5.4%", "delta": "59.7 vs 63.1 across 270 models (olud.ai, Aug 2026)", "direction": "up" },
  { "type": "metric", "title": "Lag of best open model", "value": "~4 months", "delta": "≈ one minor version — 'like GPT-5 vs GPT-5.5' (Epoch AI)", "direction": "flat" },
  { "type": "metric", "title": "Price gap", "value": "3x–5.7x", "delta": "GLM 5.3: $4.40/M tok vs Claude Opus 5: $25/M", "direction": "up" },
  { "type": "metric", "title": "Open models in top 10", "value": "5 of 10", "delta": "Artificial Analysis intelligence index", "direction": "up" }
]
```

**The killer soundbite** for your talk, from Epoch AI via DEV Community:
> *"'Four months behind' means one minor version, not one era."* — and the Doubleword trendline extrapolation predicts the gap reaching **zero around December 3, 2026** (which you can wryly note is roughly your talk date — "buy your RTX 5090 futures now").

---

## 📊 Benchmark-by-Benchmark (mid-2026)

| Benchmark | Best Closed | Best Open | Gap | Status |
|-----------|-------------|-----------|-----|--------|
| **MMLU-Pro** | GPT-5.5 (90.1%) | DeepSeek V4-Pro (86.3%) | ~4 pts | Closed |
| **MMLU** | Gemini 3 Pro (~92%) | Kimi K2.5 (92.0%) | 0 pts | **Tied** |
| **HumanEval** | GPT-5.3 Codex (~96%) | Kimi K2.5 (99.0%) | — | **Open leads** |
| **AIME 2025** | GPT-5.5 (95.2%) | DeepSeek V4-Pro (88.7%); Step-3.5-Flash 97.3 | — | **Open leads** (Step-3.5) |
| **GPQA Diamond** | Gemini 3.1 Pro (88.2%) | Qwen 3.5-397B (88.4%) | — | **Open leads** |
| **MATH-500** | OpenAI o3 (~97%) | Kimi K2.5 (98.0%) | — | **Open leads** |
| **SWE-bench Verified** | Claude Fable 5 (95.0%) | MiniMax M2.5 (80.2%) | ~15 pts | Open |
| **ARC-AGI-2** | Gemini 3.1 Pro (77.1%) | DeepSeek V4-Pro (59.8%) | ~17 pts | Open |
| **Humanity's Last Exam** | 60–64.7% | 40–52% | ~15 pts | Open |

Sources: localaimaster.com, iternal.ai, LetsDataScience, WhatLLM.org, clickrank.ai

**The narrative structure this gives you:** on *knowledge and saturated benchmarks* (MMLU, HumanEval, math) open weights have **caught up or passed** closed models. The residual gap lives in *agentic tool use and frontier abstraction* (SWE-bench scaffolds, ARC-AGI-2, WebArena/OSWorld) — which, importantly for your talk, is partly a **scaffolding/test-harness artifact** ("Scores depend heavily on the agentic scaffold" — iternal.ai).

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "width": "container",
  "title": { "text": "Best Open vs Closed Model by Benchmark (2026)", "subtitle": "Gap ranges from 0 on knowledge tasks to ~17 points on ARC-AGI-2 abstract reasoning" },
  "data": {
    "values": [
      { "benchmark": "MMLU(-Pro)", "model": "Closed", "score": 91.0 },
      { "benchmark": "MMLU(-Pro)", "model": "Open", "score": 89.2 },
      { "benchmark": "GPQA Diamond", "model": "Closed", "score": 88.2 },
      { "benchmark": "GPQA Diamond", "model": "Open", "score": 88.4 },
      { "benchmark": "AIME 2025", "model": "Closed", "score": 95.2 },
      { "benchmark": "AIME 2025", "model": "Open", "score": 88.7 },
      { "benchmark": "SWE-bench Verified", "model": "Closed", "score": 95.0 },
      { "benchmark": "SWE-bench Verified", "model": "Open", "score": 80.2 },
      { "benchmark": "ARC-AGI-2", "model": "Closed", "score": 77.1 },
      { "benchmark": "ARC-AGI-2", "model": "Open", "score": 59.8 },
      { "benchmark": "Humanity's Last Exam", "model": "Closed", "score": 62.0 },
      { "benchmark": "Humanity's Last Exam", "model": "Open", "score": 46.0 }
    ]
  },
  "mark": { "type": "bar" },
  "encoding": {
    "column": { "field": "benchmark", "type": "nominal", "title": null, "spacing": 10 },
    "x": { "field": "model", "type": "nominal", "title": null, "axis": { "labels": false } },
    "y": { "field": "score", "type": "quantitative", "title": "Score (%)", "scale": { "domain": [0, 100] } },
    "color": { "field": "model", "type": "nominal", "title": "Model class" }
  }
}
```

*(Values are best-of-table aggregations; open HLE shown as midpoint of the 40–52% cluster.)*

---

## 🗞️ The Story Arc for Part 3

**1. The historical collapse (your "horse cart → Formula 1" pay-off):**
- End of 2023: **17.5-point MMLU gap** between open and closed (aibuzz.blog, citing Stanford AI Index)
- Mid-2026: gap **effectively zero** on knowledge benchmarks

**2. It's structural, not a fluke (LetsDataScience):**
> *"Five independent open model families (DeepSeek, Qwen, Kimi, GLM, Mistral) simultaneously reached frontier quality, making the trend structural rather than a one-off anomaly."*

**3. Scale milestones to wow the audience:**
- **Kimi K3** (weights released July 26, 2026): largest open model ever — **2.8T parameters, 1.56 TB of weights, 1M context** — top aggregate scores among open models
- **Qwen3.6-27B**: a dense 27B model scoring 77.2% that *"runs on a single consumer GPU, beating Alibaba's own 397B flagship from two months earlier"* (computingforgeeks)
- **gpt-oss-120b**: purpose-built for a single 80GB GPU; **gpt-oss-20b** for 16GB laptops — the frontier labs themselves now publish local-runnable models

**4. The economics kicker (matches your sovereignty message):**
- Open-weight models deliver **85–90% of closed performance at 60–84% lower cost** at scale (aibuzz.blog)
- A RAG pipeline: **~$2,275/month on frontier API vs ~$168/month self-hosted** (93% saving)
- GLM 5.3 vs Claude Opus 5: **5.7× less money for 3.6 points less intelligence** (olud.ai)
- DeepSeek V4-Pro: within ~1 point of Claude Opus 4.6 on SWE-bench at **34× less per output token** (aimlapi.com)

**5. The honest caveat (adds credibility):** Open weights *lead nowhere yet* on agentic tool use (WebArena, OSWorld) and hardest abstraction (ARC-AGI-2, HLE) — and Epoch AI warns public benchmarks may flatter open models since public test sets are easier to optimize against.

---

## ⚠️ Conflicts to Resolve Before Quoting

I'm seeing conflicting numbers you should be careful about:

1. **SWE-bench for DeepSeek V4-Pro:** reported as **76.4%, 80.2% (MiniMax), or 80.6%** depending on the source — verify against the official model card before putting a number on a slide.
2. **"Best open model" title rotates monthly:** Kimi K3, DeepSeek V4-Pro, MiniMax M2.5, GLM-5.2, Qwen 3.5 all claim the crown on different indices. Safe phrasing: *"The best open model is disputed — by five different families, every quarter."*
3. **Aggregator naming chaos:** scores for the same benchmark vary with evaluation methodology (e.g., pass@1 vs pass@10 on HumanEval — flagged by Spheron's own benchmark footnotes).

**My recommendation:** anchor your slides on the two most defensible citations — **Epoch AI's "4 months / 8 ECI points"** and the **Stanford AI Index 2026 US-China gap of 2.7%** (down from 17.5–31.6 points in May 2023) — and use specific benchmark numbers only with a footnote to the source table.

---

Would you like me to now (a) draft the full Part 3 chapter with speaker notes using this material, (b) verify a couple of these benchmark numbers against official model cards, or (c) build the visual timeline slide showing the gap collapsing 2023→2026?

## 🎯 Headline Findings

```card-row
[
  { "type": "metric", "title": "Cost drop for GPT-4-level intelligence", "value": "~350x", "delta": "Over the past ~2 years (Artificial Analysis)", "direction": "down" },
  { "type": "metric", "title": "Fixed-capability inflation rate", "value": "1/30th per year", "delta": "Same intelligence costs ~a thirtieth of a year ago (CatalystNeuro)", "direction": "down" },
  { "type": "metric", "title": "Cheapest cost per Intelligence Index task", "value": "$0.01", "delta": "Granite 4.2 3B and GPT-5.6 Luna (low) — AA leaderboard", "direction": "flat" },
  { "type": "metric", "title": "Projected cost of a $1 task", "value": "$0.01", "delta": "By end of 2026 if pace holds (CatalystNeuro)", "direction": "down" }
]
```

**The rhetorical centerpiece for your talk** — from the CatalystNeuro analysis of AA data:
> *"If the pace of the last year holds, the capability that cost a dollar per task at the start of 2026 will cost a cent by the end of it."*

And its sovereignty punchline: **intelligence is being commoditized faster than it's improving.** When the intelligence itself costs pennies, the *differentiating* decision is no longer capability — it's where the data goes, who holds jurisdiction, and whether you can verify it. That's your bridge from Part 3 to Part 4.

---

## 📐 How the Metric Works (So You Can Defend It on Stage)

**Artificial Analysis Intelligence Index (v4.3.2)** aggregates 10 evaluations (GPQA Diamond, Humanity's Last Exam, Terminal-Bench 4.0, SciCode, GDPval-AA, etc.) and publishes alongside it:
- **Cost per Intelligence Index task** — weighted average USD per task, segmented by token type
- **Intelligence vs. cost / speed / latency plots** — the "efficiency frontier"

Per OpenTeams' calibration rule (great for managing audience expectations):
> *"A one-point difference is unlikely to be noticeable by most, while a 5-point gap is substantial."* — and an intelligence score of 50 today equals *the smartest model in the world as of February 2026* (Opus 4.6). **"Rock bottom" in September is frontier from seven months ago.**

---

## 💰 The Numbers That Matter

| Comparison | Figure | Source |
|---|---|---|
| Best open vs closed intelligence | 59.7 vs 63.1 (5.4% gap, 270 models) | olud.ai, Aug 2026 |
| Median open model cost **per point of intelligence** | **$0.0552 per 1M tokens** | olud.ai |
| GLM-5.3 vs Claude Opus 5 | 59.5 pts @ $4.40/M vs 63.1 pts @ $25/M — **5.7× cheaper for 3.6 fewer points** | olud.ai |
| Highest "score per output dollar" (paid APIs) | Qwen3.7 Flash ($0.03 in / $0.13 out per 1M) | BenchLM, Sept 18, 2026 |
| Same workload across 18 major APIs | **$0.018 to $2** (111× spread) | Reddit/analysis, Aug 2026 |
| Cheapest frontier-quality tier entry | Gemini 3.1 Pro at $2.00/M | llm-stats.com |
| Flagship pricing ceiling | Claude Fable 5 ($10/$50), GPT-5.6 Sol ($5/$30) | CloudZero |
| Highest-ranked open model on AA leaderboard | GLM-5.3 (max), II score 45 vs Claude Fable 5.1's 53 | artificialanalysis.ai |
| Kimi K3 (open, 2.8T) overall | #3 on AA Intelligence Index, ahead of every proprietary except Claude Fable 5 and GPT-5.6 Sol | Swfte |
| API price deflation 2025→2026 | ~80% drop; ~350× for GPT-4-level intelligence over 2 years | iternal.ai, Artificial Analysis |

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "width": "container",
  "title": { "text": "Output Price per 1M Tokens, Late 2026", "subtitle": "GLM-5.3 delivers 94% of Claude Opus 5's intelligence at 5.7x lower price" },
  "data": {
    "values": [
      { "model": "Claude Fable 5", "class": "Closed", "price_out": 50 },
      { "model": "GPT-5.6 Sol", "class": "Closed", "price_out": 30 },
      { "model": "Claude Opus 5", "class": "Closed", "price_out": 25 },
      { "model": "Gemini 3.1 Pro", "class": "Closed", "price_out": 2.0 },
      { "model": "GLM-5.3 (open)", "class": "Open weight", "price_out": 4.4 },
      { "model": "Qwen3.7 Flash (open)", "class": "Open weight", "price_out": 0.13 }
    ]
  },
  "mark": { "type": "bar" },
  "encoding": {
    "x": { "field": "price_out", "type": "quantitative", "title": "Output price (USD per 1M tokens)" },
    "y": { "field": "model", "type": "nominal", "sort": "-x", "title": null },
    "color": { "field": "class", "type": "nominal", "title": "Model class" }
  }
}
```

---

## ⚖️ The Honest Caveats (Include These — They Build Credibility)

1. **Cheapest per token ≠ cheapest per task.** CloudZero's warning: *"A budget model that needs three attempts, longer prompts, or human cleanup costs more than a mid-tier model that nails it once."* BenchLM makes the same point (cache hits, retries, task quality). Cost-per-task, not cost-per-token, is the real metric.
2. **Index version churn is severe.** I found the same leaderboard reporting Claude Fable 5.1 at 53 (AA units) while other sources cite closed models at 63.1 (WhatLLM/olud units) — different index versions (v4.1 vs v4.3.x) and different scales. Never mix numbers across index versions on one slide.
3. **Small-model costs hide infrastructure costs.** BenchLM explicitly excludes open-weight models from "score per dollar" tables because *"open-weight model costs depend on your infrastructure"* — self-hosting trades API cost for GPU cost (plus electricity — OpenTeams even modeled local inference at $0.2049/kWh US residential rates).
4. **Benchmarks may flatter open models** (Epoch AI's earlier warning) — token efficiency on public test sets is trainable.
5. **Jevons paradox** (CatalystNeuro's key insight): cheaper intelligence increases total spending on it. Useful as a throwaway joke: *"Economists call it Jevons paradox. CFOs call it Tuesday."*

---

## 🎤 How This Slots Into Part 3

**New slide sequence I'd suggest:**

1. **The gap is 5%. The price gap is 3–5.7×.** (olud.ai headline — almost writes your slide for you)
2. **The escalator**: "Rock-bottom intelligence today = world's smartest model seven months ago" (OpenTeams) → pairs perfectly with your "horse cart at a Formula 1 race" joke — the horse cart is now lapping the field at 90% of lap time.
3. **Cost-per-task collapsing**: $1 → $0.01 within the calendar year (CatalystNeuro) — then pivot: *"When intelligence costs a cent per task, the expensive thing you're paying for is no longer the model. It's the data you fed it."* → transition to Part 4 (choosing providers).

**Best citable anchor sources** (order of defensibility): **Artificial Analysis** (primary, methodology published, used by Jensen Huang at Computex per their pricing page), **olud.ai / WhatLLM** (clear cross-license comparisons), **BenchLM/pricepertoken** (live pricing trackers), **CatalystNeuro** (trend analysis with reproducible dashboard).

Want me to (a) fold all of this — benchmarks + cost-per-intelligence — into the full drafted Part 3 chapter with speaker notes and slide-by-slide layout, or (b) dig one level deeper into the local/self-hosted cost side (GPU amortization, electricity, the "sovereign GPU becomes superior above ~200 developers" breakeven from your confidential-computing file)?