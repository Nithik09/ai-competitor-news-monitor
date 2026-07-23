# AI Competitor News Monitor & Weekly Digest

An n8n workflow that monitors AI and automation news, summarizes updates using OpenAI, and sends a weekly digest through Gmail and Slack.

## Workflow Features

- Runs every Monday at 9:00 AM
- Uses Google News RSS and TechCrunch AI RSS
- Filters articles from the last seven days
- Removes duplicate and irrelevant stories
- Uses OpenAI GPT-4o-mini
- Generates 3–5 key takeaways
- Formats the digest as HTML
- Sends the digest through Gmail and Slack
- Sends a fallback message when no news is found

## How to Use

1. Download the workflow JSON.
2. Import it into n8n.
3. Connect your own OpenAI, Gmail, and Slack credentials.
4. Update the destination email and Slack channel.
5. Test the workflow.
6. Activate the workflow.

## AI Tools Used

- OpenAI GPT-4o-mini for summarization
- ChatGPT for workflow design, debugging, and prompt improvement
