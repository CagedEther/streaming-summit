# Vecima Networks — Overview

> Powering the Networks of Tomorrow. Today.

## What They Do
Vecima Networks is a publicly traded technology company that builds hardware and software products for broadband access networks and video content distribution. For the streaming industry specifically, Vecima's MediaScale platform provides the cache, origin, transcode, and storage infrastructure that cable operators and content service providers use to deliver IP linear TV, cloud DVR, time-shifted TV, and VOD to subscribers. They also offer Open CDN — an implementation of the SVTA Open Caching standard — and have recently added KeyFrame, an AI-powered generative video optimization product that improves perceptual quality at the encoder input without changing downstream infrastructure.

## At a Glance
- **Website:** https://www.vecima.com
- **Industry:** Cable/Telecom Infrastructure & Video Distribution Technology
- **Stage/Positioning:** Publicly traded (TSX: VCM); serves cable MSOs, broadband operators, and content service providers globally

## Products & Services

### MediaScale — Content Distribution Platform
Vecima's software-based video distribution suite, designed for cable and broadband operators delivering managed video services. It consists of four integrated components:

**MediaScale Origin** — Ingests content from live sources and VOD libraries, packages it for ABR delivery (HLS, DASH, CMAF), applies DRM encryption (Widevine, PlayReady, FairPlay), and outputs to downstream cache and edge infrastructure. Supports live linear, nDVR timeshift, cloud DVR, and VOD catalogs simultaneously.

**MediaScale Cache** — High-scale, high-density edge caching for IP ABR delivery. Supports Origin Shield Caching (protecting MediaScale Origin from direct edge requests) and legacy QAM VoD Pump functionality for hybrid analog/IP networks. Designed for flexibility across network topologies from centralized to fully distributed edge deployments.

**MediaScale Transcode** — COTS-based (Commercial Off-The-Shelf hardware) software transcoder that uses the latest CPU and GPU encoding technologies. Supports both H.264 and HEVC output, multiple adaptive bitrate profiles, and processing of live or file-based sources. Runs on standard server hardware, avoiding proprietary appliance lock-in.

**MediaScale Storage** — Modern, cost-effective storage architecture for the large-scale requirements of IP linear, timeshift buffers, cloud DVR recording, and VOD catalogs. Designed for high-throughput write performance during live recording and high-read concurrency during VOD playback.

### Open CDN
Vecima's implementation of the SVTA (Streaming Video Technology Alliance) Open Caching specification — a non-proprietary, standardized framework for deploying CDN cache capacity inside ISP networks. Open CDN aggregates edge cache resources deep in the network to serve as a CDN alternative for content providers, reducing public CDN costs and improving quality of experience. Vecima actively participates in SVTA working groups and the IETF CDNI (Content Delivery Networks Interconnection) group, contributing to the Open Caching specs for traffic delegation, configuration management, observability logging, and content management. The Logging specification, Configuration Management Interface v2.0, and Bootstrap Interface are recent developments Vecima has contributed to.

### KeyFrame — AI-Powered Video Optimization
A "bump-in-the-wire" generative AI video optimization component that sits upstream of the encoder in live streaming workflows. Rather than modifying the encoder or downstream delivery chain, KeyFrame processes the raw source video using a trained generative AI model to reconstruct lost detail, reduce noise, stabilize texture, and improve perceived quality — particularly for challenging sports content (fast motion, grass/ice textures, frequent camera cuts). The result is higher perceptual quality (measured via VMAF) at the same or lower bitrates, meaning operators can reduce delivery costs while improving viewer experience. KeyFrame operates on standard servers in the cloud or on-premises, integrating into existing encoding pipelines without re-architecture. It was originally developed by Digital Harmonic and Vecima became an exclusive global partner.

### Broadband Access — Entra Platform
Vecima's cable and fiber access hardware (primarily for MSO/telco customers): R-PHY and R-MACPHY remote nodes for DOCSIS 3.1 and DOCSIS 4.0 networks, XGS-PON fiber OLT solutions (EXS1610 All-PON Shelf), Fiber Remote OLTs (SF-4x), the vCMTS (Virtual Cable Modem Termination System) for cloud-native cable access, and management software including Entra Access Controller, Entra vPON Manager, and Entra R-PHY Monitor. Vecima has been named Global Market Share Leader in Remote Optical Line Terminals and Remote MACPHY by Dell'Oro Group for five consecutive years.

