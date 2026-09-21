## ⚠️ First: about "cortecss AI"

I could not find any AI provider named **Cortecss AI** (or "Corcets AI"). The only match is **CoRTecS** (cortecs.unistra.fr), a certified research-technology platform network of the University of Strasbourg, CNRS and INSERM — a scientific services portal, not an AI solution provider. If you have a link, a different spelling (e.g., Cortex?), or where you saw it mentioned, I'll gladly verify and add it. It's possible it's a very small or very new player not yet indexed anywhere.

---

## Step 1 — The existing lists I mined

From my sweep of directories, rankings and community threads (September 2026), these were the most productive sources:

- **Vstorm** – "Sovereign AI in Europe: 5 EU-hosted platforms (2026)"
- **Knowlee** – "EU Agentic AI Platforms Directory 2026" (country-by-country, 8 countries)
- **aimadetools.com** – "European Sovereign AI in 2026: The Complete Landscape" (maps EU-funded projects too)
- **TextCortex** – "6 Best Sovereign AI Platforms in 2026"
- **comparison.cloud & european.cloud** – full EU cloud provider datasets (13+ providers, AI services per provider)
- **france-nuage.fr & foxeet.fr** – French sovereign AI guides (assistants, clouds, on-premise)
- **Ecosystem directories**: europeantechmap.eu, OurSoftware.eu (3,300+ listings), Tech Sovereignty Catalogue (via EU-Startups, Sept 2026)
- **Reddit** – r/france, r/IAfr, r/selfhosted, r/BuyFromEU (which maintains a crowdsourced list of "big tech joint-venture" clouds like S3NS/Bleu)

**New solutions found that I missed previously:** LightOn, OUTSCALE, NumSpot, Cloud Temple, S3NS, Bleu, France Nuage, Elastx, Nebius, Verda (ex-DataCrunch), Nscale, CloudFerro, GLBNXT, Domyn, Bielik, PLLuM, TextCortex, Requesty, OpenEuroLLM, EUROPA consortium, EURO-3C.

---

## Step 2 — What I learned on each

Key findings per newly researched solution:

