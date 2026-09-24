# Speaker Notes

---

## March 2023, Samsung, Hwaseong

Samsung Semiconductor lifts its internal ChatGPT ban on March 11, 2023.

Three weeks, three separate leaks. Division: Device Solutions, Hwaseong, South Korea. Normal people, normal shortcuts, trying to work faster.

The data lands on OpenAI servers in the US. No NDA. No way to recall it. Disciplinary investigations were launched into all three engineers.

VISUAL: optional small screenshot of the Bloomberg headline (May 2, 2023) as a card in the corner. Adds authenticity, no clutter.

The bug got fixed. The company's next chip architecture got a **new co-author**.

Deliver the co-author line deadpan. Let it land. Do not smile. The audience will get it a half-second later, that is the desired effect.

Then the punchline of the story: Samsung, one of the largest companies on earth, bans generative AI entirely, effective May 1. Open door to closed door in under a month.

---

## They weren't careless

Full stop. Slow down dramatically here. This is the thesis, delivered before the word "sovereignty" exists in the room.

Everything in the next forty minutes clicks back to these four minutes: the deleted sentence, the buried toggle, the ticked checkbox, the pasted source code.

Then say the transition line out loud: "So how did we get here?" Advance into Part 1.

---

## October 2025: Stanford study

Someone finally sat down and read all the policies. Stanford HAI, October 2025. All six companies. That is roughly ninety percent of the US chatbot market.

Some retain your data indefinitely. Children's messages mostly stay in the training pile.

Everything was disclosed somewhere. Buried in a maze of 28 overlapping policy documents, which is a form of hiding in plain sight.

This is not a conspiracy. It is defaults, running quietly at scale. Say that line: "defaults, running quietly at scale."

VISUAL: the six company logos in two rows of three instead of the text line, if you prefer. The logos hit harder and they are all named in the Stanford HAI piece.

---

## Axis 1: Distance

Simple so far. Everyone in the room gets distance intuitively.
Don't linger, this axis builds trust before the harder ones.

---

## Axis 2: Retention

Emphasize the training case: this is not storage, this is
incorporation. Once your data is in the weights, deletion is
mathematically impossible. There is no uninstall for training.
That is why "we no longer use your chats for training" was
the sentence that mattered so much in Part 0.

---

## Navier-Stokes priority case

NEW MATERIAL, sourced from the Navier-Stokes controversy (Sept 2026).
This story is real, documented on Wikipedia, and involves
one of the two greatest unsolved problems in mathematics.
Even if they don't follow the math, everyone follows betrayal.

---

## Navier-Stokes priority case (continued)

Let the line land. Silence for two beats.
This is the retention axis as current events, not theory.
Callback available in Part 5: it was the same industry-wide
pattern of defaults, just aimed at Clay Research fellows.

Asked directly whether the mathematicians' files had fed the effort,
OpenAI rejected direct access to the files.

But admitted, "in a downplaying manner", that their training data
included material **"derived"** from those Codex sessions.

**The referee read your paper before you submitted it.
Through the pen you used to write it.**

---

## CLOUD Act

Note the direction: this law was written to *help investigations*.
It achieves that by removing the location defense.
The same reach applies to your prompts.

Technical nuance worth one sentence aloud: the CLOUD Act also has a
comity procedure (18 U.S.C. § 2703(h)) allowing providers to challenge
requests that conflict with foreign law. In practice, the burden is on
the provider, and the customer finds out nothing. Say: "There is an
escape valve. It belongs to the provider, not to you."

---

## GDPR

These three laws operate on three different logics. Say them slowly.

**CLOUD Act:** Extraterritorial reach. The US government compels data wherever it lives, so long as a US entity touches it. This is a sword held over any provider with a parent in California.

**Chinese Law:** Total domestic control. Data must stay inside China, and the state can demand access anytime. There is no judicial review comparable to US warrants or EU oversight. This is a wall around every interaction inside China.

