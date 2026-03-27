# Gcore — Overview

> Global Hosting, CDN, Edge and Cloud Services

## What They Do
Gcore provides a vertically integrated global infrastructure platform spanning CDN, cloud compute, AI GPU infrastructure, DDoS protection, and streaming services — all built on a proprietary network of 210+ Points of Presence across six continents. They serve media companies, gaming operators, enterprises, and AI developers who need high-performance, low-latency infrastructure that can be deployed globally without relying exclusively on hyperscaler clouds. In the streaming world specifically, Gcore operates a purpose-built streaming platform with a single unified pipeline delivering both LL-HLS (~3s glass-to-glass) and LL-DASH (~2s glass-to-glass) from shared infrastructure.

## At a Glance
- **Website:** [gcore.com](https://gcore.com)
- **Industry:** Edge Cloud / CDN / AI Infrastructure / Security
- **Stage/Positioning:** Private company; 12+ years of operation; notable partners include Microsoft (CDN), NVIDIA (Dynamo inference), and Nokia (AI Cloud Stack for telcos)

## Products & Services

### Edge Network (CDN)
Gcore's content delivery network spans 210+ PoPs worldwide with total network capacity exceeding 200 Tbps. Delivers static and dynamic content, media segments, and API responses with low latency across global audiences. Supports HTTP/2, HTTP/3, WebSockets, custom routing rules, and advanced caching behaviors. Recent additions include Dedicated IP and BYOIP (Bring Your Own IP) capabilities for customers with strict security and compliance requirements. Microsoft has selected Gcore as a global CDN partner for content delivery at scale.

### Streaming Platform
A purpose-built live and on-demand streaming platform with a unified transcoding and packaging pipeline that simultaneously produces LL-HLS, LL-DASH (both in CMAF), and standard HLS (MPEG-TS) from a single input source. Key engineering achievements:
- **LL-DASH latency:** ~2.0 seconds glass-to-glass
- **LL-HLS latency:** ~3.0 seconds glass-to-glass
- **Full ABR ladder:** 360p through 1080p, all renditions synchronized across protocols
- Supports RTMP, SRT, and WebRTC (WHIP) ingest
- Multi-language audio track support within low-latency streams
- GPU-accelerated transcoding (NVIDIA/Intel) with software fallback for handling variable-resolution/FPS inputs from WebRTC sources
- AVEQ partnership for real-time QoE monitoring and SurfMeter analytics integration

### DDoS Protection
Gcore operates more than 200 Tbps of DDoS filtering capacity across its global network — one of the largest DDoS scrubbing networks available. Provides always-on, automated mitigation for volumetric attacks (Gcore successfully stopped a 6 Tbps attack in October 2025 and observed a 12 Tbps peak in Q4 2025). Protects networks, game servers, and application endpoints. The Gcore Radar report (published bi-annually) provides threat intelligence data on DDoS attack trends globally.

### Web Application and API Protection (WAAP)
Extends protection beyond network perimeters to the application and API layers. Guards against business-logic attacks, credential stuffing, API abuse, and zero-day exploits. Part of Gcore's integrated security stack alongside DDoS protection.

### Edge Cloud
Infrastructure-as-a-service across 50+ cloud locations globally — virtual machines, Kubernetes, bare metal, load balancers, DNS, and object storage. Positioned as a distributed cloud alternative to centralized hyperscaler regions, enabling workloads to run closer to end users in markets where AWS/Azure/GCP have limited presence.

### Bare Metal
Dedicated physical servers in Gcore data centers, available on-demand for high-performance workloads that require direct hardware access — AI training, gaming servers, and high-throughput video processing.

### AI Infrastructure (Everywhere AI)
Gcore's AI platform built on its edge network:
- **GPU Cloud:** On-demand GPU instances for AI training and inference, including NVIDIA H100 and A100 configurations, starting from €1.08/hour
- **Everywhere AI:** 3-click AI training and inference deployment across any environment (cloud, edge, on-prem, sovereign). Includes integration with Slurm (for HPC job scheduling), JupyterHub (for development), and token-based inference APIs
- **NVIDIA Dynamo Integration:** Gcore is one of the first partners to deploy NVIDIA Dynamo — an inference optimization stack capable of 6× throughput increase or 2× latency reduction for LLM inference workloads
- **AI Cloud Stack:** Sovereign and air-gapped AI deployments for government agencies, defense, and enterprises with strict data residency requirements. Nokia partnership makes this available to telco customers

### VDS Hosting
Virtual Dedicated Servers starting from €3.25/month — KVM-based VMs in USA, Europe, and Asia with SSD storage, DDoS protection, and 200 Mbit/s uplinks. Entry-level product used by developers and SMBs.

## Solutions & Use Cases
- **Low-Latency Live Streaming:** Sports, gaming, interactive events requiring sub-3-second glass-to-glass latency across LL-HLS and LL-DASH simultaneously
- **Gaming Infrastructure:** DDoS-protected game server hosting; Gcore's origins are in serving the gaming industry (Wargaming, Nitrado, Photon, Funcom are customers)
- **AI Model Training and Inference:** GPU cloud for large language model training; edge inference for low-latency AI applications globally
- **Media and Entertainment:** CDN delivery for video-heavy content properties; Microsoft CDN partnership is the marquee example of delivery scale
- **DDoS-Protected Hosting:** Mission-critical applications requiring always-on DDoS mitigation from a network with sufficient capacity to absorb 12+ Tbps attacks
- **Sovereign AI Deployments:** Government and defense customers needing AI compute that never touches a public cloud hyperscaler

## Technology & Architecture
Gcore's streaming pipeline is a deeply engineered unified system. The key architectural insight is that LL-HLS and LL-DASH require fundamentally different delivery behaviors from a CDN — LL-DASH uses chunked transfer of in-progress files, while LL-HLS uses blocking manifest requests and tiny part-file polling — but can share the same source if keyframe placement is unified.

Gcore built a custom "chunked-proxy" CDN module that handles in-progress file caching for LL-DASH: as bytes arrive from origin, they're forwarded to all connected clients simultaneously, caching what's been received while appending new bytes as they arrive. For LL-HLS, the CDN holds manifest requests open (blocking playlist reload) without consuming excessive server resources, and serves thousands of tiny part-file requests with minimal overhead.

The ingest pipeline accepts CBR streams via RTMP, SRT, or WebRTC WHIP. WebRTC ingest handling is particularly sophisticated — mobile devices vary their frame resolution, FPS, and bitrate dynamically based on network conditions; Gcore's software layer wraps variable-resolution streams in a stable overlay canvas (black-background scale-and-overlay) so the downstream transcoder output never stops even when input FPS drops to zero.

A 1-second GOP structure is used as the unified foundation across both protocols — enabling player startup within 0–1000ms of pressing play, at the cost of ~10–15% higher bitrate compared to longer GOPs. 2-second segments and 0.5-second parts (for LL-HLS) achieve the 3-second end-to-end target.

For AI, Gcore's compute infrastructure reuses the same distributed edge nodes built for CDN and gaming — applying them to GPU inference deployment. The CEO has described this as "not a pivot" but an extension of the same core capability: moving compute closer to where it's needed.

## Key Differentiators
- **Unified LL-HLS and LL-DASH from a single pipeline:** Most CDNs serve one low-latency protocol or the other; Gcore's custom "chunked-proxy" architecture handles both simultaneously from shared infrastructure — enabling per-device protocol optimization (iOS 17.1+ gets LL-DASH at 2s; older devices get LL-HLS at 3s; legacy gets standard HLS at 9s) without running separate delivery workflows
- **DDoS scale that matches real-world attacks:** 200+ Tbps scrubbing capacity vs. 12 Tbps observed peak attacks in Q4 2025; Gcore's Radar reports provide genuine threat intelligence from observed traffic, not marketing estimates
- **Network-native AI infrastructure:** Unlike standalone GPU cloud providers, Gcore can deploy AI inference at 210+ PoPs with sub-millisecond proximity to end users in regions where hyperscalers have no presence
- **Sovereign and air-gapped AI:** Few infrastructure providers can genuinely serve government and defense AI needs; Gcore's combination of CDN operational history in restricted regions and the Nokia/AI Cloud Stack partnership creates a credible offering here
- **Microsoft CDN partnership:** Being selected by Microsoft as a global CDN partner validates the network's reliability and scale for the most demanding delivery requirements

## Notable Customers & Integrations
**Customers:** Microsoft (CDN partner), Wargaming, LALIGA, Mirantis, Nitrado, Sandbox (gaming), Photon, Funcom (gaming), Saber, Higgsfield (AI), ProSieben, NHN Cloud, Aleph Alpha

**Integrations/Partnerships:** NVIDIA (Dynamo inference deployment), Nokia (AI Cloud Stack for telco enterprise), AVEQ/SurfMeter (streaming QoE monitoring), Intel (hardware acceleration), Dell, Equinix

## Pricing
GPU cloud from €1.08/hour for inference instances; VDS hosting from €3.25/month. CDN pricing is usage-based by bandwidth. AI training instances priced by GPU type and reservation model (on-demand vs. reserved). Free tier available for CDN and cloud. Custom pricing for enterprise and sovereign deployments.

---

## Blog & Resources Highlights
_Curated from Gcore's blog (gcore.com/blog)_

### How We Engineered a Single Pipeline for LL-HLS and LL-DASH — October 20, 2025
> A detailed technical deep-dive into how Gcore built a unified low-latency streaming pipeline for both LL-HLS and LL-DASH from a shared source. The key engineering insight is using a unified 1-second GOP as the common foundation, then building custom CDN modules: a "chunked-proxy" for LL-DASH's in-progress file caching, and specialized request-holding logic for LL-HLS's blocking playlist reload behavior. The result: ~2.0s latency for LL-DASH and ~3.0s for LL-HLS, served simultaneously, enabling per-device protocol optimization (iOS 17.1+ at 2s, legacy HLS at 9s) from one backend.
[Read more](https://gcore.com/blog/ll-hls-and-ll-dash-single-pipeline)

### Achieving 3-Second Latency in Streaming: A Deep Dive into LL-HLS and LL-DASH Optimization with CDN — December 15, 2025
> Gcore's comprehensive technical guide to achieving and sustaining sub-3-second glass-to-glass latency in production. The article covers counterintuitive monitoring: a high response_time on an LL-HLS manifest (e.g., 500ms) is expected behavior (indicating correct blocking), while a low response_time could signal a problem. Details ffmpeg configuration for CBR, zero-latency encoding, and fixed keyframe placement. Explains how unified transcoding, packaging, and CDN delivery must be synchronized — not treated as separate pipelines — to achieve consistent low latency.
[Read more](https://gcore.com/blog/optimizing-hls-dash-3sec)

### From CDN to AI Powerhouse: Gcore at 12 — March 5, 2026
> Gcore's anniversary retrospective, published alongside two significant announcements: the NVIDIA Dynamo inference partnership and Microsoft's selection of Gcore as a global CDN partner. The article articulates Gcore's strategic thesis — that 12 years of building a production-grade global network provides the ideal foundation for AI infrastructure, specifically for inference at the edge (low-latency delivery to Frankfurt, São Paulo, Singapore), sovereign AI deployments, and air-gapped enterprise environments. CEO Andre Reitenbach: "You can't replicate our team's experience."
[Read more](https://gcore.com/blog/gcore-at-12)

### Gcore Radar Q3–Q4 2025: Three Insights Into an Accelerating Threat Landscape — March 24, 2026
> Gcore's bi-annual threat intelligence report revealed a dramatic escalation in DDoS attack scale in H2 2025: total attack counts more than doubled vs. H1, maximum observed attack size surged to 12 Tbps in Q4 (up from 2.2 Tbps in H1), and 75% of network-layer attacks now last less than one minute — hyper-concentrated bursts designed to overwhelm defenses before automated mitigation engages. Application-layer attacks trend opposite: 50% last 10–30 minutes, 8% exceed an hour. The AISURU botnet (compromised IoT devices in Mexico, Brazil, and the US) was the primary driver of the volume surge.
[Read more](https://gcore.com/blog/radar-q3-q4-2025-insights)

### Introducing Gcore Everywhere AI: 3-Click AI Training and Inference for Any Environment — November 3, 2025
> Gcore launched Everywhere AI — a platform enabling AI training and inference deployment across cloud, edge, on-prem, and sovereign environments through a unified interface. The product addresses enterprise AI fragmentation: separate tools for development, training, and serving with different infrastructure and access controls. The launch integrates Slurm for HPC job scheduling, JupyterHub for development environments, and token-based inference APIs — covering the full AI lifecycle management problem. Nokia partnership announced to bring this to telco enterprise customers.
[Read more](https://gcore.com/blog/introducing-everywhere-ai)

---

## Key Takeaways
- **The only vertically integrated CDN + AI infrastructure company at this scale:** Gcore can serve streaming delivery, DDoS protection, and GPU inference from the same 210+ PoP global network — a unique architectural combination
- **Low-latency streaming at genuine depth:** The LL-HLS/LL-DASH unified pipeline is production-grade engineering, not a marketing claim — detailed technical documentation and 2–3 second measured latency demonstrate real capability
- **DDoS expertise is a streaming differentiator:** A CDN with 200+ Tbps scrubbing capacity that publishes actual threat intelligence from observed traffic is a meaningfully more capable DDoS partner than vendors with theoretical capacity claims
- **Gaming heritage matters:** Wargaming, Nitrado, and Funcom represent years of serving the most latency-sensitive, spike-prone, abuse-prone traffic patterns — making Gcore's infrastructure battle-tested before media customers ever arrived
- **AI infrastructure is the next major growth leg:** The NVIDIA Dynamo and Nokia partnerships signal that Gcore is positioning AI compute delivery (especially sovereign and edge inference) as the next platform expansion — and the CDN heritage is the actual competitive advantage
