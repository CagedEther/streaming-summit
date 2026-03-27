# CDN77 — Overview

> Unmatched CDN performance at the best prices, powered by a 290 Tbps network across 6 continents

## What They Do
CDN77 is a global content delivery network provider with a deliberate focus on video delivery — 90% of their delivered data is video traffic. They operate a high-capacity private backbone network with embedded PoP infrastructure inside ISP networks, and offer an expanding stack that includes content delivery, media processing, object storage, edge computing, and security. Their market positioning is built on aggressive performance-to-price ratios, transparent pricing, and direct access to engineering support — positioning themselves as an alternative to larger, more expensive enterprise CDN providers like Akamai and Fastly.

## At a Glance
- **Website:** https://www.cdn77.com
- **Industry:** Content Delivery Network / Cloud Infrastructure
- **Stage/Positioning:** Private company (operated by DataCamp Limited); reported annual revenue of $218M in 2025; profitable and growing for over a decade

## Products & Services

### Content Delivery Network Services
The core CDN product handles HTTP objects, live streaming, adaptive media delivery, HTTP-FLV, and private CDN configurations. The network spans 380+ edge PoPs in 200 locations across 130 countries, with 290 Tbps total capacity and daily traffic peaks reaching 80 Tbps. The network includes Super PoPs (strategically placed high-capacity nodes with private peering) and an Embedded PoP program (custom cache appliances deployed inside ISP networks, reducing external traffic by 60–90% for cacheable content). Live streaming delivery achieves under-5-second latency. Adaptive Media Delivery dynamically adjusts bitrate to network conditions in real time.

### Video CDN (Media-Specific)
A purpose-built delivery configuration for VOD and live video platforms. Supports MP4, HLS, MPEG-DASH, and CMAF playback across all platforms and devices. Includes: multi-layer caching to achieve 98%+ cache hit ratios, latency-based routing, DVR and timeshift functionality, live stream processing over RTMP/RTSP/HLS/MPEG-DASH/MPEG-TS ingest protocols, and an HTML5 video player with audience analytics. On-the-fly encoding and transcoding of VOD content is also supported.

### Media Processing Services
A full video pipeline stack from ingest to playback: Video Origin Services (origin infrastructure optimized for media workflows), Video Encoding (transcode and package to HLS/DASH for web and mobile), Video Processing (screenshots, DVR windows, timeshift), and a customizable HTML5 Video Player with DRM support and analytics integration.

### Security
Proprietary L3/L4 DDoS protection that mitigates attacks in under 10 seconds. Content protection features include token-based access, IP/geo-blocking, referrer restrictions, Multi-DRM, and SSL. Origin Shielding uses mid-tier caching to protect origin servers from direct traffic. CDN77 operates its own in-house DDoS mitigation system rather than relying on third-party scrubbing.

### Cloud Computing & Edge Infrastructure
S3-compatible Object Storage (no egress fees between storage and CDN77 delivery), Dedicated CPU servers, High Bandwidth + CPU Services, Kubernetes Container Engine (optimized for edge workloads), Edge Computing (deploy custom functions across the globally distributed edge), Edge Intelligence (real-time detailed log streaming, Hydrolix-compatible), Edge Insights (unified API for real-time analytics), an Observability Platform for high-volume log analysis, and Private AI Infrastructure with GPU-accelerated compute for AI/ML workloads.

### Private CDN
A fully dedicated CDN infrastructure option — dedicated caching layers, full control over capacity, routing, performance, and security — for customers who need guaranteed infrastructure separation.

## Solutions & Use Cases
- **Live Sports & Events Streaming:** High-capacity live delivery with sub-5-second latency and support for RTMP/MPEG-TS ingest from broadcast feeds.
- **VOD Platform Delivery:** Multi-layer cache architecture to achieve 97%+ cache hit ratios even for long-tail content libraries (e.g., educational platforms with extensive archives).
- **OTT/SVOD Services:** Full-stack video delivery from origin to viewer, with encoding, packaging, DRM, and delivery in a single vendor relationship.
- **Gaming CDN:** Optimized delivery of large game files, patches, and updates to global audiences.
- **E-commerce & High-Traffic Web:** HTTP objects and dynamic content delivery for latency-sensitive web applications.
- **Enterprise Secure Content:** Token-based access control, geo/IP restrictions, and SSL for premium or gated content.

