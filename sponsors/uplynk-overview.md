# Uplynk — Overview

> Stream your way — Build, monetize, and operate premium streaming at scale

## What They Do
Uplynk is a cloud-native video streaming platform focused on live sports, linear channels, and premium VOD delivery — with integrated monetization, content management, and managed operations services. Originally built within Verizon's media technology stack, Uplynk emerged as an independent company in 2024–2025 through the restructuring of Edgio, and now operates under backing from investment firm Lynrock Lake. The platform serves global broadcasters, sports leagues, digital-first brands, and enterprise media teams who need to run complex live and on-demand streaming operations without building and maintaining all the underlying infrastructure themselves.

## At a Glance
- **Website:** https://www.uplynk.com
- **Industry:** Video Streaming Platform / Media Technology
- **Stage/Positioning:** Independent private company backed by Lynrock Lake (as of July 2025); formerly a product of Edgio (previously Verizon Digital Media Services)

## Products & Services

### Acquire — Content Ingest
Captures live and on-demand video and routes it into the Uplynk platform. Supported ingest protocols include RTMP (push and pull), HLS (push/pull), DASH, SRT, Zixi, and RIST — covering both traditional broadcast contribution and modern IP-based ingest. Direct-to-Cloud uploads handle VOD files. On-premises slicing and encoding is also available for customers with existing hardware investments. Multi-region ingest with automatic failover ensures redundancy for high-stakes live events. The ingest layer is API-first, enabling programmatic control of encoding profiles, failover configurations, and stream metadata from external orchestration systems.

### Manage — Content & Channel Operations
A centralized dashboard for managing the full video workflow: scheduling VOD libraries, configuring and operating virtual linear channels, managing live events, setting content metadata, applying geo-blocking rules, and configuring DRM and access control policies. Supports Adaptive Bit Rate (ABR) delivery from mobile-SD to UHD, with full DRM support for FairPlay (Apple), Widevine (Google/Android), and PlayReady (Microsoft). Content blackout configuration, regional rights management, and live event management are all handled in a single interface rather than multiple tools.

### Monetize — Ad Insertion & Revenue
Uplynk's ad monetization stack is built around Server-Side Ad Insertion (SSAI), with a 1:1 session-based architecture via the SmartPlay engine. SmartPlay delivers per-user manifests with dynamic ad decisioning, content blackout rules, geo-based targeting, and mid-stream CDN switching — all session-aware. Supported formats include VOD ad insertion, live SSAI, 24/7 linear channels (ad-supported), FAST channels (Free Ad-Supported Streaming TV), and social media syndication. The monetization dashboard shows fill rates, error trends, delivery gaps, and ad server performance across multiple ad providers in real time — centralized visibility rather than separate reporting per ad server.

New ad formats debuting at NAB 2026 include Squeezeback and Picture-in-Picture ads, integrated directly into the platform without requiring additional vendor integrations. An Ad Waterfall feature is also planned to help smaller teams maximize fill without manual engineering effort.

### Deliver — Distribution
Multi-CDN delivery with automatic failover and redundancy, designed to reach viewers globally across web, mobile, CTV, and connected TV platforms. Uplynk Deliver uses SmartPlay's 1:1 manifest architecture to support personalized delivery: content blackouts, multi-CDN routing, geo-based stream selection, and mid-stream feed switching happen at the manifest level without requiring re-encoding. Rapid startup times and buffer-free streaming are core delivery promises. The platform supports CMAF packaging for low-latency delivery compatibility with HLS and DASH simultaneously.

### StreamOps — Managed Operations
A managed service layer providing 24/7 operational support for live events and always-on linear channels. StreamOps teams monitor stream health, manage ad breaks and failover transitions, perform pre-event readiness checks, and handle post-event postmortems. This is positioned as an expert operations team extension — available both to Uplynk SaaS customers and as a standalone managed service for streamers using their own technology stack. In 2025, Uplynk supported 35,000+ live streams across premium sports and linear environments through StreamOps.

### Uplynk Studio
A redesigned interface (introduced post-independence) for content creation and management workflows. Includes AI-driven tools for automated subtitling, clip creation, and metadata enrichment — with a human-in-the-loop design philosophy that keeps editorial teams in control of AI outputs.

