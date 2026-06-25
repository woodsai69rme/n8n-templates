# ⚡ n8n Automation Templates

> Production-ready n8n workflow templates for AI-powered business automation. Self-hosted, no vendor lock-in.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![n8n](https://img.shields.io/badge/n8n-Latest-red)](https://n8n.io)

## 🚀 Quick Start

1. [Install n8n](https://docs.n8n.io/hosting/) (Docker recommended)
2. Import the `.json` workflow file from `workflows/`
3. Configure your API credentials in the n8n UI
4. Activate the workflow — done.

## 📋 Templates

| # | Workflow | Use Case | Services |
|---|---|---|---|
| 1 | **AI Lead Qualifier** | Auto-score web form leads, route hot leads to CRM | OpenRouter, Airtable, Slack |
| 2 | **Content Repurposer** | Blog → social posts → email blast pipeline | OpenRouter, Buffer, Mailchimp |
| 3 | **Invoice Generator** | Auto-generate + email invoices from tracked hours | Google Sheets, Gmail |
| 4 | **AI Email Assistant** | Categorise + draft replies + flag urgent | OpenRouter, Gmail |
| 5 | **Data Enrichment** | Enrich CRM contacts via web search + AI | OpenRouter, HubSpot, Clearbit |
| 6 | **Social Media Monitor** | Track brand mentions → AI sentiment → Slack alert | RSS, OpenRouter, Slack |
| 7 | **AI Image Pipeline** | Form trigger → ComfyUI API → image → email | Webhook, ComfyUI, Gmail |
| 8 | **RAG Q&A Bot** | Upload PDF → vector store → answer questions | OpenRouter, Pinecone, Slack |

## 🔧 Requirements

- **n8n** (self-hosted, v1.0+)
- **OpenRouter API key** (for AI nodes)
- **Docker** (recommended for n8n hosting)

Optional service credentials depend on which workflows you use (see each workflow's README).

## 🐳 Docker Quick Start

```bash
docker run -d \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  -e N8N_SECURE_COOKIE=false \
  docker.n8n.io/n8nio/n8n
```

## 🤝 Services

Need a custom n8n workflow? [AusAI Tech](https://ausai.tech) builds production automation pipelines — from A$1,500.

## 📄 License

MIT — use freely, attribution appreciated.