- **S3NS** (Thales × Google, France): SecNumCloud 3.2 qualified on 17 Dec 2025 — the first ever simultaneous IaaS+CaaS+PaaS qualification (276 requirements, 15 domains, per Futurum). Operates a Google Cloud region *fully controlled by Thales*, staffed exclusively in France, with a quarantine zone validating Google updates. Vertex AI sovereign offering arrives H2 2026 with H100 GPUs. **Controversy:** The Register (April 2026) questioned how it won a share of the EC's €180M sovereign cloud contract given Google's 49% stake; Euractiv notes SecNumCloud 3.2 requires EU HQ and <39% foreign ownership. Competitors (OUTSCALE, Cloud Temple) openly say S3NS, Bleu and AWS Sovereign Cloud "peinent à masquer leur dépendance aux technologies et réglementations extraeuropéennes" (LeMagIT).
- **OUTSCALE** (Dassault Systèmes): SecNumCloud-qualified since 2019 (first French public cloud), full IaaS scope, partner for Mistral sovereign deployment (Dassault/Mistral partnership, Nov 2025).
- **NumSpot** (La Poste, Docaposte, Dassault, Bouygues, Caisse des Dépôts...): obtained SecNumCloud IaaS qualification in Sept 2026; positioning as "hybrid and portable" platform, plus HDS in progress.
- **Cloud Temple**: SecNumCloud 3.2 on multiple offers incl. PaaS OpenShift; runs a **LLM-as-a-Service with 36 models** (Meta, Mistral, IBM, Gemma) with published price and even energy/emissions per million tokens — a rare transparency move.
- **LightOn** (Paris, founded 2016): first European GenAI company listed on Euronext Growth. **Paradigm** platform = sovereign GenAI/API layer on-premise or in sovereign cloud, used by the French Interior and Education ministries, ENS Paris-Saclay, Infocom'94 local authorities. ~€5–10M ARR — small but pure-play sovereign.
- **France Nuage** (Vendée): small French "post-cloud" (built in Rust, open-source, reversible) that **installs and operates open-source LLMs (Mistral, Qwen, Llama) on GPUs in France** for you — plus on-premise turnkey AI boxes. SME/ETI-focused, explicitly anti-CLOUD Act.
- **Nebius** (Amsterdam, Nasdaq-listed): huge GPU capacity (750+ MW, 310MW AI factory in Lappeenranta, Finland; NVIDIA $2B investor), Gold-tier in ClusterMAX rankings. **Caveat:** former Yandex spinout, multi-jurisdiction corporate structure, US-listed, US data centers too — Spheron warns teams with strict CLOUD Act requirements should review its legal structure rather than assume it matches OVHcloud.
- **Verda** (Finland, ex-DataCrunch, renamed Nov 2025): >$100M ARR GPU cloud; launched a **sovereign LLM-as-a-Service with Siili Solutions** (Dec 2025) for EU enterprises/public sector.
- **Nscale** (UK): raised $2B in March 2026, largest European AI infra funding round — but UK-based, not EU.
- **CloudFerro** (Poland): geospatial/satellite-data specialist with government contracts, strong in ESA/Copernicus ecosystems.
- **GLBNXT** (Netherlands): sovereign cloud/AI platform for regulated Dutch markets. **Elastx** (Sweden): small sovereign cloud, public-sector fit.
- **Domyn** (Italy, ex-iGenius): sovereign AI for regulated industries, built the **Colosseum** NVIDIA supercomputer, released open-source "Italia" model, plans an EC-backed open-source frontier model within a year (Economic Times).
- **Bielik & PLLuM** (Poland): open-science national LLM families, free/commercial use, Polish-optimized.
- **OpenEuroLLM / EUROPA consortium** (EU-funded): public-good open-source European LLMs; EUROPA targets a ~400B-parameter, 24-language model with Domyn involvement (Frontier AI Grand Challenge, Feb 2026). **EURO-3C** (Telefónica-led, 70+ orgs, 13 countries, MWC March 2026): federated telco-edge-sovereign-cloud + AI infrastructure.
- **TextCortex** (Germany): an EU-hosted "open-router" giving access to 18+ frontier models (including US ones like GPT-5.5 and Claude) through a single EU API with SOC/ISO certs — interesting hybrid: **European operation, non-European models**. Same category as **Requesty** (Frankfurt gateway for Mistral).
- **Mistral nuance worth flagging:** its sovereign credentials were debated in 2026 when it integrated the Chinese GLM-5.2 model into its platform (summarized by SCMP as "brancher un cerveau d'IA chinois dans une enveloppe européenne") — model-origin sovereignty ≠ infrastructure sovereignty.

---

## Step 3 — Updated master classification

### A. Full-stack European clouds with sovereign AI services (infra + GPU + models/API)

