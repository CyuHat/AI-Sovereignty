# Deep Dive: The Confidential Computing Technical Stack

## Part 1: The Problem It Solves — "Data in Use"

Classic encryption covers data **at rest** (disk) and **in transit** (network), but the moment a CPU or GPU *processes* data, it must exist in plaintext in system memory. This gap is called **data in use** exposure:

> "Encryption of data at rest and in-transit is increasingly common, but traditional computing leaves data exposed in system memory during processing—known as data in use—which puts it at risk." — Red Hat [[0]](https://www.redhat.com/en/blog/unlocking-sovereign-ai-and-protected-corporations-confidential-computing)

Confidential computing fills this with **hardware-based, attested Trusted Execution Environments (TEEs)** that protect "data confidentiality, data integrity, and code integrity while data is in use" [[0]](https://www.redhat.com/en/blog/unlocking-sovereign-ai-and-protected-corporations-confidential-computing). The key architectural consequence for sovereign AI: the cloud provider, hypervisor, host OS, and even a rogue admin are removed from the trust boundary.

---

## Part 2: Layer 1 — CPU TEEs (The Foundation)

The industry has converged on **Confidential Virtual Machines (CVMs)**, where an entire VM's memory is encrypted and the hypervisor is demoted to an untrusted scheduler. Per ACM SIGMETRICS, "SEV-SNP and TDX are production defaults in 2026, available across mainstream server SKUs and all major cloud providers, making hardware TEEs a standard infrastructure primitive rather than a niche compliance tool" [[6]](https://multiwaresolutions.com/blog/confidential-computing-amd-sev-snp-and-intel-tdx-e9c9-2026-06-09).

| Feature | **AMD SEV-SNP** | **Intel TDX** | **AWS Nitro Enclaves** |
|---|---|---|---|
| Isolation unit | Per-VM, encrypted with unique ephemeral AES key held by on-die **AMD Secure Processor** (embedded ARM Cortex-A5) | "Trust Domains" managed by a CPU-resident **TDX Module** at a new privilege level below the hypervisor | Sub-enclave of an EC2 instance via custom Nitro hypervisor + Nitro Security Chip |
| Memory encryption | AES-128 XEX per VM | MKTME AES-XTS-128 per trust domain | Proprietary isolation model |
| Maturity | 4th iteration (SEV 2016 → SEV-ES → SNP 2021 silicon); "longer optimization cycle" | Newer; available on Xeon 6 / Emerald & Granite Rapids | AWS-only; "does not currently match the TDX/SEV-SNP threat model on the AI workloads we care about" [[9]](https://voltagegpu.com/blog/tdx-vs-sev-snp-confidential-ai-2026) |
| Strength | Price/performance; scales to more VMs per socket; strongest for compute-heavy workloads [[1]](https://phala.com/learn/AMD-SEV-vs-Intel-TDX-vs-NVIDIA-GPU-TEE)[[4]](https://stealthcloud.ai/cloud-paradigms/confidential-computing-deep-dive/) | Smallest TCB; strong compliance documentation (Azure's TDX-based assurance packs are "familiar to auditors before they even see" alternatives) [[9]](https://voltagegpu.com/blog/tdx-vs-sev-snp-confidential-ai-2026) | Deep KMS integration (`kms:RecipientAttestation`) |
| Weakness | Known attack surface (see Part 6) | Younger; per one academic overview, earlier lack of shipping hardware delayed vulnerability discovery [[0]](https://sys.cs.fau.de/extern/lehre/ws22/akss/material/amd-sev-intel-tdx.pdf) | Attestation uses CBOR-COSE documents that "will not parse NVIDIA GPU attestation JWTs" — a real integration friction [[6]](https://www.spheron.network/blog/confidential-gpu-computing-nvidia-tee-encrypted-vram/) |

There's also **Arm CCA** (Confidential Compute Architecture), positioned as "future of edge and mobile confidential computing" [[1]](https://phala.com/learn/AMD-SEV-vs-Intel-TDX-vs-NVIDIA-GPU-TEE). A critical operational caveat: attestation chains differ per vendor, so "your confidential computing chip security posture can quietly change when a workload migrates between providers — a workload attested against a VCEK chain on Azure DCasv5 needs an entirely different attestation-verification path if it's later moved to a TDX-based DCesv5 instance" [[8]](https://safeguard.sh/resources/blog/technical-comparison-of-amd-sev-snp-and-intel-tdx-security-guarantees).

---

## Part 3: Layer 2 — GPU TEEs (What Makes Confidential *AI* Possible)

CPU TEEs are useless for modern AI: "GPUs are 10-100x faster than CPUs for neural network math," and until recently "GPU memory was unencrypted and visible to the cloud provider" [[4]](https://phala.com/learn/How-Nvidia-Enable-Confidential-AI). NVIDIA's Hopper architecture closed this gap — H100/H200 are the first GPUs with native confidential computing [[4]](https://phala.com/learn/How-Nvidia-Enable-Confidential-AI)[[7]](https://www.edgeless.systems/wiki/hardware/nvidia-hopper-h100).

### The NVIDIA GPU-CC trust chain

Per NVIDIA's technical blog and whitepaper [[2]](https://developer.nvidia.com/blog/confidential-computing-on-h100-gpus-for-secure-and-trustworthy-ai/)[[1]](https://images.nvidia.com/aem-dam/en-zz/Solutions/data-center/HCC-Whitepaper-v1.0.pdf):

1. **Unique per-device identity**: every H100 has a private key "burned into the fuses" at production time [[7]](https://www.edgeless.systems/wiki/hardware/nvidia-hopper-h100)
2. **Secure boot**: GPU measures/hashes its firmware at boot
3. **SPDM session**: the GPU establishes an authenticated session with the CPU TEE (DMTF Security Protocol and Data Model)
4. **Composite attestation**: the CPU TEE proves the CPU side is sealed; the NVIDIA attestation report proves the GPU side (signature, firmware measurements, workload hash); **Protected PCIe / bounce-buffer encryption** seals the bus between them — "the TEE-IO / Protected PCIe encryption proves the bus between them is sealed" [[9]](https://voltagegpu.com/blog/tdx-vs-sev-snp-confidential-ai-2026)
5. **Encrypted DMA**: all host↔device transfers are AES-GCM encrypted via dedicated hardware copy engines; "on H100 GPU, secure communication is supported with eight LCE, each having distinct keys for h2d and d2h communication, in both user and kernel mode" [[5]](https://arxiv.org/html/2507.02770v1)
6. **Transparent to applications**: "running CUDA applications is identical to running them on a GPU with CC-Off. The CUDA driver and GPU firmware take care of the required encryption workflows in CC-On mode transparently" [[2]](https://developer.nvidia.com/blog/confidential-computing-on-h100-gpus-for-secure-and-trustworthy-ai/)
7. **Side-channel hardening**: CC mode "blocks direct access to its internal memory and disables performance counters, which could be used for side-channel attacks" [[7]](https://www.edgeless.systems/wiki/hardware/nvidia-hopper-h100)

### Operating modes and current limitations

The H100 has three modes: **CC-Off**, **CC-On**, and **CC-DevTools** [[5]](https://nand-research.com/wp-content/uploads/2024/05/2024-04-30-RN-NVIDIA-H100-CC.pdf). Practical constraints found in deployment guides:

- **Not default in the cloud**: "CC mode is not available on on-demand GPU marketplace[s]... you need a reserved commitment: the data center partner must enable CC mode at the BIOS/VBIOS level on the target host, flash the matching CC-capable VBIOS" [[6]](https://www.spheron.network/blog/confidential-gpu-computing-nvidia-tee-encrypted-vram/)
- **Firmware-version coupling**: CUDA graph compatibility requires H100 firmware 550+ and vLLM v0.17.0+ — remove `--enforce-eager` and re-benchmark, or you're overpaying overhead [[6]](https://www.spheron.network/blog/confidential-gpu-computing-nvidia-tee-encrypted-vram/)
- **Ecosystem asymmetry**: "TDX + NVIDIA H100/H200/B200 is the integration NVIDIA, Microsoft, Google... document and ship as the primary path... SEV-SNP + Hopper works at the technical level but is materially less documented in cloud catalogues" [[9]](https://voltagegpu.com/blog/tdx-vs-sev-snp-confidential-ai-2026)
- **Forward roadmap**: "By late 2026, NVIDIA's Blackwell and Vera GPU architectures will ship with confidential computing capabilities designed to chain with host SEV-SNP or TDX, enabling end-to-end encrypted AI training pipelines where neither the GPU driver nor the hypervisor can observe model weights or gradients" [[6]](https://multiwaresolutions.com/blog/confidential-computing-amd-sev-snp-and-intel-tdx-e9c9-2026-06-09)

---

## Part 4: Layer 3 — Remote Attestation & Key Release (The Trust Broker)

This is the layer that turns hardware isolation into *provable* trust. The industry standard is the **IETF RATS architecture (RFC 9334)**: "Evidence flows up from the Attester; the Verifier appraises it against reference values and endorsements; Attestation Results gate the Relying Party's decision to release keys. No valid proof, no secret" [[5]](https://stribog.com/blog/confidential-computing-kubernetes-remote-attestation-tee).

### The CNCF Confidential Containers (CoCo) + Trustee stack

CoCo (promoted from CNCF Sandbox to incubating in July 2026) is the orchestration layer that "makes all of this work with an ordinary Kubernetes pod spec" — a pod opts in via `runtimeClassName: kata-qemu-snp`, and attestation/key-release negotiation happens "entirely below the pod spec, with no application changes" [[5]](https://stribog.com/blog/confidential-computing-kubernetes-remote-attestation-tee). Its component model [[3]](https://www.redhat.com/en/blog/introducing-confidential-containers-trustee-attestation-services-solution-overview-and-use-cases)[[7]](https://confidentialcontainers.org/docs/attestation/):

- **Attestation Agent (AA)** — guest-side component that produces the evidence
- **Key Broker Service (KBS)** — the gatekeeper that receives key requests, demands evidence, and releases secrets only to proven-secure TEEs
- **Attestation Service (AS)** — the verifier, appraising evidence against policy
- **Reference Value Provider Service (RVPS)** — supplies the expected measurements (firmware hashes, software versions) to compare against
- **Confidential Data Hub (CDH)** — guest-side secret cache/storage

### The canonical confidential AI inference flow

Combining the NVIDIA reference architecture, Red Hat's OpenShift AI PoC, and the CoCo docs [[4]](https://docs.nvidia.com/enterprise-reference-architectures/deploying-proprietary-models-confidential-compute-self-hosted-kubernetes/latest/architecture-summary.html)[[8]](https://www.redhat.com/en/blog/ai-meets-security-poc-run-workloads-confidential-containers-using-nvidia-accelerated-computing)[[1]](https://docs.nvidia.com/datacenter/cloud-native/confidential-containers/latest/overview.html):

```card
{ "type": "summary", "title": "Attested inference lifecycle", "body": "1) Model provider ships a SIGNED container image + ENCRYPTED model weights to a registry. 2) Kubernetes schedules the pod onto a CC-capable node (CPU TEE + H100 CC mode) via a confidential runtime class (Kata + CoCo). 3) The guest Attestation Agent collects CPU TEE evidence (e.g., SEV-SNP VCEK-signed report) AND the NVIDIA GPU attestation JWT (REMOTE_GPU_CLAIMS containing firmware measurements and CC-mode flags). 4) The KBS/Trustee verifier compares both against pinned reference values. 5) Only on success does the KMS release the model decryption key INTO the TEE. 6) Image layers are verified/decrypted INSIDE the enclave; the inference server (vLLM, Triton, NIM, TensorRT-LLM) runs unmodified. 7) Kubernetes can schedule, route, monitor, and recover the workload — but the platform can never read the model or inference payloads. Image pulls are redirected through the guest (nydus-snapshotter → image-rs inside the TEE) so the host containerd never sees plaintext layers." }
```

The composite attestation is the linchpin: "The host TEE proves the CPU side is sealed; the NVIDIA attestation proves the GPU side is sealed; the TEE-IO / Protected PCIe encryption proves the bus between them is sealed" [[9]](https://voltagegpu.com/blog/tdx-vs-sev-snp-confidential-ai-2026).

### Attestation-gated key release across clouds

Different providers implement the broker differently: AWS KMS `kms:RecipientAttestation` (Nitro), **Microsoft Azure Attestation** (TDX-rooted), **Google Confidential Space** (SEV-SNP rooted). Azure publishes a TDX-based confidential computing assurance pack that "tends to show up in customer compliance binders" [[1]](https://appscale.blog/en/blog/confidential-computing-ai-inference-tees-nitro-enclaves-nvidia-h100-h200-2026)[[9]](https://voltagegpu.com/blog/tdx-vs-sev-snp-confidential-ai-2026).

---

## Part 5: Layer 4 — Application Frameworks & Platform Abstractions

Below the Kubernetes layer sit the tools that avoid rewriting applications:

| Tool | Origin | Purpose |
|---|---|---|
| **Gramine** (formerly Graphene) | Invisible Things Lab / Intel; CCC's first production-ready implementation [[5]](https://cacm.acm.org/news/confidential-computing-conquers-hacks/) | Library OS inserting a "platform adaptation layer (PAL) between the application and the host OS" — runs unmodified Linux binaries inside enclaves; extended by "Gramine Shielded Containers" to container workloads [[1]](https://aisecurityandsafety.org/en/glossary/confidential-computing-ai/)[[5]](https://cacm.acm.org/news/confidential-computing-conquers-hacks/) |
| **Occlum** | Tsinghua / Ant Group | Library OS for unmodified apps in SGX [[0]](https://arxiv.org/pdf/2208.10134) |
| **SCONE** | Scontain | SGX-based container environment [[0]](https://arxiv.org/pdf/2208.10134) |
| **Constellation / Edgeless Systems** | Edgeless Systems | Confidential Kubernetes cluster abstraction [[6]](https://multiwaresolutions.com/blog/confidential-computing-amd-sev-snp-and-intel-tdx-e9c9-2026-06-09) |
| **Enarx / Open Enclave / Keystone / Veracruz** | CCC projects | Fungible serverless TEEs; single-app enclaves; RISC-V TEEs; multi-party distributed TEEs respectively [[5]](https://cacm.acm.org/news/confidential-computing-conquers-hacks/) |

Above them, commercial **Confidential AI platforms** package the whole stack: **Opaque** (confidential agentic RAG), **Fortanix C-AI** ("developing and deploying AI models on sensitive data"), **Privatemode.ai** ("prompts encrypted at all times... combining confidential VMs with H100 GPUs and secure sandboxing"), and **TELUS/Fortanix/NVIDIA** in Canada building a full "Confidential AI Factory" with "cryptographic attestation and secure key releases to establish a verifiable chain of [trust]" [[6]](https://www.opaque.co/)[[7]](https://www.fortanix.com/platform/confidential-ai)[[3]](https://www.nvidia.com/en-us/data-center/solutions/confidential-computing/)[[8]](https://finance.yahoo.com/news/telus-fortanix-partner-bring-confidential-163600857.html).

Crucially, modern abstractions are **TEE-agnostic**: "the same Docker container works on SEV, TDX, or GPU TEE," and combined CPU+GPU setups (AMD SEV-SNP host + H100 GPU TEE "both in the same system, both protecting data") are "common for confidential AI workloads" [[1]](https://phala.com/learn/AMD-SEV-vs-Intel-TDX-vs-NVIDIA-GPU-TEE).

---

## Part 6: Performance — What Does Confidential AI Actually Cost?

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "width": "container",
  "title": { "text": "Confidential Computing Overhead Estimates", "subtitle": "GPU inference overhead is modest; attestation cost is one-time at startup" },
  "data": {
    "values": [
      { "component": "GPU inference throughput (NVIDIA est.)", "overhead_pct": 4.0 },
      { "component": "GPU TEE typical range (low)", "overhead_pct": 5.0 },
      { "component": "GPU TEE typical range (high)", "overhead_pct": 15.0 },
      { "component": "Inference overhead (AppScale, high end)", "overhead_pct": 7.0 },
      { "component": "NVIDIA official CC performance retained", "overhead_pct": 2.0 }
    ]
  },
  "mark": { "type": "bar" },
  "encoding": {
    "x": { "field": "overhead_pct", "type": "quantitative", "title": "Overhead (%)" },
    "y": { "field": "component", "type": "nominal", "title": null }
  }
}
```

Numbers from the sources (note they vary by model size, batch config, firmware version, and PCIe transfer patterns [[6]](https://www.spheron.network/blog/confidential-gpu-computing-nvidia-tee-encrypted-vram/)[[9]](https://arxiv.org/html/2409.03992v2)):

- NVIDIA's overall claim: hardware-level protection "at up to 98% of the performance of unsecured deployments" [[3]](https://www.nvidia.com/en-us/data-center/solutions/confidential-computing/)
- NVIDIA's CC-mode benchmark characterization: "2-5% throughput overhead for transformer inference workloads" [[6]](https://www.spheron.network/blog/confidential-gpu-computing-nvidia-tee-encrypted-vram/)
- Practitioner-reported GPU TEE overhead: "5-15%" generally [[1]](https://phala.com/learn/AMD-SEV-vs-Intel-TDX-vs-NVIDIA-GPU-TEE), "1-7 percent inference throughput overhead" in 2026 deployments [[1]](https://appscale.blog/en/blog/confidential-computing-ai-inference-tees-nitro-enclaves-nvidia-h100-h200-2026)
- The academic benchmark identifies the **PCIe bottleneck** as the main cost driver for LLM inference — CPU↔GPU data transfers dominate, especially at smaller token lengths [[9]](https://arxiv.org/html/2409.03992v2)
- **Attestation cost is one-time at instance startup, not per request** [[6]](https://www.spheron.network/blog/confidential-gpu-computing-nvidia-tee-encrypted-vram/) — you must budget it for autoscaling cold starts
- Economics: "sovereign GPU model becomes economically superior once deployment scale exceeds approximately 200 developers" (from the earlier cosine.sh analysis) — TEE overhead barely changes this calculus

---

## Part 7: The Known Weaknesses — Security Research & Criticism

This is where the stack's marketing meets its reality. Honest reporting requires surfacing four major issue classes:

### 1. Closed-Ecosystem Opacity (NVIDIA's Black Box)
IBM and Ohio State researchers reverse-engineered H100 GPU-CC and found serious transparency problems: "This lack of transparency makes it difficult to evaluate whether NVIDIA GPU-CC meets the security requirements of confidential computing" — they had to probe BAR0 registers one by one and instrument "the only open-source component in Nvidia's GPU software stack" (the kernel module) to understand behavior at all [[0]](https://arxiv.org/html/2507.02770v1)[[9]](https://www.sdxcentral.com/news/nvidia-confidential-gpu-probe-uncovers-key-security-gaps/).

### 2. GPU Memory Isn't Actually Runtime-Encrypted
The most consequential finding from that research: "Nvidia's GPU-CC was also found **not to encrypt GPU memory at runtime**, unlike CPU-based confidential computing systems. Instead, GPU-CC relies solely on access control mechanisms like firewalls to protect memory regions, which creates potential vulnerabilities if such controls are bypassed" [[9]](https://www.sdxcentral.com/news/nvidia-confidential-gpu-probe-uncovers-key-security-gaps/). CPU TEEs encrypt VRAM-adjacent paths; the GPU's HBM is protected by isolation, not cryptography.

### 3. Live Academic Attack Literature
Named attacks documented against the CVM ecosystem include **HECKLER** ("Breaking Confidential VMs with Malicious Interrupts", USENIX Security 2024) and **Heracles** ("Chosen Plaintext Attack on AMD SEV-SNP", ACM CCS 2025) [[7]](https://arxiv.org/html/2507.02770v2). Earlier academic work also noted SEV-SNP "does not prevent read access to (encrypted) VM private pages, which can be used to leak guest register values or recover secret keys" [[0]](https://sys.cs.fau.de/extern/lehre/ws22/akss/material/amd-sev-intel-tdx.pdf), and survey work found H100-class products "might lack protection for certain hardware components, such as power management components" [[3]](https://dl.acm.org/doi/full/10.1145/3793532).

### 4. 128-Bit Memory Keys
Both vendors currently ship **AES-128** for the memory encryption data path, which "has drawn criticism from cryptographers who note that 128-bit keys... offer a smaller security margin than the AES-256 used by some competing memory encryption technology in HSMs" [[8]](https://safeguard.sh/resources/blog/technical-comparison-of-amd-sev-snp-and-intel-tdx-security-guarantees).

### Named Anti-Patterns (from practitioner guides)
The AppScale architecture guide catalogs failure modes: "TEE without verification, static measurement pinning, GPU without CPU TEE, marketing-label confidential" — i.e., deploying a TEE and never checking attestation results, or trusting a GPU TEE whose host CPU is fully exposed, or buying a cloud SKU labeled "confidential" without verifying the attestation chain [[1]](https://appscale.blog/en/blog/confidential-computing-ai-inference-tees-nitro-enclaves-nvidia-h100-h200-2026).

---

## Part 8: Tying It Back to Sovereign AI

Confidential computing is what makes the "hybrid sovereignty" models from our earlier discussion technically credible rather than contractual:

- **It converts a contract into a cryptographic proof**: the ultraviolet.rs framing from our sovereign AI discussion — "sovereignty is a hardware guarantee, not a contractual promise" — is literally implemented by attestation-gated key release
- **Regulatory recognition is arriving**: "regulatory frameworks like the EU Data Act explicitly recognize hardware TEEs as a valid safeguard for cross-border data processing" [[6]](https://multiwaresolutions.com/blog/confidential-computing-amd-sev-snp-and-intel-tdx-e9c9-2026-06-09), and practitioners now map TEE evidence to "HIPAA / DPDP / EU AI Act Article 10" compliance binders [[1]](https://appscale.blog/en/blog/confidential-computing-ai-inference-tees-nitro-enclaves-nvidia-h100-h200-2026)
- **Federated learning + TEEs**: Google's architecture brings "the model to the location where the data is stored, rather than centralizing the data," combining confidential federated learning with TEE-protected aggregation [[1]](https://docs.cloud.google.com/architecture/security/confidential-computing-analytics-ai) — this is the architecture underpinning sovereign multi-agency analytics
- **But it sharpens the sovereignty paradox**: even TEEs rely on trusting the chip *vendor* — NVIDIA attestation is signed by NVIDIA, and as the Part 7 research shows, you cannot fully audit that signing chain. A country can achieve cryptographic independence from its cloud provider while deepening dependence on American silicon — the same "conditional sovereignty" critique the CNAS index applied to Gulf compute

```card
{ "type": "finding", "title": "Bottom line on the stack", "body": "The confidential computing stack is genuinely production-ready in 2026: CPU CVMs (SEV-SNP/TDX) are server defaults, NVIDIA H100/H200 provide GPU TEEs at 2-7% inference overhead, and the CNCF CoCo/Kata/Trustee layer makes attestation-gated, encrypted deployments a Kubernetes pod annotation rather than a rewrite. Its honest limitations: GPU HBM is protected by access control rather than encryption, the NVIDIA trust chain is unauditable by design, a live academic attack literature targets the CVM layer (HECKLER, Heracles), and the whole edifice relocates your trust boundary from the cloud operator to the chip vendor — a trade many sovereign AI strategies are consciously making.", "severity": "warning" }
```

A sourcing caveat: performance numbers vary noticeably between NVIDIA's official benchmarks (2-5%), vendor aggregations (5-15%), and academic measurement, and some of the more recent developments (Blackwell CC chaining, exact AI Act mappings) come from 2026 vendor/practitioner content that I can't independently verify beyond these sources.

Would you like me to go deeper on any layer — for example the attestation evidence formats (SEV-SNP VCEK vs TDX DCAP quotes vs GPU JWTs), the academic attack techniques, or a worked deployment architecture for confidential LLM inference?