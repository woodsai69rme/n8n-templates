# CRM Sync

**Category:** Sales & Business  
**Complexity:** ⭐⭐⭐⭐  
**Estimated setup time:** 30 minutes  

## What It Does

Bidirectional sync between your CRM (HubSpot/Pipedrive) and your database. When a lead is created, enriched, or moved stages → triggers automated follow-ups, Slack notifications, and data enrichment.

## Triggers

- HubSpot webhook (new contact, deal stage change)
- Pipedrive webhook (new deal, status change)
- Schedule (hourly — full sync check)
- Manual webhook (`POST /webhook/sync`)

## Nodes Used

| Node | Purpose |
|---|---|
| HubSpot / Pipedrive | CRM API integration |
| PostgreSQL | Local database sync |
| HTTP Request (OpenRouter) | AI lead scoring, enrichment |
| Slack | Team notifications |
| Function | Data transformation, deduplication |
| Switch | Route per CRM event type |

## Requirements

- OpenRouter API key (`OPENROUTER_API_KEY`)
- CRM API credentials (HubSpot or Pipedrive)
- PostgreSQL connection string (`DATABASE_URL`)

## Configuration

| Variable | Default | Description |
|---|---|---|
| `CRM_TYPE` | `hubspot` | `hubspot` or `pipedrive` |
| `SYNC_INTERVAL` | `60` | Minutes between syncs |
| `AI_ENRICHMENT` | `true` | Enable AI lead enrichment |
| `NOTIFY_NEW_LEAD` | `true` | Slack notification on new lead |
| `NOTIFY_STAGE_CHANGE` | `true` | Slack notification on stage change |

## Sync Direction

| CRM Event | → | Database Action |
|---|---|---|
| New contact | → | INSERT into `contacts` |
| Contact updated | → | UPDATE in `contacts` |
| Deal created | → | INSERT into `deals` |
| Deal stage change | → | UPDATE `deals.stage` + notify |
| Deal won | → | UPDATE `deals.status = won` + celebrate |

## License

MIT — see [LICENSE](../../LICENSE).