| Solution | How it works | Fully European | Risk / CLOUD Act | Notes for users |
|---|---|---|---|---|
| **Scaleway** (FR, Iliad) | GPU instances (L4→H100), Generative APIs, managed inference, hosts Mistral/Llama/Qwen | ✅ | None; EC SEAL-3, selected for EC €180M contract & ECB digital euro | Best price/perf for EU GPU (~4.8x AWS value per Callista 2026); SecNumCloud in progress; management-plane criticism (US services in console, per Xomnia) |
| **OVHcloud** (FR) | AI Endpoints + GPU + Hosted Private Cloud | ✅ | None; SecNumCloud 3.2 (3 qualifications by Sept 2026) | Broadest catalog + HDS; 2026 price hikes (40–87%) due to RAM costs |
| **OUTSCALE** (FR, Dassault) | SecNumCloud IaaS since 2019, AWS-compatible API, Mistral sovereign deployments | ✅ | None; flagship SecNumCloud | Choice for defense/administration; small catalog vs hyperscalers |
| **Cloud Temple** (FR) | SecNumCloud 3.2 cloud + **LLMaaS (36 open models)** with per-token pricing/CO₂ disclosure | ✅ | None | Rare emissions transparency per Mtok |
| **NumSpot** (FR consortium of 8) | "Portable/hybrid" sovereign platform; SecNumCloud IaaS qualified Sept 2026 | ✅ | None (once fully qualified) | Young (2024); PaaS qualification targeted end-2026; aims at territorial/public buyers |
| **STACKIT** (DE, Schwarz Group) | German/Austrian DCs, AI Model Serving coming | ✅ | None; BSI C5 | Fastest-growing EU-native cloud 2025–2026; retail-group backing |
| **T Cloud Public** (DE, Deutsche Telekom) | Rebranded Open Telekom Cloud (Jan 2026), EU-only staff | ✅ | None; BSI C5, TISAX | Strong public-sector/regulated fit |
| **IONOS Cloud** (DE) | GPU + AI Model Hub | ✅ | None; BSI C5 Type 2 | Mittelstand favorite |
| **Infomaniak** (CH) | Public Cloud with GPU + managed K8s; **Euria** free sovereign chat; OpenAI-compatible AI API, all Swiss | ✅ (Swiss/EFTA, EU adequacy) | None | Switzerland = no CLOUD Act, but no EU-direct CNIL/CEPD recourse; strong ethics/ecology positioning |
| **Exoscale** (CH) | GPU instances, K8s, EU-only footprint | ✅ | None | Cloud-native/transparent pricing |
| **Hetzner** (DE) | Cheap GPU cloud | ✅ | None | Least certified (ISO 27001 only) — fine for startups, weak for public sector |
| **Elastx** (SE) / **GLBNXT** (NL) | Small sovereign clouds for public sector / regulated markets | ✅ | None | Niche, limited scale |
| **CloudFerro** (PL) | Sovereign cloud for earth observation/gov (ESA, Copernicus) | ✅ | None | Specialized in geospatial/satellite data; gov contracts |

### B. GPU "neoclouds" (raw European compute — you bring/run models)

| Solution | How it works | Fully European | Risk | Notes |
|---|---|---|---|---|
| **Nebius** (NL/FI) | Hyperscale GPU fleets, 750+MW EMEA, 310MW AI factory, serverless AI, managed K8s | ⚠️ Partially | **Review carefully**: Nasdaq-listed, ex-Yandex, multi-jurisdiction structure, mixed EU/US DCs | Biggest EU GPU capacity + NVIDIA backing ($2B); fine for startups, questionable for CLOUD-Act-free procurement |
| **Verda** (FI, ex-DataCrunch) | On-demand GPU clusters, serverless inference, autoscaling; + **Siili sovereign LLMaaS** | ✅ | Low | >$100M ARR; no long-term contracts |
| **Nscale** (UK) | Large-scale GPU for training | ⚠️ UK not EU | None vs CLOUD Act, but outside EU regulatory perimeter post-Brexit | $2B raised March 2026; partnered with OpenAI on European hosting — sovereignty is ambiguous (American models on European soil) |
| **Berget AI** (SE) | Open-model API platform + Berget Code (Kimi K2.6, Gemma 4, Mistral Medium 3.5, 256K ctx) on Swedish infra | ✅ | None; GDPR, "no CLOUD Act risks" claimed | €2.1M seed Feb 2026; young/small; startup & public-sector traction |

### C. Hyperscaler-tech "sovereign wrappers" (⚠️ legal edge cases)

