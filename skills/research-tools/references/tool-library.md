# Tool library

Version: 0.1.0 · Compiled: 2026-09-25

The starting point for each module's tool research. These are examples per job, not endorsements. Prices and free tiers change often: treat every entry older than 90 days as needing a recheck before recommending it, and always confirm current pricing on the vendor's site.

Tags: `free` = free or free tier · `open` = open-source, self-host · `paid` = subscription or pay per use · `connector` = a Claude connector is known to exist.

## 01 Signals

| Job | Options | Notes |
| --- | --- | --- |
| Search queries | Google Search Console (free, connector) · Semrush (paid) | |
| Site behavior | Google Analytics 4 (free, connector) · Microsoft Clarity (free) · Hotjar (paid) | |
| Competitor ranks | DataForSEO (paid per call, connector) · Ahrefs Webmaster Tools (free) · Ahrefs, Semrush (paid) | |
| Search interest | Google Trends (free) · Exploding Topics (paid) | |
| Social insights | Meta Business Suite (free) · Sprout Social (paid) | |
| Audience intel | Reddit (free, connector) · SparkToro (free tier) · Apify scrapers (paid, connector) | |
| Channel analytics | YouTube Studio and other native insights (free) | |
| Mentions | Google Alerts (free) · Brand24 (paid) | |

## 02 System of record

| Job | Options | Notes |
| --- | --- | --- |
| CRM and contacts | HubSpot free CRM (free) · Twenty (open) · HubSpot paid, Attio (paid) | |
| Content calendar | Notion or Airtable free tier (free) · Airtable (paid) | |
| Asset drive | Google Drive (free tier, connector) · Dropbox (paid) | |
| Playbook wiki | GitHub markdown (free, connector) · Notion (free tier) · Obsidian (free) | |
| Customer data platform | RudderStack (open) · Segment (paid) | Skip until three or more data sources need joining |
| Store | Shopify (paid, connector) · WooCommerce (open) | |
| Email and SMS list | Klaviyo (paid, connector) · Kit (free tier) | |

## 03 Brain

| Job | Options | Notes |
| --- | --- | --- |
| Reasoning | Claude (paid) · local models via Ollama (open) | |
| Agent runner | Claude scheduled tasks and skills (paid) · n8n self-hosted (open) · LangGraph (open) | |
| Memory store | Supabase with pgvector (free tier, connector) · NotebookLM (free, connector) · Pinecone (paid) | |
| Images | kie.ai image models (paid, connector) · Canva (free tier) · Midjourney (paid) | |
| Voiceover | ElevenLabs (free tier, paid) | |
| Live research | Claude web search (paid) · Perplexity (free tier) | |

## 06 Departments

| Job | Options | Notes |
| --- | --- | --- |
| Research and intel | DataForSEO (paid, connector) · Reddit (free, connector) · Google Trends (free) | |
| Content drafting and editing | Claude with the project's /content files · LanguageTool (free) · Grammarly (paid) · Surfer SEO (paid) | |
| Creative | kie.ai (paid, connector) · Canva (free tier) · Figma (free tier) · Remotion coded video (open) · ElevenLabs (paid) | |
| Scheduling and publishing | Buffer (free tier, paid) · Postiz (open) · Typefully (paid) · native schedulers (free) | |
| Email, newsletters, landing pages | Klaviyo (paid, connector) · Shopify Email (paid, connector) · Kit (free tier) · Carrd (free tier) | |
| Analytics | GA4 (free, connector) · Search Console (free, connector) · Looker Studio (free) · Plausible (paid) | |

## 07 Engage

| Job | Options | Notes |
| --- | --- | --- |
| DM and comment replies | ManyChat (free tier, paid) · native inboxes (free) | |

## 08 Data and observability

| Job | Options | Notes |
| --- | --- | --- |
| Pipelines | Airbyte (open) · Fivetran (paid) | Add only when reports get slow or need history |
| Transform | dbt Core (open) · dbt Cloud (paid) | |
| Warehouse | Supabase Postgres (free tier, connector) · BigQuery sandbox (free) | |
| Reporting | Looker Studio (free) · Metabase (open) | |
| Error tracking | Sentry (free tier, paid) | |

## Change log

| Date | Change | From project |
| --- | --- | --- |
| 2026-09-25 | First version, from the Marketing OS blueprint | Agentic Marketing |
