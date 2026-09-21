### 📋 Executive Summary of Review

| Aspect | Status | Recommendation |
| :--- | :--- | :--- |
| **Narrative Arc** | ✅ Strong | Tighten the callback loop between the "deleted sentence" and the "deleted clause" in Nebius. |
| **Factual Accuracy** | ⚠️ Needs Polish | Verify specific dates for the Navier-Stokes controversy and the Nebius privacy policy change. Clarify the "Cortecs" vs "Cortecss" confusion. |
| **Technical Depth** | ✅ Good | Add a specific visual for the "Confidential Computing" stack in Part 5 to make it less abstract. |
| **Audience Engagement** | ✅ High | The "Raccoon" story is perfect. Ensure the "Jevons Paradox" joke lands correctly. |
| **Visual Strategy** | ⚠️ Mixed | Replace the generic "Concentric Circles" description with a specific Vega-Lite or SVG instruction. |
| **Missing Elements** | ❌ Missing | A clear "What to do tomorrow" slide for non-technical users. A specific mention of the "Sleeper Agent" risk in Part 5. |

---

### 🔍 Detailed Review & Instructions

#### 0. General ideas

- We need a slides at the beginning and at the harness part that talk about vendor lockin, where providers like Claude and OpenAI want to contrôle the 3 things for an AI execution: the inference, the tool and the context/data. Then explain that now we can control all 3 of them without much compromise. At the end gives examples of combinaisons of Tools for the 3 elements.

- If the Navier-Stoke example is not in the text, place it. It should also be linked to the idea that just accepting the fact that vendor won't use your data without your permission is not a sure bet. Make it also clear that the user own the data produced but not surely the data sended. Also let's look for data policies in major closed AI company to be presented before (OpenAI, Anthropic, DeepMind, XAI, etc.).  

#### 1. The Hook (Part 0) & The "Deleted Sentence" Loop
*   **Current State:** You open with the OpenAI sentence disappearing. You close with the Nebius sentence disappearing. This is excellent symmetry.
*   **Issue:** The Nebius slide mentions a "September 15, 2026" update. The Wikipedia file on Navier-Stokes mentions a "September 8, 2026" event. Ensure these dates are consistent in your timeline. If the Navier-Stokes leak happened *before* the Nebius policy change, it strengthens the argument that "defaults are changing while you sleep."
*   **Instruction:**
    *   **Verify Dates:** Cross-reference the Nebius privacy policy archive date with the Navier-Stokes announcement. If the policy change happened *after* the leak, explicitly state: "While the world was arguing about who solved Navier-Stokes, Nebius quietly deleted the clause that guaranteed your data stayed where you put it."
    *   **Clarify "Cortecss":** Your `AI_EU_Sovereign_Solution.md` file explicitly states: *"I could not find any AI provider named Cortecss AI... The only match is CoRTecS (cortecs.unistra.fr)... a scientific services portal."* However, your presentation uses **cortecs.ai** as a major case study.
    *   **Action:** **Remove any reference to "Cortecss".** Stick strictly to **cortecs.ai** (the Vienna-based router). In the speaker notes, add a small footnote: *"Note: Do not confuse with CoRTecS (University of Strasbourg), which is a research portal. We are talking about cortecs.ai, the LLM router."*

#### 2. Part 2: The Three Axes & The Airbus Case
*   **Current State:** You introduce the three axes (Distance, Retention, Jurisdiction) and use Airbus as the proof.
*   **Issue:** The "Concentric Circles" visual is described but not rendered. The audience needs to *see* the map.
*   **Instruction:**
    *   **Render the Map:** Instead of describing the concentric circles, generate a **Vega-Lite** chart or a clear **SVG** diagram for the slide.
    *   **Refine the Airbus Narrative:** The `New_sources.md` file confirms the Airbus move was a *scored procurement criterion* (15% of the score). Make sure this number is on the slide. It proves sovereignty is a *business metric*, not just a philosophy.
    *   **Add the "One Fine, Zero Survivors" Visual:** The `New_sources.md` file has a great Vega-Lite chart idea for GDPR fines. **Insert this chart** right after the Airbus slide to visually demonstrate why regulators failed.