| Solution | How it works | Fully European | Risk | Notes |
|---|---|---|---|---|
| **S3NS** (Thales 51% × Google 49%) | Google Cloud tech operated solely by French staff in 3 Paris-region DCs; quarantine zone for Google updates; Vertex AI H2 2026 | ⚠️ Legally yes, technologically no | SecNumCloud 3.2 shields it *legally* (Dec 2025, 276 requirements), but underlying tech is US and Google can advise remotely | Broadest SecNumCloud-qualified catalog (IaaS+CaaS+PaaS first); picked in EC sovereign tender — challenged by The Register; French competitors openly hostile |
| **Bleu** (Orange-Capgemini-Microsoft) | Azure services operated in France | ⚠️ | Still in SecNumCloud qualification (target 2026–2027); US tech dependency | Same model as S3NS; watch ANSSI's final ruling |
| **AWS European Sovereign Cloud** / **Oracle EU Sovereign** / **Microsoft EU Data Boundary** | EU regions/partitioning | ❌ | **CLOUD Act still applies** — US-parented entities | Several sources (DanubeData, Wire.com, Outscale statement) call this "the illusion of control"; Reddit's r/BuyFromEU maintains the full JV list |

### D. Sovereign AI model/API providers (endpoints, no infra management)

| Solution | How it works | Fully European | Risk | Notes |
|---|---|---|---|---|
| **Mistral AI** (FR) | La Plateforme EU API, Le Chat/Vibe, on-prem & Mistral Compute (1GW by 2030, €830M debt raise) | ✅ | None legally; **caveats**: NVIDIA-dependent, sells via Azure/Bedrock/Vertex too, GLM-5.2 (Chinese) integration raised eyebrows | ~$1B ARR May 2026, $21B+ valuation Sept 2026; French & German gov frameworks 2026–2030 |
| **Aleph Alpha** (DE) | PhariaAI, traceable/explainable, sovereign deployment for regulated sectors | ✅ | None | The German "sovereignty-first" reference; pivoted from frontier race to enterprise software |
| **LightOn** (FR) | Paradigm platform (on-prem/private cloud), API to open-weight models, sector SaaS (Edu, Sovereign SaaS document AI) | ✅ | None | Public (Euronext Growth); French Interior & Education ministries, Safran, CNES; small revenue (~$2M TTM) |
| **Domyn** (IT) | Sovereign models (Italia, Domyn-Large), Colosseum supercomputer, EU-backed frontier open-source project | ✅ | None | Regulated-industry focus; EC Frontier AI Grand Challenge backing |
| **Cloud Temple LLMaaS** | 36 open models from SecNumCloud infra | ✅ | None | See A; cheapest certified path for public sector tokens |
| **France Nuage** (FR) | Managed open-source LLMs (Mistral/Qwen/Llama) on French GPUs + on-prem boxes | ✅ | None | Turnkey "you use the model, we run the infra"; SME/ETI scale; very small company |
| **TextCortex** (DE) | EU-hosted router: 18+ models incl. US frontier models via one EU API | ⚠️ Operation EU, models US | EU processing + no-training guarantees, but model weights/logics remain US | Pragmatic for teams needing GPT-class performance with EU processing guarantees |
| **Requesty** (DE) | Frankfurt gateway, zero-retention, for Mistral | ✅ | None | Thin layer — resells EU residency for existing SDKs |
| **Bielik / PLLuM** (PL) | Open national model families | ✅ | None | Free/self-host; Polish-language optimization |
| **OpenEuroLLM / EUROPA** (EU projects) | Publicly-funded open European LLMs (EUROPA: ~400B params, 24 languages) | ✅ | None | Research/infrastructure play, not commercial SLAs — a resilience play in TBI's terms |

### E. Privacy-first assistants (packaged products)

| Solution | How it works | Fully European | Risk | Notes |
|---|---|---|---|---|
| **Lumo** (Proton, CH) | Open-source models on Proton-controlled EU DCs, zero-access encryption, no logs, no training on data; infrastructure being moved out of Switzerland to the EU (€100M+) | ✅ | None — Swiss law, EU-bound infra; provider literally cannot read chats | Consumer/SME assistant, not a raw API; free tier limited |
| **Le Chat / Vibe** (Mistral) | Packaged sovereign assistant on EU infra | ✅ | None (Enterprise DPA, EU servers) | Most-searched sovereign packaged option in France (Foxeet 2026) |
| **Euria** (Infomaniak) | Free sovereign chat, heat-recycling D4 datacenter | ✅ | None | Free consumer/entry-level option |