**EU One-Stop-Shop:** Regulatory arbitrage. A company chooses its lead authority (usually Ireland for Big Tech). If that authority is slow, weak, or friendly to US interests, the entire EU's protection weakens. The Italian OpenAI fine annulment proved this: Italy lost because Ireland was the designated lead.

The takeaway for the audience: hosting in Europe does not protect you from the CLOUD Act if the parent is American. Hosting in China exposes you to total state access. Hosting in the EU protects you only until the company chooses a different lead regulator.

This is why Part 3's argument matters: sovereignty cannot be outsourced to law. You have to build it into the architecture itself. That is what justifies the concentric circles map and the local-first strategy.

---

## Three axes, one map

Transition slide. Slow down here, this is where the parts converge.
The diagram appears.

Distance, retention, jurisdiction. Each can be good or bad
independently. But you rarely optimize all three separately.

They correlate, roughly

**Innermost: local.** Your machine. Distance zero.
Retention is your choice, because you delete it.
Jurisdiction is wherever you already are.
The only axis left is the model itself.

**Middle ring: hosted open-weight.** A European operator you vetted.
One hop of distance, contractual retention, certifications
binding ownership.

**Outermost ring: global inference platforms.**
US, Chinese, or mixed-jurisdiction platforms, or EU fronts
routing back to them. Physical location may even look European.
The distinguishing marks: an American or Chinese parent
reachable by its home law, an EU promise with no ownership
constraint behind it, retention terms written by the party
that benefits from the data. It can be fine. It cannot be assumed.

Outer ring phrasing kept per user's direction: real distinction
between rings is legal control and retention incentives, not
map color. Emphasize the last sentence: not forbidden, just
never automatic.

---

## Why "local" is no longer a compromise

