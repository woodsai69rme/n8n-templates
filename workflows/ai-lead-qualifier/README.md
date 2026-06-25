# n8n Workflow: AI Lead Qualifier

## Overview
Automatically scores web form leads using AI, routes hot leads to CRM, and sends Slack alerts for qualified prospects.

## Trigger
- **Webhook** — receives POST from your website contact form

## Flow
1. **Webhook** receives form data (name, email, company, message)
2. **OpenRouter (GPT-4o-mini)** scores the lead 1-10 based on:
   - Company size and industry relevance
   - Budget indicators in message
   - Urgency signals
   - Decision-maker language
3. **Switch node** routes based on score:
   - Score 8-10 (Hot): → Create HubSpot deal + Slack DM to sales
   - Score 5-7 (Warm): → Add to nurture sequence (Airtable)
   - Score 1-4 (Cold): → Auto-reply with helpful resources
4. **Slack** notification: "@channel 🔥 Hot lead: {name} from {company} — score {score}/10"
5. **Airtable** append: Logs all leads with scores for dashboard

## AI Prompt
```
Score this lead 1-10 based on likelihood to buy AI consulting services. 
Consider: company size, industry (tech/finance/healthcare = higher), 
budget signals, decision-maker role, and urgency.

Lead: {name}, {email}, {company}, Message: {message}

Return ONLY a JSON: {"score": N, "reasoning": "..."}
```

## Credentials Needed
- OpenRouter API key
- HubSpot API key (or Airtable)
- Slack webhook URL

## Import
1. Download `ai_lead_qualifier.json`
2. In n8n: Workflows → Import from file
3. Configure credentials in each node
4. Activate workflow
