# PubNub — Overview

> Build, manage, & optimize real-time apps at scale

## What They Do
PubNub is a globally distributed real-time messaging network and developer platform that powers interactive, event-driven experiences in any application. Built on a publish/subscribe architecture with 15+ global Points of Presence, PubNub connects over 1 billion unique devices and processes more than 3 trillion transactions per month — handling the infrastructure complexity of real-time at scale so product teams don't have to. It is the backbone for live event chat, fan engagement, sports data streaming, virtual events, IoT data distribution, gaming, and any use case requiring instant, reliable data delivery to millions of simultaneous users.

## At a Glance
- **Website:** [https://www.pubnub.com](https://www.pubnub.com)
- **Industry:** Real-time communications infrastructure, developer platform
- **Stage/Positioning:** Private company, San Francisco. Currently attending NAB Show Las Vegas.

---

## Products & Services

### Publish/Subscribe (Core Network)
The foundation of PubNub. Publishers send messages to named channels; all subscribers to that channel receive them within 250ms or less globally (targeting <100ms for most deployments). Channels are zero-config and transient — they exist the moment you publish to them. There are no limits on the number of channels or concurrent subscribers. Messages up to 32KB are supported. PubNub's network uses HTTP streaming and pipelining to support unlimited publishes without waiting for acknowledgement on the same TCP connection.

### Presence
Real-time awareness of which users and devices are online, offline, or have timed out. Presence emits join/leave/timeout events per channel and exposes API endpoints to query current occupancy, who is present, and where a given user is connected. Useful for building live audience counters, "currently watching" indicators, active user counts during events, and user state tracking (e.g., battery level, location, game state). Presence events can trigger PubNub Functions for automated server-side responses.

### Message Persistence (History)
Optional add-on that stores all published messages automatically. Retention configurable from 1 day up to unlimited. Messages are retrieved via the History API with support for paging (up to 100 messages per request) using start/end timetokens. Stored messages are replicated across multiple availability zones globally. Without this add-on, PubNub caches the last 100 messages per channel for up to 20 minutes — useful for message catch-up on reconnect but not a durability guarantee.

### PubNub Chat SDK
A higher-level SDK purpose-built for chat and messaging applications, sitting on top of the core pub/sub network. Available for JavaScript, Kotlin, Swift, Unity, and Unreal. Provides ready-to-use abstractions for:
- Sending/receiving messages with threads and quotes
- Typing indicators and read receipts
- @mentions and user notifications
- Unread message counts
- Message reactions and pinned messages
- Message moderation (AI-powered — see below)
- Channel creation, join, leave, membership management
- Draft messages and message history

Reduces the engineering lift to ship a production chat feature from months to days.

### Illuminate (Live Analytics & Decisioning)
No-code dashboards for real-time analytics and automated decision-making. Operators define metrics and thresholds; Illuminate monitors live event data and can trigger automated actions (e.g., send a message to a channel, fire a webhook, update a user segment) when conditions are met. Designed for live events where human reaction time is too slow — e.g., automatically throttle messages when a channel hits 10,000 concurrent users, or trigger a push notification when a score changes. Integrates with A/B testing frameworks for uplift measurement.

### Access Manager (Security)
Fine-grained, token-based access control at the channel and user level. Server grants read/write permissions to an auth token with a configurable TTL (1 minute to 43,200 minutes). Clients authenticate via your server, receive a scoped token, and PubNub enforces channel-level ACLs automatically. Prevents unauthorized access even if a client intercepts publish/subscribe keys. AES-256 end-to-end message encryption is available as an independent layer — encrypted at the sending endpoint, decrypted only at receiving endpoints; PubNub never has access to cipher keys.

### PubNub Functions (Serverless Edge Logic)
JavaScript functions that execute within PubNub's Data Stream Network — at the edge, before messages reach subscribers. Used to transform message payloads, filter content, integrate with third-party APIs (via XHR), enforce rate limits, route messages conditionally, or aggregate data. Functions support a KV store (persistent key-value storage at the edge), JWT validation, crypto operations, and UUID generation. Eliminates the need to run a separate backend server for many common real-time use cases.

### AI Chat Moderation
Real-time filtering of toxic, abusive, or unsafe messages before they reach subscribers. Runs as a Function within the network to block or flag content without adding round-trip latency. Integrates with third-party moderation partners and supports custom profanity lists. Used in live event chat to maintain safe, brand-appropriate environments at scale.

### Stream Controller (Channel Multiplexing & Groups)
Enables a single client connection to subscribe to up to 2,000 channels simultaneously using Channel Groups, or up to 20,000 channels total (10 groups × 2,000 channels). Wildcard subscribe allows subscribing to all channels matching a prefix pattern (e.g., `sports.*` receives from `sports.nfl`, `sports.nba`, etc.). Reduces connection overhead for complex multi-channel applications.

### Mobile Push Notifications
Bridge between PubNub channels and native mobile push systems (Apple APNS, Google FCM). When a message is published to a channel with registered push devices, PubNub automatically delivers it via the native push infrastructure. Supports offline delivery — messages reach users even when they're not actively in the app. PubNub supports up to 32KB payloads vs. push platforms' 2-4KB limits, and provides bi-directional communication and message history that push-only solutions cannot.

### App Context (Objects & Metadata)
Server-side storage for structured metadata about users, channels, and memberships. Provides a consistent data layer for chat features like user profiles, channel descriptions, and membership lists. Updated in real time and queryable via REST or SDK. Decouples user/channel state from message streams.

### Files API
Upload and share files (images, video clips, documents) up to 5MB per file within PubNub channels. Files are stored and retrievable via the History API in combination with SDK file methods.

---

## Solutions & Use Cases

- **Live Sports Fan Engagement:** Real-time chat, reaction emoji streams, live polls, score alerts, and occupancy counters (how many fans are watching right now) — all synchronized to the live broadcast. Used for in-stadium apps, second-screen experiences, and OTT companion features. PubNub has been used for Super Bowl-scale events.
- **Virtual & Live Events Chat:** Powers the interactive layer of concerts, conferences, and esports events with millions of concurrent participants. Chat sharding across channels (recommended at >10,000 users per channel), presence-driven audience counts, and push notifications for re-engagement.
- **Live Stream Shopping:** Real-time chat and Q&A during shoppable streams; state sync for product overlays, inventory updates, and bid counters; PubNub Presence API tracks active shoppers for "X people viewing this item" indicators.
- **OTT & Broadcast Companion Experiences:** Second-screen apps with synchronized real-time commentary, trivia, and voting during live broadcasts. Low-latency delivery ensures interactions feel tied to the on-screen moment.
- **IoT Data Distribution:** Fan-out of sensor and telemetry data from devices to dashboards. PubNub handles arbitrary publish rates and distributes to any number of subscribers in real time.
- **Gaming:** Multiplayer game state sync, leaderboards, real-time chat, and presence (player online/offline tracking) for Unity, Unreal, and web games.
- **Customer Data Platforms:** Real-time event ingestion and routing; feeds stream processors (Flink, Spark) for live segmentation, churn detection, and ML-driven personalization.
- **Geolocation & Tracking:** Sub-250ms delivery of location updates for rideshare, delivery tracking, and asset monitoring.
- **Healthcare:** HIPAA-compliant real-time messaging for telemedicine, patient monitoring dashboards, and care coordination.
- **Contact Centers:** Real-time agent-to-customer chat, presence-based agent availability, and collaborative tooling.

---

## Technology & Architecture

**Global Edge Network**
PubNub operates 15+ Points of Presence (PoPs) distributed globally. Client connections route to the nearest PoP via Geo-DNS, which also provides 4-IP automatic failover across data centers. This architecture delivers a global average latency of under 250ms, with a target of under 100ms for most deployments. Uptime SLA is 99.999%.

**Pub/Sub Transport Layer**
PubNub uses HTTP streaming and long-polling (not WebSocket-only) to maximize compatibility across all environments, including restrictive corporate firewalls and embedded/IoT devices. HTTP pipelining enables unlimited publishes over a single TCP connection without waiting for responses. The subscribe mechanism uses a long-poll loop that holds the connection open until a message arrives or a timeout occurs, then immediately reopens — effectively providing a persistent real-time stream.

**Message Ordering & Delivery**
Messages carry PubNub timetokens (17-digit precision timestamps) that enable ordered retrieval, deduplication, and catch-up on reconnect. The system guarantees at-least-once delivery; applications that require exactly-once semantics implement deduplication on top.

**Serverless Edge Execution (Functions)**
Functions run inside PubNub's data stream network on each incoming message, before fan-out to subscribers. This enables sub-millisecond edge transformations without adding network round-trips. The JavaScript runtime supports async/await, XHR for external HTTP calls, and a built-in KV store for stateful edge logic.

**Security Stack**
- TLS 1.2+ enforced on all connections (as of February 2025)
- AES-256 end-to-end message encryption (cipher key stays with the application; PubNub cannot decrypt)
- Token-based Access Manager with TTL-scoped, channel-level ACLs
- DDoS mitigation: IP range banning, geo-DNS failover, TCP SYN flood mitigation, load-balanced dynamic DNS
- Compliance: HIPAA, GDPR, SOC2

**SDK Breadth**
70+ officially maintained SDKs covering: JavaScript, iOS (Swift/Objective-C), Android (Java/Kotlin), Python, Go, Ruby, PHP, Rust, C#, Dart/Flutter, Unity, Unreal Engine, FreeRTOS, embedded C (POSIX, mbed, Windows C/C++), and more. All SDKs are open source under the MIT license. REST API available for platforms without an official SDK.

**Scalability**
No hard limits on channels, users, or message volume. Customers with >1,000 concurrent connections are recommended for a Pro plan to receive architecture review and volume discounts. PubNub has demonstrated scale at millions of concurrent connections. Channel multiplexing and channel groups reduce connection overhead for high-channel-count applications (up to 20,000 channels per client connection).

---

## Key Differentiators

- **Network scale as the product, not infrastructure the customer manages:** PubNub is a hosted-only solution. There is no self-hosted option — this is a deliberate choice that enables a single globally consistent 99.999% SLA, rather than per-deployment variability.
- **Depth of add-on feature set:** Most real-time messaging networks provide pub/sub and stop. PubNub layers Presence, History, Functions, Access Manager, Illuminate, Chat SDK, Files, Push, and App Context into a single platform — reducing the number of vendors needed for a production real-time feature.
- **Live event track record at extreme scale:** Used in production for Super Bowl apps, professional sports fan engagement (DAZN, Ticketmaster), virtual concerts, and esports. Has specific operational tooling (Virtual Event Form, live event support packages) for events exceeding 10,000 concurrent users.
- **Edge execution via Functions:** Logic running inside the message network (not a separate Lambda/Cloud Function) is a meaningful architectural advantage for low-latency moderation, routing, and transformation — no additional hop.
- **SDK breadth including embedded and game engines:** Unity and Unreal Engine native SDKs, FreeRTOS, and embedded C support extend PubNub into game development and IoT hardware, well beyond what most messaging APIs cover.
- **Illuminate for non-developer operators:** The no-code analytics and decisioning layer allows event producers, operations teams, and product managers to define real-time automations without writing code — unusual in infrastructure-focused developer platforms.

---

## Notable Customers & Integrations

**Customers:** DAZN, Ticketmaster, LiveLike, Veeps, Logitech, Autodesk, Swiggy, Kiswe, Sprinklr, ACS

**Integrations:** Apple APNS, Google FCM, Stripe (payment workflows), Google Natural Language API, Firebase Cloud Messaging, RabbitMQ, Apache Kafka (event bridge patterns), Datadog/Prometheus (observability), OpenTelemetry, Kubernetes/Istio (deployment environments)

---

## Pricing

- **Free Plan:** Forever free — 200 Monthly Active Users (MAU) or 1 million transactions. Suitable for prototyping.
- **Starter Plan:** $98/month — 1,000 MAU, up to 6 months message storage. For apps in early production.
- **Pro Plan:** Custom pricing — unlimited data storage, dedicated support, advanced analytics, architecture review. Required for Message Persistence beyond 180 days and volume > 1,000 MAU at scale.
- Pricing is MAU-based (Monthly Active Users), not per-message, which provides cost predictability for event-driven workloads with bursty traffic patterns.

---

## Blog & Resources Highlights

### Architecting Scalable Live Stream Shopping Platforms — March 25, 2025
> An architectural deep-dive into building shoppable livestream infrastructure. Covers the protocol tradeoffs between WebRTC (sub-100ms, infrastructure-intensive), LL-HLS, and CMAF (2-3s, CDN-friendly) and makes the case for hybrid architectures. PubNub Presence API is positioned as the state-sync layer for product overlays, inventory indicators, and real-time bid updates. Also addresses load balancing strategy: CloudFront at edge, Nginx reverse proxy, API Gateway for throttling, and PubNub for the real-time messaging layer under high-traffic spikes with predictive Kubernetes HPA autoscaling.
[Read more](https://www.pubnub.com/blog/live-stream-shopping)

### Real-Time Customer Data Insights Platform — April 9, 2025
> Technical architecture guide for building streaming-native customer intelligence systems. PubNub is positioned as the ingestion and event propagation layer, feeding Flink/Spark stream processors for real-time segmentation, churn detection, and ML-based decisioning. Covers entity resolution for unified customer profiles, continuous audience segmentation using contextual bandits, and operational intelligence where PubNub Event Handlers route ML inference outputs to CRMs, marketing tools, and support systems in real time. End-to-end observability via OpenTelemetry, Prometheus, and Grafana.
[Read more](https://www.pubnub.com/blog/real-time-customer-data-insights-platform)

### How to Build Chat for Virtual Events — March 28, 2023
> Practical guide for handling live events with millions of participants. Explains PubNub's Chat Components (React, Android, iOS) and when to use them vs. raw SDKs. Covers channel sharding strategy (splitting users across channels when occupancy exceeds 10K for best performance), message persistence for catch-up, push notifications for re-engagement, and profanity filtering integration. Cites LiveLike and Veeps as production customers using PubNub as their chat API backbone.
[Read more](https://www.pubnub.com/how-to/build-chat-for-virtual-events)

### How to Handle Large-Scale Events with PubNub
> Operations guide for events exceeding 10,000 concurrent users. Specifies PubNub's Virtual Event Form requirement (submit 10+ days before event), live support options (Platinum Support Plan with 5 hours/month live event coverage, or purchasable Virtual Events Package), and architectural best practices: channel sharding, minimal message payload size, selective presence, Access Manager for public events, and client-side performance considerations. Also documents PubNub's track record at Super Bowl scale.
[Read more](https://www.pubnub.com/how-to/handle-large-scale-events)

### How to Develop a Real-Time Streaming Application with PubNub — March 28, 2023
> Developer guide demonstrating PubNub as a real-time data distribution layer for high-volume streams (weather, stock quotes, sensor data, social media firehoses). Shows a Twitter stream relay implementation: a server-side publisher ingests from the Twitter Real-time Streamer and publishes to PubNub; any number of subscribers across any SDK receive updates within 100-150ms. Underscores PubNub's decoupling of publish and subscribe — publishers and subscribers are fully independent. Includes working JavaScript subscribe snippet.
[Read more](https://www.pubnub.com/how-to/real-time-streaming-application)

### Building Secure Web Live Chat Apps
> Best practices guide covering the full security surface of a production chat app built on PubNub. Topics include Access Manager token scoping and TTL strategy, AES-256 cipher key management (PubNub never holds cipher keys), TLS 1.2+ enforcement, DDoS mitigation layers (geo-DNS failover, IP banning, TCP SYN flood mitigation), HIPAA/GDPR/SOC2 compliance paths, and rate limiting via Functions.
[Read more](https://www.pubnub.com/blog/building-secure-web-chat-apps)

---

## Key Takeaways

- **The real-time infrastructure layer for live media and entertainment experiences.** PubNub's core value proposition is removing the engineering burden of operating a globally distributed, low-latency messaging network — letting teams ship interactive features (chat, reactions, polls, alerts, presence counts) on top of proven infrastructure rather than building and operating it themselves.
- **Proven at live event scale.** 3 trillion transactions/month, 1B+ devices, Super Bowl-tested, and trusted by DAZN and Ticketmaster in production. PubNub has operational tooling specifically for large live events that most messaging APIs don't offer.
- **Media & entertainment is a primary vertical.** The blog content, SDK portfolio (Unity, Unreal), and use-case library (live sports, OTT companion, virtual events, live stream shopping) make clear this is not incidental — it's a core market PubNub actively targets, and a good fit with the NAB Streaming Summit audience.
- **Illuminate adds a no-code operations layer.** The ability for non-engineers to define real-time automations on top of live event data differentiates PubNub from pure infrastructure plays and positions it as a platform for both engineering and operations teams.
- **70+ SDKs means it meets developers where they are.** From React frontends to Unreal Engine games to FreeRTOS embedded hardware, PubNub's SDK coverage is broader than any comparable real-time messaging service, lowering the integration barrier significantly.