### Commercial Video — Terrace Platform
Secure, cost-effective delivery of bulk video services to commercial properties (hotels, multi-dwelling units, hospitals). Includes the Terrace IQ (intelligent head-end for IP-to-QAM conversion with dynamic ad insertion and revenue generation capabilities), Terrace IQ 2, Terrace QAM, and TC600E encoder.

## Solutions & Use Cases
- **IP Linear TV Delivery:** Operators replacing legacy QAM systems with IP-based ABR delivery — MediaScale handles the full conversion and delivery pipeline.
- **Cloud DVR & nDVR:** High-volume simultaneous recording and playback for large subscriber bases; MediaScale Storage handles the write/read concurrency requirements.
- **Timeshift TV (Start-Over, Catch-Up):** Origin and Cache work together to enable lookback services without individual subscriber recordings.
- **VOD Catalog Delivery:** Large-scale library delivery with edge caching optimized for the long-tail of VOD content access patterns.
- **Live Sports Streaming:** KeyFrame specifically targets sports content where perceptual quality breaks down under compression; Open CDN reduces public CDN egress cost for high-traffic live events.
- **Multi-CDN Open Caching:** Operators using Open CDN can delegate traffic from content providers via open standards, reducing dependence on single public CDN vendors.
- **DOCSIS 4.0 & Fiber Access:** MSOs upgrading from DOCSIS 3.1 to DOCSIS 4.0 (multi-gigabit symmetrical) and fiber operators deploying XGS-PON.

## Technology & Architecture
MediaScale is a software-defined, COTS-based platform — all components run on standard x86 server hardware (with GPU support for transcoding), avoiding proprietary appliance costs. The architecture follows a modular, scalable design where Origin, Cache, Transcode, and Storage can be deployed independently or together, scaled horizontally, and placed anywhere in the network topology (centralized, regional, or edge).

Open CDN implements the SVTA Open Caching protocol stack, which defines standard APIs for Content Provider traffic delegation (telling content owners to steer traffic to the Open CDN), Cache Configuration Management (telling cache nodes what to cache and how), Observability and Logging (standardized CDN log formats for monitoring), and Content Management (invalidation and pre-positioning). Vecima co-authors these specifications and is driving them toward IETF RFC status.

KeyFrame uses a generative AI model trained on high-quality video data to perform learned super-resolution and quality enhancement on compressed or degraded source video. It processes video frames at the pre-encoder stage, making the transcoder's input cleaner and more detailed — so the same encoder settings produce higher VMAF scores, or identical quality can be maintained at lower bitrates. The model has been specifically trained on sports content to handle the distinct visual challenges (motion estimation, texture degradation, grain, camera shake).

