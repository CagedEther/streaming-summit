# Broadpeak — Overview

> This is streaming at its peak

## What They Do
Broadpeak develops CDN and video streaming technology for video service providers — telcos, cable operators, satellite operators, and OTT platforms — enabling them to deliver live and on-demand video at scale with high quality of experience. They solve the hardest infrastructure problems in streaming: taming live event traffic spikes, reducing latency to broadcast-like levels, enabling personalized ad insertion across millions of simultaneous streams, and protecting CDN infrastructure from piracy. More than 200 companies use Broadpeak to reach over 250 million viewers in 50 countries.

## At a Glance
- **Website:** [broadpeak.tv](https://broadpeak.tv)
- **Industry:** Video Streaming Infrastructure / CDN Technology
- **Stage/Positioning:** Publicly listed on Euronext Growth Paris; French company with global deployment footprint

## Products & Services

### Advanced CDN
Broadpeak's full-featured content delivery network solution for video service providers. Supports live TV, catch-up, VOD, start-over TV, and cloud DVR delivery. Built for operator environments with support for QoE monitoring, segment caching, and origin shielding. Can be deployed on bare metal, virtualized, or cloud infrastructure.

### EdgePeak (High Performance Cache)
A software-defined, high-performance CDN cache engine built from scratch for operators who want to build or augment their own CDN. Benchmarked to serve up to 1 Tbps of throughput per server — claimed as the highest-density CDN cache on the market for a given hardware platform. Enables "Build Your Own CDN" deployments without proprietary hardware lock-in.

### Multicast ABR (nanoCDN)
Broadpeak's flagship, patented technology for delivering ABR (adaptive bitrate) streaming over IP multicast networks. It combines the unicast convenience of HLS/DASH with the broadcast efficiency of traditional IPTV, sending a single multicast stream to many subscribers simultaneously — eliminating the N×bandwidth problem during live events. Originally deployed for IPTV operators migrating to OTT, it has been adopted commercially by operators including Emtel/MC Vision (world's first commercial deployment), Cellcom, and Starhub. Reduces bandwidth costs dramatically during simultaneous live events.

### Origin Packager
Packages and protects video content for distribution, supporting both HLS and DASH formats, DRM encryption (Widevine, PlayReady, FairPlay), and simultaneous unified packaging/encryption of both manifest formats in a single pass. Handles time-shifted TV, cloud DVR, and VOD packaging workflows.

### Cloud DVR
Network-based DVR solution allowing operators to offer petabyte-scale recording services without set-top box storage. Handles content ingest, storage, and personalised playback at cloud scale, with trick play (rewind, fast-forward, pause live TV) support.

### broadpeak.io (SaaS Platform / CDN Selection)
A cloud-native SaaS offering for content providers and operators. Includes CDN selection (intelligent multi-CDN routing based on real-time QoE signals), virtual channel creation, ad insertion, and origin services. Enables content providers to access Broadpeak's technology without deploying on-premise hardware.

### bkyou (Content Personalization & Ad Insertion)
Broadpeak's server-side ad insertion and content personalization solution. Enables targeted advertising within live streams and VOD by stitching ads directly into the manifest server-side, making them compatible with any ABR player and immune to client-side ad blockers. Supports DAI (dynamic ad insertion) workflows at scale, with integrations into third-party ad decisioning systems. Certified for VMware Telco Cloud.

### CDN Security & Anti-Piracy
Security layer protecting video CDNs from credential abuse, token scraping, illegal restreaming, and bandwidth theft. Works both within Broadpeak CDN infrastructure and — through multi-CDN-compatible approaches — alongside third-party CDN edge caches.

### Multiview
Server-side multiview architecture using a "multi-package" approach that composes viewer-chosen Multiview layouts at the packaging layer rather than the encoder or client. A single output stream is assembled server-side from independently selectable video regions, enabling flexible viewer configurations (multiple angles, multiple games) without multiplying encoding tasks or requiring multi-player setups on device.

### S4Streaming
A groundbreaking ABR network control technology that significantly improves video QoE by enabling the network to actively assist ABR adaptation decisions — rather than leaving the player to adapt blindly. Tested against client-side algorithms, it enables more stable bitrate selection and faster quality recovery.

