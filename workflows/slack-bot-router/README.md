# Slack Bot Router

**Category:** Communication  
**Complexity:** ⭐⭐⭐  
**Estimated setup time:** 20 minutes  

## What It Does

Intelligent Slack bot that routes messages to the right AI service based on intent. `/ask` queries your knowledge base, `/summarize` condenses threads, `/code` generates/debugs code, `/image` creates AI images. All powered by OpenRouter.

## Triggers

- Slack slash command (`/ask`, `/summarize`, `/code`, `/image`)
- Slack @mention (bot responds in thread)
- DM to bot (direct conversation)

## Nodes Used

| Node | Purpose |
|---|---|
| Slack Trigger | Catch slash commands |
| Switch | Route by command type |
| HTTP Request (OpenRouter) | AI model inference |
| HTTP Request (RAG) | Knowledge base search |
| HTTP Request (ComfyUI) | Image generation (optional) |
| Function | Format responses |
| Slack (Reply) | Post response back |

## Requirements

- OpenRouter API key (`OPENROUTER_API_KEY`)
- Slack bot token + signing secret
- Optional: RAG API endpoint for knowledge base
- Optional: ComfyUI for image generation

## Configuration

| Variable | Default | Description |
|---|---|---|
| `SLACK_BOT_TOKEN` | `xoxb-...` | Slack bot OAuth token |
| `SLACK_SIGNING_SECRET` | — | Slack app signing secret |
| `DEFAULT_MODEL` | `openai/gpt-4o-mini` | OpenRouter model for `/ask` |
| `CODE_MODEL` | `anthropic/claude-sonnet` | Model for `/code` |
| `IMAGE_MODEL` | ComfyUI local | Local image gen |
| `MAX_THREAD_LENGTH` | `50` | Max messages to summarize |

## Commands

| Command | Description | AI Model |
|---|---|---|
| `/ask [question]` | Query knowledge base + AI | GPT-4o-mini |
| `/summarize` | Summarize current thread | Claude Haiku |
| `/code [prompt]` | Generate/debug code | Claude Sonnet |
| `/image [prompt]` | Generate AI image | ComfyUI (local) |

## Example Interaction

```
User: /ask What's our Q2 revenue projection?
Bot:  Based on current pipeline: A$4,000/mo by end of Q2 (90-day projections).
      Sources: REAL_MONEY_PLAN_2026-06-25.md
```

## License

MIT — see [LICENSE](../../LICENSE).
