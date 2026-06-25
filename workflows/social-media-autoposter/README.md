# Social Media Auto-Poster

**Category:** Content & Marketing  
**Complexity:** ⭐⭐  
**Estimated setup time:** 15 minutes  

## What It Does

Automatically posts new blog articles or content to Twitter/X, LinkedIn, and Facebook simultaneously. Uses AI to generate platform-optimized captions and hashtags.

## Triggers

- New RSS feed item detected (blog post published)
- Manual webhook trigger (`POST /webhook/social-post`)
- Schedule (every 4 hours — checks for new content)

## Nodes Used

| Node | Purpose |
|---|---|
| RSS Feed Read | Monitor blog RSS feed |
| HTTP Request (OpenRouter) | Generate AI caption + hashtags per platform |
| Twitter/X API | Post tweet |
| LinkedIn API | Post LinkedIn update |
| Facebook Pages API | Post Facebook update |
| Webhook | Manual trigger endpoint |
| Switch | Route per platform/language |

## Requirements

- OpenRouter API key (set as credential `OPENROUTER_API_KEY`)
- Twitter API credentials (set as `TWITTER_*`)
- LinkedIn API credentials (set as `LINKEDIN_*`)
- Facebook Page access token (set as `FACEBOOK_*`)

## Configuration

| Variable | Default | Description |
|---|---|---|
| `RSS_FEED_URL` | `https://ausai.tech/rss.xml` | Blog RSS feed |
| `POST_FREQUENCY` | `4` | Hours between checks |
| `MAX_POSTS_PER_RUN` | `3` | Max posts per check |
| `AI_MODEL` | `openai/gpt-4o-mini` | OpenRouter model for captions |

## Platform-Specific Formats

- **Twitter/X:** 280 chars max, 1-3 hashtags, optional image
- **LinkedIn:** 1000-2000 chars, professional tone, 3-5 hashtags
- **Facebook:** Similar to LinkedIn, more casual tone OK

## License

MIT — see [LICENSE](../../LICENSE).
