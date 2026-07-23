# AI Competitor News Monitor & Weekly Digest

An automated **n8n workflow** that monitors recent AI and automation news, summarizes important developments using OpenAI, and sends a professional weekly digest through **Gmail and Slack**.

---

## Project Overview

This workflow runs every Monday at **9:00 AM Central Time** and collects recent AI and automation news from two public RSS sources.

The workflow filters articles from the previous seven days, removes duplicate and unrelated stories, and sends the selected content to OpenAI GPT-4o-mini. The final digest includes an executive summary, key takeaways, competitor updates, industry trends, recommended actions, and source links.

---
## How to Use

1. Download the workflow file:

   `AI Competitor News Monitor & Weekly Digest.json`

2. Import the JSON file into n8n.

3. Connect your own credentials:

   - OpenAI
   - Gmail
   - Slack

4. Update the destination Gmail address.

5. Select the destination Slack channel.

6. Confirm the workflow timezone is:

   `America/Chicago`

7. Test the complete workflow.

8. Confirm that Gmail and Slack receive the digest.

9. Activate or publish the workflow.

> API keys, passwords, OAuth tokens, and private credentials are not included in the shared workflow.
---

## Workflow Architecture

```text
Schedule Trigger
       ↓
Google News RSS + TechCrunch AI RSS
       ↓
Merge Feeds
       ↓
Parse RSS Data
       ↓
Filter Recent and Relevant Articles
       ↓
Remove Duplicate Stories
       ↓
Check Whether Articles Exist
       ↓
OpenAI Summarization
       ↓
Format for Gmail and Slack
       ↓
Send Weekly Digest
```

When no relevant articles are found, the workflow sends separate no-news notifications through Gmail and Slack.

---

## Workflow Features

- Runs every Monday at **9:00 AM**
- Uses the `America/Chicago` timezone
- Collects news from two public RSS sources
- Uses Google News RSS for broad AI and automation coverage
- Uses TechCrunch AI RSS for focused technology and funding news
- Keeps articles published during the previous seven days
- Rejects articles with missing or invalid publication dates
- Filters unrelated stories
- Removes duplicate and highly similar articles
- Sorts articles by publication date
- Limits the final AI input to 15 articles
- Uses OpenAI GPT-4o-mini for summarization
- Generates three key takeaways
- Identifies competitor updates and industry trends
- Includes source links for important claims
- Formats the Gmail digest as styled HTML
- Formats the Slack digest using Slack-compatible formatting
- Sends fallback notifications when no news is found

---

## News Sources

### Google News RSS

Google News RSS provides broad coverage across topics such as:

- Artificial intelligence
- Generative AI
- AI agents
- Workflow automation
- OpenAI
- Anthropic
- Google Gemini
- Microsoft Copilot
- n8n
- Zapier
- Make.com

### TechCrunch AI RSS

TechCrunch AI provides focused reporting about:

- AI products
- Startups
- Funding
- Partnerships
- Acquisitions
- Product launches
- Strategic industry developments

Using both sources provides a balance between broad market coverage and focused AI business reporting.

---

## Digest Structure

The final weekly digest contains:

1. Executive Summary
2. Key Takeaways
3. Competitor Updates
4. Industry Trends
5. Recommended Actions
6. Sources Reviewed

The digest is delivered through:

- **Gmail** as a styled HTML email
- **Slack** as a channel message

---

## AI Tools Used

| Tool | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| OpenAI GPT-4o-mini | News summarization and competitor analysis |
| ChatGPT | Workflow design, debugging, JavaScript improvement, and prompt development |

---

## Model Settings

- **Model:** GPT-4o-mini
- **Temperature:** 0.3
- **Maximum output tokens:** 1800

GPT-4o-mini was selected because it is fast, affordable, and suitable for structured news summarization.

---

## AI Prompt Used

The following system prompt is used inside the `Summarize with AI` node.

<details>
<summary><strong>View the complete system prompt</strong></summary>

```text
You are a competitive-intelligence analyst covering AI and workflow automation.

Use only the supplied articles. Do not invent facts, numbers, companies, or events.

Create a concise weekly digest in Markdown. Always finish every required section.

Every company update must include a complete Markdown source link:
[Exact article title](complete article URL)

Do not add a title or Sources Reviewed section because another node adds them.

Return exactly:

## Executive Summary

Write 3 concise sentences.

## Key Takeaways

Provide exactly 3 numbered takeaways. Each takeaway must be one sentence and include a source link when referring to a specific event.

## Competitor Updates

Include only the 3 most important companies.

For each company:

### Company Name

- What happened
- Why it matters
- Source: [Exact article title](complete article URL)

## Industry Trends

Provide exactly 2 short bullet points.

## Recommended Actions

Provide exactly 2 practical bullet points.

Keep the complete response under 600 words. Never stop before completing Recommended Actions.
```

</details>

### User Prompt

```text
Reporting period: {{ $json.periodStart }} to {{ $json.periodEnd }}

Here are the {{ $json.count }} articles to analyze:

{{ $json.articlesText }}
```

---

## Reliability Features

The workflow includes:

- HTTP request timeout handling
- Continue-on-error behavior for failed feeds
- Defensive RSS parsing
- Seven-day publication-date validation
- Invalid-date rejection
- Future-date rejection
- AI and automation relevance filtering
- Duplicate-title detection
- Maximum article limit
- AI-response fallback handling
- No-news Gmail notification
- No-news Slack notification
- Separate formatting for Gmail and Slack

---

## Output Formatting

### Gmail

The workflow converts the Markdown digest into styled HTML before sending it through Gmail.

The Gmail output includes:

- Formatted headings
- Numbered lists
- Bullet points
- Clickable article links
- Reporting period
- Sources reviewed

### Slack

The workflow converts the digest into Slack-compatible formatting.

The Slack output includes:

- Bold section headings
- Numbered takeaways
- Bullet points
- Clickable source links
- A separate no-news notification

---

## Testing

The workflow was tested for:

- Successful Google News RSS retrieval
- Successful TechCrunch AI RSS retrieval
- RSS parsing
- Seven-day article filtering
- Relevance filtering
- Duplicate removal
- OpenAI summarization
- Three generated key takeaways
- Gmail HTML delivery
- Slack message delivery
- No-news Gmail notification
- No-news Slack notification

---

## Project Documentation

Detailed workflow architecture, design choices, AI prompts, testing results, Gmail output, Slack output, and screenshots are available in:

`Nithik_Roshan_n8n_Architecture_and_More_Details.pdf`

---

## Project Files

```text
AI Competitor News Monitor & Weekly Digest.json
Nithik_Roshan_n8n_Architecture_and_More_Details.pdf
README.md
screenshots/
```

---

## Screenshots

The project documentation includes screenshots of:

- Complete n8n workflow
- Successful workflow execution
- Gmail digest
- Slack digest
- No-news notification

---

## Public Workflow

Public n8n workflow link:

`PASTE_PUBLIC_N8N_WORKFLOW_LINK_HERE`

---

## Security

The public workflow and repository do not contain:

- OpenAI API keys
- Gmail OAuth tokens
- Slack access tokens
- Passwords
- Private credentials

Users must connect their own credentials after importing the workflow.

---

## Prepared By

**Nithik Roshan Devaraj**

Junior AI Engineer Take-Home Assignment  
**FocusKPI**