## Solutions & Use Cases
- **Live Sports Streaming:** High-stakes live events with broadcast-grade reliability; multi-source ingest failover; real-time ad insertion and blackout management; audience scales from national broadcasts to niche sports leagues.
- **Linear Channel Operations:** 24/7 virtual linear channels — ad-supported or subscription — managed through a single scheduling and playout interface; no dedicated MCR required.
- **FAST Channels:** Building and operating Free Ad-Supported Streaming TV channels that leverage existing live or VOD libraries as a new distribution and discovery channel.
- **VOD Monetization:** AVOD (ad-supported), SVOD (subscription-gated), and TVOD (transactional) delivery from a single unified workflow.
- **Financial News & Data Streaming:** Schwab Network uses Uplynk as the foundation for real-time financial news streaming to traders and investors.
- **Religious Organization Streaming:** Faith-based organizations use Uplynk for church services, conferences, and community content delivery at scale.
- **Corporate Communications:** Enterprise media teams and marketing organizations use the platform for internal and external live events.
- **International Broadcasting:** NHK (Japan) uses Uplynk as the foundation for video business management, with Uplynk handling disparate technologies from ingest to content distribution.

## Technology & Architecture
Uplynk's core architecture is cloud-native and built on AWS, giving it global reach, automatic scaling, and the reliability of hyperscaler infrastructure without the operator managing the underlying compute. The platform is API-first throughout — every workflow function (ingest configuration, channel scheduling, ad insertion rules, delivery configuration) is accessible programmatically, enabling integration with external MAMs, automation systems, and workflow orchestration tools.

The SmartPlay engine is the technical centerpiece of Uplynk's differentiation. SmartPlay generates 1:1 personalized manifests for each viewer session, containing their specific ad insertion decisions, content blackout rules, geo-based stream selections, and CDN routing assignments — all resolved at session initiation rather than requiring real-time server intervention on every manifest request. Mid-stream Multi-CDN Switching can redirect a session to a different CDN during playback without interrupting the viewer experience. Session tokenization and geo-blocking are enforced at the manifest level.

For ad insertion, Uplynk uses SCTE-35 markers from the live or channel feed to trigger ad breaks, calls connected ad servers via VAST/VPAID, and stitches ad content server-side before delivery. The monitoring dashboard gives revenue teams visibility into fill rates and delivery errors without requiring technical support tickets.

Ingest redundancy is built in: multiple concurrent ingest paths (primary + backup) with automatic failover logic in the cloud, protecting against contribution link failures. StreamOps teams monitor this redundancy in real time and can intervene manually if needed.

## Key Differentiators
- **SmartPlay 1:1 manifest architecture:** Per-session personalized manifests that enable content blackouts, multi-CDN delivery, geo targeting, and ad personalization without per-user server-side stitching at the manifest generation level — a technical approach that balances personalization with scalability.
- **Modular adoption model:** Customers can adopt individual Uplynk modules (SmartPlay Ads for monetization, SmartPlay Ingest for encoding flexibility, StreamOps for operations) without replacing their entire workflow — reducing switching risk and time-to-value.
- **StreamOps as a standalone managed service:** Uplynk's operational expertise is available even to customers who don't use the Uplynk technology platform — a differentiated offering that generates revenue from the streaming industry's general operations complexity problem.
- **Independence from Edgio/Verizon:** The separation from Edgio's restructuring and Lynrock Lake backing gives Uplynk a clean balance sheet and strategic independence to focus exclusively on the streaming platform market.
- **35,000+ live streams supported in 2025:** Scale at which Uplynk operates is demonstrated across sports leagues, broadcasters, and enterprise media — reducing the "will it work for my use case?" risk for new customers.
- **Zixi and SRT integration:** Support for both Zixi (the de facto broadcast-grade IP transport protocol) and SRT (its open-source counterpart) means Uplynk works with the transport protocols that premium broadcast customers already use.

