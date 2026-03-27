# Dolby OptiView — Overview

> Make every moment count with Dolby OptiView

## What They Do
Dolby OptiView is a streaming technology suite — built from Dolby's acquisition of THEO Technologies (the THEOplayer video player company) and the Millicast real-time streaming platform — that provides an integrated stack for video playback, live streaming at all latency levels, and server-guided ad monetization. Their core value proposition is giving streaming publishers a unified, Dolby-backed solution that handles the player, the stream, and the ad simultaneously — enabling premium viewer experiences and measurable monetization uplift without stitching together multiple vendors.

## At a Glance
- **Website:** https://optiview.dolby.com
- **Industry:** Streaming Technology / Media & Entertainment
- **Stage/Positioning:** Division of Dolby Laboratories (publicly traded: DOLBY on NYSE); streaming software and infrastructure product line

## Products & Services

### Dolby OptiView Player
A premium cross-platform video player SDK formerly known as THEOplayer. It supports native SDKs for iOS/tvOS, Android/Fire TV, Roku, HbbTV, Tizen (Samsung Smart TV), WebOS (LG), HTML5, React Native, and Flutter. The player is designed for developers but optimized for viewer retention: it handles adaptive bitrate switching, DRM (Widevine, FairPlay, PlayReady), closed captions (CEA-608/708), CMAF low-latency HLS and DASH, and AV1/HEVC codec support. An Open Video UI component enables teams to customize the player appearance without rebuilding rendering logic from scratch. The player also integrates out-of-the-box with analytics providers like Conviva, NPAW/Youbora, and Mux.

### Dolby OptiView Streaming
Live streaming infrastructure that spans the full latency spectrum — from WebRTC-based real-time streaming at sub-500ms (formerly Millicast), to low-latency HLS/DASH at 2–5 seconds, to broadcast-level latency at 8–10 seconds. Features include configurable latency targets, real-time video transcoding, multi-audio tracks, DRM content security, live clipping, re-streaming to multi-destination, synchronized metadata overlays, and live monitoring/analytics. Delivery is via a globally distributed CDN with Points of Presence worldwide, designed to scale from individual streams to millions of concurrent viewers.

### Dolby OptiView Ads (SGAI)
A Server-Guided Ad Insertion (SGAI) product that combines the scalability of server-side ad insertion (SSAI) with the personalization and measurement capabilities of client-side insertion (CSAI). Unlike SSAI — which requires per-viewer stitching at scale — SGAI uses a single, anonymous, cacheable manifest, while the player handles the actual ad decisioning, insertion, and beaconing at the client level. The server pre-conditions ad break segments (matching codec, bitrate ladder, GOP structure, and DRM to the main stream) so the player can splice them seamlessly. SGAI is pre-integrated with Google Ad Manager and is expanding to any VAST-compliant ad server. Real-world A/B testing against SSAI at a tier-one sports customer showed: 76% higher eCPM, 86% more accurate viewability tracking, 132% higher fill rates, and 40% higher programmatic match rate.

### Customizable Video Player UI
The Open Video UI layer provides a React-based component library for building branded player interfaces without managing raw SDK rendering. Teams can customize controls, branding, overlays, and interactive elements while inheriting the underlying player's reliability across all platforms.

## Solutions & Use Cases
- **Live Sports Streaming:** Ultra-low to broadcast-level latency, multi-view camera options, synchronized metadata for live stats and replays, fan engagement overlays, and personalized SGAI-powered ad experiences. Customers include NFL, NASCAR, and Sky Racing.
- **Sports Betting:** Sub-2-second latency streams aligned with real-time data feeds so odds and video stay synchronized. The Paddy Power and iGameMedia case studies show how retail and online sportsbooks rely on OptiView.
- **Live Auctions:** Real-time streaming up to 4K with multiview bidding views and instant bid update overlays. Used by Eqify and Interencheres.
- **Fan Engagement & Interactive Experiences:** Personalized instant replays, highlight inserts, promotional clips, and interactive overlays powered by the same SGAI architecture used for ads.
- **Cross-Platform OTT Playback:** Publishers serving viewers across CTV, mobile, web, and connected devices — including HbbTV/hybrid broadcast.
- **eLearning & Premium VOD:** High-quality playback with DRM and accessibility compliance (e.g., BBC Maestro).

