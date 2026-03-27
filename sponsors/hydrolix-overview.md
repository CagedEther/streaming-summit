# Hydrolix — Overview

> Real-time analytics at the speed of insight — for massive, log-intensive workloads

## What They Do
Hydrolix is a real-time data platform purpose-built for high-volume log analytics — specifically optimized for the scale of CDN log data, streaming observability, and cybersecurity telemetry. Where conventional observability platforms struggle with petabyte-scale log volumes (and charge accordingly), Hydrolix delivers sub-second query latency at 20–50x compression ratios, using a decoupled compute-storage architecture built on object storage. For media and entertainment companies specifically, Hydrolix powers real-time CDN monitoring across multiple providers, quality-of-experience analytics for live and on-demand events, and an emerging bot traffic intelligence product.

## At a Glance
- **Website:** https://www.hydrolix.io
- **Industry:** Streaming Data Platform / Observability & Analytics
- **Stage/Positioning:** Private company; venture-backed; available on AWS Marketplace and deployable as Bring Your Own Cloud (BYOC)

## Products & Services

### Hydrolix Platform (Core)
The underlying data engine with four functions: **Stream** (real-time ingest of tens of millions of events per second, including during peak live events like the Super Bowl or Olympics), **Transform** (streaming ETL that standardizes, enriches, and masks data before storage — vendor field names are normalized at ingest time, not at query time), **Store** (columnar object storage with 20–50x compression; all data remains "hot" — immediately queryable regardless of age), and **Search** (SQL-based queries with sub-second latency across petabyte-scale datasets; supports natural-language queries via AI assistants including MCP integration with Claude).

Architecture is decoupled: compute nodes (query pools) scale independently from storage, and multiple query pools can be provisioned to prevent resource contention between different workloads (e.g., real-time dashboards vs. batch analytics). The storage layer is any S3-compatible bucket — AWS, GCP, Azure, Akamai, MinIO, Linode — and in the BYOC model, data never leaves the customer's cloud account.

### CDN Insights
A pre-built solution bundle for CDN monitoring across multiple providers. Integrates with Akamai, AWS CloudFront, Cloudflare, Fastly, Tencent, Varnish, CacheFly, and more via real-time log streaming connectors. A unified dashboard shows performance metrics, error rates, cache hit ratios, TTFB, TLS performance, and geographic distribution across all CDNs simultaneously — with no sampling, full-fidelity data retained for 15+ months. Operators can drill to individual log records in sub-second time. Multi-schema tables allow logs from different CDN vendors (with different field names) to be ingested into a single normalized table — Paramount used this approach to consolidate Akamai, Fastly, and CloudFront logs into a unified view, reducing infrastructure spend by 50% while increasing retention 6x.

### Bot Insights
A pre-built solution for analyzing bot traffic across CDN infrastructure. Launched in January 2026, it provides long-term visibility (beyond the typical 30-day window of existing bot management tools) into AI bot crawl behavior, search engine bot activity, content scraper patterns, and DDoS bot signatures. Covers Akamai, Fastly, Cloudflare, Tencent EdgeOne, and AWS CloudFront (80% of global CDN traffic). Enables strategic decisions about which AI bots to allow (for generative engine optimization / GEO) vs. block (for content protection), backed by months of historical trend data. Deployed via AWS Marketplace or Akamai TrafficPeak.

### TrafficPeak (Akamai Partnership)
Hydrolix is the underlying engine for TrafficPeak — Akamai's observability product for its CDN customers. Akamai-hosted Hydrolix clusters provide Akamai customers with real-time CDN analytics at the scale their traffic requires.

## Solutions & Use Cases
- **Live Event Observability:** Real-time monitoring during Super Bowl, Olympics, major sports finals — where 50–100M simultaneous viewers generate tens of millions of log events per second and any quality issues must be diagnosed and resolved within seconds.
- **Multi-CDN Performance Monitoring:** Unified dashboards across Akamai, Fastly, CloudFront, Cloudflare and others — comparing cache hit ratios, error rates, and delivery latency across providers to drive CDN routing decisions and contract negotiations.
- **Ad Delivery Performance:** Tracking ad fill rates, delivery gaps, and error trends by CDN, geography, and device type — critical for SSAI/SGAI workflows where ad delivery failures translate directly to revenue loss.
- **Quality-of-Experience Analytics:** Enriching CDN logs with device intelligence to understand how streaming performance varies across thousands of device profiles (smart TVs, mobile, web, CTV).
- **Long-Term Data Retention for Compliance & Trend Analysis:** Retaining 15+ months of full-fidelity CDN data for year-over-year event comparison, capacity planning, and vendor contract negotiations — common observability platforms truncate at 30–90 days.
- **Bot Traffic Analysis:** Understanding how AI bots (GPTBot, ClaudeBot, PerplexityBot) interact with streaming content and CDN infrastructure — particularly relevant as agentic AI begins accessing video content at scale.
- **Cybersecurity / Threat Hunting:** Analyzing DNS, Netflow, WAF, and CDN logs at petabyte scale for security operations teams. Customers include Arkose Labs (fraud prevention), Allure Security (brand impersonation detection), and Elkjøp (DDoS detection).