Opening line for this section (say after transitioning from Part 2's three axes):

"Three years ago, running a local model meant accepting a million-fold performance drop. That trade-off is gone."

Pause. Let that sink in. Then advance to the next slide.

This entire part is the turn from fear to empowerment — the moment where sovereignty becomes a choice rather than a compromise.

---

## The gap today (4 months)

The headline numbers. Say them out loud. Five-point-four percent is less than one standard deviation on most benchmarks — basically noise.

Four months lag. For most products, that's shorter than your planning cycle to launch.

And the price gap is where this gets interesting: 5.7× cheaper for 3.6 points less intelligence. That's not a compromise anymore. That's an arbitrage opportunity.

---

## What "four months behind" actually means

This is the most important frame for your audience. The old intuition is wrong. People remember the 2023-2024 gap where local models were comically bad.

The gap has shrunk from 17.5 points on MMLU (Stanford AI Index, May 2023) to effectively zero on knowledge benchmarks today.

Say the quote slowly. Eight ECI points = one minor version bump. Not a generation leap. A patch update.

This is the escalator. Intelligence is moving so fast that "rock bottom" today is frontier from seven months ago.

Which means: when you choose local/self-hosted, you're not choosing yesterday's model. You're choosing last year's frontier. And that's still good enough for 85–90% of use cases.

This kills the "horse cart at a Formula 1 race" joke from the past — because now the horse cart is lapping at 90% lap time.

---

## Cheap (1)

This chart tells the real story. On knowledge and saturated benchmarks (MMLU, GPQA, math), open weights have caught up or passed.

The residual gap lives in agentic tool use and frontier abstraction (SWE-bench scaffolds, ARC-AGI-2, Humanity's Last Exam).

Crucially: those gaps are partly scaffolding artifacts. "Scores depend heavily on the agentic scaffold" — iternal.ai.

So for most practical workloads? The gap is five percent. The price gap is five times. Do the math.

---

## Scale milestones (mid-2026)

These three milestones tell the whole story of what's possible now.

Kimi K3: 2.8 trillion parameters. Yes, trillion. Released open weights. The largest open model ever built. And it's not a fluke — five independent families simultaneously reached frontier quality.

Qwen3.6-27B: You can run this on a single consumer GPU and it beats a model twenty times bigger from two months ago. The scaling laws are working, and they're working for everyone now.

gpt-oss-120b: This is the meta point. The frontier labs themselves — the ones selling API access — are publishing models you can run locally. They know the game is shifting.

Say the "five independent families" line. That's the structural argument. This isn't a one-off anomaly.

---

## Scale milestones (mid-2026) — economics

The economics. This is where sovereignty stops being philosophical and starts being mathematical.

Three hundred fifty times cheaper over two years. When the intelligence itself costs pennies, the differentiating decision is no longer capability — it's where the data goes, who holds jurisdiction, and whether you can verify it.

That's the bridge from Part 3 to Part 4. Intelligence is commoditizing faster than it's improving. The expensive thing you're paying for is no longer the model. It's the data you fed it.

---

## Scale milestones (mid-2026) — punchline

This is the punchline. One dollar per task becoming one cent per task within a calendar year.

Which means the sovereignty question flips: when intelligence is this cheap, why would you ever send your data to a US server? The marginal cost of running it yourself is now lower than the marginal cost of sending it elsewhere.

Say "commoditization" on purpose. It's an economic term. Intelligence is being commoditized. When something is a commodity, the only way to differentiate is through something else — like data jurisdiction, or auditability, or trust.

---

## Limitations

Credibility comes from honesty. Include these caveats. They actually strengthen your argument.

Point 1: Cost per token is misleading. You need cost per successful task. BenchLM makes this explicit — they exclude open-weight models from "score per dollar" because infrastructure costs vary.

Point 2: The test set problem. Public benchmarks can be overfit. Private test sets (like AutomationBench-AA) are harder and give different rankings.

Point 3: Be clear about where the gap still exists. Agentic workflows. Hard abstraction. Don't oversell.

Say these quickly. Three seconds each. Then pivot to: "But even with these caveats, the baseline has shifted. Local is viable now. It wasn't in 2023. It is now."

---

## Wrapped hyperscalers

Timing: 1 minute 15 seconds. This is the taxonomy tree from the visual priority list, in native layout so it can be printed, read by screen readers, and translated. Zone content (from the project research panorama, September 2026):

Zone 1: vLLM (production throughput; commercialized by Inferact, which raised $150M in 2026), Ollama (easiest, `ollama pull`), llama.cpp (CPU and edge, GGUF format), plus SGLang, LM Studio, Open WebUI. Air-gap capable. Sovereign but hard work.

Zone 2: OVHcloud (FR, SecNumCloud 3.2, broadest catalog), Scaleway (FR, Iliad, EC SEAL-3, hosts Mistral/Llama/Qwen via OpenAI-compatible API), STACKIT (DE, Schwarz Group, BSI C5), T Cloud Public (DE, Deutsche Telekom), OUTSCALE (FR, Dassault, SecNumCloud since 2019, Mistral partner), Cloud Temple (FR, SecNumCloud 3.2, runs an LLM-as-a-Service with 36 open models and publishes price and CO2 per million tokens), NumSpot (FR consortium of 8, SecNumCloud IaaS since September 2026), IONOS (DE), Exoscale and Infomaniak (CH, Swiss law, EU adequacy).

Zone 3: Verda (FI, ex-DataCrunch, over $100M ARR, sovereign LLMaaS with Siili), Nebius (NL, ex-Yandex spinout, Nasdaq-listed, 750+ MW, gets its own slide later), Nscale (UK, outside the EU regulatory perimeter), CloudFerro (PL, geospatial, ESA/Copernicus), Berget AI (SE, open-model API).

Zone 4: cortecs (Vienna, gets its own slide), TextCortex (DE, EU-hosted router serving US frontier models through one EU API), Requesty (Frankfurt gateway for Mistral, zero retention).

Zone 5: S3NS, Bleu (own slides), AWS European Sovereign Cloud, Azure EU Data Boundary, Oracle EU Sovereign.

One-liner to remember: "the zones are sorted by how many documents you must check before trusting them".

---

## What is data sovereignty?

Give one sentence per dial, no more. The detail comes next.

---

## Main takeaway

> Don't **only** use the **default option**.

> Use what suits **you** the best.