## Technology & Architecture
CDN77's network architecture is built around two tiers. **Super PoPs** are large, highly-interconnected facilities in major internet exchange points, connected to thousands of ISPs via settlement-free private peering (PNI). **Embedded PoPs** are custom-built cache appliances deployed physically inside ISP networks — when a subscriber requests content, it's served from inside the ISP rather than over external links, cutting round-trip time and eliminating upstream congestion. This reduces external transit by 60–90% for cacheable content and lowers ISP peering costs simultaneously.

For low-latency live streaming specifically, CDN77 uses chunked transfer encoding to begin serving segments to clients before they're fully written to disk — enabling sub-100ms segment availability windows rather than waiting for full segment completion. Their custom Nginx implementation (overriding native Nginx's inability to cache in-progress files) is a specific technical differentiator for LL-HLS and LL-DASH workflows. For QUIC/HTTP/3, CDN77 runs experiments using the Google Quiche library across PoPs in four regions and has published research showing BBRv1 outperforms BBRv2 in European and North American deployments for dynamic content delivery.

The multi-layer cache architecture (L0/L1/L2) is specifically designed for long-tail VOD content — where standard CDNs fail because no individual file generates enough requests to cache effectively. CDN77's solution sets progressively lower caching thresholds at each layer, so even files requested once per day are served from edge rather than origin, keeping overall hit ratios above 97%.

## Key Differentiators
- **Video-first architecture:** 90% of traffic is video; the network, caching, and latency optimization strategies are tuned specifically for streaming workloads, not generic web delivery.
- **Embedded PoP ISP program:** Deploying cache hardware inside ISP networks is a hardware-level differentiation that large cloud CDNs rarely offer; it reduces last-mile latency and transit costs for both CDN77 and the ISP.
- **Engineering-backed support model:** Direct access to L2/L3 engineers rather than tiered support queues; client-specific customizations included as standard. Response time under 60 seconds via live chat or Slack Connect.
- **Transparent, flat-rate pricing:** Flat overage fees and month-to-month plan flexibility — explicitly positioned against the high overage fees and rigid commitments of larger CDN providers. Growth Plan starts at $990/month for up to 250 TB.
- **Proprietary DDoS mitigation in-house:** Attack mitigation in under 10 seconds using a proprietary system — not reliant on third-party scrubbing services.
- **S3-compatible storage with zero egress fees** between CDN77 storage and CDN77 delivery — meaningful cost savings for video-heavy workflows where origin egress is a major cost line.

## Notable Customers & Integrations
**Customers:** STARZ, Rakuten TV, Udemy, ESL Gaming, Banijay, Sport1 (named in pricing/product pages)

**Integrations:** S3-compatible API for object storage, Kubernetes Engine for container workloads, HTML5 player SDK, Hydrolix (for Edge Intelligence log streaming), API access for all delivery, encoding, and processing services

## Pricing
- **Growth Plan:** $990/month for up to 250 TB of monthly traffic; full CDN feature access; 24/7 tech support
- **Enterprise Plan:** Custom pricing for high-volume or complex deployments; dedicated infrastructure, advanced VOD and live features, dedicated account specialist
- **Storage:** No egress fees between CDN77 Object Storage and CDN77 CDN delivery; separate storage pricing applies
- **Cloud Computing:** Custom pricing for Dedicated CPU, High Bandwidth + CPU, Kubernetes Engine, and GPU/AI infrastructure

---

## Blog & Resources Highlights
_Curated from actual article content on the CDN77 blog_