#### 3. Part 3: Benchmarks & The "Horse Cart" Joke
*   **Current State:** You have excellent data on the 5.4% gap and the 350x cost drop.
*   **Issue:** The "Horse Cart at a Formula 1 race" joke is powerful, but the transition to "The race has flattened" needs to be sharper.
*   **Instruction:**
    *   **Update the Joke:** "Three years ago, I taught local-model courses. People looked at the tiny, slow model, then at GPT, then at me, like I'd sold them a horse cart at a Formula 1 race. **Today, the horse cart is lapping the field at 90% of the lap time.**"
    *   **Add the "Escalator" Visual:** Use the `Benchmark.md` data to create a **line chart** showing the "Intelligence Floor" rising over time (OpenTeams' insight: "Rock bottom today = frontier 7 months ago"). This visualizes the "escalator" effect better than words.

#### 4. Part 4: Sovereignty Washing & The Nebius Case
*   **Current State:** You have great case studies (cortecs, S3NS, AWS, Nebius).
*   **Issue:** The Nebius case is the "slow drift" pattern. It needs to feel like a betrayal, not just a business change.
*   **Instruction:**
    *   **Highlight the "Global" Region:** Emphasize that Nebius moved from "Region: EU" to "Region: Global" where the location is "decided dynamically... without notice." This is the exact mechanism of the "sleepwalking" from Part 0.
    *   **Add the "Sleeper Agent" Warning:** The `Sovereign_AI_Research.md` file mentions "Sleeper Agents" (models trained to be malicious only under specific triggers). Add a brief bullet point in Part 4: *"Even if the data stays in Europe, the model itself might have been trained with a 'sleeper' trigger that activates only for US users. Sovereignty isn't just about location; it's about the model's DNA."*

#### 5. Part 5: Agents, Sandboxes & The "Raccoon"
*   **Current State:** The "Raccoon" story is the highlight. The legal punchline (no criminal intent) is strong.
*   **Issue:** The "Confidential Computing" stack is mentioned but feels abstract. The audience needs to understand *why* a Docker container isn't enough.
*   **Instruction:**
    *   **Visualize the Stack:** Create a **layered diagram** (or Vega-Lite bar chart) showing the "Trust Boundary" shrinking from "Cloud Provider" -> "Container" -> "CPU TEE" -> "GPU TEE". Label the "Docker" layer as "Theater" and the "TEE" layer as "Physics".
    *   **Clarify the "Raccoon" Source:** You mention "Jason Croucher" and "Filip Hric". Ensure these names are cited correctly in the notes. The story is powerful; don't let it get bogged down in attribution.
    *   **Add the "No Lawsuit" Quote:** The `New_sources.md` file has the perfect quote: *"No lawsuits have been filed... an autonomous AI agent can't form criminal intent."* Put this in **bold** on the slide.

#### 6. Part 6: Conclusion & Call to Action
*   **Current State:** You recap the map and end with "Don't use the default."
*   **Issue:** The "What to do tomorrow" slide is a bit generic.
*   **Instruction:**
    *   **Split the Audience:** Create a specific slide with two columns:
        *   **Non-Technical:** "1. Turn off training toggles. 2. Choose a provider with SecNumCloud/SEAL-3. 3. Ask: 'Who owns the parent?'"
        *   **Technical:** "1. Self-host with Ollama/vLLM. 2. Use MicroVMs (Firecracker). 3. Remove `.env` files from disk."
    *   **Final Line:** Keep the "Don't use the default. Use what suits *you*." line. It's perfect.

---

### 🛠️ Specific Changes to Implement

#### A. Content Corrections
1.  **Fix "Cortecss"**: Change all instances to **cortecs.ai**. Add a speaker note clarifying the distinction from the University of Strasbourg's CoRTecS.
2.  **Verify Nebius Dates**: Ensure the "September 15, 2026" policy change is accurate relative to the Navier-Stokes event (Sept 8). If the policy change came *after*, emphasize the timing: "While the world argued about Navier-Stokes, the default flipped again."
3.  **Add "Sleeper Agent" Risk**: Insert a bullet point in Part 4 about the risk of models trained with geopolitical triggers (from `Sovereign_AI_Research.md`).

#### B. Visual Enhancements
4.  **Generate the "Concentric Circles" Map**: Create a Vega-Lite chart or SVG for Part 2 showing the three rings (Local, Hosted Open-Weight, Global).
5.  **Generate the "GDPR Fine Failure" Chart**: Use the Vega-Lite code from `New_sources.md` to visualize the annulled fine vs. non-compliant fines.
6.  **Generate the "Escalator of Intelligence" Chart**: Create a line chart for Part 3 showing the "Floor" of intelligence rising over time.
7.  **Generate the "Trust Boundary" Diagram**: Create a layered visualization for Part 5 showing Docker (Theater) vs. TEE (Physics).

#### C. Narrative Tweaks
8.  **Sharpen the "Horse Cart" Joke**: Update the punchline to "The horse cart is now lapping at 90%."
9.  **Strengthen the Airbus Story**: Explicitly mention the "15% scored criterion" for CLOUD Act protection.
10. **Clarify the "No Lawsuit" Legal Point**: Ensure the slide explicitly states that the Computer Fraud and Abuse Act (CFAA) requires *human intent*.

#### D. Missing Slides
11. **Add "What to do Tomorrow" Slide**: Split into Non-Technical and Technical actions.
12. **Add "Sleeper Agent" Warning Slide**: Briefly explain the risk of models with hidden geopolitical triggers.