### F. Self-hosted stacks (your infrastructure — the only truly jurisdiction-free option)

| Solution | How it works | CLOUD Act risk | Notes |
|---|---|---|---|
| **vLLM** | High-throughput production inference; Inferact raised $150M (2026) to commercialize it | Zero (air-gap capable) | Production standard; pair with EU-hosted GPUs for "sovereign by configuration" |
| **Ollama** | Easiest local runtime (`ollama pull …`) | Zero | Prototyping/single-user; no batching, weaker throughput |
| **llama.cpp** | C++ low-level, GGUF, CPU/edge | Zero | Edge/embedded/max control |
| **SGLang / LM Studio / Open WebUI** | Alternatives at server-grade, desktop GUI, and web-UI layers respectively | Zero | Onyx/iunera 2026 comparisons cover the full stack |

---

## What changed vs my first answer (corrections & additions)

1. **~20 solutions added**, including the entire French SecNumCloud ecosystem (OUTSCALE, Cloud Temple, NumSpot), the "wrapped hyperscalers" (S3NS, Bleu) — a category I had wrongly collapsed into "US offerings" when S3NS is now legally qualified under SecNumCloud 3.2 — plus neoclouds (Nebius, Verda, Nscale), national model programs (Bielik, PLLuM, Domyn, EUROPA), managed integrators (LightOn, France Nuage, TextCortex), and EU-funded projects (OpenEuroLLM, EURO-3C).
2. **Corrected:** the French SecNumCloud-qualified club is now ~9–10 providers (OVHcloud, OUTSCALE, Cloud Temple, NumSpot, S3NS, Worldline, Orange Business, Cegedim, Oodrive) — my first answer omitted most of it.
3. **Nuanced:** "fully European" must be assessed on three axes — *legal* (HQ/jurisdiction), *operational* (who runs it), and *technological* (whose stack). S3NS/Bleu are legally French but technologically American; Nebius is legally Dutch but operationally global; TextCortex is operationally EU but serves US models.
4. **Kept:** the BCG/TBI reading — sovereignty is a spectrum, and per BCG's 2026 piece, resilience (diversification, exit plans, portability) often matters more than maximal sovereignty, which fits the hybrid architectures most enterprises actually deploy.

If you can point me to the "Cortecss" reference, I'll verify it and slot it into the right category.


---

Sovereign AI Solutions in Europe — Updated Panorama (Sept 2026)
Methodology
Curated lists consulted first: EuroAlternative, european-alternatives.eu, EuroToolKit.eu, europeantechmap.eu, EuroStack Directory (euro-stack.com), EuropeanPurpose, Vstorm Top 5, TextCortex Best 6, European Cloud (european.cloud), comparison.cloud, Craft AI & ProactiveAcademy guides (France), plus r/BuyFromEU threads and provider docs for each solution.

