# TwelveLabs — Overview

> The world's most performant AI for video understanding — surpassing benchmarks from cloud majors and open-source models.

## What They Do
TwelveLabs builds video foundation models and an API platform that enables enterprises to search, analyze, and extract structured meaning from video content. Unlike traditional video search (which relies on metadata, tags, and transcripts), TwelveLabs' models understand video multimodally — processing visual frames, audio, speech, motion, and narrative context together to answer natural language queries, generate text descriptions, and power recommendation systems. The company's primary markets are media & entertainment, advertising, government/security, and automotive — any domain where making sense of large video libraries is operationally critical and currently manual.

## At a Glance
- **Website:** [twelvelabs.io](https://www.twelvelabs.io)
- **Industry:** Video AI / Multimodal Foundation Models / Developer APIs
- **Stage/Positioning:** Private, Series A ($50M, June 2024, led by NVIDIA NVentures and NEA). Prior investors include Index Ventures, Radical Ventures, and Wndr Co. Models available on AWS Amazon Bedrock. Active exhibitor at NAB Show 2026.

## Products & Services

### Marengo (Retrieval Foundation Model)
TwelveLabs' multimodal retrieval model, optimized for any-to-any search tasks. Marengo understands and generates embeddings across video, audio, image, and text in a shared embedding space — enabling cross-modal search queries. A text query finds relevant video moments; an image query finds visually similar scenes; a video clip query finds related content across a library. Marengo 2.7 is the current production version, available directly through the TwelveLabs API and as a managed service on AWS Amazon Bedrock.

### Pegasus (Generation Foundation Model)
TwelveLabs' video-language model, optimized for text generation tasks from video. Pegasus integrates visual, audio, and speech information to generate: summaries, chapter lists, action items, Q&A answers, sentiment analysis, compliance flags, and open-ended descriptions — all customizable through prompting. Pegasus 1.2 is the current production version, also available on AWS Bedrock. Unlike transcript-based summarization, Pegasus reasons from the actual video frames, audio, and pacing — capturing things that transcripts miss.

### Search API
Enables semantic, natural language search across indexed video libraries. Queries can combine text, images, audio clips, or video clips. Returns timestamped results pointing to the exact moments in a video that match the query — not just the video file. Supports entity search (find every appearance of a specific person using reference images), scene-level grouping, and sorting.

### Analyze API
Generates any text output about a video through prompting — summaries, chapter timestamps, tables of content, action items, Q&A, compliance checks, or any custom format. The API also supports streaming output for real-time applications. Pegasus powers this endpoint.

### Embed API
Creates multimodal vector embeddings for video, audio, image, and text inputs in a shared semantic space. Designed for teams building their own vector databases, recommendation systems, similarity search layers, or clustering pipelines on top of TwelveLabs embeddings. Supports both synchronous and asynchronous (multipart) upload workflows.

### Playground
Interactive web interface where developers and product teams can test search, analysis, and embedding against their own videos without writing code. Designed to accelerate the demo-to-production cycle.

### TwelveLabs Claude Code Plugin
An MCP-based CLI plugin that brings video intelligence into the Claude Code workflow. Developers can index videos, run semantic search, analyze content, and generate embeddings without leaving the terminal. Supports local paths, remote URLs, and Google Drive links for indexing. Async-aware (tracks indexing status in the session). Available on the Claude Code plugin marketplace.

## Solutions & Use Cases
- **Media & Entertainment:** Semantic content discovery for MAM systems, highlights generation, sports clip search, multimodal content tagging, editorial workflow automation
- **Advertising:** Brand integration monitoring (find every brand mention or logo appearance), contextual ad matching, influencer discovery, ad break placement optimization
- **Government & Security:** Automated surveillance review, incident footage search, public safety monitoring
- **Automotive:** Driver behavior analysis, fleet safety monitoring, dash cam event extraction
- **Sports:** Automatic highlight creation, player tracking, play-by-play search, fan engagement applications
- **Learning / EdTech:** Video quiz generation, educational content search, compliance training monitoring

## Technology & Architecture
TwelveLabs built a purpose-built video indexing pipeline (Indexing 3.0, launched February 2026) that transforms raw video into structured, reusable embeddings. The pipeline runs as three composable primitives: (1) **Embedding generation** — video is decoded, segmented into scenes, and each segment is passed through multimodal encoders to produce visual + audio embeddings stored in a vector database; (2) **Search** — user queries are embedded in the same representation space and retrieved via vector similarity search + post-processing; (3) **Generation** — stored embeddings are passed to Pegasus as context for text generation tasks.

The system runs on a layered architecture (Indexing 3.0 design): a unified indexing platform atop Ray Serve (execution/orchestration layer) atop swappable infrastructure (Kubernetes, bare metal, AWS, etc.). This design makes the platform deployable across cloud, private cloud, and on-premises environments without rewriting application logic. The move from microservices mesh to layered architecture delivered: cleaner engineering onboarding, parallel team development, infrastructure portability, and structural cost efficiency.

**Models:** Marengo (any-to-any multimodal retrieval) and Pegasus (video-language generation). Both are available through TwelveLabs' own API, AWS Amazon Bedrock, and can be fine-tuned for domain-specific use cases.

**Infrastructure:** Python-native, Ray Serve for orchestration, GPU-accelerated model inference (NVIDIA-certified). SOC 2 Type II compliant.

**Integrations:** AWS (Amazon Bedrock, S3), Databricks (Mosaic AI, Delta tables, vector search), MongoDB Atlas Vector Search, Pinecone, Snowflake Cortex, Weaviate, LanceDB, Milvus, Elasticsearch, ApertureDB, n8n, MindsDB, Langflow

## Key Differentiators
- **Video-native multimodality:** Models are trained from the ground up to understand video as a temporal, spatial, multimodal object — not a combination of image models + transcript models. This is the fundamental architectural distinction from GPT-4o or Gemini applied to video
- **Marengo's any-to-any search:** A single model that handles text→video, image→video, audio→video, and video→video retrieval in the same embedding space — enabling search modalities that no other commercial API offers
- **AWS Bedrock availability:** Marengo 2.7 and Pegasus 1.2 are available as managed services in Amazon Bedrock, giving enterprises who've already standardized on AWS a zero-friction path to production
- **Indexing 3.0 portability:** Designed to deploy across cloud, private cloud, and on-premises — meeting enterprises in regulated industries (government, healthcare, finance) who cannot use public cloud for sensitive video
- **Benchmark-leading performance:** Independently benchmarked against cloud majors (AWS, Google, Azure) and open-source models on video understanding tasks — TwelveLabs claims top accuracy across search precision and generation quality

## Notable Customers & Integrations
**Customers:** MLSE (Maple Leaf Sports & Entertainment — NBA Raptors, NHL Maple Leafs; reduced sports highlight creation from days to minutes), SBS (Australian broadcaster), Protege.ai, Creator Discovery platform, Icon, Air, Source Digital, IQT, Digital Watchdog, Flytbase

**Partner integrations:** AWS, Databricks, MongoDB, Snowflake, Pinecone, Weaviate, LanceDB, Milvus, Elasticsearch, ApertureDB, MindsDB, Langflow, n8n, MASV, Blackbird (editorial AI), Pixeltable, Roe AI, Avid

**Available on:** AWS Amazon Bedrock (Marengo 2.7 + Pegasus 1.2)

## Pricing
- **Free:** Up to 10 hours of video indexing, 600-minute usage limit, 90 days of index access — no credit card required
- **Developer:** Unlimited indexing (usage-based pricing per minute of video)
- **Enterprise:** Dedicated environment, private deployment options, SLA guarantees, custom fine-tuning — contact sales

---

## Blog & Resources Highlights
_Drawn from actual article content_

### Announcing TwelveLabs Claude Code Plugin — March 2026
> TwelveLabs launched a Claude Code plugin that brings video intelligence into the terminal development workflow. The plugin uses the TwelveLabs MCP server and installs in three lines (plus API key), adding slash commands and natural-language "skills" for indexing, search, analysis, and embedding inside the Claude Code CLI. Key design insight: the plugin doesn't require developers to learn a new tool — it makes video "just another thing their agent can operate on." Supports async indexing (kick off, continue coding, check status), entity search (find a specific person using reference images), and multimodal search (text + image queries). MIT-licensed and built to be extended.

[Read more](https://www.twelvelabs.io/blog/claude-code-plugin)

### From Microservices Mesh to Streamlined Layers: Why We Rebuilt Our Internal Video Indexing System — February 2026
> A detailed engineering post explaining TwelveLabs' migration from a fragmented microservices-based indexing platform (Indexing 2.0) to a layered architecture (Indexing 3.0). The breaking point: not performance, but engineering throughput — a small team building on Indexing 2.0 couldn't reason about the full system end-to-end, and deployment was coupled to specific infrastructure. Indexing 3.0 separates concerns into three layers: indexing platform logic, Ray Serve execution, and swappable infrastructure substrate. Result: faster engineer onboarding, parallel team development, deployment across cloud/bare-metal/private environments, and structural cost efficiency from eliminating orchestration overhead.

[Read more](https://www.twelvelabs.io/blog/indexing-3-0-part-1)

### TwelveLabs x AWS Amazon Bedrock — July 2025
> TwelveLabs announced Marengo 2.7 and Pegasus 1.2 as managed services in Amazon Bedrock. The announcement highlights the company's mission: "unlock the 80% of global data hidden within video." AWS Bedrock integration means enterprise teams can deploy TwelveLabs models with AWS-native security, compliance, and redundancy — eliminating the need to manage a separate API key, egress, or SLA negotiation. Use cases highlighted include sports leagues finding player moments, public safety agencies reviewing incident footage, and media producers generating highlight reels.

[Read more](https://www.twelvelabs.io/blog/twelvelabs-x-aws-amazon-bedrock)

### Our Series A to Build the Future of Multimodal AI — June 2024
> TwelveLabs announced a $50M Series A co-led by NVIDIA NVentures and NEA, with participation from Index Ventures, Radical Ventures, and others. The post describes the company's core thesis: "AI systems need to learn from video to understand the world the way humans do." The funding is directed toward expanding the team and advancing Marengo and Pegasus models. The NVIDIA lead is significant: NVIDIA's investment validates TwelveLabs' GPU-accelerated inference approach and provides potential hardware roadmap alignment for future model generations.

[Read more](https://www.twelvelabs.io/blog/series-a-announcement)

### Semantic Content Discovery for a Post-Production World (TwelveLabs + Avid) — Blog
> This post explores how semantic search transforms post-production workflows for media teams. Traditional asset management relies on manual tagging, filename search, and transcript keyword matching — all of which fail for visual storytelling elements (camera angle, emotion, action). TwelveLabs' Marengo-powered search returns relevant clips based on semantic description (e.g., "two-shot of interviewees with natural light, serious tone") that no metadata system can index. The Avid integration brings this into the editorial suite, where editors can find B-roll in seconds instead of hours.

[Read more](https://www.twelvelabs.io/blog/twelve-labs-and-avid)

---

## Key Takeaways
- TwelveLabs is building the **AI infrastructure layer for video** — not a video product, but the API and model platform that powers video AI features inside other products (MAM systems, sports platforms, ad tech, surveillance)
- **Marengo's any-to-any search** is a genuinely unique capability: the ability to query a video library with text, images, audio, or video clips using a single model in a shared embedding space — enabling search patterns that weren't technically possible before
- The **AWS Bedrock availability** of Marengo 2.7 and Pegasus 1.2 massively expands enterprise addressability: organizations that won't adopt a new vendor API will adopt models through their existing AWS relationship
- **NVIDIA as a strategic investor** signals hardware-model alignment: as NVIDIA accelerates GPU compute for inference, TwelveLabs' models are positioned to be the beneficiary of those performance gains
- At NAB Streaming Summit, TwelveLabs' angle is **turning unstructured video archives into searchable, queryable data** — a critical capability for media companies sitting on decades of content that is currently invisible to their digital systems
