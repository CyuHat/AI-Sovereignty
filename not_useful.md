
## You Made It Past the Hard Part

Part 3 gave you the good news: open models now match frontier models, and you can run them yourself.

Most of you won't. Tonight, anyway.

So you need someone else's computer. And everyone selling one has
discovered the same magic word.

> **"sovereign"**

::: {.fragment}
Let's learn to make sellers prove it.
:::

::: {.notes}
Timing: 30 seconds. Bridge from Part 3 (local is no longer a compromise) to Part 4 (choosing a hosted provider). Tone shift: this is the defensive part of the talk, the "buyer beware" section. The word sovereign has become a marketing asset precisely because it has no legal definition in most sales contexts. Anyone can write it on a homepage. The goal of this section is to give the audience a repeatable method to sort the real offers from the decorated ones. Announce the shape: first we fix the vocabulary (because sloppy vocabulary is what sovereignty washing exploits), then a real scoreboard with published scores, then three case studies of pseudo-European offers, and finally a checklist you can use on Monday morning.
:::

## First Question: What Do You Actually Want?

"Sovereignty" hides five different wishes. People say the word and mean
very different things:

::: {.fragment}
**Residency.** The bytes stop inside the EU.
:::

::: {.fragment}
**Jurisdiction.** No Washington subpoena can reach the staff who hold the keys.
:::

::: {.fragment}
**Operational control.** Nobody abroad can switch the service off.
:::

::: {.fragment}
**Technological autonomy.** The stack itself is European or open.
:::

::: {.fragment}
**Retention.** Nothing about you is kept, logged, or learned from.
:::

::: {.fragment}
If you cannot say which of the five you need, you cannot detect when a
seller quietly swaps one for another.
:::