## Notable Customers & Integrations
**Customers:** CHL (Canadian Hockey League), ReachTV (airport streaming network), Schwab Network (real-time financial news), NHK (Japan's national broadcaster), Hearst Television (news distribution), GOTHAM, OnePlay, La Presse, Brigham Young University, The CW Television Network

**Technology Integrations:** AWS (infrastructure), Zixi (broadcast IP transport), SRT, RIST, Bitmovin (encoding), multi-CDN delivery partners, FairPlay/Widevine/PlayReady DRM, VAST/VPAID ad servers, HLS-Push/Pull, DASH, RTMP-Push/Pull, CMAF packaging, Veopix (live video delivery partnership)

**Ecosystem:** CDNs (multi-CDN delivery), video players (player-agnostic delivery), ad servers (multi-server support via SmartPlay), social platforms (YouTube, Facebook, Twitch syndication)

## Pricing
Contact sales — pricing not publicly stated. Cloud-based SaaS model with usage-based components; StreamOps managed services available on separate engagement terms.

---

## Blog & Resources Highlights
_Curated from actual article content on the Uplynk newsroom_

### Streaming Works. Now It Has to Work Profitably. — March 2026 (NAB 2026 Preview)
> Uplynk CEO Eric Black argues the streaming industry's central question has fundamentally shifted: reliability is largely solved, the new problem is economic efficiency. Rights costs are rising, ad loads can't grow indefinitely, and every new distribution channel (FAST, social, international) risks adding operational complexity rather than revenue. At NAB 2026, Uplynk is demonstrating new ad formats (Squeezeback, PiP) and deeper ad visibility tools — specifically designed so monetization innovation doesn't require adding new vendors or revenue-share partners.
[Read more](https://www.uplynk.com/blog/nab-2026-preview)

### What We Heard at IBC and How Uplynk Is Solving It — September 2025
> A structured recap of themes from IBC 2025, translated into product roadmap explanations. Cost pressure is leading operators to evaluate modular tools rather than monolithic platforms. AI is a baseline expectation but must come with human-in-the-loop controls. Cloud-native workflows are accelerating as on-prem hardware depreciates. SGAI is discussed as the future of monetization, but FAST needs solutions now. Uplynk's response is the SmartPlay: DAI product with per-user manifest personalization, dynamic overlays for ad revenue outside traditional breaks, and an Ad Waterfall for maximizing fill without engineering effort.
[Read more](https://www.uplynk.com/blog/what-we-heard-at-ibc-and-how-uplynk-is-solving-it)

### The Platform Powering Global Streaming at Scale — October 2025
> A company-authored piece describing Uplynk's current scale (25,000+ live events annually, billions of viewing minutes monthly) and positioning the platform as the "quiet force" behind some of the world's most reliable streaming experiences. Highlights the SmartPlay engine, StreamOps managed services, and Uplynk Studio's AI-driven content tools. Quotes CEO Eric Black: "Our goal is to be the partner that helps them scale without the overhead." Also covers the Lynrock Lake investment and the company's independence from Edgio.
[Read more](https://www.uplynk.com/blog/the-platform-powering-global-streaming-at-scale)

### IBC Preview: Smarter, Faster, More Flexible Streaming with Uplynk — August 2025
> Pre-IBC post by CEO Eric Black previewing Uplynk's product direction: AI features that are "pragmatic, explainable, and built for real production environments" rather than experimental — specifically human-in-the-loop clipping, metadata enrichment, and Uplynk Studio enhancements. Emphasizes building AI that teams can trust with clear, measurable outcomes rather than AI for its own sake. Also previews deeper Zixi and Bitmovin integrations for broadcast-grade IP transport and encoding flexibility.
[Read more](https://www.uplynk.com/blog/ibc2025)

### Zixi and Uplynk Partner to Accelerate the Transition to IP-Based Video Delivery — June 2025
> Announcement of a formal partnership integrating Zixi's broadcast-grade IP transport protocol directly into Uplynk's ingest layer. Zixi provides reliability guarantees and congestion management algorithms optimized for contribution-quality video over public internet — giving Uplynk customers a direct path from broadcast-grade Zixi-based contribution to cloud-native streaming delivery without protocol translation steps.
[Read more](https://www.uplynk.com/blog/zixi-and-uplynk-partner)

---

## Key Takeaways
- **Independence is the story:** Uplynk's emergence as a standalone company with fresh Lynrock Lake backing is the defining event — it signals a strategic focus on streaming as a standalone business, free from the overhead and distraction of Edgio's broader CDN business.
- **SmartPlay 1:1 sessions is a real technical moat:** Per-session manifest personalization that handles blackouts, multi-CDN, ad decisioning, and geo-targeting without per-user server stitching is architecturally distinctive and provides genuine flexibility that competing platforms struggle to match.
- **StreamOps is an underappreciated differentiation:** Offering managed operations as both an add-on for Uplynk customers and a standalone service for the broader streaming market is a smart expansion — the industry's operational complexity is universal, not platform-specific.
- **Premium sports and linear is the core market:** CHL, ReachTV, Schwab Network, NHK, and Hearst Television reflect a deliberate focus on professional-grade, high-availability streaming rather than the long tail of small streaming publishers.
- **The FAST opportunity is being actively addressed:** FAST channels are a growing distribution model and Uplynk's existing live/linear infrastructure is directly applicable — the NAB 2026 message about expanding FAST without rebuilding workflows is a timely and credible claim.