## Solutions & Use Cases
- **Live Sports at Scale:** Delivering high-volume live events (FIFA World Cup, Olympics) without bandwidth implosion via Multicast ABR and intelligent CDN orchestration
- **IPTV to OTT Migration:** Helping operators transition linear TV delivery to ABR while maintaining broadcast-grade QoE and low latency
- **Targeted Advertising:** Enabling addressable TV on live channels and VOD via server-side ad insertion across millions of simultaneous streams
- **5G Video Delivery:** Leveraging 5G edge compute for optimized mobile video streaming and low-latency delivery at the edge of cellular networks
- **Multi-CDN Management:** Routing live and VOD traffic intelligently across multiple CDN providers based on real-time QoE performance
- **Cloud DVR / Time-Shifted TV:** Enabling catch-up TV, start-over, and personal cloud recording at operator scale
- **Piracy & Fraud Protection:** Securing CDN infrastructure from live stream theft, token abuse, and illegal redistribution

## Technology & Architecture
Broadpeak's technology stack spans the origin-to-edge delivery chain. At the origin, the packager handles simultaneous HLS and DASH manifest generation and DRM encryption in a single unified pass — a proprietary capability that reduces infrastructure overhead. The CDN layer uses Broadpeak's high-performance EdgePeak cache engine (written from scratch with hardware-aware architectural decisions) capable of 1 Tbps per server.

The Multicast ABR (nanoCDN) technology sits at the network layer, using IP multicast to deliver a single stream that can be received by compatible client devices (using an iWedia or similar HLS client), converting the multicast stream at the device edge into standard unicast ABR playback. This hybrid approach avoids the N×bandwidth scaling problem of pure unicast OTT for live events.

The S4Streaming ABR control technology operates between the CDN and the player, enabling the network to provide steering signals that guide ABR decisions — achieving more stable quality levels and faster recovery from congestion compared to purely client-driven adaptation.

For security, the FireCache project (EU-funded, in progress 2026) is integrating WAF-grade security and AI-driven anomaly detection directly into the EdgePeak cache engine — eliminating the need for separate security appliances and applying detection at full CDN throughput without competing for hardware resources.

For personalization, the bkyou platform handles manifest manipulation server-side, enabling regional channel replacement, targeted ad insertion, and content blackout/substitution — critical for operators managing multi-region broadcast rights.

broadpeak.io brings these capabilities to a SaaS delivery model for content providers who don't operate their own CDN infrastructure.

## Key Differentiators
- **Multicast ABR (nanoCDN):** Commercially deployed in production — not a lab concept. Enables massive live event delivery at cable/IPTV-grade efficiency over OTT infrastructure; no other vendor has the same track record of live deployments
- **EdgePeak cache performance:** 1 Tbps per server is an exceptional density benchmark; the architecture is designed to integrate security and analytics functions without adding overhead — a significant differentiator for cost-conscious operators
- **EU-backed R&D pipeline:** FireCache is an EU/BPI France/Région Bretagne funded project integrating AI-powered anti-piracy directly into CDN cache engines — evidence of a serious, long-horizon security R&D investment
- **Multi-CDN and SaaS flexibility:** broadpeak.io lets content providers access Broadpeak's capabilities without deploying hardware, while operator-focused products run on any infrastructure
- **Deep protocol expertise:** The MoQ (Media over QUIC) exploration and NAB 2026 demo signals genuine investment in next-generation low-latency streaming protocols — not just marketing positioning

## Notable Customers & Integrations
**Customers:** Claro, Liberty Global, Tata Sky, Izzi Telecom, Telus, Megacable, Now TV, Orange, Starhub, Deutsche Telekom/Magenta, TIM, Vodafone, Sky Brasil, Dish TV, Cellcom, Charter Communications, Cogeco, TotalPlay, Cetin, STC TV, Partner TV (Israel), Andorra Telecom, VTVCab

**Notable deployments:** World's first commercial Multicast ABR deployment (Emtel/MC Vision, Mauritius); FIFA World Cup Qatar 2022 streaming via broadpeak.io; Super Low Latency live sports with VO (UK)

**Ecosystem:** AWS Marketplace listing for CDN selection; VMware Ready for Telco Cloud certification; 3SS, Beenius, and Alpha Networks integrations; Kaltura partnership (Cetin deployment)

## Pricing
Contact sales — pricing not publicly stated. Products are available as on-premise hardware/software, virtualized/containerized deployments, or SaaS via broadpeak.io. Broadpeak is publicly listed, so annual revenue figures are reported.

---

## Blog & Resources Highlights
_Curated from Broadpeak's blog (broadpeak.tv/blog)_