## Technology & Architecture
Hydrolix's core engine is built on a columnar storage format with advanced compression (achieving 20–50x ratios compared to raw log data). The architecture separates compute from storage entirely — query nodes are stateless and can be provisioned or terminated in minutes, while data remains permanently accessible in object storage. This is architecturally distinct from systems like Elasticsearch that co-locate compute and storage, making independent scaling impossible.

Ingest uses streaming ETL: data is transformed, normalized, and enriched at write time using SQL transform pipelines (including ClickHouse SQL functions, custom UDFs, and in-memory dictionary lookups). This means queries are faster at read time — the expensive work (field renaming, URL parsing, dictionary enrichment) happens once at ingest rather than on every query.

For multi-CDN use cases, Hydrolix multi-schema tables accept multiple sources with different schemas into a single table — different CDNs can use different field names for the same concept (e.g., Akamai uses `statusCode`, Fastly uses `status`, both normalize to `status_code`). Virtual columns add constant or computed metadata (e.g., `source: "fastly"`) without requiring the source data to include it. SQL transforms with `dictGet()` lookups enrich log records with business labels (stream name, environment, business unit) from in-memory dictionaries at ingest time — enabling sub-second group-by queries on those fields without runtime joins.

The Hydrolix Merge Service runs continuously, reorganizing partitions in the background to improve query performance, compression ratios, and storage efficiency — solving the "small files problem" that accumulates when high-speed ingest creates many small partitions.

## Key Differentiators
- **Sub-second queries on petabyte-scale data with no sampling:** Competing platforms either sample data (degrading analytics accuracy) or require expensive compute clusters to maintain query speed on large datasets.
- **20–50x compression ratios:** Dramatically reduces storage costs vs. raw log storage; enables long-term retention that would be cost-prohibitive on platforms like Splunk or Elasticsearch.
- **Cost reduction of 4x–200x** compared to traditional observability platforms (per customer case studies) — the economic case for Hydrolix is often the primary driver of adoption.
- **Full-fidelity, 15+ month retention:** Most CDN monitoring tools truncate at 30 days; Hydrolix retains all data indefinitely (in BYOC mode, unlimited retention).
- **Decoupled compute-storage architecture:** Query pools can be scaled independently, preventing large analytical queries from impacting real-time monitoring dashboards.
- **BYOC model preserves data sovereignty:** For media companies with sensitive viewer data, BYOC ensures data never leaves their cloud account.
- **Streaming ETL at ingest:** Field normalization and enrichment happen at write time, enabling faster queries and consistent data models across heterogeneous CDN log sources.
- **MCP integration for natural-language queries:** Hydrolix Remote MCP lets engineers query petabyte-scale data using natural language (Claude-powered), enabling faster incident resolution without SQL expertise.

## Notable Customers & Integrations
**Customers:** Paramount (multi-CDN monitoring across Akamai, Fastly, CloudFront; 50% cost reduction, 6x retention increase), Fox, DAZN, Olympics, Super Bowl, Arkose Labs, Allure Security, Elkjøp, Navy Federal Credit Union (financial services), airline (unnamed)

**CDN Integrations:** Akamai, AWS CloudFront, Cloudflare, Fastly, Tencent EdgeOne, Varnish, CacheFly, Google Media CDN

**Data Shipper Integrations:** Cribl, Vector, Fluent Bit, Journald, Apache Kafka, custom HTTP sources

**Visualization/Dashboard Integrations:** Grafana (out-of-box), Kibana, Apache Superset, Redash, Tableau, Looker

**Cloud/Infrastructure Integrations:** AWS, GCP, Azure, Akamai Connected Cloud, MinIO, Linode; Databricks, AWS EMR, Microsoft Fabric, Apache Spark (for federated analytics)

**Media Stack Integrations:** AWS Elemental MediaLive, MediaPackage, MediaTailor; Mux, Bitmovin, Datazoom

## Pricing
- **Hydrolix Cloud (HDX):** $0.45 per GB ingested; 15 months retention included
- **Bring Your Own Cloud (BYOC):** $0.20 per GB ingested; unlimited retention; data stored in customer's own cloud account
- Available on AWS Marketplace with free trial

---