## Technology & Architecture
OptiView's stack consists of three coordinated layers. The **streaming layer** (formerly Millicast) ingests from RTMP or WebRTC sources and transcodes in real time, packaging content into HLS or DASH with configurable chunked-CMAF delivery, enabling sub-second to broadcast-level latency from a single ingest pipeline. The **player layer** (formerly THEOplayer) is a hardened, multi-platform SDK that handles ABR logic, DRM license acquisition, codec negotiation, and the SGAI insertion/beaconing logic. The **ad layer** (SGAI) uses a lightweight server-side signaling service that watches for SCTE-35 or PDT break cues, pre-notifies the ad decisioning system that a break is approaching, and returns pre-conditioned ad creative segments. The player then makes its own ad server call at break time, stitches locally, and fires viewability beacons (OMID-compatible) directly — eliminating the per-user stitching farm that makes SSAI expensive. The anonymous, non-personalized manifest is fully CDN-cacheable, giving SSAI-like scale at CSAI-like per-user infrastructure cost.

## Key Differentiators
- **SGAI architecture is a genuine technical differentiator:** One cacheable manifest serves the entire audience; personalization and insertion happen on millions of clients in parallel rather than on a centralized stitcher. This simultaneously lowers infrastructure cost and raises ad revenue.
- **Full-latency-spectrum from one vendor:** Sub-500ms WebRTC streaming, 2–5s low-latency HLS/DASH, and broadcast-level 8–10s — all from a single unified platform with the same player SDK.
- **Dolby brand and 60+ years of audio/video expertise** behind the product — relevant for enterprise trust, especially in premium sports and broadcast.
- **Proven player heritage:** THEOplayer was among the most widely deployed commercial video players in Europe before the Dolby acquisition; THEO-era customers include ITV, and Dolby-era additions include NFL and NASCAR.
- **SGAI supports formats beyond ads:** The same mechanism enables personalized highlights, instant replays, and promotional content inserts — turning the ad infrastructure into an engagement engine.
- **ISO/IEC 27001:2022 certified** infrastructure.

## Notable Customers & Integrations
**Customers:** NFL, NASCAR, ITV, Paddy Power, Sky Racing, BBC Maestro, Veikkaus (TotoTV), FZ Sports, Clubber TV, LiveArena, iGameMedia, Content Arena, Eqify, GRID (esports), Watchity, CoupleTV, MwareTV (IGADO)

**Integrations:** Google Ad Manager (SGAI primary integration), VAST/VMAP-compliant ad servers, DRM providers (Widevine, FairPlay, PlayReady), QoE/analytics (Conviva, NPAW, Mux), React Native, Flutter, Expo (React Native + Expo OTT guide published), Amino H200 IPTV set-top boxes, HbbTV broadcast standards

## Pricing
Tiered plans for Streaming, Playback, and Advertising solutions — custom pricing via sales. A free/trial tier is available for getting started. Enterprise pricing is negotiated based on usage volume and feature set. Pricing is not publicly itemized.

---

## Blog & Resources Highlights
_Curated from actual article content on the Dolby OptiView blog_

