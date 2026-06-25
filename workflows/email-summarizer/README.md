# Email Summarizer

**Category:** Productivity  
**Complexity:** ⭐  
**Estimated setup time:** 10 minutes  

## What It Does

Monitors your inbox, uses AI to summarize new emails, and sends a daily digest to Slack or Telegram. Never miss important emails buried in your inbox.

## Triggers

- Gmail webhook (new email received)
- Schedule (daily at 8am — morning digest)

## Nodes Used

| Node | Purpose |
|---|---|
| Gmail Trigger | Detect new emails |
| HTTP Request (OpenRouter) | AI summarization |
| Filter | Skip spam/promotions |
| Function | Format digest message |
| Slack / Telegram | Send daily digest |

## Requirements

- OpenRouter API key (`OPENROUTER_API_KEY`)
- Gmail OAuth2 credentials
- Slack webhook URL (`SLACK_WEBHOOK_URL`) or Telegram bot token

## Configuration

| Variable | Default | Description |
|---|---|---|
| `DIGEST_TIME` | `08:00` | Daily digest send time |
| `MAX_EMAILS_PER_DIGEST` | `20` | Max emails in digest |
| `AI_MODEL` | `openai/gpt-4o-mini` | OpenRouter model |
| `SKIP_LABELS` | `spam,promotions,social` | Labels to skip |

## Example Digest Output

```
📧 Morning Email Digest — 5 new emails

🔴 URGENT (1):
• Client: "Server down — need help ASAP" → Reply

🟡 IMPORTANT (2):
• Stripe: "Monthly payout processed — $450 AUD"
• Hostinger: "Domain renewal — ausai.tech expires in 30 days"

🟢 UPDATES (2):
• Newsletter: AI Weekly — 3 interesting articles
• GitHub: woodsai69rme starred your repo
```

## License

MIT — see [LICENSE](../../LICENSE).
