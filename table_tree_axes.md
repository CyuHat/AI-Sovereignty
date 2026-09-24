talbe_tree_axes

I have conducted a deep search to verify the legal structures, data retention policies, and infrastructure origins of each provider, distinguishing between *de facto* European operations and *de jure* protection from extraterritorial laws (like the US CLOUD Act).

### The Sovereignty Matrix

| Category | Options | Distance (Data Flow) | Retention (What they keep) | Jurisdiction (Legal Shield) | Sovereignty Score |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Self-Hosted** | Ollama, LM Studio, vLLM, llama.cpp, SGLang | **Local** (Your machine) | **Zero** (unless you enable history/logs) | **Your Jurisdiction** (Physical control) | 🟢 **Maximum** |
| **2. Full-Stack EU Clouds** | OVHcloud, Scaleway, STACKIT, T Cloud Public, OUTSCALE, Cloud Temple, NumSpot, IONOS, Exoscale, Infomaniak | **EU** (Data stays in EU data centers) | **Configurable** (Most offer "Zero Retention" or strict "No Training" options; check specific SLA) | **EU** (Protected from CLOUD Act; governed by EU courts) | 🟢 **High** |
| **3. GPU Neoclouds** | Verda, Nebius, Nscale, CloudFerro, Berget AI | **EU/UK** (Varies by region selection) | **Variable** (Often zero retention for inference; check training policies) | **Mixed** (Nebius/Verda/CloudFerro: EU; **Berget AI: UK ⚠️**) | 🟡 **Medium-High** |
| **4. Routers & Gateways** | cortecs, TextCortex, Requesty | **EU** (Routing layer in EU) | **Configurable** (Zero Retention modes available) | **EU** (GDPR-native, but *depends on upstream provider*) | 🟡 **Medium** (Risk of upstream leakage) |
| **5. Wrapped Hyperscalers** | S3NS, Bleu, AWS EC, Azure EUD | **EU** (Data physically in EU) | **Variable** (Often retained for model improvement unless opted out) | **US/Global** (Parent company subject to CLOUD Act) | 🔴 **Low** (Sovereignty Washing Risk) |

---

### Detailed Analysis by Axis

#### 1. Distance (Where the data travels)
*   **Local:** Your data never leaves your hardware. This is the only way to guarantee zero network exposure.
*   **Full-Stack EU Clouds:** Data travels to EU-owned data centers (e.g., OVH in France, STACKIT in Germany). No third-country transfer occurs at the primary vendor level.
*   **Neoclouds:** Most (Nebius, Verda, Nscale) operate in the EU (Netherlands, Finland, Norway). **Berget AI** is flagged as UK jurisdiction, which is post-Brexit and technically a "third country" for GDPR purposes, though often treated similarly for practical sovereignty.
*   **Routers:** The routing layer is in the EU (e.g., Requesty in Frankfurt), but the *inference* happens at the upstream provider. If you route to a US model via a European router, the data still crosses borders to the US model provider.
*   **Wrapped Hyperscalers:** Data stays in EU regions, but the control plane often has global dependencies.

#### 2. Retention (What is kept and used for training)
*   **Self-Hosted:** You define the rules. By default, local models do not train on your prompts unless you explicitly configure fine-tuning loops.
*   **Full-Stack EU Clouds:** Providers like **OVHcloud**, **Scaleway**, and **Infomaniak** explicitly advertise "Zero Data Retention" and "No Training on Prompts" for their AI endpoints. However, always verify the specific API endpoint terms.
*   **Routers:** **Requesty** and **TextCortex** offer "Zero Data Retention" modes where prompts are not stored. **cortecs** acts as a processor but authorizes dynamic selection of upstream providers; if you select a provider that trains on data, the router cannot stop it.
*   **Wrapped Hyperscalers:** High risk. **AWS** and **Azure** often retain data for service improvement unless specific "zero retention" configurations are enabled (which may not apply to all models). **S3NS** (Thales/Google) claims strict controls but relies on Google's underlying infrastructure.

#### 3. Jurisdiction (Who holds the legal keys)
*   **Local:** You hold the keys. No foreign government can compel access remotely.
*   **Full-Stack EU Clouds:** These are incorporated under EU law (France, Germany, Switzerland). They are **immune to the US CLOUD Act** because their parent companies are not US entities. This is the critical differentiator for Airbus and other enterprises.
*   **Neoclouds:** **Nebius** (Dutch), **Verda** (Finnish), and **Nscale** (Norwegian/UK) are generally safe from US extraterritoriality, provided they have no US parentage.
*   **Routers:** The router itself is safe (EU law), but the *upstream* provider dictates the final jurisdiction. If you route to **Amazon Bedrock** via **cortecs**, Amazon still holds the data under US law.
*   **Wrapped Hyperscalers:** **Critical Risk.**
    *   **AWS European Sovereign Cloud:** Operated by a German subsidiary, but ultimately owned by **Amazon.com Inc. (USA)**. Legal experts confirm the CLOUD Act still applies to the parent company.
    *   **Azure EU Data Boundary:** Microsoft remains a US entity.
    *   **S3NS:** A partnership between **Thales (EU)** and **Google (USA)**. While SecNumCloud qualified, the infrastructure is Google-derived. Legal scholars argue the US parent retains ultimate control.

---

### Key Findings for Your Presentation

1.  **The "Sovereignty Washing" Trap:** The most dangerous category is **#5 (Wrapped Hyperscalers)**. Providers like AWS European Sovereign Cloud and S3NS offer *physical* data residency in Europe but fail the *legal* test. As noted in your abstract, "Ultimately has to listen to what the US government expects."
2.  **The Router Ambiguity:** **#4 (Routers)** like cortecs are excellent for *management* and *GDPR compliance* (acting as a single Data Processor), but they do not solve the *model origin* problem. If you route to a US model, you are still under US jurisdiction.
3.  **The True Sovereign Choice:** **#2 (Full-Stack EU Clouds)** and **#1 (Self-Hosted)** are the only options that satisfy all three axes simultaneously.
    *   **Airbus Migration:** The move from AWS to Scaleway was driven precisely by the inability of AWS to guarantee protection from the CLOUD Act, despite its "Sovereign Cloud" branding.
4.  **The "Local" Myth Debunked:** As highlighted in your Part 3, self-hosting is no longer a performance compromise. With tools like **vLLM** and **llama.cpp**, local models are now production-grade, making **#1** a viable option for many, not just hobbyists.

### Recommended Visual for the Talk
A **concentric circle diagram** (as planned in Part 2) works perfectly here:
*   **Center (Inner Circle):** Self-Hosted (Maximum Sovereignty).
*   **Middle Ring:** Full-Stack EU Clouds (High Sovereignty).
*   **Outer Ring:** Routers & Neoclouds (Medium Sovereignty - depends on configuration).
*   **Outside the Circle:** Wrapped Hyperscalers (Low Sovereignty - CLOUD Act exposure).

Would you like me to generate a **Vega-Lite chart** comparing these categories based on a hypothetical "Sovereignty Score" (0-100) derived from these three axes to visualize the gap between "European-washed" and "True Sovereign" options?