### SGAI in Practice: Lessons from Dolby OptiView Deployments — February 2026
> In an extended technical interview with Dolby Sr. Director of Engineering Michel Roofthooft, this piece traces how SGAI emerged from a single customer's "shopping list" of needs — personalization at scale, low-latency delivery, richer insights, reduced waste. Roofthooft explains how the anonymous, cacheable manifest restores CDN efficiency that personalized SSAI streams destroy, while pushing insertion and decisioning back to the client. Real A/B test data from a tier-one sports customer shows 76% higher eCPM, 132% better fill rates, and 86% more accurate viewability measurement over their prior SSAI stack — sustained over 12+ months of production.
[Read more](https://optiview.dolby.com/resources/blog/advertising/sgai-in-practice-lessons-from-dolby-optiview-deployments/)

### The Economics of Ad Insertion: How CSAI, SSAI, and SGAI Translate Architecture into Profit — November 2025
> A structured analysis comparing CSAI, SSAI, and SGAI across four business metrics — eCPM, fill rate, match rate, and total cost of ownership. The article establishes that SSAI carries the highest TCO because unique per-viewer manifests defeat CDN caching and force expensive per-user stitching; CSAI has the lowest TCO but weak yield. SGAI is positioned as the optimal balance: shared manifests restore CDN efficiency, just-in-time ad calls improve rendered-to-requested ratios, and client-side beaconing unlocks strong viewability measurement that supports higher CPMs.
[Read more](https://optiview.dolby.com/resources/blog/advertising/the-economics-of-ad-insertion-how-csai-ssai-and-sgai-translate-architecture-into-profit/)

### Live Sports Streaming That Brings Fans Closer to the Game — July 2025
> Explores how sports streaming platforms can move beyond passive viewing with personalized audio tracks, multi-camera views, SGAI-powered personalized ads, and interactive betting integrations. Cites survey data: 74% of streaming platforms rank interactive features as a top priority; 77% cite synchronized delivery as a top technical challenge; 62% of services are targeting sub-5-second latency within three years. Shows how Formula 1, NBA, and FC Barcelona use player-centric storytelling to keep fans engaged year-round.
[Read more](https://optiview.dolby.com/resources/blog/streaming/live-sports-streaming-that-brings-fans-closer-to-the-game)

### SGAI: An Engine That Drives Personalization — January 2026
> Explains the architectural shift that makes SGAI genuinely personalized at scale: the server marks break positions in a generic manifest using HLS Interstitials or DASH Events, while the player calls the ad server with fresh user-level context (device, location, session ID) at playback time. This allows each viewer to get a different ad while the CDN serves a single shared stream — something that SSAI fundamentally cannot do without per-user stitching.
[Read more](https://optiview.dolby.com/resources/blog/advertising/sgai-an-engine-that-drives-personalization/)

### Dolby OptiView Set to Debut at NAB 2025 — 2025
> Announced the rebrand of THEO Technologies + Millicast under the unified "Dolby OptiView" identity, positioning OptiView as the company's integrated streaming product brand. Highlights how the combination of player, streaming, and advertising layers into a single product represents Dolby's strategic bet on the streaming market as the successor to broadcast-era audio/video dominance.
[Read more](https://optiview.dolby.com/resources/blog/streaming/dolby-optiview-set-to-debut-at-nab-2025)

---

## Key Takeaways
- **SGAI is the centerpiece:** Dolby OptiView is positioning Server-Guided Ad Insertion as the next generation of streaming monetization — a genuine architectural alternative to SSAI, not just a marketing rebrand. Production data backing this claim is substantial and verifiable.
- **They own both ends of the transaction:** Controlling the player SDK, streaming infrastructure, and ad insertion layer in a coordinated system is rare. Most streaming publishers stitch these together from multiple vendors; OptiView is a bet on integration being a competitive advantage.
- **Sports and betting are the primary growth markets:** Customers like NFL, NASCAR, Paddy Power, and Sky Racing reflect a specific go-to-market focus on high-value, latency-sensitive live content where SGAI's economics and engagement features are most differentiated.
- **Dolby brand carries weight:** The parent company's 60+ year reputation in premium audio/video makes OptiView credible in enterprise sales conversations that a startup streaming vendor would struggle to win.
- **Real-time streaming (sub-500ms) is a unique capability:** Very few commercial platforms can deliver WebRTC-scale real-time streaming with CDN-level reliability and a full player SDK — the Millicast heritage gives OptiView a technical capability that most streaming video platforms lack.