## Blog & Resources Highlights
_Curated from actual article content on the Hydrolix blog_

### Multi-CDN Monitoring — How Paramount Uses Hydrolix — October 2023 (updated March 2026)
> A technical deep-dive into how Paramount consolidated CDN logs from Akamai, Fastly, AWS CloudFront, and Google Media CDN into a single normalized Hydrolix table — enabling unified monitoring across all four providers. The post details Hydrolix multi-schema table configuration, per-vendor transform files that standardize inconsistent field names (e.g., Akamai's `statusCode` vs. Fastly's `status` → common `status_code`), virtual columns for tagging records with CDN source at ingest time, and SQL transforms using ClickHouse functions and dictionary lookups to enrich records with business labels (stream, environment, business unit). Paramount's PoC team estimated 50% infrastructure cost reduction and 6x increase in data retention period.
[Read more](https://hydrolix.io/blog/multi-cdn-monitoring)

### Bot Insights: Strategic Bot Management for the AI Era — January 2026
> Introduces Hydrolix Bot Insights, launched in response to automated traffic reaching 51% of web traffic in 2024 (per Imperva). The article explains why AI bots present a fundamentally different challenge than traditional scrapers — they may not drive traffic back to your site the way search engine bots do, but they influence how your brand appears in LLM-generated answers (generative engine optimization / GEO). Bot Insights provides 15+ months of historical bot traffic analytics across five CDNs, enabling organizations to understand crawl frequency by AI vendor, distinguish valuable bots (search engines, ad verification) from harmful ones (content scrapers, bot networks), and make policy decisions backed by data rather than 30-day snapshots.
[Read more](https://hydrolix.io/blog/bot-insights)

### Unified Visibility Across Playback and Delivery — March 2026
> A guest post co-authored with Bitmovin explaining why CDN-level observability alone is insufficient for streaming quality assurance — you also need player-side quality-of-experience data to understand the full picture. Argues that correlating CDN delivery logs with player playback events (rebuffering, startup time, bitrate switches) requires a platform that can handle both datasets at scale and join them in real time. Positions Hydrolix + Bitmovin as a combined solution for streaming event observability that spans from origin to end user.
[Read more](https://hydrolix.io/blog/multi-cdn-monitoring)

### The Hydrolix Merge Service: A Deep Dive — March 2026
> Engineering blog explaining the fundamental tension in streaming data platforms: fast ingest creates small files and poor query layout; slow ingest creates better layout but can't keep up with high-volume sources. Hydrolix's Merge Service runs continuously in the background, reorganizing small partitions created during peak ingest into larger, better-compressed, more query-efficient partitions — without interrupting ongoing ingest or serving queries. The post details the merge scheduling algorithm, how partition selection prioritizes high-impact merges, and how compression improves as data ages.
[Read more](https://hydrolix.io/blog/multi-cdn-monitoring)

### Analyzing CDN Logs with Natural Language: How We Taught Claude to Write SQL — February 2026
> Documents Hydrolix's implementation of an MCP (Model Context Protocol) server that allows Claude to generate ClickHouse SQL queries against Hydrolix tables using plain English. An engineer investigating a CDN incident described the problem in natural language — "show me error rates by edge location for the past 2 hours grouped by status code" — and received a validated SQL query that resolved the incident in minutes. Discusses the challenges of teaching an LLM about Hydrolix's specific schema structures, transform conventions, and ClickHouse SQL dialect.
[Read more](https://hydrolix.io/blog/multi-cdn-monitoring)

---

## Key Takeaways
- **The Paramount case study is the media industry anchor:** Cutting infrastructure cost 50% and increasing retention 6x while monitoring four CDN providers simultaneously is a compelling proof point for any multi-CDN streaming operator.
- **Hydrolix is solving the "too much data to keep, too little data to diagnose" paradox:** Most streaming teams discard CDN log data after 30 days because retention is too expensive; Hydrolix makes it economical to retain everything, enabling year-over-year comparison and long-horizon trend analysis.
- **Bot traffic is an emerging strategic issue for streaming:** As AI agents begin accessing streaming content at scale, CDN infrastructure faces a new category of high-volume, hard-to-classify traffic. Bot Insights positions Hydrolix at the intersection of CDN analytics and AI agent governance.
- **The cost argument is almost always the conversation starter:** At $0.20–0.45/GB vs. Splunk's or Elasticsearch's typical pricing at 10–20x more, Hydrolix's economics often make existing observability budgets redundant — the savings pay for the migration.
- **Streaming-industry relationships are deepening:** Partnerships with Akamai (TrafficPeak), AWS Elemental, Bitmovin, Mux, and Datazoom position Hydrolix as infrastructure-layer analytics for the media tech stack, not just a general data platform.