### MoQ for Live Streaming at Scale: How to Transition — March 18, 2026
> Broadpeak published a detailed technical exploration of Media over QUIC (MoQ), the IETF-standardizing protocol for low-latency live media delivery over QUIC transport. Rather than advocating a full replacement of HLS/DASH, Broadpeak proposes a pragmatic "half MoQ relay" architecture that attaches a lightweight MoQ relay at the CDN cache level — letting existing ABR infrastructure co-serve both HLS/DASH and MoQ flows from the same cache. Early results were presented at Mile High Video; a full white paper is forthcoming. Live MoQ demos are being shown at NAB Show 2026 (Booth #W3034).
[Read more](https://broadpeak.tv/blog/moq-live-streaming-at-scale-how-to-transition/)

### Video Streaming Trends 2026: Execution Now Is Priority — February 6, 2026
> Broadpeak's detailed 2026 market analysis identifies five structural shifts reshaping the streaming industry: (1) Margins now outweigh growth — cost per streamed minute is tracked as closely as engagement; (2) Bundling is returning as app fatigue drives fragmentation pain; (3) Edge economics are forcing operators to take direct control of CDN delivery; (4) Advertising has overtaken subscriptions as the primary revenue engine, with AVOD/FAST/CTV growing fastest; (5) Piracy has become a delivery and cost problem — Parks Associates projects $113B in US content losses to piracy by 2027. The conclusion: platforms that survive 2026 are those that can handle scale, control costs, and maximize ad revenue simultaneously.
[Read more](https://broadpeak.tv/blog/video-streaming-trends-2026/)

### Multiview Streaming: More Choice for Viewers, Less Complexity for Platforms — March 2, 2026
> Broadpeak detailed its proprietary "multi-package" approach to multiview — a server-side architecture that composes viewer-selected layouts at the packaging layer rather than at the encoder or on-device. This avoids pre-encoding every possible layout combination (the multi-encode approach) while also avoiding the device resource overhead of multiple simultaneous video players. The system produces a single standard video stream for any combination of views, compatible with any player. Parks Associates data cited: over 50% of sports viewers find multi-game viewing appealing or very appealing.
[Read more](https://broadpeak.tv/blog/multiview-live-sports-flexibility-simplicity/)

### FireCache Project Awarded to Broadpeak, Almond, and University of Rennes — February 26, 2026
> Broadpeak announced receipt of EU, BPI France, and Région Bretagne funding for the FireCache project — a collaborative initiative with Almond (cybersecurity) and the University of Rennes (IRISA/WIDE team) to build high-performance security and anti-piracy solutions integrated directly into CDN cache engines. The approach embeds WAF, log parsing, anomaly detection, and AI-driven piracy pattern detection directly into EdgePeak's cache engine — using the same hardware resources rather than separate security appliances. The University of Rennes contributes novel Direct Server Return (DSR) techniques published at Usenix NSDI.
[Read more](https://broadpeak.tv/blog/firecache-project-on-video-cdn-security-and-anti-piracy/)

### Beyond Connectivity: Monetizing Networks at MWC 2026 — March 17, 2026
> Broadpeak reported on themes from Mobile World Congress 2026 related to operators looking to turn their network infrastructure into a monetization asset — not just a connectivity pipe. The discussion connected to Broadpeak's own positioning around edge delivery, targeted advertising, and 5G-enabled streaming as monetization levers for telecom operators competing with OTT platforms for both subscribers and advertising revenue.
[Read more](https://broadpeak.tv/blog/monetizing-networks-at-mwc-2026/)

---

## Key Takeaways
- **Infrastructure-layer specialist:** Broadpeak lives deep in the CDN and streaming delivery stack — it's not a consumer-facing platform but the engine powering QoE for hundreds of millions of viewers behind the scenes
- **Multicast ABR is a genuine competitive moat:** The only company with commercial Multicast ABR deployments at operator scale; addresses the live event bandwidth problem that pure unicast OTT cannot solve economically
- **Piracy is a core R&D focus:** The EU-backed FireCache project signals that Broadpeak is treating CDN security as a first-class infrastructure feature, not an afterthought
- **MoQ is the next protocol horizon:** Broadpeak is actively demonstrating live MoQ at NAB 2026 — one of the few vendors with working implementations, not just whitepapers
- **Critical infrastructure vendor for pay-TV and telco operators:** The customer list reads like a who's who of global telecom; Broadpeak is deeply embedded in the workflows of operators who cannot afford downtime during major live events