Category A: Full-Stack Sovereign Cloud + AI Services (IaaS/PaaS + model serving)
Solution	How It Works	Fully European	Legal / CLOUD Act Risk	Useful Notes
OVHcloud (FR)	Broadest catalogue: Public Cloud, Hosted Private Cloud; AI Endpoints — per Intelligence Privée, the only ready-to-use inference API with open-source models, no infra to manage. SecNumCloud 3.2 on qualified offers.	✅ France	None on SecNumCloud-qualified services; ISO 27001/27701, HDS, CISPE	~11% of French cloud spend; supports Mistral Large 123B reference architectures
Scaleway (FR)	Generative APIs, managed inference, H100/L4 GPU clusters; hosts open-weight models (Mistral, Llama, Qwen) via OpenAI-compatible API	✅ France (Iliad)	None; EC SEAL-3 — highest EU Cloud Sovereignty level; selected for EC €180M framework (2026–2032) and ECB digital euro (Oct 2025)	Best €/GPU performance per Callista benchmark (~4.8x AWS value); SecNumCloud in progress; minor caveat: parts of management console rely on US services (Xomnia analysis)
STACKIT (DE)	Cloud of Schwarz Group (Lidl); German/Austrian DCs; AI Model Serving in development	✅ Germany	None; BSI C5 Type 2, ISO 27001	Fastest-growing EU-native cloud 2025–2026
T Cloud Public (DE)	Deutsche Telekom; rebranded from Open Telekom Cloud Jan 2026; ModelArts training/inference	✅ Germany	None; BSI C5, TISAX	EU-staff-only operations
IONOS (DE)	AI Model Hub, GPU instances	✅ Germany	None; BSI C5 Type 2	Strong Mittelstand position
Exoscale (CH)	Swiss company, EU-only footprint; GPU instances, managed K8s	✅ Switzerland (EU DCs)	None (Swiss law)	Clean sovereignty score, transparent pricing
Hetzner (DE)	Budget GPU cloud	✅ Germany	None	Fewest certifications (ISO 27001 only)
Nebius (NL)	AI-focused cloud, ex-Yandex spin-off	⚠️ Netherlands HQ; check ownership history	None legally (EU-incorporated); listed as only Gold-tier EU-headquartered provider in ClusterMAX 2.1 (Apr 2026)	CADA Level 3 alignment
GCORE (LU)	Cloud/edge provider	✅ Luxembourg	None; CADA Silver-tier	Smaller player
Category B: French "Trusted Cloud" (SecNumCloud-qualified or in-process) — important addition
Solution	How It Works	Fully European	Risk	Notes
Outscale (3DS) (FR)	Dassault Systèmes subsidiary; AWS-API-compatible; certified SecNumCloud since 2016	✅ France	None	Historically the only full-production SecNumCloud IaaS; defense/health/classified focus; Mistral partnership (Nov 2025)
NumSpot (FR)	JV of 8 French actors: Docaposte, Dassault, Bouygues Telecom, La Banque Postale, La Poste, Orange, Capgemini, SFR	✅ France	None	SecNumCloud qualification in progress (PaaS target end-2026); built on Outscale infra, repositioned as hybrid/portable
Cloud Temple (FR)	SecNumCloud-qualified cloud	✅ France	None	Public sector & regulated focus
S3NS (FR)	JV Thales 60% / Google 40%; operates GCP in 3 Paris-region DCs, Thales employees only, quarantine zone for Google updates, PREMI3NS qualified SecNumCloud 3.2; Vertex AI joining H2 2026	⚠️ Legally French, technologically Google	Contested — French sovereignty contractually guaranteed by Thales, but infrastructure is US-derived; CLOUD Act exposure debated; passes the 24% non-EU ownership cap structurally	"Cloud de confiance" rather than pure sovereignty — DPLIANCE and Intelligence Privée both flag it as a compromise that doesn't satisfy strict SecNumCloud-style purists
Bleu (FR)	Orange + Capgemini + Microsoft JV on Azure	⚠️ Same hybrid model	Same contested status	Still in qualification
Key regulatory fact (new to this update): According to Cornford & Cross (July 2026), SecNumCloud enforces a 24% cap on non-EU controlling interests, EU data storage and legal domicile. This is why AWS/Azure/GCP are structurally ineligible, and why the Cohere–Aleph Alpha merger (~90% Canadian ownership) threatens Aleph Alpha's sovereign status (see below).

