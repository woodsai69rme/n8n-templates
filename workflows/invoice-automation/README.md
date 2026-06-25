# Invoice Automation

**Category:** Finance & Admin  
**Complexity:** ⭐⭐⭐  
**Estimated setup time:** 25 minutes  

## What It Does

Automatically generates, sends, and tracks invoices. Monitors a Google Sheet for new billing entries → generates PDF invoice via AI → emails to client → records payment status.

## Triggers

- New row in Google Sheets (billing tracker)
- Manual webhook (`POST /webhook/send-invoice`)
- Schedule (daily at 9am — sends pending invoices)

## Nodes Used

| Node | Purpose |
|---|---|
| Google Sheets | Read billing data |
| HTTP Request (OpenRouter) | Generate invoice content/line items |
| HTML Template | Invoice layout template |
| Convert to PDF | Convert HTML to PDF |
| Gmail | Send invoice email |
| Google Sheets (Write) | Update payment status |
| Stripe | Create payment link (optional) |

## Requirements

- OpenRouter API key (`OPENROUTER_API_KEY`)
- Google Sheets OAuth2 credentials
- Gmail OAuth2 credentials (sender email)
- Stripe API key (optional — for payment links)

## Configuration

| Variable | Default | Description |
|---|---|---|
| `BILLING_SHEET_ID` | `your-sheet-id` | Google Sheets ID |
| `COMPANY_NAME` | `AusAI Tech` | Company name on invoice |
| `COMPANY_ABN` | — | Australian Business Number |
| `CURRENCY` | `AUD` | Invoice currency |
| `PAYMENT_TERMS` | `14` | Days until due |
| `LATE_FEE_PCT` | `5` | Late fee percentage |

## Invoice Template Variables

```
{{COMPANY_NAME}}        — Your company name
{{CLIENT_NAME}}         — Client business name
{{INVOICE_NUMBER}}      — Auto-incremented (INV-001, INV-002...)
{{DATE}}                — Issue date
{{DUE_DATE}}            — Payment due date
{{LINE_ITEMS}}          — Auto-generated from Google Sheet
{{TOTAL_AUD}}           — Total in AUD
{{STRIPE_LINK}}         — Payment link (if enabled)
```

## License

MIT — see [LICENSE](../../LICENSE).