### Embedded PoPs Overview: Improving Our Last-Mile Capacity Through ISPs — September 2025
> CDN77's Head of Network Operations explains how Embedded PoPs work: custom-built cache appliances deployed physically inside ISP networks fetch content from CDN77's upstream infrastructure and serve it over HTTP/HTTPS, keeping traffic inside the ISP network. This reduces geographic round-trip time for the end user while simultaneously cutting the ISP's external transit and peering costs by 60–90%. The post details CDN77's global network and explains the partner program for ISPs interested in hosting an Embedded PoP.
[Read more](https://www.cdn77.com/blog/embedded-pops-overview)

### Low-Latency HTTP Live Streaming — February 2025
> A technical deep-dive by CDN77's Head of Livestream Engineering covering glass-to-glass latency in HLS and MPEG-DASH pipelines. The post defines "low latency" as under 5 seconds and "ultra-low latency" as under 1 second, and walks through optimizing each stage of the pipeline: shortening segment duration via chunked transfer encoding, solving index fetching with LL-DASH templates vs. Apple's LL-HLS partial segments, removing the read-ahead buffer and using ±5% playback speed adjustment to maintain live edge, and disabling transcoder look-ahead/B-frames. Notes that CDN77 built a custom Nginx implementation to support in-progress file caching — a capability native Nginx doesn't provide.
[Read more](https://www.cdn77.com/blog/low-latency-http-live-streaming)

### Tackling Long-Tail Content: How to Get the Cache Hit Ratio Above 97% — March 2021
> Explains the "long-tail problem" in CDN caching: for platforms like educational streaming services or large VOD libraries, content is distributed across thousands of titles, so no individual file reaches the threshold needed to be cached at the edge. CDN77's solution is a three-tier multilayer cache (L0: edge PoPs with high threshold, L1: regional data centers with lower threshold, L2: origin-adjacent servers caching everything requested even once). The cumulative hit ratio approaches 97%+ by ensuring that long-tail files are served from L2 rather than origin even if they never qualify for L0 caching.
[Read more](https://www.cdn77.com/blog/tackle-long-tail-with-multilayer-cache)

### Analyzing QUIC Traffic for Dynamic Content Delivery — 2025
> CDN77 Performance Engineer shares research on QUIC protocol (HTTP/3) performance for live streaming across four regional PoPs in North America, Europe, Middle East, and Asia. Using Google's Quiche library and real production traffic data from Q4 2024–Q1 2025, the study compares Cubic, BBRv1, and BBRv2 congestion control algorithms. Key finding: BBRv1 outperforms BBRv2 in Europe, North America, and the Middle East despite BBRv2's theoretical superiority; BBRv2 shows advantages in Asia. Notes that over 80% of QUIC-connected clients do not use stream multiplexing, suggesting video players haven't adopted this capability yet.
[Read more](https://www.cdn77.com/blog/analyzing-quic-traffic-for-dynamic-content-deliver)

### Benefits of SRT for Your Stream Explained — October 2020
> Covers the Secure Reliable Transport (SRT) protocol as a contribution/ingest protocol for live streaming. Explains how SRT builds on UDT's reliability mechanisms to deliver low-latency, encrypted transport over public internet links without sacrificing the reliability of dedicated fiber circuits. CDN77 was an early supporter of SRT, adding it to their video delivery solution as the protocol gained adoption for broadcast contribution workflows.
[Read more](https://www.cdn77.com/blog/benefits-of-srt-for-your-stream-explained)

---

## Key Takeaways
- **Built specifically for video:** CDN77 is not a general-purpose cloud CDN that also does video — 90% of their traffic is video, and every infrastructure decision (Embedded PoPs, multi-layer cache, low-latency Nginx, CMAF support) reflects this focus.
- **The Embedded PoP program is a structural moat:** Physical hardware inside ISP networks is difficult to replicate quickly and creates routing advantages that software-only CDN competitors cannot match.
- **Price-to-performance is the explicit positioning:** At $990/month for 250 TB and flat overages, CDN77 is directly competing against enterprise CDN pricing structures from Akamai, Fastly, and Cloudflare — and publishing comparison pages for each.
- **Engineering culture bleeds into the blog:** Technical posts on QUIC congestion control, LL-HLS vs. LL-DASH tradeoffs, and multilayer cache topology reveal a company where engineers drive product decisions — relevant credibility for technically sophisticated video teams.
- **Growing into a full edge platform:** The addition of GPU-accelerated Private AI Infrastructure, Kubernetes edge compute, and Hydrolix-compatible log streaming signals CDN77 expanding from pure delivery into edge-cloud infrastructure — positioning for the AI inference-at-edge market.