Category C: Model Developers / API Providers (sovereign LLM endpoints)
Solution	How It Works	Fully European	Risk	Notes
Mistral AI (FR)	La Plateforme API (EU-hosted, regional endpoints incl. Frankfurt); open-weight models under Apache 2.0; consumer assistant Vibe (renamed from Le Chat in May 2026)	✅ France	None on legal residence; supply-chain dependency on NVIDIA	~$1B ARR (May 2026); €3B Series D Sept 2026 at >€21B; acquired Koyeb (serverless); €830M debt financing for Bruyères-le-Châtel DC (~13,800 NVIDIA chips); €1.2B Sweden (EcoDataCenter) investment; framework agreements with French & German governments to 2030
Aleph Alpha (DE)	PhariaAI platform — traceable, explainable models for regulated/classified workloads	⚠️ Changing — merger with Canada's Cohere announced April 2026 gives Cohere shareholders majority ownership	Post-merger, ~90% Canadian ownership would exceed SecNumCloud's 24% cap by 4x — its sovereign certification status is at risk	Watch this deal if you're procuring on sovereignty grounds
Bielik (PL)	Volunteer-built Polish open-science model family (Bielik 11B v3), Apache-type open licence, commercial use OK; chat.bielik.ai, Bielik Guard	✅ Poland	None — open weights, downloadable	Most-downloaded European model (422k downloads/month, MRKT3.0 Aug 2026); runs locally (RTX 4090 etc.)
PLLuM (PL)	State-funded consortium of 6 Polish research institutions; built-in hybrid output-correction module for Polish data governance compliance	✅ Poland	None	Aimed at public administration, legal, banking/medical compliance
EU-funded open models	OpenEuroLLM, Apertus, ALIA, Teuken-7B, Velvet, EuroLLM-22B — fully open under OSI licences (Apertus even opens training data)	✅ EU	None — open weights	Production-ready now but not frontier-scale; EUROPA frontier project targets late 2027–early 2028
DeepL (DE)	Translation LLMs with EU hosting	✅ Germany	None	Immediate practical value for multilingual SMEs
Category D: Sovereign AI Platforms / Application Layer (turnkey enterprise)
Solution	How It Works	Fully European	Risk	Notes
LightOn Paradigm (FR)	Deploys LLMs on your own infrastructure (on-prem or private cloud); visual RAG with in-house retrieval; sovereign SaaS offering added June 2026	✅ France	None — data never leaves client perimeter	Clients: Safran, ENS Paris-Saclay, Sodern, Infocom'94; publicly listed on Euronext Growth (vendor-stability transparency)
Dust (FR)	Enterprise AI agents connected to your tools without development	✅ France	Low — check hosting per deployment	$40M Series B May 2026 (Abstract, Sequoia, Snowflake Ventures, Datadog)
Docaposte (FR)	La Poste subsidiary assembling sovereign GenAI offers using LightOn models + partners	✅ France	None	Target: public sector, sensitive data
Craft AI (FR)	AI platform letting you choose hosting among Scaleway, S3NS, NumSpot or hyperscalers	✅ France	Depends on chosen host	Interesting middle path: sovereignty becomes a deployment parameter
Unikia, Badis AI, Safebrain (FR)	Integrators/agencies specializing in sovereign self-hosted AI for SMEs/mid-caps	✅ France	None (self-hosted model)	Services more than products
Category E: LLM Routers / Gateways — category I under-weighted last time, and where cortecs lives
Solution	How It Works	Fully European	Risk	Notes
cortecs (DE)	Europe's LLM router — dynamically routes workloads across EU clouds (Spain, Germany, France, Finland, Poland) to ~120 model endpoints hosted in the EU; OpenAI-compatible; acts as your Data Processor, folding all upstream models in as Sub-processors under one DPA	✅ Germany (founded by Markus Tretzmüller & Alexander Steiner; Campus Founders AI Founders alum)	None operationally (EU deployment, GDPR + AI Act claims); but it routes to GPT, Claude, Gemini, Qwen, DeepSeek endpoints — the models themselves are non-European, merely EU-hosted. Token and model metadata may fall under its DPA but you should verify what each upstream provider sees	99.99% uptime SLA; ~32% average cost reduction; pay-per-use; multimodal (images, embeddings, audio); Discord community + free enterprise support above a spend threshold
TextCortex (DE)	Open-router style EU-hosted API with 18+ models (GPT-5.5, Claude Opus 4.7, GLM 5.1, Kimi K2.6), plus knowledge bases & enterprise automation	✅ Germany	Same caveat: EU-hosted, but models largely non-European	SOC/ISO certified
Requesty	Frankfurt gateway for Mistral models with zero-retention	⚠️ Verify corporate domicile — it's a routing layer, not necessarily an EU-incorporated company	Depends on deployment	Good for teams keeping existing OpenAI SDK code
The cortecs/TextCortex insight: this "router" category solves a legal-administrative problem (one DPA, GDPR umbrella, EU processing) rather than a model-sovereignty problem. Fine for compliance-driven workflows; not for those needing European-trained models. For that, combine cortecs with a Mistral or Bielik endpoint, or go one level down to Berget.