::: {.notes}
Timing: 1 minute. This is the definitional slide the audience needed before the vocabulary gets weaponized by case studies later. Walk through the five meanings with quick examples: Residency = a server in Frankfurt, but a US parent company (that's AWS EUSC, slide later). Jurisdiction = CLOUD Act exposure, the thorniest one. Operational control = can the service survive a divorce from a US vendor? (Gaia-X style concern, also the EU Cloud Sovereignty Framework's "digital resilience" SEAL-3 language). Technological autonomy = whose code actually runs it (S3NS is French but runs Google's stack). Retention = what providers do with your prompts afterward, ties back to the hook of the talk (training defaults from Part 0).

Key rhetorical move: ask the room "hands up if you have used the word sovereign in the last month, and know which of the five you meant". Most will not. That discomfort is the point: the word is doing sales work, not analysis work. Sellers exploit exactly this ambiguity, offering residency when you wanted jurisdiction, and calling both sovereignty.

The five wishes decompose the three axes from Part 2 (distance, retention, jurisdiction): residency and jurisdiction carve up distance and legal reach, operational and technological autonomy are refinements of jurisdiction and control, retention is the same axis as in Part 2. Say this link out loud, it stitches the talk together.
:::

## From a Mental Map to a Measurement Instrument

Part 2 gave us **three lenses**: legal, operational, technological.

The seller you will meet uses none of them. You need a vocabulary
**both of you share**.

::: {.fragment}
In October 2025, the European Commission published exactly that: the
**Cloud Sovereignty Framework**. Eight objectives, scored from **SEAL-0
to SEAL-4**, combined into one weighted Sovereignty Score.
:::

::: {.fragment}
Why this one? Because it is the only definition of "sovereign" that has
already **decided real money**: a 180 million euro tender in April 2026.
:::

::: {.notes}
Timing: 1 minute 15 seconds. Transition logic the user asked for: Part 2's three lenses are a thinking tool for YOU, but sellers do not answer to your private taxonomy. Procurement professionals solved this problem the classic way: a shared, published rubric. The European Commission's Cloud Sovereignty Framework (version 1.2.1, October 2025, Directorate-General for Digital Services) is that rubric. It defines eight Sovereignty Objectives, each scored on SEAL levels (Sovereignty Effectiveness Assurance Level, 0 to 4), aggregated with published weights into a Sovereignty Score usable as an award criterion in tenders.

Why we use the official framework in this part: (1) it is public and auditable, so a vendor cannot dispute the questions; (2) it is multidimensional, which forces the legal/operational/technological split our three lenses demanded; (3) and uniquely, it has been applied to real contracts, so we have actual scores to show (next slides). It builds on CIGREF's Trusted Cloud referential, Gaia-X policy rules, ENISA/NIS2/DORA, France's Cloud de Confiance, Germany's Souveräner Cloud.

Critiques worth knowing (mention briefly if asked in Q&A, they strengthen your credibility): CISPE (Cloud Infrastructure Services Providers in Europe) argued the framework is too vague to be truly binding and that the scoring can disadvantage European players; the Chamber of Progress argued SOV-5's heavy weight (supply chain, 20%) favors large incumbents and makes no distinction between allies and adversaries for supply dependencies. Sources: HarfangLab interview with Pierre-Louis Mauratille, https://harfanglab.io/blog/strategy/the-cloud-sovereignty-framework-a-first-step-toward-assessing-cloud-sovereignty ; Chamber of Progress, https://progresschamber.org/insights/the-eus-sovereignty-calculator-needs-an-upgrade

Framework references: European Commission, Cloud Sovereignty Framework v1.2.1, https://commission.europa.eu/document/download/09579818-64a6-4dd5-9577-446ab6219113_en ; implementation guidance with 48 criteria published 1 June 2026 (covered by e.g. SUSE's self-assessment tool, https://www.suse.com/cloud-sovereignty-framework-assessment?lng=en).
:::

## What the Score Actually Weighs

Not all sovereignty goals weigh the same. The Commission decided:

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "width": "container",
  "title": {
    "text": "Objective Weights in the Sovereignty Score",
    "subtitle": "Supply chain (SOV-5) weighs the most at 20%; environmental sustainability the least at 5%"
  },
  "data": {
    "values": [
      {"objective": "Supply chain (SOV-5)", "weight": 20},
      {"objective": "Strategic (SOV-1)", "weight": 15},
      {"objective": "Operational (SOV-4)", "weight": 15},
      {"objective": "Technology (SOV-6)", "weight": 15},
      {"objective": "Legal & jurisdictional (SOV-2)", "weight": 10},
      {"objective": "Data & AI (SOV-3)", "weight": 10},
      {"objective": "Security & compliance (SOV-7)", "weight": 10},
      {"objective": "Environmental (SOV-8)", "weight": 5}
    ]
  },
  "mark": "bar",
  "encoding": {
    "y": {"field": "objective", "type": "nominal", "sort": "-x", "title": null},
    "x": {"field": "weight", "type": "quantitative", "title": "Weight in the score (%)"}
  }
}
```

::: {.fragment}
Notice the heaviest weight: **where does the machinery come from?**

Not where the flag on the website comes from.
:::

::: {.notes}
Timing: 45 seconds. Data points: weights per the framework implementation guidance (1 June 2026, 48 criteria): SOV-5 Supply Chain 20%; SOV-1 Strategic 15%; SOV-4 Operational 15%; SOV-6 Technology 15%; SOV-2 Legal and jurisdictional 10%; SOV-3 Data and AI 10%; SOV-7 Security and compliance 10%; SOV-8 Environmental 5%. Confirmed by two independent explainers: Nlighten, https://www.nlighten.com/en/blog/the-eu-cloud-sovereignty-framework-explained-seal-levels-sovereignty-objectives-and-the-sovereignty-score ; SUSE self-assessment, https://www.suse.com/cloud-sovereignty-framework-assessment?lng=en

Talking points: the weighting reveals the Commission's actual priorities. Supply chain at 20% means: where is the hardware manufactured, where is the software written, how dependent are you on non-EU vendors. This is exactly the dimension sovereignty washers decorate. Strategic, operational and technology at 15% each are the "can you be switched off or locked in" objectives. Legal at only 10% surprises people; the stated rationale is that the procurement procedure itself already contains legal safeguards, so the score does not need to double-count them (framework document, section on weights).

Delivery tip: pause on the top bar. "Where the machinery comes from. Remember that bar, because the next case study fails exactly there."
:::

## The Map of Your Options

![](images/part4-map.png)

Five territories, from safest to most decorated.

::: {.notes}
Timing: 1 minute. The generated conceptual image, tree of five zones from the laptop upward. Use it as a visual anchor, then walk the next slide's textual version which is the accessible and printable equivalent. Keep the narration here short and let the image breathe: "everything at the bottom is yours. Every step up is a promise you need to check."

If the projection setup renders images poorly, jump straight to the next slide's textual map; it carries the same content in native revealjs layout. That slide is also the version to distribute as handout.
:::