## Key Differentiators
- **Five-year consecutive global market share leadership** in Remote OLTs and Remote MACPHY (per Dell'Oro Group) — meaningful credibility for cable operators evaluating access hardware.
- **SVTA Open Caching implementation:** One of the only commercial deployments of the Open Caching standard, giving MSOs a standardized, non-proprietary alternative to building private CDN relationships with each content provider.
- **COTS-based transcoding:** Running video processing on standard GPU/CPU servers rather than proprietary video appliances reduces capital expenditure and locks-in risk for operators.
- **KeyFrame pre-encoder AI:** Generative AI video quality improvement without re-architecting the encoding pipeline — a "no-regrets" deployment model that delivers ROI through bitrate savings or quality improvement.
- **Served 100+ million end-users globally** across the MediaScale content distribution customer base.
- **50 Tbps peak streaming capacity** across the MediaScale platform.
- **Charter Communications selected Vecima's Entra vCMTS** for next-generation DOCSIS network — a high-profile tier-1 MSO validation.

## Notable Customers & Integrations
**Customers:** Charter Communications, Cox Communications, Liberty Global, Comcast, Shaw, NOS, Astound Broadband, Vodafone, Millicom, JCOM, Blue Ridge Communications, Hotwire Communications, Telenet Belgium, TDS Telecom, LiWest (Austria), Mediacom

**Integrations:** AWS (cloud-based deployment), Cisco (supply agreement), IP ABR (HLS/DASH/CMAF), QAM VoD Pump, Origin Shield Caching, Google CDN technology (Terrace IQ feature set), Cadent (dynamic ad insertion partnership for video service providers), Incognito (XGS-PON provisioning), Digital Harmonic dh/KeyFrame (exclusive global partner)

## Pricing
Contact sales — pricing not publicly stated. Enterprise contracts for hardware and software licensing.

---

## Blog & Resources Highlights
_Curated from actual article content on the Vecima blog_

### How Generative AI is Transforming Live Sports Streaming Optimization — March 2026
> Vecima's Senior Director of Product and Innovation Nick Dunkin examines why traditional bitrate ladder optimization is reaching its limits for live sports — where fast motion, complex textures (grass, ice, crowds), and inconsistent source feeds create quality inconsistencies that codecs handle poorly. The article introduces KeyFrame as a bump-in-the-wire solution that applies generative AI upstream of the encoder to reconstruct lost detail, reduce noise, and improve VMAF scores. Key claim: operators can hold bitrates flat or reduce them while improving perceived quality, directly impacting delivery costs. Positions KeyFrame as fitting existing pipelines without re-architecture.
[Read more](https://vecima.com/generative-ai-impact-on-sports-streaming-optimization/)

### Open Caching Comes Alive at NAB Show 2025 with Open CDN — April 2025
> Vecima's Principal Software Engineer Ben Rosenblum reports from NAB 2025 on the state of Open CDN deployments and SVTA specification progress. Covers recent publication of the Logging specification (standardizing how CDN cache nodes report analytics to content providers), the Configuration Management Interface v2.0, and the new Open Casting project extending Open Caching to multicast. Notes that IETF CDNI working group submissions — including the Capacity Insights Interface — are approaching RFC publication. Confirms Vecima's active co-authorship role in these standards bodies.
[Read more](https://vecima.com/open-caching-comes-alive-at-nab-show-2025-with-open-cdn-plus-new-developments-from-the-svta/)

### Multi-CDN Observability: An Introduction to the Open Caching Logging Specification — 2024
> Co-authored with Nick Dunkin, this post (also presented at SCTE TechExpo 2024) covers the challenge of monitoring multiple CDNs in a standardized way, which the Open Caching Logging specification addresses. Explains how content providers today must build bespoke integrations for each CDN's proprietary log format — a problem the standardized Logging spec resolves by defining common field names, delivery event types, and transport mechanisms.
[Read more](https://vecima.com/multi-cdn-observability-an-introduction-to-the-open-caching-logging-specification/)

### Build a Converged Network That Is AI-Ready from Day One — 2025
> Vecima's CTO Colin Howlett argues for designing cable and fiber access networks with AI-ready compute capacity built into the edge infrastructure from initial deployment, rather than retrofitting later. Covers the architectural implications of placing AI inference capacity in distributed access nodes vs. centralized cloud, and how DOCSIS 4.0 and XGS-PON deployments can be planned with future AI workloads in mind.
[Read more](https://vecima.com/build-a-converged-network-that-is-ai-ready-from-day-one/)

### What's Next for Cable Broadband — January 2026
> CTO Colin Howlett reviews the major cable access trends heading into 2026: continued DOCSIS 4.0 deployment momentum, XGS-PON expansion, the convergence of cable and fiber access in all-PON network architectures, and the growing importance of software-defined, cloud-native network management. Positions Vecima's Entra platform as covering both the cable-to-fiber transition and the software-defined network management layer needed for operators managing hybrid topologies.
[Read more](https://vecima.com/2026-cable-trends/)

---

## Key Takeaways
- **MediaScale is the content distribution platform most MSOs don't know by name:** Vecima powers the video delivery infrastructure behind cable operators serving tens of millions of subscribers — making them a deeply embedded but often invisible part of the streaming supply chain.
- **Open CDN is a strategic standards play:** By implementing the SVTA Open Caching spec and co-authoring the standards, Vecima is positioning itself as the infrastructure vendor for an emerging "CDN inside the ISP" model — potentially allowing content providers to bypass public CDN costs for cable-subscriber audiences.
- **KeyFrame is the streaming-focused product at NAB 2026:** The generative AI pre-encoder optimization is Vecima's most visible streaming-industry play — relevance is highest for broadcasters and streaming platforms dealing with inconsistent source quality or high delivery bitrates.
- **Publicly traded with tier-1 MSO customers:** Charter Communications selecting Vecima's vCMTS is enterprise-grade validation that carries weight in an industry where operator relationships take years to develop.
- **Dual identity:** Vecima is simultaneously a cable access hardware company and a video software platform company — the streaming summit context is about their content distribution and AI optimization offerings, not their cable modem hardware.
