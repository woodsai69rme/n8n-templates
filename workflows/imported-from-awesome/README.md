# 5 N8N Workflows — Imported from awesome-n8n-templates

> Community-curated automation templates. Full attribution in [ATTRIBUTION.md](./ATTRIBUTION.md).

---

## 01: AI Agent Chat (`01-ai-agent-chat.json`)
**Category**: Chatbot
**Best for**: Customer support, internal Q&A, AI assistant

A complete AI agent implementation using OpenAI and n8n. Includes context management and conversational flow.

**Required setup**:
- OpenAI API key (or OpenRouter for free models)
- n8n instance (Docker or local)

---

## 02: AI Web Scraper (`02-ai-web-scraper.json`)
**Category**: Web Scraping
**Best for**: Lead generation, market research, content aggregation

An AI agent that can scrape any webpage and extract structured data using natural language prompts.

**Required setup**:
- OpenAI API key
- Target URLs (configure in node)

---

## 03: Chart Analyzer (Vision) (`03-chart-analyzer-vision.json`)
**Category**: Vision AI
**Best for**: Trading analysis, financial research, technical analysis

Uses a Chrome extension + OpenAI vision to analyze trading charts from TradingView and returns structured insights.

**Required setup**:
- Chrome extension installed
- OpenAI Vision API key
- TradingView account (optional)

---

## 04: HuggingFace Paper Summarizer (`04-hf-paper-summarizer.json`)
**Category**: Research Automation
**Best for**: Academic research, AI/ML research, content curation

Automatically fetches new papers from HuggingFace, summarizes them via AI, and categorizes by topic.

**Required setup**:
- OpenAI/OpenRouter API key
- HuggingFace RSS feed (free)

---

## 05: Financial RAG Assistant (`05-financial-rag-assistant.json`)
**Category**: RAG (Documents)
**Best for**: Legal docs analysis, financial research, compliance

Uses Qdrant + Mistral AI to build a RAG pipeline over financial documents. Ideal for high-value enterprise services.

**Required setup**:
- Qdrant instance (Docker or cloud)
- Mistral AI API key
- Financial documents corpus

---

## Quick Start

```bash
# Start n8n (if using Docker)
docker run -it --rm --name n8n -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n

# Then open http://localhost:5678
# Workflows → Import from File → Select JSON
```

## License & Attribution

All workflows are imported from:
**https://github.com/enescingoz/awesome-n8n-templates**

Original authors retain credit. See [ATTRIBUTION.md](./ATTRIBUTION.md) for full credits.
