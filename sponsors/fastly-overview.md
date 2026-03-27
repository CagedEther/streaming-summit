# Fastly — Overview

> Powering the best of the internet

## What They Do
Fastly operates a programmable edge cloud platform that powers the performance, security, and real-time delivery needs of the world's most demanding digital businesses. Their infrastructure sits between the internet and origin servers, accelerating content delivery via a globally distributed network while enabling developers to run custom logic at the edge. In the streaming world specifically, Fastly handles live video delivery, VoD streaming, media packaging, and multi-CDN optimization for major broadcasters and media companies — as well as the full security and bot protection stack that protects those properties.

## At a Glance
- **Website:** [fastly.com](https://www.fastly.com)
- **Industry:** Edge Cloud / CDN / Security / Edge Compute
- **Stage/Positioning:** Publicly traded (NYSE: FSLY); named a Leader in the 2026 Forrester Wave™ for Edge Development Platforms with 5/5 scores for performance and developer experience

## Products & Services

### Content Delivery (CDN)
Fastly's core CDN delivers dynamic and cacheable content globally from a network of high-capacity Points of Presence. Unlike traditional CDNs optimized around sheer PoP count, Fastly uses fewer but more powerful PoPs — a software-defined architecture that enables real-time configuration changes without waiting for cache propagation delays. Supports HTTP/3 & QUIC natively. Programmable via VCL (Varnish Configuration Language) or Compute (WebAssembly).

### Live Streaming
Fastly's live media streaming product handles massive concurrent viewer events for broadcasters and streaming platforms. The infrastructure is engineered for the thundering herd problem — when millions of viewers request the same manifest simultaneously at event start — with intelligent cache locking and connection management. Fastly offers dedicated Live Entertainment Services with hands-on engineering support for large events.

### Streaming Video (VoD)
Supports just-in-time transmuxing to popular streaming formats (HLS, DASH) for any resolution at any frame rate. Handles segment delivery with low-latency caching behaviors optimized for ABR player patterns, including intelligent handling of manifest refreshes.

### On-the-Fly Packager (OTFP)
Fastly's OTFP dynamically packages on-demand video content in real time from a single mezzanine file into any target format (HLS, DASH, CMAF) at request time — eliminating the need to pre-encode and store multiple format variants. Reduces storage costs and simplifies VOD workflows by maintaining one source asset.

### Media Shield
A multi-CDN optimization layer that acts as an intelligent caching shield in front of multiple downstream CDN providers or origins. Reduces origin egress costs and redundant requests to origin when running multi-CDN architectures, while maintaining consistent delivery quality across providers.

### Next-Gen WAF (Web Application & API Protection)
Fastly's Next-Gen WAF provides unified web app and API protection across any deployment environment — cloud, on-prem, hybrid. Differs from legacy WAFs by using a behavioral detection model that minimizes false positives without requiring constant rule tuning. Available as a cloud service, hybrid deployment, or agent on the edge.

### Bot Management
Detects and mitigates automated bot traffic including credential stuffing, account takeover, content scraping, and application DDoS. Includes AI Bot Management specifically designed to control and optionally monetize AI crawler traffic.

### DDoS Protection
Automated, always-on DDoS mitigation leveraging Fastly's network's massive bandwidth. Uses adaptive techniques to absorb and mitigate volumetric attacks without requiring configuration changes, keeping applications performant under attack. Fastly's Security Operations Center (CSOC) provides human-led response with a median 1-minute response time for critical incidents.

### Edge Compute (Fastly Compute)
A WebAssembly-based serverless compute platform that runs code at the edge — at every PoP in Fastly's network — in any major language (Rust, JavaScript, Go, etc.). Enables building custom delivery logic, A/B testing, authentication, personalization, and AI inference at the edge without managing servers. Named a Leader by Forrester for Edge Development Platforms.

### Websockets & Fanout
Real-time messaging and pub/sub at global scale. Enables WebSocket connections, live data feeds, IoT telemetry, and streaming APIs to be delivered from the edge — reducing latency and load on origin servers for real-time applications.

### Object Storage
Edge-native object storage with zero egress fees, available across multiple regions globally. Designed for direct access to large files at the edge — including video segments and media assets — without incurring traditional cloud egress costs.

### Instant Purge™
Fastly's signature capability: globally purging cached content in under 150ms, constrained only by the speed of light (~65ms theoretical minimum for a round-the-world trip). Available since 2011, this capability enables caching of dynamic, frequently-changing content (sports scores, inventory, live manifests) that was previously considered uncacheable.

### Observability Suite
Real-time logging (streaming logs off the edge at event time), Edge Observer for live and historical traffic data, Domain Inspector for per-domain analytics, Origin Inspector for end-to-end origin-to-edge visibility, and a Log Explorer powered by Bronto for sub-second querying across terabytes of CDN log data.

## Solutions & Use Cases
- **Live Events:** Streaming broadcasts (sports, concerts, elections) with war-room-grade observability for sub-second incident response during traffic spikes
- **Video on Demand:** Scalable VoD delivery with OTFP for format flexibility and Media Shield for multi-CDN cost efficiency
- **Media Companies:** End-to-end delivery stack for broadcasters needing CDN + security + real-time analytics in an integrated platform
- **eCommerce:** Dynamic content personalization, flash sale resilience, and instant purge for real-time inventory updates
- **Digital Publishing:** Real-time journalism with instant content updates, paywall enforcement, and global audience delivery
- **Gaming:** Ultra-fast game downloads, patch delivery, and anti-DDoS protection for gaming platforms

## Technology & Architecture
Fastly's platform is built on a custom, software-defined network architecture rather than off-the-shelf CDN appliances. Each PoP runs Fastly's Varnish-based cache software (with VCL as the configuration language), enabling real-time configuration changes that propagate across the global network in seconds — not minutes or hours like traditional CDNs.

For streaming, Fastly's architecture handles the specific demands of ABR delivery: manifest-heavy request patterns, blocking playlist reload behavior for LL-HLS, chunked transfer encoding for LL-DASH, and the thundering herd of simultaneous requests at live event start. Their chunked transfer handling allows partial objects to be cached and served while still being fetched from origin — critical for low-latency live delivery.

The Edge Compute platform (Fastly Compute) uses WebAssembly as a runtime — the fastest and most portable option for edge compute — enabling sub-millisecond cold starts and deterministic performance. Unlike lambda-style functions that spin up containers, Fastly Compute instances are persistent within a request scope.

For security, the Next-Gen WAF uses a signal-based behavioral model that analyzes attack patterns across the entire customer fleet — detecting novel attacks without requiring pre-defined rules for every CVE. This approach caught and blocked React2Shell/CVE-2025-55182 proactively before customer-specific rules were published.

The Bronto integration (announced March 2026) enables sub-second querying of terabytes of CDN logs using columnar storage optimized for time-series log data — solving the war room observability problem where queries on traditional logging platforms time out during peak events.

## Key Differentiators
- **Instant Purge™ at physics limit:** Delivering sub-150ms global cache purge since 2011 — the only CDN that has operated at this level for over a decade continuously; enables previously uncacheable dynamic content to be safely cached
- **Programmability as a first principle:** Full VCL access and Fastly Compute (WebAssembly) give developers direct control over delivery logic at the edge — vs. black-box CDN configurations
- **Media-specific product depth:** OTFP, Media Shield, dedicated Live Streaming infrastructure, and Live Entertainment Services are purpose-built for media workflows — not generic CDN features bolted on
- **Forrester Wave Leader (2026):** 5/5 scores for performance and developer experience; independently validated positioning vs. hyperscaler and CDN-only competitors
- **Real-time observability at the edge:** Sub-second log querying during live events (via Bronto integration) solves the "war room gap" between anomaly detection and root cause analysis

## Notable Customers & Integrations
**Customers:** GIPHY, The Guardian, Bell Media, Foxtel, Duolingo, Gannett/USA Today Network, TF1, Bonnier News, Atresmedia, Squarespace, Wayfair, Yelp, Shutterstock, JetBlue, Deliveroo, 1stdibs, OpenStreetMap, Python Software Foundation, Rust Foundation

**Technology Partners:** Terraform (official provider), Bronto (log analytics), Tollbit (AI bot monetization), GitHub Actions, CircleCI, Fastly Partner Program ecosystem

**Notable integrations:** VAST/VPAID for ad delivery, Akamai/Cloudflare/AWS CloudFront (multi-CDN alongside), SSO/identity providers, Datadog/Splunk (log forwarding), Kubernetes (Ingress controller support)

## Pricing
Free developer tier available; usage-based pricing (per GB delivered, per request) with volume discounts; custom enterprise packages for high-volume or media workflows. On-the-Fly Packager and Media Shield are priced separately. Contact sales for live events and managed CDN packages.

---

## Blog & Resources Highlights
_Curated from Fastly's blog (fastly.com/blog)_

### Fastly Ranked as a Leader in the 2026 Forrester Wave™ for Edge Development Platforms — March 24, 2026
> Fastly was named a Leader in Forrester's inaugural Edge Development Platforms Wave, receiving the highest score of any vendor in the performance and developer experience criteria — both scored 5/5. The report recognizes Fastly's combination of edge compute maturity, CDN programmability, and security integration as differentiating factors vs. hyperscaler edge offerings and CDN-native competitors.
[Read more](https://www.fastly.com/blog/fastly-ranked-leader-2026-forrester-wave-development)

### Fastly Instant Purge: Under 150ms for Over a Decade — (evergreen)
> Fastly published a detailed explanation of why their Instant Purge™ system achieves under 150ms globally — and why that limit is physically imposed by the speed of light. The mean purge time is constrained by network transmission latency across the globe (~65ms theoretical minimum for a round-the-world signal) plus processing overhead. The piece makes the case that instant purge should be part of normal app architecture — not an emergency recovery tool — enabling sports scores, inventory counts, and live manifests to be cached and invalidated in real time.
[Read more](https://www.fastly.com/blog/fastly-instant-purge-under-150ms-for-over-a-decade)

### Real-Time CDN Monitoring for Live Events with Bronto — March 18, 2026
> Fastly announced a partnership with Bronto (co-founded by the original Logentries team) to provide sub-second log querying across terabytes of CDN telemetry. The integration addresses the "war room gap" — the minutes-long delay between identifying an incident and diagnosing its cause during live events. Bronto processes queries in ~25ms per TB of log data, compared to 15+ minutes on legacy platforms. The integration includes pre-built CDN dashboards, AI-powered root cause analysis via BrontoScope, and 12 months of hot data retention for historical trend analysis and capacity planning.
[Read more](https://www.fastly.com/blog/real-time-cdn-monitoring-for-live-events-with-bronto)

### Multi-CDN: A Critical Decision for a Resilient Architecture — February 19, 2026
> Fastly's technical exploration of multi-CDN strategy covers four steering approaches: DNS-based (geographic routing), Layer 7 (HTTP-level switching), CDN chaining (Fastly as shield in front of other CDNs), and client-side steering. The piece makes the economic and resilience case for multi-CDN while noting that complexity scales with each approach. Fastly's own Media Shield product emerges as the recommended anchor for multi-CDN deployments — handling intelligent request routing and origin cost reduction across the CDN mix.
[Read more](https://www.fastly.com/blog/multi-cdn-critical-decision-for-resilient-architecture)

### Under Attack? How Fastly Can Help — March 17, 2026
> Fastly's Security Operations Center (CSOC) provides human-led response to DDoS and security incidents with a median response time of 1 minute for critical threats. The post outlines Fastly's layered defense approach: automated network-layer DDoS mitigation, Next-Gen WAF for application-layer attacks, and a dedicated CSOC team for escalation. Fastly's DDoS protection is always-on and requires no configuration changes to activate during an attack.
[Read more](https://www.fastly.com/blog/under-attack-how-fastly-can-help)

---

## Key Takeaways
- **The programmable CDN:** Fastly's VCL access and WebAssembly Compute platform give media companies genuine control over edge delivery logic — not just configuration knobs; relevant for teams who've outgrown black-box CDN behavior
- **Streaming is a first-class use case:** OTFP, Media Shield, Live Streaming infrastructure, and live event managed services are not afterthoughts; Fastly serves major broadcasters (Bell Media, Foxtel, TF1) with production-grade streaming infrastructure
- **Instant Purge™ as a foundational capability:** Sub-150ms global cache invalidation changes the architecture of what can be cached — enabling live scores, real-time manifests, and dynamic personalization at CDN scale
- **Security is deeply integrated:** Unlike CDNs that bolt on WAF and DDoS as separate products, Fastly's security capabilities share the same programmable infrastructure — enabling rules and logic to apply uniformly across the edge network
- **Forrester Leader validation in 2026:** Independent analyst recognition at the highest level in Edge Development Platforms positions Fastly as the enterprise-grade alternative to hyperscaler edge offerings