Category F: Consumer / Prosumer Sovereign Assistants
Solution	How It Works	Fully European	Risk	Notes
Lumo (Proton, CH)	Zero-access encryption, no logs, never trains on chats, open-source client	✅ Switzerland → moving infrastructure into the EU (€100M+ investment, announced July 2026, motivated by Swiss surveillance-law proposals and Proton's EuroStack commitment)	None	Reddit criticism noted: model identity undisclosed — users can't audit which LLM serves them
Euria (Infomaniak, CH)	Free sovereign assistant; self-hosted open models (Mistral Small, GPT-OSS 120B; default options include Qwen3); kSuite integration; waste heat warms 6,000 homes	✅ Switzerland	None legally; model caveat — Reddit r/BuyFromEU threads flag the Qwen base (Chinese-origin model) as inconsistent with a "sovereign" label, even though inference is Swiss	Ephemeral mode: discussions never stored, nothing recoverable even by Infomaniak
Mistral Vibe (ex-Le Chat) (FR)	Frontier assistant, Flash Answers at 1,100 tok/s, voice mode since late 2025	✅ France	None	Ranked by Dataethics (DK) as top on sovereignty with Lumo
GreenPT (FR)	Sustainability-focused assistant; auto-selects between GreenL (Mistral Small 3.2) and GreenR (GPT-OSS 120B) to limit token overconsumption	✅ France	None on hosting; mixed model origins	The eco-conscious positioning is unique
Ecosia AI (DE)	Chat function attached to the tree-planting search engine/browser	✅ Germany	Low — verify data handling	230M trees planted milestone
Bielik chat (PL)	Free Polish chat on Bielik models	✅ Poland	None	Pairs with LM Studio local downloads
Correction from my first answer: I mentioned HuggingChat in passing in some directories — note that Hugging Face is a US-incorporated company (NYC), so HuggingChat is not a European sovereign solution despite appearing in European-purpose directories. Its open models can, however, be self-hosted in Europe.

Category G: Self-Hosted Inference Frameworks (unchanged, still valid)
Ollama (easiest), llama.cpp (GGUF, CPU/edge), vLLM (production throughput; Inferact raised $150M in 2026 to commercialize it), SGLang, MLX (Apple Silicon), LM Studio (GUI), Open WebUI / AnythingLLM (interfaces), Onyx (RAG + enterprise search). All achieve absolute sovereignty (air-gap capable) but only control the model layer — you still choose the weights (a Qwen base is Chinese-origin even if self-hosted) and the hardware (NVIDIA dependency persists).

Category H: Public-Sector & EU Initiatives (added)
France: "Albert"-style public AI program; DiplolA (MEAE, 64 languages, opened inter-ministerially June 2026); "Visio" state videoconferencing with pyannoteAI transcription; SREN law Art. 31 decree (Apr 2026) mandating qualified clouds for sensitive admin data.
EU: EuroHPC AI Factories (19 operational per TechPlusTrends), EURO-3C federated cloud (€75M), planned AI Gigafactories (call for tenders).