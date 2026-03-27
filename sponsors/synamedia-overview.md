# Synamedia — Overview

> Video Experience Solutions

## What They Do
Synamedia provides a broad portfolio of video infrastructure and intelligence software for pay-TV operators, broadcasters, streaming services, and sports rights holders. Their products span the entire video delivery chain — from satellite and IP contribution, through cloud-native distribution and streaming, to targeted advertising, content protection, and broadband device management. Synamedia's particular strength is in the hardest operational problems: delivering live sports without failure, enabling unified ad campaigns across broadcast and streaming simultaneously, and protecting premium content from piracy with forensic watermarking.

## At a Glance
- **Website:** [synamedia.com](https://www.synamedia.com)
- **Industry:** Video Infrastructure Software / Broadcast Technology
- **Stage/Positioning:** Private company; operates globally across pay-TV, broadcast, and streaming segments; extensive patent portfolio and 30+ years of accumulated video technology IP

## Products & Services

### Quortex Platform (Cloud Video Distribution & Streaming)
Synamedia's cloud-native video distribution suite, acquired and fully integrated as the core of their streaming portfolio:

- **Quortex Play:** Just-In-Time Cloud Streaming at Scale. Delivers live streams to millions using a pay-as-you-stream elastic infrastructure model — spin up for an event, tear down when it ends, pay only for what's used. Provides near-broadcast-quality latency and instant cloud-based disaster recovery path activation.

- **Quortex Link:** One-click cloud distribution for live video. A SaaS platform handling single-input/multi-output distribution workflows for live events — receiving one live feed and simultaneously delivering to social platforms, OTT services, satellite uplinks, and digital partners in any required format. A major North American sports league used Quortex Link to distribute 1,000+ live events per season; deployment was completed in under two weeks.

- **Quortex Switch:** The industry's first SaaS multi-CDN management platform. Intelligently steers live streaming traffic across CDN providers in real time based on performance signals, optimizing cost and reliability simultaneously. Consumes CMCD v2 telemetry directly from players as steering input, creating a closed-loop: player telemetry → steering decision → CDN selection → player outcome.

- **Quortex PowerVu:** Empowers broadcasters to securely manage affiliate distribution globally — handling conditional access, encryption, and delivery to affiliate networks worldwide.

### Fluid Edge CDN
A scalable edge CDN solution designed for pay-TV operators and broadcasters who want visibility and control over CDN demands without losing cost predictability. Features 100+ pre-configured dashboards for total operational visibility. Supports elastic scaling to cloud or multi-CDN when on-prem capacity is exceeded. Available as self-operated, fully managed, or build-operate-transfer (BOT) models.

### Virtual DCM (vDCM)
Software-based replacement for traditional broadcast hardware (Digital Content Manager appliances):
- **vDCM Encoder:** Software-based encoding/transcoding delivering exceptional picture quality at all bitrates
- **vDCM Packager:** Packages, secures, and distributes media content via ABR streaming (HLS, DASH, CMAF)
- **vDCM Recorder:** Service-oriented management for video network solutions
- **Media Edge Gateway (MEG):** Handles real-world broadcast requirements including BISS-CA reception (successfully tested with Eurovision Services for premium sports feeds), satellite/IP contribution, and regional ad splicing

### Senza (Cloud-Powered TV Platform)
Transforms any screen — including low-cost HDMI sticks — into a cloud-rendered TV experience. Senza eliminates the device-centric TV model (quarterly firmware releases, 5-7 year device cycles, heavy middleware) by moving UI rendering to the cloud and operating TV like a web service: continuous deployment, feature flags, A/B testing, and telemetry-driven product decisions. Enables telcos, pay-TV operators, and hospitality TV systems to compete with streaming services on UX velocity without hardware lock-in.

### Iris (Unified Advertising Platform)
Creates, manages, and delivers targeted, unified ad campaigns simultaneously across both broadcast (linear TV) and streaming (OTT/digital) inventory. Addresses the fundamental fragmentation of TV advertising: different systems, measurement standards, and demand paths for linear vs. digital. Iris enables:
- Addressable advertising on traditional broadcast inventory via regional DAI
- Unified campaign management and reporting across both delivery paths
- Programmatic connections to digital demand partners
- Attribution and measurement across the combined linear+streaming audience

### Synamedia Go (SaaS OTT Platform)
An open, flexible, modular SaaS platform for launching and operating streaming services. Includes Go Aggregate (AI-driven metadata aggregation for content discovery), Go Recommend (content recommendation engine), flexible access control, and subscriber management. Designed for operators who want to differentiate their streaming service without building custom platform infrastructure.

### ContentArmor (Forensic Watermarking)
Advanced forensic watermarking for content protection. Embeds invisible, imperceptible identifiers in video streams that persist through screen recording, re-encoding, and format changes. Used to identify the source of pirated content leaks, enabling rights holders to take down pirated streams and pursue legal action. Particularly important for live sports and premium content where piracy has immediate revenue impact.

### Gravity (Broadband Device Management)
A fully integrated solution for managing business broadband subscribers — email, domain, office SD-WAN, firewall, and remote access — targeting SMB broadband customers of telco operators.

## Solutions & Use Cases
- **Live Sports Distribution:** Reliable, elastic distribution of 1,000+ live events per season with instant failover and multi-destination delivery
- **Cloud DVR:** Network-based recording and time-shifted viewing at scale, with rising hardware cost management as a critical operational concern
- **Satellite to IP Migration:** Gradual transition from traditional satellite distribution to IP workflows using Quortex Link as a backup then primary path
- **Multiview:** Delivering multiple simultaneous live feeds with synchronized, monetizable low-latency infrastructure for sports betting compatibility
- **Unified Advertising:** Combining linear and streaming ad sales under a single workflow to increase revenue across fragmented inventory
- **Content Protection:** Forensic watermarking for piracy investigation and leak source identification for premium live sports rights holders
- **ATSC 3.0 / NextGen TV:** Support for ATSC 3.0 broadcast delivery alongside IP/OTT delivery

## Technology & Architecture
Synamedia's technology stack spans both legacy broadcast infrastructure and modern cloud-native systems. The vDCM product line translates traditional hardware-appliance broadcast workflows into software — the same proven broadcast-quality video processing, but running on standard servers or cloud VMs. This approach is critical for operators who cannot tolerate the risk of replacing proven broadcast infrastructure but need the flexibility of software deployment.

The Quortex platform is cloud-native from the ground up, built on Kubernetes-based microservices that enable the pay-as-you-stream model. Just-In-Time infrastructure provisioning means a Quortex Play deployment spins up cloud compute resources when a live event begins and tears them down when it ends — a structural cost advantage over always-on hardware for event-based content.

Quortex Switch's multi-CDN management relies on real-time telemetry ingestion. The CMCD v2 integration is notable: rather than relying on proprietary player SDKs or CDN-specific metrics, Quortex Switch consumes standards-based player telemetry (startup time, rebuffer patterns, bitrate stability) via the emerging CMCD v2 specification, creating a more interoperable and less vendor-locked control loop.

Fluid Edge CDN's elastic scaling model enables on-prem CDN infrastructure to burst to cloud CDN capacity during demand spikes — avoiding over-provisioning for peaks while maintaining control over baseline costs.

ContentArmor watermarking is designed to be imperceptible to viewers and robust against common piracy techniques: screen capture, re-encoding, filtering, and even screen regrabs through camera. The forensic information embedded is sufficient to identify the specific session (and therefore the subscriber or affiliate) responsible for a leak.

## Key Differentiators
- **Event-based, elastic pricing model:** Quortex Play's pay-as-you-stream approach eliminates the always-on infrastructure costs of traditional CDN or playout systems for event-heavy workflows — a structural advantage for sports rights holders and event distributors
- **Broadcast-to-cloud transition expertise:** Synamedia sits at the rare intersection of deep broadcast hardware knowledge (vDCM, MEG) and cloud-native streaming (Quortex suite) — enabling gradual migrations that don't force customers to choose between broadcast reliability and streaming flexibility
- **Unified linear + digital advertising:** Iris is one of very few products that genuinely addresses the convergence of broadcast and streaming ad systems from a single management layer — relevant as advertisers increasingly demand reach measurement across both
- **CMCD v2 as an open telemetry standard:** Synamedia is actively building Quortex Switch around the emerging CMCD v2 specification rather than proprietary metrics, a forward-looking standards bet that could reduce ecosystem fragmentation
- **Forensic watermarking depth:** ContentArmor's imperceptible, piracy-resilient watermarking is mission-critical infrastructure for premium live sports rights holders dealing with organized piracy at scale

## Notable Customers & Integrations
**Customers:** Sky, Astro, beIN Sports, Vodafone, Yes (Israel), Etisalat/E-Vision, Czech TV (Česká Televize), Pitch International, Globecast, RAS, Eurovision Services, MoMe

**Partners:** AWS (primary cloud infrastructure partner), HPE (hardware partner), Accenture (Senza SI partner)

**Integrations:** BISS-CA (broadcast contribution), ATSC 3.0 (NextGen TV), CMCD v2 (player telemetry), HLS/DASH/CMAF, Widevine/PlayReady/FairPlay DRM, programmatic ad demand platforms, multi-CDN steering

## Pricing
Contact sales — pricing not publicly stated. Quortex products follow a pay-as-you-stream model (usage-based). Fluid Edge CDN and vDCM are licensed; professional/managed services available. ContentArmor and Iris are priced separately.

---

## Blog & Resources Highlights
_Curated from Synamedia's blog (synamedia.com/resources/blog)_

### CMCD v2: Should Proprietary Metrics Providers Be Worried? — March 10, 2026
> Synamedia's Robin Oakley (ex-DAZN VP of Distribution Engineering) argued that CMCD v2's multi-mode reporting — particularly event-mode signaling that decouples telemetry from segment requests — could meaningfully reduce the fragmentation of OTT streaming operations. Currently, CDN metrics, player analytics, QoE scoring, and steering logic all live in separate systems with different schemas. CMCD v2 opens the possibility of standards-based session intelligence flowing directly into CDN steering decisions. Synamedia's Fluid Edge CDN already consumes CMCD; Quortex Switch now ingests CMCD v2 directly as steering input.
[Read more](https://www.synamedia.com/blog/cmcd-v2-should-proprietary-metrics-providers-be-worried/)

### Win the Sports Streaming Game! Part 1: When Live Sports Cannot Fail — January 21, 2026
> Synamedia's Cyrille Berson described two real customer deployments. A major North American professional sports league distributes 1,000+ live events per season to OTT platforms, social media, and internal systems simultaneously; Quortex Link was deployed in under two weeks, with Quortex Play providing instant cloud-based disaster recovery. A UK football cup competition distributor migrated from satellite to IP delivery using Quortex Link as a backup path — operational in less than two days — and after a successful first season, renewed for a second year as the primary delivery path.
[Read more](https://www.synamedia.com/blog/live-sports-streaming-reliability-at-scale/)

### 2026: The Year TV Stops Being a Platform and Becomes a Web Service — January 19, 2026
> Synamedia's Lionel Adam made a detailed case that TV's device-centric model (quarterly firmware releases, 5-7 year device cycles) is incompatible with the web's operating model (continuous deployment, A/B testing, telemetry-driven product decisions). The article identifies 2026 as the inflection year where TV platforms that still optimize around device roadmaps are "optimizing the wrong constraint." The Senza cloud-rendered UI platform is positioned as the answer: TV operated like a web product, continuously iterated and deployed, with EPG replaced by AI-driven personalized decision engines.
[Read more](https://www.synamedia.com/blog/2026-the-year-tv-becomes-web-services/)

### 2026: Multiview's Inflection Point Has Arrived — February 4, 2026
> Synamedia's VP of Product Management Elke Hungenaert analyzed the commercial readiness of multiview streaming in 2026 — arguing that 2026 FIFA World Cup, Super Bowl, and Winter Olympics create the tentpole events that will stress-test multiview infrastructure at unprecedented scale while proving its revenue model. The article identifies two unresolved challenges: rights management complexity (NFL/NBA brand adjacency concerns) and advertising valuation models (how to price CPM when an ad occupies one quadrant of a four-way split). Sports betting integration is identified as the highest-value monetization use case, requiring sub-second latency synchronization across all feeds.
[Read more](https://www.synamedia.com/blog/multiview-streaming-2026-revenue-inflection-point/)

### The Future of Video Processing Is Software: Why Now Is the Moment to Move to vDCM — December 11, 2025
> Synamedia made the case for migrating from hardware DCM appliances to Virtual DCM software — arguing that hardware cycles have become a strategic liability as software-defined infrastructure enables faster feature iteration, cloud deployment flexibility, and resilience through software redundancy rather than hardware redundancy. The post acknowledged that the DCM appliance has been a "trusted workhorse for decades" while making the economic and operational case for the transition to vDCM, with Synamedia providing migration support.
[Read more](https://www.synamedia.com/blog/the-future-of-video-processing/)

---

## Key Takeaways
- **The only vendor bridging traditional broadcast and cloud-native streaming at depth:** Synamedia's product portfolio spans satellite contribution (MEG/BISS-CA), broadcast distribution (vDCM), cloud playout (Quortex Play), and cloud-native UI (Senza) — enabling migrations that don't force a wholesale replacement of proven infrastructure
- **Live sports is the marquee use case:** The Quortex Play/Link event-based model — spinning up cloud compute for a game, tearing it down after — is architecturally optimized for sports rights holders and distributors whose costs should scale with events, not infrastructure
- **Unified advertising is a genuine differentiation:** Iris bridges linear broadcast and streaming ad systems in a single campaign management workflow — addressing the fragmentation that costs broadcasters revenue when digital advertisers can't buy across both simultaneously
- **Cloud-rendered TV is a bold strategic bet:** Senza's approach — rendering the TV UI in the cloud rather than on the device — is a fundamental architectural shift; if it succeeds, it breaks the device upgrade cycle that has constrained TV innovation for decades
- **Deep pay-TV and broadcast DNA:** Customers like Sky, beIN Sports, Astro, and Etisalat represent some of the most demanding operators in the world; Synamedia's breadth of deployment in premium broadcast environments is a proof point few competitors can match
