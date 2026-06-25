# Data Enrichment

**Category:** AI & Automation  
**Complexity:** ⭐⭐⭐  
**Estimated setup time:** 20 minutes  

## What It Does

Takes a list of company names or domains, enriches each with AI-researched data (industry, size, tech stack, key contacts), and outputs to Google Sheets or Airtable. Perfect for sales prospecting and lead qualification.

## Triggers

- Google Sheets new row (company name added)
- Manual webhook (`POST /webhook/enrich`)
- CSV file upload (watch folder)

## Nodes Used

| Node | Purpose |
|---|---|
| Google Sheets | Read/write enrichment data |
| HTTP Request (OpenRouter) | AI research per company |
| HTTP Request (Clearbit/BuiltWith) | Tech stack detection |
| Function | Parse and normalize AI output |
| Google Sheets (Write) | Write enriched data back |
| Split In Batches | Process companies in parallel |

## Requirements

- OpenRouter API key (`OPENROUTER_API_KEY`)
- Google Sheets OAuth2 credentials
- Optional: Clearbit API key for tech stack

## Configuration

| Variable | Default | Description |
|---|---|---|
| `BATCH_SIZE` | `5` | Companies per batch |
| `AI_MODEL` | `openai/gpt-4o` | OpenRouter model |
| `ENRICH_INDUSTRY` | `true` | Research industry |
| `ENRICH_TECH_STACK` | `true` | Detect tech stack |
| `ENRICH_CONTACTS` | `true` | Find key contacts |
| `ENRICH_NEWS` | `true` | Recent news/funding |

## Enriched Fields Output

| Field | Source | Example |
|---|---|---|
| `company_name` | Input | AusAI Tech |
| `industry` | AI | AI/ML Consulting |
| `employee_count` | AI | 1-10 |
| `estimated_revenue` | AI | $50K-$200K |
| `tech_stack` | BuiltWith/Clearbit | React, FastAPI, Supabase |
| `key_contacts` | AI | CEO, CTO names |
| `recent_news` | AI | Launched Q2 product |
| `ai_readiness_score` | AI | 8/10 |

## License

MIT — see [LICENSE](../../LICENSE).
