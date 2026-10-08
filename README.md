# LinkedIn Remote Jobs (n8n)

Daily n8n workflow that scrapes the public (guest) LinkedIn job search for remote jobs by
country, removes duplicates, filters out generic "talent pool" postings with an LLM (Groq)
and posts a digest to Discord.

Details:

- 3 result pages per country, numeric geoId for the countries where text locations clash
  with US towns of the same name
- location filter that understands formats like "Spain (Remote)"
- dedup in workflow static data
- AI filter in chunks with a wait between calls to stay inside Groq free-tier limits
- digest: up to 15 jobs per embed, 5 embeds per message

Only the public guest endpoint is used, no login and no cookies. Respect LinkedIn terms and
rate limits.

## Setup

1. Import `linkedin-remote-jobs-europe-armenia-russia-daily.json` in n8n.
2. Replace `YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN` in the Discord nodes with your webhook.
3. Put your Groq API key into the AI filter node (`Authorization` header).
