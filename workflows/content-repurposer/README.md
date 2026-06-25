# n8n Workflow: Content Repurposer

## Overview
One blog post → auto-generate social media posts, email newsletter, and video script using AI.

## Trigger
- **Manual** or **Schedule** (e.g., every Monday 9am)

## Flow
1. **RSS Feed** or manual input fetches blog post URL
2. **HTTP Request** scrapes blog content
3. **OpenRouter (Claude 3 Haiku)** generates:
   - 3 Twitter/X posts (under 280 chars each)
   - 1 LinkedIn post (professional tone, 800 chars)
   - 1 TikTok/Reels script (60 seconds timed)
   - 1 Email newsletter version
4. **Buffer** node: Schedules social posts across platforms
5. **Mailchimp** node: Creates draft email campaign
6. **Google Docs**: Creates video script document

## AI Prompt
```
Repurpose this blog post into:
1. 3 Twitter posts (280 chars max each, include hashtags)
2. 1 LinkedIn post (professional, 800 chars, 3-5 hashtags)
3. 1 short-form video script (60 seconds, scene-by-scene)
4. 1 email newsletter version (subject line + 2 paragraphs + CTA)

Blog: {content}

Return JSON: {"twitter": ["...","...","..."], "linkedin": "...", "video_script": "...", "email": {"subject": "...", "body": "..."}}
```

## Credentials Needed
- OpenRouter API key
- Buffer API token
- Mailchimp API key
- Google service account

## Import
1. Download `content_repurposer.json`
2. In n8n: Workflows → Import from file
3. Configure credentials
4. Activate workflow
